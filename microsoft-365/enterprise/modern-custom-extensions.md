---
title: SharePoint Online modern site sayfalarında özel uzantıları iyileştirme
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online modern site sayfalarında özel uzantıların performansını iyileştirmeyi öğrenin.
ms.openlocfilehash: a31b6e68227d433359537b9655d68c63b5893cce
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093865"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>SharePoint Çevrimiçi modern site sayfalarında özel uzantı performansını iyileştirme

Bu makale, özel uzantıların kullanıcı tarafından algılanan gecikme süresini nasıl etkileyeceğini ve yaygın sorunları nasıl gidereceğini anlamanıza yardımcı olur.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Özel uzantıları analiz etmek için SharePoint için Sayfa Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePoint Çevrimiçi modern portalı hem de klasik yayımlama sitesi sayfalarını analiz eden yeni Microsoft Edge (https://www.microsoft.com/edge) ve Chrome tarayıcıları) için bir tarayıcı uzantısıdır. Araç, analiz edilen her sayfa için sayfanın tanımlı bir performans ölçütleri kümesine göre nasıl performans gösterdiğini gösteren bir rapor sağlar. SharePoint için Sayfa Tanılama aracını yüklemek ve hakkında bilgi edinmek için [SharePoint Online için Sayfa Tanılama aracını kullanma](page-diagnostics-for-spo.md) sayfasını ziyaret edin.

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint site sayfasını analiz ettiğinizde, **Uzantılar yük süresini etkiliyor** ve/veya _Tanılama testleri_ bölmesinde kullanılan **çok fazla uzantı** sonucuyla ilgili temel ölçümü aşan özel uzantılar hakkındaki bilgileri görebilirsiniz 

Olası sonuçlar şunlardır:

- **Dikkat gerekiyor** (kırmızı): Yüklenmesi bir saniyeden uzun süren herhangi **bir** _özel_ uzantı. Test sonuçlarında gösterildiği gibi toplam yük süresi modül yüküne ve başlatmaya göre ayrılmıştır. Ayrıca, bir sayfada çok fazla uzantı varsa, bunlar sayfa yükleme süresini etkileyebilir ve sayfada **yedi** veya daha fazla uzantı kullanılıyorsa bu vurgulanır.
- **İyileştirme Fırsatları** (sarı) **Beş** veya daha fazla uzantı kullanılırsa, yedi veya daha fazla uzantı kullanılana kadar bu bölümde uyarı olarak vurgulanır ve daha sonra Dikkat Gerekiyor olarak vurgulanır.
- **Eylem gerekmez** (yeşil): Uzantının yüklenmesi bir saniyeden uzun sürmemektedir.

Bir uzantı sayfa yükleme süresini etkiliyorsa veya sayfada çok fazla uzantı varsa, sonuç sonuçların **Dikkat gerekiyor** bölümünde görünür. Hangi uzantının yavaş yüklendiği veya çok fazla uzantının vurgulandığıyla ilgili ayrıntıları görmek için sonuca tıklayın. SharePoint için Sayfa Tanılama aracında gelecekteki güncelleştirmeler analiz kuralları güncelleştirmelerini içerebilir, bu nedenle lütfen aracın her zaman en son sürümüne sahip olduğunuzdan emin olun.

![Sayfa yükleme süresi sonuçları.](../media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

Sonuçlarda bulunan bilgiler şunları içerir:

- **Ad ve kimlik** , sayfada uzantıyı bulmanıza yardımcı olabilecek tanımlayıcı bilgileri gösterir
- **Toplam** , modülü yüklemek ve başlatmak için uzantının toplam süresini gösterir. Uzantının sayfada baştan sona kadar yürütülmesi için geçen toplam göreli süredir.
- **Modül Yükleme** , JavaScript ve CSS dosyalarını indirmek, değerlendirmek ve yüklemek için geçen süreyi gösterir. Ardından Init işlemini başlatır.
- **Init** , uzantının verileri başlatması için geçen süreyi gösterir.

  Bu zaman uyumsuz bir çağrıdır ve döndürülen söz çözümlendiğinde onInit işlevinin zaman hesaplaması başlatma zamanıdır.

Bu bilgiler tasarımcıların ve geliştiricilerin sorunları gidermesine yardımcı olmak için sağlanır. Bu bilgiler tasarım ve geliştirme ekibinize sağlanmalıdır.

## <a name="overview-of-extensions"></a>Uzantılara genel bakış

SharePoint Framework (SPFx) Uzantıları, SharePoint kullanıcı deneyimini genişletmek için kullanılabilir. SharePoint Framework Uzantıları ile bildirim alanları, araç çubukları ve liste veri görünümleri dahil olmak üzere SharePoint deneyiminin daha fazla modelini özelleştirebilirsiniz.

Uzantıların SharePoint sayfasının performansı üzerinde kötü bir etkisi olabilir çünkü gerekli işleri yapmak için CPU ve ağ kaynaklarını da kullanır.

Dört tür uzantı vardır:

- **Uygulama Özelleştiricileri** sayfaya betikler ekler ve iyi bilinen HTML öğesi yer tutucularına erişir ve bunları özel işlemelerle genişletir.
- **Alan Özelleştiricileri** , liste içindeki alanların verilerine değiştirilmiş görünümler sağlar.
- **Komut Kümeleri**, yeni eylemler eklemek için SharePoint komut yüzeylerini genişletir ve davranışları uygulamak için kullanabileceğiniz istemci tarafı kodu sağlar.
- **Arama Sorgusu Değiştiricisi (yalnızca önizleme)** arama sorgusu yürütülmeden hemen önce çağrılır.

## <a name="remediate-extension-performance-issues"></a>Uzantı performansı sorunlarını düzeltme

**Uzantılar sayfa yükleme süresi sonuçlarını etkiliyor** bölümünde listelenen uzantılarla ilgili performans sorunlarını belirlemek ve düzeltmek için bu bölümdeki yönergeleri izleyin.

>[!NOTE]
>Uygulama özelleştiricileri bir sayfanın yaşam döngüsü sırasında erken aşamada yürütülebilir ve sayfadaki diğer uzantıların performansını etkileyebilir.

Sayfa Tanılama Aracı'ndaki denetim sonuçları, olası performans etkisini belirlemeye yardımcı olmak için uzantı yürütmenin iki aşamasını görüntüler.

- **Modül yükü** , uzantının yüklenmesinin ne kadar sürdüğüdür ve uzantının boyutundan etkilenir, bu nedenle uzantıda yalnızca gerekli kitaplıkları paketlemek ve daha açık kitaplıklar seçmek iyi bir fikirdir.
- **Init** , uzantının başlatma zamanıdır ve uzantı geliştiricilerinin uzantının başlatma aşamasında gereksiz iş mi yoksa çok fazla komut mu yürüttüğüne karar vermesi gerekir.

Sayfa yazarları, bir sayfanın çok fazla uzantıya sahip olup olmadığını ve çok fazla uzantının sayfanın performansını olumsuz etkileyip etkilemediğini görmek için denetim sonucunu da kullanabilir.

- **Uzantı boyutu ve bağımlılıkları**
  - en iyi statik kaynak indirmesi için Office 365 CDN kullanılması gerekir. _Js/css_ dosyaları için genel CDN kaynakları tercih edilir. Office 365 CDN kullanma hakkında daha fazla bilgi için bkz. [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md).
  - _SharePoint Framework (SPFx_) parçası olarak gelen React ve _Doku içeri aktarmaları gibi çerçeveleri_ yeniden kullanma. Daha fazla bilgi için bkz. [SharePoint Framework genel bakış](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - SharePoint Framework en son sürümünü kullandığınızdan emin olun ve kullanıma sunulduklarında yeni sürümlere yükseltin.
- **Veri getirme/önbelleğe alma**
  - Uzantı, görüntülenmek üzere veri getirmek için ek sunucu çağrılarına dayanırsa, bu sunucu API'lerinin hızlı olduğundan emin olun ve/veya istemci tarafı önbelleğe alma uygulayın (daha büyük _kümeler için localStorage_ veya _IndexDB_ kullanma gibi).
  - Kritik verileri işlemek için birden çok çağrı gerekiyorsa, sunucuda toplu işlem yapmayı veya istekleri tek bir çağrıya birleştirmenin diğer yöntemlerini göz önünde bulundurun.
  - Alternatif olarak, bazı veri öğeleri daha yavaş bir API gerektiriyorsa ancak ilk işleme için kritik değilse, bunları kritik veriler işlendikten sonra yürütülen ayrı bir çağrıya ayırın.
  - Birden çok parça aynı verileri kullanıyorsa, yinelenen çağrıları önlemek için ortak bir veri katmanı kullanın.
- **İşleme süresi**
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