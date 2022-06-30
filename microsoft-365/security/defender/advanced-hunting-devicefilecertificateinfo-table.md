---
title: Gelişmiş tehdit avcılığı şemasındaki DeviceFileCertificateInfo tablosu
description: Gelişmiş tehdit avcılığı şemasının DeviceFileCertificateInfo tablosunda dosya imzalama bilgileri hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, dijital imza, sertifika, dosya imzalama, DeviceFileCertificateInfo
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
ms.openlocfilehash: 019ca8eced735b8a9e24c2b0f3e3baae37757875
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554565"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş `DeviceFileCertificateInfo` [tehdit avcılığı](advanced-hunting-overview.md) şemasındaki tablo, dosya imzalama sertifikaları hakkında bilgi içerir. Bu tabloda, uç noktalardaki dosyalarda düzenli olarak gerçekleştirilen sertifika doğrulama etkinliklerinden elde edilen veriler kullanılır.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için [gelişmiş avcılık başvurusuna bakın](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Olayın kaydedilildiği tarih ve saat |
| `DeviceId` | `string` | Hizmetteki makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `IsSigned` | `boolean` | Dosyanın imzalanıp imzalanmadığını gösterir |
| `SignatureType` | `string` | İmza bilgilerinin dosyanın kendisine eklenmiş içerik olarak mı yoksa bir dış katalog dosyasından mı okundu olduğunu gösterir |
| `Signer` | `string` | Dosyanın imzalayanı hakkında bilgi |
| `SignerHash` | `string` | İmzalayanı tanımlayan benzersiz karma değer |
| `Issuer` | `string` | Sertifika veren sertifika yetkilisi (CA) hakkında bilgi |
| `IssuerHash` | `string` | Sertifika veren sertifika yetkilisini (CA) tanımlayan benzersiz karma değer |
| `CertificateSerialNumber` | `string` | Veren sertifika yetkilisine (CA) özgü sertifikanın tanımlayıcısı |
| `CrlDistributionPointUrls` | `string` |  Sertifikalar ve sertifika iptal listeleri (CRL) içeren ağ paylaşımlarının URL'lerini listeleyen JSON dizisi |
| `CertificateCreationTime` | `datetime` | Sertifikanın oluşturulduğu tarih ve saat |
| `CertificateExpirationTime` | `datetime` | Sertifikanın süresi dolmak üzere ayarlandığı tarih ve saat |
| `CertificateCountersignatureTime` | `datetime` | Sertifikanın imzalandığı tarih ve saat |
| `IsTrusted` | `boolean` | Bilinmeyen kök sertifika bilgilerini, geçersiz imzaları, iptal edilen sertifikaları ve diğer şüpheli öznitelikleri denetleyen WinVerifyTrust işlevinin sonuçlarına bağlı olarak dosyanın güvenilir olup olmadığını gösterir |
| `IsRootSignerMicrosoft` | `boolean` | Kök sertifikanın imzalayanının Microsoft olup olmadığını ve dosyanın Windows işletim sistemine eklenip eklenmediğini gösterir |
| `ReportId` | `long` | Yinelenen sayacı temel alan olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütunun DeviceName ve Timestamp sütunlarıyla birlikte kullanılması gerekir. | 

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
