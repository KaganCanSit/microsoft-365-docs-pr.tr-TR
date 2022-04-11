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
description: DLP ilkelerinizde kullanmaya hazır birçok hassas bilgi türü vardır. Bu makalede bu hassas bilgi türlerinin tümü listelenmiştir ve bir DLP ilkesinin her türü algıladığında ne arayacağını gösterir.
ms.openlocfilehash: 69c47a717b63f8d9ac4e30f3b97fd228399bf21c
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760415"
---
# <a name="sensitive-information-type-entity-definitions"></a>Hassas bilgi türü varlık tanımları

Bu makalede tüm hassas bilgi türü varlık tanımları listelenir. Her tanım, bir DLP ilkesinin her türü algılamak için ne arayacağını gösterir. Hassas bilgi türleri hakkında daha fazla bilgi edinmek için bkz [. Hassas bilgi türleri](sensitive-information-type-learn-about.md)

> [!NOTE]
> Doğruluk numarasıyla güvenilirlik düzeyinin (yüksek/orta/düşük) eşlemesi (1 ile 100 arasında sayısal değer)
>
> - Düşük güvenilirlik: 65 veya altı
> - Orta güvenilirlik: 75
> - Yüksek güvenilirlik: 85

## <a name="aba-routing-number"></a>ABA yönlendirme numarası

### <a name="format"></a>Biçim

biçimlendirilmiş veya biçimlendirilmemiş bir desende olabilecek dokuz basamak

### <a name="pattern"></a>Desen

- 00-12, 21-32, 61-72 veya 80 aralığındaki iki basamak
- iki basamak
- isteğe bağlı kısa çizgi
- dört basamak
- isteğe bağlı kısa çizgi
- basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

İlke, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_aba_routing desenle eşleşen içeriği bulur.
- Keyword_ABA_Routing anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_aba_routing desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- aba numarası
- Aba #
- Aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- Yönlendirme #
- yönlendirme no
- yönlendirme numarası
- yönlendirme aktarım numarası
- Yönlendirme #
- RTN

## <a name="all-full-names"></a>Tüm tam adlar

Tüm tam adlar, paketlenmiş adlı bir varlıktır. Avustralya, Çin, Japonya, ABD ve AB'deki ülkeleri içeren tüm desteklenen ülkelerden/bölgelerden gelen kişilerin tam adlarını algılar. Tam adların tüm olası eşleşmelerini algılamak için bu SIT'i kullanın.

### <a name="format"></a>Biçim

Çeşitli.

### <a name="pattern"></a>Desen

Çeşitli.

### <a name="checksum"></a>Sağlama toplamı

Hayır.

### <a name="description"></a>Açıklama

Bu adlandırılmış varlık SIT, bir insanın yüksek güvene sahip bir ad olarak tanımlayacağı kişisel adlarla eşleşir. Örneğin, belirli bir addan oluşan bir dize bulunursa ve ardından bir aile adı gelirse, yüksek güvenle bir eşleşme yapılır. Üç birincil kaynak kullanır:

- Verilen adların sözlüğü.
- Aile adlarının sözlüğü.
- Adların nasıl oluşturulduğuna ait desenler.

Üç kaynak her ülke için farklıdır.  *Olivia Wilson'ın* dizeleri eşleşmeyi tetikler. Sık kullanılan verilen/aile adları nadir adlara göre daha yüksek bir güvene sahip olur. Ancak, desen kısmi eşleşmelere de izin verir. Sözlükten belirli bir ad bulunursa ve bunu sözlükte olmayan bir aile adı izlerse, kısmi bir eşleşme tetikler. Örneğin *, Tomas Richard* kısmi eşleşme tetikler. Kısmi eşleşmelere daha düşük güvenilirlik verilir.

Ayrıca, bir insanın adların göstergesi olarak göreceği desenler de uygun güvenle eşleştirilir. *O. Wilson*, *O.P. Wilson*, *Dr. O. P. Wilson**, Wilson, O.P. gibi.* ya da *T. Richard, Jr.* eşleşme olabilir.

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

Tüm tıbbi hüküm ve koşullar, tıbbi hüküm ve tıbbi koşulları algılayan paketlenmiş bir adlandırılmış varlıktır. Yalnızca İngilizce terimleri algılar. Tıbbi hüküm ve koşulların tüm olası eşleşmelerini algılamak için bu SIT'i kullanın.

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Sözlük

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="description"></a>Açıklama

Bu paketlenmiş adlandırılmış varlık, seçilmiş sözlüklerde bulunan tıbbi koşullardan bahseden metinlerle eşleşir. Desteklenen dil başına bir seçilmiş sözlük vardır. Sözlükler birçok uluslararası tıbbi kaynaktan alınmaktadır. Sözlükler, çok sayıda hatalı pozitif riski olmadan mümkün olduğunca çok sayıda tıbbi durum içerir. Her giriş, kapsamı güvence altına almak için tek bir koşulun yaygın olarak yazılmasını sağlayan farklı formlar içerir, örneğin:

- *TB*
- *Tüberküloz*
- *phthisis pulmonalis*

### <a name="contains"></a>Içerir

Bu paketlenmiş adlandırılmış varlık SIT, bu tek tek SID'leri içerir.

- Kan testi terimleri
- İlaç türleri
- Hastalık
- Genel ilaç adları
- ABD Sosyal Güvenlik Altında Engellilik Değerlendirmesi'nde listelenen bozukluklar
- Laboratuvar test terimleri
- Tıbbi koşullarla ilgili yaşam tarzları
- Tıbbi uzmanlıklar
- Cerrahi prosedürler
- Marka ilaç adları

## <a name="all-physical-addresses"></a>Tüm Fiziksel Adresler

Tüm fiziksel adresler, desteklenen tüm ülkelerden/bölgelerden fiziksel adreslerle ilgili desenleri algılayan paketlenmiş bir varlık SIT'tir.

### <a name="format"></a>Biçim

Çeşitli

### <a name="pattern"></a>Desen

Çeşitli

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="description"></a>Açıklama

Sokak adreslerinin eşleşmesi, bir insanın sokak adresi olarak tanımlayacağı dizelerle eşleşecek şekilde tasarlanmıştır. Bunu yapmak için birkaç birincil kaynak kullanır:

- Yerleşimler, ilçeler ve bölgelerin sözlüğü.
- Yol, Sokak veya Avenue gibi sokak sonekleri sözlüğü.
- Posta kodlarının desenleri.
- Adres biçimlerinin desenleri.

Kaynaklar her ülke için farklıdır. Birincil kaynaklar, belirli bir ülkede kullanılan adres biçimlerinin desenleridir. Mümkün olduğunca çok adresin eşleştiğinden emin olmak için farklı biçimler seçilir. Bu biçimler esneklik sağlar; örneğin, bir adres posta kodunu atlar veya bir şehir adını atlar veya sokak soneki olmayan bir caddeye sahip olabilir. Her durumda, bu tür eşleşmeler eşleşmenin güvenilirliğini artırmak için kullanılır.

Desenler, genel konumlarla değil tek tek adreslerle eşleşecek şekilde tasarlanmıştır. Bu nedenle *Redmond, WA 98052* veya *Main Street, Albuquerque* gibi dizeler eşleştirilmeyecek.

### <a name="contains"></a>Içerir

Bu paketlenmiş adlandırılmış varlık SIT şu ayrı SID'leri içerir:

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
- Fiziksel adresleri Birleşik Devletler

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

## <a name="argentina-national-identity-dni-number"></a>Arjantin ulusal kimlik (DNI) numarası

### <a name="format"></a>Biçim

Noktalı veya noktasız sekiz basamak

### <a name="pattern"></a>Desen

Sekiz basamak:

- iki basamak
- isteğe bağlı bir dönem
- üç basamak
- isteğe bağlı bir dönem
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_argentina_national_id desenle eşleşen içeriği bulur.
- Keyword_argentina_national_id anahtar sözcüğü bulunur.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Arjantin Ulusal Kimlik numarası
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Arjantin Benzersiz Vergi Tanımlama Anahtarı (CUIT/CUIL)

### <a name="format"></a>Biçim

Tireli 11 basamak

### <a name="pattern"></a>Desen

Tireli 11 basamak:

- 20, 23, 24, 27, 30, 33 veya 34'te iki basamak
- kısa çizgi (-)
- sekiz basamak
- kısa çizgi (-)
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_Argentina_Unique_Tax_Key` , desenle eşleşen içeriği bulur.
- 'den `Keyword_Argentina_Unique_Tax_Key` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_Argentina_Unique_Tax_Key` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- benzersiz iş gücü tanımlama kodu
- Clave Única de Identificación Tributaria
- benzersiz iş kimliği kodu
- CUİL
- Benzersiz Vergi Tanımlama Anahtarı
- Benzersiz İş Gücü Kimlik Anahtarı
- Benzersiz İşgücü Anahtarı Belirleme
- Benzersiz İş Tanımlama Kodu
- Benzersiz İş Kodu Tanımlaması
- Benzersiz İş Tanımlama Anahtarı
- Benzersiz İş Anahtarı Belirleme
- Benzersiz Vergi Kodu Belirleme
- Vergi Tanımlamanın Benzersiz Anahtarı
- Benzersiz İşgücü Tanımlama Kodu
- Benzersiz İşgücü Kimlik Kodu
- Benzersiz İşgücü Tanımlama Anahtarı
- Benzersiz İşgücü Anahtarı Belirleme
- vergi kimliği
- taxID #
- taxId
- taxidnumber
- vergi numarası
- vergi no
- Vergi #
- Vergi #
- vergi mükellefi kimliği
- vergi mükellefi numarası
- vergi mükellefi hayır
- Vergi mükellefi #
- Vergi mükellefi #
- vergi kimliği
- vergi belirleme
- Número de Identificación Fiscal
- número de contribuyente

## <a name="australia-bank-account-number"></a>Avustralya banka hesap numarası

### <a name="format"></a>Biçim

banka eyalet şube numarası olan veya olmayan altı ile 10 basamak

### <a name="pattern"></a>Desen

Hesap numarası 6 ile 10 basamaktır.

Avustralya banka eyalet şube numarası:

- üç basamak
- kısa çizgi
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_australia_bank_account_number desenle eşleşen içeriği bulur.
- Keyword_australia_bank_account_number anahtar sözcüğü bulunur.
- Normal ifade Regex_australia_bank_account_number_bsb desenle eşleşen içeriği bulur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_australia_bank_account_number desenle eşleşen içeriği bulur.

- Keyword_australia_bank_account_number anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift banka kodu
- muhabir banka
- temel para birimi
- usa hesabı
- tutucu adresi
- banka adresi
- bilgi hesabı
- fon transferleri
- banka ücretleri
- banka ayrıntıları
- bankacılık bilgileri
- tam adlar
- Uaea

## <a name="australia-business-number"></a>Avustralya iş numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcılarla 11 basamak

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcıları olan 11 basamak:

- iki basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_australian_business_number desenle eşleşen içeriği bulur.
- Keywords_australian_business_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_australian_business_number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- avustralya iş no
- iş numarası
- Abn #
- businessid #
- iş kimliği
- Abn
- businessno #

## <a name="australia-company-number"></a>Avustralya şirket numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sınırlayıcılı dokuz basamak

### <a name="pattern"></a>Desen

sınırlayıcılı dokuz basamak:

- üç basamak
- boşluk
- üç basamak
- boşluk
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_Australian_Company_Number desenle eşleşen içeriği bulur.
- Keyword_Australian_Company_Number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_Australian_Company_Number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- -bilirsiniz
- avustralya şirketi hayır
- avustralya şirketi hayır #
- avustralya şirket numarası
- avustralyalı şirket hayır
- avustralyalı şirket hayır #
- avustralya şirket numarası

## <a name="australia-drivers-license-number"></a>Avustralya ehliyet numarası

### <a name="format"></a>Biçim

dokuz harf ve rakam

### <a name="pattern"></a>Desen

dokuz harf ve rakam:

- iki basamak veya harf (büyük/küçük harfe duyarlı değil)
- iki basamak
- beş basamak veya harf (büyük/küçük harfe duyarlı değil)

VEYA

- bir-iki isteğe bağlı harf (büyük/küçük harfe duyarlı değil)
- dört -dokuz basamak

VEYA

- dokuz basamak veya harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_australia_drivers_license_number desenle eşleşen içeriği bulur.
- Keyword_australia_drivers_license_number anahtar sözcüğü bulunur.
- Keyword_australia_drivers_license_number_exclusions anahtar sözcüğü bulunamadı.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- uluslararası sürüş izinleri
- avustralya otomobil birliği
- uluslararası sürüş izni
- DriverLicence
- DriverLicences
- Sürücü Lic
- Sürücü Belgesi
- Sürücü Lisansları
- DriversLic
- DriversLicence
- DriversLicences
- Sürücüler Lic
- Sürücüler Lics
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'Lic
- Driver'Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Driver' Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Driver'sLic
- Driver'sLics
- Driver'sLicence
- Driver'sLicences
- Sürücü Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- Sürücü Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- DriversLic #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Sürücüler Lic #
- Sürücüler Lics #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'Lic #
- Driver'Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver' Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicence #
- Driver'sLicences #
- Sürücü Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- Acar
- DriverLicense
- DriverLicenses
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLicense
- DriversLicenses
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- Driver'sLicense
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- DriverLicense #
- DriverLicenses #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLicense #
- DriversLicenses #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver'sLicense #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #

## <a name="australia-medical-account-number"></a>Avustralya tıbbi hesap numarası

### <a name="format"></a>Biçim

10-11 basamak

### <a name="pattern"></a>Desen

10-11 basamak:

- İlk basamak 2-6 aralığındadır
- Dokuzuncu basamak bir denetim basamadır
- Onuncu basamak sorun basamaktır
- 11. basamak (isteğe bağlı) tek tek sayıdır

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_australian_medical_account_number desenle eşleşen içeriği bulur.
- Keyword_Australia_Medical_Account_Number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- banka hesabı ayrıntıları
- medicare ödemeleri
- ipotek hesabı
- banka ödemeleri
- bilgi dalı
- kredi kartı kredisi
- insan hizmetleri bölümü
- yerel hizmet
- Medicare

## <a name="australia-passport-number"></a>Avustralya pasaport numarası

### <a name="format"></a>Biçim

sekiz veya dokuz alfasayısal karakter

### <a name="pattern"></a>Desen

- bir harf (N, E, D, F, A, C, U, X) ve ardından yedi basamak veya
- İki harf (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) ve ardından yedi basamak.

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_australia_passport_number` , desenle eşleşen içeriği bulur.
- 'den `Keyword_australia_passport_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade `Regex_australia_passport_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları
- pasaport ayrıntıları
- göçmenlik ve vatandaşlık
- avustralya birleşik topluluğu
- göç departmanı
- ulusal kimlik kartı
- seyahat belgesi
- veren yetkili

## <a name="australia-physical-addresses"></a>Avustralya fiziksel adresleri

Sarılmamış adlandırılmış varlık, Avustralya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi
Orta

## <a name="australia-tax-file-number"></a>Avustralya vergi dosyası numarası

### <a name="format"></a>Biçim

sekiz ila dokuz basamak

### <a name="pattern"></a>Desen

sekiz ila dokuz basamak genellikle aşağıdaki gibi boşluklarla gösterilir:

- üç basamak
- isteğe bağlı bir alan
- üç basamak
- isteğe bağlı bir alan
- son basamak bir denetim basamağı olduğunda iki ile üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_australian_tax_file_number desenle eşleşen içeriği bulur.
- Keyword_Australia_Tax_File_Number veya Keyword_number_exclusions anahtar sözcüğü bulunamadı.
- Sağlama toplamı geçer.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- avustralya iş numarası
- marjinal vergi oranı
- medicare levy
- portföy numarası
- hizmet gazileri
- stopaj vergisi
- bireysel vergi iadesi
- vergi dosyası numarası
- Tfn

## <a name="austria-drivers-license-number"></a>Avusturya ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_austria_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_austria_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver s_license_number

- führerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Avusturya kimlik kartı

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Harflerin, basamakların ve özel karakterlerin 24 karakterlik birleşimi

### <a name="pattern"></a>Desen

24 karakter:

- 22 harf (büyük/küçük harfe duyarlı değil), basamaklar, ters eğik çizgi, eğik çizgi veya artı işareti

- iki harf (büyük/küçük harfe duyarlı değil), basamaklar, ters eğik çizgi, eğik çizgi, artı işareti veya eşittir işareti

### <a name="checksum"></a>Sağlama toplamı

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_austria_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_austria_eu_national_id_card` bir anahtar sözcük bulunur.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- kimlik numarası
- ulusal kimlik
- personalausweis republik österreich

## <a name="austria-passport-number"></a>Avusturya pasaport numarası

### <a name="format"></a>Biçim

Bir harf ve ardından isteğe bağlı bir boşluk ve yedi basamak

### <a name="pattern"></a>Desen

Bir harf, yedi basamak ve bir boşluk birleşimi:

- bir harf (büyük/küçük harfe duyarlı değil)
- bir boşluk (isteğe bağlı)
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_austria_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_austria_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_austria_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_austria_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
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

- sorun tarihi
- süre sonu tarihi

## <a name="austria-physical-addresses"></a>Avusturya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Avusturya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="austria-social-security-number"></a>Avusturya sosyal güvenlik numarası

### <a name="format"></a>Biçim

Belirtilen biçimde 10 basamak

### <a name="pattern"></a>Desen

10 basamak:

- seri numarasına karşılık gelen üç basamak
- bir denetim basamalı
- doğum tarihine karşılık gelen altı basamak (DDMMYY)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_austria_eu_ssn_or_equivalent` , desenle eşleşen içeriği bulur.
- anahtar sözcüğü `Keywords_austria_eu_ssn_or_equivalent` bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_austria_eu_ssn_or_equivalent` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- avusturya ssn
- ehik sayı
- ehic no
- sigorta kodu
- insurancecode #
- sigorta numarası
- sigorta no
- krankenkassennummer
- krankenversicherung
- socialsecurityno
- socialsecurityno #
- sosyal güvenlik hayır
- sosyal güvenlik numarası
- sosyal güvenlik kodu
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- ssn #
- ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje

## <a name="austria-tax-identification-number"></a>Avusturya vergi kimlik numarası

### <a name="format"></a>Biçim

isteğe bağlı kısa çizgi ve eğik çizgi içeren dokuz basamak

### <a name="pattern"></a>Desen

isteğe bağlı kısa çizgi ve eğik çizgi içeren dokuz basamak:

- iki basamak
- kısa çizgi (isteğe bağlı)
- üç basamak
- eğik çizgi (isteğe bağlı)
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_austria_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_austria_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_austria_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- Österreich
- st.nr.
- steuernummer
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- vergi numarası

## <a name="austria-value-added-tax"></a>Avusturya katma değer vergisi

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

11 karakterli alfasayısal desen:

- A veya a
- T veya t
- İsteğe bağlı alan
- U veya u
- isteğe bağlı alan
- iki veya üç basamak
- isteğe bağlı alan
- dört basamak
- isteğe bağlı alan
- bir veya iki basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_Austria_Value_Added_Tax desenle eşleşen içeriği bulur.
- Keyword_Austria_Value_Added_Tax anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_Austria_Value_Added_Tax desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- kdv numarası
- Kdv #
- avusturya kdv numarası
- kdv no.
- vatno #
- katma değer vergi numarası
- avusturya kdv
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- kdv kimlik numarası
- atu numarası
- uid numarası

## <a name="azure-documentdb-auth-key"></a>Azure DocumentDB kimlik doğrulama anahtarı

### <a name="format"></a>Biçim

"DocumentDb" dizesinin ardından aşağıdaki desende belirtilen karakterler ve dizeler gelir.

### <a name="pattern"></a>Desen

- "DocumentDb" dizesi
- 3-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- Büyüktür simgesi (>), eşittir işareti (=), tırnak işareti (") veya kesme işareti (')
- 86 küçük veya büyük harf, basamak, eğik çizgi (/) veya artı işareti (+) birleşimi
- İki eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureDocumentDBAuthKey desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Azure IAAS veritabanı bağlantı dizesi ve Azure SQL bağlantı dizesi

### <a name="format"></a>Biçim

"Sunucu", "sunucu" veya "veri kaynağı" dizesi, ardından "cloudapp.azure" dizesi de dahil olmak üzere aşağıdaki desende özetlenen karakterler ve dizeler.<!--no-hyperlink-->com" veya "cloudapp.azure.<!--no-hyperlink-->net" veya "database.windows.<!--no-hyperlink-->net" ve "Password" veya "password" ya da "pwd" dizesi.

### <a name="pattern"></a>Desen

- "Sunucu", "sunucu" veya "veri kaynağı" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" veya "database.windows.<!--no-hyperlink-->net"
- 1-300 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "Password", "password" veya "pwd" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- noktalı virgül (;), tırnak işareti (") veya kesme işareti (') olmayan bir veya daha fazla karakter
- noktalı virgül (;), tırnak işareti (") veya kesme işareti (')

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureConnectionString desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-iot-connection-string"></a>Azure IoT bağlantı dizesi

### <a name="format"></a>Biçim

"HostName" dizesinin ardından, "azure-devices" dizeleri de dahil olmak üzere aşağıdaki desende özetlenen karakterler ve dizeler.<!--no-hyperlink-->net" ve "SharedAccessKey".

### <a name="pattern"></a>Desen

- "HostName" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "azure-devices.<!--no-hyperlink-->net"
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "SharedAccessKey" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- 43 küçük veya büyük harf, basamak, eğik çizgi (/) veya artı işareti (+) birleşimi
- eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureIoTConnectionString desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Bu hassas bilgi türü, bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-publish-setting-password"></a>Azure yayımlama ayarı parolası

### <a name="format"></a>Biçim

"userpwd=" dizesi ve ardından alfasayısal dize.

### <a name="pattern"></a>Desen

- "userpwd=" dizesi
- 60 küçük harf veya basamak birleşimi
- tırnak işareti (")

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzurePublishSettingPasswords desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Bu hassas bilgi türü, bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-redis-cache-connection-string"></a>Azure Redis cache bağlantı dizesi

### <a name="format"></a>Biçim

"redis.cache.windows.<!--no-hyperlink-->net" ve ardından "password" veya "pwd" dizesi de dahil olmak üzere aşağıdaki desende belirtilen karakter ve dizeler gelir.

### <a name="pattern"></a>Desen

- "redis.cache.windows.<!--no-hyperlink-->net"
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "password" veya "pwd" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 43 karakterden oluşan herhangi bir birleşim
- eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureRedisCacheConnectionString desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Biçim

"sig" dizesinin ardından aşağıdaki desende özetlenen karakterler ve dizeler gelir.

### <a name="pattern"></a>Desen

- "sig" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- küçük veya büyük harf, rakam veya yüzde işareti (%) olan 43-53 karakter arasında herhangi bir birleşim
- "%3d" dizesi
- küçük veya büyük harf, rakam veya yüzde işareti (%) olmayan herhangi bir karakter

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureSAS desenle eşleşen içeriği bulur.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Azure service bus bağlantı dizesi

### <a name="format"></a>Biçim

"EndPoint" dizesinin ardından aşağıdaki desende belirtilen karakterler ve dizeler ve "servicebus.windows" dizeleri de dahil olmak üzere.<!--no-hyperlink-->net" ve "SharedAccesKey".

### <a name="pattern"></a>Desen

- "EndPoint" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "servicebus.windows.<!--no-hyperlink-->net"
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "SharedAccessKey" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 43 karakterden oluşan herhangi bir birleşim
- eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureServiceBusConnectionString desenle eşleşen içeriği bulur.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-storage-account-key"></a>Azure depolama hesabı anahtarı

### <a name="format"></a>Biçim

"DefaultEndpointsProtocol" dizesi ve ardından "AccountKey" dizesi de dahil olmak üzere aşağıdaki desende özetlenen karakterler ve dizeler gelir.

### <a name="pattern"></a>Desen

- "DefaultEndpointsProtocol" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "AccountKey" dizesi
- sıfırdan iki boşluk karakterine
- eşittir işareti (=)
- sıfırdan iki boşluk karakterine
- küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) olan 86 karakterden oluşan herhangi bir birleşim
- iki eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureStorageAccountKey desenle eşleşen içeriği bulur.
- Normal ifade CEP_AzureEmulatorStorageAccountFilter desenle eşleşen içeriği bulmaz.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknik olarak, bu hassas bilgi türü bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.)

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="azure-storage-account-key-generic"></a>Azure Depolama hesap anahtarı (genel)

### <a name="format"></a>Biçim

86 küçük veya büyük harf, rakam, eğik çizgi (/) veya artı işareti (+) birleşimi, aşağıdaki desende ana hatlarıyla belirtilen karakterlerden önce veya takip eder.

### <a name="pattern"></a>Desen

- sıfır ile büyüktür simgesinden birine (>), kesme işareti ('), eşittir işareti (=), tırnak işareti (") veya sayı işareti (#)
- küçük veya büyük harf, basamak, eğik çizgi (/) veya artı işareti (+) olan 86 karakterden oluşan herhangi bir birleşim
- iki eşittir işareti (=)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_AzureStorageAccountKeyGeneric desenle eşleşen içeriği bulur.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-drivers-license-number"></a>Belçika ehliyet numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_belgium_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_belgium_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver s_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- führerschein
- führerschein
- führerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire

## <a name="belgium-national-number"></a>Belçika ulusal numarası

### <a name="format"></a>Biçim

11 basamak artı isteğe bağlı sınırlayıcılar

### <a name="pattern"></a>Desen

11 basamak ve sınırlayıcılar:

- YY biçiminde altı basamak ve iki isteğe bağlı nokta. Doğum tarihi için MM.DD
- Nokta, tire, boşluktan isteğe bağlı sınırlayıcı
- üç sıralı basamak (erkekler için, hatta dişiler için)
- Nokta, tire, boşluktan isteğe bağlı sınırlayıcı
- iki denetim basamağı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_belgium_national_number desenle eşleşen içeriği bulur.
- Keyword_belgium_national_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_belgium_national_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- belasting aantal
- Bnn #
- Bnn
- carte d'identité
- identifiant national
- identifiantnational #
- identificatie
- Kimlik
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- Kimlik
- Yazıt
- ulusal sayı
- ulusal kayıt defteri
- nationalnumber #
- nationalnumber
- Nif #
- Nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- kişisel kimlik numarası
- personalausweis
- personalidnumber #
- registratie
- Kayıt
- registrationsnumme
- registrierung
- sosyal güvenlik numarası
- ssn #
- ssn
- steuernummer
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="belgium-passport-number"></a>Belçika pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen iki harf ve ardından altı basamak

### <a name="pattern"></a>Desen

iki harf ve ardından altı basamak

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

 DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_belgium_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_belgium_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date2` , tarihi DD AA YY biçiminde veya anahtar sözcük olarak `Keywords_eu_passport_date` bulur veya `Keywords_belgium_eu_passport_number` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_belgium_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_belgium_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Passport carte
- Passport livre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="belgium-physical-addresses"></a>Belçika fiziksel adresleri

Bu unbundled adlandırılmış varlık, Belçika'dan gelen fiziksel adreslerle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="belgium-value-added-tax-number"></a>Belçika katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

12 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

12 karakterli alfasayısal desen:

- B veya b harfi
- E veya e harfi
- bir basamak 0
- 1'den 9'a kadar olan bir basamak
- isteğe bağlı nokta veya Kısa Çizgi veya boşluk
- dört basamak
- isteğe bağlı nokta veya Kısa Çizgi veya boşluk
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_belgium_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_belgium_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_belgium_value_added_tax_number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- kdv numarası
- kdv no
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- Btw
- Btw #
- Kdv #

## <a name="blood-test-terms"></a>Kan testi terimleri

Bu unbundled adlandırılmış varlık *, hCG* gibi kan testleriyle ilgili terimleri algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="brand-medication-names"></a>Marka ilaç adları

Bu unbundled adlı varlık *, Tylenol* gibi marka ilaç adlarını algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="brazil-cpf-number"></a>Brezilya CPF numarası

### <a name="format"></a>Biçim

Denetim basamağı içeren ve biçimlendirilebilen veya biçimlendirilemeyen 11 basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:

- üç basamak
- dönem
- üç basamak
- dönem
- üç basamak
- kısa çizgi
- denetim basamakları olan iki basamak

Biçimlendir -ilmemiş:

- Son iki basamağın denetim basamakları olduğu 11 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_brazil_cpf desenle eşleşen içeriği bulur.
- Keyword_brazil_cpf anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_brazil_cpf desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Kimlik
- Kayıt
- Gelir
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita

## <a name="brazil-legal-entity-number-cnpj"></a>Brezilya tüzel kişilik numarası (CNPJ)

### <a name="format"></a>Biçim

Kayıt numarası, dal numarası ve denetim basamakları ile sınırlayıcıları içeren 14 basamak

### <a name="pattern"></a>Desen

14 basamak ve sınırlayıcılar:

- iki basamak
- dönem
- üç basamak
- dönem
- üç basamak (bu ilk sekiz basamak kayıt numarasıdır)
- eğik çizgi
- dört basamaklı dal numarası
- kısa çizgi
- denetim basamakları olan iki basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_brazil_cnpj desenle eşleşen içeriği bulur.
- Keyword_brazil_cnpj anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_brazil_cnpj desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- Tüzel Kişiliklerin Ulusal Kayıt Defteri
- Vergi Mükellefleri Kayıt Defteri
- Tüzel
- Tüzel kişilikler
- Kayıt Durumu
- Business
- Şirket
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação kadastro
- Inscrição
- Empresa

## <a name="brazil-national-identification-card-rg"></a>Brezilya ulusal kimlik kartı (RG)

### <a name="format"></a>Biçim

Registro Geral (eski biçim): Dokuz basamak

Registro de Identidade (RIC) (yeni biçim): 11 basamak

### <a name="pattern"></a>Desen

Registro Geral (eski biçim):

- iki basamak
- dönem
- üç basamak
- dönem
- üç basamak
- kısa çizgi
- denetim basamalı bir basamak

Registro de Identidade (RIC) (yeni biçim):

- 10 basamak
- kısa çizgi
- denetim basamalı bir basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_brazil_rg desenle eşleşen içeriği bulur.
- Keyword_brazil_rg anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- kimlik kartı
- ulusal kimlik
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (bu anahtar sözcük büyük/küçük harfe duyarlıdır)
- RIC (bu anahtar sözcük büyük/küçük harfe duyarlıdır)

## <a name="brazil-physical-addresses"></a>Brezilya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Brezilya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="bulgaria-drivers-license-number"></a>Bulgaristan ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_bulgaria_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_bulgaria_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
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

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_bulgaria_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_bulgaria_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_bulgaria_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_bulgaria_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт Hayır

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="bulgaria-physical-addresses"></a>Bulgaristan fiziksel adresleri

Bu unbundled adlandırılmış varlık, Bulgaristan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="bulgaria-uniform-civil-number"></a>Bulgaristan üniforma sivil numarası
Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

Boşluk ve sınırlayıcı içermeyen 10 basamak

- doğum tarihine karşılık gelen altı basamak (YYMMDD)
- doğum sırasına karşılık gelen iki basamak
- cinsiyete karşılık gelen bir basamak: Erkek için çift basamak ve kadın için tek bir basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_bulgaria_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_bulgaria_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_bulgaria_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- Bnn #
- Bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- kimlik numarası
- ulusal kimlik
- ulusal sayı
- nationalnumber #
- nationalnumber
- kişisel kimlik
- kişisel hayır
- kişisel numara
- personalidnumber #
- sosyal güvenlik numarası
- ssn #
- ssn
- tekdüzen sivil kimlik
- tek tip sivil hayır
- tek tip sivil numara
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- benzersiz vatandaşlık numarası
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
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #

## <a name="canada-bank-account-number"></a>Kanada banka hesap numarası

### <a name="format"></a>Biçim

7 veya 12 basamak

### <a name="pattern"></a>Desen

Kanada Banka Hesap Numarası 7 veya 12 basamaktır.

Kanada banka hesabı geçiş numarası:

- beş basamak
- kısa çizgi
- üç basamak OR
- sıfır "0"
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_canada_bank_account_number desenle eşleşen içeriği bulur.
- Keyword_canada_bank_account_number anahtar sözcüğü bulunur.
- Normal ifade Regex_canada_bank_account_transit_number desenle eşleşen içeriği bulur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_canada_bank_account_number desenle eşleşen içeriği bulur.
- Keyword_canada_bank_account_number anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- kanada tasarruf bonoları
- kanada gelir ajansı
- kanada finans kurumu
- doğrudan para yatırma formu
- kanada vatandaşı
- yasal temsilci
- noter
- yeminler komiseri
- çocuk bakımı avantajı
- evrensel çocuk bakımı
- kanada çocuk vergisi avantajı
- gelir vergisi avantajı
- uyumlaştırılmış satış vergisi
- sosyal sigorta numarası
- gelir vergisi iadesi
- çocuk vergisi avantajı
- bölgesel ödemeler
- kurum numarası
- para yatırma isteği
- bankacılık bilgileri
- doğrudan para yatırma

## <a name="canada-drivers-license-number"></a>Kanada ehliyet numarası

### <a name="format"></a>Biçim

İllere göre değişir

### <a name="pattern"></a>Desen

Çeşitli desenler kapsayan:

- Alberta
- britanya Kolumbiyası
- Manitoba
- Yeni Brunswick
- Newfoundland/Labrador
- Nova Scotia
- Ontario
- Prens Edward Adası
- Quebec
- Saskatchewan

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_[province_name]_drivers_license_number desenle eşleşen içeriği bulur.
- Keyword_[province_name]_drivers_license_name bir anahtar sözcük bulundu.
- Keyword_canada_drivers_license anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- Bölge kısaltması, örneğin AB
- Bölge adı, örneğin Alberta

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
- Sürücü Lics
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Sürücüler Lic
- Sürücüler Lics
- Sürücü Lisansı
- Sürücü Lisansları
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'Lic
- Driver'Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- Driver' Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Sürücü Lisansları
- Driver'sLicence
- Driver'sLicences
- Sürücü Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Sürücü Belgesi
- Sürücü Lisansları
- Permis de Conduire
- Kimliği
- Kimlik
- kimlik kartı numarası
- kimlik kartı numaraları
- idcard #
- idcard #s
- kimlik kartı
- kimlik kartı kartları
- idcard
- kimlik numarası
- kimlik numaraları
- Kimlik #
- tanımlama #s
- kimlik kartı
- kimlik kartları
- Kimlik
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
- Sürücü Lics #
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
- Sürücüler Lics #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'Lic #
- Driver'Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver' Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicense #
- Sürücü Lisansları #
- Driver'sLicence #
- Driver'sLicences #
- Sürücü Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Permis de Conduire #
- Kimliği #
- Kimlik #
- kimlik kartı #
- kimlik kartı kartları #
- idcard #
- kimlik kartı #
- kimlik kartları #
- Kimlik #

## <a name="canada-health-service-number"></a>Kanada sağlık hizmeti numarası

### <a name="format"></a>Biçim

 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_canada_health_service_number desenle eşleşen içeriği bulur.
- Keyword_canada_health_service_number anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- kişisel sağlık numarası
- hasta bilgileri
- sağlık hizmetleri
- uzmanlık hizmetleri
- otomobil kazası
- hasta hastanesi
- Psikiyatrist
- işçi tazminatı
- Engelli

## <a name="canada-passport-number"></a>Kanada pasaport numarası

### <a name="format"></a>Biçim

iki büyük harf ve ardından altı basamak

### <a name="pattern"></a>Desen

iki büyük harf ve ardından altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_canada_passport_number desenle eşleşen içeriği bulur.
- Keyword_canada_passport_number veya Keyword_passport anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- kanada vatandaşlığı
- kanada pasaportu
- pasaport başvurusu
- pasaport fotoğrafları
- sertifikalı çevirmen
- kanada vatandaşları
- işlem süreleri
- yenileme uygulaması

#### <a name="keyword_passport"></a>Keyword_passport

- Pasaport Numarası
- Pasaport No
- Pasaport #
- Pasaport #
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passport
- Passport n °
- Passport Non
- Passport #
- Passport #
- PassportNon
- Passportn °

## <a name="canada-personal-health-identification-number-phin"></a>Kanada kişisel sağlık kimlik numarası (PHIN)

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_canada_phin desenle eşleşen içeriği bulur.
- Keyword_canada_phin veya Keyword_canada_provinces en az iki anahtar sözcük bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- sosyal sigorta numarası
- sistem durumu bilgileri eylemi
- gelir vergisi bilgileri
- manitoba health
- sistem durumu kaydı
- reçeteli satın almalar
- avantaj uygunluğu
- kişisel sağlık
- vekaletname
- kayıt numarası
- kişisel sağlık numarası
- uygulayıcı başvurusu
- wellness professional
- hasta referansı
- sağlık ve sağlıklı yaşam

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- Quebec
- Kuzeybatı Bölgeleri
- Ontario
- britanya Kolumbiyası
- Alberta
- Saskatchewan
- Manitoba
- Yukon
- Newfoundland ve Labrador
- Yeni Brunswick
- Nova Scotia
- Prens Edward Adası
- Kanada

## <a name="canada-physical-addresses"></a>Kanada fiziksel adresleri

Bu unbundled adlandırılmış varlık, Kanada'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="canada-social-insurance-number"></a>Kanada sosyal sigorta numarası

### <a name="format"></a>Biçim

isteğe bağlı kısa çizgi veya boşluk içeren dokuz basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:

- üç basamak
- kısa çizgi veya boşluk
- üç basamak
- kısa çizgi veya boşluk
- üç basamak

Biçimlendirilmemiş: dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_canadian_sin desenle eşleşen içeriği bulur.
- Aşağıdaki desenlerden en az ikisi:
    - Keyword_sin anahtar sözcüğü bulunur.
    - Keyword_sin_collaborative anahtar sözcüğü bulunur.
    - İşlev Func_eu_date doğru tarih biçiminde bir tarih bulur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_unformatted_canadian_sin desenle eşleşen içeriği bulur.
- Keyword_sin anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_sin"></a>Keyword_sin

- Günah
- sosyal sigorta
- numero d'assurance sociale
- Günah
- ssn
- ssns
- sosyal güvenlik
- numero d'assurance social
- ulusal kimlik numarası
- ulusal kimlik
- Günah #
- soc ins
- sosyal ins

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- sürücü belgesi
- sürücü lisansı
- sürücü belgesi
- sürücü lisansı
- DOB
- Doğum tarihi
- Doğum günü
- Doğum tarihi

## <a name="chile-identity-card-number"></a>Şili kimlik kartı numarası

### <a name="format"></a>Biçim

yedi ila sekiz basamak artı bir çek basamağı veya harfi sınırlandıran

### <a name="pattern"></a>Desen

yedi ila sekiz basamak artı sınırlayıcılar:

- bir-iki basamak
- isteğe bağlı bir dönem
- üç basamak
- isteğe bağlı bir dönem
- üç basamak
- tire
- bir basamak veya harf (büyük/küçük harfe duyarlı değil) bu bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_chile_id_card desenle eşleşen içeriği bulur.
- Keyword_chile_id_card anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_chile_id_card desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- ulusal kimlik
- ulusal kimlik numarası
- ulusal kimlik
- número de identificación nacional
- rol único nacional
- rol único tributario
- ÇALIŞTIRMAK
- RUT
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- ÇALIŞTIRMAK #
- RUT #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- çok sayıda identificacion
- identidad numero
- Şili kimliği hayır.
- Şili kimlik numarası
- Şili kimliği #
- Benzersiz Vergi Kayıt Defteri
- Benzersiz Tributary Rolü
- Benzersiz Vergi Rolü
- Benzersiz Tributary Numarası
- Benzersiz Ulusal Numara
- Benzersiz Ulusal Rol
- Ulusal benzersiz rol
- Şili kimliği hayır.
- Şili kimlik numarası
- Şili kimliği #
- R.U.T
- R.U.N

## <a name="china-resident-identity-card-prc-number"></a>Çin yerleşik kimlik kartı (PRC) numarası

### <a name="format"></a>Biçim

18 basamak

### <a name="pattern"></a>Desen

18 basamak:

- adres kodu olan altı basamak
- doğum tarihi olan YYYYMMDD biçiminde sekiz basamak
- sipariş kodu olan üç basamak
- denetim basamalı bir basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_china_resident_id desenle eşleşen içeriği bulur.
- Keyword_china_resident_id anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_china_resident_id desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Yerleşik Kimlik Kartı
- ÇHC
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

Biçimlendirilebilen veya biçimlendirilemeyen 14 ile 19 basamak (dddddd) ve luhn testini geçmesi gerekir.

### <a name="pattern"></a>Desen

Visa, MasterCard, Discover Card, JCB, American Express, hediye kartları, restoran kartları, Rupay ve China UnionPay dahil olmak üzere dünya çapındaki tüm büyük markaların kartlarını algılar.

### <a name="checksum"></a>Sağlama toplamı

Evet, Luhn çeki

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_credit_card desenle eşleşen içeriği bulur.
- Aşağıdakilerden biri doğrudur:
  - Keyword_cc_verification anahtar sözcüğü bulunur.
  - Keyword_cc_name anahtar sözcüğü bulunur.
  - İşlev Func_expiration_date doğru tarih biçiminde bir tarih bulur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_credit_card desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- kart doğrulama
- kart kimlik numarası
- Cvn
- Cid
- cvc2
- cvv2
- raptiye bloğu
- güvenlik kodu
- güvenlik numarası
- güvenlik no
- sorun numarası
- sorun yok
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- Cod. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- Cod. Sönmez
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- Cod. seguranca
- Cod. segurança
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
- fecha de süre sonu
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- Cesaret
- vencimento
- Işlem
- işlem numarası
- başvuru numarası
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- Amex
- american express
- americanexpress
- americano espresso
- Vize
- Mastercard
- ana kart
- Mc
- Mastercard
- ana kartlar
- diner's Club
- diners club
- dinersclub
- Keşfetmek
- kartı bulma
- discovercard
- kartları bulma
- JCB
- BrandSmart
- japon kart bürosu
- carte blanche
- carteblanche
- kredi kartı
- Cc #
- cc#:

- son kullanma tarihi
- exp tarihi
- süre sonu tarihi
- d'süre sonu tarihi
- date d'exp
- süre sonu tarihi
- banka kartı
- Bankcard
- kart numarası
- kart numarası
- kartsayısı
- kartsayıları
- kart numaraları
- kredi kartı
- kredi kartları
- kredi kartları
- Ccn
- kart tutucu
- Kart
- kart tutucular
- Kart
- onay kartı
- onay kartı
- onay kartları
- onay kartları
- banka kartı
- banka kartı
- banka kartları
- banka kartları
- atm kartı
- atmcard
- atm kartları
- atmcards
- Enroute
- Yolda
- kart türü
- Cardmember Acct
- cardmember hesabı
- Can
- Kurumsal Kart
- Kurumsal kartlar
- Kart türü
- kart hesap numarası
- kart üyesi hesabı
- Cardmember Acct.
- kart no.
- kart hayır
- kart numarası
- carte bancaire
- carte de crédit
- carte de credit
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
- n. Carta
- n carta
- Nr. Carta
- nr carta
- çok sayıda carta
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
- No. de tarjeta
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
- çok sayıda do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- hayır cartao
- No. do cartão
- No. cartao yapma
- rupay
- sendika ödemesi
- unionpay
- lokantalar
- Diners
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

## <a name="croatia-drivers-license-number"></a>Hırvatistan ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_croatia_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_croatia_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver's_license_number

- vozačka dozvola
- vozačke dozvole

## <a name="croatia-identity-card-number"></a>Hırvatistan kimlik kartı numarası

Bu varlık, AB Ulusal Kimlik Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak kullanılabilir.

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

art arda dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_croatia_id_card desenle eşleşen içeriği bulur.
- Keyword_croatia_id_card anahtar sözcüğü bulunur.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- ana vatandaş numarası
- nacionalni identifikacijski broj
- ulusal kimlik numarası
- oib #
- oib
- osobna iskaznica
- osobni kimliği
- osobni identifikacijski broj
- kişisel kimlik numarası
- porezni broj
- porezni identifikacijski broj
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="croatia-passport-number"></a>Hırvatistan pasaport numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_croatia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_croatia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_croatia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_croatia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- Br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Hırvatistan kişisel kimlik (OIB) numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- 10 basamak
- son basamak bir denetim basamadır

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_croatia_oib_number desenle eşleşen içeriği bulur.
- Keywords_croatia_eu_tax_file_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_croatia_oib_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- ana vatandaş numarası
- nacionalni identifikacijski broj
- ulusal kimlik numarası
- oib #
- oib
- osobna iskaznica
- osobni kimliği
- osobni identifikacijski broj
- kişisel kimlik numarası
- porezni broj
- porezni identifikacijski broj
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="croatia-physical-addresses"></a>Hırvatistan fiziksel adresleri

Bu adı kaldırılmış varlık, Hırvatistan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="cyprus-drivers-license-number"></a>Kıbrıs ehliyet numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 12 basamak

### <a name="pattern"></a>Desen

12 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_cyprus_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_cyprus_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης

## <a name="cyprus-identity-card"></a>Kıbrıs kimlik kartı

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_cyprus_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_cyprus_eu_national_id_card` bir anahtar sözcük bulunur.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- kimlik kartı numarası
- kimlik kartı numarası
- kimlik kartı
- ulusal kimlik numarası
- kişisel kimlik numarası
- ταυτοτητασ

## <a name="cyprus-passport-number"></a>Kıbrıs pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı içermeyen 6-8 basamak

### <a name="pattern"></a>Desen

bir harf ve ardından altı ila sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_cyprus_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_cyprus_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_cyprus_eu_passport_date` tarihi DD/AA/YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_cyprus_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_cyprus_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_cyprus_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- yeni bir şey
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- PasaportKimlik
- pasaport akdi
- Pasaport no.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- tarihinde sona eriyor
- yayım tarihi

## <a name="cyprus-physical-addresses"></a>Kıbrıs fiziksel adresleri

Bu unbundled adlandırılmış varlık, Kıbrıs'tan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="cyprus-tax-identification-number"></a>Kıbrıs vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz basamak ve belirtilen desende bir harf

### <a name="pattern"></a>Desen

sekiz basamak ve bir harf:

- "0" veya "9"
- yedi basamak
- bir harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_cyprus_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_cyprus_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_cyprus_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- vergi kimliği
- vergi tanımlama kodu
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- Tic #
- Tic
- teneke kimlik
- tin no
- Teneke #
- vergi kimlik kodu
- vergi kimlik adedi
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού

## <a name="czech-drivers-license-number"></a>Çek ehliyet numarası

### <a name="format"></a>Biçim

iki harf ve ardından altı basamak

### <a name="pattern"></a>Desen

sekiz harf ve rakam:

- 'E' harfi (büyük/küçük harfe duyarlı değil)
- bir mektup
- boşluk (isteğe bağlı)
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_czech_republic_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_czech_republic_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver s_license_number

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů

## <a name="czech-passport-number"></a>Çek pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

boşluk veya sınırlayıcı içermeyen sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_czech_republic_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_czech_republic_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_czech_republic_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_czech_republic_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="czech-personal-identity-number"></a>Çek kişisel kimlik numarası

### <a name="format"></a>Biçim

isteğe bağlı eğik çizgili dokuz basamak (eski biçim)

İsteğe bağlı eğik çizgili 10 basamak (yeni biçim)

### <a name="pattern"></a>Desen

dokuz basamak (eski biçim):

- doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi
- üç basamak

10 basamak (yeni biçim):

- doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi
- son basamak bir denetim basamağı olan dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_czech_id_card desenle eşleşen içeriği bulur.
- Keyword_czech_id_card anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_czech_id_card_new_format desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- doğum numarası
- çek cumhuriyeti kimliği
- czechidno #
- daňové číslo
- identifikační číslo
- kimlik no
- kimlik numarası
- identityno #
- identityno
- sigorta numarası
- ulusal kimlik numarası
- nationalnumber #
- ulusal sayı
- osobní číslo
- personalidnumber #
- kişisel kimlik numarası
- kişisel kimlik numarası
- kişisel numara
- Pıd #
- Pıd
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- ssn
- ssn #
- sosyal güvenlik numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- benzersiz kimlik numarası

## <a name="czech-republic-physical-addresses"></a>Çek Cumhuriyeti fiziksel adresleri

Bu unbundled adlandırılmış varlık, Çek Cumhuriyeti'nden gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="denmark-drivers-license-number"></a>Danimarka ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_denmark_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_denmark_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver s_license_number

- kørekort
- kørekortnummer

## <a name="denmark-passport-number"></a>Danimarka pasaport numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_denmark_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_denmark_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date2` tarihi DD AA YY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_denmark_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_denmark_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="denmark-personal-identification-number"></a>Danimarka kişisel kimlik numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

10 basamak:

- doğum tarihi olan DDMMYY biçiminde altı basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- son basamağın bir denetim basamağı olduğu dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Func_denmark_eu_tax_file_number desenle eşleşen içeriği bulur.
- Keyword_denmark_id anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade Func_denmark_eu_tax_file_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- sistem durumu kartı
- sağlık sigortası kart numarası
- sağlık sigortası numarası
- kimlik numarası
- identifikationsnummer
- identifikationsnummer #
- kimlik numarası
- krankenkassennummer
- nationalid #
- nationalnumber #
- ulusal sayı
- personalidnumber #
- personalidentityno #
- kişisel kimlik numarası
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- ssn
- ssn #
- skat kimliği
- skat kode
- skat nummer
- skattenummer
- sosyal güvenlik numarası
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- vergi kodu
- seyahat sağlık sigortası kartı
- uniqueidentityno #
- vergi numarası
- vergi kayıt numarası
- vergi kimliği
- vergi kimlik numarası
- taksiye bindi #
- vergi numarası #
- vergi no
- taxno #
- vergi numarası
- vergi tanımlama no
- Teneke #
- taxidno #
- taxidnumber #
- vergi no #
- teneke kimlik
- tin no
- cpr.nr
- cprnr
- cprnummer
- kişi
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

Bu unbundled adlandırılmış varlık, Danimarka'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="diseases"></a>Hastalık

Bu unbundled adlı varlık *, diyabet* gibi hastalık adlarıyla eşleşen metinleri algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="drug-enforcement-agency-dea-number"></a>Uyuşturucu Uygulama Dairesi (DEA) numarası

### <a name="format"></a>Biçim

iki harf ve ardından yedi basamak

### <a name="pattern"></a>Desen

Desen aşağıdakilerin tümünü içermelidir:

- Bu olası harf kümesinden bir harf (büyük/küçük harfe duyarlı değil): Kayıt yapan kod olan A/B/F/G/M/P/R
- bir harf (büyük/küçük harfe duyarlı değil), kayıt sahibinin soyadının veya '9' rakamının ilk harfidir
- yedi basamak, sonuncusu ise denetim basamağıdır

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_dea_number desenle eşleşen içeriği bulur.
- 'den `Keyword_dea_number` bir anahtar sözcük bulundu
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_dea_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- uyuşturucu uygulama uygulaması
- uyuşturucu uygulama kurumu

## <a name="estonia-drivers-license-number"></a>Estonya ehliyet numarası

### <a name="format"></a>Biçim

iki harf ve ardından altı basamak

### <a name="pattern"></a>Desen

iki harf ve altı basamak:

- "ET" harfleri (büyük/küçük harfe duyarlı değil)
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_estonia_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_estonia_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver s_license_number

- permis de conduire
- juhilubade numbrid
- juhiloa numarası
- juhiluba

## <a name="estonia-passport-number"></a>Estonya pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

bir harf ve ardından yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_estonia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_estonia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_estonia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_estonia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="estonia-personal-identification-code"></a>Estonya Kişisel Kimlik Kodu

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- cinsiyete ve doğum yüzyılına karşılık gelen bir basamak (tek sayı erkek, hatta kadın sayısı; 1-2: 19. yüzyıl; 3-4: 20. yüzyıl; 5-6: 21. yüzyıl)
- doğum tarihine karşılık gelen altı basamak (YYMMDD)
- aynı tarihte doğan kişileri ayıran seri numarasına karşılık gelen üç basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_estonia_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_estonia_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_estonia_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ık
- isikukood #
- isikukood
- maksu kimliği
- maksukohustuslase identifitseerimisnumber
- maksunumber
- ulusal kimlik numarası
- ulusal sayı
- kişisel kod
- kişisel kimlik numarası
- kişisel kimlik kodu
- kişisel kimlik numarası
- personalidnumber #
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="estonia-physical-addresses"></a>Estonya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Estonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="eu-debit-card-number"></a>AB banka kartı numarası

### <a name="format"></a>Biçim

16 basamak

### <a name="pattern"></a>Desen

Karmaşık ve sağlam desen

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_eu_debit_card desenle eşleşen içeriği bulur.
- Aşağıdakilerden en az biri doğrudur:
    - Keyword_eu_debit_card anahtar sözcüğü bulunur.
    - Keyword_card_terms_dict anahtar sözcüğü bulunur.
    - Keyword_card_security_terms_dict anahtar sözcüğü bulunur.
    - Keyword_card_expiration_terms_dict anahtar sözcüğü bulunur.
    - İşlev Func_expiration_date doğru tarih biçiminde bir tarih bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- hesap numarası
- kart numarası
- kart no.
- güvenlik numarası
- Cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- acct num
- acct no
- american express
- americanexpress
- americano espresso
- Amex
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
- kart tutucu
- kart tutucular
- kart numarası
- kart numarası
- kart numaraları
- kart türü
- cardano numerico
- Kart
- Kart
- kartsayısı
- kartsayıları
- carta bianca
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- carte blanche
- carte bleue
- carte de credit
- carte de crédit
- carte di credito
- carteblanche
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- Cb
- Ccn
- onay kartı
- onay kartları
- onay kartı
- onay kartları
- chequekaart
- Cirrus
- cirrus-edc-maestro
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
- diners club
- dinersclub
- Keşfetmek
- kartı bulma
- kartları bulma
- discovercard
- keşif kartları
- débito automático
- Edc
- eigentümername
- avrupa banka kartı
- hoofdkaart
- hoofdkaarten
- viaggio'da
- japon kart bürosu
- japanse kaartdienst
- Jcb
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
- Maestro
- ana kart
- ana kartlar
- Mastercard
- Mastercard
- Mc
- bay nakit
- n carta
- Carta
- no de tarjeta
- hayır cartao
- no do cartão
- No. de tarjeta
- No. cartao yapma
- No. do cartão
- nr carta
- Nr. Carta
- numeri di scheda
- çok sayıda carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- çok sayıda do cartao
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
- Solo
- supporti di scheda
- supporto di scheda
- Anahtarı
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
- v pay
- v-pay
- Vize
- visa plus
- visa elektron
- Visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- kart kimlik numarası
- kart doğrulama
- cardi la verifica
- Cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- Cod. Sönmez
- Cod. seguranca
- Cod. segurança
- Cod. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- Cvc
- cvc2
- Cvn
- Cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr uit
- sorun yok
- sorun numarası
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- No. dell'edizione
- No. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno il blocco
- raptiye bloğu
- prufziffer
- prüfziffer
- güvenlik kodu
- güvenlik no
- güvenlik numarası
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
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
- exp tarihi
- exp datum
- Sona erme
- Sona er
- Sona eri -yor
- Bitiş
- fecha de süre sonu
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- değerli
- validade
- valido hasta
- Cesaret
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta

## <a name="eu-drivers-license-number"></a>AB ehliyet numarası

Bu varlıklar AB Sürücü Lisans Numarası'ndadır ve hassas bilgi türleridir.

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
- [INGİLTERE.](#uk-drivers-license-number)

## <a name="eu-national-identification-number"></a>AB ulusal kimlik numarası

Bu varlıklar AB Ulusal Kimlik Numarası'ndadır ve hassas bilgi türleridir.

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
- [INGİLTERE.](#uk-national-insurance-number-nino)

## <a name="eu-passport-number"></a>AB pasaport numarası

Bu varlıklar AB pasaport numarasındadır ve hassas bilgi türleridir. Bu varlıklar AB pasaport numarası paketinde yer alır.

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
- [ABD/Birleşik Krallık pasaport numarası](#usuk-passport-number)

## <a name="eu-social-security-number-or-equivalent-identification"></a>AB sosyal güvenlik numarası veya eşdeğer kimlik

Bunlar, AB Sosyal Güvenlik Numarası veya eşdeğer kimlik bilgilerindeki varlıklardır ve hassas bilgi türleridir.

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

## <a name="eu-tax-identification-number"></a>AB Vergi kimlik numarası

Bu varlıklar AB Vergi tanımlama numarasına duyarlı bilgi türündedir.

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
- [INGİLTERE.](#uk-unique-taxpayer-reference-number)

## <a name="finland-drivers-license-number"></a>Finlandiya ehliyet numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

Kısa çizgi içeren 10 basamak:

- altı basamak
- kısa çizgi
- üç basamak
- bir rakam veya harf

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_finland_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_finland_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver's_license_number

- ajokortti
- permis de conduire
- ajokortin çok
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot

## <a name="finland-european-health-insurance-number"></a>Finlandiya Avrupa sağlık sigortası numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

20 basamaklı sayı

### <a name="pattern"></a>Desen

20 basamaklı sayı:

- 10 basamak - 8024680246
- isteğe bağlı bir boşluk veya kısa çizgi
- 10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex Regex_Finland_European_Health_Insurance_Number desenle eşleşen içeriği bulur.
- Keyword_Finland_European_Health_Insurance_Number anahtar sözcüğü bulunur.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- ehic #
- ehic
- finlandiyaehicnumber #
- finska sjukförsäkringskort
- sistem durumu kartı
- sağlık sigortası kartı
- sağlık sigortası numarası
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

altı basamak artı bir yüzyıl artı üç basamak artı bir onay basamağı gösteren bir karakter

### <a name="pattern"></a>Desen

Desen aşağıdakilerin tümünü içermelidir:

- doğum tarihi olan DDMMYY biçiminde altı basamak
- yüzyıl işaretçisi ('-', '+' veya 'a')
- üç basamaklı kişisel kimlik numarası
- denetim basamağı olan bir rakam veya harf (büyük/küçük harfe duyarsız)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- işlevi Func_finnish_national_id desenle eşleşen içeriği bulur
- Keyword_finnish_national_id anahtar sözcüğü bulundu
- sağlama toplamı geçer

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- işlevi Func_finnish_national_id desenle eşleşen içeriği bulur
- sağlama toplamı geçer

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

### <a name="keywords"></a>Anahtar kelime -ler

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- Hetu
- kimlik no
- kimlik numarası
- kimlik numarası
- identiteetti numero
- kimlik numarası
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- ulusal kimlik kartı
- ulusal kimlik no.
- kişisel kimlik
- kişisel kimlik kodu
- personalidnumber #
- personbeteckning
- personnummer
- sosyal güvenlik numarası
- sosiaaliturvatunnus
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus

## <a name="finland-passport-number"></a>Finlandiya pasaport numarası

Bu varlık AB Pasaport Numarası hassas bilgi türünde kullanılabilir ve tek başına hassas bilgi türü varlığı olarak kullanılabilir.

### <a name="format"></a>Biçim
dokuz harf ve rakamın birleşimi

### <a name="pattern"></a>Desen

dokuz harf ve rakamın birleşimi:

- iki harf (büyük/küçük harfe duyarlı değil)
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_finland_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keyword_finland_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_finland_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keyword_finland_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- çok sayıda geçiş. #
- passin numero #
- çok sayıda geçiş.
- passi #
- passi numarası

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="finland-physical-addresses"></a>Finlandiya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Finlandiya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="france-drivers-license-number"></a>Fransa ehliyet numarası

Bu varlık, AB Sürücü Lisans Numarası hassas bilgi türünde kullanılabilir ve tek başına hassas bilgi türü varlığı olarak kullanılabilir.

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

Fransız telefon numaraları gibi benzer desenleri indirime kadar doğrulama ile 12 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- işlevi Func_french_drivers_license desenle eşleşen içeriği bulur.
- Keyword_french_drivers_license anahtar sözcüğü bulunur.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
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

## <a name="france-health-insurance-number"></a>Fransa sağlık sigortası numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

21 basamaklı sayı

### <a name="pattern"></a>Desen

21 basamaklı sayı:

- 10 basamak
- isteğe bağlı bir alan
- 10 basamak
- isteğe bağlı bir alan
- basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- regex Regex_France_Health_Insurance_Number desenle eşleşen içeriği bulur.
- Keyword_France_Health_Insurance_Number anahtar sözcüğü bulunur.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- sigorta kartı
- carte vitale
- carte d'assuré social

## <a name="france-national-id-card-cni"></a>Fransa ulusal kimlik kartı (CNI)

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

12 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade Regex_france_cni desenle eşleşen içeriği bulur.
- Keywords_france_eu_national_id_card anahtar sözcüğü bulunur.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

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

Bu varlık, AB Pasaport Numarası hassas bilgi türünde kullanılabilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

dokuz basamak ve harf

### <a name="pattern"></a>Desen

dokuz basamak ve harf:

- iki basamak
- iki harf (büyük/küçük harfe duyarlı değil)
- beş basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_fr_passport` , desenle eşleşen içeriği bulur.
- veya `Keywords_france_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date3` tarihi DD AA YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_fr_passport` , desenle eşleşen içeriği bulur.
- veya `Keywords_france_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passport
- passport n °
- passport non
- passport #
- passport #
- passportnon
- passportn °
- passport français
- passport livre
- passport carte
- numéro passport
- passport n°
- n° du passport
- n° geçiş noktası

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="france-physical-addresses"></a>Fransa fiziksel adresleri

Bu unbundled adlandırılmış varlık, Fransa'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="france-social-security-number-insee"></a>Fransa sosyal güvenlik numarası (INSEE)

### <a name="format"></a>Biçim

15 basamak

### <a name="pattern"></a>Desen

İki desenden biriyle eşleşmelidir:

- 13 basamak ve ardından bir boşluk ve ardından iki basamak

  veya

- Ardışık 15 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_french_insee` , desenle eşleşen içeriği bulur.
- Keyword_fr_insee anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_french_insee veya Func_fr_insee desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

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
- No. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- No. d'identite
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- sosyal güvenlik numarası
- sosyal güvenlik kodu
- sosyal sigorta numarası

## <a name="france-tax-identification-number"></a>Fransa vergi kimlik numarası

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

13 basamak

- 0, 1, 2 veya 3 olması gereken bir basamak
- Bir basamak
- Boşluk (isteğe bağlı)
- İki basamak
- Boşluk (isteğe bağlı)
- Üç basamak
- Boşluk (isteğe bağlı)
- Üç basamak
- Boşluk (isteğe bağlı)
- Üç denetim basamağı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_france_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_france_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_france_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="france-value-added-tax-number"></a>Fransa katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

13 karakter alfasayısal desen:

- iki harf - FR (büyük/küçük harfe duyarsız)
- isteğe bağlı bir boşluk veya kısa çizgi
- iki harf veya basamak
- isteğe bağlı boşluk, nokta, kısa çizgi veya virgül
- üç basamak
- isteğe bağlı boşluk, nokta, kısa çizgi veya virgül
- üç basamak
- isteğe bağlı boşluk, nokta, kısa çizgi veya virgül
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_france_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_france_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_france_value_added_tax_number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- kdv numarası
- kdv no
- Kdv #
- katma değer vergisi
- siren kimliği no numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification siren

## <a name="generic-medication-names"></a>Genel ilaç adları

Bu unbundled adlandırılmış varlık, *asetaminofen* gibi genel ilaçların adlarını algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="germany-drivers-license-number"></a>Almanya ehliyet numarası

Bu hassas bilgi türü varlığı, AB Sürücü Lisans Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

11 basamak ve harf birleşimi

### <a name="pattern"></a>Desen

11 basamak ve harf (büyük/küçük harfe duyarlı değildir):

- bir rakam veya harf
- iki basamak
- altı basamak veya harf
- basamak
- bir rakam veya harf

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_german_drivers_license desenle eşleşen içeriği bulur.
- Keyword_german_drivers_license_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- führerschein
- führerschein
- führerscheinnummer
- führerscheinnummer
- fuehrerscheinnummer
- führerschein-
- führerschein-
- führerschein-
- führerscheinnummernr
- führerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- führerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-führerschein
- nr-fuehrerschein
- no-führerschein
- führerschein yok
- no-fuehrerschein
- n-führerschein
- n-führerschein
- n-fuehrerschein
- permis de conduire
- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dlno

## <a name="germany-identity-card-number"></a>Almanya kimlik kartı numarası

### <a name="format"></a>Biçim

1 Kasım 2010'dan bu yana: Dokuz - on bir harf ve rakam

1 Nisan 1987 ile 31 Ekim 2010 arasında: 10 basamak

### <a name="pattern"></a>Desen

1 Kasım 2010'dan bu yana: 9 - 11 karakter alfasayısal desen
- one L, M, N, P, R, T, V, W, X, Y (büyük/küçük harfe duyarsız)
- C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y ve Z'de sekiz basamak veya harf (büyük/küçük harfe duyarsız)
- isteğe bağlı denetim basamalı
- İsteğe bağlı d/D

1 Nisan 1987 ile 31 Ekim 2010 arasında:

- 10 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_german_id_card_with_check` , desenle eşleşen içeriği bulur.
- 'den `Keyword_germany_id_card` bir anahtar sözcük bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_germany_id_card` , desenle eşleşen içeriği bulur (2010 öncesi verilmiş onay basamağı olmayan 9 karakter veya 2010'da verilen 10 basamak deseni).
- Keyword_germany_id_card anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_german_id_card_with_check` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- Kimlik
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

- C, F, G, H, J, K dilinde bir harf (büyük/küçük harfe duyarsız)
- C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y ve Z'de sekiz basamak veya harf (büyük/küçük harfe duyarsız)
- isteğe bağlı denetim basamalı
- İsteğe bağlı d/D

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_german_passport_checksum` , desenle eşleşen içeriği bulur.
- veya `Keywords_eu_passport_number_common` anahtar `Keyword_german_passport` sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_german_passport` dokuz karakter deseni ile eşleşen içerik bulur (denetim basamalı ve isteğe bağlı d/D olmadan).
- veya `Keywords_eu_passport_number_common` anahtar `Keyword_german_passport` sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_german_passport_checksum` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passport no.
- passport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

## <a name="germany-physical-addresses"></a>Almanya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Almanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="germany-tax-identification-number"></a>Almanya vergi kimlik numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 11 basamak

### <a name="pattern"></a>Desen

11 basamak

- İki basamak
- İsteğe bağlı bir alan
- Üç basamak
- İsteğe bağlı bir alan
- Üç basamak
- İsteğe bağlı bir alan
- İki basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_germany_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_germany_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_germany_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer kimliği
- steueridentifikationsnummer
- steuernummer
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- Zinn #
- Zinn
- zinnnummer

## <a name="germany-value-added-tax-number"></a>Almanya katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 karakter alfasayısal desen

### <a name="pattern"></a>Desen

11 karakterli alfasayısal desen:

- D veya d harfi
- E veya e harfi
- isteğe bağlı bir alan
- üç basamak
- isteğe bağlı bir alan veya virgül
- üç basamak
- isteğe bağlı bir alan veya virgül
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_germany_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_germany_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_germany_value_added_tax_number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- kdv numarası
- kdv no
- Kdv #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer

## <a name="greece-drivers-license-number"></a>Yunanistan ehliyet numarası

Bu varlık, AB Sürücü Lisans Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_greece_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_greece_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
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

7-8 harf ve sayı ile tire birleşimi

### <a name="pattern"></a>Desen

Yedi harf ve sayı (eski biçim):

- Bir harf (Yunan alfabesinin herhangi bir harfi)
- Kısa çizgi
- Altı basamak

Sekiz harf ve sayı (yeni biçim):

- Büyük harf karakteri hem Yunanca hem de Latin alfabelerinde (ABEZHIKMNOPTYX) oluşan iki harf
- Kısa çizgi
- Altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_greece_id_card desenle eşleşen içeriği bulur.
- Keyword_greece_id_card anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade Regex_greece_id_card desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- yunanca kimlik
- yunan uyruklu kimlik
- yunan kişisel kimlik kartı
- yunan polis kimliği
- kimlik kartı
- tautotita
- ταυτότητα
- ταυτότητας

## <a name="greece-passport-number"></a>Yunanistan pasaport numarası

### <a name="format"></a>Biçim

İki harf ve ardından boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

İki harf ve ardından yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_greece_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_greece_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_greece_eu_passport_date` tarihi DD AAA YY biçiminde bulur (Örnek - 28 Ağustos 19) veya anahtar sözcüğü `Keywords_greece_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_greece_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_greece_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο

## <a name="greece-physical-addresses"></a>Yunanistan fiziksel adresleri

Bu unbundled adlandırılmış varlık, Yunanistan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="greece-social-security-number-amka"></a>Yunanistan Sosyal Güvenlik Numarası (AMKA)

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 11 basamak

### <a name="pattern"></a>Desen

- Doğum tarihi olarak altı basamak YYMMDD
- Dört basamak
- denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_greece_eu_ssn` , desenle eşleşen içeriği bulur.
- 'den `Keywords_greece_eu_ssn_or_equivalent` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_greece_eu_ssn` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- sosyal güvenlik hayır
- socialsecurityno #
- sosyal güvenlik numarası
- Özdemir
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης

## <a name="greece-tax-identification-number"></a>Yunanistan vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

Dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_greece_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_greece_eu_tax_file_number` bir anahtar sözcük bulunur.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- Afm #
- Afm
- aφμ|aφμ αριθμός
- aφμ
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- vergi kayıt defteri no
- vergi kayıt defteri numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- taxregistryno #
- teneke kimlik
- tin no
- Teneke #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο

## <a name="hong-kong-identity-card-hkid-number"></a>Hong Kong kimlik kartı (HKID) numarası

### <a name="format"></a>Biçim

Son karakter çevresinde 8-9 harf ve rakam ile isteğe bağlı parantezlerin birleşimi

### <a name="pattern"></a>Desen

8-9 harf birleşimi:

- 1-2 harf (büyük/küçük harfe duyarlı değil)
- Altı basamak
- isteğe bağlı alan
- isteğe bağlı olarak parantez içine alınmış bir onay karakteri (herhangi bir rakam veya A harfi)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_hong_kong_id_card desenle eşleşen içeriği bulur.
- Keyword_hong_kong_id_card anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_hong_kong_id_card desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

## <a name="hungary-drivers-license-number"></a>Macaristan ehliyet numarası

### <a name="format"></a>Biçim

İki harf ve ardından altı basamak

### <a name="pattern"></a>Desen

İki harf ve altı basamak:

- İki harf (büyük/küçük harfe duyarlı değil)
- Altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_hungary_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_hungary_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek

## <a name="hungary-passport-number"></a>Macaristan pasaport numarası

### <a name="format"></a>Biçim

İki harf ve ardından boşluk veya sınırlayıcı içermeyen altı veya yedi basamak

### <a name="pattern"></a>Desen

İki harf ve ardından altı veya yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_hungary_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_hungary_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_hungary_eu_passport_date` tarihi DD AAA/AAA YY biçiminde bulur (Örnek - 01 MÁR/MAR 12) veya anahtar sözcüğü `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_hungary_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_hungary_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="hungary-personal-identification-number"></a>Macaristan kişisel kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- Cinsiyete karşılık gelen bir basamak, erkek için 1, kadın için 2. 1900'lü yıllardan önce doğan veya çifte vatandaşlığa sahip vatandaşlar için de başka sayılar mümkündür.
- Doğum tarihine karşılık gelen altı basamak (YYMMDD)
- Seri numarasına karşılık gelen üç basamak
- Bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_hungary_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_hungary_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_hungary_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- kimlik numarası
- kimlik numarası
- sz ig
- Sz. ıg.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány

## <a name="hungary-physical-addresses"></a>Macaristan fiziksel adresleri

Bu unbundled adlandırılmış varlık, Macaristan'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="hungary-social-security-number-taj"></a>Macaristan sosyal güvenlik numarası (TAJ)

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

Dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_hungary_eu_ssn_or_equivalent` , desenle eşleşen içeriği bulur.
- 'den `Keywords_hungary_eu_ssn_or_equivalent` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_hungary_eu_ssn_or_equivalent` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- macar sosyal güvenlik numarası
- sosyal güvenlik numarası
- socialsecuritynumber #
- hssn #
- socialsecuritynno
- hssn
- Taj
- Taj #
- ssn
- ssn #
- sosyal güvenlik hayır
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám

## <a name="hungary-tax-identification-number"></a>Macaristan vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

10 basamak:

- "8" olması gereken bir basamak
- Sekiz basamak
- Bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_hungary_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_hungary_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_hungary_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- macar tenekesi
- hungatiantin #
- vergi dairesi hayır
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- kdv numarası

## <a name="hungary-value-added-tax-number"></a>Macaristan katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

10 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

10 karakter alfasayısal desen:

- iki harf - HU veya hu
- isteğe bağlı alan
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_hungarian_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_hungarian_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_hungarian_value_added_tax_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- Kdv
- katma değer vergi numarası
- Kdv #
- vatno #
- macarvatno #
- vergi no
- katma değer vergisi áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám

## <a name="iceland-physical-addresses"></a>İzlanda fiziksel adresleri

Bu unbundled adlandırılmış varlık, İzlanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Abd'de Sosyal Güvenlik KapsamındaKi Engellilik Değerlendirmesinde listelenen bozukluklar

Bu unbundled adlı varlık, ABD Sosyal Güvenlik Kapsamında EngelliLik Değerlendirmesi bölümünde listelenen kas *distrofisi gibi bozuklukların adlarını algılar*. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="india-drivers-license-number"></a>Hindistan Ehliyet Numarası

### <a name="format"></a>Biçim

15 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

15 harf veya rakam:

- eyalet kodunu gösteren iki harf
- isteğe bağlı boşluk veya tire
- şehir kodunu gösteren iki basamak
- isteğe bağlı boşluk veya tire
- sorunun yılını gösteren dört basamak
- isteğe bağlı boşluk veya tire
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_india_driving_license` , desenle eşleşen içeriği bulur.
- 'den `Keywords_eu_driver's_license_number_common` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_india_driving_license` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver s_license_number_common

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

## <a name="india-gst-number"></a>Hindistan GST Numarası

### <a name="format"></a>Biçim

15 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

15 harf veya rakam:

- geçerli durum kodunu temsil eden iki basamak
- isteğe bağlı bir boşluk veya tire
- Kalıcı Hesap Numarasını (PAN) temsil eden on karakter
- bir harf veya rakam
- isteğe bağlı bir boşluk veya tire
- tek harfli 'z' veya 'Z'
- isteğe bağlı bir boşluk veya tire
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_india_gst_number` , desenle eşleşen içeriği bulur.
- 'den `Keyword_india_gst_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_india_gst_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Gst
- gstin
- mal ve hizmet vergisi
- mal ve hizmet vergisi

## <a name="india-permanent-account-number-pan"></a>Hindistan kalıcı hesap numarası (PAN)

### <a name="format"></a>Biçim

10 harf veya rakam

### <a name="pattern"></a>Desen

10 harf veya rakam:

- Üç harf (büyük/küçük harfe duyarlı değil)
- C, P, H, F, A, T, B, L, J, G harfi (büyük/küçük harfe duyarlı değildir)
- Bir mektup
- Dört basamak
- Alfabetik denetim basamakları olan bir harf

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_india_permanent_account_number desenle eşleşen içeriği bulur.
- Keyword_india_permanent_account_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade Regex_india_permanent_account_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Kalıcı Hesap Numarası
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Hindistan benzersiz tanımlama (Aadhaar) numarası

### <a name="format"></a>Biçim

İsteğe bağlı boşluklar veya tireler içeren 12 basamak

### <a name="pattern"></a>Desen

12 basamak:

- 0 veya 1 olmayan bir basamak
- Üç basamak
- İsteğe bağlı bir boşluk veya tire
- Dört basamak
- İsteğe bağlı bir boşluk veya tire
- Denetim basamalı olan son basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_india_aadhaar desenle eşleşen içeriği bulur.
- Keyword_india_aadhar anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_india_aadhaar desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- Acar
- Acar #
- Uıd
- आधार
- uidai

## <a name="india-voter-id-card"></a>Hindistan Seçmen Kimlik Kartı

### <a name="format"></a>Biçim

10 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

10 harf veya rakam:

- üç harf
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_india_voter_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keyword_india_voter_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade `Regex_india_voter_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- Seçmen
- voterid
- oy kartı
- voteridcard
- seçim fotoğrafı kimlik kartı
- EPİK
- ECI
- seçim takdiri

## <a name="indonesia-identity-card-ktp-number"></a>Endonezya kimlik kartı (KTP) numarası

### <a name="format"></a>Biçim

İsteğe bağlı dönemleri içeren 16 basamak

### <a name="pattern"></a>Desen

16 basamak:

- İki basamaklı il kodu
- Nokta (isteğe bağlı)
- İki basamaklı kayıt defteri veya şehir kodu
- İki basamaklı alt dağıtım kodu
- Nokta (isteğe bağlı)
- Doğum tarihi olan DDMMYY biçiminde altı basamak
- Nokta (isteğe bağlı)
- Dört basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_indonesia_id_card desenle eşleşen içeriği bulur.
- Keyword_indonesia_id_card anahtar sözcüğü bulunur.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Uluslararası bankacılık hesap numarası (IBAN)

### <a name="format"></a>Biçim

Ülke kodu (iki harf) artı çek basamakları (iki basamak) artı bban numarası (30 karaktere kadar)

### <a name="pattern"></a>Desen

Desen aşağıdakilerin tümünü içermelidir:

- İki harfli ülke kodu
- İki denetim basamağı (ardından isteğe bağlı bir boşluk)
- Dört harf veya rakamdan oluşan 1-7 grup (boşluklarla ayrılabilir)
- 1-3 harf veya rakam

Her ülkenin biçimi biraz farklıdır. IBAN hassas bilgi türü şu 60 ülkeyi kapsar:

- Reklam
- Ae
- al
- konumunda
- Az
- Ba
- be
- Bg
- bh
- Caner
- Cr
- Cy
- Cz
- de
- Dk
- do
- ee
- Es
- Fi
- Fo
- Fr
- Gb
- Ge
- Gı
- Gl
- Gr
- Hr
- Hu
- Yani
- ıl
- is
- bu
- Kw
- Kz
- Lb
- Li
- Teğmen
- Lu
- Lv
- Mc
- md
- Beni
- Mk
- Bay
- Mt
- mu
- Nl
- No
- Pl
- Pt
- Ro
- rs
- Sa
- Se
- Si
- sk
- Sm
- Tn
- tr
- Vg

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_iban desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

Yok

## <a name="international-classification-of-diseases-icd-10-cm"></a>Uluslararası hastalık sınıflandırması (ICD-10-CM)

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Anahtar kelime

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Dictionary_icd_10_updated anahtar sözcüğü bulunur.
- Dictionary_icd_10_codes anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Dictionary_icd_10_ güncelleştirilmiş anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

Uluslararası [Hastalık Sınıflandırması, Onuncu Düzeltme, Klinik Modifikasyon (ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604) temelinde Dictionary_icd_10_updated anahtar sözcük sözlüğünden herhangi bir terim. Bu tür yalnızca terimi arar, sigorta kodlarını aramaz.

Uluslararası [Hastalık Sınıflandırması, Onuncu Düzeltme, Klinik Modifikasyon (ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604) temelinde Dictionary_icd_10_codes anahtar sözcük sözlüğünden herhangi bir terim. Bu tür yalnızca sigorta kodlarını arar, açıklamayı aramaz.

## <a name="international-classification-of-diseases-icd-9-cm"></a>Uluslararası hastalık sınıflandırması (ICD-9-CM)

### <a name="format"></a>Biçim

Sözlük

### <a name="pattern"></a>Desen

Anahtar kelime

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Dictionary_icd_9_updated anahtar sözcüğü bulunur.
- Dictionary_icd_9_codes anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Dictionary_icd_9_updated anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

Uluslararası [Hastalık Sınıflandırması, Dokuzuncu Düzeltme, Klinik Modifikasyon (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605) temelinde Dictionary_icd_9_updated anahtar sözcük sözlüğünden herhangi bir terim. Bu tür yalnızca terimi arar, sigorta kodlarını aramaz.

Uluslararası [Hastalık Sınıflandırması, Dokuzuncu Düzeltme, Klinik Modifikasyon (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605) temelinde Dictionary_icd_9_codes anahtar sözcük sözlüğünden herhangi bir terim. Bu tür yalnızca sigorta kodlarını arar, açıklamayı aramaz.

## <a name="ip-address"></a>IP adresi

### <a name="format"></a>Biçim

#### <a name="ipv4"></a>IPv4:
IPv4 adreslerinin biçimlendirilmiş (dönemler) ve biçimlendirilmemiş (noktasız) sürümlerini hesaplayan karmaşık desen

#### <a name="ipv6"></a>IPv6:
Biçimlendirilmiş IPv6 sayılarını (iki nokta üst üste dahil) hesaplayan karmaşık desen

### <a name="pattern"></a>Desen

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

IPv6 için bir DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının yüksek güveni vardır:

- Normal ifade Regex_ipv6_address desenle eşleşen içeriği bulur.
- Keyword_ipaddress anahtar sözcüğü bulunamadı.

IPv4 için, bir DLP ilkesi, 300 karaktere yakınsa bu tür hassas bilgiler algılamıştır:

- Normal ifade Regex_ipv4_address desenle eşleşen içeriği bulur.
- Keyword_ipaddress anahtar sözcüğü bulunur.

IPv6 için bir DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının yüksek güveni vardır:

- Normal ifade Regex_ipv6_address desenle eşleşen içeriği bulur.
- Keyword_ipaddress anahtar sözcüğü bulunamadı.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (bu anahtar sözcük büyük/küçük harfe duyarlıdır)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת ה

## <a name="ip-address-v4"></a>IP Adresi v4

### <a name="format"></a>Biçim

IPv4 adreslerinin biçimlendirilmiş (dönemler) ve biçimlendirilmemiş (noktasız) sürümlerini hesaplayan karmaşık desen

### <a name="pattern"></a>Desen

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_ipv4_address` , desenle eşleşen içeriği bulur.
- 'den `Keyword_ipaddress` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_ipv4_address` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (büyük/küçük harfe duyarlı)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת ה

## <a name="ip-address-v6"></a>IP Adresi v6

### <a name="format"></a>Biçim

Biçimlendirilmiş IPv6 sayılarını (iki nokta üst üste dahil) hesaplayan karmaşık desen

### <a name="pattern"></a>Desen

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_ipv6_address` , desenle eşleşen içeriği bulur.
- 'den `Keyword_ipaddress` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_ipv6_address` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (büyük/küçük harfe duyarlı)
- ip adresi
- ip adresleri
- internet protokolü
- IP-כתובת ה

## <a name="ireland-drivers-license-number"></a>İrlanda ehliyet numarası

### <a name="format"></a>Biçim

Altı basamak ve ardından dört harf

### <a name="pattern"></a>Desen

Altı basamak ve dört harf:

- Altı basamak
- Dört harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_ireland_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_ireland_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver's_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>İrlanda pasaport numarası

### <a name="format"></a>Biçim

İki harf veya basamak ve ardından boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

İki harf veya basamak ve ardından yedi basamak:

- İki basamak veya harf (büyük/küçük harfe duyarlı değil)
- Yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_ireland_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_ireland_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_ireland_eu_passport_date` tarihi DD AAA/AAA YYYY biçiminde bulur (Örnek - 01 BEA/MAY 1988) veya anahtar sözcüğü `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_ireland_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_ireland_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="ireland-personal-public-service-pps-number"></a>İrlanda kişisel kamu hizmeti (PPS) numarası

### <a name="format"></a>Biçim

Eski biçim (31 Aralık 2012'ye kadar):

- yedi basamak ve ardından 1-2 harf

Yeni biçim (1 Ocak 2013 ve sonrası):

- yedi basamak ve ardından iki harf

### <a name="pattern"></a>Desen

Eski biçim (31 Aralık 2012'ye kadar):

- yedi basamak
- bir-iki harf (büyük/küçük harfe duyarlı değil)

Yeni biçim (1 Ocak 2013 ve sonrası):

- yedi basamak
- alfabetik bir denetim basamalı harf (büyük/küçük harfe duyarlı değil)
- A-I veya "W" aralığında isteğe bağlı bir harf

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_ireland_pps desenle eşleşen içeriği bulur.
- Keywords_ireland_eu_national_id_card anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_ireland_pps desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- istemci kimlik hizmeti
- kimlik numarası
- kişisel kimlik numarası
- kişisel kamu hizmeti numarası
- kişisel hizmet no
- phearsanta seirbhíse poiblí
- pps no
- pps numarası
- pps num
- pps hizmeti hayır
- ppsn
- ppsno #
- ppsno
- Psp
- kamu hizmeti hayır
- publicserviceno #
- publicserviceno
- gelir ve sosyal sigorta numarası
- rsi no
- rsi numarası
- rsin
- seirbhís aitheantais istemcisi
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="ireland-physical-addresses"></a>İrlanda fiziksel adresleri

Bu unbundled adlandırılmış varlık, İrlanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="israel-bank-account-number"></a>İsrail banka hesap numarası

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

Biçimlendirilmiş:

- iki basamak
- tire
- üç basamak
- tire
- sekiz basamak

Biçimlendir -ilmemiş:

- Ardışık 13 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_israel_bank_account_number desenle eşleşen içeriği bulur.
- Keyword_israel_bank_account_number anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_israeli_national_id_number desenle eşleşen içeriği bulur.
- Keyword_Israel_National_ID anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

- מספר זהות
- מספר זיה וי
- מספר זיהוי ישר אלי
- זהותישר אלית
- هو ية اسرائيل ية عدد
- هوية إسرائ يلية
- رقم الهوية
- عدد هوية فريدة من نوعها
- idnumber #
- kimlik numarası
- kimlik no
- identitynumber #
- kimlik numarası
- israeliidentitynumber
- kişisel kimlik
- benzersiz kimlik

## <a name="italy-drivers-license-number"></a>İtalya ehliyet numarası

Bu tür varlık, AB Sürücü Lisans Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

10 harf ve rakamın birleşimi

### <a name="pattern"></a>Desen

10 harf ve rakamın birleşimi:

- bir harf (büyük/küçük harfe duyarlı değil)
- "A" veya "V" harfi (büyük/küçük harfe duyarlı değil)
- yedi basamak
- bir harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_italy_drivers_license_number` , desenle eşleşen içeriği bulur.
- veya `Keyword_italy_drivers_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- patent guida
- patenti di guida
- patenti guida

## <a name="italy-fiscal-code"></a>İtalya mali kodu
Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Belirtilen desendeki harf ve rakamlardan oluşan 16 karakterlik bir birleşim

### <a name="pattern"></a>Desen

Harf ve rakamlardan oluşan 16 karakterlik bir birleşim:

- aile adındaki ilk üç harfe karşılık gelen üç harf
- addaki birinci, üçüncü ve dördüncü ünsüzlere karşılık gelen üç harf
- doğum yılının son rakamlarına karşılık gelen iki basamak
- doğum ayının harfine karşılık gelen bir harf— harfler alfabetik sırada kullanılır, ancak yalnızca A-E, H, L, M, P, R to T harfleri kullanılır (ocak A ve Ekim ayı R olur)
- cinsiyetleri ayırt etmek için doğum ayının gününe karşılık gelen iki basamak, kadınlar için doğum gününe 40 eklenir
- kişinin doğduğu belediyeye özgü alan koduna karşılık gelen dört basamak (ülke genelindeki kodlar yabancı ülkeler için kullanılır)
- tek eşlikli basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_italy_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_italy_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_italy_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- kodice fiscale
- codice id personale
- codice personale
- mali kod
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- çok sayıda kişisel
- kişisel sertifika numarası
- kişisel kod
- kişisel kimlik kodu
- kişisel kimlik numarası
- personalcodeno #
- vergi kodu
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="italy-passport-number"></a>İtalya pasaport numarası

### <a name="format"></a>Biçim

iki harf veya basamak ve ardından boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

iki harf veya rakam ve ardından yedi basamak:

- iki basamak veya harf (büyük/küçük harfe duyarlı değil)
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_italy_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_italy_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_italy_eu_passport_date` tarihi DD AAA/AAA YYYY biçiminde bulur (Örnek - 01 GEN/JAN 1988) veya anahtar sözcüğü `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_italy_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_italy_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passport
- numero di passaporto
- numeri del passaporto
- passport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="italy-physical-addresses"></a>İtalya fiziksel adresleri

Bu unbundled adlandırılmış varlık, İtalya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="italy-value-added-tax-number"></a>İtalya katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcılarla 13 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcılarla 13 karakterlik alfasayısal desen:

- Ben veya ben
- T veya t
- isteğe bağlı boşluk, nokta, kısa çizgi veya virgül
- 11 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_italy_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_italy_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_italy_value_added_tax_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- kdv numarası
- kdv no
- Kdv #
- ıva
- ıva #

## <a name="japan-bank-account-number"></a>Japonya banka hesap numarası

### <a name="format"></a>Biçim

yedi veya sekiz basamak

### <a name="pattern"></a>Desen

banka hesap numarası:

- yedi veya sekiz basamak
- banka hesabı dal kodu:

- dört basamak
- boşluk veya tire (isteğe bağlı)
- üç basamak

Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_jp_bank_account desenle eşleşen içeriği bulur.
- Keyword_jp_bank_account anahtar sözcüğü bulunur.
- Aşağıdakilerden biri doğrudur:

- İşlev Func_jp_bank_account_branch_code desenle eşleşen içeriği bulur.
- Keyword_jp_bank_branch_code anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_jp_bank_account desenle eşleşen içeriği bulur.
- Keyword_jp_bank_account anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Hesap Numarası Denetleniyor
- Hesap Denetleniyor
- Hesap Denetleniyor #
- Acct Numarası Denetleniyor
- Acct Denetleniyor #
- Tahakkuk No denetleniyor.
- Hesap No denetleniyor.
- Banka Hesap Numarası
- Banka Hesabı
- Banka Hesabı #
- Banka Tahakkuk Numarası
- Banka Hesabı #
- Banka Tahakkuk No
- Banka Hesabı No.
- Tasarruf Hesabı Numarası
- Tasarruf Hesabı
- Tasarruf Hesabı #
- TasarrufLar Acct Numarası
- TasarrufLar Acct #
- TasarrufLar Tahakkuk No
- Tasarruf Hesabı No.
- Banka Hesabı Numarası
- Borç Hesabı
- Borç Hesabı #
- Borç Tahakkuk Numarası
- Borç Hesabı #
- Borç Tahakkuk No
- Borç Hesabı No
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

## <a name="japan-drivers-license-number"></a>Japonya ehliyet numarası

### <a name="format"></a>Biçim

12 basamak

### <a name="pattern"></a>Desen

Ardışık 12 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_jp_drivers_license_number desenle eşleşen içeriği bulur.
- Keyword_jp_drivers_license_number anahtar sözcüğü bulunur.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- driver'slicense
- sürücü lisansları
- driver'slicenses
- sürücü lisansları
- Dl #
- Dls #
- Lisansı #
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

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 basamaklı sayı

### <a name="pattern"></a>Desen

13 basamaklı sayı:

- bir basamaktan dokuza
- 12 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_japanese_my_number_corporate desenle eşleşen içeriği bulur.
- Keywords_japanese_my_number_corporate anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_japanese_my_number_corporate desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

12 basamaklı sayı

### <a name="pattern"></a>Desen

12 basamaklı sayı:

- dört basamak
- isteğe bağlı boşluk, nokta veya kısa çizgi
- dört basamak
- isteğe bağlı boşluk, nokta veya kısa çizgi
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_japanese_my_number_personal desenle eşleşen içeriği bulur.
- Keywords_japanese_my_number_personal anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_japanese_my_number_personal desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

iki harf ve ardından yedi basamak

### <a name="pattern"></a>Desen

iki harf (büyük/küçük harfe duyarlı değil) ve ardından yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_jp_passport desenle eşleşen içeriği bulur.
- Keyword_jp_passport anahtar sözcüğü bulunur.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

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

## <a name="japan-residence-card-number"></a>Japonya konut kartı numarası

### <a name="format"></a>Biçim

12 harf ve rakam

### <a name="pattern"></a>Desen

12 harf ve rakam:

- iki harf (büyük/küçük harfe duyarlı değil)
- sekiz basamak
- iki harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_jp_residence_card_number desenle eşleşen içeriği bulur.
- Keyword_jp_residence_card_number anahtar sözcüğü bulunur.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- İkamet kartı numarası
- İkamet kartı no
- İkamet kartı #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Japonya'da ikamet eden kayıt numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

Ardışık 11 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_jp_resident_registration_number desenle eşleşen içeriği bulur.
- Keyword_jp_resident_registration_number anahtar sözcüğü bulunur.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Yerleşik Kayıt Numarası
- Yerleşikler Temel Kayıt Defteri Numarası
- Yerleşik Kayıt No.
- Yerleşik Kayıt No.
- Residents Basic Registry No.
- Temel Yerleşik Kayıt No.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証

## <a name="japan-social-insurance-number-sin"></a>Japonya sosyal sigorta numarası (SIN)

### <a name="format"></a>Biçim

7-12 basamak

### <a name="pattern"></a>Desen

7-12 basamak:

- dört basamak
- kısa çizgi (isteğe bağlı)
- altı basamak OR
- 7-12 ardışık basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_jp_sin desenle eşleşen içeriği bulur.
- Keyword_jp_sin anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_jp_sin_pre_1997 desenle eşleşen içeriği bulur.
- Keyword_jp_sin anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Sosyal Sigorta No.
- Sosyal Sigorta Numarası
- Sosyal Sigorta Numarası
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号

## <a name="lab-test-terms"></a>Laboratuvar test terimleri

Bu unbundled adlandırılmış varlık *, İnsülin C-peptid* gibi laboratuvar testleriyle ilgili terimleri algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="latvia-drivers-license-number"></a>Letonya ehliyet numarası

### <a name="format"></a>Biçim

üç harf ve ardından altı basamak

### <a name="pattern"></a>Desen

üç harf ve altı basamak:

- üç harf (büyük/küçük harfe duyarlı değil)
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_latvia_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_latvia_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver's_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība

## <a name="latvia-passport-number"></a>Letonya pasaport numarası

### <a name="format"></a>Biçim

iki harf veya basamak ve ardından boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

iki harf veya rakam ve ardından yedi basamak:

- iki basamak veya harf (büyük/küçük harfe duyarlı değil)
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_latvia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_latvia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_latvia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_latvia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurlar
- pase numur
- pases numuri
- pases nr
- passport no
- n° du Passport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="latvia-personal-code"></a>Letonya kişisel kodu

### <a name="format"></a>Biçim

11 basamak ve isteğe bağlı kısa çizgi

### <a name="pattern"></a>Desen

Eski biçim

11 basamak ve kısa çizgi:

- doğum tarihine karşılık gelen altı basamak (DDMMYY)
- kısa çizgi
- doğum yüzyıla karşılık gelen bir basamak ("19. yüzyıl için 0", 20. yüzyıl için "1" ve 21. yüzyıl için "2")
- rastgele oluşturulan dört basamak

Yeni biçim

11 basamak

- İki basamak "32"
- Dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_latvia_eu_national_id_card` veya regex `Regex_latvia_eu_national_id_card_new_format` desenle eşleşen içeriği bulur.
- 'den `Keywords_latvia_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_latvia_eu_national_id_card` veya regex `Regex_latvia_eu_national_id_card_new_format` desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- yönetim numarası
- alvas nē
- doğum numarası
- vatandaş numarası
- sivil numara
- elektronik sayım numarası
- elektronik numara
- mali kod
- sağlık hizmeti kullanıcı numarası
- Kimliği #
- id-code
- kimlik numarası
- identifikācijas numurs
- id-number
- bireysel sayı
- latvija alva
- nacionālais id
- ulusal kimlik
- ulusal tanımlayıcı sayı
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
- personas kodlar
- nüfus tanımlama kodu
- kamu hizmeti numarası
- kayıt numarası
- gelir numarası
- sosyal sigorta numarası
- sosyal güvenlik numarası
- eyalet vergi kodu
- vergi dosyası numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- seçmen sayısı

## <a name="latvia-physical-addresses"></a>Letonya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Letonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="liechtenstein-physical-addresses"></a>Liechtenstein fiziksel adresleri

Bu unbundled adlandırılmış varlık Liechtenstein fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="lifestyles-that-relate-to-medical-conditions"></a>Tıbbi koşullarla ilgili yaşam tarzları

Bu unbundled adlı varlık *, sigara gibi* tıbbi bir duruma neden olabilecek yaşam tarzlarıyla ilgili terimleri algılar. Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="lithuania-drivers-license-number"></a>Litvanya ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_lithuania_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_lithuania_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Litvanya kişisel kodu

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 11 basamak

### <a name="pattern"></a>Desen

Boşluk ve sınırlayıcı içermeyen 11 basamak:

- kişinin cinsiyetine ve doğum yüzyılına karşılık gelen bir basamak (1-6)
- doğum tarihine karşılık gelen altı basamak (YYMMDD)
- doğum tarihinin seri numarasına karşılık gelen üç basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_lithuania_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_lithuania_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_lithuania_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- vatandaş hizmet numarası
- mokesčių id
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių numeris
- ulusal kimlik numarası
- kişisel kod
- kişisel sayısal kod
- piliečio paslaugos numeris
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- uniqueidentityno #

## <a name="lithuania-physical-addresses"></a>Litvanya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Litvanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="lithuania-passport-number"></a>Litvanya pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen sekiz basamak veya harf

### <a name="pattern"></a>Desen

sekiz basamak veya harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_lithuania_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_lithuania_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date3` tarihi DD AA YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_lithuania_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_lithuania_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="luxemburg-drivers-license-number"></a>Luxemburg ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen altı basamak

### <a name="pattern"></a>Desen

altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_luxemburg_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_luxemburg_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Luxemburg ulusal kimlik numarası (gerçek kişiler)

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı içermeyen 13 basamak

### <a name="pattern"></a>Desen

13 basamak:

- 11 basamak
- iki denetim basamağı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_luxemburg_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_luxemburg_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_luxemburg_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige kimliği
- eindeutige id-nummer
- eindeutigeid #
- id personel
- idpersonnelle #
- idpersonnelle
- tek tek kod
- bireysel kimlik
- bireysel kimlik
- bireysel kimlik
- numéro d'identification personeli
- kişisel kimlik
- kişisel kimlik
- kişisel kimlik
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- benzersiz kimlik
- benzersiz kimlik
- uniqueidkey #

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Luxemburg ulusal kimlik numarası (gerçek olmayan kişiler)

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak

- iki basamak
- isteğe bağlı bir alan
- üç basamak
- isteğe bağlı bir alan
- üç basamak
- isteğe bağlı bir alan
- iki basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_luxemburg_eu_tax_file_number_non_natural` , desenle eşleşen içeriği bulur.
- 'den `Keywords_luxemburg_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_luxemburg_eu_tax_file_number_non_natural` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain olmayan
- étain #
- identifiant d'impôt
- lüksemburg vergi identifikatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourgeois
- numéro d'identification fiscale
- sosyal güvenlik
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- steier id
- steier identifikatiounsnummer
- steier nummer
- steuer kimliği
- steueridentifikationsnummer
- steuernummer
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- Zinn #
- Zinn
- zinnzahl

## <a name="luxemburg-passport-number"></a>Luxemburg pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen sekiz basamak veya harf

### <a name="pattern"></a>Desen

sekiz basamak veya harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_luxemburg_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_luxemburg_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date3` tarihi DD AA YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_luxemburg_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_luxemburg_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- lüksemburg geçişi
- lüksemburg passport
- lüksemburg pasaportu
- geçiş yok
- no-reisepass
- nr-reisepass
- numéro de passport
- net geçirme
- nr'ı geç
- passnummer
- passport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="luxemburg-physical-addresses"></a>Luxemburg fiziksel adresleri

Bu unbundled adlandırılmış varlık Luxemburg'daki fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="malaysia-identification-card-number"></a>Malezya kimlik kartı numarası

### <a name="format"></a>Biçim

İsteğe bağlı kısa çizgi içeren 12 basamak

### <a name="pattern"></a>Desen

12 basamak:

- doğum tarihi olan YYMMDD biçiminde altı basamak
- tire (isteğe bağlı)
- iki harfli doğum yeri kodu
- tire (isteğe bağlı)
- üç rastgele basamak
- tek basamaklı cinsiyet kodu

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_malaysia_id_card_number desenle eşleşen içeriği bulur.
- Keyword_malaysia_id_card_number anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- dijital uygulama kartı
- i/c
- i/c hayır
- ıc
- ic no
- kimlik kartı
- kimlik kartı
- kimlik kartı
- k/p
- k/p no
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malaysia
- kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- malezya kimlik kartı
- malezya kimlik kartı
- nric
- kişisel kimlik kartı

## <a name="malta-drivers-license-number"></a>Malta ehliyet numarası

### <a name="format"></a>Biçim

Belirtilen desende iki karakter ve altı basamak birleşimi

### <a name="pattern"></a>Desen

iki karakter ve altı basamak birleşimi:

- iki karakter (büyük/küçük harfe duyarlı değil basamaklar veya harfler)
- boşluk (isteğe bağlı)
- üç basamak
- boşluk (isteğe bağlı)
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_malta_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_malta_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver s_license_number

- liċenzja tas-sewqan
- liċenzji tas-sewwieq

## <a name="malta-identity-card-number"></a>Malta kimlik kartı numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

yedi basamak ve ardından bir harf

### <a name="pattern"></a>Desen

yedi basamak ve ardından bir harf:

- yedi basamak
- "M, G, A, P, L, H, B, Z" içinde bir harf (büyük/küçük harfe duyarsız)

### <a name="checksum"></a>Sağlama toplamı

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_malta_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_malta_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Normal ifade `Regex_malta_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- vatandaş hizmet numarası
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- kişisel sayısal kod
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- uniqueidentityno #

## <a name="malta-passport-number"></a>Malta pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen yedi basamak

### <a name="pattern"></a>Desen

yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_malta_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_malta_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- 'den `Keywords_eu_passport_date` bir anahtar sözcük bulundu

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_malta_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_malta_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="malta-physical-addresses"></a>Malta fiziksel adresleri

Bu unbundled adlandırılmış varlık, Malta'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="malta-tax-identification-number"></a>Malta vergi kimlik numarası

### <a name="format"></a>Biçim

Malta uyruklular için:

- belirtilen düzende yedi basamak ve bir harf

Malta uyruklu olmayanlar ve Maltalı varlıklar:

- dokuz basamak

### <a name="pattern"></a>Desen

Malta uyruklular: yedi rakam ve bir harf

- yedi basamak
- bir harf (büyük/küçük harfe duyarlı değil)

Malta uyruklu olmayanlar ve Malta varlıkları: dokuz basamak

- dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex `Regex_malta_eu_tax_file_number`  veya `Regex_malta_eu_tax_file_number_non_maltese_national` desenle eşleşen içeriği bulur.
- 'den `Keywords_malta_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- Regex `Regex_malta_eu_tax_file_number` veya `Regex_malta_eu_tax_file_number_non_maltese_national` desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- vatandaş hizmet numarası
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- kişisel sayısal kod
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- uniqueidentityno #

## <a name="medical-specialities"></a>Tıbbi uzmanlıklar

Bu unbundled adlandırılmış varlık, *dermatoloji* gibi tıbbi uzmanlıklarla ilgili terimleri algılar.  Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="medicare-beneficiary-identifier-mbi-card"></a>Medicare Beneficiary Identifier (MBI) kartı

### <a name="format"></a>Biçim

11 karakter alfasayısal desen

### <a name="pattern"></a>Desen

- 1 ile 9 arasında bir basamak
- S, L, O, I, B, Z hariç bir harf
- S, L, O, I, B, Z hariç bir basamak veya harf
- bir basamak
- isteğe bağlı kısa çizgi
- S, L, O, I, B, Z hariç bir harf
- S, L, O, I, B, Z hariç bir basamak veya harf
- bir basamak
- isteğe bağlı kısa çizgi
- S, L, O, I, B, Z hariç iki harf
- iki basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_mbi_card` , desenle eşleşen içeriği bulur.
- 'den `Keyword_mbi_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_mbi_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- medicare hak sahibi #
- medicare hak sahibi tanımlayıcısı
- medicare hak sahibi hayır
- medicare hak sahibi numarası
- medicare hak sahibi #

## <a name="mexico-unique-population-registry-code-curp"></a>Meksika Benzersiz Nüfus Kayıt Defteri Kodu (CURP)

### <a name="format"></a>Biçim

18 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

- dört harf (büyük/küçük harfe duyarsız)
- geçerli bir tarihi gösteren altı basamak
- a letter - H/h veya M/m
- Geçerli bir Meksika eyalet kodunu gösteren iki harf
- üç harf
- bir harf veya rakam
- bir basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_mexico_population_registry_code` , desenle eşleşen içeriği bulur.
- 'den `Keyword_mexico_population_registry_code` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_mexico_population_registry_code` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Benzersiz Nüfus Kayıt Defteri Kodu
- benzersiz nüfus kodu
- CURP
- Kişisel Kimlik
- Benzersiz Kimlik
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave kişisel Identidad
- kişisel Identidad Clave
- ClaveÚnica
- claveunica
- clavepersonalIdentidad

## <a name="netherlands-citizens-service-bsn-number"></a>Hollanda vatandaşlık hizmeti (BSN) numarası

### <a name="format"></a>Biçim

isteğe bağlı boşluklar içeren sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

sekiz-dokuz basamak:

- üç basamak
- boşluk (isteğe bağlı)
- üç basamak
- boşluk (isteğe bağlı)
- iki-üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_netherlands_bsn desenle eşleşen içeriği bulur.
- Keyword_netherlands_bsn anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- burgerservicenummer
- vatandaş hizmet numarası
- kişi numarası
- kişisel numara
- kişisel sayısal kod
- kişiyle ilgili numara
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- sosyal-mali sayı
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Hollanda ehliyet numarası

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_netherlands_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_netherlands_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers

## <a name="netherlands-passport-number"></a>Hollanda pasaport numarası

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen dokuz harf veya basamak

### <a name="pattern"></a>Desen

dokuz harf veya rakam

### <a name="checksum"></a>Sağlama toplamı

geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_netherlands_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_netherlands_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_netherlands_eu_passport_date` tarihi DD AAA/AAA YYYY biçiminde bulur (Örnek - 26 MAA/MAR 2012)

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_netherlands_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_netherlands_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr

## <a name="netherlands-physical-addresses"></a>Hollanda fiziksel adresleri

Bu unbundled adlandırılmış varlık, Hollanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="netherlands-tax-identification-number"></a>Hollanda vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_netherlands_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_netherlands_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_netherlands_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- hollânske vergi tanımlaması
- hulandes impuesto kimlik numarası
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- impuesto kimlik numarası
- impuesto numarası
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- hollanda vergi tanımlaması
- hollanda vergi tanımlaması
- hollanda tenekesi
- hollanda'nın tenekesi
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi tanımlama tal
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- vergi tal
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="netherlands-value-added-tax-number"></a>Hollanda katma değer vergi numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

14 karakterli alfasayısal desen

### <a name="pattern"></a>Desen

14 karakterli alfasayısal desen:

- N veya n
- L veya ben
- isteğe bağlı boşluk, nokta veya kısa çizgi
- dokuz basamak
- isteğe bağlı boşluk, nokta veya kısa çizgi
- B veya b
- iki basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_netherlands_value_added_tax_number desenle eşleşen içeriği bulur.
- Keywords_netherlands_value_added_tax_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_netherlands_value_added_tax_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- kdv numarası
- kdv no
- Kdv #
- wearde tafoege tax getal
- btw nûmer
- btw-nummer

## <a name="new-zealand-bank-account-number"></a>Yeni Zelanda banka hesap numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

İsteğe bağlı sınırlayıcı ile 14 basamaklıdan 16 basamaklı desene

### <a name="pattern"></a>Desen

İsteğe bağlı sınırlayıcı ile 14 basamaklıdan 16 basamaklı desene:

- iki basamak
- isteğe bağlı kısa çizgi veya boşluk
- üç-dört basamak
- isteğe bağlı kısa çizgi veya boşluk
- yedi basamak
- isteğe bağlı kısa çizgi veya boşluk
- iki ile üç basamak
- seçenekler kısa çizgi veya boşluk

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_new_zealand_bank_account_number desenle eşleşen içeriği bulur.
- Keywords_new_zealand_bank_account_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_new_zealand_bank_account_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- hesap numarası
- banka hesabı
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr

## <a name="new-zealand-drivers-license-number"></a>Yeni Zelanda ehliyet numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz karakterli alfasayısal desen

### <a name="pattern"></a>Desen

sekiz karakterli alfasayısal desen

- iki harf
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_newzealand_driver_license_number desenle eşleşen içeriği bulur.
- Keywords_newzealand_driver_license_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_newzealand_driver_license_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü #
- driverlics #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- uluslararası sürüş izni
- uluslararası sürüş izinleri
- nz automobile association
- new zealand automobile association

## <a name="new-zealand-inland-revenue-number"></a>Yeni Zelanda iç gelir numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

isteğe bağlı sınırlayıcılarla sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

isteğe bağlı sınırlayıcılarla sekiz veya dokuz basamak

- iki veya üç basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- üç basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_new_zealand_inland_revenue_number desenle eşleşen içeriği bulur.
- Keywords_new_zealand_inland_revenue_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_new_zealand_inland_revenue_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird hayır.
- ird no #
- nz ird
- yeni zelanda ird
- ird numarası
- iç gelir numarası

## <a name="new-zealand-ministry-of-health-number"></a>Yeni Zelanda sağlık bakanlığı numarası

### <a name="format"></a>Biçim

üç harf ve dört basamak

### <a name="pattern"></a>Desen

- 'I' ve 'O' dışında üç harf (büyük/küçük harfe duyarlı değil)
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_new_zealand_ministry_of_health_number desenle eşleşen içeriği bulur.
- Keyword_nz_terms anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_new_zealand_ministry_of_health_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Yeni Zelanda
- Ulusal Sağlık Endeksi
- NHI #
- Ulusal Sağlık Endeksi #

## <a name="new-zealand-physical-addresses"></a>Yeni Zelanda fiziksel adresleri

Bu unbundled adlandırılmış varlık, Yeni Zelanda'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="new-zealand-social-welfare-number"></a>Yeni Zelanda sosyal yardım numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
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

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_newzealand_social_welfare_number desenle eşleşen içeriği bulur.
- Keywords_newzealand_social_welfare_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_newzealand_social_welfare_number desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- sosyal yardım #
- sosyal yardım #
- sosyal yardım no.
- sosyal yardım numarası
- swn #

## <a name="norway-identification-number"></a>Norveç kimlik numarası

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

11 basamak:

- doğum tarihi olan DDMMYY biçiminde altı basamak
- üç basamaklı tek tek sayı
- iki denetim basamağı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_norway_id_number desenle eşleşen içeriği bulur.
- Keyword_norway_id_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_norway_id_numbe desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Kişisel kimlik numarası
- Norveç kimlik numarası
- Kimlik Numarası
- Kimlik
- Personnummer
- Fødselsnummer

## <a name="norway-physical-addresses"></a>Norveç fiziksel adresleri

Bu unbundled adlandırılmış varlık, Norveç'ten gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

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
- bir basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_philippines_unified_id desenle eşleşen içeriği bulur.
- Keyword_philippines_id anahtar sözcüğü bulunur.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Birleşik Çok Amaçlı Kimlik
- UMID
- Kimlik Kartı
- Pinag-isang Multi-Layunin Kimliği

## <a name="poland-drivers-license-number"></a>Polonya ehliyet numarası

### <a name="format"></a>Biçim

İki eğik çizgi içeren 14 basamak

### <a name="pattern"></a>Desen

14 basamak ve iki eğik çizgi:

- beş basamak
- eğik çizgi
- iki basamak
- eğik çizgi
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_poland_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_poland_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver s_license_number

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Polonya kimlik kartı

### <a name="format"></a>Biçim

üç harf ve altı basamak

### <a name="pattern"></a>Desen

üç harf (büyük/küçük harfe duyarlı değil) ve ardından altı basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_polish_national_id desenle eşleşen içeriği bulur.
- Keyword_polish_national_id_passport_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tożsamości
- Dowód Tożsamości
- Dow. Os.

## <a name="poland-national-id-pesel"></a>Polonya ulusal kimliği (PESEL)

### <a name="format"></a>Biçim

11 basamak

### <a name="pattern"></a>Desen

- YYMMDD biçiminde doğum tarihini temsil eden altı basamak
- dört basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_pesel_identification_number desenle eşleşen içeriği bulur.
- Keyword_pesel_identification_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_pesel_identification_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tożsamości narodowej

## <a name="poland-passport-number"></a>Polonya pasaport numarası

Bu hassas bilgi türü varlığı AB Pasaport Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

iki harf ve yedi basamak

### <a name="pattern"></a>Desen

İki harf (büyük/küçük harfe duyarlı değil) ve ardından yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_polish_passport_number_v2` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.
- veya `Keyword_polish_national_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- 'den `Keywords_eu_passport_date` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_polish_passport_number_v2` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.
- veya `Keyword_polish_national_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_polish_passport_number_v2` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- Nr. paszportu
- nr paszportów
- n° geçiş noktası
- passport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="poland-physical-addresses"></a>Polonya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Polonya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="poland-regon-number"></a>Polonya REGON numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

9 basamaklı veya 14 basamaklı sayı

### <a name="pattern"></a>Desen

dokuz basamaklı veya 14 basamaklı sayı:

- dokuz basamak veya
- dokuz basamak
- Tire
- beş basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_polish_regon_number desenle eşleşen içeriği bulur.
- Keywords_polish_regon_number anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_polish_regon_number desenle eşleşen içeriği bulur.

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
### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon id
- istatistiksel sayı
- istatistiksel kimlik
- istatistiksel hayır
- regon sayısı
- regonid #
- regonno #
- şirket kimliği
- şirket kimliği #
- companyidno #
- sayı statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #

## <a name="poland-tax-identification-number"></a>Polonya vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı içermeyen 11 basamak

### <a name="pattern"></a>Desen

11 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_poland_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_poland_eu_tax_file_number` bir anahtar sözcük bulunur.

```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- Nip #
- Nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- kdv kimliği #
- kdv kimliği
- kdv no
- kdv numarası
- vatid #
- vatid
- vatno #

## <a name="portugal-citizen-card-number"></a>Portekiz vatandaşı kart numarası

### <a name="format"></a>Biçim

sekiz basamak

### <a name="pattern"></a>Desen

sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_portugal_citizen_card desenle eşleşen içeriği bulur.
- Keyword_portugal_citizen_card anahtar sözcüğü bulunur.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- vatandaş kartı
- belge numarası
- documento de identificação
- kimlik numarası
- tanımlama no
- kimlik numarası
- kimlik kartı no
- kimlik kartı numarası
- ulusal kimlik kartı
- Nıc
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi numarası

## <a name="portugal-drivers-license-number"></a>Portekiz ehliyet numarası

### <a name="format"></a>Biçim

iki desen - iki harf ve ardından özel karakterler içeren 5-8 basamak

### <a name="pattern"></a>Desen

Desen 1: İki harf ve ardından özel karakterlerle 5/6:

- İki harf (büyük/küçük harfe duyarlı değil)
- Kısa çizgi
- Beş veya Altı basamak
- Boşluk
- Bir basamak

Desen 2: Bir harf ve ardından özel karakterler içeren 6/8 basamak:

- Bir harf (büyük/küçük harfe duyarlı değil)
- Kısa çizgi
- Altı veya sekiz basamak
- Boşluk
- Bir basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_portugal_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_portugal_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver s_license_number

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução

## <a name="portugal-passport-number"></a>Portekiz pasaport numarası

### <a name="format"></a>Biçim

bir harf ve ardından boşluk veya sınırlayıcı içermeyen altı basamak

### <a name="pattern"></a>Desen

bir harf ve ardından altı basamak:

- bir harf (büyük/küçük harfe duyarlı değil)
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_portugal_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_portugal_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_portugal_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_portugal_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- portekiz pasaportu
- portekizce passport
- portekizce passaporte
- passaporte nº
- passport nº
- números de passaporte
- portekizce pasaportlar
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="portugal-physical-addresses"></a>Portekiz fiziksel adresleri

Bu unbundled adlandırılmış varlık, Portekiz'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="portugal-tax-identification-number"></a>Portekiz vergi kimlik numarası

### <a name="format"></a>Biçim

isteğe bağlı boşluklar içeren dokuz basamak

### <a name="pattern"></a>Desen

- üç basamak
- isteğe bağlı bir alan
- üç basamak
- isteğe bağlı bir alan
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_portugal_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_portugal_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_portugal_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- Cpf #
- Cpf
- Nif #
- Nif
- número de identificação fisca
- çok sayıda mali
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="romania-drivers-license-number"></a>Romanya ehliyet numarası

### <a name="format"></a>Biçim

bir karakter ve ardından sekiz basamak

### <a name="pattern"></a>Desen

bir karakter ve ardından sekiz basamak:

- bir harf (büyük/küçük harfe duyarlı değil) veya basamak
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_romania_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_romania_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver's_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere

## <a name="romania-passport-number"></a>Romanya pasaport numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen sekiz veya dokuz basamak

### <a name="pattern"></a>Desen

sekiz veya dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_romania_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_romania_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_romania_eu_passport_date` tarihi DD MMM/AAA YY biçiminde bulur (Örnek- 01 ŞUB/ŞUB 10) veya anahtar sözcüğü `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_romania_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_romania_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul kararılui numerele pașaportului Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="romania-personal-numeric-code-cnp"></a>Romanya kişisel sayısal kodu (CNP)

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 13 basamak

### <a name="pattern"></a>Desen

- 1-9 arasında bir basamak
- doğum tarihini temsil eden altı basamak (YYMMDD)
- 01-52 veya 99 olabilecek iki basamak
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_romania_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_romania_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_romania_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- Cnp #
- Cnp
- cod identificare personal
- cod sayısal kişisel
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- sigorta numarası
- insurancenumber #
- ulusal kimlik #
- ulusal kimlik
- ulusal kimlik numarası
- număr identificare personal
- număr identitate
- număr kişisel unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- kişisel sayısal kod
- Pin #
- Pin
- vergi dosyası no
- vergi dosyası numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-physical-addresses"></a>Romanya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Romanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="russia-passport-number-domestic"></a>Rusya pasaport numarası yurt içi

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

10 basamaklı sayı

### <a name="pattern"></a>Desen

10 basamaklı sayı:

- iki basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- iki basamak
- isteğe bağlı bir alan
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex Regex_Russian_Passport_Number_Domestic desenle eşleşen içeriği bulur.
- Keyword_Russian_Passport_Number anahtar sözcüğü bulunur.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- pasaport numarası
- pasaport no
- Pasaport #
- pasaport kimliği
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="russia-passport-number-international"></a>Rusya pasaport numarası uluslararası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

dokuz basamaklı sayı

### <a name="pattern"></a>Desen

dokuz basamaklı sayı:

- iki basamak
- isteğe bağlı bir boşluk veya kısa çizgi
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex Regex_Russian_Passport_Number_International desenle eşleşen içeriği bulur.
- Keyword_Russian_Passport_Number anahtar sözcüğü bulunur.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- pasaport numarası
- pasaport no
- Pasaport #
- pasaport kimliği
- passportno #
- passportnumber #
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

Ardışık 10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_saudi_arabia_national_id desenle eşleşen içeriği bulur.
- Keyword_saudi_arabia_national_id anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

- "F", "G", "M", "S" veya "T" harfi (büyük/küçük harfe duyarlı değildir)
- yedi basamak
- alfabetik denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade Regex_singapore_nric desenle eşleşen içeriği bulur.
- Keyword_singapore_nric anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_singapore_nric desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- Ulusal Kayıt Kimlik Kartı
- Kimlik Kartı Numarası
- NRIC
- IC
- Yabancı Kimlik Numarası
- FIN
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>Slovakya sürücü ehliyeti numarası

### <a name="format"></a>Biçim

bir karakter ve ardından yedi basamak

### <a name="pattern"></a>Desen

bir karakter ve ardından yedi basamak

- bir harf (büyük/küçük harfe duyarlı değil) veya basamak
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_slovakia_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovakia_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-passport-number"></a>Slovakya pasaport numarası

### <a name="format"></a>Biçim

sekiz veya dokuz karakterli alfasayısal desen

### <a name="pattern"></a>Desen

bir harf (büyük/küçük harfe duyarlı değil) ve ardından yedi basamak veya iki harf (büyük/küçük harfe duyarlı değil) ve ardından altı veya yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_slovakia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovakia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_slovakia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovakia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passport n°
- n° Geçiş Noktası

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="slovakia-personal-number"></a>Slovakya kişisel numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

isteğe bağlı ters eğik çizgi içeren dokuz veya 10 basamak

### <a name="pattern"></a>Desen

- doğum tarihini temsil eden altı basamak
- isteğe bağlı eğik çizgi (/)
- üç basamak
- isteğe bağlı bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_slovakia_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_slovakia_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_slovakia_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- doğum numarası
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- kimlik numarası
- tanımlama no
- kimlik numarası
- identifikačná karta č
- identifikačné číslo
- kimlik kartı no
- kimlik kartı numarası
- národná identifikačná značka č
- ulusal sayı
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- sosyal güvenlik numarası
- ssn #
- ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- vergi dosyası no
- vergi dosyası numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="slovakia-physical-addresses"></a>Slovakya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Slovakya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="slovenia-drivers-license-number"></a>Slovenya ehliyet numarası

### <a name="format"></a>Biçim

boşluk ve sınırlayıcı içermeyen dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_slovenia_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovenia_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
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

boşluk veya sınırlayıcı içermeyen iki harf ve ardından yedi basamak

### <a name="pattern"></a>Desen

iki harf ve ardından yedi basamak:

- "P" harfi
- bir büyük harf
- yedi basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_slovenia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovenia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_eu_passport_date1` tarihi DD.AA.YYYY biçiminde bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_slovenia_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_slovenia_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- potni listesi #
- datum rojstva
- potni listesi
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="slovenia-physical-addresses"></a>Slovenya fiziksel adresleri

Bu unbundled adlandırılmış varlık, Slovenya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="slovenia-tax-identification-number"></a>Slovenya vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

boşluk veya sınırlayıcı içermeyen sekiz basamak

### <a name="pattern"></a>Desen

- 1-9 arasında bir basamak
- altı basamak
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_slovenia_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_slovenia_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_slovenia_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- vergi dosyası no
- vergi dosyası numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="slovenia-unique-master-citizen-number"></a>Slovenya Benzersiz Ana Vatandaş Numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk veya sınırlayıcı içermeyen 13 basamak

### <a name="pattern"></a>Desen

Belirtilen desende 13 basamak:

- doğum tarihine (DDMMLLL) karşılık gelen yedi basamak; burada "LLL" doğum yılının son üç basamağını ifade eder
- doğum alanına karşılık gelen iki basamak "50"
- aynı gün doğan kişiler için cinsiyet ve seri numarasının birleşimine karşılık gelen üç basamak. Erkek için 000-499, kadın için 500-999.
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_slovenia_eu_national_id_card` , desenle eşleşen içeriği bulur.
- 'den `Keywords_slovenia_eu_national_id_card` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_slovenia_eu_national_id_card` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- kimlik kartı
- kimlik numarası
- identifikacijska številka
- kimlik kartı
- nacionalna id
- nacionalni potni list
- ulusal kimlik
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- kişisel kod
- kişisel numara
- kişisel sayısal kod
- številka državljana
- benzersiz vatandaş numarası
- benzersiz kimlik numarası
- benzersiz kimlik numarası
- benzersiz ana vatandaş numarası
- benzersiz kayıt numarası
- uniqueidentityno #
- uniqueidentityno #

## <a name="south-africa-identification-number"></a>Güney Afrika kimlik numarası

### <a name="format"></a>Biçim

Boşluk içerebilen 13 basamak

### <a name="pattern"></a>Desen

13 basamak:

- doğum tarihi olan YYMMDD biçiminde altı basamak
- dört basamak
- tek basamaklı vatandaşlık göstergesi
- "8" veya "9" rakamı
- sağlama toplamı olan bir basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_south_africa_identification_number desenle eşleşen içeriği bulur.
- Keyword_south_africa_identification_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Kimlik kartı
- Kimlik
- Kimlik

## <a name="south-korea-resident-registration-number"></a>Güney Kore ikamet kayıt numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 13 basamak

### <a name="pattern"></a>Desen

13 basamak:

- doğum tarihi olan YYMMDD biçiminde altı basamak
- kısa çizgi
- yüzyıla ve cinsiyete göre belirlenen bir rakam
- dört basamaklı doğum bölgesi kodu
- önceki sayıların özdeş olduğu kişileri ayırt etmek için kullanılan bir basamak
- onay basamalı.

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_south_korea_resident_number desenle eşleşen içeriği bulur.
- Keyword_south_korea_resident_number anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_south_korea_resident_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- Ulusal kimlik kartı
- Vatandaşın Kayıt Numarası
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-dni"></a>İspanya DNI

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz basamak ve ardından bir karakter

### <a name="pattern"></a>Desen

yedi basamak ve ardından bir karakter

- sekiz basamak
- İsteğe bağlı bir boşluk veya kısa çizgi
- bir onay harfi (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_spain_eu_DL_and_NI_number_citizen` veya `Func_spain_eu_DL_and_NI_number_foreigner` desenle eşleşen içeriği bulur.
- 'den `Keywords_spain_eu_national_id_card"` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_spain_eu_DL_and_NI_number_citizen` veya `Func_spain_eu_DL_and_NI_number_foreigner` desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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
- Nie #
- Nie
- nienúmero #
- número de identificación
- número nacional identidad
- kişisel kimlik numarası
- kişisel kimlik no
- benzersiz kimlik numarası
- Uniqueıd #

## <a name="spain-drivers-license-number"></a>İspanya ehliyet numarası

### <a name="format"></a>Biçim

sekiz basamak ve ardından bir karakter

### <a name="pattern"></a>Desen

sekiz basamak ve ardından bir karakter:

- sekiz basamak
- bir basamak veya harf (büyük/küçük harfe duyarlı değil)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_spain_eu_DL_and_NI_number_citizen` veya `Func_spain_eu_DL_and_NI_number_foreigner` desenle eşleşen içeriği bulur.
- veya `Keywords_spain_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_spain_eu_DL_and_NI_number_citizen` veya `Func_spain_eu_DL_and_NI_number_foreigner` desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver s_license_number

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

boşluk veya sınırlayıcı içermeyen sekiz veya dokuz karakterlik harf ve sayıların birleşimi

### <a name="pattern"></a>Desen

harflerin ve sayıların sekiz veya dokuz karakterlik bir birleşimi:

- iki basamak veya harf
- bir basamak veya harf (isteğe bağlı)
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Geçerli değil

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade `Regex_spain_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_spain_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- Normal ifade `Regex_spain_eu_passport_date` tarihi DD-AA-YYYY biçiminde bulur veya bir anahtar sözcük `Keywords_eu_passport_date` bulunur

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_spain_eu_passport_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_spain_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passport n°
- n° Geçiş Noktası
- pasaporte no.
- pasaporte n°
- İspanya pasaportu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="spain-physical-addresses"></a>İspanya fiziksel adresleri

Bu unbundled adlandırılmış varlık, İspanya'dan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="spain-social-security-number-ssn"></a>İspanya sosyal güvenlik numarası (SSN)

### <a name="format"></a>Biçim

11-12 basamak

### <a name="pattern"></a>Desen

11-12 basamak:

- iki basamak
- eğik çizgi (isteğe bağlı)
- yedi ila sekiz basamak
- eğik çizgi (isteğe bağlı)
- iki basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_spanish_social_security_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.
- - 'den `Keywords_spain_eu_ssn_or_equivalent` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_spanish_social_security_number desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- sosyal güvenlik hayır
- sosyal güvenlik numarası
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>İspanya vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

belirtilen düzende yedi veya sekiz basamak ve bir veya iki harf

### <a name="pattern"></a>Desen

İspanya Ulusal Kimlik Kartı olan İspanyol Gerçek Kişiler:

- sekiz basamak
- bir büyük harf (büyük/küçük harfe duyarlı)

İspanya Ulusal Kimlik Kartı olmayan yerleşik olmayan İspanyollar

- bir büyük harf "L" (büyük/küçük harfe duyarlı)
- yedi basamak
- bir büyük harf (büyük/küçük harfe duyarlı)

İspanya Ulusal Kimlik Kartı olmayan 14 yaşın altındaki yerleşik İspanyollar:

- bir büyük harf "K" (büyük/küçük harfe duyarlı)
- yedi basamak
- bir büyük harf (büyük/küçük harfe duyarlı)

Yabancı Kimlik Numarası olan Yabancılar

- "X", "Y" veya "Z" (büyük/küçük harfe duyarlı) olan bir büyük harf
- yedi basamak
- bir büyük harf (büyük/küçük harfe duyarlı)

Yabancı Kimlik Numarası Olmayan Yabancılar

- "M" olan bir büyük harf (büyük/küçük harfe duyarlı)
- yedi basamak
- bir büyük harf (büyük/küçük harfe duyarlı)

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_spain_eu_tax_file_number` veya `Func_spain_eu_DL_and_NI_number_citizen` desenle eşleşen içeriği bulur.
- 'den `Keywords_spain_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_spain_eu_tax_file_number` veya `Func_spain_eu_DL_and_NI_number_citizen` desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Cıf
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- İspanyolca #
- İspanyolca
- spanishcifno #
- spanishcifno
- vergi dosyası no
- vergi dosyası numarası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="sql-server-connection-string"></a>bağlantı dizesini SQL Server

### <a name="format"></a>Biçim

"Kullanıcı Kimliği", "Kullanıcı Kimliği", "uid" veya "UserId" dizesi ve ardından aşağıdaki desende özetlenen karakterler ve dizeler.

### <a name="pattern"></a>Desen

- "Kullanıcı Kimliği", "Kullanıcı Kimliği", "uid" veya "UserId" dizesi
- 1-200 arasında küçük veya büyük harf, rakam, simge, özel karakter veya boşluk birleşimi
- "Password" veya "pwd" dizesinde "pwd" harfinin önüne küçük harf eklenmez
- eşittir işareti (=)
- dolar işareti ($), yüzde simgesi (%), simgeden büyük (>), simge (@), tırnak işareti ("), noktalı virgül (;), sol ayraç([) veya sol köşeli ayraç ({) olmayan herhangi bir karakter
- noktalı virgül (;), eğik çizgi (/) veya tırnak işareti (") olmayan 7-128 karakterden oluşan herhangi bir birleşim
- noktalı virgül (;) veya tırnak işareti (")

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- Normal ifade CEP_Regex_SQLServerConnectionString desenle eşleşen içeriği bulur.
- CEP_GlobalFilter anahtar sözcüğü bulunamadı.
- Normal ifade CEP_PasswordPlaceHolder desenle eşleşen içeriği bulmaz.
- Normal ifade CEP_CommonExampleKeywords desenle eşleşen içeriği bulmaz.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- bazı parolalar
- somepassword
- secretPassword
- Örnek

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Bu hassas bilgi türü, bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.

- Parola veya pwd ve ardından 0-2 boşluk, eşittir işareti (=), 0-2 boşluk ve yıldız (*) -OR-
- Parola veya pwd ve ardından:
    - Eşittir işareti (=)
    - Küçüktür simgesi (<)
    - Büyük veya küçük harf, basamak, yıldız işareti (*), kısa çizgi (-), altı çizili (_) veya boşluk karakteri olan 1-200 karakterden oluşan herhangi bir birleşim
    - Büyüktür simgesi (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Bu hassas bilgi türü, bu anahtar sözcükleri anahtar sözcük listesi değil normal bir ifade kullanarak tanımlar.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net

## <a name="surgical-procedures"></a>Cerrahi prosedürler

Bu unbundled adlı varlık, *apandisektomi* gibi cerrahi prosedürlerle ilgili terimleri algılar.  Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="sweden-drivers-license-number"></a>İsveç ehliyet numarası

### <a name="format"></a>Biçim

Kısa çizgi içeren 10 basamak

### <a name="pattern"></a>Desen

Kısa çizgi içeren 10 basamak:

- altı basamak
- kısa çizgi
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade `Regex_sweden_eu_driver's_license_number` , desenle eşleşen içeriği bulur.
- veya `Keywords_sweden_eu_driver's_license_number` anahtar `Keywords_eu_driver's_license_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver s_license_number

- ajokortti
- permis de conducere
- ajokortin çok
- kuljettajat lic.
- drivere lic.
- körkort
- numărul permisului de conducere
- שאָפער דערלויבעניש נומער
- förare lic.
- דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>İsveç ulusal kimliği

### <a name="format"></a>Biçim

10 veya 12 basamak ve isteğe bağlı sınırlayıcı

### <a name="pattern"></a>Desen

10 veya 12 basamak ve isteğe bağlı sınırlayıcı:

- iki basamak (isteğe bağlı)
- YYMMDD tarih biçiminde altı basamak
- "-" veya "+" sınırlayıcısı (isteğe bağlı)
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_swedish_national_identifier` , desenle eşleşen içeriği bulur.
- 'den `Keywords_swedish_national_identifier` bir anahtar sözcük bulundu
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_swedish_national_identifier` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- kimlik no
- kimlik numarası
- Kimliği #
- tanımlama no
- kimlik numarası
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- kimlik belgesi
- kimlik no
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

ardışık sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- normal ifade Regex_sweden_passport_number desenle eşleşen içeriği bulur.
- veya `Keyword_sweden_passport` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- normal ifade `Regex_sweden_eu_passport_date` DD MMM/AAA YY (01 OCA/JAN 12) biçiminde bir tarih bulur veya bir `Keywords_eu_passport_date` anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- normal ifade Regex_sweden_passport_number desenle eşleşen içeriği bulur.
- veya `Keyword_sweden_passport` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- yabancı kayıt kartı
- g3 işleme ücretleri
- birden çok giriş
- Numéro de passport
- passport n °
- passport non
- passport #
- passport #
- passportnon
- passportn °
- passnummer
- nr'ı geç
- schengen vizesi
- schengen vizeleri
- tek girdi
- sverige pass
- vize gereksinimleri
- vize işleme
- vize türü

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- sorun tarihi
- süre sonu tarihi

## <a name="sweden-physical-addresses"></a>İsveç fiziksel adresleri

Bu unbundled adlandırılmış varlık, İsveç'ten gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="sweden-tax-identification-number"></a>İsveç vergi kimlik numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Belirtilen desende 10 basamak ve bir simge

### <a name="pattern"></a>Desen

10 basamak ve bir simge:

- doğum tarihine karşılık gelen altı basamak (YYMMDD)
- artı işareti veya eksi işareti
- kimlik numarasını benzersiz hale getiren üç basamak:
  - 1990'den önce verilen sayılar için yedinci ve sekizinci basamak, doğum ilçesini veya yabancı doğumlu kişileri tanımlar
  - dokuzuncu konumdaki rakam, cinsiyeti erkek için tek, hatta kadın için gösterir
- bir denetim basamalı

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_sweden_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_sweden_eu_tax_file_number` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_sweden_eu_tax_file_number` , desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- kişisel kimlik numarası
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- sverige tenekesi
- vergi dosyası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi numarası
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="swift-code"></a>SWIFT kodu

### <a name="format"></a>Biçim

dört harf ve ardından 5-31 harf veya rakam

### <a name="pattern"></a>Desen

dört harf ve ardından 5-31 harf veya rakam:

- dört harfli banka kodu (büyük/küçük harfe duyarlı değildir)
- isteğe bağlı bir alan
- 4-28 harf veya rakam (Temel Banka Hesap Numarası (BBAN))
- isteğe bağlı bir alan
- bir ile üç harf veya basamak (BBAN'ın geri kalanı)

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_swift desenle eşleşen içeriği bulur.
- Keyword_swift anahtar sözcüğü bulunur.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_swift"></a>Keyword_swift

- standardizasyon için uluslararası kuruluş 9362
- iso 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- swift kodu
- swift numarası #
- swift yönlendirme numarası
- bic numarası
- bic kodu
- Bıc #
- Bıc #
- banka tanımlayıcı kodu
- Organizasyon internationale de normalisation 9362
- rapide #
- kod SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
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

Bu unbundled adlandırılmış varlık, İsviçre'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="switzerland-ssn-ahv-number"></a>İsviçre SSN AHV numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

13 basamaklı sayı

### <a name="pattern"></a>Desen

13 basamaklı sayı:

- üç basamak - 756
- isteğe bağlı nokta
- dört basamak
- isteğe bağlı nokta
- dört basamak
- isteğe bağlı nokta
- iki basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_swiss_social_security_number_ahv desenle eşleşen içeriği bulur.
- Keywords_swiss_social_security_number_ahv anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_swiss_social_security_number_ahv desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- Pıd
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
- einzigartige identität nicht
- sozialversicherungsnummer
- kimlik personel kimliği
- numéro de sécurité sociale

## <a name="taiwan-national-identification-number"></a>Tayvan ulusal kimlik numarası

### <a name="format"></a>Biçim

bir harf (İngilizce) ve ardından dokuz basamak

### <a name="pattern"></a>Desen

bir harf (İngilizce) ve ardından dokuz basamak:

- bir harf (büyük/küçük harfe duyarlı değil İngilizce)
- "1" veya "2" rakamı
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_taiwanese_national_id desenle eşleşen içeriği bulur.
- Keyword_taiwanese_national_id anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_taiwanese_national_id desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

- biyometrik pasaport numarası: dokuz basamak
- biyometrik olmayan pasaport numarası: dokuz basamak

### <a name="pattern"></a>Desen
biyometrik pasaport numarası:

- "3" karakteri
- sekiz basamak

biyometrik olmayan pasaport numarası:

- dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_taiwan_passport desenle eşleşen içeriği bulur.
- Keyword_taiwan_passport anahtar sözcüğü bulunur.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC pasaport numarası
- Pasaport numarası
- Pasaport no
- Passport Num
- Pasaport #
- 护照
- 中華民國護照
- Zhônghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>Tayvan'da yerleşik sertifika (ARC/TARC) numarası

### <a name="format"></a>Biçim

10 harf ve rakam

### <a name="pattern"></a>Desen

10 harf ve rakam:

- iki harf (büyük/küçük harfe duyarlı değil)
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_taiwan_resident_certificate desenle eşleşen içeriği bulur.
- Keyword_taiwan_resident_certificate anahtar sözcüğü bulunur.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Yerleşik Sertifika
- Resident Cert
- Yerleşik Sertifika.
- Kimlik kartı
- Yabancı Yerleşik Sertifika
- ARC
- Tayvan Alan Yerleşik Sertifikası
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證

## <a name="thai-population-identification-code"></a>Tay nüfus tanımlama kodu

### <a name="format"></a>Biçim

13 basamak

### <a name="pattern"></a>Desen

13 basamak:

- ilk basamak sıfır veya dokuz değil
- 12 basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_Thai_Citizen_Id desenle eşleşen içeriği bulur.
- Keyword_Thai_Citizen_Id anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_Thai_Citizen_Id desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

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

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_Turkish_National_Id desenle eşleşen içeriği bulur.
- Keyword_Turkish_National_Id anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_Turkish_National_Id desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik sn.
- Vatandaşlık sn.
- Vatandaşlık no

## <a name="turkey-physical-addresses"></a>Türkiye fiziksel adresleri

Bu unbundled adlı varlık, Türkiye'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="types-of-medication"></a>İlaç türleri

Bu unbundled adlı varlık *, insülin* gibi ilaç adlarını algılar.  Yalnızca İngilizce terimleri destekler. Ayrıca entity SIT adlı [tüm tıbbi hüküm ve koşullar](#all-medical-terms-and-conditions) paketinde yer alır.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Yüksek

## <a name="uk-drivers-license-number"></a>INGİLTERE. ehliyet numarası

### <a name="format"></a>Biçim

Belirtilen biçimdeki 18 harf ve basamak birleşimi

### <a name="pattern"></a>Desen

18 harf ve rakam:

- Harf yerine beş harf (büyük/küçük harfe duyarlı değil) veya "9" rakamı.
- Bir basamak.
- Doğum tarihi için MMDDY tarih biçiminde beş basamak. Sürücü kadınsa yedinci karakter 50 artırılır; örneğin, 01 ile 12 yerine 51 - 62.
- Harf yerine iki harf (büyük/küçük harfe duyarlı değil) veya "9" rakamı.
- Beş basamak.

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_uk_drivers_license` , desenle eşleşen içeriği bulur.
- 'den `Keywords_eu_driver's_license_number` bir anahtar sözcük bulunur.
- Sağlama toplamı geçer.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_uk_drivers_license` , desenle eşleşen içeriği bulur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- sürücü
- driverlics
- driverlicense
- sürücü lisansları
- sürücülik
- driverlicences
- sürücü lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücüler
- sürücüler
- sürücüler
- sürücüler
- driverslicense
- sürücü lisansları
- sürücüler lic
- sürücüler lics
- sürücü lisansı
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- driver'lic
- driver'lics
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'lic
- sürücü lisansları
- sürücü lisansı
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- driver'slic
- sürücü dilimleri
- driver'slicense
- driver'slicenses
- sürücü dilimi
- sürücü dilimleri
- sürücü lic
- sürücü lics
- sürücü belgesi
- sürücü lisansları
- sürücü belgesi
- sürücü lisansları
- Dl #
- Dls #
- sürücü #
- driverlics #
- driverlicense #
- sürücü lisansları #
- sürücülik #
- driverlicences #
- sürücü lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- driverslicense #
- sürücü lisansları #
- sürücüler #
- sürücüler #
- sürücüler lic #
- sürücüler lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- driver'lic #
- driver'lics #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'lic #
- sürücü lisansları #
- sürücü lisansı #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- driver'slic #
- sürücü dilimleri #
- driver'slicense #
- driver'slicenses #
- sürücü dilimi #
- sürücü dilimleri #
- sürücü lic #
- sürücü lics #
- sürücü belgesi #
- sürücü lisansları #
- sürücü belgesi #
- sürücü lisansları #
- Ehliyet
- Ehliyet
- dlno #
- driv lic
- driv licen
- driv lisansı
- driv lisansları
- driv lisansı
- driv lisansları
- sürücü lisans
- sürücüler lisans
- sürücü lisans
- sürüş lic
- sürüş licen
- sürücü lisansları
- Ehliyet
- ehliyetler
- sürüş izni
- dl no
- dlno
- dl numarası

## <a name="uk-electoral-roll-number"></a>INGİLTERE. seçim rulosu numarası

### <a name="format"></a>Biçim

iki harf ve ardından 1-4 basamak

### <a name="pattern"></a>Desen

iki harf (büyük/küçük harfe duyarlı değil) ve ardından 1-4 sayı

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_uk_electoral desenle eşleşen içeriği bulur.
- Keyword_uk_electoral anahtar sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- konsey adaylığı
- adaylık formu
- seçmen kaydı
- seçim rulosu

## <a name="uk-national-health-service-number"></a>INGİLTERE. ulusal sağlık hizmeti numarası

### <a name="format"></a>Biçim

Boşluklarla ayrılmış 10-17 basamak

### <a name="pattern"></a>Desen

10-17 basamak:

- 3 veya 10 basamak
- boşluk
- üç basamak
- boşluk
- dört basamak

### <a name="checksum"></a>Sağlama toplamı

Evet

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_uk_nhs_number desenle eşleşen içeriği bulur.
- Aşağıdakilerden biri doğrudur:
    - Keyword_uk_nhs_number anahtar sözcüğü bulunur.
    - Keyword_uk_nhs_number1 anahtar sözcüğü bulunur.
    - Keyword_uk_nhs_number_dob anahtar sözcüğü bulunur.
- Sağlama toplamı geçer.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- ulusal sağlık hizmeti
- Nhs
- sağlık hizmetleri yetkilisi
- sistem durumu yetkilisi

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- hasta kimliği
- hasta belirleme
- hasta hayır
- hasta numarası

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Doğum tarihi
- Doğum Tarihi

## <a name="uk-national-insurance-number-nino"></a>INGİLTERE. ulusal sigorta numarası (NINO)

Bu hassas bilgi türü varlığı AB Ulusal Kimlik Numarası hassas bilgi türüne dahil edilir. Tek başına hassas bilgi türü varlığı olarak da kullanılabilir.

### <a name="format"></a>Biçim

boşluk veya tirelerle ayrılmış yedi karakter veya dokuz karakter

### <a name="pattern"></a>Desen

iki olası desen:

- iki harf (geçerli NINO'lar bu ön ekte yalnızca belirli karakterler kullanır; bu desen bunu doğrular; büyük/küçük harfe duyarlı değildir)
- altı basamak
- 'A', 'B', 'C' veya 'D' (ön ek gibi, son ekte yalnızca belirli karakterlere izin verilir; büyük/küçük harfe duyarlı değildir)

VEYA

- iki harf
- boşluk veya tire
- iki basamak
- boşluk veya tire
- iki basamak
- boşluk veya tire
- iki basamak
- boşluk veya tire
- 'A', 'B', 'C' veya 'D'

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_uk_nino desenle eşleşen içeriği bulur.
- Keyword_uk_nino anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_uk_nino desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- ulusal sigorta numarası
- ulusal sigorta katkıları
- koruma eylemi
- Sigorta
- sosyal güvenlik numarası
- sigorta uygulaması
- tıbbi uygulama
- sosyal sigorta
- tıbbi müdahale
- sosyal güvenlik
- Ingiltere
- NI Numarası
- NI Hayır.
- NI #
- NI #
- Sigorta #
- insurancenumber
- ulusal dayanıklılık #
- nationalinsurancenumber

## <a name="uk-physical-addresses"></a>INGİLTERE. fiziksel adresler

Bu unbundled adlandırılmış varlık, Birleşik Krallık'tan gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="uk-unique-taxpayer-reference-number"></a>INGİLTERE. Benzersiz Vergi Mükellefi Başvuru Numarası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

Boşluk ve sınırlayıcı içermeyen 10 basamak

### <a name="pattern"></a>Desen

10 basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev `Func_uk_eu_tax_file_number` , desenle eşleşen içeriği bulur.
- 'den `Keywords_uk_eu_tax_file_number` bir anahtar sözcük bulunur.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- vergi numarası
- vergi dosyası
- vergi kimliği
- vergi tanımlama no
- vergi kimlik numarası
- vergi no #
- vergi no
- vergi kayıt numarası
- taksiye bindi #
- taxidno #
- taxidnumber #
- taxno #
- vergi numarası #
- vergi numarası
- teneke kimlik
- tin no
- Teneke #

## <a name="us-bank-account-number"></a>ABD banka hesap numarası

### <a name="format"></a>Biçim

6-17 basamak

### <a name="pattern"></a>Desen

6-17 ardışık basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_usa_bank_account_number desenle eşleşen içeriği bulur.
- Keyword_usa_Bank_Account anahtar sözcüğü bulunur.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Hesap Numarası Denetleniyor
- Hesap Denetleniyor
- Hesap Denetleniyor #
- Acct Numarası Denetleniyor
- Acct Denetleniyor #
- Tahakkuk No denetleniyor.
- Hesap No denetleniyor.
- Banka Hesap Numarası
- Banka Hesabı #
- Banka Tahakkuk Numarası
- Banka Hesabı #
- Banka Tahakkuk No
- Banka Hesabı No.
- Tasarruf Hesabı Numarası
- Tasarruf Hesabı.
- Tasarruf Hesabı #
- TasarrufLar Acct Numarası
- TasarrufLar Acct #
- TasarrufLar Tahakkuk No
- Tasarruf Hesabı No.
- Banka Hesabı Numarası
- Borç Hesabı
- Borç Hesabı #
- Borç Tahakkuk Numarası
- Borç Hesabı #
- Borç Tahakkuk No
- Borç Hesabı No

## <a name="us-drivers-license-number"></a>ABD ehliyet numarası

### <a name="format"></a>Biçim

Duruma bağlıdır

### <a name="pattern"></a>Desen

eyalete bağlıdır; örneğin, New York:

- ddd ddd ddd gibi biçimlendirilmiş dokuz basamak eşleşir.
- ddd gibi dokuz basamak eşleşmez.

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_new_york_drivers_license_number desenle eşleşen içeriği bulur.
- Keyword_[state_name]_drivers_license_name anahtar sözcüğü bulundu.
- Keyword_us_drivers_license anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_new_york_drivers_license_number desenle eşleşen içeriği bulur.
- Keyword_[state_name]_drivers_license_name anahtar sözcüğü bulundu.
- Keyword_us_drivers_license_abbreviations anahtar sözcüğü bulunur.
- Keyword_us_drivers_license anahtar sözcüğü bulunamadı.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- Kimlik
- Kimlik
- DL #
- DLS #
- CDL #
- CDLS #
- KİMLİĞİ #
- Kimlik #
- Kimlik numarası
- Kimlik numaraları
- LİSANSI
- LİSANSI #
- DLN

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Sürücü Lic
- Sürücü Lics
- Sürücü Lisansı
- Sürücü Lisansları
- DriversLic
- DriversLics
- DriversLicense
- DriversLicenses
- Sürücüler Lic
- Sürücüler Lics
- Sürücü Lisansı
- Sürücü Lisansları
- Driver'Lic
- Driver'Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Driver' Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Sürücü Lisansları
- Sürücü Lic
- Sürücü Lics
- Sürücü Belgesi
- Sürücü Lisansları
- kimlik numarası
- kimlik numaraları
- Kimlik #
- kimlik kartı
- kimlik kartları
- kimlik kartı
- kimlik kartları
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- Sürücü Lic #
- Sürücü Lics #
- Sürücü Lisansı #
- Sürücü Lisansları #
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- Sürücüler Lic #
- Sürücüler Lics #
- Sürücü Lisansı #
- Sürücü Lisansları #
- Driver'Lic #
- Driver'Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver' Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicense #
- Sürücü Lisansları #
- Sürücü Lic #
- Sürücü Lics #
- Sürücü Belgesi #
- Sürücü Lisansları #
- kimlik kartı #
- kimlik kartları #
- kimlik kartı #
- kimlik kartları #

#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- eyalet kısaltması (örneğin, "NY")
- eyalet adı (örneğin, "New York")

## <a name="us-individual-taxpayer-identification-number-itin"></a>ABD bireysel vergi mükellefi kimlik numarası (ITIN)

### <a name="format"></a>Biçim

"9" ile başlayan ve dördüncü basamak olarak "7" veya "8" içeren dokuz basamak, isteğe bağlı olarak boşluk veya tirelerle biçimlendirilmiş

### <a name="pattern"></a>Desen

Biçimlendirilmiş:

- "9" rakamı
- iki basamak
- boşluk veya tire
- "7" veya "8"
- basamak
- boşluk veya tire
- dört basamak

Biçimlendir -ilmemiş:

- "9" rakamı
- iki basamak
- "7" veya "8"
- beş basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_formatted_itin desenle eşleşen içeriği bulur.
- Keyword_itin anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_unformatted_itin desenle eşleşen içeriği bulur.
- Keyword_itin anahtar sözcüğü bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev Func_formatted_itin veya Func_unformatted_itin desenle eşleşen içeriği bulur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_itin"></a>Keyword_itin

- Vergi mükellefi
- vergi kimliği
- vergi belirleme
- bu
- i.t.i.n.
- ssn
- Teneke
- sosyal güvenlik
- vergi ödeyen
- itins
- taksiye bindi
- bireysel vergi mükellefi

## <a name="us-physical-addresses"></a>ABD fiziksel adresleri

Bu unbundled adlandırılmış varlık, ABD'den gelen fiziksel adresle ilgili desenleri algılar. Ayrıca, varlık SIT adlı [paketlenmiş Tüm Fiziksel Adresler'e](#all-physical-addresses) de dahildir.

### <a name="confidence-level"></a>Güvenilirlik düzeyi

Orta

## <a name="us-social-security-number-ssn"></a>ABD sosyal güvenlik numarası (SSN)

### <a name="format"></a>Biçim

dokuz basamak, biçimlendirilmiş veya biçimlendirilmemiş bir desende olabilir

> [!NOTE]
> 2011'in ortasından önce verilirse, SSN'nin geçerli olması için sayının belirli bölümlerinin belirli aralıklar içinde yer alması gereken güçlü biçimlendirmesi vardır (ancak sağlama toplamı yoktur).

### <a name="pattern"></a>Desen

dört işlev, SSN'leri dört farklı desende arar:

- Func_ssn, tire veya boşluklarla biçimlendirilmiş 2011 öncesi güçlü biçimlendirmeye sahip SSN'leri bulur (ddd-dd-dddd VEYA ddd dd d)
- Func_unformatted_ssn, 2011 öncesi güçlü biçimlendirmesi olan ve ardışık dokuz basamak (dddd) olarak biçimlendirilmemiş SSN'leri bulur
- Func_randomized_formatted_ssn 2011 sonrası kısa çizgi veya boşluklarla biçimlendirilmiş SSN'leri bulur (ddd-dd-dd VEYA ddd dd d)
- Func_randomized_unformatted_ssn, ardışık dokuz basamak (ddddd) olarak biçimlendirilmemiş 2011 sonrası SSN'leri bulur

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev `Func_ssn` , desenle eşleşen içeriği bulur.
- 'den `Keyword_ssn` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Func_unformatted_ssn işlevi desenle eşleşen içeriği bulur.
- 'den `Keyword_ssn` bir anahtar sözcük bulunur.

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının güvenilirliği düşüktür:

- İşlev `Func_randomized_formatted_ssn` veya `Func_randomized_unformatted_ssn` desenle eşleşen içeriği bulur.
- 'den `Keyword_ssn` bir anahtar sözcük bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ssn"></a>Keyword_ssn

- SSA Numarası
- sosyal güvenlik numarası
- sosyal güvenlik #
- sosyal güvenlik #
- sosyal güvenlik hayır
- Sosyal Güvenlik #
- Soc Sn
- SSN
- SSN'ler
- SSN #
- SS #
- SSID

## <a name="usuk-passport-number"></a>Birleşik Krallık pasaport numarası

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

- bir harf veya rakam
- sekiz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgileri algılamıştır:

- İşlev Func_usa_uk_passport desenle eşleşen içeriği bulur.
- veya `Keywords_uk_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.
- 'den `Keywords_eu_passport_date` bir anahtar sözcük bulundu

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- İşlev Func_usa_uk_passport desenle eşleşen içeriği bulur.
- veya `Keywords_uk_eu_passport_number` anahtar `Keywords_eu_passport_number` sözcüğü bulunur.

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

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Pasaport #
- Pasaport #
- passportid
- Pasaport
- passportno
- pasaport no
- passportnumber
- pasaport numarası
- passportnumbers
- pasaport numaraları

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- İngiliz pasaportu
- uk passport

## <a name="ukraine-passport-domestic"></a>Ukrayna pasaportu yurt içi

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

dokuz basamak

### <a name="pattern"></a>Desen

dokuz basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex Regex_Ukraine_Passport_Domestic desenle eşleşen içeriği bulur.
- Keyword_Ukraine_Passport_Domestic anahtar sözcüğü bulunur.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- ukrayna pasaportu
- pasaport numarası
- pasaport no
- паспорт України
- номер паспорта
- персональний

## <a name="ukraine-passport-international"></a>Ukrayna pasaportu uluslararası

Bu hassas bilgi türü yalnızca şu durumlarda kullanılabilir:

- veri kaybı önleme ilkeleri
- iletişim uyumluluk ilkeleri
- bilgi idaresi
- kayıt yönetimi
- Bulut Uygulamaları için Microsoft Defender

### <a name="format"></a>Biçim

sekiz karakterli alfasayısal desen

### <a name="pattern"></a>Desen

sekiz karakterli alfasayısal desen:

- iki harf veya basamak
- altı basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Regex Regex_Ukraine_Passport_International desenle eşleşen içeriği bulur.
- Keyword_Ukraine_Passport_International anahtar sözcüğü bulunur.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- ukrayna pasaportu
- pasaport numarası
- pasaport no
- паспорт України
- номер паспорта
