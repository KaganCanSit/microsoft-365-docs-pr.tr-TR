---
title: Güvenlik temelleri değerlendirme profilleri
description: "\"Tehdit ve Güvenlik Açığı Yönetimi\" verileri çeken güvenlik temelleri değerlendirme profilleri API'leri hakkında bilgi sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir."
keywords: api, API'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirmesi başına, makine değerlendirmesi başına, güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım güvenlik açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: ca110cfba43b95790114928f1c0d3adcae46f087
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65369625"
---
# <a name="list-all-security-baselines-assessment-profiles"></a>Tüm güvenlik temelleri değerlendirme profillerini listeleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi - Güncelleştirme](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender Güvenlik Açığı Yönetimi mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.- Güncelleştirme](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-security-baselines-assessment-profiles"></a>1. Güvenlik temelleri değerlendirme profillerini alma

Bu API, kuruluş tarafından oluşturulan tüm güvenlik temelleri değerlendirme profillerinin listesini alır.  

### <a name="11-parameters"></a>1.1 Parametreler

- OData V4 sorgularını destekler.  
- OData tarafından desteklenen işleçler:  
  - üzerinde $filter: id,name, operatingSystem, operatingSystemVersion, status, settingsNumber, passedDevices, totalDevices  
  - maksimum değeri 10.000 olan $top.  
  - $skip.

### <a name="12-http-request"></a>1.2 HTTP isteği

```http
GET:/api/baselineProfiles
```

### <a name="13-request-headers"></a>1.3 İstek üst bilgileri

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

### <a name="14-properties"></a>1.4 Özellikleri

|Özellik | Tür | Açıklama |
|:---|:---|:---|
|Kimliği | Dize | Belirli temel profilin benzersiz tanımlayıcısı.
|Adı | Dize | Profil adı.
|Açıklama | Dize | Profil açıklaması.
|Kriter | Dize | Profil karşılaştırması.
|Sürüm | Dize | Profil sürümü.
|Operatingsystem|Dize|Profilin geçerli işletim sistemi.
|operatingSystemVersion|Dize|Profilin geçerli işletim sistemi sürümü.
|Durum|Boole|Profilin etkin olup olmadığını gösterir
|complianceLevel|Dize|Profil için seçilen uyumluluk düzeyi.
|settingsNumber|Int|Profildeki seçili yapılandırmaların sayısı.
|Createdby|Dize|Bu profili oluşturan kullanıcı.
|lastUpdatedBy|Datetime|Bu profili değiştiren son kullanıcı.
|createdOnTimeOffset|Datetime|Profilin oluşturulduğu tarih ve saat.
|lastUpdateTimeOffset|Datetime|Profilin son güncelleştirildiği tarih ve saat.
|passedDevices|Int|Bu profil için geçerli olan ve tüm profil yapılandırmalarıyla uyumlu olan cihaz sayısı.
|totalDevices|Int|Bu profil için geçerli cihaz sayısı.

## <a name="15-example"></a>1.5 Örneği

### <a name="151-request-example"></a>1.5.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/baselineProfiles 
```

### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json
{  
    "@odata.context": "https:// api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicBaselineProfileDto)",  
    "value": 
    [  
        {  
            "id": "02bcbb9d-d197-479e-811e-1cd5a6f9f8fa",  
            "name": "Windows 10 build 1909 CIS profile",  
            "description": "important",  
            "benchmark": "CIS",  
            "version": "1.0.0",  
            "operatingSystem": "Windows 10",  
            "operatingSystemVersion": "1909",  
            "status": true,  
            "complianceLevel": "Level 1 (L1) - Corporate/Enterprise Environment (general use)",  
            "settingsNumber": 51,  
            "createdBy": "user@org.net",  
            "lastUpdatedBy": null,  
            "createdOnTimestampUTC": "0001-01-01T00:00:00Z",  
            "lastUpdateTimestampUTC": "0001-01-01T00:00:00Z",  
            "passedDevices": 0,  
            "totalDevices": 10  
        }  
     ]  
}  
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik temellerini dışarı aktarma değerlendirmesi](export-security-baseline-assessment.md)
- [Güvenlik temelleri değerlendirme yapılandırmalarını alma](get-security-baselines-assessment-configurations.md)
