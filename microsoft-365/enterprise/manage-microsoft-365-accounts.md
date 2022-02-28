---
title: Kullanıcı Microsoft 365 hesaplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Kullanıcı hesaplarını yönetmeyi Microsoft 365 öğrenin.
ms.openlocfilehash: 7f75c74984ce58a8b403f01948075b185047f260
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977674"
---
# <a name="manage-microsoft-365-user-accounts"></a>Kullanıcı Microsoft 365 hesaplarını yönetme

Kullanıcı hesaplarını Microsoft 365 yapılandırmanıza bağlı olarak birkaç farklı şekilde yönetebilirsiniz. Kullanıcı hesaplarını [Microsoft 365 yönetim merkezi,](/admin) [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), Active Directory Etki Alanı Hizmetleri'nden (AD DS) veya Azure Active Directory (Azure AD) yönetim portalında yönetebilirsiniz. 

Microsoft 365 satın Microsoft 365 yönetim merkezi hesapları yönetmek için Microsoft 365 yönetim merkezi PowerShell kullanılabilir.<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> Bulut kimliklerini yönetmeye çalışan herkes, ayrı bir kullanıcı hesabı adına ve parolaya sahip olur. Şirket içi altyapınızı tümleştirin ve Microsoft 365 ile eşitlenmiş kullanıcı hesaplarınız varsa, çoklu oturum açma (SSO) işlevselliği için kimliklerin ve parolaların eşitlenmesi sağlamak üzere Azure AD Bağlan'i kullanabilirsiniz.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Kullanıcı hesaplarınızı nerede ve nasıl yöneteceklerinizi planlama

Kullanıcı hesaplarınızı nasıl ve nerede yönetebilirsiniz, kullanıcı hesaplarınız için kullanmak istediğiniz kimlik modeline Microsoft 365. Genel olarak iki model yalnızca bulut ve karmadır.
  
### <a name="cloud-only"></a>Yalnızca bulut

Kullanıcı oluşturmak ve yönetmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi.</a> PowerShell'i veya Azure AD yönetim merkezini de kullanabilirsiniz. 
    
### <a name="hybrid"></a>Karma

Kullanıcı hesapları AD DS'Microsoft 365 hesaplarla eşitlenir, dolayısıyla kullanıcı hesaplarını yönetmek için şirket içi AD DS araçlarını kullansanız gerekir. 
    
## <a name="managing-accounts"></a>Hesapları Yönetme

Kuruluşta hangi yolla hesap oluşturulacak ve yönetecek karar verirken aşağıdaki gereksinimleri göz önünde bulundurabilirsiniz:
  
- Kimlikleri Microsoft 365 AD DS'niz arasında bağlamak için, dizin eşitleme yazılımının şirket içi ortamınız içindeki sunuculara yüklenmiş olması gerekir.
    
- SSO seçenekleri de dahil olmak üzere herhangi bir dizin eşitleme seçeneği AD DS özniteliklerinizin standartlara uygun olduğunu gerektirir. Dizinde kullanılan öznitelikler ve varsa temizleme (varsa) özellikleri, Dizin eşitlemesi için gerekli temizleme (varsa) bilgileri Dizin eşitlemesi için gerekli [Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Yeni hesap oluşturma Microsoft 365 planla.
    
Aşağıdaki tabloda farklı hesap yönetim araçları listelemektedir.
    
|Araç|Notlar|
|:-----|:-----|
|Microsoft 365 yönetici merkezi  <br/> |[Kullanıcıları tek tek veya toplu olarak ekleme](../admin/add-users/add-users.md) <br/>  Kullanıcı hesaplarını eklemek ve değiştirmek için basit bir web arabirimi sağlar.  <br/>  Dizin eşitleme etkinleştirildiyse kullanıcıları değiştirmek için kullanılamaz (konum ve lisans ataması ayarlanmış olabilir).  <br/>  SSO seçenekleriyle kullanılamaz.  <br/> |
|Windows PowerShell  <br/> |[Microsoft 365 ile Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Bir kullanıcı betiği kullanarak kullanıcıları toplu olarak Windows PowerShell sağlar.  <br/>  Hesapların nasıl oluşturulduklarından bağımsız olarak, hesaplara konum ve lisans atamak için kullanılabilir.  <br/> |
|Toplu içeri aktarma  <br/> |[Aynı anda birkaç kullanıcı ekleme](add-several-users-at-the-same-time.md) <br/>  Verilerinize bir grup kullanıcı eklemek için CSV dosyasını içeri aktarmanıza olanak Microsoft 365.  <br/>  SSO seçenekleriyle kullanılamaz.  <br/> |
|Azure AD  <br/> |Microsoft 365 aboneliğiniz ile Azure AD'nin ücretsiz Microsoft 365 alırsınız. Bulut kullanıcıları için self servis parola sıfırlama ve ücretsiz sürümü kullanarak Oturum açma ve Erişim Paneli sayfalarını özelleştirme gibi işlevleri gerçekleştirebilirsiniz. Gelişmiş işlevsellik elde etmek için temel sürüme, özelliklere veya Azure AD Premium P1 sürümüne Azure AD Premium P2. Desteklenen [özellikler listesi için bkz. Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) sürümleri.  <br/> |
|Dizin eşitlemesi  <br/> |[Şirket içi kimliklerinizi Azure AD ile tümleştirme](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  Parola eşitlemesi olan veya olmayan dizin eşitlemesi için [Azure AD'yi hızlı Bağlan ayarlarıyla birlikte kullanın](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  Birden çok orman ve SSO seçeneği için Azure [AD'nin Özel Yüklemesi'Bağlan](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  SSO'nun etkin olduğu altyapıyı sağlar.  <br/>  Aşamalı geçiş ve karma senaryo gibi birçok karma senaryo için Exchange  <br/>  AD DS'nizin güvenlik ve posta özellikli gruplarını eşitler.  <br/> |
|||
   
- Kullanıcı hesaplarını Microsoft 365'e nasıl eklemek istediğinizden bağımsız olarak, lisans atama, konum belirtme gibi çeşitli hesap özelliklerini yönetmeniz gerekir. Bu özellikler ilk kullanıcılardan uzun vadeli olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> ayrıca [PowerShell ile kullanıcı hesapları da oluşturabilirsiniz](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Tüm kullanıcılarınızı yönetim merkezi aracılığıyla eklemeye ve yönetmeye seçerseniz, konum belirtme ve lisans atama aynı anda Microsoft 365 gerekir. Sonuç olarak, çok fazla planlama gerekmez.
    
    > [!IMPORTANT]
    > Microsoft 365'te hesap oluşturmak (örneğin, SharePoint Online'a) atamadan hesap sahibinin Microsoft 365 merkezini görüntül olabilir ancak şirketin aboneliği kapsamındaki hizmetlerden herhangi bir'e erişe almay olduğu anlamına gelir. Konumu ve lisansı atadikten sonra hesap, atadığınız hizmete veya hizmetlere çoğaltılır. Kullanıcı, hesabında oturum açın ve ona atadınız hizmetleri kullanabilir. 
  
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 yönetici merkezi](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)