---
title: E-SharePoint ve OneDrive
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
search.appverid:
- MOE150
- MET150
description: Bekletmenin, e-SharePoint için nasıl çalıştığını OneDrive.
ms.openlocfilehash: a553945fdb0b0034d8f3182164749b06badfe503
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014336"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>E-SharePoint ve OneDrive

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bu makaledeki bilgiler [Bekletme hakkında bilgi](retention.md) edin'e ek bilgiler içerir, çünkü bekletme ve saklama SharePoint OneDrive.

Diğer iş yükleri için bkz:

- [Müşteri için bekletme hakkında bilgi Microsoft Teams](retention-policies-teams.md)
- [Müşteri için bekletme hakkında bilgi Yammer](retention-policies-yammer.md)
- [Müşteri için bekletme hakkında bilgi Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Bekletme ve silme işlemi için neler dahildir?

Site içinde veya SharePoint OneDrive tüm dosyalar, bir bekletme ilkesi veya bekletme etiketi uygulanarak saklanabilir. 

Aşağıdaki dosyalar silinebilir:

- Bekletme ilkesi kullanırken: Belge kitaplıklarında yer alan ve otomatik olarak oluşturulan tüm dosyaları içeren SharePoint Varlıkları gibi belge **kitaplıklarında yer alan tüm dosyalar**.
    
- Bekletme etiketlerini kullanırsanız: Tüm belge kitaplıklarında yer alan tüm dosyalar ve kök düzeyindeki tüm dosyalar bir klasörde yer olmayanlardır.
    
> [!TIP]
> Bekletme etiketi için [otomatik uygulama ilkesi olan bir](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties) sorgu kullanırken, aşağıdaki girdiyi kullanarak belirli belge kitaplıklarını dışarıda tutabilirsiniz: `NOT(DocumentLink:"<URL to document library>")`

Liste öğeleri bekletme ilkeleri tarafından desteklanmaz, ancak sistem listelerinde yer alan öğeler dışında, bekletme etiketleri tarafından de destekler. Bunlar, Sistem Yöneticisi SharePoint tarafından kullanılan gizli listelerdir ve bunlar ana sayfa kataloğunu, çözüm kataloğunu ve veri kaynaklarını içerir. Desteklenen liste öğelerine bekletme etiketleri uygulandığında, bunlar her zaman bekletme ayarlarına göre korunur, ancak aramadan gizlendiğinde silinmezler.

Belge eki olan desteklenen bir liste öğesine bekletme etiketi uygulayabilirsiniz:
- Standart bir bekletme etiketi için (öğeyi kayıt olarak bildirmz):
    - Belge eki, etiketin bekletme ayarlarını otomatik olarak devralmaz, ancak bağımsız olarak etiketılabilir.
- Öğeyi kayıt olarak bildiren bir bekletme etiketi için: 
    - Belge zaten etiketli değilse, belge eki bekletme ayarlarını etiketten otomatik olarak devralıyor.

Hem bekletme ilkelerinden hem de bekletme etiketlerinden gelen bekletme ayarları kitaplık, liste ve klasör içeren yapıları düzenlemek için geçerli değildir.

Bekletme ilkeleri ve etiket ilkelerinin otomatik olarak uygulanması için: SharePoint ayarlarının uygulansı için sitelerde dizine alınan siteler olmalıdır. Öte yandan, belge SharePoint öğeleri arama sonuçlarında görünmeyecek şekilde yapılandırılırsa, bu yapılandırma dosyaları bekletme ayarlarının dışında tutmaz.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Bekletme, alan ve SharePoint için OneDrive

Korunması gereken içeriği depolamak için, site SharePoint OneDrive yerinde saklama kitaplığı yoksa bir Saklama Kitaplığı oluşturun. Yasal Saklama kitaplığı etkileşimli olarak kullanılmaya tasarlanmamıştır, ancak uyumluluk nedenlerinden dolayı gerektiğinde dosyaları otomatik olarak depolar. Aşağıdaki şekilde çalışır:

Kullanıcı bekletmeye tabi olan bir öğeyi değiştirse veya silebilirse, bekletme ayarları uygulandığından bu yana içeriğin değişip değişmediğini denetleme yapılır. Bu, bekletme ayarları uygulandığından bu yana yapılan ilk değişiklikse, içerik Saklama kitaplığına kopyalanır ve bu da kullanıcının özgün içeriği değiştirmesini veya silmesini sağlar.

Bir zamanlayıcı işi düzenli olarak Saklama kitaplığında çalışır. Bu iş, Saklama Saklama kitaplığında 30'dan fazla gündür kullanılan içerikle, bu içerik için bekletme ayarları tarafından kullanılan tüm sorgularla içeriği karşılaştırıldığında. Yapılandırılmış bekletme süresinden daha eski olan içerik, Saklama Saklama kitaplığından ve hala orada ise özgün konumdan silinir. Bu zamanlayıcı işi her yedi günde bir çalışır; bu da en az 30 günde bir, içeriğin Saklama Kitaplığı'dan silinmesinin 37 gün kadar zaman al geril bütün olduğu anlamına gelir.

Saklama kitaplığına dosya kopyalamaya karşı bu davranış, bekletme ayarları uygulandığında var olan içeriğe uygulanır. Buna ek olarak, bekletme ilkeleri için, ilkeye eklendikten sonra sitede oluşturulan veya siteye eklenen tüm yeni içerik, Saklama Saklama kitaplığında korunur. Ancak, yeni içerik Saklama kitaplığı ilk kez düzenlenemez ve ancak silindiğinde kopyalanmaz. Dosyanın tüm sürümlerini korumak için, [özgün](#how-retention-works-with-document-versions) sitede sürümlamanın açık olması gerekir.
  
Kullanıcılar bekletmeye tabi olan bir kitaplığı, listeyi, klasörü veya siteyi silmeyi denerse bir hata iletisi alırlar. Önce bekletmeye tabi olan klasördeki dosyaları taşımaları veya silmeleri durumuyla klasörü silebilirler.

Aşağıdaki durumlardan herhangi biri etiketli öğeyi silebilirlerse, kullanıcılar bir hata iletisi de görebilir. Öğe Saklama kitaplığına kopyalanmaz, ancak özgün konumda kalır:

- Kullanıcıların etiketli öğeleri silmelerini sağlayan kayıt yönetimi ayarı kapalıdır.
    
    Bu ayarı kontrol etmek veya değiştirmek için, Kayıt yönetimi  ayarları sayfasındaki Kayıt yönetimi Microsoft 365 uyumluluk merkezi > >  >  >  Sağlık **etiketleriŞordu etiketleriSiçenekler**. Ayrı ayrı E-SharePoint ayarları OneDrive.
    
    Alternatif olarak, **Kayıt** yönetimi çözümüne erişiminiz yoksa [, Get-PnPTenant ve Set-PnPTenant'tan](/powershell/module/sharepoint-pnp/get-pnptenant) *AllowFilesWithKeepLabelToDeletedSPO* ve [](/powershell/module/sharepoint-pnp/set-pnptenant)*AllowFilesWithKeepLabelToDeletedODB* kullanabilirsiniz.

- Bekletme etiketi öğeleri kayıt olarak işaretler ve [kilitlenir](record-versioning.md).
    
    Yalnızca kaydın kilidi açık olduğunda, son sürümün bir kopyası Saklama Kitaplığı'nın depolaması gerekir.

- Bekletme etiketi öğeleri bir yasal düzenleme [kaydı olarak](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) işaretler ve bu da öğenin her zaman düzenlemesini veya silinmesini sağlar.

Bekletme ayarları bir OneDrive hesabı veya SharePoint sitesinde bulunan içeriğe atandıktan sonra, içeriğin gereken yolları, bekletme ayarlarının alıkoyma ve silme, yalnızca koruma veya yalnızca silme gibi ayarlara bağlı olarak ilerler.

Bekletme ayarları korunarak silinecek olduğunda:

![SharePoint ve OneDrive'de içerik yaşam döngüsünün diyagramı.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **İçerik bekletme süresi boyunca değiştirilir** veya silinirse, Saklama Saklama kitaplığında bekletme ayarları atandığı zaman özgün içeriğin var olduğu gibi bir kopyası oluşturulur. Burada, süreölçer işi, bekletme süresinin sona ermiş olduğu öğeleri tanımlar. Bu öğeler ikinci aşama Geri Dönüşüm Kutusu'na taşınır ve 93 günün sonunda kalıcı olarak silinirler. İkinci aşama Geri Dönüşüm Kutusu son kullanıcılar tarafından görülmeyebilir (yalnızca ilk aşama Geri Dönüşüm Kutusu'dur), ancak site koleksiyonu yöneticileri buradan içeriği  görebilir ve geri yükleyebilir.

    > [!NOTE]
    > Yanlışlıkla veri kaybını önlemeye yardımcı olmak için, artık Saklama Kitaplığı'nın içeriğini kalıcı olarak silmez. Bunun yerine, yalnızca Geri Dönüşüm Kutusu'nun içeriğini kalıcı olarak sildiriz, dolayısıyla Saklama Saklama kitaplığının tüm içeriği artık ikinci aşama Geri Dönüşüm Kutusu'na gidiyor.
    
2. **bekletme süresi boyunca içerik** değiştirilmez veya silinmezse, zamanlayıcı işi bu içeriği bekletme döneminin sonundaki ilk aşama Geri Dönüşüm Kutusu'na taşır. Kullanıcı buradan içeriği silebilir veya bu Geri Dönüşüm Kutusu'nu boşaltmışsa (temizleme olarak da bilinir), belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük bekletme süresi hem ilk hem de ikinci aşama geri dönüşüm alanlarına yayılan bir süredir. 93 günün sonunda, belge ilk aşama veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. Geri Dönüşüm Kutusu dizine alındı ve dolayısıyla arama için kullanılamaz. Sonuç olarak, eBulma araması üzerinde tutulacak herhangi bir Geri Dönüşüm Kutusu içeriğini bulamaz.

> [!NOTE]
> İlk bekletme ilkesi [nedeniyle, aynı](retention.md#the-principles-of-retention-or-what-takes-precedence) öğenin başka bir bekletme ilkesi veya bekletme etiketi nedeniyle korunması gerekirse ya da yasal veya yatırımlı nedenlerle eBulma bekletme kapsamında ise kalıcı silme işlemi her zaman askıya alınır.

Bekletme ayarları yalnızca koruma veya yalnızca silme olduğunda, içerik yolları koruma ve silme çeşitlemeleridir:

### <a name="content-paths-for-retain-only-retention-settings"></a>Yalnızca bekletme ayarları için içerik yolları

1.  İçerik bekletme süresi boyunca değiştirilir veya silinirse: Özgün belgenin bir kopyası, Saklama Saklama kitaplığında oluşturulur ve bekletme süresi sonuna kadar korunur. Saklama Saklama kitaplığının kopyası İkinci Aşama Geri Dönüşüm Kutusu'na taşındığında ve 93 gün sonra kalıcı olarak silinir.

2. **İçerik bekletme süresi boyunca değiştirilmez veya silinmezse** : Bekletme süresi öncesinde ve sonrasında hiçbir şey olmaz; Belge özgün konumda kalır.

### <a name="content-paths-for-delete-only-retention-settings"></a>Yalnızca silme bekletme ayarları için içerik yolları

1. **Yapılandırılmış dönem boyunca içerik** silinirse: Belge ilk aşama Geri Dönüşüm Kutusu'na taşınır. Kullanıcı belgeyi buradan silerse veya Bu Geri Dönüşüm Kutusu'nu boşaltmışsa, belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük bekletme süresi hem ilk aşamayı hem de ikinci aşama geri dönüşüm kutusunu içerir. 93 günün sonunda, belge ilk aşama veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. Yapılandırılmış dönem boyunca içerik değiştirilirse, yapılandırılan süreçten sonra da aynı silme yolu izler.

2. **İçerik, yapılandırılan** süre boyunca silinmezse: Bekletme ilkesinde yapılandırılmış sürenin sonunda, belge ilk aşama Geri Dönüşüm Kutusu'na taşınır. Kullanıcı belgeyi buradan silerse veya Bu Geri Dönüşüm Kutusu'nu boşaltmışsa (temizleme olarak da bilinir), belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük bekletme süresi hem ilk aşamayı hem de ikinci aşama geri dönüşüm kutusunu içerir. 93 günün sonunda, belge ilk aşama veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. Geri Dönüşüm Kutusu dizine alındı ve dolayısıyla arama için kullanılamaz. Sonuç olarak, eBulma araması üzerinde tutulacak herhangi bir Geri Dönüşüm Kutusu içeriğini bulamaz.

## <a name="how-retention-works-with-cloud-attachments"></a>Bekletme bulut ekleriyle nasıl çalışır?

Bulut ekleri, kullanıcıların paylaştığı dosyalara eklenmiş bağlantılardır ve kullanıcılarınız bu dosyaları e-postalarda ve Outlook iletilerde paylaştığında Teams silinebilir. Bulut [ekleri için otomatik](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments) olarak bir bekletme etiketi uygulandığında bekletme etiketi, Saklama Kitaplığı'nın depolandığı paylaşılan dosyanın bir kopyasına uygulanır.

Bu senaryo için, bekletme dönemini başlatması için öğenin ne zaman etiketli olduğunu temel alarak etiket ayarını yapılandırmanizi öneririz. Bekletme dönemini öğenin ne zaman oluşturulduğunda veya en son değiştirildiğinden bağlı olarak yapılandırırsanız, bu tarih paylaşım zamanında özgün dosyadan alınır. Bekletme başlangıcını son değiştirildiğinde yapılacak şekilde yapılandırdısanız, Bu ayar, Saklama Kitaplığı'nın bu kopyası için hiçbir etkisi olmaz.

Bununla birlikte, özgün dosya değiştirilir ve yeniden paylaşılırsa, dosyanın yeni bir sürümü olarak yeni bir kopyası Koruma Saklama kitaplığına kaydedilir ve etiketlenmiş olur.

Özgün dosya yeniden paylaşılır ancak değiştirilmezse, Saklama Kitaplığı'nın kopyanın etiketli tarihi güncelleştirilir. Bu eylem bekletme döneminin başlangıcını sıfırlar ve bekletme döneminin başlangıcını, öğenin etiketli olduğu zaman temel olacak şekilde yapılandırmanız önerilir.

Bekletme etiketi özgün dosyaya uygulanmay olduğundan, etiketli dosya hiçbir zaman kullanıcı tarafından değiştirilmez veya silinmez. Etiketli dosya, süreölçer işi bekletme süresinin sona ermiş olduğunu belirleyene kadar Saklama Saklama kitaplığında kalır. Bekletme ayarları öğeleri secek şekilde yapılandırılmışsa, dosya daha sonra ikinci aşama Geri Dönüşüm Kutusu'na taşınır ve 93 günün sonunda kalıcı olarak silinir:

![SharePoint ve OneDrive'te depolanan bulut ekleri için bekletme OneDrive](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

Saklama kitaplığında depolanan kopya normalde bulut ekin paylaşılıyor olmasıyla bir saat içinde oluşturulur.

## <a name="how-retention-works-with-onenote-content"></a>Bekletme, yeni içerikle OneNote çalışır

OneNote içeriğinin bulunduğu bir konuma ya da OneNote klasörüne bekletme etiketi içeren bir bekletme ilkesi uygulasanız, farklı OneNote sayfaları ve bölümleri bekletme ayarlarını devralan tek tek dosyalardır. Bu, belirttiğiniz bekletme ayarlarına göre sayfa içindeki her bölümün ayrı ayrı tutulacak ve silinecek olması anlamına gelir.

Yalnızca sayfalar ve bölümler belirttiğiniz bekletme ayarlarından etkiler. Örneğin, tek tek her not defteri **için** Değiştirme tarihi görse bile, bu tarih ayrı bir bekletme Microsoft 365 kullanılır.

## <a name="how-retention-works-with-document-versions"></a>Bekletme belge sürümleriyle nasıl çalışır?

Sürüm oluşturma, çalışma kitaplarının ve kitaplarının tüm belge listelerinin ve kitaplıkların SharePoint bir OneDrive. Varsayılan olarak, sürüming bu sınırı artırsa da en az 500 ana sürüm içerir. Daha fazla bilgi için bkz [. Liste veya kitaplık için sürüm oluşturma](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) etkinleştirme ve yapılandırma ve [Listelerde ve kitaplıklarda sürüm oluşturma nasıl çalışır](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247)?
  
Sürümleri olan bir belge bu içeriği korumak için bekletme ayarlarına tabi olduğunda, Saklama Saklama kitaplığına kopyalanan sürümler ayrı bir öğe olarak yer olur. Bekletme ayarları, bekletme döneminin sonunda silinecek şekilde yapılandırılmışsa:

- Bekletme süresi içeriğin oluşturulma tarihini temel alarak oluşturulmuşsa, her sürümün son kullanma tarihi özgün belgeyle aynı olur. Özgün belgenin ve sürümlerinin hepsi aynı anda sona erer.

- Bekletme süresi içeriğin son değiştirilma saatlerine bağlı olarak yapılacaksa, her sürümün, özgün belgenin o sürümü oluşturmak için değiştirilma tarihine bağlı olarak kendi sona erme tarihi vardır. Özgün belge ve sürümleri birbirinden bağımsız olarak sona erer.

Bekletme eylemi belgeyi silmekse, Saklama Kitaplığı'nda yer alan tüm sürümler geçerli sürüme göre aynı anda silinir.

Bekletme ilkesine (veya eBulma bekletmeye) tabi olan öğelerde, belgenin bekletme süresine ulaşana (veya eBulma saklama sürümü yayımlanana) kadar belge kitaplığının sürüm oluşturma sınırları yoksayılır. Bu senaryoda, eski sürümler otomatik olarak temizlanmaz ve kullanıcıların sürümleri silmeden önlenir.

İçerik bir bekletme ilkesine (veya eBulma saklamaya) tabi değilse, bekletme etiketleri böyle olmaz. Bunun yerine, eski sürümlerin yeni sürümlere uyum sağlayacak şekilde otomatik olarak silinmesine, ancak kullanıcıların sürümleri silmeden yine de önüne geçmek için sürüm oluşturma sınırlamaları geçerli olur.

## <a name="when-a-user-leaves-the-organization"></a>Bir kullanıcı kuruluşdan ayrıldığında

**SharePoint**:

Bir kullanıcı kuruluştan ayrıldığında, o kullanıcı tarafından oluşturulan tüm içerik etkilenmez çünkü SharePoint posta kutusu veya posta kutusunun aksine işbirliğine dayalı bir ortam OneDrive kabul edilir.

**OneDrive**:

Bir kullanıcı kuruluştan ayrılırsa, bekletme ilkesine tabi veya bekletme etiketi olan tüm dosyalar, ilkede veya etikette belirtilen bekletme süresi boyunca bekletme ayarlarına tabi kalır. Bu süre boyunca, tüm paylaşım erişimi çalışmaya devam eder ve içerik İçerik Arama ve eBulma tarafından aranabilir hale geldi. 

Bekletme süresi dolduğunda ve bekletme ayarları bir silme eylemi dahil olduğunda, içerik Site Koleksiyonu Geri Dönüşüm Kutusu'na taşınır ve yönetici dışında herkes tarafından erişilemez.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bekletmeyi yeni bir web günlüğünde yapılandırmaya Microsoft 365 [bkz. Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md).

E-posta için bir bekletme ilkesi veya bekletme etiketi yapılandırmaya Exchange, aşağıdaki yönergelere bakın:
- [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)
- [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)