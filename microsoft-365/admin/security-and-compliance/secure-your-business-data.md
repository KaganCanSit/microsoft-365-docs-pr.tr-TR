---
title: İş planları için Microsoft 365 güvenliğini sağlamanın en iyi 10 yolu
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkDEFENDER
- adminvideo
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: İş e-postanızı ve verilerinizi fidye yazılımı, kimlik avı ve kötü amaçlı ekler gibi siber tehditlere karşı koruyun.
ms.openlocfilehash: 0e09b245d084b946596c61f9e760b56baed6043d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935927"
---
# <a name="top-10-ways-to-secure-microsoft-365-for-business-plans"></a>İş planları için Microsoft 365 güvenliğini sağlamanın en iyi 10 yolu

Microsoft'un iş planlarından birini kullanan küçük veya orta ölçekli bir kuruluşsanız, kuruluşunuzun güvenliğini artırmak için bu makaledeki kılavuzu kullanabilirsiniz. Bu kılavuz, kuruluşunuzun Harvard Kennedy School [Cybersecurity Campaign Handbook'ta](https://go.microsoft.com/fwlink/p/?linkid=2015598) açıklanan hedeflere ulaşmasına yardımcı olur.

> [!TIP]
> Bu makaledeki adımlarla ilgili yardıma ihtiyacınız varsa [bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="watch-overview-of-security"></a>İzleme: Güvenliğe genel bakış

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mzxI?autoplay=false]

Microsoft 365 İş Ekstra, şirketinizi çevrimiçi tehditlere ve yetkisiz erişime karşı korumanıza, ayrıca telefon, tablet ve bilgisayarlarınızda şirket verilerini korumanıza ve yönetmenize yardımcı olmak için tehdit koruması, veri koruma ve cihaz yönetimi özellikleri sağlar.

## <a name="security-tasks-to-complete"></a>Tamamlayacak güvenlik görevleri

Microsoft, hizmet planınız için geçerli olan aşağıdaki tabloda listelenen görevleri tamamlamanızı önerir.

|*Sayı*|Görev|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|---|
| 1 | [Kaybolan veya çalınan parolalara karşı koruma](#1-set-up-multi-factor-authentication) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 2 | [Kullanıcılarınızı eğitme](#2-train-your-users) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 3 | [Ayrılmış yönetici hesaplarını kullanma](#3-use-dedicated-admin-accounts)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | 
| 4 | [Kötü amaçlı yazılımlara karşı koruma](#4-protect-against-malware) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta için koruma) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta ve cihazlar için artırılmış koruma) |
| 5 | [Fidye yazılımlarından koruma](#5-protect-against-ransomware) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta ve bulut depolama için koruma) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(cihazlar, e-posta ve bulut depolama için artırılmış koruma) |
| 6 | [E-posta için otomatik iletmeyi durdurma](#6-stop-auto-forwarding-for-email) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 7 | [İleti şifrelemeyi kullanma](#7-use-microsoft-purview-message-encryption) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 8 | [E-postanızı kimlik avı saldırılarına karşı koruma](#8-protect-your-email-from-phishing-attacks) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(antiphishing protection) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(gelişmiş antiphishing koruması) |
| 9 | [E-posta ve Office dosyalarındaki kötü amaçlı eklere, dosyalara ve URL'lere karşı koruma](#9-protect-against-malicious-attachments-files-and-urls) | | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Kasa Bağlantılar ve Kasa Ekleri) |
| 10 | [Kuruluşunuzun cihazları için korumayı artırma](#10-increase-protection-for-your-organizations-devices) | | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(kurumsal sınıf cihaz koruması) |

Microsoft Business Premium'niz varsa, güvenliği ayarlamanın ve güvenli bir şekilde işbirliği yapmaya başlamanın en hızlı yolu şu kitaplıktaki yönergeleri izlemektir: [Microsoft 365 İş Ekstra](../../business-premium/index.md). Bu kılavuz, tüm küçük işletme müşterilerini gelişmiş bilgisayar korsanları tarafından başlatılan siber tehditlere karşı korumak için Microsoft Savunma Demokrasisi ekibiyle ortaklaşa geliştirilmiştir.

Başlamadan önce Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında Microsoft 365</a> [Güvenli Puanınızı](../../security/defender/microsoft-secure-score.md) denetleyin. Merkezi bir panodan Microsoft 365 kimlikleriniz, verileriniz, uygulamalarınız, cihazlarınız ve altyapınızın güvenliğini izleyebilir ve geliştirebilirsiniz. Önerilen güvenlik özelliklerini yapılandırma, güvenlikle ilgili görevleri gerçekleştirme (raporları görüntüleme gibi) veya üçüncü taraf bir uygulama veya yazılımla önerileri ele almak için size puan verilir. Daha geniş bir Microsoft ürün ve hizmetleri kümesine yönelik içgörüler ve daha fazla görünürlük sayesinde kuruluşunuzun güvenlik durumuyla ilgili raporlama konusunda kendinizi güvende hissedebilirsiniz.

![Microsoft Güvenli Puanı'nın ekran görüntüsü.](../../media/secure-score.png)

## <a name="1-set-up-multi-factor-authentication"></a>1: Çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması (MFA) kullanarak kaybolan veya çalınan parolalara karşı koruma sağlayın. Çok faktörlü kimlik doğrulaması ayarlandığında, kişilerin Microsoft 365 oturum açmak için telefonlarında bir kod kullanmaları gerekir. Bu ek adım, korsanların parolanızı biliyorsa devralmalarını engelleyebilir. 

Çok faktörlü kimlik doğrulaması, 2 aşamalı doğrulama olarak da adlandırılır. Kişiler çoğu 2 aşamalı doğrulamayı, örneğin Google veya Microsoft hesaplarına kolayca ekleyebilir. [Kişisel Microsoft hesabınıza iki aşamalı doğrulamayı şu şekilde ekleyebilirsiniz](https://go.microsoft.com/fwlink/p/?linkid=2016403).

Microsoft 365 kullanan işletmeler için, kullanıcılarınızın çok faktörlü kimlik doğrulaması kullanarak oturum açmasını gerektiren bir ayar ekleyin. Bu değişikliği yaptığınızda, kullanıcılardan bir sonraki oturum açışında telefonlarını iki öğeli kimlik doğrulaması için ayarlamaları istenir.
MFA'yı ayarlama ve kullanıcıların kurulumu nasıl tamamlayacağına ilişkin bir eğitim videosu görmek için bkz. [MFA'yı](set-up-multi-factor-authentication.md) ve [kullanıcı kurulumunu](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) ayarlama.

### <a name="to-set-up-multi-factor-authentication-you-turn-on-security-defaults"></a>Çok faktörlü kimlik doğrulamasını ayarlamak için güvenlik varsayılanlarını açarsınız

Çoğu kuruluş için güvenlik varsayılanları iyi bir ek oturum açma güvenliği düzeyi sunar. Daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz yeniyse güvenlik varsayılanları sizin için zaten otomatik olarak açılmış olabilir.

Azure portal Azure Active Directory (Azure AD) için **Özellikler** bölmesinden güvenlik varsayılanlarını etkinleştirir veya devre dışı bırakırsınız.

1. Genel yönetici kimlik bilgileriyle [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Sol gezinti bölmesinde **Tümünü Göster'i** seçin ve **Yönetim merkezleri'nin** altında **Azure Active Directory'ı** seçin.

3. **Azure Active Directory yönetim merkezinde** **Azure Active Directory** >  **Özellikler'i** seçin.

4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.

5. Güvenlik varsayılanlarını etkinleştirmek için **Evet'i** veya güvenlik varsayılanlarını devre dışı bırakmak için **Hayır'ı** ve ardından **Kaydet'i** seçin.

Kuruluşunuz için çok faktörlü kimlik doğrulamasını ayarladıktan sonra, kullanıcılarınızın kendi cihazlarında iki aşamalı doğrulamayı ayarlaması gerekir. Daha fazla bilgi için bkz. [Microsoft 365 için 2 aşamalı doğrulamayı ayarlama](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

> [!TIP]
> Diğer ayrıntılar ve öneriler için bkz. [Kullanıcılar için çok faktörlü kimlik doğrulamasını ayarlama](set-up-multi-factor-authentication.md).

## <a name="2-train-your-users"></a>2: Kullanıcılarınızı eğitin

Harvard Kennedy School [Siber Güvenlik Kampanyası El Kitabı](https://go.microsoft.com/fwlink/p/?linkid=2015598) , kullanıcıları kimlik avı saldırılarını belirlemeye yönelik eğitim de dahil olmak üzere kuruluşunuzda güçlü bir güvenlik farkındalığı kültürü oluşturma konusunda mükemmel rehberlik sağlar.

Ayrıca Microsoft, kullanıcılarınızın bu makalede açıklanan eylemleri gerçekleştirmelerini önerir: [Hesabınızı ve cihazlarınızı korsanlara ve kötü amaçlı yazılımlara karşı koruma](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Bu eylemler şunlardır:

- Güçlü parolalar kullanma

- Cihazları koruma

- Windows 10 ve Mac bilgisayarlarda güvenlik özelliklerini etkinleştirme

Microsoft, kullanıcıların aşağıdaki makalelerde önerilen eylemleri gerçekleştirerek kişisel e-posta hesaplarını korumalarını da önerir:

- [Outlook.com e-posta hesabınızın korunmasına yardımcı olun](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Gmail hesabınızı 2 aşamalı doğrulama ile koruma](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="3-use-dedicated-admin-accounts"></a>3: Ayrılmış yönetici hesaplarını kullanma

Microsoft 365 ortamınızı yönetmek için kullandığınız yönetim hesapları yükseltilmiş ayrıcalıklar içerir. Bunlar bilgisayar korsanları ve siber saldırganlar için değerli hedeflerdir. Yalnızca yönetim için yönetici hesaplarını kullanın. Yöneticilerin düzenli ve yönetici olmayan kullanım için ayrı bir kullanıcı hesabı olmalıdır ve yalnızca iş işleviyle ilişkili bir görevi tamamlamak için gerektiğinde yönetim hesaplarını kullanmalıdır. Ek öneriler:

- Yönetici hesaplarının çok faktörlü kimlik doğrulaması için de ayarlandığından emin olun.

- Yönetici hesaplarını kullanmadan önce, kişisel e-posta hesapları da dahil olmak üzere tüm ilgisiz tarayıcı oturumlarını ve uygulamalarını kapatın.

- Yönetici görevlerini tamamladıktan sonra tarayıcı oturumunda oturumunuzu kapatmış olmanız gerekir.

## <a name="4-protect-against-malware"></a>4: Kötü amaçlı yazılımlara karşı koruma

Microsoft 365 ortamınız kötü amaçlı yazılımlara karşı koruma içerir. Kötü amaçlı yazılım korumanızı şu şekilde artırabilirsiniz:

- Belirli dosya türlerine sahip ekleri engelleme
- Cihazlarınızda virüsten koruma/kötü amaçlı yazılımdan koruma kullanma

### <a name="block-attachments-with-certain-file-types"></a>Belirli dosya türlerine sahip ekleri engelleme

Kötü amaçlı yazılım için yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek kötü amaçlı yazılım korumanızı artırabilirsiniz. E-postada kötü amaçlı yazılım korumasına engel olmak için [kısa bir eğitim videosu](increase-threat-protection.md#raise-the-level-of-protection-against-malware-in-mail) görüntüleyin veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a>, **İlkeler** bölümünde **e-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** \> **Kötü amaçlı yazılımdan koruma** bölümüne gidin.

2. **Kötü amaçlı yazılımdan koruma** sayfasında **Varsayılan (Varsayılan)** seçeneğine çift tıklayın. Açılır öğe görüntülenir. 

3. Açılır pencerenin alt kısmındaki **Koruma ayarlarını düzenle'yi** seçin. 

4. Sonraki sayfada, **Koruma ayarları'nın** altında **Ortak ekler filtresini etkinleştir'in** yanındaki onay kutusunu seçin. Engellenen dosya türleri bu seçeneğin hemen altında listelenir. Dosya türleri eklemek veya silmek için listenin sonundaki **Dosya türlerini özelleştir'i** seçin. 

5. **Kaydet**'i seçin. 

Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma](../../security/office-365-security/anti-malware-protection.md).

### <a name="use-antivirus-and-antimalware-protection"></a>Virüsten koruma ve kötü amaçlı yazılımdan koruma kullanma

Microsoft Defender Virüsten Koruma güçlü virüsten koruma ve kötü amaçlı yazılımdan koruma sağlar ve Windows işletim sisteminde yerleşiktir.

Kuruluşunuz Microsoft 365 İş Ekstra kullanıyorsa şunları içeren ek cihaz koruması elde edersiniz:

- Yeni nesil koruma

- Güvenlik duvarı koruması

- Web içeriği filtreleme

Bu özellikler, 1 Mart 2022'de Microsoft 365 İş Ekstra müşterilerine sunulmaya başlanacak bir teklif olan İş için Microsoft Defender'ye dahildir. 

[İş için Microsoft Defender hakkında daha fazla bilgi edinin](../../security/defender-business/mdb-overview.md).

## <a name="5-protect-against-ransomware"></a>5: Fidye yazılımlarından koruma

Fidye yazılımı, dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilere erişimi kısıtlar. Daha sonra verilere erişim karşılığında genellikle Bitcoin gibi kripto para birimleri biçiminde "fidye" isteyerek kurbanlardan para sızdırmaya çalışır.

Microsoft 365'da barındırılan e-postalar ve OneDrive'de depolanan dosyalar için fidye yazılımı koruması alırsınız. Microsoft 365 İş Ekstra varsa kuruluşunuzun cihazları için ek fidye yazılımı koruması alırsınız.

Fidye yazılımı için yaygın olarak kullanılan dosya uzantılarını engellemek veya bu ekleri e-postayla alan kullanıcıları uyarmak için bir veya daha fazla posta akışı kuralı oluşturarak fidye yazılımlarına karşı koruma sağlayabilirsiniz. İyi bir başlangıç noktası iki kural oluşturmaktır:

- Makro içeren Office dosya eklerini açmadan önce kullanıcıları uyarın. Fidye yazılımı makroların içine gizlenebilir, bu nedenle kullanıcıları tanımadıkları kişilerden bu dosyaları açmamaları konusunda uyaracağız.

- Fidye yazılımı veya diğer kötü amaçlı kodlar içerebilecek dosya türlerini engelleyin. Yaygın bir yürütülebilir dosya listesiyle başlayacağız (aşağıdaki tabloda listelenmiştir). Kuruluşunuz bu yürütülebilir dosya türlerinden herhangi birini kullanıyorsa ve bunların e-postayla gönderilmesini bekliyorsanız, bunları önceki kurala ekleyin (kullanıcıları uyar).

Posta taşıma kuralı oluşturmak için [kısa bir eğitim videosu](increase-threat-protection.md#protect-against-ransomware) görüntüleyin veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. **Posta akışı** kategorisinde **kurallar'ı** seçin.

3. öğesini ve ardından **Yeni kural oluştur'u** seçin **+**.

4. Tüm seçenekler kümesini görmek için iletişim kutusunun alt kısmındaki *** öğesini seçin.

5. Her kural için aşağıdaki tabloda yer alan ayarları uygulayın. Değiştirmek istemediğiniz sürece ayarların geri kalanını varsayılanda bırakın.

6. **Kaydet**'i seçin.
    
| Ayar | Office dosyalarının eklerini açmadan önce kullanıcıları uyarma | Fidye yazılımı veya diğer kötü amaçlı kod içerebilecek dosya türlerini engelleme |
|:-----|:-----|:-----|
|Name  <br/> |Fidye yazılımı önleme kuralı: kullanıcıları uyarma  <br/> |Fidye yazılımı önleme kuralı: dosya türlerini engelleme  <br/> |
|ise bu kuralı uygulayın. . .  <br/> |Herhangi bir ek . . . dosya uzantısı ile eşleşir. . .  <br/> |Herhangi bir ek . . . dosya uzantısı ile eşleşir. . .  <br/> |
|Sözcükleri veya tümcecikleri belirtme  <br/> |Şu dosya türlerini ekleyin:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Şu dosya türlerini ekleyin:  <br/> ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, wsh, exe, pif  <br/> |
|Aşağıdakini yapın. . .  <br/> |Bir uyarıyı önceden ekleme  <br/> |iletisini engelleyin. . . iletiyi reddetme ve açıklama ekleme  <br/> |
|İleti metni sağlama  <br/> |Dosyalar kötü amaçlı kod içerebileceğinden ve göndereni tanımak bir güvenlik garantisi olmadığından, bu tür dosyaları beklemediğiniz sürece açmayın.  <br/> ||
   
> [!TIP]
> Engellemek istediğiniz dosyaları [4. Adım: Kötü](#4-protect-against-malware) amaçlı yazılımlara karşı koruma bölümünden kötü amaçlı yazılımdan koruma listesine de ekleyebilirsiniz.

Daha fazla bilgi için bkz.:

- [Fidye yazılımı: riski azaltma](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Office 365](../../security/defender-endpoint/office-365-microsoft-defender-antivirus.md)

- [OneDrive geri yükleme](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="6-stop-auto-forwarding-for-email"></a>6: E-posta için otomatik iletmeyi durdurma

Bir kullanıcının posta kutusuna erişim elde eden bilgisayar korsanları, posta kutusunu e-postayı otomatik olarak iletecek şekilde yapılandırarak postayı yok edebilir. Bu sorun, kullanıcının farkındalığı olmadan bile oluşabilir. Bir posta akışı kuralı yapılandırarak bunun olmasını önleyebilirsiniz.

Posta taşıma kuralı oluşturmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. **Posta akışı** kategorisinde **kurallar'ı** seçin.

3. öğesini ve ardından **Yeni kural oluştur'u** seçin **+**.

4. Tüm **seçenekler** kümesini görmek için iletişim kutusunun alt kısmındaki Diğer seçenekler'i seçin.

5. Aşağıdaki tabloda yer alan ayarları uygulayın. Bunları değiştirmek istemiyorsanız ayarların geri kalanını varsayılanda bırakın.

6. **Kaydet**'i seçin.

|Ayar|Dış etki alanlarına e-postaları Otomatik İlet'i reddet|
|---|---|
|Name|E-postanın dış etki alanlarına otomatik iletmesini engelleme|
|Eğer bu kuralı uygula ...|Gönderen. . . dış/iç şeklindedir. . . Kuruluşun içinde|
|Koşul ekle|Alıcı. . . dış/iç şeklindedir. . . Kuruluş dışında|
|Koşul ekle|İleti özellikleri. . . ileti türünü ekleyin. . . Otomatik iletme|
|Aşağıdakini yapın...|iletisini engelleyin. . . iletisini reddedin ve bir açıklama ekleyin.|
|İleti metni sağlama|E-postanın bu kuruluş dışında otomatik olarak iletilmesi güvenlik nedeniyle engellenir.|

## <a name="7-use-microsoft-purview-message-encryption"></a>7: Microsoft Purview İleti Şifrelemesi'ni kullanma

Microsoft Purview İleti Şifrelemesi Microsoft 365 dahildir. Zaten ayarlandı. Microsoft Purview İleti Şifrelemesi ile kuruluşunuz, kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri gönderebilir ve alabilir. Microsoft Purview İleti Şifrelemesi Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyebilmesine yardımcı olur.

Microsoft Purview İleti Şifrelemesi, posta gönderirken iki koruma seçeneği sağlar:

- İletme

- Şifrelemek

Kuruluşunuz e-postaya etiket uygulayan gizli gibi diğer seçenekleri yapılandırmış olabilir.

### <a name="to-send-protected-email"></a>Korumalı e-posta göndermek için

Bilgisayar için Outlook'nde e-postadaki **Seçenekler'i** ve ardından **İzinler'i** seçin.

![Outlook'de e-posta iletisi şifrelemesi.](../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639a.png)

Outlook.com'da e-postada **Koru'yu** seçin. Varsayılan koruma **İletme'dir**. Bunu şifrelemek üzere değiştirmek için **İzinleri** \> **Değiştir Şifreleme'yi** seçin.

![Outlook.com'da e-posta iletisi şifrelemesi.](../../media/329ccf50-f6b1-4fb8-b249-60b907a82b7e.png)

### <a name="to-receive-encrypted-email"></a>Şifrelenmiş e-posta almak için

Alıcının Outlook 2013 veya Outlook 2016 ve bir Microsoft e-posta hesabı varsa, Okuma bölmesinde öğenin kısıtlı izinleri hakkında bir uyarı görür. İletiyi açtıktan sonra, alıcı iletiyi diğer tüm iletilerde olduğu gibi görüntüleyebilir.

Alıcı Gmail veya Yahoo gibi başka bir e-posta istemcisi veya e-posta hesabı kullanıyorsa, e-posta iletisini okumak için oturum açmasına veya iletiyi web tarayıcısında görüntülemek için tek seferlik geçiş kodu istemesine olanak tanıyan bir bağlantı görür. Kullanıcılar e-postayı almıyorsa İstenmeyen posta veya Gereksiz klasörlerini denetlemelerini isteyin.

> [!TIP]
> Daha fazla bilgi için bkz. [Bilgisayar için Outlook şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="8-protect-your-email-from-phishing-attacks"></a>8. E-postanızı kimlik avı saldırılarına karşı koruma

Microsoft 365 ortamınız için bir veya daha fazla özel etki alanı yapılandırdıysanız, hedeflenen kimlik avı koruması yapılandırabilirsiniz. Office 365 için Microsoft Defender bir parçası olan kimlik avı koruması, kuruluşunuzun kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarına ve diğer kimlik avı saldırılarına karşı korunmasına yardımcı olabilir. Özel bir etki alanı yapılandırmadıysanız, bunu yapmanız gerekmez.

En önemli kullanıcılarınızı ve özel etki alanınızı korumak için bir ilke oluşturarak bu korumayı kullanmaya başlamanızı öneririz.

Office 365 için Defender'da kimlik avı önleme ilkesi oluşturmak için [kısa bir eğitim videosu](increase-threat-protection.md#protect-your-email-from-phishing-attacks) görüntüleyin veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin.

2. **İlkeler bölümünde e-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin.

3. Kimlik avı önleme sayfasında **+ Oluştur'u** seçin. Kimlik avı önleme ilkenizi tanımlama işleminde size yol gösteren bir sihirbaz başlatılır.

4. Aşağıdaki grafikte önerilen ilkenizin adını, açıklamasını ve ayarlarını belirtin. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender seçeneklerinde kimlik avı önleme ilkesi hakkında bilgi edinin](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Ayarlarınızı gözden geçirdikten sonra **, Bu ilkeyi oluştur'u** veya **Uygun şekilde Kaydet'i** seçin.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Etki alanı ve en değerli kampanya personeli|
|Açıklama|En önemli personelin ve etki alanımızın kimliğine bürünülmediğinden emin olun.|
|Korunacak kullanıcıları ekleme|**+ Koşul ekle'yi seçin, Alıcıdır**. Kullanıcı adlarını yazın veya adayın, kampanya yöneticisinin ve diğer önemli personel üyelerinin e-posta adresini girin. Kimliğe bürünmeye karşı korumak istediğiniz en fazla 20 iç ve dış adres ekleyebilirsiniz.|
|Korunacak etki alanları ekleme|**+ Koşul ekle'yi seçin, Alıcı etki alanı.** Tanımladıysanız Microsoft 365 aboneliğinizle ilişkilendirilmiş özel etki alanını girin. Birden fazla etki alanı girebilirsiniz.|
|Eylemleri seçme|E-posta kimliğine bürünülen bir kullanıcı tarafından gönderiliyorsa: **İletiyi başka bir e-posta adresine yeniden yönlendir'i** seçin ve güvenlik yöneticisinin e-posta adresini yazın; örneğin, securityadmin@contoso.com. <br/> E-posta kimliğine bürünülen bir etki alanı tarafından gönderiliyorsa, **İletiyi karantinaya al'ı** seçin.|
|Posta kutusu zekası|Varsayılan olarak, yeni bir kimlik avı önleme ilkesi oluşturduğunuzda posta kutusu zekası seçilir. En iyi sonuçlar için bu ayarı **Açık** bırakın.|
|Güvenilir gönderenler ve etki alanları ekleme|Bu örnekte hiçbir geçersiz kılma tanımlamayın.|
|Uygulandığı yer|**Alıcı etki alanı'nı** seçin. **Bunlardan herhangi biri'nin** altında **Seç'i** seçin. **+ Ekle'yi** seçin. Etki alanı adının yanındaki onay kutusunu seçin(örneğin, listede contoso.com) ve ardından **Ekle'yi** seçin. **Bitti'yi** seçin.|

> [!TIP]
> Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini ayarlama](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="9-protect-against-malicious-attachments-files-and-urls"></a>9: Kötü amaçlı eklere, dosyalara ve URL'lere karşı koruma

Kişiler belgeler, sunular, elektronik tablolar ve daha fazlası gibi ekleri düzenli olarak gönderir, alır ve paylaşır. Yalnızca e-posta iletisine bakarak bir ekin güvenli mi yoksa kötü amaçlı mı olduğunu söylemek her zaman kolay değildir. Office 365 için Microsoft Defender Kasa Ek koruması içerir, ancak bu koruma varsayılan olarak açık değildir. Bu korumayı kullanmaya başlamak için yeni bir kural oluşturmanızı öneririz. Bu koruma SharePoint, OneDrive ve Microsoft Teams dosyalarına genişletir.

### <a name="set-up-safe-attachments"></a>Kasa Eklerini Ayarlama

Kasa Ekler ilkesi oluşturmak için [kısa bir eğitim videosu](increase-threat-protection.md) görüntüleyin veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve yönetici hesabınızla oturum açın.

2. **İlkeler** bölümünde **e-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **Kötü amaçlı yazılımdan koruma** bölümüne gidin.

3. Yeni bir ilke oluşturmak için **+ Oluştur'u** seçin.

4. Aşağıdaki tabloda yer alan ayarları uygulayın.

5. Ayarlarınızı gözden geçirdikten sonra **, Bu ilkeyi oluştur'u** veya **Uygun şekilde Kaydet'i** seçin.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Algılanan kötü amaçlı yazılımlarla geçerli ve gelecekteki e-postaları engelleyin.|
|Açıklama|Algılanan kötü amaçlı yazılımlarla geçerli ve gelecekteki e-postaları ve ekleri engelleyin.|
|Ekleri kaydetme bilinmeyen kötü amaçlı yazılım yanıtı|**Engelle - Algılanan kötü amaçlı yazılım içeren geçerli ve gelecekteki e-postaları ve ekleri engelle'yi** seçin.|
|Algılamada eki yeniden yönlendirme|Yeniden yönlendirmeyi etkinleştir (bu kutuyu seçin) <br/> Karantina için yönetici hesabını veya posta kutusu kurulumunu girin. <br/> Eklerde kötü amaçlı yazılım taraması zaman aşımına uğradıysa veya hata oluşursa yukarıdaki seçimi uygulayın (bu kutuyu seçin).|
|Uygulandığı yer|Alıcı etki alanı şeklindedir. . . etki alanınızı seçin.|

> [!TIP]
> Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini ayarlama](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

### <a name="set-up-safe-links"></a>Kasa Bağlantılarını Ayarlama

Korsanlar bazen kötü amaçlı web sitelerini e-posta veya diğer dosyalardaki bağlantılarda gizler. Office 365 için Microsoft Defender parçası olan Kasa Bağlantıları, e-posta iletilerinde ve Office belgelerde web adreslerinin (URL' ler) tıklama zamanında doğrulanmasını sağlayarak kuruluşunuzun korunmasına yardımcı olabilir. Koruma, Kasa Bağlantıları ilkeleri aracılığıyla tanımlanır.

Saldırılara karşı korumak için aşağıdakileri yapın:

- Korumayı artırmak için varsayılan ilkeyi değiştirin.

- Etki alanınızdaki tüm alıcıları hedefleyen yeni bir ilke ekleyin.

Kasa Bağlantıları'na ulaşmak için [kısa bir eğitim videosu](increase-threat-protection.md#protect-against-phishing-attacks-with-safe-links) görüntüleyin veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve yönetici hesabınızla oturum açın.

2. **İlkeler** bölümünde **e-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **Kötü amaçlı yazılımdan koruma** bölümüne gidin.

3. Yeni bir ilke oluşturmak veya varsayılan ilkeyi değiştirmek için **+ Oluştur'u** seçin.

Varsayılan ilkeyi değiştirmek için:

1. **Varsayılan** ilkeye çift tıklayın. Açılır öğe görüntülenir. 

2. Açılır pencerenin alt kısmındaki **Koruma ayarlarını düzenle'yi** seçin.

3. Varsayılan ilkeyi değiştirdikten sonra **Kaydet'i** seçin.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Etki alanındaki tüm alıcılar için bağlantı ilkesi Kasa|
|İletilerde bilinmeyen kötü amaçlı olabilecek URL'ler için eylemi seçin|**Açık - URL'ler yeniden yazılır ve kullanıcı bağlantıya tıkladığında bilinen kötü amaçlı bağlantıların listesiyle karşılaştırılır**.|
|Şüpheli bağlantılar ve dosyalara işaret eden bağlantılar için gerçek zamanlı URL taraması uygulama|Bu kutuyu seçin.|
|Uygulandığı yer|Alıcı etki alanı şeklindedir. . . etki alanınızı seçin.|

> [!TIP]
> Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Kasa Bağlantılar](../../security/office-365-security/atp-safe-links.md).

## <a name="10-increase-protection-for-your-organizations-devices"></a>10: Kuruluşunuzun cihazları için korumayı artırma

Microsoft Defender Virüsten Koruma Windows işletim sisteminde yerleşiktir ve virüslere ve kötü amaçlı yazılımlara karşı iyi koruma sağlar. Ancak, kuruluşunuzun cihazları için korumayı, sizinki gibi küçük ve orta ölçekli işletmeler için yeni bir teklif olan İş için Microsoft Defender'a ekleyerek artırabilirsiniz. İş için Defender ile kuruluşunuzun cihazları fidye yazılımlarına, kötü amaçlı yazılımlara, kimlik avına ve diğer tehditlere karşı daha iyi korunur.

**1 Mart 2022'de [Microsoft 365 İş Ekstra](../../security/defender-business/index.yml) İş için Microsoft Defender özellikleri ekleniyor**. 


Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [İş için Microsoft Defender'a Genel Bakış](../../security/defender-business/mdb-overview.md)

- [İş için Microsoft Defender ayarlama ve yapılandırma](../../security/defender-business/mdb-setup-configuration.md)

- [Microsoft 365 Defender portalını kullanarak Kullanmaya başlayın](../../security/defender-business/mdb-get-started.md)

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 için çok faktörlü kimlik doğrulaması](multi-factor-authentication-microsoft-365.md) (makale)\
[Öncelik hesaplarını yönetme ve izleme](../setup/priority-accounts.md) (makale)\
[Yönetim merkezinde Microsoft 365 Raporları](../activity-reports/activity-reports.md) (video)