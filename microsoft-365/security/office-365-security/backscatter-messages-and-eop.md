---
title: EOP'de geri geri yasla
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
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, Geri gerici ve Güvenlik Koruması (EOP) Microsoft Exchange Online bilgi bulabilirsiniz
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79a6dd1be6c33bdbfc3d87b834f231de7cd08a0c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986516"
---
# <a name="backscatter-in-eop"></a>EOP'de geri geri yasla

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Geri çıktı,* göndermediği iletiler için size gönderilen teslim edililmeyen raporlardır (NDR'ler veya geri dönen iletiler olarak da bilinir). Geri çıktı, iletilerinde istenmeyen posta gönderenlerin From adresini (veya P2 adresi olarak da bilinir) kimliklerini ( `5322.From` kimliklerini) göndermeleri nedeniyledir. İstenmeyen posta gönderenler genellikle, Gönderen adresi olarak gerçek e-posta adreslerini kullanarak iletilerine güven verir. İstenmeyen posta var olmayan bir alıcıya gönderilebilir, hedef e-posta sunucusu temelde NDR'de teslim edilemeyen iletiyi Gönderen adresinin sahte gönderenine geri göndermeniz için püf noktası kullanılır.

EOP, Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu olan Exchange Online kuruluşlarında, EOP bir NDR oluşturmadan şüpheli kaynaklardan gelen iletileri tanımlamak ve sessize bırakmak için her çabayı gösteriyor. Microsoft 365 Ancak, hizmette akan açık toplu e-postaya bağlı olarak, EOP'nin her zaman bunu ima etme olasılığı vardır.

Backscatterer.org geri çıktı göndermekten sorumlu olan e-posta sunucularının bir engelleme listesini (DNS engelleme listesi veya DNSBL olarak da bilinir) bulundurur ve EOP sunucuları bu listede görünebilir. Ancak kendi listelerinin istenmeyen posta gönderenler listesi Backscatterer.org, bu listelerin engellenenler listesinden kendi çıkarlarını kaldırmaya çalışmayız.

> [!TIP]
> Büyük Backscatterer.org e-posta hizmetleri neredeyse her zaman biraz geri Kasa, çünkü Bu web sitesi Reddetme<http://www.backscatterer.org/?target=usage> modu yerine Kasa modunda kullanılması önerilir.
