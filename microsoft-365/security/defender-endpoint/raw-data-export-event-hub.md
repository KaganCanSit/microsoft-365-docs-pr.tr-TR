---
title: Uç nokta olaylarının Microsoft Defender'ı Azure Olay Hub'lara akışı
description: Etkinlik Merkezi'nize Gelişmiş Av etkinliklerini akışla akışı için Uç Nokta için Microsoft Defender'ı yapılandırmayı öğrenin.
keywords: ham veri dışarı aktarma, akış API'si, API, Azure Etkinlik Hub'ları, Azure depolama, depolama hesabı, Gelişmiş Av, ham veri paylaşımı
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
ms.openlocfilehash: b1d313ed2980f84318a590df55e0a8d8e7b152ab
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014113"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Gelişmiş Av etkinliklerini Azure Etkinlik Hub'larınızı akışla yapmak üzere Uç Nokta için Microsoft Defender'ı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Başlamadan önce

1. Kiracınız [içinde bir](/azure/event-hubs/) olay hub'ı oluşturun.

2. Azure kiracınıza oturum [açmak için Abonelikler](https://ms.portal.azure.com/) 'e **>. >. Microsoft.insights'a > Için Kaydol'u seçin**.

## <a name="enable-raw-data-streaming"></a>Ham veri akışını etkinleştirme

1. [Microsoft 365 Defender'da](https://security.microsoft.com) ***Genel** Yönetici_ veya _*_Güvenlik Yöneticisi** olarak oturum_ açın.

2. Microsoft Defender [portalında Veri dışarı](https://security.microsoft.com/interoperability/dataexport) aktarma ayarları sayfasına gidin.

3. Veri dışarı **aktarma ayarları ekle'ye tıklayın**.

4. Yeni ayarlarınız için bir ad seçin.

5. **Etkinlikleri Azure Etkinlik Hub'lara ilet'i seçin**.

6. Olay **Hub'ları adını ve** Olay **Hub'ları kaynak kimliğinizi yazın**.

   Olay **Hub'ları** kaynak kimliğinizi almak için Azure [](https://ms.portal.azure.com/) \> > özellikleri sekmesinde, Kaynak Kimliği'nin altındaki metni **kopyalayın:**

   :::image type="content" alt-text="Olay merkezi kaynak Kimliği1'in görüntüsü." source="images/event-hub-resource-id.png" lightbox="images/event-hub-resource-id.png":::

7. Akışla akışı yapmak istediğiniz olayları seçin ve Kaydet'e **tıklayın**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>Azure Olay Hub'larında olayların şeması

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

- Azure Olay Hub'larında her olay merkezi iletisi kayıt listesini içerir.

- Her kayıt olay adını, Uç Nokta için Microsoft Defender'ın olayı aldığı zamanı, ait olduğu kiracıyı (yalnızca kiracıdan olay alıyabilirsiniz) ve "**properties**" adlı bir özelliğe JSON biçiminde olay içerir.

- Uç nokta olayları için Microsoft Defender şeması hakkında daha fazla bilgi için bkz. [Gelişmiş Atlamaya genel bakış](advanced-hunting-overview.md).

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

  ![Olay merkezi kaynak Kimliği2'nin görüntüsü.](images/machine-info-datatype-example.png)

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](advanced-hunting-overview.md)
- [Uç nokta akış API'si için Microsoft Defender](raw-data-export.md)
- [Azure depolama hesabınıza Uç nokta olayları için Microsoft Defender'ı akışla uygulama](raw-data-export-storage.md)
- [Azure Olay Hub'ları belgeleri](/azure/event-hubs/)
- [Bağlantı sorunlarını giderme - Azure Olay Hub'ları](/azure/event-hubs/troubleshooting-guide)
