---
title: Gelişmiş tehdit avcılığı şemasındaki CloudAppEvents tablosu
description: Gelişmiş tehdit avcılığı şemasının CloudAppEvents tablosunda bulut uygulamaları ve hizmetlerinden gelen olaylar hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, CloudAppEvents, Bulut için Defender Uygulamaları
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 77b4ebd42a8c105340d6d965380aa42b64ae6734
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664974"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

`CloudAppEvents` [Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) şemasındaki tablo, Microsoft Defender for Cloud Apps kapsamındaki çeşitli bulut uygulamaları ve hizmetlerindeki etkinlikler hakkında bilgi içerir. Tam liste için [kapsanan Uygulamalar ve hizmetler'e atlayın](#apps-and-services-covered). Bu tablodan bilgi döndüren sorgular oluşturmak için bu başvuruyu kullanın.

> [!IMPORTANT]
> Bu tablo, tabloda önceden kullanılabilir `AppFileEvents` olan bilgileri içerir. 7 Mart 2021'den itibaren, bu tarihte ve sonrasında bulut hizmetlerinde dosyayla ilgili etkinlikler aracılığıyla av yapan kullanıcılar tabloyu kullanmalıdır `CloudAppEvents` . <br><br>Tabloyu kullanmaya `AppFileEvents` devam eden sorguları ve özel algılama kurallarını aramayı ve tabloyu kullanmak üzere düzenlemeyi `CloudAppEvents` unutmayın. Etkilenen sorguları dönüştürme hakkında daha fazla kılavuz, [Microsoft 365 Defender gelişmiş avcılık ile bulut uygulaması etkinlikleri arasında avlanma](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857) bölümünde bulunabilir.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için [gelişmiş avcılık başvurusuna bakın](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Olayın kaydedilildiği tarih ve saat |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `ApplicationId` | `string` | Uygulama için benzersiz tanımlayıcı |
| `AccountObjectId` | `string` | Azure Active Directory'deki hesabın benzersiz tanımlayıcısı |
| `AccountId` | `string` | Microsoft Defender for Cloud Apps tarafından bulunan hesabın tanımlayıcısı. Azure Active Directory kimliği, kullanıcı asıl adı veya diğer tanımlayıcılar olabilir. |
| `AccountDisplayName` | `string` | Adres defterinde görüntülenen hesap kullanıcısının adı. Genellikle belirli bir adın veya adın, ikinci bir başlatmanın ve soyadının veya soyadının birleşimidir. |
| `IsAdminOperation` | `string` | Etkinliğin bir yönetici tarafından gerçekleştirilip gerçekleştirilmediğini gösterir |
| `DeviceType` | `string` | "Ağ cihazı", "İş İstasyonu", "Sunucu", "Mobil", "Oyun konsolu" veya "Yazıcı" gibi amaca ve işlevselliğe dayalı cihaz türü |
| `OSPlatform` | `string` | Cihazda çalışan işletim sisteminin platformu. Bu sütun, aynı ailedeki Windows 11, Windows 10 ve Windows 7 gibi varyasyonlar da dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `IPAddress` | `string` | Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi |
| `IsAnonymousProxy` | `string` | IP adresinin bilinen bir anonim ara sunucuya ait olup olmadığını gösterir |
| `CountryCode` | `string` | İstemci IP adresinin coğrafi olarak konumlandırıldığı ülkeyi gösteren iki harfli kod |
| `City` | `string` | İstemci IP adresinin coğrafi olarak konumlandırıldığı şehir |
| `Isp` | `string` | IP adresiyle ilişkilendirilmiş İnternet servis sağlayıcısı (ISS) |
| `UserAgent` | `string` | Web tarayıcısından veya diğer istemci uygulamasından kullanıcı aracısı bilgileri |
| `ActivityType` | `string` | Olayı tetikleyen etkinlik türü |
| `ActivityObjects` | `dynamic` | Kaydedilen etkinlikte yer alan dosyalar veya klasörler gibi nesnelerin listesi |
| `ObjectName` | `string` | Kaydedilen eylemin uygulandığı nesnenin adı |
| `ObjectType` | `string` | Kaydedilen eylemin uygulandığı dosya veya klasör gibi nesne türü |
| `ObjectId` | `string` | Kaydedilen eylemin uygulandığı nesnenin benzersiz tanımlayıcısı |
| `ReportId` | `string` | Olayın benzersiz tanımlayıcısı |
| `RawEventData` | `string` | JSON biçiminde kaynak uygulama veya hizmetten ham olay bilgileri |
| `AdditionalFields` | `dynamic` | Varlık veya olay hakkında ek bilgi |
| `AccountType` | `string` | Normal, Sistem, Yönetici, DcAdmin, Sistem, Uygulama gibi genel rolünü ve erişim düzeylerini gösteren kullanıcı hesabı türü |
| `IsExternalUser` | `boolean` | Ağ içindeki bir kullanıcının kuruluşun etki alanına ait olup olmadığını gösterir |
| `IsImpersonated` | `boolean` | Etkinliğin başka bir kullanıcı (kimliğine bürünülen) kullanıcı için gerçekleştirilip gerçekleştirilmediğini gösterir |
| `IPTags` | `dynamic` | Belirli IP adreslerine ve IP adresi aralıklarına uygulanan müşteri tanımlı bilgiler |
| `IPCategory` | `string` | IP adresi hakkında ek bilgi |
| `UserAgentTags` | `dynamic` | Kullanıcı aracısı alanındaki bir etikette Microsoft Defender for Cloud Apps tarafından sağlanan daha fazla bilgi. Aşağıdaki değerlerden herhangi birine sahip olabilir: Yerel istemci, Güncel olmayan tarayıcı, Eski işletim sistemi, Robot |

## <a name="apps-and-services-covered"></a>Kapsanan uygulamalar ve hizmetler

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive İş
- Power Automate
- Power BI
- SharePoint Online
- Skype Kurumsal
- Office 365
- Yammer

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
