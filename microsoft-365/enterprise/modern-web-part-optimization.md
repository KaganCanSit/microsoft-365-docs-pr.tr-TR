---
title: SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 543ee889831d08b2b465c077cc391a653fa0b9a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093360"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme

SharePoint Çevrimiçi modern site sayfaları, genel sayfa yükleme sürelerine katkıda bulunabilecek web bölümleri içerir. Bu makale, sayfalarınızdaki web bölümlerinin kullanıcı tarafından algılanan gecikme süresini nasıl etkileyeceğini ve yaygın sorunları nasıl giderebileceğinizi anlamanıza yardımcı olur.

> [!NOTE]
> SharePoint Çevrimiçi modern portallardaki performans hakkında daha fazla bilgi için bkz. [Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Web bölümlerini analiz etmek için SharePoint için Sayfa Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePoint Çevrimiçi modern portalı hem de klasik yayımlama sitesi sayfalarını analiz eden yeni Microsoft Edge (https://www.microsoft.com/edge) ve Chrome tarayıcıları) için bir tarayıcı uzantısıdır. Araç, analiz edilen her sayfa için sayfanın tanımlı bir performans ölçütleri kümesine göre nasıl performans gösterdiğini gösteren bir rapor sağlar. SharePoint için Sayfa Tanılama aracını yüklemek ve hakkında bilgi edinmek için [SharePoint Online için Sayfa Tanılama aracını kullanma](page-diagnostics-for-spo.md) sayfasını ziyaret edin.

> [!NOTE]
> Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint site sayfasını çözümlediğinizde, _Tanılama testleri_ bölmesinde Web bölümlerinde temel ölçümü aşan **web bölümleri hakkındaki bilgilerin sayfa yükleme süresi sonucunu etkilediğini** görebilirsiniz.

Olası sonuçlar şunlardır:

- **Dikkat gerekiyor** (kırmızı): Görünüm penceresi içinde görünen herhangi bir _özel_ web bölümü (sayfanın ilk yüklenen ekran görünür bölümü) yüklenmesi **iki** saniyeden uzun sürer. Görünüm penceresi dışında **dört saniyeden** uzun sürecek _tüm özel_ web bölümlerinin yüklenmesi. Toplam yük süresi test sonuçlarında görüntülenir ve modül yükü, gecikmeli yük, başlatma ve işlemeye göre ayrılmıştır.
- **İyileştirme fırsatları** (sarı): Sayfa yükleme süresini etkileyebilecek öğeler bu bölümde gösterilir ve gözden geçirilip izlenmesi gerekir. Bu, "kullanıma açık" (OOTB) Microsoft web bölümlerini içerebilir. Bu bölümde gösterilen tüm Microsoft web bölümlerinin sonuçları otomatik olarak Microsoft'a bildirilir, bu nedenle **herhangi bir eylem gerekmez**. Yalnızca sayfada çok yavaş performansla karşılaşıyorsanız ve sayfadaki **tüm Microsoft web bölümleri** **İyileştirme fırsatları** bölümündeki sonuçlarda görünüyorsa araştırma için bir destek bileti kaydetmeniz gerekir. SharePoint araç güncelleştirmesi için gelecek bir Sayfa Tanılaması'nın, Microsoft web bölümünün belirli yapılandırmasına bağlı olarak sonuçları daha da böleceğini unutmayın.
- **Eylem gerekmez** (yeşil): Hiçbir web bölümünün veri döndürmesi **iki** saniyeden uzun sürmemektedir.

**Web bölümleri sayfa yükleme süresini etkiliyorsa**, sonuçların **Dikkat gerekiyor** veya **İyileştirme fırsatları** bölümünde görünüyorsa, hangi web bölümlerinin yavaş yüklendiğiyle ilgili ayrıntıları görmek için sonuca tıklayın. SharePoint için Sayfa Tanılama aracında gelecekteki güncelleştirmeler analiz kuralları güncelleştirmelerini içerebilir, bu nedenle lütfen aracın her zaman en son sürümüne sahip olduğunuzdan emin olun.

![Sayfa Tanılama aracı sonuçları.](../media/modern-portal-optimization/pagediag-web-part.png)

Sonuçlarda bulunan bilgiler şunları içerir:

- **Oluşturan** , web bölümünün özel mi yoksa Microsoft OOTB mi olduğunu gösterir.
- **Ad ve kimlik** , sayfada web bölümünü bulmanıza yardımcı olabilecek tanımlayıcı bilgileri gösterir.
- **Toplam** , web bölümünün modül yükleme, başlatma ve işleme için toplam süresini gösterir. Başlangıçtan sonuna kadar web bölümünün sayfada işlenmesi için geçen toplam göreli süredir.
- **Modül Yükleme** , JavaScript ve CSS dosyalarını indirmek, değerlendirmek ve yüklemek için geçen süreyi gösterir. Ardından Init işlemini başlatır.
- **Gecikmeli Yükleme** , sayfanın ana bölümünde görünmeyen web bölümlerinin ertelenmiş yükleme süresini gösterir. İşlenmek üzere çok fazla web bölümü olduğu ve sayfa yükleme süresini en aza indirmek için işlenmek üzere kuyruğa alındığı bazı koşullar vardır.
- **Init** , web bölümünün verileri başlatması için geçen süreyi gösterir.

  Bu zaman uyumsuz bir çağrıdır ve döndürülen söz çözümlendiğinde onInit işlevinin zaman hesaplaması başlatma zamanıdır.

- **İşleme** , modül yükü ve Init tamamlandıktan sonra kullanıcı arabirimini (kullanıcı arabirimi) işlemek için geçen süreyi gösterir.

  DoM'u belgeye (sayfa) bağlamak için JavaScript yürütme zamanıdır.
  Zaman uyumsuz kaynakların (örneğin, görüntülerin) işlenmesinin tamamlanması ek zaman alabilir.

Bu bilgiler tasarımcıların ve geliştiricilerin sorunları gidermesine yardımcı olmak için sağlanır. Bu bilgiler tasarım ve geliştirme ekibinize sağlanmalıdır.

## <a name="remediate-web-part-performance-issues"></a>Web bölümü performans sorunlarını düzeltme

Web bölümlerinde listelenen web bölümleri sayfa **yükleme süresi sonuçlarını etkiliyorsa** performans sorunlarını belirlemek ve düzeltmek için bu bölümdeki yönergeleri izleyin.

Kötü web bölümü performansının üç olası nedeni kategorisi vardır. Senaryonuz için hangi sorunların geçerli olduğunu belirlemek ve bunları düzeltmek için aşağıdaki bilgileri kullanın.

- Web bölümü betik boyutu ve bağımlılıkları
  - _Yalnızca görüntüleme modu_ için ana hat senaryosunu işleyen ilk betiği iyileştirin.
  - _Import()_ deyimini kullanarak daha az sıklıkta senaryoları ve düzenleme modu kodunu (özellik bölmesi gibi) ayrı öbeklere taşıyın.
  - Tüm ölü kodları tamamen kaldırmak için _package.json_ dosyasının bağımlılıklarını gözden geçirin. Tüm test/derleme bağımlılıklarını devDependencies'e taşıyın.
  - en iyi statik kaynak indirmesi için Office 365 CDN kullanılması gerekir. _Js/css_ dosyaları için genel CDN kaynakları tercih edilir. Office 365 CDN kullanma hakkında daha fazla bilgi için bkz. [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md).
  - _SharePoint Framework (SPFx_) parçası olarak gelen React ve _Doku içeri aktarmaları gibi çerçeveleri_ yeniden kullanma. Daha fazla bilgi için bkz. [SharePoint Framework genel bakış](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - SharePoint Framework en son sürümünü kullandığınızdan emin olun ve kullanıma sunulduklarında yeni sürümlere yükseltin.
- Veri getirme/önbelleğe alma
  - Web bölümü, görüntülenmek üzere veri getirmek için ek sunucu çağrılarına dayanırsa, bu sunucu API'lerinin hızlı olduğundan emin olun ve/veya istemci tarafı önbelleğe alma (daha büyük _kümeler için localStorage_ veya _IndexedDB_ kullanma gibi) uygulayın.
  - Kritik verileri işlemek için birden çok çağrı gerekiyorsa, sunucuda toplu işlem yapmayı veya istekleri tek bir çağrıya birleştirmenin diğer yöntemlerini göz önünde bulundurun.
  - Alternatif olarak, bazı veri öğeleri daha yavaş bir API gerektiriyorsa ancak ilk işleme için kritik değilse, bunları kritik veriler işlendikten sonra yürütülen ayrı bir çağrıya ayırın.
  - Birden çok parça aynı verileri kullanıyorsa, yinelenen çağrıları önlemek için ortak bir veri katmanı kullanın.
- İşleme süresi
  - Görüntüler ve videolar gibi tüm medya kaynakları gereksiz büyük varlıkların indirilmesini önlemek için kapsayıcı, cihaz ve/veya ağın sınırlarına göre boyutlandırılmalıdır. İçerik bağımlılıkları hakkında daha fazla bilgi için bkz. [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md).
  - Yeniden akışa, karmaşık CSS kurallarına veya karmaşık animasyonlara neden olan API çağrılarından kaçının. Daha fazla bilgi için bkz. [Tarayıcı yeniden akışını en aza indirme](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Zincirlenmiş uzun süre çalışan görevleri kullanmaktan kaçının. Bunun yerine, uzun süre çalışan görevleri ayrı kuyruklara ayırın. Daha fazla bilgi için bkz. [JavaScript Yürütmesini İyileştirme](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Atlanan çerçeveleri ve takılmayı ( _jank_ olarak da bilinir) önlemek için zaman uyumsuz olarak medya veya görsel öğeleri işlemek için ilgili alanı ayırın.
  - Belirli bir tarayıcı işlemede kullanılan bir özelliği desteklemiyorsa, polyfill yükleyin veya bağımlı kodu çalıştırmayı dışlayın. Özellik kritik değilse, bellek sızıntılarını önlemek için olay işleyicileri gibi kaynakları atın.

Performans sorunlarını düzeltmek için sayfa düzeltmeleri yapmadan önce, çözümleme sonuçlarında sayfa yükleme süresini not edin. Yeni sonucun temel standart içinde olup olmadığını görmek için düzeltmenizden sonra aracı yeniden çalıştırın ve bir iyileştirme olup olmadığını görmek için yeni sayfa yükleme süresini denetleyin.

![Sayfa yükleme süresi sonuçları.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sayfa yükleme süresi, ağ yükü, günün saati ve diğer geçici koşullar gibi çeşitli faktörlere bağlı olarak farklılık gösterebilir. Sonuçları ortalamanıza yardımcı olacak değişiklikler yapmadan önce ve sonra sayfa yükleme süresini birkaç kez test etmelisiniz.

## <a name="related-topics"></a>İlgili konular

[çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Office 365 performansını ayarlama](tune-microsoft-365-performance.md)

[Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md)
