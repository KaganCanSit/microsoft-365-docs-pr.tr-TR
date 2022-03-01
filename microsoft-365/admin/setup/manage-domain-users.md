---
title: Etki alanı kullanıcılarını eşitleme Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom:
- Adm_O365
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
description: Etki alanı denetimli kullanıcıları Microsoft 365 eşitleme.
ms.openlocfilehash: e49a3095cff77692e58d1b70ca1169dc8fd4802a
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010781"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Etki alanı kullanıcılarını eşitleme Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Dizin Eşitlemesi'ne Hazırlanma 

Kullanıcılarınızı ve bilgisayarlarınızı yerel Active Directory Etki Alanı'dan eşitlemeden önce Dizin eşitlemesi için hazırlanma'yi gözden [Microsoft 365](../../enterprise/prepare-for-directory-synchronization.md). Özellikle:

   - Aşağıdaki öznitelikler için dizinde yinelenen değerler ( **mail**, **proxyAddresses** ve **userPrincipalName**) yoktur. Bu değerlerin benzersiz olması ve tüm yinelenenlerin kaldırılması gerekir.
   
   - Her yerel kullanıcı hesabı için **userPrincipalName** (UPN) özniteliğini, lisanslı kullanıcıya karşılık gelen birincil e-posta adresiyle eş olacak şekilde Microsoft 365 öneririz. Örneğin: *mary.shelley@contoso.com.local yerine mary@contoso.* 
   
   - Active Directory etki alanı .*com* veya *.org* gibi İnternet'e yönlendirilebilir bir sonek yerine *.local* veya *.lan* gibi yönlendirilebilir olmayan bir sonekle bitiyorsa, öncelikle Dizin eşitlemesi için yönlendirilebilir olmayan bir etki alanını hazırlama konusunda açıklandığı gibi yerel kullanıcı hesaplarının UPN soneki'ne [ayarlayın.](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md) 

Aşağıdaki **dört.** adımda (4) IdFix'i çalıştır, şirket içi Active Directory'nizin dizin eşitlemeye hazır olduğundan da emin olur.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Azure AD E-postası'nın yükleme Bağlan

Kullanıcılarınızı, gruplarınızı ve kişilerinizi yerel Active Directory'den başka bir Azure Active Directory eşitlemek için Azure Active Directory Bağlan eşitlemesini yükleyin ve ayarlayın. 

 1. Yönetim merkezinde [, sol](https://go.microsoft.com/fwlink/p/?linkid=2024339) **gezintiden** Kurulum'u seçin.

 2. Oturum **açma ve güvenlik'in altında** Kullanıcıları **Microsoft hesabınıza ekleyin veya eşitle'yi seçin**.

 3. **Kullanıcıları Microsoft hesabınıza ekleyin veya eşitle sayfasında,** **Başla'ya tıklayın**.

 4. İlk adımda, IdFix aracını çalıştırarak Dizin eşitlemeye hazırlanmak için.

 5. Azure AD E-posta aboneliğini indirmek Bağlan sihirbaz adımlarını izleyin ve bu adımları kullanarak etki alanı denetimli kullanıcılarınızı eşitlemek Microsoft 365.


Daha [fazla bilgi edinmek için bkz. Microsoft 365](../../enterprise/set-up-directory-synchronization.md) eşitlemeyi ayarlama.

Azure AD Bağlan için seçeneklerinizi yapılandırken, parola eşitlemesini **, Sorunsuz** Çoklu Oturum Açma özelliğini ve aynı zamanda Microsoft 365 İş için Microsoft'ta da desteklenen  parola geri yazma özelliğini etkinleştirmenizi öneririz.

> [!NOTE]
> Azure AD'de parola geri yazmanın, Azure AD'de onay kutusunun ötesinde bazı ek Bağlan. Daha fazla bilgi için bkz [. Nasıl yapılandırılır: parola geri yazma](/azure/active-directory/authentication/howto-sspr-writeback). 

Etki alanına katılmış cihazları da Windows 10, karma bir Azure AD Join ayarlamak için bkz. Etki alanına katılmış [Windows 10](manage-windows-devices.md) cihazlarının Microsoft 365 İş Ekstra tarafından yönetillerini etkinleştirme.
