---
title: İstenmeyen posta güvenilirlik düzeyi
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
description: Yöneticiler, Exchange Online Protection (EOP) içindeki iletilere uygulanan istenmeyen posta güvenilirlik düzeyi (SCL) hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8febc1d0e0c4fd98b33fb0016beee89a30802241
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647919"
---
# <a name="spam-confidence-level-scl-in-eop"></a>EOP'de istenmeyen posta güvenilirlik düzeyi (SCL)

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, gelen iletiler EOP'de istenmeyen posta filtrelemeden geçer ve bir istenmeyen posta puanı atanır. Bu puan, X üst bilgisindeki iletiye eklenen tek bir istenmeyen posta güvenilirlik düzeyine (SCL) eşlenir. Daha yüksek bir SCL, iletinin istenmeyen posta olma olasılığının daha yüksek olduğunu gösterir. EOP, ileti üzerinde SCL'yi temel alarak işlem uygular.

SCL'nin anlamı ve iletilerde gerçekleştirilen varsayılan eylemler aşağıdaki tabloda açıklanmıştır. İstenmeyen posta filtreleme kararına göre iletilerde gerçekleştirebileceğiniz eylemler hakkında daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

|SCL|Tanım|Varsayılan eylem|
|:---:|---|---|
|-1|İleti istenmeyen posta filtrelemeyi atladı. Örneğin, ileti güvenilir bir gönderenden, güvenilir bir alıcıya gönderildi veya IP İzin Ver Listesi'nde bir e-posta kaynak sunucusundan geliyor. Daha fazla bilgi için bkz. [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).|İletiyi alıcıların gelen kutusuna teslim edin.|
|0, 1|İstenmeyen posta filtreleme, iletinin istenmeyen posta olmadığını belirledi.|İletiyi alıcıların gelen kutusuna teslim edin.|
|5, 6|İstenmeyen posta filtrelemesi iletiyi **İstenmeyen Posta** olarak işaretledi|İletiyi alıcıların Gereksiz E-posta klasörüne teslim edin.|
|9|İstenmeyen posta filtrelemesi iletiyi **Yüksek güvenilirlikli istenmeyen posta** olarak işaretledi|İletiyi alıcıların Gereksiz E-posta klasörüne teslim edin.|

SCL 2, 3, 4, 7 ve 8'in istenmeyen posta filtrelemesi tarafından kullanılmadığını fark edeceksiniz.

İletilerde SCL'yi damgalama amacıyla posta akışı kurallarını (taşıma kuralları olarak da bilinir) kullanabilirsiniz. SCL'yi ayarlamak için bir posta akışı kuralı kullanırsanız, 5 veya 6 değerleri **İstenmeyen Posta** için istenmeyen posta filtreleme eylemini tetikler ve 7, 8 veya 9 değerleri **yüksek güvenilirlikli istenmeyen posta** için istenmeyen posta filtreleme eylemini tetikler. Daha fazla bilgi için bkz. [İletilerde istenmeyen posta güvenilirlik düzeyini (SCL) ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

SCL'ye benzer şekilde, toplu şikayet düzeyi (BCL) hatalı toplu e-postayı ( _gri posta_ olarak da bilinir) tanımlar. Daha yüksek bir BCL, toplu posta iletisinin şikayet oluşturma olasılığının daha yüksek olduğunu gösterir (ve bu nedenle istenmeyen posta olma olasılığı daha yüksektir). İstenmeyen posta önleme ilkelerinde BCL eşiğini yapılandırabilirsiniz. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md), [EOP'de toplu şikayet düzeyi (BCL)](bulk-complaint-level-values.md) ve [Gereksiz e-posta ile toplu e-posta arasındaki fark nedir?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![LinkedIn Learning kısa simgesi.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Microsoft 365'da yeni misiniz?** LinkedIn Learning tarafından size getirilen **Microsoft 365 yöneticileri ve BT uzmanlarına** yönelik ücretsiz video kurslarını keşfedin.
