---
title: Hassas bilgi türü REGEX geçerliliği ve ek denetimler
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
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
description: Hassas bilgi türlerinde REGEX doğrulamaları ve ek denetimleri kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 615d4757be16b3171005105aea8148536e6f3015
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015499"
---
# <a name="sensitive-information-type-regex-validators-and-additional-check"></a>Hassas bilgi türü REGEX geçerlileri ve ek denetim

> [!IMPORTANT]
> Microsoft Müşteri & Desteği, özel sınıflandırmalar veya normal ifade düzenleri oluşturmaya yardımcı olabilir. Destek mühendisleri, özellik için test amacıyla örnek normal ifade modelleri sağlama veya beklendiği gibi tetik getirmeyen mevcut normal ifade düzeninde sorun gidermeye yardımcı olmak gibi, ancak özel içerik eşleştirme geliştirmeleri için gereksinimlerinizi veya yükümlülüklerinizi karşılayacak güvenceler sağlanmaz.

## <a name="sensitive-information-type-regular-expression-validators"></a>Hassas Bilgi Türü normal ifade doğrulayıcıları

### <a name="checksum-validator"></a>Checksum geçerlileyicisi

Normal ifadede bir rakam üzerinde bir denetim numarası çalıştırmaniz gerekirse, denetimum *doğrulayıcıyı kullanabilirsiniz*. Örneğin, sekiz basamaklı bir lisans numarası için SIT oluşturmanız gerekmektedir. Burada son basamak, mod 9 hesaplaması kullanılarak doğrulanmış bir sağlama sayısı basamaktır. Denetimlerum algoritmasını şu şekilde ayarladk:

```console
Sum = digit 1 * Weight 1 + digit 2 * weight 2 + digit 3 * weight 3 + digit 4 * weight 4 + digit 5 * weight 5 + digit 6 * weight 6 + digit 7 * weight 7 + digit 8 * weight 8
Mod value = Sum % 9
If Mod value == digit 8
    Account number is valid
If Mod value != digit 8
    Account number is invalid
```

1. Birincil öğeyi şu normal ifadeyle tanımlayın:

   ```console
   \d{8}
   ```

2. Ardından, denetimli kimlik doğrulamayı ekleyin.

3. Ağırlık değerlerini virgüllerle ayırarak, onay basamaklarının konumunu ve Mod değerini ekleyin. Modül işlemi hakkında daha fazla bilgi için bkz. [Mod işlemi](https://en.wikipedia.org/wiki/Modulo_operation).

   > [!NOTE]
   > Onay rakamı, çek numarası hesaplamasına dahil değilken, onay rakamı için ağırlık olarak 0 kullanın. Örneğin, yukarıdaki ağırlık 8 ise, onay rakamlarını hesaplamak için çek rakamı kullanılmazsa 0'a eşit olur.

   :::image type="content" alt-text="yapılandırılmış denetimlerum doğrulayıcının ekran görüntüsü." source="../media/checksum-validator.png" lightbox="../media/checksum-validator.png":::

### <a name="date-validator"></a>Tarih doğrulayıcı

Normal ifadeye eklenmiş olan tarih değeri oluşturmakta olduğu yeni bir düzenin parçası ise, tarih doğrulayıcıyı kullanarak ölçütlerinize  uygun olduğunu sınayabilirsiniz. Örneğin, dokuz basamaklı bir çalışan kimlik numarası için bir SIT oluşturmak istediğinizi var diyelim. İlk altı rakam DDMMY biçimindeki işe alma tarihidir ve son üç rakam rastgele oluşturulur. İlk altı basama nın doğru biçimde olduğunu doğrulamak için.

1. Birincil öğeyi şu normal ifadeyle tanımlayın:

   ```console
   \d{9}
   ```

2. Ardından tarih doğrulayıcıyı ekleyin.

3. Tarih biçimini ve başlangıç uzaklığını seçin. Tarih dizesi ilk altı basamak olduğu için, uzaklık değeri : `0`.

   :::image type="content" alt-text="yapılandırılmış tarih doğrulayıcının ekran görüntüsü." source="../media/date-validator.png" lightbox="../media/date-validator.png":::

### <a name="functional-processors-as-validators"></a>Doğrulayıcı olarak işlevsel işlemciler

En sık kullanılan SITS'lerden bazıları için geçerlik olarak işlev işlemcileri kullanabilirsiniz. Bu, sit için gereken ek denetimleri geçmelerinden emin olarak kendi normal ifadenizi tanımlamanıza olanak sağlar. Örneğin, Func_India_Aadhar sizin tanımlandığı özel normal ifadenin Indian Aadhar kartı için gereken doğrulama mantığını geçtiğinden emin olur. Geçerli olarak kullanılan DLP işlevleri hakkında daha fazla bilgi için hassas bilgi [türü işlevleri bkz](sit-functions.md). 

### <a name="luhn-check-validator"></a>Luhn check validator

Luhn algoritmasının geçmesi gereken normal bir ifade içeren özel bir Hassas bilgi türünüz varsa [, Luhn denetimi doğrulayıcısını kullanabilirsiniz](https://en.wikipedia.org/wiki/Luhn_algorithm).

## <a name="sensitive-information-type-additional-checks"></a>Hassas bilgi türü ek denetimler

Burada, kullanılabilir ek denetim tanımları ve bazı örnekler verilmiştir.

**Belirli eşleşmeleri hariç tut**: Bu denetim, düzenlemekte olduğunuz desene göre eşleşmeleri algılarken hariç tutulacak anahtar sözcükleri tanımlamanız için olanak sağlar. Örneğin, geçerli bir numarayla eşleşmeleri için '4111111111111111' gibi test kredi kartı numaralarını hariç tutebilirsiniz.

**Başlar veya karakterlerle başlamaz**: Bu denetim, eşleşmesi gereken veya başlamamalıdır karakterleri tanımlamanız için size olanak sağlar. Örneğin, düzenin yalnızca 41, 42 veya 43 ile başlayan kredi kartı numaralarını algılamak istiyorsanız, Başlar'ı seçin ve virgülle ayırarak listeye 41, 42 ve 43 ekleyin. 

**Sona erer veya karakterlerin sonunda olmaz**: Bu denetim, eşleşmesi gereken veya bitmeyecek karakterleri tanımlamanız için size olanak sağlar. Örneğin, Çalışan Kimliği numaranız 0 veya 1 **ile** bitene bilmiyorsa, Sonu ile bitsin öğesini seçin ve virgülle ayırarak listeye 0 ve 1 ekleyin.

**Yinelenen karakterleri dışla**: Bu denetim, tüm basamakların aynı olduğu eşleşmeleri yoksaymanizi sağlar. Örneğin, altı basamaklı çalışan kimlik numarasının tüm basamakları aynı olamazsa, çalışan kimliği için geçerli eşleşmeler listesinden 111111, 222222, 333333, 444444, 555555, 666666, 777777, 888888, 999999 ve 000000 karakterlerini hariç tutmak için Yinelenen karakterleri dışla seçeneğini seçebilirsiniz.

**Ön ekleri dahil edin veya** dışla: Bu denetim, eşleşen varlığa hemen var olan veya bulunmayacak anahtar sözcükleri tanımlamanız için olanak sağlar. Seçiminize bağlı olarak, varlıklar buraya ekli ön eklerin başında yer alan adlarla eş olur veya eşleşmez. Örneğin, GUID ön **eklerini** dışla **:** öneki: önünde **GUID** olan herhangi bir varlık eşleşme olarak kabul edilir.

**Sonekleri dahil etmek veya hariç tutmak** Bu denetim, eşleşen varktan hemen sonra bulunmalıdır veya bulunmalıdır gereken anahtar sözcükleri tanımlamanız için olanak sağlar. Seçiminize bağlı olarak, varlıklar burada yer alan soneklerin ardından gelecekse eşlerileri ya da eşleşmezler. Örneğin, :GUID soneki **dışla'yı** dışlarsanız, **:GUID** ile birlikte gelen metinler eşleşmez.
