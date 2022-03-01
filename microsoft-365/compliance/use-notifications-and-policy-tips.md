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
description: Bir kullanıcıya DLP ilkesiyle çakışan içerikle çalıştığını bildirmek için, veri kaybı önleme (DLP) ilkesine ilke ipucu ekleme hakkında bilgi öğrenin.
ms.openlocfilehash: 793ae9410ff40d989fffa4dfeae457ff0e61e392
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021773"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>DLP ilkeleri için e-posta bildirimleri gönderme ve ilke ipuçlarını gösterme

Farklı bir genelinde hassas bilgileri tanımlamak, izlemek ve korumak için veri kaybı önleme (DLP) Office 365. Kuruluşta bu hassas bilgilerle çalışan kişilerin DLP ilkelerinize uyumlu kalmasını istiyor, ancak onların çalışmalarınızı gereksiz yere yapmalarını engellemek istemiyoruz. Bu noktada e-posta bildirimleri ve ilke ipuçları yardımcı olabilir.

![İleti çubuğu, posta çubuğunda ilke ipucu Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Uyumluluk Merkezi'nde bir DLP ilkesi seniz, kullanıcı bildirimlerini şu şekilde yapılandırarak:

- Seçtiğiniz kişilerin sorunu açıklayan bir e-posta bildirimi gönderin.

- DLP ilkesiyle çakışan içerik için bir ilke ipucu görüntüleme:

  - Web üzerinde Outlook Outlook 2013 ve sonraki adreslerde e-posta için, ilke ipucu ileti iletiyi oluşturmakta olan iletinin üst kısmında alıcıların üstünde görünür.

  - OneDrive İş hesabı veya SharePoint Online sitesinde bulunan belgeler için, ilke ipucu öğede görünen bir uyarı simgesiyle gösterilir. Daha fazla bilgi görüntülemek için bir öğeyi seçebilir ve ardından Bilgi Bilgileri bölmesi **simgesi** ![öğesini seçebilirsiniz.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) sayfanın sağ üst köşesinde ayrıntılar bölmesini açın.

  - DLP ilkesine Excel bir OneDrive İş sitesinde veya SharePoint Online sitesinde depolanan Excel, PowerPoint ve Word belgeleri için, ilke ipucu İleti Çubuğu'nda ve Backstage **görünümünde (** \> Dosya menüsü Bilgileri) **görünür.**

## <a name="add-user-notifications-to-a-dlp-policy"></a>DLP ilkesine kullanıcı bildirimleri ekleme

Bir DLP ilkesi oluşturmak için Kullanıcı **bildirimlerini etkinleştirin**. Kullanıcı bildirimleri etkinleştirildiğinde, Kullanıcı Microsoft 365 hem e-posta bildirimlerini hem de ilke ipuçlarını gönderir. Bildirim e-postalarını gönderen kişiye, e-posta metnini ve ilke ipucu metnini özelleştirebilirsiniz.

1. [https://(](https://compliance.microsoft.com/permissionshttps://()https://compliance.microsoft.com/permissions) https://.

2. İş veya okul hesabınızla oturum açın. Artık Güvenlik Uyumluluk Merkezi'ndesiniz &amp; .

3. Güvenlik Uyumluluk Merkezi'nde &amp; sol \> gezinti Veri **kaybı** \> önleme \> **İlkesi** \> **+ İlke oluşturma**.

    ![İlke oluştur düğmesi.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. Sonraki seçeneğine ihtiyacınız olan hassas bilgi türlerini koruyan DLP ilkesi şablonunu \> **seçin**.

    Boş bir şablonla başlamak için, Özel Özel ilke **Sonraki'yi** \>  \> **seçin**.

5. İlkeyi Sonraki olarak \> **adlayın**.

6. DLP ilkesine korumak istediğiniz konumları seçmek için, aşağıdan birini yapın:

   - Düzen **menüsünde Tüm Office 365** \> **seçin**.

   - Sonraki **için Belirli konumları seçmeme izin ver'i** \> **seçin**.

   Tüm e-posta hesapları veya tüm Exchange hesapları gibi bir konumun tamamını dahil etmek veya dışarıda OneDrive için, söz konusu konumun durumunu açın veya kapatın.

   Yalnızca belirli siteleri veya SharePoint hesapları dahil etmek OneDrive için Durum'u açık olarak değiştirin ve  ardından Belirli siteleri veya hesapları seçmek için Ekle'nin  altındaki bağlantılara tıklayın.

7. Gelişmiş ayarları **kullan İleri'yi** \> **seçin**.

8. **+ Yeni kural'ı seçin**.

9. Kural düzenleyicisinde, Kullanıcı **bildirimleri'nin** altında durumu açın.

    ![Kural düzenleyicisinin kullanıcı bildirimleri bölümü.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Bildirim e-postaları korumasız gönderilir.

## <a name="options-for-configuring-email-notifications"></a>E-posta bildirimlerini yapılandırma seçenekleri

DLP ilkesinde yer alan her kural için şunları s gerekir:

- Bildirimi seçtiğiniz kişiler için gönderin. Bu kişiler içeriğin sahibini, içeriği son değiştiren kişiyi, içeriğin depolandığı sitenin sahibini veya belirli bir kullanıcıyı içerebilir.

- HTML veya belirteçleri kullanarak bildirime dahil edilen metni özelleştirin. Daha fazla bilgi için aşağıdaki bölüme bakın.

> [!NOTE]
>  E-posta bildirimleri yalnızca tek tek alıcılara gönderebilirsiniz; gruplar veya dağıtım listelerine gönderebilirsiniz. Yalnızca yeni içerik e-posta bildirimini tetikler. Var olan içeriğin düzenlenmesi ilke ipuçlarını tetikler, ancak e-posta bildirimini tetiklemez.

![E-posta bildirimi seçenekleri.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Varsayılan e-posta bildirimi

Bildirimlerin, yapılan işlemle başlayan bir Konu satırı vardır. Örneğin, "Bildirim", e-posta için "İleti Engellendi", belgeler için "Erişim Engellendi". Bildirim bir belgeyle ilgili ise, bildirim ileti gövdesinde belgenin depolandığı siteye bir bağlantı yer alır ve belgenin tüm sorunları çözebilirsiniz ilke ipucu açılır (ilke ipuçlarıyla ilgili aşağıdaki bölüme bakın). Bildirim bir iletiyle ilgili ise, bildirim bir DLP ilkesiyle eşleşen bir ileti eki olarak yer alır.

![Bildirim mesajı.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Varsayılan olarak, bildirimler siteden bir öğe için aşağıdakine benzer bir metin görüntüler. Bildirim metni her kural için ayrı yapılandırıldığından, görüntülenen metin hangi kuralla eşli olduğuna bağlı olarak farklılık gösterir.

|**DLP ilke kuralı bunu yaparsa...**|**Ardından, belgeleriniz veya belgeleriniz SharePoint varsayılan OneDrive İş bunu söylüyor...**|**Ardından, yeni iletiler için Outlook bildirimi bunu söylüyor...**|
|:-----|:-----|:-----|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor.  <br/> |E-posta iletiniz, kuruluşun bir ilkesiyle çakışıyor.  <br/> |
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor. Bu çakışmayı çözemezse, bu dosyaya erişim engellenmiş olabilir.  <br/> |E-posta iletiniz, kuruluşun bir ilkesiyle çakışıyor. İleti tüm alıcılara teslim edilmedi.  <br/> |
|Erişimi engeller ve bildirim gönderir  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor. Bu öğeye erişim sahibi, son değiştirici ve birincil site koleksiyonu yöneticisi dışındaki herkes için engellenir.  <br/> |E-posta iletiniz, kuruluşun bir ilkesiyle çakışıyor. İleti tüm alıcılara teslim edilmedi.  <br/> |

### <a name="custom-email-notification"></a>Özel e-posta bildirimi

Son kullanıcılarınıza veya yöneticilerinize varsayılan e-posta bildirimini göndermek yerine özel bir e-posta bildirimi oluşturabilirsiniz. Özel e-posta bildirimi HTML'yi destekler ve 5.000 karakter sınırlaması vardır. Bildirime resimler, biçimlendirme ve başka markalamalar eklemek için HTML kullanabilirsiniz.

E-posta bildirimini özelleştirmeye yardımcı olmak için aşağıdaki belirteçleri de kullanabilirsiniz. Bu belirteçler, gönderilen bildirimle ilgili belirli bilgilerle değiştirilmiş olan değişkenlerdir.

|**Belirteç**|**Açıklama**|
|:-----|:-----|
|%%AppliedActions%%  <br/> |içeriğe uygulanan eylemler.  <br/> |
|%%ContentURL%%  <br/> |SharePoint Online sitesinde veya OneDrive İş URL'si.  <br/> |
|%%MatchedConditions%%  <br/> |İçerikle eşleşme koşulları. İçerikle ilgili olası sorunlar hakkında bilgi almak için bu belirteci kullanın.  <br/> |

![Belirteçlerin nerede olduğunu gösteren bildirim iletisi.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>İlke ipuçlarını yapılandırma seçenekleri

DLP ilkesinde yer alan her kural için, ilke ipuçlarını şu şekilde yapılandırarak:

- Çakışmayı çözmeye yardımcı olmak için, kişiye içeriğin bir DLP ilkesiyle çakıştılı olduğunu bildirmeniz basit bir yöntemdir. Varsayılan metni kullanabilir (aşağıdaki tablolara bakın) veya kuruluşa özgü ilkeler hakkında özel metin girebilirsiniz.

- Kişinin DLP ilkeyi geçersiz k olmasına izin ver. İsteğe bağlı olarak, şunları da s olabilir:

  - İlkeyi geçersiz kılması için kişinin bir işletme gerekçesi girmesini gerekli kılma. Bu bilgiler günlüğe kaydedilir ve Bu bilgileri Güvenlik Uyumluluk Merkezi'nin **Raporlar bölümündeki** DLP raporlarında &amp; görüntüebilirsiniz.

  - Kişinin hatalı pozitif bir sonuç bildirmesine ve DLP ilkeyi geçersiz k olmasına izin ver. Bu bilgiler aynı zamanda raporlama için de günlüğe kaydedilir, böylece kurallarınıza ince ayar yapmak için hatalı pozitif sonuçlar kullanabilirsiniz.

![İlke ipucu seçenekleri.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Örneğin, kişisel kimliği ortayalayabilecek bilgileri (PII) algılayan OneDrive İş sitelerine uygulanan bir DLP ilkeniz olabilir ve bu ilkenin üç kuralı vardır:

1. İlk kural: Bu hassas bilgilerin beşten az örneği belgede algılanırsa ve belge kuruluş içindeki kişilerle paylaşılıyorsa, Bildirim gönder eylemi ilke ipucu görüntüler. İlke ipuçları için geçersiz kılma seçeneği gerekmez, çünkü bu kural yalnızca kullanıcıları bilgilendirmeyi ve erişimi engellemeyi engellemez.

2. İkinci kural: Bu hassas bilgilerin beşten fazla örneği bir belgede algılanırsa ve belge kuruluş içindeki kullanıcılarla paylaşılırsa, İçerik erişimini engelle eylemi dosyanın izinlerini  kısıtlar ve Bildirim gönder eylemi kişilerin bir işletme gerekçesi sağlayarak bu kuralda  eylemleri geçersiz kılacaklarını sağlar. Kuruluş kuruluşlarının işlerine bazen PII verilerini iç kişilerin paylaşması gerekir ve DLP ilkenizin bu işi engellemelerini istemiyorsunuz.

3. Üçüncü kural: Bu hassas bilgilerin beşten fazla örneği bir belgede algılanırsa ve belge kuruluş dışındaki kullanıcılarla paylaşılıyorsa, İçerik erişimini engelle eylemi dosyanın izinlerini  kısıtlar ve Bildirim gönder eylemi kişilerin bu kuralda eylemleri geçersiz k olmasına izin  vermez çünkü bilgiler dışarıyla paylaşılır. Hiçbir durumda, kuruluş dışındaki kişilerin PII verilerini paylaşmasına izin verilmez.

### <a name="user-override-support"></a>Kullanıcı Geçersiz Kılma desteği

Kuralı geçersiz kılmak için ilke ipucu kullanma hakkında anlamamız gereken bazı ince noktalar şu şekildedir:

- Geçersiz kılma seçeneği her kurala göre geçerli olur ve kuralda bulunan tüm eylemleri geçersiz kılar (bildirim gönderme dışında, geçersiz kılınamaz).

- İçeriğin DLP ilkesinde birden fazla kuralla eşleşmesi mümkündür, ancak yalnızca en kısıtlayıcı, en yüksek öncelikli kuraldan gelen ilke ipucu gösterilir. Örneğin, içeriğe erişimi engelleyen bir kuraldan gelen ilke ipucu, doğrudan bildirim gönderen bir kuraldan gelen bir ilke ipucu üzerinde gösterilir. Bu, kişilerin ilke ipuçları basamaklarını görmelerini önler.

- En kısıtlayıcı kuralda yer alan ilke ipuçları kişilerin kuralı geçersiz k olmasına izin vermiyorsa, bu kuralı geçersiz kılmak da içeriğin eş olduğu diğer tüm kuralları geçersiz kılar.

- NotifyAllowOverride eylemi Yeniden Ayarlamadan veya Yeniden Ayarlamadan veya FlasePositives ile ayarlanmışsa BlockAccess'in doğru olarak ve BlockAccessScope'un uygun değeri olduğundan emin olun. Aksi takdirde ilke ipucu ortaya çıktı ancak kullanıcı e-postayı gerekçeyle geçersiz kacak bir seçenek bulamaz.

#### <a name="availability-of-override"></a>Geçersiz Kılma kullanılabilirliği

|Bildirim Kuralı |Bildir/Engelle eylemi  |Geçersiz kılma kullanılabilir  |Yaslama Gerektir  |
|---------|---------|---------|---------|
|Yalnızca bildir     |Bildir         |Hayır         |Hayır         |
|Notify + AllowOverride     |Bildir         |Hayır         |Hayır         |
|Notify + AllowOverride + Hatalı pozitif     |Bildir         |Hayır         |Hayır         |
|Notify + AllowOverride + Gerekçelendirme ile     |Bildir         |Hayır         |Hayır         |
|Notify + AllowOverride + Yanlış pozitif + Gerekçesiz    |Bildir         |Hayır         |Hayır         |
|Notify + AllowOverride + Yanlış pozitif + Yaslama ile     |Bildir         |Hayır         |Hayır         |
|Bildir + Engelle     |Engelle         |Hayır         |Hayır         |
|Notify + Block + AllowOverride     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + False pozitif     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + Gerekçelendirme ile     |Engelle         |Evet         |Evet         |
|Notify + Block + AllowOverride + False pozitif + Gerekçesiz     |Engelle         |Evet         |Hayır         |
|Notify + Block + AllowOverride + False pozitif + Yaslama ile     |Engelle         |Evet         |Evet         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Sitelere ve OneDrive İş Online sitelerine SharePoint ilke ipuçları

OneDrive İş sitesinde veya SharePoint Online sitesinde bulunan bir belge DLP ilkesine sahip bir kuralla eşleniyorsa ve bu kural ilke ipuçlarını kullanıyorsa, ilke ipuçları belgede özel simgeler görüntüler:

1. Kural dosya hakkında bir bildirim gönderirse uyarı simgesi görüntülenir.

2. Kural belgeye erişimi engellerse, engellenen simge görüntülenir.

   ![Bir hesapta bulunan belgeler üzerinde ilke OneDrive simgeleri.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Belgede işlem yapmak için bir öğe seçerek Bilgi Bilgileri bölmesi \> **simgesini** ![seçebilirsiniz.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) sayfanın sağ üst köşesindeki Ayrıntılar bölmesini açmak için İlke \> **ipucuna bakın**.

İlke ipucu, içerikle ilgili sorunları listeler ve ilke ipuçları bu seçeneklerle yapılandırılmışsa, Çöz'e tıklayın ve ardından İlke ipucunı geçersiz  kıl'a veya Hatalı pozitif sonuç **bildir'e** tıklayın.

![İlke ipucu gösteren Bilgi bölmesi.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Geçersiz kılma seçeneğinin olduğu ilke ipucu.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

DLP ilkeleri sitelere eşitlenen ve içerikli olarak bunlar için düzenli aralıklarla ve zaman uyumsuz olarak değerlendirilir, dolayısıyla DLP ilkesi oluşturma zaman ile ilke ipuçlarını görmeye başlama saat arasında kısa bir gecikme olabilir. İlke ipucu, siteden silinecek olan belge simgesi silinecekse, bu durumla benzer bir gecikme olabilir.

### <a name="default-text-for-policy-tips-on-sites"></a>Sitelerde ilke ipuçları için varsayılan metin

Varsayılan olarak, ilke ipuçları sitede bir öğe için aşağıdakine benzer bir metin görüntüler. Bildirim metni her kural için ayrı yapılandırıldığından, görüntülenen metin hangi kuralla eşli olduğuna bağlı olarak farklılık gösterir.

|**DLP ilke kuralı bunu yaparsa...**|**Ardından varsayılan ilke ipucu bunu söylüyor...**|
|:-----|:-----|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor.  <br/> |
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor. Bu çakışmayı çözemezse, bu dosyaya erişim engellenmiş olabilir.  <br/> |
|Erişimi engeller ve bildirim gönderir  <br/> |Bu öğe, kuruma göre bir ilkeyle çakışıyor. Bu öğeye erişim sahibi, son değiştirici ve birincil site koleksiyonu yöneticisi dışındaki herkes için engellenir.  <br/> |

### <a name="custom-text-for-policy-tips-on-sites"></a>Sitelerde ilke ipuçları için özel metin

İlke ipuçları metnini e-posta bildiriminden ayrı olarak özelleştirebilirsiniz. E-posta bildirimleri için özel metnin aksine (yukarıdaki bölüme bakın), ilke ipuçlarına yönelik özel metin HTML veya belirteçleri kabul etmez. Bunun yerine, ilke ipuçları için özel metin yalnızca 256 karakter sınırı olan düz metindir.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>2013 ve Web üzerinde Outlook Outlook ilke ipuçları

Web üzerinde Outlook ve Outlook 2013 ve sonraki bir9(e-posta) veya daha yeni bir e-posta  oluşturmada, bir DLP ilkesinde yer alan bir kuralla eşleşen içerik eklerseniz ve bu kural ilke ipuçları kullanırsa, bir ilke ipucu alırsınız. İlke ipucu iletinin en üstünde, alıcıların üzerinde görüntülenir ve ileti oluştur alıkolar.

![Bir iletinin üst kısmında İlke ipucu.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

İlke ipuçları, hassas bilgilerin burada gösterildiği gibi ileti gövdesinde, konu satırda, hatta bir ileti eksinde görüntülendiğinde çalışır.

![Bir ekin DLP ilkesiyle çakışıyor olduğunu gösteren ilke ipucu.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

İlke ipuçları geçersiz kılmaya izin verecek şekilde yapılandırılmışsa,  \>  \> Ayrıntıları Geçersiz Kılma Göster'i seçen bir işletme gerekçelendirmesi girin veya geçersiz geçersiz kılma olduğunu **bildirebilirsiniz**\>.

![İletide Geçersiz Kılma seçeneğini gösterecek şekilde genişletilmiş ilke ipucu.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![İlke ipucu geçersiz kılabilirsiniz ilke ipucu iletişim kutusu.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Bir e-postaya hassas bilgiler eklerken, hassas bilgilerin eklendiğinde ve ilke ipucunın göründüğü arasında bir gecikme olabilir.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 ve sonraki türler, yalnızca bazı koşullar için ilke ipuçlarının göstermeyi destekler

Şu anda Outlook 2013 ve sonraki sürümü, yalnızca bu koşullarla ilgili ilke ipuçlarının göstermeyi destekler:

- İçerik içeriği
- İçerik paylaşılıyor

Özel durumlar koşulları kabul edilir ve bu koşulların tümlerinin, Outlook içeriği eşleyecekleri ve içerik üzerinde koruyucu eylemler gerçekleştirecekleri bir yerde çalışır. Ancak kullanıcılara ilke ipuçlarını gösterme henüz desteklenemedi. Ayrıca Outlook, dinamik dağıtım grubuna uygulanan bir DLP ilkesi için ilke ipuçlarının göstermeyi de desteklemez.

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-security-amp-compliance-center"></a>Yönetim merkezinde ilke Exchange ipuçları ve Güvenlik Uyumluluk &amp; Merkezi karşılaştırması

İlke ipuçları, İlke ipuçları, İlke yönetim merkezinde oluşturulmuş D <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> LP ilkeleriyle ve posta akışı kurallarıyla veya Güvenlik Uyumluluk Merkezi'nde oluşturulmuş DLP &amp; ilkeleriyle çalışsa da her ikisi için birden çalışabilirsiniz. Çünkü, bu ilkeler farklı konumlarda depolanır, ancak ilke ipuçları yalnızca tek bir konumdan çizebilirsiniz.

Exchange yönetim merkezinde ilke ipuçlarını yapılandırdıysanız, &amp; Web üzerinde Outlook yönetim merkezinde ipuçlarını kapatana kadar Web üzerinde Outlook ve Outlook 2013 ve sonraki sayfalarındaki kullanıcılara Güvenlik Uyumluluk Merkezi'nde yapılandırılan tüm ilke ipuçları Exchange görünmez. Bu, posta Exchange kuralları olarak da bilinir) geçerli posta akışı kurallarınızı, siz Güvenlik Uyumluluk Merkezi'ne geçmeyi seçene kadar çalışmaya devam &amp; edeceğini sağlar.

İlke ipuçlarının yalnızca tek bir konumdan çizilmesine rağmen, hem Güvenlik Uyumluluk Merkezi'nde hem de Genel Yönetim Merkezinde DLP &amp; ilkeleri kullanıyorsanız bile e-posta bildirimlerinin her Exchange gönderilir.

### <a name="default-text-for-policy-tips-in-email"></a>E-postada ilke ipuçları için varsayılan metin

Varsayılan olarak, ilke ipuçları e-postada aşağıdakine benzer bir metin görüntüler.

|**DLP ilke kuralı bunu yaparsa...**|**Ardından varsayılan ilke ipucu bunu söylüyor...**|
|:-----|:-----|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez  <br/> |E-postanız, kuruma göre bir ilkeyle çakışıyor.  <br/> |
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir  <br/> |E-postanız, kuruma göre bir ilkeyle çakışıyor.  <br/> |
|Erişimi engeller ve bildirim gönderir  <br/> |E-postanız, kuruma göre bir ilkeyle çakışıyor.  <br/> |

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Excel, PowerPoint ve Word'de ilke ipuçları

Kişiler Excel, PowerPoint ve Word'in masaüstü sürümlerinde hassas içerikle birlikte çalışıyorsa, ilke ipuçları onlara içeriğin DLP ilkesiyle çakışıyor olduğu konusunda gerçek zamanlı olarak bildirim sağlar. Bunun için:

- En Office belge OneDrive İş Online sitesinde SharePoint depolanır.

- Site, ilke ipuçlarını kullanmak üzere yapılandırılmış bir DLP ilkesinde yer almaktadır.

Office masaüstü programları DLP ilkelerini doğrudan Office 365'den otomatik olarak eşitler ve DLP ilkeleriyle çakışmamalarını sağlamak ve ilke ipuçlarını gerçek zamanlı olarak görüntülemek için belgelerinizi tarayın.

> [!NOTE]
> Office masaüstü uygulamaları, DLP ilkesi ipuçlarının göster gidip gösterilmeyeceklerini belirlemek için belgeleri tarar; SharePoint Online sitelerinin veya OneDrive İş sitelerinin zaten belirlediği ilke ipuçlarını bir dosyada gösterecektir. Sonuç olarak, SharePoint Online sitelerinde veya OneDrive İş sitelerinde gördüğünüz masaüstü uygulamalarına her zaman bir DLP ilkesi ipucu OneDrive İş alabilirsiniz. Buna karşılık, web'Office uygulamaları yalnızca SharePoint Online siteleri veya OneDrive İş sitelerinin zaten belirlediği DLP ilkesi ipuçlarını gösterir.

DLP ilkesinde ilke ipuçlarını nasıl yapılandırdınıza bağlı olarak, kişiler yalnızca ilke ipucunun yoksaymalarını, iş gerekçeleriyle veya bu ilkeyi geçersiz kılmadan geçersiz k kullanmayı ya da hatalı pozitif sonuçlar bildirmeyi seçebilirler.

İlke ipuçları İleti Çubuğu'ta görünür.

![İleti çubuğu, posta iletisinde ilke Excel 2016.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

İlke ipuçları da Backstage görünümünde (Dosya sekmesinde **)** görünür.

![Backstage görünümünde ilke ipucu Excel 2016.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

DLP ilkesinde ilke ipuçları bu seçeneklerle yapılandırılmışsa, İlke ipucuyu Geçersiz Kılmak  için Çöz'i veya Hatalı **pozitif sonuç** bildir'i seçebilirsiniz.

![Backstage görünümündeki ilke ipucu seçenekleri Excel 2016.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

Bu masaüstü programlarının Office, kişiler ilke ipuçlarını kapatmayı seçebilir. Devre dışı ise, basit bildirim olan ilke ipuçları İleti Çubuğu'nda veya Backstage görünümünde (Dosya sekmesinde) **görünmez** . Bununla birlikte, engelleme ve geçersiz kılma ile ilgili ilke ipuçları yine görünür ve e-posta bildirimini almaya devam ediyor. Buna ek olarak, ilke ipuçlarının kapatması, belgeye uygulanmış olan herhangi bir DLP ilkesinden muaf olmaz.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>E-posta, PowerPoint 2016 ve Excel 2016 ilke ipuçları için varsayılan Word 2016

Varsayılan olarak, ilke ipuçları metni açık bir belgenin İleti Çubuğu'nda ve Backstage görünümünde aşağıdakine benzer şekilde görüntüler. Bildirim metni her kural için ayrı yapılandırıldığından, görüntülenen metin hangi kuralla eşli olduğuna bağlı olarak farklılık gösterir.

|**DLP ilke kuralı bunu yaparsa...**|**Ardından varsayılan ilke ipucu bunu söylüyor...**|
|:-----|:-----|
|Bildirim gönderir ancak geçersiz kılmaya izin vermez  <br/> |Bu dosya, kuruma göre bir ilkeyle çakışır. Daha fazla bilgi **için** Dosya menüsüne gidin.  <br/> |
|Erişimi engeller, bildirim gönderir ve geçersiz kılmaya izin verir  <br/> |Bu dosya, kuruma göre bir ilkeyle çakışır. Bu çakışmayı çözemezse, bu dosyaya erişim engellenmiş olabilir. Daha fazla bilgi **için** Dosya menüsüne gidin.  <br/> |
|Erişimi engeller ve bildirim gönderir  <br/> |Bu dosya, kuruma göre bir ilkeyle çakışır. Bu çakışmayı çözemezse, bu dosyaya erişim engellenmiş olabilir. Daha fazla bilgi **için** Dosya menüsüne gidin.  <br/> |

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Word, Excel ve Word'de ilke ipuçları PowerPoint özel metin

İlke ipuçları metnini e-posta bildiriminden ayrı olarak özelleştirebilirsiniz. E-posta bildirimleri için özel metnin aksine (yukarıdaki bölüme bakın), ilke ipuçlarına yönelik özel metin HTML veya belirteçleri kabul etmez. Bunun yerine, ilke ipuçları için özel metin yalnızca 256 karakter sınırı olan düz metindir.

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [DLP ilkesi koşulları, özel durumlar ve eylemler (önizleme)](./dlp-microsoft-teams.md)
- [Belgeleri FCI veya diğer özelliklerle korumak için DLP ilkesi oluşturma](protect-documents-that-have-fci-or-other-properties.md)
- [DLP ilkesi şablonlarının şunları içermesi](what-the-dlp-policy-templates-include.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
