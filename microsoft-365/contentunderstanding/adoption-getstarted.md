---
title: Microsoft SharePoint Syntex'un benimsenmesini Kullanmaya başlayın
description: İş süreçlerinizi kolaylaştırmanıza yardımcı olmak için kuruluşunuzda SharePoint Syntex kullanmayı ve uygulamayı öğrenin.
ms.author: chucked
author: chuckedmonson
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
ms.openlocfilehash: 9b11c5077551aad666d565b0f3c077b3e43dc78e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937839"
---
# <a name="get-started-driving-adoption-of-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'un benimsenmesini Kullanmaya başlayın

SharePoint Syntex'da bulunan akıllı içerik hizmetlerini üç bölüme sahip olarak düşünün:

- **İçerik anlama:** Bilgi bulma ve yeniden kullanma için meta verileri otomatik olarak uygulamak üzere içerikten bilgileri sınıflandırmak ve ayıklamak için kodsuz yapay zeka modelleri oluşturun. [İçerik anlama](document-understanding-overview.md) hakkında daha fazla bilgi edinin.
- **İçerik işleme:** İçeriği yakalama, alma ve kategorilere ayırma işlemlerini otomatikleştirin ve Power Automate kullanarak içerik odaklı işlemleri kolaylaştırın. [İçerik işleme](form-processing-overview.md) hakkında daha fazla bilgi edinin.
- **İçerik uyumluluğu:** Microsoft Purview Information Protection tümleştirmesiyle güvenliği ve idareyi geliştirmek için içeriği denetleme ve yönetme.

Yeni yapay zeka hizmetleri ve özellikleriyle, SharePoint Syntex kullanarak içerik anlama ve sınıflandırma uygulamalarını doğrudan içerik yönetimi akışına oluşturabilirsiniz. İçeriğinizi anlamanın iki farklı yolu vardır. Kullandığınız model türü dosya biçimini ve kullanım örneğini temel alır.

| Form işleme | Belge anlama |
|:-------|:-------|
| Belge kitaplığından oluşturulur. | SharePoint Syntex parçası olan içerik merkezinde oluşturulur. |
| Yapay zeka oluşturucusunda oluşturulan model. | Yerel arabirimde oluşturulan model. |
| Yarı yapılandırılmış dosya biçimleri için kullanılır. | Yapılandırılmamış dosya biçimleri için kullanılır. |
| Ayarlanabilir sınıflandırıcı. | İsteğe bağlı ayıklayıcılarla eğitilebilir sınıflandırıcı. |
| Tek bir kitaplıkla sınırlıdır. | Birden çok kitaplık için uygulanabilir. |
| PDF, JPG, PNG biçiminde eğitin, toplam 50 MB/500 pp. | Negatif örnekler de dahil olmak üzere 5-10 PDF, Office veya e-posta dosyaları üzerinde eğitin. |

Özelliklerin daha eksiksiz bir karşılaştırması için bkz. [Belge anlama ve form işleme modelleri arasındaki fark](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>İyileştirme için pilot iş senaryolarını belirleme

Kuruluşunuzda SharePoint Syntex kullanmaya hazırlanmak için öncelikle yararlı olacağı senaryoları anlamanız gerekir. "Neden", hangi modelin gerekli olacağını ve kuruluşunuzun modelin uygulanacağı yere göre nasıl yapılandırılacağını belirlemeye yardımcı olur. Belge anlamanın kuruluşunuza yardımcı olabileceği birkaç senaryo aşağıdadır:

- **İçerik işleme:** Sözleşmeleri, iş deyimlerini ve form benzeri diğer belgeleri işleyin. Formları alın, alanları anlamak ve eşlemek için modeli eğitin ve ardından verileri otomatik olarak toplamak için formlarınızı çalıştırın. Daha fazla bilgi için bkz. [Form işlemeye genel bakış](form-processing-overview.md).
- **Fatura analizi:** Faturalarınızdan ilgili ayrıntıları çekin ve ilkeye uygun olduklarından veya uygun şekilde işlendiklerinden emin olun.

SharePoint Syntex kuruluşunuza nasıl yardımcı olabileceğini düşünün:

- İş süreçlerini otomatikleştirme
- Arama doğruluğunu geliştirme
- Uyumluluk riskini yönetme

Dikkate almanız gereken iş senaryolarını düşünürken kendinize aşağıdaki soruları sorun:

- Gerçek bir sorunu çözer mi?
- Yaygın olarak kullanılacak mı yoksa geniş bir etkisi olacak mı?
- Elde edilebilir mi?
- Başarıyı ölçebilir misiniz?

Etki ve uygulama kolaylığına göre senaryoların önceliklerini belirleyin. İlk odak alanınızı kolayca uygulanabilecek daha yüksek etki senaryoları haline getirin. Uygulanması zor olan düşük etki senaryolarının önceliklerini kaldırın.

Kuruluşunuzda SharePoint Syntex nasıl kullanabileceğiniz hakkında fikir almak için [örnek senaryoları ve kullanım örneklerini](adoption-scenarios.md) kullanın.

## <a name="identify-roles--responsibilities"></a>Rolleri & sorumlulukları belirleme

Kuruluşunuzda modelleri kimin oluşturacağını ve yöneteceğini belirleyin. Aşağıdaki roller söz konusu olabilir.

| SharePoint/Bilgi yöneticisi | Power Platform yöneticisi | Bilgi yöneticisi | Model sahibi |
|:-------|:-------|:-------|:-------|
| AAD rolü| AAD rolü | AAD rolü | Şampiyonlar |
| Form işlemeyi yapılandırma | Form işleme için Dataverse ortamını yapılandırma | Kullanım örneklerini toplama | İş kullanım örneklerini toplama |
| İçerik merkezlerini ve izinleri yönetme| AIB kredilerini satın alma ve ayırma | En iyi uygulamaları oluşturma ve model analizini gözden geçirme | Model oluşturma ve uygulama |

Bilgi yöneticisi, İş Süreci Sahibi ve İçerik modeli sahibi, kuruluşta örnek modeller ve şampiyon benimsemesi oluşturur.
İlgili olabilecek diğer kişiler: Uyumluluk yöneticisi, Taksonomi yöneticileri.

Modelleri nerede oluşturup uygulayacak? İyileştirilebilen mevcut süreçler veya depolar var mı?

- Form işleme: Hangi sitelerin Form işleme eylemini alacağını belirleyin.
- Belge anlama: Farklı iş alanları için birden çok içerik merkezi oluşturabilirsiniz.

## <a name="strategic-positioning"></a>Stratejik konumlandırma

Proje katılımcılarıyla birlikte çalışarak SharePoint Syntex kullanma stratejisine uygun olduklarından emin olun. Bu konumlandırmaya yardımcı olmak için aşağıdaki kaynakları araştırın ve sağlayın:

- İş sonuçları:
  - Olası mali sonuçlar
  - Olası çeviklik sonuçları
  - İş sonucu şablonu
- Paydaşlar/Exec sponsoru satın alma/hizalama
  - İş olayı desteleri
  - Finansal modeller
  - Şirket hazırlığı - kültür

## <a name="identify-stakeholders"></a>Paydaşları belirleme

Projeniz için paydaşları belirleyin.

|Rol |Sorumluluk |Bölüm |
|:-------|:-------|:--------|
| Yönetici sponsorları   | Üst düzey vizyon ve değerleri şirkete iletme   |  Yönetici liderliği   |
| müşteri adaylarını Project | Başlatma yürütme ve dağıtım işleminin tamamını denetleme | Project yönetimi |
| Bilgi yöneticileri| İçerik merkezleri oluşturma ve yönetme | BT veya diğer departman|
| İçerik yöneticileri ve model sahipleri| Kullanım örneklerini toplama ve model oluşturma ve uygulama | Herhangi bir departman|
| Şampiyonlar | İtiraz işlemeyi yaygınlaştırmaya ve yönetmeye yardımcı olun | Herhangi bir departman (personel) |
| Kiracı yöneticisi | Kiracı düzeyi ayarlarını yapılandırma | BT departmanı|
| Power Platform yöneticisi| Dataverse ortamını yapılandırma | BT departmanı|

> [!NOTE]
> Dağıtımınız boyunca bu rollerin her birinin yerine getirilmesini önersek de, tanımladığınız çözümü kullanmaya başlamak için tümünün gerekli olmadığını fark edebilirsiniz.

## <a name="readiness-checklist"></a>Hazırlık denetim listesi

SharePoint Syntex uygulamaya hazırlanmak için şunları yapmanız gerekir:

![content understanding için hazır olma.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Bitiş durumunu planlama
    - Belge anlama modelleri son değil, araçlardır.
    - Ayıklanan meta verilerin değerinden şu şekilde yararlanmayı planlayın:
      - Arama
      - Biçimlendirmeyi filtreleme ve görüntüleme
      - Uyumluluk
      - Otomasyon
2. Tanımlamak
    - Mevcut bilgi mimarisini ve içerik yönetimi özellik kullanımını anlama.
    - Mevcut içerik türleri modeller için iyi adaylar mıdır?
    - Meta verilerle hangi mevcut işlemler geliştirilebilir?
3. Design
    - Bilgi mimarisine, yönetilen meta verilere ve içerik türlerine yaklaşımınızı tasarlar.
    - Tanım, oluşturma, yönetim sürecini tasarlar.

## <a name="engage-your-organization"></a>Kuruluşunuzla etkileşime geçme

1. Bahis sahiplerini belirleyin, senaryoları onaylayın ve proje planı geliştirin.
1. Ayarları yapılandırın ve lisansları uygulayın.
1. Farkındalık ve eğitime başlayın – Şampiyonları işe alın.
1. Aşamalı olarak dağıt.  
1. Geri bildirim toplayın ve yineleme yapın.
1. Kullanım gerektiğinde AI Builder kredileri için plan arttıkça.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint Syntex için senaryolar ve kullanım örnekleri](adoption-scenarios.md)

[Microsoft 365 çözümü kullanarak sözleşmeleri yönetme](solution-manage-contracts-in-microsoft-365.md)
