---
title: Microsoft 365 Defender için gelişmiş avda FileProfile() işlevi
description: Gelişmiş arama sorgusu sonuçlarınıza dosya bilgilerini zenginleştirmek için FileProfile() işlevini kullanmayı öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, FileProfile, dosya profili, işlev, zenginleştirme
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
ms.openlocfilehash: 2cd8c91717af8390160bf45a625ae3a3044ee387
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019021"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

İşlev `FileProfile()` , gelişmiş avda bulunan ve [sorgu tarafından](advanced-hunting-overview.md) bulunan dosyalara aşağıdaki verileri ekleyen bir zenginleştirme işlevidir.

| Sütun | Veri türü | Açıklama |
|------------|---------------|-------------|
| `SHA1` | `string` | Kaydedilen eylemin uygulandığı dosyanın SHA-1 |
| `SHA256` | `string` | Kayıtlı eylemin uygulandığı dosyanın SHA-256'sı |
| `MD5` | `string` | Kaydedilen eylemin uygulandığı dosyanın MD5 karması |
| `FileSize` | `int` | Dosyanın bayt cinsinden boyutu |
| `GlobalPrevalence` | `int` | Microsoft tarafından genel olarak gözlemlenen varlık örneklerinin sayısı |
| `GlobalFirstSeen` | `datetime` | Varlığın Microsoft tarafından ilk kez gözlenme tarihi ve saati |
| `GlobalLastSeen` | `datetime` | Varlığın Microsoft tarafından en son gözlemlenme tarihi ve saati |
| `Signer` | `string` | Dosyanın imzacı hakkında bilgiler |
| `Issuer` | `string` | Sertifika yetkilisi (CA) hakkında bilgi |
| `SignerHash` | `string` | İmzayı tanımlayan benzersiz karma değeri |
| `IsCertificateValid` | `boolean` | Dosyayı imzalamak için kullanılan sertifikanın geçerli olup olmadığı |
| `IsRootSignerMicrosoft` | `boolean` | Kök sertifikanın imzalayanın Microsoft olup olmadığını gösterir |
| `SignatureState` | `string` | Dosya imza durumu: SignedValid - dosya geçerli bir imzayla imzalanmış, SignedInvalid - dosya imzalandı ama sertifika geçersiz, İmzasız - dosya imzalanmamış, Bilinmiyor - dosyayla ilgili bilgiler alınamıyor
| `IsExecutable` | `boolean` | Dosyanın Taşınabilir Yürütülebilir (PE) dosyası olup olmadığı |
| `ThreatName` | `string` | Kötü amaçlı yazılım veya bulunan diğer tehditlere yönelik algılama adı |
| `Publisher` | `string` | Dosyayı yayım kuruluş adı |
| `SoftwareName` | `string` | Yazılım ürününün adı |

## <a name="syntax"></a>Söz dizimi

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Bağımsız değişkenler

- **x**—kullanmak üzere dosya kimliği sütunu: `SHA1`, `SHA256`, `InitiatingProcessSHA1`veya `InitiatingProcessSHA256`; işlevi `SHA1` belirtilmemişse kullanır
- **y**—zenginleştirmek için kayıt sayısıyla sınırla, 1-1000; belirtilmemişse, işlev 100 kullanır


>[!TIP]
> Zenginleştirme işlevleri, ek bilgileri yalnızca uygun olduğunda gösterir. Bilgilerin kullanılabilirliği değişkendir ve çok fazla faktöre bağlıdır. Sorgularda FileProfile() kullanırken veya özel algılamalar oluştururken bunu göz önünde bulundurarak göz önünde bulundurabilirsiniz. En iyi sonuçları elde etmek için FileProfile() işlevini SHA1 ile birlikte kullanmanız önerilir.

## <a name="examples"></a>Örnekler

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Project SHA1 sütununu yeniler ve zenginleştirir

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>İlk 500 kaydı zenginleştirme ve yaygın olmayan dosyaları listele

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Daha fazla sorgu örneği elde](advanced-hunting-shared-queries.md)
