---
title: Bir XDR Microsoft 365 Defender değerlendirme ve pilot Microsoft 365 Defender
description: Cihazları, Microsoft 365 Defender, verileri ve uygulamaları korumak için tasarlanmış bir güvenlik çözümünü test etmek ve bu çözümden deneyim yaşamak için test etmek üzere test edin.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 06/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 442ac9859f259479da556a9611880a61ab0413e0
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014416"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Değerlendirme ve pilot Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Microsoft 365 Defender, Microsoft 365 ortamınız genelinde uç nokta, e-posta, uygulamalar ve kimlikler dahil olmak üzere sinyali, tehdide ve uyarıyı otomatik olarak toplayan, bu bilgileri analiz eden ve analiz eden genişletilmiş bir algılama ve yanıt (XDR) çözümüdür. Kapsamlı AI ve otomasyondan yararlanarak saldırıları otomatik olarak durdurarak etkilenen varlıkları güvenli bir halde düzeltmeyi sağlar. Aşağıdaki makaleler, bir deneme ortamı ayarlama sürecinde size yollar; böylelikle bu ortamın özelliklerini ve özelliklerini Microsoft 365 Defender. 

Bu makalelere baktıkça adımlar, her bileşeni nasıl etkinleştirecek, ayarları nasıl yapılandıracak ve pilot bir grupla izlemeye nasıl başlanacaklarını gösterir. Hazır olduğunda değerlendirme ortamınızı doğrudan üretime dönüştürerek promosyonla bitirebilirsiniz.

Microsoft, değerlendirmenizi şu an için mevcut bir üretim aboneliğinde oluşturmanızı Office 365. Bu şekilde, gerçek dünyaya hemen öngörüler edinecek ve ayarları ortamınıza yönelik mevcut tehditlere karşı çalışacak şekilde ayar yapabilirsiniz. Deneyim kazandıktan ve platformda rahat olduktan sonra, her bileşeni tek tek üretime yükseltin.

## <a name="the-anatomy-of-an-attack"></a>Saldırının anatomisi

Microsoft 365 Defender tabanlı, birleşik, ihlal öncesi ve ihlal sonrası bir kurumsal savunma paketidir. Engelleme, *algılama**, soruşturma* ve uç *noktalar,* kimlikler, uygulamalar, e-posta, işbirliğine dayalı uygulamalar ve tüm verileri genelinde engelleme, algılama, soruşturma ve yanıt noktaları eşgüdüm sağlar.

Bu çizimde bir saldırı yapılıyor. Kimlik avı e-postası, e-posta ekini farkında olmayan ve kuruluşta çalışan bir çalışanın Gelen Kutusu'na gelir. Bu, kötü amaçlı yazılımları yükser ve bu da hassas verilerin çalınarak çalınarak bitilebilecek bir olay zincirine yol açıyor. Ancak bu durumda, Office 365 için Defender işlemdedir.

![Bu Microsoft 365 Defender tehdit zincirini nasıl durduracak?](../../media/defender/m365-defender-eval-threat-chain.png)

Çizimde:

- **Exchange Online Protection** için Microsoft Defender'ın bir parçası olan Office 365, kimlik avı e-postalarını algılayabilirsiniz ve gelen kutunuza hiçbir zaman gelmezken posta akış kurallarını kullanabilirsiniz.
- **Güvenli Office 365 için Defender** eki test ediyor ve zararlı olduğunu tespit ediyor, dolayısıyla gelen posta kullanıcı tarafından işleme engel olur veya ilkeler postanın hiçbir şekilde gelmeye engel olur.
- **Uç Nokta için Defender** , şirket ağına bağlanan cihazları yönetir ve aksi halde açıklardan yararlanabilecek cihaz ve ağ açıklarını algılar.
- **Kimlik için Defender ayrıcalık** yükseltmesi veya yüksek riskli uzar hareketi gibi daha önce olan hesap değişikliklerinin olduğunu dikkate alır. Ayrıca, güvenlik ekibi tarafından düzeltme için kısıtlanmamış Kerberos temsilcisi gibi kolayca yararlanan kimlik sorunları hakkında da bilgi sağlar.
- **Bulut Uygulamaları için Microsoft Defender** bildirim, imkansız seyahat, kimlik bilgileri erişimi ve olağandışı indirme, dosya paylaşımı veya posta iletme etkinliği gibi anormal davranışlara sahip ve bunları güvenlik ekibine raporlar.

### <a name="microsoft-365-defender-components"></a>Microsoft 365 Defender bileşenleri

Microsoft 365 Defender, birlikte çalışan bu güvenlik teknolojilerden ileri türetir. XDR ve diğer bileşenlerin özelliklerinden yararlanabilmek için bu bileşenlerin Microsoft 365 Defender. Bir veya iki kullanımıyla da kazançlar ve verimlilik elde ettiysiniz. 

|Bileşen  |Açıklama  |Başvuru malzemesi  |
|---------|---------|---------|
|Kimlik için Microsoft Defender     |      Identity için Microsoft Defender, Active Directory sinyallerini kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırr.     |     [Kimlik için Microsoft Defender nedir?](/defender-for-identity/what-is)   |
|Exchange Online Protection     |      Exchange Online Protection, bulut tabanlı yerel SMTP geçişi ve istenmeyen posta ve kötü amaçlı yazılımlara karşı korunmanıza yardımcı olan filtreleme hizmetidir.      |   [Exchange Online Protection (EOP) genel bakış - Office 365](../office-365-security/overview.md)     |
|Office 365 için Microsoft Defender     |     Microsoft Defender For Office 365, e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya atacak kötü amaçlı tehditlere karşı organizasyonlarınızı korur.      |    [Office 365 için Microsoft Defender - Office 365](../office-365-security/overview.md)    |
|Uç Nokta için Microsoft Defender     |     Uç Nokta için Microsoft Defender cihaz koruması, ihlal sonrası algılama, otomatik soruşturma ve önerilen yanıt için birleşik bir platformdur.      |   [Uç Nokta için Microsoft Defender - Windows güvenlik](../defender-endpoint/microsoft-defender-endpoint.md)    |
|Bulut Uygulamaları için Microsoft Defender     |      Bulut Uygulamaları için Microsoft Defender, bulut uygulamalarınız için derin görünürlük, güçlü veri denetimleri ve gelişmiş tehdit koruması sağlayan kapsamlı bir cross-SaaS çözümüdür.       |    [Bulut Uygulamaları için Defender nedir?](/cloud-app-security/what-is-cloud-app-security)    |
|Azure AD Identity Protection|Azure AD Kimlik Koruması, milyar oturum açma girişimlerinden risk verilerini değerlendirir ve ortamınıza her oturum açmanın riskini değerlendirmek için bu verileri kullanır. Bu veriler, Koşullu Erişim ilkelerinin nasıl yapılandırıldıklarına bağlı olarak, Azure AD tarafından hesap erişimine izin vermek veya engellemek için kullanılır. Azure AD Identity Protection, azure addan ayrı Microsoft 365 Defender. Bu, yeni e-Azure Active Directory Premium P2.|[Kimlik Koruması nedir?](/azure/active-directory/identity-protection/overview-identity-protection)|
| | | |

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender mimarisi

Aşağıdaki diyagramda, önemli bileşenleri ve tümleştirmeleri temel alan Microsoft 365 Defender bir mimari gösterilmiştir. *Her* Defender bileşeni için ayrıntılı mimari ve kullanım durumu senaryoları, bu makale dizisi boyunca verilmiştir.

![Microsoft 365 Defender düzeyde bir mimariye sahiptir.](../../media/defender/m365-defender-eval-architecture.png)

Bu şekilde:

- Microsoft 365 Defender, tüm Defender bileşenlerinden gelen sinyalleri birleştirarak etki alanları arasında genişletilmiş algılama ve yanıt (XDR) sağlar. Buna birleşik bir olay sırası, saldırılarını durdurmak için otomatik yanıt, öz güveni (güvenliği tehlikeye atılmış cihazlar, kullanıcı kimlikleri ve posta kutuları için), çapraz tehdit avı ve tehdit çözümlemeleri dahildir.
- Güvenlik için Microsoft Defender Office 365 e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı kuruluşu korur. Bu etkinliklerden elde edilen sinyalleri, diğer Microsoft 365 Defender. Exchange Online Protection (EOP), gelen e-postalar ve ekler için  end-uç koruma sağlamak için tümleşiktir.
- Identity için Microsoft Defender, Active Directory Federasyon Hizmetleri (AD FS) ve şirket içi Active Directory Etki Alanı Hizmetleri'ne (AD DS) çalışan sunuculardan sinyal toplar. Karma kimlik ortamınızı korumak için bu sinyalleri kullanır ve bu da şirket içi ortamda daha sonra iş istasyonlarında güvenliği tehlikeye atılmış hesapları kullanan korsanlara karşı koruma sağlar.
- Uç Nokta için Microsoft Defender, kurum tarafından kullanılan cihazlardan sinyal toplar ve bu cihazları korur.
- Bulut Uygulamaları için Microsoft Defender, kurumuz tarafından bulut uygulamalarının kullanımından gelen sinyalleri toplar ve hem tahmin hem de işaretsiz bulut uygulamaları dahil, ortamınız ile bu uygulamalar arasında akan verileri korur.
- Azure AD Kimlik Koruması, milyar oturum açma girişimlerinden risk verilerini değerlendirir ve ortamınıza her oturum açmanın riskini değerlendirmek için bu verileri kullanır. Bu veriler, Koşullu Erişim ilkelerinin nasıl yapılandırıldıklarına bağlı olarak, Azure AD tarafından hesap erişimine izin vermek veya engellemek için kullanılır. Azure AD Identity Protection, azure addan ayrı Microsoft 365 Defender. Bu, yeni e-Azure Active Directory Premium P2.  

Bu çizimde yer alan ek isteğe bağlı mimari bileşenleri:

- Tüm veri bileşenlerinden ayrıntılı sinyal Microsoft 365 Defender bileşenleri Microsoft Sentinel ile tümleştirildi ve diğer günlük kaynaklarıyla birleştirildi ve tam SIEM ve SOAR özellikleriyle içgörüler sunabilirsiniz.

## <a name="the-evaluation-process"></a>Değerlendirme süreci

Microsoft, aşağıdakiler için Microsoft 365 bileşenlerini etkinleştirmenizi önermektedir:

![Microsoft 365 Defender düzey değerlendirme sürecidir.](../../media/defender/m365-defender-eval-process.png)

Aşağıdaki tabloda bu çizim açık gösterilmiştir.

|      |Adım  |Açıklama  |
|------|---------|---------|
|1     | [Değerlendirme ortamı oluşturma](eval-create-eval-environment.md)       |Bu adım, deneme sürümü lisansına sahip Microsoft 365 Defender.         |
|2     | [Kimlik için Defender'ı etkinleştirme](eval-defender-identity-overview.md)        | Mimari gereksinimlerini gözden geçirmek, değerlendirmeyi etkinleştirmek ve farklı saldırı türlerini belirlemek ve düzeltmeye yönelik öğreticileri gözden geçirmek.   |
|3     | [Windows için Defender'ı Office 365 ](eval-defender-office-365-overview.md)       | Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun. Bu bileşen, Exchange Online Protection özellikleri içerir ve dolayısıyla ikisini de burada *değerlendirirsiniz*.      |
|4     | [Uç Nokta için Defender'ı Etkinleştir ](eval-defender-endpoint-overview.md)       | Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun.         |
|5     | [Bulut Uygulamaları için Microsoft Defender'ı etkinleştirme](eval-defender-mcas-overview.md)        |  Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun.        |
|6     | [Tehditleri araştırma ve yanıtlama](eval-defender-investigate-respond.md)        |   Bir saldırının benzetimini yapmak ve olay yanıtı özelliklerini kullanmaya başlamak.      |
|7     | [Denemeyi üretime yükseltin](eval-defender-promote-to-production.md)        | Yeni Microsoft 365 tek üretime yükseltin.        |
| | | |

Bu, genellikle özellikleri dağıtmak ve yapılandırmak için ne kadar çaba gerektirmektedir? temel alarak yeteneklerin değerini hızlı bir şekilde elde etmek için tasarlanmış ve yaygın olarak önerilen bir sıradır. Örneğin, Office 365 için Defender, Uç nokta için Defender'da cihazları kaydetmek için gerekenden daha kısa sürede ya yapılandırabilirsiniz. Kuşkusuz, iş ihtiyaçlarını karşılayacak bileşenlere öncelik ve bunları farklı bir sırada etkinleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Değerlendirme Microsoft 365 Defender Oluşturma](eval-create-eval-environment.md)
