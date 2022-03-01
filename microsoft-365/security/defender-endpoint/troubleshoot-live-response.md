---
title: Uç nokta canlı yanıt sorunları için Microsoft Defender'da sorun giderme
description: Uç nokta için Microsoft Defender'da canlı yanıt kullanırken ortaya çıkabilecek sorunları giderme
keywords: canlı yanıt, canlı, yanıt, kilitli, dosya sorunlarını giderme
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
ms.openlocfilehash: 4a3bab27a4e2efd6b196167754303f35d5553de6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998152"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>Uç nokta canlı yanıt sorunları için Microsoft Defender'da sorun giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Bu sayfada, canlı yanıt sorunlarını gidermek için ayrıntılı adımlar yer sağlar.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>Canlı yanıt oturumları sırasında dosyaya erişilemiyor

Canlı yanıt oturumu sırasında bir eylem yapmaya çalışırken dosyaya erişile olmadığını belirten bir hata iletisiyle karşılaşırsanız, sorunu gidermek için aşağıdaki adımları kullanın.

1. Aşağıdaki komut dosyası kod parçacığını kopyalayın ve PS1 dosyası olarak kaydedin:

    ```powershell
    $copied_file_path=$args[0]
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue

    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }

    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message

    }
    ```

2. Betiği canlı yanıt kitaplığına ekleyin.
3. Betiği tek bir parametreyle çalıştırın: kopyalanan dosyanın dosya yolu.
4. TEMP klasörünüze gidin.
5. Kopyalanan dosyada yapmak istediğiniz eylemi çalıştırın.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>Yavaş canlı yanıt oturumları veya ilk bağlantılar sırasında gecikmeler

Canlı yanıt, Windows'de WNS hizmetiyle Uç nokta algılayıcısı kaydı için Defender'dan Windows. Canlı yanıtla ilgili bağlantı sorunlarınız varsa, aşağıdaki ayrıntıları onaylayın:

1. `notify.windows.com` ortamınız içinde engellenmiş değil. Daha fazla bilgi için bkz. [Cihaz ara sunucusunu ve İnternet bağlantı ayarlarını yapılandırma](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).
2. WpnService (Windows Push Notifications System Service) devre dışı bırakılamaz.

WpnService hizmet davranışını ve gereksinimlerini tam olarak anlamak için aşağıdaki makalelere bakın:

- [Windows Bildirim Hizmetleri'ne (WNS) genel bakış](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Enterprise WNS Trafiğini Desteklemek için Güvenlik Duvarı ve Ara Sunucu Yapılandırmalarını Yapılandırma](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Microsoft Anında Bildirimler Hizmeti (MPNS) Genel IP aralıkları](https://www.microsoft.com/download/details.aspx?id=44535)
