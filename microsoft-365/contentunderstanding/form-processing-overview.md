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
description: Microsoft SharePoint Syntex'da form işleme hakkında bilgi SharePoint Syntex.
ms.openlocfilehash: 8079f12c3b05d62de95bcb08808d1acc931a37d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985161"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta form işlemeye genel bakış

 ![AI Oluşturucusu.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex, belge kitaplıkları içinde Power Apps SharePoint oluşturmak için Microsoft [Power Apps AI Builder](/ai-builder/overview) form işlemeyi kullanır.

AI Builder form işlemeyi kullanarak, form ve faturalar gibi yapılandırılmış veya yarı yapılandırılmış belgelerden önemli değer çiftlerini ve tablo verilerini tanımlamak ve ayıklamak için makine öğrenme teknolojisini kullanan AI modelleri oluşturabilirsiniz.

Kuruluşlar genellikle posta, faks, e-posta gibi çeşitli kaynaklardan büyük miktarlarda fatura alır. Bu belgelerin işlemesi ve bunları veritabanına el ile girmek oldukça fazla zaman alsa da bu kadar zaman alır. Belgelerinizin metinlerini, anahtar/değer çiftlerini ve tabloları ayıklamak için AI kullanarak form işleme bu işlemi otomatik halelar. 

> [!NOTE]
> Aşağıdaki [benimsemeyi SharePoint Syntex: Form işleme senaryo](./adoption-getstarted.md) örnekleri hakkında daha fazla bilgi edinmek için çalışmaya başlama kılavuzu.

Örneğin, belge kitaplığına yüklenen tüm satın alma siparişi belgelerini tanımlayan bir form işleme modeli oluşturabilirsiniz. Her satın alma siparişinden sizin için önemli olan *SATıN* ALMA Siparişi Numarası, Tarih veya Toplam Maliyet *gibi belirli verileri ayıklar* ve *görüntüebilirsiniz*.

![Belge kitaplığı görünümü.](../media/content-understanding/doc-lib-done.png)</br>  

Modelinizi eğitmek ve formdan ayıklanan bilgileri tanımlamak için örnek dosyaları kullanırız. Belgenizin düzeni, modelinizi eğitimle öğrenerek öğrenebilirsiniz. Yalnızca beş form belgesine ihtiyacınız var. AI Oluşturucusu örnek dosyalarınızı anahtar-değer çiftleri için çözümler ve algılanmayacakları el ile de tanımlayabilirsiniz.  AI oluşturucusu, örnek dosyalarınız üzerinde modelinizin doğruluğunu test etmek için olanak sağlar.

Modelinizi eğitip yayımladikten sonra, modeliniz [yeni bir](/power-automate/getting-started) Power Automate Flow. Akış, bir dosya belge kitaplığına SharePoint ve modelde tanımlanan verileri ayıklar. Ayıklanan veriler modelinizin belge kitaplığı görünümündeki sütunlarda görüntülenir.

Kullanıcı Office 365, belgenin belge kitaplığında [form](./set-up-content-understanding.md) işlemeyi etkinleştirmesi SharePoint, bu kitaplığın [içinde form işleme modeli](create-a-form-processing-model.md) oluşturabilecektir. Siteleri kurulum sırasında veya kurulumdan sonra yönetim ayarlarınıza seçebilirsiniz.

### <a name="file-limitations"></a>Dosya sınırlamaları

Form işleme modelleri kullanırken, dosya kullanımıyla ilgili gereksinimleri ve [sınırlamaları not edin](/ai-builder/form-processing-model-requirements).

### <a name="multi-geo-environments"></a>Multi-Geo ortamları

Çok Coğrafi SharePoint Syntex bir [Microsoft 365](../enterprise/microsoft-365-multi-geo.md) ayarları sırasında, bunu yalnızca merkezi konumda form işlemeyi kullanmak üzere yapılandırabilirsiniz. Uydu konumda form işlemeyi kullanmak için Microsoft destek ile iletişime geçin.






## <a name="see-also"></a>Ayrıca Bkz
  
[Power Automate belgeleri](/power-automate/)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)

[Belgeyi anlamaya genel bakış](document-understanding-overview.md)

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)