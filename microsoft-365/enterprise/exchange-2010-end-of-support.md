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
description: Exchange 2010 destek sonuna ulaşmıştır. Şirket içi Exchange Server Exchange Online veya daha yeni bir sürümüne yükseltmeye hazırlanmak için bu planlama yol haritasını kullanın.
ms.openlocfilehash: 24834a600a14c46287434f8f273fcd139d117376
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822782"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 destek sonu yol haritası

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Exchange Server 2010 **, 13 Ekim 2020** tarihinde destek sonuna ulaşmıştır. Exchange 2010'dan Microsoft 365, Office 365 veya Exchange 2016'ya geçişe henüz başlamadıysanız, şimdi planlamaya başlamanın tam zamanı.

## <a name="what-does-end-of-support-mean"></a>*Destek sonu* ne anlama gelir?

Microsoft ürünlerinin çoğu, yeni özellikler, hata düzeltmeleri, güvenlik düzeltmeleri vb. edindikleri bir destek yaşam döngüsüne sahiptir. Bu yaşam döngüsü genellikle ürünün ilk sürümünden itibaren 10 yıl sürer. Bu yaşam döngüsünün sonu, ürünün destek sonu olarak bilinir. Exchange 2010, 13 Ekim 2020'de destek sonuna ulaştığından, Microsoft artık şunları sağlamamaktadır:

- Oluşabilecek sorunlar için teknik destek.
- Sunucunun kararlılığını ve kullanılabilirliğini etkileyebilecek sorunlar için hata düzeltmeleri.
- Sunucuyu güvenlik ihlallerine açık hale getirebilecek güvenlik açıklarına yönelik güvenlik düzeltmeleri.
- Saat dilimi güncelleştirmeleri.

Exchange 2010 kurulumunuz bu tarihten sonra çalışmaya devam edecektir. Ancak yukarıda listelenen değişiklikler nedeniyle, Exchange 2010'dan en kısa sürede geçmenizi kesinlikle öneririz.

Destek sonuna yaklaşma hakkında daha fazla bilgi için bkz. [Office 2010 sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Seçeneklerim nelerdir?

Seçeneklerinizi keşfetmek ve bir geçiş planı hazırlamak için harika bir zaman. Şunları yapabilirsiniz:

- Tamamen Microsoft 365 geçiş. Tam geçiş, en düşük karma veya tam karma geçişi kullanarak posta kutularını geçirin. Ardından şirket içi Exchange sunucularını ve Active Directory'yi kaldırın.
- Exchange 2010 sunucularınızı şirket içi sunucularınızda Exchange 2016'ya geçirin.

> [!IMPORTANT]
> Kuruluşunuz posta kutularını Microsoft 365 geçirmeyi seçerse ancak kullanıcı hesaplarını şirket içi Active Directory yönetmeye devam etmek için DirSync veya Azure AD Bağlan yerinde tutmayı planlıyorsa, en az bir Microsoft Exchange sunucusunu şirket içinde tutmanız gerekir. Tüm Exchange sunucuları kaldırırsanız, yetki kaynağı şirket içi Active Directory kaldığından Exchange Online'daki Exchange alıcılarda değişiklik yapamazsınız. Orada değişiklikler yapılması gerekir. Bu senaryoda, aşağıdaki seçeneklere sahipsiniz:
>
> - *Önerilen:* Posta kutularınızı Microsoft 365'ye geçirdiyseniz ve sunucularınızı 13 Ekim 2020'ye kadar yükselttiyseniz, Microsoft 365 bağlanmak ve posta kutularını geçirmek için Exchange 2010'u kullanın. Ardından, Exchange 2010'Exchange 2016'ya geçirin ve kalan Exchange 2010 sunucularının yetkisini alın.
> - Posta kutusu geçişini ve şirket içi sunucu yükseltmesini 13 Ekim 2020'ye kadar tamamlamadıysanız, önce şirket içi Exchange 2010 sunucularınızı Exchange 2016'ya yükseltin. Ardından Microsoft 365 bağlanmak ve posta kutularını geçirmek için Exchange 2016'yı kullanın.

> [!NOTE]
> Bu biraz daha karmaşık olsa da, şirket içi Exchange 2010 sunucularınızı Exchange 2016'ya geçirirken posta kutularını Microsoft 365 geçirebilirsiniz.

Exchange Server 2010 desteğinin sona ermesini önlemek için izleyebileceğiniz üç yol aşağıdadır.

![Exchange Server 2010 yükseltme yolları.](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Aşağıdaki bölümlerde her bir seçenek daha ayrıntılı olarak incelanmıştır.

## <a name="migrate-to-microsoft-365"></a>Microsoft 365'e geçiş

E-postanızı Microsoft 365'a geçirmek, Exchange 2010 dağıtımınızı devre dışı bırakmanıza yardımcı olacak en iyi ve en basit seçenektir. Microsoft 365 geçişle, eski teknolojiden geçerli özelliklere şu özellikler gibi tek bir atlama yapabilirsiniz:

- Bekletme İlkeleri, In-Place ve Dava Tutma, yerinde eBulma ve daha fazlası gibi uyumluluk özellikleri.
- Microsoft Teams.
- Power BI.
- Odaklanmış Gelen Kutusu.
- MyAnalytics.

Microsoft 365 ayrıca yeni özellikleri ve deneyimleri de ilk olarak alır, böylece kuruluşunuz bunları hemen kullanmaya başlayabilir. Ayrıca, şu konularda endişelenmeniz gerekmez:

- Donanım satın alma ve bakım.
- Sunucularınızı ısıtmak ve soğutmak için ödeme.
- Güvenlik, ürün ve saat dilimi düzeltmeleri hakkında güncel kalma.
- Uyumluluk gereksinimlerini desteklemek için depolama ve yazılımları koruma.
- Exchange yeni bir sürümüne yükseltme. Microsoft 365'da her zaman en son Exchange sürümündesiniz.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Microsoft 365'a nasıl geçiş yapmalıyım?

Kuruluşunuza bağlı olarak, Microsoft 365 ulaşmak için birkaç seçeneğiniz vardır. İlk olarak, aşağıdakiler gibi birkaç şeyi göz önünde bulundurmanız gerekir:

- Taşımanız gereken koltuk veya posta kutularının sayısı.
- Geçişin ne kadar sürmesini istediğiniz.
- Geçiş sırasında şirket içi yüklemenizle Microsoft 365 arasında sorunsuz bir tümleştirmeye ihtiyacınız olup olmadığı.

Bu tablo, geçiş seçeneklerinizi ve hangi yöntemin kullanılacağını belirleyen en önemli faktörleri gösterir.

|Geçiş seçeneği|Kuruluş boyutu|Süre|
|---|---|---|
|Tam geçiş|150'den az koltuk|Bir hafta veya daha az|
|Minimum karma geçiş|150'den az koltuk|Birkaç hafta veya daha az|
|Tam karma geçiş|150'den fazla koltuk|Birkaç hafta veya daha fazla|

Aşağıdaki bölümlerde bu yöntemlere genel bir bakış sunun. Daha fazla bilgi için bkz. [Geçiş yoluna karar verme](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Tam geçiş

Tam geçişte, tüm posta kutularınızı, dağıtım gruplarınızı, kişilerinizi vb. belirli bir tarih ve saatte Office 365 geçirirsiniz. İşiniz bittiğinde şirket içi Exchange sunucularınızı kapatır ve yalnızca Microsoft 365 kullanmaya başlarsınız.

Tam geçiş, çok fazla posta kutusu olmayan, hızlı bir şekilde Microsoft 365 almak isteyen ve diğer yöntemlerin karmaşıklığıyla ilgilenmek istemeyen küçük kuruluşlar için harikadır. Ancak bir hafta veya daha kısa bir süre içinde tamamlanmalıdır. Ayrıca kullanıcıların Outlook profillerini yeniden yapılandırması gerekir. Tam geçiş 2.000 posta kutusuna kadar geçiş yapabilir, ancak en fazla 150 posta kutusu için kullanmanızı öneririz. Daha fazla geçiş yapmaya çalışırsanız, son tarihinizden önce tüm posta kutularını aktarmak için zamanınız tükenebilir ve BT destek personeliniz kullanıcıların Outlook yeniden yapılandırmasına yardımcı olmak için yapılan isteklerle bunalabilir.

Tam geçişle ilgili dikkat edilmesi gerekenler şunlardır:

- Microsoft 365 443 numaralı TCP bağlantı noktası üzerinden Outlook Anywhere kullanarak Exchange 2010 sunucularınıza bağlanması gerekir.
- Tüm şirket içi posta kutuları Microsoft 365 taşınacaktır.
- Kullanıcılarınızın posta kutularına okuma erişimi olan bir şirket içi yönetici hesabınız olmalıdır.
- Microsoft 365 kullanmak istediğiniz Exchange 2010 kabul edilen etki alanlarının hizmete doğrulanmış etki alanları olarak eklenmesi gerekir.
- Geçişi başlattığınızda ve tamamlama aşamasına başladığınızda Microsoft 365 Microsoft 365 ve şirket içi posta kutularını düzenli aralıklarla eşitler. Bu, şirket içi posta kutularınızda e-postanın geride bırakılması konusunda endişelenmeden geçişi tamamlamanıza olanak tanır.
- Kullanıcılar Microsoft 365 hesapları için yeni geçici parolalar alır. Posta kutularında ilk kez oturum açtıklarında bunları değiştirmeleri gerekir.
- Geçiş yaptığınız her kullanıcı posta kutusu için Exchange Online içeren bir Microsoft 365 lisansına ihtiyacınız vardır.
- Kullanıcıların cihazlarının her birinde yeni bir Outlook profili ayarlamaları ve e-postalarını yeniden indirmeleri gerekir. Outlook indireceği e-posta miktarı farklılık gösterebilir. Daha fazla bilgi için bkz[. Outlook'da çevrimdışı çalışma](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Tam geçiş hakkında daha fazla bilgi edinmek için bkz:

- [Tam e-posta geçişi hakkında bilmeniz gerekenler](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [E-postanın Office 365 tam geçişini gerçekleştirme](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Minimum karma geçiş

Minimum karma veya hızlı geçişte birkaç yüz posta kutusunu birkaç hafta içinde Microsoft 365 taşırsınız. Bu yöntem, paylaşılan serbest/meşgul takvim bilgileri gibi gelişmiş karma geçiş özelliklerini desteklemez.

Minimum karma geçiş, posta kutularını Microsoft 365 geçirmek için daha fazla zaman alması gereken ancak birkaç hafta içinde geçişi tamamlamayı planlayan kuruluşlar için idealdir. Karmaşıklığın büyük bölümü olmadan daha gelişmiş *tam hibrit geçişin* avantajlarından bazılarını elde edersiniz. Belirli bir anda kaç posta kutusunun ve hangi posta kutularının geçirileceğini denetleyebilirsiniz. Microsoft 365 posta kutuları, şirket içi hesapların kullanıcı adları ve parolalarıyla oluşturulur. Tam geçişlerden farklı olarak, kullanıcılarınızın Outlook profillerini yeniden oluşturması gerekmez.

Karma geçişin en az düzeyde olmasıyla ilgili dikkat edilmesi gerekenler şunlardır:

- şirket içi Active Directory sunucularınız ile Microsoft 365 arasında tek seferlik dizin eşitlemesi yapmanız gerekir.
- Kullanıcılar, Microsoft 365 posta kutularında, posta kutularının önceki kullanıcı adı ve parolası ile oturum açabilecektir.
- Geçiş yaptığınız her kullanıcı posta kutusu için Exchange Online içeren bir Microsoft 365 lisansına ihtiyacınız vardır.
- Kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmez, ancak bazı eski Android telefonların yeni bir profile ihtiyacı olabilir. Kullanıcıların e-postalarını yeniden indirmeleri gerekmez.

Daha fazla bilgi için bkz. [Exchange posta kutularını hızla Office 365 geçirmek için En Az Karma kullanma](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Tam karma

Tam karma geçişte, yüzlerce, on binlerce posta kutusuna sahip olursunuz ve bazılarını veya tümünü Microsoft 365 taşırsınız. Bu geçişler genellikle daha uzun süreli olduğundan karma geçişler şunları mümkün hale getirir:

- Şirket içi kullanıcılara, Microsoft 365'daki kullanıcılar için serbest/meşgul takvim bilgilerini (veya tam tersini) gösterin.
- Hem şirket içi hem de Microsoft 365 alıcıları içeren birleşik bir genel adres listesine bakın.
- Şirket içinde veya Microsoft 365 olup olmadıklarına bakılmaksızın tüm kullanıcılar için tam Outlook alıcı özelliklerini görüntüleyin.
- TLS ve sertifikalar kullanarak şirket içi Exchange sunucuları ile Office 365 arasındaki e-posta iletişimlerinin güvenliğini sağlayın.
- Şirket içi Exchange sunucuları ile Microsoft 365 arasında gönderilen iletileri dahili olarak değerlendirerek şunların gerçeklestirilmesini sağlayın:
  - İç iletileri hedefleyen aktarım ve uyumluluk aracıları tarafından düzgün bir şekilde değerlendirilip işlenebilir.
  - İstenmeyen posta önleme filtrelerini atla.

Tam karma geçişler, hibrit yapılandırmada uzun aylar veya daha uzun süre kalmayı bekleyen kuruluşlar için en iyisidir. Bu bölümün önceki bölümlerinde listelenen özelliklerin yanı sıra dizin eşitlemesi, daha iyi tümleşik uyumluluk özellikleri ve posta kutularını çevrimiçi posta kutusu taşımalarını kullanarak Microsoft 365 taşıma özelliğine sahip olursunuz. Microsoft 365, şirket içi kuruluşunuzun bir uzantısı haline gelir.

Tam karma geçiş hakkında dikkat edilmesi gerekenler:

- Bunlar tüm kuruluşlar için uygun değildir. Tam karma geçişlerin karmaşıklığı nedeniyle, birkaç yüzden az posta kutusu olan kuruluşlar genellikle çabayı ve maliyeti haklı gösteren avantajlar görmez. Bu gibi durumlarda bunun yerine tam geçişi veya minimum karma geçişi göz önünde bulundurmanızı öneririz.
- şirket içi Active Directory sunucularınız ile Microsoft 365 arasında Azure Active Directory (Azure AD) Bağlan kullanarak dizin eşitlemesi ayarlamanız gerekir.
- Kullanıcılar, yerel ağda oturum açarken kullandıkları kullanıcı adı ve parolayla Microsoft 365 posta kutularında oturum açabilecektir. (Bu işlev, parola eşitleme ve/veya Active Directory Federasyon Hizmetleri (AD FS) ile Azure AD Bağlan gerektirir).
- Geçiş yaptığınız her kullanıcı posta kutusu için Exchange Online içeren bir Microsoft 365 lisansına ihtiyacınız vardır.
- Kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmez, ancak bazı eski Android telefonlarda yeni bir profile ihtiyaç duyulabilir. Kullanıcıların e-postalarını yeniden indirmeleri gerekmez.

> [!IMPORTANT]
> Kuruluşunuz posta kutularını Microsoft 365 geçirmeyi seçerse ancak kullanıcı hesaplarını şirket içi Active Directory yönetmeye devam etmek için DirSync veya Azure AD Bağlan yerinde tutmayı planlıyorsa, şirket içinde en az bir Exchange sunucu tutmanız gerekir. Tüm Exchange sunucuları kaldırılırsa, Exchange Online'da Exchange alıcılarda değişiklik yapamazsınız. Bunun nedeni, yetki kaynağının şirket içi Active Directory içinde kalması ve değişikliklerin orada yapılması gerektiğidir.

Tam karma geçiş sizin için uygunsa aşağıdaki yararlı kaynaklara bakın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Karma Dağıtımları Exchange Server](/exchange/exchange-hybrid)
- [Karma Yapılandırma sihirbazı](/exchange/hybrid-configuration-wizard)
- [Karma Yapılandırma sihirbazı hakkında SSS](/exchange/hybrid-configuration-wizard-faqs)
- [Karma dağıtım önkoşulları](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Şirket içi Exchange Server daha yeni bir sürümüne yükseltme

Tamamen Microsoft 365 geçirerek en iyi değeri ve kullanıcı deneyimini elde ettiğinize kesinlikle inanıyoruz. Ancak bazı kuruluşların bazı Exchange Sunucularını şirket içinde tutması gerektiğini anlıyoruz. Bunun nedeni, verilerin yabancı bir veri merkezinde depolanmadığını garanti etmek için, bulutta karşılanamıyor benzersiz ayarlarınız veya gereksinimleriniz olması veya şirket içi Active Directory'yi kullanmaya devam ettiğiniz için bulut posta kutularını yönetmek için Exchange ihtiyacınız olması olabilir. Her durumda, Exchange şirket içinde tutarsanız, Exchange 2010 ortamınızın en az Exchange 2013 veya Exchange 2016'ya yükseltildiğinden emin olmanız gerekir.

En iyi deneyim için kalan şirket içi ortamınızı Exchange 2016'ya yükseltmenizi öneririz. Doğrudan Exchange Server 2010'dan Exchange Server 2016'ya gitmek istiyorsanız Exchange Server 2013'ü yüklemeniz gerekmez.

Exchange 2016, önceki Exchange sürümlerinin tüm özelliklerini içerir. Bazı özellikler yalnızca Microsoft 365'da kullanılabilse de, Microsoft 365 ile sağlanan deneyimle en yakından eşleşir. Kaçırdığınız şeylerden yalnızca birkaçını gözden geçirin:

|Exchange sürümü|Özellik|
|---|---|
|**Exchange 2013**|Basitleştirilmiş mimari, sunucu rollerinin sayısını üçe düşürür (Posta Kutusu, İstemci Erişimi, Edge Aktarımı)|
||Hassas bilgilerin sızmasını önlemeye yardımcı olan veri kaybı önleme ilkeleri (DLP)|
||geliştirilmiş Outlook Web App deneyimi|
|**Exchange 2016**|*Exchange 2013 ve ...*|
||Yalnızca Posta Kutusu ve Edge Aktarım için daha basitleştirilmiş sunucu rolleri|
||SharePoint ile tümleştirme ile birlikte geliştirilmiş DLP|
||Geliştirilmiş veritabanı dayanıklılığı|
||Çevrimiçi belge işbirliği|


|Dikkate|Daha fazla bilgi|
|---|---|
|Destek sonu tarihleri|Exchange 2010'da olduğu gibi her Exchange sürümünün de kendi destek sonu tarihi vardır: <br/><br/> Exchange 2013 - Nisan 2023 <br/><br/> Exchange 2016 - Ekim 2025 <br/><br/> Destek sonu tarihi ne kadar erken olursa, o kadar erken başka bir geçiş gerçekleştirmeniz gerekir. Nisan 2023 düşündüğünüzden çok daha yakın!|
|Exchange 2013 veya 2016'ya geçiş yolu|Exchange 2010'dan daha yeni bir sürüme geçiş yolu, Exchange 2013 veya Exchange 2016'yı seçtiğinizde aynıdır: <br/><br/> mevcut Exchange 2010 kuruluşunuza Exchange 2013 veya 2016 yükleyin. <br/><br/> Hizmetleri ve diğer altyapıyı Exchange 2013 veya 2016'ya taşıyın. <br/><br/> Posta kutularını ve ortak klasörleri Exchange 2013 veya 2016'ya taşı kalan Exchange 2010 sunucularının yetkisini alın.|
|Sürüm bir arada bulunma|Exchange 2013 veya Exchange 2016'ya geçiş yaparken, mevcut bir Exchange 2010 kuruluşuna herhangi bir sürümü yükleyebilirsiniz. Bu, bir veya daha fazla Exchange 2013 veya Exchange 2016 sunucusu yüklemenize ve geçişinizi yapmanıza olanak tanır.|
|Sunucu donanımı|Sunucu donanım gereksinimleri Exchange 2010'dan itibaren değişti. Donanımınızın uyumlu olduğundan emin olun. Her sürüm için donanım gereksinimleri hakkında daha fazla bilgi için buraya bakın: <br/><br/> [Exchange 2016 sistem gereksinimleri](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <br/><br/> [Exchange 2013 sistem gereksinimleri](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <br/><br/> Exchange performansındaki önemli geliştirmeler ve daha yeni sunucularda artan bilgi işlem gücü ve depolama kapasitesi sayesinde, aynı sayıda posta kutusunu desteklemek için büyük olasılıkla daha az sunucuya ihtiyacınız olacaktır.|
|İşletim sistemi sürümü|Her sürüm için desteklenen en düşük işletim sistemi sürümleri şunlardır: <br/><br/> Exchange 2016 - Windows Server 2012 <br/><br/> Exchange 2013 - Windows Server 2008 R2 SP1 <br/><br/> İşletim sistemi desteği hakkında daha fazla bilgiyi [Exchange Desteklenebilirlik Matrisi'nde](/exchange/plan-and-deploy/supportability-matrix) bulabilirsiniz.|
|Active Directory ormanı işlev düzeyi|Her sürüm için desteklenen en düşük Active Directory ormanı işlev düzeyleri şunlardır: <br/><br/> Exchange 2016 - Windows Server 2008 R2 SP1 <br/><br/> Exchange 2013 - Windows Server 2003 <br/><br/> Orman işlev düzeyi desteği hakkında daha fazla bilgiyi [Exchange Desteklenebilirlik Matrisi'nde](/exchange/plan-and-deploy/supportability-matrix) bulabilirsiniz.|
|İstemci sürümlerini Office|Her sürüm için desteklenen en düşük Office istemci sürümleri şunlardır: <br/><br/> Exchange 2016 - Office 2010 (en son güncelleştirmelerle) <br/><br/> Exchange 2013 - Office 2007 SP3 <br/><br/> Exchange [Desteklenebilirlik Matrisi'nde Office](/exchange/plan-and-deploy/supportability-matrix) istemci desteği hakkında daha fazla bilgi bulabilirsiniz.|

Geçişinize yardımcı olması için aşağıdaki kaynakları kullanın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help) için Active Directory şema değişiklikleri
- Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help) için sistem gereksinimleri
- Exchange [2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-prerequisites-exchange-2013-help) önkoşulları

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 istemci ve sunucuları ile Windows 7 seçeneklerinin özeti

Office 2010 istemcileri ve sunucuları ile Windows 7 için yükseltme, geçiş ve buluta taşıma seçeneklerinin görsel bir özeti için [destek sonu posterine](../downloads/Office2010Windows7EndOfSupport.pdf) bakın.

[![Office 2010 istemcileri ve sunucuları ile Windows 7 posteri için destek sonu.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Bu tek sayfalık posterde, Office 2010 istemci ve sunucu ürünlerine yanıt vermek için izleyebileceğiniz çeşitli yollar ve Windows 7 destek sonuna ulaşıyor, tercih edilen yollar ve Microsoft 365 Kurumsal seçeneği desteği vurgulanmış olarak gösterilmektedir.

Ayrıca bu posteri [indirebilir](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) ve mektup, yasal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

## <a name="what-if-i-need-help"></a>Ya yardıma ihtiyacım olursa?

Microsoft 365 geçiş gerçekleştiriyorsanız Microsoft FastTrack hizmetimizi kullanmaya uygun olabilirsiniz. FastTrack, Microsoft 365 geçişinizi mümkün olduğunca sorunsuz hale getirmek için en iyi yöntemleri, araçları ve kaynakları sağlar. En iyisi, planlama ve tasarımdan son posta kutunuzu geçirmenize kadar size yol gösterir. FastTrack hakkında daha fazla bilgi için bkz. [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Microsoft 365 geçişiniz sırasında sorunlarla karşılaşırsanız ve FastTrack kullanmıyorsanız veya Exchange Server daha yeni bir sürümüne geçiriyorsanız, kullanabileceğiniz bazı kaynaklar şunlardır:

- [Teknik topluluk](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Müşteri desteği](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>İlgili makaleler

[Office 2010 sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2010-servers-and-products.md)
