---
title: Makineyle ilgili uyarılar API'sini al
description: Makineyle ilgili uyarılar API'sini nasıl kullanabileceğiniz hakkında bilgi edinin. Bu API, Uç Nokta için Microsoft Defender'da belirli bir cihazla ilgili tüm uyarıları alamanizi sağlar.
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, cihazlar, ilgili, uyarılar
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
ms.openlocfilehash: 49cc0fca3ae7617b86ab079daace92eb3790db94
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997161"
---
# <a name="get-machine-related-alerts--api"></a>Makineyle ilgili uyarılar API'sini al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Belirli bir [cihazla ilgili](alerts.md) tüm Uyarıları verir.

## <a name="limitations"></a>Sınırlamalar

1. Yapılandırılmış bekletme sürenize göre en son güncelleştirilen cihazlarda sorgu kullanabilirsiniz.
2. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alert.Read.All|'Tüm uyarıları oku'
Uygulama|Alert.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı) | Alert.Read | 'Uyarıları oku'
Temsilcili (iş veya okul hesabı) | Alert.ReadWrite | 'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle'. İzinler hakkında daha fazla bilgi için bkz [. Rolleri oluşturma ve yönetme](user-roles.md).
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir. Cihaz grubu ayarları hakkında daha fazla bilgi için bkz. [Cihaz grupları oluşturma ve yönetme](machine-groups.md).

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/{id}/alerts
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve cihaz varsa: Gövdede uyarı varlıklarının listesiyle birlikte 200 Tamam.[](alerts.md) Cihaz bulunamadı: 404 Bulunamadı.
