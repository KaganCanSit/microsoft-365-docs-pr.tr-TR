---
title: IP istatistikleri API'sini edinin
description: Uç Nokta için Microsoft Defender'ı kullanarak IP'niz için en son istatistikleri elde edin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, al, ip, istatistikler, yaygınlık
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
ms.openlocfilehash: a98b78e85956d49c3b7d7e389882e017dcede3a4
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997131"
---
# <a name="get-ip-statistics-api"></a>IP istatistikleri API'sini edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması
Verilen IP'nin istatistiklerini alınır.

## <a name="limitations"></a>Sınırlamalar
1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.
2. Geri Saat değerleri için En Fazla Değer 720 Saat(30 gün) olur.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|ip.Read.All|'IP adresi profillerini oku'
Temsilcili (iş veya okul hesabı)|ip.Read.All|'IP adresi profillerini oku'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET /api/ips/{ip}/stats
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-uri-parameters"></a>URI parametreleri isteği

Name|Tür|Açıklama
:---|:---|:---
lookBackHours|Int32|İstatistikleri almak için geri arama saatlerini tanımlar. Varsayılan değer 30 gündür. **İsteğe bağlı**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve ip varsa - Gövdede istatistiksel veriler ile 200 Tamam. IP geçerlidir ama yoktur - organizationPrevalence 0, IP geçersiz - HTTP 400.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/stats?lookBackHours=48
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgIPStats",
    "ipAddress": "10.209.67.177",
    "organizationPrevalence": 63515,
    "orgFirstSeen": "2017-07-30T13:36:06Z",
    "orgLastSeen": "2017-08-29T13:32:59Z"
}
```

|Name|Açıklama|
|---|---|
|Kuruluş yaygınlık|bu IP'ye ağ bağlantısını açan cihazların ayrı sayısıdır.|
|İlk kez görülen kuruluş|kuruluşta bu IP'nin ilk bağlantısı.|
|En son görülen kuruluş|kuruluşta bu IP'nin son bağlantısı.|

> [!NOTE]
> Bu istatistik bilgileri, son 30 günlük verilere dayalıdır.
