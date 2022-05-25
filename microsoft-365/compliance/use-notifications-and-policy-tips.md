---
title: DLP ilkeleri için e-posta bildirimleri gönderme ve ilke ipuçlarını gösterme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleNotifyUser
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Bir kullanıcıya DLP ilkesiyle çakişen içerikle çalıştığını bildirmek için veri kaybı önleme (DLP) ilkesine ilke ipucu eklemeyi öğrenin.
ms.openlocfilehash: af3dd2181c5bd8865f02755ba4d17f1feb0514d2
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669550"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>DLP ilkeleri için e-posta bildirimleri gönderme ve ilke ipuçlarını gösterme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Office 365 genelinde hassas bilgileri tanımlamak, izlemek ve korumak için Microsoft Purview veri kaybı önleme (DLP) ilkesi kullanabilirsiniz. Kuruluşunuzda bu hassas bilgilerle çalışan kişilerin DLP ilkelerinizle uyumlu kalmasını istiyorsunuz, ancak işlerini yapmalarını gereksiz yere engellemek istemiyorsunuz. Burada e-posta bildirimleri ve ilke ipuçları yardımcı olabilir.

![İleti çubuğu, Excel 2016 ilke ipucunu gösterir](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

DLP ilkesi oluşturduğunuzda, kullanıcı bildirimlerini şu şekilde yapılandırabilirsiniz:

- Seçtiğiniz kişilere sorunu açıklayan bir e-posta bildirimi gönderin.

- DLP ilkesiyle çakişen içerik için bir ilke ipucu görüntüleyin:

  - Web üzerinde Outlook ve Outlook 2013 ve sonraki sürümlerdeki e-postalar için, ileti oluşturulurken, ilke ipucu alıcıların üstündeki iletinin üst kısmında görünür.

  - OneDrive İş hesabındaki veya çevrimiçi SharePoint sitedeki belgeler için ilke ipucu, öğede görünen bir uyarı simgesiyle gösterilir. Daha fazla bilgi görüntülemek için bir öğeyi ve ardından **Bilgi** ![Bilgileri bölmesi simgesini seçebilirsiniz.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) ayrıntılar bölmesini açmak için sayfanın sağ üst köşesinde.

  - Excel, PowerPoint ve DLP ilkesine dahil edilen bir OneDrive İş sitede veya SharePoint Online sitesinde depolanan Word belgeleri için, ilke ipucu İleti Çubuğu'nda ve Backstage görünümünde (**Dosya** menüsü \> **Bilgileri**) görüntülenir.

## <a name="add-user-notifications-to-a-dlp-policy"></a>DLP ilkesine kullanıcı bildirimleri ekleme

DLP ilkesi oluşturduğunuzda **Kullanıcı bildirimlerini** etkinleştirebilirsiniz. Kullanıcı bildirimleri etkinleştirildiğinde Microsoft 365 hem e-posta bildirimlerini hem de ilke ipuçlarını gönderir. Bildirim e-postalarının kime gönderileceğini, e-posta metnini ve ilke ipucu metnini özelleştirebilirsiniz.

1. [https://(](https://compliance.microsoft.com/permissionshttps://()https://compliance.microsoft.com/permissions) öğesine gidin.

2. İş veya okul hesabınızı kullanarak oturum açın.

3. sol \> gezinti Microsoft Purview uyumluluk portalı \> **Veri kaybı önleme** \> **İlkesi** \> **+ İlke oluştur'a tıklayın**.

    ![İlke düğmesi oluşturun.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. **İleri'yi** korumak istediğiniz \> hassas bilgi türlerini koruyan DLP ilke şablonunu seçin.

    Boş bir şablonla başlamak için **Özel Özel** \> **ilke** \> **İleri'yi** seçin.

5. İlkeyi \> **İleri olarak adlandırın**.

6. DLP ilkesinin korumasını istediğiniz konumları seçmek için aşağıdakilerden birini yapın:

   - **sonraki** **Office 365 tüm konumlar'ı** \> seçin.

   - Belirli konumları \> **seçmeme izin ver** **İleri'yi** seçin.

   Tüm Exchange e-posta veya tüm OneDrive hesapları gibi bir konumun tamamını dahil etmek veya hariç tutmak için bu konumun **Durumunu** açın veya kapatın.

   Yalnızca belirli SharePoint siteleri veya OneDrive hesaplarını eklemek için **, Durum'u** açık olarak değiştirin ve **ardından Ekle** altındaki bağlantılara tıklayarak belirli siteleri veya hesapları seçin.

7. **Gelişmiş ayarları** \> kullan **İleri'yi** seçin.

8. **+ Yeni kural'ı** seçin.

9. Kural düzenleyicisinde, **Kullanıcı bildirimleri'nin** altında durumu açın.

    ![Kural düzenleyicisinin kullanıcı bildirimleri bölümü.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Bildirim e-postaları korumasız gönderilir.

## <a name="options-for-configuring-email-notifications"></a>E-posta bildirimlerini yapılandırma seçenekleri

DLP ilkesindeki her kural için şunları yapabilirsiniz:

- Bildirimi seçtiğiniz kişilere gönderin. Bu kişiler içeriğin sahibini, içeriği son değiştiren kişiyi, içeriğin depolandığı sitenin sahibini veya belirli bir kullanıcıyı içerebilir.

- HTML veya belirteçleri kullanarak bildirime dahil edilen metni özelleştirin. Daha fazla bilgi için aşağıdaki bölüme bakın.

> [!NOTE]
>
> - E-posta bildirimleri gruplara veya dağıtım listelerine değil yalnızca tek tek alıcılara gönderilebilir.
> - Yalnızca yeni içerik bir e-posta bildirimi tetikler. Mevcut içeriğin düzenlenmesi ilke ipuçlarını tetikler, ancak e-posta bildirimlerini tetiklemez.
> - Dış gönderenler bildirim almaz. Bildirimler yalnızca iç kullanıcılara gider.

![E-posta bildirim seçenekleri.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Varsayılan e-posta bildirimi

Bildirimlerin, gerçekleştirilen eylemle başlayan bir Konu satırı vardır. Örneğin, e-posta için "Bildirim", "İleti Engellendi" veya belgeler için "Erişim Engellendi" gibi. Bildirim bir belgeyle ilgiliyse, bildirim iletisi gövdesinde sizi belgenin depolandığı siteye götüren ve belgenin ilke ipucunu açan bir bağlantı bulunur; burada tüm sorunları çözebilirsiniz (ilke ipuçları hakkında aşağıdaki bölüme bakın). Bildirim bir iletiyle ilgiliyse bildirim, DLP ilkesiyle eşleşen iletiyi ek olarak içerir.

![Bildirim iletisi.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Varsayılan olarak, bildirimler sitedeki bir öğe için aşağıdakine benzer bir metin görüntüler. Bildirim metni her kural için ayrı ayrı yapılandırıldığından, görüntülenen metin hangi kuralın eşleştirildiğine bağlı olarak değişir.

|DLP ilke kuralı bunu yaparsa...|Ardından, SharePoint veya OneDrive İş belgeler için varsayılan bildirimde bu...|Ardından Outlook iletileri için varsayılan bildirimde şu ifade yer alır:...|
|---|---|---|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer.|E-posta iletiniz kuruluşunuzdaki bir ilkeyle çakişer.|
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer. Bu çakışmayı çözmezseniz, bu dosyaya erişim engellenebilir.|E-posta iletiniz kuruluşunuzdaki bir ilkeyle çakişer. İleti tüm alıcılara teslim edilmedi.|
|Erişimi engeller ve bildirim gönderir|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer. Bu öğeye erişim sahibi, son değiştiricisi ve birincil site koleksiyonu yöneticisi dışında herkes için engellenir.|E-posta iletiniz kuruluşunuzdaki bir ilkeyle çakişer. İleti tüm alıcılara teslim edilmedi.|

### <a name="custom-email-notification"></a>Özel e-posta bildirimi

Varsayılan e-posta bildirimini son kullanıcılarınıza veya yöneticilerinize göndermek yerine özel bir e-posta bildirimi oluşturabilirsiniz. Özel e-posta bildirimi HTML'yi destekler ve 5.000 karakterlik bir sınıra sahiptir. Bildirime resim, biçimlendirme ve diğer markayı eklemek için HTML kullanabilirsiniz.

E-posta bildirimini özelleştirmeye yardımcı olması için aşağıdaki belirteçleri de kullanabilirsiniz. Bu belirteçler, gönderilen bildirimdeki belirli bilgilerle değiştirilen değişkenlerdir.

|Belirte -ci|Açıklama|
|---|---|
|%%AppliedActions%%|İçeriğe uygulanan eylemler.|
|%%ContentURL%%|SharePoint Online sitesindeki veya OneDrive İş sitedeki belgenin URL'si.|
|%%MatchedConditions%%|İçerikle eşleşen koşullar. İçerikle ilgili olası sorunlar hakkında kişileri bilgilendirmek için bu belirteci kullanın.|

![Belirteçlerin nerede göründüğünü gösteren bildirim iletisi.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>İlke ipuçlarını yapılandırma seçenekleri

DLP ilkesindeki her kural için, ilke ipuçlarını şu şekilde yapılandırabilirsiniz:

- İçeriğin bir DLP ilkesiyle çakıştığını kişiye bildirmeniz yeterlidir, böylece çakışmayı çözmek için eyleme geçebilir. Varsayılan metni kullanabilir (aşağıdaki tablolara bakın) veya kuruluşunuzun belirli ilkeleri hakkında özel metin girebilirsiniz.

- Kişinin DLP ilkesini geçersiz kmasına izin verin. İsteğe bağlı olarak şunları yapabilirsiniz:

  - kişinin ilkeyi geçersiz kılması için bir iş gerekçesi girmesini zorunlu kıl. Bu bilgiler günlüğe kaydedilir ve portalın **Raporlar** bölümündeki DLP raporlarında görüntüleyebilirsiniz.

  - Kişinin hatalı pozitif rapor vermesine ve DLP ilkesini geçersiz kmasına izin verin. Bu bilgiler raporlama için de günlüğe kaydedilir, böylece kurallarınızda ince ayar yapmak için hatalı pozitif sonuçları kullanabilirsiniz.

![İlke ipucu seçenekleri.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Örneğin, kişisel bilgileri (PII) algılayan OneDrive İş sitelerine uygulanan bir DLP ilkeniz olabilir ve bu ilkenin üç kuralı vardır:

1. İlk kural: Belgede bu hassas bilgilerin beşten az örneği algılanırsa ve belge kuruluş içindeki kişilerle paylaşılıyorsa, **Bildirim gönder** eylemi bir ilke ipucu görüntüler. İlke ipuçları için hiçbir geçersiz kılma seçeneği gerekli değildir çünkü bu kural yalnızca kişileri bilgilendirir ve erişimi engellemez.

2. İkinci kural: Bir belgede bu hassas bilgilerin beşten fazla örneği algılanırsa ve belge kuruluş içindeki kişilerle paylaşılıyorsa, **İçeriğe erişimi engelle** eylemi dosyanın izinlerini kısıtlar ve **Bildirim gönder** eylemi, kişilerin iş gerekçesi sağlayarak bu kuraldaki eylemleri geçersiz kılmasını sağlar. Kuruluşunuzun işletmesi bazen şirket içindeki kişilerin PII verilerini paylaşmasını gerektirir ve DLP ilkenizin bu çalışmayı engellemesini istemezsiniz.

3. Üçüncü kural: Bir belgede bu hassas bilgilerin beşten fazla örneği algılanırsa ve belge kuruluş dışındaki kişilerle paylaşılıyorsa, **İçeriğe erişimi engelle** eylemi dosyanın izinlerini kısıtlar ve **Bildirim gönder** eylemi, bilgiler dışarıdan paylaşıldığından kişilerin bu kuraldaki eylemleri geçersiz kılmasına izin vermez. Hiçbir koşulda kuruluşunuzdaki kişilerin kuruluş dışında PII verilerini paylaşmasına izin verilmemelidir.

### <a name="user-override-support"></a>Kullanıcı Geçersiz Kılma desteği

Kuralı geçersiz kılmak için ilke ipucu kullanma hakkında anlamanız gereken bazı ince noktalar şunlardır:

- Geçersiz kılma seçeneği kurala göredir ve kuraldaki tüm eylemleri geçersiz kılar (geçersiz kılınamaz bir bildirim gönderme dışında).

- İçeriğin bir DLP ilkesindeki çeşitli kurallarla eşleşmesi mümkündür, ancak yalnızca en kısıtlayıcı, en yüksek öncelikli kuraldan gelen ilke ipucu gösterilir. Örneğin, içeriğe erişimi engelleyen bir kuraldan gelen ilke ipucu, yalnızca bildirim gönderen bir kuraldan gelen ilke ipucu üzerinden gösterilir. Bu, kişilerin ilke ipuçlarının art arda görülmesini önler.

- En kısıtlayıcı kuraldaki ilke ipuçları kişilerin kuralı geçersiz kılmasına izin verirse, bu kuralın geçersiz kılınmış olması, içeriğin eşleştirilen diğer kuralları da geçersiz kılar.

- NotifyAllowOverride eylemi, Justification veya WithJustification veya FlasePositives ile ayarlandıysa, BlockAccess'in true olarak ayarlandığından ve BlockAccessScope'un uygun değere sahip olduğundan emin olun. Aksi takdirde ilke ipucu ortaya çıkar, ancak kullanıcı e-postayı gerekçeyle geçersiz kılma seçeneği bulamaz.

#### <a name="availability-of-override"></a>Geçersiz Kılma Kullanılabilirliği

|Bildirim Kuralı |Bildir/Engelle eylemi  |Geçersiz kılma kullanılabilir  |Gerekçe gerektir  |
|---------|---------|---------|---------|
|Yalnızca bildir     |Bildirmek         |Hayır         |Hayır         |
|Notify + AllowOverride     |Bildirmek         |Hayır         |Hayır         |
|Notify + AllowOverride + False pozitif     |Bildirmek         |Hayır         |Hayır         |
|Notify + AllowOverride + With justification     |Bildirmek         |Hayır         |Hayır         |
|Notify + AllowOverride + False positive + Justification olmadan    |Bildirmek         |Hayır         |Hayır         |
|Notify + AllowOverride + False positive + With justification     |Bildirmek         |Hayır         |Hayır         |
|Bildirim + Engelle     |Engelle         |Hayır         |Hayır         |
|Notify + Block + AllowOverride     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + False pozitif     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + With justification     |Engelle         |Evet         |Evet         |
|Notify + Block + AllowOverride + False positive + Without justification     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + False positive + With justification     |Engelle         |Evet         |Evet         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>OneDrive İş siteleri ve SharePoint Çevrimiçi siteleri ile ilgili ilke ipuçları

OneDrive İş sitedeki veya çevrimiçi SharePoint sitedeki bir belge DLP ilkesindeki bir kuralla eşleştiğinde ve bu kural ilke ipuçlarını kullandığında, ilke ipuçları belgede özel simgeler görüntüler:

1. Kural dosya hakkında bir bildirim gönderirse uyarı simgesi görüntülenir.

2. Kural belgeye erişimi engelliyorsa engellenen simgesi görüntülenir.

   ![OneDrive hesabındaki belgelerde ilke ipucu simgeleri.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Belge üzerinde işlem yapmak için **Bilgi Bilgileri bölmesi** simgesini seçen öğeyi \> seçebilirsiniz![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) ayrıntılar bölmesini \> açmak için sayfanın sağ üst köşesinde **İlke ipucunu görüntüleyin**.

İlke ipucu içerikle ilgili sorunları listeler ve ilke ipuçları bu seçeneklerle yapılandırılmışsa **Çöz'e** ve ardından İlke ipucunu **geçersiz kıl'a** **veya Hatalı** pozitif bildir'e tıklayın.

![İlke ipucunu gösteren Bilgi bölmesi.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Geçersiz kılma seçeneğine sahip ilke ipucu.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

DLP ilkeleri sitelerle eşitlenir ve içerikli ilkeler belirli aralıklarla ve zaman uyumsuz olarak değerlendirilir, bu nedenle DLP ilkesini oluşturduğunuz süre ile ilke ipuçlarını görmeye başlamanız arasında kısa bir gecikme olabilir. İlke ipucunu çözümlediğiniz veya geçersiz kıldığınız zaman, sitedeki belgedeki simgenin ortadan kalkmasına benzer bir gecikme olabilir.

### <a name="default-text-for-policy-tips-on-sites"></a>Sitelerdeki ilke ipuçları için varsayılan metin

Varsayılan olarak, ilke ipuçları sitedeki bir öğe için aşağıdakine benzer bir metin görüntüler. Bildirim metni her kural için ayrı ayrı yapılandırıldığından, görüntülenen metin hangi kuralın eşleştirildiğine bağlı olarak değişir.

|DLP ilke kuralı bunu yaparsa...|Ardından varsayılan ilke ipucu şunu söyler...|
|---|---|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer.|
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer. Bu çakışmayı çözmezseniz, bu dosyaya erişim engellenebilir.|
|Erişimi engeller ve bildirim gönderir|Bu öğe, kuruluşunuzdaki bir ilkeyle çakişer. Bu öğeye erişim sahibi, son değiştiricisi ve birincil site koleksiyonu yöneticisi dışında herkes için engellenir.|

### <a name="custom-text-for-policy-tips-on-sites"></a>Sitelerdeki ilke ipuçları için özel metin

İlke ipuçları metnini e-posta bildiriminden ayrı olarak özelleştirebilirsiniz. E-posta bildirimleri için özel metinden farklı olarak (yukarıdaki bölüme bakın), ilke ipuçları için özel metin HTML veya belirteçleri kabul etmez. Bunun yerine, ilke ipuçları için özel metin yalnızca 256 karakter sınırı olan düz metindir.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Web üzerinde Outlook ve Outlook 2013 ve sonraki sürümlerde ilke ipuçları

Web üzerinde Outlook ve Outlook 2013 ve sonraki sürümlerde yeni bir e-posta oluşturduğunuzda, DLP ilkesindeki bir kuralla eşleşen içerik eklerseniz ve bu kural ilke ipuçlarını kullanırsa bir ilke ipucu görürsünüz. İlke ipucu, ileti oluşturulurken iletinin en üstünde, alıcıların üstünde görünür.

![Oluşturulan iletinin en üstündeki ilke ipucu.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

İlke ipuçları, hassas bilgilerin ileti gövdesinde, konu satırında, hatta ileti ekinde burada gösterildiği gibi görünüp görünmediğini belirler.

![Ekin bir DLP ilkesiyle çakışmasını gösteren ilke ipucu.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

İlke ipuçları geçersiz kılmaya izin verecek şekilde yapılandırıldıysa **, Ayrıntıları** \> Göster **Geçersiz Kılma** \> bir iş gerekçesi girin'i seçebilir veya hatalı pozitif \> **Geçersiz Kılma bildirebilirsiniz**.

![İletideki ilke ipucu Geçersiz Kılma seçeneğini gösterecek şekilde genişletildi.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![İlke ipucu iletişim kutusunda ilke ipucunu geçersiz kılabilirsiniz.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Bir e-postaya hassas bilgiler eklediğinizde, hassas bilgilerin eklenmesiyle ilke ipucunun görünmesi arasında gecikme olabileceğini unutmayın. E-postalar Microsoft Purview İleti Şifrelemesi ile şifrelendiğinde ve bunları algılamak için kullanılan ilke tarafından kullanıldığında şifreleme koşulu algıla ilke ipuçları görünmez.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 ve üzeri, yalnızca bazı koşullar için ilke ipuçlarının gösterilmesini destekler

Şu anda Outlook 2013 ve üzeri sürümler yalnızca şu koşullar için ilke ipuçlarının gösterilmesini destekler:

- İçerik içeriği
- İçerik paylaşılıyor

Özel durumlar koşul olarak kabul edilir ve bu koşulların tümü, içerikle eşleşecekleri ve içerik üzerinde koruyucu eylemler uygulayacakları Outlook çalışır. Ancak kullanıcılara ilke ipuçlarının gösterilmesi henüz desteklenmiyor. Ayrıca Outlook, dinamik dağıtım grubuna uygulanan bir DLP ilkesi için ilke ipuçlarının gösterilmesini desteklemez.

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-microsoft-purview-compliance-portal"></a>Exchange yönetim merkezinde ve Microsoft Purview Uyumluluk portalında ilke ipuçları

İlke ipuçları<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">, Exchange yönetim merkezinde</a> oluşturulan DLP ilkeleri ve posta akışı kurallarıyla veya uyumluluk portalında oluşturulan DLP ilkeleriyle çalışabilir, ancak ikisini birden çalışmaz. Bunun nedeni, bu ilkelerin farklı konumlarda depolanmasıdır, ancak ilke ipuçları yalnızca tek bir konumdan çizim yapabilir.

Exchange yönetim merkezinde ilke ipuçlarını yapılandırdıysanız, uyumluluk portalında yapılandırdığınız ilke ipuçları, Exchange yönetim merkezindeki ipuçlarını kapatana kadar Web üzerinde Outlook ve Outlook 2013 ve sonraki sürümlerde kullanıcılara gösterilmez. Bu, geçerli Exchange posta akışı kurallarınızın (taşıma kuralları olarak da bilinir) uyumluluk portalına geçiş yapmayı seçene kadar çalışmaya devam etmesini sağlar.

İlke ipuçları yalnızca tek bir konumdan çizim yapabilirken, hem uyumluluk portalında hem de Exchange yönetim merkezinde DLP ilkelerini kullanıyor olsanız bile e-posta bildirimlerinin her zaman gönderildiğini unutmayın.

### <a name="default-text-for-policy-tips-in-email"></a>E-postada ilke ipuçları için varsayılan metin

Varsayılan olarak, ilke ipuçları e-posta için aşağıdakine benzer bir metin görüntüler.

|DLP ilke kuralı bunu yaparsa...|Ardından varsayılan ilke ipucu şunu söyler...|
|---|---|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez|E-postanız kuruluşunuzdaki bir ilkeyle çakişer.|
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir|E-postanız kuruluşunuzdaki bir ilkeyle çakişer.|
|Erişimi engeller ve bildirim gönderir|E-postanız kuruluşunuzdaki bir ilkeyle çakişer.|

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Excel, PowerPoint ve Word'de ilke ipuçları

kişiler Excel, PowerPoint ve Word'ün masaüstü sürümlerinde hassas içerikle çalıştığında, ilke ipuçları onlara içeriğin bir DLP ilkesiyle çakışıp çakışmadığını gerçek zamanlı olarak bildirebilir. Bunun için şunlar gerekir:

- Office belgesi OneDrive İş bir sitede veya SharePoint Online sitesinde depolanır.

- Site, ilke ipuçlarını kullanacak şekilde yapılandırılmış bir DLP ilkesine dahil edilir.

Office masaüstü programları DLP ilkelerini doğrudan Office 365'dan otomatik olarak eşitler ve ardından belgelerinizi tarar ve DLP ilkelerinizle çakışmadığından ve ilke ipuçlarını gerçek zamanlı olarak görüntülemediğinden emin olur.

> [!NOTE]
> Office masaüstü uygulamaları, DLP ilke ipuçlarının gösterilip gösterilmeyeceğini belirlemek için belgeleri kendileri tarar; Çevrimiçi sitelerin veya SharePoint OneDrive İş sitelerin zaten belirlediği ilke ipuçlarının bir dosyada gösterilmesi gerektiğini göstermez. Sonuç olarak, SharePoint Çevrimiçi sitelerinde veya OneDrive İş sitelerinde gördüğünüz masaüstü uygulamalarında her zaman bir DLP ilkesi ipucu göremeyebilirsiniz. Buna karşılık, web'deki Office uygulamaları yalnızca çevrimiçi sitelerin veya OneDrive İş sitelerin önceden belirlediği DLP ilkesi ipuçlarının gösterilmesini SharePoint gösterir.

DLP ilkesindeki ilke ipuçlarını nasıl yapılandırdığınıza bağlı olarak, kişiler ilke ipucunu yoksaymayı, ilkeyi iş gerekçesiyle veya gerekçe olmadan geçersiz kılmayı veya hatalı pozitif rapor etmeyi seçebilir.

İlke ipuçları İleti Çubuğu'nda görünür.

![İleti çubuğu, Excel 2016 ilke ipucunu gösterir.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

İlke ipuçları da Backstage görünümünde ( **Dosya** sekmesinde) görünür.

![Backstage, ilke ipucunu Excel 2016 gösterir.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

DLP ilkesindeki ilke ipuçları bu seçeneklerle yapılandırılmışsa **Çözümle'yi** seçerek İlke ipucunu **geçersiz kıl** **veya Hatalı** pozitif raporla seçeneğini belirleyebilirsiniz.

![Excel 2016 Backstage'da ilke ipucu seçenekleri.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

Bu Office masaüstü programlarının her birinde, insanlar ilke ipuçlarını kapatmayı seçebilir. Kapalıysa, basit bildirimler olan ilke ipuçları İleti Çubuğu veya Backstage görünümünde ( **Dosya** sekmesinde) görünmez. Ancak engelleme ve geçersiz kılmayla ilgili ilke ipuçları görünmeye devam eder ve e-posta bildirimini almaya devam eder. Ayrıca, ilke ipuçlarını kapatmak belgeyi uygulanan DLP ilkelerinden muaf tutmaz.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Excel 2016, PowerPoint 2016 ve Word 2016 ilke ipuçları için varsayılan metin

Varsayılan olarak, ilke ipuçları açık bir belgenin İleti Çubuğu ve Backstage görünümünde aşağıdakine benzer bir metin görüntüler. Bildirim metni her kural için ayrı ayrı yapılandırıldığından, görüntülenen metin hangi kuralın eşleştirildiğine bağlı olarak değişir.

|DLP ilke kuralı bunu yaparsa...|Ardından varsayılan ilke ipucu şunu söyler...|
|---|---|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez|Bu dosya kuruluşunuzdaki bir ilkeyle çakişer. Daha fazla bilgi için **Dosya** menüsüne gidin.|
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir|Bu dosya kuruluşunuzdaki bir ilkeyle çakişer. Bu çakışmayı çözmezseniz, bu dosyaya erişim engellenebilir. Daha fazla bilgi için **Dosya** menüsüne gidin.|
|Erişimi engeller ve bildirim gönderir|Bu dosya kuruluşunuzdaki bir ilkeyle çakişer. Bu çakışmayı çözmezseniz, bu dosyaya erişim engellenebilir. Daha fazla bilgi için **Dosya** menüsüne gidin.|

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Excel, PowerPoint ve Word'de ilke ipuçları için özel metin

İlke ipuçları metnini e-posta bildiriminden ayrı olarak özelleştirebilirsiniz. E-posta bildirimleri için özel metinden farklı olarak (yukarıdaki bölüme bakın), ilke ipuçları için özel metin HTML veya belirteçleri kabul etmez. Bunun yerine, ilke ipuçları için özel metin yalnızca 256 karakter sınırı olan düz metindir.

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [DLP ilkesi koşulları, özel durumlar ve eylemler (önizleme)](./dlp-microsoft-teams.md)
- [FCI veya diğer özellikler ile belgeleri korumak için bir DLP ilkesi oluşturma](protect-documents-that-have-fci-or-other-properties.md)
- [DLP ilke şablonları neler içerir?](what-the-dlp-policy-templates-include.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
