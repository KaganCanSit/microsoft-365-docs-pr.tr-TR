---
title: Hassas bilgi türü/kural paketiyle tam olarak eşleşmesi için veri oluşturma
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
description: Hassas bilgi türü/kural paketiyle tam olarak eşleşmesi için veri oluşturma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e44d18bc1a779ace95fb2f64171ff0bf91de57ed
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526048"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Hassas bilgi türü/kural paketiyle tam olarak eşleşmesi için veri oluşturma

Uyumluluk merkezinde EDM şemasını ve SIT sihirbazını kullanarak veya kural paketi XML dosyasını el ile oluşturarak, tam veri eşleşmesi ( [EDM](#use-the-edm-schema-and-sit-wizard) ) duyarlı bilgi türü (SIT) [oluşturabilirsiniz](#create-a-rule-package-manually). Şemayı oluşturmak için bir yöntem kullanarak ve daha sonra diğer yöntemi kullanarak düzenleyemezsiniz.

EDM tabanlı SITS veya uygulama hakkında bilginiz yoksa, şunları tanımanız gerekir:

- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>EDM şeması ve SIT sihirbazını kullanma

Bu sihirbazı kullanarak hassas bilgi türü (SIT) dosyalarınızı oluşturabilir ve bu işlemi basitleştirebilirsiniz.

EDM Duyarlı Bilgi türü bir veya birden çok düzenden oluşur. Her desen, belge veya e-postada hassas içeriği tanımlamak için kullanılacak kanıtın (şemadan alanlar) bir bileşimini açıklar.

## <a name="pre-requisites"></a>Önkoşullar

Şu makalelerde adımları gerçekleştirin:

1. [Hassas bilgi türüne göre tam veri eşleşmesi için kaynak verileri dışarı aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı tablosuna karma sağlama ve yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Sihirbaz veya PowerShell aracılığıyla kural paketi XML dosyası kullanarak EDM hassas bilgi türü oluşturuyor olun, kullanıcı arabirimi aracılığıyla özel hassas bilgi türünü oluşturmak, test etmek ve dağıtmak için Genel yönetici veya Uyumluluk yöneticisi izinlerine sahip olmak gerekir. Bkz[. Office 365'da yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).
- Birincil öğelere duyarlı bilgi türü olarak kullanmak üzere yerleşik SITS'lerden birini seçin.
  - Yerleşik hassas bilgi türlerinden hiçbiri seçtiğiniz sütundaki veriyle eşlerizse, bunu yapmak için özel bir hassas bilgi türü oluşturmanız gerekir.
  - Şemadaki birincil öğe sütunu için Yoksayılan Sınırlayıcılar seçeneğini belirttiyseniz, oluşturuğum özel SIT'in verileri seçili sınırlayıcılarla ve bu sınırlayıcılar olmadan da aynı olduğundan emin olun.
  - Yerleşik bir SIT kullanıyorsanız, seçmek istediğiniz dizelerin tam olarak algılandığına ve çevresindeki karakterleri içermeyecek veya hassas bilgi tablolarında depolandığı şekilde dizenin geçerli bir bölümünü dışarıda tutmayacak şekilde emin olun.

Uyumluluk [merkezi'nde Hassas bilgi türü varlık](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) [tanımları ve Özel hassas bilgi türleri oluşturma konularına bakın](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Tam veri eşleşme şemasını ve hassas bilgi türü desen sihirbazını kullanma

1. Kiracınız için Microsoft 365 Uyumluluk Merkezi'nde Veri **sınıflandırmasıExact** >  **veri eşleşmeleri'ne gidin**.

2. Hassas **bilgi türü yapılandırma sihirbazını açmak için** **EDM duyarlı bilgi türlerini ve EDM** duyarlı bilgi türü oluştur'ı seçin.

3. Var **olan bir EDM şeması seç'i** seçin ve Temel alınan hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma altında [oluşturduğunuz şemayı seçin](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. **Sonraki'yi seçin** ve Desen **oluştur'a seçin**.

5. Güven düzeyi **ve Birincil** **öğeyi seçin**. Güven düzeyleri hakkında daha fazla bilgi edinmek için bkz[. Hassas bilgi türleri hakkında bilgi.](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)

6. Birincil **öğenin hassas bilgi türünü** seçarak, belgedeki hangi metnin birincil öğe alanında yer alan tüm değerlerle karşılaştırıl olacağını tanımlayın. Kullanılabilir [hassas bilgi türleri hakkında daha fazla bilgi](sensitive-information-type-entity-definitions.md) edinmek için bkz. Hassas Bilgi Türü Varlık Tanımları.

   > [!IMPORTANT]
   > Bulmak istediğiniz içeriğin biçimine yakın bir bilgi türü seçin. Tüm metin dizeleri ile eşleşen bir tür veya tüm sayılar gibi gereksiz içerikle eşleşen hassas bir bilgi türü seçmek sistemde aşırı yüke neden olabilir ve bu da hassas bilgilerin atlandırılamalarına neden olabilir. Burada kullanmak üzere hassas bir bilgi türü seçme önerileri için, bu belgelerde Tam Veri Eşleştirmeye Giriş makalesinde En İyi Yöntemler bölümüne bakın.

7. Destekleyen **öğelerinizi ve eşleşme seçeneklerinizi** seçin.

8. Bitti  ve **Sonraki'yi seçin**.

9. İstediğiniz Güven düzeyi **ve karakter yakınlığınızı seçin**. Bu, EDM'ye duyarlı tüm bilgi türü için varsayılan değerdir.

10. EDM **duyarlı bilgi** türünüz için ek desenler oluşturmak için Desen oluştur'a tıklayın.

11. **Sonraki'yi** seçin ve yöneticiler **için Ad** **ve Açıklama yazın**.

12. Gözden geçir'i ve **Gönder'i seçin**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Hassas bilgi türü desenini düzenleme veya silme

1. Uyumluluk **merkeziVeri** >  **sınıflandırmasıExact** >  **veri eşleşmeleri**.

2. **EDM'ye duyarlı bilgi türlerini seçin**.

3. Düzenlemek istediğiniz EDM SIT'i seçin.

4. **EDM duyarlı bilgi türünü düzenle'yi veya** **çıktıdan EDM duyarlı bilgi** türünü sil'i seçin.

## <a name="create-a-rule-package-manually"></a>El ile kural paketi oluşturma

Bu yordamda, kural paketi olarak adlandırılan XML biçiminde bir dosya oluşturma (Unicode kodlamayla) ve sonra Uyumluluk merkezi PowerShell cmdlet'lerini kullanarak Microsoft 365'e yükleme işlemi görüntülenir.

> [!NOTE]
> Eşleniyladığınız SIT çok sözcüklüroborl kanıtı algılayana kadar, el ile oluşturulan bir kural paketinde tanımladığınız ikincil öğeler SIT'e eşilebilir. Örneğin, `John Smith` `John` `Smith` `John Smith` bu ad ikincil bir öğeyle eşleşmez çünkü bu deseni algılayan bir SIT alanıyla eşlenmemişse, bu içerikle alanlardan birini karşıya yüklenen terimle ayrı olarak karşılaştırabilir ve bulunuruz.
>
> Bir kiracıda en fazla 10 kural Microsoft 365 vardır. Kural paketi rastgele bir sayıda hassas bilgi türü içereb, bu yöntemi kullanarak yeni bir hassas bilgi türü tanımlamak istediğiniz her durumda yeni bir kural paketi oluşturmaktan kaçınabilirsiniz; bunun yerine var olan bir kural paketini dışarı aktarın ve hassas bilgi türlerinizi yeniden yüklemeden önce XML'ye ekleyin.

1. Aşağıdaki örnekte olduğu gibi XML biçiminde (Unicode kodlamayla) bir kural paketi oluşturun. (Örneğimizi kopyalayıp değiştirebilir ve kullanabilirsiniz.)

   Kural paketinizi ayar hazırlarken, .csv, .tsv veya pipe (|) sınırlandırılmış hassas bilgi kaynağı tablo dosyanıza ve şema dosyanıza doğru **edm.xml** emin olun. Örneğimizi kopyalayıp değiştirebilir ve kullanabilirsiniz. Bu örnek xml'de, EDM duyarlı türlerinizi oluşturmak için aşağıdaki alanların özelleştirilebilir:

   - **RulePack id & ExactMatch id**: [Guid oluşturmak için New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) kullanın.

   - **Veri deposu**: Bu alanda, kullanılacak EDM arama veri deposu belirtir. Yapılandırılmış EDM Şemasının veri kaynağı adını siz sağlarsınız.

   - **idMatch**: Bu alan EDM'nin birincil öğesini ifade ediyor.
   - **Eşleşmeler**: Tam aramada kullanılacak alanı belirtir. DataStore için EDM Şemasında aranabilir bir alan adı sağlarsınız.
   - **Sınıflandırma**: Bu alan EDM aramalarını tetikleyen hassas bilgi türünü belirtir. Var olan yerleşik veya özel duyarlı bilgi türünün adını veya GUID'sini kullanabilirsiniz.

   > [!NOTE]
   > SIT ile eşleşen tüm dizelerin, hassas bilgi kaynağı tablosunda yer alan tüm girdilerle karma kodlu olacağını ve karşıt olacağını lütfen dikkat edin. Sınıflandırma öğesi için özel bir SIT seçerseniz performans sorunlarını önlemek için, içeriğin büyük bir yüzdesine uygun bir sit kullanmayın. Örneğin, "herhangi bir sayı" veya "herhangi bir beş harfli sözcük" ile eşleşen bir sözcük. Bunu, destekleyen anahtar sözcükler ekleyerek veya özel sınıflandırma SIT tanımında biçimlendirme ekleyerek ayırt etmek için kullanabilirsiniz.

   - **Eşleşme**: Bu alan, idMatch'in yakınlığında bulunan ek kanıtı ortaya ediyor.
   - **Eşleşmeler**: Veri Deposu için EDM Şemasında herhangi bir alan adı sağlarsınız.
   - **Kaynak kimliğiRef:** Bu bölüm, birden çok yerel ayarda hassas türün adını ve açıklamasını belirtir
     - ExactMatch ID için GUID sağlar.
     - **Ad** &  **açıklama**: gerektiğinde özelleştirin.

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

2. Upload PowerShell komutunu çalıştırarak kural paketinin sonlarını yapın:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> Kural paketi dosyasının söz dizimi, diğer hassas bilgi türleriyle aynıdır. Kural paketi dosyasının söz dizimi ve ek yapılandırma seçenekleriyle ilgili tam ayrıntılar ve PowerShell kullanarak hassas bilgi türlerini değiştirme ve silme yönergeleri için, [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell) kullanarak özel bir hassas bilgi türü oluşturun.

## <a name="next-step"></a>Sonraki adım

- [Hassas bilgi türüyle tam olarak eşan bir veri sınaması](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
