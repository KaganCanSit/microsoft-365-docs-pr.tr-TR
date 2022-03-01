---
title: Gelişmiş av şemasında DeviceFileEvents tablosu
description: Gelişmiş av şemasının DeviceFileEvents tablosunda dosyayla ilgili etkinlikler hakkında bilgi edinebilirsiniz
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, filecreationevents, DeviceFileEvents, dosyalar, yol, karma, sha1, sha256, md5
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
ms.openlocfilehash: 2350e2dfd4736743f23d181d4fc2c6de0d82ccc0
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019047"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş `DeviceFileEvents` av [şemasında dosya oluşturma](advanced-hunting-overview.md) , değiştirme ve diğer dosya sistemi olayları hakkında bilgi içeren tablo. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!TIP]
> Tablo tarafından desteklenen olay türleri (`ActionType` değerler) hakkında ayrıntılı bilgi için, Bulut için Defender'da bulunan yerleşik şema başvurularını kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `ActionType` | `string` | Olayı tetikleyen etkinlik türü. Ayrıntılar için [portal şeması başvurusuna](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) bakın |
| `FileName` | `string`| Kaydedilen eylemin uygulandığı dosyanın adı |
| `FolderPath` | `string` | Kaydedilen eylemin uygulandığı dosyayı içeren klasör |
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `SHA256` | `string` | Kayıtlı eylemin uygulandığı dosyanın SHA-256'sı. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `MD5` | `string` | Kaydedilen eylemin uygulandığı dosyanın MD5 karması |
| `FileOriginUrl` | `string` | Dosyanın indirildikten bulunduğu URL |
| `FileOriginReferrerUrl` | `string` | İndirilen dosyaya bağlantı içeren web sayfasının URL'si |
| `FileOriginIP` | `string` | Dosyanın indirildikten sonra IP adresi |
| `PreviousFolderPath` | `string` | Kayıtlı eylem uygulanmadan önce dosyayı içeren özgün klasör |
| `PreviousFileName` | `string` | Eylem sonucunda yeniden adlandırılan dosyanın özgün adı |
| `FileSize` | `long` | Dosyanın bayt cinsinden boyutu |
| `InitiatingProcessAccountDomain` | `string` | Etkinlikten sorumlu olan işlemi hesapta işlemden sorumlu olan etki alanı |
| `InitiatingProcessAccountName` | dize | Etkinlikten sorumlu olan işlemi randayanın kullanıcı adı |
| `InitiatingProcessAccountSid` | `string` | Olaydan sorumlu olan işlemi hesapta bulunduran hesabın Güvenlik Tanımlayıcısı (SID) |
| `InitiatingProcessAccountUpn` | `string` | Etkinlikten sorumlu olan işlemi hesaptan sorumlu olan hesabın kullanıcı asıl adı (UPN) |
| `InitiatingProcessAccountObjectId` | `string` | Olaydan sorumlu olan işlemi hesap hesaplarından sorumlu olan kullanıcı hesabının Azure AD nesne kimliği |
| `InitiatingProcessMD5` | `string` | Etkinliği başlatan işlem (resim dosyası) MD5 karması |
| `InitiatingProcessSHA1` | `string` | Olayı başlatan işlem (resim dosyası) SHA-1 |
| `InitiatingProcessSHA256` | `string` | Olayı başlatan işlem (resim dosyası) SHA-256. Bu alan genellikle doldurulmaz; kullanılabilir olduğunda SHA1 sütununu kullanın. |
| `InitiatingProcessFolderPath` | `string` | Olayı başlatan işlemi (resim dosyası) içeren klasör |
| `InitiatingProcessFileName` | `string` | Olayı başlatan sürecin adı |
| `InitiatingProcessFileSize` | `long` | Etkinliği başlatan işlem boyutu (resim dosyası) |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden şirket adı |
| `InitiatingProcessVersionInfoProductName` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden ürün adı |
|` InitiatingProcessVersionInfoProductVersion` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden gelen ürün sürümü |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden iç dosya adı |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Olayın sorumlu olduğu işlem (resim dosyası) sürüm bilgilerinden özgün dosya adı |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Etkinlikten sorumlu olan işlem (resim dosyası) sürüm bilgilerinden açıklama |
| `InitiatingProcessId` | `int` | Olayı başlatan sürecin Süreç Kimliği (PID) |
| `InitiatingProcessCommandLine` | `string` | Olayı başlatan işlemi çalıştırmak için kullanılan komut satırı |
| `InitiatingProcessCreationTime` | `datetime` | Olayı başlatan sürecin başlatıldığı tarih ve saat |
| `InitiatingProcessIntegrityLevel` | `string` | Olayı başlatan sürecin bütünlük düzeyi. Windows, İnternet indirmesi'den başlatıldılar gibi bazı özelliklere dayalı işlemlere bütünlük düzeyleri atar. Bu bütünlük düzeyleri kaynaklar üzerindeki izinleri etkiler |
| `InitiatingProcessTokenElevation` | `string` | Etkinliği başlatan işleme uygulanan Kullanıcı Erişim Denetimi (UAC) ayrıcalık yükseltmesi varlığını veya olmadığını belirten belirteç türü |
| `InitiatingProcessParentId` | `int` | Olaydan sorumlu olan işlemi bir diğer ana sürecin Süreç Kimliği (PID) |
| `InitiatingProcessParentFileName` | `string` | Etkinlikle ilgili olarak sorumlu olan işlemi bir ana sürecin adı |
| `InitiatingProcessParentCreationTime` | `datetime` | Etkinlikle ilgili olarak sorumlu olan sürecin üst öğesi başlat başlangıç tarihi ve saati |
| `RequestProtocol` | `string` | Uygunsa, etkinliği başlatmak için kullanılan ağ protokolü: Bilinmiyor, Yerel, SMB veya NFS |
| `RequestSourceIP` | `string` | Etkinliği başlatan uzak cihazın IPv4 veya IPv6 adresi |
| `RequestSourcePort` | `string` | Etkinliği başlatan uzak cihaz üzerinde kaynak bağlantı noktası |
| `RequestAccountName` | `string` | Etkinliği uzaktan başlatmak için kullanılan hesabın kullanıcı adı |
| `RequestAccountDomain` | `string` | Etkinliği uzaktan başlatmak için kullanılan hesabın etki alanı |
| `RequestAccountSid` | `string` | Etkinliği uzaktan başlatmak için kullanılan hesabın Güvenlik Tanımlayıcısı (SID) |
| `ShareName` | `string` | Dosyayı içeren paylaşılan klasörün adı |
| `InitiatingProcessFileSize` | `long` | Etkinlikten sorumlu olan işlemi randaen dosyanın boyutu |
| `SensitivityLabel` | `string` | Bilgi koruması için sınıflandırmak için e-postaya, dosyaya veya başka bir içeriğe uygulanan etiket |
| `SensitivitySubLabel` | `string` | Bilgi koruması için sınıflandırmak için e-postaya, dosyaya veya başka bir içeriğe uygulanan alt etiket; duyarlılık alt etiketleri duyarlılık etiketleri altında grupludur, ancak bağımsız olarak işlem gören |
| `IsAzureInfoProtectionApplied` | `boolean` | Dosyanın Azure Information Protection tarafından şifrelenmiş olup olmadığını gösterir |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için, bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır. |
| `AppGuardContainerId` | `string` | Application Guard tarafından tarayıcı etkinliğini yalıtmak için kullanılan sanallaştırılmış kapsayıcının tanımlayıcısı |
| `AdditionalFields` | `string` | Varlık veya olay hakkında ek bilgiler |
>[!NOTE]
> Dosya karma bilgileri her zaman kullanılabilir olduğunda gösterilir. Bununla birlikte, SHA1, SHA256 veya MD5'in hesaplanmamalerinin çeşitli olası nedenleri vardır. Örneğin, dosya uzak depolamada yer alıyor, başka bir işlemle kilitlenmiş, sıkıştırılmış veya sanal olarak işaretlenmiş olabilir. Bu senaryolarda, dosya karma bilgileri boş görünür.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
