---
title: SharePoint Online için gezinti seçenekleri
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, SharePoint Online'da SharePoint Yayımlama'nın etkinleştirildiği gezinti seçenekleri siteleri açıklanmaktadır.
ms.openlocfilehash: 67bf1c854d97cf254d1484151987a87853e1ae9d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101193"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online için gezinti seçenekleri

Bu makalede, SharePoint Online'da SharePoint Yayımlama'nın etkinleştirildiği gezinti seçenekleri siteleri açıklanmaktadır. Gezinti seçimi ve yapılandırması, SharePoint Online'daki sitelerin performansını ve ölçeklenebilirliğini önemli ölçüde etkiler. SharePoint Yayımlama sitesi şablonu yalnızca merkezi bir portal için gerekliyse ve yayımlama özelliği yalnızca belirli sitelerde etkinleştirilmelidir ve yalnızca yanlış kullanıldığında performansı etkileyeebileceği için kesinlikle gerekli olduğunda kullanılmalıdır.

>[!NOTE]
>Mega menü, basamaklı gezinti veya hub gezintisi gibi modern SharePoint gezinti seçeneklerini kullanıyorsanız, bu makale siteniz için geçerli değildir. Modern SharePoint site mimarileri daha düzleştirilmiş bir site hiyerarşisi ve merkez-uç modelinden yararlanıyor. Bu, SharePoint Yayımlama özelliğinin kullanılmasını gerektirmeyen birçok senaryonun gerçekleştirilmesini sağlar.

## <a name="overview-of-navigation-options"></a>Gezinti seçeneklerine genel bakış

Gezinti sağlayıcısı yapılandırması tüm sitenin performansını önemli ölçüde etkileyebilir ve SharePoint sitenin gereksinimleri için etkili bir şekilde ölçeklendirilen bir gezinti sağlayıcısı ve yapılandırma seçmek için dikkatli bir şekilde dikkat edilmelidir. kullanıma uygun iki gezinti sağlayıcısının yanı sıra özel gezinti uygulamaları da vardır.

İlk seçenek [**olan Yapısal gezinti**](#using-structural-navigation-in-sharepoint-online), **siteniz için yapısal gezinti önbelleğini açarsanız** klasik SharePoint siteleri için SharePoint Online'da önerilen gezinti seçeneğidir. Bu gezinti sağlayıcısı, geçerli sitenin altındaki gezinti öğelerini ve isteğe bağlı olarak geçerli siteyi ve eşdüzey öğelerini görüntüler. Güvenlik kırpması ve site yapısı numaralandırması gibi ek özellikler sağlar. Önbelleğe alma devre dışı bırakılırsa, bu durum performansı ve ölçeklenebilirliği olumsuz etkiler ve azaltmaya tabi olabilir.

İkinci seçenek olan [**Yönetilen (Meta Veri) gezintisi**](#using-managed-navigation-and-metadata-in-sharepoint-online), Yönetilen Meta Veri terim kümesi kullanan gezinti öğelerini temsil eder. Gerekmedikçe güvenlik kırpmanın devre dışı bırakılması önerilir. Güvenlik kırpması, bu gezinti sağlayıcısı için varsayılan olarak güvenli bir ayar olarak etkinleştirilir; ancak, gezinti öğeleri genellikle sitenin tüm kullanıcıları için tutarlı olduğundan, birçok site güvenlik kırpma ek yükü gerektirmez. Güvenlik kırpmayı devre dışı bırakmak için önerilen yapılandırmayla, bu gezinti sağlayıcısı site yapısını listelemeyi gerektirmez ve kabul edilebilir performans etkisiyle yüksek oranda ölçeklenebilir.

Kullanıma sunulan gezinti sağlayıcılarına ek olarak, birçok müşteri alternatif özel gezinti uygulamalarını başarıyla uyguladı. Bu makaledeki [Arama temelli istemci tarafı betiği oluşturma](#using-search-driven-client-side-scripting) bölümüne bakın.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>SharePoint Çevrimiçi gezinti seçeneklerinin Avantajları ve Dezavantajları

Aşağıdaki tabloda her seçeneğin artıları ve eksileri özetlemektedir.

|Yapısal gezinti  |Yönetilen gezinti  |Arama temelli gezinti  |Özel gezinti sağlayıcısı  |
|---------|---------|---------|---------|
|Profesyonel:<br/><br/>Bakımı kolay<br/>Güvenlik kırpıldı<br/>İçerik değiştirildiğinde 24 saat içinde otomatik olarak güncelleştirilir<br/>     |Profesyonel:<br/><br/>Bakımı kolay<br/>|Profesyonel:<br/><br/>Güvenlik kırpıldı<br/>Siteler eklendikçe otomatik olarak güncelleştirilir<br/>Hızlı yükleme süresi ve yerel olarak önbelleğe alınmış gezinti yapısı<br/>|Profesyonel:<br/><br/>Daha geniş seçenek seçenekleri<br/>Önbelleğe alma doğru kullanıldığında hızlı yükleme<br/>Hızlı yanıt veren sayfa tasarımıyla birçok seçenek iyi çalışır<br/>|
|Eksi -lerini:<br/><br/>**Önbelleğe alma devre dışı bırakılırsa performansı etkiler**<br/>Azaltmaya tabi<br/>|Eksi -lerini:<br/><br/>Site yapısını yansıtacak şekilde otomatik olarak güncelleştirilmez<br/>**Güvenlik kırpma etkinse** veya gezinti yapısı karmaşıksa performansı etkiler<br/>|Eksi -lerini:<br/><br/>Siteleri kolayca sipariş etme olanağı yok<br/>Ana sayfanın özelleştirilmesini gerektirir (teknik beceriler gereklidir)<br/>|Eksi -lerini:<br/><br/>Özel geliştirme gereklidir<br/>Dış veri kaynağı /depolanan önbellek gereklidir, örneğin Azure<br/>|

Siteniz için en uygun seçenek, site gereksinimlerinize ve teknik yeteneğinize bağlıdır. İçerik değiştirildiğinde otomatik olarak güncelleştirilen, yapılandırması kolay bir gezinti sağlayıcısı istiyorsanız, [önbelleğe alma etkin](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) yapısal gezinti iyi bir seçenektir.

>[!NOTE]
>Genel site yapısını düz ve hiyerarşik olmayan bir yapıya basitleştirerek modern SharePoint sitelerle aynı ilkeyi uygulamak, performansı artırır ve modern SharePoint sitelerine geçişi basitleştirir. Bunun anlamı, yüzlerce site (alt web) içeren tek bir site koleksiyonuna sahip olmak yerine, çok az alt siteye (alt web) sahip birçok site koleksiyonuna sahip olmak daha iyi bir yaklaşımdır.

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>SharePoint Online'da gezinti performansını analiz etme

[SharePoint için Sayfa Tanılama aracı](./page-diagnostics-for-spo.md), hem SharePoint Çevrimiçi modern portalı hem de klasik yayımlama sitesi sayfalarını analiz eden Microsoft Edge ve Chrome tarayıcıları için bir tarayıcı uzantısıdır. Bu araç yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

Araç, analiz edilen her sayfa için sayfanın önceden tanımlanmış bir kural kümesine göre nasıl performans gösterdiğini gösteren bir rapor oluşturur ve test sonuçları temel değerin dışında olduğunda ayrıntılı bilgiler görüntüler. SharePoint Çevrimiçi yöneticiler ve tasarımcılar, yayımlama öncesinde yeni sayfaların iyileştirildiğinden emin olmak için performans sorunlarını gidermek için aracı kullanabilir.

**SPRequestDuration** özellikle SharePoint sayfayı işleme süresidir. Ağır gezinti (gezintideki sayfalar dahil), karmaşık site hiyerarşileri ve diğer yapılandırma ve topoloji seçeneklerinin tümü daha uzun sürelere önemli ölçüde katkıda bulunabilir.

## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online'da yapısal gezintiyi kullanma

Bu, varsayılan olarak kullanılan kullanıma hazır gezintidir ve en basit çözümdür. Herhangi bir özelleştirme gerektirmez ve teknik olmayan bir kullanıcı da kolayca öğe ekleyebilir, öğeleri gizleyebilir ve ayarlar sayfasından gezintiyi yönetebilir. [Önbelleğe almayı etkinleştirmenizi](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) öneririz, aksi takdirde pahalı bir performans dengelemesi vardır.

### <a name="how-to-implement-structural-navigation-caching"></a>Yapısal gezinti önbelleğini uygulama

**Site Ayarlar** >  **Look ve** **FeelNavigation** >  altında, genel gezinti veya geçerli gezinti için yapısal gezintinin seçili olup olmadığını doğrulayabilirsiniz. **Sayfaları göster'in** seçilmesi performansı olumsuz etkiler.

![Alt Siteleri Göster'in seçili olduğu yapısal gezinti.](../media/SPONavOptionsStructuredShowSubsites.png)

Önbelleğe Alma, site koleksiyonu düzeyinde ve site düzeyinde etkinleştirilebilir veya devre dışı bırakılabilir ve her ikisi için de varsayılan olarak etkinleştirilir. Site koleksiyonu düzeyinde etkinleştirmek için **, Site Ayarlar** >  **Site Koleksiyonu YönetimiSite** >  **Koleksiyonu Gezintisi'nin** altında **Önbelleğe almayı etkinleştir** kutusunu işaretleyin.

![Site düzeyinde önbelleğe almayı etkinleştirin.](../media/structural-nav/structural-nav-caching-site-coll.png)

Site düzeyinde etkinleştirmek için **Site Ayarlar** >  **Navigation** altında **Önbelleğe almayı etkinleştir** kutusunu işaretleyin.

![Site düzeyinde önbelleğe almayı etkinleştirin.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online'da yönetilen gezinti ve meta verileri kullanma

Yönetilen gezinti, yapısal gezintiyle aynı işlevlerin çoğunu yeniden oluşturmak için kullanabileceğiniz bir diğer kullanıma uygun seçenektir. Yönetilen meta veriler, güvenlik kırpmanın etkinleştirilmesi veya devre dışı bırakılması için yapılandırılabilir. Güvenlik kırpma devre dışıyken yapılandırıldığında, tüm gezinti bağlantılarını sabit sayıda sunucu çağrısıyla yüklediğinden yönetilen gezinti oldukça verimlidir. Bununla birlikte, güvenlik kırpmanın etkinleştirilmesi, yönetilen gezintinin bazı performans avantajlarını engeller.

Güvenlik kırpmasını etkinleştirmeniz gerekiyorsa şunları yapmanızı öneririz:

- Tüm kolay URL bağlantılarını basit bağlantılara güncelleştirin
- Gerekli güvenlik kırpma düğümlerini kolay URL'ler olarak ekleme
- Gezinti öğelerinin sayısını en fazla 100 ve en fazla 3 düzey derinliğinde sınırlayın

Gezinti yapısı genellikle sitenin tüm kullanıcıları için tutarlı olduğundan, birçok site güvenlik kırpması gerektirmez. Güvenlik kırpma devre dışı bırakılırsa ve gezintiye tüm kullanıcıların erişimi olmayan bir bağlantı eklenirse, bağlantı yine de gösterilir ancak erişim reddedildi iletisine yol açar. İçeriğe yanlışlıkla erişim riski yoktur.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Yönetilen gezintiyi ve sonuçları uygulama

yönetilen gezintinin ayrıntıları hakkında docs.microsoft.com birkaç makale vardır. Örneğin, bkz. [SharePoint Server'da yönetilen gezintiye genel bakış](/sharepoint/administration/overview-of-managed-navigation).

Yönetilen gezintiyi uygulamak için, sitenin gezinti yapısına karşılık gelen URL'lerle terimler ayarlarsınız. Yönetilen gezinti, çoğu durumda yapısal gezintiyi değiştirmek için el ile de kullanılabilir. Örneğin:

![SharePoint Online site yapısı.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Arama temelli istemci tarafı betiği kullanma

Yaygın bir özel gezinti uygulaması sınıfı, yerel gezinti düğümleri önbelleğini depolayan istemci tarafından işlenmiş tasarım desenlerini benimser.

Bu gezinti sağlayıcılarının birkaç önemli avantajı vardır:

- Genellikle hızlı yanıt veren sayfa tasarımlarıyla iyi çalışırlar.
- Bunlar son derece ölçeklenebilir ve yüksek performanslıdır çünkü kaynak maliyeti olmadan işlenebilirler (ve zaman aşımından sonra arka planda yenileyebilirler).
- Bu gezinti sağlayıcıları, basit statik yapılandırmalardan çeşitli dinamik veri sağlayıcılarına kadar çeşitli stratejileri kullanarak gezinti verilerini alabilir.

Veri sağlayıcısına örnek olarak, gezinti düğümlerini listeleme ve güvenlik kırpma işlemlerini verimli bir şekilde işleme esnekliği sağlayan **Arama temelli gezinti** kullanmaktır.

**Özel gezinti sağlayıcıları** oluşturmak için başka popüler seçenekler de vardır. Özel gezinti sağlayıcısı oluşturma konusunda daha fazla rehberlik [için lütfen SharePoint Çevrimiçi portallar](/sharepoint/dev/solution-guidance/portal-navigation) için gezinti çözümlerini gözden geçirin.

Aramayı kullanarak, sürekli gezinmeyi kullanarak arka planda oluşturulan dizinleri kullanabilirsiniz. Arama sonuçları arama dizininden çekilir ve sonuçlar güvenlikle kırpılır. Bu genellikle güvenlik kırpması gerektiğinde kullanıma kullanıma yönelik gezinti sağlayıcılarından daha hızlıdır. Özellikle karmaşık bir site yapınız varsa yapısal gezinti araması kullanmak sayfa yükleme süresini önemli ölçüde hızlandıracaktır. Bunun yönetilen gezintiye göre temel avantajı, güvenlik kırpmasından yararlanmanızdır.

Bu yaklaşım, özel bir ana sayfa oluşturmayı ve kullanıma açık gezinti kodunu özel HTML ile değiştirmeyi içerir. dosyasındaki `seattle.html`gezinti kodunu değiştirmek için aşağıdaki örnekte özetlenen bu yordamı izleyin. Bu örnekte, dosyayı açar `seattle.html` ve öğenin tamamını `id="DeltaTopNavigation"` özel HTML koduyla değiştirirsiniz.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Örnek: Bir ana sayfadaki kullanıma özel gezinti kodunu değiştirme

1. Site Ayarlar sayfasına gidin.
2. **Ana Sayfalar'a** tıklayarak ana sayfa galerisini açın.
3. Buradan kitaplıkta gezinebilir ve dosyasını `seattle.master`indirebilirsiniz.
4. Bir metin düzenleyicisi kullanarak kodu düzenleyin ve aşağıdaki ekran görüntüsünde kod bloğunu silin.<br/>![Gösterilen kod bloğunu silin.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. ve `<\SharePoint:AjaxDelta>` etiketleri arasındaki `<SharePoint:AjaxDelta id="DeltaTopNavigation">` kodu kaldırın ve aşağıdaki kod parçacığıyla değiştirin:<br/>

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
6. Başlangıçtaki yükleme görüntüsü tutturucu etiketindeki URL'yi site koleksiyonunuzdaki bir yükleme görüntüsünün bağlantısıyla değiştirin. Değişiklikleri yaptıktan sonra dosyayı yeniden adlandırın ve ana sayfa galerisine yükleyin. Bu, yeni bir .master dosyası oluşturur.<br/>
7. Bu HTML, JavaScript kodundan döndürülen arama sonuçlarıyla doldurulacak temel işaretlemedir. Aşağıdaki kod parçacığında gösterildiği gibi var root = "site koleksiyonu URL'si" değerini değiştirmek için kodu düzenlemeniz gerekir:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Sonuçlar self.nodes dizisine atanır ve çıkışı bir dizi self.hierarchy'e atamak linq.js kullanılarak nesnelerden bir hiyerarşi oluşturulur. Bu dizi, HTML'ye bağlı nesnedir. Bu işlem, toggleView() işlevinde kendi nesnesini ko.applyBinding() işlevine geçirerek yapılır.<br/>Bu, hiyerarşi dizisinin aşağıdaki HTML'ye bağlanmasına neden olur:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

ve `mouseexit` için `mouseenter` olay işleyicileri, işlevinde yapılan alt site açılan menülerini işlemek için üst düzey gezintiye `addEventsToElements()` eklenir.

Karmaşık gezinti örneğimizde, yerel önbelleğe alma olmadan yapılan yeni bir sayfa yükü, yönetilen gezinti yaklaşımına benzer bir sonuç elde etmek için sunucuda harcanan sürenin karşılaştırma yapısal gezintisinden azaltıldığını gösterir.

### <a name="about-the-javascript-file"></a>JavaScript dosyası hakkında...

>[!NOTE]
>Özel JavaScript kullanıyorsanız, genel CDN etkinleştirildiğinden ve dosyanın CDN bir konumda olduğundan emin olun.

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

İşlevde `jQuery $(document).ready` yukarıda gösterilen kodu özetlemek için bir `viewModel object` oluşturulur ve bu nesnedeki `loadNavigationNodes()` işlev çağrılır. Bu işlev, istemci tarayıcısının HTML5 yerel depolama alanında depolanan önceden oluşturulmuş gezinti hiyerarşisini yükler veya işlevini `queryRemoteInterface()`çağırır.

`QueryRemoteInterface()` betiğinde `getRequest()` daha önce tanımlanan sorgu parametresiyle işlevini kullanarak bir istek oluşturur ve ardından sunucudan veri döndürür. Bu veriler temelde çeşitli özelliklere sahip veri aktarım nesneleri olarak temsil edilen site koleksiyonundaki tüm sitelerin dizisidir.

Daha sonra bu veriler, değerleri daha önce tanımladığımız HTML'ye bağlayan veriler tarafından kullanılmak üzere gözlemlenebilir özellikler oluşturmak için kullanılan `Knockout.js` önceden tanımlanmış `SPO.Models.NavigationNode` nesnelere ayrıştırılır.

Nesneler daha sonra bir sonuç dizisine konur. Bu dizi, Knockout kullanılarak JSON'a ayrıştırılır ve gelecekteki sayfa yüklemelerinde daha iyi performans için yerel tarayıcı depolama alanında depolanır.

### <a name="benefits-of-this-approach"></a>Bu yaklaşımın avantajları

[Bu yaklaşımın](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) önemli avantajlarından biri, HTML5 yerel depolama kullanılarak gezintinin sayfayı bir sonraki yükleyişinde kullanıcı için yerel olarak depolanmasıdır. Yapısal gezinti için arama API'sini kullanarak önemli performans iyileştirmeleri elde ederiz; ancak bu işlevi yürütmek ve özelleştirmek için bazı teknik yetenekler gerekir.

[Örnek uygulamada](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), siteler kullanıma yönelik yapısal gezinti ile aynı şekilde sıralanır; alfabetik sıra. Bu düzenden sapmak istiyorsanız, geliştirmek ve korumak daha karmaşık olacaktır. Ayrıca, bu yaklaşım desteklenen ana sayfalardan sapmanızı gerektirir. Özel ana sayfa korunmazsa, siteniz Microsoft'un ana sayfalarda yaptığı güncelleştirmeleri ve iyileştirmeleri kaçıracaktır.

[Yukarıdaki kod](#about-the-javascript-file) aşağıdaki bağımlılıklara sahiptir:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/veya github.com/neuecc/linq.js

LinqJS'nin geçerli sürümü yukarıdaki kodda kullanılan ByHierarchy yöntemini içermez ve gezinti kodunu bozar. Bunu düzeltmek için, satırından `Flatten: function ()`önce Linq.js dosyasına aşağıdaki yöntemi ekleyin.

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

[Yapısal gezinti önbelleği ve performansı](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)