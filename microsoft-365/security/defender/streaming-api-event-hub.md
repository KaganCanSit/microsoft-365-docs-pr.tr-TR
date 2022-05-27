---
title: Microsoft 365 Defender olaylarını Azure Event Hubs akışla aktar
description: Gelişmiş Tehdit Avcılığı olaylarını Event Hubs'ınıza akışla aktaracak Microsoft 365 Defender yapılandırmayı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Azure Event Hubs, Azure depolama, depolama hesabı, Gelişmiş Tehdit Avcılığı, ham veri paylaşımı
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 9cae28cc69d67bb18058e2c81cd8235ffce79997
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754410"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Gelişmiş Tehdit Avcılığı olaylarını Azure Olay Hub'ınıza akışla aktaracak şekilde Microsoft 365 Defender yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="prerequisites"></a>Önkoşullar

Event Hubs'a veri akışı yapmak için Microsoft 365 Defender yapılandırmadan önce aşağıdaki önkoşulların karşılandığından emin olun:

1. Event Hubs oluşturma (bilgi için bkz. [Event Hubs'ı ayarlama](configure-event-hub.md#set-up-event-hubs)).

2. Event Hubs Ad Alanı oluşturma (bilgi için bkz. [Event Hubs ad alanını ayarlama](configure-event-hub.md#set-up-event-hubs-namespace)).

3. Bu varlığın Event Hubs'a veri aktarabilmesi için **Katkıda Bulunan** ayrıcalıklarına sahip olan varlığa izinler ekleyin. İzin ekleme hakkında daha fazla bilgi için bkz. [İzin ekleme](configure-event-hub.md#add-permissions)

> [!NOTE]
> Akış API'si Event Hubs veya Azure Depolama Hesabı aracılığıyla tümleştirilebilir.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> ***Genel Yönetici** _ veya _*_Güvenlik Yöneticisi_** olarak oturum açın.

2. [Akış API'sinin ayarlar sayfasına](https://security.microsoft.com/settings/mtp_settings/raw_data_export) gidin.

3. **Ekle'ye** tıklayın.

4. Yeni ayarlarınız için bir ad seçin.

5. **Olayları Azure Olay Hub'ına ilet'i** seçin.

6. Olay verilerini tek bir Olay Hub'ına aktarmak mı yoksa her olay tablosunu Event Hubs ad alanınızdaki farklı bir Event Hubs'a aktarmak mı istediğinizi seçebilirsiniz.

7. Olay verilerini tek bir Olay Hub'ına aktarmak için **Olay Hub'ınızın adını** ve **Olay Hub'ı kaynak kimliğinizi** girin.

   **Olay Hub'ı kaynak kimliğinizi** almak için [Azure](https://ms.portal.azure.com/) > **Özellikler** sekmesindeki Azure Event Hubs ad alanı sayfanıza gidin > **Kaynak Kimliği** altındaki metni kopyalayın:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Olay Hub'ı kaynak kimliği" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. [Microsoft 365 Akış API'sindeki olay türlerinin destek durumunu gözden geçirmek için Olay akışı API'sinde Desteklenen Microsoft 365 Defender olay](supported-event-types.md) türleri'ne gidin.

9. Akış yapmak istediğiniz olayları seçin ve **Kaydet'e** tıklayın.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Azure Event Hub'daki olayların şeması

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft 365 Defender received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- Azure Event Hubs içindeki her Event Hubs iletisi kayıtların listesini içerir.

- Her kayıt olay adını, Microsoft 365 Defender olayı aldığı zamanı, ait olduğu kiracıyı (yalnızca kiracınızdan olayları alırsınız) ve olayı "**properties**" adlı bir özellikte JSON biçiminde içerir.

- Microsoft 365 Defender olaylarının şeması hakkında daha fazla bilgi için bkz[. Gelişmiş Avcılık'a genel bakış](advanced-hunting-overview.md).

- Gelişmiş Avcılık'ta **DeviceInfo** tablosunda, cihazın grubunu içeren **MachineGroup** adlı bir sütun bulunur. Burada her etkinlik bu sütunla da donatılacaktır.

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özelliklerinin veri türlerini almak için aşağıdaki adımları uygulayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> oturum açın ve [Gelişmiş Avcılık sayfasına](https://security.microsoft.com/hunting-package) gidin.

2. Her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayına bir örnek aşağıda verilmiştir:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Cihaz bilgileri için örnek sorgu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Avcılık'a Genel Bakış](advanced-hunting-overview.md)
- [akış API'sini Microsoft 365 Defender](streaming-api.md)
- [Olay akış API'sinde desteklenen Microsoft 365 Defender olay türleri](supported-event-types.md)
- [Microsoft 365 Defender olaylarını Azure depolama hesabınıza akışla aktarma](streaming-api-storage.md)
- [Azure Event Hubs belgeleri](/azure/event-hubs/)
- [Bağlantı sorunlarını giderme - Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
