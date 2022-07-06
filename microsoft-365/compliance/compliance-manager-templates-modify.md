---
title: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirme
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirme hakkında bilgi edinin.
ms.openlocfilehash: f21ff61f6bb06f00d1db8381e3760e7c4b5343aa
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630421"
---
# <a name="modify-assessment-templates-in-microsoft-purview-compliance-manager"></a>Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirme

Uyumluluk Yöneticisi'nde değerlendirmelerle çalışırken, oluşturduğunuz bir değerlendirme şablonunu değiştirmek isteyebilirsiniz. bu işlem, şablon verilerinizle birlikte biçimlendirilmiş bir Excel dosyasını karşıya yükleyebilmek için şablon [oluşturma](compliance-manager-templates-create.md) işlemine benzer.

Ancak, dosyanızı var olan şablon verilerinde yapılan değişikliklerle biçimlendirdiğinizde bilmeniz gereken ayrıntılar vardır. **Saklamak istediğiniz mevcut verilerin üzerine yazmadığınızdan emin olmak için bu yönergeleri dikkatle gözden geçirmenizi öneririz.**

Bu elektronik tablonun biçimi hakkında daha fazla bilgi edinmek için bkz. [Excel ile şablon verilerinizi biçimlendirme](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Var olan bir şablonu değiştirmek için Excel dosyanızı biçimlendirme

**Değerlendirme şablonları** sayfanızdan, değiştirmek istediğiniz şablonu seçin ve bu şablonun ayrıntılar sayfası açılır. Ardından **Excel'e Aktar'ı** seçin. Tüm şablon verilerinizi içeren bir Excel dosyası indirilir. Dosyayı yerel makinenize kaydedin.

Bu dosyayla çalışmak için, ihtiyacınız olan yönergeleri hızla bulmak için aşağıdaki bölüme atlayın:

- [Ana şablon özniteliklerini düzenleme](#edit-the-main-template-attributes)
- [İyileştirme eylemi ekleme](#add-an-improvement-action)
- [İyileştirme eyleminin bilgilerini düzenleme](#edit-an-improvement-actions-information)
- [İyileştirme eyleminin adını değiştirme](#change-an-improvement-actions-name)
- [İyileştirme eylemini kaldırma](#remove-an-improvement-action)
- [Denetimi kaldırma](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Ana şablon özniteliklerini düzenleme

**Şablonlar** sekmesinde **başlık sütunundaki**, **inScopeServices** sütunundaki ve eklemiş olabileceğiniz diğer sütunlardaki her şeyi düzenleyebilirsiniz. Ancak **, ürün** veya **sertifikasyon** sütunlarında hiçbir şeyi düzenleyemezsiniz.

### <a name="add-an-improvement-action"></a>İyileştirme eylemi ekleme

1. **Eylemler** sekmesine gidin. Bilgilerinizi, mevcut eylemlerinizin altındaki ilk boş satırdaki gerekli alanlara ekleyin.
2. **ControlFamily** sekmenize gidin. geliştirme eyleminizin eşlenmesi denetimini içeren satırı bulun. Yeni eyleminizi bu satırdaki **controlActionTitle** sütununa ekleyin (bu alandaki birden çok eylemi iki noktalı virgülle ayırmayı unutmayın; aralarında boşluk yoktur).
3. Elektronik tablonuzu kaydedin.

### <a name="edit-an-improvement-actions-information"></a>İyileştirme eyleminin bilgilerini düzenleme

*Başlığı dışında* herhangi bir geliştirme eyleminin bilgilerini değiştirebilirsiniz. B sütunlarından herhangi bir hücreyi düzenleyebilirsiniz ve dosyayı şablona geri aktardığınızda, bu şablondaki iyileştirme eylemleri artık güncelleştirilmiş verileri içerir.

Bunu yaparsanız, Uyumluluk Yöneticisi bunu yeni bir geliştirme eylemi olarak değerlendirdiğinden **actionTitle** (A sütunu) öğesini düzenleyemezsiniz. İyileştirme eyleminin adını değiştirmek istiyorsanız aşağıdaki yönergelere hemen bakın.

### <a name="change-an-improvement-actions-name"></a>İyileştirme eyleminin adını değiştirme

İyileştirme eyleminin adını değiştirmek istiyorsanız, var olan bir adı yeni bir adla değiştirdiğiniz elektronik tabloda açıkça belirtmiş olmanız gerekir. Şu adımları izleyin:

1. Elektronik tablonuzun **Eylemler** sekmesinde, A sütunundan sonra elektronik tabloya yeni bir sütun ekleyin.
2. Şimdi B sütunu olan bu yeni sütunda, üst bilgisi olarak 1. **satıra koyun: oldActionTitle**.
3. A sütununun içeriğini kopyalayın ve B sütununa yapıştırın. Bu, değiştirmek istediğiniz mevcut geliştirme eylemi başlıklarınızı B sütununa yerleştirir.
4. A sütununda **actionTitle**, eski adı silin ve iyileştirme eyleminiz için yeni adla değiştirin.

Denetimlerde başvurulduğunda tanınması için hem geliştirme eylemleriniz hem de Microsoft eylemleri için eylem başlıklarının İngilizce yazılması gerektiğini unutmayın.

### <a name="remove-an-improvement-action"></a>İyileştirme eylemini kaldırma

Şablondan bir iyileştirme eylemini kaldırmak için, şablona başvuran her denetimden kaldırmanız gerekir. Elektronik tablonuzu değiştirmek için aşağıdaki adımları izleyin:

1. **ControlFamily** sekmesinde, kaldırmak istediğiniz geliştirme eyleminin başlığını arayın.
2. İyileştirme eyleminin başlığını göründüğü hücrelerde silin. Geliştirme eylemi söz konusu satırdaki tek eylemse, satırın tamamını silin (denetimi kaldırır).
3. **Eylemler** sekmesinde, sildiğiniz geliştirme eylemini içeren satırı silin.
4. Elektronik tablonuzu kaydedin.

Elektronik tablonuzu şablona geri aktardığınızda, geliştirme eyleminiz şablondan kaldırılır.

Şablondan iyileştirme eylemini kaldırmak, geliştirme eylemini Uyumluluk Yöneticisi'nden tamamen kaldırmaz. Bu eyleme başka bir şablon tarafından başvurulabilir.

### <a name="remove-a-control"></a>Denetimi kaldırma

Denetimi kaldırmak için aşağıdaki adımları izleyerek elektronik tablonuzu değiştirin ve ardından elektronik tablonuzu yeniden içeri aktarın:

1. **ControlFamily** sekmesinde, kaldırmak istediğiniz denetimi **controlName** sütununda bulun.
2. Bu denetimin satırını silin.
    - Bu silinen denetim başka bir denetim tarafından başvurulmayan iyileştirme eylemleri içeriyorsa, bu iyileştirme eylemlerini **Eylemler** sekmesinden kaldırmanız gerekir. Aksi takdirde doğrulama hatası alırsınız.

3. Elektronik tablonuzu kaydedin.

Elektronik tablonuzu şablona geri aktardığınızda, denetiminiz şablondan kaldırılır.

## <a name="modify-template-info-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde şablon bilgilerini değiştirme

Excel dosyanız tamamlandıktan ve kaydedildikten sonra aşağıdaki adımları izleyin.

1. Değerlendirme şablonu sayfasını yeniden açın ve şablonunuzu seçin. Şablonunuzun ayrıntılar sayfasında Şablonu **değiştir'i** seçerek değişiklik sihirbazını başlatın.
2. **Dosyayı karşıya yükle** ekranında **Gözat'ı** seçerek Excel dosyanızı bulun ve karşıya yükleyin.
3. Dosyanızla ilgili bir sorun yoksa, bir sonraki ekranda karşıya yüklenen dosyanın adı gösterilir. Devam etmek için **İleri'yi** seçin (dosyayı değiştirmeniz gerekiyorsa **Farklı bir dosyayı karşıya yükle'yi** seçin).
    - Dosyanızla ilgili bir sorun varsa, en üstteki hata iletisi sorunun ne olduğunu açıklar. Dosyanızı düzeltmeniz ve yeniden karşıya yüklemeniz gerekir. Elektronik tablonuz yanlış biçimlendirilirse veya belirli alanlarda geçersiz bilgiler varsa hatalar oluşur.

4. **Gözden geçir ve bitir** ekranı, iyileştirme eylemlerinin ve denetimlerinin sayısını ve şablonun en yüksek puanını gösterir. Onaylamaya hazır olduğunuzda **İleri'yi** seçin.
5. Son ekran, şablonun değiştirildiğini onaylar. **Sihirbazdan çıkmak için Bitti'yi** seçin.

Şablonunuz artık yaptığınız değişiklikleri içerecektir. Bu değiştirilen şablonu kullanan tüm değerlendirmelerde artık bekleyen güncelleştirmeler gösterilir ve şablonda yapılan değişiklikleri yansıtmak için değerlendirmelerdeki güncelleştirmeleri kabul etmeniz gerekir. [Değerlendirme güncelleştirmeleri](compliance-manager-assessments.md#accept-updates-to-assessments) hakkında daha fazla bilgi edinin.

> [!NOTE]
> Uyumluluk Yöneticisi'ni İngilizce dışında bir dilde kullanıyorsanız, şablonu Excel'e aktardığınızda bazı metinlerin İngilizce göründüğünü fark edersiniz. Denetimlerin tanınması için eylemlerin başlıkları (hem geliştirme eylemleriniz hem de uygun olduğunda Microsoft eylemleri) İngilizce olmalıdır. Bir eylem başlığında değişiklik yaparsanız, dosyanın doğru içeri aktarılması için bunu İngilizce yazdığınızdan emin olun.
