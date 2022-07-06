---
title: Gözden geçirme kümesine Microsoft 365 olmayan verileri yükleme
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
description: eBulma (Premium) durumunda analiz için Microsoft 365 dışı verileri bir gözden geçirme kümesine aktarmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c1efdcb98c0d9ae5b0f47215997782a3b88c8683
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636017"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Gözden geçirme kümesine Microsoft 365 olmayan verileri yükleme

Microsoft Purview eKeşif (Premium) içinde analiz etmeniz gereken belgelerin tümü Microsoft 365'te yer almamaktadır. eKeşif'teki (Premium) Microsoft 365 dışı veri içeri aktarma özelliğiyle, Microsoft 365'te yer almayan belgeleri bir gözden geçirme kümesine yükleyebilirsiniz. Bu makalede, Microsoft olmayan 365 belgelerinizi analiz için eKeşif'e (Premium) nasıl getireceğiniz gösterilmektedir.

## <a name="requirements-to-upload-non-office-365-content"></a>Office 365 olmayan içeriği karşıya yükleme gereksinimleri

Bu makalede açıklanan Microsoft 365 dışı karşıya yükleme özelliğini kullanmak için aşağıdakilere sahip olmanız gerekir:

- Microsoft 365 dışı içeriği ilişkilendirmek istediğiniz tüm koruyuculara uygun lisans atanmalıdır. Daha fazla bilgi için bkz. [eBulma (Premium) kullanmaya başlama](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- Mevcut bir eBulma (Premium) olayı.

- Microsoft 365 olmayan verileri karşıya yükleyip bunlarla ilişkilendirebilmeniz için önce koruyucuların olaya eklenmesi gerekir.

- Microsoft 365 dışı veriler, eBulma (Premium) tarafından desteklenen bir dosya türü olmalıdır. Daha fazla bilgi için bkz. [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md).

- Bir gözden geçirme kümesine yüklenen tüm dosyalar, her klasörün belirli bir koruyucuyla ilişkilendirildiği klasörlerde bulunmalıdır. Bu klasörlerin adları şu adlandırma biçimini kullanmalıdır: *alias@domainname*. alias@domainname kullanıcının Microsoft 365 diğer adı ve etki alanı olmalıdır. Kök klasördeki tüm alias@domainname klasörlerini toplayabilirsiniz. Kök klasör yalnızca alias@domainname klasörlerini içerebilir. Kök klasördeki gevşek dosyalar desteklenmez.

   Karşıya yüklemek istediğiniz Microsoft olmayan 365 verilerinin klasör yapısı aşağıdaki örneğe benzer olacaktır:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Burada abraham.mcmahon@contoso.com, jewell.gordon@contoso.com ve staci.gonzalez@contoso.com, olaydaki koruyucuların SMTP adresleridir.

   ![Microsoft 365 dışı veri karşıya yükleme klasör yapısı.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- eBulma Yöneticisi rol grubuna atanan (ve eBulma Yöneticisi olarak eklenen) bir hesap.

- Microsoft 365 olmayan içerik klasörü yapısına erişimi olan bir bilgisayarda yüklü Olan AzCopy v8.1 aracı. AzCopy'yi yüklemek için bkz. [Windows'da AzCopy v8.1 ile veri aktarma](/previous-versions/azure/storage/storage-use-azcopy). AzCopy'yi **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy** olan varsayılan konuma yüklediğinizden emin olun. AzCopy v8.1 kullanmanız gerekir. eBulma(Premium) içinde Microsoft dışı 365 verileri yüklenirken AzCopy'nin diğer sürümleri çalışmayabilir.


## <a name="upload-non-microsoft-365-content-into-ediscovery-premium"></a>Microsoft 365 dışı içeriği eBulma'ya yükleme (Premium)

1. eBulma Yöneticisi veya eBulma Yöneticisi olarak eKeşif (Premium) dosyasını açın ve Microsoft olmayan 365 verilerinin karşıya yüklendiği duruma gidin.  

2. **Kümeleri gözden geçir'e** tıklayın ve ardından Microsoft olmayan 365 verilerini karşıya yüklemek için gözden geçirme kümesini seçin.  Gözden geçirme kümeniz yoksa bir tane oluşturabilirsiniz. 
 
3. Üzerine tıklayarak veya seçip **Gözden geçirme kümesini aç'a tıklayarak gözden geçirme kümesini** açın.

4. Gözden geçirme kümesinde **Gözden geçirme kümesini yönet'e** (**Eylemler** seçeneğinin hemen yanındaki aşağı ok) ve ardından **veri Office 365 olmayan** seçeneğine tıklayın.

5. Veri içeri aktarma sihirbazını başlatmak için **Dosyaları karşıya yükle'ye** tıklayın.

   ![Dosyaları karşıya yükleyin.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   Sihirbazın ilk adımı, dosyaları karşıya yüklemek için Microsoft tarafından sağlanan güvenli bir Azure Depolama konumu hazırlar.  Hazırlık tamamlandığında **Sonraki: Dosyaları karşıya yükle** düğmesi etkin hale gelir.

   ![Microsoft 365 Dışı İçeri Aktarma: Hazırlama.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. **İleri: Dosyaları karşıya yükle'ye** tıklayın.

6. **Dosyaları karşıya yükle** sayfasında aşağıdakileri yapın:

   ![Microsoft 365 Dışı İçeri Aktarma: Dosyaları karşıya yükleyin.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. **Dosyaların konumuna giden yol** kutusunda, karşıya yüklemek istediğiniz Microsoft 365 dışı verileri depoladığınız kök klasörün konumunu doğrulayın veya yazın. Örneğin, **Başlamadan önce bölümünde** gösterilen örnek dosyaların konumu için **% USERPROFILE\Downloads\nonO365** yazarsınız. Doğru konumun sağlanması, yolun altındaki kutuda görüntülenen AzCopy komutunun düzgün bir şekilde güncelleştirilmesini sağlar.

   b. Kutuda görüntülenen komutu kopyalamak için **Panoya kopyala'ya** tıklayın.

7. Bir Windows komut istemi başlatın, önceki adımda kopyaladığınız komutu yapıştırın ve ardından AzCopy komutunu başlatmak için **Enter tuşuna** basın.  Komutu başlattıktan sonra, Microsoft olmayan 365 dosyaları 4. adımda hazırlanan Azure Depolama konumuna yüklenir.

   ![Microsoft 365 Dışı İçeri Aktarma: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Daha önce belirtildiği gibi, **Dosyaları karşıya yükleme** sayfasında sağlanan komutu başarıyla kullanmak için AzCopy v8.1 kullanmanız gerekir. Sağlanan AzCopy komutu başarısız olursa, lütfen [eBulma(Premium) içinde AzCopy sorunlarını giderme](troubleshooting-azcopy.md) bölümüne bakın.

8. Microsoft Purview uyumluluk portalı Geri dön ve **İleri: Sihirbazdaki dosyaları işleme'ye** tıklayın.  Bu işlem, Azure Depolama konumuna yüklenen Microsoft olmayan 365 dosyalarının işlenmesini, metin ayıklamasını ve dizine kaydedilmesini başlatır.  

9. Dosyaları işleme sayfasında veya **İşler** sekmesinde, **Gözden geçirme kümesine Microsoft 365 dışı veri ekleme adlı bir** işi görüntüleyerek **dosyaların** işlenmesinin ilerleme durumunu izleyin.  İş tamamlandıktan sonra, yeni dosyalar gözden geçirme kümesinde kullanılabilir.

   ![Microsoft 365 Dışı İçeri Aktarma: dosyaları işleme.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. İşlem tamamlandıktan sonra sihirbazı kapatabilirsiniz.
