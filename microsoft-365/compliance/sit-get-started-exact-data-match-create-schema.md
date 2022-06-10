---
title: Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma
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
description: Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 080bdff37893bcf0d41414c066b51727d2650f7a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017174"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Tam veri eşleşmesine dayalı hassas bilgi türleri için tam veri eşleşmesi şeması oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Şemayı ve EDM SIT'i oluşturmak için [Tam veri eşleştirme şemasını ve hassas bilgi türü desenini kullanma sihirbazını](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) veya [el ile kullanabilirsiniz](#create-exact-data-match-schema-manually-and-upload). Ayrıca, şemayı oluşturmak için bir yöntem kullanarak her ikisini de birleştirebilir ve daha sonra diğer yöntemi kullanarak düzenleyebilirsiniz.

EDM tabanlı SITS veya uygulamaları hakkında bilgi sahibi değilseniz, şunları tanımanız gerekir:

- [Hassas bilgi türleri hakkında daha fazla bilgi edinme](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Aynı hassas veri tablosunu kullanan birden çok hassas bilgi türünde tek bir EDM şeması kullanılabilir. bir Microsoft 365 kiracısında en fazla 10 farklı EDM şeması oluşturabilirsiniz.



## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Tam Veri Eşleştirme Şemasını ve Hassas Bilgi Türü Sihirbazını Kullanma

Şema dosyası oluşturma işlemini basitleştirmeye yardımcı olması için bu sihirbazı kullanabilirsiniz.

## <a name="pre-requisites"></a>Önkoşullar

- [Tam olarak eşleşen hassas bilgi türü için Kaynak verileri dışarı aktarma](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) başlığındaki adımları gerçekleştirin.

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Tam veri eşleme şemasını ve hassas bilgi türü deseni sihirbazını kullanma

1. Kiracınızın Microsoft Purview uyumluluk portalında **Veri sınıflandırması** > **Tam veriler****EDM şemalarıyla eşleşir** >  bölümüne gidin.

2. Şema sihirbazı yapılandırması açılır öğesini açmak için **EDM şeması oluştur'u** seçin.

   ![EDM şema oluşturma sihirbazı yapılandırma açılır öğesi.](../media/edm-schema-wizard-1.png)

3. Uygun bir **Ad** ve **Açıklama** girin.

4. Şemanın **tamamı için bu davranışı istiyorsanız Tüm şema alanları için sınırlayıcıları ve noktalama işaretlerini yoksay'ı** seçin. EDM'yi büyük/küçük harf veya sınırlayıcıları yoksayacak şekilde yapılandırma hakkında daha fazla bilgi edinmek için bu özellik hakkında daha fazla bilgi için bkz. [CaseInsensitive ve ignoredDelimiters alanlarını kullanma](#using-the-caseinsensitive-and-ignoreddelimiters-fields) .

5. **Şema alanınız #1** için istediğiniz değerleri doldurun ve gerektiğinde daha fazla alan ekleyin. Her şema alanı, hassas bilgi kaynak dosyanızdaki sütun üst bilgileriyle aynı olmalıdır.

6. İstersen, aşağıdakiler için alan başına değerleri ayarlayın:
    1. **Alan aranabilir**
    1. **Alan büyük/küçük harfe duyarlı değil**
    1. **Bu alan için yoksaymak üzere sınırlayıcıları ve noktalama işaretlerini seçin**
    1. **Bu alan için özel sınırlayıcılar ve noktalama işaretleri girin**

   > [!IMPORTANT]
   > En az bir tane, ancak şema alanlarınızın beşten fazlası aranabilir olarak belirlenmelidir.

7. **Kaydet**'i seçin. Şemanız artık listelenecek ve kullanıma sunulacaktır.

   > [!IMPORTANT]
   > Bir şemayı kaldırmak istiyorsanız ve zaten bir EDM hassas bilgi türüyle ilişkiliyse, önce EDM hassas bilgi türünü silmeniz gerekir, ardından şemayı silebilirsiniz. Kendisiyle ilişkilendirilmiş bir veri deposu olan bir şema silindiğinde, veri deposu da 24 saat içinde silinir.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>EDM şema dosyasını XML biçiminde dışarı aktarma

EDM şemasını EDM şema sihirbazında oluşturduysanız, EDM şema dosyasını XML biçiminde dışarı aktarmanız gerekir. Karma'da buna ihtiyacınız olacak [ve hassas bilgi türleri aşamasıyla tam olarak eşleşen veriler için hassas bilgi kaynağı tablosunu karşıya yükleyeceksiniz](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. EDM şema dosyasını dışarı aktarmak için şu söz dizimini kullanın:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Bu dosyayı daha sonra kullanmak üzere kaydedin.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>El ile tam veri eşleştirme şeması oluşturma ve karşıya yükleme

Şema dosyasında, söz dizimini kullanarak hassas bilgi kaynağı tablosundaki her sütun için bir girdi yapılandırın:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>caseInsensitive ve ignoredDelimiters alanlarını kullanma

Aşağıdaki şema XML örneği *caseInsensitive* ve *ignoredDelimiters* alanlarını kullanır.

şema tanımınızda değerine ayarlanmış `true` *caseInsensitive* alanını eklediğinizde, EDM büyük/küçük harf farklarına göre bir öğeyi dışlamaz. Örneğin, EDM **FOO-1234** ve **fOo-1234** değerlerini alan için `PatientID` aynı olarak görür.

*IgnoredDelimiters* alanını desteklenen karakterlerle eklediğinizde, EDM bu karakterleri yoksayar. Bu nedenle EDM **, FOO-1234** ve **FOO#1234** değerlerinin alan için `PatienID` aynı olduğunu görür.

Hem hem de `caseInsensitive` `ignoredDelimiters` kullanılan bu örnekte, EDM **FOO-1234** ve **fOo#1234'i** aynı görür ve öğeyi hasta kaydı hassas bilgi türü olarak sınıflandırır.

Bu parametrelerin her ikisi de alan bazında kullanılır.

> [!IMPORTANT]
> *Boşlukları* yoksayılacak şekilde yapılandırdıysanız, bu yalnızca birincil alan sütunları için ve çok sözcüklü dizeleri algılayan hassas bir bilgi türünün tanımlandığı için etkili olur. Aksi takdirde, analiz edilen içerikteki her bir sözcükle karşılaştırma yapılır.

*ignoredDelimiters* bayrağı alfasayısal olmayan karakterleri destekler, aşağıda bazı örnekler verilmiştir:

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

Bayrak `ignoredDelimiters` aşağıdakileri desteklemez:

- 0-9 arası karakterler
- A-Z
- a-z
- \"
- \,

> [!IMPORTANT]
> EDM hassas bilgi türünüzü tanımlarken *ignoreDelimiters* , bir EDM desenindeki birincil öğeyle ilişkili Sınıflandırmaya duyarlı bilgi türünün bir öğedeki içeriği nasıl tanımladığını etkilemez. Bu nedenle, aranabilir bir alan için *ignoreDelimiters* yapılandırıyorsanız, bu alanı temel alan birincil öğe için kullanılan hassas bilgi türünün bu karakterlerin hem bulunduğu hem de bulunmadığı dizeleri seçtiğinden emin olmanız gerekir.
>
> Hassas bilgi kaynağı tablonuzdaki sütunların sayısı ve şemanızdaki alanların sayısı eşleşmelidir; sıra önemli değildir.

1. Şemayı XML biçiminde tanımlayın (aşağıdaki örneğimize benzer). Bu şema dosyasını **edm.xml** adlandırın ve hassas bilgi kaynağı tablosundaki her sütun için söz dizimini kullanan bir satır olacak şekilde yapılandırın:

      `\<Field name="" searchable=""/\>`.

      - *Alan adı* değerleri için sütun adlarını kullanın.
      - Aranabilir olmasını istediğiniz alanlar ve en fazla 5 alana kadar birincil alanlar için *searchable="true"* kullanın. En az bir alan aranabilir olmalıdır.

      Örnek olarak, aşağıdaki XML dosyası bir patient records veritabanının şemasını tanımlar ve aranabilir olarak belirtilen beş alan vardır: *PatientID*, *MRN*, *SSN*, *Telefon* ve *DOB*.

      (Örneğimizi kopyalayabilir, değiştirebilir ve kullanabilirsiniz.)

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

   EDM şema dosyasını XML biçiminde oluşturduktan sonra bulut hizmetine yüklemeniz gerekir.

2. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

3. Veritabanı şemasını karşıya yüklemek için aşağıdaki komutu çalıştırın:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Aşağıdaki gibi onaylamanız istenir:

      > Onaylamak
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için yeni EDM Şeması içeri aktarılacak.
      >
      > \[Y\] Evet \[\] Tümüne \[Evet N\] Hayır \[L\] Tümüne \[Hayır?\] Yardım (varsayılan olarak "Y"dir):

   > [!TIP]
   > Değişikliklerinizin onay olmadan gerçekleşmesini istiyorsanız 3. Adım'da kullanmayın `-Confirm:$true` .

> [!NOTE]
> EDMSchema'nın eklenmesi 10-60 dakika arasında sürebilir. Eklemeleri kullanan adımları yürütmeden önce güncelleştirmenin tamamlanması gerekir.

## <a name="next-step"></a>Sonraki adım

- [Tam veri eşleşmeli hassas bilgi türleri için hassas bilgi kaynak tablosu karması oluşturma ve karşıya yükleme](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)
