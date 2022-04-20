---
title: Microsoft SharePoint Syntex'da önceden oluşturulmuş modellere genel bakış
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex'da önceden oluşturulmuş modeller hakkında bilgi edinin.
ms.openlocfilehash: d43a608885864f5c81a8938010a0a52a2c4998a6
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916237"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da önceden oluşturulmuş modellere genel bakış

SharePoint Syntex, [belgeleri anlama modellerine](document-understanding-overview.md) ve [form işleme modellerine](form-processing-overview.md) ek olarak, bilgilerin ayıklanmını otomatikleştirmek için önceden oluşturulmuş modeller sağlar.

Önceden oluşturulmuş modeller, belgeleri ve belgelerdeki yapılandırılmış bilgileri tanımak için önceden eğitilir. Sıfırdan yeni bir özel model oluşturmak yerine, kuruluşunuzun gereksinimlerine uygun belirli alanlar eklemek için önceden eğitilmiş mevcut bir modeli yineleyebilirsiniz. 

Önceden oluşturulmuş modeller, belirli belge türlerinde ortak olan önceden tanımlanmış metin ve veri alanlarını tanımlamak ve ayıklamak için derin öğrenme modelleriyle birlikte optik karakter tanıma (OCR) kullanır. Dosyalarınızdan birini önceden oluşturulmuş modele göre analiz ederek işe başlarsınız. Ardından, amacınız için anlamlı olan algılanan alanları seçersiniz. Model ihtiyacınız olan alanları algılamazsa farklı bir dosya kullanarak yeniden analiz edebilirsiniz.

Belge anlama modelleri gibi, önceden oluşturulmuş modeller [de içerik merkezinde](create-a-content-center.md) oluşturulur ve yönetilir. SharePoint belge kitaplığına uygulandığında, model bir içerik türüyle ilişkilendirilir ve ayıklanan bilgilerin depolandığı sütunlara sahiptir. 

Modelinizi yayımladıktan sonra, erişiminiz olan herhangi bir SharePoint belge kitaplığına uygulamak için içerik merkezini kullanın.  

## <a name="requirements"></a>Gereksinimler

- Desteklenen dosya biçimleri: JPEG, PNG, BMP, TIFF ve PDF (metin eklenmiş veya taranmış).

- Desteklenen diller: Şu anda yalnızca Birleşik Devletler İngilizce dil faturaları desteklenmektedir. Avustralya, Kanada, Birleşik Devletler, Büyük Britanya ve Hindistan'dan İngilizce satış makbuzları desteklenir.

- Metin eklenmiş PDF'ler, karakter ayıklama ve konum hata olasılığını ortadan kaldırmak için en iyisidir.

- PDF ve TIFF için en fazla 2.000 sayfa işlenebilir.

- Dosya boyutu 50 MB'tan küçük olmalıdır.

- Görüntü boyutları 50 x 50 piksel ile 10.000 x 10.000 piksel arasında olmalıdır.

- PDF boyutları, Yasal veya A3 kağıt boyutuna karşılık gelen en fazla 17 x 17 inç veya daha küçüktür.

- Eğitim verilerinin toplam boyutu 500 sayfa veya daha azdır.

### <a name="file-limitations"></a>Dosya sınırlamaları

metin tabanlı dosyalar ve OCR ile taranan dosyalar (PDF, görüntü veya TIFF) Microsoft Office aşağıdaki farklara dikkat edin:

- Office dosyaları: 64.000 karakterde kesilir (belge kitaplığındaki dosyalarda çalıştırıldığında).

- OCR ile taranan dosyalar: 20 sayfalık bir sınır vardır.  

## <a name="model-considerations"></a>Modelle ilgili dikkat edilmesi gerekenler

- Aynı kitaplığa önceden oluşturulmuş iki veya daha fazla model uygulanırsa, dosya en yüksek ortalama güvenilirlik puanına sahip model kullanılarak sınıflandırılır. Ayıklanan varlıklar yalnızca uygulanan modelden olacaktır.

- Belge anlama modeline sahip bir kitaplığa önceden oluşturulmuş bir model uygulanırsa, dosya belge anlama modeli ve bu model için eğitilen ayıklayıcılar kullanılarak sınıflandırılır. Önceden oluşturulmuş modelle eşleşen boş sütunlar varsa, sütunlar ayıklanan bu değerler kullanılarak doldurulur.

- Özel form işleme modeline sahip bir kitaplığa önceden oluşturulmuş bir model uygulanırsa, dosya önceden oluşturulmuş model ve bu model için algılanan ayıklayıcılar kullanılarak sınıflandırılır. Form işleme modeliyle eşleşen boş sütunlar varsa, bu ayıklanan değerler kullanılarak sütunlar doldurulur.

- Kitaplığa birden fazla özel form işleme modeli uygulanması desteklenmez.


## <a name="see-also"></a>Ayrıca bkz.

[Faturalardan veya makbuzlardan bilgi ayıklamak için önceden oluşturulmuş bir model kullanma](prebuilt-overview.md)
 

