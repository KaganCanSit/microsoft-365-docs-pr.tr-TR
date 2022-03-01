---
title: Gelişmiş av şemasında AADSpnSignInEventsBeta tablosu
description: Kullanıcın hizmet sorumlusu ve Azure Active Directory oturum açma olayları tablosuyla ilişkili bilgiler hakkında bilgi edinebilirsiniz.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, UyarıBilgileri, uyarı, varlıklar, kanıt, dosya, IP adresi, cihaz, makine, kullanıcı, hesap, kimlik, AAD
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
ms.openlocfilehash: 77cf2d7b74dfc4ccea88661642579f5244e14089
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63016321"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Tablo `AADSpnSignInEventsBeta` şu anda beta sürümündedir ve Azure Active Directory (AAD) oturum açma etkinliklerini takip etmek için kısa vadeli olarak sunulmaktadır. Müşterilerin bu tablo için Azure Active Directory Premium P2 toplamak ve görüntülemek için bir lisansa sahip ihtiyaçları vardır. Microsoft sonunda tüm oturum açma şema bilgilerini tabloya `IdentityLogonEvents` taşıtır.

Gelişmiş `AADSpnSignInEventsBeta` arama şemasında yer alan tablo, hizmet sorumlusu Azure Active Directory ve yönetilen kimlik oturum açma bilgileri içerir. Oturum açma etkinlik raporları - önizlemede, farklı oturum [açma Azure Active Directory hakkında daha fazla bilgi edinsiniz](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Sütun adı|Veri türü|Açıklama|
|---|---|---|
|`Timestamp`|`datetime`|Kaydın oluşturulma tarihi ve saati|
|`Application`|`string`|Kaydedilen eylemi gerçekleştiren uygulama|
|`ApplicationId`|`string`|Uygulamanın benzersiz tanımlayıcısı|
|`IsManagedIdentity`|`boolean`|Oturum açmanın yönetilen kimlikle başlat olup olmadığını gösterir|
|`ErrorCode`|`int`|Oturum açma hatası oluşursa, hata kodunu içerir. Belirli bir hata kodunun açıklamasını bulmak için, ziyaret edin <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Oturum açma olayı için benzersiz tanımlayıcı|
|`ServicePrincipalName`|`string`|Oturum açma başlatan hizmet sorumlusun adı|
|`ServicePrincipalId`|`string`|Oturum açma başlatan hizmet sorumlusuna özel tanımlayıcı|
|`ResourceDisplayName`|`string`|Erişilen kaynağın görünen adı|
|`ResourceId`|`string`|Erişilen kaynağın benzersiz tanımlayıcısı|
|`ResourceTenantId`|`string`|Erişilen kaynağın kiracı benzersiz tanımlayıcısı|
|`IPAddress`|`string`|Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi|
|`Country`|`string`|İstemci IP adresinin coğrafi olarak bulunduğu ülkeyi gösteren iki harfli kod|
|`State`|`string`|Varsa, oturum açmanın nerede olduğunu haber vere|
|`City`|`string`|Hesap kullanıcıs 2007'nin bulunduğu şehir|
|`Latitude`|`string`|Oturum açma konumunun kuzeyden güneye koordinatları|
|`Longitude`|`string`|Oturum açma konumunun doğudan batıya koordinatları|
|`RequestId`|`string`|İsteğin benzersiz tanımlayıcısı|
|`ReportId`|`string`|Olay için benzersiz tanımlayıcı|
||||

## <a name="related-articles"></a>İlgili makaleler

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Gelişmiş ava genel bakış](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Sorgu dilini öğrenme](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Şemayı anlama](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
