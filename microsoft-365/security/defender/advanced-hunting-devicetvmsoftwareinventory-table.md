---
title: DeviceTvmSoftwareInventory table in the advanced hunting schema
description: Gelişmiş arama şemasının DeviceTvmSoftwareInventory tablosunda cihazlarınız için yazılım stoku hakkında bilgi edinebilirsiniz.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, yazılım, envanter, güvenlik açıkları, YERİnEKULLANİş Kimliği, OS DeviceTvmSoftwareInventoryNerabilities
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
ms.openlocfilehash: 10a184e6ce36129a84197cc02caae3b96625e39a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018993"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

>[!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.


Gelişmiş `DeviceTvmSoftwareInventory` arama şemasında yer alan tablo, [destek &](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) da içinde olmak üzere ağınıza yüklenmiş yazılımların Tehdit & Güvenlik Açığı Yönetimi envanterini içerir. Örneğin, şu anda korumasız bir yazılım sürümüyle yüklü olan cihazlara ilişkin etkinliklerin avına bakabilirsiniz. Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!NOTE]
> `DeviceTvmSoftwareVulnerabilities` Tablo`DeviceTvmSoftwareInventory`, ve tabloların yerini `DeviceTvmSoftwareInventoryVulnerabilities` alır. Birlikte, ilk iki tablo daha fazla sütun içerir. Bu sütunlardan daha fazlasını, bu nedenle kötümserlik yönetimi etkinliklerinizi bilgilendirmeye veya korumasız cihazlar için avına devam edin.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `OSPlatform` | `string` | Makinede çalışan işletim sisteminin platformu. Bu, Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `OSVersion` | `string` | Makinede çalışan işletim sisteminin sürümü |
| `OSArchitecture` | `string` | Makinede çalışan işletim sisteminin mimarisi |
| `SoftwareVendor` | `string` | Yazılım satıcısının adı |
| `SoftwareName` | `string` | Yazılım ürününün adı |
| `SoftwareVersion` | `string` | Yazılım ürününün sürüm numarası |
| `EndOfSupportStatus` | `string` | Yazılım ürününün yaşam döngüsü aşamasını belirtilen destek sonu (EOS) veya kullanım ömrü sonu (EOL) tarihine göre gösterir |
| `EndOfSupportDate` | `string` | Yazılım ürününün destek sonu (EOS) veya ömür sonu (EOL) tarihi |



## <a name="related-topics"></a>İlgili konular

- [Önceden tehdit avı](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Tehdit Veya Güvenlik & Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)