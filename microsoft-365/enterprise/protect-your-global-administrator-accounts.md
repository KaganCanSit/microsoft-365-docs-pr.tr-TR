---
title: Adım 2. Microsoft 365 ayrıcalıklı hesaplarınızı koruma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, Microsoft 365 kiracınıza ayrıcalıklı erişimi koruma hakkında bilgi sağlanır.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3da8a6279d122a056a168485145c171f9d3d7f5f
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930207"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Adım 2. Microsoft 365 ayrıcalıklı hesaplarınızı koruma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Bilgi toplama ve kimlik avı saldırıları dahil olmak üzere bir Microsoft 365 kiracısının güvenlik ihlalleri genellikle Microsoft 365 ayrıcalıklı hesabının kimlik bilgilerini tehlikeye atarak yapılır. Buluttaki güvenlik, sizinle Microsoft arasındaki bir iş ortaklığıdır:
  
- Microsoft bulut hizmetleri, güven ve güvenlik temeli üzerine kurulmuştur. Microsoft, verilerinizi ve uygulamalarınızı korumanıza yardımcı olacak güvenlik denetimleri ve özellikleri sağlar.
    
- Verilerinize ve kimliklerinize ve bunları koruma sorumluluğuna, şirket içi kaynaklarınızın güvenliğine ve denetlediğiniz bulut bileşenlerinin güvenliğine sahip olursunuz.
    
Microsoft, kuruluşunuzu korumaya yardımcı olacak özellikler sağlar, ancak yalnızca bunları kullandığınızda etkilidir. Bunları kullanmazsanız saldırılara karşı savunmasız olabilirsiniz. Ayrıcalıklı hesaplarınızı korumak için Microsoft, aşağıdakilere ilişkin ayrıntılı yönergelerle size yardımcı olmak için buradadır:
  
1. Ayrılmış, ayrıcalıklı, bulut tabanlı hesaplar oluşturun ve bunları yalnızca gerektiğinde kullanın.
    
2. Ayrılmış Microsoft 365 ayrıcalıklı hesaplarınız için çok faktörlü kimlik doğrulamasını (MFA) yapılandırın ve en güçlü ikincil kimlik doğrulama biçimini kullanın.

3. Sıfır Güven kimliği ve cihaz erişim önerileriyle ayrıcalıklı hesapları koruyun.

> [!NOTE]
> Ayrıcalıklı rollerinizin güvenliğini sağlamak için kiracınıza ayrıcalıklı erişimin güvenliğini sağlamak [için Azure AD rollerine yönelik en iyi yöntemler'e](/azure/active-directory/roles/best-practices) göz atın.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Ayrılmış, ayrıcalıklı, bulut tabanlı kullanıcı hesapları oluşturun ve bunları yalnızca gerektiğinde kullanın

Yönetici rolleri atanmış günlük kullanıcı hesaplarını kullanmak yerine, Azure AD'de yönetici rollerine sahip ayrılmış kullanıcı hesapları oluşturun. 

Şu andan itibaren, yalnızca yönetici ayrıcalıkları gerektiren görevler için ayrılmış ayrıcalıklı hesaplarla oturum açarsınız. Diğer tüm Microsoft 365 yönetimi, kullanıcı hesaplarına başka yönetim rolleri atanarak yapılmalıdır.
  
> [!NOTE]
> Bunun için günlük kullanıcı hesabınız olarak oturumu kapatmak ve ayrılmış bir yönetici hesabıyla oturum açmak için ek adımlar gerekir. Ancak bunun yalnızca yönetici işlemleri için zaman zaman yapılması gerekir. Yönetici hesabı ihlalinden sonra Microsoft 365 aboneliğinizi kurtarmanın çok daha fazla adım gerektirdiğini göz önünde bulundurun.

Azure AD'nin yanlışlıkla kilitlenmesini önlemek için [acil durum erişim hesapları](/azure/active-directory/roles/security-emergency-access) da oluşturmanız gerekir.

Yönetici rollerinin isteğe bağlı, tam zamanında atanması için Azure AD Privileged Identity Management (PIM) ile ayrıcalıklı hesaplarınızı daha da koruyabilirsiniz. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Ayrılmış Microsoft 365 ayrıcalıklı hesaplarınız için çok faktörlü kimlik doğrulamasını yapılandırma

Çok faktörlü kimlik doğrulaması (MFA), hesap adı ve parola dışında ek bilgiler gerektirir. Microsoft 365 şu ek doğrulama yöntemlerini destekler:
  
- Microsoft Authenticator uygulaması
- Telefon araması
- Kısa mesajla gönderilen rastgele oluşturulmuş doğrulama kodu
- Akıllı kart (sanal veya fiziksel) (federasyon kimlik doğrulaması gerektirir)
- Biyometrik bir cihaz
- Oauth belirteci
    
>[!Note]
>Ulusal Standartlar ve Teknoloji Enstitüsü (NIST) standartlarına uyması gereken kuruluşlar için, telefon görüşmesi veya kısa mesaj tabanlı ek doğrulama yöntemlerinin kullanımı kısıtlanır. Ayrıntılar için [buraya](https://pages.nist.gov/800-63-FAQ/#q-b01) tıklayın.
>

Yalnızca bulutta depolanan kullanıcı hesaplarını (yalnızca bulut kimlik modeli) kullanan küçük bir işletmeyseniz [, MFA'yı](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) her ayrılmış ayrıcalıklı hesap için akıllı telefona gönderilen bir telefon araması veya kısa mesaj doğrulama kodu kullanarak MFA'yı yapılandıracak şekilde ayarlayın.
    
Microsoft 365 karma kimlik modeli kullanan daha büyük bir kuruluşsanız daha fazla doğrulama seçeneğiniz vardır. Daha güçlü bir ikincil kimlik doğrulama yöntemi için güvenlik altyapısı zaten mevcutsa [, MFA'yı ayarlayın](../admin/security-and-compliance/set-up-multi-factor-authentication.md) ve her ayrılmış ayrıcalıklı hesabı uygun doğrulama yöntemi için yapılandırın.
  
İstenen daha güçlü doğrulama yöntemi için güvenlik altyapısı yerinde değilse ve Microsoft 365 MFA için çalışmıyorsa, microsoft Authenticator uygulamasını, telefon aramasını veya ayrıcalıklı hesaplarınız için akıllı telefona gönderilen kısa mesaj doğrulama kodunu geçici güvenlik önlemi olarak kullanarak MFA ile ayrılmış ayrıcalıklı hesaplar yapılandırmanızı kesinlikle öneririz. MFA tarafından sağlanan ek koruma olmadan ayrılmış ayrıcalıklı hesaplarınızı bırakmayın.
  
Daha fazla bilgi için bkz. [Microsoft 365 için MFA](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Sıfır Güven kimliği ve cihaz erişim önerileriyle yönetici hesaplarını koruma

Microsoft, güvenli ve üretken bir iş gücü sağlamaya yardımcı olmak için [kimlik ve cihaz erişimine](../security/office-365-security/microsoft-365-policies-configurations.md) yönelik bir dizi öneri sunar. Kimlik için şu makalelerdeki önerileri ve ayarları kullanın:

- [Önkoşullar](../security/office-365-security/identity-access-prerequisites.md)
- [Genel kimlik ve cihaz erişim ilkeleri](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Kurumsal kuruluşlar için ek korumalar

Ayrıcalıklı hesabınızın ve bunu kullanarak gerçekleştirdiğiniz yapılandırmanın mümkün olduğunca güvenli olduğundan emin olmak için bu ek yöntemleri kullanın.
  
### <a name="privileged-access-workstation"></a>Ayrıcalıklı erişim iş istasyonu

Yüksek ayrıcalıklı görevlerin yürütülmesinin mümkün olduğunca güvenli olmasını sağlamak için ayrıcalıklı bir erişim iş istasyonu (PAW) kullanın. PAW, yalnızca ayrıcalıklı hesap gerektiren Microsoft 365 yapılandırması gibi hassas yapılandırma görevleri için kullanılan ayrılmış bir bilgisayardır. Bu bilgisayar İnternet'e gözatma veya e-posta için günlük olarak kullanılmadığından, İnternet saldırılarına ve tehditlerine karşı daha iyi korunur.
  
PAW'ı ayarlama yönergeleri için bkz [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices). .

Azure AD kiracınız ve yönetici hesaplarınız için Azure PIM'i etkinleştirmek [için PIM'i yapılandırma adımlarına](/azure/active-directory/active-directory-privileged-identity-management-configure) bakın.

Siber saldırganlara karşı ayrıcalıklı erişimi güvenli hale getirmek için kapsamlı bir yol haritası geliştirmek için bkz. [Azure AD'de hibrit ve bulut dağıtımları için ayrıcalıklı erişimin güvenliğini sağlama](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Ayrıcalıklı hesaplarınıza kalıcı olarak yönetici rolü atanmasını sağlamak yerine, gerektiğinde yönetici rolünün isteğe bağlı, tam zamanında atanmasını etkinleştirmek için Azure AD PIM'i kullanabilirsiniz.
  
Yönetici hesaplarınız kalıcı yönetici olmaktan çıkar ve uygun yöneticilere geçer. Yönetici rolü, biri ihtiyaç duyana kadar etkin değildir. Ardından, yönetici rolünü önceden belirlenmiş bir süre için ayrıcalıklı hesaba eklemek için bir etkinleştirme işlemini tamamlarsınız. Süre dolduğunda, PIM yönetici rolünü ayrıcalıklı hesaptan kaldırır.
  
PIM'i kullanmak ve bu işlem, ayrıcalıklı hesaplarınızın saldırılara ve kötü amaçlı kullanıcıların kullanımına karşı savunmasız olduğu süreyi önemli ölçüde azaltır.

PIM, Microsoft 365 E5'e dahil olan Azure Active Directory Premium P2 ile kullanılabilir. Alternatif olarak, yönetici hesaplarınız için tek tek Azure Active Directory Premium P2 lisansları satın alabilirsiniz.
  
Daha fazla bilgi için bkz.:

- [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Azure AD'de karma ve bulut dağıtımları için ayrıcalıklı erişimin güvenliğini sağlama](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Ayrıcalıklı erişim yönetimi

Kiracınızdaki görev tabanlı etkinlikler için tam zamanında erişim belirten ilkeler yapılandırılarak ayrıcalıklı erişim yönetimi etkinleştirilir. Kuruluşunuzun hassas verilere veya kritik yapılandırma ayarlarına erişimi olan mevcut ayrıcalıklı yönetici hesaplarını kullanabilecek ihlallere karşı korunmasına yardımcı olabilir. Örneğin, kiracınızdaki kuruluş posta kutusu ayarlarına erişmek ve değiştirmek için açık onay gerektiren ayrıcalıklı bir erişim yönetimi ilkesi yapılandırabilirsiniz.

Bu adımda, kiracınızda ayrıcalıklı erişim yönetimini etkinleştirecek ve kuruluşunuz için verilere ve yapılandırma ayarlarına görev tabanlı erişim için ek güvenlik sağlayan ayrıcalıklı erişim ilkeleri yapılandıracaksınız. Kuruluşunuzda ayrıcalıklı erişimi kullanmaya başlamak için üç temel adım vardır:

- Onaylayan grubu oluşturma
- Ayrıcalıklı erişimi etkinleştirme
- Onay ilkeleri oluşturma

Ayrıcalıklı erişim yönetimi, kuruluşunuzun sıfır ayakta ayrıcalıklarla çalışmasını ve bu tür yönetim erişimi nedeniyle ortaya çıkan güvenlik açıklarına karşı bir savunma katmanı sağlamasını sağlar. Ayrıcalıklı erişim, ilişkili onay ilkesi tanımlanmış herhangi bir görevi yürütmek için onay gerektirir. Onay ilkesine dahil edilen görevleri yürütmesi gereken kullanıcıların erişim onayı istemesi ve verilmesi gerekir.

Ayrıcalıklı erişim yönetimini etkinleştirmek için bkz. [Ayrıcalıklı erişim yönetimini yapılandırma](/office365/securitycompliance/privileged-access-management-configuration).

Daha fazla bilgi için bkz [. Ayrıcalıklı erişim yönetimi](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Microsoft 365 günlüğü için güvenlik bilgileri ve olay yönetimi (SIEM) yazılımı

Bir sunucuda çalıştırılan SIEM yazılımı, uygulamalar ve ağ donanımı tarafından oluşturulan güvenlik uyarılarının ve olaylarının gerçek zamanlı analizini gerçekleştirir. SIEM sunucunuzun analiz ve raporlama işlevlerine Microsoft 365 güvenlik uyarılarını ve olaylarını eklemesine izin vermek için Azure AD'yi SEIM'inizle tümleştirin. Bkz. [Azure Günlük Tümleştirmesine Giriş](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Sonraki adım

[![Microsoft 365 kullanıcı hesaplarınızı koruma](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Kullanıcı hesaplarınızın güvenliğini sağlamak için [3. Adımla](microsoft-365-secure-sign-in.md) devam edin.
