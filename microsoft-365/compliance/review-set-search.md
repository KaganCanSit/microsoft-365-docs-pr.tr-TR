---
title: Gözden geçirme kümesinde içeriği sorgulama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Bir çalışma durumunda daha verimli bir gözden geçirme için içeriği düzenlemek için bir gözden geçirme kümesinde sorguyu nasıl Advanced eDiscovery öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ebcb129241565321297b78072a5d02d173552ee1
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015552"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Gözden geçirme kümesinde içeriği sorgulama ve filtreleme

Çoğu durumda, gözden geçirme kümesinde içeriği daha derinden incelemeniz ve daha verimli bir inceleme için düzenlemeniz yararlı olur. Gözden geçirme kümesinde filtreler ve sorgular kullanmak, gözden geçirmenizin ölçütlerine uyan belgelerin bir alt kümesine odaklanmanıza yardımcı olur.

## <a name="default-filters"></a>Varsayılan filtreler

Bir gözden geçirme kümesinde, gözden geçirme kümesine önceden yüklenmiş beş varsayılan filtre vardır:

- Anahtar Sözcükler
- Tarih
- Gönderen/Yazar
- Konu/Başlık
- Etiketler

![Varsayılan filtre türleri.](../media/DefaultFilterTypes.png)

Genişletmek ve bir değer atamak için her filtreye tıklayın. Filtreyi gözden geçirme kümesine otomatik olarak uygulamak için filtrenin dışına tıklayın. Aşağıdaki ekran görüntüsünde, bir tarih aralığındaki belgeleri gösterecek şekilde yapılandırılmış olan Tarih filtresi görüntülenmiştir.

![Varsayılan filtre genişletildi.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Filtre ekleme veya kaldırma

Gözden geçirme kümesinde görüntülenen filtreleri eklemek veya kaldırmak için, Filtreler'i  seçerek bir açılır sayfada görüntülenen filtre panelini açın. 

![Filtre paneli.](../media/FilterPanel.png)

Kullanılabilir filtreler dört bölümde düzenlenmiştir:

- **Arama**: Farklı arama özellikleri sağlayan filtreler.

- **Çözümleme & kodlaması** kullanır: Belge Ana &-posta analitik işini çalıştırarak veya tahmine **dayalı** kodlama modellerini kullanarak belgelerde oluşturulan ve belgelere eklenen özellikler için filtreler.

- **Kimlikler**: Belgelerin tüm kimlik özellikleri için filtreler.

- **Öğe özellikleri**: Belge özellikleri için filtreler. 

Filtre kümesinde eklemek veya kaldırmak için, her bölümü genişletin ve filtreleri seçin veya seçimleri kaldırın. Filtreyi eklerken, filtre kümesinde görüntülenir. 

![Filtre panelinde filtre bölümlerinin ve özelliklerinin listesi.](../media/FilterPanel2.png)

> [!NOTE]
> Filtre panelinde bir bölümü genişletmişsinizdir; varsayılan filtre türlerinin seçili olduğunu fark edin. Bunları seçili bulundurarak veya seçimlerini kaldırarak filtre kümesinden kaldırılabilirsiniz. 

## <a name="filter-types"></a>Filtre türleri

Gözden geçirme kümesinde aranabilir her alanın, belirli bir alanı temel alan öğeleri filtrelemek için kullanabileceğiniz bir filtresi vardır.

Birden çok filtre türü vardır:

- **Serbest Metin**: "Konu" gibi metin alanlarına serbest metin filtresi uygulanır. Birden çok arama terimlerini virgülle ayırarak liste edebilirsiniz.

- **Tarih**: "Son değiştirme tarihi" gibi tarih alanları için tarih filtresi kullanılır.

- **Arama seçenekleri**: Arama seçenekleri filtresi, gözden geçirmede yer alan belirli alanlar için olası değerlerin listesini sunar (her değer seçebilirsiniz bir onay kutusuyla görüntülenir). Bu filtre, gözden geçirme kümesinde sonlu sayıda olası değer bulunduğu "Gönderen" gibi alanlar için kullanılır.

- **Anahtar** sözcük: Anahtar sözcük koşulu, terimleri aramak için kullanabileceğiniz belirli bir serbest metin koşulu örneğidir. Bu filtre türünde KQL benzer sorgu dilini de kullanabilirsiniz. Daha fazla bilgi için, bu makaledeki Sorgu dili ve Gelişmiş sorgu oluşturucusu bölümlerine bakın.

## <a name="include-and-exclude-filter-relationships"></a>Filtre ilişkilerini dahil etmek ve dışarıda tutmak

Belirli bir filtre için ilişki dahil ve dışlama ilişkisini değiştirebilirsiniz. Örneğin Etiket filtresinde, açılan filtrede Belirli bir etiketle etiketlenen öğelerin dışında tutabilirsiniz. 

![Etiket filtresini dışla.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Filtreleri sorgu olarak kaydetme

Filtrelerden memnun olduktan sonra, filtre bileşimini filtre sorgusu olarak kaydedebilirsiniz. Bu, gelecekte gözden geçirme oturumlarında filtreyi uygulamana olanak sağlar.

Filtreyi kaydetmek için, **Sorguyu kaydet'i seçin** ve adını seçin. Siz veya diğer gözden geçirenler, Kaydedilmiş filtre sorguları açılan listesinden seçim yapan ve  ayarlanmış belgeleri gözden geçirmek için uygulanacak filtre sorgusunu seçerek, önceden kaydedilmiş filtre sorgularını çalıştırabilirsiniz. 

![Filtre sorgusunu kaydetme.](../media/SaveFilterQuery.png)

Filtre sorgusunu silmek için, filtre panelini açın ve sorgunun yanındaki çöp kutusu simgesini seçin.

![Filtre sorgusunu silme.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Sorgu dili

Filtreleri kullanmanın yanı sıra, gözden geçirme kümesi arama sorgusunu oluşturmak için Anahtar Sözcükler filtresinde KQL'ye benzer bir sorgu dili de kullanabilirsiniz. Gözden geçirme kümesi sorgularının sorgu dili, **VE, VEYA**, NOT ve NEAR gibi standart Boole **işleçlerini** **destekler**.  Ayrıca tek karakterli joker karakteri (?) ve çok karakterli joker karakteri (*) destekler.

## <a name="advanced-query-builder"></a>Gelişmiş sorgu oluşturucusu

Ayrıca, gözden geçirme kümesinde belge aramak için daha gelişmiş sorgular da oluşturabilirsiniz.

1. Filtre panelini açın, **Filtreler'i** seçin ve Ara **bölümünü** genişletin.

  ![KQL filtresi ekleyin.](../media/AddKQLFilter.png)

2. **KQL filtresini seçin** ve Sorgu oluşturucusunu **aç'a tıklayın**.

   Bu panelde, sorgu oluşturucusunu kullanarak karmaşık KQL sorguları oluşturabilirsiniz. VE veya VEYA ilişkileriyle mantıksal olarak bağlantılı olan birden çok koşuldan yapılmış koşul **veya koşul** **grupları ekleyebilir** .

   ![Karmaşık filtre sorgularını yapılandırmak için sorgu oluşturucusunu kullanın.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Kısmen dizinelenmiş öğeleri filtreleme

Taslak koleksiyonunu gözden geçirme kümesine kabul ettiyseniz, ek veri kaynaklarından kısmen dizine alınan öğeleri ekleme seçeneğini seçtiyseniz. Bir öğenin araştırmanız ile ilgili olup olmadığını belirlemek ve bu öğeleri görüntülemek ve öğenin kısmen dizine alındı hatasına neden olan hatayı düzeltmek isteyip istemeyebilirsiniz.

Şu anda, gözden geçirme kümesinde kısmen dizinelenmiş öğeleri görüntülemek için bir filtre seçeneği yok. Ancak bunun üzerinde çalışıyoruz. O zamana kadar, burada, gözden geçirme kümesine eklenmiş olan kısmen dizine eklenen öğeleri filtre uygulama ve görüntülemenin bir yolu vardır.

1. Ek veri kaynaklarından kısmen dizine alınan öğeleri eklemeden *bir* koleksiyon oluşturun ve bunu yeni bir gözden geçirme kümesine ayarlayın.

2. 1. adımdan koleksiyonu kopyalayıp yeni bir koleksiyon oluşturun.

3. Yeni koleksiyonu aynı gözden geçirme kümesine işler. Ancak bu kez, ek veri kaynaklarından kısmen dizine alınan öğeleri ekleyin. 1. adımda oluşturduğunuz koleksiyondaki öğeler gözden geçirme kümesine önceden eklendiklerinden, gözden geçirme kümesine yalnızca ikinci koleksiyondaki kısmen dizine eklenen öğeler eklenir.

4. Her iki koleksiyon da gözden geçirme kümesine eklendikten sonra, gözden geçirme kümesine gidin ve **ManageLoad kümelerini** >  **seçin**.

5. İkinci koleksiyonun (2 **.** adımda oluşturduğunuz) Yükleme Kimliği'ne kopyalayın veya not edin. Koleksiyon adı Kaynak bilgi **sütununda tanımlanır** .

6. Gözden geçirme kümesine geri dönerek **Filtre'ye** tıklayın, **Kimlikler** bölümünü genişletin ve Kimlik **Yükle onay** kutusunu seçin.

7. Yükleme **Kimliği filtresini** genişletin ve ardından kısmen dizinelenmiş öğeleri görüntülemek için ikinci koleksiyona karşılık gelen yükleme kimliği onay kutusunu seçin.
