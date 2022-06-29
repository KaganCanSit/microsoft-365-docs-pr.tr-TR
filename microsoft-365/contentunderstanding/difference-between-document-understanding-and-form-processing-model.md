---
title: Belge anlama ve form işleme modelleri arasındaki farklar
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Belge anlama modeli ile form işleme modeli arasındaki temel farklar hakkında bilgi edinin.
ms.openlocfilehash: 49e3e2a0d63303b1c5cbdbfd941ba8aaa40594a7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66491713"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Belge anlama ve form işleme modelleri arasındaki farklar 

Microsoft SharePoint Syntex'da içerik anlama, SharePoint belge kitaplıklarına yüklenen belgeleri tanımlamanıza ve sınıflandırmanıza ve ardından her dosyadan ilgili bilgileri ayıklamanıza olanak tanır. Örneğin, dosyalar bir SharePoint belge kitaplığına yüklendiğinden, *Satın Alma Siparişleri* olarak tanımlanan tüm dosyalar bu şekilde sınıflandırılır ve sonra özel belge kitaplığı görünümünde görüntülenir. Ayrıca, her dosyadan belirli bilgileri (po *numarası* ve *toplam* gibi) çekebilir ve belge kitaplığı görünümünüzde bir sütun olarak görüntüleyebilirsiniz. 

İçerik anlama, ihtiyacınız olan bilgileri tanımlamak ve ayıklamak için *modeller* oluşturmanıza olanak tanır. Modellerin arama, iş süreçleri, uyumluluk ve diğerleri için iş sorunlarını çözmeye yardımcı olması önemlidir.

Kullanabileceğiniz iki özel model türü vardır:

- [Modelleri belge anlama](document-understanding-overview.md)
- [Form işleme modelleri](form-processing-overview.md)

Her iki model de genellikle aynı amaç için kullanılırken, aşağıda listelenen temel farklar hangilerini kullanabileceğinizi etkiler.

> [!NOTE]
> Form işleme ve belge anlama senaryosu örnekleri hakkında daha fazla bilgi için [bkz. SharePoint Syntex benimsemeye başlama](./adoption-getstarted.md).

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Yapılandırılmış veya yapılandırılmamış ve yarı yapılandırılmış içerik

Ayıklamak istediğiniz metin varlıklarının cümleler veya belgenin belirli bölgelerinde olduğu, mektuplar veya sözleşmeler gibi yapılandırılmamış belgelerden veri tanımlamak ve ayıklamak için belge anlama modellerini kullanın. Örneğin, yapılandırılmamış bir belge, farklı şekillerde yazılabilen bir sözleşme yenileme mektubu olabilir. Ancak bilgiler, metin dizesi `Service start date of` ve ardından gerçek bir tarih gibi her sözleşme yenileme belgesinin gövdesinde tutarlı bir şekilde bulunur.

Dosyaları tanımlamak ve formlar veya faturalar gibi yapılandırılmış veya yarı yapılandırılmış belgelerden veri ayıklamak için form işleme modellerini kullanın. Form işleme modelleri, örnek belgelerden formunuzun düzenini anlamak ve benzer konumlardan ayıklamak için ihtiyacınız olan verileri aramayı öğrenmek için eğitilir. Formlar genellikle varlıkların aynı konumda olduğu daha yapılandırılmış bir düzene sahiptir (örneğin, vergi formundaki bir sosyal güvenlik numarası).

> [!NOTE]
> Belge anlama modeli oluşturmak veya sharepoint belge kitaplığına uygulamak için içerik merkezi sitesine erişiminiz olmalıdır. 

## <a name="where-models-are-created"></a>Modellerin oluşturulduğu yer

Belge anlama modelleri bir SharePoint içerik merkezi sitesinde oluşturulur ve yönetilir. 

> [!NOTE]
> Giriş belgeleri hakkında daha fazla bilgi için bkz. [Form işleme modeli gereksinimleri ve sınırlamaları](/ai-builder/form-processing-model-requirements). 

Form işleme modelleri Power Apps [AI Builder'da](/ai-builder/overview) oluşturulur, ancak oluşturma işlemi doğrudan bir SharePoint belge kitaplığından başlar. Bir kullanıcının form işleme modeli oluşturabilmesi için önce belge kitaplığında form işleme modeli oluşturma özelliğinin etkinleştirilmesi gerekir. Yöneticiler, içerik anlama yönetici ayarlarında form işleme modeli oluşturmayı etkinleştirebilir. Form işleme modelleri, belge kitaplığına yüklenen dosyaları işlemek için Power Automate akışlarını kullanır.

Belge anlama modeli oluşturduğunuzda, [SharePoint İçerik](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) Türleri galerisine kaydedilmiş yeni bir SharePoint içerik türü oluşturursunuz. Gerekirse modelinizi tanımlamak için mevcut içerik türlerini de kullanabilirsiniz.

bir içerik türü oluşturulduktan ve bir modelle ilişkilendirildikten sonra, **Site İçerik Türü** özellik panelinden bu modele de başvurabilirsiniz.

:::image type="content" source="../media/content-understanding/site-content-type-panel.png" alt-text="Belge anlama modelinin vurgulandığı Site İçerik Türü panelinin ekran görüntüsü." lightbox="../media/content-understanding/site-content-type-panel.png":::

Form işleme modelleri ayrıca yeni [SharePoint içerik türleri](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) oluşturur ve SharePoint İçerik Türleri galerisinde de depolanır.

## <a name="where-they-can-be-applied"></a>Uygulanabilecek yerler

Erişiminiz olan SharePoint belge kitaplıklarına belge anlama modelleri uygulayabilirsiniz. İçerik merkezini kullanarak belge anlama modeli oluşturun ve bunu farklı belge kitaplıklarına uygulayın. İçerik merkezi, belge anlama modellerinin nasıl kullanıldığı ve bunların nereye uygulandığı konusunda size daha merkezi bir denetim sağlar. Bu bilgilerin bir içerik merkezine de toplanmış olması gerektiğini unutmayın.

Form işleme modelleri şu anda yalnızca kendi oluşturduğunuz SharePoint belge kitaplığına uygulanabilir. Bu, siteye erişimi olan lisanslı kullanıcıların form işleme modeli oluşturmasına olanak tanır. Bir yöneticinin lisanslı kullanıcıların kullanımına sunulabilmesi için sharepoint belge kitaplığında form işlemeyi etkinleştirmesi gerektiğini unutmayın.

## <a name="comparison-of-form-processing-and-document-understanding"></a>Form işleme ve belge anlama karşılaştırması

Form işlemenin ne zaman kullanılacağını ve belge anlamanın ne zaman kullanılacağını anlamak için aşağıdaki tabloyu kullanın.

| Özellik | Form işleme | Belge anlama |
| ------- | ------- | ------- |
| Model türü - her bir modelin ne zaman kullanılacağı | Yapılandırılmış ve yarı yapılandırılmış dosya biçimleri, örneğin, düzen ve biçimlendirmenin benzer olduğu faturalar veya satın alma siparişleri gibi form içeriğine yönelik PDF'ler.  | Yapılandırılmamış veya yarı yapılandırılmış dosya biçimleri, örneğin, düzende farklılıklar olan ancak yine de ayıklanacak benzer bilgilerin bulunduğu Office belgeleri. |
| Model oluşturma | SharePoint belge kitaplığından sorunsuz erişimle yapay zeka oluşturucusunda oluşturulan model.| SharePoint'te içerik merkezi olan yeni bir sitede oluşturulan model. |
| Sınıflandırma türü| Ayarlanabilir sınıflandırıcı, sisteme hangi verilerin ayıklanacağı konusunda ipuçları vermek için kullanılır.| Hangi verilerin ayıklanması için belge konumu atamak için makine öğretimi kullanan isteğe bağlı ayıklayıcılarla eğitilebilir sınıflandırıcı.|
| Konum | Tek bir belge kitaplığı için eğitildi.| Birden çok kitaplık için uygulanabilir.|
| Desteklenen dosya türleri| PDF, JPG, PNG biçiminde, toplam 50 MB ve 500 sayfada eğitin.| Negatif örnekler de dahil olmak üzere 5-10 PDF, Office veya e-posta dosyaları üzerinde eğitin.<br>Office dosyaları 64.000 karakterle kesilir. OCR ile taranan dosyalar 20 sayfayla sınırlıdır. Belge anlama modelleri aşağıdaki dosya türlerini destekler doc, docx, eml, heic, heif, htm, html, jpeg, jpg, markdown, md, msg, pdf, png, ppt, pptx, rtf, tif, tiff, txt, xls ve xlsx.|
| Yönetilen Meta Verilerle Tümleştirme | Hayır | Evet, yapılandırılmış yönetilen meta veri alanına başvuran varlık ayıklayıcısı eğiterek.|
| Microsoft Purview Bilgi Koruması ile uyumluluk özelliği tümleştirmesi | Yayımlanan bekletme etiketlerini ayarlayın.<br>Duyarlılık etiketlerini ayarlama geliyor. | Yayımlanan bekletme etiketlerini ayarlayın.<br>Yayımlanan duyarlılık etiketlerini ayarlayın. |
| Desteklenen bölgeler| Form işleme, Power Platform'a dayanır. Power Platform ve AI Builder için genel kullanılabilirlik hakkında bilgi için bkz. [Power Platform kullanılabilirliği](https://dynamics.microsoft.com/geographic-availability/). | Tüm bölgelerde kullanılabilir.|
| İşlem maliyeti | AI Builder kredilerini kullanır.<br>Aylık her SharePoint Syntex lisansı için 3,5K kredi dahildir.<br>1M kredi, 2.000 dosya sayfası işlenmesine izin verir.<br>| Geçerli değil |
| Kapasite | Varsayılan Power Platform ortamını kullanır (Dataverse veritabanının desteklendiği özel ortamlar). | Kapasite kısıtlamaları yoktur.|
| Desteklenen diller| [73'ten fazla dil için dil](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support) desteği. | Modeller tüm Latin alfabesi dillerinde çalışır. İngilizceye ek olarak: Almanca, İsveççe, Fransızca, İspanyolca, İtalyanca ve Portekizce.|


## <a name="see-also"></a>Ayrıca bkz.

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Belge anlamaya genel bakış](document-understanding-overview.md)

[Form işlemeye genel bakış](form-processing-overview.md)

[SharePoint Syntex giriş](index.md)
