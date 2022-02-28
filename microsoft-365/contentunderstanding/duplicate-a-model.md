---
title: Microsoft SharePoint Syntex'da modeli çoğaltma
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
description: Microsoft SharePoint Syntex'da bir modeli nasıl ve neden çoğaltılmış SharePoint Syntex.
ms.openlocfilehash: dc8668ccf407e881bb2114cb679b1ed2049c256e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983485"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da modeli çoğaltma

Belgeyi anlama modelini çoğaltmak, yeni bir model oluşturmanız gerekirse size zaman ve emek tasarrufu sağlar ve var olan bir modelin size gerekenlere çok ben ben olduğunu bilirsiniz.

Örneğin, "Sözleşmeler" adında var olan bir model, üzerinde çalışmak zorunda olduğunuz dosyaları sınıflara sınıflardır. Yeni modeliniz var olan verilerin bir'ini ayıklar, ancak bazı ek verileri ayıklamak için güncelleştirilmiş olması gerekir. Sıfırdan yeni bir model oluşturmak ve bu modeli eğitime vermek yerine, yinelenen model özelliğini kullanarak Sözleşmeler modelinin bir kopyasını elde edersiniz. Bu, örnek dosyalar ve varlık ayıklama öğeleri gibi tüm ilişkili eğitim öğelerini de kopyalar.

Modeli yineledikten sonra yeniden adlandırdıktan (örneğin, "Sözleşme Yenilemeleri" olarak) sonra modelin güncelleştirmelerini de abilirsiniz. Örneğin, ihtiyaç olmadığınız mevcut ayıklanan alanlardan bazılarını kaldırmayı seçebilir ve modeli yenisini ayıkla (örneğin, "Yenileme tarihi") için eğitebilirsiniz.

## <a name="duplicate-a-model"></a>Modeli çoğaltma

Belge anlama modelini çoğaltmak için bu adımları izleyin.

1. Model listenizi görmek için içerik **merkezinde** Modeller'i seçin.

2. Modeller **sayfasında** , çoğaltmak istediğiniz modeli seçin.

3. Şeridi veya Eylemleri göster düğmesini **kullanarak** (model adının yanında) Çoğalt'ı **seçin**.</br>

    ![Yinele seçenekleri vurgulanmış seçili bir modeli gösteren Modeller sayfasının ekran görüntüsü.](../media/content-understanding/select-model-duplicate-both.png) </br>

4. Çoğalt **modeli panelinde** :

   a. **Ad'ın** altında, çoğaltmak istediğiniz modelin yeni adını girin.</br>

    ![Çoğalt modeli panelini gösteren ekran görüntüsü.](../media/content-understanding/duplicate-model-panel.png) </br>

   b. **Açıklama'nın** altında, yeni modelinizin açıklamasını ekleyin.

   c. (İsteğe bağlı) Gelişmiş **ayarlar'ın** altında, var olan bir içerik türünü ilişkilendirmek isteyip [istemiyorsanız bunu seçin](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview).

5. **Çoğalt'ı seçin**.

## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Modeli yeniden adlandırma](rename-a-model.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Açıklama türleri](explanation-types-overview.md)

[Model uygulama](apply-a-model.md) 

[SharePoint Syntex Modu](accessibility-mode.md)