---
title: Etki Alanı Anahtarları Tanımlanan Posta (DKIM) imzalı iletileri doğrulama desteği
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
description: Exchange Online Protection ve Exchange Online DKIM imzalı iletileri doğrulama hakkında bilgi edinin
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dcdd251ba1266033671ac524426d1ac3d2f56a10
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130724"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>DKIM imzalı iletileri doğrulama desteği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) ve Exchange Online her ikisi de Etki Alanı Anahtarları Tanımlanan Posta ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)) iletilerinin gelen doğrulamayı destekler.

DKIM, bir e-posta iletisinin başka biri tarafından *sahte* olmadığını ve geldiği *belirtilen* etki alanından gönderildiğini doğrular. E-posta iletisini gönderen kuruluşa bağlar. DKIM doğrulaması, IPv6 ile gönderilen tüm iletiler için otomatik olarak kullanılır. Microsoft 365, IPv4 üzerinden posta gönderildiğinde DKIM'ı da destekler. (IPv6 desteği hakkında daha fazla bilgi için bkz. [IPv6 üzerinden anonim gelen e-posta iletileri desteği](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

DKIM, ileti üst bilgilerinin DKIM-Signature üst bilgisinde görünen dijital olarak imzalanmış bir iletiyi doğrular. DKIM-Signature doğrulamanın sonuçları Authentication-Results üst bilgisinde damgalanır. İleti üst bilgisi metni aşağıdakine benzer görünür (burada contoso.com gönderendir):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Authentication-Results üst bilgisi hakkında daha fazla bilgi için bkz. RFC 7001 ([İleti Kimlik Doğrulama Durumunu Belirtmek için İleti Üst Bilgisi Alanı](https://www.rfc-editor.org/rfc/rfc7001.txt)). Microsoft'un DKIM uygulaması bu RFC ile uyumlu.

Yöneticiler DKIM doğrulamasının sonuçlarında Exchange [posta akışı kuralları](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (taşıma kuralları olarak da bilinir) oluşturabilir. Bu posta akışı kuralları, yöneticilerin iletileri gerektiği gibi filtrelemesine veya yönlendirmesine olanak tanır.
