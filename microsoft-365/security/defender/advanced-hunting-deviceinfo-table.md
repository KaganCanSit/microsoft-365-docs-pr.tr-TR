---
title: Gelişmiş av şemasında CihazBilgileri tablosu
description: Gelişmiş av şemasının CihazBilgileri tablosunda işletim sistemi, bilgisayar adı ve diğer makine bilgileri hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, makinebilgileri, CihazBilgileri, cihaz, makine, işletim sistemi, platform, kullanıcılar
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
ms.openlocfilehash: 245a9aa11bcaf10ba6f3b8fe0fe429267a355560
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034238"
---
# <a name="deviceinfo"></a>CihazBilgileri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş `DeviceInfo` arama [şemasında yer alan](advanced-hunting-overview.md) tablo, kuruluşta işletim sistemi sürümü, etkin kullanıcılar ve bilgisayar adı gibi cihazlar hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `ClientVersion` | `string` | Makinede çalışan uç nokta aracısı veya algılayıcı sürümü |
| `PublicIP` | `string` | Ekli makine tarafından Uç Nokta için Microsoft Defender hizmetine bağlanmak için kullanılan genel IP adresi. Bu, makinenin kendi IP adresi, NAT cihazı veya proxy olabilir |
| `OSArchitecture` | `string` | Makinede çalışan işletim sisteminin mimarisi |
| `OSPlatform` | `string` | Makinede çalışan işletim sisteminin platformu. Bu, Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `OSBuild` | `string` | Makinede çalışan işletim sisteminin derleme sürümü |
| `IsAzureADJoined` | `boolean` | Makinenin diğer makineye katılıp katılmadı şeklinde Boole Azure Active Directory |
| `AadDeviceId` | `string` | Azure AD'de cihaz için benzersiz tanımlayıcı |
| `LoggedOnUsers` | `string` | JSON dizi biçiminde etkinlik sırasında makinede oturum açan tüm kullanıcıların listesi |
| `RegistryDeviceTag` | `string` | Kayıt defteri aracılığıyla eklenen makine etiketi |
| `OSVersion` | `string` | Makinede çalışan işletim sisteminin sürümü |
| `MachineGroup` | `string` | Makinenin makine grubu. Bu grup, makineye erişimi belirlemek için rol tabanlı erişim denetimi tarafından kullanılır |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır |
| `OnboardingStatus` | `string` | Cihazın şu anda Uç Nokta için Microsoft Defender'a ekli mi yoksa desteklenmiyor mu olduğunu gösterir |
|`AdditionalFields` | `string` | JSON dizi biçimindeki olay hakkında ek bilgi |
|`DeviceCategory` | `string` | Belirli cihaz türlerini aşağıdaki kategoriler altında gruplandıran daha geniş sınıflandırma: Uç nokta, Ağ cihazı, IoT, Bilinmiyor |
|`DeviceType` | `string` | Ağ cihazı, iş istasyonu, sunucu, mobil, oyun konsolu veya yazıcı gibi amaca ve işlevlere dayalı cihazın türü |
|`DeviceSubType` | `string` | Mobil cihaz bir tablet veya akıllı telefon gibi belirli cihaz türleri için ek değiştirici olabilir; yalnızca cihaz bulma bu öznitelik hakkında yeterli bilgi bulursa kullanılabilir |
|`Model` | `string` | Satıcı veya üreticinin ürün adı veya numarası, ancak cihaz bulma bu öznitelik hakkında yeterli bilgi bulursa kullanılabilir |
|`Vendor` | `string` | Ürün satıcısının veya üreticisinin adı; ancak cihaz bulma bu öznitelik hakkında yeterli bilgi bulursa kullanılabilir |
|`OSDistribution` | `string` | Linux için Ubuntu veya RedHat gibi işletim sistemi platformlarının dağıtımı |
|`OSVersionInfo` | `string` | Işletim sistemi sürümü hakkında popüler ad, kod adı veya sürüm numarası gibi ek bilgiler |
|`MergedDeviceIds` | `string` | Aynı cihaza atanmış olan önceki cihaz kimlikleri |
|`MergedToDeviceId` | `string` | Bir cihaza atanan en son cihaz kimliği |

Tablo `DeviceInfo` , bir cihazdan düzenli raporlar veya sinyaller olan sinyallere dayalı olarak cihaz bilgilerini sağlar. Her on beş dakikada bir, cihaz gibi öznitelikleri sık sık değiştiren bir kısmi sinyal gönderir `LoggedOnUsers`. Günde bir, cihazın özniteliklerini içeren tam sinyal gönderilir.

Cihazın en son durumunu almak için aşağıdaki örnek sorguyu kullanabilirsiniz:

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
