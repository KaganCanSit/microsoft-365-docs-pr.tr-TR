---
title: Multi-Geo Microsoft 365 arama yapılandırma
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
description: Çok coğrafi bir ortamda arama yapılandırmayı öğrenin. Çok coğrafi bir ortamda OneDrive bazı istemciler sonuç geri getir olabilir.
ms.openlocfilehash: d6d6895c6dc393bb1f28dff60dea996bf80aad5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988183"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Multi-Geo Microsoft 365'i yapılandırma

Çok coğrafi bir ortamda, her coğrafi konumun kendi arama dizini ve Arama Merkezi vardır. Kullanıcı aramalarında, sorgu tüm dizinlere işaret ediyor ve döndürülen sonuçlar birleştirilir.

Örneğin, bir coğrafi konumdaki kullanıcı başka bir coğrafi konumda depolanan içeriği veya farklı bir coğrafi konumla sınırlı SharePoint bir Coğrafi Konum sitesinde içerik arayabilir. Kullanıcının bu içeriğe erişimi varsa, arama sonucu gösterir.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Çok coğrafi ortamda hangi arama istemcileri çalışır?

Bu istemciler tüm coğrafi konumlardan sonuçlar geri getirebilirsiniz:

- OneDrive
- Delve
- Sayfa SharePoint sayfası
- Arama Merkezi
- Arama API'sini kullanan SharePoint arama uygulamaları

### <a name="onedrive"></a>OneDrive

Çok coğrafi ortam ayar hemen ayarlanır ayarlamaz, kaynakta arama OneDrive tüm coğrafi konumlardan sonuçlar elde eder.

### <a name="delve"></a>Delve

Çok coğrafi ortam ayar hemen ayarlanır ayarlamaz, kaynakta arama Delve tüm coğrafi konumlardan sonuçlar elde eder.

Sayfa Delve ve profil kartı yalnızca merkezi konumda depolanan dosyaların önizlemelerini gösterir. Uydu konumlarında depolanan dosyalar için bunun yerine dosya türünün simgesi gösterilir.

### <a name="the-sharepoint-home-page"></a>Sayfa SharePoint sayfası

Multi-geo ortamı ayarlanmaz, kullanıcılar ana sayfalarında birden çok coğrafi konumdaki haberleri, son ve takip edilen siteleri SharePoint görebilirler. Ana sayfada yer alan arama kutusunu SharePoint, birden çok coğrafi konumdan birleştirilmiş sonuçlar elde olur.

### <a name="the-search-center"></a>Arama Merkezi

Çok coğrafi ortam ayarlandıktan sonra, her Arama Merkezi yalnızca kendi coğrafi konumlarından sonuçları göstermeye devam eder. Yöneticilerin tüm [coğrafi konumlardan sonuç almak için](#_Set_up_a_1) her Arama Merkezi'nin ayarlarını değiştirmesi gerekir. Bundan sonra, Arama Merkezi'nde arama kullanan kullanıcılar tüm coğrafi konumlardan sonuçlar elde ediyor.

### <a name="custom-search-applications"></a>Özel arama uygulamaları

Özel arama uygulamaları her zamanki gibi, var olan ARAMA REST API'lerini kullanarak arama SharePoint etkileşimde kullanılmaktadır. Tüm konumlardan veya bazı coğrafi konumlardan sonuç almak için uygulamanın API'yi araması ve yeni [Multi-Geo](#_Get_custom_search) sorgu parametrelerini istekte içermesi gerekir. Bu, sorgunun tüm coğrafi konumlara doğru bir fanı tetikler.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Çok coğrafi bir ortamda arama arasında ne fark vardır?

Biliyor olabileceğiniz bazı arama özellikleri, çok coğrafi bir ortamda farklı çalışır.

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
<td align="left">Yükseltildi sonuçları</td>
<td align="left">Farklı düzeylerde yükselten sonuçlarla, sorgu kuralları oluşturabilirsiniz: tüm kiracı, bir site koleksiyonu veya bir site için. Çok coğrafi bir ortamda, sonuçları tüm coğrafi konumlarda Arama Merkezlerine tanıtmak için, yükseltilen sonuçları kiracı düzeyinde tanımlayın. Yalnızca site koleksiyonunun veya sitenin coğrafi konumu olan Arama Merkezi'nde sonuçların tanıtımını yapmak için, yükseltilen sonuçları site koleksiyonu veya site düzeyinde tanımlayın. Bu sonuçlar, diğer coğrafi konumlarda yükseltlanmaz.</td>
<td align="left">Coğrafi konum başına farklı yükseltilecek sonuçlara, örneğin seyahat için farklı kurallara ihtiyacınız yoksa, yükseltilecek sonuçları kiracı düzeyinde tanımlamanız önerilir.</td>
</tr>
<tr class="even">
<td align="left">İyileştiricileri arama</td>
<td align="left">Arama, bir kiracının tüm coğrafi konumlarından iyileştiricileri döndürür ve sonra bunları bir araya döndürür. Toplama en iyi çalışmadır; başka bir ifadeyle, iyileştirici sayıları %100 doğru olmayabilir. Arama güdümlü senaryoların çoğu için bu doğruluk yeterli olacaktır. 
</td>
<td align="left">İyileştiricinin eksiksizliğine bağımlı arama odaklı uygulamalar için, her coğrafi konumu birbirinden bağımsız olarak sorgular.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Çok coğrafi arama, sayısal iyileştiriciler için dinamik demetleri desteklemez.</td>
<td align="left">Sayısal <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">iyileştiriciler için "Ayrık"</a> parametresini kullanın.</td>
</tr>
<tr class="even">
<td align="left">Belge Kimlikleri</td>
<td align="left">Arama odaklı, belge kimliklarına dayalı bir uygulama geliştiriyorsanız, çok coğrafi bir ortamdaki belge kimliklerin coğrafi konumlar arasında benzersiz olmadığını, coğrafi konumlar başına benzersiz olduğunu unutmayın.</td>
<td align="left">Coğrafi konumu tanımlayan bir sütun ekledik. Benzersizlik elde etmek için bu sütunu kullanın. Bu sütunun adı "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Sonuç sayısı</td>
<td align="left">Arama sonuçları sayfası coğrafi konumlardan birleştirilmiş sonuçları gösterir, ancak 500 sonucun ötesinde sonuçlar almak mümkün değildir.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Karma arama</td>
<td align="left">Bulut karma SharePoint karma <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">bir</a> ortamda, şirket içi içerik merkezi konumun Microsoft 365 dizine eklenir.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Çok coğrafi bir ortamda arama için neler desteklenmiyor?

Aşina olabileceğiniz arama özelliklerinin bazıları çok coğrafi bir ortamda desteklenmiyor.

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
<td align="left">Yalnızca uygulama kimlik doğrulaması (hizmetlerden ayrıcalıklı erişim) birden fazla coğrafi konumda arama.</td>
</tr>
<tr class="even">
<td align="left">Konuklar</td>
<td align="left">Konuklar yalnızca arayarak katıldıkları coğrafi konumdan sonuçlar elde ediyor.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Çok coğrafi ortamda arama nasıl çalışır?

Tüm arama istemcileri, arama dizinleriyle SharePoint Search REST API'leri için mevcut verileri kullanır.

![Search REST API'SharePoint arama dizinleriyle nasıl etkileşim kurduğu gösteren diyagram.](../media/configure-search-for-multi-geo-image1-1.png)

1. Arama istemcisi, EnableMultiGeoSearch= true sorgu özelliğiyle REST Ara uç noktasını arar.
2. Sorgu, kiracının tüm coğrafi konumlara gönderilir.
3. Her coğrafi konumdan gelen arama sonuçları birleştirilir ve dereceleştirilir.
4. İstemci, birleşik arama sonuçlarını alır.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Tüm coğrafi konumlardan sonuç alınana kadar arama sonuçlarını birleştirmeyimize dikkat edin. Bu, çok coğrafi aramaların tek bir coğrafi konumu olan bir ortamda yapılan aramalara göre ek gecikme süresine sahip olduğu anlamına gelir.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Tüm coğrafi konumlardan sonuçları göstermek için bir Arama Merkezi'ne sahip olur

Her Arama Merkezi'nin birçok dikey dikey konumu vardır ve her dikey konumu tek tek ayarlamalısiniz.

1. Arama sonuçları sayfasını ve Arama Sonucu Web Bölümünü düzenleme izni olan bir hesap ile bu adımları gerçekleştirin.

2. Arama sonuçları sayfasına gidin (arama [sonuçları sayfalarının](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) listesine bakın)

3. Ayarlamak için dikey simgesini seçin, sağ **üst Ayarlar** dişli simgesine tıklayın ve sonra da Sayfayı Düzenle'ye **tıklayın**. Arama sonuçları sayfası Düzenleme modunda açılır.

   ![Çalışma sayfasında sayfa seçimini Ayarlar.](../media/configure-search-for-multi-geo-image2.png)

4. Arama Sonuçları Web Bölümünde, işaretçiyi web adının sağ üst köşesine hareket ettirin, oka tıklayın ve ardından menüde **Web Bölümünü Düzenle'ye** tıklayın. Arama Sonuçları Web Bölümü araç bölmesi, sayfanın sağ üst kısmında şeridin altında açılır.

   ![Web Bölümünü Düzenle seçimi.](../media/configure-search-for-multi-geo-image3.png)

5. Tüm coğrafi konumlardan sonuçları göstermek için Web Bölümü araç bölmesindeki Arama **Ayarlar** Kontrol ayarları'nın altında **Multi-Geo** Sonuçlarını Göster'i seçerek Arama Sonuçları Web Bölümü'ne gidin.

6. **Değişikliğinizi** kaydetmek ve Web Bölümü araç bölmesini kapatmak için Tamam'a tıklayın.

7. Ana menenin Sayfa sekmesindeki Iade **Edin'e** tıklayarak Arama Sonuçları Web Bölümü'ne yaptığınız değişiklikleri kontrol edin.

8. Sayfanın en üstünde yer alan notta sağlanan bağlantıyı kullanarak değişiklikleri yayımlayın.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Tüm konumlardan veya bazı coğrafi konumlardan sonuçları göstermek için özel arama uygulamaları elde

Özel arama uygulamaları, REST API'sini ara isteğiyle birlikte sorgu parametreleri belirterek sonuçları SharePoint elde edin. Sorgu parametrelerine bağlı olarak, sorgu tüm coğrafi konumlara veya bazı coğrafi konumlara yakın olur. Örneğin, ilgili bilgileri bulmak için yalnızca coğrafi konumların bir alt kümesini sorgulamanız yeterli olacaksa, bunları sadece bunlara yakın bir şekilde kontrol edin. İstek başarılı olursa, REST API'SharePoint Arama API'si yanıt verilerini döndürür.

### <a name="requirement"></a>Gereksinim

Her coğrafi konum için, kuruluşta tüm kullanıcılara kök web sitesi için Okuma izin düzeyinin verilmiş  olduğundan emin olmak gerekir (örneğin, **contosoAPAC.sharepoint.com/** ve **contosoEU.sharepoint.com/**). [İzinler hakkında bilgi edinmek için](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848):

### <a name="query-parameters"></a>Sorgu parametreleri

EnableMultiGeoSearch - Bu, sorgunun multi-geo kiracının diğer coğrafi konumlarının dizinleri için fantale olup olmadığını belirten Boole değeridir. Sorguyu **fani olarak** true olarak ayarlayın; **sorguyu** fan out out için false. Bu parametreyi dahil etmek yoksa, Enterprise Arama Merkezi şablonunu kullanan bir siteye karşı REST API çağrısı yaparken varsayılan değer false olur, ancak bu durumda varsayılan değer **true olur**. Parametreyi birden çok coğrafi olmayan bir ortamda kullanırsanız, parametre göz ardı edilir.

ClientType - Bu bir dizedir. Her arama uygulaması için benzersiz bir istemci adı girin. Bu parametreyi dahil etmeyebilirsiniz, sorgu diğer coğrafi konumlara bağlı değildir.

MultiGeoSearchConfiguration - Bu, **EnableMultiGeoSearch'un** ne zaman doğru olduğunu takip etmek için çok coğrafi kiracıda coğrafi konumların yer alan isteğe bağlı bir **listesidir**. Bu parametreyi dahil etmek veya boş bırakmak zorunda kalırsanız, sorgu tüm coğrafi konumlara yakın görünür. Her coğrafi konum için JSON biçiminde aşağıdaki öğeleri girin:

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
<td align="left">Coğrafi konum (örneğin NAM).</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">Bağlanıla uç nokta, örneğin https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">Sonuç kaynağının GUID'si; örneğin B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

DataLocation veya EndPoint'i atlarsanız veya bir DataLocation çoğaltılmışsa, istek başarısız olur. [Microsoft Graph kullanarak kiracının coğrafi konumlarının bitiş noktası hakkında bilgi Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Yanıt verileri

MultiGeoSearchStatus – Bu özellik, SharePoint Search API'sinde bir ima yanıt olarak döndüren bir özelliktir. Özelliğin değeri bir dizedir ve Ara API'sinde döndüren sonuçlar SharePoint verir:

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
<td align="left">Tüm coğrafi <strong>konumlardan</strong> tam sonuçlar.</td>
</tr>
<tr class="even">
<td align="left">Kısmi</td>
<td align="left">Bir veya birden çok coğrafi konumdan kısmi sonuçlar. Geçici bir hata nedeniyle sonuçlar eksik.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>REST hizmetini kullanan sorgu

GET isteğiyle, sorgu parametrelerini URL'de belirtirsiniz. POST isteğiyle, sorgu parametrelerini JavaScript Nesne Notasyonu (JSON) biçiminde gövdeye geçersiniz.

#### <a name="request-headers"></a>Üstbilgi isteği

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

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Tüm coğrafi konumlara fanenenen **örnek GET** isteği

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Bazı coğrafi konumlara fan yapmak **için örnek** GET isteği

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> MultiGeoSearchConfiguration özelliğinin coğrafi konumlar listesinde virgül ve iki nokta üst üste, ters eğik çizgi **karakteri vardır** . Bunun nedeni, GET isteklerinin özellikleri birbirinden ayırmak için iki nokta üst üste ve virgül kullanarak özellik bağımsız değişkenlerini birbirinden ayırmasıdır. Ters eğik çizgi bir çıkış karakteri olarak olmadan, MultiGeoSearchConfiguration özelliği yanlış yorumlanır.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Tüm coğrafi konumlara yazılan örnek **POSTA** isteği

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

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Bazı coğrafi konumlara yazılan örnek POST isteği 

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

### <a name="query-using-csom"></a>CSOM kullanan sorgu

Tüm coğrafi konumlara yakın olan örnek bir CSOM **sorgusu** şöyledir:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
