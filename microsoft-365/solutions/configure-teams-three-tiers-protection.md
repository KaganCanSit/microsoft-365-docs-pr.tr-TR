---
title: Teams üç dosya paylaşımı güvenliği katmanıyla yapılandırma
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
description: Güvenliği işbirliği kolaylığıyla dengelemek üzere üç koruma katmanı kullanarak daha iyi dosya paylaşımı güvenliği için Teams yapılandırmayı öğrenin.
ms.openlocfilehash: 4d287d342371a8182a4c9de5742d2d45ca01a1c6
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012483"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Üç koruma katmanıyla Teams yapılandırma

Bu serideki makaleler, Microsoft Teams ekiplerini ve ilişkili SharePoint sitelerini işbirliği kolaylığıyla güvenliği dengeleyen dosya koruması için yapılandırmaya yönelik öneriler sağlar.

Bu makale, en açık paylaşım ilkelerine sahip genel bir ekiple başlayarak dört farklı yapılandırmayı tanımlar. Her ek yapılandırma, korumada anlamlı bir adımı temsil ederken, ekiplerde depolanan dosyalara erişim ve bu dosyalar üzerinde işbirliği yapma özelliği ilgili ekip üyeleri kümesine indirgendi. 

Bu makaledeki yapılandırmalar, Microsoft'un veri, kimlik ve cihazlar için üç koruma katmanı önerileriyle uyumlu:

- Temel koruma

- hassas koruma

- Son derece hassas koruma

Her katman için önerilen bu katmanlar ve özellikler hakkında daha fazla bilgi için bkz. [Kurumsal mimarlar için Microsoft bulutu çizimleri](./cloud-architecture-models.md)

## <a name="three-tiers-at-a-glance"></a>Bir bakışta üç katman

Aşağıdaki tabloda her katman için yapılandırmalar özetlemektedir. Başlangıç noktası önerileri olarak bu yapılandırmaları kullanın ve yapılandırmaları kuruluşunuzun gereksinimlerini karşılayacak şekilde ayarlayın. Her katmana ihtiyacınız olmayabilir.

|&nbsp;|Temel (Genel)|Temel (Özel)|Hassas|Son derece hassas|
|:-----|:-----|:-----|:-----|:-----|
|Özel veya genel ekip|Kamu|Özel|Özel|Özel|
|Who erişimi var?|B2B kullanıcıları dahil olmak üzere kuruluştaki herkes.|Yalnızca ekibin üyeleri. Diğerleri ilişkili siteye erişim isteyebilir.|Yalnızca ekibin üyeleri.|Yalnızca ekibin üyeleri.|
|Özel kanallar|Sahipler ve üyeler özel kanallar oluşturabilir|Sahipler ve üyeler özel kanallar oluşturabilir|Yalnızca sahipler özel kanallar oluşturabilir|Yalnızca sahipler özel kanallar oluşturabilir|
|Paylaşılan kanallar|Sahipler ve üyeler paylaşılan kanallar oluşturabilir|Sahipler ve üyeler paylaşılan kanallar oluşturabilir|Yalnızca sahipler paylaşılan kanallar oluşturabilir|Yalnızca sahipler paylaşılan kanallar oluşturabilir|
|Site düzeyinde konuk erişimi|**Yeni ve mevcut konuklar** (varsayılan).|**Yeni ve mevcut konuklar** (varsayılan).|Ekip gereksinimlerine bağlı olarak **yeni ve mevcut konuklar** veya **Yalnızca kuruluşunuzdaki kişiler**.|Ekip gereksinimlerine bağlı olarak **yeni ve mevcut konuklar** veya **Yalnızca kuruluşunuzdaki kişiler**.|
|Site paylaşım ayarları|**Site sahipleri ve üyeleri ile Düzenleme izinlerine sahip kişiler dosya ve klasörleri paylaşabilir, ancak siteyi yalnızca site sahipleri paylaşabilir**.|**Site sahipleri ve üyeleri ile Düzenleme izinlerine sahip kişiler dosya ve klasörleri paylaşabilir, ancak siteyi yalnızca site sahipleri paylaşabilir**.|**Site sahipleri ve üyeleri ile Düzenleme izinlerine sahip kişiler dosya ve klasörleri paylaşabilir, ancak siteyi yalnızca site sahipleri paylaşabilir**.|**Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir**.<br>Erişim istekleri **Kapalı**.|
|Site düzeyinde yönetilmeyen cihaz erişimi|**Masaüstü uygulamalarından, mobil uygulamalardan ve web'den tam erişim** (varsayılan).|**Masaüstü uygulamalarından, mobil uygulamalardan ve web'den tam erişim** (varsayılan).|**Sınırlı, yalnızca web erişimine izin verin**.|**Erişimi engelle**.|
|Varsayılan paylaşım bağlantı türü|**Yalnızca kuruluşunuzdaki kişiler**|**Yalnızca kuruluşunuzdaki kişiler**|**Belirli kişiler**|**Mevcut erişimi olan kişiler**|
|Duyarlılık etiketleri|Yok|Yok|Ekibi sınıflandırmak ve konuk paylaşımını ve yönetilmeyen cihaz erişimini denetlemek için kullanılan duyarlılık etiketi.|Ekibi sınıflandırmak ve konuk paylaşımını ve yönetilmeyen cihaz erişimini denetlemek için kullanılan duyarlılık etiketi. Etiket, dosyaları şifrelemek için dosyalarda da kullanılabilir.|

Güvenlik [yalıtımına sahip Teams](secure-teams-security-isolation.md) Yüksek oranda hassas seçeneğinin bir varyasyonu, ek güvenlik sağlayan bir ekip için benzersiz bir duyarlılık etiketi kullanır. Dosyaları şifrelemek için bu etiketi kullanabilirsiniz ve yalnızca bu ekibin üyeleri bunları okuyabilir.

Temel koruma, genel ve özel ekipleri içerir. Genel ekipler kuruluştaki herkes tarafından bulunabilir ve bu ekiplere erişilebilir. Özel ekipler yalnızca ekibin üyeleri tarafından bulunabilir ve bunlara erişebilir. Bu yapılandırmaların her ikisi de, izin yönetimine yardımcı olmak için ilişkili SharePoint sitesinin ekip sahipleriyle paylaşılması kısıtlar.

Hassas ve son derece hassas koruma için Teams, paylaşım ve ilişkili site için erişim isteği sınırlı olan özel ekiplerdir ve konuk paylaşımı, cihaz erişimi ve içerik şifrelemesi ile ilgili ilkeler ayarlamak için duyarlılık etiketleri kullanılır.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Hassas ve son derece hassas katmanlar, ekibin ve dosyalarının güvenliğini sağlamaya yardımcı olmak için duyarlılık etiketlerini kullanır. Bu katmanları uygulamak için Microsoft Teams[, Office 365 Grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini](../compliance/sensitivity-labels-teams-groups-sites.md) etkinleştirmeniz gerekir.

Temel katman duyarlılık etiketleri gerektirmez, ancak bir "genel" etiket oluşturmayı ve ardından tüm ekiplerin etiketlenmelerini zorunlu kılabilirsiniz. Bu, kullanıcıların ekip oluştururken duyarlılık konusunda bilinçli bir seçim yapmalarına yardımcı olur. Hassas veya son derece hassas katmanları dağıtmayı planlıyorsanız, temel ekipler ve hassas olmayan dosyalar için kullanabileceğiniz bir "genel" etiket oluşturmanızı öneririz.

Duyarlılık etiketlerini kullanmaya yeni başladıysanız, başlamak için [duyarlılık etiketleriyle Kullanmaya başlayın](../compliance/get-started-with-sensitivity-labels.md) okumanızı öneririz. 

Kuruluşunuzda duyarlılık etiketlerini zaten dağıtmışsanız, hassas ve son derece hassas katmanlarda kullanılan etiketlerin genel etiket stratejinize nasıl uyyacağını göz önünde bulundurun. 

## <a name="sharing-the-sharepoint-site"></a>SharePoint sitesini paylaşma

Her ekibin belgelerin depolandığı ilişkili bir SharePoint sitesi vardır. (Bu, teams kanalındaki **Dosyalar** sekmesidir.) SharePoint sitesi kendi izin yönetimini korur, ancak ekip izinlerine bağlıdır. Ekip sahipleri site sahibi olarak, ekip üyeleri ise ilişkili siteye site üyesi olarak dahil edilir.

Sonuçta elde edilen izinler şunları sağlar:

- Siteyi yönetmek ve site içeriği üzerinde tam denetime sahip olmak için ekip sahipleri.
- Sitede dosya oluşturmak ve düzenlemek için ekip üyeleri. 

Varsayılan olarak, ekip sahipleri ve üyeleri, siteyi ekip dışından kişilerle, ekise eklemeden paylaşabilir. Kullanıcı yönetimini karmaşık hale getirmesi ve ekip üyesi olmayan kişilerin ekip sahipleri bunu fark etmeden ekip dosyalarına erişmesine neden olabileceği için buna karşı öneririz. Temel koruma düzeyinden başlayarak, bunu önlemeye yardımcı olmak için yalnızca sahiplerin siteyi doğrudan paylaşmasına izin vermenizi öneririz.

Ekiplerin salt okunur izin seçeneği olmasa da, SharePoint site bunu yapar. Ekip dosyalarını görüntülemesi gereken ancak düzenleyemeyen iş ortağı gruplarının paydaşlarınız varsa, bunları okuma izinleriyle doğrudan SharePoint sitesine eklemeyi göz önünde bulundurun.

## <a name="sharing-files-and-folders"></a>Dosya ve klasörleri paylaşma

Varsayılan olarak, hem sahipler hem de ekibin üyeleri, dosya ve klasörleri ekip dışındaki kişilerle paylaşabilir. Konuk paylaşımına izin verdiyseniz bu, kuruluşunuzun dışındaki kişileri içerebilir. Her üç katmanda da, yanlışlıkla fazla paylaşımı önlemeye yardımcı olmak için varsayılan paylaşım bağlantı türünü güncelleştiriyoruz. Son derece hassas katmanda bu tür paylaşımları yalnızca ekip sahiplerine kısıtlarız.

## <a name="sharing-with-people-outside-your-organization"></a>Kuruluşunuzun dışındaki kişilerle paylaşma

kuruluşunuzun dışındaki kişilerle Teams içerik paylaşmanız gerekiyorsa iki seçenek vardır:

- **Konuk paylaşımı** - Konuk paylaşımı, kullanıcıların kuruluşunuzun dışındaki kişilerle dosya, klasör, site, grup ve ekip paylaşmasına olanak tanıyan Azure AD B2B işbirliğini kullanır. Bu kişiler, dizininizdeki konuk hesaplarını kullanarak paylaşılan kaynaklara erişer.
- **Paylaşılan kanallar** - Paylaşılan kanallar, kullanıcıların kuruluşunuzdaki kaynakları diğer Azure AD kuruluşlardaki kişilerle paylaşmasına olanak tanıyan Azure AD B2B doğrudan bağlantı kullanır. Bu kişiler, kendi iş veya okul hesabını kullanarak Teams paylaşılan kanallara erişmektedir. Kuruluşunuzda hiçbir konuk hesabı oluşturulmaz.

Duruma bağlı olarak hem konuk paylaşımı hem de paylaşılan kanallar yararlıdır. Her bir senaryoyla ilgili ayrıntılar ve belirli bir senaryo için hangisinin kullanılacağına karar vermek için bkz. [Dış işbirliği planlama](plan-external-collaboration.md) .

Konuk paylaşımını kullanmayı planlıyorsanız, en iyi paylaşım ve yönetim deneyimi için [Azure AD B2B ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview) yapılandırmanızı öneririz.

Teams konuk paylaşımı varsayılan olarak açıktır, ancak bir duyarlılık etiketi kullanarak hassas ve son derece hassas katmanlarda gerekirse kapatabilirsiniz. Paylaşılan kanallar varsayılan olarak açıktır, ancak işbirliği yapmak istediğiniz her kuruluş için kuruluşlar arası ilişkilerin ayarlanmasını gerektirir. Ayrıntılar için bkz. [Kanaldaki dış katılımcılarla işbirliği yapma](collaborate-teams-direct-connect.md) .

Son derece hassas katmanda duyarlılık etiketini uygulandığı dosyaları şifrelemek için yapılandırıyoruz. Konukların bu dosyalara erişmesi gerekiyorsa, etiketi oluştururken onlara izin vermeniz gerekir. Paylaşılan kanallardaki dış katılımcılara duyarlılık etiketleri için izin verilemiyor ve duyarlılık etiketiyle şifrelenen içeriğe erişilemiyor.

Kuruluşunuzun dışındaki kişilerle işbirliği yapmanız gerekiyorsa temel katman ve hassas veya yüksek düzeyde hassas katmanlar için konuk paylaşımını açık bırakmanızı kesinlikle öneririz. Microsoft 365'daki konuk paylaşım özellikleri, dosyaları e-posta iletilerinde ek olarak göndermekten çok daha güvenli ve yönetilebilir bir paylaşım deneyimi sağlar. Ayrıca kullanıcıların yasal dış ortak çalışanlarla paylaşmak için devredilmiş tüketici ürünlerini kullandığı gölge BT riskini azaltır.

Azure AD kullanan diğer kuruluşlarla düzenli olarak işbirliği yaparsanız, paylaşılan kanallar iyi bir seçenek olabilir. Paylaşılan kanallar, diğer kuruluşun Teams istemcisinde sorunsuz bir şekilde görünür ve dış katılımcıların bir konuk hesabı kullanarak ayrı olarak oturum açmak yerine kendi kuruluşlarında normal kullanıcı hesabını kullanmalarına izin verir.

Kuruluşunuz için güvenli ve üretken bir konuk paylaşım ortamı oluşturmak için aşağıdaki başvurulara bakın:

- [Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmaya yönelik en iyi yöntemler](best-practices-anonymous-sharing.md)
- [Kuruluşunuzun dışındaki kişilerle paylaşım yaparken dosyaların yanlışlıkla açığa çıkmalarını sınırlayın](share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Yönetilmeyen cihazlardan erişim

Hassas ve yüksek oranda hassas katmanlar için, duyarlılık etiketleriyle SharePoint içeriğe erişimi kısıtlarız. Azure AD koşullu erişim, konum, risk, cihaz uyumluluğu ve diğer faktörlere bağlı sınırlamalar da dahil olmak üzere kişilerin Microsoft 365 nasıl erişebileceğine ilişkin birçok seçenek sunar. [Koşullu Erişim nedir?](/azure/active-directory/conditional-access/overview) konusunu okumanızı ve kuruluşunuz için hangi ek ilkelerin uygun olabileceğini göz önünde bulundurmanızı öneririz.

Konukların genellikle kuruluşunuz tarafından yönetilen cihazları olmadığını unutmayın. Katmanlardan herhangi birinde konuklara izin verirseniz, ekiplere ve sitelere erişmek ve yönetilmeyen cihaz ilkelerinizi buna göre ayarlamak için ne tür cihazlar kullanabileceklerini göz önünde bulundurun.

### <a name="control-device-access-across-microsoft-365"></a>Microsoft 365 genelinde cihaz erişimini denetleme

Duyarlılık etiketlerindeki yönetilmeyen cihazlar ayarı yalnızca SharePoint erişimi etkiler. Yönetilmeyen cihazların denetimini SharePoint ötesinde genişletmek istiyorsanız, [bunun yerine kuruluşunuzdaki tüm uygulamalar ve hizmetler için Azure Active Directory koşullu erişim ilkesi oluşturabilirsiniz](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). Bu ilkeyi [özellikle Microsoft 365 hizmetleri](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365) için yapılandırmak için **Bulut uygulamaları veya eylemleri** altındaki **Office 365** bulut uygulamasını seçin.

![Azure Active Directory koşullu erişim ilkesindeki Office 365 bulut uygulamasının ekran görüntüsü.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Tüm Microsoft 365 hizmetlerini etkileyen bir ilke kullanmak, kullanıcılarınız için daha iyi güvenlik ve daha iyi bir deneyime yol açabilir. Örneğin, yönetilmeyen cihazlara erişimi yalnızca SharePoint'de engellediğinizde, kullanıcılar yönetilmeyen bir cihazla ekipteki sohbete erişebilir, ancak **Dosyalar** sekmesine erişmeye çalıştıklarında erişimi kaybederler. Office 365 bulut uygulamasını kullanmak [hizmet bağımlılıklarıyla](/azure/active-directory/conditional-access/service-dependencies) ilgili sorunları önlemeye yardımcı olur.

## <a name="next-step"></a>Sonraki adım

[Başlangıç olarak temel koruma düzeyini yapılandırın](configure-teams-baseline-protection.md). Gerekirse, temelin üzerine [hassas koruma](configure-teams-sensitive-protection.md) ve [yüksek oranda hassas koruma](configure-teams-highly-sensitive-protection.md) ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft Teams'da güvenlik ve uyumluluk](/microsoftteams/security-compliance-overview)

[Uyarı ilkeleri](../compliance/alert-policies.md)
