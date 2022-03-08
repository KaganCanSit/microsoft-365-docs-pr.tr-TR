---
title: Microsoft Uyumluluk Yöneticisi için Excel şablonu verilerini E-posta'da biçimlendirme
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
description: Microsoft Uyumluluk Yöneticisi'nde Excel şablonları için değerlendirme verileriyle nasıl çalışııı anlıyoruz.
ms.openlocfilehash: 755716e67589b2f002fcaec7458f502ff945c318
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320585"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-compliance-manager"></a>Microsoft Uyumluluk Yöneticisi için Excel şablonu verilerini E-posta'da biçimlendirme

[](compliance-manager-templates-extend.md) Uyumluluk [](compliance-manager-templates-create.md)[Yöneticisi'nde](compliance-manager-templates-modify.md) değerlendirme şablonlarını oluştururken, değiştirirken veya genişletken, belirli bir biçim Excel şema kullanan elektronik tablolarla birlikte çalışacaksınız. Dosyaların doğru içeri aktar olması için bu belirtimlere karşıt olması gerekir.

## <a name="download-example-spreadsheet"></a>Örnek elektronik tablo indirme

Örnek bir elektronik tablo görüntülemek için [örnek bir dosya indirin](https://go.microsoft.com/fwlink/?linkid=2124865). Kendi dosyanızı oluşturmak için başvuru için bunu kullanabilirsiniz.

Var olan bir şablonu değiştirmeyi planlıyorsanız, başlangıç olarak şablonun ayrıntılarını Uyumluluk Yöneticisi'nde görüntüp şablonun ayrıntılarını Excel indirin.

## <a name="spreadsheet-format"></a>Elektronik tablo biçimi

En Excel elektronik tabloda dört sekme vardır ve bu sekmelerden üçü gereklidir:

1. [Şablon](#template-tab) (gerekli)
2. [ControlFamily](#controlfamily-tab) (gerekli)
3. [Eylemler](#actions-tab) (gerekli)
4. [Boyutlar](#dimensions-tab) (isteğe bağlı)

Elektronik tablonuzu şablon verileriyle doldururken, elektronik tablonun yukarıda listelenen sırayla sekmeleri de içermesi **gerekir; aksi** takdirde verileriniz şablona başarılı bir şekilde içeri aktarılamayacaktır.

### <a name="template-tab"></a>Şablon sekmesi

**Şablon sekmesi** gereklidir. Bu sekmede yer alan bilgiler, şablonla ilgili meta veriler sağlar. Dört gerekli sütun vardır. Sütunların, sayfada aşağıda Excel şekilde tutmaları gerekir. Kendi boyutlarınızı sağlamak için **dört sütundan** sonra kendi sütununu ekleyebilirsiniz. Bunu yapmak için, bunları Boyutlar sekmesine eklemeniz **gerekir** .

- **başlık**: Bu, şablon başlığıdır ve benzersiz olmalıdır. Bu şablon, Kendi şablonlarınız veya Uyumluluk Yöneticisi şablonu dahil olmak üzere Uyumluluk Yöneticisi'nde sahip olduğunuz başka bir şablonla ad paylaşamaz.

- **ürün**: Bu gerekli bir boyutdur. Şablonla ilişkilendirilmiş ürünü listele.

- **sertifika**: Bu, şablon için kullanmakta olduğunuz düzenlemedir.

- **inScopeServices**: Bunlar, ürün içinde bu değerlendirmenin adreslerini (örneğin, ürün olarak Office 365 varsa, Microsoft Teams hizmet kapsamındaki bir hizmet olabilir). Birden çok hizmeti iki noktalı virgülle ayırarak listeabilirsiniz.

> [!NOTE]
> Şablon oluşturmak veya özelleştirmek için **elektronik** tabloyu  içeri aktardıktan sonra, ürün ve sertifika hücrelerine ekleyilen veriler düzenlenemez. Ayrıca, bir grup aynı ürün/sertifika bileşimine sahip iki **değerlendirmeyi içere** değildir. Aynı ürün/sertifika bileşimine sahip birden çok şablonunuz olabilir.

### <a name="controlfamily-tab"></a>ControlFamily sekmesi

**ControlFamily** sekmesi gereklidir.  Bu sekmede, örnek elektronik tabloda verilen sırayı izlemesi gereken sütunlar:

- **denetimAdı**: Bu normalde herhangi bir kimlik türünde olan sertifika, standart veya düzenlemeden gelen denetim adıdır. Denetim adları şablon içinde benzersiz olmalıdır. Elektronik tabloda aynı adı içeren birden çok denetimiz yok.

- **controlFamily**: Denetim için bir sözcük veya tümcecik sağlamaY çok çeşitli denetimleri tanımlayanFamily. Bir denetimin benzersiz olması gerekir; elektronik tabloda birden çok kez listelenmiş olabilir. Aynı denetimFamily, birbirlerine ilişkinleri olmasına rağmen birden çok şablonda da listelenmiş olabilir. Her denetimFamily en az bir denetimle eşlenmiş olmalı.

- **controlTitle**: Denetim için bir başlık sağlar. ControlName bir başvuru kodudur, ancak başlık genellikle yasal düzenlemeler içinde görülen zengin bir metin biçimidir.

- **controlDescription**: Denetimle ilgili bir açıklama sağlar.

- **controlActionTitle**: Bu alan, denetiminizi actionTitle ile listelenmiş bir veya birden çok eylemle ilgilidir. Aralarında boşluk olmayan iki noktalı virgülle ayırarak birden çok eylem  eklersiniz. Listeniz olan her denetim var olan en az bir eylem içermeli ve eylem aynı elektronik tablonun Eylemler  sekmesinde tanımlanmış, farklı bir şablonda yer alıyor veya Microsoft tarafından oluşturulmuş olabilir. Farklı denetimler aynı eyleme başvurur.

### <a name="actions-tab"></a>Eylemler sekmesi

**Eylemler sekmesi** gereklidir.  Bu iyileştirme eylemleri, Uyumluluk Yöneticisi'nde bulunan Microsoft'un değil, organizasyon tarafından yönetilen geliştirme eylemlerini ifade eder. Bu sekmenin, örnek elektronik tabloda verilen sırayı izlemesi gereken sütunlar:

- **actionTitle**: Bu, eyleminizin başlığıdır ve gerekli bir alandır. Sağlayma başlığı benzersiz olmalıdır. **Önemli**: Sahip olduğunuz ve zaten var olan bir eyleme (örneğin, başka bir şablonda) başvurursanız ve sonraki sütunlarda bu öğelerin herhangi birini değiştirirsanız, bu değişiklikler diğer şablonlarda da aynı eyleme yalıtır.

- **implementationType**: Bu gerekli alanda, aşağıdaki üç uygulama türü arasında listelenin: 
  1) **İşlem** - kuruluş sistemlerinin, varlıklarının, verilerin ve personelinin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için kişiler ve süreçler tarafından uygulanan eylemler (örnek: güvenlik farkındalığı ve eğitim).      
  2) **Teknik** - eylemler, kuruluş sistemleri ve verilerin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için bilgi sisteminin donanım, yazılım veya üretici yazılımı bileşenlerinde bulunan teknoloji ve mekanizmalar kullanılarak tamamlanır (örneğin: çok faktörlü kimlik doğrulaması).
  3) **Belgeler** - Kurumsal sistemlerin, varlıkların, verilerin ve personelin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için gereken denetimleri belirleyen ve belirleyen belgelenmiş ilkeler ve yordamlar aracılığıyla uygulanan eylemler (örnek: bilgi güvenliği ilkesi).

- **actionScore**: Bu gerekli alanda, eyleminiz için sayısal bir puan değeri girin. Değer 1 ile 99 arasında bir tam sayı olmalı; 0, null veya boş olamaz. Sayı ne kadar yüksekse, uyumluluk postuzlarınızı geliştirmeye de o kadar büyük bir değer verir. Aşağıdaki resimde Uyumluluk Yöneticisi'nin denetimleri nasıl puanla ilgili olduğu gösterilmiştir:

  ![Uyumluluk Yöneticisi, nokta değerlerini kontrol eder.](../media/compliance-score-action-scoring.png "Uyumluluk Yöneticisi nokta değerlerini kontrol eder")

- **actionDescriptionTitle**: Bu, açıklamanın başlığıdır ve gereklidir. Bu açıklama başlığı, birden çok şablonda aynı eylemi uygulama ve her şablonda farklı bir açıklama ortaya çıkar.  Bu alan, açıklamanın hangi şablona başvur yaptığını netleştirmeye yardımcı olur. Çoğu durumda, bu alana oluşturmakta olduğunu şablonun adını koyabilirsiniz.

- **actionDescription**: Eylemle ilgili bir açıklama sağlar. Kalın metin ve köprü gibi biçimlendirmeler uygulayabilirsiniz. Bu alan gereklidir.

- **boyut-Eylem Amacı**: Bu isteğe bağlı bir alandır. Bunu eklersiniz, üst bilgide "boyut-" ön eki olmalıdır. Buraya dahil edersiniz tüm boyutlar Uyumluluk Yöneticisi'nde filtre olarak kullanılır ve Uyumluluk Yöneticisi'nin geliştirme eylemleri ayrıntıları sayfasında görünür.

### <a name="dimensions-tab"></a>Boyutlar sekmesi

Boyutlar **sekmesi** isteğe bağlıdır. Öte yandan, başka bir boyuttan bir boyuta başvurursanız, daha önce oluşturduğunuz bir şablonda veya Microsoft şablonunda yoksa burada belirtmeniz gerekir. Bu sekmenin sütunları aşağıda listelenmiştir:

- **dimensionKey**: "ürün", "sertifikalar", "eylem amacı" olarak liste
- **dimensionValue**: örnekler: Office 365, HIPPA, Preventative, 2

Var olan bir şablonu dışarı aktarsanız, dışarı aktaran elektronik tabloda,  şablonda kullanılan tüm boyutların listen yer alan Boyutlar sekmesi olur.
