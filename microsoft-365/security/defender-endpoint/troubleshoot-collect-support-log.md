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
ms.openlocfilehash: a0d0f470a2af18dab298ba3a1af642362590da4c
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401168"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Canlı yanıtı kullanarak Uç Nokta için Microsoft Defender'da destek günlüklerini toplama


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Destek ile iletişime geçerek, Uç Nokta İstemci Çözümleyicisi aracı için Microsoft Defender'ın çıkış paketini sağlamanız istenebilirsiniz.

Bu konu başlığında, aracı Canlı Yanıt ile çalıştırma hakkında yönergeler ve bilgiler verr.

1. Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ın 'Araçlar' alt dizininden kullanılabilir [gerekli betikleri indirin ve alın](https://aka.ms/BetaMDEAnalyzer). <br>
Örneğin, temel algılayıcı ve cihaz sistem durumu günlüklerini almak için ".. \Tools\MDELiveAnalyzer.ps1".<br>
Defender Virüsten Koruma destek günlükleri de (MpSupportFiles.cab) MpSupportFiles.cab" getir'i alın. \Tools\MDELiveAnalyzerAV.ps1" 

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
