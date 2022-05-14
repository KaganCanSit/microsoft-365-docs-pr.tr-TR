---
title: Microsoft Defender Virüsten Koruma koruma özelliklerini etkinleştirme ve yapılandırma
description: Microsoft Defender AV'de davranış tabanlı, buluşsal ve gerçek zamanlı korumayı etkinleştirin.
keywords: buluşsal, makine öğrenmesi, davranış izleme, gerçek zamanlı koruma, her zaman açık, Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 57f66dd4643ea04c505e61ea2db40a7ac9a61e68
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419208"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Davranışsal, buluşsal ve gerçek zamanlı korumayı yapılandırın


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma 

**Platform**
- Windows

Microsoft Defender Virüsten Koruma tehdit koruması sağlamak için çeşitli yöntemler kullanır:

- Yeni ve yeni tehditlerin neredeyse anında algılanması ve engellenmesi için bulut koruması
- Dosya ve işlem davranışı izleme ve diğer buluşsal yöntemleri kullanarak ("gerçek zamanlı koruma" olarak da bilinir) her zaman açık tarama
- Makine öğrenmesi, insan ve otomatik büyük veri analizi ve ayrıntılı tehdit direnci araştırmalarına dayalı ayrılmış koruma güncelleştirmeleri

Microsoft Defender Virüsten Koruma grup ilkesi, System Center Yapılandırma Yönetimi, PowerShell cmdlet'leri ve Windows Yönetim Araçları (WMI) ile bu yöntemleri nasıl kullandığını yapılandırabilirsiniz.

Bu bölüm, güvenli olmadığı kabul edilen ancak kötü amaçlı yazılım olarak algılanamayan uygulamaları algılama ve engelleme de dahil olmak üzere her zaman açık tarama için yapılandırmayı kapsar.

Microsoft Defender Virüsten Koruma bulut korumasını etkinleştirme ve yapılandırma için bkz. [Bulut koruması aracılığıyla yeni nesil Microsoft Defender Virüsten Koruma teknolojilerini kullanma](cloud-protection-microsoft-defender-antivirus.md).

## <a name="in-this-section"></a>Bu bölümde

| Konu|Açıklama |
|---|---|
| [İstenmeyen olası uygulamaları tespit edin ve engelleyin](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Ağınızda reklam yazılımı, tarayıcı değiştiricileri ve araç çubukları ve sahte veya sahte virüsten koruma uygulamaları gibi istenmeyen uygulamaları algılama ve engelleme |
| [Microsoft Defender Virüsten Koruma koruma özelliklerini etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|Gerçek zamanlı korumayı, buluşsal yöntemleri ve diğer her zaman açık Microsoft Defender Virüsten Koruma izleme özelliklerini etkinleştirme ve yapılandırma |

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
