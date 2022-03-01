---
title: Hassas bilgi türü varlık tanımları
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: DLP ilkeleriniz içinde kullanımınıza hazır birçok hassas bilgi türü vardır. Bu makalede, tüm bu hassas bilgi türleri listelanmıştır ve her tür algılana kadar bir DLP ilkesi ne için arama yaptığını gösterir.
ms.openlocfilehash: a3d2592af6b7692b5a5e634947deb811412b5650
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015525"
---
# <a name="sensitive-information-type-entity-definitions"></a>Hassas bilgi türü varlık tanımları

Bu makalede tüm hassas bilgi türü varlık tanımları listelanmıştır. Her tanım, her türü algılamak için bir DLP ilkesi için nelerin göründüğünü gösterir. Hassas bilgi türleri hakkında daha fazla bilgi edinmek için bkz. [Hassas bilgi türleri](sensitive-information-type-learn-about.md)

> [!NOTE]
> Güven düzeyi eşlemesi (yüksek/orta/düşük) ve doğruluk sayısı (1 ile 100 arasında sayısal değer)
> - Düşük güven: 65 veya daha düşük
> - Orta güven: 75
> - Yüksek güven: 85


## <a name="aba-routing-number"></a>ABA yönlendirme numarası

### <a name="format"></a>Biçim

Biçimlendirilmiş veya biçimlendirilmemiş bir desende dokuz basamak

### <a name="pattern"></a>Desen

- 00-12, 21-32, 61-72 veya 80 aralıklarında iki basamak
- İki basamak
- isteğe bağlı kısa çizgi
- dört basamak
- isteğe bağlı kısa çizgi
- basamak


### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

İlkenin, 300 karakter yakınlık içinde bu tür hassas bilgiler algılandığında orta düzeyde güveni vardır:
- İşlev Func_aba_routing desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_ABA_Routing bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_aba_routing desene eşleşen içeriği bulur.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- aba numarası
- aba #
- aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- banka yönlendirme #
- banka yönlendirmesayısı
- yönlendirme #
- yönlendirme no
- yönlendirme numarası
- yönlendirme toplu taşıma numarası
- yönlendirme #
- RTN


## <a name="all-full-names"></a>Tüm tam adlar

Tüm tam adlar, paketli bir varlıktır. Avustralya, Çin, Japonya, ABD ve AB'deki ülkelerde bulunan desteklenen tüm ülkelerden/bölgelerden kişilerin tam adlarını algılar. Tam adların tüm olası eşleşmelerini algılamak için bu SIT'i kullanın.

### <a name="format"></a>Biçim

Çeşitli.

### <a name="pattern"></a>Desen

Çeşitli.

### <a name="checksum"></a>Checksum

Hayır.

### <a name="description"></a>Açıklama

Bu adlı varlık SIT, bir insan tarafından büyük güvenle ad olarak tanımlanacak kişisel adlarla eştir. Örneğin, verilen bir addan oluşan bir dize bulunursa ve bunu bir aile adı takip ediyorsa, büyük güvenle bir eşleşme yapılır. Üç birincil kaynak kullanır:

-   Verilen adların sözlüğü.
-   Aile adlarını içeren bir sözlük.
-   Adların nasıl oluştuğuna desenler.

Bu üç kaynak, her ülke için farklıdır.  Zaman *Zaman dizeleri Eşleşmeyi* tetikler. Yaygın olarak verilen/aile adlara, nadir kullanılan adlardan daha yüksek güven verilir. Öte yandan, desen kısmi eşleşmelere de izin verir. Sözlükte verilen bir ad bulunursa ve onu sözlükte yer alan aile adı takip ediyorsa, kısmi bir eşleşme tetiklenir. Örneğin, *Tomas Richard* kısmi eşleşmeyi tetikler. Kısmi eşleşmelere daha düşük güven verilir.

Buna ek olarak, insanların adları belirten olarak göreceği desenler de uygun bir güvenle eş olur. Like *O. Gerçekten*, *O.P. Her*, *Dr. O. P. S. 10000000* .  veya *T. Richard, Jr.* eşleşmeleri olabilir.

### <a name="supported-languages"></a>Desteklenen diller

- English
- Bulgarian
- Çince
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- İzlanda dili
- İrlanda dili
- Italian
- Japanese
- Latvian
- Lithuanian
- Malta dili
- Dutch
- Norveç dili
- Polish
- Portekizce
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="all-medical-terms-and-conditions"></a>Tüm tıbbi hüküm ve koşullar

Tüm tıbbi hüküm ve koşullar, tıbbi hüküm ve sağlık koşullarını algılayan, paketli bir adlandırılmış kurumdur. Yalnızca İngilizce terimleri algılar. Sağlık hüküm ve koşullarının tüm olası eşleşmelerini algılamak için bu SIT'i kullanın.

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Sözlük

### <a name="checksum"></a>Checksum

Hayır

### <a name="description"></a>Açıklama

Bu paketli varlık, özel sözlüklerde mevcut olan tıbbi koşulların sözlüğünü içeren metinle eştir. Desteklenen her dil için bir özel sözlük vardır. Bu sözlükler birçok uluslararası tıbbi kaynaktandır. Çok fazla sayıda hatalı pozitif sonuç riski olmadan, sözlükler mümkün olduğunca fazla sağlık durumu içerir. Her girdi, kapsam sağlamak için yaygın olarak tek bir koşula göre yazılmış farklı formları içerir; örneğin:

- *TB*
- *boruktüroz*
- *phthisis pulmonalis*

### <a name="contains"></a>Içerir

Bu paketli varlık SIT bu tek tek SIT'leri içerir.

- Kan testi koşulları 
- Ilaç türleri
- 10000 Yıl Sonra
- Genel ilaç adları
- ABD Engellilik Değerlendirmesinde Sosyal Güvenlik kapsamında listelenen engellilik bozuklukları
- Laboratuvar test koşulları
- Tıbbi koşullarla ilgili yaşam tarzları
- Tıbbi uzmanlıklar
- Yordamlar
- Ilaç adları


## <a name="all-physical-addresses"></a>Tüm Fiziksel Adresler

Tüm fiziksel adresler, desteklenen tüm ülkelerin/bölgelerin fiziksel adresleriyle ilgili desenleri algılayan, paketli bir VARLıK SIT'tir.

### <a name="format"></a>Biçim

Çeşitli

### <a name="pattern"></a>Desen

Çeşitli

### <a name="checksum"></a>Checksum

Hayır

### <a name="description"></a>Açıklama

Sokak adreslerinin eşleşmesi, bir insan tarafından posta adresi olarak tanımlanacak dizeleri eşleştirecek şekilde tasarlanmıştır. Bunu yapmak için birkaç birincil kaynak kullanır:

-   Düzenleme, ilçe ve bölgelerin bir sözlüğü.
-   Yol, Sokak veya Cadde gibi sokak soneklerinin bir sözlüğü.
-   Posta kodu desenleri.
-   Adres biçimlerinin desenleri.

Kaynaklar her ülke için farklıdır. Birincil kaynaklar, verilen ülkede kullanılan adres biçimlerinin desenleridir. Mümkün olan en fazla adresin eş olduğundan emin olmak için farklı biçimler seçilir. Bu biçimler esneklik sağlar; örneğin, adres posta kodunu atlar veya şehir adını atlar ya da sokak son eki yoktur. Her durumda, bu tür eşleşmeler eşleşmenin güvenlerini artırmak için kullanılır.

Desenler genel konumlarla değil tek tek adreslerin eşleşmesi için tasarlanmıştır. Dolayısıyla *Redmond, WA 98052* veya *Main Street, Albuquerque* gibi dizeler eşleşmez.

### <a name="contains"></a>Içerir

Bu paketli varlık SIT'i şu bireysel SI'ları içerir:

- Avustralya fiziksel adresleri
- Avusturya fiziksel adresleri
- Belçika fiziksel adresleri
- Brezilya fiziksel adresleri
- Bulgaristan fiziksel adresleri
- Kanada fiziksel adresleri
- Hırvatistan fiziksel adresleri
- Kıbrıs fiziksel adresleri
- Çek Cumhuriyeti fiziksel adresleri
- Danimarka fiziksel adresleri
- Estonya fiziksel adresleri
- Finlandiya fiziksel adresleri
- Fransa fiziksel adresleri
- Almanya fiziksel adresleri
- Yunanistan fiziksel adresleri
- Macaristan fiziksel adresleri
- İzlanda fiziksel adresleri
- İrlanda fiziksel adresleri
- İtalya fiziksel adresleri
- Letonya fiziksel adresleri
- Liechtenstein fiziksel adresleri
- Litvanya fiziksel adresleri
- Lüksemburg fiziksel adresleri
- Malta fiziksel adresleri
- Hollanda fiziksel adresleri
- Yeni Zelanda fiziksel adresleri
- Norveç fiziksel adresleri
- Polonya fiziksel adresleri
- Portekiz fiziksel adresleri
- Romanya fiziksel adresleri
- Slovakya fiziksel adresleri
- Slovenya fiziksel adresleri
- İspanya fiziksel adresleri
- İsveç fiziksel adresleri
- İsviçre fiziksel adresleri
- Türkiye fiziksel adresleri
- Birleşik Krallık fiziksel adresleri
- Amerika Birleşik Devletleri'nde fiziksel adresler

### <a name="supported-languages"></a>Desteklenen diller

- English
- Bulgarian
- Çince
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- İzlanda dili
- İrlanda dili
- Italian
- Japanese
- Latvian
- Lithuanian
- Malta dili
- Dutch
- Norveç dili
- Polish
- Portekizce
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="argentina-national-identity-dni-number"></a>Arjantin ulusal kimliği (DNI) numarası

### <a name="format"></a>Biçim

Noktalı veya noktasız sekiz basamak

### <a name="pattern"></a>Desen

Sekiz basamak:
- İki basamak
- isteğe bağlı bir nokta
- üç basamak
- isteğe bağlı bir nokta
- üç basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_argentina_national_id desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_argentina_national_id bulunur.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Arjantin Ulusal Kimliği numarası
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp


## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Argentina Unique Tax Identification Key (CUIT/CUIL)

### <a name="format"></a>Biçim

Çizgili 11 basamak

### <a name="pattern"></a>Desen

Çizgili 11 basamak:
- 20, 23, 24, 27, 30, 33 veya 34'te iki basamak
- kısa çizgi (-)
- sekiz basamak
- kısa çizgi (-)
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_Argentina_Unique_Tax_Key` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_Argentina_Unique_Tax_Key` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_Argentina_Unique_Tax_Key` desene eşleşen içeriği bulur.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Alkışve Unica de Identificacion Tributaria
- CUIT
- benzersiz kimlik kodu 
- Cupve Única de Identificación Tributaria
- benzersiz kimlik kodu
- CUIL
- Benzersiz Vergi Kimliği Anahtarı
- Benzersiz Kimlik Kimliği Anahtarı
- Kimliğinin Benzersiz Anahtarı
- Benzersiz İş Kimlik Kodu
- İş Kimliğinin Benzersiz Kodu
- Benzersiz İş Tanımlama Anahtarı
- İş Kimliğinin Benzersiz Anahtarı
- Benzersiz Vergi Kodu Kodu
- Benzersiz Vergi Numarası Anahtarı
- Benzersiz İş Gücü Kimlik Kodu
- İş Gücü Kimliğinin Benzersiz Kodu
- Benzersiz İş Gücü Kimlik Anahtarı
- İş Gücü Kimliğinin Benzersiz Anahtarı
- vergi no
- taxID #
- taxId
- aracısayı
- vergi numarası
- vergi yok
- vergi #
- vergi #
- vergi mükellefi kimliği
- vergi mükellefi numarası
- vergi mükellefi yok
- vergi mükellefi #
- vergi mükellefi #
- vergi kimliği
- vergi kimliği
- Número de Identificación Mali
- número de contribuyente


## <a name="australia-bank-account-number"></a>Avustralya banka hesap numarası

### <a name="format"></a>Biçim

Banka şube numarası olan veya olmayan altı ile 10 basamak arasında

### <a name="pattern"></a>Desen

Hesap numarası 6 ile 10 basamak arasındadır.

Avustralya banka şube numarası:
- üç basamak
- kısa çizgi
- üç basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_australia_bank_account_number desene eşleşen içeriği bulur.
- Bir arama Keyword_australia_bank_account_number anahtar sözcüğü bulunur.
- Normal ifade Regex_australia_bank_account_number_bsb desene eşleşen içeriği bulur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_australia_bank_account_number desene eşleşen içeriği bulur.

- Bir arama Keyword_australia_bank_account_number anahtar sözcüğü bulunur.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift banka kodu
- karşılık gelen banka
- temel para birimi
- abd hesabı
- tutucu adresi
- banka adresi
- bilgi hesabı
- fon aktarımları
- banka ücretleri
- banka ayrıntıları
- bankacılık bilgileri
- tam adlar
- iaea


## <a name="australia-business-number"></a>Avustralya iş numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcılar ile 11 basamak

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcılar ile 11 basamak:

- İki basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_australian_business_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keywords_australian_business_number bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_australian_business_number desene eşleşen içeriği bulur.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- avustralya iş no
- iş numarası
- abn #
- businessid #
- iş kimliği
- abn
- businessno #


## <a name="australia-company-number"></a>Avustralya şirket numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Sınırlayıcıları olan dokuz basamak

### <a name="pattern"></a>Desen

Sınırlayıcılarla dokuz basamak:

- üç basamak
- boşluk
- üç basamak
- boşluk
- üç basamak


### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_Australian_Company_Number desene eşleşen içeriği bulur.
- Bir Keyword_Australian_Company_Number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_Australian_Company_Number desene eşleşen içeriği bulur.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- acn
- avustralya şirket no
- avustralya şirket no #
- Avustralya şirket numarası
- Avustralyalı şirket hayır
- Avustralyalı şirket hayır #
- Avustralyalı şirket numarası


## <a name="australia-drivers-license-number"></a>Avustralya sürücüsünün lisans numarası

### <a name="format"></a>Biçim

dokuz harf ve rakam

### <a name="pattern"></a>Desen

dokuz harf ve rakam:

- İki basamak veya harf (büyük/küçük harfe duyarlı değildir)
- İki basamak
- beş rakam veya harf (büyük/küçük harfe duyarlı değildir)

VEYA

- bir - iki isteğe bağlı harf (büyük/küçük harfe duyarlı değildir)
- dört ile dokuz basamak arasında

VEYA

- dokuz rakam veya harf (büyük/küçük harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_australia_drivers_license_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_australia_drivers_license_number bulunur.
- Anahtar sözcük Keyword_australia_drivers_license_number_exclusions anahtar sözcük bulunamıyor.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- uluslararası sürüş izinleri
- Avustralya otomobil birliği
- uluslararası sürüş izni
- DriverLicence
- DriverLicences
- Sürücü Lic
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLic
- DriversLicence
- DriversLicences
- Sürücüler Lic
- SürücülerLics
- Sürücüler Lisansı
- Sürücüler Lisansları
- Driver'Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü' Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'sLic
- Sürücü Lisansları
- Sürücü Lisansları
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- Sürücü Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Sürücüler Lic #
- SürücülerLics #
- Sürücüler Lisansı #
- Sürücüler Lisansları #
- Driver'Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü' Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'sLic #
- Sürücü Lisansları #
- Sürücü Lisansları #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- DriverLicense
- DriverLicenses
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLicense
- DriversLicenses
- Sürücüler Lisansı
- Sürücüler Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- DriverLicense #
- DriverLicenses #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLicense #
- DriversLicenses #
- Sürücüler Lisansı #
- Sürücüler Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #


## <a name="australia-medical-account-number"></a>Avustralya tıbbi hesap numarası

### <a name="format"></a>Biçim

10-11 basamak

### <a name="pattern"></a>Desen

10-11 basamak:
- İlk basamak 2-6 aralığındadır
- Dokuzuncu basamak bir onay rakamıdır
- Onuncu basamak, sorun rakamıdır
- 11. basamak (isteğe bağlı) tek sayıdır

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_australian_medical_account_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_Australia_Medical_Account_Number bulunur.
- Denetimli denetimler geçer.


```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- banka hesabı ayrıntıları
- sağlıkla ilgili ödemeler
- konut kredisi hesabı
- banka ödemeleri
- bilgi dalı
- kredi kartı kredisi
- Department of human services
- yerel hizmet
- sıhhi


## <a name="australia-passport-number"></a>Avustralya pasaport numarası

### <a name="format"></a>Biçim

sekiz veya dokuz alfasayısal karakter

### <a name="pattern"></a>Desen

- bir harf (N, E, D, F, A, C, U, X) ve ardından yedi basamak veya
- İki harf (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) ve ardından yedi basamak.

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_australia_passport_number` eşleşen içerik bulur.
- Anahtar sözcük `Keyword_australia_passport_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade desene `Regex_australia_passport_number` eşleşen içerik bulur.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları
- pasaport ayrıntıları
- neden ve teslimi
- Avustralya commonwealth
- departman
- ulusal kimlik kartı
- seyahat belgesi
- yetkili verme


## <a name="australia-physical-addresses"></a>Avustralya fiziksel adresleri 

İşle ilgili olmayan bir adlandırılmış varlık, Avustralya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi
orta


## <a name="australia-tax-file-number"></a>Avustralya vergi dosyası numarası

### <a name="format"></a>Biçim

sekiz ile dokuz basamak arasında

### <a name="pattern"></a>Desen

Tipik olarak boşluklarla sunulan sekiz ile dokuz basamak arasında:
- üç basamak
- isteğe bağlı bir boşluk
- üç basamak
- isteğe bağlı bir boşluk
- Son rakamın onay rakamı olduğu iki ile üç basamak arasında

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_australian_tax_file_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_Australia_Tax_File_Number Keyword_number_exclusions anahtar sözcük bulunamıyor.
- Denetimli denetimler geçer.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- Avustralya iş numarası
- kâr marjı vergi oranı
- sıhhare lezy
- portföy numarası
- hizmet eskileri
- stoping tax
- bireysel vergi iadesini
- vergi dosyası numarası
- tfn


## <a name="austria-drivers-license-number"></a>Avusturya sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_austria_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_austria_eu_driver's_license_number` bulunur.

```xml
      <!-- Austria Driver's License Number -->
      <Entity id="682f18ce-44eb-482b-8198-2bcb96a0761e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_austria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver's_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern


## <a name="austria-identity-card"></a>Avusturya kimlik kartı

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Harflerin, basamakların ve özel karakterlerin 24 karakterlik birleşimi

### <a name="pattern"></a>Desen

24 karakter:

-  22 harf (büyük/küçük harfe duyarlı değil), basamaklar, eğik çizgi, eğik çizgi veya artı işaretleri

- İki harf (büyük/küçük harfe duyarlı değil), basamaklar, eğik çizgi, eğik çizgi, artı işaretleri veya eşittir işaretleri

### <a name="checksum"></a>Checksum

Uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_austria_eu_national_id_card` eşleşen içerik bulur.
- Anahtar sözcük  `Keywords_austria_eu_national_id_card` bulunur.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- kimlik numarası
- ulusal kimlik
- personalausweis republik österreich


## <a name="austria-passport-number"></a>Avusturya pasaport numarası

### <a name="format"></a>Biçim

Bir harf ve ardından isteğe bağlı bir boşluk ve yedi basamak

### <a name="pattern"></a>Desen

Bir harf, yedi basamak ve bir boşluk birleşimi:

- tek harf (büyük/harfe duyarlı değildir)
- bir boşluk (isteğe bağlı)
- yedi basamak

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_austria_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_austria_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_austria_eu_passport_number` bulunur.

```xml
      <!-- Austria Passport Number -->
      <Entity id="1c96ae4e-303b-447d-86c7-77113ac266bf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="austria-physical-addresses"></a>Avusturya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Avusturya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="austria-social-security-number"></a>Avusturya sosyal güvenlik numarası

### <a name="format"></a>Biçim

Belirtilen biçimde 10 basamak

### <a name="pattern"></a>Desen

10 basamak:

- Seri numarasına karşılık gelen üç basamak
- tek bir onay rakamı
- Doğum tarihine karşılık gelen altı basamak (DDMMY)

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_austria_eu_ssn_or_equivalent` desene eşleşen içeriği bulur.
- anahtar sözcüğü  `Keywords_austria_eu_ssn_or_equivalent` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_austria_eu_ssn_or_equivalent` desene eşleşen içeriği bulur.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- Avusturya ssn
- ehic sayı
- ehic no
- sigorta kodu
- sigortakodu #
- sigorta numarası
- sigorta no
- krankenkassennummer
- krankenversicherung
- socialsecurityno
- socialsecurityno #
- sosyal güvenlik yok
- sosyal güvenlik numarası
- sosyal güvenlik kodu
- sozialversicherungsnummer
- sozialversicherungsnummer #
- so bire bir sicherheit kein
- solislesicherheitkein #
- ssn #
- ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje


## <a name="austria-tax-identification-number"></a>Avusturya vergi kimlik numarası

### <a name="format"></a>Biçim

isteğe bağlı kısa çizgi ve eğik çizgiyle dokuz basamak

### <a name="pattern"></a>Desen

İsteğe bağlı kısa çizgi ve eğik çizgiyle dokuz basamak:

- İki basamak
- kısa çizgi (isteğe bağlı)
- üç basamak
- eğik çizgi (isteğe bağlı)
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_austria_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_austria_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev,  `Func_austria_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Austria Tax Identification Number -->
      <Entity id="4fd58d22-af28-4451-b18a-6f722430a56d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
          <Match idRef="Keywords_austria_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- steuernummer
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- vergi numarası


## <a name="austria-value-added-tax"></a>Avusturya katma değeri vergileri

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

11 karakterli alfasayısal desen:

- A veya a
- T veya t
- İsteğe bağlı boşluk
- U veya u
- isteğe bağlı boşluk
- iki veya üç basamak
- isteğe bağlı boşluk
- dört basamak
- isteğe bağlı boşluk
- bir veya iki basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_Austria_Value_Added_Tax desene eşleşen içeriği bulur.
- Farklı bir Keyword_Austria_Value_Added_Tax anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_Austria_Value_Added_Tax desene eşleşen içeriği bulur.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- kdv numarası
- kdv #
- AVUSTURYA KDV numarası
- kdv no.
- vatno #
- katma değer vergi numarası
- AVUSTURYA KDV
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- kdv kimlik numarası
- atu numarası
- kullanıcı arabirimi numarası


## <a name="azure-documentdb-auth-key"></a>Azure DocumentDB kimlik doğrulaması anahtarı

### <a name="format"></a>Biçim

"DocumentDb" dizesini, ardından aşağıdaki desende belirtilen karakterleri ve dizeleri içerir.

### <a name="pattern"></a>Desen

- "DocumentDb" dizesi
- 3-200 arasında küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar herhangi bir bileşimi
- Büyüktür simgesi (>), eşittir işareti (=), tırnak işareti (") veya kesme işareti (')
- 86 küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) birleşimi
- İki eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureDocumentDBAuthKey desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Azure IAAS veritabanı bağlantı dizesi ve Azure SQL bağlantı dizesi

### <a name="format"></a>Biçim

"Sunucu", "sunucu" veya "veri kaynağı" dizesi ve ardından "cloudapp.azure" dizesiyle birlikte aşağıdaki düzende belirtilen karakterler ve dizeler gelir.<!--no-hyperlink-->com" veya "cloudapp.azure.<!--no-hyperlink-->net" veya "database.windows.<!--no-hyperlink-->net" ve "Password" ya da "password" ya da "pwd" dizelerini kullanın.

### <a name="pattern"></a>Desen

- "Sunucu", "sunucu" veya "veri kaynağı" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" veya "database.windows.<!--no-hyperlink-->net"
- 1-300 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "Parola", "parola" veya "pwd" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- noktalı virgül (noktalı virgül, tırnak işareti (") ;) veya kesme işareti (') olmayan bir veya birden çok karakter
- noktalı virgül (;), tırnak işareti (") veya kesme işareti (')

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureConnectionString desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iot-connection-string"></a>Azure IoT bağlantı dizesi

### <a name="format"></a>Biçim

"Ana BilgisayarAdı" dizesi, ardından "azure-devices" dizelerini de içeren, aşağıdaki düzende ana hatları verilen karakter ve dizeleri içerir.<!--no-hyperlink-->net" ve "SharedAccessKey".

### <a name="pattern"></a>Desen

- "Ana BilgisayarAdı" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "azure-devices.<!--no-hyperlink-->net"
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "SharedAccessKey" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- herhangi bir 43 küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+)
- eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureIoTConnectionString desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Bu hassas bilgi türü, bu anahtar sözcükleri bir anahtar sözcük listesi değil, normal bir ifade kullanarak tanımlar.

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-publish-setting-password"></a>Azure yayımlama ayarı parolası

### <a name="format"></a>Biçim

"userpwd=" dizesi ve ardından bir alfasayısal dize.

### <a name="pattern"></a>Desen

- "userpwd=" dizesi
- 60 küçük harf veya rakam birleşimi
- tırnak işareti (")

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzurePublishSettingPasswords desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.


```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Bu hassas bilgi türü, bu anahtar sözcükleri bir anahtar sözcük listesi değil, normal bir ifade kullanarak tanımlar.

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-redis-cache-connection-string"></a>Azure Önbelleği yeniden dağıt bağlantı dizesi

### <a name="format"></a>Biçim

"redis.cache.windows.<!--no-hyperlink-->net" ifadesini, ardından da "password" veya "pwd" dizesini içeren aşağıdaki düzende belirtilen karakterleri ve dizeleri takip edin.

### <a name="pattern"></a>Desen

- "redis.cache.windows.<!--no-hyperlink-->net"
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "password" veya "pwd" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- Küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 43 karakterin herhangi bir bileşimi
- eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureRedisCacheConnectionString desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Biçim

"sig" dizesi, ardından aşağıdaki desende belirtilen karakter ve dizeleri içerir.

### <a name="pattern"></a>Desen

- "sig" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- küçük ya da büyük harf, rakam veya yüzde işareti (%) olan 43-53 karakter arasında herhangi bir birleşim
- "%3d" dizesi
- Küçük veya büyük harf, rakam veya yüzde işareti (%) olmayan herhangi bir karakter

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureSAS desene eşleşen içeriği bulur.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Azure hizmet verisi bağlantı dizesi

### <a name="format"></a>Biçim

"EndPoint" dizesi, ardından "servicebus.windows" dizelerini de içeren, aşağıdaki düzende ana hatları verilen karakter ve dizeleri içerir.<!--no-hyperlink-->net" ve "SharedAccesKey".

### <a name="pattern"></a>Desen

- "EndPoint" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "servicebus.windows.<!--no-hyperlink-->net"
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "SharedAccessKey" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- Küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 43 karakterin herhangi bir bileşimi
- eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureServiceBusConnectionString desene eşleşen içeriği bulur.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key"></a>Azure depolama hesap anahtarı

### <a name="format"></a>Biçim

"DefaultEndpointsProtocol" dizesi ve ardından aşağıdaki düzende ana hatları verilen karakter ve dizeler ("AccountKey" dizesini içerir).

### <a name="pattern"></a>Desen

- "DefaultEndpointsProtocol" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "AccountKey" dizesi
- sıfır ile iki boşluk karakteri arasında
- eşittir işareti (=)
- sıfır ile iki boşluk karakteri arasında
- Küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 86 karakterin herhangi bir bileşimi
- iki eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureStorageAccountKey desene eşleşen içeriği bulur.
- Normal CEP_AzureEmulatorStorageAccountFilter ifade, desene eşleşen içeriği bulamıyor.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri bir anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key-generic"></a>Azure Depolama hesabı anahtarı (generic)

### <a name="format"></a>Biçim

Aşağıdaki modelde belirtilen 86 küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+), bunların ardından gelen veya bunların ardından gelen herhangi bir karakter.

### <a name="pattern"></a>Desen

- sıfır simgesinden (>), kesme işareti ('), eşittir işareti (=), tırnak işareti (") veya sayı işaretinden (#)
- Küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 86 karakterin herhangi bir bileşimi
- iki eşittir işareti (=)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_AzureStorageAccountKeyGeneric desene eşleşen içeriği bulur.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```


## <a name="belgium-drivers-license-number"></a>Belçika sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_belgium_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya `Keywords_eu_driver's_license_number` `Keywords_belgium_eu_driver's_license_number` bulunur.

```xml
      <!-- Belgium Driver's License Number -->
      <Entity id="d89fd329-9324-433c-b687-2c37bd5166f3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_belgium_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver's_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>Belçika ulusal numarası

### <a name="format"></a>Biçim

11 basamak artı isteğe bağlı sınırlayıcılar

### <a name="pattern"></a>Desen

11 rakam artı sınırlayıcılar:
- YY biçiminde altı basamaklı ve isteğe bağlı iki dönem. Doğum tarihi için AA.DD
- Nokta, çizgi, boşluktan isteğe bağlı bir sınırlayıcı
- Üç sıralı basamak (erkekler için tek, kadınlar için bile)
- Nokta, çizgi, boşluktan isteğe bağlı bir sınırlayıcı
- iki onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_belgium_national_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_belgium_national_number bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_belgium_national_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- olarak aantal
- bnn #
- bnn
- carte d'identité
- identifiant national
- identifiantnational #
- identificatie
- tanımlama
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- kimlik
- 1912
- ulusal numara
- national register
- ulusalsayı #
- ulusalsayı
- nif #
- nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- kişisel kimlik numarası
- personalausweis
- kişiselsayı #
- registratie
- kayıt
- registrationsnumme
- registrierung
- sosyal güvenlik numarası
- ssn #
- ssn
- steuernummer
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="belgium-passport-number"></a>Belçika pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı yok, iki harf ve ardından da altı basamak

### <a name="pattern"></a>Desen

İki harf ve ardından altı basamak

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

 DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_belgium_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date2` tarihi DD MM YY biçiminde veya bir anahtar sözcük veya `Keywords_eu_passport_date` `Keywords_belgium_eu_passport_number` bulunur biçimde bulur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_belgium_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_belgium_eu_passport_number` bulunur.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Passeport carte
- Passeportportre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="belgium-physical-addresses"></a>Belçika fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Belçika'dan gelen fiziksel adreslerle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="belgium-value-added-tax-number"></a>Belçika değeri eklenen vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

12 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

12 karakterli alfasayısal desen:

- a letter B or b
- E harfi veya e harfi
- basamak 0
- 1 ile 9 arasında bir basamak
- isteğe bağlı bir nokta veya Kısa çizgi veya boşluk
- dört basamak
- isteğe bağlı bir nokta veya Kısa çizgi veya boşluk
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_belgium_value_added_tax_number desene eşleşen içeriği bulur.
- Bir başka Keywords_belgium_value_added_tax_number anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_belgium_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- kdv numarası
- kdv yok
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw #
- kdv #


## <a name="blood-test-terms"></a>Kan testi koşulları

Bu bakıla sahip olmayan bu varlık, *hCG* gibi kan testleri ile ilgili terimleri algılar. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek

## <a name="brand-medication-names"></a>Ilaç adları

Bu bakıla adlandırılmış varlık, *Tylenol* gibi marka ilaçlarının adlarını algılar. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="brazil-cpf-number"></a>Brezilya CPF numarası

### <a name="format"></a>Biçim

Onay basamakları içeren ve biçimlendirilemeyen 11 basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:
- üç basamak
- dönem
- üç basamak
- dönem
- üç basamak
- kısa çizgi
- basamamlı iki basamak

Biçimlendirilmemiş:
- Son iki basamamanın çek basamakları olduğu 11 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_brazil_cpf desene eşleşen içeriği bulur.
- Bir başka Keyword_brazil_cpf anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_brazil_cpf desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Kimlik
- Kayıt
- Gelir
- Cadastro de Pesoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita


## <a name="brazil-legal-entity-number-cnpj"></a>Brezilya yasal varlık numarası (CNPJ)

### <a name="format"></a>Biçim

Kayıt numarası, dal numarası ve çek basamakları ile sınırlayıcıları içeren 14 basamak

### <a name="pattern"></a>Desen

14 rakam, artı olarak sınırlayıcılar:

- İki basamak
- dönem
- üç basamak
- dönem
- üç basamak (ilk sekiz basamak kayıt numarasıdır)
- eğik çizgi
- dört basamaklı dal numarası
- kısa çizgi
- basamamlı iki basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_brazil_cnpj desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_brazil_cnpj bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_brazil_cnpj desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- Ulusal Yasal Varlıklar Kayıt Defteri
- Taxpayers Kayıt Defteri
- Tüzel kişi
- Yasal varlıklar
- Kayıt Durumu
- Business
- Şirket
- CNPJ
- Cadastro Nacional da Pezsoa Luciaídica
- Cadastro Geral de Contribuintes
- CGC
- Pezsoa pesídica
- Pezsoas pesídicas
- Situação cadastral
- Inscrição
- Empresa


## <a name="brazil-national-identification-card-rg"></a>Brezilya ulusal kimlik kartı (RG)

### <a name="format"></a>Biçim

Registro Geral (eski biçim): Dokuz basamaklı

Registro de Identidade (RIC) (yeni biçim): 11 basamak

### <a name="pattern"></a>Desen

Registro Geral (eski biçim):
- İki basamak
- dönem
- üç basamak
- dönem
- üç basamak
- kısa çizgi
- bir rakam, bir onay rakamıdır

Registro de Identidade (RIC) (yeni biçim):
- 10 basamak
- kısa çizgi
- bir rakam, bir onay rakamıdır

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_brazil_rg desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_brazil_rg bulunur.
- Denetimli denetimler geçer.


```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- kimlik kartı
- ulusal kimlik
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (bu anahtar sözcük büyük/harfe duyarlıdır)
- RIC (bu anahtar sözcük büyük/harfe duyarlıdır)


## <a name="brazil-physical-addresses"></a>Brezilya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Brezilya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="bulgaria-drivers-license-number"></a>Bulgaristan sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_bulgaria_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_bulgaria_eu_driver's_license_number` bulunur.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver's_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки


## <a name="bulgaria-passport-number"></a>Bulgaristan pasaport numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_bulgaria_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_bulgaria_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_bulgaria_eu_passport_number` bulunur.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт No

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="bulgaria-physical-addresses"></a>Bulgaristan fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Bulgaristan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="bulgaria-uniform-civil-number"></a>Bulgaristan muntalik (ABD)
Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 10 basamak

### <a name="pattern"></a>Desen

Boşluk ve sınırlayıcı olmayan 10 basamak

- Doğum tarihine karşılık gelen altı basamak (YYAAA)
- Doğum siparişine karşılık gelen iki basamak
- Cinsiyete karşılık gelen tek basamak: Erkek için çift basamak, kadın için tek basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_bulgaria_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_bulgaria_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_bulgaria_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinen grahdanski nomer
- egn #
- egn
- kimlik numarası
- ulusal kimlik
- ulusal numara
- ulusalsayı #
- ulusalsayı
- kişisel kimlik
- kişisel hayır
- kişisel numara
- kişiselsayı #
- sosyal güvenlik numarası
- ssn #
- ssn
- tekdüdüz kimlik
- uniform civil no
- muntalik (muntaz)
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- benzersiz benzersiz benzersiz benzersiz numara
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ грамдански id
- униформ граждански не
- униформ граждански номер
- униформграмданскиid #
- униформгражданскине. #


## <a name="canada-bank-account-number"></a>Kanada banka hesap numarası

### <a name="format"></a>Biçim

7 veya 12 basamak

### <a name="pattern"></a>Desen

Kanada Banka Hesap Numarası 7 veya 12 basamaktır.

Kanada banka hesabı taşıma numarası:
- beş basamak
- kısa çizgi
- üç basamak VEYA
- sıfır "0"
- sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_canada_bank_account_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_canada_bank_account_number anahtar sözcük bulunur.
- Normal ifade Regex_canada_bank_account_transit_number desene eşleşen içeriği bulur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_canada_bank_account_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_canada_bank_account_number anahtar sözcük bulunur.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- Kanada tasarruf bonoları
- Canada revenue agency
- Kanada mali kurumu
- doğrudan ödeme formu
- Kanada(Kanada)
- hukuk temsilcisi
- noter genel
- Oaths için tirnak
- çocuk bakımı avantajı
- evrensel çocuk bakımı
- Kanada'da çocuk vergi avantajı
- gelir vergisi avantajı
- harmonize satış vergisi
- sosyal sigorta numarası
- gelir vergisi geri ödemesi
- çocuk vergi avantajı
- bölgeli ödemeler
- kuruluş numarası
- yatırılan ödeme isteği
- bankacılık bilgileri
- doğrudan ödeme


## <a name="canada-drivers-license-number"></a>Kanada sürücüsünün lisans numarası

### <a name="format"></a>Biçim

İle göre değişir

### <a name="pattern"></a>Desen

Kapsayan çeşitli desenler:
- Alberta
- İngiliz Kolombiyası
- Manitoba
- New Brunswick
- Newfoundland/Labrador
- Nova Scotia
- Ontario
- Prince Edward Adası
- Quebec
- Saskatchewan

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_[province_name]_drivers_license_number desene eşleşen içeriği bulur.
- Bir Keyword_[province_name]_drivers_license_name anahtar sözcüğü bulunur.
- Anahtar sözcük Keyword_canada_drivers_license bulunur.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- İl kısaltması, örneğin AB
- İl adı, örneğin Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Sürücü Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Sürücüler Lic
- SürücülerLics
- Sürücüler Lisansı
- Sürücüler Lisansları
- Sürücüler Lisansı
- Sürücüler Lisansları
- Driver'Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü' Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'sLic
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisansları
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Permis de Conduire
- id
- kimlikler
- kimlik kartı numarası
- kimlik kartı numaraları
- kimlik kartı #
- idcard #s
- kimlik kartı
- kimlik kartı kartları
- kimlik kartı
- kimlik numarası
- kimlik numaraları
- tanımlama #
- tanımlama #s
- kimlik kartı
- kimlik kartları
- tanımlama
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- Sürücü Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- Sürücüler Lic #
- SürücülerLics #
- Sürücüler Lisansı #
- Sürücüler Lisansları #
- Sürücüler Lisansı #
- Sürücüler Lisansları #
- Driver'Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü' Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'sLic #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisansları #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Permis de Conduire #
- id #
- kimlikler #
- kimlik kartı #
- kimlik kartı kartları #
- kimlik kartı #
- kimlik kartı #
- kimlik kartları #
- tanımlama #


## <a name="canada-health-service-number"></a>Kanada sağlık hizmet numarası

### <a name="format"></a>Biçim

 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_canada_health_service_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_canada_health_service_number anahtar sözcük bulunur.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- kişisel sağlık numarası
- hasta bilgileri
- sağlık hizmetleri
- özel hizmetler
- otomobil kaza
- hasta hastanesi
- tir
- çalışan telafisi
- engellilik


## <a name="canada-passport-number"></a>Kanada pasaport numarası

### <a name="format"></a>Biçim

İki büyük harf, ardından altı basamak

### <a name="pattern"></a>Desen

İki büyük harf, ardından altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_canada_passport_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_canada_passport_number Keyword_passport anahtar sözcük bulunur.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- Kanada'dan(Kanada)
- Kanada pasaport
- pasaport uygulaması
- pasaport fotoğrafları
- sertifikalı çeviri aracı
- Kanada'da yaşayanlar
- işleme saatleri
- yenileme uygulaması

#### <a name="keyword_passport"></a>Keyword_passport

- Pasaport Numarası
- Pasaport No
- Pasaport #
- Pasaport #
- PassportID
- Passportno
- pasaportsayı
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport #
- PasseportNon
- Passeportn °


## <a name="canada-personal-health-identification-number-phin"></a>Kanada kişisel sağlık tanımlama numarası (PHIN)

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_canada_phin desene eşleşen içeriği bulur.
- Anahtar sözcük ve Keyword_canada_phin Keyword_canada_provinces anahtar sözcük bulunur.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- sosyal sigorta numarası
- durum bilgileri harekete
- gelir vergi bilgileri
- manitoba health
- sağlık kaydı
- satın almalar
- avantaj uygunluğu
- kişisel sağlık
- vekaletname
- kayıt numarası
- kişisel sağlık numarası
- referans referansı
- professional
- hasta başvurusu
- sağlık ve sağlık

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- Quebec
- Kuzeybatı Toprakları
- Ontario
- İngiliz Kolombiyası
- Alberta
- Saskatchewan
- Manitoba
- Yukon
- Newfoundland ve Labrador
- New Brunswick
- Nova Scotia
- Prince Edward Adası
- Kanada


## <a name="canada-physical-addresses"></a>Kanada fiziksel adresleri

Buundled adlandırılmış varlık, Kanada'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="canada-social-insurance-number"></a>Kanada sosyal sigorta numarası

### <a name="format"></a>Biçim

isteğe bağlı tireler veya boşluklar ile dokuz basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:
- üç basamak
- kısa çizgi veya boşluk
- üç basamak
- kısa çizgi veya boşluk
- üç basamak

Biçimlendirilmemiş: dokuz basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_canadian_sin desene eşleşen içeriği bulur.
- Aşağıdaki düzenlerden en az ikisi:
    - Anahtar sözcük Keyword_sin bulunur.
    - Bir başka Keyword_sin_collaborative anahtar sözcük bulunur.
    - İşlev Func_eu_date doğru tarih biçimindeki bir tarihi bulur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_unformatted_canadian_sin desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_sin bulunur.
- Denetimli denetimler geçer.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_sin"></a>Keyword_sin

- sin
- sosyal sigorta
- numero d'assurance sociale
- neden
- ssn
- ssns
- sosyal güvenlik
- numero d'assurance social
- ulusal kimlik numarası
- ulusal kimlik
- sin #
- soc ins
- sosyal ins

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- sürücü lisansı
- sürücüler lisansı
- sürücü lisansı
- sürücüler lisansı
- DOB
- Doğum Tarihi
- Doğum günü
- Doğum tarihi


## <a name="chile-identity-card-number"></a>Şili kimlik kartı numarası

### <a name="format"></a>Biçim

Yedi ile sekiz basamak arasında artı bir onay rakamı veya harf sınırlayıcılar

### <a name="pattern"></a>Desen

Yedi ile sekiz basamak arasında artı sınırlayıcılar:
- bir ile iki basamak arasında
- isteğe bağlı bir nokta
- üç basamak
- isteğe bağlı bir nokta
- üç basamak
- Tire
- tek basamaklı veya büyük/küçük harf (büyük/küçük harfe duyarlı değildir) bir onay rakamıdır

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_chile_id_card desene eşleşen içeriği bulur.
- Bir başka Keyword_chile_id_card anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_chile_id_card desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- ulusal kimlik
- ulusal kimlik numarası
- ulusal kimlik
- número de identificación nacional
- rol único nacional
- rol único tributario
- RUN
- BIRAYI
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- RUN #
- BIRAYI #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- çok fazla şey oldu
- Şili kimliği hayır.
- Şili kimlik numarası
- Şili kimliği #
- Benzersiz Vergi Kayıt Defteri
- Benzersiz Tributary Rolü
- Benzersiz Vergi Rolü
- Benzersiz Tributer Numarası
- Benzersiz Ulusal Numara
- Benzersiz Ulusal Rol
- Ulusal benzersiz rol
- Şili kimliği hayır.
- Şili kimlik numarası
- Şili kimliği #
- R.U.T
- R.U.N


## <a name="china-resident-identity-card-prc-number"></a>Çin'de yerleşik kimlik kartı (ÇK) numarası

### <a name="format"></a>Biçim

18 basamak

### <a name="pattern"></a>Desen

18 basamak:
- Adres kodu olan altı basamak
- YYYYAAD şeklinde, doğum tarihi olan sekiz basamak
- Sipariş kodu olan üç basamak
- bir rakam, bir onay rakamıdır

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_china_resident_id desene eşleşen içeriği bulur.
- Bir başka Keyword_china_resident_id anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_china_resident_id desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Yerleşik Kimlik Kartı
- ÇÇY
- Ulusal Kimlik Kartı
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定


## <a name="credit-card-number"></a>Kredi kartı numarası

### <a name="format"></a>Biçim

Biçimlendirilmiş veya biçimlendirilmemiş (dddddd) ve Luhn testini geçmesi gereken 14 - 19 basamak.

### <a name="pattern"></a>Desen

Visa, MasterCard, Discover Card, JCB, American Express, hediye kartları, diner kartları, Rupay ve China UnionPay gibi dünya çapındaki tüm önemli markalardan kartları algılar.

### <a name="checksum"></a>Checksum

Evet, Luhn denetimi

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_credit_card desene eşleşen içeriği bulur.
- Aşağıdakilerden biri doğrudur:
    - Farklı bir Keyword_cc_verification anahtar sözcük bulunur.
    - Bir Keyword_cc_name anahtar sözcüğü bulunur.
    - İşlev Func_expiration_date doğru tarih biçimindeki bir tarihi bulur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_credit_card desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- kart doğrulaması
- kart kimlik numarası
- cvn
- cid
- cvc2
- cvv2
- pin bloğu
- güvenlik kodu
- güvenlik numarası
- güvenlik yok
- sorun numarası
- sorun no
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- teta
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- cod. sicurezza
- cod sicurezza
- n autorizzazzane
- código
- codigo
- cod. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- cod. seguranca
- cod. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificacao
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- data scad
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- işlem
- işlem numarası
- başvuru numarası
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- American Express
- americanexpress
- americano americano
- Visa
- ana kart
- ana kart
- mc
- mastercards
- ana kartlar
- diner's Club
- diners kulüp
- dinersclub
- keşfedin
- kart keşfetme
- discovercard
- kartları keşfetme
- JCB
- Brand Smart
- Japonca kart bürosu
- karblanka
- karblanka
- kredi kartı
- bilgi #
- bilgi#:
- son kullanma tarihi
- exp date
- Son kullanma tarihi
- tarih d'son kullanma tarihi
- date d'exp
- son kullanma tarihi
- banka kartı
- bankcard
- kart numarası
- kart num
- kartsayı
- kartsayıları
- kart numaraları
- kredi kartı
- kredi kartları
- kredi kartları
- ccn
- kart sahibi
- kart sahibi
- kart tutucular
- kartholders
- kart kontrol edin
- checkcard
- kartları denetleme
- checkcards
- banka kartı
- banka kartı
- banka kartları
- banka kartları
- atm kartı
- atmcard
- atm kartları
- atmcards
- enroute
- rota
- kart türü
- KartMember Acct
- kartmember hesabı
- Cardno
- Kurumsal Kart
- Şirket kartları
- Kart türü
- kart hesap numarası
- kart üyesi hesabı
- KartMember Acct.
- kartı hayır.
- kart yok
- kart numarası
- carte bancaire
- carte de crédit
- carte de kredisi
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- n. carta
- n carta
- nr. carta
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
- hayır. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- debito automatico
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- no do cartao
- hayır. do cartão
- hayır. do cartao
- rupay
- union pay
- unionpay
- diner's
- diners
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- Visaカード
- Visa カード
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联


## <a name="croatia-drivers-license-number"></a>Hırvatistan sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_croatia_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya `Keywords_eu_driver's_license_number` `Keywords_croatia_eu_driver's_license_number` bulunur.

```xml
      <!-- Croatia Driver's License Number -->
      <Entity id="005b3ef1-47dd-4e68-bb02-c6db484d00f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_croatia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver's_license_number

- vozačka hervola
- vozačke hervole


## <a name="croatia-identity-card-number"></a>Hırvatistan kimlik kartı numarası
Bu varlık, AB Ulusal Kimlik Numarası hassas bilgi türü içinde yer almaktadır. Tek başına hassas bilgi türü bir varlık olarak kullanılabilir.

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

art arda dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_croatia_id_card desene eşleşen içeriği bulur.
- Bir başka Keyword_croatia_id_card anahtar sözcük bulunur.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- maystorski broj graıana
- ana ana ana sayı
- nacionalni identifikacijski broj
- ulusal kimlik numarası
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- kişisel kimlik numarası
- porezni broj
- porezni identifikacijski broj
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="croatia-passport-number"></a>Hırvatistan pasaport numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_croatia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_croatia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_croatia_eu_passport_number` bulunur.

```xml
      <!-- Croatia Passport Number -->
      <Entity id="7d7a729d-32d8-4204-8d01-d5e6a6c25581" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Hırvatistan kişisel kimlik (OIB) numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:
- 10 basamak
- son basamak bir onay rakamıdır

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_croatia_oib_number desene eşleşen içeriği bulur.
- Bir arama Keywords_croatia_eu_tax_file_number anahtar sözcüğü bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_croatia_oib_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- maystorski broj graıana
- ana ana ana sayı
- nacionalni identifikacijski broj
- ulusal kimlik numarası
- oib #
- oib
- osobna iskaznica
- osobni id
- osobni identifikacijski broj
- kişisel kimlik numarası
- porezni broj
- porezni identifikacijski broj
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="croatia-physical-addresses"></a>Hırvatistan fiziksel adresleri

Bu şaşırtıcı olmayan bir adlandırılmış varlık, Hırvatistan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="cyprus-drivers-license-number"></a>Kıbrıs sürücüleri lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 12 basamak

### <a name="pattern"></a>Desen

12 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_cyprus_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_cyprus_eu_driver's_license_number` bulunur.

```xml
      <!-- Cyprus Driver's License Number -->
      <Entity id="356fa104-f9ac-4aff-a0e4-2e6e65ea06c4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_cyprus_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver's_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>Kıbrıs kimlik kartı

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_cyprus_eu_national_id_card` eşleşen içerik bulur.
- Anahtar sözcük  `Keywords_cyprus_eu_national_id_card` bulunur.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- kimlik kartı numarası
- kimlik kartı numarası
- kimlik karti
- ulusal kimlik numarası
- kişisel kimlik numarası
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>Kıbrıs pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı olmayan 6-8 basamak

### <a name="pattern"></a>Desen

bir harf ve ardından altı ile sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_cyprus_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` bulunur.
- Normal ifade `Regex_cyprus_eu_passport_date` , tarihi D/AA/YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_cyprus_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_cyprus_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_cyprus_eu_passport_number` bulunur.

```xml
      <!-- Cyprus Passport Number -->
      <Entity id="9193e2e8-7f8c-43c1-a274-ac40d651936f" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_cyprus_eu_passport_date" />
            <Match idRef="Keywords_cyprus_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- olarak dam
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliği
- pasaport numarası
- Pasaport hayır.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- son kullanma tarihi
- verilen


## <a name="cyprus-physical-addresses"></a>Kıbrıs fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Kıbrıs'tan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="cyprus-tax-identification-number"></a>Kıbrıs vergi tanımlama numarası
Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Sekiz basamak ve belirtilen desende bir harf

### <a name="pattern"></a>Desen

sekiz basamak ve bir harf:

- "0" veya "9"
- yedi basamak
- tek harf (büyük/harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_cyprus_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_cyprus_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_cyprus_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Cyprus Tax Identification Number -->
      <Entity id="40e64bd9-55f3-4a09-9bd6-1db18dced9dd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
          <Match idRef="Keywords_cyprus_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- vergi no
- vergi kimlik kodu
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tic #
- tic
- tin kimliği
- tin no
- tin #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>Çek sürücü lisans numarası

### <a name="format"></a>Biçim

İki harf ve ardından da altı basamak

### <a name="pattern"></a>Desen

sekiz harf ve rakam:

- letter 'E' (büyük/harfe duyarlı değildir)
- bir harf
- boşluk (isteğe bağlı)
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_czech_republic_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_czech_republic_eu_driver's_license_number` bulunur.

```xml
      <Entity id="86b40d3b-d8ea-4c36-aab0-ef9416a6769c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_czech_republic_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver's_license_number

- čidičskú prúkaz
- čidičské prčkazy
- číslo ùidičského prčkazu
- čísla ùidičskích prčkaz


## <a name="czech-passport-number"></a>Çek pasaport numarası

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcılar olmadan sekiz basamak

### <a name="pattern"></a>Desen

Boşluk veya sınırlayıcılar olmadan sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_czech_republic_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_czech_republic_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_czech_republic_eu_passport_number` bulunur.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="czech-personal-identity-number"></a>Çek kişisel kimlik numarası

### <a name="format"></a>Biçim

İsteğe bağlı eğik çizgi (eski biçim) 10 basamaklı, isteğe bağlı eğik çizgi (yeni biçim) olan dokuz basamak

### <a name="pattern"></a>Desen

dokuz rakam (eski biçim):
- Doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi
- üç basamak

10 basamak (yeni biçim):
- Doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi
- Son rakamın bir onay rakamı olduğu dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev Func_czech_id_card desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_czech_id_card bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev Func_czech_id_card_new_format desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- doğum numarası
- çek Cumhuriyeti kimliği
- çekidno #
- daňové číslo
- identifikační číslo
- kimlik hayır
- kimlik numarası
- identityno #
- identityno
- sigorta numarası
- ulusal kimlik numarası
- ulusalsayı #
- ulusal numara
- osobní číslo
- kişiselsayı #
- kişisel kimlik numarası
- kişisel kimlik numarası
- kişisel numara
- pid #
- pid
- pojištňní číslo
- rč
- hanne cislo
- cafené číslo
- ssn
- ssn #
- sosyal güvenlik numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- benzersiz tanımlama numarası


## <a name="czech-republic-physical-addresses"></a>Çek Cumhuriyeti fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Çek Cumhuriyeti'nden gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="denmark-drivers-license-number"></a>Danimarka sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_denmark_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_denmark_eu_driver's_license_number` bulunur.

```xml
      <!-- Denmark Driver's License Number -->
      <Entity id="98a95812-6203-451a-a220-d39870ebef0e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_denmark_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver's_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>Danimarka pasaport numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_denmark_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` bulunur.
- Normal ifade `Regex_eu_passport_date2` , tarihi D MM YY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_denmark_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_denmark_eu_passport_number` bulunur.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="denmark-personal-identification-number"></a>Danimarka kişisel kimlik numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

10 basamak:
- Doğum tarihi olan  DAAAY biçiminde altı basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- Son rakamın onay rakamı olduğu dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Func_denmark_eu_tax_file_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_denmark_id bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade Func_denmark_eu_tax_file_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- cpr
- cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- sağlık kartı
- sağlık sigorta kartı numarası
- sağlık sigorta numarası
- kimlik numarası
- identifikationsnummer
- identifikationsnummer #
- kimlik numarası
- krankenkassennummer
- nationalid #
- ulusalsayı #
- ulusal numara
- kişiselsayı #
- personalidentityno #
- kişisel kimlik numarası
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- ssn
- ssn #
- skat id
- skat kode
- skat nummer
- skattenummer
- sosyal güvenlik numarası
- sundhedsforringringskort
- sundhedsforringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- vergi kodu
- seyahat sağlık sigorta kartı
- uniqueidentityno #
- vergi numarası
- vergi sicil numarası
- vergi no
- vergi numarası
- iş bire bir #
- vergi numarası #
- vergi yok
- taxno #
- vergi numarası
- vergi numarası yok
- tin #
- yaln #
- aracısayı #
- vergi yok #
- tin kimliği
- tin no
- cpr.nr
- cprnr
- cprnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer


## <a name="denmark-physical-addresses"></a>Danimarka fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık Danimarka'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="diseases"></a>10000 Yıl Sonra

Bu bakıla sahip olmayan bu varlık, özel adlar gibi, özel adlara eşleşen *metinleri algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="drug-enforcement-agency-dea-number"></a>Enforcement Agency (DEA) numarası

### <a name="format"></a>Biçim

İki harf ve ardından da yedi basamak

### <a name="pattern"></a>Desen

Desen aşağıdakilerin hepsini içermeli:
- bu olası harf kümesinden bir harf (büyük/küçük harfe duyarlı değildir): abcdefghjklmnprstux, bir kayıt kodudur
- tek harfli (büyük/harfe duyarlı değildir), kayıt şirketi adının ilk harfi veya '9' rakamıdır
- yedi basamak, son basamak onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_dea_number desene eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_dea_number` bulundu
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_dea_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- dea
- dea #
- uygulama yönetimi
- enişlek zorlama acentesi


## <a name="estonia-drivers-license-number"></a>Estonya sürücüsünün lisans numarası

### <a name="format"></a>Biçim

İki harf ve ardından da altı basamak

### <a name="pattern"></a>Desen

İki harf ve altı basamak:

- "ET" harfleri (büyük/küçük harfe duyarlı değildir)
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_estonia_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_estonia_eu_driver's_license_number` bulunur.

```xml
      <!-- Estonia Driver's License Number -->
      <Entity id="51da8171-da70-4cc1-9d65-055a59ca4f83" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_estonia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver's_license_number

- permis de conduire
- juubaubaderid
- ju bir sayı
- ju birauba


## <a name="estonia-passport-number"></a>Estonya pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı yok yedi basamak

### <a name="pattern"></a>Desen

bir harf ve ardından yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_estonia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_estonia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_estonia_eu_passport_number` bulunur.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="estonia-personal-identification-code"></a>Estonya Kişisel Kimlik Kodu

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- cinsiyete ve doğum yüzyılına karşılık gelen bir basamak (tek sayı erkek, çift sayı kadın; 1-2: 19. yüzyıl; 3-4: 20. yüzyıl; 5-6: 21. yüzyıl)
- Doğum tarihine karşılık gelen altı basamak (YYAAA)
- Aynı tarihte doğan kişiyi ayıran seri numarasına karşılık gelen üç basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_estonia_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_estonia_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_estonia_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- ulusal kimlik numarası
- ulusal numara
- kişisel kod
- kişisel kimlik numarası
- kişisel kimlik kodu
- kişisel kimlik numarası
- kişiselsayı #
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="estonia-physical-addresses"></a>Estonya fiziksel adresleri

Buundled adlı varlık, Estonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="eu-debit-card-number"></a>AB banka kartı numarası

### <a name="format"></a>Biçim

16 basamak

### <a name="pattern"></a>Desen

Karmaşık ve güçlü desen

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_eu_debit_card desene eşleşen içeriği bulur.
- Aşağıdakilerden en az biri doğrudur:
    - Bir başka Keyword_eu_debit_card anahtar sözcük bulunur.
    - Anahtar sözcük Keyword_card_terms_dict bulunur.
    - Anahtar sözcük Keyword_card_security_terms_dict bulunur.
    - Bir arama Keyword_card_expiration_terms_dict anahtar sözcüğü bulunur.
    - İşlev Func_expiration_date doğru tarih biçimindeki bir tarihi bulur.
- Denetimli denetimler geçer.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- hesap numarası
- kart numarası
- kartı hayır.
- güvenlik numarası
- bilgi #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- acct num
- acct no
- American Express
- americanexpress
- americano americano
- amex
- atm kartı
- atm kartları
- atm kaart
- atmcard
- atmcards
- atmkaart
- atmkaarten
- bancontact
- banka kartı
- bankkaart
- kart sahibi
- kart tutucular
- kart num
- kart numarası
- kart numaraları
- kart türü
- cardano numerico
- kart sahibi
- kartholders
- kartsayı
- kartsayıları
- carta carta
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- karblanka
- carte bleue
- carte de kredisi
- carte de crédit
- carte di credito
- karblanka
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- cb
- ccn
- kart kontrol edin
- kartları denetleme
- checkcard
- checkcards
- biraat
- cirrus
- cirrus-edc-olog
- controlekaart
- controlekaarten
- kredi kartı
- kredi kartları
- kredi kartı
- kredi kartları
- debetkaart
- debetkaarten
- banka kartı
- banka kartları
- banka kartı
- banka kartları
- debito automatico
- diners kulüp
- dinersclub
- keşfedin
- kart keşfetme
- kartları keşfetme
- discovercard
- discovercards
- débito automático
- edc
- eigentümername
- Avrupa banka kartı
- yaşay
- ya da
- in via 365
- Japonca kart bürosu
- japanse kaartdienst
- jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- karte
- karteninhaber
- karteninhabers
- kartennr
- kartennummer
- kreditkarte
- kreditkarten-nummer
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- olarak yenile
- ana kart
- ana kartlar
- ana kart
- mastercards
- mc
- nakit para
- n carta
- carta
- no de tarjeta
- no do cartao
- no do cartão
- hayır. de tarjeta
- hayır. do cartao
- hayır. do cartão
- nr carta
- nr. carta
- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- nº carta
- nº de carte
- nº de la carte
- nº de tarjeta
- nº do cartao
- nº do cartão
- nº. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- solo
- supporti di scheda
- supporto di scheda
- değiştir
- tarjeta atm
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetahabiente
- tipo della scheda
- ufficio giapponese della
- scheda
- v ödeme
- v-pay
- visa
- visa plus
- visa electron
- visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- kart kimlik numarası
- kart doğrulaması
- cardi la verifica
- cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- cod. seg
- cod. seguranca
- cod. segurança
- cod. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- cvc
- cvc2
- cvn
- cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- atlft nr uit
- sorun no
- sorun numarası
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- hayır. dell'edizione
- hayır. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nº autorizzazzane
- número de verificação
- perno il blobloblo
- pin bloğu
- teta
- prüfziffer
- güvenlik kodu
- güvenlik yok
- güvenlik numarası
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldbdbdb
- veiligheid nr
- veiligheidsaantal
- veiligheidscode
- veiligheidsnummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expiracao
- data de expiração
- data del exp
- data di exp
- data di scadenza
- data em que expira
- data scad
- data scadenza
- date de validité
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- exp date
- exp datum
- son kullanma tarihi
- son kullanma
- son kullanma tarihi
- son kullanma tarihi
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- değere edilebilir
- validade
- valido hasta
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta


## <a name="eu-drivers-license-number"></a>AB sürücü lisans numarası

Bu varlıklar AB'nin Lisans Numarası'dır ve hassas bilgi türleridir.

- [Avusturya](#austria-drivers-license-number)
- [Belçika](#belgium-drivers-license-number)
- [Bulgaristan](#bulgaria-drivers-license-number)
- [Hırvatistan](#croatia-drivers-license-number)
- [Kıbrıs](#cyprus-drivers-license-number)
- [Czech](#czech-drivers-license-number)
- [Danimarka](#denmark-drivers-license-number)
- [Estonya](#estonia-drivers-license-number)
- [Finlandiya](#finland-drivers-license-number)
- [Fransa](#france-drivers-license-number)
- [Almanya](#germany-drivers-license-number)
- [Yunanistan](#greece-drivers-license-number)
- [Macaristan](#hungary-drivers-license-number)
- [İrlanda](#ireland-drivers-license-number)
- [İtalya](#italy-drivers-license-number)
- [Letonya](#latvia-drivers-license-number)
- [Litvanya](#lithuania-drivers-license-number)
- [Luxemburg](#luxemburg-drivers-license-number)
- [Malta](#malta-drivers-license-number)
- [Hollanda](#netherlands-drivers-license-number)
- [Polonya](#poland-drivers-license-number)
- [Portekiz](#portugal-drivers-license-number)
- [Romanya](#romania-drivers-license-number)
- [Slovakya](#slovakia-drivers-license-number)
- [Slovenya](#slovenia-drivers-license-number)
- [İspanya](#spain-drivers-license-number)
- [İsveç](#sweden-drivers-license-number)
- [B.K.](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>AB ulusal kimlik numarası

Bu varlıklar AB Ulusal Kimlik Numarası'dır ve hassas bilgi türleridir.

- [Avusturya](#austria-identity-card)
- [Belçika](#belgium-national-number)
- [Bulgaristan](#bulgaria-uniform-civil-number)
- [Hırvatistan](#croatia-identity-card-number)
- [Kıbrıs](#cyprus-identity-card)
- [Czech](#czech-personal-identity-number)
- [Danimarka](#denmark-personal-identification-number)
- [Estonya](#estonia-personal-identification-code)
- [Finlandiya](#finland-national-id)
- [Fransa](#france-national-id-card-cni)
- [Almanya](#germany-identity-card-number)
- [Yunanistan](#greece-national-id-card)
- [Macaristan](#hungary-personal-identification-number)
- [İrlanda](#ireland-personal-public-service-pps-number)
- [İtalya](#italy-fiscal-code)
- [Letonya](#latvia-personal-code)
- [Litvanya](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-natural-persons)
- [Malta](#malta-identity-card-number)
- [Hollanda](#netherlands-citizens-service-bsn-number)
- [Polonya](#poland-national-id-pesel)
- [Portekiz](#portugal-citizen-card-number)
- [Romanya](#romania-personal-numeric-code-cnp)
- [Slovakya](#slovakia-personal-number)
- [Slovenya](#slovenia-unique-master-citizen-number)
- [İspanya](#spain-dni)
- [B.K.](#uk-national-insurance-number-nino)


## <a name="eu-passport-number"></a>AB pasaport numarası

Bu varlıklar AB pasaport numarasındadır ve hassas bilgi türleridir. Bu varlıklar AB pasaport sayı paketinde yer alıyor.

- [Avusturya](#austria-passport-number)
- [Belçika](#belgium-passport-number)
- [Bulgaristan](#bulgaria-passport-number)
- [Hırvatistan](#croatia-passport-number)
- [Kıbrıs](#cyprus-passport-number)
- [Czech](#czech-passport-number)
- [Danimarka](#denmark-passport-number)
- [Estonya](#estonia-passport-number)
- [Finlandiya](#finland-passport-number)
- [Fransa](#france-passport-number)
- [Almanya](#germany-passport-number)
- [Yunanistan](#greece-passport-number)
- [Macaristan](#hungary-passport-number)
- [İrlanda](#ireland-passport-number)
- [İtalya](#italy-passport-number)
- [Letonya](#latvia-passport-number)
- [Litvanya](#lithuania-passport-number)
- [Luxemburg](#luxemburg-passport-number)
- [Malta](#malta-passport-number)
- [Hollanda](#netherlands-passport-number)
- [Polonya](#poland-passport-number)
- [Portekiz](#portugal-passport-number)
- [Romanya](#romania-passport-number)
- [Slovakya](#slovakia-passport-number)
- [Slovenya](#slovenia-passport-number)
- [İspanya](#spain-passport-number)
- [İsveç](#sweden-passport-number)
- [ABD/İngiltere pasaport numarası](#usuk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>AB sosyal güvenlik numarası veya eşdeğer tanımlama

Bunlar, AB Sosyal Güvenlik Numarası veya eşdeğer kimlik bilgilerine sahip olan varlıklardır ve hassas bilgi türleridir.

- [Avusturya](#austria-social-security-number)
- [Belçika](#belgium-national-number)
- [Hırvatistan](#croatia-personal-identification-oib-number)
- [Czech](#czech-personal-identity-number)
- [Danimarka](#denmark-personal-identification-number)
- [Finlandiya](#finland-national-id)
- [Fransa](#france-social-security-number-insee)
- [Almanya](#germany-identity-card-number)
- [Yunanistan](#greece-national-id-card)
- [Macaristan](#hungary-social-security-number-taj)
- [Portekiz](#portugal-citizen-card-number)
- [İspanya](#spain-social-security-number-ssn)
- [İsveç](#sweden-national-id)


## <a name="eu-tax-identification-number"></a>AB Vergi tanımlama numarası

Bu varlıklar AB Vergi numarası hassas bilgi türündedir.

- [Avusturya](#austria-tax-identification-number)
- [Belçika](#belgium-national-number)
- [Bulgaristan](#bulgaria-uniform-civil-number)
- [Hırvatistan](#croatia-identity-card-number)
- [Kıbrıs](#cyprus-tax-identification-number)
- [Czech](#czech-personal-identity-number)
- [Danimarka](#denmark-personal-identification-number)
- [Estonya](#estonia-personal-identification-code)
- [Finlandiya](#finland-national-id)
- [Fransa](#france-tax-identification-number)
- [Almanya](#germany-tax-identification-number)
- [Yunanistan](#greece-tax-identification-number)
- [Macaristan](#hungary-tax-identification-number)
- [İrlanda](#ireland-personal-public-service-pps-number)
- [İtalya](#italy-fiscal-code)
- [Letonya](#latvia-personal-code)
- [Litvanya](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-non-natural-persons)
- [Malta](#malta-tax-identification-number)
- [Hollanda](#netherlands-tax-identification-number)
- [Polonya](#poland-tax-identification-number)
- [Portekiz](#portugal-tax-identification-number)
- [Romanya](#romania-personal-numeric-code-cnp)
- [Slovakya](#slovakia-personal-number)
- [Slovenya](#slovenia-tax-identification-number)
- [İspanya](#spain-tax-identification-number)
- [İsveç](#sweden-tax-identification-number)
- [B.K.](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>Finlandiya sürücüsünün lisans numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

Kısa çizgi içeren 10 basamak:

- altı basamak
- kısa çizgi
- üç basamak
- basamak veya harf

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_finland_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_finland_eu_driver's_license_number` bulunur.

```xml
      <!-- Finland Driver's License Number -->
      <Entity id="bb3b27a3-79bd-4ac4-81a7-f9fca3c7d1a7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_finland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver's_license_number

- ajokortti
- permis de conduire
- ajokortin çok sayıda
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot


## <a name="finland-european-health-insurance-number"></a>Finlandiya Avrupa sağlık sigorta numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

20 basamaklı sayı

### <a name="pattern"></a>Desen

20 basamaklı sayı:

- 10 basamak - 8024680246
- isteğe bağlı bir boşluk veya kısa çizgi
- 10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtexex Regex_Finland_European_Health_Insurance_Number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_Finland_European_Health_Insurance_Number bulunur.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- finlandehicnumber #
- finska sjukförsäkringskort
- sağlık kartı
- sağlık sigorta kartı
- sağlık sigorta numarası
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti


## <a name="finland-national-id"></a>Finlandiya ulusal kimliği

### <a name="format"></a>Biçim

Altı basamak artı bir yüzyıl artı üç basamak ve bir de onay basamaklarını gösteren bir karakter

### <a name="pattern"></a>Desen

Desen aşağıdakilerin hepsini içermeli:
- Doğum tarihi olan  DAAAY biçiminde altı basamak
- century marker ('-', '+' veya 'a')
- üç basamaklı kişisel kimlik numarası
- bir onay rakamı olan basamak veya harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_finnish_national_id desene eşleşen içeriği bulur
- Keyword_finnish_national_id anahtar sözcüğü bulunur
- denetimli denetimler geçer

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_finnish_national_id desene eşleşen içeriği bulur
- denetimli denetimler geçer

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- id no
- kimlik numarası
- kimlik numarası
- identite bir çok
- kimlik numarası
- kimliksayı
- kansallinen henkilötunnus
- kansallisen henkilökortin
- ulusal kimlik kartı
- national id No.
- kişisel kimlik
- kişisel kimlik kodu
- kişiselsayı #
- personbeteckning
- personnummer
- sosyal güvenlik numarası
- sosiaaliturvatunnus
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus


## <a name="finland-passport-number"></a>Finlandiya pasaport numarası

Bu varlık EU Passport Number hassas bilgi türünde mevcuttur ve tek başına hassas bilgi türü bir varlık olarak kullanılabilir.

### <a name="format"></a>Biçim
dokuz harf ve rakam bileşimi

### <a name="pattern"></a>Desen
dokuz harf ve rakam birleşimi:
- İki harf (büyük/küçük harfe duyarlı değildir)
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene `Regex_finland_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keyword_finland_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_finland_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keyword_finland_passport_number` bulunur.

```xml
      <!-- Finland Passport Number -->
      <Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin numero( #
- passin numero #
- passin numero(
- passi #
- geçiş numarası

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="finland-physical-addresses"></a>Finlandiya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Finlandiya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="france-drivers-license-number"></a>Fransa sürücü lisans numarası

Bu varlık AB Sürücü's Lisans Numarası hassas bilgi türünde mevcuttur ve tek başına hassas bilgi türü bir varlık olarak kullanılabilir.

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

Fransızca telefon numaraları gibi benzer düzenlerde indirim yapmak için doğrulamaya sahip 12 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_french_drivers_license desene eşleşen içeriği bulur.
- bir Keyword_french_drivers_license anahtar sözcüğü bulunur.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası
- permis de conduire
- lisans numarası
- lisans numarası
- lisans numaraları
- lisans numaraları
- numéros de licence


## <a name="france-health-insurance-number"></a>Fransa sağlık sigorta numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

21 basamaklı sayı

### <a name="pattern"></a>Desen

21 basamaklı sayı:

- 10 basamak
- isteğe bağlı bir boşluk
- 10 basamak
- isteğe bağlı bir boşluk
- basamak


### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- kayıtex Regex_France_Health_Insurance_Number desene eşleşen içeriği bulur.
- bu sözcükten Keyword_France_Health_Insurance_Number anahtar sözcük bulunur.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- sigorta kartı
- carte vitale
- carte d'assuré social


## <a name="france-national-id-card-cni"></a>Fransa ulusal kimlik kartı (CNI)

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

12 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade Regex_france_cni desene eşleşen içeriği bulur.
- Bir başka Keywords_france_eu_national_id_card anahtar sözcük bulunur.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- kart numarası
- carte nationale d'identité
- carte nationale d'idenite no
- cni #
- cni
- compte bancaire
- ulusal kimlik numarası
- ulusal kimlik
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale


## <a name="france-passport-number"></a>Fransa pasaport numarası

Bu varlık AB Pasaport Numarası hassas bilgi türünde kullanılabilir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

dokuz rakam ve harf

### <a name="pattern"></a>Desen

dokuz rakam ve harf:
- İki basamak
- İki harf (büyük/küçük harfe duyarlı değildir)
- beş basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_fr_passport` desene eşleşen içeriği bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date3` tarihi DD MM YYYY biçiminde veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur biçimde bulur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_fr_passport` desene eşleşen içeriği bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keywords_france_eu_passport_number` bulunur.


```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passeport français
- passeportportre
- passeport carte
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="france-physical-addresses"></a>Fransa fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Fransa'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="france-social-security-number-insee"></a>Fransa sosyal güvenlik numarası (INSEE)

### <a name="format"></a>Biçim

15 basamak

### <a name="pattern"></a>Desen

İki desenden birini eşleşmesi gerekir:
- 13 basamak, ardından bir boşluk ve ardından iki basamak<br/>
veya
- Art arda 15 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_french_insee` desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_fr_insee bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, Func_french_insee veya Func_fr_insee desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- ulusal kimlik
- ulusal kimlik
- no d'identité
- hayır. d'identité
- numéro d'assurance
- numéro d'identité
- çok sayıda d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- hayır. d'identite
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- sosyal güvenlik numarası
- sosyal güvenlik kodu
- sosyal sigorta numarası


## <a name="france-tax-identification-number"></a>Fransa vergi tanımlama numarası

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

13 basamak

- 0, 1, 2 veya 3 olması gereken bir basamak
- Bir rakam
- Boşluk (isteğe bağlı)
- İki basamak
- Boşluk (isteğe bağlı)
- Üç basamak
- Boşluk (isteğe bağlı)
- Üç basamak
- Boşluk (isteğe bağlı)
- Üç onay rakamı


### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_france_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_france_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_france_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- France Tax Identification Number (numéro SPI.) -->
      <Entity id="ed59e77e-171d-442c-9ec1-88e2ebcb5b0a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Match idRef="Keywords_france_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_france_eu_telephone_number" />
            <Match idRef="Keywords_france_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="france-value-added-tax-number"></a>Fransa'da katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 karakter alfasayısal desen

### <a name="pattern"></a>Desen

13 karakter alfasayısal desen:

- İki harf - FR (büyük/küçük harfe duyarlı değil)
- isteğe bağlı bir boşluk veya kısa çizgi
- İki harf veya basamak
- isteğe bağlı bir boşluk, nokta, kısa çizgi veya virgül
- üç basamak
- isteğe bağlı bir boşluk, nokta, kısa çizgi veya virgül
- üç basamak
- isteğe bağlı bir boşluk, nokta, kısa çizgi veya virgül
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_france_value_added_tax_number desene eşleşen içeriği bulur.
- Bir Keywords_france_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_france_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- kdv numarası
- kdv yok
- kdv #
- katma değer vergisi
- olarak tanımlama no numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification atom


## <a name="generic-medication-names"></a>Genel ilaç adları

Bu bakıla sahip olmayan bu varlık, asetatoz gibi genel *ilaçların adlarını algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="germany-drivers-license-number"></a>Almanya sürücü lisans numarası

Bu hassas bilgi türü varlık AB Sürücü'sinde Lisans Numarası hassas bilgi türüne dahildir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

11 rakam ve harf birleşimi

### <a name="pattern"></a>Desen

11 rakam ve harf (büyük/küçük harfe duyarlı değildir):
- basamak veya harf
- İki basamak
- altı basamak veya harf
- basamak
- basamak veya harf

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_german_drivers_license desene eşleşen içeriği bulur.
- Bir arama Keyword_german_drivers_license_number anahtar sözcüğü bulunur.
- Denetimli denetimler geçer.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
- fuehrerscheinnummer
- führerschein- 
- fuhrerschein- 
- fuehrerschein- 
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-fuhrerschein
- nr-fuehrerschein
- no-führerschein
- no-fuhrerschein
- no-fuehrerschein
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dlno


## <a name="germany-identity-card-number"></a>Almanya kimlik kartı numarası

### <a name="format"></a>Biçim

1 Kasım 2010'dan itibaren: Dokuz ile on bir harf ve basamak

1 Nisan 1987 ile 31 Ekim 2010 arasında: 10 basamak

### <a name="pattern"></a>Desen

1 Kasım 2010'dan bu yana: 9 - 11 karakter alfasayısal desen
- bir L, M, N, P, R, T, V, W, X, Y (büyük/harfe duyarlı değil)
- C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y ve Z'de sekiz basamak veya harf (büyük/küçük harfe duyarlı değil)
- isteğe bağlı onay basamakları
- İsteğe bağlı d/D

1 Nisan 1987 ile 31 Ekim 2010 arasında:
- 10 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_german_id_card_with_check` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_germany_id_card` bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade `Regex_germany_id_card` desene eşleşen içerik bulur (2010 öncesi veya 2010 öncesi ya da 10 basamaklık bir desen verilen 9 karakter.
- Bir başka Keyword_germany_id_card anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev, `Func_german_id_card_with_check` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.


```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75"> 
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" /> 
         <Match idRef="Keyword_germany_id_card" /> 
        </Pattern>
        <Version minEngineVersion="15.20.4545.000"> 
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" /> 
          </Pattern> 
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" /> 
          </Pattern> 
        </Version>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- tanımlama
- identifikation
- identifizierungsnummer
- kimlik kartı
- kimlik numarası
- id-nummer
- kişisel kimlik
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer


## <a name="germany-passport-number"></a>Almanya pasaport numarası

### <a name="format"></a>Biçim

9 - 11 karakter

### <a name="pattern"></a>Desen

- C, F, G, H, J, K (büyük/harfe duyarlı değil) içinde bir harf
- C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y ve Z'de sekiz basamak veya harf (büyük/küçük harfe duyarlı değil)
- isteğe bağlı onay basamakları
- İsteğe bağlı d/D

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_german_passport_checksum` desene eşleşen içeriği bulur.
- Anahtar sözcük veya `Keyword_german_passport` `Keywords_eu_passport_number_common` bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_german_passport` dokuz karakter düzenine (sayısal denetimi ve isteğe bağlı d/D olmadan) eşleşen içeriği bulur.
- Anahtar sözcük veya `Keyword_german_passport` `Keywords_eu_passport_number_common` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev, `Func_german_passport_checksum` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport no.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları


## <a name="germany-physical-addresses"></a>Almanya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Almanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="germany-tax-identification-number"></a>Almanya vergi tanımlama numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 11 basamak

### <a name="pattern"></a>Desen

11 basamak

- İki basamak
- İsteğe bağlı bir boşluk
- Üç basamak
- İsteğe bağlı bir boşluk
- Üç basamak
- İsteğe bağlı bir boşluk
- İki basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_germany_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_germany_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_germany_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- suer kimliği
- steueridentifikationsnummer
- steuernummer
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- zinn #
- zinn
- zinnnummer


## <a name="germany-value-added-tax-number"></a>Almanya'nın katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 karakter alfasayısal desen

### <a name="pattern"></a>Desen

11 karakterli alfasayısal desen:

- a letter D or d
- E harfi veya e harfi
- isteğe bağlı bir boşluk
- üç basamak
- isteğe bağlı boşluk veya virgül
- üç basamak
- isteğe bağlı boşluk veya virgül
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_germany_value_added_tax_number desene eşleşen içeriği bulur.
- Bir Keywords_germany_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_germany_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- kdv numarası
- kdv yok
- kdv #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>Yunanistan sürücü lisans numarası

Bu varlık, AB'nin Lisans Numarası hassas bilgi türüne dahildir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_greece_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_greece_eu_driver's_license_number` bulunur.

```xml
      <!-- Greece Driver's License Number -->
      <Entity id="7a2200b5-aacf-4e3c-ab36-136d3e68b7da" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_greece_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver's_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>Yunanistan ulusal kimlik kartı

### <a name="format"></a>Biçim

7-8 harf ve rakam ile çizgi birleşimi

### <a name="pattern"></a>Desen

Yedi harf ve sayı (eski biçim):
- Bir harf (Yunan alfabesinin herhangi bir harfi)
- Tire
- Altı basamak

Sekiz harf ve sayı (yeni biçim):
- Hem Yunanca hem de Latin alfabelerinde büyük harf karakterler bulunan iki harf (ABEZHIKMNOPTYX)
- Tire
- Altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_greece_id_card desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_greece_id_card bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade Regex_greece_id_card desene eşleşen içeriği bulur.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- Yunanca kimlik
- Yunanca ulusal kimliği
- Yunanca kişisel kimlik kartı
- Yunanca yunanca kimlik
- kimlik kartı
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>Yunanistan pasaport numarası

### <a name="format"></a>Biçim

İki harf ve ardından boşluk veya sınırlayıcı yok, yedi basamak

### <a name="pattern"></a>Desen

İki harf, ardından yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_greece_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` bulunur.
- Normal ifade `Regex_greece_eu_passport_date` , tarihi AAAA YY biçiminde (Örnek - 28 Ağu 19) veya bir anahtar sözcük `Keywords_greece_eu_passport_date` bulur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_greece_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_greece_eu_passport_number` bulunur.

```xml
      <!-- Greece Passport Number -->
      <Entity id="7e65eb47-cdf9-4f52-8f90-2a27d5ee67e3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_greece_eu_passport_date" />
            <Match idRef="Keywords_greece_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο


## <a name="greece-physical-addresses"></a>Yunanistan fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Yunanistan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="greece-social-security-number-amka"></a>Yunanistan Sosyal Güvenlik Numarası (AMKA)

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 11 basamak

### <a name="pattern"></a>Desen

- Doğum tarihi olarak altı basamak YYAAA
- Dört basamak
- bir onay basamakı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_greece_eu_ssn` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_greece_eu_ssn_or_equivalent` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_greece_eu_ssn` desene eşleşen içeriği bulur.

```xml
      <!-- Greece Social Security Number (AMKA) -->
      <Entity id="e39b03f4-50ea-41ae-af7a-a4b9539596ad" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_greece_eu_ssn" />
          <Match idRef="Keywords_greece_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_greece_eu_ssn" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- sosyal güvenlik yok
- socialsecurityno #
- sosyal güvenlik numarası
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης


## <a name="greece-tax-identification-number"></a>Yunanistan vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan dokuz basamak

### <a name="pattern"></a>Desen

Dokuz rakam

### <a name="checksum"></a>Checksum

Uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_greece_eu_tax_file_number` eşleşen içerik bulur.
- Anahtar sözcük  `Keywords_greece_eu_tax_file_number` bulunur.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- afm #
- afm
- aμμ|aμμ αμμμμ αμμ 1
- aμμ
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- vergi kayıt defteri no
- vergi kayıt defteri numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- taxregistryno #
- tin kimliği
- tin no
- tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>Hong Kong kimlik kartı (HKID) numarası

### <a name="format"></a>Biçim

8-9 harf ve sayı ile son karakterin çevresinde isteğe bağlı parantezlerin bileşimi

### <a name="pattern"></a>Desen

8-9 harf birleşimi:
- 1-2 harf (büyük/küçük harfe duyarlı değildir)
- Altı basamak
- Son karakter (herhangi bir rakam veya A harfi), onay rakamıdır ve isteğe bağlı olarak parantez içine alınır.

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_hong_kong_id_card desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_hong_kong_id_card bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_hong_kong_id_card desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- hong kong kimlik kartı
- HKIDC
- kimlik kartı
- kimlik kartı
- hk kimlik kartı
- hong kong kimliği
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証


## <a name="hungary-drivers-license-number"></a>Macaristan sürücünün lisans numarası

### <a name="format"></a>Biçim

İki harf ve ardından da altı basamak

### <a name="pattern"></a>Desen

İki harf ve altı basamak:

- İki harf (büyük/küçük harfe duyarlı değildir)
- Altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_hungary_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_hungary_eu_driver's_license_number` bulunur.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver's_license_number

- vezetoi engedely
- vezetazı engedély
- vezetazı engedélyek


## <a name="hungary-passport-number"></a>Macaristan pasaport numarası

### <a name="format"></a>Biçim

İki harf ve ardından boşluk veya sınırlayıcı yok, altı veya yedi basamak

### <a name="pattern"></a>Desen

İki harf, ardından altı veya yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_hungary_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` bulunur.
- Normal ifade `Regex_hungary_eu_passport_date` , tarihi AAAA/AAA YY (Örnek - 01 MÁR/MAR 12) `Keywords_eu_passport_date` biçiminde veya bir anahtar sözcük bulunan

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_hungary_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_hungary_eu_passport_number` bulunur.

```xml
      <!-- Hungary Passport Number -->
      <Entity id="5b483910-9aa7-4c99-9917-f4001464bda7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_hungary_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevá száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="hungary-personal-identification-number"></a>Macaristan kişisel kimlik numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- Cinsiyete karşılık gelen bir rakam, erkek için 1, Kadın için 2. Diğer sayılar, 1900'den önce doğan veya çift yataklı olan insanlar için de mümkündür.
- Doğum tarihine karşılık gelen altı basamak (YYAAA)
- Seri numarasına karşılık gelen üç basamak
- Tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev,  `Func_hungary_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_hungary_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev,  `Func_hungary_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- kimlik numarası
- kimlik numarası
- sz ig
- sz. ig.
- sz.ig.
- személyazonosító ig buvány
- személyi ig biravány


## <a name="hungary-physical-addresses"></a>Macaristan fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Macaristan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="hungary-social-security-number-taj"></a>Macaristan sosyal güvenlik numarası (TAJ)

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan dokuz basamak

### <a name="pattern"></a>Desen

Dokuz rakam

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev,  `Func_hungary_eu_ssn_or_equivalent` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_hungary_eu_ssn_or_equivalent` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev,  `Func_hungary_eu_ssn_or_equivalent` desene eşleşen içeriği bulur.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- Macarca sosyal güvenlik numarası
- sosyal güvenlik numarası
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- taj
- taj #
- ssn
- ssn #
- sosyal güvenlik yok
- áfa
- ayyzösségi adószám
- általááá forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>Macaristan vergi tanımlama numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı yok 10 basamak

### <a name="pattern"></a>Desen

10 basamak:

- "8" olması gereken bir rakam
- Sekiz basamak
- Tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev,  `Func_hungary_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_hungary_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev,  `Func_hungary_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Hungary Tax Identification Number -->
      <Entity id="ede42eb4-59d9-49eb-9603-d7853fbda91d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Match idRef="Keywords_hungary_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- Macarca tin
- hungatiantin #
- vergi dairesi no
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- kdv numarası


## <a name="hungary-value-added-tax-number"></a>Macaristan değeri eklenen vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

10 karakter alfasayısal desen

### <a name="pattern"></a>Desen

10 karakter alfasayısal desen:

- İki harf - HU veya hu
- isteğe bağlı boşluk
- sekiz basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev Func_hungarian_value_added_tax_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keywords_hungarian_value_added_tax_number bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev Func_hungarian_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- kdv
- katma değer vergi numarası
- kdv #
- vatno #
- macarvatno #
- vergi no.
- katma değer vergi áfa
- ayyzösségi adószám
- általááá forgalmi adó szám
- hozzáadottérték adó
- áfa szám


## <a name="iceland-physical-addresses"></a>İzlanda fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, İzlanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>SOSYAL GÜVENLIK kapsamındaki ABD Engellilik Değerlendirmesinde listelenen engellilik bozuklukları

Bu bakıla sahip olmayan bu varlık, ABD Engellilik Değerlendirme'de, disk kupa gibi, Sosyal Güvenlik kapsamındaki engellilik algılamada bulunan adları *algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="india-drivers-license-number"></a>Hindistan Sürücü Lisans Numarası

### <a name="format"></a>Biçim

15 karakter alfasayısal desen

### <a name="pattern"></a>Desen

15 harf veya rakam:
- eyalet kodunu gösteren iki harf
- isteğe bağlı boşluk veya kısa çizgi
- Şehir kodunu gösteren iki rakam
- isteğe bağlı boşluk veya kısa çizgi
- sorunun yıl gösteren dört basamak
- isteğe bağlı boşluk veya kısa çizgi
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene `Regex_india_driving_license` eşleşen içerik bulur.
- Anahtar sözcük `Keywords_eu_driver's_license_number_common` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_india_driving_license` eşleşen içerik bulur.


```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver's_license_number_common

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası



## <a name="india-gst-number"></a>Hindistan GST Numarası

### <a name="format"></a>Biçim

15 karakter alfasayısal desen

### <a name="pattern"></a>Desen

15 harf veya rakam:
- Geçerli durum kodunu temsil eden iki basamak
- isteğe bağlı bir boşluk veya tire
- Kalıcı Hesap Numarasını (PAN) temsil eden on karakter 
- bir harf veya rakam
- isteğe bağlı bir boşluk veya tire
- bir harf 'z' veya 'Z'
- isteğe bağlı bir boşluk veya tire
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_india_gst_number` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_india_gst_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_india_gst_number` desene eşleşen içeriği bulur.


```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- gst
- gstin
- mal ve hizmet vergisi
- mal ve hizmet vergisi


## <a name="india-permanent-account-number-pan"></a>Hindistan kalıcı hesap numarası (PAN)

### <a name="format"></a>Biçim

10 harf veya rakam

### <a name="pattern"></a>Desen

10 harf veya rakam:
- Üç harf (büyük/küçük harfe duyarlı değildir)
- C, P, H, F, A, T, B, L, J, G harfli (büyük/küçük harfe duyarlı değildir)
- Bir harf
- Dört basamak
- Alfabetik onay rakamı olan bir harf

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_india_permanent_account_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_india_permanent_account_number bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade Regex_india_permanent_account_number desene eşleşen içeriği bulur.


```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Kalıcı Hesap Numarası
- YATAY KAYDıRMA

## <a name="india-unique-identification-aadhaar-number"></a>Hindistan benzersiz tanımlama (Aadhaar) numarası

### <a name="format"></a>Biçim

İsteğe bağlı boşluklar veya tireler içeren 12 basamak

### <a name="pattern"></a>Desen

12 basamak:
- 0 veya 1 değil rakam
- Üç basamak
- İsteğe bağlı bir boşluk veya kısa çizgi
- Dört basamak
- İsteğe bağlı bir boşluk veya kısa çizgi
- Son basamak, yani onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_india_aadhaar desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_india_aadhar bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- İşlev Func_india_aadhaar desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- kullanıcı arabirimi
- आधार
- uidai


## <a name="india-voter-id-card"></a>Hindistan Kimlik Kartı

### <a name="format"></a>Biçim

10 karakter alfasayısal desen

### <a name="pattern"></a>Desen

10 harf veya rakam:
- üç harf
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_india_voter_id_card` eşleşen içerik bulur.
- Anahtar sözcük `Keyword_india_voter_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade desene `Regex_india_voter_id_card` eşleşen içerik bulur.


```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- 1912
- bilginlik
- card
- bilgi kartı
- seçici fotoğraflı kimlik kartı
- DESTANSı
- ECI
- election commmision


## <a name="indonesia-identity-card-ktp-number"></a>Endonezya kimlik kartı (KTP) numarası

### <a name="format"></a>Biçim

İsteğe bağlı dönemler içeren 16 basamak

### <a name="pattern"></a>Desen

16 basamak:
- İki basamaklı il kodu
- Nokta (isteğe bağlı)
- İki basamaklı regency or city code
- İki basamaklı alt dağıtım kodu
- Nokta (isteğe bağlı)
- Doğum tarihi olan  DAAAY biçiminde altı basamak
- Nokta (isteğe bağlı)
- Dört basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- Normal ifade Regex_indonesia_id_card desene eşleşen içeriği bulur.
- Bir Keyword_indonesia_id_card anahtar sözcüğü bulunur.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Uluslararası bankacılık hesap numarası (IBAN)

### <a name="format"></a>Biçim

Ülke kodu (iki harf) artı onay basamakları (iki basamaklı) artı bban numarası (en çok 30 karakter)

### <a name="pattern"></a>Desen

Desen aşağıdakilerin hepsini içermeli:

- İki harfli ülke kodu
- İki basamaklı onay kutusu (ardından isteğe bağlı bir boşluk)
- Dört harf veya rakamdan oluşur 1-7 grupları (boşluklarla ayrılabilir)
- 1-3 harf veya rakam

Her ülkenin biçimi biraz farklıdır. IBAN'a duyarlı bilgi türü şu 60 ülkeyi kapsar:

- reklam
- ae
- al
- saat
- az
- ba
- be
- bg
- 10 gün içinde
- ch
- cr
- cy
- cz
- de
- dk
- yap
- ee
- es
- fi
- fo
- fr
- GB
- ge
- gi
- gl
- gr
- sa
- hu
- ie
- il
- is
- bunu
- kw
- kz
- lb
- li
- lt
- lu
- lv
- mc
- md
- ben
- mk
- mr
- mt
- mu
- nl
- hayır
- pl
- pt
- ro
- rs
- sa
- s
- si
- mürekkep
- sm
- tn
- tr
- vg

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:

- İşlev Func_iban desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

Yok


## <a name="international-classification-of-diseases-icd-10-cm"></a>Ulusal hukuk sınıflandırması (ICD-10-CM)

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Anahtar Sözcük

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Bir başka Dictionary_icd_10_updated anahtar sözcük bulunur.
- Farklı bir Dictionary_icd_10_codes anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Güncelleştirilmiş bir Dictionary_icd_10_ anahtar sözcük bulunur.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

### <a name="keywords"></a>Anahtar Sözcükler

Uluslararası Hastalık Sınıflandırması, Onuncu Düzeltme, Klinik Değişiklik [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604)'ye dayalı olan, Dictionary_icd_10_updated anahtar sözcük sözlüğünden herhangi bir terim. Bu tür, sigorta kodlarını değil, yalnızca terimi aramaz.

Uluslararası Hastalık Sınıflandırması, Onuncu Düzeltme, Klinik Değişiklik [(ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604)'ye dayalı olan Dictionary_icd_10_codes anahtar sözcük sözlüğünden herhangi bir terim. Bu tür açıklamayı değil, yalnızca sigorta kodlarını aramaz.


## <a name="international-classification-of-diseases-icd-9-cm"></a>Uluslararası hastalık sınıflandırması (ICD-9-CM)

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Anahtar Sözcük

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Bir başka Dictionary_icd_9_updated anahtar sözcük bulunur.
- Anahtar sözcük Dictionary_icd_9_codes bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Bir başka Dictionary_icd_9_updated anahtar sözcük bulunur.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

Uluslararası Hastalık Sınıflandırması,Dokuzuncu Düzeltme, Klinik Değişiklik [(ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605)'yi temel alan Dictionary_icd_9_updated anahtar sözcük sözlüğünden herhangi bir terim. Bu tür, sigorta kodlarını değil, yalnızca terimi aramaz.

Uluslararası Teklif Sınıflandırması,Dokuzuncu Düzeltme, Klinik Değişiklik [(ICD-9-CM)'](https://go.microsoft.com/fwlink/?linkid=852605)yi temel alan Dictionary_icd_9_codes anahtar sözcük sözlüğünden herhangi bir terim. Bu tür açıklamayı değil, yalnızca sigorta kodlarını aramaz.

## <a name="ip-address"></a>IP adresi

### <a name="format"></a>Biçim

#### <a name="ipv4"></a>IPv4:
IPv4 adreslerinin biçimlendirilmiş (nokta) ve biçimlendirilmemiş (nokta yok) sürümlerini hesap eden karmaşık desen

#### <a name="ipv6"></a>IPv6:
Biçimlendirilmiş IPv6 sayılarını (iki nokta üst üste içeren) hesaba katan karmaşık desen

### <a name="pattern"></a>Desen

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

IPv6 için, DLP ilkesi bu tür hassas bilgileri 300 karakter yakınlıkta algılandığında yüksek güvene sahip olmalıdır:
- Normal ifade Regex_ipv6_address desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_ipaddress anahtar sözcük bulunamıyor.

IPv4 için, DLP ilkesi 300 karakter yakınlık içinde olursa, bu tür hassas bilgiler algılandığından büyük güven verir:
- Normal ifade Regex_ipv4_address desene eşleşen içeriği bulur.
- Bir arama Keyword_ipaddress anahtar sözcüğü bulunur.

IPv6 için, DLP ilkesi bu tür hassas bilgileri 300 karakter yakınlıkta algılandığında yüksek güvene sahip olmalıdır:
- Normal ifade Regex_ipv6_address desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_ipaddress anahtar sözcük bulunamıyor.

```xml
    <!-- IP Address --> 
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (Bu anahtar sözcük büyük/harfe duyarlıdır)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת   Bir


## <a name="ip-address-v4"></a>IP Adresi v4

### <a name="format"></a>Biçim

IPv4 adreslerinin biçimlendirilmiş (nokta) ve biçimlendirilmemiş (nokta yok) sürümlerini hesap eden karmaşık desen

### <a name="pattern"></a>Desen


### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene `Regex_ipv4_address` eşleşen içerik bulur.
- Anahtar sözcük `Keyword_ipaddress` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_ipv4_address` eşleşen içerik bulur.


```xml
      <!-- IP Address v4--> 
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (büyük/büyük/harfe duyarlı)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת   Bir


## <a name="ip-address-v6"></a>IP Adresi v6

### <a name="format"></a>Biçim

Biçimlendirilmiş IPv6 sayılarını (iki nokta üst üste içeren) hesaba katan karmaşık desen

### <a name="pattern"></a>Desen


### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene `Regex_ipv6_address` eşleşen içerik bulur.
- Anahtar sözcük `Keyword_ipaddress` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_ipv6_address` eşleşen içerik bulur.


```xml
      <!-- IP Address v6-->
      <Entity id="3f691089-7413-4926-ab3b-3c5ea8a1c17e" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv6_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv6_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (büyük/büyük/harfe duyarlı)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת   Bir


## <a name="ireland-drivers-license-number"></a>İrlanda sürücü lisans numarası

### <a name="format"></a>Biçim

Altı basamaklı, ardından dört harf

### <a name="pattern"></a>Desen

Altı basamak ve dört harf:

- Altı basamak
- Dört harf (büyük/küçük harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:

- Normal ifade desene  `Regex_ireland_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_ireland_eu_driver's_license_number` bulunur.

```xml
      <!-- Ireland Driver's License Number -->
      <Entity id="e01bccd9-eb4d-414f-ace1-e9b6a4c4a2ca" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_ireland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver's_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>İrlanda pasaport numarası

### <a name="format"></a>Biçim

İki harf veya rakam, ardından boşluk veya sınırlayıcı yokken yedi basamak

### <a name="pattern"></a>Desen

İki harf veya rakam, ardından yedi basamak:

- İki rakam veya harf (büyük/küçük harfe duyarlı değildir)
- Yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_ireland_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` bulunur.
- Normal ifade `Regex_ireland_eu_passport_date` , tarihi AAAA/AAA YYYY (Örnek - 01 BEA/MAY 1988) `Keywords_eu_passport_date` biçiminde veya bir anahtar sözcük bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_ireland_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_ireland_eu_passport_number` bulunur.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="ireland-personal-public-service-pps-number"></a>İrlanda kişisel genel hizmet (PPS) numarası

### <a name="format"></a>Biçim

Eski biçim (31 Aralık 2012'ye kadar):
- Yedi rakam ve ardından 1-2 harf

Yeni biçim (1 Ocak 2013 ve sonrası):
- Yedi basamaklı, ardından iki harf

### <a name="pattern"></a>Desen

Eski biçim (31 Aralık 2012'ye kadar):
- yedi basamak
- bir ile iki harf arasında (büyük/küçük harfe duyarlı değildir)

Yeni biçim (1 Ocak 2013 ve sonrası):
- yedi basamak
- alfabetik bir onay rakamı olan harf (büyük/küçük harfe duyarlı değildir)
- A-I aralığında veya "W" aralığında isteğe bağlı bir harf

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_ireland_pps desene eşleşen içeriği bulur.
- Bir başka Keywords_ireland_eu_national_id_card anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_ireland_pps desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- istemci kimlik hizmeti
- kimlik numarası
- kişisel kimlik numarası
- kişisel genel hizmet numarası
- kişisel hizmet no
- phephebruta seirbhíse poiblí
- pps no
- pps numarası
- pps num
- pps hizmeti no
- ppsn
- ppsno #
- ppsno
- psp
- genel hizmet no
- publicserviceno #
- publicserviceno
- gelir ve sosyal sigorta numarası
- rsi no
- rsi numarası
- rsin
- seirbhís aitheantais istemcisi
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phephefenta
- uimhir phephepheirbhíse poiblí
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="ireland-physical-addresses"></a>İrlanda fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, İrlanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="israel-bank-account-number"></a>İsrail banka hesap numarası

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:
- İki basamak
- Tire
- üç basamak
- Tire
- sekiz basamak

Biçimlendirilmemiş:
- Birbirini arda 13 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_israel_bank_account_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_israel_bank_account_number bulunur.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Banka Hesap Numarası
- Banka Hesabı
- Hesap Numarası
- מספר חשבון בנק


## <a name="israel-national-identification-number"></a>İsrail ulusal kimlik numarası

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

art arda dokuz basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_israeli_national_id_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_Israel_National_ID anahtar sözcük bulunur.
- Denetimli denetimler geçer.

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

-   מספר זהות
-   מספר זיה וי
-   מספר זיהוי ישר אלי      
-   זהותישר אלית
-   هو ية اسرائيل ية عدد
-   هوية إسرائ يلية
-   رقم الهوية
-   عدد هوية فريدة من نوعها
-   kimliksayı #
-   kimlik numarası
-   kimlik hayır        
-   kimliksayı #
-   kimlik numarası
-   İsrailidentitynumber       
-   kişisel kimlik
-   benzersiz kimlik  


## <a name="italy-drivers-license-number"></a>İtalya sürücü lisans numarası

Bu tür varlık AB'nin Lisans Numarası hassas bilgi türüne dahildir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

10 harf ve rakam birleşimi

### <a name="pattern"></a>Desen

10 harf ve rakam birleşimi:
- tek harf (büyük/harfe duyarlı değildir)
- "A" veya "V" harfi (büyük/küçük harfe duyarlı değildir)
- yedi basamak
- tek harf (büyük/harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene `Regex_italy_drivers_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya `Keywords_eu_driver's_license_number` `Keyword_italy_drivers_license_number` bulunur.

```xml
    <!-- Italy Driver's license Number -->
    <Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keyword_italy_drivers_license_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- sayısız di patent
- patente di guida
- patente guida
- patenti di guida
- patenti guida


## <a name="italy-fiscal-code"></a>İtalya mali kodu
Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

belirtilen desende harf ve basamakların 16 karakterlik bir bileşimi

### <a name="pattern"></a>Desen

Harf ve basamakların 16 karakterlik birleşimi:
- Aile adı'nın ilk üç ssonantine karşılık gelen üç harf
- Adın ilk, üçüncü ve dördüncü consonantlarına karşılık gelen üç harf
- Doğum yılı son rakamlarına karşılık gelen iki basamak
- Doğum ayındaki harfe karşılık gelen tek harf; harfler alfabetik sırada kullanılır, ama yalnızca A - E, H, L, M, P, R - T harfleri kullanılır (dolayısıyla, Ocak A ve Ekim R'ye karşılıktır)
- Cinsiyetler arasında ayrım yapmak için doğum günü ile doğum günü arasında karşılık gelen iki basamak, kadınlar için doğum günü 40'a eklenir
- Kişinin doğum tarihine özgü alan koduna karşılık gelen dört basamak (ülke çapında kodlar yabancı ülkeler için kullanılır)
- tek parity basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_italy_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_italy_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_italy_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- mali dönemler
- mali dönemler
- codice id personale
- codice personale
- mali kod
- numero certificific personale
- numero di identificazione fiscale
- numero id personale
- çok kişisel
- kişisel sertifika numarası
- kişisel kod
- kişisel kimlik kodu
- kişisel kimlik numarası
- personalcodeno #
- vergi kodu
- vergi no
- vergi numarası yok
- vergi numarası
- vergi kimlik numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="italy-passport-number"></a>İtalya pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı yok, iki harf veya rakam, ardından da yedi basamak

### <a name="pattern"></a>Desen

İki harf veya rakam, ardından yedi basamak:

- İki basamak veya harf (büyük/küçük harfe duyarlı değildir)
- yedi basamak

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_italy_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` bulunur.
- Normal ifade `Regex_italy_eu_passport_date` , tarihi AAAA/AAA YYYY (Örnek - 01 GEN/OCA 1988) `Keywords_eu_passport_date` biçiminde veya bir anahtar sözcük bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_italy_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_italy_eu_passport_number` bulunur.

```xml
      <!-- Italy Passport Number -->
      <Entity id="39811019-4750-445f-b26d-4c0e6c431544" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_italy_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="italy-physical-addresses"></a>İtalya fiziksel adresleri

Buundled adlı varlık, İtalya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="italy-value-added-tax-number"></a>İtalya değeri eklenen vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcılarla 13 karakter alfasayısal desen

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcılarla 13 karakter alfasayısal desen:

- I veya i
- T veya t
- isteğe bağlı boşluk, nokta, kısa çizgi veya virgül
- 11 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_italy_value_added_tax_number desene eşleşen içeriği bulur.
- Farklı bir Keywords_italy_value_added_tax_number anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_italy_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- Italy Value Added Tax -->
      <Entity id="26a8cc07-2283-4a2a-ab1d-4ab643c4c67f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
          <Match idRef="Keywords_italy_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- kdv numarası
- kdv yok
- kdv #
- iva
- iva #


## <a name="japan-bank-account-number"></a>Japonya banka hesap numarası

### <a name="format"></a>Biçim

yedi veya sekiz basamak

### <a name="pattern"></a>Desen

banka hesabı numarası:
- yedi veya sekiz basamak
- banka hesabı şube kodu:
- dört basamak
- boşluk veya kısa çizgi (isteğe bağlı)
- üç basamak

Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_jp_bank_account desene eşleşen içeriği bulur.
- Farklı bir Keyword_jp_bank_account anahtar sözcük bulunur.
- Aşağıdakilerden biri doğrudur:
- İşlev Func_jp_bank_account_branch_code desene eşleşen içeriği bulur.
- Bir başka Keyword_jp_bank_branch_code anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_jp_bank_account desene eşleşen içeriği bulur.
- Farklı bir Keyword_jp_bank_account anahtar sözcük bulunur.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Hesap Numarasını Denetleme
- Hesabı Denetleme
- Hesabı Denetleme #
- Acct Numarasını Denetleme
- Acct Denetimi #
- Acct No denetlendi.
- Hesap No denetlendi.
- Banka Hesap Numarası
- Banka Hesabı
- Banka Hesabı #
- Banka Tahakkuk Numarası
- Banka Acct #
- Banka Acct No.
- Banka Hesabı No.
- Tasarruf Hesap Numarası
- Tasarruf Hesabı
- Tasarruf Hesabı #
- Tasarruf Tasarruf Sayısı
- Tasarruf Tasarrufları #
- Tasarruf Tasarruf Tasarrufları Hayır.
- Tasarruf Hesabı Hayır.
- Borç Hesap Numarası
- Borç Hesabı
- Borç Hesabı #
- Borç Tahakkuk Numarası
- Borç Hesabı #
- Borç Bakiyesi No.
- Borç Hesabı No.
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号

## <a name="japan-drivers-license-number"></a>Japonya sürücü lisans numarası

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

Art arda 12 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_jp_drivers_license_number desene eşleşen içeriği bulur.
- Bir başka Keyword_jp_drivers_license_number anahtar sözcük bulunur.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- driver'slicense
- driverslicenses
- sürücü dilimleri
- driverlicenses
- dl #
- dls #
- lic #
- lics #
- 運転免許証
- 運転免許
- 免許証
- 免許
- 運転免許証番号
- 運転免許番号
- 免許証番号
- 免許番号
- 運転免許証ナンバー
- 運転免許ナンバー
- 免許証ナンバー
- 運転免許証no
- 運転免許no
- 免許証no
- 免許no
- 運転経歴証明書番号
- 運転経歴証明書
- 運転免許証No.
- 運転免許No.
- 免許証No.
- 免許No.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #


## <a name="japan-my-number---corporate"></a>Japonya Numaram - Kurumsal

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 basamaklı sayı

### <a name="pattern"></a>Desen

13 basamaklı sayı:

- bir ile dokuz basamaktan bir basamak
- 12 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_japanese_my_number_corporate desene eşleşen içeriği bulur.
- Farklı bir Keywords_japanese_my_number_corporate anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_japanese_my_number_corporate desene eşleşen içeriği bulur.

```xml
      <!-- Japanese My Number – Corporate -->
      <Entity id="9e0eaf79-ff20-4ffb-b3e4-e7368d5db6ff" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
          <Match idRef="Keywords_japanese_my_number_corporate" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_japan_my_number_corporate"></a>Keyword_japan_my_number_corporate

- şirket numarası
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書


## <a name="japan-my-number---personal"></a>Japonya Numaram - Kişisel

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

12 basamaklı sayı

### <a name="pattern"></a>Desen

12 basamaklı sayı:

- dört basamak
- isteğe bağlı bir boşluk, nokta veya kısa çizgi
- dört basamak
- isteğe bağlı bir boşluk, nokta veya kısa çizgi
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_japanese_my_number_personal desene eşleşen içeriği bulur.
- Bir arama Keywords_japanese_my_number_personal anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_japanese_my_number_personal desene eşleşen içeriği bulur.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- numaram
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード


## <a name="japan-passport-number"></a>Japonya pasaport numarası

### <a name="format"></a>Biçim

İki harf ve ardından da yedi basamak

### <a name="pattern"></a>Desen

İki harf (büyük/küçük harfe duyarlı değil) ve ardından yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_jp_passport desene eşleşen içeriği bulur.
- Farklı bir Keyword_jp_passport anahtar sözcük bulunur.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Pasaport
- Pasaport Numarası
- Pasaport No.
- Pasaport #
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー


## <a name="japan-residence-card-number"></a>Japonya İkamet kartı numarası

### <a name="format"></a>Biçim

12 harf ve rakam

### <a name="pattern"></a>Desen

12 harf ve rakam:
- İki harf (büyük/küçük harfe duyarlı değildir)
- sekiz basamak
- İki harf (büyük/küçük harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_jp_residence_card_number desene eşleşen içeriği bulur.
- Bir başka Keyword_jp_residence_card_number anahtar sözcük bulunur.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- İkamet kartı numarası
- İkamet kartı hayır
- İkamet kartı #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Japonya'daki yerleşik kayıt numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

Birbirini arda 11 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_jp_resident_registration_number desene eşleşen içeriği bulur.
- Arama sözcüğünden Keyword_jp_resident_registration_number anahtar sözcük bulunur.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Yerleşik Kayıt Numarası
- Bölge Sakinlerinin Temel Kayıt Defteri Numarası
- Yerleşik Kayıt No.
- Yerleşik Kayıt No.
- Bölge Sakinlerinin Temel Kayıt Defteri No.
- Temel Yerleşik Kayıt No.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証


## <a name="japan-social-insurance-number-sin"></a>Japonya sosyal sigorta numarası (SN)

### <a name="format"></a>Biçim

7-12 basamak

### <a name="pattern"></a>Desen

7-12 basamak:
- dört basamak
- kısa çizgi (isteğe bağlı)
- altı basamak VEYA
- 7-12 art arda basamaklar

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_jp_sin desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_jp_sin bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_jp_sin_pre_1997 desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_jp_sin bulunur.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Sosyal Sigorta No.
- Sosyal Sigorta Num
- Sosyal Sigorta Numarası
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社İpnot保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号


## <a name="lab-test-terms"></a>Laboratuvar test koşulları

Bu şaşırtıcı olmayan adlandırılmış varlık, Laboratuvar testleri ile ilgili, *C-doğrualt gibi terimleri algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="latvia-drivers-license-number"></a>Letonya sürücüsünün lisans numarası

### <a name="format"></a>Biçim

Üç harf, ardından altı basamak

### <a name="pattern"></a>Desen

üç harf ve altı basamak:

- üç harf (büyük/küçük harfe duyarlı değildir)
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_latvia_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_latvia_eu_driver's_license_number` bulunur.

```xml
      <!-- Latvia Driver's License Number -->
      <Entity id="ec996de0-30f2-46b1-b192-4d2ff8805fa7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_latvia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver'S_LICENSE_NUMBER

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība


## <a name="latvia-passport-number"></a>Letonya pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı yok, iki harf veya rakam, ardından da yedi basamak

### <a name="pattern"></a>Desen

İki harf veya rakam, ardından yedi basamak:

- İki basamak veya harf (büyük/küçük harfe duyarlı değildir)
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_latvia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_latvia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_latvia_eu_passport_number` bulunur.

```xml
      <!-- Latvia Passport Number -->
      <Entity id="23ae25ec-cc28-421b-b77a-3054eadf1ede" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="latvia-personal-code"></a>Letonya kişisel kodu

### <a name="format"></a>Biçim

11 basamak ve isteğe bağlı kısa çizgi

### <a name="pattern"></a>Desen

Eski biçim

11 rakam ve kısa çizgi:

- Doğum tarihine karşılık gelen altı basamak (DDMMY)
- kısa çizgi
- doğum yüzyılı için bir basamak ("19. yüzyıl için 0", 20. yüzyıl için "1", 21. yüzyıl için "2" )
- rastgele oluşturulan dört basamak

Yeni biçim

11 basamak

- İki basamaklı "32"
- Dokuz rakam

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev veya  `Func_latvia_eu_national_id_card` kayıtex, `Regex_latvia_eu_national_id_card_new_format` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_latvia_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev veya  `Func_latvia_eu_national_id_card` kayıtex, `Regex_latvia_eu_national_id_card_new_format` desene eşleşen içeriği bulur.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- yönetim numarası
- alē nē
- doğum numarası
- hizmet numarası
- hukuk numarası
- elektronik nüfus numarası
- elektronik numara
- mali kod
- sağlık kullanıcı numarası
- id #
- id-code
- kimlik numarası
- identifikācijas numurs
- id-number
- tek bir numara
- latvija alva
- nacionālais id
- ulusal kimlik
- ulusal tanımlayıcı numara
- ulusal kimlik numarası
- ulusal sigorta numarası
- ulusal kayıt numarası
- nodokļa numurs
- nodokļu kimliği
- nodokļu identifikācija numurs
- kişisel sertifika numarası
- kişisel kod
- kişisel kimlik kodu
- kişisel kimlik numarası
- kişisel kimlik kodu
- kişisel tanımlayıcı
- kişisel kimlik numarası
- kişisel numara
- kişisel sayısal kod
- personalcodeno #
- personas kods
- nüfus tanımlama kodu
- genel hizmet numarası
- kayıt numarası
- gelir numarası
- sosyal sigorta numarası
- sosyal güvenlik numarası
- eyalet vergi kodu
- vergi dosyası numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- 2010'un numarası


## <a name="latvia-physical-addresses"></a>Letonya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Letonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="liechtenstein-physical-addresses"></a>Liechtenstein fiziksel adresleri

Buundled adlandırılmış varlık, Liechtenstein'dan gelen fiziksel adresle ilgili desenler algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir. 

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="lifestyles-that-relate-to-medical-conditions"></a>Tıbbi koşullarla ilgili yaşam tarzları

Bu bakıla sahip olmayan bu varlık, yaşam biçimiyle ilgili, sadece tinlik gibi tıbbi bir koşula neden olan terimleri *algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="lithuania-drivers-license-number"></a>Litvanya sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_lithuania_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_lithuania_eu_driver's_license_number` bulunur.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver's_license_number

- vairuotojo pažym bujimas
- vairuotojo pažym  birjimo numeris
- vairuotojo pa birayijimo numeriai


## <a name="lithuania-personal-code"></a>Litvanya kişisel kodu

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 11 basamak

### <a name="pattern"></a>Desen

Boşluk ve sınırlayıcı olmayan 11 basamak:

- kişinin cinsiyetine ve doğum yüzyılı ile ilgili bir basamak (1-6)
- Doğum tarihine karşılık gelen altı basamak (YYAAA)
- Doğum tarihin seri numarasına karşılık gelen üç basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_lithuania_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_lithuania_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_lithuania_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- hizmet numarası
- mokesčių kimliği
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių sayısı
- ulusal kimlik numarası
- kişisel kod
- kişisel sayısal kod
- piliečio paslaugos numeris
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- benzersiz tanımlama numarası
- benzersiz kimlik numarası
- uniqueidentityno #


## <a name="lithuania-physical-addresses"></a>Litvanya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Litvanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="lithuania-passport-number"></a>Litvanya pasaport numarası

### <a name="format"></a>Biçim

sekiz basamaklı veya boşluk veya sınırlayıcısız harfler

### <a name="pattern"></a>Desen

sekiz basamaklı veya harfler (büyük/küçük harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_lithuania_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date3` tarihi DD MM YYYY biçiminde veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur biçimde bulur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_lithuania_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_lithuania_eu_passport_number` bulunur.

```xml
      <!-- Lithuania Passport Number -->
      <Entity id="1b79900f-047b-4c3f-846f-7d73b5534bce" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- amerika numeris
- olarak sayımeriai
- olarak nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="luxemburg-drivers-license-number"></a>Luxemburg sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan altı basamak

### <a name="pattern"></a>Desen

altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_luxemburg_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_luxemburg_eu_driver's_license_number` bulunur.

```xml
      <!-- Luxemburg Driver's License Number -->
      <Entity id="89daf717-1544-4860-9a2e-fc9166dd8852" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_luxemburg_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver's_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Luxemburg ulusal kimlik numarası (doğal kişiler)

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı yok 13 basamak

### <a name="pattern"></a>Desen

13 basamak:

- 11 basamak
- iki onay rakamı

### <a name="checksum"></a>Checksum

evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_luxemburg_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_luxemburg_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_luxemburg_eu_tax_file_number` desene eşleşen içeriği bulur.


```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- kimlik personeli
- idpersonnelle #
- idpersonnelle
- tek tek kod
- bireysel kimlik
- bireysel kimlik
- bireysel kimlik
- numéro d'identification personel
- kişisel kimlik
- kişisel kimlik
- kişisel kimlik
- personalidno #
- kişiselsayı #
- persönliche identifikationsnummer
- benzersiz kimlik
- benzersiz kimlik
- uniqueidkey #


## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Luxemburg ulusal kimlik numarası (doğal olmayan kişiler)

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak

- İki basamak
- isteğe bağlı bir boşluk
- üç basamak
- isteğe bağlı bir boşluk
- üç basamak
- isteğe bağlı bir boşluk
- İki basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_luxemburg_eu_tax_file_number_non_natural` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_luxemburg_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_luxemburg_eu_tax_file_number_non_natural` desene eşleşen içeriği bulur.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain non
- étain #
- identifiant d'impôt
- Luxembourg tax identifikatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourge tanıtıcı
- numéro d'identification fiscale
- sosyal güvenlik
- sounglunterstützung
- sozialversécherung
- sozialversicherungsausweis
- s steier kimliği
- steier identifikatiounsnummer
- s steier nummer
- suer kimliği
- steueridentifikationsnummer
- steuernummer
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- zinn #
- zinn
- zinnzahl


## <a name="luxemburg-passport-number"></a>Luxemburg Passport numarası

### <a name="format"></a>Biçim

sekiz basamaklı veya boşluk veya sınırlayıcısız harfler

### <a name="pattern"></a>Desen

sekiz basamaklı veya harfler (büyük/küçük harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_luxemburg_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date3` tarihi DD MM YYYY biçiminde veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur biçimde bulur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_luxemburg_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_luxemburg_eu_passport_number` bulunur.

```xml
      <!-- Luxemburg Passport Number -->
      <Entity id="81d5c027-bed9-4421-91a0-3b2e55b3eb85" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luxembourg pass
- luxembourg passeport
- Lüksemburg Pasaport
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- net'i geç
- nr geçiş
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="luxemburg-physical-addresses"></a>Luxemburg fiziksel adresleri

Buundled adlı varlık, Luxemburg'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="malaysia-identification-card-number"></a>Malezya kimlik kartı numarası

### <a name="format"></a>Biçim

İsteğe bağlı kısa çizgi içeren 12 basamak

### <a name="pattern"></a>Desen

12 basamak:
- Doğum tarihi olan YYAAAA biçiminde altı basamak
- Tire (isteğe bağlı)
- İki harfli doğum yeri kodu
- Tire (isteğe bağlı)
- üç rastgele basamak
- tek basamaklı cinsiyet kodu

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_malaysia_id_card_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_malaysia_id_card_number bulunur.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- dijital uygulama kartı
- i/c
- i/c hayır
- ic
- ic no
- kimlik kartı
- kimlik Kartı
- kimlik kartı
- k/p
- k/p hayır
- olarak tüm gün iş bire bir gün devam ediyor
- aplikasi digital
- olarak pengenalan Malaysia
- kp
- kp hayır
- mykad
- mykas
- mykid
- nis
- mytentera
- Malezya kimlik kartı
- Malezya kimlik kartı
- nric
- kişisel kimlik kartı


## <a name="malta-drivers-license-number"></a>Malta sürücü lisans numarası

### <a name="format"></a>Biçim

Belirtilen desende iki karakter ve altı basamak birleşimi

### <a name="pattern"></a>Desen

iki karakter ve altı basamak birleşimi:

- İki karakter (büyük/küçük harfe duyarlı değil, rakam veya harf)
- boşluk (isteğe bağlı)
- üç basamak
- boşluk (isteğe bağlı)
- üç basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_malta_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_malta_eu_driver's_license_number` bulunur.

```xml
      <!-- Malta Driver's License Number -->
      <Entity id="a3bdaa4a-8371-4735-8fa5-56ee0fb4afc4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_malta_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver's_license_number

- liċenzja tas-bire birQan
- liċenzji tas-wieq


## <a name="malta-identity-card-number"></a>Malta kimlik kartı numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Yedi basamaklı ve ardından bir harf

### <a name="pattern"></a>Desen

Yedi basamaklı ve ardından bir harf:

- yedi basamak
- "M, G, A, P, L, H, B, Z" (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Checksum

Uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_malta_eu_national_id_card` eşleşen içerik bulur.
- Anahtar sözcük  `Keywords_malta_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Normal ifade desene  `Regex_malta_eu_national_id_card` eşleşen içerik bulur.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- hizmet numarası
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-zzzz taċ-ċittadin
- numru tat-taxxa
- kişisel sayısal kod
- benzersiz tanımlama numarası
- benzersiz kimlik numarası
- uniqueidentityno #


## <a name="malta-passport-number"></a>Malta pasaport numarası

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı olmayan yedi basamak

### <a name="pattern"></a>Desen

yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_malta_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` bulunur.
- Anahtar sözcük `Keywords_eu_passport_date` bulundu

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_malta_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_malta_eu_passport_number` bulunur.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="malta-physical-addresses"></a>Malta fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık Malta'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="malta-tax-identification-number"></a>Malta vergi tanımlama numarası

### <a name="format"></a>Biçim

Maltese ulusalları için:
- Belirtilen desende yedi basamak ve bir harf

Maltese dışı milliler ve Maltese varlıkları:
- dokuz basamak

### <a name="pattern"></a>Desen

Maltese ulusalları: yedi basamak ve bir harf

- yedi basamak
- tek harf (büyük/harfe duyarlı değildir)

Maltese dışı milliler ve Maltese varlıkları: dokuz basamak

- dokuz basamak

### <a name="checksum"></a>Checksum

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtex,  `Regex_malta_eu_tax_file_number`  desene `Regex_malta_eu_tax_file_number_non_maltese_national` eşleşen içeriği bulur veya bulur.
- Anahtar sözcük  `Keywords_malta_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- Kayıtex,  `Regex_malta_eu_tax_file_number` desene `Regex_malta_eu_tax_file_number_non_maltese_national` eşleşen içeriği bulur veya bulur.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- hizmet numarası
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-zzzz taċ-ċittadin
- numru tat-taxxa
- kişisel sayısal kod
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- benzersiz tanımlama numarası
- benzersiz kimlik numarası
- uniqueidentityno #

## <a name="medical-specialities"></a>Tıbbi uzmanlıklar

Bu bakıla sahip olmayan bu varlık, tıbbi uzmanlık alanıyla ilgili koşulları (örneğin, *şüpheli) algılar*.  Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek

## <a name="medicare-beneficiary-identifier-mbi-card"></a>Medicare Yardım Tanımlayıcı (MBI) kartı

### <a name="format"></a>Biçim

11 karakter alfasayısal desen

### <a name="pattern"></a>Desen

- 1 ile 9 arasında bir basamak
- S, L, O, I, B, Z dışında bir harf
- S, L, O, I, B, Z hariç bir rakam veya harf
- bir rakam
- isteğe bağlı Tire
- S, L, O, I, B, Z dışında bir harf
- S, L, O, I, B, Z hariç bir rakam veya harf
- bir rakam
- isteğe bağlı Tire
- S, L, O, I, B, Z hariç iki harf
- İki basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_mbi_card` eşleşen içerik bulur.
- Anahtar sözcük  `Keyword_mbi_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_mbi_card` eşleşen içerik bulur.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- akare hak sahibi #
- medicare hak sahibi tanımlayıcı
- alan hak sahibi no
- hhare hak sahibi sayı
- akare hak sahibi #


## <a name="mexico-unique-population-registry-code-curp"></a>Mexico Unique Population Registry Code (CURP)

### <a name="format"></a>Biçim

18 karakter alfasayısal desen

### <a name="pattern"></a>Desen

- dört harf (büyük/küçük harfe duyarlı değil)
- Geçerli bir tarihi gösteren altı basamak
- a letter - H/s veya M/m
- Geçerli bir Meksika eyalet kodunu gösteren iki harf
- üç harf
- bir harf veya rakam
- bir rakam

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_mexico_population_registry_code` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keyword_mexico_population_registry_code` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_mexico_population_registry_code` desene eşleşen içeriği bulur.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Alkışve Única de Registro de Población
- Alkışve Unica de Registro de Poblacion
- Benzersiz Nüfus Kayıt Defteri Kodu 
- benzersiz nüfus kodu
- CURP
- Kişisel Kimlik
- Benzersiz Kimlik
- personalid
- kişiselsayı
- uniqueidkey
- benzersizsayı
- cupve única
- alkışve unica
- alkışve kişisel Identidad
- kişisel Identidad Alkış
- AlkışveÚnica
- alkışveunica
- yalçınIdentidad


## <a name="netherlands-citizens-service-bsn-number"></a>Hollanda genel hizmet numarası (BSN)

### <a name="format"></a>Biçim

isteğe bağlı boşluklar içeren sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

sekiz-dokuz basamak:
- üç basamak
- boşluk (isteğe bağlı)
- üç basamak
- boşluk (isteğe bağlı)
- iki-üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_netherlands_bsn desene eşleşen içeriği bulur.
- Bir başka Keyword_netherlands_bsn anahtar sözcük bulunur.
- Denetimli denetimler geçer.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- servicenummer
- hizmet numarası
- kişi numarası
- kişisel numara
- kişisel sayısal kod
- ilgili kişi numarası
- persoonlijk nummer
- persoonlijke numerieke kodu
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- sosyal-mali numara
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- benzersiz tanımlama numarası
- benzersiz kimlik numarası
- uniqueidentityno #


## <a name="netherlands-drivers-license-number"></a>Hollanda sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_netherlands_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_netherlands_eu_driver's_license_number` bulunur.

```xml
      <!-- Netherlands Driver's License Number -->
      <Entity id="6247fbea-ab80-4be5-8233-308b7c031401" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_netherlands_eu_driver's_license_number" />
            </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver's_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>Hollanda pasaport numarası

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı yok dokuz harf veya basamak

### <a name="pattern"></a>Desen

dokuz harf veya rakam

### <a name="checksum"></a>Checksum

uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_netherlands_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` bulunur.
- Normal ifade `Regex_netherlands_eu_passport_date` tarihi AAAA/AAA YYYY biçiminde bulur (Örnek - 26 MAA/MAR 2012)

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_netherlands_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_netherlands_eu_passport_number` bulunur.

```xml
      <!-- Netherlands Passport Number -->
      <Entity id="61786727-bafd-45f6-94d9-888d815e228e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Regex_netherlands_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr


## <a name="netherlands-physical-addresses"></a>Hollanda fiziksel adresleri

Buundled adlı varlık, Hollanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="netherlands-tax-identification-number"></a>Hollanda vergi tanımlama numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı olmayan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_netherlands_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_netherlands_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev,  `Func_netherlands_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- hol tümcedenske vergi kimliği
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer insting
- identificatienummer van insting
- impuesto tanımlama numarası
- impuesto sayı
- nederlands her zaman kimlik numarası
- nederlands her şey identificatie
- nederlands her şey identificatienummer
- nederlandsavastingnummer
- nederlandse her zaman identificatie
- Hollanda Vergi Kimliği
- Hollanda Vergi Kimliği
- Hollanda tin
- Hollanda tin'i
- vergi no
- vergi numarası yok
- vergi numarası
- vergi tanımlama tal
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- vergi tal
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="netherlands-value-added-tax-number"></a>Hollanda'nın katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

14 karakter alfasayısal desen

### <a name="pattern"></a>Desen

14 karakterli alfasayısal desen:

- N veya n
- L veya l
- isteğe bağlı boşluk, nokta veya kısa çizgi
- dokuz basamak
- isteğe bağlı boşluk, nokta veya kısa çizgi
- B veya b
- İki basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_netherlands_value_added_tax_number desene eşleşen içeriği bulur.
- Bir başka Keywords_netherlands_value_added_tax_number anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_netherlands_value_added_tax_number desene eşleşen içeriği bulur.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- kdv numarası
- kdv yok
- kdv #
- wearde tafoege tax getal
- btw n bir
- btw-nummer


## <a name="new-zealand-bank-account-number"></a>Yeni Zelanda banka hesap numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcıyla 14 basamaklı - 16 basamaklı desen

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcıyla 14 basamaklı - 16 basamaklı desen:

- İki basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç ile dört basamak arasında
- isteğe bağlı kısa çizgi veya boşluk
- yedi basamak
- isteğe bağlı kısa çizgi veya boşluk
- İki ile üç basamak arasında
- seçenekler kısa çizgi veya boşluk

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_new_zealand_bank_account_number desene eşleşen içeriği bulur.
- Farklı bir Keywords_new_zealand_bank_account_number anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_new_zealand_bank_account_number desene eşleşen içeriği bulur.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- hesap numarası
- banka hesabı
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr


## <a name="new-zealand-drivers-license-number"></a>Yeni Zelanda sürücüsünün lisans numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz karakter alfasayısal desen

### <a name="pattern"></a>Desen

sekiz karakter alfasayısal desen

- iki harf
- altı basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_newzealand_driver_license_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keywords_newzealand_driver_license_number bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_newzealand_driver_license_number desene eşleşen içeriği bulur.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslicence
- driverslicences
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- uluslararası sürüş izni
- uluslararası sürüş izinleri
- nz otomobil birliği
- yeni Zelanda otomobil birliği


## <a name="new-zealand-inland-revenue-number"></a>Yeni Zelanda iç gelir numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

isteğe bağlı sınırlayıcılar ile sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

isteğe bağlı sınırlayıcılar ile sekiz veya dokuz basamak

- iki veya üç basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- üç basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_new_zealand_inland_revenue_number desene eşleşen içeriği bulur.
- Bir arama Keywords_new_zealand_inland_revenue_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_new_zealand_inland_revenue_number desene eşleşen içeriği bulur.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- Hayır.
- ird no #
- nz ird
- yeni Zelanda
- üçüncü numara
- iç gelir numarası


## <a name="new-zealand-ministry-of-health-number"></a>Sağlık numarasıyla ilgili yeni Zelanda

### <a name="format"></a>Biçim

Üç harf ve dört basamak

### <a name="pattern"></a>Desen

- üç harfli (büyük/küçük harfe duyarlı değil) "I" ve "O" dışında
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_new_zealand_ministry_of_health_number desene eşleşen içeriği bulur.
- Bir arama Keyword_nz_terms anahtar sözcüğü bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_new_zealand_ministry_of_health_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Yeni Zelanda
- National Health Index
- NHI #
- National Health Index #


## <a name="new-zealand-physical-addresses"></a>Yeni Zelanda fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Yeni Zelanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="new-zealand-social-welfare-number"></a>Yeni Zelanda sosyal yardım numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

- üç basamak
- isteğe bağlı kısa çizgi
- üç basamak
- isteğe bağlı kısa çizgi
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_newzealand_social_welfare_number desene eşleşen içeriği bulur.
- Farklı bir Keywords_newzealand_social_welfare_number anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_newzealand_social_welfare_number desene eşleşen içeriği bulur.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- sosyal yardım #
- sosyal yardım #
- sosyal yardım No.
- sosyal yardım numarası
- swn #


## <a name="norway-identification-number"></a>Norveç kimlik numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:
- Doğum tarihi olan  DAAAY biçiminde altı basamak
- üç basamaklı tek tek sayı
- iki onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_norway_id_number desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_norway_id_number bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_norway_id_numbe desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Kişisel kimlik numarası
- Norveççe Kimlik Numarası
- Kimlik Numarası
- Kimlik
- Personnummer
- Fødselsnummer


## <a name="norway-physical-addresses"></a>Norveç fiziksel adresleri

Buundled adlı varlık, Norveç'teki fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="philippines-unified-multi-purpose-identification-number"></a>Filipinler birleşik çok amaçlı kimlik numarası

### <a name="format"></a>Biçim

Kısa çizgilerle ayrılmış 12 basamak

### <a name="pattern"></a>Desen

12 basamak:
- dört basamak
- kısa çizgi
- yedi basamak
- kısa çizgi
- bir rakam

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_philippines_unified_id desene eşleşen içeriği bulur.
- Bir başka Keyword_philippines_id anahtar sözcük bulunur.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Birleşik Çok Amaçlı Kimlik
- UMID
- Kimlik Kartı
- Pinag-isang Multi-Layunin Kimliği


## <a name="poland-drivers-license-number"></a>Polonya sürücüsünün lisans numarası

### <a name="format"></a>Biçim

İki eğik çizgi içeren 14 basamak

### <a name="pattern"></a>Desen

14 basamak ve iki eğik çizgi:

- beş basamak
- eğik çizgi
- İki basamak
- eğik çizgi
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_poland_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_poland_eu_driver's_license_number` bulunur.

```xml
      <!-- Poland Driver's License Number -->
      <Entity id="24d51f99-ee9e-4060-a077-cae58cab1ee4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_poland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_poland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver's_license_number

- prawo jazdy
- prawa jazdy


## <a name="poland-identity-card"></a>Polonya kimlik kartı

### <a name="format"></a>Biçim

Üç harf ve altı rakam

### <a name="pattern"></a>Desen

Üç harf (büyük/küçük harfe duyarlı değil) ve ardından altı basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_polish_national_id desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_polish_national_id_passport_number bulunur.
- Denetimli denetimler geçer.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osósty
- Numer dowodu osobistego
- Herwa i numer dowodu osobistego
- Zaman (i nr dowodu osobistego)
- Zamanwa i nr dowodu tośsamości
- Dowód Tośsamości
- dow. işletim sistemi.


## <a name="poland-national-id-pesel"></a>Polonya ulusal kimliği (PESEL)

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

- YYAAAA biçimindeki doğum tarihini temsil eden altı basamak
- dört basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_pesel_identification_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_pesel_identification_number anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_pesel_identification_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
      <!-- Poland National ID (PESEL) -->
      <Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_pesel_identification_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osósty
- dowódos busty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tośsamości narodowej


## <a name="poland-passport-number"></a>Polonya pasaport numarası

Bu hassas bilgi türü varlık, AB Pasaport Numarası duyarlı bilgi türüne dahildir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

İki harf ve yedi basamak

### <a name="pattern"></a>Desen

İki harf (büyük/küçük harfe duyarlı değil) ve ardından yedi basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_polish_passport_number_v2` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` bulunur.
- Anahtar sözcük `Keywords_eu_passport_date` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_polish_passport_number_v2` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keyword_polish_national_passport_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev, `Func_polish_passport_number_v2` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="poland-physical-addresses"></a>Polonya fiziksel adresleri

Buundled adlandırılmış varlık, Polonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="poland-regon-number"></a>Polonya REGON numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

9 basamaklı veya 14 basamaklı sayı

### <a name="pattern"></a>Desen

dokuz basamaklı veya 14 basamaklı sayı:

- dokuz rakam veya
- dokuz basamak
- kısa çizgi
- beş basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_polish_regon_number desene eşleşen içeriği bulur.
- Bir Keywords_polish_regon_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_polish_regon_number desene eşleşen içeriği bulur.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon kimliği
- istatistiksel sayı
- istatistiksel kimlik
- istatistiksel hayır
- regon numarası
- regonid #
- regonno #
- şirket kimliği
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>Polonya vergi tanımlama numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı yok 11 basamak

### <a name="pattern"></a>Desen

11 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_poland_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_poland_eu_tax_file_number` bulunur.


```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podathan
- numeridentyfikacjipodatvir #
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- kdv no #
- kdv no
- kdv yok
- kdv numarası
- kdvid #
- kdvid
- vatno #


## <a name="portugal-citizen-card-number"></a>Portekiz kart numarası

### <a name="format"></a>Biçim

sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_portugal_citizen_card desene eşleşen içeriği bulur.
- Farklı bir Keyword_portugal_citizen_card anahtar sözcük bulunur.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- Kart
- belge numarası
- documento de identificação
- kimlik numarası
- kimlik no
- kimlik numarası
- kimlik kartı hayır
- kimlik kartı numarası
- ulusal kimlik kartı
- nic
- número bi de portugal
- número de identificação civil
- número de identificação mali
- número do documento
- portekiz bi numarası


## <a name="portugal-drivers-license-number"></a>Portekiz sürücü lisans numarası

### <a name="format"></a>Biçim

two patterns - two letters followed followed 5-8 digits with special characters

### <a name="pattern"></a>Desen

Desen 1: İki harf, ardından özel karakterlerle 5/6:
- İki harf (büyük/küçük harfe duyarlı değildir)
- Kısa çizgi
- Beş veya Altı basamak
- Boşluk
- Bir rakam

Desen 2: Bir harf ve ardından özel karakterlerle 6/8 basamak:
- Tek harf (büyük/büyük/harfe duyarlı değildir)
- Kısa çizgi
- Altı veya sekiz basamak
- Boşluk
- Bir rakam


### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_portugal_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_portugal_eu_driver's_license_number` bulunur.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver's_license_number

- cart de motorista
- cartista motorista
- cartaş de habilitação
- cartlis habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução


## <a name="portugal-passport-number"></a>Portekiz pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı yok olarak altı basamak

### <a name="pattern"></a>Desen

bir harf ve ardından altı basamak:

- tek harf (büyük/harfe duyarlı değildir)
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_portugal_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_portugal_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_portugal_eu_passport_number` bulunur.

```xml
      <!-- Portugal Passport Number -->
      <Entity id="080a52fd-a7bc-431e-b54d-51f08f59db11" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- Portekizce pasaport
- portekizce geçiş
- Portekizce geçiş
- passaporte nº
- passeport nº
- números de passaporte
- Portekizce pasaport
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="portugal-physical-addresses"></a>Portekiz fiziksel adresleri

Buundled adlandırılmış varlık, Portekiz'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="portugal-tax-identification-number"></a>Portekiz vergi tanımlama numarası

### <a name="format"></a>Biçim

İsteğe bağlı boşluklar olan dokuz basamak

### <a name="pattern"></a>Desen

- üç basamak
- isteğe bağlı bir boşluk
- üç basamak
- isteğe bağlı bir boşluk
- üç basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_portugal_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_portugal_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev,  `Func_portugal_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- cpf #
- cpf
- nif #
- nif
- número de identificação fisca
- çok sayıda mali
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="romania-drivers-license-number"></a>Romanya sürücü lisans numarası

### <a name="format"></a>Biçim

bir karakter ve ardından sekiz basamak

### <a name="pattern"></a>Desen

bir karakter ve ardından sekiz basamak:
- tek harf (büyük/büyük/harfe duyarlı değildir) veya basamak
- sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_romania_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_romania_eu_driver's_license_number` bulunur.

```xml
      <!-- Romania Driver's License Number -->
      <Entity id="b5511ace-2fd8-4ae4-b6fc-c7c6e4689e3c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_romania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver's_license_number

- permis de conduisere
- permisului de condurine
- permisului conduisere
- permisele de conduazie
- permisele conduazie
- permis conduisere


## <a name="romania-passport-number"></a>Romanya pasaport numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

sekiz veya dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_romania_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` bulunur.
- Normal ifade `Regex_romania_eu_passport_date` , tarihi AAAA/AAA YY (Örnek- 01 ŞUB/ŞUB 10) `Keywords_eu_passport_date` biçiminde veya bir anahtar sözcük bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_romania_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_romania_eu_passport_number` bulunur.

```xml
      <!-- Romania Passport Number -->
      <Entity id="5d31b90c-7fe2-4a76-a14b-767b8fd19d6c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_romania_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numrul parul parulportului numarul bului numerele paışaportului Paışaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="romania-personal-numeric-code-cnp"></a>Romanya kişisel sayısal kodu (CNP)

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 13 basamak

### <a name="pattern"></a>Desen

- 1-9 arasında bir basamak
- Doğum tarihini temsil eden altı basamak (YYAAA)
- İki basamak; 01-52 veya 99 olabilir
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_romania_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_romania_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_romania_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- mali dönemler hakkında daha fazla ifade.
- identificarea fiscalÜnr #
- id-ul taxei
- sigorta numarası
- sigorta numarası #
- ulusal kimlik #
- ulusal kimlik
- ulusal kimlik numarası
- num identificare personal
- numır kimlikleri
- num bir kişisel unic
- numridentitate #
- numridentitate
- numãrpersonalunic #
- numãrpersonalunic
- num birru de identificare mali
- numrul de identificare mali
- kişisel sayısal kod
- sabitleme #
- sabitleme
- vergi dosyası yok
- vergi dosyası numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #
- benzersiz tanımlama numarası
- benzersiz kimlik numarası
- uniqueidentityno #
- uniqueidentityno


## <a name="romania-physical-addresses"></a>Romanya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Romanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="russia-passport-number-domestic"></a>Yurt içi Rusya pasaport numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

10 basamaklı sayı

### <a name="pattern"></a>Desen

10 basamaklı sayı:

- İki basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- İki basamak
- isteğe bağlı bir boşluk
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtex türü Regex_Russian_Passport_Number_Domestic desene eşleşen içeriği bulur.
- Bir Keyword_Russian_Passport_Number anahtar sözcüğü bulunur.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- pasaport numarası
- pasaport yok
- pasaport #
- pasaport kimliği
- Passportno #
- pasaportsayı #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>Rusya pasaport numarası uluslararası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

dokuz basamaklı sayı

### <a name="pattern"></a>Desen

dokuz basamaklı sayı:

- İki basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtexex Regex_Russian_Passport_Number_International desene eşleşen içeriği bulur.
- Bir Keyword_Russian_Passport_Number anahtar sözcüğü bulunur.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- pasaport numarası
- pasaport yok
- pasaport #
- pasaport kimliği
- Passportno #
- pasaportsayı #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>Suudi Arabistan Ulusal Kimliği

### <a name="format"></a>Biçim

10 basamak

### <a name="pattern"></a>Desen

Birbirini arda 10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_saudi_arabia_national_id desene eşleşen içeriği bulur.
- Bir Keyword_saudi_arabia_national_id anahtar sözcüğü bulunur.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Kimlik Kartı
- I kart numarası
- Kimlik numarası
- الوطنية الهوية بطاقة رقم


## <a name="singapore-national-registration-identity-card-nric-number"></a>Singapur ulusal kayıt kimlik kartı (NRIC) numarası

### <a name="format"></a>Biçim

dokuz harf ve rakam

### <a name="pattern"></a>Desen

- dokuz harf ve rakam:
- "F", "G", "S" veya "T" harfi (büyük/harfe duyarlı değildir)
- yedi basamak
- alfabetik onay basamakları

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade Regex_singapore_nric desene eşleşen içeriği bulur.
- Farklı bir Keyword_singapore_nric anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_singapore_nric desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card
- Kimlik Kartı Numarası
- NRIC
- IC
- Yabancı Kimlik Numarası
- FIN
- 身份证
- 身份證


## <a name="slovakia-drivers-license-number"></a>Slovakya sürücü lisans numarası

### <a name="format"></a>Biçim

bir karakter ve ardından yedi basamak

### <a name="pattern"></a>Desen

bir karakter ve ardından yedi basamak

- tek harf (büyük/büyük/harfe duyarlı değildir) veya basamak
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_slovakia_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_slovakia_eu_driver's_license_number` bulunur.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver's_license_number

- vodičskč preukaz
- vodičské preukazy
- vodičského preukazu
- vodičskčch preukazov


## <a name="slovakia-passport-number"></a>Slovakya pasaport numarası

### <a name="format"></a>Biçim

bir basamak veya harf, ardından boşluk veya sınırlayıcı yokken yedi basamak

### <a name="pattern"></a>Desen

bir rakam veya harf (büyük/harfe duyarlı değil) ve ardından yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_slovakia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_slovakia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_slovakia_eu_passport_number` bulunur.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="slovakia-personal-number"></a>Slovakya kişisel numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı ters eğik çizgi içeren dokuz veya 10 basamak

### <a name="pattern"></a>Desen

- Doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi (/)
- üç basamak
- isteğe bağlı bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_slovakia_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_slovakia_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev,  `Func_slovakia_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- doğum numarası
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- kimlik numarası
- kimlik no
- kimlik numarası
- identifikačná karta č
- identifikačné číslo
- kimlik kartı hayır
- kimlik kartı numarası
- národná identifikačná značka č
- ulusal numara
- ulusalsayı #
- cafezeti személyazonosító igttivány
- kişiselsayı #
- rč
- hanne cislo
- cafené číslo
- sosyal güvenlik numarası
- ssn #
- ssn
- személyi ig biryavány szám
- személyi ig biryavány száma
- személyig birvány szám
- vergi dosyası yok
- vergi dosyası numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="slovakia-physical-addresses"></a>Slovakya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Slovakya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="slovenia-drivers-license-number"></a>Slovenya sürücü lisans numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcılar olmadan dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_slovenia_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_slovenia_eu_driver's_license_number` bulunur.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver's_license_number

- vozniško dovoljenje
- vozniška številka licence
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj


## <a name="slovenia-passport-number"></a>Slovenya pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı yok, iki harf ve ardından da yedi basamak

### <a name="pattern"></a>Desen

İki harf ve ardından da yedi basamak:

- "P" harfi
- büyük harf
- yedi basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_slovenia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` bulunur.
- Normal ifade, `Regex_eu_passport_date1` tarihi D.AA.YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_slovenia_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` bulunur.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljav herti
- potni listesi #
- datum rojstva
- potni listesi
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="slovenia-physical-addresses"></a>Slovenya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Slovenya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="slovenia-tax-identification-number"></a>Slovenya vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı yok sekiz basamak

### <a name="pattern"></a>Desen

- 1-9 arasında bir basamak
- altı basamak
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_slovenia_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_slovenia_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev,  `Func_slovenia_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- vergi dosyası yok
- vergi dosyası numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="slovenia-unique-master-citizen-number"></a>Slovenya benzersiz ana numarayı

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı olmayan 13 basamak

### <a name="pattern"></a>Desen

Belirtilen desende 13 basamak:

- Doğum tarihine karşılık gelen yedi basamak (DDMMLLL) ve burada "LLL" doğum yılı son üç basamabdır
- Doğum alanına karşılık gelen iki basamak "50"
- Cinsiyet ve seri numarası bileşimine karşılık gelen üç basamak aynı gün doğum günü doğum günü. Erkek için 000-499, kadın için 500-999.
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_slovenia_eu_national_id_card` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_slovenia_eu_national_id_card` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_slovenia_eu_national_id_card` desene eşleşen içeriği bulur.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega dršavljana
- emšo
- enotna maticna številka obcana
- kimlik kartı
- kimlik numarası
- identifikacijska številka
- kimlik kartı
- nacionalna kimliği
- nacionalni potni listesi
- ulusal kimlik
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- kişisel kod
- kişisel numara
- kişisel sayısal kod
- številka dršavljana
- benzersiz benzersiz benzersiz telefon numarası
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- benzersiz ana ürün numarası
- benzersiz kayıt numarası
- uniqueidentityno #
- uniqueidentityno #


## <a name="south-africa-identification-number"></a>Güney Afrika kimlik numarası

### <a name="format"></a>Biçim

Boşluk içeremez 13 basamak

### <a name="pattern"></a>Desen

13 basamak:
- Doğum tarihi olan YYAAAA biçiminde altı basamak
- dört basamak
- tek basamaklı bir ekinlik göstergesi
- "8" veya "9" rakamı
- bir basamak, yani bir çek numarası numarası

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_south_africa_identification_number desene eşleşen içeriği bulur.
- Bir arama Keyword_south_africa_identification_number anahtar sözcüğü bulunur.
- Denetimli denetimler geçer.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Kimlik kartı
- Kimlik
- Kimlik


## <a name="south-korea-resident-registration-number"></a>Güney Kore yerleşik kayıt numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 13 basamak

### <a name="pattern"></a>Desen

13 basamak:
- Doğum tarihi olan YYAAAA biçiminde altı basamak
- kısa çizgi
- yüzyıla ve cinsiyete göre belirlenen bir rakam
- dört basamaklı bölge-doğum kodu
- yukarıdaki sayıların özdeş olduğu birini ayırt etmek için kullanılan bir rakam
- bir onay basamakları seçin.

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_south_korea_resident_number desene eşleşen içeriği bulur.
- Farklı bir Keyword_south_korea_resident_number anahtar sözcük bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_south_korea_resident_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- Ulusal kimlik kartı
- Sökenin Kayıt Numarası
- Jumin deungnok beonho
- RRN
- 주민등록번호


## <a name="spain-dni"></a>İspanya DNI

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz basamak ve ardından bir karakter

### <a name="pattern"></a>Desen

Yedi basamak ve ardından bir karakter

- sekiz basamak
- İsteğe bağlı bir boşluk veya kısa çizgi
- tek bir onay harfi (büyük/harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev veya  `Func_spain_eu_DL_and_NI_number_citizen` desene `Func_spain_eu_DL_and_NI_number_foreigner` eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_spain_eu_national_id_card"` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev veya  `Func_spain_eu_DL_and_NI_number_citizen` desene `Func_spain_eu_DL_and_NI_number_foreigner` eşleşen içeriği bulur.


```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- sigorta numarası
- ulusal kimlik numarası
- ulusal kimlik
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- kişisel kimlik numarası
- kişisel kimlik hayır
- benzersiz kimlik numarası
- uniqueid #


## <a name="spain-drivers-license-number"></a>İspanya sürücüsü lisans numarası

### <a name="format"></a>Biçim

sekiz basamak ve ardından bir karakter

### <a name="pattern"></a>Desen

sekiz basamak ve ardından bir karakter:

- sekiz basamak
- tek basamaklı veya harf (büyük/harfe duyarlı değildir)

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev veya  `Func_spain_eu_DL_and_NI_number_citizen` desene `Func_spain_eu_DL_and_NI_number_foreigner` eşleşen içeriği bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_spain_eu_driver's_license_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev veya  `Func_spain_eu_DL_and_NI_number_citizen` desene `Func_spain_eu_DL_and_NI_number_foreigner` eşleşen içeriği bulur.

```xml
      <!-- Spain Driver's License Number -->
      <Entity id="d5a82922-b501-4f40-8868-341321146aa2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver's_license_number

- permiso de conducción
- permiso conducción
- licencia de conducir
- licencia conducir
- permiso conducir
- permiso de conducir
- permisos de conducir
- permisos conducir
- carnet conducir
- carnet de conducir
- licencia de manejo
- licencia manejo


## <a name="spain-passport-number"></a>İspanya pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı olmayan harflerle sayıların sekiz veya dokuz karakterlik birleşimi

### <a name="pattern"></a>Desen

harf ve sayıların sekiz veya dokuz karakterlik birleşimi:

- İki basamak veya harf
- bir rakam veya harf (isteğe bağlı)
- altı basamak

### <a name="checksum"></a>Checksum

Uygulanamaz

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade desene  `Regex_spain_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` bulunur.
- Normal ifade `Regex_spain_eu_passport_date` , tarihi DD-AA-YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_spain_eu_passport_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_passport_number` `Keywords_spain_eu_passport_number` bulunur.

```xml
      <!-- Spain Passport Number -->
      <Entity id="d17a57de-9fa5-4e9f-85d3-85c26d89686e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_spain_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passeport n°
- n° Passeport
- pasaporte no.
- pasaporte n°
- İspanya Pasaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="spain-physical-addresses"></a>İspanya fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, İspanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="spain-social-security-number-ssn"></a>İspanya sosyal güvenlik numarası (SSN)


### <a name="format"></a>Biçim

11-12 basamak

### <a name="pattern"></a>Desen

11-12 basamak:
- İki basamak
- eğik çizgi (isteğe bağlı)
- yedi ile sekiz basamak arasında
- eğik çizgi (isteğe bağlı)
- İki basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_spanish_social_security_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.
- - Anahtar sözcük  `Keywords_spain_eu_ssn_or_equivalent` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_spanish_social_security_number desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- sosyal güvenlik yok
- sosyal güvenlik numarası
- número de la seguridad social


## <a name="spain-tax-identification-number"></a>İspanya vergi tanımlama numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Belirtilen desende yedi veya sekiz basamak ve bir veya iki harf

### <a name="pattern"></a>Desen

İspanya Ulusal Kimlik Kartı bulunan İspanyolca Doğal Kişiler:

- sekiz basamak
- büyük harf (büyük/küçük harfe duyarlı)

İspanya Ulusal Kimlik Kartı olmayan yerleşik olmayan spaniardlar

- büyük harf "L" (büyük/küçük harfe duyarlı)
- yedi basamak
- büyük harf (büyük/küçük harfe duyarlı)

İspanya Ulusal Kimlik Kartı olmayan 14 yıllık yaş altında yaşayan yerleşik spaniardlar:

- büyük harf "K" (büyük/küçük harfe duyarlı)
- yedi basamak
- büyük harf (büyük/küçük harfe duyarlı)

Yabancı'nın Kimlik Numarası ile özel olarak belirlendi

- "X", "Y" veya "Z" olan büyük harf (büyük/küçük harfe duyarlı)
- yedi basamak
- büyük harf (büyük/küçük harfe duyarlı)

Yabancının Kimlik Numarası olmadan yabancı

- "M" olan bir büyük harf (büyük/küçük harfe duyarlı)
- yedi basamak
- büyük harf (büyük/küçük harfe duyarlı)

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev veya  `Func_spain_eu_tax_file_number` desene `Func_spain_eu_DL_and_NI_number_citizen` eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_spain_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev veya  `Func_spain_eu_tax_file_number` desene `Func_spain_eu_DL_and_NI_number_citizen` eşleşen içeriği bulur.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación mali
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- vergi dosyası yok
- vergi dosyası numarası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="sql-server-connection-string"></a>SQL Server dizesini seçin

### <a name="format"></a>Biçim

"Kullanıcı Kimliği", "Kullanıcı Kimliği", "kullanıcı arabirimi" veya "UserId" dizesi ve ardından aşağıdaki desende ana hatlarıyla belirtilen karakterler ve dizeler.

### <a name="pattern"></a>Desen

- "Kullanıcı Kimliği", "Kullanıcı Kimliği", "kullanıcı arabirimi" veya "UserId" dizesi
- 1-200 arası küçük veya büyük harfler, basamaklar, simgeler, özel karakterler veya boşluklar arasında herhangi bir birleşim
- "Parola" veya "pwd" dizesinin önünde küçük harf olmayan "pwd" dizesi
- eşittir işareti (=)
- Dolar işareti ($), yüzde simgesi (%), simgeden büyük (>), simge (@), tırnak işareti ("), noktalı virgül (;), sol küme ayracı([) veya sol köşeli ayraç ({) olmayan herhangi bir karakter
- noktalı virgül (;), eğik çizgi (/) veya tırnak işareti (") olmayan 7-128 karakter birleşimi
- noktalı virgül (;) veya tırnak işareti (")

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- Normal ifade CEP_Regex_SQLServerConnectionString desene eşleşen içeriği bulur.
- Bir CEP_GlobalFilter anahtar sözcüğü bulunamıyor.
- Normal CEP_PasswordPlaceHolder ifadesi desene eşleşen içeriği bulamıyor.
- Normal CEP_CommonExampleKeywords ifade, desene eşleşen içeriği bulamıyor.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- bazı parolalar
- somepassword
- secretPassword
- örnek

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Bu hassas bilgi türü, bu anahtar sözcükleri bir anahtar sözcük listesi değil, normal bir ifade kullanarak tanımlar.

- Parola veya pwd ve ardından 0-2 boşluk, eşittir işareti (=), 0-2 boşluk ve yıldız (*) -OR-
- Password veya pwd ve ardından:
    - Eşittir işareti (=)
    - Küçük simge (<)
    - Büyük veya küçük harf, rakam, yıldız (*), kısa çizgi (-), alt çizgi (_) veya boşluk karakteri olan 1-200 karakterden herhangi biri
    - Büyüktür simgesi (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Bu hassas bilgi türü, bu anahtar sözcükleri bir anahtar sözcük listesi değil, normal bir ifade kullanarak tanımlar.

- contoso
- fabrikam
- northwind
- korumalı alan
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="surgical-procedures"></a>Yordamlar

Bu bakıla sahip olmayan varlık, ek yordamları gibi yordamlarla ilgili *terimleri algılar*.  Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="sweden-drivers-license-number"></a>İsveç sürücüsünün lisans numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

Kısa çizgi içeren 10 basamak:

- altı basamak
- kısa çizgi
- dört basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade desene  `Regex_sweden_eu_driver's_license_number` eşleşen içerik bulur.
- Anahtar sözcük veya  `Keywords_eu_driver's_license_number` `Keywords_sweden_eu_driver's_license_number` bulunur.

```xml
      <!-- Sweden Driver's License Number -->
      <Entity id="70088720-90dd-47f5-805e-5525f3567391" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_sweden_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver's_license_number

- ajokortti
- permis de conduisere
- ajokortin çok sayıda
- kuljettajat lic.
- drivere lic.
- körkort
- numrul permisului de condulişe
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer


## <a name="sweden-national-id"></a>İsveç ulusal kimliği

### <a name="format"></a>Biçim

10 veya 12 basamak ve isteğe bağlı sınırlayıcı

### <a name="pattern"></a>Desen

10 veya 12 basamak ve isteğe bağlı sınırlayıcı:
- İki basamak (isteğe bağlı)
- Tarih biçimindeki altı basamak YYAAA
- "-" veya "+" sınırlayıcı (isteğe bağlı)
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_swedish_national_identifier` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keywords_swedish_national_identifier` bulundu
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_swedish_national_identifier` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.


```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id no
- kimlik numarası
- id #
- kimlik no
- kimlik numarası
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- kimlik belgesi
- kimlik hayır
- kimlik numarası
- id-nummer
- kişisel kimlik
- personnummer #
- personnummer
- skatteidentifikationsnummer


## <a name="sweden-passport-number"></a>İsveç pasaport numarası

### <a name="format"></a>Biçim

sekiz basamak

### <a name="pattern"></a>Desen

art arda sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- normal ifade Regex_sweden_passport_number desene eşleşen içeriği bulur.
- veya bulunan bir `Keywords_eu_passport_number` anahtar `Keyword_sweden_passport` sözcük.
- Normal ifade `Regex_sweden_eu_passport_date` AAA/AAA YY (01 OCA/OCA 12) biçiminde bir tarih veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- normal ifade Regex_sweden_passport_number desene eşleşen içeriği bulur.
- veya bulunan bir `Keywords_eu_passport_number` anahtar `Keyword_sweden_passport` sözcük.


```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- kayıt kartı
- g3 işleme ücretleri
- birden çok giriş
- Numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- nr geçiş
- schengen visa
- schengen visas
- tek giriş
- sverige pass
- visa requirements
- visa processing
- visa type

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- çıkış tarihi
- son kullanma tarihi


## <a name="sweden-physical-addresses"></a>İsveç fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, İsveç'ten gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="sweden-tax-identification-number"></a>İsveç vergi tanımlama numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Belirtilen desende 10 basamak ve bir simge

### <a name="pattern"></a>Desen

10 basamak ve bir simge:

- Doğum tarihine karşılık gelen altı basamak (YYAAA)
- artı veya eksi işareti
- aşağıdaki üç basamaklı kimlik numarasını benzersiz hale
  - 1990'dan önce verilen sayılar için, yedinci ve sekizinci basamakta doğum ilçesi veya yabancı olarak doğum yapan kişiler tanımlamak
  - dokuzuncu konumdaki rakam, erkek için tek sayıya, kadın için bile cinsiyeti gösterir
- tek bir onay rakamı

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev,  `Func_sweden_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_sweden_eu_tax_file_number` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_sweden_eu_tax_file_number` desene eşleşen içeriği bulur.

```xml
      <!-- Sweden Tax Identification Number -->
      <Entity id="139acba0-a5bc-4fbb-876d-f7a493ae8a40" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Match idRef="Keywords_sweden_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_sweden_eu_telephone_number" />
            <Match idRef="Keywords_sweden_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- kişisel kimlik numarası
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- tverige tin
- vergi dosyası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi numarası
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="swift-code"></a>SWIFT kodu

### <a name="format"></a>Biçim

dört harf ve ardından 5-31 harf veya rakam

### <a name="pattern"></a>Desen

dört harf ve ardından 5-31 harf veya rakam:
- dört harfli banka kodu (büyük/harfe duyarlı değildir)
- isteğe bağlı bir boşluk
- 4-28 harf veya rakam (Temel Banka Hesap Numarası (BBAN))
- isteğe bağlı bir boşluk
- bir ile üç harf veya rakama (BBAN'nın kalanı)

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_swift desene eşleşen içeriği bulur.
- Farklı bir Keyword_swift anahtar sözcük bulunur.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_swift"></a>Keyword_swift

- standartlaştırma için uluslararası kuruluş 9362
- iso 9362
- iso9362
- swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- swift kodu
- swift sayı #
- swift yönlendirme numarası
- bic sayı
- bic kodu
- bic #
- bic #
- banka tanımlayıcı kodu
- Organisation internationale de normalisation 9362
- rapide #
- SWIFT kodu
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード


## <a name="switzerland-physical-addresses"></a>İsviçre fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, İsviçre'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="switzerland-ssn-ahv-number"></a>İsviçre SSN AHV numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 basamaklı sayı

### <a name="pattern"></a>Desen

13 basamaklı sayı:

- üç basamak - 756
- isteğe bağlı bir nokta
- dört basamak
- isteğe bağlı bir nokta
- dört basamak
- isteğe bağlı bir nokta
- İki basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_swiss_social_security_number_ahv desene eşleşen içeriği bulur.
- Farklı bir Keywords_swiss_social_security_number_ahv anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_swiss_social_security_number_ahv desene eşleşen içeriği bulur.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- pid
- sigorta numarası
- personalidno #
- sosyal güvenlik numarası
- kişisel kimlik numarası
- kişisel kimlik no.
- insuranceno #
- uniqueidno #
- benzersiz kimlik no.
- avs numarası
- kişisel kimlik no versicherungsnummer
- identifikationsnummer
- einzigartige identität nijer
- sozialversicherungsnummer
- kimlik personeli kimliği
- numéro de sécurité sociale


## <a name="taiwan-national-identification-number"></a>Tayvan ulusal kimlik numarası

### <a name="format"></a>Biçim

bir harf (İngilizce) ve ardından dokuz basamaklı

### <a name="pattern"></a>Desen

bir harf (İngilizce) ve ardından dokuz basamaklı:
- tek harf (İngilizce, büyük/harfe duyarlı değil)
- "1" veya "2" rakamı
- sekiz basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_taiwanese_national_id desene eşleşen içeriği bulur.
- Bir arama Keyword_taiwanese_national_id anahtar sözcüğü bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_taiwanese_national_id desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章


## <a name="taiwan-passport-number"></a>Tayvan pasaport numarası

### <a name="format"></a>Biçim

- biyometrik pasaport numarası: dokuz rakam
- biyometrik olmayan pasaport numarası: dokuz rakam

### <a name="pattern"></a>Desen
biyometrik pasaport numarası:
- "3" karakteri
- sekiz basamak

biyometrik olmayan pasaport numarası:
- dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_taiwan_passport desene eşleşen içeriği bulur.
- Bir arama Keyword_taiwan_passport anahtar sözcüğü bulunur.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC pasaport numarası
- Pasaport numarası
- Pasaport yok
- Pasaport Num
- Pasaport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào


## <a name="taiwan-resident-certificate-arctarc-number"></a>Tayvan'da yerleşik sertifika (ARC/TARC) numarası

### <a name="format"></a>Biçim

10 harf ve rakam

### <a name="pattern"></a>Desen

10 harf ve rakam:
- İki harf (büyük/küçük harfe duyarlı değildir)
- sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_taiwan_resident_certificate desene eşleşen içeriği bulur.
- Bir arama Keyword_taiwan_resident_certificate anahtar sözcüğü bulunur.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Yerleşik Sertifika
- Yerleşik Sertifika
- Yerleşik Sertifika.
- Kimlik kartı
- 2010'da Yerleşik Sertifika
- ARC
- Tayvan Bölgesi Yerleşik Sertifikası
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證


## <a name="thai-population-identification-code"></a>Tayca nüfus tanımlama kodu

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

13 basamak:
- ilk basamak sıfır veya dokuz değil
- 12 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_Thai_Citizen_Id desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_Thai_Citizen_Id bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_Thai_Citizen_Id desene eşleşen içeriği bulur.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- Kimlik Numarası
- Kimlik Numarası
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Türkiye ulusal kimlik numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_Turkish_National_Id desene eşleşen içeriği bulur.
- Bir arama Keyword_Turkish_National_Id anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_Turkish_National_Id desene eşleşen içeriği bulur.

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Zaman numarası
- Her zaman olduğu gibi,


## <a name="turkey-physical-addresses"></a>Türkiye fiziksel adresleri

Bu şaşırtıcı olmayan adlandırılmış varlık, Türkiye'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="types-of-medication"></a>Ilaç türleri

Bu bakıla adlandırılmış varlık, ilaç adlarını, örneğin sk *.*  Yalnızca İngilizce terimleri destekler. Ayrıca SIT adlı tüzel kişi [SIT adlı sağlık hüküm ve koşullarına](#all-medical-terms-and-conditions) da dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Yüksek


## <a name="uk-drivers-license-number"></a>B.K. sürücü lisans numarası

### <a name="format"></a>Biçim

Belirtilen biçimdeki 18 harf ve rakam birleşimi

### <a name="pattern"></a>Desen

18 harf ve rakam:
- Bir harfin yerine beş harf (büyük/küçük harfe duyarlı değildir) veya "9" rakamı.
- Bir rakam.
- Doğum tarihi için tarih biçiminde MMDDY biçiminde beş basamak. Sürücü kadın ise yedinci karakter 50 artırılır; örneğin, 01 - 12 yerine 51 - 62 arasında olabilir.
- İki harfli (büyük/küçük harf duyarlı değildir) veya bir harfin yerine "9" rakamı.
- Beş basamak.

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev, `Func_uk_drivers_license` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keywords_eu_driver's_license_number` bulunur.
- Denetimli denetimler geçer.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev, `Func_uk_drivers_license` desene eşleşen içeriği bulur.
- Denetimli denetimler geçer.

```xml
    <!-- U.K. Driver's License Number -->
    <Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75" relaxProximity="true" >
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_uk_drivers_license" />
          <Match idRef="Keywords_eu_driver's_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_uk_drivers_license" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver's_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- sürücüler lic
- sürücüler lisansları
- sürücüler lisansı
- sürücüler lisansları
- sürücüler lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü'lisansı
- sürücü lisansları
- driver'licence
- driver'licences
- sürücü'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü slic
- sürücü'slics
- driver'slicense
- sürücü dilimleri
- sürücü dilimleyicisi
- sürücü dilimleyicileri
- sürücü lic'i
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- dl #
- dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- sürücüler lic #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücüler lisansları #
- sürücüler lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü'lisansı #
- sürücü lisansları #
- driver'licence #
- driver'licences #
- sürücü'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü slic #
- sürücü'slics #
- driver'slicense #
- sürücü dilimleri #
- sürücü dilimleyicisi #
- sürücü dilimleyicileri #
- sürücü lic'i #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürüş lisansı 
- sürüş lisansı
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisanslı
- sürücüler lisanslı
- sürücü lisans
- sürüş lic
- sürücü lisans
- sürüş lisansları
- sürüş lisansı
- sürüş lisansı
- sürüş izni
- dl no
- dlno
- dl numarası


## <a name="uk-electoral-roll-number"></a>B.K. seçici rulo numarası

### <a name="format"></a>Biçim

İki harf ve ardından 1-4 basamak

### <a name="pattern"></a>Desen

İki harf (büyük/küçük harfe duyarlı değil) ve ardından 1-4 sayı

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_uk_electoral desene eşleşen içeriği bulur.
- Bir Keyword_uk_electoral anahtar sözcüğü bulunur.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- kurul üyesi adaylığı
- nomination form
- seçici kaydı
- seçici rulo


## <a name="uk-national-health-service-number"></a>B.K. ulusal sağlık hizmeti numarası

### <a name="format"></a>Biçim

Boşluklarla ayrılmış 10-17 basamak

### <a name="pattern"></a>Desen

10-17 basamak:
- 3 veya 10 basamak
- boşluk
- üç basamak
- boşluk
- dört basamak

### <a name="checksum"></a>Checksum

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_uk_nhs_number desene eşleşen içeriği bulur.
- Aşağıdakilerden biri doğrudur:
    - Farklı bir Keyword_uk_nhs_number anahtar sözcük bulunur.
    - Farklı bir Keyword_uk_nhs_number1 anahtar sözcük bulunur.
    - Bir başka Keyword_uk_nhs_number_dob anahtar sözcük bulunur.
- Denetimli denetimler geçer.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- ulusal sağlık hizmeti
- nhs
- hizmet yetkilisi
- sağlık yetkilisi

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- hasta kimliği
- hasta kimliği
- hasta no
- hasta numarası

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Doğum tarihi
- Doğum Tarihi


## <a name="uk-national-insurance-number-nino"></a>B.K. ulusal sigorta numarası (NINO)

Bu hassas bilgi türü varlık, AB Ulusal Kimlik Numarası hassas bilgi türüne dahildir. Ayrıca tek başına hassas bilgi türü bir varlık olarak da kullanılabilir.

### <a name="format"></a>Biçim

Boşluk veya tirelerle ayrılmış yedi karakter veya dokuz karakter

### <a name="pattern"></a>Desen

İki olası model:

- İki harf (geçerli NINOS bu ön ekte yalnızca belirli karakterleri kullanır; bu desen büyük/küçük harfe duyarlı değildir)
- altı basamak
- ya 'A', 'B', 'C' veya 'D' (ön ek gibi, sonekte yalnızca belirli karakterlere izin verilir; büyük/küçük harfe duyarlı değildir)

VEYA

- iki harf
- boşluk veya kısa çizgi
- İki basamak
- boşluk veya kısa çizgi
- İki basamak
- boşluk veya kısa çizgi
- İki basamak
- boşluk veya kısa çizgi
- ya 'A', 'B', 'C' veya 'D'

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_uk_nino desene eşleşen içeriği bulur.
- Bir arama Keyword_uk_nino anahtar sözcüğü bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_uk_nino desene eşleşen içeriği bulur.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- ulusal sigorta numarası
- ulusal sigorta katkıları
- koruma eylemi
- sigorta
- sosyal güvenlik numarası
- sigorta uygulaması
- tıbbi uygulama
- sosyal sigorta
- tıbbi dikkat
- sosyal güvenlik
- büyük Britanya
- NI Numarası
- NI Hayır.
- NI #
- NI #
- sigorta #
- sigorta numarası
- nationalins bire bir #
- nationalinsnumber


## <a name="uk-physical-addresses"></a>B.K. fiziksel adresler

Buundled adlı varlık, ABD'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta



## <a name="uk-unique-taxpayer-reference-number"></a>B.K. Benzersiz Vergi Mükellefi Başvuru Numarası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı olmayan 10 basamak


### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev,  `Func_uk_eu_tax_file_number` desene eşleşen içeriği bulur.
- Anahtar sözcük  `Keywords_uk_eu_tax_file_number` bulunur.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- vergi numarası
- vergi dosyası
- vergi no
- vergi numarası yok
- vergi numarası
- vergi yok #
- vergi yok
- vergi sicil numarası
- iş bire bir #
- yaln #
- aracısayı #
- taxno #
- vergi numarası #
- vergi numarası
- tin kimliği
- tin no
- tin #


## <a name="us-bank-account-number"></a>ABD banka hesap numarası

### <a name="format"></a>Biçim

6-17 basamak

### <a name="pattern"></a>Desen

6-17 art arda basamaklar

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_usa_bank_account_number desene eşleşen içeriği bulur.
- Bir Keyword_usa_Bank_Account anahtar sözcüğü bulunur.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Hesap Numarasını Denetleme
- Hesabı Denetleme
- Hesabı Denetleme #
- Acct Numarasını Denetleme
- Acct Denetimi #
- Acct No denetlendi.
- Hesap No denetlendi.
- Banka Hesap Numarası
- Banka Hesabı #
- Banka Tahakkuk Numarası
- Banka Acct #
- Banka Acct No.
- Banka Hesabı No.
- Tasarruf Hesap Numarası
- Tasarruf Hesabı.
- Tasarruf Hesabı #
- Tasarruf Tasarruf Sayısı
- Tasarruf Tasarrufları #
- Tasarruf Tasarruf Tasarrufları Hayır.
- Tasarruf Hesabı Hayır.
- Borç Hesap Numarası
- Borç Hesabı
- Borç Hesabı #
- Borç Tahakkuk Numarası
- Borç Hesabı #
- Borç Bakiyesi No.
- Borç Hesabı No.


## <a name="us-drivers-license-number"></a>ABD sürücüsünün lisans numarası

### <a name="format"></a>Biçim

Duruma bağlıdır

### <a name="pattern"></a>Desen

eyalete bağlıdır - örneğin, New York:
- sizi    ddd ile eşecek şekilde biçimlendirilmiş dokuz basamak.
- ddddddd gibi dokuz rakam eş olmaz.

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_new_york_drivers_license_number desene eşleşen içeriği bulur.
- Arama sözcüğünden Keyword_[state_name]_drivers_license_name anahtar sözcük bulunur.
- Anahtar sözcük Keyword_us_drivers_license bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev Func_new_york_drivers_license_number desene eşleşen içeriği bulur.
- Arama sözcüğünden Keyword_[state_name]_drivers_license_name anahtar sözcük bulunur.
- Farklı bir Keyword_us_drivers_license_abbreviations anahtar sözcük bulunur.
- Anahtar sözcük Keyword_us_drivers_license anahtar sözcük bulunamıyor.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- Kimlik
- Kimlikler
- DL #
- DLS #
- CDL #
- CDLS #
- Kimlik #
- Kimlikler #
- Kimlik numarası
- Kimlik numaraları
- LIC
- LIC #

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Sürücü Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLic
- DriversLics
- DriversLicense
- DriversLicenses
- Sürücüler Lic
- SürücülerLics
- Sürücüler Lisansı
- Sürücüler Lisansları
- Driver'Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü' Lic
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'sLic
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisans'ı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- kimlik numarası
- kimlik numaraları
- tanımlama #
- kimlik kartı
- kimlik kartları
- kimlik kartı
- kimlik kartları
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- Sürücü Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- Sürücüler Lic #
- SürücülerLics #
- Sürücüler Lisansı #
- Sürücüler Lisansları #
- Driver'Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü' Lic #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'sLic #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisans'ı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- kimlik kartı #
- kimlik kartları #
- kimlik kartı #
- kimlik kartları #


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- eyalet kısaltması (örneğin, "NY")
- eyalet adını (örneğin, "İstanbul")


## <a name="us-individual-taxpayer-identification-number-itin"></a>ABD tek tek vergi mükellefi kimlik numarası (ITIN)

### <a name="format"></a>Biçim

"9" ile baş eden ve dördüncü basamak olarak "7" veya "8" içeren dokuz basamak, isteğe bağlı olarak boşluk veya tirelerle biçimlendirildi

### <a name="pattern"></a>Desen

biçimlendirilmiş:
- "9" rakamı
- İki basamak
- boşluk veya kısa çizgi
- "7" veya "8"
- basamak
- boşluk veya kısa çizgi
- dört basamak

biçimlendirilmemiş:
- "9" rakamı
- İki basamak
- "7" veya "8"
- beş basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_formatted_itin desene eşleşen içeriği bulur.
- Bir başka Keyword_itin anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_unformatted_itin desene eşleşen içeriği bulur.
- Bir başka Keyword_itin anahtar sözcük bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlevin Func_formatted_itin veya Func_unformatted_itin desene eşleşen içeriği bulur.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_itin"></a>Keyword_itin

- vergi mükellefi
- vergi no
- vergi kimliği
- itin
- i.t.i.n.
- ssn
- tin
- sosyal güvenlik
- vergi mükellefi
- itins
- iş bire bir
- vergi mükellefi


## <a name="us-physical-addresses"></a>ABD fiziksel adresleri

Buundled adlandırılmış varlık, ABD'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca SIT adlı varlıkla [birlikte gelen Tüm Fiziksel](#all-physical-addresses) Adresler'e de dahildir.

### <a name="confidence-level"></a>Güven düzeyi

Orta


## <a name="us-social-security-number-ssn"></a>ABD sosyal güvenlik numarası (SSN)

### <a name="format"></a>Biçim

Biçimlendirilmiş veya biçimlendirilmemiş bir desende yer alan dokuz basamak

> [!NOTE]
> 2011'in ortasından önce verilen SSN'de, ssnnin bazı bölümlerinin geçerli olması için belirli aralıklar içinde olması gereken güçlü bir biçimlendirmesi vardır (ancak denetim sayısı yoktur).

### <a name="pattern"></a>Desen

dört işlev, dört farklı düzende SSN'ler için bakın:
- Func_ssn, tireler veya boşluklarla biçimlendirilmiş, 2011 öncesi güçlü biçimlendirmeye sahip SSN'leri (biçimlendirilmiş SSN'ler) bulur
- Func_unformatted_ssn SSN'leri 2011 öncesi, art arda dokuz basamaklı (ddddddddd) biçimlendirilmemiş, güçlü biçimlendirmeye sahip SSN'leri bulur
- Func_randomized_formatted_ssn tireler veya boşluklarla biçimlendirilmiş 2011 sonrası SSN'leri bulur (dd-dd-dddd VEYA  daği biçimlendirilmiş SSN'ler)
- Func_randomized_unformatted_ssn art arda dokuz basamaklı (ddddddd) olarak biçimlendirilmemiş 2011 sonrası SSN'leri bulur

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev, `Func_ssn` desene eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_ssn` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_unformatted_ssn' deseniyle eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_ssn` bulunur.

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından daha fazla güven verir:
- İşlev veya `Func_randomized_formatted_ssn` desene `Func_randomized_unformatted_ssn` eşleşen içeriği bulur.
- Anahtar sözcük `Keyword_ssn` bulunur.


```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ssn"></a>Keyword_ssn

- SSA Numarası
- sosyal güvenlik numarası
- sosyal güvenlik #
- sosyal güvenlik #
- sosyal güvenlik yok
- Sosyal Güvenlik #
- Soc Sn
- SSN
- SSN'ler
- SSN #
- SS #
- SSID


## <a name="usuk-passport-number"></a>ABD pasaport numarası

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

- bir harf veya rakam
- sekiz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgileri algılandığından büyük güven verir:
- İşlev Func_usa_uk_passport desene eşleşen içeriği bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` bulunur.
- Anahtar sözcük `Keywords_eu_passport_date` bulundu

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- İşlev Func_usa_uk_passport desene eşleşen içeriği bulur.
- Anahtar sözcük veya `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` bulunur.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pasaport #
- pasaport #
- Passportid
- pasaport
- Passportno
- pasaport yok
- pasaportsayı
- pasaport numarası
- pasaportlar
- pasaport numaraları

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- İngiliz pasaport
- İngiltere pasaport


## <a name="ukraine-passport-domestic"></a>Ukrayna pasaportunu yurt içi

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtexex Regex_Ukraine_Passport_Domestic desene eşleşen içeriği bulur.
- Bir başka Keyword_Ukraine_Passport_Domestic anahtar sözcük bulunur.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- Ukrayna pasaport
- pasaport numarası
- pasaport yok
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>Ukrayna pasaportunu uluslararası

Bu hassas bilgi türü yalnızca şu kişilerde kullanılabilir:
- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi yönetimi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz karakterli alfasayısal desen

### <a name="pattern"></a>Desen

sekiz karakterli alfasayısal desen:
- İki harf veya basamak
- altı basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Kayıtexex Regex_Ukraine_Passport_International desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_Ukraine_Passport_International bulunur.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- Ukrayna pasaport
- pasaport numarası
- pasaport yok
- паспорт України
- номер паспорта


