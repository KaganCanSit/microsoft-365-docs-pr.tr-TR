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
description: Microsoft 365 İş'te AutoPilot için CSV dosyası yapmayı öğrenin.
ms.openlocfilehash: 62dbcddbdab1a08ab3b19c6616b814c421a57c04
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996603"
---
# <a name="device-list-csv-file"></a>Cihaz listesi CSV dosyası

## <a name="device-list-csv-file-format"></a>Cihaz listesi .csv biçimi

AutoPilot'a Windows cihazları yönetmek ve dağıtmak için, cihazlar hakkında belirli .csv içeren bir .csv dosyası gerekir.
  
Cihaz listesi dosyasındaki sütunlar, belirtilen sırada aşağıdaki başlıklara sahip olması gerekir:
  
- A sütunu: Cihaz Seri Numarası

- B Sütunu: Boş bırakın

- C sütunu: Donanım Numarası

Bu bilgileri donanım satıcınızdan edinebilir veya CSV dosyasını oluşturmak için [Get-WindowsAutoPilotInfo PowerShell betiğini](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) kullanabilirsiniz. 

Cihaz eklerken, bunları bir Profile de eklemeniz gerekir. Bir cihaza veya cihaz grubuna AutoPilot dağıtım profillerini uygulamak için bir profil kullanılır.
  
## <a name="related-content"></a>İlgili içerik

[Microsoft 365 belgeleri ve kaynakları için belgeler](../../index.yml)
  
[Microsoft 365 kurumsal ile çalışmaya başlama](../../admin/admin-overview/what-is-microsoft-365.md)