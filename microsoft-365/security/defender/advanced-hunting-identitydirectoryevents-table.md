---
title: Gelişmiş av şemasında IdentityDirectoryEvents tablosu
description: Gelişmiş av şemasının IdentityDirectoryEvents tablosunda etki alanı denetleyicisi ve Active Directory olayları hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, IdentityDirectoryEvents, etki alanı denetleyicisi, Active Directory, Kimlik için Microsoft Defender, kimlikler
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
ms.openlocfilehash: b7d880e0865ebeaf09e40fc543abba37566d2081
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019043"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `IdentityDirectoryEvents` arama [şemasında,](advanced-hunting-overview.md) Active Directory (AD) çalıştıran bir şirket içi etki alanı denetleyicisini içeren olaylar yer alır. Bu tablo, parola değişiklikleri, parola süre sonu ve kullanıcı asıl adı (UPN) değişiklikleri gibi kimlikle ilgili çeşitli olayları yakalar. Ayrıca, görevlerin zamanlaması ve PowerShell etkinliği gibi etki alanı denetleyicisinde sistem olaylarını da yakalar. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü. Ayrıntılar için [portal şeması başvurusuna](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) bakın |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `TargetAccountUpn` | `string` | Kayıtlı eylemin uygulandığı hesabın kullanıcı asıl adı (UPN) |
| `TargetAccountDisplayName` | `string` | Kaydedilen eylemin uygulandığı hesabın görünen adı |
| `TargetDeviceName` | `string` | Kaydedilen eylemin uygulandığı cihazın tam etki alanı adı (FQDN) |
| `DestinationDeviceName` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın adı |
| `DestinationIPAddress` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın IP adresi |
| `DestinationPort` | `string` | Etkinliğin hedef bağlantı noktası |
| `Protocol` | `string` | İletişim sırasında kullanılan protokol |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountUpn` | `string` | Hesabın kullanıcı asıl adı (UPN) |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `AccountObjectId` | `string` | Hesap için benzersiz bir tanımlayıcı Azure Active Directory |
| `AccountDisplayName` | `string` | Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir veya ad, ortadaki bir başlatma ve soyadı veya surname bileşimidir. |
| `DeviceName` | `string` | Cihazın tam etki alanı adı (FQDN) |
| `IPAddress` | `string` | İletişim sırasında cihaza atanan IP adresi |
| `Port` | `string` | İletişim sırasında kullanılan TCP bağlantı noktası |
| `Location` | `string` | Etkinlikle ilişkilendirilmiş şehir, ülke veya başka bir coğrafi konum |
| `ISP` | `string` | IP adresiyle ilişkilendirilmiş İnternet servis sağlayıcısı |
| `ReportId` | `long` | Olay için benzersiz tanımlayıcı |
| `AdditionalFields` | `string` | Varlık veya olay hakkında ek bilgiler |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
