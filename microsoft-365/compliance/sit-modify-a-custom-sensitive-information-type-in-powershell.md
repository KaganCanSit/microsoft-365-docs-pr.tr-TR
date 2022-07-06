---
title: PowerShell kullanarak özel hassas bilgi türünü değiştirme
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
ms.openlocfilehash: 639a52526924d3068ce2d1cd38006a1773b6d098
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621985"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel hassas bilgi türünü değiştirme

Güvenlik & Uyumluluğu PowerShell'de, özel bir hassas bilgi türünü değiştirmek için şunlar gerekir:

1. Özel hassas bilgi türünü içeren mevcut kural paketini bir XML dosyasına aktarın (veya varsa mevcut XML dosyasını kullanın).

2. Dışarı aktarılan XML dosyasındaki özel hassas bilgi türünü değiştirin.

3. Güncelleştirilmiş XML dosyasını mevcut kural paketine geri aktarın.

Güvenlik & Uyumluluğu PowerShell'e bağlanmak için bkz [. Güvenlik & Uyumluluk PowerShell](/powershell/exchange/exchange-online-powershell).

## <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>1. Adım: Var olan kural paketini XML dosyasına aktarma

> [!NOTE]
> XML dosyasının bir kopyasına sahipseniz (örneğin, yeni oluşturup içeri aktardıysanız), XML dosyasını değiştirmek için sonraki adıma atlayabilirsiniz.

1. Henüz bilmiyorsanız, özel kural paketinin adını bulmak için [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Yerleşik hassas bilgi türlerini içeren yerleşik kural paketi Microsoft Kural Paketi olarak adlandırılır. Uyumluluk merkezi kullanıcı arabiriminde oluşturduğunuz özel hassas bilgi türlerini içeren kural paketi Microsoft.SCCManaged.CustomRulePack olarak adlandırılır.

2. Özel kural paketini bir değişkene [depolamak için Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Örneğin, kural paketinin adı "Çalışan Kimliği Özel Kural Paketi" ise aşağıdaki cmdlet'i çalıştırın:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Özel kural paketini xml dosyasına aktarmak için aşağıdaki söz dizimini kullanın:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   Bu örnek, kural paketini C:\Belgelerim klasöründeki ExportedRulePackage.xml adlı dosyaya aktarır.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

## <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>2. Adım: Dışarı aktarılan XML dosyasındaki hassas bilgi türünü değiştirme

XML dosyasındaki hassas bilgi türleri ve dosyadaki diğer öğeler bu konunun başlarında açıklanmıştır.

## <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>3. Adım: Güncelleştirilmiş XML dosyasını mevcut kural paketine geri aktarma

Güncelleştirilmiş XML'yi mevcut kural paketine geri aktarmak için [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Daha fazla bilgi

- [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Hassas bilgi türü işlevleri](sit-functions.md)
