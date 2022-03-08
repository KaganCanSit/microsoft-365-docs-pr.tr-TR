---
title: kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu
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
description: İş e-postanızı ve fidye yazılımları, kimlik avı ve kötü amaçlı ekler de dahil olmak üzere siber tehditlere karşı koruyun.
ms.openlocfilehash: 2e72ca635269000fe97a555390e7c65d39d2377e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325705"
---
# <a name="top-10-ways-to-secure-microsoft-365-for-business-plans"></a>kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu

Microsoft'un iş planlarından birini kullanan küçük veya orta ölçekli bir kuruluşsanız, bu makaledeki kılavuzu kullanarak kurumnizin güvenliğini artırabilirsiniz. Bu kılavuz, kuruluşlarının Harvard School [Cybersecurity Campaign El Kitabı'nde açıklanan hedeflere ulaşmalarını sağlar](https://go.microsoft.com/fwlink/p/?linkid=2015598).

> [!TIP]
> Bu makaledeki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="watch-overview-of-security"></a>İzle: Güvenlikle ilgili genel bakış

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mzxI?autoplay=false]

Microsoft 365 İş Ekstra, şirketinizi çevrimiçi tehditlere ve yetkisiz erişime karşı korumanın yanı sıra telefon, tablet ve bilgisayarlarda şirket verilerini korumanıza ve yönetmenize yardımcı olmak için tehdit koruması, veri koruması ve cihaz yönetimi özellikleri sağlar.

## <a name="security-tasks-to-complete"></a>Tamamlanması gereken güvenlik görevleri

Microsoft, aşağıdaki tabloda listelenen ve hizmet planınıza uygun olarak listelenen görevleri tamamlamanızı öneririz.

|*Sayı*|Görev|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|---|
| 1 | [Kaybolan veya çalınan parolalara karşı koruma](#1-set-up-multi-factor-authentication) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 2 | [Kullanıcılarınızı eğitin](#2-train-your-users) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 3 | [Adanmış yönetici hesaplarını kullanma](#3-use-dedicated-admin-accounts)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | 
| 4 | [Kötü amaçlı yazılıma karşı koruma](#4-protect-against-malware) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta için koruma) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta ve cihazlar için artırılmış koruma) |
| 5 | [Fidye yazılımlarına karşı koruma](#5-protect-against-ransomware) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(e-posta ve bulut depolama alanı için koruma) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(cihazlar, e-posta ve bulut depolama için artırılmış koruma) |
| 6 | [E-posta için otomatik iletmeyi durdurma](#6-stop-auto-forwarding-for-email) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 7 | [Şifreleme kullanma](#7-use-office-message-encryption) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
| 8 | [E-postanızı kimlik avı saldırılarından koruma](#8-protect-your-email-from-phishing-attacks) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(antiphishing protection) | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(gelişmiş koruma koruma) |
| 9 | [E-posta ve diğer dosyalarda kötü amaçlı eklere, dosyalara ve URL'lere Office koruma](#9-protect-against-malicious-attachments-files-and-urls) | | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Kasa ve Ekleri Kasa Ekleme) |
| 10 | [Kuruluş cihazları için korumayı artırma](#10-increase-protection-for-your-organizations-devices) | | ![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(kurumsal sınıf cihaz koruması) |

Microsoft Business hizmetine sahip Premium, güvenliği ayarlamanın ve işbirliğine güvenli bir şekilde başlamanın en hızlı yolu bu kitaplıkta yer alan yönergeleri takip etmektir: [Microsoft 365 İş Ekstra](../../business-premium/index.md). Bu kılavuz, tüm küçük işletme müşterilerini karmaşık korsanlar tarafından başlatılan siber tehditlere karşı korumak için Microsoft Savunma Savunma Ekibi ile ortaklıkta geliştirilmiştir.

Başlamadan önce, portalda Microsoft 365 [Puanınızı](../../security/defender/microsoft-secure-score.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a> Merkezi bir panodan kimlikleri, verileri, uygulamaları, cihazları ve altyapıyı Microsoft 365 için güvenliği izleyebilir ve geliştirebilirsiniz. Önerilen güvenlik özelliklerini yapılandırma, güvenlikle ilgili görevleri (raporları görüntüleme gibi) gerçekleştirme ya da üçüncü taraf bir uygulama veya yazılımla önerilere yönelik öneriler gerçekleştirmeyle ilgili puanlar verilir. Daha geniş bir Microsoft ürün ve hizmetleri kümesiyle ilgili daha geniş içgörüler ve daha görünür hale gelen bu hizmet sayesinde, organizasyonlu kuruluşun güvenlik durumu hakkında güvenli bir rapor ile görüşlerinizi bildirebilirsiniz.

![Microsoft Güvenli Puanı'nın ekran görüntüsü.](../../media/secure-score.png)

## <a name="1-set-up-multi-factor-authentication"></a>1: Çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması (MFA) kullanarak kayıp veya çalınmış parolalara karşı koruyun. Çok faktörlü kimlik doğrulaması ayar gerektiriyorsa, kişilerin telefonlarında kendi telefonlarında oturum açmaları için kod Microsoft 365. Bu ek adım, bilgisayar korsanlarının parolanızı biliyorsa bunu ele almalarını önlenebilir. 

Multifactor authentication, 2 aşamalı doğrulama olarak da adlandırılan bir işlemdir. Bireyler, Google veya Microsoft hesaplarına, örneğin hesapların çoğuna kolayca 2 aşamalı doğrulama ekleyebilir. Kişisel [Microsoft hesabınıza iki aşamalı doğrulamayı şu şekilde eklersiniz](https://go.microsoft.com/fwlink/p/?linkid=2016403).

Multifactor Authentication Microsoft 365 kullanan işletmeler için, kullanıcılarının çok faktörlü kimlik doğrulaması kullanarak oturum açmasını gerektiren bir ayar ekleyin. Bu değişikliği yapınca, bir sonraki oturum açmaları için telefonlarında iki faktörlü kimlik doğrulaması yapmaları istenir.
MFA'nın nasıl ayarlanacaklarını ve kullanıcıların kurulumu nasıl tamamlayacaklarını görmek için bkz. [MFA](set-up-multi-factor-authentication.md) ve [kullanıcı ayarlama](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

### <a name="to-set-up-multi-factor-authentication-you-turn-on-security-defaults"></a>Çok faktörlü kimlik doğrulamasını ayarlamak için, güvenlik varsayılanlarını

Çoğu kuruluş için, güvenlik varsayılanları iyi bir düzeyde ek oturum açma güvenliği sağlar. Daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz yeniyse, güvenlik varsayılanları sizin için otomatik olarak zaten açık olabilir.

Azure portalında yer alan kullanıcı (Azure AD) için Özellikler bölmesinde Azure Active Directory varsayılanları etkinleştirebilirsiniz veya devre dışı bırakabilirsiniz.

1. Genel yönetici kimlik [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açma.

2. Sol gezintide, Her Şeyi **Göster'i seçin** ve Yönetim **merkezleri'nin altında** **Geri Azure Active Directory**.

3. Azure Active Directory **merkezindeProperties'i** **Azure Active Directory** >  seçin.

4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.

5. Güvenlik **varsayılanlarını** etkinleştirmek için Evet'i veya **güvenlik varsayılanlarını** devre dışı bırakmak için Hayır'ı seçin ve sonra da Kaydet'i **seçin**.

Kuruluşunuz için çok faktörlü kimlik doğrulamasını ayarladıktan sonra, kullanıcılarınızın kendi cihazlarında iki aşamalı doğrulamayı ayarlaması gerekir. Daha fazla bilgi için bkz[. E-postanız için 2 aşamalı doğrulama Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

> [!TIP]
> Diğer ayrıntılar ve öneriler için bkz. [Kullanıcılar için çok faktörlü kimlik doğrulamasını ayarlama](set-up-multi-factor-authentication.md).

## <a name="2-train-your-users"></a>2: Kullanıcılarınızı eğitin

Harvard Harvard School [Cybersecurity Campaign El](https://go.microsoft.com/fwlink/p/?linkid=2015598) Kitabı, kullanıcıları kimlik avı saldırılarını belirlemeye yönelik eğitim de dahil olmak üzere, organizasyonu dahilinde güvenlik farkındalığı konusunda güçlü bir güvenlik kültürü kurma konusunda mükemmel rehberlik sağlar.

Buna ek olarak Microsoft, kullanıcılarınızı bu makalede açıklanan eylemleri uygulamanızı önermektedir: Hesaplarınızı ve cihazlarınızı bilgisayar korsanlarından ve kötü amaçlı [yazılımdan koruyun](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Bu eylemler şunlardır:

- Güçlü parolalar kullanma

- Cihazları koruma

- E-bilgisayarlarda ve Mac Windows 10 özellikleri etkinleştirme

Microsoft ayrıca, aşağıdaki makalelerde önerilen eylemleri gerçekleştirerek kullanıcıların kişisel e-posta hesaplarını korumalarını da önerir:

- [Outlook.com e-posta adresinizin korunmasına yardımcı olun](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [2 aşamalı doğrulama ile Gmail hesabınızla koruma](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="3-use-dedicated-admin-accounts"></a>3: Adanmış yönetici hesaplarını kullanma

Ortamınızı yönetmek için kullanabileceğiniz yönetim hesapları Microsoft 365 yükseltilmiş ayrıcalıklar içerir. Bunlar korsanlar ve siber saldırıların değerli hedefleridir. Yönetici hesaplarını yalnızca yönetim için kullanın. Yöneticilerin normal, yönetim dışı kullanım için ayrı bir kullanıcı hesabına sahip olması ve yalnızca görevleriyle ilişkilendirilmiş bir görevi tamamlamak için gerektiğinde yönetim hesaplarını kullanmaları gerekir. Ek öneriler:

- Yönetici hesaplarının çok faktörlü kimlik doğrulaması için de ayarlanmış olduğundan emin olun.

- Yönetici hesaplarını kullanmadan önce, kişisel e-posta hesapları da dahil olmak üzere tüm ilgili olmayan tarayıcı oturumlarını ve uygulamalarını kapatın.

- Yönetici görevlerini tamamladıktan sonra, tarayıcı oturumunu oturumundan çıkış yapın.

## <a name="4-protect-against-malware"></a>4: Kötü amaçlı yazılıma karşı koruma

Sizin Microsoft 365 kötü amaçlı yazılıma karşı koruma içerir. Kötü amaçlı yazılımdan korunmanızı şu şekilde artırabilirsiniz:

- Belirli dosya türlerinde ekleri engelleme
- Cihazlarınıza virüsten koruma/kötü amaçlı yazılımlardan koruma kullanma

### <a name="block-attachments-with-certain-file-types"></a>Belirli dosya türlerine sahip ekleri engelleme

Kötü amaçlı yazılımda yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek kötü amaçlı yazılımdan korunmanızı artırabilirsiniz. E-postaya kötü amaçlı yazılımdan korumayı çarpmak için [kısa bir eğitim videosu](increase-threat-protection.md#raise-the-level-of-protection-against-malware-in-mail) izleyin veya aşağıdaki adımları tamamlayın:

1.  Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında</a>, İlkeler bölümünde **E-posta &** \> işbirliği **& kuralları** \> \> İlkeler bölümünde Tehdit ilkeleri **Kötü** amaçlı yazılımdan koruma **ilkeleri'ne** gidin.

2. Kötü amaçlı **yazılımdan koruma sayfasında** Varsayılan **(Varsayılan)'a çift tıklayın**. Bir açılır çıktı görüntülenir. 

3. Çıkış **öğesinin alt** kısmında Koruma ayarlarını düzenle'yi seçin. 

4. Sonraki sayfada, Koruma **ayarları'nın altında**, Yaygın ek filtresini **etkinleştir'in yanındaki onay kutusunu seçin**. Engellenen dosya türleri bu seçeneğin hemen altında listelenir. Dosya türlerini eklemek veya silmek için, **listenin sonundaki** Dosya türlerini özelleştir'i seçin. 

5. **Kaydet**'i seçin. 

Daha fazla bilgi için bkz [. EOP'de kötü amaçlı yazılımlardan koruma](../../security/office-365-security/anti-malware-protection.md).

### <a name="use-antivirus-and-antimalware-protection"></a>Virüsten koruma ve kötü amaçlı yazılımlardan koruma kullanma

Microsoft Defender Virüsten Koruma virüsten koruma ve kötü amaçlı yazılımlardan koruma sağlar ve yazılımdan koruma Windows sistemi olarak yerleşiktir.

If your organization is using Microsoft 365 İş Ekstra, you get additional device protection that includes:

- Yeni nesil koruma

- Güvenlik duvarı koruması

- Web içeriği filtreleme

Bu özellikler, 1 Mart 2022'den itibaren müşterilere Microsoft 365 İş Ekstra üzere teklif olan Microsoft Defender for Business'da yer almaktadır. 

[İş için Microsoft Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

## <a name="5-protect-against-ransomware"></a>5: Fidye yazılımlarına karşı koruma

Fidye yazılımları, dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilere erişimi kısıtlar. Daha sonra, verilere erişim için genellikle Bitcoin gibi şifreleme şifrelemeleri biçimine sahip "bilgi" istemeleri ile onaylatan paraları ödemeye çalışır.

E-postalarda barındırılan e-postalara ve Microsoft 365 içinde depolanan dosyalara fidye yazılımı koruması OneDrive. Yazılımınız varsa Microsoft 365 İş Ekstra için ek fidye yazılımı koruması edinebilirsiniz.

Fidye yazılımlarına karşı korunmak için, fidye yazılımında yaygın olarak kullanılan dosya uzantılarını engellemek veya bu ekleri e-postayla alan kullanıcıları uyarmak için bir veya daha fazla posta akışı kuralı oluşturabilirsiniz. İyi bir başlangıç noktası iki kural oluşturmaktır:

- Makro içeren bir Office açmadan önce kullanıcıları uyarın. Fidye yazılımları makroların içine gizlenmiş olabilir, bu yüzden kullanıcıları bu dosyaları henüz haberlerin dışında olan kişilerden açmamalarını sağlıyoruz.

- Fidye yazılımı veya başka zararlı kodlar içer verebilecek dosya türlerini engelin. Ortak bir yürütülebilir dosya listesiyle (aşağıdaki tabloda listelenmiştir) başlayacağız. Organizasyonunız bu yürütülebilir dosya türlerinden herhangi birini kullanıyorsa ve bunların e-postayla gönderilmelerini bekliyorsanız, bunları önceki kurala ekleyin (kullanıcıları uyarın).

Posta aktarım kuralı oluşturmak için, kısa [bir eğitim videosu izleyin](increase-threat-protection.md#protect-against-ransomware) veya aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. Posta **akışı kategorisinde kurallar'ı** **seçin**.

3. öğesini **+** ve ardından Yeni **kural oluştur'a seçin**.

4. Tüm seçenekleri görmek için iletişim kutusunun en altındaki **** düğmesini seçin.

5. Her kural için aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarları değiştirmek istemiyorsanız, varsayılan ayarda bırakın.

6. **Kaydet**'i seçin.
    
| Ayar | Dosya eklerini açmadan önce Office uyar | Fidye yazılımı veya başka zararlı kodlar içer verebilecek dosya türlerini engelleme |
|:-----|:-----|:-----|
|Name  <br/> |Fidye yazılımıyla mücadele kuralı: kullanıcıları uyarın  <br/> |Fidye yazılımı koruması kuralı: dosya türlerini engelleme  <br/> |
|Bu kuralı şu durumda uygula: . . .  <br/> |Herhangi bir ek. . . dosya uzantısı eşleşmeleri . . .  <br/> |Herhangi bir ek. . . dosya uzantısı eşleşmeleri . . .  <br/> |
|Sözcükleri veya tümcecikleri belirtme  <br/> |Şu dosya türlerini ekleyin:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Şu dosya türlerini ekleyin:  <br/> ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, iss, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif  <br/> |
|Aşağıdakini yapın. . .  <br/> |Uyarı hazırlama  <br/> |İletiyi engelin. . . iletiyi reddetme ve açıklama içerme  <br/> |
|İleti metni sağlama  <br/> |Bu tür dosyaları açmayın; beklemedikçe— dosyalar kötü amaçlı kodlar içeriyor olabilir ve göndereni bilmek bir güvenlik garantisi değildir.  <br/> ||
   
> [!TIP]
> Ayrıca, 4. Adım: Kötü amaçlı yazılımdan koruma'da engellemek [istediğiniz dosyaları kötü amaçlı yazılımdan koruma listesine de ekleyebilirsiniz](#4-protect-against-malware).

Daha fazla bilgi için bkz.:

- [Fidye yazılımı: riski azaltma](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Office 365](../../security/defender-endpoint/office-365-microsoft-defender-antivirus.md)

- [OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="6-stop-auto-forwarding-for-email"></a>6: E-posta için otomatik iletmeyi durdurma

Kullanıcının posta kutusuna erişim elde eden bilgisayar korsanları, posta kutusunu e-postayı otomatik olarak ilet olacak şekilde yapılandırarak e-postayı aradan atacaktır. Bu sorun, kullanıcı farkında olmadan bile olabilir. Posta akış kuralı yapılandırarak bunun önüne geçebilirsiniz.

Posta aktarım kuralı oluşturmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. Posta **akışı kategorisinde kurallar'ı** **seçin**.

3. öğesini **+** ve ardından Yeni **kural oluştur'a seçin**.

4. Tam **seçenek kümesi** görmek için iletişim kutusunun altındaki Diğer seçenekler'i seçin.

5. Aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarları değiştirmek istemiyorsanız, diğer ayarları varsayılanda bırakın.

6. **Kaydet**'i seçin.

|Ayar|Dış etki alanlarına Otomatik Iletme e-postalarını reddetme|
|---|---|
|Name|E-postanın dış etki alanlarına otomatik olarak ilet 100'den fazla etki alanıyla ileriye doğru ilet 1|
|Bu kuralı şu durumda uygula:|Gönderen . . . dış/iç . . . Kuruluşun içinde|
|Koşul ekle|Alıcı . . . dış/iç . . . Kuruluş dışında|
|Koşul ekle|İleti özellikleri . . . ileti türünü de içerir. . . Otomatik olarak iletme|
|Aşağıdakini yapın ...|İletiyi engelin. . . iletiyi reddeder ve bir açıklama içerir.|
|İleti metni sağlama|Güvenlik nedeniyle e-postanın bu kuruluş dışında otomatik olarak ilet organizasyonun dışından iletilem engellenebilir.|

## <a name="7-use-office-message-encryption"></a>7: İleti Şifrelemesi Office'i kullanma

Office Şifreleme, iletiye dahil Microsoft 365. Zaten ayarlanmış durumdadır. İleti Office ile, kuruluşları içindeki ve dışındaki kişiler arasında şifrelenmiş e-posta iletileri gönderebilir ve alabilirsiniz. Office 365 İleti Şifrelemesi e-posta Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyemelerini sağlamaya yardımcı olur.

Office Şifreleme, posta gönderirken iki koruma seçeneği sağlar:

- İleriye iletme

- Encrypt

Kuruluş, e-postaya etiket uygulayan Gizli gibi başka seçenekler yapılandırmış olabilir.

### <a name="to-send-protected-email"></a>Korumalı e-posta göndermek için

PC için Outlook'de, **e-postada Seçenekler'i** ve sonra İzinler'i **seçin**.

![E-posta iletisi şifreleme Outlook.](../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639a.png)

Outlook.com'da, **e-postada Koru'ya** gidin. Varsayılan koruma, **Iletme ayarındadır**. Bunu şifrele olacak şekilde değiştirmek için İzinleri **Şifrele'yi** \> **seçin**.

![Outlook.com'da e-posta iletisi şifrelemesi.](../../media/329ccf50-f6b1-4fb8-b249-60b907a82b7e.png)

### <a name="to-receive-encrypted-email"></a>Şifreli e-posta almak için

Alıcının Outlook 2013 veya Outlook 2016 hesabı ve bir Microsoft e-posta hesabı varsa, Okuma bölmesinde öğenin kısıtlanmış izinleri hakkında bir uyarı alır. İletiyi açtıktan sonra, alıcı iletiyi de tıpkı diğer biri gibi iletiyi de iletiyi görüntüler.

Alıcı başka bir e-posta istemcisi veya Gmail ya da Yahoo gibi bir e-posta hesabı kullanıyorsa, e-posta iletisi okumak için oturum açmasını sağlayan bir bağlantı görüntüler veya iletiyi web tarayıcısında görüntülemek için tek seferlik geçiş kodu ister. Kullanıcılar e-postayı almıyorsa İstenmeyen veya Gereksiz klasörlerini kontrol etmelerini istiyorum.

> [!TIP]
> Daha fazla bilgi için bkz[. PC için Posta'da şifrelenmiş iletileri gönderme, Outlook ve yanıtlama](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="8-protect-your-email-from-phishing-attacks"></a>8. E-postanızı kimlik avı saldırılarından koruyun

Kimlik avı ortamınız için bir veya daha fazla özel etki Microsoft 365 yapılandırdıysanız, hedefli kimlik avı korumasını yapılandırabilirsiniz. Office 365 için Microsoft Defender'ın bir parçası olan Kimlik avı koruması, organizasyonlarınızı kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarından ve diğer kimlik avı saldırılarından korumaya yardımcı olabilir. Özel etki alanını yapılandırmadınız, bunu yapmak zorunda değilsiniz.

En önemli kullanıcılarınızı ve özel etki alanınızı korumak için bir ilke oluşturarak, bu korumayla çalışmaya başlamanızı öneririz.

For Office 365 Defender'da kimlik avına karşı koruma ilkesi oluşturmak için kısa bir [eğitim videosunu](increase-threat-protection.md#protect-your-email-from-phishing-attacks) izleyin veya aşağıdaki adımları tamamlayın:

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.

2. **İlkeler bölümünde &-posta** \> **& kuralları Tehdit** \> **ilkeleri** \> **Kimlik** avıyla mücadele ilkeleri **bölümüne** gidin.

3. Kimlik avı önleme sayfasında + **Oluştur'a tıklayın**. Kimlik avına karşı koruma ilkenizi tanımlamanız için size yol belirleyen bir sihirbaz başlatır.

4. İlkenizin adını, açıklamasını ve ayarlarını aşağıdaki grafikte önerilen şekilde belirtin. Daha fazla bilgi için bkz[. Kimlik avı önleme seçenekleri için Microsoft Defender'da kimlik Office 365 öğrenin](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Ayarlarınızı gözden geçirdikten sonra, Uygun şekilde **Bu ilkeyi oluştur'a veya** **Kaydet'e** tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Etki alanı ve en değerli kampanya personeli|
|Açıklama|En önemli personelin ve etki alanımızın kimliğine bürünülmemelerini sağlar.|
|Korumak için kullanıcı ekleme|+ **Koşul ekle'yi seçin; Alıcı:** Kullanıcı adlarını yazın veya aday, kampanya yöneticisi ve diğer önemli personel üyelerinin e-posta adresini girin. Kimliğe bürünmelerden korumak istediğiniz en çok 20 iç ve dış adres ebilirsiniz.|
|Korumak için etki alanı ekleme|+ **Koşul ekle'yi seçin; Alıcı etki alanı:** Tanımladıysanız, Microsoft 365 aboneliğiniz ile ilişkili özel etki alanını girin. Birden çok etki alanı girebilirsiniz.|
|Eylemleri seçme|E-posta kimliğine bürünülen bir kullanıcı tarafından gönderilirse **: İletiyi** başka bir e-posta adresine yeniden yönlendir'i seçin ve sonra güvenlik yöneticisinin e-posta adresini yazın; örneğin, securityadmin@contoso.com. <br/> E-posta kimliğine bürünülen bir etki alanı tarafından gönderilirse: İletiyi **karantinaya alın'ı seçin**.|
|Posta kutusu zekası|Yeni bir kimlik avı önleme ilkesi  oluşturmak, posta kutusu zekası varsayılan olarak seçilidir. En iyi sonuçları elde **etmek için bu** ayarı Açık bırakın.|
|Güvenilen gönderenleri ve etki alanlarını ekleme|Bu örnekte, geçersiz kılmalar tanımlamayın.|
|Uygulamanın uygulandığı yer|Alıcı **etki alanı' seçin**. Bu **seçeneklerden herhangi biri altında** Seç'i **seçin**. **+ Ekle'yi seçin**. Etki alanı adının yanındaki onay kutusunu seçin (örneğin, contoso.com ekle'yi seçin ve sonra da **Ekle'yi seçin**. **Bitti'yi seçin**.|

> [!TIP]
> Daha fazla bilgi için bkz[. Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="9-protect-against-malicious-attachments-files-and-urls"></a>9: Kötü amaçlı eklere, dosyalara ve URL'lere karşı koruma

Kişiler belge, sunu, elektronik tablo gibi ekleri düzenli aralıklarla gönderir, alır ve paylaşır. Yalnızca bir e-posta iletisine bakarak eklerin güvenli mi yoksa kötü amaçlı mı olduğunu söylemek her zaman kolay değildir. Office 365 için Microsoft Defender Kasa Koruması içerir, ancak bu koruma varsayılan olarak açık değildir. Bu korumayı kullanmaya başlamak için yeni bir kural oluşturmanızı öneririz. Bu koruma dosya ve klasörlerin SharePoint, OneDrive ve Microsoft Teams.

### <a name="set-up-safe-attachments"></a>Ekleri Kasa Ayarlama

Daha fazla Kasa ilkesi oluşturmak için, kısa [bir eğitim videosu izleyin](increase-threat-protection.md) veya aşağıdaki adımları tamamlayın:

1. Yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin ve yönetici hesabınızla oturum açın.

2. **İlkeler bölümünde& te E-posta** \> **& birlikte çalışma İlkeleri ve kuralları** \> **Tehdit ilkeleri** \> **Kötü** amaçlı yazılımdan koruma **ilkeleri bölümüne** gidin.

3. Yeni **bir ilke oluşturmak için +** Oluştur'a seçin.

4. Aşağıdaki tabloda yer alan ayarları uygulama.

5. Ayarlarınızı gözden geçirdikten sonra, Uygun şekilde **Bu ilkeyi oluştur'a veya** **Kaydet'e** tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Kötü amaçlı yazılım algılandı olarak mevcut ve gelecekteki e-postaları engelin.|
|Açıklama|Kötü amaçlı yazılım algılandı olarak mevcut ve gelecek e-postaları ve ekleri engelin.|
|Bilinmeyen kötü amaçlı yazılım yanıtını kaydetme|Engelle **- Geçerli ve gelecekteki e-postaları ve kötü amaçlı yazılım algılandı olan ekleri engelle'yi seçin**.|
|Eki algılamada yeniden yönlendirme|Yeniden yönlendirmeyi etkinleştir (bu kutuyu seçin) <br/> Yönetici hesabını veya karantina için posta kutusu kurulumunu girin. <br/> Kötü amaçlı yazılım ekleri tarayanın zaman dışında veya hata oluştuğunda yukarıdaki seçimi uygula (bu kutuyu seçin).|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

> [!TIP]
> Daha fazla bilgi için bkz[. Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

### <a name="set-up-safe-links"></a>Bağlantı Kasa ayarlama

Bilgisayar korsanları bazen e-posta veya diğer dosyalarda bağlantılarda kötü amaçlı web sitelerini gizler. Kasa için Microsoft Defender'ın bir parçası olan Office 365 Bağlantıları, e-posta iletilerinde ve belgelerinde web adreslerinin (URL)'lerde tıklamalı doğrulama sağlayarak, Office yardımcı olabilir. Koruma, Bağlantı ilkeleri Kasa tanımlanır.

Saldırılara karşı korumak için şunları yapın:

- Korumayı artırmak için varsayılan ilkeyi değiştirme.

- Etki alanınız içinde yer alan tüm alıcılara hedeflenen yeni bir ilke ekleyin.

Bağlantılara Kasa için kısa bir [eğitim videosu izleyin](increase-threat-protection.md#protect-against-phishing-attacks-with-safe-links) veya aşağıdaki adımları tamamlayın:

1. Yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin ve yönetici hesabınızla oturum açın.

2. **İlkeler bölümünde& te E-posta** \> **& birlikte çalışma İlkeleri ve kuralları** \> **Tehdit ilkeleri** \> **Kötü** amaçlı yazılımdan koruma **ilkeleri bölümüne** gidin.

3. Yeni **bir ilke oluşturmak** veya varsayılan ilkeyi değiştirmek için + Oluştur'a seçin.

Varsayılan ilkeyi değiştirmek için:

1. Varsayılan ilkeye **çift** tıklayın. Bir açılır çıktı görüntülenir. 

2. Çıkış **öğesinin alt** kısmında Koruma ayarlarını düzenle'yi seçin.

3. Varsayılan ilkeyi değiştirdikten sonra Kaydet'i **seçin**.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Kasa etki alanındaki tüm alıcılar için bağlantı ilkesi ekleme|
|İletilerde kötü amaçlı olabilecek bilinmeyen URL'lerin eylemlerini seçme|**Açık'ı seçin: KULLANıCı bağlantıya tıkladığında**, URL'ler yeniden yazılır ve bilinen kötü amaçlı bağlantılar listesinde denetlenir.|
|Dosyaları işaret alan şüpheli bağlantılar ve bağlantılar için gerçek zamanlı URL tarama uygulama|Bu kutuyu seçin.|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

> [!TIP]
> Daha fazla bilgi için bkz. [Kasa için Microsoft Defender'daki Office 365](../../security/office-365-security/atp-safe-links.md).

## <a name="10-increase-protection-for-your-organizations-devices"></a>10: Kuruluş cihazları için korumayı artırma

Microsoft Defender Virüsten Koruma, Windows işletim sisteminde yerleşik olarakdır ve virüslere ve kötü amaçlı yazılımlara karşı iyi bir koruma sağlar. Bununla birlikte, organizasyonlu cihazları sizin gibi küçük ve orta ölçekli işletmelere uygun yeni bir teklif olan İş için Microsoft Defender'a yükerek korumayı artırabilirsiniz. İş için Defender ile, kuruluş cihazları fidye yazılımlarına, kötü amaçlı yazılımlara, kimlik avına ve diğer tehditlere karşı daha iyi korunur.

**1 Mart 2022'den itibaren İş için [Microsoft Defender](../../security/defender-business/index.yml)** özellikleri yeni Microsoft 365 İş Ekstra. 


Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [İş için Microsoft Defender'a genel bakış](../../security/defender-business/mdb-overview.md)

- [İş için Microsoft Defender'ı ayarlama ve yapılandırma](../../security/defender-business/mdb-setup-configuration.md)

- [Microsoft 365 Defender portalını kullanmaya başlama](../../security/defender-business/mdb-get-started.md)

## <a name="related-content"></a>İlgili içerik

[Birden çok faktörlü kimlik Microsoft 365](multi-factor-authentication-microsoft-365.md) (makale)\
[Öncelik hesaplarını yönetme ve izleme](../setup/priority-accounts.md) (makale)\
[Microsoft 365 Merkezinde Rapor Raporları](../activity-reports/activity-reports.md) (video)