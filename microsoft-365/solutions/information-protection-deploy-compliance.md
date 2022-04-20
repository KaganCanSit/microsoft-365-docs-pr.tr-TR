---
title: İyileştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
description: Kişisel veriler için koruma düzeyinizi geliştirmek için Uyumluluk Puanı ve Uyumluluk Yöneticisi'ni kullanmayı öğrenin.
ms.openlocfilehash: 469584abbf784fe6c556aab14a49a5ed44280a69
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947461"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>İyileştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma

Microsoft Purview Uyumluluk Yöneticisi, Avrupa Birliği [Genel Veri Koruma Yönetmeliği (GDPR)](/compliance/regulatory/gdpr), [California Tüketici Koruma Yasası CCPA)](/compliance/regulatory/ccpa-faq), HIPAA-HITECH (ABD sağlık hizmetleri gizlilik yasası) ve Brezilya Veri Koruma Yasası (LGPD) gibi veri gizliliği düzenlemelerine ilişkin iyileştirmeleri yönetmenize yardımcı olabilir.

Bu makale, veri gizliliği amacıyla bu aracın kullanımı hakkında rehberlik sağlar.

> [!NOTE]
> Uyumluluk Yöneticisi'nden gelen Öneriler, uyumluluk garantisi olarak yorumlanmamalıdır. Yasal ortamınıza göre müşteri denetimlerinin etkinliğini değerlendirmek ve doğrulamak size aittir. Bu hizmetler [, Çevrimiçi Hizmet Koşulları'ndaki](https://go.microsoft.com/fwlink/?linkid=2108910) hüküm ve koşullara tabidir. Ayrıca bkz[. Microsoft 365 güvenlik ve uyumluluk için lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Uyumluluk Yöneticisi ile çalışmaya başlama

#### <a name="what-is-compliance-manager"></a>Uyumluluk Yöneticisi nedir?

[Uyumluluk Yöneticisi](../compliance/compliance-manager.md) , Microsoft bulut hizmetleriyle ilgili mevzuat uyumluluğu etkinliklerini yönetmek için Microsoft Purview uyumluluk portalında bulunan iş akışı tabanlı bir risk değerlendirme aracıdır. Microsoft 365 veya Azure Active Directory (Azure AD) aboneliğinizin bir parçası olarak Uyumluluk Yöneticisi, Microsoft bulut hizmetleri için paylaşılan sorumluluk modeli içinde mevzuat uyumluluğunu yönetmenize yardımcı olur.

**Kullanıma hazır değerlendirmeler**

Uyumluluk Yöneticisi, GDPR ve HIPAA/HITECH gibi veri gizliliğiyle ilgili düzenlemelere uygun [değerlendirmeler oluşturmak](../compliance/compliance-manager-assessments.md) için önceden oluşturulmuş şablonlar sağlar. Şablonlar, düzenlemenin gereksinimlerini karşılamak için iyileştirme eylemleri gerçekleştirmenize yardımcı olacak yerleşik denetim eşlemesine sahiptir. Her değerlendirme, her düzenlemenin hedef hizmete özgü olarak çağırdığı denetimler hakkında bilgi sağlar. Bu denetimler Microsoft'un yönettiği denetimler ve denetimlerle ayrılmıştır.

Önceden oluşturulmuş bir şablon kullanmak, risk değerlendirmelerini hızlı bir şekilde kullanmaya başlamanıza yardımcı olur. Uyumluluk Yöneticisi'ni kullanma konusunda daha becerikli hale geldikçe, kendi denetimlerinizi ve geliştirme eylemlerinizi ekleyerek önceden oluşturulmuş bir şablonu özelleştirebilir veya kuruluşunuzun gereksinimlerine uygun kendi özel değerlendirmelerinizi oluşturabilirsiniz.

Uyumluluk Yöneticisi tarafından sağlanan [değerlendirme şablonlarının tam listesini](../compliance/compliance-manager-templates-list.md) görüntüleyin.

**Gerçek zamanlı uyumluluk puanı**

Uyumluluk Yöneticisi, denetimler içinde önerilen iyileştirme eylemlerini tamamlamadaki ilerlemenizi ölçen bir uyumluluk puanı da sağlar. Bu puanı, ilerleme durumunuzu izlemeye yardımcı olmak ve riskleri azaltma potansiyeline göre eylemleri önceliklendirmek için kullanabilirsiniz.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Uyumluluk Yöneticisi hızlı başlangıç kılavuzunu kullanma

[Uyumluluk Yöneticisi hızlı başlangıç](../compliance/compliance-manager-quickstart.md) kılavuzu, Uyumluluk Yöneticisi ile çalışmanıza yardımcı olmak için derecelendirilen adımlar ve önemli kaynaklara bağlantılar sağlar:

- [İlk ziyaret: Uyumluluk Yöneticisi'ne alışma](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Uyumluluk Yöneticisi panonuzla çalışma
    - Uyumluluk puanınızı anlama
    - İyileştirme eylemleri hakkında Learning
    - Değerlendirmeleri ve şablonları anlama
- [Yükseltme: Uyumluluk Yöneticisi'ne uyumluluk etkinliklerinizi yönetecek şekilde yapılandırma](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - İlk değerlendirmenizi oluşturma ve yönetme
    - Değerlendirmelerinizdeki denetimleri tamamlamak için iyileştirme eylemleri üzerinde uygulama ve test çalışması gerçekleştirme
    - Farklı eylemlerin uyumluluk puanınızı nasıl etkilediğini anlama
- [Ölçeği artırma: Özel gereksinimlerinizi karşılamak için gelişmiş işlevleri kullanın](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Microsoft 365 olmayan ürünleri izlemek için özel değerlendirmelerinizi oluşturma
    - Denetimleri eklemek veya kaldırmak için mevcut şablonları değiştirme
    - İyileştirme eylemlerinin otomatik testini ayarlama

## <a name="how-your-compliance-score-is-calculated"></a>Uyumluluk puanınızı hesaplama

Uyumluluk puanınız, Microsoft ve müşteri tarafından yönetilen denetim uygulamalarının bir birleşimine göre hesaplanır. Ayrıntılı bir açıklama için bkz [. uyumluluk puanı hesaplaması](../compliance/compliance-score-calculation.md) .

Denetimlere zorunlu veya isteğe bağlı olup olmadıklarına ve önleyici, dedektif veya düzeltici olup olmadıklarına bağlı olarak bir puan değeri atanır. Bunlar, bunu diğer denetimlere göre uygulamama riskini toplu olarak temsil eder.

Uyumluluk puanı hesaplama makalesinde gösterildiği gibi, önleyici denetimler dedektif ve düzeltici denetimlerden daha yüksek puan alır ve zorunlu denetimler isteğe bağlı denetimlerden daha yüksek puan alır.

Uyumluluk Puanı yönetici kullanıcı arabirimi bu parametreleri listelemez ve bunlara göre filtreleme olanağı sağlamaz. Ancak, ilişkili şablonu Uyumluluk Yöneticisi'nden indirirseniz, sonuçta elde edilen veri kümesi çoğu düzenleme için bu parametreleri listeler.

Teknik denetimler için, eylem başarıyla uygulanıp test edildikten sonra Uyumluluk Yöneticisi iyileştirme eylem puanını otomatik olarak güncelleştirir. Diğer, teknik olmayan denetim eylemleri, puan puanınıza doğru sayılmadan önce el ile uygulanması gereken operasyonel veya belgelerle&mdash; ilgili olan eylemlerdir&mdash;.

Ayrıca, veri gizliliği düzenleme uyumluluğu&mdash; dışında nedenlerle&mdash; bekletme etiketleri kullanmak gibi başka amaçlarla bazı iyileştirme eylemleri de uyguluyorsunuz. Bu özellik, kasıtlı bir uyumluluk eyleminin parçası değil, başka amaçlarla kullanılıyor olsa bile bu özelliği kullanmak için kredi alırsınız.

Uyumluluk puanınız, geliştirmeyi geniş ölçekte izlemek için göreli bir ölçü olarak kabul edilmelidir. Mükemmel bir skor peşinde koşmamalısın.

## <a name="additional-guidance"></a>Ek yönergeler

Aşağıda, veri gizliliği düzenleme uyumluluğunu sağlamanıza yardımcı olmak için Uyumluluk Yöneticisi'nin kullanılmasına yönelik birkaç önemli ipucu bulabilirsiniz:

- Her veri gizliliği düzenlemesi teknik denetimlerin, belge belirtimlerinin ve operasyonel, süreç ve raporlama gereksinimlerinin bir birleşimine sahiptir. Bunların tümü geliştirme eylemlerinde gösterilir.

- İyileştirme eylemlerinin görünümünü ilgilendiğiniz alana odaklamak için, Uyumluluk Yöneticisi yöneticisinin **Çözümler** sekmesinde eylem türüne göre filtreleyebilirsiniz. [Uyumluluk Yöneticisi pano görünümünüzü filtreleme](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view) hakkında daha fazla bilgi edinin.

- Uyumluluk Yöneticisi'nde tanımlanan iyileştirme eylemlerinin göreli önemi ve önceliği, kuruluşunuzun yönetmesi gerektiğini belirlediğiniz veri gizliliği riskinin yanı sıra daha kapsamlı bir risk incelemesinin parçası olarak değerlendirilmelidir.

- Birden çok mevzuat gereksiniminde iyileştirme eylemi toplaması olsa bile GDPR, LGPD, CCPA ve HIPAA-HITECH için düzenleme değerlendirme şablonları seçilirse, uyumluluk yöneticisinde neredeyse 400 iyileştirme eylemi listelenir. Bu uzun listeyle daha iyi başa çıkmak için iyileştirme eylem filtresini kullanarak sonuç kümesini daha yönetilebilir bir listeye düşürün.

- Kategoriler filtresi, bu genel çözümdeki İzle, Engelle, Koru, Koru ve Araştır makalelerinin hizalandığı mantıksal gruplandırmaya göre iyileştirme eylemlerini filtrelemek için bir araç sağlar.

- İyileştirme eylemlerinde listelenen denetimlerin bazıları belirli bir mevzuat makalesine daha doğrudan bağlı olarak kabul edilebilirken, diğer denetimler bir düzenlemenin ruhuyla daha dolaylı olarak ilişkilendirilebilir ve çoğu zaman yalnızca önerilen etkinlikler veya en iyi uygulamalardır.