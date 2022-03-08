---
title: Kimlik için Microsoft Defender'ı Pilot Uygulama
description: Kimlik için Microsoft Defender'ı pilot edin, karşılaştırma ayarlayın, uyumlu çalışma, kimlik bilgilerinin güvenliği ihlal edildi, esnaf hareketi, etki alanı dominasyonu ve sızıntı uyarıları hakkında öğreticiler edin.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 3801fdb4a7aeda5e75c4e36f622f7e76604d96a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318739"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Kimlik için Microsoft Defender'ı Pilot Uygulama


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale [, Kimlik için](eval-defender-identity-overview.md) Microsoft Defender değerlendirme ortamını ayarlama işleminin 3. adımıdır. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-identity-overview.md).

Microsoft Defender'da kimlik için pilot uygulamanın kurulumu ve yapılandırılması için aşağıdaki adımları kullanın. Önerilerin pilot grup ayarlamaya dahil olmadığını unutmayın. En iyi uygulama, devam etmek ve Active Directory Etki Alanı Hizmetleri (AD DS) ve Active Directory Federasyon Hizmetleri (AD FS) çalıştıran tüm sunucularınıza algılayıcı yüklemektir.

![Defender değerlendirme ortamına Kimlik için Microsoft Defender ekleme adımları.](../../media/defender/m365-defender-identity-pilot-steps.png)

Aşağıdaki tabloda, çizimde yer alan adımlar açık gösterilmiştir.

- [1. Adım: Kimlik ortamınız için karşılaştırma önerilerini yapılandırma](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [2. Adım: Özellikleri deneyin : Farklı saldırı türlerini tanımlamak ve düzeltme için öğreticilere göz atabilirsiniz ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>Adım 1. Kimlik ortamınız için karşılaştırma önerilerini yapılandırma

Microsoft, Microsoft Bulut hizmetlerini kullanan müşteriler için güvenlik karşılaştırma önerileri sunar. [Azure Güvenlik KarşılaştırmaSı](/security/benchmark/azure/overview) (ASB), Azure'da iş yüklerinin, verilerin ve hizmetlerin güvenliğini iyileştirmeye yardımcı olmak için en iyi uygulamaları ve önerileri sağlar.

Bu karşılaştırma önerileri Kimlik için [Microsoft Defender için Azure güvenlik temeli içerir](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). Bu önerilerin uygulanması biraz zaman alıp plan yapmak ve uygulamak olabilir. Bunlar kimlik ortamının güvenliğini önemli ölçüde artırsa da Kimlik için Microsoft Defender'ı değerlendirmeye ve uygulamaya devam etmenizi engellemezler. Bunlar, farkındalığınız için burada sağlanmıştır.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>Adım 2. Özellikleri deneyin: Farklı saldırı türlerini belirlemek ve düzeltme için öğreticilere göz atabilirsiniz

Identity için Microsoft Defender belgeleri, çeşitli saldırı türlerini tanımlama ve düzeltme sürecini takip eden bir dizi öğretici içerir.

Kimlik için Defender öğreticilerini deneyin:
- [Reconnaissance alerts](/defender-for-identity/reconnaissance-alerts)
- [Güvenliği ihlal edilmiş kimlik bilgileri uyarıları](/defender-for-identity/compromised-credentials-alerts)
- [Lateral movement alerts](/defender-for-identity/lateral-movement-alerts)
- [Etki alanı dominance uyarıları](/defender-for-identity/domain-dominance-alerts)
- [Exfiltration uyarıları](/defender-for-identity/exfiltration-alerts)
- [Kullanıcı araştırma](/defender-for-identity/investigate-a-user)
- [Bilgisayarı araştırma](/defender-for-identity/investigate-a-computer)
- [Lateral movement paths](/defender-for-identity/investigate-lateral-movement-path)
- [Varlıkları araştırma](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>Sonraki adımlar

[Microsoft Defender'ı Office 365](eval-defender-office-365-overview.md)

Windows için [Microsoft Defender'ı Değerlendirme genel görünümüne Office 365](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)