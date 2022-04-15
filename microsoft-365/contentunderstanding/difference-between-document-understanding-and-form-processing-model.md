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
ms.openlocfilehash: f6fe6e821e41b47bcce6ef157d971245fdd072b8
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882296"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Belge anlama ve form işleme modelleri arasındaki farklar 

Microsoft SharePoint Syntex'da içerik anlama, SharePoint belge kitaplıklarına yüklenen belgeleri tanımlamanıza ve sınıflandırmanıza ve ardından her dosyadan ilgili bilgileri ayıklamanıza olanak tanır. Örneğin, dosyalar bir SharePoint belge kitaplığına yüklendiğinden, *Satın Alma Siparişleri* olarak tanımlanan tüm dosyalar bu şekilde sınıflandırılır ve sonra özel belge kitaplığı görünümünde görüntülenir. Ayrıca, her dosyadan belirli bilgileri (po *numarası* ve *toplam* gibi) çekebilir ve belge kitaplığı görünümünüzde bir sütun olarak görüntüleyebilirsiniz. 

İçerik anlama, ihtiyacınız olan bilgileri tanımlamak ve ayıklamak için *modeller* oluşturmanıza olanak tanır. Modellerin arama, iş süreçleri, uyumluluk ve diğerleri için iş sorunlarını çözmeye yardımcı olması önemlidir.

Kullanabileceğiniz iki özel model türü vardır:

- [Modelleri belge anlama](document-understanding-overview.md)
- [Form işleme modelleri](form-processing-overview.md)

Her iki model de genellikle aynı amaç için kullanılırken, aşağıda listelenen temel farklar hangilerini kullanabileceğinizi etkiler.

> [!NOTE]
> Form işleme ve belge anlama senaryosu örnekleri hakkında daha fazla bilgi için [SharePoint Syntex benimseme: Kullanmaya başlayın kılavuzuna](./adoption-getstarted.md) bakın.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Yapılandırılmış veya yapılandırılmamış ve yarı yapılandırılmış içerik

Ayıklamak istediğiniz metin varlıklarının cümleler veya belgenin belirli bölgelerinde olduğu, mektuplar veya sözleşmeler gibi yapılandırılmamış belgelerden veri tanımlamak ve ayıklamak için belge anlama modellerini kullanın. Örneğin, yapılandırılmamış bir belge, farklı şekillerde yazılabilen bir sözleşme yenileme mektubu olabilir. Ancak bilgiler, hizmet başlangıç tarihi ve ardından gerçek bir tarih metin dizesi gibi her sözleşme yenileme *belgesinin gövdesinde* tutarlı bir şekilde bulunur.

Dosyaları tanımlamak ve formlar veya faturalar gibi yapılandırılmış veya yarı yapılandırılmış belgelerden veri ayıklamak için form işleme modellerini kullanın. Form işleme modelleri, örnek belgelerden formunuzun düzenini anlamak ve benzer konumlardan ayıklamak için ihtiyacınız olan verileri aramayı öğrenmek için eğitilir. Formlar genellikle varlıkların aynı konumda olduğu daha yapılandırılmış bir düzene sahiptir (örneğin, vergi formundaki bir sosyal güvenlik numarası).

> [!NOTE]
> Belge anlama modeli oluşturmak veya bir SharePoint belge kitaplığına uygulamak için içerik merkezi sitesine erişiminiz olmalıdır. 

## <a name="where-models-are-created"></a>Modellerin oluşturulduğu yer

Belge anlama modelleri bir SharePoint içerik merkezi sitesinde oluşturulur ve yönetilir. 

> [!NOTE]
> Giriş belgeleri hakkında daha fazla bilgi için bkz. [Form işleme modeli gereksinimleri ve sınırlamaları](/ai-builder/form-processing-model-requirements). 

Form işleme modelleri Power Apps [AI Builder'da](/ai-builder/overview) oluşturulur, ancak oluşturma işlemi doğrudan SharePoint belge kitaplığından başlar. Bir kullanıcının form işleme modeli oluşturabilmesi için önce belge kitaplığında form işleme modeli oluşturma özelliğinin etkinleştirilmesi gerekir. Yöneticiler, içerik anlama yönetici ayarlarında form işleme modeli oluşturmayı etkinleştirebilir. Form işleme modelleri, belge kitaplığına yüklenen dosyaları işlemek için Power Automate akışları kullanır.

Belge anlama modeli oluşturduğunuzda, SharePoint İçerik Türleri galerisine kaydedilen yeni bir SharePoint [içerik türü](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) oluşturursunuz. Gerekirse modelinizi tanımlamak için mevcut içerik türlerini de kullanabilirsiniz.

bir içerik türü oluşturulduktan ve bir modelle ilişkilendirildikten sonra, **Site İçerik Türü** özellik panelinden bu modele de başvurabilirsiniz.

![Belge anlama modelinin vurgulandığı Site İçerik Türü panelinin ekran görüntüsü.](../media/content-understanding/site-content-type-panel.png)

Form işleme modelleri ayrıca yeni [SharePoint içerik türleri](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) oluşturur ve SharePoint İçerik Türleri galerisinde de depolanır.

## <a name="where-they-can-be-applied"></a>Uygulanabilecek yerler

Erişiminiz olan SharePoint belge kitaplıklarına belge anlama modelleri uygulayabilirsiniz. İçerik merkezini kullanarak belge anlama modeli oluşturun ve bunu farklı belge kitaplıklarına uygulayın. İçerik merkezi, belge anlama modellerinin nasıl kullanıldığı ve bunların nereye uygulandığı konusunda size daha merkezi bir denetim sağlar. Bu bilgilerin bir içerik merkezine de toplanmış olması gerektiğini unutmayın.

Form işleme modelleri şu anda yalnızca bunları oluşturduğunuz SharePoint belge kitaplığına uygulanabilir. Bu, siteye erişimi olan lisanslı kullanıcıların form işleme modeli oluşturmasına olanak tanır. Bir yöneticinin lisanslı kullanıcıların kullanımına sunulabilmesi için SharePoint belge kitaplığında form işlemeyi etkinleştirmesi gerektiğini unutmayın.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Form işleme ve belge anlama karşılaştırması

Form işlemenin ne zaman kullanılacağını ve belge anlamanın ne zaman kullanılacağını anlamak için aşağıdaki tabloyu kullanın.

| Özellik | Form işleme | Belge anlama |
| ------- | ------- | ------- |
| Model türü - her bir modelin ne zaman kullanılacağı | Düzenin ve biçimlendirmenin benzer olduğu faturalar veya satın alma siparişleri gibi form içeriğine yönelik PDF'ler gibi yarı yapılandırılmış dosya biçimleri için kullanılır.  | Yarı yapılandırılmış dosya biçimleri için kullanılır; örneğin, düzende farklılıklar olan belgeler Office, ancak yine de ayıklanacak benzer bilgiler. |
| Model oluşturma | SharePoint belge kitaplığından sorunsuz erişimle yapay zeka oluşturucusunda oluşturulan model.| İçerik merkezi olan yeni bir sitede SharePoint oluşturulan model. |
| Sınıflandırma türü| Ayarlanabilir sınıflandırıcı, sisteme hangi verilerin ayıklanacağı konusunda ipuçları vermek için kullanılır.| Hangi verilerin ayıklanması için belge konumu atamak için makine öğretimi kullanan isteğe bağlı ayıklayıcılarla eğitilebilir sınıflandırıcı.|
| Konum | Tek bir belge kitaplığı için eğitildi.| Birden çok kitaplık için uygulanabilir.|
| Desteklenen dosya türleri| PDF, JPG, PNG biçiminde, toplam 50 MB ve 500 sayfada eğitin.| Negatif örnekler de dahil olmak üzere 5-10 PDF, Office veya e-posta dosyaları üzerinde eğitin.<br>Office dosyalar 64k karakterde kesilir. OCR ile taranan dosyalar 20 sayfayla sınırlıdır.|
| Yönetilen meta verilerle tümleştirme | Hayır | Evet, yapılandırılmış yönetilen meta veri alanına başvuran varlık ayıklayıcısı eğiterek.|
| Microsoft Bilgi Koruması etkinleştirildiğinde uyumluluk özelliği tümleştirmesi | Yayımlanan Bekletme etiketlerini ayarlayın.<br>Duyarlılık etiketlerini ayarlama geliyor. | Yayımlanan Bekletme etiketlerini ayarlayın.<br>Yayımlanan Duyarlılık etiketlerini ayarlayın. |
| Desteklenen bölgeler| Form işleme, Power Platform'a dayanır. Power Platform ve AI Builder için genel kullanılabilirlik hakkında bilgi için bkz. [Power Platform kullanılabilirliği](https://dynamics.microsoft.com/geographic-availability/). | Tüm bölgelerde kullanılabilir.|
| İşlem maliyeti | AI Builder kredilerini kullanır.<br>Krediler 1M toplu olarak satın alınabilir.<br>300+SharePoint Syntex lisansları satın alındığında 1M kredi dahil edilir.<br>1M kredi, 2.000 dosya sayfası işlenmesine izin verir.<br>| Yok |
| Kapasite | Varsayılan Power Platform ortamını kullanır (Dataverse veritabanının desteklendiği özel ortamlar). | Kapasite kısıtlamaları yoktur.|
| Desteklenen diller| [Daha fazla 73 dil için dil](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support) desteği. | Modeller tüm Latin alfabesi dillerinde çalışır. İngilizceye ek olarak: Almanca, İsveççe, Fransızca, İspanyolca, İtalyanca ve Portekizce.|


## <a name="see-also"></a>Ayrıca bkz.

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Belge anlamaya genel bakış](document-understanding-overview.md)

[Form işlemeye genel bakış](form-processing-overview.md)

[SharePoint Syntex giriş](index.md)
