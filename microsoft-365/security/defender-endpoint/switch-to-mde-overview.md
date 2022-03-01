---
title: Microsoft olmayan uç nokta korumasından Uç Nokta için Microsoft Defender'a geçme
description: Uç nokta koruma çözümünüz için uç nokta koruma çözümünüz için Microsoft Defender Virüsten Koruma için Microsoft Defender'a geçiş yapma.
keywords: geçiş, windows defender, gelişmiş uç nokta koruması, virüsten koruma, kötü amaçlı yazılımdan koruma, pasif modu, etkin mod
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- m365initiative-defender-endpoint
ms.topic: overview
ms.custom: migrationguides
ms.date: 11/29/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: eb0971c6f5b8fd8bf37f3d33cb65cff8d331e0d0
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010016"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Microsoft olmayan uç nokta korumasından Uç Nokta için Microsoft Defender'a geçme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804) Microsoft olmayan bir uç nokta koruma çözümünden Uç Nokta için [Microsoft Defender'a](microsoft-defender-endpoint.md) (Uç Nokta için Defender) geçmeyi planlıyorsanız veya planlama aşamasındaysanız, bu makaleyi kılavuz olarak kullanın. Bu makalede, Uç Nokta için Defender'a taşıma işleminin genel süreci açıklanmıştır.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Uç nokta koruma çözümlerinizi Uç nokta için Defender'a geçiş.":::

Uç nokta için Defender'a geçişte, etkin modda Microsoft dışı virüsten koruma/kötü amaçlı yazılımlardan koruma ile başlarsınız. Ardından, pasif modunda Microsoft Defender Virüsten Koruma ve cihazlarınızı Uç Nokta için Defender'a başlatın. Ardından uç nokta koruma özelliklerinizi yapılandırmış, Microsoft Defender Virüsten Koruma moduna ayarlamış ve her şeyin düzgün çalıştığını doğrularsınız. Son olarak, Microsoft olmayan çözümü kaldırırsiniz.

## <a name="the-migration-process"></a>Geçiş işlemi

Aşağıdaki tabloda açıklandığı gibi, Uç nokta için Defender'a geç işlemi üç aşamaya ayrılarak bölünebilirsiniz:

![MDE geçiş işlemi.](images/phase-diagrams/migration-phases.png)

<br/><br/>

|Aşama|Açıklama|
|--|--|
|[Geçişe hazırlanma](switch-to-mde-phase-1.md)|Hazırla [**aşamasında**](switch-to-mde-phase-1.md): <br/>1. Kuruluş cihazlarınızı güncelleştirin.<br/>2. Uç Nokta için Defender'ı Al.<br/>3. Rolleri ve izinleri plan edin ve portala Microsoft 365 Defender verin.<br/>4. Cihazınızın cihazları ve Uç nokta için Defender arasındaki iletişimi etkinleştirmek üzere cihaz ara sunucu ve internet ayarlarınızı yapılandırabilirsiniz. |
|[Uç Nokta için Defender'ı ayarlama](switch-to-mde-phase-2.md)|Kurulum [**aşamasında**](switch-to-mde-phase-2.md): <br/>1. E-Microsoft Defender Virüsten Koruma etkinleştirin/yeniden yükleyin ve pasif moduna ayarlayın.<br/>2. Uç Nokta için Defender'ı yapılandır.<br/>3. Var olan çözümünüz için dışlama listesine Uç Nokta için Defender ekleyin.<br/>4. Mevcut çözümlerinizi dışlama listesine sizin için Microsoft Defender Virüsten Koruma.<br/>5. Cihaz gruplarınızı, koleksiyonlarınızı ve kuruluş birimlerinizi ayarlayın.<br/>6. Kötü amaçlı yazılımdan koruma ilkelerinizi ve gerçek zamanlı koruma ayarlarınızı yapılandırma.|
|[Uç Nokta için Defender'a Ekleme](switch-to-mde-phase-3.md)|Ekleme [**aşamasında**](switch-to-mde-phase-3.md): <br/>1. Cihazlarınızı Uç Nokta için Defender'a ekleme.<br/>2. Bir algılama testi çalıştırın.<br/>3. Edilgen Microsoft Defender Virüsten Koruma modunda çalıştır bu onaylayın.<br/>4. Yeni e-posta güncelleştirmelerini Microsoft Defender Virüsten Koruma.<br/>5. Var olan uç nokta koruma çözümlerinizi kaldırın.<br/>6. Uç nokta için Defender'ın doğru şekilde çalıştığına emin olun.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'a neler dahildir?

Bu geçiş kılavuzunda yeni nesil koruma ve [](microsoft-defender-antivirus-in-windows-10.md) uç noktada algılama ve yanıtlama için Defender for Endpoint'a geçişte başlangıç noktası olarak bu özelliklere odaklanacağız.[](overview-endpoint-detection-response.md) Bununla birlikte, Uç Nokta için Defender virüsten koruma ve uç nokta korumasından çok daha fazlasını içerir. Uç Nokta için Defender, koruma, ihlal sonrası algılama, otomatik soruşturma ve yanıt için birleşik bir platformdur. Aşağıdaki tabloda, Uç Nokta için Defender'daki özellikler ve özellikler özetlenmiştir.

<br/><br/>

|Özellik/Özellik|Açıklama|
|---|---|
|[Tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)|Tehdit & güvenlik açığı yönetimi özellikleri, uç noktalarınız genelinde (örneğin cihazlar) zayıf noktaları belirlemeye, değerlendirmeye ve düzeltmeye yardımcı olur.|
|[Saldırı yüzeyini azaltma](overview-attack-surface-reduction.md)|Saldırı yüzeyini azaltma kuralları, kuruluş cihazlarınızı ve uygulamalarınızı siber tehditlere ve saldırılara karşı korumaya yardımcı olur.|
|[Yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md)|Yeni nesil koruma, tehditleri Microsoft Defender Virüsten Koruma kötü amaçlı yazılımları engellemeye yardımcı olacak yeni nesil koruma yazılımlarını içerir.|
|[Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md)|Uç nokta algılama ve yanıt özellikleri izinsiz giriş girişimlerini ve etkin ihlalleri algılar, araştırma ve yanıtlama özellikleri.|
|[Gelişmiş av](advanced-hunting-overview.md)|Gelişmiş koruma özellikleri, güvenlik işlemleri ekibimizin bilinen veya potansiyel tehditlere yönelik göstergeleri ve varlıkları bulmasını sağlar.|
|[Davranışsal engelleme ve engelleme](behavioral-blocking-containment.md)|Davranışsal engelleme ve engelleme özellikleri, tehdit yürütmeye başlamış olsalar bile davranışlarını ve işlem ağaçlarını temel alarak tehditleri belirlemeye ve durdurmaya yardımcı olur.|
|[Otomatik araştırma ve düzeltme](automated-investigations.md)|Otomatik araştırma ve yanıt özellikleri uyarıları inceler ve ihlalleri çözmek için hemen düzeltme eylemi alır.|
|[Tehdit arama hizmeti](microsoft-threat-experts.md) (Microsoft Tehdit Uzmanları)|Tehdit arama hizmetleri, uzman düzeyinde izleme ve çözümlemeler yapan güvenlik işlemleri ekipleri sağlar ve kritik tehditlere karşı atlamamalarına yardımcı olur.|

**Daha fazla bilgi edinmek mi istiyor musunuz? Bkz [. Uç Nokta için Defender](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>Sonraki adım

- Geçişe [hazırlanmaya devam edin](switch-to-mde-phase-1.md).
