---
title: Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişletme
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
description: Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişleterek denetim ekleme ve değiştirme hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: d47488f578436b1ea8bd865855d681d8778d07bd
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989989"
---
# <a name="extend-assessment-templates-in-microsoft-compliance-manager"></a>Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarını genişletme

Uyumluluk Yöneticisi, mevcut bir şablona kendi denetimlerinizi ve geliştirme eylemlerinizi ekleme seçeneği sunar. Bu işlem şablon genişletme olarak adlandırılan bir işlemdir.

Şablonu genişletmek için, Microsoft değerlendirme şablonlarını veya evrensel değerlendirme şablonlarını genişletip genişletmenize bağlı olarak, şablon verilerini değiştirmek için özel yönergeler kullanırsınız.

## <a name="extend-microsoft-assessment-templates"></a>Microsoft değerlendirme şablonlarını genişletme

Şablonla birlikte kullanmak üzere oluşturulmuş bir Şablon gibi bir Microsoft Microsoft 365, microsoft tarafından yayımlanan güncelleştirmeleri almaya devam ediyor olabilir. İlgili düzenleme veya üründe değişiklik olduğunda güncelleştirmeler olabilir (bkz. [Değerlendirmelerde yapılan güncelleştirmeleri kabul etme](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Şablon verilerini hazırlama ve uzantı oluşturma

Hazırlanmak için, gerekli şablon verilerini içeri aktaran özel olarak biçimlendirilmiş bir Excel elektronik tabloyu toplamanız gerekir. Aşağıdaki Excel, Değerlendirme şablonu verilerini değerlendirmeyle biçimlendirme ve Değerlendirme şablonu verileri Excel aynı biçimde [olur, ancak](compliance-manager-templates-format-excel.md) uzantılar için özel gereksinimler vardır. Hataları önlemeye yardımcı olmak için şu ek noktalara bakın:

- Elektronik tablo, yalnızca değerlendirmeye eklemek istediğiniz eylemleri ve denetimleri içeriyor olabilir.
- Elektronik tablo, değiştirmek istediğiniz değerlendirmede önceden var olan denetim veya eylemleri içeramaz.
- Şablon başlığına "uzantı" ifadesini eklemeyi düşünün. Örneğin, "GDPR – [şirket adı] uzantısı." Bu, değerlendirme şablonları sayfanız üzerinde, Microsoft tarafından sağlanan  standart şablondan veya benzer bir adı olan özel şablondan farklı olarak listeden daha kolay bulun sağlar.

Elektronik tablonuzu biçimlendirdikten sonra, aşağıdaki adımları izleyin.

1. Değerlendirme şablonları **sayfanıza gidin ve** Yeni şablon **oluştur'a tıklayın**. Bir şablon oluşturma sihirbazı açılır.

2. Oluşturmak istediğiniz şablon türünü seçin. Bu durumda, Microsoft şablonunu **genişlet'i ve ardından Microsoft** şablonunu **seçin**.

3. Ekrannizin sağ tarafında, tüm şablonların listesini ve etkin veya etkin değil durumlarını gösteren bir şablon seçimi açılır bölmesi görüntülenir. **Etkinleştirilen şablonlar sayaç**, şu anda kullanmakta olan toplam şablon sayısının dışında kaç şablon olduğunu gösterir. Sınırınızı aştıysanız, ileti çubuğu size bildirim sağlar.

4. Ekrannizin sağ tarafında bir şablon seçimi açılır bölmesi görüntülenir. Kullanmak **istediğiniz** şablonu bulmak üzere filtreler uygulamak için Ara'ya

5. Şablona bu kez bastıktan sonra adının sol radyo düğmesini seçin ve sonra da Kaydet'i **seçin**.

6. Sonraki ekranda seçtiğiniz şablon gösterilir. Doğruysa, Sonraki'yi **seçin**. (Yanlışsa, yeniden **seçmek için Farklı bir şablon** seçin öğesini seçin.)

7. dosyanın **Upload,** tüm gerekli şablon verilerini içeren biçimlendirilmiş  Excel bulmak ve karşıya yüklemek için Gözat'ı seçin.

8. Dosyanız ile ilgili sorun yoksa karşıya yüklenen dosyanın adını sonraki ekranda gösterir. Devam **etmek** için Sonraki'yi seçin (dosyayı değiştirmek için farklı bir **Upload seçin**).

    - Dosyanız ile ilgili bir sorun varsa, sorunun ne olduğunu en üst düzeye alan bir hata iletisiyle açıklar. Dosyanızı düzeltmeniz ve yeniden karşıya yüklemeniz gerekir. Elektronik tablonuzu yanlış biçimlendirilmişse veya bazı alanlarda geçersiz bilgiler varsa hatalar meydana gelir.

9. Gözden **Geçir ve bitiş** ekranı, geliştirme eylemlerinin ve denetimlerin sayısını ve şablon için en yüksek puanı gösterir. Onaylamaya hazır olduğunda, Sonraki'yi **seçin**. (Değişiklik yapmak için farklı bir dosya **Upload seçin**.)

10. Son ekranda yeni bir şablonun oluşturulmuş olduğu onaylar. **Sihirbazdan çıkmak** için Bitti'yi seçin.

11. Yeni şablonun ayrıntılar sayfasına ulaşabilirsiniz. Buradan Değerlendirme oluştur'a seçerek değerlendirmenizi **oluşturabilirsiniz**. Kılavuz için değerlendirmeleri [oluşturma ve yönetme.'ye bakın](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Evrensel değerlendirme şablonlarını genişletme

Şablonların evrensel sürümleri, ürüne özgü değerlendirmelerinizi özelleştirmek için de uzatılabilir. Evrensel şablon kullanarak bir değerlendirme  oluşturursanız ve değerlendirme benzersiz bir ürün ve sertifika bileşimine sahip olduğunda özel bir uzantı şablonu alırsınız. Bu dosya, ihtiyaçlarına göre değiştirilebilir. Şablonu düzenleme konusunda yol gösterici yönergeler için, şablonu değiştirme [yönergelerine bakın](compliance-manager-templates-modify.md).

Evrensel şablonu düzenlerken, şablonda yer alan tüm içerik değiştirilebilir, ancak bu işlem üst şablonla devralmayı bozacak. Bu, üst şablon yenilendiğinde artık Microsoft'tan güncelleştirmeleri otomatik olarak almayacak anlamına gelir.
