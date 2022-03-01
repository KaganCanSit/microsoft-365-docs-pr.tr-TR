---
title: Gelişmiş av şemasında IdentityInfo tablosu
description: Gelişmiş av şemasının IdentityInfo tablosunda kullanıcı hesabı bilgileri hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, HesapBilgileri, IdentityInfo, hesap
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
ms.openlocfilehash: b09d1774ab35dbca9119deb98864d6c6f78051a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019020"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `IdentityInfo` arama [şemasında yer alan](advanced-hunting-overview.md) tablo, ürün şemaları dahil olmak üzere çeşitli hizmetlerden alınan kullanıcı hesapları Azure Active Directory. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!NOTE]
>Bu tablonun adı .`AccountInfo` Yeniden adlandırmalar sırasında portala kaydedilen tüm sorgular otomatik olarak güncelleştirilir. Başka bir yere kayıtlı sorguları kontrol edin.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `AccountObjectId` | `string` | Azure AD'de hesabın benzersiz tanımlayıcısı |
| `AccountUpn` | `string` | Hesabın kullanıcı asıl adı (UPN) |
| `OnPremSid` | `string` | Hesabın şirket içi güvenlik tanımlayıcısı (SID) |
| `CloudSid` | `string` | Hesabın bulut güvenlik tanımlayıcısı |
| `GivenName` | `string` | Hesap kullanıcı adının veya adının verildiği ad |
| `Surname` | `string` | Hesap kullanıcı adının soyadı, aile adı veya soyadı |
| `AccountDisplayName` | `string` | Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir veya ad, ortadaki bir başlatma ve soyadı veya surname bileşimidir. |
| `Department` | `string` | Hesap kullanıcısı tarafından ait olduğu departmanın adı |
| `JobTitle` | `string` | Hesap kullanıcılarının iş unvanı |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `EmailAddress` | `string` | Hesabın SMTP adresi |
| `SipProxyAddress` | `string` | Hesabın IP (VOIP) oturumları üzerinden ses (SIP) adresi |
| `City` | `string` | Hesap kullanıcıs 2007'nin bulunduğu şehir |
| `Country` | `string` | Hesap kullanıcıs ın bulunduğu Ülke/Bölge |
| `IsAccountEnabled` | `boolean` | Hesabın etkin olup olmadığını gösterir |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
