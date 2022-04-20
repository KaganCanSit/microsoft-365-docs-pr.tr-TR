---
title: SharePoint ve OneDrive için bekletme hakkında bilgi edinin
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
description: Bekletmenin SharePoint ve OneDrive için nasıl çalıştığını öğrenin.
ms.openlocfilehash: ed9cc45218dde112baec8fbca997abc6e82b4d72
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911500"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>SharePoint ve OneDrive için bekletme hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Bu makaledeki bilgiler, SharePoint ve OneDrive özgü bilgiler içerdiğinden [Elde tutma hakkında bilgi edinin](retention.md) ekini ekler.

Diğer iş yükleri için bkz:

- [Microsoft Teams için bekletme hakkında bilgi edinin](retention-policies-teams.md)
- [Yammer için bekletme hakkında bilgi edinin](retention-policies-yammer.md)
- [Exchange için bekletme hakkında bilgi edinin](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Saklama ve silmeye dahil olanlar

SharePoint veya OneDrive sitelerinde depolanan tüm dosyalar bir bekletme ilkesi veya bekletme etiketi uygulanarak saklanabilir. 

Aşağıdaki dosyalar silinebilir:

- Bekletme ilkesi kullandığınızda: Site Varlıkları gibi otomatik olarak oluşturulan SharePoint belge kitaplıklarını içeren belge **kitaplıklarındaki** tüm dosyalar.
    
- Bekletme etiketlerini kullandığınızda: Tüm belge kitaplıklarındaki tüm dosyalar ve bir klasörde olmayan kök düzeydeki tüm dosyalar.
    
> [!TIP]
> [Bekletme etiketi için otomatik uygulama ilkesi olan bir sorgu](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties) kullandığınızda, aşağıdaki girdiyi kullanarak belirli belge kitaplıklarını dışlayabilirsiniz:`NOT(DocumentLink:"<URL to document library>")`

Liste öğeleri bekletme ilkeleri tarafından desteklenmez, ancak sistem listelerindeki öğeler dışında bekletme etiketleri tarafından desteklenir. Bunlar, SharePoint tarafından sistemi yönetmek için kullanılan ve ana sayfa kataloğunu, çözüm kataloğunu ve veri kaynaklarını içeren gizli listelerdir. Bekletme etiketleri desteklenen liste öğelerine uygulandığında, bunlar her zaman bekletme ayarlarına göre korunur, ancak aramadan gizlenirse silinmez.

Belge eki olan desteklenen bir liste öğesine bekletme etiketi uyguladığınızda:
- Standart saklama etiketi için (öğeyi kayıt olarak bildirmez):
    - Belge eki, etiketin bekletme ayarlarını otomatik olarak devralmaz, ancak bağımsız olarak etiketlenebilir.
- Öğeyi kayıt olarak bildiren bir bekletme etiketi için: 
    - Belge henüz etiketlenmemişse belge eki, bekletme ayarlarını etiketten otomatik olarak devralır.

Hem bekletme ilkelerine hem de bekletme etiketlerine ait bekletme ayarları kitaplıklar, listeler ve klasörler içeren yapıları düzenlemek için geçerli değildir.

Bekletme ilkeleri ve etiket ilkelerini otomatik uygulama için: bekletme ayarlarının uygulanması için SharePoint sitelerin dizine alınması gerekir. Ancak, SharePoint belge kitaplıklarındaki öğeler arama sonuçlarında görünmeyecek şekilde yapılandırılmışsa, bu yapılandırma dosyaları bekletme ayarlarından dışlamaz.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Bekletme SharePoint ve OneDrive için nasıl çalışır?

Korunması gereken içeriği depolamak için, SharePoint ve OneDrive site için mevcut olmayan bir Koruma Bekletme kitaplığı oluşturun. Koruma Bekletme kitaplığı etkileşimli olarak kullanılmak üzere tasarlanmamıştır, ancak bunun yerine, uyumluluk nedenleriyle gerektiğinde dosyaları otomatik olarak depolar. Aşağıdaki şekilde çalışır:

Kullanıcı bekletmeye tabi olan bir öğeyi değiştirdiğinde veya sildiğinde, bekletme ayarları uygulandıktan sonra içeriğin değiştirilip değiştirilmediğine ilişkin bir denetim yapılır. Bekletme ayarları uygulandıktan sonra yapılan ilk değişiklik buysa, içerik, kullanıcının özgün içeriği değiştirmesine veya silmesine olanak tanıyan Koruma Saklama kitaplığına kopyalanır.

Bir zamanlayıcı işi, Koruma Bekletme kitaplığında düzenli aralıklarla çalışır. Koruma Bekletme kitaplığında 30 günden uzun süredir bulunan içerik için, bu iş içeriği söz konusu içeriğin bekletme ayarları tarafından kullanılan tüm sorgularla karşılaştırır. Yapılandırılan saklama süresinden daha eski olan içerik daha sonra Koruma Saklama kitaplığından ve hala oradaysa özgün konumdan silinir. Bu zamanlayıcı işi yedi günde bir çalıştırılır ve bu da minimum 30 günle birlikte içeriğin Koruma Tutma kitaplığından silinmesinin 37 güne kadar sürebileceği anlamına gelir.

Dosyaları Koruma Bekletme kitaplığına kopyalamak için bu davranış, bekletme ayarları uygulandığında var olan içeriğe uygulanır. Ayrıca, bekletme ilkeleri için, ilkeye eklendikten sonra oluşturulan veya siteye eklenen tüm yeni içerikler Koruma Bekletme kitaplığında saklanır. Ancak yeni içerik, ilk kez düzenlendiğinde, yalnızca silindiğinde Koruma Saklama kitaplığına kopyalanmamıştır. Dosyanın tüm sürümlerini korumak için, özgün site için [sürüm oluşturma](#how-retention-works-with-document-versions) açık olmalıdır.
  
Kullanıcılar saklamaya tabi olan bir kitaplığı, listeyi, klasörü veya siteyi silmeye çalışırlarsa bir hata iletisi görür. İlk olarak klasördeki saklamaya tabi olan dosyaları taşırlarsa veya silerlerse klasörü silebilirler.

Kullanıcılar aşağıdaki koşullardan herhangi birinde etiketli bir öğeyi silmeye çalışırlarsa da bir hata iletisi görür. Öğe Koruma Saklama kitaplığına kopyalanır ancak özgün konumda kalır:

- Kullanıcıların etiketlenmiş öğeleri silmesine olanak tanıyan kayıt yönetimi ayarı kapalıdır.
    
    Bu ayarı denetlemek veya değiştirmek için Kayıt **yönetimiKayıt yönetimi** ayarlarıKayıtlar yönetim **ayarlarıDeletion** >  **labelsDeletion** >  of items(**Kayıt yönetimi** > ) Microsoft 365 uyumluluk merkezi > Kayıtlar yönetimi **çözümüne** gidin. SharePoint ve OneDrive için ayrı ayarlar vardır.
    
    Alternatif olarak, **Kayıt yönetimi** çözümüne erişiminiz yoksa [Get-PnPTenant ve Set-PnPTenant'tan](/powershell/module/sharepoint-pnp/get-pnptenant) *AllowFilesWithKeepLabelToBeDeletedSPO* ve *AllowFilesWithKeepLabelToBeDeletedODB* kullanabilirsiniz [](/powershell/module/sharepoint-pnp/set-pnptenant).

- Bekletme etiketi öğeleri kayıt olarak işaretler ve [kilitlenir](record-versioning.md).
    
    Yalnızca kaydın kilidi açıkken, son sürümün bir kopyası Koruma Bekletme kitaplığında depolanır.

- Bekletme etiketi, öğeleri düzenleme [kaydı](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) olarak işaretler ve bu da öğenin düzenlenmesini veya silinmesini her zaman engeller.

Saklama ayarları bir OneDrive hesabındaki veya SharePoint sitedeki içeriğe atandıktan sonra, içeriğin izlediği yollar bekletme ayarlarının tutulup silineceği, yalnızca korunacak veya yalnızca silinecek olmasına bağlıdır.

Bekletme ayarlarının saklanması ve silinmesi gerektiğinde:

![SharePoint ve OneDrive içerik yaşam döngüsü diyagramı.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. Saklama süresi boyunca **içerik değiştirilir veya silinirse**, saklama ayarları atandığında var olan özgün içeriğin bir kopyası Koruma Bekletme kitaplığında oluşturulur. Burada zamanlayıcı işi, bekletme süresi dolan öğeleri tanımlar. Bu öğeler, 93 günün sonunda kalıcı olarak silindikleri ikinci aşama Geri Dönüşüm Kutusu'na taşınır. İkinci aşama Geri Dönüşüm Kutusu son kullanıcılara görünmez (yalnızca birinci aşama Geri Dönüşüm Kutusu'dur), ancak site koleksiyonu yöneticileri içeriği buradan görüntüleyebilir ve geri yükleyebilir.

    > [!NOTE]
    > Yanlışlıkla veri kaybını önlemeye yardımcı olmak için artık Koruma Bekletme kitaplığından içeriği kalıcı olarak silmeziz. Bunun yerine, içeriği yalnızca Geri Dönüşüm Kutusu'ndan kalıcı olarak sileriz, bu nedenle Koruma Bekletme kitaplığındaki tüm içerik artık ikinci aşama Geri Dönüşüm Kutusu'ndan geçer.
    
2. Saklama süresi boyunca **içerik değiştirilmez veya silinmezse**, zamanlayıcı işi bu içeriği saklama süresinin sonunda birinci aşama Geri Dönüşüm Kutusu'na taşır. Kullanıcı içeriği oradan silerse veya bu Geri Dönüşüm Kutusu'nu boşaltırsa (temizleme olarak da bilinir), belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük saklama süresi hem birinci hem de ikinci aşama geri dönüşüm kutularına yayılmıştır. 93 günün sonunda, belge ilk aşamada veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. Geri Dönüşüm Kutusu dizine alınmamış ve bu nedenle arama için kullanılamıyor. Sonuç olarak, bir eBulma araması, ayrı tutulacak geri dönüşüm kutusu içeriğini bulamaz.

> [!NOTE]
> [İlk saklama ilkesi](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle, aynı öğenin başka bir bekletme ilkesi veya saklama etiketi nedeniyle korunması gerekiyorsa veya yasal veya araştırma amaçlı olarak eBulma tutmaları altındaysa kalıcı silme işlemi her zaman askıya alınır.

Bekletme ayarları yalnızca saklama veya yalnızca silme olduğunda, içerik yolları saklama ve silme çeşitlemeleridir:

### <a name="content-paths-for-retain-only-retention-settings"></a>Yalnızca saklama saklama ayarları için içerik yolları

1. saklama süresi boyunca **içerik değiştirilir veya silinirse**: Koruma Saklama kitaplığında özgün belgenin bir kopyası oluşturulur ve Saklama Saklama kitaplığındaki kopya ikinci aşama Geri Dönüşüm Kutusu'na taşındığında saklama süresinin sonuna kadar saklanır ve 93 gün sonra kalıcı olarak silinir.

2. Saklama süresi boyunca **içerik değiştirilmez veya silinmezse**: Saklama süresinden önce ve sonra hiçbir şey olmaz; belge özgün konumunda kalır.

### <a name="content-paths-for-delete-only-retention-settings"></a>Yalnızca silme bekletme ayarları için içerik yolları

1. İçerik yapılandırılan süre boyunca **silinirse**: Belge birinci aşama Geri Dönüşüm Kutusu'na taşınır. Kullanıcı belgeyi oradan silerse veya bu Geri Dönüşüm Kutusu'nu boşaltırsa, belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük saklama süresi hem birinci hem de ikinci aşama geri dönüşüm kutularına yayılmıştır. 93 günün sonunda, belge ilk aşamada veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. İçerik yapılandırılan dönemde değiştirilirse, yapılandırılan dönemden sonra aynı silme yolunu izler.

2. İçerik yapılandırılan süre boyunca **silinmezse**: Saklama ilkesinde yapılandırılan dönemin sonunda, belge birinci aşama Geri Dönüşüm Kutusu'na taşınır. Kullanıcı belgeyi oradan silerse veya bu Geri Dönüşüm Kutusu'nu boşaltırsa (temizleme olarak da bilinir), belge ikinci aşama Geri Dönüşüm Kutusu'na taşınır. 93 günlük saklama süresi hem birinci hem de ikinci aşama geri dönüşüm kutularına yayılmıştır. 93 günün sonunda, belge ilk aşamada veya ikinci aşama Geri Dönüşüm Kutusu'nda bulunduğu yerden kalıcı olarak silinir. Geri Dönüşüm Kutusu dizine alınmamış ve bu nedenle arama için kullanılamıyor. Sonuç olarak, bir eBulma araması, ayrı tutulacak geri dönüşüm kutusu içeriğini bulamaz.

## <a name="how-retention-works-with-cloud-attachments"></a>Bekletme bulut ekleriyle nasıl çalışır?

Bulut ekleri, kullanıcıların paylaştığı dosyalara eklenmiş bağlantılardır ve kullanıcılarınız bunları Outlook e-postalarda ve Teams iletilerde paylaştığında bunlar saklanabilir ve silinebilir. [Bulut eklerine otomatik olarak bir bekletme etiketi uyguladığınızda](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments), bekletme etiketi paylaşılan dosyanın bir kopyasına uygulanır ve bu kopya Koruma Saklama kitaplığında depolanır.

Bu senaryoda, öğenin etiketlendiği zaman temelinde bekletme süresini başlatmak için etiket ayarını yapılandırmanızı öneririz. Saklama süresini, öğenin ne zaman oluşturulduğuna veya son değiştirildiğine göre yapılandırırsanız, bu tarih paylaşım sırasında özgün dosyadan alınır. Saklama başlangıcını en son değiştirildiğinde olacak şekilde yapılandırdıysanız, bu ayarın Koruma Saklama kitaplığındaki bu kopya için hiçbir etkisi olmaz.

Ancak, özgün dosya değiştirilip yeniden paylaşılırsa, dosyanın yeni bir sürümü olarak yeni bir kopyası kaydedilir ve Koruma Bekletme kitaplığına etiketlenmiştir.

Özgün dosya yeniden paylaşılır ancak değiştirilmezse, Koruma Saklama kitaplığındaki kopyanın etiketli tarihi güncelleştirilir. Bu eylem bekletme döneminin başlangıcını sıfırlar ve bu nedenle, saklama süresinin başlangıcını öğenin etiketlendiği zaman temelinde yapılandırmanızı öneririz.

Bekletme etiketi özgün dosyaya uygulanmadığından etiketlenen dosya hiçbir zaman değiştirilmez veya kullanıcı tarafından silinmez. Etiketli dosya, zamanlayıcı işi saklama süresinin dolduğunu belirleyene kadar Koruma Bekletme kitaplığında kalır. Bekletme ayarları öğeleri silmek üzere yapılandırılmışsa, dosya daha sonra ikinci aşama Geri Dönüşüm Kutusu'na taşınır ve burada 93 günün sonunda kalıcı olarak silinir:

![SharePoint ve OneDrive depolanan bulut eklerinde bekletme nasıl çalışır?](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

Koruma Bekletme kitaplığında depolanan kopya genellikle paylaşılmakta olan bulut ekinden bir saat içinde oluşturulur.

## <a name="how-retention-works-with-onenote-content"></a>Bekletme OneNote içerikle nasıl çalışır?

OneNote klasörüne OneNote içerik veya bekletme etiketi içeren bir konuma bekletme ilkesi uyguladığınızda, arka planda farklı OneNote sayfaları ve bölümleri bekletme ayarlarını devralan ayrı dosyalardır. Bu, bir sayfadaki her bölümün, belirttiğiniz bekletme ayarlarına göre ayrı ayrı tutulacağı ve silineceği anlamına gelir.

Yalnızca sayfalar ve bölümler belirttiğiniz bekletme ayarlarından etkilenir. Örneğin, her not defteri için bir **Değiştirme** tarihi görmenize rağmen, bu tarih Microsoft 365 saklama tarafından kullanılmaz.

## <a name="how-retention-works-with-document-versions"></a>Bekletme belge sürümleriyle nasıl çalışır?

Sürüm oluşturma, SharePoint ve OneDrive tüm belge listelerinin ve kitaplıklarının bir özelliğidir. Varsayılan olarak, sürüm oluşturma en az 500 ana sürümü korur, ancak bu sınırı artırabilirsiniz. Daha fazla bilgi için bkz [. Liste veya kitaplık için sürüm oluşturmayı etkinleştirme ve yapılandırma](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) ve [Listelerde ve kitaplıklarda sürüm oluşturma nasıl çalışır](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247)?
  
Sürümleri olan bir belge bu içeriği korumak için bekletme ayarlarına tabi olduğunda, Koruma Bekletme kitaplığına kopyalanan sürümler ayrı bir öğe olarak bulunur. Bekletme ayarları saklama süresinin sonunda silinecek şekilde yapılandırıldıysa:

- Bekletme süresi içeriğin oluşturulduğu zamana bağlıysa, her sürüm özgün belgeyle aynı sona erme tarihine sahiptir. Özgün belgenin ve sürümlerinin tümü aynı anda sona erer.

- Saklama süresi içeriğin en son ne zaman değiştirildiğine bağlıysa, özgün belgenin bu sürümü oluşturmak için ne zaman değiştirildiğine bağlı olarak her sürümün kendi sona erme tarihi vardır. Özgün belgenin ve sürümlerinin süresi birbirinden bağımsız olarak dolar.

Bekletme eylemi belgeyi silmek olduğunda, Koruma Bekletme kitaplığında bulunmayan tüm sürümler geçerli sürüme göre aynı anda silinir.

Bekletme ilkesine (veya eBulma ayrı tutmasına) tabi olan öğeler için, belge kitaplığının sürüm oluşturma sınırları, belgenin saklama süresine ulaşılana (veya eBulma ayrı tutması serbest bırakılana) kadar yoksayılır. Bu senaryoda, eski sürümler otomatik olarak temizlenmez ve kullanıcıların sürümleri silmesi engellenir.

İçerik bir bekletme ilkesine (veya eBulma bekletmesine) tabi olmadığında bekletme etiketleri için bu durum geçerli değildir. Bunun yerine, eski sürümlerin yeni sürümleri barındıracak şekilde otomatik olarak silinmesi, ancak kullanıcıların sürümleri silmesinin engellenmesi için sürüm oluşturma sınırları uygulanır.

## <a name="when-a-user-leaves-the-organization"></a>Kullanıcı kuruluştan ayrıldığında

**SharePoint**:

Bir kullanıcı kuruluşunuzdan ayrıldığında, kullanıcının posta kutusu veya OneDrive hesabından farklı olarak SharePoint işbirliğine dayalı bir ortam olarak kabul edildiğinden bu kullanıcı tarafından oluşturulan içerik etkilenmez.

**OneDrive**:

Kullanıcı kuruluşunuzdan ayrılırsa, bekletme ilkesine tabi olan veya bekletme etiketi olan tüm dosyalar, ilkede veya etikette belirtilen saklama süresi boyunca bekletme ayarlarına tabi kalır. Bu süre boyunca tüm paylaşım erişimi çalışmaya devam eder ve içerik İçerik Arama ve eBulma tarafından bulunabilir olmaya devam eder. 

Saklama süresi dolduğunda ve bekletme ayarları bir silme eylemi içerdiğinde, içerik Site Koleksiyonu Geri Dönüşüm Kutusu'na taşınır ve yönetici dışında hiç kimse tarafından erişilemez.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Microsoft 365'da bekletmeyi yapılandırma konusunda yeniyseniz bkz. [bilgi idaresiyle Kullanmaya başlayın](get-started-with-information-governance.md).

Exchange için bir bekletme ilkesi veya bekletme etiketi yapılandırmaya hazırsanız aşağıdaki yönergelere bakın:
- [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)