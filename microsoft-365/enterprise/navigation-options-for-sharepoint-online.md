---
title: SharePoint Online için gezinti seçenekleri
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Bu makalede, SharePoint Online'da SharePoint Yayımlama etkinleştirilmiş gezinti SharePoint açıklanmıştır.
ms.openlocfilehash: c59006db8505991bd41d29714caae144b284f07d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984461"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online için gezinti seçenekleri

Bu makalede, SharePoint Online'da SharePoint Yayımlama etkinleştirilmiş gezinti SharePoint açıklanmıştır. Gezinti seçimi ve yapılandırması, SharePoint Online'da sitelerin performansını ve ölçeklenebilirliğini önemli ölçüde etkiler. SharePoint Yayımlama sitesi şablonu, yalnızca merkezi bir portal için gerekli olduğunda ve yayımlama özelliği yalnızca belirli sitelerde etkinleştirildiyse ve ancak gerçekten gerekli olduğu zaman performansı yanlış kullanıldıklarında etkileyebilir.

>[!NOTE]
>Mega menü, basamaklı gezinti SharePoint hub gezintisi gibi modern gezinti seçeneklerini kullanıyorsanız, bu makale siteniz için geçerli değildir. Modern SharePoint yapıtları daha düz site hiyerarşisi ve merkez ve sözcük bir modelden yararlanmaktadır. Bu, yayımlama özelliğinin kullanımını GEREKTIRMEYEN birçok senaryoyu SharePoint sağlar.

## <a name="overview-of-navigation-options"></a>Gezinti seçeneklerine genel bakış

Gezinti sağlayıcısı yapılandırması sitenin tamamı için performansı önemli ölçüde etkileyebilir ve bir sitenin gereksinimlerine göre etkili bir şekilde ölçeklendirilen bir gezinti sağlayıcısı ve yapılandırması seçmek için dikkatli bir SharePoint alınması gerekir. İlk kullanılanın dışında iki gezinti sağlayıcısının yanı sıra özel gezinti uygulamaları vardır.

İlk seçenek olan [**Yapısal gezinti**](#using-structural-navigation-in-sharepoint-online), siteniz için yapısal gezinti önbelleğini SharePoint Online'da klasik SharePoint siteleri için önerilen **gezinti seçeneğidir**. Bu gezinti sağlayıcısı, gezinti öğelerini geçerli sitenin altında, isteğe bağlı olarak da geçerli siteyi ve bu sitenin öğelerini görüntüler. Güvenlik kırpma ve site yapısı numaralama gibi ek özellikler sağlar. Önbelleğe alma devre dışı bırakılmışsa, bu durum performansı ve ölçeklenebilirliği olumsuz etkiler ve azaltmaya tabi olabilir.

İkinci seçenek olan Yönetilen [**(Meta Veri) gezintisi**](#using-managed-navigation-and-metadata-in-sharepoint-online), Yönetilen Meta Veri terim kümesi kullanan gezinti öğelerini temsil eder. Güvenlik kırpmanın gerekli olmadığı sürece devre dışı bırakılabilir. Bu gezinti sağlayıcısı için güvenlik kırpma, varsayılan güvenli bir ayar olarak etkinleştirilir; bununla birlikte, gezinti öğeleri sitenin tüm kullanıcıları için çoğunlukla tutarlı olduğu için birçok site için güvenlik kırpma yükünün yükü gerekli değildir. Güvenlik kırpmayı devre dışı bırakmak için önerilen yapılandırmayla, bu gezinti sağlayıcısı site yapısını numaralama gerektirmez ve kabul edilebilir performans etkisiyle üst düzeyde ölçeklenebilirdir.

Gelen gezinti sağlayıcılarına ek olarak, birçok müşteri alternatif özel gezinti uygulamalarını başarıyla gerçekleştirdi. Bu [makaledeki Arama odaklı istemci tarafı betikleri](#using-search-driven-client-side-scripting) makalesine bakın.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Çevrimiçi gezinti seçeneklerinin Artıları SharePoint Eksileri

Aşağıdaki tabloda her seçeneğin artıları ve eksileri özetlenmiştir.

|Yapısal gezinti  |Yönetilen gezinti  |Arama odaklı gezinti  |Özel gezinti sağlayıcısı  |
|---------|---------|---------|---------|
|Profesyoneller:<br/><br/>Bakımı kolay<br/>Güvenlik kırpıldı<br/>İçerik değiştirilirken 24 saat içinde otomatik olarak  güncellemeler<br/>     |Profesyoneller:<br/><br/>Bakımı kolay<br/>|Profesyoneller:<br/><br/>Güvenlik kırpıldı<br/>Otomatik olarak siteler eklendikken güncelleştirmeler<br/>Hızlı yükleme süresi ve yerel olarak önbelleğe alınmış gezinti yapısı<br/>|Profesyoneller:<br/><br/>Daha geniş seçenek seçeneği<br/>Önbelleğe alma doğru kullanılırken hızlı yükleme<br/>Birçok seçenek iyi yanıt veren sayfa tasarımıyla iyi çalışır<br/>|
|Eksiler:<br/><br/>**Önbelleğe alma devre dışı bırakılmıştır, performansı etkiler**<br/>Azaltmaya tabi<br/>|Eksiler:<br/><br/>Site yapısını yansıtacak şekilde otomatik olarak güncelleştirilmez<br/>**Güvenlik kırpma etkinleştirildiğinde veya gezinti yapısı karmaşık** olduğunda performansı etkiler<br/>|Eksiler:<br/><br/>Siteleri kolayca sıralayabilme özelliği yok<br/>Ana sayfanın özelleştirilmesi gerekir (teknik beceriler gereklidir)<br/>|Eksiler:<br/><br/>Özel geliştirme gereklidir<br/>Azure gibi dış veri kaynağı / önbelleğinin depolanmış olması gerekir<br/>|

Siteniz için en uygun seçenek site gereksinimlerinize ve teknik yeteneklerinize bağlıdır. İçerik değiştirildiğinde otomatik olarak güncelleştirmeler kullanan, kullanımı kolay bir gezinti sağlayıcısını tercih ediyorsanız, önbelleğe alma etkinleştirilmiş yapısal [gezinti iyi bir](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) seçenektir.

>[!NOTE]
>Genel site yapısını daha hoş, hiyerarşik olmayan bir yapıya basitleştirerek modern SharePoint sitelerle aynı ilkeyi uygulamak, performansı iyileştirir ve modern sitelere SharePoint kolaylaştırır. Bunun anlamı, yüzlerce sitede (alt web) olan tek bir site koleksiyonu olması yerine, çok az alt sitesi (alt web) olan birçok site koleksiyonu olmasıdır.

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>SharePoint Online'da gezinti SharePoint çözümleme

[SharePoint için](./page-diagnostics-for-spo.md) Sayfa Tanılama aracı, hem Microsoft Edge Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen SharePoint Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç yalnızca SharePoint Online'da çalışır ve SharePoint sayfasında kullanılamaz.

Araç, önceden tanımlanmış bir dizi kurala karşı sayfanın nasıl bir performans göstermesini gösteren, analize alınan her sayfa için bir rapor üretir ve bir sınamanın sonuçları temel değerinin dışında kalıyorsa ayrıntılı bilgi görüntüler. SharePoint Online yöneticileri ve tasarımcıları, yeni sayfaların yayımlamadan önce en iyi duruma getirilmiş performans sorunlarını gidermek için bu aracı kullanabilir.

**Özel olarak, SPRequestDuration** sayfanın nasıl iş SharePoint kadar sürer. Yoğun gezinti (gezinti sayfaları dahil), karmaşık site hiyerarşileri ve diğer yapılandırma ve topoloji seçeneklerinin hepsi, daha uzun sürelere büyük ölçüde katkıda bulunabilirsiniz.

## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online'da yapısal gezintiyi kullanma

Bu, varsayılan olarak kullanılan ilk kullanımdan gezintidir ve en kolay çözümdür. Herhangi bir özelleştirme gerektirmez ve teknik olmayan bir kullanıcı da ayarlar sayfasında kolayca öğe ekleyebilir, öğeleri gizleebilir ve gezintiyi yönetebilir. Önbelleğe [almayı etkinleştirmenizi öneririz](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), aksi takdirde pahalı bir performans satın alma işleminin olmasıdır.

### <a name="how-to-implement-structural-navigation-caching"></a>Yapısal gezinti önbelleği uygulama

**Site Gezintisi Ayarlar** >  **Look ve** **FeelNavigation** >  altında, genel gezinti veya geçerli gezinti için yapısal gezintinin seçili olup olduğunu doğrulayan bir araçtır. Sayfaları göster **seçeneği performansı** olumsuz etkiler.

![Alt Siteleri Göster'in seçili olduğu yapısal gezinti.](../media/SPONavOptionsStructuredShowSubsites.png)

Önbelleğe Alma koleksiyonu düzeyinde ve site düzeyinde etkinleştirilebilir veya devre dışı bırakılabilir ve her ikisi için de varsayılan olarak etkindir. Site koleksiyonu düzeyinde etkinleştirmek için Site Koleksiyonu Yönetimi **Site Ayarlar** >  **Site Koleksiyonu** >  Gezintisi'nin **altında Önbelleğe** almayı etkinleştir **kutusunu işaretleyin**.

![Site düzeyinde önbelleğe almayı etkinleştirin.](../media/structural-nav/structural-nav-caching-site-coll.png)

Site düzeyinde etkinleştirmek için, **Site Özellikleri'Ayarlar** >  **Gerekleme'nin** altında Önbelleğe almayı **etkinleştir kutusunu işaretleyin**.

![Site düzeyinde önbelleğe almayı etkinleştirin.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online'da yönetilen gezintiyi ve meta verileri kullanma

Yönetilen gezinti, yapısal gezintiyle aynı işlevlerin çoğunu yeniden oluşturmak için kullanabileceğiniz, ilk kullanımdan çıkma seçeneklerden biridir. Yönetilen meta veriler, güvenlik kırpmanın etkinleştirilmesi veya devre dışı bırakılabilir. Güvenlik kırpma devre dışı bırakıldığında, yönetilen gezinti oldukça verimlidir çünkü sabit sayıda sunucu çağrısı içeren tüm gezinti bağlantılarını yükler. Bununla birlikte, güvenlik kırpmanın etkinleştirilmesi, yönetilen gezintinin performans avantajlarından bazılarını olumsuz artırır.

Güvenlik kırpmayı etkinleştirmeniz gerekirse şunları öneririz:

- Tüm kolay URL bağlantılarını basit bağlantılara güncelleştirin
- Gerekli güvenlik kırpma düğümlerini kolay URL'ler olarak ekleme
- Gezinti öğelerinin sayısını 100'den fazla değil ve 3 düzeyden daha derinle sınırlama

Gezinti yapısı genellikle sitenin tüm kullanıcıları için tutarlı olduğu için birçok sitede güvenlik kırpması gerektirmez. Güvenlik kırpma devre dışı bırakılırsa ve gezintiye tüm kullanıcıların erişeliklerini sağymayacak bir bağlantı eklenirse, bağlantı yine de gösterir ancak erişim reddedildi iletisine yol gösterir. İçeriklere yanlışlıkla erişim riski yoktur.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Yönetilen gezintiyi ve sonuçları uygulama

Yönetilen gezintinin ayrıntıları hakkında docs.microsoft.com hakkında birçok makale bulunmaktadır. Örneğin, [SharePoint Server'da yönetilen gezintiye genel bakış.](/sharepoint/administration/overview-of-managed-navigation)

Yönetilen gezintiyi uygulamak için, sitenin gezinti yapısına karşılık gelen URL'ler için terimler ayarlayın. Yönetilen gezinti, birçok durumda yapısal gezintinin yerini alacak şekilde el ile bile ayarlanabilir. Örneğin:

![SharePoint Online site yapısı.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Arama odaklı istemci tarafı betiklerini kullanma

Ortak bir özel gezinti uygulaması sınıfı, yerel gezinti düğümleri önbelleğini depolayan istemci tarafından işlenen tasarım desenlerini sağlar.

Bu gezinti sağlayıcılarının birkaç önemli avantajı vardır:

- Genel olarak iyi yanıt veren sayfa tasarımlarla iyi çalışırlar.
- Bunlar aşırı ölçeklendirilebilir ve performans gösterirler çünkü kaynak maliyeti yoktur (ve zaman aşımı sonrasında arka planda yenilenirler).
- Bu gezinti sağlayıcıları, basit statik yapılandırmalardan çeşitli dinamik veri sağlayıcılarına kadar çeşitli stratejiler kullanarak gezinti verilerini alabilir.

Veri sağlayıcısına örnek olarak, gezinti düğümlerini numaralandırma ve güvenlik kırpmayı verimli bir şekilde işleme esnekliği sağlayan Arama odaklı gezintiyi kullanabilirsiniz.

Özel gezinti sağlayıcıları oluşturmak için diğer popüler **seçenekler vardır**. Özel gezinti [sağlayıcısı oluşturma konusunda SharePoint için lütfen](/sharepoint/dev/solution-guidance/portal-navigation) Web Sitem Online portalları için Gezinti çözümleri'ni gözden geçin.

Arama'ı kullanarak, sürekli gezinmeyi kullanarak arka planda yerleşik olarak yer alan dizinlerden yararlan bulabilirsiniz. Arama sonuçları arama dizininden çekilir ve sonuçlar güvenlikle birlikte kırpıldı. Bu genellikle, güvenlik kırpma gerektiğinde, ilk kullanıma kullanıman gezinti sağlayıcılarından daha hızlıdır. Özellikle karmaşık bir site yapınız varsa, yapısal gezinti aramanızı kullanmak sayfa yükleme sürelerini önemli ölçüde hızlandıracak. Yönetilen gezinti üzerinden bunun en büyük avantajı, güvenlik kırpmadan yararlanmadır.

Bu yaklaşım, özel bir ana sayfa oluşturmayı ve ilk önce gezinti kodunu özel HTML'ye değiştirmeyi içerir. Dosyada gezinti kodunu değiştirmek için aşağıdaki örnekte belirtilen bu yordamı izleyin `seattle.html`. Bu örnekte, dosyayı açar ve tüm `seattle.html` öğeyi özel HTML koduyla `id="DeltaTopNavigation"` değiştirirsiniz.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Örnek: Ana sayfada ilk önce kullanılan gezinti kodunu değiştirme

1. Site Sayfası sayfasına Ayarlar gidin.
2. Ana Sayfalar'a tıklayarak ana sayfa **galerisini açın**.
3. Buradan kitaplıkta gezinerek dosyayı indirebilirsiniz `seattle.master`.
4. Aşağıdaki ekran görüntüsinde, metin düzenleyicisi kullanarak kodu düzenleyin ve kod bloğunı silin.<br/>![Gösterilen kod bloğuni silin.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Etiketler arasındaki kodu kaldırın `<SharePoint:AjaxDelta id="DeltaTopNavigation">` ve `<\SharePoint:AjaxDelta>` aşağıdaki kod parçacığıyla değiştirin:<br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. Başlangıçtaki yükleme resmi bağlantısı etiketinde URL'yi, site koleksiyonu yükleme resminin bağlantısıyla değiştirin. Değişikliklerinizi yapın ve dosyayı yeniden adlandırarak ana sayfa galerisine yükleyin. Bu, yeni bir .master dosyası üretir.<br/>
7. Bu HTML, JavaScript kodundan döndürülen arama sonuçları tarafından doldurulacak temel işaretlemedir. Aşağıdaki parçacıkta da göstermek istediğiniz var kök = "site koleksiyonu URL'si" değerini değiştirmek için kodu düzenlemeniz gerekir:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Sonuçlar self.nodes dizisine atanır ve çıktıyı kendi kendine.hiyerarşiye atamak için linq.js kullanılarak nesnelerden bir hiyerarşi yerleşik olarak bulunur. Bu dizi, HTML'ye bağlı olan nesnedir. Bu, öz nesneyi ko.applyBinding() işlevine ileterek toggleView() işlevinde yapılır.<br/>Bu da hiyerarşi dizisinin aşağıdaki HTML'ye bağlı olmasına neden olur:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

İşlevde yapılan alt `mouseenter` `mouseexit` site açılan menülerini işlemek için olay işleyicileri ve bunlar en üst düzey gezintiye `addEventsToElements()` eklenir.

Karmaşık gezinti örneğimizde, yerel önbelleğe almadan temiz bir sayfa yükü, yönetilen gezinti yaklaşımına benzer bir sonuç elde etmek için sunucuya harcanan zamanı karşılaştırma yapısal gezinti bölmesinden kestiğini gösteriyor.

### <a name="about-the-javascript-file"></a>JavaScript dosyası hakkında...

>[!NOTE]
>Özel JavaScript kullanıyorsanız, ortak javascript CDN ve dosyanın farklı bir konumda CDN olun.

JavaScript dosyasının tamamı aşağıdaki gibidir:

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

Yukarıda işlevde gösterilen kodu özetlemek `jQuery $(document).ready` için, bir oluşturuldu `viewModel object` ve sonra bu nesne `loadNavigationNodes()` üzerindeki işlev çağrılır. Bu işlev, istemci tarayıcısının HTML5 yerel depolamasında depolanan önceden yerleşik gezinti hiyerarşisini yükler veya işlevi arar `queryRemoteInterface()`.

`QueryRemoteInterface()` betikte daha önce tanımlanan `getRequest()` sorgu parametresiyle işlevi kullanarak bir istek oluşturur ve sonra da sunucudan veri döndürür. Bu veriler temelde, site koleksiyonunda çeşitli özelliklere sahip veri aktarma nesneleri olarak temsil edilen tüm sitelerin bir dizisidir.

Daha sonra bu veriler `SPO.Models.NavigationNode` `Knockout.js` önceden tanımlanmış olan nesnelere ayrıştırılabilir ve bunlar, değerleri daha önce tanımlandığı HTML'e bağleyerek, gözlemlenebilir özellikler oluşturmak için kullanılır.

Bundan sonra nesneler bir sonuç dizisine yer verir. Bu dizi, Açılır öğe kullanılarak JSON'da ayrıştırıldı ve gelecek sayfa yüklemelerinde daha iyi performans için yerel tarayıcı depolamasında depolanır.

### <a name="benefits-of-this-approach"></a>Bu yaklaşımın avantajları

Bu yaklaşımın en [büyük](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) faydalarından biri, HTML5 yerel depolama alanı kullanılarak gezintinin, sayfayı bir sonraki yükleykisinde kullanıcı için yerel olarak depolanmasıdır. Yapısal gezinti için arama API'sini kullanmayla ilgili önemli performans iyileştirmeleri elde ediyor; bununla birlikte, bu işlevselliği yürütmek ve özelleştirmek için bazı teknik özellikler de gerektir.

Örnek [uygulama içinde](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), siteler ilk ve son kullanılan yapısal gezintiyle aynı şekilde sıralandı; alfabetik sıra. Bu düzenden sapmak istediysiniz, geliştirmeniz ve sürdürmeniz daha karmaşık olur. Ayrıca, bu yaklaşım desteklenen ana sayfalardan sapmayı gerektirir. Özel ana sayfa korunamazsa, siteniz Microsoft'un ana sayfalarda edatları ve geliştirmeleri kaçıracak.

Yukarıdaki [kod aşağıdaki](#about-the-javascript-file) bağımlılıklara sahip:

- jQuery - https://jquery.com/
- NakavtJ'ler - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/, veya github.com/neuecc/linq.js

LinqJS'nin geçerli sürümü, yukarıdaki kodda kullanılan ByHierarchy yöntemini içermemektedir ve gezinti kodunu bozar. Bunu düzeltmek için dosya dosyasına satırdan Linq.js yöntemini ekleyin `Flatten: function ()`.

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>İlgili konular

[SharePoint Server'da yönetilen gezintiye genel bakış](/sharepoint/administration/overview-of-managed-navigation)

[Yapısal gezinti önbelleğe alma ve performans](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)