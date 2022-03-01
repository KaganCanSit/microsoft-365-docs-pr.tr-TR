---
title: Uç Nokta API sürüm notları için Microsoft Defender
description: Uç nokta API'leri kümesi için Microsoft Defender'da yapılan güncelleştirmelerin sürüm notları.
keywords: Uç Nokta API sürüm notları için Microsoft Defender, mde, API'ler, Uç Nokta API için Microsoft Defender, güncelleştirmeler, notlar, sürüm
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
ms.openlocfilehash: 2c34add5968021d6a31bffc80ec16e0ebed9baf0
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997168"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>Uç Nokta API sürüm notları için Microsoft Defender

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Aşağıdaki bilgilerde, Uç Nokta API'leri için Microsoft Defender'da yapılan güncelleştirmeler ve bunların hangi tarihlerde olduğu listelemektedir.

> [!TIP]
> RSS akışı: Bu sayfa güncelleştirildiğinde, akış okuyucuya aşağıdaki URL'yi kopyalayıp yapıştırarak bilgi alın:
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>Sürüm notları - en yeniden eskiye (d.mm.yyyy)

### <a name="06102021"></a>06.10.2021

- Yeni Dışarı aktarma değerlendirme API yöntemi - _Delta Dışarı aktarma yazılım açıkları değerlendirmesi (JSON yanıtı) Cihaz_ başına değerlendirme [yöntemlerini ve özelliklerini dışarı aktarın](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- Yeni API Cihaz [başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma eklendi](get-assessment-methods-properties.md).

### <a name="03052021"></a>03.05.2021

- Yeni API eklendi: [Düzeltme etkinliği yöntemleri ve özellikleri](get-remediation-methods-properties.md).

### <a name="10022021"></a>10.02.2021

- Yeni API eklendi: [Toplu güncelleştirme uyarıları](batch-update-alerts.md).

### <a name="25012021"></a>25.01.2021

- Dakika başına 15 [-](run-advanced-query-api.md) 45 istek arasında Gelişmiş Av API'si için güncelleştirilmiş fiyat sınırlamaları.

### <a name="21012021"></a>21.01.2021

- Yeni API eklendi: [Cihazları etikete göre bulun](machine-tags.md).
- Yeni API eklendi: [İçeri Aktarma Göstergeleri](import-ti-indicators.md).

### <a name="03012021"></a>03.01.2021

- Güncelleştirilmiş Uyarı kanıtı: ***detectionStatus** _, _*_parentProcessFilePath ve_*_ _ *_parentProcessFileName_** özellikleri eklendi.
- [Güncelleştirilmiş Uyarı varlığı](alerts.md): ***özelId özelliği*** eklendi.

### <a name="15122020"></a>15.12.2020

- [Güncelleştirilmiş Cihaz](machine.md) varlığı: ***IpInterfaces*** listesi eklendi. Bkz [. Cihazları listele](get-machines.md).

### <a name="04112020"></a>04.11.2020

- Yeni API eklendi: [Cihaz değerini ayarla](set-device-value.md).
- [Güncelleştirilmiş Cihaz](machine.md) varlığı: ***deviceValue özelliği*** eklendi.

### <a name="01092020"></a>01.09.2020

- Uyarı varlığını ilişkili Kanıtlarla birlikte genişletmek için seçenek eklendi. Liste [Uyarıları'ne bakın](get-alerts.md).
