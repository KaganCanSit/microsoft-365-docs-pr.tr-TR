---
title: Microsoft 365 Defender API'leri ve olayları kaynak türü olarak atama
description: Olay kaynağı türü yöntemleri ve özellikleri hakkında bilgi Microsoft 365 Defender
keywords: olay, olaylar, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a1a3f119e0aafe75b58df9c2330a950d5ab31ead
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010738"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender API'sini ve olayları kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Olay [,](incidents-overview.md) bir saldırıyı açıklayan ilgili uyarıların koleksiyonudur. Farklı varlıklardan gelen olaylar otomatik olarak bu kuruluşlar tarafından Microsoft 365 Defender. Olayları API'sini, kuruluş olaylarına ve ilgili uyarılara programlı olarak erişmek için kullanabilirsiniz.

## <a name="quotas-and-resource-allocation"></a>Kotalar ve kaynak ayırma

Dakikada 50 veya saatte 1500 çağrı için istekte bulundurarak bu istekleri yanıtlayabiliyoruz. Her yöntemin kendi kotaları da vardır. Yönteme özgü kotalar hakkında daha fazla bilgi için, kullanmak istediğiniz yöntemin ilgili makalesine bakın.

HTTP `429` yanıt kodu, gönderilen istek sayısıyla veya en çok çalışan süreyle bir kotaya ulaştığını gösterir. Yanıt gövdesi, ulaştığınız kota sıfırlanacak kadar süreyi içerecektir.

## <a name="permissions"></a>İzinler

Olaylar API'si, her bir yöntemi için farklı tür izinler gerektirir. Gerekli izinler hakkında daha fazla bilgi için, ilgili yöntemin makalesine bakın.

## <a name="methods"></a>Yöntemler

Yöntem | İade Türü | Açıklama
-|-|-
[Olayları listele](api-list-incidents.md) | [Olay](api-incident.md) listesi | Olayın listesini al.
[Olayı güncelleştir](api-update-incidents.md) | [Olay](api-incident.md) | Belirli bir olayı güncelleştirme.
[Olay al](api-get-incident.md) | [Olay](api-incident.md) | Tek bir olayla ilgili.

## <a name="request-body-response-and-examples"></a>Gövde, yanıt ve örnekler isteği

İstek oluşturma veya yanıtı ayrıştırma ve pratik örnekler için daha ayrıntılı bilgi için ilgili yöntem makalelerine bakın.

## <a name="common-properties"></a>Ortak özellikler

Özellik | Tür | Açıklama
-|-|-
olaykimlikkim | long | Olay benzersiz kimliği.
redirectIncidentId | nullable long | Geçerli Olayın birleştirilen Olay Kimliği.
incidentName | dize | Olayın adı.
createdTime | DateTimeOffset | Olayın oluşturulmuş olduğu tarih ve saat (UTC).
lastUpdateTime | DateTimeOffset | Olayın son güncelleştirme tarihi ve saati (UTC).
atanan | dize | Olayın sahibi.
önem derecesi | Enum | Olayın Önem Derecesi. Olası değerler: ```UnSpecified```, ```Informational```, ```Low```, ```Medium```ve ```High```.
durum | Enum | Olayın geçerli durumunu belirtir. Olası değerler: ```Active```, ```InProgress```, ```Resolved```ve ```Redirected```.
sınıflandırma | Enum | Olayın belirtimi. Olası değerler: ```Unknown```, ```FalsePositive```, . ```TruePositive```
karartma | Enum | Olayın belirlenmesini belirtir. Olası değerler şöyledir: ```NotAvailable```, ```Malware``````Apt```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware```. ```Other```
etiketler | dize Listesi | Olay etiketlerinin listesi.
açıklamalar | Olay açıklamalarının listesi | Olay Açıklaması nesnesi şunları içerir: açıklama dizesi, createdBy dizesi ve createTime tarih saati.
uyarılar | Uyarı Listesi | İlgili uyarıların listesi. Olay listesi API [belgeleri örneklerine](api-list-incidents.md) bakın.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Olaylara genel bakış](incidents-overview.md)
- [Olay listesi API'si](api-list-incidents.md)
- [Olay API'sini güncelleştir](api-update-incidents.md)
