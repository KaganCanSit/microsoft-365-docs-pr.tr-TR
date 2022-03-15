---
title: Microsoft SharePoint Syntex'ta içerik derlemesi kullanarak belgeler oluşturma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft Web Sitesinde içerik derlemesi kullanarak belgeleri ve diğer içerikleri otomatik olarak SharePoint Syntex.
ms.openlocfilehash: 9da2aa91443ffe1dd3bbd632b5284ce8f7622069
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504567"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta içerik derlemesi kullanarak belgeler oluşturma

SharePoint Syntex'i sözleşmeler, iş ifadeleri, hizmet sözleşmeleri, izin mektupları, satış perdeleri ve yazışmalar gibi standart tekrarlanan iş belgelerini otomatik olarak oluşturmanıza yardımcı olmak için kullanabilirsiniz. Tüm bu hataları daha hızlı, daha tutarlı ve hatalara daha az uygun bir şekilde, aynı SharePoint Syntex.

İçerik derlemesi ile, var olan bir belgeyi kullanarak *modern* bir şablon oluşturabilir ve sonra veri kaynağı olarak kendi listelerini veya kullanıcı girişlerini kullanarak otomatik olarak SharePoint yeni içerik oluşturmak için bu şablonu kullanabilirsiniz.

> [!NOTE]
> İçerik derleme özelliklerine erişmek SharePoint Syntex için lisanslı bir kullanıcınız olması gerekir. Ayrıca, bu listeleri yönetmek için SharePoint sahip SharePoint gerekir.

## <a name="create-a-modern-template"></a>Modern şablon oluşturma

Modern bir şablon oluşturmak için bu adımları izleyin.

1. SharePoint belge kitaplığından NewCreate  > **modern şablon'ı seçin**. 
 
   ![Modern şablon oluştur seçeneğinin vurgulu olduğu belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-1.png)

2. Var olan ve modern bir şablon oluşturmak için temel olarak kullanmak istediğiniz bir Word belgesi seçin ve sonra da Aç'ı **seçin**. 
 
   ![Belgeyi seçen karşıya yükleme sayfasının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > Şu anda şablon oluşturmak için yalnızca Word belgelerini (.docx uzantısını) karşıya yükleyebilirsiniz. Upload veya masaüstünüzden Word belgelerini depolar.

3. Belgeyi karşıya yükledikten sonra, belge şablon stüdyoda görüntülenir ve burada belgeyi şablona dönüştürebilirsiniz.
 
   ![Şablon görüntüleyicisinde belgenin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-3.png)

4. Şablon stüdyonun sol üst köşesinde, şablonun adını seçin. Varsayılan ad, şablonu oluşturmak için kullanılan belgenin adıdır. Şablonu yeniden adlandırmak için, varsayılan adı veya adın yanındaki kalem simgesini seçin, yeni adı yazın ve ardından **Enter'ı seçin**.
 
   ![Yeniden adlandırmak için seçen belgenin adını gösteren şablon görüntüleyicinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Kullanıcıların bir belgeden diğerine değiştirmek istemeleri gereken tüm dinamik metinler için yer tutucular oluşturun. Örneğin, şirket adı, müşteri adı, adres, telefon numarası veya tarih gibi girişler için yer tutucu oluşturmak istiyor olabilir.

    Yer tutucu oluşturmak için metni (tarih gibi) seçin. Tüm **yer tutucular** paneli açılır; burada yer tutucuya ilgili bir ad ve yer tutucuyla ilişkilendirmek istediğiniz giriş türünü seçersiniz.
 
   ![Bir alanı vurgulanmış ve Tüm yer tutucular panelini gösteren şablon görüntüleyicinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-4a.png)

   Şu anda, kullanıcıların yer tutucuyu doldurmaları için iki yol vardır:

   - [Metin girme veya tarih seçme](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Liste veya kitaplık sütunundaki seçeneklerden seçme](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

   > [!NOTE]
   > Yalnızca metin için yer tutucular oluşturabilirsiniz. Şu anda resimler, akıllı resimler, tablolar ve madde işareti listeleri desteklenemİ değildir.   

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Metin girerek veya tarih seçerek yer tutucuyu ilişkilendirme 

Tüm yer **tutucular panelinde** :

1. Ad **alanına** , yer tutucu için uygun bir ad girin.

   ![El ile giriş için Tüm yer tutucular panelini gösteren şablon görüntüleyicinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-5.png)

2. Yazarların **bu yer tutucuyu nasıl dolduracakları** bölümünde Metin girin **veya tarih seçin**.

3. Bilgi **türü alanında** , yer tutucuyla ilişkilendirmek istediğiniz veri türünü seçin. Şu anda altı seçenek vardır: **Tek** satır **metin, Birden** çok metin satırı, **Sayı**, **Tarih ve** saat, **E-posta** ve **Köprü**.

4. **Ekle**'yi seçin.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Bir liste veya kitaplığın sütunundaki seçeneklerden seçerek yer tutucuyu ilişkilendirme

Tüm yer **tutucular panelinde** :

1. Ad **alanına** , yer tutucu için uygun bir ad girin.

   ![Şablon listesinden giriş için Tüm yer tutucular panelini gösteren şablon görüntüleyicinin SharePoint görüntüsü.](../media/content-understanding/content-assembly-create-template-6.png)

2. Yazarların **bu yer tutucuyu nasıl dolduracakları** bölümünde, liste veya kitaplık sütununda Seçim seçim'i **ve** ardından Seç'i **seçin**.

3. Kaynak **sütun eklemek için bir liste seçin sayfasında** , kullanmak istediğiniz listeyi seçin ve sonra da Sonraki'yi **seçin**.

   ![Listelerin görüntü olduğu Kaynak sütun eklemek için liste seçin sayfasının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-7.png)

4. Var olan **liste sayfasından bir kaynak sütun seçin** sayfasında, yer tutucuyla ilişkilendirmek istediğiniz sütun adını seçin ve sonra da Kaydet'i **seçin**. 

   ![Var olan liste sayfasından bir kaynak sütun seçin sayfasının sütun adlarını gösteren ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-8.png)

    Listelerin özgün sayfasını yeniden görmek için listenin en **altındaki Git (liste adı)** bağlantısına tıklayın.

5. Bitirebilirsiniz, liste alanı yer tutucuyla ilişkilendirildi.

   ![Yer tutucuyla ilişkilendirilmiş liste alanını gösteren Tüm yer tutucular panelinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-9.png)

6. Kullanıcıların girdileri el ile ekley istemesini, ayrıca listeden seçime ek olarak Yazarların yeni seçim eklemesine **izin ver'i seçin**. Bu durumda, el ile giriş veri türü için varsayılan ayar Tek *metin satırıdır*. Ayrıca, yazarların girişi yalnızca belgeyi oluşturmak için kullanılır. Bunlar yeni liste listene SharePoint.
 
Gerekli olduğunu düşünüyor gibi çok fazla yer tutucu oluşturabilirsiniz. Bitirebilirsiniz, şablonu taslak olarak kaydetmeyi veya yayımlamayı seçebilirsiniz.

   - **Taslağı kaydet** – Şablonu taslak olarak kaydeder ve daha sonra buna erişebilirsiniz. Modern şablonlar bölümünde kaydedilmiş taslakları ekleyebilirsiniz, düzenleyebilir veya belge kitaplığından  **NewEdit** >  **New menüsünü** seçerek yayımlayın. 
   - **Yayımla** – Şablonu, kuruluşta diğer kullanıcılar tarafından belge oluşturmak için kullanılacak şekilde yayımlar.  Belge kitaplığından **YeniEdit**  >  Yeni menüsünü seçerek, **yayımlanan şablonları Modern** şablonlar bölümünden ekleyebilirsiniz, düzenleyebilir veya yayımdan kaldırabilirsiniz. 

## <a name="edit-a-modern-template"></a>Modern şablonu düzenleme

Var olan bir şablonu düzenlemeniz ya da şablonu silmeniz veya yayımlamayı silmeniz gerekirse, bu adımları izleyin.

1. SharePoint belge kitaplığından **NewEdit Yeni** >  **menüsü'ni seçin**. 
 
   ![Yeniyi Düzenle menü seçeneğinin vurgulu olduğu belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-edit-template-1.png)

2. Yeniyi **Düzenle menü** panelinde, **Modern şablonlar** bölümünde, düzenlemek istediğiniz yayımlanmış veya taslak şablonunu seçin.
 
   ![Yeniyi Düzenle menü panelinin Modern şablonlar bölümünü gösteren ekran görüntüsü.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Yayımlanan şablonu veya taslak şablonunu düzenlemek için:

   - Yayımlanan **şablonlar'da**, yayımlanmış şablonu düzenleyemezsiniz şablon stüdyosturklarını açmak  **içinEdit'i**  seçin. Şablonu silmeyi veya yayımlamayı da seçebilirsiniz. 
 
      ![Yayımlanan şablonları gösteren Modern şablonlar bölümünün ekran görüntüsü.](../media/content-understanding/content-assembly-edit-published.png)

   - Taslak **şablonlar'da**, taslak şablonunu düzenleyemezsiniz şablon stüdyosını açmak  **içinEdit'i**  seçin. Şablonu silmeyi veya yayımlamayı da seçebilirsiniz.
 
      ![Taslak şablonları gösteren Modern şablonlar bölümünün ekran görüntüsü.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Modern şablondan belge oluşturma

Sıfırdan başlamak *zorunda kalmadan* hızlıca benzer belgeler oluşturmak için yayımlanmış modern şablonu kullanabilirsiniz. Yayımlanmış şablonu kullanarak belge oluşturmak için şu adımları izleyin:

1. SharePoint belge kitaplığından **Yeni'yi** seçin ve sonra da kullanmak istediğiniz modern şablonu seçin.
 
   ![Yeni menüsündeki modern şablon seçimlerini gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-document-1.png)

2. Şablon, şablon stüdyoda açılır.

3. Şablondan **belge oluştur panelinde, bilgileri** girin ve Belge oluştur'a **tıklayın**.

   ![Şablon panelinden belge oluşturma'yı gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-document-2.png)

   Yer tutucuların değerlerini doldurmada zaman ve çabayı azaltmaya yardımcı olmak SharePoint Syntex sağlar:

      - Listeden değer seçiminizi kolayca seçmenize yardımcı olacak öneriler.
      - Aynı listeyle ilişkilendirilmiş yer tutucuların kaydını benzersiz olarak tanımlayabilecekse, yer tutucu değerlerini otomatik doldurma.

> [!NOTE]
> - Şu anda şablon Microsoft Word yalnızca .docx belge (uzantı) desteği vardır. Belgeyi karşıya yüklemeden önce, Word belgesinde Değişiklikleri izle'nin veya **açıklamalar özelliği etkinleştirilmemiş** olduğundan emin olun. Belgeniz, resimler için metin yer tutucuları içeriyorsa, metnin kaydırılmış olduğundan emin olur. Şu anda **Word'de İçerik** Denetimlerini desteklemez. İçerik denetimlerinin olduğu bir Word belgesinde şablon oluşturmak için, lütfen modern bir şablon oluşturmadan önce bu şablonları kaldırın.
>- Şablon ve belge tek bir belge kitaplığıyla ilişkilendirildi. Şablonu başka bir belge kitaplığında kullanmak için, şablonu o belge kitaplığında yeniden oluşturmanız gerekir.
>- Modern şablonu oluşturmak için kullanılan karşıya yüklenen belge ayrı bir kopya olarak kaydedilir ve belge kitaplığının /forms dizinine yerleştirilir. Diskte özgün dosya etkilenmez.
>- Yalnızca metin için yer tutucular oluşturabilirsiniz. Şu anda resimler, akıllı resimler, tablolar ve madde işareti listeleri desteklenemİ değildir.
>- Şablondan bir belge oluşturulduğunda, bu belge şablonla ilişkilendirilz.



 
