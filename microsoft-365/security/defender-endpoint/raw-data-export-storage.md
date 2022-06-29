---
title: Depolama hesabınıza Uç Nokta için Microsoft Defender olayları akışla aktarma
description: Depolama hesabınıza Gelişmiş Tehdit Avcılığı olaylarının akışını yapmak için Uç Nokta için Microsoft Defender yapılandırmayı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Event Hubs, Azure depolama, depolama hesabı, Gelişmiş Tehdit Avcılığı, ham veri paylaşımı
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
ms.openlocfilehash: c94830e4f9dbfe16a8dfafba35aecb5a36efddf5
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493453"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Depolama hesabınıza Gelişmiş Tehdit Avcılığı olaylarının akışını yapmak için Uç Nokta için Microsoft Defender yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracınızda bir [Depolama hesabı](/azure/storage/common/storage-account-overview) oluşturun.

2. [Azure kiracınızda](https://ms.portal.azure.com/) oturum açın, **Aboneliğiniz > Kaynak Sağlayıcılarınız > Abonelikler'e gidin > Microsoft.insights'a kaydolun**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. ***Genel Yönetici** _ veya _*_Güvenlik Yöneticisi_** olarak [Microsoft 365 Defender](https://security.microsoft.com) oturum açın.

2. Microsoft 365 Defender'de [Veri dışarı aktarma ayarları sayfasına](https://security.microsoft.com/settings/mtp_settings/raw_data_export) gidin.

3. **Veri dışarı aktarma ayarları ekle'ye** tıklayın.

4. Yeni ayarlarınız için bir ad seçin.

5. **Olayları Azure Depolama'ya ilet'i** seçin.

6. **Depolama Hesabı Kaynak Kimliğinizi** yazın. **Depolama Hesabı Kaynak Kimliğinizi** almak için [Azure portal özellikler sekmesindeki](https://ms.portal.azure.com/) \> \> Depolama hesabı sayfanıza gidin ve **Depolama hesabı kaynak kimliği** altındaki metni kopyalayın:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="Kaynak kimliği1 olan Event Hubs" lightbox="images/storage-account-resource-id.png":::

7. Akış yapmak istediğiniz olayları seçin ve **Kaydet'e** tıklayın.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Depolama hesabındaki olayların şeması

- Her olay türü için bir blob kapsayıcısı oluşturulur:

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="Kaynak kimliği2 olan Event Hubs" lightbox="images/storage-account-event-schema.png":::

- Blobdaki her satırın şeması aşağıdaki JSON'dır:

  ```json
  {
    "time": "<The time WDATP received the event>"
    "tenantId": "<Your tenant ID>"
    "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
    "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Her blob birden çok satır içerir.

- Her satır olay adını, Uç Nokta için Defender'ın olayı aldığı zamanı, ait olduğu kiracıyı (yalnızca kiracınızdan olayları alırsınız) ve JSON biçimindeki olayı "properties" adlı bir özellikte içerir.

- Uç Nokta için Microsoft Defender olaylarının şeması hakkında daha fazla bilgi için bkz. [Gelişmiş Avcılık'a genel bakış](advanced-hunting-overview.md).

- Gelişmiş Avcılık'ta **DeviceInfo** tablosunda, cihazın grubunu içeren **MachineGroup** adlı bir sütun bulunur. Burada her etkinlik bu sütunla da donatılacaktır. Daha fazla bilgi için bkz [. Cihaz Grupları](machine-groups.md) .

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özelliklerimizin veri türlerini almak için aşağıdakileri yapın:

1. [Microsoft 365 Defender](https://security.microsoft.com) oturum açın ve [Gelişmiş Tehdit Avcılığı sayfasına](https://security.microsoft.com/hunting-package) gidin.

2. Her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayına bir örnek aşağıda verilmiştir:

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="Kaynak kimliği3 olan Event Hubs" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Avcılık'a Genel Bakış](advanced-hunting-overview.md)
- [Uç Nokta için Microsoft Defender Akış API'si](raw-data-export.md)
- [Azure depolama hesabınıza Uç Nokta için Microsoft Defender olayları akışla aktarma](raw-data-export-storage.md)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)
