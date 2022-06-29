---
title: Depolama hesabınıza Microsoft 365 Defender olayları akışla aktarma
description: Depolama hesabınıza Gelişmiş Tehdit Avcılığı olaylarının akışını yapmak için Microsoft 365 Defender yapılandırmayı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Event Hubs, Azure depolama, depolama hesabı, Gelişmiş Tehdit Avcılığı, ham veri paylaşımı
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
ms.openlocfilehash: 0f5195e5a74395073267fd4df87f077c6a1d5f20
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530586"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Depolama hesabınıza Gelişmiş Tehdit Avcılığı olaylarının akışını yapmak için Microsoft 365 Defender yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracınızda bir [Depolama hesabı](/azure/storage/common/storage-account-overview) oluşturun.

2. [Azure kiracınızda](https://ms.portal.azure.com/) oturum açın, **Abonelikler > Aboneliğiniz > Kaynak Sağlayıcıları > Microsoft.Insights'a Kaydolun'a** gidin.

### <a name="add-contributor-permissions"></a>Katkıda bulunan izinleri ekleme

Depolama hesabı oluşturulduktan sonra aşağıdakileri yapmanız gerekir:

1. Microsoft 365 Defender oturum açmak için kullanılacak kullanıcıyı Katkıda Bulunan olarak tanımlayın.

    **Rol atamaları** altında **Depolama Hesabı > Erişim denetimi (IAM) > Ekle** ve doğrula'ya gidin.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. ***Genel Yönetici** _ veya _*_Güvenlik Yöneticisi_** olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> oturum açın.

2. **Ayarlar** \> **Microsoft 365 Defender** \> **Akış API'sine** gidin. Doğrudan **Akış API'si** sayfasına gitmek için kullanın <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. **Ekle**'ye tıklayın.

4. Görüntülenen **Yeni Akış API'si ayarları ekle** açılır penceresinde aşağıdaki ayarları yapılandırın:
   1. **Ad**: Yeni ayarlarınız için bir ad seçin.
   2. **Olayları Azure Depolama'ya ilet'i** seçin.
   3. Görüntülenen **Depolama Hesabı Kaynak Kimliği** kutusuna **Depolama Hesabı Kaynak Kimliğinizi** yazın. **Depolama Hesabı Kaynak Kimliğinizi** almak için konumunda Azure portal <https://portal.azure.com>açın, **Depolama hesapları'na** \> tıklayın özellikler sekmesine \> gidin **ve Depolama Hesabı Kaynak Kimliği** altındaki metni kopyalayın.

      :::image type="content" source="../defender-endpoint/images/storage-account-resource-id.png" alt-text="Depolama Hesabı Kaynak Kimliği" lightbox="../defender-endpoint/images/storage-account-resource-id.png":::

   4. **Yeni Akış API'si ayarları ekle** açılır menüsüne geri dönüp akış yapmak istediğiniz **Olay türlerini** seçin.

   İşiniz bittiğinde **Gönder'e** tıklayın.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Depolama hesabındaki olayların şeması

- Her olay türü için bir blob kapsayıcısı oluşturulur:

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="Blob kapsayıcısı örneği" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

- Blobdaki her satırın şeması aşağıdaki JSON'dır:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Her blob birden çok satır içerir.

- Her satır olay adını, Uç Nokta için Defender'ın olayı aldığı zamanı, ait olduğu kiracıyı (yalnızca kiracınızdan olayları alırsınız) ve JSON biçimindeki olayı "properties" adlı bir özellikte içerir.

- Microsoft 365 Defender olaylarının şeması hakkında daha fazla bilgi için bkz[. Gelişmiş Avcılık'a genel bakış](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özelliklerimizin veri türlerini almak için aşağıdakileri yapın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender'da</a> oturum açın ve **Gelişmiş Avcılık'a** \> gidin. **Doğrudan Gelişmiş avcılık** sayfasına gitmek için <security.microsoft.com/advanced-hunting> kullanın.

2. **Sorgu** sekmesinde, her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayına bir örnek aşağıda verilmiştir:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Örnek cihaz bilgisi sorgusu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="monitoring-created-resources"></a>Oluşturulan kaynakları izleme

**Azure İzleyici'yi** kullanarak akış API'sinin oluşturduğu kaynakları izleyebilirsiniz. Daha fazla bilgi için bkz[. Hedefleri izleme - Azure İzleyici | Microsoft Docs](/azure/azure-monitor/logs/logs-data-export?tabs=portal#monitor-destinations).

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Avcılık'a Genel Bakış](../defender/advanced-hunting-overview.md)
- [Microsoft 365 Defender Akış API'si](streaming-api.md)
- [Microsoft 365 Defender olaylarını Azure depolama hesabınıza akışla aktarma](streaming-api-storage.md)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)
