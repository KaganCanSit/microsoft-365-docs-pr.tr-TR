---
title: Linux'ta Uç Nokta için Microsoft Defender performans sorunlarını giderme
description: Linux'ta Uç Nokta için Microsoft Defender'da performans sorunlarını giderin.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, performans
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
ms.openlocfilehash: 14424f0cdff908fc641d6de1c22d25546473cc13
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011883"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender performans sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu belgede, mevcut kaynak eksikliklerini ve sistemi böyle durumlara dönüştüren süreçleri anlamak ve azaltmak için kullanılabilir tanılama araçlarını kullanarak Linux'ta Uç Nokta için Defender ile ilgili performans sorunlarını nasıl daraltacak yönergeleri sağlar. Performans sorunlarına genellikle sistemdeki kaynak kullanımının profiline bağlı olarak bir veya birden çok donanım alt sistemideki performans sorunları neden olur. Uygulamalar bazen disk I/O kaynaklarına duyarlıdır ve daha fazla CPU kapasitesine ihtiyacı olabilir; bazı yapılandırmalar sürdürülebilir değildir ve çok fazla yeni işlem tetikler ve çok fazla dosya tanımlayıcısı açabilir.

Linux'ta Uç Nokta için Defender'ı çalıştırmanız, çalıştırmada kullandığınız uygulamalara ve cihaz özelliklerinize bağlı olarak alt performansla ilgili olabilir. Özellikle CPU, Disk ve Bellek gibi çok sayıda kaynakta kısa bir zaman aralığının bu kadar çok kaynağına erişen uygulamalar veya sistem süreçleri, Linux'ta Uç Nokta için Defender'da performans sorunlarına yol açabilirsiniz.

> [!WARNING]
> Başlamadan önce **, lütfen diğer güvenlik ürünlerinin şu anda cihazda çalışmay olduğundan emin olun**. Birden çok güvenlik ürünü çakışarak ana bilgisayar performansını etkileyebilir.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Gerçek Zamanlı Koruma İstatistiklerini kullanarak performans sorunlarını giderme

**Aşağıdakiler için geçerlidir:**
- Yalnızca AV ile ilgili performans sorunları

Gerçek zamanlı koruma (RTP), Linux'ta cihazınızı sürekli izleyen ve tehditlere karşı koruyan uç nokta için Defender'ın bir özelliğidir. Dosya ve süreç izleme ve diğer üç taraftan oluşur.

Aşağıdaki adımlar, bu sorunları gidermek ve azaltmak için kullanılabilir:

1. Aşağıdaki yöntemlerden birini kullanarak gerçek zamanlı korumayı devre dışı bırakın ve performansın geliştirip geliştiri olmadığınızı gözlemin. Bu yaklaşım, Linux'ta Uç Nokta için Defender'ın performans sorunlarına katkıda olup olmadığını daraltmaya yardımcı olur.

    Cihazınız organizasyonu tarafından yönetilmiyorsa, gerçek zamanlı koruma komut satırına devre dışı bırakılabilir:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Cihazınız organizasyonu tarafından yönetiliyorsa, Linux'ta Uç nokta için Defender tercihlerini ayarlama konusunda verilen yönergeler kullanılarak gerçek zamanlı koruma yöneticiniz [tarafından devre dışı bırakılabilir](linux-preferences.md).

    > [!NOTE]
    > Gerçek zamanlı koruma kapalıyken performans sorunu devam ederse sorunun kaynağı uç noktada algılama ve yanıtlama (EDR) bileşeni olabilir. Bu durumda, lütfen bu makalenin Uç Nokta İstemci Çözümleyicisi **için Microsoft Defender'ı** kullanma performans sorunlarını giderme bölümündeki adımları izleyin.

2. En çok taramaları tetikleyen uygulamaları bulmak için Linux'ta Uç Nokta için Defender ile toplanmış gerçek zamanlı istatistikleri kullanabilirsiniz.

    > [!NOTE]
    > Bu özellik 100.90.70 veya daha yeni sürümlerde kullanılabilir.

    Bu özellik ve kanallarda varsayılan olarak `Dogfood` etkindir `InsiderFast` . Farklı bir güncelleştirme kanalı kullanıyorsanız, bu özellik komut satırdan etkinleştirilebilir:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Bu özelliğin etkinleştirilmesi için gerçek zamanlı koruma gerekir. Gerçek zamanlı korumanın durumunu kontrol etmek için aşağıdaki komutu çalıştırın:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Girdinin olduğunu `real_time_protection_enabled` doğrulayın `true`. Aksi takdirde, etkinleştirmek için aşağıdaki komutu çalıştırın:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    Geçerli istatistikleri toplamak için çalıştırın:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Çıkış ```--output json``` biçiminin (çift çizgiye dikkat olun) kullanılması, çıkış biçiminin ayrıştırmaya hazır olduğunu gösterir.

    Bu komutun çıktısı tüm işlemleri ve ilişkili tarama etkinliklerini gösterir.

3. Linux sisteminiz üzerinde, aşağıdaki komutu kullanarak örnek Python ayrıştırıcı **high_cpu_parser.py'yi** indirin:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Bu komutun çıkışı aşağıdakine benzer olması gerekir:


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. Ardından aşağıdaki komutları yazın:

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      Yukarıdakinin çıktısı, performans sorunlarına en çok katkıda bulunanların listesidir. İlk sütun süreç tanımlayıcısıdır (PID), ikinci sütun süreç adı ve son sütun da etkiye göre sıralanmış taranmış dosyaların sayısıdır.
    Örneğin, komutun çıkışı aşağıdakine benzer olur: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool     1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd    407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Linux'ta Uç Nokta için Defender'ın performansını artırmak için, `Total files scanned` satırın altında en yüksek sayıya sahip olan numarayı bulun ve bunun için bir dışlama ekleyin. Daha fazla bilgi için bkz [. Linux'ta Uç Nokta için Defender için dışlamaları yapılandırma ve doğrulama](linux-exclusions.md).

    > [!NOTE]
    > Uygulama, istatistikleri bellekte depolar ve yalnızca dosyanın başlatılıyor olduğu ve gerçek zamanlı koruma etkinleştirildiğinden bu yana etkinliklerini takip ediyor. Gerçek zamanlı korumanın kapalı olduğu dönemlerden önce veya bu süre içinde başlatılan süreçler sayılmaz. Buna ek olarak, yalnızca taramaları tetikleyen olaylar sayılır.

5. Performans sorunlarına katkıda bulunan işlemler veya disk konumları için dışlamalar bulunan Linux'ta Uç Nokta için Microsoft Defender'ı yapılandırın ve gerçek zamanlı korumayı yeniden etkinleştirin.

    Daha fazla bilgi için bkz. [Linux'ta Uç Nokta için Microsoft Defender dışlamaları yapılandırma ve doğrulama](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ı kullanarak performans sorunlarını giderme

**Aşağıdakiler için geçerlidir:**
- AV ve EDR gibi uç nokta bileşenleri için kullanılabilir Tüm Defender bileşenlerinin performans EDR  

Uç Nokta İstemci Çözümleyicisi için Microsoft Defender (MDECA), Linux'ta ekli cihazlarda performans sorunlarını gidermek için izleme, günlük ve [tanılama bilgilerini](/microsoft-365/security/defender-endpoint/onboard-configure) toplayabilirsiniz.

> [!NOTE]
> Uç Nokta İstemci Çözümleyicisi için Microsoft Defender aracı, Microsoft Customer Support Services (CSS) tarafından IP adresleri, Uç Nokta için Microsoft Defender ile karşılaşabilirsiniz sorunları gidermenize yardımcı olacak bilgisayar adları gibi bilgileri toplamak için düzenli olarak kullanılır. Gizlilik bildirimimiz hakkında daha fazla bilgi için bkz. [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Gereksinimler

- İstemci çözümleyicisi, Uç Nokta için Microsoft Defender'a eklemeden önce veya bu yüklemeden sonra [Linux'un](microsoft-defender-endpoint-linux.md#system-requirements) desteklenen dağıtımları üzerinde çalıştırabilirsiniz.
- Linux için istemci çözümleyicisini en son preview sürümü buradan indirebilirsiniz: <https://aka.ms/XMDEClientAnalyzer>
- Cihazınız bir proxy arkasında ise, proxy sunucusunu mde_support_tool.sh betiğine ortam değişkeni olarak kolayca geçebilirsiniz. Örneğin: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Linux'ta istemci çözümleyicisini çalıştırın

İlgili makinede bir terminal veya SSH açın ve aşağıdaki komutları çalıştırın:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Gerekli pip ve lxml'i yüklemek için kök olmayan kullanım olarak çalıştırın; hangi bileşenler: `./mde_support_tool.sh`
6. Gerçek tanılama paketini toplamak ve sonuç arşiv dosyasını oluşturmak için yeniden kök olarak çalıştırın: `./mde_support_tool.sh -d` Örnek:

   ![Komut satırı örneği görüntüsü.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Çözümleyicinin sonuç çıktısını üretmesi için 'lxml' gerekir. Yüklü değilse, çözümleyici aşağıdaki python paketleri için resmi depodan getirmeyi dener: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Buna ek olarak, araç şu anda Python sürüm 3 veya daha sonraki bir sürümünün de yüklü olması gerekir.
>
> - Python 3'ü kullana almayan veya lxml bileşenini getiren bir makinede çalışıyorsanız, hiçbir gereklilik belirt almayan çözümleyicinin ikili tabanlı sürümünü indirebilirsiniz: [XMDE İstemci](https://aka.ms/XMDEClientAnalyzerBinary) Çözümleyicisi İkilisi

### <a name="additional-syntax-help"></a>Ek söz dizimi yardımı:

**-h** \# Yardım<br>
\# Yardım iletisi göster

**performans** \# Performans<br>
\# Bir performans sorunu üzerinde isteğe bağlı olarak yeniden üretilebilir çözümlemesi için kapsamlı izleme toplar. Karşılaştırma `--length=<seconds>` süresini belirtmek için kullanma.

**-o** \# Çıktı<br>
\# Sonuç dosyasının hedef yolunu belirtme

**-nz** \# No-Zip<br>
\# Ayarlanırsa, sonuçta elde edilen bir arşiv dosyası yerine bir dizin oluşturulur

**-f** \# Kuvvet<br>
\# Çıktı hedef yolda zaten varsa üzerine yaz

### <a name="result-package-contents"></a>Sonuç paketi içeriği

- report.html

  Açıklama: Çözümleyici betiği tarafından makinede çalıştırılarak  çalıştırınan bulguları ve kılavuzu içeren ana HTML çıkış dosyası.

- mde_diagnostic.zip

  Açıklama: Linux'ta *mdatp tanılama oluşturulurken oluşturulan aynı tanılama* [çıktısı](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Açıklama: Çalışırken oluşturulan VE HTML rapor dosyasını oluşturmak için kullanılan XML çıktısı.

- Processes_information.txt

  Açıklama: Sistemde uç nokta ile ilgili işlemler için çalışan Microsoft Defender'ın ayrıntılarını içerir.

- Log.txt

  Açıklama: Veri toplama sırasında ekranda yazılan günlük iletilerinin aynısını içerir.

- Health.txt

  Açıklama: Mdatp health komutu çalıştırlarda gösterilen *aynı temel durum çıktısı* .

- Events.xml

  Açıklama: HTML raporu oluşturmak için çözümleyici tarafından kullanılan ek XML dosyası.

- Auditd_info.txt

  Açıklama: Denetlenen hizmet ve Linux işletim sistemiyle ilgili bileşenler [hakkında](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events) ayrıntılar

- perf_benchmark.tar.gz

  Açıklama: Performans testi raporları. Bunu yalnızca performans parametresini kullanıyorsanız görebilirsiniz.

> [!NOTE]
> Yukarıda adımları takipdikten sonra performans sorunu devam ederse, diğer yönergeler ve risk azaltma için lütfen müşteri desteğine başvurun.



## <a name="see-also"></a>Ayrıca bkz.

- [Aracı durumu sorunlarını araştırma](health-status.md)
