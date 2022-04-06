---
title: Belgeyi anlama ile form işleme modelleri arasındaki farklar
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
description: Belge anlama modeli ile form işleme modeli arasındaki önemli farkları öğrenin.
ms.openlocfilehash: e5de4c55cc8a559ad03d722b1f7235797db76e07
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681292"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Belgeyi anlama ile form işleme modelleri arasındaki farklar 

Microsoft SharePoint Syntex içeriğinin anlaşılması, SharePoint kitaplıklarına yüklenen belgeleri tanımlamanıza, sınıflandırmanıza ve sonra da her dosyadan ilgili bilgileri ayıklamanıza olanak sağlar. Örneğin, dosyalar SharePoint belge kitaplığına yüklendiğinden, Satın Alma Siparişleri olarak tanımlanan tüm dosyalar bu şekilde sınıflandırılır  ve sonra özel bir belge kitaplığı görünümünde görüntülenir. Buna ek olarak, her dosyadan belirli bilgileri (örneğin, *POSTA* Numarası ve *Toplam*) çekebilir ve belge kitaplığı görünümde bir sütun olarak görüntüebilirsiniz. 

İçeriğin anlaşılması, gereken *bilgileri* tanımlamak ve ayıklamak için modeller oluşturmanıza olanak sağlar. Modeller arama, iş süreçleri, uyumluluk ve diğer birçok konu ile ilgili iş sorunlarını çözmenize yardımcı olacak değerlidir.

Kullanabileceğiniz iki özel model türü vardır:

- [Belge anlama modelleri](document-understanding-overview.md)
- [Form işleme modelleri](form-processing-overview.md)

Her iki model de genel olarak aynı amaç için kullanılır, ancak aşağıda listelenen önemli farklılıklar hangisini kullanabileceğiniz etkileyebilir.

> [!NOTE]
> Aşağıdaki [benimsemeyi SharePoint Syntex: Form işleme ve senaryo](./adoption-getstarted.md) örneklerini belge anlama hakkında daha fazla bilgi edinmek için kılavuza bakın.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Yapılandırılmış ve yapılandırılmamış ve yarı yapılandırılmış içerikler karşılaştırması

Harfler veya sözleşmeler gibi yapılandırılmamış belgelerden verileri tanımlamak ve ayıklamak için, ayıklamak istediğiniz metin varlıklarının tümceler veya belgenin belirli bölgeleri olduğu belge anlama modellerini kullanın. Örneğin yapılandırılmamış bir belge, farklı şekillerde yazılacak bir sözleşme yenileme mektubu olabilir. Bununla birlikte, bilgiler her sözleşme yenileme belgesinin gövdesinde tutarlı bir şekilde yer alır, örneğin Hizmet *başlangıç* tarihi ve ardından gerçek bir tarih metin dizesidir.

Form işleme modellerini kullanarak dosyalar tanımlayabilir ve formlar veya faturalar gibi yapılandırılmış ya da yarı yapılandırılmış belgelerden veri ayıklarsiniz. Form işleme modelleri, örnek belgelerden form düzeninizi anlamak ve benzer konumlardan ayıklamak istediğiniz verileri nasıl bu şekilde alamanız gerekmektedir? Formlar genellikle varlıkların aynı konumda bulunduğu daha yapılandırılmış bir düzendir (örneğin, vergi formundaki bir sosyal güvenlik numarası).

> [!NOTE]
> Belge anlama modeli oluşturmak veya bunu bir belge kitaplığına uygulamak için içerik merkezi sitesine SharePoint gerekir. 

## <a name="where-models-are-created"></a>Modeller nerede oluşturulur?

Belge anlama modelleri, içerik merkezi sitesinde SharePoint yönetilir. 

> [!NOTE]
> Girdi belgeleri hakkında daha fazla bilgi için bkz [. Form işleme modeli gereksinimleri ve sınırlamaları](/ai-builder/form-processing-model-requirements). 

Form işleme modelleri Power Apps [AI Builder'da](/ai-builder/overview) oluşturulur, ancak oluşturma işlemi doğrudan SharePoint kitaplığından başlatılır. Kullanıcının, onun için bir form işleme modeli oluşturamadan önce, belge kitaplığında form işleme modeli oluşturmanın etkinleştirilmiş olması gerekir. Yöneticiler, yönetici ayarlarının anlaşılması için içerikte form işleme modeli oluşturulmasını etkinleştirebilirsiniz. Form işleme modelleri, Power Automate dosyaları belge kitaplığına yüklerken bu dosyaları işlemeye uygun akışlar kullanır.

Belge anlama modeli ekleyebilirsiniz, SharePoint Türleri galerisine kaydedilen yeni bir [](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) SharePoint içerik türü oluşturabilirsiniz. Ayrıca, gerekirse modelinizi tanımlamak için var olan içerik türlerini de kullanabilirsiniz.

bir içerik türü oluşturulduktan ve bir modelle ilişkilendiril oluşturulduktan sonra, Site İçerik Türü özellik panelinden bu **modele** de başvurabilirsiniz.

![Site İçerik Türü panelinin Belge anlama modelini vurgulu gösteren ekran görüntüsü.](../media/content-understanding/site-content-type-panel.png)

Form işleme modelleri aynı zamanda yeni [SharePoint içerik türleri de](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) oluşturabilir ve bunlar SharePoint galerisinde depolanır.

## <a name="where-they-can-be-applied"></a>Uygulan uygulan uygulanmayacakları yer

Erişiminiz olan belge kitaplıklarını SharePoint anlama modelleri uygulayabilirsiniz. bir belge anlama modeli oluşturmak ve bunu farklı belge kitaplıklarına uygulamak için içerik merkezini kullanın. İçerik merkezi, modellerin nasıl kullanıldıklarını ve nereye uygulandığını anlamada size daha merkezi bir denetim sağlar. Bu bilgilerin bir içerik merkezinde de toplandır olması gerektiğini unutmayın.

Form işleme modelleri şu anda yalnızca oluşturduğunuz SharePoint kitaplığına uygulanabilir. Bu, siteye erişimi olan lisanslı kullanıcıların bir form işleme modeli oluşturmalarına olanak sağlar. Bir yöneticinin, lisanslı kullanıcıların da SharePoint için bir kitaplıkta form işlemeyi etkinleştirmesi gerektiğini unutmayın.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Formları işleme ve belgeyi anlama karşılaştırması

Form işlemenin ne zaman ve ne zaman belge kullanımı olduğunu anlamak için aşağıdaki tabloyu kullanın.

| Özellik | Form işleme | Belgeyi anlama |
| ------- | ------- | ------- |
| Model türü - her biri ne zaman kullanın | Düzen ve biçimlendirmenin benzer olduğu faturalar veya satın alma siparişleri gibi form içeriği için PDF'ler gibi yarı yapılandırılmış dosya biçimleri için kullanılır.  | Yarı yapılandırılmış dosya biçimleri için kullanılır; örneğin, Office farklılıklar olduğu ama yine de ayıklanan benzer bilgilerin bulunduğu belgeleri kullanır. |
| Model oluşturma | AI oluşturucusnda oluşturulmuş ve belge kitaplığından sorunsuz SharePoint modeli.| yeni bir SharePoint, içerik merkezinde oluşturulmuş model. |
| Sınıflandırma türü| Settable classifier is used to give clues the system on what data extract.| Ayıklamak istediğiniz veriler üzerinde belge konumu atamak için makine öğretimini kullanarak isteğe bağlı ayıklayıcılarla eğitilebilir sınıflandırıcı.|
| Konumlar | Tek bir belge kitaplığı için eğitim.| Birden çok kitaplı kitaplara uygulanabilir.|
| Desteklenen dosya türleri| PDF, JPG, PNG biçimi, toplam 50 MB ve 500 sayfayla eğitin.| Negatif örnekler de dahil olmak üzere 5-10 PDF, Office veya e-posta dosyasıyla eğitin.<br>Office dosyası 64k karakterde kesilir. OCR taranan dosyalar 20 sayfayla sınırlıdır.|
| Yönetilen meta verilerle tümleştirin | Hayır | Evet, yapılandırılmış yönetilen meta veri alanına başvuran eğitim varlık ayıklayı tarafından.|
| Uyumluluk özellikleri etkin Microsoft Bilgi Koruması tümleştirmesi | Yayımlanmış Bekletme etiketlerini ayarlayın.<br>Duyarlılık etiketlerini ayarlayın. | Yayımlanmış Bekletme etiketlerini ayarlayın.<br>Yayımlanmış Duyarlılık etiketlerini ayarlayın. |
| Desteklenen bölgeler| Form işleme, Power Platform'a dayandır. Power Platform ve AI Builder'ın genel kullanılabilirliği hakkında bilgi için bkz. [Power Platform kullanılabilirliği](https://dynamics.microsoft.com/geographic-availability/). | Tüm bölgelerde kullanılabilir.|
| İşlem maliyeti | AI Builder kredilerini kullanır.<br>Krediler 1M toplu olarak satın alınabilir.<br>300'den fazla lisans satın SharePoint Syntex 1M kredisi dahil edilir.<br>1M kredisi 2.000 dosya sayfası işlemeye olanak sağlayacaktır.<br>| Yok |
| Kapasite | Varsayılan Power Platform ortamını kullanır (Veri Ters veritabanı desteklenen özel ortamlar). | Kapasite kısıtlamaları yoktur.|
| Desteklenen diller| English <br>2022'de gelecek: Latin alfabesi dilleri | Modeller tüm Latin alfabelerinde çalışır. İngilizce'nin yanı sıra: Almanca, İsveççe, Fransızca, İspanyolca, İtalyanca ve Portekizce.|

## <a name="see-also"></a>Ayrıca Bkz

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Belgeyi anlamaya genel bakış](document-understanding-overview.md)

[Form işlemeye genel bakış](form-processing-overview.md)

[Giriş SharePoint Syntex](index.md)