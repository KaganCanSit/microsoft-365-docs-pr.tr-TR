---
title: Depolama hesabınıza Uç nokta olayları için Microsoft Defender'Depolama akışı
description: Gelişmiş Av etkinliklerini iş akışı için Uç Nokta için Microsoft Defender'ı nasıl yapılandır Depolama öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Etkinlik Hub'ları, Azure depolama, depolama hesabı, Gelişmiş Av, ham veri paylaşımı
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
ms.openlocfilehash: a9db98456cc971b4ac4179cd4f3460dfe2137b91
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014077"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Gelişmiş Av etkinliklerini iş akışı için Uç Nokta için Microsoft Defender'ı Depolama yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracı [Depolama bir](/azure/storage/common/storage-account-overview) hesap oluşturun.

2. Azure kiracınıza oturum [açmak için Abonelikler](https://ms.portal.azure.com/) 'e **>. >. Microsoft.insights'a > Için Kaydol'u seçin**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. [Microsoft 365 Defender'da](https://security.microsoft.com) ***Genel** Yönetici_ veya _*_Güvenlik Yöneticisi** olarak oturum_ açın.

2. Veri dışarı [aktarma ayarları sayfasında Veri dışarı](https://security.microsoft.com/interoperability/dataexport) Microsoft 365 Defender.

3. Veri dışarı **aktarma ayarları ekle'ye tıklayın**.

4. Yeni ayarlarınız için bir ad seçin.

5. **Etkinlikleri Azure Depolama'a ilet'i seçin**.

6. Hesap Depolama **Kimliği'nizi yazın**. Depolama Hesap Kaynak **Depolama** almak için [Azure portal](https://ms.portal.azure.com/) \> \> özellikleri sekmesindeki Depolama hesap sayfanıza gidin ve hesap kaynak kimliği **Depolama kopyalayın**:

   :::image type="content" alt-text="Olay merkezi kaynak kimliği1 görüntüsü." source="images/storage-account-resource-id.png" lightbox="images/storage-account-resource-id.png":::

7. Akışla akışı yapmak istediğiniz olayları seçin ve Kaydet'e **tıklayın**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Depolama hesabında olayların şeması

- Her olay türü için bir blob kapsayıcısı oluşturulur:

  :::image type="content" alt-text="Olay merkezi kaynak kimliği2 görüntüsü." source="images/storage-account-event-schema.png" lightbox="images/storage-account-event-schema.png":::

- Bir blob'un her satırın şeması aşağıdaki JSON'tır:

  ```json
  {
      "time": "<The time WDATP received the event>"
      "tenantId": "<Your tenant ID>"
      "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
      "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Her blob birden çok satır içerir.

- Her satır olay adını, Uç Nokta için Defender'ın olayı aldığı zaman, ait olduğu kiracı (yalnızca kiracıdan olay alıyabilirsiniz) ve "özellikler" adlı bir özelliğe JSON biçiminde olay içerir.

- Uç nokta olayları için Microsoft Defender şeması hakkında daha fazla bilgi için bkz. [Gelişmiş Atlamaya genel bakış](advanced-hunting-overview.md).

- Gelişmiş Av'da, **CihazBilgileri** tablosunda, cihaz grubunu içeren **Makine** Grubu adlı bir sütun vardır. Burada her etkinlik bu sütunla da süslenmiş olarak görüntülenir. Daha [fazla bilgi için cihaz](machine-groups.md) gruplarına bakın.

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özelliklerimizin veri türlerini almak için şunları yapın:

1. [2013'te Microsoft 365 Defender](https://security.microsoft.com) Gelişmiş Av [sayfasına gidin](https://security.microsoft.com/hunting-package).

2. Her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayı için bir örnek:

  ![Olay merkezi kaynak kimliği3 resmi.](images/data-types-mapping-query.png)

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](advanced-hunting-overview.md)
- [Uç Nokta Akış API'si için Microsoft Defender](raw-data-export.md)
- [Azure depolama hesabınıza Uç nokta olayları için Microsoft Defender'ı akışla uygulama](raw-data-export-storage.md)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)
