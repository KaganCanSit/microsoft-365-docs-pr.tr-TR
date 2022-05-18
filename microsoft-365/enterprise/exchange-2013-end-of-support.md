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
description: Exchange 2013, Nisan 2023'te destek sonuna ulaşacaktır. Şirket içi Exchange Server Exchange Online veya sonraki bir sürümüne yükseltmeye hazırlanmak için bu planlama yol haritasını kullanın.
ms.openlocfilehash: 0d0cf068ad018e710c6d8e861ac04acfd261def9
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468514"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange 2013 destek sonu yol haritası

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Exchange Server 2013 **, 11 Nisan 2023** tarihinde destek sonuna ulaşacaktır. Exchange 2013'ten Microsoft 365, Office 365 veya Exchange 2019'a geçişe henüz başlamadıysanız, şimdi planlamaya başlamanın tam zamanı.

## <a name="what-does-end-of-support-mean"></a>*Destek sonu* ne anlama gelir?

Microsoft ürünlerinin çoğu, yeni özellikler, hata düzeltmeleri, güvenlik düzeltmeleri vb. edindikleri bir destek yaşam döngüsüne sahiptir. Bu yaşam döngüsü genellikle ürünün ilk sürümünden itibaren 10 yıl sürer. Bu yaşam döngüsünün sonu, ürünün destek sonu olarak bilinir. Exchange 2013, 11 Nisan 2023'te destek sonuna ulaştığından, Microsoft artık bu tarihten sonra aşağıdakileri sağlamayacaktır:

- Oluşabilecek sorunlar için teknik destek.
- Sunucunun kararlılığını ve kullanılabilirliğini etkileyebilecek sorunlar için hata düzeltmeleri.
- Sunucuyu güvenlik ihlallerine açık hale getirebilecek güvenlik açıklarına yönelik güvenlik düzeltmeleri.
- Saat dilimi güncelleştirmeleri.

Exchange 2013 yüklemeniz bu tarihten sonra çalışmaya devam edecektir. Ancak yukarıda listelenen değişiklikler nedeniyle, en kısa sürede Exchange 2013'ten Exchange 2019'a geçmenizi kesinlikle öneririz.


## <a name="what-are-my-options"></a>Seçeneklerim nelerdir?

Seçeneklerinizi keşfetmek ve bir geçiş planı hazırlamak için harika bir zaman. Şunları yapabilirsiniz:

- Microsoft 365 geçiş. Tam geçiş, en düşük karma veya tam karma geçişi kullanarak posta kutularını, ortak klasörleri ve diğer verileri geçirin. Ardından şirket içi Exchange sunucularını ve Active Directory'yi kaldırın.
- 2013 Exchange yükseltin. Şirket içi sunucularınız için Exchange 2019'a geçin.

> [!IMPORTANT]
> Kuruluşunuz posta kutularını Microsoft 365 geçirmeyi seçerse ancak Active Directory'deki kullanıcı hesaplarını yönetmek için Azure AD Bağlan kullanmaya devam etmeyi planlıyorsa, en az bir Microsoft Exchange sunucusunu şirket içinde tutmanız gerekir. Tüm Exchange sunucuları kaldırırsanız, yetki kaynağı sizin şirket içi Active Directory olduğundan Exchange Online'daki Exchange alıcılarda değişiklik yapamazsınız. Bu senaryoda, aşağıdaki seçeneklere sahipsiniz:
>
>- *Önerilen:* Posta kutularınızı Microsoft 365 geçirin ve ortamınızı 11 Nisan 2023'e kadar Exchange 2019'a yükseltin. Microsoft 365 bağlanmak ve posta kutularını geçirmek için Exchange 2013'i kullanın. Ardından, Exchange 2013'ten Exchange 2019'a yükseltin ve Exchange 2013 çalıştıran sunucuların yetkisini alın.
>- Exchange Online geçişini tamamlayamaz ve şirket içi sunucularınızı 11 Nisan 2023'e kadar yükseltemiyorsanız, önce Exchange 2013'ten Exchange 2019'a yükseltin ve ardından posta kutularını Microsoft 365 geçirmek için Exchange 2019'ı kullanın.

Exchange Server 2013 desteğinin sona ermesini önlemek için izleyebileceğiniz üç yol aşağıdadır.

## <a name="migrate-to-microsoft-365"></a>Microsoft 365'e geçiş

Microsoft 365 geçiş, Exchange 2013 dağıtımınızı devre dışı bırakmanıza yardımcı olacak en iyi ve en basit seçenektir. Microsoft 365 geçişle, eski teknolojiden geçerli özelliklere şu özellikler gibi tek bir atlama yapabilirsiniz:

- Daha fazla veri dayanıklılığına sahip daha büyük posta kutuları;
- İstenmeyen posta ve kötü amaçlı yazılımdan koruma gibi güvenlik özellikleri, 
- Veri Kaybı Önleme, Bekletme İlkeleri, In-Place ve Dava Tutma, yerinde eBulma ve daha fazlası gibi uyumluluk özellikleri;
- SharePoint Online, OneDrive, Teams, Power BI ve diğer Microsoft 365 hizmetleriyle tümleştirme;
- Odaklanmış Gelen Kutusu; Ve
- Gelişmiş analiz ve Viva Analizler.

Microsoft 365 ayrıca yeni özellikleri ve deneyimleri de ilk olarak alır, böylece kuruluşunuz bunları hemen kullanmaya başlayabilir. Ayrıca, şu konularda endişelenmeniz gerekmez:

- Donanım satın alma ve bakım;
- Sunucularınızı çalıştırmak ve soğutmak için ödeme;
- Sunucuları güvenlik, ürün ve saat dilimi düzeltmeleri hakkında güncel tutma;
- Uyumluluk gereksinimlerini desteklemek için sunucu depolama ve yazılım bakımını yapmak; Veya
- yeni bir Exchange sürümüne yükseltme; her zaman Microsoft 365 ile en son sürümdesiniz.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Microsoft 365'a nasıl geçiş yapmalıyım?

Kuruluşunuza bağlı olarak, Microsoft 365 ulaşmak için birkaç seçeneğiniz vardır. İlk olarak, aşağıdakiler gibi birkaç şeyi göz önünde bulundurmanız gerekir:

- Taşımanız gereken posta kutularının sayısı;
- Geçişin ne kadar sürmesini istiyorsunuz; Ve
- Geçiş sırasında şirket içi ortamınızla Microsoft 365 arasında sorunsuz bir tümleştirmeye ihtiyacınız olup olmadığı.

Bu tablo, geçiş seçeneklerinizi ve hangi yöntemin kullanılacağını belirleyen en önemli faktörleri gösterir.

<br>

****

|Geçiş seçeneği|Kuruluş boyutu|Süre|
|---|---|---|
|Tam geçiş|150'den az posta kutusu|Bir hafta veya daha az|
|Minimum karma geçiş|150'den az posta kutusu|Birkaç hafta veya daha az|
|Tam karma geçiş|150'den fazla posta kutusu|Birkaç hafta veya daha fazla|
|

Aşağıdaki bölümlerde bu yöntemlere genel bir bakış sunun. Daha fazla bilgi için bkz. [Geçiş yoluna karar verme](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Tam geçiş

Tam geçişte, tüm posta kutularınızı, dağıtım gruplarınızı, kişilerinizi vb. belirli bir tarih ve saatte Office 365 geçirirsiniz. İşiniz bittiğinde şirket içi Exchange sunucularınızı kapatır ve yalnızca Microsoft 365 kullanmaya başlarsınız.

Tam geçiş, çok fazla posta kutusu olmayan, hızlı bir şekilde Microsoft 365 almak isteyen ve diğer yöntemlerin karmaşıklığıyla ilgilenmek istemeyen küçük kuruluşlar için harikadır. Ancak bir hafta veya daha kısa bir süre içinde tamamlanmalıdır. Ayrıca kullanıcıların Outlook profillerini yeniden yapılandırması gerekir. Tam geçiş 2.000 posta kutusuna kadar geçiş yapabilir, ancak en fazla 150 posta kutusu için kullanmanızı öneririz. Daha fazla geçiş yapmaya çalışırsanız, son tarihinizden önce tüm posta kutularını aktarmak için zamanınız tükenebilir ve BT destek personeliniz kullanıcıların Outlook yeniden yapılandırmasına yardımcı olmak için yapılan isteklerle bunalabilir.

Tam geçişle ilgili dikkat edilmesi gerekenler şunlardır:

- Microsoft 365 443 numaralı TCP bağlantı noktası üzerinden Outlook Anywhere kullanarak Exchange 2013 sunucularınıza bağlanması gerekir.
- Tüm şirket içi posta kutuları Microsoft 365 taşınacaktır.
- Kullanıcılarınızın posta kutularına okuma erişimi olan bir şirket içi yönetici hesabınız olmalıdır.
- Microsoft 365 kullanmak istediğiniz Exchange 2013 kabul edilen etki alanlarının hizmete doğrulanmış etki alanları olarak eklenmesi gerekir.
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
- şirket içi Active Directory sunucularınızla Microsoft 365 arasında Azure Active Directory (Azure AD) Bağlan kullanarak dizin eşitlemesi ayarlamanız gerekir.
- Kullanıcılar, yerel ağda oturum açarken kullandıkları kullanıcı adı ve parolayla Microsoft 365 posta kutularında oturum açabilecektir. (Bu işlev parola eşitleme ve/veya Active Directory Federasyon Hizmetleri (AD FS) ile Azure AD Bağlan gerektirir).
- Geçiş yaptığınız her kullanıcı posta kutusu için Exchange Online içeren bir Microsoft 365 lisansına ihtiyacınız vardır.
- Kullanıcıların cihazlarının çoğunda yeni bir Outlook profili ayarlamaları gerekmez, ancak bazı eski Android telefonların yeni bir profile ihtiyacı olabilir. Kullanıcıların e-postalarını yeniden indirmeleri gerekmez.

> [!IMPORTANT]
> Kuruluşunuz posta kutularını Microsoft 365 geçirmeyi seçerse ancak Active Directory'deki kullanıcı hesaplarını yönetmek için Azure AD Bağlan tutmayı planlıyorsa, şirket içinde en az bir Exchange sunucu tutmanız gerekir. Tüm Exchange sunucuları kaldırılırsa, Exchange alıcılarda değişiklik yapamazsınız. Bunun nedeni, yetki kaynağının Active Directory olması ve değişikliklerin orada yapılması gerekir.

Tam karma geçiş sizin için uygunsa aşağıdaki yararlı kaynaklara bakın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Karma Dağıtımları Exchange Server](/exchange/exchange-hybrid)
- [Karma Yapılandırma sihirbazı](/exchange/hybrid-configuration-wizard)
- [Karma Yapılandırma sihirbazı hakkında SSS](/exchange/hybrid-configuration-wizard-faqs)
- [Karma dağıtım önkoşulları](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Şirket içi Exchange Server daha yeni bir sürümüne yükseltme

Tamamen Microsoft 365 geçirerek en iyi değeri ve kullanıcı deneyimini elde ettiğinize kesinlikle inanıyoruz. Ancak bazı kuruluşların bazı Exchange sunucularını şirket içinde tutması gerektiğini anlıyoruz. Bunun nedeni, verilerin yabancı bir veri merkezinde depolanmadığını garanti etmek için, bulutta karşılanamıyor benzersiz ayarlarınız veya gereksinimleriniz olması veya şirket içi Active Directory'yi kullanmaya devam ettiğiniz için bulut posta kutularını yönetmek için Exchange ihtiyacınız olması olabilir. Her durumda, Exchange şirket içinde tutarsanız, Exchange 2013 ortamınızın yükseltildiğinden emin olmanız gerekir.

En iyi deneyim için kalan şirket içi ortamınızı Exchange 2019'a yükseltmenizi öneririz. doğrudan Exchange Server 2013'ten Exchange Server 2019'a geçebileceğiniz için Exchange Server 2016'ya yüklemeniz gerekmez. Exchange 2019, Microsoft 365 ile sunulan deneyimle en yakından eşleşir ancak bazı özellikler yalnızca Microsoft 365'de kullanılabilir.



****
Exchange 2013'e yükseltme hakkında bilmeniz gereken önemli şeyler aşağıdadır:

|Öğe|Daha fazla bilgi|
|---|---|
|Destek sonu tarihleri|Exchange 2013'de olduğu gibi her Exchange sürümünün de kendi destek sonu tarihi vardır: <p> Exchange 2013 - Nisan 2023 <p> Nisan 2023 düşündüğünüzden çok daha yakın!|
|Exchange 2019'a geçiş yolu|Exchange 2013'ten daha yeni bir sürüme geçiş yolu basittir: <p> mevcut Exchange 2013 kuruluşunuza Exchange 2019'u yükleyin. <p> Hizmetleri ve verileri Exchange 2013'ten Exchange 2019'a taşıyın ve Exchange 2013 sunucularının yetkisini alın.|
|Sunucu donanımı|Sunucu donanım gereksinimleri Exchange 2013'ten itibaren değişti. Donanımınızın uyumlu olduğundan emin olun. Donanım gereksinimleri hakkında daha fazla bilgi için buraya bakın: <p> [Exchange 2019 sistem gereksinimleri](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Exchange performansındaki önemli geliştirmeler ve daha yeni sunucularda artan bilgi işlem gücü ve depolama kapasitesi sayesinde, aynı sayıda posta kutusunu desteklemek için büyük olasılıkla daha az sunucuya ihtiyacınız olacaktır.|
|İşletim sistemi sürümü|Exchange 2019 için desteklenen en düşük işletim sistemi sürümü Windows Server 2019'dur. Windows Server 2022 desteği yakında sunulacak <p> İşletim sistemi desteği hakkında daha fazla bilgiyi [Exchange Desteklenebilirlik Matrisi'nde](/exchange/plan-and-deploy/supportability-matrix) bulabilirsiniz.|
|Active Directory ormanı işlev düzeyi|Desteklenen en düşük Active Directory ormanı işlev düzeyi R2 Windows Server 2012 dir. Orman işlev düzeyi desteği hakkında daha fazla bilgiyi [Exchange Desteklenebilirlik Matrisi'nde](/exchange/plan-and-deploy/supportability-matrix) bulabilirsiniz.|
|İstemci sürümlerini Office|Desteklenen en düşük Office istemci sürümü de [Exchange Desteklenebilirlik Matrisi'nde](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients) belgelenmiştir.|
|

Geçişinize yardımcı olması için aşağıdaki kaynakları kullanın:

- [Exchange Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)
- [Exchange 2019 için Active Directory şema değişiklikleri](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019)
- [Exchange 2019 için sistem gereksinimleri](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019)


## <a name="what-if-i-need-help"></a>Ya yardıma ihtiyacım olursa?

Microsoft 365 geçiş gerçekleştiriyorsanız Microsoft FastTrack hizmetimizi kullanmaya uygun olabilirsiniz. FastTrack, Microsoft 365 geçişinizi mümkün olduğunca sorunsuz hale getirmek için en iyi yöntemleri, araçları ve kaynakları sağlar. En iyisi, planlama ve tasarımdan son posta kutunuzu geçirmenize kadar size yol gösterir. FastTrack hakkında daha fazla bilgi için bkz. [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Microsoft 365 geçişiniz sırasında sorunlarla karşılaşırsanız ve FastTrack kullanmıyorsanız veya Exchange Server daha yeni bir sürümüne geçiriyorsanız, kullanabileceğiniz bazı kaynaklar şunlardır:

- [Teknik topluluk](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Müşteri desteği](https://support.microsoft.com/gp/support-options-for-business)


