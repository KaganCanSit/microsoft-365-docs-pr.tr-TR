---
title: E-posta ile bulut Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Bir soruşturma veya Advanced eDiscovery gözden geçirmek üzere bulut eklerini toplamak üzere E-posta'da koleksiyonları kullanın.
ms.openlocfilehash: bdf30fea0e168d4b36175296f524ade13539970b
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2021
ms.locfileid: "63007659"
---
# <a name="collect-cloud-attachments-in-advanced-ediscovery-preview"></a>E-postalarda bulut Advanced eDiscovery (önizleme) toplama

Bulut ekleri, genellikle site içinde veya başka bir SharePoint depolanan belgelere OneDrive. Dolayısıyla, e-posta iletisine veya sohbet görüşmesine bir Teams kopyasını eklemek yerine, dosyanın bağlantısını paylaşma seçeneğiniz vardır. Bulut ekleri, belgeleri paylaşmak ve organizasyonlu diğer kişiler ile işbirliği yapmak için etkili bir yol sağlar. Ancak eBulma iş akışı sırasında bulut ekleri, paylaşılan belgeye gerçek içeriği değil yalnızca bulut eki bağlantısı bir eBulma aramasinde döndürüleceği için zorluk gösterir. Bu soruna çözüm olarak, Advanced eDiscovery ekleri toplamak için iki çözüm sağlar:  

- Bulut eke bağlı bir belgenin canlı sürümünü toplama.

- Belgenin bir bulut eksinde paylaşılırken sürümünü toplama.

## <a name="collecting-cloud-attachments"></a>Bulut eklerini toplama

Bir taslak koleksiyonu  oluşturmanıza ve arama sonuçlarında bulut ekleri içeren öğelere sahipseniz, taslak koleksiyonunu gözden geçirme kümesine işlerken bulut ekin hedefini toplama seçeneğiniz vardır. Bu seçeneği tercih ettiyseniz, Advanced eDiscovery bulut eke bağlı olan belgeleri gözden geçirme kümesine ekler. Bu, hedef belgeleri gözden geçirmenize ve belgenin olay veya incelemenize uygun olup olmadığını belirlemenizi sağlar.

Aşağıdaki ekran görüntüsünde, koleksiyonu gözden geçirme kümesine işlerken bulut eklerinin hedeflerini ekleme seçeneği gösterir.

![Koleksiyonu gözden geçirme kümesine işlerken bulut ekleri ekleme seçeneği](../media/CollectCloudAttachments1.png)

> [!NOTE]
>- Advanced eDiscovery'da yeni [](advanced-ediscovery-new-case-format.md) büyük/harf biçimini kullanıyorsanız, gözden geçirme kümesine bulut ekleri ekleme seçeneği varsayılan olarak seçilidir ve seçilmez.<br/>
>- Ayrıca, bulut eklerinin tüm sürümlerini (paylaşılan sürüme ek olarak) gözden geçirme kümesine ekleme seçeneğiniz de vardır.  
Koleksiyonu gözden geçirme kümesine kaydetme yönergeleri için bkz. [Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md).

## <a name="collecting-the-version-shared-in-a-cloud-attachment"></a>Bulut eksinde paylaşılan sürümü toplama

Bulut Advanced eDiscovery toplamaya yönelik en iyi iş akışı, yalnızca bulut eklerinin en güncel sürümünü gözden geçirme kümesine eklemeyi içerir. Bu, bir gözden geçirme kümesinde toplanan ve eklenen sürümün, özgün olarak bulut eksinde paylaşılan sürümden farklı olduğu anlamına gelir. Dolayısıyla, bulut ekinde yer alan ve paylaşıldığı sırada bulut ekinde yer alan içerik kaldırılmış ve gözden geçirme kümesine eklenmiş olan geçerli sürümde yer almayabilirsiniz.

Kuruluşlar artık belgenin sürümünü bulut eki Microsoft 365 bir zamanda korumak için bekletme etiketlerini saklama seçeneğine sahiptir. Bunu yapmak için, organizasyonunız bir bekletme etiketi oluşturabilir, etiketi bulut eklere uygula seçeneğini belirleyin ve sonra etiketi otomatik olarak SharePoint ve OneDrive. Bu yapılandırmayı oluşturduktan sonra, dosya paylaşılırken belgenin bir kopyası oluşturulur. Ayrıca, belge değiştirilirse ve yeniden bulut eki olarak paylaşılırsa, değiştirilen sürüm de korunur. Dosya değiştirilir ve yeniden paylaşılırsa, dosyanın yeni bir sürümü olarak yeni bir kopyası korunur.

Bulut eklerinin paylaşılan sürümlerinin korunması, kurum gerek geçerli canlı sürüm yerine belgenin paylaşılan belirli sürümüyle ilgili olabilecek içeriğin korunmasına ve toplanmasına yardımcı olur. Bu bekletme çözümünü gerçekleştirdikten sonra, hem bulut eklerinin geçerli canlı sürümü hem de bulut ekte paylaşılan sürüm toplanır ve gözden geçirme kümesine eklenir.

Bir bekletme etiketini ayarlama ve bunu bulut eklerine otomatik olarak uygulama yönergeleri için bkz. Bulut eklerine [otomatik olarak etiket uygulama](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments).

Aşağıdaki ekran görüntüsünde, gözden geçirme kümesine *eklenmiş olan XYZ Research.docx* adlı bir bulut eki belgesi yer aldı. Belge bir sohbet görüşmesinde bulut eki Teams paylaşıldı. Gözden geçirme kümesi, özgün olarak bulut eksinde paylaşılan sürümü de içerir. Bulut eklerinin bu sürümünün adının sistem tarafından oluşturulmuş olduğunu ve yazarın e-posta olarak **SharePoint.**

![Gözden geçirme kümesinde paylaşılan bir bulut eki sürümü](../media/CollectCloudAttachments2.png)

Buna ek olarak, geçerli canlı sürüm ve paylaşılan sürüm, üst nesnenin **FamilyId** değeriyle (e-posta iletisi veya sohbet görüşmesi gibi) aynı **FamilyId** özelliği Teams vardır. Bu sayede bulut eklerini, içinde paylaşıldıları öğeyle gruplandırabilirsiniz.

Bekletme etiketini uygulayan ve bu etiketi SharePoint belgelerine otomatik olarak uygulaytıktan sonra, taslak koleksiyonunu gözden geçirme kümesine işlerken bulut eklerini toplama seçeneğini yine seçersiniz. Bulut ekleri toplanıyorsa, hem geçerli canlı sürüm hem de başlangıçta paylaşılan sürüm gözden geçirme kümesine eklenir.
