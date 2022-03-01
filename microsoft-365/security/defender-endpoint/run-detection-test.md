---
title: Uç nokta için Microsoft Defender'a düzgün bir şekilde ekli olduğunu doğrulamak için cihazda bir algılama testi çalıştırın
description: Düzgün ekli olduğunu doğrulamak için, uç nokta için Microsoft Defender hizmetine eklenen bir cihazda algılama test betiği çalıştırın.
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 41ba14fd2e4a9e3726e4ef4287812cf8d3ffb2d1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012009"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Yeni eklenen Uç nokta cihazı için Microsoft Defender'da bir algılama testi çalıştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Windows 11
- Desteklenen Windows 10 sürümleri
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server, sürüm 1803
- Windows Server 2019
- Windows Server 2022
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Yönetim için Uç Nokta hizmeti için Microsoft Defender'a bir cihaz eklerken, buna ekleme cihazları da denir. Ekleme, cihazların sistem durumuyla ilgili sinyalleri hizmete bildirmesini sağlar.

Bir cihazın hizmete başarıyla ekli olduğundan emin olmak veya bunu doğrulamak, dağıtım işleminin tamamına yönelik önemli bir adımdır. Beklenen tüm cihazların yönetiliyor olması güvence sağlar. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>PowerShell algılama testi kullanarak cihazın Uç Nokta eklemesi için Microsoft Defender'ı doğrulama

Yeni eklenen bir cihazda aşağıdaki PowerShell betiğini çalıştırarak cihazın Uç nokta için Defender hizmetine düzgün bir şekilde rapor olduğunu doğrulayın.

1. Klasör oluşturun: 'C:\test-MDATP-test'.
2. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

   1. **Başlat'a gidin** ve **cmd yazın**.

   1. Komut **İstemi'ne sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

      ![Window Başlat menüsü Yönetici olarak çalıştır'a işaret ediyor olabilir.](images/run-as-admin.png)

3. Komut isteminde, aşağıdaki komutu kopyalayıp çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa, yaklaşık on dakika içinde portalda bulunan cihaz için yeni bir uyarı görünür.

## <a name="related-topics"></a>İlgili konular

- [Cihaz Windows ekleme](configure-endpoints.md)
- [Sunucuları ekleme](configure-server-endpoints.md)
- [Uç nokta ekleme sorunları için Microsoft Defender'da sorun giderme](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
