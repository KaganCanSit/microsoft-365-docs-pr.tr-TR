---
title: Microsoft 365 Kurumsal için tehdit korumasını artırma
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
description: Microsoft Defender'ı güvenlik için Office 365 kimlik avı, kötü amaçlı yazılım ve diğer tehditlere karşı hassas verileri korur.
ms.openlocfilehash: 8bf954930edc94ccf750bb334a62a4c8a4581f80
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010177"
---
# <a name="increase-threat-protection"></a>Tehdit korumasını artırma

Bu makale kimlik avına, kötü amaçlı yazılıma Microsoft 365 diğer tehditlere karşı korumak üzere e-posta aboneliğinizin korumasını artırmanıza yardımcı olur. Bu öneriler, hukuk daireleri ve sağlık hizmetleri gibi güvenlik ihtiyacı daha yüksek olan kuruluşlar için uygundur.

Başlamadan önce Güvenli Puanınızı Office 365 kontrol edin. Office 365 Puanı, normal etkinliklerinize ve güvenlik ayarlarınıza göre kuruluş güvenliklerini analiz eder ve bir puan atar. Geçerli puanınızı not alarak başlama. Puanınızı artırmak için bu makalede önerilen eylemleri gerçekleştirin. Amaç maksimum puanı elde etmek değil, kullanıcılarınız için üretkenliği olumsuz etkilemeyen ortamınızı koruma fırsatlarını da takip etmektir.

Daha fazla bilgi için [bkz. Microsoft Güvenli Puanı](../../security/defender/microsoft-secure-score.md).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Postada kötü amaçlı yazılıma karşı koruma düzeyini yükseltme

Sizin Office 365 veya Microsoft 365 ortamınız kötü amaçlı yazılıma karşı koruma içerir. Kötü amaçlı yazılımda yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek bu korumayı artırabilirsiniz. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi,</a> Daha **fazla göster, Yönetim merkezleri** **ve sonra da** Güvenlik'i **seçin**.

1. **E-posta ve işbirliği &'ne** \> **& tehdit ilkeleri'ne** \> **gidin**.

1. Kullanılabilir ilkelerden Kötü amaçlı yazılımdan **koruma'ya seçin**.

E-postada kötü amaçlı yazılıma karşı korumayı artırmak için:

1.  Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında</a>, İlkeler bölümünde **E-posta &** \> işbirliği **& kuralları** \> \> İlkeler bölümünde Tehdit ilkeleri **Kötü** amaçlı yazılımdan koruma **ilkeleri'ne** gidin.

2. Kötü amaçlı **yazılımdan koruma sayfasında** Varsayılan **(Varsayılan)'a çift tıklayın**. Bir açılır çıktı görüntülenir. 

3. Çıkış **öğesinin alt** kısmında Koruma ayarlarını düzenle'yi seçin. 

4. Koruma **ayarları'nın** altında, Yaygın ek filtresini **etkinleştir'in yanındaki onay kutusunu seçin**. Engellenen dosya türleri bu denetimin hemen altında listelenir. Şu dosya türlerini de eklemek istediğinizden emin olun:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Dosya türlerini eklemek veya silmek için, **listenin sonundaki** Dosya türlerini özelleştir'i seçin.

6. **Kaydet'i seçin.**

Daha fazla bilgi için bkz [. EOP'de kötü amaçlı yazılımdan koruma](../../security/office-365-security/anti-malware-protection.md).

## <a name="protect-against-ransomware"></a>Fidye yazılımlarına karşı koruma

Fidye yazılımları, dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilere erişimi kısıtlar. Daha sonra, verilere erişim için genellikle Bitcoin gibi şifreleme şifrelemeleri biçimine sahip olan "bilgi" istemeleri ile onaylatan paralar hakkında bilgi istemeye çalışır.

Fidye yazılımlarına karşı korunmak için, fidye yazılımları için yaygın olarak kullanılan dosya uzantılarını engellemek için bir veya daha fazla posta akış kuralı oluşturun. (Bu kuralları posta adımlarında [kötü amaçlı yazılıma karşı koruma düzeyini yükseltmeye eklediniz](#raise-the-level-of-protection-against-malware-in-mail) .) Bu ekleri e-postayla alan kullanıcıları da uyarabilirsiniz.

Önceki adımda engelleyilen dosyalara ek olarak, makro içeren bir dosya eklerini açmadan önce kullanıcıları uyarmak için Office bir kural oluşturmak iyi bir uygulamadır. Fidye yazılımları makroların içine gizlenmiş olabilir, bu nedenle kullanıcıları bu dosyaları kimsenin görene kadar açmamalarını uyarın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. 'da bulunan yönetim merkezinde, Yönetim [https://admin.microsoft.com](https://admin.microsoft.com)**Exchange** **yönet'i seçin**.

1. Sol menüden posta **akışı'ı seçin**.
 
1. Kurallar sekmesinde (+) simgesinin yanındaki oku seçin ve sonra da Yeni kural **oluştur'a tıklayın**.

1. Yeni **kural sayfasında kuralınız** için bir ad girin, en alta kaydırın ve ardından Diğer **seçenekler'i seçin**.

Posta aktarım kuralı oluşturmak için:

1. 'da yönetim merkezine gidin ve Yönetim <https://admin.microsoft.com>merkezleri '**ni ve ardından Exchange**\>.

2. Posta **akışı kategorisinde kurallar'ı** **seçin**.

3. öğesini **+** seçin ve ardından Yeni **kural oluştur'a seçin**.

4. Tam **seçenek kümesi** görmek için iletişim kutusunun altındaki Diğer seçenekler'i seçin.

5. Kural için aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarlar için varsayılan değerleri, değiştirmek istemiyorsanız kullanın.

6. **Kaydet**'i seçin.

|Ayar|Dosya eklerini açmadan önce Office uyar|
|---|---|
|Name|Fidye yazılımıyla mücadele kuralı: kullanıcıları uyarın|
|Bu kuralı şu durumda uygula: . . .|Herhangi bir ek. . . dosya uzantısı eşleşmeleri . . .|
|Sözcükleri veya tümcecikleri belirtme|Şu dosya türlerini ekleyin:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Aşağıdakini yapın. . .|Alıcıyı bir iletiyle bilgilendirin|
|İleti metni sağlama|Bu tür dosyaları, kötü amaçlı kod içeren makrolar içere içere bilmleri olduğundan, bu tür dosyaları açmayın.|

Daha fazla bilgi için bkz.:

- [Fidye yazılımı: riski azaltma](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>E-posta için otomatik iletmeyi durdurma

Bir kullanıcının posta kutusuna erişim elde eden bilgisayar korsanları, posta kutusunu otomatik olarak e-postayı iletacak şekilde ayarerek e-postaları çalmak anlamına gelir. Bu durum, kullanıcının farkında olmadan bile olabilir. Bunun önüne geçmek için bir posta akışı kuralı yapılandırabilirsiniz.

Posta aktarım kuralı oluşturmak için şu adımları izleyin:

1. Genel Microsoft 365 yönetim merkezi Yönetim **merkezleri'ni Exchange**\>.

2. Posta **akışı kategorisinde kurallar'ı** **seçin**.

3. öğesini **+** seçin ve ardından Yeni **kural oluştur'a seçin**.

4. Tüm seçenekleri görmek için, iletişim **kutusunun altındaki** Diğer seçenekler'i seçin.

5. Aşağıdaki tabloda yer alan ayarları uygulama. Diğer ayarlar için varsayılan değerleri, değiştirmek istemiyorsanız kullanın.

6. **Kaydet**'i seçin.

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

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.

2. **İlkeler bölümünde &-posta** \> **& kuralları Tehdit** \> **ilkeleri** \> **Kimlik** avıyla mücadele ilkeleri **bölümüne** gidin.

3. Kimlik avı **önleme sayfasında +** **Oluştur'a tıklayın**. Kimlik avına karşı koruma ilkenizi tanımlamanız için size yol belirleyen bir sihirbaz başlatır.

4. İlkenizin adını, açıklamasını ve ayarlarını aşağıdaki tabloda önerilen şekilde belirtin. Daha fazla ayrıntı için bkz[. Kimlik avı önleme seçenekleri için Microsoft Defender'da kimlik Office 365 öğrenin](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Ayarlarınızı gözden geçirmenizin ardından, Uygun şekilde Bu **ilkeyi oluştur'a veya** **Kaydet'e** tıklayın.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Etki alanı ve en değerli kampanya personeli|
|Açıklama|En önemli personelin ve etki alanımızın kimliğine bürünülmemelerini sağlar.|
|Korumak için kullanıcı ekleme|+ **Koşul ekle'yi seçin; Alıcı:** Kullanıcı adlarını yazın veya aday, kampanya yöneticisi ve diğer önemli personel üyelerinin e-posta adresini girin. Kimliğe bürünmelerden korumak istediğiniz en çok 20 iç ve dış adres ebilirsiniz.|
|Korumak için etki alanı ekleme|+ **Koşul ekle'yi seçin; Alıcı etki alanı:** Tanımladıysanız, Microsoft 365 aboneliğiniz ile ilişkili özel etki alanını girin. Birden çok etki alanı girebilirsiniz.|
|Eylemleri seçme|E-posta kimliğine bürünülen bir kullanıcı tarafından gönderilirse: İletiyi başka bir e-posta adresine yeniden yönlendir'i seçin ve sonra güvenlik yöneticisinin e-posta adresini yazın; örneğin, *Ali<span><span>@contoso.com*. E-posta kimliğine bürünülen bir etki alanı tarafından gönderilirse: İletiyi **karantinaya alın'ı seçin**.|
|Posta kutusu zekası|Yeni bir kimlik avı önleme ilkesi  oluşturmak, posta kutusu zekası varsayılan olarak seçilidir. En iyi sonuçları elde **etmek için bu** ayarı Açık bırakın.|
|Güvenilen gönderenleri ve etki alanlarını ekleme|Buradan kendi etki alanlarınızı veya diğer güvenilen etki alanlarınızı  eklemeye devam edersiniz.|
|Uygulamanın uygulandığı yer|Alıcı **etki alanı' seçin**. Bu **seçeneklerden herhangi biri altında** Seç'i **seçin**. **+ Ekle'yi seçin**. Etki alanı adının yanındaki onay kutusunu işaretleyin; örneğin, *contoso.<span><span> com'a* tıklayın ve ardından Ekle'yi **seçin**. **Bitti'yi seçin**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>İzle: Dosya Ekleriyle kötü amaçlı eklere ve dosyalara Kasa koruma

Kişiler belge, sunu, elektronik tablo gibi ekleri düzenli aralıklarla gönderir, alır ve paylaşır. Yalnızca bir e-posta iletisine bakarak eklerin güvenli mi yoksa kötü amaçlı mı olduğunu söylemek her zaman kolay değildir. Office 365 için Microsoft Defender (eski adı Microsoft 365 ATP veya Gelişmiş Tehdit Koruması) Kasa Ek koruması içerir, ancak bu koruma varsayılan olarak açık değildir. Bu korumayı kullanmaya başlamak için yeni bir kural oluşturmanızı öneririz. Bu koruma dosya ve klasörlerin SharePoint, OneDrive ve Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Yönetim merkezine [gidin ve Kurulum'u](https://admin.microsoft.com) **seçin**.
1. Ekranı aşağı kaydırarak Gelişmiş **tehditlere karşı artırılabilir koruma'ya kaydırın**. Görünüm **,** Yönet **ve ardından** **ATP güvenli ekler'i seçin**.
1. Güvenli ekler kuralınızı seçin ve sonra da Düzenle **simgesini** seçin.
1. **Ayarlar'ı** seçin ve engelle'nin seçili olduğunu doğrulayın.
1. Aşağı kaydırın. Yeniden **yönlendirmeyi** etkinleştir'i seçin ve e-posta adresinizi veya engellenen ekleri gözden geçirmek istediğiniz kişinin adresini girin.
1. **Uygulanıyor seçeneğini** ve ardından etki alanı adınızı seçin.
1. Kuralın uygulanmasını istediğiniz diğer etki alanlarını (onmicrosoft.com etki alanınız gibi) seçin. **Ekle'yi** ve ardından Tamam'ı **seçin**.
1. **Kaydet**'i seçin.

ATP güvenli ekler kuralınız güncelleştirildi. Artık koruma yerine geldi ve Outlook, OneDrive, SharePoint veya Teams'den kötü amaçlı dosyaları aça Teams. Etkilenen dosyaların yanında kırmızı kalkanlar olur. Birisi engellenen bir dosyayı açmaya çalışırsa, bir uyarı iletisi alır.

İlkeniz bir süre bulunduktan sonra, nelerin taranmış olduğunu görmek için Raporlar sayfasını ziyaret edin.

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
|Eki algılamada yeniden yönlendirme|Yeniden yönlendirmeyi etkinleştir (bu kutuyu seçin) Yönetici hesabını veya karantina için posta kutusu kurulumunu girin.          Kötü amaçlı yazılım ekleri tarayanın zaman dışında veya hata oluştuğunda yukarıdaki seçimi uygula (bu kutuyu seçin).|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

Daha fazla bilgi için bkz[. Kimlik avı önleme ilkeleri için Microsoft Defender'da kimlik Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-phishing-attacks-with-safe-links"></a>Yeni Bağlantılar ile kimlik avı saldırılarına Kasa koruyun

Bilgisayar korsanları bazen e-posta veya diğer dosyalarda bağlantılarda kötü amaçlı web sitelerini gizler. Kasa için Microsoft Defender'ın bir parçası olan Office 365 Bağlantıları, e-posta iletilerinde ve belgelerinde web adreslerinin (URL)'lerde tıklamalı doğrulama sağlayarak, Office yardımcı olabilir. Koruma, Bağlantı ilkeleri Kasa tanımlanır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Office 365 için Microsoft Defender (eski adı Microsoft 365 ATP veya Gelişmiş Tehdit Koruması) kişiler Office uygulamaları bağlantıları tıklayana kadar kötü amaçlı sitelere karşı korunmanıza yardımcı olur.

1. Yönetim merkezine [gidin ve Kurulum'u](https://admin.microsoft.com) **seçin**.

1. Ekranı aşağı kaydırarak Gelişmiş **tehditlere karşı artırılabilir koruma'ya kaydırın**. **Yönet'i** ve ardından **Bağlantılar'Kasa seçin**.

1. Genel **Ayarlar'yi** **seçin ve Aşağıdaki URL'leri** engelle alanına engellemek istediğiniz URL'yi girin.

Şunları yapmanizi öneririz:

- Korumayı artırmak için varsayılan ilkeyi değiştirme.

- Etki alanınız içinde yer alan tüm alıcılara hedeflenen yeni bir ilke ekleyin.

Bağlantılar'Kasa ayarlamak için aşağıdaki adımları tamamlayın:

1. Yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin ve yönetici hesabınızla oturum açın.

2. o to **Email & İşbirliği İlkeleri** \> **ve & kuralları İlkeler** \> bölümünde Tehdit **ilkeleri** \> Kötü amaçlı **yazılımdan koruma** **ilkeleri.**

3. Yeni **bir ilke oluşturmak** veya varsayılan ilkeyi değiştirmek için + Oluştur'a seçin.

Varsayılan ilkeyi değiştirmek için:

1. Varsayılan ilkeye **çift** tıklayın. Bir açılır çıktı görüntülenir. 

2. Çıkış **öğesinin alt** kısmında Koruma ayarlarını düzenle'yi seçin.

3. Varsayılan ilkeyi değiştirdikten sonra Kaydet'i **seçin**.

|Ayar veya seçenek|Önerilen ayar|
|---|---|
|Name|Kasa etki alanındaki tüm alıcılar için bağlantı ilkesi ekleme|
|İletilerde kötü amaçlı olabilecek bilinmeyen URL'lerin eylemlerini seçme|**Açık'ı seçin: KULLANıCı bağlantıya tıkladığında**, URL'ler yeniden yazılır ve bilinen kötü amaçlı bağlantılar listesinde denetlenir.|
|İndirilebilir Kasa taramak için Ekleri Kullanma|Bu kutuyu seçin.|
|Uygulamanın uygulandığı yer|Alıcı etki alanı: . . . etki alanınızı seçin.|

Daha fazla bilgi için Bkz. [Kasa.](../../security/office-365-security/safe-links.md)

## <a name="go-to-intune-admin-center"></a>Intune yönetim merkezine gitme

1. [Azure portalda oturum açın](https://portal.azure.com/).

2. Tüm **hizmetler'i** seçin ve *Arama Kutusuna Intune* **yazın**.

3. Sonuçlar görüntüden sonra, daha sonra kolayca **bulmak için Microsoft Intune** yanındaki başlangıç öğesini seçin.

Yönetim merkezine ek olarak, Intune'u kullanarak kuruluşun cihazlarını kaydolarak yönetebilirsiniz. Daha fazla bilgi için bkz[. Farklı cihazlar için kayıt Windows özellikleri](/intune/enrollment/enrollment-method-capab) ve [Intune tarafından yönetilen cihazlar için Kayıt seçenekleri](/intune/enrollment-options).
