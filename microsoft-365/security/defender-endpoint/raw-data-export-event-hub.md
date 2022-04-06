---
title: Etkinlikleri Uç Nokta için Microsoft Defender akışına Azure Event Hubs
description: Etkinlik Merkezi'nize Gelişmiş Uç Nokta için Microsoft Defender etkinlikleri akışı için nasıl yapılandırılanı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Azure Event Hubs, Azure depolama, depolama hesabı, Gelişmiş Koruma, ham veri paylaşımı
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
ms.openlocfilehash: eb58e21ee9dc2cf7c1eaf89c8fa9d06edfbbe050
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467917"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Gelişmiş Uç Nokta için Microsoft Defender etkinliklerini akışı için gelişmiş av etkinliklerini Azure Event Hubs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracınız [içinde bir](/azure/event-hubs/) olay hub'ı oluşturun.

2. Azure kiracınıza oturum [açmak için Abonelikler](https://ms.portal.azure.com/) 'e **>. >. Microsoft.insights'a > Için Kaydol'u seçin**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. [Microsoft 365 Defender'da](https://security.microsoft.com) ***Genel** Yönetici_ veya _*_Güvenlik Yöneticisi** olarak oturum_ açın.

2. Microsoft Defender [portalında Veri dışarı](https://security.microsoft.com/interoperability/dataexport) aktarma ayarları sayfasına gidin.

3. Veri dışarı **aktarma ayarları ekle'ye tıklayın**.

4. Yeni ayarlarınız için bir ad seçin.

5. Olayları **ilet'i seç Azure Event Hubs**.

6. Olay **Hub'ları adını ve** Olay **Hub'ları kaynak kimliğinizi yazın**.

   Olay **Hub'ları kaynak** kimliğinizi almak için Azure > özellikleri sekmesindeki [Azure Event Hubs](https://ms.portal.azure.com/) \> alanı sayfanıza gidin ve **Kaynak Kimliği'nin altındaki metni kopyalayın**:

   :::image type="content" source="images/event-hub-resource-id.png" alt-text="Olay Hub'ları kaynak Kimliği-1" lightbox="images/event-hub-resource-id.png":::

7. Akışla akışı yapmak istediğiniz olayları seçin ve Kaydet'e **tıklayın**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>düzende olayların şeması Azure Event Hubs

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the tenant that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

- Azure Event Hubs olay merkezi iletisi kayıtların listesini içerir.

- Her kayıt olay adını, Uç Nokta için Microsoft Defender aldığı zamanı, ait olduğu kiracıyı (yalnızca kiracıdan olay alıyabilirsiniz) ve "properties" adlı bir özelliğe JSON biçiminde **olay** içerir.

- Bu etkinliklerin şeması hakkında daha fazla bilgi Uç Nokta için Microsoft Defender bkz. [Gelişmiş Atlamaya genel bakış](advanced-hunting-overview.md).

- Gelişmiş Av'da, **CihazBilgileri** tablosunda, cihaz grubunu içeren **Makine** Grubu adlı bir sütun vardır. Burada her etkinlik bu sütunla da süslenmiş olarak görüntülenir. Daha [fazla bilgi için cihaz](machine-groups.md) gruplarına bakın.

## <a name="data-types-mapping"></a>Veri türleri eşlemesi

Olay özellikleri için veri türlerini almak için şunları yapın:

1. [2013'te Microsoft 365 Defender](https://security.microsoft.com) Gelişmiş Av [sayfasına gidin](https://security.microsoft.com/hunting-package).

2. Her olay için veri türleri eşlemesini almak için aşağıdaki sorguyu çalıştırın:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Cihaz Bilgileri olayı için bir örnek:

  :::image type="content" source="images/machine-info-datatype-example.png" alt-text="Olay Hub'ları kaynak Kimliği-2" lightbox="images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](advanced-hunting-overview.md)
- [Uç Nokta için Microsoft Defender akış API'si](raw-data-export.md)
- [Azure Uç Nokta için Microsoft Defender hesabınıza etkinlik akışı uygulama](raw-data-export-storage.md)
- [Azure Event Hubs belgeleri](/azure/event-hubs/)
- [Bağlantı sorunlarını giderme - Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
