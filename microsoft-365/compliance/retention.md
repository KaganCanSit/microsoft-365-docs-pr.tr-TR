---
title: İçeriği otomatik olarak saklamak veya silmek için bekletme ilkeleri & etiketleri hakkında bilgi edinin
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: İhtiyaç duyduklarınızı korumanıza ve saklamadığınız şeyleri silmenize yardımcı olan bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin.
ms.openlocfilehash: c8ac850c77c97cbcc313108ffc74e05aa1735fde
ms.sourcegitcommit: 4cd8be7c22d29100478dce225dce3bcdce52644d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65302234"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*


[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Teams bekletme ilkeleriyle ilgili iletiler görüyorsanız veya uygulamalarınızdaki bekletme etiketleri hakkında sorularınız varsa, bunların sizin için nasıl yapılandırıldığı hakkında bilgi için BT departmanınıza başvurun. Bu arada, aşağıdaki makaleleri yararlı bulabilirsiniz:
>
> - [Bekletme ilkeleriyle ilgili iletileri Teams](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)
> - [SharePoint veya OneDrive dosyalarına bekletme etiketleri uygulama](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df)
>
> Bu sayfadaki bilgiler, uyumluluk nedeniyle bekletme ilkeleri ve bekletme etiketleri oluşturabilen BT yöneticilerine yöneliktir.

Çoğu kuruluşta, verilerinin hacmi ve karmaşıklığı her gün artmaktadır: e-posta, belgeler, anlık iletiler ve daha fazlası. Bu bilgilerin etkili bir şekilde yönetilmesi veya yönetilmesi önemlidir çünkü şunlar gerekir:

- İçeriği en az bir süre saklamanızı gerektiren **sektör düzenlemelerine ve iç politikalara proaktif olarak uyun**; örneğin, Sarbanes-Oxley Yasası belirli içerik türlerini yedi yıl boyunca saklamanızı gerektirebilir.

- Artık saklamanız gerekmeyen eski içeriği kalıcı olarak silerek **dava açma veya güvenlik ihlali durumunda riskinizi azaltın**.

- Kullanıcılarınızın yalnızca güncel ve ilgili içeriklerle çalıştığından emin olarak **kuruluşunuzun bilgileri etkili bir şekilde paylaşmasına ve daha çevik çalışmasına yardımcı olun**.

Yapılandırdığınız bekletme ayarları bu hedeflere ulaşmanıza yardımcı olabilir. İçeriği yönetmek için genellikle iki eylem gerekir:

| Eylem| Amaç |
|:-----|:-----|
|İçeriği saklama | Kalıcı silmeyi önleme ve eBulma için kullanılabilir durumda kalma |
|İçerik silme | Kuruluşunuzdan içeriği kalıcı olarak silme|

Bu iki bekletme eylemiyle, aşağıdaki sonuçlar için bekletme ayarlarını yapılandırabilirsiniz:

- Yalnızca saklama: İçeriği sonsuza kadar veya belirli bir süre boyunca tutun.
- Yalnızca silme: Belirli bir süre sonra içeriği kalıcı olarak silin.
- Saklama ve silme: İçeriği belirli bir süre boyunca tutun ve kalıcı olarak silin.

Bu bekletme ayarları, uyumluluk nedeniyle içeriği saklamanız gerektiğinde ek depolama alanı oluşturma ve yapılandırma ek yüklerinden tasarruf etmenizi sağlayan içerikle çalışır. Ayrıca, bu verileri kopyalamak ve eşitlemek için özelleştirilmiş işlemler uygulamanız gerekmez.

Bekletme ilkelerinin ve bekletme etiketlerinin nasıl çalıştığı, bunların ne zaman kullanılacağı ve bunların birbirini nasıl tamamladıkları hakkında daha fazla bilgi edinmek için aşağıdaki bölümleri kullanın. Ancak bazı yaygın senaryolar için saklama ayarlarını kullanmaya başlamaya ve dağıtmaya hazırsanız bkz. [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md).

## <a name="how-retention-settings-work-with-content-in-place"></a>Bekletme ayarları içerikle nasıl çalışır?

İçerikte bekletme ayarları atandığında, bu içerik özgün konumunda kalır. Çoğu zaman, insanlar hiçbir şey değişmemiş gibi belgeleriyle veya postalarıyla çalışmaya devam eder. Ancak bekletme ilkesine dahil edilen içeriği düzenler veya silerlerse içeriğin bir kopyası otomatik olarak korunur.

- SharePoint ve OneDrive siteleri için: Kopya **, Koruma Bekletme** kitaplığında tutulur.

- Exchange posta kutuları için: Kopya **Kurtarılabilir Öğeler** klasöründe tutulur.

- Teams ve Yammer iletileri için: Kopya, **Kurtarılabilir Öğeler** klasöründe alt Exchange klasör olarak **SubstrateHolds** adlı gizli bir klasörde tutulur.

> [!NOTE]
> Koruma Bekletme kitaplığı sitenin depolama kotasına eklendiğinden, SharePoint ve Microsoft 365 grupları için saklama ayarlarını kullandığınızda depolama alanınızı artırmanız gerekebilir.
>
Bu güvenli konumlar ve korunan içerik çoğu kişi tarafından görülmeyebilir. Çoğu durumda, kişilerin içeriklerinin saklama ayarlarına tabi olduğunu bilmesi bile gerekmez.

Bekletme ayarlarının farklı iş yükleri için nasıl çalıştığı hakkında daha ayrıntılı bilgi için aşağıdaki makalelere bakın:

- [SharePoint ve OneDrive için bekletme hakkında bilgi edinin](retention-policies-sharepoint.md)
- [Microsoft Teams için bekletme hakkında bilgi edinin](retention-policies-teams.md)
- [Yammer için bekletme hakkında bilgi edinin](retention-policies-yammer.md)
- [Exchange için bekletme hakkında bilgi edinin](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri

Saklama ayarlarınızı içeriğe atamak için, **bekletme ilkelerini** ve **etiket ilkeleriyle bekletme etiketlerini** kullanın. Bu yöntemlerden yalnızca birini kullanabilir veya birleştirebilirsiniz.

Site veya posta kutusu düzeyinde içerik için aynı bekletme ayarlarını atamak için bekletme ilkesi kullanın ve bir öğe düzeyinde (klasör, belge, e-posta) bekletme ayarları atamak için bir bekletme etiketi kullanın.

Örneğin, bir SharePoint sitesindeki tüm belgelerin 5 yıl boyunca saklanması gerekiyorsa, bunu bir bekletme ilkesiyle yapmak, sitedeki tüm belgelere aynı bekletme etiketini uygulamaktan daha verimlidir. Ancak, bu sitedeki bazı belgeler 5 yıl, diğerleri 10 yıl saklanmalıdır, bir saklama ilkesi bunu yapamaz. Öğe düzeyinde bekletme ayarlarını belirtmeniz gerektiğinde bekletme etiketlerini kullanın.

Bekletme ilkelerinden farklı olarak, bekletme etiketlerinin bekletme ayarları, Microsoft 365 kiracınızda farklı bir konuma taşınırsa içerikle birlikte taşınır. Ayrıca bekletme etiketleri, bekletme ilkelerinin desteklemediğini aşağıdaki özelliklere sahiptir:

- Saklama süresini, içeriğin yaşına veya en son değiştirildiği tarihe ek olarak içeriğin etiketlendiği veya bir olayı temel alarak başlatma seçenekleri.

- Etikete dönüştürülecek içeriği tanımlamak için [eğitilebilir sınıflandırıcıları](classifier-learn-about.md) kullanın.

- SharePoint öğeleri veya Exchange iletileri için varsayılan bir etiket uygulayın.

- Saklama süresi sonunda desteklenen eylemler:
    - [Değerlendirmeyi bırakma](./disposition.md)  kalıcı olarak silinmeden önce içeriği gözden geçirin.
    - Başka bir bekletme etiketini otomatik olarak uygulama

- İçeriği etiket ayarlarının bir parçası olarak [bir kayıt](records-management.md#records) olarak işaretleyin ve saklama süresinin sonunda içerik silindiğinde her zaman [kullanımdan kaldırılma kanıtına](disposition.md#disposition-of-records) sahip olun.

### <a name="retention-policies"></a>Bekletme ilkeleri

Bekletme ilkeleri aşağıdaki konumlara uygulanabilir:

- e-postayı Exchange
- siteyi SharePoint
- hesapları OneDrive
- Microsoft 365 Grupları
- Skype Kurumsal
- Ortak klasörleri Exchange
- kanal iletilerini Teams
- sohbetleri Teams
- Özel kanal iletilerini Teams
- Topluluk iletilerini Yammer
- Kullanıcı iletilerini Yammer

> [!NOTE]
> Teams kanal iletileri artık [paylaşılan kanalları](/MicrosoftTeams/shared-channels) (şu anda önizleme aşamasında) ve standart kanalları içerir.

Tek bir ilkeyi birden çok konuma veya belirli konumlara veya kullanıcılara çok verimli bir şekilde uygulayabilirsiniz.

Saklama süresinin başlangıcı için içeriğin ne zaman oluşturulduğunu veya yalnızca dosyalar ve SharePoint, OneDrive ve Microsoft 365 Grupları konumları için desteklendiğini ve içeriğin en son ne zaman değiştirildiğini seçebilirsiniz.

Öğeler bekletme ilkesinde belirtilen kapsayıcılarından bekletme ayarlarını devralır. İlke içeriği saklayacak şekilde yapılandırıldığında bu kapsayıcının dışına taşınırlarsa, söz konusu öğenin bir kopyası iş yükünün güvenli konumunda tutulur. Ancak bekletme ayarları içerikle birlikte yeni konumuyla birlikte hareket etmez. Bu gerekiyorsa bekletme ilkeleri yerine bekletme etiketlerini kullanın.

### <a name="retention-labels"></a>Bekletme etiketleri

Farklı bekletme ayarları gerektiren farklı içerik türleri için bekletme etiketlerini kullanın. Örneğin:

- En az bir süre saklanması gereken vergi formları.

- Belirli bir yaşa ulaştıklarında kalıcı olarak silinmesi gereken basın malzemeleri.

- Belirli bir süre boyunca saklanması ve kalıcı olarak silinmesi gereken rekabetçi araştırmalar.

- Düzenlenmeleri veya silinememeleri için kayıt olarak işaretlenmesi gereken iş vizeleri.

Tüm bu durumlarda bekletme etiketleri, idare denetimi için saklama ayarlarını öğe düzeyinde (belge veya e-posta) uygulamanıza olanak sağlar.

Bekletme etiketleriyle şunları yapabilirsiniz:

- Kuruluşunuzdaki kişilerin Outlook ve Web üzerinde Outlook, OneDrive, SharePoint ve Microsoft 365 gruplarındaki içeriğe **el ile bekletme etiketi uygulamasına olanak tanıyın**. Kullanıcılar genellikle ne tür içerikle çalıştıklarını en iyi bilirler, böylece içeriği sınıflandırabilir ve uygun saklama ayarlarının uygulanmasını sağlayabilirler.

- E-posta veya Teams paylaşılan bulut eklerini içeren belirli koşullarla eşleşiyorsa veya içerik şunları içeriyorsa içeriğe **bekletme etiketlerini otomatik olarak uygulayın**:
  - Belirli hassas bilgi türleri.
  - Oluşturduğunuz sorguyla eşleşen belirli anahtar sözcükler.
  - Eğitilebilir sınıflandırıcı için desen eşleşmeleri.

- SharePoint sitelerdeki ve OneDrive hesaplarındaki belgeler ve e-posta öğeleri için **içeriğin etiketlendiği saklama süresini başlatın**.

- Çalışanların kuruluştan ayrılması veya sözleşmelerin süresi dolması gibi **bir olayın gerçekleştiği saklama süresini başlatın**.

- SharePoint'da **ayarlanmış bir belge kitaplığına, klasöre veya belge kümesine varsayılan bir bekletme etiketi uygulayın**; böylece bu konumda depolanan tüm belgeler varsayılan bekletme etiketini devralır.

- Öğeleri kayıt [yönetimi](records-management.md) stratejinizin bir parçası olarak **kayıt olarak işaretleyin**. Etiketli bu içerik Microsoft 365 kaldığında, yasal nedenlerle gerekebilecek içeriğe başka kısıtlamalar da eklenir. Daha fazla bilgi için bkz. [İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

İçerik Microsoft 365 dışına taşınırsa[, duyarlılık etiketlerinin](sensitivity-labels.md) aksine bekletme etiketleri kalıcı olmaz.

#### <a name="classifying-content-without-applying-any-actions"></a>Herhangi bir eylem uygulamadan içeriği sınıflandırma

Bekletme etiketlerinin ana amacı içeriği saklamak veya silmek olsa da, bekletme etiketlerini bekletmeyi veya başka eylemleri açmadan da kullanabilirsiniz. Bu durumda, bekletme etiketini herhangi bir eylem uygulamadan yalnızca metin etiketi olarak kullanabilirsiniz.

Örneğin, hiçbir eylem olmadan "Daha sonra gözden geçir" adlı bir bekletme etiketi oluşturup uygulayabilir ve ardından bu etiketi kullanarak içeriği daha sonra bulabilirsiniz.

![Yalnızca sınıflandırmak için etiket ayarları.](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>DLP ilkesinde koşul olarak bekletme etiketi kullanma

SharePoint'deki belgeler için Microsoft Purview Veri Kaybı Önleme (DLP) ilkesinde koşul olarak bir bekletme etiketi belirtebilirsiniz. Örneğin, belgelere belirtilen bir bekletme etiketi uygulanmışsa, belgelerin kuruluş dışında paylaşılmasını önlemek için bir DLP ilkesi yapılandırın.

Daha fazla bilgi için bkz. [DLP ilkesinde koşul olarak bekletme etiketi kullanma](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Bunları uygulayan bekletme etiketleri ve ilkeleri

Bekletme etiketlerini yayımladığınızda, bunlar yöneticilerin ve kullanıcıların içeriğe başvurmasını sağlayan bir **bekletme etiketi ilkesine** eklenir. Aşağıdaki diyagramda gösterildiği gibi:

1. Tek bir bekletme etiketi birden çok bekletme etiketi ilkesine dahil edilebilir.

2. Bekletme etiketi ilkeleri, bekletme etiketlerini yayımlayacak konumları belirtir. Aynı konum birden çok bekletme etiketi ilkesine dahil edilebilir.

![Bekletme etiketlerinin konumları belirten etiket ilkelerine nasıl eklendiği.](../media/retention-labels-and-policies.png)

Ayrıca, her biri tek bir bekletme etiketine sahip bir veya daha fazla **otomatik uygulama bekletme etiketi ilkesi** oluşturabilirsiniz. Bu ilkeyle, ilkede belirttiğiniz koşullar karşılandığında otomatik olarak bir bekletme etiketi uygulanır.

#### <a name="retention-label-policies-and-locations"></a>Bekletme etiketi ilkeleri ve konumları

Bekletme etiketleri, bekletme etiketinin ne yaptığına bağlı olarak farklı konumlarda yayımlanabilir.

| Bekletme etiketi... | Ardından etiket ilkesi... |
|:-----|:-----|
|Yöneticilere ve son kullanıcılara yayımlandı  |Exchange, SharePoint, OneDrive, Microsoft 365 Grupları  |
|Hassas bilgi türlerine veya eğitilebilir sınıflandırıcılara göre otomatik olarak uygulanır  |Exchange, SharePoint, OneDrive  |
|Anahtar sözcüklere veya sorguya göre otomatik uygulama  |Exchange, SharePoint, OneDrive, Microsoft 365 Grupları  |
|Bulut eklerine otomatik olarak uygulama  |SharePoint, OneDrive, Microsoft 365 Grupları  |

Exchange ortak klasörler, Skype, Teams ve Yammer iletileri bekletme etiketlerini desteklemez. Bu konumlardaki içeriği korumak ve silmek için bunun yerine bekletme ilkelerini kullanın.

#### <a name="only-one-retention-label-at-a-time"></a>Aynı anda yalnızca bir bekletme etiketi

Bir e-posta veya belgenin aynı anda yalnızca tek bir bekletme etiketi uygulanabilir. Bekletme etiketi son kullanıcı veya yönetici tarafından [el ile](create-apply-retention-labels.md#manually-apply-retention-labels) veya aşağıdaki yöntemlerden herhangi biri kullanılarak otomatik olarak uygulanabilir:

- [Etiket ilkesini otomatik uygulama](apply-retention-labels-automatically.md)
- [SharePoint Syntex için belge anlama modeli](../contentunderstanding/apply-a-retention-label-to-a-model.md)
- [SharePoint veya Outlook için varsayılan etiket](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) [](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)
- [Outlook kuralları](create-apply-retention-labels.md#automatically-applying-a-retention-label-to-email-by-using-rules)

Standart saklama etiketleri için (öğeleri [kayıt veya mevzuat kaydı](records-management.md#records) olarak işaretlemez):

- Yöneticiler ve son kullanıcılar, içeriğe uygulanan mevcut bir bekletme etiketini el ile değiştirebilir veya kaldırabilir.

- İçerikte zaten bir bekletme etiketi uygulandığında, mevcut etiket otomatik olarak kaldırılmaz veya olası bir özel durumla başka bir bekletme etiketiyle değiştirilmez: Mevcut etiket varsayılan etiket olarak uygulandı. Varsayılan bir etiket kullandığınızda, başka bir varsayılan etiketle değiştirilebileceği veya otomatik olarak kaldırılabildiği bazı senaryolar vardır.

- İçerikte zaten bir bekletme etiketi uygulandığında, mevcut etiket otomatik olarak kaldırılmaz veya iki olası özel durumla başka bir bekletme etiketiyle değiştirilmez: 
    
    - Mevcut etiket, bekletme süresinin sonunda otomatik olarak farklı bir bekletme etiketi uygulayacak şekilde yapılandırılır.
    - Mevcut etiket varsayılan etiket olarak uygulandı. Varsayılan bir etiket kullandığınızda, başka bir varsayılan etiketle değiştirilebileceği veya otomatik olarak kaldırılabildiği bazı senaryolar vardır. 
        
        Varsayılan etiket kullanılarak uygulandığında etiket davranışı hakkında daha fazla bilgi için:
        - SharePoint için varsayılan etiket: [SharePoint için varsayılan etiket kullandığınızda etiket davranışı](create-apply-retention-labels.md#label-behavior-when-you-use-a-default-label-for-sharepoint)
        - Outlook için varsayılan etiket: [Outlook klasörüne varsayılan bekletme etiketi uygulama](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)

- Bekletme etiketi uygulayabilecek birden çok otomatik uygulama etiketi ilkesi varsa ve içerik birden çok ilkenin koşullarını karşılıyorsa, en eski otomatik uygulama etiket ilkesinin bekletme etiketi (oluşturulma tarihine göre) uygulanır.

Bekletme etiketleri öğeleri kayıt veya mevzuat kaydı olarak işaretlediğinde, bu etiketler yapılandırılmış saklama süreleri boyunca hiçbir zaman otomatik olarak değiştirilmez. Yalnızca kapsayıcının yöneticileri öğeleri kayıt olarak işaretleyen bekletme etiketlerini el ile değiştirebilir veya kaldırabilir, ancak mevzuat kayıtlarını değiştiremez. Daha fazla bilgi için bkz. [İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

#### <a name="monitoring-retention-labels"></a>Bekletme etiketlerini izleme

Microsoft Purview uyumluluk portalından **Veri sınıflandırması'nı** ve **Genel Bakış** sayfasını seçerek bekletme etiketlerinizin kiracınızda nasıl kullanıldığını izleyin ve etiketli öğelerinizin nerede bulunduğunu belirleyin. Önemli önkoşullar da dahil olmak üzere daha fazla bilgi için bkz. [Veri sınıflandırması hakkında bilgi edinin](data-classification-overview.md).

Ardından [içerik gezginini](data-classification-content-explorer.md) ve [etkinlik gezginini](data-classification-activity-explorer.md) kullanarak ayrıntılara gidebilirsiniz.

> [!TIP]
>Saklamanız veya silmeniz veya kayıt olarak yönetmeniz gerekebilecek içeriği belirlemenize yardımcı olmak için eğitilebilir sınıflandırıcılar ve hassas bilgi türleri gibi diğer veri sınıflandırma içgörülerinden bazılarını kullanmayı göz önünde bulundurun.

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Belirli bir bekletme etiketine sahip tüm içeriği bulmak için İçerik Arama'yı kullanma

Kullanıcılar tarafından veya otomatik olarak uygulanan bekletme etiketleri içeriğe uygulandıktan sonra, belirli bir bekletme etiketi uygulanmış olan tüm öğeleri bulmak için içerik aramasını kullanabilirsiniz.

İçerik araması oluşturduğunuzda **Bekletme etiketi** koşulunu seçin ve ardından tam bekletme etiketi adını veya etiket adının bir bölümünü girin ve joker karakter kullanın. Daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

![Bekletme etiketi koşulu.](../media/retention-label-condition.png)

## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri için özellikleri karşılaştırma

Özelliklere göre bekletme ilkesi mi yoksa bekletme etiketi mi kullanacağınızı belirlemenize yardımcı olması için aşağıdaki tabloyu kullanın.

|Yeteneği|Bekletme ilkesi |Bekletme etiketi|
|:-----|:-----|:-----|:-----|
|Saklama ayarlarını koruyup silebilen, yalnızca tutabilen veya yalnızca silebilen bekletme ayarları |Evet |Evet |
|Desteklenen iş yükleri: <br />- Exchange <br />- SharePoint <br />- OneDrive <br />- Microsoft 365 grupları <br />- Skype Kurumsal <br />- Teams<br />- Yammer|<br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet | <br /> Evet, ortak klasörler dışında <br /> Evet <br /> Evet <br /> Evet <br /> Hayır <br /> Hayır <br /> Hayır |
|Bekletme otomatik olarak uygulanır | Evet | Evet |
|Saklama süresinin sonunda farklı bekletme ayarlarını otomatik olarak uygulama | Hayır | Evet |
|Koşullara göre uygulanan bekletme <br /> - hassas bilgi türleri, KQL sorgular ve anahtar sözcükler, eğitilebilir sınıflandırıcılar, bulut ekleri| Hayır | Evet |
|Bekletme el ile uygulandı | Hayır | Evet |
|Son kullanıcı etkileşimi | Hayır | Evet |
|İçerik taşınırsa kalıcı olur | Hayır | Evet, Microsoft 365 kiracınızda |
|Öğeyi kayıt olarak bildirme| Hayır | Evet |
|Etiketlendiğinde veya bir olayı temel alarak bekletme süresini başlatma | Hayır | Evet |
|Değerlendirmeyi bırakma | Hayır| Evet |
|7 yıla kadar edat kanıtı | Hayır |Evet, değerlendirmeyi kullandığınızda veya öğe bir kayıt olarak işaretlendiğinde|
|Yönetici etkinliklerini denetleme| Evet | Evet|
|Saklama eylemlerini denetleme| Hayır | Evet <sup>\*</sup> |
|Bekletmeye tabi öğeleri tanımlama: <br /> - İçerik Arama <br /> - Veri sınıflandırma sayfası, içerik gezgini, etkinlik gezgini | <br /> Hayır <br /> Hayır | <br /> Evet <br /> Evet|

**Dipnot:**

<sup>\*</sup>İçeriği kayıt veya mevzuat kaydı olarak işaretlemeyen bekletme etiketleri için denetim olayları, SharePoint veya OneDrive bir öğenin etiketi uygulandığı, değiştirildiği veya kaldırıldığı durumla sınırlıdır. Bekletme etiketlerinin denetim ayrıntıları için bu sayfadaki [Bekletme eylemlerini denetleme](#auditing-retention-actions) bölümüne bakın.

### <a name="combining-retention-policies-and-retention-labels"></a>Bekletme ilkelerini ve bekletme etiketlerini birleştirme

Yalnızca bekletme ilkelerini veya yalnızca bekletme etiketlerini kullanma arasında seçim yapmanız gerekmez. Her iki yöntem birlikte kullanılabilir ve aslında daha kapsamlı bir çözüm için birbirini tamamlayıcı niteliktedir.

Aşağıdaki örnekler, bekletme ilkelerini ve bekletme etiketlerini aynı konum için birleştirmenin yollarından yalnızca bazılarıdır.

Bekletme ilkeleri ve bekletme etiketlerinin birlikte nasıl çalıştığı ve bunların birleştirilmiş sonuçlarının nasıl belirleneceği hakkında daha fazla bilgi için, bu sayfadaki [bekletme ilkelerini ve önceliklerini](#the-principles-of-retention-or-what-takes-precedence) açıklayan bölüme bakın.

**Kullanıcıların otomatik silmeyi geçersiz kılabilir örneği**

Senaryo: Varsayılan olarak, kullanıcıların OneDrive hesaplarındaki içerik beş yıl sonra otomatik olarak silinir, ancak kullanıcıların belirli belgeler için bunu geçersiz kılma seçeneğine sahip olması gerekir.

1. İçeriği son değiştirilmeden beş yıl sonra otomatik olarak silen ve ilkeyi tüm OneDrive hesaplarına uygulayan bir bekletme ilkesi oluşturup yapılandırabilirsiniz.

2. İçeriği sonsuza kadar saklayan bir bekletme etiketi oluşturup yapılandırıp bunu tüm OneDrive hesaplarında yayımladığınız bir etiket ilkesine eklersiniz. Kullanıcılara bu etiketin beş yıl sonra değiştirilmemesi durumunda otomatik silmenin dışında tutulması gereken belirli belgelere nasıl el ile uygulanacağını açıklarsınız.

**Öğeleri daha uzun süre saklama örneği**

Senaryo: Varsayılan olarak, SharePoint öğeler beş yıl sonra otomatik olarak korunur ve silinir, ancak belirli kitaplıklardaki belgeler on yıl boyunca saklanmalıdır.

1. Beş yıl sonra içeriği otomatik olarak saklayan ve silecek bir bekletme ilkesi oluşturup yapılandırıp ilkeyi tüm SharePoint ve Microsoft 365 Grupları örneklerine uygularsınız.

2. İçeriği otomatik olarak on yıl boyunca saklayan bir bekletme etiketi oluşturup yapılandırabilirsiniz. Bu etiketi, belirli belge kitaplıklarındaki tüm öğeler tarafından devralınacak varsayılan bir etiket olarak uygulayabilmeleri için SharePoint site yöneticilerine yayımlarsınız.

**Daha kısa bir zaman aralığındaki öğeleri silme örneği**

Senaryo: Varsayılan olarak, e-postalar korunmaz ancak on yıl sonra otomatik olarak silinir. Ancak, yayın öncesi kod adına sahip belirli bir projeyle ilgili e-postaların bir yıl sonra otomatik olarak silinmesi gerekir.

1. On yıl sonra içeriği otomatik olarak silecek ve ilkeyi tüm Exchange alıcılara uygulayan bir bekletme ilkesi oluşturup yapılandırabilirsiniz.

2. Bir yıl sonra içeriği otomatik olarak silecek bir bekletme etiketi oluşturup yapılandırabilirsiniz. Bu etiketi ilgili e-postalara uygulama seçenekleri şunlardır:
    - Proje kodu adını anahtar sözcük olarak kullanarak içeriği tanımlayan bir otomatik etiketleme ilkesi oluşturur ve ilkeyi tüm Exchange alıcılara uygularsınız
    - Etiketi yayımlar ve projede yer alan kullanıcılara bu etiketi uygulayan Outlook otomatik kural oluşturmayı açıklarsınız
    - Etiketi yayımlar ve kullanıcılara projeyle ilgili tüm e-postalar için Outlook bir klasör oluşturmalarını ve yayımlanmış etiketi klasöre uygulamalarını ve ardından projeyle ilgili tüm e-postaları bu klasöre taşımak için bir Outlook kuralı oluşturmalarını emredersiniz

## <a name="how-long-it-takes-for-retention-settings-to-apply"></a>Bekletme ayarlarının uygulanması ne kadar sürer?

Bir bekletme etiketini otomatik olarak uygulamak üzere iş yükleri ve etiket ilkeleri için bekletme ilkeleri gönderdiğinizde, bekletme ayarlarının içeriğe uygulanması için 7 güne kadar izin verin:

- [Bekletme ilkelerinin geçerli olması ne kadar sürer?](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- [Bekletme etiketlerinin etkili olması ne kadar sürer?](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect)

Benzer şekilde, etiketleri yayımladıktan sonra bekletme etiketlerinin uygulamalarda görünür olması için 7 güne kadar izin verin:

- [Bekletme etiketleri uygulanabilecek duruma geldiğinde](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply)

Genellikle ilkeler geçerli olur ve etiketler 7 günden daha hızlı görünür. Ancak bu süreci etkileyebilecek birçok olası değişkenle, en fazla 7 gün planlamak en iyisidir.

## <a name="adaptive-or-static-policy-scopes-for-retention"></a>Bekletme için uyarlamalı veya statik ilke kapsamları

Bekletme ilkesi veya bekletme etiketi ilkesi oluşturduğunuzda, ilkenin kapsamını tanımlamak için uyarlamalı ve statik arasında seçim yapmanız gerekir.

- **Uyarlamalı kapsam**, belirttiğiniz bir sorgu kullanır, bu nedenle üyelik statik değildir ancak seçili konumlar için belirttiğiniz özniteliklere veya özelliklere göre günlük çalıştırılarak dinamiktir. Tek bir ilkeyle birden çok uyarlamalı kapsam kullanabilirsiniz.

    Örnek: Yöneticilere yönelik e-postalar ve OneDrive belgeleri standart kullanıcılardan daha uzun bir saklama süresi gerektirir. "Yönetici" Azure AD öznitelik iş unvanını kullanan uyarlamalı bir kapsama sahip bir bekletme ilkesi oluşturur ve ardından ilke için Exchange e-posta ve OneDrive hesapları konumlarını seçersiniz. Uyarlamalı kapsam bu değerleri otomatik olarak aldığından, bu kullanıcılar için e-posta adreslerini veya OneDrive URL'lerini belirtmeniz gerekmez. Yeni yöneticiler için bekletme ilkesini yeniden yapılandırmanıza gerek yoktur çünkü bu yeni kullanıcılar e-posta ve OneDrive karşılık gelen değerleriyle otomatik olarak alınır.

- **Statik kapsam** sorguları kullanmaz ve belirtilen bir konum için tüm örneklere uygulanabileceği veya söz konusu konum için belirli örnekler için dahil etme ve dışlamaları kullanabilecek şekilde yapılandırması sınırlıdır. Bu üç seçenek bazen sırasıyla "kuruluş genelinde", "içerir" ve "dışlar" olarak adlandırılır.

    Örnek: Yöneticilere yönelik e-postalar ve OneDrive belgeleri standart kullanıcılardan daha uzun bir saklama süresi gerektirir. İlke için Exchange e-posta ve OneDrive hesapları konumlarını seçen statik kapsamlı bir bekletme ilkesi oluşturursunuz. Exchange e-posta konumu için, yalnızca yöneticileri içeren bir grubu tanımlayabilirsiniz, bu nedenle bekletme ilkesi için bu grubu belirtirsiniz ve ilke oluşturulduğunda ilgili e-posta adresleriyle grup üyeliği alınır. OneDrive hesapları konumu için, her yönetici için ayrı ayrı OneDrive URL'leri belirlemeniz ve belirtmeniz gerekir. Yeni yöneticiler için, yeni e-posta adreslerini eklemek ve URL'leri OneDrive için bekletme ilkesini yeniden yapılandırmanız gerekir. Ayrıca, bir yöneticinin UPN'sinde değişiklik olduğunda OneDrive URL'lerini de güncelleştirmeniz gerekir.

    OneDrive URL'lerin güvenilir bir şekilde belirtilmesi özellikle zordur çünkü varsayılan olarak bu URL'ler kullanıcı OneDrive ilk kez erişene kadar oluşturulmaz. Ayrıca, bir kullanıcının UPN'si değişirse ve sizin de haberiniz olmayabilir, OneDrive URL'si otomatik olarak değişir.

Uyarlamalı kapsamları kullanmanın avantajları:

- [İlke başına öğe sayısıyla](retention-limits.md#maximum-number-of-items-per-policy) ilgili sınır yoktur. Uyarlamalı ilkeler kiracı [başına en fazla ilke sayısına](retention-limits.md#maximum-number-of-policies-per-tenant) tabi olsa da, daha esnek yapılandırma büyük olasılıkla çok daha az ilkeyle sonuçlanır.

- Bekletme gereksinimleriniz için daha güçlü hedefleme. Örneğin, var olan Azure AD özniteliklerini kullanarak, bu amaç için grup oluşturma ve bakımını yönetme ek yükü olmadan kullanıcılara coğrafi konumlarına göre farklı bekletme ayarları atayabilirsiniz.

- Sorgu tabanlı üyelik, grup üyeliğine veya departmanlar arası iletişime dayanan dış süreçlere güvenilir bir şekilde yansıtılmayan iş değişikliklerine karşı dayanıklılık sağlar.

- Tek bir bekletme ilkesi hem Microsoft Teams hem de Yammer için konumlar içerebilir, ancak statik bir kapsam kullandığınızda bu konumlar kendi bekletme ilkelerini gerektirir.

- Belirli bekletme ayarlarını yalnızca etkin olmayan posta kutularına uygulayabilirsiniz. İlke atandığı sırada statik kapsamlar etkin olmayan posta kutularına sahip alıcıların eklenmesini desteklemediğinden bu yapılandırma statik kapsamla mümkün değildir.

Statik kapsamları kullanmanın avantajları:

- Bir iş yükü için tüm örneklerin otomatik olarak seçilmesini istiyorsanız daha basit yapılandırma.

    "Eklemeler" ve "dışlar" için, belirtmeniz gereken örnek sayısı düşükse ve değişmezse bu seçenek başlangıçta daha basit bir yapılandırma olabilir. Ancak, bu sayıda örnek artmaya başladığında ve kuruluşunuzda ilkelerinizi yeniden yapılandırmanızı gerektiren sık sık değişiklikleriniz olduğunda uyarlamalı kapsamların yapılandırılması daha basit ve bakımı çok daha kolay olabilir.

- **Skype Kurumsal** ve **Exchange ortak klasör** konumları uyarlamalı kapsamları desteklemez. Bu konumlar için statik bir kapsam kullanmanız gerekir.

Yapılandırma bilgileri için bkz [. Uyarlamalı kapsamları yapılandırma](retention-settings.md#configuration-information-for-adaptive-scopes).

Kaydedilmiş bir web seminerini izlemek için (kayıt gerektirir), [Uyarlamalı Kapsamlar hakkında Ayrıntılı Bakış sayfasını ziyaret edin](https://mipc.eventbuilder.com/event/45703).

> [!IMPORTANT]
> Şu anda uyarlamalı kapsamlar, [bekletme ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'nin](#use-preservation-lock-to-restrict-changes-to-policies) desteklenmemektedir.

## <a name="policy-lookup"></a>İlke araması

Microsoft 365 konumlar için birden çok bekletme ilkesi ve yayımladığınız veya otomatik uyguladığınız birden çok bekletme etiketi ilkesi yapılandırabilirsiniz. Belirli kullanıcılara, sitelere ve Microsoft 365 gruplarına atanan bekletme ilkelerini bulmak için, Microsoft Purview uyumluluk portalındaki **Veri yaşam döngüsü yönetimi** veya **Kayıt yönetimi** çözümlerinden **İlke araması'nı** kullanın.

Örneğin:

![Belirli kullanıcılara, sitelere ve Microsoft 365 gruplarına atanan bekletme ilkelerini bulmak için ilke araması ](../media/policy-lookup.png)

Bir kullanıcının tam e-posta adresini, sitenin tam URL'sini veya Microsoft 365 grubu için tam e-posta adresini belirtmeniz gerekir. Örneğin joker karakterler veya kısmi eşleşmeler kullanamazsınız.

Siteler seçeneği OneDrive hesapları içerir. Kullanıcının OneDrive hesabının URL'sini belirtme hakkında bilgi için bkz. [Kuruluşunuzdaki tüm kullanıcı OneDrive URL'lerinin listesini alma](/onedrive/list-onedrive-urls).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Bekletme ilkeleri veya öncelik neleri alır?

Bekletme etiketlerinden farklı olarak, aynı içeriğe birden fazla bekletme ilkesi uygulayabilirsiniz. Her bekletme ilkesi bir saklama eylemine ve silme eylemine neden olabilir. Ayrıca, bu öğe bir bekletme etiketinden bu eylemlere de tabi olabilir.

Bu senaryoda, öğeler birbiriyle çakışabilecek birden çok bekletme ayarına tabi olabileceğinde, sonucu belirlemek için öncelikli olan nedir?

Sonuç, hangi tek bekletme ilkesinin veya tek bekletme etiketinin kazanıldığı değil, bir öğenin ne kadar süreyle korunacak (varsa) ve bir öğenin ne zaman silindiği (varsa) değildir. Bu iki eylem, bir öğeye uygulanan tüm bekletme ayarlarından birbirinden bağımsız olarak hesaplanır.

Örneğin, bir öğe yalnızca silme eylemi için yapılandırılan bir bekletme ilkesine ve korunacak ve sonra silinecek şekilde yapılandırılmış başka bir bekletme ilkesine tabi olabilir. Sonuç olarak, bu öğenin yalnızca bir saklama eylemi vardır, ancak iki silme eylemi vardır. Bekletme ve silme eylemleri birbiriyle çakışabilir ve iki silme eylemi çakışan bir tarihe sahip olabilir. Elde tutma ilkeleri sonucu açıklar.

Yüksek düzeyde saklamanın her zaman kalıcı silmeden öncelikli olduğundan ve en uzun saklama süresinin kazanılacağından emin olabilirsiniz. Bu iki basit kural her zaman bir öğenin ne kadar süre tutulacağını karar verir.

Bir öğenin kalıcı olarak ne zaman silineceğini belirleyen birkaç faktör daha vardır. Bu, bekletme etiketinden silme eyleminin bir bekletme ilkesinden silme eyleminden her zaman öncelikli olmasını içerir.

Tek bir öğenin elde tutma ve silme sonuçlarını anlamak için aşağıdaki akışı kullanın. Burada her düzey, yukarıdan aşağıya doğru çakışmalar için bir bağlama kesici görevi görür. Daha fazla çakışma olmadığı için sonuç ilk düzeye göre belirlenirse, bir sonraki düzeye ilerlemeye gerek yoktur ve bu şekilde devam eder.

> [!IMPORTANT]
> Bekletme etiketleri kullanıyorsanız: Aynı öğedeki birden çok bekletme ayarının sonucunu belirlemek için ilkeleri uygulamadan önce [, hangi bekletme etiketinin uygulandığını](#only-one-retention-label-at-a-time) bildiğinizden emin olun.

![Bekletme ilkelerinin diyagramı.](../media/principles-of-retention.png)

Her ilkeyi daha ayrıntılı bir şekilde açıklamadan önce, öğe için saklama süresi ile bekletme ilkesinde veya bekletme etiketinde belirtilen saklama süresi arasındaki farkı anlamak önemlidir. Bunun nedeni, varsayılan yapılandırma bir öğe oluşturulduğunda bekletme süresini başlatmak olsa da, böylece öğe için saklama süresinin sonu sabitlenmiş olsa da, dosyaların dosyanın en son değiştirildiği zaman bekletme süresini başlatmak için yapılandırmayı da desteklemesidir. Bu alternatif yapılandırmayla, dosya her değiştirildiğinde, saklama süresinin başlangıcı sıfırlanır ve bu da öğenin saklama süresinin sonunu uzatır. Bekletme etiketleri, etiketlendiğinde ve bir olayın başlangıcında bekletme süresinin başlatılmasını da destekler.

İlkeleri bir dizi Evet ve Hayır sorusuyla uygulamada uygulamak için [bekletme akış çizelgesini](retention-flowchart.md) de kullanabilirsiniz.

Dört farklı ilkenin açıklaması:

1. **Bekletme silme işlemine göre kazanır.** İçerik, saklama ayarlarına sahip olduğunda kalıcı olarak silinmez. Bu ilke, içeriğin uyumluluk nedeniyle korunmasını sağlar, ancak silme işlemi yine de başlatılabilir (kullanıcı tarafından başlatılan veya sistem tarafından başlatılan) ve sonuç olarak, içeriği kullanıcıların ana görünümünden kaldırabilir. Ancak kalıcı silme işlemi askıya alınır. İçeriğin nasıl ve nerede tutulacağı hakkında daha fazla bilgi için her iş yükü için aşağıdaki bağlantıları kullanın:

    - [Bekletme SharePoint ve OneDrive için nasıl çalışır?](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)
    - [Bekletme Microsoft Teams ile nasıl çalışır?](retention-policies-teams.md#how-retention-works-with-microsoft-teams)
    - [Bekletme Yammer ile nasıl çalışır?](retention-policies-yammer.md#how-retention-works-with-yammer)
    - [Bekletme Exchange için nasıl çalışır?](retention-policies-exchange.md#how-retention-works-for-exchange)

    **Bu ilk ilkeye örnek**: E-posta iletisi, oluşturulduktan üç yıl sonra öğeleri silmek üzere yapılandırılmış Exchange için bekletme ilkesine tabidir ve ayrıca öğeleri oluşturulduktan beş yıl sonra saklamak üzere yapılandırılmış bir bekletme etiketi de vardır.

    Bu bekletme eylemi silme işleminden öncelikli olduğundan, e-posta iletisi beş yıl boyunca saklanır. Bekletme eylemi etkinken askıya alınan silme eylemi nedeniyle e-posta iletisi beş yılın sonunda kalıcı olarak silinir.

2. **En uzun saklama süresi kazanır.** İçerik, içeriği farklı süreler boyunca saklayan birden çok bekletme ayarına tabiyse, içerik öğe için en uzun saklama süresinin sonuna kadar korunur.

    > [!NOTE]
    > 5 yıllık süre, dosyanın en son ne zaman değiştirildiğine göre başlayacak şekilde yapılandırıldığından ve 7 yıllık süre dosyanın oluşturulduğundan itibaren başlayacak şekilde yapılandırıldığından, bekletme ilkesinde veya etiketinde 5 yıllık bir saklama süresi elde edilir.

    **Bu ikinci ilke için örnek**: Pazarlama SharePoint sitesindeki belgeler iki saklama ilkesine tabidir. İlk bekletme ilkesi, tüm SharePoint siteleri için öğeleri oluşturulduktan sonra beş yıl boyunca saklayacak şekilde yapılandırılır. İkinci bekletme ilkesi, belirli SharePoint siteleri için öğeleri oluşturulduktan sonra on yıl boyunca saklayacak şekilde yapılandırılır.

    Bu Pazarlama SharePoint sitesindeki belgeler, öğe için en uzun saklama süresi olduğundan on yıl boyunca saklanır.

3. **Silme işlemleri için örtük olarak açıkça kazanır.** Çakışmalar artık bekletme için çözümlenmiş durumdaysa, yalnızca silme işlemleri için çakışmalar kalır:

    1. Bekletme ayarları kapsayıcıdan örtük olarak atanmak yerine tek bir öğeye uygulandığından, bekletme etiketi (ancak uygulandı) bekletme ilkeleriyle karşılaştırıldığında açık saklama sağlar. Bu, bekletme etiketinden silme eyleminin her zaman herhangi bir bekletme ilkesindeki silme eyleminden öncelikli olduğu anlamına gelir.

        **Bu üçüncü ilke (etiket) için örnek**: Belge, sırasıyla beş yıl ve on yıllık silme eylemine ve ayrıca yedi yıllık silme eylemine sahip bir bekletme etiketine sahip iki bekletme ilkesine tabidir.

        Saklama etiketinden silme eylemi öncelikli olduğundan, belge yedi yıl sonra kalıcı olarak silinir.

    2. Yalnızca bekletme ilkeleriniz varsa: Bir konum için bekletme ilkesi uyarlamalı bir kapsam veya belirli örnekleri (Exchange e-posta için belirli kullanıcılar gibi) içeren statik bir kapsam kullanıyorsa, bekletme ilkesi aynı konum için tüm örnekler için yapılandırılmış statik bir kapsamdan önceliklidir.

        Bir konum için tüm örnekler için yapılandırılan statik kapsam bazen "kuruluş genelinde ilke" olarak adlandırılır. Örneğin, **e-postayı ve** **varsayılan Tüm alıcılar** ayarını Exchange. Ya da **siteleri ve** **Varsayılan Tüm siteler** ayarını SharePoint. Bekletme ilkeleri kuruluş genelinde olmadığında ancak uyarlamalı bir kapsamla veya belirli örnekleri içeren statik bir kapsamla yapılandırıldığında, bu düzeyde eşit önceliğe sahiptir.

        **Bu üçüncü ilke (ilkeler) için örnek 1**: E-posta iletisi iki bekletme ilkesine tabidir. İlk bekletme ilkesi kapsam dışıdır ve on yıl sonra öğeleri siler. İkinci bekletme ilkesinin kapsamı belirli posta kutularına göre belirlenmiştir ve beş yıl sonra öğeleri siler.

        Kapsamı belirlenmiş saklama ilkesindeki silme eylemi kuruluş genelinde saklama ilkesinden öncelikli olduğundan, e-posta iletisi beş yıl sonra kalıcı olarak silinir.

        **Bu üçüncü ilke (ilkeler) için örnek 2**: Kullanıcının OneDrive hesabındaki bir belge iki saklama ilkesine tabidir. İlk bekletme ilkesinin kapsamı bu kullanıcının OneDrive hesabını içerecek şekilde belirlenmiştir ve 10 yıl sonra silme eylemi vardır. İkinci bekletme ilkesinin kapsamı bu kullanıcının OneDrive hesabını içerecek şekilde belirlenmiştir ve yedi yıl sonra silme eylemi vardır.

        Her iki bekletme ilkesi de belirli örnekleri içerecek şekilde belirlendiğinden bu belgenin kalıcı olarak silineceği bu düzeyde belirlenemez.

4. **En kısa silme süresi kazanır.** Öğelerin bekletme ilkelerinden ne zaman silineceğini ve sonucun önceki düzeyden çözümlenemeyeceğini belirlemek için geçerlidir: İçerik, öğe için en kısa saklama süresinin sonunda kalıcı olarak silinir.

    > [!NOTE]
    > 7 yıllık saklama süresine sahip bir bekletme ilkesi, 5 yıllık bir bekletme ilkesine göre kazanılabilir çünkü ilk ilke, dosyanın oluşturulduğu tarihe ve dosyanın son değiştirildiği ikinci bekletme ilkesine göre bekletme süresini başlatacak şekilde yapılandırılır.

    **Bu dördüncü ilke örneği**: Kullanıcının OneDrive hesabındaki bir belge iki bekletme ilkesine tabidir. İlk bekletme ilkesinin kapsamı bu kullanıcının OneDrive hesabını içerecek şekilde belirlenmiştir ve dosya oluşturulduktan sonra 10 yıllık silme eylemine sahiptir. İkinci bekletme ilkesinin kapsamı, bu kullanıcının OneDrive hesabını içerecek şekilde belirlenmiştir ve dosya oluşturulduktan sonra yedi yıllık bir silme eylemine sahiptir.

    Bu belge yedi yıl sonra kalıcı olarak silinir çünkü bu, bu iki kapsamlı saklama ilkesindeki öğe için en kısa saklama süresidir.

eBulma saklamaya tabi öğeler de ilk saklama ilkesi kapsamındadır; herhangi bir bekletme ilkesi veya bekletme etiketi tarafından kalıcı olarak silinemez. Bu saklama serbest bırakıldığında saklama ilkeleri bunlar için geçerli olacaktır. Örneğin, bunlar daha sonra süresiz saklama süresine veya silme eylemine tabi olabilir.

### <a name="principles-of-retention-examples-that-combine-retain-and-delete-actions"></a>Saklama ve silme eylemlerini birleştiren bekletme örnekleri ilkeleri

Aşağıdaki örnekler, farklı saklama ve silme eylemleri birleştirildiğinde elde tutma ilkelerini göstermek için daha karmaşıktır. Örneklerin daha kolay izlenebilmesini sağlamak için, tüm bekletme ilkeleri ve etiketleri, öğe oluşturulduğunda bekletme süresini başlatma varsayılan ayarını kullanır, böylece bekletme döneminin sonu öğe için aynıdır.

1. Bir öğeye aşağıdaki bekletme ayarları uygulanır:

    - Beş yıl sonra yalnızca silme için bekletme ilkesi
    - Üç yıl boyunca saklayan ve ardından silecek bir bekletme ilkesi
    - Yedi yıl boyunca yalnızca saklamayı sağlayan bir bekletme etiketi

    **Sonuç**: Saklama, silme işleminden öncelikli olduğundan ve yedi yıl öğe için en uzun saklama süresi olduğundan, öğe yedi yıl boyunca korunur. Bu saklama döneminin sonunda, saklama ilkelerinden silme eylemi nedeniyle öğe kalıcı olarak silinir.

    İki bekletme ilkesi silme eylemleri için farklı tarihlere sahip olsa da, öğenin kalıcı olarak silinebileceği en erken tarih, her iki silme tarihi de daha uzun olan en uzun saklama süresinin sonundadır.

2. Bir öğeye aşağıdaki bekletme ayarları uygulanır:

    - On yıl sonra yalnızca silebilen kuruluş genelinde saklama ilkesi
    - Kapsamı beş yıl boyunca tutulan ve ardından silen belirli örneklerle kapsamlı bir bekletme ilkesi
    - Üç yıl boyunca saklayan ve ardından silecek bir bekletme etiketi

    **Sonuç**: Bu, öğe için en uzun saklama süresi olduğundan, öğe beş yıl boyunca saklanır. Bu saklama döneminin sonunda, saklama etiketinden üç yıllık silme eylemi nedeniyle öğe kalıcı olarak silinir. Bekletme etiketlerinden silme, tüm bekletme ilkelerinden silme işleminden önceliklidir. Bu örnekte, tüm çakışmalar üçüncü düzey tarafından çözülür.

## <a name="use-preservation-lock-to-restrict-changes-to-policies"></a>İlkelerde yapılan değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma

Bazı kuruluşların Menkul Kıymetler ve Exchange Komisyonu (SEC) Kuralı 17a-4 gibi düzenleyici kuruluşlar tarafından tanımlanan kurallara uyması gerekebilir. Bu kural, saklama ilkesi açıldıktan sonra kapatılamayacağını veya daha az kısıtlayıcı hale getirilemeyeceğini gerektirebilir.

Koruma Kilidi, kuruluşunuzun bu tür yasal gereksinimleri karşılayabilmesini sağlar çünkü bir bekletme ilkesini veya bekletme etiketi ilkesini kilitler ve böylece yönetici de dahil olmak üzere hiç kimse ilkeyi kapatabilir, ilkeyi silebilir veya daha az kısıtlayıcı hale getiremez.

Saklama ilkesi veya bekletme etiketi ilkesi oluşturulduktan sonra Koruma Kilidi uygularsınız. Daha fazla bilgi ve yönergeler için bkz [. Saklama ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma](retention-preservation-lock.md).

## <a name="releasing-a-policy-for-retention"></a>Bekletme için ilke yayımlama

Bekletme ilkelerinizin Koruma Kilidi olmadığından, ilkelerinizi istediğiniz zaman silebilirsiniz; bu da bekletme ilkesi için bekletme ayarlarını etkin bir şekilde kapatır ve bekletme etiketleri artık bekletme etiketi ilkelerinden uygulanamaz. Daha önce uygulanan tüm bekletme etiketleri yapılandırılmış bekletme ayarlarıyla kalır ve bu etiketler için, öğelerin etiketlendiği zamanı temel almayan saklama süresini yine güncelleştirebilirsiniz.

Ayrıca bir ilkeyi koruyabilir, ancak konum durumunu kapalı olarak değiştirebilir veya ilkeyi devre dışı bırakabilirsiniz. Bir diğer seçenek de ilkeyi, artık belirli kullanıcıları, siteleri, grupları vb. içeremeyecek şekilde yeniden yapılandırmaktır.

Belirli konumlar için ek bilgiler:

- **Siteleri ve OneDrive hesaplarını SharePoint:**

    SharePoint siteler ve OneDrive hesapları için bir bekletme ilkesi yayımladığınızda, ilkeden elde tutulması gereken tüm içerikler, yanlışlıkla veri kaybını önlemek için 30 gün boyunca korunmaya devam eder. Bu 30 günlük yetkisiz kullanım süresi boyunca silinen dosyalar hala korunur (dosyalar Koruma Bekletme kitaplığına eklenmeye devam eder), ancak koruma bekletme kitaplığını düzenli aralıklarla temizleyen zamanlayıcı işi bu dosyalar için askıya alınır, böylece gerekirse bunları geri yükleyebilirsiniz.

    bu 30 günlük yetkisiz kullanım süresinin bir istisnası, ilkeyi SharePoint veya OneDrive hesapları için bir veya daha fazla siteyi dışlamak üzere güncelleştirdiğinizdedir; bu durumda zamanlayıcı işi, 30 günlük gecikme olmadan Koruma Bekletme kitaplığındaki bu konumların dosyalarını siler.

    Koruma Bekletme kitaplığı hakkında daha fazla bilgi için bkz. [Bekletme SharePoint ve OneDrive için nasıl çalışır](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)?

    Yetkisiz kullanım süresindeki davranış nedeniyle, ilkeyi yeniden etkinleştirirseniz veya konum durumunu 30 gün içinde yeniden açarsanız, ilke bu süre boyunca kalıcı bir veri kaybı olmadan devam eder.

- **E-posta ve Microsoft 365 Grupları Exchange**

  İlke yayımlandığında [etkin olmayan](inactive-mailboxes-in-office-365.md) posta kutuları için bir bekletme ilkesi yayımladığınızda:

  - Bekletme ilkesi açıkça bir posta kutusuna uygulanırsa, bekletme ayarları artık geçerli olmaz. Bekletme ayarları uygulanmazsa, etkin olmayan bir posta kutusu her zamanki gibi otomatik silme için uygun hale gelir.

    Açık saklama ilkesi, uyarlamalı bir ilke kapsamı veya ilkenin uygulandığı ve daha sonra etkin olmayan bir posta kutusu belirten bir ekleme yapılandırmasına sahip statik ilke kapsamı gerektirir

  - Bekletme ilkesi bir posta kutusuna örtük olarak uygulanmışsa ve yapılandırılmış bekletme eylemi korunacaksa, bekletme ilkesi uygulanmaya devam eder ve etkin olmayan bir posta kutusu hiçbir zaman otomatik silme için uygun olmaz. Saklama süresi dolduğunda saklama eylemi artık geçerli olmadığında, Exchange yöneticisi [artık etkin olmayan posta kutusunu el ile silebilir](delete-an-inactive-mailbox.md)

    Örtük saklama ilkesi, **Tüm alıcılar** (Exchange e-posta için) veya **Tüm gruplar** (Microsoft 365 Grupları için) yapılandırmasıyla statik bir ilke kapsamı gerektirir.

    Bekletme ilkeleri uygulanmış etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. [Etkin olmayan posta kutuları ve Microsoft 365 bekletme](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-microsoft-365-retention).

## <a name="auditing-retention-configuration-and-actions"></a>Bekletme yapılandırmasını ve eylemlerini denetleme

[Denetim etkinleştirildiğinde](turn-audit-log-search-on-or-off.md), bekletme için denetim olayları hem yönetim yapılandırması (bekletme ilkeleri ve bekletme etiketleri) hem de bekletme eylemleri (yalnızca bekletme etiketleri) için desteklenir.

### <a name="auditing-retention-configuration"></a>Bekletme yapılandırmasını denetleme

Bekletme ilkeleri ve bekletme etiketleri için yönetici yapılandırması, bir bekletme ilkesi veya etiket oluşturulduğunda, yeniden yapılandırıldığında veya silindiğinde denetim olayları olarak günlüğe kaydedilir.

Denetim olaylarının tam listesi için bkz [. Bekletme ilkesi ve bekletme etiketi etkinlikleri](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="auditing-retention-actions"></a>Bekletme eylemlerini denetleme

Denetim olayları olarak günlüğe kaydedilen bekletme eylemleri yalnızca bekletme etiketleri için kullanılabilir ve bekletme ilkeleri için kullanılamaz:

- SharePoint veya OneDrive bir öğeye bekletme etiketi uygulandığında, değiştirildiğinde veya öğeden kaldırıldığında:
  - **Dosya ve sayfa etkinlikleri'nden** **Dosya için bekletme etiketi değiştirildi'yi** seçin

- SharePoint etiketli bir öğe kayıt olarak işaretlendiğinde ve bir kullanıcı tarafından kilitlendiğinde veya kilitlendiğinde:
  - **Dosya ve sayfa etkinlikleri'nden** **Kilitsiz kayıt durumu değiştirildi** ve **Kayıt durumu kilitli olarak değiştirildi'yi** seçin

- İçeriği kayıt veya mevzuat kaydı olarak işaretleyen bir bekletme etiketi Exchange'daki bir öğeye uygulandığında:
  - **posta kutusu etkinlikleri Exchange** **etiketli ileti'yi seçin**

- SharePoint, OneDrive veya Exchange etiketli bir öğe kayıt veya mevzuat kaydı olarak işaretlendiğinde ve kalıcı olarak silindiğinde:
  - **Dosya ve sayfa etkinlikleri'nden** **Kayıt olarak işaretlenmiş Silinmiş dosya'yı** seçin

- Bir değerlendirme gözden geçiren, saklama süresinin sonuna ulaşmış bir öğe için eylem gerçekleştirdiğinde:
  - **Elden çıkarma gözden geçirme etkinliklerinden** **Onaylı elden çıkarma**, **Genişletilmiş saklama süresi**, **Yeniden etiketlenen öğe** veya **Gözden geçirenler eklendi'yi** seçin

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri için PowerShell cmdlet'leri

Bekletme cmdlet'lerini kullanmak [için önce Office 365 Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmanız](/powershell/exchange/connect-to-scc-powershell) gerekir. Ardından aşağıdaki cmdlet'lerden birini kullanın:

- [Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)

- [New-ComplianceTag](/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag)

- [Enable-complianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](/powershell/module/exchange/get-compliancetagstorage)

- [Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig)

- [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/set-recordreviewnotificationtemplateconfig)

- [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancerule)

- [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule)

## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Bekletme ilkeleri ve bekletme etiketleri veya eBulma saklamaları ne zaman kullanılır?

[Bir eBulma olayıyla oluşturduğunuz](create-ediscovery-holds.md) bekletme ayarları ve tutmaları her ikisi de verilerin kalıcı olarak silinmesini engelleyebilse de, farklı senaryolar için tasarlanmıştır. Farklılıkları anlamanıza ve hangisini kullanacağınıza karar vermenize yardımcı olmak için aşağıdaki kılavuzu kullanın:

- Bekletme ilkeleri ve bekletme etiketlerinde belirttiğiniz bekletme ayarları, uyumluluk gereksinimleri için verileri saklamak veya silmek için uzun vadeli bir veri yaşam döngüsü yönetimi stratejisi için tasarlanmıştır. Kapsam genellikle geniştir ve asıl odak tek tek kullanıcılar yerine konum ve içeriktir. Bekletme süresinin başlangıcı ve sonu yapılandırılabilir ve ek yönetici müdahalesi olmadan içeriği otomatik olarak silme seçeneği sağlanır.

- eBulma için ayrı tutmalar (eBulma (Standart) veya eBulma (Premium) durumları), yasal bir araştırma için verileri korumak üzere sınırlı bir süre için tasarlanmıştır. Kapsam belirlidir ve odak, tanımlanan kullanıcıların sahip olduğu içeriktir. Koruma döneminin başlangıcı ve sonu yapılandırılabilir değildir, ancak ayrı ayrı yönetici eylemlerine bağımlıdır; ayrı tutma serbest bırakıldığında içeriği otomatik olarak silme seçeneği yoktur.

Bekletmeyi ayrı tutmalarla karşılaştırmak için özet:

|Dikkate|Saklama |eBulma tutmaları|
|:-----|:-----|:-----|:-----|
|İş gereksinimi: |Uyumluluk |Yasal |
|Zaman kapsamı: |Uzun vadeli |Kısa vadeli |
|Odak: |Geniş, içerik tabanlı |Belirli, kullanıcı tabanlı |
|Başlangıç ve bitiş tarihi yapılandırılabilir: |Evet |Hayır |
|İçerik silme: |Evet (isteğe bağlı) |Hayır |
|Yönetim ek yükleri: |Düşük |Yüksek |

İçerik hem bekletme ayarlarına hem de eBulma saklamaya tabiyse, eBulma saklama için içeriğin korunması her zaman önceliklidir. Bu şekilde, [saklama ilkeleri](#the-principles-of-retention-or-what-takes-precedence) eBulma'ya genişletir, çünkü bir yönetici saklamayı el ile serbest bırakana kadar verileri korurlar. Ancak, bu önceliğe rağmen, uzun süreli veri yaşam döngüsü yönetimi için eBulma tutmalarını kullanmayın. Verilerin otomatik olarak silinmesiyle ilgili endişeniz varsa, öğeleri sonsuza kadar saklamak için bekletme ayarlarını yapılandırabilir veya bekletme etiketleriyle [edat incelemesini](disposition.md#disposition-reviews) kullanabilirsiniz.

Verileri korumak için eski eBulma araçlarını kullanıyorsanız aşağıdaki kaynaklara bakın:

- Exchange:
  - [Yerinde Saklama ve Dava Tutma](/exchange/security-and-compliance/in-place-and-litigation-holds)
  - [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](./identify-a-hold-on-an-exchange-online-mailbox.md)

- SharePoint ve OneDrive:
  - [Bir servis talebine içerik ekleme ve kaynakları eBulma Merkezi'nde beklemeye alma](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Eski eKeşif araçlarını kullanımdan kaldırma](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Eski özellikler yerine bekletme ilkelerini ve bekletme etiketlerini kullanma

Veri yaşam döngüsü yönetimi için Microsoft 365 içeriği proaktif olarak saklamanız veya silmeniz gerekiyorsa, aşağıdaki eski özellikler yerine bekletme ilkelerini ve bekletme etiketlerini kullanmanızı öneririz.

Şu anda bu eski özellikleri kullanıyorsanız, bunlar Microsoft 365 bekletme ilkeleri ve bekletme etiketleriyle yan yana çalışmaya devam eder. Ancak bundan sonra, Microsoft 365'da birden çok iş yükünde içeriğin hem elde tutulmasını hem de silinmesini yönetmek için tek bir çözümden yararlanmak için Microsoft 365 bekletme ilkelerini ve bekletme etiketlerini kullanmanızı öneririz.

**Exchange Online eski özellikler:**

- Mesajlaşma [kayıtları yönetimi (MRM) olarak](/exchange/security-and-compliance/messaging-records-management/messaging-records-management) da bilinen [bekletme etiketleri ve bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) (yalnızca silme)

  Ancak aşağıdaki MRM özelliklerini kullanıyorsanız, şu anda Microsoft 365 saklama ilkeleri tarafından desteklenmediğini unutmayın:

  - Belirli bir süre sonra [kullanıcının birincil posta kutusundan gelen e-postaları](enable-archive-mailboxes.md) otomatik olarak arşiv posta kutusuna taşımaya yönelik arşiv posta kutularına yönelik arşiv ilkesi. Arşiv ilkesi (tüm ayarlarla) kullanıcının birincil ve arşiv posta kutusu için geçerli olan bir Microsoft 365 bekletme ilkesiyle birlikte kullanılabilir.

  - Bir yönetici tarafından posta kutusu içindeki belirli klasörlere uygulanan bekletme ilkeleri. Microsoft 365 bekletme ilkesi, posta kutusundaki tüm klasörler için geçerlidir. Ancak, bir yönetici kullanıcının [varsayılan bekletme etiketi](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder) olarak Outlook klasörlerine uygulayabileceği bekletme etiketlerini kullanarak farklı bekletme ayarları yapılandırabilir.

- [Dava tutma](create-a-litigation-hold.md) (yalnızca saklama)

   Dava tutmaları hala desteklense de, [uygun şekilde](#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds) Microsoft 365 saklama veya eBulma tutmaları kullanmanızı öneririz.

**SharePoint ve OneDrive eski özellikler:**

- [Belge silme ilkeleri](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (yalnızca silme)

- [Yerinde kayıt yönetimini yapılandırma](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (yalnızca saklama)

- [Site kapatma ve silme için ilkeleri kullanma](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (yalnızca silme)

- [Bilgi yönetimi ilkeleri](intro-to-info-mgmt-policies.md) (yalnızca silme)

bir liste veya kitaplık içeriğini korumak için SharePoint siteleri içerik türü ilkeleri veya bilgi yönetimi ilkeleri için yapılandırdıysanız, bekletme ilkesi etkinken bu ilkeler yoksayılır.

## <a name="related-information"></a>İlgili bilgiler

- [SharePoint Online Sınırları](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Microsoft Teams için sınırlar ve belirtimler](/microsoftteams/limits-specifications-teams) 
- [Veri yaşam döngüsü yönetimi ve kayıt yönetimi için mevzuat gereksinimlerini karşılamanıza yardımcı olacak kaynaklar](retention-regulatory-requirements.md)

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bkz. [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md). Bu makalede abonelikler, izinler ve bekletme senaryoları için uçtan uca yapılandırma kılavuzu bağlantıları hakkında bilgiler yer alır.
