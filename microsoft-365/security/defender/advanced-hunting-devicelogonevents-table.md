---
title: Gelişmiş tehdit avcılığı şemasında DeviceLogonEvents tablosu
description: Gelişmiş tehdit avcılığı şemasının DeviceLogonEvents tablosunda kimlik doğrulaması veya oturum açma olayları hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, logonevents, DeviceLogonEvents, kimlik doğrulaması, oturum açma, oturum açma
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
ms.openlocfilehash: 516b74eb8d1e62194718e0ad3234b3269e07fb83
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731383"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender



`DeviceLogonEvents` [Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) şemasındaki tablo, cihazlardaki kullanıcı oturum açma işlemleri ve diğer kimlik doğrulama olayları hakkında bilgi içerir. Bu tablodan bilgi döndüren sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Bir tablo tarafından desteklenen olay türleri (`ActionType`değerler) hakkında ayrıntılı bilgi için Bulut için Defender bulunan yerleşik şema başvurularını kullanın.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için [gelişmiş avcılık başvurusuna bakın](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Olayın kaydedilildiği tarih ve saat |
| `DeviceId` | `string` | Hizmetteki makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `ActionType` | `string` |Olayı tetikleyen etkinlik türü |
| `LogonType` | `string` | Özellikle oturum açma oturumunun türü:<br><br> - **Etkileşimli** - Kullanıcı yerel klavyeyi ve ekranı kullanarak makineyle fiziksel olarak etkileşim kurar<br><br> - **Uzaktan etkileşimli (RDP) oturum açmalar** - Kullanıcı Uzak Masaüstü, Terminal Hizmetleri, Uzaktan Yardım veya diğer RDP istemcilerini kullanarak makineyle uzaktan etkileşim kurar<br><br> - **Ağ** - Makineye PsExec kullanılarak erişildiğinde veya makinedeki yazıcılar ve paylaşılan klasörler gibi paylaşılan kaynaklara erişildiğinde başlatılan oturum<br><br> - **Batch** - Zamanlanmış görevler tarafından başlatılan oturum<br><br> - **Hizmet** - Hizmetler başlatılırken başlatılan oturum<br> |
| `AccountDomain` | `string` | Hesabın etki alanı |
| `AccountName` | `string` | Hesabın kullanıcı adı |
| `AccountSid` | `string` | Hesabın Güvenlik Tanımlayıcısı (SID) |
| `Protocol` | `string` | İletişim sırasında kullanılan protokol |
| `FailureReason` | `string` | Kaydedilen eylemin neden başarısız olduğunu açıklayan bilgiler |
| `IsLocalAdmin` | `boolean` | Kullanıcının makinede yerel yönetici olup olmadığını gösteren Boole göstergesi |
| `LogonId` | `string` | Oturum açma oturumlarının tanımlayıcısı. Bu tanımlayıcı aynı makinede yalnızca yeniden başlatmalar arasında benzersizdir |
| `RemoteDeviceName` | `string` | Etkilenen makinede uzak işlem gerçekleştiren makinenin adı. Bildirilen olaya bağlı olarak, bu ad tam etki alanı adı (FQDN), NetBIOS adı veya etki alanı bilgisi olmayan bir ana bilgisayar adı olabilir |
| `RemoteIP` | `string` | Bağlanılmakta olan IP adresi |
| `RemoteIPType` | `string` | Genel, Özel, Ayrılmış, Geri Döngü, Teredo, FourToSixMapping ve Broadcast gibi IP adresi türü |
| `RemotePort` | `int` | Bağlı olan uzak cihazda TCP bağlantı noktası |
| `InitiatingProcessAccountDomain` | `string` | Olaydan sorumlu işlemi çalıştıran hesabın etki alanı |
| `InitiatingProcessAccountName` | `string` | Olaydan sorumlu işlemi çalıştıran hesabın kullanıcı adı |
| `InitiatingProcessAccountSid` | `string` | Olaydan sorumlu işlemi çalıştıran hesabın Güvenlik Tanımlayıcısı (SID) |
| `InitiatingProcessAccountUpn` | `string` | Olaydan sorumlu işlemi çalıştıran hesabın kullanıcı asıl adı (UPN) |
| ` InitiatingProcessAccountObjectId` | `string` | Olaydan sorumlu işlemi çalıştıran kullanıcı hesabının Azure AD nesne kimliği |
| `InitiatingProcessIntegrityLevel` | `string` | Olayı başlatan işlemin bütünlük düzeyi. Windows, bir internet indirmesinden başlatılmış olmaları gibi belirli özelliklere göre süreçlere bütünlük düzeyleri atar. Bu bütünlük düzeyleri kaynaklara yönelik izinleri etkiler |
| `InitiatingProcessTokenElevation` | `string` | Olayı başlatan işleme uygulanan Kullanıcı Access Control (UAC) ayrıcalık yükseltmesinin varlığını veya yokluğunu gösteren belirteç türü |
| `InitiatingProcessSHA1` | `string` | Olayı başlatan işlemin SHA-1 'i (görüntü dosyası) |
| `InitiatingProcessSHA256` | `string` | Olayı başlatan işlemin SHA-256'sı (görüntü dosyası). Bu alan genellikle doldurulmamaktadır; kullanılabilir olduğunda SHA1 sütununu kullanın |
| `InitiatingProcessMD5` | `string` | Olayı başlatan işlemin MD5 karması (görüntü dosyası) |
| `InitiatingProcessFileName` | `string` | Olayı başlatan işlemin adı |
| `InitiatingProcessFileSize` | `long` | Olaydan sorumlu işlemi çalıştıran dosyanın boyutu |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Olayın sorumlu olduğu işlemin sürüm bilgilerinden (görüntü dosyası) şirket adı |
| `InitiatingProcessVersionInfoProductName` | `string` | Olaydan sorumlu işlemin sürüm bilgilerinden (görüntü dosyası) ürün adı |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Olaydan sorumlu işlemin sürüm bilgilerinden (görüntü dosyası) ürün sürümü |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Olayın sorumlu olduğu işlemin sürüm bilgilerinden (görüntü dosyası) iç dosya adı |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Olaydan sorumlu işlemin sürüm bilgilerinden (görüntü dosyası) özgün dosya adı |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Olaydan sorumlu işlemin sürüm bilgilerinden açıklama (görüntü dosyası) |
| `InitiatingProcessId` | `int` | Olayı başlatan işlemin İşlem Kimliği (PID) |
| `InitiatingProcessCommandLine` | `string` | Olayı başlatan işlemi çalıştırmak için kullanılan komut satırı |
| `InitiatingProcessCreationTime` | `datetime` | Olayı başlatan işlemin başlatıldığı tarih ve saat |
| `InitiatingProcessFolderPath` | `string` | Olayı başlatan işlemi (görüntü dosyası) içeren klasör |
| `InitiatingProcessParentId` | `int` | Olaydan sorumlu işlemi oluşturan üst işlemin İşlem Kimliği (PID) |
| `InitiatingProcessParentFileName` | `string` | Olaydan sorumlu işlemi oluşturan üst işlemin adı |
| `InitiatingProcessParentCreationTime` | `datetime` | Olaydan sorumlu işlemin üst öğesinin başlatıldığı tarih ve saat |
| `ReportId` | `long` | Yinelenen sayacı temel alan olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütunun DeviceName ve Timestamp sütunlarıyla birlikte kullanılması gerekir |
| `AppGuardContainerId` | `string` | Application Guard tarafından tarayıcı etkinliğini yalıtmak için kullanılan sanallaştırılmış kapsayıcının tanımlayıcısı |
| `AdditionalFields` | `string` | JSON dizi biçimindeki olay hakkında ek bilgi |

>[!NOTE]
>Uç Nokta için Defender'a eklenen Windows 7 veya Windows Server 2008R2 cihazlarında DeviceLogonEvents koleksiyonu desteklenmez. Kullanıcı oturum açma etkinliğine en uygun görünürlük için daha yeni bir işletim sistemine yükseltmenizi öneririz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
