---
title: Sıfır Güven kimlik ve cihaz erişim yapılandırmaları - kuruluş için Microsoft 365
description: Sıfır Güven için güvenli e-posta, belgeler ve uygulama ilkeleri ve yapılandırmaları dağıtmaya yönelik Microsoft önerilerini ve temel kavramlarını açıklar.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-overview
- m365solution-zero-trust
ms.technology: mdo
ms.openlocfilehash: 066fc33bb5047c354fa6a4b3d954387fdfeae2e9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947791"
---
# <a name="zero-trust-identity-and-device-access-configurations"></a>kimlik ve cihaz erişim yapılandırmalarını Sıfır Güven

Bir kuruluşun teknoloji kaynaklarına ve hizmetlerine erişimi yalıtmak ve kısıtlamak için ağ güvenlik duvarlarına ve sanal özel ağlara (VPN) dayanan güvenlik mimarileri, geleneksel kurumsal ağ sınırlarının ötesindeki uygulamalara ve kaynaklara düzenli olarak erişim gerektiren bir iş gücü için artık yeterli değildir.

Microsoft, bu yeni bilgi işlem dünyasını ele almak için aşağıdaki yol gösterici ilkeleri temel alan Sıfır Güven güvenlik modelini kesinlikle önerir:

- Açıkça doğrula

  Kullanılabilir tüm veri noktalarına göre her zaman kimlik doğrulaması ve yetkilendirme. Burada, oturum açma ve sürekli doğrulama için Sıfır Güven kimlik ve cihaz erişim ilkeleri çok önemlidir.

- En az ayrıcalık erişimi kullan

  Tam Zamanında ve Yeterli Erişim (JIT/JEA), risk tabanlı uyarlamalı ilkeler ve veri koruması ile kullanıcı erişimini sınırlayın.

- İhlal varsay

  Patlama yarıçapı ve segment erişimini en aza indirin. Uçtan uca şifrelemeyi doğrulayın ve görünürlük elde etmek, tehdit algılamayı yönlendirmek ve savunmaları geliştirmek için analizi kullanın.

Sıfır Güven genel mimarisi aşağıdadır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png" alt-text="Microsoft Sıfır Güven mimarisi" lightbox="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png":::

Sıfır Güven kimlik ve cihaz erişim ilkeleri aşağıdakiler için Açıkça yönlendiren **doğrulama** ilkesini ele alın:

- Kimlik

  Bir kimlik bir kaynağa erişmeye çalıştığında, güçlü kimlik doğrulamasıyla bu kimliği doğrulayın ve istenen erişimin uyumlu ve tipik olduğundan emin olun.

- Cihazlar (uç noktalar olarak da adlandırılır)

  Güvenli erişim için cihaz durumu ve uyumluluk gereksinimlerini izleyin ve uygulayın.

- Uygulamalar

  Gölge BT'yi keşfetmek, uygun uygulama içi izinleri sağlamak, gerçek zamanlı analize göre geçit erişimi sağlamak, anormal davranışları izlemek, kullanıcı eylemlerini denetlemek ve güvenli yapılandırma seçeneklerini doğrulamak için denetimler ve teknolojiler uygulayın.

Bu makale serisinde kimlik ve cihaz erişimi önkoşul yapılandırmaları ve Azure Active Directory (Azure AD) Koşullu Erişim, Microsoft Intune ve Microsoft 365 Sıfır Güven erişimine yönelik diğer ilkeler açıklanmaktadır  Azure AD Uygulama Ara Sunucusu ile yayımlanan kurumsal bulut uygulamaları ve hizmetleri, diğer SaaS hizmetleri ve şirket içi uygulamalar için.

Sıfır Güven kimlik ve cihaz erişim ayarları ve ilkeleri üç katmanda önerilir: başlangıç noktası, kurumsal ve yüksek oranda düzenlenmiş veya sınıflandırılmış verilere sahip ortamlar için özel güvenlik. Bu katmanlar ve bunlara karşılık gelen yapılandırmalar verileriniz, kimlikleriniz ve cihazlarınız arasında tutarlı Sıfır Güven koruma düzeyleri sağlar.

Bu özellikler ve bunların önerileri:

- Microsoft 365 E3 ve Microsoft 365 E5 desteklenir.
- Azure AD'de [Hem Microsoft Güvenli Puanı](../defender/microsoft-secure-score.md) hem de [kimlik puanıyla](/azure/active-directory/fundamentals/identity-secure-score) uyumlu olduğundan kuruluşunuz için bu puanları artırır.
- [Kimlik altyapınızın güvenliğini sağlamak için bu beş adımı uygulamanıza](/azure/security/azure-ad-secure-steps) yardımcı olur.

Kuruluşunuzun benzersiz ortam gereksinimleri veya karmaşıklıkları varsa, başlangıç noktası olarak bu önerileri kullanın. Ancak çoğu kuruluş bu önerileri öngörüldüğü gibi uygulayabilir.

Kuruluş için Microsoft 365 kimlik ve cihaz erişim yapılandırmalarına hızlı bir genel bakış için bu videoyu izleyin.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxEDQ]

> [!NOTE]
> Microsoft ayrıca Office 365 abonelikleri için Enterprise Mobility + Security (EMS) lisansları da satar. EMS E3 ve EMS E5 özellikleri, Microsoft 365 E3 ve Microsoft 365 E5 özellikleriyle eşdeğerdir. Ayrıntılar için bkz. [EMS planları](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing) .

## <a name="intended-audience"></a>Hedeflenen hedef kitle

Bu öneriler, Azure AD (kimlik), Microsoft Intune (cihaz yönetimi) ve Microsoft Purview Information Protection (veri koruması) dahil Microsoft 365 bulut üretkenliği ve güvenlik hizmetleri hakkında bilgi sahibi olan kurumsal mimarlara ve BT uzmanlarına yöneliktir.

### <a name="customer-environment"></a>Müşteri ortamı

Önerilen ilkeler, hem tamamen Microsoft bulutu içinde çalışan kurumsal kuruluşlar hem de bir Azure AD kiracısıyla eşitlenmiş bir şirket içi Active Directory Domain Services (AD DS) ormanı olan karma kimlik altyapısına sahip müşteriler için geçerlidir.

Sağlanan önerilerin çoğu yalnızca Microsoft 365 E5, Microsoft 365 E3 E5 Güvenlik eklentisi, EMS E5 veya Azure AD Premium P2 lisanslarıyla kullanılabilen hizmetlere dayanır.

Microsoft, bu lisanslara sahip olmayan kuruluşlar için en azından tüm Microsoft 365 [planlarına dahil olan güvenlik varsayılanlarını](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) uygulamanızı önerir.

### <a name="caveats"></a>Uyarılar

Kuruluşunuz, bu önerilen yapılandırmalardan farklı ilkeler uygulamanızı gerektirebilecek belirli öneriler de dahil olmak üzere yasal düzenlemelere veya diğer uyumluluk gereksinimlerine tabi olabilir. Bu yapılandırmalar, geçmişte kullanılamayan kullanım denetimlerini önerir. Güvenlik ve üretkenlik arasındaki dengeyi temsil ettiğine inandığımız için bu denetimleri öneririz.

Çok çeşitli kuruluş koruma gereksinimlerini hesaba eklemek için elimizden geleni yaptık, ancak olası tüm gereksinimleri veya kuruluşunuzun tüm benzersiz yönlerini hesaba aktaramadık.

## <a name="three-tiers-of-protection"></a>Üç koruma katmanı

Çoğu kuruluşun güvenlik ve veri korumasıyla ilgili belirli gereksinimleri vardır. Bu gereksinimler sektör segmentlerine ve kuruluşlardaki iş işlevlerine göre farklılık gösterir. Örneğin, hukuk departmanınız ve yöneticileriniz e-posta yazışmaları etrafında diğer iş birimleri için gerekli olmayan ek güvenlik ve bilgi koruma denetimleri gerektirebilir.

Her endüstrinin kendi özel düzenlemeleri de vardır. Tüm olası güvenlik seçeneklerinin listesini ya da sektör segmenti veya iş işlevi başına öneri sağlamak yerine, gereksinimlerinizin ayrıntı düzeyine göre uygulanabilecek üç farklı güvenlik ve koruma düzeyi için öneriler sağlanmıştır.

- **Başlangıç noktası**: Tüm müşterilerin hem verileri hem de verilerinize erişen kimlikleri ve cihazları korumak için en düşük standardı oluşturmasını ve kullanmasını öneririz. Tüm kuruluşlar için başlangıç noktası olarak güçlü bir varsayılan koruma sağlamak için bu önerileri izleyebilirsiniz.
- **Enterprise**: Bazı müşteriler, daha yüksek düzeylerde korunması gereken bir veri alt kümesine sahiptir veya tüm verilerin daha yüksek düzeyde korunmasını gerektirebilir. Microsoft 365 ortamınızdaki tüm veya belirli veri kümelerine daha fazla koruma uygulayabilirsiniz. Benzer güvenlik düzeyleriyle hassas verilere erişen kimlikleri ve cihazları korumanızı öneririz.
- **Özel güvenlik**: Gerektiğinde, birkaç müşteri yüksek oranda sınıflandırılmış, ticari gizli diziler oluşturan veya düzenlenen az miktarda veriye sahiptir. Microsoft, bu müşterilerin kimlikler ve cihazlar için ek koruma da dahil olmak üzere bu gereksinimleri karşılamasına yardımcı olacak özellikler sağlar.

:::image type="content" source="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png" alt-text="Güvenlik konisi" lightbox="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png":::

Bu kılavuz, bu koruma düzeylerinin her biri için kimlikler ve cihazlar için Sıfır Güven korumayı nasıl uygulayabileceğinizi gösterir. Bu kılavuzu kuruluşunuz için en düşük düzeyde kullanın ve ilkeleri kuruluşunuzun özel gereksinimlerini karşılayacak şekilde ayarlayın.

Kimlikleriniz, cihazlarınız ve verileriniz arasında tutarlı koruma düzeyleri kullanmanız önemlidir. Örneğin, yöneticiler, liderler, yöneticiler ve diğerleri&mdash; gibi öncelikli hesapları&mdash; olan kullanıcılar için koruma, kimlikleri, cihazları ve erişdikleri veriler için aynı koruma düzeyini içermelidir. 
<!--

The **Zero Trust identity and device protection for Microsoft 365** architecture model shows you which capabilities are comparable.

[![Thumb image for Zero Trust Identity and device protection for Microsoft 365 poster.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-thumbnail.png)](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) <br> [View as a PDF](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.pdf)  \| [Download as a Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.vsdx)

--> 

Ayrıca, Microsoft 365 depolanan [bilgileri korumak için veri gizliliği düzenlemeleri için bilgi koruma](../../solutions/information-protection-deploy.md) dağıtma çözümüne bakın.

## <a name="security-and-productivity-trade-offs"></a>Güvenlik ve üretkenlik dengeleri

Herhangi bir güvenlik stratejisinin uygulanması, güvenlik ve üretkenlik arasında dengeyi sağlamayı gerektirir. Her kararın güvenlik, işlevsellik ve kullanım kolaylığı dengesini nasıl etkilediğini değerlendirmek yararlı olur.

:::image type="content" source="../../media/microsoft-365-policies-configurations/security-triad.png" alt-text="Güvenlik triad dengeleme güvenliği, işlevselliği ve kullanım kolaylığı" lightbox="../../media/microsoft-365-policies-configurations/security-triad.png":::

Sağlanan öneriler aşağıdaki ilkelere dayanır:

- Kullanıcılarınızı tanıyıp güvenlik ve işlevsel gereksinimlerine karşı esnek olun.
- Tam zamanında bir güvenlik ilkesi uygulayın ve bunun anlamlı olduğundan emin olun.

## <a name="services-and-concepts-for-zero-trust-identity-and-device-access-protection"></a>Sıfır Güven kimliği ve cihaz erişim korumasına yönelik hizmetler ve kavramlar

kurumsal Microsoft 365, büyük kuruluşlar için herkesin yaratıcı olmasını ve güvenli bir şekilde birlikte çalışmasını sağlamak için tasarlanmıştır.

Bu bölüm, Sıfır Güven kimlik ve cihaz erişimi için önemli olan Microsoft 365 hizmetlerine ve özelliklerine genel bir bakış sağlar.

### <a name="azure-ad"></a>Azure AD

Azure AD, tam bir kimlik yönetimi özellikleri paketi sağlar. Erişimin güvenliğini sağlamak için bu özellikleri kullanmanızı öneririz.

|Yetenek veya özellik|Açıklama|Lisanslama|
|---|---|---|
|[Çok faktörlü kimlik doğrulaması (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA, kullanıcıların kullanıcı parolası ve Microsoft Authenticator uygulamasından gelen bildirim veya telefon görüşmesi gibi iki doğrulama biçimi sağlamasını gerektirir. MFA, çalınan kimlik bilgilerinin ortamınıza erişmek için kullanılabilmesi riskini büyük ölçüde azaltır. Microsoft 365, MFA tabanlı oturum açma işlemleri için Azure AD Multi-Factor Authentication hizmetini kullanır.|Microsoft 365 E3 veya E5|
|[Koşullu Erişim](/azure/active-directory/conditional-access/overview)|Azure AD, kullanıcı oturum açma koşullarını değerlendirir ve izin verilen erişimi belirlemek için Koşullu Erişim ilkelerini kullanır. Örneğin, bu kılavuzda hassas verilere erişim için cihaz uyumluluğu gerektiren bir Koşullu Erişim ilkesinin nasıl oluşturulacağını gösteririz. Bu, kendi cihazına ve çalınan kimlik bilgilerine sahip bir korsanın hassas verilerinize erişme riskini büyük ölçüde azaltır. Ayrıca cihazlardaki hassas verileri de korur çünkü cihazların sistem durumu ve güvenliği için belirli gereksinimleri karşılaması gerekir.|Microsoft 365 E3 veya E5|
|[Azure AD grupları](/azure/active-directory/fundamentals/active-directory-manage-groups)|Koşullu Erişim ilkeleri, Intune ile cihaz yönetimi ve hatta kuruluşunuzdaki dosya ve sitelere yönelik izinler, kullanıcı hesaplarına veya Azure AD gruplarına atamayı kullanır. Uyguladığınız koruma düzeylerine karşılık gelen Azure AD grupları oluşturmanızı öneririz. Örneğin, yönetici personeliniz korsanlar için büyük olasılıkla daha yüksek değer hedefleridir. Bu nedenle, bu çalışanların kullanıcı hesaplarını bir Azure AD grubuna eklemek ve bu grubu Koşullu Erişim ilkelerine ve erişim için daha yüksek bir koruma düzeyini zorlayan diğer ilkelere atamak mantıklıdır.|Microsoft 365 E3 veya E5|
|[Cihaz kaydı](/azure/active-directory/devices/overview)|Cihaz için bir kimlik oluşturmak için bir cihazı Azure AD'ye kaydedersiniz. Bu kimlik, kullanıcı oturum açtığında cihazın kimliğini doğrulamak ve etki alanına katılmış veya uyumlu bilgisayarlar gerektiren Koşullu Erişim ilkelerini uygulamak için kullanılır. Bu kılavuz için, etki alanına katılmış Windows bilgisayarları otomatik olarak kaydetmek için cihaz kaydını kullanırız. Cihaz kaydı, Intune cihazları yönetmek için bir önkoşuldur.|Microsoft 365 E3 veya E5|
|[Azure AD Kimlik Koruması](/azure/active-directory/identity-protection/overview)|Kuruluşunuzun kimliklerini etkileyen olası güvenlik açıklarını algılamanıza ve otomatik düzeltme ilkesini düşük, orta ve yüksek oturum açma riski ile kullanıcı riski olarak yapılandırmanıza olanak tanır. Bu kılavuz, çok faktörlü kimlik doğrulaması için Koşullu Erişim ilkelerini uygulamak için bu risk değerlendirmesine dayanır. Bu kılavuz, hesaplarında yüksek riskli etkinlik algılandığında kullanıcıların parolalarını değiştirmelerini gerektiren bir Koşullu Erişim ilkesi de içerir.|Microsoft 365 E5, E5 Güvenlik eklentisi, EMS E5 veya Azure AD Premium P2 lisanslarıyla Microsoft 365 E3|
|[Kendi kendine parola sıfırlama (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Yöneticinin denetleyebileceği birden çok kimlik doğrulama yönteminin doğrulanmasını sağlayarak kullanıcılarınızın parolalarını güvenli bir şekilde ve yardım masası müdahalesi olmadan sıfırlamasına izin verin.|Microsoft 365 E3 veya E5|
|[Azure AD parola koruması](/azure/active-directory/authentication/concept-password-ban-bad)|Bilinen zayıf parolaları ve bunların değişkenlerini ve kuruluşunuza özgü ek zayıf terimleri algılayın ve engelleyin. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısında tüm kullanıcılara otomatik olarak uygulanır. Özel yasaklanmış parola listesinde ek girdiler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirdiğinde veya sıfırladığında, bu yasaklanmış parola listeleri güçlü parolaların kullanımını zorunlu kılmak için denetlenir.|Microsoft 365 E3 veya E5|

Intune ve Azure AD nesneleri, ayarları ve alt hizmetleri de dahil olmak üzere Sıfır Güven kimliğin ve cihaz erişiminin bileşenleri aşağıdadır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-components.png" alt-text="Sıfır Güven kimliği ve cihaz erişiminin bileşenleri" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-components.png":::

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](/intune/introduction-intune), Microsoft'un bulut tabanlı mobil cihaz yönetimi hizmetidir. Bu kılavuz, Intune Windows bilgisayarların cihaz yönetimini ve cihaz uyumluluk ilkesi yapılandırmalarını önerir. Intune cihazların uyumlu olup olmadığını belirler ve bu verileri Koşullu Erişim ilkeleri uygularken kullanmak üzere Azure AD'ye gönderir.

#### <a name="intune-app-protection"></a>Uygulama korumasını Intune

[Intune uygulama koruma](/intune/app-protection-policy) ilkeleri, cihazları yönetime kaydederek veya kaydetmeden mobil uygulamalarda kuruluşunuzun verilerini korumak için kullanılabilir. Intune bilgilerin korunmasına, çalışanlarınızın üretken olmaya devam etmelerine ve veri kaybını önlemeye yardımcı olur. Uygulama düzeyinde ilkeler uygulayarak şirket kaynaklarına erişimi kısıtlayabilir ve verileri BT departmanınızın denetiminde tutabilirsiniz.

Bu kılavuzda, onaylı uygulamaların kullanımını zorunlu kılmak ve bu uygulamaların iş verilerinizle nasıl kullanılabileceğini belirlemek için önerilen ilkelerin nasıl oluşturulacağı gösterilmektedir.

### <a name="microsoft-365"></a>Microsoft 365

Bu kılavuzda Microsoft Teams, Exchange, SharePoint ve OneDrive dahil olmak üzere Microsoft 365 bulut hizmetlerine erişimi korumak için bir dizi ilkenin nasıl uygulandığı gösterilmektedir. Bu ilkeleri uygulamaya ek olarak, aşağıdaki kaynakları kullanarak kiracınız için koruma düzeyini yükseltmenizi öneririz:

- [Daha fazla güvenlik için kiracınızı yapılandırma](tenant-wide-setup-for-increased-security.md)

  Kiracınız için başlangıç noktası güvenliği için geçerli olan Öneriler.

- [Güvenlik yol haritası: İlk 30 gün, 90 gün ve sonrası için en önemli öncelikler](security-roadmap.md)

  Günlüğe kaydetme, veri idaresi, yönetici erişimi ve tehdit koruması gibi Öneriler.

### <a name="windows-11-or-windows-10-with-microsoft-365-apps-for-enterprise"></a>Kurumlar için Microsoft 365 Uygulamaları ile Windows 11 veya Windows 10

Kurumlar için Microsoft 365 Uygulamaları ile Windows 11 veya Windows 10 bilgisayarlar için önerilen istemci ortamıdır. Azure hem şirket içi hem de Azure AD için mümkün olan en sorunsuz deneyimi sağlamak üzere tasarlandığından Windows 11 veya Windows 10 öneririz. Windows 11 veya Windows 10, Intune aracılığıyla yönetilebilen gelişmiş güvenlik özellikleri de içerir. Kurumlar için Microsoft 365 Uygulamaları, Office uygulamalarının en son sürümlerini içerir. Bunlar, daha güvenli ve Koşullu Erişim gereksinimi olan modern kimlik doğrulamasını kullanır. Bu uygulamalar ayrıca gelişmiş uyumluluk ve güvenlik araçları içerir.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Bu özellikleri korumanın üç katmanına uygulama

Aşağıdaki tabloda, bu özelliklerin üç koruma katmanında kullanılmasına yönelik önerilerimiz özetlemektedir.

|Koruma mekanizması|Başlangıç noktası|Enterprise|Özel güvenlik|
|---|---|---|---|
|**MFA'yı zorunlu kılma**|Orta veya üst düzey oturum açma riskinde|Düşük veya daha yüksek oturum açma riskinde|Tüm yeni oturumlarda|
|**Parola değişikliğini zorunlu kılma**|Yüksek riskli kullanıcılar için|Yüksek riskli kullanıcılar için|Yüksek riskli kullanıcılar için|
|**Intune uygulama korumasını zorunlu kılma**|Evet|Evet|Evet|
|**Kuruluşa ait cihaz için Intune kaydını zorunlu kılma**|Uyumlu veya etki alanına katılmış bir bilgisayar iste, ancak kendi cihazlarını getir (KCG) telefon ve tabletlere izin ver|Uyumlu veya etki alanına katılmış bir cihaz gerektirme|Uyumlu veya etki alanına katılmış bir cihaz gerektirme|

## <a name="device-ownership"></a>Cihaz sahipliği

Yukarıdaki tablo, birçok kuruluşun kuruluşa ait cihazların yanı sıra iş gücü genelinde mobil üretkenliği sağlamak için kişisel veya BYOD'ların bir karışımını destekleme eğilimini yansıtır. Intune uygulama koruma ilkeleri, e-postanın hem kuruluşa ait cihazlarda hem de KDD'lerde Outlook mobil uygulamasından ve diğer Office mobil uygulamalarından dışarı sızmaya karşı korunmasını sağlar.

Ek korumalar ve denetim uygulamak için kuruluşa ait cihazların Intune veya etki alanına katılmış olarak yönetilmesini öneririz. Veri duyarlılığına bağlı olarak, kuruluşunuz belirli kullanıcı popülasyonları veya belirli uygulamalar için BYOD'lere izin vermemeyi seçebilir.

## <a name="deployment-and-your-apps"></a>Dağıtım ve uygulamalarınız

Azure AD ile tümleşik uygulamalarınız için Sıfır Güven kimlik ve cihaz erişim yapılandırmasını yapılandırmadan ve dağıtmadan önce şunları yapmalısınız:

- Kuruluşunuzda hangi uygulamaları kullanmak istediğinize karar verin.
- Uygun koruma düzeylerini sağlayan ilke kümelerini belirlemek için bu uygulama listesini analiz edin.

  Her biri uygulama için ayrı ilke kümeleri oluşturmamalısınız çünkü bunların yönetimi zahmetli hale gelebilir. Microsoft, aynı kullanıcılar için aynı koruma gereksinimlerine sahip uygulamalarınızı gruplandırmanızı önerir.

  Örneğin, başlangıç noktası koruması için tüm kullanıcılarınız için tüm Microsoft 365 uygulamalarını ve insan kaynakları veya finans departmanları tarafından kullanılanlar gibi tüm hassas uygulamalar için ikinci bir ilke kümesini içeren bir ilke kümeniz olabilir ve bunları bu gruplara uygulayabilirsiniz.

Güvenli hale getirmek istediğiniz uygulamalar için ilke kümesini belirledikten sonra, ilkeleri kullanıcılarınıza artımlı olarak dağıtın ve bu aradaki sorunları giderin.

Örneğin, tüm Microsoft 365 uygulamalarınız için kullanılacak ilkeleri yalnızca Exchange ek değişikliklerle Exchange için yapılandırın. Bu ilkeleri kullanıcılarınıza dağıtıp tüm sorunları çözebilirsiniz. Ardından, ek değişiklikleriyle Teams ekleyin ve bunu kullanıcılarınıza dağıtin. Ardından, ek değişiklikleriyle SharePoint ekleyin. Bu başlangıç noktası ilkelerini tüm Microsoft 365 uygulamaları içerecek şekilde güvenle yapılandırana kadar kalan uygulamalarınızı eklemeye devam edin.

Benzer şekilde, hassas uygulamalarınız için ilke kümesini oluşturun ve tek seferde bir uygulama ekleyin ve hepsi hassas uygulama ilke kümesine dahil edilene kadar tüm sorunları gözden geçirin.

Microsoft, bazı istenmeyen yapılandırmalara neden olabileceği için tüm uygulamalar için geçerli olan ilke kümeleri oluşturmamanızı önerir. Örneğin, tüm uygulamaları engelleyen ilkeler yöneticilerinizi Azure portal ve dışlamalar Microsoft Graph gibi önemli uç noktalar için yapılandırılamaz.

## <a name="steps-to-configure-zero-trust-identity-and-device-access"></a>Sıfır Güven kimliği ve cihaz erişimini yapılandırma adımları

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png" alt-text="Sıfır Güven kimliği ve cihaz erişimini yapılandırma adımları" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png":::

1. Önkoşul kimlik özelliklerini ve ayarlarını yapılandırın.
2. Ortak kimliği yapılandırın ve Koşullu Erişim ilkelerine erişin.
3. Konuk ve dış kullanıcılar için Koşullu Erişim ilkelerini yapılandırın.
4. Microsoft Teams, Exchange ve SharePoint ve Microsoft Defender for Cloud Apps ilkeleri olarak Microsoft 365&mdash; bulut uygulamaları&mdash; için Koşullu Erişim ilkelerini yapılandırın.

kimlik ve cihaz erişimini Sıfır Güven yapılandırdıktan sonra, dikkate alınacak ek özelliklerin aşamalı denetim listesi için [Azure AD özellik dağıtım kılavuzuna](/azure/active-directory/fundamentals/active-directory-deployment-checklist-p2) ve erişimi korumak, izlemek ve denetlemek için [Azure AD Kimlik İdaresi'ne](/azure/active-directory/governance/) bakın.

## <a name="next-step"></a>Sonraki adım

[Sıfır Güven kimlik ve cihaz erişim ilkelerini uygulamak için önkoşul çalışması](identity-access-prerequisites.md)
