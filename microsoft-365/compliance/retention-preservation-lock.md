---
title: Saklama ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma
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
description: Yasal düzenleme gereksinimlerini karşılamanıza ve dolandırıcı yöneticilere karşı korumanıza yardımcı olması için saklama ilkeleri ve bekletme etiketi ilkeleriyle Koruma Kilidi'ni kullanın.
ms.openlocfilehash: 228d4cd1a7778b5352df6d10d31b7e4c25af915f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016294"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Saklama ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> Şu anda [uyarlamalı ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) Koruma Kilidi'ni desteklememektedir.

Koruma Kilidi bir bekletme ilkesini veya bekletme etiketi ilkesini kilitler, böylece genel yönetici de dahil olmak üzere hiç kimse ilkeyi kapatabilir, ilkeyi silebilir veya daha az kısıtlayıcı hale getiremez. Bu yapılandırma yasal gereksinimler için gerekli olabilir ve düzenbaz yöneticilere karşı korunmaya yardımcı olabilir.

Bekletme ilkesi kilitlendiğinde:

- Hiç kimse ilkeyi devre dışı bırakamıyor veya silemiyor
- Konumlar eklenebilir ancak kaldırılamaz
- Saklama süresini uzatabilir ancak azaltmayabilirsiniz

Bekletme etiketi ilkesi kilitlendiğinde:

- Hiç kimse ilkeyi devre dışı bırakamıyor veya silemiyor
- Konumlar eklenebilir ancak kaldırılamaz
- Etiketler eklenebilir ancak kaldırılamaz

Özetle, kilitli bir ilke artırılabilir veya uzatılabilir, ancak azaltılamaz veya kapatılamaz.

> [!IMPORTANT]
> Bekletme ilkesini veya bekletme etiketi ilkesini kilitlemeden önce, etkiyi anlamanız ve kuruluşunuz için gerekli olup olmadığını onaylamanız kritik önem taşır. Örneğin, mevzuat gereksinimlerini karşılamak için gerekli olabilir. Koruma kilidi uygulandıktan sonra yöneticiler bu ilkeleri devre dışı bırakamaz veya silemez.

Bir [bekletme ilkesi](create-retention-policies.md) veya [yayımladığınız](create-apply-retention-labels.md) ve yalnızca [öğeleri düzenleyici kayıt olarak işaretleyen](records-management.md#records) etiketler içeren bir bekletme etiketi ilkesi oluşturduktan sonra Koruma Kilidi'ni yapılandırın.

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Bekletme ilkesini veya bekletme etiketi ilkesini kilitleme

Koruma Kilidi kullanmanız gerekiyorsa PowerShell'i kullanmanız gerekir. Yöneticiler bu kilit uygulandıktan sonra bekletme için bir ilkeyi devre dışı bırakamadığından veya silemediğinden, yanlışlıkla yapılandırmaya karşı koruma sağlamak için bu özelliği etkinleştirmek kullanıcı arabiriminde kullanılamaz.

Herhangi bir yapılandırmaya sahip tüm bekletme ilkeleri Koruma Kilidi'ne sahiptir. Saklama etiketi ilkesine Koruma Kilidi uygulamak için yalnızca öğeleri düzenleyici kayıt olarak işaretleyen etiketler içermelidir.

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) komutunu çalıştırarak kilitlemek istediğiniz ilkenin adını bulun. Örneğin:
    
   ![PowerShell'deki bekletme ilkelerinin listesi.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. İlkenize Bir Koruma Kilidi yerleştirmek için, ilkenin adıyla [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) cmdlet'ini ve *RestrictiveRetention* parametresini true olarak ayarlayın:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    ```
    
    Örneğin:
    
    ![PowerShell'de RestrictiveRetention parametresi.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     İstendiğinde, **Y** girerek bu yapılandırmayla birlikte gelen kısıtlamaları okuyun ve kabul edin:
    
   ![PowerShell'de bekletme ilkesini kilitlemek istediğinizi onaylama istemi.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Artık ilkeye bir Koruma Kilidi yerleştirilir. Onaylamak için yeniden çalıştırın `Get-RetentionCompliancePolicy` , ancak ilke adını belirtin ve ilke parametrelerini görüntüleyin:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

**RestrictiveRetention** değerinin **True** olarak ayarlandığını görmeniz gerekir. Örneğin:

![PowerShell'de gösterilen tüm parametrelerle kilitlenmiş ilke.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Ayrıca bkz.

[Veri yaşam döngüsü yönetimi ve kayıt yönetimi için mevzuat gereksinimlerini karşılamanıza yardımcı olacak kaynaklar](retention-regulatory-requirements.md)
