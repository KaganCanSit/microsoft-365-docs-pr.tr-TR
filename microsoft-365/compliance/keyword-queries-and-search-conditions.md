---
title: eKbulma için anahtar sözcük sorguları ve arama koşulları
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SearchQueryLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: c4639c2e-7223-4302-8e0d-b6e10f1c3be3
ms.custom:
- seo-marvel-apr2020
description: E-posta ve belge özellikleri hakkında, çalışma sayfalarındaki eBulma arama araçlarını kullanarak Microsoft 365.
ms.openlocfilehash: 390d0721dc5b256da224c70573953e23bbb91225
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010024"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>eKbulma için anahtar sözcük sorguları ve arama koşulları

Bu makalede, Exchange Online'te e-posta öğelerinde ve Microsoft Teams'te sohbet görüşmelerini, SharePoint ve OneDrive İş sitelerinde depolanan belgeleri bulmak için, Microsoft 365 uyumluluk merkezi. Buna İçerik arama, Çekirdek eKbulma ve Advanced eDiscovery (Advanced eDiscovery'daki eBulma aramaları *koleksiyon olarak denir) dahildir*. Bu özellikleri aramak için Güvenlik **ve\* Uyumluluk** Merkezi PowerShell'& -ComplianceSearch cmdlet'lerini de kullanabilirsiniz. Bu makalede ayrıca şu da açıklanmıştır:

- Arama sonuçlarınızı iyileştirmek için Boole arama işleçlerini, arama koşullarını ve diğer arama sorgusu tekniklerini kullanma.
- Hassas veri türlerini ve özel hassas veri türlerini aynı dosya ve SharePoint OneDrive İş.
- Kuruluş dışındaki kullanıcılarla paylaşılan site içeriğini arama

Farklı eBulma aramaları oluşturmayla ilgili adım adım yönergeler için bkz:

- [İçerik arama](content-search.md)
- [Core eDiscovery'de içerik arama](search-for-content-in-core-ediscovery.md)
- [Web'de taslak Advanced eDiscovery](create-draft-collection.md)

> [!NOTE]
> eBulma, Güvenlik Microsoft 365 uyumluluk merkezi **\*** Uyumluluk Merkezi PowerShell'de Microsoft 365 uyumluluk merkezi-ComplianceSearch cmdlet'lerinde Anahtar Sözcük Sorgu Dili'& Kullanır. Daha ayrıntılı bilgi için bkz. [Anahtar Sözcük Sorgusu Dili söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

## <a name="searchable-email-properties"></a>Aranabilir e-posta özellikleri

Aşağıdaki tabloda, Microsoft 365 uyumluluk merkezi'de eBulma arama araçları kullanılarak veya Yeni Uyumluluk Arama veya **Set-ComplianceSearch** cmdlet'i kullanılarak aranacak **e-posta** iletisi özellikleri listelemektedir. Tabloda, her özellik için  _özellik:değer söz_ dizimi örneği ve örnekler tarafından döndürülen arama sonuçlarının açıklaması yer alır. Bu çiftleri  `property:value` bir eBulma arama anahtar sözcükleri kutusuna yazın.

> [!NOTE]
> E-posta özelliklerinde arama yapmak, belirtilen özelliği boş veya boş olan öğeler için arama yapmak mümkün değildir. Örneğin, konu satırı boş *olan e-posta* iletilerini aramak için **konu:""** özelliğinin:değer çifti değerinin kullanımı sıfır sonuçları verir. Bu durum site ve kişi özellikleri için de geçerlidir.

|Özellik|Özellik açıklaması|Örnekler|Örnekler tarafından döndürülen arama sonuçları|
|---|---|---|---|
|AttachmentNames|E-posta iletisine eklenmiş dosyaların adları.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|Dosya adında ekli bir dosya annualreport.ppt. İkinci örnekte, joker karakterin ( * ) kullanımı, ekin dosya adı altında "yıllık" sözcüğü olan iletileri döndürür. Üçüncü örnekte pptx dosya uzantısına sahip tüm ekler döndürür.|
|Gizli|E-posta iletisine ait Gizli alanı. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|Tüm örnekler, Gizli alanında Pilar Pinilla bulunan iletileri geri göndermez.|
|Kategori|Aranecek kategoriler. Kategoriler, kullanıcı tarafından kategori Outlook veya Web üzerinde Outlook (eski adıyla Outlook Web App). Olası değerler: <ul><li>mavi<li>yeşil<li>turuncu<li>mor<li>kırmızı<li>sarı</li></ul>|`category:"Red Category"`|Kaynak posta kutularında kırmızı kategoriye atanmış iletiler.|
|Bilgi|E-posta iletisi bilgi alanı. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|Her iki örnekte de, Bilgi alanında Pilar Pinilla ile belirtilen iletiler.|
|Folderid|Belirli bir posta kutusu klasörünün klasör kimliği (GUID). Bu özelliği kullanıyorsanız, belirtilen klasörün bulunduğu posta kutusunda arama yapmak için emin olun. Yalnızca belirtilen klasörde arama  aranacak. Klasördeki alt klasörlerde arama olmayacak. Alt klasörlerde arama yapmak için, aramak istediğiniz alt klasörün Folderid özelliğini kullansanız gerekir. <p> Folderid özelliğini arama ve betiği kullanarak belirli bir posta kutusunun klasör kimliklerini alma hakkında daha fazla bilgi için bkz. Hedefli koleksiyonlar için [İçerik arama özelliğini kullanma](use-content-search-for-targeted-collections.md).|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|İlk örnekte, belirtilen posta kutusu klasöründeki tüm öğeler döndürür. İkinci örnekte, belirtilen posta kutusu klasöründe yer alan ve posta kutusu tarafından gönderilmiş veya garthf@contoso.com.|
|Kaynak|E-posta iletisi gönderen. <sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Belirtilen kullanıcı tarafından gönderilen veya belirtilen etki alanından gönderilen iletiler.|
|HasAttachment|İletinin eki olup olmadığını gösterir. Doğru veya **yanlış** değerlerini **kullanın**.|`from:pilar@contoso.com AND hasattachment:true`|Belirtilen kullanıcı tarafından gönderilen ve ekleri olan iletiler.|
|Önem|E-posta iletisi gönderirken gönderenin belirtebilirsiniz. Varsayılan olarak iletiler, gönderenin önem ayarlarını yüksek veya düşük olarak olmadığı sürece normal **öneme sahip** olarak **gönderilir**.|`importance:high` <p> `importance:medium` <p> `importance:low`|Yüksek önem derecesi, orta önem derecesi veya düşük öneme sahip olarak işaretlenmiş iletiler.|
|IsRead|İletilerin okundu olup olmadığını gösterir. Doğru veya **yanlış** değerlerini **kullanın**.|`isread:true` <p> `isread:false`|İlk örnekte, IsRead özelliği True olarak ayarlanmış iletiler **döndürür**. İkinci örnekte IsRead özelliği False olarak ayarlanmış iletiler **döndürür**.|
|ItemClass|Bu özelliği kullanarak, kuruluş tarafından üçüncü taraf verilerine aktarılmış belirli veri türlerinde Office 365. Bu özellik için aşağıdaki söz dizimlerini kullanın:  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|İlk örnekte, Konu özelliğinde "contoso" sözcüğü geçen Facebook öğeleri döndürür. İkinci örnekte, Ann Beebe tarafından gönderilen ve "Northwind Traders" anahtar sözcüğünü içeren Twitter öğeleri döndürür. <p> ItemClass özelliği için üçüncü taraf veri türlerinde kullanmak üzere değerlerin tam listesi için bkz. öğeye aktarılmış olan üçüncü taraf verilerinde arama yapmak için [İçerik Office 365](use-content-search-to-search-third-party-data-that-was-imported.md).|
|Tür|Aranan e-posta iletisi türü. Olası değerler: <p>  kişiler <p>  belgeler <p>  E-posta <p>  dış veriler <p>  fakslar <p>  im <p>  günlükler <p>  toplantılar <p>  microsoftteams (ekip arkadaşlarınızdaki sohbetlerden, toplantılardan ve çağrılardan Microsoft Teams) <p>  notlar <p>  gönderiler <p>  rssfeeds <p>  görevler <p>  sesli mesaj|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|İlk örnekte, arama ölçütlerine uyan e-posta iletileri döndürür. İkinci örnekte e-posta iletileri, anlık ileti konuşmaları (Skype Kurumsal'ta yapılan konuşmalar ve Microsoft Teams sohbetler dahil) ve arama ölçütlerine uyan sesli mesajlar geri gönderilir. Üçüncü örnekte, Twitter, Facebook ve Cisco Microsoft 365 gibi üçüncü taraf veri kaynaklarından arama ölçütlerine uyan posta kutularına aktarılmış olan öğeler sonuç olarak gelir. Daha fazla bilgi için bkz[. Bu dosyalarda üçüncü taraf verilerini Office 365](https://www.microsoft.com/?ref=go).|
|Katılımcılar|E-posta iletisinde tüm kişiler alanları. Bu alanlar Ilk, Son, Bilgi ve <sup>Gizli'dir.1</sup>|`participants:garthf@contoso.com` <p> `participants:contoso.com`|Posta ile gönderilen veya bu postaya garthf@contoso.com. İkinci örnekte, bu etki alanında bir kullanıcı tarafından gönderilen veya bu kullanıcıya contoso.com döndürür.|
|Alındı|E-posta iletisi alıcı tarafından alınmıştır.|`received:2021-04-15` <p> `received>=2021-01-01 AND received<=2021-03-31`|15 Nisan 2021'de alınan iletiler. İkinci örnekte, 1 Ocak 2021 ile 31 Mart 2021 arasında alınan tüm iletiler döndürür.|
|Alıcılar|E-posta iletisinde tüm alıcı alanları. Bu alanlar To, Bilgi ve <sup>Gizli'dir.1</sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|İletiler garthf@contoso.com. İkinci örnekte, bu etki alanındaki herhangi bir alıcıya contoso.com döndürür.|
|Gönderildi|Gönderen tarafından e-posta iletisi gönderildiği tarih.|`sent:2021-07-01` <p> `sent>=2021-06-01 AND sent<=2021-07-01`|Belirtilen tarihte gönderilmiş veya belirtilen tarih aralığı içinde gönderilmiş iletiler.|
|Boyut|Bir öğenin boyutu bayt cinsinden.|`size>26214400` <p> `size:1..1048567`|25 MB'den büyük iletiler. İkinci örnekte, boyutu 1 ile 1.048.567 bayt (1 MB) arasında olan iletiler döndürür.|
|Konu|E-posta iletisi konu satırı metindir. <p> **Not:** Sorguda Konu özelliğini kullanırsanız, arama, konu satırı için aramada aray istediğiniz metni içeren tüm iletileri döndürür. Başka bir deyişle, sorgu yalnızca tam eşleşmesi olan iletileri geri göndermez. Örneğin, için arama yaptıysanız  `subject:"Quarterly Financials"`, sonuçlarınız "Üç Aylık Finansallar 2018" konusunu içeren iletileri içerir.|`subject:"Quarterly Financials"` <p> `subject:northwind`|Konu satırı metninin herhangi bir yerinde "Üç Aylık Finansallar" ifadesini içeren iletiler. İkinci örnekte, konu satırlarında Northwind sözcüğü geçen tüm iletiler döndürür.|
|Hedef|E-posta iletisine gelen To alanı. <sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Tüm örnekler, Ann Beebe'nin To: satırı içinde belirtilen iletiler olarak geri döner.|

> [!NOTE]
> <sup>1</sup> Alıcı özelliğinin değeri için, kullanıcı belirtmek üzere e-posta adresini (kullanıcı asıl adı  veya UPN olarak da adlandırılan), görünen ad veya diğer adı kullanabilirsiniz. Örneğin, Ann Beebe annb@contoso.com, annb veya "Ann Beebe" kullanabilirsiniz.

### <a name="recipient-expansion"></a>Alıcı genişletme

Alıcı özelliklerinin herhangi birini (Kaynak, To, Bilgi, Gizli, Katılımcılar ve Alıcılar) ararken Microsoft 365, kullanıcı kimliğini Azure Active Directory Azure Active Directory azure AD) genişletmeye çalışır.  Kullanıcı Azure AD'de bulunursa, sorgu kullanıcının e-posta adresini (veya UPN),diğer adını, görünen adı ve LegacyExchangeDN'yi içerecek şekilde genişletilir. Örneğin, gibi bir sorgu `participants:ronnie@contoso.com` için genişletilen `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"`.

Alıcı genişletmesini önlemek için, e-posta adresinin sonuna bir joker karakter (yıldız işareti) ekleyin ve etki alanı adı azalır; Örneğin, e-posta `participants:"ronnie@contoso*"` adresinin çift tırnak içine alınmaya dikkat edin.

Ancak, alıcıya arama sorgusunun genişletilmesi önlenebilir ve bunun sonucunda arama sonuçlarında ilgili öğelerin döndürüleyebilirsiniz. E-posta Exchange alıcı alanlarında farklı metin biçimleriyle kaydedilebilir. Alıcı genişletmesi, farklı metin biçimlerine sahip iletiler döndürerek bu gerçeğin azaltmak için tasarlanmıştır. Bu nedenle alıcı genişletmesinin önlenmesi, arama sorgusunun araştırmanıza uygun tüm öğeleri döndürene kadar geri dönmesine neden olabilir.

> [!NOTE]
> Alıcı genişletmesi nedeniyle arama sorgusunun döndürülen öğeleri gözden geçirmesi veya azaltmanız gerekirse, Sorgular'ı Advanced eDiscovery. İletileri arayabilir (alıcı genişletme özelliğiden yararlanmak için), bunları gözden geçirme kümesine ekleyebilir ve sonra da sonuçları gözden geçirmek veya daraltmak için gözden geçirme kümesi sorgularını veya filtrelerini kullanabilirsiniz. Daha fazla bilgi için bkz [. Olay için veri toplama](collecting-data-for-ediscovery.md) [ve Gözden geçirme kümesinde verileri sorgulama](review-set-search.md).

## <a name="searchable-site-properties"></a>Aranabilir site özellikleri

Aşağıdaki tabloda, Microsoft 365 Uyumluluk Merkezi'nde eBulma arama araçları kullanılarak veya Yeni Uyumluluk Arama veya **Set-ComplianceSearch** cmdlet'i kullanılarak aranacak SharePoint ve OneDrive İş özelliklerinin bazıları listelemektedir. Tabloda, her özellik için  _özellik:değer söz_ dizimi örneği ve örnekler tarafından döndürülen arama sonuçlarının açıklaması yer alır.

Aramanın da SharePoint tam listesi için bkz. SharePoint'de [gezinilen ve yönetilen özelliklere genel SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Sorgulanabilir sütununda **Evet** ile **işaretlenmiş özelliklerde** arama olabilir.

|Özellik|Özellik açıklaması|Örnek|Örnekler tarafından döndürülen arama sonuçları|
|---|---|---|---|
|Yazar|Belgelerden yazar Office alanı; belge kopyalanırsa kalıcı olur. Örneğin, bir kullanıcı belgeyi oluşturur ve bu belgeyi başka birine e-postayla gönderdikten sonra SharePoint, belge özgün yazarı korur. Bu özellik için kullanıcının görünen adını kullanmaya emin olun.|`author:"Garth Fort"`|Garth Fort tarafından kaleme alan tüm belgeler.|
|ContentType|SharePoint, Belge veya Video gibi bir öğenin içerik türü kullanılır.|`contenttype:document`|Tüm belgeler döndürülecek.|
|Oluşturuldu|Öğenin oluşturulma tarihi.|`created>=2021-06-01`|1 Haziran 2021 veya daha sonra oluşturulan tüm öğeler.|
|CreatedBy|Öğeyi oluşturan veya karşıya yük alan kişi. Bu özellik için kullanıcının görünen adını kullanmaya emin olun.|`createdby:"Garth Fort"`|Garth Fort tarafından oluşturulan veya yüklenen tüm öğeler.|
|DetectedLanguage|Öğenin dili.|`detectedlanguage:english`|Tüm İngilizce öğeler.|
|DocumentLink|Sitedeki veya sitedeki belirli bir klasörün SharePoint (URL OneDrive İş. Bu özelliği kullanıyorsanız, belirtilen klasörün bulunduğu sitede arama yapmak için emin olun. <p> Documentlink özelliği için belirttiğiniz klasörün alt klasörlarında yer alan öğeleri geri almak için, belirtilen klasörün URL'sini /\* eklemeniz gerekir; örneğin, `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Belirli bir sitedeki klasörler için belge bağlantısı URL'lerini almak üzere documentlink özelliğini arama ve betik kullanma hakkında daha fazla bilgi için bkz. Hedefli koleksiyonlar için [İçerik arama özelliğini kullanma](use-content-search-for-targeted-collections.md).|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|İlk örnekte, belirtilen veri klasöründeki tüm OneDrive İş döndürür. İkinci örnekte, belirtilen site klasöründe (ve tüm alt klasörlerde) dosya adının "gizli" sözcüğü geçen belgeleri döndürür.|
|FileExtension|Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx.|`fileextension:xlsx`|Tüm Excel (Excel 2007 ve sonrası)|
|FileName|Dosyanın adı.|`filename:"marketing plan"` <p> `filename:estimate`|İlk örnekte, başlığında tam olarak "pazarlama planı" tümceciği olan dosyalar döndürür. İkinci örnekte, dosya adının içinde "tahmin" sözcüğü olan dosyalar döndürür.|
|LastModifiedTime|Bir öğenin son değiştir bitiş tarihi.|`lastmodifiedtime>=2021-05-01` <p> `lastmodifiedtime>=2021-05-01 AND lastmodifiedtime<=2021-06-01`|İlk örnekte, 1 Mayıs 2021'de veya daha sonra değiştirilmiş öğeler döndürür. İkinci örnekte, 1 Mayıs 2021 ile 1 Haziran 2021 arasında değişen öğeler döndürür.|
|ModifiedBy|Öğeyi en son değiştiren kişi. Bu özellik için kullanıcının görünen adını kullanmaya emin olun.|`modifiedby:"Garth Fort"`|En son Garth Fort tarafından değiştirilen tüm öğeler.|
|Yol|Site içinde belirli bir sitenin yolu (URL SharePoint OneDrive İş. <p> Yalnızca belirtilen siteden öğeler iade etmek için, `/` URL'nin sonuna sonuna sonda eklemelisiniz; örneğin, `path: "https://contoso.sharepoint.com/sites/international/"` <p> Yol özelliğinde belirttiğiniz sitedeki klasörlerde yer alan öğeleri geri dönmek için, `/*` URL'nin sonuna eklemeniz gerekir; örneğin,  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Not:** Konumlarda `Path` arama OneDrive özelliği kullanılırsa, arama sonuçlarında .png, .tiff veya .wav gibi medya dosyaları geri dönmez. Dosya veya klasörlerin içinde medya dosyaları aramak için, arama sorgunuza farklı bir site OneDrive kullanın. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|İlk örnekte, belirtilen sitedeki tüm OneDrive İş döndürür. İkinci örnekte, belirtilen sitede (ve sitedeki klasörlerde) dosya adı altında "gizli" sözcüğü geçen belgeler döndürür.|
|SharedWithUsersOWSUser|Belirtilen kullanıcıyla paylaşılan ve kullanıcının sitenin Benimle paylaşılan sayfasında gösterilen belgeler  OneDrive İş. Bunlar, belirtilen kullanıcıyla kuruluşta yer alan diğer kişiler tarafından açıkça paylaşılan belgelerdir. SharedWithUsersOWSUser özelliğini kullanan bir arama sorgusuyla eşleşmeye sahip belgeleri dışarı aktarabilirsiniz, belgeler belgeyi belirtilen kullanıcıyla paylaşan kişinin özgün içerik konumdan dışarı aktarılır. Daha fazla bilgi için bkz [. Kuruluş içinde paylaşılan site içeriğini arama](#searching-for-site-content-shared-within-your-organization).|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Her iki örnek de, Garth Fort ile açıkça paylaşılan ve Garth Fort'un şirket hesabı'nın  Benimle paylaşılan sayfasında görünen tüm iç OneDrive İş getirmektedir.|
|Site|Bir sitenin veya bir site grubunun url'si.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|İlk örnekte, çalışma OneDrive İş tüm kullanıcılar için bu sitelerden öğeler döndürür. İkinci örnekte tüm ekip sitelerinden öğeler geri gelir.|
|Boyut|Bir öğenin boyutu bayt cinsinden.|`size>=1` <p> `size:1..10000`|İlk örnekte 1 baytan büyük öğeler döndürür. İkinci örnekte, boyutu 1 ile 10.000 bayt arasında olan öğeler döndürür.|
|Başlık|Belgenin başlığı. Başlık özelliği, bu belgelerde belirtilen meta Microsoft Office kullanılır. Belgenin dosya adıyla farklı.|`title:"communication plan"`|Bir belgeye ait Başlık meta veri özelliğinde "iletişim planı" tümceciğinin yer Office.|

## <a name="searchable-contact-properties"></a>Aranabilir kişi özellikleri

Aşağıdaki tabloda dizine alan kişi özellikleri ve eBulma arama araçlarını kullanarak arama yapabilirsiniz. Bunlar, kullanıcıların posta kutusunun kişisel adres defterine yer alan kişiler (kişisel kişiler olarak da denir) için yapılandırılan özelliklerdir. Kişileri aramak için, aranarak posta kutularını seçerek anahtar sözcük sorgusunda bir veya birden çok kişi özelliğini kullanabilirsiniz.

> [!TIP]
> Boşluk veya özel karakter içeren değerleri aramak için, tümceciği içeren çift tırnak (" ") kullanın; örneğin, `businessaddress:"123 Main Street"`.

|Özellik|Özellik açıklaması|
|---|---|
|BusinessAddress|İş Adresi **özelliğinde adres** . Bu özellik, kişi özellikleri **sayfasındaki** İş adresi olarak da adlandırılan özelliktir.|
|BusinessPhone|İş numarası özelliklerinde herhangi **bir Telefon** numarası.|
|ŞirketAdı|Şirket **özelliğinde ad** .|
|Bölüm|Department özelliğinde **ad** .|
|DisplayName|Kişinin görünen adı. Bu, kişinin Tam **Ad özelliğinde** yer alan addır.|
|EmailAddress|Kişinin herhangi bir e-posta adresi özelliğinin adresi. Kullanıcılar bir kişi için birden çok e-posta adresi ekleyebilir. Bu özelliğin kullanımı, kişinin e-posta adreslerinde yer alan kişileri geri gönderebilirsiniz.|
|FileAs|Dosya **özelliği** . Bu özellik, kişinin kullanıcının kişi listesinde nasıl listelenmiş olduğunu belirtmek için kullanılır. Örneğin, bir kişi Ad, Soyadı  *veya Soyadı,Ad*  *olarak listelenmiş olabilir*.|
|GivenName|Ad **özelliğinde ad** .|
|HomeAddress|Herhangi bir Giriş adresi **özelliğinde bulunan** adres.|
|Ev Telefonu|Herhangi bir Ev telefonu numarası **özelliğinde** yer alan telefon numarası.|
|IMAddress|Anlık ileti için kullanılan bir e-posta adresi olan anlık ileti adresi özelliğidir.|
|MiddleName|Ad **özelliğinde ad** .|
|MobilePhone|Cep telefonu numarası **özelliğinde** telefon numarası.|
|Takma ad|Takma Ad **özelliğinde ad** .|
|OfficeLocation|Konum özelliği **Office** **Office değerdir**.|
|OtherAddress|Diğer adres **özelliğinin** değeri.|
|Surname|Soyadı **özelliğinde** ad.|
|Başlık|İş unvanı **özelliğinde başlık** .|

## <a name="searchable-sensitive-data-types"></a>Aranabilir hassas veri türleri

Microsoft 365 uyumluluk merkezi'ta ve başka sitelerde depolanan kredi kartı numaraları veya sosyal güvenlik numaraları gibi hassas verileri aramak için SharePoint'daki eBulma arama araçlarını OneDrive İş kullanabilirsiniz. Bir anahtar sözcük sorgusunda, hassas `SensitiveType` bir bilgi türünün özelliğini ve adını (veya kimliğini) kullanarak bunuabilirsiniz. Örneğin, sorgu kredi `SensitiveType:"Credit Card Number"` kartı numarası içeren belgeleri döndürür. Sorgu,  `SensitiveType:"U.S. Social Security Number (SSN)"` ABD sosyal güvenlik numarasını içeren belgeleri döndürür.

Arayabilirsiniz hassas bilgi türlerinin listesini görmek için,  \> Aşağıdaki listede Veri sınıflandırmaları Hassas **bilgi türleri'ne** Microsoft 365 uyumluluk merkezi. Hassas bilgi türlerinin listesini görüntülemek için Güvenlik ve Uyumluluk Merkezi PowerShell'de **Get-DlpSensitiveInformationType** cmdlet'ini & da kullanabilirsiniz.

Özelliği kullanarak sorgu oluşturma hakkında daha fazla bilgi için `SensitiveType` bkz. [Sitelerde depolanan hassas verileri bulmak için sorgu oluşturma](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Hassas veri türlerini arama sınırlamaları

- Özel hassas bilgi türlerini aramak için, özellikte hassas bilgi türünün kimliğini belirtmeniz `SensitiveType` gerekir. Özel bir hassas bilgi türünün adı (önceki bölümdeki yerleşik hassas bilgi türleri için de gösterildiği gibi) hiçbir sonuç dönmez. Yerleşik **Publisher** özel hassas bilgi türlerini ayırt etmek için  uyumluluk merkezi sayfasının Hassas bilgi türleri sayfasındaki Hassas bilgi sütununu (veya **PowerShell'Publisher'daki Publisher** özelliğini) kullanın. Yerleşik hassas veri türlerinin özellik değeri, `Microsoft Corporation` değer **Publisher** vardır.

  Özel hassas veri türlerinin adını ve kimliğini görüntülemek için Güvenlik ve Uyumluluk Merkezi PowerShell'de & çalıştırın:

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Daha sonra arama özelliğinde `SensitiveType` kimliği kullanarak özel duyarlı veri türünü içeren belgeleri getirebilirsiniz; örneğin, `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Hassas bilgi türlerini ve arama özelliğini, belirli `SensitiveType` bir posta kutusunda kalan hassas verileri aramak için Exchange Online yoktur. Bu içeriklerin hepsi posta kutularında depolandığı için Microsoft Teams'da 1:1 sohbet iletileri, 1:N grup sohbeti iletileri ve ekip kanalı konuşmaları yer almaktadır. Bununla birlikte, geçişte hassas e-posta verilerini korumak için veri kaybı önleme (DLP) ilkelerini kullanabilirsiniz. Daha fazla bilgi için bkz [. Veri kaybını önleme ve Kişisel](dlp-learn-about-dlp.md) [verileri arama ve bulma](/compliance/regulatory/gdpr).

## <a name="search-operators"></a>Arama işleçleri

**VE**, **VEYA** ve NOT gibi Boole arama işleçleri **, arama** sorgusuna belirli sözcükleri dahillayarak veya hariç tutarak daha hassas aramalar tanımlamanıza yardımcı olur. Özellik işleçlerini (`>=``..`veya gibi), tırnak işaretlerini, ayraçları ve joker karakterleri kullanma gibi diğer teknikler, arama sorgusunu geliştirmenizi sağlar. Aşağıdaki tabloda, arama sonuçlarını daraltmak veya daraltmak için kullanabileceğiniz işleçler liste almaktadır.

|İşleç|Kullanım|Açıklama|
|---|---|---|
|VE|anahtar sözcük1 VE anahtar sözcük2|Belirtilen tüm anahtar sözcükleri veya ifadeleri içeren öğeleri  `property:value` döndürür. Örneğin,  `from:"Ann Beebe" AND subject:northwind` Ann Beebe tarafından gönderilen ve konu satırlarında Northwind sözcüğü geçen tüm iletilerin dönebilirsiniz. <sup>2</sup>|
|+|anahtar sözcük1 + anahtar sözcük2 + anahtar sözcük3|Veya içeren  *ve aynı*  `keyword2` zamanda  `keyword3` *da*  bulunan öğeleri döndürür  `keyword1`. Bu nedenle, bu örnek sorguyla eşdeğerdir  `(keyword2 OR keyword3) AND keyword1`. <p> `keyword1 + keyword2` Sorgu (simgeden sonra boşlukla **+**), AND işlecinin kullanımıyla **aynı değildir**. Bu sorgu, öğeleri tam aşamasıyla  `"keyword1 + keyword2"` eşdeğer olacak ve geri gönderebilirsiniz  `"keyword1 + keyword2"`.|
|VEYA|anahtar sözcük1 VEYA anahtar sözcük2|Belirtilen anahtar sözcüklerden veya ifadelerden birini veya birden fazlasını içeren  `property:value` öğeleri döndürür. <sup>2</sup>|
|NOT|anahtar sözcük1 NOT anahtar sözcük2 <p> NOT from:"Ann Beebe" <p> NOT kind:im|Anahtar sözcük veya ifade ile belirtilen öğeleri dışlar  `property:value` . İkinci örnekte, Ann Beebe tarafından gönderilen iletiler hariçtir. Üçüncü örnekte, Konuşma Geçmişi posta kutusu klasörüne kaydedilen Skype Kurumsal konuşmalar gibi anlık ileti konuşmaları dahil değildir. <sup>2</sup>|
|-|anahtar sözcük1 -anahtar sözcük2|**NOT işleciyle aynıdır**. Dolayısıyla bu sorgu, 'i içeren öğeleri içeren  `keyword1` ve hariç tutmak istediğiniz öğeleri döndürür  `keyword2`.|
|NEAR|anahtar sözcük1 NEAR(n) anahtar sözcük2|Birbirinin yakınında olan sözcüklerin bulunduğu öğeleri döndürür ve burada n sözcük sayısı olarak apart sözcük sayısına eşittir. Örneğin, " `best NEAR(5) worst` en kötü" sözcüğünü "en iyi" sözcüğünü beş sözcük içinde döndüren herhangi bir öğeyi döndürür. Hiçbir sayı belirtilmezse, varsayılan mesafe sekiz sözcük olur. <sup>2</sup>|
|:|property:value|İki nokta üst üste (:) söz dizimsinde  `property:value` , aranacak özelliğin değeri belirtilen değeri içerir. Örneğin, iletiye  `recipients:garthf@contoso.com` gönderilen tüm garthf@contoso.com.|
|=|property=value|**: işleciyle aynıdır**.|
|\<|özelliksayisi\<|Arama özelliğinin belirtilen değerden az olduğunu unutmayın. <sup>1</sup>|
|\>|özelliksayisi\>|Arama özelliğinin belirtilen değerden büyük olduğunu unutmayın. <sup>1</sup>|
|\<=|property\<=value|Arama özelliğinin belirli bir değerden küçük veya eşit olduğunu unutmayın. <sup>1</sup>|
|\>=|property\>=value|Arama özelliğinin belirli bir değerden büyük veya eşit olduğunu unutmayın. <sup>1</sup>|
|..|property:değer1.. değer2|Arama özelliğinin değer1'den büyük veya eşit ve değer2'ye eşit veya daha küçük olduğunu unutmayın. <sup>1</sup>|
|"  "|"adil değer" <p> konu:"Çeyreklik Mali Durumlar"|Bir anahtar sözcük sorgusunda (Anahtar `property:value` sözcük kutusuna çifti yazın), tam bir tümcecik veya terim aramak için çift tırnak işareti (" ") kullanın. Bununla birlikte, Konu veya Konu  **/** [](#search-conditions) Başlık arama koşulu koşulu kullanıyorsanız, bu arama koşulları kullanırken otomatik olarak tırnak işaretleri eklendi olduğundan değere çift tırnak işareti eklemeyin. Değere tırnak işareti eklersiniz, koşul değerine iki çift tırnak çifti eklenir ve arama sorgusu hata döndürür. |
|\*|kedi\* <p> konu:set\*|Önek aramaları ( *önek eşleştirme olarak* da adlandırılan) burada, anahtar sözcükler veya sorgularda bir sözcüğün sonuna joker karakter ( * ) `property:value` yerleştirilir. Ön ek aramalarında, arama sonucunda sözcüğü içeren terimler ve ardından sıfır veya daha çok karakter gelir. Örneğin, belge `title:set*` başlığında "ayarla", "kurulum" ve "ayar" sözcüklerini (ve "küme" ile baş geçen diğer sözcükleri) içeren belgeleri döndürür. <p> **Not:** Yalnızca ön ek aramaları kullanabilirsiniz; örneğin, **kedi\**_ veya _* set\**_. Sonek aramaları (_*\*kedi**), infix aramaları (**ct\***) ve alt dize aramaları (**\*kedi\***) desteklemez. <p> Ayrıca, nokta ( \. ) önek arama sonucu döndürülen sonuçları değiştirir. Çünkü nokta, durma sözcüğü olarak kabul edilir. Örneğin, kedi **_ için\* *arama ve _* cat arama.\*** farklı sonuçlar verir. Bir ön ek aramada nokta kullanmamanızı öneririz.|
|(  )|(fair OR free) VE (from:contoso.com) <p> (IPO VEYA baş harfi) VE (hisse senedi VEYA paylaşımlar) <p> (üç aylık finansallar)|Parantezler, Boole tümcecikleri, öğeleri ve anahtar sözcükleri  `property:value` bir arada grup sağlar. Örneğin, üç  `(quarterly financials)` aylık ve finansal sözcükleri içeren öğeleri döndürür.|

> [!NOTE]
> <sup>1</sup> Tarih veya sayısal değerlere sahip özellikler için bu işleci kullanın.<br/> <sup>2</sup> Boole arama işleçleri büyük harf olmalıdır; örneğin, **VE**. Ve gibi küçük harf işleci kullanırsanız **, arama** sorgusunda anahtar sözcük olarak kabul edilir.

## <a name="search-conditions"></a>Arama koşulları

Bir arama daraltmak ve daha daraltılmış bir sonuç kümesi geri dönmek için, arama sorgusuna koşullar ebilirsiniz. Her koşul, oluşturulan ve aramayı başlatarak çalıştırılan KQL arama sorgusuna bir yan tümce ekler.

[Ortak özellikler için koşullar](#conditions-for-common-properties)

[Posta özellikleri koşulları](#conditions-for-mail-properties)

[Belge özellikleri koşulları](#conditions-for-document-properties)

[Koşullarla kullanılan işleçler](#operators-used-with-conditions)

[Koşulları kullanma yönergeleri](#guidelines-for-using-conditions)

[Arama sorgularında koşullar kullanma örnekleri](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Ortak özellikler için koşullar

Aynı aramada posta kutularını ve siteleri ararken ortak özellikleri kullanarak bir koşul oluşturun. Aşağıdaki tabloda, koşul eklerken  kullanmak üzere kullanılabilir özellikler listeledir.

|Koşul|Açıklama|
|---|---|
|Tarih|E-posta için, iletinin bir alıcı tarafından veya gönderen tarafından gönderildiği tarihtir. Belgeler için, belgenin son değiştirilma tarihidir.|
|Gönderen/Yazar|E-posta için, iletiyi gönderen kişidir. Belgeler için, yazar alanında adı geçen kişi Office içerir. Virgülle ayırarak birden çok ad yazın. İki veya daha fazla değer OR işleci tarafından mantıksal **olarak bağlantılıdır** .|
|Boyut (bayt cinsinden)|Hem e-posta hem de belgeler için, öğenin boyutu (bayt cinsinden).|
|Konu/Başlık|E-posta için, iletinin konu satırı metindir. Belgeler için, belgenin başlığı. Daha önce de belirtildiği gibi Başlık özelliği, bu belgelerde belirtilen Microsoft Office veridir. Birbirinden virgülle ayırarak birden çok konu/başlık değeri adı yazın. İki veya daha fazla değer OR işleci tarafından mantıksal **olarak bağlantılıdır** . <p> **Not**: Bu arama koşulu kullanılırken otomatik olarak tırnak işaretleri eklendi diye bu koşul için değerlere çift tırnak işareti dahil etme. Değere tırnak işareti eklersiniz, koşul değerine iki çift tırnak çifti eklenir ve arama sorgusu hata döndürür.|
|Bekletme etiketi|Hem e-posta hem de belgeler için, kullanıcılar tarafından el ile atanmış otomatik etiket ilkeleri veya bekletme etiketleri tarafından iletilere ve belgelere otomatik olarak atanmış bekletme etiketleri. Bekletme etiketleri, bilgi idaresi için e-postaları ve belgeleri sınıflandırmak ve bekletme kurallarını etiket tarafından tanımlanan ayarlara göre zorunlu tutma için kullanılır. Bekletme etiketi adının bir kısmını yazarak joker karakter kullanabilir veya tam etiket adını kullanabilirsiniz. Bekletme etiketleri hakkında daha fazla bilgi için bkz. Bekletme [ilkeleri ve bekletme etiketleri hakkında bilgi.](retention.md)|

### <a name="conditions-for-mail-properties"></a>Posta özellikleri koşulları

Posta kutularında veya ortak klasörlerde arama kullanırken posta özelliklerini kullanarak bir koşul oluşturun. Aşağıdaki tabloda, bir koşul için kullanabileceğiniz e-posta özellikleri listeledir. Bu özellikler, daha önce açıklanan e-posta özelliklerinin bir alt kümesidir. Bu açıklamalar size kolaylık sağlamak için tekrarlanır.

|Koşul|Açıklama|
|---|---|
|İletinin tür|Aranan ileti türü. Bu, Tür e-posta özelliğiyle aynı özelliktir. Olası değerler: <ul><li>kişiler</li><li>belgeler</li><li>E-posta</li><li>dış veriler</li><li>faks</li><li>im</li><li>günlükler</li><li>toplantılar</li><li>microsoftteams</li><li>notlar</li><li>gönderiler</li><li>rssfeeds</li><li>görevler</li><li>sesli mesaj</li></ul>|
|Katılımcılar|E-posta iletisinde tüm kişiler alanları. Bu alanlar Ilk, Son, Bilgi ve Gizli alanlarıdır.|
|Tür|E-posta öğesinin ileti sınıfı özelliği. Bu, ItemClass e-posta özelliğiyle aynı özelliktir. Bu aynı zamanda çok değerli bir koşuldur. Birden çok ileti sınıfı seçmek için **, CTRL** tuşunu basılı tutun ve sonra koşula eklemek istediğiniz açılan listede iki veya daha çok ileti sınıfına tıklayın. Listede seçen her ileti sınıfı, ilgili arama sorgusundaki **OR** işleciyle mantıksal olarak bağlantılı olur. <p> Exchange tarafından kullanılan ve İleti sınıfı listesinden seçerek kullansanız da ileti sınıflarının listesi için, bkz. Öğe Türleri ve İleti [Sınıfları](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Alındı|E-posta iletisi alıcı tarafından alınmıştır. Bu, Alınan e-posta özelliğiyle aynı özelliktir.|
|Alıcılar|E-posta iletisinde tüm alıcı alanları. Bu alanlar To, Bilgi ve Gizli'dir.|
|Gönderen|E-posta iletisi gönderen.|
|Gönderildi|Gönderen tarafından e-posta iletisi gönderildiği tarih. Bu, Gönderilmiş e-posta özelliğiyle aynı özelliktir.|
|Konu|E-posta iletisi konu satırı metindir. <p> **Not**: Bu arama koşulu kullanılırken otomatik olarak tırnak işaretleri eklendi diye bu koşul için değerlere çift tırnak işareti dahil etme. Değere tırnak işareti eklersiniz, koşul değerine iki çift tırnak çifti eklenir ve arama sorgusu hata döndürür.|
|Hedef|E-posta iletisi alıcısı, Son alanında.|

### <a name="conditions-for-document-properties"></a>Belge özellikleri koşulları

Site içinde ve diğer sitelerde belge ararken belge özelliklerini SharePoint bir OneDrive İş oluşturun. Aşağıdaki tabloda, bir koşul için kullanabileceğiniz belge özellikleri listelenmiştir. Bu özellikler, daha önce açıklanan site özelliklerinin bir alt kümesidir. Bu açıklamalar size kolaylık sağlamak için tekrarlanır.

|Koşul|Açıklama|
|---|---|
|Yazar|Belgelerden yazar Office alanı; belge kopyalanırsa kalıcı olur. Örneğin, bir kullanıcı belgeyi oluşturur ve bu belgeyi başka birine e-postayla gönderdikten sonra SharePoint, belge özgün yazarı korur.|
|Başlık|Belgenin başlığı. Başlık özelliği, bu belgelerde belirtilen meta Office kullanılır. Belgenin dosya adıyla aynı değil.|
|Oluşturuldu|Belgenin oluşturulma tarihi.|
|Son değiştirme|Belgenin son değiştir bitiş tarihi.|
|Dosya türü|Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx. Bu, FileExtension site özelliğiyle aynı özelliktir. <p> **Not:** Arama sorgusunda herhangi bir işleci Eşittir veya  Eşittir'i  kullanarak Dosya türü koşulu eklersanız, bir dosya türünün tüm sürümlerini geri dönmek için ön ek araması (dosya türünün sonuna joker karakteri ( \* ) içerecek şekilde) ek yoktur. Bunu yaparsanız, joker karakter yok sayılır. Örneğin , koşul içerirse `Equals any of doc*`, yalnızca uzantısı olan dosyalar `.doc` döndürülür. Uzantısı olan `.docx` dosyalar iade edilir. Bir dosya türünün tüm sürümlerini dönmek için anahtar sözcük *sorgusunda property:value* çifti kullanılır; örneğin, `filetype:doc*`.|

### <a name="operators-used-with-conditions"></a>Koşullarla kullanılan işleçler

Bir koşul eklerken, koşula ait özellik türüyle ilgili olan bir işleç seçin. Aşağıdaki tabloda, koşullarla birlikte kullanılan işleçler ve arama sorgusunda kullanılan eşdeğeri listelemektedir.

|İşleç|Sorgu eşdeğeri|Açıklama|
|---|---|---|
|Sonra|`property>date`|Tarih koşullarıyla kullanılır. Belirtilen tarihten sonra gönderilmiş, alınan veya değiştirilen öğeleri döndürür.|
|Önce|`property<date`|Tarih koşullarıyla kullanılır. Belirtilen tarihten önce gönderilmiş, alınan veya değiştirilen öğeleri döndürür.|
|Arasında|`date..date`|Tarih ve boyut koşullarıyla kullanın. Tarih koşuluyla kullanılırken, belirtilen tarih aralığında gönderilmiş, alınan veya değiştirilmiş olan öğeleri döndürür. Boyut koşuluyla kullanılırken, boyutu belirtilen aralık içinde olan öğeleri döndürür.|
|Şu içeriği içerir:|`(property:value) OR (property:value)`|Dize değeri belirten özellikler için koşullarla kullanılır. Belirtilen bir veya birden çok dize değerlerinin herhangi bir bölümünü içeren öğeleri döndürür.|
|Herhangi bir|`-property:value` <p> `NOT property:value`|Dize değeri belirten özellikler için koşullarla kullanılır. Belirtilen dize değerinin hiçbir bölümünü içermeden öğeleri döndürür.|
|Eşit|`-property=value` <p> `NOT property=value`|Dize değeri belirten özellikler için koşullarla kullanılır. Belirli bir dizeyi içermeden öğeleri döndürür.|
|Eşittir|`size=value`|Belirtilen boyuta eşit öğeleri döndürür. <sup>1</sup>|
|Eşit|`(property=value) OR (property=value)`|Dize değeri belirten özellikler için koşullarla kullanılır. Belirtilen bir veya birden çok dize değeriyle eş değeri olan öğeleri döndürür.|
|Büyüktür|`size>value`|Belirtilen özellik belirtilen değerden büyük olan öğeleri döndürür. <sup>1</sup>|
|Büyük veya eşit|`size>=value`|Belirtilen özellik belirtilen değerden büyük veya eşit olan öğeleri döndürür. <sup>1</sup>|
|Daha az|`size<value`|Belirli bir değerden büyük veya eşit olan öğeleri döndürür. <sup>1</sup>|
|Daha az veya eşit|`size<=value`|Belirli bir değerden büyük veya eşit olan öğeleri döndürür. <sup>1</sup>|
|Eşit değil|`size<>value`|Belirtilen boyuta eşit değildir öğeleri döndürür. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Bu işleç yalnızca Size özelliğini kullanan koşullar için kullanılabilir.

### <a name="guidelines-for-using-conditions"></a>Koşulları kullanma yönergeleri

Arama koşullarını kullanırken aşağıdakilere göz asın.

- Koşul, AND işleci tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal **olarak** bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de sonuçlara dahil edilecek koşulu karşılaması gereken anlamına gelir. Koşullar, sonuçlarınızı daraltmanıza böyle yardımcı olur.

- Bir arama sorgusuna iki veya daha fazla benzersiz durum (farklı özellikler belirten koşullar) eklersanız, bu koşullar AND işleci tarafından mantıksal olarak **bağlanır** . Bu, yalnızca tüm koşulları karşılayan öğeler (anahtar sözcük sorgusuna ek olarak) döndürülür.

- Aynı özellik için birden çok koşul eklersanız, bu koşullar OR işleci tarafından mantıksal olarak **bağlanır** . Bu, anahtar sözcük sorgusunu karşılayan öğeler ve koşullardan herhangi birinin döndürül olduğu anlamına gelir. Dolayısıyla, aynı koşulların grupları **OR** işleci tarafından birbirine bağlanır ve sonra benzersiz koşullar kümeleri AND işleci **tarafından** bağlanır.

- Tek koşula birden çok değer eklersiniz (virgül veya noktalı virgülle ayrılmış olarak), bu değerler **OR işleciyle** bağlanır. Bu, koşulda özellik için belirtilen değerlerden herhangi birini içeren öğeler döndürülür.

- Contains ve Equals mantığı olan **işleç** **kullanan herhangi** bir koşul, basit dize aramaları için benzer arama sonuçlarını döndürür. Basit dize araması, koşulda joker karakter içeren bir dizedir. Örneğin, Eşittir kullanan bir **koşul** , Herhangi birini içerir ifadesinin olduğu koşulla aynı **öğeleri geri dönecektir**.

- Anahtar sözcükler kutusu ve koşullar kullanılarak oluşturulan arama sorgusu Arama sayfasında, seçili aramanın ayrıntılar bölmesinde  görüntülenir. Sorguda, notasyonun sağ sağı,  `(c:c)` sorguya eklenen koşulları gösterir.

- Koşullar yalnızca arama sorgusuna özellikler ekler; işleçleri eklemez. İşte bu nedenle, ayrıntı bölmesinde görüntülenen sorgu, notasyonun sağda işleçleri  `(c:c)` görüntülemez. KQL, sorguyu yürütürken mantıksal işleçleri ekler (daha önce açıklanan kurallara göre).

- Koşulların sıralamalarını yeniden sıralamak için sürükleyip bırakma denetimlerini kullanabilirsiniz. Bir koşul için denetime tıklayın ve yukarı veya aşağı hareket ettirin.

- Daha önce de açıklanmıştır, bazı koşul özellikleri birden çok değer (noktalı virgülle ayırarak) yazmanız için olanak sağlar. Her değer OR işleci **tarafından mantıksal olarak** bağlantılıdır ve sorgunun sonucudur `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)`. Aşağıdaki çizimde, birden çok değer içeren bir koşul örneği gösterilmiştir.

    ![Birden çok değer içeren tek bir koşul.](../media/SearchConditions1.png)

  > [!NOTE]
  > Birden çok koşul ekyenesiniz (aynı özellik için **Koşul ekle'yi** tıklatarak). Bunun yerine, önceki örnekte gösterildiği gibi koşul için birden çok değer (noktalı virgülle ayırarak) sağlamış oluruz.

### <a name="examples-of-using-conditions-in-search-queries"></a>Arama sorgularında koşullar kullanma örnekleri

Aşağıdaki örneklerde, koşulları içeren bir arama sorgusunun GUI tabanlı sürümü, seçili aramanın ayrıntılar bölmesinde görüntülenen arama sorgusu söz dizimi ( **Get-ComplianceSearch** cmdlet'i tarafından da döndürülür) ve ilgili KQL sorgusunun mantığı gösterilir.

#### <a name="example-1"></a>Örnek 1

Bu örnek, kredi SharePoint numarası OneDrive İş tüm sitelerde bulunan ve son olarak 1 Ocak 2021'den önce değiştirilmiş olan belgeleri döndürür.

**GUI**:

![Arama koşullarına ilk örnek.](../media/SearchConditions2.png)

**Arama sorgusu söz dizimi**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Arama sorgu mantığı**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Önceki ekran görüntüsünde, arama kullanıcı arabiriminin anahtar sözcük sorgusunun ve koşulun AND işleci tarafından bağlanarak **bağlandılı olduğunu ifade etti** .

#### <a name="example-2"></a>Örnek 2

Bu örnek, 1 Nisan 2021'den önce gönderilmiş veya oluşturulmuş olan ve e-posta iletilerinin konu alanında veya belgelerin başlık özelliğinde "northwind" sözcüğünü içeren "rapor" anahtar sözcüğünü içeren e-posta öğelerini veya belgeleri döndürür. Sorgu, diğer arama ölçütlerine uyan Web sayfalarını dışlar.

**GUI**:

![İkinci arama koşulları örneği.](../media/SearchConditions3.png)

**Arama sorgusu söz dizimi**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Arama sorgu mantığı**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Örnek 3

Bu örnek, 1 Aralık 2019 ile 30 Kasım 2020 arasında gönderilmiş olan ve "telefon" veya "akıllı telefon" ile başlamak üzere sözcükleri içeren e-posta iletilerini veya takvim toplantılarını döndürür.

**GUI**:

![Üçüncü arama koşulları örneği.](../media/SearchConditions4.png)

**Arama sorgusu söz dizimi**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Arama sorgu mantığı**:

`phone* OR smartphone* AND (sent=2019-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Özel karakterler

Bazı özel karakterler arama dizinine dahil değildir ve bu nedenle aranamaz. Bu, arama sorgusunda arama işleçlerini temsil eden özel karakterleri de içerir. Burada, asıl arama sorgusunda boş bir alanla değiştirilmiş veya bir arama hatasına neden olan özel karakterlerin listesi ve ve bir liste yer alır.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Dış kullanıcılarla paylaşılan site içeriğini arama

Uyumluluk merkezinde eBulma arama araçlarını, kuruluş dışından kişileriyle paylaşılan SharePoint ve OneDrive İş sitelerinde depolanan belgeleri aramak için de kullanabilirsiniz. Bu, kuruluş dışında paylaşılan hassas veya özel bilgileri tanımlamanıza yardımcı olabilir. Özelliği bir anahtar sözcük sorgusunda  `ViewableByExternalUsers` kullanarak bunuabilirsiniz. Bu özellik, aşağıdaki paylaşım yöntemlerinden birini kullanarak dış kullanıcılarla paylaşılan belgeleri veya siteleri döndürür:

- Kullanıcıların, kimliği doğrulanmış bir kullanıcı olarak organizasyonunuza oturum açmasını gerektiren paylaşım daveti.
- Anonim konuk bağlantısı, bu bağlantıya sahip olan herkesin kimlik doğrulaması yapmak zorunda kalmadan kaynağa erişmelerine olanak sağlar.

İşte birkaç örnek:

- Sorgu,  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` kuruluşun dışındakilerle paylaşılan ve kredi kartı numarası içeren tüm öğeleri döndürür.
- Sorgu,  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` kuruluşta dış kullanıcılarla paylaşılan tüm ekip sitelerinin belgelerinin listesini döndürür.

> [!TIP]
> Örneğin, arama sonuçlarına  `ViewableByExternalUsers:true AND ContentType:document` çok fazla .aspx dosyası gönderebilirsiniz. Bu (veya diğer dosya türlerini) ortadan kaldırmak için, özelliği belirli dosya  `FileExtension` türlerini dışarıda tutmak için kullanabilirsiniz; örneğin  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx`.

Kuruluş dışından kişileriyle paylaşılan içerik olarak ne kabul edilir? Bir paylaşım daveti göndererek SharePoint veya OneDrive İş konumlarda paylaşılan belgeler. Örneğin, aşağıdaki kullanıcı etkinlikleri, dış kullanıcılar tarafından görüntülenebilir içerikle sonuçlanabilir:

- Kullanıcı, dosya veya klasörü kuruluş dışındaki bir kullanıcıyla paylaştığında.
- Kullanıcı, paylaşılan dosyanın bağlantısını, kuruluş dışındaki bir kişiye gönderir. Bu bağlantı dış kullanıcının dosyayı görüntülemesi (veya düzenlemesi) için olanak sağlar.
- Bir kullanıcı paylaşılan dosyayı görüntülemesi (veya düzenlemesi) için kuruluş dışındaki bir kişiye paylaşım daveti veya konuk bağlantısı gönderir.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>ViewableByExternalUsers özelliğini kullanma sorunları

Özellik,  `ViewableByExternalUsers` bir belgenin veya sitenin dış kullanıcılarla paylaşılıyor olup olmadığı durumunu temsil eder, ancak bu özelliğin yaptığı ve yansıtmadığı bazı uyarılar vardır. Aşağıdaki senaryolarda, özelliğin  `ViewableByExternalUsers` değeri güncelleştirilmez ve bu özelliği kullanan bir arama sorgusunun sonuçları yanlış olabilir.

- Paylaşım ilkesinde yapılan, site veya kuruluş için dış paylaşımı kapatma gibi değişiklikler. Dış erişim iptal edilmiş olsa bile, özellik daha önce paylaşılan belgelerin dış olarak erişilebilir olduğunu göstermeye devam ediyor.
- Grup üyeliğinde yapılan, Dış kullanıcıları Grup gruplarına ekleme veya Microsoft 365 veya güvenlik Microsoft 365 gibi değişiklikler. Grubun erişim izni olan öğeler için özellik otomatik olarak güncelleştirilmez.
- Alıcı daveti kabul etmemiş olan ve dolayısıyla içeriğe henüz erişimi olmayan dış kullanıcılara paylaşım davetleri gönderme.

Bu senaryolarda,  `ViewableByExternalUsers` site veya belge kitaplığı yeniden yorumlana kadar özellik geçerli paylaşım durumunu yansıtmaz.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Kuruluş içinde paylaşılan site içeriğini arama

Daha önce de belirtildiği gibi, bu  `SharedWithUsersOWSUser` özelliği kullanarak, kuruluşta yer alan kişiler arasında paylaşılan belgeleri arayabilirsiniz. Bir kişi, kurum içindeki başka bir kullanıcıyla dosya (veya klasör) paylaştığında, paylaşılan dosyanın bağlantısı, dosyanın paylaşıldı  olduğu kişinin OneDrive İş hesabı'nın Benimle paylaşılan sayfasında görünür. Örneğin, Sara Davis ile paylaşılan belgeleri aramak için sorguyu kullanabilirsiniz  `SharedWithUsersOWSUser:"sarad@contoso.com"`. Bu aramanın sonuçlarını dışarı aktarsanız, özgün belgeler (belgeleri Deniz ile paylaşan kişinin içerik konumda bulunur) indirilir.

Özellik kullanılırken arama sonuçlarında döndürülecek belgelerin belirli bir kullanıcıyla açık bir şekilde paylaşılıyor olması  `SharedWithUsersOWSUser` gerekir. Örneğin, bir kişi OneDrive hesabında bir belge paylaştığında, bu belgeyi herkesle (kuruluşun içindeki veya dışındaki) paylaşma, yalnızca kuruluş içindeki kişilerle paylaşma veya belirli bir kişi ile paylaşma seçeneği vardır. Burada, **OneDrive'da** üç paylaşım OneDrive Paylaş penceresinin ekran görüntüsü ve gösterilir.

![Yalnızca belirli kişilerle paylaşılan dosyalar, SharedWithUsersOWSUser özelliğini kullanan bir arama sorgusu tarafından döndürülür.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Yalnızca üçüncü seçenek (Belirli kişiler ile **paylaşılan) kullanılarak** paylaşılan belgeler, özelliği kullanan bir arama sorgusu tarafından  `SharedWithUsersOWSUser` döndürülür.

## <a name="searching-for-skype-for-business-conversations"></a>Daha fazla Skype Kurumsal arama

Aşağıdaki anahtar sözcük sorgusunu, belirli bir konuşmada özellikle içerik aramak Skype Kurumsal kullanabilirsiniz:

```powershell
kind:im
```

Önceki arama sorgusu, çalışma sayfalarındaki sohbetleri de Microsoft Teams. Bunu önlemek için, aşağıdaki anahtar sözcük sorgusunu kullanarak yalnızca Skype Kurumsal arama sonuçlarını daraltabilirsiniz:

```powershell
kind:im AND subject:conversation
```

Önceki anahtar sözcük sorgusu Microsoft Teams'te sohbetleri dışlar çünkü Skype Kurumsal konuşmaları Konu satırı "Konuşma" ile başlayan e-posta iletileri olarak kaydedilir.

Belirli bir Skype Kurumsal aralığında yapılan konuşmaları aramak için aşağıdaki anahtar sözcük sorgusunu kullanın:

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Aramalar için karakter sınırları

Sitelerde ve SharePoint hesaplarında içerik ararken, arama sorguları için 4.000 OneDrive vardır.
Arama sorgusunda toplam karakter sayısı şöyle hesaplanır:

- Anahtar sözcük arama sorgusunda karakterler (hem kullanıcı hem de filtre alanları dahil) bu sınıra göre sayılır.
- Konum özelliğinde yer alan karakterler (tüm site sitelerinin veya SharePoint konumların URL'leri OneDrive) bu sınıra göre sayılır.
- Tüm arama izinleri filtrelerinde yer alan ve arama sayısını sınır üzerinde çalıştıran kullanıcıya uygulanan karakterler.

Karakter sınırları hakkında daha fazla bilgi için bkz [. eBulma arama sınırları](limits-for-content-search.md#search-limits).

> [!NOTE]
> 4.000 karakter sınırı İçerik araması, Çekirdek eKbulma ve Advanced eDiscovery.

## <a name="search-tips-and-tricks"></a>Arama ipuçları ve püf noktaları

- Anahtar sözcük aramaları büyük/harfe duyarlı değildir. Örneğin, **kedi ve** **CAT** aynı sonuçları verir.

- Boole işleçleri **AND**, **OR**, **NOT** ve **NEAR** büyük harfle olmalıdır.

- İki anahtar sözcük veya iki ifade arasında  `property:value` boşluk kullanmak VE kullanmakla **aynıdır**. Örneğin,  `from:"Sara Davis" subject:reorganization` Sara Davis tarafından gönderilen ve konu satırlarında düzenleme sözcüğü bulunan tüm iletileri döndürür.

- Biçimle eşleşen söz dizimi kullanın `property:value` . Değerler büyük/küçük harfe duyarlı değildir ve işleçlerden sonra boşlukları da değildir. Boşluk varsa, istediğiniz değer tam metin araması olur. Örneğin, `to: pilarp` pilarp'e gönderilen iletiler yerine anahtar sözcük olarak "pilarp" için arama yapmak gerekir.

- To, Kaynak, Bilgi veya Alıcılar gibi bir alıcı özelliğini ararken alıcıyı göstermek için SMTP adresi, diğer ad veya görünen ad kullanabilirsiniz. Örneğin, Pinilla, pilarp@contoso.com veya "Pilar Pinilla" kullanabilirsiniz.

- Yalnızca ön ek aramaları kullanabilirsiniz; örneğin, **kedi\**_ veya _* set\**_. Sonek aramaları (_*\*kedi**), infix aramaları (**ct\***) ve alt dize aramaları (**\*kedi\***) desteklemez.

- Bir özelliği ararken, arama değeri birden çok sözcüklerden oluşan bir özellik için çift tırnak işareti (" ") kullanın. Örneğin, `subject:budget Q1` konu satırlarında **bütçe içeren** ve iletinin herhangi bir yerinde veya ileti özelliklerinde **Ç1** içeren iletileri döndürür. Kullanımı `subject:"budget Q1"` , konu satırı içinde herhangi bir **yerde bütçe Q1** ifadesini içeren tüm iletileri döndürür.

- Belirli bir özellik değeriyle işaretlenmiş içerikleri arama sonuçlarınıza dahil etmek için özelliğin adının önce bir eksi işareti (-) girin. Örneğin, Sara `-from:"Sara Davis"` Davis tarafından gönderilen tüm iletileri dışlar.

- Öğeleri ileti türüne göre dışarı aktarabilirsiniz. Örneğin, bir Skype konuşmaları ve sohbetleri dışarı Microsoft Teams, söz dizimi kullanın`kind:im`. Yalnızca e-posta iletilerini geri göndermek için ' kullanırsınız `kind:email`. Bir toplantıda sohbet, toplantı ve arama geri Microsoft Teams için kullanın`kind:microsoftteams`.

- Daha önce de belirtildiği gibi `/` , sitelerde arama yapmak için özelliği kullanırken yalnızca belirli bir sitedeki öğeleri geri dönecek şekilde URL'nin `path` sonuna sonda eklemeniz gerekir. Sonda 'i dahil etmeyebilirsiniz; `/`benzer yol adına sahip bir sitedeki öğeler de döndürülür. Örneğin, daha sonra adlandırılmış `path:sites/HelloWorld` sitelerden öğeler kullanırsanız `sites/HelloWorld_East` veya bu öğeler `sites/HelloWorld_West` de döndürülür. Yalnızca HelloWorld sitesinden öğeler iade etmek için , kullanın `path:sites/HelloWorld/`.
