---
title: Yeni özellikleri Microsoft Tehdit Uzmanları ve yönetme
ms.reviewer: ''
description: Günlük güvenlik işlemlerinizi ve güvenlik yönetimi işlerinizi yapılandırmak, yönetmek ve kullanmak için Microsoft Tehdit Uzmanlarına kaydolma.
keywords: Microsoft Tehdit Uzmanları tehdit arama hizmeti, MTE, Microsoft tarafından yönetilen arama hizmeti
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f6e1bd4653318897ec82d49cd1dccfc0ab4105de
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2022
ms.locfileid: "63010820"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>Yeni özellikleri Microsoft Tehdit Uzmanları ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>Başlamadan önce

> [!NOTE]
> Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimi yönetilen tehdit avı hizmetine başvurmadan önce Microsoft Teknik Servis sağlayıcınız ve hesap ekibi ile uygunluk gereksinimlerini tartışın.

Yalnızca bir laboratuvar ayarlaması için değil, kayıtlı cihazlarla ortamınıza Uç Nokta için Defender'ın dağıtıldığından emin olun.

Uç nokta için Defender müşterisiysiniz, en kritik tehditleri belirlemeye yardımcı olmak için **Microsoft Tehdit Uzmanları -** Hedefli Saldırı Bildirimleri'ne başvurarak en kritik tehditleri hızla yanıt verebilirsiniz. **Microsoft Tehdit Uzmanları -** Talep Uzmanlarına abone olmak için hesap ekibinize veya Microsoft temsilcisine başvurarak ilgili algılamalar ve destek uzmanlarımız ile iletişime geçin.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Uygulama Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri hizmeti

Zaten uç nokta için Defender müşterisiysiniz, Microsoft 365 Defender portalı üzerinden Microsoft 365 Defender.

1. Gezinti bölmesinde Genel 'i ve **Ayarlar > Gelişmiş > - > Microsoft Tehdit Uzmanları Saldırı Bildirimleri'ne gidin**.

2. **Uygula**'ya tıklayın.

    ![Resim Microsoft Tehdit Uzmanları.](images/mte-collaboratewithmte.png)

3. Microsoft'un size uygulamanıza geri dönesin için, adını ve e-posta adresinizi girin.

    ![Uygulamanın Microsoft Tehdit Uzmanları.](images/mte-apply.png)

4. Gizlilik [bildirimini okuyun](https://privacy.microsoft.com/privacystatement) ve **bitirinca** Gönder'e tıklayın. Başvurunız onaylandıktan sonra bir hoş geldiniz e-postası alırsınız.

    ![Uygulama Microsoft Tehdit Uzmanları resmi.](images/mte-applicationconfirmation.png)

Kabul edilirken bir hoş geldiniz e-postası alırsınız ve **Uygula düğmesinin** "açık" olan bir geçiş düğmesine değiştir değiştirmesini alırsınız. Kendinizi Hedefli Saldırı Bildirimleri hizmetten almak istemeniz durumunda, iki durumlu düğmeyi "kapalı" kaydırın ve sayfanın altındaki Kaydetme tercihleri'ne tıklayın.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Buradan, hedefli saldırı bildirimlerini göreceğiniz Microsoft Tehdit Uzmanları

Hedefli saldırı bildirimini şu Microsoft Tehdit Uzmanları üzerinden alırsınız:

- Uç Nokta portalının **Olayları için** Defender sayfası
- Uç nokta portalının Uyarılar panosu **için** Defender
- OData uyarı [API'si](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) ve [REST API'si](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Gelişmiş avda DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) tablosu
- E-postanızı yapılandırmayı seçerseniz

Hedefli saldırı bildirimlerini e-posta aracılığıyla almak için bir e-posta bildirim kuralı oluşturun.

### <a name="create-an-email-notification-rule"></a>E-posta bildirim kuralı oluşturma

Bildirim alıcıları için e-posta bildirimleri göndermek için kurallar oluşturabilirsiniz. Ayrıntılar  [için bkz. E-posta](configure-email-notifications.md) bildirimi oluşturmak, düzenlemek, silmek veya sorunlarını gidermek için uyarı bildirimlerini yapılandırma.

## <a name="view-the-targeted-attack-notification"></a>Hedefli saldırı bildirimini görüntüleme

Sisteminizi e-posta bildirimi alacak şekilde yapılandırdıktan Microsoft Tehdit Uzmanları e-postanıza hedefli saldırı bildirimi almaya başlarsınız.

1. Tehdit uzmanlarıyla etiketlenen panoda ilgili uyarı bağlamına gitmek için e-postada bağlantıya **tıklayın**.

2. Ayrıntıları görüntülemek için panodan e-postadan size gelen uyarı konusunu seçin.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Microsoft Tehdit Uzmanları - Talep Üzerine Uzmanlara Abone Olma

Bu, abonelik hizmeti olarak kullanılabilir. Zaten bir Uç Nokta için Defender müşterisiysiniz, microsoft temsilcinize başvurarak Microsoft Tehdit Uzmanları Uzmanla iletişime geçebilirsiniz.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Bir Microsoft tehdit uzmanına, organizasyonlu şüpheli siber güvenlik etkinlikleri hakkında danışma

Zamanında ve doğru Microsoft Tehdit Uzmanları yanıt için doğrudan web sitesi Microsoft 365 Defender kullanıcı Microsoft 365 Defender iş ortağıyla ortak çalışmanız mümkün. Uzmanlar karmaşık tehditleri, size gelen hedefli saldırı bildirimlerini daha iyi anlamak için içgörüler sağlar veya portal panoda gördüğünüz uyarılar, güvenliği tehlikeye atılmış olabilecek bir cihaz veya tehdit İstihbaratı bağlamı hakkında daha fazla bilgiye ihtiyacınız varsa.

> [!NOTE]
>
> - Kuruluşun özelleştirilmiş tehdit zekası verileriyle ilgili uyarı sorguları şu anda desteklenmiyor. Ayrıntılar için güvenlik işlemlerinize veya olay müdahale ekibine danışın.
> - "Bir tehdit **uzmanına başvur**" sorgus Microsoft 365 Defender için Güvenlik ayarlarını yönetme iznine sahip olmak gerekir.

1. Portal sayfasında olay sayfası gibi araştırma yapmak istediğiniz ilgili bilgileri **bulun** . Araştırma isteği göndermeden önce ilgili uyarı veya cihazın sayfasının görüntüde olduğundan emin olun.

2. Sağ üstteki menüde? simgesini seçin. Ardından, Tehdit **uzmanına başvur'ı seçin**.

    ![Menüden Microsoft Tehdit Uzmanları Uzmanlara Özel'in görüntüsü.](images/mte-eod-menu.png)

    Açılır ekran açılır. Aşağıdaki ekran, bir deneme aboneliği için ne zaman olduğunu gösterir.

    ![Uzmanlardan Microsoft Tehdit Uzmanları görüntüsü.](images/mte-eod.png)

    Tam kullanıcı - Uzman isteğe bağlı Microsoft Tehdit Uzmanları aşağıdaki ekran size gösterilir.

    ![Uzmanlardan Microsoft Tehdit Uzmanları tam abonelik ekranı görüntüsü.](images/mte-eod-fullsubscription.png)

    Sorgulama **konu** alanı, araştırma isteğinize ilişkin ilgili sayfanın bağlantısıyla önceden doldurulur. Örneğin, isteği hazırlarken olay, uyarı veya cihaz ayrıntıları sayfasının bağlantısı.

3. Sonraki alanda, ilgili kullanıcıya araştırmayı başlatmak için Microsoft Tehdit Uzmanları yeterli bağlamı sağlayacak kadar bilgi girin.

4. Bu adresle karşılık gelen e-posta adresini Microsoft Tehdit Uzmanları.

> [!NOTE]
> Microsoft Hizmetleri Merkezi aracılığıyla Talep Üzerine Uzman servis taleplerinizin durumunu izlemek için Müşteri Başarısı Hesap Yöneticinize iletişime geçebilirsiniz.

Microsoft Hizmetleri Merkezi'ne hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>Uzmanla birlikte başvurabilirsiniz örnek soruşturma Microsoft Tehdit Uzmanları - Talep Üzerine Uzmanlar

### <a name="alert-information"></a>Uyarı bilgileri

- Karadan canlı ikili için yeni bir uyarı türü görüyoruz: [UyarıKimlik]. Bu uyarı hakkında bize daha fazla bilgi ve nasıl daha fazla araştırmamız olduğunu söyler misiniz?
- Kötü amaçlı PowerShell betiklerini yürütmeye çalışarak farklı uyarılar oluşturan iki benzer saldırı gözlemlediriz. Bunlardan biri "Suspicious PowerShell komut satırı", diğeri "O365 tarafından sağlanan göstergeye göre kötü amaçlı bir dosya algılandı" olur. Fark nedir?
- Bugün yüksek profilli bir kullanıcının cihazında olağandışı sayıda başarısız oturum açma için tek uyarı almak istiyorum. Bu oturum açma girişimleriyle ilgili başka kanıt bulamıyorum. Uç Nokta için Defender bu denemeleri nasıl görebilir? Hangi tür oturumlar izleniyor?
- Bu uyarıyla ilgili daha fazla bağlam veya öngörüler verebilirsiniz: "Sistem yardımcı programı tarafından şüpheli davranış gözlemlendi".

### <a name="possible-machine-compromise"></a>Olası makine güvenliği

- "Bilinmeyen süreç gözlemlendi?" sorusunu neden gördüğünüze yanıt vermede yardımcı olabilir misiniz? Bu ileti veya uyarı birçok cihazda sık sık görülür. Bu ileti veya uyarının kötü amaçlı etkinliklerle ilgili olup olmadığını netleştirmek için yapılan tüm girdiler bizim için çok teşekkür ederiz.
- [ay] içinde aynı sistem üzerinde önceki [kötü amaçlı yazılım adı] kötü amaçlı yazılım algılamaya benzer davranışlara sahip [tarih] üzerinde aşağıdaki sistem üzerinde olası ödünleri doğrulamaya yardımcı olabilir misiniz?

### <a name="threat-intelligence-details"></a>Tehdit İstihbaratı ayrıntıları

- Kullanıcıya kötü amaçlı bir Word belgesi teslim edilen bir kimlik avı e-postası algıladık. Kötü amaçlı Word belgesi, [kötü amaçlı yazılım] kötü amaçlı yazılım için uç nokta uyarıları için birden çok Defender'ı tetikleyen bir dizi şüpheli olaya neden oldu. Bu kötü amaçlı yazılım hakkında herhangi bir bilginiz var mı? Evet ise, bana bağlantı gönderebilir misiniz?
- Yakın zamanda sektörüm için hedef alan bir tehditle ilgili bir [örneğin, Twitter veya blog] gönderisi gördüm. Uç nokta için Defender'ın bu tehditlere karşı hangi korumayı sağladığını anlamama yardımcı olabilir misiniz?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft Tehdit Uzmanları iletişimleri

- Olay müdahale ekibiniz, bize gelen hedefli saldırı bildirimini bizim için ele alı edebilir mi?
- Bu hedefli saldırı bildirimini Microsoft Tehdit Uzmanları. Kendi olay müdahale ekibimiz yok. Şimdi ne yapabiliriz ve olayı nasıl içerebiliriz?
- Bir iş için hedefli saldırı bildirimi Microsoft Tehdit Uzmanları. Olay müdahale ekibimize hangi verileri veriyebilirsiniz?

  > [!NOTE]
  > Microsoft Tehdit Uzmanları bir olay yanıt hizmeti değil, yönetilen bir siber güvenlik arama hizmetidir. Ancak, bir olay yanıtı gerektiren sorunları ele alan kendi olay müdahale ekibiyle etkileşime girişebilirsiniz. Kendi olay müdahale ekibiniz yoksa ve Microsoft'un yardımını istediysiniz, CSS Siber Güvenlik Olayı Yanıt Ekibi'nden (CIRT) etkileşim s belirttiysiniz. Sorgulamanıza yardımcı olmak için bir bilet açabilirler.

## <a name="scenario"></a>Senaryo

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Yönetilen av sorgunuz hakkında bir ilerleme raporu alma

Yanıt Microsoft Tehdit Uzmanları sorguya göre değişir. Aşağıdaki kategorilerden araştırma durumunu iletecek şekilde, iki  gün içinde bir tehdit uzmanı sorgusuna başvurarak ilerleme durumunu size e-postayla iletirler:

- Soruşturmaya devam etmek için daha fazla bilgi gereklidir
- Teknik bağlamı belirlemek için bir dosya veya birkaç dosya örneği gerekir
- İnceleme için daha fazla zaman gerekiyor
- İlk bilgiler araştırmayı sonuçlandıracak kadar yeterli değildi

Araştırmanın hareketli ilerlemesi için hızlı bir şekilde yanıt vermek çok önemlidir.

## <a name="related-topic"></a>İlgili konu

- [Microsoft Tehdit Uzmanları genel bakış](microsoft-threat-experts.md)
- [Microsoft Tehdit Uzmanları'de Microsoft 365 Genel Bakış](/microsoft-365/security/mtp/microsoft-threat-experts)
