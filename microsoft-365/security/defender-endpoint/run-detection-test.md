---
title: Cihazda algılama testini çalıştırarak bu cihazda cihazın düzgün şekilde yerleşik olduğunu Uç Nokta için Microsoft Defender
description: Düzgün ekli olduğunu doğrulamak için yakın zamanda Uç Nokta için Microsoft Defender hizmette eklenmiş bir cihazda algılama sınama betiği çalıştırın.
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
ms.openlocfilehash: 1d8459633d00d759fda1584e0084cd8ed4e12633
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477269"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Windows 11
- Desteklenen Windows 10 sürümleri
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server, sürüm 1803
- Windows Server 2019
- Windows Server 2022
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Yönetim için mobil cihaz hizmetine Uç Nokta için Microsoft Defender, buna ekleme cihazları da denir. Ekleme, cihazların sistem durumuyla ilgili sinyalleri hizmete bildirmesini sağlar.

Bir cihazın hizmete başarıyla ekli olduğundan emin olmak veya bunu doğrulamak, dağıtım işleminin tamamına yönelik önemli bir adımdır. Beklenen tüm cihazların yönetiliyor olması güvence sağlar. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>PowerShell Uç Nokta için Microsoft Defender sınaması kullanarak bir cihaz ekleme işlemi doğrulama

Yeni eklenen bir cihazda aşağıdaki PowerShell betiğini çalıştırarak cihazın Uç nokta için Defender hizmetine düzgün bir şekilde rapor olduğunu doğrulayın.

1. Klasör oluşturun: 'C:\test-MDATP-test'.
2. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

   1. **Başlat'a gidin** ve **cmd yazın**.

   1. Komut **İstemi'ne sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Yönetici Başlat menüsü çalıştır'a işaret ediyor olan olay" lightbox="images/run-as-admin.png":::
    
3. Komut isteminde, aşağıdaki komutu kopyalayıp çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa, yaklaşık on dakika içinde portalda bulunan cihaz için yeni bir uyarı görünür.

## <a name="related-topics"></a>İlgili konular

- [Cihaz Windows ekleme](configure-endpoints.md)
- [Sunucuları ekleme](configure-server-endpoints.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
