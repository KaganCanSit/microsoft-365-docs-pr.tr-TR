---
title: Azure Microsoft 365 Defender Hub'a etkinlik akışı
description: Etkinlik Merkezi'nize Gelişmiş Microsoft 365 Defender etkinlikleri akışı için nasıl yapılandırılanı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Azure Etkinlik Merkezi, Azure depolama, depolama hesabı, Gelişmiş Koruma, ham veri paylaşımı
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
ms.openlocfilehash: 064ce5f796d59994b9d7ec4c3403711b1d683e56
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500485"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Gelişmiş Microsoft 365 Defender etkinliklerini Azure Etkinlik Merkezi'nize akış olarak yapılandırmak için gelişmiş av etkinliklerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracınız [içinde bir](/azure/event-hubs/) Olay hub'ı oluşturun.

2. Azure kiracınıza oturum açmak [için Abonelikler](https://ms.portal.azure.com/) 'e **>. >. Microsoft.>.Analizler**.

3. Olay Merkezi Ad Alanı oluşturun, Olay Merkezi Ad Alanı **'** > Fiyat katmanını, aktarım hızı birimlerini ve beklenen yüke uygun Otomatik Inflate'yi ekleyin ve seçin. Daha fazla bilgi için bkz. [Etkinlik Hub'larının fiyatı](https://azure.microsoft.com/pricing/details/event-hubs/).

### <a name="add-contributor-permissions"></a>Katılımcı izinleri ekleme

Olay Merkezi ad alanı oluşturulduktan sonra şunları açıklamanız gerekir:

1. Microsoft 365 Defender'da oturum aecek Microsoft 365 Defender tanımlayın.

2. Bir uygulamaya bağlanıyorsanız, Uygulama Kayıt Hizmeti Sorumluyu Okuyucu, Azure Olay Merkezi Veri Alıcısı olarak ekleyin (bu işlem Kaynak Grubu veya Abonelik düzeyinde de yapılabilir).

    Access denetimi **(IAM) > rol atamaları altında ekleme >** ve doğrulamak için Olay hub'ları **ad alanına gidin**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. Portalda <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">*Microsoft 365 Defender Yönetici</a>**_ veya** _*Güvenlik Yöneticisi** _olarak oturum_ açın.

2. Akış [API'si ayarları sayfasına gidin](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. **Ekle'ye tıklayın**.

4. Yeni ayarlarınız için bir ad seçin.

5. **Olayları Azure Etkinlik Merkezi'ne ilet'i seçin**.

6. Olay verilerini tek bir Olay Merkezi'ne dışarı aktarmayı veya her olay tabloyu Olay Merkezi ad alanınıza farklı bir olay hub'ını dışarı aktarmayı seçin.

7. Olay verilerini tek bir Olay Merkezi'ne dışarı aktarmak için, Olay Merkezi **adını ve** Olay Merkezi **kaynak kimliğinizi girin**.

   Olay Merkezi kaynak **kimliğinizi almak için**, **AzureProperties** sekmesinde [Azure](https://ms.portal.azure.com/) >  Olay Merkezi ad alanı sayfanıza gidin ve > kimliği altındaki **metni kopyalayın**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Olay Merkezi kaynak kimliği" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Akış [API'sinde Microsoft 365 Defender](supported-event-types.md) türlerinin destek durumunu gözden geçirmek için olay akışı API'sinde desteklenen olay Microsoft 365 gidin.

9. Akışla akışı yapmak istediğiniz olayları seçin ve Kaydet'e **tıklayın**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Azure Olay Merkezi'nde olayların şeması

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

- Azure Olay Merkezi'nde yer alan her Etkinlik Merkezi iletisi kayıt listesini içerir.

- Her kayıt olay adını, Microsoft 365 Defender zamanı, ait olduğu kiracıyı (yalnızca kiracıdan olay alıyabilirsiniz) ve "properties" adlı bir özelliğe JSON biçiminde **olay** içerir.

- Bu etkinliklerin şeması hakkında daha fazla bilgi Microsoft 365 Defender bkz. [Gelişmiş Atlamaya genel bakış](advanced-hunting-overview.md).

- Gelişmiş Av'da, **CihazBilgileri** tablosunda, cihaz grubunu içeren **Makine** Grubu adlı bir sütun vardır. Burada her etkinlik bu sütunla da süslenmiş olarak görüntülenir.

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özellikleri için veri türlerini almak için şunları yapın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">2013'te Microsoft 365 Defender</a> Gelişmiş Av [sayfasına gidin](https://security.microsoft.com/hunting-package).

2. Her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Cihaz Bilgileri olayı için bir örnek:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Cihaz bilgileri için örnek bir sorgu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](advanced-hunting-overview.md)
- [Microsoft 365 Defender akışı API'si](streaming-api.md)
- [Olay Microsoft 365 Defender API'sinde desteklenen etkinlik türleri](supported-event-types.md)
- [Azure Microsoft 365 Defender hesabınıza etkinlik akışı uygulama](streaming-api-storage.md)
- [Azure Etkinlik Merkezi belgeleri](/azure/event-hubs/)
- [Bağlantı sorunlarını giderme - Azure Olay Merkezi](/azure/event-hubs/troubleshooting-guide)
