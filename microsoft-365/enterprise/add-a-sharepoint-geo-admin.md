---
title: Coğrafi yönetici ekleme veya kaldırma
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Her coğrafi konum için ayrı yöneticiler yapılandırmanız mı gerekiyor? Microsoft 365 Multi-Geo'da coğrafi yönetici ekleme veya kaldırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e661e42759fe0b035bfe97c33165f78316973403
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973847"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Multi-Geo'da coğrafi yönetici Microsoft 365 ekleme veya kaldırma

Kiracınıza sahip olduğunuz her coğrafi konum için ayrı yöneticiler yapılandırabilirsiniz. Bu yöneticiler, SharePoint Online'a OneDrive coğrafi konumlarına özgü ayarları kullanabilir.

Terim deposu gibi bazı hizmetler merkezi konumdan yönette ve uydu konumlara çoğaltılır. Merkezi konumun coğrafi yöneticisi bunlara erişime sahiptir, ancak uydu konumlarına coğrafi yöneticilerin erişimi vardır.

Genel yöneticiler ve SharePoint Online yöneticileri merkezi konumdaki ve tüm uydu konumlarında ayarlara erişmeye devam eder.

## <a name="configuring-geo-administrators"></a>Coğrafi yöneticileri yapılandırma

Coğrafi yöneticilerin yapılandırılması için SharePoint Online PowerShell modülü gerekir.

[Bağlan-SPOService'i](/powershell/module/sharepoint-online/Connect-SPOService) kullanarak coğrafi yöneticiyi eklemek istediğiniz coğrafi konumun yönetim merkezine bağlanın. (Örneğin, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Bir konumun mevcut coğrafi yöneticilerini görüntülemek için `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Bir kullanıcı coğrafi yönetici olarak ekleme

Bir kullanıcı coğrafi yönetici olarak eklemek için `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Bir kullanıcıyı bir konumun Coğrafi Yöneticisi olarak kaldırmak için  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Grubu coğrafi yönetici olarak ekleme

Bir güvenlik grubunu veya posta etkin güvenlik grubunu coğrafi yönetici olarak  ekleme. (Dağıtım grupları Microsoft 365 grupları desteklenmiyor.)

Grubu coğrafi yönetici olarak eklemek için `Add-SPOGeoAdministrator -GroupAlias <alias>`

Grubu coğrafi yönetici olarak kaldırmak için `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Tüm güvenlik gruplarının grup diğer adı olmadığını unutmayın. Diğer adı olmayan bir güvenlik grubu eklemek için [, Get-MsolGroup'i](/powershell/module/msonline/get-msolgroup) çalıştırarak grupların listesini alın, güvenlik grubu nesnenin ObjectID'nizi bulun ve çalıştırın:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

ObjectID kullanarak bir grubu kaldırmak için `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="related-topics"></a>İlgili konular

[Add-SPOGeoAdministrator](/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Güvenlik grubu için diğer ad (MailNickName) ayarlama](/powershell/module/azuread/set-azureadgroup)