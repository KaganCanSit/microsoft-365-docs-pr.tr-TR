---
title: Etki Alanı Anahtarlarının Doğrulanması Için DestekTak edilen Posta (DKIM) imzalı iletiler
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: E-posta ve posta iletileri için DKIM Exchange Online Protection hakkında bilgi Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5ea98add5ebe860f756d645909366a1f5502832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988180"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>DKIM imzalı iletileri doğrulama desteği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) ve Exchange Online, Tanımlanan Etki Alanı Anahtarları ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)) iletilerinin gelen doğrulamasını destekler.

DKIM, e-posta mesajının başka biri tarafından  kimlikle gönderildiğini ve bu iletinin geldiği etki *alanından* gönderildiğini doğrular. E-posta iletisi, gönderilen kuruluşa bağlı. DKIM doğrulaması, IPv6 ile gönderilen tüm iletiler için otomatik olarak kullanılır. Microsoft 365 IPv4 üzerinden posta gönderildiği zaman DAM işlevini de destekler. (IPv6 desteği hakkında daha fazla bilgi için bkz. [IPv6 üzerinden anonim gelen e-posta iletileri desteği](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

DKIM, ileti üst bilgisinde görüntülenen dijital DKIM-Signature iletiyi doğrular. Geçerlilik DKIM-Signature, üst bilgide Authentication-Results damgalanır. İleti üst bilgisi metni aşağıdakine benzer görünür (burada contoso.com gönderendir):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Bu üst bilgi hakkında daha Authentication-Results için bkz. RFC 7001 (İleti Kimlik Doğrulama Durumunu Gösteren [İleti Üst Bilgisi Alanı](https://www.rfc-editor.org/rfc/rfc7001.txt). Microsoft'un DKIM uygulaması bu RFC ile uyumlu.

Yöneticiler DKIM Exchange [sonuçları üzerinde posta](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) akış kuralları (aktarım kuralları olarak da bilinir) oluşturabilir. Bu posta akış kuralları yöneticilerin iletileri gerektiğinde filtrelemesine veya yönlendirmesine olanak sağlar.