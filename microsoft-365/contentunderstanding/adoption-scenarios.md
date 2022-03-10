---
title: Microsoft SharePoint Syntex için senaryolar ve kullanım SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
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
description: Bir veya daha fazla SharePoint Syntex ilgili iş senaryolarını bulun.
ms.openlocfilehash: fe4f72dc56014e5bc990e5ea39bd019785bd8572
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419093"
---
# <a name="scenarios-and-use-cases-for-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex için senaryolar ve kullanım SharePoint Syntex

Aşağıdaki örnek senaryoları kullanarak, organizasyonda işlerinizi nasıl kullanabileceğiniz hakkında SharePoint Syntex fikirler istensin.

- [Senaryo: Form işleme ile faturalardan verileri izleme](adoption-scenarios.md#scenario-track-data-from-invoices-with-form-processing)
- [Senaryo: Belgeyi anlama ile sözleşmelerden bilgileri izleme](adoption-scenarios.md#scenario-track-information-from-contracts-with-document-understanding)
- [Senaryo: Temel alan kayıt yönetimi, belge yönetimi ve uyumluluk süreçleriyle ilgili risklerden SharePoint Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex)
- [Senaryo: Daha önce erişilemeyen belgelerden bilgi yakalama](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Senaryo: Öngörüler ve çözümlemeler sağlamak için veri işlemeyi geliştirme](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Senaryo: Sipariş işlemeyi otomatikleştirme](adoption-scenarios.md#scenario-automate-order-processing)
- [Senaryo: Visa yenileme işlemini basitleştirme](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-data-from-invoices-with-form-processing"></a>Senaryo: Form işleme ile faturalardan verileri izleme

Örneğin, faturaları izlemek ve izlemek için faturalara SharePoint Syntex özellikleri Power Automate bir süreç kurebilirsiniz.

1. Fatura belgelerini depolamak için bir kitaplık ayarlayın.
1. Modeli, belgelerde yer alan alanları tanıyacak şekilde eğitin.
1. Listede izlemek istediğiniz alanları ayıkla.
1. Belirli olayları size bildirmek için bir akış ayarlama; örneğin:
    - Yeni bir fatura eklenir.
    - Faturanın son tarihi geçmiş.
    - Fatura, otomatik onay tutarınıza göre daha büyük bir tutardır.

![Faturalara faturalar, faturalar SharePoint Syntex ve fatura Power Automate.](../media/content-understanding/process-invoices-flow.png)

Bu senaryoyu otomatik hale zaman şu şekilde oluşturabilirsiniz:

- Faturalardan verileri elle yapmak yerine otomatik olarak ayıklaarak zaman ve paradan tasarruf edebilirsiniz.
- Olası hataları azaltmak ve iş akışlarını kullanarak faturaları kontrol etmek ve sorunları size bildirmek için daha iyi uyumluluk sağlayın.

## <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Senaryo: Belgeyi anlama ile sözleşmelerden bilgileri izleme

Başka bir örnek olarak, şirketinizin diğer şirketlerle veya bireylerle olan sözleşmelerini belirlemek için bir süreç de hazırlanmıştır. Müşteri adı, ücretler, tarihler veya diğer önemli bilgiler gibi söz konusu sözleşmelerden önemli bilgileri ayıklayacak bir model ayarlayın ve bilgileri hızla görüntü spor alanı olarak kitaplıklara ekleyin. İşle ilgili yasal düzenlemelere uygun uyumluluk için sözleşmelerin belirli bir süre öncesinde silinemeden önce silinemeden emin olmak için belge kitaplığına bir bekletme etiketi ekleyin.

1. İçerik merkezinden başlar ve sözleşmeler için yeni bir belge anlama modeli oluşturun.
1. Upload ve negatif örnekler için örnek belgeleri gözden geçirmek, sonra sözleşme belgelerini tanımlamak ve sonuçları gözden geçirmek için eğitimi çalıştırın.
1. Ayıklayı, sözleşmelerde müşteri adı, ücret ve tarih gibi alanları tanımlaması için eğitin ve sonra ayıklayı test etmek için.
1. Model tamamlandıktan sonra, modeli sözleşmeler yükley yeri olan kitaplı kitaplıya uygulayabilirsiniz.
1. Sözleşmelerin gereken süre boyunca kitaplıkta tutulması için tarih alanına bir bekletme etiketi uygulayabilirsiniz.

![Sözleşme ve bekletme etiketleriyle SharePoint Syntex ve takip edin.](../media/content-understanding/process-contracts-flow.png)

Bu senaryoyu otomatik hale zaman şu şekilde oluşturabilirsiniz:

- Sözleşmelerde el ile yapmak yerine verileri otomatik olarak ayıklaarak zaman ve paradan tasarruf edebilirsiniz.
- Sözleşmelerin uygun şekilde korun olduğundan emin olmak için bekletme etiketlerini kullanarak daha iyi uyumluluk sağlayın.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex"></a>Senaryo: Temel alan kayıt yönetimi, belge yönetimi ve uyumluluk süreçleriyle ilgili risklerden SharePoint Syntex

Riskleri azaltma, çoğu şirket için ortak bir hedeftir. Size gerekenler:

- Kiracınız genelinde bilgi idaresi sağlamanın/zorunlu kılınmanın daha iyi bir yolu.
- Projelerde belgelerin, e-postaların ve diğer iletişim formlarının sınıflandırması için sistemi geliştirmek için "kayıtlar" olarak düşünülmelidir.
- Şirket ilkelerine uyumluluğu sağlamak için makbuzları, sözleşmeleri ve diğer faturaları denetleme.
- Projelerin uyumluluk için gereken tüm belgelere sahip olduğundan emin olmak için.

Daha iyi yönetim gereken belgeleri ve formları SharePoint Syntex şekilde sınıflandırmak, denetlemek ve bayrakla bayrakla sınıflandırmak için bu belgelere uyumluluk için bazı süreçler ayarlayın. Son kullanıcılardan el ile etiketlemek için SharePoint Syntex ve yönetim kurallarını ve arşivlemeyi el ile uygulamak için uyumluluk ekibine güvenmek yerine, içeriği otomatik olarak sınıflandırmak için E-postalara güvenebilirsiniz. Ayrıca, basitleştirilmiş bir arama deneyimini etkinleştirebilirsiniz, veri hacimlerini yönetebilir, kayıt yönetimi ve bekletme ilkeleri uygulayabilir, uyumluluktan emin olabilir ve en iyi arşivleme ve temizleme uygulamalarını uygulayabilirsiniz.

Bu senaryoyu otomatik hale geldiğinde şunların güvenli olduğunu hissedin:

- Uyumluluktan yarar vardır ve risk azaltıldı.
- Taksonomi ve kayıt yönetimi tutarlı ve doğru bir şekilde uygulanır.
- İçerik hacimleri denetlenr.
- Çalışanlar doğru bağlamda doğru bilgileri kolayca keşfedebilir.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Senaryo: Daha önce erişilemeyen belgelerden bilgi yakalama

Çoğu kuruluşun, yasal belgeler, ilkeler, sözleşmeler, İk belgeleri ve yönetim yönergeleri için büyük depoları vardır. Projeler, nedenler, temalar, kişiler, coğrafi alanlar gibi değerli bilgileri ayıklamak için bu veri depolarına veri verilerim.

Örneğin bir İk yöneticisinin özgeçmişler, İk ilkeleri ve diğer formlar dahil olmak üzere tüm İk belgelerine hızla erişmesi gerekiyor. Özgeçmişler ve İk ile ilgili diğer belgelerle ilgili gerekli bilgileri belgelere el ile atmadan tanımlamak da istiyor. Kullanıcılar çeşitli sitelere yayılmış binlerce özgeçmişe, İk ilkelerine ve diğer belgelere el ile bakmak zorunda kalmadan ihtiyaçları olan bilgileri hızla bulmalarını sağlayan bir çözüm arıyor.

Bu senaryoyu otomatik hale zaman şu şekilde oluşturabilirsiniz:

- Dijital içerikten bilginin kilidini açın.
- İk ilkelerini, özgeçmişleri, satış belgelerini, teknik şemaları, hesap planlarını sınıflandırarak bilgileri ayıklar.
- Bulmak istediğiniz doğru bilgileri veya belgeyi hızla bulun.
- En son bilgilere anında erişin.
- Arama sürelerini azaltır.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Senaryo: Öngörüler ve çözümlemeler sağlamak için veri işlemeyi geliştirme

Örneğin, bir farmasötik şirketi, SharePoint Syntex sahip olduğu soruları yanıtlamak için FDA belgelerinden bilgiler almak için şirket tarafından kullanılabilir. Yanıtların daha kolay erişilebilir olmasını sağlamak, bu yanıtları oluşturmak için gereken zamanı azaltabilir ve liderlik sorularına daha doğru yanıtlar oluşturmak için verilerin kullanılabilirliğini artırabilir.

Örneğin, bir proje yöneticisinin liderlik ekibimin ürünle ilgili sorulara hızlıca yanıtlar sağlaması gerekiyor. Tek bir birleşik panoda sorgularla ilgili bilgileri ve ölçümleri bulmaları gerekir. Ürün etiketlerinden, ürün kitapçıklarından ve diğer malzemelerden ihtiyaçları olan bilgileri ayıklanan ve liderlik ekibine geri bildirim sunarken kullanabileceği birleştirilmiş bir rapor oluşturan bir çözüm arıyor.

Bu senaryoyu otomatik hale zaman şu şekilde oluşturabilirsiniz:

- Yanıtlar üretme süresini azaltır.
- Verilerin kullanılabilirliğini artırma.
- Daha doğru yanıtlar sağlama.

## <a name="scenario-automate-order-processing"></a>Senaryo: Sipariş işlemeyi otomatikleştirme

Müşteri SharePoint Syntex ile, müşteri siparişlerinin el ile işleme süresini azaltabilirsiniz. Örneğin, OCR işlemeyi kullanarak faks, e-posta veya kağıttan SharePoint'ye siparişleri yükleyebilir ve ardından otomatik süreçleri kullanarak gerçekleştirilmiş işlemleri gerçekleştirebilirsiniz.

Örneğin, bir tedarik zinciri yöneticisi el ile veri girişinin neden olduğu hataları azaltmak istiyor. İş sistemlerine giden hataları azaltmak için gelen müşteri siparişlerinin (kağıt, faks veya e-posta) elle gözden geçirmesini ve veri girişini önlemek istiyor. Gelen sipariş bilgilerini doğrulamak, çekirdek verileri ayıklamak ve sipariş karşılamak ve mutabakat için otomatik olarak ERP sistemine itmek için AI ve makine öğrenme tekniklerini uygular bir çözüm istiyor.

Bu senaryoyu otomatik hale garanti etmek için:

- Sipariş ve sevkiyat doğruluğu artar.
- Sipariş veya sevkiyat hatalarına bağlı ücretler veya kalemler azaltıldı.
- Faturalamadaki veya ödemelerdeki gecikmeler azalır.
- Personel maliyetleri azaltıldı.

## <a name="scenario-simplify-visa-renewal-process"></a>Senaryo: Visa yenileme işlemini basitleştirme

SharePoint Syntex bilgileri için anımsatıcıları ve yenilemeleri otomatikleştirmenize yardımcı olabilir. Örneğin İk müdürü, çalışanların visas'larının güncel ve/veya zamanında yenilenmesine gerekmektedir. Bu kişiler, kişilerin Visas'larını güncelleştirmek için basit ve sezgisel bir işlem yapmak istiyor. Sözleşmelerden yenileme tarihlerini ayıklatan ve yenileme tarihleri yaklaştığında çalışanlara otomatik olarak anımsatıcılar gönderen bir çözüme ihtiyaçları vardır.

Bu senaryoyu otomatik hale garanti etmek için:

- Uyumluluk dışı düzeyler azaltıldı.
- Elle anımsatıcıların sayısı azalır.
- Uyumluluk dışılık ile ilgili ince kuralların sayısı azaltıldı.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft SharePoint Syntex benimseme: Çalışmaya başlama](adoption-getstarted.md)