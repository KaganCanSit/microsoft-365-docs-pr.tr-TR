---
title: Gelişmiş av şemasında DeviceNetworkInfo tablosu
description: Gelişmiş av şemasının DeviceNetworkInfo tablosunda ağ yapılandırma bilgileri hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, makinenetworkinfo, DeviceNetworkInfo, cihaz, makine, mac, ip, bağdaştırıcı, dns, tabloya, ağ geçidi, şema
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
ms.openlocfilehash: 86c087c8a8cdfa80904612625c08ec37ca6813ca
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018998"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender



Gelişmiş `DeviceNetworkInfo` arama [şemasında yer](advanced-hunting-overview.md) alan tablo, ağ bağdaştırıcıları, IP ve MAC adresleri ve bağlı ağlar veya etki alanları gibi makine ağ yapılandırması hakkında bilgi içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `NetworkAdapterName` | `string` | Ağ bağdaştırıcısının adı |
| `MacAddress` | `string` | Ağ bağdaştırıcısının MAC adresi |
| `NetworkAdapterType` | `string` | Ağ bağdaştırıcısı türü. Olası değerler için bu [numaralamaya bakın](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | Ağ bağdaştırıcısının işlem durumu. Olası değerler için bu [numaralamaya bakın](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | Geçiş protokolü, arabirimin bu amaçla kullanılıyorsa (örneğin, 6'dan 4'e, Teredo, ISATAP, PPTP, SSTP ve SSH) |
| `ConnectedNetworks` | `string` | Bağdaştırıcının bağlı olduğu ağlar. Her JSON dizisi ağ adını, kategoriyi (genel, özel veya etki alanı), bir açıklamayı ve İnternet'e genel olarak bağlı olup olmadığını gösteren bir bayrak içerir |
| `DnsAddresses` | `string` | JSON dizi biçiminde DNS sunucusu adresleri |
| `IPv4Dhcp` | `string` | AİLE sunucusunun IPv4 adresi |
| `IPv6Dhcp` | `string` | IPv6 address of HERale sunucusu |
| `DefaultGateways` | `string` | JSON dizi biçimindeki varsayılan ağ geçidi adresleri |
| `IPAddresses` | `string` | Bağdaştırıcıya atanan tüm IP adreslerini ve ilgili alt ağ ön eklerini ve IP adresi alanı (genel, özel veya link-local gibi) içeren JSON dizisi |
| `ReportId` | `long` | Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütun DeviceName ve Timestamp sütunlarıyla birlikte kullanılmalıdır |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)