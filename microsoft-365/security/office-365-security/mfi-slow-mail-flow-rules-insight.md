---
title: Yavaş posta akışı kuralları içgörülerini düzeltme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, kuruluşlarında verimsiz veya bozuk posta akış kurallarını (aktarım kuralları olarak da bilinir) tanımlamak ve düzeltmek için Güvenlik & Uyumluluk Merkezi'nde Yavaş posta akışı kurallarını düzeltme içgörüsini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9866761e683e15d34d81b8ea0962d974b0b474da
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021800"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde posta akışı kurallarının yavaş & çözme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Verimsiz posta akış kuralları (aktarım kuralları olarak da bilinir), kurumda posta akışı gecikmelerine yol açabiliyor. Bu içgörü, kurum posta akışını etkileyen posta akışı kurallarını raporlar. Bu tür kurallara bazı örnekler verilmiştir:

- Kullanan koşullar **Büyük gruplar için** Üyedir.
- Karmaşık normal ifade (regex) desen eşleştirmesi kullanan koşullar.
- Eklerde içerik denetimi kullanan koşullar.

Güvenlik **ve Uyumluluk** Merkezi'nde Posta akışı panosunun Sizin için önerilenler alanında yer [](mail-flow-insights-v2.md) alan Yavaş posta akışı kurallarını [](https://protection.office.com) düzelt içgörüsörü, posta akış kuralının tamamlanmasının çok uzun zaman akar olduğunu size haber &.

Bu içgörü ancak koşul algılandığında görüntülenir (posta döngüleri yoksa, içgörüyü görmezsiniz).

Bu bildirimi, posta akışı gecikmelerini azaltmaya yardımcı olacak posta akış kurallarını tanımlamanıza ve ince ayarlamalarnıza yardımcı olacak şekilde kullanabilirsiniz.

![Posta akışı panosunun Sizin için önerilenler alanında yavaş posta akışı kuralları içgörülerini düzeltin.](../../media/mfi-fix-slow-mail-flow-rules.png)

Widget'ta **Ayrıntıları görüntüle'ye** tıklarken, daha fazla bilgiyle birlikte bir açılır pencere açılır:

- **Kural**: Tüm koşulları, özel durumları ve kuralın eylemlerini görmek için özetin üzerine gelin. Kuralı, genel yönetim merkezinde (EAC) düzenlemek Exchange için özete tıklarız<https://admin.exchange.microsoft.com/#/transportrules>.
- **Değerlendirilen ileti sayısı**: Kuraldan etkilenen iletilerden bir örneğin [ileti](message-trace-scc.md) izleme sonuçlarını görmek için Örnek iletileri görüntüle'yi tıklatın.
- **Her ileti için harcanan ortalama süre**
- **İletiye harcanan orta değer**: Üst kısmı zaman verilerinin alt yarısından ayıran orta değer.

![Yavaş posta akışı kurallarını düzeltme içgörüseği üzerinde Ayrıntıları görüntüle'ye tık olduktan sonra görüntülenen ayrıntılar açılır görünümü.](../../media/mfi-fix-slow-mail-flow-rules-details.png)

Posta akış kurallarında koşullar ve özel durumlar hakkında daha fazla bilgi için, bu konudaki Posta akışı kuralı koşulları ve özel durumları [(koşullar) Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).