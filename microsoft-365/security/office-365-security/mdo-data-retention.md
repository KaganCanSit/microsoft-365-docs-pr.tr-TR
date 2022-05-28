---
title: veri saklamayı Office 365 için Microsoft Defender
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Office 365 için Microsoft Defender veri saklama bilgileriThreat Explorer/ Real-Time algılamaları
ms.openlocfilehash: 9cab47358890b47796a42e48b690818d65e20527
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772801"
---
# <a name="data-retention-information-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender için veri saklama bilgileri

Varsayılan olarak, farklı özellikler arasındaki veriler en fazla 30 gün boyunca tutulur. Ancak bazı özellikler için bekletme süresini ilkeye göre belirtebilirsiniz. Her özellik için farklı saklama süreleri için aşağıdaki tabloya bakın.

> [!NOTE]
> Office 365 için Microsoft Defender iki farklı Plan türünde gelir. **'** Gerçek Zamanlı Algılamalar' ve Tehdit Gezgini'niz varsa **Plan 1'iniz** olup olmadığını anlayabilirsiniz. Sahip olduğunuz Plan, göreceğiniz araçları etkiler, bu nedenle öğrenirken Planınızın farkında olduğunuzdan emin olun.

## <a name="defender-for-office-365-plan-1"></a>Office 365 için Defender Plan 1

|Özellik|Bekletme süresi|
|---|---|
|Uyarı meta verileri ayrıntıları (Office uyarıları için Microsoft Defender) | 90 gün |
|Varlık meta veri ayrıntıları (E-postalar) | 30 gün |
|Etkinlik uyarısı ayrıntıları (denetim günlükleri) | 7 gün |
|E-posta varlık sayfası | 30 gün |
|Karantina | 30 gün (en fazla 30 güne kadar yapılandırılabilir) |
|Raporlar | 90 gün (tüm toplanan veriler için) <br>30 gün (aşağıdakiler dışında tüm ayrıntılı bilgiler için) <br> 10 gün (Tehdit koruması durum raporu ayrıntıları ve kimlik sahtekarı posta raporu ayrıntıları için) <br> 7 gün (URL koruma raporu ayrıntıları için) <br>
|Gönderi | 30 gün |
|Tehdit Gezgini/ Real-Time algılamaları | 30 gün |

## <a name="defender-for-office-365-plan-2"></a>Office 365 için Defender Plan 2

plan 1 özelliklerini Office 365 için Defender ayrıca:

|Özellik|Bekletme süresi|
|---|---|
|İşlem Merkezi | 180 gün, 30 gün (Office İşlem merkezi)   |
|Gelişmiş Avcılık | 30 gün |
|AIR (Otomatik Araştırma ve Yanıt) | 60 gün (araştırma meta verileri için)<br> 30 gün (e-posta meta verileri için)  |
|Saldırı Benzetimi Verileri | 18 ay |
|Kampanya | 30 gün |
|Olaylar | 30 gün|
|Düzeltme | 30 gün |
|Tehdit Analizi | 30 gün |
|Tehdit İzleyiciler | 30 gün |
