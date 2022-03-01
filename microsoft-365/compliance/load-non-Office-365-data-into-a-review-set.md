---
title: Gözden Microsoft 365 olmayan verileri gözden geçirme kümesine yükleme
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
description: Örnek olayda, Microsoft 365 olmayan verilerin çözümleme için ayarlanmış bir gözden geçirme kümesine nasıl Advanced eDiscovery öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39f91846e42bb2403c2b1faf7fd98ff3e7759182
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010775"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Gözden Microsoft 365 olmayan verileri gözden geçirme kümesine yükleme

Analiz etmeniz gereken tüm belgeler Advanced eDiscovery başka bir Microsoft 365. Advanced eDiscovery'Microsoft 365 olmayan veri içeri aktarma özelliğiyle, Microsoft 365 bir gözden geçirme kümesine yükleyebilirsiniz. Bu makalede, çözümleme yapmak üzere belgeniz olmayan Microsoft 365 başka bir Advanced eDiscovery getirebilirsiniz.

## <a name="requirements-to-upload-non-office-365-content"></a>Office 365 olmayan içeriği karşıya Office 365 gereksinimler

Bu makalede açıklanan Microsoft 365 olmayan karşıya yükleme özelliğini kullanmak için aşağıdakilere sahip olmak gerekir:

- Bu olmayan içeriği ilişkilendirmek istediğiniz tüm koruyucular Microsoft 365 lisans atanabilir. Daha fazla bilgi için bkz[. Yeni iş Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- Varolan bir Advanced eDiscovery durumu.

- Bu olmayan verileri karşıya yükleymeden ve ilişkilendirmeden önce özel Microsoft 365 eklilerin ekli olması gerekir.

- Veri Microsoft 365, veri kaynağı tarafından desteklenen bir dosya Advanced eDiscovery. Daha fazla bilgi için bkz[. Dosya dosyalarında desteklenen Advanced eDiscovery](supported-filetypes-ediscovery20.md).

- Gözden geçirme kümesine yüklenen tüm dosyalar, her klasörün belirli bir custo cust ile ilişkilendirilen klasörlerde yer almaları gerekir. Bu klasörlerin adları aşağıdaki adlandırma biçimini kullan olmalıdır: *alias@domainname*. Kullanıcı alias@domainname diğer adı ve etki Microsoft 365 olması gerekir. Kök klasördeki tüm alias@domainname toplayabilirsiniz. Kök klasör yalnızca en son alias@domainname içerebilir. Kök klasördeki eksik dosyalar desteklenmez.

   Karşıya yüklemek istediğiniz ve Microsoft 365 olmayan verilerin klasör yapısı aşağıdaki örnektekine benzer olur:

   - c:\nO365\abraham.mcmahon@contoso.com
   - c:\nO365\jewell.gordon@contoso.com
   - c:\nO365\staci.gonzalez@contoso.com

   Diğer abraham.mcmahon@contoso.com, jewell.gordon@contoso.com ve staci.gonzalez@contoso.com durumdaki koruyucuların SMTP adresleridir.

   ![Veri karşıya Microsoft 365 olmayan klasör yapısı.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- eBulma Yöneticisi rol grubuna atanan (ve eBulma Yöneticisi olarak eklenen hesap).

- Dosya olmayan içerik klasörü yapısına erişimi olan bir bilgisayara yüklenmiş AzCopy v8.1 Microsoft 365 aracı. AzCopy'i yüklemek için bkz. [AzCopy v8.1 ile verileri aktarma Windows](/previous-versions/azure/storage/storage-use-azcopy). AzCopy'nin varsayılan konuma yük olduğundan emin olun; bu **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy konumundadır**. AzCopy v8.1 kullanmalıdır. AzCopy'nin diğer sürümleri, çalışma Microsoft 365 yüklenirken Advanced eDiscovery.


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>Upload olmayan Microsoft 365 diğer içeriğe Advanced eDiscovery

1. eBulma Yöneticisi veya eBulma Yöneticisi olarak, Advanced eDiscovery'i açın ve Microsoft 365 olmayan verilerin karşıya yük devretme durumuna gidin.  

2. Gözden **Geçir kümeleri'ne** tıklayın ve sonra gözden geçirilmeyen verileri karşıya yüklemek Microsoft 365 seçin.  Gözden geçirme kümemiz yoksa, bir gözden geçirme kümesi oluşturabilirsiniz. 
 
3. Gözden geçirme kümesine tıklayarak veya seçerek ve Gözden geçirme kümesi **aç'a tıklayarak açın**.

4. Gözden geçirme kümesinde **Gözden geçirme kümesi** yönet'e (Eylemler seçeneğinin hemen yanındaki  aşağı ok) tıklayın ve sonra Da Gözden Geçirme **Office 365 seçeneğine** tıklayın.

5. Veri **Upload sihirbazını** başlatmak için Dosya Ekle'ye tıklayın.

   ![Upload seçin.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   Sihirbazın ilk adımı, Microsoft tarafından sağlanan güvenli bir Azure depolama Depolama ve dosyaları karşıya yüklemek için bu konumu hazırlar.  Hazırlık tamamlandığında, Sonraki **: Dosyalar Upload etkin** hale gelir.

   ![İçeri Aktarma Microsoft 365: Hazırla.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Sonraki **: Dosyaları Upload tıklatın**.

6. Yeni **Upload** sayfasında şunları yapın:

   ![Non-Microsoft 365 Import: Upload dosyaları seçin.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. Dosyaların **konumu yolu kutusuna**, karşıya yüklemek istediğiniz veri olmayan kök klasörün Microsoft 365 doğrula veya yazın. Örneğin, Başlamadan önce bölümünde gösterilen örnek dosyaların konumu için **,O365 üzerinde %USERPROFILE\Downloads\nyazın**. Doğru konumun sağlanması, yolun altındaki kutuda görüntülenen AzCopy komutunun düzgün bir şekilde güncelleştirilsini sağlar.

   b. Kutuda **gösterilen komutu** kopyalamak için Panoya kopyala'ya tıklayın.

7. Kopyalanan Windows istemini çalıştırın, önceki adımda kopyalanmış olan komutu yapıştırın ve **ardından AzCopy** komutunu başlatmak için Enter tuşuna basın.  Siz komutu başlattıktan sonra, Microsoft 365 olmayan dosyalar 4. adımda hazır Depolama Azure Depolaması'na karşıya yükler.

   ![Non-Microsoft 365 Import: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Daha önce de belirtildiği gibi, Dosya Dosyaları sayfasında sağlanan komutu başarılı bir şekilde kullanmak için AzCopy v8.1 **Upload** gerekir. Sağlanan AzCopy komutu başarısız olursa, lütfen [Aşağıdakiler'de AzCopy sorunlarını giderme Advanced eDiscovery](troubleshooting-azcopy.md).

8. Sihirbaza geri Microsoft 365 uyumluluk merkezi ve Sonraki **: Sihirbazda dosyaları** işleme'ye tıklayın.  Bu, Azure kaynak konuma yüklenen, Microsoft 365 olmayan dosyaların işlemesini, metin ayıklamayı ve Depolama başlatılır.  

9. İş dosyaları sayfasında veya İş sekmesinde, Gözden geçirme kümesine veri ekleme adlı bir iş  görüntüerek **Microsoft 365 ilerlemesini izleyebilirsiniz**.  İş bittiğinde, yeni dosyalar gözden geçirme kümesinde kullanılabilir.

   ![Non-Microsoft 365 Import: Process files.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. İşleme tamam olduktan sonra sihirbazı kapatabilirsiniz.
