---
title: PowerShell kullanarak özel duyarlı bilgi türünü kaldırma
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
description: PowerShell kullanarak özel duyarlı bilgi türünü kaldırmayı öğrenin
ms.openlocfilehash: 852f9987b072f05dcf4f322f600bed23bcce7ef2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015498"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel duyarlı bilgi türünü kaldırma

Uyumluluk merkezi PowerShell'de, özel hassas bilgi türlerini kaldırmak için iki yöntem vardır:

- **Tek tek özel duyarlı bilgi türlerini kaldırma**: PowerShell kullanarak özel duyarlı [bilgi türünü değiştirme konusunda belgelenmiş yöntemi kullanın](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Özel duyarlı bilgi türü içeren özel kural paketini dışarı aktarın, hassas bilgi türünü XML dosyasından kaldırın ve güncelleştirilmiş XML dosyasını var olan özel kural paketine geri aktarın.

- **Özel bir kural paketini ve içerdiği tüm özel hassas bilgi türlerini kaldırın**: Bu yöntem bu bölümde belgelenmiştir.

> [!NOTE]
> Özel hassas bilgi türünü kaldırmadan önce, hiçbir DLP ilkelerinin veya posta akış kurallarının (aktarım kuralları olarak da Exchange) hassas bilgi türüne hala başvuramadan emin olun.

1. [Bağlan merkezi PowerShell'e](/powershell/exchange/exchange-online-powershell)

2. Özel bir kural paketini kaldırmak için [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) cmdlet'ini kullanın:

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Kural paketini tanımlamak için Ad değerini (herhangi bir dil `RulePack id` için) veya (GUID) değerini kullanabilirsiniz.

   Bu örnekte, "Çalışan Kimliği Özel Kural Paketi" adlı kural paketi kaldırabilirsiniz.

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Özel hassas bir bilgi türünü başarıyla kaldırıldığınızı doğrulamak için, aşağıdaki adımlardan herhangi birini yapın:

   - [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini çalıştırın ve kural paketinin artık liste olmadığını doğrulayın:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kaldırılan kural paketinde hassas bilgi türlerinin artık liste olmadığını doğrulamak için [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     Özel hassas bilgi türlerinde, Publisher değeri Microsoft Corporation'dan farklı bir değer olur.

   - Hassas \<Name\> bilgi türünün Ad değeriyle (örneğin, Çalışan Kimliği) değiştirin ve hassas bilgi türünün artık liste olmadığını doğrulamak için [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)
