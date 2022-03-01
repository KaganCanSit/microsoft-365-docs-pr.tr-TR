---
title: Anahtar sözcük sözlüğü değiştirme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Uyumluluk Merkezi'nde bir anahtar sözcük sözlüğünün Microsoft 365 öğrenin.
ms.openlocfilehash: acdf8b24aced21ed2f576fd57a3c685ef14debea
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010058"
---
# <a name="modify-a-keyword-dictionary"></a>Anahtar sözcük sözlüğü değiştirme

Anahtar sözcük sözlükleri arasında anahtar sözcükleri değiştirmeniz veya yerleşik sözlüklerden birini değiştirmeniz gerekir. Bunu PowerShell veya Uyumluluk Merkezi aracılığıyla da yapabiliriz.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Uyumluluk merkezinde anahtar sözcük sözlüğünü değiştirme

Anahtar sözcük sözlükleri hassas bilgi türü `Primary elements` `Supporting elements` (SIT) düzenleri olarak veya bu düzenlerde kullanılabilir. Bir sit veya mevcut bir SIT oluştururken anahtar sözcük sözlüğünü düzenleyebilirsiniz. Örneğin, var olan bir anahtar sözcük sözlüğünü düzenlemek için:

1. Güncelleştirmek istediğiniz anahtar sözcük sözlüğünün yer alan deseni açın.
2. Güncelleştirmek istediğiniz anahtar sözcük sözlüğünü bulun ve düzenle'yi seçin.
3. Satır başına tek bir anahtar sözcük kullanarak düzenlemelerinizi yapma.

   ![anahtar sözcükleri düzenle ekran görüntüsü.](../media/edit-keyword-dictionary.png)

4. 'yi seçin `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>PowerShell kullanarak anahtar sözcük sözlüğü değiştirme

Örneğin, PowerShell'de bazı terimleri değiştiririz, bu terimleri yerel olarak bir düzenleyicide değiştirerek yerel olarak kaydeder ve önceki terimleri yerinde güncelleştireriz.

İlk olarak, sözlük nesnesini alın:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Yazdırma `$dict` işlemi çeşitli özellikleri gösterir. Anahtar sözcüklerin kendileri arka uçta bir nesnede depolanır, `$dict.KeywordDictionary` ancak sözlükte değişiklik yapmak için kullanabileceğiniz dize temsilini içerir.

Sözlüğü değiştirmeden önce, yöntemi kullanarak terim dizesini yeniden diziye dönüştürebilirsiniz `.split(',')` . Ardından, yöntem ile anahtar sözcükler arasındaki istenmeyen boşlukları temizlenir `.trim()` ve yalnızca anahtar sözcüklerin birlikte çalışamaz halde bırakarak bu boşlukları temizleyebilirsiniz.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Şimdi, sözlükten bazı terimleri kaldıracaksiniz. Örnek sözlüğün yalnızca birkaç anahtar sözcüğü olduğundan, sözlüğü Not Defteri'te dışarı aktarmayı ve düzenlemeyi kolayca atlayabilirsiniz, ancak sözlükler genellikle büyük miktarda metin içerir; dolayısıyla ilk olarak bunları PowerShell'de kolayca düzenlemek için bu yolu öğrenirsiniz.

Son adımda, anahtar sözcükleri bir diziye kaydedtildiniz. Bir dizideki öğeleri kaldırmanın çeşitli yolları [vardır, ancak](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)) anlaşılır bir yaklaşım olarak, sözlükten kaldırmak istediğiniz terimlerin dizisini oluşturabilir ve sonra yalnızca sözlük terimlerini kaldırmak istediğiniz terimler listesinde olmayan bir dizi kopyalayıp kopyalayabilirsiniz.

Geçerli terimlerin `$terms` listesini göstermek için komutu çalıştırın. Komutun çıkışı şöyle görünüyor:

```powershell
aarskog's syndrome
abandonment
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablatio
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Kaldırmak istediğiniz terimleri belirtmek için bu komutu çalıştırın:

```powershell
$termsToRemove = @('abandonment','ablatio')
```

Terimleri listeden gerçekten kaldırmak için bu komutu çalıştırın:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Komutu çalıştırarak `$updatedTerms` güncelleştirilmiş terimlerin listesini gösterebilirsiniz. Komutun çıkışı şöyle görünüyor (belirtilen terimler kaldırıldı):

```powershell
aarskog's syndrome
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Şimdi sözlüğü yerel olarak kaydedin ve birkaç terim daha ekleyin. Terimleri burada PowerShell'e  eklersiniz, ancak Unicode kodlamayla kaydedildik ve TIR'i içerdiğiden emin olmak için dosyayı yerel olarak dışarı aktarmanız gerekir.

Aşağıdakini çalıştırarak sözlüğü yerel olarak kaydedin:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Şimdi dosyayı açın, diğer terimlerinizi ekleyin ve Unicode kodlamayla (UTF-16) kaydedin. Şimdi, güncelleştirilmiş terimleri karşıya yükp sözlüğü yerinde güncelleştirin.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Sözlük artık yerine güncelleştirildi. Alan `Identity` , sözlüğün adını alır. Ayrıca, `Set-` cmdlet'i kullanarak sözlüğün adını da değiştirmek istediysiniz, `-Name` yeni sözlük adınızla yukarıdakilere parametreyi eklemeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar sözcük sözlüğü oluşturma](create-a-keyword-dictionary.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
