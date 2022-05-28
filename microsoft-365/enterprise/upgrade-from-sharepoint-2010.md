---
title: SharePoint 2010'dan yükseltme
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: SharePoint 2010 ve SharePoint Server 2010'dan yükseltecek bilgileri ve kaynakları bulun. Her iki destek de 13 Nisan 2021'de sona erer.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4ed6cf873442d4fd48cdbf9562e6067fd238384e
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772762"
---
# <a name="upgrading-from-sharepoint-2010"></a>SharePoint 2010'dan yükseltme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft SharePoint 2010 ve SharePoint Server 2010 **, 13 Nisan 2021'de** destek sonuna ulaşacaktır. Bu makale, mevcut SharePoint Server 2010 verilerinizi Microsoft 365'da SharePoint Online'a geçirmenize veya şirket içi SharePoint Server 2010 ortamınızı yükseltmenize yardımcı olacak kaynaklar sağlar.

## <a name="what-is-end-of-support"></a>*Destek sonu* nedir?

Microsoft ürünlerinin çoğu, yeni özellikler, hata düzeltmeleri, güvenlik düzeltmeleri vb. alan bir destek yaşam döngüsüne sahiptir. Destek sonu tarihinden sonra ürün çalışmayı durdurmaz, ancak Microsoft artık şunları sağlamaz:

- Oluşabilecek sorunlar için teknik destek.

- Sunucunun kararlılığını ve kullanılabilirliğini etkileyebilecek sorunlar için hata düzeltmeleri.

- Sunucuyu güvenlik ihlallerine açık hale getirebilecek güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Bu, ürün için başka güncelleştirme, düzeltme eki veya düzeltme olmayacağı anlamına gelir (güvenlik düzeltme ekleri/düzeltmeler dahil). Microsoft Desteği destek çalışmalarını daha yeni sürümlere tamamen kaydırmış olacak.

SharePoint Server 2010 desteği sona ererken, ürünü yükseltmeden ve önemli verilerinizi geçirmeden önce artık ihtiyacınız olmayan verileri silin.

> [!NOTE]
> Yazılım yaşam döngüsü genellikle ilk sürümden itibaren on yıl sürer. [Microsoft çözüm sağlayıcıları](https://go.microsoft.com/fwlink/?linkid=841249), yazılımın sonraki sürümüne yükseltmenize veya Microsoft 365 geçişe (veya her ikisine) geçmenize yardımcı olabilir. Özellikle de SharePoint ile kullandığınız Microsoft SQL Server sürümü için kritik temel teknolojiler için destek sonu tarihlerini bildiğinizden emin olun. Daha fazla bilgi için bkz [. Sabit Yaşam Döngüsü İlkesi](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Önceden planlayın

[Ürün Yaşam Döngüsü sitesinde](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) desteğin sona erdiğini gösteren tarihleri denetleyin. Bu tarihleri göz önünde bulundurarak yükseltmelerinizi veya geçişlerinizi planlayın. Ürününüzün listelenen tarihte *çalışmayı durdurmayacağını* unutmayın. Ancak bu tarihten sonra yüklemenize artık düzeltme eki uygulanmayacağından ürünün sonraki sürümüne sorunsuz bir geçiş planlamak istersiniz.

Bu matris, geçiş seçenekleri arasında bir kurs çizmeye yardımcı olur:

|Destek sonu ürünü|Iyi |En iyi|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (şirket içi)|SharePoint Online|
||SharePoint Online ile SharePoint Server 2013 karma|SharePoint Server 2016 (şirket içi)|
|||bulut karma arama SharePoint|

Ölçeğin düşük ucunda (iyi) bir seçenek belirlerseniz, SharePoint Server 2010'dan geçişinizden kısa süre sonra başka bir yükseltme planlamaya başlamanız gerekir.

SharePoint Server 2010 desteğinin sona ermesini önlemek için izleyebileceğiniz üç yol aşağıdadır.

![SharePoint Server 2010 yükseltme yolları.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> SharePoint Server 2010 ve SharePoint Foundation 2010 desteğinin sona ermesi şu anda 13 Nisan 2021'de zamanlanmıştır. Ancak en güncel tarihler için [Ürün Yaşam Döngüsü sitesini](https://support.microsoft.com/lifecycle) kontrol edin.

## <a name="whats-next"></a>Sırada ne var?

SharePoint Server 2013 ve SharePoint Foundation 2013 kendi sunucularınıza şirket içinde yüklenebilir. Microsoft 365 bir parçası olan çevrimiçi bir hizmet olan SharePoint Online'ı da kullanabilirsiniz. Şunu seçebilirsiniz:

- SharePoint Online'a geçiş.

- şirket içi SharePoint Server veya SharePoint Foundation'a yükseltin.

- Yukarıdakilerin ikisini de yapın.

- [SharePoint bir karma](/sharepoint/hybrid/hybrid) çözüm uygulayın.

Özelleştirmeleri korumak veya geçirmek ve donanımı yükseltmek de dahil olmak üzere bir sunucu grubunun bakımının gizli maliyetlerini göz önünde bulundurun. Bu faktörleri dikkate aldıysanız şirket içinde yükseltme yapmak daha kolay olacaktır. Grubunuzu ağır özelleştirme olmadan eski SharePoint Sunucularında çalıştırıyorsanız, SharePoint Online'a planlı geçişten yararlanabilirsiniz. Şirket içi SharePoint Sunucusu ortamında, donanım yönetimi ek yükünü azaltmak için SharePoint Online'da bazı verileri taşımayı da düşünebilirsiniz.

> [!NOTE]
> SharePoint yöneticileri bir Microsoft 365 Aboneliği oluşturabilir, yeni SharePoint Çevrimiçi siteleri ayarlayabilir ve ardından yeni sitelere yalnızca temel belgeleri alarak SharePoint Server 2010'dan temiz bir şekilde kesebilir. Ardından, kalan tüm veriler SharePoint Server 2010 sitesinden şirket içi arşivlere boşaltılabilir.

|SharePoint Online|şirket içi SharePoint Sunucusu|
|---|---|
|Zaman içinde yüksek maliyet (plan/yürütme/doğrulama)|Zaman içinde yüksek maliyet (plan/yürütme/doğrulama)|
|Fonlarda daha düşük maliyet (donanım satın alma işlemi yapılmaz)|Fonlarda daha yüksek maliyet (donanım satın almaları)|
|Geçişte tek seferlik maliyet|Gelecekteki geçiş başına tek seferlik maliyet yinelenir|
|Düşük toplam sahip olma/bakım maliyeti|Yüksek toplam sahip olma/bakım maliyeti|

Verileri düzenlerken ve buluta nelerin alınacağını ve nelerin geride bırakılacağına karar verirken, Microsoft 365 tek seferlik bir taşımanın maliyeti daha yüksek olacaktır. Ancak verileriniz geçirildikten sonra, donanım ve yazılım güncelleştirmelerini yönetmenize gerek kalmayacağı için gelecekteki yükseltmeler otomatik olarak gerçekleştirilir. Ayrıca, grubunuzun çalışma süresi bir [Microsoft hizmet düzeyi sözleşmesi (SLA)](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) tarafından yedeklenir.

### <a name="migrate-to-sharepoint-online"></a>SharePoint Online'a geçiş

SharePoint Online'ın ihtiyacınız olan tüm özellikleri sunduğundan emin olun. [Hizmet açıklaması SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) bakın.

doğrudan SharePoint Server 2010'dan (veya SharePoint Foundation 2010'dan) SharePoint Online'a geçiş yapamazsınız. Geçiş çalışmalarının çoğu el ile gerçekleştirilir. Ancak bu aşama, taşıma işleminden önce artık gerekli olmayan verileri ve siteleri ayıklama fırsatı sunar. Diğer verileri depolama alanına arşivleyebilirsiniz. 

SharePoint Server 2010 ve SharePoint Foundation 2010'un destek sonunda çalışmayı durdurmayacağını unutmayın. Böylece yöneticilerin, müşterilerinin verilerinin bir kısmını taşımayı unutması durumunda SharePoint hala çalıştığı bir dönem olabilir.

SharePoint Server 2013 veya SharePoint Server 2016'ya yükseltip verileri SharePoint Online'a yerleştirmeye karar verirseniz, [bilgileri OneDrive İş geçirmek için SharePoint Geçiş API'sini](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) kullanabilirsiniz.

|SharePoint Online avantajı|SharePoint Online dezavantajı|
|---|---|
|Microsoft, SPO donanımlarını ve tüm donanım yönetimini sağlar.|Kullanılabilir özellikler şirket içi SharePoint Sunucusu ile SPO arasında farklılık gösterebilir.|
|Aboneliğinizin SharePoint yöneticisi veya genel yöneticisisiniz ve SPO sitelerine yönetici atayabilirsiniz.|şirket içi SharePoint Sunucusu'ndaki bir grup yöneticisinin kullanabileceği bazı eylemler, Microsoft 365'daki SharePoint Yöneticisi rolünde yoktur (veya gerekli değildir). Ancak SharePoint Yönetimi, Site Koleksiyonu Yönetimi ve Site Sahipliği kuruluşunuzda yereldir.|
|Microsoft, SharePoint Online'ın çalıştığı SQL sunucuları da dahil olmak üzere temel donanım ve yazılımlara düzeltme ekleri, düzeltmeler ve güncelleştirmeler uygular.|Hizmette temel alınan dosya sistemine erişim olmadığından özelleştirme sınırlıdır.|
|Microsoft [, hizmet düzeyi sözleşmeleri yayımlar](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) ve hizmet düzeyi olaylarını çözmek için hızlı bir şekilde taşınır.|Yedekleme ve geri yükleme ile diğer kurtarma seçenekleri SharePoint Online'da hizmet tarafından otomatik hale getirilir. Kullanılmıyorsa yedeklemelerin üzerine yazılır.|
|Güvenlik testi ve sunucu performansı ayarlama, Microsoft tarafından hizmette sürekli olarak gerçekleştirilir.|Kullanıcı arabiriminde ve diğer SharePoint özelliklerinde yapılan değişiklikler hizmet tarafından yüklenir ve açık veya kapalı olması gerekebilir.|
|Microsoft 365 birçok endüstri standardına uygundur: [Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home).|[Geçiş için FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) yardımı sınırlıdır.  <br/> Yükseltmenin büyük bir kısmını el ile veya [SharePoint Online ve OneDrive Geçiş İçeriği Yol Haritası'nda](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets) açıklanan SPO Geçiş API'sini kullanarak yapacaktır.|
|Microsoft Desteği mühendislerin ve veri merkezi çalışanlarının aboneliğinize sınırsız yönetici erişimi yoktur.|Donanım altyapısının daha yeni bir SharePoint sürümünü destekleyecek şekilde yükseltilmesi gerekiyorsa veya yükseltme için ikincil bir grup gerekiyorsa ek maliyetler olabilir.|
|Çözüm sağlayıcıları, verilerinizi SharePoint Online'a tek seferlik geçirme konusunda yardımcı olabilir.|SharePoint Online'da yapılan tüm değişiklikler sizin denetiminizde değildir. Geçiş sonrasında menüler, kitaplıklar ve diğer özelliklerdeki tasarım farklılıkları geçici olarak kullanılabilirliği etkileyebilir.|
|Çevrimiçi ürünler hizmet genelinde otomatik olarak güncelleştirilir. Özellikler kullanımdan kaldırılabilir, ancak destek yaşam döngüsünün gerçek sonu yoktur.|SharePoint Server veya SharePoint Foundation'ın yanı sıra temel SQL sunucuları için destek sonu yaşam döngüsü vardır.|

Yeni bir Microsoft 365 sitesi oluşturmaya karar verdiyseniz ve gerektiğinde verileri bu siteye el ile geçirirseniz [Microsoft 365 seçeneklerinizi](https://www.microsoft.com/microsoft-365/) denetleyin.

### <a name="upgrade-sharepoint-server-on-premises"></a>Şirket içi SharePoint Sunucusu'nu yükseltme

SharePoint Server 2019 itibarıyla yükseltmelerin *seri olarak* gitmesi gerekir. SharePoint Server 2010'dan SharePoint Server 2016'ya veya doğrudan SharePoint 2019'a yükseltmenin hiçbir yolu yoktur. Seri yükseltme yolu:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

SharePoint 2010'dan SharePoint Server 2016'ya kadar tüm yolu izlemek zaman alır ve planlama gerektirir. Yükseltmeler donanım (SQL sunucuların da yükseltilmesi gerekir), yazılım ve yönetim maliyetlerini içerir. Ayrıca özelleştirmelerin yükseltilmesi ve hatta terk edilmesi gerekebilir. SharePoint Server grubunuzu yükseltmeden önce kritik özelleştirmeleri belgelediğinizden emin olun.

> [!NOTE]
> Destek sonu SharePoint 2010 grubunuzun bakımını yapmak, yeni donanıma bir SharePoint Server 2016 grubu yüklemek (böylece ayrı gruplarda yan yana çalışmak) ve ardından el ile içerik geçişi planlamak ve yürütmek mümkündür (örneğin, içeriği indirmek ve yeniden yüklemek için). Ancak, 2010'dan gelen belgelerin, el ile taşımayı gerçekleştiren hesabın diğer adıyla geçerli bir son değiştirilmiş hesaba sahip olması gibi bu el ile yapılan taşımalarda olası tuzaklar vardır. Ayrıca siteleri, alt siteleri, izinleri ve liste yapılarını yeniden oluşturma gibi bazı işlerin önceden yapılması gerekir. Yükseltmeden önce ortamınızı temizlemeyi unutmayın. Depolama alanına taşıyabileceğiniz veya artık gerek duymadığınız verileri göz önünde bulundurun. Bu, geçişin etkisini azaltabilir. Yükseltmeden önce mevcut grubunuzun işlevsel olduğundan emin olun ve (kesinlikle) yetkisini almadan önce!

*Desteklenen ve desteklenmeyen yükseltme yollarını* gözden geçirmeyi unutmayın:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

*Özelleştirmeleriniz* varsa, geçiş yolundaki her adım için planlamanız önemlidir:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Şirket içi avantaj|Şirket içi dezavantajı|
|---|---|
|sunucu donanımından SharePoint Grubunuzun (ve SQL) tüm yönleriyle tam denetim.|Tüm kesmeler ve düzeltmeler şirketinizin sorumluluğundadır. Ancak ürününüz destek sonunu aşmadıysa ücretli Microsoft Desteği devreye girebilirsiniz.|
|Şirket içi grubunuzu karma aracılığıyla bir SharePoint Online aboneliğine bağlama seçeneğiyle şirket içi SharePoint Server'ın tam özellik kümesi.|Yükseltme, düzeltme ekleri, güvenlik düzeltmeleri, donanım yükseltmeleri ve SharePoint Sunucusu ile SQL grubunun tüm bakımları şirket içinde yönetilir.|
|SharePoint Online'dan daha fazla özelleştirme seçeneği için tam erişim.|[Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home) şirket içinde el ile yapılandırılmalıdır.|
|Güvenlik testi ve sunucu performansı ayarlama işlemleri, sizin denetiminizde şirket içinde gerçekleştirilir.|Microsoft 365, SharePoint Online'da şirket içi SharePoint Server ile birlikte çalışmamayan özellikleri kullanıma sunabilir.|
|Çözüm sağlayıcıları, verileri SharePoint Sunucusu'nun sonraki sürümüne (ve ötesine) geçirmeye yardımcı olabilir.|SharePoint Server siteleriniz, SharePoint Online'da görüldüğü gibi ssl[/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) sertifikalarını otomatik olarak kullanmaz.|
|SharePoint Server şirket içinde adlandırma kuralları, yedekleme ve geri yükleme ile diğer kurtarma seçenekleri üzerinde tam denetim.|SharePoint Server şirket içi, ürün yaşam döngülerine duyarlıdır.|

### <a name="upgrade-resources"></a>Kaynakları yükseltme

Donanım ve yazılım gereksinimlerini karşılaştırarak başlayın. Geçerli ortamınız temel gereksinimleri karşılamıyorsa, önce gruptaki donanımı veya SQL sunucularını yükseltmeniz gerekebilir. 

Bazı sitelerinizi SharePoint Online'ın "yeşil" donanımına taşımaya karar vekleyebilirsiniz. Değerlendirmenizi yaptıktan sonra desteklenen yükseltme yollarını ve yöntemlerini izleyin.

- *Donanım/yazılım gereksinimleri:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Yazılım sınırları ve sınırları:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Yükseltme işlemine genel bakış:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>şirket içi SharePoint Online ve SharePoint Server ile karma çözüm oluşturma

Karma kurulum, bazı geçiş gereksinimleri için hem şirket içi hem de çevrimiçi olarak en iyi şekilde kullanılabilir. SharePoint karma oluşturmak için SharePoint Server 2013, 2016 veya 2019 gruplarını SharePoint Online'a [bağlayabilirsiniz: Karma çözümleri SharePoint hakkında bilgi edinin](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Geçiş hedefiniz karma SharePoint Sunucusu grubuysa, hangi sitelerin ve kullanıcıların çevrimiçi taşınacaklarını ve hangilerinin şirket içinde kalması gerektiğini belirleyin. SharePoint Sunucusu grubu içeriğinizi şirketinize yüksek, orta veya düşük etki olarak derecelendirmek bu kararda yardımcı olabilir. Yalnızca oturum açma için kullanıcı hesaplarını ve SharePoint Sunucusu arama dizinini SharePoint Online ile paylaşmanız gerekebilir. Ancak sitelerinizin nasıl kullanıldığına bakıncaya kadar bu faktör net olmayabilir. Şirketiniz daha sonra tüm içeriğinizi SharePoint Online'a geçirmeye karar verirse kalan tüm hesapları ve verileri çevrimiçi olarak taşıyabilir ve şirket içi grubunuzun yetkisini alabilirsiniz. SharePoint grubunun yönetimi/yönetimi bu noktadan itibaren Microsoft 365 konsollar aracılığıyla yapılır.

Mevcut karma türlerini ve şirket içi SharePoint grubunuzla Microsoft 365 aboneliğiniz arasındaki bağlantıyı yapılandırmayı bildiğinizden emin olun.

|Seçeneği|Açıklama|
|---|---|
|[Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home).|[Geçiş için FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) yardımı sınırlıdır.<br/><br/> Yükseltmenin büyük bir kısmını el ile veya [SharePoint Online ve OneDrive Geçiş İçeriği Yol Haritası'nda](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets) açıklanan SPO Geçiş API'sini kullanarak yapacaktır.|
|Microsoft Desteği mühendislerin ve veri merkezi çalışanlarının aboneliğinize sınırsız yönetici erişimi yoktur.|Donanım altyapısının daha yeni SharePoint sürümünü destekleyecek şekilde yükseltilmesi gerekiyorsa veya ikincil bir grup gerekiyorsa ek maliyetler olabilir.|
|İş ortakları, verilerinizi SharePoint Online'a tek seferlik geçirme konusunda yardımcı olabilir.||
|Çevrimiçi ürünler hizmet genelinde otomatik olarak güncelleştirilir. Özellikler kullanımdan kaldırılabilir, ancak gerçek destek sonu yoktur.||

Yeni bir Microsoft 365 sitesi oluşturmaya ve gerektiğinde verileri bu siteye el ile geçirmeye karar verdiyseniz[, Microsoft 365 seçeneklerinizi](https://www.microsoft.com/microsoft-365/) denetleyin.

### <a name="upgrade-sharepoint-server-on-premises"></a>Şirket içi SharePoint Sunucusu'nu yükseltme

SharePoint Yükseltmeleri'nde sürümleri atlamanın hiçbir yolu yoktur. Bu, yükseltmelerin seri olarak gittiği anlamına gelir:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

SharePoint 2007'den SharePoint Server 2016'ya kadar tüm yolu almak, önemli bir zaman yatırımı anlamına gelir ve donanım (SQL sunucuların da yükseltilmesi gerekir), yazılım ve yönetim maliyetlerini içerir. Özelleştirmelerin, özelliğin kritikliğine göre yükseltilmesi veya terk edilmesi gerekir.

> [!NOTE]
> Kullanım süresi sonu SharePoint 2007 grubunuzun bakımını yapmak, yeni donanıma bir SharePoint Server 2016 grubu yüklemek (böylece ayrı gruplarda yan yana çalışmak) ve ardından el ile içerik geçişi planlamak ve yürütmek mümkündür (örneğin, içeriği indirmek ve yeniden yüklemek için). Ancak bu el ile yapılan taşımaların bazı dezavantajları vardır, örneğin belgelerin son değiştirilen hesabı el ile taşımayı gerçekleştiren hesabın diğer adıyla değiştirmesi. Ayrıca siteleri, alt siteleri, izinleri ve liste yapılarını yeniden oluşturma gibi çok fazla iş önceden yapılmalıdır. Her durumda, hangi verileri depolama alanına taşıyabileceğinizi veya geçişin etkisini azaltmanız gerekmeyen verileri göz önünde bulundurun.

Yükseltmeden önce ortamınızı temizlediğinden emin olun. Yükseltmeden önce mevcut grubunuzun işlevsel olduğundan emin olun ve kesinlikle yetkisini almadan önce!

*Desteklenen ve desteklenmeyen yükseltme yollarını* gözden geçirmeyi unutmayın:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

*Özelleştirmeleriniz* varsa, geçiş yolundaki her adım için yükseltmenizi planlamak önemlidir:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Şirket içi profesyonel|Şirket içi con|
|---|---|
|Sunucu donanımından SharePoint Grubunuzun tüm yönleriyle tam denetim.|Tüm kesmeler ve düzeltmeler şirketinizin sorumluluğundadır. (Ancak ürününüz destek sonunu geçmezse ücretli Microsoft Desteği etkileşim kurabilirsiniz.)|
|Şirket içi grubunuzu karma aracılığıyla bir SharePoint Online aboneliğine bağlama seçeneğiyle şirket içi SharePoint Server'ın tam özellik kümesi.|Yükseltme, düzeltme ekleri, güvenlik düzeltmeleri ve şirket içinde yönetilen SharePoint Sunucusu'nun tüm bakımları.|
|Daha fazla özelleştirme için tam erişim.|[Microsoft uyumluluk teklifleri](/compliance/regulatory/offering-home) şirket içinde el ile yapılandırılmalıdır.|
|Güvenlik testi ve sunucu performansı ayarlama işlemleri, sizin denetiminizde şirket içinde gerçekleştirilir.|Microsoft 365, SharePoint Online'da şirket içi SharePoint Server ile birlikte çalışmamayan özellikleri kullanıma sunabilir.|
|İş ortakları, verileri SharePoint Sunucusu'nun sonraki sürümüne (ve ötesine) geçirmeye yardımcı olabilir.|SharePoint Server siteleriniz, SharePoint Online'da görüldüğü gibi ssl[/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) sertifikalarını otomatik olarak kullanmaz.|
|SharePoint Server şirket içinde adlandırma kuralları, yedekleme ve geri yükleme ile diğer kurtarma seçenekleri üzerinde tam denetim.|SharePoint Server şirket içi, ürün yaşam döngülerine duyarlıdır.|

### <a name="upgrade-resources"></a>Kaynakları yükseltme

Donanım ve yazılım gereksinimlerini karşıladığınızdan emin olarak başlayın, ardından desteklenen yükseltme yöntemlerini izleyin.

- *Donanım/yazılım gereksinimleri*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Yazılım sınırları ve sınırları*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Yükseltme işlemine genel bakış*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>SharePoint Online ile şirket içi arasında SharePoint karma çözüm oluşturma

Geçiş gereksinimlerinizin yanıtı şirket içinde sunulan denetimle SharePoint Online tarafından sunulan daha düşük sahip olma maliyeti arasında bir yerdeyse, SharePoint Server 2013 veya 2016 gruplarını karmalar aracılığıyla SharePoint Online'a bağlayabilirsiniz. [Karma çözümleri SharePoint hakkında bilgi edinin](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Karma SharePoint Sunucu grubunun işletmenize fayda sağlayacağına karar verirseniz, mevcut karma türleri ve şirket içi SharePoint grubunuzla Microsoft 365 aboneliğiniz arasındaki bağlantıyı yapılandırma hakkında bilgi edinin.

[Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md) ile ayarlayabileceğiniz bir Microsoft 365 geliştirme/test ortamı oluşturmak isteyebilirsiniz. Deneme sürümünü aldıktan veya Microsoft 365 aboneliği satın aldıktan sonra, SharePoint Online'da verileri geçirebileceğiniz site koleksiyonları, web'ler ve belge kitaplıkları oluşturabilirsiniz. Geçiş API'sini kullanarak veya Sitem içeriğini karma sihirbaz aracılığıyla OneDrive İş geçirmek istiyorsanız el ile geçirebilirsiniz.

> [!NOTE]
> Karma seçeneği kullanmak için, SharePoint Server 2010 grubunuzun önce şirket içi SharePoint Server 2013 veya 2016'ya yükseltilmesi gerekir. SharePoint Foundation 2010 ve SharePoint Foundation 2013, SharePoint Online ile karma bağlantıları desteklemez.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 istemci ve sunucuları ile Windows 7 seçeneklerinin özeti

Office 2010 istemcileri ve sunucuları ile Windows 7 için yükseltme, geçiş ve buluta taşıma seçeneklerinin görsel bir özeti için [destek sonu posterine](../downloads/Office2010Windows7EndOfSupport.pdf) bakın.

[![Office 2010 istemcileri ve sunucuları ile Windows 7 posteri için destek sonu.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Bu posterde, Office 2010 istemci ve sunucu ürünlerinden kaçınmak için izleyebileceğiniz çeşitli yollar ve tercih edilen yollar ve Microsoft 365 Kurumsal'deki seçenek desteklerinin vurgulandığı Windows 7 destek sonu gösterilmektedir.

Ayrıca bu posteri [indirebilir](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) ve mektup, yasal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

[Office 2007 veya 2010 sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2010-servers-and-products.md)

[SharePoint 2010'dan SharePoint 2013'e yükseltme işlemine genel bakış](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[SharePoint 2010'dan SharePoint 2013'e yükseltmek için en iyi yöntemler](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[SharePoint 2013'te veritabanı yükseltme sorunlarını giderme](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Yükseltmenize yardımcı olması için Microsoft çözüm sağlayıcılarını arayın](https://go.microsoft.com/fwlink/?linkid=841249)

[SharePoint 2013 için Güncelleştirilmiş Ürün Bakım İlkesi](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[SharePoint Server 2016 için Güncelleştirilmiş Ürün Bakım İlkesi](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
