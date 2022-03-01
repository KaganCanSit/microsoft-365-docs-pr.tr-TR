---
title: Zamanlanmış ve isteğe bağlı taramaları çalıştırın ve özelleştirin.
description: Ağ genelinde uç Microsoft Defender Virüsten Koruma taramalarını özelleştirme ve başlatma
keywords: tarama, zamanlama, özelleştirme, dışlamalar, dosyaları dışlama, düzeltme, tarama sonuçları, karantina, tehdit kaldırma, hızlı tarama, tam tarama, Microsoft Defender Virüsten Koruma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9acac2868b0bd2449338f4a61f663d8cfe8a8ee4
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997055"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Yeni taramalar yapılandırmak için Grup İlkesi, PowerShell Windows Yönetim Aracı'Microsoft Defender Virüsten Koruma kullanabilirsiniz. 

## <a name="in-this-section"></a>Bu bölümde

Konu | Açıklama
---|---
[Taramalarda dosya, klasör ve işlem açık durumdaki dosya dışlamalarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md) | Dosyaları (belirtilen işlemler tarafından değiştirilen dosyalar dahil) ve klasörleri isteğe bağlı taramalardan, zamanlanmış taramalardan ve her zaman gerçek zamanlı koruma izleme ve taramadan çıkarabilirsiniz
[Tarama Microsoft Defender Virüsten Koruma yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Dosyaları, Microsoft Defender Virüsten Koruma tür e-posta depolama dosyalarını, noktaları, arşivlenmiş dosyaları (örneğin, .zip dosyaları) içerecek şekilde yapılandırabilirsiniz. Ağ dosyası taramayı da etkinleştirebilirsiniz
[Taramalar için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md) | Bir Microsoft Defender Virüsten Koruma algılayana kadar ne olacağını ve karantina klasöründe ne kadar süreyle karantinada tutmaları gerektiğini yapılandırma
[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Ne zaman çalıştıracakları ve tam veya hızlı tarama olarak çalıştırıp çalışmamaları da dahil olmak üzere yinelenen (zamanlanmış) taramalar ayarlayın
[Taramaları yapılandırma ve çalıştırma](run-scan-microsoft-defender-antivirus.md) | PowerShell kullanarak isteğe bağlı taramaları, Windows Araçları'Windows veya Windows Güvenliği uygulamasıyla uç noktaları çalıştırma ve yapılandırma
[Tarama sonuçlarını gözden geçirme](review-scan-results-microsoft-defender-antivirus.md) | Microsoft Endpoint Configuration Manager, Microsoft Intune veya Windows Güvenliği uygulamasını kullanarak taramaların sonuçlarını gözden geçirme