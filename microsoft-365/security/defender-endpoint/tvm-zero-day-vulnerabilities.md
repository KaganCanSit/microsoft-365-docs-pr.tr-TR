---
title: Sıfır günlük güvenlik açıklarını azaltmak - Tehdit ve Güvenlik Açığı Yönetimi
description: Güvenlik açıklarını güvenlik açıkları aracılığıyla bulma ve bu güvenlik açıklarını Tehdit ve Güvenlik Açığı Yönetimi.
keywords: Uç Nokta için Microsoft Defender tvm sıfır gün güvenlik açıkları, TVM, tehdit & güvenlik açığı yönetimi, sıfır gün, 0 gün güvenlik açıklarını ortadan kaldırır, KORUMASıZ 0 gün güvenlik açıkları, korumasız VULNERABLE
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2de9f0a3a0d860b2513c8947a1fe92563b516444
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476609"
---
# <a name="mitigate-zero-day-vulnerabilities---threat-and-vulnerability-management"></a>Sıfır günlük güvenlik açıklarını azaltmak - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Sıfır günlük bir güvenlik açığı, resmi düzeltme eki veya güvenlik güncelleştirmesi yayımlanmayacak bir yazılım hatasıdır. Yazılım satıcısı bu güvenlik açığını fark edeebilir veya fark edemebilir ve bu riskle ilgili genel bilgi yoktur. Sıfır gün açıkları genellikle yüksek önem düzeyine sahiptir ve etkin bir şekilde açıklardan yararlanmaktadır.

Tehdit ve güvenlik açığı yönetimi, yalnızca hakkında bilgi edinen sıfır günlük güvenlik açıkları görüntüler.

## <a name="find-information-about-zero-day-vulnerabilities"></a>Sıfır günlük güvenlik açıkları hakkında bilgi bulma

Sıfır gün içinde bir güvenlik açığı bulunursa, güvenlik açığı bulunursa, bu güvenlik açığıyla ilgili bilgiler Microsoft 365 Defender.

> [!NOTE]
> 0 günlük güvenlik açığı özelliği şu anda yalnızca Windows kullanılabilir.

### <a name="threat-and-vulnerability-management-dashboard"></a>Tehdit ve güvenlik açığı yönetimi panosu

"En iyi güvenlik önerileri" kartında sıfır gün etiketiyle önerileri bulun.

:::image type="content" source="images/tvm-zero-day-top-security-recommendations.png" alt-text="Sıfır gün etiketiyle en iyi öneriler" lightbox="images/tvm-zero-day-top-security-recommendations.png":::

"En korumasız yazılım" kartında en önemli yazılımı, sıfır gün etiketiyle bulabilirsiniz.

:::image type="content" source="images/tvm-zero-day-top-software.png" alt-text="En korumasız yazılım, sıfır gün etiketiyle" lightbox="images/tvm-zero-day-top-software.png":::

### <a name="weaknesses-page"></a>Zayıf sayfa

Açıklama ve ayrıntılarla birlikte, sıfır gün olarak adlandırılmış güvenlik açığını da göz atabilirsiniz.

- Bu güvenlik açığına BIR DEMİ KIMLIĞI atanmışsa, YERİNATAN adının yanında sıfır günlük etiketin olduğunu görüyorsunuz.

- Bu güvenlik açığına 112 SAAT KODU atanmamışsa, bunu "TVM-XXXX-XXXX" gibi geçici bir iç ad altında bulabilirsiniz. Ad, resmi bir TEMSİ kimliği atandıktan sonra güncelleştirilir, ancak önceki iç ad yine aranabilir ve yan panelde bulunur.

:::image type="content" source="images/tvm-zero-day-weakness-name.png" alt-text="Alıkanlar sayfasındaki VELI-2020-17087 için sıfır gün örneği" lightbox="images/tvm-zero-day-weakness-name.png":::

### <a name="software-inventory-page"></a>Yazılım stoku sayfası

Sıfır gün etiketi olan yazılımları ara. Yalnızca sıfır gün açıkları olan yazılımları görmek için "sıfır gün" etiketine göre filtre kullanın.

:::image type="content" source="images/tvm-zero-day-software-inventory.png" alt-text="Yazılım stoku sayfasındaki Windows Server 2016 günlük iş günü örneği" lightbox="images/tvm-zero-day-software-inventory.png":::

### <a name="software-page"></a>Yazılım sayfası

Sıfır günlük güvenlik açığı tarafından etkilenen her yazılım için sıfır gün etiketine bakın.

:::image type="content" source="images/tvm-zero-day-software-page.png" alt-text="Yazılım sayfasına sıfır Windows Server 2016 örneği" lightbox="images/tvm-zero-day-software-page.png":::

### <a name="security-recommendations-page"></a>Güvenlik önerileri sayfası

Varsa geçici çözümler de dahil olmak üzere düzeltme ve risk azaltma seçenekleriyle ilgili açık önerileri görüntüye alın. Yalnızca sıfır gün açıkları olan güvenlik önerilerini görmek için "sıfır gün" etiketine göre filtre ekleyin.

Sıfır gün açıkları olan bir yazılım ve açıkları olan ek güvenlik açıkları varsa, tüm güvenlik açıkları hakkında bir öneriniz olur.

:::image type="content" source="images/tvm-zero-day-security-recommendation.png" alt-text="Güvenlik önerileri sayfasında Windows Server 2016 gün değeri örneği." lightbox="images/tvm-zero-day-security-recommendation.png":::

## <a name="addressing-zero-day-vulnerabilities"></a>Sıfır günlük güvenlik açıklarını ele alıyor

Güvenlik önerisi sayfasına gidin ve sıfır gün içinde bir öneri seçin. Bu yazılıma yönelik sıfır günlük güvenlik açıkları ve diğer güvenlik açıkları hakkında bilgilerle bir açılır.

Varsa, risk azaltma seçeneklerinin ve geçici çözümlerin bir bağlantısı vardır. Geçici çözümler, bir düzeltme eki veya güvenlik güncelleştirmesi dağıtılana kadar bu sıfır günlük güvenlik açığının neden olduğu riski azaltmaya yardımcı olabilir.

Düzeltme seçeneklerini açın ve dikkat türünü seçin. Bir güncelleştirme henüz yayınlanmamış olduğu için, sıfır günlük güvenlik açıkları için "dikkat gereken" bir düzeltme seçeneği önerilir. Son tarih seçesiniz, çünkü belirli bir eylem gerçekleştirecek bir eylem yoktur. Bu yazılım için düzeltme yapmak istediğiniz eski güvenlik açıkları varsa, "dikkat gerekiyor" düzeltme seçeneğini geçersiz kabilir ve "güncelleştir" seçeneğini seçebilirsiniz.

:::image type="content" source="images/tvm-zero-day-recommendation-flyout400.png" alt-text="Güvenlik önerileri sayfasında sıfır gün Windows Server 2016 flyout örneği" lightbox="images/tvm-zero-day-recommendation-flyout400.png":::

## <a name="track-zero-day-remediation-activities"></a>Sıfır günlük düzeltme etkinliklerini izleme

Düzeltme etkinliği Tehdit ve Güvenlik Açığı Yönetimi [için](tvm-remediation.md) Düzeltme Sayfasına gidin. "Dikkat gerekiyor" düzeltme seçeneğini tercih ettiyseniz, iz izdeleymiz gerçek bir eylem söz değilken ilerleme çubuğu, bilet durumu veya son tarih olmaz. Aynı kategorideki tüm etkinlik öğelerini görmek için, "yazılım güncelleştirmesi" veya "dikkat gerekiyor" gibi düzeltme türüne göre filtre atabilirsiniz.

## <a name="patching-zero-day-vulnerabilities"></a>Sıfır günlük güvenlik açıklarına düzeltme eki uygulama

Sıfır gün için bir düzeltme eki yayınlanır ve önerinin yanında "Sıfır gün için yeni güvenlik güncelleştirmesi" diyen mavi bir etiketle "Güncelleştir" önerisi değiştirilir. Artık sıfır gün olarak düşünmeyecek ve sıfır gün etiketi tüm sayfalardan kaldırılacak.

![Yeni düzeltme eki etiketiyle "Microsoft Windows 10 Güncelleştirme" önerisi.](images/tvm-zero-day-patch.jpg)

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Yazılım envanteri](tvm-software-inventory.md)
- [Kuruluşumda güvenlik açıkları](tvm-weaknesses.md)
