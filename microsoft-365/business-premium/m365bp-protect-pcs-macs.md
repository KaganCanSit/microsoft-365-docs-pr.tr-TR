---
title: Aynı Windows 10 ve Mac bilgisayarlarında, unmanaged Microsoft 365 İş Ekstra
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Diğer cihazlarla, unmanaged veya bring-your-own devices (BYOD) Microsoft 365 İş Ekstra.
ms.openlocfilehash: b3d783ba498337af7ff867fe749366abe1734da5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705012"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs-in-microsoft-365-business-premium"></a>Aynı Windows 10 ve Mac bilgisayarlarında, unmanaged Microsoft 365 İş Ekstra

Bilgisayar ve Mac Windows 10 bilgisayarlarınızı Microsoft Intune'a kaydederek yönetebilirsiniz, böylece ortamınıza erişmeden önce iyi ve güvenli olduğundan emin olursanız. Bununla birlikte, pek çok kampanya ve küçük işletme kendi cihazlarını getiren (BYOD) personel içerir ve bu, kuruluş tarafından yönetil değildir. Bu yönetimi olmayan PC ve Mac bilgisayarlarda, en düşük güvenlik yetenekleri yapılandırıldığından emin olmak için bu makaleyi kullanın.

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>Mac veya Windows 10 çalıştıran bir bilgisayarı koruma

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365, or a Mac, the Microsoft 365 protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
Bilgisayarınız Windows 10 Mac veya BILGISAYARıNıZ tarafından yönetilmiyorsa, bu güvenlik özelliklerini yapılandırmış olun.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Cihaz şifrelemeyi açma**<p>

Cihaz şifreleme, çok çeşitli cihazlarda kullanılabilir Windows şifrelemeyle verilerinizin korunmasına yardımcı olur. Cihaz şifrelemeyi açsanız, yalnızca yetkili kişiler cihazınıza ve verilerinize erişebilirsiniz. Yönergeler [için bkz. Cihaz şifrelemeyi](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) açma.

 Aygıtınızda cihaz şifrelemesi kullanılamıyorsa, bunun yerine standart [BitLocker şifrelemesi'ni açabilirsiniz](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) . (BitLocker Windows 10 Home sürümüyle kullanılamaz.) 

**Cihazınızı bir mobil cihazla Windows Güvenliği**<p>
Virüsten koruma Windows 10, Virüsten Koruma ile en son virüsten koruma Windows Güvenliği. Windows 10'i ilk kez Windows Güvenliği, kötü amaçlı yazılım, virüs ve güvenlik tehditlerini taraarak bilgisayarınızın korunmasına etkin bir şekilde yardımcı olur. Windows Güvenliği, bilgisayarınıza indiren veya bilgisayarınızda çalıştırdınız her şeyi taramak için gerçek zamanlı koruma kullanır.

Windows Güncelleştirme, bilgisayarınızın güvenli Windows Güvenliği tehditlere karşı korunmasına yardımcı olmak için güncelleştirmeleri otomatik olarak indirir.

Windows'in önceki bir sürümünü kullanıyorsanız ve Microsoft Security Essentials kullanıyorsanız, temel sürüme Windows Güvenliği. Daha fazla bilgi için bkz[. Mobil cihazla cihazımı korumaya Windows Güvenliği](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Güvenlik Duvarı'Windows açma**<p>
Başka bir güvenlik Windows açık olsa bile Güvenlik Duvarı'nı her zaman çalıştırmalısınız. Güvenlik duvarı Windows kullanılması, cihazınızın (ve varsa ağınız) yetkisiz erişime karşı daha korumasız hale gelir. Yönergeler [için Windows Duvarı'nı açma veya](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) kapatma'ya bakın.

## <a name="mac"></a>[Mac](#tab/Mac)

**FileVault'u kullanarak Mac diskini şifreleme**<p>
Disk şifreleme, cihazlar kaybolur veya çalınırsa verileri korur. FileVault tam disk şifreleme, başlangıç diskinizin bilgilerine yetkisiz erişimin önlenmesine yardımcı olur. Yönergeler [için bkz. FileVault'u kullanarak Mac'inizin başlangıç diskini](https://support.apple.com/HT204837) şifreleme.

**Mac'inizi kötü amaçlı yazılımdan koruma**<p>
Microsoft, Mac bilgisayarınıza güvenilir bir virüsten koruma yazılımı yüklemenizi ve bu yazılımı kullanmanızı önerir. Tercih listesi için şu makaleye bakın: En iyi [Mac virüsten koruma yazılımı 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Ayrıca, yalnızca güvenilir kaynaklardan gelen yazılımları kullanarak kötü amaçlı yazılım riskini azaltabilirsiniz. Güvenlik ve Gizlilik & ayarları, Mac'inize yüklenmiş yazılım kaynaklarını belirtmenize olanak sağlar. Daha fazla bilgi için bkz. [Mac'inizi kötü amaçlı yazılımdan koruma](https://support.apple.com/kb/PH25087).

**Güvenlik duvarı korumasını açma**<p>
Mac'inizi İnternet'e veya bir ağa bağlıyken diğer bilgisayarlar tarafından başlatılan istenmeyen kişilerden korumak için güvenlik duvarı ayarlarını kullanın. Bu koruma olmadan, Mac'iniz yetkisiz erişime karşı daha korumasız olabilir. Yönergeler [için uygulama güvenlik duvarı hakkında](https://support.apple.com/HT201642) bilgi edinebilirsiniz.
