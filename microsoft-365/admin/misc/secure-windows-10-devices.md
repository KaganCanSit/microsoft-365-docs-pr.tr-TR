---
title: Windows 10 cihazlarının güvenliğini sağlama
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: medium
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
description: İş veya okul hesaplarında oturum Windows 10 ilgili cihaza varsayılan cihaz ilkesi ayarlarını yapılandırma hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 1a39fdad31de5e4aef2fa5bbc4995d9c4c8bbb90
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985014"
---
# <a name="secure-windows-10-devices"></a>Windows 10 cihazlarının güvenliğini sağlama

Bu makale diğer Microsoft 365 İş Ekstra.

Burada yapılandırdığınız ayarlar, Windows 10 için varsayılan cihaz ilkesinin bir parçasıdır. Mobil cihazlar ve bilgisayarlar da Windows 10 bir cihaza bağlanarak iş hesaplarıyla oturum alan tüm kullanıcılar bu ayarları otomatik olarak alır. Kurulum sırasında varsayılan ilkeyi kabul etmenizi ve daha sonra belirli kullanıcı gruplarını hedef alan ilkeler eklemenizi öneririz.
  
## <a name="settings-to-secure-windows-10-devices"></a>Windows 10 cihazlarının güvenliğini sağlayan ayarlar

Varsayılan olarak tüm ayarlar **Açık** durumdadır. Aşağıdaki ayarlar kullanılabilir:
  


|Ayar  <br/> |Açıklama  <br/> |
|:-----|:-----|
|Windows Defender Virüsten Koruma kullanarak bilgisayarların virüslere ve diğer tehditlere karşı korunmasına yardımcı ol  <br/> |Bilgisayarları internete bağlı olmanın getirdiği tehlikelerden korumak için Windows Defender Virüsten Koruma programının açık olması gerekir.  <br/> |
|Bilgisayarları Microsoft Edge'de web tabanlı tehditlere karşı korumaya yardımcı ol  <br/> |Edge'de, kullanıcıları kötü amaçlı sitelerden ve indirmelerden korumaya yardımcı olan ayarları açar.  <br/> |
|BitLocker ile PC'lerdeki dosyaların ve klasörlerin yetkisiz erişime karşı korunmasına yardımcı ol  <br/> |BitLocker bilgisayar sabit sürücülerini şifreleyerek verileri korur ve bilgisayar kaybolduğunda veya çalındığında verilerin açığa çıkma durumuna karşı koruma sağlar. Daha fazla bilgi için bkz. [Bitlocker SSS](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Cihaz şu kadar süre boşta kaldığında ekranı kapat  <br/> |Kullanıcı cihaz başında olmadığında şirket verilerinin korunmasını sağlar. Kullanıcı bir kafe gibi herkese açık bir konumda çalışıyorken kısa süreliğine uzaklaşabilir veya başka bir şeyle ilgilenebilir ve bu sırada diğer kişiler cihazdaki bilgilere bakabilir. Bu ayar sayesinde, ekran kapanmadan önce kullanıcının ne kadar süre boşta olabileceğini denetleyebilirsiniz.  <br/> |
|