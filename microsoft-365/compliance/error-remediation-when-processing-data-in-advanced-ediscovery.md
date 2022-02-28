---
title: Veri işleme hatası düzeltmesi
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
description: İçerik düzgün işlenebilir ve düzgün bir şekilde işlenebilirken Advanced eDiscovery hataları düzeltmek için hata düzeltmeyi nasıl kullanabileceğinizi öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: d0dabe5a16ff2b9b67b5f282401806daff8f82ea
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985565"
---
# <a name="error-remediation-when-processing-data"></a>Veri işleme hatası düzeltmesi

Hata düzeltmesi, eBulma yöneticilerinin içeriği düzgün bir şekilde işlemesini Advanced eDiscovery veri sorunlarını düzeltme olanağı sağlar. Örneğin, parola korumalı dosyalar kilitlendiğinden veya şifrelendiğinden işlenemez. eBulma yöneticileri hata düzeltmeyi kullanarak bu tür hatalara sahip dosyaları indirebilir, parola korumasını kaldırabilir ve sonra düzeltilmemiş dosyaları karşıya yükleyebilir.

bazı durumlarda hatalı dosyaları düzeltmek için aşağıdaki iş Advanced eDiscovery kullanın.

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>İşleme hatalarının olduğu dosyaları düzeltmek için hata düzeltme oturumu oluşturma

> [!NOTE]
> Aşağıdaki yordam sırasında hata düzeltme sihirbazı herhangi bir zamanda kapatılırsa, Görünüm açılan menüsünde Düzeltmeler'i seçerek İşleme sekmesindeki hata düzeltme oturumuna dönebilirsiniz. 

1. çalışma **durumuna** yönelik Advanced eDiscovery sekmesinde, Görünüm açılan menüsünde Hatalar'ı seçin  ve ardından Kapsam  açılan menüsünde bir gözden geçirme kümesi veya tüm büyük/küçük harf seçeneğini belirleyin. Bu bölümde, belirli bir gözden geçirme kümesinden gelen büyük/küçük harf hatasının tüm hataları görüntülenir.

   ![Hata düzeltme.](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Düzeltmek istediğiniz hataları, hata türü veya dosya türünün yanındaki radyo düğmesine tıklayarak seçin.  Aşağıdaki örnekte, parola korumalı bir dosya düzeltildi.

3. Yeni **hata düzeltme'ye tıklayın**.

    Hata düzeltme iş akışı, hatalı dosyaların Microsoft tarafından sağlanan bir Azure Depolama Depolama konuma kopyalanır ve böylece düzeltmek için bunları yerel bilgisayarınıza indirebilirsiniz.

    ![Hata düzeltmesi hazırlanıyor.](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Hazırlık tamamlandıktan sonra, Sonraki **: İndirme işlemine devam etmek için** dosyaları indir'e tıklayın.

    ![Dosyaları indirin.](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Dosyaları indirmek için, İndirme **hedefi yolunu belirtin**. Bu, yerel bilgisayarınızdan dosyanın indirilecek olduğu üst klasörün yoludur.  %USERPROFILE%\Downloads\errors varsayılan yol, oturum açan kullanıcının indirmeler klasörüne gösterir. İsterseniz bu yolu değiştirebilirsiniz. Değiştirdiğiniz bir dosyayı kullanıyorsanız, en iyi performans için yerel bir dosya yolu kullanmanız önerilir. Uzak ağ yolu kullanmama. Örneğin, **C:\Düzeltme yolunu kullanabilirsiniz**.

   Üst klasörün yolu otomatik olarak AzCopy komutuna eklenir ( **/Dest parametresinin değeri** olarak).

6. Panoya kopyala'ya tıklayarak önceden **tanımlanmış komutu kopyalayın**. DosyaLa Windows İstemi'nde AzCopy komutunu yapıştırın ve Enter tuşuna **basın**.

    ![Hata düzeltme için hazırlanma.](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > Dosyaları indir sayfasında sağlanan komutu başarılı bir şekilde kullanmak için AzCopy v8.1 **kullanmalıdır** . 10. adımda dosyaları karşıya yüklemek için AzCopy v8.1'i de kullanmalıdır. AzCopy'nin bu sürümünü yüklemek için bkz. [AzCopy v8.1 ile veri aktarma Windows](/previous-versions/azure/storage/storage-use-azcopy). Sağlanan AzCopy komutu başarısız olursa, lütfen [Aşağıdakiler'de AzCopy sorunlarını giderme Advanced eDiscovery](troubleshooting-azcopy.md).

    Seçtiğiniz dosyalar 5. adımda belirttiğiniz konuma indirilir. Üst klasörde (örneğin, **C:\Düzeltme**), aşağıdaki alt klasör yapısı otomatik olarak oluşturulur:

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *1.* adımda seçtiğiniz kapsama bağlı olarak, alt klasör 1, vakanın kimliğiyle veya gözden geçirme kümesiyle adlandırılmıştır.

    - *Alt klasör 2* , indirilen dosyanın dosya kimliğiyle adlandırılmıştır

    - İndirilen dosya Alt klasör *2'de yer alan* ve dosya kimliğiyle de adlandırılmıştır.

    Burada, öğeler **C:\Remediation** üst klasörüne indirilirken oluşturulan klasör yolu ve hata dosyası adı örneği:

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Birden çok dosya indirilirse, bunların her biri dosya kimliğiyle adlandırılmış bir alt klasöre indirilir.

    > [!IMPORTANT]
    > 9. ve 10. adımda dosyaları karşıya yüklerken, düzeltici dosyaların aynı dosya adı aynı olması ve aynı alt klasör yapısında yer alıyor olması gerekir. Düzeltilen dosyayı özgün hata dosyasıyla ilişkilendirilmiş alt klasör ve dosya adları kullanılır. Klasör yapısı veya dosya adları değiştirilirse, şu hatayı alırsınız: `Cannot apply Error Remediation to the current Workingset`. Herhangi bir sorun önlemek için, düzeltilen dosyaları aynı üst klasör ve alt klasör yapısında tutmanız önerilir.

7. Dosyaları indirdikten sonra, uygun bir araçla düzeltmeniz gerekir. Parola korumalı dosyalar için, kullanabileceğiniz çeşitli parola kırmak araçları vardır. Dosyaların parolalarını biliyorsanız, bunları açabilir ve parola korumasını kaldırabilirsiniz.

8. Düzeltme sihirbazına Advanced eDiscovery dönebilirsiniz ve sonra da Sonraki: Dosyaları düzeltme **Upload tıklatın**.  Bu, dosyaları artık karşıya yükleyebilirsiniz sonraki sayfaya taşınır.

    ![Upload'i seçin.](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Düzeltilen dosyaların dosya konumu yolu metin kutusunda **, düzeltilen dosyaların bulunduğu üst klasörü** belirtin. Bir kez daha, üst klasörün dosyaları indirdiğiniz zaman oluşturulan alt klasör yapısıyla aynı olması gerekir.

    Üst klasörün yolu otomatik olarak AzCopy komutuna eklenir ( **/Source parametresinin değeri olarak** ).

10. Panoya kopyala'ya tıklayarak önceden **tanımlanmış komutu kopyalayın**. DosyaLa Windows İstemi'nde AzCopy komutunu yapıştırın ve Enter tuşuna **basın**. dosyaları karşıya yükleyin.

    ![Azcopy'de düzeltilenmiş dosyaların başarılı bir şekilde karşıya yüklemenin sonuçları.](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. AzCopy komutunu çalıştırdikten sonra, Sonraki **: Dosyaları işleme'ye tıklayın**.

    İşleme tamamlandığında, kümeyi gözden geçirme ve düzeltilen dosyaları görüntüleme makalesini gözden geçirebilirsiniz.

## <a name="remediating-errors-in-container-files"></a>Kapsayıcı dosyalarda hataları düzeltme

Kapsayıcı dosyasının (.zip dosyası gibi) içeriği Advanced eDiscovery tarafından ayıklanmayacak durumlarda, kapsayıcılar indirilebilir ve içindekiler özgün kapsayıcının bulunduğu klasöre genişletilir. Genişletilmiş dosyalar, ilk olarak Advanced eDiscovery tarafından genişletilir gibi üst kapsayıcıyla Advanced eDiscovery. İşlem, değiştirme dosyası olarak tek bir dosyayı karşıya yükleme işlemi dışında yukarıda açıklandığı gibi çalışır.  Düzeltlenmiş dosyaları karşıya yüklerken, özgün kapsayıcı dosyayı dahil etme.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Ayıklanan metni karşıya yükerek hataları düzeltme

Bazen dosyayı yorumlandır en iyi yorumlandıranın yerel Advanced eDiscovery düzeltmek mümkün olmaz. Ancak, özgün dosyayı yerel dosyanın özgün metnini içeren bir metin dosyasıyla değiştirebilirsiniz (metin yer paylaşımı olarak adlandırılan *işlemde*). Bunu yapmak için, bu makalede açıklanan adımları izleyin ancak özgün dosyayı yerel biçimde düzeltmek yerine, özgün dosyadan ayıklanan metni içeren bir metin dosyası oluşturabilir ve sonra da .txt soneki ekinde özgün dosya adını kullanarak metin dosyasını karşıya yükleyebilirsiniz. Örneğin, hata düzeltmesi sırasında 335850cc-6602-4af0-acfa-1d14d9128ca2.abc adlı bir dosyayı indirmişsiniz. Dosyayı yerel uygulamada açar, metni kopyalayıp Dosya adında yeni bir dosyaya 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt. Bunu yapmak için, düzeltilen metin dosyasını bilgisayarınıza yüklemeden önce özgün dosyayı yerel bilgisayarınızda düzeltilen dosyanın bulunduğu konumdan yerel biçimde Advanced eDiscovery.

## <a name="what-happens-when-files-are-remediated"></a>Dosyalar düzeltilince ne olur?

Düzeltlenmiş dosyalar karşıya yüklendiklerinde, aşağıdaki alanlar dışında özgün meta veriler korunur:

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Metin
- WordCount
- WorkingsetId

Belge kitaplığında tüm meta veri alanlarının tanımı Advanced eDiscovery bkz[. Belge meta veri alanları](document-metadata-fields-in-advanced-ediscovery.md).