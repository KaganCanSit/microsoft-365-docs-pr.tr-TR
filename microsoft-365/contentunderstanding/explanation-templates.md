---
title: Microsoft SharePoint Syntex'de açıklama şablonlarını kullanma
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
description: Microsoft web sitesinde açıklama şablonlarını kullanma ve kaydetme hakkında daha fazla SharePoint Syntex.
ms.openlocfilehash: 87d151a3dc0863b880515abb6ee59d3691d9e4c6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985560"
---
# <a name="use-explanation-templates-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de açıklama şablonlarını kullanma

Açıklamanız için çeşitli tümcecik listesi değerlerini el ile ekleyeceniz, açıklama kitaplığında size sağlanan şablonları kullanmak daha kolay olabilir.

Örneğin, tarih çeşitlemelerinin hepsini el ile eklemek *yerine, tarih* olarak tümcecik listesi şablonunu kullanabilirsiniz çünkü  zaten birçok tümcecik listesi değeri içerir:

![Açıklama kitaplığı.](../media/content-understanding/explanation-template.png)

Açıklama kitaplığı, aşağıdakiler de dahil olmak *üzere sık kullanılan tümcecik* listesi açıklamalarını içerir:

- Tarih: Takvim tarihleri, tüm biçimler. Metin ve sayıları içerir (örneğin "9 Aralık 2020").
- Tarih (sayısal): Takvim tarihleri, tüm biçimler. Sayıları içerir (örneğin, 1-11-2020).
- Zaman: 12 saatlik ve 24 saatlik biçimler.
- Sayı: En çok iki ondalık basamağı olan pozitif ve negatif sayılardır.
- Yüzde: Yüzdeyi temsil eden desenlerin listesi. Örneğin, %1, %11, %100 veya %11,11.
- Telefon numarası: Yaygın ABD ve Uluslararası biçimler. Örneğin, 000 000 0000, 000-000-0000, (000)000-0000 veya (000) 000-0000.
- Posta kodu: ABD Posta kodu biçimleri. Örneğin, 11111, 11111-1111.
- Tümcenin ilk sözcüğü: En çok dokuz karakterden uzun sözcükler için genel desenler.
- Tümcenin sonu: Tümcenin sonu için yaygın olarak kullanılan noktalama işaretleri.
- Kredi kartı: Yaygın kredi kartı numarası biçimleri. Örneğin, 1111-1111-1111-1111.
- Sosyal güvenlik numarası: ABD Sosyal Güvenlik Numarası biçimi. Örneğin, 111-11-1111.
- Onay kutusu: Dolu bir onay kutusunun çeşitlemelerini temsil eden tümcecik listesi. Örneğin, _X_, _ _X_.
- Para Birimi: Büyük uluslararası simgeler. Örneğin, $.
- E-posta BILGI: Genellikle iletinin gönderildiği diğer kişilerin veya grupların adları veya e-posta adresleri yakınlarında bulunan ve 'BILGI:' terimini içeren bir tümcecik listesi.
- E-posta tarihi: 'Gönderme tarihi:' terimini içeren bir tümcecik listesi, çoğunlukla e-postanın gönderildiği tarihin yanında bulunur.
- E-posta karşılaması: E-postalar için yaygın kullanılan açılış çizgileri.
- E-posta alıcısı: Genellikle iletinin gönderildiği kişilerin veya grupların adları veya e-posta adresleri yakınlarında bulunan ve 'Hedef:' terimini içeren bir tümcecik listesi.
- E-posta gönderen: Çoğunlukla gönderenin adının veya e-posta adresinin yanında bulunan 'Gönderen:' terimini içeren tümcecik listesi.
- E-posta konusu: Çoğunlukla e-postanın konusunun yanında bulunan 'Konu:' terimini içeren bir tümcecik listesi.

Açıklama kitaplığı, aşağıdakiler gibi yaygın olarak *kullanılan normal ifade* açıklamalarını da içerir:

- 6 basamaklı - 17 basamaklı sayılar: 6 ile 17 basamak uzunluğunda herhangi bir sayıyla eşler. ABD banka hesap numaraları bu modele uyar.
- E-posta adresi: E-posta adresi gibi yaygın bir tür e-meganb@contoso.com.
- ABD vergi mükellefi numarası: 9 ile başlayan ve 7 veya 8 ile başlayan 6 basamaklı bir sayı ile eşleşen üç basamaklı bir sayı.
- Web adresi (URL): Web adresinin biçimiyle, Adres Defteri veya Http:// ile https://.

Buna ek olarak, açıklama kitaplığı örnek dosyalarınıza etiketle ilgili verilerle birlikte üç otomatik şablon türü içerir:

- Etiketden sonra: Örnek dosyalarda yer alan etiketlerden sonra gelen sözcükler veya karakterler.
- Etiketden önce: Örnek dosyalarda yer alan etiketlerden önce gelen sözcükler veya karakterler.
- Etiketler: Örnek dosyalardan ilk 10 etikete kadar.

Otomatik şablonların nasıl çalışmasına bir örnek vermek için, aşağıdaki örnek dosyada modele daha doğru bir eşleşme elde etmek üzere daha fazla bilgi vermeye yardımcı olmak için Etiket açıklamasıdan önce şablonunu kullanıla bir şablon kullanılamız.

![Örnek dosya.](../media/content-understanding/before-label.png)

Etiket açıklamasıdan önce şablonunu seçerek, örnek dosyalarınız içinde etiketden önce görünen ilk sözcük kümesi için arama görünür. Örnekte, ilk örnek dosyada tanımlanan sözcükler kümesi "Şu anda" sözcükleridir.

![Etiket şablonudan önce.](../media/content-understanding/before-label-explanation.png)

Şablondan bir **açıklama** oluşturmak için Ekle'yi seçin. Başka örnek dosyalar eklerken, tümcecik listesine başka sözcükler de tanımlanır ve eklenir.

![Etiketi ekleyin.](../media/content-understanding/before-label-add.png)

## <a name="use-a-template-from-the-explanation-library"></a>Açıklama kitaplığından şablon kullanma

1. Modelinizin **Tren** sayfasının Açıklamalar bölümünde Yeni'yi ve  **ardından Şablondan'ı** **seçin**.

   ![Etiket önünde ekle'yi seçin.](../media/content-understanding/from-template.png)

2.  Açıklama **şablonları sayfasında,** kullanmak istediğiniz açıklamayı seçin ve sonra da Ekle'yi **seçin**.

    ![Bir şablon seçin.](../media/content-understanding/phone-template.png)

3. Seçtiğiniz şablona ilişkin bilgiler Açıklama oluştur **sayfasında** görüntülenir. Gerekirse açıklama adını düzenleyin ve tümcecik listesinde öğe ekleyin veya kaldırın.

    ![Şablonu düzenle'yi seçin.](../media/content-understanding/phone-template-live.png)

4. Bitirdikten sonra Kaydet'i **seçin**.

## <a name="save-a-template-to-the-explanation-library"></a>Açıklama kitaplığına şablon kaydetme

Diğer modellerle kullanılacak içerik merkezinin açıklama kitaplığında kullanılabilir hale yapmak için, açıklamayı şablon olarak kaydedebilirsiniz. Şablonda, tümceciklerin belgede nerede olduğunu belirtin seçeneği dışında, açıklamanın temel ve gelişmiş ayarları yer almaktadır.

> [!NOTE]
> Yalnızca tümcecik listesi ve normal ifade açıklamaları şablon olarak kaydedilebilir.

1. Modelinizin **Tren** sayfasının Açıklamalar **bölümünde** :

   a. Açıklamalar listesinde şablon olarak kaydetmek istediğiniz açıklamayı seçin.

   b. Şablon **olarak kaydet'i seçin**.

    ![Şablon olarak kaydet seçeneğini gösteren Açıklamalar bölümünün ekran görüntüsü.](../media/content-understanding/explanation-save-as-template.png)

2. Açıklama **şablonunu kaydet sayfasında** :

   a. Ad bölümünde **,** gerekirse açıklamayı yeniden adlandırabilirsiniz.

   b. Açıklama **bölümünde** , başkalarının açıklamayı nasıl kullanabileceğini başkalarına haber vermeleri için bir açıklama ekleyin.

   c. **Kaydet**'i seçin.

    ![Açıklamayı kaydet şablon sayfasının ekran görüntüsü.](../media/content-understanding/save-explanation-template.png)

### <a name="see-also"></a>Ayrıca bkz.

[Açıklama türü SharePoint Syntex](explanation-types-overview.md)