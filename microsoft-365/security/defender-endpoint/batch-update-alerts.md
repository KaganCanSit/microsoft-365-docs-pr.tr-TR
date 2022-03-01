---
title: Toplu Güncelleştirme Uyarı Varlıkları API'si
description: Bu API'yi kullanarak bir toplu işlemde Uç Nokta uyarıları için Microsoft Defender'ı güncelleştirmeyi öğrenin. Durumu, belirlemeyi, sınıflandırmayı ve atanan özellikleri güncelleştirebilirsiniz.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alert, information, id
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a2d695a2b406d4850f0e9896af3ec3b2aede8870
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997167"
---
# <a name="batch-update-alerts"></a>Toplu güncelleştirme uyarıları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API açıklaması

Var olan bir Grup Uyarı'nın [özelliklerini güncelleştirme](alerts.md).

Açıklamanın **gönderimi** özelliklerle birlikte veya güncelleştirmeden kullanılabilir.

En iyi özellikler: `status`, ve `classification` `determination``assignedTo`.

## <a name="limitations"></a>Sınırlamalar

1. API'de bulunan uyarıları güncelleştirebilirsiniz. Daha [fazla bilgi için Liste Uyarıları'ne](get-alerts.md) bakın.
2. Bu API için fiyat sınırlamaları, dakikada 10 çağrı ve saatte 500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü | İzin | İzin görünen adı
:---|:---|:---
Uygulama | Alert.ReadWrite.All | 'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı) | Alert.ReadWrite | 'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Uyarı soruşturması' (Daha fazla bilgi için bkz [.](user-roles.md) Rol oluşturma ve yönetme)
> - Kullanıcının, cihaz grubu ayarlarına göre uyarıyla ilişkilendirilmiş cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [grupları oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.
İçerik Türü | Dize | application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, güncelleştirilacak uyarı kimliklerini ve bu uyarılar için güncelleştirmek istediğiniz ilgili alanların değerlerini girin.

İstek gövdesine dahil edilen mevcut özellikler, önceki değerlerini korumaz veya diğer özellik değerlerinde yapılan değişikliklere bağlı olarak yeniden hesaplanır.

En iyi performans için değişmemiş olan mevcut değerleri içerme olmaması gerekir.

Özellik | Tür | Açıklama
:---|:---|:---
alertIds | ListString&lt;&gt;| Güncelleştirilen uyarıların kimliklerinin listesi. **Gerekli**
durum | Dize | Belirtilen uyarıların güncelleştirilmiş durumunu belirtir. Özellik değerleri şöyledir: 'Yeni', 'Çıkış' ve 'Çözümlendi'.
atanan | Dize | Belirtilen uyarıların sahibi
sınıflandırma | Dize | Belirtilen uyarıların belirtimlerini belirtir. Özellik değerleri şöyledir: 'Bilinmiyor', 'YanlışPositive', 'TruePositive'. 
karartma | Dize | Belirtilen uyarıların belirlenmesini belirtir. Özellik değerleri şöyledir: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
açıklama | Dize | Belirtilen uyarılara eklenecek açıklama.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem boş bir yanıt gövdesiyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
