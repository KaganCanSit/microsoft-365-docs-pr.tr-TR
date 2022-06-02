---
title: Yüklü yazılımı al
description: Belirli bir cihaz kimliğiyle ilgili yüklü yazılım koleksiyonunu alır.
keywords: apis, graph api, desteklenen API'ler, get, list, file, information, software inventory, installed software per device, threat & güvenlik açığı yönetimi API, Uç Nokta için Microsoft Defender tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 97aa4a668306c4790dcd42c046ba4bf3a04bcf51
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840419"
---
# <a name="get-installed-software"></a>Yüklü yazılımı al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Belirli bir cihaz kimliğiyle ilgili yüklü yazılım koleksiyonunu alır.

## <a name="permissions"></a>İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek için bkz[. Uç Nokta için Microsoft Defender API'leri kullanma](apis-intro.md)

İzin türü|Izni|İzin görünen adı
:---|:---|:---
Uygulama |Software.Read.All|'Tehdit ve Güvenlik Açığı Yönetim Yazılımı bilgilerini okuyun'
Temsilci (iş veya okul hesabı)|Software.Read|'Tehdit ve Güvenlik Açığı Yönetim Yazılımı bilgilerini okuyun'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/{machineId}/software
```

## <a name="request-headers"></a>İstek üst bilgileri

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem gövdede yüklü yazılım bilgileriyle 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği verilmiştir.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/software
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği aşağıda verilmiştir.

```json
{
"@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
"value": [
        {
"id": "microsoft-_-internet_explorer",
"name": "internet_explorer",
"vendor": "microsoft",
"weaknesses": 67,
"publicExploit": true,
"activeAlert": false,
"exposedMachines": 42115,
"impactScore": 46.2037163
        }
    ]
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığı yazılım envanteri](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
