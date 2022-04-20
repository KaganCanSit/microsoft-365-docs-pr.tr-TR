---
title: eBulma'da konuşmaları gözden geçirme (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.assetid: ''
description: Microsoft Teams ve Yammer gruplarında sohbet konuşmalarını yeniden yapılandırmak, gözden geçirmek ve dışarı aktarmak için Microsoft Purview eBulma (Premium) (konuşma yazışması olarak adlandırılır) konuşma yeniden oluşturma özelliği hakkında bilgi edinin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c3cd05ab340775a7a923b9e4a0f66c3abaf559cb
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993282"
---
# <a name="conversation-threading-in-ediscovery-premium"></a>eBulma'da konuşma yazışması oluşturma (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Anlık ileti, soru sormanın, fikir paylaşmanın veya büyük kitleler arasında hızlı bir şekilde iletişim kurmanın kullanışlı bir yoludur. Microsoft Teams ve Yammer grupları gibi anlık ileti platformları kurumsal işbirliğinin temeli haline geldikçe kuruluşların eBulma iş akışlarının bu yeni iletişim ve işbirliği biçimlerini nasıl ele alacağını değerlendirmesi gerekir.

Microsoft Purview eKeşif'teki (Premium) konuşma yeniden yapılandırma özelliği, bağlamsal içeriği belirlemenize ve farklı konuşma görünümleri oluşturmanıza yardımcı olmak için tasarlanmıştır. Bu özellik, Microsoft Teams gibi platformlarda oluşturulan anlık ileti konuşmalarını (*yazışma konuşmaları* olarak da adlandırılır) verimli ve hızlı bir şekilde gözden geçirmenizi sağlar.

Konuşma yeniden yapılandırma ile, iş parçacıklı konuşmaları yeniden yapılandırmak, gözden geçirmek ve dışarı aktarmak için yerleşik özellikleri kullanabilirsiniz. eBulma (Premium) konuşma yeniden derlemesini kullanarak:

- Konuşmadaki tüm iletilerde benzersiz ileti düzeyinde meta verileri koruma.

- Arama sonuçlarınızın çevresinde bağlamsal iletiler toplayın.

- Yazışma yazışmalarını gözden geçirin, açıklama ekleyin ve yeniden düzenleme yapın.

- Tek tek iletileri veya yazışma konuşmalarını dışarı aktarma

## <a name="terminology"></a>Terminoloji

Konuşma yeniden yapılandırmayı kullanmaya başlamanıza yardımcı olacak birkaç tanım aşağıdadır.

- **Ileti:** Konuşmanın en küçük birimini temsil edin. İletilerin boyutu, yapısı ve meta verileri farklılık gösterebilir.

- **Konuşma:** Bir veya daha fazla iletinin gruplandırma işlemini temsil eder. Farklı uygulamalarda konuşmalar farklı şekillerde gösterilebilir. Bazı uygulamalarda, var olan bir iletiyi yanıtlamaktan kaynaklanan açık bir eylem vardır. Konuşmalar, bu kullanıcı eyleminin bir sonucu olarak açıkça oluşturulur. Örneğin, Microsoft Teams'daki kanal konuşmasının ekran görüntüsü aşağıda verilmiştir.

   ![kanal konuşma Microsoft Teams.](../media/threadedchat.png)

   Diğer uygulamalarda (Teams grup sohbeti iletileri gibi), resmi bir yanıt zinciri yoktur ve bunun yerine iletiler tek bir yazışma içinde "iletilerin düz nehri" olarak görünür. Bu tür uygulamalarda, konuşmalar belirli bir süre içinde gerçekleşen bir ileti grubundan çıkarılır. İletilerin bu "geçici gruplandırılması" (yanıt zincirinin aksine) belirli bir ilgi konusuyla ilgili "ileri geri" konuşmayı temsil eder.

## <a name="step-1-create-a-draft-collection"></a>1. Adım: Taslak koleksiyon oluşturma

İlgili koruyucuları ve içerik konumlarını belirledikten sonra, uygun olabilecek içeriği bulmak için bir arama oluşturabilirsiniz. eBulma (Premium) örneğindeki **Koleksiyonlar** sekmesinde, Yeni koleksiyon'a tıklayıp sihirbazı izleyerek bir **koleksiyon** oluşturabilirsiniz. Koleksiyon oluşturma, arama sorgusu oluşturma ve arama sonuçlarını önizleme hakkında bilgi için bkz. [Taslak koleksiyonu oluşturma](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>2. Adım: Taslak koleksiyonu gözden geçirme kümesine işleme

Bir koleksiyondaki arama sorgusunu gözden geçirip son haline getirdikten sonra, arama sonuçlarını bir gözden geçirme kümesine ekleyebilirsiniz. Arama sonuçlarınızı bir gözden geçirme kümesine eklediğinizde, inceleme ve analiz sürecini kolaylaştırmak için özgün veriler bir Azure Depolama alanına kopyalanır. Gözden geçirme kümesine arama sonuçları ekleme hakkında daha fazla bilgi için bkz. Gözden [geçirme kümesine taslak koleksiyonu işleme](commit-draft-collection.md).

Konuşmalardan bir gözden geçirme kümesine öğe eklediğinizde, koleksiyonun arama ölçütlerine uyan öğeleri içeren konuşmalardan bağlamsal iletileri toplamak için yazışmalı konuşmalar seçeneğini kullanabilirsiniz. Yazışma konuşmaları seçeneğini seçtikten sonra aşağıdaki işlemler yapılabilir:

  ![Konuşma Alma.](../media/messagesandconversations.png)

1. Anahtar sözcük ve tarih aralığı sorgusu kullanıldığında, arama *İleti 3'te* bir isabet döndürdü. Bu ileti, *CRC1* tarafından gösterilen daha büyük bir konuşmanın parçasıydı.

2. Verileri bir gözden geçirme kümesine eklediğinizde ve konuşma alma seçeneklerini etkinleştirdiğinizde, eBulma (Premium) geri döner ve *CRC1'deki* diğer öğeleri toplar.

3. Öğeler gözden geçirme kümesine eklendikten sonra *CRC1'den* gelen tüm iletileri tek tek gözden geçirebilirsiniz.

Yazışmalı konuşmalar seçeneğini etkinleştirmek için bkz [. Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>3. Adım: Yazışma yazışmalarını gözden geçirme ve dışarı aktarma

İçerik işlenip gözden geçirme kümesine eklendikten sonra, gözden geçirme kümesindeki verileri gözden geçirmeye başlayabilirsiniz. Tek tek iletiler birlikte oluşturulur ve konuşma olarak sunulur. Bu, bağlamsal konuşmaları gözden geçirmenize ve dışarı aktarmanıza olanak tanır.

  ![Konuşma gözden geçirme kümesi.](../media/ConversationRSOptions.PNG)

Aşağıdaki bölümlerde konuşmaları gözden geçirme ve dışarı aktarma işlemleri açıklanmaktadır.

### <a name="reviewing-conversations"></a>Konuşmaları gözden geçirme

Gözden geçirme kümesinde, gözden geçirme işlemini kolaylaştırmak için aşağıdaki seçenekleri kullanabilirsiniz.

- **Konuşmaya göre gruplandır:** Kullanıcıların gözden geçirme sürecini basitleştirmesine ve hızlandırmasına yardımcı olmak için iletileri aynı konuşma içinde birlikte gruplandırın.

- **Özet görünümü:** Yazışma yazışmasını görüntüler. Bu görünümde konuşmanın tamamını görebilir ve her iletinin meta verilerine erişebilirsiniz.

   - Tek tek iletiler için meta verileri görüntüleme

   - Tek tek iletileri indirme

- **Metin görünümü:** Konuşmanın tamamı için ayıklanan metni sağlar.

- **Görünüme açıklama ekleme:** Konuşmanın yazışma görünümünü işaretlemenize olanak tanır. Konuşmadaki tüm iletiler aynı açıklama eklenmiş belgeyi paylaşır.

- **Etiketleme:** Bir gözden geçirme kümesindeki konuşmaları görüntülerken, Kodlama **panelinde Etiketleme paneli'ne** tıklayarak etiketleri görüntüleyebilir ve uygulayabilirsiniz.

- **Konuşma dönüştürmeyi yeniden çalıştırma:** İletiler konuşma gözden geçirme kümesine eklendiğinde, yazışma özetini oluşturmak ve görünümlere açıklama eklemek için otomatik olarak bir dönüştürme işi çalıştırılır. Konuşma Yeniden Yapılandırma işi başarısız olursa, gözden geçirme kümesinde **Eylem > Konuşma PDF'leri oluştur'a** tıklayarak bu işi yeniden çalıştırabilirsiniz.

### <a name="exporting-conversations"></a>Konuşmaları dışarı aktarma

Gözden geçirme kümesinden konuşmaları dışarı aktarırken seçebileceğiniz seçenekler için bkz. [Belgeleri gözden geçirme kümesinden dışarı aktarma](export-documents-from-review-set.md#export-options).

Özel olarak, sohbet konuşmalarının tamamını tek bir PDF dosyasında dışarı aktarabilir veya konuşmadaki her sohbet iletisini tek bir dosya olarak dışarı aktarabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

eBulma'da (Premium) büyük/küçük harf verilerini gözden geçirme hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın:

- [Bir inceleme setindeki içeriği sorgulama ve filtreleme](review-set-search.md)
- [Bir inceleme setindeki belgeleri etiketleme](tagging-documents.md)
- [Büyük/küçük harf verilerini görüntüleme](view-documents-in-review-set.md)
- [Servis talebi verilerini analiz etme](analyzing-data-in-review-set.md)
- [Servis talebi verilerini dışarı aktarma](exporting-data-ediscover20.md)
