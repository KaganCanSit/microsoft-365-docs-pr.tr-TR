---
title: Daha büyük Microsoft 365 Defender XDR için Değerlendirme Ortamı oluşturma
description: Hangi XDR'nin Microsoft 365 Defender olduğunu öğrenin ve deneme lisanslarını etkinleştirerek Microsoft 365 Defender laboratuvarınızı veya pilot ortamınızı bulun. XDR siber güvenlik yolculuğuna buradan başlayabilir ve bu testi üretime nasıl başlayacağınızı öğren öğrenin.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/19/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 5b684a1ead5638a787413d7470cb103cbe55e7df
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775532"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Adım 1. Daha büyük Microsoft 365 Defender siber güvenlik için Değerlendirme Ortamı oluşturma

Bu sorunun çözümü, bu Microsoft Defender XDR kalan bölüm boyunca dağıtılacak adımlarda daha fazla bilgi edinebilirsiniz ve dağıtabilirsiniz:

- [Ortamı oluşturma](eval-create-eval-environment.md)
- Bu Microsoft XDR teknolojisinin her bir teknolojisini ayarlama veya öğrenme
    - [Kimlik için Microsoft Defender](eval-defender-identity-overview.md)
    - [Office için Microsoft Defender](eval-defender-office-365-overview.md)
    - [Uç Nokta için Microsoft Defender](eval-defender-endpoint-overview.md)
    - [Bulut Uygulamaları için Microsoft Defender](eval-defender-mcas-overview.md)
- [Bu XDR kullanarak araştırma ve yanıtlama](eval-defender-investigate-respond.md)
- [Deneme ortamını üretim ortamına tanıtma](eval-defender-promote-to-production.md)
- [Genel Bakış'a geri dön](eval-overview.md)

Bu dizide adımlar, Microsoft 365 Defender XDR'nin ardındaki kavramları öğrenmekten bunu inşa etmek ve değerlendirme ortamını üretime almaya kadar  uç bir çalışma sunar.

Bir sonraki adımı değerlendirmede yapmak için iki yaygın yol vardır. Bu seride, zaten bir üretim Microsoft 365 olduğu varsay Microsoft 365 geçerli ortamdaki deneme sürümü lisanslarını değerlendirmek için E5 deneme Microsoft 365 Defender *etkinleştireceksiniz*. Yerinde değerlendirme, değerlendirme süresi sona kadar lisans satın alımıyla tüm güvenlik yöntemlerini elde tutmanız için size zaman sağlar.

İkincisi de değerlendirme [amacıyla Microsoft 365 Defender test laboratuvarı ortamınızı](setup-m365deval.md) ayarlamaktır. Test ederken işletmeden birçok gerçek sinyalin olmadığını unutmayın.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Denemeyi değerlendirmek için E5 deneme lisanslarını Microsoft 365 Defender

1. Var olan kiracı yönetim Microsoft 365 oturum açın.
2. Gezinti **menüsünde Hizmet Satın** Alın'ı seçin.
3. Sayfayı aşağı kaydırarak Office 365'nin **altında Ayrıntılar** düğmesini Office 365 E5 seçin.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Microsoft 365 Defender portalında Ayrıntılar düğmesi" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. Ücretsiz **deneme bağlantısını başlat'ı** seçin.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Web portalında Ücretsiz denemeyi Microsoft 365 Defender düğmesi" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. İsteğinizi onaylayın ve Şimdi dene **düğmesine** tıklayın.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Web portalında Şimdi Microsoft 365 Defender düğmesi" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>Sonraki adıma gitme

[Identity için Microsoft 365 etkinleştirmeyi öğrenin](eval-defender-identity-overview.md)

Ya da Değerlendirme ve pilot değerlendirme [genel görünümüne Microsoft 365 Defender](eval-overview.md)
