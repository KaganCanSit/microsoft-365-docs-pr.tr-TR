---
title: Adım 2. Zero Trust Framework kullanarak SOC tümleştirme hazırlık değerlendirmesini gerçekleştirme
description: Bu sistemi güvenlik işlemleriyle tümleştirinken Sıfır Güven Çerçevesi'nin kullanımıyla SOC tümleştirme hazırlık Microsoft 365 Defender temelleri.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1197edf14977c0232936531399d726f62ab70889
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314315"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>Adım 2. Zero Trust Framework kullanarak SOC tümleştirme hazırlık değerlendirmesini gerçekleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Güvenlik İşlemleri Merkezi (SOC) ekibinin temel işlevleri tanımlandığı zaman, organizasyonun bir sonraki adımı Sıfır Güven yaklaşımıyla Microsoft 365 Defender'in [benimsenmesi için hazırlanmaktır](/security/zero-trust/). Benimseme, modern endüstri lideri uygulamaları kullanarak Microsoft 365 Defender gereksinimlerini belirlemenize yardımcı olurken, Microsoft 365 Defender ortamınıza karşı bu özellikleri değerlendirebilirsiniz.

Bu yaklaşım güçlü bir koruma temelını temel alarak kimlik, uç noktalar (cihazlar), veriler, uygulamalar, altyapı ve ağ gibi önemli alanları içerir. Hazırlık Değerlendirme ekibi, hazırlık değerlendirmesini etkinleştirmek için temel gereksinimin Microsoft 365 Defender henüz karşılanmadı ve düzeltme gerektirecek alanları belirler.

SOC'nin SOC'daki süreçleri tam olarak en iyi duruma getirmesi için aşağıda düzeltilleri gerekir:

- **Kimlik:** Eski şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) etki alanları; MFA planı yoktur, ayrıcalıklı hesapların envanteri olmaz ve diğerleri.
- **Uç noktalar (cihazlar):** Çok sayıda eski işletim sistemi, sınırlı cihaz envanteri ve diğerleri.
- **Veriler ve uygulamalar:**  Veri yönetimi standartlarının olmaması, tümleştir olmayacak özel uygulamaların envanteri yoktur.
- **Altyapı:** Çok sayıda ama hiçbir kapsayıcı güvenliği olmayan SaaS lisansı sayısı.
- **Ağ:** Düşük bant genişliği, düz ağ, kablosuz güvenlik sorunları ve diğer sorunlar nedeniyle performans sorunları.

Kuruluşların temel yapılandırma gereksinimleri [kümelerini yakalamak Microsoft 365 Defender](m365d-enable.md) temel yapılandırma gereksinimleri makalesini açması gerekir. Bu adımlar, SOC ekiplerinin kullanım durumlarını etkili bir şekilde geliştirmek için gerçekleştirecekleri düzeltme etkinliklerini de belirler. 

Benimseme yordamları ve kullanım durumu oluşturma işlemi 3. ve 4. Adımlarda açıklanmıştır.

## <a name="next-step"></a>Sonraki adım

[3. Adım. SOC hizmet Microsoft 365 Defender ile veri tümleştirmesi planlama](integrate-microsoft-365-defender-secops-services.md)
