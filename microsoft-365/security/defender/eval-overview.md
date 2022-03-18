---
title: Bir XDR çözümü Microsoft 365 Defender değerlendirme ve pilot uygulama
description: XDR güvenliği nedir? Microsoft XDR'sini aynı Microsoft 365 Defender? Cihazları, kimlikleri, verileri ve Microsoft 365 Defender korumak üzere tasarlanmış bir güvenlik çözümünü test etmek ve bu çözüm üzerinde pilot çalışma ortamınızı planlamak için bu blog serisini kullanın. XDR siber güvenlik yolculuğunu burada başlatarak bu testi üretime attır.
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
ms.openlocfilehash: 2502a4781e9844fca8de3113d64ee1836efddabd
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63557901"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Değerlendirme ve pilot Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>Bu makale serisi nasıl çalışır?

Bu makale dizisi, deneme XDR ortamını *, sona* doğru ayarlama işleminin tamamına adım atacak şekilde tasarlanmıştır; böylece, Microsoft 365 Defender'in özelliklerini ve özelliklerini değerlendirerek, hatta hazır olduğunda ve hazırsanız değerlendirme ortamını doğrudan üretime yükseltebilirsiniz.

XDR'i ilk kez düşünüyorsanız, çözümün ne kadar kapsamlı olduğunu ilk kez düşünmek için bu 7 bağlantılı makaleyi tarayamazsanız.

- [Ortamı oluşturma](eval-create-eval-environment.md)
- Bu Microsoft XDR teknolojisinin her bir teknolojisini ayarlama veya öğrenme
  - [Kimlik için Microsoft Defender](eval-defender-identity-overview.md)
  - [Office için Microsoft Defender](eval-defender-office-365-overview.md)
  - [Uç Nokta için Microsoft Defender](eval-defender-endpoint-overview.md)
  - [Bulut Uygulamaları için Microsoft Defender](eval-defender-mcas-overview.md)
- [Bu XDR kullanarak araştırma ve yanıtlama](eval-defender-investigate-respond.md)
- [Deneme ortamını üretim ortamına tanıtma](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender bir Microsoft XDR siber güvenlik çözümüdür

Microsoft 365 Defender, Microsoft 365 ortamınız genelinde uç nokta, e-posta, uygulamalar ve kimlikler dahil olmak üzere sinyali, tehdide ve uyarıyı otomatik olarak toplayan, birbiriyle ilgili olan ve analiz eden bir  **e-posta algılama ve yanıt (XDR)** *çözümüdür*. Yapay zekadan (AI) ve otomasyondan yararlanarak  saldırıları otomatik olarak durdurur ve etkilenen varlıkları güvenli bir durumda düzeltmeye yöneliktir.

XDR'i, tek bir yerde güvenlik, uç noktayı (uç noktada algılama ve yanıtlama veya EDR), e-posta, uygulama ve kimlik güvenliğinin bir sonraki adımı olarak düşünebilirsiniz.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Değerlendirmeyle ilgili Microsoft Microsoft 365 Defender

Microsoft, değerlendirmenizi şu an için mevcut bir üretim aboneliğinde oluşturmanızı Office 365. Bu şekilde, gerçek dünyaya hemen öngörüler edinecek ve ayarları ortamınıza yönelik mevcut tehditlere karşı çalışacak şekilde ayar yapabilirsiniz. Deneyim kazandıktan ve platformda rahat olduktan sonra, her bileşeni tek tek üretime yükseltin.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>Siber güvenlik saldırılarının anatomisi

Microsoft 365 Defender tabanlı, birleşik, ihlal öncesi ve ihlal sonrası bir kurumsal savunma paketidir. Engelleme, *algılama**, soruşturma* ve uç *noktalar,* kimlikler, uygulamalar, e-posta, işbirliğine dayalı uygulamalar ve tüm verileri genelinde engelleme, algılama, soruşturma ve yanıt noktaları eşgüdüm sağlar.

Bu çizimde bir saldırı yapılıyor. Kimlik avı e-postası, e-posta ekini farkında olmayan ve kuruluşta çalışan bir çalışanın Gelen Kutusu'na gelir. Bu, kötü amaçlı yazılımları yükser ve bu da hassas verilerin çalınarak çalınarak bitilebilecek bir olay zincirine yol açıyor. Ancak bu durumda, Office 365 için Defender işlemdedir.

![Bu Microsoft 365 Defender tehdit zincirini nasıl durduracak?](../../media/defender/m365-defender-eval-threat-chain.png)

Çizimde:

- **Exchange Online Protection** için Microsoft Defender'ın bir parçası olan Office 365, kimlik avı e-postalarını algılayabilirsiniz ve gelen kutunuza hiçbir zaman gelmezken posta akış kurallarını kullanabilirsiniz.
- **Güvenli Office 365 için Defender** eki test ediyor ve zararlı olduğunu tespit ediyor, dolayısıyla gelen posta kullanıcı tarafından işleme engel olur veya ilkeler postanın hiçbir şekilde gelmeye engel olur.
- **Uç Nokta için Defender** , şirket ağına bağlanan cihazları yönetir ve aksi halde açıklardan yararlanabilecek cihaz ve ağ açıklarını algılar.
- **Kimlik için Defender ayrıcalık** yükseltmesi veya yüksek riskli uzar hareketi gibi daha önce olan hesap değişikliklerinin olduğunu dikkate alır. Ayrıca, güvenlik ekibi tarafından düzeltme için kısıtlanmamış Kerberos temsilcisi gibi kolayca yararlanan kimlik sorunları hakkında da bilgi sağlar.
- **Bulut Uygulamaları için Microsoft Defender** bildirim, imkansız seyahat, kimlik bilgileri erişimi ve olağandışı indirme, dosya paylaşımı veya posta iletme etkinliği gibi anormal davranışlara sahip ve bunları güvenlik ekibine raporlar.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender, kimliği, verileri ve uygulamaları güvenlik altına almak için bu bileşenleri kullanın

Microsoft 365 Defender, birlikte çalışan bu güvenlik teknolojilerden ileri türetir. XDR ve diğer bileşenlerin özelliklerinden yararlanabilmek için bu bileşenlerin Microsoft 365 Defender. Bir veya iki kullanımıyla da kazançlar ve verimlilik elde ettiysiniz.

|Bileşen|Açıklama|Başvuru malzemesi|
|---|---|---|
|Kimlik için Microsoft Defender|Identity için Microsoft Defender, Active Directory sinyallerini kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırr.|[Kimlik için Microsoft Defender nedir?](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection, bulut tabanlı yerel SMTP geçişi ve istenmeyen posta ve kötü amaçlı yazılımlara karşı korunmanıza yardımcı olan filtreleme hizmetidir.|[Exchange Online Protection (EOP) genel bakış - Office 365](../office-365-security/overview.md)|
|Office 365 için Microsoft Defender|Microsoft Defender For Office 365, e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya atacak kötü amaçlı tehditlere karşı organizasyonlarınızı korur.|[Office 365 için Microsoft Defender - Office 365](../office-365-security/overview.md)|
|Uç Nokta için Microsoft Defender|Uç Nokta için Microsoft Defender cihaz koruması, ihlal sonrası algılama, otomatik soruşturma ve önerilen yanıt için birleşik bir platformdur.|[Uç Nokta için Microsoft Defender - Windows güvenlik](../defender-endpoint/microsoft-defender-endpoint.md)|
|Bulut Uygulamaları için Microsoft Defender|Bulut Uygulamaları için Microsoft Defender, bulut uygulamalarınız için derin görünürlük, güçlü veri denetimleri ve gelişmiş tehdit koruması sağlayan kapsamlı bir cross-SaaS çözümüdür.|[Bulut Uygulamaları için Defender nedir?](/cloud-app-security/what-is-cloud-app-security)|
|Azure AD Identity Protection|Azure AD Kimlik Koruması, milyar oturum açma girişimlerinden risk verilerini değerlendirir ve ortamınıza her oturum açmanın riskini değerlendirmek için bu verileri kullanır. Bu veriler, Koşullu Erişim ilkelerinin nasıl yapılandırıldıklarına bağlı olarak, Azure AD tarafından hesap erişimine izin vermek veya engellemek için kullanılır. Azure AD Identity Protection, azure addan ayrı Microsoft 365 Defender. Bu, yeni e-Azure Active Directory Premium P2.|[Kimlik Koruması nedir?](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

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

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Microsoft SIEM ve SOAR, veri kaynağından Microsoft 365 Defender

Bu çizimde yer alan ek isteğe bağlı mimari bileşenleri:

- **Tüm veri bileşenlerinden ayrıntılı sinyal Microsoft 365 Defender bileşenleri Microsoft Sentinel** ile tümleştirildi ve diğer günlük kaynaklarıyla birleştirildi ve tam SIEM ve SOAR özellikleriyle içgörüler sunabilirsiniz.
- Azure SIEM olan ve XDR olarak Microsoft 365 Defender olan **Microsoft Sentinel'i** kullanma hakkında daha fazla bilgi için, bu Genel Bakış makalesine ve [](/azure/sentinel/microsoft-365-defender-sentinel-integration) Microsoft Sentinel ve Microsoft 365 Defender tümleştirme adımlarına [göz atabilirsiniz](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE).
- Microsoft Sentinel'de SOAR hakkında daha fazla bilgi için (Microsoft Sentinel Depolama Havuzu'GitHub çalışma kitaplarının bağlantıları dahil), lütfen bu [makaleyi okuyun](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Siber güvenliği Microsoft 365 Defender değerlendirme süreci

Microsoft, aşağıdakiler için Microsoft 365 bileşenlerini etkinleştirmenizi önermektedir:

![Microsoft 365 Defender düzey değerlendirme sürecidir.](../../media/defender/m365-defender-eval-process.png)

Aşağıdaki tabloda bu çizim açık gösterilmiştir.

|Adım|Bağlantı|Açıklama|
|---|---|---|
|1|[Değerlendirme ortamı oluşturma](eval-create-eval-environment.md)|Bu adım, deneme sürümü lisansına sahip Microsoft 365 Defender.|
|2|[Kimlik için Defender'ı etkinleştirme](eval-defender-identity-overview.md)|Mimari gereksinimlerini gözden geçirmek, değerlendirmeyi etkinleştirmek ve farklı saldırı türlerini belirlemek ve düzeltmeye yönelik öğreticileri gözden geçirmek.|
|3|[Windows için Defender'ı Office 365](eval-defender-office-365-overview.md)|Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun. Bu bileşen, Exchange Online Protection özellikleri içerir ve dolayısıyla ikisini de burada *değerlendirirsiniz*.|
|4|[Uç Nokta için Defender'ı Etkinleştir](eval-defender-endpoint-overview.md)|Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun.|
|5|[Bulut Uygulamaları için Microsoft Defender'ı etkinleştirme](eval-defender-mcas-overview.md)|Mimari gereksinimlerini karşılarsınız, değerlendirmeyi etkinleştirin ve ardından pilot ortamı oluşturun.|
|6|[Tehditleri araştırma ve yanıtlama](eval-defender-investigate-respond.md)|Bir saldırının benzetimini yapmak ve olay yanıtı özelliklerini kullanmaya başlamak.|
|7|[Denemeyi üretime yükseltin](eval-defender-promote-to-production.md)|Yeni Microsoft 365 tek üretime yükseltin.|
||||

Bu, genellikle özellikleri dağıtmak ve yapılandırmak için ne kadar çaba gerektirmektedir? temel alarak yeteneklerin değerinden hızlı bir şekilde yararlanabilmek için tasarlanmış ve yaygın olarak önerilen bir sıradır. Örneğin, Office 365 için Defender, Uç nokta için Defender'da cihazları kaydetmek için gerekenden daha kısa sürede ya yapılandırabilirsiniz. Kuşkusuz, iş ihtiyaçlarını karşılayacak bileşenleri önceliklendirmeli ve bunları farklı bir sırada etkinleştirebilirsiniz.

## <a name="go-to-the-next-step"></a>Sonraki Adıma gitme

[Değerlendirme Ortamı hakkında ve/veya Microsoft 365 Defender hakkında bilgi](eval-create-eval-environment.md)
