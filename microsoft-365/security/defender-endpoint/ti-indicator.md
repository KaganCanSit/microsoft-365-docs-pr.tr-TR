---
title: Gösterge kaynağı türü
description: Varlık ayrıntılarını belirtin ve Uç Nokta için Microsoft Defender'ı kullanarak göstergenin sona erme tarihini tanımlayın.
keywords: api'ler, desteklenen api'ler, get, TiIndicator, Indicator, recent
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
ms.openlocfilehash: 8e8660574f65d614bacfe705d7fad19e39d501a6
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997116"
---
# <a name="indicator-resource-type"></a>Gösterge kaynağı türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- Portalda [ilgili Göstergeler](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) sayfasına bakın.

Yöntem|İade Türü|Açıklama
:---|:---|:---
[Liste Göstergeleri](get-ti-indicators-collection.md)|[Gösterge](ti-indicator.md) Koleksiyon|Liste [Göstergesi](ti-indicator.md) varlıkları.
[Gönderme Göstergesi](post-ti-indicator.md)|[Gösterge](ti-indicator.md)|Gösterge varlıkını gönderin [veya](ti-indicator.md) güncelleştirin.
[İçeri Aktarma Göstergeleri](import-ti-indicators.md)|[Gösterge](ti-indicator.md) Koleksiyon|Gösterge varlıklarını [gönderin veya](ti-indicator.md) güncelleştirin.
[Silme Göstergesi](delete-ti-indicator-by-id.md)|İçerik Yok|Gösterge [varlıkını](ti-indicator.md) siler.

## <a name="properties"></a>Özellikler

Özellik|Tür|Açıklama
:---|:---|:---
id|Dize|Gösterge varlık [kimliği](ti-indicator.md) .
indicatorValue|Dize|Gösterge [değeridir](ti-indicator.md).
indicatorType|Enum|Göstergenin türü. Olası değerler şöyledir: "FileSha1", "FileSha256", "FileMd5", "CertificateThumbprint", "IpAddress", "DomainName" ve "Url".
uygulama|Dize|Göstergeyle ilişkili uygulama.
eylem|Enum|Gösterge kuruluşta keşfedilecekse, alınacak eylem. Olası değerler şöyledir: "Uyarı", "Engelle", "Denetim", "Uyarı", "AlertAndBlock", "BlockAndRemediate" ve "İzin Verildi".
|externalID|Dize|Müşterinin özel korelasyon isteğiyle gönderebn olduğu kimlik.|
sourceType|Enum|"Kullanıcı", kullanıcı tarafından oluşturulan Gösterge (örneğin portaldan), API aracılığıyla otomatik uygulama kullanılarak gönderilme durumuna karşı "AadApp".
createdBySource|dize|Göstergeyi gönderilen kullanıcının/uygulamanın adı.
createdBy|Dize|Göstergeyi gönderilen kullanıcının/uygulamanın benzersiz kimliği.
lastUpdatedBy|Dize|Göstergeyi en son güncelleştirilen kullanıcının/uygulamanın kimliği.
creationTimeDateTimeUtc|DateTimeOffset|Göstergenin oluşturulma tarihi ve saati.
expirationTime|DateTimeOffset|Göstergenin sona erme zamanıdır.
lastUpdateTime|DateTimeOffset|Göstergenin en son güncelleştirilmiş zamanı.
önem derecesi|Enum|Göstergenin önem derecesidir. olası değerler şöyledir: "Bilgilendirme", "Düşük", "Orta" ve "Yüksek".
başlık|Dize|Gösterge başlığı.
açıklama|Dize|Göstergenin açıklaması.
recommendedActions|Dize|Gösterge için önerilen eylemler.
rbacGroupNames|Dize listesi|Göstergenin açık olduğu ve etkin olduğu RBAC cihaz grup adları. Tüm cihazlara açık olduğu durumda boş liste.
rbacGroupIds|Dize listesi|Göstergenin açık olduğu ve etkin olduğu RBAC cihaz grup kimliğidir. Tüm cihazlara açık olduğu durumda boş liste.
generateAlert|Enum|**Uyarı** oluşturma gerekirse Doğru, bu **gösterge** bir uyarı oluşturmazsa False.

## <a name="indicator-types"></a>Gösterge Türleri

API tarafından desteklenen gösterge eylem türleri:

- İzin verildi
- Denetim
- Engelle
- BlockAndRemediate
- Uyar (Yalnızca Bulut Uygulamaları için Defender)

Yanıt eylem türlerinin açıklaması hakkında daha fazla bilgi için bkz. [Gösterge oluşturma](manage-indicators.md).

> [!Note]
>
> Önceki yanıt eylemleri (AlertAndBlock ve Uyarı) Ocak 2022'ye kadar desteklenecek. Bu tarihten sonra, tüm müşterilerin yukarıda listelenen eylem türlerinden birini kullanmaları gerekir.

## <a name="json-representation"></a>Json gösterimi

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
