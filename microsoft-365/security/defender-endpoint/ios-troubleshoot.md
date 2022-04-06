---
title: iOS'ta karşılaşılan sorunlar ile ilgili sorunları giderin ve SSS Uç Nokta için Microsoft Defender bulun
description: Sorun giderme ve SSS - iOS Uç Nokta için Microsoft Defender sorunları giderme
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, sorun giderme, s, nasıl gönderilir
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
ms.openlocfilehash: bc8cda3fb61ec9338b95eed58f5f0a70e1deb3e1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469371"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>iOS'ta sorunları giderme ve SSS'Uç Nokta için Microsoft Defender yanıt bulma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konu başlığı altında, iOS'ta iOS'ta e-posta kullanımınız devam e Uç Nokta için Microsoft Defender e yardımcı olacak sorun giderme bilgileri yer sağlar.



> [!NOTE]
> iOS'ta Uç Nokta için Defender, Web Koruma özelliğini sağlamak için VPN kullanıyor olabilir. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>VPN açıkken uygulamalar çalışmıyor
Etkin bir VPN algılandığında çalışması durduran bazı uygulamalar vardır. Bu tür uygulamaları kullanırken VPN'yi devre dışı abilirsiniz. 

Varsayılan olarak, iOS'ta Uç Nokta için Defender web koruma özelliğini içerir ve sağlar. [Web koruması,](web-protection-overview.md) cihazların web tehditlerine karşı güvenliğini korumaya ve kullanıcıları kimlik avı saldırılarından korumaya yardımcı olur. iOS'ta Uç Nokta için Defender bu korumayı sağlamak için VPN kullanır. Bunun yerel bir VPN olduğunu ve geleneksel VPN'den farklı olarak ağ trafiğinin cihazın dışına gönderilme olmadığını unutmayın.

Varsayılan olarak etkin durumdayken VPN'yi devre dışı bırakmanızı gerektiren bazı durumlar olabilir. Örneğin, VPN yapılandırıldığında çalışmayan bazı uygulamaları çalıştırmak istiyor olun. Böyle durumlarda, VPN'yi doğrudan Uç Nokta için Defender uygulamasından veya aşağıdaki adımları kullanarak devre dışı bırakmayı seçebilirsiniz:

1. iOS aygıtınızda, **Genel'e ve Ayarlar** **VPN'ye** tıklayın **veya** dokunun.
1. "i" düğmesine tıklayarak veya dokunarak Uç Nokta için Microsoft Defender.
1. VPN'yi devre **Bağlan için On Demand özelliğini** kapatın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="isteğe Bağlan seçeneği" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> VPN devre dışı bırakılmıştır, Web Koruması kullanılamaz. Web Korumasını yeniden etkinleştirmek için, Uç Nokta için Microsoft Defender Web Korumasını Etkinleştir'i açın.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Birden çok VPN profiliyle birlikte yer

Apple iOS, aynı anda etkin **olmak için cihaz** genelinde birden çok VPN'i desteklemez. Cihazda birden çok VPN profili mevcut olabilir ama aynı anda yalnızca bir VPN etkin olabilir. Cihazda başka bir VPN kullanmak zorundaysanız, diğer VPN'yi kullanırken Uç Nokta VPN için Defender'ı devre dışı abilirsiniz.

## <a name="battery-consumption"></a>Pil tüketimi

Web tabanlı tehditlere karşı size tüm zaman koruma sağlamak için, Uç Nokta için Microsoft Defender zaman arka planda çalışması gerekir. Bu, cihazınızın genel pil tüketiminde küçük bir artışa yol açabilir. Pil pil gücünde önemli bir şey görüyor olurken lütfen [bize geri bildirim gönderin.](ios-troubleshoot.md#send-in-app-feedback) Biz de incelemeye devam ederiz.

Ayrıca, Ayarlar uygulamasında iOS yalnızca belirli bir süre boyunca kullanıcının görebilir olduğu uygulamaların pil kullanımını gösterir. Ekranda gösterilen uygulamaların pil kullanımı yalnızca bu süre boyunca kullanılabilir ve CPU ve Ağ kullanımı gibi çok sayıda faktöre bağlı olarak iOS tarafından hesaplanır. Uç Nokta için Microsoft Defender kötü amaçlı web siteleri veya bağlantılar için web trafiğini kontrol etmek için arka planda yerel/geri döngülü bir VPN kullanır. Herhangi bir uygulamanın ağ paketleri bu denetimden geçerek pil kullanımının Uç Nokta için Microsoft Defender yanlış hesaplandı. Gerçek pil tüketimi Uç Nokta için Microsoft Defender pil tüketimi, cihazda Pil ve Ayarlar sayfasında gösterilenden daha azdır.

Kullanılan VPN'nin yerel bir VPN olduğunu ve geleneksel VPN'den farklı olarak ağ trafiğinin cihazın dışına gönderilme olmadığını unutmayın.

## <a name="data-usage"></a>Veri kullanımı

Uç Nokta için Microsoft Defender kötü amaçlı web siteleri veya bağlantılar için web trafiğini kontrol etmek için yerel/geri dönüş VPN kullanır. Bu nedenle, Uç Nokta için Microsoft Defender kullanımı yanlış hesap olabilir. Ayrıca, cihaz yalnızca cep telefonu ağına bağlı olduğu zaman hizmet sağlayıcı tarafından bildirilen veri kullanımının gerçek tüketimine çok yakın olduğunu, Apple'ın ise Ayarlar uygulamasında yaklaşık 1,5x ile 2x gerçek veri kullanımına yakın olduğunu gözlemledık.

Diğer VPN hizmetleriyle benzer gözlemlerimiz var ve bunu Apple'a bildirdik.

Buna ek olarak, daha iyi Uç Nokta için Microsoft Defender sağlamak için arka uç hizmetlerimizle güncel olması önemlidir.

## <a name="report-unsafe-site"></a>Güvenli olmayan siteyi bildirme

Kimlik avı web siteleri, kişisel veya finansal bilgilerinizi almak için güvenilir web siteleri kimliğine bürünüler. Kimlik avı [sitesi olabilir bir web sitesini rapor](https://www.microsoft.com/wdsi/support/report-unsafe-site) etmek için Ağ koruması hakkında geri bildirim sağlama sayfasını ziyaret edin.

## <a name="malicious-site-detected"></a>Kötü amaçlı site algılandı

Uç Nokta için Microsoft Defender kimlik avı veya diğer web tabanlı saldırılara karşı sizi korur. Kötü amaçlı bir site algılanırsa, bağlantı engellenir ve kuruluşun posta portalına bir uyarı Microsoft 365 Defender. Uyarı bağlantının etki alanı adını, uzak IP adresini ve cihaz ayrıntılarını içerir.

Buna ek olarak, iOS cihazında bir bildirim gösterilir. Bildirime dokunulduğunda, kullanıcının ayrıntıları gözden geçirmesi için aşağıdaki ekran açılır.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Sitenin güvenli olmayan bildirim olarak raporlandığı" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Cihaz, ekleme sonrasında Uç nokta konsolu için Defender'da görülems.

Eklemeden sonra, cihazın Uç nokta için Defender güvenlik konsolunda Cihaz envanteri'nin içinde yer alan bir uygulamanın gösterilesi birkaç saat sürer. Ayrıca, her cihazda İnternet bağlantısı olduğundan ve Azure Active Directory ile doğru kaydedildikten emin olun. Başarılı bir şekilde işe alım için cihazın Microsoft Authenticator veya Intune Şirket Portalı ile kaydedilmiş olması ve kullanıcının, Azure AD'ye kayıtlı cihazın hesabıyla oturum açması gerekir.

> [!NOTE]
> Bazen, cihaz adı Microsoft Endpoint Manager (Intune) konsolda bu adla tutarlı değildir. Uç nokta konsolu için Defender'daki cihaz adı, <username_iPhone/iPad biçimidir>. Cihazı Uç nokta konsolu için Defender'da tanımlamak için Azure AD cihaz kimliğini de kullanabilirsiniz.

## <a name="data-and-privacy"></a>Veri ve Gizlilik

Toplanan veriler ve gizlilik hakkında ayrıntılı bilgi için bkz. [iOS'ta Uç Nokta için Microsoft Defender Bilgileri.](ios-privacy.md)

## <a name="connectivity-issue-on-cellular-network"></a>Cep telefonu şebekesi üzerinde bağlantı sorunu

Hücresel ağ üzerinde İnternet bağlantısı sorunlarıyla karşı karşıyaysanız, Uç Nokta için Microsoft Defender'de hücresel verinin etkinleştirildiğinden emin olun: MS Defender için Ayarlar uygulamasını > MS Defender > için "Hücresel veri" etkinleştirildiğinden emin olun.

Bağlantı sorunlarınız devam ediyorsa Uçak modunu açma/kapatmanın sorunu çözmenize yardımcı olup yardımcı olup denetleyin. Sorun devam ederse bize [günlük gönderin](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>İçerik filtresi profili yüklü olan denetlenen cihazlarda sorunlar

Denetlenen cihazlarda Uç nokta için Defender içerik filtresinin yüklü olduğu bir sorun vardır. Bu tür cihazlarda internet bağlantısında yavaşlık veya gecikme gözlemlersiniz, cihazdan içerik filtresi profilini kaldırın veya silin. Bu sorunu çözmek için çalışıyoruz ve çözüme varktan sonra bu yeri güncelleştireceğiz. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Uygulama mağazasından yapılan uygulama güncelleştirmeleri sırasında karşılaşılan sorunlar

Uygulama mağaza aracılığıyla güncelleştirildiğinde sorun gözlemlersiniz (otomatik güncelleştirmeler veya el ile güncelleştirmeler), cihazı yeniden başlatmanız gerekir. Bu işlem sorunu çözmezse Defender VPN'yi devre dışı bırakarak uygulama güncelleştirmesini gerçekleştirebilirsiniz. Bu sorunu rapor etmek için uygulama içinde geri bildirim de sebilirsiniz.

## <a name="send-in-app-feedback"></a>Uygulama içinde geri bildirim gönderme

Kullanıcı yukarıdaki bölümlerde henüz çözüme ulaşamayan veya listelenen adımların kullanamadığı bir sorunla karşı karşıya geliyorsa, kullanıcı tanılama verileriyle birlikte uygulama içinde geri bildirim de sağlar. Bundan sonra ekibimiz doğru çözümü sağlamak için günlükleri araştıracak. Kullanıcılar geri bildirim göndermek için aşağıdaki adımları kullanabilir:

  - iOS/iPadOS cihazında MSDefender uygulamasını açın.
  - Sol üst köşedeki Menü (profil simgesi) öğesine dokunun.
  - Geri Bildirim **Gönder'e dokunun**.
  - Verilen seçeneklerden birini belirleyin. Sorun bildirmek için Bir **şeyi istemiyorum'ı seçin**.
  - Karşılaştığınız sorunun ayrıntılarını iletin ve Tanılama verileri **gönder'i seçin**. Ekibin çözüm veya takip için size başvuramalarını için e-posta adresinizi de dahil etmenizi öneririz.
  - Geri **bildirimi başarıyla** göndermek için Gönder'e dokunun.
