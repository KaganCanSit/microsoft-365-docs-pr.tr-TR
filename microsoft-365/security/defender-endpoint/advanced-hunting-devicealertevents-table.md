---
title: Gelişmiş av şemasında DeviceAlertEvents tablosu
description: Gelişmiş av şemasının DeviceAlertEvents tablosunda uyarı oluşturma olayları hakkında bilgi
keywords: gelişmiş av, tehdit avı, siber tehdit avı, mdatp, microsoft defender atp, uç nokta için Microsoft Defender, wdatp arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, DeviceAlertEvents, uyarı, önem derecesi, kategori
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/22/2020
ms.technology: mde
ms.openlocfilehash: 32dbff60a37c31cdbfd492eb5d746a10d9b7a185
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021768"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Gelişmiş `DeviceAlertEvents` arama [şemasında yer alan](advanced-hunting-overview.md) tablo, aramayla ilgili uyarılar hakkında Microsoft 365 Defender. Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av şeması başvurusu](advanced-hunting-schema-reference.md).

|Sütun adı|Veri türü|Açıklama|
|---|---|---|
|`AlertId`|dize|Uyarı için benzersiz tanımlayıcı|
|`Timestamp`|datetime|Etkinliğin kaydedl olduğu tarih ve saat|
|`DeviceId`|dize|Hizmette cihaz için benzersiz tanımlayıcı|
|`DeviceName`|dize|Cihazın tam etki alanı adı (FQDN)|
|`Severity`|dize|Uyarıda tanımlanan tehdit göstergesi veya ihlal etkinliğinin olası etkisini (yüksek, orta veya düşük) gösterir|
|`Category`|dize|Uyarıda tanımlanan tehdit göstergesi veya ihlal etkinliğinin türü|
|`Title`|dize|Uyarının başlığı|
|`FileName`|dize|Kaydedilen eylemin uygulandığı dosyanın adı|
|`SHA1`|dize|Kaydedilen eylemin uygulandığı dosyanın SHA-1|
|`RemoteUrl`|dize|Bağlanan URL veya tam etki alanı adı (FQDN)|
|`RemoteIP`|dize|Bağlantının olduğu IP adresi|
|`AttackTechniques`|dize|MITRE ATT&uyarıyı tetikleyen etkinlikle ilişkilendirilmiş CK tekniklerini kullanır|
|`ReportId`|long|Yinelenen bir sayaça dayalı olay tanımlayıcısı. Benzersiz olayları tanımlamak için bu sütun ve sütunlarla `DeviceName` birlikte `Timestamp` kullanılmalıdır|
|`Table`|dize|Olayın ayrıntılarını içeren tablo|

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Şemayı anlama](advanced-hunting-schema-reference.md)
