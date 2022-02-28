---
title: Gruplarda üye ekleme Microsoft 365 kaldırma
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: e186d224-a324-4afa-8300-0e4fc0c3000a
description: Grup üyeleri arasında gruba üye ekleme, gruptan üye kaldırma ve grup sahibi durumunu yönetme hakkında bilgi Microsoft 365 yönetim merkezi.
ms.openlocfilehash: 610da28d6282cb45cb43e086fb3f80acaf18bb05
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983984"
---
# <a name="add-or-remove-members-from-microsoft-365-groups-using-the-admin-center"></a>Yönetim merkezini kullanarak gruplarda Microsoft 365 ekleme veya kaldırma

Grup Microsoft 365, grup üyeleri normalde kendi gruplarını oluşturmalı, katılmak istemedileri gruplara kendilerini eklemeli veya grup sahipleri tarafından davet edilmeleri gerekir. Grup sahipliği değişirse veya bir üyenin eklenmesi veya kaldırılması gerektiğine karar verdiyseniz yönetici olarak siz de bu değişikliği yapabilirsiniz. Bu değişiklikleri yalnızca genel Exchange, Grup yöneticisi veya kullanıcı yöneticisi yapabilirsiniz. [Grup Microsoft 365 nedir?](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

> [!TIP]
> Yönetici değilseniz [Outlook'u kullanarak üye ekleyebilir veya kaldırabilirsiniz](https://support.microsoft.com/office/3b650f4a-5c9b-4f94-a1bb-0cca4b1091de).
  
## <a name="add-a-member-to-a-group-in-the-admin-center"></a>Yönetim merkezinde gruba üye ekleme

1. Yönetim merkezinde Etkin gruplar [**sayfasına**](https://admin.microsoft.com/Adminportal/Home?#/groups) gidin.  

2. Bir grup adına tıklayın.

3. Ayrıntılar bölmesinde, Üyeler sekmesinde, **Tüm üyeleri** görüntüle **ve üyeleri** yönet'i seçin ve sonra da Üye **ekle'yi seçin**.

4. Eklemek istediğiniz üyenin adını arayın veya seçin.

5. **Kaydet**'i seçin.

## <a name="add-a-group-to-a-member-in-the-admin-center"></a>Yönetim merkezinde bir üyeye grup ekleme

1. Yönetim merkezinde Etkin kullanıcılar [**sayfasına**](https://admin.microsoft.com/Adminportal/Home?#/users) gidin.  

2. Bir kullanıcıya tıklayın.

3. Ayrıntılar bölmesindeki Hesap sekmesinde **Grupları** **yönet'i seçin**.

4. Eklemek istediğiniz grubun adını arayın veya seçin.

5. **Kaydet**'i seçin.

## <a name="remove-a-member-from-a-group-in-the-admin-center"></a>Yönetim merkezinde bir gruptan üye kaldırma

> [!NOTE]
> Özel gruptan bir üyeyi kaldırırken, bu kişinin gruptan engellenmiş olması 5 dakika sürer.

1. Yönetim merkezinde Etkin gruplar [**sayfasına**](https://admin.microsoft.com/Adminportal/Home?#/groups) gidin.  

2. Bir grup adına tıklayın.

3. Ayrıntılar bölmesinde, Üyeler sekmesinde, **Tüm** üyeleri görüntüle **ve üyeleri yönet'i seçin**.

4. Kaldırmak istediğiniz üyenin yanındaki X'i seçin.

5. **Üyeyi kaldırmak** için Kaydet'i seçin.

## <a name="manage-group-owner-status"></a>Grup sahibi durumunu yönetme

Varsayılan olarak, grubu oluşturan kişi grup sahibi olur. Çoğunlukla, yedek destek sağlama gibi nedenlerle grupların birden çok sahibi vardır. Üyeler grup sahibi durumuna yükseltilebilir ve grup sahipleri de üye durumuna düşürülebilir.
  
### <a name="promote-a-member-to-owner-status-in-the-admin-center"></a>Yönetici merkezinde üyeyi sahip durumuna tanıtma

1. Yönetim merkezinde Etkin gruplar [**sayfasına**](https://admin.microsoft.com/Adminportal/Home?#/groups) gidin.  

2. Bir grup adına tıklayın.

3. Ayrıntılar bölmesinde, Üyeler sekmesinde, **Tüm** sahipleri görüntüle **ve yönet'i seçin**.

4. Sahip **ekle'yi seçin**.

5. Eklemek istediğiniz üye adının yanındaki onay kutusunu seçin.

6. **Kaydet'i** ve sonra **Kapat'ı seçin**.

### <a name="remove-owner-status-in-the-admin-center"></a>Yönetim merkezinde sahip durumunu kaldırma

1. Yönetim merkezinde Etkin gruplar [**sayfasına**](https://admin.microsoft.com/Adminportal/Home?#/groups) gidin.  

2. Bir grup adına tıklayın.

3. Ayrıntılar bölmesinde, Üyeler sekmesinde, **Tüm** sahipleri görüntüle **ve yönet'i seçin**.

4. Sahibin adının yanındaki X'i seçin.

5. **Kaydet**'i seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory'de grupları dinamik olarak yönetme](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal): "Bir grubun üyeliğini dinamik olarak nasıl yönetirim?" bölümüne bakın.

- Gruplara yüzlerce veya binlerce kullanıcı eklemek için [Add-UnifiedGroupLinks'i kullanın](/powershell/module/exchange/add-unifiedgrouplinks).

- [Sahipsiz bir gruba yeni sahip atama](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732)

## <a name="related-content"></a>İlgili içerik

[Dağıtım listelerini Microsoft 365 gruplarına yükseltme (Outlook](../manage/upgrade-distribution-lists.md))\
[Dağıtım listelerinizi neden Yeni Sürüm'de gruplara Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188) (makale)\
[Gruplarda konuk erişimini Microsoft 365 (](manage-guest-access-in-groups.md)makale)\
[PowerShell Microsoft 365 grupları](../../enterprise/manage-microsoft-365-groups-with-powershell.md) yönetme: Bu makalede önemli cmdlet'leri tanıtıyor ve örnekler (makale)\
[Microsoft 365 grupları adlandırma ilkesi (](../../solutions/groups-naming-policy.md)makale)