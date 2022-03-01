---
title: Grup oluştururken kullanmak istediğiniz etki Microsoft 365 seçin
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
description: PowerShell kullanarak e-posta adresi ilkelerini yapılandırarak Microsoft 365 grupları oluştururken kullanmak istediğiniz etki alanını seçmeyi öğrenin.
ms.openlocfilehash: 31b84304643190f343ae9ee74a947ecf6741f135
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005019"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Grup oluştururken kullanmak istediğiniz etki Microsoft 365 seçin

Bazı kuruluşlar, işlerinin farklı bölümlerini birbirinden ayırmak için ayrı e-posta etki alanları kullanır. Kullanıcılarınızı yeni gruplar oluşturmak için hangi etki alanının Microsoft 365 belirtebilirsiniz.
  
Kuruluşta kullanıcıların, işletmenizin varsayılan kabul edilen etki alanı dışında etki alanlarında grup oluşturmaları gerekiyorsa, PowerShell kullanarak e-posta adresi ilkeleri (EAP) yapılandırarak buna izin veebilirsiniz.

PowerShell cmdlet'lerini çalıştırmadan önce, organizasyonla konuşmanıza izin verecek bir modül indirin ve yükleyin. Uzak [PowerShell Bağlan Exchange Online göz atabilirsiniz](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Örnek senaryolar

İşletmenizin ana etki alanının önemli olduğunu Contoso.com. Ancak, kuruluşun varsayılan kabul edilen etki alanı service.contoso.com. Bu, grupların kendi gruplarında (service.contoso.com, grup) oluşturulacakları jimsteam@service.contoso.com.
  
Ayrıca, kurum içinde yapılandırılmış alt etki alanlarınız olduğunu da var diyelim. Grupların şu etki alanlarında da oluşturulsun:
  
- students.contoso.com için karne
    
- faculty.contoso.com üyeleri için son bilgiler
    
Aşağıdaki iki senaryoda bunu nasıl gerçekleştirersiniz?

> [!NOTE]
> Çok fazla EAP'niz olduğunda, bunlar öncelik sırasına göre değerlendirilir. 1 değeri en yüksek öncelik anlamına gelir. EAP eşleşmesi yapıldıktan sonra, artık EAP değerlendirilmez ve grupta damga damgalı adresler eşleşen EAP'ya göre olur. > ESA'lar belirtilen ölçütlere uyan bir ESA'yoksa, grup kuruluşun varsayılan kabul edilen etki alanında hazır olur. Kabul edilen [etki alanı ekleme ayrıntıları için Exchange Online'de](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) kabul edilen etki alanlarını yönetme.
  
### <a name="scenario-1"></a>Senaryo 1

Aşağıdaki örnek, aynı etki alanında Microsoft 365 grupların tüm kullanıcı gruplarının nasıl groups.contoso.com gösterir.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Senaryo 2

Hangi alt etki alanlarının ve grupların Microsoft 365 kontrol etmek istediğinize izin verirsiniz. İstiyorsun:
  
- Aynı etki alanında Öğrenciler tarafından oluşturulan gruplar ( **Bölümü** Öğrenciler olarak **ayarlanmış** kullanıcılar students.groups.contoso.com. Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Fakülte üyeleri tarafından oluşturulan gruplar (Bölüm veya e-posta adresi Fakülte veya **e-posta adresine** ayarlanmış olan kullanıcılar faculty.contoso.com)) faculty.groups.contoso.com içerir. Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Başka herhangi biri tarafından oluşturulan gruplar groups.contoso.com oluşturulur. Şu komutu kullanın:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>E-posta adresi ilkelerini değiştirme

Var olan bir EAP'nın öncelik veya e-posta adresi şablonlarını değiştirmek için Set-EmailAddressPolicy kullanın.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

EAP'nin değiştirilmesi, önceden sağmış olan grupların üzerinde etkili olmaz.
  
## <a name="delete-email-address-policies"></a>E-posta adresi ilkelerini silme

EAP'yı silmek için, Remove-EmailAddressPolicy kullanın.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

EAP'nin değiştirilmesi, önceden sağmış olan grupların üzerinde etkili olmaz.
  
## <a name="hybrid-requirements"></a>Karma gereksinimler

Organizasyonunız karma bir senaryoda yapılandırılmışsa, Microsoft 365 grupları oluşturma gereksinimlerini karşılaması için Exchange grupları şirket içi karmayla yapılandırma Microsoft 365.[](/exchange/hybrid-deployment/set-up-microsoft-365-groups) 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>E-posta adresi ilkeleri gruplarını kullanma hakkında ek bilgiler:

Bilmek gereken birkaç şey daha var:
  
- Grupların ne kadar hızlı oluşturuleceği, kurumda yapılandırılan ESA'ların sayısına bağlıdır.
    
- Yöneticiler ve kullanıcılar grup oluşturduklarında etki alanlarını değiştirebilir.
    
- Kullanıcı grubu, önceden kullanılabilen standart sorgular (Kullanıcı özellikleri) kullanılarak belirlenir. Desteklenen [filtrelenebilir özellikler için -RecipientFilter parametresinin](/powershell/exchange/recipientfilter-properties) Filtrelenebilir özellikleri'ne göz atabilirsiniz. 
    
- Hiçbir EAP'yi gruplar için yapılandırmazsanız, grup oluşturma için varsayılan kabul edilen etki alanı seçilir.
    
- Kabul edilen bir etki alanını kaldırırsanız önce ESA'ları güncelleştirmeniz gerekir; aksi takdirde grup sağlama etki olur.
    
- Kuruluş için en fazla 100 e-posta adresi ilkeleri yapılandırabilirsiniz.
    
## <a name="related-content"></a>İlgili içerik

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (makale)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md) (makale)

[Yönetim Microsoft 365 Grup Oluşturma](../admin/create-groups/create-groups.md) (makale)