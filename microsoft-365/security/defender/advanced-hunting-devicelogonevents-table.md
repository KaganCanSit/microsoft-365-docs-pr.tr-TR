---
title: Gelişmiş av şemasında DeviceLogonEvents tablosu
description: Gelişmiş av şemasının DeviceLogonEvents tablosunda kimlik doğrulama veya oturum açma olayları hakkında bilgi edinebilirsiniz
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, oturum açma olayları, DeviceLogonEvents, kimlik doğrulama, oturum açma, oturum açma
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
ms.openlocfilehash: dbafb4c967bca09195277aa4c79c95dd1dc87afb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018896"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender



Gelişmiş `DeviceLogonEvents` arama şemasında [yer alan tablo](advanced-hunting-overview.md) , cihazlardaki kullanıcı oturum açma bilgileri ve diğer kimlik doğrulama olayları hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `ActionType` | `string` |Olayı tetikleyen etkinlik türü |
| `LogonType` | `string` | Özellikle oturum açma oturumunun türü:<br><br> - **Etkileşimli** - Kullanıcı yerel klavye ve ekranı kullanarak makineyle fiziksel olarak etkileşim sağlar<br><br> - **Uzaktan etkileşimli (RDP) oturum** açmaları - Kullanıcı Uzak Masaüstü, Terminal Hizmetleri, Uzaktan Yardım veya diğer RDP istemcilerini kullanarak makineyle uzaktan etkileşim sağlar<br><br> - **Ağ** - Makineye PsExec kullanılarak erişilirken veya makinede yazıcılar ve paylaşılan klasörler gibi paylaşılan kaynaklara erişilirken başlatılan oturuma erişilir<br><br> - **Toplu** işlem - Zamanlanmış görevler tarafından başlatılan oturum<br><br> - **Hizmet** - Hizmetler tarafından başlatılan ve başlatılan oturum<br> |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `Protocol` | `string` | İletişim sırasında kullanılan protokol |
| `FailureReason` | `string` | Kaydedilen eylemin neden başarısız olduğunu açıklayan bilgiler |
| `IsLocalAdmin` | `boolean` | Kullanıcının makinede yerel yönetici olup olmadığının Boole göstergesi |
| `LogonId` | `string` | Oturum açma oturumu için tanımlayıcı. Bu tanımlayıcı aynı makinede yalnızca yeniden başlatmalar arasında benzersizdir |
| `RemoteDeviceName` | `string` | Etkilenen makinede uzaktan işlem gerçekleştirilen makinenin adı. Bildirilen etkinliğe bağlı olarak, bu ad tam etki alanı adı (FQDN), Net BIR ADı veya etki alanı bilgisi olmayan bir ana bilgisayar adı olabilir |
| `RemoteIP` | `string` | Bağlantının olduğu IP adresi |
| `RemoteIPType` | `string` | GENEL, Özel, Özel, Loopback, Teredo, FourToSixMapping ve Broadcast gibi IP adresi türü |
| `RemotePort` | `int` | Bağlanılan uzak cihaz üzerinde TCP bağlantı noktası |
| `InitiatingProcessAccountDomain` | `string` | Etkinlikten sorumlu olan işlemi hesapta işlemden sorumlu olan etki alanı |
| `InitiatingProcessAccountName` | `string` | Etkinlikten sorumlu olan işlemi randayanın kullanıcı adı |
| `InitiatingProcessAccountSid` | `string` | Olaydan sorumlu olan işlemi hesapta bulunduran hesabın Güvenlik Tanımlayıcısı (SID) |
| `InitiatingProcessAccountUpn` | `string` | Etkinlikten sorumlu olan işlemi hesaptan sorumlu olan hesabın kullanıcı asıl adı (UPN) |
| ` InitiatingProcessAccountObjectId` | `string` | Olaydan sorumlu olan işlemi hesap hesaplarından sorumlu olan kullanıcı hesabının Azure AD nesne kimliği |
| `InitiatingProcessIntegrityLevel` | `string` | Olayı başlatan sürecin bütünlük düzeyi. Windows, İnternet indirmesi'den başlatıldılar gibi bazı özelliklere dayalı işlemlere bütünlük düzeyleri atar. Bu bütünlük düzeyleri kaynaklar üzerindeki izinleri etkiler |
| `InitiatingProcessTokenElevation` | `string` | Etkinliği başlatan işleme uygulanan Kullanıcı Erişim Denetimi (UAC) ayrıcalık yükseltmesi varlığını veya olmadığını belirten belirteç türü |
| `InitiatingProcessSHA1` | `string` | Olayı başlatan işlem (resim dosyası) SHA-1 |
| `InitiatingProcessSHA256` | `string` | Olayı başlatan işlem (resim dosyası) SHA-256. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın |
| `InitiatingProcessMD5` | `string` | Etkinliği başlatan işlem (resim dosyası) MD5 karması |
| `InitiatingProcessFileName` | `string` | Olayı başlatan sürecin adı |
| `InitiatingProcessFileSize` | `long` | Etkinlikten sorumlu olan işlemi randaen dosyanın boyutu |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden şirket adı |
| `InitiatingProcessVersionInfoProductName` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden ürün adı |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden gelen ürün sürümü |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden iç dosya adı |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden özgün dosya adı |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden açıklama |
| `InitiatingProcessId` | `int` | Olayı başlatan sürecin Süreç Kimliği (PID) |
| `InitiatingProcessCommandLine` | `string` | Olayı başlatan işlemi çalıştırmak için kullanılan komut satırı |
| `InitiatingProcessCreationTime` | `datetime` | Olayı başlatan sürecin başlatıldığı tarih ve saat |
| `InitiatingProcessFolderPath` | `string` | Olayı başlatan işlemi (resim dosyası) içeren klasör |
| `InitiatingProcessParentId` | `int` | Olaydan sorumlu olan işlemi bir diğer ana sürecin Süreç Kimliği (PID) |
| `InitiatingProcessParentFileName` | `string` | Etkinlikle ilgili olarak sorumlu olan işlemi bir ana sürecin adı |
| `InitiatingProcessParentCreationTime` | `datetime` | Etkinlikle ilgili olarak sorumlu olan sürecin üst öğesi başlat başlangıç tarihi ve saati |
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
