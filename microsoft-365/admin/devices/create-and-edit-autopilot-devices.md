---
title: AutoPilot cihazlarını oluşturma ve düzenleme
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Microsoft 365 İş Ekstra'da AutoPilot kullanarak cihazları karşıya Microsoft 365 İş Ekstra. Bir cihaza veya cihaz grubuna profil atabilirsiniz.
ms.openlocfilehash: 96034ca50da114adca60169ae29da5948793b498
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984124"
---
# <a name="create-and-edit-autopilot-devices"></a>AutoPilot cihazlarını oluşturma ve düzenleme

## <a name="upload-a-list-of-devices"></a>Cihaz listesini karşıya yükleme

Cihazları karşıya yüklemek [için Adım adım kılavuzu kullanabilirsiniz](add-autopilot-devices-and-profile.md) , ancak cihazları Cihazlar sekmesinden de **karşıya yükleyebilirsiniz** . 
  
Cihazlar şu gereksinimleri karşılamalıdır:
  
- Windows 10, sürüm 1703 veya sonrası
    
- Henüz ilk ve en son Windows yeni cihazlar

1. Daha fazla Microsoft 365 yönetim merkezi **Devices** **AutoPilot'ı**\> seçin.
  
2. **AutoPilot sayfasında** Cihazlar sekmesini Cihaz **ekle'yi** \> **seçin**.
    
    ![In the Devices tab, choose Add devices.](../../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Cihaz **ekle panelinde**, Kapat'ı Kaydet'i [hazırlayın bir](../misc/device-list.md) Cihaz listesi CSV **dosyasına** \> \> **göz atabilirsiniz**.
    
    Bu bilgileri donanım satıcıdan edinebilirsiniz veya CSV dosyası oluşturmak için [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) betiği kullanabilirsiniz. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Cihaza veya cihaz grubuna profil atama

1. Şu cihazları **Windows** Cihazlar sekmesini **seçin ve** bir veya birden çok cihaz yanındaki onay kutusunu seçin. 
    
2. **Cihaz** panelinde, **Atanan profil** açılan listesinden bir profil seçin. 
    
    Henüz hiç profiliniz yoksa, yönergeler için bkz. [AutoPilot profillerini oluşturma ve düzenleme](create-and-edit-autopilot-profiles.md). 
