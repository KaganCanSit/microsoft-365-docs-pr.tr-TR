---
title: Uygulama kısıtlama API'sini kaldır
description: Uygulamalardan yürütme kısıtlamasını kaldırmayla ilgili çağrılar oluşturmak için bu API'yi kullanın.
keywords: api'ler, grafik api'leri, desteklenen api'ler, cihazı yalıtımtan kaldırma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: c2fe35d73cd9abf3483c32067bf59334c6ad016b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997512"
---
# <a name="remove-app-restriction-api"></a>Uygulama kısıtlama API'sini kaldır

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Cihazda herhangi bir uygulamanın yürütülmesini etkinleştirin.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Tam yalıtım, 1703 Windows 10 cihazlarda kullanılabilir.
> - Seçmeli yalıtım en son sürüm Windows 10 1709 veya sonraki sürümlerde kullanılabilir.
> - Bir cihazı yorumlarken yalnızca belirli işlemlere ve hedeflere izin verilir. Bu nedenle, tam VPN hedeflerinin arkasındaki cihazlar cihaz yalıtılmış halde uç nokta için Microsoft Defender bulut hizmetine ulaşamayabilecektir. Uç Nokta için Microsoft Defender ve bulut tabanlı korumayla ilgili Microsoft Defender Virüsten Koruma bir VPN kullanılması önerilir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Machine.RestrictExecution|'Kod yürütmeyi kısıtla'
Temsilcili (iş veya okul hesabı)|Machine.RestrictExecution|'Kod yürütmeyi kısıtla'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Etkin düzeltme eylemleri' (Daha fazla bilgi için bkz [.](user-roles.md) Rol oluşturma ve yönetme)
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
:---|:---|:---
Açıklama ekleme|Dize|Eylemle ilişkilendirmek için açıklama. **Gerekli**.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde 201 - Yanıt kodu [ve Makine](machineaction.md) Eylemi oluşturuldu hata kodunu döndürür.

Aynı cihaz için uygulama kısıtlamalarını kaldırmak üzere birden çok API çağrısı gönderirsiniz, "Bekleyen makine eylemi" veya HTTP 400'ü "Eylem zaten devam ediyor" iletisiyle döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

Bir cihazda kod yürütmeyi kısıtlamak için bkz. [Uygulama yürütmeyi kısıtlama](restrict-code-execution.md).
