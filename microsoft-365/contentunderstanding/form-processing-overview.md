---
title: Microsoft SharePoint Syntex'da form işlemeye genel bakış
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex'da form işleme modelleri oluşturmak için AI Build'i kullanmayı öğrenin.
ms.openlocfilehash: 7b9ff8b8a1014dfb47aa7061caf31599e497c18a
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463197"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da form işlemeye genel bakış

 ![AI Builder.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex, SharePoint belge kitaplıkları içinde modeller oluşturmak için Microsoft Power Apps [AI Builder](/ai-builder/overview) form işlemeyi kullanır.

Formlar ve faturalar gibi yapılandırılmış veya yarı yapılandırılmış belgelerden anahtar-değer çiftlerini ve tablo verilerini tanımlamak ve ayıklamak için makine öğrenmesi teknolojisini kullanan yapay zeka modelleri oluşturmak için AI Builder form işlemeyi kullanabilirsiniz.

Kuruluşlar genellikle posta, faks ve e-posta gibi çeşitli kaynaklardan büyük miktarlarda fatura alır. Bu belgelerin işlenmesi ve veritabanına el ile girilmesi önemli ölçüde zaman alabilir. Belgelerinizdeki metinleri, anahtar/değer çiftlerini ve tabloları ayıklamak için yapay zeka kullanarak form işleme bu işlemi otomatikleştirir. 

> [!NOTE]
> Form işleme senaryosu örnekleri hakkında daha fazla bilgi için [SharePoint Syntex benimseme: Kullanmaya başlayın kılavuzuna](./adoption-getstarted.md) bakın.

Örneğin, belge kitaplığına yüklenen tüm satınalma siparişi belgelerini tanımlayan bir form işleme modeli oluşturabilirsiniz. Her satın alma siparişinden, *po numarası*, *tarih* veya *toplam maliyet* gibi sizin için önemli olan belirli verileri ayıklayabilir ve görüntüleyebilirsiniz.

![Belge kitaplığı görünümü.](../media/content-understanding/doc-lib-done.png)</br>  

Modelinizi eğitmek ve formunuzdan ayıklanacak bilgileri tanımlamak için örnek dosyaları kullanırsınız. Belgenizin düzeni, modeliniz eğitilerek öğrenilir. Başlamak için yalnızca beş form belgesine ihtiyacınız vardır. AI Builder örnek dosyalarınızı anahtar-değer çiftleri için analiz eder ve algılanmamış olabilecek dosyaları el ile de tanımlayabilirsiniz.  AI builder, modelinizin doğruluğunu örnek dosyalarınızda test etmenizi sağlar.

Modelinizi eğitip yayımladıktan sonra modeliniz [bir Power Automate akışı](/power-automate/getting-started) oluşturur. Akış, bir dosya SharePoint belge kitaplığına yüklendiğinde çalışır ve modelde tanımlanan verileri ayıklar. Ayıklanan veriler, modelinizin belge kitaplığı görünümündeki sütunlarda görüntülenir.

kullanıcıların [içinde form işleme](./set-up-content-understanding.md) modeli oluşturabilmesi için Office 365 yöneticisinin SharePoint belge kitaplığı [için form işlemeyi](create-a-form-processing-model.md) etkinleştirmesi gerekir. Siteleri kurulum sırasında veya kurulumdan sonra yönetim ayarlarınızdan seçebilirsiniz.

## <a name="file-limitations"></a>Dosya sınırlamaları

Form işleme modellerini kullanırken [, dosya kullanımına yönelik gereksinimleri ve sınırlamaları](/ai-builder/form-processing-model-requirements) not aldığınızdan emin olun.

## <a name="supported-languages"></a>Desteklenen diller

Form işleme, belgeleri 73'ten fazla dilde destekler. Dillerin listesi için bkz. [Form işleme dili desteği](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

## <a name="multi-geo-environments"></a>Multi-Geo ortamları

[Microsoft 365 Multi-Geo ortamında SharePoint Syntex](../enterprise/microsoft-365-multi-geo.md) ayarlarken, bunu yalnızca merkezi konumda form işlemeyi kullanacak şekilde yapılandırabilirsiniz. Form işlemeyi bir uydu konumunda kullanmak istiyorsanız Microsoft desteğine başvurun.

## <a name="custom-environments"></a>Özel ortamlar

Power Platform işleme için özel bir ortam (varsayılan ortam yerine) kullanıyorsanız ek kurulum gereksinimleri vardır. Daha fazla bilgi için bkz [. Özel Power Platform ortamları](set-up-content-understanding.md#requirements).


## <a name="see-also"></a>Ayrıca bkz.
  
[Power Automate belgeleri](/power-automate/)

[Form işleme modeli oluştur](create-a-form-processing-model.md)

[Belge anlamaya genel bakış](document-understanding-overview.md)

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)