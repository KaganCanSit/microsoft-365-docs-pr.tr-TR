---
title: Microsoft SharePoint Syntex'da modeli yeniden adlandırma
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
description: Microsoft web sitesinde belge anlama modelini nasıl ve neden yeniden adlandır SharePoint Syntex.
ms.openlocfilehash: b1ced765d7a69fdf8b9fe9eb44d6716a840bf8a0
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450304"
---
# <a name="rename-a-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da modeli yeniden adlandırma

Bir noktada, belge anlama modelini yeniden adlandırmak iyi olabilir. Bunun yaygın bir örneği, modelin ilk taslağını  hazırlarken son adı iyi iyi düşünemeyebileceksiniz (örneğin, buna "AlexWilburModel1" adını verdiysiniz). Modelin sonlandırılması ve kullanımının ne kadar yakın olduğunu fark ettiyken, daha doğru bir adın "Sözleşme Yenilemeleri" olduğunu fark etti ve adını yeniden adlandırmak istiyor oldu.  

Diğer bir örnek de, kuruluş bir işlem veya belge türüne farklı bir adla başvurarak karar vermesindedir. Örneğin, modelinizi oluşturduk ve bunu uygulamaya hazır olduktan sonra, organizasyonunız tüm "Sözleşmeler" için artık resmi olarak "Sözleşmeler" olarak adlandırılan velilerde yer almaktadır. Gerekirse modelinizi "Sözleşme Yenilemeleri" olan modelinizi "Sözleşme Yenilemeleri" olarak yeniden adlandırmayı seçebilirsiniz.

> [!IMPORTANT]
> Belge anlama modelini yalnızca belge kitaplığına uygulanmadı olarak yeniden adlandırabilirsiniz. 

Modeli yeniden adlandırmak, modelle [ilişkilendirilmiş içerik](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) türünü de yeniden adlandırıyor.

## <a name="rename-a-model"></a>Modeli yeniden adlandırma

Belge anlama modelini yeniden adlandırmak için bu adımları izleyin.

1. Model listenizi görmek için içerik **merkezinde** Modeller'i seçin.

2. Modeller **sayfasında** , yeniden adlandırmak istediğiniz modeli seçin.

3. Şeridi veya Eylemleri göster düğmesini **kullanarak** (model adının yanında) Yeniden Adlandır'ı **seçin**. </br>

    ![Yeniden Adlandır seçenekleri vurgulanmış seçili bir modeli gösteren Modeller sayfasının ekran görüntüsü.](../media/content-understanding/select-model-rename-both.png) </br>

4. Modeli yeniden **adlandır panelinde** :

   a. Yeni **ad'ın** altında, yeniden adlandırmak istediğiniz modelin yeni adını girin.</br>

    ![Modeli yeniden adlandır panelini gösteren ekran görüntüsü.](../media/content-understanding/rename-model-panel.png) </br>

   b. (İsteğe bağlı) Gelişmiş **ayarlar'ın** altında, var olan bir içerik türünü ilişkilendirmek isteyip [istemiyorsanız bunu seçin](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview). Varolan bir **içerik türünü kullan'ı seçerseniz** model, seçilen içerik türüyle eş olacak şekilde yeniden adlandırılır.

5. Yeniden **Adlandır'ı seçin**.

## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Ayıklayı yeniden adlandırma](rename-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Açıklama türleri](explanation-types-overview.md)

[Model uygulama](apply-a-model.md) 
