---
title: Kimlik avı saldırılarına karşı koruma
ms.reviewer: ''
description: Kimlik avının nasıl çalıştığı, kötü amaçlı yazılımların cihazlarınıza nasıl çalıştığı ve kendinizi korumak için neler yapabileceğiniz hakkında bilgi edinin
keywords: güvenlik, kötü amaçlı yazılım, kimlik avı, bilgi, dolandırıcılık, sosyal mühendislik, yem, yem, koruma, eğilimler, hedefli saldırı
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
ms.openlocfilehash: 1f414c80d3c0b5478112cd402f8e3839908787d4
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666778"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Kimlik avı saldırılarına karşı koruma

Kimlik avı saldırıları e-postalar, web siteleri, kısa mesajlar veya diğer elektronik iletişim biçimleri aracılığıyla hassas bilgileri çalmaya çalışır. Yasal şirketlerden veya bireylerden gelen resmi iletişim gibi görünmeye çalışırlar.

Siber suçlular genellikle kullanıcı adlarını, parolaları, kredi kartı bilgilerini, banka hesabı bilgilerini veya diğer kimlik bilgilerini çalmaya çalışır. Çalınan bilgileri korsanlık, kimlik hırsızlığı veya doğrudan banka hesaplarından ve kredi kartlarından para çalma gibi kötü amaçlı amaçlarla kullanırlar. Bu bilgiler siber suçlu yeraltı pazarlarında da satılabilir.

Sosyal mühendislik saldırıları, kullanıcının karar alma sürecindeki olası atlamalarından yararlanmak için tasarlanmıştır. Hassas veya kişisel bilgileri e-posta veya bilinmeyen web siteleri aracılığıyla ya da telefon üzerinden sağlamayı unutmayın ve hiçbir zaman sağlamayın. Kimlik avı e-postalarının meşru görünecek şekilde tasarlandığını unutmayın.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Kimlik avı dolandırıcılığı işaretlerini öğrenin

En iyi koruma farkındalık ve eğitimdir. E-postalar tanınan bir kaynaktan gelmiş olsa bile, istenmeyen e-postalardaki ekleri veya bağlantıları açmayın. E-posta beklenmeyen bir durumsa, eki açma konusunda dikkatli olun ve URL'yi doğrulayın.

Kuruluşlar, çalışanlarını kişisel veya finansal bilgi isteyen iletişimlere karşı dikkatli olacak şekilde eğitmeli ve eğitmelidir. Ayrıca çalışanlara tehdidi derhal şirketin güvenlik operasyonları ekibine bildirmelerini de bildirmeleri gerekir.

Kimlik avı dolandırıcılığıyla ilgili birkaç telltale işareti şunlardır:

* E-postalarda sağlanan bağlantılar veya URL'ler **doğru konumu göstermiyor** veya e-postayı gönderenle bağlantılı olmayan bir üçüncü taraf sitesini işaret ediyor. Örneğin, aşağıdaki görüntüde sağlanan URL, alınacağı URL ile eşleşmiyor.

    ![url'nin üzerine gelme örneği.](../../media/security-intelligence-images/url-hover.png)

* Sosyal güvenlik numaraları, banka veya finansal **bilgiler gibi kişisel bilgiler için bir istek** vardır. Resmi iletişimler genellikle sizden e-posta biçiminde kişisel bilgiler istemez.

* **E-posta adresindeki öğeler, geçerli bir e-posta** adresine yeterince benzeyecek, ancak sayı veya harf eklemiş olacak şekilde değiştirilir.

* İleti **beklenmeyen ve istenmeyen** bir iletidir. Bir varlıktan veya nadiren anlaşma yaptığınız bir kişiden aniden bir e-posta alırsanız, bu e-postanın şüpheli olduğunu düşünün.

* İleti veya ek **, makroları etkinleştirmenizi, güvenlik ayarlarını ayarlamanızı veya uygulamaları yüklemenizi** ister. Normal e-postalar bunu yapmanızı istemez.

* İleti **hatalar** içeriyor. Yasal kurumsal iletilerde yazım veya dil bilgisi hataları olması veya yanlış bilgi içerme olasılığı daha düşüktür.

* **Gönderen adresi iletideki imzayla eşleşmiyor**. Örneğin, bir e-posta Contoso Corp'dan Mary'den alınmış olarak bildirilir, ancak gönderenin adresi ali<span></span>@example.com şeklindedir.

* "To" alanında **birden çok alıcı** var ve bunlar rastgele adresler gibi görünüyor. Şirket iletileri normalde doğrudan tek tek alıcılara gönderilir.

* İletideki selamlama **size kişisel olarak hitap etmiyor**. Yanlışlıkla farklı bir kişiye hitap eden iletiler dışında, adınızı kötüye kullanan veya adınızı doğrudan e-posta adresinizden çeken selamlamalar kötü amaçlı olabilir.

* Web sitesi tanıdık görünüyor ancak **tutarsızlıklar veya tam olarak doğru olmayan şeyler** var. Uyarı işaretleri eski logolar, yazım hataları içerir veya kullanıcılardan yasal oturum açma web siteleri tarafından istenmeyen ek bilgiler vermelerini ister.

* Açılan sayfa **canlı bir sayfa değil**, bildiğiniz site gibi görünecek şekilde tasarlanmış bir resimdir. Kimlik bilgilerini isteyen bir açılır pencere görüntülenebilir.

Şüpheli e-postaların gerçekten meşru olup olmadığını doğrulamak için şüpheli kanallardan işletmeyle iletişime geçin.

## <a name="software-solutions-for-organizations"></a>Kuruluşlar için yazılım çözümleri

* [Microsoft Edge](/microsoft-edge/deploy/index) ve [Windows Defender Application Guard](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md), Microsoft'un sektör lideri Hyper-V sanallaştırma teknolojisini kullanarak hedeflenen saldırıların artan tehdidine karşı koruma sağlar. Göz atılan bir web sitesine güvenilmezse, Hyper-V kapsayıcısı bu cihazı ağınızın geri kalanından yalıtarak kurumsal verilerinize erişimi engeller.

* [Microsoft Exchange Online Koruması (EOP),](https://products.office.com/exchange/exchange-email-security-spam-protection) acil durumlar sırasında ve sonrasında e-posta erişimini korurken istenmeyen postalara ve kötü amaçlı yazılımlara karşı kurumsal düzeyde güvenilirlik ve koruma sunar.  EOP, çeşitli filtreleme katmanlarını kullanarak, istenmeyen posta filtreleme için toplu posta denetimleri ve uluslararası istenmeyen postalar gibi koruma hizmetlerinizi daha da geliştirecek farklı denetimler sağlayabilir.

* E-postanızı, dosyalarınızı ve çevrimiçi depolama alanınızı kötü amaçlı yazılımlara karşı korumaya yardımcı olmak için [Office 365 için Microsoft Defender](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) kullanın. Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online ve OneDrive İş bütünsel koruma sunar. Güvenli olmayan eklere karşı koruma sağlayarak ve kötü amaçlı bağlantılara karşı korumayı genişleterek, sıfır gün daha iyi koruma sağlamak için Exchange Online Protection güvenlik özelliklerini tamamlar.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Kimlik avı dolandırıcılığı kurbanıysanız yapmanız gerekenler

Kimlik avı saldırısı kurbanı olduğunuzu düşünüyorsanız:

1. İş bilgisayarındaysanız BT yöneticinize başvurun
2. Hesaplarla ilişkili tüm parolaları hemen değiştirin
3. Sahte etkinlikleri bankanıza ve kredi kartı şirketinize bildirin

### <a name="reporting-spam"></a>İstenmeyen posta raporlama

- **Outlook.com**: Kişisel bilgileri soran şüpheli bir e-posta iletisi alırsanız, Outlook gelen kutunuzdaki iletinin yanındaki onay kutusunu seçin. **Gereksiz'in** yanındaki oku ve ardından **Kimlik Avı'nı** seçin.

- **Microsoft Office Outlook**: Şüpheli iletideyken şeritten **Rapor iletisi'ni** ve ardından **Kimlik Avı'nı** seçin.

- **Microsoft 365**: Gereksiz veya kimlik avı örneğini analiz için [Microsoft'a göndermek için Microsoft 365 Defender'daki Gönderimler portalını](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft) kullanın. Daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Kimlik Avına Karşı Koruma Çalışma Grubu**: phishing-report@us-cert.gov. Grup, kimlik avı dolandırıcılığı ve korsanlarla mücadele etmek için gönderilen e-postalardan oluşturulan raporları kullanır. ISS'ler, güvenlik satıcıları, finansal kurumlar ve kolluk kuvvetleri bu işe dahil edilir.

### <a name="if-youre-on-a-suspicious-website"></a>Şüpheli bir web sitesindeyseniz

- **Microsoft Edge**: Şüpheli bir sitedeyken **Diğer (...) simgesini** >  **Yardım ve geri bildirimGüvensiz** >  **siteyi bildir'i** seçin. Web sitesini bildirmek için görüntülenen web sayfasındaki yönergeleri izleyin.

- **Internet Explorer**: Şüpheli bir sitedeyken dişli simgesini seçin, **Güvenlik'in** üzerine gelin ve **ardından Güvenli Olmayan Web Sitesini Bildir'i** seçin. Web sitesini bildirmek için görüntülenen web sayfasındaki yönergeleri izleyin.

## <a name="more-information-about-phishing-attacks"></a>Kimlik avı saldırıları hakkında daha fazla bilgi

- [Kendinizi kimlik avından koruma](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Kimlik avı eğilimleri](phishing-trends.md)
