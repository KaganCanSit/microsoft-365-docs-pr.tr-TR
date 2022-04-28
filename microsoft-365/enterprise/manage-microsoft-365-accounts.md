---
title: Microsoft 365 kullanıcı hesaplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Microsoft 365 kullanıcı hesaplarını yönetmeyi öğrenin.
ms.openlocfilehash: dbd1c0a3c1c6fdb10d157299552e83a77f495e3c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098350"
---
# <a name="manage-microsoft-365-user-accounts"></a>Microsoft 365 kullanıcı hesaplarını yönetme

yapılandırmanıza bağlı olarak Microsoft 365 kullanıcı hesaplarını çeşitli yollarla yönetebilirsiniz. Kullanıcı hesaplarını Microsoft 365 yönetim merkezi, [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), [Active Directory Domain Services](/admin) (AD DS) veya Azure Active Directory (Azure AD) yönetim portalında yönetebilirsiniz. 

Microsoft 365 satın aldığınız anda<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">, hesapları</a> yönetmek için Microsoft 365 yönetim merkezi ve PowerShell kullanılabilir. Bulut kimliklerini yönetirken, kuruluşunuzdaki her kişinin ayrı bir kullanıcı hesabı adı ve parolası vardır. Şirket içi altyapınızla tümleştirmek ve kullanıcı hesaplarının Microsoft 365 ile eşitlenmesini istiyorsanız, çoklu oturum açma (SSO) işlevselliği için kimliklerin ve parolaların eşitlenmesini sağlamak için Azure AD Bağlan kullanabilirsiniz.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Kullanıcı hesaplarınızı nerede ve nasıl yönetebileceğinizi planlama

Kullanıcı hesaplarınızı nerede ve nasıl yönetebileceğiniz, Microsoft 365 için kullanmak istediğiniz kimlik modeline bağlıdır. İki genel model yalnızca bulut ve hibrit modeldir.
  
### <a name="cloud-only"></a>Yalnızca bulut

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">kullanıcıları Microsoft 365 yönetim merkezi</a> oluşturur ve yönetirsiniz. PowerShell'i veya Azure AD yönetim merkezini de kullanabilirsiniz. 
    
### <a name="hybrid"></a>Karma

Kullanıcı hesapları AD DS'den Microsoft 365 ile eşitlenir, bu nedenle kullanıcı hesaplarını yönetmek için şirket içi AD DS araçlarını kullanmanız gerekir. 
    
## <a name="managing-accounts"></a>Hesapları Yönetme

Kuruluşunuzun hesapları hangi yolla oluşturup yöneteceğini belirlerken aşağıdaki gereksinimleri göz önünde bulundurun:
  
- Kimlikleri Microsoft 365 ve AD DS'niz arasında bağlamak için dizin eşitleme yazılımının şirket içi ortamınızdaki sunuculara yüklenmesi gerekir.
    
- SSO seçenekleri de dahil olmak üzere tüm dizin eşitleme seçenekleri, AD DS özniteliklerinizin standartları karşılamasını gerektirir. Dizininizde hangi özniteliklerin kullanıldığına ve hangi temizlemenin (varsa) gerekli olduğuna ilişkin ayrıntılar[, dizin eşitlemesini Microsoft 365 için hazırlama](prepare-for-directory-synchronization.md) bölümünde açıklanmıştır. 
    
- Microsoft 365 hesaplarını nasıl oluşturabileceğinizi planlayın.
    
Aşağıdaki tabloda farklı hesap yönetimi araçları listelenmektedir.
    
|Araç|Notlar|
|:-----|:-----|
|Microsoft 365 yönetici merkezi  <br/> |[Kullanıcıları tek tek veya toplu olarak ekleme](../admin/add-users/add-users.md) <br/>  Kullanıcı hesaplarını eklemek ve değiştirmek için basit bir web arabirimi sağlar.  <br/>  Dizin eşitlemesi etkinse kullanıcıları değiştirmek için kullanılamaz (konum ve lisans ataması ayarlanabilir).  <br/>  SSO seçenekleriyle kullanılamaz.  <br/> |
|Windows PowerShell  <br/> |[Windows PowerShell ile Microsoft 365 yönetme](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Windows PowerShell betiği kullanarak toplu kullanıcılara kullanıcı eklemenize olanak tanır.  <br/>  Hesapların nasıl oluşturulduğundan bağımsız olarak, hesaplara konum ve lisans atamak için kullanılabilir.  <br/> |
|Toplu içeri aktarma  <br/> |[Aynı anda birkaç kullanıcıyı ekleme](add-several-users-at-the-same-time.md) <br/>  Microsoft 365 bir kullanıcı grubu eklemek için CSV dosyasını içeri aktarmanıza olanak tanır.  <br/>  SSO seçenekleriyle kullanılamaz.  <br/> |
|Azure AD  <br/> |Microsoft 365 aboneliğinizle Azure AD'nin ücretsiz bir sürümünü alırsınız. Bulut kullanıcıları için self servis parola sıfırlama ve ücretsiz sürümü kullanarak Oturum açma ve Erişim Paneli sayfalarını özelleştirme gibi işlevleri gerçekleştirebilirsiniz. Gelişmiş işlevsellik elde etmek için temel sürüme, Azure AD Premium P1 veya Azure AD Premium P2 yükseltebilirsiniz. Desteklenen özelliklerin listesi için bkz. [Azure AD sürümleri](/azure/active-directory/fundamentals/active-directory-whatis) .  <br/> |
|Dizin eşitleme  <br/> |[Şirket içi kimliklerinizi Azure AD ile tümleştirme](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  Parola eşitleme ile veya parola eşitleme olmadan dizin eşitlemesi için hızlı [ayarlarla Azure AD Bağlan](/azure/active-directory/hybrid/how-to-connect-install-express) kullanın.  <br/>  Birden çok orman ve SSO seçeneği için [Azure AD Bağlan Özel Yüklemesi'ni](/azure/active-directory/hybrid/how-to-connect-install-custom) kullanın.  <br/>  SSO'nun etkinleştirilmesi için gereken altyapıyı sağlar.  <br/>  Aşamalı geçiş ve karma Exchange gibi birçok karma senaryo için gereklidir  <br/>  AD DS'nizden güvenlik ve posta etkin grupları eşitler.  <br/> |
|||
   
- Kullanıcı hesaplarını Microsoft 365 nasıl eklemeyi amaçladığınıza bakılmaksızın, lisans atama, konum belirtme vb. gibi çeşitli hesap özelliklerini yönetmeniz gerekir. Bu özellikler <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> uzun vadeli olarak yönetilebilir veya [PowerShell ile kullanıcı hesapları da oluşturabilirsiniz](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Yönetim merkezi aracılığıyla tüm kullanıcılarınızı eklemeyi ve yönetmeyi seçerseniz, konumu belirtir ve Microsoft 365 hesabını oluştururken lisansları aynı anda atarsınız. Sonuç olarak, çok fazla planlama gerekmez.
    
    > [!IMPORTANT]
    > Lisans atamadan (örneğin, SharePoint Online'a) Microsoft 365 hesap oluşturmak, hesap sahibinin Microsoft 365 merkezini görüntüleyebileceği ancak şirketinizin aboneliğindeki hizmetlere erişemeyecekleri anlamına gelir. Bir konum ve lisans atadıktan sonra hesap, atadığınız hizmete veya hizmetlere çoğaltılır. Kullanıcı hesabında oturum açabilir ve kendisine atadığınız hizmetleri kullanabilir. 
  
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 yönetici merkezi](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)