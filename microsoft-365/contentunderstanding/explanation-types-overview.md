---
title: Microsoft SharePoint Syntex'da açıklama türleri
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
description: Microsoft SharePoint Syntex'da tümcecik listesi, normal ifade ve yakınlık açıklaması türleri hakkında daha fazla bilgi edinin.
ms.openlocfilehash: ae31ee3e4d9550c54f884360f3beea960db47b20
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824794"
---
# <a name="explanation-types-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da açıklama türleri

Açıklamalar, Microsoft SharePoint Syntex'daki belge anlama modellerinizde etiketlemek ve ayıklamak istediğiniz bilgileri tanımlamaya yardımcı olmak için kullanılır. Açıklama oluştururken bir açıklama türü seçmeniz gerekir. Bu makale, farklı açıklama türlerini ve bunların nasıl kullanıldığını anlamanıza yardımcı olur.

![Üç açıklama türünü gösteren Açıklama oluştur panelinin ekran görüntüsü.](../media/content-understanding/explanation-types.png)

Bu açıklama türleri kullanılabilir:

- [**Tümcecik listesi**](#phrase-list): Belgede veya ayıkladığınız bilgilerde kullanabileceğiniz sözcüklerin, tümceciklerin, sayıların veya diğer karakterlerin listesi. Örneğin, *başvuruda bulunan* metin dizesi doktor, tanımladığınız tüm Tıbbi Referans belgelerinde yer alır. Ya da tanımladığınız tüm Tıbbi Referans belgelerinden başvuran doktorun *telefon numarası* .

- [**Normal ifade**](#regular-expression): Belirli karakter desenlerini bulmak için desen eşleştirme gösterimi kullanır. Örneğin, bir belge kümesindeki *e-posta adresi* deseninin tüm örneklerini bulmak için normal bir ifade kullanabilirsiniz.

- [**Yakınlık**](#proximity): Açıklamaların birbirine ne kadar yakın olduğunu açıklar. Örneğin, *sokak numarası* tümcecik listesi, arasında belirteç olmadan *sokak adı* tümcecik listesinden hemen önce gider (bu makalenin devamındaki belirteçler hakkında bilgi edineceksiniz). Yakınlık türünü kullanmak için modelinizde en az iki açıklama olması gerekir, aksi takdirde seçenek devre dışı bırakılır.

## <a name="phrase-list"></a>Tümcecik listesi

İfade listesi açıklama türü genellikle modeliniz aracılığıyla belgeyi tanımlamak ve sınıflandırmak için kullanılır. *Başvuruda bulunan doktor* etiketi örneğinde açıklandığı gibi, tanımladığınız belgelerde tutarlı olarak bulunan bir sözcük, tümcecik, sayı veya karakter dizesidir.

Bir gereksinim olmasa da, yakaladığınız tümcecik belgenizde tutarlı bir konumda bulunuyorsa açıklamanızla daha iyi bir başarı elde edebilirsiniz. Örneğin, *başvuran doktor* etiketi tutarlı bir şekilde belgenin ilk paragrafında bulunabilir. Ayrıca, özellikle de **[tümceciği belgenizdeki](explanation-types-overview.md#configure-where-phrases-occur-in-the-document)** birden çok konumda bulunma olasılığı varsa, tümceciğin bulunduğu belirli alanları seçmek için Belge gelişmiş ayarında tümceciklerin nerede olduğunu yapılandır ayarını da kullanabilirsiniz.

Büyük/küçük harf duyarlılığı etiketinizi tanımlamada bir gereksinimse, tümcecik listesi türünü kullanmak **, Yalnızca tam büyük harf** kullanımı onay kutusunu seçerek açıklamanızda bunu belirtmenize olanak tanır.

![Büyük/küçük harf duyarlılığı.](../media/content-understanding/case-sensitivity.png)

İfade türü özellikle tarihler, telefon numaraları ve kredi kartı numaraları gibi farklı biçimlerdeki bilgileri tanımlayan ve ayıklayan bir açıklama oluşturduğunuzda kullanışlıdır. Örneğin, tarih birçok farklı biçimde görüntülenebilir (1/1/2020, 1-1-2020, 01/01/20, 01/01/2020 veya 1 Ocak 2020). Tümcecik listesi tanımlamak, tanımlamaya ve ayıklamaya çalıştığınız verilerdeki olası varyasyonları yakalayarak açıklamanızı daha verimli hale getirir.

*Telefon numarası* örneği için, modelin tanımladığını tüm Tıbbi Referans belgelerinden başvuran her doktorun telefon numarasını ayıklarsınız. Açıklamayı oluşturduğunuzda, olası varyasyonları yakalayabilmeniz için belgenizde telefon numarasının görüntüleyebileceği farklı biçimleri yazın.

![Telefon sayı tümceciği desenleri.](../media/content-understanding/pattern-list.png)

Bu örnekte **, Gelişmiş Ayarlar** tümcecik listenizde kullanılan her "0" değerinin 0 ile 9 arasında herhangi bir rakam olduğunu tanımak için **0-9** arasında herhangi bir basamak onay kutusunu seçin.

![0-9 arası herhangi bir rakam.](../media/content-understanding/digit-identity.png)

Benzer şekilde, metin karakterleri içeren bir tümcecik listesi oluşturursanız, tümcecik listesinde kullanılan her "a" karakterini "a" ile "z" arasında herhangi bir karakter olarak tanımak için **A-z'den** herhangi bir harf onay kutusunu seçin.

Örneğin, **bir Tarih** tümcecik listesi oluşturursanız ve *1 Ocak 2020* gibi bir tarih biçiminin tanındığından emin olmak istiyorsanız şunları yapmanız gerekir:

- tümcecik listenize *aaa 0, 0000* ve *aaa 00, 0000* ekleyin.
- **A-z harfinden herhangi bir harfin** de seçili olduğundan emin olun.

![A-z'den gelen herhangi bir harf.](../media/content-understanding/any-letter.png)

Tümcecik listenizde büyük harfe çevirme gereksinimleri varsa **, Yalnızca tam büyük harfe çevirme** onay kutusunu seçebilirsiniz. Tarih örneğinde, ayın ilk harfinin büyük harfle yazılması gerekiyorsa şunları yapmanız gerekir:

- Tümcecik listenize *Aaa 0, 0000* ve *Aaa 00, 0000* ekleyin.
- **Yalnızca tam büyük harfe çevirme'nin** de seçili olduğundan emin olun.

![Yalnızca tam büyük harf kullanımı.](../media/content-understanding/exact-caps.png)

> [!NOTE]
> Tümcecik listesi açıklamasını el ile oluşturmak yerine, *tarih*, *telefon numarası* veya *kredi kartı numarası* gibi ortak bir tümcecik listesi için tümcecik listesi şablonlarını kullanmak için [açıklama kitaplığını](explanation-templates.md) kullanın.

## <a name="regular-expression"></a>Normal ifade

Normal ifade açıklama türü, belgelerde belirli metin dizelerini bulmanıza ve tanımlamanıza yardımcı olan desenler oluşturmanıza olanak tanır. Büyük miktarda metni hızla ayrıştırmak için normal ifadeleri kullanabilirsiniz:

- Belirli karakter desenlerini bulma.
- Önceden tanımlanmış bir desenle (e-posta adresi gibi) eşleştiğinden emin olmak için metni doğrulayın.
- Metin alt dizelerini ayıklayın, düzenleyin, değiştirin veya silin.

Normal ifade türü özellikle e-posta adresleri, banka hesap numaraları veya URL'ler gibi benzer biçimlerde bilgileri tanımlayan ve ayıklayan bir açıklama oluşturduğunuzda kullanışlıdır. Örneğin, megan@contoso.com gibi bir e-posta adresi belirli bir düzende görüntülenir ("megan" ilk bölüm, "com" ise son bölümdür).

E-posta adresi için normal ifade: **[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+.[ A-Za-z]{2,6}**.

Bu ifade şu sırayla beş bölümden oluşur:

1. Aşağıdaki karakterlerden herhangi biri:

   a. A'dan z'ye mektuplar

   b. 0-9 arası sayılar

   c. Nokta, alt çizgi, yüzde veya tire

2. @ simgesi

3. E-posta adresinin ilk bölümüyle aynı karakter miktarı

4. Bir dönem

5. İki ile altı harf

Normal ifade açıklama türü eklemek için:

1. **Açıklama oluştur** panelindeki **Açıklama türü'nin** altında **Normal ifade'yi** seçin.

   ![Normal İfade'nin seçili olduğu Açıklama oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/create-regular-expression.png)

2. **Normal ifade** metin kutusuna bir ifade yazabilir veya **Şablondan normal ifade ekle'yi** seçebilirsiniz.

   Şablon kullanarak normal ifade eklediğinizde, ad ve normal ifade otomatik olarak metin kutusuna eklenir. Örneğin, **E-posta adresi** şablonunu seçerseniz, **Açıklama oluştur** paneli doldurulur.

   ![E-posta adresi şablonunun uygulandığı Açıklama oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/create-regular-expression-email.png)

### <a name="limitations"></a>Sınırlamalar

Aşağıdaki tabloda, normal ifade desenlerinde şu anda kullanılamayan satır içi karakter seçenekleri gösterilmektedir.

|Seçeneği|Durum|Geçerli işlevsellik|
|---|---|---|
|Büyük/küçük harf duyarlılığı|Şu anda desteklenmiyor.|Gerçekleştirilen tüm eşleşmeler büyük/küçük harfe duyarlı değildir.|
|Çizgi tutturucular|Şu anda desteklenmiyor.| Dizede eşleşmenin olması gereken belirli bir konum belirtilemiyor.|

## <a name="proximity"></a>Yakınlık

Yakınlık açıklaması türü, modelinizin başka bir veri parçasının ona ne kadar yakın olduğunu tanımlayarak verileri tanımlamasına yardımcı olur. Örneğin, modelinizde hem müşteri *adres numarasını* hem de *telefon numarasını* etiketleyen iki açıklama tanımlamış olduğunuzu varsayalım.

Müşteri telefon numaralarının her zaman sokak adres numarasından önce göründüğüne dikkat edin.

Alex Wilburn<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Yakınlık açıklamasını kullanarak, telefon numarası açıklamasının belgelerinizdeki sokak adresi numarasını daha iyi tanımlamak için ne kadar uzak olduğunu tanımlayın.

![Yakınlık açıklaması.](../media/content-understanding/proximity.png)

> [!NOTE]
> Normal ifadeler şu anda yakınlık açıklaması türüyle kullanılamaz.

#### <a name="what-are-tokens"></a>Belirteçler nedir?

Yakınlık açıklaması türünü kullanmak için belirtecin ne olduğunu anlamanız gerekir. Belirteç sayısı, yakınlık açıklamasının bir açıklamadan diğerine olan mesafeyi nasıl ölçt olduğudur. Belirteç, harflerin ve sayıların sürekli yayılma alanıdır (boşluklar veya noktalama işaretleri dahil değildir).

Aşağıdaki tabloda, bir tümcecikteki belirteç sayısını belirlemeye yönelik örnekler gösterilmektedir.

|Ifa -de|Belirteç sayısı|Açıklama|
|---|---|---|
|`Dog`|1|Noktalama işareti veya boşluk içermeyen tek bir sözcük.|
|`RMT33W`|1|Kayıt bulucu numarası. Sayı ve harf içerebilir, ancak noktalama işaretleri yoktur.|
|`425-555-5555`|5|Telefon numarası. Her noktalama işareti tek bir belirteçtir ve `425-555-5555` 5 belirteçtir:<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555`|
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`|

#### <a name="configure-the-proximity-explanation-type"></a>Yakınlık açıklaması türünü yapılandırma

Örneğin, *telefon numarası* açıklamasındaki belirteç sayısının aralığını *açık adres numarası* açıklamasından tanımlamak için yakınlık ayarını yapılandırın. Telefon numarası ile sokak adresi numarası arasında belirteç olmadığından en düşük aralığın "0" olduğuna dikkat edin.

Ancak örnek belgelerdeki bazı telefon numaraları *(mobil)* ile eklenir.

Nestor Wilke<br>
111-111-1111 (mobil)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

*(mobil)* içinde üç belirteç vardır:

|Ifa -de|Belirteç sayısı|
|--|--|
|(|1|
|Mobil|2|
|)|3|

Yakınlık ayarını 0 ile 3 arasında bir aralığa sahip olacak şekilde yapılandırın.

![Yakınlık örneği.](../media/content-understanding/proximity-example.png)

## <a name="configure-where-phrases-occur-in-the-document"></a>Tümceciklerin belgede nerede olduğunu yapılandırma

Bir açıklama oluşturduğunuzda, varsayılan olarak ayıklamaya çalıştığınız tümceciği belgenin tamaminde arama yapılır. Ancak, belgede bir **tümceciğin oluştuğu** belirli bir konumu yalıtmaya yardımcı olması için bu tümceciklerin oluştuğu yer gelişmiş ayarını kullanabilirsiniz. Bu ayar, bir tümceciğin benzer örneklerinin belgede başka bir yerde görünebileceği ve doğru ifadenin seçildiğinden emin olmak istediğiniz durumlarda kullanışlıdır.

Tıbbi Referans belgesi örneğimize atıfta bulunarak, *başvuran doktor* her zaman belgenin ilk paragrafında belirtilir. **Bu tümceciklerin oluştuğu yer** ayarıyla, bu örnekte açıklamanızı yalnızca belgenin başlangıç bölümünde veya belgenin oluşabileceği başka bir konumda bu etiketi aramak üzere yapılandırabilirsiniz.

![Bu tümceciklerin nerede oluştuğu ayarı.](../media/content-understanding/phrase-location.png)

Bu ayar için aşağıdaki seçenekleri belirleyebilirsiniz:

- Dosyanın herhangi bir yerinde: Tümcecik için belgenin tamamı arandı.

- Dosyanın başlangıcı: Belgede baştan tümcecik konumuna kadar arama yapılır.

   ![Dosyanın başlangıcı.](../media/content-understanding/beginning-of-file.png)

    Görüntüleyicide, aşamanın gerçekleştiği konumu içerecek şekilde seçme kutusunu el ile ayarlayabilirsiniz. **Bitiş konumu** değeri, seçtiğiniz alanın içerdiği belirteç sayısını gösterecek şekilde güncelleştirilir. Seçilen alanı ayarlamak için **Bitiş konumu** değerini de güncelleştirebilirsiniz.

   ![Dosya konumu başlangıcı kutusu.](../media/content-understanding/beginning-box.png)

- Dosyanın sonu: Belgenin sonundan tümcecik konumuna kadar arama yapılır.

   ![Dosya sonu.](../media/content-understanding/end-of-file.png)

    Görüntüleyicide, aşamanın gerçekleştiği konumu içerecek şekilde seçme kutusunu el ile ayarlayabilirsiniz. **Başlangıç konumu** değeri, seçtiğiniz alanın içerdiği belirteç sayısını gösterecek şekilde güncelleştirilir. Seçilen alanı ayarlamak için Başlangıç konumu değerini de güncelleştirebilirsiniz.

   ![Dosya sonu kutusu.](../media/content-understanding/end-box.png)

- Özel aralık: Belge, belirtilen aralıkta tümcecik konumu için arandı.

   ![Özel aralık.](../media/content-understanding/custom-file.png)

    Görüntüleyicide, aşamanın gerçekleştiği konumu içerecek şekilde seçme kutusunu el ile ayarlayabilirsiniz. Bu ayar için bir **Başlangıç** ve **Bitiş** konumu seçmeniz gerekir. Bu değerler, belgenin başından itibaren belirteç sayısını temsil eder. Bu değerleri el ile girebilirsiniz ancak görüntüleyicideki seçim kutusunu el ile ayarlamak daha kolaydır.

## <a name="considerations-when-configuring-explanations"></a>Açıklamaları yapılandırırken dikkat edilmesi gerekenler

Bir sınıflandırıcıyı eğitirken, daha öngörülebilir sonuçlara neden olacak dikkate alınması gereken birkaç şey vardır:

- Ne kadar çok belgeyle eğitildiyseniz sınıflandırıcı o kadar doğru olur.  Mümkün olduğunda, 5'ten fazla iyi belge kullanın ve 1'den fazla hatalı belge kullanın.  Üzerinde çalıştığınız kitaplıkların içinde birkaç farklı belge türü varsa, her türden birkaçı daha öngörülebilir sonuçlara yol açar.
- Belgenin etiketlenmesi eğitim sürecinde önemli bir rol oynar.  Modeli eğitmek için açıklamalarla birlikte kullanılırlar.  Sınıflandırıcıyı çok fazla içeriği olmayan belgelerle eğitirken bazı anomaliler görebilirsiniz.  Açıklama belgedeki hiçbir şeyle eşleşmeyebilir, ancak "iyi" bir belge olarak etiketlendiği için eğitim sırasında bir eşleşme olduğunu görebilirsiniz.
- Açıklamalar oluştururken, bir eşleşme olup olmadığını belirlemek için etiketle birlikte OR mantığını kullanır.  AND mantığını kullanan normal ifade daha tahmin edilebilir olabilir.  Burada, gerçek belgeler üzerinde eğitim olarak kullanılacak örnek bir normal ifade verilmiştir.  Kırmızıyla vurgulanan metnin, aradığınız tümcecikler olduğuna dikkat edin.

    <pre>(?=.*network provider)(?=.*participating providers).*</pre>

- Etiketler ve açıklamalar birlikte çalışır ve modeli eğiterken kullanılır.  Bu, yapılandırılmış olan her değişkene çift ve hassas ağırlıklar veya tahmin uygulanabilen bir dizi kural değildir.  Eğitimde kullanılan belgelerin varyasyonu ne kadar büyük ise modelde daha fazla doğruluk sağlar.

### <a name="see-also"></a>Ayrıca bkz.

[SharePoint Syntex'de açıklama şablonlarını kullanma](explanation-templates.md)
