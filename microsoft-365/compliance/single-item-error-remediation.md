---
title: Tek öğede hata düzeltme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Toplu hata düzeltme işlemini izlemek zorunda kalmadan eBulma (Premium) içindeki bir gözden geçirme kümesindeki bir belgedeki işleme hatasını düzeltebilirsiniz.
ms.openlocfilehash: cb1b7248ff02a4aafce529b764efdf7408a05386
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622183"
---
# <a name="single-item-error-remediation-in-ediscovery-premium"></a>eBulma'da tek öğe hatası düzeltmesi (Premium)

Hata düzeltme, Microsoft Purview eKeşif (Premium) kullanıcılara eKeşif'in (Premium) içeriği düzgün bir şekilde işlemesini engelleyen veri sorunlarını düzeltme olanağı sağlar. Örneğin, parola korumalı dosyalar kilitli veya şifrelenmiş olduğundan işlenemez. Daha önce bu [iş akışını](error-remediation-when-processing-data-in-advanced-ediscovery.md) kullanarak hataları yalnızca toplu olarak düzeltebiliyorsunuz. Ancak bazen, bu dosyalardan herhangi birinin araştırdığınız olaya yanıt vermediğinden emin olmadığınız durumlarda birden çok dosyadaki hataları düzeltmek mantıklı değildir. Yanıt verme konusunda önceden karar vermenize yardımcı olmak için dosya meta verilerini (dosya konumu veya erişimi olan kişiler gibi) gözden geçirme fırsatınız olmadan önce hataları düzeltmeniz de mantıklı olmayabilir. *Tek öğe hatasını düzeltme* adlı yeni bir özellik, eBulma yöneticilerine işleme hatası olan dosyaların meta verilerini görüntüleme ve gerekirse hatayı doğrudan gözden geçirme kümesinde düzeltme olanağı sağlar. Makalede, bir gözden geçirme kümesindeki işleme hatalarıyla dosyaları tanımlama, yoksayma ve düzeltme işlemleri açıklanır.

## <a name="identify-documents-with-errors"></a>Hataları olan belgeleri tanımlama

Gözden geçirme kümesinde işleme hataları olan belgeler artık tanımlanır (başlıkla). Hatayı düzeltebilir veya yoksayabilirsiniz. Aşağıdaki ekran görüntüsünde, parola korumalı bir gözden geçirme kümesindeki bir Word belgesinin işleme hatası başlığı gösterilmektedir. Ayrıca, işleme hataları olan belgelerin dosya meta verilerini görüntüleyebileceğinize de dikkat edin.

![İşleme hatası olan belge için başlık görüntüleniyor.](../media/SIERimage1.png)

Ayrıca, [bir gözden geçirme kümesindeki belgeleri sorgularken](review-set-search.md) **İşleme durumu** koşulunu kullanarak işleme hataları olan belgeleri de arayabilirsiniz.

![Hata belgelerini aramak için İşlem durumu koşulunu kullanın.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Hataları yoksay

İşleme hatası başlığında Yoksay'a tıklayarak bir işleme hatasını **yoksayabilirsiniz** . Bir hatayı yoksaydığınızda, belge [toplu hata düzeltme iş akışından](error-remediation-when-processing-data-in-advanced-ediscovery.md) kaldırılır. Bir hata yoksayıldıktan sonra, belge başlığı rengi değişir ve işleme hatasının yoksayıldığını gösterir. İstediğiniz zaman Geri Al'a tıklayarak hatayı yoksayma kararını **geri alabilirsiniz**.

![İşleme hatasını yoksaymak için Yoksay'a tıklayın.](../media/SIERimage3.png)

Ayrıca, gözden geçirme kümesindeki belgeler sorgulanırken *Yoksayılan işleme hataları koşulu kullanılarak yoksayılan işleme hatası* olan tüm belgeleri de arayabilirsiniz.

![Yoksayılan hata belgelerini aramak için Yoksayılan işleme hataları koşulunu kullanın.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Belgeyi hatalarla düzeltme

Bazen belgelerdeki bir işleme hatasını düzeltmeniz (parolayı kaldırarak, şifrelenmiş bir dosyanın şifresini çözerek veya bozuk bir belgeyi kurtararak) ve ardından düzeltilen belgeyi gözden geçirme kümesine eklemeniz gerekebilir. Bu, hata belgesini gözden geçirmenize ve gözden geçirme kümesindeki diğer belgelerle birlikte dışarı aktarmanıza olanak tanır. 

Tek bir belgeyi düzeltmek için şu adımları izleyin:

1. Dosyanın bir kopyasını yerel bir bilgisayara indirmek için **Özgün dosyayı** **indir'e** >  tıklayın.

   ![İşleme hatası içeren belgeyi indirin.](../media/SIERimage5.png)

2. Dosyadaki hatayı çevrimdışı olarak düzeltin. Şifre çözme yazılımı gerektiren şifrelenmiş dosyalar için parola korumasını kaldırmak için parolayı sağlayın ve dosyayı kaydedin veya parola cracker kullanın. Dosyayı düzeltdikten sonra sonraki adıma geçin.

3. Gözden geçirme kümesinde, düzeltmiş olduğunuz işleme hatasını içeren dosyayı seçin ve ardından **Düzeltme'ye** tıklayın.

   ![Belgenin başlığında Düzeltme'ye ve işleme hatasına tıklayın.](../media/SIERimage6.png)


4. **Gözat'a** tıklayın, düzeltilmiş dosyanın yerel bilgisayarınızdaki konumuna gidin ve dosyayı seçin.

   ![Gözat'a tıklayın ve yerel bilgisayarınızda düzeltilmiş dosyayı seçin.](../media/SIERimage7.png)

    Düzeltilen dosya seçtikten sonra, otomatik olarak gözden geçirme kümesine yüklenir. Dosyanın işleme durumunu izleyebilirsiniz.

    ![Düzeltme işleminin durumu görüntülenir.](../media/SIERimage8.png)

   İşlem tamamlandıktan sonra, düzeltilmiş belgeyi görüntüleyebilirsiniz.

    ![Düzeltilmiş dosyayı gözden geçirme kümesinde yerel biçimde görüntüleyebilirsiniz.](../media/SIERimage9.png)

Belge düzeltildiğinde ne olacağı hakkında daha fazla bilgi için bkz. [Dosyalar düzeltildiğinde ne olur](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated)?

## <a name="search-for-remediated-documents"></a>Düzeltilmiş belgeleri arama

**Anahtar Sözcükler** koşulu kullanılarak ve şu özellik:değer çifti belirtilerek düzeltilen bir gözden geçirme kümesindeki tüm belgeleri arayabilirsiniz: **IsFromErrorRemediation:true**. Bu özellik, belgeleri bir gözden geçirme kümesinden dışarı aktardığınızda dışarı aktarma yükleme dosyasında da kullanılabilir.
