---
title: iOS'ta Uç Nokta için Microsoft Defender için uygulama tabanlı dağıtım
ms.reviewer: ''
description: Uygulama kullanarak iOS'ta Uç Nokta için Microsoft Defender'ın nasıl dağıtıı açık
keywords: microsoft, defender, Endpoint için Microsoft Defender, ios, uygulama, yükleme, dağıtma, kaldırma, intune
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
ms.openlocfilehash: a2e17e5b7a2a5a5a7abed9c7f2a3f42c0cf63b37
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010796"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Microsoft Defender'ı Dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu konuda, kayıtlı cihazlarda iOS üzerinde Uç Nokta için Defender Intune Şirket Portalı dağıtma açıklanmıştır. Intune cihaz kaydı hakkında daha fazla bilgi için bkz [. Intune'da iOS/iPadOS cihazlarını kaydetme](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft Uç Nokta Yöneticisi yönetim [merkezine erişiminiz olduğundan emin olun](https://go.microsoft.com/fwlink/?linkid=2109431).

- Kullanıcılarınız için iOS kaydının tamam olduğundan emin olur. iOS'ta Uç Nokta için Defender'ı kullanmak için kullanıcıların uç nokta için Defender lisansı atanmış olmalıdır. Lisans [atama yönergeleri için Kullanıcılara](/azure/active-directory/users-groups-roles/licensing-groups-assign) lisans atama'ya bakın.

> [!NOTE]
> iOS'ta Uç Nokta için Microsoft Defender [Apple App Store'da kullanılabilir](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>Dağıtım adımları

iOS üzerinde Uç Nokta için Deploy Defender'ı Intune Şirket Portalı.

### <a name="add-ios-store-app"></a>iOS mağaza uygulamasını ekleme

1. [Microsoft Endpoint manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsiOS** -> **/iPadOSAddiOS** ->  ->  mağazası uygulamasına gidin **ve Seç'e** **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi Microsoft Endpoint Manager 1'in görüntüsü.](images/ios-deploy-1.png)

1. Uygulama ekle **sayfasında App** **Store'da Ara'ya tıklayın** ve arama çubuğuna **Uç Nokta için Microsoft Defender** yazın. Arama sonuçları bölümünde, Uç nokta için *Microsoft Defender'a ve ardından Seç'e* **tıklayın**.

1. Minimum **işletim sistemi olarak iOS 11.0'ı** seçin. Uygulamayla ilgili diğer bilgileri gözden geçirin ve Sonraki'ye **tıklayın**.

1. Ödevler **bölümünde** Gerekli bölümüne gidin **ve Grup** **ekle'yi seçin**. Ardından, iOS uygulamasında Uç Nokta için Defender'ı hedeflemek istediğiniz kullanıcı grubunu seçebilirsiniz. **Seç'e ve** ardından **Sonraki'ne tıklayın**.

    > [!NOTE]
    > Seçilen kullanıcı grubu Intune'a kayıtlı kullanıcılardan oluşur.

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi2 Microsoft Endpoint Manager görüntüsü.](images/ios-deploy-2.png)

1. Gözden Geçir *+ Oluştur bölümünde* , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**. Birkaç dakika içinde, Uç Nokta için Defender uygulaması başarıyla oluşturulacak ve sayfanın sağ üst köşesinde bir bildirim gösterilmesi gerekir.

1. Görüntülenen uygulama bilgileri sayfasında, Monitör bölümünde Cihaz yükleme durumunu seçerek cihaz yükleme işleminin başarıyla tamamlanmıştır. 

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi3 Microsoft Endpoint Manager resmi.](images/ios-deploy-3.png)

## <a name="complete-deployment-for-supervised-devices"></a>Denetlenen cihazlar için tam dağıtım

iOS'ta Uç Nokta için Microsoft Defender uygulaması, bu tür cihazlarda platform tarafından sağlanan artırılmış yönetim yeteneklerine sahip ve denetlemeli iOS/iPadOS cihazları üzerinde özelleştirilmiş bir beceriye sahip. Ayrıca cihazda yerel bir **VPN ayarlamadan Da Web Korumasını sağlar**. Bu, son kullanıcılara kimlik avı ve diğer web tabanlı saldırılardan korunmaya devam ederken sorunsuz bir deneyim sunar.

### <a name="configure-supervised-mode-via-intune"></a>Intune yoluyla Denetleme Modunu Yapılandırma

Ardından, Uygulama Yapılandırması ilkesi aracılığıyla Uç Nokta uygulaması için Defender için denetlenen modu yapılandırabilirsiniz.

   > [!NOTE]
   > Denetlenen cihazlar için bu uygulama yapılandırma ilkesi yalnızca yönetilen cihazlar için geçerlidir ve en iyi uygulama olarak TÜM yönetilen iOS cihazları için hedef kitleye yöneliktir.

1. Yönetim merkezinde oturum [Microsoft Endpoint Manager ve Uygulamalar](https://go.microsoft.com/fwlink/?linkid=2109431) Uygulaması yapılandırma ilkeleri **Ekle'ye** \>  \> **gidin**. Yönetilen **cihazlar'ı seçin**.

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi Microsoft Endpoint Manager 4 resmi.](images/ios-deploy-4.png)

1. Uygulama *yapılandırma ilkesi oluştur sayfasında* , aşağıdaki bilgileri sağlar:
    - İlke Adı
    - Platform: iOS/iPadOS'u seçin
    - Hedefli uygulama: Listeden Uç **Nokta için Microsoft Defender'ı** seçin

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi5 Microsoft Endpoint Manager resmi.](images/ios-deploy-5.png)

1. Sonraki ekranda, Yapılandırma tasarımcısını **biçim olarak kullan'ı** seçin. Aşağıdaki özelliği belirtin:
    - Yapılandırma Anahtarı: issupervised
    - Değer türü: Dize
    - Yapılandırma Değeri: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi6 Microsoft Endpoint Manager görüntüsü.](images/ios-deploy-6.png)

1. Kapsam **etiketleri** sayfasını açmak için **Sonraki'yi** seçin. Kapsam etiketleri isteğe bağlıdır. Devam etmek **için Sonraki'yi** seçin.

1. Ödevler **sayfasında** , bu profili alacak grupları seçin. Bu senaryo için, en iyi yöntem Tüm Cihazları **hedeflemektir**. Profil atama hakkında daha fazla bilgi için bkz. [Kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).

   Kullanıcı gruplarına dağıtımda, kullanıcının ilkenin geçerli olması için önce bir cihazda oturum açması gerekir.

   **İleri**'ye tıklayın.

1. **Gözden Geçir + oluştur** sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Yeni profil yapılandırma profilleri listesinde görüntülenir.

1. Ardından, gelişmiş Kimlik avı önleme özellikleri için, denetlenen iOS cihazlara özel bir profil dağıtabilirsiniz. Aşağıdaki adımları izleyin:

    - Yapılandırma profilini [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - **DevicesiOS** -> **/iPadOSConfiguration** ->  **profillerine gidin Profile** ->  **Oluşturma**

    > [!div class="mx-imgBorder"]
    > ![Yönetim Merkezi7 Microsoft Endpoint Manager görüntüsü.](images/ios-deploy-7.png)
    
    - Profilin adını girin. Bir Yapılandırma profil dosyasını içeri aktarmanız istendiğinde, önceki adımdan indirileni seçin.
    - Ödev **bölümünde** , bu profili uygulamak istediğiniz cihaz grubunu seçin. En iyi uygulama olarak, bu tüm yönetilen iOS cihazlarına uygulanmalıdır. **İleri**'yi seçin.
    - **Gözden Geçir + oluştur** sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Yeni profil yapılandırma profilleri listesinde görüntülenir.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>VPN profilinde Otomatik Ekleme (Basitleştirilmiş Ekleme)

Web Koruması özelliğini sağlamak amacıyla, güvenli olmayan cihazlar için VPN kullanılır. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.

>[!NOTE]
>Denetlenen cihazlar için Web Koruması özelliği için VPN gerekmez ve yöneticilerin denetleme yapılan cihazlara yapılandırma profili ayarlamasını gerektirir. Denetlenen cihazları yapılandırmak için, Denetlenen cihazlar için [dağıtımı tamamlama bölümündeki adımları](#complete-deployment-for-supervised-devices) izleyin.

Yöneticiler VPN profilinin otomatik kurulumunu yapılandırabilirsiniz. Bu, kullanıcının ekleme sırasında bunu yapmak zorunda kalmadan Uç Nokta VPN profili için Defender'ı otomatik olarak ayarlar. 

Bu adım VPN profilini ayarerek ekleme işlemini basitler. Sıfır dokunmatik veya sessiz ekleme deneyimi için sonraki bölüme bakın: [Sıfır dokunmatik ekleme](#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview).

1. [Microsoft Endpoint manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **DevicesConfiguration** ->  **ProfilesCreate** ->  Profile gidin.
1. **iOS/iPadOS olarak Platform'u** ve VPN **olarak profil türünü** **seçin**. **Oluştur'a tıklayın**.
1. Profil için bir ad yazın ve Sonraki'ye **tıklayın**.
1. Bağlantı **Türü için** Özel VPN'yi **seçin ve Temel VPN** bölümünde şunları girin:
    - Bağlantı Adı = Uç Nokta için Microsoft Defender
    - VPN sunucu adresi = 127.0.0.1
    - Kimlik doğrulama yöntemi = "Kullanıcı adı ve parola"
    - Bölünmüş Bölme = Devre Dışı Bırak
    - VPN tanımlayıcısı = com.microsoft.scmx
    - Anahtar değeri çiftleri içinde **AutoOnboard** tuşuna basın ve değeri **True olarak ayarlayın**.
    - Otomatik VPN türü = isteğe bağlı VPN
    - **İsteğe** Bağlı **Kurallar Ekle'ye** tıklayın ve Şu yapmak istiyorum **= VPN** Kur, kısıtlamak istiyorum **= Tüm etki alanları seçeneğini seçin**.

    ![VPN profili yapılandırma ayarlarının ekran görüntü](images/ios-deploy-8.png)

1. Sonraki'ne tıklayın ve profili hedefli kullanıcılara attaynın.
1. Gözden Geçir *+ Oluştur bölümünde* , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview"></a>Uç Nokta (Önizleme) için Microsoft Defender'ın sıfır dokunmalı eklemesi

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.


Yöneticiler, sessizce dağıtım yapmak ve etkinleştirmek üzere Uç Nokta için Microsoft Defender'ı yapılandırmış olabilir. Bu akışta, yönetici bir dağıtım profili oluşturur ve kullanıcıya yalnızca yüklemeyle ilgili bir bilgi olur. Kullanıcının uygulamayı açması gerekmeden Uç Nokta için Defender otomatik olarak yüklenir. Kayıtlı iOS cihazlarda Uç Nokta için Defender'ın sıfır dokunmatik veya sessiz dağıtımının kurulumu için aşağıdaki adımları izleyin:

1. [Microsoft Endpoint manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **DevicesConfiguration** >  **ProfilesCreate** >  Profile gidin.
1. **iOS/iPadOS olarak Platform'u** ve VPN **olarak profil türünü** **seçin**. **Oluştur**’u seçin.
1. Profil için bir ad yazın ve Sonraki'yi **seçin**.
1. Bağlantı **Türü için** Özel VPN'yi **seçin ve Temel VPN** bölümünde şunları girin:
    - Bağlantı Adı = Uç Nokta için Microsoft Defender
    - VPN sunucu adresi = 127.0.0.1
    - Kimlik doğrulama yöntemi = "Kullanıcı adı ve parola"
    - Bölünmüş Bölme = Devre Dışı Bırak
    - VPN tanımlayıcısı = com.microsoft.scmx
    - Anahtar değeri çiftlerinin içine **SilentOnboard anahtarını girin ve** değeri **True olarak ayarlayın**.
    - Otomatik VPN türü = isteğe bağlı VPN
    - **İsteğe** Bağlı **Kurallar Ekle'yi seçin** ve şu adımları yapmak istiyorum **= VPN** Kur, kısıtlamak istiyorum **= Tüm etki alanları seçeneğini seçin**.

    ![VPN profili yapılandırmasının ekran görüntü.](images/ios-deploy-9.png)

1. **Sonraki'yi** seçin ve profili hedefli kullanıcılara attaynın.
1. Gözden Geçir *+ Oluştur bölümünde* , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**.

Yukarıdaki yapılandırma tamamlanın ve cihazla eşitlenen aşağıdaki eylemler hedef iOS cihaz veya cihaz üzerinde  yapılır:
    - Uç Nokta için Microsoft Defender dağıtılır, sessizce uygulanır ve cihaz Uç Nokta için Defender portalında görülür.
    - Kullanıcı cihazına bir geçici bildirim gönderilir.
    - Web Koruması ve diğer özellikler etkinleştirilir.

   > [!NOTE]
   > Denetlenen cihazlar için VPN profili gerekli değildir ancak yöneticiler Intune aracılığıyla Uç Nokta VPN profili için Defender'ı yapılandırarak Sıfır dokunmatik ekleme ayarlarını yine de kullanabilir. VPN profili cihazda dağıtılır, ancak cihazda yalnızca geçiş profili olarak mevcut olur ve ilk eklemeden sonra silinebilir.

## <a name="complete-onboarding-and-check-status"></a>Ekleme işlemini tamamlama ve durumu denetleme

1. Cihaza iOS'ta Uç Nokta için Defender yüklendikten sonra uygulama simgesini görüntülersiniz.

    ![Otomatik olarak akıllı telefon Açıklaması'nın ekran görüntü oluşturulur.](images/41627a709700c324849bf7e13510c516.png)

2. Uç nokta için Defender uygulama simgesine (MSDefender) dokunun ve ekleme adımlarını tamamlamak için ekrandaki yönergeleri izleyin. Ayrıntılar, iOS'ta Uç Nokta için Defender tarafından gereken iOS izinlerinin son kullanıcı kabulünü içerir.

3. Başarılı bir şekilde işe alım sırasında cihaz, portalda bulunan Cihazlar listesinde Microsoft 365 Defender başlar.

    > [!div class="mx-imgBorder"]
    > ![Otomatik olarak oluşturulan bir cep telefonu Açıklamasının ekran görüntüsü.](images/device-inventory-screen.png)


## <a name="next-steps"></a>Sonraki Adımlar

- [Uç nokta risk işaretleri (MAM) için Defender'ı içerecek şekilde uygulama koruma ilkesi yapılandırma](ios-install-unmanaged.md)
- [iOS'ta Uç Nokta için Defender'ı Yapılandırma](ios-configure-features.md)
