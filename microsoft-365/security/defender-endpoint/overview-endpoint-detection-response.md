---
title: uç noktada algılama ve yanıtlama özelliklerine genel bakış
ms.reviewer: ''
description: Uç Nokta için Microsoft Defender'daki uç noktada algılama ve yanıtlama özellikleri hakkında bilgi edinin
keywords: Uç Nokta için Microsoft Defender, uç noktada algılama ve yanıtlama, yanıt, algılama, siber güvenlik, koruma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 78f05c9e366d2f8b4d5b4d7697961f0d702581f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438538"
---
# <a name="overview-of-endpoint-detection-and-response"></a>uç noktada algılama ve yanıtlama genel bakış

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planları 1 ve 2](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender uç noktada algılama ve yanıtlama özellikleri, neredeyse gerçek zamanlı ve eyleme dönüştürülebilir gelişmiş saldırı algılamaları sağlar. Güvenlik analistleri uyarıların önceliklerini etkili bir şekilde belirleyebilir, ihlal kapsamının tamamını görebilir ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirebilir.

Bir tehdit algılandığında, analistin araştırması için sistemde uyarılar oluşturulur. Aynı saldırı tekniklerine sahip veya aynı saldırgana atfedilen uyarılar _olay_ adı verilen bir varlıkta toplanır. Uyarıları bu şekilde toplama, analistlerin tehditleri topluca araştırmasını ve yanıtlamasını kolaylaştırır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

> [!IMPORTANT]
> [Uç Nokta Planı 1](defender-endpoint-plan-1.md) ve [İş için Microsoft Defender](../defender-business/mdb-overview.md) için Defender yalnızca aşağıdaki el ile yanıt eylemlerini içerir:
> - Antivirüs taraması başlat
> - Cihazı yalıtma
> - Dosyayı durdurma ve karantinaya al
> - Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme

"İhlal varsay" düşünce yapısından ilham alan Uç Nokta için Defender, davranışsal siber telemetri verilerini sürekli olarak toplar. Buna işlem bilgileri, ağ etkinlikleri, çekirdek ve bellek yöneticisine yönelik derin optik, kullanıcı oturum açma etkinlikleri, kayıt defteri ve dosya sistemi değişiklikleri ve diğerleri dahildir. Bilgiler altı ay boyunca depolanır ve analistin saldırının başlangıcına kadar zamanda geriye gitmesine olanak tanır. Analist daha sonra çeşitli görünümlerde özetleyebilir ve birden çok vektör aracılığıyla bir araştırmaya yaklaşabilir.

Yanıt özellikleri, etkilenen varlıklar üzerinde hareket ederek tehditleri hemen düzeltme gücü sağlar.

## <a name="related-topics"></a>İlgili konular

- [Güvenlik işlemleri panosu](security-operations-dashboard.md)
- [Olay sırası](view-incidents-queue.md)
- [Uyarı sırası](alerts-queue.md)
- [Cihazlar listesi](machines-view-overview.md)
