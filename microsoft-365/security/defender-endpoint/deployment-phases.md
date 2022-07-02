---
title: Uç Nokta için Microsoft Defender dağıtımına genel bakış
description: Uç noktaları hazırlayarak, ayarlayarak ve bu hizmete ekleyerek Uç Nokta için Microsoft Defender dağıtmayı öğrenin
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
ms.openlocfilehash: 3520d249e7241eb1b890c3939fe6e6165d5c6011
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607619"
---
# <a name="microsoft-defender-for-endpoint-deployment-overview"></a>Uç Nokta için Microsoft Defender dağıtımına genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kuruluşunuzun önleyici koruma, ihlal sonrası algılama, otomatik araştırma ve yanıt avantajlarından yararlanabilmesi için Uç Nokta için Microsoft Defender dağıtmayı öğrenin.

Bu kılavuz, proje katılımcıları arasında çalışarak ortamınızı hazırlamanıza ve ardından cihazları değerlendirmeden anlamlı bir pilota ve tam dağıtıma geçerek yöntemli bir şekilde eklemenize yardımcı olur.

Her bölüm bu çözümdeki ayrı bir makaleye karşılık gelir.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Tablodan ayrıntıları içeren dağıtım aşamaları" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Dağıtım aşamalarının özeti: hazırlama, kurulum, ekleme" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Aşama|Açıklama|
|---|---|
|[Aşama 1: Hazırlık](prepare-deployment.md)|Paydaş onayları, ortam konuları, erişim izinleri ve özelliklerin benimseme sırası gibi Uç Nokta için Defender'ı dağıtırken dikkate almanız gerekenler hakkında bilgi edinin.|
|[Aşama 2: Kurulum](production-deployment.md)|Portala erişmek için uygulamanız gereken lisanslama, kurulum sihirbazını tamamlama ve ağ yapılandırması gibi ilk adımlarla ilgili rehberlik alın.|
|[Aşama 3: Katılım](onboarding.md)|Dağıtım halkalarını, uç nokta türüne göre desteklenen ekleme araçlarını kullanmayı ve kullanılabilir özellikleri yapılandırmayı öğrenin.|
|

Bu kılavuzu tamamladıktan sonra doğru erişim izinlerine sahip olacaksınız, uç noktalarınız eklenecek ve algılayıcı verilerini hizmete bildirecek ve yeni nesil koruma ve saldırı yüzeyini azaltma gibi özellikler sağlanacaktır.

[Plan dağıtımı](deployment-strategy.md) kılavuzunda özetlenen ortam mimarisinden ve dağıtım yönteminden bağımsız olarak, bu kılavuz ekleme uç noktalarını desteklemenizi sağlar.

## <a name="key-capabilities"></a>Önemli özellikler

Uç Nokta için Microsoft Defender birçok özellik sağlasa da, bu dağıtım kılavuzunun birincil amacı cihazları eklemeye başlamanızı sağlamaktır. Bu kılavuz, eklemeye ek olarak aşağıdaki özellikleri kullanmaya başlamanızı sağlar.

<br>

****

|Yeteneği|Açıklama|
|---|---|
|Uç nokta algılama ve yanıt|İzinsiz giriş girişimlerini ve etkin ihlalleri algılamak, araştırmak ve yanıtlamak için uç nokta algılama ve yanıt özellikleri devreye alınmaktadır.|
|Yeni nesil koruma|Ağınızın güvenlik çevresini daha da güçlendirmek için Uç Nokta için Microsoft Defender her türlü yeni tehdidi yakalamak için tasarlanmış yeni nesil korumayı kullanır.|
|Saldırı yüzeyini azaltma|Yığında ilk savunma hattını sağlayın. Yapılandırma ayarlarının düzgün ayarlandığından ve açıklardan yararlanma azaltma tekniklerinin uygulandığından emin olarak, bu özellikler saldırılara ve açıklardan yararlanmaya karşı dayanıklıdır.|
|

Tüm bu özellikler Uç Nokta için Microsoft Defender lisans sahipleri için kullanılabilir. Daha fazla bilgi için bkz [. Lisanslama gereksinimleri](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Kapsam

### <a name="in-scope"></a>Kapsamda

- Uç noktaları hizmete eklemek ve özellikleri yapılandırmak için Microsoft Endpoint Manager ve Microsoft Endpoint Configuration Manager kullanımı
- Uç nokta için Defender uç nokta algılama ve yanıt (EDR) özelliklerini etkinleştirme
- Uç nokta için Defender uç nokta koruma platformu (EPP) özelliklerini etkinleştirme
  - Yeni nesil koruma
  - Saldırı yüzeyini azaltma

### <a name="out-of-scope"></a>Kapsam dışı

Aşağıdakiler bu dağıtım kılavuzunun kapsamı dışındadır:

- Uç Nokta için Defender ile tümleştirebilecek üçüncü taraf çözümlerin yapılandırması
- Üretim ortamında sızma testi

## <a name="see-also"></a>Ayrıca bkz.

- [Aşama 1: Hazırlık](prepare-deployment.md)
- [Aşama 2: Kurulum](production-deployment.md)
- [Aşama 3: Katılım](onboarding.md)
- [Dağıtımınızı planlayın](deployment-strategy.md)
