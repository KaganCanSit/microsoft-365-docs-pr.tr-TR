---
title: Eğitilebilir sınıflayıcılar hakkında bilgi
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Eğitilebilir sınıflayıcılar, pozitif ve negatif örnekler vererek etiketleme veya ilke uygulaması için çeşitli içerik türlerini tanıyabilir.
ms.openlocfilehash: 50d20c3a40b21696c06064b548d7766684fb12a0
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015565"
---
# <a name="learn-about-trainable-classifiers"></a>Eğitilebilir sınıflayıcılar hakkında bilgi

İçeriği, koruma altına almak ve düzgün bir şekilde ele almak için sınıflama ve etiketleme, bilgi koruma disiplini için başlangıç noktasıdır. Microsoft 365, içeriği sınıflandırmak için üç yolu vardır.

## <a name="manually"></a>El ile

El ile sınıflandırma için insan kararlarını ve eylemlerini gerektirir. Kullanıcılar ve yöneticiler, karşılaştıkları içeriğe bunları uygulanır. Önceden var olan etiketleri ve hassas bilgi türlerini kullanabileceğiniz gibi, özel oluşturulanları da kullanabilirsiniz.  Ardından içeriği koruyabilir ve içeriğinin yok olduğunu yönetebilirsiniz.

## <a name="automated-pattern-matching"></a>Otomatik desen eşleştirme

Bu sınıflandırma mekanizmaları kategorisi içeriği aşağıdakilere göre bulmayı içerir:

- Anahtar sözcükler veya meta veri değerleri (anahtar sözcük sorgu dili).
- Sosyal güvenlik, kredi kartı veya banka hesap numaraları gibi hassas bilgilerin önceden tanımlanan desenlerini kullanma [(Hassas bilgi türü varlık tanımları)](sensitive-information-type-entity-definitions.md).
- Öğenin şablonda çeşitlemesi olduğundan (belge parmak yazdırma) [bunu tanıma](document-fingerprinting.md).
- Tam dizelerin tam [eşleşmesi için iletişim durumu kullanılır](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Daha sonra, Bekletme etiketleri için veri kaybı önleme ve otomatik uygulama ilkeleri hakkında bilgi edin konusunda, [](dlp-learn-about-dlp.md) içeriğin kullanılabilir olması için duyarlılık ve bekletme etiketleri otomatik [olarak uygulanabilir](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Sınıflayıcılar

Bu sınıflandırma yöntemi, el ile veya otomatik desen eşleştirme yöntemleriyle kolayca tanım bulunmayan içeriğe çok uygun bir yöntemdir. Bu sınıflandırma yöntemi, öğenin içinde olan öğelere (desen eşleştirmesi) göre değil, öğenin ne olduğunu temel alan bir sınıflandırıcı kullanmakla daha çok ilgili bir yöntemdir. Sınıflandırıcı, sınıflendirmeyle ilgilendiğiniz içeriğin yüzlerce örneğine bakarak bir içerik türünün nasıl tanımlan olduğunu öğrenir.

> [!NOTE]
> Önizleme'de - Filtreler panelinde Eğitime Uygun Sınıflayıcılar'ı genişleterek içerik gezgininde eğitilebilir **sınıflayıcıları** görüntüleyebilirsiniz. Eğitilebilir sınıflayıcılar herhangi bir etikete gerek kalmadan SharePoint, Teams ve OneDrive'de bulunan olay sayısını otomatik olarak görüntüler.
> Bu özelliği kullanmak istemiyorsanız, ilk gelen sınıflandırmayı devre dışı bırakmak için Microsoft Desteği'nden bir istek dosyası açabilirsiniz. Bu, etiket ilkeleri oluşturmadan önce hassas ve etiketli içeriğinizin taransını devre dışı bırakacak.

### <a name="where-you-can-use-classifiers"></a>Sınıflayıcıları kullanabileceğiniz yer

Sınıflayıcılar, duyarlılık etiketleriyle otomatik etiket oluşturma, [](apply-sensitivity-label-automatically.md)bir koşula dayalı olarak otomatik saklama etiketi ilkesi uygulama ve iletişim [](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) uyumluluğu için Office koşulu olarak [kullanılabilir](communication-compliance.md). 

Duyarlılık etiketleri sınıflandırıcıları koşullar olarak kullanabilir, bkz [. Otomatik olarak içeriğe duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Sınıflandırıcılar yalnızca şifrelenmiş öğelerle çalışır.

## <a name="types-of-classifiers"></a>Sınıflandırıcı türleri

- **önceden eğitilmiş sınıflandırıcılar** - Microsoft, bunları eğitmeden kullanmaya başy çoklu sınıflandırıcılar oluşturabilir ve önceden eğitmiş olabilir. Bu sınıflandırıcılar, durumuyla birlikte görüntülenir `Ready to use`.
- **özel eğitilebilir** sınıflayıcılar - Önceden eğitilmiş sınıflayıcıların kapağında yer alan sınıflandırma ihtiyaçlarının ötesine geçse de, kendi sınıflandırıcılarınızı oluşturabilir ve eğitebilirsiniz.

### <a name="pre-trained-classifiers"></a>Önceden eğitilmiş sınıflayıcılar

Microsoft 365 önceden eğitilmiş birden çok sınıflandırıcıyla birlikte gelir:

> [!CAUTION]
> Rahatsız Edici Dil ön eğitimcisini, yüksek sayıda yanlış pozitif sonuç üretmiş olduğu için kullanımdandan alıkıyoruz. Bu e-postayı kullanmamanızı ve şu anda kullanıyorsanız iş süreçlerinizi bundan çıkaracağız. Bunun yerine **Tehdit,** **Küfür ve Taciz** ön eğitimcilerini  öneririz.

- **Özgeçmişler**: bir başvuranın kişisel, eğitim, profesyonel nitelikleri, iş deneyimi ve diğer kişisel tanımlayıcı bilgilerine ilişkin metinsel hesaplar olan docx, .pdf, .rtf, .txt öğelerini algılar
- Kaynak **Kodu:** GitHub'de kullanılan en çok kullanılan 25 bilgisayar programlama dilinde yazılmış yönergeler ve deyimler kümesi içeren öğeleri algılar: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx içeriklerini algılar .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . RData, .rds, .rb, .scala, .sc, .sh, .swift dosyaları.

> [!NOTE]
> Kaynak Kod, metnin büyük kısmının kaynak kod olduğunu algılamak için eğitildir. Düz metinle kesişen kaynak kod metnini algılamaz.

- **Sözleşmeler**: Gizlilik dışı sözleşmeler, iş bildirimi, kredi ve kira sözleşmeleri, işe alma ve rekabet dışı sözleşmeler gibi yasal sözleşmelerle ilgili içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml dosyalarında içeriği algılar.
- **Saptama**: Açık bir ayırt etmek için dil algılar ve diğer topluluklara göre Afrika Amerika/Siyah topluluklarına karşı ayrım diline duyarlıdır.
- **Finans**: Kurumsal finans, muhasebe, ekonomi, bankacılık ve yatırım kategorilerinde içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt'da içeriği algılar .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyaları.
- **Taciz**: Şu özellikleri temel alarak bir veya birden çok bireyi hedef alan rahatsız edici dil metin öğeleri içeren belirli bir rahatsız edici dil metin kategorisi algılar: yarış, cinsiyet, din, ulusal köken, cinsiyet, cinsel yönlendirme, yaş, engellilik. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarında içeriği algılar.
- **Sağlık:** Tıbbi hizmetler, tanılar, tedavi, talepler gibi tıbbi ve sağlık yönetimi ile ilgili yönlerinin içeriğini algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt'da içeriği algılar .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyaları.
- **İk**: İnsan kaynakları ile ilgili olan görüşme, görüşme, işe alma, eğitim, değerlendirme, uyarı ve sonlandırma kategorilerinde içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt'da içeriği algılar .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyaları.
- **IP**: Ticari sırlar ve benzer gizli bilgiler gibi Fikri Mülkiyet ile ilgili kategorilerde içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt'da içeriği algılar .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyaları.
- **IT**: Bilgi Teknolojisi'nin ve ağ ayarları, bilgi güvenliği, donanım ve yazılım gibi Siber güvenlik kategorilerinde içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt'da içeriği algılar .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyaları.
- **Yasal İlişkiler**: Davalar, yasal süreç, yasal yükümlülük, yasal terminoloji, yasa ve mevzuat gibi yasal ilişkilere yönelik kategorilerde içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml dosyalarında içeriği algılar.
- **Tedarik**: İçerikleri mal ve hizmet tedariki için alıntı, alıntı, satın alma ve ödeme kategorilerinde algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyalarında içeriği algılar.
- **Küfür:** Çoğu kişiyi rahatsız eden ifade içeren rahatsız edici dil metin öğeleri kategorisini algılar. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarında içeriği algılar.
- **Vergi**: Vergi planlaması, vergi formları, vergi dosyalama, vergi düzenlemeleri gibi Vergi ilişkisinin içeriğini algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf .pdf içeriği algılar .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .ppsx, .ppsm, .pps, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlam, xla dosyaları.
- **Tehdit**: Şiddet işlemeye yönelik tehditlerle ilgili rahatsız edici dil metin öğeleri içeren belirli bir kategoriyi algılar veya bir kişiye ya da metne fiziksel zarar veya zarar verir. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarında içeriği algılar.

Bunlar Microsoft 365 uyumluluk merkezi  > **Data sınıflandırmasıTrainable** >  **classifiers** görünümünde ve durumuyla birlikte görüntülenir`Ready to use`.

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Rahatsız edici dil, taciz, küfür, tehdit sınıflayıcıları yalnızca aranabilir metinle çalışır ve bu alanlar genelinde terimlerin veya dilin tam veya kapsamlı bir listesi olmadığını lütfen unutmayın. Ayrıca, dil ve kültürel standartlar sürekli değişir ve bu gerçeklerin ışığı altında, Microsoft kendi takdirine bağlı olarak bu sınıflayıcıları güncelleştirme hakkını sahiptir. Sınıflayıcılar bu alanları algılamada kuruluşa yardımcı olabilir, ancak sınıflayıcılar yalnızca bu tür bir dilin kullanımını algılamak veya bunlara yönelik olarak kuruma yardımcı olmak için tasarlanmıştır. Microsoft veya yan kuruluşları değil, organizasyonu, yerel gizlilik ve diğer ilgili yasalarla uyumluluk da dahil olmak üzere, önceden eğitime alınan bir sınıflandırıcı tarafından tanımlanan içerikleri izleme, tarama, engelleme, kaldırma ve saklama ile ilgili tüm kararlardan sorumlu kalır. Microsoft dağıtım ve kullanımdan önce hukuk danışmanını teşvik ediyor.

Önceden eğitilmiş sınıflayıcılar şu dillerde içeriği tarayabilirsiniz:

• Çince (Basitleştirilmiş) • İngilizce • Fransızca • Almanca • İtalyanca • Japonca • Portekizce • İspanyolca

### <a name="custom-classifiers"></a>Özel sınıflandırıcılar

Önceden eğitilmiş sınıflayıcılar sizin ihtiyaçlarını karşılamazsa, kendi sınıflandırıcılarınızı oluşturabilir ve eğitebilirsiniz. Kendi çalışmalarınızı oluşturma konusunda çok daha fazla çalışma söz konusudur, ancak bu çalışmalar çok daha uygun şekilde kuruluşların gereksinimlerine uyarlanmış olacaktır.

Kategori içinde kesinlikle farklı örnekler vermek için özel bir eğitilebilir sınıflandırıcı oluşturmaya başlarsiniz. Bu örnekler işlemenin ardından, bu örnekleri hem eşleşen hem de eşleşmeyen örneklerle karma olarak vererek test etmek için sınayın. Ardından sınıflandırıcı, herhangi bir öğenin yapmakta olduğu kategoriye denk olup olmadığını tahminler yapar. Ardından, tahminlerinin doğruluğunu artırmaya yardımcı olmak için sonuçlarını onaylar, doğru pozitif sonuçları, doğru negatifleri, yanlış pozitifleri ve yanlış negatifleri sıralar. 

Sınıflandırıcıyı yayımlarken, SharePoint Online, Exchange ve OneDrive gibi konumlarda öğeleri sıralar ve içeriği sınıflara göre sıralar. Sınıflandırıcıyı yayımladikten sonra, ilk eğitim sürecine benzer bir geri bildirim işlemi kullanarak bunu eğitebilirsiniz.

Örneğin, aşağıdakiler için eğitilebilir sınıflayıcılar oluşturabilirsiniz:

- Yasal belgeler - vekaletname, kapatma kümeleri, iş bildirimi gibi
- Stratejik iş belgeleri - basın bülteni, birleşme ve alma, anlaşmalar, iş veya pazarlama planları, fikri mülkiyet, patentler, tasarım belgeleri gibi
- Fiyatlandırma bilgileri - faturalar, fiyat teklifleri, iş siparişleri, açık belgeler gibi
- Finansal bilgiler - kuruluş yatırımları, üç aylık veya yıllık sonuçlar gibi

#### <a name="process-flow-for-creating-custom-classifiers"></a>Özel sınıflandırıcılar oluşturmak için süreç akışı

Bekletme ilkeleri ve iletişim gözetimi gibi uyumluluk çözümlerde kullanmak üzere bir sınıflandırıcı oluşturma ve yayımlama bu akışı izler. Özel bir eğitilebilir sınıflandırıcı oluşturma hakkında daha fazla ayrıntı için bkz [. Özel sınıflandırıcı oluşturma](classifier-get-started-with.md).

![süreç akışı özel sınıflandırıcısı.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Sınıflayıcıları yeniden kısıtla

Tüm özel eğitilebilir sınıflayıcıların doğruluğunu geliştirmeye yardımcı olabilir ve gerçekleştirecekleri sınıflandırmanın doğruluğu hakkında geri bildirim sağlayarak onlara yardımcı olabilirsiniz. Buna yeniden kısıtlama adı verilen ve bu iş akışını izleyen bir iş akışı vardır.

> [!NOTE]
> Önceden eğitilmiş sınıflayıcılar yeniden eğitil kullanılamaz.

![sınıflandırıcı iş akışını yeniden kısıtlar.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Bekletme etiketleri](retention.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Belge parmağınızı yazdırma](document-fingerprinting.md)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
