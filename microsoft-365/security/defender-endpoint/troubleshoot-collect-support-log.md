---
title: Canlı yanıtı kullanarak Uç Nokta için Microsoft Defender'da destek günlüklerini toplama
description: Uç nokta için Microsoft Defender sorunlarını gidermek için canlı yanıtı kullanarak günlük toplamayı öğrenin
keywords: destek, günlük, toplama, sorun giderme, canlı yanıt, liveanalyzer, çözümleyici, canlı, yanıt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: b6d4b6f78cc677f9be5f664d86d8734ebd8df2f7
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997558"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Canlı yanıtı kullanarak Uç Nokta için Microsoft Defender'da destek günlüklerini toplama


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Destek ile iletişime geçerek, Uç Nokta İstemci Çözümleyicisi aracı için Microsoft Defender'ın çıkış paketini sağlamanız istenebilirsiniz.

Bu konu başlığında, aracı Canlı Yanıt ile çalıştırma hakkında yönergeler ve bilgiler verr.

1. Uygun betiği indirme
   - Yalnızca Uç nokta istemci algılayıcı günlükleri için Microsoft Defender: [LiveAnalyzer.ps1 betik.](https://aka.ms/MDELiveAnalyzer)
      - Sonuç paketi yaklaşık boyut: ~100 Kb
   - Uç nokta istemci algılayıcısı ve Virüsten Koruma günlükleri için Microsoft Defender: [LiveAnalyzer+MDAV.ps1 betiği](https://aka.ms/MDELiveAnalyzerAV).
       - Sonuç paketi yaklaşık boyutu: ~10 Mb

2. Araştırmamız [gereken makinede](live-response.md#initiate-a-live-response-session-on-a-device) Canlı Yanıt oturumu başlatma.

3. Dosyayı **Upload seç öğesini seçin**.

    ![Karşıya yükleme dosyasının görüntüsü.](images/upload-file.png)

4. Dosya **seç'i seçin**.

    ![Dosya seç düğmesinin resmi1.](images/choose-file.png)

5. MDELiveAnalyzer.ps1 adlı indirilmiş dosyayı seçin ve Onayla'ya **tıklayın**

   ![Dosya seç düğmesinin resmi2.](images/analyzer-file.png)

6. LiveResponse oturumu devam ederken çözümleyiciyi çalıştırmak ve sonuç dosyasını toplamak için aşağıdaki komutları kullanın:

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![Komutların görüntüsü.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - MDEClientAnalyzer'ın en son önizleme sürümü buradan indirilebilir: [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer).
>
> - LiveAnalyzer betiği, sorun giderme paketini hedef makineye şu makineden indirir: https://mdatpclientanalyzer.blob.core.windows.net.
>
>   Makinenin yukarıdaki URL'ye ulaşmalarına izin veramıyorsanız, LiveAnalyzer betiği MDEClientAnalyzerPreview.zip önce bu dosyayı kitaplı kitaplılara yükleyin:
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Makinenin Uç nokta bulut hizmetleri için Microsoft Defender ile iletişim kurmama veya Uç nokta portalı için Microsoft Defender'da beklendiği gibi görünmese bile, makinede yerel olarak veri toplama hakkında daha fazla bilgi için bkz. Uç nokta hizmeti [URL'leri için Microsoft Defender'a](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls) istemci bağlantısını doğrulama.
> 
> - Canlı yanıt [komut örneklerinde](live-response-command-examples.md) de açıklandığı gibi, arka plan eylemi olarak günlükleri toplamak için komutun sonundaki '&' simgesini kullanabilirsiniz:
>   ```console
>   Run MDELiveAnalyzer.ps1&
>   ```


## <a name="see-also"></a>Ayrıca bkz.
- [İstemci çözümleyicisi genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirme ve çalıştırma](download-client-analyzer.md)
- [İstemci çözümleyicisini çözümleyiciyi çalışma Windows](run-analyzer-windows.md)
- [macOS veya Linux'ta istemci çözümleyicisini çalıştırın](run-analyzer-macos-linux.md)
- [Windows'da gelişmiş sorun giderme için veri Windows](data-collection-analyzer.md)
- [Çözümleyici HTML raporunu anlama](analyzer-report.md)
