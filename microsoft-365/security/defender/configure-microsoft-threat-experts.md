---
title: Microsoft 365 Defender aracılığıyla Microsoft Tehdit Uzmanları özelliklerini yapılandırma ve yönetme
description: Günlük güvenlik operasyonlarınızda ve güvenlik yönetimi çalışmanızda yapılandırmak, yönetmek ve kullanmak için Microsoft 365 Defender aracılığıyla Microsoft Threats Uzmanlarına abone olun.
keywords: Microsoft Tehdit Uzmanları, yönetilen tehdit avcılığı hizmeti, MTE, Microsoft yönetilen tehdit avcılığı hizmeti
search.product: Windows 10
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-maave
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: cd8f7e65c409138d6404a734b098e70e6d419cbb
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667284"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Microsoft 365 Defender aracılığıyla Microsoft Tehdit Uzmanları özelliklerini yapılandırma ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Başlamadan önce

> [!IMPORTANT]
> Başvurmadan önce, Microsoft Tehdit Uzmanları – Hedefli Saldırı Bildirimleri yönetilen tehdit avcılığı hizmeti için uygunluk gereksinimlerini Microsoft Teknik Hizmet sağlayıcınız ve hesap ekibinizle tartıştığınızdan emin olun.

Hedeflenen saldırı bildirimlerini almak için Microsoft 365 Defender kayıtlı cihazlarla dağıtılmış olması gerekir. Ardından, Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri için M365 portalı üzerinden bir uygulama gönderin.

Microsoft Tehdit Uzmanları - İsteğe Bağlı Uzmanlar'a abone olmak için hesap ekibinize veya Microsoft temsilcinize başvurun. İsteğe Bağlı Uzmanlar, kuruluşunuzu ilgili algılamalardan ve saldırganlardan nasıl koruyabileceğiniz konusunda tehdit uzmanlarımıza danışmanızı sağlar.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri hizmeti için başvurun

Zaten Uç Nokta için Microsoft Defender ve Microsoft 365 Defender varsa, Microsoft Tehdit Uzmanları – Hedefli Saldırı Bildirimleri için Microsoft 365 Defender Portal.  Hedeflenen saldırı bildirimleri, kuruluşunuza yönelik en kritik tehditleri belirlemenize yardımcı olacak özel içgörüler ve analizler sağlar, böylece bunlara hızlı bir şekilde yanıt vekleyebilirsiniz.

1. Gezinti bölmesinden **Ayarlar > Uç Noktalar > Genel > Gelişmiş özellikler > Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri'ne** gidin.

2. **Uygula'yı** seçin.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Tehdit Uzmanları ayarları sayfası" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Microsoft'un uygulamanız hakkında sizinle iletişim kurabilmesi için adınızı ve e-posta adresinizi girin.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Tehdit Uzmanları uygulama sayfası" lightbox="../../media/mte/mte-apply.png":::
  
4. [Gizlilik bildirimini](https://privacy.microsoft.com/en-us/privacystatement) okuyun ve işiniz bittiğinde **Gönder'i** seçin. Uygulamanız onaylandıktan sonra bir karşılama e-postası alırsınız.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Microsoft 365 Defender portalında Microsoft Tehdit Uzmanları uygulama onayı" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Hoş geldiniz e-postanızı aldıktan sonra otomatik olarak hedeflenen saldırı bildirimlerini almaya başlarsınız.

6. **Ayarlar > Uç Noktaları > Genel > Gelişmiş özellikler** sayfasını ziyaret ederek durumunuzu doğrulayabilirsiniz. Onaylandığında **, Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimi** iki durumlu düğmesi görünür ve **Açık** olarak değiştirilir.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Microsoft Tehdit Uzmanları hedeflenen saldırı bildirimlerini göreceğiniz yer

Microsoft Tehdit Uzmanları hedefli saldırı bildirimini aşağıdaki ortamlar aracılığıyla alabilirsiniz:

- Microsoft 365 Defender portalın **Olaylar** sayfası
- Microsoft 365 Defender portalın **Uyarılar** panosu
- OData uyarı [API'si](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) ve [REST API](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- Gelişmiş avcılıkta [DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) tablosu
- Hedeflenen saldırı bildirimlerinin size e-posta yoluyla gönderilmesini seçerseniz gelen kutunuz. Aşağıdaki [E-posta bildirim kuralı oluşturma](#create-an-email-notification-rule) bölümüne bakın.

### <a name="create-an-email-notification-rule"></a>E-posta bildirim kuralı oluşturma

Bildirim alıcıları için e-posta bildirimleri göndermek için kurallar oluşturabilirsiniz. Tüm ayrıntılar için bkz. E-posta bildirimi oluşturmak, düzenlemek, silmek veya sorunlarını gidermek için  [uyarı bildirimlerini yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) .

## <a name="view-targeted-attack-notifications"></a>Hedeflenen saldırı bildirimlerini görüntüleme

Sisteminizi e-posta bildirimi alacak şekilde yapılandırdıktan sonra e-postanızdaki Microsoft Tehdit Uzmanları hedeflenen saldırı bildirimini almaya başlarsınız.

1. **Tehdit uzmanlarıyla** etiketlenmiş panodaki ilgili uyarı bağlamını görmek için e-postadaki bağlantıyı seçin.

2. **Uyarılar** sayfasında, diğer ayrıntıları görüntülemek için e-postada aldığınız uyarı konusunun aynısını seçin.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Microsoft Tehdit Uzmanları Abone Olma - İsteğe Bağlı Uzmanlar

Zaten Uç Nokta için Microsoft Defender bir müşteriyseniz, Microsoft Tehdit Uzmanları - İsteğe Bağlı Uzmanlar'a abone olmak için Microsoft temsilcinizle iletişime geçebilirsiniz.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Kuruluşunuzdaki şüpheli siber güvenlik etkinlikleri hakkında bir Microsoft tehdit uzmanına başvurun

Microsoft Tehdit Uzmanları Microsoft 365 Defender portalından iletişime geçebilirsiniz. Uzmanlar karmaşık tehditleri ve hedeflenen saldırı bildirimlerini anlamanıza yardımcı olabilir. Uyarılar ve olaylar hakkında daha fazla ayrıntı için uzmanlarla iş ortaklığı veya güvenliğin aşılmasına ilişkin öneriler. Portal panonuz tarafından açıklanan tehdit bilgileri bağlamı hakkında içgörü elde edin.

> [!NOTE]
>
> - Kuruluşunuzun özelleştirilmiş tehdit bilgileri verileriyle ilgili uyarı sorguları şu anda desteklenmiyor. Ayrıntılar için güvenlik operasyonlarınıza veya olay yanıt ekibinize başvurun.
> - **Tehdit uzmanına başvurun** formu aracılığıyla bir sorgu göndermek için Microsoft 365 Defender portalında **Güvenlik merkezinde güvenlik ayarlarını yönetme** iznine sahip olmanız gerekir.

1. Araştırmak istediğiniz bilgilerle ilgili portal sayfasına gidin: örneğin, **Cihaz**, **Uyarı** veya **Olay**. Araştırma isteği göndermeden önce sorgunuzla ilgili portal sayfasının görüntülendiğinden emin olun.

2. Üstteki menüden ? öğesini seçin **. Bir tehdit uzmanına başvurun**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Microsoft 365 Defender portalındaki menüden İsteğe Bağlı Microsoft Tehdit Uzmanları Uzmanları" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Açılır ekran açılır.

    Üst bilgi, deneme aboneliğinde veya tam bir Microsoft Tehdit Uzmanları - İsteğe Bağlı Uzmanlar aboneliğinde olup olmadığını gösterir.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Tehdit Uzmanları İsteğe Bağlı Uzmanlar deneme aboneliği ekranı" lightbox="../../media/mte/mte-trial.png":::

    **Araştırma konusu** alanı zaten isteğiniz için ilgili sayfanın bağlantısıyla doldurulur.

3. Sonraki alanda, Microsoft Tehdit Uzmanları araştırmayı başlatmak için yeterli bağlamı sağlamak için yeterli bilgi sağlayın.

4. Microsoft Tehdit Uzmanları karşılık olarak kullanmak istediğiniz e-posta adresini girin.

> [!NOTE]
> İsteğe Bağlı Uzmanlar servis taleplerinizin durumunu Microsoft Services Hub aracılığıyla izlemek isterseniz teknik hesap yöneticinize ulaşın.

Microsoft Services Hub'a hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Örnek araştırma konuları

### <a name="alert-information"></a>Uyarı bilgileri

- Arazi dışında yaşayan ikili dosya için yeni bir uyarı türü gördük. Uyarı kimliğini sağlayabiliriz. Bu uyarı hakkında daha fazla bilgi verebilir misiniz ve bunu nasıl daha fazla araştırabiliriz?
- Her ikisi de kötü amaçlı PowerShell betiklerini yürütmeye çalışan ancak farklı uyarılar oluşturan iki benzer saldırı gözlemledik. Biri "Şüpheli PowerShell komut satırı" diğeri ise "O365 tarafından sağlanan göstergeye göre kötü amaçlı bir dosya algılandı". Ne fark var?
- Bugün, yüksek profilli bir kullanıcının cihazından olağan dışı sayıda başarısız oturum açma işlemiyle ilgili garip bir uyarı aldık. Bu girişimler için başka kanıt bulamıyoruz. Microsoft 365 Defender bu girişimleri nasıl görebilir? Ne tür oturum açma işlemleri izleniyor?
- "Bir sistem yardımcı programı tarafından şüpheli davranış gözlemlendi" uyarısı hakkında daha fazla bağlam veya içgörü verebilir misiniz?
- "İletme/yeniden yönlendirme kuralı oluşturma" başlıklı bir uyarı gözlemledim. Etkinliğin zararsız olduğuna inanıyorum. Neden uyarı aldığımdan bahsedebilir misiniz?

### <a name="possible-machine-compromise"></a>Olası makine güvenliğinin aşılmasına neden olabilir

- Kuruluşumuzdaki birçok cihazda neden "Bilinmeyen işlem gözlemlendi" iletisini veya uyarısını gördüğümüzu açıklamaya yardımcı olabilir misiniz? Bu iletinin veya uyarının kötü amaçlı etkinliklerle ilgili olup olmadığını netleştirmek için her türlü girişi takdir ediyoruz.
- Geçen haftadan kalma aşağıdaki sistemde olası bir güvenliğin aşılmış olduğunu doğrulamaya yardımcı olabilir misiniz? Altı ay önce aynı sistemde önceki kötü amaçlı yazılım algılama işlemine benzer şekilde davranıyor.

### <a name="threat-intelligence-details"></a>Tehdit bilgileri ayrıntıları

- Kullanıcıya kötü amaçlı bir Word belgesi teslim eden bir kimlik avı e-postası algılandı. Belge, belirli bir kötü amaçlı yazılım ailesi için birden çok uyarı tetikleyen bir dizi şüpheli olaya neden oldu. Bu kötü amaçlı yazılım hakkında herhangi bir bilginiz var mı? Evet ise, bize bir bağlantı gönderebilir misiniz?
- Kısa süre önce sektörümüzü hedefleyen bir tehditle ilgili bir blog gönderisi gördük. Microsoft 365 Defender bu tehdit aktörü karşısında hangi korumayı sağladığını anlamamıza yardımcı olabilir misiniz?
- Kısa süre önce kuruluşumuza karşı yürütülen bir kimlik avı kampanyası gözlemledik. Bunun özel olarak şirketimize mi yoksa dikey mi hedeflendiğini söyleyebilir misiniz?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft Tehdit Uzmanları uyarı iletişimleri

- Olay yanıtı ekibiniz aldığımız hedeflenen saldırı bildirimini ele almamıza yardımcı olabilir mi?
- Bu hedefli saldırı bildirimini Microsoft Tehdit Uzmanları aldık. Kendi olay müdahale ekibimiz yok. Şimdi ne yapabiliriz ve olayı nasıl kapsayabiliriz?
- Microsoft Tehdit Uzmanları hedefli bir saldırı bildirimi aldık. Olay yanıtı ekibimize geçirebileceğimiz hangi verileri bize sağlayabilirsiniz?

> [!NOTE]
> Microsoft Tehdit Uzmanları, olay yanıtı hizmeti değil yönetilen tehdit avcılığı hizmetidir. Ancak, olay yanıtı gerektiren sorunları gidermek için kendi olay yanıt ekibinizle etkileşim kurabilirsiniz. Kendi olay yanıt ekibiniz yoksa ve Microsoft'un yardımını istiyorsanız CSS Siber Güvenlik Olayı Yanıt Ekibi (CIRT) ile etkileşime geçebilirsiniz. Sorgunuzu ele almak için bir bilet açabilirler.

## <a name="scenario"></a>Senaryo

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Yönetilen tehdit avcılığı sorgunuz hakkında bir ilerleme raporu alma

Microsoft Tehdit Uzmanları yanıtı sorgunuza göre değişir. Genel olarak aşağıdaki yanıtlardan birini alırsınız:

- Araştırmaya devam etmek için daha fazla bilgi gerekiyor
- Teknik bağlamı belirlemek için bir dosya veya birkaç dosya örneği gerekir
- Araştırma daha fazla zaman gerektirir
- İlk bilgiler soruşturmayı sonuçlandırmak için yeterliydi

Bir uzman daha fazla bilgi veya dosya örneği isterse, araştırmayı devam ettirmek için hızlı bir şekilde yanıt vermek çok önemlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Tehdit Uzmanlarına genel bakış](microsoft-threat-experts.md)
