---
title: eBulma için anahtar sözcük sorguları ve arama koşulları
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
description: Microsoft 365'daki eBulma arama araçlarını kullanarak arama yapabileceğiniz e-posta ve belge özellikleri hakkında bilgi edinin.
ms.openlocfilehash: 09c939f7d92bf06a9eab89d8ac45fec78bd424a8
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936653"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>eBulma için anahtar sözcük sorguları ve arama koşulları

Bu makalede, e-posta öğelerinde arayabileceğiniz e-posta ve belge özellikleri ve Exchange Online sohbet konuşmaları Microsoft Teams ve Microsoft Purview uyumluluk portalındaki eBulma arama araçlarını kullanarak SharePoint ve OneDrive İş sitelerinde depolanan belgeler açıklanmaktadır. Buna İçerik arama, Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) dahildir (eBulma'daki (Premium) eBulma aramalarına *koleksiyon* adı verilir). Bu özellikleri aramak için Güvenlik & Uyumluluk Merkezi PowerShell'deki -ComplianceSearch cmdlet'lerini de kullanabilirsiniz **\***. Makalede ayrıca şunlar açıklanmaktadır:

- Arama sonuçlarınızı daraltmak için Boole arama işleçlerini, arama koşullarını ve diğer arama sorgusu tekniklerini kullanma.
- SharePoint ve OneDrive İş hassas veri türlerini ve özel hassas veri türlerini arama.
- Kuruluşunuzun dışındaki kullanıcılarla paylaşılan site içeriğini arama

Farklı eBulma aramaları oluşturma hakkında adım adım yönergeler için bkz:

- [İçerik arama](content-search.md)
- [eBulma'da içerik arama (Standart)](search-for-content-in-core-ediscovery.md)
- [eBulma'da taslak koleksiyon oluşturma (Premium)](create-draft-collection.md)

> [!NOTE]
> Uyumluluk portalında eBulma aramaları ve Güvenlik & Uyumluluk Merkezi PowerShell'deki ilgili **\*-ComplianceSearch** cmdlet'leri Anahtar Sözcük Sorgu Dili'ni (KQL) kullanır. Daha ayrıntılı bilgi için bkz [. Anahtar Sözcük Sorgu Dili söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

## <a name="searchable-email-properties"></a>Aranabilir e-posta özellikleri

Aşağıdaki tabloda, uyumluluk portalındaki eBulma arama araçları kullanılarak veya **New-ComplianceSearch veya Set-ComplianceSearch** cmdlet'i kullanılarak aranabilecek **e-posta** iletisi özellikleri listelenmiştir. Tabloda her  _özellik için property:value_ söz dizimi örneği ve örnekler tarafından döndürülen arama sonuçlarının açıklaması yer alır. EBulma araması için anahtar sözcükler kutusuna bu  `property:value` çiftleri yazabilirsiniz.

> [!NOTE]
> E-posta özelliklerinde arama yaparken, belirtilen özelliğin boş veya boş olduğu öğeleri aramak mümkün değildir. Örneğin, konu satırı boş olan e-posta iletilerini aramak için **subject:"" özelliğinin:***değer* çiftinin kullanılması sıfır sonuç döndürür. Bu, site ve kişi özelliklerinde arama yaparken de geçerlidir.

|Özellik|Özellik açıklaması|Örnekler|Örnekler tarafından döndürülen arama sonuçları|
|---|---|---|---|
|AttachmentNames|E-posta iletisine eklenen dosyaların adları.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|annualreport.ppt adlı ekli bir dosyası olan iletiler. İkinci örnekte, joker karakter ( * ) kullanıldığında, ekin dosya adında "yıllık" sözcüğü bulunan iletiler döndürülüyor. Üçüncü örnek, pptx dosya uzantısına sahip tüm ekleri döndürür.|
|Gizli|E-posta iletisinin Gizli alanı. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|Tüm örnekler Gizli alanına Pilar Pinilla eklenmiş iletileri döndürür.|
|Kategori|Aranacak kategoriler. Kategoriler kullanıcılar tarafından Outlook veya Web üzerinde Outlook (eski adıyla Outlook Web App) kullanılarak tanımlanabilir. Olası değerler: <ul><li>Mavi<li>Yeşil<li>Turuncu<li>Mor<li>Kırmızı<li>Sarı</li></ul>|`category:"Red Category"`|Kaynak posta kutularında kırmızı kategoriye atanmış iletiler.|
|Cc|E-posta iletisinin Bilgi alanı. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|Her iki örnekte de Bilgi alanında Pilar Pinilla'nın belirtildiği iletiler.|
|Folderid|Belirli bir posta kutusu klasörünün klasör kimliği (GUID). Bu özelliği kullanırsanız, belirtilen klasörün bulunduğu posta kutusunda arama yapmaya özen gösterin. Yalnızca belirtilen klasör aranacak. Klasördeki alt klasörler aranmayacak. Alt klasörleri aramak için, aramak istediğiniz alt klasörün Folderid özelliğini kullanmanız gerekir. <p> Folderid özelliğini arama ve belirli bir posta kutusunun klasör kimliklerini almak için betik kullanma hakkında daha fazla bilgi için bkz. [Hedeflenen koleksiyonlar için İçerik aramasını kullanma](use-content-search-for-targeted-collections.md).|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|İlk örnek, belirtilen posta kutusu klasöründeki tüm öğeleri döndürür. İkinci örnek, belirtilen posta kutusu klasöründeki garthf@contoso.com tarafından gönderilen veya alınan tüm öğeleri döndürür.|
|Kaynak|E-posta iletisinin göndereni. <sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Belirtilen kullanıcı tarafından gönderilen veya belirtilen bir etki alanından gönderilen iletiler.|
|HasAttachment|İletinin eki olup olmadığını gösterir. **true** veya **false** değerlerini kullanın.|`from:pilar@contoso.com AND hasattachment:true`|Belirtilen kullanıcı tarafından gönderilen ve ekleri olan iletiler.|
|Önemi|Gönderenin ileti gönderirken belirtebileceği e-posta iletisinin önemi. Varsayılan olarak, gönderen önem derecesini **yüksek** veya **düşük** olarak belirlemediği sürece iletiler normal öneme sahip olarak gönderilir.|`importance:high` <p> `importance:medium` <p> `importance:low`|Yüksek önem, orta önem veya düşük önem olarak işaretlenmiş iletiler.|
|IsRead|İletilerin okunup okunmadığını gösterir. **true** veya **false** değerlerini kullanın.|`isread:true` <p> `isread:false`|İlk örnek, IsRead özelliğinin **True** olarak ayarlandığı iletileri döndürür. İkinci örnek, IsRead özelliğinin **False** olarak ayarlandığı iletileri döndürür.|
|ItemClass|Kuruluşunuzun Office 365 aktarmış olduğu belirli üçüncü taraf veri türlerini aramak için bu özelliği kullanın. Bu özellik için aşağıdaki söz dizimini kullanın:  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|İlk örnek, Subject özelliğinde "contoso" sözcüğünü içeren Facebook öğelerini döndürür. İkinci örnek, Ann Beebe tarafından gönderilen ve "Northwind Traders" anahtar sözcüğünü içeren Twitter öğelerini döndürür. <p> ItemClass özelliği için üçüncü taraf veri türleri için kullanılacak değerlerin tam listesi için bkz. [Office 365 içeri aktarılan üçüncü taraf verilerinde arama yapmak için İçerik aramasını kullanma](use-content-search-to-search-third-party-data-that-was-imported.md).|
|Tür|Aranacak e-posta iletisinin türü. Olası değerler: <p>  Kişiler <p>  Dokümanlar <p>  E-posta <p>  externaldata <p>  Faks <p>  Im <p>  Günlük <p>  Toplantı <p>  microsoftteams (Microsoft Teams sohbetlerden, toplantılardan ve aramalardan öğeleri döndürür) <p>  Notlar <p>  Mesaj <p>  rssfeeds <p>  Görev <p>  Sesli|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|İlk örnek, arama ölçütlerine uyan e-posta iletilerini döndürür. İkinci örnek e-posta iletilerini, anlık ileti konuşmalarını (Skype Kurumsal konuşmalar ve Microsoft Teams sohbetler dahil) ve arama ölçütlerini karşılayan sesli mesajları döndürür. Üçüncü örnek, arama ölçütlerini karşılayan Twitter, Facebook ve Cisco Jabber gibi üçüncü taraf veri kaynaklarından Microsoft 365 posta kutularına aktarılan öğeleri döndürür. Daha fazla bilgi için bkz[. Office 365 üçüncü taraf verilerini arşivleme](https://www.microsoft.com/?ref=go).|
|Katılımcı|E-posta iletisindeki tüm kişiler alanları. Bu alanlar Kimden, Kime, Bilgi ve <sup>Gizli'dir.1</sup>|`participants:garthf@contoso.com` <p> `participants:contoso.com`|tarafından gönderilen veya garthf@contoso.com gönderilen iletiler. İkinci örnek, contoso.com etki alanındaki bir kullanıcı tarafından gönderilen veya kullanıcıya gönderilen tüm iletileri döndürür.|
|Alınan|E-posta iletisinin alıcı tarafından alındığı tarih.|`received:2021-04-15` <p> `received>=2021-01-01 AND received<=2021-03-31`|15 Nisan 2021'de alınan iletiler. İkinci örnek, 1 Ocak 2021 ile 31 Mart 2021 arasında alınan tüm iletileri döndürür.|
|Alıcı|E-posta iletisindeki tüm alıcı alanları. Bu alanlar Kime, Bilgi ve <sup>Gizli'dir.1</sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|garthf@contoso.com gönderilen iletiler. İkinci örnek, contoso.com etki alanındaki herhangi bir alıcıya gönderilen iletileri döndürür.|
|Gönderilen|Gönderen tarafından e-posta iletisinin gönderildiği tarih.|`sent:2021-07-01` <p> `sent>=2021-06-01 AND sent<=2021-07-01`|Belirtilen tarihte gönderilen veya belirtilen tarih aralığında gönderilen iletiler.|
|Boyutu|Bir öğenin bayt cinsinden boyutu.|`size>26214400` <p> `size:1..1048567`|25 MB'tan büyük iletiler. İkinci örnek, boyutu 1 ile 1.048.567 bayt (1 MB) arasında olan iletileri döndürür.|
|Konu|E-posta iletisinin konu satırındaki metin. <p> **Not:** Sorguda Subject özelliğini kullandığınızda, arama, konu satırının aradığınız metni içerdiği tüm iletileri döndürür. Başka bir deyişle, sorgu yalnızca tam eşleşmesi olan iletileri döndürmez. Örneğin, için  `subject:"Quarterly Financials"`arama yaparsanız sonuçlarınız "Quarterly Financials 2018" konusuna sahip iletileri içerir.|`subject:"Quarterly Financials"` <p> `subject:northwind`|Konu satırının metninin herhangi bir yerinde "Üç Aylık Finansallar" ifadesini içeren iletiler. İkinci örnek, konu satırında northwind sözcüğünü içeren tüm iletileri döndürür.|
|Hedef|E-posta iletisinin To alanı. <sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Tüm örnekler, Ann Beebe'nin To: satırında belirtildiği iletileri döndürür.|

> [!NOTE]
> <sup>1</sup> Alıcı özelliğinin değeri için, bir kullanıcı belirtmek için e-posta adresini ( *kullanıcı asıl adı* veya UPN olarak da adlandırılır), görünen adı veya diğer adı kullanabilirsiniz. Örneğin, ann Beebe kullanıcısını belirtmek için annb@contoso.com, annb veya "Ann Beebe" kullanabilirsiniz.

### <a name="recipient-expansion"></a>Alıcı genişletme

Alıcı özelliklerinden herhangi birini (Kimden, Kime, Bilgi, Gizli, Katılımcılar ve Alıcılar) ararken Microsoft 365 her kullanıcının kimliğini Azure Active Directory(Azure AD) içinde arayarak genişletmeye çalışır.  Kullanıcı Azure AD'de bulunursa, sorgu kullanıcının e-posta adresini (veya UPN'sini), diğer adını, görünen adını ve LegacyExchangeDN'yi içerecek şekilde genişletilir. Örneğin, gibi `participants:ronnie@contoso.com` bir sorgu olarak `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"`genişletir.

Alıcının genişlemesini önlemek için e-posta adresinin sonuna joker karakter (yıldız) ekleyin ve azaltılmış bir etki alanı adı kullanın; örneğin, `participants:"ronnie@contoso*"` e-posta adresini çift tırnak işaretiyle çevrelemeye özen gösterin.

Ancak, arama sorgusunda alıcının genişlemesini engellemenin, arama sonuçlarında ilgili öğelerin döndürülmemesine neden olabileceğini unutmayın. Exchange'daki e-posta iletileri, alıcı alanlarında farklı metin biçimleriyle kaydedilebilir. Alıcı genişletmesi, farklı metin biçimleri içerebilecek iletiler döndürerek bu gerçeğin azaltılmasına yardımcı olmak için tasarlanmıştır. Bu nedenle, alıcının genişlemesini önlemek, arama sorgusunun araştırmanızla ilgili olabilecek tüm öğeleri döndürmemesine neden olabilir.

> [!NOTE]
> Alıcı genişletmesi nedeniyle arama sorgusu tarafından döndürülen öğeleri gözden geçirmeniz veya azaltmanız gerekiyorsa eBulma (Premium) kullanmayı göz önünde bulundurun. İletileri arayabilir (alıcı genişletme özelliğinden yararlanarak), bunları bir gözden geçirme kümesine ekleyebilir ve ardından sonuçları gözden geçirmek veya daraltmak için gözden geçirme kümesi sorgularını veya filtrelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Servis talebi için veri toplama](collecting-data-for-ediscovery.md) ve [Gözden geçirme kümesindeki verileri sorgulama](review-set-search.md).

## <a name="searchable-site-properties"></a>Aranabilir site özellikleri

Aşağıdaki tabloda, Microsoft Purview uyumluluk portalındaki eBulma arama araçları kullanılarak veya **New-ComplianceSearch** veya **Set-ComplianceSearch** cmdlet'i kullanılarak aranabilecek SharePoint ve OneDrive İş özelliklerinden bazıları listelenmiştir. Tabloda her  _özellik için property:value_ söz dizimi örneği ve örnekler tarafından döndürülen arama sonuçlarının açıklaması yer alır.

Aranabilecek SharePoint özelliklerin tam listesi için bkz. [SharePoint'da gezinilen ve yönetilen özelliklere genel bakış](/SharePoint/technical-reference/crawled-and-managed-properties-overview). **Sorgulanabilir** sütununda **Evet** ile işaretlenmiş özellikler aranabilir.

|Özellik|Özellik açıklaması|Örnek|Örnekler tarafından döndürülen arama sonuçları|
|---|---|---|---|
|Yazar|Office belgedeki yazar alanı, belge kopyalandığında kalıcı olur. Örneğin, bir kullanıcı bir belge oluşturursa ve belgeyi başka birine e-postayla SharePoint, belge özgün yazarı korur. Bu özellik için kullanıcının görünen adını kullandığınızdan emin olun.|`author:"Garth Fort"`|Garth Fort tarafından yazılan tüm belgeler.|
|Contenttype|Öğe, Belge veya Video gibi bir öğenin SharePoint içerik türü.|`contenttype:document`|Tüm belgeler döndürülür.|
|Oluşturuldu|Bir öğenin oluşturulduğu tarih.|`created>=2021-06-01`|1 Haziran 2021 veya sonrasında oluşturulan tüm öğeler.|
|Createdby|Öğeyi oluşturan veya karşıya yükleyen kişi. Bu özellik için kullanıcının görünen adını kullandığınızdan emin olun.|`createdby:"Garth Fort"`|Garth Fort tarafından oluşturulan veya yüklenen tüm öğeler.|
|Algılanan Dil|Öğenin dili.|`detectedlanguage:english`|Tüm İngilizce öğeler.|
|DocumentLink|SharePoint veya OneDrive İş sitesindeki belirli bir klasörün yolu (URL). Bu özelliği kullanırsanız, belirtilen klasörün bulunduğu sitede arama yapmaya özen gösterin. <p> Documentlink özelliği için belirttiğiniz klasörün alt klasörlerinde bulunan öğeleri döndürmek için belirtilen klasörün URL'sine /\* eklemeniz gerekir; örneğin, `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Documentlink özelliğini arama ve belirli bir sitedeki klasörler için belge bağlantısı URL'lerini almak üzere bir betik kullanma hakkında daha fazla bilgi için bkz. [Hedeflenen koleksiyonlar için İçerik aramasını kullanma](use-content-search-for-targeted-collections.md).|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|İlk örnek, belirtilen OneDrive İş klasöründeki tüm öğeleri döndürür. İkinci örnek, belirtilen site klasöründeki (ve tüm alt klasörlerdeki) dosya adında "gizli" sözcüğünü içeren belgeleri döndürür.|
|Dosyauzantısı|Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx.|`fileextension:xlsx`|Tüm Excel dosyaları (Excel 2007 ve üzeri)|
|Dosyaadı|Dosyanın adı.|`filename:"marketing plan"` <p> `filename:estimate`|İlk örnek, başlıkta tam olarak "pazarlama planı" tümceciği bulunan dosyaları döndürür. İkinci örnek, dosya adında "tahmin" sözcüğü bulunan dosyaları döndürür.|
|LastModifiedTime|Bir öğenin son değiştirildiği tarih.|`lastmodifiedtime>=2021-05-01` <p> `lastmodifiedtime>=2021-05-01 AND lastmodifiedtime<=2021-06-01`|İlk örnek, 1 Mayıs 2021 veya sonrasında değiştirilmiş öğeleri döndürür. İkinci örnek, 1 Mayıs 2021 ile 1 Haziran 2021 arasında değiştirilen öğeleri döndürür.|
|Modifiedby|Bir öğeyi en son değiştiren kişi. Bu özellik için kullanıcının görünen adını kullandığınızdan emin olun.|`modifiedby:"Garth Fort"`|En son Garth Fort tarafından değiştirilen tüm öğeler.|
|Yol|SharePoint veya OneDrive İş sitedeki belirli bir sitenin yolu (URL). <p> Yalnızca belirtilen siteden öğe döndürmek için url'nin sonuna sondakini `/` eklemeniz gerekir; örneğin, `path: "https://contoso.sharepoint.com/sites/international/"` <p> Sitedeki klasörlerde bulunan ve path özelliğinde belirttiğiniz öğeleri döndürmek için URL'nin sonuna eklemeniz `/*` gerekir; örneğin,  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Not:** `Path` OneDrive konumları aramak için özelliğinin kullanılması, arama sonuçlarında .png, .tiff veya .wav dosyaları gibi medya dosyalarını döndürmez. OneDrive klasörlerdeki medya dosyalarını aramak için arama sorgunuzda farklı bir site özelliği kullanın. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|İlk örnek, belirtilen OneDrive İş sitesindeki tüm öğeleri döndürür. İkinci örnek, belirtilen sitede (ve sitedeki klasörlerde) dosya adında "gizli" sözcüğünü içeren belgeleri döndürür.|
|SharedWithUsersOWSUser|Belirtilen kullanıcıyla paylaşılan ve kullanıcının OneDrive İş sitesindeki **Benimle paylaşılan** sayfasında görüntülenen belgeler. Bunlar, kuruluşunuzdaki diğer kişiler tarafından belirtilen kullanıcıyla açıkça paylaşılmış belgelerdir. SharedWithUsersOWSUser özelliğini kullanan bir arama sorgusuyla eşleşen belgeleri dışarı aktardığınızda, belgeler belgeyi belirtilen kullanıcıyla paylaşan kişinin özgün içerik konumundan dışarı aktarılır. Daha fazla bilgi için bkz. [Kuruluşunuzda paylaşılan site içeriğini arama](#searching-for-site-content-shared-within-your-organization).|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Her iki örnek de Garth Fort ile açıkça paylaşılan ve Garth Fort'un OneDrive İş hesabının **Benimle paylaşılan** sayfasında görünen tüm iç belgeleri döndürür.|
|Site|Kuruluşunuzdaki bir sitenin veya site grubunun URL'si.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|İlk örnek, kuruluştaki tüm kullanıcılar için OneDrive İş sitelerindeki öğeleri döndürür. İkinci örnek, tüm ekip sitelerindeki öğeleri döndürür.|
|Boyutu|Bir öğenin bayt cinsinden boyutu.|`size>=1` <p> `size:1..10000`|İlk örnek 1 bayttan büyük öğeleri döndürür. İkinci örnek, boyutu 1 ile 10.000 bayt arasında olan öğeleri döndürür.|
|Başlık|Belgenin başlığı. Title özelliği, Microsoft Office belgelerde belirtilen meta verilerdir. Belgenin dosya adından farklıdır.|`title:"communication plan"`|bir Office belgesinin Başlık meta veri özelliğinde "iletişim planı" ifadesini içeren tüm belgeler.|

## <a name="searchable-contact-properties"></a>Aranabilir kişi özellikleri

Aşağıdaki tabloda, dizine alınan ve eBulma arama araçlarını kullanarak arama yapabileceğiniz kişi özellikleri listelenmiştir. Bunlar, kullanıcıların kullanıcının posta kutusunun kişisel adres defterinde bulunan kişiler (kişisel kişiler olarak da adlandırılır) için yapılandırabilecekleri özelliklerdir. Kişileri aramak için, aranacak posta kutularını seçebilir ve anahtar sözcük sorgusunda bir veya daha fazla kişi özelliğini kullanabilirsiniz.

> [!TIP]
> Boşluk veya özel karakter içeren değerleri aramak için çift tırnak işareti (" ") kullanarak tümceciği kullanın; örneğin, `businessaddress:"123 Main Street"`.

|Özellik|Özellik açıklaması|
|---|---|
|BusinessAddress|**İş Adresi** özelliğindeki adres. Özelliği, kişi özellikleri sayfasındaki **İş** adresi olarak da adlandırılır.|
|İş Telefonu|**İş Telefon** numarası özelliklerinden herhangi birindeki telefon numarası.|
|Şirketadı|**Şirket** özelliğindeki ad.|
|Bölüm|**Department** özelliğindeki ad.|
|Displayname|Kişinin görünen adı. Bu, kişinin **Tam Ad** özelliğindeki addır.|
|Emailaddress|Kişinin herhangi bir e-posta adresi özelliğinin adresi. Kullanıcılar bir kişi için birden çok e-posta adresi ekleyebilir. Bu özelliğin kullanılması, kişinin e-posta adreslerinden herhangi biriyle eşleşen kişileri döndürür.|
|Dosya A'ları|**File as** özelliği. Bu özellik, kişinin kullanıcının kişi listesinde nasıl listeleneceğini belirtmek için kullanılır. Örneğin, bir kişi  *Ad, Soyadı*  veya  *Soyadı,Ad* olarak listelenebilir.|
|Givenname|Ad özelliğindeki **ad** .|
|Evadresi|**Giriş** adresi özelliklerinden herhangi birindeki adres.|
|HomePhone|**Herhangi bir Giriş** telefon numarası özelliğindeki telefon numarası.|
|IMAddress|Anlık ileti için kullanılan bir e-posta adresi olan anlık ileti adresi özelliği.|
|Middlename|**İkinci** ad özelliğindeki ad.|
|Mobilephone|**Cep** telefonu numarası özelliğindeki telefon numarası.|
|Takma|**Takma Ad** özelliğindeki ad.|
|OfficeLocation|**Office** veya **Office konum** özelliğindeki değer.|
|OtherAddress|**Diğer** adres özelliğinin değeri.|
|Soyadı|**Soyadı** özelliğindeki ad.|
|Başlık|İş başlığı özelliğindeki **başlık** .|

## <a name="searchable-sensitive-data-types"></a>Aranabilir hassas veri türleri

SharePoint ve OneDrive İş sitelerindeki belgelerde depolanan kredi kartı numaraları veya sosyal güvenlik numaraları gibi hassas verileri aramak için uyumluluk portalındaki eBulma arama araçlarını kullanabilirsiniz. Bunu yapmak için anahtar sözcük sorgusundaki `SensitiveType` hassas bilgi türünün özelliğini ve adını (veya kimliğini) kullanabilirsiniz. Örneğin, sorgu `SensitiveType:"Credit Card Number"` kredi kartı numarası içeren belgeleri döndürür. Sorgu  `SensitiveType:"U.S. Social Security Number (SSN)"` , ABD sosyal güvenlik numarası içeren belgeleri döndürür.

Arayabileceğiniz hassas bilgi türlerinin listesini görmek için uyumluluk portalında **Veri sınıflandırmaları** \> **Hassas bilgi türleri'ne** gidin. Hassas bilgi türlerinin listesini görüntülemek için Güvenlik & Uyumluluk Merkezi PowerShell'de **Get-DlpSensitiveInformationType** cmdlet'ini de kullanabilirsiniz.

özelliğini kullanarak `SensitiveType` sorgu oluşturma hakkında daha fazla bilgi için bkz. [Sitelerde depolanan hassas verileri bulmak için sorgu oluşturma](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Hassas veri türlerini arama sınırlamaları

- Özel hassas bilgi türlerini aramak için özelliğinde hassas bilgi türünün `SensitiveType` kimliğini belirtmeniz gerekir. Özel bir hassas bilgi türünün adını kullanmak (önceki bölümde yerleşik hassas bilgi türleri örneğinde gösterildiği gibi) hiçbir sonuç döndürmez. Yerleşik **ve** özel hassas bilgi türlerini ayırt etmek için uyumluluk merkezindeki **Hassas bilgi türleri** sayfasındaki (veya PowerShell'deki Publisher özelliği) **Publisher** sütununu kullanın. Yerleşik hassas veri türleri **, Publisher** özelliği için değerine `Microsoft Corporation` sahiptir.

  Kuruluşunuzdaki özel hassas veri türlerinin adını ve kimliğini görüntülemek için Güvenlik & Uyumluluk Merkezi PowerShell'de aşağıdaki komutu çalıştırın:

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Ardından arama özelliğindeki `SensitiveType` kimliği kullanarak özel hassas veri türünü içeren belgeleri döndürebilirsiniz; örneğin, `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Exchange Online posta kutularında bekleyen hassas verileri aramak için hassas bilgi türlerini ve `SensitiveType` arama özelliğini kullanamazsınız. Buna 1:1 sohbet iletileri, 1:N grup sohbet iletileri ve Microsoft Teams ekip kanalı konuşmaları dahildir çünkü bu içeriğin tümü posta kutularında depolanır. Ancak, aktarım sırasındaki hassas e-posta verilerini korumak için veri kaybı önleme (DLP) ilkelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinme](dlp-learn-about-dlp.md) ve [Kişisel verileri arama ve bulma](/compliance/regulatory/gdpr).

## <a name="search-operators"></a>Arama işleçleri

**AND**, **OR** ve **NOT** gibi Boole arama işleçleri, arama sorgusuna belirli sözcükleri ekleyerek veya dışlayarak daha hassas aramalar tanımlamanıza yardımcı olur. Özellik işleçlerini (veya `..`gibi`>=`), tırnak işaretlerini, parantezleri ve joker karakterleri kullanma gibi diğer teknikler, arama sorgusunu geliştirmenize yardımcı olur. Aşağıdaki tabloda, arama sonuçlarını daraltmak veya genişletmek için kullanabileceğiniz işleçler listelenmiştir.

|Işleç|Kullanım|Açıklama|
|---|---|---|
|VE|anahtar sözcük1 VE anahtar sözcüğü2|Belirtilen tüm anahtar sözcükleri veya  `property:value` ifadeleri içeren öğeleri döndürür. Örneğin,  `from:"Ann Beebe" AND subject:northwind` Ann Beebe tarafından gönderilen ve konu satırında northwind sözcüğünü içeren tüm iletileri döndürür. <sup>2</sup>|
|+|anahtar sözcük1 + anahtar sözcük2 + anahtar sözcük3|veya `keyword3` *içeren*`keyword2` *ve* içeren `keyword1`öğeleri döndürür.   Bu nedenle, bu örnek sorgusuna  `(keyword2 OR keyword3) AND keyword1`eşdeğerdir. <p> Sorgu  `keyword1 + keyword2` (simgeden **+** sonra boşlukla), **AND** işlecini kullanmakla aynı değildir. Bu sorgu ile eşdeğerdir  `"keyword1 + keyword2"` ve tam aşamasına  `"keyword1 + keyword2"`sahip öğeleri döndürür.|
|VEYA|anahtar sözcük1 VEYA anahtar sözcük2|Belirtilen anahtar sözcüklerden veya ifadelerden birini veya  `property:value` daha fazlasını içeren öğeleri döndürür. <sup>2</sup>|
|DEĞİL|anahtar sözcük1 NOT anahtar sözcüğü2 <p> NOT from:"Ann Beebe" <p> NOT kind:im|Bir anahtar sözcük veya  `property:value` ifade tarafından belirtilen öğeleri dışlar. İkinci örnekte Ann Beebe tarafından gönderilen iletiler dışlanır. Üçüncü örnek, Konuşma Geçmişi posta kutusu klasörüne kaydedilen Skype Kurumsal konuşmalar gibi anlık ileti konuşmalarını dışlar. <sup>2</sup>|
|-|anahtar sözcük1 -anahtar sözcük2|**NOT** işleciyle aynı. Bu nedenle, bu sorgu içeren  `keyword1` öğeleri döndürür ve içeren  `keyword2`öğeleri hariç tutar.|
|YAKIN -INDAKİ|keyword1 NEAR(n) anahtar sözcüğü2|Birbirine yakın sözcükler içeren öğeleri döndürür; burada n sözcük sayısı birbirinden ayrılır. Örneğin, `best NEAR(5) worst` "en kötü" sözcüğünün "en iyi" sözcüğünün beş sözcüğü içinde olduğu herhangi bir öğeyi döndürür. Sayı belirtilmezse, varsayılan uzaklık sekiz sözcük olur. <sup>2</sup>|
|:|property:value|İki nokta üst üste (:) söz diziminde  `property:value` , aranmakta olan özelliğin değerinin belirtilen değeri içerdiğini belirtir. Örneğin,  `recipients:garthf@contoso.com` garthf@contoso.com gönderilen tüm iletileri döndürür.|
|=|property=value|**ile aynıdır:** işleci.|
|\<|propertyvalue\<|Aranmakta olan özelliğin belirtilen değerden küçük olduğunu belirtir. <sup>1</sup>|
|\>|propertyvalue\>|Aranmakta olan özelliğin belirtilen değerden büyük olduğunu belirtir. <sup>1</sup>|
|\<=|property\<=value|Aranan özelliğin belirli bir değerden küçük veya buna eşit olduğunu belirtir. <sup>1</sup>|
|\>=|property\>=value|Aranan özelliğin belirli bir değerden büyük veya buna eşit olduğunu belirtir. <sup>1</sup>|
|..|property:value1.. değer2|Aranan özelliğin değer1'den büyük veya buna eşit ve değer2'den küçük veya buna eşit olduğunu belirtir. <sup>1</sup>|
|"  "|"eşit değer" <p> konu:"Çeyreklik Mali Durumlar"|Anahtar sözcük sorgusunda (anahtar **sözcük kutusuna** `property:value` çifti yazdığınız yerde), tam bir tümcecik veya terim aramak için çift tırnak işareti (" ") kullanın. Ancak **Konu** veya **Konu/Başlık** [arama koşulu](#search-conditions) koşulu kullanıyorsanız, bu arama koşulları kullanılırken tırnak işaretleri otomatik olarak eklendiğinden değere çift tırnak işareti eklemeyin. Değere tırnak işareti eklerseniz, koşul değerine iki çift çift tırnak eklenir ve arama sorgusu hata döndürür. |
|\*|Kedi\* <p> subject:set\*|Anahtar sözcüklerde veya `property:value` sorgularda bir sözcüğün sonuna joker karakter ( * ) yerleştirildiği önek aramaları (*ön ek eşleştirme* olarak da adlandırılır). Ön ek aramalarında arama, sözcüğü içeren terimleri ve ardından sıfır veya daha fazla karakteri içeren sonuçlar döndürür. Örneğin, `title:set*` belge başlığında "set", "setup" ve "setting" sözcüklerini (ve "set" ile başlayan diğer sözcükleri) içeren belgeleri döndürür. <p> **Not:** Yalnızca ön ek aramalarını kullanabilirsiniz; örneğin, **cat\**_ veya _* set\**_. Sonek aramaları (_*\*kedi**), infix aramaları (**ct\***) ve alt dize aramaları (**\*kedi\***) desteklenmez. <p> Ayrıca nokta ekleme ( \. ) için bir ön ek araması döndürülen sonuçları değiştirir. Bunun nedeni noktanın bir durdurma sözcüğü olarak değerlendirilmesidir. Örneğin, **cat\**_ araması ve _* cat.\* araması** farklı sonuçlar döndürür. Ön ek aramasında nokta kullanmamanızı öneririz.|
|(  )|(adil VEYA ücretsiz) AND (kimden:contoso.com) <p> (IPO VEYA başlangıç) AND (hisse senedi VEYA hisse senetleri) <p> (üç aylık finansallar)|Parantezler Boole tümceciklerini,  `property:value` öğelerini ve anahtar sözcüklerini bir arada gruplandırıyor. Örneğin,  `(quarterly financials)` üç aylık ve finansal sözcükleri içeren öğeleri döndürür.|

> [!NOTE]
> <sup>1</sup> Tarih veya sayısal değerlere sahip özellikler için bu işleci kullanın.<br/> <sup>2</sup> Boole arama işleci büyük harf olmalıdır; örneğin **, AND**. **ve** gibi küçük harfli bir işleç kullanırsanız, arama sorgusunda anahtar sözcük olarak değerlendirilir.

## <a name="search-conditions"></a>Arama koşulları

Bir aramayı daraltmak ve daha iyileştirilmiş bir sonuç kümesi döndürmek için arama sorgusuna koşullar ekleyebilirsiniz. Her koşul, aramayı başlattığınızda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler.

[Ortak özellikler için koşullar](#conditions-for-common-properties)

[Posta özellikleri koşulları](#conditions-for-mail-properties)

[Belge özellikleri koşulları](#conditions-for-document-properties)

[Koşullarla kullanılan işleçler](#operators-used-with-conditions)

[Koşulları kullanma yönergeleri](#guidelines-for-using-conditions)

[Arama sorgularında koşulları kullanma örnekleri](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Ortak özellikler için koşullar

Aynı aramada posta kutularını ve siteleri ararken ortak özellikleri kullanarak bir koşul oluşturun. Aşağıdaki tabloda, koşul eklerken kullanılacak kullanılabilir özellikler listelenmektedir.

|Durum|Açıklama|
|---|---|
|Tarih|E-posta için, iletinin bir alıcı tarafından alındığı veya gönderen tarafından gönderildiği tarih. Belgeler için, belgenin son değiştirildiği tarih.|
|Gönderen/Yazar|E-posta için, ileti gönderen kişi. Belgeler için, Office belgelerden yazar alanında alıntı yapılan kişi. Virgülle ayırarak birden fazla ad yazabilirsiniz. İki veya daha fazla değer **OR** işleci tarafından mantıksal olarak bağlanır.|
|Boyut (bayt cinsinden)|Hem e-posta hem de belgeler için öğenin boyutu (bayt cinsinden).|
|Konu/Başlık|E-posta için, iletinin konu satırındaki metin. Belgeler için, belgenin başlığı. Daha önce açıklandığı gibi Title özelliği, Microsoft Office belgelerde belirtilen meta verilerdir. Birden çok konu/başlık değerinin adını virgülle ayırarak yazabilirsiniz. İki veya daha fazla değer **OR** işleci tarafından mantıksal olarak bağlanır. <p> **Not**: Bu arama koşulu kullanılırken tırnak işaretleri otomatik olarak eklendiğinden, bu koşulun değerlerine çift tırnak işareti eklemeyin. Değere tırnak işareti eklerseniz, koşul değerine iki çift tırnak eklenir ve arama sorgusu hata döndürür.|
|Bekletme etiketi|Hem e-posta hem de belgeler için, iletilere ve belgelere otomatik olarak veya el ile uygulanabilen bekletme etiketleri. Bekletme etiketleri, kayıtları bildirmek ve etiket tarafından belirtilen saklama ve silme kurallarını zorunlu kılarak içeriğin veri yaşam döngüsünü yönetmenize yardımcı olmak için kullanılabilir. Bekletme etiketi adının bir bölümünü yazabilir ve joker karakter kullanabilir veya tam etiket adını yazabilirsiniz. Bekletme etiketleri hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).|

### <a name="conditions-for-mail-properties"></a>Posta özellikleri koşulları

Posta kutularını veya ortak klasörleri ararken posta özelliklerini kullanarak bir koşul oluşturun. Aşağıdaki tabloda, bir koşul için kullanabileceğiniz e-posta özellikleri listelenmektedir. Bu özellikler, daha önce açıklanan e-posta özelliklerinin bir alt kümesidir. Bu açıklamalar kolaylık sağlamak için yinelenir.

|Durum|Açıklama|
|---|---|
|İleti türü|Aranacak ileti türü. Bu, Kind e-posta özelliğiyle aynı özelliktir. Olası değerler: <ul><li>Kişiler</li><li>Dokümanlar</li><li>E-posta</li><li>externaldata</li><li>Faks</li><li>Im</li><li>Günlük</li><li>Toplantı</li><li>microsoftteams</li><li>Notlar</li><li>Mesaj</li><li>rssfeeds</li><li>Görev</li><li>Sesli</li></ul>|
|Katılımcı|E-posta iletisindeki tüm kişiler alanları. Bu alanlar Kimden, Kime, Bilgi ve Gizli alanlarıdır.|
|Tür|E-posta öğesinin ileti sınıfı özelliği. Bu, ItemClass e-posta özelliğiyle aynı özelliktir. Aynı zamanda çok değerli bir koşuldur. Birden çok ileti sınıfı seçmek için **CTRL** tuşunu basılı tutun ve ardından koşula eklemek istediğiniz açılan listede iki veya daha fazla ileti sınıfına tıklayın. Listede seçtiğiniz her ileti sınıfı, ilgili arama sorgusundaki **OR** işleci tarafından mantıksal olarak bağlanır. <p> Exchange tarafından kullanılan ve **İleti sınıfı** listesinde seçebileceğiniz ileti sınıflarının listesi için bkz [. Öğe Türleri ve İleti Sınıfları](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Alınan|E-posta iletisinin alıcı tarafından alındığı tarih. Bu, Alınan e-posta özelliğiyle aynı özelliktir.|
|Alıcı|E-posta iletisindeki tüm alıcı alanları. Bu alanlar Kime, Bilgi ve Gizli alanlarıdır.|
|Gönderen|E-posta iletisinin göndereni.|
|Gönderilen|Gönderen tarafından e-posta iletisinin gönderildiği tarih. Bu, Gönderilmiş e-posta özelliğiyle aynı özelliktir.|
|Konu|E-posta iletisinin konu satırındaki metin. <p> **Not**: Bu arama koşulu kullanılırken tırnak işaretleri otomatik olarak eklendiğinden, bu koşulun değerlerine çift tırnak işareti eklemeyin. Değere tırnak işareti eklerseniz, koşul değerine iki çift tırnak eklenir ve arama sorgusu hata döndürür.|
|Hedef|E-posta iletisinin Alıcı alanındaki alıcısı.|

### <a name="conditions-for-document-properties"></a>Belge özellikleri koşulları

SharePoint ve OneDrive İş sitelerinde belge ararken belge özelliklerini kullanarak bir koşul oluşturun. Aşağıdaki tabloda, bir koşul için kullanabileceğiniz belge özellikleri listelenmektedir. Bu özellikler, daha önce açıklanan site özelliklerinin bir alt kümesidir. Bu açıklamalar kolaylık sağlamak için yinelenir.

|Durum|Açıklama|
|---|---|
|Yazar|Office belgedeki yazar alanı, belge kopyalandığında kalıcı olur. Örneğin, bir kullanıcı bir belge oluşturursa ve belgeyi başka birine e-postayla SharePoint, belge özgün yazarı korur.|
|Başlık|Belgenin başlığı. Title özelliği, Office belgelerde belirtilen meta verilerdir. Belgenin dosya adından farklıdır.|
|Oluşturuldu|Belgenin oluşturulduğu tarih.|
|Son değiştirme|Belgenin son değiştirildiği tarih.|
|Dosya türü|Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx. Bu, FileExtension site özelliğiyle aynı özelliktir. <p> **Not:** Bir arama sorgusuna **Eşittir** veya **Eşittir** işlecini kullanan bir Dosya türü koşulu eklerseniz, bir dosya türünün tüm sürümlerini döndürmek için bir ön ek araması (dosya türünün sonuna joker karakter ( \* ) ekleyerek) kullanamazsınız. Bunu yaparsanız joker karakter yoksayılır. Örneğin koşulunu `Equals any of doc*`eklerseniz, yalnızca uzantısına `.doc` sahip dosyalar döndürülür. uzantısına `.docx` sahip dosyalar döndürülmeyecek. Bir dosya türünün tüm sürümlerini döndürmek için anahtar sözcük sorgusunda *property:value* çiftini kullandı; örneğin, `filetype:doc*`.|

### <a name="operators-used-with-conditions"></a>Koşullarla kullanılan işleçler

Koşul eklediğinizde, koşul için özellik türüyle ilgili bir işleç seçebilirsiniz. Aşağıdaki tabloda koşullarla birlikte kullanılan işleçler açıklanır ve arama sorgusunda kullanılan eşdeğeri listelenir.

|Işleç|Sorgu eşdeğeri|Açıklama|
|---|---|---|
|Sonra|`property>date`|Tarih koşullarıyla kullanılır. Belirtilen tarihten sonra gönderilen, alınan veya değiştirilen öğeleri döndürür.|
|Önce|`property<date`|Tarih koşullarıyla kullanılır. Belirtilen tarihten önce gönderilen, alınan veya değiştirilen öğeleri döndürür.|
|Arasında|`date..date`|Tarih ve boyut koşullarıyla kullanın. Tarih koşuluyla kullanıldığında, belirtilen tarih aralığında gönderilmiş, alınmış veya değiştirilmiş olan öğeleri döndürür. Boyut koşuluyla kullanıldığında, boyutu belirtilen aralık içinde olan öğeleri döndürür.|
|Herhangi birini içerir|`(property:value) OR (property:value)`|Bir dize değeri belirten özellikler için koşullarla birlikte kullanılır. Belirtilen bir veya daha fazla dize değerinin herhangi bir bölümünü içeren öğeleri döndürür.|
|İçermez|`-property:value` <p> `NOT property:value`|Bir dize değeri belirten özellikler için koşullarla birlikte kullanılır. Belirtilen dize değerinin herhangi bir bölümünü içermeyen öğeleri döndürür.|
|Herhangi birine eşit değildir|`-property=value` <p> `NOT property=value`|Bir dize değeri belirten özellikler için koşullarla birlikte kullanılır. Belirli bir dizeyi içermeyen öğeleri döndürür.|
|Eşit -tir|`size=value`|Belirtilen boyuta eşit öğeleri döndürür. <sup>1</sup>|
|Herhangi birine eşit|`(property=value) OR (property=value)`|Bir dize değeri belirten özellikler için koşullarla birlikte kullanılır. Belirtilen bir veya daha fazla dize değeriyle eşleşen öğeleri döndürür.|
|Büyük|`size>value`|Belirtilen özelliğin belirtilen değerden büyük olduğu öğeleri döndürür. <sup>1</sup>|
|Büyük veya eşit|`size>=value`|Belirtilen özelliğin belirtilen değerden büyük veya buna eşit olduğu öğeleri döndürür. <sup>1</sup>|
|Daha az|`size<value`|Belirli bir değerden büyük veya buna eşit öğeleri döndürür. <sup>1</sup>|
|Daha az veya eşit|`size<=value`|Belirli bir değerden büyük veya buna eşit öğeleri döndürür. <sup>1</sup>|
|Eşit değil|`size<>value`|Belirtilen boyuta eşit olmayan öğeleri döndürür. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Bu işleç yalnızca Size özelliğini kullanan koşullar için kullanılabilir.

### <a name="guidelines-for-using-conditions"></a>Koşulları kullanma yönergeleri

Arama koşullarını kullanırken aşağıdakileri göz önünde bulundurun.

- Koşul, **AND** işleci tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de sonuçlara dahil edilecek koşulu karşılaması gerektiğini gösterir. Koşulların sonuçlarınızı daraltmanıza bu şekilde yardımcı olur.

- Arama sorgusuna iki veya daha fazla benzersiz koşul eklerseniz (farklı özellikler belirten koşullar), bu koşullar **AND** işleci tarafından mantıksal olarak bağlanır. Bu, yalnızca tüm koşulları karşılayan öğelerin (herhangi bir anahtar sözcük sorgusuna ek olarak) döndürüldüğünü gösterir.

- Aynı özellik için birden fazla koşul eklerseniz, bu koşullar **OR** işleci tarafından mantıksal olarak bağlanır. Bu, anahtar sözcük sorgusunu karşılayan öğelerin ve koşullardan herhangi birinin döndürüldüğünü gösterir. Bu nedenle, aynı koşulların grupları **OR** işleci tarafından birbirine bağlanır ve ardından benzersiz koşul kümeleri **AND** işleci tarafından bağlanır.

- Tek bir koşula birden çok değer (virgül veya noktalı virgülle ayrılmış) eklerseniz, bu değerler **OR** işleci tarafından bağlanır. Başka bir deyişle, koşuldaki özellik için belirtilen değerlerden herhangi birini içeren öğeler döndürülür.

- **İçerir** ve **Eşittir** mantığına sahip bir işleç kullanan tüm koşullar, basit dize aramaları için benzer arama sonuçları döndürür. Basit dize araması, koşulda joker karakter içermeyen bir dizedir). Örneğin, **Herhangi birine Eşit'i** kullanan bir koşul, herhangi birini **içerir** seçeneğini kullanan bir koşulla aynı öğeleri döndürür.

- Anahtar sözcükler kutusu ve koşullar kullanılarak oluşturulan arama sorgusu, **Arama sayfasında,** seçili aramanın ayrıntılar bölmesinde görüntülenir. Sorguda, gösterimin  `(c:c)` sağındaki her şey sorguya eklenen koşulları gösterir.

- Koşullar yalnızca arama sorgusuna özellikler ekler; işleç eklemez. Bu nedenle ayrıntı bölmesinde görüntülenen sorgu, gösterimin  `(c:c)` sağında işleçleri göstermez. KQL, sorgu yürütülürken mantıksal işleçleri (önceden açıklanan kurallara göre) ekler.

- Koşulların sırasını yeniden sorgulamak için sürükle ve bırak denetimini kullanabilirsiniz. Bir koşulun denetimine tıklayın ve yukarı veya aşağı taşıyın.

- Daha önce açıklandığı gibi, bazı koşul özellikleri birden çok değer (noktalı virgülle ayrılmış) yazmanıza olanak sağlar. Her değer **OR** işleci tarafından mantıksal olarak bağlanır ve sorguyla `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)`sonuçlanır. Aşağıdaki çizimde, birden çok değer içeren bir koşul örneği gösterilmektedir.

    ![Birden çok değer içeren bir koşul.](../media/SearchConditions1.png)

  > [!NOTE]
  > Birden çok koşul ekleyemezsiniz (aynı özellik için **koşul ekle'ye** tıklayarak). Bunun yerine, önceki örnekte gösterildiği gibi koşul için birden çok değer sağlamanız gerekir (noktalı virgülle ayrılmıştır).

### <a name="examples-of-using-conditions-in-search-queries"></a>Arama sorgularında koşulları kullanma örnekleri

Aşağıdaki örneklerde bir arama sorgusunun gui tabanlı sürümü ve koşullar, seçili aramanın ayrıntılar bölmesinde görüntülenen arama sorgusu söz dizimi (**Get-ComplianceSearch** cmdlet'i tarafından da döndürülür) ve ilgili KQL sorgusunun mantığı gösterilir.

#### <a name="example-1"></a>Örnek 1

Bu örnek, kredi kartı numarası içeren ve en son 1 Ocak 2021'de değiştirilmiş SharePoint ve OneDrive İş sitelerindeki belgeleri döndürür.

**GUI**:

![Arama koşullarının ilk örneği.](../media/SearchConditions2.png)

**Arama sorgusu söz dizimi**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Arama sorgusu mantığı**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Önceki ekran görüntüsünde arama kullanıcı arabiriminin anahtar sözcük sorgusunun ve koşulunun **AND** işleci tarafından bağlandığını güçlendirdiğini görebilirsiniz.

#### <a name="example-2"></a>Örnek 2

Bu örnek, "rapor" anahtar sözcüğünü içeren, 1 Nisan 2021'de gönderilen veya oluşturulan ve e-posta iletilerinin konu alanında veya belgelerin başlık özelliğinde "northwind" sözcüğünü içeren e-posta öğelerini veya belgeleri döndürür. Sorgu, diğer arama ölçütlerine uyan Web sayfalarını dışlar.

**GUI**:

![İkinci arama koşulları örneği.](../media/SearchConditions3.png)

**Arama sorgusu söz dizimi**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Arama sorgusu mantığı**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Örnek 3

Bu örnek, 1 Aralık 2019 ile 30 Kasım 2020 arasında gönderilen ve "telefon" veya "akıllı telefon" ile başlayan sözcükleri içeren e-posta iletilerini veya takvim toplantılarını döndürür.

**GUI**:

![Üçüncü arama koşulları örneği.](../media/SearchConditions4.png)

**Arama sorgusu söz dizimi**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Arama sorgusu mantığı**:

`phone* OR smartphone* AND (sent=2019-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Özel karakterler

Bazı özel karakterler arama dizinine dahil edilmez ve bu nedenle aranamaz. Bu, arama sorgusundaki arama işleçlerini temsil eden özel karakterleri de içerir. Burada, gerçek arama sorgusunda boş bir boşlukla değiştirilen veya arama hatasına neden olan özel karakterlerin listesi yer alır.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Dış kullanıcılarla paylaşılan site içeriğini arama

Kuruluşunuzun dışındaki kişilerle paylaşılan SharePoint ve OneDrive İş sitelerinde depolanan belgeleri aramak için uyumluluk merkezindeki eBulma arama araçlarını da kullanabilirsiniz. Bu, kuruluşunuzun dışında paylaşılmakta olan hassas veya özel bilgileri belirlemenize yardımcı olabilir. Bir anahtar sözcük sorgusunda  `ViewableByExternalUsers` özelliğini kullanarak bunu yapabilirsiniz. Bu özellik, aşağıdaki paylaşım yöntemlerinden biri kullanılarak dış kullanıcılarla paylaşılan belgeleri veya siteleri döndürür:

- Kullanıcıların kuruluşunuzda kimliği doğrulanmış kullanıcı olarak oturum açmasını gerektiren paylaşım daveti.
- Bu bağlantıya sahip olan herkesin kimliğinin doğrulanması gerekmeden kaynağa erişmesine olanak tanıyan anonim bir konuk bağlantısı.

İşte birkaç örnek:

- Sorgu  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` , kuruluşunuzun dışındaki kişilerle paylaşılan ve kredi kartı numarası içeren tüm öğeleri döndürür.
- Sorgu  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` , kuruluştaki dış kullanıcılarla paylaşılan tüm ekip sitelerindeki belgelerin listesini döndürür.

> [!TIP]
> gibi  `ViewableByExternalUsers:true AND ContentType:document` bir arama sorgusu, arama sonuçlarında çok sayıda .aspx dosyası döndürebilir. Bunları (veya diğer dosya türlerini) ortadan kaldırmak için özelliğini kullanarak  `FileExtension` belirli dosya türlerini hariç tutabilirsiniz; örneğin  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx`.

Kuruluşunuzun dışındaki kişilerle paylaşılan içerik olarak kabul edilen içerik nedir? Kuruluşunuzun SharePoint ve OneDrive İş sitelerindeki, paylaşım daveti göndererek paylaşılan veya ortak konumlarda paylaşılan belgeler. Örneğin, aşağıdaki kullanıcı etkinlikleri dış kullanıcılar tarafından görüntülenebilir içerikle sonuçlanır:

- Kullanıcı, kuruluşunuzun dışındaki bir kişiyle dosya veya klasör paylaşır.
- Kullanıcı paylaşılan bir dosyanın bağlantısını oluşturur ve kuruluşunuzun dışındaki bir kişiye gönderir. Bu bağlantı, dış kullanıcının dosyayı görüntülemesine (veya düzenlemesine) olanak tanır.
- Kullanıcı, paylaşılan dosyayı görüntülemek (veya düzenlemek) için kuruluşunuzun dışındaki bir kişiye paylaşım daveti veya konuk bağlantısı gönderir.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>ViewableByExternalUsers özelliğini kullanma sorunları

`ViewableByExternalUsers` özelliği, bir belgenin veya sitenin dış kullanıcılarla paylaşılıp paylaşılmadığının durumunu temsil ederken, bu özelliğin ne yaptığı ve yansıtmadığı konusunda bazı uyarılar vardır. Aşağıdaki senaryolarda özelliğin  `ViewableByExternalUsers` değeri güncelleştirilmez ve bu özelliği kullanan bir arama sorgusunun sonuçları yanlış olabilir.

- Bir site veya kuruluş için dış paylaşımı kapatma gibi paylaşım ilkesi değişiklikleri. Özellik, dış erişim iptal edilmiş olsa bile daha önce paylaşılan belgeleri dışarıdan erişilebilir olarak göstermeye devam eder.
- Dış kullanıcıları Microsoft 365 Grupları veya Microsoft 365 güvenlik gruplarına ekleme veya kaldırma gibi grup üyeliği değişiklikleri. Özellik, grubun erişimi olan öğeler için otomatik olarak güncelleştirilmez.
- Alıcının daveti kabul etmediği ve bu nedenle henüz içeriğe erişimi olmayan dış kullanıcılara paylaşım davetleri gönderme.

Bu senaryolarda,  `ViewableByExternalUsers` site veya belge kitaplığı yeniden gezilinceye ve yeniden dizine alınana kadar özellik geçerli paylaşım durumunu yansıtmaz.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Kuruluşunuzda paylaşılan site içeriğini arama

Daha önce açıklandığı gibi özelliğini kullanarak  `SharedWithUsersOWSUser` kuruluşunuzdaki kişiler arasında paylaşılan belgeleri arayabilirsiniz. Bir kişi, kuruluşunuzdaki başka bir kullanıcıyla dosya (veya klasör) paylaştığında, paylaşılan dosyanın bağlantısı, dosyanın paylaşıldığı kişinin OneDrive İş hesabındaki **Benimle** paylaşılan sayfasında görünür. Örneğin, Sara Davis ile paylaşılan belgeleri aramak için sorgusunu  `SharedWithUsersOWSUser:"sarad@contoso.com"`kullanabilirsiniz. Bu aramanın sonuçlarını dışarı aktarırsanız, özgün belgeler (Belgeleri Sara ile paylaşan kişinin içerik konumunda bulunur) indirilir.

Özelliği kullanılırken  `SharedWithUsersOWSUser` arama sonuçlarında döndürülmek için belgelerin belirli bir kullanıcıyla açıkça paylaşılması gerekir. Örneğin, bir kişi OneDrive hesabında bir belge paylaştığında, belgeyi herkesle (kuruluşun içinde veya dışında) paylaşma, yalnızca kuruluş içindeki kişilerle paylaşma veya belirli bir kişiyle paylaşma seçeneğine sahiptir. OneDrive'daki **Paylaş** penceresinin üç paylaşım seçeneğini gösteren ekran görüntüsü.

![Yalnızca belirli kişilerle paylaşılan dosyalar SharedWithUsersOWSUser özelliğini kullanan bir arama sorgusu tarafından döndürülür.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Yalnızca üçüncü seçenek kullanılarak paylaşılan belgeler ( **Belirli kişilerle** paylaşılan) özelliğini kullanan  `SharedWithUsersOWSUser` bir arama sorgusu tarafından döndürülür.

## <a name="searching-for-skype-for-business-conversations"></a>Skype Kurumsal konuşmaları arama

özellikle Skype Kurumsal konuşmalardaki içeriği aramak için aşağıdaki anahtar sözcük sorgusunu kullanabilirsiniz:

```powershell
kind:im
```

Önceki arama sorgusu, Microsoft Teams sohbetlerini de döndürür. Bunu önlemek için, aşağıdaki anahtar sözcük sorgusunu kullanarak arama sonuçlarını yalnızca Skype Kurumsal konuşmaları içerecek şekilde daraltabilirsiniz:

```powershell
kind:im AND subject:conversation
```

Önceki anahtar sözcük sorgusu, Skype Kurumsal konuşmalar "Konuşma" sözcüğüyle başlayan bir Konu satırıyla e-posta iletileri olarak kaydedildiğinden, Microsoft Teams sohbetleri dışlar.

Belirli bir tarih aralığında gerçekleşen Skype Kurumsal konuşmaları aramak için aşağıdaki anahtar sözcük sorgusunu kullanın:

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Aramalar için karakter sınırları

SharePoint sitelerde ve OneDrive hesaplarında içerik ararken arama sorguları için 4.000 karakter sınırı vardır.
Arama sorgusundaki toplam karakter sayısı şu şekilde hesaplanır:

- Anahtar sözcük arama sorgusundaki karakterler (hem kullanıcı hem de filtre alanları dahil) bu sınıra göre sayılır.
- Herhangi bir konum özelliğindeki karakterler (tüm SharePoint sitelerin URL'leri veya aranmakta olan OneDrive konumlar gibi) bu sınıra göre sayılır.
- Tüm arama izinleri filtrelerindeki karakterler, sınıra göre arama sayısını çalıştıran kullanıcıya uygulanır.

Karakter sınırları hakkında daha fazla bilgi için bkz. [eBulma arama sınırları](limits-for-content-search.md#search-limits).

> [!NOTE]
> 4.000 karakter sınırı İçerik arama, eBulma (Standart) ve eBulma (Premium) için geçerlidir.

## <a name="search-tips-and-tricks"></a>Arama ipuçları ve püf noktaları

- Anahtar sözcük aramaları büyük/küçük harfe duyarlı değildir. Örneğin, **kedi** ve **CAT** aynı sonuçları döndürür.

- Boole işleçleri **VE**, **OR**, **NOT** ve **NEAR** büyük harf olmalıdır.

- İki anahtar sözcük veya iki  `property:value` ifade arasındaki boşluk **, AND** kullanımıyla aynıdır. Örneğin,  `from:"Sara Davis" subject:reorganization` Sara Davis tarafından gönderilen ve konu satırında yeniden düzenleme sözcüğünü içeren tüm iletileri döndürür.

- Biçimle eşleşen söz dizimini `property:value` kullanın. Değerler büyük/küçük harfe duyarlı değildir ve işlecinden sonra boşluk olamaz. Boşluk varsa, hedeflenen değer tam metin araması olur. Örneğin `to: pilarp` , pilarp'e gönderilen iletiler yerine anahtar sözcük olarak "pilarp" sözcüğünü arar.

- Kime, Kimden, Bilgi veya Alıcılar gibi bir alıcı özelliğinde arama yaparken, alıcıyı belirtmek için SMTP adresi, diğer ad veya görünen ad kullanabilirsiniz. Örneğin, pilarp@contoso.com, pilarp veya "Pilar Pinilla" kullanabilirsiniz.

- Yalnızca ön ek aramalarını kullanabilirsiniz; örneğin, **cat\**_ veya _* set\**_. Sonek aramaları (_*\*kedi**), infix aramaları (**ct\***) ve alt dize aramaları (**\*kedi\***) desteklenmez.

- Bir özellikte arama yaparken, arama değeri birden çok sözcükden oluşuyorsa çift tırnak işareti (" ") kullanın. Örneğin `subject:budget Q1` , konu satırında **bütçe** içeren ve iletinin herhangi bir yerinde veya ileti özelliklerinden herhangi birinde **Q1** içeren iletileri döndürür. kullanma `subject:"budget Q1"` , konu satırının herhangi bir yerinde **bütçe Q1** içeren tüm iletileri döndürür.

- Belirli bir özellik değeriyle işaretlenmiş içeriği arama sonuçlarınızdan dışlamak için, özelliğin adının önüne eksi işareti (-) koyun. Örneğin, `-from:"Sara Davis"` Sara Davis tarafından gönderilen tüm iletileri hariç tutar.

- İleti türüne göre öğeleri dışarı aktarabilirsiniz. Örneğin, Microsoft Teams Skype konuşmaları ve sohbetleri dışarı aktarmak için söz dizimini `kind:im`kullanın. Yalnızca e-posta iletilerini döndürmek için kullanabilirsiniz `kind:email`. Microsoft Teams'de sohbetleri, toplantıları ve aramaları döndürmek için kullanın`kind:microsoftteams`.

- Daha önce açıklandığı gibi, sitelerde arama yaparken yalnızca belirtilen sitedeki öğeleri döndürmek için özelliğini kullanırken `path` URL'nin sonuna sondakini `/` eklemeniz gerekir. Sondaki `/`öğesini eklemezseniz, benzer yol adına sahip bir sitedeki öğeler de döndürülür. Örneğin, kullanırsanız `path:sites/HelloWorld` veya `sites/HelloWorld_West` adlı `sites/HelloWorld_East` sitelerdeki öğeler de döndürülür. Yalnızca HelloWorld sitesinden öğe döndürmek için kullanmanız `path:sites/HelloWorld/`gerekir.
