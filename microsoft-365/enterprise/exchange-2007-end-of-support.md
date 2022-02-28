---
title: Exchange 2007 end of support roadmap
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: 2007 destek Exchange Server sonra seçenekleriniz hakkında bilgi edinmek ve 2016'da Microsoft 365, Office 365 veya başka bir Exchange planlamaya başlayabilirsiniz.
ms.openlocfilehash: d5e79666c0e8e9804a63c89a0095a8725f14cd35
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984490"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 end of support roadmap

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Exchange Server 2007'de destek sonuna Nisan 2017'de ulaşıldı. Exchange 2007'den Microsoft 365, Office 365 veya Exchange 2016'ya geçiş işlemini başlatmadınız, şimdi planlamaya başlamanın tam zamanı.
  
## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Exchange Server neredeyse bütün Microsoft ürünleri gibi diğer tüm Microsoft ürünlerinin de bir destek yaşam döngüsü vardır; bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi özellikler sağlariz. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. 11 Exchange 2007'de destek sonuna ulaşana kadar, Microsoft artık şunları sağlar:
  
- Ortaya çıkabilir sorunlar için teknik destek.
    
- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.
    
- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.
    
- Saat dilimi güncelleştirmeleri.
    
Exchange 2007 yüklemeniz destek sonu tarihini takip eden tarihten sonra da çalışmaya devam edecektir. Ancak yeni bir güncelleştirme veya destek gerektir, bu nedenle en kısa zamanda Exchange 2007'den geçişnizi kesinlikle öneririz.
  
Destek sonuna yaklaşan Office 2007 sunucularını destekleme hakkında daha fazla bilgi için bkz. [Office 2007 sunucuları ve ürünlerinden yükseltmeyi planlama](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Seçeneklerim neler?

Şunları yapabilirsiniz:
  
- Geçişin Microsoft 365, aşamalı veya karma geçişini kullanarak geçiş.
    
- Exchange 2007 sunucularınızı, şirket içi sunucu Exchange daha yeni bir sürüme geçirme.
    
Aşağıdaki bölümlerde her seçenek daha ayrıntılı olarak incelanmaktadır.
  
### <a name="migrate-to-microsoft-365"></a>Geçiş Microsoft 365

E-postanızı Microsoft 365, Exchange 2007 dağıtımınızı devre Exchange en iyi ve en basit seçenektir. Microsoft 365'a geçişle, tek sıçramada 10 yıllık bir teknolojiden en yeni özelliklere atlarsiniz:
  
- Bekletme İlkeleri, Yerinde In-Place, Yerinde eKilda ve daha fazlası gibi uyumluluk özellikleri
    
- Microsoft 365 Grupları
    
- Odaklanmış Gelen Kutusu
    
- MyAnalytics
    
- E-postaya, takvimlere, kişilere ve diğer girişlere programlı erişim için REST API'leri
    
Microsoft 365 olarak yeni özellikler ve deneyimler de edinebilirsiniz, böylece siz ve kullanıcılarınız çoğunlukla bunları hemen kullanmaya başlayabilirsiniz. Ayrıca, şu konuda kaygılanmaniz da gerek olmayacak:
  
- Donanımı satın alma ve koruma.
    
- Sunucularınızı ısıya ve soğutarak ödeme.
    
- Güvenlik, ürün ve saat dilimi düzeltmelerini güncel tutma.
    
- Uyumluluk gereksinimlerini desteklemek için depolamanın ve yazılımın bakımını yapmak.
    
- Yeni bir sürüme yükseltme Exchange. Microsoft 365 ile her zaman en son dosya sürümünü Exchange.
    
#### <a name="how-should-i-migrate-to-microsoft-365"></a>Microsoft 365'e geçiş Microsoft 365?

Birkaç geçiş seçeneği vardır. Aşağıdakiler gibi birkaç şeyi dikkate alısmalı:

- Taşımanız gereken kullanıcı veya posta kutusu sayısı.
- Geçişin ne kadar süreyle devam etmek istediğiniz.
- Şirket içi yükleme ile geçiş sırasında şirket içi yükleme arasında sorunsuz bir Microsoft 365 gerekip gerek olmadığı.

Bu tabloda, geçiş seçenekleriniz ve hangi yöntemin kullanıla birlikte kullanılamayacaklarını belirleyen en önemli faktörler yer alır:
  

|**Geçiş seçeneği**|**Kuruluş boyutu**|**Süre**|
|:-----|:-----|:-----|
|Tam geçiş  <br/> |150'den az kullanıcı  <br/> |Bir hafta veya daha kısa  <br/> |
|Aşamalı geçiş  <br/> |150'den fazla koltuk  <br/> |Birkaç hafta  <br/> |
|Tam karma geçiş  <br/> |Birkaç yüz - bin kişilik  <br/> |Birkaç ay veya daha uzun  <br/> |
   
Aşağıdaki bölümlerde bu yöntemlere genel bir bakış sağlanmıştır. Daha ayrıntılı bilgi için bkz [. Geçiş yolunu karar verme](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27). 
  
#### <a name="cutover-migration"></a>Tam geçiş

Kesin geçişte, tüm posta kutularınızı, dağıtım gruplarınızı, kişilerinizi, bu şekilde Microsoft 365 önceden seçilen bir tarih ve saatle geçirebilirsiniz. Geçiş tamamlandıktan sonra, şirket içi sunucularınızı kapatır Exchange özel olarak Microsoft 365 kullanmaya başlarsanız.
  
Tam geçiş, çok fazla posta kutusu olan, Microsoft 365'a hızlıca gitmek isteyen ve diğer yöntemlerin bazı karmaşıklıkları ile uğraşmak istemeyen küçük kuruluşlar için harika bir yöntemdir. Ancak bir hafta veya daha kısa sürede tamamlanması gerekir ve kullanıcıların profillerini yeniden yapılandırmalarını Outlook gerekir. Tam geçiş en çok 2.000 posta kutusuyla başa çıkabilir, ancak en çok 150 posta kutusunu geçirmek için bu posta kutusunu kullanmanızı kesinlikle öneririz. Daha fazla geçiş yapmaya çalışsanız, son tarihinize kadar tüm posta kutularını aktaracak zamannız olur ve IT destek personeliniz kullanıcıların son tarihlerini yeniden yapılandırmaya yardımcı olan isteklerle Outlook.
  
Yarı geçiş yapmayı düşünüyorsanız, şu gibi düşünün:
  
- Microsoft 365 TCP bağlantı noktası 443 üzerinden Exchange Her Yerde'i kullanarak Outlook 2007 sunucularınıza bağlanmanız gerekir.
    
- Tüm şirket içi posta kutuları diğer posta kutularına Microsoft 365.
    
- Kullanıcılarının posta kutularına okuma erişimi olan bir şirket içi yönetici hesabına ihtiyacınız vardır.
    
- Hizmet Exchange 2007'de kullanmak istediğiniz kabul edilen etki Microsoft 365 hizmette doğrulanmış etki alanı olarak ekleniyor olmalıdır.
    
- Geçişi başlatmanız ile tamamlama aşamasına başlamanız arasında, Microsoft 365 posta kutuları düzenli Microsoft 365 posta kutularını eşitler. Böylece, şirket içi posta kutularınızda e-postanın geride bırakılama endişesi olmadan geçişi tamamlarsınız.
    
- Kullanıcılar hesap hesapları için yeni geçici Microsoft 365 alır. Posta kutusunda ilk kez oturum a giriş yaptıklarında parolalarını değiştirmeleri gerekir.
    
- Geçişiniz olan her kullanıcı Microsoft 365 posta kutusu için Exchange Online bir lisansa ihtiyacınız var.
    
- Kullanıcıların cihazlarının her biri için yeni bir Outlook profili ayarlamaları ve e-postalarını yeniden indirmeleri gerekir. E-postanın indir Outlook e-posta miktarı değişiklik gösterebilir. Daha fazla bilgi için bkz [. Çevrimdışı tutmak için ne kadar postayı değiştirme](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Cutover geçişi hakkında daha fazla bilgi için bkz:
  
- [Tam e-posta geçişi hakkında bilmek istediğinizler](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [E-postanın tamam geçişini gerçekleştirme](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Aşamalı geçiş

Aşamalı geçişte, Microsoft 365'a geçirmek istediğiniz birkaç yüz veya birkaç bin posta kutunuz olabilir, geçişi tamamlamak için bir hafta veya daha uzun zaman gerekir ve paylaşılan Serbest/Meşgul takvim bilgileri gibi gelişmiş karma geçiş özelliklerinden hiçbirinde ihtiyacınız olmaz.
  
Aşamalı geçiş, posta kutularını başka bir posta kutusuna geçirmek için daha fazla zaman gereken ama yine de geçişi birkaç hafta içinde Microsoft 365 planlayan kuruluşlar için harika bir aşamadır. Posta kutularını toplu olarak geçirebilirsiniz. Bir defada kaç posta kutusunun geçir geçirilir olduğunu siz kontrol etmeksiniz. Örneğin, aynı departmanda yer alan kullanıcıların posta kutularını toplu hale batch olarak kullanabilirsiniz; örneğin, bunların aynı anda taşındığından emin olmak için. Ya da üst düzey posta kutularını son toplu işleme kadar  bırakın. Son geçişlerde olduğu gibi, kullanıcılarının kendi kullanıcı profillerini de Outlook gerekir.
  
Aşamalı geçiş yapmayı düşünüyorsanız, şu göz önünde bulunduracak şeyler vardır:
  
- Microsoft 365 TCP bağlantı noktası 443 üzerinden Exchange Her Yerde'i kullanarak Outlook 2007 sunucularınıza bağlanmanız gerekir.
    
- Kullanıcılarının posta kutularına okuma erişimi olan bir şirket içi yönetici hesabına ihtiyacınız vardır.
    
- Bu Exchange 2007 kabul edilen etki alanları Microsoft 365 hizmette doğrulanmış etki alanı olarak ekleniyor olmalıdır.
    
- Bir toplu işlemle geçirmeyi planladınız her posta kutusunun tam adını ve e-posta adresini içeren bir CSV dosyası oluşturmanız gerekir. Ayrıca, tamamlaysınız ve bu parolayı her kullanıcıya göndermek için, o posta kutusuna yeni bir parolayı da göndermeniz gerekir. Kullanıcıdan, yeni posta kutusunda ilk kez oturum a açması için parolayı değiştirmesi Microsoft 365 istenir.
    
- Geçiş toplu işlemini başlatmanız ile tamamlama aşamasına başlamanız arasında, Microsoft 365 toplu işleme dahil edilen Microsoft 365 şirket içi posta kutularını düzenli aralıklarla eşitler. Böylece, şirket içi posta kutularınızda e-postanın geride bırakılama endişesi olmadan geçişi tamamlarsınız.
    
- Geçişiniz olan her kullanıcı Microsoft 365 posta kutusu için Exchange Online bir lisansa ihtiyacınız var.
    
- Kullanıcıların cihazlarının her biri için yeni bir Outlook profili ayarlamaları ve e-postalarını yeniden indirmeleri gerekir. E-postanın indir Outlook e-posta miktarı değişiklik gösterebilir. Daha fazla bilgi için bkz [. Çevrimdışı tutmak için ne kadar postayı değiştirme](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Aşamalı geçiş hakkında daha fazla bilgi için bkz:
  
- [Aşamalı e-posta geçişi hakkında bilmek istediğinizler](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [E-postanın aşamalı geçişini gerçekleştirme](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Tam karma

Tam karma geçişte, kurumda birçok yüz veya on binlerce posta kutusu vardır ve siz de bunların bir veya hepsini bir yere taşımak Microsoft 365. Bu geçişler normalde uzun vadeli olduğundan, karma geçişler şunların mümkün olduğundan:
  
- Şirket içi kullanıcılara, şirket içi kullanıcıların serbest/meşgul takvim bilgilerini Microsoft 365 tersi de olabilir.
    
- Hem şirket içi hem de posta alıcılarını içeren birleşik bir genel adres Microsoft 365.
    
- İster Outlook ister başka bir kullanıcıda olsunlar, tüm kullanıcılar için tam kullanıcı alıcı Microsoft 365.
    
- TLS ve sertifikaları kullanarak, şirket içi Exchange ve sunucu Microsoft 365 güvenli e-posta iletişimi.
    
- Şirket içi iletiler arasında gönderilen Exchange ve şirket Microsoft 365 olarak davranarak şunların etkinleştirilmesini sağlar:
    
  - Dahili iletileri hedef alan aktarım ve uyumluluk aracıları tarafından düzgün değerlendiri ve işlenebilir.
    
  - İstenmeyen posta önleme filtrelerini atlar.
    
Tam karma geçiş, aylarca veya daha uzun süre karma bir yapılandırmada kalmayı beklediğiniz kuruluşlar için en iyisidir. Bu bölümün başlarında listelenen özellikleri, artı olarak dizin eşitlemeyi, daha iyi tümleşik uyumluluk özelliklerini ve çevrimiçi posta kutusu taşımalarını kullanarak posta kutularını Microsoft 365'a ve sunuculardan taşıma olanağını elde edersiniz. Microsoft 365, şirket içi kuruluşun bir uzantısı haline gelir.
  
Tam karma geçiş yapmayı düşünüyorsanız, şu iki şekilde göz önünde önündesiniz:
  
- Tam karma geçiş, tüm kuruluş türleri için uygun değildir. Tam karma geçişler karmaşıklığının karmaşık olması nedeniyle, birkaç yüzden az posta kutusu olan kuruluşlar normalde bu geçişi ayarlamak için gereken çabayı ve maliyeti haklı düşüren avantajları görmemektedir. Sizinki de buna benziyorsa, bunun yerine tam veya aşamalı geçişi göz önünde bulundurmanızı öneririz.
    
- Exchange 2007 kuruluşu içinde "karma sunucu" gibi davranacak en az bir Exchange 2013 sunucusunun dağıtımı gerekir. Bu sunucu, Microsoft 365 2007 sunucularınız adına Exchange iletişim kurar.
    
- Microsoft 365 TCP bağlantı noktası 443 üzerinden Her Yerde'i kullanarak "Outlook sunucusuna" bağlanması gerekir.
    
- Şirket içi Active Directory sunucularınız ile başka Azure Active Directory (Azure AD) Bağlan kullanarak dizin eşitlemesi Microsoft 365.
    
- Kullanıcılar, yerel ağda oturum Microsoft 365 aynı kullanıcı adı ve parolayı kullanarak kendi posta kutularında oturum ağına sahip olabilir. (Bu işlevsellik için, parola eşitlemesi Bağlan Azure AD hizmeti ve/veya Active Directory Federasyon Hizmetleri gerekir.)
    
- Geçişiniz olan her kullanıcı Microsoft 365 posta kutusu için Exchange Online bir lisansa ihtiyacınız var.
    
- Bazı eski Android telefonların yeni bir profile ihtiyacı Outlook, ancak kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmektedir. Kullanıcıların e-postalarını yeniden yüklemeleri gerek değildir.
    
Tam karma geçiş size uygun geliyorsa, geçiş işleminize yardımcı olacak aşağıdaki kaynaklara bakın:
  
- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
    
- [Exchange Server Karma Dağıtımları](/exchange/exchange-hybrid)
    
- [Karma Yapılandırma sihirbazı](/exchange/hybrid-configuration-wizard)
    
- [Karma Yapılandırma sihirbazı SSS](/exchange/hybrid-configuration-wizard-faqs)
    
- [Karma dağıtım önkoşulları](/exchange/hybrid-deployment-prerequisites)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Daha yeni bir sürüme Exchange Server

En iyi değeri ve kullanıcı deneyimini elde etmek için aşağıdakilere Microsoft 365. Ancak bazı kuruluşların e-postalarını şirket içinde tutmaları gerekmektedir. Bunun nedeni yasal düzenlemelere yönelik gereksinimler, verilerin başka bir ülkede bulunan veya benzer bir konumda bulunan bir veri merkezinde depo olmadığını garanti etmek olabilir. E-postanızı şirket içinde tutmayı seçerseniz, Exchange 2007 ortamınızı Exchange 2010, Exchange 2013 veya Exchange 2016'ya geçirebilirsiniz.
  
Microsoft 365'e Microsoft 365, Exchange 2016'ya geçirmenizi öneririz. Exchange 2016, 2016'nın önceki tüm Exchange. Bazı özellikler yalnızca Yakın Zamanda Microsoft 365'de mevcut olsa da, en yakın zamanda Microsoft 365. Yalnızca birkaç eksik şeyi kontrol edin:
  
|**Exchange sürümü**|**Özellikler**|
|:-----|:-----|
|Exchange 2010  <br/> | Role-Based Denetimi'ne tıklayın (ACL'ler olmadan izinler)  <br/>  Outlook Web App kutusu ilkelerini geri alın  <br/>  Serbest/meşgul bilgileri paylaşabilme ve kuruluşlar arasında takvim temsilciliği  <br/> |
|Exchange 2013  <br/> | *Exchange 2010 ve ...*  <br/>  Sunucu rollerinin sayısını üçe indiren basitleştirilmiş mimari (Posta Kutusu, İstemci Erişimi, Uç Aktarım)  <br/>  Hassas bilgilerin sızdır olmasını önlemeye yardımcı olan veri kaybı önleme ilkeleri (DLP)  <br/>  Geliştirilmiş Outlook Web App deneyimi  <br/> |
|Exchange 2016  <br/> | *Exchange 2013'den özellikler ve ...*  <br/>  Daha da basitleştirilmiş sunucu rolleri (yalnızca Posta Kutusu ve Uç Aktarım)  <br/>  DLP ile tümleştirme ve gelişmiş DLP SharePoint  <br/>  Geliştirilmiş veritabanı performansı  <br/>  Çevrimiçi belge işbirliği |
   
#### <a name="which-version-should-i-migrate-to"></a>Hangi sürüme geçiş olmalı?

Başlangıçta Exchange 2016'ya Exchange öneririz. Ardından, aşağıdaki bilgileri kullanarak varsayımını onaylayın veya 2016'Exchange eyi seçin. Exchange 2016'ya herhangi bir nedenle geçiş işleminiz yoksa, aynı işlemi Exchange 2013'te de yapar.
  
|**Dikkate Alınacak Nokta**|**Daha Fazla Bilgi**|
|:-----|:-----|
|Destek sonu tarihleri  <br/> | Exchange 2007'de olduğu gibi, Exchange her sürümün kendi destek sonu tarihi vardır:  <br/> *Exchange 2010* - Ocak 2020  <br/> *Exchange 2013* - Nisan 2023  <br/> *Exchange 2016* - Ekim 2025  <br/>  Desteğin sonu ne kadar erken olursa, o kadar erken bir zamanda başka bir geçiş gerçekleştirmeniz gerekir.<br/> |
|Exchange 2010 ve 2013'e geçiş yolu.  <br/> |İşte 2010 veya Exchange 2013'e Exchange aşamaları:  <br/> - 2010 Exchange 2013'ü mevcut 2007 Exchange yükleyin. <br/>- Hizmetleri ve diğer altyapıyı 2010 veya 2013 Exchange e taşıma.<br/>- Posta kutularını ve ortak klasörleri 2010 Exchange 2013'e taşıma.<br/>- 2007 sunucularının kalan Exchange alın. |
|Exchange 2016'ya geçiş yolu  <br/> |Exchange 2016'ya Exchange aşamaları:  <br/> - Exchange 2007 kuruluş Exchange 2013'ü yükleyin.<br/>- Hizmetleri ve diğer altyapıyı 2013'Exchange taşıma.<br/>- Posta kutularını ve ortak klasörleri 2013'Exchange taşıma.<br/>- 2007 sunucularının kalan Exchange alın.<br/>- Exchange 2013 kuruluşu olan Exchange 2016'ya yükleyin.<br/>- Posta kutularını, ortak klasörleri, hizmetleri ve diğer altyapıyı 2016'ya Exchange (sıra önemli değildir). 2013 sunucularında kalan Exchange alın.<br/><br/> **Not:** 2013'Exchange 2016'dan Exchange 2016'ya basit bir işlemdir. İki sürümün donanım gereksinimleri neredeyse aynı ve bu sürümler çok uyumludur. Böylece, Exchange 2013 için satın almış Exchange 2016'ya yükleyebilirsiniz. Çevrimiçi posta kutusu taşırken, çoğu kullanıcı posta kutusunun sunucudan taşındığını ve siz sunucuyu 2016'da yeniden Exchange fark etmez.           |
|Sürüm birlikte kullanılabilirlik  <br/> | ...  <br/> **Exchange 2016:** Exchange 2016, Exchange 2007 sunucusunun olduğu bir kuruluşta yük kurulamadı. önce Exchange 2010 veya 2013'e (kesinlikle Exchange 2013'ü öneririz), tüm Exchange 2007 sunucularını kaldırmanız ve ardından Exchange 2016'ya geçişniz gerekir.  <br/> **Exchange 2010 veya Exchange 2013:** Exchange 2010 veya Exchange 2013'ü mevcut Exchange 2007 kuruluşuna yükleyebilirsiniz. Bu, bir veya birden çok Exchange 2013 sunucusu yüklemenize ve geçiş işleminizi gerçekleştirmenize olanak sağlar.  <br/> |
|Sunucu donanımı  <br/> | Sunucu donanım gereksinimleri 2007'den Exchange değiştirildi. Donanımının uyumlu olduğundan emin olun. Ayrıntılar için bkz:  <br/> [Exchange 2016 Sistem Gereksinimleri](/Exchange/plan-and-deploy/system-requirements) <br/> [Exchange 2013 Sistem Gereksinimleri](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [Exchange 2010 Sistem Gereksinimleri](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/>  Yeni sunucularda, Exchange performansında yapılan önemli geliştirmelerin ve daha yeni sunucularda artırılmış bilgi işlem gücü ve depolama kapasitesi, aynı sayıda posta kutusunu desteklemek için büyük olasılıkla daha az sunucuya ihtiyacınız olduğu anlamına gelir.  <br/> |
|İşletim sistemi sürümü  <br/> | Her sürümde desteklenen en düşük işletim sistemi sürümleri:  <br/> **Exchange 2016** - Windows Server 2012  <br/> **Exchange 2013** - Windows Server 2008 R2 SP1  <br/> **Exchange 2010** - Windows Server 2008 SP2  <br/>  Destek Matrisi'nde, işletim sistemi [desteği Exchange daha fazla bilgi bulabilirsiniz](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Active Directory ormanı işlev düzeyi  <br/> | Her sürümde desteklenen en düşük Active Directory ormanı işlev düzeyleri:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange Server 2003 Windows 2010**  <br/>  En Düşük Destek Matrisi'nde orman işlev düzeyi [desteği Exchange daha fazla bilgi bulabilirsiniz](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Office istemci sürümleri  <br/> | Her sürümde desteklenen Office istemci sürümleri:  <br/> **Exchange 2016** - Office 2010 (en son güncelleştirmelerle)  <br/> **Exchange 2013** - Office 2007 SP3  <br/> **Exchange 2010** - Office 2003  <br/>  Destek Matrisi'Office destek hakkında daha [fazla Exchange bulabilirsiniz](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Nasıl geçiş yapabilirim?

E-postanızı şirket içinde tutmaya karar verdiysanız, geçiş işleminize yardımcı olmak için aşağıdaki kaynakları kullanın:
  
- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
    
- Exchange [2016, 2013](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2010](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help) için Active Directory şema [değişiklikleri](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010 için sistem gereksinimleri](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))
    
- Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010 için önkoşullar](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))
    
## <a name="get-help"></a>Yardım alın

Microsoft 365'e Microsoft 365, Microsoft FastTrack hizmetini kullanmaya uygun olabilirsiniz. FastTrack, geçiş işleminizi mümkün olduğunca sorunsuz hale Microsoft 365 yöntemleri, araçları ve kaynakları sağlar. En güzeli de, bir destek mühendisi planlama ve tasarımdan en son posta kutunuzu geçirmeye kadar geçiş işleminin adımlarını atacak. Daha fazla bilgi FastTrack bkz. [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Microsoft 365'a geçiş işleminiz sırasında sorunlar ile FastTrack veya Exchange Server'in daha yeni bir sürümüne geçiş işleminiz sırasında sorun ile karşınıza geliyorsa size yardımcı olabiliriz. Kullanabileceğiniz bazı kaynaklar:
  
- [Teknik topluluk](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [Müşteri desteği](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>İlgili konular

[Office 2007 sunucularınızı ve istemcilerinizi yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2007-servers-and-products.md)