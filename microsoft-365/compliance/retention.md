---
title: Etiketleri otomatik olarak korumak veya & için saklama ilkeleri hakkında bilgi edinmek için
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
description: Size gerekenleri korumanıza ve neye ihtiyacınız olmadığını silmeye yardımcı olan bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: b0d179a412a2e0470db844a7e9b422c8ae89db34
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010147"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Teams'de bekletme ilkeleriyle ilgili iletiler görüyorsanız veya uygulamalarınız içinde bekletme etiketleri hakkında sorularınız varsa, sizin için nasıl yapılandırıldıklarına ilişkin bilgi için IT departmanınıza bakın. Bu arada, aşağıdaki makaleleri yararlı bulabilirsiniz:
> -  [Teams ilkeleri hakkında ileti gönderme](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)
> - [SharePoint veya OneDrive'te dosyalara bekletme OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df)
>
> Bu sayfada yer alan bilgiler, uyumluluk nedenleriyle bekletme ilkeleri ve bekletme etiketleri oluşturabiliyor olan IT yöneticilerine yöneliktir.

Çoğu kuruluşta e-posta, belgeler, anlık iletiler ve çok daha fazlası gibi verileri hacmi ve karmaşıklığı her gün artmaktadır. Bu bilgileri etkili bir şekilde yönetmek veya yönetmek önemlidir çünkü:

- **İçeriği minimum** bir süre boyunca tutmanı gerektiren sektör düzenlemelerine ve iç ilkelere önceden uymak; örneğin, Sarbanes-Oxley Yasası belirli içerik türlerini yedi yıl süreyle tutmanı gerekli olabilir.

- **Artık tutmanız gerekmeyecek** eski içerikleri kalıcı olarak silerek mahkeme nedeniyle veya güvenlik ihlali durumunda risklerinizi düşürebilirsiniz.

- **Kullanıcılarının yalnızca geçerli ve onlara uygun içerikle** çalışmalarını sağlayarak, organizasyon kuruluşlarının bilgileri etkili bir şekilde paylaşmalarına ve daha çevik çalışmasına yardımcı olun.

Yapılandırılan bekletme ayarları bu hedeflere ulaşmanıza yardımcı olabilir. Genellikle içeriğin yönetilmesi için iki eylem gerekir:

| Eylem| Amaç |
|:-----|:-----|
|İçeriği koruma | Kalıcı silmeyi önleme ve eKbulma için kullanılabilir kalma |
|İçeriği silme | Kuruluştan kalıcı olarak içerik silme|

Bu iki bekletme eylemiyle, aşağıdaki sonuçları elde etmek için bekletme ayarlarını yapılandırabilirsiniz:

- Yalnızca koruma: İçeriği sonsuza kadar veya belirli bir süre boyunca tutma.
- Yalnızca silme: belirtilen süre sonunda içeriği kalıcı olarak silin.
- İçeriği koruma ve silme: İçeriği belirtilen süre boyunca tutma ve sonra kalıcı olarak silme.

Bu bekletme ayarları, içeriği uyumluluk nedenleriyle saklamanız gerekirken ek depolama alanı oluşturma ve yapılandırmanın ek yükünü azaltan içerikle birlikte çalışır. Buna ek olarak, bu verileri kopyalamak ve eşitlemek için özelleştirilmiş işlemler uygulamanız da gerekli değildir.

Bekletme ilkelerinin ve bekletme etiketlerinin nasıl çalışması, bunların ne zaman ve nasıl ekli olduğu hakkında daha fazla bilgi edinmek için aşağıdaki bölümleri kullanın. Ancak, bazı yaygın senaryolarda bekletme ayarlarını dağıtmaya hazırsanız, bkz. Bilgi [yönetimiyle çalışmaya başlama](get-started-with-information-governance.md).

## <a name="how-retention-settings-work-with-content-in-place"></a>Bekletme ayarları içerikle nasıl çalışır?

İçeriğin bekletme ayarları atanmışsa, bu içerik özgün konumda kalır. Çoğu zaman, kişiler hiçbir şey değişmiş gibi belgeleri veya postalarıyla çalışmaya devam eder. Ancak, bekletme ilkesinde yer alan içeriği düzenler veya silerse, içeriğin bir kopyası otomatik olarak korunur.
  
- Site SharePoint OneDrive için: Kopya, Koruma Kitaplığı **kitaplığında** korunur.

- Daha Exchange için: Kopya, Kurtarılabilir Öğeler **klasöründe** korunur. 

- İletileri Teams Yammer için: Kopya, Kurtarılabilir Öğeler klasöründe alt klasör olarak **SubstrateHolds** **adlı gizli Exchange** korunur.

> [!NOTE]
> Saklama Kitaplığı sitenin depolama kotasının içinde yer alıyor olduğundan, saklama grupları ve depolama grupları için bekletme ayarlarını kullanırken SharePoint Microsoft 365 gerekebilir.
> 
Bu güvenli konumlar ve korunan içerik çoğu kişi tarafından görülmeyebilir. Çoğu durumda, kişilerin içeriklerinin bekletme ayarlarına tabi olduğunu haberleri bile olmaz.

Bekletme ayarlarının farklı iş yükleri için nasıl çalıştığından daha ayrıntılı bilgi için aşağıdaki makalelere bakın:

- [E-SharePoint ve OneDrive](retention-policies-sharepoint.md)
- [Müşteri için bekletme hakkında bilgi Microsoft Teams](retention-policies-teams.md)
- [Müşteri için bekletme hakkında bilgi Yammer](retention-policies-yammer.md)
- [Müşteri için bekletme hakkında bilgi Exchange](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri

Bekletme ayarlarınızı içeriğe atamak için, bekletme ilkelerini **ve bekletme** **etiketlerini etiket ilkeleriyle kullanın**. Bu yöntemlerden yalnızca birini kullanabilir veya bunları birleştirebilirsiniz.

Bir site veya posta kutusu düzeyindeki içerik için aynı bekletme ayarlarını atamak üzere bir bekletme ilkesi kullanın ve bekletme ayarlarını öğe düzeyinde (klasör, belge, e-posta) atamak için de bekletme etiketi kullanın.

Örneğin, bir SharePoint sitenin tüm belgeleri 5 yıl süreyle tutulacaksa, bir bekletme ilkesiyle bunu yapmak, o sitenin tüm belgelerine aynı bekletme etiketini uygulamaktan daha verimli olur. Bununla birlikte, siteden bazı belgeler 5 yıl süreyle korunur ve diğerleri 10 yıl korunursa, bekletme ilkesi bunu yapmak mümkün olmaz. Bekletme ayarlarını öğe düzeyinde belirtmeniz gerekirken, bekletme etiketlerini kullanın. 

Bekletme ilkelerinden farklı olarak, bekletme etiketlerinden gelen bekletme ayarları, kiracı kiracınız içinde farklı bir konuma taşınırsa içerikle birlikte Microsoft 365 olur. Buna ek olarak, bekletme etiketleri bekletme ilkelerinin destekleme desteklemez özelliklerine sahiptir: 
 
- İçeriğin etiketli olduğu veya bir etkinliğe dayalı olduğu zaman ile içeriğin yaşının veya en son ne zaman değiştirildiğinden itibaren bekletme dönemini başlatma seçenekleri.

- İçeriği [etiketli olarak tanımlamak için](classifier-learn-about.md) eğitilebilir sınıflayıcıları kullanın.

- Belgeleriniz için varsayılan SharePoint uygulama.

- İçeriği [kalıcı olarak silinmeden](./disposition.md)  önce gözden geçirmek için incelemeyi destekle.

- İçeriği etiket ayarlarının [bir parçası](records-management.md#records) olarak [](disposition.md#disposition-of-records)  kayıt olarak işaretle ve bekletme döneminin sonunda içerik silindiğinde her zaman konumlandırmayı doğrula.

### <a name="retention-policies"></a>Bekletme ilkeleri

Bekletme ilkeleri aşağıdaki konumlara uygulanabilir:
- Exchange-posta gönderme
- SharePoint sitesi
- OneDrive hesapları
- Microsoft 365 Grupları
- Skype Kurumsal
- Exchange klasörleri taşıma
- Teams iletilerini gönderme
- Teams sohbetleri geri
- Teams kanal iletilerini gönderme
- Yammer iletilerini gönderme
- Yammer iletilerini gönderme

Birden çok konuma ya da belirli konumlara veya kullanıcılara tek bir ilkeyi çok verimli bir şekilde uygulayabilirsiniz.

Bekletme döneminin başlangıcı için, içeriğin ne zaman oluşturulacaklarını veya yalnızca dosyaların ve içeriğin son değiştirilme zamanlarının SharePoint, OneDrive ve Microsoft 365 Grupları konumlarında destek olaylarını seçebilirsiniz.

Öğeler, bekletme ayarlarını bekletme ilkesinde belirtilen kapsayıcılarından devralır. Bundan sonra ilke içeriği korumak üzere yapılandırıldığında kapsayıcının dışına taşınırsa, öğenin bir kopyası iş yükünün güvenli olduğu konumda korunur. Bununla birlikte, bekletme ayarları yeni konumunun içeriğiyle birlikte seyahat etmez. Bu gerekli olursa, bekletme ilkeleri yerine bekletme etiketlerini kullanın.

### <a name="retention-labels"></a>Bekletme etiketleri

Farklı bekletme ayarları gerektiren farklı türde içerikler için bekletme etiketlerini kullanın. Örneğin:
  
- Minimum bir süre için tutulacak vergi formları. 
    
- Belirli bir yaşa geldiğinde kalıcı olarak silinmesi gereken malzemelere basın. 
    
- Belirli bir süre boyunca korunarak kalıcı olarak silinmesi gereken rekabetçi araştırma. 
    
- Düzenlenemedik veya silinemez şekilde kayıt olarak işaretlenen çalışma serbestlikleri. 
    
Tüm bu durumlarda bekletme etiketleri, öğe düzeyinde yönetim denetimi için bekletme ayarlarını (belge veya e-posta) uygulamanızı sağlar.
  
Bekletme etiketleriyle şunları kullanabilirsiniz:
  
- **Kuruluş veya grupların Outlook**, site, site veya site Web üzerinde Outlook içeriğine el ile bir bekletme OneDrive SharePoint olanak Microsoft 365. Kullanıcılar hangi içerik türüyle çalıştığını çoğunlukla en iyi  bil ki, bunu sınıflandırarak uygun bekletme ayarları uygulanır. 
    
- **İçeriğin belirli koşullarla eşleşmesi**, e-postada veya e-postada paylaşılan bulut ekleri de dahil olması Teams içeriği içerdiğinde, bekletme etiketlerini otomatik olarak uygulama: 
    - Belirli türlerde hassas bilgiler vardır.
    - Bir sorguyla eş alan belirli anahtar sözcükler.
    - Eğitilebilir bir sınıflandırıcı için desen eşleşmeleri.

- **İçeriğin sitelerde ve** posta hesaplarında ve e-posta öğelerinde SharePoint için OneDrive bekletme dönemini başlatma.

- **Çalışanların kuruluştan ayrılması veya sözleşmelerin** sona ermiş olduğu bir olay olduğunda bekletme süresini başlar.

- **SharePoint'ta** ayarlanmış belge kitaplığına, klasöre veya belge kümesine varsayılan bekletme etiketi uygulayabilirsiniz; böylelikle, bu konumda depolanan tüm belgeler varsayılan bekletme etiketini devralabilir.

- **Öğeleri kayıt yönetim stratejinizin** bir parçası olarak [işaretleme](records-management.md) . Bu etiketli içerik geçerli Microsoft 365, mevzuatla ilgili nedenlerle gerekebilecek içerik üzerinde başka kısıtlamalar yerleştirilir. Daha fazla bilgi için bkz [. İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

Duyarlılık etiketlarından [farklı olarak bekletme](sensitivity-labels.md) etiketleri, içerik sitenin dışına taşınırsa Microsoft 365.

#### <a name="classifying-content-without-applying-any-actions"></a>Hiçbir eylem uygulamadan içeriği sınıflendirme

Bekletme etiketlerinin ana amacı içeriği korumak veya silmek olsa da, bekletme etiketlerini hiçbir bekletmeyi veya başka eylemleri açmadan da kullanabilirsiniz. Bu durumda, hiçbir eylem zorlamadan bekletme etiketini yalnızca metin etiketi olarak kullanabilirsiniz.
  
Örneğin, hiçbir eylem göstermeden "Daha sonra gözden geçir" adlı bir bekletme etiketi oluşturabilir ve uygulayabilir, daha sonra bu içeriği bulmak için bu etiketi kullanabilirsiniz.
  
![Yalnızca sınıflandırma için etiket ayarları.](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>DLP ilkesinde bir bekletme etiketini koşul olarak kullanma

Bir bekletme etiketini, bir belge belgesinde veri kaybı önleme (DLP) ilkesinde koşul olarak SharePoint. Örneğin, belirtilen bekletme etiketi uygulanmışsa, belgelerin kuruluş dışında paylaşılmasını önlemek için bir DLP ilkesi yapılandırabilirsiniz.

Daha fazla bilgi için bkz [. DLP ilkesinde bir koşul olarak bekletme etiketi kullanma](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Bunları uygulayan bekletme etiketleri ve ilkeleri

Bekletme etiketlerini yayımlarken, bu etiketler, yöneticilerin  ve kullanıcıların içeriğe uygulayabilecekleri bir bekletme etiketi ilkesine dahil edilirler. Aşağıdaki diyagramda gösterildiği gibi:

1. Tek bir bekletme etiketi, birden çok bekletme etiketi ilkesine dahil olabilir.

2. Bekletme etiketi ilkeleri, bekletme etiketlerini yayımlayacak konumları belirtir. Aynı konum, birden çok bekletme etiketi ilkesine dahil olabilir.

![Bekletme etiketleri konum belirten etiket ilkelerine nasıl eklenebilir?](../media/retention-labels-and-policies.png)

Ayrıca, her biri tek bir bekletme **etiketine sahip bir veya birden** çok otomatik uygulama bekletme etiketi ilkesi oluşturabilirsiniz. Bu ilkeyle, ilkede belirttiğiniz koşullar karşı karşılaştığında otomatik olarak bir bekletme etiketi uygulanır.

#### <a name="retention-label-policies-and-locations"></a>Bekletme etiketi ilkeleri ve konumları

Bekletme etiketleri, bekletme etiketinin ne yaptığına bağlı olarak farklı konumlarda yayımlanır.
  
| Bekletme etiketi aşağıdaki gibi ise... | Daha sonra etiket ilkesi şu ilkeye uygulanabilir: |
|:-----|:-----|
|Yöneticilere ve son kullanıcılara yayımlanır  |Exchange, SharePoint, OneDrive, Microsoft 365 Grupları  |
|Hassas bilgi türlerine veya eğitilebilir sınıflayıcılara göre otomatik olarak uygulanır  |Exchange, SharePoint, OneDrive  |
|Anahtar sözcüklere veya bir sorguya dayalı otomatik uygulama  |Exchange, SharePoint, OneDrive, Microsoft 365 Grupları  |
|Bulut eklere otomatik olarak uygulanan  |SharePoint Grupları OneDrive, Microsoft 365'i kullanın  |

Exchange klasörleri, klasörleri, Skype Teams Yammer iletileri bekletme etiketlerini desteklemez. Bu konumlardan içeriği korumak ve silmek için, bunun yerine bekletme ilkelerini kullanın.

#### <a name="only-one-retention-label-at-a-time"></a>Bir defada yalnızca bir bekletme etiketi

E-posta veya belgeye aynı anda yalnızca tek bir bekletme etiketi uygulanmış olabilir. Bekletme etiketi son kullanıcı veya [yönetici](create-apply-retention-labels.md#manually-apply-retention-labels) tarafından el ile veya aşağıdaki yöntemlerden herhangi biri kullanılarak otomatik olarak uygulanabilir:

- [Etiket ilkesi otomatik olarak uygulama](apply-retention-labels-automatically.md)
- [Belge anlama modeli SharePoint Syntex](../contentunderstanding/apply-a-retention-label-to-a-model.md)
- [Etiket veya etiket SharePoint](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) varsayılan [Outlook](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)
- [Outlook kuralları](create-apply-retention-labels.md#automatically-applying-a-retention-label-to-email-by-using-rules)

Standart bekletme etiketleri için (öğeleri kayıt veya mevzuat kaydı [olarak işaretlemezler](records-management.md#records)):

- Yöneticiler ve son kullanıcılar, içeriğe uygulanmış olan mevcut bir bekletme etiketini el ile değiştirebilir veya kaldırabilir. 

- İçerikte zaten bir bekletme etiketi uygulandığında, var olan etiket otomatik olarak kaldırılamaz veya başka bir bekletme etiketiyle değiştirilirken tek bir özel durum vardır: Var olan etiket varsayılan etiket olarak uygulandı. Varsayılan etiket kullanılırken, başka bir varsayılan etiketle değiştir veya otomatik olarak kaldırıldığı bazı senaryolar vardır. 
    
    Varsayılan etiket kullanılarak uygulandığında etiket davranışı hakkında daha fazla bilgi için:
    - Varsayılan etiket SharePoint: [Varsayılan etiket için varsayılan etiket kullanırken SharePoint](create-apply-retention-labels.md#label-behavior-when-you-use-a-default-label-for-sharepoint)
    - Outlook için varsayılan etiket: [Outlook klasörüne varsayılan bekletme etiketi uygulama](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)

- Bekletme etiketi uygulayabilecek birden çok otomatik uygulama etiketi ilkesi varsa ve içerik birden çok ilkenin koşullarına uygunsa, en eski otomatik uygulama etiket ilkesine (oluşturulma tarihine göre) bekletme etiketi uygulanır.

Bekletme etiketleri öğeleri kayıt veya mevzuat kaydı olarak işaretlese bile, bu etiketler hiçbir zaman otomatik olarak değişmez. Yalnızca kapsayıcının yöneticileri öğeleri kayıt olarak işaretleyebilirsiniz, ancak mevzuat kayıtları olarak işaretleyene kadar bekletme etiketlerini el ile değiştirebilir veya kaldırabilir. Daha fazla bilgi için bkz [. İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

#### <a name="monitoring-retention-labels"></a>Bekletme etiketlerini izleme

Kiracı Microsoft 365 uyumluluk merkezi, bekletme etiketlerinizin kiracıda nasıl kullanılıyor olduğunu  izlemek ve etiketli öğelerinizin nerede olduğunu belirlemek için Veri sınıflandırması ve Genel Bakış sayfasını seçin. Önemli önkoşullar da dahil olmak üzere daha fazla bilgi için bkz[. Veri sınıflandırması hakkında bilgi.](data-classification-overview.md)

Ardından, içerik gezginini ve etkinlik [gezginini kullanarak ayrıntılara](data-classification-content-explorer.md) [girebilirsiniz](data-classification-activity-explorer.md).

> [!TIP]
>Eğitim edilebilir sınıflayıcılar ve hassas bilgi türleri gibi diğer veri sınıflandırma içgörülerini, tutmanız veya silmeniz ya da kayıt olarak yönetmeniz gereken içeriği tanımlamanıza yardımcı olması için kullanmayı göz önünde bulundurabilirsiniz.

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Belirli bir bekletme etiketine sahip tüm içeriği bulmak için İçerik Arama'nın kullanımı

Bekletme etiketleri kullanıcılar tarafından veya otomatik olarak uygulanan içeriklere uygulandıktan sonra, belirli bir bekletme etiketinin uygulandığı tüm öğeleri bulmak için içerik arama özelliğini kullanabilirsiniz.

İçerik araması oluşturmak için Bekletme etiketi koşul koşullarını  seçin, ardından tam bekletme etiketi adını veya etiket adının bir bölümünü girin ve joker karakter kullanın. Daha fazla bilgi için bkz [. Anahtar Sözcük sorguları ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).
  
![Bekletme etiketi koşulu.](../media/retention-label-condition.png)


## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketlerinin özelliklerini karşılaştırma

Özelliklere bağlı olarak, bekletme ilkesi mi yoksa bekletme etiketi mi kullanıla belirlemek için aşağıdaki tabloyu kullanın.

|Özellik|Bekletme ilkesi |Bekletme etiketi|
|:-----|:-----|:-----|:-----|
|Silebilir, yalnızca koruma veya yalnızca silmeyi koruyabilirsiniz bekletme ayarları |Evet |Evet |
|Desteklenen iş yükleri: <br />- Exchange <br />- SharePoint <br />- OneDrive <br />- Microsoft 365 grupları <br />- Skype Kurumsal <br />- Teams<br />- Yammer|<br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet <br /> Evet | <br /> Evet, ortak klasörler dışında <br /> Evet <br /> Evet <br /> Evet <br /> Hayır <br /> Hayır <br /> Hayır |
|Otomatik olarak uygulanan bekletme | Evet | Evet |
|Koşulları temel alarak uygulanan bekletme <br /> - hassas bilgi türleri, KQL sorguları ve anahtar sözcükler, eğitilebilir sınıflayıcılar, bulut ekleri| Hayır | Evet |
|El ile uygulanan bekletme | Hayır | Evet |
|Son kullanıcı etkileşimi | Hayır | Evet |
|İçerik taşınırsa kalıcı olur | Hayır | Evet, kiracınız Microsoft 365 içinde |
|Öğeyi kayıt olarak bildir| Hayır | Evet |
|Bir olay etiketli veya bir etkinliğe dayalı bekletme dönemini başlatma | Hayır | Evet |
|Disposition review | Hayır| Evet |
|7 yıl boyunca yok olduğunu kanıtı | Hayır |Evet, disposition review veya item is marked a record|
|Yönetici etkinliklerini denetleme| Evet | Evet|
|Bekletme eylemlerini denetleme| Hayır | Evet <sup>\*</sup> |
|Bekletmeye tabi öğeleri belirleme: <br /> - İçerik Arama <br /> - Veri sınıflandırma sayfası, içerik gezgini, etkinlik gezgini | <br /> Hayır <br /> Hayır | <br /> Evet <br /> Evet|

**Dipnot:**

<sup>\*</sup>İçeriği kayıt veya mevzuat kaydı olarak işaretlemeen bekletme etiketleri için, denetleme olayları SharePoint veya OneDrive'daki bir öğenin etiket uygulanması, değişmesi veya kaldırılması ile sınırlıdır. Bekletme etiketlerinin denetim ayrıntıları için bu sayfanın [Bekletme eylemlerini denetleme](#auditing-retention-actions) bölümüne bakın.

### <a name="combining-retention-policies-and-retention-labels"></a>Bekletme ilkelerini ve bekletme etiketlerini birleştirme

Yalnızca bekletme ilkelerini veya yalnızca bekletme etiketlerini kullanma arasında seçim yapmak zorunda değilsiniz. Her iki yöntem de birlikte ve hatta daha kapsamlı bir çözüm için birbirini tamamlayıcı nitelikte kullanılabilir. Örneğin:

1. İçeriği son değiştirildikten beş yıl sonra otomatik olarak silen bir bekletme ilkesi oluşturabilir ve yapılandırmış olursunuz ve bu ilkeyi tüm OneDrive uygulayabilirsiniz.

2. İçeriği sonsuza kadar tutan bir bekletme etiketi oluşturabilir ve yapılandırabilirsiniz ve bunu tüm hesaplarda yayımlay etiketi ilkesine OneDrive gerekir. Bu etiketi, beş yıl sonra değiştirilmezse otomatik silme işleminin dışında tutulacak belirli belgelere nasıl el ile uygulayacaklarını kullanıcılara açıklarsınız.

Bekletme ilkelerinin ve bekletme etiketlerinin birlikte nasıl çalışması ve birleştirilmiş sonuçlarının nasıl belirlenecekleri hakkında daha fazla bilgi için, bekletme ilkeleri ve öncelik alınan ilkeleri açıklayan bir sonraki bölüme bakın.

## <a name="how-long-it-takes-for-retention-settings-to-apply"></a>Bekletme ayarlarının geçerlik süresi

bir bekletme etiketinin otomatik olarak uygulanması için iş yükleri ve etiket ilkeleri için bekletme ilkeleri gönderdiğinizde, bekletme ayarlarının içeriğe uygulanması için 7 gün kadar süre kullanın:

- [Bekletme ilkelerinin yürürlüğe girecekleri süre](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- [Bekletme etiketlerinin etkilisi ne kadar sürer?](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect)

Benzer şekilde, etiketleri yayımlayan uygulamalarda bekletme etiketlerinin görünür olması için 7 gün kadar süre verin:

- [Bekletme etiketleri uygulanabilecek hale geldiğinde](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply)

Genellikle ilkeler etkili olur ve etiketler 7 günden daha hızlı görünür olur. Ancak, bu süreci etkileyecek çok sayıda potansiyel değişken vardır ve en iyisi en çok 7 gün planlamaktır.

## <a name="adaptive-or-static-policy-scopes-for-retention"></a>Bekletme için uyarlanabilir veya statik ilke kapsamları

Bir bekletme ilkesi veya bekletme etiketi ilkesi  oluşturmada, ilkenin kapsamını tanımlamak üzere uyarlanabilir ve statik arasında seçim oluşturmanız gerekir.

- **Uyarlanabilir kapsam** sizin belirttiğiniz bir sorgu kullanır, dolayısıyla üyelik statik değildir ve seçili konumlarda belirttiğiniz öznitelikler veya özelliklerle günlük olarak dinamik olarak çalışan bir sorgudur. Tek bir ilkeyle birden çok uyarlanabilir kapsam kullanabilirsiniz.
    
    Örnek: Yöneticiler için OneDrive e-posta ve posta belgelerini saklama süresi standart kullanıcılara göre daha uzun bir bekletme süresi gerektirir. "Executive" Azure AD özniteliği iş unvanını kullanan uyarlanabilir bir kapsam içeren bir bekletme ilkesi oluşturun ve ardından ilke için Exchange e-posta OneDrive hesap konumlarını seçin. Uyarlanabilir kapsam bu değerleri otomatik olarak alır, OneDrive e-posta adreslerini veya URL'leri belirtmenize gerek yoktur. Yeni yöneticiler için bekletme ilkesi yeniden yapılandırılmaya gerek yoktur, çünkü e-posta ve posta için karşılık gelen değerlerine sahip bu OneDrive otomatik olarak seçilir.

- Statik **kapsamlar** sorguları kullanmaz ve belirli bir konumun tüm örneklerine uygulayabilecek şekilde yapılandırmayla sınırlıdır veya bu konum için belirli örneklerde ekleme ve dışlamalar kullanabilir. Bu üç seçim kimi zaman sırasıyla "kuruluş genelinde", "içerir" ve "dışlamalar" olarak adlandırılır.
    
    Örnek: Yöneticiler için OneDrive e-posta ve posta belgelerini saklama süresi standart kullanıcılara göre daha uzun bir bekletme süresi gerektirir. İlkenin e-posta ve hesap konumlarını Exchange statik bir kapsam OneDrive bir bekletme ilkesi oluşturabilirsiniz. Exchange e-posta konumu için yalnızca yöneticilere sahip bir grup tanımlayabilirsiniz, dolayısıyla bekletme ilkesi için bu grubu belirtirsiniz ve ilke oluşturulduğunda ilgili e-posta adresleriyle grup üyeliği alınır. Yeni OneDrive konumu için her bir yönetici için tek tek URL'leri OneDrive tanımlamanız ve belirtmeniz gerekir. Yeni yöneticiler için, yeni e-posta adreslerini ve url'leri eklemek için bekletme OneDrive gerekir. Ayrıca, bir OneDrive UPN'sinde değişiklik olduğu her zaman URL'leri de güncelleştirmeniz gerekir.
    
    OneDrive güvenilir bir şekilde belirtmek için bu URL'leri oldukça zordur, çünkü varsayılan olarak bu URL'ler kullanıcı veritabanına ilk kez OneDrive için oluşturulmaz. Kullanıcının UPN'si değişirse ve sizin de bilmiyor olabileceğiniz upn, URL'si OneDrive değişir.

Uyarlanabilir kapsamları kullanmanın avantajları:

- İlke başına [öğe sayısı üzerinde sınır yoktur](retention-limits.md#maximum-number-of-items-per-policy). Uyarlanabilir ilkeler yine de kiracı sınırlamaları [](retention-limits.md#maximum-number-of-policies-per-tenant) başına en fazla ilke sayısına tabi olsa da, daha esnek yapılandırma sonucunda çok daha az ilke ortaya konur.

- Bekletme gereksinimleriniz için daha güçlü hedefleme. Örneğin, bu amaç için grupları oluşturma ve korumanın yönetim yükünü oluşturmadan var olan Azure AD özniteliklerini kullanarak, kullanıcılara coğrafi konumlarına göre farklı bekletme ayarları atabilirsiniz.

- Sorgu tabanlı üyelik, güvenilir bir şekilde grup üyeliğine veya departmanlar arası iletişimi temel alan dış süreçlere güvenilir bir şekilde yansıtılana kadar iş değişikliklerine karşı güvenilirlik sağlar.

- Tek bir bekletme ilkesi hem sizin hem de Microsoft Teams Yammer için konumlar içerebilir, ancak statik bir kapsam kullanıyorken, bu konumlar kendi bekletme ilkelerini gerektirir.
    
- Yalnızca etkin olmayan posta kutularına belirli bekletme ayarlarını uygulayabilirsiniz. Statik kapsam için bu yapılandırma mümkün değildir, çünkü ilke atandığı sırada, statik kapsamlar etkin olmayan posta kutuları olan alıcıların belirli eklenmesini desteklemez.

Statik kapsamları kullanmanın avantajları:

- bir iş yükü için tüm örneklerin otomatik olarak seçili durumda olması için daha basit yapılandırma.
    
    "içerir" ve "dışlar" söz konusu olursa, belirtmeniz gereken örneklerin sayısı düşükse ve değişmezse, bu seçenek başlangıçta daha basit bir yapılandırma olabilir. Bununla birlikte, bu sayı artya başlıyorsa ve organizasyonda ilkelerinizi yeniden yapılandırmanızı gerektiren sık değişiklikler oluyorsa, uyarlanabilir kapsamları yapılandırmak daha kolay ve bakımları çok daha kolay olabilir.

- Klasör **Skype Kurumsal** **Exchange klasör konumları** uyarlanabilir kapsamları desteklemez. Bu konumlar için statik bir kapsam kullan gerekir. 

Yapılandırma bilgileri için bkz. [Uyarlanabilir kapsamları yapılandırma](retention-settings.md#configuration-information-for-adaptive-scopes).

Kayıtlı bir web projesini izlemek için (kayıt gerektirir), Uyarlanabilir [Kapsamlar'da Deep Dive sayfasını ziyaret edin](https://mipc.eventbuilder.com/event/45703).

> [!IMPORTANT]
> Şu anda, uyarlanabilir kapsamlar bekletme ilkeleri ve [bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Tutma Kilidi'i desteklememektedir](#use-preservation-lock-to-restrict-changes-to-policies).

## <a name="policy-lookup"></a>İlke araması

Yayımlama veya otomatik olarak uygulama Microsoft 365 birçok bekletme etiketi ilkelerinin yanı sıra bu konumlar için birden çok bekletme ilkesi yapılandırabilirsiniz. Belirli kullanıcılara, sitelere ve kullanıcı gruplarına atanan bekletme Microsoft 365 bulmak için, aşağıdaki çözümde Bilgi yönetimi çözümünden  İlke araması Microsoft 365 uyumluluk merkezi:

![Belirli kullanıcılara, sitelere ve site gruplarına atanan bekletme ilkelerini bulmak Microsoft 365 arama ](../media/policy-lookup.png)

Kullanıcının tam e-posta adresini, sitenin tam URL'sini veya bir grup kullanıcı grubu için tam e-Microsoft 365 belirtebilirsiniz.

Siteler seçeneği e-OneDrive içerir. Bir kullanıcının iş hesabının URL'sini belirtme hakkında bilgi OneDrive için bkz. Kuruluşta çalışan tüm [OneDrive URL'lerin listesini elde edin](/onedrive/list-onedrive-urls).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Bekletme ilkeleri veya öncelik gerekenler?

Bekletme etiketlerinden farklı olarak, aynı içeriğe birden çok bekletme ilkesi uygulayabilirsiniz. Her bekletme ilkesi bir bekletme eylemine ve silme eylemine neden olabilir. Buna ek olarak, söz konusu öğe bir bekletme etiketinden de bu eylemlere tabi olabilir.

Bu senaryoda, öğeler bir diğerinde çakışmaya neden olan birden çok bekletme ayarına tabi olduğunda sonucu belirlemek için hangi önceliğe sahip olur?

Sonuç, tek bir bekletme ilkesi veya tek bekletme etiketi kazanır, ancak bir öğenin ne kadar süreyle tutul (varsa) ve bir öğe silindiğinde (varsa) sonucu değildir. Bu iki eylem, bir öğeye uygulanan tüm bekletme ayarlarından bağımsız olarak hesaplanır.

Örneğin, bir öğe yalnızca silme eylemi için yapılandırılmış bir bekletme ilkesine ve alıkoyma ve sonra da silme işlemiyle yapılandırılan başka bir bekletme ilkesine tabi olabilir. Sonuç olarak, bu öğenin tek bir koruma eylemi, ancak iki silme eylemi vardır. Bekletme ve silme eylemlerinin arasında çakışma olabilir ve iki silme eylemi de çakışan bir tarihe sahip olabilir. Bekletme ilkeleri sonucu açıklar.

Yüksek bir düzeyde, bekletmenin her zaman kalıcı silme önceliğe ve en uzun bekletme süresine sahip olacağını garanti olabilirsiniz. Bu iki basit kural her zaman bir öğenin ne kadar süreyle tutulacak olduğuna karar verir.

Bir öğenin kalıcı olarak ne zaman silineceklerini belirleyen birkaç etmen daha vardır ve bu eylem bir bekletme ilkesinden silme eylemine her zaman bir bekletme ilkesinden önce gelir.

Her düzeyin üst düzeyden alta çakışmalar için bir bağ sonu gibi davranarak tek bir öğe için bekletme ve silme sonuçlarını anlamak üzere aşağıdaki akışı kullanın. Sonuç, başka çakışmalar olduğundan birinci düzeye göre belirlenirse, sonraki düzeye ilerlemek zorunda değildir ve bu şekilde devam etmek zorunda değildir.

> [!IMPORTANT]
> Bekletme etiketleri kullanıyorsanız: Aynı öğede birden çok bekletme ayarlarının sonucunu belirleyen ilkeleri uygulamadan önce, hangi bekletme etiketinin uygulandığını biliyor [olun](#only-one-retention-label-at-a-time).

![Bekletme ilkeleri diyagramı.](../media/principles-of-retention.png)

Her ilkeyi daha ayrıntılı açıklamadan önce, bekletme ilkesi veya bekletme etiketinde belirtilen bekletme süresi ile öğenin bekletme süresi arasındaki farkı anlamak önemlidir. Bunun nedeni, varsayılan yapılandırmanın bir öğe oluşturulduğunda bekletme dönemini başlatmak olmasına rağmen, bekletme süresi sonu öğe için sabit olsa da dosyaların, bekletme dönemini dosya en son değiştirildiğinden itibaren başlatması için yapılandırmasını da desteklemesidir. Bu alternatif yapılandırmayla, dosya her değiştirildiğinde bekletme süresinin başlangıcı sıfırlanır ve bu da öğe için bekletme süresinin sonunu uzatır. Bekletme etiketleri, etiketli olduğu bekletme dönemini olayın başında ve başında başlatmayı da destekler.

İlkeleri bir dizi Evet ve Hayır sorusuyla birlikte uygulamak için bekletme akış çizelgesini [de kullanabilirsiniz](retention-flowchart.md).

Dört farklı ilkenin açıklaması:
  
1. **Bekletme, silme işlemini geri kazanır.** İçeriğin saklamayı da istediğiniz bekletme ayarları olduğunda, içerik kalıcı olarak silinmez. Bu ilke, içeriğin uyumluluk nedeniyle korunmasını sağlarken, silme işlemi hala başlat (kullanıcı tarafından başlatılmış veya sistem tarafından başlatılan) ve sonuç olarak da kullanıcıların ana görünümünden içerik kaldırabilirsiniz. Bununla birlikte, kalıcı silme işlemi askıya alınır. İçeriğin nasıl ve nerede tutul olduğu hakkında daha fazla bilgi için, her iş yükü için aşağıdaki bağlantıları kullanın:
    
    - [Bekletme, alan ve SharePoint için OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)
    - [Bekletme, alanla birlikte Microsoft Teams](retention-policies-teams.md#how-retention-works-with-microsoft-teams)
    - [Bekletme, alanla birlikte Yammer](retention-policies-yammer.md#how-retention-works-with-yammer)
    - [Müşteri için bekletme nasıl Exchange](retention-policies-exchange.md#how-retention-works-for-exchange)
    
    Bu birinci ilkeye **örnek:** E-posta iletisi, oluşturduktan üç yıl sonra öğeleri secek şekilde yapılandırılmış Exchange için bir bekletme ilkesine tabi olur ve ayrıca, öğeleri oluşturulduktan beş yıl sonra alıkoyacak şekilde yapılandırılmış bir bekletme etiketine de sahiptir.
    
    E-posta iletisi beş yıl süreyle korunur, çünkü bu bekletme eylemi silinmeye göre öncelikli olur. Bekletme eylemi devam ederken askıya alınan silme eylemi nedeniyle, e-posta iletisi beş yıl sonunda kalıcı olarak silinir.

2. **En uzun bekletme süresi kazanır.** İçerik, içeriği farklı süreler boyunca alıkoyan birden çok bekletme ayarına tabi olursa, içerik öğe için en uzun bekletme döneminin sonuna kadar korunur.
    
    > [!NOTE]
    > Bekletme ilkesinde veya etikette 5 yıllık bir bekletme süresi, bekletme ilkesinde veya etikette 7 yıllık bir bekletme süresi elde etmek mümkündür, çünkü 5 yıllık dönem dosyanın en son ne zaman değiştirildiğinden başlayacak şekilde yapılandırılır ve 7 yıllık süre dosya oluşturulduğunda buradan başlayacak şekilde yapılandırılır.
    
    **Bu ikinci ilkeye örnek**: Pazarlama Belgeleri SharePoint iki bekletme ilkesine tabidir. İlk bekletme ilkesi, tüm sitelerde SharePoint oluşturulduktan sonra beş yıl boyunca alıkoyacak şekilde yapılandırılır. İkinci bekletme ilkesi, belirli sitelere SharePoint, oluşturduktan sonra on yıl boyunca öğeleri alıkoyacak şekilde yapılandırılır.
    
    Bu Pazarlama Pazarlama SharePoint sitenin belgeleri on yıl süreyle korunur, çünkü bu öğe için en uzun bekletme süresidir.

3. **Belirtik, silmeler için örtülü olarak kazanır.** Artık bekletme çakışmaları çözüldü, yalnızca silme çakışmaları kalır: 
    
    1. Bekletme ayarları kapsayıcıdan örtülü olarak değil de tek bir öğeye uygulandığından, bekletme ilkeleriyle karşılaştırmalı olarak, açık bir bekletme etiketi sağlar. Bu, bekletme etiketinden silme eyleminin her zaman herhangi bir bekletme ilkesinden silme eylemine göre öncelikli olduğu anlamına gelir.
        
        **Bu** üçüncü ilke (etiket) örneği: Belge, sırasıyla beş yıl ve on yıllık silme eylemine sahip iki bekletme ilkesine, ayrıca yedi yıllık silme eylemine sahip bir bekletme etiketine tabidir.
        
        Bekletme etiketinden silme eylemi öncelikli olduğundan, belge yedi yıl sonra kalıcı olarak silinir.
    
    2. Yalnızca bekletme ilkeleriniz olduğunda: Bir konumun bekletme ilkesi uyarlanabilir kapsam veya belirli örnekleri (örneğin Exchange e-postası için belirli kullanıcıları) içeren statik bir kapsam kullanıyorsa, bu bekletme ilkesi aynı konum için tüm örneklerde yapılandırılmış statik kapsamdan öncelikli olur.
        
        Bir konumun tüm örnekleri için yapılandırılmış statik kapsam bazen "kuruluş çapında bir ilke" olarak da adlandırılır. Örneğin, **Exchange postayı** ve Tüm alıcılar'ın **varsayılan ayarını seçin**. Ayrıca, **SharePoint ve** Tüm siteler varsayılan ayarını **da değiştirebilirsiniz**. Bekletme ilkeleri kuruluş genelinde değil de uyarlanabilir bir kapsam veya belirli örnekleri içeren statik kapsam ile yapılandırıldığında, bu düzeyde eşit öncelikleri vardır.
        
        **Bu üçüncü ilke (ilkeler) için örnek 1**: E-posta iletisi iki bekletme ilkesine tabidir. İlk bekletme ilkesi, on yıl sonra incelenir ve öğeleri siler. İkinci bekletme ilkesi, belirli posta kutularının kapsamındadır ve beş yıl sonra öğeleri siler.
        
        Kapsamlı bekletme ilkesinden silme eylemi kuruluş genelindeki bekletme ilkesine göre öncelikli olduğundan, e-posta iletisi beş yıl sonra kalıcı olarak silinir.
        
        **Örnek 2. ilke (ilkeler)**: Bir kullanıcının hesaplarında yer alan OneDrive iki bekletme ilkesine tabidir. İlk bekletme ilkesi, bu kullanıcının kullanıcı hesabını içerecek şekilde OneDrive ve 10 yılın ardından silme eylemine sahiptir. İkinci bekletme ilkesi, bu kullanıcının kullanıcı hesabını içerecek şekilde OneDrive ve yedi yıl sonra silme eylemine sahiptir.
        
        Her iki bekletme ilkesi de belirli örnekleri içerecek şekilde kapsamında olduğundan, bu belge kalıcı olarak silindiğinde bu düzeyde belirlenemez.

4. **En kısa silme dönemi kazanır.** Öğelerin bekletme ilkelerinden ne zaman silineceklerini ve sonucun önceki düzeyden ne zaman çözümlenemediklerini belirlemek için geçerlidir: İçerik, öğe için en kısa bekletme döneminin sonunda kalıcı olarak silinir.
    
    > [!NOTE]
    > Bekletme süresi 7 yıl olan bir bekletme ilkesi 5 yıllık bir bekletme ilkesinden sonra elde edilmiş olabilir, çünkü ilk ilke dosyanın ne zaman oluşturulduğunda buna göre bekletme dönemini, ikinci bekletme ilkesi de dosya en son değiştirildiğinden başlayacak şekilde yapılandırılır.
    
    **Bu dördüncü ilkeye örnek**: Kullanıcının hesaplarında yer alan bir OneDrive iki bekletme ilkesine tabidir. İlk bekletme ilkesi, bu kullanıcının OneDrive içerir ve dosya oluşturulduktan sonra 10 yıllık bir silme eylemi içerir. İkinci bekletme ilkesi, bu kullanıcının OneDrive içerir ve dosya oluşturulduktan sonra yedi yıl süreyle silme eylemine sahiptir.
    
    Bu belge yedi yıl sonra kalıcı olarak silinecek, çünkü bu iki kapsamda bekletme ilkelerinden bir öğe için en kısa bekletme süresidir.

eBulma saklamaya tabi olan öğeler de ilk bekletme ilkesine sahiptir; hiçbir bekletme ilkesi veya bekletme etiketi tarafından kalıcı olarak silinemez. Bu saklama ilkeleri serbest bırakıca, bekletme ilkeleri bu ilkelere uygulanmalıdır. Örneğin, bundan sonra bunlar eldeki bir bekletme süresine veya silme eylemine tabi olabilir.

### <a name="principles-of-retention-examples-that-combine-retain-and-delete-actions"></a>Bekletme ve silme eylemlerini birleştiren bekletme örneklerinin ilkeleri

Aşağıdaki örnekler, farklı koruma ve silme eylemleri bir araya geldiğinde bekletme ilkelerini göstermek için daha karmaşıktır. Örneklerin takip kolay olması için, tüm bekletme ilkeleri ve etiketler, öğe oluşturulduğunda bekletme dönemini başlatmaya yönelik varsayılan ayarı kullanır; böylelikle bekletme döneminin sonu öğe için de aynı olur.

1. Bir öğeye aşağıdaki bekletme ayarları uygulanmıştır:
    
    - Beş yıl sonra yalnızca silme için bekletme ilkesi
    - Üç yıl süreyle tutulan ve sonra silinen bir bekletme ilkesi
    - Yalnızca yedi yıl süreyle tutulan bir bekletme etiketi
    
    **Sonuç**: Bekletme, silinmeden önceliğe sahip olduğundan ve öğe için en uzun bekletme süresi yedi yıl olduğundan, öğe yedi yıl boyunca korunur. Bu bekletme döneminin sonunda, bekletme ilkelerinden silme eylemi nedeniyle öğe kalıcı olarak silinir.
    
    İki bekletme ilkesi silme eylemleri için farklı tarihlere sahip olsa da, kalıcı olarak silinebilir en erken öğe, her iki silme döneminden daha uzun olan en uzun bekletme döneminin sonunda olur. 

2.  Bir öğeye aşağıdaki bekletme ayarları uygulanmıştır:
    
    - Kuruluş genelinde yalnızca on yıl sonra silmeyi ilke edinen bir bekletme ilkesi
    - Beş yıl süreyle alıkoyan ve sonra s olan belirli örneklerle kapsamı olan bir bekletme ilkesi
    - Üç yıl süreyle tutulan ve sonra silinen bir bekletme etiketi
    
    **Sonuç**: Öğenin en uzun bekletme süresi olduğu için öğe beş yıl boyunca korunur. Bekletme döneminin sonunda, bekletme etiketinden üç yıllık silme eylemi nedeniyle öğe kalıcı olarak silinir. Bekletme etiketlerinden silme, tüm bekletme ilkelerinden silinmeye göre önceliklidir. Bu örnekte, tüm çakışmalar üçüncü düzey tarafından çözülür.

## <a name="use-preservation-lock-to-restrict-changes-to-policies"></a>İlkelerde yapılan değişiklikleri kısıtlamak için Saklama Kilidi'ne

Bazı kuruluşların, Menkul Değer ve Exchange Komisyonu (SEC) Kuralı 17a-4 gibi yasal düzenlemeler tarafından tanımlanan kurallara uyması gerekir. Bu kurallara uyması için bekletme ilkesi açık olduktan sonra bu ilkenin kapatılamayacak veya daha az kısıtlayıcı hale olabileceği gerekir. 

Yasal Koruma Kilidi, bir bekletme ilkesi veya bekletme etiketi politikasını kilitler ve dolayısıyla kimsenin (yönetici dahil) ilkeyi kapatması, ilkeyi silemez veya daha az kısıtlayıcı hale konuy açması için bu tür yasal düzenleme gereksinimlerini karşılamalarını sağlar.
  
Bekletme ilkesi veya bekletme etiketi ilkesi oluşturulduktan sonra Saklama Kilidi'ne uygulanır. Daha fazla bilgi ve yönergeler için bkz [. Bekletme ilkeleri ve bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Saklama Kilidi'i kullanma](retention-preservation-lock.md).

## <a name="releasing-a-policy-for-retention"></a>Bekletme ilkesi bırakma

Bekletme ilkelerinizin Saklama Kilidi yoktur; ilkelerinizi istediğiniz zaman silebilirsiniz; bu da bekletme ilkesi için bekletme ayarlarını etkili bir şekilde kapatamaz ve bekletme etiketleri artık bekletme etiketi ilkelerinden uygulanamaz. Önceden uygulanmış olan tüm bekletme etiketleri yapılandırılmış bekletme ayarlarıyla kalır ve bu etiketler için, öğelerin ne zaman etiketli olduğunu temel alarak bekletme dönemini yine güncelleştirebilirsiniz.

Ayrıca bir ilkeyi saklayabilirsiniz, ancak konum durumunu kapalı olarak değiştirebilir veya ilkeyi devre dışı abilirsiniz. Bir diğer seçenek de ilkeyi yeniden yapılandırarak artık belirli kullanıcıları, siteleri, grupları, diğer siteleri ve diğer özellikleri kapsar. 

Belirli konumlar için ek bilgiler:

- **SharePoint ve hesap OneDrive seçin:**
    
    SharePoint siteleri ve OneDrive hesapları için bir bekletme ilkesi bıraksanız bile, yanlışlıkla veri kaybını önlemek için ilkeden bekletmeye tabi olan tüm içerik 30 gün boyunca korunur. Bu 30 günlük yetkisiz kullanım süresi boyunca silinen dosyalar korunur (dosyalar Saklama kitaplığına eklenmeye devam eder), ancak Bu dosyalar için Düzenli Saklama kitaplığını düzenli aralıklarla temiz alan zamanlayıcı işi bu dosyalar için askıya alınır ve böylelikle gerekirse bunları geri yükleyebilirsiniz.
    
    Bu 30 günlük yetkisiz kullanım süresi için bir özel durum, ilkeyi SharePoint'de bir veya daha fazla siteyi veya OneDrive hesaplarını dışarıda tutmak için güncelleştirmenizdir; bu durumda, Süreölçer işi Koruma Kitaplığı'nın bu konumlara yönelik dosyalarını 30 günlük gecikme olmadan siler.
    
    Saklama Kitaplığı hakkında daha fazla bilgi için bkz. Koruma Kitaplığı [kitaplığında bekletme SharePoint nasıl OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).
    
    yetkisiz kullanım süresi boyuncaki davranış nedeniyle, 30 gün içinde ilkeyi yeniden etkinleştirir veya konum durumunu yeniden etkin hale gelirseniz, ilke bu süre boyunca kalıcı bir veri kaybı olmaksızın sürdürebilirsiniz.

- **Exchange-postayı ve grup Microsoft 365 gönderme**
    
    İlkenin yayım tarihi geldiğinde etkin olmayan posta [kutuları için](inactive-mailboxes-in-office-365.md) bir bekletme ilkesi yayımlarken:
    
    - Bekletme ilkesi açıkça posta kutusuna uygulanmışsa, bekletme ayarları artık geçerli olmaz. Hiçbir bekletme ayarı uygulanmazsa, etkin olmayan posta kutuları her zamanki gibi otomatik silme için uygun hale gelir.
        
        Açık bir bekletme ilkesi için uyarlanabilir bir ilke kapsamı veya ilke uygulandığı sırada etkin bir posta kutusunu belirttiğiniz ve daha sonra devre dışı hale gelen bir yapılandırma içeren statik ilke kapsamı gerekir
    
    - Bekletme ilkesi bir posta kutusuna örtülü olarak uygulanmışsa ve yapılandırılan bekletme eylemi korumaksa, bekletme ilkesi uygulanmaya devam eder ve etkin olmayan posta kutuları hiçbir zaman otomatik silme için uygun hale gelir. Bekletme süresinin süresi sona erdiğinde bekletme eylemi artık geçerli olmadığı durumda, Exchange yönetici artık etkin olmayan posta kutusunu el [ile silebilir](delete-an-inactive-mailbox.md)
        
        Örtülü bir bekletme ilkesi, Tüm **alıcılar (** e-posta için) veya Tüm **gruplar (Exchange** Grupları için) yapılandırmasına sahip statik bir ilke Microsoft 365 gerektirir.
    
    Bekletme ilkeleri uygulanmış etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. [Etkin olmayan posta kutuları ve bekletmeyi Microsoft 365.](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-microsoft-365-retention)

## <a name="auditing-retention-configuration-and-actions"></a>Bekletme yapılandırmasını ve eylemlerini denetleme

Denetim [etkinleştirildiğinde](turn-audit-log-search-on-or-off.md), bekletme için denetim olayları hem yönetim yapılandırmasında (bekletme ilkeleri ve bekletme etiketleri) hem de bekletme eylemlerini (yalnızca bekletme etiketleri) destekler.

### <a name="auditing-retention-configuration"></a>Bekletme yapılandırmasını denetleme

Bekletme ilkeleri ve bekletme etiketleri için yönetici yapılandırması, bir bekletme ilkesi veya etiket oluşturulduğunda, yeniden yapılandırıldıktan veya silindiğinde denetim olayları olarak günlüğe kaydedilir.

Denetim olaylarının tam listesi için bkz. [Bekletme ilkesi ve bekletme etiketi etkinlikleri](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="auditing-retention-actions"></a>Bekletme eylemlerini denetleme

Denetim olayları olarak kaydedilen bekletme eylemleri yalnızca bekletme etiketleri için kullanılabilir; bekletme ilkeleri için kullanılamaz:

- Bir bekletme etiketi şirket içinde veya başka bir satırda bir öğeye uygulandığında, SharePoint veya OneDrive:
    - Dosya **ve sayfa etkinliklerinden, bir** dosya **için Değiştirilmiş bekletme etiketi'ne tıklayın** 

- E-postada etiketli SharePoint bir kayıt olarak işaretlenir ve öğenin kilidi açılır veya kullanıcı tarafından kilitlenir:
    - Dosya **ve sayfa etkinliklerinden,** Kayıt **durumu kilidi açık olarak değiştirildi ve Kayıt** durumu **kilitli olarak değiştirildi'yi seçin**

- İçeriği kayıt veya mevzuat kaydı olarak işaret alan bir bekletme etiketi kayıt veya yasal düzenlemelere uygun olarak Exchange:
    - Posta **Exchange etkinlikleri için, İleti** **kayıt olarak etiketlenmiş'i seçin**

- SharePoint, OneDrive veya Exchange etiketli bir öğe kayıt veya mevzuat kaydı olarak işaretlenir ve kalıcı olarak silinir:
    - Dosya **ve sayfa etkinliklerinden,** Kayıt **olarak işaretlenmiş dosya silindi'yi seçin**

- Disposition reviewer takes action for an item that's reach the end of its retention period:
    -  **Disposition review activities from**, **select Approved disposal**, **Extended retention period**, **Relabeled item**, or **Added reviewers**

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri için PowerShell cmdlet'leri

Bekletme cmdlet'lerini kullanmak için, önce [Office 365 Güvenlik ve Uyumluluk & PowerShell'e bağlanmanız gerekir](/powershell/exchange/connect-to-scc-powershell). Ardından aşağıdaki cmdlet'lerden herhangi birini kullanın:

- [Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)

- [Yeni-ComplianceTag](/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag)

- [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](/powershell/module/exchange/get-compliancetagstorage)

- [Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig)

- [Get-retentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-retentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/set-recordreviewnotificationtemplateconfig)

- [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-retentionComplianceRule](/powershell/module/exchange/get-retentioncompliancerule)

- [New-retentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-retentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule)


## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Bekletme ilkeleri ve bekletme etiketleri veya eBulma bekletmeleri ne zaman kullanılır?

[eBulma durumuyla](create-ediscovery-holds.md) birlikte bir bekletme ayarları ve bekletmeleri, verilerin kalıcı olarak silinmesini de önlese de, bunlar farklı senaryolar için tasarlanmıştır. Farklılıkları anlamanıza ve hangisinin kullanılamayacaklarını anlamanıza yardımcı olmak için aşağıdaki kılavuzu kullanın:

- Bekletme ilkeleri ve bekletme etiketlarında belirttiğiniz bekletme ayarları, uyumluluk gereksinimlerine yönelik verileri tutmak veya silmek için uzun vadeli bilgi yönetim stratejisine yönelik tasarlanmıştır. Kapsam genelde geniştir ve odak, tek tek kullanıcılar yerine konum ve içerikte olur. Bekletme döneminin başlangıcı ve sonu yapılandırılabilir ve ek yönetici müdahalesi olmadan içeriği otomatik olarak silme seçeneği kullanılır.

- eBulma için 10.01.011.2007 tarihine kadar (Çekirdek eKbulma veya Advanced eDiscovery servisleri) yasal soruşturma verilerini korumak üzere sınırlı bir süre için tasarlanmıştır. Kapsam, odağın tanımlanan kullanıcıların sahip olduğu içeriğe özeldir. Saklama döneminin başlangıç ve bitişi yapılandırılabilir değildir, ancak ayrı ayrı yönetici eylemlerine bağımlıdır ve saklama süresi yayın olduğunda içeriği otomatik olarak silme seçeneği olmadan yapılır.

Bekletmelerle bekletmeleri karşılaştırmak için özet:

|Dikkate Alınacak Nokta|Bekletme |eKbulma 1|
|:-----|:-----|:-----|:-----|
|İşle ilgili gerekenler: |Uyumluluk |Yasal |
|Zaman kapsamı: |Uzun vadeli |Kısa vadeli |
|Odak: |Geniş, içerik tabanlı |Belirli, kullanıcı tabanlı |
|Yapılandırılabilir başlangıç ve bitiş tarihi: |Evet |Hayır |
|İçerik silme: |Evet (isteğe bağlı) |Hayır |
|Yönetimsel masraflar: |Düşük |Yüksek |

İçerik hem bekletme ayarlarına hem de eBulma saklama durumuna tabi olursa, eBulma saklama içeriğinin korunması her zaman öncelikli olur. Bu şekilde, [bekletme ilkeleri](#the-principles-of-retention-or-what-takes-precedence) eBulma bekletmesi'ne genişletilir çünkü yöneticiler saklamayı el ile serbest bırakıncaya kadar verileri korurlar. Bununla birlikte, bu önceliğe rağmen, uzun vadeli bilgi idaresi için eKbulma 100'leri kullanmaz. Verilerin otomatik silinmesi konusunda endişeleriniz varsa, bekletme ayarlarını öğeleri sonsuza kadar alıkoyacak şekilde yapılandırabilirsiniz veya bekletme etiketleriyle [incelemeyi](disposition.md#disposition-reviews) kullanabilirsiniz.

Verileri korumak için eski eBulma araçlarını kullanıyorsanız, aşağıdaki kaynaklara bakın:

- Exchange: 
    - [Yerinde Tutma ve Mahkeme Tutma](/exchange/security-and-compliance/in-place-and-litigation-holds)
    - [Exchange Online posta kutusuna yerleştirilen tutma Exchange Online tanımlama](./identify-a-hold-on-an-exchange-online-mailbox.md)

- SharePoint ve OneDrive: 
    - [eBulma Merkezi'nde vakaya içerik ekleme ve kaynakları yerinde yerinde tutma](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Eski eBulma araçlarının emeklilik](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Eski özellikler yerine bekletme ilkelerini ve bekletme etiketlerini kullanma

Bilgi yönetimi için Microsoft 365'de içeriği önceden korumalı veya silmeniz gerekirse, aşağıdaki eski özellikler yerine bekletme ilkelerini ve bekletme etiketlerini kullanmalarını öneririz.

Şu anda bu eski özellikleri kullanıyorsanız, bunlar sizin bekletme ilkeleri ve bekletme etiketleriyle Microsoft 365 birlikte çalışmaya devam eder. Bununla birlikte, bundan sonra, Microsoft 365 iş yüklerinde içeriğin hem bekletme hem de silinmesini yönetmek için tek bir çözümden yararlanmak üzere Microsoft 365.

**Bu özelliğin eski Exchange Online:**

- [İleti kayıtları yönetimi (](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)[MRM) olarak da bilinen bekletme etiketleri ve bekletme ilkeleri (](/exchange/security-and-compliance/messaging-records-management/messaging-records-management)yalnızca silme)
    
    Bununla birlikte, aşağıdaki MRM özelliklerini kullanıyorsanız, bunların şu anda bazı bekletme ilkeleri tarafından destek Microsoft 365 gerekir:
    
    - Belirtilen süre sonrasında [kullanıcının birincil posta kutusundan](enable-archive-mailboxes.md) gelen e-postaları otomatik olarak arşiv posta kutusuna taşımak için arşiv posta kutularına arşiv ilkesi. Arşiv ilkesi (tüm ayarlarla) kullanıcının birincil Microsoft 365 arşiv posta kutusu için geçerli olan bir bekletme ilkesiyle birlikte kullanılabilir.
    
    - Yönetici tarafından posta kutusunun içindeki belirli klasörlere uygulanan bekletme ilkeleri. Önemli Microsoft 365 bekletme ilkesi, posta kutusunun tüm klasörleri için geçerlidir. Öte yandan yönetici, bir kullanıcının Outlook'daki klasörlere varsayılan bekletme etiketi olarak uygulayabilecek bekletme etiketlerini kullanarak farklı bekletme [ayarlarını yapılandırabilirsiniz](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder).

- [Mahkeme tutma](create-a-litigation-hold.md) (yalnızca bekletme)
    
   Mahkeme bekletmeleri hala desteklese de, uygun bir şekilde Microsoft 365 bekletmeleri veya eKbulma bekletmeleri [kullanmalarını öneririz](#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds). 

**Yeni ve farklı SharePoint eski OneDrive:**

- [Belge silme ilkeleri](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (yalnızca silme)
    
- [Yerinde kayıt yönetimini yapılandırma](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (yalnızca bekletme) 
    
- [Site kapatma ve silme ilkeleri kullanma](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (yalnızca silme)
    
- [Bilgi yönetimi ilkeleri](intro-to-info-mgmt-policies.md) (yalnızca silme)
     
Liste veya kitaplığın içeriğini SharePoint için içerik türü ilkeleri veya bilgi yönetimi ilkeleri için yapılandırılmışsa, bekletme ilkesi devam ederken bu ilkeler yoksayılır. 

## <a name="related-information"></a>İlgili bilgiler

- [SharePoint Online Sınırları](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Teknik özellikler için sınırlar ve Microsoft Teams](/microsoftteams/limits-specifications-teams) 
- [Bilgi yönetimi ve kayıt yönetimiyle ilgili mevzuat gereksinimlerini karşılamanıza yardımcı olacak kaynaklar](retention-regulatory-requirements.md)

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bkz [. Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md). Bu makalede abonelikler, izinler ve bekletme senaryoları için  uç  uç yapılandırma kılavuzuna bağlantılar hakkında bilgiler vardır.
