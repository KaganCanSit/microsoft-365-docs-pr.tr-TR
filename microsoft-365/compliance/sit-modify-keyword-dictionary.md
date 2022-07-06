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
description: Microsoft Purview uyumluluk portalı anahtar sözcük sözlüğünde değişiklik yapmayı öğrenin.
ms.openlocfilehash: 8b2f2256be506f0ba01dc059bf0ac54e84c481c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621721"
---
# <a name="modify-a-keyword-dictionary"></a>Anahtar sözcük sözlüğü değiştirme

Anahtar sözcük sözlüklerinizden birinde anahtar sözcükleri değiştirmeniz veya yerleşik sözlüklerden birini değiştirmeniz gerekebilir. Bunu PowerShell veya Uyumluluk merkezi aracılığıyla yapabilirsiniz.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Uyumluluk merkezinde anahtar sözcük sözlüğünü değiştirme

Anahtar sözcük sözlükleri hassas bilgi türü (SIT) desenleri olarak `Primary elements` veya `Supporting elements` olarak kullanılabilir. Sit oluştururken veya var olan bir SIT'te anahtar sözcük sözlüğü düzenleyebilirsiniz. Örneğin, mevcut bir anahtar sözcük sözlüğü düzenlemek için:

1. Güncelleştirmek istediğiniz anahtar sözcük sözlüğüne sahip deseni açın.
2. Güncelleştirmek istediğiniz anahtar sözcük sözlüğünü bulun ve düzenle'yi seçin.
3. Satır başına bir anahtar sözcük kullanarak düzenlemelerinizi yapın.

   ![anahtar sözcükleri düzenleme ekran görüntüsü.](../media/edit-keyword-dictionary.png)

4. öğesini seçin `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>PowerShell kullanarak anahtar sözcük sözlüğü değiştirme

Örneğin, PowerShell'de bazı terimleri değiştirecek, düzenleyicide değiştirebileceğiniz terimleri yerel olarak kaydedip önceki terimleri güncelleştireceğiz.

İlk olarak sözlük nesnesini alın:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Yazdırma `$dict` işlemi çeşitli özellikleri gösterir. Anahtar sözcüklerin kendileri arka uçtaki bir nesnede depolanır, ancak `$dict.KeywordDictionary` sözlüğünü değiştirmek için kullanacağınız dize gösterimini içerir.

Sözlüğü değiştirmeden önce, yöntemini kullanarak terim dizesini bir diziye `.split(',')` geri döndürmeniz gerekir. Ardından yöntemiyle `.trim()` anahtar sözcükler arasındaki istenmeyen boşlukları temizler ve yalnızca çalışabileceğiniz anahtar sözcükleri bırakırsınız.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Şimdi sözlükten bazı terimleri kaldıracaksınız. Örnek sözlüğün yalnızca birkaç anahtar sözcüğü olduğundan, sözlüğü dışarı aktarmaya ve Not Defteri'nde düzenlemeye kolayca atlayabilirsiniz, ancak sözlükler genellikle büyük miktarda metin içerdiğinden, önce PowerShell'de bunları kolayca düzenlemeyi bu şekilde öğreneceksiniz.

Son adımda anahtar sözcükleri bir diziye kaydettiniz. [Bir diziden öğeleri kaldırmanın](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)) çeşitli yolları vardır, ancak basit bir yaklaşım olarak, sözlükten kaldırmak istediğiniz terimlerin bir dizisini oluşturacak ve kaldırılacak terimler listesinde yer almayan terimleri ona kopyalayacaksınız.

Geçerli terim listesini göstermek için komutunu `$terms` çalıştırın. Komutun çıkışı şöyle görünür:

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

Kaldırmak istediğiniz terimleri belirtmek için şu komutu çalıştırın:

```powershell
$termsToRemove = @('abandonment','ablatio')
```

Listeden terimleri kaldırmak için şu komutu çalıştırın:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Güncelleştirilmiş terim listesini göstermek için komutunu `$updatedTerms` çalıştırın. Komutun çıkışı şöyle görünür (belirtilen terimler kaldırılmıştır):

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

Şimdi sözlüğü yerel olarak kaydedin ve birkaç terim daha ekleyin. Terimleri doğrudan PowerShell'de buraya ekleyebilirsiniz, ancak dosyanın Unicode kodlaması ile kaydedildiğinden ve ürün reçetesini içerdiğinden emin olmak için dosyayı yerel olarak dışarı aktarmanız gerekir.

Aşağıdakileri çalıştırarak sözlüğü yerel olarak kaydedin:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Şimdi dosyayı açın, diğer terimlerinizi ekleyin ve Unicode kodlama (UTF-16) ile kaydedin. Şimdi güncelleştirilmiş terimleri karşıya yükleyecek ve sözlüğü yerinde güncelleştireceksiniz.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Şimdi sözlük yerinde güncelleştirildi. alanı `Identity` sözlüğün adını alır. Cmdlet'ini kullanarak `Set-` sözlüğünüzün adını da değiştirmek isterseniz, yeni sözlük adınızla yukarıdakine parametresini eklemeniz `-Name` yeterli olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar sözcük sözlüğü oluşturma](create-a-keyword-dictionary.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
