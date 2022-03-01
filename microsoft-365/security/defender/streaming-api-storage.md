---
title: Microsoft 365 Defender hesabınıza Depolama akışı
description: Gelişmiş Av etkinliklerini Microsoft 365 Defender için gelişmiş av etkinliklerini yapılandırmayı Depolama öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Etkinlik Hub'ları, Azure depolama, depolama hesabı, Gelişmiş Av, ham veri paylaşımı
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
ms.openlocfilehash: 159b4a41d423c2a7af3d367185e29af35a378b6b
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "63004999"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Gelişmiş Microsoft 365 Defender etkinlikleri akışı için gelişmiş av etkinliklerini Depolama yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracı [Depolama bir](/azure/storage/common/storage-account-overview) hesap oluşturun.

2. Azure kiracınıza oturum açmak [için Abonelikler](https://ms.portal.azure.com/) 'e **>. >. Microsoft.>.Analizler**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender'da</a> ***Genel** Yönetici_ veya _*_Güvenlik Yöneticisi** olarak oturum_ açın.

2. Akış **API'Ayarlar** \> **Microsoft 365 Defender** \> **gidin**. Doğrudan Akış **API'si sayfasına gitmek** için kullanın <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. **Ekle**'ye tıklayın.

4. Görüntülenen **Yeni Akış API'si ayarları** ekle açılır sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   1. **Ad**: Yeni ayarlarınız için bir ad seçin.
   2. **Etkinlikleri Azure Depolama'a ilet'i seçin**.
   3. Görüntülenen **Depolama Kaynak Kimliği** kutusuna Hesap Kaynak Kimliği'Depolama **hesap kimliğinizi yazın**. Hesap Kaynak **Depolama almak** için Azure portalını <https://portal.azure.com> \> \> 'da açın, Depolama hesapları sekmesine gidip Hesap Kaynak Kimliği'nin altındaki **metni Depolama tıklayın**.

      ![Olay merkezi kaynak kimliği1 görüntüsü.](../defender-endpoint/images/storage-account-resource-id.png)

   4. Yeni Akış **API'si ayarları ekle** seçeneğine geri dönerek **akış oluşturmak istediğiniz** Etkinlik türlerini seçin.

   Bitirdikten sonra Gönder'e **tıklayın**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Depolama hesabında olayların şeması

- Her olay türü için bir blob kapsayıcısı oluşturulur:

  ![Olay merkezi kaynak kimliği2 görüntüsü.](../defender-endpoint/images/storage-account-event-schema.png)

- Bir blob'un her satırın şeması aşağıdaki JSON'tır:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Her blob birden çok satır içerir.

- Her satır olay adını, Uç Nokta için Defender'ın olayı aldığı zaman, ait olduğu kiracı (yalnızca kiracıdan olay alıyabilirsiniz) ve "özellikler" adlı bir özelliğe JSON biçiminde olay içerir.

- Bu etkinliklerin şeması hakkında daha fazla bilgi Microsoft 365 Defender bkz. [Gelişmiş Atlamaya genel bakış](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özelliklerimizin veri türlerini almak için şunları yapın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">3.05'te oturum Microsoft 365 Defender</a> gelişmiş **atlamaya** \> **gidin**. Doğrudan Gelişmiş av sayfasına **gitmek için** Gelişmiş av <security.microsoft.com/advanced-hunting>.

2. Sorgu **sekmesinde,** her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayı için bir örnek:

  ![Olay merkezi kaynak kimliği3 resmi.](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](../defender/advanced-hunting-overview.md)
- [Microsoft 365 Defender Akışı API'si](streaming-api.md)
- [Azure Microsoft 365 Defender hesabınıza etkinlik akışı uygulama](streaming-api-storage.md)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)
