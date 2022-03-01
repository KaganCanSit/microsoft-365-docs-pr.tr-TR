---
title: DeviceTvmSoftwareEvidenceBeta tablo in the advanced hunting schema
description: Gelişmiş av şemasında DeviceTvmSoftwareEvidenceBeta tabloyu kullanmayı öğrenin.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, kanıt, yazılım kanıtı, TVM, cihaz yönetimi, yazılım, stok, GÜVENLIK açıkları, YERKARAKD kimliği, OS DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 7fd064b906e4afe5e337df85d9dc6f174edc99cf
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021553"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

> [!IMPORTANT]
> Tablo `DeviceTvmSoftwareEvidenceBeta` şu anda beta aşamasındadır. Beta sürümünden ayrıldığında, tablonun son adı değişir ve sütun adları da değişebilir. Bu değişiklikler büyük olasılıkla önceki adları kullanmaya devam ediyor olan sorguları kıracak. Kullanıcılara, bu tablo sonlandırıldıklarında sorgularını gözden geçirmeleri ve ayarlamaları önerilir. 


Gelişmiş `DeviceTvmSoftwareEvidenceBeta` arama şemasında yer alan tablo, Tehdit & Güvenlik [Açığı Yönetimi'ne](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) ilişkin [yazılım kanıtı bölümünden veriler içerir](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence). Bu tablo, belirli bir yazılımın cihazda nerede algılandığından dair kanıtı görüntülemene olanak sağlar. Örneğin bu tabloyu belirli bir yazılımın dosya yollarını belirlemek için kullanabilirsiniz. Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Hizmette cihaz için benzersiz tanımlayıcı |
| `SoftwareVendor` | `string` | Yazılım yayıncının adı |
| `SoftwareName` | `string` | Yazılım ürününün adı |
| `SoftwareVersion` | `string` | Yazılım ürününün sürüm numarası |
| `RegistryPaths` | `dynamic` | Bir cihaz üzerinde yazılımın varlığını belirten kanıtın algılandığında kayıt defteri yolları |
| `DiskPaths` | `dynamic` | Bir cihaz üzerinde yazılımın varlığını belirten dosya düzeyinde kanıtın algılandığında disk yolları |
| `LastSeenTime` | `string` | Cihazın bu hizmet tarafından en son görülen tarih ve saat |




## <a name="related-topics"></a>İlgili konular

- [Tehdit Veya Güvenlik & Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Önceden tehdit avı](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
