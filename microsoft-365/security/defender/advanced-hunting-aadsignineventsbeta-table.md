---
title: Gelişmiş av şemasında AADSignInEventsBeta tablosu
description: Gelişmiş av Azure Active Directory oturum açma olayları tablosu hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, dosya, IP adresi, cihaz, makine, kullanıcı, hesap, kimlik, AAD
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
ms.openlocfilehash: dad3ea9fe4297d93864032130e3f6d6b5f6e4e82
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014053"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Tablo `AADSignInEventsBeta` şu anda beta sürümündedir ve Azure Active Directory (AAD) oturum açma etkinliklerini takip etmek için kısa vadeli olarak sunulmaktadır. Müşterilerin bu tablo için Azure Active Directory Premium P2 toplamak ve görüntülemek için bir lisansa sahip ihtiyaçları vardır. Tüm oturum açma şeması bilgileri zamanla tabloya `IdentityLogonEvents` taşınacak.

Gelişmiş `AADSignInEventsBeta` av şemasında yer alan tablo, Azure Active Directory etkileşimli olmayan oturum açma bilgileri içerir. Oturum açma etkinlik raporları - önizleme Azure Active Directory [oturum açma hakkında daha fazla bilgi edinin](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın. Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Sütun adı|Veri türü|Açıklama|
|---|---|---|
|`Timestamp`|`datetime`|Kaydın oluşturulma tarihi ve saati|
|`Application`|`string`|Kaydedilen eylemi gerçekleştiren uygulama|
|`ApplicationId`|`string`|Uygulamanın benzersiz tanımlayıcısı|
|`LogonType`|`string`|Oturum açma oturumunun, etkileşimli, uzak etkileşimli (RDP), ağ, toplu işlem ve hizmetin türü|
|`ErrorCode`|`int`|Oturum açma hatası oluşursa, hata kodunu içerir. Belirli bir hata kodunun açıklamasını bulmak için, ziyaret edin <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Oturum açma olayı için benzersiz tanımlayıcı|
|`SessionId`|`string`|Ziyaret veya oturum sırasında web sitesinin sunucusu tarafından kullanıcıya atanan benzersiz numara|
|`AccountDisplayName`|`string`|Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir adın veya adın, ilk adının baş harfinin ve soyadının veya surname'in bir bileşimidir.|
|`AccountObjectId`|`string`|Azure AD'de hesabın benzersiz tanımlayıcısı|
|`AccountUpn`|`string`|Hesabın kullanıcı asıl adı (UPN)|
|`IsExternalUser`|`int`|Oturum gösteren kullanıcının dış olup olduğunu gösterir. Olası değerler: -1 (ayarlanmaz), 0 (dış değil), 1 (dış).|
|`IsGuestUser`|`boolean`|Oturum gösteren kullanıcının kiracıda konuk olup olmadığını gösterir|
|`AlternateSignInName`|`string`|Azure AD'de oturum alan kullanıcının şirket içi kullanıcı asıl adı (UPN)|
|`LastPasswordChangeTimestamp`|`datetime`|Oturum anın son kez oturum alan kullanıcının parolasını değiştir olduğu tarih ve saat|
|`ResourceDisplayName`|`string`|Erişilen kaynağın görünen adı|
|`ResourceId`|`string`|Erişilen kaynağın benzersiz tanımlayıcısı|
|`ResourceTenantId`|`string`|Erişilen kaynağın kiracı benzersiz tanımlayıcısı|
|`DeviceName`|`string`|Makinenin tam etki alanı adı (FQDN)|
|`AadDeviceId`|`string`|Azure AD'de cihaz için benzersiz tanımlayıcı|
|`OSPlatform`|`string`|Makinede çalışan işletim sisteminin platformu. Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir.|
|`DeviceTrustType`|`string`|Oturum imzalanan cihazın güven türünü gösterir. Yalnızca yönetilen cihaz senaryoları için. Olası değerler Çalışma Alanı, AzureAd ve ServerAd'dır.|
|`IsManaged`|`int`|Oturum açmayı başlatan cihazın yönetilen bir cihaz (1) olup olmadığını gösterir (0)|
|`IsCompliant`|`int`|Oturum açma başlatan cihazın uyumlu (1) veya uyumlu olmayan (0) olup olmadığını gösterir|
|`AuthenticationProcessingDetails`|`string`|Kimlik doğrulama işlemcisi hakkında ayrıntılar|
|`AuthenticationRequirement`|`string`|Oturum açma için gereken kimlik doğrulama türü. Olası değerler: multiFactorAuthentication (MFA gereklidi) ve singleFactorAuthentication (MFA gerekmez).|
|`TokenIssuerType`|`int`|Belirteçyı alan kişi (0) Azure Active Directory Active Directory Federasyon Hizmetleri'nin mi (1) olduğunu gösterir|
|`RiskLevelAggregated`|`int`|Oturum açma sırasında toplanan risk düzeyi. Olası değerler: 0 (kümelenmiş risk düzeyi ayarlanmaz), 1 (yok), 10 (düşük), 50 (orta) veya 100 (yüksek).|
|`RiskDetails`|`int`|Oturum alıkan kullanıcının riskli durumu hakkında ayrıntılar|
|`RiskState`|`int`|Riskli kullanıcı durumunu gösterir. Olası değerler: 0 (yok), 1 (güvenli onaylandı), 2 (düzeltildi), 3 (reddedildi), 4 (risk altında) veya 5 (güvenliği ihlal edildi onaylandı).|
|`UserAgent`|`string`|Web tarayıcısında veya başka bir istemci uygulamasından kullanıcı aracısı bilgileri|
|`ClientAppUsed`|`string`|Kullanılan istemci uygulamasını gösterir|
|`Browser`|`string`|Oturum a açılırken kullanılan tarayıcı sürümü hakkında ayrıntılar|
|`ConditionalAccessPolicies`|`string`|Oturum açma olayına uygulanan koşullu erişim ilkelerinin ayrıntıları|
|`ConditionalAccessStatus`|`int`|Oturum açma için uygulanan koşullu erişim ilkelerinin durumu. Olası değerler 0 (uygulanan ilkeler), 1 (ilkeleri uygulama girişimi başarısız) veya 2 (ilke uygulanmadı) olabilir.|
|`IPAddress`|`string`|Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi|
|`Country`|`string`|İstemci IP adresinin coğrafi olarak bulunduğu ülkeyi gösteren iki harfli kod|
|`State`|`string`|Varsa, oturum açmanın nerede olduğunu haber vere|
|`City`|`string`|Hesap kullanıcıs 2007'nin bulunduğu şehir|
|`Latitude`|`string`|Oturum açma konumunun kuzeyden güneye koordinatları|
|`Longitude`|`string`|Oturum açma konumunun doğudan batıya koordinatları|
|`NetworkLocationDetails`|`string`|Oturum açma olayında kimlik doğrulama işlemcisinin ağ konumu ayrıntıları|
|`RequestId`|`string`|İsteğin benzersiz tanımlayıcısı|
|`ReportId`|`string`|Olay için benzersiz tanımlayıcı|

## <a name="related-articles"></a>İlgili makaleler

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [Gelişmiş ava genel bakış](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Sorgu dilini öğrenme](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Şemayı anlama](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
