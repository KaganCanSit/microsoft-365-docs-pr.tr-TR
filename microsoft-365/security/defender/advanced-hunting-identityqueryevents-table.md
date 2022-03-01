---
title: Gelişmiş av şemasında IdentityQueryEvents tablosu
description: Gelişmiş av şemasının IdentityQueryEvents tablosunda Active Directory sorgu olayları hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, IdentityQueryEvents, Azure AD, Active Directory, Kimlik için Microsoft Defender, kimlikler, LDAP sorguları
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
ms.openlocfilehash: 0b3c98b629d8984b984af3f3dba25a65ab7671e6
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019016"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `IdentityQueryEvents` arama [şemasında yer alan](advanced-hunting-overview.md) tablo, kullanıcılar, gruplar, cihazlar ve etki alanları gibi Active Directory nesneleri üzerinde gerçekleştirilen sorgular hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü. Ayrıntılar için [portal şeması başvurusuna](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) bakın |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `QueryType` | `string` | QueryGroup, QueryUser veya EnumerateUsers gibi sorgu türü |
| `QueryTarget` | `string` | Sorgulanan kullanıcının, grubun, cihazın, etki alanının veya diğer herhangi bir varlık türünün adı |
| `Query` | `string` | Sorguyu çalıştırmak için kullanılan dize |
| `Protocol` | `string` | İletişim sırasında kullanılan protokol |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountUpn` | `string` | Hesabın kullanıcı asıl adı (UPN) |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `AccountObjectId` | `string` | Azure AD'de hesabın benzersiz tanımlayıcısı |
| `AccountDisplayName` | `string` | Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir veya ad, ortadaki bir başlatma ve soyadı veya surname bileşimidir. |
| `DeviceName` | `string` | Uç noktanın tam etki alanı adı (FQDN) |
| `IPAddress` | `string` | Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi |
| `Port` | `string` | İletişim sırasında kullanılan TCP bağlantı noktası |
| `DestinationDeviceName` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın adı |
| `DestinationIPAddress` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın IP adresi |
| `DestinationPort` | `string` | İlgili ağ iletişimlerinin hedef bağlantı noktası |
| `TargetDeviceName` | `string` | Kaydedilen eylemin uygulandığı cihazın tam etki alanı adı (FQDN) |
| `TargetAccountUpn` | `string` | Kayıtlı eylemin uygulandığı hesabın kullanıcı asıl adı (UPN) |
| `TargetAccountDisplayName` | `string` | Kaydedilen eylemin uygulandığı hesabın görünen adı |
| `Location` | `string` | Etkinlikle ilişkilendirilmiş şehir, ülke veya başka bir coğrafi konum |
| `ReportId` | `long` | Olay için benzersiz tanımlayıcı |
| `AdditionalFields` | `string` | Varlık veya olay hakkında ek bilgiler |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
