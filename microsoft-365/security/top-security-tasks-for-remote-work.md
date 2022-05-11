---
title: Güvenlik ekiplerinin evden çalışmayı desteklemesi için en önemli 12 görev
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- remotework
ms.custom: admindeeplinkDEFENDER
description: İş e-postanızı ve verilerinizi fidye yazılımı, kimlik avı ve kötü amaçlı ekler gibi siber tehditlere karşı koruyun.
ms.openlocfilehash: 3c3a6ad89a795a45a0f76f868fbc6d23a52b963b
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319231"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>Güvenlik ekiplerinin evden çalışmayı desteklemesi için en önemli 12 görev

[Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) gibiyseniz ve aniden öncelikli olarak ev tabanlı bir iş gücünü destekliyorsanız, kuruluşunuzun mümkün olduğunca güvenli bir şekilde çalıştığından emin olmanıza yardımcı olmak istiyoruz. Bu makalede, güvenlik ekiplerinin en önemli güvenlik özelliklerini mümkün olan en hızlı şekilde uygulamasına yardımcı olacak görevlere öncelik verilmiştir.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="Evden çalışmayı desteklemek için gerçekleştirilecek en önemli görevler" lightbox="../media/security/security-support-remote-work.png":::


Microsoft'un iş planlarından birini kullanan küçük veya orta ölçekli bir kuruluşsanız, bunun yerine şu kaynaklara bakın:

- [İş planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](../admin/security-and-compliance/secure-your-business-data.md)
- [Kampanyalar için Microsoft 365](../business-premium/index.md) (Microsoft 365 İş için önerilen bir güvenlik yapılandırması içerir)

Kurumsal planlarımızı kullanan müşteriler için Microsoft, aşağıdaki tabloda listelenen ve hizmet planınız için geçerli olan görevleri tamamlamanızı önerir. Microsoft 365 kurumsal plan satın almak yerine abonelikleri birleştiriyorsanız, aşağıdakileri not edin:

- Microsoft 365 E3 Enterprise Mobility + Security (EMS) E3 ve Azure AD P1 içerir
- Microsoft 365 E5 EMS E5 ve Azure AD P2 içerir

****

|Adım|Görev|Tüm Office 365 Kurumsal planları|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Azure AD Multi-Factor Authentication'ı (MFA) etkinleştirme](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Tehditlere karşı korunun](#2-protect-against-threats)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Office 365 için Microsoft Defender yapılandırma](#3-configure-microsoft-defender-for-office-365)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Kimlik için Microsoft Defender yapılandırma](#4-configure-microsoft-defender-for-identity)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Microsoft 365 Defender’ı açın](#5-turn-on-microsoft-365-defender)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Telefonlar ve tabletler için Intune mobil uygulama korumasını yapılandırma](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Intune uygulama koruması da dahil olmak üzere konuklar için MFA ve koşullu erişimi yapılandırma](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Bilgisayarları cihaz yönetimine kaydetme ve uyumlu bilgisayarlar gerektirme](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Ağınızı bulut bağlantısı için iyileştirme](#9-optimize-your-network-for-cloud-connectivity)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Kullanıcıları eğitme](#10-train-users)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Bulut Uygulamaları için Microsoft Defender’ı kullanmaya başlayın](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Tehditleri izleme ve eylem gerçekleştirme](#12-monitor-for-threats-and-take-action)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

Başlamadan önce Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında Microsoft 365</a> [Güvenli Puanınızı](./defender/microsoft-secure-score.md) denetleyin. Merkezi bir panodan Microsoft 365 kimlikleriniz, verileriniz, uygulamalarınız, cihazlarınız ve altyapınızın güvenliğini izleyebilir ve geliştirebilirsiniz. Önerilen güvenlik özelliklerini yapılandırma, güvenlikle ilgili görevleri gerçekleştirme (raporları görüntüleme gibi) veya üçüncü taraf bir uygulama veya yazılımla önerileri ele almak için size puan verilir. Bu makalede önerilen görevler puanınızı yükseltir.

:::image type="content" source="../media/secure-score.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Güvenli Puan ekranı" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: Azure AD Multi-Factor Authentication'ı (MFA) etkinleştirme

Evden çalışan çalışanların güvenliğini artırmak için yapabileceğiniz en iyi şey MFA'yi açmaktır. Henüz süreçleriniz yoksa, bunu acil durum pilotu olarak değerlendirin ve takılan çalışanlara yardımcı olmak için destek personeline hazır olduğunuzdan emin olun. Donanım güvenlik cihazlarını muhtemelen dağıtamazsınız, Windows Hello biyometri ve Microsoft Authenticator gibi akıllı telefon kimlik doğrulama uygulamalarını kullanın.

Normalde Microsoft, MFA gerektirmeden önce kullanıcılara cihazlarını Multi-Factor Authentication'a kaydetmeleri için 14 gün süre vermenizi önerir. Ancak, iş gücünüz aniden evden çalışıyorsa, devam edin ve güvenlik önceliği olarak MFA'yı gerekli kılıp ihtiyacı olan kullanıcılara yardımcı olmaya hazır olun.

Bu ilkelerin uygulanması yalnızca birkaç dakika sürer, ancak önümüzdeki birkaç gün içinde kullanıcılarınızı desteklemeye hazır olun.

****

|Plan|Öneri|
|---|---|
|Microsoft 365 planları (Azure AD P1 veya P2 olmadan)|[Azure AD'de Güvenlik varsayılanlarını etkinleştirin](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Azure AD'deki güvenlik varsayılanları, kullanıcılar ve yöneticiler için MFA içerir.|
|Microsoft 365 E3 (Azure AD P1 ile)|Aşağıdaki ilkeleri yapılandırmak için [Ortak Koşullu Erişim ilkelerini](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) kullanın: <br/>- [Yöneticiler için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Tüm kullanıcılar için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Eski kimlik doğrulamasını engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (Azure AD P2 ile)|Azure AD Kimlik Koruması'nın avantajlarından yararlanarak, şu ilkeleri oluşturarak Microsoft'un [önerilen koşullu erişim ve ilgili ilke kümesini](./office-365-security/identity-access-policies.md) uygulamaya başlayın:<br/> - [Oturum açma riski orta veya yüksek olduğunda MFA gerektirme](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Modern kimlik doğrulamayı desteklemeyen istemcileri engelleme](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Yüksek riskli kullanıcıların parola değiştirmesi gerekir](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2: Tehditlere karşı koruma

Tüm Microsoft 365 planları çeşitli tehdit koruma özellikleri içerir. Bu özellikler için korumayı artırma işlemi yalnızca birkaç dakika sürer.

- Kötü amaçlı yazılımdan koruma
- Kötü amaçlı URL'lere ve dosyalara karşı koruma
- Kimlik avından koruma
- İstenmeyen posta önleme koruma

Başlangıç noktası olarak kullanabileceğiniz yönergeler için bkz. [Office 365 tehditlere karşı koruma](office-365-security/protect-against-threats.md).

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: Office 365 için Microsoft Defender yapılandırma

Microsoft 365 E5 ve Office 365 E5 dahil Office 365 için Microsoft Defender, kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya konan kötü amaçlı tehditlere karşı korur. Bunun yapılandırılması birkaç saat sürebilir.

Office 365 için Microsoft Defender:

- Kötü amaçlı içerik eklerini ve bağlantılarını inceleyen akıllı sistemler kullanarak kuruluşunuzu bilinmeyen e-posta tehditlerine karşı gerçek zamanlı olarak korur. Bu otomatik sistemler güçlü bir patlama platformu, buluşsal yöntemler ve makine öğrenmesi modelleri içerir.
- Ekip sitelerindeki ve belge kitaplıklarındaki kötü amaçlı dosyaları tanımlayıp engelleyerek, kullanıcılar işbirliği yaparken ve dosya paylaştığında kuruluşunuzu korur.
- Kimlik avı saldırılarını önlemeye yönelik makine öğrenmesi modellerini ve gelişmiş kimliğe bürünme algılama algoritmalarını uygular.

Planların özeti de dahil olmak üzere genel bakış için bkz. [Office 365 için Defender](./office-365-security/defender-for-office-365.md).

Genel Yöneticiniz şu korumaları yapılandırabilir:

- [Kasa Bağlantıları ilkelerini ayarlama](office-365-security/set-up-safe-links-policies.md)
- [Kasa Bağlantıları için genel ayarları yapılandırma](office-365-security/configure-global-settings-for-safe-links.md)
- [Kasa Ek ilkelerini ayarlama](office-365-security/set-up-safe-attachments-policies.md)

Bu iş yükleri için Office 365 için Defender yapılandırmak için Exchange Online yöneticiniz ve SharePoint Online yöneticinizle birlikte çalışmanız gerekir:

- [SharePoint, OneDrive ve Microsoft Teams için Uç Nokta için Microsoft Defender](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: Kimlik için Microsoft Defender yapılandırma

[Kimlik için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) gelişmiş tehditleri, güvenliği aşılmış kimlikleri ve kuruluşunuza yönelik kötü amaçlı insider eylemlerini tanımlamak, algılamak ve araştırmak için şirket içi Active Directory sinyallerinizden yararlanan bulut tabanlı bir güvenlik çözümüdür. Şirket içi altyapınızı ve bulut altyapınızı koruduğu, bağımlılıkları veya önkoşulları olmadığı ve anında avantaj sağlayabilecekleri için buna daha sonra odaklanın.

- Hızlı kurulum için [bkz. Kimlik için Microsoft Defender Hızlı Başlangıçlar](/azure-advanced-threat-protection/install-atp-step1)
- [Videoyu izleyin: Kimlik için Microsoft Defender giriş](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- [Kimlik için Microsoft Defender dağıtımının üç aşamasını](/azure-advanced-threat-protection/what-is-atp#whats-next) gözden geçirin

## <a name="5-turn-on-microsoft-365-defender"></a>5: Microsoft 365 Defender açma

Artık Office 365 için Microsoft Defender ve Kimlik için Microsoft Defender yapılandırdığınıza göre, bu özelliklerden gelen birleşik sinyalleri tek bir panoda görüntüleyebilirsiniz. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) uyarıları, olayları, otomatik araştırmayı ve yanıtı ve iş yükleri arasında (Kimlik için Microsoft Defender, Office 365 için Defender, Uç Nokta için Microsoft Defender ve gelişmiş tehdit avcılığı) bir araya getirir Microsoft Defender for Cloud Apps) öğesini <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalındaki</a> tek bir bölmede görüntüleyin.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="Microsoft 365 Defender panosu" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

Office 365 için Defender hizmetlerinizden birini veya daha fazlasını yapılandırdıktan sonra MTP'yi açın. MTP'ye sürekli yeni özellikler eklenir; önizleme özelliklerini almayı göz önünde bulundurun.

- [MTP hakkında daha fazla bilgi edinin](./defender/microsoft-365-defender.md)
- [MTP'i açma](./defender/m365d-enable.md)
- [Önizleme özelliklerini kabul etme](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: Telefonlar ve tabletler için Intune mobil uygulama korumasını yapılandırma

Microsoft Intune Mobil Uygulama Yönetimi (MAM), kuruluşunuzun telefon ve tablet verilerini bu cihazları yönetmeden yönetmenize ve korumanıza olanak tanır. Şu şekilde çalışır:

- Bir cihazdaki hangi uygulamaların yönetildiğini ve hangi davranışlara izin verileceğini belirleyen bir Uygulama Koruma İlkesi (APP) oluşturursunuz (yönetilen bir uygulamadaki verilerin yönetilmeyen bir uygulamaya kopyalanmasını önlemek gibi). Her platform için bir ilke oluşturursunuz (iOS, Android).
- Uygulama koruma ilkelerini oluşturduktan sonra, onaylı uygulamalar ve APP veri koruması gerektirmek için Azure AD'de bir koşullu erişim kuralı oluşturarak bunları zorunlu kılarsınız.

UYGULAMA koruma ilkeleri birçok ayar içerir. Neyse ki, her ayar hakkında bilgi edinmeniz ve seçenekleri tartmanıza gerek yoktur. Microsoft, başlangıç noktaları önererek ayarların yapılandırmasını uygulamayı kolaylaştırır. [Uygulama koruma ilkelerini kullanan Veri koruma çerçevesi](/mem/intune/apps/app-protection-framework), aralarından seçim yapabileceğiniz üç düzey içerir.

Daha da iyisi, Microsoft bu uygulama koruma çerçevesini bir dizi koşullu erişim ve tüm kuruluşların başlangıç noktası olarak kullanmasını önerdiğimiz ilgili ilkelerle koordine eder. Bu makaledeki yönergeleri kullanarak MFA uyguladıysanız, yarı yoldasınız!

Mobil uygulama korumasını yapılandırmak için [Ortak kimlik ve cihaz erişim ilkeleri](./office-365-security/identity-access-policies.md) bölümündeki yönergeleri kullanın:

 1. iOS ve Android için ilkeler oluşturmak için [APP veri koruma ilkelerini uygulama](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) kılavuzunu kullanın. Temel koruma için Düzey 2 (gelişmiş veri koruması) önerilir.
 2. [Onaylı uygulamalar ve APP koruması gerektir](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection) için bir koşullu erişim kuralı oluşturun.

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: Intune mobil uygulama koruması da dahil olmak üzere konuklar için MFA ve koşullu erişimi yapılandırma

Şimdi işbirliği yapmaya ve konuklarla çalışmaya devam edebilirsiniz. Microsoft 365 E3 planını kullanıyorsanız ve tüm kullanıcılar için MFA uyguladıysanız hazırsınız demektir.

Microsoft 365 E5 planını kullanıyorsanız ve risk tabanlı MFA için Azure Identity Protection'ın avantajlarından yararlanıyorsanız, birkaç ayarlama yapmanız gerekir (çünkü Azure AD Kimlik koruması konuklara genişletilmez):

- Konuklar ve dış kullanıcılar için her zaman MFA gerektirmek için yeni bir koşullu erişim kuralı oluşturun.
- Konukları ve dış kullanıcıları dışlamak için risk tabanlı MFA koşullu erişim kuralını güncelleştirin.

Konuk erişiminin Azure AD ile nasıl çalıştığını anlamak ve etkilenen ilkeleri güncelleştirmek için [konuk ve dış erişime izin vermek ve bu erişimi korumak için Ortak](./office-365-security/identity-access-policies-guest-access.md) ilkeleri güncelleştirme bölümündeki kılavuzu kullanın.

Oluşturduğunuz Intune mobil uygulama koruma ilkeleri, onaylı uygulamalar ve APP koruması gerektirmek için koşullu erişim kuralıyla birlikte konuk hesaplarına uygulanır ve kuruluş verilerinizin korunmasına yardımcı olur.

> [!NOTE]
> Uyumlu bilgisayarlar gerektirmek için bilgisayarları zaten cihaz yönetimine kaydettiyseniz, konuk hesaplarını cihaz uyumluluğunu zorlayan koşullu erişim kuralından da dışlamanız gerekir.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: Bilgisayarları cihaz yönetimine kaydetme ve uyumlu bilgisayarlar gerektirme

İş gücünüzün cihazlarını kaydetmek için çeşitli yöntemler vardır. Her yöntem cihazın sahipliğine (kişisel veya kurumsal), cihaz türüne (iOS, Windows, Android) ve yönetim gereksinimlerine (sıfırlama, benzite, kilitleme) bağlıdır. Bu işlem biraz zaman alabilir. Bkz. [Cihazları Microsoft Intune kaydetme](/mem/intune/enrollment/).

Başlamanın en hızlı yolu[, Windows 10 cihazlar için otomatik kayıt ayarlamaktır](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Bu öğreticilerden de yararlanabilirsiniz:

- [Windows cihazları Intune kaydetmek için Autopilot kullanma](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [iOS/iPadOS cihazlarını Intune kaydetmek için Apple Business Manager'da (ABM) Apple'ın Kurumsal Cihaz Kaydı özelliklerini kullanma](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Cihazları kaydettikten sonra, [şu ilkeleri oluşturmak için Ortak kimlik ve cihaz erişim ilkeleri'ndeki](./office-365-security/identity-access-policies.md) yönergeleri kullanın:

- [Cihaz uyumluluk ilkelerini tanımlama](./office-365-security/identity-access-policies.md#define-device-compliance-policies) — Windows 10 için önerilen ayarlar virüsten koruma gerektirmeyi içerir. Microsoft 365 E5 varsa çalışan cihazlarının durumunu izlemek için Uç Nokta için Microsoft Defender kullanın. Diğer işletim sistemleri için uyumluluk ilkelerinin virüsten koruma ve son nokta koruma yazılımı içerdiğini unutmayın.
- [Uyumlu bilgisayarlar gerektir](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) — Bu, cihaz uyumluluk ilkelerini zorunlu kılan Azure AD koşullu erişim kuralıdır.

Bir cihazı yalnızca bir kuruluş yönetebilir, bu nedenle konuk hesaplarını Azure AD koşullu erişim kuralının dışında tutmayı unutmayın. Konuk ve dış kullanıcıları cihaz uyumluluğu gerektiren ilkelerden dışlamıyorsanız, bu ilkeler bu kullanıcıları engeller. Daha fazla bilgi için bkz [. Konuk ve dış erişime izin vermek ve bunları korumak için ortak ilkeleri güncelleştirme](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: Ağınızı bulut bağlantısı için iyileştirme

Çalışanlarınızın büyük bir kısmının evden çalışmasını hızlı bir şekilde sağlıyorsanız, bu ani bağlantı düzenleri değişimi kurumsal ağ altyapısını önemli ölçüde etkileyebilir. Bulut hizmetleri benimsenmeden önce birçok ağ ölçeklendirildi ve tasarlandı. Çoğu durumda, ağlar uzaktan çalışanlara dayanıklıdır, ancak tüm kullanıcılar tarafından aynı anda uzaktan kullanılmak üzere tasarlanmamıştır.

VPN yoğunlaştırıcıları, merkezi ağ çıkış ekipmanları (ara sunucular ve veri kaybı önleme cihazları gibi), merkezi internet bant genişliği, backhaul MPLS devreleri, NAT özelliği vb. gibi ağ öğeleri, bunları kullanan tüm işletmenin yükü nedeniyle aniden muazzam bir yük altına konur. Sonuçta düşük performans ve üretkenlik ile birlikte evden çalışmaya uyum sağlayan kullanıcılar için kötü bir kullanıcı deneyimi elde edilir.

Trafiği bir kurumsal ağ üzerinden geri yönlendirerek geleneksel olarak sağlanan korumalardan bazıları, kullanıcılarınızın eriştiği bulut uygulamaları tarafından sağlanır. Bu makalede bu adıma ulaştıysanız, Microsoft 365 hizmetleri ve verileri için bir dizi gelişmiş bulut güvenliği denetimi uygulamış olursunuz. Bu denetimler gerçekleştiğinde, uzak kullanıcıların trafiğini doğrudan Office 365 yönlendirmeye hazır olabilirsiniz. Diğer uygulamalara erişim için hala bir VPN bağlantısına ihtiyacınız varsa, bölünmüş tünel uygulayarak performansınızı ve kullanıcı deneyiminizi büyük ölçüde geliştirebilirsiniz. Kuruluşunuzda anlaşmaya vardığınızda, bu işlem iyi eşgüdümlü bir ağ ekibi tarafından bir gün içinde gerçekleştirilebilir.

Daha fazla bilgi için Docs'ta şu kaynaklara bakın:

- [Genel bakış: VPN bölünmüş tünel kullanarak uzak kullanıcılar için bağlantıyı iyileştirme](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Office 365 için VPN bölünmüş tüneli uygulama](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Bu konudaki son blog makaleleri:

- [Altyapınızdaki yükü azaltmak & uzak personel için trafiği hızla iyileştirme](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimleri elde etmek için güvenlik uzmanları ve BT için alternatif yollar](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: Kullanıcıları eğit

Eğitim kullanıcıları, kullanıcılarınızı ve güvenlik operasyonları ekibinizi çok zaman ve hayal kırıklığından kurtarabilir. Savvy kullanıcılarının şüpheli e-posta iletilerindeki ekleri açma veya bağlantılara tıklama olasılığı daha düşüktür ve şüpheli web sitelerinden kaçınma olasılıkları daha yüksektir.

Harvard Kennedy School [Siber Güvenlik Kampanyası El Kitabı](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) , kullanıcıları kimlik avı saldırılarını belirlemeye yönelik eğitim de dahil olmak üzere kuruluşunuzda güçlü bir güvenlik farkındalığı kültürü oluşturma konusunda mükemmel rehberlik sağlar.

Microsoft 365, kuruluşunuzdaki kullanıcıları bilgilendirmeye yardımcı olmak için aşağıdaki kaynakları sağlar:

****

|Kavram|Kaynaklar|
|---|---|
|Microsoft 365|[Özelleştirilebilir öğrenme yolları](/office365/customlearning/) <p>Bu kaynaklar, kuruluşunuzdaki son kullanıcılar için eğitimi bir araya getirebilmenize yardımcı olabilir|
|Microsoft 365 güvenlik|[Learning modülü: kuruluşunuzun güvenliğini Microsoft 365 yerleşik, akıllı güvenlikle sağlama](/learn/modules/security-with-microsoft-365) <p>Bu modül, Microsoft 365 güvenlik özelliklerinin birlikte nasıl çalıştığını açıklamanıza ve bu güvenlik özelliklerinin avantajlarını açıklamanıza olanak tanır.|
|Çok faktörlü kimlik doğrulaması|[İki aşamalı doğrulama: Ek doğrulama sayfası nedir?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Bu makale, son kullanıcıların çok faktörlü kimlik doğrulamasının ne olduğunu ve kuruluşunuzda neden kullanıldığını anlamasına yardımcı olur.|

Microsoft, bu kılavuza ek olarak, kullanıcılarınızın bu makalede açıklanan eylemleri gerçekleştirmelerini önerir: [Hesabınızı ve cihazlarınızı korsanlara ve kötü amaçlı yazılımlara karşı koruma](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Bu eylemler şunlardır:

- Güçlü parolalar kullanma
- Cihazları koruma
- Windows 10 ve Mac bilgisayarlarda güvenlik özelliklerini etkinleştirme (yönetilmeyen cihazlar için)

Microsoft, kullanıcıların aşağıdaki makalelerde önerilen eylemleri gerçekleştirerek kişisel e-posta hesaplarını korumalarını da önerir:

- [Outlook.com e-posta hesabınızın korunmasına yardımcı olun](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Gmail hesabınızı 2 aşamalı doğrulama ile koruma](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Microsoft Defender for Cloud Apps ile Kullanmaya başlayın

[Microsoft Defender for Cloud Apps](/cloud-app-security), tüm bulut hizmetlerinizde siber tehditleri belirlemek ve mücadele etmek için zengin görünürlük, veri seyahati üzerinde denetim ve gelişmiş analiz sağlar. Bulut için Defender Uygulamaları kullanmaya başladıktan sonra, anomali algılama ilkeleri otomatik olarak etkinleştirilir, ancak Bulut için Defender Uygulamalar'ın tüm anomali algılama uyarılarının tetiklenmediği yedi günlük ilk öğrenme süresi vardır.

şimdi Bulut için Defender Uygulamaları ile Kullanmaya başlayın. Daha sonra daha gelişmiş izleme ve denetimler ayarlayabilirsiniz.

- [Hızlı Başlangıç: Bulut için Defender Uygulamaları ile Kullanmaya başlayın](/cloud-app-security/getting-started-with-cloud-app-security)
- [Anlık davranış analizi ve anomali algılaması alma](/cloud-app-security/anomaly-detection-policy)
- [Microsoft Defender for Cloud Apps hakkında daha fazla bilgi edinin](/cloud-app-security/what-is-cloud-app-security)
- [Yeni özellikleri ve özellikleri gözden geçirme](/cloud-app-security/release-notes)
- [Temel kurulum yönergelerine bakın](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Tehditleri izleme ve işlem gerçekleştirme

Microsoft 365, durumu izlemenin ve uygun eylemleri gerçekleştirmenin çeşitli yollarını içerir. En iyi başlangıç noktanız, kuruluşunuzun [Microsoft Güvenli Puanını](./defender/microsoft-secure-score.md) ve dikkatinizi gerektiren uyarıları veya varlıkları görüntüleyebileceğiniz <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalıdır</a>.

- [Microsoft 365 Defender portalıyla Kullanmaya başlayın](./defender/microsoft-365-defender.md#the-microsoft-365-defender-portal)
- [Microsoft 365'de güvenlik portallarına bakın](./defender/portals.md)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler! En önemli güvenlik korumalarından bazılarını hızlı bir şekilde uyguladınız ve kuruluşunuz çok daha güvenlidir. Artık tehdit koruma özellikleri (Uç Nokta için Microsoft Defender dahil), veri sınıflandırma ve koruma özellikleri ve yönetim hesaplarının güvenliğini sağlama konusunda daha da ileri gitmeye hazırsınız. Microsoft 365 için daha ayrıntılı, yöntemsel güvenlik önerileri kümesi için bkz. [Microsoft 365 İş İçin Güvenlik Karar Alıcılar (BDM)](Microsoft-365-security-for-bdm.md).

Ayrıca docs.microsoft.com/security'da Microsoft'un yeni [Bulut için Defender](/security) ziyaret edin.
