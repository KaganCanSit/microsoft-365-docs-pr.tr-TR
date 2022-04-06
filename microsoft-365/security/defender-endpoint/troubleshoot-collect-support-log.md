---
title: Canlı yanıtı kullanarak Uç Nokta için Microsoft Defender günlüklerini toplama
description: Günlük toplama hakkında bilgi edinmek ve sorunları gidermek için canlı Uç Nokta için Microsoft Defender öğrenin
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
ms.openlocfilehash: 138b532e7786a3d142c3cbbe68f668a4b0e05591
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472583"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Canlı yanıtı kullanarak Uç Nokta için Microsoft Defender günlüklerini toplama


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Destekle iletişime geçerek, Çözümleyici Çözümleyicisi aracının çıkış paketini Uç Nokta için Microsoft Defender istenebilirsiniz.

Bu konu başlığında, aracı Canlı Yanıt ile çalıştırma hakkında yönergeler ve bilgiler verr.

1. İstemci Çözümleyicisi'nin 'Araçlar' alt dizininde bulunan gerekli betikleri [Uç Nokta için Microsoft Defender alın](https://aka.ms/BetaMDEAnalyzer). <br>
Örneğin, temel algılayıcı ve cihaz sistem durumu günlüklerini almak için ".. \Tools\MDELiveAnalyzer.ps1".<br>
Defender Virüsten Koruma destek günlükleri de (MpSupportFiles.cab) MpSupportFiles.cab" getir'i alın. \Tools\MDELiveAnalyzerAV.ps1" 

2. Araştırmamız [gereken makinede](live-response.md#initiate-a-live-response-session-on-a-device) Canlı Yanıt oturumu başlatma.

3. Dosyayı **Upload seç öğesini seçin**.

   :::image type="content" source="images/upload-file.png" alt-text="Karşıya yükleme dosyası" lightbox="images/upload-file.png":::

4. Dosya **seç'i seçin**.

   :::image type="content" source="images/choose-file.png" alt-text="Dosya seç düğmesi-1" lightbox="images/choose-file.png":::

5. MDELiveAnalyzer.ps1 adlı indirilmiş dosyayı seçin ve Onayla'ya **tıklayın**

   :::image type="content" source="images/analyzer-file.png" alt-text="Dosya seç düğmesi-2" lightbox="images/analyzer-file.png":::

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
> - Makine Uç Nokta için Microsoft Defender bulut hizmetleriyle iletişim kurama veya beklendiği gibi Uç Nokta için Microsoft Defender bir makinede yerel olarak veri toplama hakkında daha fazla bilgi için bkz. İstemci [bağlantısını doğrulama Uç Nokta için Microsoft Defender hizmeti URL'leri.](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)
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
