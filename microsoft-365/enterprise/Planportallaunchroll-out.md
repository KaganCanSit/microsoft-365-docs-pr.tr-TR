---
title: SharePoint Online'da portal lansman planınızı planlama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Bu makalede, SharePoint Online'da portal lansmanını nasıl planlayabilirsiniz ve başarılı bir lansman için atılacak adımlar açıklanmıştır.
ms.openlocfilehash: 064870dd2748c6e936b12c2f333ab1d873b572cd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985357"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>SharePoint Online'da portal lansman planınızı planlama

Portal, intranet SharePoint site üzerinde içerik tüketen birçok site görüntüleyicisi bulunan bir sitedir. Büyük kuruluşların çeşitli portalları olabilir. Örneğin, bir şirket portalı ve İk portalı. Portallarda genellikle, siteyi ve içeriğini oluşturan ve yazan oldukça az kişi vardır. Portalın çoğu ziyaretçi yalnızca içeriği okur ve tüketir.

Bu makalede, SharePoint Online için dağıtım ve dağıtım planınızı planlama açıklanmıştır. Ayrıca, SharePoint Online'da geleneksel yükleme testine izin verilmedi şeklinde takip etmeye SharePoint sağlar. SharePoint Online bir bulut hizmetidir ve hizmet üzerindeki yükleme özellikleri, durumu ve genel yük dengesi Microsoft tarafından yönetilir.

Başarılı bir portal oluşturma konusunda yardımcı olması için, sağlıklı bir portalı oluşturma, başlatma ve koruma konusunda ayrıntılı olarak bilgi edinen temel ilkelere [, uygulamalara ve önerilere uyma](/sharepoint/portal-health) 

Dağıtım yaklaşımı aşağıda vurgulanmıştır.

## <a name="portal-launch-scheduler"></a>Portal Başlatma Zamanlayıcı

Portalınızı, zamanlanmış aşamalar içinde kuruluşta yer alan kullanıcılara bırakmak için portal başlatma zamanlayıcısını kullanın. Daha fazla bilgi edinin: 

![Takvim](https://docs.microsoft.com/Office/media/icons/calendar.png "Portal başlatma zamanlayıcısı") [simgesiPortal Launch Scheduler](https://docs.microsoft.com/microsoft-365/enterprise/portallaunchscheduler)  



## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>SharePoint Online'da kapasite planlamasına genel bakış
Herhangi bir grupta kapasiteyi verimli bir şekilde kullanmak ve beklenmedik büyümeyle başa çık sağlamak için, bazı kullanım senaryolarını takipen otomasyonu kullanıruz. Tek bir grup içinde herhangi bir kiracı için tam büyüme öngörülemezken, toplam istek toplamı zamanla öngörülebilir olur. SharePoint Online'da büyüme eğilimlerini tanımarak, gelecekteki genişletmeyi planlayacağız. SharePoint [Online'da Kapasite planlaması ve yükleme testi hakkında daha SharePoint için.](capacity-planning-and-load-testing-sharepoint-online.md)

Başarılı bir başlatmanın önemli bir parçası aşağıda ayrıntılı olarak "dalga" veya "aşamalı uygulama" yaklaşımıdır. 

## <a name="can-i-load-test-sharepoint-online"></a>Test yükleme testini SharePoint Online'a SharePoint?
SharePoint Online, gruplarda ve ölçek genelinde dengeli olarak ayarlanmış, çok kiracılı paylaşılan bir ortamdır. SharePoint Online gibi bir ortamın, ölçeği sürekli olarak değiştiklerinde size beklenmedik sonuçlar vermekle birlikte bu sonuçlara izin verilmez. 

Daha fazla bilgi: [SharePoint Online'da kapasite planlaması ve yükleme testi](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Önerilen yönergeleri takip edin ve sayfaları en iyi duruma getirme
Şirket içi dağıtımdan gelen sayfalar, önerilen SharePoint SharePoint Online yönergelerine göre gözden geçirimeden yalnızca SharePoint Online'a taşınmalıdır. En iyi yaklaşım, herhangi bir giriş sayfasını SharePoint'ta herhangi bir site veya portal için her zaman en iyi duruma getirmektir çünkü burada, organizasyonu kullanan çoğu kullanıcı siteniz veya kullanıcılarınız için başlangıç noktası olarak erişecek.

Birkaç temel faktör dikkate alınmalıdır:
- Şirket içi dağıtımlarda nesne önbelleği, çıkış önbelleği ve blob önbelleği gibi geleneksel sunucu tarafı önbellekleri kullanılabilir. Buluttaki topoloji farklılıklarıyla, ölçek farklılıkları daha az uygulanabilir yaklaşımlar olarak bu seçeneklerin kullanılabilir olması gerekmez.
- Bulut tüketimi için kullanılan tüm sayfalar / özellikler / özelleştirmeler daha yüksek gecikme süresi ve kullanıcıların dağıtılmış konumları için en iyi duruma getirilmiş olmalıdır, böylece farklı alanlardaki veya bölgelerdeki kullanıcılar daha tutarlı bir deneyime sahip olur. Bulut, dağıtılmış bir kullanıcı tabanı için iyileştirme yapmak üzere İçerik Teslim Ağları (CDN) gibi iyileştirmeler sunar ve modern SharePoint için, bilinen en son iyi (LKG) en son hazır web bölümlerimiz (OOTB) tarafından kullanılır.

### <a name="what-to-do"></a>Ne yapmak gerek?
 - SharePoint Online'daki tüm site [sayfalarında, çözümleme](./page-diagnostics-for-spo.md) ve rehberlik sağlama konusunda yardımcı Chromium bir uzantı olan Sayfa Tanılama aracını kullanın. Bu, çözümleme ve iyileştirme için başlangıç noktası olacak şekilde tasarlanarak site sahipleri, düzenleyiciler, yöneticiler ve geliştiriciler tarafından kullanılabilir.
 - Geliştiriciler ayrıca modern sayfalarda F12 tarayıcı geliştirici aracı ve CTRL-F12 gibi geliştirme araçlarını tarayıcıda kullanmaları gerekir. [Fiddler](https://www.telerik.com/download/fiddler) ayrıca sayfanın boyutunu (sayfanın megabayt cinsinden ne kadar büyük olduğunu) ve genel sayfa yükünü etkileyen aramaların ve öğelerin sayısını gözden geçirmek için de kullanılabilir. 

Bu bölüm sayfaları en iyi duruma getirmeyle ilgili kısa bir özetdi.  Daha fazla bilgi edinmek için bkz:  [Sağlıklı bir portalı oluşturma, başlatma ve koruma](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Bir Dalgayı Takip Etme / Aşamalı roll-out yaklaşımı
Site başlatmaları için geleneksel büyük bağlantı yaklaşımı, özelleştirmelerin, dış kaynakların, hizmetlerin veya işlemlerin doğru ölçekte test edilmiş olduğunu doğrulamaya izin vermez. Bu yaklaşım, başlatılmasının ayları alacak olduğu anlamına gelir, ancak kuruluş boyutuna bağlı olarak en az birkaç gün boyunca kullanılması önerilir. Dolayısıyla bir dalga uygulama planının takip etmek, sonraki aşamayla devam etmeden önce sorunları duraklatma ve çözme seçeneği sağlar ve dolayısıyla herhangi bir sorundan etkilenmesi olası kullanıcı sayısını düşürer. SharePoint olarak, kapasitenizi kullanım ve öngörülen kullanım ve kullanım ölçeğine göre ölçeklendiren hizmet olarak, başlatmanızı bize bildirmenize gerek yok, ancak başarılı olmak için yönergeleri takip edin.
  
Aşağıdaki resimde de gösterildiği gibi, çoğu zaman davet edilen kullanıcı sayısı siteyi gerçekten kullananlardan çok daha yüksektir. Bu resimde, bir sürümün nasıl piyasaya çıkarıla ilgili bir strateji olduğu görüntüdedir. Bu yöntem, siteyi çoğu kullanıcı SharePoint daha önce geliştirmenin yollarını belirlemeye yardımcı olur.
  
![Graph ve etkin kullanıcıları gösteren bir bağlantı.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Pilot aşamasında, kuruluşun güvendi ve ne zaman meşgul olacağını bilen kullanıcılardan geri bildirim almak iyi bir fikirdir. Bu şekilde, sistemin nasıl ve nasıl bir performansta olduğunu ölçmek mümkündür.
  
Dalgalardan her biri sırasında, dağıtım dalgalarının her biri sırasında özellikler ve performansla ilgili kullanıcı geri bildirimlerini toplayın. Geri bildirim toplama, sistemin yavaşça tanıtımını yapma ve sistem daha fazla kullanım elde ettiyken geliştirmeler yapma avantajına sahiptir. Bu aynı zamanda, site daha fazla kullanıcıya sunarken artan yüke tepki vermemizi sağlar ve sayfa iyileştirme yönergelerini takip etmek kullanıcılarınızı açısından olumlu bir deneyim sağlar.

### <a name="what-to-do"></a>Ne yapmak gerek?
- Her aşamanın zamanlamasını karar verin ve devam etmeden önce ayarlamalar yapmak zorunda bekleme / duraklatma fırsatınız olduğundan emin olmak
- İleride ilerlemeniz gereken geri bildirimleri almak için etkinleştirmek istediğiniz ilk kullanıcı grubunu planla.  Mümkünse, zamanında geri bildirim sağlayacak etkin bir kullanıcı grubu seçin
- Her dalgayı planken, küçük bir kullanıcı tabanıyla (5000 kullanıcıdan az) başlamayı deneyin. Her dalgayla devam ettiyseniz grup boyutlarını artırma. Basamaklı bir yaklaşım oluşturarak, gerektiğinde fırsatları daha kolay duraklatma imkanı sağlar.