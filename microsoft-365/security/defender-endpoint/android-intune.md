---
title: Android’de Uç Nokta için Defender’ı Microsoft Intune ile dağıtın
description: Microsoft Intune ile Android'de Uç Nokta için Microsoft Defender dağıtmayı açıklar
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mde, android, installation, deploy, uninstallation,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 461664cc72486a49e5b7bd9be44235559409adff
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825296"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Android’de Uç Nokta için Defender’ı Microsoft Intune ile dağıtın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kayıtlı Intune Şirket Portalı cihazlarda Android'de Uç Nokta için Defender'ı dağıtmayı öğrenin. Intune cihaz kaydı hakkında daha fazla bilgi için bkz. [Cihazınızı kaydetme](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Android'de Uç Nokta için Defender artık [Google Play'de](https://play.google.com/store/apps/details?id=com.microsoft.scmx) kullanılabilir**
>
> Uç Nokta için Defender uygulamasını Cihaz Yöneticisi ve Android Enterprise kayıt modları arasında dağıtmak için Intune'den Google Play'e bağlanabilirsiniz.
>
> Uygulama güncelleştirmeleri Google Play aracılığıyla otomatik olarak gerçekleştirilir.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Cihaz Yöneticisi tarafından kaydedilen cihazlarda dağıtma

**Intune Şirket Portalı üzerinde Android'de Uç Nokta için Defender'ı dağıtma - Cihaz Yöneticisi tarafından kaydedilen cihazlar**

Intune Şirket Portalı - Cihaz Yöneticisi tarafından kaydedilen cihazlarda Android'de Uç Nokta için Defender'ı dağıtmayı öğrenin.

### <a name="add-as-android-store-app"></a>Android mağazası uygulaması olarak ekle

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar** \> **Android Uygulamaları Android mağazası** \> **uygulaması ekle'ye \>** gidin ve **Seç'i** seçin.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalındaki Android mağazası uygulaması ekle bölmesi"  lightbox="images/mda-addandroidstoreapp.png":::

2. **Uygulama ekle** sayfasında ve *Uygulama Bilgileri* bölümüne şunu girin:

   - **Ad**
   - **Açıklama**
   - **Microsoft olarak Publisher**.
   - **Olarak uygulama mağazası URL'si** https://play.google.com/store/apps/details?id=com.microsoft.scmx (Uç nokta uygulaması için Defender Google Play Store URL'si)

   Diğer alanlar isteğe bağlıdır. **İleri**'yi seçin.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalında uygulamanın yayımcısını ve URL bilgilerini görüntüleyen Uygulama Ekle sayfası" lightbox="images/mda-addappinfo.png":::

3. *Atamalar* bölümünde **Gerekli** bölümüne gidin ve **Grup ekle'yi seçin.** Ardından, Android uygulamasında Uç Nokta için Defender'ı hedeflemek istediğiniz kullanıcı gruplarını seçebilirsiniz. **Seç'i** ve ardından **İleri'yi** seçin.

    > [!NOTE]
    > Seçilen kullanıcı grubu kayıtlı Intune kullanıcıdan oluşmalıdır.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalındaki Uygulama Ekle sayfasındaki Grup ekle bölmesi" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. **Gözden Geçir+Oluştur** bölümünde, girilen tüm bilgilerin doğru olduğunu doğrulayın ve **Oluştur'u** seçin.

    Birkaç dakika içinde Uç Nokta için Defender uygulaması başarıyla oluşturulur ve sayfanın sağ üst köşesinde bir bildirim gösterilir.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalındaki uygulama durumu bölmesi" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Görüntülenen uygulama bilgileri sayfasındaki **İzleyici** bölümünde **Cihaz yükleme durumu'nu** seçerek cihaz yüklemesinin başarıyla tamamlandığını doğrulayın.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Microsoft Defender 365 portalındaki Cihaz yükleme durumu sayfası" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Eklemeyi tamamlama ve durumu denetleme

1. Android'de Uç Nokta için Defender cihaza yüklendikten sonra uygulama simgesini görürsünüz.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Arama bölmesinde listelenen Microsoft Defender ATP simgesi" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Uç Nokta için Microsoft Defender uygulama simgesine dokunun ve uygulamayı ekleme işlemini tamamlamak için ekrandaki yönergeleri izleyin. Ayrıntılar, Android'de Uç Nokta için Defender tarafından gereken Android izinlerinin son kullanıcı tarafından kabul edilmesini içerir.

3. Ekleme başarılı olursa cihaz, Microsoft 365 Defender portalındaki Cihazlar listesinde gösterilmeye başlar.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Uç Nokta için Microsoft Defender portalındaki bir cihaz"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Android Enterprise kayıtlı cihazlarda dağıtma

Android'de Uç Nokta için Defender, Android Enterprise kayıtlı cihazları destekler.

Intune tarafından desteklenen kayıt seçenekleri hakkında daha fazla bilgi için bkz. [Kayıt Seçenekleri](/mem/intune/enrollment/android-enroll).

**Şu anda, şirkete ait tam olarak yönetilen kullanıcı cihaz kayıtları ve iş profiline sahip kişisel cihazlar dağıtım için desteklenmektedir.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Android'de Yönetilen Google Play uygulaması olarak Uç Nokta için Microsoft Defender ekleme

Yönetilen Google Play'inize Uç Nokta için Microsoft Defender uygulama eklemek için aşağıdaki adımları izleyin.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar** \> **Android Uygulamaları** \> **Ekle'ye** gidin ve **Yönetilen Google Play uygulaması'nı** seçin.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki uygulama ekleme bölmesi" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Daha sonra yüklenen yönetilen Google Play sayfanızda arama kutusuna gidin ve yazın `Microsoft Defender`. Aramanızda Yönetilen Google Play'inizde Uç Nokta için Microsoft Defender uygulaması görüntülenmelidir. Uygulamalar arama sonucundan Uç Nokta için Microsoft Defender uygulamasına tıklayın.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki Yönetilen Google Play sayfası" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. Sonraki uygulama açıklaması sayfasında, Uç Nokta için Defender'da uygulama ayrıntılarını görebilmeniz gerekir. Sayfadaki bilgileri gözden geçirin ve **onayla'yı** seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalında Yönetilen Google Play sayfası" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Uç Nokta için Defender'ın çalışması için aldığı izinler sunulur. Bunları gözden geçirin ve **onayla'yı** seçin.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Microsoft Defender 365 portalındaki izin onay sayfası" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Size Onay ayarları sayfası gösterilir. Sayfa, Android'de Uç Nokta için Defender'ın sorabileceği yeni uygulama izinlerini işleme tercihinizi onaylar. Seçenekleri gözden geçirin ve tercih ettiğiniz seçeneği belirleyin. **Bitti'yi** seçin.

    Varsayılan olarak, yönetilen Google Play **, uygulama yeni izinler istediğinde Onaylı tut'ı** seçer.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Microsoft Defender 365 portalındaki onay ayarları yapılandırma tamamlama sayfası" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. İzinleri işleme seçimi yapıldıktan sonra, Uç Nokta için Microsoft Defender uygulama listenize eşitlemek için **Eşitle'yi** seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Microsoft Defender 365 portalındaki Eşitleme bölmesi" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Eşitleme birkaç dakika içinde tamamlanır.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Microsoft Defender 365 portalındaki Android uygulamaları sayfasındaki uygulama eşitleme durumu bölmesi"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Android uygulamaları ekranında **Yenile** düğmesini seçtiğinizde Uç Nokta için Microsoft Defender uygulamalar listesinde görünür olmalıdır.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Eşitlenen uygulamayı görüntüleyen sayfa" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Uç Nokta için Defender, Intune aracılığıyla yönetilen cihazlar için Uygulama yapılandırma ilkelerini destekler. Bu özellik, Defender için farklı yapılandırmalar seçmek için kullanılabilir.

    1. **Uygulamalar** sayfasında **İlke > Uygulama yapılandırma ilkeleri'ne gidin > yönetilen > cihaz ekle'ye** gidin.

       :::image type="content" source="images/android-mem.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki Uygulama yapılandırma ilkeleri bölmesi" lightbox="images/android-mem.png":::

    1. **Uygulama yapılandırma ilkesi oluştur** sayfasında aşağıdaki ayrıntıları girin:

        - Ad: Uç Nokta için Microsoft Defender.
        - **Platform olarak Android Enterprise'ı** seçin.
        - **Yalnızca Profil Türü olarak İş Profili'ni** seçin.
        - **Uygulama Seç'e** tıklayın, **Microsoft Defender ATP'yi** seçin, **Tamam'ı** ve ardından **İleri'yi** seçin.

        :::image type="content" source="images/android-create-app.png" alt-text=" İlişkili uygulama ayrıntıları bölmesi" lightbox="images/android-create-app.png":::

    1. **Ayarlar** sayfasında Yapılandırma ayarları bölümüne gidin ve **Yapılandırma ayarları** biçiminde **'Yapılandırma tasarımcısını kullan'ı** seçin. 

       :::image type="content" alt-text="Android oluşturma uygulama yapılandırma ilkesinin görüntüsü." source="images/configurationformat.png" lightbox="images/configurationformat.png":::

    1. Desteklenen yapılandırmaların listesini görüntülemek için **Ekle'ye** tıklayın. Gerekli yapılandırmayı seçin ve **Tamam'a** tıklayın.

       :::image type="content" alt-text="Android için yapılandırma ilkelerini seçme görüntüsü." source="images/selectconfigurations.png" lightbox="images/selectconfigurations.png":::


    1. Tüm seçili yapılandırmaların listelendiğini görmeniz gerekir. Yapılandırma değerini gerektiği gibi değiştirebilir ve ardından **İleri'yi** seçebilirsiniz.
        
        :::image type="content" alt-text="Seçili yapılandırma ilkelerinin görüntüsü." source="images/listedconfigurations.png" lightbox="images/listedconfigurations.png":::
       

    1. **Atamalar** sayfasında, bu uygulama yapılandırma ilkesinin atanacağı kullanıcı grubunu seçin. **Dahil etmek için Grupları seç'e** tıklayın, uygun grubu seçin ve ardından **İleri'yi** seçin. Burada seçilen grup genellikle Android uygulaması Uç Nokta için Microsoft Defender atayacağınız grupla aynıdır.

       :::image type="content" source="images/android-select-group.png" alt-text="Seçili gruplar bölmesi" lightbox="images/android-select-group.png":::

    1. Ardından gelen **Gözden Geçir + Oluştur** sayfasında tüm bilgileri gözden geçirin ve **Oluştur'u** seçin.

        Depolama iznini otomatik olarak alan Uç Nokta için Defender uygulama yapılandırma ilkesi artık seçili kullanıcı grubuna atanır.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Uygulama yapılandırma ilkesi oluştur sayfasındaki Gözden Geçir + oluştur sekmesi" lightbox="images/android-review-create.png":::

10. **Özellikler** \> **Atamalarını** \> **Düzenle** listesinden \> **Microsoft Defender ATP** uygulaması'nı seçin.

   :::image type="content" source="images/mda-properties.png" alt-text="Özellikler sayfasındaki Düzenle seçeneği" lightbox="images/mda-properties.png":::

11. Uygulamayı bir kullanıcı grubuna *Gerekli* uygulama olarak atayın. Cihazın bir sonraki Şirket Portalı uygulaması aracılığıyla eşitlenmesi sırasında *iş profiline* otomatik olarak yüklenir. Bu atama, *Gerekli* bölüm \> **Ekle grubuna** gidip kullanıcı grubunu seçip **Seç'e** tıklayarak yapılabilir.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Uygulamayı düzenle sayfası" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. **Uygulamayı Düzenle** sayfasında, yukarıda girilen tüm bilgileri gözden geçirin. Ardından **Gözden Geçir + Kaydet'i** seçin ve sonra atamaya devam etmek için yeniden **Kaydet'i** seçin.

### <a name="auto-setup-of-always-on-vpn"></a>Her Zaman Açık VPN'in Otomatik Kurulumu

Uç Nokta için Defender, Intune aracılığıyla yönetilen cihazlar için Cihaz yapılandırma ilkelerini destekler. Bu özellik, Android Enterprise kayıtlı cihazlarda **Always-on VPN'in otomatik kurulumu** için kullanılabilir, bu nedenle son kullanıcının ekleme sırasında VPN hizmetini ayarlaması gerekmez.

1. **Cihazlar'da** **Yapılandırma Profilleri** \> **Profil** \> **Platformu** \> Oluştur **Android Enterprise'ı** seçin

   Cihaz kayıt türünüz temelinde aşağıdakilerden birinin altında Cihaz **kısıtlamaları'nı** seçin:
   - **Tam Olarak Yönetilen, Ayrılmış ve Corporate-Owned İş Profili**
   - **Kişisel İş Profili**

   **Oluştur**’u seçin.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="İlke bölmesindeki Yapılandırma profilleri menü öğesi" lightbox="images/1autosetupofvpn.png":::

2. **Yapılandırma Ayarlar** Yapılandırma profilini benzersiz olarak tanımlamak için bir **Ad** ve **Açıklama** sağlayın.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Temel bilgiler bölmesindeki cihaz yapılandırma profili Ad ve Açıklama alanları" lightbox="images/2autosetupofvpn.png":::

3. **Bağlantı'ya tıklayın** ve VPN'yi yapılandırın:

   - **Always-on VPN'yi** etkinleştirme

     Mümkün olduğunda vpn'e otomatik olarak bağlanmak ve yeniden bağlanmak için iş profilinde bir VPN istemcisi ayarlayın. Belirli bir cihazda her zaman açık VPN için yalnızca bir VPN istemcisi yapılandırılabilir, bu nedenle tek bir cihaza birden fazla her zaman açık VPN ilkesi dağıtılmadığından emin olun.

   - VPN istemcisi açılan listesinde **Özel'i** seçin

     Bu durumda özel VPN, Web Koruması özelliğini sağlamak için kullanılan Uç Nokta IÇIN Defender VPN'dir.

     > [!NOTE]
     > Uç Nokta için Microsoft Defender uygulamasının bu VPN'nin otomatik kurulumunun çalışması için kullanıcının cihazına yüklenmesi gerekir.

   - Google Play store'da Uç Nokta için Microsoft Defender uygulamasının **Paket Kimliğini** girin. Defender uygulama URL'si <https://play.google.com/store/apps/details?id=com.microsoft.scmx>için Paket Kimliği **: com.microsoft.scmx**

   - **Kilitleme modu** Yapılandırılmadı (Varsayılan)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Yapılandırma ayarları sekmesinin altındaki Bağlantı bölmesi" lightbox="images/3autosetupofvpn.png":::

4. **Atama**

   **Atamalar** sayfasında, bu uygulama yapılandırma ilkesinin atanacağı kullanıcı grubunu seçin. Dahil etmek istediğiniz **grupları seçin** ve uygun grubu seçin ve ardından **İleri'yi** seçin. Burada seçilen grup genellikle Android uygulaması Uç Nokta için Microsoft Defender atayacağınız grupla aynıdır.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Cihaz kısıtlamalarındaki cihazlar yapılandırma profili Atama bölmesi" lightbox="images/4autosetupofvpn.png":::

5. Ardından gelen **Gözden Geçir + Oluştur** sayfasında tüm bilgileri gözden geçirin ve **Oluştur'u** seçin.
Cihaz yapılandırma profili artık seçili kullanıcı grubuna atanır.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="Bir cihaz yapılandırma profilinin Gözden Geçir ve oluştur için sağlaması" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Durumu denetleme ve ekleme işlemini tamamlama

1. **Cihaz Yükleme Durumu'na** tıklayarak Android'de Uç Nokta için Microsoft Defender yükleme durumunu onaylayın. Cihazın burada görüntülendiğini doğrulayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Cihaz yükleme durumu bölmesi" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. Cihazda, **iş profiline** giderek ekleme durumunu doğrulayabilirsiniz. Uç Nokta için Defender'ın kullanılabilir olduğunu ve **kişisel cihazlara iş profiliyle** kaydolduğunuz onaylayın. **Şirkete ait, tam olarak yönetilen bir kullanıcı cihazına** kayıtlıysanız, cihazda Uç Nokta için Defender'ın kullanılabilir olduğunu onaylayabileceğiniz tek bir profiliniz olur.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Uygulama görüntüleme bölmesi" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Uygulama yüklendiğinde uygulamayı açın ve izinleri kabul edin; ardından ekleme işleminiz başarılı olmalıdır.

    :::image type="content" source="images/MDE_new.png" alt-text="Mobil cihazda bir Uç Nokta için Microsoft Defender uygulamasının th ekranı" lightbox="images/MDE_new.png":::

4. Bu aşamada cihaz, Android'de Uç Nokta için Defender'a başarıyla eklenir. Bunu [Microsoft 365 Defender portalında](https://security.microsoft.com) **Cihaz Envanteri** sayfasına giderek doğrulayabilirsiniz.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Uç Nokta için Microsoft Defender portalı" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender’a genel bakış](microsoft-defender-endpoint-android.md)
- [Android’de Uç Nokta için Microsoft Defender’ı yapılandırın](android-configure.md)
