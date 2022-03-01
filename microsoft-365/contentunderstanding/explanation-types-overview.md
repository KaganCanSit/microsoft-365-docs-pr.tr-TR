---
title: Microsoft SharePoint Syntex'te açıklama türleri
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft Web sitesinde tümcecik listesi, normal ifade ve yakınlık açıklama türleri hakkında daha fazla SharePoint Syntex.
ms.openlocfilehash: 71c7379b3a9fcd71b996da5eefd18b6aaaef5016
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021643"
---
# <a name="explanation-types-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'te açıklama türleri

Açıklamalar, Microsoft SharePoint Syntex'daki modelleri anlama belgenize etiket olarak almak ve ayıklamak istediğiniz bilgileri tanımlamanıza yardımcı olmak için SharePoint Syntex. Açıklama  oluşturmada, bir açıklama türü seçmeniz gerekir. Bu makale, farklı açıklama türlerini ve bunların nasıl kullanıldılarını anlamanıza yardımcı olur.

![Üç açıklama türü gösteren Açıklama oluştur panelinin ekran görüntüsü.](../media/content-understanding/explanation-types.png)

Bu açıklama türleri kullanılabilir:

- [**Tümcecik**](#phrase-list) listesi: Belgede veya ayıklamakta olduğunuz bilgiler için kullanabileceğiniz sözcüklerin, tümceciklerin, sayıların veya diğer karakterlerin listesi. Örneğin, doktorları *yönlendiren metin dizesi* tanım istediğiniz tüm Tıbbi Referans belgesinde yer alır. Ya *da tanımta* bulundurduyuz tüm Tıbbi Referans belgelerinden başvuran doktorların telefon numarası.

- [**Normal ifade**](#regular-expression): Belirli karakter desenlerini bulmak için desen eşleştirmesi içeren bir notasyonu kullanır. Örneğin, bir belge kümesinde e-posta adresi deseninin tüm örneklerini *bulmak* için normal bir ifade kullanabilirsiniz.

- [**Yakınlık**](#proximity): Açıklamaların birbirine yakın olduğunu açıklar. Örneğin, sokak *numarası* tümcecik listesi, aralarında belirteç olmadan  sokak adı tümceciği listesinden hemen önce yer alır (bu makalenin devamlarında belirteçler hakkında bilgi alırsınız). Yakınlık türünü kullanmak için modelinize en az iki açıklama yazmanız gerekir, yoksa seçenek devre dışı bırakılır.

## <a name="phrase-list"></a>Tümcecik listesi

Tümcecik listesi açıklama türü tipik olarak bir belgeyi modeliniz aracılığıyla tanımlamak ve sınıflandırmak için kullanılır. Başvuruta olan doktor *etiketi* örneğinde de açıklandığı gibi, bu tanım ınduz belgelerde tutarlı bir şekilde tutarlı olarak yer alan bir sözcük, tümcecik, sayı veya karakter dizesidir.

Yakalamakta olduğu tümcecik belgenizin içinde tutarlı bir konumda yer alıyorsa, açıklamanız ile daha iyi bir başarı elde etmek için bir zorunluluk değildir. Örneğin, *başvurusal doktor* etiketi tutarlı bir şekilde belgenin ilk paragrafta yer alıyor olabilir. Tümceciğin bulunduğu **[](explanation-types-overview.md#configure-where-phrases-occur-in-the-document)** belirli alanları seçmek için, özellikle de bu tümceciğin belgenizin birden çok konumda yer alıyor olma ihtimali varsa, belgenin gelişmiş ayarında Tümceciklerin nerede olduğunu yapılandır ayarını da kullanabilirsiniz.

Büyük/küçük harfe duyarlılık etiketinizi tanımlamanız için bir zorunluluksa tümcecik liste türünü kullanmak, Yalnızca tam büyük harfe duyarlı onay kutusunu seçerek bunu **açıklamanıza** göre belirtmenize olanak sağlar.

![Büyük/küçük harf duyarlılığı.](../media/content-understanding/case-sensitivity.png)

Bir tümcecik türü, özellikle tarih, telefon numarası ve kredi kartı numarası gibi farklı biçimlerde bilgileri tanımlayan ve ayıklatan bir açıklama  oluşturmak için kullanışlıdır. Örneğin, tarih birçok farklı biçimlerde görüntülenebilir (1/1/2020, 1-1-2020, 01/01/20, 01/01/2020 veya Oca 1,2020). Tümcecik listesi tanımlamak, tanımlamaya ve ayıklamaya çalışırken verilerde olası çeşitlemeleri yakalayarak açıklamanızı daha verimli hale getirir.

Telefon *numarası örneği için* , modelin tanımları olan tüm Tıbbi Referans belgelerinden, yönlendirmede olan her doktor için telefon numarasını ayıklarsiniz. Açıklamayı ekleyebilirsiniz; olası çeşitlemeleri yakalamak için, belgenize bir telefon numarasının görüntülebilirsiniz farklı biçimler yazın.

![Telefon tümceciği desenlerini seçin.](../media/content-understanding/pattern-list.png)

Bu örnekte, Gelişmiş **Ayarlar** tümcecik listesinde kullanılan her "0" değerini 0 ile 9 arasında bir basamak olacak şekilde tanımak için **0-9** arasında herhangi bir rakam seçin.

![0-9 arasında herhangi bir rakam.](../media/content-understanding/digit-identity.png)

Benzer şekilde, metin karakterleri içeren bir tümcecik listesi oluşturursanız, tümcecik listesinde kullanılan her "a" karakterini "a" ile "z" arasında bir karakter olarak tanımak için **A-z** arasında herhangi bir harf onay kutusunu seçin.

Örneğin, bir Tarih tümcecik  listesi 1 Ocak *2020* gibi bir tarih biçiminin tanınması için gerekenler:

- İfade *listennize aaa 0, 0000* ve *aaa 00, 0000* ekleyin.
- **A-z'den herhangi bir harfin de seçili** olduğundan emin olun.

![A-z harfinden herhangi bir harf.](../media/content-understanding/any-letter.png)

Tümcecik listesinde büyük/küçük harfeleştirme gereksinimleriniz varsa, Yalnızca tam olarak **büyük harfe özelleştirme onay kutusunu** seçebilirsiniz. Tarih örneğinde, ayın ilk harfinin büyük harfle yaz  özelikli olması için:

- İfade *listennize Aaa 0, 0000* *ve Aaa 00, 0000* ekleyin.
- Yalnızca tam büyük **harfeleştirme'nin de** seçili olduğundan emin olun.

![Yalnızca tam büyük harfeleştirme.](../media/content-understanding/exact-caps.png)

> [!NOTE]
> Tümcecik listesi açıklamasını el ile oluşturmak yerine, açıklama [](explanation-templates.md) kitaplığını kullanarak tarih, telefon numarası veya kredi kartı numarası gibi yaygın bir tümcecik listesi listesi için tümcecik *listesi şablonları kullanın*.

## <a name="regular-expression"></a>Normal ifade

Normal bir ifade açıklama türü, belgelerde belirli metin dizelerini bulamanıza ve tanımlamanıza yardımcı olacak desenler oluşturmanıza olanak sağlar. Şu şekilde büyük miktarlardaki metni hızla ayrıştırmak için normal ifadeleri kullanabilirsiniz:

- Belirli karakter desenlerini bulma.
- Metnin önceden tanımlanmış bir desenle (e-posta adresi gibi) eş olduğundan emin olmak için metni doğrula.
- Metin alt dizelerini ayıklama, düzenleme, değiştirme veya silme.

Normal bir ifade türü, özellikle e-posta adresleri, banka hesap numaraları veya URL'ler gibi benzer biçimlerde bilgileri tanımlayan ve ayık eden bir açıklama  oluşturmak için kullanışlıdır. Örneğin, E-posta megan@contoso.com gibi bir e-posta adresi belirli bir desenle görüntülenir ("bu" ilk kısımdır ve "com" ise son bölüm).

E-posta adresinin normal ifadesi: **[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+.[ A-Za-z]{2,6}**.

Bu ifade, şu sırayla beş bölümden oluşur:

1. Herhangi bir miktarda aşağıdaki karakter:

   a. A'dan z'ye harfler

   b. 0-9 arasında sayılar

   c. Nokta, alt çizgi, yüzde veya çizgi

2. @ simgesi

3. E-posta adresinin ilk bölümüyle aynı karakterler miktarda

4. Dönem

5. İki ile altı harf

Normal bir ifade açıklama türü eklemek için:

1. Açıklama oluştur **panelinde Açıklama türü'nin** **altında Normal ifade'yi** **seçin**.

   ![Normal İfade'nin seçili olduğu Açıklama oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/create-regular-expression.png)

2. Normal ifade metin kutusuna bir ifade **yazabilirsiniz** veya Şablondan normal **ifade ekle'yi seçin**.

   Şablon kullanarak normal bir ifade eklerken, bu şablon adı ve normal ifadeyi otomatik olarak metin kutusuna ekler. Örneğin, E-posta adresi **şablonunu seçerseniz** , **Açıklama oluştur** paneli doldurulur.

   ![E-posta adresi şablonunun uygulandığı Açıklama oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/create-regular-expression-email.png)

### <a name="limitations"></a>Sınırlamalar

Aşağıdaki tablo, şu anda normal ifade desenlerinde kullanılabilen satır içi karakter seçeneklerini gösterir.

|Seçenek  |Durum  |Geçerli işlevsellik  |
|---------|---------|---------|
|Büyük/küçük harfe duyarlılık | Şu anda desteklenmiyor. | Gerçekleştirilen tüm eşleşmeler büyük/harfe duyarlı değildir.  |
|Çizgi tutturucuları     | Şu anda desteklenmiyor. | Dizede eşleşmenin gerçekleşmesi gereken belirli bir konum belirtemezseniz.   |

## <a name="proximity"></a>Yakınlık

Yakınlık açıklama türü, başka bir veri parçasının ona ne kadar yakın olduğunu tanımlayarak modelinizin verileri tanımlamalarına yardımcı olur. Örneğin, modelinize göre hem müşteri sokak adresi numarasını hem de telefon numarasını etiketleen *iki* açıklama *tanımlattınız*.

Müşteri telefon numaralarının her zaman açık adres numaradan önce görüntüde olduğunu fark etmez.

Alex Wilburn<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Telefon numarası açıklamasının, belgeleriniz içinde açık adres numarasını daha iyi tanımlamak için yakınlık açıklamasını kullanın.

![Yakınlık açıklaması.](../media/content-understanding/proximity.png)

> [!NOTE]
> Normal ifadeler şu anda yakınlık açıklama türüyle kullanılamaz.

#### <a name="what-are-tokens"></a>Belirteç nedir?

Yakınlık açıklaması türünü kullanmak için, belirteci anlamalısınız. Belirteçlerin sayısı, yakınlık açıklamasının bir açıklamadan diğerine uzaklığı nasıl ölçür? Belirteç, harflerin ve sayıların kesintisiz bir aralığıdır (boşluk veya noktalama işareti dahil değildir).

Aşağıdaki tabloda bir tümceciğin belirteç sayısını belirlemeyle ilgili örnekler verilmiştir.

|İfade|Belirteç sayısı|Açıklama|
|--|--|--|
|`Dog`|1|Noktalama işareti veya boşluklar yok tek sözcük.|
|`RMT33W`|1|Kayıt konum belirleyicisi numarası. Sayı ve harf içerebilir, ancak noktalama işareti yok.|
|`425-555-5555`|5|Bir telefon numarası. Her noktalama işareti tek bir belirteçtir, yani `425-555-5555` 5 belirteçtir:<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555` |
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`<br>|

#### <a name="configure-the-proximity-explanation-type"></a>Yakınlık açıklama türünü yapılandırma

Örneğin, açık adres numarası açıklamasından telefon numarası açıklamasında belirteç sayısı *aralığını tanımlamak için* yakınlık *ayarını yapılandırabilirsiniz* . Telefon numarası ile sokak adresi numarası arasında belirteç yoktur, çünkü en küçük aralığın "0" olduğunu fark edersiniz.

Ancak örnek belgelerde bazı telefon numaraları (mobil *) olarak ekli olarak eklenir*.

Nestor Wilke<br>
111-111-1111 (mobil)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

(Mobil) üç *belirteç vardır*:

|İfade|Belirteç sayısı|
|--|--|
|(|1|
|mobil|2|
|)|3|

Yakınlık ayarını 0 ile 3 arasında bir aralık olacak şekilde yapılandırabilirsiniz.

![Yakınlık örneği.](../media/content-understanding/proximity-example.png)

## <a name="configure-where-phrases-occur-in-the-document"></a>Tümceciklerin belgede nerede olduğunu yapılandırma

Bir açıklama ekleyebilirsiniz; varsayılan olarak, ayıklamaya çalışırken tüm belgede arama vardır. Ancak, belgede bir **tümceciğin** oluştuğu belirli bir konumu yalıtmanıza yardımcı olmak için Bu tümceciklerin nerede oluştuğu gelişmiş ayarını kullanabilirsiniz. Bu ayar, bir tümceciğin benzer örnekleri belgenin başka bir yerde görünebilir ve doğru ayarın seçildiğinden emin olmak istediğiniz durumlarda kullanışlıdır.

Tıbbi Referans belge örneğimize başvururken, *başvuru* doktordan her zaman belgenin ilk paragrafı bahsediliyor. Bu **tümceciklerin** nerede olduğu ayarıyla, bu etiket için belgenin yalnızca başlangıç bölümünde veya başka bir konumda arama yapmak üzere bu örnekte açıklamanızı yapılandırabilirsiniz.

![Bu tümceciklerin nerede bulunduğu ayarı.](../media/content-understanding/phrase-location.png)

Bu ayar için aşağıdaki seçenekleri kullanabilirsiniz:

- Dosyanın herhangi bir yerinde: Tüm belgede tümcecik aranır.

- Dosyanın başı: Belge, en baştan tümceciğin bulunduğu konuma kadar aranır.

   ![Dosyanın başı.](../media/content-understanding/beginning-of-file.png)

    Görüntüleyicide, seçme kutusunu el ile ayarerek aşamanın bulunduğu konumu da ekleyebilirsiniz. Bitiş **konumu** değeri, seçtiğiniz alanda yer alan belirteç sayısını gösterecek şekilde güncelleştirmesi olur. Seçili alanı ayarlamak **için yanı sıra** Bitiş konumu değerini de güncelleştirin.

   ![Dosya konumu kutusunun başlangıcı.](../media/content-understanding/beginning-box.png)

- Dosyanın sonu: Belge, sonundan tümceciğin bulunduğu konuma kadar aranır.

   ![Dosyanın sonu.](../media/content-understanding/end-of-file.png)

    Görüntüleyicide, seçme kutusunu el ile ayarerek aşamanın bulunduğu konumu da ekleyebilirsiniz. Başlangıç **konumu** değeri, seçtiğiniz alanda yer alan belirteç sayısını gösterecek şekilde güncelleştirmesi olur. Seçili alanı ayarlamak için olduğu gibi Başlangıç konumu değerini de güncelleştirin.

   ![Dosya sonu kutusu.](../media/content-understanding/end-box.png)

- Özel aralık: Belge, tümceciğin konumu için belirtilen aralık içinde aranır.

   ![Özel aralık.](../media/content-understanding/custom-file.png)

    Görüntüleyicide, seçme kutusunu el ile ayarerek aşamanın bulunduğu konumu da ekleyebilirsiniz. Bu ayar için bir Başlangıç ve **Bitiş konumu** **seçmeniz** gerekir. Bu değerler, belgenin başlangıcından itibaren belirteç sayısını temsil eder. Bu değerleri el ile girebilirsiniz, ancak seçim kutusunu görüntüleyicide el ile ayarlamak daha kolaydır.
    
## <a name="considerations-when-configuring-explanations"></a>Açıklamaları yapılandırarak göz önünde bulundurulması gereken noktalar
Sınıflandırıcı eğitimde, daha öngörülebilir sonuçlar üretecek birkaç şey olduğunu unutmayın:

- Ne kadar çok eğitim belgesiyle eğitersiniz, sınıflandırıcı o kadar doğru olur.  Mümkünse 5'den fazla uygun belge kullanın ve 1'den fazla kötü belge kullanın.  Üzerinde çalışmakta olduğunuz kitaplıklarda çeşitli belge türleri varsa, her türlerden birkaçı daha öngörülebilir sonuçlara neden olur.
- Belgeyi etiketleme, eğitim sürecinde önemli bir rol oynar.  Bunlar, modeli eğitmek için açıklamalarla birlikte kullanılır.  Çok fazla içeriği olan belgelerle bir sınıflandırıcı eğitim görüyoruz.  Açıklama belge içinde herhangi bir şey ile eşleşmeyebilirsiniz, ancak "iyi" belgesi olarak etiketlenmiş olması nedeniyle, eğitim sırasında bunun bir eşleşme olduğunu da görüyorsunuz.
- Açıklamalar oluştururken, bunun bir eşleşme olup olmadığını belirlemek için etiketle birlikte OR mantığını kullanır.  AND mantığı kullanan normal ifade daha öngörülebilir olabilir.  Burada, eğitim belgelerinde gerçek belgeler üzerinde  kullanmak için kullanabileceğiniz örnek bir normal ifade vemektedir.  Kırmızı renkle vurgulanan metnin, arıyor olacağınız tümcecik olduğunu unutmayın.

    <pre>(?=.*network provider)(?=.*participating providers).*</pre>
    
- Etiketler ve açıklamalar birlikte çalışır ve modelin eğitimi için kullanılır.  Bu, yapılandırılan her değişkene uygulanan bir dizi ve hassas ağırlık veya tahminle bir dizi kural değildir.  Eğitimde kullanılan belgelerin çeşitlemesi ne kadar fazla ise modelde daha doğru bir doğruluk sağlayacaktır.

### <a name="see-also"></a>Ayrıca bkz.

[E-postada açıklama SharePoint Syntex](explanation-templates.md)
