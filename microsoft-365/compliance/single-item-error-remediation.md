---
title: Tek öğe hatası düzeltmesi
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
description: Toplu hata düzeltme işlemini takip etmek zorunda kalmadan, Advanced eDiscovery gözden geçirme kümesinde yer alan bir belgeyi işleme hatasını düzeltebilirsiniz.
ms.openlocfilehash: c816ef1e3fd28299bb316e51aa434a8f08d544a0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988093"
---
# <a name="single-item-error-remediation-in-advanced-ediscovery"></a>Düzeltmede tek öğe Advanced eDiscovery

Hata düzeltmesi, Advanced eDiscovery kullanıcıların içeriği düzgün işlemesini önleyen veri Advanced eDiscovery düzeltme olanağı sağlar. Örneğin, parola korumalı dosyalar kilitli ya da şifrelenmiş olduğundan işlenemez. Daha önce, bu iş akışını kullanarak yalnızca toplu hataları [düzeltebilirsiniz](error-remediation-when-processing-data-in-advanced-ediscovery.md). Ancak bazen, araştırılıyor olan durumla ilgili olarak bu dosyalardan herhangi biri hassas olduğunda emin değilseniz birden çok dosyada oluşan hataları düzeltmek mantıklı değildir. Ayrıca, yanıt süresiyle ilgili önceden karar ver verebilirsiniz ve buna yardımcı olmak için dosya meta verilerini (dosya konumu veya erişimi olanlar gibi) gözden geçirme fırsatına sahip olmadan önce hataları düzeltmek de mantıklı olmaz. Tek öğe hata *düzeltmesi* adı verilen yeni bir özellik, eBulma yöneticilerine işleme hatası olan dosyaların meta verilerini görüntüleme olanağı verir ve gerekirse doğrudan gözden geçirme kümesinde hatayı düzeltebilirsiniz. Bu makalede, bir gözden geçirme kümesinde işleme hataları ile dosyaların nasıl tanım, yoksayma ve düzeltme işlemleri olduğu açıklanmıştır.

## <a name="identify-documents-with-errors"></a>Hatalı belgeleri tanımlama

Gözden geçirme kümesinde işleme hataları olan belgeler artık (başlıkla) tanımlanır. Hatayı düzeltmek veya yoksayabilirsiniz. Aşağıdaki ekran görüntüsü, parola korumalı bir gözden geçirme kümesinde bir Word belgesinin işleme hatasını gösterir. Ayrıca, işleme hatalarının olduğu belgelerin dosya meta verilerini görüntü ola bildirimini de edin.

![İşleme hatası olan belge için görüntülenen başlık.](../media/SIERimage1.png)

Gözden geçirme kümesinde belgeleri sorgularken, İşleme **durumu** koşulsunu kullanarak da [işleme hataları olan belgeleri arayabilirsiniz](review-set-search.md).

![Hata belgelerini aramak için İşleme durumu koşullarını kullanın.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Hataları yoksayma

İşleme hatası başlığında Yoksay'a **tıklayarak işleme** hatasını yoksayabilirsiniz. Bir hatayı yoksaymasanız, belge toplu hata [düzeltme iş akışından kaldırılır](error-remediation-when-processing-data-in-advanced-ediscovery.md). Hata yoksayıldıktan sonra, belge başlığı renk değiştirir ve işleme hatasının yoksayıldı olduğunu gösterir. Geri Al'a tıklayarak, istediğiniz zaman hatayı yoksayma kararını geri **alabilirsiniz**.

![İşleme hatasını yoksaymak için Yoksay'a tıklayın.](../media/SIERimage3.png)

Gözden geçirme kümesinde belgeleri sorgularken Yoksayılan işleme hataları koşulsunu kullanarak, işleme hatası  olan tüm belgeleri de arayabilirsiniz.

![Yoksayılan hata belgelerini aramak için Yoksayılan işleme hataları durumunu kullanın.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Hatalı bir belgeyi düzeltme

Bazen belgelerde bir işlem hatasını düzeltmek (parolayı kaldırarak, şifreli bir dosyanın şifresini çözerek veya bozuk bir belgeyi kurtararak) ve sonra düzeltilen belgeyi gözden geçirme kümesine eklemeniz gerekebilir. Bu, hata belgesini gözden geçirme kümesinde diğer belgelerle birlikte gözden geçirmenizi ve dışarı aktarmayı sağlar. 

Tek bir belgeyi düzeltmek için şu adımları izleyin:

1. **Dosyanın** >  **bir kopyasını yerel** bilgisayara indirmek için Özgün dosyayı indir'e tıklayın.

   ![Belgeyi işleme hatasıyla birlikte indirin.](../media/SIERimage5.png)

2. Dosyada çevrimdışı hatayı düzeltmek. Şifre çözme yazılımı gerektiren şifrelenmiş dosyalar için parola korumasını kaldırmak için, parolayı girin ve dosyayı kaydedin veya parola kırıcı kullanın. Dosyayı düzeltmek için bir sonraki adıma geçin.

3. Gözden geçirme kümesinde, düzelttikleri işlem hatasını olan dosyayı seçin ve sonra **Düzeltme'ye tıklayın**.

   ![Belgenin iş hatasını olan başlıkta Düzeltme'yi tıklatın.](../media/SIERimage6.png)


4. **Gözat'a** tıklayın, yerel bilgisayarınızda düzeltilen dosyanın bulunduğu konuma gidin ve dosyayı seçin.

   ![Gözat'a tıklayın ve yerel bilgisayarınızdan düzeltmiş dosyayı seçin.](../media/SIERimage7.png)

    Düzeltilen dosya seçidikten sonra, gözden geçirme kümesine otomatik olarak yüklenir. Dosyanın işleme durumunu izleyebilirsiniz.

    ![Düzeltme işleminin durumu görüntülenir.](../media/SIERimage8.png)

   İşlem tamamlandıktan sonra düzeltili belgeyi görüntüebilirsiniz.

    ![Düzeltlenmiş dosyayı gözden geçirme kümesinde yerel biçimde görüntüebilirsiniz.](../media/SIERimage9.png)

Bir belge düzeltilene kadar neler olduğu hakkında daha fazla bilgi için bkz [. Dosyalar düzeltilince ne olur](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated)?

## <a name="search-for-remediated-documents"></a>Düzeltilenmiş belgeleri arama

Anahtar sözcükler koşulu kullanarak düzeltmiş ve şu özelliği:değer çifti: **IsFromErrorRemediation:true** değerini belirterek gözden geçirme kümesinde tüm belgeleri arayabilirsiniz. Bu özellik, gözden geçirme kümesinden belge dışarı aktarsanız da dışarı aktarma yükleme dosyasında kullanılabilir.
