---
title: Yerleşik hassas bilgi türünü özelleştirme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Özel, hassas bir bilgi türünün, kurum 365'in  ihtiyaçlarını karşılayacak kuralları kullanmanızı sağlayacak şekilde nasıl oluşturulacaklarını öğrenin.
ms.openlocfilehash: 8393da8e2b2607692983010783d9ae110f268f4c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010050"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Yerleşik hassas bilgi türünü özelleştirme

İçerikte hassas bilgiler için bu bilgileri kural olarak adlandırılan bölümde *açıklamalısiniz*. Veri kaybı önleme (DLP), hemen kullanabileceğiniz en yaygın hassas bilgi türlerine yönelik kurallar içerir. Bu kuralları kullanmak için, bunları bir ilkeye dahil etmek gerekir. Bu yerleşik kuralları, kuruma özel ihtiyaçlarına göre ayarlamak ve bunu yapmak için özel bir hassas bilgi türü oluşturabilirsiniz. Bu konu başlığı altında, mevcut kural koleksiyonunu içeren XML dosyasını nasıl özelleştirebileceğiniz ve daha çok olası kredi kartı bilgisi yelpazesini nasıl algılayebileceğiniz açıklanmıştır.

Bu örneği alıp diğer yerleşik hassas bilgi türlerine uygulayabilirsiniz. Varsayılan hassas bilgi türlerinin ve XML tanımlarının listesi için bkz. [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Geçerli kuralların XML dosyasını dışarı aktarma

XML'yi dışarı aktarmanız için, [Uzak PowerShell aracılığıyla Güvenlik ve Uyumluluk Merkezi'ne bağlanmanız gerekir](/powershell/exchange/connect-to-scc-powershell).

1. PowerShell'de, kuruluş kurallarını ekranda görüntülemek için aşağıdakini yazın. Kendi kurallarınızı oluşturmadıysanız, yalnızca "Microsoft Kural Paketi" etiketli varsayılan yerleşik kuralları görüntülersiniz.

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Aşağıdakini yazarak, kuruluş kurallarını bir değişkende depolar. Bir şeyin değişkende depolanması, daha sonra uzak PowerShell komutlarında çalışan bir biçimde kolayca kullanılabilir.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Aşağıdakini yazarak tüm verilerle biçimlendirilmiş bir XML dosyası yapın.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Kural paketinizin gerçekte depolandığı dosya konumunu kullanmaya emin olun. `C:\custompath\` bir yer tutucudur.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>XML'de değiştirmek istediğiniz kuralı bulma

Yukarıdaki cmdlet'ler, sağlamamız *varsayılan* kuralları içeren kural koleksiyonunun tamamını dışarı aktardı. Ardından, özel olarak değiştirmek istediğiniz Kredi Kartı Numarası kuralına bakmanız gerekir.

1. Önceki bölümde dışarı aktarmış olduğunuz XML dosyasını açmak için bir metin düzenleyicisi kullanın.

2. Sayfayı aşağı `<Rules>` kaydırarak, DLP kurallarını içeren bölümün başlangıcı olan etikete gidin. Bu XML dosyası kural koleksiyonunun tamamına ilişkin bilgileri içerdiği için, en üstte kuralları bulmak için geçmiş bilgileri kaydırmanız gereken başka bilgiler içerir.

3. Kredi *Func_credit_card* kural tanımını bulmak için aşağıdakilere bakın. XML'de, kural adları boşluk içeremez, dolayısıyla boşluklar çoğunlukla alt çizgilerle değiştirilir ve kural adları bazen kısaltılmış olur. Buna örnek olarak, kısaltılmış SSN'nin kısaltması olan ABD Sosyal Güvenlik numarası _kuralı ve bir örnek de yer almaktadır_. Kredi Kartı Numarası kuralı XML aşağıdaki kod örneğine benzer.

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

Artık XML'de Kredi Kartı Numarası kural tanımını bula sayesinde, kuralın XML'ini gereksinimlerinizi karşılayacak şekilde özelleştirebilirsiniz. XML tanımlarını yenilemek için, bu konunun [sonundaki](#term-glossary) Terim sözlüğüne bakın.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>XML'yi değiştirme ve yeni bir hassas bilgi türü oluşturma

İlk olarak, yeni bir hassas bilgi türü oluşturmanız gerekir çünkü varsayılan kuralları doğrudan değiştiremezsiniz. Güvenlik ve Uyumluluk Merkezi PowerShell'de özel bir hassas bilgi türü oluşturma konusunda ana hatlarıyla açıklanan özel hassas bilgi [türleriyle çok & şey kullanabilirsiniz](create-a-custom-sensitive-information-type-in-scc-powershell.md). Bu örnekte, basit bir şekilde tut hem de yalnızcaroborlu kanıtı kaldıran ve Kredi Kartı Numarası kuralına anahtar sözcükler eklemiz.

Tüm XML kuralı tanımları aşağıdaki genel şablonda yerleşik olarak yer almaktadır. Şablona Kredi Kartı Numarası tanımı XML'sini kopyalayıp yapıştırmanız, bazı değerleri değiştirmeniz gerekir (". . ." yer tutucularını ve sonra da değiştirilmiş XML'yi ilkelerde değiştirilebilir yeni bir kural olarak karşıya yükleyin.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

Artık, aşağıdaki XML'ye benzer bir şeye sahipsiniz. Kural paketleri ve kurallar benzersiz GUID'leri tarafından tanımlandıklarından, biri kural paketi ve bir tane de Kredi Kartı Numarası kuralının GUID'sini değiştirmek için olmak olmak zorunda. Aşağıdaki kod örneğinde yer alan varlık kimliği için GUID, yeni bir tanımla değiştirmeniz gereken yerleşik kural tanımımız için geçerli olandır. GUID oluşturmanın çeşitli yolları vardır, ancak bunu PowerShell'de **[guid]::NewGuid() yazarak kolayca yapabilirsiniz**.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Hassas bir bilgi türünden, yol açıcı kanıt gereksinimini kaldırma

Artık Güvenlik Uyumluluk Merkezi'ne &amp; yük başka bir hassas bilgi türünüz olduğu için, bir sonraki adım kuralı daha özel hale yüklemektir. Kuralı, yalnızca denetim sayısı geçen ancak anahtar sözcükler gibi ek (parola ek) kanıt gerektirmeyen 16 basamaklı bir sayı olacak şekilde değiştirebilirsiniz. Bunu yapmak için, XML'ninroboratif kanıt olarak ihtiyacı olan kısmını kaldırmanız gerekir. Hatalı pozitif pozitif sonuç azaltmada, yol açıcı kanıt çok yararlıdır. Bu durumda, kredi kartı numarasının yanında çoğunlukla belirli anahtar sözcükler veya son kullanma tarihi vardır. Bu kanıtı kaldırırsanız, `confidenceLevel`kredi kartı numarasını (örnekte 85 olan ) indirerek ne kadar güven güvenerek bu olduğuna da karar velisiniz.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Belirli bir kuruluşa özel anahtar sözcükleri arama

Kanıt gerektiren ancak farklı veya ek anahtar sözcükler almak istiyor ve belki de bu kanıtın yerini değiştirmek istiyor da olabilir. 16 basamaklı `patternsProximity` sayı çevresinde düzeltici kanıt için pencereyi genişletecek veya daraltacak şekilde ayarlayabilirsiniz. Kendi anahtar sözcüklerinizi eklemek için, bir anahtar sözcük listesi tanımlamanız ve kuralınız içinde listeye göndermeniz gerekir. Aşağıdaki XML", "şirket kartı" ve "Contoso kartı" anahtar sözcüklerini ekler; böylelikle, kredi kartı numarasında 150 karakter içinde bu tümcecikleri içeren her ileti bir kredi kartı numarası olarak tanımlanır.

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>Upload kuralınızı seçin

Kuralınızı karşıya yüklemek için, aşağıdaki adımları gerçekleştirin.

1. Unicode kodlamayla .xml bir dosya olarak kaydedin. Dosya farklı bir kodlamayla kaydedilirse kural çalışmayy olduğundan, bu önemlidir.

2. [Bağlan ve Uyumluluk Merkezi'ne Uzak PowerShell aracılığıyla bağlanın.](/powershell/exchange/connect-to-scc-powershell)

3. PowerShell'de, aşağıdakini yazın.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Kural paketinizin gerçekte depolandığı dosya konumunu kullanmaya emin olun. `C:\custompath\` bir yer tutucudur.

4. Onaylamak için Y yazın ve Enter tuşuna **basın**.

5. Aşağıdakini yazarak yeni kuralınıza ve görünen adına yükleniyor olduğunu doğrulayın:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Hassas bilgileri algılamak üzere yeni kuralı kullanmaya başlamak için, kuralı bir DLP ilkesine eklemeniz gerekir. Kuralı bir ilkeye ekleme hakkında bilgi edinmek için bkz [. Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Terim sözlüğü

Bunlar, bu yordam sırasında karşılaştığınız terimlerin tanımlarıdır.

<br>

****

|Dönem|Tanım|
|---|---|
|Varlık|Varlıklar, kredi kartı numaraları gibi hassas bilgi türleri olarak çağrıllarımızdır. Her varlığın kimliği olarak benzersiz bir GUID'si vardır. GUID kopyalayıp XML'de arama yaptıysanız, XML kuralı tanımını ve bu XML kuralının tüm yerelleştirilmiş çevirilerini bulursanız. Bu tanımı, çevirinin GUID'sini bulup GUID için arayarak da bulabilirsiniz.|
|İşlevler|Derlenmiş kodda `Func_credit_card`bir işlev olan XML dosya başvuruları. İşlevler, karmaşık kayıt defterlerini çalıştırmak ve yerleşik kurallarımız için checksums'un eşleni olduğunu doğrulamak için kullanılır.) Kodda böyle bir durum ortaya olduğundan, değişkenlerden bazıları XML dosyasında görünmez.|
|IdMatch|Bu, desenin eşlemeye çalıştığı tanımlayıcıdır (örneğin, bir kredi kartı numarası).|
|Anahtar sözcük listeleri|XML dosyası ayrıca başvurular `keyword_cc_verification` ve `keyword_cc_name`, ilgili varlık içinde eşleşmeleri aramamız için anahtar sözcüklerin listesidir `patternsProximity` . Bunlar şu anda XML'de görüntülenmez.|
|Desen|Bu düzen, hassas türün ne istediğinin listesini içerir. Bu anahtar sözcükleri, kayıt defterlerini ve iç işlevleri içerir ve bunlar, denetim defterlerini doğrulama gibi görevleri yerine gösterir. Hassas bilgi türlerinin, benzersiz güven içeren birden çok düzeni olabilir. Bu, özer kanıt bulunursa yüksek güven verir ve çok az hata kanıtı bulunursa veya yoksa daha düşük bir güven verir.|
|Desen güveni Düzey|Bu, DLP altyapısının bir eşleşme bulduğu güven düzeyidir. Desenin gereksinimleri karşısa, bu güven düzeyi desene uygun bir eşleşmeyle ilişkilendirildi. Bu, posta akış kurallarını (aktarım kuralları olarak da bilinir) kullanırken Exchange bir güven ölçüsüdür.|
|patternsProximity|Kredi kartı numarası düzenine benzer olan bir model bulunca, `patternsProximity` bu sayına yakınlık içinde buroboratif kanıt bulabilirsiniz.|
|recommendedConfidence|Bu kural için öneririz güven düzeyidir. Önerilen güven, varlıklar ve benliklere uygulanır. Varlıklar için, bu sayı hiçbir zaman desene `confidenceLevel` göre değerlendirilmez. Yalnızca, uygulamak istediğiniz bir güven düzeyi seçmenize yardımcı olmak için bir öneridir. Affinities için, `confidenceLevel` bir `recommendedConfidence` posta akışı kuralı eyleminin çağrılacak sayıdan daha yüksek olması gerekir. Eylemi `recommendedConfidence` çağıran posta akışı kurallarında kullanılan varsayılan güven düzeyidir. Ekleyebilirsiniz, posta akışı kuralının bunun yerine desenin güven düzeyine göre çağırmayı el ile değiştirebilirsiniz.|
|

## <a name="for-more-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
