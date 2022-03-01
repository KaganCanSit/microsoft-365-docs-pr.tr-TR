---
title: Sorgu sonuçlarını bir olayla bağlama
description: Sorgu sonuçlarını bir olayla bağlama
keywords: gelişmiş av, olay, özet, varlık, avına git, ilgili etkinlikler, tehdit avı, siber tehdit araması, arama, sorgu, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 5302c078da3ded781007412a2807fc20fa77319e
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997073"
---
# <a name="link-query-results-to-an-incident"></a>Sorgu sonuçlarını bir olayla bağlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Olay özelliği bağlantısı, araştırma kapsamındaki yeni veya mevcut bir olay için gelişmiş arama sorgusu sonuçları eklemenizi sağlar. Bu özellik, gelişmiş av etkinliklerinden kayıtları kolayca yakalamanıza yardımcı olur ve böylece bir olayla ilgili daha zengin bir zaman çizelgesi veya bağlam oluşturabilirsiniz. 

## <a name="link-results-to-new-or-existing-incidents"></a>Sonuçları yeni veya var olan olaylara bağlama

1. Gelişmiş arama sorgusu sayfasında, önce sorgunuza verilen sorgu alanına girin, ardından sonuçlarınızı **almak için Sorguyu** çalıştır'ı seçin.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Örnek Portalda **Query** Microsoft 365 Defender" lightbox="../../media/link-to-incident-1.png":::

2. Sonuçlar sayfasında, üzerinde çalışmakta olduğunu yeni veya geçerli bir soruşturmayla ilgili olayları veya kayıtları seçin, sonra da Olay **bağlantısı'ı seçin**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Portalda **Sonuçlar** sekmesinin **Olay bağlantısı** Microsoft 365 Defender." lightbox="../../media/link-to-incident-1b.png":::

3. Olay **bağlantısı bölmesinde** Uyarı ayrıntıları bölümünü bulun, ardından olayları uyarılara dönüştürmek ve  bunları yeni bir olay haline dönüştürmek için Yeni olay oluştur'a tıklayın:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Portalda **Olay bağlantısı** bölmesindeki **Uyarı ayrıntıları** Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Ya da **seçili kayıtları var olan bir** olayla bağlantıla'ya tıklayarak seçili kayıtları var olan bir olayla birlikte ekleyin. Var olan olayları açılan listesinden ilgili olayı seçin. Var olan olayı bulmak için olay adının veya kimliğinin ilk birkaç karakteri de girebilirsiniz. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Portalda **Olay bağlantısı** bölmesindeki **Uyarı ayrıntıları** Microsoft 365 Defender":::

4. Seçimlerden herhangi biri için aşağıdaki ayrıntıları sağ tıklayın ve ardından Sonraki'yi **seçin**:
      - **Uyarı başlığı** - Olay yanıtlayanların anlayanların anlayan sonuçlar için açıklayıcı bir başlık girin. Bu, uyarı başlığı olur.
      - **Önem Derecesi** - Uyarı grubu için geçerli önem derecenizi seçin.
      - **Kategori** - Uyarılar için uygun tehdit kategorisini seçin.
      - **Açıklama** - Gruplamış uyarılar için yararlı bir açıklama sağlar.
      - **Önerilen eylemler** - Düzeltme eylemleri sağlama.

5. Etkilenen **varlıklar bölümünde** , etkilenen veya etkilenen ana varlığı seçin. Bu bölümde, yalnızca sorgu sonuçlarını temel alan geçerli varlıklar görünür. Örneğimizde, olası bir e-posta sızıntı olayıyla ilgili olayları bulmak için sorgu kullandık, dolayısıyla etki alanı Gönderen kişidir. Örneğin dört farklı gönderen varsa, dört uyarı oluşturulur ve seçilen olayla bağlantılı olur.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Portalda **Olay bağlantısı** bölümündeki etki Microsoft 365 Defender" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. **İleri**'yi seçin.
1. Özet bölümünde sağladığımız ayrıntıları **gözden** geçirebilirsiniz.
     :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Portalda **Olay bağlantısı** bölümündeki sonuç Microsoft 365 Defender" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. **Bitti'yi seçin**.

## <a name="view-linked-records-in-the-incident"></a>Olayda bağlantılı kayıtları görüntüleme

Olayların bağlı olduğu olayı görüntülemek için olayın adını seçin.
     :::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Portalda **Summary** sekmesindeki olay ayrıntıları Microsoft 365 Defender" lightbox="../../media/link-to-incident-6-incident-pg.png":::

Örneğimizde, seçilen dört olayı temsil eden dört uyarı yeni bir olayla başarıyla bağlanmıştır. 

Uyarı sayfalarının her biri, olay veya olaylarla ilgili tüm bilgileri zaman çizelgesi görünümünde (varsa) ve sorgu sonuçları görünümünde bulabilirsiniz.
     :::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Zaman Çizelgesi portalının **Zaman Çizelgesi** sekmesinde bir etkinliğin tüm Microsoft 365 Defender örneği" lightbox="../../media/link-to-incident-7-alert-story.png":::

Olayı seçerek Kaydı incele bölmesini **de açabilirsiniz** .
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Portalda yer alan **Zaman Çizelgesi** sekmesinde bir olayın kayıt ayrıntılarını inceleme Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Gelişmiş av kullanarak eklenen etkinlikler için filtre uygulama
El ile algılama kaynağıyla Olaylar sırasına ve Uyarılar kuyruğuna filtreyi atarak gelişmiş avdan hangi uyarıların **üretlmiş** olduğunu görüntüabilirsiniz.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Yeni portalda **Filtreler** sayfasındaki Olayları ve Uyarıları el ile filtreleme Microsoft 365 Defender" lightbox="../../media/link-to-incident-8-filter.png":::
