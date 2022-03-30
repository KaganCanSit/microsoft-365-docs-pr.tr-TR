---
title: Toplu şikayet düzeyi değerleri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Yöneticiler, EOP'de (EOP) kullanılan toplu şikayet düzeyi (BCL) Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c50ca25a355ca142e36c67d03fad42c3aa461a2
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679884"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>EOP'de toplu şikayet düzeyi (BCL)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP Exchange Online) kuruluşlarında, EOP toplu posta kutularından gelen iletilere toplu şikayet düzeyi (BCL) atar. BCL, X üstbilgisinde iletiye eklenir ve istenmeyen posta olarak iletileri tanımlamak için kullanılan istenmeyen posta güven düzeyine [(SCL)](spam-confidence-levels.md) benzer. Daha yüksek bir BCL, toplu bir iletinin şikayet oluşturma olasılığı daha yüksek (ve bu nedenle de istenmeyen posta olma olasılığı) olduğunu gösterir. Microsoft, toplu postayı tanımlamak ve uygun BCL'yi belirlemek için hem iç hem de üçüncü taraf kaynaklarını kullanır.

Toplu posta gönderenlerin gönderme desenleri, içerik oluşturma ve alıcı edinme uygulamalarında farklılık gösterir. İyi toplu postalar, abonelerine ilgili içeriği olan istenen iletiler gönderir. Bu iletiler alıcılardan birkaç şikayet oluşturmaz. Diğer toplu posta gönderenler, istenmeyen postalara çok benzeyen ve alıcılardan birçok şikayet oluşturan talep edilmemiş iletiler gönderir. Toplu postacıdan gelen iletiler, toplu posta veya gri posta olarak bilinir.

 İstenmeyen posta filtreleme,  iletileri BCL eşiğine (varsayılan değer veya sizin belirttiğiniz değer) göre Toplu e-posta olarak işaretler ve ileti üzerinde belirtilen eylemi alır (varsayılan eylem iletiyi alıcının Gereksiz E-posta klasörüne teslim eder). Daha fazla bilgi için bkz [. İstenmeyen](configure-your-spam-filter-policies.md) posta önleme ilkelerini yapılandırma [ve Gereksiz e-posta ile toplu e-posta arasındaki fark nedir?](what-s-the-difference-between-junk-email-and-bulk-email.md)

BCL eşikleri aşağıdaki tabloda açıklanmıştır.

|BCL|Açıklama|
|:---:|---|
|0|İleti toplu bir gönderenden değil.|
|1, 2, 3|İleti, birkaç şikayet oluşturan toplu bir gönderenden gelen bir iletidir.|
|4, 5, 6, 7<sup>\*</sup>|İleti, çok sayıda şikayet oluşturan toplu bir gönderenden gelir.|
|8, 9|İleti, çok fazla sayıda şikayet oluşturan toplu bir gönderenden gelen bir iletidir.|

<sup>\*</sup> Bu, istenmeyen posta önleme ilkelerde kullanılan varsayılan eşik değeridir.
