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
description: Microsoft SharePoint Syntex'da belge anlama modelini nasıl ve neden yeniden adlandıracağınızı öğrenin.
ms.openlocfilehash: 0044b237705e6a716efb6133db392c68b82c7a25
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916149"
---
# <a name="rename-a-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da modeli yeniden adlandırma

Bir noktada, belge anlama modelini yeniden adlandırmak isteyebilirsiniz. Bir modelin ilk taslağını oluşturduğunuzda, son adı çok fazla düşünmemiş olabilirsiniz (örneğin, modeli "AlexWilburModel1" olarak adlandırmış olabilirsiniz). Modeli son haline getirmeye ve kullanmaya yaklaştığınızda daha uygun bir adın "Sözleşme Yenilemeleri" olacağını fark eder ve modeli yeniden adlandırmak istersiniz.  

Bir diğer örnek de kuruluşunuzun bir işleme veya belge türüne farklı bir adla başvurma kararı verdiği durumdur. Örneğin, modelinizi oluşturduktan ve uygulamaya hazır olduktan sonra, kuruluşunuz tüm "Sözleşmelerin" artık resmi olarak "Sözleşmeler" olarak anılması zorunlu kılınabilir. Gerekirse modelinizi "Sözleşme Yenilemeleri" yerine "Sözleşme Yenilemeleri" olarak yeniden adlandırmayı seçebilirsiniz.

> [!IMPORTANT]
> Belge anlama modelini yalnızca belge kitaplığına uygulanmamışsa yeniden adlandırabilirsiniz. 

Modeli yeniden adlandırmak, modelle ilişkili [içerik türünü](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) de yeniden adlandırır.

## <a name="rename-a-model"></a>Modeli yeniden adlandırma

Belge anlama modelini yeniden adlandırmak için bu adımları izleyin.

1. model listenizi görmek için içerik merkezinde **Modeller'i** seçin.

2. **Modeller** sayfasında, yeniden adlandırmak istediğiniz modeli seçin.

3. Şeridi veya **Eylemleri göster** düğmesini (model adının yanında) kullanarak **Yeniden Adlandır'ı** seçin. </br>

    ![Yeniden Adlandırma seçeneklerinin vurgulandığı seçili modeli gösteren Modeller sayfasının ekran görüntüsü.](../media/content-understanding/select-model-rename-both.png) </br>

4. **Modeli yeniden adlandır** panelinde:

   a. **Yeni ad'ın** altında, yeniden adlandırmak istediğiniz modelin yeni adını girin.</br>

    ![Modeli yeniden adlandır panelini gösteren ekran görüntüsü.](../media/content-understanding/rename-model-panel.png) </br>

   b. (İsteğe bağlı) **Gelişmiş ayarlar'ın** altında mevcut [bir içerik türünü](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) ilişkilendirmek isteyip istemediğinizi seçin. **Var olan bir içerik türünü kullan'ı** seçerseniz model seçilen içerik türüyle eşleşecek şekilde yeniden adlandırılır.

5. **Yeniden Adlandır'ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Ayıklayıcıyı yeniden adlandırma](rename-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)

[Açıklama türleri](explanation-types-overview.md)

[Model uygulama](apply-a-model.md) 
