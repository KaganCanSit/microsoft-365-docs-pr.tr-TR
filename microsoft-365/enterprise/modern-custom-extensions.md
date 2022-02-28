---
title: SharePoint Online modern site sayfalarında özel uzantıları en iyi duruma getirme
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online modern site sayfalarında özel uzantıların performansını iyileştirmeyi öğrenin.
ms.openlocfilehash: 6493f140a1335b5439707fed94372760ac6fab50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986527"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>SharePoint Online modern site sayfalarında özel uzantı performansını iyileştirme

Bu makale, özel uzantıların kullanıcı gecikme süresini nasıl etkilediğini belirleme ve yaygın sorunları düzeltme konularını anlamanıza yardımcı olur.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Özel uzantıları çözümlemek için SharePoint Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint sitesi sayfasını çözümlerken, Uzantılar'daki temel ölçümü aşan özel uzantılar hakkında bilgi görebilirsiniz. Yükleme süresi ve/veya Tanılama testleri bölmesinde  Çok fazla kullanılan uzantı sonucu   

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): Bir _saniyeden_ uzun sürebilir tüm **özel** uzantılar. Test sonuçlarında görüntülendiğinde toplam yükleme süresi, modül yükleme ve init ile bozulur. Ayrıca, sayfada çok fazla uzantı varsa, bunlar sayfa yükleme sürelerini etkileyebilirsiniz ve sayfada yedi veya daha fazla uzantı kullanılıyorsa bu vurgulanır.
- **Geliştirme Fırsatları** (sarı) Beş  veya daha fazla uzantı kullanılırsa, yedi veya daha fazla uzantı kullanıncaya kadar bu bölümde bir uyarı olarak vurgulanır ve bu durumda Dikkat Gerekiyor olarak vurgulanır.
- **Herhangi bir işlem gerekmez** (yeşil): Uzantı yükleme işlemi bir saniyeden uzun sürer.

Bir uzantı sayfa yükleme sürelerini etkiliyorsa veya sayfada çok fazla uzantı varsa, sonuç sonuçların **Dikkat** gerekiyor bölümünde görünür. Hangi uzantının yavaş yükleniyor hakkında ayrıntılı bilgi için veya çok fazla sayıda uzantının vurgulanmış olduğunu görmek için sonucu tıklatın. Daha sonra Çözümleme Kuralları için Sayfa Tanılama SharePoint çözümleme kurallarında güncelleştirmeler olabilir, bu nedenle lütfen aracın her zaman en son sürümüne sahip olduğundan emin olun.

![Sayfa yükleme süresi sonuçları.](../media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

Sonuçlarda yer alan bilgiler:

- **Ad ve Kimlik** , sayfada uzantıyı bu konuda size yardımcı olacak tanımlayıcı bilgileri gösterir
- **Toplam** , modül yükleme ve başlatma uzantısı için toplam zamanı gösterir. Bu, uzantının sayfada başından sonuna kadar yürütmesi gereken toplam göreli süredir.
- **Modül Yükleme** , JavaScript ve CSS dosyalarını indirme, değerlendirme ve yükleme sürelerini gösterir. Ardından Init işlemi başlar.
- **Init** , verileri başlatmak üzere uzantı için alınan zamanı gösterir.

  Bu zaman uyumsuz bir çağrıdır ve init zaman, döndürülen taa kinaye çözüm olduğunda OnInit işlevinin zaman hesaplamasıdır.

Tasarımcıların ve geliştiricilerin sorunları gidermesine yardımcı olmak için bu bilgiler sağlanır. Bu bilgiler tasarım ve geliştirme ekibinize sağlanmalıdır.

## <a name="overview-of-extensions"></a>Uzantılara genel bakış

SharePoint Framework (SPFx) Uzantılar, kullanıcı deneyimini SharePoint için kullanılabilir. Uzantılar SharePoint Framework, bildirim alanları, araç çubukları ve liste SharePoint görünümler de dahil olmak üzere, kullanıcı deneyiminin daha fazla görünümünü özelleştirebilirsiniz.

Aynı zamanda CPU ve ağ kaynaklarını gerekli işi yapmak için gerektiğinden, uzantılar bir SharePoint sayfasının performansını kötü etkileyebilir.

Dört tür uzantı vardır:

- **Uygulama Özelleştiricileri** sayfaya betikler ekler ve iyi bilinen HTML öğesi yer tutucularına erişer ve bunları özel işlemelerle genişleter.
- **Alan Özelleştirleştiricileri** , liste içindeki alanların verilerine değiştirilmiş görünümler sağlar.
- **Komut Kümeleri**, SharePoint eklemek üzere komut yüzeylerini genişlettir ve eylemleri uygulamak için kullanabileceğiniz istemci tarafı kodu sağlar.
- **Arama Sorgusu Değiştirici (yalnızca önizleme),** arama sorgusu yürütülmeden hemen önce çağırıldı.

## <a name="remediate-extension-performance-issues"></a>Uzantı performans sorunlarını düzeltme

Uzantılar bölümünde listelenen uzantılarla ilgili performans sorunlarını tanımlamak ve düzeltmek için bu bölümdeki yönergeleri izleyin ve **sayfa yükleme süresi sonuçlarını** etkiler.

>[!NOTE]
>Uygulama özelleştiricileri, bir sayfanın yaşam döngüsü boyunca erken aşamada yürütülebilir ve bu da sayfada diğer uzantıların performansını etkileyebilir.

Sayfa Tanılama Aracı'nın denetim sonuçlarında, performans üzerindeki olası etkiyi belirlemeye yardımcı olmak için bir uzantıyı yürütmenin iki aşamasında görüntülenir.

- **Modül yüklemesi** , uzantıyı yüklemenin ne kadar uzun sürer? Bu uzantının boyutundan etki büyük olduğu için, uzantıda yalnızca gerekli kitaplıkları paketli yapmak ve daha açık kitaplıkları seçmek iyi bir fikirdir.
- **Init** , uzantıyı ve uzantı geliştiricilerinin başlatma zamanıdır; uzantının gereksiz çalışmalar mı yaptığını yoksa başlatma aşamasında çok fazla komutu yürütüp yürütme yaptığını dikkate almaları gerekir.

Sayfa yazarları da denetim sonucu kullanarak bir sayfanın çok fazla uzantısının olup olmadığını görmek için sayfanın performansını olumsuz etkileyebilir.

- **Uzantı boyutu ve bağımlılıkları**
  - En iyi statik Office 365 CDN için kaynağın kullanımı gereklidir. Genel CDN _js/css dosyaları için tercih_ edilir. Web siteyi kullanma hakkında daha fazla Office 365 CDN için bkz[. Office 365 Content Delivery Network (CDN) SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Yeni e-React _parçası_ olarak _gelen Doku_ ve Kumaş içeri aktarmaları gibi çerçeveleri SharePoint Framework SPFx. Daha fazla bilgi için bkz[. 2010'a SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Yeni sürümün en son sürümünü kullanmaya SharePoint Framework ve kullanılabilir hale geldikleri anda yeni sürümlere yükseltin.
- **Veri alma/önbelleğe alma**
  - Uzantı, görüntü için veri getirmek için fazladan sunucu aramalarına dayanıyorsa, bu sunucu API'leri için hızlı olduğundan emin olun ve/veya istemci tarafı önbelleğe alma (daha büyük kümeler için _localStorage_ veya _IndexDB_ kullanma gibi).
  - Kritik verileri işlemek için birden çok arama gerekirse, sunucuda toplu işlem yapmak veya istekleri tek bir aramada birleştirmenin diğer yöntemlerini kullanabilirsiniz.
  - Alternatif olarak, bazı veri öğelerine daha yavaş bir API gerektir ise ancak işlemenin başlatması için kritik öneme sahip değildir; kritik veriler iş geçirildikten sonra yürütülecek ayrı bir çağrı için bu kod çözebilirsiniz.
  - Birden fazla parça aynı verileri kullanıyorsa, yinelenen çağrıları önlemek için ortak bir veri katmanından faydalanabilirsiniz.
- **İşleme süresi**
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