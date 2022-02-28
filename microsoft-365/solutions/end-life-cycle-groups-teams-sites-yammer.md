---
title: Gruplar, ekipler ve ekipler için yaşam döngüsü sonu Yammer
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
description: Gruplar, ekipler ve ekipler için yaşam döngüsü sonu Yammer.
ms.openlocfilehash: 883af3878bd0bc68aa539fc1cc36b66c4f1cfe9e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985179"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Gruplar, ekipler ve ekipler için yaşam döngüsü sonu Yammer

Microsoft 365 Grupları ve Microsoft Teams hizmetlerle çalışma. Bir grup veya ekip silindiğinde, bağlı hizmetlerde yer alan bilgilerin çoğu da silinir. Bu makalede, bilgileri silmeden önce grubun veya ekibin dışından taşımaya yönelik seçenekler açıklanmıştır.

Artık gerekli olan gruplar veya ekipler için yaygın bir uygulama, dosyaları ekip dışında taşımak ve bunları belge kitaplığı gibi başka bir SharePoint arşivlemektir. Bu uygulama, dosyaların ve klasörlerin içinde bilgilerin depolandığı ve iletişimlerin e-posta yoluyla yürütüldükleri eski bir çalışma stilini temel alır.

Aşağıdaki tabloda gruplarla ve ekiplerle ilişkili hizmetler ve bunların her biri bulunan önemli içerik türleri özetlemektedir:

|Hizmet|İçerik türleri|
|:------|:---------------|
|Teams|Kanal konuşmaları, kanallarda dosyalar|
|Formlar|Anket yapısı ve sonuçları|
|OneNote|Not Defteri|
|Outlook|Posta ve takvim|
|Planner|Project ve görev bilgilerini kontrol edin|
|Power Automate|İş Akışları|
|Power BI|Veriler, raporlar ve panolar|
|Project'da arama|Project planları|
|Yol Haritası|Yol Haritaları|
|SharePoint|Dosyalar, listeler ve Teams wiki verileri|
|Stream|Videolar|
|Yammer|Konuşmalar|

Bir grup veya ekibi sildikten sonra ilişkili kaynakların çoğu da silinir. Özel durumlar şunlardır:

- Stream'de videolar kalır ve bunları karşıya yük eden/kaydeden kişiye aittir
- Akışlar Power Automate kalır ve bunları oluşturan kişiye aittir.
- Project Web üzerinde Project yol haritası verileri CDS'de kalır ve ayrı olarak geri yüklenebilir.

Gruplar ve ekipler 30 gün boyunca yumuşak silme durumda kalır ve istediğiniz zaman geri yüklenebilir. Bununla birlikte, 30 günlük süreden sonra bunlar ve hizmetler ve içerik gibi ilişkili kaynaklar Microsoft 365 temiz olur. Bekletme ilkesi tarafından korunan tüm içerikler eBulma aramaları yoluyla kullanılabilir durumda kalır.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Grup bağlantılı hizmetler için yaşam döngüsü sonu ile ilgili dikkate alınacak noktalar

Ekip ve grup sahiplerinin ve IT yöneticilerinin bir grubu veya ekibi silerek göz önünde bulunduracak üç önemli alanı vardır.

**İçerik**

Ekip artık orada kalmadan içeriği korumamız gerekiyor mu? Bekletme özelliklerine güvenerek mi Microsoft 365 yoksa bekletme özelliği sun yer alan uygulama ve hizmetlerde yer alan bazı içerikler mi kullanılabilir? İçerik kayıt yönetimi, arşivleme veya gelecekte kullanım ve başvuru amacıyla tutulsun mu?

Olası veri kaybını önlemek için, herhangi bir ekibi arşivlemeden veya smeden önce bu sorular sorulması gerekir.

**Hizmetler**

İçerik geçerli çalışma formunda kalmalı mı? Örneğin, bu Power BI erişilebilir olmaya devam etmek zorunda mı? Form sonuçlarının görsel özet görünümünde kullanılabilir olması gerekiyor mu? Aşağıdaki listelerde listeler her SharePoint bağlanmış veya eklenmiş mi?

İçeriği dışarı aktarma yeterli olmayabilir ve temel grup silinmeden önce bu sorular sorulmelidir.

**Konuklar**

Konuklar ekme davet edildiklerde, onları ekme eklemeden önce, ev sahibi Azure Active Directory hesabında bir konuk hesabı oluşturulur. Ekip silindiğinde konuklar bu konuk tarafından Azure Active Directory. Konuklar kendileriyle paylaşılmamış gruplara, sitelere, ekiplere veya içeriğe erişimleri mümkün olmasa da, Microsoft Teams'da sohbet başlatma, sesli ve görüntülü arama başlatma ve uygulamaları kullanma gibi özellikleri kullanabilir.

Ekip veya grup sahibi, kuruluş dışından birini ek bir ek gruba ekleyerek Azure Active Directory konuk olmaya davet ediyor olabilir. Ancak ekip sahibi, bu konuk yerine o konuğu Azure Active Directory. Hesapları silme işlemi yalnızca genel yönetici veya kullanıcı yöneticisi tarafından yapılabilir.

Konuk değerlendirmeleri yapmak ve ekibi silme işlemi sırasında konukların değerlendirmeden kaldırılmasının gerekli olup olmadığını Azure Active Directory önemlidir. Konukların dizinde kalması, örneğin diğer ekiplerin üyesi olması ya da diğer kullanıcıları ya da Azure hizmetlerini Microsoft 365 geçerli bir durum olabilir.

## <a name="teams"></a>Teams

Teams belirli içerik öncelikle konuşma biçimine göredir.

Kanallarda yer alan konuşmalar, yerel dil kullanımı veya Microsoft Teams kullanılarak kopyalanamaz. Ancak bunlar Graph API kullanılarak dışarı Graph.

Buna ek olarak, eBulma aramaları Teams bir bekletme ilkesi uygulanmışsa, konuşmalar korunur ve kullanılabilir. Gelişmiş eBulma kullanarak sohbet görüşmelerini [yeniden Teams edebilirsiniz](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Ekibi arşivleme

Ekibi [arşivlemenin avantajı, ekibi](/microsoftteams/archive-or-delete-a-team) daha önce olduğu gibi tam erişime sahip olarak arşivlemektır. Kullanıcılar hala kanal konuşmalarına göz atabilir ve etkin olmayan dosyaları açabilir. Buna ek olarak, üzerinde çalışmaya devam etmek gerekirse (örneğin, bir proje uzatıldı ise) ekipler de arşivden silinebiliyor.

Ekip sahibi tarafından arşivlenen ekip, üyeler için hem ekip içindeki içerikler için hem de seçiliyse ilişkili site için salt SharePoint ayarlanır. Bu eylemin amacı, kanallarda yapılan konuşmaların mevcut durumlarında ve dosya ve wiki SharePoint tabanlı içeriklerde korunmasını sağlamaktır.

Site SharePoint görünür bir değişiklik yok. Bununla birlikte, Herhangi bir dosya veya liste üzerinde hiçbir değişiklik SharePoint, Microsoft 365 Site ziyaretçileri olarak **ayarlanmıştır**. Bu, OneNote site içindeki Site Varlıkları kitaplığında depolanan ekip için SharePoint içerir.

Bir ekip arşivlenirken, temel Microsoft 365 grubu süre sonu ilkesine (ayarlanmışsa) tabi olmaya devam eder ve bu şekilde ekibin sahibinin ekibi yenilemeye devammesi gerekir.

Ekibin kanal konuşmaları ve site SharePoint salt okunur olarak ayarlanırken, aynı durum diğer ilişkili hizmetlere uygulanmaz:

- Planner demetleri ve görevleri yine oluşturulabilir, değiştirilebilir ve silinebilir.
- Formlar yine gönderimleri almaya devam ediyor.
- Posta Outlook e-posta almaya devam ediyor olabilir.
- Power BI, raporlar ve veriler yine değiştirilebilir.
- Projeler ve yol haritaları, web üzerinde Project düzenlenemez.
- Videolar Stream'de yine karşıya yüklenebilir, değiştirilebilir ve silinebilir.
- Çalışma Power Automate, değiştirilebilir, silinebilir ve çalışmaya devam eder. (Ancak, arşivlenmiş ekibin bir kanalına ileti göndermeleri gerekirse başarısız olur.)

## <a name="forms"></a>Formlar

Form tek bir hesaptan bir gruba taşınsa da, bir gruptan diğerine taşınama veya kopyalanamaz. Bir ekip silindiğinde, form için üç seçenek vardır.

**Formu çoğaltma**

Formlar şablon [olarak paylaşarak](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f) diğer kullanıcıların kendi hesaplarına veya bir gruba kopyalamalarına olanak sağlar. Bu, sonuç gönderimlerinden gelen verileri tutmaz; sorular ve ayarlar gibi yalnızca form yapısı.

**Sonuçları elektronik tablo olarak dışarı aktarma**

Form yanıtlarının verileri korunsa da, sonuçlar bir elektronik tabloda dışarı aktararak [Excel sağ edilebilir](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Bu, yalnızca soruları ve onların yanıtlarını veri olarak dışarı aktaracak; Forms tarafından oluşturulan grafikleri içermez.

**Formu silme**

Grubun silinmesi de ilişkili formların silinmesine neden olurken, grup üyeleri bunları grubun sahibi olmadan doğrudan [](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) silebilir. Bununla birlikte, bu el ile herhangi bir ek avantaj sağlamaktan başka bir adımdır.

## <a name="onenote"></a>OneNote

Gruba OneNote not defteri, ilişkili sitenin Site Varlıkları kitaplığında SharePoint. Not defteri dosyaları bazen birden çok ayrı dosyaya yayılabilir ama bunlar birbirinden bağımsız olarak kopyalanamaz ve açılamıyor. Bunun yerine, not defterinin OneNote defteri kullanılarak başka bir yere OneNote 2016.

**Sayfaları ve bölümleri başka bir not defterine taşıma**

[Sayfaları veya bölümleri başka bir not](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) defterine tek tek taşıma, sahiplere verilerini temizleme ve yalnızca korumaları gerekenleri alma fırsatı sunar.

**Not defterinin tamamını paket olarak dışarı aktarma**

Not defterinin tamamının mevcut yapısıyla korunması gerekirse, not defteri OneNote olarak dışarı [](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) aktarıldı ve sonra yeni bir konuma aktarıldı. Bunun yerine, içeriği var olan çok dosyalı yapı yerine tek bir dosyada tutmak için bir yöntem olarak kullanılabilir.

**PDF olarak yazdırma**

Not defterinin bazı içeriğinin başvuru ya da kayıt olarak tutul olması gereken senaryolarda, tek tek sayfalar PDF'ye yazdırılabilir ve başka [bir yerde depolanır](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Posta kutusu ve takvim

Grupla ilişkilendirilmiş posta kutusunun kullanılması az görülen bir durum değildir; ancak ekip kanalları içinde birçok konuşma yürüttürtür. Posta kutusu yalnızca doğrudan e-postayla gönderilen e-postaları depolar ve doğrudan kanallara gönderilen e-postaları içermez.

Bazı durumlarda, posta kutusunda depolanan e-postalar toplantılar, Planner görev güncelleştirmeleri ve diğer uygulama veya sistem tarafından oluşturulan iletiler olabilir. İçeriğin orada depolanıp depolanmayacaklarını veya silinip silinmeyeceklerini belirlemek için posta kutusunun içeriğinin gözden geçirmesi önemlidir.

E-postalar ve takvim öğeleri Exchange, eBulma aramaları aracılığıyla korunur ve kullanılabilir.

**Posta ve takvimi dışarı aktarma**

Ekip veya grup üyeleri, posta kutusu ve takvimin içeriğini bir Outlook [Veri / Kişisel Depolama (PST) dosyasına aktarabilirsiniz](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91). Bu dosya daha sonra başka bir yerde depolanıyor olabilir veya içerikler başka bir posta kutusuna aktarabilir. PST dosyasının içeriği, dosyayı Outlook'ta açılmadan aranamaz olduğu ve zamanla dosyanın kendisi bozulabilir olduğu için, eski dosyanın kendisi önerilmez.

**IT tarafından gerçekleştirilen içerik geçişi**

Yöneticiler, kullanıcı müdahalesi olmadan e-postayı ve takvim içeriğini posta kutuları arasında geçirmek için üçüncü taraf araçlarını kullanabilir. Olası depolama konumlarından biri, yalnızca grup posta kutusu içeriğinin "arşivi" olarak hizmet verecek şekilde oluşturulmuş paylaşılan bir posta kutusu olabilir.

## <a name="planner"></a>Planner

Her grup veya ekibin birden fazla planı olabilir. Her bir planı saklama gereksinimlerinin karşı olduğundan emin olmak, uçuştan çıkar işlemi sırasında önemlidir. Diğer hizmetler gibi Planner'da da yer dışı içerik için çeşitli yaklaşımlar vardır.

**Planı elektronik tabloya aktarma**

Planın yalnızca kayıt tutma amacıyla bir kopyasını tutmanız gerekirse, en basit yaklaşım planı bir elektronik tablo için dışarı [Excel.](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a) Bu tek yol içeren bir eylemdir; elektronik tablodan plan aktarma seçeneği yoktur.

> [!IMPORTANT]
> Planı başka bir Excel, plan içinde bilgilerin çoğunu alır ancak açıklama, bağlantı veya dosya içermez.

**Görevleri başka bir Plana kopyalama ve taşıma**

Görevleri başka bir plana kopyalamak veya başka bir plana taşıma çözüm gibi görünüyorsa, tek tek görevler yalnızca [](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) aynı grup içindeki planlar arasında kopyalanamaz veya taşınabilirsiniz. Planla ilişkilendirilmiş grup silinirse, bu bilgi verileri korumaz.

**Planın tamamını kopyalama**

Ayrıca planın tamamını [kopyalamak da mümkündür](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Var olan bir gruba kopyalama yapılmaz. Planı kopyalamak yeni bir grup oluşturacak. Ayrıca, planın tamamı kopyalarda açıklamalar, ödevler, bağlantılar, ekler veya tarihler de yer almayacaktır.

## <a name="power-automate"></a>Power Automate

Özel grup Power Automate grup veya ekiple ilişkilendirilmiş akışlar gruba ait değil. Bunlar oluşturan kişi tarafından sahip olur ve yalnızca diğer kullanıcılar ve gruplarla paylaşılır. Bu nedenle, bir grup veya ekip silindiğinde bunlar etkilenmez.

**Akışın sahipliğini değiştirme**

Akışın çalışmaya devam olması gerekirse, tüm sahipler diğer kullanıcıları ekleyebilir veya Microsoft 365 olarak ekleyebilir.

**Akışı dışarı aktarma**

Akışın çalışmaya devam olması gerek yoksa, ancak gelecekte olası kullanım için korunması gerekirse, dosya olarak dışarı aktarıldı ve daha sonra yeniden [](https://flow.microsoft.com/blog/import-export-bap-packages/) aktarıldı.

## <a name="power-bi"></a>Power BI

Power BI ve çalışma alanları, gruplardan ve ekiplerden bağımsız olarak çalışabilir ve diğer iş yükleri gibi farklı iş yüklerinden bağımsız çalışabilir.

**Raporları başka bir çalışma alanına kopyalama**

Grup veya ekip silindikten sonra rapora ihtiyacınız olursa, grup veya ekip içindeki mevcut çalışma alanında bulunan başka [bir çalışma alanına Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Pano veya rapordan verileri dışarı aktarma**

Bunun yerine, raporun artık etkin olması gerekmeyecekse ancak verilerin muhafazası gerekirse, rapor başka bir [Excel](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Web için Web için Project'de oluşturulmuş projeler ve Yol Haritaları, Microsoft 365 gruplarıyla ilişkilendirilr ve benzer şekilde çıkarlıma yaklaşımları Power BI.

**Projeyi başka bir gruba atama**

Projenin, grubun veya ekibin ömrü dışında işlevsel durumda korunması gerekirse, farklı bir çalışma grubu Microsoft 365 [atanabilir](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Bu, Dynamics 365 Yönetim Merkezi kullanılarak yapılabilir.

**Proje veya yol haritasından verileri dışarı aktarma**

Dynamics 365 Yönetim Merkezi'nin kullanımıyla, kullanıcı verilerini [projeden](/project-for-the-web/export-user-data-from-project-for-the-web) bir elektronik tabloya aktarabilirsiniz. Veriler bir dosya (. Project aktarabilirsiniz. MPP) ve XML dosya biçimlerini PowerShell kullanarak kullanın.

## <a name="sharepoint"></a>SharePoint

Ekip kanallarında yer alan tüm dosyalar, SharePoint grubun ekip sitesinde depolanır. Bazı durumlarda, liste veya sayfa gibi belgelerde SharePoint başka içerikler olabilir.

Dosyalar genel olarak bir site içinde üç birincil SharePoint depolanır:

- Sayfalar - Site Sayfaları kitaplığı
- Sayfalarda kullanılan resimler – Site Varlıkları kitaplığı
- Kanallarda dosyalar – Belge kitaplığı
- Wiki sayfaları – Teams Wiki Verileri kitaplığına ekleme

Sitede bir veya daha fazla alt site varsa, her alt site için uçağa bindirma işleminin tekrarı gerekir. Ekip özel kanallar içeriyorsa, her kanal için ayrı SharePoint site vardır.

Bir grup veya ekipten dosya kaldırılırken, bunların grubun veya ekibin üyesi olmayan kullanıcılarla paylaşılıyor olduğunu göz önünde bulundurabilirsiniz. Yaklaşan değişikliği onlara iletirsiniz.

**Dosyaları indirme**

Yukarıda adı SharePoint kitaplıklardan bir kitaplıkta depolanan dosyalar [yerel bir bilgisayara indirilebilir](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Dosyaları taşıma**

Bunlara ek olarak, [dosyalar klasör içinde başka bir SharePoint bir kitaplık gibi farklı bir siteye de taşınabilirsiniz](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Listeyi dışarı aktarma**

Listelerde depolanan SharePoint bir elektronik tablo Excel [dışarı](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) aktarabilir ve başka bir siteden bir listeye yeniden aktarabilirsiniz.

Alternatif olarak, işlevi, liste görünümlerini, biçimlendirmeyi ve diğer öznitelikleri korumak için listeyi siteler arasında geçirmek için üçüncü taraf bir araç da kullanılabilir.

**Wiki dosyalarını "dışarı aktarma"**

Ekip kanalları içindeki wiki içeriği, ilgili sitenin özel bir kitaplığında HTML olarak biçimlendirilmiş bir SharePoint depolanır. Bunlar hazır bulunabilir ve başka bir kanal wiki'sini dışarı aktarılamaz, ancak HTML dosyasına  dönüştürülür ve web sayfası olarak açılabilir.

## <a name="microsoft-stream"></a>Microsoft Stream

Aynı Power Automate gibi, bir grup veya ekiple ilişkilendirilmiş Stream'de yer alan videolar da gruba ait olduğu gibi, grup silindiğinde de silinmez. Stream'de videolar, kullanıcıları veya grupları sahip olarak ekleseler bile videoyu karşıya yük eden veya oluşturan kişiye aittir. Bir kayıt Teams kaydedilen toplantılar, kaydı başlatan kişiye aittir.

**Diğer sahipleri ekleme**

Video, grup silindiğinde Stream'de korunsa da, özgün sahibi videoyu diğer kullanıcılar ve gruplarla paylaşabilir, hatta bunları sahip [olarak ekler](/stream/portal-edit-video).

**Videoyu indirin**

Videonun Stream'de depolandığı veya kayıt yönetim sistemi gibi alternatif bir konumda depolandığı senaryolarda, videonun sahibi bunu yerel [olarak indirebilir](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

Microsoft Teams'daki Yammer, hem kullanıcılara hem de yöneticilere konuşmaları taşıma veya dışarı aktarma seçenekleri sunar.

**Konuşmaları başka bir gruba veya gruba taşıma**

Sadece sahipler veya yöneticiler Yammer, herhangi bir kullanıcı tarafından konuşmalar başka bir grup gruba taşınmalıdır. Bu hem klasik arabirimlerde [hem Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872) [yeni kullanıcı arabirimlerinde Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) mümkündür.

**Ağ verilerini dışarı aktarma**

Yammer yöneticilerinin ağ [verilerini dışarı aktarması gerekir](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Bununla birlikte, bunu yapmak tüm ağ için tüm konuşmaları dışarı aktaracak. Sonuçta elde edilen dışarı aktarmada Grup Kimliği listelemektedir. Konuşmaları bu kimlik tabanlı olarak filtrelemek mümkündür.

## <a name="related-topics"></a>İlgili konular

[Eski çalışanı kaldırma ve verilerin güvenliğini sağlama](/microsoft-365/admin/add-users/remove-former-employee)
