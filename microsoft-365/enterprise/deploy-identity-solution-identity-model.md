---
title: Adım 1. Bulut kimlik modelinizi belirleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Adım 1. Microsoft bulut kimliği modelinizi belirleme
ms.openlocfilehash: 41604ebb08104f802e33023763e9771d2b6acfda
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101281"
---
# <a name="step-1-determine-your-cloud-identity-model"></a>Adım 1. Bulut kimlik modelinizi belirleme

Microsoft 365, Microsoft 365 kimliklerini ve kimlik doğrulamasını yönetmek için Microsoft 365 aboneliğinize dahil olan bulut tabanlı bir kullanıcı kimliği ve kimlik doğrulama hizmeti olan Azure Active Directory (Azure AD) kullanır. Kimlik altyapınızı doğru şekilde yapılandırmak, kuruluşunuz için Microsoft 365 kullanıcı erişimini ve izinlerini yönetmek için çok önemlidir.

Başlamadan önce kimlik modellerine ve Microsoft 365 kimlik doğrulamasına genel bir bakış için bu videoyu izleyin.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

İlk planlama tercihiniz bulut kimliği modelinizdir.

## <a name="microsoft-cloud-identity-models"></a>Microsoft bulut kimliği modelleri

Kullanıcı hesaplarını planlamak için önce Microsoft 365'deki iki kimlik modeli anlamanız gerekir. Kuruluşunuzun kimliklerini yalnızca bulutta koruyabilir veya şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) kimliklerinizi koruyabilir ve kullanıcılar Microsoft 365 bulut hizmetlerine eriştiğinde kimlik doğrulaması için kullanabilirsiniz.

İki kimlik türü ve bunların en uygun ve avantajlarını aşağıda bulabilirsiniz.

| Öznitelik | Yalnızca bulut kimliği | Karma kimlik |
|:-------|:-----|:-----|
| **Tanım** | Kullanıcı hesabı yalnızca Microsoft 365 aboneliğiniz için Azure AD kiracısında bulunur. | Kullanıcı hesabı AD DS'de var ve bir kopyası da Microsoft 365 aboneliğinizin Azure AD kiracısında yer alır. Azure AD'deki kullanıcı hesabı, zaten karma ad DS kullanıcı hesabı parolasının karma sürümünü de içerebilir. |
| **Microsoft 365 kullanıcı kimlik bilgilerinin kimliğini nasıl doğrular?** | Microsoft 365 aboneliğinizin Azure AD kiracısı, kimlik doğrulamasını bulut kimliği hesabıyla gerçekleştirir. | Microsoft 365 aboneliğinizin Azure AD kiracısı, kimlik doğrulama işlemini gerçekleştirir veya kullanıcıyı başka bir kimlik sağlayıcısına yönlendirir. |
| **Için en iyi** | Şirket içi AD DS'ye sahip olmayan veya buna ihtiyacı olmayan kuruluşlar. | AD DS veya başka bir kimlik sağlayıcısı kullanan kuruluşlar. |
| **En büyük avantaj** | Kullanımı basit. Ek dizin araçları veya sunucuları gerekmez. | Kullanıcılar şirket içi veya bulut tabanlı kaynaklara erişirken aynı kimlik bilgilerini kullanabilir. |
||||

## <a name="cloud-only-identity"></a>Yalnızca bulut kimliği

Yalnızca bulut kimliği, yalnızca Azure AD'de bulunan kullanıcı hesaplarını kullanır. Yalnızca bulut kimliği genellikle şirket içi sunucuları olmayan veya yerel kimlikleri yönetmek için AD DS kullanmayan küçük kuruluşlar tarafından kullanılır.

Burada yalnızca bulut kimliğinin temel bileşenleri yer alır.

![Yalnızca bulut kimliğinin temel bileşenleri.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Hem şirket içi hem de uzak (çevrimiçi) kullanıcılar, Microsoft 365 bulut hizmetlerine erişmek için Azure AD kullanıcı hesaplarını ve parolalarını kullanır. Azure AD, depolanan kullanıcı hesaplarına ve parolalarına göre kullanıcı kimlik bilgilerini doğrular.

### <a name="administration"></a>Yönetim
Kullanıcı hesapları yalnızca Azure AD'de depolandığından, bulut kimliklerini [Microsoft 365 yönetim merkezi](/admin) ve [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md) gibi araçlarla yönetirsiniz.

## <a name="hybrid-identity"></a>Karma kimlik

Karma kimlik, şirket içi AD DS'den kaynaklanan ve bir Microsoft 365 aboneliğinin Azure AD kiracısında bir kopyası olan hesapları kullanır. Çoğu değişiklik, [belirli hesap öznitelikleri](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized) dışında yalnızca bir şekilde akar. AD DS kullanıcı hesaplarında yaptığınız değişiklikler, Azure AD'deki kopyalarıyla eşitlenir.

Azure AD Bağlan devam eden hesap eşitlemesini sağlar. Şirket içi sunucuda çalışır, AD DS'deki değişiklikleri denetler ve bu değişiklikleri Azure AD'ye iletir. Azure AD Bağlan, hangi hesapların eşitlendiğini ve parola karması eşitleme (PHS) olarak bilinen kullanıcı parolalarının karma sürümünün eşitlenip eşitlenmeyeceğini filtreleme olanağı sağlar.

Karma kimlik uyguladığınızda, hesap bilgileri için yetkili kaynak şirket içi AD DS'niz olur. Bu, daha sonra Azure AD ile eşitlenen yönetim görevlerini çoğunlukla şirket içinde gerçekleştirdiğiniz anlamına gelir.

Karma kimliğin bileşenleri aşağıdadır.

![Karma kimliğin bileşenleri.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD kiracısı, AD DS hesaplarının bir kopyasına sahiptir. Bu yapılandırmada, hem şirket içi hem de Microsoft 365 bulut hizmetlerine erişen uzak kullanıcılar Azure AD'de kimlik doğrulaması yapar.

> [!NOTE]
> Karma kimlik için kullanıcı hesaplarını eşitlemek için her zaman Azure AD Bağlan kullanmanız gerekir. Lisans ataması ve grup yönetimi gerçekleştirmek, izinleri yapılandırmak ve kullanıcı hesaplarını içeren diğer yönetim görevlerini gerçekleştirmek için Azure AD'deki eşitlenmiş kullanıcı hesaplarına ihtiyacınız vardır.

### <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Microsoft 365 için karma kimlik ve dizin eşitlemesi

İş gereksinimlerinize ve teknik gereksinimlerinize bağlı olarak karma kimlik modeli ve dizin eşitlemesi, Microsoft 365 benimseyen kurumsal müşteriler için en yaygın seçenektir. Dizin eşitlemesi, Active Directory Domain Services (AD DS) kimliklerinizi yönetmenize olanak tanır ve kullanıcı hesapları, grupları ve kişilere yönelik tüm güncelleştirmeler Microsoft 365 aboneliğinizin Azure Active Directory (Azure AD) kiracısına eşitlenir.

>[!Note]
>AD DS kullanıcı hesapları ilk kez eşitlendiğinde, bunlara otomatik olarak bir Microsoft 365 lisansı atanamaz ve e-posta gibi Microsoft 365 hizmetlerine erişemez. Önce onlara bir kullanım konumu atamanız gerekir. Ardından, grup üyeliği aracılığıyla bu kullanıcı hesaplarına tek tek veya dinamik olarak bir lisans atayın.
>

#### <a name="authentication-for-hybrid-identity"></a>Karma kimlik için kimlik doğrulaması

Karma kimlik modeli kullanılırken iki tür kimlik doğrulaması vardır:

- Yönetilen kimlik doğrulaması

  Azure AD, parolanın yerel olarak depolanan karma sürümünü kullanarak kimlik doğrulama işlemini işler veya kimlik bilgilerini şirket içi AD DS tarafından kimlik doğrulaması için şirket içi yazılım aracısına gönderir.

- Şirket Dışı Kimlik Doğrulaması

  Azure AD, kimlik doğrulaması isteyen istemci bilgisayarı başka bir kimlik sağlayıcısına yönlendirir.

#### <a name="managed-authentication"></a>Yönetilen kimlik doğrulaması

İki tür yönetilen kimlik doğrulaması vardır:

- Parola karması eşitlemesi (PHS)

  Azure AD kimlik doğrulamasının kendisini gerçekleştirir.

- Doğrudan kimlik doğrulaması (PTA)

  Azure AD' de kimlik doğrulamasını gerçekleştiren AD DS vardır.


##### <a name="password-hash-synchronization-phs"></a>Parola karması eşitlemesi (PHS)

PHS ile AD DS kullanıcı hesaplarınızı Microsoft 365 ile eşitler ve kullanıcılarınızı şirket içinde yönetirsiniz. Kullanıcı parolalarının karmaları AD DS'nizden Azure AD'ye eşitlenir, böylece kullanıcılar şirket içinde ve bulutta aynı parolaya sahip olur. Bu, Azure AD'de AD DS kimlikleri için kimlik doğrulamasını etkinleştirmenin en basit yoludur. 

![Parola karması eşitlemesi (PHS).](../media/plan-for-directory-synchronization/phs-authentication.png)

Parolalar şirket içinde değiştirildiğinde veya sıfırlandığında, kullanıcılarınızın bulut kaynakları ve şirket içi kaynaklar için her zaman aynı parolayı kullanabilmesi için yeni parola karmaları Azure AD ile eşitlenir. Kullanıcı parolaları hiçbir zaman Azure AD'ye gönderilmez veya Azure AD'de düz metin olarak depolanmaz. Kimlik Koruması gibi Azure AD'nin bazı premium özellikleri, hangi kimlik doğrulama yönteminin seçildiğinden bağımsız olarak PHS gerektirir.
  
Daha fazla bilgi edinmek için [doğru kimlik doğrulama yöntemini seçme](/azure/active-directory/hybrid/choose-ad-authn) bölümüne bakın.
  
##### <a name="pass-through-authentication-pta"></a>Doğrudan kimlik doğrulaması (PTA)

PTA, kullanıcıları doğrudan AD DS'nizle doğrulamak için bir veya daha fazla şirket içi sunucuda çalışan bir yazılım aracısı kullanarak Azure AD kimlik doğrulama hizmetleri için basit bir parola doğrulaması sağlar. PTA ile AD DS kullanıcı hesaplarını Microsoft 365 ile eşitler ve kullanıcılarınızı şirket içinde yönetirsiniz. 

![Doğrudan kimlik doğrulaması (PTA).](../media/plan-for-directory-synchronization/pta-authentication.png)

PTA, kullanıcılarınızın şirket içi hesap ve parolalarını kullanarak hem şirket içinde hem de Microsoft 365 kaynaklarda ve uygulamalarda oturum açmasına olanak tanır. Bu yapılandırma, parola karmalarını Azure AD'de depolamadan doğrudan şirket içi AD DS'nize karşı kullanıcı parolalarını doğrular. 

PTA ayrıca şirket içi kullanıcı hesabı durumlarını, parola ilkelerini ve oturum açma saatlerini hemen zorunlu kılmak için güvenlik gereksinimi olan kuruluşlara yöneliktir. 
  
Daha fazla bilgi edinmek için [doğru kimlik doğrulama yöntemini seçme](/azure/active-directory/hybrid/choose-ad-authn) bölümüne bakın.
  
##### <a name="federated-authentication"></a>Şirket Dışı Kimlik Doğrulaması

Federasyon kimlik doğrulaması öncelikli olarak daha karmaşık kimlik doğrulaması gereksinimleri olan büyük kurumsal kuruluşlar içindir. AD DS kimlikleri Microsoft 365 ile eşitlenir ve kullanıcı hesapları şirket içinde yönetilir. Federasyon kimlik doğrulamasıyla, kullanıcılar şirket içinde ve bulutta aynı parolaya sahiptir ve Microsoft 365 kullanmak için yeniden oturum açmaları gerekmez. 

Federasyon kimlik doğrulaması, akıllı kart tabanlı kimlik doğrulaması veya üçüncü taraf çok faktörlü kimlik doğrulaması gibi ek kimlik doğrulama gereksinimlerini destekleyebilir ve kuruluşların Azure AD tarafından yerel olarak desteklenmeyen bir kimlik doğrulama gereksinimi olduğunda genellikle gereklidir.
 
Daha fazla bilgi edinmek için [doğru kimlik doğrulama yöntemini seçme](/azure/active-directory/hybrid/choose-ad-authn) bölümüne bakın.
  
Üçüncü taraf kimlik doğrulaması ve kimlik sağlayıcıları için, şirket içi dizin nesneleri öncelikle üçüncü taraf kimlik sağlayıcısı (IdP) tarafından yönetilen Microsoft 365 ve bulut kaynağı erişimiyle eşitlenebilir. Kuruluşunuz bir üçüncü taraf federasyon çözümü kullanıyorsa, üçüncü taraf federasyon çözümünün Azure AD ile uyumlu olması koşuluyla Microsoft 365 için bu çözümle oturum açmayı yapılandırabilirsiniz.
  
Daha fazla bilgi edinmek için [Bkz. Azure AD federasyon uyumluluğu listesi](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .
  
### <a name="administration"></a>Yönetim

Özgün ve yetkili kullanıcı hesapları şirket içi AD DS'de depolandığından, kimliklerinizi AD DS'nizi yönettiğiniz araçlarla yönetirsiniz.

Azure AD'de eşitlenmiş kullanıcı hesaplarını yönetmek için Microsoft 365 için Microsoft 365 yönetim merkezi veya PowerShell'i kullanmazsınız.

## <a name="next-step"></a>Sonraki adım

[![Microsoft 365 ayrıcalıklı hesaplarınızı koruma](../media/deploy-identity-solution-overview/protect-your-global-administrator-accounts.png)](protect-your-global-administrator-accounts.md)

Genel yönetici hesaplarınızın güvenliğini sağlamak için [2. Adımla](protect-your-global-administrator-accounts.md) devam edin.
