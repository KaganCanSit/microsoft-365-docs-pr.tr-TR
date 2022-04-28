---
title: gözden geçirme kümesindeki içeriği sorgulama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft Purview eKeşif (Premium) durumunda daha verimli bir inceleme için içeriği düzenlemek üzere bir gözden geçirme kümesinde sorgu oluşturmayı ve çalıştırmayı öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 44f4b9d6aed92a6593f5c6c70322656e4c770c3d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090927"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Bir inceleme setindeki içeriği sorgulama ve filtreleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Çoğu durumda, bir inceleme kümesindeki içeriği daha ayrıntılı incelemek ve daha verimli bir gözden geçirmeyi kolaylaştırmak için düzenlemek yararlı olacaktır. Gözden geçirme kümesinde filtreleri ve sorguları kullanmak, gözden geçirme ölçütlerinizi karşılayan belgelerin bir alt kümesine odaklanmanıza yardımcı olur.

## <a name="default-filters"></a>Varsayılan filtreler

Bir gözden geçirme kümesinde, gözden geçirme kümesinde önceden yüklenmiş beş varsayılan filtre vardır:

- Anahtar kelime -ler
- Tarih
- Gönderen/Yazar
- Konu/Başlık
- Etiketler

![Varsayılan filtre türleri.](../media/DefaultFilterTypes.png)

Her filtreyi tıklayarak genişletin ve bir değer atayın. Filtreyi gözden geçirme kümesine otomatik olarak uygulamak için filtrenin dışına tıklayın. Aşağıdaki ekran görüntüsünde, bir tarih aralığındaki belgeleri göstermek için yapılandırılmış Tarih filtresi gösterilmektedir.

![Varsayılan filtre genişletildi.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Filtre ekleme veya kaldırma

Gözden geçirme kümesinde görüntülenen filtreleri eklemek veya kaldırmak için **Filtreler'i** seçerek açılır sayfada görüntülenen filtre panelini açın. 

![Filtre paneli.](../media/FilterPanel.png)

Kullanılabilir filtreler dört bölümde düzenlenmiştir:

- **Arama**: Farklı arama özellikleri sağlayan filtreler.

- **Analiz & tahmine dayalı kodlama**: **Belge & e-posta analizi** işini çalıştırdığınızda veya tahmine dayalı kodlama modelleri kullandığınızda oluşturulan ve belgelere eklenen özelliklere yönelik filtreler.

- **Kimlikler**: Belgelerin tüm kimlik özellikleri için filtreler.

- **Öğe özellikleri**: Belge özellikleri için filtreler. 

Her bölümü genişletin ve filtre kümesine eklemek veya kaldırmak için filtreleri seçin veya seçimini kaldırın. Filtre eklediğinizde, filtre kümesinde görüntülenir. 

![Filtre panelindeki filtre bölümlerinin ve özelliklerin listesi.](../media/FilterPanel2.png)

> [!NOTE]
> Filtre panelinde bir bölümü genişlettiğinizde, varsayılan filtre türlerinin seçili olduğunu fark edersiniz. Bunların seçili kalmasını sağlayabilir veya bunların seçimini kaldırıp filtre kümesinden kaldırabilirsiniz. 

## <a name="filter-types"></a>Filtre türleri

Gözden geçirme kümesindeki aranabilir her alanın, belirli bir alana göre öğeleri filtrelemek için kullanabileceğiniz bir filtresi vardır.

Birden çok filtre türü vardır:

- **Serbest metin**: "Konu" gibi metin alanlarına serbest metin filtresi uygulanır. Birden çok arama terimlerini virgülle ayırarak listeleyebilirsiniz.

- **Tarih**: "Son değiştirme tarihi" gibi tarih alanları için tarih filtresi kullanılır.

- **Arama seçenekleri**: Arama seçenekleri filtresi, incelemedeki belirli alanlar için olası değerlerin listesini (her değer seçebileceğiniz bir onay kutusuyla görüntülenir) sağlar. Bu filtre, gözden geçirme kümesinde sınırlı sayıda olası değerin bulunduğu "Gönderen" gibi alanlar için kullanılır.

- **Anahtar sözcük**: Anahtar sözcük koşulu, terimleri aramak için kullanabileceğiniz belirli bir serbest metin koşulu örneğidir. Bu filtre türünde KQL benzeri sorgu dilini de kullanabilirsiniz. Daha fazla bilgi için bu makaledeki Sorgu dili ve Gelişmiş sorgu oluşturucu bölümlerine bakın.

## <a name="include-and-exclude-filter-relationships"></a>Filtre ilişkilerini dahil et ve hariç tut

Belirli bir filtre için ekleme ve dışlama ilişkisini değiştirebilirsiniz. Örneğin, Etiket filtresinde, açılan filtrede **Eşittir hiçbiri'ni** seçerek belirli bir etiketle etiketlenen öğeleri dışlayabilirsiniz. 

![Etiket filtrelerini hariç tut.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Filtreleri sorgu olarak kaydetme

Filtrelerinizi tamamladıktan sonra, filtre bileşimini bir filtre sorgusu olarak kaydedebilirsiniz. Bu, filtreyi sonraki gözden geçirme oturumlarında uygulamanıza olanak tanır.

Bir filtreyi kaydetmek için **Sorguyu kaydet'i** seçin ve adlandırın. Siz veya diğer gözden geçirenler **, Kaydedilmiş filtre sorguları** açılan listesini seçip ayarlanmış belgeleri gözden geçirmek için uygulanacak bir filtre sorgusu seçerek önceden kaydedilmiş filtre sorgularını çalıştırabilirsiniz. 

![Filtre sorgusunu kaydedin.](../media/SaveFilterQuery.png)

Filtre sorgusunu silmek için filtre panelini açın ve sorgunun yanındaki çöp kutusu simgesini seçin.

![Filtre sorgusunu silin.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Sorgu dili

Filtreleri kullanmaya ek olarak, anahtar sözcükler filtresinde KQL benzeri bir sorgu dili kullanarak gözden geçirme kümesi arama sorgunuzu oluşturabilirsiniz. Gözden geçirme kümesi sorgularının sorgu dili **AND**, **OR**, **NOT** ve **NEAR** gibi standart Boole işleçlerini destekler. Ayrıca tek karakterli joker karakteri (?) ve çok karakterli joker karakteri (*) destekler.

## <a name="advanced-query-builder"></a>Gelişmiş sorgu oluşturucusu

Ayrıca, bir gözden geçirme kümesindeki belgeleri aramak için daha gelişmiş sorgular oluşturabilirsiniz.

1. Filtre panelini açın, **Filtreler'i** seçin ve **Arama** bölümünü genişletin.

  ![KQL filtresi ekleyin.](../media/AddKQLFilter.png)

2. **KQL** filtresini seçin ve **Sorgu oluşturucusunu aç'a** tıklayın.

   Bu panelde, sorgu oluşturucusunu kullanarak karmaşık KQL sorgular oluşturabilirsiniz. **AND** veya **OR** ilişkileri tarafından mantıksal olarak bağlanan birden çok koşuldan oluşan koşullar veya koşul grupları ekleyebilirsiniz.

   ![Karmaşık filtre sorgularını yapılandırmak için sorgu oluşturucusunu kullanın.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Kısmen dizine alınan öğeleri filtreleme

Taslak koleksiyonu bir gözden geçirme kümesine işlediğiniz sırada ek veri kaynaklarından kısmen dizinlenmiş öğeler ekleme seçeneğini belirlediyseniz. Bir öğenin araştırmanızla ilgili olup olmadığını ve öğenin kısmen dizine alınmasına neden olan hatayı düzeltmeniz gerekip gerekmediğini belirlemek için bu öğeleri tanımlamak ve görüntülemek isteyebilirsiniz.

Şu anda, bir gözden geçirme kümesinde kısmen dizine alınan öğeleri görüntülemek için bir filtre seçeneği yoktur. Ama üzerinde çalışıyoruz. O zamana kadar, bir gözden geçirme kümesine eklediğiniz kısmen dizinlenmiş öğeleri filtrelemenin ve görüntülemenin bir yolu aşağıdadır.

1. Bir koleksiyon oluşturun ve ek veri kaynaklarından kısmen dizinlenmiş öğeler *eklemeden* yeni bir gözden geçirme kümesine işleyin.

2. 1. adımdaki koleksiyonu kopyalayarak yeni bir koleksiyon oluşturun.

3. Yeni koleksiyonu aynı gözden geçirme kümesine işleyin. Ancak bu kez, ek veri kaynaklarından kısmen dizine alınan öğeleri ekleyin. 1. adımda oluşturduğunuz koleksiyondaki öğeler gözden geçirme kümesine zaten eklendiğinden, gözden geçirme kümesine yalnızca ikinci koleksiyondan kısmen dizine alınmış öğeler eklenir.

4. Her iki koleksiyon da gözden geçirme kümesine eklendikten sonra gözden geçirme kümesine gidin ve **YönetYükleme kümeleri'ni** >  seçin.

5. İkinci koleksiyonun (2. adımda oluşturduğunuz **) Load Id** değerini kopyalayın veya not edin. Koleksiyon adı **Kaynak bilgileri** sütununda tanımlanır.

6. Gözden geçirme kümesine geri dönün, **Filtre'ye** tıklayın, **Kimlikler** bölümünü genişletin ve ardından **Yük Kimliği** onay kutusunu seçin.

7. **Yük Kimliği** filtresini genişletin ve sonra kısmen dizine alınan öğeleri görüntülemek için ikinci koleksiyona karşılık gelen yük kimliğinin onay kutusunu seçin.
