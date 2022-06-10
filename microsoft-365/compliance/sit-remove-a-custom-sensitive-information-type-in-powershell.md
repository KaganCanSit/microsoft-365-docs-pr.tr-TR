---
title: PowerShell kullanarak özel hassas bilgi türünü kaldırma
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
description: PowerShell kullanarak özel hassas bilgi türünü kaldırmayı öğrenin
ms.openlocfilehash: e935c9340c353561e71e25fdadfec5509da041e5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014750"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel hassas bilgi türünü kaldırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Güvenlik & Uyumluluğu PowerShell'de, özel hassas bilgi türlerini kaldırmak için iki yöntem vardır:

- **Tek tek özel hassas bilgi türlerini kaldırma**: [PowerShell kullanarak özel hassas bilgi türünü değiştirme](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell) bölümünde belgelenen yöntemi kullanın. Özel hassas bilgi türünü içeren özel kural paketini dışarı aktarır, hassas bilgi türünü XML dosyasından kaldırır ve güncelleştirilmiş XML dosyasını mevcut özel kural paketine geri aktarırsınız.

- **Özel kural paketini ve içerdiği tüm özel hassas bilgi türlerini kaldırın**: Bu yöntem bu bölümde belgelenmiştir.

> [!NOTE]
> Özel bir hassas bilgi türünü kaldırmadan önce, DLP ilkelerinin veya Exchange posta akışı kurallarının (aktarım kuralları olarak da bilinir) hassas bilgi türüne başvurmadığını doğrulayın.

1. [Güvenlik & Uyumluluğu PowerShell](/powershell/exchange/exchange-online-powershell)

2. Özel kural paketini kaldırmak için [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Kural paketini tanımlamak için Ad değerini (herhangi bir dil için) veya `RulePack id` (GUID) değerini kullanabilirsiniz.

   Bu örnek, "Çalışan Kimliği Özel Kural Paketi" adlı kural paketini kaldırır.

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Özel bir hassas bilgi türünü başarıyla kaldırdığınızdan emin olmak için aşağıdaki adımlardan herhangi birini yapın:

   - [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini çalıştırın ve kural paketinin artık listelenmediğinden emin olun:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kaldırılan kural paketindeki hassas bilgi türlerinin artık listelenmediğinden emin olmak için [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     Özel hassas bilgi türleri için Publisher özellik değeri Microsoft Corporation dışında bir değer olacaktır.

   - değerini hassas bilgi türünün (örneğin, Çalışan Kimliği) Ad değeriyle değiştirin \<Name\> ve hassas bilgi türünün artık listelenmediğinden emin olmak için [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Daha fazla bilgi

- [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)
