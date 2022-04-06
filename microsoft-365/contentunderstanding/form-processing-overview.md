---
title: Microsoft SharePoint Syntex'ta form işlemeye genel bakış
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
description: Microsoft SharePoint Syntex'da AI Derlemesi kullanarak form işleme modelleri oluşturma hakkında SharePoint Syntex.
ms.openlocfilehash: a3a3d1fa0e160b96d487a5eeb03c69f9e4fe7fb3
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507399"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta form işlemeye genel bakış

 ![AI Oluşturucusu.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex, belge kitaplıkları içinde Power Apps SharePoint oluşturmak için Microsoft [Power Apps AI Builder](/ai-builder/overview) form işlemeyi kullanır.

AI Builder form işlemeyi kullanarak, form ve faturalar gibi yapılandırılmış veya yarı yapılandırılmış belgelerden önemli değer çiftlerini ve tablo verilerini tanımlamak ve ayıklamak için makine öğrenme teknolojisini kullanan AI modelleri oluşturabilirsiniz.

Kuruluşlar genellikle posta, faks, e-posta gibi çeşitli kaynaklardan büyük miktarlarda fatura alır. Bu belgelerin işlemesi ve bunları veritabanına el ile girmek oldukça fazla zaman alsa da bu kadar zaman alır. Belgelerinizin metinlerini, anahtar/değer çiftlerini ve tabloları ayıklamak için AI kullanarak form işleme bu işlemi otomatik halelar. 

> [!NOTE]
> Form işleme [SharePoint Syntex için Kullanmaya başlayın benimseme](./adoption-getstarted.md) kılavuzuna bakın.

Örneğin, belge kitaplığına yüklenen tüm satın alma siparişi belgelerini tanımlayan bir form işleme modeli oluşturabilirsiniz. Her satın alma siparişinden sizin için önemli olan *SATıN* ALMA Siparişi Numarası, Tarih veya Toplam Maliyet *gibi belirli verileri ayıklar* ve *görüntüebilirsiniz*.

![Belge kitaplığı görünümü.](../media/content-understanding/doc-lib-done.png)</br>  

Modelinizi eğitmek ve formdan ayıklanan bilgileri tanımlamak için örnek dosyaları kullanırız. Belgenizin düzeni, modelinizi eğitimle öğrenerek öğrenebilirsiniz. Yalnızca beş form belgesine ihtiyacınız var. AI Oluşturucusu örnek dosyalarınızı anahtar-değer çiftleri için çözümler ve algılanan olmayanları el ile de tanımlayabilirsiniz.  AI oluşturucusu, örnek dosyalarınız üzerinde modelinizin doğruluğunu test etmek için olanak sağlar.

Modelinizi eğitip yayımladikten sonra, modeliniz bir [Power Automate oluşturur](/power-automate/getting-started). Akış, bir dosya belge kitaplığına SharePoint ve modelde tanımlanan verileri ayıklar. Ayıklanan veriler modelinizin belge kitaplığı görünümündeki sütunlarda görüntülenir.

Bir Office 365, kullanıcıların belge kitaplığında [form](./set-up-content-understanding.md) işleme modelini oluştur SharePoint için bu kitaplıkta [form işlemeyi etkinleştirmesi](create-a-form-processing-model.md) gerekir. Siteleri kurulum sırasında veya kurulumdan sonra yönetim ayarlarınıza seçebilirsiniz.

### <a name="file-limitations"></a>Dosya sınırlamaları

Form işleme modelleri kullanırken, dosya kullanımıyla ilgili gereksinimleri ve [sınırlamaları not edin](/ai-builder/form-processing-model-requirements).

### <a name="supported-languages"></a>Desteklenen diller

Form işleme, belgeleri 73'den fazla dilde destekler. Dil listesi için bkz. [Form işleme dili desteği](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

### <a name="multi-geo-environments"></a>Multi-Geo ortamları

Çok Coğrafi SharePoint Syntex bir [Microsoft 365](../enterprise/microsoft-365-multi-geo.md) ayarları sırasında, bunu yalnızca merkezi konumda form işlemeyi kullanmak üzere yapılandırabilirsiniz. Uydu konumda form işlemeyi kullanmak için Microsoft destek ile iletişime geçin.






## <a name="see-also"></a>Ayrıca Bkz
  
[Power Automate belgeleri](/power-automate/)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)

[Belgeyi anlamaya genel bakış](document-understanding-overview.md)

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)