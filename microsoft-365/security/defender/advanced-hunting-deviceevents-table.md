---
title: Gelişmiş av şemasında DeviceEvents tablosu
description: Gelişmiş av şemasının çeşitli cihaz olayları (DeviceEvents) tablosunda virüsten koruma yazılımı, güvenlik duvarı ve diğer olay türleri hakkında bilgi edinebilirsiniz
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, güvenlik olayları, virüsten koruma, güvenlik duvarı, exploit guard, DeviceEvents
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
ms.openlocfilehash: 54eef2d828f9a236ae457769c8c4ff9ba429dac9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019002"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş av şemasında yer `DeviceEvents` alan çeşitli cihaz olayları veya tablo, [](advanced-hunting-overview.md) çeşitli olay türleri hakkında bilgi içerir; örneğin, güvenlik denetimleri tarafından tetiklenen, Windows Defender Virüsten Koruma ve exploit protection. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).


| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü. Ayrıntılar için [portal şeması başvurusuna](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) bakın |
| `FileName` | `string` | Kaydedilen eylemin uygulandığı dosyanın adı |
| `FolderPath` | `string` | Kaydedilen eylemin uygulandığı dosyayı içeren klasör |
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `SHA256` | `string` | Kayıtlı eylemin uygulandığı dosyanın SHA-256'sı. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `MD5` | `string` | Kaydedilen eylemin uygulandığı dosyanın MD5 karması |
| `FileSize` | `long` | Dosyanın bayt cinsinden boyutu |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `RemoteUrl` | `string` | Bağlanan URL veya tam etki alanı adı (FQDN) |
| `RemoteDeviceName` | `string` | Etkilenen makinede uzaktan işlem gerçekleştirilen makinenin adı. Bildirilen etkinliğe bağlı olarak, bu ad tam etki alanı adı (FQDN), Net DOMAIN adı veya etki alanı bilgisi olmayan bir ana bilgisayar adı olabilir |
| `ProcessId` | `int` | Yeni oluşturulan işlemin Süreç Kimliği (PID) |
| `ProcessCommandLine` | `string` | Yeni işlemi oluşturmak için kullanılan komut satırı |
| `ProcessCreationTime` | `datetime` | sürecin oluşturulmuş olduğu tarih ve saat |
| `ProcessTokenElevation` | `string` | Yeni oluşturulan işleme Kullanıcı Erişimi Denetimi (UAC) ayrıcalık yükseltmesi uygulandığını veya olmadığını belirten belirteç türü |
| `LogonId` | `string` | Oturum açma oturumu için tanımlayıcı. Bu tanımlayıcı aynı makinede yalnızca yeniden başlatmalar arasında benzersizdir |
| `RegistryKey` | `string` | Kaydedilen eylemin uygulandığı kayıt defteri anahtarı |
| `RegistryValueName` | `string` | Kaydedilen eylemin uygulandığı kayıt defteri değerinin adı |
| `RegistryValueData` | `string` | Kayıtlı eylemin uygulandığı kayıt defteri değerinin verileri |
| `RemoteIP` | `string` | Bağlantının olduğu IP adresi |
| `RemotePort` | `int` | Bağlanılan uzak cihaz üzerinde TCP bağlantı noktası |
| `LocalIP` | `string` | İletişim sırasında kullanılan yerel makineye atanan IP adresi |
| `LocalPort` | `int` | İletişim sırasında kullanılan yerel makinede TCP bağlantı noktası |
| `FileOriginUrl` | `string` | Dosyanın indirildikten bulunduğu URL |
| `FileOriginIP` | `string` | Dosyanın indirildikten sonra IP adresi |
| `InitiatingProcessSHA1` | `string` | Olayı başlatan işlem (resim dosyası) SHA-1 |
| `InitiatingProcessSHA256` | `string` | Olayı başlatan işlem (resim dosyası) SHA-256. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `InitiatingProcessMD5` | `string` | Etkinliği başlatan işlem (resim dosyası) MD5 karması |
| `InitiatingProcessFileName` | `string` | Olayı başlatan sürecin adı |
| `InitiatingProcessFileSize` | `long` | Etkinlikten sorumlu olan işlemi randaen dosyanın boyutu |
| `InitiatingProcessFolderPath` | `string` | Olayı başlatan işlemi (resim dosyası) içeren klasör |
| `InitiatingProcessId` | `int` | Olayı başlatan sürecin Süreç Kimliği (PID) |
| `InitiatingProcessCommandLine` | `string` | Olayı başlatan işlemi çalıştırmak için kullanılan komut satırı |
| `InitiatingProcessCreationTime` | `datetime` | Olayı başlatan sürecin başlatıldığı tarih ve saat |
| `InitiatingProcessAccountDomain` | `string` | Etkinlikten sorumlu olan işlemi hesapta işlemden sorumlu olan etki alanı |
| `InitiatingProcessAccountName` | `string` | Etkinlikten sorumlu olan işlemi randayanın kullanıcı adı |
| `InitiatingProcessAccountSid` | `string` | Olaydan sorumlu olan işlemi hesapta bulunduran hesabın Güvenlik Tanımlayıcısı (SID) |
| `InitiatingProcessAccountUpn` | `string` | Etkinlikten sorumlu olan işlemi hesaptan sorumlu olan hesabın kullanıcı asıl adı (UPN) |
| `InitiatingProcessAccountObjectId` | `string` | Olaydan sorumlu olan işlemi hesap hesaplarından sorumlu olan kullanıcı hesabının Azure AD nesne kimliği |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden şirket adı |
| `InitiatingProcessVersionInfoProductName` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden ürün adı |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden gelen ürün sürümü |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden iç dosya adı |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden özgün dosya adı |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden açıklama |
| `InitiatingProcessParentId` | `int` | Olaydan sorumlu olan işlemi bir diğer ana sürecin Süreç Kimliği (PID) |
| `InitiatingProcessParentFileName` | `string` | Etkinlikle ilgili olarak sorumlu olan işlemi bir ana sürecin adı |
| `InitiatingProcessParentCreationTime` | `datetime` | Etkinlikle ilgili olarak sorumlu olan sürecin üst öğesi başlat başlangıç tarihi ve saati |
| `InitiatingProcessLogonId` | `string` | Etkinliği başlatan işlem oturum açma oturumunun tanımlayıcısı. Bu tanımlayıcı aynı makinede yalnızca yeniden başlatmalar arasında benzersizdir |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır |
| `AppGuardContainerId` | `string` | Application Guard tarafından tarayıcı etkinliğini yalıtmak için kullanılan sanallaştırılmış kapsayıcının tanımlayıcısı |
| `AdditionalFields` | `string` | JSON dizi biçimindeki olay hakkında ek bilgi |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
