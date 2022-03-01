---
title: Makine varlık API'sini güncelleştirme
description: Bu API'yi kullanarak makine etiketlerini güncelleştirme hakkında bilgi edinin. Etiketler ve cihaz değeri özelliklerini güncelleştirebilirsiniz.
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
ms.openlocfilehash: 77876024faa7452ff284e30a587e72855068cc98
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996528"
---
# <a name="update-machine"></a>Makine güncelleştirme 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Mevcut Makine özelliklerini [güncelleştirme](machine.md).

En iyi özellikler: `machineTags` ve `deviceValue`.

## <a name="limitations"></a>Sınırlamalar

1. API'de bulunan makineleri güncelleştirebilirsiniz. 
2. Güncelleştirme makinesi etiketleri yalnızca etiket koleksiyonunun sonuna ekler. Etiketler varsa, gövdeye etiketler koleksiyonunda yer alıyor olması gerekir.
3. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Machine.ReadWrite.All|'Tüm makineler için makine bilgilerini okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Machine.ReadWrite|'Makine bilgilerini okuma ve yazma'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Uyarılar soruşturması'. Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md).
> - Kullanıcının, cihaz grubu ayarlarına göre uyarıyla ilişkilendirilmiş cihaza erişimi olması gerekir. Daha fazla bilgi için bkz [. Cihaz grupları oluşturma ve yönetme](machine-groups.md).

## <a name="http-request"></a>HTTP isteği

```http
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|Dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde güncelleştirilmiş olması gereken ilgili alanların değerlerini girin.

İstek gövdesine dahil edilen mevcut özellikler, önceki değerlerini korumaz veya diğer özellik değerlerinde yapılan değişikliklere bağlı olarak yeniden hesaplanır.

En iyi performans için değişmeden var olan değerleri dahil etmeyebilirsiniz.

Özellik|Tür|Açıklama
:---|:---|:---
makine Etiketleri|Dize koleksiyonu|Makine [etiketleri](machine.md) kümesi.
deviceValue|Nullable Enum|Cihazın [değeridir](tvm-assign-device-value.md). Olası değerler şöyledir: 'Normal', 'Düşük' ve 'Yüksek'.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem 200 Tamam'ı ve güncelleştirilmiş [](machine.md) özelliklerin yanıt gövdesinde yer alan makine varlığı döndürür.

Gövdede makine etiketleri koleksiyonu mevcut makine etiketlerini içeriyorsa - tüm etiketleri istek gövdesinde sağlanan etiketlerle değiştirir.

Belirtilen kimliğin bulunduğu makine bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
