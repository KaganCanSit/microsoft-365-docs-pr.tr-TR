---
title: eBulma'daki koleksiyonlara genel bakış (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 05/31/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: eBulma (Premium) içindeki koleksiyonları kullanarak olay veya araştırmanıza göre içerik arayın ve toplayın.
ms.openlocfilehash: 7b5c09cd0b8a9f0a2ea0fe75e3ebf82e27223b14
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839393"
---
# <a name="learn-about-collections-in-ediscovery-premium"></a>eBulma'daki koleksiyonlar hakkında bilgi edinin (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşlar bir soruşturma veya olası dava ile ilgili olabilecek iletişimleri ve içerikleri toplamayla karşı karşıya kaldıklarında, en iyi koşullarda önemli bir zorlukla karşı karşıya kalırlar. Günümüzün modern çalışma alanında, içeriğin hacmi, çeşitliliği ve hızı yeniliklere ve uzaktan çalışmaya olanak tanırken, eBulma araştırmalarına yönelik koleksiyonları yönetme gereksinimlerini ve sürecini de genişletmektedir.

Koleksiyon iş akışı, yerel konumlardan ve kaynaklardan içerik ayıklama konusunda önemli teknik zorluklar oluşturur. Ayrıca, yaygın dava veya araştırma senaryoları için değerlendirme ve strateji açısından kritik bir noktadır. Kuruluşlar bir araştırmayı değerlendirmeye başladığında, sorulan ilk sorular kimin dahil olduğu? Kimlerin dahil olduğunu belirledikten sonra, bu koruyucular ilgili içeriği korumak için hızlı bir şekilde askıya alınabiliyor. Bir sonraki soru ne oldu? Herhangi bir soruşturmayla ilgili bu ikinci temel soruyu yanıtlamak için yöneticilerin verilere yönelmelidir. Yöneticiler, gerçekleşen sorunun en ilgili içeriğini hızla değerlendirmek için, toplama sonuçlarının çok geniş olmadan kapsamlı olduğundan emin olmak için sorunun hedefini daraltmaya başlar.

eBulma (Premium) içindeki koleksiyonlar, eBulma yöneticilerinin e-posta, belgeler, Teams tepkiler ve Microsoft 365 diğer içeriklerde içerik aramasını hızla kapsamalarına yardımcı olur. Koleksiyonlar, yöneticilere servis talebiyle ilgili olabilecek içerikle ilgili bir tahmin sağlar. Bu, yöneticilerin bir servis talebiyle ilgili içeriğin boyutu ve kapsamı hakkında hızlı ve bilinçli kararlar almalarına olanak tanır. eBulma yöneticileri, gözaltı veri kaynaklarını (posta kutuları ve SharePoint siteleri gibi) aramak ve koleksiyonlarının kapsamını hızla tanımlamak için belirli arama ölçütlerini (anahtar sözcükler ve tarih aralıkları gibi) kullanarak bir koleksiyon oluşturabilir.

Koleksiyon tanımlandıktan sonra, eBulma yöneticileri koleksiyonu taslak olarak kaydedebilir ve veri hacmine ilişkin tahminler, sonuçları içeren içerik konumları ve arama sorgusu koşulu için isabet sayısı dahil olmak üzere tahminler alabilir. Bu içgörüler, eBulma iş akışındaki gözden geçirme ve analiz aşamalarına geçmeden önce koleksiyonun kapsamını daraltacak veya genişletecek şekilde düzeltilmesi gerektiğinin bildirilmesine yardımcı olabilir.

Yönetici koleksiyonun kapsamından ve yanıt verme olasılığı olan tahmini içerik miktarından memnun olduğunda, içeriği bir gözden geçirme kümesine ekleyebilir veya *işleyebilir* . Bir koleksiyonu bir gözden geçirme kümesine işlerken, bu yöneticinin sohbet konuşmalarını, bulut eklerini ve belge sürümlerini dahil etme seçenekleri de vardır. Koleksiyondaki içerik, gözden geçirme kümesine alım sırasında başka bir işlem düzeyinden de geçer. ve koleksiyon son koleksiyon özetiyle güncelleştirilir. gözden geçirme kümesine içerik eklendikten sonra, eBulma yöneticileri içeriği en aza indirmek ve gözden geçirmek için içinde sorgulamaya, gruplandırmaya ve daraltmaya devam edebilir. Ayrıca koleksiyon, inceleme kümesine kaydedilmiş içerikle ilgili bilgiler ve istatistiklerle güncelleştirilir. Bu, koleksiyondaki içerik hakkında geçmişe dönük bir başvuru sağlar.

Koleksiyonların bir eBulma (Premium) sürümünde, **Aramalar** sekmesi Microsoft Purview uyumluluk portalı bir eBulma (Premium) durumunda **Koleksiyonlar** olarak yeniden adlandırıldı. Koleksiyonun kapsamını ve boyutunu tanımlama adımları, konumları ve koşulları tanımlamak için aramayla aynı işlemi izler. Taslak olarak kaydetme ve önizleme tahminlerini alma, gözden geçirme kümesine tam arama ve koleksiyon işlemeden önce hedeflenen koleksiyon kapsamının hızlı doğrulanmasını sağlar. Bu, arama ve toplama işlemi sırasında içeriği en aza indirmeye başlamak için iyileştirilmiş iş yönetimi ve hedefli yinelemeler sağlar.

## <a name="collections-workflow"></a>Koleksiyonlar iş akışı

eBulma'da (Premium) koleksiyonları kullanmaya başlamak için işlemdeki her adımın temel iş akışı ve açıklamaları aşağıdadır.

![eBulma'da koleksiyon iş akışı (Premium).](../media/CollectionsWorkflow.png)

1. **Taslak koleksiyon oluşturma ve çalıştırma**. İlk adım bir taslak koleksiyon oluşturmak ve aranacak koruyucu ve gözetimsiz veri kaynaklarını tanımlamaktır. Servis talebine eklenmemiş diğer veri kaynaklarını da arayabilirsiniz. Veri kaynaklarını ekledikten sonra, arama sorgusunu büyük/küçük harfe uygun içerik için veri kaynaklarında arama yapmak üzere yapılandırabilirsiniz. Büyük olasılıkla büyük/küçük harfe en uygun içeriği döndüren arama sorguları oluşturmak için anahtar sözcükler, özellikler ve koşullar oluşturabilirsiniz. Daha fazla bilgi için bkz. [Taslak koleksiyonu oluşturma](create-draft-collection.md).

2. **Tahminleri ve istatistikleri gözden geçirin**. Bir taslak koleksiyon oluşturup çalıştırdıktan sonra, sonraki adım, ilgili içeriğin bulunup bulunmadığını ve en çok isabet alan içerik konumlarını doğrulamanıza yardımcı olmak için koleksiyon istatistiklerini görüntülemektir. Ayrıca, içeriğin araştırmanızın kapsamında olup olmadığını belirlemenize yardımcı olması için arama sonuçlarının bir örneğini de önizleyebilirsiniz. Daha fazla bilgi için bkz. [Taslak koleksiyonlar için istatistikler ve raporlar](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).

3. **Taslak koleksiyonu gözden geçirme ve yeniden çalıştırma**. Koleksiyon tarafından döndürülen tahminlere ve istatistiklere bağlı olarak, aranan veri kaynaklarını ve koleksiyonu genişletmek veya daraltmak için arama sorgusunu değiştirerek taslak koleksiyonu düzenleyebilirsiniz. Koleksiyonun olayınıza en uygun içeriği içerdiğinden emin olana kadar taslak koleksiyonu güncelleştirebilir ve yeniden çalıştırabilirsiniz.

4. **Taslak koleksiyonu gözden geçirme kümesine işleme**. Koleksiyonun servis talebiyle ilgili tür içeriğini döndürdüğünden memnun olduğunuzda, koleksiyonu gözden geçirme kümesine işleyebilirsiniz. Bir koleksiyonu işlerken, gözden geçirme kümesine konuşma yazışmaları, bulut ekleri ve belge sürümleri ekleme seçeneğiniz vardır ve bunların tümü büyük/küçük harfle ilgili olabilir.

   Bir koleksiyonu işlediğiniz zaman, e-posta imzaları ve resimler gibi alt öğeler üst öğeden (e-posta iletisi, sohbet iletisi veya belge gibi) ayıklanır ve sonra alt öğeden herhangi bir metni ayıklamak için Optik Karakter Tanıma (OCR) tarafından işlenir. Daha sonra alt öğelerden ayıklanan metin, gözden geçirme kümesinde görüntüleyebilmeniz için üst öğesine eklenir. Gözden geçirme kümesine ayrı bir dosya olarak alt öğe eklemeyerek, eBulma (Premium), gözden geçirme kümesine eklenmiş potansiyel olarak önemsiz öğe sayısını sınırlamaya yardımcı olur. Alt öğelerin nasıl işlenme şekli hakkında daha fazla bilgi için bkz [. Koleksiyon istatistikleri ve raporları](collection-statistics-reports.md#collection-contents).

   Daha fazla bilgi için bkz [. Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md).

5. **Koleksiyon özetini ve istatistiklerini gözden geçirin**. Bir koleksiyonu bir gözden geçirme kümesine işledikten sonra, ayıklanan öğelerle ilgili istatistikler, derin dizin oluşturma, koleksiyon için kullanılan arama sorgusu ve öğelerin toplandığı içerik konumları gibi koleksiyon hakkındaki bilgiler korunur. Ayrıca, işlenen koleksiyonlar düzenlenemez veya yeniden çalıştırılamaz. Bunları yalnızca kopyalayabilir veya silebilirsiniz. Koleksiyonların korunması, bir gözden geçirme kümesine eklenen toplanan öğelerin geçmiş kaydını sağlar. Daha fazla bilgi için bkz. [Kaydedilmiş koleksiyonlar için istatistikler ve raporlar](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).
