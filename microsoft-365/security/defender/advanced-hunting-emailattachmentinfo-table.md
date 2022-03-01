---
title: Gelişmiş av şemasında EmailAttachmentInfo tablosu
description: Gelişmiş av şemasının EmailAttachmentInfo tablosunda e-posta eki bilgileri hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, EmailAttachmentInfo, ağ iletisi kimliği, gönderen, alıcı, ek kimliği, ek adı, kötü amaçlı yazılım kararlığı
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
ms.openlocfilehash: ac3e7aeff6778709f68aa1da74446cf55a1a6c06
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019011"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Gelişmiş `EmailAttachmentInfo` av şemasında [yer alan tablo](advanced-hunting-overview.md), ürün için Microsoft Defender tarafından işlenen e-postalarda yer alan Office 365. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `NetworkMessageId` | `string` | E-posta için, kullanıcı tarafından oluşturulan benzersiz Microsoft 365 |
| `SenderFromAddress` | `string` | FROM üst bilgisinde gönderenin e-posta adresi; bu adres e-posta istemcilerinde e-posta alıcıları tarafından görülebilir |
| `SenderDisplayName` | `string` | Adres defteri içinde görüntülenen gönderenin adı, genellikle belirli veya ad, ilk harfi ve soyadı veya surname birleşimidir |
| `SenderObjectId` | `string` | Azure AD'de gönderenin hesabı için benzersiz tanımlayıcı |
| `RecipientEmailAddress` | `string` | Dağıtım listesi genişletidikten sonra alıcının e-posta adresi veya alıcının e-posta adresi |
| `RecipientObjectId` | `string` | Azure AD'de e-posta alıcısı için benzersiz tanımlayıcı |
| `FileName` | `string` | Kaydedilen eylemin uygulandığı dosyanın adı |
| `FileType` | `string` | Dosya uzantısı türü |
| `SHA256` | `string` | Kayıtlı eylemin uygulandığı dosyanın SHA-256'sı. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `ThreatTypes` | `string` | E-posta filtreleme yığınından alınan karar, e-postanın kötü amaçlı yazılım, kimlik avı veya diğer tehditlerden uzak olup olmadığı |
| `ThreatNames` | `string` | Kötü amaçlı yazılım veya bulunan diğer tehditlere yönelik algılama adı |
| `DetectionMethods` | `string` | Kötü amaçlı yazılımları, kimlik avını veya e-postada bulunan diğer tehditleri algılamak için kullanılan yöntemler |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için, bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır. |
| `FileSize` | `string` | Dosyanın bayt cinsinden boyutu |

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
