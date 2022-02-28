---
title: SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online modern site sayfalarında web bölümlerinin performansını iyileştirmek için Sayfa Tanılama'yı kullanmayı öğrenin.
ms.openlocfilehash: 15b15e56a1c490cab86f225c5784d8bb9adcb36e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977693"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme

SharePoint Online modern site sayfalarında, genel sayfa yükleme zamanlarında katkıda bulunabilirsiniz. Bu makale, sayfalarınıza web bölümlerinin kullanıcı gecikme süresini nasıl etkilediğini belirleme ve sık karşılaşılan sorunları düzeltme konularını anlamanıza yardımcı olur.

> [!NOTE]
> Çevrimiçi modern portallarda performans SharePoint için bkz[. Modern modern portalda SharePoint.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Web bölümlerini çözümlemek için SharePoint Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

> [!NOTE]
> Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint sitesi sayfasını çözümlerken, **Tanılama testleri bölmesindeki Web** bölümleri temel ölçümlerini aşan web bölümleri hakkında bilgilerin sayfa yükleme zamanlarını etkilemesini _görebilirsiniz._

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): görünüm görünümünde görünen herhangi bir _özel web bölümünün_ (önce yüklenen sayfanın ekran görünür bölümü) yüklenm süresi iki saniyeden uzun sürer. Görünüm _görünümünün_ dışında yer alan ve dört saniyeden uzun sürecek **tüm özel** web bölümlerinin yüklemesi. Toplam yükleme süresi test sonuçlarında görüntülenir ve modül yükü, tembel yükleme, init ve işleme ile bozulur.
- **Geliştirme fırsatları** (sarı): Bu bölümde sayfa yükleme sürelerini etkiliyor olabilir ve gözden geçirili ve izleniyor olması gerekir. Bu, "ilk önce" (OOTB) Microsoft web bölümlerini içerebilir. Bu bölümde gösterilen tüm Microsoft web bölümlerinin sonuçları otomatik olarak Microsoft'a bildirilir, dolayısıyla **işlem yapmak gerekmez**. Sayfada çok yavaş performansla ilgili sorunlar yaşıyorsanız ve sayfada tüm **Microsoft web** bölümleri Geliştirme fırsatları bölümündeki sonuçlarda görüntülenirse, yalnızca araştırma için bir destek bileti **günlüğe kaydedilir** . Gelecekteki bir Sayfa Tanılama aracı SharePoint güncelleştirmesi, Microsoft web sayfasının belirli yapılandırmasına bağlı olarak sonuçları daha da bozacak.
- **Herhangi bir işlem gerekmez** (yeşil): Hiçbir web bölümü, verileri geri almak **iki saniyeden** uzun sürüyor.

**Web bölümleri sayfa yükleme** süresi sonuçlarını etkiliyorsa, sonuçların Dikkat gerekiyor veya Geliştirme  fırsatları bölümünde görünüyorsa, hangi web bölümlerinin yavaş yükleniyor olduğuyla ilgili ayrıntıları görmek için sonucu tıklatın. Daha sonra Çözümleme Kuralları için Sayfa Tanılama SharePoint çözümleme kurallarında güncelleştirmeler olabilir, bu nedenle lütfen aracın her zaman en son sürümüne sahip olduğundan emin olun.

![Sayfa Tanılama aracı sonuçları.](../media/modern-portal-optimization/pagediag-web-part.png)

Sonuçlarda yer alan bilgiler:

- **Made by** shows whether the web part is custom or Microsoft OOTB.
- **Ad ve Kimlik** , sayfada web bölümünü bu konuda size yardımcı olacak tanımlayıcı bilgileri gösterir.
- **Toplam** , web bölümü için modül yükleme, başlatma ve işleme için toplam zamanı gösterir. Bu, web bölümü tarafından sayfada başından sonuna kadar işlemek için alınan toplam göreli süredir.
- **Modül Yükleme** , JavaScript ve CSS dosyalarını indirme, değerlendirme ve yükleme sürelerini gösterir. Ardından Init işlemi başlar.
- **Tembel Yükleme** , sayfanın ana bölümünde görülemez web bölümlerinin ertelenmiş yüklenme zamanlarını gösterir. İş için çok fazla web bölümü bulunduğu ve sayfa yükleme süresini en aza indirmek için iş işlemek için sıraya alınan bazı koşullar vardır.
- **Init** , web bölümü için verileri başlatma süresi gösterir.

  Bu zaman uyumsuz bir çağrıdır ve init zaman, döndürülen taa kinaye çözüm olduğunda OnInit işlevinin zaman hesaplamasıdır.

- **Oluşturma** işlemi, modül yüklemesi ve Init tamamlandıktan sonra kullanıcı arabirimini işlemek için gereken zamanı gösterir.

  Belgede (sayfa) DOM'leri bağlamanın JavaScript yürütme süresidir.
  Resimler gibi zaman uyumsuz kaynakların işlemesi ek zaman alsa da bu işlem biraz daha sürebilir.

Tasarımcıların ve geliştiricilerin sorunları gidermesine yardımcı olmak için bu bilgiler sağlanır. Bu bilgiler tasarım ve geliştirme ekibinize sağlanmalıdır.

## <a name="remediate-web-part-performance-issues"></a>Web bölümü performans sorunlarını düzeltme

Web bölümleri içinde listelenen web bölümleriyle ilgili performans sorunlarını tanımlamak ve düzeltmek için bu bölümdeki yönergeleri izleyin ve sayfa **yükleme süresi sonuçlarını** etkiler.

Kötü web bölümü performansının üç olası nedeni vardır. Senaryo için hangi sorunların geçerli olduğunu belirlemek ve düzeltmek için aşağıdaki bilgileri kullanın.

- Web bölümü komut dosyası boyutu ve bağımlılıkları
  - Ana hat senaryosunu yalnızca görüntüleme modu için işen ilk _betiği en iyi duruma getirme_.
  - Import() deyimini kullanarak öbekleri ayırmak için daha az sık senaryolar ve düzenleme modu kodunu (özellik bölmesi _gibi)_ taşıma.
  - Tüm eski kodu tamamen _kaldırmak için paket.json_ dosyasının bağımlılıklarını gözden geçirebilirsiniz. Tüm sınama/derleme yalnızca bağımlılıkları Bağımlılıklara taşıma.
  - En iyi statik Office 365 CDN için kaynağın kullanımı gereklidir. Genel CDN _js/css dosyaları için tercih_ edilir. Web siteyi kullanma hakkında daha fazla Office 365 CDN için bkz[. Office 365 Content Delivery Network (CDN) SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Yeni e-React _parçası_ olarak _gelen Doku_ ve Kumaş içeri aktarmaları gibi çerçeveleri SharePoint Framework SPFx. Daha fazla bilgi için bkz[. 2010'a SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Yeni sürümün en son sürümünü kullanmaya SharePoint Framework ve kullanılabilir hale geldikleri anda yeni sürümlere yükseltin.
- Veri alma/önbelleğe alma
  - Web bölümü, görüntü için veri getirmek için fazladan sunucu aramalarına dayanıyorsa, bu sunucu API'leri için hızlı olduğundan emin olun ve/veya istemci tarafı önbelleğe alma (daha büyük kümeler için _localStorage_ veya _IndexedDB_ kullanma gibi).
  - Kritik verileri işlemek için birden çok arama gerekirse, sunucuda toplu işlem yapmak veya istekleri tek bir aramada birleştirmenin diğer yöntemlerini kullanabilirsiniz.
  - Alternatif olarak, bazı veri öğelerine daha yavaş bir API gerektir ise ancak işlemenin başlatması için kritik öneme sahip değildir; kritik veriler iş geçirildikten sonra yürütülecek ayrı bir çağrı için bu kod çözebilirsiniz.
  - Birden fazla parça aynı verileri kullanıyorsa, yinelenen çağrıları önlemek için ortak bir veri katmanından faydalanabilirsiniz.
- İşleme süresi
  - Gereksiz büyük varlıkları indirmek için, resim ve videolar gibi medya kaynakları kapsayıcı, cihaz ve/veya ağ sınırlarına göre boyutlandırılmalıdır. İçerik bağımlılıkları hakkında daha fazla bilgi için bkz[. Office 365 Content Delivery Network (CDN) SharePoint Online..](use-microsoft-365-cdn-with-spo.md)
  - Yeniden akışa, karmaşık CSS kurallarına veya karmaşık animasyonlara neden olan API çağrılarından kaçının. Daha fazla bilgi için bkz [. Tarayıcı yeniden akışını en aza indirme](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Zincirleme uzun çalışan görevleri kullanmaktan kaçının. Bunun yerine, uzun süre çalışan görevleri birbirinden ayrı kuyruklara ayırabilirsiniz. Daha fazla bilgi için bkz. [JavaScript Yürütmeyi En İyi Duruma Getirme](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Atlanan kareleri ve teklemeleri (yalçın olarak da bilinir) önlemek için, zaman uyumsuz olarak medya veya görsel öğeleri işlemeye karşılık gelen _alanı rezerve etmek._
  - Belirli bir tarayıcı işlemede kullanılan bir özelliği desteklemezse, çoklu doldurmayı yükleyin veya bağımlı kodu çalıştırmayı dışlayın. Özellik kritik öneme sahip değilse, bellek sızıntılarını önlemek için olay işleyicileri gibi kaynakları atabilirsiniz.

Performans sorunlarını düzeltmek için sayfa düzeltmeleri öncesinde, çözümleme sonuçlarında sayfa yükleme sürelerini not edin. Yeni sonucun taban çizgisi standardı içinde olup olmadığını görmek için düzeltmeden sonra aracı yeniden çalıştırın ve bir geliştirme olup olmadığını görmek için yeni sayfa yükleme süresine bakın.

![Sayfa yükleme süresi sonuçları.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sayfa yükleme süresi ağ yükü, günün saati ve diğer geçici koşullar gibi çeşitli faktörlere bağlı olarak değişiklik gösterebilir. Sonuçların ortalamasını alarken değişiklik yaparak sayfa yükleme sürelerini birkaç kez test edebilirsiniz.

## <a name="related-topics"></a>İlgili konular

[Çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)

[Modern deneyimde SharePoint deneyimi](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)
