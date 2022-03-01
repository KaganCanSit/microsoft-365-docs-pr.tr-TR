---
title: Adım 1. Bulut kimlik modelinizi belirleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.date: 09/30/2020
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Adım 1. Microsoft bulut kimlik modelinizi belirleme
ms.openlocfilehash: 2f9527b05a688b27304529634a75db4ef8a1b07d
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016469"
---
# <a name="step-1-determine-your-cloud-identity-model"></a>Adım 1. Bulut kimlik modelinizi belirleme

Microsoft 365, Azure Active Directory kimlikleri ve kimlik doğrulamasını yönetmek için Microsoft 365 aboneliğinize dahil bulut tabanlı bir kullanıcı kimliği ve kimlik doğrulama hizmeti olan Microsoft 365. Kimlik altyapınızı doğru şekilde yapılandırmak, kullanıcıların erişimini Microsoft 365 izinlerini yönetme açısından çok önemlidir.

Başlamadan önce, kimlik modellarına ve kimlik doğrulamasına genel bir bakış için bu videoyu Microsoft 365.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

İlk planlama seçiminiz bulut kimlik modelinizdir.

## <a name="microsoft-cloud-identity-models"></a>Microsoft bulut kimlik modelleri

Kullanıcı hesaplarını planlamak için öncelikle kullanıcı profili profilinde yer alan iki kimlik Microsoft 365. Kuruluş kimliklerini yalnızca bulutta bulundurabilirsiniz veya şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) kimliklerinizi koruyabilirsiniz ve kullanıcılar bulut hizmetlerinde bulut hizmetleriyle erişim sağlarken kimlik doğrulaması Microsoft 365 kullanabilirsiniz.

İki kimlik türü ve bu kimlik türüne en uygun ve avantajları burada ve şekildedir.

| Öznitelik | Yalnızca bulut kimliği | Karma kimlik |
|:-------|:-----|:-----|
| **Tanım** | Kullanıcı hesabı, yalnızca Azure AD kiracısı'nın içinde Microsoft 365 vardır. | Kullanıcı hesabı AD DS'de yer alır ve bu hesabın bir kopyası da Microsoft 365 olur. Azure AD'de kullanıcı hesabı, zaten karma olarak karma olarak karma bir AD DS kullanıcı hesabı parolasının karma sürümünü de içerebilir. |
| **Kullanıcı Microsoft 365 kimlik doğrulaması nasıl olur?** | Aboneliğiniz için Azure AD kiracısı Microsoft 365, bulut kimlik hesabıyla kimlik doğrulamasını gerçekleştirir. | Microsoft 365 aboneliğiniz için Azure AD kiracısı, kimlik doğrulama işlemini ele alır veya başka bir kimlik sağlayıcısına yeniden yönlendirebilir. |
| **En iyi** | Şirket içi AD DS'si olmayan veya bu kuruluşlara gerek olmayan kuruluşlar. | AD DS veya başka bir kimlik sağlayıcısı kullanan kuruluşlar. |
| **En büyük avantaj** | Kullanımı kolaydır. Fazladan dizin aracı veya sunucu gerekmez. | Kullanıcılar, şirket içi veya bulut tabanlı kaynaklara erişirken aynı kimlik bilgilerini kullanabilir. |
||||

## <a name="cloud-only-identity"></a>Yalnızca bulut kimliği

Yalnızca bulut kimliği, yalnızca Azure AD'de var olan kullanıcı hesaplarını kullanır. Yalnızca bulut kimliği normalde şirket içi sunucuları olmayan veya yerel kimlikleri yönetmek için AD DS kullanmayan küçük kuruluşlar tarafından kullanılır.

Burada, yalnızca bulut kimliğinin temel bileşenleri ve bilgileri ve bilgileri ve hizmetleri ve diğer bileşenleri ve daha sonralarını açıklarız.

![Yalnızca bulut kimliğinin temel bileşenleri.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Hem şirket içi hem de uzak (çevrimiçi) kullanıcılar Azure AD kullanıcı hesaplarını ve parolalarını kullanarak bulut Microsoft 365 kullanırlar. Azure AD, depolanan kullanıcı hesaplarına ve parolalarına göre kullanıcı kimlik bilgilerini doğrular.

### <a name="administration"></a>Yönetim
Kullanıcı hesapları yalnızca Azure AD'de depolandığı için bulut kimliklerini kimlik bilgileri ve kimlik bilgileri gibi [araçlarla Microsoft 365 yönetim merkezi](/admin) [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).

## <a name="hybrid-identity"></a>Karma kimlik

Karma kimlik, şirket içi AD DS'den gelen hesapları kullanır ve bu hesapların Azure AD kiracısına bir kopyasını Microsoft 365 olur. Çoğu değişiklikte, belirli hesap [öznitelikleri dışında, tek](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized) bir yolla akışı sağlar. AD DS kullanıcı hesaplarında yaptığınız değişiklikler, Azure AD'nin kopyasıyla eşitlenir.

Azure AD Bağlan sürekli hesap eşitlemesini sağlar. Şirket içi bir sunucuda çalışır, AD DS'de yapılan değişiklikleri denetler ve bu değişiklikleri Azure AD'ye iletir. Azure AD Bağlan, hangi hesapların eşitleneceklerini ve parola karması eşitlemesi (PHS) olarak bilinen karma kullanıcı parolalarının karma sürümünün eşitlenip eşitlenmeyebilmelerini sağlayan bir özelliktir.

Karma kimlikler hesaplarken, hesap bilgisinin yetkili kaynağı şirket içi AD DS'nizdir. Bu, çoğunlukla şirket içi olan ve ardından Azure AD ile eşitlenen yönetim görevlerini gerçekleştirin anlamına gelir.

Karma kimliğin bileşenleri aşağıdaki gibidir.

![Karma kimliğin bileşenleri.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD kiracısı, AD DS hesaplarının bir kopyasına sahip. Bu yapılandırmada, hem şirket içi hem de azure ad Microsoft 365 uzak kullanıcılar Azure AD'de kimlik doğrulaması kullanır.

> [!NOTE]
> Karma kimlikle ilgili kullanıcı hesaplarını eşitlemek Bağlan için her zaman Azure AD Bağlan'i kullanasınız. Lisans atamasını ve grup yönetimini gerçekleştirmek, izinleri yapılandırmak ve kullanıcı hesaplarını içeren diğer yönetim görevlerini gerçekleştirmek için Azure AD'de eşitlenmiş kullanıcı hesaplarına ihtiyacınız vardır.

### <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Etki alanı için karma kimlik ve dizin Microsoft 365

İş gereksinimlerinize ve teknik gereksinimlerinize bağlı olarak, karma kimlik modeli ve dizin eşitlemesi, kurumsal müşterileri benimsemek için en yaygın Microsoft 365. Dizin eşitlemesi, Active Directory Etki Alanı Hizmetleri'nizin (AD DS) kimliklerini yönetmenize olanak sağlar ve kullanıcı hesapları, gruplar ve kişilerde yapılan tüm güncelleştirmeler Azure Active Directory (Azure AD) kiracısına Microsoft 365 eşitlenir.

>[!Note]
>AD DS kullanıcı hesapları ilk kez eşitlenirken, bu hesaplara otomatik olarak Microsoft 365 lisansı atanamaz ve e-Microsoft 365 hizmetlere erişamaz. Öncelikle onlara bir kullanım konumu atamalısiniz. Ardından, bu kullanıcı hesaplarına tek tek veya grup üyeliği aracılığıyla dinamik olarak lisans attayabilirsiniz.
>

#### <a name="authentication-for-hybrid-identity"></a>Karma kimlik için kimlik doğrulaması

Karma kimlik modelini kullanırken iki tür kimlik doğrulama vardır:

- Yönetilen kimlik doğrulaması

  Azure AD, parolanın yerel olarak depolanan karma bir sürümünü kullanarak kimlik doğrulama işlemini ele alır veya kimlik bilgilerini şirket içi AD DS tarafından kimlik doğrulaması yapılan bir şirket içi yazılım aracısına gönderir.

- Federasyon kimlik doğrulaması

  Azure AD, kimlik doğrulaması talep etmek için istemci bilgisayarı başka bir kimlik sağlayıcısına yeniden yönlendirmektedir.

#### <a name="managed-authentication"></a>Yönetilen kimlik doğrulaması

İki tür yönetilen kimlik doğrulaması vardır:

- Parola karması eşitlemesi (PHS)

  Azure AD, kimlik doğrulamayı kendisinin gerçekleştirir.

- Geçişli kimlik doğrulaması (PTA)

  Azure AD'nin kimlik doğrulamayı gerçekleştirmesi için AD DS vardır.


##### <a name="password-hash-synchronization-phs"></a>Parola karması eşitlemesi (PHS)

PHS ile AD DS kullanıcı hesaplarınızı diğer kullanıcılarla Microsoft 365 ve kullanıcılarınızı şirket içinde yönetirsiniz. Kullanıcıların şirket içinde ve bulutta aynı parolaya sahip olması için kullanıcı parolaları karmaları AD DS'niz ile Azure AD'ye eşitlenir. Bu, Azure AD'de AD DS kimlikleri için kimlik doğrulamayı etkinleştirmenin en basit yolu. 

![Parola karması eşitlemesi (PHS).](../media/plan-for-directory-synchronization/phs-authentication.png)

Parolalar şirket içinde değiştir olduğunda veya sıfır olduğunda, kullanıcılarının bulut kaynakları ve şirket içi kaynaklar için her zaman aynı parolayı kullanamalarını sağlamaları için yeni parola karmaları Azure AD'ye eşitlenir. Kullanıcı parolaları hiçbir zaman Azure AD'ye gönderilmez veya Azure AD'de temiz metin olarak depo saklanmaz. Azure AD'nin Kimlik Koruması gibi bazı ekstra özellikleri, hangi kimlik doğrulama yönteminin seçilecek olursa olsun PHS gerektirir.
  
Daha [fazla bilgi edinmek için bkz. doğru](/azure/active-directory/hybrid/choose-ad-authn) kimlik doğrulama yöntemini seçme.
  
##### <a name="pass-through-authentication-pta"></a>Geçişli kimlik doğrulaması (PTA)

PTA, kullanıcıların doğrudan AD DS'niz ile doğrulanması için bir veya birden çok şirket içi sunucu üzerinde çalışan yazılım aracısını kullanarak Azure AD kimlik doğrulama hizmetleri için basit parola doğrulaması sağlar. PTA ile AD DS kullanıcı hesaplarını diğer kullanıcılarla Microsoft 365 ve kullanıcılarınızı şirket içinde yönetirsiniz. 

![Geçişli kimlik doğrulaması (PTA).](../media/plan-for-directory-synchronization/pta-authentication.png)

PTA, kullanıcılarının şirket içi hesaplarını ve parolalarını kullanarak hem şirket içi Microsoft 365 kaynak ve uygulamalarda oturum açmalarına olanak sağlar. Bu yapılandırma, azure ad'de parola karmaları depolamadan kullanıcı parolalarını doğrudan şirket içi AD DS'niz ile doğrular. 

PTA, güvenlik gereksinimi olan kuruluşlarda şirket içi kullanıcı hesabı durumları, parola ilkeleri ve oturum açma saatlerini hemen zorunlu kılmalıdır. 
  
Daha [fazla bilgi edinmek için bkz. doğru](/azure/active-directory/hybrid/choose-ad-authn) kimlik doğrulama yöntemini seçme.
  
##### <a name="federated-authentication"></a>Federasyon kimlik doğrulaması

Federasyon kimlik doğrulaması öncelikli olarak, daha karmaşık kimlik doğrulama gereksinimleri olan büyük kurumsal kuruluşlar için kullanılır. AD DS kimlikleri kullanıcı hesaplarıyla Microsoft 365 ve kullanıcı hesapları da şirket içinde yönetilir. Şirket içi kimlik doğrulamasıyla, kullanıcıların şirket içinde ve buluttaki parolaları aynı olur ve şirket içi parolayı kullanmak için yeniden oturum açmaları Microsoft 365. 

Federasyon kimlik doğrulaması, akıllı kart tabanlı kimlik doğrulaması veya üçüncü taraf çok faktörlü kimlik doğrulaması gibi ek kimlik doğrulama gereksinimlerini destekleyenin ve kuruluşlar Azure AD tarafından yerel olarak desteklenen bir kimlik doğrulama gereksinimine sahip olduğunda genellikle gereklidir.
 
Daha [fazla bilgi edinmek için bkz. doğru](/azure/active-directory/hybrid/choose-ad-authn) kimlik doğrulama yöntemini seçme.
  
Üçüncü taraf kimlik doğrulama ve kimlik sağlayıcıları için, şirket içi dizin nesneleri öncelikli olarak üçüncü taraf kimlik sağlayıcısı (IdP) tarafından yönetilen Microsoft 365 ve bulut kaynağı erişimiyle eşitlenebiliyor olabilir. Organizasyonunuz üçüncü taraf federasyon çözümü kullanıyorsa, üçüncü taraf federasyon çözümünün Azure AD ile uyumlu olması Microsoft 365 bu çözümle oturum açma ayarlarını yapılandırabilirsiniz.
  
Daha fazla [bilgi edinmek için bkz. Azure AD](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) federasyon uyumluluk listesi.
  
### <a name="administration"></a>Yönetim

Özgün ve yetkili kullanıcı hesapları şirket içi AD DS'de depolandığı için, kimliklerinizi AD DS'nizi yönetirken aynı araçlarla yönetirsiniz.

Azure AD'de eşitlenmiş kullanıcı Microsoft 365 yönetim merkezi yönetmek için Microsoft 365 veya Microsoft 365 PowerShell'i kullanmazsınız.

## <a name="next-step"></a>Sonraki adım

[![Ayrıcalıklı Microsoft 365 hesaplarınızı koruma](../media/deploy-identity-solution-overview/protect-your-global-administrator-accounts.png)](protect-your-global-administrator-accounts.md)

Genel yönetici [hesaplarınızı güvence altına](protect-your-global-administrator-accounts.md) almak için 2. Adımdan devam edin.
