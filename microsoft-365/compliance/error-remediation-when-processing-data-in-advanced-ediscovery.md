---
title: Verileri işlerken hata düzeltme
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
description: eBulma 'da (Premium) içeriğin düzgün işlenmesini engelleyebilecek veri sorunlarını düzeltmek için hata düzeltmeyi kullanmayı öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 1f56ad34cb295103178c5f244ccd78d7ad3757b0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994556"
---
# <a name="error-remediation-when-processing-data"></a>Verileri işlerken hata düzeltme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Hata düzeltme, eBulma yöneticilerinin Microsoft Purview eBulma'nın (Premium) içeriği düzgün bir şekilde işlemesini engelleyen veri sorunlarını düzeltmesine olanak tanır. Örneğin, parola korumalı dosyalar kilitli veya şifrelenmiş olduğundan işlenemez. Hata düzeltmeyi kullanan eBulma yöneticileri bu tür hatalara sahip dosyaları indirebilir, parola korumasını kaldırabilir ve ardından düzeltilmiş dosyaları karşıya yükleyebilir.

eBulma (Premium) olaylarındaki hatalarla dosyaları düzeltmek için aşağıdaki iş akışını kullanın.

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>İşleme hatalarıyla dosyaları düzeltmek için hata düzeltme oturumu oluşturma

> [!NOTE]
> Aşağıdaki yordam sırasında hata düzeltme sihirbazı herhangi bir zamanda kapatılırsa, **Görünüm** açılan menüsünde **Düzeltmeler'i** seçerek **İşleme** sekmesinden hata düzeltme oturumuna dönebilirsiniz.

1. eBulma (Premium) servis talebinin **İşleme** sekmesinde **, Görünüm** açılan menüsünde **Hatalar'ı** seçin ve ardından **Kapsam** açılan menüsünde bir gözden geçirme kümesi veya büyük/küçük harf tamamını seçin. Bu bölüm, belirli bir gözden geçirme kümesinden gelen tüm hataları veya servis talebi hatalarını görüntüler.

   ![Hata düzeltme.](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Hata türünün veya dosya türünün yanındaki radyo düğmesine tıklayarak düzeltmek istediğiniz hataları seçin.  Aşağıdaki örnekte parola korumalı bir dosyayı düzeltiyoruz.

3. **Yeni hata düzeltme'ye** tıklayın.

    Hata düzeltme iş akışı, hataları olan dosyaların microsoft tarafından sağlanan bir Azure Depolama konumuna kopyalandığı bir hazırlık aşamasıyla başlar, böylece bunları düzeltmek için yerel bilgisayarınıza indirebilirsiniz.

    ![Hata düzeltme hazırlanıyor.](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Hazırlık tamamlandıktan sonra, indirme işlemine devam etmek için **İleri: Dosyaları indir'e** tıklayın.

    ![Dosyaları indirin.](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Dosyaları indirmek **için indirilecek Hedef yolunu** belirtin. Bu, yerel bilgisayarınızdaki dosyanın indirileceği üst klasörün yoludur.  Varsayılan yol olan %USERPROFILE%\Downloads\errors, oturum açmış kullanıcının indirmeler klasörünü gösterir. İsterseniz bu yolu değiştirebilirsiniz. Bunu değiştirirseniz, en iyi performans için yerel bir dosya yolu kullanmanızı öneririz. Uzak ağ yolu kullanmayın. Örneğin, **C:\Düzeltme** yolunu kullanabilirsiniz.

   Üst klasörün yolu otomatik olarak AzCopy komutuna eklenir ( **/Dest** parametresinin değeri olarak).

6. **Panoya kopyala'ya** tıklayarak önceden tanımlanmış komutu kopyalayın. Windows Komut İstemi'ni açın, AzCopy komutunu yapıştırın ve **enter tuşuna** basın.

    ![Hata düzeltmeye hazırlanın.](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > **Dosyaları indir** sayfasında sağlanan komutu başarıyla kullanmak için AzCopy v8.1 kullanmanız gerekir. 10. adımda dosyaları karşıya yüklemek için AzCopy v8.1'i de kullanmanız gerekir. AzCopy'nin bu sürümünü yüklemek için bkz[. Windows'de AzCopy v8.1 ile veri aktarma](/previous-versions/azure/storage/storage-use-azcopy). Sağlanan AzCopy komutu başarısız olursa, lütfen [eBulma'da (Premium) AzCopy sorunlarını giderme](troubleshooting-azcopy.md) bölümüne bakın.

    Seçtiğiniz dosyalar, 5. adımda belirttiğiniz konuma indirilir. Üst klasörde (örneğin, **C:\Düzeltme**) aşağıdaki alt klasör yapısı otomatik olarak oluşturulur:

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *1. alt klasör, 1* . adımda seçtiğiniz kapsama bağlı olarak servis talebi veya gözden geçirme kümesinin kimliğiyle adlandırılır.

    - *Alt klasör 2* , indirilen dosyanın dosya kimliğiyle adlandırılır

    - İndirilen dosya *Alt Klasör 2'de* bulunur ve dosya kimliğiyle de adlandırılır.

    Öğeler **C:\Remediation** üst klasörüne indirildiğinde oluşturulan klasör yolu ve hata dosyası adı örneği aşağıda verilmiştir:

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Birden çok dosya indirilirse, her biri dosya kimliğiyle adlandırılan bir alt klasöre indirilir.

    > [!IMPORTANT]
    > 9. ve 10. adımda dosyaları karşıya yüklediğinizde, düzeltilmiş dosyaların aynı dosya adına sahip olması ve aynı alt klasör yapısında bulunması gerekir. Alt klasör ve dosya adları, düzeltilen dosyayı özgün hata dosyasıyla ilişkilendirmek için kullanılır. Klasör yapısı veya dosya adları değiştirilirse şu hatayı alırsınız: `Cannot apply Error Remediation to the current Workingset`. Herhangi bir sorunu önlemek için, düzeltilmiş dosyaları aynı üst klasörde ve alt klasör yapısında tutmanızı öneririz.

7. Dosyaları indirdikten sonra uygun bir araçla düzeltebilirsiniz. Parola korumalı dosyalar için kullanabileceğiniz çeşitli parola çözme araçları vardır. Dosyaların parolalarını biliyorsanız, bunları açabilir ve parola korumasını kaldırabilirsiniz.

8. eBulma (Premium) ve hata düzeltme sihirbazına dönün ve **ardından İleri: Upload dosyaları'na** tıklayın.  Bu, artık dosyaları karşıya yükleyebileceğiniz bir sonraki sayfaya taşınır.

    ![Dosyaları Upload.](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Düzeltilmiş dosyaların dosyaların **konumuna giden yol** metin kutusunda bulunduğu üst klasörü belirtin. Üst klasör, dosyaları indirdiğinizde oluşturulan alt klasör yapısına sahip olmalıdır.

    Üst klasörün yolu otomatik olarak AzCopy komutuna eklenir ( **/Source** parametresinin değeri olarak).

10. **Panoya kopyala'ya** tıklayarak önceden tanımlanmış komutu kopyalayın. Windows Komut İstemi'ni açın, AzCopy komutunu yapıştırın ve **enter tuşuna** basın. dosyaları karşıya yükleyin.

    ![Azcopy'de düzeltilmiş dosyaların başarıyla karşıya yüklenmesinin sonuçları.](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. AzCopy komutunu çalıştırdıktan sonra **İleri: dosyaları işleme'ye** tıklayın.

    İşlem tamamlandığında, kümeyi gözden geçirebilir ve düzeltilmiş dosyaları görüntüleyebilirsiniz.

## <a name="remediating-errors-in-container-files"></a>Kapsayıcı dosyalarındaki hataları düzeltme

Kapsayıcı dosyasının içeriği (.zip dosyası gibi) eBulma (Premium) tarafından ayıklanamıyorsa kapsayıcılar indirilebilir ve içerik özgün kapsayıcının bulunduğu klasöre genişletilebilir. Genişletilmiş dosyalar, ilk olarak eBulma (Premium) tarafından genişletilmiş gibi üst kapsayıcıya özniteliklendirilir. İşlem, değiştirme dosyası olarak tek bir dosyanın karşıya yüklenmesi dışında yukarıda açıklandığı gibi çalışır.  Düzeltilmiş dosyaları karşıya yüklediğinizde, özgün kapsayıcı dosyasını eklemeyin.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Ayıklanan metni karşıya yükleyerek hataları düzeltme

Bazen bir dosyayı eBulma'nın (Premium) yorumlayabildiği yerel biçime düzeltmek mümkün değildir. Ancak özgün dosyayı, yerel dosyanın özgün metnini içeren bir metin dosyasıyla değiştirebilirsiniz ( *metin katmanı* adı verilen bir işlemde). Bunu yapmak için, bu makalede açıklanan adımları izleyin, ancak özgün dosyayı yerel biçimde düzeltmek yerine, özgün dosyadan ayıklanan metni içeren bir metin dosyası oluşturur ve sonra .txt soneki eklenmiş özgün dosya adını kullanarak metin dosyasını karşıya yüklersiniz. Örneğin, hata düzeltmesi sırasında 335850cc-6602-4af0-acfa-1d14d9128ca2.abc dosya adıyla bir dosya indirirsiniz. Dosyayı yerel uygulamada açar, metni kopyalar ve 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt adlı yeni bir dosyaya yapıştırırsınız. Bunu yaptığınızda, düzeltilmiş metin dosyasını eBulma'ya (Premium) yüklemeden önce yerel biçimdeki özgün dosyayı yerel bilgisayarınızdaki düzeltilmiş dosya konumundan kaldırdığınızdan emin olun.

## <a name="what-happens-when-files-are-remediated"></a>Dosyalar düzeltildiğinde ne olur?

Düzeltilen dosyalar karşıya yüklendiğinde, özgün meta veriler aşağıdaki alanlar dışında korunur:

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Metin
- WordCount
- WorkingsetId

eBulma'daki (Premium) tüm meta veri alanlarının tanımı için bkz. [Belge meta veri alanları](document-metadata-fields-in-advanced-ediscovery.md).