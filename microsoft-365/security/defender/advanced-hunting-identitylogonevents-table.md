---
title: Gelişmiş av şemasında IdentityLogonEvents tablosu
description: Gelişmiş av şemasının IdentityLogonEvents tablosunda Active Directory tarafından kaydedilen kimlik doğrulama olayları hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, IdentityLogonEvents, Azure AD, Active Directory, Kimlik için Microsoft Defender, kimlikler
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
ms.openlocfilehash: c5f8de4015ed8b031d3f228f29a6a0d63a57bf2a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019017"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `IdentityLogonEvents` arama şemasında [](advanced-hunting-overview.md) yer alan tablo, Kimlik için Microsoft Defender tarafından yakalanan şirket içi Active Directory'niz üzerinden 2013'te 2013'te 2007'ye kadar olan kimlik doğrulama etkinlikleri ve Bulut Uygulamaları için Microsoft Defender tarafından yakalanan Microsoft çevrimiçi hizmetleriyle ilgili kimlik doğrulama etkinlikleri hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

>[!NOTE]
>Bu tablo, Azure Active Directory ActiveSync ve diğer eski protokolleri kullanan özellikle etkileşimli oturum açma ve kimlik doğrulama etkinlikleri gibi Bulut Uygulamaları için Defender tarafından  izlenen oturum açma etkinliklerini (Azure AD) kapsar. Bu tabloda yer alan etkileşimli olmayan oturum açmalar, Azure AD denetim günlüğünde  bakabilirsiniz. [Bulut Uygulamaları için Defender'ı mobil cihaza bağlama hakkında daha fazla Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü. Ayrıntılar için [portal şeması başvurusuna](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) bakın |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `LogonType` | `string` | Özellikle oturum açma oturumunun türü:<br><br> - **Etkileşimli** - Kullanıcı yerel klavye ve ekranı kullanarak makineyle fiziksel olarak etkileşim sağlar<br><br> - **Uzaktan etkileşimli (RDP) oturum** açmaları - Kullanıcı Uzak Masaüstü, Terminal Hizmetleri, Uzaktan Yardım veya diğer RDP istemcilerini kullanarak makineyle uzaktan etkileşim sağlar<br><br> - **Ağ** - Makineye PsExec kullanılarak erişilirken veya makinede yazıcılar ve paylaşılan klasörler gibi paylaşılan kaynaklara erişilirken başlatılan oturuma erişilir<br><br> - **Toplu** işlem - Zamanlanmış görevler tarafından başlatılan oturum<br><br> - **Hizmet** - Hizmetler tarafından başlatılan ve başlatılan oturum |
| `Protocol` | `string` | Kullanılan ağ protokolü |
| `FailureReason` | `string` | Kaydedilen eylemin neden başarısız olduğunu açıklayan bilgiler |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountUpn` | `string` | Hesabın kullanıcı asıl adı (UPN) |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `AccountObjectId` | `string` | Azure AD'de hesabın benzersiz tanımlayıcısı |
| `AccountDisplayName` | `string` | Adres defteri'de görüntülenen hesap kullanıcı adı. Normalde, belirli bir veya ad, ortadaki bir başlatma ve soyadı veya surname bileşimidir. |
| `DeviceName` | `string` | Cihazın tam etki alanı adı (FQDN) |
| `DeviceType` | `string` | Cihaz türü |
| `OSPlatform` | `string` | Makinede çalışan işletim sisteminin platformu. Bu, Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `IPAddress` | `string` | Uç noktaya atanan ve ilgili ağ iletişimleri sırasında kullanılan IP adresi |
| `Port` | `string` | İletişim sırasında kullanılan TCP bağlantı noktası |
| `DestinationDeviceName` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın adı |
| `DestinationIPAddress` | `string` | Kaydedilen eylemi işlenen sunucu uygulamasını çalıştıran cihazın IP adresi |
| `DestinationPort` | `string` | İlgili ağ iletişimlerinin hedef bağlantı noktası |
| `TargetDeviceName` | `string` | Kaydedilen eylemin uygulandığı cihazın tam etki alanı adı (FQDN) |
| `TargetAccountDisplayName` | `string` | Kaydedilen eylemin uygulandığı hesabın görünen adı |
| `Location` | `string` | Etkinlikle ilişkilendirilmiş şehir, ülke veya başka bir coğrafi konum |
| `Isp` | `string` | Uç nokta IP adresiyle ilişkilendirilmiş İnternet servis sağlayıcısı (ISS) |
| `ReportId` | `long` | Olay için benzersiz tanımlayıcı |
| `AdditionalFields` | `string` | Varlık veya olay hakkında ek bilgiler |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
