---
title: Hassas bilgi türleri için ortak kullanım senaryoları
f1.keywords:
- NOCSH
ms.author: chrfox
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Yaygın hassas bilgi türleri kullanım örneği senaryolarını uygulama
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 54945a3ac6f13ed541cef212305f713d8b5d2b73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633377"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Hassas bilgi türleri için ortak kullanım senaryoları

Bu makalede bazı yaygın hassas bilgi türü (SIT) kullanım örneği senaryolarının nasıl uygulandığı açıklanmaktadır. Bu yordamları örnek olarak kullanabilir ve bunları özel gereksinimlerinize uyarlayabilirsiniz.

## <a name="protect-credit-card-numbers"></a>Kredi kartı numaralarını koruma

Contoso Bank'ın, verdikleri kredi kartı numaralarını hassas olarak sınıflandırması gerekir. Kredi kartları altı basamaklı bir dizi desenle başlar. Yalnızca altı basamaklı düzenlerinden başlayarak kredi kartı numaralarını algılamak için kullanıma açık kredi kartı tanımını özelleştirmek istiyor.

**Önerilen çözüm**

1. Kredi kartı SIT'in bir kopyasını oluşturun. Kredi kartı [SIT'ini kopyalamak için hassas bir bilgi türünü kopyalamak ve değiştirmek](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) için adımları kullanın.
1. Yüksek güvenilirlik desenini düzenleyin. [Hassas bilgi türü desenini düzenleme veya silme adımlarını](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern) izleyin.
1. 'şununla başlar' denetimi ekleyin ve bölme basamasının listesini ekleyin (biçimlendirilmemiş & biçimlendirilmiş). Örneğin, yalnızca 411111 & 433512 ile başlayan kredi kartlarının geçerli kabul edilmesini sağlamak için aşağıdakileri 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512 listesine ekleyin.
1. Düşük güvenilirlik deseni için 2. & 3. adımı yineleyin.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Sosyal Güvenlik numaralarına benzer test numaraları

Contoso, Sosyal Güvenlik Numarası (SSN) Microsoft Purview veri kaybı önleme (DLP) ilkesinde hatalı pozitif eşleşmeleri tetikleyen birkaç dokuz basamaklı test numarası tanımladı. Bu sayıları SSN için geçerli eşleşmeler listesinden dışlamak istiyorlar.

**Önerilen çözüm**

1. SSN SIT'in bir kopyasını oluşturun. SSN SIT'i [kopyalamak için hassas bir bilgi türünü kopyalamak ve değiştirmek](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) için adımları kullanın.
1. Yüksek güvenilirlik desenini düzenleyin. [Hassas bilgi türü desenini düzenleme veya silme adımlarını](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern) izleyin.
1. Dışlanacak sayıları 'belirli değerleri hariç tut' ek denetimine ekleyin. Örneğin, 239-23-532 & 23923532 hariç tutmak için yalnızca 23923532 eklemek yeterli olacaktır
1. Diğer güvenilirlik desenleri için de 2. & 3. adımı yineleyin

## <a name="phone-numbers-in-signature-trigger-match"></a>İmza tetikleyicisindeki telefon numaraları eşleşmesi

Avustralya merkezli Contoso, e-posta imzalarındaki telefon numaralarının Avustralya şirket numarası DLP ilkesiyle eşleşme tetiklediğini bulur.

**Önerilen çözüm**

"Telefon", "Mobil", "e-posta", "Teşekkürler ve saygılar" gibi e-posta imzasında yaygın olarak kullanılan anahtar sözcükleri içeren bir anahtar sözcük listesi kullanarak destekleyici öğelere bir 'not' grubu ekleyin. Daha iyi doğruluk için bu anahtar sözcük listesinin 50 karakter gibi daha küçük bir değere yakınlığını koruyun. Daha fazla bilgi için bkz. [Özel hassas bilgi türlerini kullanmaya başlama](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>ABA yönlendirme ilkesi tetiklenemiyor

Gerekli anahtar sözcük 300 karakter içinde bulunmadığından DLP ilkesi büyük excel dosyalarında ABA yönlendirme numarası ilkesini tetikleyemiyor.

**Önerilen çözüm**

Yerleşik SIT'in bir kopyasını oluşturun ve anahtar sözcük listesinin "300 karakterden" "Belgede herhangi bir yere" yakınlık değerini değiştirmek için bu kopyayı düzenleyin.

> [!TIP]
> Kuruluşunuzla ilgili anahtar sözcükleri dahil etmek/hariç tutmak için anahtar sözcük listesini düzenleyebilirsiniz.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Olağan dışı sınırlayıcılarla kredi kartı numaraları algılanamıyor

Contoso Bank, çalışanlarından bazılarının kredi kartı numaralarını sınırlayıcı olarak '/' ile paylaştığını fark etti, örneğin 4111/1111/1111/1111; bu, kullanıma hazır kredi kartı tanımı tarafından algılanmıyor. Contoso kendi regex'ini tanımlamak ve LuhnCheck kullanarak doğrulamak istiyor.

**Önerilen çözüm**

1. [Yerleşik hassas bilgi türünü özelleştirme'deki adımları kullanarak Kredi kartı SIT'in bir](customize-a-built-in-sensitive-information-type.md) kopyasını oluşturun.
1. Yeni desen ekleme
1. Birincil öğede normal ifadeyi seçin
1. Normal ifadenin bir parçası olarak '/' içeren normal ifadeyi tanımlayın ve ardından doğrulayıcıyı seçin ve regex'in LuhnCheck değerini de geçtiğinden emin olmak için luhncheck veya func_credit_card seçin.

## <a name="ignore-a-disclaimer-notice"></a>Bildirim bildirimini yoksayma

Birçok kuruluş, kuruluşuna giren veya ayrılan e-posta iletilerinin en üstüne veya altına ve hatta bazı durumlarda kuruluş içinde bile yasal uyarı, açıklama bildirimleri, imzalar veya diğer bilgileri ekler. Çalışanlar, motivasyona dayalı alıntılar, sosyal mesajlar vb. gibi imzalar koyar. Bir sorumluluk reddi veya imza, CC sözlüğünde bulunan terimleri içerebilir ve çok sayıda hatalı pozitif sonuç oluşturabilir.  

Örneğin, tipik bir sorumluluk reddi, hassas veya gizli gibi sözcükler içerebilir ve hassas bilgileri arayan bir ilke bunu bir olay olarak algılar ve bu da çok sayıda hatalı pozitif sonuçla sonuçlanır. Böylece müşterilere yasal uyarıyı yoksayma seçeneği sağlamak hatalı pozitif sonuçları azaltabilir ve uyumluluk ekibinin verimliliğini artırabilir.

### <a name="example-of-disclaimer"></a>Yasal uyarı örneği

Aşağıdaki yasal uyarıyı göz önünde bulundurun:

ÖNEMLİ BİlDİrİm: Bu e-posta iletisinin yalnızca içerebileceği gizli bilgileri almaya hak kazanan kişiler tarafından alınması amaçlanmıştır. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Hedeflenen alıcı değilseniz lütfen bu iletiyi okumayın, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayar sisteminizden tamamen silin.

SIT gizli anahtar sözcüğü algılayacak şekilde yapılandırılmışsa, desen e-postada her bildirim kullanıldığında eşleşmeyi çağırır ve bu da çok sayıda hatalı pozitif sonuç oluşturur.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>SIT'te ön ek ve soneki kullanarak sorumluluk reddini yoksayma

Sorumluluk reddindeki anahtar sözcüklerin örneklerini yoksayma yollarından biri, önce bir önek ve ardından bir sonek olan anahtar sözcük örneklerini dışlamaktır.

Bu uyarıyı göz önünde bulundurun:

ÖNEMLİ BİlDİrİm: Bu e-posta iletisinin yalnızca **içerebileceği gizli bilgileri** *almaya hak kazanan* kişiler tarafından alınması amaçlanmıştır. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Hedeflenen alıcı değilseniz lütfen bu iletiyi okumayın, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayar sisteminizden tamamen silin.

"Gizli" anahtar sözcüğünü iki örneğimiz vardır ve SIT'i ön eklerden (örnekte italik) ve ardından sonekleri (örnekte kalın yazıyla) gelen bu anahtar sözcüğün örneklerini yoksayacak şekilde yapılandırırsak, çoğu durumda sorumluluk reddini yoksaymayı başarabiliriz.

Ön ek ve soneki kullanarak bildirimi yoksaymak için:

1. Geçerli SIT'e, bildirimde yoksaymak istediğimiz ön ek ve sonek metnini anahtar sözcükte dışlamak için ek denetimler ekleyin.
1. Ön eki dışlamak için seçin ve **Önekler** metin kutusuna şu **bilgileri girin**:
1. Soneki dışlamak için seçin ve **Sonekler** metin kutusuna **ve yasal olarak ayrıcalıklı** girin.
1. Aşağıdaki grafikte gösterildiği gibi, bildirimdeki anahtar sözcüklerin diğer örnekleri için bu işlemi yineleyin.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>İkincil öğeleri dışlayarak sorumluluk reddini yoksayma

Dışlanması gereken destekleyici öğelerin (sorumluluk reddindeki örnekler) listesini eklemenin bir diğer yolu da ikincil öğeleri dışlamaktır.

Bu uyarıyı göz önünde bulundurun:

ÖNEMLİ BİlDİrİm: Bu e-posta iletisinin yalnızca içerebileceği gizli bilgileri almaya hak kazanan kişiler tarafından alınması amaçlanmıştır. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Hedeflenen alıcı değilseniz lütfen bu iletiyi okumayın, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayar sisteminizden tamamen silin.

Bu örnekte "gizli" anahtar sözcüğünü iki örneğimiz vardır. SIT'i bu anahtar sözcüğün sorumluluk reddindeki örneklerini yoksayacak şekilde yapılandırırsak (kırmızı olarak altı çizili), çoğu durumda sorumluluk reddini yoksayabiliriz.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Bildirimdeki ek örnekleri dışlamak için desene daha fazla koşul ekleyebilirsiniz.":::

İkincil öğeleri kullanarak bildirimi yoksaymak için:

1. Destekleyici öğelerde **Bu gruptan herhangi biri değil'i** seçin.
1. Yoksaymak istediğimiz sorumluluk reddi örneklerini anahtar sözcük listesi/sözlük olarak ekleyin.
1. Anahtar sözcükleri yoksaymak istediğimiz yeni bir satır olarak ekleyin. Her metnin uzunluğunun 50 karakterden uzun olamaz.
1. Bu öğenin yakınlık değerini birincil öğenin 50-60 karakteri içinde olacak şekilde ayarlayın.
