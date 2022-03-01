---
title: E-Advanced eDiscovery
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
description: Farklı gruplarda ve farklı gruplarda sohbet Advanced eDiscovery yeniden yapılandırma, gözden geçirme ve dışarı aktarma için Advanced eDiscovery sohbet sohbeti özelliği hakkında Microsoft Teams Yammer öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7bd13bdb01298d0cf1f37671f044a3405a2de0b6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034259"
---
# <a name="conversation-threading-in-advanced-ediscovery"></a>Konuşma dizileri Advanced eDiscovery

Anlık ileti, soru sormanın, fikir paylaşmanın veya büyük bir hedef kitleyle hızlı bir şekilde iletişim kurmanın kolay bir yolu. Microsoft Teams ve Yammer grupları gibi anlık ileti platformları kurumsal işbirliğinin temel bir özelliği haline geldi olarak, kuruluşların eBulma iş akışının bu yeni iletişim ve işbirliği biçimlerine nasıl adreslerini değerlendirmeleri gerekir.

Web'de konuşma Advanced eDiscovery özelliği, bağlamsal içeriği tanımlamanıza ve farklı konuşma görünümleri üretmenize yardımcı olmak için tasarlanmıştır. Bu özellik, konuşma dizileri gibi platformlarda oluşturulan tam anlık ileti konuşmalarını (zincir konuşmalar olarak da *adlandırılan) verimli* ve hızlı bir şekilde Microsoft Teams.

Konuşma konuşmalarını yeniden can geçirmek, gözden geçirmek ve dışarı aktarmak için yerleşik özellikleri kullanabilirsiniz. Aşağıdaki Advanced eDiscovery görüşme için sohbet sohbeti sohbeti her zaman kullanın:

- Konuşma içindeki tüm iletilerde ileti düzeyinde benzersiz meta verileri koruma.

- Arama sonuçlarınız çevresinde bağlamsal iletiler toplayın.

- Dizili konuşmaları gözden geçirme, açıklamalı açıklama ve açıklama ek açıklama.

- Tek tek iletileri veya ileti dizili konuşmaları dışarı aktarma

## <a name="terminology"></a>Terminoloji

Konuşma konuşma konuşmalarını kullanmaya başlamanıza yardımcı olacak birkaç tanım:

- **İletiler:** Konuşmanın en küçük birimini temsil etme. İletilerin boyutu, yapısı ve meta verileri farklılık gösterebilir.

- **Görüşme:** Bir veya birden çok ileti grubunu temsil eder. Farklı uygulamalarda konuşmalar farklı şekillerde temsil edildi olabilir. Bazı uygulamalarda, var olan bir iletiyi yanıtlamaya neden olan açık bir eylem vardır. Bu kullanıcı eyleminin sonucunda konuşmalar açıkça oluşturulur. Örneğin, bu videoda kanal konuşmalarının ekran Microsoft Teams.

   ![Microsoft Teams Konuşmayı Seçin.](../media/threadedchat.png)

   Diğer uygulamalarda (Teams'ta grup sohbeti iletileri gibi), resmi bir yanıt zinciri değildir ve bunun yerine iletiler tek bir zincir içinde "iletilerin düz bir nehri" olarak görünür. Bu tür uygulamalarda, konuşmalar belirli bir süre içinde oluşan bir grup iletiden çıkar. İletilerin "yumuşak gruplama" olması (yanıt zincirinin aksine) belirli bir ilgi konusuyla ilgili "ileri ve geri" konuşmalarını temsil etme.

## <a name="step-1-create-a-draft-collection"></a>1. Adım: Taslak koleksiyonu oluşturma

İlgili koruyucuları ve içerik konumlarını belirledikten sonra, olası ilgili içeriği bulmak için bir arama oluşturabilirsiniz. Koleksiyonlar **sekmesinin** Koleksiyonlar Advanced eDiscovery, Yeni koleksiyon'a tıklar ve sihirbazı **takip eden bir** koleksiyon oluşturabilirsiniz. Koleksiyon oluşturma, arama sorgusu oluşturma ve arama sonuçlarını önizleme hakkında bilgi için bkz. [Taslak koleksiyonu oluşturma](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>2. Adım: Taslak koleksiyonunu gözden geçirme kümesine kaydetme

Koleksiyonda arama sorgusunu gözden geçirdikten ve son olarak tamamladikten sonra, arama sonuçlarını gözden geçirme kümesine  eklersiniz. Arama sonuçlarınızı gözden geçirme kümesine eklerken, gözden geçirme ve çözümleme işlemini kolaylaştırmak için özgün veriler bir Azure Depolama alanına kopyalanır. Gözden geçirme kümesine arama sonuçları ekleme hakkında daha fazla bilgi için bkz [. Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md).

Konuşmalardan gözden geçirme kümesine öğe eklerken, koleksiyondaki arama ölçütlerine uyan öğeler içeren konuşmalardan bağlamsal iletileri toplamak için zincirsel konuşmalar seçeneğini kullanabilirsiniz. Dizi konuşmaları seçeneğini kullandıktan sonra, aşağıdaki şeyler olabilir:

  ![Konuşma Alma.](../media/messagesandconversations.png)

1. Anahtar sözcük ve tarih aralığı sorgusu kullanarak, arama İleti *3'te bir arama verdi*. Bu ileti, CRC1 tarafından gösterilen daha büyük bir *konuşmanın parçası oldu*.

2. Verileri bir gözden geçirme kümesine ekler ve konuşma alma seçeneklerini etkinleştirirken, *Advanced eDiscovery CRC1'de* geri dönüp diğer öğeleri toplar.

3. Öğeler gözden geçirme kümesine eklendikten sonra, *CRC1'den* tek tek tüm iletileri gözden geçirebilirsiniz.

Zincirli görüşmeler seçeneğini etkinleştirmek için bkz. [Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>3. Adım: Dizi konuşmalarını gözden geçirme ve dışarı aktarma

İçerik işlendikten ve gözden geçirme kümesine eklendikten sonra, gözden geçirme kümesinde verileri gözden geçirmeye başlayabilirsiniz. Tek tek iletiler bir araya konur ve konuşmalar olarak gösterir. Bu, bağlamsal konuşmaları gözden geçirmenizi ve dışarı aktarmanız için olanak sağlar.

  ![Konuşma gözden geçirme kümesi.](../media/ConversationRSOptions.PNG)

Aşağıdaki bölümlerde, konuşmaları gözden geçirme ve dışarı aktarma açıklanmaktadır.

### <a name="reviewing-conversations"></a>Konuşmaları gözden geçirme

Gözden geçirme kümesinde, gözden geçirme işlemini kolaylaştırmak için aşağıdaki seçenekleri kullanabilirsiniz.

- **Konuşmaya göre grupla:** Aynı konuşma içindeki iletileri, kullanıcıların gözden geçirme sürecini basitleştirmelerine ve kolaylaştırmalarına yardımcı olmak için grup halinde gruptur.

- **Özet görünümü:** Dizili konuşmayı görüntüler. Bu görünümde, konuşmanın tamamını görebilir ve her iletinin meta verilerine erişebilirsiniz.

   - Tek tek iletilerin meta verilerini görüntüleme

   - Tek tek iletileri indirme

- **Metin görünümü:** Tüm konuşma için ayıklanan metni sağlar.

- **Ek Açıklama görünümü:** Konuşmanın zincirleme görünümünü işaretlemenizi sağlar. Konuşmada yer alan tüm iletiler aynı açıklamalı belgeyi paylaşır.

- **Etiketleme:** Bir gözden geçirme kümesinde konuşmaları görüntülerken, Kodlama panelinde Etiketleme **paneline tıklayarak etiketleri görüntüleyebilirsiniz** ve uygulayabilirsiniz.

- **Konuşma dönüştürmeyi yeniden çalıştırma:** İletiler konuşma gözden geçirme kümesine eklenmiştir ve bu konuşma özetini oluşturmak ve ek açıklama görünümlerini oluşturmak için otomatik olarak bir dönüştürme işi çalışır. Konuşma Görevi Başarısız Olursa, gözden geçirme kümesinde Eylem Pdf'leri oluşturma'ya **>** bu işi yeniden çalıştırabilirsiniz.

### <a name="exporting-conversations"></a>Konuşmaları dışarı aktarma

Gözden geçirme kümesinden konuşmaları dışarı aktararak seçebilirsiniz seçenekler için bkz. [Gözden geçirme kümesinden belgeleri dışarı aktarma](export-documents-from-review-set.md#export-options).

Özel olarak, sohbet konuşmaların tamamını tek bir PDF dosyasında dışarı aktarabilirsiniz veya bir konuşmada yer alan her sohbet mesajını tek bir dosya olarak dışarı aktarabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

Aynı dosyada büyük/yeni olay verilerini gözden geçirme hakkında Advanced eDiscovery aşağıdaki makalelere bakın:

- [Gözden geçirme kümesinde içeriği sorgulama ve filtreleme](review-set-search.md)
- [Gözden geçirme kümesinde belgeleri etiketleme](tagging-documents.md)
- [Vaka verilerini görüntüleme](view-documents-in-review-set.md)
- [Vaka verilerini çözümleme](analyzing-data-in-review-set.md)
- [Vaka verilerini dışarı aktarma](exporting-data-ediscover20.md)
