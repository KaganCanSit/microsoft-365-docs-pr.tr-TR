---
title: 'Microsoft SharePoint Syntex benimseme: Çalışmaya başlama'
description: İş sorunlarınızı çözmenize yardımcı SharePoint Syntex işlerinizi nasıl kullanabileceğinizi ve uygulaya öğrenin.
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 172c0a681bc8e7c7867e4bcba1c75f94cfc12e60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986343"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Microsoft SharePoint Syntex benimseme: Çalışmaya başlama

SharePoint Syntex'da bulunan akıllı içerik hizmetlerinin üç parçası olduğunu düşünebilirsiniz:

- **İçeriğin anlaşılması:** Bilgi bulma ve yeniden kullanma için meta verileri otomatik olarak uygulamak üzere içerikten bilgileri sınıflandırmak ve ayıklamak için kod olmayan AI modelleri oluşturun. İçeriği anlama hakkında daha [fazla bilgi öğrenin](document-understanding-overview.md).
- **İçerik işleme:** İçerik yakalama, içeriği geçirme ve kategorilere ayırma işlemlerini otomatik hale getirmek ve içerik odaklı işlemleri otomatik olarak kullanmak için Power Automate. İçerik işleme hakkında [daha fazla bilgi edinmek için](form-processing-overview.md):
- **İçerik uyumluluğu:** Güvenlik ve yönetimi geliştirmek için, içerik üzerinde denetimler ve denetimler Microsoft Bilgi Koruması.

Yeni AI hizmetleri ve yetenekleri sayesinde, SharePoint Syntex kullanarak içeriği anlama ve sınıflandırma uygulamalarını doğrudan içerik yönetim akışına SharePoint Syntex. İçeriğinizi anlamanın iki farklı yolu vardır. Kullanabileceğiniz model türü dosya biçimine ve kullanım durumuna göredir.

| Form işleme | Belgeyi anlama |
|:-------|:-------|
| Belge kitaplığından oluşturuldu. | İçerik merkezinde oluşturulmuş, içeriğin bir SharePoint Syntex. |
| AI oluşturucusuzla oluşturulan model. | Yerel arabirimde oluşturulan model. |
| Yarı yapılandırılmış dosya biçimleri için kullanılır. | Yapılandırılmamış dosya biçimleri için kullanılır. |
| Settable classifier. | İsteğe bağlı ayıklayıcılarla eğitilebilir sınıflandırıcı. |
| Tek bir kitaplıkla sınırlandırılmıştır. | Birden çok kitaplı kitaplara uygulanabilir. |
| PDF, JPG, PNG biçiminde eğitin, toplam 50 MB/500 pp. | Negatif örnekler de dahil olmak üzere 5-10 PDF, Office veya e-posta dosyasıyla eğitin. |

Yeteneklerin daha eksiksiz bir karşılaştırması için bkz. Belgeyi anlama ve [form işleme modelleri arasındaki fark.](difference-between-document-understanding-and-form-processing-model.md)

## <a name="identify-pilot-business-scenarios-to-optimize"></a>İyileştirilen pilot iş senaryolarını belirleme

E-posta SharePoint Syntex için öncelikle yararlı olacak senaryoları anlamanız gerekir. "Neden", hangi modelin gerekli olacağını ve modelin nereye uygulanacaklarına göre kuruluş şemasını nasıl yapılandıracaklarını belirlemeye yardımcı olur. Belgeyi anlamanın organizasyonunıza yardımcı olduğu birkaç senaryo şöyledir:

- **İçerik işleme:** Sözleşmeleri, iş ifadelerini ve diğer form benzer belgeleri işlenin. Formları eğitin, alanları anlamak ve eşlemek için modeli eğitin ve ardından verileri otomatik olarak toplamak için formlarınızı çalıştırın. Daha fazla bilgi için bkz [. Form işlemeye genel bakış](form-processing-overview.md).
- **Fatura çözümlemesi:** Faturalardan ilgili ayrıntıları alın ve ilkeye uygun olduğundan veya uygun şekilde işleme alındıklarından emin olun.

Organizasyona yardımcı olacak SharePoint Syntex bir düşünebilirsiniz:

- İş işlemlerini otomatikleştirme
- Arama doğruluğunu geliştirme
- Uyumluluk riskini yönetme

Hangi işletme senaryolarını göz önünde bulundurabilirsiniz diye düşünürken, kendinize aşağıdaki soruları sorun:

- Bu gerçek bir sorunu çözdü mü?
- Yaygın olarak kullanılacak mı yoksa çok etkisi olacak mı?
- Elde edilebilir mi?
- Başarıyı ölçebilir misiniz?

Senaryolara, etki ve uygulama kolaylığına göre öncelikleri belirleme. İlk odak alanınızı, kolayca uygulanabiliyor olacak daha yüksek etki senaryoları yapma. Uygulanması zor olan daha düşük etki senaryolarına önceliklerini belirleme.

Örnek [senaryoları ve örnekleri kullanarak, organizasyonda](adoption-scenarios.md) nasıl kullanabileceğiniz hakkında fikir SharePoint Syntex kullanın.

## <a name="identify-roles--responsibilities"></a>Rolleri ve & belirleme

Organizasyonda modelleri kimlerin kuracaklarını ve yöneteceklerini belirleme. Aşağıdaki roller söz konusu olabilir.

| SharePoint/Bilgi yöneticisi | Power Platform yöneticisi | Bilgi yöneticisi | Model sahibi |
|:-------|:-------|:-------|:-------|
| AAD rolü| AAD rolü | AAD rolü | Şampiyon |
| Form işlemeyi yapılandırma | Form işleme için Veri Ters ortamını yapılandırma | Kullanım durumlarını toplama | İş kullanımı durumlarını toplama |
| İçerik merkezlerini ve izinleri yönetme| AIB kredisi satın alma ve tahsisi | En iyi uygulamaları kurma ve model analizini gözden geçirme | Model oluşturma ve uygulama |

Bilgi yöneticisi, İş Süreci Sahibi ve İçerik modeli sahibi kuruluşta örnek modeller ve şampiyon benimsemesi oluşturabilir.
Dahil olacak diğer kullanıcılar: Uyumluluk yöneticisi, Taksonomi yöneticileri.

Modelleri nerede oluşturmalı ve uygulamalı? Geliştirnen mevcut süreçler veya depolar var mı?

- Form işleme: Hangi sitelerin Form işleme eylemine almayacaklarını seçin.
- Belgeyi anlama: Farklı iş alanları için birden çok içerik merkezi oluşturabilirsiniz.

## <a name="strategic-positioning"></a>Stratejik konumlandırma

Proje katılımcıları ile birlikte çalışarak proje katılımcılarının proje katılımcılarını kullanma stratejisini SharePoint Syntex. Bu konumlandırmaya yardımcı olmak için araştırma yapın ve aşağıdaki kaynakları sağlar:

- İş sonuçları:
  - Olası mali sonuçlar
  - Olası çeviklik sonuçları
  - İş sonuç şablonu
- Paydaşlar/Exec sponsoru satın alma/hizalama
  - İş desteleri
  - Finansal modeller
  - Şirket hazırlığı - kültür

## <a name="identify-stakeholders"></a>Paydaşları tanımlama

Projenize paydaşları tanıyın.

|Rol |Sorumluluklar |Bölüm |
|:-------|:-------|:--------|
| Yönetici sponsorları   | Şirketle üst düzey görüş ve değerleri iletişim kurma   |  Yönetim liderlik   |
| Project müşteri adayları | Tüm başlatma yürütme ve yürütme sürecini denetleme | Project yönetimi |
| Bilgi yöneticileri| İçerik merkezlerini oluşturma ve yönetme | IT veya başka bir bölüm|
| İçerik yöneticileri ve model sahipleri| Kullanım durumlarını toplama ve modelleri oluşturma ve uygulama | Herhangi bir bölüm|
| Şampiyon | Itirazları ele alıma ve yönetmeye yardımcı olur | Herhangi bir bölüm (personel) |
| Kiracı yöneticisi | Kiracı düzeyinde ayarları yapılandırma | IT bölümü|
| Power Platform yöneticisi| Veri Ters ortamını yapılandırma | IT bölümü|

> [!NOTE]
> Her bir rolün tüm bu rollerin rulon boyunca karşıldır getirilmesini önerse de, çözümün tanımını almaya başlamanız için bunların hepsini gerekli olmadığını bulabilirsiniz.

## <a name="readiness-checklist"></a>Hazırlık denetim listesi

Bu uygulamanın uygulanmasına SharePoint Syntex için şunları gerekir:

![İçerik Anlama hazırlığı.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Bitiş durumunu planlama
    - Belge anlama modelleri son değildir, anlamanın anlamıdır.
    - Ayıklanan meta verilerin değerini şu şekilde kullanın:
      - Arama
      - Filtreleme ve biçimlendirmeyi görüntüleme
      - Uyumluluk
      - Otomasyon
2. Tanımlama
    - Var olan bilgi mimarisini ve içerik yönetimi özellik kullanımını anlıyoruz.
    - Mevcut içerik türleri modellere uygun aday var mı?
    - Meta verilerle hangi mevcut süreçler geliştirnsin?
3. Design
    - Bilgi mimarisi yaklaşımınızı, yönetilen meta verileri ve içerik türlerini tasarlar.
    - Tanımlama, oluşturma ve yönetim için süreci tasarlar.

## <a name="engage-your-organization"></a>Organizasyonla etkileşim kurma

1. Tutucuları tanımlama, senaryoları onaylama ve proje planı geliştirme.
1. Ayarları yapılandır ve lisansları uygula.
1. Farkındalık ve eğitime başla – Şampiyonları işe alın.
1. Evreler olarak sahneyi takip et.  
1. Geri bildirim toplama ve iterat.
1. Kullanım arttıkça tüm AI Builder kredileri için gereken plan büyür.

## <a name="see-also"></a>Ayrıca bkz.

[Durumlar için senaryolar ve kullanım SharePoint Syntex](adoption-scenarios.md)

[Yeni bir çözüm kullanarak Microsoft 365 yönetin](solution-manage-contracts-in-microsoft-365.md)
