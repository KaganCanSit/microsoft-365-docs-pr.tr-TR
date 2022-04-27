---
title: Paketinizi karşıya yükleyin
description: Uygulamanızı, ikili dosyalarını ve bağımlılıklarını Test Temeli'ne yükleme
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 23c21eae9ad149aea5442c0c8a00f716f3d22506
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099487"
---
# <a name="upload-your-test-base-package-zip"></a>Test Base paketinizi (Zip) yükleyin 

Test Temeli portalı sayfasında, sol gezinti **çubuğundaki Yeni paket** seçeneğine gidin ve ardından Aşağıda gösterildiği gibi Zip **karşıya yükleme deneyimini etkinleştirmek için Eski karşıya yükleme deneyimi'ne** tıklayın:

:::image type="content" alt-text="Yeni bir paket Upload." source="Media/testapplication01.png" lightbox="Media/testapplication01.png":::

:::image type="content" alt-text="İşlemi uygulayın." source="Media/testapplication21.png" lightbox="Media/testapplication21.png":::

Oraya vardıktan sonra, yeni bir paketi karşıya yüklemek için aşağıdaki adımları izleyin.

## <a name="enter-details-for-your-package"></a>Paketinizin ayrıntılarını girin

Test ayrıntıları sekmesinde, paketinizin adını, sürümünü ve diğer ayrıntıları istediğiniz şekilde yazın.

**Kullanıma Uygun** ve **İşlevsel testler** bu pano aracılığıyla yapılabilir.

Aşağıdaki adımlar, paket ayrıntılarınızı doldurma hakkında bir kılavuz sağlar:

1. Paketinize `Package name` verilecek adı alanına girin.

    > [!NOTE]
    > Girilen paket adı ve sürüm bileşimi kuruluşunuzda benzersiz olmalıdır. Bu, aşağıda gösterildiği gibi onay işaretiyle doğrulanır.

    - Bir paketin adını yeniden kullanmak isterseniz, sürüm numarası benzersiz olmalıdır (yani, hiçbir zaman bu adı taşıyan bir paketle kullanılmamıştır).

    - Paket adı + sürüm birleşimi benzersizlik denetimini geçmezse *, "Bu paket sürümüyle paket zaten var"* hata iletisini görürsünüz.

    :::image type="content" alt-text="Paket yönergelerini karşıya yükleme resmi." source="Media/Instructions.png":::

2. "Paket sürümü" alanına bir sürüm girin.

    :::image type="content" alt-text="Paket sürümü." source="Media/ApplicationVersion.png":::

3. Bu pakette çalıştırmak istediğiniz test türünü seçin.

    Kullanıma **Açık (OOB)** testi paketinizi *yükleme*, *başlatma*, *kapatma* ve *kaldırma* işlemlerini gerçekleştirir. Yüklemeden sonra başlatma-kapatma yordamı, tek bir kaldırma çalıştırılmadan önce 30 kez yinelenir.

    Bu OOB testi, Windows derlemeleri karşılaştırmak için paketinizde standart telemetri sağlar.

    **İşlevsel test**, paketinizde karşıya yüklenen test betiklerinizi yürütür. Betikler karşıya yükleme sırasında çalıştırılır ve belirli bir betikteki bir hata, izleyen betiklerin yürütülmesini durdurur.

    > [!NOTE]
    > **Tüm** betikler en fazla 80 dakika boyunca çalışır.

4. İşletim sistemi güncelleştirme türünü seçin.

    - 'Güvenlik güncelleştirmeleri', paketinizin Windows yayın öncesi aylık güvenlik güncelleştirmelerinin artımlı değişim sıklığına göre test edilmesine olanak tanır.
    - 'Özellik güncelleştirmeleri', paketinizin Windows Insider Programı'ndan Windows yayın öncesi iki yıllık özellik güncelleştirmeleri derlemelerine karşı test edilmesine olanak tanır.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="İşletim sistemi güncelleştirme türü." source="Media/OSUpdateType.png":::

5. Güvenlik güncelleştirme testleri için işletim sistemi sürümlerini seçin.

    Çoklu seçim açılan listesinde paketinizin yükleneceği Windows işletim sistemi sürümlerini seçin.

    - Paketinizi yalnızca Windows İstemci işletim sistemlerinde test etmek için menü listesinden uygun Windows İstemci işletim sistemi sürümlerini seçin.
    - Paketinizi yalnızca Windows Server işletim sistemlerinde test etmek için menü listesinden uygun Windows Sunucu işletim sistemi sürümlerini seçin.
    - Paketinizi Windows İstemci ve Windows Sunucusu işletim sistemlerine karşı test etmek için menü listesinden tüm geçerli işletim sistemlerini seçin.

    > [!NOTE]
    > Paketinizi hem Sunucu hem de İstemci işletim sistemiyle test etmek isterseniz lütfen paketin uyumlu olduğundan ve her iki işletim sisteminde de çalıştırılabilir olduğundan emin olun

    :::image type="content" alt-text="İşletim sistemi sürümünü seçme." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Özellik güncelleştirme testleri için seçenekleri belirleyin:

    - "Insider Kanalını Seçin" seçeneğinde `Windows Insider Program Channel` paketlerinizin test edilmesi gereken derleme olarak öğesini seçin.

      Şu anda Insider Beta Kanalında sunulan derlemeleri kullanıyoruz.

    - "İçgörüler için işletim sistemi temelini seçin" seçeneğinde, test sonuçlarınızı karşılaştırmak için temel olarak kullanılacak Windows işletim sistemi sürümünü seçin.

    > [!NOTE]
    > Şu anda Sunucu işletim sistemi için özellik güncelleştirme testlerini DESTEKLEMEYİZ
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Özellik güncelleştirme testi." source="Media/FeatureUpdate.png":::

7. Tamamlanmış bir Test ayrıntıları sayfası şöyle görünmelidir:

    :::image type="content" alt-text="Test ayrıntılarını görüntüleme." source="Media/TestDetails.png":::



## <a name="upload-your-binaries-dependencies-and-scripts"></a>İkili dosyalarınızı, bağımlılıklarınızı ve betiklerinizi Upload

Bu sekmede, test paketinizi çalıştırmak için kullanılan ikili dosyaları, bağımlılıkları ve betikleri içeren tek bir zip paketini karşıya yükleyebilirsiniz.

> [!NOTE]
> Zip paketinin boyutu en az 10 MB ile en fazla 2 GB arasında olmalıdır.

**paket zip dosyasını Upload**

:::image type="content" alt-text="İkili değerlerinizi Upload." source="Media/AddBinaries.png":::

  - Karşıya yüklenen bağımlılıklar test çerçevelerini, betik altyapılarını veya uygulamanızı veya test çalışmalarınızı çalıştırmak için erişilecek verileri içerebilir. Örneğin, tarayıcı tabanlı testler çalıştırmaya yardımcı olmak için Selenium'u ve bir web sürücüsü yükleyicisini karşıya yükleyebilirsiniz.
  - Betik etkinliklerinizin modüler kalmasını sağlamak en iyi yöntemdir. 
    - Betik `Install` yalnızca yükleme işlemlerini gerçekleştirir.
    - Betik `Launch` yalnızca uygulamayı başlatır.
    - Betik `Close` yalnızca uygulamayı kapatır.
    - İsteğe bağlı `Uninstall` betik yalnızca uygulamayı kaldırır.

**Şu anda portal yalnızca PowerShell betiklerini desteklemektedir.**



## <a name="the-tasks-tab"></a>Görevler sekmesi

Görevler sekmesinde, ikili dosyalar sekmesi altında karşıya yüklediğiniz zip klasöründe bulunan test betiklerinizin yollarını sağlamanız beklenir.

  - **Kullanıma Ait Test Betikleri:** Yükleme, başlatma, kapatma ve kaldırma betiklerinizin göreli yollarını yazın. Yükleme betiği için ek ayarlar da seçebilirsiniz.
  - **İşlevsel Test Betikleri:** Karşıya yüklenen her işlevsel test betiğinin göreli yolunu yazın. Düğme kullanılarak ek işlevsel test betikleri ```Add Script``` eklenebilir. En az bir (1) betik gerekir ve en fazla sekiz (8) işlevsel test betiği ekleyebilirsiniz. 
  
    Betikler listelendikleri sırayla çalışır. Belirli bir betikteki bir hata, izleyen betiklerin yürütülmesini durdurur.
    Sağlanan her betik için ek ayarlar seçme seçeneğiniz de vardır.

**Betik yolunu ayarlama**

:::image type="content" alt-text="Test görevinin resmi." source="Media/testtask.png":::

Klasör yapısında göreli yol sağlama örneği aşağıda verilmiştir:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** olurdu. _göreli_ yol olarakScriptX.ps1.
  - **Script.ps1** göreli yol olarak _klasör1/script.ps1_ olacaktır.



## <a name="choose-your-test-options"></a>Test seçeneklerinizi belirleyin. 

Sekme```Test Options```, işlevsel test betiklerini yürütme sırasında Windows Update düzeltme ekinin ne zaman uygulanacağını belirtmek için işlevsel testler yapmak isteyen kullanıcılara yöneliktir.

:::image type="content" alt-text="Test seçeneklerinin resmi. Kullanıma uygun veya işlevsel testler." source="Media/testoptions.png":::

_**Gözden Geçir'i**_ seçerek sonraki sekmeye gidin ve seçtiğiniz test seçeneklerini gözden geçirin.



## <a name="review-your-selections-to-create-your-package"></a>Paketinizi oluşturmak için seçimlerinizi gözden geçirin.

1. Bu sekmede hizmet, test ayrıntılarınızı görüntüler ve hızlı bir tamlık denetimi çalıştırır.

    **Doğrulama başarılı** oldu veya **Doğrulama başarısız oldu** iletisi sonraki adımlara geçip geçemeyeceğinizi gösterir.

2. Test ayrıntılarınızı gözden geçirin ve memnunsanız **Oluştur** düğmesine tıklayın.

    :::image type="content" alt-text="Doğrulamayı görüntüleyin." source="Media/validation.png" lightbox="Media/validation.png":::

3. Bu işlem paketinizi Test Temeli ortamına ekler. Paketiniz başarıyla oluşturulursa, paketinizin Azure'da başarıyla yürütülip yürütülemeyeceğini doğrulayan otomatik bir test tetiklenir.

    :::image type="content" alt-text="Başarılı sonuç." source="Media/successful.png":::

    > [!NOTE]
    > Azure portal, paket doğrulamasının başarılı veya başarısız olduğunu bildiren bir bildirim alırsınız.
    >
    > İşlemin 24 saat kadar sürebileceğini, bu nedenle web sayfanızda etkin değilseniz zaman aşımına uğrar ve bu nedenle bildirim, bu isteğe bağlı çalıştırmanın tamamlandığını size bildirmez.

    - Böyle bir durumda paketinizin durumunu **Paketleri yönet** sekmesinde görüntüleyebilirsiniz.

      :::image type="content" alt-text="Paketleri yönetme resmi." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - Başarılı testler için sonuçları zamanlanmış aralıklarla **Test Özeti**, **Güvenlik Güncelleştirmeleri Sonuçları** ve **Özellik Güncelleştirmeleri Sonuçları** sayfaları aracılığıyla görülebilir ve bunlar genellikle karşıya yüklemenizden birkaç gün sonra başlar.
  
    - Başarısız testler sırasında yeni bir paket yüklemenizi gerektirir. 

      Daha fazla analiz için **test günlüklerini** **Güvenlik güncelleştirme sonuçları** ve **Özellik güncelleştirmeleri sonuçları** sayfalarından indirebilirsiniz.

    - Yinelenen test hatalarıyla karşılaşırsanız lütfen hatanızın ayrıntılarını içeren testbasepreview@microsoft.com ulaşın.

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki bağlantı aracılığıyla İçerik Yönergelerimizi keşfedin.

> [!div class="nextstepaction"]
> [Sonraki adım](contentguideline.md)
