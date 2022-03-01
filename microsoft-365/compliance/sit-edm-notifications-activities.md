---
title: Tam veri eşleşme etkinlikleri için bildirimler oluşturma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Tam veri eşleşme etkinlikleri için bildirimlerin nasıl oluşturulacaklarını öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e5f7c2a2d724a66aea1ce55658ff84e6e0da4738
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010774"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Tam veri eşleşme etkinlikleri için bildirimler oluşturma

Tam veri [eşleşmesi olan (EDM) özel](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) hassas bilgi türleri oluşturulduğunda, denetim günlüğünde oluşturulmuş bir dizi [etkinlik vardır](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). Bu etkinlikler gerçekleşirken [size haber verilmesini sağlamak için New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) PowerShell cmdlet'ini kullanabilirsiniz:

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 EDM etkinlikleri için bildirim oluşturabilme özelliği yalnızca World Wide ve GCC bulutlarda kullanılabilir.

## <a name="pre-requisites"></a>Önkoşullar

Kullanmakta olan hesap, aşağıdaki hesaplardan biri olabilir:

- Genel yönetici
- Uyumluluk yöneticisi
- Exchange Online yönetici

DLP izinleri hakkında daha fazla bilgi edinmek için İzinler'e [bakın](data-loss-prevention-policies.md#permissions).

EDM tabanlı sınıflandırma şu aboneliklere dahildir:

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Uyumluluk
- Microsoft E5/A5 Bilgi Koruması ve Yönetimi

DLP lisansı hakkında daha fazla bilgi edinmek için güvenlik [Microsoft 365 uyumluluk için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>EDM etkinlikleri için bildirimleri yapılandırma

1. Bağlan ve Uyumluluk [Merkezi PowerShell& e bakın](/powershell/exchange/connect-to-scc-powershell).

2. `New-ProtectionAlert` Bildirimi oluşturmak istediğiniz etkinliği kullanarak cmdlet'i çalıştırın.  Örneğin, Verileri Tamamlandı Karşıya Yükle eylemi oluştunda **size bildirilecekse** , şu işlemi çalıştırın:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    **UploadDataFailed için** çalıştır şunları çalıştırarak:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>İlgili makaleler

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)