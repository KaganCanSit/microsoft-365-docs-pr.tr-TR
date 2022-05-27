---
title: Anahtar sözcük sözlüğü oluşturma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Office 365 Güvenlik & Uyumluluk Merkezi'nde anahtar sözcük sözlüğü oluşturmanın temel adımlarını öğrenin.
ms.openlocfilehash: ceb410d09d9869d87681128f2c6e7b45cd8363cb
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753682"
---
# <a name="create-a-keyword-dictionary"></a>Anahtar sözcük sözlüğü oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Veri Kaybı Önleme (DLP), hassas öğelerinizi tanımlayabilir, izleyebilir ve koruyabilir. Hassas öğelerin tanımlanması bazen özellikle genel içeriği (sağlık hizmetleriyle ilgili iletişim gibi) veya uygunsuz veya açık dili tanımlarken anahtar sözcüklerin aranması gerekir. Hassas bilgi türlerinde anahtar sözcük listeleri oluşturabilirsiniz ancak anahtar sözcük listelerinin boyutu sınırlıdır ve bunları oluşturmak veya düzenlemek için XML'nin değiştirilmesi gerekir. Anahtar sözcük sözlükleri, sözlükte 1 MB'a kadar terimleri (sıkıştırma sonrası) destekleyen ve herhangi bir dili destekleyen anahtar sözcüklerin daha basit bir şekilde yönetilmesini ve çok daha büyük bir ölçekte yönetilmesini sağlar. Sıkıştırmadan sonra kiracı sınırı da 1 MB'tır. 1 MB sıkıştırma sonrası sınırı, kiracı genelinde birleştirilen tüm sözlüklerin 1 milyona yakın karaktere sahip olabileceği anlamına gelir.

## <a name="keyword-dictionary-limits"></a>Anahtar sözcük sözlüğü sınırları

Kiracı başına oluşturulabilecek 50 anahtar sözcük sözlüğü tabanlı hassas bilgi türü sınırı vardır. Kiracınızda kaç anahtar sözcük sözlükünüzün olduğunu öğrenmek için, [Bağlan güvenlik & Uyumluluk Merkezi PowerShell'e](/powershell/exchange/connect-to-scc-powershell) bağlanarak kiracınıza bağlanın ve bu PowerShell betiğini çalıştırın.

```powershell
$rawFile = $env:TEMP + "\rule.xml"

$kd = Get-DlpKeywordDictionary
$ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
[System.IO.File]::WriteAllBytes((Resolve-Path $rawFile), $ruleCollections.SerializedClassificationRuleCollection)
$UnicodeEncoding = New-Object System.Text.UnicodeEncoding
$FileContent = [System.IO.File]::ReadAllText((Resolve-Path $rawFile), $unicodeEncoding)

if($kd.Count -gt 0)
{
$count = 0
$entities = $FileContent -split "Entity id"
for($j=1;$j -lt $entities.Count;$j++)
{
for($i=0;$i -lt $kd.Count;$i++)
{
$Matches = Select-String -InputObject $entities[$j] -Pattern $kd[$i].Identity -AllMatches
$count = $Matches.Matches.Count + $count
if($Matches.Matches.Count -gt 0) {break}
}
}

Write-Output "Total Keyword Dictionary SIT:"
$count
}
else
{
$Matches = Select-String -InputObject $FileContent -Pattern $kd.Identity -AllMatches
Write-Output "Total Keyword Dictionary SIT:"
$Matches.Matches.Count
}

Remove-Item $rawFile
```

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>Anahtar sözcük sözlüğü oluşturmanın temel adımları

Sözlüğünüzün anahtar sözcükleri, en yaygın olarak hizmette veya PowerShell cmdlet'i tarafından içeri aktarılan bir dosyadan (.csv veya .txt listesi gibi), doğrudan PowerShell cmdlet'ine girdiğiniz bir listeden veya mevcut bir sözlükten gelen çeşitli kaynaklardan gelebilir. Anahtar sözcük sözlüğü oluşturduğunuzda aynı temel adımları izlersiniz:

1. *<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> kullanın veya **Microsoft Purview uyumluluk portalı PowerShell'e bağlanın**.

2. **Anahtar sözcüklerinizi hedeflenen kaynağınızdan tanımlayın veya yükleyin**. Sihirbaz ve cmdlet,özel anahtar sözcük sözlüğü oluşturmak için virgülle ayrılmış bir anahtar sözcük listesi kabul eder, bu nedenle bu adım anahtar sözcüklerinizin nereden geldiğine bağlı olarak biraz farklılık gösterir. Yüklendikten sonra, içeri aktarılmadan önce kodlanır ve bir bayt dizisine dönüştürülür.

3. **Sözlüğünüzü oluşturun**. Bir ad ve açıklama seçin ve sözlüğünüzü oluşturun.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'ni kullanarak anahtar sözcük sözlüğü oluşturma

Özel bir sözlük için anahtar sözcükler oluşturmak ve içeri aktarmak için aşağıdaki adımları kullanın:

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Bağlan</a>.

2. **Sınıflandırmalar > Hassas bilgi türleri'ne** gidin.

3. **Oluştur'u** seçin ve hassas bilgi türünüz için bir **Ad** ve **Açıklama** girin, ardından **İleri'yi** seçin

4. **Öğe ekle'yi** ve **ardından Açılan** **listeden Sözlük (Büyük anahtar sözcükler)** öğesini seçin.

5. **Sözlük ekle'yi** seçin

6. Arama denetimi altında **Burada yeni anahtar sözcük sözlükleri oluşturabilirsiniz'i** seçin.

7. Özel sözlüğünüz için bir **Ad** girin.

8. **İçeri Aktar'ı** seçin ve anahtar sözcük dosya türünüze bağlı olarak **Metinden** veya **Csv'den'i** seçin.

9. Dosya iletişim kutusunda yerel bilgisayarınızdan veya ağ dosya paylaşımınızdan anahtar sözcük dosyasını seçin ve ardından **Aç'ı** seçin.

10. **Kaydet'i** seçin ve anahtar **sözcük sözlükleri** listesinden özel sözlüğünüzü seçin.

11. **Ekle'yi** ve ardından **İleri'yi** seçin.

12. Hassas bilgi türü seçimlerinizi gözden geçirin ve sonlandırın, ardından **Son'u** seçin.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>PowerShell kullanarak bir dosyadan anahtar sözcük sözlüğü oluşturma

Genellikle büyük bir sözlük oluşturmanız gerektiğinde, bir dosyadan veya başka bir kaynaktan dışarı aktarılan bir listeden anahtar sözcükler kullanmaktır. Bu durumda, dış e-postada ekrana alınacak uygun olmayan dilin listesini içeren bir anahtar sözcük sözlüğü oluşturacaksınız. Öncelikle [Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell) gerekir.

1. Anahtar sözcükleri bir metin dosyasına kopyalayın ve her anahtar sözcüğün ayrı bir satırda olduğundan emin olun.

2. Metin dosyasını Unicode kodlama ile kaydedin. Not Defteri \> **Kodlama** \> **Unicode** **Olarak** \> Kaydet'te.

3. Şu cmdlet'i çalıştırarak dosyayı bir değişkene okuyun:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Bu cmdlet'i çalıştırarak sözlüğü oluşturun:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Özel hassas bilgi türlerinde ve DLP ilkelerinde anahtar sözcük sözlüklerini kullanma

Anahtar sözcük sözlükleri, özel bir hassas bilgi türü için eşleştirme gereksinimlerinin bir parçası olarak veya hassas bilgi türü olarak kullanılabilir. Her ikisi de [özel bir hassas bilgi türü](create-a-custom-sensitive-information-type-in-scc-powershell.md) oluşturmanızı gerektirir. Hassas bir bilgi türü oluşturmak için bağlantılı makaledeki yönergeleri izleyin. XML'yi aldıktan sonra, sözlüğün kullanabilmesi için GUID tanımlayıcısına ihtiyacınız olacaktır.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Sözlüğünüzün kimliğini almak için şu komutu çalıştırın ve **Identity** özellik değerini kopyalayın:

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Komutun çıkışı şöyle görünür:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Kimliği özel hassas bilgi türünüzün XML'ine yapıştırın ve karşıya yükleyin. Artık sözlüğünüz hassas bilgi türleri listenizde görünür ve bunu doğrudan ilkenizde kullanabilir ve kaç anahtar sözcüğün eşleşmesi gerektiğini belirtebilirsiniz.

```xml
<Entity id="d333c6c2-5f4c-4131-9433-db3ef72a89e8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f" />
      </Pattern>
    </Entity>
    <LocalizedStrings>
      <Resource idRef="d333c6c2-5f4c-4131-9433-db3ef72a89e8">
        <Name default="true" langcode="en-us">Diseases</Name>
        <Description default="true" langcode="en-us">Detects various diseases</Description>
      </Resource>
    </LocalizedStrings>
```

> [!NOTE]
> Microsoft 365 Information Protection için çift baytlık karakter kümesi dillerini destekler:
>
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türleri için kullanılabilir. Daha fazla bilgi için bkz. [Çift bayt karakter kümeleri için bilgi koruma desteği sürüm notları (önizleme).](mip-dbcs-relnotes.md)

> [!TIP]
> Çince/Japonca karakterler ve tek bayt karakterler içeren desenleri algılamak veya Çince/Japonca ve İngilizce içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki değişkenini tanımlayın.
>
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için anahtar sözcüğün iki değişkenini kullanın; Biri Japonca ve İngilizce metin arasında boşluk, diğeri ise Japonca ve İngilizce metin arasında boşluk olmadan. Bu nedenle, SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olmalıdır. Benzer şekilde, "東京オリンピック2020" ifadesini algılamak için iki değişken kullanılmalıdır; "東京オリンピック 2020" ve "東京オリンピック2020".
>
> Çince/Japonca/çift bayt karakterlerle birlikte, anahtar sözcükler/tümcecikler listesinde Çince/Japonca olmayan sözcükler de varsa (yalnızca İngilizce gibi), iki sözlük/anahtar sözcük listesi oluşturmanız önerilir. Biri Çince/Japonca/çift bayt karakter içeren anahtar sözcükler için, diğeri ise yalnızca İngilizce için.
>
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak istiyorsanız, iki anahtar sözcük listesi oluşturmanız gerekir.
>   1. Çok gizli
>   2. 機密性が高い, 机密的document ve 机密的 belgesi
>
> Çift bayt kısa çizgi veya çift bayt dönemi kullanarak bir regex oluştururken, bir kısa çizgi veya bir regex'teki nokta gibi karakterlerin her ikisine de kaçış yaptığınızdan emin olun. Başvuru için örnek bir regex aşağıda verilmiştir:
>
> - `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanmanızı öneririz.
