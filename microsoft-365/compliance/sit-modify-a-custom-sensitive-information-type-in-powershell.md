---
title: PowerShell kullanarak özel duyarlı bilgi türünü değiştirme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: PowerShell kullanarak özel hassas bilgileri değiştirmeyi öğrenin.
ms.openlocfilehash: 2f1bc44dca9ec4a938c8cd3d4158163f9d5e2e2f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015474"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel duyarlı bilgi türünü değiştirme

Uyumluluk Merkezi PowerShell'de, özel hassas bilgi türünde değişiklik yapmak için şunları yapmak gerekir:

1. Özel duyarlı bilgi türünü içeren var olan kural paketini bir XML dosyasına aktarın (veya varsa varolan XML dosyasını kullanın).

2. Dışarı aktarıldı XML dosyasında özel duyarlı bilgi türünü değiştirme.

3. Güncelleştirilmiş XML dosyasını var olan kural paketine geri aktarın.

Uyumluluk Merkezi PowerShell'e bağlanmak için bkz[. Bağlan PowerShell Uyumluluk Merkezi'ne bağlanma](/powershell/exchange/exchange-online-powershell).

### <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>1. Adım: Var olan kural paketini BIR XML dosyasına dışarı aktarma

> [!NOTE]
> XML dosyasının bir kopyasına sahipsanız (örneğin, az önce oluşturdunız ve bunu dışarı aktardınız), XML dosyasını değiştirmek için sonraki adıma geçebilirsiniz.

1. Daha önce bilmiyorsanız, özel kural paketinin adını bulmak için [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Yerleşik hassas bilgi türlerini içeren yerleşik kural paketi Microsoft Kural Paketi olarak adlandırılmıştır. Uyumluluk merkezi kullanıcı arabiriminde oluşturduğunuz özel hassas bilgi türlerini içeren kural paketi Microsoft.SCCManaged.CustomRulePack olarak adlandırılmıştır.

2. Özel kural [paketini bir değişkende depolamak için Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Örneğin, kural paketinin adı "Çalışan Kimliği Özel Kural Paketi" ise, aşağıdaki cmdlet'i çalıştırın:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Özel kural paketini bir XML dosyasına dışarı aktaracak şekilde aşağıdaki söz dizimi kullanın:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   Bu örnekte, kural paketi C:\Belgelerim klasöründeki ExportedRulePackage.xml dosya olarak adlandırılmıştır.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

#### <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>2. Adım: Dışarı aktaran XML dosyasında hassas bilgi türünü değiştirme

XML dosyasındaki hassas bilgi türleri ve dosyanın diğer öğeleri bu konunun başlarında açıklanmıştır.

#### <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>3. Adım: Güncelleştirilmiş XML dosyasını var olan kural paketine geri aktarma

Güncelleştirilmiş XML'yi var olan kural paketine geri almak için [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Hassas bilgi türü işlevleri](sit-functions.md)
