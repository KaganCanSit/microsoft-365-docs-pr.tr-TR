---
title: Microsoft 365 Defender'ta gelişmiş kotalar ve kullanım parametreleri
description: Gelişmiş av hizmetinin yanıt veren çeşitli kotalarını ve kullanım parametrelerini (hizmet sınırları) anlama
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema, kusto, CPU sınırı, sorgu sınırı, kaynaklar, en yüksek sonuç, kota, parametreler, ayırma
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fe0ad42ac0ebfc7f6816e412ab6ffb0ac9291b44
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989259"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Gelişmiş kotalar ve kullanım parametreleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Hizmet performansına ve hassas özelliklere sahip olmak için gelişmiş av, çeşitli kotaları ve kullanım parametrelerini ("hizmet sınırları" olarak da bilinir) ayarlar. Bu kotalar ve parametreler, el ile çalıştırılmaktadır ve sorgular özel algılama kuralları kullanılarak [çalıştırılmaktadır](custom-detection-rules.md). Düzenli olarak birden çok sorgu çalıştıran müşteriler bu sınırlara dikkat edin ve kesintileri en aza indirmek için [en iyi iyileştirme](advanced-hunting-best-practices.md) uygulamalarını uygulamalı.

Var olan kotaları ve kullanım parametrelerini anlamak için aşağıdaki tabloya bakın.

| Kota veya parametre | Boyut | Yenileme döngüsü | Açıklama |
|--|--|--|--|
| Veri aralığı | 30 gün | Her sorgu | Her sorgu, son 30 gün içinde yapılan verileri aramada 30 gün içinde olabilir. |
| Sonuç kümesi | 10.000 satır | Her sorgu | Her sorgu en çok 10.000 kayıt geri dönecektir. |
| Zaman Aşımı | 10 dakika | Her sorgu | Her sorgu en çok 10 dakika çalıştırabilirsiniz. 10 dakika içinde tamamlanmazsa, hizmet bir hata görüntüler.
| CPU kaynakları | Kiracı boyutuna göre | Her 15 dakikada bir | Portal [, bir sorgu çalıştırildiğinde](advanced-hunting-errors.md) ve kiracı ayrılan kaynakların %10'undan fazlasını tüketmesi sırasında hata görüntüler. Kiracı sonraki 15 dakikalık döngüye kadar %100 oranına ulaştı ise, sorgular engellenir. |

>[!NOTE] 
>API aracılığıyla gerçekleştirilen gelişmiş av sorgularına ayrı bir kota ve parametre kümesi uygulanır. [Gelişmiş av API'leri hakkında bilgi](./api-advanced-hunting.md)

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş arama için en iyi yöntemler](advanced-hunting-best-practices.md)
- [Gelişmiş av hatalarını işleme](advanced-hunting-errors.md)
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Özel algılamalara genel bakış](custom-detections-overview.md)