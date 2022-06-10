---
title: Microsoft 365 grupları oluştururken kullanılacak etki alanını seçin
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: PowerShell kullanarak e-posta adresi ilkelerini yapılandırarak Microsoft 365 grupları oluştururken kullanılacak etki alanını seçmeyi öğrenin.
ms.openlocfilehash: c6eb1bbccf8745c88941f40d6fefeed29aec5620
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012548"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Microsoft 365 grupları oluştururken kullanılacak etki alanını seçin

Bazı kuruluşlar, işlerinin farklı bölümlerini birbirinden ayırmak için ayrı e-posta etki alanları kullanır. Kullanıcılarınız Microsoft 365 grupları oluştururken hangi etki alanının kullanılacağını belirtebilirsiniz.
  
Kuruluşunuzun, işletmenizin varsayılan kabul edilen etki alanı dışındaki etki alanlarında kendi gruplarını oluşturması gerekiyorsa, PowerShell kullanarak e-posta adresi ilkelerini (EAP) yapılandırarak buna izin vekleyebilirsiniz.

PowerShell cmdlet'lerini çalıştırmadan önce, kuruluşunuzla konuşmanıza olanak sağlayacak bir modülü indirin ve yükleyin. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell) göz atın.

## <a name="example-scenarios"></a>Örnek senaryolar

İşletmenizin ana etki alanının Contoso.com olduğunu düşünelim. Ancak kuruluşunuzun varsayılan kabul edilen etki alanı service.contoso.com. Bu, grupların service.contoso.com (örneğin, jimsteam@service.contoso.com) oluşturulacağı anlamına gelir.
  
Kuruluşunuzda da alt etki alanlarının yapılandırıldığını varsayalım. Grupların da bu etki alanlarında oluşturulmasını istiyorsunuz:
  
- Öğrenciler için students.contoso.com
    
- Öğretim üyeleri için faculty.contoso.com
    
Aşağıdaki iki senaryoda bunu nasıl başaracağınız açıklanmaktadır.

> [!NOTE]
> Mulitple EAP'leriniz olduğunda, bunlar öncelik sırasına göre değerlendirilir. 1 değeri en yüksek öncelik anlamına gelir. Bir EAP eşleştiğinde başka EAP değerlendirilmez ve gruba damgalanan adresler eşleşen EAP'ye göre olur. > Belirtilen ölçütle eşleşen EAP yoksa, grup kuruluşun varsayılan kabul edilen etki alanında sağlanır. Kabul edilen etki alanı ekleme hakkında ayrıntılı bilgi için [Exchange Online'de kabul edilen etki alanlarını yönetme](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) konusuna göz atın.
  
### <a name="scenario-1"></a>Senaryo 1

Aşağıdaki örnekte, kuruluşunuzdaki tüm Microsoft 365 gruplarının groups.contoso.com etki alanındaki sağlanması gösterilmektedir.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Senaryo 2

Grupların hangi alt etki alanlarında Microsoft 365 oluşturulduğunu denetlemek istediğinizi varsayalım. İstiyorsun:
  
- students.groups.contoso.com etki alanında öğrenciler ( **Bölümü** **Öğrenciler** olarak ayarlanmış kullanıcılar) tarafından oluşturulan gruplar. Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- faculty.groups.contoso.com etki alanında öğretim üyeleri tarafından oluşturulan gruplar ( **Bölümü** **Fakülte olarak ayarlanmış kullanıcılar veya e-posta adresi faculty.contoso.com içerir)**). Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Başkaları tarafından oluşturulan gruplar groups.contoso.com etki alanında oluşturulur. Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>E-posta adresi ilkelerini değiştirme

Mevcut bir EAP'nin öncelik veya e-posta adresi şablonlarını değiştirmek için Set-EmailAddressPolicy cmdlet'ini kullanın.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

EAP'nin değiştirilmesi, önceden sağlanmış olan grupları etkilemez.
  
## <a name="delete-email-address-policies"></a>E-posta adresi ilkelerini silme

EAP'yi silmek için Remove-EmailAddressPolicy cmdlet'ini kullanın.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

EAP'nin değiştirilmesi, önceden sağlanmış olan grupları etkilemez.
  
## <a name="hybrid-requirements"></a>Karma gereksinimler

Kuruluşunuz karma bir senaryoda yapılandırılmışsa, kuruluşunuzun Microsoft 365 grupları oluşturma gereksinimlerini karşıladığından emin olmak için [şirket içi Exchange karma ile](/exchange/hybrid-deployment/set-up-microsoft-365-groups) Microsoft 365 grupları yapılandırma konusuna bakın. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>E-posta adresi ilkeleri gruplarını kullanma hakkında ek bilgiler:

Bilmeniz gereken birkaç şey daha vardır:
  
- Grupların ne kadar hızlı oluşturulduğu, kuruluşunuzda yapılandırılan EAP sayısına bağlıdır.
    
- Yöneticiler ve kullanıcılar grup oluştururken etki alanlarını da değiştirebilir.
    
- Kullanıcı grubu, zaten kullanılabilir olan standart sorgular (Kullanıcı özellikleri) kullanılarak belirlenir. Desteklenen [filtrelenebilir özellikler için -RecipientFilter parametresinin Filtrelenebilir](/powershell/exchange/recipientfilter-properties) özellikleri'ne göz atın. 
    
- Gruplar için hiçbir EAP yapılandırmazsanız, grup oluşturma için varsayılan kabul edilen etki alanı seçilir.
    
- Kabul edilen bir etki alanını kaldırırsanız önce EAP'leri güncelleştirmeniz gerekir, aksi takdirde grup sağlama etkilenir.
    
- Bir kuruluş için en fazla 100 e-posta adresi ilkesi sınırı yapılandırılabilir.
    
## <a name="related-content"></a>İlgili içerik

[İşbirliği idaresi planlama önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (makale)

[İşbirliği idare planınızı oluşturma](collaboration-governance-first.md) (makale)

[Yönetim merkezinde Microsoft 365 grubu oluşturma](../admin/create-groups/create-groups.md) (makale)