---
title: Windows cihazlarının güvenliğini sağlama
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: herhangi bir Windows cihazının iş veya okul hesabında oturum açtıktan sonra alacağı varsayılan cihaz ilkesinin ayarlarını yapılandırma hakkında bilgi edinin.
ms.openlocfilehash: a9fd78ef37aed3663572b7049ae150e85916e41b
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607421"
---
# <a name="secure-windows-devices"></a>Windows cihazlarının güvenliğini sağlama

Buradaki amaç, Windows 10 veya 11 için varsayılan cihaz ilkesinin parçası olan ayarları yapılandırmaktır. Mobil cihazlar ve bilgisayarlar da dahil olmak üzere bir Windows cihazını iş hesaplarıyla oturum açarak bağlayan tüm kullanıcılar bu ayarları otomatik olarak alır. Kurulum sırasında varsayılan ilkeyi kabul etmenizi ve daha sonra belirli kullanıcı gruplarını hedef alan ilkeler eklemenizi öneririz.

## <a name="before-you-begin"></a>Başlamadan önce

windows cihazlarını Microsoft 365 İş Ekstra kullanıcılar için ayarlamadan önce tüm Windows cihazlarının Windows 10 Pro çalıştığından emin olun.

Windows 10 Pro, Windows 10 Pro ve Windows 11 Pro tamamlayan ve merkezi yönetim ve güvenlik denetimlerini etkinleştiren bir dizi bulut hizmeti ve cihaz yönetimi özelliği olan Windows 10 Business dağıtımı için önkoşuldur Microsoft 365 İş Ekstra.

[Microsoft 365 İş Ekstra gereksinimleri hakkında daha fazla bilgi edinin](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro"></a>Windows 10 Pro

Windows 7 Pro, Windows 8 Pro veya Windows 8.1 Pro gibi Windows'un önceki sürümlerini çalıştıran Windows cihazlarınız varsa, Microsoft 365 İş Ekstra aboneliğiniz bu cihazları Windows 10 Pro veya Windows 11 Pro.
  
Windows cihazlarını yükseltme hakkında daha fazla bilgi için bkz[. Windows cihazlarını Windows 10 Pro yükseltme](m365bp-upgrade-windows-10-pro.md).

## <a name="secure-your-windows-10-and-11-devices"></a>Windows 10 ve 11 cihazlarınızın güvenliğini sağlama

Varsayılan olarak tüm ayarlar **Açık** durumdadır. Aşağıdaki ayarlar kullanılabilir:<br/><br/>

|Ayar  <br/> |Açıklama  <br/> |
|:-----|:-----|
|Microsoft Defender Virüsten Koruma'yı kullanarak bilgisayarları virüslerden ve diğer tehditlerden korumaya yardımcı olun  <br/> |Bilgisayarları İnternet'e bağlı olmanın tehlikelerinden korumak için Microsoft Defender Virüsten Koruma'nın açık olmasını gerektirir.  <br/> |
|Bilgisayarları Microsoft Edge'de web tabanlı tehditlere karşı korumaya yardımcı ol  <br/> |Edge'de, kullanıcıları kötü amaçlı sitelerden ve indirmelerden korumaya yardımcı olan ayarları açar.  <br/> |
|BitLocker ile PC'lerdeki dosyaların ve klasörlerin yetkisiz erişime karşı korunmasına yardımcı ol  <br/> |BitLocker, bilgisayar sabit sürücülerini şifreleyerek verileri korur ve bir bilgisayar kaybolur veya çalınırsa verilerin açığa çıkarmasını önler. Daha fazla bilgi için bkz. [BitLocker SSS](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Cihaz şu kadar süre boşta kaldığında ekranı kapat  <br/> |Kullanıcı cihaz başında olmadığında şirket verilerinin korunmasını sağlar. Kullanıcı bir kafe gibi herkese açık bir konumda çalışıyorken kısa süreliğine uzaklaşabilir veya başka bir şeyle ilgilenebilir ve bu sırada diğer kişiler cihazdaki bilgilere bakabilir. Bu ayar sayesinde, ekran kapanmadan önce kullanıcının ne kadar süre boşta olabileceğini denetleyebilirsiniz.  <br/> |

## <a name="next-objective"></a>Sonraki hedef

[Windows cihazları yönetme](m365bp-manage-windows-devices.md)
