---
title: Exchange 2013 destek sonu yol haritası
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2013 desteği Nisan 2023'te sonuna gelecek. Şirket içi sürümüne veya sonraki bir Exchange Online yükseltmeye hazırlanmak için bu Exchange Server yol haritasını kullanın.
ms.openlocfilehash: 2b949c113be16db97d68d92f2f1529245c287e48
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010013"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange 2013 destek sonu yol haritası

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Exchange Server 2013 destek sonuna **11 Nisan 2023'te ulaştı**. Exchange 2013'den Microsoft 365, Office 365 veya Exchange 2019'a geçiş işlemini henüz başlatmadıysanız, şimdi planlamaya başlamanın tam zamanı.

## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. 11 Exchange 2013 destek sonuna ulaştığından, 11 Nisan 2023'te Microsoft artık şunları sağlar:

- Ortaya çıkabilir sorunlar için teknik destek.
- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.
- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.
- Saat dilimi güncelleştirmeleri.

Exchange 2013 yüklemeniz bu tarihten sonra da çalışmaya devam edecektir. Ancak yukarıda listelenen değişikliklerden dolayı en kısa zamanda Exchange 2013'den Exchange 2019'a geçişnizi kesinlikle öneririz.


## <a name="what-are-my-options"></a>Seçeneklerim neler?

Şimdi seçeneklerinizi keşfetmek ve geçiş planınızı hazırlamak için çok uygun bir zaman. Şunları yapabilirsiniz:

- Geçiş için Microsoft 365. Tam, en düşük karma veya tam karma geçişi kullanarak posta kutularını, ortak klasörleri ve diğer verileri geçirme. Ardından, şirket içi dizin sunucularını Exchange Active Directory'i kaldırın.
- 2013'Exchange yükseltin. Şirket içi Exchange için Exchange 2019'a taşıma.

> [!IMPORTANT]
> Organizasyonunız posta kutularını Microsoft 365'e geçirmeyi seçer ama kullanıcı hesaplarını Active Directory'de yönetmek için Azure AD Bağlan'i kullanmaya devam etmek planlıyorsa, en az bir Microsoft Exchange sunucuyu şirket içinde tutmanız gerekir. Tüm Exchange sunucularını kaldırırsanız, yetkili kaynağınız şirket içi Active Directory'niz olduğundan Exchange alıcılarında Exchange Online alıcılarda değişiklik yapabilirsiniz. Bu senaryoda aşağıdaki seçenekleri kullanabilirsiniz:
>
>- *Önerilen:* Posta kutularınızı posta kutularınıza Microsoft 365 ve ortamınızı 11 Nisan 2023 Exchange 2019'a yükseltin. Posta kutularına Exchange ve geçirmek için Microsoft 365 2013'ü kullanın. Ardından, Exchange 2013'Exchange 2019'a yükseltin ve 2013'te çalışan sunucuların Exchange alın.
>- Exchange Online'e geçişi tamamlayasanız ve şirket içi sunucularınızı 11 Nisan 2023'e kadar yükseltin, önce Exchange 2013'ten Exchange 2019'a yükseltin ve ardından posta kutularını Exchange 2019'a geçirmek için Microsoft 365.

2013'te destek sonunu önlemek için Exchange Server:

## <a name="migrate-to-microsoft-365"></a>Geçiş Microsoft 365

Microsoft 365'a Microsoft 365, Exchange 2013 dağıtımınızı devre Exchange en iyi ve en basit seçenektir. Microsoft 365'a Microsoft 365, eski teknolojiden geçerli özelliklere tek sıçrama yapmak için şunları da kullanabilirsiniz:

- Daha yüksek veri kullanılabilirlik ile daha büyük posta kutuları;
- İstenmeyen posta önleme ve kötü amaçlı yazılımlardan koruma gibi güvenlik özellikleri, 
- Veri Kaybını Önleme, Bekletme İlkeleri, In-Place Yerinde eBulma ve Mahkeme Tutma gibi uyumluluk özellikleri;
- SharePoint Online, OneDrive, Teams, Power BI ve diğer Microsoft 365 hizmetleriyle tümleştirme;
- Odaklanmış Gelen Kutusu; ve
- Gelişmiş çözümleme ve Viva Analizler.

Microsoft 365 olarak yeni özellikler ve deneyimler edin de edinin, böylece organizasyonunız bunları hemen kullanmaya başlayabilir. Ayrıca, şu konuda endişelenmenize gerek yok:

- Donanımı satın alma ve koruma;
- Sunucularınızı çalıştırmak ve soğut etmek için ödeme yapmak;
- Sunucuları güvenlik, ürün ve saat dilimi düzeltmelerini güncel tutma;
- Uyumluluk gereksinimlerini desteklemek için sunucu depolama ve yazılımın bakımını yapmak; veya
- Exchange'un yeni sürümüne yükseltme; her zaman en son sürümde ve en son Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Microsoft 365'e geçiş Microsoft 365?

Organizasyona bağlı olarak, belirli bir süre için birkaç Microsoft 365. İlk olarak, aşağıdakiler gibi birkaç şeye dikkat etmek gerekir:

- Taşımanız gereken posta kutusu sayısı;
- Geçişin ne kadar süreyle devam etmek istediğiniz; ve
- Şirket içi ortamınız ve şirket içi ortamınız arasında sorunsuz bir tümleştirmeye gerek Microsoft 365 geçiş sırasında sorunsuz bir tümleştirmeye ihtiyacınız olabilir.

Bu tabloda geçiş seçenekleriniz ve hangi yöntemin kullanılamayacaklarını belirleyen en önemli faktörler yer alır.

<br>

****

|Geçiş seçeneği|Kuruluş boyutu|Süre|
|---|---|---|
|Tam geçiş|150'den az posta kutusu|Bir hafta veya daha kısa|
|En düşük karma geçiş|150'den az posta kutusu|Birkaç hafta veya daha kısa|
|Tam karma geçiş|150'den fazla posta kutusu|Birkaç hafta veya daha uzun|
|

Aşağıdaki bölümlerde, bu yöntemlere genel bir bakış yer almaktadır. Daha fazla bilgi için bkz [. Geçiş yolunu karar verme](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Tam geçiş

Kesin geçişte, tüm posta kutularınızı, dağıtım gruplarınızı, kişilerinizi, daha sonra Office 365 ve saat içinde geçirebilirsiniz. Bitirince, şirket içi sunucularınızı kapatır Exchange özel olarak Microsoft 365 kullanmaya başlarsanız.

Tam geçiş, çok fazla posta kutusu olan, Microsoft 365'a hızlıca gitmek isteyen ve diğer yöntemlerin karmaşıklığıyla uğraşmak istemeyen küçük kuruluşlar için harika bir yöntemdir. Ancak bir hafta veya daha kısa sürede tamamlanır. Ayrıca kullanıcıların profil profillerini yeniden yapılandırmalarını Outlook gerekir. Tam geçiş en çok 2.000 posta kutusu geçirebilirsiniz, ancak bunu en çok 150 posta kutusu için kullanmanızı öneririz. Daha fazla geçiş yapmaya çalışsanız, son tarihinize kadar tüm posta kutularını aktaracak zamannız olur ve IT destek personeliniz kullanıcıların son tarihlerini yeniden yapılandırmaya yardımcı olan isteklerle Outlook.

İşte, cutover geçişi hakkında dikkat gerekenler:

- Microsoft 365 TCP bağlantı noktası 443 üzerinden Outlook Yerde'yi kullanarak Exchange 2013 sunucularınıza bağlanmanız gerekir.
- Tüm şirket içi posta kutuları diğer posta kutularına Microsoft 365.
- Kullanıcılarının posta kutularına okuma erişimi olan bir şirket içi yönetici hesabına ihtiyacınız vardır.
- Bu Exchange 2013 tarafından kabul edilen etki alanlarının Microsoft 365 doğrulanmış etki alanları olarak hizmette ekleniyor olması gerekir.
- Geçişi başlatmanız ve tamamlama aşamasına başlamanız arasında, Microsoft 365 posta kutuları düzenli Microsoft 365 posta kutularını eşitler. Böylece, şirket içi posta kutularınızda e-postanın geride bırakılama endişesi olmadan geçişi tamamlarsınız.
- Kullanıcılar hesap hesapları için yeni geçici Microsoft 365 alır. Posta kutularına ilk kez giriş yaptıklarında bu değiştirmeleri gerekir.
- Geçişiniz olan her kullanıcı Microsoft 365 posta kutusu için Exchange Online bir lisansa ihtiyacınız var.
- Kullanıcıların cihazlarının her biri için yeni bir Outlook profili ayarlamaları ve e-postalarını yeniden indirmeleri gerekir. E-postanın indir Outlook e-posta miktarı değişiklik gösterebilir. Daha fazla bilgi için bkz[. Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Tamamla geçiş hakkında daha fazla bilgi edinmek için bkz:

- [Tam e-posta geçişi hakkında bilmek istediğinizler](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [E-postanın diğer adreslere geçişini Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>En düşük karma geçiş

Çok düşük bir karma veya hızlı geçişte, birkaç yüz posta kutusunu birkaç Microsoft 365 içinde başka posta kutularına taşıyoruz. Bu yöntem, paylaşılan serbest/meşgul takvim bilgileri gibi gelişmiş karma geçiş özelliklerini desteklemez.

Düşük karma geçiş, Microsoft 365 posta kutularını başka bir posta kutusuna geçirmek için daha fazla zaman gereken ama yine de geçişi birkaç hafta içinde tamamlamayı planlayan kuruluşlar için harika bir araçtır. Karmaşıklık düzeyi çok fazla olmadan daha gelişmiş *tam karma geçişin* avantajlarından faydalanın. Bir defada kaç posta kutusunun geçirilir olduğunu siz kontrolebilirsiniz. Microsoft 365 posta kutuları, şirket içi hesapların kullanıcı adları ve parolaları ile oluşturulur. Ayrıca, tam geçişlerin aksine kullanıcılarınız kendi kullanıcı profillerini yeniden Outlook yok.

En düşük karma geçiş hakkında dikkat gerekenler:

- Şirket içi Active Directory sunucularınız ve şirket içi Active Directory sunucularınız arasında tek seferlik dizin eşitlemesi Microsoft 365.
- Kullanıcılar, posta kutularıyla aynı kullanıcı adı Microsoft 365 parolayla kendi posta kutularında oturum aabilecektir.
- Geçişiniz için, Microsoft 365 posta kutuları için Exchange Online bir lisansa ihtiyacınız olur.
- Bazı eski Android telefonların yeni bir profile ihtiyacı Outlook, ancak kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmektedir. Kullanıcıların e-postalarını yeniden yüklemeleri gerek değildir.

Daha fazla bilgi için bkz[. Posta kutularınızı hızlı bir Exchange için En Düşük Karma'Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Tam karma

Tam karma geçişte, birçok yüz veya on binlerce posta kutunuz olur ve posta kutularının bir çoğunu veya tamamını başka bir Microsoft 365. Bu geçişler normalde uzun vadeli olduğundan, karma geçişler şunların mümkün olduğundan:

- Şirket içi kullanıcılara, şirket içi kullanıcıların serbest/meşgul takvim bilgilerini Microsoft 365 tersi de olabilir.
- Hem şirket içi hem de posta alıcılarını içeren birleşik bir genel adres Microsoft 365.
- İster Outlook ister başka bir kullanıcıda olsunlar, tüm kullanıcılar için tam kullanıcı alıcı Microsoft 365.
- TLS ve sertifikaları kullanarak, şirket içi Exchange ve sunucu Office 365 güvenli e-posta iletişimi.
- Şirket içi iletiler arasında gönderilen Exchange ve şirket Microsoft 365 olarak davranarak şunların etkinleştirilmesini sağlar:
  - Dahili iletileri hedef alan aktarım ve uyumluluk aracıları tarafından düzgün değerlendiri ve işlenebilir.
  - İstenmeyen posta önleme filtrelerini atlar.

Tam karma geçişler, aylarca veya daha uzun süre karma bir yapılandırmada kalmayı beklediğiniz kuruluşlar için en iyisidir. Bu bölümün başlarında listelenen özellikleri, artı olarak dizin eşitlemeyi, daha iyi tümleşik uyumluluk özelliklerini ve çevrimiçi posta kutusu taşımalarını kullanarak posta kutularını gelen kutusuna Microsoft 365 ve taşıma olanağını elde edersiniz. Microsoft 365, şirket içi kuruluşun bir uzantısı haline gelir.

Tam karma geçiş hakkında dikkat gerekenler:

- Tüm kuruluşlar için uygun değil. Tam karma geçişler karmaşıklığının karmaşık olması nedeniyle, birkaç yüzden az posta kutusu olan kuruluşlar normalde bu çabayı ve maliyeti haklı düşüren avantajları görmemektedir. Böyle durumlarda, bunun yerine tam veya en düşük karma geçişi göz önünde bulundurmanizi öneririz.
- Şirket içi Active Directory sunucularınız ile Azure Active Directory Dizin sunucularınız arasında Bağlan Eşitleme (Azure AD) Microsoft 365.
- Kullanıcılar, yerel Microsoft 365 aynı kullanıcı adı ve parolayla kendi kullanıcı adı ve parolalarıyla kendi posta kutularında oturum aabilecektir. (Bu işlevsellik için, parola eşitlemesi Bağlan Azure AD hizmeti ve/veya Active Directory Federasyon Hizmetleri gerekir).
- Geçişte, Microsoft 365 posta kutuları için Exchange Online bir lisansa ihtiyacınız var.
- Bazı eski Android telefonların yeni bir profile ihtiyacı Outlook, ancak kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmektedir. Kullanıcıların e-postalarını yeniden yüklemeleri gerek değildir.

> [!IMPORTANT]
> Organizasyonunız posta kutularını Microsoft 365'e geçirmeyi seçer ama kullanıcı hesaplarını Active Directory'de yönetmek için Azure AD Bağlan'i tutmayı planlıyorsa, en az bir Exchange sunucuyu şirket içinde tutmanız gerekir. Tüm Exchange sunucusu kaldırılırsa, alıcı adı ve alıcılarda Exchange. Bunun nedeni, yetkili kaynağın Active Directory olması ve burada değişikliklerin yapmak zorunda olmasıdır.

Tam karma geçiş size uygun geliyorsa, aşağıdaki yararlı kaynaklara bakın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Exchange Server Karma Dağıtımları](/exchange/exchange-hybrid)
- [Karma Yapılandırma sihirbazı](/exchange/hybrid-configuration-wizard)
- [Karma Yapılandırma sihirbazı SSS](/exchange/hybrid-configuration-wizard-faqs)
- [Karma dağıtım önkoşulları](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Şirket içi sürümün daha Exchange Server sürümüne yükseltme

En iyi değeri ve kullanıcı deneyimini elde etmek için tümüyle Başka bir Microsoft 365. Ancak bazı kuruluşların, bazı çalışan ve sunucularını şirket Exchange tutmak zorunda olduğunu anlıyoruz. Bunun nedeni yasal düzenlemelerle ilgili gereksinimler, verilerin yabancı veri merkezinde depoil olmadığını garanti etme, bulutta karşılanalay benzersiz ayarlarınız veya gereksinimleriniz olması ya da bulut posta kutularını yönetmek için Exchange'e ihtiyacınız olması nedeniyle şirket içi Active Directory'ye ihtiyacınız olabilir. Her durumda, şirket içinde Exchange devam edersanız, Exchange 2013 ortamının yükseltilir.

En iyi deneyimi yaşamak için, kalan şirket içi ortamınızı 2019'a Exchange öneririz. Exchange Server 2013'ü doğrudan Exchange Server 2019'a kadar yükleyesiniz, çünkü Exchange Server yüklemenize gerek yok. Exchange özellikler yalnızca Microsoft 365'de mevcut olsa da, Microsoft 365 2019'daki deneyime Microsoft 365.



****
Aşağıda, 2013'e yükseltme hakkında Exchange önemli şeyler bulabilirsiniz:

|Öğe|Daha fazla bilgi|
|---|---|
|Destek sonu tarihleri|Exchange 2013'te olduğu gibi, Exchange her sürümün kendi destek sonu tarihi vardır: <p> Exchange 2013 - Nisan 2023 <p> Nisan 2023, düşünmen gerekenden çok daha yakın!|
|Exchange 2019'a geçiş yolu|Exchange 2013'den daha yeni bir sürüme geçiş yolu basit: <p> 2013 Exchange 2013'ü var olan Exchange 2019'a yükleyin. <p> Hizmetleri ve verileri Exchange 2013'Exchange 2019'a taşıma ve 2013 sunucularının Exchange alın.|
|Sunucu donanımı|Sunucu donanım gereksinimleri 2013 Exchange değiştirildi. Donanımının uyumlu olduğundan emin olun. Donanım gereksinimleri hakkında daha fazla bilgi için buraya tıklayın: <p> [Exchange 2019 sistem gereksinimleri](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Yeni sunucularda performans Exchange ve artırılmış bilgi işlem gücü ve depolama kapasitesinde yapılan önemli geliştirmelerle, aynı sayıda posta kutusunu desteklemek için büyük olasılıkla daha az sunucuya ihtiyacınız olacak.|
|İşletim sistemi sürümü|Exchange 2019 için desteklenen en düşük işletim sistemi sürümü, Server 2019 Windows sürümüdür. Windows Server 2022 desteği yakında geliyor <p> Destek Matrisi'nde, işletim sistemi desteği [hakkında daha Exchange bulabilirsiniz](/exchange/plan-and-deploy/supportability-matrix).|
|Active Directory ormanı işlev düzeyi|Desteklenen en düşük Active Directory ormanı işlev düzeyi R2 Windows Server 2012 tir. Daha fazla bilgiyi, En Düşük Destek Matrisi'nde [Exchange bulabilirsiniz](/exchange/plan-and-deploy/supportability-matrix).|
|Office istemci sürümleri|Desteklenen matriste Office en düşük sürüm de Exchange [belgelenmiş olabilir](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients).|
|

Geçiş işleminize yardımcı olmak için aşağıdaki kaynakları kullanın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Exchange 2019](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019) için Active Directory şema değişiklikleri
- [Exchange 2019 için sistem gereksinimleri](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019)


## <a name="what-if-i-need-help"></a>Yardım gerekirse ne olur?

Microsoft 365'e Microsoft 365, Microsoft FastTrack hizmetini kullanmaya uygun olabilirsiniz. FastTrack, geçiş işleminizi mümkün olduğunca sorunsuz hale Microsoft 365 yöntemleri, araçları ve kaynakları sağlar. En güzeli de, planlama ve tasarımdan son posta kutunuzu en geçe kadar size yol eden bir destek mühendisiniz olur. Daha fazla bilgi FastTrack bkz. [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Microsoft 365'a geçiş işleminiz sırasında sorunlar ile FastTrack kullanıyorsanız veya Exchange Server'in daha yeni bir sürümüne geçiş ediyorsanız, şu kaynakları kullanabilirsiniz:

- [Teknik topluluk](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Müşteri desteği](https://support.microsoft.com/gp/support-options-for-business)


