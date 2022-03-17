---
title: Veri kaybı önleme ilkesi tasarlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Veri kaybı önleme (DLP) ilkesi tasarlamayı öğrenin
ms.openlocfilehash: 14e9fbb5efd20ddcf3d0a47da41a0cce89c88cee
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526326"
---
# <a name="design-a-data-loss-prevention-policy"></a>Veri kaybı önleme ilkesi tasarlama

Bir ilkeyi uygulamaya başlamadan önce tasarlamaya zaman yaratmak, istenen sonuçlara daha hızlı şekilde ulaşabilirsiniz. Bu, ilkeyi oluşturma ve ardından tek başına deneme ve hatayla ayarlamalar yapmaktan daha az sayıda ve daha az istenmeden oluşur. İlke tasarımlarınızı belgelenmiş olarak ayarlamak iletişim, ilke incelemeleri, sorun giderme ve daha fazla ayarlamada da size yardımcı olur.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

DLP'de Microsoft 365 çalışıyorsanız, ilke tasarlamaya başlamadan önce şu makalelerde çalışma yararlı olur:

- [Veri kaybını önleme hakkında bilgi edinmek](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) - Bu makalede, veri kaybı önleme disiplini ve Microsoft'un DLP'yi uygulama hakkında bilgi sağlar
- [Veri kaybını önleme (DLP) planını](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) kullanın; bu makale üzerinde çalışarak şunları will:
    - [Paydaşları tanımlama](dlp-overview-plan-for-dlp.md#identify-stakeholders)
    - [Korunması için hassas bilgi kategorilerini açıkla](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
    - [Hedef ve strateji ayarlama](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Veri Kaybı Önleme ilke başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference) - Bu makalede, bir DLP ilkesi tüm bileşenleri ve bunların her birinin bir ilkenin davranışını nasıl etkilemektedir

## <a name="policy-design-overview"></a>İlke tasarımına genel bakış

[İlke tasarlama,](#policy-design-process) büyük ölçüde iş ihtiyaçlarınızı net bir şekilde tanımlama [,](#define-intent-for-the-policy) bunları bir ilke amacı bildiriminde belgelama ve sonra da bu ihtiyaçları ilke [yapılandırmasına eşlemeyle ilgilidir](#map-business-needs-to-policy-configuration). İlke tasarımı kararlarınızı bazılarına bilgi vermek için planlama aşamasında kararlarınızı kullanırsiniz. 

### <a name="define-intent-for-the-policy"></a>İlkenin amacını tanımlama 

Tek bir deyimde var olan her ilkenin iş amacını özetlemeniz gerekir. Bu bildirimin geliştirilmesi, kurum içinde konuşmaları geliştirecek ve tam olarak dikkati çekiyorsa, bu ifade ilkeyi doğrudan iş amacına bağlar ve ilke tasarımına yönelik bir yol haritası sağlar. Veri kaybını [önlemeyi planlama (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) makalesinde yer alan adımlar, ilke amacı bildiriminize başlamanıza yardımcı olur.  

[DLP ilkesi yapılandırmasına genel bakış için tüm](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) DLP ilkelerinin şunları gerekli olduğunu unutmayın:

- İzlemek istediğiniz şeyi seçme
- İzlemek istediğiniz yeri seçin
- İlkenin bir öğeye uygulanması için eşleşmesi gereken koşulları seçme
- İlke koşullarına uygun olduğunda eylemi seçme 

Örneğin, burada, dört soruya yanıt veren bir amaç deyiminin kurgusal ilk taslağı ve bir örneği bulunmaktadır: 

*"BIZ ABD'de tabanlı bir kuruluşuz ve HIPPA'nın kapsamış olduğu hassas sağlık hizmetleri bilgilerini OneDrive/SharePoint'de depolanan hassas sağlık bilgileri içeren Office belgelerini algılamamız ve Teams sohbeti ve kanal iletisinde paylaşılan bu bilgilere karşı korumamız ve herkesin bunları yetkisiz üçüncü taraflarla paylaşmasını kısıtlamamız gerekir."* 

Bir ilke tasarımı geliştirirken, büyük olasılıkla bildirimi değiştirir ve genişletersiniz.

### <a name="map-business-needs-to-policy-configuration"></a>İşle ilgili ihtiyaçları ilke yapılandırmasına eşleme

Şimdi örnek taslak deyimini alta bırakarak DLP ilkesi yapılandırma noktalarıyla eşlenin.

|Deyim  |Yanıtlandı yapılandırma sorusu ve yapılandırma eşlemesi  |
|---------|---------|
| "Biz ABD'de tabanlı bir kuruluşuz ve HIPPA tarafından kapsa Office sağlık hizmetleri bilgilerini içeren farklı belgeler algılamamız gerekiyor...  |- **Neleri izleyebilirsiniz**: Office, ABD Sağlık [Sigortası Yasası (HIPAA) şablonunu](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) kullanın </br>- **Eşleşme** için koşullar: (önceden yapılandırılmış ancak düzenlenebilir) - öğe; ABD SSN ve Muntaz Yaptırım Daire (DEA) numarası, Uluslararası Daire Sınıflandırması (ICD-9-CM), Uluslararası Hastalık Sınıflandırması (ICD-10-CM), içeriği kuruluşum dışındaki kişilerle paylaşılır  </br> - konuşmaları, güven düzeyi ve örnek sayısı (sızıntı sızıntıları olarak [](sensitive-information-type-learn-about.md#more-on-confidence-levels)adlandırılan) algılama için [tetikleyen](dlp-policy-reference.md#content-contains) eşiği netleştirmeye devam eder.|
|... ve bu bilgilerin sohbet OneDrive kanal SharePoint Teams paylaşılmalarına karşı korumak... |- **Izlanacak yer**: [Sohbet](dlp-policy-reference.md#locations)/kanal hesapları veya dağıtım grupları dahil OneDrive SharePoint ve sohbet/kanal Teams dahil ederek veya dışlayarak konumcoping. |
|... ve herkesin bu öğeleri yetkisiz üçüncü taraflarla paylaşmasını kısıtla."  | - **Alacak işlemler**: [Belirli](dlp-policy-reference.md#actions) *konumlarda erişimi kısıtla veya içeriği Microsoft 365 gerekir* </br> - Paylaşım kısıtlamaları, bildirimler ve uyarılar gibi farkındalık eylemleri ve kullanıcının engelleme eylemlerini geçersiz kılmaya izin verme gibi kullanıcı gücü eylemleri gibi koruyucu işlemler de dahil olmak üzere bir ilke tetiklendiğinde hangi eylemlerin gerçekleştirilmesi konusunda konuşmalar devam ediyor |

Bu örnek, bir DLP ilkesine bağlı yapılandırma noktalarının hepsini kapsıyorsa, genişletilebilir olması gerekir. Ancak, kendi DLP ilkesi amacı ifadelerinizi geliştirirken doğru yönü düşünmenizi sağlar.

> [!IMPORTANT]
> Hassas bilgi türlerini, duyarlılık etiketlerini ve bekletme etiketlerini ve kullanılabilir eylemleri kullanıp kullanamayyabilirsiniz; seçenkler üzerindeki etkiyi unutmayın. Bkz. [Veri Kaybı Önleme ilke başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>İlke Tasarım Süreci

1. Aşağıdaki adımları tamamlayın:
    1. [Veri kaybını önleme (DLP) planını](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) kullanın; bu makale üzerinde çalışarak şunları will:
        1. [Paydaşlarınızı tanımlama](dlp-overview-plan-for-dlp.md#identify-stakeholders)
        1. [Korunması için hassas bilgi kategorilerini açıkla](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
        1. [Hedef ve strateji ayarlama](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
        1. [İlke dağıtım planınızı tanımlama](dlp-overview-plan-for-dlp.md#policy-deployment)

1. DLP [ilkesinin tüm bileşenlerini](dlp-policy-reference.md#data-loss-prevention-policy-reference) ve her birinin bir ilkenin davranışını nasıl etkileyeni anlıyoruz, böylece Veri Kaybı Önleme ilke başvurusuna aşinalık sahibi olursunuz.

1. [DLP ilke şablonlarının neleri dahil olduğunu kendinizi ifade edin](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

1. İlke amacı bildiriminizi önemli paydaşlarla birlikte geliştirin. Bu makalenin önceki örneğine bakın.

1. Bu ilkenin genel DLP ilkesi stratejinize nasıl uyduğunu belirler.

> [!IMPORTANT]
> İlkeler oluşturulduktan sonra yeniden adlandırılamaz. Bir ilkeyi yeniden adlandırmak zorundaysanız, istediğiniz adla yeni bir ilke oluşturmalı ve eski ilkeyi devre dışı 12'den kaldırabilirsiniz. Bu nedenle, tüm ilkelerinizin şu anda kullanabileceği adlandırma yapısına karar verin. 

6. İlke amacı bildiriminizdeki öğeleri yapılandırma seçenekleriyle eşler.

7. Önceden tanımlanmış veya özel olarak hangi ilke şablonundan başlayacağınızı seçin.

8. Şablonun üzerinden geçerek, ilkeyi oluşturmadan önce gereken tüm bilgileri birleştirin. İlke amacı bildiriminizin kapsamında olmayan bazı yapılandırma noktaları olduğunu büyük olasılıkla fark edersiniz. Tamam. Eksik yapılandırma noktalarının gereksinimlerini karşılamak için proje katılımcılarımıza geri gidin. 

9. Tüm ilke ayarlarının yapılandırmasını belgelenin ve bunları proje katılımcılarınızı gözden geçirin. İlke amacı deyimi eşlemenizi, artık tümüyle işlerine hazır olan yapılandırma noktalarıyla yeniden kullanabilirsiniz.

10. [Taslak ilke](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) oluşturun ve ilke dağıtım [planınıza geri](dlp-overview-plan-for-dlp.md#policy-deployment) bakın.

<!--## Policy design examples

|Customer business needs description  | approach  |
|---------|---------|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft| - Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.     |- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users       |
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices     |- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage      |


1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally



–   For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**


  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
–   (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

<!--


> [!TIP] The more locations you include ensures broader application of the policy and more consistent coverage. If you include locations that are mostly used for internal collaboration, the responsiveness of collaboration may be impacted.


- whether the protective actions you need are supported throught the associated location or if you need to compromise to extend coverage
    - also usefule for identifying the most restrictive actions available 
    - (we shouldn't mention here that the "content contains" condition is the primary staple for a DLP policy and should be utilized as a starting point for policy creation. The other workload-specific conditions can be ustilized as an extended or granular control of company's DLP policy. Useful for when "too much" data is being restricted and known sensitive data typically falls under certain conditions.)
    - (We can mention here that their quantitative goal such as "protect X% of data across all locations while maintaining x productivity" can be monitored throught alerts or reports. If protection is too high of working against their established goals, they can come back to policy and tweak their conditions/actions)
- Finally, you should have a union of what, hwo and when to be covered which will easily map to generating a live policy via Microsoft DLP. 
- 
5. At this stage you should asses how you should start this policy. ***LINK OUT TO DEPLOYING A POLICY COVERED IN THE PLANNING TOPIC TOO***
    - Test: your company is very large, conservative or the actions established are pretty restrictive
    - Test w/ notifications: same as above, but you get to test out investigation cadence or volume
    - Live: immediately start this policy in your environment. Useful for when data protection is needed immediately, such as a reactive policy creation, or if you're confident in your planning, or if the risk is low (liek audit actions, etc.)
    - keep it off:
-->

<!--## Policy Design Examples

Here are some examples of more detailed policy intent statement to configuration mappings.

*We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information and prevent it from egressing outside of our company’s borders. We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices. We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item. We have a Microsoft 365 E5 subscription and want to protect all locations and first party apps that are available to us because we can’t afford to have any data leaks. If an event occurs or is prevented, we want to alert our compliance admin and educate our end-users where necessary.*

|Statement  |Configuration question answered and configuration mapping  |
|---------|---------|
| We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
| ...and prevent it from egressing outside of our company’s borders... |- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...| - **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
| ...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....| - **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages... |- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups. |
|...and restrict everyone from sharing those items with unauthorized third parties."  | - **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action |

-->


## <a name="see-also"></a>Ayrıca Bkz

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Veri kaybı önleme (DLP) planı](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Veri Kaybı Önleme ilke başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Veri Kaybı Önleme ilke ipuçları başvurusu](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)