---
title: SharePoint Online için Sayfa Tanılama aracını kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/03/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: SharePoint Çevrimiçi modern portalı ve klasik yayımlama sayfalarını önceden tanımlanmış performans ölçütleri kümesine göre çözümlemek için SharePoint için Sayfa Tanılama aracını kullanın.
ms.openlocfilehash: b39b547754acc6f12c750192af2986e9b4e54150
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095674"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint için Sayfa Tanılama aracını kullanma

Bu makalede, SharePoint Çevrimiçi modern ve klasik site sayfalarını önceden tanımlanmış bir performans ölçütleri kümesine göre analiz etmek **üzere SharePoint için Sayfa Tanılama aracının** nasıl kullanılacağı açıklanmaktadır.

SharePoint için Sayfa Tanılama aracı aşağıdakiler için yüklenebilir:

- **Microsoft Edge** [(Edge uzantısı)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(Chrome uzantısı)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>Sürüm **2.0.0** ve üzeri, klasik site sayfalarına ek olarak modern sayfalar için destek içerir. Aracın hangi sürümünü kullandığınızdan emin değilseniz, sürümünüzü doğrulamak için **Hakkında** bağlantısını veya üç noktayı (...) seçebilirsiniz. Aracı kullanırken **her zaman en son sürüme güncelleştirin**.

SharePoint için Sayfa Tanılama aracı, hem SharePoint Çevrimiçi modern portalı hem de klasik yayımlama sitesi sayfalarını analiz eden yeni Microsoft Edge (https://www.microsoft.com/edge) ve Chrome tarayıcıları) için bir tarayıcı uzantısıdır. Bu araç yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

Araç, analiz edilen her sayfa için sayfanın önceden tanımlanmış bir kural kümesine göre nasıl performans gösterdiğini gösteren bir rapor oluşturur ve test sonuçları temel değerin dışında olduğunda ayrıntılı bilgiler görüntüler. SharePoint Çevrimiçi yöneticiler ve tasarımcılar, performans sorunlarını gidermek ve yayımlamadan önce yeni sayfaların iyileştirildiğinden emin olmak için aracı kullanabilir.

Sayfa Tanılama aracı, *allitems.aspx* veya *sharepoint.aspx* gibi sistem sayfalarını değil, yalnızca SharePoint site sayfalarını analiz etmek için tasarlanmıştır. Aracı bir sistem sayfasında veya site olmayan başka bir sayfada çalıştırmayı denerseniz, aracın bu tür bir sayfa için çalıştırılamayacağını bildiren bir hata iletisi alırsınız.

> [!div class="mx-imgBorder"]
> ![SharePoint sayfasında çalıştırılmalıdır.](../media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Kitaplıkları veya sistem sayfalarını değerlendirmede değer olmadığından bu araçta bir hata değildir. Aracı kullanmak için lütfen SharePoint site sayfasına gidin. Bu hata bir SharePoint sayfasında oluşursa, SharePoint meta etiketlerinin kaldırılmadığından emin olmak için lütfen ana sayfayı denetleyin.

Araç hakkında geri bildirim sağlamak için aracın sağ üst köşesindeki üç noktayı ve ardından [Geri bildirimde bulun'ı](https://go.microsoft.com/fwlink/?linkid=874109) seçin.

> [!div class="mx-imgBorder"]
> ![Geri bildirimde bulunmak.](../media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint için Sayfa Tanılama aracını yükleme

Bu bölümdeki yükleme yordamı hem Chrome hem de Microsoft Edge tarayıcılar için çalışır.

> [!IMPORTANT]
> Microsoft, SharePoint için Sayfa Tanılama aracı tarafından analiz edilen verileri veya sayfa içeriğini okumaz ve hiçbir kişisel bilgi, web sitesi veya indirme bilgisi yakalamayız. Araç tarafından Microsoft'ta günlüğe kaydedilen tek tanımlanabilir bilgiler kiracı adı, başarısız olan kural sayısı ve aracın çalıştırıldığı tarih ve saattir. Bu bilgiler Microsoft tarafından modern portalı daha iyi anlamak ve site kullanım eğilimlerini ve yaygın performans sorunlarını yayımlamak için kullanılır.

1. Microsoft Edge ([Edge uzantısı)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) veya **Chrome** ([Chrome uzantısı](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)) için **SharePoint** için Sayfa Tanılama aracını yükleyin. Lütfen mağazanın açıklama sayfasında sağlanan Kullanıcı Gizlilik İlkesi'ni gözden geçirin. Aracı tarayıcınıza eklerken aşağıdaki izin bildirimini görürsünüz.

    > [!div class="mx-imgBorder"]
    > ![Uzantı izinleri.](../media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Sayfa, web bölümlerine ve sayfadaki özelleştirmelere bağlı olarak SharePoint dışındaki konumlardan içerik içerebileceğinden bu bildirim uygulanır. Bu, başlangıç düğmesine tıklandığında ve yalnızca aracın çalıştığı etkin SharePoint sekmesi için aracın istekleri ve yanıtları okuyacağı anlamına gelir. Bu bilgiler web tarayıcısı tarafından yerel olarak yakalanır ve aracın _Ağ izleme_ sekmesindeki **JSON'a Aktar** veya **HAR'ya Aktar** düğmesi aracılığıyla size sağlanır. **Bilgiler Microsoft'a gönderilmez veya microsoft tarafından yakalanmaz.** (Araç [, buradan](https://go.microsoft.com/fwlink/p/?linkid=857875) erişilebilen Microsoft gizlilik ilkesine saygı gösterir.)

    _İndirmelerinizi yönetin_ izni, aracın **JSON'a aktar** işlevinin kullanımını kapsar. Sonuçlar URL'ler içerdiğinden ve PII (Kişisel Bilgiler) olarak sınıflandırılaabildiği için JSON dosyasını kuruluşunuzun dışında paylaşmadan önce lütfen şirketinizin kendi gizlilik yönergelerini izleyin.
1. Aracı Gizli veya InPrivate modunda kullanmak istiyorsanız tarayıcınızın yordamını izleyin:
    1. Microsoft Edge'da **Uzantılar'a** gidin veya URL çubuğuna _edge://extensions_ yazın ve uzantı için **Ayrıntılar'ı** seçin. Uzantı ayarlarında **InPrivate'te izin ver** onay kutusunu seçin.
    1. Chrome'da **Uzantılar'a** gidin veya URL çubuğuna _chrome://extensions_ yazın ve uzantı için **Ayrıntılar'ı** seçin. Uzantı ayarlarında **Gizli'de izin ver** kaydırıcısını seçin.
1. SharePoint Online'da gözden geçirmek istediğiniz SharePoint site sayfasına gidin. Sayfalardaki öğelerin "yüklenmesini geciktirme" izni verdik; bu nedenle, araç otomatik olarak durmaz (bu, tüm sayfa yükleme senaryolarını barındırmak için tasarım gereğidir). Koleksiyonu durdurmak için **Durdur'u** seçin. Veri toplamayı durdurmadan önce sayfa yükünün tamamlandığından emin olun; aksi takdirde yalnızca kısmi bir izleme yakalarsınız.
1. Uzantının araç çubuğu düğmesine tıklayın ![SharePoint logosu için Sayfa Tanılama.](../media/page-diagnostics-for-spo/pagediag-icon32.png) aracı yüklemek için size aşağıdaki uzantı açılır penceresi gösterilir:

    ![Sayfa Tanılama aracı Açılan menüsü.](../media/page-diagnostics-for-spo/pagediag-Landing.png)

Analiz için veri toplamaya başlamak için **Başlat'ı** seçin.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint için Sayfa Tanılama aracında görecekler

1. Aşağıdaki bağlantıları bulmak için aracın sağ üst köşesindeki üç noktaya (...) tıklayın:
   1. **Ek kaynaklar** bağlantısı, bu makalenin bağlantısı da dahil olmak üzere araçla ilgili genel yönergeler ve ayrıntılar sağlar.
   1. **Geri bildirimde bulun** bağlantısı _, SharePoint Siteleri ve İşbirliği User Voice_ sitesine bir bağlantı sağlar.
   1. **Hakkında** bağlantısı, aracın şu anda yüklü olan sürümünü ve aracın üçüncü taraf bildiriminin doğrudan bağlantısını içerir.  
1. **Bağıntı Kimliği, SPRequestDuration, SPIISLatency**, **Sayfa yükleme süresi** ve **URL** ayrıntıları bilgilendiricidir ve birkaç amaç için kullanılabilir.

    > [!div class="mx-imgBorder"]
    > ![Sayfa tanılama ayrıntıları.](../media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID**, belirli bir sayfa için ek tanılama verileri toplamalarına olanak sağladığından, Microsoft Desteği ile çalışırken önemli bir öğedir.
   - **SPRequestDuration**, SharePoint sayfayı işlemesi için geçen süredir. Yapısal gezinti, büyük görüntüler ve çok sayıda API çağrısı daha uzun sürelere katkıda bulunabilir.
   - **SPIISLatency**, SharePoint Online'ın sayfayı yüklemeye başlaması için geçen milisaniye cinsinden süredir. Bu değer, web uygulamasının yanıt vermesi için geçen süreyi içermez.
   - **Sayfa yükleme süresi** , istek saatinden yanıtın alındığı ve tarayıcıda işlendiği zamana kadar sayfa tarafından kaydedilen toplam süredir. Bu değer ağ gecikme süresi, bilgisayarın performansı ve tarayıcının sayfayı yükleme süresi gibi çeşitli faktörlerden etkilenir.
   - **Sayfa URL'si** (Tekdüzen Kaynak Bulucu), geçerli sayfanın web adresidir.

1. [**Tanılama testleri**](#how-to-use-the-diagnostic-tests-tab) sekmesi analiz sonuçlarını üç kategoride görüntüler; **Eylem gerekmez**, **İyileştirme fırsatları** ve **Dikkat gerekir**. Her test sonucu, aşağıdaki tabloda açıklandığı gibi bu kategorilerden birinde yer alan bir öğeyle temsil edilir:

    |Kategori  |Renk  |Açıklama  |
    |---------|---------|---------|
    |**Dikkat gerekiyor** |Kırmızı |Test sonucu temel değerin dışında kalıyor ve sayfa performansını etkiliyor. Düzeltme kılavuzlarını izleyin.|
    |**İyileştirme fırsatları** |Sarı |Test sonucu temel değerin dışında kalıyor ve performans sorunlarına katkıda bulunuyor olabilir. Teste özgü ölçütler uygulanabilir.|
    |**Eylem gerekmez** |Yeşil |Test sonucu, testin temel değerinin içinde yer alır.|

    > [!div class="mx-imgBorder"]
    > ![Sayfa tanılama.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. [**Ağ izleme**](#how-to-use-the-network-trace-tab-and-how-to-export-a-har-file) sekmesi, sayfa derleme istekleri ve yanıtları hakkında ayrıntılar sağlar.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Tanılama testleri sekmesini kullanma

SharePoint için Sayfa Tanılama aracıyla SharePoint modern portal sayfasını veya klasik yayımlama sitesi sayfasını analiz ettiğinizde, sonuçlar temel değerlerle karşılaştıran önceden tanımlanmış kurallar kullanılarak analiz edilir ve **Tanılama testleri** sekmesinde görüntülenir. Bazı testlerin kuralları, modern portal ve klasik yayımlama siteleri için belirli performansa bağlı olarak farklı temel değerler kullanabilir  özellikleri ikisi arasında farklılık gösterir.

**İyileştirme fırsatları** veya **Dikkat gerektiren** kategoriler bölümünde gösterilen test sonuçları, önerilen yöntemlere göre gözden geçirilmesi gereken alanları gösterir ve sonuç hakkında ek bilgi görüntülemek için seçilebilir. Her öğenin ayrıntıları, sizi doğrudan testle ilgili uygun rehberliğe götürecek _daha fazla bilgi edinin_ bağlantısı içerir. **Eylem gerekli değil** kategorisinde gösterilen test sonuçları, ilgili kuralla uyumluluğu gösterir ve seçildiğinde ek ayrıntıları görüntülemez.

Tanılama testleri sekmesindeki bilgiler sayfaları nasıl tasarlayabileceğinizi söylemez, ancak sayfa performansını etkileyebilecek faktörleri vurgular. Bazı sayfa işlevleri ve özelleştirmeleri sayfa performansı üzerinde kaçınılmaz bir etkiye sahiptir ve etkileri önemliyse olası düzeltme veya eksiklik açısından gözden geçirilmelidir.

Kırmızı veya sarı sonuçlar, verileri çok sık yenileyen web bölümlerini de gösterebilir. Örneğin, kurumsal haberler her saniye güncelleştirilmez, ancak özel web bölümleri genellikle genel kullanıcı deneyimini geliştirebilecek önbelleğe alma öğeleri uygulamak yerine en son haberleri her saniye getirmek için oluşturulur. Web bölümlerini sayfaya eklerken, hedeflenen amaca uygun şekilde ayarlandığından emin olmak için kullanılabilir her parametrenin değerini değerlendirerek performans etkilerini azaltmanın genellikle basit yolları olduğunu unutmayın.

>[!NOTE]
>Yayımlama özelliği etkin olmayan klasik ekip siteleri CDN'leri kullanamaz. Aracı bu sitelerde çalıştırdığınızda, CDN testinin başarısız olması beklenir ve yoksayılabilir, ancak kalan tüm testler geçerlidir. SharePoint yayımlama özelliğinin ek işlevleri sayfa yükleme sürelerini artırabilir, bu nedenle yalnızca CDN işlevselliğine izin vermek için etkinleştirilmemelidir.

>[!IMPORTANT]
>Test kuralları düzenli olarak eklenir ve güncelleştirilir, bu nedenle geçerli kurallar ve test sonuçlarına dahil edilen belirli bilgiler için lütfen aracın en son sürümüne bakın. Uzantılarınızı yöneterek sürümü doğrulayabilirsiniz ve uzantı bir güncelleştirmenin kullanılabilir olup olmadığını önerir.

## <a name="how-to-use-the-network-trace-tab-and-how-to-export-a-har-file"></a>Ağ İzleme sekmesini kullanma ve HAR dosyasını dışarı aktarma

**Ağ İzleme** sekmesi, hem sayfayı derleme istekleri hem de SharePoint alınan yanıtlar hakkında ayrıntılı bilgi sağlar.

1. **Kırmızı olarak işaretlenmiş öğe yükleme sürelerini arayın**. Her istek ve yanıt, aşağıdaki gecikme süresi ölçümlerini kullanarak genel sayfa performansı üzerindeki etkisini göstermek için renk kodludur:
    - Yeşil: \< 500ms
    - Sarı: 500-1000ms
    - Kırmızı: \> 1000ms

    > [!div class="mx-imgBorder"]
    > ![Ağ İzleme.](../media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    Yukarıda gösterilen resimde kırmızı öğe varsayılan sayfaya ait. Sayfa 1000ms (1 saniyeden kısa) olarak \< yüklenmediği sürece her zaman kırmızı gösterilir.

2. **Öğe yükleme sürelerini test edin**. Bazı durumlarda, öğeler tarayıcı tarafından önceden önbelleğe alınmış olduğundan zaman veya renk göstergesi olmaz. Bunu doğru şekilde test etmek için sayfayı açın, tarayıcı önbelleğini temizleyin ve ardından **Başlat'a** tıklayarak "soğuk" bir sayfa yüklemesini zorlayın ve ilk sayfa yükünün gerçek bir yansıması olun. Bu, sayfada hangi öğelerin önbelleğe alındığını belirlemeye de yardımcı olacağı için "sıcak" sayfa yüküyle karşılaştırılmalıdır.

3. **Sorunları araştırmaya yardımcı olabilecek diğer kişilerle ilgili ayrıntıları paylaşın**. Araçta sağlanan ayrıntıları veya bilgileri geliştiricilerinizle veya bir teknik destek görevlisiyle paylaşmak için ÖNERILEN yaklaşım **HTTP Arşivi'ne dışarı aktarmayı etkinleştir (HAR)** kullanmaktır. 

   > [!div class="mx-imgBorder"]
   > ![HAR'ye dışarı aktarmayı etkinleştirin.](../media/page-diagnostics-for-spo/pagediag-submithar.png)

Başlangıç'a tıklamadan önce bu özellik etkinleştirilmelidir. Bu, tarayıcınızda hata ayıklama modunu etkinleştirir. Daha sonra "Ağ İzleme" sekmesi aracılığıyla erişilebilen bir HTTP Arşiv dosyası (HAR) oluşturur. "HAR'ye Aktar"a tıkladığınızda dosya bilgisayarınıza indirilir ve ardından uygun şekilde paylaşabilirsiniz. Dosya F12 Geliştirici Araçları ve Fiddler gibi çeşitli hata ayıklama araçlarında açılabilir.

> [!div class="mx-imgBorder"]
> ![Ağ izleme.](../media/page-diagnostics-for-spo/pagediag-networktracehar.png)

> [!IMPORTANT]
> Bu sonuçlar URL'ler içerir ve PII (Kişisel Bilgiler) olarak sınıflandırılabilir. Bu bilgileri dağıtmadan önce kuruluşunuzun yönergelerine uyduğunuzdan emin olun.

## <a name="engaging-with-microsoft-support"></a>Microsoft Desteği ile etkileşime geçilmesi

Yalnızca doğrudan bir destek olayı üzerinde çalışırken kullanılması gereken **Microsoft Desteği düzeyinde bir özellik** dahil ettik. Bu özelliğin kullanılması, destek ekibi katılımı olmadan kullanıldığında size hiçbir fayda sağlamaz ve sayfanın önemli ölçüde daha yavaş performans göstermesini sağlayabilir. Hizmetteki günlüğe ek bilgiler eklendiğinden, araçta bu özellik kullanılırken ek bilgi yoktur.

Etkinleştirdiğiniz bildirilmesi ve sayfa performansınızın etkinken performansın 2-3 kat daha yavaş olması dışında hiçbir değişiklik görünmez. Yalnızca belirli bir sayfa ve etkin oturumla ilgili olacaktır. Bu nedenle, bu, yalnızca destekle etkin bir şekilde etkileşime geçtiğinde düzenli olarak kullanılmalıdır.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Microsoft Desteği düzeyi özelliğini etkinleştirmek için

1. SharePoint için Sayfa Tanılama aracını açın.
2. Klavyenizde **ALT-Shift-L tuşlarına** basın. Bu, **Destek günlüğünü etkinleştir** onay kutusunu görüntüler.
3. Onay kutusunu seçin ve ardından **Başlat'a** tıklayarak sayfayı yeniden yükleyin ve ayrıntılı günlük kaydı oluşturun.

   > [!div class="mx-imgBorder"]
   > ![Destek Seçeneği Etkin.](../media/page-diagnostics-for-spo/pagediag-support.png)
  
    CorrelationID değerini not edin (aracın en üstünde görüntülenir) ve tanılama oturumu hakkında ek bilgi toplamalarını sağlamak için destek temsilcinize sağlamanız gerekir.

## <a name="related-topics"></a>İlgili konular

[çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Office 365 performansını ayarlama](tune-microsoft-365-performance.md)

[Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md)