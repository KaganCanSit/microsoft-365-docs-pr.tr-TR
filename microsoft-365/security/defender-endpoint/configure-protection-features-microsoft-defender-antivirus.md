---
title: Koruma özelliklerini etkinleştirme Microsoft Defender Virüsten Koruma yapılandırma
description: Microsoft Defender AV'de davranış tabanlı, heuristic ve gerçek zamanlı korumayı etkinleştirin.
keywords: uristic, makine öğrenimi, davranış izlemesi, gerçek zamanlı koruma, her zaman açık, Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender
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
ms.openlocfilehash: f949623b7d0647d71f4c665ed2016ee14a765e5f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015224"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma tehdit koruması sağlamak için çeşitli yöntemler kullanır:

- Yeni ve yeni ortaya çıkan tehditlerin neredeyse anında algılanması ve engellenmesi için bulut koruması
- Dosya ve süreç davranışı izleme ve diğer heuristleri kullanarak her zaman tarama ("gerçek zamanlı koruma" olarak da bilinir)
- Makine öğrenimi, insan ve otomatik büyük veri çözümlemelerine ve derinlemesine tehdit direnci araştırmalarına dayalı özel koruma güncelleştirmeleri

Microsoft Defender Virüsten Koruma'ın bu yöntemleri Grup İlkesi, System Center Configuration Manage, PowerShell cmdlet'leri ve Windows Araç Kullanımı (WMI) ile nasıl kullandığını yapılandırabilirsiniz.

Bu bölüm, güvenli olmayan olarak kabul edilen, ancak kötü amaçlı yazılım olarak algılanmayacak uygulamaların nasıl algılandığından ve engellenmiş olduğu da dahil olmak üzere, her zaman açık taramanın yapılandırmasını kapsar.

Bulut [korumasını etkinleştirme ve Microsoft Defender Virüsten Koruma için bkz.](cloud-protection-microsoft-defender-antivirus.md) Bulut koruması aracılığıyla yeni nesil Microsoft Defender Virüsten Koruma kullanma.

## <a name="in-this-section"></a>Bu bölümde

| Konu|Açıklama |
|---|---|
| [İstenmeyen olabilecek uygulamaları algılama ve engelleme](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Adware, tarayıcı değiştiricileri ve araç çubukları ve ya da sahte virüsten koruma uygulamaları gibi ağ telefonunuzda istenmeyen uygulamaları algıla ve engelle |
| [Veri koruma Microsoft Defender Virüsten Koruma etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|Gerçek zamanlı korumayı, heuristics'i ve her zaman açık diğer her zaman açık Microsoft Defender Virüsten Koruma özellikleri etkinleştirin ve yapılandırın |
