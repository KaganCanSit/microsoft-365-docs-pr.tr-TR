---
title: Gruplar, ekipler ve Yammer için yaşam döngüsü sonu seçenekleri
ms.reviewer: mmclean
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
description: Gruplar, ekipler ve Yammer için yaşam döngüsü sonu seçenekleri.
ms.openlocfilehash: f7774498047f74c27b21e45ed86b284a42325bb0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973937"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Gruplar, ekipler ve Yammer için yaşam döngüsü sonu seçenekleri

Microsoft 365 Grupları ve Microsoft Teams birden çok bağlı hizmetle çalışır. Bir grup veya ekip silindiğinde, bağlı hizmetlerdeki bilgilerin çoğu da silinir. Bu makalede, silme işleminden önce bilgileri gruptan veya ekipten çıkararak saklama seçenekleri açıklanmaktadır.

Artık gerekli olmayan gruplar veya ekipler için yaygın bir uygulama, dosyaları ekip dışına taşımak ve bunları SharePoint belge kitaplığı gibi başka bir konumda arşivlemektir. Bu uygulama, bilgilerin dosya ve klasörlerde depolandığı ve iletişimlerin e-posta yoluyla yürütüldüğü eski bir çalışma stilini temel alır.

Aşağıdaki tabloda gruplar ve ekiplerle ilişkilendirilmiş hizmetler ve bunların her birinde bulunan önemli içerik türleri özetlenmektedir:

|Hizmet|İçerik türleri|
|:------|:---------------|
|Teams|Kanal konuşmaları, kanallardaki dosyalar|
|Forms|Anket yapısı ve sonuçları|
|OneNote|Dizüstü|
|Outlook|Posta ve takvim|
|Planner|Project durumu ve görev bilgileri|
|Power Automate|Iş akışı|
|Power BI|Veriler, raporlar ve panolar|
|Web'de Project|planları Project|
|Yol Haritası|Yol Haritaları|
|SharePoint|Dosyalar, listeler Teams kanal wiki verileri|
|Stream|Videolar|
|Yammer|Konuşma|

Bir grup veya ekip silinirken, ilişkili kaynakların çoğu da silinir. Özel durumlar şunlardır:

- Stream'deki videolar kalır ve bunları karşıya yükleyen/kaydeden kişiye aittir
- Power Automate akışlar kalır ve bunları oluşturan kişiye aittir.
- Web üzerinde Project Project ve yol haritası verileri CDS'de kalır ve ayrı olarak geri yüklenebilir.

Gruplar ve ekipler 30 gün boyunca geçici silme durumunda kalır ve istedikleri zaman geri yüklenebilir. Ancak, 30 gün sonra bunlar ve hizmetler ve içerik gibi ilişkili kaynaklar Microsoft 365 ortamından temizlenir. Bekletme ilkesi tarafından korunan tüm içerikler eBulma aramalarıyla kullanılabilir durumda kalır.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Gruba bağlı hizmetler için kullanım süresi sonu ile ilgili dikkat edilmesi gerekenler

Ekip ve grup sahiplerinin ve BT yöneticilerinin bir grubu veya ekibi silerken dikkate almaları gereken üç önemli alan vardır.

**İçerik**

Ekip artık orada olmadığında içeriğin korunması gerekiyor mu? Microsoft 365 saklama özelliklerine güvenmek yeterli mi yoksa uygulama ve hizmetlerde bekletme sunmayan içeriklerden bazıları mı? İçeriğin kayıt yönetimi, arşivleme veya gelecekte kullanım ve başvuru amacıyla saklanması gerekiyor mu?

Olası veri kaybını önlemek için, herhangi bir ekibin arşivlenip silinmesi için bu soruların sorulması gerekir.

**Hizmetleri**

İçeriğin geçerli çalışma formunda kalması gerekiyor mu? Örneğin, Power BI raporunun erişilebilir olmaya devam etmesi gerekiyor mu? Form sonuçlarının görsel özet görünümünde kullanılabilir olması gerekiyor mu? SharePoint'deki listeler herhangi bir yere bağlı mı yoksa eklenmiş mi?

İçeriği dışarı aktarmak yeterli olmadığından, temel alınan grup silinmeden önce bu soruların sorulması gerekir.

**Konuklar**

Konuklar bir takıma davet edildiğinde, konak kuruluşun Azure Active Directory eklenmeden önce bir konuk hesabı oluşturulur. Bir ekip silindiğinde, konuklar Azure Active Directory kaldırılmaz. Konuklar kendileriyle paylaşılmayan gruplara, sitelere, ekiplere veya içeriğe erişemese de sohbet başlatma, sesli ve görüntülü arama yapma ve uygulamaları kullanma gibi Microsoft Teams içindeki özellikleri kullanmaya devam edebilir.

Ekip veya grup sahibi, kuruluş dışından birini bir ekibİye ekleyerek Azure Active Directory konuk olmaya davet edebilir. Ancak ekip sahibi, konuğu Azure Active Directory kaldıramaz. Hesapları silme işlemi yalnızca genel yönetici veya kullanıcı yöneticisi tarafından gerçekleştirilebilir.

Konuk değerlendirmeleri yapmak ve ekip silindikten sonra konukların Azure Active Directory kaldırılması gerekip gerekmediğini anlamak önemlidir. Diğer ekiplerin üyesi olmak veya diğer Microsoft 365 veya Azure hizmetlerini kullanmak gibi, konukların dizinde kalması için geçerli bir durum olabilir.

## <a name="teams"></a>Teams

Teams özgü içerik öncelikli olarak konuşma biçimindedir.

Kanallardaki konuşmalar yerel Microsoft Teams işlevselliği kullanılarak kopyalanamaz veya taşınamaz. Ancak Graph API kullanılarak dışarı aktarılabilirler.

Ayrıca, Teams bir bekletme ilkesi uygulanırsa, konuşmalar korunur ve eBulma aramaları aracılığıyla kullanılabilir. eBulma (Premium) kullanarak [Teams sohbet konuşmasını yeniden oluşturabilirsiniz](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Ekibi arşivleme

[Ekibi arşivlemenin](/microsoftteams/archive-or-delete-a-team) avantajı, ekibi olduğu gibi tam erişim sağlamasıdır. Kullanıcılar etkin olmasalar bile kanal konuşmalarına göz atabilir ve dosyaları açabilir. Ayrıca, üzerinde çalışmaya devam etmeniz gerekiyorsa (örneğin, bir proje genişletilmişse) ekiplerin arşivleri kaldırılabilir.

Ekip sahibi tarafından arşivlendiğinde, ekip içindeki içerik için ve seçilirse ilişkili SharePoint sitesi üyeleri için salt okunur olarak ayarlanır. Bu eylemin amacı, kanallardaki konuşmaların dosyalar ve wiki'ler gibi SharePoint tabanlı içerikle birlikte mevcut durumlarında korunmasını sağlamaktır.

SharePoint sitesinde görünür bir değişiklik yoktur. Ancak, Microsoft 365 grubu için SharePoint izinleri **Site ziyaretçileri** olarak ayarlandığından hiçbir dosyada veya listede değişiklik yapılamaz. Bu, SharePoint sitesindeki Site Varlıkları kitaplığında depolanan ekip için OneNote not defterini içerir.

Bir ekip arşivlendiğinde, temel alınan Microsoft 365 grubu hala süre sonu ilkesine tabi olur (ayarlandıysa) ve bu nedenle sahibin ekibi yenilemeye devam etmesi gerekir.

Ekibin kanal konuşmaları ve SharePoint site içeriği salt okunur olarak ayarlanmış olsa da, aynı durum diğer ilişkili hizmetlere uygulanmaz:

- Planner demetleri ve görevleri yine oluşturulabilir, değiştirilebilir ve silinebilir.
- Formlar yine de gönderim alabilir.
- Outlook posta kutusu yine de e-posta alabilir.
- Power BI panolar, raporlar ve veriler hala değiştirilebilir.
- Projeler ve yol haritaları web'deki Project düzenlenebilir.
- Stream'de videolar yine karşıya yüklenebilir, değiştirilebilir ve silinebilir.
- Power Automate akışlar yine oluşturulabilir, değiştirilebilir, silinebilir ve çalışmaya devam eder. (Ancak, arşivlenen ekibin bir kanalına ileti göndermek gerekirse başarısız olur.)

## <a name="forms"></a>Forms

Form tek bir hesaptan bir gruba taşınabilir ancak bir gruptan diğerine taşınamaz veya kopyalanamaz. Bir ekip silindiğinde form için üç seçenek kullanılabilir.

**Formu yineleme**

Formlar [şablon olarak paylaşılabilir](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f) ve diğer kullanıcıların kendi hesaplarına veya bir gruba kopyalamasına olanak sağlar. Bu işlem sonuç gönderimlerindeki verileri korumaz; yalnızca sorular ve ayarlar gibi bir yapı oluşturur.

**Sonuçları elektronik tabloya aktarma**

Form yanıtlarının verilerinin korunması gerekiyorsa, [sonuçları bir Excel elektronik tablosuna aktararak](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af) bu elde edilebilir. Bu yalnızca soruları ve yanıtlarını veri olarak dışarı aktarır; Formlar tarafından oluşturulan grafikleri içermez.

**Formu Silme**

Grubun silinmesi de ilişkili formların silinmesine neden olur, ancak grup üyeleri grubun sahibi olmadan [bunları doğrudan silebilir](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) . Ancak, bu el ile gerçekleştirilen ve ek fayda sağlamayan bir adımdır.

## <a name="onenote"></a>OneNote

Bir gruba dahil OneNote not defteri, ilişkili SharePoint sitesindeki Site Varlıkları kitaplığında depolanır. Not defteri dosyaları bazen birden çok dosyaya yayılabilir ancak bağımsız olarak kopyalanamaz ve açılamaz. Bunun yerine, OneNote not defterinin içeriği OneNote 2016 kullanılarak taşınmalıdır veya dışarı aktarılmalıdır.

**Sayfaları ve bölümleri başka bir not defterine taşıma**

[Sayfaları veya bölümleri ayrı ayrı başka bir not defterine taşımak](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) , sahiplere verilerini temizleme ve yalnızca saklanması gerekenleri alma fırsatı sağlar.

**Not defterinin tamamını paket olarak dışarı aktarma**

Not defterinin tamamının mevcut yapısıyla korunması gerekiyorsa, [OneNote paket dosyası olarak dışarı](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) aktarılabilir ve ardından yeni bir konuma aktarılabilir. Bunun yerine, bu, içeriği mevcut çok dosyalı yapı yerine tek bir dosyada tutmak için bir yöntem olarak kullanılabilir.

**PDF'ye yazdır**

Not defterinin bazı içeriğinin yalnızca başvuru için veya kayıt olarak saklanması gereken senaryolarda, tek tek sayfalar [PDF'ye yazdırılabilir ve başka bir yerde depolanabilir](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Posta kutusu ve takvim

Ekip kanallarında birçok konuşma yapılmış olsa bile grupla ilişkili posta kutusunun kullanılması sık karşılaşılan bir durum değildir. Posta kutusu yalnızca doğrudan e-postayla gönderilen e-postaları depolar ve doğrudan kanallara gönderilen e-postaları içermez.

Bazı durumlarda, posta kutusunda depolanan e-postalar toplantı bildirimleri, Planner görev güncelleştirmeleri ve diğer uygulama veya sistem tarafından oluşturulan iletiler olabilir. posta kutusunun içeriğinin gözden geçirilmesi, içeriğin korunması mı yoksa silinmesi mi gerektiğini belirlemek için önemlidir.

Exchange bir bekletme ilkesi uygulanırsa, e-postalar ve takvim öğeleri korunur ve eBulma aramaları aracılığıyla kullanılabilir.

**Postayı ve takvimi dışarı aktarma**

Ekip veya grup üyeleri[, posta kutusunun ve takvimin içeriğini bir Outlook Verileri / Kişisel Depolama (PST) dosyasına aktarabilir](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91). Bu dosya daha sonra başka bir yerde depolanabilir veya içerik farklı bir posta kutusuna aktarılabilir. PST dosyasının içeriği Outlook açılmadan aranamaz ve dosyanın kendisi zaman içinde bozulaabildiği için ilk dosya önerilmez.

**BT tarafından gerçekleştirilen içerik geçişi**

Yöneticiler, herhangi bir kullanıcı müdahalesi olmadan e-posta ve takvim içeriğini posta kutuları arasında geçirmek için üçüncü taraf araçları kullanabilir. Olası bir depolama konumu, yalnızca grup posta kutusu içeriğinin "arşivi" olarak görev yapmak için oluşturulmuş paylaşılan bir posta kutusu olabilir.

## <a name="planner"></a>Planner

Her grubun veya ekibin birden çok planı olabilir. Her plan için bekletme gereksinimlerinin karşılandığından emin olmak, biniş dışı işlem sırasında önemlidir. Diğer hizmetler gibi Planner'da da pano dışı içeriğe yönelik çeşitli yaklaşımlar vardır.

**Planı elektronik tabloya aktarma**

Yalnızca kayıt tutma amacıyla planın bir kopyasının tutulması gerekiyorsa, en basit yaklaşım [planı Excel bir elektronik tabloya dışarı aktarmaktır](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Bu tek yönlü bir eylemdir; planları elektronik tablodan içeri aktarma seçeneği yoktur.

> [!IMPORTANT]
> Planı Excel dışarı aktarmak, plan içindeki bilgilerin çoğunu alır, ancak açıklamalar, bağlantılar veya dosyalar içermez.

**Görevleri kopyalama ve başka bir Plana taşıma**

Görevleri başka bir plana kopyalamak veya taşımak bir çözüm gibi görünse de, tek tek görevler yalnızca aynı grup içindeki [planlar arasında kopyalanabilir veya taşınabilir](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) . Planla ilişkili grup siliniyorsa bu işlem verileri yedeklemez.

**Planın tamamını kopyalama**

[Planın tamamını kopyalamak](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4) da mümkündür. Kopyalama mevcut bir gruba yapılamaz. Planın kopyalanması yeni bir grup oluşturur. Ayrıca, planın tamamının kopyalanması açıklamalar, atamalar, bağlantılar, ekler veya tarihler içermez.

## <a name="power-automate"></a>Power Automate

Power Automate oluşturulan ve bir grup veya ekiple ilişkilendirilmiş akışlar gruba ait değildir. Bunlar oluşturucuya aittir ve yalnızca diğer kullanıcılar ve gruplarla paylaşılır. Bu nedenle, bir grup veya ekip silinirse bu durumdan etkilenmez.

**Akışın sahipliğini değiştirme**

Akışın çalışmaya devam etmesi gerekiyorsa, herhangi bir sahip diğer kullanıcıları veya Microsoft 365 gruplarını sahip olarak ekleyebilir.

**Akışı dışarı aktarma**

Akışın çalışmaya devam etmesi gerekmiyorsa ancak gelecekteki olası kullanım için korunması gerekiyorsa, [bir dosya olarak dışarı aktarılabilir](https://flow.microsoft.com/blog/import-export-bap-packages/) ve daha sonra yeniden içeri aktarılabilir.

## <a name="power-bi"></a>Power BI

Power BI veriler ve çalışma alanları gruplardan ve ekiplerden bağımsız olarak çalışabilir ve diğer iş yükleri gibi farklı yollardan kullanıma alınamaz.

**Raporları başka bir çalışma alanına kopyalama**

Grup veya ekip silindikten sonra rapora ihtiyacınız varsa, rapor [mevcut çalışma alanından Power BI içindeki başka bir çalışma alanına kopyalanabilir](/power-bi/connect-data/service-datasets-copy-reports).

**Panodan veya rapordan verileri dışarı aktarma**

Bunun yerine, raporun artık etkin olması ve verilerin korunması gerekiyorsa[, Excel dışarı aktarılabilir](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Web için Project oluşturulan projeler ve Yol Haritaları Microsoft 365 gruplarla ilişkilendirilir ve Power BI benzer şekilde bindirmeye yönelik yaklaşımlara sahiptir.

**Projeyi başka bir gruba atama**

Projenin, grubun veya ekibin ömrü dışında işlevsel durumunda korunması gerekiyorsa, [farklı bir Microsoft 365 grubuna atanabilir](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Bu işlem Dynamics 365 Yönetim Merkezi kullanılarak yapılabilir.

**Projeden veya yol haritasından verileri dışarı aktarma**

Dynamics 365 Yönetim Merkezi'ni kullanarak [kullanıcı verilerini projeden](/project-for-the-web/export-user-data-from-project-for-the-web) bir elektronik tabloya dışarı aktarabilirsiniz. Veriler Project dosyasına da aktarılabilir (. powershell kullanarak MPP) ve XML dosya biçimleri.

## <a name="sharepoint"></a>SharePoint

Ekip kanallarındaki tüm dosyalar, ilişkili grubun SharePoint sitesinde depolanır. Bazı durumlarda, belgeler dışındaki içerikler listeler veya sayfalar gibi SharePoint bulunabilir.

Dosyalar genellikle bir SharePoint sitesinde üç birincil konumda depolanır:

- Sayfalar - Site Sayfaları kitaplığı
- Sayfalarda kullanılan görüntüler – Site Varlıkları kitaplığı
- Kanallardaki dosyalar – Belgeler kitaplığı
- Wiki sayfaları – Wiki Veri kitaplığı Teams

Sitede bir veya daha fazla alt site varsa, her alt site için biniş dışı işleminin yinelenmesi gerekir. Ekip özel veya paylaşılan kanallar içeriyorsa, her kanal için ayrı bir SharePoint sitesi vardır.

Dosyaları bir gruptan veya ekipten kaldırırken, bunların grubun veya ekibin üyesi olmayan kullanıcılarla paylaşılabileceğini göz önünde bulundurmak önemlidir. Yaklaşan değişikliği onlara iletmek isteyebilirsiniz.

**Dosyaları indirme**

Yukarıda bahsedilen kitaplıklardan birinde SharePoint depolanan dosyalar [yerel bir bilgisayara indirilebilir](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Dosyaları taşıma**

Ayrıca, dosyalar [farklı bir sitedeki kitaplık gibi SharePoint içinde başka bir konuma taşınabilir](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Listeyi dışarı aktar**

SharePoint listelerinde depolanan veriler [Excel bir elektronik tabloya aktarılabilir](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) ve yeniden başka bir sitedeki bir listeye aktarılabilir.

Alternatif olarak, işlevi, liste görünümlerini, biçimlendirmeyi ve diğer öznitelikleri korumak için listeyi siteler arasında geçirmek için üçüncü taraf bir araç kullanılabilir.

**"Dışarı aktar" wiki dosyaları**

Ekip kanallarındaki Wiki içeriği, ilişkili SharePoint sitesinin ayrılmış kitaplığında HTML biçimli bir dosyada depolanır. Bunlar kolayca dışarı aktarılamaz ve başka bir kanal wiki'sine aktarılamaz, ancak html dosyasına dönüştürülebilir ve web sayfası olarak açılabilir.

## <a name="microsoft-stream"></a>Microsoft Stream

Power Automate gibi Stream'de bir grup veya ekiple ilişkilendirilmiş videolar da gruba ait değildir ve grup silindiğinde silinmez. Stream'deki videolar, kullanıcıları veya grupları sahip olarak ekleseler bile videoyu karşıya yükleyen veya oluşturan kişiye aittir. bir Teams kanalında kaydedilen toplantılar kaydı başlatan kişiye aittir.

**Diğer sahipleri ekleme**

Grup silindiğinde video Stream'de tutulduğundan, özgün sahip [videoyu diğer kullanıcılar ve gruplarla paylaşabilir, hatta bunları sahip olarak ekleyebilir](/stream/portal-edit-video).

**Videoyu indirin**

Videonun Stream'de tutulmasının gerekmeyen veya kayıt yönetim sistemi gibi alternatif bir konumda depolanması gereken senaryolarda, bir sahip [videoyu yerel olarak indirebilir](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

Microsoft Teams konuşmalarından farklı olarak, Yammer hem kullanıcılara hem de yöneticilere konuşmaları taşıma veya dışarı aktarma seçenekleri sunar.

**Konuşmaları başka bir gruba veya topluluğa taşıma**

Konuşmalar, yalnızca sahipler veya yöneticiler tarafından değil, herhangi bir kullanıcı tarafından başka bir Yammer grubuna taşınabilir. Bu hem [klasik Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872) hem de [yeni Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) arabirimlerinde mümkündür.

**Ağ verilerini dışarı aktarma**

Yammer ağ yöneticileri [ağ verilerini dışarı aktarır](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Ancak, bunu yaptığınızda tüm ağ için tüm konuşmalar dışarı aktarılır. Sonuçta elde edilen dışarı aktarmada Grup Kimliği listelenir. Bu kimliğe göre konuşmaları filtrelemek mümkündür.

## <a name="related-topics"></a>İlgili konular

[Eski bir çalışanı kaldırın ve verileri güvenli hale getirin](/microsoft-365/admin/add-users/remove-former-employee)
