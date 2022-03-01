---
title: Gelişmiş av şemasında CloudAppEvents tablosu
description: Gelişmiş av şemasının CloudAppEvents tablosunda bulut uygulamaları ve hizmetlerinden etkinlikler hakkında bilgi edinin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, CloudAppEvents, Bulut Uygulamaları için Defender
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
ms.openlocfilehash: daed3fb87aab498cdf91247a59e48af685aed010
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "63019147"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender



Gelişmiş `CloudAppEvents` arama şemasında [yer alan](advanced-hunting-overview.md) tablo, Bulut Uygulamaları için Microsoft Defender kapsamındaki çeşitli bulut uygulamaları ve hizmetleri etkinlikleri hakkında bilgi içerir. Tam liste için, ele alan [Uygulamalar ve hizmetler'e atlayın](#apps-and-services-covered). Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın. 

>[!IMPORTANT]
>Bu tabloda önceden tabloda kullanılabilen bilgiler yer `AppFileEvents` alır. 7 Mart 2021'den başlayarak, `CloudAppEvents` bu tarihte ve bu tarihten sonra bulut hizmetlerinde dosyayla ilgili etkinliklerle ilgili olarak alan alan kullanıcıların bunun yerine tabloyu kullanmaları gerekir. <br><br>Tabloyu kullanmaya devaman sorgular ve özel algılama kuralları için arama `AppFileEvents` yapmaya ve bunları tabloyu kullanmak üzere düzenlemeye emin `CloudAppEvents` olun. Etkilenen sorguları dönüştürme konusunda daha fazla kılavuz, gelişmiş aramayla bulut uygulaması etkinlikleri genelinde [Hunt Microsoft 365 Defender bulunabilir](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).


Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `ApplicationId` | `string` | Uygulamanın benzersiz tanımlayıcısı |
| `AccountObjectId` | `string` | Hesap için benzersiz bir tanımlayıcı Azure Active Directory |
| `AccountId` | `string` | Bulut Uygulamaları için Microsoft Defender'da bulunan hesabın tanımlayıcısı. Kimlik Azure Active Directory, kullanıcı asıl adı veya başka tanımlayıcılar olabilir. |
| `AccountDisplayName` | `string` | Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir veya ad, ortadaki bir başlatma ve soyadı veya surname bileşimidir. |
| `IsAdminOperation` | `string` | Etkinliğin yönetici tarafından gerçekleştirip gerçekleştiril olmadığını gösterir |
| `DeviceType` | `string` | Amaç ve işlevlere dayalı olarak "Ağ cihazı", "İş istasyonu", "Sunucu", "Mobil", "Oyun konsolu" veya "Yazıcı" gibi cihaz türü | 
| `OSPlatform` | `string` | Cihazda çalışan işletim sisteminin platformu. Bu sütun, Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler dahil olmak üzere belirli işletim Windows gösterir. |
| `IPAddress` | `string` | Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi |
| `IsAnonymousProxy` | `string` | IP adresinin bilinen bir anonim ara sunucuya ait olup olmadığını gösterir |
| `CountryCode` | `string` | İstemci IP adresinin coğrafi olarak bulunduğu ülkeyi gösteren iki harfli kod |
| `City` | `string` | İstemci IP adresinin coğrafi olarak bulunduğu şehir |
| `Isp` | `string` | IP adresiyle ilişkilendirilmiş İnternet servis sağlayıcısı (ISS) |
| `UserAgent` | `string` | Web tarayıcısında veya başka bir istemci uygulamasından kullanıcı aracısı bilgileri |
| `ActivityType` | `string` | Olayı tetikleyen etkinlik türü |
| `ActivityObjects` | `dynamic` | Kaydedilen etkinlikte yer alan dosyalar veya klasörler gibi nesnelerin listesi |
| `ObjectName` | `string` | Kaydedilen eylemin uygulandığı nesnenin adı |
| `ObjectType` | `string` | Kayıtlı eylemin uygulandığı dosya veya klasör gibi nesnenin türü |
| `ObjectId` | `string` | Kaydedilen eylemin uygulandığı nesnenin benzersiz tanımlayıcısı |
| `ReportId` | `string` | Olay için benzersiz tanımlayıcı |
| `RawEventData` | `string` | JSON biçiminde kaynak uygulama veya hizmetten ham olay bilgileri |
| `AdditionalFields` | `dynamic` | Varlık veya olay hakkında ek bilgiler |
| `AccountType` | `string` | Genel rolünü ve Normal, Sistem, Yönetici, DcAdmin, Sistem, Uygulama gibi erişim düzeylerini gösteren kullanıcı hesabı türü | 
| `IsExternalUser` | `boolean` | Ağ içindeki bir kullanıcının kuruluşun etki alanına ait olup olmadığını gösterir | 
| `IsImpersonated` | `boolean` | Etkinliğin, başka bir kullanıcı (kimliğine bürünülen) kullanıcı için bir kullanıcı tarafından gerçekleştirip gerçekleştiril olmadığını gösterir | 
| `IPTags` | `dynamic` | Belirli IP adreslerine ve IP adresi aralıklara uygulanan müşteri tanımlı bilgiler | 
| `IPCategory` | `string` | IP adresi hakkında ek bilgi | 
| `UserAgentTags` | `dynamic` | Kullanıcı aracısı alanında bir etikette Bulut Uygulamaları için Microsoft Defender tarafından sağlanan daha fazla bilgi. Şu değerlerden herhangi biri olabilir: Yerel istemci, Outdated tarayıcısı, Outdated işletim sistemi, Robot | 

## <a name="apps-and-services-covered"></a>Kaps altında olan uygulamalar ve hizmetler

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
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
