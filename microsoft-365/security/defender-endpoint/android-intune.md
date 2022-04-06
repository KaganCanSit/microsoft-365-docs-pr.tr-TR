---
title: Android'Uç Nokta için Microsoft Defender uygulama dağıtımı ve Microsoft Intune
description: Android cihazlarda Uç Nokta için Microsoft Defender dağıtımı açık Microsoft Intune
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mde, android, yükleme, dağıtma, kaldırma,
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
ms.openlocfilehash: aab50764a13a671cdeb10902744456dcbc1cb48f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471417"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Android'Uç Nokta için Microsoft Defender uygulama dağıtımı ve Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kayıtlı cihazlarda Android'de Uç nokta için Defender Intune Şirket Portalı dağıtmayı öğrenin. Cihaz kaydı hakkında daha Intune için bkz[. Cihazınızı kaydetme](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Android'de Uç Nokta için Defender artık [Google Play'de kullanılabilir](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Cihaz Yöneticisi ve Android uygulamasına Uç Intune için Defender'ı dağıtmak için Google Play'e Enterprise bağlanabilirsiniz.
>
> Uygulamanın güncelleştirmeleri Google Play üzerinden otomatik olarak 65 gün içinde 65 gün içinde 65 gün içinde 65 gün içinde otomatik olarak

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Cihaz Yöneticisi tarafından kayıt yapılan cihazlarda dağıtma

**Android'de Uç Nokta için Deploy Defender Intune Şirket Portalı - Cihaz Yöneticisi tarafından kayıt yapılan cihazlar**

Android cihazlarda Uç Nokta için Defender'ı dağıtmayı Intune Şirket Portalı - Cihaz Yöneticisi tarafından kayıtlı cihazlar.

### <a name="add-as-android-store-app"></a>Android Store uygulaması olarak ekle

1. Uygulama [Microsoft Endpoint Manager , Uygulamalar](https://go.microsoft.com/fwlink/?linkid=2109431)  \> **Android Uygulamaları Android mağazası ekle uygulaması'ne** \> **gidin \> ve Seç'i** **seçin**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalında Android Microsoft Endpoint Manager uygulama bölmesi"  lightbox="images/mda-addandroidstoreapp.png":::

2. Uygulama **ekle sayfasında** ve Uygulama *Bilgileri bölümüne şunları* girin:

   - **Ad**
   - **Açıklama**
   - **Publisher** olarak açık.
   - **Olarak uygulama mağazası URL'si** https://play.google.com/store/apps/details?id=com.microsoft.scmx (Uç nokta uygulaması Google Play Store URL'si için Defender)

   Diğer alanlar isteğe bağlıdır. **İleri**'yi seçin.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Uygulama Yönetim Merkezi portalında uygulamanın yayımcısını ve URL bilgilerini Microsoft Endpoint Manager Sayfa" lightbox="images/mda-addappinfo.png":::

3. Ödevler *bölümünde* Gerekli bölümüne gidin **ve Grup** **ekle'yi seçin.** Ardından, Android uygulamasında Uç Nokta için Defender'ı hedeflemek istediğiniz kullanıcı grubunu seçebilirsiniz. **Seç'i ve** ardından **Sonraki'yi seçin**.

    > [!NOTE]
    > Seçilen kullanıcı grubu, kayıtlı Intune şekilde çalışmalı.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalında Uygulama Ekle sayfasındaki Grup ekle bölmesi" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. Gözden Geçir **+Oluştur bölümünde** , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**.

    Birkaç dakika içinde, Uç Nokta için Defender uygulaması başarıyla oluşturulabilir ve sayfanın sağ üst köşesinde bir bildirim görüntülenir.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Microsoft Endpoint Manager Yönetim Merkezi portalında uygulama durumu bölmesi" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Görüntülenen uygulama bilgileri sayfasında, Monitör bölümünde Cihaz yükleme durumunu seçerek cihaz yükleme işleminin başarıyla tamamlanmıştır. 

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Microsoft Defender 365 portalında Cihaz yükleme durumu sayfası" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Ekleme işlemini tamamlama ve durumu denetleme

1. Cihaza Android'de Uç Nokta için Defender yüklendikten sonra uygulama simgesini gösterilir.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Arama bölmesinde listelenen Microsoft Defender ATP simgesi" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Uygulamayı Uç Nokta için Microsoft Defender simgesine dokunun ve uygulamayı ekleme işlemini tamamlamak için ekrandaki yönergeleri izleyin. Ayrıntılar arasında, Android'de Uç Nokta için Defender tarafından gereken Android izinlerinin son kullanıcı kabulü yer amektedir.

3. Başarılı bir şekilde işe alım sırasında cihaz, portalda bulunan Cihazlar listesinde Microsoft 365 Defender başlar.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Uç Nokta için Microsoft Defender portalında bir cihaz"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Android veya Enterprise cihazlarda dağıtma

Android'de Uç Nokta için Defender, Enterprise cihazlarda Android'i destekler.

Kayıt seçenekleri tarafından desteklenen kayıt seçenekleri hakkında daha fazla bilgi Intune bkz. [Kayıt Seçenekleri](/mem/intune/enrollment/android-enroll).

**Şu anda, İş profiline sahip ve Kurumsal'a ait tam kullanıcı cihaz kayıtlarına sahip olan, kişisel olarak sahip olunan cihazlar dağıtım için desteklemektedir.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Android Uç Nokta için Microsoft Defender da Yönetilen Google Play uygulaması olarak kullanıcı ekleme

Yönetilen Google Play'inize Uç Nokta için Microsoft Defender uygulama eklemek için aşağıdaki adımları izleyin.

1. Uygulama [Microsoft Endpoint Manager , Uygulamalar](https://go.microsoft.com/fwlink/?linkid=2109431) Android Uygulamaları **Ekle'ye** \> **gidin ve** \> **Yönetilen** **Google Play uygulaması'ı seçin**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Yönetim merkezi portalında uygulama Microsoft Endpoint Manager bölmesi" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Yönetilen Google Play sayfanız sonradan yüklenirken, arama kutusuna gidin ve 'ı girin `Microsoft Defender`. Aramanız Yönetilen Google Play'Uç Nokta için Microsoft Defender mobil uygulamayı görüntülemeli. Uygulamalar arama Uç Nokta için Microsoft Defender en son uygulamaya tıklayın.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Yönetim merkezi portalında yönetilen Microsoft Endpoint Manager Google Play sayfası" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. Sonraki ortaya çıkan Uygulama açıklaması sayfasında, Uç nokta için Defender'da uygulama ayrıntılarını görebilirsiniz. Sayfada bilgileri gözden geçirip Onayla'ya **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalında Yönetilen Google Play sayfası" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Uç Nokta için Defender'ın bu uygulamanın çalışması için edinilen izinler size sunulacaktır. Bunları gözden geçirip **Onayla'ya seçin**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Microsoft Defender 365 portalında izin onay sayfası" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Onay ayarları sayfası görüntülenir. Sayfada, Android'deki Uç Nokta için Defender'ın sor sor olabileceği yeni uygulama izinlerini işleme tercihinizi onaylar. Seçenekleri gözden geçirerek tercih ettiğiniz seçeneği belirleyin. **Bitti'yi seçin**.

    Varsayılan olarak, yönetilen Google Play uygulaması yeni **izinler isterken Onaylandır'ı seçer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Microsoft Defender 365 portalında onay ayarları yapılandırma tamamlama sayfası" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. İzinleri işleme seçimi yapıldıktan sonra, **eşitlemek için** Eşitle'Uç Nokta için Microsoft Defender uygulamalar listenizle eşitle'yi seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Microsoft Defender 365 portalında Eşitleme bölmesi" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Eşitleme birkaç dakika içinde tamamlanır.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Microsoft Defender 365 portalında Android uygulamaları sayfasının uygulama eşitleme durumu bölmesi"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Android **uygulamaları** ekranında Yenile düğmesini seçin Uç Nokta için Microsoft Defender uygulamalar listesinde görünür olması gerekir.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Eşitlenen uygulamayı görüntüleyen sayfa" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Uç Nokta için Defender, yönetilen cihazlar için uygulama yapılandırma ilkelerini Intune. Bu özellik geçerli Android izinlerini otomatik olarak almak için kullanılabilir, dolayısıyla son kullanıcının bu izni veya izinlerini kabul etme ihtiyacı olmaz.

    1. Uygulamalar sayfasında **,** İlke ve Uygulama **> ilkeleri'ne gidin > Yönetilen > ekleyin**.

       :::image type="content" source="images/android-mem.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalında Uygulama yapılandırma ilkeleri bölmesi" lightbox="images/android-mem.png":::

    1. Uygulama **yapılandırma ilkesi oluştur sayfasında** aşağıdaki ayrıntıları girin:

        - Ad: Uç Nokta için Microsoft Defender.
        - **Android 'i Enterprise** olarak seçin.
        - Yalnızca **Profil Türü olarak İş** Profili'ne tıklayın.
        - Uygulama **Seç'e tıklayın**, **Microsoft Defender ATP'yi seçin**, **Tamam'ı ve** ardından Sonraki'yi seçin.

        :::image type="content" source="images/android-create-app.png" alt-text=" İlişkili uygulama ayrıntıları bölmesi" lightbox="images/android-create-app.png":::

    1. Destek **Ayarlar** İzinler bölümüne gidip, desteklenen izinlerin listesini görüntülemek için Ekle'ye tıklayın. İzin Ekle bölümünde aşağıdaki izinleri seçin:

       - Dış depolama (okuma)
       - Dış depolama (yazma)

       Sonra **Tamam**’ı seçin.

       :::image type="content" source="images/android-create-app-config.png" alt-text="İzin ekle bölmesi" lightbox="images/android-create-app-config.png":::

    1. Şimdi hem listelenen izinleri hem de artık İzin durumu açılır listesinde otomatik yetkiyi seçerek ve sonra da Sonraki'yi seçerek otomatik olarak veri **alabilirsiniz**.

       :::image type="content" source="images/android-auto-grant.png" alt-text="İzin durumu bölmesi" lightbox="images/android-auto-grant.png":::

    1. Atamalar **sayfasında** , bu uygulama yapılandırma ilkesi'nin atandığı kullanıcı grubunu seçin. Dahil **etmek için grupları seç'e** tıklayın, uygun grubu seçin ve ardından Sonraki'yi **seçin**. Burada seçilen grup genellikle Android uygulamasında seçtiğiniz grupla Uç Nokta için Microsoft Defender olur.

       :::image type="content" source="images/android-select-group.png" alt-text="Seçili gruplar bölmesi" lightbox="images/android-select-group.png":::

    1. Sonraki sayfada **yer alan Gözden Geçir +** Oluştur sayfasında, tüm bilgileri gözden geçirin ve ardından Oluştur'a **tıklayın**.

        Depolama iznini otomatik olarak almak için Uç Nokta için Defender'ın uygulama yapılandırma ilkesi artık seçili kullanıcı grubuna atanır.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Uygulama yapılandırma ilkesi oluştur sayfasında gözden geçir + oluştur sekmesi" lightbox="images/android-review-create.png":::

10. Özellikler **Atamaları Düzenleme listesinde** Microsoft \>  \> Defender ATP **uygulaması'ı** \> **seçin**.

   :::image type="content" source="images/mda-properties.png" alt-text="Özellikler sayfasındaki Düzenle seçeneği" lightbox="images/mda-properties.png":::

11. Uygulamayı bir kullanıcı grubuna *Gerekli* uygulama olarak attayabilirsiniz. Cihazın bir sonraki *eşitlemesi sırasında uygulama üzerinden* iş profiline otomatik olarak Şirket Portalı. Bu atama, Gerekli bölümüne (Grup  ekle) \> gidin **, kullanıcı** grubunu seçin ve Seç'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Uygulamayı düzenle sayfası" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. Uygulamayı **Düzenle sayfasında** , yukarıda girilen tüm bilgileri gözden geçirebilirsiniz. Sonra ödevi başlamak **için Gözden Geçir + Kaydet'i** **ve sonra** yeniden Kaydet'i seçin.

### <a name="auto-setup-of-always-on-vpn"></a>Her Zaman Açık VPN'nin Otomatik Kurulumu

Uç Nokta için Defender, yönetilen cihazlar için cihaz yapılandırma ilkelerini Intune. Bu özellik, Android veya kayıtlı cihazlarda Her Zaman **Açık VPN'nin** otomatik olarak kurulumu Enterprise, dolayısıyla son kullanıcının ekleme sırasında VPN hizmetini ayarlaması gerekmektedir.

1. Cihazlarda **,** Yapılandırma Profilleri **Profil Platformu Oluştur** \> **Android** **Ayarları'Enterprise** \>  \>

   Cihaz **kayıt türünüz** bağlı olarak, aşağıdaki seçeneklerden birinin altında Cihaz kısıtlamaları'ı seçin:
   - **Tümüyle Yönetilen, Adanmış ve Corporate-Owned Profili**
   - **Kişisel olarak sahip olunan İş Profili**

   **Oluştur**’u seçin.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="İlke bölmesindeki Yapılandırma profilleri menü öğesi" lightbox="images/1autosetupofvpn.png":::

2. **Yapılandırma Ayarlar** Yapılandırma **profilini benzersiz** olarak tanımlamak **için** bir Ad ve Açıklama girin.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Temel Bilgiler bölmesinde cihazlar yapılandırma profili Ad ve Açıklama alanları" lightbox="images/2autosetupofvpn.png":::

3. **Bağlantı'yi** seçin ve VPN'yi yapılandıryın:

   - Her **Zaman Açık VPN'yi Etkinleştir**

     Vpn'e mümkün olduğunca otomatik olarak bağlanıp yeniden bağlanmak için iş profilinde bir VPN istemcisi ayarlayın. Belirli bir cihazda her zaman açık VPN için tek bir VPN istemcisi yapılandırılabilir, bu nedenle tek bir cihaza dağıtılmış birden fazla VPN ilkesine sahip olmadığınızdan emin olun.

   - VPN **istemcisi** açılan listesinde Özel'i seçin

     Bu durumda özel VPN, Web Koruma özelliğini sağlamak için kullanılan Uç Nokta VPN için Defender'dır.

     > [!NOTE]
     > Uç Nokta için Microsoft Defender VPN'nin otomatik kurulumu için kullanıcının cihazında yüklü olması gerekir.

   - Google **Play Store'da** Uç Nokta için Microsoft Defender paketinin Paket Kimliği'ne girin. Defender uygulamasının URL'si için <https://play.google.com/store/apps/details?id=com.microsoft.scmx>Paket Kimliği **com.microsoft.scmx**

   - **Kilitleme modu** Yapılandırılmadı (Varsayılan)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Yapılandırma ayarları sekmesinin altındaki Bağlantı bölmesi" lightbox="images/3autosetupofvpn.png":::

4. **Ödev**

   Atamalar **sayfasında** , bu uygulama yapılandırma ilkesi'nin atandığı kullanıcı grubunu seçin. Dahil **olacak grupları** seçin ve uygun grubu seçin ve sonra da Sonraki'yi **seçin**. Burada seçilen grup genellikle Android uygulamasında seçtiğiniz grupla Uç Nokta için Microsoft Defender olur.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Cihaz kısıtlamalarında cihazlar yapılandırma profili Atama bölmesi" lightbox="images/4autosetupofvpn.png":::

5. Sonraki sayfada **yer alan Gözden Geçir +** Oluştur sayfasında, tüm bilgileri gözden geçirin ve ardından Oluştur'a **tıklayın**.
Cihaz yapılandırma profili artık seçili kullanıcı grubuna atanır.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="A devices configuration profile 'provision for Review + create" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Durumu denetleme ve ekleme işlemini tamamlama

1. Cihaz Yükleme Durumu'Uç Nokta için Microsoft Defender tıklayarak Android'de cihaz yükleme **durumunu onaylayın**. Cihazın burada görüntülendiğinden emin olun.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Cihaz yükleme durumu bölmesi" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. Cihazda, iş profiline gidip ekleme durumunu **doğrulaabilirsiniz**. Uç nokta için Defender'ın kullanılabilir olduğunu ve Kişisel olarak sahip olunan cihazlara iş **profiliyle kayıtlı olduğunu onaylayın**. Kurumsal'a ait **,** tam olarak yönetilen bir cihaza kayıtlıysanız, cihazda uç nokta için Defender'ın kullanılabilir olduğunu onaylayan tek bir profiliniz olur.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Uygulama görüntüleme bölmesi" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Uygulama yüklü olduğunda uygulamayı açın ve izinleri kabul edin; ardından ekleme başarılı olacaktır.

    :::image type="content" source="images/MDE_new.png" alt-text="Mobil cihazda Uç Nokta için Microsoft Defender uygulaması görüntüsü" lightbox="images/MDE_new.png":::

4. Bu aşamada cihaz Android'de Uç Nokta için Defender'a başarıyla alındı. Bunu mobil portalda [Microsoft 365 Defender](https://security.microsoft.com) Stok sayfasına giderek **doğruleyebilirsiniz**.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Uç Nokta için Microsoft Defender portalı" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender genel bakış](microsoft-defender-endpoint-android.md)
- [Android Uç Nokta için Microsoft Defender'da özellikleri yapılandırma](android-configure.md)
