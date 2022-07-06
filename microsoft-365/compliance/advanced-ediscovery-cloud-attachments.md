---
title: eBulma'da bulut eklerini toplama (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 06/03/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview eKeşif (Premium) içindeki koleksiyonları kullanarak bir araştırmada veya olayda gözden geçirmek üzere bulut eklerini toplayın.
ms.openlocfilehash: e59b4720613572763b300517c0b603493ab5a9de
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636953"
---
# <a name="collect-cloud-attachments-in-microsoft-purview-ediscovery-premium"></a>Microsoft Purview eKeşif'da bulut eklerini toplama (Premium)

Bulut ekleri, genellikle SharePoint sitesinde ve OneDrive'da depolanan belgelerin bağlantılarıdır. Bu nedenle, e-posta iletisine veya Teams sohbet konuşmasına belgenin gerçek bir kopyasını eklemek yerine dosyanın bağlantısını paylaşma seçeneğiniz vardır. Bulut ekleri, belgeleri paylaşmanın ve kuruluşunuzdaki diğer kişilerle işbirliği yapmanın etkili bir yoludur. Ancak eBulma iş akışı sırasında bulut ekleri güçlükler sunar çünkü eBulma aramasında paylaşılan belgedeki gerçek içerik değil yalnızca bulut eki bağlantısı döndürülür. Bu zorluğu gidermek için eBulma (Premium), bulut eklerini toplamaya yönelik iki çözüm sağlar:  

- Bir bulut ekinde bağlantılı bir belgenin canlı sürümünü toplama.

- Belgenin bir bulut ekinde paylaşıldığı sırada sürümünü toplama.

## <a name="collecting-cloud-attachments"></a>Bulut eklerini toplama

Taslak koleksiyon oluşturduğunuzda ve arama sonuçları bulut ekleri içeren öğeler içerdiğinde, taslak koleksiyonu bir gözden geçirme kümesine işlerken bulut ekinin hedefini toplama seçeneğine sahip olmanız gerekir. Bu seçeneği belirlediğinizde, eBulma (Premium), bulut ekinde bağlı olan belgeleri gözden geçirme kümesine ekler. Bu, hedef belgeleri gözden geçirmenize ve belgenin olay veya araştırmanızla ilgili olup olmadığını belirlemenize olanak tanır.

Aşağıdaki ekran görüntüsünde, bir koleksiyonu gözden geçirme kümesine işlerken bulut eklerinin hedeflerini ekleme seçeneği gösterilmektedir.

![Bir koleksiyonu gözden geçirme kümesine işlerken bulut eklerini ekleme seçeneği](../media/CollectCloudAttachments1.png)

> [!NOTE]
>- eBulma 'da (Premium) [yeni durum biçimini](advanced-ediscovery-new-case-format.md) kullanırsanız, bulut eklerini gözden geçirme kümesine ekleme seçeneği varsayılan olarak seçilidir ve seçilemez.<br/>
>- Ayrıca, bulut eklerinin tüm sürümlerini (paylaşılan sürüme ek olarak) gözden geçirme kümesine ekleme seçeneğiniz de vardır.  
Bir koleksiyonu gözden geçirme kümesine işleme yönergeleri için bkz. [Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md).

## <a name="collecting-the-version-shared-in-a-cloud-attachment-preview"></a>Bulut ekinde paylaşılan sürümü toplama (önizleme)

Bulut eklerini toplamaya yönelik eBulma (Premium) iş akışı yalnızca bir bulut ekinin en güncel sürümünü bir gözden geçirme kümesine eklemeyi içerir. Bu, toplanan ve bir gözden geçirme kümesine eklenen sürümün başlangıçta bulut ekinde paylaşılan sürümden farklı olabileceği anlamına gelir. Bu nedenle, paylaşıldığı sırada bulut ekinde bulunan içerik kaldırılmış olabilir ve gözden geçirme kümesine eklenen geçerli sürümde mevcut olmayabilir.

Kuruluşlar artık bir belgenin bulut eki olarak paylaşıldığı sırada sürümünü korumak için Microsoft 365 bekletme etiketlerini kullanma seçeneğine sahiptir. Bunu yapmak için kuruluşunuz bir bekletme etiketi oluşturabilir, etiketi bulut eklerine uygula seçeneğini belirleyebilir ve ardından etiketi SharePoint ve OneDrive'da depolanan belgelere otomatik olarak uygulayabilir. Bu yapılandırmayı ayarladıktan sonra, dosyanın paylaşıldığında belgenin bir kopyası oluşturulur. Ayrıca, belge yeniden değiştirilip bulut eki olarak paylaşılırsa, değiştirilen sürüm de korunur. Dosya yeniden değiştirilir ve paylaşılırsa, dosyanın yeni sürüm olarak yeni bir kopyası korunur.

Bulut eklerinin paylaşılan sürümlerinin korunması, kuruluşunuzun geçerli canlı sürüm yerine paylaşılan belgenin belirli bir sürümüyle ilgili olabilecek içeriğin korunmasını ve toplanmasını kapsamasına yardımcı olabilir. Bu bekletme çözümünü uyguladıktan sonra hem bulut ekinin geçerli canlı sürümü hem de bulut ekinde paylaşılan sürüm toplanır ve bir gözden geçirme kümesine eklenir.

Bekletme etiketi ayarlama ve bunu bulut eklerine otomatik olarak uygulama yönergeleri için bkz. [Etiketleri bulut eklerine otomatik olarak uygulama](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments).

Aşağıdaki ekran görüntüsünde, inceleme kümesine eklenen *XYZ Research.docx* adlı bir bulut eki belgesi gösterilmektedir. Belge, Teams sohbet konuşmasında bulut eki olarak paylaşıldı. Gözden geçirme kümesi, başlangıçta bulut ekinde paylaşılan sürümü de içerir. Bulut ekinin bu sürümünün adının sistem tarafından oluşturulduğuna ve yazarın **SharePoint** olarak tanımlandığından emin olabilirsiniz.

![Paylaşılan bulut ekinin bir gözden geçirme kümesinde görüntülenen sürümü](../media/CollectCloudAttachments2.png)

Ayrıca, geçerli canlı sürüm ve paylaşılan sürüm, üst nesnenin **FamilyId** değeriyle (e-posta iletisi veya Teams sohbet konuşması gibi) aynı **FamilyId** özellik değerine sahiptir. Bu, bulut eklerini paylaşıldıkları öğeyle gruplandırmanıza olanak tanır.

Bekletme etiketini uyguladıktan ve etiketi SharePoint belgelerine otomatik olarak uyguladıktan sonra, bir taslak koleksiyonu gözden geçirme kümesine işlerken bulut eklerini toplama seçeneğini belirlemeye devam edebilirsiniz. Bulut ekleri toplandığında hem geçerli canlı sürüm hem de başlangıçta paylaşılan sürüm gözden geçirme kümesine eklenir.
