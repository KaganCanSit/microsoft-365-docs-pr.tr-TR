---
title: Adım 2. Ayrıcalıklı Microsoft 365 hesaplarınızı koruma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365initiative-coredeploy
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Bu makale, kiracınıza ayrıcalıklı erişimi koruma hakkında Microsoft 365 sağlar.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff20b8dcaf203771b0c3a935b67e83eb291ec75e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014388"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Adım 2. Ayrıcalıklı Microsoft 365 hesaplarınızı koruma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Bilgi toplama ve kimlik avı Microsoft 365 da dahil olmak üzere bir Microsoft 365 kiracının güvenlik ihlalleri genellikle bir kullanıcı ayrıcalığı olan bir hesabın kimlik bilgilerinden ödün Microsoft 365 yapılır. Buluttaki güvenlik, siz ve Microsoft arasında bir ortaklıktır:
  
- Microsoft bulut hizmetleri güven ve güvenlik temel üzerine kurulur. Microsoft, verilerinizi ve uygulamalarınızı korumanıza yardımcı olmak için güvenlik denetimleri ve özellikler sağlar.
    
- Verilerinizi ve kimliklerinizi ve bunları koruma sorumluluğunuz, şirket içi kaynaklarınızı koruma ve sizin denetiminiz olan bulut bileşenlerinin güvenliği sizin sorumluluğumdadır.
    
Microsoft, kurumlarınızı korumaya yardımcı olacak özellikler sağlar, ancak bu özellikler ancak siz onları kullanıyorsanız etkilidir. Bunları kullansanız bile saldırıya açık olabilirsiniz. Ayrıcalıklı hesaplarınızı korumak için Microsoft, aşağıdaki ayrıntılı yönergelerde size yardımcı olur:
  
1. Özel, ayrıcalıklı, bulut tabanlı hesaplar oluşturun ve bunları yalnızca gerektiğinde kullanın.
    
2. Adanmış veya ayrıcalıklı hesaplarınız için çok faktörlü kimlik doğrulamasını (MFA) Microsoft 365 ikincil kimlik doğrulamanın en güçlü yöntemini kullanın.

3. Sıfır Güven kimliği ve cihaz erişimi önerileriyle ayrıcalıklı hesapları koruyun.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Özel, ayrıcalıklı, bulut tabanlı kullanıcı hesapları oluşturun ve bunları yalnızca gerektiğinde kullanın

Yönetici rolleri atanmış günlük kullanıcı hesaplarını kullanmak yerine, Azure AD'de yönetici rollerine sahip özel kullanıcı hesapları oluşturun. 

Şu andan itibaren, yalnızca yönetici ayrıcalıkları gerektiren görevler için özel ayrıcalıklı hesaplarla oturum açın. Diğer Microsoft 365 yönetim, kullanıcı hesaplarına başka yönetim rolleri atanarak yapılabilir.
  
> [!NOTE]
> Bu, günlük kullanıcı hesabınız olarak oturum açmanızı ve özel bir yönetici hesabıyla oturum açmanızı gerektiren ek adımlar gerektirmez. Ancak bu yalnızca yönetici işlemleri için ara sıra yapılması gerekir. Yönetici hesabı ihlali sonrasında Microsoft 365 fazla adım gerektir olduğunu düşünün.

Ayrıca, yanlışlıkla Azure [AD'nin kilitlenmesini](/azure/active-directory/roles/security-emergency-access) önlemek için acil durum erişim hesapları oluşturmanız gerekir.

Yönetici rollerinin isteğe bağlı, yalnızca bir defalık ataması için Azure AD Privileged Identity Management (PIM) ile ayrıcalıklı hesaplarınızı daha da koruyabilirsiniz. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Özel veya ayrıcalıklı hesaplarınız için çok faktörlü Microsoft 365 yapılandırma

Çok faktörlü kimlik doğrulaması (MFA), hesap adı ve parolası dışında ek bilgiler gerektirir. Microsoft 365 doğrulama yöntemleri şu ek doğrulama yöntemlerini destekler:
  
- Microsoft Authenticator uygulaması
- Telefon araması
- SMS mesajıyla gönderilen rastgele oluşturulmuş doğrulama kodu
- Akıllı kart (sanal veya fiziksel) (federasyon kimlik doğrulaması gerektirir)
- Biyometrik bir cihaz
- Oauth belirteci
- 
    
>[!Note]
>Ulusal Standartlar ve Teknoloji Enstitüsü (NIST) standartlarına uyması gereken kuruluşlar için telefon görüşmesi veya SMS tabanlı ek doğrulama yöntemleri kısıtlanmıştır. Ayrıntılar [için](https://pages.nist.gov/800-63-FAQ/#q-b01) buraya tıklayın.
>

Yalnızca bulutta depolanan kullanıcı hesaplarını kullanan küçük bir işletmeysanız (yalnızca bulut kimlik modeli), özel her bir ayrıcalıklı hesap için akıllı telefona gönderilen bir telefon görüşmesi veya SMS mesajı doğrulama kodu kullanarak [MFA'yi yapılandıracak şekilde MFA'yi](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) ayarlayın.
    
Karma kimlik modeli kullanan daha büyük bir Microsoft 365, daha fazla doğrulama seçeneğine sahipsiniz. Daha güçlü bir ikincil kimlik doğrulama yöntemi için güvenlik altyapısı zaten hazırsa, [MFA'yi](../admin/security-and-compliance/set-up-multi-factor-authentication.md) ayarlayın ve uygun doğrulama yöntemi için her bir ayrıcalıklı hesabı ayarlayın.
  
İstenen daha güçlü doğrulama yönteminin güvenlik altyapısı yerine sağlanmaz ve Microsoft 365 MFA için çalışmıyorsa, bir ara güvenlik önlemi olarak ayrıcalıklı hesaplarınız için akıllı telefona gönderilen Microsoft Authenticator uygulamasını, telefon aramasını veya SMS ile doğrulama kodunu kullanarak MFA ile özel ayrıcalıklı hesaplar yapılandırmanızı kesinlikle öneririz. MFA tarafından sağlanan ek koruma olmadan, özel ayrıcalıklı hesaplarınızı bırakabilirsiniz.
  
Daha fazla bilgi için bkz. [Daha fazla bilgi için MFA Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Sıfır Güven kimliği ve cihaz erişimi önerileriyle yönetici hesaplarını koruma

Güvenli ve üretken bir iş gücü sağlamaya yardımcı olmak için, Microsoft kimlik ve cihaz erişimi [için bir dizi öneri sağlar](../security/office-365-security/microsoft-365-policies-configurations.md). Kimlik için, şu makalelerde yer alan önerileri ve ayarları kullanın:

- [Önkoşullar](../security/office-365-security/identity-access-prerequisites.md)
- [Ortak kimlik ve cihaz erişimi ilkeleri](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Büyük kuruluşlar için ek korumalar

Ayrıcalıklı hesabınızla bu yapılandırmanın ve bunu kullanarak gerçekleştirilen yapılandırmanın mümkün olduğunca güvenli olmasını sağlamak için bu ek yöntemleri kullanın.
  
### <a name="privileged-access-workstation"></a>Ayrıcalıklı erişim iş istasyonu

Yüksek derecede ayrıcalıklı görevlerin yürütülmesinin mümkün olduğunca güvenli olduğundan emin olmak için, ayrıcalıklı erişim iş istasyonu (ISL) kullanın. BIR DAMİYA, ayrıcalıklı bir hesap gerektiren belirli bir yapılandırma gibi yalnızca hassas yapılandırma Microsoft 365 kullanılan özel bir bilgisayardır. Bu bilgisayar günlük olarak İnternet'e gözatma veya e-posta için kullanılmay olduğundan, İnternet saldırılarından ve tehditlerinden daha iyi korunmaktadır.
  
BURMİ'nin nasıl ayar görmeleri gerekir? yönergeleri için bkz.[https://aka.ms/cyberpaw](/security/compass/privileged-access-devices)

Azure AD kiracınız ve yönetici hesaplarınız için Azure PIM'yi etkinleştirmek için, [PIM'yi yapılandırma adımlarına bakın](/azure/active-directory/active-directory-privileged-identity-management-configure).

Siber saldırganlara karşı ayrıcalıklı erişimi güvence altına almak için kapsamlı bir yol haritası geliştirmek için bkz. Azure AD'de karma ve bulut dağıtımları için ayrıcalıklı [erişimin güvenliğini sağlama](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Ayrıcalıklı hesaplarınıza kalıcı olarak bir yönetici rolü atanmasını sağlamak yerine, gerektiğinde yönetici rolünün isteğe bağlı olarak, yalnızca zamanında atanmasını sağlamak için Azure AD PIM'yi kullanabilirsiniz.
  
Yönetici hesaplarınız kalıcı yönetici olmaktan uygun yöneticilere gider. Yönetici rolü, birinin ihtiyacı olana kadar devre dışı kalır. Ardından, önceden belirlenen bir süre için ayrıcalıklı hesaba yönetici rolü eklemek için bir etkinleştirme işlemini tamamlarsınız. Süre dolduğunda PIM, yönetici rolünü ayrıcalıklı hesaptan kaldırır.
  
PIM kullanmak ve bu işlem, ayrıcalıklı hesaplarınızı kötü amaçlı kullanıcılar tarafından saldırıya ve kullanmaya açık olan süresini önemli ölçüde azaltır.

PIM, Azure Active Directory Premium P2 ile birlikte Microsoft 365 E5. Alternatif olarak, yönetici hesaplarınız Azure Active Directory Premium P2 tek tek lisans satın alınabilir.
  
Daha fazla bilgi için bkz.:

- [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Azure AD'de karma ve bulut dağıtımlarına yönelik ayrıcalıklı erişimin güvenliğini sağlama](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Ayrıcalıklı erişim yönetimi

Ayrıcalıklı erişim yönetimi, kiracınız içinde görev tabanlı etkinlikler için tam zamanlı erişim belirten ilkeler yapılandırarak etkinleştirilir. Bu, hassas verilere ayakta erişim veya kritik yapılandırma ayarlarına erişimle, var olan ayrıcalıklı yönetici hesaplarının kullanılamalarına neden olan ihlallere karşı organizasyonlarınızı korumaya yardımcı olabilir. Örneğin, kiracınıza erişmek ve kuruluş posta kutusu ayarlarını değiştirmek için açık onay gerektiren ayrıcalıklı bir erişim yönetimi ilkesi yapılandırabilirsiniz.

Bu adımda, kiracınız için ayrıcalıklı erişim yönetimini etkinleştirir ve verilerinize ve yapılandırma ayarlarına görev tabanlı erişim için ek güvenlik sağlayan ayrıcalıklı erişim ilkelerini yapılandırabilirsiniz. Kuruluşta ayrıcalıklı erişimle çalışmaya başlamanın üç temel adımı vardır:

- Onaylayan grubu oluşturma
- Ayrıcalıklı erişimi etkinleştirme
- Onay ilkeleri oluşturma

Ayrıcalıklı erişim yönetimi, organizasyon ekser süreleriyle sıfır ayakta çalışma ayrıcalıklarına sahip çalışmasına ve bu tür ayakta yönetim erişimi nedeniyle oluşan güvenlik açıklarına karşı bir savunma katmanı sağlar. Ayrıcalıklı erişim, ilişkili onay ilkesi tanımlanmış herhangi bir görevi yürütmek için onay gerektirir. Onay ilkesinde yer alan görevleri gerçekleştirmesi gereken kullanıcılara istekte veya erişim onayı verilmesi gerekir.

Ayrıcalıklı erişim yönetimini etkinleştirmek için bkz. [Ayrıcalıklı erişim yönetimini yapılandırma](/office365/securitycompliance/privileged-access-management-configuration).

Daha fazla bilgi için bkz. [Ayrıcalıklı erişim yönetimi](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Günlük kaydı için güvenlik bilgileri ve olay yönetimi (SIEM) Microsoft 365 yazılımı

Sunucuda çalıştırılan SIEM yazılımı, uygulamalar ve ağ donanımı tarafından oluşturulan güvenlik uyarılarını ve olayları gerçek zamanlı olarak analiz gerçekleştirir. SIEM sunucunuza çözümleme ve raporlama Microsoft 365 ilgili güvenlik uyarılarını ve olaylarını içermesine izin vermek için, Azure AD'yi seIM ile tümleştirin. Bkz[. Giriş Azure Günlük Tümleştirmesi](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Sonraki adım

[![Microsoft 365 kullanıcı hesaplarınızı koruma](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Kullanıcı [hesaplarınızı güvence altına almak için 3](microsoft-365-secure-sign-in.md) . Adım ile devam edin.
