---
title: Dosya Teams güvenliğinin üç katmanına sahip dosya ayarlarını yapılandırma
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
- m365solution-securecollab
- m365solution-scenario
ms.custom:
- Ent_Architecture
- seo-marvel-jun2020
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
recommendations: false
description: Korumanın üç katmanını kullanarak Teams paylaşımı güvenliği ve işbirliği kolaylığıyla güvenliği dengelemeyi daha iyi bir dosya paylaşımı güvenliği için nasıl yapılandırırsanız öğrenin.
ms.openlocfilehash: 279e338af6db4d82291209deb66e1ea1eef74630
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988138"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Dört Teams koruma katmanıyla yapılandırma

Bu dizide yer alan makaleler, güvenliği işbirliği kolaylığıyla dengede sağlayan dosya koruması için Microsoft Teams'de ve ilişkili SharePoint sitelerinde ekipleri yapılandırmaya yönelik öneriler sağlar.

Bu makalede, en açık paylaşım ilkelerine sahip bir genel ekiple başlayan dört farklı yapılandırma tanımlanmıştır. Her ek yapılandırma, koruma için anlamlı bir adımı temsil ederken, ekiplerde depolanan dosyalara erişme ve bu dosyalar üzerinde işbirliği yapma özelliği, ilgili ekip üyelerine indir indirildi. 

Bu makaledeki yapılandırmalar Microsoft'un veriler, kimlikler ve cihazlar için üç koruma katmanıyla ilgili önerileriyle uyumludur:

- Taban çizgisi koruması

- hassas koruma

- Çok hassas koruma

Her katman için önerilen bu katman ve özellikler hakkında daha fazla bilgi için bkz. Kurumsal [mimarlar için Microsoft bulutu çizimleri](./cloud-architecture-models.md)


## <a name="three-tiers-at-a-glance"></a>Bir bakışta üç katman

Aşağıdaki tabloda her katman için yapılandırmalar özetlenmiştir. Başlangıç noktası önerileri olarak bu yapılandırmaları kullanın ve yapılandırmaları, kuruma uygun ihtiyaçları karşılayacak şekilde ayarlayın. Her katmana ihtiyacınız olabilir.

|-|Taban Çizgisi (Genel)|Taban çizgisi (Özel)|Hassas|Çok hassas|
|:-----|:-----|:-----|:-----|:-----|
|Özel ekip veya genel ekip|Genel|Özel|Özel|Özel|
|Who erişiminiz var mı?|B2B kullanıcıları dahil, kuruluşta herkes.|Yalnızca ekibin üyeleri. Başkaları ilişkili siteye erişim isteğinda  olabilir.|Yalnızca ekibin üyeleri.|Yalnızca ekibin üyeleri.|
|Özel kanallar|Sahipler ve üyeler özel kanallar oluşturabilir|Sahipler ve üyeler özel kanallar oluşturabilir|Yalnızca sahipler özel kanallar oluşturabilir|Yalnızca sahipler özel kanallar oluşturabilir|
|Site düzeyinde konuk erişimi|**Yeni ve mevcut konuklar** (varsayılan).|**Yeni ve mevcut konuklar** (varsayılan).|**Yeni ve mevcut konuklar veya** **Ekip gereksinimlerine bağlı olarak** yalnızca kuruluşta olan kişiler.|**Yeni ve mevcut konuklar veya** **Ekip gereksinimlerine bağlı olarak** yalnızca kuruluşta olan kişiler.|
|Site paylaşım ayarları|**Site sahipleri ve üyeleri ve Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir, ancak yalnızca site sahipleri siteyi paylaşabilir**.|**Site sahipleri ve üyeleri ve Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir, ancak yalnızca site sahipleri siteyi paylaşabilir**.|**Site sahipleri ve üyeleri ve Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir, ancak yalnızca site sahipleri siteyi paylaşabilir**.|**Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir**.<br>Erişim istekleri **Kapalı.**|
|Site düzeyindeki unmanaged cihaz erişimi|**Masaüstü uygulamalardan, mobil uygulamalardan ve web'den tam erişim** (varsayılan).|**Masaüstü uygulamalardan, mobil uygulamalardan ve web'den tam erişim** (varsayılan).|**Sınırlı, yalnızca web erişimine izin verme**.|**Erişimi engelin**.|
|Varsayılan paylaşım bağlantı türü|**Yalnızca kuruluşta yer alan kişiler**|**Yalnızca kuruluşta yer alan kişiler**|**Belirli kişiler**|**Mevcut erişimi olan kişiler**|
|Duyarlılık etiketleri|Yok|Yok|Ekibi sınıflandırmak ve konuk paylaşımını ve yöneticisi olmayan cihaz erişimini kontrol etmek için kullanılan duyarlılık etiketi.|Ekibi sınıflandırmak ve konuk paylaşımını ve yöneticisi olmayan cihaz erişimini kontrol etmek için kullanılan duyarlılık etiketi. Etiket, dosyalar üzerinde dosyaları şifrelemek için de kullanılabilir.|

Çok hassas seçeneğinin bir çeşitleci olan [Teams](secure-teams-security-isolation.md), ek güvenlik sağlayan tek bir ekip için benzersiz bir duyarlılık etiketi kullanır. Dosyaları şifrelemek için bu etiketi kullanabilirsiniz ve yalnızca o ekibin üyeleri okuyabilir.

Taban çizgisi koruması genel ve özel ekipleri içerir. Açık ekipler kuruluşta herkes tarafından keşfedilir ve erişilir. Özel ekipler yalnızca ekibin üyeleri tarafından keşfedilir ve erişilebilir. Bu yapılandırmaların her ikisi de izin yönetimine yardımcı SharePoint sitenin ekip sahipleriyle paylaşımını kısıtlar.

Teams ve çok hassas koruma için kullanılan özel ekipler, paylaşım ve ilişkili site için erişim isteğinin sınırlı olduğu ve duyarlılık etiketlerinin konuk paylaşımı, cihaz erişimi ve içerik şifrelemesi ile ilgili ilkeler ayarlamak için kullandığı özel ekiplerdir.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Hassas ve çok hassas katman, ekibin ve dosyalarının güvenliğini sağlamak için duyarlılık etiketleri kullanır. Bu katmanları uygulamak için, farklı sitelerde, gruplarda ve sitelerde [Microsoft Teams Office 365 için duyarlılık SharePoint etkinleştirmeniz gerekir](../compliance/sensitivity-labels-teams-groups-sites.md).

Taban çizgisi katmanı duyarlılık etiketleri gerektirmese de, bir "genel" etiket oluşturmayı ve ardından tüm ekiplerin etiketlenmiş olarak etiketlenmiş olarak gerektirmesini göz önünde bulundurabilirsiniz. Bu, kullanıcıların bir ekip oluşturdukta duyarlılık konusunda bilinçli bir seçim yapmalarını sağlamaya yardımcı olur. Hassas veya çok hassas katmanları dağıtmayı planlıyorsanız, taban çizgisi ekipleri için ve hassas değil dosyalar için kullanabileceğiniz bir "genel" etiket oluşturmanız önerilir.

Duyarlılık etiketlerini kullanmaya yeni başladıysanız, kullanmaya başlama için Duyarlılık [etiketlerini kullanmaya başlama'ya](../compliance/get-started-with-sensitivity-labels.md) okumanizi öneririz. 

Kuruluşta zaten duyarlılık etiketleri sunduysanız, etiketlerin hassas ve çok hassas katmanlarda nasıl kullanıldıklarını genel etiket stratejinize nasıl uyduklarını düşünün. 

## <a name="sharing-the-sharepoint-site"></a>SharePoint sitesi paylaşma

Her ekibin, belgelerin depolandığı SharePoint bir siteyle ilişkilendirilmiş bir site vardır. (Bu, bir **ekip** kanalında Dosyalar sekmesidir.) Site SharePoint kendi izin yönetimini korur, ancak ekip izinlerine bağlıdır. Ekip sahipleri site sahipleri olarak, ekip üyeleri de ilişkili siteye site üyeleri olarak dahil edilir.

Sonuçta elde edilen izinler şunları sağlar:

- Ekip sahipleri siteyi yönetmeye ve site içeriği üzerinde tam denetime sahip olur.
- Sitede dosya oluşturmak ve düzenlemek için ekip üyeleri. 

Varsayılan olarak, ekip sahipleri ve üyeleri siteyi, ek ekip üyelerine eklemeden ekip dışındaki İnsanlarla paylaşabilir. Kullanıcı yönetimini karmaşıklaştırması ve ekip üyesi olmayan kişilerin ekip sahipleri bunu fark etmeden ekip dosyalarına erişmesine yol açamadan bu durumu önerilmez. Bunu önlemeye yardımcı olmak için, temel koruma düzeyinden başlayarak, yalnızca sahiplerin siteyi doğrudan paylaşmasına izin verilenleri öneririz.

Ekipler salt okunur izin seçeneğine sahip değildir, ancak SharePoint vardır. Ekip dosyalarını görüntüley okuyabile ihtiyacı olan ancak düzenleyene kadar iş ortağı gruplarının paydaşları varsa, okuma izinlerine sahip olarak bunları doğrudan SharePoint siteye eklemeyi göz önünde bulundurabilirsiniz.

## <a name="sharing-files-and-folders"></a>Dosya ve klasör paylaşma

Varsayılan olarak, hem ekip sahipleri hem de üyeleri dosyaları ve klasörleri ekip dışındaki kişiler ile paylaşabilir. Bu, konuk paylaşımına izin verdiysanız, kuruluş dışındaki kişiler dahil olabilir. Üç katmanda da, yanlışlıkla paylaşımı önlemek için varsayılan paylaşım bağlantı türünü güncelleştiriz. Çok hassas katmanda, bu paylaşımı yalnızca ekip sahipleriyle kısıtlarız.

## <a name="guest-sharing"></a>Konuk paylaşımı

Kuruluş dışından çalışanlarla işbirliği yapmak zorundaysanız, en iyi paylaşım ve yönetim [deneyimi için Azure AD B2B ile SharePoint ve OneDrive](/sharepoint/sharepoint-azureb2b-integration-preview) tümleştirmeyi yapılandırmanızı öneririz.

Teams paylaşımı varsayılan olarak açıktır, ancak gerekirse bir duyarlılık etiketi kullanarak hassas ve çok hassas katmanlarda bu paylaşımı kapatmış olursanız.

Çok hassas katmanda, duyarlılık etiketini uygulandığı dosyaları şifrele olacak şekilde yapılandır ediyoruz. Konukların bu dosyalara erişimi olması için ihtiyacınız varsa, etiketi  oluşturarak bu dosyalara izin verebilirsiniz.

Kuruluş dışındanlarıyla işbirliği yapmak gerekirse, temel katman için ve hassas veya çok hassas katmanlarda konuk paylaşımını açık bırakmanızı kesinlikle öneririz. E-posta iletilerine Microsoft 365 olarak dosya göndermeye göre çok daha güvenli ve yönetilebilir bir paylaşım deneyimi sağlayan konuk paylaşımı özellikleri. Ayrıca, kullanıcıların yasal dış işbirliği yapanlarla paylaşmak üzere unoverned tüketici ürünlerini kullanmaları için GÖLGELE riskini azaltır.

Güvenli ve üretken bir konuk paylaşım ortamı oluşturmak için aşağıdaki başvurulara bakın:

- [Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)
- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Unmanaged cihazlarından erişim

Hassas ve çok hassas katmanlar için, hassas etiketlere ve SharePoint içeriğine erişimi kısıtlarız. Azure AD koşullu erişimi, konum, risk, cihaz uyumluluğu Microsoft 365 diğer faktörlere dayalı sınırlamalar da dahil olmak üzere kişilerin posta hizmetine nasıl erişeni belirlemek için birçok seçenek sunar. Koşullu Erişim nedir [? makalelerini okumanızı ve](/azure/active-directory/conditional-access/overview) hangi ek ilkelerin organizasyonunıza uygun olabileceğini göz önünde bulundurmanızı öneririz.

Konukların genellikle kuruluşları tarafından yönetilen cihazları olmadığını unutmayın. Katmanlardan herhangi birsinde konuklara izin verirsiniz, ekiplere ve sitelere erişmek için hangi tür cihazları kullan olduklarını düşünün ve yönetim dışı cihaz ilkelerinizi buna göre ayarlayın.

### <a name="control-device-access-across-microsoft-365"></a>Farklı cihazda cihaz erişimini Microsoft 365

Duyarlılık etiketlerinin devre dışı bırakıldı cihaz ayarı yalnızca erişim SharePoint etkiler. Unmanaged devices beyond SharePoint, you can [Create an Azure Active Directory conditional access policy](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) for all apps and services in your organization instead. Bu ilkeyi özel olarak Bulut [Microsoft 365 veya](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365) eylemler **altında Office 365** **bulut uygulamasını seçin**.

![Office 365 koşullu erişim ilkesinde bulut Azure Active Directory ekran görüntüsü.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Tüm hizmet hizmetlerini etkileyen bir ilke Microsoft 365, kullanıcılarınız için daha iyi bir güvenlik ve daha iyi bir deneyime neden olabilir. Örneğin, yalnızca SharePoint'te yöneticisi olmayan cihazlara erişimi engelleyebilirsiniz, kullanıcılar bir ekipte, yöneticisi olmayan bir cihazla sohbete erişim iznine sahip olabilir, ancak Dosyalar sekmesine erişmeye ettiklerde erişimi kaybederler.  Office 365 bulut uygulamasının kullanımı, hizmet bağımlılıkları ile ilgili sorunları önlemeye yardımcı [olur.](/azure/active-directory/conditional-access/service-dependencies)

## <a name="next-step"></a>Sonraki adım

Temel [koruma düzeyini yapılandırarak başlayabilirsiniz](configure-teams-baseline-protection.md). Gerekirse, temelin [üstüne hassas koruma](configure-teams-sensitive-protection.md) [ve çok hassas](configure-teams-highly-sensitive-protection.md) koruma eklersiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Güvenlik ve uyumluluk Microsoft Teams](/microsoftteams/security-compliance-overview)

[Güvenlik ve uyumluluk merkezinde uyarı ilkeleri](../compliance/alert-policies.md)
