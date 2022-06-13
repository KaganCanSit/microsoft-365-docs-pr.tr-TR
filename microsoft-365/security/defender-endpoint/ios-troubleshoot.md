---
title: Sorunları giderme ve iOS Uç Nokta için Microsoft Defender ile ilgili SSS'lerde yanıtlar bulma
description: Sorun giderme ve SSS - iOS'da Uç Nokta için Microsoft Defender
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, sorun giderme, SSS, nasıl yapılır
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ae6e65d99a82bdf4a9c0adbb740c6e5b969f4b68
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016338"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Sorunları giderme ve iOS Uç Nokta için Microsoft Defender hakkında SSS yanıtlarını bulma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konuda, iOS Uç Nokta için Microsoft Defender kullanırken ortaya çıkabilecek sorunları gidermenize yardımcı olacak sorun giderme bilgileri sağlanır.

> [!NOTE]
> iOS'da Uç Nokta için Defender, Web Koruması özelliğini sağlamak için bir VPN kullanır. Bu normal bir VPN değildir ve cihazın dışına trafiği almayan yerel/kendi kendini döngüye alan bir VPN'dir.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>VPN açıkken uygulamalar çalışmıyor
Etkin bir VPN algılandığında çalışmayı durduran bazı uygulamalar vardır. Bu tür uygulamaları kullanırken VPN'i devre dışı bırakabilirsiniz.

Varsayılan olarak, iOS'da Uç Nokta için Defender web koruma özelliğini içerir ve etkinleştirir. [Web koruması](web-protection-overview.md) , cihazların web tehditlerine karşı korunmasına ve kullanıcıların kimlik avı saldırılarına karşı korunmasına yardımcı olur. iOS'da Uç Nokta için Defender, bu korumayı sağlamak için bir VPN kullanır. Bunun yerel bir VPN olduğunu ve geleneksel VPN'in aksine ağ trafiğinin cihazın dışına gönderilmediğini unutmayın.

Varsayılan olarak etkinleştirildiğinde VPN'yi devre dışı bırakmanızı gerektiren bazı durumlar olabilir. Örneğin, VPN yapılandırıldığında çalışmayan bazı uygulamaları çalıştırmak istiyorsunuz. Böyle durumlarda VPN'i doğrudan Uç Nokta için Defender uygulamasından veya aşağıdaki adımları kullanarak devre dışı bırakabilirsiniz:

1. iOS cihazınızda **Ayarlar** uygulamasını açın, **Genel'e** ve ardından **VPN'e** tıklayın veya dokunun.
1. Uç Nokta için Microsoft Defender için "i" düğmesine tıklayın veya dokunun.
1. VPN'yi devre dışı bırakmak için **İsteğe Bağlı Bağlan** kapatın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="İsteğe bağlı Bağlan seçeneği" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> VPN devre dışı bırakıldığında Web Koruması kullanılamaz. Web Koruması'nı yeniden etkinleştirmek için cihazda Uç Nokta için Microsoft Defender uygulamasını açın ve Web Korumasını Etkinleştir'i seçin.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Birden çok VPN profiliyle birlikte bulunma

Apple iOS, **cihaz genelinde** birden fazla VPN'in aynı anda etkin olmasını desteklemez. Cihazda birden çok VPN profili bulunabilir ancak aynı anda yalnızca bir VPN etkin olabilir. Cihazda başka bir VPN kullanmanız gerekiyorsa, diğer VPN'yi kullanırken Uç Nokta VPN için Defender'ı devre dışı bırakabilirsiniz.

## <a name="battery-consumption"></a>Pil tüketimi

Web tabanlı tehditlere karşı size her zaman koruma sağlamak için Uç Nokta için Microsoft Defender her zaman arka planda çalışması gerekir. Bu, cihazınızın genel pil tüketiminde küçük bir artışa yol açabilir. Pilin önemli ölçüde tükenmesi ihtimaline karşı lütfen [bize geri bildirim gönderin](ios-troubleshoot.md#send-in-app-feedback) , biz de araştıralım.

Ayrıca Ayarlar uygulamasında iOS yalnızca belirli bir süre boyunca kullanıcıya görünen uygulamaların pil kullanımını gösterir. Ekranda gösterilen uygulamalar tarafından pil kullanımı yalnızca bu süre için geçerlidir ve CPU ve Ağ kullanımı gibi çok sayıda faktöre göre iOS tarafından hesaplanır. Uç Nokta için Microsoft Defender, kötü amaçlı web siteleri veya bağlantıların web trafiğini denetlemek için arka planda yerel/geri döngü VPN kullanır. Herhangi bir uygulamadan gelen ağ paketleri bu denetimden geçer ve bu da Uç Nokta için Microsoft Defender pil kullanımının yanlış hesaplanmasına neden olur. Uç Nokta için Microsoft Defender gerçek pil tüketimi, cihazdaki Pil Ayarlar sayfasında gösterilenden daha azdır.

Kullanılan VPN'nin yerel bir VPN olduğunu ve geleneksel VPN'nin aksine ağ trafiğinin cihazın dışına gönderilmediğini unutmayın.

## <a name="data-usage"></a>Veri kullanımı

Uç Nokta için Microsoft Defender, kötü amaçlı web siteleri veya bağlantıların web trafiğini denetlemek için yerel/geri döngü VPN'i kullanır. Bu nedenle, Uç Nokta için Microsoft Defender veri kullanımı yanlış bir şekilde hesaba eklenebilir. Ayrıca cihaz yalnızca hücresel ağdaysa hizmet sağlayıcısı tarafından bildirilen veri kullanımının gerçek tüketime çok yakın olduğunu, ancak Ayarlar uygulamasında sayıların yanlış olabileceğini de gözlemledik.

Diğer VPN hizmetleriyle de benzer gözlemlerimiz var.

Ayrıca, daha iyi koruma sağlamak için Uç Nokta için Microsoft Defender arka uç hizmetlerimizle güncel olması kritik öneme sahiptir.

## <a name="report-unsafe-site"></a>Güvenli olmayan siteyi bildir

Kimlik avı web siteleri, kişisel veya finansal bilgilerinizi almak için güvenilir web sitelerini taklit ediyor. Kimlik avı sitesi olabilecek bir web sitesini bildirmek için [Ağ koruması hakkında geri bildirim sağlayın](https://www.microsoft.com/wdsi/support/report-unsafe-site) sayfasını ziyaret edin.

## <a name="malicious-site-detected"></a>Kötü amaçlı site algılandı

Uç Nokta için Microsoft Defender sizi kimlik avına veya diğer web tabanlı saldırılara karşı korur. Kötü amaçlı bir site algılanırsa bağlantı engellenir ve kuruluşun Microsoft 365 Defender portalına bir uyarı gönderilir. Uyarı, bağlantının etki alanı adını, uzak IP adresini ve cihaz ayrıntılarını içerir.

Ayrıca, iOS cihazda bir bildirim gösterilir. Bildirime dokunulduğunda, kullanıcının ayrıntıları gözden geçirmesi için aşağıdaki ekran açılır.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Güvenli olmayan bildirim olarak bildirilen site" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Cihaz eklendikten sonra Uç Nokta için Defender konsolunda görünmüyor

Eklendikten sonra cihazın Uç Nokta için Defender güvenlik konsolundaki Cihaz envanterinde görünmesi birkaç saat sürer. Ayrıca cihazın Azure Active Directory doğru şekilde kaydedildiğinden ve cihazın İnternet bağlantısı olduğundan emin olun. Ekleme işleminin başarılı olması için cihazın Microsoft Authenticator veya Intune Şirket Portalı aracılığıyla kaydedilmesi ve kullanıcının Azure AD kayıtlı olduğu hesabı kullanarak oturum açması gerekir.

> [!NOTE]
> Bazen cihaz adı, Microsoft Endpoint Manager (Intune) konsolunda bu adla tutarlı değildir. Uç Nokta için Defender konsolundaki cihaz adı, <username_iPhone/iPad model> biçimindedir. Uç Nokta için Defender konsolunda cihazı tanımlamak için Azure AD cihaz kimliğini de kullanabilirsiniz.

## <a name="data-and-privacy"></a>Veri ve Gizlilik

Toplanan veriler ve gizlilik hakkında ayrıntılı bilgi için bkz. [Gizlilik Bilgileri - iOS'da Uç Nokta için Microsoft Defender](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Hücresel ağda bağlantı sorunu

Hücresel ağda İnternet bağlantısı sorunlarıyla karşılaşıyorsanız, Uç Nokta için Microsoft Defender hücresel verinin etkinleştirilip etkinleştirilmediğini denetleyin: MS Defender > Ayarlar uygulamasını açın > MS Defender için "Hücresel veri" özelliğinin etkinleştirildiğinden emin olun.

Hala bağlantı sorunlarınız varsa Uçak modunu açma/kapatmanın sorunu çözmenize yardımcı olup olmadığını denetleyin. Sorun devam ederse [günlükleri bize gönderin](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>İçerik filtresi profilinin yüklü olduğu denetimli cihazlarda sorunlar

Uç Nokta için Defender içerik filtresinin yüklü olduğu denetimli cihazlarda bir sorun var. Bu tür cihazlarda İnternet bağlantısında yavaşlık veya gecikme olduğunu gözlemlerseniz, içerik filtresi profilini cihazdan kaldırın veya silin. Bu sorunu çözmek için çalışıyoruz ve bir çözüm buldukta burayı güncelleştireceğiz. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Uygulama mağazasından uygulama güncelleştirmeleri sırasında karşılaşılan sorunlar

Uygulama mağaza üzerinden güncelleştirildiğinde (otomatik güncelleştirmeler veya el ile güncelleştirmeler) sorunları gözlemlerseniz, cihazı yeniden başlatmanız gerekebilir. Bu işlem sorunu çözmezse Defender VPN'i devre dışı bırakabilir ve uygulama güncelleştirmesini gerçekleştirebilirsiniz. Bu sorunu bildirmek için uygulama içi geri bildirim de sağlayabilirsiniz.

## <a name="send-in-app-feedback"></a>Uygulama içi geri bildirim gönderme

Bir kullanıcı yukarıdaki bölümlerde henüz ele alınmamış bir sorunla karşılaşıyorsa veya listelenen adımları kullanarak çözülemiyorsa, kullanıcı tanılama verileriyle birlikte uygulama içi geri bildirim sağlayabilir. Ekibimiz daha sonra doğru çözümü sağlamak için günlükleri araştıracaktır. Kullanıcılar geri bildirim göndermek için aşağıdaki adımları kullanabilir:

- iOS/iPadOS cihazında MSDefender uygulamasını açın.
- Sol üst köşedeki Menü'ye (profil simgesi) dokunun.
- **Geri Bildirim Gönder'e** dokunun.
- Verilen seçenekler arasından seçim yapın. Bir sorunu bildirmek için Bir **şeyi beğenmedim'i** seçin.
- Karşılaştığınız sorunun ayrıntılarını sağlayın ve **Tanılama verilerini gönder'i** işaretleyin. Ekibin bir çözüm veya takip için sizinle iletişim kurabilmesi için e-posta adresinizi eklemenizi öneririz.
- Geri bildirimi başarıyla göndermek için **Gönder'e** dokunun.
