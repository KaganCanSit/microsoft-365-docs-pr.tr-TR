---
title: Geliştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma
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
description: Kişisel veriler için koruma düzeyinizi geliştirmek üzere Uyumluluk Puanı ve Uyumluluk Yöneticisi'ni nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: 5a655d504551e42398cdabbcf7a3f651d788c0ad
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990591"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Geliştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma

Microsoft Uyumluluk Yöneticisi, Avrupa Birliği Genel Veri Koruma Yönetmeliği [(GDPR)](/compliance/regulatory/gdpr), California Tüketici Koruma Yasası [CCPA),](/compliance/regulatory/ccpa-faq) HIPAA-HITECH (ABD sağlık bakımı gizlilik yasası) ve Brezilya Veri Koruma Yasası (LGPD) gibi veri gizliliği düzenlemelerine ilişkin geliştirmeleri yönetmenize yardımcı olabilir.

Bu makalede, bu aracın veri gizliliği amacıyla kullanımıyla ilgili yol gösterici bilgiler ve almaktadır.

> [!NOTE]
> Öneriler Yöneticisi'nin size yardımcı olması, uyumluluk garantisi olarak yorumlanmaz. Mevzuat ortamınız başına müşteri denetimlerinin ne kadar etkili olduğunu değerlendirmeniz ve doğrulamanız size göredir. Bu hizmetler Çevrimiçi Hizmet Koşullarındaki hüküm ve [şartlara bağlıdır](https://go.microsoft.com/fwlink/?linkid=2108910). Güvenlik ve [Microsoft 365 lisanslama kılavuzuna da bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Uyumluluk Yöneticisi'ni çalışmaya başlama

#### <a name="what-is-compliance-manager"></a>Uyumluluk Yöneticisi nedir?

[Uyumluluk Yöneticisi](../compliance/compliance-manager.md), Microsoft bulut hizmetleriyle ilgili mevzuat uyumluluğu Microsoft 365 uyumluluk merkezi yönelik çalışma makalesinde iş akışı tabanlı bir risk değerlendirme aracıdır. Uyumluluk Yöneticisi, Microsoft 365 veya Azure Active Directory (Azure AD) aboneliğinizin bir parçası olarak, Microsoft bulut hizmetlerinin paylaşılan sorumluluk modeli içinde yasal düzenlemelere uyumluluğu yönetmenize yardımcı olur.

**Değerlendirmeleri kullanmaya hazır**

Uyumluluk Yöneticisi, GDPR ve HIPAA[](../compliance/compliance-manager-assessments.md)/HITECH gibi veri gizliliğiyle ilgili düzenlemelere uygun değerlendirmeler oluşturmak için önceden yerleşik şablonlar sağlar. Şablonlar, düzenlemenin gereksinimlerini karşılamaya yardımcı olmak için yerleşik denetim eşlemesini içerir. Her değerlendirme, Microsoft'un sizin yönettüğü denetimler ve denetimler tarafından ayrı olarak, hedef hizmete özel her düzenleme çağrılarında denetimler hakkında bilgi sağlar.

Önceden yerleşik bir şablon kullanmak, risk değerlendirmelerine hızlı bir şekilde başlamanıza yardımcı olur. Uyumluluk Yöneticisi'ni kullanma konusunda daha yetkin hale geldiyken, kendi denetimlerinizi ve geliştirme eylemlerinizi ekleyerek önceden yerleşik bir şablonu özelleştirilebilir veya kendi özel değerlendirmelerinizi kurum gereksinimlerinize uygun olarak oluşturabilirsiniz.

Uyumluluk [Yöneticisi tarafından sağlanan değerlendirme şablonlarının tam](../compliance/compliance-manager-templates-list.md) listesini görüntüleme.

**Gerçek zamanlı uyumluluk puanı**

Uyumluluk Yöneticisi ayrıca denetimler içinde önerilen geliştirme eylemlerini tamamlamayla ilgili ilerlemenizi ölçüp size bir uyumluluk puanı da sağlar. Bu puanı, ilerlemenizi izlemenize yardımcı olabilir ve riski azaltma potansiyellerine göre eylemlerin önceliklerini belirlemek için kullanabilirsiniz.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Uyumluluk Yöneticisi hızlı başlangıç kılavuzunu kullanma

Uyumluluk [Yöneticisi hızlı başlangıç kılavuzu](../compliance/compliance-manager-quickstart.md) , Uyumluluk Yöneticisi ile çalışmanıza yardımcı olacak önemli kaynakların bağlantılarını sağlar:

- [İlk ziyaret: Uyumluluk Yöneticisi'ni tanıma](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Uyumluluk Yöneticisi panoyla çalışma
    - Uyumluluk puanınızı anlama
    - Learning eylemleri hakkında daha fazla bilgi
    - Değerlendirmeleri ve şablonları anlama
- [Ramping: configure Compliance Manager to manage your compliance activities](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - İlk değerlendirmenizi inşa ve yönetme
    - Değerlendirmeleriniz içinde denetimleri tamamlamak için iyileştirme eylemleri üzerinde uygulama ve test çalışmaları gerçekleştirme
    - Farklı eylemlerin uyumluluk puanınızı nasıl etkile olduğunu anlama
- [Ölçeklendirme: Özel ihtiyaçları karşılamak için gelişmiş işlevselliği kullanma](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Standart dışı ürünleri izlemek için özel Microsoft 365 oluşturma
    - Denetim eklemek veya kaldırmak için var olan şablonları değiştirme
    - Geliştirme eylemlerinin otomatik testlerini ayarlama

## <a name="how-your-compliance-score-is-calculated"></a>Uyumluluk puanınız nasıl hesaplanır?

Uyumluluk puanınız, Microsoft ve müşteri tarafından yönetilen denetim uygulamalarının bir bileşimine bağlı olarak hesaplanır. Ayrıntılı [bir açıklama için uyumluluk](../compliance/compliance-score-calculation.md) puanı hesaplamasına bakın.

Denetimlere, zorunlu mu yoksa imtiyazlı mı olduğu ve bunların koruyucu, güvenlikli veya düzeltici olup olmadığını bağlı olarak puan değeri atanır. Bunlar toplu olarak diğer denetimlere göre uygulamama riskini temsil eder.

Uyumluluk puanı hesaplama makalesinde de sunulan gibi, preventative denetimler daha iyi ve düzeltici denetimlerden daha yüksek puan, zorunlu denetimler ise ikli kontrollerden daha yüksek puana sahip olur.

Uyumluluk Puanı yönetici kullanıcı arabirimi bu parametreleri listelemz ya da bunlara göre filtre uygulama olanağı sağlamaz. Bununla birlikte, ilişkili şablonu Uyumluluk Yöneticisi'den indirirsanız, sonuçta elde edilen veri kümesi çoğu düzenlemenin bu parametrelerini listelemektedir.

Teknik denetimler için, eylem başarıyla uygulanan ve test edilen uyumluluk yöneticisi geliştirme eylem puanını otomatik olarak günceller. Diğer, teknik olmayan denetim&mdash; eylemleri;&mdash; bunlar gibi işlem yapan veya belgelerle ilgili olan eylemler, puanınıza göre puandan önce el ile kaydedilleri gerekir.

Ayrıca birçoğu,&mdash;&mdash; veri gizliliği düzenleme uyumluluğu dışında nedenlerle bekletme etiketleri kullanma gibi başka amaçlara yönelik bazı geliştirme eylemleri gerçekleştirmektedir. Bu tür bir özelliğin kasıtlı uyumluluk eylemlerinin bir parçası değil, başka bir amaçla kullanılıyor olsa bile bu tür bir özelliğin kullanımı konusunda kredi elde edersiniz.

Uyumluluk puanınız, büyük ölçekteki iyileştirmeyi takip etmek için göreli bir ölçü kabul edilir. Mükemmel bir puanı takipmamalı.

## <a name="additional-guidance"></a>Ek kılavuz

Veri gizliliği düzenleme uyumluluğu elde etmeye yardımcı olmak için Uyumluluk Yöneticisi'ni kullanmaya ilişkin birkaç önemli ipucu:

- Her veri gizlilik yönetmeliği, teknik denetimler, belge belirtimleri ve işlem, süreç ve raporlama gereksinimlerinin bir birleşimine sahiptir. Bunların hepsi geliştirme eylemsinde ortaya çıktı.

- Geliştirme eylemlerinin ilgi alanınıza odaklanması için, Uyumluluk Yöneticisi yöneticisinin Çözümler sekmesinde eylem **türüne göre** filtreleyebilirsiniz. Uyumluluk Yöneticisi pano [görünümlerinizi filtreleme hakkında daha fazla bilgi edinebilirsiniz](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- Uyumluluk Yöneticisi'nde tanımlanan geliştirme eylemlerinin göreli önemi ve önceliği, kurum un yönetmesi gereken veri gizlilik riski ile birlikte daha kapsamlı bir risk incelemesi kapsamında düşünülmelidir.

- GDPR, LGPD, CCPA ve HIPAA-HITECH için düzenleme değerlendirme şablonları seçiliyse, birden çok mevzuat gereksinimlerine yönelik iyileştirme eylemi toplama işlemi olsa bile, Uyumluluk Yöneticisi'nde neredeyse 400 geliştirme eylemi listelenmiştir. Bu uzun listeyle daha iyi başa olmak için, iyileştirme eylem filtresini kullanarak sonuç kümesinde daha yönetilebilir bir liste ayarlayın.

- Kategoriler filtresi, bu genel çözümdeki Izleme, Engelleme, Koruma, Koruma ve Araştırma makalelerinin uyumlu olduğu mantıksal gruplamayla geliştirme eylemlerini filtrelemek için bir yol sağlar.

- Geliştirme eylemleri içinde listelenen denetimlerden bazıları belirli bir mevzuat makalesine daha doğrudan bağlı olarak kabul edilirken, diğer denetimler bir düzenlemenin ruhunu daha dolaylı olarak ilişkilendirilmiş olabilir ve birçok kez önerilen etkinlikler veya en iyi uygulamalardır.