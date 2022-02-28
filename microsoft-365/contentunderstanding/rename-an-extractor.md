---
title: Microsoft SharePoint Syntex'da bir ayıklaıcıyı yeniden SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex'da ayıklaıcıyı nasıl ve neden yeniden adlandır SharePoint Syntex.
ms.openlocfilehash: 0b5c52e00b287b6f4b41e7c8c3070261bccfda96
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986694"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da bir ayıklaıcıyı yeniden SharePoint Syntex

Bir noktada, ayıklanan veri alanına farklı bir adla başvurmak istediğiniz bir ayıklaıcıyı yeniden adlandırmak zorundayabilirsiniz. Örneğin, organizasyonunız sözleşme belgelerinde değişiklik yapmaya karar verir ve belgelerinde "müşteriler" olarak "müşteriler" sözlerine başvurur. Modelinize bir "Müşteri" alanı ayıklarsanız, bunu "İstemci" olarak yeniden adlandırmayı seçebilirsiniz.

Güncelleştirilmiş modelinizi belge kitaplığınıza SharePoint, belge kitaplığı görünümde yeni bir "İstemci" sütunu görüntülersiniz. Görünümünüz geçmiş etkinlikler için "Müşteri" sütununu korur, ancak modeliniz tarafından işlenen tüm yeni belgeler için yeni "İstemci" sütununu güncelleştirecektir. 

> [!IMPORTANT]
>  Güncelleştirilmiş modelinizi, yeni sütun adının lenmesi için daha önce uygulanmış olan belge kitaplıklarına eşitlemeye emin olun. 

## <a name="rename-an-extractor"></a>Ayıklayı yeniden adlandırma

Varlık ayıklayı yeniden adlandırmak için bu adımları izleyin.

1. Model listenizi görmek için içerik **merkezinde** Modeller'i seçin.

2. Modeller **sayfasındaki** **Ad sütununda,** ayıklaıcıyı yeniden adlandırmak istediğiniz modeli seçin.

3. Varlık **ayıklaıcıları** altında, yeniden adlandırmak istediğiniz ayıklaıcının adını seçin ve sonra da Yeniden Adlandır'ı **seçin**.</br>

    ![Yeniden Adlandır seçeneğinin vurgulu olduğu seçili bir ayıklayanı gösteren Varlık ayıklayanlar bölümünün ekran görüntüsü.](../media/content-understanding/entity-extractor-rename.png) </br>

4. Varlık **ayıklaıcıyı yeniden adlandır** panelinde:

   a. Yeni **ad'ın** altında ayıklaıcının yeni adını girin.</br>

    ![Varlık ayıkla panelinin ekran görüntüsü.](../media/content-understanding/rename-entity-extractor-panel.png) </br>

   b. (İsteğe bağlı) Gelişmiş **ayarlar'ın** altında, var olan bir site sütununu ilişkilendirmek isteyip istemiyorsanız seçin.

5. Yeniden **Adlandır'ı seçin**.

## <a name="see-also"></a>Ayrıca Bkz
[Ayıklaıcı oluşturma](create-an-extractor.md)

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Modeli yeniden adlandırma](rename-a-model.md)

[Açıklama türleri](explanation-types-overview.md)

[Ayıklaıcı oluştururken terim deposu taksonomilerinden faydalanma](leverage-term-store-taxonomy.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Model uygulama](apply-a-model.md) 
