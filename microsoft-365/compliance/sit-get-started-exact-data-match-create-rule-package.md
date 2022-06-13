---
title: Tam veri eşleşmesi hassas bilgi türü/kural paketi oluşturma
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
description: Tam veri eşleşmesi hassas bilgi türü/kural paketi oluşturma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff493f7af88d377bcf008d13752969107cfd65e7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017196"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Tam veri eşleşmesi hassas bilgi türü/kural paketi oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Uyumluluk merkezindeki [EDM şemasını ve SIT sihirbazını](#use-the-edm-schema-and-sit-wizard) kullanarak tam veri eşleşmesi (EDM) hassas bilgi türü (SIT) oluşturabilir veya kural paketi XML dosyasını [el ile](#create-a-rule-package-manually) oluşturabilirsiniz. Ayrıca, şemayı oluşturmak için bir yöntem kullanarak her ikisini de birleştirebilir ve daha sonra diğer yöntemi kullanarak düzenleyebilirsiniz.

EDM tabanlı SITS veya uygulamaları hakkında bilgi sahibi değilseniz, şunları tanımanız gerekir:

- [Hassas bilgi türleri hakkında daha fazla bilgi edinme](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>EDM şemasını ve SIT sihirbazını kullanma

İşlemi basitleştirmeye yardımcı olmak için hassas bilgi türü (SIT) dosyalarınızı oluşturmak için bu sihirbazı kullanabilirsiniz.

EDM Hassas Bilgi türü bir veya daha fazla desenden oluşur. Her desen, belgedeki veya e-postadaki hassas içeriği tanımlamak için kullanılacak bir kanıt birleşimini (şemadaki alanlar) açıklar.

## <a name="pre-requisites"></a>Önkoşullar

Şu makalelerdeki adımları gerçekleştirin:

1. [Tam veri eşleşmesine dayalı hassas bilgi türleri için kaynak verilerini dışa aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Tam veri eşleşmeli hassas bilgi türleri için hassas bilgi kaynak tablosu karması oluşturma ve karşıya yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Sihirbazı veya PowerShell aracılığıyla kural paketi XML dosyasını kullanarak EDM hassas bilgi türü oluşturacak olmanız fark etmeksizin, kullanıcı arabirimi aracılığıyla özel bir hassas bilgi türü oluşturmak, test etmek ve dağıtmak için Genel yönetici veya Uyumluluk yöneticisi izinlerine sahip olmanız gerekir. Bkz. [Office 365'da yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).
- Birincil öğelere duyarlı bilgi türü olarak kullanılacak yerleşik SID'lerden birini belirleyin.
  - Yerleşik hassas bilgi türlerinden hiçbiri seçtiğiniz sütundaki veriyle eşleşmiyorsa, bunu yapacak özel bir hassas bilgi türü oluşturmanız gerekir.
  - Şemanızdaki birincil öğe sütunu için Yoksayılan Sınırlayıcılar seçeneğini belirlediyseniz, oluşturduğunuz özel SIT'in verileri seçili sınırlayıcılarla ve seçili sınırlayıcılar olmadan eşleştirdiğinden emin olun.
  - Yerleşik bir SIT kullanıyorsanız, tam olarak seçmek istediğiniz dizeleri algıladığından ve dizenin herhangi bir çevresindeki karakteri içermediğinden veya hassas bilgi tablonuzda depolandığı gibi dizenin geçerli bir bölümünü dışlamadığından emin olun.

Bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) ve [Uyumluluk merkezinde özel hassas bilgi türleri oluşturma](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Tam veri eşleme şemasını ve hassas bilgi türü deseni sihirbazını kullanma

1. Kiracınızın Microsoft Purview uyumluluk portalında **Veri sınıflandırması** > **Tam veri eşleşmeleri'ne** gidin.

2. Hassas bilgi türü yapılandırma sihirbazını açmak için **EDM hassas bilgi türlerini** ve **EDM hassas bilgi türü oluştur'u** seçin.

3. **Var olan bir EDM şemasını seçin'i** seçin ve [Tam veri eşleşmesi için şemayı oluşturma bölümünde oluşturduğunuz şemayı seçin.](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

4. **İleri'yi** ve **ardından Desen oluştur'u** seçin.

5. **Güvenilirlik düzeyini** ve **Birincil öğesini** seçin. Güvenilirlik düzeyleri hakkında daha fazla bilgi edinmek için bkz. [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Belgedeki hangi metnin birincil öğe alanındaki tüm değerlerle karşılaştırılacağını tanımlamak için **Birincil öğenin hassas bilgi türünü** seçin. Kullanılabilir hassas bilgi türleri hakkında daha fazla bilgi edinmek için bkz. [Hassas Bilgi Türü Varlık Tanımları](sensitive-information-type-entity-definitions.md) .

   > [!IMPORTANT]
   > Bulmak istediğiniz içeriğin biçimiyle yakından eşleşen hassas bir bilgi türü seçin. Tüm metin dizeleriyle veya tüm sayılarla eşleşen gibi gereksiz içerikle eşleşen hassas bir bilgi türü seçmek sistemde aşırı yüke neden olabilir ve bu da hassas bilgilerin kaçırılmasına neden olabilir.

7. **Destekleyici öğelerinizi** ve eşleştirme seçeneklerinizi belirleyin.

8. **Bitti** ve **İleri'yi** seçin.

9. İstediğiniz **Güvenilirlik düzeyini ve karakter yakınlığı'nı** seçin. Bu, EDM hassas bilgi türünün tamamı için varsayılan değer olacaktır.

10. EDM hassas bilgi türünüz için ek desenler oluşturmak istiyorsanız **Desen oluştur'u** seçin.

11. **İleri'yi** seçin ve **yöneticiler için** bir **Ad** ve Açıklama girin.

12. Gözden geçirin ve **Gönder'i** seçin.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Hassas bilgi türü desenini düzenleme veya silme

1. **Uyumluluk merkezi** > **Veri sınıflandırması** > **Tam veri eşleşmelerini** açın.

2. **EDM hassas bilgi türlerini** seçin.

3. Düzenlemek istediğiniz EDM SIT'i seçin.

4. **EDM hassas bilgi türünü düzenle'yi** veya Açılır menüden **EDM hassas bilgi türünü sil'i** seçin.

## <a name="working-with-specific-types-of-data"></a>Belirli veri türleriyle çalışma

Performans nedenleriyle, gereksiz eşleşme sayısını en aza indirecek desenler kullanmanız kritik önem taşır. Örneğin, normal ifadeyi temel alan hassas bir bilgi türü kullanabilirsiniz.

`\b\w*\b`

Bu, herhangi bir belge veya e-postadaki tek tek her sözcük veya numarayla eşleşer. Bu, hizmetin eşleşmelerle aşırı yüklenmesine ve doğru eşleşmelerin algılanmamasına neden olabilir. Daha kesin desenler kullanmak bu durumu önleyebilir. Bazı yaygın veri türleri için doğru yapılandırmayı belirlemeye yönelik bazı öneriler aşağıdadır.

**E-posta adresleri**: E-posta adreslerini tanımlamak kolay olabilir, ancak içerikte çok yaygın olduklarından, birincil alan olarak kullanıldığında sistemde önemli bir yüke neden olabilirler. Bunları yalnızca ikincil kanıt olarak kullanın. Birincil kanıt olarak kullanılması gerekiyorsa, e-postalarda veya `From` `To` alanlarında kullanımlarını dışlamak ve eşleştirilmesi gereken gereksiz dize sayısını azaltmak için şirketinizin e-posta adresiyle bunları dışlamak için mantığı kullanan özel bir hassas bilgi türü tanımlamayı deneyin.

**Telefon sayılar**: Telefon sayılar ülke ön ekleri, alan kodları ve ayırıcılar dahil veya hariç olmak üzere birçok farklı biçimde gelebilir. Yükü en düşük düzeyde tutarken hatalı negatifleri azaltmak için bunları yalnızca ikincil öğeler olarak kullanın, parantez ve tireler gibi olası tüm ayırıcıları hariç tutun ve yalnızca hassas veri tablonuza her zaman telefon numarasında bulunacak bölümü ekleyin.

**Kişinin adları**: Bu EDM türünün sınıflandırma öğesi olarak normal bir ifadeyi temel alan hassas bir bilgi türü kullanıyorsanız, ortak sözcüklerden ayırt etmek zor olduğundan, kişinin adlarını birincil öğe olarak kullanmayın.

İşlenecek çok sayıda eşleşme oluşturabilecek bir proje kodu adı gibi belirli bir desenle tanımlanması zor bir birincil öğe kullanmanız gerekiyorsa, EDM türünüz için sınıflandırma öğesi olarak kullandığınız hassas bilgi türüne anahtar sözcükler eklediğinizden emin olun. Örneğin, normal sözcükler olabilecek proje kodu adları kullanıyorsanız, EDM türünüz için sınıflandırma öğesi olarak kullanılan hassas türdeki proje adı normal ifade tabanlı desene yakın bir şekilde gerekli ek kanıt olarak sözcüğü `project` kullanabilirsiniz. Ya da EDM SIT'inizin sınıflandırma öğesi olarak normal sözlüğü temel alan hassas bir tür kullanmayı da düşünebilirsiniz.

Sayısal dizeleri eşleştirmeye çalışırken, bilinen basamak sayısı veya başlangıç basamakları gibi izin verilen sayı aralıklarını belirtin. Görece esnek bir sayı aralığını eşleştirmeniz gerekiyorsa, eşleşme sayısını azaltmak için temel SIT'teki anahtar sözcükleri kullanabilirsiniz. Örneğin, 7-11 basamaklı hesap numaralarını eşleştirmeye çalışıyorsanız, gerekli ek kanıt olarak SIT'e , `customer`, `acct.` sözcüklerini `account`ekleyin. Bu, EDM tarafından işlenecek eşleşme sınırlarının aşılmasına neden olabilecek gereksiz eşleşme olasılığını azaltır.

Birincil öğe olarak kullanmanız gereken bir alan çok sayıda eşleşmeye neden olabilecek basit bir desene uyarsa ve anahtar sözcüklerin varlığını hassas bilgi türüne ek kanıt olarak ek olarak ekleyemezseniz, alternatif olarak bu desenin en az sayıda oluşumunu gerektirebilirsiniz. Örneğin, EDM ile eşleşmesi için beş basamaklı olası bir sayıyı çevreleyen en az 29 diğer beş basamaklı sayıyı algılamak için aşağıdaki şekilde tanımlanan özel bir hassas bilgi türü kullanabilirsiniz:

```xml
 <Entity id="98703510-18b3-43d4-961f-15317594beb7"
                  patternsProximity="300"
                  recommendedConfidence="85"
                  relaxProximity="false">
                  <Pattern confidenceLevel="85"
                              proximity="300">
                              <IdMatch idRef="MRN"/>
                              <Match idRef="30 AccountNrs"
                                    minCount="30"
                                    proximity="3000"
                                    uniqueResults="true"/>
                  </Pattern>
      </Entity>
      <Regex id="30 AccountNrs">\d{5}</Regex>
```

Bazı durumlarda, geçmiş nedenlerden dolayı standartlaştırılmış bir desene uymayen belirli hesap veya kayıt kimlik numaralarını tanımlamanız gerekebilir. Örneğin, `Medical Record Numbers` aynı kuruluş içindeki birçok farklı harf ve sayı permütasyonlarından oluşabilir. İlk başta bir deseni tanımlamak zor olsa da, daha yakın inceleme genellikle aşırı sayıda geçersiz eşleşmeye neden olmadan tüm geçerli değerleri açıklayan bir düzeni daraltmanıza olanak tanır. Örneğin, "tüm MRN'lerin en az yedi karakter uzunluğunda olduğu, en az iki sayısal basamağı olduğu ve içinde harf varsa bir karakterle başladıkları" algılanabilir. Bu tür ölçütlere dayalı bir normal ifade oluşturmak, istenen tüm değerleri yakalarken gereksiz eşleşmeleri en aza indirmenize olanak tanır ve daha fazla analiz, farklı biçimleri açıklayan ayrı desenler tanımlayarak duyarlığı artırmanıza olanak tanıyabilir.

## <a name="create-a-rule-package-manually"></a>El ile kural paketi oluşturma

Bu yordamda, kural paketi (Unicode kodlamalı) olarak adlandırılan XML biçiminde bir dosya oluşturma ve ardından Güvenlik & Uyumluluğu PowerShell cmdlet'lerini kullanarak dosyayı Microsoft Purview'a yükleme işlemi gösterilmektedir.

> [!NOTE]
> Eşlediğiniz SIT çok sözcüklü doğrulayıcı kanıtı algılayabilirse, el ile oluşturulan bir kural paketinde tanımladığınız ikincil öğeler SIT ile eşlenebilir. Örneğin, bu destekleyici kanıt alanı bu deseni algılayan bir SIT ile eşlenmediyse, içerikteki içeriği alanlardan birinde karşıya yüklenen terimle `John Smith` ayrı ayrı karşılaştırıp `John` `Smith` bulduğumuz için ad `John Smith` ikincil öğe olarak eşleşmez.
>
> Microsoft 365 kiracıda 10 kural paketi sınırı vardır. Kural paketi rastgele sayıda hassas bilgi türü içerebileceğinden, bu yöntemi kullanarak yeni bir hassas bilgi türü tanımlamak istediğinizde yeni bir kural paketi oluşturmaktan kaçınabilir, bunun yerine mevcut bir kural paketini dışarı aktarabilir ve yeniden yüklemeden önce hassas bilgi türlerinizi XML'ye ekleyebilirsiniz.

1. Xml biçiminde (Unicode kodlama ile) aşağıdaki örneğe benzer bir kural paketi oluşturun. (Örneğimizi kopyalayabilir, değiştirebilir ve kullanabilirsiniz.)

   Kural paketinizi ayarlarken, .csv, .tsv veya kanal (|) sınırlandırılmış hassas bilgi kaynak tablo dosyanıza ve **edm.xml** şema dosyanıza doğru şekilde başvurdığınızdan emin olun. Örneğimizi kopyalayabilir, değiştirebilir ve kullanabilirsiniz. Bu örnek xml'de, EDM hassas türünüzü oluşturmak için aşağıdaki alanların özelleştirilmesi gerekir:

   - **RulePack kimliği & ExactMatch kimliği**: Guid oluşturmak için [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) kullanın.

   - **Veri deposu**: Bu alan, kullanılacak EDM arama veri depolarını belirtir. Yapılandırılan EDM Şemasının veri kaynağı adını sağlarsınız.

   - **idMatch**: Bu alan EDM için birincil öğeyi gösterir.
   - **Eşleşmeler**: Tam aramada kullanılacak alanı belirtir. DataStore için EDM Şeması'nda aranabilir bir alan adı sağlarsınız.
   - **Sınıflandırma**: Bu alan, EDM aramasını tetikleyen hassas bilgi türü eşleşmesini belirtir. Mevcut yerleşik veya özel hassas bilgi türünün adını veya GUID'sini kullanabilirsiniz.

   > [!NOTE]
   > Sağlanan SIT ile eşleşen herhangi bir dizenin karma olacağını ve hassas bilgi kaynağı tablosundaki her girişle karşılaştırılacağını unutmayın. Sınıflandırma öğesi için özel bir SIT seçerseniz performans sorunlarını önlemek için, içeriğin büyük bir yüzdesiyle eşleşecek bir sit kullanmayın. Örneğin, "herhangi bir sayı" veya "herhangi bir beş harfli sözcük" ile eşleşen bir sözcük. Destekleyici anahtar sözcükler ekleyerek veya özel sınıflandırma SIT tanımına biçimlendirme ekleyerek bunu ayırt edebilirsiniz.

   - **Eşleşme**: Bu alan idMatch'e yakın bulunan ek kanıtlara işaret eder.
   - **Eşleşmeler**: DataStore için EDM Şeması'nda herhangi bir alan adı sağlarsınız.
   - **Kaynak kimliğiBaşvuru:** Bu bölüm, birden çok yerel ayardaki hassas türün adını ve açıklamasını belirtir
     - ExactMatch Kimliği için GUID sağlarsınız.
     - **Adı** &  **description**: gerektiği gibi özelleştirin.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

2. Aşağıdaki PowerShell komutunu çalıştırarak kural paketini Upload:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> Kural paketi dosyasının söz dizimi, diğer hassas bilgi türleriyle aynıdır. Kural paketi dosyasının söz diziminin tüm ayrıntıları ve ek yapılandırma seçenekleri için ve PowerShell kullanarak hassas bilgi türlerini değiştirme ve silme yönergeleri için [PowerShell kullanarak özel bir hassas bilgi türü oluşturun](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Sonraki adım

- [Tam veri eşleşmesi hassas bilgi türünü test etme](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
