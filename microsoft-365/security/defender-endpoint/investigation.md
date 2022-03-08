---
title: araştırma kaynak türü
description: Uç Nokta Soruşturma varlığı için Microsoft Defender.
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, uyarılar, soruşturmalar
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1749404942b42778ecde99417a8e3501c7c4f4cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327231"
---
# <a name="investigation-resource-type"></a>araştırma kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Uç Nokta için Defender'da bir Otomatik Araştırma varlıklarını temsil etme.

Daha fazla bilgi için bkz [. Otomatik soruşturmalara genel bakış](automated-investigations.md).

## <a name="methods"></a>Yöntemler

Yöntem|İade Türü|Açıklama
:---|:---|:---
[Liste Soruşturmaları](get-investigation-collection.md)|Araştırma koleksiyonu|Araştırma koleksiyonunu al
[Tek araştırmayı al](get-investigation-object.md)|İnceleme varlığı|Tek Araştırma varlığı alır.
[Araştırmayı Başlat](initiate-autoir-investigation.md)|İnceleme varlığı|Bir cihazda Araştırma'ya başlar.

## <a name="properties"></a>Özellikler

Özellik|Tür|Açıklama
:---|:---|:---
Kimlik|Dize|Araştırma varlıklarının kimliği. 
startTime|DateTime Nullable|Araştırmanın oluşturulma tarihi ve saati.
endTime|DateTime Nullable|Araştırmanın tamamıldığı tarih ve saat.
cancelledBy|Dize|Bu araştırmayı iptal edilen kullanıcının/uygulamanın kimliği.
Durum|Enum|Araştırmanın geçerli durumu. Olası değerler şöyledir: 'Bilinmiyor', 'Sonlandırıldı', 'Başarıyla Gönderildi', 'Silindi', 'Başarısız', 'Kısmen Kuyruğa Alındı', 'Çalışıyor', 'PendingApproval', 'PendingResource', 'PartialLyInvestigated', 'TerminatedByUser', 'TerminatedBySystem', 'Kuyruğa Alındı', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.
statusDetails|Dize|Araştırmanın durumu hakkında ek bilgi.
machineId|Dize|Araştırmanın yürütül olduğu cihazın kimliği.
computerDnsName|Dize|Araştırmanın yürütül olduğu cihazın adı.
triggeringAlertId|Dize|Araştırmayı tetikleyen uyarının kimliği.

## <a name="json-representation"></a>Json gösterimi

```json
{
    "id": "63004",
    "startTime": "2020-01-06T13:05:15Z",
    "endTime": null,
    "state": "Running",
    "cancelledBy": null,
    "statusDetails": null,
    "machineId": "e828a0624ed33f919db541065190d2f75e50a071",
    "computerDnsName": "desktop-test123",
    "triggeringAlertId": "da637139127150012465_1011995739"
}
```
