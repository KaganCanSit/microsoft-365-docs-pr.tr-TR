---
title: Uç Nokta için Microsoft Defender API bağlantısı Power BI
ms.reviewer: ''
description: Kullanıcı API'lerinin en üstünde Power Business Intelligence (BI) Uç Nokta için Microsoft Defender oluşturun.
keywords: api'ler, desteklenen api'ler, Power BI, raporlar
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
ms.openlocfilehash: 4cad6fd5188745773ce561d1db697989598a1dc5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472165"
---
# <a name="create-custom-reports-using-power-bi"></a>Özel raporları kullanarak özel Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Bu bölümde, Uç nokta API'leri için Defender'Power BI bir rapor oluşturma hakkında bilgi edinebilirsiniz.

İlk örnekte, Power BI Gelişmiş Av API'sine nasıl bağlan bağlantısı olduğu ve ikinci örnekte de Makine Eylemleri veya Uyarılar gibi OData API'lerimize bağlantının olduğu yer almaktadır.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Bağlan Power BI Av API'sini Kullanma

- Microsoft Power BI.

- Verileri Boş **Sorgu** **Al'a**\> tıklayın.

  :::image type="content" source="images/power-bi-create-blank-query.png" alt-text="Veri Al menü öğesinin altındaki Boş Sorgu seçeneği" lightbox="images/power-bi-create-blank-query.png":::

- **Ekle'Gelişmiş Düzenleyici**.

  :::image type="content" source="images/power-bi-open-advanced-editor.png" alt-text="Gelişmiş Düzenleyici menü öğesi" lightbox="images/power-bi-open-advanced-editor.png":::

- Aşağıdaki kopyayı kopyalayıp düzenleyiciye yapıştırın:

```
    let
        AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",

        HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",

        Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),

        TypeMap = #table(
            { "Type", "PowerBiType" },
            {
                { "Double",   Double.Type },
                { "Int64",    Int64.Type },
                { "Int32",    Int32.Type },
                { "Int16",    Int16.Type },
                { "UInt64",   Number.Type },
                { "UInt32",   Number.Type },
                { "UInt16",   Number.Type },
                { "Byte",     Byte.Type },
                { "Single",   Single.Type },
                { "Decimal",  Decimal.Type },
                { "TimeSpan", Duration.Type },
                { "DateTime", DateTimeZone.Type },
                { "String",   Text.Type },
                { "Boolean",  Logical.Type },
                { "SByte",    Logical.Type },
                { "Guid",     Text.Type }
            }),

        Schema = Table.FromRecords(Response[Schema]),
        TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
        Results = Response[Results],
        Rows = Table.FromRecords(Results, Schema[Name]),
        Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))

    in Table
```

- **Bitti'ye tıklayın**.

- Kimlik Bilgilerini **Düzenle'ye tıklayın**.

    :::image type="content" source="images/power-bi-edit-credentials.png" alt-text="Kimlik Bilgilerini Düzenle menü öğesi" lightbox="images/power-bi-edit-credentials.png":::
    

- Kuruluş **hesabı Oturum** **açın'ı**\> seçin.

    :::image type="content" source="images/power-bi-set-credentials-organizational.png" alt-text="Kuruluş hesabı menü öğesinde Oturum aç seçeneği" lightbox="images/power-bi-set-credentials-organizational.png":::

- Kimlik bilgilerinizi girin ve oturum açık olmak için bekleyin.

- **Ekle'Bağlan**.

    :::image type="content" source="images/power-bi-set-credentials-organizational-cont.png" alt-text="Kuruluş hesabı menü öğesinde oturum açma onay iletisi" lightbox="images/power-bi-set-credentials-organizational-cont.png":::

- Artık sorgunun sonuçları tablo olarak görüntülenir ve üzerine görsel öğeler yapmaya başlayabilirsiniz!

- Bu tabloyu yineleyemez, yeniden adlandırarak istediğiniz verileri elde etmek için Gelişmiş Av sorgusunu içinden düzenleyebilirsiniz.

## <a name="connect-power-bi-to-odata-apis"></a>Bağlan Power BI OData API'lerini arama

- Yukarıdaki örnekteki tek fark düzenleyicinin içindeki sorgudur.

- Aşağıdan kopyalayıp, tüm makine eylemlerini kuruluştan çekmek **için düzenleyiciye** yapıştırın:

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- Alerts and Machines için **de aynı şeyi** **yapmak gerekir**.
- Sorgu filtreleri için OData sorgularını da kullanabilirsiniz. Bkz [. OData Sorgularını Kullanma](exposed-apis-odata-samples.md).

## <a name="power-bi-dashboard-samples-in-github"></a>Power BI örneklerine bir pano GitHub

Daha fazla bilgi için [Power BI şablonuna bakın](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>Örnek raporlar

Rapor Uç Nokta için Microsoft Defender Power BI görüntüleme. Daha fazla bilgi için bkz. [Kod örneklerine göz atma](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta API'leri için Defender](apis-intro.md)
- [Gelişmiş Avcılık API'si](run-advanced-query-api.md)
- [OData Sorgularını Kullanma](exposed-apis-odata-samples.md)
