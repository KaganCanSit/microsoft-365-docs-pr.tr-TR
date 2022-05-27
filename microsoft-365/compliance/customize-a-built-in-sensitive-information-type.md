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
description: Kuruluşunuzun gereksinimlerini karşılayan kuralları kullanmanıza olanak sağlayacak özel bir hassas bilgi türü oluşturmayı öğrenin.
ms.openlocfilehash: f0ebc1bb4b13f9e31ca1a8a1967fce007105cfe6
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753902"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Yerleşik hassas bilgi türünü özelleştirme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

İçerikte hassas bilgiler ararken, bu bilgileri *kural* olarak adlandırılan bölümde açıklamanız gerekir. Microsoft Purview Veri Kaybı Önleme (DLP), hemen kullanabileceğiniz en yaygın hassas bilgi türleri için kurallar içerir. Bu kuralları kullanmak için bir ilkeye eklemeniz gerekir. Bu yerleşik kuralları kuruluşunuzun özel gereksinimlerini karşılayacak şekilde ayarlamak istediğinizi ve özel bir hassas bilgi türü oluşturarak bunu yapabileceğinizi fark edebilirsiniz. Bu konu başlığı altında, mevcut kural koleksiyonunu içeren XML dosyasının daha geniş bir yelpazedeki olası kredi kartı bilgilerini algılamak için nasıl özelleştirileceği gösterilmektedir.

Bu örneği alıp diğer yerleşik hassas bilgi türlerine uygulayabilirsiniz. Varsayılan hassas bilgi türlerinin ve XML tanımlarının listesi için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Geçerli kuralların XML dosyasını dışarı aktarma

XML'yi dışarı aktarmak [için Uzak PowerShell aracılığıyla Güvenlik ve Uyumluluk Merkezi'ne bağlanmanız gerekir.](/powershell/exchange/connect-to-scc-powershell).

1. PowerShell'de, kuruluşunuzun kurallarını ekranda görüntülemek için aşağıdakileri yazın. Kendi kurallarınızı oluşturmadıysanız yalnızca "Microsoft Kural Paketi" etiketli varsayılan yerleşik kuralları görürsünüz.

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Aşağıdakileri yazarak kuruluşunuzun kurallarını bir değişkende depolayın. Bir öğeyi bir değişkende depolamak, daha sonra uzak PowerShell komutları için çalışan bir biçimde kolayca kullanılabilir hale getirir.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Aşağıdakini yazarak tüm bu verilerle biçimlendirilmiş bir XML dosyası yapın.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Kural paketinizin gerçekten depolandığı dosya konumunu kullandığınızdan emin olun. `C:\custompath\` bir yer tutucudur.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>XML'de değiştirmek istediğiniz kuralı bulma

Yukarıdaki cmdlet'ler, sağladığımız varsayılan kuralları içeren *kural koleksiyonunun* tamamını dışarı aktardı. Ardından, özellikle değiştirmek istediğiniz Kredi Kartı Numarası kuralını aramanız gerekir.

1. Önceki bölümde dışarı aktardığınız XML dosyasını açmak için bir metin düzenleyicisi kullanın.

2. Aşağı kaydırarak `<Rules>` DLP kurallarını içeren bölümün başlangıcı olan etikete gelin. Bu XML dosyası kural koleksiyonunun tamamına ilişkin bilgileri içerdiğinden, en üstte kurallara ulaşmak için kaydırmanız gereken diğer bilgileri içerir.

3. Kredi Kartı Numarası kural tanımını bulmak için *Func_credit_card* arayın. XML'de kural adları boşluk içeremez, bu nedenle boşluklar genellikle alt çizgilerle değiştirilir ve kural adları bazen kısaltılır. Buna örnek olarak _SSN_ olarak kısaltılan ABD Sosyal Güvenlik numarası kuralı gösteriliyor. Kredi Kartı Numarası kuralı XML'i aşağıdaki kod örneğine benzer olmalıdır.

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

Artık XML'de Kredi Kartı Numarası kural tanımını konumlandırdığınıza göre, kuralın XML'sini gereksinimlerinizi karşılayacak şekilde özelleştirebilirsiniz. XML tanımlarıyla ilgili bir yenileyici için bu konunun sonundaki [Terim sözlüğüne](#term-glossary) bakın.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>XML'yi değiştirme ve yeni bir hassas bilgi türü oluşturma

İlk olarak, varsayılan kuralları doğrudan değiştiremediğiniz için yeni bir hassas bilgi türü oluşturmanız gerekir. [Güvenlik & Uyumluluk Merkezi PowerShell'de özel hassas bilgi türü oluşturma bölümünde özetlenen özel hassas bilgi türleriyle](create-a-custom-sensitive-information-type-in-scc-powershell.md) çok çeşitli işlemler yapabilirsiniz. Bu örnekte, bunu basit tutacağız ve yalnızca doğrulayıcı kanıtı kaldıracak ve Kredi Kartı Numarası kuralına anahtar sözcükler ekleyeceğiz.

Tüm XML kuralı tanımları aşağıdaki genel şablon üzerinde oluşturulur. Şablona Kredi Kartı Numarası tanımı XML'sini kopyalayıp yapıştırmanız, bazı değerleri değiştirmeniz gerekir (". . ." yer tutucularını seçin) ve ardından değiştirilen XML'yi ilkelerde kullanılabilecek yeni bir kural olarak karşıya yükleyin.

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

Şimdi, aşağıdaki XML'e benzer bir öğeniz var. Kural paketleri ve kuralları benzersiz GUID'leri tarafından tanımlandığından, biri kural paketi için, diğeri de Kredi Kartı Numarası kuralının GUID değerini değiştirmek için olmak üzere iki GUID oluşturmanız gerekir. Aşağıdaki kod örneğindeki varlık kimliğinin GUID değeri, yenisiyle değiştirmeniz gereken yerleşik kural tanımımızın GUID değeridir. GUID oluşturmanın çeşitli yolları vardır, ancak **bunu PowerShell'de [guid]::NewGuid()** yazarak kolayca yapabilirsiniz.

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

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Hassas bilgi türünden doğrulayıcı kanıt gereksinimini kaldırma

artık Microsoft Purview uyumluluk portalı karşıya yükleyebileceğiniz yeni bir hassas bilgi türünüz olduğuna göre, sonraki adım kuralı daha belirgin hale getirmektir. Kuralı, sağlama toplamını geçiren ancak anahtar sözcükler gibi ek (destekleyici) kanıt gerektirmeyen 16 basamaklı bir sayı arayabilecek şekilde değiştirin. Bunu yapmak için, XML'in doğrulayıcı kanıt arayabilen bölümünü kaldırmanız gerekir. Doğrulayıcı kanıt, hatalı pozitif sonuçların azaltılmasında çok yararlıdır. Bu durumda genellikle kredi kartı numarasının yanında belirli anahtar sözcükler veya son kullanma tarihi vardır. Bu kanıtı kaldırırsanız, örnekte 85 olan değerini düşürerek `confidenceLevel`bir kredi kartı numarası bulduğunuzdan ne kadar emin olduğunuzu da ayarlamanız gerekir.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Kuruluşunuza özgü anahtar sözcükleri arayın

Doğrulayıcı kanıt gerektirebilir, ancak farklı veya ek anahtar sözcükler isteyebilirsiniz ve belki de bu kanıtı nerede arayabileceğinizi değiştirmek isteyebilirsiniz. 16 basamaklı sayı etrafında doğrulayıcı kanıt için penceresini genişletecek veya küçültecek şekilde ayarlayabilirsiniz `patternsProximity` . Kendi anahtar sözcüklerinizi eklemek için bir anahtar sözcük listesi tanımlamanız ve kuralınız içinde buna başvurmanız gerekir. Aşağıdaki XML, kredi kartı numarasının 150 karakteri içinde bu tümcecikleri içeren tüm iletilerin kredi kartı numarası olarak tanımlanması için "şirket kartı" ve "Contoso kartı" anahtar sözcüklerini ekler.

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

## <a name="upload-your-rule"></a>Kuralınızı Upload

Kuralınızı karşıya yüklemek için aşağıdakileri yapmanız gerekir.

1. Unicode kodlamalı .xml dosyası olarak kaydedin. Dosya farklı bir kodlamayla kaydedilirse kural çalışmayacağından bu önemlidir.

2. [Uzak PowerShell aracılığıyla Güvenlik ve Uyumluluk Merkezi'ne Bağlan.](/powershell/exchange/connect-to-scc-powershell)

3. PowerShell'de aşağıdakileri yazın.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Kural paketinizin gerçekten depolandığı dosya konumunu kullandığınızdan emin olun. `C:\custompath\` bir yer tutucudur.

4. Onaylamak için Y yazın ve **Enter tuşuna** basın.

5. Yeni kuralınızın karşıya yüklendiğini ve görünen adını yazarak doğrulayın:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Hassas bilgileri algılamak için yeni kuralı kullanmaya başlamak için kuralı bir DLP ilkesine eklemeniz gerekir. Kuralı ilkeye eklemeyi öğrenmek için bkz. [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Terim sözlüğü

Bunlar, bu yordam sırasında karşılaştığınız terimlerin tanımlarıdır.

<br>

****

|Terim|Tanım|
|---|---|
|Varlık|Varlıklar, kredi kartı numaraları gibi hassas bilgi türleri olarak adlandırdığımız öğelerdir. Her varlığın kimliği benzersiz bir GUID'si vardır. BIR GUID'yi kopyalayıp XML'de ararsanız, XML kuralı tanımını ve bu XML kuralının tüm yerelleştirilmiş çevirilerini bulursunuz. Ayrıca, çevirinin GUID'sini bulup bu GUID'yi arayarak da bu tanımı bulabilirsiniz.|
|İşlevler|XML dosyası, derlenmiş koddaki bir işlev olan öğesine başvurur `Func_credit_card`. İşlevler karmaşık regex'leri çalıştırmak ve sağlama toplamlarının yerleşik kurallarımızla eşleşip eşleşmediğini doğrulamak için kullanılır.) Bu kodda gerçekleştiğinden, bazı değişkenler XML dosyasında görünmez.|
|IdMatch|Bu, desenin eşleşmeye çalıştığı tanımlayıcıdır(örneğin, bir kredi kartı numarası).|
|Anahtar sözcük listeleri|XML dosyası ayrıca, varlığın içinde `patternsProximity` eşleşmeleri `keyword_cc_verification` aradığımız anahtar sözcüklerin listesi olan ve `keyword_cc_name`öğesine başvurur. Bunlar şu anda XML'de görüntülenmez.|
|Desen|Desen, hassas türün aradığı şeyin listesini içerir. Bu anahtar sözcükler, regexes ve sağlama toplamlarını doğrulama gibi görevleri gerçekleştiren iç işlevleri içerir. Hassas bilgi türlerinin benzersiz güvenleri olan birden çok deseni olabilir. Bu, doğrulayıcı kanıt bulunursa yüksek güven döndüren hassas bir bilgi türü oluştururken ve çok az veya hiç doğrulayıcı kanıt bulunamazsa daha düşük bir güven oluştururken yararlıdır.|
|Desen güvenilirliğiLevel|Bu, DLP altyapısının bir eşleşme bulduğuna dair güven düzeyidir. Bu güvenilirlik düzeyi, desenin gereksinimleri karşılanırsa desenin eşleşmesiyle ilişkilendirilir. Bu, Exchange posta akışı kurallarını (taşıma kuralları olarak da bilinir) kullanırken dikkate almanız gereken güvenilirlik ölçüsüdür.|
|patternsProximity|Kredi kartı numarası deseni gibi görünen bir şey bulduğumuzda, `patternsProximity` doğrulayıcı kanıt arayacağımız numaranın etrafındaki yakınlıktır.|
|recommendedConfidence|Bu kural için önerdiğimiz güvenilirlik düzeyi budur. Önerilen güvenilirlik varlıklar ve benziteler için geçerlidir. Varlıklar için bu sayı hiçbir zaman desene göre `confidenceLevel` değerlendirilmez. Bu yalnızca, uygulamak istiyorsanız güvenilirlik düzeyi seçmenize yardımcı olacak bir öneridir. Benzimsizlikler için, `confidenceLevel` desenin sayısı, çağrılacak posta akışı kuralı eyleminin sayısından daha yüksek `recommendedConfidence` olmalıdır. `recommendedConfidence`, bir eylemi çağıran posta akışı kurallarında kullanılan varsayılan güvenilirlik düzeyidir. İsterseniz, desenin güvenilirlik düzeyine göre çağrılacak posta akışı kuralını el ile değiştirebilirsiniz.|
|

## <a name="for-more-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
