---
title: Kimlik avı saldırılarına karşı koruma
ms.reviewer: ''
description: Kimlik avının nasıl iş yaptığını, cihazlarınızı kötü amaçlı yazılım teslim etmeyi ve kendinizi korumak için neler yapnizi öğrenin
keywords: güvenlik, kötü amaçlı yazılım, kimlik avı, bilgi, dolandırıcılık, sosyal mühendislik, açık, açık, koruma, eğilimler, hedefli saldırı
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
ms.openlocfilehash: 39b998b69b62a8c927ff26c1325d8a88812e0be6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706042"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Kimlik avı saldırılarına karşı koruma

Kimlik avı saldırıları e-postalar, web siteleri, kısa mesajlar veya diğer elektronik iletişim formları aracılığıyla hassas bilgileri çalmaya yöneliktir. Yasal şirketlerden veya kişilerden gelen resmi iletişim gibi görünüyor.

Siber suçlular çoğunlukla kullanıcı adlarını, parolaları, kredi kartı ayrıntılarını, banka hesap bilgilerini veya diğer kimlik bilgilerini çalmaya girişer. Çalınan bilgileri bilgisayar korsanları, kimlik hırsızlığı veya doğrudan banka hesaplarından ve kredi kartlarından para çalma gibi kötü niyetli amaçlar için kullanırlar. Bu bilgiler siber suç pazarlarında da satılmalarını sağlar.

Sosyal mühendislik saldırıları, bir kullanıcının karar almada olası atlamalarından yararlanmak için tasarlanmıştır. Dikkat edin ve hassas veya kişisel bilgileri e-posta ya da bilinmeyen web siteleri aracılığıyla ya da telefon üzerinden asla sağlamayın. Unutmayın, kimlik avı e-postaları yasal olarak görünecek şekilde tasarlanmıştır.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Kimlik avı dolandırıcılığı işaretlerini öğrenme

En iyi koruma, farkındalık ve eğitimdir. E-postalar tanınan bir kaynaktan gelmiş olsa bile, talep edilmemiş e-postalarda ekleri veya bağlantıları açmayın. E-posta beklenmeyen bir durumsa, eki açma konusunda emin olun ve URL'yi doğrulayın.

Kuruluşlar, çalışanlarını kişisel veya finansal bilgiler talep eden her türlü iletişim konusunda eğit olmalı ve bu iletişimlerden konusunda eğitin. Ayrıca çalışanlara, tehditle ilgili olarak şirketin güvenlik işlemleri ekibine hemen rapor etmelerini bildirmeleri gerekir.

Burada, kimlik avı dolandırıcılığıyla ilgili çeşitli belirtim işaretleri veserleri ve sonra da şunları söyler:

* E-postalarda sağlanan bağlantılar veya URL'ler doğru konuma işaret çalışmıyor veya e-postanın göndereni ile bağlantılı olmayan bir üçüncü taraf sitesini işaret ediyor. Örneğin, sağlanan URL'nin altındaki resimde bu URL'ye değil, size verilen URL'ye uygun değil.

    ![bir url'nin üzerine gelme örneği.](../../media/security-intelligence-images/url-hover.png)

* Sosyal güvenlik numaraları **, banka ya da** finansal bilgiler gibi kişisel bilgiler için istekte bulunduruz. Resmi iletişimler genellikle e-posta şeklinde kişisel bilgilerinizi talep etmeyebilirsiniz.

* **E-posta adresin öğeleri, geçerli** bir e-posta adresine benser, ancak sayı eklenecek veya harfleri değiştirecek şekilde değiştirilir.

* İleti beklenmeyen **ve talep edilmemiştir**. Birden birden bire bir varlıktan veya nadiren uğraşmak zorunda olduğunuz bir kişiden e-posta alırsanız, bu e-posta şüphelisi olarak düşünün.

* İletide veya ekte makroları **etkinleştirmeniz, güvenlik ayarlarını ayarlamanız veya uygulamaları yüklemeniz sormektedir**. Normal e-postalar bunu sizden istemez.

* İletide hatalar **var**. Geçerli şirket iletilerinin tipografik veya dil bilgisi hataları ya da yanlış bilgi içerme olasılığı daha düşük olur.

* Gönderen **adresi, iletinin kendi imzasıyla** eşleşmez. Örneğin, e-postanın Mary of Contoso Corp'dan olduğu doğrulansa ancak gönderen adresi ali<span></span>@example.com.

* " **Ta" alanında** birden çok alıcı var ve bunlar rastgele adresler gibi görünüyor. Şirket iletileri genellikle tek tek alıcılara doğrudan gönderilir.

* İletinin kendi karşılama mesajı **kişisel olarak size hitap etmemektedir**. Başka bir kişiyi yanlışlıkla adres alan iletiler dışında, adını yanlış kullanılan veya doğrudan e-posta adresinizden adınız geçen karşılamalar kötü amaçlı olabilir.

* Web sitesi tanıdıktır ama **tutarsızlıklar veya doğru olmayan şeyler vardır**. Uyarı işaretleri, geçerli oturum açma web siteleri tarafından sorul olmayan ek bilgiler vermelerini istemek veya kullanıcılardan dışarı çıkma logolarını, yazım hatalarını içerir.

* Açılan sayfa canlı **bir sayfa değil**, daha çok alışık olduğunuz site gibi olacak şekilde tasarlanmış bir resimdir. Kimlik bilgilerini istekte olan bir açılır pencere görünebilir.

Şüpheniz varsa, şüpheli e-postaların aslında yasal olduğunu doğrulamak için bilinen kanalları kullanarak işletmeyle iletişime geçin.

## <a name="software-solutions-for-organizations"></a>Kuruluşlar için yazılım çözümleri

* [Microsoft Edge](/microsoft-edge/deploy/index) ve [Windows Defender Application Guard, Microsoft'un](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) endüstri lideri Hyper-V sanallaştırma teknolojisini kullanarak giderek artan hedefli saldırılara karşı koruma sağlar. Göz atan bir web sitesi güvenilmeyen olarak kabul edildiyse, Hyper-V kapsayıcısı bu cihazı ağın geri kalanından ayırarak kurumsal verilerinize erişimi önler.

* [Microsoft Exchange Online Koruması (EOP),](https://products.office.com/exchange/exchange-email-security-spam-protection) acil durumlarda ve sonrasında e-postaya erişimi koruyarak kurumsal sınıf güvenilirlik ve kötü amaçlı yazılımlara karşı koruma sağlar.  Çeşitli filtre katmanları kullanarak EOP, toplu posta denetimleri ve uluslararası istenmeyen posta gibi istenmeyen posta filtrelemesi için koruma hizmetlerinizi daha da geliştirecek farklı denetimler sağlar.

* [E-postanızı, dosyalarınızı ve çevrimiçi Office 365](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) kötü amaçlı yazılımlara karşı korumaya yardımcı olmak üzere güvenlik bilgileri için Microsoft Defender'ı kullanın. Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online ve OneDrive İş'te holist koruma sağlar. Güvenli olmayan eklere karşı koruma ve kötü amaçlı bağlantılara karşı korumayı genişleterek, sıfır gün içinde daha iyi bir koruma sağlamak için Exchange Online Protection özelliklerinin tamamlanır.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Kimlik avı dolandırıcılığıyla mücadeleye yeni başladıysanız ne yapmak zorunda olursanız

Kimlik avı saldırılarının bir saldırı sonucu olduğunu hissedersanız:

1. İş bilgisayarda çalışıyorsanız, IT yöneticinize ulaşın
2. Hesaplarla ilişkilendirilmiş tüm parolaları hemen değiştirme
3. Herhangi bir dolandırıcılık etkinliğini bankanıza ve kredi kartı şirketine bildirme

### <a name="reporting-spam"></a>İstenmeyen posta bildirme

- **Outlook.com**: Kişisel bilgiler isteyen şüpheli bir e-posta iletisi alırsanız gelen kutunuzda yer alan iletinin yanındaki Outlook seçin. Gereksiz'in yanındaki oku **ve ardından** Kimlik **Avı'ı seçin**.

- **Microsoft Office Outlook**: Şüpheli iletideyken şeritten İletiyi **bildir'i** ve sonra Kimlik **Avı'ı seçin**.

- **Microsoft 365**: Gereksiz veya kimlik avı örneğini [çözümleme için Microsoft 365 Defender'e](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft) göndermek üzere Gönderimler portalını kullanın. Daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Kimlik Avı Önleme Çalışma Grubu: kimlik** phishing-report@us-cert.gov. Grup, kimlik avı dolandırıcılığı dolandırıcılığı ve korsanlarla mücadele etmek için gönderilen e-postalardan oluşturulan raporları kullanır. ISS'ler, güvenlik satıcıları, mali kurumlar ve hukuk yaptırım kuruluşları bu işe dahil olur.

### <a name="if-youre-on-a-suspicious-website"></a>Şüpheli bir web sitesindeysiniz

- **Microsoft Edge**: Şüpheli bir sitedeyken, Diğer **(...)** >  simgesini **SeçinHelp ve geri** >  **bildirimEr güvenli olmayan siteyi bildirin**. Web sitesini bildirmeyi gösteren web sayfasındaki yönergeleri izleyin.

- **Internet Explorer**: Şüpheli bir sitedeyken dişli simgesini seçin, Güvenlik'in üzerine gelin ve ardından Güvenli Olmayan Web Sitesini **Bildir'i seçin**. Web sitesini bildirmeyi gösteren web sayfasındaki yönergeleri izleyin.

## <a name="more-information-about-phishing-attacks"></a>Kimlik avı saldırıları hakkında daha fazla bilgi

- [Kendinizi kimlik avına karşı koruma](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Kimlik avı eğilimleri](phishing-trends.md)
