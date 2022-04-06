---
title: İstenmeyen posta güven düzeyi
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
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) gönderilen iletilere uygulanan istenmeyen posta güven Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7783eb0655a6e3b0457a45057b920c87388e4c05
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682933"
---
# <a name="spam-confidence-level-scl-in-eop"></a>EOP'de istenmeyen posta güven düzeyi (SCL)

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu Exchange Online olan kuruluşlarda, gelen iletiler EOP'de istenmeyen posta filtrelemesi yoluyla gider ve istenmeyen posta puanı atanır. Bu puan, bir X üstbilgisinde iletiye eklenen tek bir istenmeyen posta güven düzeyine (SCL) eşlenmiştir. Daha yüksek bir SCL, bir iletinin istenmeyen posta olma olasılığı daha yüksek olduğunu gösterir. EOP, SCL'ye dayalı olarak ileti üzerinde eylem gerçektir.

SCL'nin anlamı ve iletilere  alınan varsayılan eylemler aşağıdaki tabloda açıklanmıştır. İstenmeyen posta filtreleme kararını temel alarak iletiler üzerinde gerçekleştirebilirsiniz işlemler hakkında daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

|SCL|Tanım|Varsayılan eylem|
|:---:|---|---|
|-1|İleti istenmeyen posta filtrelemeyi atlandı. Örneğin, ileti güvenilir gönderenden gönderilmiş, güvenilir alıcıya gönderilmiş veya IP İzin Listesi'nin bir e-posta kaynağı sunucusundan gönderilmiş olabilir. Daha fazla bilgi için bkz [. EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).|İletiyi alıcıların gelen kutusunda teslim edin.|
|0, 1|İstenmeyen posta filtreleme, iletinin istenmeyen posta olmadığını belirledi.|İletiyi alıcıların gelen kutusunda teslim edin.|
|5, 6|İletiyi İstenmeyen Posta olarak işaretlenen istenmeyen posta **filtreleme**|İletiyi alıcıların Gereksiz E-posta klasörüne teslim edin.|
|9|İletiyi Yüksek güvene sahip istenmeyen posta olarak **işaretlenen istenmeyen posta filtresi**|İletiyi alıcıların Gereksiz E-posta klasörüne teslim edin.|

İstenmeyen posta filtrelemesi tarafından SCL 2, 3, 4, 7 ve 8'in kullanılma olmadığını fark edin.

İletilerde SCL'ye damga yapmak için posta akış kurallarını (aktarım kuralları olarak da bilinir) kullanabilirsiniz. SCL'i ayarlamak için posta akış kuralı kullanırsanız, 5 veya 6 değerleri İstenmeyen Posta için istenmeyen posta filtreleme eylemlerini tetikler ve 7, 8 veya 9 değerleri de Yüksek güveni olan istenmeyen posta için istenmeyen posta filtreleme eylemlerini tetikler **.** Daha fazla bilgi için bkz [. İletilerde istenmeyen posta güven düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

SCL'ye benzer şekilde, toplu şikayet düzeyi de (BCL) hatalı toplu e-postaları (gri posta olarak da _bilinir) tanımlar_. Daha yüksek bir BCL, toplu posta iletisinin şikayet oluşturma olasılığı daha yüksek (ve bu nedenle istenmeyen posta olma olasılığı daha yüksek) olduğunu gösterir. İstenmeyen posta önleme ilkelerde BCL eşiğini yapılandırmış oluruz. Daha fazla bilgi için bkz. EOP'de istenmeyen posta önleme ilkelerini yapılandırma, EOP'de Toplu şikayet düzeyi [(BCL)](bulk-complaint-level-values.md) ve Gereksiz [e-posta ile toplu e-posta](configure-your-spam-filter-policies.md) arasındaki [fark nedir?](what-s-the-difference-between-junk-email-and-bulk-email.md)

****

![LinkedIn Learning kısa simgesi.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Yeni misiniz? Microsoft 365?** LinkedIn tarafından size Microsoft 365 yönetici ve **IT** profesyonelleri için ücretsiz görüntülü kursları Learning.
