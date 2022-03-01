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
description: Güvenlik ve Uyumluluk Merkezi'nde anahtar sözcük sözlüğü Office 365 temel & öğrenin.
ms.openlocfilehash: ca88c57739c8734f9fcdb5d3356a44dc6a72faa5
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010057"
---
# <a name="create-a-keyword-dictionary"></a>Anahtar sözcük sözlüğü oluşturma

Veri kaybı önleme (DLP), hassas öğelerinizi tanımlayabilir, izleyebilir ve koruyabilir. Hassas öğeleri belirlemek bazen, özellikle de genel içeriği (sağlıkla ilgili iletişim gibi) veya uygunsuz veya açık bir dilin belirlenmesi için anahtar sözcükler aramanız gerekir. Hassas bilgi türlerinde anahtar sözcük listeleri oluşturabileceksiniz, ancak anahtar sözcük listelerinin boyutu sınırlıdır ve bunları oluşturmak veya düzenlemek için XML'de değişiklik yapmak gerekir. Anahtar sözcük sözlükleri anahtar sözcüklerin daha kolay yönetimini ve çok daha büyük bir ölçekte, sözlükte 1 MB'ye kadar terimleri (sıkıştırma sonrası) destekler ve her dili destekler. Sıkıştırma sonrasında kiracı sınırı da 1 MB olur. 1 MB'lık sıkıştırma sonrası sınırı, kiracı genelindeki tüm sözlüklerin 1 milyon karaktere yakın olması anlamına gelir.

## <a name="keyword-dictionary-limits"></a>Anahtar sözcük sözlüğü sınırları

Kiracı başına oluşturulacak en fazla 50 anahtar sözcükli sözlük tabanlı hassas bilgi türü vardır. Kiracınıza kaç anahtar sözcük sözlüğünün olduğunu bulmak için, Bağlan'daki yordamları kullanarak kiracınıza bağlanmak ve bu PowerShell betiğini çalıştırmak için Güvenlik & Uyumluluk Merkezi [PowerShell'e](/powershell/exchange/connect-to-scc-powershell) bağlanın.

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

Sözlüğü ekleyebilirsiniz anahtar sözcükler, en yaygın olarak hizmette veya PowerShell cmdlet'i tarafından içeri aktarılan bir dosyadan (.csv veya .txt listesi gibi), doğrudan PowerShell cmdlet'ine veya var olan bir sözlükten gelen çeşitli kaynaklardan gelebilir. Anahtar sözcük sözlüğü ekleyebilirsiniz, aynı temel adımları izleyin:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">*Uyumluluk</a> Microsoft 365 uyumluluk merkezi'i kullanın veya **PowerShell Güvenlik &amp; Uyumluluk Merkezi'ne bağlanın**.

2. **Anahtar sözcüklerinizi hedeflene kaynağından tanımlayın veya yüklenin**. Sihirbaz ve cmdlet, özel bir anahtar sözcük sözlüğü oluşturmak için virgülle ayrılmış bir anahtar sözcük listesini kabul eder; dolayısıyla bu adım, anahtar sözcüklerinizin geldiği yere bağlı olarak biraz değişiklik gösterir. Bunlar aktarıldıktan sonra kodlanmış ve bir byte dizisine dönüştürülürler.

3. **Sözlüğü oluşturun**. Bir ad ve açıklama seçin ve sözlüğü oluşturun.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde anahtar sözcük & oluşturma

Özel sözlükte anahtar sözcükleri oluşturmak ve içeri aktarma için aşağıdaki adımları kullanın:

1. Bağlan'e <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>.

2. Sınıflandırmalar **ve Hassas > türleri'ne gidin**.

3. **Oluştur'a** tıklayın ve hassas **bilgi türünüz** **için** Ad ve Açıklama girin, sonra da Sonraki'yi **seçin**

4. Öğe **ekle'yi seçin**, sonra **da açılan listede** İçeriği algıla listesinde **Sözlük (Büyük anahtar sözcükler** ) öğesini seçin.

5. Sözlük **ekle'yi seçin**

6. Arama denetimi altında, Burada **yeni anahtar sözcük sözlükleri oluşturabilirsiniz öğesini seçin**.

7. Özel **sözlüğüniz** için Ad girin.

8. İçeri **Aktar'ı** seçin ve anahtar **sözcük dosya** **türünüze bağlı** olarak Metinden'i veya Csv'den'i seçin.

9. Dosya iletişim kutusunda yerel bilgisayarınızdan veya ağ dosya paylaşımından anahtar sözcük dosyasını seçin ve sonra da Aç'ı **seçin**.

10. **Kaydet'i** seçin ve sonra Anahtar sözcük sözlükleri **listesinden özel sözlüğünü** seçin.

11. **Ekle'yi** ve ardından Sonraki'yi **seçin**.

12. Hassas bilgi türü seçimlerinizi gözden geçirip son olarak bitirin ve ardından Son'a **tıklayın**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>PowerShell kullanarak bir dosyadan anahtar sözcük sözlüğü oluşturma

Büyük bir sözlük oluşturmanız gereken durumlarda, çoğunlukla bir dosyadan veya başka bir kaynaktan dışarı aktarıldı bir listeden anahtar sözcükler kullanmaktır. Bu durumda, dış e-postada ekrana gelen uygunsuz dilin listesini içeren bir anahtar sözcük sözlüğü oluşturabilirsiniz. İlk olarak Güvenlik [Bağlan Uyumluluk Merkezi PowerShell& e gerek vardır](/powershell/exchange/connect-to-scc-powershell).

1. Anahtar sözcükleri bir metin dosyasına kopyalayın ve her anahtar sözcüğün ayrı bir satırda olduğundan emin olun.

2. Metin dosyasını Unicode kodlamayla kaydedin. Farklı Not Defteri \> **Kodlama Unicode'u** \>  \> **kaydedin**.

3. Bu cmdlet'i çalıştırarak dosyayı değişken olarak okuyun:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Şu cmdlet'i çalıştırarak sözlüğü oluşturun:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Özel hassas bilgi türlerinde ve DLP ilkelerinde anahtar sözcük sözlüklerini kullanma

Anahtar sözcük sözlükleri, özel hassas bilgi türünün eşleşme gereksinimlerinin bir parçası olarak veya hassas bir bilgi türünün kendileri olarak kullanılabilir. Her ikisi için de özel bir [hassas bilgi türü oluşturmanız gerekir](create-a-custom-sensitive-information-type-in-scc-powershell.md). Hassas bir bilgi türü oluşturmak için bağlantılı makaledeki yönergeleri izleyin. XML'iniz olduktan sonra, sözlüğün bunu kullanabileceği GUID tanımlayıcısı gerekir.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Sözlüğün kimliğini almak için, bu komutu çalıştırın ve **Identity özellik değerini** kopyalayın:

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Komutun çıkışı şöyle görünüyor:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Kimliği özel hassas bilgi türü xml'nize yapıştırın ve karşıya yükleyin. Artık sözlüğüz hassas bilgi türleri listesinde görünür ve kaç anahtar sözcüğün eşleşmesi için gerekli olduğunu belirterek bunu ilkenize göre hemen kullanabilirsiniz.

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
> Microsoft 365 Koruması aşağıdakiler için çift byte karakter kümesi dillerini destekler:
>
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türlerinde kullanılabilir. Daha fazla [bilgi için çift byte karakter kümesi sürüm notları (önizleme) için Bilgi koruma](mip-dbcs-relnotes.md) desteği'ne bakın.

> [!TIP]
> Çince/Japonca karakterler ve tek bir byte karakteri içeren desenleri algılamak veya Çince/Japonca ve İngilizce dillerini içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki çeşitleni tanımlayın.
>
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için, anahtar sözcüğün iki çeşitleni kullanın; Japonca ve İngilizce metin arasında boşluk olmayan ve Japonca ve İngilizce metinler arasında boşluk olmayan bir metin. Dolayısıyla SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olabilir. Benzer şekilde, "東京オリンピック2020" tümceciği algılamak için iki değişken kullanılmalıdır: "東京オリンピック 2020" ve "東京オリンピック2020".
>
> Anahtar sözcükler/tümcecikler listesi Çince/Japonca sözcükler de (yalnızca İngilizce gibi) içeriyorsa, Çince/Japonca/çift byte karakterleriyle birlikte, iki sözlük/anahtar sözcük listesi oluşturmanız önerilir. Çince/Japonca/çift byte karakter içeren anahtar sözcükler için bir tane ve yalnızca İngilizce için bir tane daha.
>
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak için iki anahtar sözcük listesi oluşturmanız gerekir.
>     1. Çok gizli
>     2. 機密性が高い, 机密的document ve 机密的 belgesi
>
> Çift bayt kısa çizgi veya çift byte dönemi kullanarak bir kayıtex oluşturulurken, bir kayıtex içinde bir kısa çizgi veya nokta gibi iki karakterin de kaçışta olduğundan emin olun. Başvuru için örnek bir kayıtex:
>
> - `(?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}`
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanılması önerilir.
