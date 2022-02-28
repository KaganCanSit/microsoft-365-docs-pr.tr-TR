---
title: Belgeleri, kuruluşun Azure Azure hesaplarında Depolama verme
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
ms.custom: seo-marvel-mar2020
description: Belgeleri bir Azure Depolama hesabına ayarlanmış bir gözden geçirme Azure Depolama Gezgini dışarı aktarın ve Azure Depolama Gezgini yerel bir bilgisayara indirmek için bunu kullanın.
ms.openlocfilehash: 8f3110ef386fd5c5d8adc641aa223435caf0da67
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988166"
---
# <a name="export-documents-in-a-review-set-to-an-azure-storage-account"></a>Belgeleri gözden geçirme kümesine Azure Depolama verme

Büyük bir olayda gözden geçirme kümesinden dışarı Advanced eDiscovery belgeleri dışarı aktarabilirsiniz, bu belgeleri azure Depolama tarafından yönetilen bir Azure Depolama hesabına aktarma seçeneğiniz vardır. Bu seçeneği kullanırsanız belgeler, Azure Posta'nın farklı Depolama yükler. Dışarı aktarıldıktan sonra, Dosyayı kullanarak belgelere erişebilirsiniz (ve bunları yerel bir bilgisayara veya başka bir konuma indirebilirsiniz) Azure Depolama Gezgini. Bu makalede, belgeleri Azure Depolama hesabınıza aktarma ve Azure Depolama Gezgini dışarı aktarıldı belgeleri indirmek üzere Azure Depolama konuma bağlanmak için Depolama'i kullanma yönergeleri sağlar. Bu konuda daha fazla Azure Depolama Gezgini için bkz. [Azure Depolama Gezgini](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer).

## <a name="before-you-export-documents-from-a-review-set"></a>Gözden geçirme kümesinden belgeleri dışarı aktarmadan önce

- Azure Depolama hesabınız için bir paylaşılan erişim imzası (SAS) belirteci ve gözden geçirme kümesinden belgeleri dışarı aktaracak depolama hesabıyla ilgili belirli bir kapsayıcının URL'sini sağlanız. 2. Adımı gerçekleştirecekken, bunları hazır bulundurarak (örneğin, bir metin dosyasına kopyalanmış) emin olun

  - **SAS belirteci**: SAS belirtecinin Azure Depolama hesabınıza uygun olduğundan emin olun (kapsayıcı için değil). Azure Depolama'da hesabınız için bir SAS belirteci Depolama. Bunu yapmak için Azure Depolama hesabına gidin ve Blade depolama hesabı ayarları altındaki **Ayarlar** imzayı  paylaş'ı seçin. VARSAYıLAN ayarları kullanın ve SAS belirteci 2007'ye 00.0000'i 100'den fazla kaynak türü 2013'e izin ver.

  - **Kapsayıcı URL**: Gözden geçirme kümesi belgelerini karşıya yüklemek için bir kapsayıcı oluşturmanız ve sonra kapsayıcıNıN URL'sinin bir kopyasını alınız; örneğin, `https://ediscoverydata.blob.core.windows.net/exportdata`. URL'yi almak için, Azure Depolama kapsayıcıya gidin ve kapsayıcı  **blade'ın Ayarlar** kısmında Özellikler'i seçin.

- Dosyayı indirin ve Azure Depolama Gezgini. Yönergeler için bkz. [Azure Depolama Gezgini.](https://go.microsoft.com/fwlink/p/?LinkId=544842) Bu aracı, Azure Depolama hesabınıza kapsayıcıya bağlanmak ve 1. Adımda dışarı aktarmış olduğunuz belgeleri indirmek için kullanırsınız.

## <a name="step-1-export-the-documents-from-a-review-set"></a>1. Adım: Gözden geçirme kümesinden belgeleri dışarı aktarma

İlk adım, gözden geçirme kümesi dışında belgeleri dışarı aktaran bir dışarı aktarma işi oluşturmaktır. Tüm dışarı aktarma seçenekleri hakkında daha ayrıntılı yönergeler için bkz. [Gözden geçirme kümesinden belgeleri dışarı aktarma](export-documents-from-review-set.md). Aşağıdaki yordamda, belgeleri organizasyon azure hesabı olarak dışarı aktarma ayarları Depolama vurgulanır.

1. Görünüm Microsoft 365 uyumluluk merkezi büyük/Advanced eDiscovery açın, Gözden Geçir kümeleri sekmesini seçin ve sonra da dışarı  aktarma yapmak istediğiniz gözden geçirme kümesine tıklayın.

2. Gözden geçirme kümesinde **ActionExport'a** >  **tıklayın**.

3. Dışarı aktarma **seçenekleri uç** sayfasında, dışarı aktarma için bir ad (gerekli) ve açıklama (isteğe bağlı) yazın.

4. Belgeler, meta veriler, içerik ve seçenekler bölümlerindeki ayarları yapılandırabilirsiniz. Bu ayarlar hakkında daha fazla bilgi için bkz [. Gözden geçirme kümesinden belgeleri dışarı aktarma](export-documents-from-review-set.md).

5. Çıkış **seçenekleri bölümünde**, **Azure** Depolama hesabınıza aktarıldı.

6. Kapsayıcı URL'sini ve depolama hesabınız için SAS belirtecini ilgili alanlara yapıştırın.

   ![Bağlantı URL'sini ve SAS belirtecini ilgili alanlara yapıştırın.](../media/AzureStorageOutputOptions.png)

7. Dışarı **aktarma işini** oluşturmak için Dışarı Aktar'a tıklayın.

## <a name="step-2-obtain-the-sas-url-from-the-export-job"></a>2. Adım: Dışarı aktarma işlerinden SAS URL'sini alma

Sonraki adım, 1. Adımda dışarı aktarma işini oluşturduktan sonra oluşturulan SAS URL'sini almak olacak. Sas URL'sini, Azure Depolama ve gözden geçirme kümesi belgelerini dışarı aktarmış olduğunuz kapsayıcıya bağlamak için kullanırsınız.

1. Sayfa **Advanced eDiscovery**, vakaya gidin ve Dışarı Aktarmalar **sekmesine** tıklayın.

2. Dışarı **Aktarmalar** sekmesinde, indirmek istediğiniz dışarı aktarma işini tıklatın. Bu, 1. Adımda oluşturduğunuz dışarı aktarma işidir.

3. Çıkış sayfasındaki **Konumlar'ın** altında gösterilen SAS URL'sini kopyalayın. Gerekirse, bir metin dosyasına kaydedebilir ve böylelikle 3. Adımda bu dosyaya erişebilirsiniz.

   ![Konumlar altında gösterilen SAS URL'sini kopyalayın.](../media/eDiscoExportJob.png)

   > [!TIP]
   > Dışarı aktarma işsinde görüntülenen SAS URL'si, kapsayıcı URL'nin ve Azure Depolama hesabınız için SAS belirtecinin bir Depolama olur. Bunu dışarı aktarma işlerinden kopyalayıp URL ve SAS belirteci birleştirerek kendiniz oluşturabilirsiniz.

## <a name="step-3-connect-to-the-azure-storage-container"></a>3. Adım: Bağlan Azure kapsayıcıya Depolama adım

Son adım, Azure Depolama hesabınıza kapsayıcıya bağlanmak ve dışarı aktaran belgeleri yerel bir bilgisayara indirmek için Azure Depolama Gezgini VE SAS URL'sini kullanmaktır.

1. İndirdiğiniz Azure Depolama Gezgini güncelleştirmeleri başlatma.

2. İletişim Kutusunu **Aç Bağlan tıklayın**.

   ![Hesap ekle simgesine tıklayın.](../media/AzureStorageConnect.png)

3. **Azure Bağlan kapsayıcısı Depolama** **Blob kapsayıcısı'ne tıklayın**.

4. Kimlik Doğrulama **Yöntemi Seç sayfasında** Paylaşılan erişim imzası **(SAS) seçeneğini belirtin** ve ardından Sonraki'ye **tıklayın**.

5. Bağlantı **Bilgilerini Girin sayfasında** , **Blob Kapsayıcı SAS URL'si** kutusuna SAS URL'sini (2. adımda dışarı aktarma işlerinden edinilen) yapıştırın.

    ![SAS URL'sini URI kutusuna yapıştırın.](../media/AzureStorageConnect3.png)

    Kapsayıcı adının Görünen ad kutusunda **görüntülendiğinden dikkat** edin. Bu adı düzenleyebilirsiniz.

6. Özet **sayfasını** görüntülemek için **Sonraki'ne** ve sonra Tamam'a **Bağlan**.

    **Blob kapsayıcıları** düğümü (**Depolama Hesaplar** > **(Ekli Kapsayıcılar)** \> açılır.

    ![Blobs kapsayıcıları düğümünde işleri dışarı aktarın.](../media/AzureStorageConnect5.png)

    5. adımdan görünen adla adlandırılmış bir kapsayıcı içerir. Bu kapsayıcı, Azure Depolama hesabı klasörünüzdeki kapsayıcıya indirdiğiniz her dışarı aktarma işi için bir klasör içerir. Bu klasörler, dışarı aktarma işinin kimliğine karşılık gelen bir kimlikle adlandırılmıştır. Bu dışarı aktarma kimliklerini (ve dışarı aktarmanın adı) her dışarı aktarma işi için veri hazırlama sayfasının İş durumu bilgilerinde İş  ve İş için Veri hazırlama'nın Advanced eDiscovery bulabilirsiniz.

7. İş dışarı aktarma klasörünü çift tıklatın ve açın.

   Klasörlerin ve dışarı aktarma raporlarının listesi görüntülenir.

    ![Dışarı aktarma klasörü dışarı aktarıldı dosyaları ve dışarı aktarma raporlarını içerir.](../media/AzureStorageConnect6.png)

8. Dışarı aktarma işlerinden tüm içeriği dışarı aktarma işlemi için, **Yukarı oka** tıklayın ve dışarı aktarma işi klasörüne geri gidin ve ardından İndir'e **tıklayın**.

9. Dışarı aktarilen dosyaları indirmek istediğiniz konumu belirtin ve ardından Klasör seç'e tıklayın.

    Aşağıdaki Azure Depolama Gezgini indirme işlemini başlatır. Dışarı aktarıldı öğeler indirildi durumunu **Etkinlikler bölmesinde görüntülenir** . İndirme tamamlandığında bir ileti görüntülenir.

> [!NOTE]
> bir dosyadaki dışarı aktarma işinin tamamını indirmek Azure Depolama Gezgini, indirmek ve görüntülemek için belirli öğeleri seçin.

## <a name="more-information"></a>Daha fazla bilgi

- Dışarı aktarma işi klasörü aşağıdaki öğeleri içerir. Dışarı aktarma klasöründeki gerçek öğeler, dışarı aktarma işi oluşturulduğunda yapılandırılan dışarı aktarma seçenekleri tarafından belirlenir. Bu seçenekler hakkında daha fazla bilgi için bkz [. Gözden geçirme kümesinden belgeleri dışarı aktarma](export-documents-from-review-set.md).

  - Export_load_file.csv: Bu CSV dosyası, dışarı aktarıldı her belgeyle ilgili bilgileri içeren ayrıntılı bir dışarı aktarma raporu. Dosya, bir belgenin her meta veri özelliği için bir sütundan oluşur. Bu rapora dahil edilen meta verilerin listesi ve açıklaması için, bu rapordaki Belge meta veri  alanları başlığı altında yer alan tablonun Dışarı aktarıldı [alan adı sütununa Advanced eDiscovery](document-metadata-fields-in-advanced-ediscovery.md).

  - Summary.txt: Dışarı aktarma istatistikleri dahil dışarı aktarmanın özetini içeren metin dosyası.

  - Extracted_text_files: Bu klasör, dışarı aktarıldı her belgenin metin dosyası sürümünü içerir.

  - NativeFiles: Bu klasör, dışarı aktarıldı her belgenin yerel dosya sürümünü içerir.

  - Error_files: Dışarı aktarma işi herhangi bir hata dosyası içeriyorsa, bu klasör aşağıdaki öğeleri içerir:

    - ExtractionError.csv: Bu CSV dosyası, üst öğeden düzgün ayık olmayan dosyalar için kullanılabilen meta verileri içerir.

    - processingError: Bu klasör, işleme hatalarının olduğu belgeleri içerir. Bu içerik öğe düzeyindedir ve bu da ekin işleme hatası olması durumda eki içeren belgenin de bu klasöre ekli olduğu anlamına gelir.
