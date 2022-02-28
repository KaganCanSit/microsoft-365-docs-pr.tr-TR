---
title: Gözden geçirme kümesinde belgeleri etiketleme
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
description: Gözden geçirme kümesinde belgeleri etiketlemek, gereksiz içeriği kaldırmaya ve bir e-posta durumunda uygun Advanced eDiscovery olur.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 43b0bf42bcd94f0bc3ade169ee5b41ee33dcbc5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985009"
---
# <a name="tag-documents-in-a-review-set-in-advanced-ediscovery"></a>Belgeleri belge kümesinde bir gözden geçirme kümesinde Advanced eDiscovery

Gözden geçirme kümesinde içerik düzenlemek, eBulma sürecindeki çeşitli iş akışlarını tamamlamak önemlidir. Bu şunları içerir:

- Gereksiz içeriği bir hale alma

- İlgili içeriği tanımlama

- Uzman veya avukat tarafından gözden geçirmesi gereken içeriği tanımlama

Uzmanlar, avukatlar veya diğer kullanıcılar bir inceleme kümesinde içeriği gözden geçir yaptıklarında, içerikle ilgili görüşlerini etiketler kullanılarak yakalanabilirsiniz. Örneğin, amacı gereksiz içeriği bir yere vermekse, kullanıcı belgeleri "yanıt vermiyor" gibi bir etiketle etiketlsin. İçerik gözden geçirildikten ve etiketlendikten sonra, "yanıt vermiyor" olarak etiketlenen içerikleri dışarıda tutmak için bir gözden geçirme kümesi araması oluşturulabilir. Bu işlem, eBulma iş akışının sonraki adımlarından yanıtlanmayan içeriği ortadan kaldırıyor. Bir gözden geçirme kümesinde etiketleme paneli, her durum için özelleştirilebilir ve böylece etiketler dava için hedeflenen gözden geçirme iş akışını destekler.

> [!NOTE]
> Etiketlerin kapsamı önemli bir Advanced eDiscovery durum olur. Bu, bir davanın gözden geçirenlerin gözden geçirme kümesi belgelerini etiketlemek için kullanabileceği tek bir etiket kümesine sahip olduğu anlamına gelir. Aynı durumda, farklı gözden geçirme kümelarında kullanmak üzere farklı bir etiket kümesi ayaramazsiniz.

## <a name="tag-types"></a>Etiket türleri

Advanced eDiscovery iki tür etiket sağlar:

- **Tek seçim etiketleri**: Gözden geçirenlerin grup içindeki tek bir etiketi seçmelerini kısıtlar. Bu tür etiketler, gözden geçirenlerin "yanıt veren" ve "yanıt vermiyor" gibi çakışan etiketleri seçmeylerini sağlamak için yararlı olabilir. Tek seçim etiketleri radyo düğmeleri olarak görünür.

- **Çoklu seçim etiketleri**: Incelemelerin grup içinde birden çok etiket seçmesine izin ver. Bu tür etiketler onay kutuları olarak görünür.

## <a name="tag-structure"></a>Etiket yapısı

Etiket türlerine ek olarak, etiket belgelerini daha kolay etiketlemek için etiket panelinde etiketlerin nasıl düzenleniyor olması da kullanılabilir. Etiketler bölümlere göre gruplanmıştır. Gözden Geçirme kümesi araması, etikete göre ve etiket bölümüne göre arama yapma olanağını destekler. Bu, bölümdeki herhangi bir etiketle etiketlenmiş belgeleri almak için bir gözden geçirme kümesi araması oluşturabilirsiniz.

![Etiket panelinde etiket bölümleri.](../media/TagTypes.png)

Etiketleri bir bölümün içine yerleştirmeyi daha da düzenleyebilirsiniz. Örneğin, amacı ayrıcalıklı içeriği tanımlamak ve etiketlemek ise, gözden geçirenin bir belgeyi "Ayrıcalıklı" olarak etiketley kimliğini açıkça ifade etmek ve uygun iç içe etikete bakarak ayrıcalık türünü seçmeyi belirlemek için iç içe yerleştirme kullanılabilir.

![Etiket bölümü içinde iç içe etiketler.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Etiketleri oluşturma ve uygulama

Gözden geçirme kümeleri içinde öğeleri etiketleme, iki adımlı bir işlemdir. İlk adım, ayarlanmış öğeleri gözden geçirmek için uygulanan etiketleri oluşturmaktır. Etiketleri oluşturdukktan sonra, siz ve diğer gözden geçirenler bunları gözden geçirme kümesinde öğelere uygulayabilirsiniz. Daha önce de Advanced eDiscovery da Advanced eDiscovery gözden geçirenlerin gözden geçirme kümesi öğelerini etiketlemek için kullanabileceği tek bir etiket kümesi olabilir.

### <a name="create-tags"></a>Etiket oluşturma

Gözden geçirme kümesinde öğelere etiket uygulamadan önce, etiket yapısı oluşturmanız gerekir.

1. Gözden geçirme kümesi açın, komut çubuğuna gidin ve Etiket **dosyaları'na gidin**.

2. Etiket dosyaları **uç sayfasında** Etiket oluştur **/düzenle'ye tıklayın**.

   ![Çıkış sayfasında Etiket oluştur/düzenle'ye tıklayın.](../media/CreateAeDTags1.png)

3. Etiketler sayfasında **Bölüm** **ekle'yi seçin**.

4. Etiket grubu başlığını ve isteğe bağlı bir açıklama yazın, sonra Da **Kaydetme'ye tıklayın**.

5. Etiket grubu başlığının yanındaki üç nokta açılır menüsünü seçin ve Ekle onay kutusuna **veya Seçenek ekle** **düğmesine tıklayın**.

6. Onay kutusu veya seçenek düğmesi için bir ad ve açıklama yazın.

7. Yeni etiket bölümleri, etiket seçenekleri ve onay kutuları oluşturmak için bu işlemi yineler. Örneğin, aşağıdaki ekran görüntüsünde Yanıt veren ve Yanıt vermiyor onay kutulerinden oluşan Gözden Geçir  **adlı bir etiket** grubu yer almaktadır.

   ![Etiket yapısını yapılandırma.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Etiket uygulama

Etiket yapısı yerindeken, gözden geçirenler etiketleme ayarlarını yapılandırarak gözden geçirme kümesinde öğelere etiketler uygulayabilir.

1. Gözden geçirme kümesi komut çubuğunda **Etiket dosyaları öğesini** seçerek Etiket dosyaları uç  sayfası (etiketleme paneli olarak *da denir) görüntülenir*.

   ![Etiketleme panelini açmak için komut çubuğundaKimlik dosyaları'na tıklayın.](../media/TagFilesFlyoutPage.png)

2. Etiket **dosyaları uç** sayfasında, aşağıdaki seçenekleri ayarp gözden geçirme kümesinde görüntülenen öğelerin nasıl etiket olaylarını etiketley onu yapılandırabilirsiniz. Şu anda gözden geçirme kümesine uygulanan filtreler veya filtre sorguları hangi öğelerin görüntüleniyor olduğunu ve dolayısıyla etiketleri uygulayabilecek öğeleri belirler. Daha fazla bilgi için bkz [. Gözden geçirme kümesinde içeriği sorgulama ve filtreleme](review-set-search.md).

   - **Seçim'i seçin**. Etiketlerin uygulanacak öğe kapsamını belirlemek için aşağıdaki seçeneklerden birini seçin.

      - **Seçili öğeleri etiketleme**: Bu seçenek, seçtiğiniz öğelere etiketleri uygular. Etiketleme panelini başlatmadan önce veya başlattıktan sonra öğeleri seçin. Bu seçenek etiketilecek seçili öğelerin sayısını görüntüler (gerçek zamanlı olarak).

      - **Tüm öğeleri etiketle**: Bu seçenek, gözden geçirme kümesinde görüntülenen tüm öğelere etiketleri uygular. Bu seçenek etiketlenen öğelerin toplam sayısını görüntüler.

   - **Seçimi genişletme**: Gözden geçirme kümesinde etiketlenmiş öğelerle ilgili ek öğeleri etiketlemek için aşağıdaki seçenekleri kullanın.

      - **İlişkili aile öğelerini** ekle: Bu seçenek, etiketlenmiş öğelerin ilişkili aile öğelerine aynı etiketi uygular.  *Aile öğeleri* , aynı FamilyId meta veri özellik **değerini paylaşan** öğelerdir. Örneğin, bir e-posta iletisine eklenmiş olan belge, e-posta iletisiyle aynı **FamilyId'i** paylaşıyor. Dolayısıyla, bu örnekte bu seçenek seçiliyse, belge gözden geçirme kümesi öğeleri listesine eklense bile e-posta iletisi ve belge etiketlenir.

      - **İlişkili konuşma öğelerini** dahil et: Bu seçenek, aynı konuşmada veya konuşmada etiketlenen Teams veya Yammer konuşmadaki tüm öğelere aynı etiketi uygular. *Konuşma öğeleri* , aynı ConversationId meta veri özellik **değerini paylaşan** öğelerdir. Konuşmanın tüm iletileri, gönderileri ve bunların döküm dosyası aynı **ConversationId'i paylaşır**. Bu seçenek işaretliyse, bu konuşma öğelerinin bazıları gözden geçirme kümesi öğeleri listesine eklense bile, aynı konuşmadaki (ve döküm dosyasındaki) tüm öğeler etiketlenir. Konuşma öğeleri hakkında daha fazla bilgi için, İş Akışı'nda içerik [için Advanced eDiscovery "Gruplama" Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Yok**: Bu seçenek aile öğelerine veya konuşma öğelerine etiket uygulamaz. Yalnızca seçilen öğelere veya gözden geçirme kümesi listesinde yer alan tüm öğelere etiketler uygulanır.

   > [!NOTE]
   > İlişkili aile veya görüşme öğeleri dahil olmak üzere, Seçili öğeleri etiketle veya Liste  seçeneklerinde Tüm öğeleri etiketle **seçeneklerinde gösterilen öğelerin sayısı değişmez**. Başka bir deyişle, etiketlenen öğe sayısı görüntülenmez.

   - **Etiket atama**: Bu bölümde, belgelere uygulayabilecek etiketleri (etiket gruplarına göre düzenlenmiş) görüntüler. Her etiket grubuna tek bir seçim etiketi (radyo düğmesiyle tanımlanır) uygulayabilirsiniz. Bununla birlikte, birden çok seçimli etiket (onay kutusuyla tanımlanır) uygulayabilirsiniz.

3. Etiketleri **ayarlarınıza** göre uygulamak için Etiket uygula'ya tıklayın.

   Etiketleme **panelindeki** her etiket grubu için Etiket uygulama durumu iletisi görüntülendiğinde bir etiketleme işinin başlatılmaktadır. Etiket atama bölümündeki her etiket **grubunun** etiketleri, iş tamamlanana kadar gri gösterilir.

> [!TIP]
> Etiketleme panelinde ayarları yapılandırma sürecindeyseniz, ancak en baştan başlamak istiyorsanız, geçerli ayarı temizlemek için Etiket atamasını sıfırla'ya tıklayın. Bu denetim, zaten etiketlenmiş öğelere yönelik değildir ve daha önce etiketlenmiş öğelerdeki etiketleri değiştirmez veya kaldırmaz.  

#### <a name="monitor-tagging-jobs"></a>İşleri etiketlemeyi izleme

Çok fazla sayıda öğe etiketlerseniz (veya Tüm öğeleri liste olarak etiketle **) seçeneğini** belirlerseniz, **Belge etiketleme** işi oluşturulur. Bu işin durumunu, olayda **İş sekmesinde** görüntülersiniz. Bu, tamamlanması çok uzun zaman al götüren büyük etiketleme işlerini takip etmenizi sağlar. Bazı durumlarda bir etiketleme işi tamamlanmıştır, ancak etiketleme **panelinde** etiketlerin uygulanması durumu iletisi yine görüntülenir. Etiketleme işlerinin durumunu güncelleştirmek için gözden geçirme **kümesi komut** çubuğunda Yenile'ye tıklayın.

## <a name="removing-tags"></a>Etiketleri kaldırma

Gözden geçirme kümesinde öğelerden etiketleri kaldırabilirsiniz. Bununla birlikte, gözden geçirme kümesi öğesine uygulanmış olan tek seçimli etiketi kaldıramazsiniz. Tek seçimli etiketi yalnızca aynı etiket grubunda tek seçimli başka bir etiketle değiştirebilirsiniz.

Etiketi kaldırmak için:

1. Etiketi kaldırmak istediğiniz öğeleri seçin.

2. Etiketleme **panelini** görüntülemek için Etiket dosyaları'nı tıklatın.

3. Etiket **atama altında**, etiketin seçimini kaldırın ve Etiket **uygula'ya tıklayın**.

Seçili öğelere uygulanan etiketi değiştirmek için önceki yordamı da kullanabilirsiniz. Geçerli etiketin seçimini kaldırdikten sonra farklı bir etiket de kaldırabilirsiniz.
