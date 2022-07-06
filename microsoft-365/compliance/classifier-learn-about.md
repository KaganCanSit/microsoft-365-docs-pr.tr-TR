---
title: Eğitilebilir sınıflandırıcılar hakkında daha fazla bilgi edinme
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
description: Eğitilebilir sınıflandırıcılar, etiketleme veya ilke uygulamasına bakılması için pozitif ve negatif örnekler vererek çeşitli içerik türlerini tanıyabilir.
ms.openlocfilehash: 0c47d019b3508bdd8d8fba1f1b4303c7f4c9579d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621215"
---
# <a name="learn-about-trainable-classifiers"></a>Eğitilebilir sınıflandırıcılar hakkında daha fazla bilgi edinme

İçeriğin korunabilmesi ve doğru şekilde işlenebilmesi için sınıflandırma ve etiketleme, bilgi koruma uzmanlık alanı için başlangıç noktasıdır. Microsoft 365'in içeriği sınıflandırmak için üç yolu vardır.

## <a name="manually"></a>Elle

El ile sınıflandırma insan yargısı ve eylem gerektirir. Kullanıcılar ve yöneticiler, içerikle karşılaştıklarında bunları içeriğe uygular. Önceden var olan etiketleri ve hassas bilgi türlerini veya özel oluşturulanları kullanabilirsiniz.  Daha sonra içeriği koruyabilir ve eğilimini yönetebilirsiniz.

## <a name="automated-pattern-matching"></a>Otomatik desen eşleştirme

Bu sınıflandırma mekanizması kategorisi içeriği bulma ölçütü:

- Anahtar sözcükler veya meta veri değerleri (anahtar sözcük sorgu dili).
- Sosyal güvenlik, kredi kartı veya banka hesabı numaraları ( [Hassas bilgi türü varlık tanımları)](sensitive-information-type-entity-definitions.md) gibi hassas bilgilerin önceden tanımlanmış desenlerini kullanma.
- Şablondaki bir çeşitleme olduğundan [öğeyi tanıma (belge parmağıyla yazdırma)](document-fingerprinting.md).
- Tam dizelerin varlığının [kullanılması tam veri eşleşmesi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Daha sonra duyarlılık ve bekletme etiketleri otomatik olarak uygulanarak içeriğin [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md) ve [bekletme etiketleri için ilkeleri otomatik olarak uygulama](apply-retention-labels-automatically.md) başlığı altında kullanılabilir hale getirilebilir.

## <a name="classifiers"></a>Sınıflandırıcı

Bu sınıflandırma yöntemi, el ile veya otomatik desen eşleştirme yöntemleri tarafından kolayca tanımlanmayan içeriğe çok uygundur. Bu sınıflandırma yöntemi, öğedeki öğeler (desen eşleştirme) tarafından değil, öğenin ne olduğuna göre bir öğeyi tanımlamak için bir sınıflandırıcı kullanmakla daha fazla ilgili olur. Sınıflandırıcı, sınıflandırmak istediğiniz içeriğin yüzlerce örneğine bakarak bir içerik türünü tanımlamayı öğrenir.

> [!NOTE]
> Önizlemede - Filtreler panelinde Eğitilebilir Sınıflandırıcılar'ı genişleterek içerik gezgininde **eğitilebilir sınıflandırıcıları** görüntüleyebilirsiniz. Eğitilebilir sınıflandırıcılar, hiçbir etiketleme gerektirmeden SharePoint, Teams ve OneDrive'da bulunan olay sayısını otomatik olarak görüntüler.
> Bu özelliği kullanmak istemiyorsanız, Microsoft Desteği ile bir istekte bulunmanız gerekir. Bu, İçerik Gezgini'ndeki hiçbir etiketleme ilkesinde kullanılmayan hassas verilerinizin görüntülenmesini devre dışı bırakır. Verilerinizi taramayı da devre dışı bırakabilirsiniz. Tarama kapalıysa, bu sınıflandırıcılarla duyarlılık etiketleme ve DLP ilkeleri çalışmaz

### <a name="where-you-can-use-classifiers"></a>Sınıflandırıcıları kullanabileceğiniz yerler

Sınıflandırıcılar, [duyarlılık etiketleriyle Office otomatik etiketleme](apply-sensitivity-label-automatically.md), [bir koşula göre ve iletişim uyumluluğuna göre bekletme etiketi ilkesini otomatik uygulama](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) koşulu olarak kullanılabilir.[](communication-compliance.md)

Duyarlılık etiketleri sınıflandırıcıları koşul olarak kullanabilir. Bkz. [İçeriğe otomatik olarak duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Sınıflandırıcılar yalnızca şifrelenmemiş öğelerle çalışır.

## <a name="types-of-classifiers"></a>Sınıflandırıcı türleri

- **önceden eğitilmiş sınıflandırıcılar** - Microsoft, eğitmeden kullanmaya başlayabileceğiniz birden çok sınıflandırıcı oluşturmuş ve önceden eğitmiştir. Bu sınıflandırıcılar, durumunda `Ready to use`görüntülenir.
- **özel eğitilebilir sınıflandırıcılar** - Önceden eğitilen sınıflandırıcıların kapsadığını aşan sınıflandırma gereksinimleriniz varsa, kendi sınıflandırıcılarınızı oluşturabilir ve eğitebilirsiniz.

### <a name="pre-trained-classifiers"></a>Önceden eğitilmiş sınıflandırıcılar

Microsoft 365, önceden eğitilmiş birden çok sınıflandırıcı ile birlikte gelir:

- **Yetişkin, müstehcen ve gory**: Bu tür görüntüleri algılar. Görüntülerin boyutu 50 kilobayt (KB) ile 4 megabayt (MB) arasında olmalı ve yükseklik x genişlik boyutlarında 50 x 50 pikselden büyük olmalıdır. Tarama ve algılama, Exchange Online e-posta iletileri ile Microsoft Teams kanalları ve sohbetleri için desteklenir. .jpeg, .png, .gif ve .bmp dosyalarındaki içeriği algılar.

- **Sözleşmeler**: İfşa etmeme sözleşmeleri, iş beyanları, kredi ve kira sözleşmeleri, istihdam ve rekabet dışı sözleşmeler gibi yasal sözleşmelerle ilgili içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml dosyalarındaki içeriği algılar.

- **Müşteri şikayetleri**: Müşteri şikayetleri sınıflandırıcısı, kuruluşunuzun ürünleri veya hizmetleri hakkında yapılan geri bildirimleri ve şikayetleri algılar. Bu sınıflandırıcı, Tüketici Finansal Koruma Bürosu ve Gıda ve İlaç Yönetimi gereksinimleri gibi şikayetlerin tespiti ve önceliklendirmesi ile ilgili mevzuat gereksinimlerini karşılamanıza yardımcı olabilir. İletişim Uyumluluğu için .msg ve .eml dosyalarındaki içeriği algılar. Microsoft Purview Bilgi Koruması hizmetlerinin geri kalanında .docx, .pdf, .txt, .rtf, .jpg, .jpeg, .png, .gif, .bmp, .svg dosyalarındaki içeriği algılar.

- **Ayrımcılık**: Açık ayrımcı dili algılar ve diğer topluluklarla karşılaştırıldığında Afrikalı Amerikalı/Siyah topluluklara karşı ayrımcı dile duyarlıdır.

- **Finans**: Kurumsal finans, muhasebe, ekonomi, bankacılık ve yatırım kategorilerindeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **Taciz**: Irk, etnik köken, din, ulusal köken, cinsiyet, cinsel yönelim, yaş, engellilik gibi bir veya birden çok kişiyi hedefleyen saldırgan davranışla ilgili belirli bir rahatsız edici dil metin öğesi kategorisini algılar. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarındaki içeriği algılar.

- **Sağlık**: Tıbbi hizmetler, tanılar, tedavi, talepler gibi tıbbi ve sağlık yönetimi açısından içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **İk**: İnsan kaynaklarıyla ilgili işe alım, görüşme, işe alma, eğitim, değerlendirme, uyarı ve sonlandırma kategorilerindeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **IP**: Ticari sırlar ve benzer gizli bilgiler gibi Fikri Mülkiyetle ilgili kategorilerdeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **BT**: Ağ ayarları, bilgi güvenliği, donanım ve yazılım gibi Bilgi Teknolojisi ve Siber Güvenlik kategorilerindeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **Yasal işler**: Dava, yasal süreç, yasal yükümlülük, yasal terminoloji, hukuk ve mevzuat gibi hukuk işleri ile ilgili kategorilerdeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml dosyalarındaki içeriği algılar.

- **Tedarik**: Teklif verme, alıntılama, satın alma ve mal ve hizmet tedariki için ödeme kategorilerindeki içeriği algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla dosyalarındaki içeriği algılar.

- **Küfür**: Çoğu kişiyi utandıran ifadeler içeren belirli bir rahatsız edici dil metin öğeleri kategorisini algılar. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarındaki içeriği algılar.

- **Özgeçmiş**: Bir başvuru sahibinin kişisel, eğitim, mesleki nitelikleri, iş deneyimi ve diğer kişisel tanımlayıcı bilgilerinin metinsel hesapları olan docx, .pdf, .rtf, .txt öğelerini algılar

- **Kaynak kodu**: GitHub'da bilgisayar programlama dilleri yazılmış bir dizi yönerge ve deyim içeren öğeleri algılar: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Betiği. .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . RData, .rds, .rb, .scala, .sc, .sh, .swift dosyaları.

  > [!NOTE]
  > Kaynak Kodu, metnin büyük kısmının kaynak kodu olduğunu algılamak için eğitilir. Düz metinle kesişen kaynak kodu metnini algılamaz.

- **Vergi: Vergi** planlaması, vergi formları, vergi dosyalama, vergi düzenlemeleri gibi Vergi ilişkisi içeriğini algılar. .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xltm, .xlam, .xla dosyaları.

- **Tehdit**: Şiddet uygulama veya bir kişi ya da mülke fiziksel zarar verme ya da zarar verme tehditleriyle ilgili belirli bir rahatsız edici dil metin öğesi kategorisini algılar.

- **Tehdit**: Şiddet uygulama veya bir kişi ya da mülke fiziksel zarar verme ya da zarar verme tehditleriyle ilgili belirli bir rahatsız edici dil metin öğesi kategorisini algılar. .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg dosyalarındaki içeriği algılar.

Bu sınıflandırıcılar **, Microsoft Purview uyumluluk portalı** \> **Veri sınıflandırması** \> **Eğitilebilir sınıflandırıcılar** görünümünde durumunu `Ready to use`gösterir.

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Yerleşik eğitilebilir ve genel sınıflandırıcıların bu alanlarda terimlerin veya dillerin kapsamlı veya eksiksiz bir listesini sağlamadığını lütfen unutmayın. Ayrıca, dil ve kültürel standartlar sürekli olarak değişir ve bu gerçekler ışığında, Microsoft bu sınıflandırıcıları kendi takdirine bağlı olarak güncelleştirme hakkını saklı tutar. Sınıflandırıcılar kuruluşunuzun bu alanları algılamasına yardımcı olabilir ancak sınıflandırıcılar, kuruluşunuzun bu dilin kullanımını algılama veya ele alma için tek aracı sağlamayı amaçlamamaktadır. Microsoft veya yan kuruluşları değil kuruluşunuz, yerel gizlilik ve diğer geçerli yasalara uyumluluk dahil olmak üzere önceden eğitilmiş bir sınıflandırıcı tarafından tanımlanan tüm içeriklerin izlenmesi, taranması, engellenmesi, kaldırılması ve saklanmasıyla ilgili tüm kararlardan sorumlu kalır. Microsoft, dağıtım ve kullanımdan önce hukuk müşaviri ile danışmayı teşvik eder.

Tehdit, Küfür, Taciz ve Ayrımcılık sınıflandırıcılarımız içeriği şu dillerde tarar:

- Arapça
- Çince (Basitleştirilmiş)
- Çince (Geleneksel)
- Dutch
- English
- French
- German
- Italian
- Korean
- Japanese
- Portekizce
- Spanish

Diğerleri sadece şu anda İngilizce.

### <a name="custom-classifiers"></a>Özel sınıflandırıcılar

Önceden eğitilmiş sınıflandırıcılar gereksinimlerinizi karşılamadığında kendi sınıflandırıcılarınızı oluşturabilir ve eğitebilirsiniz. Kendi çalışmanızı oluşturma konusunda daha fazla iş vardır, ancak bunlar kuruluşunuzun ihtiyaçlarına göre çok daha iyi uyarlanır.

Özel eğitilebilir sınıflandırıcıyı, kesinlikle kategoride yer alan örnekleri besleyerek oluşturmaya başlarsınız. Bu örnekleri işledikten sonra, hem eşleşen hem de eşleşmeyen örneklerin bir karışımını vererek test edebilirsiniz. Ardından sınıflandırıcı, belirli bir öğenin oluşturduğunuz kategoriye girip girmediğine ilişkin tahminlerde bulunur. Ardından, tahminlerinin doğruluğunu artırmaya yardımcı olmak için gerçek pozitifleri, gerçek negatifleri, hatalı pozitifleri ve hatalı negatifleri sıralayarak sonuçlarını onaylarsınız.

Sınıflandırıcıyı yayımladığınızda, SharePoint Online, Exchange ve OneDrive gibi konumlardaki öğeleri sıralar ve içeriği sınıflandırır. Sınıflandırıcıyı yayımladıktan sonra, ilk eğitim sürecine benzer bir geri bildirim işlemi kullanarak eğitmeye devam edebilirsiniz.

Örneğin, aşağıdakiler için eğitilebilir sınıflandırıcılar oluşturabilirsiniz:

- Yasal belgeler - avukat müşteri ayrıcalığı, kapanış kümeleri, iş bildirimi gibi
- Basın bültenleri, birleşme ve satın alma, anlaşmalar, iş veya pazarlama planları, fikri mülkiyet, patentler, tasarım belgeleri gibi stratejik iş belgeleri
- Faturalar, fiyat teklifleri, iş siparişleri, teklif belgeleri gibi fiyatlandırma bilgileri
- Finansal bilgiler - kurumsal yatırımlar, üç aylık veya yıllık sonuçlar gibi

#### <a name="process-flow-for-creating-custom-classifiers"></a>Özel sınıflandırıcılar oluşturmak için işlem akışı

Bekletme ilkeleri ve iletişim denetimi gibi uyumluluk çözümlerinde kullanılmak üzere bir sınıflandırıcı oluşturma ve yayımlama bu akışı izler. Özel eğitilebilir sınıflandırıcı oluşturma hakkında daha fazla ayrıntı için bkz. [Özel sınıflandırıcı oluşturma](classifier-get-started-with.md).

![işlem akışı özel sınıflandırıcısı.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Sınıflandırıcıları yeniden eğitme

Tüm özel eğitilebilir sınıflandırıcıların doğruluğunu artırmaya yardımcı olabilir ve gerçekleştirdikleri sınıflandırmanın doğruluğu hakkında geri bildirim sağlayabilirsiniz. Buna yeniden eğitme denir ve bu iş akışını izler.

> [!NOTE]
> Önceden eğitilmiş sınıflandırıcılar yeniden eğitilemez.

![sınıflandırıcı yeniden eğitme iş akışı.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Bekletme etiketleri](retention.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Belge parmakla yazdırma](document-fingerprinting.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
