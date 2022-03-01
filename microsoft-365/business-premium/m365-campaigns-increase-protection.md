---
title: Tehdit korumasını artırma
f1.keywords:
- NOCSH
ms.author: sharik
author: Skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 5abfef7b-5957-484a-b06b-a7c55e013e44
description: E-Microsoft 365'de koruma düzeyini artırmayla ilgili Microsoft 365
ms.openlocfilehash: 8a3f2e26a34cc84d17305badd7be3f8497cd3e41
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019449"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>Güvenlik için tehdit korumasını Microsoft 365 İş Ekstra

Bu makale kimlik avına, kötü amaçlı yazılıma Microsoft 365 diğer tehditlere karşı korumak üzere e-posta aboneliğinizin korumasını artırmanıza yardımcı olur. Bu öneriler, kampanyalar, hukuk daireleri ve sağlık hizmetleri gibi güvenlik önlemleri artırılmış kuruluşlara uygundur.

Başlamadan önce Microsoft Güvenli Puanınızı kontrol edin. Microsoft Güvenli Puanı, normal etkinliklerinize ve güvenlik ayarlarınıza göre kuruluş güvenliğini analiz eder ve bir puan atar. Geçerli puanınızı not alarak başlama. Bu makalede önerilen işlemler gerçekleştirerek puanınızı artırır. Amaç maksimum puanı elde etmek değil, kullanıcılarınız için üretkenliği olumsuz etkilemeyen ortamınızı koruma fırsatlarını da takip etmektir.

Daha fazla bilgi için [bkz. Microsoft Güvenli Puanı](../security/defender/microsoft-secure-score.md).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Postada kötü amaçlı yazılıma karşı koruma düzeyini yükseltme

Varsayılan Office 365 veya Microsoft 365 ortamınız kötü amaçlı yazılıma karşı koruma içerir, ancak kötü amaçlı yazılımda yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek bu korumayı artırabilirsiniz. E-postada kötü amaçlı yazılım korumasıyla çarpmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Güvenlik & Merkezi'ne gidin</a> ve yönetici hesabı kimlik bilgilerinizle oturum açın.

2. Sol gezinti bölmesinde, Tehdit yönetimi'nin **altında İlke** Kötü Amaçlı **Yazılımdan** \> **Koruma'ya tıklayın**.

3. Şirket çapında bu ilkeyi düzenlemek için varsayılan ilkeye çift tıklayın.

4. **Ekle'Ayarlar**.

5. Ortak **Ek Türleri Filtresi'nin altında** **Aç'ı seçin**. Engellenmiş dosya türleri, bu denetimin hemen altındaki pencerede listelenir. Şu dosya türlerini ekleyenin:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Gerekirse, daha sonra dosya türlerini ekleyebilir veya silebilirsiniz.

6. **Kaydet'e tıklayın.**

Daha fazla bilgi için bkz [. EOP'de kötü amaçlı yazılımdan koruma](../security/office-365-security/anti-malware-protection.md).

## <a name="protect-against-ransomware"></a>Fidye yazılımlarına karşı koruma

Fidye yazılımları, dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilere erişimi kısıtlar. Daha sonra, verilere erişim için genellikle Bitcoin gibi şifreleme şifrelemeleri biçimine sahip olan "bilgi" istemeleri ile onaylatan paralar hakkında bilgi istemeye çalışır.

Fidye yazılımları için yaygın olarak kullanılan dosya uzantılarını engellemek (bunlar posta adımlarında kötü amaçlı yazılımlara karşı koruma düzeyine yükseltildi) veya bu ekleri e-postayla alan kullanıcıları uyarmak için bir veya birden çok posta akış kuralı oluşturarak fidye yazılımlarına karşı koruma sabilirsiniz.[](#raise-the-level-of-protection-against-malware-in-mail)

Önceki adımda engelle dosyalara ek olarak, makro içeren ekleri açmadan önce kullanıcıları uyarmak için bir kural Office iyi bir yöntemdir. Fidye yazılımları makroların içine gizlenmiş olabilir, bu nedenle kullanıcıları bu dosyaları kimsenin görene kadar açmamaya uyar.

Posta aktarım kuralı oluşturmak için:

1. Yönetim merkezine gidin ve Yönetim merkezleri '<https://admin.microsoft.com>**ni Exchange** \> **.**

2. Posta akışı **kategorisinde kurallar'a** **tıklayın**.

3. öğesini **+** ve ardından Yeni **kural oluştur'u tıklatın**.

4. Tam **seçenek kümesi** görmek için iletişim kutusunun en altındaki Diğer seçenekler'e tıklayın.

5. Kural için aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarları değiştirmek istemiyorsanız, varsayılan ayarda bırakın.

6. **Kaydet**'e tıklayın.

|Ayar|Dosya eklerini açmadan önce Office uyar|
|---|---|
|Name|Fidye yazılımıyla mücadele kuralı: kullanıcıları uyarın|
|Bu kuralı şu durumda uygula: . . .|Herhangi bir ek. . . dosya uzantısı eşleşmeleri . . .|
|Sözcükleri veya tümcecikleri belirtme|Şu dosya türlerini ekleyin: <br/> `dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm`|
|Aşağıdakini yapın. . .|Alıcıyı bir iletiyle bilgilendirin|
|İleti metni sağlama|Bu tür dosyaları, kötü amaçlı kod içeren makrolar içere içere bilmleri olduğundan, bu tür dosyaları açmayın.|

Daha fazla bilgi için bkz.:

- [Fidye yazılımı: riski azaltma](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [OneDrive](https://support.microsoft.com//office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>E-posta için otomatik iletmeyi durdurma

Bir kullanıcının posta kutusuna erişim elde eden bilgisayar korsanları, posta kutusunu otomatik olarak e-postayı iletacak şekilde ayarerek postanızı çalarlar. Bu durum, kullanıcının farkında olmadan bile olabilir. Posta akış kuralı yapılandırarak bunun önüne geçebilirsiniz.

Posta aktarım kuralı oluşturmak için bu kısa [videoyu izleyin veya](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) şu adımları izleyin:

1. Daha fazla <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetim **merkezleri'ne** \> **Exchange**.

2. Posta akışı **kategorisinde kurallar'a** **tıklayın**.

3. öğesini **+** ve ardından Yeni **kural oluştur'u tıklatın**.

4. Tam **seçenek kümesi** görmek için iletişim kutusunun en altındaki Diğer seçenekler'e tıklayın.

5. Aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarları değiştirmek istemiyorsanız, varsayılan ayarda bırakın.

6. **Kaydet**'e tıklayın.

|Ayar|Dosya eklerini açmadan önce Office uyar|
|---|---|
|Name|E-postanın dış etki alanlarına otomatik olarak ilet ingingsini engelleme|
|Bu kuralı şu durumda uygula:|Gönderen . . . dış/iç . . . Kuruluşun içinde|
|Koşul ekle|İleti özellikleri . . . ileti türünü de içerir. . . Otomatik olarak iletme|
|Aşağıdakini yapın ...|İletiyi engelin. . . iletiyi reddeder ve bir açıklama içerir.|
|İleti metni sağlama|Güvenlik nedeniyle e-postanın bu kuruluş dışında otomatik olarak ilet organizasyonun dışından iletilem engellenebilir.|

## <a name="protect-your-email-from-phishing-attacks"></a>E-postanızı kimlik avı saldırılarından koruma

Kimlik avı ortamınız veya ortamınız için bir veya daha fazla Office 365 etki Microsoft 365, hedefli kimlik avı korumasını yapılandırabilirsiniz. Office 365 için Microsoft Defender'ın bir parçası olan Kimlik avı koruması, kurumlarınızı kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarından ve diğer kimlik avı saldırılarından korumaya yardımcı olabilir. Özel etki alanını yapılandırmadınız, bunu yapmak zorunda değilsiniz.

En önemli kullanıcılarınızı ve özel etki alanınızı korumak için bir ilke oluşturarak, bu korumayla çalışmaya başlamanızı öneririz.

Office 365 için Defender'da kimlik avına karşı koruma ilkesi oluşturmak için bu kısa eğitim [videosunu](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c) izleyin veya aşağıdaki adımları tamamlayın:

1. Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">ve uyumluluk Office 365'& gidin</a>.

2. Sol gezinti bölmesinde, Tehdit yönetimi'nin **altında İlke'yi** **seçin**.

3. İlke **sayfasında** Kimlik avı **önleme'yi seçin**.

4. Kimlik avı **önleme sayfasında +** **Oluştur'a tıklayın**. Kimlik avına karşı koruma ilkenizi tanımlamanız için size yol belirleyen bir sihirbaz başlatır.

5. İlkenizin adını, açıklamasını ve ayarlarını aşağıdaki grafikte önerilen şekilde belirtin. Daha fazla bilgi için bkz[. Kimlik avı önleme seçenekleri için Microsoft Defender'da kimlik Office 365 öğrenin](../security/office-365-security/set-up-anti-phishing-policies.md).

6. Ayarlarınızı gözden geçirmenizin ardından, Uygun şekilde Bu **ilkeyi oluştur'a veya** **Kaydet'e** tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Etki alanı ve en değerli personel|
|Açıklama|En önemli personelin ve etki alanımızın kimliğine bürünülmemelerini sağlar.|
|Korumak için kullanıcı ekleme|+ **Koşul ekle'yi seçin; Alıcı:** Kullanıcı adlarını yazın veya işletme sahiplerinin, ortaklarının veya adayın, yöneticilerin ve diğer önemli personel üyelerinin e-posta adresini girin. Kimliğe bürünmelerden korumak istediğiniz en çok 20 iç ve dış adres ebilirsiniz.|
|Korumak için etki alanı ekleme|+ **Koşul ekle'yi seçin; Alıcı etki alanı:** Tanımladıysanız, Microsoft 365 aboneliğiniz ile ilişkili özel etki alanını girin. Birden çok etki alanı girebilirsiniz.|
|Eylemleri seçme|E-posta kimliğine bürünülen bir kullanıcı tarafından gönderilirse: İletiyi başka bir e-posta adresine yeniden yönlendir'i seçin ve sonra güvenlik yöneticisinin e-posta adresini yazın; örneğin, *Ali<span><span>@contoso.com*. <br/> E-posta kimliğine bürünülen bir etki alanı tarafından gönderilirse: İletiyi **karantinaya alın'ı seçin**.|
|Posta kutusu zekası|Yeni bir kimlik avı önleme ilkesi  oluşturmak, posta kutusu zekası varsayılan olarak seçilidir. En iyi sonuçları elde **etmek için bu** ayarı Açık bırakın.|
|Güvenilen gönderenleri ve etki alanlarını ekleme|Buradan kendi etki alanlarınızı veya diğer güvenilen etki alanlarınızı  eklemeye devam edersiniz.|
|Uygulamanın uygulandığı yer|Alıcı **etki alanı' seçin**. Bu **seçeneklerden herhangi biri altında** Seç'i **seçin**. **+ Ekle'yi seçin**. Etki alanı adının yanındaki onay kutusunu işaretleyin; örneğin, *contoso.<span><span> com'a* tıklayın ve ardından Ekle'yi **seçin**. **Bitti'yi seçin**.|

Daha fazla bilgi için bkz[. Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-links-with-defender-for-office-365"></a>Dosya için Defender ile kötü amaçlı eklere, dosyalara ve bağlantılara karşı Office 365

!['ya işaret alan başlık https://aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)

İlk olarak, yönetim merkezinde yeni yönetim <https://admin.microsoft.com> merkezi önizlemesini açık olduğundan emin olun. Yeni yönetim merkezi metninin yanındaki **iki durumlu düğmeyi açma/kapatma**.

   ![Yeni yönetim merkezi önizlemesi.](../media/previewon.png)

Kiracınıza henüz kartlardan **sahip Kurulum** sayfasını görmüyorsanız, bu adımların nasıl tamamlanacaklarını Güvenlik ve Uyumluluk Merkezi'nde & bakın. Güvenlik [ve Kasa Merkezi'nde Güvenlik &'nde](#set-up-safe-attachments-in-the-security--compliance-center) Ekleri Ayarlama ve Güvenlik [Kasa'nde Ekleri Ayarlama &.](#set-up-safe-links-in-the-security--compliance-center)

1. Sol gezintide Kurulum'u **seçin**.
2. Kurulum sayfasında **Gelişmiş** tehditlere karşı **korumayı** **artır kartında Görüntüle'yi** seçin.

   ![Gelişmiş tehditlere karşı Artıran korumada Görüntüle'yi seçin.](../media/startatp.png)

3. Gelişmiş **tehditlere karşı korumayı artır sayfasında** , **Başla'ya tıklayın**.
4. Açılan bölmede E-postada bağlantılar ve **ekler,** **SharePoint, OneDrive ve Teams'te** dosyaları tara ve Office masaüstü ve **Office Online** uygulamaları'nın altında Bağlantıları tara'nın yanındaki onay kutularını **işaretleyin**.

   **E-postada bulunan bağlantılar ve ekler'in** altında, Tüm Kullanıcılar'a veya e-postalarını tarantıracak belirli kullanıcılara yazın.

   ![Gelişmiş tehditlere karşı korumayı artır seçeneğinde tüm onay kutularını seçin.](../media/setatp.png)

5. **Ekleri ve Bağlantıları** Paylaş'ı Kasa için İlkeler Kasa seçin.

### <a name="set-up-safe-attachments-in-the-security--compliance-center"></a>Güvenlik Kasa & Merkezi'nde ekleri & ayarlama

Kişiler belge, sunu, elektronik tablo gibi ekleri düzenli aralıklarla gönderir, alır ve paylaşır. Yalnızca bir e-posta iletisine bakarak eklerin güvenli mi yoksa kötü amaçlı mı olduğunu söylemek her zaman kolay değildir. Office 365 için Microsoft Defender Kasa Koruması içerir, ancak bu koruma varsayılan olarak açık değildir. Bu korumayı kullanmaya başlamak için yeni bir kural oluşturmanızı öneririz. Bu koruma dosya ve klasörlerin SharePoint, OneDrive ve Microsoft Teams.

Ek Kasa ilkesi oluşturmak için bu [kısa videoyu izleyin](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5) veya aşağıdaki adımları tamamlayın:

1. Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Uyumluluk &'ne</a> gidin ve yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesinde, Tehdit yönetimi'nin **altında İlke'yi** **seçin**.

3. İlke sayfasında Ekleri **Ekle'Kasa seçin**.

4. Ekleri Kasa bu korumayı daha geniş bir şekilde uygulamak için SharePoint **,** OneDrive ve diğer Microsoft Teams seçin.

5. Yeni **+** bir ilke oluşturmak için öğesini seçin.

6. Aşağıdaki tabloda yer alan ayarları uygulama.

7. Ayarlarınızı gözden geçirdikten sonra, Uygun **şekilde Bu ilkeyi oluştur'a** **veya Kaydet'e** tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Kötü amaçlı yazılım algılandı olarak mevcut ve gelecekteki e-postaları engelin.|
|Açıklama|Kötü amaçlı yazılım algılandı olarak mevcut ve gelecek e-postaları ve ekleri engelin.|
|Bilinmeyen kötü amaçlı yazılım yanıtını kaydetme|Engelle **- Geçerli ve gelecekteki e-postaları ve kötü amaçlı yazılım algılandı olan ekleri engelle'yi seçin**.|
|Eki algılamada yeniden yönlendirme|Yeniden yönlendirmeyi etkinleştir (bu kutuyu seçin) <br/> Yönetici hesabını veya karantina için posta kutusu kurulumunu girin. <br/> Kötü amaçlı yazılım ekleri tarayanın zaman dışında veya hata oluştuğunda yukarıdaki seçimi uygula (bu kutuyu seçin).|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

Daha fazla bilgi için bkz[. Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

### <a name="set-up-safe-links-in-the-security--compliance-center"></a>Güvenlik Kasa Uyumluluk Merkezi'nde güvenlik & ayarlama

Bilgisayar korsanları bazen e-posta veya diğer dosyalarda bağlantılarda kötü amaçlı web sitelerini gizler. Kasa için Microsoft Defender'ın bir parçası olan Office 365 Bağlantıları, e-posta iletilerinde ve belgelerinde web adreslerinin (URL)'lerde tıklamalı doğrulama sağlayarak, Office yardımcı olabilir. Koruma, Bağlantı ilkeleri Kasa tanımlanır.

Şunları yapmanizi öneririz:

- Korumayı artırmak için varsayılan ilkeyi değiştirme.

- Etki alanınız içinde yer alan tüm alıcılara hedeflenen yeni bir ilke ekleyin.

Bağlantılar'Kasa ayarlamak için bu [kısa eğitim videosunu izleyin](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa) veya aşağıdaki adımları tamamlayın:

1. Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Uyumluluk &'ne</a> gidin ve yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesinde, Tehdit yönetimi'nin **altında İlke'yi** **seçin**.

3. İlke sayfasında, **Bağlantılar'ı Kasa seçin**.

Varsayılan ilkeyi değiştirmek için:

1. Yeni Kasa sayfasında, Kuruluşun **tamamına uygulanacak ilkeler'in altında** Varsayılan **ilke'yi** seçin.

2. E **Ayarlar dışındaki içeriğe uygun seçenekler'in** altında **iOS ve Android için Kurumlar için Microsoft 365 Uygulamaları, Office'i seçin**.

3. **Kaydet**'e tıklayın.

Etki alanınız içinde yer alan tüm alıcılara hedeflenen yeni bir ilke oluşturmak için:

1. Yeni Kasa, Kuruluşun tamamına **uygulanacak ilkeler'in altında**, yeni bir **+** ilke oluşturmak için tıklayın.

2. Aşağıdaki tabloda listelenen ayarları uygulama.

3. **Kaydet**'e tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Kasa etki alanındaki tüm alıcılar için bağlantı ilkesi ekleme|
|İletilerde kötü amaçlı olabilecek bilinmeyen URL'lerin eylemlerini seçme|**Açık'ı seçin: KULLANıCı bağlantıya tıkladığında**, URL'ler yeniden yazılır ve bilinen kötü amaçlı bağlantılar listesinde denetlenir.|
|İndirilebilir Kasa taramak için Ekleri Kullanma|Bu kutuyu seçin.|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

Daha fazla bilgi için bkz. [Kasa için Defender'daki Bağlantılar'Office 365](../security/office-365-security/safe-links.md).

## <a name="turn-on-the-unified-audit-log"></a>Birleşik Denetim Günlüğü'ne açma

Güvenlik Ve Uyumluluk Merkezi'nde denetim günlüğü aramasını & sonra, yöneticiyi ve diğer kullanıcı etkinliğini günlükte bulundurarak arayabilirsiniz.

Exchange Online aboneliğinde denetim günlüğü aramalarını açmak veya kapatmak için, bu abonelikte Denetim Günlükleri rolüne Microsoft 365 gerekir. Varsayılan olarak bu rol, Yönetim Merkezi'nin İzinler sayfasındaki Uyumluluk Yönetimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. E-posta Microsoft 365 genel yöneticiler bu grubun varsayılan üyeleridir.

1. Denetim günlüğü aramasını açmak için, yönetim merkezine <https://admin.microsoft.com> gidin ve sol gezinti çubuğundaki **Yönetim merkezleri'nin altında Güvenlik'i** seçin.
2. Güvenlik Microsoft 365 **' seçin**, ardından **Güvenlik ve** Uyumluluk Merkezi **kartında Office 365'&** seçin.

    ![Güvenlik ve uyumluluk arabaları için & seçin.](../media/gotosecandcomp.png)
3. Güvenlik ve uyumluluk sayfasında Arama'ya ve **sonra Denetim** günlüğü **araması'ne tıklayın**.
4. Denetim günlüğü araması sayfasının **en üstünde,** Denetimi **aç'ı seçin**.

Özellik açık durumdan sonra dosya, klasör ve çok sayıda etkinlik için arama gerçekleştirebilirsiniz. Daha fazla bilgi için bkz[. Denetim günlüğünde arama.](../compliance/search-the-audit-log-in-security-and-compliance.md)

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Dosya ve klasörlerinizi ayarlamak SharePoint anonim OneDrive ayarlarını ayarlama

(varsayılan anonim bağlantının süresini 14 gün olarak değiştirme, varsayılan paylaşım türünü "Belirli Kişiler" olarak değiştirme) E-OneDrive paylaşımı ayarlarını değiştirmek SharePoint:

1. Şu tarafta yönetim merkezine gidin ve sol <https://admin.microsoft.com> gezinti **SharePoint** **merkezleri'nin altında Yönet'i** seçin.
2. Yönetim SharePoint, İlkeler **Paylaşımı'ne** \> **gidin**.
3. Paylaşım sayfasında, Dosya ve klasör bağlantıları'nın altında Belirli kişiler'i seçin ve "Herkes" bağlantıları için gelişmiş ayarlar'ın altında Bu bağlantıların süresi bu kadar gün içinde dolacak ve 14 (veya bağlantı yaşam süresini kısıtlamak istediğiniz başka bir gün sayısı **)** yazın.

   ![Belirli kişiler'i seçin ve bağlantı süresinin son kullanma süresini 14 gün olarak ayarlayın.](../media/anyonelinks.png)

## <a name="activity-alerts"></a>Etkinlik uyarıları

Kuruluşta yönetici ve kullanıcı etkinliklerini izlemek, kötü amaçlı yazılım ve veri kaybı önleme olaylarını algılamak için etkinlik uyarılarını kullanabilirsiniz. Aboneliğiniz bir dizi varsayılan ilke içerir, ancak özel ilkeler de oluşturabilirsiniz. Daha fazla bilgi için uyarı [ilkelerine bakın](../compliance/alert-policies.md). Örneğin, bir dosyanın SharePoint dışında paylaşmalarını istemiyorsanız, biri bunu paylaştığında sizi uyaran bir bildirim oluşturabilirsiniz.

Aşağıdaki şekilde, yeni programlarla birlikte varsayılan ilkeler Microsoft 365.

![Bu ayarlara dahil edilen varsayılan Microsoft 365.](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>Takvim paylaşımını devre dışı bırakma veya yönetme

Kuruluşta kişilerin takvimlerini paylaşmalarını önlenebilir veya neleri paylaşeceklerini yönetebilirsiniz. Örneğin, paylaşımı yalnızca serbest/meşgul zamanları ile kısıtlarız.

1. Yönetim merkezine gidin ve Ayarlar <https://admin.microsoft.com> **Org** \> **Ayarlar** <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services'ı**</a> >  seçin.

1. **Takvim'i** seçin ve kuruluşta yer alan ve takvimlerini kuruluş dışından gelen veya başkalarıyla Office 365 veya Exchange paylaşıp paylaşamay seçin.

   Herhangi biri ile paylaş seçeneğini seçerseniz, yalnızca serbest/meşgul bilgilerini de paylaşmaya karar veabilirsiniz.

3. Sayfanın **alt kısmında** Değişiklikleri kaydet'i seçin.

   Aşağıdaki şekilde takvim paylaşımına izin verilmemektedir.

   ![Dış takvim paylaşımını izin verilmiyor olarak gösteren ekran görüntüsü.](../media/nocalendarsharing.png)

   Aşağıdaki şekilde, takvim paylaşımına yalnızca serbest/meşgul bilgilerini içeren bir e-posta bağlantısıyla izin verilen ayarlar yer alır.

   ![Takvim serbest/meşgul paylaşımının herkesle ekran görüntüsü.](../media/sharefreebusy.png)

Kullanıcılarınızı kendi takvimlerini paylaşmalarına izin veriliyorsa, diğer [kullanıcılardan takvimleri](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) paylaşmak için Web üzerinde Outlook.
