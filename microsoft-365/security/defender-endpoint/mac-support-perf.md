---
title: macOS'ta Uç Nokta için Microsoft Defender sorunları giderme
description: macOS'ta Uç Nokta için Microsoft Defender sorunlarını giderin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, performans
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e83400e444d4c8c733bea5552a31954bb019e358
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474057"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender sorunları giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [macOS Uç Nokta için Microsoft Defender üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konu başlığında, macOS'ta karşılaşılan performans sorunlarıyla ilgili performans sorunlarını daraltmak Uç Nokta için Microsoft Defender adımlarını sağlar.

Gerçek zamanlı koruma (RTP), macOS üzerinde cihazınızı sürekli izleyen Uç Nokta için Microsoft Defender tehditlere karşı koruyan bir özelliktir. Dosya ve süreç izleme ve diğer üç taraftan oluşur.

Çalıştırıyorsanız uygulamalara ve cihaz özelliklerinize bağlı olarak, macOS'ta çalışan uygulamalarınız ve cihaz özelliklerinize bağlı olarak, Uç Nokta için Microsoft Defender performansıyla deneyimleebilirsiniz. Özel olarak, kısa bir zaman süresinde birçok kaynaklara erişen uygulamalar veya sistem süreçleri, macOS'ta Uç Nokta için Microsoft Defender sorunlarına yol açabilirsiniz.

Aşağıdaki adımlar, bu sorunları gidermek ve azaltmak için kullanılabilir:

1. Aşağıdaki yöntemlerden birini kullanarak gerçek zamanlı korumayı devre dışı bırakın ve performansın geliştirip geliştiri olmadığınızı gözlemin. Bu yaklaşım, macOS'Uç Nokta için Microsoft Defender performans sorunlarına katkıda bulunmak isteyip olmadığını daraltmanıza yardımcı olur.

      Cihazınız organizasyonu tarafından yönetilmiyorsa, gerçek zamanlı koruma aşağıdaki seçeneklerden biri kullanılarak devre dışı bırakılabilir:

    - Kullanıcı arabiriminden. MacOS Uç Nokta için Microsoft Defender da ayarları açın ve Ayarları **yönet'e gidin**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Gerçek zamanlı korumayı yönet sayfası" lightbox="images/mdatp-36-rtp.png":::
      

    - Terminal'den. Güvenlik nedeniyle bu işlem için yükseltme gerekir.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Cihazınız organizasyonu tarafından yönetiliyorsa, macOS'ta mobil cihaz için tercihleri ayarlama konusunda verilen yönergeler kullanılarak gerçek zamanlı koruma [Uç Nokta için Microsoft Defender devre dışı bırakılabilir](mac-preferences.md).

      Gerçek zamanlı koruma kapalıyken performans sorunu devam ederse sorunun kaynağı ana bileşen uç noktada algılama ve yanıtlama olabilir. Bu durumda, diğer yönergeler ve risk azaltma için lütfen müşteri desteğine başvurun.

2. Finder'ı açın ve Uygulamalar Yardımcı **Programları'nı** \> **bulun**. Etkinlik **İzleyicisi'ne** açın ve sisteminiz için hangi uygulamaların kaynakları kullananları çözümlenin. Tipik örnekler yazılım güncelleştirenleri ve derleyicileridir.

3. En çok taramaları tetikleyen uygulamaları bulmak için, Mac'te Uç Nokta için Defender tarafından toplanan gerçek zamanlı istatistikleri kullanabilirsiniz.

      > [!NOTE]
      > Bu özellik 100.90.70 veya daha yeni sürümlerde kullanılabilir.
      Bu özellik **Dogfood** ve **InsiderFast kanallarında varsayılan olarak etkindir** . Farklı bir güncelleştirme kanalı kullanıyorsanız, bu özellik komut satırdan etkinleştirilebilir:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Bu özelliğin etkinleştirilmesi için gerçek zamanlı koruma gerekir. Gerçek zamanlı korumanın durumunu kontrol etmek için aşağıdaki komutu çalıştırın:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Yeni **girdinin real_time_protection_enabled** doğru olduğunu doğrulayın. Aksi takdirde, etkinleştirmek için aşağıdaki komutu çalıştırın:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      Geçerli istatistikleri toplamak için çalıştırın:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > **--output json kullanarak** (çift çizgiye dikkat olun) çıkış biçiminin ayrıştırmaya hazır olduğunu unutmayın.
      Bu komutun çıktısı tüm işlemleri ve ilişkili tarama etkinliklerini gösterir.

4. Mac sisteminiz üzerinde, aşağıdaki komutu kullanarak örnek Python ayrıştırıcı high_cpu_parser.py'yi indirin:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Bu komutun çıkışı aşağıdakine benzer olması gerekir:

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.
    mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in
    0s
    ```

5. Ardından aşağıdaki komutları yazın:

      ```bash
        chmod +x high_cpu_parser.py
      ```

      ```bash
        cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
      ```

      Yukarıdakinin çıktısı, performans sorunlarına en çok katkıda bulunanların listesidir. İlk sütun süreç tanımlayıcısıdır (PID), ikinci sütun süreç adı ve son sütun da etkiye göre sıralanmış taranmış dosyaların sayısıdır.

      Örneğin, komutun çıkışı aşağıdakine benzer olur:

      ```output
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

      Mac'te Uç Nokta için Defender'ın performansını artırmak için taranan toplam dosya satırı altında en yüksek sayıya sahip satırı bulun ve dışlama ekleyin. Daha fazla bilgi için bkz [. Linux'ta Uç Nokta için Defender için dışlamaları yapılandırma ve doğrulama](linux-exclusions.md).

      > [!NOTE]
      > Uygulama, istatistikleri bellekte depolar ve yalnızca dosyanın başlatılıyor olduğu ve gerçek zamanlı koruma etkinleştirildiğinden bu yana etkinliklerini takip ediyor. Gerçek zamanlı korumanın kapalı olduğu dönemlerden önce veya bu süre içinde başlatılan süreçler sayılmaz. Buna ek olarak, yalnızca taramaları tetikleyen olaylar sayılır.
      >
6. MacOS Uç Nokta için Microsoft Defender performans sorunlarına katkıda bulunan işlemler veya disk konumlarının dışlamaları ile ilgili sorunları yapılandırın ve gerçek zamanlı korumayı yeniden etkinleştirin.

     Ayrıntılar [için bkz. macOS'ta Uç Nokta için Microsoft Defender dışlamaları yapılandırma ve](mac-exclusions.md) doğrulama.
