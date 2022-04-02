---
title: Sorgu sonuçlarını bir olayla bağlayın
description: Sorgu sonuçlarını bir olayla bağlayın
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: c81b0b0850686242c675629cf99fa2c4b3a18496
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755495"
---
# <a name="link-query-results-to-an-incident"></a>Sorgu sonuçlarını bir olayla bağlayın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Araştırma kapsamındaki yeni veya mevcut bir olayda gelişmiş arama sorgusu sonuçları eklemek için olay özelliğinin bağlantısını kullanabilirsiniz. Bu özellik, gelişmiş av etkinliklerinden kolayca kayıt alamanıza yardımcı olur ve böylece bir olayla ilgili daha zengin bir zaman çizelgesi veya bağlam oluşturmanıza olanak sağlar. 

## <a name="link-results-to-new-or-existing-incidents"></a>Sonuçları yeni veya var olan olaylara bağlama

1. Gelişmiş arama sorgusu sayfasında, önce sorgunuza verilen sorgu alanına girin, ardından sonuçlarınızı **almak için Sorguyu** çalıştır'ı seçin.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Microsoft 365 Defender portalında Sorgu sayfası" lightbox="../../media/link-to-incident-1.png":::

2. Sonuçlar sayfasında, üzerinde çalışmakta olduğunu yeni veya geçerli bir soruşturmayla ilgili olayları veya kayıtları seçin, sonra da Olay **bağlantısı'ı seçin**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Portalda Sonuçlar sekmesinin Olay bağlantısı Microsoft 365 Defender." lightbox="../../media/link-to-incident-1b.png":::

3. Olay **bağlantısı bölmesinde** Uyarı ayrıntıları bölümünü bulun, ardından olayları uyarılara dönüştürmek ve  bunları yeni bir olay haline dönüştürmek için Yeni olay oluştur'a tıklayın:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Microsoft 365 Defender portalında Olay bağlantısı bölmesindeki Uyarı ayrıntıları bölümü" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Ya da **seçili kayıtları var olan bir** olayla bağlantıla'ya tıklayarak seçili kayıtları var olan bir olayla birlikte ekleyin. Var olan olayları açılan listesinden ilgili olayı seçin. Var olan olayı bulmak için olay adının veya kimliğinin ilk birkaç karakteri de girebilirsiniz. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Microsoft 365 Defender portalında Uyarı ayrıntıları bölümü" lightbox="../../media/link-to-incident-3-link-to-existing.png":::

4. Seçimlerden herhangi biri için aşağıdaki ayrıntıları sağ tıklayın ve ardından Sonraki'yi **seçin**:
      - **Uyarı başlığı** - Olay yanıtlayanların anlayanların anlayan sonuçlar için açıklayıcı bir başlık girin. Bu açıklayıcı başlık uyarı başlığı olur.
      - **Önem Derecesi** - Uyarı grubu için geçerli önem derecenizi seçin.
      - **Kategori** - Uyarılar için uygun tehdit kategorisini seçin.
      - **Açıklama** - Gruplamış uyarılar için yararlı bir açıklama sağlar.
      - **Önerilen eylemler** - Düzeltme eylemleri sağlama.

5. Etkilenen **varlıklar bölümünde** , etkilenen veya etkilenen ana varlığı seçin. Bu bölümde, yalnızca sorgu sonuçlarını temel alan geçerli varlıklar görünür. Örneğimizde, olası bir e-posta sızıntı olayıyla ilgili olayları bulmak için sorgu kullandık, dolayısıyla etki alanı Gönderen kişidir. Örneğin dört farklı gönderen varsa, dört uyarı oluşturulur ve seçilen olayla bağlantılı olur.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Etki alanı portalının Olay bağlantısı bölümündeki Microsoft 365 Defender." lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. **İleri**'yi seçin.
1. Özet bölümünde sağlanan ayrıntıları **gözden** geçirebilirsiniz.
   :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Portalda Olay bağlantısı bölümündeki Microsoft 365 Defender sayfası" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. **Bitti'yi seçin**.

## <a name="view-linked-records-in-the-incident"></a>Olayda bağlantılı kayıtları görüntüleme

Olayların bağlı olduğu olayı görüntülemek için olayın adını seçin.
:::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Microsoft 365 Defender portalında Özet sekmesindeki olay Microsoft 365 Defender ekranı" lightbox="../../media/link-to-incident-6-incident-pg.png":::

Örneğimizde, seçilen dört olayı temsil eden dört uyarı yeni bir olayla başarıyla bağlanmıştır. 

Uyarı sayfalarının her biri, olay veya olaylarla ilgili tüm bilgileri zaman çizelgesi görünümünde (varsa) ve sorgu sonuçları görünümünde bulabilirsiniz.
:::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Microsoft 365 Defender portalında Zaman Çizelgesi sekmesinde bir olayın tüm ayrıntıları" lightbox="../../media/link-to-incident-7-alert-story.png":::

Olayı seçerek Kaydı incele bölmesini **de açabilirsiniz** .
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Microsoft 365 Defender portalında Zaman Çizelgesi sekmesinde bir olayın kayıt Microsoft 365 Defender incele" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Gelişmiş av kullanarak eklenen etkinlikler için filtre uygulama
El ile algılama kaynağıyla Olaylar sırasına ve Uyarılar kuyruğuna filtreyi atarak gelişmiş avdan hangi uyarıların **üretlmiş** olduğunu görüntüabilirsiniz.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Yeni portalda, Filtreler sayfasındaki Olayları ve Uyarıları el ile filtreleme Microsoft 365 Defender." lightbox="../../media/link-to-incident-8-filter.png":::
