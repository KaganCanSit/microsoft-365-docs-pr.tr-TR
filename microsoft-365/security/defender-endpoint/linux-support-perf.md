---
title: Linux'ta Uç Nokta için Microsoft Defender performans sorunlarını giderme
description: Linux'ta Uç Nokta için Microsoft Defender performans sorunlarını giderme.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, performans
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3452f36068facc92885047184f7e00828f569cbc
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873016"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender performans sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu belgede, mevcut kaynak yetersizliklerini ve sistemi bu tür durumlara dönüştüren işlemleri anlamak ve azaltmak için kullanılabilir tanılama araçlarını kullanarak Linux'ta Uç Nokta için Defender ile ilgili performans sorunlarının nasıl daraltılacağına ilişkin yönergeler sağlanır. Performans sorunları, sistemdeki kaynak kullanımı profiline bağlı olarak bir veya daha fazla donanım alt sistemindeki performans sorunlarına neden olur. Bazen uygulamalar disk G/Ç kaynaklarına duyarlıdır ve daha fazla CPU kapasitesine ihtiyaç duyar ve bazen bazı yapılandırmalar sürdürülebilir değildir ve çok fazla yeni işlem tetikleyebilir ve çok fazla dosya tanımlayıcısı açabilir.

Çalıştırdığınız uygulamalara ve cihazınızın özelliklerine bağlı olarak, Linux'ta Uç Nokta için Defender'ı çalıştırırken en iyi performansın altında bir performansla karşılaşabilirsiniz. Özellikle CPU, Disk ve Bellek gibi birçok kaynağa kısa bir zaman aralığı boyunca erişen uygulamalar veya sistem işlemleri Linux üzerinde Uç Nokta için Defender'da performans sorunlarına yol açabilir.

> [!WARNING]
> Başlamadan önce **lütfen cihazda şu anda diğer güvenlik ürünlerinin çalışmadığından emin olun**. Birden çok güvenlik ürünü çakışabilir ve konak performansını etkileyebilir.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Gerçek Zamanlı Koruma İstatistiklerini kullanarak performans sorunlarını giderme

**Şunlar için geçerlidir:**
- Yalnızca AV ile ilgili performans sorunları

Gerçek zamanlı koruma (RTP), Linux'ta cihazınızı sürekli izleyen ve tehditlere karşı koruyan bir Uç Nokta için Defender özelliğidir. Dosya ve süreç izleme ve diğer buluşsal yöntemlerden oluşur.

Bu sorunları gidermek ve azaltmak için aşağıdaki adımlar kullanılabilir:

1. Aşağıdaki yöntemlerden birini kullanarak gerçek zamanlı korumayı devre dışı bırakın ve performansın iyileşip iyileşmediğini gözlemleyin. Bu yaklaşım, Linux'ta Uç Nokta için Defender'ın performans sorunlarına katkıda bulunup bulunmadığını daraltmaya yardımcı olur.

    Cihazınız kuruluşunuz tarafından yönetilmiyorsa, gerçek zamanlı koruma komut satırından devre dışı bırakılabilir:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Cihazınız kuruluşunuz tarafından yönetiliyorsa, [Linux'ta Uç Nokta için Defender tercihlerini ayarlama](linux-preferences.md) başlığı altındaki yönergeler kullanılarak gerçek zamanlı koruma yöneticiniz tarafından devre dışı bırakılabilir.

    > [!NOTE]
    > Gerçek zamanlı koruma kapalıyken performans sorunu devam ederse sorunun kaynağı uç noktada algılama ve yanıtlama (EDR) bileşeni olabilir. Bu durumda lütfen bu makalenin **Uç Nokta için Microsoft Defender İstemci Çözümleyicisi'ni kullanarak performans sorunlarını giderme** bölümündeki adımları izleyin.

2. En çok taramayı tetikleyen uygulamaları bulmak için, Linux'ta Uç Nokta için Defender tarafından toplanan gerçek zamanlı istatistikleri kullanabilirsiniz.

    > [!NOTE]
    > Bu özellik 100.90.70 veya daha yeni sürümlerde kullanılabilir.

    Bu özellik ve `InsiderFast` kanallarında `Dogfood` varsayılan olarak etkindir. Farklı bir güncelleştirme kanalı kullanıyorsanız, bu özellik komut satırından etkinleştirilebilir:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Bu özelliğin etkinleştirilmesi için gerçek zamanlı koruma gerekir. Gerçek zamanlı korumanın durumunu denetlemek için aşağıdaki komutu çalıştırın:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Girdinin `real_time_protection_enabled` olduğunu `true`doğrulayın. Aksi takdirde, etkinleştirmek için aşağıdaki komutu çalıştırın:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    Geçerli istatistikleri toplamak için şunu çalıştırın:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Kullanmak ```--output json``` (çift çizgiye dikkat edin), çıkış biçiminin ayrıştırma için hazır olmasını sağlar.

    Bu komutun çıkışı tüm işlemleri ve bunların ilişkili tarama etkinliğini gösterir.

3. Linux sisteminizde şu komutu kullanarak örnek Python ayrıştırıcısını **high_cpu_parser.py** indirin:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Bu komutun çıkışı aşağıdakine benzer olmalıdır:


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. Ardından, aşağıdaki komutları yazın:

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      Yukarıdaki çıkışı, performans sorunlarına en çok katkıda bulunanların listesidir. İlk sütun işlem tanımlayıcısı (PID), ikinci sütun işlem adı ve son sütun ise etkilenen öğeye göre sıralanmış taranan dosyaların sayısıdır.
    Örneğin, komutun çıkışı aşağıdakine benzer olacaktır: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool    1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd     407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Linux'ta Uç Nokta için Defender'ın performansını geliştirmek için satırın altında `Total files scanned` en yüksek sayıya sahip olanı bulun ve bunun için bir dışlama ekleyin. Daha fazla bilgi için bkz. [Linux'ta Uç Nokta için Defender dışlamalarını yapılandırma ve doğrulama](linux-exclusions.md).

    > [!NOTE]
    > Uygulama istatistiği bellekte depolar ve yalnızca başlatıldığından ve gerçek zamanlı koruma etkinleştirildiğinden beri dosya etkinliğini izler. Gerçek zamanlı korumanın kapalı olduğu dönemlerde veya öncesinde başlatılan işlemler sayılmaz. Ayrıca, yalnızca taramaları tetikleyen olaylar sayılır.

5. Performans sorunlarına katkıda bulunan işlemler veya disk konumları için dışlamalarla Linux'ta Uç Nokta için Microsoft Defender yapılandırın ve gerçek zamanlı korumayı yeniden etkinleştirin.

    Daha fazla bilgi için bkz. [Linux'ta Uç Nokta için Microsoft Defender dışlamaları yapılandırma ve doğrulama](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Uç Nokta için Microsoft Defender İstemci Çözümleyicisi'ni kullanarak performans sorunlarını giderme

**Şunlar için geçerlidir:**
- AV ve EDR gibi tüm kullanılabilir Uç Nokta için Defender bileşenlerinin performans sorunları  

Uç Nokta için Microsoft Defender İstemci Çözümleyicisi (MDECA), Linux'ta [eklenen cihazlardaki](/microsoft-365/security/defender-endpoint/onboard-configure) performans sorunlarını gidermek için izlemeleri, günlükleri ve tanılama bilgilerini toplayabilir.

> [!NOTE]
> Uç Nokta için Microsoft Defender İstemci Çözümleyicisi aracı, Microsoft Müşteri Destek Hizmetleri (CSS) tarafından ip adresleri, Uç Nokta için Microsoft Defender karşılaşabileceğiniz sorunları gidermeye yardımcı olacak bilgisayar adları gibi bilgileri toplamak için düzenli olarak kullanılır. Gizlilik bildirimimiz hakkında daha fazla bilgi için bkz. [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Gereksinimler

- İstemci çözümleyicisi, Uç Nokta için Microsoft Defender eklemeden önce veya sonra [Desteklenen Linux](microsoft-defender-endpoint-linux.md#system-requirements) dağıtımlarında çalıştırılabilir.
- Linux için istemci çözümleyicisini buradan indirilebilen en son önizleme sürümünden indirin: <https://aka.ms/XMDEClientAnalyzer>
- Cihazınız bir ara sunucunun arkasındaysa, proxy sunucusunu mde_support_tool.sh betiğine ortam değişkeni olarak geçirebilirsiniz. Örneğin: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Linux'ta istemci çözümleyicisini çalıştırma

İlgili makinede bir terminal veya SSH açın ve aşağıdaki komutları çalıştırın:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Gerekli pip ve lxml bileşenlerini yüklemek için kök olmayan kullanım olarak çalıştırın: `./mde_support_tool.sh`
6. Gerçek tanılama paketini toplamak ve sonuç arşiv dosyasını oluşturmak için kök olarak yeniden çalıştırın: `./mde_support_tool.sh -d` Örnek:

   ![Komut satırı örneğinin resmi.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Çözümleyicinin sonuç çıktısını oluşturması için 'lxml' gerekir. Yüklü değilse çözümleyici aşağıdaki Python paketleri için resmi depodan getirmeye çalışır: <https://pypi.org/search/?q=lxml>
> 
> - Ayrıca aracın şu anda Python sürüm 3 veya üzerinin yüklü olması gerekir.
>
> - Python 3 kullanamayan veya lxml bileşenini getiremeyen bir makinede çalışıyorsanız, çözümleyicinin gereksinimlerinden herhangi birine sahip olmayan ikili tabanlı bir sürümünü indirebilirsiniz: [XMDE İstemci Çözümleyicisi İkili](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Ek söz dizimi yardımı:

**-h** \# Yardım<br>
\# Yardım iletisini göster

**Performans** \# Performans<br>
\# İsteğe bağlı olarak yeniden oluşturulabilen bir performans sorununun analizi için kapsamlı izleme toplar. Karşılaştırmanın süresini belirtmek için kullanma `--length=<seconds>` .

**-o** \# Çıkış<br>
\# Sonuç dosyası için hedef yolu belirtme

**-nz** \# No-Zip<br>
\# Ayarlanırsa, sonuçta elde edilen arşiv dosyası yerine bir dizin oluşturulur

**-f** \# Kuvvet<br>
\# Çıkış hedef yolda zaten varsa üzerine yaz

### <a name="result-package-contents"></a>Sonuç paketi içeriği

- report.html

  Açıklama: Çözümleyici betiğinin makinede çalıştırabileceği bulguları ve yönergeleri içeren ana HTML çıkış dosyası.

- mde_diagnostic.zip

  Açıklama: [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information) üzerinde *mdatp tanılama oluşturma* çalıştırılırken oluşturulan tanılama çıktısı aynı

- mde.xml

  Açıklama: Çalıştırılırken oluşturulan ve html rapor dosyasını derlemek için kullanılan XML çıkışı.

- Processes_information.txt

  Açıklama: Sistemdeki çalışan Uç Nokta için Microsoft Defender ilgili işlemlerin ayrıntılarını içerir.

- Log.txt

  Açıklama: Veri toplama sırasında ekrana yazılan günlük iletilerinin aynısını içerir.

- Health.txt

  Açıklama: *mdatp* health komutu çalıştırılırken gösterilen temel sistem durumu çıktısının aynısı.

- Events.xml

  Açıklama: ÇÖZÜMleyici tarafından HTML raporu oluştururken kullanılan ek XML dosyası.

- Audited_info.txt

  Açıklama: [Linux](/microsoft-365/security/defender-endpoint/linux-resources) işletim sistemi için denetlenen hizmet ve ilgili bileşenlerle ilgili ayrıntılar

- perf_benchmark.tar.gz

  Açıklama: Performans testi raporları. Bunu yalnızca performans parametresini kullanıyorsanız görürsünüz.

> [!NOTE]
> Yukarıdaki adımları takip ettikten sonra performans sorununun devam etmesi durumunda, daha fazla yönerge ve risk azaltma için lütfen müşteri desteğine başvurun.



## <a name="see-also"></a>Ayrıca bkz.

- [Sistem durumu sorunlarını araştırın](health-status.md)
