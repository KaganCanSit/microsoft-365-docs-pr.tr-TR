---
title: Microsoft SharePoint Syntex'da belgeyi anlama genel bakış
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
description: Microsoft SharePoint Syntex'da belgeyi anlama hakkında bilgi SharePoint Syntex.
ms.openlocfilehash: 0c72c4e0d3865a7247db78760d02a51f7f91dbcf
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016521"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da belgeyi anlama genel bakış


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

Belge kullanımı yapay zeka (AI) modellerini, dosyaların sınıflandırması ve bilgi ayıklamayı otomatikleştirmek için kullanır. Mektuplar veya sözleşmeler gibi yapılandırılmamış belgelerle en iyi şekilde çalışır. Bu belgelerde, tümceciklere veya desenlere göre tanım edilemeyen metinler olması gerekir. Tanımlanan metin, hem dosyanın türünü (sınıflandırması) hem de ayıklamak istediğiniz dosyayı (ayıklar) belirtir.

> [!NOTE]
> Senaryo örneklerini [SharePoint Syntex: Senaryo örneklerini belge anlama](./adoption-getstarted.md) hakkında daha fazla bilgi edinmek için kılavuza bakın.

Belge anlama modelleri, içerik merkezi olarak adlandırılan bir SharePoint site içinde *oluşturulur ve yönetilir*. Bir belge kitaplığına SharePoint, modelin ayıklanan bilgileri depolamak için sütunları olan bir içerik türüyle ilişkilendirildi. Kendi oluşturtuz içerik türü, SharePoint galerisinde depolanır. Şemalarını kullanmak için mevcut içerik türlerini de kullanabilirsiniz.

> [!NOTE]
> Salt okunur veya gizli içerik türleri güncelleştirilemez, dolayısıyla bir modelde kullanılamaz.

Aşağıdaki *eylemleri yapmak için* *belgenize sınıflayıcılar* ve ayıklayıcılar ekleyin, modelleri anlama: 

- Sınıflayıcılar, belge kitaplığına yüklenen belgeleri tanımlamak ve sınıflandırmak için kullanılır. Örneğin, bir sınıflandırıcı kitaplı kitaplıya yüklenen tüm *sözleşme yenileme* belgelerini tanımlamak için "eğitimli" olabilir. Sınıflandırıcınızı  oluşturma işlemi, sözleşme yenileme içerik türü sizin tarafından tanımlanır.

- Ayıklar bu belgelerden bilgi çeker. Örneğin, belge kitaplığında tanımlanan her sözleşme yenileme belgesi için, her belge için Hizmet *Başlangıç Tarihi ve İstemcisi'nin* *görüntüleniyor* olduğu sütunlar görüntülenir. 

Modelde sınıflayıcılarınızı ve ayıklayıcılarınızı eğitmek ve test etmek için örnek dosyalar kullanabilirsiniz. Örnek dosyalar, dosyalardan verileri tanımlamaya ve ayıklamaya çalışırken ne bulmaya çalışabilirsiniz modelinize örnekler sağlar. Örneğin, sözleşme yenileme sınıflayıcılarınızı ve ayıklayıcılarınızı, şirketinizin birlikte çalıştığını sözleşme yenileme belgeleri örnekleriyle eğitebilirsiniz. Modelinizin ne kadar etkili olduğunu test etmek için örnek dosyalar da kullanabilirsiniz.

Modelinizi yayımlandıktan sonra, erişiminiz olan herhangi bir belge kitaplığına SharePoint için içerik merkezini kullanın.  

## <a name="file-limitations"></a>Dosya sınırlamaları

Modelleri kullanan belgelerde PDF'leri, resimleri ve TIFF dosyalarını taramak için Optik Karakter Tanıma (OCR) teknolojisi kullanılır. Bir modeli örnek dosyalarla eğitip, modeli belge kitaplığında dosyalara karşı çalıştırdığında dosyalar taranır.

Metin tabanlı dosyalar ve OCR taranmış Microsoft Office (PDF, resim veya TIFF) ilgili olarak aşağıdaki farklara dikkat edin:

- Office: 64.000 karakterde kesilmiş (eğitimde ve belge kitaplığında dosyalarda çalıştırılırken).

- OCR taranan dosyalar: 20 sayfalık bir sınır vardır.  

### <a name="requirements"></a>Gereksinimler

OCR işleme, aşağıdaki gereksinimleri karşıleyen belgeler üzerinde en iyi şekilde çalışır:

- JPG, PNG veya PDF biçimi (metin veya taranmış). Metin ekli PDF'ler daha iyidir, çünkü karakter ayıklama ve konumda hata olmayacaktır.

- PDF'lerinizi parola kilitliyse, göndermeden önce kilidi kaldırmanız gerekir.

- Koleksiyon başına eğitim için kullanılan belgelerin birleştirilmiş dosya boyutu 50 MB'yi geçmemektedir ve PDF belgelerinin 500'den fazla sayfası olmaması gerekir.

- Resimler için boyutların 50 ile 50 × 10.000 × 10.000 piksel arasında olması gerekir.
   > [!NOTE]
   > Çok geniş olan veya tek boyutları olan resimler (örneğin, kat planları) OCR işlemi içinde kesilebilir ve doğruluğu kaybedebilir.
 
- PDF dosyaları için, boyutların Yasal veya A3 kağıt boyutlarına karşılık gelen en fazla 17 x 17 inç ve daha küçük olması gerekir.

- Kağıt belgelerden taranmışsa, taramaların yüksek kaliteli resimler olması gerekir.

- Latin alfabesi (İngilizce karakterler) kullanmalıdır.

> [!NOTE]
> AI Builder şu anda aşağıdaki form işleme giriş verilerini desteklememektedir:<br>- Onay kutuları veya radyo düğmeleri<br>- İmzalar<br>- Doldurulabilir PDF'ler

### <a name="supported-file-types"></a>Desteklenen dosya türleri

Belge anlama modelleri aşağıdaki dosya türlerini destekler:

- belge
- docx
- eml
- heic
- heif
- htm
- html
- jpeg
- jpg
- markdown
- md
- msg
- pdf
- png
- ppt
- pptx
- rtf
- tif
- tiff
- txt
- xls
- xlsx

### <a name="supported-languages"></a>Desteklenen diller

Belge anlama modelleri aşağıdaki dilleri destekler:
- French
- German
- Italian
- Spanish


## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[İçerik merkezi oluşturma](create-a-content-center.md)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)

[Model uygulama](apply-a-model.md)   

[Belgeyi anlama ve form işleme modeli arasındaki fark](difference-between-document-understanding-and-form-processing-model.md)
  
[Form işlemeye genel bakış](form-processing-overview.md)

[SharePoint Syntex Modu](accessibility-mode.md)
