---
title: Microsoft SharePoint Syntex'da önceden oluşturulmuş modellere genel SharePoint Syntex
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
description: Microsoft SharePoint Syntex'da önceden oluşturulmuş modeller hakkında bilgi SharePoint Syntex.
ms.openlocfilehash: 1146e4947392ce0e0848632e55f22e5b8b8d2d91
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569058"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da önceden oluşturulmuş modellere genel SharePoint Syntex

SharePoint Syntex, [modellerin](document-understanding-overview.md) ve [form](form-processing-overview.md) işleme modellerinin anlaşılmasını belgelemenin yanı sıra, bilgi ayıklamayı otomatikleştirmek için önceden oluşturulmuş modeller sağlar.

Önceden oluşturulmuş modeller belgeleri ve belgelerde yer alan yapılandırılmış bilgileri tanıyacak şekilde kısıtlanmıştır. Sıfırdan yeni bir özel model oluşturmak yerine, var olan bir kısıtlanmış modelin üzerinde kuruma uygun belirli alanlar eklemek için bu modeli iterebilirsiniz. 

Önceden oluşturulmuş modeller, belirli belge türlerinde ortak olan önceden tanımlanmış metin ve veri alanlarını tanımlamak ve ayıklamak için optik karakter tanıma (OCR) ile birlikte derin öğrenme modelleri kullanır. Dosyalarınızı önceden oluşturulmuş modele göre çözümlemeye başlar. Ardından, amacınıza anlam ifade etmek için algılanan alanları seçersiniz. Model ihtiyacınız olan alanları algılayamazsa, farklı bir dosya kullanarak yeniden çözümebilirsiniz.

Modelleri anan belge gibi, önceden oluşturulmuş modeller de içerik merkezinde oluşturulur [ve yönetilir](create-a-content-center.md). Belge kitaplığına SharePoint, model bir içerik türüyle ilişkilendirilr ve ayıklanan bilgileri depolamak için sütunları vardır. 

Modelinizi yayımlandıktan sonra, erişiminiz olan herhangi bir belge kitaplığına SharePoint için içerik merkezini kullanın.  

## <a name="requirements"></a>Gereksinimler

- Desteklenen dosya biçimleri: JPEG, PNG, BMP, TIFF ve PDF (metin eklenmiş veya taranmış).

- Desteklenen diller: Şu anda faturalardan yalnızca Birleşik Devletler dili faturaları desteklemektedir. Avustralya, Kanada, İngiltere, Birleşik Devletler Hindistan'dan yapılan İngilizce satış makbuzları da desteklemektedir.

- Metin ekli PDF'ler, karakter ayıklama ve konumlarda hata olasılığını ortadan kaldırmak için en iyisidir.

- PDF ve TIFF için, en çok 2.000 sayfa işlenebilir.

- Dosya boyutu 50 MB'den küçük olmalıdır.

- Resim boyutları 50 x 50 piksel ile 10.000 x 10.000 piksel arasında olmalıdır.

- PDF boyutları en çok 17 x 17 inçtir ve Legal veya A3 kağıt boyutuna karşılık gelen veya daha küçüktür.

- Eğitim verilerin toplam boyutu 500 veya daha azdır.

### <a name="file-limitations"></a>Dosya sınırlamaları

Metin tabanlı dosyalar ve OCR taranmış Microsoft Office (PDF, resim veya TIFF) ilgili olarak aşağıdaki farklara dikkat edin:

- Office: 64.000 karakterde kesilmiş (belge kitaplığında dosyalarda çalıştırılırken).

- OCR taranan dosyalar: 20 sayfalık bir sınır vardır.  

## <a name="model-considerations"></a>Modelde dikkate alınacak noktalar

- Aynı kitaplı kitaplara önceden oluşturulmuş iki veya daha fazla model varsa, dosya en yüksek ortalama güven puanına sahip model kullanılarak sınıflandırılır. Ayıklanan varlıklar yalnızca uygulanan modelden olur.

- Belge anlama modeline sahip bir kitaplı kitaplara önceden oluşturulmuş bir model uygulanmışsa, dosya, belge anlama modeli ve bu model için eğitilmiş ayıknıcılar kullanılarak sınıflandırılır. Önceden oluşturulmuş modele uygun boş sütunlar varsa, sütunlar bu ayıklanan değerler kullanılarak doldurulur.

- Önceden oluşturulmuş bir model, özel form işleme modeli olan bir kitaplı kitaplara uygulanırsa, dosya önceden oluşturulmuş modeli ve bu model için algılanan ayıklamaların herhangi birini kullanarak sınıflandırılır. Form işleme modeliyle eşleşmeye devam eden boş sütunlar varsa, sütunlar bu ayıklanan değerler kullanılarak doldurulur.

- Kitaplı kitaplı kitaplı kitaplara birden fazla özel form işleme modeli uygulama desteklenmiyor.


## <a name="see-also"></a>Ayrıca Bkz

[Faturalardan veya faturalardan bilgi ayıklamak için önceden oluşturulmuş bir model kullanın](prebuilt-overview.md)
 

