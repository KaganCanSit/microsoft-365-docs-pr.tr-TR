---
title: Bir inceleme setindeki belgeleri etiketleme
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
description: Gözden geçirme kümesindeki belgeleri etiketlemek, gereksiz içeriğin kaldırılmasına ve eBulma (Premium) durumunda ilgili içeriğin tanımlanmasına yardımcı olur.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 2cd1243f520be21cf27c810a5f2dc2e4a033a33f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623749"
---
# <a name="tag-documents-in-a-review-set-in-ediscovery-premium"></a>eBulma'da (Premium) bir gözden geçirme kümesinde belgeleri etiketleme

Bir gözden geçirme kümesindeki içeriği düzenlemek, eBulma işleminde çeşitli iş akışlarını tamamlamak için önemlidir. Buna şunlar dahildir:

- Gereksiz içeriği itlaf etmek

- İlgili içeriği tanımlama

- Bir uzman veya avukat tarafından gözden geçirilmesi gereken içeriği belirleme

Uzmanlar, avukatlar veya diğer kullanıcılar bir inceleme kümesindeki içeriği gözden geçirdiğinde, içerikle ilgili görüşleri etiketler kullanılarak yakalanabilir. Örneğin, amaç gereksiz içeriği geçersiz kılmasıysa, kullanıcı belgeleri "yanıt vermeyen" gibi bir etiketle etiketleyebilir. İçerik gözden geçirilip etiketlendikten sonra, "yanıt vermeyen" olarak etiketlenen tüm içerikleri dışlamak için bir gözden geçirme kümesi araması oluşturulabilir. Bu işlem, eBulma iş akışındaki sonraki adımlarda yanıt vermeyen içeriği ortadan kaldırır. Bir inceleme kümesindeki etiketleme paneli, etiketlerin servis talebi için hedeflenen gözden geçirme iş akışını desteklemesi için her servis talebi için özelleştirilebilir.

> [!NOTE]
> Etiketlerin kapsamı bir eBulma (Premium) olayıdır. Bu, bir servis talebinin gözden geçirenlerin gözden geçirme kümesi belgelerini etiketlemek için kullanabileceği tek bir etiket kümesine sahip olabileceği anlamına gelir. Aynı durumda farklı gözden geçirme kümelerinde kullanmak üzere farklı bir etiket kümesi ayarlayamazsınız.

## <a name="tag-types"></a>Etiket türleri

eBulma (Premium) iki tür etiket sağlar:

- **Tek seçimli etiketler**: Gözden geçirenleri bir grup içinde tek bir etiket seçmeye kısıtlar. Bu tür etiketler, gözden geçirenlerin "duyarlı" ve "yanıt vermeyen" gibi çakışan etiketleri seçmediğinden emin olmak için yararlı olabilir. Tek seçenekli etiketler radyo düğmeleri olarak görünür.

- **Çoktan seçmeli etiketler**: Gözden geçirmelerin bir grup içinde birden çok etiket seçmesine izin verin. Bu etiket türleri onay kutuları olarak görünür.

## <a name="tag-structure"></a>Etiket yapısı

Etiket türlerine ek olarak, etiketlerin etiket panelinde düzenlenme şekli, etiketleme belgelerini daha sezgisel hale getirmek için kullanılabilir. Etiketler bölümlere göre gruplandırılır. Gözden geçirme kümesi araması, etikete ve etiket bölümüne göre arama özelliğini destekler. Bu, bir bölümdeki herhangi bir etiketle etiketlenmiş belgeleri almak için bir gözden geçirme kümesi araması oluşturabileceğiniz anlamına gelir.

![Etiket panelinde bölümleri etiketleyin.](../media/TagTypes.png)

Etiketleri bir bölüm içinde iç içe yerleştirerek daha fazla düzenleyebilirsiniz. Örneğin, amaç ayrıcalıklı içeriği tanımlamak ve etiketlemekse, iç içe yerleştirme, gözden geçirenin bir belgeyi "Privileged" olarak etiketleyip uygun iç içe etiketi denetleyerek ayrıcalık türünü seçebileceğini açıkça ifade etmek için kullanılabilir.

![Bir etiket bölümü içinde iç içe yerleştirilmiş etiketler.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Etiket oluşturma ve uygulama

Gözden geçirme kümelerindeki öğeleri etiketlemek iki adımlı bir işlemdir. İlk adım, daha sonra küme öğelerini gözden geçirmek için uygulanan etiketleri oluşturmaktır. Etiketleri oluşturduktan sonra, siz ve diğer gözden geçirenler bunları bir gözden geçirme kümesindeki öğelere uygulayabilirsiniz. Daha önce açıklandığı gibi, bir eBulma (Premium) olayı gözden geçirenlerin gözden geçirme kümesi öğelerini etiketlemek için kullanabileceği tek bir etiket kümesine sahip olabilir.

### <a name="create-tags"></a>Etiket oluşturma

Bir gözden geçirme kümesindeki öğelere etiket uygulamadan önce bir etiket yapısı oluşturmanız gerekir.

1. Bir gözden geçirme kümesi açın, komut çubuğuna gidin ve **Dosyaları etiketle'yi** seçin.

2. **Etiket dosyaları** açılır sayfasında **Etiket oluştur/düzenle'ye** tıklayın.

   ![Açılır sayfada Etiket oluştur/düzenle'ye tıklayın.](../media/CreateAeDTags1.png)

3. **Etiketler** sayfasında **Bölüm ekle'yi** seçin.

4. Bir etiket grubu başlığı ve isteğe bağlı bir açıklama yazıp **Kaydet'e** tıklayın.

5. Etiket grubu başlığının yanındaki üç nokta açılan menüsünü seçin ve **Ekle onay kutusuna** veya **Seçenek ekle düğmesine** tıklayın.

6. Onay kutusu veya seçenek düğmesi için bir ad ve açıklama yazın.

7. Yeni etiket bölümleri, etiket seçenekleri ve onay kutuları oluşturmak için bu işlemi yineleyin. Örneğin, aşağıdaki ekran görüntüsünde **Duyarlı ve Yanıt vermeyen** onay kutularından oluşan **Gözden Geçir** adlı bir  etiket grubu gösterilmektedir.

   ![Etiket yapısını yapılandırın.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Etiketleri uygulama

Etiket yapısı uygulandığında, gözden geçirenler etiketleme ayarlarını yapılandırarak bir gözden geçirme kümesindeki öğelere etiket uygulayabilir.

1. Gözden geçirme kümesi komut çubuğunda **Etiket dosyaları** açılır sayfasını (*etiketleme paneli* olarak da adlandırılır) görüntülemek için **Etiket dosyaları'nı** seçin.

   ![Etiketleme panelini açmak için komut çubuğunda Dosyaları etiketle'ye tıklayın.](../media/TagFilesFlyoutPage.png)

2. **Dosyaları etiketle** açılır sayfasında, gözden geçirme kümesinde görüntülenen öğelerin nasıl etiketleneceğini yapılandırmak için aşağıdaki seçenekleri ayarlayabilirsiniz. Şu anda gözden geçirme kümesine uygulanan filtreler veya filtre sorguları hangi öğelerin görüntüleneceğini ve dolayısıyla etiketleri uygulayabileceğiniz öğeleri belirler. Daha fazla bilgi için bkz. [Gözden geçirme kümesindeki içeriği sorgulama ve filtreleme](review-set-search.md).

   - **Seçimi seçin**. Etiketlerin uygulanacağı öğelerin kapsamını belirlemek için aşağıdaki seçeneklerden birini belirleyin.

      - **Seçili öğeleri etiketle**: Bu seçenek, etiketleri seçtiğiniz öğelere uygular. Etiketleme panelini başlatmadan önce veya sonra öğeleri seçebilirsiniz. Bu seçenek, etiketlenecek seçili öğelerin sayısını (gerçek zamanlı olarak) görüntüler.

      - **Listedeki tüm öğeleri etiketle**: Bu seçenek, etiketleri gözden geçirme kümesinde görüntülenen tüm öğelere uygular. Bu seçenek, etiketlenecek öğelerin toplam sayısını görüntüler.

   - **Seçimi genişlet**: Gözden geçirme kümesindeki etiketli öğelerle ilgili ek öğeleri etiketlemek için aşağıdaki seçenekleri kullanın.

      - **İlişkili aile öğelerini dahil et**: Bu seçenek, etiketlenmiş öğelerin ilişkili aile öğelerine aynı etiketi uygular.  *Aile öğeleri* , aynı **FamilyId** meta veri özelliği değerini paylaşan öğelerdir. Örneğin, e-posta iletisine eklenmiş bir belge, e-posta iletisiyle aynı **FamilyId** değerini paylaşır. Bu nedenle, bu örnek için bu seçenek belirlenmişse, belge gözden geçirme kümesi öğeleri listesine eklenmese bile e-posta iletisi ve belge etiketlenir.

      - **İlişkili konuşma öğelerini ekle**: Bu seçenek, etiketlenen öğelerle aynı Teams veya Yammer konuşmasında yer alan tüm öğelere aynı etiketi uygular. *Konuşma öğeleri* , aynı **ConversationId** meta veri özelliği değerini paylaşan öğelerdir. Konuşmanın tüm iletileri, gönderileri ve ilgili transkript dosyası aynı **ConversationId değerini** paylaşır. Bu seçenek belirlenirse, aynı konuşmadaki (ve transkript dosyasındaki) tüm öğeler etiketlenir, ancak bu konuşma öğelerinin bazıları gözden geçirme kümesi öğeleri listesine eklenmeyebilir. Konuşma öğeleri hakkında daha fazla bilgi [için Microsoft Teams'deki içerik için eKeşif (Premium) iş akışının](teams-workflow-in-advanced-ediscovery.md#grouping) "Gruplandırma" bölümüne bakın.

      - **Hiçbiri**: Bu seçenek, aile öğelerine veya konuşma öğelerine etiket uygulamaz. Etiketleri yalnızca seçili öğelere veya gözden geçirme kümesi listesindeki tüm öğelere uygular.

   > [!NOTE]
   > İlişkili aile veya konuşma öğeleri dahil olmak, **Seçili öğeleri etiketleme** veya Liste seçeneklerindeki **tüm öğeleri etiketleme** bölümünde gösterilen öğelerin sayısını değiştirmez. Başka bir deyişle, etiketlenecek ilişkili öğelerin sayısı görüntülenmez.

   - **Etiket atama**: Bu bölümde, belgelere uygulayabileceğiniz etiketler (etiket gruplarına göre düzenlenmiş) görüntülenir. Etiket grubu başına yalnızca bir tek seçenekli etiket (radyo düğmesiyle tanımlanır) uygulayabilirsiniz. Bununla birlikte, birden çok çok seçenekli etiket uygulayabilirsiniz (onay kutusuyla tanımlanır).

3. Etiketleri ayarlarınıza göre uygulamak için Etiketleri **uygula'ya** tıklayın.

   **Etiketleme işinin** başlatıldığını belirtmek üzere etiketleme panelindeki her etiket grubu için Etiket uygulama durum iletisi görüntülenir. İş tamamlanana kadar **Etiket ata** bölümündeki her etiket grubunun etiketleri gri olur.

> [!TIP]
> Etiketleme panelinde ayarları yapılandırma aşamasındaysanız ancak baştan başlamak istiyorsanız Geçerli ayarı temizlemek için **Etiket atamasını sıfırla'ya** tıklayın. Bu denetim zaten etiketlenmiş öğeler için geçerli değildir ve daha önce etiketlenmiş öğelerdeki etiketleri değiştirmez veya kaldırmaz.  

#### <a name="monitor-tagging-jobs"></a>Etiketleme işlerini izleme

Çok sayıda öğeyi etiketlediğinizde (veya **Listedeki tüm öğeleri etiketle) seçeneğini belirlediğinizde**, **belge etiketleme** işi oluşturulur. Bu işin durumunu servis talebindeki **İşler** sekmesinde görüntülersiniz. Bu, tamamlanması uzun sürebilecek büyük etiketleme işlerini izlemenize yardımcı olur. Bazı durumlarda bir etiketleme işi tamamlanmış olabilir, ancak etiketleme panelinde **Etiket uygulama** durum iletisi görüntülenmeye devam edilir. Etiketleme işlerinin durumunu güncelleştirmek için gözden geçirme kümesi komut çubuğunda **Yenile'ye** tıklayın.

## <a name="removing-tags"></a>Etiketleri kaldırma

Bir gözden geçirme kümesindeki öğelerden etiketleri kaldırabilirsiniz. Ancak, bir gözden geçirme kümesi öğesine uygulanmış olan tek seçenekli etiketi kaldıramazsınız. Tek seçenekli bir etiketi yalnızca aynı etiket grubu içindeki başka bir tek seçenekli etiketle değiştirebilirsiniz.

Etiketi kaldırmak için:

1. Etiketi kaldırmak istediğiniz öğeleri seçin.

2. Etiketleme panelini görüntülemek için **Dosyaları etiketle'ye** tıklayın.

3. **Etiket ata'nın** altında etiketin seçimini kaldırın ve ardından **Etiketleri uygula'ya** tıklayın.

Seçili öğelere uygulanan etiketi değiştirmek için önceki yordamı da kullanabilirsiniz. Geçerli etiketin seçimini kaldırdıktan sonra farklı bir etiket seçebilirsiniz.
