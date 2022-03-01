---
title: Gelişmiş av şemasında UyarıBilgileri tablosu
description: Gelişmiş av şemasının AlertInfo tablosunda uyarı oluşturma olayları hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, UyarıBilgileri, uyarı, önem derecesi, kategori, MITRE, ATT&CK, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Microsoft Cloud App Security, MCAS ve Kimlik için Microsoft Defender
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
ms.openlocfilehash: 0298b4f83ac748048215af4f5b1f8261a2a8c67c
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018990"
---
# <a name="alertinfo"></a>UyarıBilgileri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender



Gelişmiş `AlertInfo` av [şemasında](advanced-hunting-overview.md) yer alan tablo, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender ile ilgili uyarılar hakkında bilgiler içerir. Bu tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz [. gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Etkinliğin kaydedl olduğu tarih ve saat |
| `AlertId` | `string` | Uyarı için benzersiz tanımlayıcı |
| `Title` | `string` | Uyarının başlığı |
| `Category` | `string` | Uyarıda tanımlanan tehdit göstergesi veya ihlal etkinliğinin türü |
| `Severity` | `string` | Uyarıda tanımlanan tehdit göstergesi veya ihlal etkinliğinin olası etkisini (yüksek, orta veya düşük) gösterir |
| `ServiceSource` | `string` | Uyarı bilgilerini sağlanan ürün veya hizmet |
| `DetectionSource` | `string` | Önemli bileşeni veya etkinliği tespit edilen algılama teknolojisi veya algılayıcı |
| `AttackTechniques` | `string` | MITRE ATT&uyarıyı tetikleyen etkinlikle ilişkilendirilmiş CK tekniklerini kullanır |

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
