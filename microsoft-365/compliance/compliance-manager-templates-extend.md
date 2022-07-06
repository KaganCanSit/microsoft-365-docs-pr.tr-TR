---
title: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişletme
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
description: Denetim eklemek ve değiştirmek için Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişletmeyi öğrenin.
ms.openlocfilehash: b4cf642e7b5a9dac47cd513251c05a802f16b77b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630465"
---
# <a name="extend-assessment-templates-in-microsoft-purview-compliance-manager"></a>Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişletme

Uyumluluk Yöneticisi, mevcut bir şablona kendi denetimlerinizi ve iyileştirme eylemlerinizi ekleme seçeneği sunar. Bu işleme şablonu genişletme denir.

Şablonu genişletmek için, Microsoft değerlendirme şablonlarını veya evrensel değerlendirme şablonlarını genişletip genişletmediğinize bağlı olarak şablon verilerini değiştirmek için özel yönergeler kullanacaksınız.

## <a name="extend-microsoft-assessment-templates"></a>Microsoft değerlendirme şablonlarını genişletme

Microsoft 365 ile kullanılmak üzere oluşturulmuş bir şablon gibi bir Microsoft şablonunu genişlettiğiniz zaman, microsoft tarafından yayımlanan güncelleştirmeleri almaya devam edebilir. Güncelleştirmeler ilgili düzenlemede veya üründe değişiklikler olduğunda gerçekleşebilir (bkz. [Değerlendirme güncelleştirmelerini kabul etme](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Şablon verilerini hazırlama ve uzantı oluşturma

Hazırlamak için, gerekli şablon verilerini içeri aktarmak için özel olarak biçimlendirilmiş bir Excel elektronik tablosu oluşturmanız gerekir. Excel dosyaları, [Excel ile değerlendirme şablonu verilerini biçimlendirme](compliance-manager-templates-format-excel.md) konusunda belirtilen biçimi izler, ancak uzantılar için özel gereksinimler vardır. Hataları önlemeye yardımcı olmak için şu ek noktalara bakın:

- Elektronik tablonuz yalnızca değerlendirmeye eklemek istediğiniz eylemleri ve denetimleri içermelidir.
- Elektronik tablo, değiştirmek istediğiniz değerlendirmede zaten var olan denetimlerin veya eylemlerin hiçbirini içeremez.
- Şablonunuzun başlığına "uzantı" eklemeyi göz önünde bulundurun; örneğin, "GDPR – [şirketinizin adı] uzantısı." Bu, **değerlendirme şablonları** sayfanızdaki listede Microsoft tarafından sağlanan standart şablondan veya benzer ada sahip özel bir şablondan farklı olarak tanımlanmasını kolaylaştırır.

Elektronik tablonuzu biçimlendirdikten sonra aşağıdaki adımları izleyin.

1. **Değerlendirme şablonları** sayfanıza gidin ve **Yeni şablon oluştur'u** seçin. Şablon oluşturma sihirbazı açılır.

2. Oluşturmak istediğiniz şablon türünü seçin. Bu durumda Microsoft **şablonunu genişlet'i** ve ardından **Microsoft şablonu seç'i seçin**.

3. Ekranınızın sağ tarafında tüm şablonların listesini ve bunların etkin veya etkin olmayan durumunu gösteren bir şablon seçimi açılır penceresi görüntülenir. **Etkinleştirilmiş şablonlar** sayacınız, kullanılabilir toplam sayıdan kaç tane şablonun şu anda kullanımda olduğunu gösterir. Sınırınızı aştıysanız, bir ileti çubuğu bildirim sağlar.

4. Ekranınızın sağ tarafında bir şablon seçimi açılır penceresi görüntülenir. İstediğiniz şablonu bulmak için filtre uygulamak için **Arama'yı** kullanma

5. Şablonunuzu bulduklarından sonra adının sol tarafındaki radyo düğmesini ve ardından **Kaydet'i** seçin.

6. Sonraki ekranda seçtiğiniz şablon gösterilir. Doğruysa **İleri'yi** seçin. (Yanlışsa, yeniden seçmek için **Farklı bir şablon seçin'i** seçin.)

7. **Dosyayı karşıya yükle** ekranında **Gözat'ı** seçerek tüm gerekli şablon verilerini içeren biçimlendirilmiş Excel dosyanızı bulun ve karşıya yükleyin.

8. Dosyanızla ilgili bir sorun yoksa, bir sonraki ekranda karşıya yüklenen dosyanın adı gösterilir. Devam etmek için **İleri'yi** seçin (dosyayı değiştirmeniz gerekiyorsa **Farklı bir dosyayı karşıya yükle'yi** seçin).

    - Dosyanızla ilgili bir sorun varsa, en üstteki hata iletisi sorunun ne olduğunu açıklar. Dosyanızı düzeltmeniz ve yeniden yüklemeniz gerekir. Elektronik tablonuz yanlış biçimlendirilirse veya belirli alanlarda geçersiz bilgiler varsa hatalar oluşur.

9. **Gözden geçir ve bitir** ekranı, iyileştirme eylemlerinin ve denetimlerinin sayısını ve şablonun en yüksek puanını gösterir. Onaylamaya hazır olduğunuzda **İleri'yi** seçin. (Değişiklik yapmanız gerekiyorsa **Farklı bir dosya yükle'yi** seçin.)

10. Son ekranda yeni bir şablon oluşturulduğu onaylanır. **Sihirbazdan çıkmak için Bitti'yi** seçin.

11. Yeni şablonunuzun ayrıntılar sayfasına ulaşırsınız. Buradan Değerlendirme oluştur'u seçerek **değerlendirmenizi** oluşturabilirsiniz. Rehberlik için bkz. [Değerlendirmeleri derleme ve yönetme](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Evrensel değerlendirme şablonlarını genişletme

Ürüne özgü değerlendirmelerinizi özelleştirmek için şablonların evrensel sürümleri de genişletilebilir. Evrensel bir şablon kullanarak değerlendirme oluşturduğunuzda özel bir uzantı şablonu alırsınız ve değerlendirmenin benzersiz bir ürün ve sertifikasyon birleşimi vardır. Bu dosya gereksinimlerinizi karşılayacak şekilde değiştirilebilir. Şablonu düzenleme hakkında yönergeler için, şablonu [değiştirme](compliance-manager-templates-modify.md) yönergelerine bakın.

Evrensel şablonu düzenlerken, şablondaki tüm içerik değiştirilebilir, ancak bunun yapılması üst şablonla devralmayı bozar. Bu, üst şablon yenilenirse artık Microsoft'tan güncelleştirmeleri otomatik olarak alamayacağı anlamına gelir.
