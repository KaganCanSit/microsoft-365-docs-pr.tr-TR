---
title: Microsoft 365 Multi-Geo için aramayı yapılandırma
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Çok coğrafi bir ortamda aramayı yapılandırmayı öğrenin. Yalnızca OneDrive gibi bazı istemciler sonuçları çok coğrafi bir ortamda döndürebilir.
ms.openlocfilehash: a6f152a3f226befa8bc060dadd0eed1c0952523c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824936"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo için Aramayı Yapılandırma

Çok coğrafi bir ortamda her coğrafi konumun kendi arama dizini ve Arama Merkezi vardır. Kullanıcı arama yaparken, sorgu tüm dizinlere yönlendirilir ve döndürülen sonuçlar birleştirilir.

Örneğin, bir coğrafi konumdaki bir kullanıcı başka bir coğrafi konumda depolanan içeriği veya farklı bir coğrafi konumla kısıtlanmış bir SharePoint sitesindeki içeriği arayabilir. Kullanıcının bu içeriğe erişimi varsa, arama sonucu gösterir.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Hangi arama istemcileri çok coğrafi bir ortamda çalışır?

Bu istemciler tüm coğrafi konumlardan sonuçlar döndürebilir:

- OneDrive
- Delve
- SharePoint giriş sayfası
- Arama Merkezi
- SharePoint Arama API'sini kullanan özel arama uygulamaları

### <a name="onedrive"></a>OneDrive

Çok coğrafi ortam ayarlanır kurulmaz, OneDrive'de arama yapılan kullanıcılar tüm coğrafi konumlardan sonuçlar alır.

### <a name="delve"></a>Delve

Çok coğrafi ortam ayarlanır ayarlanmaz, Delve'de arama Delve kullanıcılar tüm coğrafi konumlardan sonuçlar alır.

Delve akışı ve profil kartı yalnızca merkezi konumda depolanan dosyaların önizlemelerini gösterir. Uydu konumlarında depolanan dosyalar için bunun yerine dosya türü simgesi gösterilir.

### <a name="the-sharepoint-home-page"></a>SharePoint giriş sayfası

Çok coğrafi ortam ayarlanır kurulmaz, kullanıcılar SharePoint giriş sayfasında birden çok coğrafi konumdan gelen haberleri, son ve takip edilen siteleri görür. SharePoint giriş sayfasındaki arama kutusunu kullanırlarsa, birden çok coğrafi konumdan birleştirilmiş sonuçlar alır.

### <a name="the-search-center"></a>Arama Merkezi

Çok coğrafi ortam ayarlandıktan sonra, her Arama Merkezi yalnızca kendi coğrafi konumlarından sonuçları göstermeye devam eder. Yöneticilerin tüm coğrafi konumlardan sonuç almak için [her Arama Merkezi'nin ayarlarını değiştirmesi](#_Set_up_a_1) gerekir. Daha sonra Arama Merkezi'nde arama yapılan kullanıcılar tüm coğrafi konumlardan sonuçlar alır.

### <a name="custom-search-applications"></a>Özel arama uygulamaları

Her zamanki gibi, özel arama uygulamaları mevcut SharePoint Arama REST API'lerini kullanarak arama dizinleriyle etkileşim kurar. Tüm veya bazı coğrafi konumlardan sonuç almak için uygulamanın [API'yi çağırması ve isteğe yeni Multi-Geo sorgu parametrelerini eklemesi](#_Get_custom_search) gerekir. Bu, sorgudan tüm coğrafi konumlara giden bir fan tetikler.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Çok coğrafili bir ortamda aramanın farkı nedir?

Aşina olabileceğiniz bazı arama özellikleri, çok coğrafi bir ortamda farklı çalışır.

<table>
<thead>
<tr class="header">
<th align="left">Özellik</th>
<th align="left">Nasıl çalışır?</th>
<th align="left">Geçici Çözüm</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Yükseltilen sonuçlar</td>
<td align="left">Yükseltilen sonuçlarla farklı düzeylerde sorgu kuralları oluşturabilirsiniz: kiracının tamamı, site koleksiyonu veya site için. Çok coğrafi bir ortamda, tüm coğrafi konumlarda sonuçları Arama Merkezlerine yükseltmek için kiracı düzeyinde yükseltilen sonuçları tanımlayın. Sonuçları yalnızca site koleksiyonunun veya sitenin coğrafi konumundaki Arama Merkezi'nde yükseltmek istiyorsanız, yükseltilen sonuçları site koleksiyonu veya site düzeyinde tanımlayın. Bu sonuçlar diğer coğrafi konumlarda yükseltilmemiştir.</td>
<td align="left">Coğrafi konum başına farklı yükseltilen sonuçlara ihtiyacınız yoksa (örneğin seyahat için farklı kurallar) kiracı düzeyinde yükseltilen sonuçları tanımlamanızı öneririz.</td>
</tr>
<tr class="even">
<td align="left">Arama iyileştiricileri</td>
<td align="left">Arama, bir kiracının tüm coğrafi konumlarından iyileştiriciler döndürür ve sonra bunları toplar. Toplama en iyi çabadır, yani iyileştirici sayıları %100 doğru olmayabilir. Çoğu arama temelli senaryo için bu doğruluk yeterlidir.
</td>
<td align="left">İyileştiricinin eksiksizliğine bağlı arama temelli uygulamalar için her coğrafi konumu bağımsız olarak sorgulayabilirsiniz.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Çok coğrafi arama, sayısal iyileştiriciler için dinamik demeti desteklemez.</td>
<td align="left">Sayısal iyileştiriciler için <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" parametresini</a> kullanın.</td>
</tr>
<tr class="even">
<td align="left">Belge Kimlikleri</td>
<td align="left">Belge kimliklerine bağlı arama temelli bir uygulama geliştiriyorsanız, çok coğrafi bir ortamdaki belge kimliklerinin coğrafi konumlar arasında benzersiz olmadığını, coğrafi konum başına benzersiz olduğunu unutmayın.</td>
<td align="left">Coğrafi konumu tanımlayan bir sütun ekledik. Benzersizliğe ulaşmak için bu sütunu kullanın. Bu sütun "GeoLocationSource" olarak adlandırılır.</td>
</tr>
<tr class="odd">
<td align="left">Sonuç sayısı</td>
<td align="left">Arama sonuçları sayfasında coğrafi konumlardan elde edilen birleşik sonuçlar gösterilir, ancak 500'den fazla sonucu sayfaya eklemek mümkün değildir.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Karma arama</td>
<td align="left"><a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">Bulut karma aramalı</a> karma SharePoint ortamında, şirket içi içerik merkezi konumun Microsoft 365 dizinine eklenir.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Çok coğrafili bir ortamda arama için ne desteklenmez?

Aşina olabileceğiniz bazı arama özellikleri çok coğrafi bir ortamda desteklenmez.

<table>
<thead>
<tr class="header">
<th align="left">Arama özelliği</th>
<th align="left">Not</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Yalnızca uygulama kimlik doğrulaması</td>
<td align="left">Yalnızca uygulama kimlik doğrulaması (hizmetlerden ayrıcalıklı erişim) birden fazla coğrafi konumda arama desteklenmez.</td>
</tr>
<tr class="even">
<td align="left">Konuklar</td>
<td align="left">Konuklar yalnızca aradıkları coğrafi konumdan sonuçlar alır.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Çok coğrafi bir ortamda arama nasıl çalışır?

Tüm arama istemcileri, arama dizinleriyle etkileşime geçmek için mevcut SharePoint Arama REST API'lerini kullanır.

![SharePoint Arama REST API'lerinin arama dizinleriyle nasıl etkileşime geçtiğini gösteren diyagram.](../media/configure-search-for-multi-geo-image1-1.png)

1. Arama istemcisi Search REST uç noktasını EnableMultiGeoSearch= true sorgu özelliğiyle çağırır.
2. Sorgu kiracıdaki tüm coğrafi konumlara gönderilir.
3. Her coğrafi konumdan gelen arama sonuçları birleştirilir ve derecelendirilir.
4. İstemci birleşik arama sonuçları alır.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Tüm coğrafi konumlardan sonuçlar alınana kadar arama sonuçlarını birleştirmediğimize dikkat edin. Bu, çok coğrafi konumlu aramaların yalnızca bir coğrafi konuma sahip bir ortamdaki aramalara kıyasla ek gecikme süresine sahip olduğu anlamına gelir.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Tüm coğrafi konumlardan sonuçları göstermek için arama merkezi alma

Her Arama Merkezi'nin birkaç dikey ayarı vardır ve her dikeyi ayrı ayrı ayarlamanız gerekir.

1. Bu adımları, arama sonuçları sayfasını ve Arama Sonucu Web Bölümünü düzenleme izni olan bir hesapla gerçekleştirdiğinizden emin olun.

2. Arama sonuçları sayfasına gidin (arama sonuçları sayfalarının [listesine](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) bakın)

3. Ayarlamak için dikey öğeyi seçin, sağ üst köşedeki **Ayarlar** dişli simgesine ve ardından **Sayfayı Düzenle'ye** tıklayın. Arama sonuçları sayfası Düzenleme modunda açılır.

   ![Ayarlar'de sayfa seçimini düzenleyin.](../media/configure-search-for-multi-geo-image2.png)

4. Arama Sonuçları Web Bölümü'nde, işaretçiyi web bölümünün sağ üst köşesine getirin, oka tıklayın ve ardından menüde **Web Bölümünü Düzenle'ye** tıklayın. Arama Sonuçları Web Bölümü araç bölmesi, sayfanın sağ üst kısmındaki şeridin altında açılır.

   ![Web Bölümü seçimini düzenleyin.](../media/configure-search-for-multi-geo-image3.png)

5. Web Bölümü araç bölmesindeki **Ayarlar** bölümündeki **Sonuçlar denetim ayarları'nın** altında **Multi-Geo sonuçlarını göster'i** seçerek Arama Sonuçları Web Bölümü'nü seçerek tüm coğrafi konumlardaki sonuçları görüntüleyin.

6. Değişikliğinizi kaydetmek ve Web Bölümü araç bölmesini kapatmak için **Tamam'a** tıklayın.

7. Ana menünün Sayfa sekmesinde **İade Et'e** tıklayarak Arama Sonuçları Web Bölümü'nde yaptığınız değişiklikleri denetleyin.

8. Sayfanın üst kısmındaki notta sağlanan bağlantıyı kullanarak değişiklikleri yayımlayın.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Tüm veya bazı coğrafi konumlardaki sonuçları göstermek için özel arama uygulamaları alma

Özel arama uygulamaları, SharePoint Arama REST API'sine yönelik istekle sorgu parametrelerini belirterek tüm coğrafi konumlardan veya bazı coğrafi konumlardan sonuç alır. Sorgu parametrelerine bağlı olarak, sorgu tüm coğrafi konumlara veya bazı coğrafi konumlara yönlendirilir. Örneğin, ilgili bilgileri bulmak için yalnızca coğrafi konumların bir alt kümesini sorgulamanız gerekiyorsa, fanı yalnızca bunlara göre denetleyebilirsiniz. İstek başarılı olursa, SharePoint Arama REST API'si yanıt verilerini döndürür.

### <a name="requirement"></a>Gereksinim

Her coğrafi konum için kuruluştaki tüm kullanıcılara kök web sitesi (örneğin **contosoAPAC.sharepoint.com/** ve **contosoEU.sharepoint.com/**) için **Okuma** izni verildiğinden emin olmanız gerekir. [İzinler hakkında bilgi edinin](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Sorgu parametreleri

EnableMultiGeoSearch - Bu, sorgunun çok coğrafi kiracının diğer coğrafi konumlarının dizinlerine aktarılıp aktarılmayacağını belirten bir Boole değeridir. Sorguyu yaymak için **true** olarak ayarlayın; **false** değerini sunun. Bu parametreyi eklemezseniz, Enterprise Arama Merkezi şablonunu kullanan bir sitede REST API çağrısı yapmak dışında varsayılan değer **false** olur; bu durumda varsayılan değer **true** olur. parametresini çok coğrafi olmayan bir ortamda kullanırsanız, parametre yoksayılır.

ClientType - Bu bir dizedir. Her arama uygulaması için benzersiz bir istemci adı girin. Bu parametreyi eklemezseniz, sorgu diğer coğrafi konumlara eklenmez.

MultiGeoSearchConfiguration - Bu, **EnableMultiGeoSearch** **true** olduğunda sorguyu hayran kılmak için çok coğrafi kiracıdaki coğrafi konumların isteğe bağlı bir listesidir. Bu parametreyi dahil etmez veya boş bırakırsanız, sorgu tüm coğrafi konumlara yönlendirilir. Her coğrafi konum için JSON biçiminde aşağıdaki öğeleri girin:

<table>
<thead>
<tr class="header">
<th align="left">Öğe</th>
<th align="left">Açıklama</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Coğrafi konum, örneğin NAM.</td>
</tr>
<tr class="even">
<td align="left">Bitiş noktası</td>
<td align="left">Bağlanacak uç nokta, örneğin https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">Sonuç kaynağının GUID değeri, örneğin B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

DataLocation veya EndPoint'i atlarsanız veya bir DataLocation yineleniyorsa istek başarısız olur. [Microsoft Graph kullanarak kiracının coğrafi konumlarının uç noktası hakkında bilgi alabilirsiniz](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Yanıt verileri

MultiGeoSearchStatus : Bu, SharePoint Arama API'sinin bir isteğe yanıt olarak döndürdüğü bir özelliktir. özelliğinin değeri bir dizedir ve SharePoint Arama API'sinin döndürdüğü sonuçlar hakkında aşağıdaki bilgileri verir:

<table>
<thead>
<tr class="header">
<th align="left">Değer</th>
<th align="left">Açıklama</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Tam</td>
<td align="left"><strong>Tüm</strong> coğrafi konumlardan tam sonuçlar.</td>
</tr>
<tr class="even">
<td align="left">Kısmi</td>
<td align="left">Bir veya daha fazla coğrafi konumdan kısmi sonuçlar. Geçici bir hata nedeniyle sonuçlar tamamlanmadı.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>REST hizmetini kullanarak sorgulama

GET isteğiyle, URL'de sorgu parametrelerini belirtirsiniz. POST isteğiyle, gövdedeki sorgu parametrelerini JavaScript Nesne Gösterimi (JSON) biçiminde geçirirsiniz.

#### <a name="request-headers"></a>İstek üst bilgileri

<table>
<thead>
<tr class="header">
<th align="left">Name</th>
<th align="left">Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">İçerik Türü</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>**Tüm** coğrafi konumlara giden örnek GET isteği

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>**Bazı** coğrafi konumlara giden örnek GET isteği

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> MultiGeoSearchConfiguration özelliği için coğrafi konumlar listesindeki virgüller ve iki nokta üst üsteler **ters eğik çizgi** karakterinden önce gelir. Bunun nedeni GET isteklerinin özellikleri ayırmak için iki nokta üst üste ve özelliklerin bağımsız değişkenlerini ayırmak için virgül kullanmasıdır. Kaçış karakteri olarak ters eğik çizgi olmadan MultiGeoSearchConfiguration özelliği yanlış yorumlanır.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>**Tüm** coğrafi konumlara giden örnek POST isteği

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>**Bazı** coğrafi konumlara giden örnek POST isteği

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a>CSOM kullanarak sorgulama

Tüm **coğrafi** konumlara giden örnek bir CSOM sorgusu aşağıda verilmişti:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
