---
title: Evden çalışmayı desteklemek için güvenlik ekipleri için en önemli 12 görev
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
description: İş e-postanızı ve verilerinizi fidye yazılımları, kimlik avı ve kötü amaçlı ekler de dahil olmak üzere siber tehditlere karşı koruyun.
ms.openlocfilehash: 584da4e192ddbd8ac5b223e0d292a71f0c35c305
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019446"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>Evden çalışmayı desteklemek için güvenlik ekipleri için en önemli 12 görev

[Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) gibiysanız ve aniden ev iş gücüne dayalı bir iş gücüne destek olasanız, organizasyonsunuz mümkün olduğunca güvenli bir şekilde çalışıyor olduğundan emin olmak istiyoruz. Bu makalede, güvenlik ekiplerinin en önemli güvenlik özelliklerini mümkün olan en kısa sürede gerçekleştirmesine yardımcı olmak için görevler önceliklendirmede yer almaktadır.

![Evden çalışmayı desteklemek için bu en önemli görevleri gerçekleştirin.](../media/security/security-support-remote-work.png)

Microsoft'un iş planlarından birini kullanan küçük veya orta ölçekli bir kuruluşsanız, bunun yerine aşağıdaki kaynaklara bakın:

- [İş planları için güvenlik sağlamanın en Office 365 10 Microsoft 365](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 Ayarları](../business-premium/index.md) (Microsoft 365 İş için önerilen bir güvenlik Microsoft 365 içerir)

Kurumsal planlarımızı kullanan müşteriler için Microsoft, aşağıdaki tabloda listelenen ve hizmet planınıza uygun görevleri tamamlamanızı önermektedir. Kurumsal plan satın almak Microsoft 365 abonelikleri birleştirerek şu bilgileri not alabilirsiniz:

- Microsoft 365 E3 posta Enterprise Mobility + Security (EMS) E3 ve Azure AD P1'i içerir
- Microsoft 365 E5 ems E5 ve Azure AD P2 içerir

****

|Adım|Görev|Tüm Office 365 Kurumsal planları|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Azure AD Multi-Factor Authentication'i (MFA) etkinleştirme](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Tehditlere karşı koruma](#2-protect-against-threats)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Windows için Microsoft Defender'ı Office 365](#3-configure-microsoft-defender-for-office-365)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Kimlik için Microsoft Defender'ı yapılandırma](#4-configure-microsoft-defender-for-identity)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[E-Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Telefonlar ve tabletler için Intune mobil uygulama korumasını yapılandırma](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Intune uygulama koruması da dahil olmak üzere konuklar için MFA ve koşullu erişimi yapılandırma](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Bilgisayarları cihaz yönetimine kaydettirin ve uyumlu bilgisayarlar gerektirir](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Anızı bulut bağlantısı için en iyi duruma getirme](#9-optimize-your-network-for-cloud-connectivity)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Kullanıcıları eğitin](#10-train-users)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Bulut Uygulamaları için Microsoft Defender ile çalışmaya başlama](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Tehditleri izleme ve önlem alma](#12-monitor-for-threats-and-take-action)|![Dahil.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|

Başlamadan önce, portalda Microsoft 365 [Puanınızı](./defender/microsoft-secure-score.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a> Merkezi bir panodan kimlikleri, verileri, uygulamaları, cihazları ve altyapıyı Microsoft 365 için güvenliği izleyebilir ve geliştirebilirsiniz. Önerilen güvenlik özelliklerini yapılandırma, güvenlikle ilgili görevleri (raporları görüntüleme gibi) gerçekleştirme ya da üçüncü taraf bir uygulama veya yazılımla önerilere yönelik öneriler gerçekleştirmeyle ilgili puanlar verilir. Bu makalede önerilen görevler puanınızı yükseltecek.

![Microsoft Güvenli Puanı'nın ekran görüntüsü.](../media/secure-score.png)

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: Azure AD Multi-Factor Authentication'i (MFA) etkinleştirme

Evden çalışan çalışanların güvenliğini iyileştirmek için tek bir şey, MFA'ya açmaktır. Henüz süreçleriz yoksa, bunu bir acil durum pilot olarak işlemden takip edin ve takılmış çalışanlara yardımcı olmaya hazır destek personeline sahip olduğundan emin olun. Donanım güvenlik cihazlarını dağıtamayy olarak, biyometrik Windows Hello akıllı telefon kimlik doğrulama uygulamaları (yazılım gibi) Microsoft Authenticator.

Microsoft, MFA gerektirmeden önce, kullanıcıları Multi-Factor Authentication için kaydetmeleri için kullanıcılara 14 gün süre verir. Öte yandan, iş gücünüzü aniden evden çalışıyorsanız devam edin ve bir güvenlik önceliği olarak MFA'yı gerekli olarak iş gücünüzün ihtiyacı olan kullanıcılara yardımcı olmak için hazır olun.

Bu ilkelerin uygulanması yalnızca birkaç dakika sürer, ancak kullanıcılarınızı önümüzdeki birkaç gün boyunca desteklemeye hazır olur.

****

|Plan|Öneri|
|---|---|
|Microsoft 365 (Azure AD P1 veya P2 olmadan)|[Azure AD'de güvenlik varsayılanlarını etkinleştirin](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Azure AD'de güvenlik varsayılanları, kullanıcılar ve yöneticiler için MFA içerir.|
|Microsoft 365 E3 (Azure AD P1 ile)|Aşağıdaki [ilkeleri yapılandırmak için Ortak](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) Koşullu Erişim ilkelerini kullanın: <br/>- [Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Eski kimlik doğrulamayı engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (Azure AD P2 ile)|Azure AD Kimlik Koruması'ndan yararlanmak için, bu ilkeleri oluşturarak Microsoft'un önerilen koşullu erişim ve [ilgili ilkeler](./office-365-security/identity-access-policies.md) setlerini uygulamaya başlayabilirsiniz:<br/> - [Oturum açma riski orta veya yüksek olduğunda MFA gerektirme](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Modern kimlik doğrulamasını desteklemez istemcileri engelleme](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|
|

## <a name="2-protect-against-threats"></a>2: Tehditlere karşı koruma

Tüm Microsoft 365 planları çeşitli tehdit koruma özellikleri içerir. Bu özellikler için çarpma koruması yalnızca birkaç dakika sürer.

- Kötü amaçlı yazılımdan koruma
- Kötü amaçlı URL'lere ve dosyalara karşı koruma
- Kimlik avı koruması
- İstenmeyen posta önleme koruması

Başlangıç [noktası olarak kullanabileceğiniz Office 365](office-365-security/protect-against-threats.md) için bkz. Güvenlik tehditlerine karşı koruma.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: Windows için Microsoft Defender'ı Office 365

Microsoft 365 E5 Office 365 ile birlikte gelen Office 365 için Microsoft Defender, e-posta iletileri, bağlantılar (Office 365 E5 URL'ler) ve işbirliği araçları tarafından tehditlere karşı kuruluşu korur. Bunun yapılandırılması birkaç saat sürebilir.

Office 365 için Microsoft Defender:

- Ekleri ve bağlantıları kötü amaçlı içerik için inceleyen akıllı sistemleri kullanarak, organizasyonlarınızı bilinmeyen e-posta tehditlerinden gerçek zamanlı olarak korur. Bu otomatik sistemler güçlü bir detonation platformu, heuristics ve makine öğrenme modellerini içerir.
- Kullanıcılar ekip sitelerinde ve belge kitaplıklarında kötü amaçlı dosyaları tanımleyerek ve engelleyerek, işbirliği yapın ve dosya paylaştığında organizasyonlarınızı korur.
- Kimlik avı saldırılarını tersine çeviren makine öğrenme modellerini ve gelişmiş kimliğe bürünme algılama algoritmalarını uygular.

Planların özeti de dahil olmak üzere genel bir bakış için bkz. [Office 365](./office-365-security/defender-for-office-365.md).

Genel Yöneticiniz şu korumaları yapılandırarak şunları yapılandırmış olabilir:

- [Bağlantılar Kasa ayarlama](office-365-security/set-up-safe-links-policies.md)
- [Bağlantılar için genel Kasa yapılandırma](office-365-security/configure-global-settings-for-safe-links.md)
- [Ekleri Kasa ilkelerini ayarlama](office-365-security/set-up-safe-attachments-policies.md)

Bu iş yükleri için Defender'ı Exchange Online için SharePoint Online yöneticinizle birlikte çalışmanız ve Office 365 gerekir:

- [SharePoint, OneDrive için Uç Nokta için Microsoft Defender Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: Kimlik için Microsoft Defender'ı yapılandırma

[Identity için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) , şirket içi Active Directory sinyallerinizi kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini belirlemek, algılamak ve araştırmak için yararlanan bulut tabanlı bir güvenlik çözümüdür. Prem ve bulut altyapınızı koruması, bağımlılıkları veya önkoşulları yok olması ve anında avantaj sağ sağlay özelliğinden dolayı bir sonraki adıma odaklanın.

- Kurulumu [hızla yapmak için Kimlik için Microsoft Defender](/azure-advanced-threat-protection/install-atp-step1) Hızlı Başlangıçlar'a bakın
- Videoyu [izleyin: Identity için Microsoft Defender'a Giriş](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Kimlik dağıtımı [için Microsoft Defender'ın üç aşamasını gözden geçirme](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: Sayfayı Microsoft 365 Defender

Artık Microsoft Defender for Office 365 Ve Identity için Microsoft Defender'ı yapılandırmış olduğunuuza göre, bu özelliklerden gelen birleşik sinyalleri tek bir panoda görüntüleyebilirsiniz. [Microsoft 365 Defender](./defender/microsoft-365-defender.md), iş yükleri arasında uyarıları, olayları, otomatik soruşturma ve yanıtı ve gelişmiş avları (Kimlik için Microsoft Defender, Office 365 için Defender, Uç Nokta için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender) bir araya getirir Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"> portalında oturum açın</a>.

![MTP panosu çizimi.](../media/top-ten-security-remote-work-mtp-dashboard.png)

Defender for Office 365 hizmetlerinizi yapılandırdıktan sonra, MTP'yi açma. Yeni özellikler MTP'ye sürekli olarak eklenir; önizleme özelliklerini almayı kabul etmek iyi bir tercih.

- [MTP hakkında daha fazla bilgi](./defender/microsoft-365-defender.md)
- [MTP'yi açma](./defender/m365d-enable.md)
- [Önizleme özelliklerini kabul etmek](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: Telefonlar ve tabletler için Intune mobil uygulama korumasını yapılandırma

Microsoft Intune Uygulama Yönetimi (MAM), bu cihazları yönetmeden kuruluş verilerinizi telefon ve tabletlerde yönetmenize ve korumanıza olanak tanır. Bu, şu şekilde çalışır:

- Bir cihazda hangi uygulamaların yönetil olduğunu ve hangi davranışların izin verilmiyor olduğunu belirleyen bir Uygulama Koruma İlkesi (APP) oluşturabilirsiniz (örneğin, yönetilen bir uygulamadan yönetilemeyen bir uygulamaya verilerin kopyalanır). Her platform (iOS, Android) için bir ilke oluşturun.
- Uygulama koruma ilkelerini oluşturduktaktan sonra, Azure AD'de onaylı uygulamalara ve UYGULAMA veri koruması gerektirmeye yönelik bir koşullu erişim kuralı oluşturarak bunları zorunlu kılınabilirsiniz.

UYGULAMA koruma ilkeleri birçok ayar içerir. Neyse ki, her ayarı öğrenmeniz ve seçenekleri değerlendirmeniz gerek yok. Microsoft, başlangıç noktaları önererek ayarların yapılandırmasını uygulamayı kolaylaştırır. Uygulama [koruma ilkelerini kullanan Veri koruma çerçevesi](/mem/intune/apps/app-protection-framework) üç düzey içerir.

Microsoft daha da iyisi, bu uygulama koruma çerçevesini bir koşullu erişim kümesi ve ilgili ilkelerle eşgüdüm sağlar. Tüm kuruluşların başlangıç noktası olarak kullanmalarını öneririz. Bu makaledeki kılavuzu kullanarak MFA'ya ulaştıysanız, burada yarıdasiniz!

Mobil uygulama korumasını yapılandırmak için, Ortak kimlik ve cihaz [erişimi ilkeleri'nin kılavuzu kullanın](./office-365-security/identity-access-policies.md):

 1. iOS [ve Android için ilkeler oluşturmak](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) için UYGULAMA veri koruma ilkeleri uygulama kılavuzuna kullanın. Taban çizgisi koruması için Düzey 2 (gelişmiş veri koruması) önerilir.
 2. Onaylanmış uygulamalar ve UYGULAMA koruması [gerektirmek için koşullu erişim kuralı oluşturun](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: Intune mobil uygulama koruması da içinde olmak üzere konuklar için MFA'yi ve koşullu erişimi yapılandırma

Bundan sonra, işbirliğine devam etmek ve konuklarla birlikte çalışmaya devam etmek istiyorum. Uygulama planını kullanıyorsanız ve Microsoft 365 E3 için MFA'ya çıktıysanız, hazır olursanız.

Microsoft 365 E5 planını kullanıyorsanız ve risk tabanlı MFA için Azure Kimlik Koruması'nın avantajını kullanıyorsanız, birkaç ayar yapma gerekir (Azure AD Identity protection konuklara genişletilemmektedir):

- Konuklar ve dış kullanıcılar için her zaman MFA gerektiren yeni bir koşullu erişim kuralı oluşturun.
- Konukları ve dış kullanıcıları dışlamak için risk tabanlı MFA koşullu erişim kuralını güncelleştirin.

Konuk erişiminin Azure [AD ile nasıl](./office-365-security/identity-access-policies-guest-access.md) çalıştığını anlamak ve etkilenen ilkeleri güncelleştirmek için, konuk ve dış erişime izin vermek ve bu erişimi korumak için ortak ilkeleri güncelleştirme konusunda kılavuzu kullanın.

Oluşturduğunuz Intune mobil uygulama koruma ilkeleri ile birlikte, onaylanan uygulamalar ve UYGULAMA koruması gerektirmeye yönelik koşullu erişim kuralı, konuk hesaplarına uygulanır ve kuruluş verilerinizin korunmasına yardımcı olur.

> [!NOTE]
> Bilgisayarları uyumlu bilgisayarlar gerektirmek için cihaz yönetimine zaten kaydettiysinizse, cihaz uyumluluğunu zorunlu kılacak koşullu erişim kuralından konuk hesaplarını da hariç tutabilirsiniz.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: Bilgisayarları cihaz yönetimine kaydettirin ve uyumlu bilgisayarlar gerektirir

İş gücünüzün cihazlarını kaydetmek için çeşitli yöntemler vardır. Her yöntem cihazın sahipliğine (kişisel veya kurumsal), cihaz türüne (iOS, Windows, Android) ve yönetim gereksinimlerine (sıfırlamalar, yakınlık, kilitleme) bağlıdır. Bu biraz zaman alıp sıralanmış olabilir. Bkz[. Cihazları mobil cihazlarında Microsoft Intune](/mem/intune/enrollment/).

Devam etmek için en hızlı yol, Windows 10 [ayarlamaktır](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Bu öğreticilerden de faydalanamazsanız:

- [Intune'da otomatik Windows için AutoPilot'u kullanma](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [iOS/iPadOS cihazlarını Intune'a kaydetmek için Apple Business Manager'da (ABM) Apple Kurumsal Cihaz Kaydı özelliklerini kullanma](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Cihazları kaydettikten sonra, Bu ilkeleri oluşturmak için [Ortak kimlik ve cihaz erişimi ilkeleri'nin](./office-365-security/identity-access-policies.md) kılavuzu kullanın:

- [Cihaz uyumluluğu ilkelerini tanımlama](./office-365-security/identity-access-policies.md#define-device-compliance-policies) — Virüsten koruma gerektirmeyi de içeren Windows 10 için önerilen ayarlar. Cihaz kullanıyorsanız Microsoft 365 E5 cihazlarının durumunu izlemek üzere Uç Nokta için Microsoft Defender'ı kullanın. Diğer işletim sistemlerinin uyumluluk ilkelerinin virüsten koruma ve son nokta koruma yazılımı olduğundan emin olun.
- [Uyumlu bilgisayar gerektir](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) — Bu, Azure AD'de cihaz uyumluluğu ilkelerini zorunlu bulunduran koşullu erişim kuralıdır.

Bir cihazı yalnızca bir kuruluş yönetebilir, bu nedenle konuk hesaplarını Azure AD'de koşullu erişim kuralından dışlayın. Konuk ve dış kullanıcıları cihaz uyumluluğu gerektiren ilkeler dışında tutamazsanız, bu ilkeler bu kullanıcıları engelleyebilir. Daha fazla bilgi için bkz [. Konuk ve dış erişime izin vermek ve korumak için ortak ilkeleri güncelleştirme](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: Anızı bulut bağlantısı için en iyi duruma getirme

Çalışanlarınızı toplu olarak evden çalışmaya hızlı bir şekilde etkinleştiriyorsanız, bu anlılı bağlantı düzenleri geçişini kurumsal ağ altyapısı üzerinde önemli bir etkisi olabilir. Birçok ağ ölçeklendirildi ve bulut hizmetleri benimsenmeden önce tasarlanmıştır. Birçok durumda, ağlar uzak çalışanlarına karşıttır, ancak aynı anda tüm kullanıcılar tarafından uzaktan kullanılmak üzere tasarlanmadı.

VPN karşıtlığı, merkezi ağ çıkış donanımı (örneğin,x'ler ve veri kaybı önleme cihazları), merkezi internet bant genişliği, backhaul MPLS devreleri, NAT özelliği gibi ağ öğeleri, bunları kullanan tüm işletmenin yükünden dolayı aniden inanılmaz bir yük altında olur. Sonuçta, evden çalışmaya uyarlan kullanıcılar için düşük bir kullanıcı deneyimiyle birlikte düşük performans ve verimlilik elde edildi.

Geleneksel olarak sağlanan korumalardan bazıları, kullanıcılarınıza erişen bulut uygulamaları tarafından trafiği şirket ağına geri yönlendirme yoluyla sağlanır. Bu makalede bu adıma ulaştıysanız, veri ve hizmetleri için gelişmiş bulut güvenlik denetimleri Microsoft 365 uygulanmıştır. Bu denetimler yerine sahip olduğunda, uzak kullanıcıların trafiğini doğrudan bu denetimlere yönlendirmeye Office 365. Diğer uygulamalara erişim için yine de VPN bağlantısına ihtiyaç ediyorsanız, bölünmüş bölme uygulayarak performansınızı ve kullanıcı deneyimini önemli ölçüde geliştirebilirsiniz. Organizasyonda anlaşma sağladıktan sonra, bunu bir gün içinde iyi koordine bir ağ ekibi gerçekleştirebilirsiniz.

Daha fazla bilgi için Belgeler'de şu kaynaklara bakın:

- [Genel bakış: VPN bölünmüş şifreleme kullanarak uzak kullanıcılar için bağlantıları en iyi duruma getirme](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [VPN bölmeli bölme Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Bu konudaki en son blog makaleleri:

- [Uzak personel için trafiği hızlı bir şekilde iyileştirme & altyapı üzerindeki yükü azaltma](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: Kullanıcıları eğitin

Eğitim kullanıcıları, kullanıcılarınızı ve güvenlik işlemleri ekibinizi çok fazla zaman ve sıkıntıdan kurtarabilir. Meraklı kullanıcıların ekleri açma veya şüpheli e-posta iletilerinden bağlantılara tıklama olasılığı daha düşük ve şüpheli web sitelerinden kaçınma olasılığı daha düşük olur.

Harvard Harvard School [Cybersecurity Campaign El](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) Kitabı, kullanıcıları kimlik avı saldırılarını belirlemeye yönelik eğitim de dahil olmak üzere, organizasyonu dahilinde güvenlik farkındalığı konusunda güçlü bir güvenlik kültürü kurma konusunda mükemmel rehberlik sağlar.

Microsoft 365, kullanıcıları bilgilendirmeye yardımcı olmak için aşağıdaki kaynakları sağlar:

****

|Kavram|Kaynaklar|
|---|---|
|Microsoft 365|[Özelleştirilebilir öğrenme yolları](/office365/customlearning/) <p>Bu kaynaklar, kurumda son kullanıcılar için eğitim bir araya çalışmanıza yardımcı olabilir|
|Microsoft 365 güvenliği|[Learning: Yerleşik ve akıllı güvenlik ile kuruluş güvenliğinizi Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Bu modül, güvenlik özelliklerinin Microsoft 365 birlikte nasıl olduğunu açıklamaya ve bu güvenlik özelliklerinin avantajlarını açıklamaya olanak sağlar.|
|Çok faktörlü kimlik doğrulaması|[İki aşamalı doğrulama: Ek doğrulama sayfası nedir?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Bu makale, son kullanıcıların çok faktörlü kimlik doğrulamasının ne olduğunu ve bu kimlik doğrulamanın neden kuruluşta kullanılıyor olduğunu anlıyoruz.|
|

Bu kılavuzun yanı sıra, Microsoft kullanıcılarınızı bu makalede açıklanan eylemleri gerçekleştirler: Hesaplarınızı ve cihazlarınızı bilgisayar korsanlarından ve kötü amaçlı [yazılımdan koruyun](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Bu eylemler şunlardır:

- Güçlü parolalar kullanma
- Cihazları koruma
- Mac bilgisayarlarda ve Windows 10 özelliklerini etkinleştirme (unmanaged cihazlar için)

Microsoft ayrıca, aşağıdaki makalelerde önerilen eylemleri gerçekleştirerek kullanıcıların kişisel e-posta hesaplarını korumalarını da önerir:

- [Outlook.com e-posta adresinizin korunmasına yardımcı olun](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [2 aşamalı doğrulama ile Gmail hesabınızla koruma](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Bulut Uygulamaları için Microsoft Defender ile çalışmaya başlama

[Bulut Uygulamaları için Microsoft Defender](/cloud-app-security) zengin görünürlük, veri seyahati üzerinde denetim ve tüm bulut hizmetleriniz genelinde siber tehditlere karşı mücadele etmek için gelişmiş analiz sağlar. Bulut Uygulamaları için Defender'ı başlattıktan sonra anormal algılama ilkeleri otomatik olarak etkinleştirilir, ancak Bulut Uygulamaları için Defender'ın, tüm anormal algılama uyarılarının yükseltilma başladığı yedi günlük bir başlangıç öğrenme süresi vardır.

Bulut Uygulamaları için Defender ile çalışmaya hemen başlandı. Daha sonra daha gelişmiş izleme ve denetimler kurabilirsiniz.

- [Hızlı Başlangıç: Bulut Uygulamaları için Defender ile çalışmaya başlama](/cloud-app-security/getting-started-with-cloud-app-security)
- [Anında davranış analizi ve anormal algılamayı edinin](/cloud-app-security/anomaly-detection-policy)
- [Bulut Uygulamaları için Microsoft Defender hakkında daha fazla bilgi edinin](/cloud-app-security/what-is-cloud-app-security)
- [Yeni özellikleri ve özellikleri gözden geçirme](/cloud-app-security/release-notes)
- [Temel kurulum yönergelerine bakın](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Tehditleri izleme ve önlem alma

Microsoft 365, durumu izlemek ve uygun eylemleri yapmak için çeşitli yollar içerir. En iyi başlangıç <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender, kuruluş</a> [Microsoft](./defender/microsoft-secure-score.md) Güvenli Puanı'nın ve dikkat gerektiren tüm uyarıların veya varlıkların görüntü geçitleri portalıdır.

- [Microsoft 365 Defender portalını Microsoft 365 Defender başlama](./defender/microsoft-365-defender.md#the-microsoft-365-defender-portal)
- [Portallarda güvenlik portallarına Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler! En önemli güvenlik korumalarından bazılarını hızlı bir şekilde uygulamaya başladınız ve organizasyonunız çok daha güvenli. Artık tehdit koruması özellikleriyle (Uç Nokta için Microsoft Defender dahil), veri sınıflandırma ve koruma özellikleriyle ve yönetim hesaplarının güvenliğini sağlamada daha da ileri bir yere hazırsınız. Daha derin ve yöntemsel bir güvenlik önerileri kümesi için bkz. Microsoft 365 karar vericiler [için Microsoft 365 Güvenliği (BDM)](Microsoft-365-security-for-bdm.md).

Ayrıca Microsoft'un Yeni BuluttaKimlik Defender'ı [da docs.microsoft.com/security](/security).
