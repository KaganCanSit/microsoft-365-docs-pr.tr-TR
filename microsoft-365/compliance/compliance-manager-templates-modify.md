---
title: Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirme
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirmeyi anlama.
ms.openlocfilehash: 539da4118843e8d72ead07b06a351d2245c2f6d9
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "62988797"
---
# <a name="modify-assessment-templates-in-microsoft-compliance-manager"></a>Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını değiştirme

Uyumluluk Yöneticisi'nde değerlendirmelerle çalışırken, oluşturduğunuz bir değerlendirme şablonunu değiştirmek istiyor olabilirsiniz. İşlem, şablon [verilerinizle](compliance-manager-templates-create.md) biçimlendirilmiş bir Excel karşıya yüklediğiniz şablon oluşturma sürecine benzer.

Bununla birlikte, dosyanızı var olan şablon verisinde yapılan değişikliklerle biçimlendiren ve dikkat dikkat gereken ayrıntılar vardır. **Korumak istediğiniz verilerin üzerine yazılmaması için bu yönergeleri dikkatle gözden geçirmenizi öneririz.**

Bu elektronik tablonun biçimi hakkında daha fazla bilgi edinmek için bkz[. Elektronik tabloyla şablon Excel](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Var olan Excel değiştirmek için Excel dosyanızı biçimlendirme

Bir  **araya getirme şablonlarısayfanıza** , değiştirmek istediğiniz şablonu seçin; bu şablon ayrıntılar sayfasını da getirir. Ardından,  **RaporaPort'Excel**. Tüm Excel verilerini indiren bir dosya indirecek. Dosyayı yerel makinenize kaydedin.

Bu dosyayla çalışmak için, aşağıdaki bir bölüme atlayıp ihtiyacınız olan yönergeleri hızla bulun:

- [Ana şablon özniteliklerini düzenleme](#edit-the-main-template-attributes)
- [Geliştirme eylemi ekleme](#add-an-improvement-action)
- [Geliştirme eyleminin bilgilerini düzenleme](#edit-an-improvement-actions-information)
- [Geliştirme eyleminin adını değiştirme](#change-an-improvement-actions-name)
- [Geliştirme eylemlerini kaldırma](#remove-an-improvement-action)
- [Denetimi kaldırma](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Ana şablon özniteliklerini düzenleme

Şablonlar **sekmesinde** başlık sütununda, **inScopeServices** sütununda ve başka  herhangi bir sütunda eklenen her şeyi düzenleyebilirsiniz. Bununla birlikte, ürün veya sertifika sütunlarında hiçbir **şeyi** **düzenleyemezsiniz** .

### <a name="add-an-improvement-action"></a>Geliştirme eylemi ekleme

1. Eylemler **sekmesine** gidin. Mevcut eylemlerinizin altındaki ilk boş satıra gerekli alanlara bilgi ekleyin.
2. **ControlFamily sekmenize** gidin. Geliştirme işlemi eşlemenizin bulunduğu satırı bulun. Yeni eyleminizi bu satırdaki **controlActionTitle** sütununa ekleyin (bu alanda birden çok eylemi iki noktalı virgülle ayırmayı unutmayın, arasında boşluk yoktur).
3. Elektronik tablonuzu kaydedin.

### <a name="edit-an-improvement-actions-information"></a>Geliştirme eyleminin bilgilerini düzenleme

Geliştirme eyleminin başlığı dışında bilgilerini *değiştirebilirsiniz*. B sütunlarından herhangi bir hücreyi düzenleyebilirsiniz ve dosyayı şablona geri aktarsanız bile, bu şablonda yapılan geliştirme eylemleri artık güncelleştirilmiş verileri içerir.

**ActionTitle'yi** (A sütunu) düzenleyemezsiniz, çünkü bunu düzenlersanız, Uyumluluk Yöneticisi bunun yeni bir geliştirme eylemi olduğunu kabul ediyor. Geliştirme eyleminin adını değiştirmek için hemen aşağıdaki yönergelere bakın.

### <a name="change-an-improvement-actions-name"></a>Geliştirme eyleminin adını değiştirme

Geliştirme eyleminin adını değiştirmek için, elektronik tabloda var olan bir adı yeni bir adla değiştir geçerek açıkça atamanız gerekir. Şu adımları izleyin:

1. Elektronik **tablonuzun** Eylemler sekmesinde, A sütunundan sonra elektronik tablo için yeni bir sütun ekleyin.
2. Şimdi B sütunu olan bu yeni sütunda, üst bilgi olarak 1. satıra girin: **oldActionTitle**.
3. A sütununu kopyalayıp B sütununa yapıştırın. Bu, değiştirmek istediğiniz varolan geliştirme eylem başlıklarınızı B sütununa koyar.
4. A **sütunundaki actionTitle'de**, eski adı silin ve geliştirme eyleminiz için yeni adla değiştirin.

Denetimlerde başvurularak tanınmak için, hem geliştirme eylemleriniz hem de Microsoft eylemleri için eylem başlıklarının İngilizce yaz gerektiğini unutmayın.

### <a name="remove-an-improvement-action"></a>Geliştirme eylemlerini kaldırma

Geliştirme eylemlerini şablondan kaldırmak için, o şablona başvurulan her denetimden kaldırmanız gerekir. Elektronik tablonuzu değiştirmek için aşağıdaki adımları izleyin:

1. **ControlFamily sekmesinde**, kaldırmak istediğiniz geliştirme eyleminin başlığını aratır.
2. Geliştirme eyleminin başlığını göründüğü hücrelerde silin. Geliştirme eylemi bu satırdaki tek eylemse, satırın tamamını silin (denetimi kaldırır).
3. Eylemler **sekmesinde** , sildiren geliştirme eylemlerini içeren satırı silin.
4. Elektronik tablonuzu kaydedin.

Elektronik tablonuzu şablona geri aktarsanız da geliştirme eyleminiz şablondan kaldırılır.

Bir geliştirme eyleminin şablondan kaldırılması, geliştirme eylemlerini Uyumluluk Yöneticisi'den tamamen kaldırmaz. Bu eyleme başka bir şablon yine de başvurulabilirsiniz.

### <a name="remove-a-control"></a>Denetimi kaldırma

Denetimi kaldırmak için aşağıdaki adımları takip edin ve elektronik tablonuzu yeniden içeri aktarın:

1. **ControlFamily sekmesinde**, denetimAdı sütununda kaldırmak istediğiniz **denetimi** bulun.
2. Bu denetimin satırı silin.
    - Bu silinmiş denetim başka hiçbir denetim tarafından başvurulmayacak geliştirme eylemleri içeriyorsa, bu geliştirme eylemlerini Eylemler sekmesinden **kaldırmanız** gerekir. Aksi takdirde, doğrulama hatası alırsınız.

3. Elektronik tablonuzu kaydedin.

Elektronik tablonuzu şablona geri aktarsanız, denetiminiz şablondan kaldırılır.

## <a name="modify-template-info-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde şablon bilgilerini değiştirme

Dosyanız Excel ve kaydedildikten sonra bu adımları izleyin.

1. Değerlendirme şablonu sayfasını yeniden açın ve şablonlarınızı seçin. Şablon ayrıntıları sayfasında, şablonda değişiklik **sihirbazını başlatmak için** Şablonu değiştir'i seçin.
2. Dosyanın **Upload gözat'ı** **seçerek** dosyanızı bulun ve Excel yükleyin.
3. Dosyanız ile ilgili sorun yoksa karşıya yüklenen dosyanın adını sonraki ekranda gösterir. Devam **etmek** için Sonraki'yi seçin (dosyayı değiştirmek için farklı bir **Upload seçin**).
    - Dosyanız ile ilgili bir sorun varsa, sorunun ne olduğunu en üst düzeye alan bir hata iletisiyle açıklar. Dosyanızı düzeltmeniz ve yeniden karşıya yüklemeniz gerekir. Elektronik tablonuzu yanlış biçimlendirilmişse veya bazı alanlarda geçersiz bilgiler varsa hatalar meydana gelir.

4. Gözden **Geçir ve bitiş** ekranı, geliştirme eylemlerinin ve denetimlerin sayısını ve şablon için en yüksek puanı gösterir. Onaylamaya hazır olduğunda, Sonraki'yi **seçin**.
5. Son ekran şablonun değiştiril olduğunu onaylar. **Sihirbazdan çıkmak** için Bitti'yi seçin.

Artık şablonunuz yaptığınız değişiklikleri içerir. Bu değiştirilmiş şablonu kullanan tüm değerlendirmeler artık bekleyen güncelleştirmeleri gösterir ve şablonda yapılan değişiklikleri yansıtmak için değerlendirmelerde yapılan güncelleştirmeleri kabul etmek gerekir. Değerlendirmelere ilişkin [güncelleştirmeler hakkında daha fazla bilgi alın](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Uyumluluk Yöneticisi'ni İngilizce dışında bir dilde kullanıyorsanız, şablonu başka bir dilde dışarı aktararak İngilizce metinlerden bazılarının İngilizce olduğunu Excel. Denetimlerin tanınması için eylemlerin başlıkları (hem geliştirme eylemleriniz hem de uygun olduğunda Microsoft eylemleri) İngilizce olması gerekir. Eylem başlığında değişiklik yaptıysanız, dosyanın doğru şekilde içeri aktar olması için bunu İngilizce yazmayı lütfen kullanın.
