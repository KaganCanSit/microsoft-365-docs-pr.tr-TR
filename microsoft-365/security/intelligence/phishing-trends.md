---
title: Kimlik avı eğilimleri ve teknikleri
ms.reviewer: ''
description: Kimlik avı tekniklerini belirleme hakkında bilgi edinin
keywords: güvenlik, kötü amaçlı yazılım, kimlik avı, bilgi, dolandırıcılık, sosyal mühendislik, yem, yem, yem, koruma, eğilimler, hedefli saldırı, zıpkınla kimlik avı, balina avcılığı
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: c56478f4dbe496f7e2080e9c73d6466df0e2c5d7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666756"
---
# <a name="phishing-trends-and-techniques"></a>Kimlik avı eğilimleri ve teknikleri

Kimlik avı saldırıları genellikle sosyal mühendislik yemleri kullanan veya içeriği çeken dolandırıcılıklardır. Kimlik avı saldırılarında kullanılan en yaygın yöntemlerden biri, genellikle e-posta olmak üzere bir kimlik avı sitesine bağlanan yasal görünümlü iletişimdir. Kimlik avı sitesi genellikle kullanıcıların kimlik bilgilerini ve hesap bilgilerini girmenizi gerektiren oturum açma sayfalarını taklit eder. Ardından kimlik avı sitesi, hassas bilgileri kullanıcı sağlar sağlamaz yakalar ve saldırganların bilgilere erişmesini sağlar.

Aşağıda, saldırganların bilgileri çalmaya veya cihazlarınıza erişmeye çalışmak için en yaygın kimlik avı tekniklerinden bazıları yer alır.

## <a name="invoice-phishing"></a>Fatura kimlik avı

Bu dolandırıcılıkta saldırgan, bilinen bir satıcıdan veya şirketten kalan bir faturanız olduğunu belirten bir e-postayla sizi kandırmaya çalışır. Ardından faturanıza erişmeniz ve ödemeniz için bir bağlantı sağlar. Siteye eriştiğinizde saldırgan kişisel bilgilerinizi ve fonlarınızı çalmaya hazır hale gelmektedir.

## <a name="paymentdelivery-scam"></a>Ödeme/teslimat dolandırıcılığı

Ödeme bilgilerinizin yaygın olarak bilinen bir satıcı veya tedarikçiyle güncelleştirilebilmesi için kredi kartı veya diğer kişisel bilgileri sağlamanız istenir. Sipariş ettiğiniz malların teslimini alabilmeniz için güncelleştirme istenir. Genel olarak, şirket hakkında bilgi sahibi olabilirsiniz ve geçmişte büyük olasılıkla onlarla iş yapmış olabilirsiniz. Ancak, yakın zamanda satın aldığınız öğelerin hiçbirinin farkında değilsiniz.

## <a name="tax-themed-phishing-scams"></a>Vergi temalı kimlik avı dolandırıcılığı

Yaygın bir IRS kimlik avı dolandırıcılığı, IRS'ye borcun olduğunu belirten acil bir e-posta mektubu almaktır. Siteye zamanında erişmezseniz ve vergilerinizi ödemezseniz, e-posta genellikle yasal işlemleri tehdit eder. Siteye eriştiğinizde saldırganlar kişisel kredi kartınızı veya banka bilgilerinizi çalabilir ve hesaplarınızı boşaltabilir.

## <a name="downloads"></a>Indirme

Saldırgan, PDF gibi bir belge eki açmanızı veya indirmenizi isteyen sahte bir e-posta gönderir. Ek genellikle belgeyi açmak için e-posta veya dosya paylaşım web siteleri gibi başka bir sitede oturum açmanızı isteyen bir ileti içerir. Oturum açma kimlik bilgilerinizi kullanarak bu kimlik avı sitelerine eriştiğinizde, saldırgan artık bilgilerinize erişebilir ve hakkınızda ek kişisel bilgiler edinebilir.

## <a name="phishing-emails-that-deliver-other-threats"></a>Diğer tehditleri teslim eden kimlik avı e-postaları

Kimlik avı e-postaları genellikle etkilidir, bu nedenle saldırganlar bazen fidye [yazılımlarını](/security/compass/human-operated-ransomware) e-postalardaki bağlantılar veya ekler aracılığıyla dağıtmak için kullanır. Çalıştırıldığında fidye yazılımı dosyaları şifreler ve dosyalarınıza erişmek için bir miktar para ödemenizi isteyen bir fidye notu görüntüler.

[Teknik destek dolandırıcılığı](support-scams.md) web sitelerine bağlantılar içeren kimlik avı e-postaları da gördük. Bu web siteleri sizi çeşitli korku taktikleri kullanarak çağrı hattı çağırmanız ve ilgili cihaz, platform veya yazılım sorunlarını düzelten gereksiz "teknik destek hizmetleri" için ödeme yapması için çeşitli korkutma taktikleri kullanır.

## <a name="spear-phishing"></a>Zıpkınla kimlik avı

Mızraklı kimlik avı, yüksek oranda özelleştirilmiş yem içeriği içeren hedefli bir kimlik avı saldırısıdır. Saldırganlar genellikle hedeflenen hedefleriyle ilgili sosyal medyayı ve diğer bilgi kaynaklarını araştırma yoluyla keşif çalışmaları yapar.

Zıpkınla kimlik avı, sahte sitelerde oturum açmak ve kimlik bilgilerini bölmek için sizi kandırmayı içerebilir. Ayrıca, otomatik olarak kötü amaçlı yazılım yükleyen bağlantılara tıklayarak da belgeleri açmanız için sizi cezbedebilirim. Bu kötü amaçlı yazılım mevcut olduğunda, saldırganlar virüslü bilgisayarı uzaktan işleyebilir.

yerleştirilen kötü amaçlı yazılım, gelişmiş kalıcı tehdit (APT) olarak bilinen daha gelişmiş bir saldırı için giriş noktası görevi görür. APT'ler, denetimi sağlamak ve uzun süreler boyunca verileri çalmak için tasarlanmıştır. Saldırganlar daha gizli korsanlık araçları dağıtmayı, diğer bilgisayarlara daha sonra taşınmayı, ayrıcalıklı hesapları tehlikeye atmayı veya oluşturmayı ve güvenliği aşılmış ağlardan düzenli olarak bilgi sızdırmayı deneyebilir.

## <a name="whaling"></a>Balina

Balina avcılığı, belirli şirketlerdeki üst düzey veya üst düzey yöneticilere kimlik bilgilerine ve/veya banka bilgilerine erişmeleri için yönlendirilen bir kimlik avı biçimidir. E-postanın içeriği yasal bir celp, müşteri şikayeti veya başka bir yönetici sorunu olarak yazılabilir. Bu tür bir saldırı, kuruluş içinde APT saldırısına da yol açabilir.

## <a name="business-email-compromise"></a>İş e-posta güvenliğinin aşılmasına neden olan

İş e-posta güvenliğinin aşılması (BEC), sık sık yabancı tedarikçilerle çalışan veya para havalesi yapan işletmeleri hedefleyen karmaşık bir dolandırıcılıktır. BEC saldırganları tarafından kullanılan en yaygın şemalardan biri, mızraklı kimlik avı saldırısı yoluyla bir şirketin ağına erişim elde etmeyi içerir. Saldırgan, hedefledikleri şirkete benzer bir etki alanı oluşturur veya kullanıcıların para aktarımları için kişisel hesap bilgilerini serbest bırakmaları için e-postalarını sahtekarlığa sürükler.

## <a name="more-information-about-phishing-attacks"></a>Kimlik avı saldırıları hakkında daha fazla bilgi

En son kimlik avı saldırıları, teknikler ve eğilimler hakkında bilgi için Microsoft [Güvenlik blogu'nda](https://www.microsoft.com/security/blog/product/windows/) şu girdileri okuyabilirsiniz:

- [Kimlik avı avcıları PDF eklerini kullanarak basit ama etkili sosyal mühendislik tekniklerini açığa çıkarıyor](https://cloudblogs.microsoft.com/microsoftsecure/2017/01/26/phishers-unleash-simple-but-effective-social-engineering-techniques-using-pdf-attachments/?source=mmpc)
- [Vergi dosyası sezonunda vergi temalı kimlik avı ve kötü amaçlı yazılım saldırıları çoğalıyor](https://cloudblogs.microsoft.com/microsoftsecure/2017/03/20/tax-themed-phishing-and-malware-attacks-proliferate-during-the-tax-filing-season/?source=mmpc)
- [E-postalar gibi kimlik avı teknik destek dolandırıcılığına yol açar](https://cloudblogs.microsoft.com/microsoftsecure/2017/08/07/links-in-phishing-like-emails-lead-to-tech-support-scam/?source=mmpc)
