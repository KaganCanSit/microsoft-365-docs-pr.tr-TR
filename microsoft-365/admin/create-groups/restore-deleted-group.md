---
title: Silinmiş bir grup Microsoft 365 geri yükleme
ms.reviewer: arvaradh
f1.keywords: CSH
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: Silinen bir grup 30 gün boyunca korunur ve grubu yine de geri yükleyebilirsiniz. 30 gün sonra, grup ve içeriği kalıcı olarak silinir.
ms.openlocfilehash: 926cfa18972a7ca72009258b02b565bd28a183be
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983978"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Silinmiş bir grup Microsoft 365 geri yükleme

Grubu sildikten sonra, grup varsayılan olarak 30 gün boyunca korunur. Bu 30 günlük süre "yumuşak silme" olarak kabul edilir, çünkü grubu yine de geri yükleyebilirsiniz. 30 gün sonra, grup ve ilişkili içeriği kalıcı olarak silinir ve geri yüklenir.

Grup geri yüklendiğinde, aşağıdaki içerikler geri yüklenir:
  
- Azure Active Directory (AD) Microsoft 365 Groups nesnesi, özellikleri ve üyelerini görüntüler.
    
- Grubun e-posta adresleri.
    
- Exchange Online Kutusu'na ve takvime tıklayın.
    
- SharePoint Online ekip sitesi ve dosyaları.
    
- OneNote not defteri
    
- Planner
    
- Teams

- Yammer ve grup içeriğinin nasıl oluşturulacaklarını seçin (Microsoft 365 grup, gruptan Yammer)

- Power BI [Klasik çalışma alanı](/power-bi/collaborate-share/service-create-workspaces)

> [!NOTE]
> Bu makalede yalnızca kullanıcı gruplarının geri Microsoft 365 açıklanmıştır. Diğer tüm gruplar bir kez silindikten sonra geri yüklenebilir.

## <a name="restore-a-group"></a>Grubu geri yükleme

# <a name="outlook"></a>[Outlook](#tab/outlook)

Bir grup sahibiyseniz, Microsoft 365 aşağıdaki adımları kullanarak grubu kendiniz Web üzerinde Outlook geri yükleyebilirsiniz:

1. Silinmiş gruplar [sayfasında Gruplar düğümünün](https://outlook.office.com/people/group/deleted) **altındaki Grupları yönet** seçeneğini belirleyin **ve** ardından Silinmiş'i **seçin**.

2. Geri yüklemek **istediğiniz** grubun yanındaki Geri Yükle sekmesine tıklayın.

Silinen grup burada görünmüyorsa, yöneticiye başvurun.

# <a name="admin-center"></a>[Yönetim merkezi](#tab/admin-center)

Genel yönetici veya grup yöneticisiyseniz, silinmiş bir grubu aşağıdaki çalışma grubunda geri Microsoft 365 yönetim merkezi:

1. Yönetim merkezine [gidin](https://admin.microsoft.com).
2. **Gruplar'ı** genişletin ve Ardından Silinmiş **gruplar'ı tıklatın**.
3. Geri yüklemek istediğiniz grubu seçin ve grubu geri **yükle'ye tıklayın**.

> [!NOTE]
> Bazı durumlarda, grubun ve tüm verilerin geri yüklenebilir olması 24 saat kadar sürebilir. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Gruplarla ilgili sorularınız Microsoft 365 mi var?

Gruplarla [ilgili soru Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) ve konuşmalara katılmak için Microsoft Tech Microsoft 365 ziyaret edin. 
  
## <a name="related-content"></a>İlgili içerik

[PowerShell Microsoft 365 Grupları Yönetme](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (makale)\
[Remove-UnifiedGroup cmdlet'ini](/powershell/module/exchange/remove-unifiedgroup) kullanarak grupları silme (makale)\
[Grup bağlantılı ekip sitesi ayarlarınızı yönetme](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (makale)\
[Grup silme Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (makale)
