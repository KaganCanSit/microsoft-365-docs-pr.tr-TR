---
title: Hassas bilgi türleri için yaygın kullanım senaryoları
f1.keywords:
- NOCSH
ms.author: chrfox
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Yaygın hassas bilgi türleri uygulama kullanım durumu senaryoları
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cd11c4843d91923f1ca5e171cc8bfc8e1c64c73d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010071"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Hassas bilgi türleri için yaygın kullanım senaryoları

Bu makalede, bazı yaygın hassas bilgi türü (SIT) kullanım durumu senaryolarını nasıl uygulayacağım açıklanmıştır. Bu yordamları örnek olarak kullanabilir ve özel ihtiyaçlarınıza uyarlanabilirsiniz.

## <a name="protect-credit-card-numbers"></a>Kredi kartı numaralarını koruma

Contoso Bank'in, çıkaracakları kredi kartı numaralarını hassas olarak sınıflandırması gerekir. Kredi kartları altı basamaklı desenlerle başlar. Yalnızca altı basamaklı düzenleriyle başlayan kredi kartı numaralarını algılamak için, ilk kutusundan önce yer alan kredi kartı tanımını özelleştirmek istiyorum.

**Önerilen çözüm**

1. Kredi kartı SIT'in bir kopyasını oluşturun. Kredi kartı [SIT'ini kopyalamak için hassas bilgi türünü](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) kopyalama ve değiştirme adımlarını kullanın.
1. Yüksek güven desenini düzenleyin. Hassas bilgi türü [desenini düzenleme veya silme adımlarını izleyin](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. 'Başlar' ekle onay kutusunu seçin ve ikili rakam listesini ekleyin (biçimlendirilmemiş & biçimlendirildi). Örneğin, yalnızca 411111 & 433512 ile başlayan kredi kartlarının geçerli kabul olmasını sağlamak için, aşağıdaki listeyi 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Düşük güven düzeni için 2. & 3. adımı yinelayın.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Sosyal Güvenlik numaralarına benzer test numaraları

Contoso, Sosyal Güvenlik Numarası (SSN) veri kaybını önleme (DLP) ilkesinde hatalı pozitif eşleşmeleri tetikleyen dokuz basamaklı birkaç test numarası belirledi. SSN için geçerli eşleşmeler listesinden bu sayıları dışarıda tutmak istiyorum.

**Önerilen çözüm**

1. SSN SIT'in bir kopyasını oluşturun. SSN [SIT'i kopyalamak üzere hassas bir bilgi türünü](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) kopyalamak ve değiştirmek için adımları kullanın.
1. Yüksek güven desenini düzenleyin. Hassas bilgi türü [desenini düzenleme veya silme adımlarını izleyin](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. 'Belirli değerleri hariç tut' ek denetiminde hariç tutulacak numaraları ekleyin. Örneğin, 239-23-532 & 23923532 hariç tutmak için yalnızca 23923532 eklemek yeterlidir
1. Diğer güven düzenleri için 2. & 3. adımı yinele

## <a name="phone-numbers-in-signature-trigger-match"></a>Telefon tetikleyicisi eşleşmesinde yer alan numaraları ekleme

Avustralya tabanlı Contoso, e-posta imzalarında yer alan telefon numaralarının Avustralya şirket numarası DLP ilkesi için bir eşleşmeyi tetikle olduğunu bulur.

**Önerilen çözüm**

"Telefon", "Mobile", "email", "Thanks and regards" vb. gibi e-posta imzalarında sık kullanılan anahtar sözcükleri içeren bir anahtar sözcük listesini kullanarak destek öğelerinde "Not" grubu ekleyin. Daha doğru doğruluğu için bu anahtar sözcük listesinin yakınlıklarını 50 karakter gibi daha küçük bir değerle kullanın. Daha fazla bilgi için bkz [. Özel hassas bilgi türleriyle çalışmaya başlama](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>ABA yönlendirme ilkesi tetikleyemiyor

DLP ilkesi büyük Excel dosyalarında ABA yönlendirme numarası ilkesi tetikleyemiyor, çünkü gerekli anahtar sözcük 300 karakter içinde bulunamıyor.

**Önerilen çözüm**

Yerleşik SIT'in bir kopyasını oluşturun ve "300 karakter" olan anahtar sözcük listesinin yakınlıklarını "Belgenin herhangi bir yerinde" olarak değiştirmek için bu kopyayı düzenleyin.

> [!TIP]
> Anahtar sözcük listesini, organizasyonuyla ilgili anahtar sözcükleri dahil etmek/hariç tutmak için düzenleyebilirsiniz.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Sıra dışı sınırlayıcıları olan kredi kartı numaraları algılanamadı

Contoso Bank, çalışanlarından bazılarının kredi kartı numaralarını '/' ile sınırlayıcı olarak paylaştığını fark etti; örneğin 4111/1111/1111/1111, hazır bulunan kredi kartı tanımı tarafından algılanmaz. Contoso, luhnCheck kullanarak kendi kayıt defterlerini tanımlamak ve doğrulamak istiyorum.

**Önerilen çözüm**

1. Yerleşik hassas bilgi türünü özelleştirme konusunda yer alan adımları kullanarak KREDI [kartı SIT'in bir kopyasını oluşturun](customize-a-built-in-sensitive-information-type.md).
1. Yeni desen ekleme
1. Birincil öğede, normal ifadeyi seçin
1. Normal ifadenin bir parçası olarak '/' içeren normal ifadeyi tanımlayın, ardından doğrulayıcıyı seçin ve regex'in LuhnCheck'i de geçtiğinden emin olmak için luhncheck veya func_credit_card'ı seçin.

## <a name="ignore-a-disclaimer-notice"></a>Bildirim bildirimini yoksayma

Birçok kuruluş e-posta iletilerinin altına, kuruluşlarını giren veya bırakırken, bazı durumlarda da kuruluşlar içinde bile yasal uyarı, açıklama bildirimi, imza veya başka bilgiler ekler. Çalışanların kendileri, motivasyona bağlı alıntılar, sosyal mesajlar gibi imzalar koymalarıdır. Bir uyarı veya imza, bir CC'nin tutarsızlık içinde bulunan terimleri içerebilir ve birçok yanlış pozitif sonuç üreteci olabilir.  

Örneğin, tipik bir uyarıda hassas veya gizli gibi sözcükler yer almaktadır ve hassas bilgileri arayan bir ilke bunu bir olay olarak algılar ve bu da birçok hatalı pozitif sonuç verir. Bu nedenle müşterilere uyarıyı yoksayma seçeneği sağlamak hatalı pozitif sonuç sayısını azaltabilir ve uyumluluk ekibinin verimliliğini artırır.

### <a name="example-of-disclaimer"></a>Uyarı örneği

Aşağıdaki tekzleci dikkate alın:

ÖNEMLİ TİPİ: Bu e-posta iletisinin yalnızca içerdiği gizli bilgileri alma hakkı olan kişilerce verilmesi amaçlanan bir iletidir. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Lütfen hedeflenen iletiyi alıcı olmadığınız sürece bu iletiyi okumayı, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayarınızdan tamamen silin.

SIT, gizli bir anahtar sözcüğü algılayan şekilde yapılandırılmışsa, bu düzen e-postada her uyarı kullanıldığında eşleşmeyi çağırır ve bu da birçok hatalı pozitif sonuç verir.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>SIT'te ön ek ve son ek kullanarak uyarıyı yoksayma

Yasal uyarıda anahtar sözcük örneklerini yoksaymanın bir yolu, ön ek ile önce gelen ve sonek ile devam eden anahtar sözcüklerin örneklerini dışlamamaktır.

Bu tekzleci dikkate alın:

ÖNEMLİ TİPİ: Bu e-posta iletisinin yalnızca içerdiği gizli bilgileri  alma hakkı olan **kişilerce verilmesi amaçlanan bir iletidir**. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Lütfen hedeflenen iletiyi alıcı olmadığınız sürece bu iletiyi okumayı, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayarınızdan tamamen silin.

"Gizli" anahtar sözcüğünün iki örneği vardır ve SIT'i bu anahtar sözcüğün ön eklerinden önce gelen (örnekte italik) örneklerini, ardından da sonekleri (örnekte kalın yazıyla gösterilir) yoksayacak şekilde yapılandırıyorsanız, çoğu durumda feragatlerin yoksaynarak başarabilirsiniz.

Ön ek ve son ek kullanarak tekzleci yoksaymak için:

1. Yasal uyarıda yoksaymak istediğiniz anahtar sözcüğün ön ek ve son ek metnini dışarıda tutmak için geçerli SIT'te ek denetimler ekleyin.
1. Öneki hariç tutmak için seçin ve **Önekler** metin kutusuna **, önek olarak bulunan bilgileri girin**.
1. Son eki ve Sonekler metin kutusuna girerek **yasal** olarak ayrıcalıklı **seçeneğine tıklayın**.
1. Aşağıdaki grafikte gösterildiği gibi, bu işlemi yasal uyarıda anahtar sözcüklerin diğer örnekleri için yinele.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>İkincil öğeler hariç bırakarak tekzciliği yoksayma

İkincil öğeleri hariç tutmak için destekleyen öğeler listesi (uyarıda bulunan örnekler) eklemenin bir diğer yolu da ikincil öğeleri hariç tutmaktır.

Bu tekzleci dikkate alın:

ÖNEMLİ TİPİ: Bu e-posta iletisinin yalnızca içerdiği gizli bilgileri alma hakkı olan kişilerce verilmesi amaçlanan bir iletidir. Contoso istemcilerine gönderilen e-posta iletileri gizli ve yasal olarak ayrıcalıklı bilgiler içerebilir. Lütfen hedeflenen iletiyi alıcı olmadığınız sürece bu iletiyi okumayı, kopyalamayı, iletmeyi veya depolamayın. Bu iletiyi hatayla aldıysanız, lütfen gönderene iletin ve bilgisayarınızdan tamamen silin.

Bu örnekte "gizli" anahtar sözcüğünün iki örneği vardır. SIT'i bu anahtar sözcüğün örneklerini yasal uyarıda (kırmızı olarak altı çizili) yoksayacak şekilde yapılandırırsanız, çoğu durumda yasal uyarıyı yoksaymamizi başarabilirsiniz.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Sorumluluk reddinde ek örnekleri dışarıda tutmak için bu modele daha fazla koşullar  eklersiniz.":::

İkincil öğeleri kullanarak tekzciliği yoksaymak için:

1. Desteklenen **öğelerde Bu gruplardan** herhangi biri değil'i seçin.
1. Bir anahtar sözcük listesi/sözlüğü olarak yoksaymak istediğiniz uyarı örneklerini ekleyin.
1. Anahtar sözcükleri yoksaymak istediğiniz yeni bir satır olarak ekleyin. Her metnin uzunluğunun 50 karakterden fazla olamaz.
1. Bu öğenin yakınlıklarını, birincil öğenin 50-60 karakteri arasında olacak şekilde ayarlayın.
