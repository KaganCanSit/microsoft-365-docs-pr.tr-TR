---
title: Mac'te Uç Nokta için Microsoft Defender yükleme sorunlarını giderme
description: Mac'te Uç Nokta için Microsoft Defender'da yükleme sorunlarını giderin.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme
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
ms.openlocfilehash: 5f56e28d472cb3fdf8dd089effcd4beac6e42374
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011967"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender yükleme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [macOS'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>Yükleme başarısız oldu

El ile yükleme için, yükleme sihirbazının Özet sayfasında "Yükleme sırasında bir hata oluştu. Yükleyici yüklemenin başarısız olmasına neden olan bir hatayla karşılaştı. Yardım için yazılım yayıncıya başvurun." MDM dağıtımlarında da genel yükleme hatası olarak görüntülenir.

Son kullanıcıya tam bir hata görüntülemezken, yüklemenin ilerleme durumuyla birlikte günlük dosyasını sürekli olarakliyoruz `/Library/Logs/Microsoft/mdatp/install.log`. Her yükleme oturumu bu günlük dosyasının sonuna eklenir. Yalnızca son yükleme `sed` oturumunun çıkışını alırsınız:

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

Bu örnekte, asıl nedeni ile önek vardır `[ERROR]`.
Bu sürümler arasındaki bir düşürme destek verme sistemi destek verme nedeniyle yükleme başarısız oldu.

## <a name="mdatp-install-log-missing-or-not-updated"></a>MDATP yükleme günlüğü eksik veya güncelleştirilmedi

Ender durumlarda, yükleme MDATP's /Library/Logs/Microsoft/mdatp/install.log dosyasında izleme bırakır.
İlk olarak, bir yükleme olduğunu doğrulayın. Sonra macOS günlüklerini sorguarak olası hataları çözümleyebilirsiniz. İstemci kullanıcı arabirimi yoksa, MDM dağıtımlarında bunu yapmak yararlı olur. Çok fazla miktarda bilgi elde edilene kadar, bir sorguyu çalıştırmak ve günlük işlem adına göre filtrelemek için dar bir zaman penceresi kullanmanızı öneririz.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
