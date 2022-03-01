---
title: Hassas bilgi türü işlevleri
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: low
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Hassas bilgi türü işlevlerinin ne için arama yaptığını öğrenin.
ms.openlocfilehash: d00b61aeeb435940436bd0c901edce2fef81a3e4
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015484"
---
# <a name="sensitive-information-type-functions"></a>Hassas bilgi türü işlevleri

Hassas bilgi türleri (SIT) hassas öğeleri tanımlamak için birincil öğeler olarak işlevleri kullanabilir. Örneğin, Kredi Kartı Numarası duyarlı bilgi türü, Func_credit_card numarası algılamak için Kredi Kartı işlevini kullanır.

Bu makalede, önceden tanımlanmış hassas bilgi türlerinin nasıl olduğunu anlamanıza yardımcı olması için bu işlevlerin ne araması olduğu açıklanmıştır. Daha fazla bilgi için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>İşlev tablosu

|İşlev adı | İşlev eylemi | Geçerli bir|
|---------|----------|---------|
|Func_aba_routing|ABA yönlendirme numarasını algılar|evet|
|Func_alabama_drivers_license_number|Alabama sürücüsünün lisans numarasını algılar|hayır|
|Func_alaska_delaware_oregon_drivers_license_number|Alaska, Delaware, Oregon sürücüsünün lisans numarasını algılar|hayır|
|Func_alaska_drivers_license_number|Alaska sürücüsünün lisans numarasını algılar|hayır|
|Func_alberta_drivers_license_number|Alberta sürücüsünün lisans numarasını algılar|hayır|
|Func_argentina_Unique_Tax_Key|Arjantin Benzersiz vergi anahtarını algılar ve doğrular|hayır|
|Func_Argentina_Unique_Tax_Key|Arjantin Benzersiz vergi anahtarını algılar|hayır|
|Func_arizona_drivers_license_number|Arizona sürücüsünün lisans numarasını algılar|hayır|
|Func_arkansas_drivers_license_number|Arkansas sürücü lisans numarasını algılar|hayır|
|Func_australian_business_number|Avustralya iş numarasını algılar|hayır|
|Func_Australian_Company_Number|Avustralya şirket numarasını algılar|hayır|
|Func_australian_medical_account_number|Avustralya tıbbi hesap numarasını algılar|hayır|
|Func_australian_tax_file_number|Avustralya vergi dosyası numarasını algılar|evet|
|Func_austria_eu_ssn_or_equivalent|Avusturya sosyal güvenlik numarasını algılar|hayır|
|Func_austria_eu_tax_file_number|Avusturya vergi dosyası numarasını algılar|hayır|
|Func_Austria_Value_Added_Tax|Avusturya Katma Değer Vergisini algılar|hayır|
|Func_belgium_national_number|Belçika ulusal numarasını algılar|hayır|
|Func_belgium_value_added_tax_number|Belçika değeri eklenen vergi numarasını algılar|hayır|
|Func_brazil_cnpj|Brezilya yasal varlık numarasını (CNPJ) algılar|evet|
|Func_brazil_cpf|Brezilya CPF'lerini algılar|evet|
|Func_brazil_rg|Brazil RG algılar|hayır|
|Func_british_columbia_drivers_license_number|İngiliz Columbia sürücüsünün lisans numarasını algılar|hayır|
|Func_bulgaria_eu_national_id_card|Bulgaristan tekdüdüz devlet numarasını algılar|hayır|
|Func_california_drivers_license_number|California sürücü lisans numarasını algılar|hayır|
|Func_canadian_sin|Kanada sin'ini algılar|evet|
|Func_chile_id_card|Şili Kimlik kartını algılar|hayır|
|Func_china_resident_id|Çin'deki yerleşik kimliği algılar|hayır|
|Func_colorado_drivers_license_number|Colorado sürücüsünün lisans numarasını algılar|hayır|
|Func_connecticut_drivers_license_number|Bilgisayar sürücüsünün lisans numarasını algılar|hayır|
|Func_credit_card|kredi kartını algılar|evet|
|Func_croatia_id_card|Hırvatistan Kimlik kartını algılar|hayır|
|Func_croatia_oib_number|Hırvatistan OIB numarasını algılar|hayır|
|Func_cyprus_eu_tax_file_number|Kıbrıs vergi dosyası numarasını algılar|hayır|
|Func_czech_id_card_new_format|Çek Kimliği kartını yeni biçimde algılar|hayır|
|Func_czech_id_card|Çek Kimliği kartını algılar|hayır|
|Func_dea_number|DEA numarasını algılar|evet|
|Func_denmark_eu_tax_file_number|Danimarka kişisel kimlik numarasını algılar|hayır|
|Func_district_of_columbia_drivers_license_number|Columbia Sürücüsünün Bölge lisans numarasını algılar|hayır|
|Func_estonia_eu_national_id_card|Estonya Kişisel Kimlik Kodunu algılar|hayır|
|Func_eu_debit_card|AB banka kartını algılar|hayır|
|Func_finnish_national_id|Fince ulusal kimliği algılar|hayır|
|Func_florida_drivers_license_number|Florida sürücüsünün lisans numarasını algılar|hayır|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|Florida, Maryland, Michigan, Minnesota sürücüsünün lisans numarasını algılar|hayır|
|Func_formatted_itin|biçimlendirilmiş US ITIN'i algılar|evet|
|Func_fr_insee|France INSEE'yi algılar|hayır|
|Func_fr_passport|Fransa pasaportunu algılar|hayır|
|Func_france_eu_tax_file_number|Fransa vergi dosyası numarasını algılar|hayır|
|Func_france_value_added_tax_number|Fransa değeri eklenen vergi numarasını algılar|hayır|
|Func_french_drivers_license|Fransızca sürücü lisansını algılar|hayır|
|Func_french_insee|Fransızca INSEE'yi algılar|hayır|
|Func_georgia_drivers_license_number|Georgia sürücüsünün lisans numarasını algılar|hayır|
|Func_german_drivers_license|Almanya sürücü lisansını algılar|hayır|
|Func_german_passport_data|Almanya pasaportunu algılar|hayır|
|Func_german_passport|Almanya pasaportunu algılar|hayır|
|Func_germany_eu_tax_file_number|Almanya vergi dosyası numarasını algılar|hayır|
|Func_germany_value_added_tax_number|Almanya değeri eklenen vergi numarasını algılar|hayır|
|Func_greece_eu_ssn|Yunanistan sin'ini (AMKA) algılar|hayır|
|Func_hawaii_drivers_license_number|Hawaii sürücüsünün lisans numarasını algılar|hayır|
|Func_hong_kong_id_card|Hong Kong Kimlik Kartını algılar|hayır|
|Func_hungarian_value_added_tax_number|Macaristan değeri eklenen vergi numarasını algılar|hayır|
|Func_hungary_eu_national_id_card|Macaristan kişisel kimlik numarasını algılar|hayır|
|Func_hungary_eu_ssn_or_equivalent|Macaristan sosyal güvenlik numarasını algılar|hayır|
|Func_hungary_eu_tax_file_number|Macaristan vergi dosyası numarasını algılar|hayır|
|Func_iban|IBAN'ı algılar|evet|
|Func_idaho_drivers_license_number|Idaho sürücüsünün lisans numarasını algılar|hayır|
|Func_illinois_drivers_license_number|Illinois sürücü lisans numarasını algılar|hayır|
|Func_india_aadhaar|Hindistan aadhaar'ı algılar|evet|
|Func_indiana_drivers_license_number|Indiana sürücü lisans numarasını algılar|hayır|
|Func_iowa_drivers_license_number|Iowa sürücüsünün lisans numarasını algılar|hayır|
|Func_ireland_pps|Ireland PPS'i algılar|hayır|
|Func_israeli_national_id_number|İsrail ulusal kimlik numarasını algılar|hayır|
|Func_italy_eu_national_id_card|İtalya mali kodunu algılar|hayır|
|Func_italy_value_added_tax_number|İtalya değeri eklenen vergi numarasını algılar|hayır|
|Func_japanese_my_number_corporate|şirket numaram Japonya'yı algılar|evet|
|Func_japanese_my_number_personal|Japonya kişisel numaramı algılar|evet|
|Func_jp_bank_account_branch_code|Japonya banka hesabı şube kodunu algılar|hayır|
|Func_jp_bank_account|Japonya banka hesabını algılar|hayır|
|Func_jp_drivers_license_number|Japonya sürücü lisans numarasını algılar|hayır|
|Func_jp_passport|Japonya pasaportunu algılar|hayır|
|Func_jp_resident_registration_number|Japonya'daki yerleşik kayıt numarasını algılar|hayır|
|Func_jp_sin_pre_1997|Japan sin pre 1997'i algılar|hayır|
|Func_jp_sin|Japonya SN'lerini algılar|hayır|
|Func_kansas_drivers_license_number|Kansas sürücüsünün lisans numarasını algılar|hayır|
|Func_kentucky_drivers_license_number|Kupon sürücüsünün lisans numarasını algılar|hayır|
|Func_kentucky_massachusetts_virginia_drivers_license_number|Virginia, Virgins, Virginia sürücüsünün lisans numarasını algılar|hayır|
|Func_latvia_eu_national_id_card|Letonya kişisel kodunu algılar|hayır|
|Func_lithuania_eu_tax_file_number|Litvanya kişisel kodunu algılar|hayır|
|Func_louisiana_drivers_license_number|Louisiana sürücüsünün lisans numarasını algılar|hayır|
|Func_luxemburg_eu_tax_file_number_non_natural|Luxemburg ulusal kimlik numarasını (doğal olmayan kişiler) algılar|hayır|
|Func_luxemburg_eu_tax_file_number|Luxemburg ulusal kimlik numarasını (doğal kişiler) algılar|hayır|
|Func_maine_drivers_license_number|Maine sürücüsünün lisans numarasını algılar|hayır|
|Func_manitoba_drivers_license_number|Manitoba sürücü lisans numarasını algılar|hayır|
|Func_maryland_drivers_license_number|Maryland sürücüsünün lisans numarasını algılar|hayır|
|Func_massachusetts_drivers_license_number|Yalniza sürücü lisans numarasını algılar|hayır|
|Func_mexico_population_registry_code|Meksika nüfus kayıt defteri kodunu algılar|hayır|
|Func_michigan_minnesota_drivers_license_number|Michigan, Minnesota sürücüsünün lisans numarasını algılar|hayır|
|Func_minnesota_drivers_license_number|Minnesota sürücüsünün lisans numarasını algılar|hayır|
|Func_mississippi_oklahoma_drivers_license_number|Mississippi, Oklahoma sürücüsünün lisans numarasını algılar|hayır|
|Func_missouri_drivers_license_number|Missouri sürücüsünün lisans numarasını algılar|hayır|
|Func_montana_drivers_license_number|Montana sürücüsünün lisans numarasını algılar|hayır|
|Func_nebraska_drivers_license_number|Nebraska sürücü lisans numarasını algılar|hayır|
|Func_netherlands_bsn|Hollanda BSN'lerini algılar|hayır|
|Func_netherlands_eu_tax_file_number|Hollanda vergi dosyası numarasını algılar|hayır|
|Func_netherlands_value_added_tax_number|Hollanda değeri eklenen vergi numarasını algılar|hayır|
|Func_nevada_drivers_license_number|Nevada sürücüsünün lisans numarasını algılar|hayır|
|Func_new_brunswick_drivers_license_number|New Brunswick sürücü lisans numarasını algılar|hayır|
|Func_new_hampshire_drivers_license_number|NewShireshire sürücüsünün lisans numarasını algılar|hayır|
|Func_new_jersey_drivers_license_number|New Jersey sürücüsünün lisans numarasını algılar|hayır|
|Func_new_mexico_drivers_license_number|New Mexico sürücü lisans numarasını algılar|hayır|
|Func_new_york_drivers_license_number|New York sürücüsünün lisans numarasını algılar|hayır|
|Func_new_zealand_bank_account_number|Yeni Zelanda banka hesap numarasını algılar|hayır|
|Func_new_zealand_inland_revenue_number|Yeni Zelanda iç gelir numarasını algılar|hayır|
|Func_new_zealand_ministry_of_health_number|yeni Zelanda'da sağlık numarası olduğunu algılar|hayır|
|Func_newfoundland_labrador_drivers_license_number|Newfoundland Labrador sürücüsünün lisans numarasını algılar|hayır|
|Func_newzealand_driver_license_number|Yeni Zelanda sürücü lisans numarasını algılar|hayır|
|Func_newzealand_social_welfare_number|Yeni Zelanda sosyal yardım numarasını algılar|hayır|
|Func_north_carolina_drivers_license_number|North Carolina sürücüsünün lisans numarasını algılar|hayır|
|Func_north_dakota_drivers_license_number|North Dakota sürücüsünün lisans numarasını algılar|hayır|
|Func_norway_id_number|Norveç Kimlik numarasını algılar|hayır|
|Func_nova_scotia_drivers_license_number|Nova Scotia sürücü lisans numarasını algılar|hayır|
|Func_ohio_drivers_license_number|Ohio sürücüsünün lisans numarasını algılar|hayır|
|Func_ontario_drivers_license_number|Ontario sürücüsünün lisans numarasını algılar|hayır|
|Func_pennsylvania_drivers_license_number|Pennsylvania sürücüsünün lisans numarasını algılar|hayır|
|Func_pesel_identification_number|Polonya Ulusal Kimliğini (PESEL) algılar|hayır|
|Func_poland_eu_tax_file_number|Polonya vergi dosyası numarasını algılar|hayır|
|Func_polish_national_id|Polonya kimlik kartını algılar|hayır|
|Func_polish_passport_number|Lehçe Pasaport numarasını algılar|hayır|
|Func_polish_regon_number|Lehçe REGON numarasını algılar|hayır|
|Func_portugal_eu_tax_file_number|Portekiz Vergi Tanımlama Numarasını algılar|hayır|
|Func_prince_edward_island_drivers_license_number|Prince Edward Island sürücüsünün lisans numarasını algılar|hayır|
|Func_quebec_drivers_license_number|Quebec sürücüsünün lisans numarasını algılar|hayır|
|Func_randomized_formatted_ssn|rastgele biçimlendirilmiş US SSN'leri algılar|evet|
|Func_randomized_unformatted_ssn|rastgele biçimlendirilmemiş US SSN'leri algılar|evet|
|Func_rhode_island_drivers_license_number|Rhode Island sürücü lisans numarasını algılar|hayır|
|Func_romania_eu_national_id_card|Romanya kişisel sayısal kodunu (CNP) algılar|hayır|
|Func_saskatchewan_drivers_license_number|Saskatchewan sürücüsünün lisans numarasını algılar|hayır|
|Func_slovakia_eu_national_id_card|Slovakya kişisel numarasını algılar|hayır|
|Func_slovenia_eu_national_id_card|Slovloven Asıl Slovuz Numarasını algılar|hayır|
|Func_slovenia_eu_tax_file_number|Slovenya vergi dosyası numarasını algılar|hayır|
|Func_south_africa_identification_number|Güney Afrika kimlik numarasını algılar|evet|
|Func_south_carolina_drivers_license_number|South Carolina sürücüsünün lisans numarasını algılar|hayır|
|Func_south_dakota_drivers_license_number|South Dakota sürücüsünün lisans numarasını algılar|hayır|
|Func_south_korea_resident_number|Güney Kore yerleşik numarasını algılar|hayır|
|Func_spain_eu_DL_and_NI_number_citizen|İspanya DL ve NI sayı sayılarını çok sayıda algılar|hayır|
|Func_spain_eu_DL_and_NI_number_foreigner|İspanya DL ve NI numarası yabancıyı algılar|hayır|
|Func_spain_eu_driver's_license_number|İspanya sürücü lisans numarasını algılar|hayır|
|Func_spain_eu_tax_file_number|İspanya vergi dosyası numarasını algılar|hayır|
|Func_spanish_social_security_number|İspanyolca sosyal güvenlik numarasını algılar|hayır|
|Func_ssn|Rastgele olmayan biçimlendirilmiş US SSN'leri algılama işlevi|evet|
|Func_sweden_eu_tax_file_number|İsveç vergi dosyası numarasını algılar|hayır|
|Func_swedish_national_identifier|İsveççe ulusal tanımlayıcıyı algılar|evet|
|Func_swiss_social_security_number_ahv|İsviçre sosyal güvenlik numarası AHV'i algılar|hayır|
|Func_taiwanese_national_id|Tayvan ulusal kimliğini algılar|hayır|
|Func_tennessee_drivers_license_number|Sürücü sürücü lisans numarasını algılar|hayır|
|Func_texas_drivers_license_number|Texas sürücüsünün lisans numarasını algılar|hayır|
|Func_Thai_Citizen_Id|Tay Dili Kimliklerini algılar|hayır|
|Func_Turkish_National_Id|Türkçe Ulusal Kimliği algılar|evet|
|Func_uk_drivers_license|Birleşik Krallık sürücü lisansını algılar|hayır|
|Func_uk_eu_tax_file_number|İngiltere'de benzersiz vergi mükellefi numarasını algılar|hayır|
|Func_uk_nhs_number|UK NHS numarasını algılar|evet|
|Func_uk_nino|UK NINO'yu algılar|hayır|
|Func_unformatted_canadian_sin|biçimlendirilmemiş Kanada SN'lerini algılar|hayır|
|Func_unformatted_itin|biçimlendirilmemiş US ITIN'i algılar|evet|
|Func_unformatted_ssn|rastgele olmayan biçimlendirilmemiş US SSN'leri algılar|evet|
|Func_usa_uk_passport|ABD ve İngiltere pasaportunu algılar|evet|
|Func_utah_drivers_license_number|Utah sürücüsünün lisans numarasını algılar|hayır|
|Func_vermont_drivers_license_number|Vermont sürücüsünün lisans numarasını algılar|hayır|
|Func_virginia_drivers_license_number|Virginia sürücüsünün lisans numarasını algılar|hayır|
|Func_washington_drivers_license_number|Washington sürücüsünün lisans numarasını algılar|hayır|
|Func_west_virginia_drivers_license_number|West Virginia sürücüsünün lisans numarasını algılar|hayır|
|Func_wisconsin_drivers_license_number|Wisconsin sürücüsünün lisans numarasını algılar|hayır|
|Func_wyoming_drivers_license_number|Wyoming sürücüsünün lisans numarasını algılar|hayır|

## <a name="func_us_date"></a>Func_us_date

Func_us_date, sık kullanılan ABD biçimlerini içinde tarihler için görünüm sağlar. Yaygın biçimler "ay/gün/yıl", "ay-gün-yıl" ve "ay günü yıl" biçimleridir. Ay adları veya kısaltmaları büyük/harfe duyarlı değildir.

Örnekler:

- 2 Aralık 2016
- 2 Aralık 2016
- aralık 02 2016
- 12/2/2016
- 12/02/16
- Ara-2-2016
- 12-2-16

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Oca. Şub. Nis. Haziran Haziran Ağu. Eylül. Eki. Kas. Ara.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates, SıK KULLANıLAN ABD'de tarihleri biçimleri (ve ABD dışındaki çoğu yerde), "gün/ay/yıl", "gün-ay-yılı" ve "gün ay yılı" gibi. Ay adları veya kısaltmaları büyük/harfe duyarlı değildir.

Örnekler:

- 2 Aralık 2016
- 02 ara 2016
- 2 Ara 16
- 2/12/2016
- 02/12/16
- 2.Ara-2016
- 2-12-16

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Oca. Şub. Nis. Haziran Haziran Ağu. Eylül. Eki. Kas. Ara.
- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, Eylül, ocktober, October, Kasım, Aralık
  - jan feb maart apr mei jun jul aug sep oct okt nov dec
- French
  - janvier, février, mars, avril, mai, juillet, aofart, septembre, octobre, novembre, décembre
  - ocav. févr. mars avril mai juil. ao yl. eki. Kasım déc.
- German
  - jänuar, februar, märz, April, mai, juni juli, Ağustos, Eylül, oktober, Kasım, dezember
  - Jan./Jän. Şub. März Apr. Mai Juni Juli Ağu. Eylül. Okt. Kasım. Dez.
- Italian
  - gennaio, febbraio, marını, aprile, mamur, giugno, lu gif, agosto, settembre, ottobre, Novembre, dicembre
  - genn. febbr. mar. nis. magg. giugno lu bir ag. sett. ott. Kasım dic.
- Portekizce
  - janeiro, bireiro, março, mara, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar a mai jun jul jul nov dez
- Spanish
  - enero, febrero, marını, abril, mayo, hazio, adası, agosto, eylüliembre, octubre, noviembre, diciembre
  - enero şub. marzo abru. mayo jun. tem. agosto eylül./set. eki. Kasım dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (kullanımdan kullanımdan)

> [!NOTE]
> Bu işlev, yalnızca Portekizce ay adlarını desteklediği için kullanım dışıdır ve şimdi yukarıdaki işlevde  `Func_eu_date` yer almaktadır.

Bu işlev, Portekizcede yaygın olarak kullanılan biçimde bir tarih için tarih görüntüler. Bu işlevin biçimi ile aynıdır  `Func_eu_date`ve yalnızca kullanılan dilden farklıdır.

Örnekler:

- 2 Dez 2016
- 02 dez 2016
- 2 Dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

Kabul edilen ay adları:

- Portekizce
  - janeiro, bireiro, março, mara, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar a mai jun jul jul nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (kullanımdan kullanımdan kullanımdan)

> [!NOTE]
> Bu işlev, yalnızca Hollanda ay adlarını desteklediği için kullanım dışıdır ve şimdi yukarıdaki işlevde  `Func_eu_date` yer almaktadır.

Bu işlev, Felemenkçe'de yaygın olarak kullanılan biçimde bir tarih görüntüler. Bu işlevin biçimi ile aynıdır  `Func_eu_date`ve yalnızca kullanılan dilden farklıdır.

Örnekler:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2-Mei-2016
- 2-12-16

Kabul edilen ay adları:

- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, Eylül, ocktober, October, Kasım, Aralık
  - jan feb maart apr mei jun jul aug sep out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date, kredi kartı ve banka kartları tarafından yaygın olarak kullanılan biçimlerde tarihlerin nasıl olduğunu okur. Bu işlev, "ay/yıl", "ay-yıl", "[ay adı] yılı" ve "[ay kısaltması] yıl" biçimindeki tarihleri eşler. Ay adları veya kısaltmaları büyük/harfe duyarlı değildir.

Örnekler:

- AA/YY -- örneğin, 01/11 veya 1/11
- AA/YYYY -- örneğin, 01/2011 veya 1/2011
- AA-YY -- örneğin, 01-22 veya 1-11
- AA-YYYY -- örneğin, 01-2000 veya 1-2000

Aşağıdaki biçimler YY'yi veya YYYY'yi destekler:

- Ay-YYYY -- örneğin Ocak 2010 veya Ocak-2010 ya da Oca 10 ya da Ocak-10
- Ay YYYY -- örneğin, 'ocak 2010' veya 'Ocak 2010' ya da '10 Ocak' veya '10 Ocak'
- MonthYYY -- örneğin, 'ocak2010' veya 'Ocak2010' ya da 'ocak10' veya 'Ocak10'
- Ay/YYYY -- örneğin, 'ocak/2010' veya 'Oca/2010' ya da 'ocak/10' veya 'Oca/10'

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Oca Şub Mar Mayıs Haziran Haziran Eylül Eki Eki Aralık

## <a name="func_us_address"></a>Func_us_address

Func_us_address, ABD eyaleti adını veya posta kısaltmasını ve ardından geçerli bir posta kodunu atayabilir. Posta kodu, ABD eyaleti adıyla veya kısaltmayla ilişkilendirilmiş doğru posta kodlarından biri olmalı. ABD eyaleti adı ve posta kodu noktalama işaretleri veya harflerle ayrılabilir.

Örnekler:

- Washington 98052
- Washington 98052-9998
- WA 98052
- WA 98052-9998
