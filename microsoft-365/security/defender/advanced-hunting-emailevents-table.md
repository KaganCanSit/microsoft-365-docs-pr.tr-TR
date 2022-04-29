---
title: Gelişmiş tehdit avcılığı şemasındaki EmailEvents tablosu
description: Gelişmiş tehdit avcılığı şemasının EmailEvents tablosunda Microsoft 365 e-postalarla ilişkili olaylar hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, EmailEvents, ağ ileti kimliği, gönderen, alıcı, ek kimliği, ek adı, kötü amaçlı yazılım kararı, kimlik avı kararı, ek sayısı, bağlantı sayısı, URL sayısı
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
ms.openlocfilehash: b34ac5538a2c38261f7da0a0cd3a75452660ef6e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128815"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender
- Office 365 için Microsoft Defender

[Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) şemasındaki tablo, `EmailEvents` Office 365 için Microsoft Defender e-postaların işlenmesini içeren olaylar hakkında bilgi içerir. Bu tablodan bilgi döndüren sorgular oluşturmak için bu başvuruyu kullanın.

> [!TIP]
> Bir tablo tarafından desteklenen olay türleri (`ActionType`değerler) hakkında ayrıntılı bilgi için Bulut için Defender bulunan yerleşik şema başvurularını kullanın.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için [gelişmiş avcılık başvurusuna bakın](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Olayın kaydedilildiği tarih ve saat |
| `NetworkMessageId` | `string` | Microsoft 365 tarafından oluşturulan e-postanın benzersiz tanımlayıcısı |
| `InternetMessageId` | `string` | Gönderen e-posta sistemi tarafından ayarlanan e-posta için genel kullanıma yönelik tanımlayıcı |
| `SenderMailFromAddress` | `string` | POSTADAN üst bilgisindeki gönderen e-posta adresi; zarf göndereni veya Return-Path adresi olarak da bilinir |
| `SenderFromAddress` | `string` | KIMDEN üst bilgisindeki gönderen e-posta adresi, e-posta istemcilerindeki e-posta alıcıları tarafından görülebilir |
| `SenderDisplayName` | `string` | Adres defterinde görüntülenen gönderenin adı, genellikle verilen veya adın, ikinci bir adın ve soyadının veya soyadının birleşimidir |
| `SenderObjectId` | `string` |Azure AD'da gönderenin hesabının benzersiz tanımlayıcısı |
| `SenderMailFromDomain` | `string` | POSTADAN üst bilgisindeki gönderen etki alanı; zarf göndereni veya Return-Path adresi olarak da bilinir |
| `SenderFromDomain` | `string` | GÖNDEREN üst bilgisindeki gönderen etki alanı, e-posta istemcilerindeki e-posta alıcıları tarafından görülebilir |
| `SenderIPv4` | `string` | İletiyi aktaran son algılanan posta sunucusunun IPv4 adresi |
| `SenderIPv6` | `string` | İletiyi aktaran son algılanan posta sunucusunun IPv6 adresi |
| `RecipientEmailAddress` | `string` | Dağıtım listesi genişletildikten sonra alıcının e-posta adresi veya alıcının e-posta adresi |
| `RecipientObjectId` | `string` | Azure AD'de e-posta alıcısı için benzersiz tanımlayıcı |
| `Subject` | `string` | E-postanın konusu |
| `EmailClusterId` | `string` | İçeriğinin buluşsal analizine göre kümelenmiş benzer e-posta grubunun tanımlayıcısı |
| `EmailDirection` | `string` | E-postanın ağınıza göre yönü: Gelen, Giden, Kuruluş içi |
| `DeliveryAction` | `string` | E-postanın teslim eylemi: Teslim Edildi, Gereksiz, Engellendi veya Değiştirildi |
| `DeliveryLocation` | `string` | E-postanın teslim edildiği konum: Gelen Kutusu/Klasör, Şirket İçi/Dış, Gereksiz, Karantina, Başarısız, Bırakılan, Silinen öğeler |
| `ThreatTypes` | `string` | E-posta filtreleme yığınından, e-postanın kötü amaçlı yazılım, kimlik avı veya diğer tehditler içerip içermediğine ilişkin karar |
| `ThreatNames` | `string` |Bulunan kötü amaçlı yazılım veya diğer tehditler için algılama adı |
| `DetectionMethods` | `string` | E-postada bulunan kötü amaçlı yazılımları, kimlik avı veya diğer tehditleri algılamak için kullanılan yöntemler |
| `ConfidenceLevel` | `string` | İstenmeyen posta veya kimlik avı kararlarının güvenilirlik düzeylerinin listesi. İstenmeyen postalar için, bu sütun, e-postanın atlandığını (-1), istenmeyen posta (0,1), ılımlı güvenle istenmeyen posta (5,6) veya yüksek güvenle istenmeyen posta olarak bulunup bulunmadığını gösteren istenmeyen posta güvenilirlik düzeyini (SCL) gösterir (9). Kimlik avı için bu sütun güvenilirlik düzeyinin "Yüksek" mi yoksa "Düşük" mü olduğunu gösterir. |
| `EmailAction` | `string` | Filtre kararına, ilkelere ve kullanıcı eylemlerine göre e-postada gerçekleştirilen son eylem: İletiyi gereksiz posta klasörüne taşıma, X üst bilgisi ekle, Konuyu değiştir, Yeniden yönlendirme iletisi, İletiyi sil, karantinaya gönderme, Eylem yapılmamış, Gizli iletisi |
| `EmailActionPolicy` | `string` | Etkili olan eylem ilkesi: Antispam yüksek güvenilirlik, Antispam, Antispam toplu posta, Antispam kimlik avı, Kimlik avı önleme etki alanı kimliğe bürünme, Kimlik avı önleme kullanıcı kimliğine bürünme, Kimlik avına karşı koruma sahtekarlığı, Kimlik avı önleme grafı kimliğe bürünme, Kötü amaçlı yazılımdan koruma, Kasa Ekler, Enterprise Aktarım Kuralları (ETR) |
| `EmailActionPolicyGuid` | `string` | Son posta eylemini belirleyen ilkenin benzersiz tanımlayıcısı |
| `AttachmentCount` | `int` | E-postadaki eklerin sayısı |
| `UrlCount` | `int` | E-postadaki eklenmiş URL sayısı |
| `EmailLanguage` | `string` | E-posta içeriğinin dili algılandı |
| `Connectors` | `string` | Kurumsal posta akışını ve e-postanın nasıl yönlendirildiğini tanımlayan özel yönergeler |
| `OrgLevelAction` | `string` | E-postada, kuruluş düzeyinde tanımlanan ilkeyle eşleşmelere yanıt olarak gerçekleştirilen eylem |
| `OrgLevelPolicy` | `string` | E-postada gerçekleştirilen eylemi tetikleyen kuruluş ilkesi |
| `UserLevelAction` | `string` | Alıcı tarafından tanımlanan posta kutusu ilkesiyle eşleşmelere yanıt olarak e-postada gerçekleştirilen eylem |
| `UserLevelPolicy` | `string` | E-postada gerçekleştirilen eylemi tetikleyen son kullanıcı posta kutusu ilkesi |
| `ReportId` | `long` | Yinelenen sayacı temel alan olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütunun DeviceName ve Timestamp sütunlarıyla birlikte kullanılması gerekir. |
| `AuthenticationDetails` | `string` | DMARC, DKIM, SPF gibi e-posta kimlik doğrulama protokollerine göre veya birden çok kimlik doğrulama türünün (CompAuth) birleşimine göre geçiş veya başarısız kararların listesi |

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
