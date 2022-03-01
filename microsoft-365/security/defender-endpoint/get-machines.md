---
title: Liste makineleri API'si
description: Uç nokta bulutu için Microsoft Defender ile iletişim kuran makine koleksiyonunu almak için Liste makineleri API'sini kullanmayı öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, cihazlar
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection: M365-security-compliance
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6e522f2baac234097ed75d26eb1427719211a7de
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996470"
---
# <a name="list-machines-api"></a>Liste makineleri API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Uç nokta [bulutu için Microsoft](machine.md) Defender ile iletişim kuran bir Makine koleksiyonunu sağlar.

[OData V4 sorgularını destekler](https://www.odata.org/documentation/).

OData'nın `$filter` sorgusu şu şekilde destekler: `computerDnsName`, `id`, `version`, `deviceValue`, `aadDeviceId`, `lastSeen``machineTags``exposureLevel`, `onboardingStatus`, ve . `lastIpAddress``healthStatus``osPlatform``riskScore` `rbacGroupId`
<br>```$stop``` maksimum değeri 10.000
<br>```$skip``` Uç Nokta için [Defender ile OData sorgularında örneklere bakın](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Sınırlamalar

1. Yapılandırılmış bekletme sürenize göre en son görülen cihazları edinebilirsiniz.
2. En büyük sayfa boyutu 10.000'tir.
3. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır. 

## <a name="permissions"></a>İzinler

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Machine.Read.All|'Tüm makine profillerini oku'
Uygulama|Machine.ReadWrite.All|'Tüm makine bilgilerini okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Machine.Read|'Makine bilgilerini oku'
Temsilcili (iş veya okul hesabı)|Machine.ReadWrite|'Makine bilgilerini okuma ve yazma'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)
> - Yanıt, cihaz grubu ayarlarına göre kullanıcının erişim iznine sahip olduğu cihazları içerir (daha fazla bilgi için bkz. Cihaz [grupları oluşturma ve](machine-groups.md) yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve makine varsa - Gövdede makine varlıklarının listesiyle birlikte 200 Tamam.[](machine.md) Son makine yoksa - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Machines",
    "value": [
        {
            "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
            "computerDnsName": "mymachine1.contoso.com",
            "firstSeen": "2018-08-02T14:55:03.7791856Z",
            "lastSeen": "2018-08-02T14:55:03.7791856Z",
            "osPlatform": "Windows10" "Windows11",
            "version": "1709",
            "osProcessor": "x64",
            "lastIpAddress": "172.17.230.209",
            "lastExternalIpAddress": "167.220.196.71",
            "osBuild": 18209,
            "healthStatus": "Active",
            "rbacGroupId": 140,
            "rbacGroupName": "The-A-Team",
            "riskScore": "Low",
            "exposureLevel": "Medium",
            "isAadJoined": true,
            "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
            "machineTags": [ "test tag 1", "test tag 2" ]
        }
        ...
    ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta için Microsoft Defender ile OData sorguları](exposed-apis-odata-samples.md)
