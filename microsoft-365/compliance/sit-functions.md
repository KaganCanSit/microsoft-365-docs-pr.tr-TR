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
description: Hassas bilgi türü işlevlerinin neleri arayacağınızı öğrenin.
ms.openlocfilehash: 7c2ce289cab93e4a0491cbf13379c169a01e7fbf
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760261"
---
# <a name="sensitive-information-type-functions"></a>Hassas bilgi türü işlevleri

Hassas bilgi türleri (SIT), hassas öğeleri tanımlamak için birincil öğeler olarak işlevleri kullanabilir. Örneğin, Kredi Kartı Numarasına duyarlı bilgi türü, kredi kartı numarasını algılamak için Func_credit_card işlevini kullanır.

Bu makalede, önceden tanımlanmış hassas bilgi türlerinin nasıl çalıştığını anlamanıza yardımcı olmak için bu işlevlerin neye bakıldığı açıklanır. Daha fazla bilgi için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>İşlevler tablosu

|İşlev adı | İşlev eylemi | Doğrulayıcıdır|
|---------|----------|---------|
|Func_aba_routing|ABA yönlendirme numarasını algılar|Evet|
|Func_alabama_drivers_license_number|Alabama sürücü lisans numarasını algılar|No|
|Func_alaska_delaware_oregon_drivers_license_number|Alaska, Delaware, Oregon sürücü lisans numarasını algılar|No|
|Func_alaska_drivers_license_number|Alaska sürücü lisans numarasını algılar|No|
|Func_alberta_drivers_license_number|Alberta sürücü lisans numarasını algılar|No|
|Func_argentina_Unique_Tax_Key|Arjantin Benzersiz vergi anahtarını algılar ve doğrular|No|
|Func_Argentina_Unique_Tax_Key|Arjantin Benzersiz vergi anahtarını algılar|No|
|Func_arizona_drivers_license_number|Arizona sürücüsünün lisans numarasını algılar|No|
|Func_arkansas_drivers_license_number|Arkansas sürücü lisans numarasını algılar|No|
|Func_australian_business_number|Avustralya iş numarasını algılar|No|
|Func_Australian_Company_Number|Avustralya şirket numarasını algılar|No|
|Func_australian_medical_account_number|Avustralya tıbbi hesap numarasını algılar|No|
|Func_australian_tax_file_number|Avustralya vergi dosya numarasını algılar|Evet|
|Func_austria_eu_ssn_or_equivalent|Avusturya sosyal güvenlik numarasını algılar|No|
|Func_austria_eu_tax_file_number|Avusturya vergi dosya numarasını algılar|No|
|Func_Austria_Value_Added_Tax|Avusturya Katma Değer Vergilerini algılar|No|
|Func_belgium_national_number|Belçika ulusal numarasını algılar|No|
|Func_belgium_value_added_tax_number|Belçika katma değerli vergi numarasını algılar|No|
|Func_brazil_cnpj|Brezilya tüzel kişilik numarasını (CNPJ) algılar|Evet|
|Func_brazil_cpf|Brezilya CPF'yi algılar|Evet|
|Func_brazil_rg|Brezilya RG'lerini algılar|No|
|Func_british_columbia_drivers_license_number|Britanya Kolumbiyası sürücü lisans numarasını algılar|No|
|Func_bulgaria_eu_national_id_card|Bulgaristan tek tip sivil numarasını algılar|No|
|Func_california_drivers_license_number|California sürücü lisans numarasını algılar|No|
|Func_canadian_sin|Kanada günahı algılar|Evet|
|Func_chile_id_card|Şili kimlik kartını algılar|No|
|Func_china_resident_id|Çin'de yerleşik kimliği algılar|No|
|Func_colorado_drivers_license_number|Colorado sürücüsünün lisans numarasını algılar|No|
|Func_connecticut_drivers_license_number|Connecticut sürücü lisans numarasını algılar|No|
|Func_credit_card|kredi kartını algılar|Evet|
|Func_croatia_id_card|Hırvatistan kimlik kartını algılar|No|
|Func_croatia_oib_number|Hırvatistan OIB numarasını algılar|No|
|Func_cyprus_eu_tax_file_number|Kıbrıs vergi dosya numarasını algılar|No|
|Func_czech_id_card_new_format|Çek kimlik kartını yeni biçimde algılar|No|
|Func_czech_id_card|Çek kimlik kartını algılar|No|
|Func_dea_number|DEA numarasını algılar|Evet|
|Func_denmark_eu_tax_file_number|Danimarka kişisel kimlik numarasını algılar|No|
|Func_district_of_columbia_drivers_license_number|Columbia Bölgesi sürücü lisans numarasını algılar|No|
|Func_estonia_eu_national_id_card|Estonya Kişisel Kimlik Kodunu algılar|No|
|Func_eu_debit_card|AB banka kartını algılar|No|
|Func_finnish_national_id|Finlandiya ulusal kimliğini algılar|No|
|Func_florida_drivers_license_number|Florida ehliyet numarasını algılar|No|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|Florida, Maryland, Michigan, Minnesota sürücü lisans numarasını algılar|No|
|Func_formatted_itin|biçimlendirilmiş ABD ITIN'ini algılar|Evet|
|Func_fr_insee|Fransa INSEE'lerini algılar|No|
|Func_fr_passport|Fransa pasaportlarını algılar|No|
|Func_france_eu_tax_file_number|Fransa vergi dosya numarasını algılar|No|
|Func_france_value_added_tax_number|Fransa katma değerli vergi numarasını algılar|No|
|Func_french_drivers_license|Fransız sürücü lisansını algılar|No|
|Func_french_insee|Fransızca INSEE'leri algılar|No|
|Func_georgia_drivers_license_number|Georgia sürücü lisans numarasını algılar|No|
|Func_german_drivers_license|Almanya'nın sürücü lisansını algılar|No|
|Func_german_passport_data|Almanya pasaportlarını algılar|No|
|Func_german_passport|Almanya pasaportlarını algılar|No|
|Func_germany_eu_tax_file_number|Almanya vergi dosya numarasını algılar|No|
|Func_germany_value_added_tax_number|Almanya katma değerli vergi numarasını algılar|No|
|Func_greece_eu_ssn|Algılar Yunanistan sin (AMKA)|No|
|Func_hawaii_drivers_license_number|Hawaii sürücüsünün lisans numarasını algılar|No|
|Func_hong_kong_id_card|Hong Kong kimlik kartını algılar|No|
|Func_hungarian_value_added_tax_number|Macaristan katma değerli vergi numarasını algılar|No|
|Func_hungary_eu_national_id_card|Macaristan kişisel kimlik numarasını algılar|No|
|Func_hungary_eu_ssn_or_equivalent|Macaristan sosyal güvenlik numarasını algılar|No|
|Func_hungary_eu_tax_file_number|Macaristan vergi dosya numarasını algılar|No|
|Func_iban|IBAN'i algılar|Evet|
|Func_idaho_drivers_license_number|Idaho sürücü lisans numarasını algılar|No|
|Func_illinois_drivers_license_number|Illinois sürücü lisans numarasını algılar|No|
|Func_india_aadhaar|Hindistan aadhaar algılar|Evet|
|Func_indiana_drivers_license_number|Indiana sürücü lisans numarasını algılar|No|
|Func_iowa_drivers_license_number|Iowa sürücü lisans numarasını algılar|No|
|Func_ireland_pps|İrlanda PPS'lerini algılar|No|
|Func_israeli_national_id_number|İsrail ulusal kimlik numarasını algılar|No|
|Func_italy_eu_national_id_card|İtalya mali kodunu algılar|No|
|Func_italy_value_added_tax_number|İtalya katma değerli vergi numarasını algılar|No|
|Func_japanese_my_number_corporate|Japonya'da benim sayı şirket algılar|Evet|
|Func_japanese_my_number_personal|Japonya'da kişisel numaramı algılar|Evet|
|Func_jp_bank_account_branch_code|Japonya banka hesabı şube kodunu algılar|No|
|Func_jp_bank_account|Japonya banka hesabını algılar|No|
|Func_jp_drivers_license_number|Japonya sürücü lisans numarasını algılar|No|
|Func_jp_passport|Japonya pasaportlarını algılar|No|
|Func_jp_resident_registration_number|Japonya'da ikamet eden kayıt numarasını algılar|No|
|Func_jp_sin_pre_1997|1997 öncesi Japonya sin'ini algılar|No|
|Func_jp_sin|Japonya SIN'i algılar|No|
|Func_kansas_drivers_license_number|Kansas sürücüsünün lisans numarasını algılar|No|
|Func_kentucky_drivers_license_number|Kentucky sürücü lisans numarasını algılar|No|
|Func_kentucky_massachusetts_virginia_drivers_license_number|Kentucky, Massachusetts, Virginia sürücü lisans numarasını algılar|No|
|Func_latvia_eu_national_id_card|Letonya kişisel kodunu algılar|No|
|Func_lithuania_eu_tax_file_number|Litvanya kişisel kodunu algılar|No|
|Func_louisiana_drivers_license_number|Louisiana sürücü lisans numarasını algılar|No|
|Func_luxemburg_eu_tax_file_number_non_natural|Luxemburg ulusal kimlik numarasını (gerçek olmayan kişiler) algılar|No|
|Func_luxemburg_eu_tax_file_number|Luxemburg ulusal kimlik numarasını (gerçek kişiler) algılar|No|
|Func_maine_drivers_license_number|Maine sürücüsünün lisans numarasını algılar|No|
|Func_manitoba_drivers_license_number|Manitoba sürücü lisans numarasını algılar|No|
|Func_maryland_drivers_license_number|Maryland sürücüsünün lisans numarasını algılar|No|
|Func_massachusetts_drivers_license_number|Massachusetts sürücü lisans numarasını algılar|No|
|Func_mexico_population_registry_code|Mexico nüfus kayıt defteri kodunu algılar|No|
|Func_michigan_minnesota_drivers_license_number|Michigan, Minnesota sürücü lisans numarasını algılar|No|
|Func_minnesota_drivers_license_number|Minnesota sürücü lisans numarasını algılar|No|
|Func_mississippi_oklahoma_drivers_license_number|Mississippi, Oklahoma sürücü lisans numarasını algılar|No|
|Func_missouri_drivers_license_number|Missouri sürücü lisans numarasını algılar|No|
|Func_montana_drivers_license_number|Montana sürücü lisans numarasını algılar|No|
|Func_nebraska_drivers_license_number|Nebraska sürücü lisans numarasını algılar|No|
|Func_netherlands_bsn|Hollanda BSN'lerini algılar|No|
|Func_netherlands_eu_tax_file_number|Hollanda vergi dosya numarasını algılar|No|
|Func_netherlands_value_added_tax_number|Hollanda katma değerli vergi numarasını algılar|No|
|Func_nevada_drivers_license_number|Nevada sürücü lisans numarasını algılar|No|
|Func_new_brunswick_drivers_license_number|New Brunswick sürücü lisans numarasını algılar|No|
|Func_new_hampshire_drivers_license_number|New Hampshire sürücü lisans numarasını algılar|No|
|Func_new_jersey_drivers_license_number|New Jersey sürücü lisans numarasını algılar|No|
|Func_new_mexico_drivers_license_number|New Mexico sürücü lisans numarasını algılar|No|
|Func_new_york_drivers_license_number|New York sürücü lisans numarasını algılar|No|
|Func_new_zealand_bank_account_number|Yeni Zelanda banka hesap numarasını algılar|No|
|Func_new_zealand_inland_revenue_number|Yeni Zelanda iç gelir numarasını algılar|No|
|Func_new_zealand_ministry_of_health_number|Yeni Zelanda sağlık bakanlığı numarasını algılar|No|
|Func_newfoundland_labrador_drivers_license_number|Newfoundland Labrador sürücü lisans numarasını algılar|No|
|Func_newzealand_driver_license_number|Yeni Zelanda sürücü lisans numarasını algılar|No|
|Func_newzealand_social_welfare_number|Yeni Zelanda sosyal yardım numarasını algılar|No|
|Func_north_carolina_drivers_license_number|Kuzey Carolina sürücü lisans numarasını algılar|No|
|Func_north_dakota_drivers_license_number|North Dakota sürücüsünün lisans numarasını algılar|No|
|Func_norway_id_number|Norveç kimlik numarasını algılar|No|
|Func_nova_scotia_drivers_license_number|Nova Scotia sürücü lisans numarasını algılar|No|
|Func_ohio_drivers_license_number|Ohio sürücü lisans numarasını algılar|No|
|Func_ontario_drivers_license_number|Ontario sürücü lisans numarasını algılar|No|
|Func_pennsylvania_drivers_license_number|Pennsylvania sürücü lisans numarasını algılar|No|
|Func_pesel_identification_number|Polonya Ulusal Kimliğini (PESEL) algılar|No|
|Func_poland_eu_tax_file_number|Polonya vergi dosya numarasını algılar|No|
|Func_polish_national_id|Polonya kimlik kartını algılar|No|
|Func_polish_passport_number|Polonya pasaport numarasını algılar|No|
|Func_polish_regon_number|Lehçe REGON numarasını algılar|No|
|Func_portugal_eu_tax_file_number|Portekiz Vergi Tanımlama Numarasını algılar|No|
|Func_prince_edward_island_drivers_license_number|Prens Edward Adası sürücü lisans numarasını algılar|No|
|Func_quebec_drivers_license_number|Quebec sürücüsünün lisans numarasını algılar|No|
|Func_randomized_formatted_ssn|rastgele biçimlendirilmiş ABD SSN'sini algılar|Evet|
|Func_randomized_unformatted_ssn|rastgele biçimlendirilmemiş ABD SSN'sini algılar|Evet|
|Func_rhode_island_drivers_license_number|Rhode Island sürücü lisans numarasını algılar|No|
|Func_romania_eu_national_id_card|Romanya kişisel sayısal kodunu (CNP) algılar|No|
|Func_saskatchewan_drivers_license_number|Saskatchewan sürücü lisans numarasını algılar|No|
|Func_slovakia_eu_national_id_card|Slovakya kişisel numarasını algılar|No|
|Func_slovenia_eu_national_id_card|Slovenya Benzersiz Ana Vatandaş Numarasını algılar|No|
|Func_slovenia_eu_tax_file_number|Slovenya vergi dosya numarasını algılar|No|
|Func_south_africa_identification_number|Güney Afrika kimlik numarasını algılar|Evet|
|Func_south_carolina_drivers_license_number|Güney Carolina sürücü lisans numarasını algılar|No|
|Func_south_dakota_drivers_license_number|Güney Dakota sürücüsünün lisans numarasını algılar|No|
|Func_south_korea_resident_number|Güney Kore yerleşik numarasını algılar|No|
|Func_spain_eu_DL_and_NI_number_citizen|İspanya DL ve NI numaralı vatandaşı algılar|No|
|Func_spain_eu_DL_and_NI_number_foreigner|İspanya DL ve NI numaralı yabancıyı algılar|No|
|Func_spain_eu_driver s_license_number|İspanya sürücü lisans numarasını algılar|No|
|Func_spain_eu_tax_file_number|İspanya vergi dosya numarasını algılar|No|
|Func_spanish_social_security_number|İspanyolca sosyal güvenlik numarasını algılar|No|
|Func_ssn|Rastgele biçimlendirilmemiş ABD SSN'sini algılama işlevi|Evet|
|Func_sweden_eu_tax_file_number|İsveç vergi dosya numarasını algılar|No|
|Func_swedish_national_identifier|İsveç ulusal tanımlayıcısı algılar|Evet|
|Func_swiss_social_security_number_ahv|İsviçre sosyal güvenlik numarası AHV'lerini algılar|No|
|Func_taiwanese_national_id|Tayvan ulusal kimliğini algılar|No|
|Func_tennessee_drivers_license_number|Tennessee sürücüsünün lisans numarasını algılar|No|
|Func_texas_drivers_license_number|Texas sürücü lisans numarasını algılar|No|
|Func_Thai_Citizen_Id|Tay Vatandaşı Kimliğini algılar|No|
|Func_Turkish_National_Id|Türkiye Ulusal Kimliğini algılar|Evet|
|Func_uk_drivers_license|Birleşik Krallık sürücü lisansını algılar|No|
|Func_uk_eu_tax_file_number|Birleşik Krallık'ın benzersiz vergi mükellefi numarasını algılar|No|
|Func_uk_nhs_number|UK NHS numarasını algılar|Evet|
|Func_uk_nino|UK NINO'yu algılar|No|
|Func_unformatted_canadian_sin|biçimlendirilmemiş Kanada SIN'ini algılar|No|
|Func_unformatted_itin|biçimlendirilmemiş ABD ITIN'ini algılar|Evet|
|Func_unformatted_ssn|rastgele biçimlendirilmemiş ABD SSN'sini algılar|Evet|
|Func_usa_uk_passport|ABD ve Birleşik Krallık pasaportlarını algılar|Evet|
|Func_utah_drivers_license_number|Utah sürücüsünün lisans numarasını algılar|No|
|Func_vermont_drivers_license_number|Vermont sürücü lisans numarasını algılar|No|
|Func_virginia_drivers_license_number|Virginia sürücü lisans numarasını algılar|No|
|Func_washington_drivers_license_number|Washington sürücü lisans numarasını algılar|No|
|Func_west_virginia_drivers_license_number|West Virginia sürücüsünün lisans numarasını algılar|No|
|Func_wisconsin_drivers_license_number|Wisconsin sürücüsünün lisans numarasını algılar|No|
|Func_wyoming_drivers_license_number|Wyoming sürücüsünün lisans numarasını algılar|No|

## <a name="func_us_date"></a>Func_us_date

Func_us_date tarihleri ortak ABD biçimlerinde arar. Yaygın biçimler şunlardır: "ay/gün/yıl", "ay-gün-yıl" ve "ay günü yılı". Ayların adları veya kısaltmaları büyük/küçük harfe duyarlı değildir.

Örnekler:

- 2 Aralık 2016, Cumartesi
- 2 Aralık 2016
- 2 Aralık 2016
- 12/2/2016
- 12/02/16
- 2 Aralık 2016
- 12-2-16

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart, Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Ocak Şub. Mar. Nisan Mayıs Haziran Ağustos Ağustos Eylül Ekim Ekim. Aralık.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates ortak E.U.'da tarihleri arar. biçimlerini (ve ABD dışındaki çoğu yeri), örneğin "gün/ay/yıl", "gün-ay-yıl" ve "gün ay yılı". Ayların adları veya kısaltmaları büyük/küçük harfe duyarlı değildir.

Örnekler:

- 2 Aralık 2016
- 02 aralık 2016
- 2 Aralık 16
- 2/12/2016
- 02/12/16
- 2 Aralık 2016
- 2-12-16

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart, Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Ocak Şub. Mar. Nisan Mayıs Haziran Ağustos Ağustos Eylül Ekim Ekim. Aralık.
- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, Ekim, Kasım, Aralık
  - jan şub maart apr mei jun jul aug sept oct okt nov dec
- French
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
  - janv. févr. mars avril mai juin juil. août sept. Ekim. Kasım. déc.
- German
  - jänuar, februar, märz, April, mai, juni juli, August, September, oktober, November, dezember
  - Jan./Jän. Şub. März Apr. Mai Juni Juli Aug. Eylül Okt. Nov. Dez.
- Italian
  - gennaio, şubbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
  - genn. febbr. Mart. Nisan. magg. giugno luglio ag. Sümer. Ott. Kasım. Dıc.
- Portekizce
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez
- Spanish
  - enero, febrero, marzo, abril, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
  - enero şub. marzo abr. mayo jun. Temmuz. agosto sept./set. Ekim. Kasım. Dıc.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (kullanım dışı)

> [!NOTE]
> Bu işlev, artık yukarıdaki işleve dahil edilen yalnızca Portekizce ay adlarını desteklediğinden  `Func_eu_date` kullanım dışıdır.

Bu işlev, Portekizce olarak yaygın olarak kullanılan biçimde bir tarih arar. Bu işlevin biçimi ile aynıdır  `Func_eu_date`ve yalnızca kullanılan dilde farklılık gösterir.

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
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (kullanım dışı)

> [!NOTE]
> Bu işlev, artık yukarıdaki işleve dahil edilen yalnızca Felemenkçe ay adlarını desteklediğinden  `Func_eu_date` kullanım dışıdır.

Bu işlev, Felemenkçe'de yaygın olarak kullanılan biçimde bir tarih arar. Bu işlevin biçimi ile aynıdır  `Func_eu_date`ve yalnızca kullanılan dilde farklılık gösterir.

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
  - januari, februari, maart, April, mei, juni, juli, augustus, September, ocktober, Ekim, Kasım, Aralık
  - jan şub maart apr mei jun jul aug sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date, kredi ve banka kartları tarafından yaygın olarak kullanılan biçimlerdeki tarihleri arar. Bu işlev tarihleri "ay/yıl", "ay-yıl", "[ay adı] yıl" ve "[ay kısaltması] yıl" biçiminde eşleştirir. Ayların adları veya kısaltmaları büyük/küçük harfe duyarlı değildir.

Örnekler:

- AA/YY -- örneğin, 01/11 veya 1/11
- AA/YYYY -- örneğin, 01/2011 veya 1/2011
- AA-YY -- örneğin, 01-22 veya 1-11
- AA-YYYY -- örneğin, 01-2000 veya 1-2000

Aşağıdaki biçimler YY veya YYYY'yi destekler:

- Ay-YYYY -- örneğin Ocak-2010 veya Ocak-2010 ya da Ocak-10 ya da Ocak-10
- YYYY Ayı -- örneğin, 'Ocak 2010' veya 'Ocak 2010' veya '10 Ocak' veya '10 Ocak'
- MonthYYY -- örneğin, 'ocak2010' veya 'Ocak2010' ya da 'ocak10' veya 'Ocak10'
- Ay/YYYY -- örneğin, 'ocak/2010' veya 'Ocak/2010' veya 'ocak/10' veya 'Ocak/10'

Kabul edilen ay adları:

- English
  - Ocak, Şubat, Mart, Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık
  - Jan Şub Mar Nisan Mayıs Haziran Temmuz Ağustos Ağustos Ekim Aralık

## <a name="func_us_address"></a>Func_us_address

Func_us_address ABD eyalet adını veya posta kısaltmasını ve ardından geçerli bir posta kodunu arar. Posta kodu, ABD eyalet adı veya kısaltmasıyla ilişkili doğru posta kodlarından biri olmalıdır. ABD eyalet adı ve posta kodu noktalama işaretleri veya harflerle ayrılamaz.

Örnekler:

- Washington 98052
- Washington 98052-9998
- WA 98052
- WA 98052-9998
