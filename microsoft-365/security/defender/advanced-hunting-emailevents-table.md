---
title: Gelişmiş av şemasında EmailEvents tablosu
description: Gelişmiş av şemasının EmailEvents Microsoft 365 e-posta adresleriyle ilişkili etkinlikler hakkında bilgi edinin
keywords: gelişmiş av, tehdit dolandırıcılığı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, EmailEvents, ağ ileti kimliği, gönderen, alıcı, ek kimliği, ek adı, kötü amaçlı yazılım kararını, kimlik avı kararını, ek sayısı, bağlantı sayısı, URL sayısı
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
ms.openlocfilehash: baf6e8d6d896e31b5092f7d2b8948bb7771382bd
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019024"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Gelişmiş `EmailEvents` av şemasında [yer alan tablo](advanced-hunting-overview.md), bu şema için Microsoft Defender'da e-postaların işlemesi ile ilgili Office 365. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `NetworkMessageId` | `string` | E-posta için, kullanıcı tarafından oluşturulan benzersiz Microsoft 365 |
| `InternetMessageId` | `string` | Gönderen e-posta sistemi tarafından ayarlanmış e-posta için genele açık tanımlayıcı |
| `SenderMailFromAddress` | `string` | Zarf gönderen veya alıcı adresi olarak da bilinen MAIL FROM üst bilgisinde gönderen Return-Path adresi |
| `SenderFromAddress` | `string` | FROM üst bilgisinde gönderenin e-posta adresi; bu adres e-posta istemcilerinde e-posta alıcıları tarafından görülebilir |
| `SenderDisplayName` | `string` | Adres defteri içinde görüntülenen gönderenin adı, genellikle belirli veya ad, ilk harfi ve soyadı veya surname birleşimidir |
| `SenderObjectId` | `string` |Azure AD'de gönderenin hesabı için benzersiz tanımlayıcı |
| `SenderMailFromDomain` | `string` | Zarf gönderen veya alıcı adresi olarak da bilinen MAIL FROM üst bilgisinde gönderen Return-Path alanı |
| `SenderFromDomain` | `string` | FROM üst bilgisinde bulunan ve e-posta istemcilerinde e-posta alıcıları tarafından görülebilen Gönderen etki alanı |
| `SenderIPv4` | `string` | İletiyi iletirken algılanan en son posta sunucusunun IPv4 adresi |
| `SenderIPv6` | `string` | İletiyi iletirken algılanan en son posta sunucusunun IPv6 adresi |
| `RecipientEmailAddress` | `string` | Dağıtım listesi genişletidikten sonra alıcının e-posta adresi veya alıcının e-posta adresi |
| `RecipientObjectId` | `string` | Azure AD'de e-posta alıcısı için benzersiz tanımlayıcı |
| `Subject` | `string` | E-postanın konusu |
| `EmailClusterId` | `string` | İçeriklerinin durum çözümlemesi temel alarak kümelenmiş benzer e-posta grubunun tanımlayıcısı |
| `EmailDirection` | `string` | E-postanın ağınıza göre yönü: Gelen, Giden, Intra-org |
| `DeliveryAction` | `string` | E-postanın teslim eylemi: Teslim Edildi, Gereksiz, Engellendi veya Değiştirildi |
| `DeliveryLocation` | `string` | E-postanın teslim alındığı konum: Gelen Kutusu/Klasör, Şirket İçi/Dış, Gereksiz, Karantina, Başarısız Oldu, Bırakılan, Silinmiş öğeler |
| `ThreatTypes` | `string` | E-posta filtreleme yığınından alınan karar, e-postanın kötü amaçlı yazılım, kimlik avı veya diğer tehditlerden uzak olup olmadığı |
| `ThreatNames` | `string` |Kötü amaçlı yazılım veya bulunan diğer tehditlere yönelik algılama adı |
| `DetectionMethods` | `string` | Kötü amaçlı yazılımları, kimlik avını veya e-postada bulunan diğer tehditleri algılamak için kullanılan yöntemler |
| `ConfidenceLevel` | `string` | İstenmeyen veya kimlik avıyla ilgili kararların güven düzeylerinin listesi. İstenmeyen posta için bu sütun, e-postanın atlanmış olup olmadığını (-1), istenmeyen posta olmadığını (0,1) tespit eden veya kolay bir güvenle (5,6) istenmeyen posta olduğu bulunan veya yüksek güvenle istenmeyen posta olduğunu belirten (9) istenmeyen posta olduğunu belirten istenmeyen posta güven düzeyini (SCL) gösterir. Kimlik avı için, bu sütunda güven düzeyi "Yüksek" veya "Düşük" olup olmadığı görüntülenir. |
| `EmailAction` | `string` | Filtre kararlarına, ilkelere ve kullanıcı eylemlerine dayalı olarak e-posta üzerinde  alınan son eylem: İletiyi gereksiz posta klasörüne taşı, X üstbilgisi ekle, Konuyu değiştir, Yeniden yönlendir iletisi, İletiyi sil, karantinaya gönder, Hiçbir eylem gerçekleştir, Gizli ileti |
| `EmailActionPolicy` | `string` | Etkili olan eylem ilkesi: Antispam yüksek güven, Antispam, Antispam toplu posta, Antispam kimlik avı, Kimlik avı önleme etki alanı kimliğe bürünme, Kimlik avı önleme kullanıcı kimliğe bürünme, Kimlik avı önleme kimliğine bürünme, Kimlik avı önleme grafiği kimliğe bürünme, Kasa Ekleri, Enterprise Aktarım Kuralları (ETR) |
| `EmailActionPolicyGuid` | `string` | Son posta eyleminde karar alan ilke için benzersiz tanımlayıcı |
| `AttachmentCount` | `int` | E-postada ek sayısı |
| `UrlCount` | `int` | E-postaya eklenmiş URL'lerin sayısı |
| `EmailLanguage` | `string` | E-posta içeriğinin algılanan dili |
| `Connectors` | `string` | Kurumsal posta akışını ve e-postanın nasıl yönlendirildiklerini tanımlayan özel yönergeler |
| `OrgLevelAction` | `string` | E-postaya, kuruluş düzeyinde tanımlanan bir ilkeyle eşleşen yanıt olarak  alınan eylem |
| `OrgLevelPolicy` | `string` | E-postada  yapılan eylemi tetikleyen kuruluş ilkesi |
| `UserLevelAction` | `string` | E-postada, alıcı tarafından tanımlanan posta kutusu ilkesiyle eşleşmelere yanıt olarak  alınan eylem |
| `UserLevelPolicy` | `string` | E-postada  yapılan eylemi tetikleyen son kullanıcı posta kutusu ilkesi |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için, bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır. |
| `AuthenticationDetails` | `string` | DMARC, DKIM, SPF veya birden çok kimlik doğrulama türü birleşimi (CompAuth) gibi e-posta kimlik doğrulama protokollerinin geçiş veya başarısız kararlarının listesi |

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
