---
title: Microsoft Purview Uyumluluk Yöneticisi için Excel'de değerlendirme şablonu verilerini biçimlendirme
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
description: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonları için Excel verileriyle çalışma hakkında bilgi edinin.
ms.openlocfilehash: 6c94d79fec8ff59419854c34755a7402f841cfe8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631237"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-purview-compliance-manager"></a>Microsoft Purview Uyumluluk Yöneticisi için Excel'de değerlendirme şablonu verilerini biçimlendirme

Uyumluluk Yöneticisi'nde değerlendirme şablonları [oluştururken](compliance-manager-templates-create.md), [değiştirirken](compliance-manager-templates-modify.md) veya [genişletirken](compliance-manager-templates-extend.md) , belirli bir biçim ve şema kullanan Excel elektronik tabloları ile çalışırsınız. Dosyaların doğru içeri aktarılması için bu belirtimlere uyulmalıdır.

## <a name="download-example-spreadsheet"></a>Örnek elektronik tabloyu indirme

Örnek bir elektronik tabloyu görüntülemek için [örnek bir dosya indirin](https://go.microsoft.com/fwlink/?linkid=2124865). Kendi dosyanızı oluşturmak için başvuru için bunu kullanabilirsiniz.

Mevcut bir şablonu değiştirmeyi planlıyorsanız, şablonun ayrıntılarını Uyumluluk Yöneticisi'nde görüntüleyip Excel dosyasını indirerek başlayın.

## <a name="spreadsheet-format"></a>Elektronik tablo biçimi

Excel elektronik tablosu dört sekme içerir ve bunların üçü gereklidir:

1. [Şablon](#template-tab) (gerekli)
2. [ControlFamily](#controlfamily-tab) (gerekli)
3. [Eylemler](#actions-tab) (gerekli)
4. [Boyutlar](#dimensions-tab) (isteğe bağlı)

Elektronik tablonuzu şablon verileriyle doldururken, elektronik tablo **yukarıda listelenen sırayla sekmeleri içermelidir**, aksi takdirde verileriniz şablona başarıyla aktarılamaz.

### <a name="template-tab"></a>Şablon sekmesi

**Şablon** sekmesi gereklidir. Bu sekmedeki bilgiler şablon hakkında meta veriler sağlar. Dört gerekli sütun vardır. Sütunların Excel sayfasındaki sırayı aşağıda listelendiği gibi tutması gerekir. Kendi boyutlarınızı sağlamak için dört sütunun **arkasına** kendi sütununuzu ekleyebilirsiniz. Bunu yaparsanız, bunları **Boyutlar** sekmesine eklediğinizden emin olun.

- **title**: Bu, şablonunuzun benzersiz olması gereken başlığıdır. Kendi şablonlarınız veya Uyumluluk Yöneticisi şablonunuz da dahil olmak üzere, Bir adı Uyumluluk Yöneticisi'nde sahip olduğunuz başka bir şablonla paylaşamaz.

- **ürün**: Bu gerekli bir boyutdur. Şablonla ilişkili ürünü listeleyin.

- **sertifikasyon**: Bu, şablon için kullandığınız düzenlemedir.

- **inScopeServices**: Bunlar, bu değerlendirmenin çözümlendiği ürün içindeki hizmetlerdir (örneğin, ürün olarak Office 365 listelediyseniz, Microsoft Teams kapsam içi bir hizmet olabilir). İki noktalı virgülle ayrılmış birden çok hizmeti listeleyebilirsiniz.

> [!NOTE]
> Şablon oluşturmak veya özelleştirmek için elektronik tabloyu içeri aktardıktan sonra **ürün** ve **sertifika** hücrelerine eklediğiniz veriler düzenlenemez. Ayrıca, bir grup aynı **ürün/sertifika** birleşimine sahip iki değerlendirme içeremez. Aynı ürün/sertifika bileşimine sahip birden çok şablona sahip olabilirsiniz.

### <a name="controlfamily-tab"></a>ControlFamily sekmesi

**ControlFamily** sekmesi gereklidir.  Örnek elektronik tabloda sağlanan sırayı izlemesi gereken bu sekmedeki gerekli sütunlar şunlardır:

- **controlName**: Bu, genellikle bir kimlik türü olan sertifikasyon, standart veya düzenleme denetim adıdır. Denetim adları bir şablon içinde benzersiz olmalıdır. Elektronik tabloda aynı ada sahip birden çok denetime sahip olamazsınız.

- **controlFamily: ControlFamily** için geniş bir denetim grubunu tanımlayan bir sözcük veya tümcecik sağlayın. ControlFamily'nin benzersiz olması gerekmez; elektronik tabloda birden çok kez listelenebilir. Aynı controlFamily, birbiriyle hiçbir ilişkisi olmasa da birden çok şablonda listelenebilir. Her controlFamily en az bir denetimle eşlenmelidir.

- **controlTitle**: Denetim için bir başlık sağlayın. controlName bir başvuru kodu olsa da, başlık genellikle düzenlemelerde görülen zengin bir metin biçimidir.

- **controlDescription**: Denetimin açıklamasını sağlayın.

- **controlActionTitle**: Bu alan, denetiminizi actionTitle tarafından listelenen bir veya daha fazla eylemle ilişkilendirmektedir. Aralarında boşluk olmayan iki noktalı virgülle ayırarak birden çok eylem ekleyebilirsiniz. Listelediğiniz her denetim en az bir eylem içermelidir ve eylem aynı elektronik tablonun **Eylemler** sekmesinde tanımlanabilir, farklı bir şablonda yer alabilir veya Microsoft tarafından oluşturulabilir. Farklı denetimler aynı eyleme başvurabilir.

### <a name="actions-tab"></a>Eylemler sekmesi

**Eylemler** sekmesi gereklidir.  Uyumluluk Yöneticisi'nde zaten var olan Microsoft'un değil, kuruluşunuz tarafından yönetilen iyileştirme eylemlerini tanımlar. Örnek elektronik tabloda sağlanan sırayı izlemesi gereken bu sekme için gerekli sütunlar şunlardır:

- **actionTitle**: Bu, eyleminizin başlığıdır ve gerekli bir alandır. Sağladığınız başlık benzersiz olmalıdır. **Önemli**: Zaten var olan bir eyleme başvurursanız (başka bir şablonda olduğu gibi) ve sonraki sütunlardaki öğelerinden herhangi birini değiştirirseniz, bu değişiklikler diğer şablonlarda aynı eyleme yayılır.

- **implementationType**: Bu gerekli alanda, aşağıdaki üç uygulama türünden birini listeleyin: 
  1) **operasyonel** - Kuruluş sistemlerinin, varlıkların, verilerin ve personelin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için kişiler ve süreçler tarafından uygulanan eylemler (örneğin: güvenlik farkındalığı ve eğitimi).      
  2) **Teknik** - Kuruluş sistemlerinin ve verilerinin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için bilgi sisteminin donanım, yazılım veya üretici yazılımı bileşenlerinde yer alan teknoloji ve mekanizmalar kullanılarak gerçekleştirilir (örnek: çok faktörlü kimlik doğrulaması).
  3) **Belgeler** - Kuruluş sistemlerinin, varlıkların, verilerin ve personelin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için gerekli denetimleri oluşturan ve tanımlayan belgelenmiş ilkeler ve yordamlar aracılığıyla uygulanan eylemler (örnek: bilgi güvenliği ilkesi).

- **actionScore**: Bu gerekli alanda, eyleminiz için sayısal bir puan değeri sağlayın. Değer 1 ile 99 arasında bir tamsayı olmalıdır; 0, null veya boş olamaz. Sayı ne kadar yüksek olursa uyumluluk duruşunuzu geliştirmeye yönelik değeri de o kadar artar. Aşağıdaki resimde, Uyumluluk Yöneticisi'nin denetimleri nasıl puanlar:

  ![Uyumluluk Yöneticisi, nokta değerlerini denetler.](../media/compliance-score-action-scoring.png "Uyumluluk Yöneticisi, nokta değerlerini denetler")

- **actionDescriptionTitle**: Bu açıklamanın başlığıdır ve gereklidir. Bu açıklama başlığı, birden çok şablonda aynı eyleme sahip olmanıza ve her şablonda farklı bir açıklama oluşturmanıza olanak tanır.  Bu alan, açıklamanın başvuruda bulunan şablonu netleştirmenize yardımcı olur. Çoğu durumda, oluşturmakta olduğunuz şablonun adını bu alana koyabilirsiniz.

- **actionDescription**: Eylemin açıklamasını sağlayın. Kalın metin ve köprüler gibi biçimlendirmeler uygulayabilirsiniz. Bu gerekli bir alandır.

- **boyut-Eylem Amacı**: Bu isteğe bağlı bir alandır. Eklerseniz, üst bilgi "dimension-" ön ekini içermelidir. Buraya eklediğiniz tüm boyutlar Uyumluluk Yöneticisi'nde filtre olarak kullanılır ve Uyumluluk Yöneticisi'nin iyileştirme eylemleri ayrıntıları sayfasında görünür.

### <a name="dimensions-tab"></a>Boyutlar sekmesi

**Boyutlar** sekmesi isteğe bağlıdır. Ancak başka bir yerde bir boyuta başvuruda bulunursanız, önceden oluşturduğunuz bir şablonda veya Microsoft şablonunda mevcut değilse burada belirtmeniz gerekir. Bu sekmenin sütunları aşağıda listelenmiştir:

- **dimensionKey**: list as "product", "certifications," "action purpose"
- **dimensionValue**: örnekler: Office 365, HIPPA, Önleyici, Dedektif

Var olan bir şablonu dışarı aktardığınızda, dışarı aktarılan elektronik tabloda şablonda kullanılan tüm boyutların listelendiği **Boyutlar** sekmesi bulunur.
