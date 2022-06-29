---
title: Gelişmiş tehdit avcılığı şemasında DeviceTvmSoftwareInventory tablosu
description: Gelişmiş tehdit avcılığı şemasının DeviceTvmSoftwareInventory tablosunda cihazlarınızdaki yazılım envanteri hakkında bilgi edinin.
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, yazılım, envanter, güvenlik açıkları, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: cecbf2078bff0143a5c14b8b0cffb636d4fa3454
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490807"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

>[!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.


`DeviceTvmSoftwareInventory` Gelişmiş tehdit avcılığı şemasındaki tablo, destek sonu bilgileri de dahil olmak üzere ağınızdaki cihazlarda yüklü olan yazılımların [Tehdit & Güvenlik Açığı Yönetimi](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) envanterini içerir. Örneğin, şu anda güvenlik açığı olan bir yazılım sürümüyle yüklenen cihazlarla ilgili olayları avlayabilirsiniz. Tablodan bilgi döndüren sorgular oluşturmak için bu başvuruyu kullanın.

>[!NOTE]
> `DeviceTvmSoftwareInventory` ve `DeviceTvmSoftwareVulnerabilities` tabloları tablonun yerini aldı`DeviceTvmSoftwareInventoryVulnerabilities`. İlk iki tablo birlikte, güvenlik açığı yönetim etkinliklerinizi bilgilendirmek veya savunmasız cihazları avlamak için kullanabileceğiniz daha fazla sütun içerir.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için gelişmiş [avcılık başvurusuna](advanced-hunting-schema-tables.md) bakın.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Hizmetteki makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `OSPlatform` | `string` | Makinede çalışan işletim sisteminin platformu. Bu, Windows 11, Windows 10 ve Windows 7 gibi aynı aile içindeki varyasyonlar da dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `OSVersion` | `string` | Makinede çalışan işletim sisteminin sürümü |
| `OSArchitecture` | `string` | Makinede çalışan işletim sisteminin mimarisi |
| `SoftwareVendor` | `string` | Yazılım satıcısının adı |
| `SoftwareName` | `string` | Yazılım ürününün adı |
| `SoftwareVersion` | `string` | Yazılım ürününün sürüm numarası |
| `EndOfSupportStatus` | `string` | Yazılım ürününün belirtilen destek sonu (EOS) veya kullanım süresi sonu (EOL) tarihine göre yaşam döngüsü aşamasını gösterir |
| `EndOfSupportDate` | `string` | Yazılım ürününün destek sonu (EOS) veya kullanım süresi sonu (EOL) tarihi |
| `ProductCodeCpe` | `string` | CpE olmayan yazılım ürünü veya 'kullanılamaz' CPE |
| `CveTags` | `string` | CVE ile ilgili bir etiket dizisi. Şu anda desteklenen etiketler "ZeroDay" ve "NoSecurityUpdate" etiketleridir.

## <a name="related-topics"></a>İlgili konular

- [Tehditleri proaktif olarak avlama](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
- [Tehdit & Güvenlik Açığı Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)