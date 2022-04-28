---
title: dizin eşitleme durumunu Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, Office 365'da dizin eşitlemenizin durumunu nasıl denetleyeceğinizi öğrenin.
ms.openlocfilehash: 8f21985f8db3539e8dd1a839cc6cb499a425feeb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095564"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>dizin eşitleme durumunu Microsoft 365

Şirket içi ortamınızı Microsoft 365 ile eşitleyerek şirket içi Active Directory Etki Alanı Hizmetlerinizi (AD DS) Azure Active Directory (Azure AD) ile tümleştirdiyseniz, eşitlemenizin durumunu da de kontrol edebilirsiniz.
  
## <a name="view-directory-synchronization-status"></a>Dizin eşitleme durumunu görüntüleme

- [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın ve giriş sayfasında **DirSync Durumu'nu** seçin.
- Alternatif olarak, **Kullanıcılar** \> **Etkin kullanıcılar'a** gidebilir ve **Etkin kullanıcılar** sayfasında **Diğer** \> **Dizin eşitlemesi'ni** seçebilirsiniz. **Dizin Eşitleme** bölmesinde **DirSync yönetimine git'i** seçin.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Dizin eşitlemesini yönet sayfasındaki bilgiler

Aşağıdaki tabloda, sayfada hakkında bilgi alabileceğiniz özellikler listelenmiştir.
  
Dizin eşitlemenizle ilgili bir sorun varsa, hatalar bu sayfada da listelenir. Karşılaşabileceğiniz farklı hatalar hakkında daha fazla bilgi için bkz. [Microsoft 365 dizin eşitleme hatalarını belirleme](identify-directory-synchronization-errors.md).
  
|Öğe|Kullanım amacı|
|:-----|:-----|
|**Doğrulanan etki alanları** | sahip olduğunuzu doğruladığınız Microsoft 365 kiracınızdaki etki alanı sayısı. |
|**Etki alanları doğrulanmadı** | Eklediğiniz ancak doğrulanmamış etki alanları. |
|**Dizin eşitleme etkin** |Doğru veya Yanlış. Dizin eşitlemeyi etkinleştirip etkinleştirmediğiniz belirtir. |
|**En son dizin eşitleme** | Dizin eşitlemenin son çalıştırışı. Son eşitleme üç günden uzun bir süre önceyse bir uyarı ve sorun giderme aracının bağlantısını görüntüler. |
|**Parola eşitleme etkin** | Doğru veya Yanlış. Şirket içi ile Microsoft 365 kiracınız arasında parola karması eşitlemesi yapıp yapmadığınızı belirtir. |
|**Son Parola Eşitleme** | Parola karması eşitlemenin son çalıştırışı. Son eşitleme üç günden uzun bir süre önceyse bir uyarı ve sorun giderme aracının bağlantısını görüntüler. |
|**Dizin eşitleme istemcisi sürümü** | Azure AD Bağlan'nin yeni bir sürümü yayımlandıysa indirme bağlantısı içerir. |
|**Dizin eşitleme hizmeti hesabı** | Microsoft 365 dizin eşitleme hizmeti hesabınızın adını görüntüler. |
|||

## <a name="monitor-synchronization-health"></a>Eşitleme durumunu izleme

Bu bölümde, kimlik altyapınızı ve Azure AD Bağlan tarafından sağlanan eşitleme hizmetlerini izlemek için şirket içi AD DS etki alanı denetleyicilerinizin her birine bir Azure AD Bağlan Health aracısı yükleyeceksiniz. İzleme bilgileri, uyarıları, performans izlemeyi, kullanım analizini ve diğer bilgileri görüntüleyebileceğiniz bir Azure AD Bağlan Health portalında sağlanır.

Azure AD Bağlan Health'in nasıl kullanılacağına ilişkin temel tasarım kararı, Azure AD Bağlan nasıl kullandığınıza bağlıdır:

- **Yönetilen kimlik doğrulama** seçeneğini kullanıyorsanız Azure AD Bağlan Health'i anlamak ve yapılandırmak için Azure [AD Bağlan Health'i eşitleme ile kullanma](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) ile başlayın.
- Active Directory Federasyon Hizmetleri (AD FS) (AD FS) ile **federasyon kimlik doğrulaması** kullanarak hesapların ve grupların yalnızca adlarını eşitlerseniz, [Azure AD Bağlan Health'i anlamak ve yapılandırmak için AD FS ile Azure AD Bağlan Health kullanma ile](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) başlayın.

Tamamlandığında şunları yapacaksınız:

- Şirket içi kimlik sağlayıcısı sunucularınıza yüklenen Azure AD Bağlan Health aracısı.
- Microsoft 365 aboneliğiniz için Azure AD kiracısıyla şirket içi altyapınızın ve eşitleme etkinliklerinizin geçerli durumunu görüntüleyen Azure AD Bağlan Health portalı.