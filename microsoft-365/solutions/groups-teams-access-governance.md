---
title: Farklı gruplarda, Microsoft 365 ve Teams için SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Farklı gruplarda, gruplarda Microsoft 365 yönetme hakkında Teams bilgi SharePoint.
ms.openlocfilehash: e01326093476f341c6c4c75448efbdf8c745779f
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005032"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Farklı gruplarda, Microsoft 365 ve Teams için SharePoint

Kişilerin gruplarda, ekiplerde ve ekiplerde yer alan kaynaklara nasıl erişeceklerini sizin SharePoint. Bu seçenekleri gözden geçirebilirsiniz ve bunların iş ihtiyaçlarına nasıl eş olduğunu, verilerinizin duyarlılığını ve kullanıcılarının işbirliği yapmaları gereken kişilerin kapsamını göz önünde bulundurabilirsiniz.

Aşağıdaki tabloda, çalışma sayfalarındaki erişim denetimleri için hızlı Microsoft 365. Aşağıdaki bölümlerde başka bilgiler sağlanmaktadır.

|Kategori|Açıklama|Başvuru|
|:-------|:----------|:--------|
|Üyelik|||
||Özel ekiplerin keşifleri|[Bir ekipte özel ekiplerin keşiflerini Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||Kurallara dayalı dinamik grup üyeliği|[Grup içinde dinamik grup oluşturma veya Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||Dosyaları, klasörleri ve siteleri kimlerin paylaşalırı kontrol edin.|[Erişim isteklerini ayarlama ve yönetme](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Koşullu erişim|||
||Multifactor Authentication|[Azure AD Multifactor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)|
||Grup, ekip veya site duyarlılığına göre cihaz erişimini kontrol edin.|[Aynı sitelerde, gruplarda ve Microsoft Teams sitelerde Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Site erişimini, unmanaged cihazlar için sınırlandırma.|[Kolay SharePoint cihazlardan erişim denetimi](/sharepoint/control-access-from-unmanaged-devices)|
||Konuma göre site erişimini denetleme|[Ağ konumu temel SharePoint veriye OneDrive ve verilere erişimi denetleme](/sharepoint/control-access-based-on-network-location)|
|Konuk erişimi|||
||Belirtilen etki alanlarından SharePoint paylaşımına izin verme veya engelleme.|[Etki alanına göre SharePoint ve OneDrive paylaşımını kısıtlama](/sharepoint/restricted-domains-sharing)|
||Ekip veya grup üyeliğinin belirtilen etki alanlarından yürütülmesine izin verme veya engelleme.|[Belirli kuruluşlardan B2B kullanıcılarına davetlere izin verme veya davetleri engelleme](/azure/active-directory/b2b/allow-deny-list)|
||Anonim paylaşımı engelin.|[Herkes bağlantılarını kapatma](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||Anonim erişim bağlantıları için izinleri denetleyin.|[Herkes bağlantıları için bağlantı izinlerini ayarlama](./best-practices-anonymous-sharing.md#set-link-permissions)|
||Anonim paylaşım bağlantılarının süre sona erme tarihini kontrol edin.|[Herkes bağlantıları için son kullanma tarihi ayarlama](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||Varsayılan olarak kullanıcılara gösterilen paylaşım bağlantısı türünü kontrol edin.|[Bir site için varsayılan bağlantı türünü değiştirme](/sharepoint/change-default-sharing-link)|
||Dış paylaşımı belirli kişilerle sınırlandırma.|[Dış paylaşımı belirtilen güvenlik gruplarıyla sınırlandırma](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Bilgi duyarlılığını temel alarak konuk erişimini grup, ekip veya siteye kontrol edin.|[Aynı sitelerde, gruplarda ve Microsoft Teams sitelerde Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Paylaşım seçeneklerini kapatın.|[Dosyada paylaşımı Microsoft 365](./microsoft-365-limit-sharing.md)|
|Kullanıcı yönetimi|||
||Ekip ve grup üyeliğini düzenli olarak gözden geçirme.|[Azure AD erişim incelemeleri nedir?](/azure/active-directory/governance/access-reviews-overview)|
||Gruplara ve ekiplere erişim yönetimini otomatikleştirin.|[Azure AD yetkilendirme yönetimi nedir?](/azure/active-directory/governance/entitlement-management-overview)|
||Kişilerin belirli bir gün içinde özel kanallar oluşturmasına izin Teams.|[Özel kanalların yaşam döngüsünü Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a>Üyelik

Ekip ve grup üyeliği, sahipler tarafından denetleniyor. Üyeler başkalarını davet etsa da, davetler onay için sahiplere gönderilir. Herkese açık ekipler ve gruplar kuruluşta herkes tarafından keşfedilebilir olsa da, özel ekiplerin ve grupların keşfedilebilir olup olmadığını kontrol edilebilir:

- [Bir ekipte özel ekiplerin keşiflerini Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

Bölüm gibi bazı ölçütlere göre bir grup veya ekibin üyeliğini dinamik olarak yönetabilirsiniz. Bu durumda, üyeler ve sahipler kişileri takıma davet etmeyecektir. Dinamik gruplar, grubun üyesi olan Azure Active Directory denetim için grup içinde tanımladığınız meta verileri kullanır. Yanlış meta verilerin kullanıcıların grup dışında bırakılamalarına veya yanlış kullanıcıların eklenmelerine yol açamaya neden olduğundan, kullanmakta olduğu meta verilerin eksiksiz ve güncel olduğundan emin olun.

- [Grup içinde dinamik grup oluşturma veya Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

SharePoint siteleri grup veya ekip üyeliği dışında sahip, üye ve ziyaretçi ekleme olanağı sağlar. Gereksinimlerinize bağlı olarak, siteye kimlerin davet gereksinimlerini kısıtlayabilirsiniz. Ayrıca, belirli bir sitedeki bilgilerin duyarlılığına bağlı olarak, dosyaları ve klasörü paylaşacak kullanıcıları kısıtlamak da istemeniz iyi olabilir. Bu kısıtlamalar ekip, grup veya site sahibi tarafından yapılandırılır:

- [Erişim isteklerini ayarlama ve yönetme](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Koşullu erişim

Birden Microsoft 365, hem kuruluşun içindeki hem de dışındaki kişiler için çok faktörlü kimlik doğrulaması gerekli olabilir. kişilerin ikinci bir kimlik doğrulama faktörü istendiğinde, bu durum için birçok seçenek vardır. Çok faktörlü kimlik doğrulamasını organizasyonunız için dağıtmanızı kesinlikle öneririz:

- [Azure AD Multifactor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)

Bazı grup ve ekiplerde hassas bilgiler varsa, bir grup veya ekibin duyarlılık etiketine bağlı olarak cihaz yönetimi ilkelerini zorunlu  edebilirsiniz. Erişimi tamamen unmanaged cihazlarından engelleyebilir veya sınırlı, yalnızca web erişimine izin veebilirsiniz:

- [Aynı sitelerde, gruplarda ve Microsoft Teams sitelerde Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)

Site SharePoint belirtilen ağ konumlarından sitelere erişimi kısıtabilirsiniz.

- [Ağ konumu temel SharePoint veriye OneDrive ve verilere erişimi denetleme](/sharepoint/control-access-based-on-network-location)


Ek kaynaklar:

- [Koşullu Erişim dağıtımı planlama](/azure/active-directory/conditional-access/plan-conditional-access)

- [Microsoft Intune genel bakış](/mem/intune/fundamentals/what-is-intune)

- [Kolay SharePoint cihazlardan erişim denetimi](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Konuk erişimi

Konukları, e-posta adreslerinin etki alanına göre kısıtabilirsiniz. SharePoint, kuruluş genelinde ve siteye özgü etki alanı kısıtlama ayarları sunar. Gruplar ve Teams Azure AD'de etki alanı izinlistelerini veya engellemelerini kullanır. İstenmeyen paylaşımı önlemek ve tutarlı bir kullanıcı deneyimi sağlamak için her iki ayarı da yapılandırmış olun:

- [Etki alanına göre SharePoint ve OneDrive paylaşımını kısıtlama](/sharepoint/restricted-domains-sharing)

- [Belirli kuruluşlardan B2B kullanıcılarına davetlere izin verme veya davetleri engelleme](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365, Herkes bağlantı paylaşarak dosya ve klasörlerin anonim *olarak paylaştır 2013'e* izin verir. *Herkes* bağlantıları iletebilirsiniz ve bu bağlantıyı alan herkes paylaşılan öğeye erişebilirsiniz. Verilerinizin duyarlılığına bağlı olarak, Herkes bağlantılarının nasıl kullanıldıklarına  bağlı olarak, bağlantı izinlerini tamamen kapatma, salt okunur izinlerini kısıtlama veya bağlantı için süre sonu ayarlama gibi çeşitli kurallar kullanabilirsiniz:

- [Herkes bağlantılarını kapatma](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [Herkes bağlantıları için bağlantı izinlerini ayarlama](./best-practices-anonymous-sharing.md#set-link-permissions)

- [Herkes bağlantıları için son kullanma tarihi ayarlama](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

Dosya veya klasörleri paylaştığınızda, kullanıcıların seçim yapmak için çeşitli bağlantı türleri vardır. Yanlışlıkla uygunsuz paylaşım riskini azaltmak için, paylaştığınız kullanıcılara sunulan varsayılan bağlantı türünü değiştirebilirsiniz. Örneğin, anonim erişime *olanak sağlayan Herkes* bağlantılarından Kuruluş bağlantılarınıza varsayılan ayarın  değiştirilmesi hassas bilgilerin istenmeyen dış paylaşım riskini azaltır:

- [Bir site için varsayılan bağlantı türünü değiştirme](/sharepoint/change-default-sharing-link)

Kuruluşta konuklarla paylaşmanız gereken hassas veriler varsa, ancak uygunsuz paylaşım konusunda endişeleniyorsanız, dosya ve klasörlerin dış paylaşımını belirtilen güvenlik gruplarının üyeleriyle sınırlandırabilirsiniz. Bu şekilde, paylaşımı belirli bir kişi grubuyla harici olarak kısıtlar veya kullanıcılarınızı güvenlik grubuna eklemeden önce uygun dış paylaşımla ilgili eğitim almalarını gerekli bulundurabilirsiniz:

- [Dış paylaşımı belirtilen güvenlik gruplarıyla sınırlandırma](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Gruplar ve Teams erişime izin ve reddeden kuruluş düzeyinde ayarlara sahip olabilir. [Microsoft PowerShell kullanarak konuk erişimini belirli ekiplere](per-group-guest-access.md) veya gruplara kısıtlasanız da, bunu bir duyarlılık etiketiyle yapmanizi öneririz. Duyarlılık etiketleriyle, uygulanan etikete bağlı olarak konuk erişimine otomatik olarak izin ve edebilir veya reddedabilirsiniz:

- [Aynı sitelerde, gruplarda ve Microsoft Teams sitelerde Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)

Konukları gruplara ve ekiplere sık sık davet etmek için zamanlanmış konuk erişimi incelemeleri ayarlamayı düşünebilirsiniz. Sahiplerin gruplarında ve ekiplerinde konukları gözden geçirmesi ve erişimi onaylaması veya reddetmesi istendiğinde.

- [Konuk erişimi incelemelerini ayarlama](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365, birçok farklı bilgi paylaşma yöntemi sunar. Hassas bilginiz varsa ve bu bilgilerin paylaşılmalarını kısıtlamak için, paylaşımı sınırlama seçeneklerini gözden geçirin:

- [Dosyada paylaşımı Microsoft 365](./microsoft-365-limit-sharing.md)

Ek kaynaklar:

- [İş Birliği ile güvenli işbirliği Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](./best-practices-anonymous-sharing.md)

- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](./share-limit-accidental-exposure.md)

- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

- [B2B dış işbirliğini etkinleştirme ve konukları kimlerin davet edebileceğini yönetme](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Kullanıcı yönetimi

Gruplar ve ekipler kuruluş içinde geliştikçe, ekip ve grup üyeliğini düzenli olarak gözden geçirmek iyi bir uygulamadır. Bu, değişen üyeliği olan, hassas bilgiler içeren veya konuk içeren ekipler ve gruplar için özellikle yararlı olabilir. Bu ekipler ve gruplar için erişim incelemeleri ayarlamayı düşünebilirsiniz:

- [Azure AD erişim incelemeleri nedir?](/azure/active-directory/governance/access-reviews-overview)

Birçok kuruluşun, birlikte derinlikte birlikte çalışan diğer kuruluşlarla veya önemli satıcılarla iş ortaklığı vardır. Bu senaryolarda, kullanıcı yönetiminin ve kaynaklara erişimin yönetimi zor olabilir. Kullanıcı yönetimi görevlerden bazılarının otomatik hale nasıl geçerek iş ortağı organizasyona geçişini bile göz önünde bulundurabilirsiniz:

- [Azure AD yetkilendirme yönetimi nedir?](/azure/active-directory/governance/entitlement-management-overview)

Ekip üyeleri Teams alt kümesi arasında kapsamları olan konuşmalara ve dosya paylaşımına izin veren özel kanallar. İşle ilgili gereksinimlerinize bağlı olarak, bu beceriye izin vermek veya bunu engellemek istiyor olabilir.

- [Kanallarda özel Microsoft Teams](/MicrosoftTeams/private-channels)

- [Özel kanalların yaşam döngüsünü Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)

Ek kaynaklar:

- [Azure Active Directory Yönetimi](/azure/active-directory/governance)

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Güvenlik ve uyumluluk Microsoft Teams](/microsoftteams/security-compliance-overview)

[E-postada paylaşım SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[Dış ağ oluşturma ve yönetme Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[Dört Teams koruma katmanıyla yapılandırma](./configure-teams-three-tiers-protection.md)