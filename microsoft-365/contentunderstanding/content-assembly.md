---
title: Microsoft SharePoint Syntex'da içerik derlemesini kullanarak belge oluşturma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto, shrganguly
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex'da modern bir şablon kullanarak belgeleri ve diğer içerikleri otomatik olarak oluşturmayı öğrenin.
ms.openlocfilehash: 2ec87a1255e7bd53e03e05c53d9cfbb8e6c77be1
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772500"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da içerik derlemesini kullanarak belge oluşturma

sözleşmeler, iş beyanları, hizmet sözleşmeleri, onay mektupları, satış sunumları ve yazışmalar gibi standart yinelenen iş belgelerini otomatik olarak oluşturmanıza yardımcı olması için SharePoint Syntex kullanabilirsiniz. tüm bunları SharePoint Syntex içerik derlemesini kullanarak daha hızlı, daha tutarlı ve hatalara daha az eğilimli yapabilirsiniz.

İçerik derlemesiyle, *modern bir şablon* oluşturmak için var olan bir belgeyi kullanabilir ve ardından bu şablonu kullanarak veri kaynağı olarak SharePoint listeleri veya kullanıcı girişlerini kullanarak otomatik olarak yeni içerik oluşturabilirsiniz.

> [!NOTE]
> İçerik derleme özelliklerine erişmek ve bunları kullanmak için lisanslı bir SharePoint Syntex kullanıcısı olmanız gerekir. ayrıca SharePoint listelerini yönetmek için de izinleriniz olmalıdır.

## <a name="create-a-modern-template"></a>Modern şablon oluşturma

Modern bir şablon oluşturmak için bu adımları izleyin.

1. SharePoint belge kitaplığından Yeni **Modern şablon oluştur'u** >  seçin.

   ![Modern şablon oluştur seçeneğinin vurgulandığı belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-1.png)

2. Modern şablon oluşturmak için temel olarak kullanmak istediğiniz mevcut bir Word belgesini seçin ve ardından **Aç'ı** seçin.

   ![Belgeyi seçtiğiniz karşıya yükleme sayfasının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > Şu anda şablon oluşturmak için yalnızca Word belgelerini (.docx uzantısı) karşıya yükleyebilirsiniz. Word belgelerini yerel depolama alanınızdan veya masaüstünüzden Upload.

3. Belgeyi karşıya yükledikten sonra, belge şablon stüdyosunda görüntülenir ve burada belgeyi şablona dönüştürebilirsiniz.

   ![Şablon görüntüleyicisindeki belgenin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-3.png)

4. Şablon stüdyosunun sol üst köşesinde şablonun adını seçin. Varsayılan ad, şablonu oluşturmak için kullanılan belgenin adıdır. Şablonu yeniden adlandırmak istiyorsanız, varsayılan adı veya adın yanındaki kalem simgesini seçin, yeni adı yazın ve **ardından Enter'ı** seçin.

   ![Yeniden adlandırmayı seçecek belgenin adını gösteren şablon görüntüleyicisinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Belgedeki tüm dinamik metinler için, kullanıcıların bir belgeden diğerine değiştirmek isteyebileceği yer tutucular oluşturun. Örneğin, şirket adı, istemci adı, adres, telefon numarası veya tarih gibi girişler için bir yer tutucu oluşturmak isteyebilirsiniz.

    Yer tutucu oluşturmak için metni (tarih gibi) seçin. **Tüm yer tutucular** paneli açılır; burada yer tutucuya ilgili bir ad verir ve yer tutucuyla ilişkilendirmek istediğiniz giriş türünü seçersiniz.
 
   ![Bir alanın vurgulandığı ve Tüm yer tutucular panelinin gösterildiği şablon görüntüleyicisinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-4b.png)

   Şu anda, kullanıcıların bir yer tutucuyu doldurması için üç yol vardır:

   - [Metin girin veya tarih seçin](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Liste veya kitaplığın sütunundaki seçenekler arasından seçim yapma](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)
   - [Yönetilen meta veri terim kümesinden veya terimden seçim yapın](#associate-a-placeholder-by-selecting-from-managed-metadata-term-set-or-term)

   > [!NOTE]
   > Yalnızca metin için yer tutucular oluşturabilirsiniz. Görüntüler, akıllı resim, tablolar ve madde işaretleri listeleri şu anda desteklenmiyor.   

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Metin girerek veya tarih seçerek yer tutucuyu ilişkilendirme

**Tüm yer tutucular** panelinde:

1. **Ad** alanına yer tutucu için uygun bir ad girin.

   ![El ile giriş için Tüm yer tutucular panelini gösteren şablon görüntüleyicisinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-5a.png)

2. **Yazarların bu yer tutucuyu nasıl doldurduğu** bölümünde **Metin girin'i seçin veya bir tarih seçin**.

3. **Bilgi türü** alanında, yer tutucuyla ilişkilendirmek istediğiniz veri türünü seçin. Şu anda altı seçenek vardır: **Tek satırlı metin**, **Birden çok metin satırı**, **Sayı**, **Tarih ve saat**, **E-posta** ve **Köprü**.

4. **Ekle**'yi seçin.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Bir liste veya kitaplığın sütunundaki seçenekler arasından seçim yaparak yer tutucuyu ilişkilendirme

**Tüm yer tutucular** panelinde:

1. **Ad** alanına yer tutucu için uygun bir ad girin.

   ![SharePoint listesinden giriş için Tüm yer tutucular panelini gösteren şablon görüntüleyicisinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-6a.png)

2. **Yazarların bu yer tutucuyu nasıl doldurduğu** bölümünde, **liste veya kitaplığın sütunundaki seçeneklerden seç'i** ve ardından **Seç'i** seçin.

3. **Kaynak sütun eklemek için liste seçin** sayfasında, kullanmak istediğiniz listeyi seçin ve ardından **İleri'yi** seçin.

   ![Listeleri gösteren kaynak sütun eklemek için liste seçin sayfasının ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-7.png)

4. **Var olan liste sayfasında Kaynak sütun seçin** sayfasında, yer tutucuyla ilişkilendirmek istediğiniz sütun adını seçin ve ardından **Kaydet'i** seçin.

   ![Mevcut liste sayfasından sütun adlarını gösteren Kaynak sütun seçin öğesinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-8.png)

    Listelerin özgün sayfasını yeniden görmek istiyorsanız listenin en altındaki **Git (liste adı)** bağlantısını seçin.

5. İşiniz bittiğinde, liste alanının yer tutucuyla ilişkilendirildiğini görürsünüz.

   ![Yer tutucuyla ilişkilendirilmiş liste alanını gösteren Tüm yer tutucular panelinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-9.png)

6. Kullanıcıların el ile giriş ekleyebilmesini istiyorsanız, listeden seçim yapmaya ek olarak **Yazarların yeni seçenekler eklemesine izin ver'i** seçin. Bu durumda, el ile giriş veri türü için varsayılan değer *Tek satır metindir*. Ayrıca, yazarların giriş yaptığı değerler yalnızca belgeyi oluşturmak için kullanılır. Bunlar SharePoint listesine eklenmez.

### <a name="associate-a-placeholder-by-selecting-from-managed-metadata-term-set-or-term"></a>Yönetilen meta veri terim kümesinden veya terimden seçim yaparak yer tutucuyu ilişkilendirme

**Tüm yer tutucular** panelinde:

1. **Ad** alanına yer tutucu için uygun bir ad girin.

   ![Bir terim veya terim kümesinden giriş için Tüm yer tutucular panelini gösteren şablon görüntüleyicisinin ekran görüntüsü.](../media/content-understanding/content-assembly-create-template-term.png)

2. **Yazarların bu yer tutucuyu nasıl doldurduğu** bölümünde **Yönetilen meta veri terim kümesinden veya teriminden seç'i** ve ardından **Seç'i** seçin.

3. **Terim kümelerini veya terimleri seçin** sayfasında, yer tutucuyla ilişkilendirilecek terim kümesini veya terimi arayın veya seçin ve ardından **Kaydet'i** seçin.

   ![Terim kümelerini veya terimleri seçin sayfasının ekran görüntüsü.](../media/content-understanding/content-assembly-select-term.png)

4. İşiniz bittiğinde, seçilen terim kümesinin veya terimin yer tutucuyla ilişkilendirildiğini görürsünüz. 

   ![İlişkili terim kümesini veya terimi gösteren Tüm yer tutucular panelinin ekran görüntüsü.](../media/content-understanding/content-assembly-associated-term.png)

5. Kullanıcıların terim kümesine veya terime karşılık gelen birden çok değer ekleyebilmesini istiyorsanız **Birden çok değere izin ver'i** seçin. Ayrıca terim kümesi açık terim kümesi olarak yapılandırılmışsa **Yeni değerlere izin ver'i** seçebilirsiniz. Bu seçeneği etkinleştirirseniz, modern şablondan belge oluşturan kullanıcılar terim kümesine yeni terimler ekleyebilir ve bu terimleri yer tutucu değerler olarak ekleyebilir.

   > [!TIP]
   > **Yeni değerlere izin ver** seçeneğini etkinleştirdiğinizde (yalnızca açık terim kümeleri için izin verilir), kullanıcıların terim deposuna yedekli terimler ekleme olasılığı daha yüksektir. Yedekli terimler, yöneticilerin terim kümesini yönetmesini zorlaştırabilir.

Gerekli olduğunu düşündüğünüz kadar yer tutucu oluşturabilirsiniz. İşiniz bittiğinde, şablonu taslak olarak kaydetmeyi veya şablonu yayımlamayı seçebilirsiniz.

   - **Taslağı kaydet** – Şablonu taslak olarak kaydeder ve daha sonra erişebilirsiniz. Belge kitaplığından **Yeni** > **Düzenle menüsünü** seçerek **Modern şablonlar** bölümünden kaydedilmiş taslakları görüntüleyebilir, düzenleyebilir veya yayımlayabilirsiniz.
 
   - **Yayımla** – Belge oluşturmak için kuruluştaki diğer kullanıcılar tarafından kullanılacak şablonu yayımlar. Belge kitaplığından **Yeni** > **Düzenle menüsünü** seçerek **, Yayımlanan şablonları Modern şablonlar** bölümünden görüntüleyebilir, düzenleyebilir veya yayımdan kaldırabilirsiniz. 

## <a name="edit-a-modern-template"></a>Modern şablonu düzenleme

Mevcut bir şablonu düzenlemeniz veya şablonu silmeniz veya yayımlamanız gerekiyorsa bu adımları izleyin.

1. SharePoint belge kitaplığından **Yeni** > **Düzenle Yeni menüsünü** seçin.

   ![Yeni Düzenle menü seçeneğinin vurgulandığı belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-edit-template-1.png)

2. **Yeni Düzenle menü** panelinin **Modern şablonlar** bölümünde, düzenlemek istediğiniz yayımlanmış veya taslak şablonu seçin.

   ![Modern şablonlar bölümünü gösteren Yeni Düzenle menü panelinin ekran görüntüsü.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Yayımlanmış bir şablonu veya taslak şablonu düzenlemek için:

   - **Yayımlanan şablonlar** için **Düzenle'yi** seçerek yayımlanan şablonu düzenleyebileceğiniz şablon stüdyoyu açın. Şablonu silmeyi veya yayımdan kaldırmayı da seçebilirsiniz.

      ![Yayımlanan şablonları gösteren Modern şablonlar bölümünün ekran görüntüsü.](../media/content-understanding/content-assembly-edit-published.png)

   - **Taslak şablonları** için **Düzenle'yi** seçerek taslak şablonu düzenleyebileceğiniz şablon stüdyoyu açın. Şablonu silmeyi veya yayımlamayı da seçebilirsiniz.

      ![Taslak şablonları gösteren Modern şablonlar bölümünün ekran görüntüsü.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Modern şablondan belge oluşturma

*Sıfırdan* başlamak zorunda kalmadan benzer belgeleri hızla oluşturmak için yayımlanmış bir modern şablon kullanabilirsiniz. Yayımlanmış bir şablon kullanarak belge oluşturmak için şu adımları izleyin:

1. SharePoint belge kitaplığından **Yeni'yi** ve ardından kullanmak istediğiniz modern şablonu seçin.

   ![Yeni menüsündeki modern şablon seçeneklerini gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-document-1.png)

2. Şablon, şablon stüdyosunda açılır.

3. **Şablondan belge oluştur** panelinde bilgileri girin ve **Belge oluştur'u** seçin.

   ![Şablondan belge oluşturma panelini gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/content-assembly-create-document-2b.png)

   Yer tutucuların değerlerini doldurmaya yönelik zaman ve çabayı azaltmaya yardımcı olmak için SharePoint Syntex şunları sağlar:

      - Listeden değer seçerken değerleri kolayca seçmenize yardımcı olacak öneriler.
      - Aynı listeyle ilişkilendirilmiş yer tutucular için bir kaydı benzersiz olarak tanımlayabilmek için yer tutucu değerlerini otomatik olarak doldurun.

> [!NOTE]
> **Geçerli sürüm sınırlamaları**
>- Şu anda şablon oluşturmak için yalnızca Microsoft Word belgeler (.docx uzantısı) desteklenmektedir. Word belgesini karşıya yüklemeden önce, belgenin açıklama içermediğinden veya **Değişiklikleri izle** seçeneğinin etkin olduğundan emin olun. Belgede resimler için metin yer tutucuları varsa, bunların metin sarmalı olmadığından emin olun. Word'deki içerik denetimleri şu anda desteklenmiyor. İçerik denetimleri olan bir Word belgesinden şablon oluşturmak istiyorsanız, modern bir şablon oluşturmadan önce bunları kaldırın.
>- Şablon ve belge bir belge kitaplığıyla ilişkilendirilir. Şablonu başka bir belge kitaplığında kullanmak için, şablonu bu belge kitaplığında yeniden oluşturmanız gerekir.
>- Modern şablonu oluşturmak için kullanılan karşıya yüklenen belge ayrı bir kopya olarak kaydedilir ve belge kitaplığının /forms dizinine yerleştirilir. Disk üzerindeki özgün dosya etkilenmez.
>- Yalnızca metin için yer tutucular oluşturabilirsiniz. Görüntüler, akıllı resim, tablolar ve madde işaretleri listeleri şu anda desteklenmiyor.
>- Şablondan bir belge oluşturulduktan sonra, şablonla ilişkilendirilmemiş olur.



 
