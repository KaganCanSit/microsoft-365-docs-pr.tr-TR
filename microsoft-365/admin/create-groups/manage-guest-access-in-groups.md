---
title: Gruplarda konuk Microsoft 365 yönetme
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
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Konuk erişimini kontrol etmek için grup Microsoft 365, konuk kullanıcıları görüntüleme ve PowerShell kullanma hakkında bilgi öğrenin.
ms.openlocfilehash: 99c0a9f46abfffe56f8c751ca614287181f39a5d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983981"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gruplarda konuk Microsoft 365 yönetme

Varsayılan olarak, tüm Microsoft 365 için konuk erişimi, sizin için açıktır. Yöneticiler, tüm kuruluşları için veya tek tek gruplar için konuk erişimine izin verilip izin ver vermeyeceğini kontrol ediyor.

Açık olduğunda, grup üyeleri Web'de herhangi bir web sitesi aracılığıyla konuk Microsoft 365 konuk Outlook davet etmelerini sağlar. Davetler onay için grup sahibine gönderilir.

Onaylanan konuk kullanıcı dizine ve gruba eklenir.

> [!Note]
> Yammer Enterprise Modunda veya AB Coğrafi olarak olan [ağlarda](/yammer/manage-security-and-compliance/manage-data-compliance) ağ konuklarını desteklemez.
> Microsoft 365 Bağlı Yammer şu anda konuk erişimini desteklemez, ancak bağlı olmayan, dış grupları Yammer oluşturabilirsiniz. Yönergeler [için bkz. Dış grupları Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) yönetme.

Gruplara konuk erişimi, genellikle konuk erişimi veya özel konuk SharePoint daha kapsamlı Teams. Bu hizmetlerin kendi konuk paylaşım ayarları vardır. Gruplar, gruplar, gruplar ve gruplar arasında konuk paylaşımını ayarlamaya SharePoint tam Teams bkz.

- [Bir sitede konuklarla işbirliği yapma](../../solutions/collaborate-in-site.md)
- [Ekipte konuklarla işbirliği yapma](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Grupların konuk erişimini yönetme

Gruplarda konuk erişimini etkinleştirmek veya devre dışı bırakmak için, bunu Gruplar'da <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**da yapabiliriz**</a>.

1. Yönetim merkezinde Tüm Kuruluş ayarlarını **göster'Ayarlar** \>  \> **gidin** ve Hizmetler sekmesinde **Gruplara** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Ekle'Microsoft 365 seçin**</a>.
  
2. Gruplar **Microsoft 365,** kuruluş dışındaki kişilerin grup kaynaklarına erişmesine izin mi yoksa grup sahiplerinin, kuruluş dışındaki kişilerin gruplara eklemesine izin mi etmek istediğinize karar verme.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Yönetim merkezinden Microsoft 365 Grup grubuna konuk ekleme

Konuk zaten dizinde yer alan bir konuksa, onu dizinden gruplarınıza <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Microsoft 365 yönetim merkezi</a>. (Dinamik üyeliği olan gruplar grup [olarak Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. Yönetim merkezinde **GroupsGroups'a** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**gidin**</a>.
  
2. Konuğu eklemek istediğiniz gruba tıklayın ve Üyeler sekmesinde Tüm üyeleri **görüntüle ve yönet'i** seçin. 
  
4. Üye **ekle'yi** seçin ve eklemek istediğiniz konuğun adını seçin.
    
5. **Kaydet**'i seçin.

Doğrudan dizine konuk eklemek için [Azure portalında B2B işbirliği kullanıcılarını Azure Active Directory kişi edebilirsiniz](/azure/active-directory/b2b/add-users-administrator).

Bir konuğun bilgilerini düzenlemek için Bu Kişi Ekle'yi kullanarak bir kullanıcının [profil bilgilerini ekleyebilir veya Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>İlgili içerik

[Konuk kullanıcıları belirli bir gruptan engelleme](../../solutions/per-group-guest-access.md) (makale)\
[Grupta grup üyeliğini Microsoft 365 yönetim merkezi](add-or-remove-members-from-groups.md) (makale)\
[Azure Active Directory incelemeler](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (makale)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (makale)