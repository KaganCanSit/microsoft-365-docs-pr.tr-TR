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
ms.openlocfilehash: 2d7c370ab34eea2c708769674495a2c51f1a3fcf
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782049"
---
# <a name="design-a-data-loss-prevention-policy"></a>Veri kaybı önleme ilkesi tasarlama

İlkeyi uygulamadan önce tasarlamaya zaman ayırarak istediğiniz sonuçlara daha hızlı ve daha az istenmeyen sorunla ulaşabilirsiniz. Bu, ilkeyi oluşturmaktan ve ardından yalnızca deneme ve hataya göre ayarlamaya kıyasla daha azdır. İlke tasarımlarınızın belgelenmesi iletişimlerde, ilke incelemelerinde, sorun gidermede ve daha fazla ayarlamada da size yardımcı olur.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

Microsoft 365 DLP kullanmaya yeni başladıysanız, ilke tasarlamaya başlamadan önce şu makalelere göz atabilirsiniz:

- [Veri kaybı önleme hakkında bilgi edinin](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) - bu makalede veri kaybı önleme uzmanlık alanı ve Microsoft'un DLP uygulaması tanıtılarak
- [Veri kaybı önlemeyi (DLP) planlama](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) - bu makale üzerinde çalışarak şunları yapacaksınız:
  - [Paydaşları belirleme](dlp-overview-plan-for-dlp.md#identify-stakeholders)
  - [Korunacak hassas bilgi kategorilerini açıklama](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
  - [Hedefleri ve stratejiyi belirleme](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Veri Kaybı Önleme ilkesi başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference) - bu makalede DLP ilkesinin tüm bileşenleri ve her birinin ilkenin davranışını nasıl etkilediği tanıtılmıştır

## <a name="policy-design-overview"></a>İlke tasarımına genel bakış

[İlke tasarlamak](#policy-design-process) çoğunlukla [iş gereksinimlerinizi net bir şekilde tanımlamak, bunları bir ilke amacı bildiriminde belgeleyip](#define-intent-for-the-policy) [bu gereksinimleri ilke yapılandırmasına eşlemektir](#map-business-needs-to-policy-configuration). İlke tasarımı kararlarınızdan bazılarını bilgilendirmek için planlama aşamanızda alınan kararları kullanacaksınız.

### <a name="define-intent-for-the-policy"></a>İlkenin amacını tanımlama

Tek bir deyimde sahip olduğunuz her ilkenin iş amacını özetleyebilmelidir. Bu deyimin geliştirilmesi, kuruluşunuzdaki konuşmaları yönlendirecek ve tamamen ayrıntılı bir şekilde açıklandığında, bu bildirim ilkeyi doğrudan bir iş amacına bağlar ve ilke tasarımı için bir yol haritası sağlar. [Veri kaybı önlemeyi planlama (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) makalesindeki adımlar, ilke amacı bildiriminizi kullanmaya başlamanıza yardımcı olur.

[DLP ilkesi yapılandırmasına genel bakış](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) bölümünden tüm DLP ilkelerinin şunları yapmanız gerektiğini unutmayın:

- İzlemek istediğiniz şeyi seçin
- İzlemek istediğiniz yeri seçin
- Bir ilkenin bir öğeye uygulanması için eşleşmesi gereken koşulları seçme
- İlke koşulları karşılandığında gerçekleştirecek eylemi seçin

Örneğin, dört sorunun da yanıtlarını sağlayan bir amaç bildiriminin kurgusal ilk taslağı aşağıda verilmiştir:

*"ABD merkezli bir kuruluşuz ve HIPPA tarafından kapsanan ve OneDrive/SharePoint depolanan hassas sağlık hizmetleri bilgilerini içeren Office belgeleri algılamamız ve Teams sohbet ve kanal iletilerinde paylaşılmakta olan bilgilere karşı koruma sağlamamız ve herkesin bunları yetkisiz üçüncü taraflarla paylaşmasını kısıtlamamız gerekiyor".*

İlke tasarımı geliştirirken büyük olasılıkla deyimini değiştirecek ve genişleteceksiniz.

### <a name="map-business-needs-to-policy-configuration"></a>İş gereksinimlerini ilke yapılandırmasıyla eşleme

Örnek taslak deyimini bölelim ve DLP ilkesi yapılandırma noktalarıyla eşleyelim.

|Deyim|Yapılandırma sorusu yanıtlandı ve yapılandırma eşlemesi|
|---|---|
|"ABD merkezli bir kuruluşuz ve HIPPA'nın kapsadığı hassas sağlık hizmetleri bilgilerini içeren Office belgeleri algılamamız gerekiyor...|- **İzlenecekler**: belgeleri Office, [ABD Sağlık Sigortası Yasası (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) şablonunu kullanın </br>- **Eşleşme koşulları**: (önceden yapılandırılmış ancak düzenlenebilir) - öğe ABD SSN ve Uyuşturucu Uygulama Dairesi (DEA) numarası, Uluslararası Hastalık Sınıflandırması (ICD-9-CM), Uluslararası Hastalık Sınıflandırması (ICD-10-CM) içerir, içerik kuruluşum dışındaki kişilerle paylaşılır  </br> - [güvenilirlik düzeyleri](sensitive-information-type-learn-about.md#more-on-confidence-levels) ve [örnek sayısı](dlp-policy-reference.md#content-contains) (sızıntıya dayanıklılık olarak adlandırılır) gibi algılama için tetikleme eşiğini netleştirmek için konuşmaları destekler.|
|... OneDrive/SharePoint depolanan ve sohbet ve kanal iletileri Teams paylaşılan bilgilere karşı koruma sağlar...|- **İzlenecek yer**: OneDrive ve SharePoint siteleri ve Teams sohbet/kanal hesaplarını veya dağıtım gruplarını ekleyerek veya hariç tutarak [konum kapsamını](dlp-policy-reference.md#locations) belirleme.|
|... ve herkesin bu öğeleri yetkisiz üçüncü taraflarla paylaşmalarını kısıtlayın."|- **Yapılması gereken eylemler**[:](dlp-policy-reference.md#actions) *Erişimi kısıtla veya içeriği Microsoft 365 konumlarda şifrele* </br> - Paylaşım kısıtlamaları gibi koruyucu eylemler, bildirimler ve uyarılar gibi farkındalık eylemleri ve bir engelleme eyleminin kullanıcı geçersiz kılınmasına izin verme gibi kullanıcı güçlendirme eylemleri de dahil olmak üzere bir ilke tetiklendiğinde hangi eylemlerin gerçekleştirilmesi konusunda konuşmayı teşvik eder|

Bu örnek bir DLP ilkesinin tüm yapılandırma noktalarını kapsamaz, genişletilmesi gerekir. Ancak kendi DLP ilke amaç ifadelerinizi geliştirirken doğru yönde düşünmenizi sağlamalıdır.

> [!IMPORTANT]
> Seçtiğiniz konumların hassas bilgi türlerini, duyarlılık etiketlerini ve bekletme etiketlerini ve kullanılabilir eylemleri kullanıp kullanamayacağınızı etkileyip etkilemediğini unutmayın. Bkz. [Veri Kaybı Önleme ilkesi başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>İlke Tasarım süreci

1. [Veri kaybı önlemeyi planlama (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) başlığı altında yer alan adımları tamamlayın. Bu makalede şunları yapacaksınız:
   1. [Paydaşlarınızı belirleme](dlp-overview-plan-for-dlp.md#identify-stakeholders)
   1. [Korunacak hassas bilgi kategorilerini açıklama](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
   1. [Hedefleri ve stratejiyi belirleme](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
   1. [İlke dağıtım planınızı tanımlama](dlp-overview-plan-for-dlp.md#policy-deployment)

2. DLP ilkesinin tüm bileşenlerini ve her birinin bir ilkenin davranışını nasıl etkilediğini anlamak için [Veri Kaybı Önleme ilke başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference) hakkında bilgi edinin.

3. [DLP ilke şablonlarının neler içerdiğini](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include) öğrenin.

4. Temel paydaşlarınızla ilke amacı bildiriminizi geliştirin. Bu makalenin önceki bölümlerindeki örne bakın.

5. Bu ilkenin genel DLP ilke stratejinize nasıl uyduğunu belirleyin.

   > [!IMPORTANT]
   > İlkeler oluşturulduktan sonra yeniden adlandırılamaz. İlkeyi yeniden adlandırmanız gerekiyorsa, istenen ada sahip yeni bir ilke oluşturmanız ve eskisini devre dışı bırakmanız gerekir. Bu nedenle, tüm ilkelerinizin şimdi kullanacağı adlandırma yapısına karar verin.

6. İlke amaç bildiriminizdeki öğeleri yapılandırma seçenekleriyle eşleyin.

7. Hangi ilke şablonundan başlayacağınıza karar verin, önceden tanımlı veya özel.

8. İlkeyi oluşturmadan önce şablonu gözden geçirip gerekli tüm bilgileri bir araya getirebilirsiniz. İlke amaç bildiriminizde yer almayan bazı yapılandırma noktaları olduğunu fark edebilirsiniz. Tamam. Eksik yapılandırma noktalarının gereksinimlerini çözmek için paydaşlarınıza Geri dön.

9. Tüm ilke ayarlarının yapılandırmasını belgeleyin ve paydaşlarınızla birlikte gözden geçirin. İlke amacı deyiminizi yapılandırma noktalarına eşlemeyi yeniden kullanabilirsiniz. Bu durum artık tamamen ayrıntılı bir şekilde açıklanmış durumdadır.

10. [Bir](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) taslak ilke oluşturun ve [ilke dağıtım](dlp-overview-plan-for-dlp.md#policy-deployment) planınıza geri dönün.

<!--## Policy design examples

|Customer business needs description|approach|
|---|---|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft|- Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.|- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users|
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices|- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage|

1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally

– For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**

  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
– (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

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

|Statement|Configuration question answered and configuration mapping|
|---|---|
|We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
|...and prevent it from egressing outside of our company’s borders...|- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...|- **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
|...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....|- **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages...|- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups.|
|...and restrict everyone from sharing those items with unauthorized third parties."|- **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action|

-->

## <a name="see-also"></a>Ayrıca Bkz

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Veri kaybı önlemeyi planlama (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Veri Kaybı Önleme ilkesi başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Veri Kaybı Önleme ilkesi ipuçları referansı](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)