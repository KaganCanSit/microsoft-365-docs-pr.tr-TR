---
title: Office 365 için Microsoft Defender için gelişmiş Office 365
description: Gelişmiş avı kullanarak e-posta tehditlerini aramaya başlama
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 04e4fd2267cc3774e9a816539f0de044ae988dfb
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997081"
---
# <a name="advanced-hunting-example-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender için gelişmiş Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş avı kullanarak e-posta tehditlerini aramaya mı başladınız? Deneyebileceğiniz yöntem:

Bu [makalenin Microsoft](/microsoft-365/security/office-365-security/defender-for-office-365#getting-started) [Defender'ın Başlarken Office 365](/microsoft-365/security/office-365-security/defender-for-office-365), aşağıdaki gibi mantıksal erken yapılandırma öbekleri vardır:

1. Adı 'Anti' olan her şeyi yapılandır.
   - Kötü amaçlı yazılımdan koruma
   - Kimlik avı önleme
   - İstenmeyen posta önleme
2. Her şeyi, adı 'Kasa' ile ayarlayın.
   - Güvenli Bağlantılar
   - Kasa Ekleri Kaydetme
3. İş yüklerini savunma (örneğin. SharePoint Online, OneDrive ve Teams).
4. Sıfır Saatlik otomatik temizleme ile koruyun.

Doğrudan içine atlamak [ve](../office-365-security/protect-against-threats.md) 1. Gün'de yapılandırmaya devam etmek için bir bağlantıyla birlikte.

Başlarken'in **son adımı** , ZAP olarak da bilinen **Sıfır** Saatlik otomatik temizleme özelliğiyle kullanıcıları korumaktır. ŞÜPHELI veya kötü amaçlı bir e-postaYA ZAP uygulama çabalarınız başarılı olup olmadığını bilmek çok önemli olabilir.

Sorunları yakalamak için Hemen Kusto sorgu diline gitmek, bu iki güvenlik merkeziyle bir konuşmanın avantajıdır. Güvenlik ekipleri, burada, Gelişmiş Sındır'ın altında [ZAP'ın](https://security.microsoft.com/advanced-hunting) kaçırılan **günlerini** \> **izleyebilir**.

1. Gelişmiş Av sayfasında Sorgu'ya **tıklayın**.
1. Aşağıdaki sorguyu sorgu penceresine kopyalayın.
1. Sorguyu **çalıştır'ı seçin**.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfullyconverge-2-endpoints-new.png
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

:::image type="content" source="../../media/ah-query-example-new.png" alt-text="Sorgu panelinin en üstünde Sorgu seçili olan ve son 7 gün içinde ZAP eylemlerini yakalamak için Bir Kusto sorgusu çalıştıran Gelişmiş av sayfası (Çınlama altında)." lightbox="../../media/ah-query-example-new.png":::

Bu sorgudan gelen veriler, sorgunun kendi altındaki sonuçlar panelinde gösterilir. Sonuçlar, özelleştirilebilir bir sonuç kümesinde 'DeviceName', 'AccountDisplayName' ve 'ZapTime' gibi bilgiler içerir. Kayıtlarınız için de sonuçlar dışarı aktarabilirsiniz. Sorgu yeniden ihtiyacınız olacaksa,  >  Farklı Kaydet'i seçin ve sorguyu sorgu, paylaşılan veya topluluk sorguları listenize ekleyin.

## <a name="related-information"></a>İlgili bilgiler
- [Gelişmiş arama için en iyi yöntemler](advanced-hunting-best-practices.md)
- [Genel Bakış - Gelişmiş av](advanced-hunting-overview.md)
