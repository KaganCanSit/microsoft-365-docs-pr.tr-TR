---
title: Gelişmiş av şemasında AlertEvidence tablosu
description: Gelişmiş av şemasının AlertEvidence tablosunda uyarılar ile ilgili bilgiler hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, UyarıBilgileri, uyarı, varlıklar, kanıt, dosya, IP adresi, cihaz, makine, kullanıcı, hesap
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
ms.openlocfilehash: 9d7fc7e757b15c3682368cbd6c41b32c18724422
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019004"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Gelişmiş `AlertEvidence` arama şemasında [](advanced-hunting-overview.md) yer alan tablo, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender uyarılarında ilişkilendirilmiş dosyalar, IP adresleri, URL'ler, kullanıcılar veya cihazlar gibi çeşitli varlıklar hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `AlertId` | `string` | Uyarı için benzersiz tanımlayıcı |
| `ServiceSource` | `string` | Uyarı bilgilerini sağlanan ürün veya hizmet |
| `EntityType` | `string` | Dosya, süreç, cihaz veya kullanıcı gibi nesne türü |
| `EvidenceRole` | `string` | Varlığın etkide olup olmadığını veya yalnızca ilgili olduğunu belirten uyarıya nasıl dahil olduğu |
| `EvidenceDirection` | `string` | Varlığın ağ bağlantısının kaynağı mı yoksa hedefi mi olduğunu gösterir |
| `FileName` | `string` | Kaydedilen eylemin uygulandığı dosyanın adı |
| `FolderPath` | `string` | Kaydedilen eylemin uygulandığı dosyayı içeren klasör |
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `SHA256` | `string` | Kayıtlı eylemin uygulandığı dosyanın SHA-256'sı. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `FileSize` | `int` | Dosyanın bayt cinsinden boyutu |
| `ThreatFamily` | `string` | Şüpheli veya kötü amaçlı dosya ya da sürecin aşağıdakiler altında sınıflandırılmış kötü amaçlı yazılım ailesi |
| `RemoteIP` | `string` | Bağlantının olduğu IP adresi |
| `RemoteUrl` | `string` | Bağlanan URL veya tam etki alanı adı (FQDN) |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `AccountObjectId` | `string` | Hesap için benzersiz bir tanımlayıcı Azure Active Directory |
| `AccountUpn` | `string` | Hesabın kullanıcı asıl adı (UPN) |
| `DeviceId` | `string` | Hizmette cihaz için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `LocalIP` | `string` | İletişim sırasında kullanılan yerel cihaza atanan IP adresi |
| `NetworkMessageId` | `string` | Kullanıcı tarafından oluşturulan e-posta için benzersiz Office 365 |
| `EmailSubject` | `string` | E-postanın konusu |
| `ApplicationId` | `string` | Uygulamanın benzersiz tanımlayıcısı |
| `Application` | `string` | Kaydedilen eylemi gerçekleştiren uygulama |
| `ProcessCommandLine` | `string` | Yeni işlemi oluşturmak için kullanılan komut satırı |
| `AdditionalFields` | `string` | JSON dizi biçimindeki olay hakkında ek bilgi |
| `RegistryKey` |`string` | Kaydedilen eylemin uygulandığı kayıt defteri anahtarı |
| `RegistryValueName` |`string` | Kaydedilen eylemin uygulandığı kayıt defteri değerinin adı |
| `RegistryValueData` |`string` | Kayıtlı eylemin uygulandığı kayıt defteri değerinin verileri |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
