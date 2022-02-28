---
title: SharePoint Online için Sayfa Tanılama aracını kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: SharePoint Online modern portalı ve klasik yayımlama sayfalarını, önceden tanımlanmış bir performans ölçütleri kümesiyle çözümlemek için SharePoint için Sayfa Tanılama aracını kullanın.
ms.openlocfilehash: 7e1931b7cdc661b5e0a6ed8751a26f8a77e4bc2e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986522"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Yeni Araç için Sayfa Tanılama SharePoint kullanma

Bu makalede, SharePoint Online modern ve klasik  site sayfalarını önceden tanımlanmış bir performans ölçütleri kümesiyle çözümlemek amacıyla SharePoint için Sayfa Tanılama aracının nasıl kullanımı açıklanmıştır.

Aşağıdakiler için Sayfa SharePoint aracı şu için yüklenebilirsiniz:

- **Microsoft Edge** [(Edge uzantısı)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(Chrome uzantısı)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>Sürüm **2.0.0** ve sonraki sürümler, klasik site sayfalarının yanı sıra modern sayfalar için de destek içerir. Aracın hangi sürümünü kullanmakta olduğunu emin değilseniz, sürümü doğrulayın ve Hakkında bağlantısını veya üç noktayı  (...) seçin. **Aracı kullanırken her zaman en son** sürüme güncelleştirin.

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç yalnızca SharePoint Online'da çalışır ve SharePoint sayfasında kullanılamaz.

Araç, önceden tanımlanmış bir dizi kurala karşı sayfanın nasıl bir performans göstermesini gösteren, analize alınan her sayfa için bir rapor üretir ve bir sınamanın sonuçları temel değerinin dışında kalıyorsa ayrıntılı bilgi görüntüler. SharePoint Online yöneticileri ve tasarımcıları bu aracı kullanarak performans sorunlarını giderebilir ve yeni sayfaların yayımlamadan önce en iyi duruma getirilmiş olduğundan emin olabilir.

Sayfa Tanılama aracı, *allitems.aspx SharePoint sharepoint.aspx* gibi sistem sayfalarını değil, yalnızca site sayfalarını analiz *etmek için tasarlanmıştır*. Aracı bir sistem sayfasında veya site dışında başka bir sayfada çalıştırmayı denersiniz, aracın bu tür bir sayfa için çalıştırılamayayan bir hata iletisi alırsınız.

> [!div class="mx-imgBorder"]
> ![Çalışma sayfası üzerinde SharePoint gerekir.](../media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Kitaplıkları veya sistem sayfalarını değerlendirirken hiçbir değer almama nedeniyle bu araçta hata değildir. Lütfen aracı kullanmak SharePoint site sayfasına gidin. Bu hata bir SharePoint oluşursa, meta etiketlerin SharePoint için lütfen ana sayfayı kontrol edin.

Araç hakkında geri bildirim sağlamak için, aracın sağ üst köşesindeki üç noktayı seçin ve ardından Geri bildirim [ver'i seçin](https://go.microsoft.com/fwlink/?linkid=874109).

> [!div class="mx-imgBorder"]
> ![Geri bildirim gönderin.](../media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Office 365 için Sayfa SharePoint aracını yükleme

Bu bölümdeki yükleme yordamı hem Chrome hem de Microsoft Edge için kullanılabilir.

> [!IMPORTANT]
> Microsoft, SharePoint için Sayfa Tanılama aracı tarafından analiz edilir verileri veya sayfa içeriğini okumaz ve hiçbir kişisel bilgi, web sitesi veya indirme bilgisi yakalamaz. Araç tarafından Microsoft'a kaydedilen tek tanımlayıcı bilgiler kiracı adı, başarısız olan kuralların sayısı ve aracın çalıştırılacağı tarih ve saatdir. Bu bilgiler, Microsoft tarafından modern portal ve yayımlama sitesi kullanım eğilimlerini ve yaygın performans sorunlarını daha iyi anlamak için kullanılır.

1. Microsoft Edge (Edge uzantısı) veya **Chrome** [(](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)Chrome uzantısı) **için SharePoint** Tanılama [aracını yükleyin](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi). Lütfen mağazanın açıklama sayfasında sağlanan Kullanıcı Gizlilik İlkesi'ne bakın. Aracı tarayıcınıza eklerken aşağıdaki izin bildirimlerini görüyorsunuz.

    > [!div class="mx-imgBorder"]
    > ![Uzantı izinleri.](../media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Bu bildirim, sayfada yer alan web bölümlerine ve özelleştirmelere bağlı olarak SharePoint konumlardan içerik içermesi nedeniyle görüntülenir. Başka bir ifadeyle, başlat düğmesine tıkıldığında aracın istekleri ve yanıtları okuması ve yalnızca SharePoint durumda olan etkin sekmede olması gerekir. Bu bilgiler web tarayıcısı tarafından yerel olarak yakalanır ve aracın Ağ izleme **sekmesindeki JSON'a** Aktar veya **HAR'ya** Aktar düğmesi aracılığıyla bu bilgilere erişebilirsiniz. Bilgiler Microsoft tarafından gönderilmez veya **gönderilmez.**  (Araç, burada erişilebilir Microsoft gizlilik ilkesine [uyar](https://go.microsoft.com/fwlink/p/?linkid=857875).)

    _İndirmelerinizi yönetme izni_, aracın **JSON'a Aktar işlevinin kullanımını** kapsar. Sonuçlar URL'leri içerdiği ve PII (Kişisel Olarak Tanımlayıcı Bilgiler) olarak sınıflandırılabilen JSON dosyasını kuruluş dışında paylaşmadan önce lütfen şirketinizin kendi gizlilik yönergelerini izleyin.
1. Aracı Incognito veya InPrivate modunda kullanmak için tarayıcınızdaki yordamı izleyin:
    1. Daha Microsoft Edge'de **Uzantılar'a** gidin veya URL _edge://extensions_ uzantının **ayrıntıları'ı** seçin. Uzantı ayarlarında **InPrivate içinde izin ver onay kutusunu seçin**.
    1. Chrome'da **Uzantılar'a gidin** ya da URL _chrome://extensions_ uzantı için **Ayrıntılar'ı** seçin. Uzantı ayarlarında, **Incognito'da izin ver kaydırıcısını seçin**.
1. SharePoint SharePoint Online'da SharePoint istediğiniz site sayfasına gidin. Sayfalarda öğelerin "yüklenmesini geciktirme"ye izin verildi; Bu nedenle araç otomatik olarak durmayacaktır (bu, tüm sayfa yükleme senaryolarına uyum sağlayacak şekilde tasarım gereğidir). Koleksiyonu durdurmak için Durdur'a **seçin**. Veri toplamayı durdurmadan önce sayfa yüklemenin tamamlandığından emin olun; yoksa yalnızca kısmi bir izleme yakalayabilirsiniz.
1. Uzantının araç çubuğu düğmesine tıklayın ![Sayfa Tanılama SharePoint.](../media/page-diagnostics-for-spo/pagediag-icon32.png) seçin; aşağıdaki uzantı açılan penceresi gösterilir:

    ![Sayfa Tanılama aracı Açılan Menüsü.](../media/page-diagnostics-for-spo/pagediag-Landing.png)

Çözümleme **için veri** toplamaya başlamak için Başlat'ı seçin.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Bu sorun için Sayfa Tanılama aracında SharePoint.

1. Aşağıdaki bağlantıları bulmak için, aracın sağ üst köşesindeki üç noktayı (...) tıklatın:
   1. Ek **kaynaklar bağlantısı** , bu makalenin bağlantısını da içeren araçla ilgili genel rehberlik ve ayrıntılar sağlar.
   1. Geri **bildirim ver** bağlantısı, Geri bildirim siteleri SharePoint _Ortak Çalışma Kullanıcısı Sesi sitesine bir bağlantı_ sağlar.
   1. Hakkında **bağlantısı** , aracın şu anda yüklü olan sürümünü ve aracın üçüncü taraf bildirimine doğrudan bağlantıyı içerir.  
1. **Bağıntı Kimliği, SPRequestDuration, SPIISLatency****, Sayfa** yükleme süresi ve **URL** ayrıntıları bilgilendirme amaçlıdır ve birkaç amaçla kullanılabilir.

    > [!div class="mx-imgBorder"]
    > ![Sayfa tanılama ayrıntıları.](../media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **Bağıntı** Kimliği, Microsoft Desteği ile çalışırken belirli bir sayfa için ek tanılama verileri toplamalarına olanak sağlayan önemli bir öğedir.
   - **SPRequestDuration**, sayfanın SharePoint alınma zamanıdır. Yapısal gezinti, büyük resimler, çok sayıda API çağrısının hepsi daha uzun süreye katkı sağlar.
   - **SPIISLatency**, SharePoint Online'ın sayfayı yüklemeye başlaması için SharePoint milisaniye cinsinden süredir. Bu değer, web uygulamasının yanıtlaması için gereken saati dahil değildir.
   - **Sayfa yükleme süresi** , isteğin işlenen ve tarayıcıda işlenen yanıt süresine kadar sayfa tarafından kaydedilen toplam süredir. Bu değer ağ gecikme süresi, bilgisayarın performansı ve tarayıcının sayfayı yükleme süresi gibi çeşitli faktörlerden etkilenir.
   - Sayfa **URL'si** (Tekdüz Kaynak Konum Belirleyicisi), geçerli sayfanın web adresidir.

1. Tanılama [**testleri sekmesi**](#how-to-use-the-diagnostic-tests-tab) çözümleme sonuçlarını üç kategoride görüntüler; **Herhangi bir işlem gerekmez**, **Geliştirme fırsatları ve** **Dikkat gerekmez**. Her test sonucu, aşağıdaki tabloda açıklandığı gibi, bu kategorilerden birinde yer alan bir öğeyle temsil edildi:

    |Kategori  |Renk  |Açıklama  |
    |---------|---------|---------|
    |**Dikkat** |Kırmızı |Sınama sonucu temel değerin dışında düştüğünden sayfa performansını etkiler. Düzeltme yönergelerini izleyin.|
    |**Geliştirme fırsatları** |Sarı |Test sonucu temel değerin dışında olur ve performans sorunlarına katkıda bulunuyor olabilir. Teste özgü ölçütler uygulanabilir.|
    |**Herhangi bir işlem gerekmez** |Yeşil |Test sonucu, sınamanın temel değerine denktir.|

    > [!div class="mx-imgBorder"]
    > ![Sayfa tanılama'yı seçin.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Ağ [**izleme sekmesi**](#how-to-use-the-network-trace-tab-and-how-to-export-a-har-file) , sayfa oluşturma istekleri ve yanıtları hakkında ayrıntılar sağlar.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Tanılama testleri sekmesini kullanma

SharePoint için Sayfa Tanılama aracıyla bir SharePoint modern portal sayfasını veya klasik yayımlama sitesi sayfasını çözümlerken, sonuçlar temel değerlerle sonuçları karşılaştıran ve Tanılama testleri sekmesinde görüntülenen önceden tanımlanmış kurallar kullanılarak analiz edilir. Bazı testlere yönelik kurallar, belirli  performansa bağlı olarak modern portal ve klasik yayımlama sitelerinde farklı temel değerler kullanabilir.  özellikler ikisi arasında farklılık gösterir.

Geliştirme fırsatları veya Dikkat gereken kategorilerde gösterilen test  sonuçları, önerilen uygulamalara karşı gözden geçirilecek alanları gösterir ve sonuç hakkında ek bilgi görüntülemek için seçilebilir. Her öğenin ayrıntıları, sizi _testle_ ilgili doğrudan ilgili kılavuza götüren Daha fazla bilgi bağlantısı içerir. Eylem gerekmez kategorisinde gösterilen **test** sonuçları ilgili kurala uyumluluğu gösterir ve seçildiğinde ek ayrıntılar görüntülemez.

Tanılama testleri sekmesindeki bilgiler sayfaların nasıl tasarla ilgili olduğunu size söylemez, ancak sayfa performansını etki etkileyen faktörleri vurgular. Bazı sayfa işlevleri ve özelleştirmelerinin sayfa performansı üzerinde kaçınılmaz bir etkisi vardır ve etkisinin önemli olması durumda olası düzeltme veya sayfadan eksiklik açısından gözden geçirilemeleri gerekir.

Kırmızı veya sarı sonuçlar, verileri çok sık yenilene web bölümlerini de gösteriyor olabilir. Örneğin, şirket haberleri her saniye güncelleştirilmez ama özel web bölümleri genellikle genel kullanıcı deneyimini geliştiren önbellek öğeleri uygulamak yerine en son haberleri her saniyeye getirmek için yerleşik olarak gelir. Sayfaya web bölümleri dahil etmenin genellikle, kullanılabilen her parametrenin amacına uygun olarak ayar olduğundan emin olmak için, kullanılabilir parametrelerin değerini değerlendirerek, performans etkilerini azaltmanın genellikle basit yolları olduğunu unutmayın.

>[!NOTE]
>Yayımlama özelliğinin etkinleştirilmemiş klasik ekip siteleri CDN'lerden kullanılamaz. Aracı bu sitelerde çalıştıracaksanız, CDN testinin başarısız olması gerekir ve yoksayılabilir, ancak kalan tüm testler uygulanabilir. Yayımlama özelliğinin ek SharePoint, sayfa yükleme süreleri artabilir, bu nedenle yalnızca bu işlevlerin etkinleştirilmesine izin CDN değil.

>[!IMPORTANT]
>Test kuralları düzenli olarak eklenir ve güncelleştirilir; bu nedenle geçerli kurallar ve test sonuçlarına eklenen belirli bilgilerle ilgili ayrıntılar için lütfen aracın en son sürümüne bakın. Uzantılarınızı yöneterek sürümü doğrulayabilirsiniz ve uzantıda bir güncelleştirmenin mevcut olup olmadığı önerilmektedir.

## <a name="how-to-use-the-network-trace-tab-and-how-to-export-a-har-file"></a>Ağ İzleme sekmesini kullanma ve HAR dosyasını dışarı aktarma

Ağ **İzleme sekmesi**, sayfayı oluşturma istekleri ve siteden alınan yanıtlar hakkında ayrıntılı bilgi SharePoint.

1. **Kırmızı olarak işaretlenen öğe yükleme sürelerini bakın**. Her istek ve yanıt, aşağıdaki gecikme ölçümleri kullanılarak genel sayfa performansı üzerindeki etkisini belirtmek için renk kodlu olarak görüntülenir:
    - Yeşil: \< 500ms
    - Sarı: 500-1000ms
    - Kırmızı: \> 1000ms

    > [!div class="mx-imgBorder"]
    > ![Ağ İzleme.](../media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    Yukarıda gösterilen resimde, kırmızı öğe varsayılan sayfayı gösterir. Sayfa 1000m'de \< (1 saniyeden az) yük olmadığı sürece her zaman kırmızı görünür.

2. **Öğe yükleme zamanlarını sınayın**. Bazı durumlarda, öğeler tarayıcı tarafından önceden önbelleğe alınmış olduğundan saat veya renk göstergesi olmaz. Bunu doğru test etmek için sayfayı açın, tarayıcı önbelleğini temizleyin ve ardından Başlat'a tıklayın. Bu, "soğuk" sayfa yüklemesini zorlar ve ilk sayfa yüklemenin gerçek yansımasını sağlar. Bu daha sonra sayfada hangi öğelerin önbelleğe alınarak önbelleğe alınarak belirlenecek olması gerektiği için "sıcak" sayfa yüküyle karşılaştırılamaz.

3. **İlgili ayrıntıları, sorunları araştırmanıza yardımcı olacak diğerleriyle paylaşın**. Araçta sağlanan ayrıntıları veya bilgileri geliştiricileriniz veya teknik destek kişileriyle paylaşmak için, **HTTP Arşive (HAR)** dışarı aktarmayı etkinleştir seçeneği önerilen yaklaşımdır. 

   > [!div class="mx-imgBorder"]
   > ![HAR'ya dışarı aktarmayı etkinleştirin.](../media/page-diagnostics-for-spo/pagediag-submithar.png)

Bu seçeneğin Başlat'a tıklamadan önce etkinleştirilmesi gerekir ve bu da tarayıcınızda hata ayıklama modunu etkinleştirir. Bir HTTP Arşiv dosyası (HAR) oluşturulur ve bu dosyaya "Ağ İzleme" sekmesi üzerinden erişilebilir. "HAR Dışarı Aktar" öğesini tıklatın; dosyayı bilgisayarınıza indirir ve ardından uygun şekilde paylaşabilirsiniz. Dosya, F12 Geliştirici Araçları ve Fiddler gibi çeşitli hata ayıklama araçlarında açılabilir.

> [!div class="mx-imgBorder"]
> ![Ağ izleme.](../media/page-diagnostics-for-spo/pagediag-networktracehar.png)

> [!IMPORTANT]
> Bu sonuçlar URL'leri içerir ve PII (Kişisel Olarak Tanımlayıcı Bilgiler) olarak sınıflandırılabilir. Bu bilgileri dağıtmadan önce, kuruluşun yönergelerine uymayı unutmayın.

## <a name="engaging-with-microsoft-support"></a>Microsoft Desteği ile cazip hale

Yalnızca bir destek **durumu üzerinde doğrudan** çalışırken kullanılması gereken bir Microsoft Destek düzeyi özelliği dahil edildi. Bu özelliği kullanmak, destek ekibi katılımı olmadan kullanılırken size hiçbir avantaj sağlamaz ve sayfanın çok daha yavaş çalışmasına neden olabilir. Bu özelliğin araçta kullanımıyla ilgili ek bilgi yoktur, çünkü ek bilgiler hizmette günlüğe eklenir.

Hiçbir değişiklik olmaz, ancak bunu etkinleştirmiş olduğunuz size bildirilecek ve sayfa performansınız 2-3 kat daha yavaş performansla 2-3 kez daha düşük olur. Yalnızca belirli sayfayla ve o etkin oturumla ilgili olur. Bu nedenle, bu ancak ancak etkin bir şekilde destekle meşgul olduğunda kullanılmalıdır.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Microsoft Destek düzeyi özelliğini etkinleştirmek için

1. Bu sorun için Sayfa Tanılama SharePoint açın.
2. Klavyenizde **ALT-Shift-L tuşlarına basın**. Bu, Destek günlüğünü **etkinleştir onay kutusunu** görüntüler.
3. Onay kutusunu seçin ve sonra **Başlat'a** tıklarsanız sayfayı yeniden yükleyin ve ayrıntılı günlük üretin.

   > [!div class="mx-imgBorder"]
   > ![Destek Seçeneği Etkin.](../media/page-diagnostics-for-spo/pagediag-support.png)
  
    Bağıntı Kimliği'ne (aracın en üstünde görüntülenir) dikkat edin ve tanılama oturumu hakkında ek bilgi toplamalarını sağlamak için destek temsilcinize bunu sağlayın.

## <a name="related-topics"></a>İlgili konular

[Çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)

[Modern deneyimde SharePoint deneyimi](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)