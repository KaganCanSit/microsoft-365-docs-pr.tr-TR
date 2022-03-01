---
title: Etki alanıyla ilgili uyarılar API'sini al
description: Uç Nokta için Microsoft Defender'da etki alanıyla ilgili uyarıları almak üzere Etki alanıyla ilgili uyarılar API'sini nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, al, etki alanı, ilgili, uyarılar
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
ms.openlocfilehash: b67b97ac115057b0e17bfd492e6330a13ee9e213
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996471"
---
# <a name="get-domain-related-alerts-api"></a>Etki alanıyla ilgili uyarılar API'sini al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Verilen bir etki alanı [adresiyle ilgili](alerts.md) Uyarılar koleksiyonunu sağlar.

## <a name="limitations"></a>Sınırlamalar

- Yapılandırılmış bekletme sürenize göre en son güncelleştirilen uyarılarda sorgu kullanabilirsiniz.
- Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alert.Read.All|'Tüm uyarıları oku'
Uygulama|Alert.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Alert.Read|'Uyarıları oku'
Temsilcili (iş veya okul hesabı)|Alert.ReadWrite|'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)
> - Yanıt, cihaz grubu ayarlarına göre kullanıcının erişimi olan cihazlarla ilişkilendirilmiş uyarıları içerir (daha fazla bilgi için bkz. Cihaz grupları [](machine-groups.md) oluşturma ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET /api/domains/{domain}/alerts
```

## <a name="request-headers"></a>Üstbilgi isteği

|Üst bilgi|Değer|
|---|---|
|Yetkilendirme|Dize|

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve etki alanı varsa - Uyarı varlıklarının listesiyle 200 [Tamam](alerts.md) . Etki alanı yoksa - Boş bir kümeyle 200 Tamam.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/domains/client.wns.windows.com/alerts
```
