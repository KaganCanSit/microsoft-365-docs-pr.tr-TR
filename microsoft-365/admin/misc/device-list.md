---
title: Cihaz listesi CSV dosyası
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: İş için Microsoft 365'da AutoPilot için CSV dosyası oluşturmayı öğrenin.
ms.openlocfilehash: af695448e31ea93d36b36a8831702acb84a92410
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469568"
---
# <a name="windows-autopilot-device-list-csv-file"></a>Windows Autopilot cihaz listesi CSV dosyası

## <a name="device-list-csv-file-format"></a>Cihaz listesi .csv dosya biçimi

Windows Autopilot aracılığıyla cihazları yönetmek ve dağıtmak için cihazlar hakkında belirli bilgileri içeren bir .csv dosyası gerekir.
  
Cihaz listesi dosyasındaki sütunların belirtilen sırada aşağıdaki üst bilgileri olması gerekir:
  
- A sütunu: Cihaz Seri Numarası

- B Sütunu: Boş bırakın

- C sütunu: Donanım Numarası

Bu bilgileri donanım satıcınızdan edinebilir veya CSV dosyasını oluşturmak için [Get-WindowsAutoPilotInfo PowerShell betiğini](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) kullanabilirsiniz. 

Cihazları eklerken, bunları bir Profile da eklemeniz gerekir. Bir cihaza veya bir cihaz grubuna AutoPilot dağıtım profilleri uygulamak için bir profil kullanılır.
  
## <a name="related-content"></a>İlgili içerik

[İş belgeleri ve kaynakları için Microsoft 365](../../index.yml)
  
[İş için Microsoft 365 ile Kullanmaya başlayın](../../admin/admin-overview/what-is-microsoft-365.md)