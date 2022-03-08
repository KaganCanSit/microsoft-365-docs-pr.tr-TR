---
title: AutoPilot Profili ayarları hakkında
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: AutoPilot profilleri, kullanıcı cihazlarına Windows yüklemelerini denetlemeye yardımcı olur. Profiller, yükleme işlemini atlama gibi varsayılan ve Cortana içerir.
ms.openlocfilehash: d0b1a15ef8279234868b94ab5c16e449a54cf62f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313881"
---
# <a name="about-autopilot-profile-settings"></a>AutoPilot Profili ayarları hakkında

## <a name="autopilot-profile-settings"></a>AutoPilot profil ayarları

> [!NOTE]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

Kullanıcı cihazlarına postanın nasıl yük olduğunu Windows AutoPilot profillerini kullanabilirsiniz. Profiller aşağıdaki ayarları içerir.
  
 **Otomatik olarak ayarlanmış AutoPilot varsayılan özellikleri (gerekli):**
  
|**Ayar**|**Açıklama**|
|:-----|:-----|
|Kayıt Cortana, OneDrive OEM kaydı atla  <br/> |Kişisel ve kişisel uygulamalar gibi tüketici uygulamalarının Cortana atlar. OneDrive. Kullanıcı cihazda yerel yönetici olduğu sürece cihaz kullanıcısı bunları daha sonra yükleyebilir. Orijinal üretici kaydı atlanır çünkü cihaz diğer üretici tarafından Microsoft 365 İş Ekstra.  <br/> |
|Şirket markanız ile oturum açma deneyimi  <br/> |Şirketinizin Oturum Açma bilgilerine şirket markanızı [ekleme Microsoft 365](../setup/customize-sign-in-page.md) sayfası varsa, oturum a açmada cihaz kullanıcısı bu deneyimi edinecektir.  <br/> |
|Yapılandırılmış veya otomatik hesaplarla MDM AAD kaydı.  <br/> |Kullanıcı kimliği E-posta Azure Active Directory tarafından yönetilir ve kullanıcılar kimlik bilgileriyle Windows ve Microsoft 365 bilgileriyle Microsoft 365 İş Ekstra oturumlar.  <br/> |
   
 **İsteğe bağlı ayarlar:**
  
|**Ayar**|**Açıklama**|
|:-----|:-----|
|Gizlilik ayarlarını atla (Varsayılan olarak Kapalı)  <br/> |Bu seçenek On olarak **ayarlanırsa**, cihaz kullanıcısı cihazın lisans sözleşmelerini görmez ve ilk Windows oturum anlaşmayı kabul etmiş olur.  <br/> |
|Kullanıcının yerel yönetici olmasına izin verme  <br/> |Bu seçenek Açık olarak **ayarlanırsa**, cihaz kullanıcısı Kullanıcı Hesabı gibi hiçbir kişisel Cortana.<br/> |

## <a name="see-also"></a>Ayrıca bkz.

[kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](../security-and-compliance/secure-your-business-data.md)