---
title: Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma
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
description: Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6bd411411c3075259bd3b9fc74ec3f558171fce7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526298"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma

Şema ve EDM SIT oluşturmak için Tam veri eşleşme şemasını ve hassas bilgi türü desen sihirbazını kullanabilir [veya el ile](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) [kullanabilirsiniz](#create-exact-data-match-schema-manually-and-upload). Şemayı oluşturmak için bir yöntem kullanarak ve daha sonra diğer yöntemi kullanarak düzenleyemezsiniz.

EDM tabanlı SITS veya uygulama hakkında bilginiz yoksa, kendinizi şu şekilde tanımanız gerekir:

- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Tek bir EDM şeması, aynı hassas veri tablosu kullanan birden çok hassas bilgi türü içinde kullanılabilir. Bir çalışma kiracısinde en çok 10 farklı EDM Microsoft 365 oluşturabilirsiniz.

## <a name="working-with-specific-types-of-data"></a>Belirli veri türleriyle çalışma

Performans nedenleriyle, gereksiz eşleşme sayısını en aza indirecek desenleri kullanmak kritik öneme sahip bir iştir. Örneğin, normal ifadeyi temel alan hassas bir bilgi türü kullanabilirsiniz.

`\b\w*\b`

Bu, herhangi bir belge veya e-postada her sözcük veya sayıyla aynı olabilir. Bu, hizmetin eşleşmelerle aşırı yüklenmiş olması ve doğru eşleşmeleri algılamayı kaçırmalarına neden olur. Daha hassas desenler kullanmak bu durumu önler. Burada, bazı yaygın veri türleri için doğru yapılandırmayı tanımlamaya yönelik bazı öneriler ve bulunabilirsiniz.

**E-posta** adresleri: E-posta adreslerini tanımlamak kolay olabilir, ancak içerikte çok yaygın olduğundan birincil alan olarak kullanılırsa sistemde önemli yüke neden olabilir. Bunları yalnızca ikincil kanıt olarak kullanın. Temel kanıt olarak kullanılmaları gerekirse, `From` `To` e-postalarda kullanımlarını veya e-postalarda alanlarını dışarıda tutmak için mantık kullanan özel ve hassas bir bilgi türü tanımlamaya ve eşleşmesi gereken gereksiz dize sayısını azaltmak için, şirketinizin e-posta adresiyle gönderilenleri hariç tutmak için deneyin.

**Telefon:** Telefon, ülke ön ekleri, alan kodları ve ayırıcılar dahil veya bu sayılar çok farklı biçimlerde olabilir. Yükü en düşük düzeyde tutarken hatalı negatif değerleri azaltmak için, bunları yalnızca ikincil öğe olarak kullanın, parantez ve tire gibi olası tüm ayırıcıları dışlama ve yalnızca hassas veri tablonıza her zaman telefon numarasında yer alan bölümü dahil eder.

**Kişinin adları**: Bu EDM türü için sınıflandırma öğesi olarak normal bir ifadeyi temel alan hassas bir bilgi türü kullanıyorsanız, bu kişilerin adlarını birincil öğe olarak kullanmayın, çünkü bunlar sık kullanılan sözcüklerden ayırt etmek zordur.

İşlenecek çok sayıda eşleşme oluşturabilen proje kodu adı gibi, belirli bir desenle tanımlaması zor bir birincil öğe kullanmak zorundaysanız, EDM türünüz için sınıflandırma öğesi olarak kullanabileceğiniz hassas bilgi türüne anahtar sözcükleri dahil edin. Örneğin, proje kodu adlarını normal sözcüklerden farklı kullanıyorsanız, `project` EDM türünüz için sınıflandırma öğesi olarak kullanılan hassas türdeki proje adı normal ifade tabanlı desene yakın bir şekilde gerekli ek kanıt olarak bu sözcüğü kullanabilirsiniz. Ya da EDM SIT'iniz için sınıflandırma öğesi olarak normal bir sözlüğü temel alan hassas bir tür kullanmayı düşünebilirsiniz.

Sayısal dizeleri eşleşmeye çalışırken basamak sayısı veya varsa başlangıç basamakları gibi izin verilen sayı aralıklarını belirtin. Görece esnek bir sayı aralığını eşleşmeniz gerekirse, eşleşme sayısını azaltmak için temel SIT'te anahtar sözcükler kullanabilirsiniz. Örneğin, 7-11 basamaklı hesap numaralarını eşleşmeye çalışılıyorsa, `account`gerekli ek kanıt olarak , `customer``acct.` , sözcüklerini SIT'e ekleyin. Bu, EDM tarafından işlenecek eşleşme sınırlarını aşmaya neden olan gereksiz eşleşme olasılığını azaltır.

Birincil öğe olarak eklemeniz gereken bir alan çok büyük miktarda eşleşmeye neden olan basit bir düzeni izliyorsa ve anahtar sözcüklerin varlığını hassas bilgi türüne ek kanıt olarak ek kanıt olarak ekley belirlene bilgilere ek olarak, alternatif olarak bu desenin tekrarlarının en az sayıda olmasını da gerekli yapabilirsiniz. Örneğin, EDM ile eşleştirilebilir olası beş basamaklı slasımları çevreleyen diğer en az 29 başka beş basamaklı sayıları belirlemek için aşağıdaki şekilde tanımlanan özel duyarlı bilgi türünü kullanabilirsiniz:

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

Bazı durumlarda, geçmiş nedenlerden dolayı standart bir düzende uymayan belirli hesap veya tanımlama numaraları tanımlamanız gerekir. Örneğin, `Medical Record Numbers` aynı kuruluş içindeki harflerin ve sayıların birçok farklı permütasyondan biri olabilir. Bir düzeni belirlemek ilk başta zor olsa da, genellikle daha yakın denetim, çok fazla geçersiz eşleşmeye neden olmadan tüm geçerli değerleri açıklayan bir düzeni daraltmanıza olanak sağlar. Örneğin, "tüm MRN'lerde en az yedi karakter uzunluğunda, en az iki sayısal rakam olduğu ve içinde harf varsa bunların bir harfle başlamaları" algı edilebilir. Bu gibi ölçütlere dayalı normal bir ifade oluşturmak, tüm istenen değerleri alırken gereksiz eşleşmeleri en aza indirmeyi sağlayacaktır; daha fazla çözümleme yapmak ise farklı biçimleri açıklayan ayrı desenler tanımlayarak daha fazla duyarlılık sağlar.

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Tam Veri Eşleşme Şemasını ve Hassas Bilgi Türü Sihirbazı'nı kullanma

Şema dosyası oluşturma işlemini basitleştirmeye yardımcı olmak için bu sihirbazı kullanabilirsiniz.

## <a name="pre-requisites"></a>Önkoşullar

- Hassas bilgi türüne göre [tam veri eşleşmesi için kaynak verileri dışarı aktarma konusunda adımları uygulayın](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Tam veri eşleşme şemasını ve hassas bilgi türü desen sihirbazını kullanma

1. Kiracınız için Microsoft 365 Uyumluluk Merkezi'nde Veri **sınıflandırmasıExact** >  verileri,EDM  > **şemaları ile eşleri.**

2. Şema **sihirbazı yapılandırma açılır şemasını açmak için EDM** şeması oluştur'a tıklayın.

   ![EDM şeması oluşturma sihirbazı yapılandırması uçarak çıkış.](../media/edm-schema-wizard-1.png)

3. Uygun bir Ad **ve Açıklama** **girin**.

4. **Şemanın tamamı için bu davranışın tüm şema alanları** için de yoksay'ı seçin. EDM'i büyük/harf veya sınırlayıcıları yoksayacak şekilde yapılandırma hakkında daha [](#using-the-caseinsensitive-and-ignoreddelimiters-fields) fazla bilgi edinmek için, bu özellikle ilgili daha fazla ayrıntı için bkz. Büyük/harfe duyarlı değil ve yoksayılmışDelimiters alanlarını kullanma.

5. Şema alanınız # **1 için istediğiniz değerleri doldurun** ve gerektiğinde başka alanlar ekleyin. Her şema alanı, hassas bilgi kaynağı dosyandaki sütun başlıklarıyla aynı olmalıdır.

6. 2010/2016 için aşağıdakiler için alan başına değerleri ayarlayın:
    1. **Alan aranabilir**
    1. **Alan büyük/harfe duyarlı değildir**
    1. **Bu alan için yoksaymak istediğiniz sınırlayıcıları ve noktalama işaretlerini seçin**
    1. **Bu alan için özel sınırlayıcılar ve noktalama işaretleri girin**

   > [!IMPORTANT]
   > En az bir, ancak şema alanlarınızı beşten fazla aranabilir olarak belirlen olmalıdır.

7. **Kaydet**'i seçin. Şemanız artık listelenir ve kullanılabilir.

   > [!IMPORTANT]
   > Şemayı kaldırmak istiyorsanız ve zaten bir EDM duyarlı bilgi türüyle ilişkilendirilmişse, önce EDM duyarlı bilgi türünü silmeniz gerekir; ardından şemayı silebilirsiniz. Veri deposuyla ilişkilendirilmiş bir şemanın silinmesi, veri depolarını da 24 saat içinde siler.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>EDM şema dosyasını XML biçiminde dışarı aktarma

EDM şemasını EDM şema sihirbazında oluşturduysanız, EDM şema dosyasını XML biçiminde dışarı aktarmanız gerekir. Bu değer Karma'ya ihtiyacınız vardır ve hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı [tablosuna yükleyebilirsiniz](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. EDM şema dosyasını dışarı aktarma için şu söz dizimlerini kullanın:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Daha sonra kullanmak üzere bu dosyayı kaydedin.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>Şemayı el ile tam olarak eşleşme ve karşıya yükleme

Şema dosyasında, söz dizimi kullanarak hassas bilgi kaynağı tablosunda yer alan her sütun için bir girdi yapılandırabilirsiniz:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Büyük/harfe duyarlı değil ve yoksayılanDelimiters alanlarını kullanma

Aşağıdaki şema XML örneği, *caseInsensitive* ve *ignoredDelimiters alanlarını* kullanır.

Büyük/küçük *harfe duyarlı değil* `true` alanını şema tanımınıza bu değere ayarlanmazsa, EDM büyük/küçük harf farklılıklarına dayalı olarak öğeyi hariç tanımaz. Örneğin, EDM, **FOO-1234** ve **fOo-1234** değerlerinin alanla aynı olduğunu `PatientID` gösterir.

Desteklenen karakterlerle *ignoreDelimiters alanını* da dahil etmek için, EDM bu karakterleri yoksayacaktır. Dolayısıyla EDM, **FOO-1234** ve **FOO#1234** değerlerini alanla aynı olduğunu `PatienID` görebilir.

`caseInsensitive` `ignoredDelimiters` Hem kullanılan hem de kullanılan bu örnekte, EDM **FOO-1234** ve **fOo#1234'ü** aynı görüyor ve öğeyi hasta kaydı hassas bilgi türünde sınıflandırıyor.

Bu parametrelerin her ikisi de alan temelinde kullanılır.

> [!IMPORTANT]
> Boşlukları *yoksayılacak* şekilde yapılandırsanız, bu yalnızca birincil alan sütunları için geçerli olur ve çok sözcüklü dizeleri algılayan hassas bir bilgi türü tanımlanır. Aksi takdirde, çözümleme yapılan içerikte her sözcük için ayrı ayrı karşılaştırma yapılır.

*YoksayılanDelimiters* bayrağı alfasayısal olmayan karakterleri destekler; aşağıda bazı örnekler verilmiştir:

- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \;

Bayrak `ignoredDelimiters` şunları desteklemez:

- 0-9 karakterleri
- A-Z
- a-z
- \"
- \,

> [!IMPORTANT]
> EDM hassas bilgi türlerinizi *tanımlarken,Delimiters'i yoksayMaters* , EDM desenli birincil öğeyle ilişkili Sınıflandırma duyarlı bilgi türünün bir öğedeki içeriği nasıl tanımyeceğini etkilemez. *Dolayısıyla,Delimiters'i* aranabilir bir alan için yapılandırıyorsanız, bu alana dayalı olarak birincil öğe için kullanılan hassas bilgi türünün bu karakterlerle birlikte ve bu karakterler olmadan dizeler seçmesi gerekir.
>
> Hassas bilgi kaynağı tablomdaki sütun sayısıyla şemadaki alanların sayısı eşleşmeli, sıra önemli değildir.

1. Şemayı XML biçiminde tanımlayın (aşağıdaki örneğimize benzer). Bu şema dosyasını **edm.xml** ve bunu hassas bilgi kaynağı tablodaki her sütun için söz dizimi kullanan bir satır olacak şekilde yapılandırabilirsiniz:

      `\<Field name="" searchable=""/\>`.

      - Alan adı değerleri için *sütun adlarını* kullanın.
      - *Aranabilir olmak istediğiniz alanlar için aranabilir="true"* kullanın ve en çok 5 alanlık birincil alanlar kullanın. En az bir alanın aranabilir olması gerekir.

      Örnek olarak, aşağıdaki XML dosyası aranabilir olarak belirtilen beş alanla hasta kayıtları veritabanının şemasını tanımlar: *PatientID*, *MRN*, *SSN*, *Telefon* *ve DOB*.

      (Örneğimizi kopyalayıp değiştirebilir ve kullanabilirsiniz.)

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

   EDM şema dosyasını XML biçiminde oluşturduktan sonra, bunu bulut hizmetine yüklelisiniz.

2. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

3. Veritabanı şemasını karşıya yüklemek için aşağıdaki komutu çalıştırın:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Aşağıdaki gibi onaylamanız istenir:

      > Onayla
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için yeni EDM Şeması aktarılır.
      >
      > \[Y\] Evet \[A\] Yes to All \[N No \[\] L\] No to All \[?\] Yardım (varsayılan değer "Y"dir):

   > [!TIP]
   > Değişikliklerinizin onay olmadan gerçekleşmesini istemiyorsanız, 3. `-Confirm:$true` Adım'da bu değişiklikleri kullanmayın.

> [!NOTE]
> EDMSchema'yı eklemelerle güncelleştirmek 10-60 dakika arasında sürebilir. Eklemeleri kullanan adımları yürütmeden önce güncelleştirmenin tamamlanması gerekir.

## <a name="next-step"></a>Sonraki adım

- [Hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı tablosuna karma sağlama ve yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)