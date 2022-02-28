---
title: Bekletme ilkelerine ve bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Saklama Kilidi'i kullanma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Yasal düzenleme gereksinimlerini karşılamanıza ve yönetici yöneticilerini korumanıza yardımcı olmak için Bekletme ilkeleri ve bekletme etiketi ilkeleriyle Yasal Koruma Kilidi'ne başvurun.
ms.openlocfilehash: 64c2bb8f2718ce0da9d638b5b8b6bd4f89d33668
ms.sourcegitcommit: f6fff04431d632db02e7bdbf12f691091a30efad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "62988819"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Bekletme ilkelerine ve bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Saklama Kilidi'i kullanma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!IMPORTANT]
> Şu anda, [uyarlanabilir ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) Koruma Kilidi'i desteklemez.

Koruma Kilidi, kimsenin (genel yönetici dahil) ilkeyi kapatmasını, silemez veya daha az kısıtlayıcı hale döndüreni bir bekletme ilkesi veya bekletme etiketi ilkesi kilitler. Bu yapılandırma yasal düzenleme gereksinimleri için gerekli olabilir ve yöneticilerini korumaya yardımcı olabilir.

Bekletme ilkesi kilitlenirken:

- Hiç kimse ilkeyi devre dışı bırakama veya silemez
- Konumlar eklenebilir, ancak kaldırılamaz
- Bekletme süresini uzatabiliyor, ancak azaltamayabiliyor

Bekletme etiketi ilkesi kilitlenirken:

- Hiç kimse ilkeyi devre dışı bırakama veya silemez
- Konumlar eklenebilir, ancak kaldırılamaz
- Etiketler eklenebilir, ancak kaldırılamaz

Özet olarak, kilitli bir ilke artırılabilir veya uzatılabilir ancak indirilemez veya kapatılabilir.

> [!IMPORTANT]
> Bir bekletme ilkesi veya bekletme etiketi ilkesi kilitlemeden önce, etkisini anlamanız ve bunun organizasyonunız için gerekli olup olmadığını onaylamanız çok önemlidir. Örneğin, mevzuat gereksinimlerini karşılamak için bu gerekli olabilir. Koruma kilidi uygulandıktan sonra yöneticiler bu ilkeleri devre dışı bırakamaz veya silemez.

Bir bekletme ilkesi veya yayımlayan [veya otomatik olarak](create-retention-policies.md) uygulayan bir bekletme etiketi ilkesi [oluşturduktan sonra Koruma](create-apply-retention-labels.md) [Kilidi'yi yapılandırın](apply-retention-labels-automatically.md).

> [!NOTE]
> Etiket ilkesi kilitlemek yöneticinin kilitli ilkeye dahil olan bir etikette bekletme süresini azaltmasını engellemez. Bu gereksinim, diğer kısıtlamalarla birlikte, bir etiketi öğeleri mevzuat kaydı olarak işaretlemek üzere yapılandırıldığında [karşı kullanılabilir](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Bekletme ilkesi veya bekletme etiketi ilkesi nasıl kilitlenebilir?

Koruma Kilidi'ne ihtiyacınız varsa PowerShell kullanabilirsiniz. Yöneticiler bu kilit uygulandıktan sonra bekletme için bir ilkeyi devre dışı bırakama veya silemezler, çünkü kullanıcı arabiriminde bu özelliği etkinleştirme özelliği yanlışlıkla yapılan yapılandırmalara karşı korumak için kullanılamaz.

Bekletmeye ve tüm yapılandırma desteği olan Saklama Kilidi ilkelerine yönelik tüm ilkeler.

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. [Get-RetentionCompliancePolicy'i çalıştırarak kilitlemek istediğiniz ilkenin adını bulun](/powershell/module/exchange/get-retentioncompliancepolicy). Örneğin:
    
   ![PowerShell'de bekletme ilkelerinin listesi.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. İlkenize bir Koruma Kilidi ayarlamak için [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) cmdlet'ini ilkenin adıyla ve *RestrictiveRetention* parametresi true olarak ayarlanmış durumda çalıştırın:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" –RestrictiveRetention $true
    ```
    
    Örneğin:
    
    ![PowerShell'de RestrictiveRetention parametresi.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     İstendiğinde, Y girerek bu yapılandırmayla birlikte gelen kısıtlamaları okuyun ve kabul **edin**:
    
   ![PowerShell'de bekletme ilkesi kilitlemek istediğiniz onay istemi.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Artık koruma kilidi ilkeye yerleştirilmiştir. Onaylamak için yeniden `Get-RetentionCompliancePolicy` çalıştırın, ancak ilke adını belirtin ve ilke parametrelerini görüntüleme:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

**RestrictiveRetention true olarak** **ayarlanmıştır**. Örneğin:

![PowerShell'de gösterilen tüm parametrelerin kullanıldığı kilitli ilkesi.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Ayrıca bkz.

[Bilgi yönetimi ve kayıt yönetimiyle ilgili mevzuat gereksinimlerini karşılamanıza yardımcı olacak kaynaklar](retention-regulatory-requirements.md)