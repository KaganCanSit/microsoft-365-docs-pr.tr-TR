---
title: Dağıtım aşamaları
description: Bu hizmete uç Uç Nokta için Microsoft Defender hazırlarken, ayarerek ve hazırlarken bu uç noktaların nasıl dağıtın olduğunu öğrenin
keywords: dağıtma, hazırlama, kurulum, ekleme, aşama, dağıtım, dağıtma, benimseme, yapılandırma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-overview
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c39ef92448317e625f3f2e6948f69a38093b1504
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467719"
---
# <a name="deployment-phases"></a>Dağıtım aşamaları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kuruluş için engelleme Uç Nokta için Microsoft Defender, ihlal sonrası algılama, otomatik soruşturma ve yanıttan yararlanmak için güvenlik engellemelerini nasıl dağıtın?

Bu kılavuz, ortamınızı hazırlamak ve ardından cihazları yöntemsel bir yolla, değerlendirmeden anlamlı bir pilota, tam dağıtıma hazırlamak için proje katılımcıları arasında çalışmanıza yardımcı olur.

Her bölüm bu çözümde ayrı bir makaleye karşılık geldi.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Tablodaki ayrıntıların yer olduğu dağıtım aşamaları" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Dağıtım aşamalarının özeti: hazırlama, kurulum, ekleme" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Aşama|Açıklama|
|---|---|
|[Aşama 1: Hazırlama](prepare-deployment.md)|Paydaş onayları, ortamın dikkate alınması, erişim izinleri ve yeteneklerin benimsenmesi sırası gibi Uç nokta için Defender'ı dağıtırken dikkate alınması gerekenler hakkında bilgi alın.|
|[Aşama 2: Kurulum](production-deployment.md)|Lisanslama, ayarlama sihirbazını tamamlama ve ağ yapılandırması gibi portala erişmek için atılması gereken ilk adımlarda yol gösterir.|
|[Aşama 3: Ekleme](onboarding.md)|Dağıtım halkalarını kullanmayı, uç noktanın türüne bağlı olarak desteklenen ekleme araçlarını ve kullanılabilir özellikleri yapılandırmayı öğrenin.|
|

Bu kılavuzu tamamlandıktan sonra doğru erişim izinleri ile ayarlanır, uç noktalarınız hazırlanır ve algılayıcı verilerini hizmete bildirecek ve yeni nesil koruma ve saldırı yüzeyini azaltma gibi özellikler uygulanır.

Dağıtım planlama kılavuzunda ana hatlarıyla açıklanan ortamın mimarisine ve dağıtım yöntemine [](deployment-strategy.md) bakılmaksızın, bu kılavuz sizi ekleme uç noktalarında destekleyecektir.

## <a name="key-capabilities"></a>Önemli özellikler

Uç Nokta için Microsoft Defender çok sayıda özellik sağlarken, bu dağıtım kılavuzunun temel amacı, cihaz eklemeye başlamanızı sağlar. Bu kılavuz, eklemeye ek olarak aşağıdaki özelliklerle başlamana da yardımcı olur.

<br>

****

|Özellik|Açıklama|
|---|---|
|Uç nokta algılama ve yanıt|Uç nokta algılama ve yanıt özellikleri izinsiz giriş girişimlerini ve etkin ihlalleri algılamak, araştırmak ve yanıtlamak için kullanılır.|
|Yeni nesil koruma|Ağın güvenlik çevresini daha da güçlendirmek için Uç Nokta için Microsoft Defender her tür yeni tehdityi yakalamak için tasarlanmış yeni nesil korumayı kullanır.|
|Saldırı yüzeyini azaltma|Yığında ilk savunma hattını sağla. Yapılandırma ayarlarının doğru bir şekilde ayarlanmış olması ve açıktan yararlanma azaltma tekniklerinin uygulanmasıyla, bu özellikler saldırılara ve sömürüye karşı karşı koyar.|
|

Bu becerilerin tüm özellikleri Uç Nokta için Microsoft Defender kullanılabilir. Daha fazla bilgi için Lisans [gereksinimleri'ne bakın](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Kapsam

### <a name="in-scope"></a>Kapsamda

- Uç noktaları hizmete Microsoft Endpoint Manager uç Microsoft Endpoint Configuration Manager noktaları Microsoft Endpoint Manager uç noktaları kullanma ve özellikleri yapılandırma
- Uç Nokta Özellikleri (uç noktada algılama ve yanıtlama) özellikleri EDR Defender'ı etkinleştirme
- Uç nokta uç nokta koruma platformu (EPP) özellikleri için Defender'ı etkinleştirme
  - Yeni nesil koruma
  - Saldırı yüzeyini azaltma

### <a name="out-of-scope"></a>Kapsam dışında

Aşağıdakiler, bu dağıtım kılavuzunun kapsamı dışındadır:

- Uç Nokta için Defender ile tümleştiren üçüncü taraf çözümlerinin yapılandırması
- Üretim ortamında test etme

## <a name="see-also"></a>Ayrıca bkz.

- [Aşama 1: Hazırlama](prepare-deployment.md)
- [Aşama 2: Ayarlama](production-deployment.md)
- [Aşama 3: Ekleme](onboarding.md)
- [Dağıtımı planlama](deployment-strategy.md)
