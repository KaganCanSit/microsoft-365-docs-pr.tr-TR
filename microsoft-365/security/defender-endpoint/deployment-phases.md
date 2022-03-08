---
title: Dağıtım aşamaları
description: Bu hizmet için uç noktaları hazırlarken, ayararak ve hazırlarken Uç Nokta için Microsoft Defender'ı dağıtmayı öğrenin
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
ms.openlocfilehash: 5715a796e0c7b78ae369f074b5edcb6ccfc8ae90
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330573"
---
# <a name="deployment-phases"></a>Dağıtım aşamaları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kuruluş olarak korumanın, ihlal sonrası algılamadan, otomatik soruşturmadan ve yanıttan yararlanmak için Uç Nokta için Microsoft Defender'ı dağıtmayı öğrenin.

Bu kılavuz, ortamınızı hazırlamak ve ardından cihazları yöntemsel bir yolla, değerlendirmeden anlamlı bir pilota, tam dağıtıma hazırlamak için proje katılımcıları arasında çalışmanıza yardımcı olur.

Her bölüm bu çözümde ayrı bir makaleye karşılık geldi.

![Tablodaki ayrıntıların yer alan dağıtım aşamaları resmi.](images/deployment-guide-phases.png)


![Dağıtım aşamalarının özeti: hazırlama, kurulum, ekleme.](images/phase-diagrams/deployment-phases.png)

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

Uç Nokta için Microsoft Defender birçok özellik sağlarken, bu dağıtım kılavuzunun birincil amacı, ekleme cihazlarıyla çalışmaya başlamanızı sağlar. Bu kılavuz, eklemeye ek olarak aşağıdaki özelliklerle başlamana da yardımcı olur.

<br>

****

|Özellik|Açıklama|
|---|---|
|Uç nokta algılama ve yanıt|Uç nokta algılama ve yanıt özellikleri izinsiz giriş girişimlerini ve etkin ihlalleri algılamak, araştırmak ve yanıtlamak için kullanılır.|
|Yeni nesil koruma|Ağın güvenlik çevresini daha da güçlendirmek için, Uç Nokta için Microsoft Defender yeni nesil koruma kullanarak ortaya çıkan her türlü tehdityi yakalayacak şekilde tasarlanmıştır.|
|Saldırı yüzeyini azaltma|Yığında ilk savunma hattını sağla. Yapılandırma ayarlarının doğru bir şekilde ayarlanmış olması ve açıktan yararlanma azaltma tekniklerinin uygulanmasıyla, bu özellikler saldırılara ve sömürüye karşı karşı koyar.|
|

Tüm bu özellikler Uç nokta lisans sahipleri için Microsoft Defender'da kullanılabilir. Daha fazla bilgi için Lisans [gereksinimleri'ne bakın](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Kapsam

### <a name="in-scope"></a>Kapsamda

- Uç noktaları hizmete ekleme ve özellikleri yapılandırma için Microsoft Endpoint Manager ve Microsoft Endpoint Configuration Manager'ın Kullanımı
- Uç nokta algılama ve yanıt (EDR) özellikleri için Defender'ı etkinleştirme
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
