---
title: Gözden Geçir
description: Eklemeden sonra bölümü gözden geçirme.
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 3bb6ef605d360e259ef9fa91ed51da35506a2942
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988720"
---
# <a name="step-6-review-your-selections-to-create-your-package"></a>6. Adım: Paketinizi oluşturmak için seçimlerinizi gözden geçirme.

1. Bu sekmede, hizmet test ayrıntılarınızı görüntüler ve hızlı bir eksiksizlik denetimi çalıştırır.

    Doğrulama **geçirildi veya** Doğrulama **başarısız oldu iletisi** , sonraki adımlarla devam edip e-postayla devam edip olmadığınızı gösterir.

2. Test ayrıntılarınızı gözden geçirebilirsiniz ve memnunsanız **Oluştur düğmesine tıklayın** .

    :::image type="content" alt-text="Doğrulamayı görüntüleme." source="Media/validation.png" lightbox="Media/validation.png":::

3. Bu, paketinizi Test Temel ortamına sunar. Paketiniz başarıyla oluşturulduktan sonra, paketinizin Azure'da başarıyla yürütülip yürütüleneb başarıyla yürütüleb başarıyla yürütüleb başarıyla çalıştırılamayacaklarını doğrulayan otomatik bir test tetiklenir.

    ![Başarılı sonuç.](Media/successful.png)

    > [!NOTE]
    > Paket doğrulamasının başarılı veya başarısız olduğunu bildirmek için Azure portaldan bir bildirim alırsınız.
    >
    > Bu işlem 24 saate kadar sürebilir, dolayısıyla bu nedenle etkin değilken web sayfanız zaman aşımına neden olabilir; bu nedenle, bildirim bu isteğe bağlı çalıştırmanın tamamlanması konusunda sizi bilgilendirmez.

    - Peradventure bu durumda, Paketinizin durumunu Paketleri yönet **sekmesinde görüntüleyebilirsiniz** .

      :::image type="content" alt-text="Paketleri yönetme resmi." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - Başarılı testler için, sonuçları zamanlanmış aralıklarla (genellikle karşıya yüklemeden  birkaç gün sonra başlayarak) **Test** Özeti, Güvenlik Güncelleştirmeleri Sonuçları ve Özellik Güncelleştirmeleri Sonuçları sayfaları aracılığıyla görülebilir.
  
    - Başarısız testler yaparken, yeni bir paket yüklemenizi gerektirir. 

      Güvenlik güncelleştirmesi sonuçları **ve Özellik** güncelleştirmeleri sonuçları sayfalarından daha fazla çözümleme **yapmak için** test **günlüklerini** indirebilirsiniz.

    - Tekrarlanan test hatalarına neden oluyorsanız lütfen hatanın testbasepreview@microsoft.com ayrıntılarıyla size ulaşmak için iletişime geçin.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bağlantıyı kullanarak İçerik Yönergelerimizi keşfedin.

> [!div class="nextstepaction"]
> [Sonraki adım](contentguideline.md)
