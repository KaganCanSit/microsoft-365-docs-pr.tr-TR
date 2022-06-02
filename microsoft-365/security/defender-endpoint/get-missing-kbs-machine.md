---
title: Cihaz kimliğine göre eksik KB'leri alma
description: Cihaz kimliğine göre eksik güvenlik güncelleştirmelerini alır
keywords: apis, graph api, desteklenen API'ler, get, list, file, information, device id, threat & güvenlik açığı yönetimi api, Uç Nokta için Microsoft Defender tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4a570851263b6a52193353e2c229e2df47b677e3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840331"
---
# <a name="get-missing-kbs-by-device-id"></a>Cihaz kimliğine göre eksik KB'leri alma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cihaz kimliğine göre eksik KB'leri (güvenlik güncelleştirmeleri) alır

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/{machineId}/getmissingkbs
```
## <a name="permissions"></a>İzinler

Bu API'yi çağırmak için aşağıdaki izin gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender API'leri kullanma](apis-intro.md).

İzin türü | Izni | İzin görünen adı
:---|:---|:---
Uygulama | Software.Read.All | 'Tehdit ve Güvenlik Açığı Yönetim Yazılımı bilgilerini okuyun'

## <a name="request-header"></a>İstek üst bilgisi

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem 200 Tamam döndürür ve belirtilen cihazda gövdede kb verileri eksiktir.

## <a name="example"></a>Örnek

### <a name="request"></a>Istek

burada isteğin bir örneği verilmiştir.

```http
GET https://api.securitycenter.microsoft.com/api/machines/2339ad14a01bd0299afb93dfa2550136057bff96/getmissingkbs 
```

### <a name="response"></a>Yanıt

Yanıtın bir örneği aşağıda verilmiştir.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
        {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "windows_10",
                "edge",
                "internet_explorer"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 1,
            "cveAddressed": 97
        }
        ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığı yazılım envanteri](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
