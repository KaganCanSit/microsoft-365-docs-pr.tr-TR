---
title: RBAC makine grupları koleksiyonu API'sini edinin
description: Uç Nokta için Microsoft Defender'da RBAC cihaz grupları koleksiyonunu almak için KB koleksiyonu alma API'sini nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'si, desteklenen api'ler, get, RBAC, grup
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 10/07/2018
ms.custom: api
ms.openlocfilehash: 699a7e2738f1e0c89977bd152832f45935a06387
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997475"
---
# <a name="get-kb-collection-api"></a>KB koleksiyonu API'sini edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

RBAC cihaz grupları koleksiyonunu verir.

## <a name="permissions"></a>İzinler

Kullanıcı için okuma izinleri gerekir.

## <a name="http-request"></a>HTTP isteği

```http
GET /testwdatppreview/machinegroups
```

## <a name="request-headers"></a>Üstbilgi isteği

Üst bilgi|Değer
:---|:---
Yetkilendirme | Taşıyıcı {token}. **Gerekli**.
İçerik türü | application/json

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa - 200 Tamam.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:
Alan kimliği, cihaz grup **kimliğini ve** cihaz bilgilerinde **alan rbacGroupId alanına** eşittir.
Grubu **olmayan alan** , herhangi bir gruba atanmamış tüm cihazlar için yalnızca bir grup için doğrudur. Bu grubun adı her zamanki gibi "UnassignedGroup" şeklindedir.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineGroups",
    "@odata.count":7,
    "value":[
        {
            "id":86,
            "name":"UnassignedGroup",
            "description":"",
            "ungrouped":true},
        ...
}
```
