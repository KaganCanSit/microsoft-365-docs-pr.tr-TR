---
title: SharePoint 2010'dan yükseltme
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: SharePoint Server 2010 ve SharePoint yükseltme için bilgi ve kaynakları bulun. Her ikisi için de destek 13 Nisan 2021'de sona erer.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7ce6b333e39d02000514c174579a1ad0fa816771
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988585"
---
# <a name="upgrading-from-sharepoint-2010"></a>SharePoint 2010'dan yükseltme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft SharePoint 2010 ve SharePoint Server 2010, **13 Nisan 2021'de destek sonuna ulaşacak**. Bu makale, var olan SharePoint Server 2010 verilerinizi Microsoft 365'te SharePoint Online'a geçirmenize veya şirket içi SharePoint Server 2010 ortamınızı yükseltmenize yardımcı olacak kaynakları sağlar.

## <a name="what-is-end-of-support"></a>Destek *sonu nedir*?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Destek sonu tarihini tamamlanın, ürün çalışmayı durdurmaz, ancak Microsoft artık şunları sağlar:

- Ortaya çıkabilir sorunlar için teknik destek.

- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.

- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Bu, ürün için başka güncelleştirme, yama veya düzeltme (güvenlik yamaları/düzeltmeleri de dahil) olmayacaktır. Microsoft Desteği, destek çalışmalarını tümüyle daha yeni sürümlere kaydıracak.

SharePoint Server 2010 desteğinin sonunda, ürünü yükseltmeden ve önemli verilerinizi geçirmeden önce artık ihtiyacınız olan verileri silin.

> [!NOTE]
> Bir yazılım yaşam döngüsü genellikle ilk sürümden itibaren on yıl devam eder. [Microsoft çözüm sağlayıcıları](https://go.microsoft.com/fwlink/?linkid=841249) yazılımın sonraki sürümüne yükseltmenıza veya geçiş için geçiş (veya her iki sürüme Microsoft 365 yardımcı olabilir. Kritik temel teknolojiler için, özellikle de Microsoft SQL Server ile birlikte kullanmakta olduğunuz teknolojilerin destek sonu tarihlerini bildiğinizden emin SharePoint. Daha fazla bilgi için bkz. [Sabit Yaşam Döngüsü İlkesi](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Devam et'i planla

Desteğin Ürün Yaşam Döngüsü sitesinde sona [erer tarihlerini kontrol edin](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Yükseltmelerinizi veya geçişlerinizi bu tarihleri unutmayın. Ürününüz listelenen *tarihte çalışmayı durdurmayacak* . Ancak, yükleme işleminize bu tarihten sonra yama olmayacak olması nedeniyle ürünün sonraki sürümüne sorunsuz bir geçiş planlamak istemeniz gerekir.

Bu matris, geçiş seçenekleri arasında bir kursun çizimine yardımcı olur:

|Destek ürünü sonu|İyi |En iyi|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (şirket içi)|SharePoint Online|
||SharePoint Online ile SharePoint Server 2013 karma|SharePoint Server 2016 (şirket içi)|
|||SharePoint Bulut Karma Arama|

Ölçeğin alt ucunda (iyi) bir seçenek belirtirseniz, SharePoint Server 2010'dan geçiş sonrasında başka bir yükseltme planlamaya başlamanız gerekir.

SharePoint Server 2010 desteğinin sona erer.

![SharePoint Server 2010 yükseltme yolları.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> SharePoint Server 2010 ve SharePoint Foundation 2010 için destek sonu, şu anda 13 Nisan 2021'e zamanlandı. Ancak, en güncel [tarihler için Ürün Yaşam](https://support.microsoft.com/lifecycle) Döngüsü sitesini kontrol edin.

## <a name="whats-next"></a>Sırada ne var?

SharePoint Server 2013 ve SharePoint Foundation 2013 şirket içinde kendi sunucularınıza yükleyebilir. Ya da SharePoint parçası olan çevrimiçi bir hizmet olan Microsoft 365. Şunları seçebilirsiniz:

- SharePoint Online'a geçiş.

- SharePoint Server veya SharePoint Foundation şirket içi sürümüne yükseltin.

- Yukarıdakilerin ikisini de yapma.

- Karma bir [SharePoint](/sharepoint/hybrid/hybrid) hayata geçirin.

Özelleştirmelerin bakımı ve yükseltilmesi de içinde olmak üzere, sunucularını korumanın gizli maliyetlerini göz önünde bulundurabilirsiniz. Bu etmenlere hesap verdiysiniz, şirket içi yükseltme daha kolay olacaktır. Sunucu grubunızı çok fazla özelleştirme olmaksızın eski SharePoint Sunucuları üzerinde çalıştırsanız, SharePoint Online'a planlanan bir geçişten SharePoint olabilir. Şirket içi SharePoint Server ortamında, donanım yönetim yükünü azaltmak için bazı verileri SharePoint Online'a taşımayı da göz önünde bulundurabilirsiniz.

> [!NOTE]
> SharePoint yöneticiler bir Microsoft 365 Aboneliği oluşturabilir, yeni SharePoint Online siteleri oluşturabilir ve ardından yalnızca temel belgeleri yeni sitelere alarak SharePoint Server 2010'dan temiz bir şekilde oluşturabilir. Ardından, kalan tüm veriler SharePoint Server 2010 sitesinden şirket içi arşivlere tüketebilirsiniz.

|SharePoint Online|SharePoint Server şirket içi|
|---|---|
|Zaman içinde yüksek maliyet (plan/yürütme/doğrulama)|Zaman içinde yüksek maliyet (plan/yürütme/doğrulama)|
|Fonlarda düşük maliyet (donanım satın alma yok)|Kredilerde yüksek maliyet (donanım satın almaları)|
|Geçişte bir defalık maliyet|Gelecek geçiş başına tekrarlanan tek seferlik maliyet|
|Düşük toplam sahip olma/bakım maliyeti|Yüksek toplam sahip olma/bakım maliyeti|

Buluta tek seferlik bir Microsoft 365 verilerinizi düzenleyecek ve buluta neleri bırakacağıza ve neleri bırakacağıza karar verirken, daha yüksek bir maliyetle devam eder. Ama verileriniz geçirildikten sonra, gelecek yükseltmeler otomatik olarak yapılır çünkü artık donanım ve yazılım güncelleştirmelerini yönetmenize gerek olmayacaktır. Ayrıca, grup süreniz Microsoft hizmet düzeyi sözleşmesi [(SLA) ile de destek dönecektir](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement).

### <a name="migrate-to-sharepoint-online"></a>SharePoint Online'a geçiş

SharePoint Online'ın ihtiyacınız olan tüm özellikleri sunduğundan emin olun. Hizmet [SharePoint bakın](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

SharePoint Server 2010'dan (veya SharePoint Foundation 2010) doğrudan SharePoint Online'a SharePoint. Geçiş işleminin büyük bir işi el ile yapılan bir iştir. Ancak bu aşama size, taşıma öncesinde artık gerekli olan verileri ve siteleri daha iyi değerlendirebilirsiniz. Diğer verileri depolama alanına arşivebilirsiniz. 

SharePoint Server 2010 ve SharePoint Foundation 2010 destek sonunda çalışmayı durdurmayacaklarını unutmayın. Bu nedenle yöneticilerin, müşterileri SharePoint bazı verileri taşımayı unutursa, Yöneticilerin Çalışma Süresi'nin hala çalışıyor olduğu bir dönem olabilir.

SharePoint Server 2013 veya SharePoint Server 2016'ya yükselter ve verileri SharePoint Online'a koymaya karar verirsiniz, bilgileri OneDrive İş'e geçirmek için [SharePoint Geçiş API'sini](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) kullanabilirsiniz.

|SharePoint Online avantajı|SharePoint Online dezavantajı|
|---|---|
|Microsoft, SPO donanımlarını ve tüm donanım yönetimini sağlar.|Kullanılabilir özellikler, SharePoint Server şirket içi ile SPO arasında farklılık gösterebilir.|
|Aboneliğinizin SharePoint yöneticisi veya genel yöneticisisiniz ve SPO sitelerine yöneticiler atabilirsiniz.|SharePoint Server şirket içi sunucu grubu yöneticisi tarafından kullanılabilen bazı eylemler, şirket içi Sunucu Grubu'SharePoint Yönetici rolünde yoktur Microsoft 365. Ancak SharePoint, Site Koleksiyonu Yönetimi ve Site Sahipliği kuruluşta yereldir.|
|Microsoft, SQL Online'ın çalıştıracağı sunucularda dahil olmak üzere, temel SQL, SharePoint düzeltmeler ve güncelleştirmeler uygular.|Hizmette temel dosya sistemine erişim olduğundan, özelleştirme sınırlıdır.|
|Microsoft, hizmet [düzeyi anlaşmaları yayımlar](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) ve hizmet düzeyi olaylarını çözmek için hızla harekete geçen bir yöntemdir.|SharePoint Online'da yedekleme, geri yükleme ve diğer kurtarma seçenekleri hizmet SharePoint. Kullanılmazsa yedeklerin üzerine yazılır.|
|Microsoft, hizmette güvenlik testi ve sunucu performans ayarı sürekli olarak gerçekleştirilen bir hizmettir.|Kullanıcı arabiriminde ve diğer SharePoint özelliklerinde yapılan değişiklikler hizmet tarafından yüklenir ve bunun açık veya kapalı olması gerekir.|
|Microsoft 365 birçok endüstri standarda uygundur: [Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) yardımı sınırlıdır.  <br/> Yükseltmenin büyük bir yolu el ile veya SharePoint Online ve Geçiş İçeriği Yol Haritası'OneDrive açıklanan SPO [Geçiş API'si aracılığıyla ılacaktır](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft Destek mühendislerinin ve veri merkezi çalışanlarının aboneliğinize kısıtlamasız yönetici erişimi yok.|Yeni sürümü desteklemek için donanım altyapısının yükselti yapılması gerekirse veya yükseltme için ikincil bir grup SharePoint bir grup gerekirse ek maliyetler olabilir.|
|Çözüm sağlayıcıları, SharePoint Online'a verilerinizi tek seferlik bir işte yardımcı olabilir.|SharePoint Online'da yapılan tüm değişiklikler sizin denetiminiz içinde değildir. Geçiş sonrasında menüler, kitaplıklar ve diğer özellikler tasarım farklılıkları geçici olarak kullanılabilirliği etkileyebilir.|
|Çevrimiçi ürünler hizmet genelinde otomatik olarak güncelleştirilir. Özellikler kullanımdan kullanımdan kullanım dışı olabilir, ancak destek yaşam döngüsünün gerçek bir sonu yoktur.|SharePoint Server veya SharePoint Foundation'ın yanı sıra temel SQL vardır.|

Yeni bir site oluşturmaya karar Microsoft 365 ve gerektiğinde verileri bu siteye el ile geçirecekse, Microsoft 365 [kontrol edin](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>SharePoint Server şirket içi sürümüne yükseltme

Yükseltmeler SharePoint Server 2019 olarak *devam gerekiyor*. SharePoint Server 2010'dan SharePoint Server 2016'ya veya SharePoint 2019'a yükseltmenin hiçbir yolu yoktur. Seri yükseltme yolu:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

2010'dan SharePoint Server 2016'ya kadar yolun tamamını takip etmek SharePoint zaman alır. Yükseltmeler donanım (SQL da yükseltil olmalı), yazılım ve yönetimle ilgili maliyetleri içerir. Ayrıca, özelleştirmelerin yükseltilmiş veya vazgeçilmiş olması da gerekir. Kritik özelleştirmeleri, SharePoint Server sunucu grubunızı yükseltmeden önce belge SharePoint emin olun.

> [!NOTE]
> Destek sonu SharePoint 2010 sunucu grubuyu korumak, yeni donanıma bir SharePoint Server 2016 grubu yüklemek (dolayısıyla ayrı gruplarda yan yana çalıştırıldı) ve ardından içeriğin el ile geçişini planlamak ve yürütmek (örneğin, içeriği indirmek ve yeniden karşıya yüklemek için) mümkündür. Ancak bu el ile yapılan taşımalarda, 2010'dan gelen ve el ile taşımayı yapılan hesabın diğer adı ile son değiştirilen geçerli hesaba sahip belgeler gibi olası aksalar vardır. Ayrıca siteleri, alt siteleri, izinleri ve liste yapılarını yeniden ekleme gibi bazı çalışmalar da öncesinden yapılması gerekir. Yükseltmeden önce ortamınızı temizlemeye emin olun. Depolama alanına hangi verileri taşıyabilirsiniz, yoksa artık ihtiyacınız olmadığını düşünün. Bu durum, geçişin etkisini azaltır. Yükseltmeden önce ve (kesinlikle) siz izin olmadan önce, var olan grubun işlevsel olduğunu emin olun!

Desteklenen ve desteklenmeyen *yükseltme yollarını gözden geçirmeyi unutmayın*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Özelleştirmeleriniz *varsa*, geçiş yolunun her adımı için planlamanız kritik öneme sahip olur:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Şirket içi avantajı|Şirket içi dezavantaj|
|---|---|
|Sunucu donanımından yukarıya SharePoint Sunucu Grubu'SQL her yönüyle tam denetim.|Tüm kesmeler ve düzeltmeler, tüm şirketin sorumluluğundadır. Ancak ürününüz destek sona ermiş değilse ücretli Microsoft Desteği ile etkileşime geçsiniz.|
|Şirket içi sunucu grubunızı karma aracılığıyla bir SharePoint Online aboneliğine bağlama seçeneğiyle, SharePoint SharePoint Server şirket içi özelliğinin tam özellik kümesi.|Yükseltme, yamalar, güvenlik düzeltmeleri, donanım yükseltmeleri ve SharePoint Server ile onun SQL sunucu grubu tüm bakımı şirket içinde yönetilir.|
|SharePoint Online'dan daha fazla özelleştirme seçeneği için tam erişim.|[Microsoft uyumluluk tekliflerini](/compliance/regulatory/offering-home) şirket içinde el ile yapılandırmalısınız.|
|Şirket içinde güvenlik testi ve sunucu performans ayarı sizin denetiminiz altında gerçekleştirilen bir hizmettir.|Microsoft 365, SharePoint Server şirket içi ile birlikte çalışmayan SharePoint Online'a özellikler sağlar.|
|Çözüm sağlayıcıları, verilerin SharePoint Server'ın sonraki sürümüne (ve ötesine) geçişe yardımcı olabilir.|SharePoint Server siteleriniz, [SharePoint Online'da olduğu gibi SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) sertifikalarını otomatik olarak kullanmaz.|
|SharePoint Server şirket içinde adlandırma kuralları, yedekleme, geri yükleme ve diğer kurtarma seçenekleri üzerinde tam denetim.|SharePoint Server şirket içi, ürün yaşam döngüleri için çok duyarlıdır.|

### <a name="upgrade-resources"></a>Kaynakları yükseltme

Başlangıç olarak donanım ve yazılım gereksinimlerini karşılaştırabilirsiniz. Geçerli ortamınız temel gereksinimleri karşılamıyorsa, önce sunucu grubu veya ana sunucu SQL yükseltmeniz gerekir. 

Sitelerinizi bazı sitelerinizi SharePoint Online'ın "evergreen" donanıma taşımaya karar SharePoint. Değerlendirmenizi tamamlanın, desteklenen yükseltme yollarını ve yöntemlerini izleyin.

- *Donanım/yazılım gereksinimleri:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Yazılım sınırları ve sınırlamaları:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Yükseltme sürecine genel bakış:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>SharePoint Online ve SharePoint Server şirket içi ile karma çözüm oluşturma

Karma kurulum, bazı geçiş 2013 için hem şirket içi hem de çevrimiçi olarak en iyi şekilde sağlar. SharePoint karma oluşturmak için SharePoint Online'a SharePoint Server 2013, 2016 veya 2019 sunucu gruplarını bağlanabilirsiniz: SharePoint çözümleri hakkında bilgi [SharePoint öğrenin](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Geçiş hedefiniz karma SharePoint Sunucu grubu ise, çevrimiçi olarak hangi sitelerin ve kullanıcıların taşınacağız, hangi sitelerin ve kullanıcıların şirket içinde kalması gerekmektedir. SharePoint Server sunucu grubu içeriğinizin şirket için yüksek, orta veya düşük etki olarak derecelendirmesi bu kararda yardımcı olabilir. Oturum açma için kullanıcı hesaplarını ve SharePoint Server arama dizinini SharePoint Online ile paylaşmanız gerekir. Ancak, sitelerinizi nasıl kullandığına bakana kadar bu faktör net olmaz. Daha sonra tüm içeriğinizi SharePoint Online'a geçirmeye karar verirse, kalan tüm hesapları ve verileri çevrimiçi olarak taşımaya ve şirket içi grubun veri sahiplerini alabilirsiniz. Grup grubu yönetim/SharePoint bu noktadan sonra Microsoft 365 konsollar aracılığıyla yapılır.

Var olan karma türleri hakkında bilgi sahibi olun ve şirket içi karma grubuzla SharePoint aboneliğiniz arasındaki bağlantıyı Microsoft 365 olun.

|Seçenek|Açıklama|
|---|---|
|[Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) yardımı sınırlıdır.<br/><br/> Yükseltmenin büyük bir yolu el ile veya SharePoint Online ve Geçiş İçeriği Yol Haritası'OneDrive açıklanan SPO [Geçiş API'si aracılığıyla ılacaktır](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft Destek mühendislerinin ve veri merkezi çalışanlarının aboneliğinize kısıtlamasız yönetici erişimi yok.|Donanım altyapısının yeni sürümüne destek olmak için donanım altyapısının yükseltilsi gerekirse veya ikincil bir grup gerekirse ek maliyetler SharePoint olabilir.|
|İş ortakları, SharePoint Online'a verilerinizin tek seferlik bir şekilde SharePoint olabilir.||
|Çevrimiçi ürünler hizmet genelinde otomatik olarak güncelleştirilir. Özellikler kullanımdan kullanımdan söner, ancak desteğin gerçek bir sonu yoktur.||

Yeni bir site oluşturmaya ve gerektiğinde Microsoft 365 bu siteye el ile geçirmeye karar verdiysanız, Microsoft 365 [kontrol edin](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>SharePoint Server şirket içi sürümüne yükseltme

Yükseltmelerde sürüm atlamanın hiçbir yolu SharePoint yoktur. Başka bir ifadeyle yükseltmeler seri olarak ilerler:

- SharePoint Server 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

SharePoint 2007'den SharePoint Server 2016'ya kadar tüm yolu almak önemli ölçüde zaman alacak ve donanım (SQL sunucuları da yükseltilsin), yazılım ve yönetim maliyetlerini içerir. Özelliğin ne kadar kritik olduğunu temel alan özelleştirmelerin yükseltildikten veya vazgeçilmiş olması gerekir.

> [!NOTE]
> Kullanım ömrü sona ermiş SharePoint 2007 sunucu grubunızı korumak, yeni donanıma bir SharePoint Server 2016 sunucu grubu yüklemek (dolayısıyla ayrı gruplarda yan yana çalıştırıldı) ve ardından içeriğin el ile geçişini planlamak ve yürütmek (örneğin, içeriği indirmek ve yeniden karşıya yüklemek için) mümkündür. Ancak, bu el ile taşımalarda, son değiştirilen hesabı el ile taşımayı eden hesabın diğer adıyla değiştirme gibi bazı dezavantajlar vardır. Ayrıca siteleri, alt siteleri, izinleri ve liste yapılarını yeniden ekleme gibi çok daha fazla işi öncesinden yapılması gerekir. Her durumda, depolamaya hangi verileri taşıyabilirsiniz, yoksa geçişin etkisini azaltmanız gerekmeyecektir.

Yükseltmeden önce ortamınızı temizlemeyi sağlar. Yükseltmeden önce ve kesinlikle siz izin olmadan önce, var olan grubun işlevsel olduğunu emin olun!

Desteklenen ve desteklenmeyen *yükseltme yollarını gözden geçirmeyi unutmayın*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Özelleştirmeleriniz *varsa*, geçiş yolunun her adımı için yükseltmenizi planlamanız çok önemlidir:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Şirket içi artı|Şirket içi con|
|---|---|
|Sunucu donanımından yukarıya, SharePoint Sunucu Grubu'hepsinin tam denetimi.|Tüm kesmeler ve düzeltmeler, tüm şirketin sorumluluğundadır. (Ancak ürününüz destek sona ermiş değilse ücretli Microsoft Desteği ile etkileşime geçsiniz.)|
|Şirket içi sunucu grubunızı karma aracılığıyla bir SharePoint Online aboneliğine bağlama seçeneğiyle, SharePoint SharePoint Server şirket içi özelliğinin tam özellik kümesi.|Yükseltme, yamalar, güvenlik düzeltmeleri ve şirket içinde yönetilen SharePoint Sunucusunun tüm bakımı.|
|Daha fazla özelleştirme için tam erişim.|[Microsoft uyumluluk tekliflerini](/compliance/regulatory/offering-home) şirket içinde el ile yapılandırmalısınız.|
|Şirket içinde güvenlik testi ve sunucu performans ayarı sizin denetiminiz altında gerçekleştirilen bir hizmettir.|Microsoft 365, SharePoint Server şirket içi ile birlikte çalışmayan SharePoint SharePoint tarafından kullanılabilir.|
|İş ortakları, verilerin SharePoint Server'ın sonraki sürümüne (ve ötesine) geçişe yardımcı olabilir.|SharePoint Server siteleriniz, [SharePoint Online'da olduğu gibi SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) sertifikalarını otomatik olarak kullanmaz.|
|SharePoint Server şirket içinde adlandırma kuralları, yedekleme, geri yükleme ve diğer kurtarma seçenekleri üzerinde tam denetim.|SharePoint Server şirket içi, ürün yaşam döngüleri için çok duyarlıdır.|

### <a name="upgrade-resources"></a>Kaynakları yükseltme

Başlangıç olarak donanım ve yazılım gereksinimlerini karşılasmanızı ve desteklenen yükseltme yöntemlerini takip edin.

- *Donanım/yazılım gereksinimleri*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Yazılım sınırları ve sınırlamaları*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Yükseltme sürecine genel bakış*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>SharePoint Online SharePoint şirket içi arasında karma bir çözüm oluşturma

Geçiş ihtiyaçlarının yanıtı şirket içi tarafından sunulan denetimle SharePoint Online'ın sunduğu düşük sahip olma maliyeti arasında bir yerde yer alıyorsa, karmalar aracılığıyla SharePoint Server 2013 veya 2016 sunucu gruplarınızı SharePoint Online'a bağlanabilirsiniz. [Karma çözümler SharePoint öğrenin](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Karma bir SharePoint Server sunucu sunucusunun işletmenize yararına olduğuna karar verirsiniz, var olan karma türleri öğrenin ve şirket içi SharePoint sunucu grubuyla Microsoft 365 aboneliğiniz arasındaki bağlantıyı nasıl yapılandırın.

Test Laboratuvarı Kılavuzları ile Microsoft 365 bir geliştirme/test ortamı [oluşturabilirsiniz](m365-enterprise-test-lab-guides.md). Deneme veya satın alınan bir Microsoft 365 sonra, SharePoint Online'da verileri geçirebilirsiniz ve site koleksiyonları, web'ler ve belge kitaplıkları oluşturabilirsiniz. Geçiş API'sini kullanarak el ile veya Sitem içeriğini karma sihirbazı aracılığıyla OneDrive İş'e geçirebilirsiniz.

> [!NOTE]
> Karma seçeneği kullanmak için, SharePoint Server 2010 sunucu grubu önce şirket içi sürümü SharePoint Server 2013 veya 2016'ya yükseltilsin. SharePoint Foundation 2010 ve SharePoint Foundation 2013, SharePoint Online ile karma bağlantıları desteklemez.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 istemci ve sunucuları ile 7. Windows özeti

Office 2010 istemcileri ve sunucuları ve Windows 7 için yükseltme, geçirme ve buluta taşıma seçeneklerinin görsel bir özeti için destek [posteri](../downloads/Office2010Windows7EndOfSupport.pdf) sonuna bakın.

[![Office 2010 istemcileri ve sunucuları ve Posta 7 posteri için Windows sonu.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Bu posterde, Office 2010 istemci ve sunucu ürünlerinden kaçınmak için atılması gereken çeşitli yollar ve Windows 7 destek sonu vurgulanmış, tercih edilen yollar ve seçenek Microsoft 365 Kurumsal vurgulanır.

Ayrıca bu [posteri](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) indirip letter, legal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

[Office 2007 veya 2010 sunucularından ve istemcilerinden yükseltmeye yardımcı olacak kaynaklar](upgrade-from-office-2010-servers-and-products.md)

[SharePoint 2010'dan 2013'e yükseltme SharePoint genel bakış](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[SharePoint 2010'dan 2013'e yükseltme SharePoint yöntemleri](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[SharePoint 2013'te veritabanı yükseltme sorunlarını giderme](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Yükseltmenize yardımcı olmak için Microsoft çözüm sağlayıcılarını arama](https://go.microsoft.com/fwlink/?linkid=841249)

[SharePoint 2013 için Güncelleştirilmiş Ürün Hizmet İlkesi](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[SharePoint Server 2016 için Güncelleştirilmiş Ürün Hizmet İlkesi](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
