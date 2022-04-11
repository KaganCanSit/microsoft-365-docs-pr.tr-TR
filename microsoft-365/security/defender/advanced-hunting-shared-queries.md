---
title: Microsoft 365 Defender gelişmiş avcılıkta paylaşılan sorguları kullanma
description: Önceden tanımlanmış ve paylaşılan sorgularla tehdit avcılığı yapmaya hemen başlayın. Sorgularınızı genel veya kuruluşunuzla paylaşın.
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto, github deposu, sorgularım, paylaşılan sorgular
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 2e86d733304eeaa0e5e16f3ce1bfde87c21258d4
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761634"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Gelişmiş avcılıkta paylaşılan sorguları kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) sorguları aynı kuruluştaki kullanıcılar arasında paylaşılabilir. Ayrıca yalnızca sizin erişebileceğiniz sorguları da kaydedebilirsiniz. Ayrıca, GitHub genel olarak paylaşılan topluluk sorgularını da bulabilirsiniz. Kaydedilen bu sorgular, sıfırdan sorgu yazmak zorunda kalmadan belirli tehdit avcılığı senaryolarını hızla izlemenize olanak sağlar.

Gelişmiş avcılıkta Sorgular sekmesinin altında **Paylaşılan sorgular**, **Sorgularım** ve **Community sorguların** açılan menülerini bulabilirsiniz. Menüyü genişletmek için aşağı dönük bir ok seçebilirsiniz.


:::image type="content" source="../../media/advanced-hunting-shared-queries-1.png" alt-text="Microsoft 365 Defender portalında paylaşılan sorgular, Sorgularım ve Community sorguları" lightbox="../../media/advanced-hunting-shared-queries-1.png":::



## <a name="save-modify-and-share-a-query"></a>Sorguyu kaydetme, değiştirme ve paylaşma
Yeni veya mevcut bir sorguyu kaydederek yalnızca sizin için erişilebilir olmasını veya kuruluşunuzdaki diğer kullanıcılarla paylaşılabilmesini sağlayabilirsiniz. 

1. Sorgu oluşturma veya değiştirme. 

2. **Sorguyu kaydet** açılan düğmesine tıklayın ve **Farklı kaydet'i** seçin.
    
3. Sorgu için bir ad girin. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="Microsoft 365 Defender portalına kaydedilmek üzere olan yeni sorgu" lightbox="../../media/shared-query-2.png":::

4. Sorguyu kaydetmek istediğiniz klasörü seçin.
    - **Paylaşılan sorgular** — kuruluşunuzda tüm kullanıcılarla paylaşıldı
    - **Sorgularım** — yalnızca sizin için erişilebilir
    
5. **Kaydet**'i seçin. 

## <a name="delete-or-rename-a-query"></a>Sorguyu silme veya yeniden adlandırma
1. Yeniden adlandırmak veya silmek istediğiniz sorgunun sağındaki üç noktayı seçin.

    :::image type="content" source="../../media/advanced-hunting-del-save-query.png" alt-text="Microsoft 365 Defender portalındaki Gelişmiş Tehdit Avcılığı sayfasında sorguyu yeniden adlandırma veya silme" lightbox="../../media/advanced-hunting-del-save-query.png":::

2. **Sil'i** seçin ve silmeyi onaylayın. İsterseniz **Yeniden Adlandır'ı** seçip sorgu için yeni bir ad da sağlayabilirsiniz.

## <a name="create-a-direct-link-to-a-query"></a>Sorguya doğrudan bağlantı oluşturma
Sorgunuzu doğrudan gelişmiş tehdit avcılığı sorgu düzenleyicisinde açan bir bağlantı oluşturmak için sorgunuzu sonlandırın ve **Bağlantıyı paylaş'ı** seçin.

## <a name="access-community-queries-in-the-github-repo"></a>GitHub deposunda topluluk sorgularını erişme  
Microsoft güvenlik araştırmacıları, [GitHub'daki belirli bir genel depoda](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender) düzenli olarak gelişmiş avlanma sorgularını paylaşır. Bu depoya yapılan katkılar yayımlanmadan önce gözden geçirilir. Katkıda bulunmak için [ücretsiz olarak GitHub katılın](https://github.com/).

Bu sorguları **Community sorguları** açılan menüsünde de kolayca bulabilirsiniz.

:::image type="content" source="../../media/advanced-hunting-shared-queries-2.png" alt-text="Microsoft 365 Defender portalında klasöre göre düzenlenmiş sorguları Community" lightbox="../../media/advanced-hunting-shared-queries-2.png":::

Community sorgular *Kampanyalar*, *Koleksiyon*, *Savunma kaçaması* ve benzeri klasörler halinde gruplandırılır. Sorgu hakkında daha fazla bilgi, sorgunun kendisinde satır içi açıklamalar olarak sağlanır. 

>[!tip]
>Microsoft güvenlik araştırmacıları, yeni ortaya çıkan tehditlerle ilişkili etkinlikleri ve göstergeleri bulmak için kullanabileceğiniz gelişmiş tehdit avcılığı sorguları da sağlar. Bu sorgular, [Microsoft 365 Defender'daki tehdit analizi](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) raporlarının bir parçası olarak sağlanır.


## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)