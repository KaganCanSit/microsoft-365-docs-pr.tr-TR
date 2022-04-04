---
title: Web siteniz aracılığıyla Microsoft Tehdit Uzmanları özelliklerini yapılandırma Microsoft 365 Defender
description: Günlük güvenlik işlemlerinizi ve güvenlik Microsoft 365 Defender işlerinizi yapılandırmak, yönetmek ve kullanmak için Microsoft Tehdit Uzmanlarına Abone Olun.
keywords: Microsoft Tehdit Uzmanları tehdit arama hizmeti, MTE, Microsoft tarafından yönetilen arama hizmeti
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
ms.openlocfilehash: 8a8de691ff08b50b56c34ed9e779cc97d48c5fcd
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755823"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Web siteniz aracılığıyla Microsoft Tehdit Uzmanları özelliklerini yapılandırma Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Başlamadan önce

> [!IMPORTANT]
> Başvurmadan önce, Microsoft Teknik Servis sağlayıcınız ve hesap ekibiyle birlikte Microsoft Tehdit Uzmanları uygunluğu gereksinimlerini tartışın : Hedefli Saldırı Bildirimleri tarafından yönetilen tehdit avı hizmeti.

Hedefli saldırı bildirimlerini almak için, kayıtlı cihazlarla Microsoft 365 Defender uygulama uygulamanız gerekir. Ardından, uygulama için M365 portalı üzerinden bir uygulama gönderin Microsoft Tehdit Uzmanları Saldırı Bildirimleri.

Microsoft Tehdit Uzmanları - Talep Uzmanlarına abone olmak için hesap ekibinize veya Microsoft temsilcisine başvurun. Talep Uzmanları, tehdit uzmanlarımıza başvurarak kurumlarınızı ilgili algılamalardan ve tehditlerden nasıl koruyacaklarını tartışmanıza olanak sağlar.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Uygulama Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri hizmeti

Uç Nokta ve Microsoft 365 Defender için Microsoft Defender'a zaten sahipsinizse Microsoft Tehdit Uzmanları – Hedefli Saldırı Bildirimleri için Microsoft 365 Defender uygulayabilirsiniz.  Hedefli saldırı bildirimleri, size, organizasyon açısından en önemli tehditleri belirlemeye yardımcı olmak için özel içgörü ve çözümleme sağlar, böylece bunları hızla yanıtabilirsiniz.

1. Gezinti bölmesinde, Ayarlar > **Endpoints > > Advanced features > Microsoft Tehdit Uzmanları - Targeted Attack Notifications 'a gidin**.

2. **Uygula'ya seçin**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Portalda Microsoft Tehdit Uzmanları Ayarları Microsoft 365 Defender sayfası" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Microsoft'un uygulamanız hakkında size ulaşamalarını istediğiniz adı ve e-posta adresinizi girin.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Microsoft Tehdit Uzmanları Microsoft 365 Defender portalında Microsoft 365 Defender sayfası" lightbox="../../media/mte/mte-apply.png":::
  
4. Gizlilik [bildirimini okuyun](https://privacy.microsoft.com/en-us/privacystatement) ve **bitirerek** Gönder'i seçin. Başvurunız onaylandıktan sonra bir hoş geldiniz e-postası alırsınız.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Microsoft Tehdit Uzmanları portalında uygulama Microsoft 365 Defender onayı" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Hoş geldiniz e-postanızı aldıktan sonra, otomatik olarak hedefli saldırı bildirimlerini almaya başlarsınız.

6. Genel Bağlantı Noktaları ve Gelişmiş **Ayarlar >'Ayarlar > ziyaret > > doğrularız**. Onaylandıktan sonra, **Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimi** iki durumlu düğme görünür ve **Açık hale gelir**.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Buradan, hedefli saldırı bildirimlerini göreceğiniz Microsoft Tehdit Uzmanları

Hedefli saldırı bildirimini Microsoft Tehdit Uzmanları ortamlar aracılığıyla alırsınız:

- Microsoft 365 Defender portalının **Olaylar** sayfası
- Microsoft 365 Defender portalının **Uyarılar panosu**
- OData uyarı [API'si](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) ve [REST API'si](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Gelişmiş avda DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) tablosu
- Hedefli saldırı bildirimlerinin e-posta yoluyla size gönderilmeyi seçerseniz gelen kutunuz. Aşağıdaki [E-posta bildirimi kuralı oluşturma.](#create-an-email-notification-rule)

### <a name="create-an-email-notification-rule"></a>E-posta bildirim kuralı oluşturma

Bildirim alıcıları için e-posta bildirimleri göndermek için kurallar oluşturabilirsiniz. Tüm ayrıntılar için bkz.  [E-posta bildirimi oluşturmak](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) , düzenlemek, silmek veya gidermek için uyarı bildirimlerini yapılandırma.

## <a name="view-targeted-attack-notifications"></a>Hedefli saldırı bildirimlerini görüntüleme

Sisteminizi e-posta bildirimi alacak şekilde yapılandırdıktan Microsoft Tehdit Uzmanları e-postanıza hedefli saldırı bildirimi almaya başlarsınız.

1. Tehdit uzmanlarıyla etiketlenen panoda ilgili uyarı bağlamına gitmek için e-postada bağlantıyı **seçin**.

2. Uyarılar **sayfasında,** diğer ayrıntıları görüntülemek için e-postada alınanla aynı uyarı konusunu seçin.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Microsoft Tehdit Uzmanları - Talep Üzerine Uzmanlara Abone Olma

Zaten bir Uç Nokta için Microsoft Defender müşterisiysiniz, Microsoft Tehdit Uzmanları - Talep Üzerine Uzmanlara abone olmak için Microsoft temsilcinize başvurebilirsiniz.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Bir Microsoft tehdit uzmanına, organizasyonlu şüpheli siber güvenlik etkinlikleri hakkında danışma

Microsoft Tehdit Uzmanları portalın içinden Microsoft 365 Defender kurabilirsiniz. Uzmanlar karmaşık tehditleri ve hedefli saldırı bildirimlerini anlamanıza yardımcı olabilir. Uyarılar ve olaylar hakkında daha ayrıntılı bilgi almak veya güvenliğin ele ele alınarak ele alınarak öneri almak için uzmanlarla ortak çalışma. Portal panonuz tarafından açıklanan tehdit zekası bağlamı hakkında içgörü elde edin.

> [!NOTE]
>
> - Kuruluşun özelleştirilmiş tehdit zekası verileriyle ilgili uyarı sorguları şu anda desteklenmiyor. Ayrıntılar için güvenlik işlemleriniz veya olay müdahale ekibinize danışın.
> - Bir tehdit uzmanı formu aracılığıyla **sorgu** göndermek için Microsoft 365 Defender portalında güvenlik merkezi ayarlarını **yönetme iznine sahip olmak** gerekir.

1. Araştırma yapmak istediğiniz bilgilerle ilgili portal sayfasına gidin: **Örneğin, Cihaz**, **Uyarı** veya **Olay**. Bir soruşturma isteği göndermeden önce sorgulamanıza ilişkin portal sayfasının görüntüde olduğundan emin olun.

2. Üst menüden? öğesini seçin **. Bir tehdit uzmanına danışın**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Microsoft Tehdit Uzmanları portalında yer alan menüden Talep Üzerine Microsoft 365 Defender." lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Açılır bir ekran açılır.

    Üst bilgide, bir deneme aboneliği mi yoksa tam deneme sürümü ya da Microsoft Tehdit Uzmanları Uzman isteğe bağlı abonelik mi olduğu belirtiliyor.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Microsoft Tehdit Uzmanları Microsoft 365 Defender portalında ISTEĞE Bağlı Microsoft 365 Defender ekranı" lightbox="../../media/mte/mte-trial.png":::

    Araştırma **konu** alanı, isteğinize uygun sayfanın bağlantısıyla önceden doldurulur.

3. Sonraki alanda, ilgili kullanıcıya araştırmayı başlatmak için Microsoft Tehdit Uzmanları yeterli bağlamı sağlayacak kadar bilgi girin.

4. Bu adresle karşılık gelen e-posta adresini Microsoft Tehdit Uzmanları.

> [!NOTE]
> Microsoft Services Hub aracılığıyla Talep Üzerine Uzmanlar vakalarının durumunu izlemek için teknik hesap yöneticinize erişin.

Microsoft Hizmetleri Merkezi'ne hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Örnek araştırma konuları

### <a name="alert-information"></a>Uyarı bilgileri

- Karadan canlı ikili için yeni bir uyarı türü gördük. Uyarı kimliğini s sağlamamız gerekir. Bu uyarı hakkında daha fazla bilgi ve bu uyarıyı daha fazla nasıl araştıracağız?
- Her ikisi de kötü amaçlı PowerShell betiklerini yürütmeye çalışsa da farklı uyarılar oluşturan iki benzer saldırı gözlemledi. Bunlardan biri "Suspicious PowerShell komut satırı", diğeri "O365 tarafından sağlanan göstergeye göre kötü amaçlı bir dosya algılandı" olur. Fark nedir?
- Bugün yüksek profilli bir kullanıcının cihazında olağandışı sayıda başarısız oturum açma olduğuyla ilgili tek bir uyarı aldık. Bu girişimler için başka kanıt bulamıyoruz. Bu Microsoft 365 Defender nasıl görebilirim? Hangi tür oturum açmalar izleniyor?
- "Sistem yardımcı programı tarafından şüpheli davranış gözlendi" uyarısı hakkında daha fazla bağlam veya içgörü ve bilgi verecek misiniz?
- "İ iletme/yeniden yönlendirme kuralı oluşturma" başlıklı bir uyarı gözlemledm. Etkinliğin böyle olduğunu biliyorum. Neden uyarı aldığımı söyler misiniz?

### <a name="possible-machine-compromise"></a>Olası makine güvenliği

- Kuruluşumuz birçok cihazlarında "Bilinmeyen süreç gözlemlendi" iletisi veya uyarılarını neden gördüğünüze yardımcı olabilir misiniz? Bu ileti veya uyarının kötü amaçlı etkinliklerle ilgili olup olmadığını netleştirmek için yapılan tüm girdiler bizim için çok teşekkür ederiz.
- Geçen haftadan itibaren, aşağıdaki sistemle olası bir güvenliğin doğrulanmasına yardımcı olabilir misiniz? Altı ay önce aynı sistemde daha önceki bir kötü amaçlı yazılım algılaması gibi devam ediyor.

### <a name="threat-intelligence-details"></a>Tehdit İstihbaratı ayrıntıları

- Kullanıcıya kötü amaçlı bir Word belgesi teslim edilen bir kimlik avı e-postası algıladık. Belge, belirli bir kötü amaçlı yazılım ailesi için birden çok uyarıyı tetikleyen bir dizi şüpheli olaya neden oldu. Bu kötü amaçlı yazılım hakkında herhangi bir bilginiz var mı? Evet ise bize bağlantı gönderebilir misiniz?
- Yakın zamanda, endüstrimizi hedef alan bir tehditle ilgili bir blog gönderisi gördük. Bu tehditlere karşı hangi koruma Microsoft 365 Defender anlamamıza yardımcı olabilir misiniz?
- Yakın zamanda kuruluşumuz için yürütülen bir kimlik avı kampanyası gözlemledi. Bu hedefin özellikle şirketini mi yoksa dikey mi olduğunu bize söyler misiniz?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft Tehdit Uzmanları iletişimleri

- Olay müdahale ekibiniz, bize gelen hedefli saldırı bildirimini bizim için ele alı edebilir mi?
- Bu hedefli saldırı bildirimini Microsoft Tehdit Uzmanları. Kendi olay müdahale ekibimiz yok. Şimdi ne yapabiliriz ve olayı nasıl içerebiliriz?
- Bir iş için hedefli saldırı bildirimi Microsoft Tehdit Uzmanları. Olay müdahale ekibimize hangi verileri veriyebilirsiniz?

> [!NOTE]
> Microsoft Tehdit Uzmanları bir olay yanıt hizmeti değil, yönetilen bir tehdit arama hizmetidir. Ancak, bir olay yanıtı gerektiren sorunları ele alan kendi olay müdahale ekibiyle etkileşime girişebilirsiniz. Kendi olay müdahale ekibiniz yoksa ve Microsoft'un yardımını istediysiniz, CSS Siber Güvenlik Olayı Yanıt Ekibi'nden (CIRT) etkileşim s belirttiysiniz. Sorgulamanıza yardımcı olmak için bir bilet açabilirler.

## <a name="scenario"></a>Senaryo

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Yönetilen av sorgunuz hakkında bir ilerleme raporu alma

Sorgudan gelen Microsoft Tehdit Uzmanları sorgulamanıza göre değişir. Genellikle aşağıdaki yanıtlardan birini alırsınız:

- Soruşturmaya devam etmek için daha fazla bilgi gereklidir
- Teknik bağlamı belirlemek için bir dosya veya birkaç dosya örneği gerekir
- İnceleme için daha fazla zaman gerekiyor
- İlk bilgiler araştırmayı sonuçlandıracak kadar yeterli değildi

Bir uzman daha fazla bilgi veya dosya örneği isterse, araştırmanın hareketli ilerlemesi için hızlı bir şekilde yanıt vermek çok önemlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Tehdit Uzmanları genel bakış](microsoft-threat-experts.md)
