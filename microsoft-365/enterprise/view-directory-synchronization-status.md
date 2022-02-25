---
title: Eşitleme görünümünde dizin eşitlemesi Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Bu makalede, microsoft iş yerizsinde dizin eşitlemenizin durumunu nasıl Office 365.
ms.openlocfilehash: 0cc5b5244c5809d3f1b13b15b200bd8cea585c7c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959929"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Eşitleme görünümünde dizin eşitlemesi Microsoft 365

Şirket içi ortamınızı Microsoft 365 ile eşitleyerek şirket içi Active Directory Etki Alanı Hizmetleri'nizi (AD DS) Azure Active Directory (Azure AD) ile tümleştirdıysanız, eşitlemenizin durumunu da kontrol edin.
  
## <a name="view-directory-synchronization-status"></a>Dizin eşitleme durumunu görüntüleme

- E-Microsoft 365 yönetim merkezi [giriş sayfasında](https://admin.microsoft.com) **DirSync Durumu'ne** tıklayın.
- Alternatif olarak, Kullanıcılar Etkin **kullanıcılar'a** \> **gidebilir** ve Etkin kullanıcılar sayfasında **Diğer Dizin** **eşitlemesi'ne** \> **seçebilirsiniz**. Dizin **Eşitlemesi bölmesinde** **DirSync yönetimine git'i seçin**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Dizin eşitlemesini yönet sayfasındaki bilgiler

Aşağıdaki tabloda, sayfa hakkında bilgi edinebilirsiniz özellikler listeledik.
  
Dizin eşitlemeniz ile ilgili bir sorun varsa, hatalar da bu sayfada listelenir. Karşılaş karşılaşabilirsiniz farklı hatalar hakkında daha fazla bilgi için bkz. Bu [hatalarda dizin eşitleme Microsoft 365](identify-directory-synchronization-errors.md).
  
|Öğe|Kullanım amacı|
|:-----|:-----|
|**Doğrulanan etki alanları** | Etki alanı kiracınız içinde Microsoft 365 sahip olduğunu doğruladığınız etki alanı sayısı. |
|**Doğrulanmamış etki alanları** | Kendi ekledik ancak doğrulanmamış etki alanları. |
|**Dizin eşitlemesi etkin** |Doğru veya Yanlış. Dizin eşitlemeyi etkinleştirip etkinleştirmediysenizi belirtir. |
|**En son dizin eşitlemesi** | Dizin eşitlemesi en son ne zaman başladı? Son eşitlemenin üç gün öncesine kadar olan bir uyarı ve sorun giderme aracının bağlantısı görüntülenir. |
|**Parola eşitlemesi etkin** | Doğru veya Yanlış. Bizim şirket içi parola karma eşitlemeniz ile kiracınız arasında parola karma eşitlemesi Microsoft 365 belirtir. |
|**Son Parola Eşitlemesi** | Parola karma eşitlemesi en son ne zaman başladı? Son eşitlemenin üç gün öncesine kadar olan bir uyarı ve sorun giderme aracının bağlantısı görüntülenir. |
|**Dizin eşitleme istemcisi sürümü** | Azure AD'nin yeni bir sürümü yayınlandı Bağlan indirme bağlantısı içerir. |
|**Dizin eşitleme hizmeti hesabı** | Dizin eşitleme hizmeti Microsoft 365 adını görüntüler. |
|||

## <a name="monitor-synchronization-health"></a>Eşitleme durumunu izleme

Bu bölümde, kimlik altyapınızı ve Azure AD Bağlan tarafından sağlanan eşitleme hizmetlerini izlemek için şirket içi AD DS etki alanı denetleyicilerinizin her bir bölümüne bir Azure AD Bağlan Health aracısı Bağlan. İzleme bilgileri, uyarıları, performansı izleme, kullanım Bağlan ve diğer bilgileri görüntüley yeri olan Azure AD Bağlan Health portalında kullanılabilir.

Azure AD Bağlan Health'in nasıl kullanımına ilişkin temel tasarım kararı, Azure AD Bağlan:

- Yönetilen kimlik doğrulama seçeneğini **kullanıyorsanız**, Azure AD kimlik durumunu anlamak ve yapılandırmak için [Azure AD Bağlan Health'i](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) eşitlemeyle kullanma ile Bağlan kullanın.
- Active Directory Federasyon Hizmetleri (AD FS) ile federasyon kimlik doğrulaması kullanarak yalnızca hesapların ve grupların adlarını eşitlerken, Azure AD Bağlan Health'i anlamak ve yapılandırmak için [Azure AD Bağlan Health'i AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) ile kullanma ile çalışmaya başlama.

Tamamlandığında şunları sahip oluruz:

- Azure AD Bağlan hizmet durumu aracısı şirket içi kimlik sağlayıcısı sunucularına yüklenmiştir.
- Microsoft 365 aboneliği Bağlan niz için Azure AD kiracısı ile şirket içi altyapı ve eşitleme etkinliklerinizin geçerli durumunu gösteren Azure AD Microsoft 365 portalı.