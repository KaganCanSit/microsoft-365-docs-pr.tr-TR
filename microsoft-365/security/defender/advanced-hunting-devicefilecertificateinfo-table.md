---
title: Gelişmiş av şemasında DeviceFileCertificateInfo tablosu
description: Gelişmiş av şemasının DeviceFileCertificateInfo tablosunda dosya imzalama bilgileri hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, dijital imza, sertifika, dosya imzalama, DeviceFileCertificateInfo
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
ms.openlocfilehash: 7b43b6ad8ed1422830f08358f460b20b16588996
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018897"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş `DeviceFileCertificateInfo` av [şemasında yer alan tablo](advanced-hunting-overview.md) , dosya imzalama sertifikaları hakkında bilgi içerir. Bu tablo, uç noktalardaki dosyalarda düzenli olarak gerçekleştirilen sertifika doğrulama etkinliklerinden alınan verileri kullanır.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `IsSigned` | `boolean` | Dosyanın imzalanmış olup olmadığını gösterir |
| `SignatureType` | `string` | İmza bilgisinin dosyanın kendisine eklenmiş içerik olarak mı yoksa bir dış katalog dosyasından mı okundu olduğunu gösterir |
| `Signer` | `string` | Dosyanın imzacı hakkında bilgiler |
| `SignerHash` | `string` | İmzayı tanımlayan benzersiz karma değeri |
| `Issuer` | `string` | Sertifika yetkilisi (CA) hakkında bilgi |
| `IssuerHash` | `string` | Sertifika yetkilisini (CA) tanımlayan benzersiz karma değeri |
| `CertificateSerialNumber` | `string` | Sertifika yetkilisine (CA) özgü sertifikanın tanımlayıcısı |
| `CrlDistributionPointUrls` | `string` |  Sertifikalar ve sertifika iptal listeleri (CRL) içeren ağ paylaşımlarının URL'lerini listeen JSON dizisi |
| `CertificateCreationTime` | `datetime` | Sertifikanın oluşturulma tarihi ve saati |
| `CertificateExpirationTime` | `datetime` | Sertifikanın süresinin dolacak şekilde ayar olduğu tarih ve saat |
| `CertificateCountersignatureTime` | `datetime` | Sertifikanın imzalanmamış olduğu tarih ve saat |
| `IsTrusted` | `boolean` | Bilinmeyen kök sertifika bilgilerini, geçersiz imzaları, iptal edilen sertifikaları ve diğer şüpheli öznitelikleri denetlerken WinVerifyTrust işlevinin sonuçlarına dayalı olarak dosyanın güvenilir olup olmadığını gösterir |
| `IsRootSignerMicrosoft` | `boolean` | Kök sertifikanın imzalayanın Microsoft olup olmadığını gösterir |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için, bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır. | 

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
