---
title: iOS'da Uç Nokta için Microsoft Defender için uygulama tabanlı dağıtım
ms.reviewer: ''
description: Uygulama kullanarak iOS'da Uç Nokta için Microsoft Defender dağıtmayı açıklar
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, uygulama, yükleme, dağıtma, kaldırma, intune
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
ms.openlocfilehash: 4a81f125f9f32a5b4bdafd6d4656699fa17caa82
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669980"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>Uç Nokta için Microsoft Defender iOS dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu konuda, kayıtlı Intune Şirket Portalı cihazlarda uç nokta için Defender'ın iOS dağıtılması açıklanmaktadır. Intune cihaz kaydı hakkında daha fazla bilgi için bkz[. iOS/iPadOS cihazlarını Intune kaydetme](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>Başlamadan önce

- [Microsoft Endpoint Manager yönetim merkezine](https://go.microsoft.com/fwlink/?linkid=2109431) erişiminiz olduğundan emin olun.

- Kullanıcılarınız için iOS kaydın yapıldığından emin olun. Kullanıcıların iOS'de Uç Nokta için Defender'ı kullanabilmeleri için atanmış bir Uç Nokta için Defender lisansına sahip olması gerekir. [Lisans atama yönergeleri için Bkz. Kullanıcılara](/azure/active-directory/users-groups-roles/licensing-groups-assign) lisans atama.

> [!NOTE]
> iOS Uç Nokta için Microsoft Defender [Apple App Store'nde](https://aka.ms/mdatpiosappstore) kullanılabilir.

## <a name="deployment-steps"></a>Dağıtım adımları

uç nokta için Defender'ı Intune Şirket Portalı aracılığıyla iOS'da dağıtın.

### <a name="add-ios-store-app"></a>iOS mağazası uygulaması ekleme

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar** ->  **iOS/iPadOS** -> **Ekle** ->  **iOS mağaza uygulaması'na** gidin ve **Seç'e** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-1.png" alt-text="Microsoft Endpoint Manager Yönetici Merkezi'ndeki Uygulama ekle sekmesi" lightbox="images/ios-deploy-1.png":::

1. **Uygulama ekle** sayfasında App Store **ara'ya** tıklayın ve arama çubuğuna **Uç Nokta için Microsoft Defender** yazın. Arama sonuçları bölümünde *Uç Nokta için Microsoft Defender* ve **Seç'e** tıklayın.

1. En düşük işletim sistemi olarak **iOS 11.0'ı** seçin. Uygulama hakkındaki diğer bilgileri gözden geçirin ve **İleri'ye** tıklayın.

1. **Atamalar** bölümünde **Gerekli** bölümüne gidin ve **Grup ekle'yi** seçin. Ardından, iOS uygulamada Uç Nokta için Defender'ı hedeflemek istediğiniz kullanıcı gruplarını seçebilirsiniz. **Seç'e** ve ardından **İleri'ye** tıklayın.

    > [!NOTE]
    > Seçilen kullanıcı grubu kayıtlı Intune kullanıcıdan oluşmalıdır.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-2.png" alt-text="Microsoft Endpoint Manager Yönetici Merkezi'ndeki Grup ekle sekmesi" lightbox="images/ios-deploy-2.png":::

1. *Gözden Geçir + Oluştur* bölümünde, girilen tüm bilgilerin doğru olduğunu doğrulayın ve **Oluştur'u** seçin. Birkaç dakika içinde Uç Nokta için Defender uygulaması başarıyla oluşturulmalıdır ve sayfanın sağ üst köşesinde bir bildirim gösterilmelidir.

1. Görüntülenen uygulama bilgileri sayfasındaki **İzleyici** bölümünde **Cihaz yükleme durumu'nu** seçerek cihaz yüklemesinin başarıyla tamamlandığını doğrulayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-3.png" alt-text="Cihaz yükleme durumu sayfası" lightbox="images/ios-deploy-3.png":::

## <a name="complete-deployment-for-supervised-devices"></a>Denetimli cihazlar için dağıtımı tamamlama

iOS uygulamasındaki Uç Nokta için Microsoft Defender, platform tarafından bu tür cihazlarda sağlanan artan yönetim özellikleri göz önünde bulundurulduğunda denetimli iOS/iPadOS cihazlarda özel bir özelliğe sahiptir. Ayrıca **cihazda yerel BIR VPN ayarlamadan** Web Koruması sağlayabilir. Bu, son kullanıcılara kimlik avı ve diğer web tabanlı saldırılardan korunmaya devam ederken sorunsuz bir deneyim sunar.

### <a name="configure-supervised-mode-via-intune"></a>denetimli modu Intune aracılığıyla yapılandırma

Ardından, bir Uygulama Yapılandırması ilkesi aracılığıyla Uç Nokta için Defender uygulamasının denetimli modunu yapılandırın.

   > [!NOTE]
   > Denetimli cihazlar için bu uygulama yapılandırma ilkesi yalnızca yönetilen cihazlar için geçerlidir ve en iyi uygulama olarak TÜM yönetilen iOS cihazlar için hedeflenmelidir.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın ve **Uygulama** \> **Uygulaması yapılandırma ilkeleri** \> **Ekle'ye** gidin. **Yönetilen cihazlar'ı** seçin.

    > [!div class="mx-imgBorder"]
    > ![Microsoft Endpoint Manager Yönetici Center4 görüntüsü.](images/ios-deploy-4.png)

1. *Uygulama yapılandırma ilkesi oluştur* sayfasında aşağıdaki bilgileri sağlayın:
    - İlke Adı
    - Platform: iOS/iPadOS'i seçin
    - Hedeflenen uygulama: Listeden **Uç Nokta için Microsoft Defender** seçin

    > [!div class="mx-imgBorder"]
    > ![Microsoft Endpoint Manager Yönetici Center5 görüntüsü.](images/ios-deploy-5.png)

1. Sonraki ekranda **Yapılandırma tasarımcısını** biçim olarak kullan'ı seçin. Aşağıdaki özelliği belirtin:
    - Yapılandırma Anahtarı: denetimli
    - Değer türü: Dize
    - Yapılandırma Değeri: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![Microsoft Endpoint Manager Yönetici Center6 görüntüsü.](images/ios-deploy-6.png)

1. **Kapsam etiketleri** sayfasını açmak için **İleri'yi** seçin. Kapsam etiketleri isteğe bağlıdır. Devam etmek için **İleri'yi** seçin.

1. **Atamalar** sayfasında, bu profili alacak grupları seçin. Bu senaryoda **, Tüm Cihazları** hedeflemek en iyi yöntemdir. Profil atama hakkında daha fazla bilgi için bkz. [Kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).

   Kullanıcı gruplarına dağıtım yaparken, ilkenin geçerli olması için bir kullanıcının cihazda oturum açması gerekir.

   **İleri**'ye tıklayın.

1. **Gözden Geçir + oluştur** sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Yeni profil, yapılandırma profilleri listesinde görüntülenir.

1. Ardından denetimli iOS cihazlarda özel bir profil dağıtmanız gerekir. Bu, gelişmiş kimlik avı önleme özellikleri içindir. Aşağıdaki adımları izleyin:

    - Yapılandırma profilini şu kaynaktan indirin: [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - **Cihazlar** ->  **iOS/iPadOS** -> **Yapılandırma profilleri** -> **Profil Oluştur'a** gidin

    > [!div class="mx-imgBorder"]
    > ![Microsoft Endpoint Manager Yönetici Center7 görüntüsü.](images/ios-deploy-7.png)
    
    - Profilin adını belirtin. Yapılandırma profili dosyasını içeri aktarmanız istendiğinde, önceki adımdan indirilen dosyayı seçin.
    - **Atama** bölümünde, bu profili uygulamak istediğiniz cihaz grubunu seçin. En iyi yöntem olarak, bu tüm yönetilen iOS cihazlara uygulanmalıdır. **İleri**'yi seçin.
    - **Gözden Geçir + oluştur** sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Yeni profil, yapılandırma profilleri listesinde görüntülenir.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>VPN profilini otomatik olarak ekleme (Basitleştirilmiş Ekleme)

Denetimsiz cihazlar için, Web Koruması özelliğini sağlamak için bir VPN kullanılır. Bu normal bir VPN değildir ve cihazın dışına trafiği almayan yerel/kendi kendini döngüye alan bir VPN'dir.

>[!NOTE]
>Denetimli cihazlar için Web Koruması özelliği için VPN gerekmez ve yöneticilerin denetimli cihazlarda bir yapılandırma profili ayarlamasını gerektirir. Denetimli cihazlar için yapılandırmak için Denetimli [cihazlar için dağıtımı tamamlama](#complete-deployment-for-supervised-devices) bölümündeki adımları izleyin.

Yöneticiler VPN profilinin otomatik kurulumunu yapılandırabilir. Bu, ekleme sırasında kullanıcının bunu yapması gerekmeden Uç Nokta için Defender VPN profilini otomatik olarak ayarlar. 

Bu adım, VPN profilini ayarlayarak ekleme işlemini basitleştirir. Sıfır dokunma veya sessiz ekleme deneyimi için sonraki bölüme bakın: [Sıfır dokunmayla ekleme](#zero-touch-onboarding-of-microsoft-defender-for-endpoint).

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** -> **Yapılandırma Profilleri** -> **Profil Oluştur'a** gidin.
1. **iOS/iPadOS** olarak **Platform** ve **VPN** olarak **Profil türü'nü** seçin. **Oluştur'a** tıklayın.
1. Profil için bir ad yazın ve **İleri'ye** tıklayın.
1. Bağlantı Türü için **Özel VPN'yi** seçin ve **Temel VPN** bölümüne aşağıdakileri girin:
    - Bağlantı Adı = Uç Nokta için Microsoft Defender
    - VPN sunucusu adresi = 127.0.0.1
    - Auth yöntemi = "Kullanıcı adı ve parola"
    - Bölünmüş Tünel = Devre Dışı Bırak
    - VPN tanımlayıcısı = com.microsoft.scmx
    - Anahtar-değer çiftlerinde **AutoOnboard** anahtarını girin ve değeri **True** olarak ayarlayın.
    - Otomatik VPN türü = İsteğe bağlı VPN
    - **İsteğe Bağlı Kurallar** için **Ekle'yi** seçin ve **aşağıdakileri yapmak istiyorum = VPN Bağlan**, **kısıtlamak istiyorum = Tüm etki alanları'nı** seçin.

    :::image type="content" source="images/ios-deploy-8.png" alt-text="VPN profili Yapılandırma ayarları sekmesi" lightbox="images/ios-deploy-8.png":::

1. İleri'ye tıklayın ve profili hedeflenen kullanıcılara atayın.
1. *Gözden Geçir + Oluştur* bölümünde, girilen tüm bilgilerin doğru olduğunu doğrulayın ve **Oluştur'u** seçin.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender sıfır dokunmayla ekleme



> [!NOTE]
> Sıfır dokunma, kullanıcı benşimi olmadan kaydedilen iOS cihazlarda (kullanıcısız cihazlar veya paylaşılan cihazlar) yapılandırılamaz.

Yöneticiler Uç Nokta için Microsoft Defender sessizce dağıtacak ve etkinleştirecek şekilde yapılandırabilir. Bu akışta yönetici bir dağıtım profili oluşturur ve kullanıcıya yüklemeyle ilgili bildirim gönderilir. Uç Nokta için Defender, kullanıcının uygulamayı açmasına gerek kalmadan otomatik olarak yüklenir. Kayıtlı iOS cihazlarda Uç Nokta için Defender'ın sıfır dokunma veya sessiz dağıtımını ayarlamak için aşağıdaki adımları izleyin:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** > **Yapılandırma Profilleri** > **Profil Oluştur'a** gidin.
1. **iOS/iPadOS** olarak **Platform** ve **VPN** olarak **Profil türü'nü** seçin. **Oluştur**’u seçin.
1. Profil için bir ad yazın ve **İleri'yi** seçin.
1. Bağlantı Türü için **Özel VPN'yi** seçin ve **Temel VPN** bölümüne aşağıdakileri girin:
    - Bağlantı Adı = Uç Nokta için Microsoft Defender
    - VPN sunucusu adresi = 127.0.0.1
    - Auth yöntemi = "Kullanıcı adı ve parola"
    - Bölünmüş Tünel = Devre Dışı Bırak
    - VPN tanımlayıcısı = com.microsoft.scmx
    - Anahtar-değer çiftlerinde **SilentOnboard** anahtarını girin ve değeri **True** olarak ayarlayın.
    - Otomatik VPN türü = İsteğe bağlı VPN
    - **İsteğe Bağlı Kurallar** için **Ekle'yi** seçin ve **aşağıdakileri yapmak istiyorum = VPN Bağlan**, **kısıtlamak istiyorum = Tüm etki alanları'nı** seçin.

    :::image type="content" source="images/ios-deploy-9.png" alt-text="VPN profili Yapılandırma sayfası" lightbox="images/ios-deploy-9.png":::

1. **İleri'yi** seçin ve profili hedeflenen kullanıcılara atayın.
1. *Gözden Geçir + Oluştur* bölümünde, girilen tüm bilgilerin doğru olduğunu doğrulayın ve **Oluştur'u** seçin.

Yukarıdaki yapılandırma tamamlandıktan ve cihazla eşitlendikten sonra, hedeflenen iOS cihazlarında aşağıdaki eylemler gerçekleştirilir:
    - Uç Nokta için Microsoft Defender dağıtılır ve sessizce eklenir ve cihaz Uç Nokta için Defender portalında görünür.
    - Kullanıcı cihazına geçici bir bildirim gönderilir.
    - Web Koruması ve diğer özellikler etkinleştirilir.

   > [!NOTE]
   > Denetimli cihazlar için VPN profili gerekli olmasa da, yöneticiler Intune aracılığıyla Uç Nokta için Defender VPN profilini yapılandırarak Sıfır dokunma eklemeyi ayarlamaya devam edebilir. VPN profili cihaza dağıtılır, ancak cihazda yalnızca geçiş profili olarak bulunur ve ilk eklemeden sonra silinebilir.

## <a name="complete-onboarding-and-check-status"></a>Eklemeyi tamamlama ve durumu denetleme

1. iOS'da Uç Nokta için Defender cihaza yüklendikten sonra uygulama simgesini görürsünüz.

    :::image type="content" source="images/41627a709700c324849bf7e13510c516.png" alt-text="Otomatik olarak oluşturulan akıllı telefon açıklaması" lightbox="images/41627a709700c324849bf7e13510c516.png":::

2. Uç Nokta için Defender uygulaması simgesine (MSDefender) dokunun ve ekleme adımlarını tamamlamak için ekrandaki yönergeleri izleyin. Ayrıntılar, uç nokta için Defender tarafından iOS gereken iOS izinlerinin son kullanıcı tarafından kabul edilmesini içerir.

3. Ekleme başarılı olursa cihaz, Microsoft 365 Defender portalındaki Cihazlar listesinde gösterilmeye başlar.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/device-inventory-screen.png" alt-text="Cihaz envanteri sayfası" lightbox="images/device-inventory-screen.png":::

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>Denetimli Mod için Uç Nokta için Microsoft Defender yapılandırma

iOS uygulamasındaki Uç Nokta için Microsoft Defender, platform tarafından bu tür cihazlarda sağlanan artan yönetim özellikleri göz önünde bulundurulduğunda denetimli iOS/iPadOS cihazlarda özel bir özelliğe sahiptir. Bu özelliklerden yararlanmak için Uç Nokta için Defender uygulamasının bir cihazın Denetimli Modda olup olmadığını bilmesi gerekir.

### <a name="configure-supervised-mode-via-intune"></a>denetimli modu Intune aracılığıyla yapılandırma

Intune, Uygulama Yapılandırması ilkesi aracılığıyla iOS için Defender uygulamasını yapılandırmanıza olanak tanır.

   > [!NOTE]
   > Denetimli cihazlar için bu uygulama yapılandırma ilkesi yalnızca yönetilen cihazlar için geçerlidir ve en iyi uygulama olarak tüm yönetilen iOS cihazları için hedeflenmelidir.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın ve **Uygulama** \> **Uygulaması yapılandırma ilkeleri** \> **Ekle'ye** gidin. **Yönetilen cihazlar'a** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-4.png" alt-text="Yönetilen cihazlar seçeneği" lightbox="images/ios-deploy-4.png":::

1. *Uygulama yapılandırma ilkesi oluştur* sayfasında aşağıdaki bilgileri sağlayın:
    - İlke Adı
    - Platform: iOS/iPadOS'i seçin
    - Hedeflenen uygulama: Listeden **Uç Nokta için Microsoft Defender** seçin

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-5.png" alt-text="Uygulamanın yapılandırma ilkesi için temel alanlar" lightbox="images/ios-deploy-5.png":::

1. Sonraki ekranda **Yapılandırma tasarımcısını** biçim olarak kullan'ı seçin. Aşağıdaki özelliği belirtin:
    - Yapılandırma Anahtarı: denetimli
    - Değer türü: Dize
    - Yapılandırma Değeri: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-6.png" alt-text="İlke yapılandırması ayarlarının biçiminin seçileceği sayfa" lightbox="images/ios-deploy-6.png":::

1. **Kapsam etiketleri** sayfasını açmak için **İleri'ye** tıklayın. Kapsam etiketleri isteğe bağlıdır. Devam etmek için **İleri'ye** tıklayın.

1. **Atamalar** sayfasında, bu profili alacak grupları seçin. Bu senaryoda **, Tüm Cihazları** hedeflemek en iyi yöntemdir. Profil atama hakkında daha fazla bilgi için bkz. [Kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).

   Kullanıcı gruplarına dağıtım yaparken, ilkenin geçerli olması için bir kullanıcının cihazda oturum açması gerekir.

   **İleri**'ye tıklayın.

1. **Gözden Geçir + oluştur** sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Yeni profil, yapılandırma profilleri listesinde görüntülenir.

## <a name="next-steps"></a>Sonraki Adımlar

- [Uygulama koruma ilkesini Uç Nokta için Defender risk sinyallerini (MAM) içerecek şekilde yapılandırma](ios-install-unmanaged.md)
- [iOS özelliklerinde Uç Nokta için Defender'ı yapılandırma](ios-configure-features.md)
