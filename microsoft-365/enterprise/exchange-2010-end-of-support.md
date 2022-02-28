---
title: Exchange 2010 destek sonu yol haritası
ms.author: dstrome
author: dstrome
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 destek sonuna ulaştı. Şirket içi sürümüne veya daha yeni bir sürümüne Exchange Online için bu planlama yol haritasını Exchange Server kullanın.
ms.openlocfilehash: e49bf68ce2fb9b441ecd40ae4bb89ad88ea568c8
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990574"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 destek sonu yol haritası

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Exchange Server 2010, **13 Ekim 2020'de destek sonuna ulaştı**. Exchange 2010' dan Microsoft 365, Office 365 veya Exchange 2016'ya geçiş işlemini henüz başlatmadıysanız, şimdi planlamaya başlamanın tam zamanı.

## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. 13 Exchange 2010'da destek sonuna ulaştığı için, Microsoft artık şunları sağlar:

- Ortaya çıkabilir sorunlar için teknik destek.
- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.
- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.
- Saat dilimi güncelleştirmeleri.

Exchange 2010 kurulumunuz bu tarihten sonra çalışmaya devam edecektir. Ancak yukarıda listelenen değişikliklerden dolayı en kısa zamanda Exchange 2010'dan geçişnizi kesinlikle öneririz.

Destek sonuna yaklaşarak ilgili daha fazla bilgi için, Office [2010 sunucu ve istemcilerinden yükseltmeye yardımcı olacak kaynaklar'a bakın](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Seçeneklerim neler?

Şimdi seçeneklerinizi keşfetmek ve geçiş planınızı hazırlamak için çok uygun bir zaman. Şunları yapabilirsiniz:

- Geçişin tümüyle Microsoft 365. Tam, en düşük karma veya tam karma geçişi kullanarak posta kutularını geçirme. Ardından, şirket içi sunucularını Exchange Active Directory'i kaldırın.
- Exchange 2010 sunucularınızı şirket Exchange 2016'ya geçirme.

> [!IMPORTANT]
> Organizasyonunız posta kutularını Microsoft 365'a geçirmeyi seçer ama kullanıcı hesaplarını şirket içi Active Directory'den yönetmeye devam etmek için DirSync veya Azure AD Bağlan'yi yerinde tutmayı planlıyorsa, en az bir Microsoft Exchange sunucusunu şirket içinde tutmanız gerekir. Tüm Exchange sunucularını kaldırırsanız, yetkilinin kaynağı şirket içi Active Directory'sinde Exchange olduğu için Exchange Online alıcılarında değişiklik yapabilirsiniz. Burada değişikliklerin yapılmış olması gerekir. Bu senaryoda aşağıdaki seçenekleri kullanabilirsiniz:
>
>- *Önerilen:* Posta kutularınızı Microsoft 365'a geçirir ve sunucularınızı 13 Ekim 2020'ye kadar yükselttiysanız, Exchange 2010'a bağlanmak ve posta kutularını geçirmek için Microsoft 365'i kullanın. Ardından, Exchange 2010'Exchange 2016'ya geçişin ve 2010 Exchange kalan tüm sunucuların izinlerini alın.
>- Posta kutusu geçişini ve şirket içi sunucu yükseltmeyi 13 Ekim 2020'ye kadar tamamlamadısanız, şirket içi Exchange 2010 sunucularınızı önce Exchange 2016'ya yükseltin. Ardından, Exchange posta kutularına bağlanmak ve Microsoft 365 için Microsoft 365 2016'ya kullanın.

> [!NOTE]
> Bu biraz daha karmaşıktır, ancak aynı zamanda şirket içi Microsoft 365 2010 sunucularınızı Exchange 2016'ya geçirirken posta kutularını Exchange geçirebilirsiniz.

2010'da destek sonunun sona erersiniz ve Exchange Server.

![Exchange Server 2010 yükseltme yolları.](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Aşağıdaki bölümlerde her seçenek daha ayrıntılı olarak incelanmaktadır.

## <a name="migrate-to-microsoft-365"></a>Geçiş Microsoft 365

E-postanızı başka bir Microsoft 365, 2010 dağıtımınızı devre Exchange en iyi ve en basit seçenektir. Microsoft 365'a Microsoft 365, eski teknolojiden geçerli özelliklere tek sıçrama yapmak için şunları da kullanabilirsiniz:

- Bekletme İlkeleri, Yerinde In-Place Mahkeme Tutma, yerinde eKbulma ve daha fazlası gibi uyumluluk özellikleri.
- Microsoft Teams.
- Power BI.
- Odaklanmış Gelen Kutusu.
- MyAnalytics.

Microsoft 365 olarak yeni özellikler ve deneyimler edin de edinin, böylece organizasyonunız bunları hemen kullanmaya başlayabilir. Ayrıca, şu konuda endişelenmenize gerek yok:

- Donanımı satın alma ve koruma.
- Sunucularınızı ısıya ve soğutarak ödeme.
- Güvenlik, ürün ve saat dilimi düzeltmelerini güncel tutma.
- Uyumluluk gereksinimlerini desteklemek için depolamanın ve yazılımın bakımını yapmak.
- Yeni bir sürüme yükseltme Exchange. Microsoft 365'de her zaman Exchange en son Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Microsoft 365'e geçiş Microsoft 365?

Organizasyona bağlı olarak, belirli bir süre için birkaç Microsoft 365. İlk olarak, aşağıdakiler gibi birkaç şeye dikkat etmek gerekir:

- Taşımanız gereken kullanıcı veya posta kutusu sayısı.
- Geçişin ne kadar süreyle devam etmek istediğiniz.
- Şirket içi yükleme ile geçiş sırasında sorunsuz bir tümleştirmeye ihtiyacınız Microsoft 365 olabilir.

Bu tabloda geçiş seçenekleriniz ve hangi yöntemin kullanılamayacaklarını belirleyen en önemli faktörler yer alır.

<br>

****

|Geçiş seçeneği|Kuruluş boyutu|Süre|
|---|---|---|
|Tam geçiş|150'den az kullanıcı|Bir hafta veya daha kısa|
|En düşük karma geçiş|150'den az kullanıcı|Birkaç hafta veya daha kısa|
|Tam karma geçiş|150'den fazla koltuk|Birkaç hafta veya daha uzun|
|

Aşağıdaki bölümlerde, bu yöntemlere genel bir bakış yer almaktadır. Daha fazla bilgi için bkz [. Geçiş yolunu karar verme](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Tam geçiş

Kesin geçişte, tüm posta kutularınızı, dağıtım gruplarınızı, kişilerinizi, daha sonra Office 365 ve saat içinde geçirebilirsiniz. Bitirince, şirket içi sunucularınızı kapatır Exchange özel olarak Microsoft 365 kullanmaya başlarsanız.

Tam geçiş, çok fazla posta kutusu olan, Microsoft 365'a hızlıca gitmek isteyen ve diğer yöntemlerin karmaşıklığıyla uğraşmak istemeyen küçük kuruluşlar için harika bir yöntemdir. Ancak bir hafta veya daha kısa sürede tamamlanır. Ayrıca kullanıcıların profil profillerini yeniden yapılandırmalarını Outlook gerekir. Tam geçiş en çok 2.000 posta kutusu geçirebilirsiniz, ancak bunu en çok 150 posta kutusu için kullanmanızı öneririz. Daha fazla geçiş yapmaya çalışsanız, son tarihinize kadar tüm posta kutularını aktaracak zamannız olur ve IT destek personeliniz kullanıcıların son tarihlerini yeniden yapılandırmaya yardımcı olan isteklerle Outlook.

İşte, cutover geçişi hakkında dikkat gerekenler:

- Microsoft 365 TCP bağlantı noktası 443 üzerinden her yerde Outlook kullanarak Exchange 2010 sunucularınıza bağlanmanız gerekir.
- Tüm şirket içi posta kutuları diğer posta kutularına Microsoft 365.
- Kullanıcılarının posta kutularına okuma erişimi olan bir şirket içi yönetici hesabına ihtiyacınız vardır.
- Bu Exchange 2010 kabul edilen etki alanlarının Microsoft 365 hizmette doğrulanmış etki alanı olarak ekleniyor olması gerekir.
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
> Organizasyonunız posta kutularını Microsoft 365'e geçirmeyi seçer ama kullanıcı hesaplarını şirket içi Active Directory'den yönetmeye devam etmek için DirSync veya Azure AD Bağlan'i yerinde tutmayı planlıyorsa, en az bir Exchange sunucuyu şirket içinde tutmanız gerekir. Tüm Exchange sunucuları kaldırılırsa, bu sunucularda alıcı Exchange değişiklik Exchange Online. Çünkü yetkili kaynağı şirket içi Active Directory'nizin içinde kalır ve orada değişikliklerin olması gerekir.

Tam karma geçiş size uygun geliyorsa, aşağıdaki yararlı kaynaklara bakın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Exchange Server Karma Dağıtımları](/exchange/exchange-hybrid)
- [Karma Yapılandırma sihirbazı](/exchange/hybrid-configuration-wizard)
- [Karma Yapılandırma sihirbazı SSS](/exchange/hybrid-configuration-wizard-faqs)
- [Karma dağıtım önkoşulları](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Şirket içi sürümün daha Exchange Server sürümüne yükseltme

En iyi değeri ve kullanıcı deneyimini elde etmek için tümüyle Başka bir Microsoft 365. Ancak bazı kuruluşların bazı sunucularını şirket içinde tutmaları Exchange anlıyoruz. Bunun nedeni yasal düzenlemelerle ilgili gereksinimler, verilerin yabancı veri merkezinde depoil olmadığını garanti etme, bulutta karşılanalay benzersiz ayarlarınız veya gereksinimleriniz olması ya da bulut posta kutularını yönetmek için Exchange'e ihtiyacınız olması nedeniyle şirket içi Active Directory'ye ihtiyacınız olabilir. Her durumda, şirket içinde Exchange durumda olursanız, Exchange 2010 ortamının en az Exchange 2013 veya Exchange 2016'ya yükseltilir.

En iyi deneyimi yaşamak için, kalan şirket içi ortamınızı 2016'ya Exchange öneririz. Doğrudan Exchange Server 2010'dan Exchange Server 2016'ya gitmek için Exchange Server 2013'ü yüklemenize gerek yok.

Exchange 2016, 2016'nın önceki tüm Exchange. Bazı özellikler yalnızca Bu yeni Microsoft 365, ancak en yakın şekilde kullanılabilen deneyime Microsoft 365. Yalnızca birkaç eksik şeyi kontrol edin:

<br>

****

|Exchange sürümü|Özellikler|
|---|---|
|**Exchange 2013**|Basitleştirilmiş mimari sunucu rollerinin sayısını üçe indiriyor (Posta Kutusu, İstemci Erişimi, Uç Aktarım)|
||Hassas bilgilerin sızdır olmasını önlemeye yardımcı olan veri kaybı önleme ilkeleri (DLP)|
||Geliştirilmiş Outlook Web App deneyimi|
|**Exchange 2016**|*Exchange 2013'den özellikler ve ...*|
||Daha da basitleştirilmiş sunucu rolleri (yalnızca Posta Kutusu ve Uç Aktarım)|
||DLP ile tümleştirme ve gelişmiş DLP SharePoint|
||Geliştirilmiş veritabanı performansı|
||Çevrimiçi belge işbirliği|
|

<br>

****

|Dikkate Alınacak Nokta|Daha fazla bilgi|
|---|---|
|Destek sonu tarihleri|Exchange 2010'da olduğu gibi, Exchange her sürümün kendi destek sonu tarihi vardır: <p> Exchange 2013 - Nisan 2023 <p> Exchange 2016 - Ekim 2025 <p> Destek sonu tarihi ne kadar erken olursa, o kadar erken bir tarihte başka bir geçiş gerçekleştirmeniz gerekir. Nisan 2023, düşünmen gerekenden çok daha yakın!|
|Exchange 2013 veya 2016'ya geçiş yolu|Exchange 2010'dan daha yeni bir sürüme geçiş yolu, 2013 veya Exchange 2016'da Exchange aynıdır: <p> 2010 Exchange 2010'da mevcut Exchange 2016'ya yükleyin. <p> Hizmetleri ve diğer altyapıyı 2013 Exchange 2016'ya taşıma. <p> Posta kutularını ve ortak klasörleri 2013 Exchange 2016'ya taşıma 2010 sunucularında kalan Exchange alın.|
|Sürüm birlikte kullanılabilirlik|Exchange 2013 veya Exchange 2016'ya Exchange, var olan bir Exchange kuruluşa yükleyebilirsiniz. Bu, 2013 veya Exchange 2016 sunucularından birini Exchange başkalarını yüklemenize ve geçiş işleminizi yüklemenize olanak sağlar.|
|Sunucu donanımı|Sunucu donanım gereksinimleri 2010 Exchange değiştirildi. Donanımının uyumlu olduğundan emin olun. Her sürümün donanım gereksinimleri hakkında daha fazla bilgi edinebilirsiniz: <p> [Exchange 2016 sistem gereksinimleri](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <p> [Exchange 2013 sistem gereksinimleri](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <p> Yeni sunucularda performans Exchange ve artırılmış bilgi işlem gücü ve depolama kapasitesinde yapılan önemli geliştirmelerle, aynı sayıda posta kutusunu desteklemek için büyük olasılıkla daha az sunucuya ihtiyacınız olacak.|
|İşletim sistemi sürümü|Her sürümde desteklenen en düşük işletim sistemi sürümleri: <p> Exchange 2016 - Windows Server 2012 <p> Exchange 2013 - Windows Server 2008 R2 SP1 <p> Destek Matrisi'nde, işletim sistemi desteği [hakkında daha Exchange bulabilirsiniz](/exchange/plan-and-deploy/supportability-matrix).|
|Active Directory ormanı işlev düzeyi|Her sürümde desteklenen en düşük Active Directory ormanı işlev düzeyleri: <p> Exchange 2016 - Windows Server 2008 R2 SP1 <p> Exchange 2013 - Windows Server 2003 <p> Daha fazla bilgiyi, En Düşük Destek Matrisi'nde [Exchange bulabilirsiniz](/exchange/plan-and-deploy/supportability-matrix).|
|Office istemci sürümleri|Her sürümde desteklenen Office istemci sürümleri: <p> Exchange 2016 - Office 2010 (en son güncelleştirmelerle) <p> Exchange 2013 - Office 2007 SP3 <p> Destek Matrisi'Office destek hakkında daha [fazla Exchange bulabilirsiniz](/exchange/plan-and-deploy/supportability-matrix).|
|

Geçiş işleminize yardımcı olmak için aşağıdaki kaynakları kullanın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help) için Active Directory şema değişiklikleri
- Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013 için sistem gereksinimleri](/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- [Exchange 2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013 için önkoşullar](/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 istemci ve sunucuları ile 7. Windows özeti

Office 2010 istemcileri ve sunucuları ve Windows 7 için yükseltme, geçirme ve buluta taşıma seçeneklerinin görsel bir özeti için destek [posteri](../downloads/Office2010Windows7EndOfSupport.pdf) sonuna bakın.

[![Office 2010 istemcileri ve sunucuları ve Posta 7 posteri için Windows sonu.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Bu tek sayfalı posterde, Office 2010 istemci ve sunucu ürünlerine ve Windows 7 destek sonuna ulaşarak, 2010'da tercih edilen yollar ve seçenek desteği vurgulanmış olarak yanıt vermek için Microsoft 365 Kurumsal yol göstermektedir.

Ayrıca bu [posteri](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) indirip letter, legal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

## <a name="what-if-i-need-help"></a>Yardım gerekirse ne olur?

Microsoft 365'e Microsoft 365, Microsoft FastTrack hizmetini kullanmaya uygun olabilirsiniz. FastTrack, geçiş işleminizi mümkün olduğunca sorunsuz hale Microsoft 365 yöntemleri, araçları ve kaynakları sağlar. En güzeli de, planlama ve tasarımdan son posta kutunuzu en geçe kadar size yol eden bir destek mühendisiniz olur. Daha fazla bilgi FastTrack bkz. [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Microsoft 365'a geçiş işleminiz sırasında sorunlar ile FastTrack kullanıyorsanız veya Exchange Server'in daha yeni bir sürümüne geçiş ediyorsanız, şu kaynakları kullanabilirsiniz:

- [Teknik topluluk](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Müşteri desteği](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>İlgili makaleler

[Office 2010 sunucularından ve istemcilerinden yükseltmeye yardımcı olan kaynaklar](upgrade-from-office-2010-servers-and-products.md)
