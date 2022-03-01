---
title: Gelişmiş av şemasında EmailPostDeliveryEvents tablosu
description: Gelişmiş av şemasının EmailPostDeliveryEvents tablosunda e-postalarda Microsoft 365 teslim sonrası eylemleri hakkında bilgi edinin
keywords: gelişmiş av, tehdit dolandırıcılığı, siber tehdit avı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, EmailPostDeliveryEvents, ağ ileti kimliği, gönderen, alıcı, ek kimliği, ek adı, kötü amaçlı yazılım kararını, kimlik avı kararlığı, ek sayısı, bağlantı sayısı, url sayısı
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
ms.openlocfilehash: 59d611ae89aeedf386cd0dcad5939a9510f0820e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018893"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `EmailPostDeliveryEvents` av şemasında [yer alan tablo](advanced-hunting-overview.md), kullanıcılar tarafından işlenen e-posta iletilerine teslim Microsoft 365. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Tek tek e-posta iletileri hakkında daha fazla bilgi almak için [`EmailEvents`](advanced-hunting-emailevents-table.md), ve [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)tabloları da kullanabilirsiniz [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) . Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `NetworkMessageId` | `string` | E-posta için, kullanıcı tarafından oluşturulan benzersiz Microsoft 365 |
| `InternetMessageId` | `string` | Gönderen e-posta sistemi tarafından ayarlanmış e-posta için genele açık tanımlayıcı |
| `Action` | `string` | Varlık üzerinde  alınan eylem |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü: El ile düzeltme, Kimlik Avı ZAP, Kötü Amaçlı Yazılım ZAP |
| `ActionTrigger` | `string` | Bir eylemin yönetici tarafından tetik isteyip olmadığını (el ile veya bekleyen otomatik bir eylemin onayı yoluyla) ya da ZAP veya Dinamik Teslim gibi özel bir mekanizma tarafından tetiklenen eylemi gösterir |
| `ActionResult` | `string` | Eylemin sonucu |
| `RecipientEmailAddress` | `string` | Dağıtım listesi genişletidikten sonra alıcının e-posta adresi veya alıcının e-posta adresi |
| `DeliveryLocation` | `string` | E-postanın teslim alındığı konum: Gelen Kutusu/Klasör, Şirket İçi/Dış, Gereksiz, Karantina, Başarısız Oldu, Bırakılan, Silinmiş öğeler |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için, bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır. |
| `ThreatTypes` | `string` | E-posta filtreleme yığınından alınan karar, e-postanın kötü amaçlı yazılım, kimlik avı veya diğer tehditlerden uzak olup olmadığı |
| `DetectionMethods` | `string` | Kötü amaçlı yazılımları, kimlik avını veya e-postada bulunan diğer tehditleri algılamak için kullanılan yöntemler |

## <a name="supported-event-types"></a>Desteklenen olay türleri
Bu tablo, aşağıdaki değerlere sahip olayları `ActionType` yakalar:

- **El ile düzeltme –** Yönetici, kullanıcı posta kutusuna teslim edildikten sonra e-posta ileti üzerinde el ile bir işlem yaptı. Bu, Tehdit Gezgini aracılığıyla el [ile yapılan](../office-365-security/threat-explorer.md) eylemleri veya otomatik soruşturma [ve yanıt (AIR) eylemleri onaylarını içerir](m365d-autoir-actions.md).
- **Kimlik Avı ZAP** – [Teslimden sonra kimlik avı e-postası](../office-365-security/zero-hour-auto-purge.md) üzerinde sıfır saatlik otomatik temizleme (ZAP) işlemi yaptı.
- **Kötü amaçlı yazılım ZAP** – Teslimden sonra kötü amaçlı yazılım içeren bir e-posta iletisinde sıfır saatlik otomatik temizleme (ZAP) işlemi yaptı.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
