---
title: Uyarı VARLıK API'sini güncelleştirme
description: Bu API'yi kullanarak Uç Nokta için Microsoft Defender uyarısını güncelleştirme hakkında bilgi edinin. Durumu, belirlemeyi, sınıflandırmayı ve atanan özellikleri güncelleştirebilirsiniz.
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4efe1460374350d054bbe6d19543c75454d7b5ce
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996074"
---
# <a name="update-alert"></a>Uyarıyı güncelleştir

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması
Var olan Uyarının özelliklerini [güncelleştirme](alerts.md).

Açıklamanın **gönderimi** özelliklerle birlikte veya güncelleştirmeden kullanılabilir.

En iyi özellikler: `status`, `determination`, ve `classification``assignedTo`.

## <a name="limitations"></a>Sınırlamalar

1. API'de bulunan uyarıları güncelleştirebilirsiniz. Daha fazla bilgi için bkz [. Liste Uyarıları](get-alerts.md).
2. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alerts.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Alert.ReadWrite|'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Uyarı soruşturması' (Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md) )
> - Kullanıcının, cihaz grubu ayarlarına göre uyarıyla ilişkilendirilmiş cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz grupları [oluşturma ve yönetme](machine-groups.md)

## <a name="http-request"></a>HTTP isteği

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|Dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde güncelleştirilmiş olması gereken ilgili alanların değerlerini girin.

İstek gövdesine dahil olmayan mevcut özellikler, önceki değerlerini korunur veya diğer özellik değerlerinde yapılan değişikliklere bağlı olarak yeniden hesaplanır.

En iyi performans için değişmeden var olan değerleri dahil etmeyebilirsiniz.

Özellik|Tür|Açıklama
:---|:---|:---
Durum|Dize|Uyarının geçerli durumunu belirtir. Özellik değerleri şöyledir: 'Yeni', 'Çıkış' ve 'Çözümlendi'.
atanan|Dize|Uyarının sahibi
Sınıflandırma|Dize|Uyarının belirtimlerini belirtir. Özellik değerleri şöyledir: 'Bilinmiyor', 'YanlışPositive', 'TruePositive'.
Karartma|Dize|Uyarıyı belirlemeyi belirtir. Özellik değerleri şöyledir: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
Açıklama ekleme|Dize|Uyarıya eklenecek açıklama.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem 200 Tamam'ı ve güncelleştirilmiş [](alerts.md) özellikleriyle yanıt gövdesine uyarı varlığı döndürür. Belirtilen kimlikle ilgili uyarı bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
PATCH https://api.securitycenter.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
