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
ms.openlocfilehash: 784db256bb5dae16739722566b6f7a9c8511a678
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313895"
---
# <a name="create-and-edit-autopilot-devices"></a>AutoPilot cihazlarını oluşturma ve düzenleme

> [!NOTE]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

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

## <a name="see-also"></a>Ayrıca bkz.

[kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](../security-and-compliance/secure-your-business-data.md)