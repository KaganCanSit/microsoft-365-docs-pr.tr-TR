---
title: Zamanlanmış ve isteğe bağlı taramaları çalıştırma ve özelleştirme
description: Ağ genelinde uç Microsoft Defender Virüsten Koruma taramalarını özelleştirin ve başlatabilirsiniz.
keywords: tarama, zamanlama, özelleştirme, dışlamalar, dosyaları dışlama, düzeltme, tarama sonuçları, karantina, tehdit kaldırma, hızlı tarama, tam tarama, Microsoft Defender Virüsten Koruma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: f3e0cc7ffccf02e24b9746d539a44d3a72810ead
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2021
ms.locfileid: "62959636"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans--remediation"></a>Düzeltme için tarama veya tarama Microsoft Defender Virüsten Koruma sonuçlarını & başlatma ve gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/)

Yeni taramalar yapılandırmak için Grup İlkesi, PowerShell Windows Yönetim Aracı'Microsoft Defender Virüsten Koruma kullanabilirsiniz. 

## <a name="in-this-section"></a>Bu bölümde

| Makale | Açıklama |
|:---|:---|
|[Taramalarda dosya, klasör ve işlem açık durumdaki dosya dışlamalarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md) | Dosyaları (belirtilen işlemler tarafından değiştirilen dosyalar dahil) ve klasörleri isteğe bağlı taramalardan, zamanlanmış taramalardan ve her zaman gerçek zamanlı koruma izleme ve taramadan çıkarabilirsiniz |
|[Tarama Microsoft Defender Virüsten Koruma yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md) | E-Microsoft Defender Virüsten Koruma depolama dosyalarını, noktaları, arşivlenmiş dosyaları (örneğin, .zip dosyalarını) taramalara dahil etmek üzere e-posta depolama dosyalarını yapılandırabilirsiniz. Ağ dosyası taramayı da etkinleştirebilirsiniz |
|[Taramalar için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md) | Bir Microsoft Defender Virüsten Koruma algılayana kadar ne olacağını ve karantina klasöründe ne kadar süreyle karantinada tutması gerektiğini yapılandırma |
|[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Ne zaman çalıştıracakları ve tam veya hızlı tarama olarak çalıştırıp çalışmamaları da dahil olmak üzere yinelenen (zamanlanmış) taramalar ayarlayın |
|[Taramaları yapılandırma ve çalıştırma](run-scan-microsoft-defender-antivirus.md) | Windows Güvenliği uygulamasıyla PowerShell'i kullanarak, Windows Yönetim Araç Kullanımı'Windows kullanarak isteğe bağlı taramaları çalıştırma ve yapılandırma |
|[Tarama sonuçlarını gözden geçirme](review-scan-results-microsoft-defender-antivirus.md) | Microsoft Endpoint Configuration Manager, Microsoft Intune veya Windows Güvenliği uygulamasını kullanarak taramaların sonuçlarını gözden geçirme |