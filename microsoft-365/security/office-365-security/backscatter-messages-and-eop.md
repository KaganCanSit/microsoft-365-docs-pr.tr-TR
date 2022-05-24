---
title: EOP'de geri yansıma
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
description: Bu makalede Backscatter ve Microsoft Exchange Online Koruması (EOP) hakkında bilgi edineceksiniz
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d132ed56c02989987da9e0ce32e7d4593e85e651
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648227"
---
# <a name="backscatter-in-eop"></a>EOP'de geri yansıma

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Backscatter* , göndermediğiniz iletiler için aldığınız teslim dışı raporlardır (NDR'ler veya geri dönen iletiler olarak da bilinir). Backscatter, istenmeyen posta gönderenlerin iletilerinde Kimden adresini (veya P2 adresi olarak `5322.From` da bilinir) sahte hale getirmesinden (yanıltma) kaynaklanır. spam gönderenler genellikle iletilerine güvenilirlik sağlamak için Kimden adresi olarak gerçek e-posta adreslerini kullanır. Var olmayan bir alıcıya istenmeyen posta gönderildiğinde, hedef e-posta sunucusu temelde ndr'deki teslim edilemeyen iletiyi Kimden adresinde sahte gönderene döndürecek şekilde kandırılır.

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda EOP, NDR oluşturmadan şüpheli kaynaklardan gelen iletileri tanımlamak ve sessizce bırakmak için her çabayı gösterir. Ancak, hizmette akan büyük hacimli e-postaya bağlı olarak, EOP'nin istemeden geri ölçeklendirici gönderme olasılığı her zaman vardır.

Backscatterer.org, backscatter göndermekle sorumlu olan e-posta sunucularının blok listesini (DNS blok listesi veya DNSBL olarak da bilinir) tutar ve EOP sunucuları bu listede görünebilir. Ancak liste istenmeyen posta gönderenlerin listesi olmadığından kendimizi Backscatterer.org engelleme listesinden kaldırmaya çalışmıyoruz.

> [!TIP]
> Backscatterer.org web sitesi (<http://www.backscatterer.org/?target=usage>) büyük e-posta hizmetleri neredeyse her zaman bazı geri dönüşler gönderdiğinden, hizmetlerini Reddetme modu yerine Kasa modunda kullanmanızı önerir.
