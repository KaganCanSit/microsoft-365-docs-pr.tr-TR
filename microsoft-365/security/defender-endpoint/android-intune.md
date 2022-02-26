---
title: Android'de Uç Nokta için Microsoft Defender'ı Microsoft Intune
description: Android cihazlarda Uç Nokta için Microsoft Defender'ın nasıl dağıtın açık Microsoft Intune
keywords: microsoft, defender, Endpoint için Microsoft Defender, mde, android, yükleme, dağıtma, kaldırma,
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
ms.openlocfilehash: 380e2ecb9ee8df7eb066eef600f796685215662f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "62974127"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Android'de Uç Nokta için Microsoft Defender'ı Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kayıtlı cihazlarda Android'de Uç nokta için Defender Intune Şirket Portalı dağıtmayı öğrenin. Intune cihaz kaydı hakkında daha fazla bilgi için bkz [. Cihazınızı kaydetme](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Android'de Uç Nokta için Defender artık [Google Play'de kullanılabilir](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Intune'dan Google Play'e bağlanarak Cihaz Yöneticisi ve Android uygulaması genelinde Uç Nokta için Defender'ı Enterprise kullanabilirsiniz.
>
> Uygulamanın güncelleştirmeleri Google Play üzerinden otomatik olarak 65 gün içinde 65 gün içinde 65 gün içinde 65 gün içinde otomatik olarak

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Cihaz Yöneticisi tarafından kayıt yapılan cihazlarda dağıtma

**Android'de Uç Nokta için Deploy Defender Intune Şirket Portalı - Cihaz Yöneticisi tarafından kayıt yapılan cihazlar**

Android cihazlarda Uç Nokta için Defender'ı dağıtmayı Intune Şirket Portalı - Cihaz Yöneticisi tarafından kayıtlı cihazlar.

### <a name="add-as-android-store-app"></a>Android Store uygulaması olarak ekle

1. Uygulama [Microsoft Endpoint Manager , Uygulamalar](https://go.microsoft.com/fwlink/?linkid=2109431) Android Uygulamaları  \> **Android mağazası ekle uygulaması'ne** \> **gidin \> ve Seç'i** **seçin**.

   :::image type="content" alt-text="Yönetim Merkezi Microsoft Endpoint Manager Android Store uygulaması ekle'nin görüntüsü." source="images/mda-addandroidstoreapp.png" lightbox="images/mda-addandroidstoreapp.png":::

2. Uygulama **ekle sayfasında** ve Uygulama *Bilgileri bölümüne şunları* girin:

   - **Ad**
   - **Açıklama**
   - **Publisher** olarak devam.
   - **Olarak uygulama mağazası URL'si** https://play.google.com/store/apps/details?id=com.microsoft.scmx (Uç nokta uygulaması Google Play Store URL'si için Defender)

   Diğer alanlar isteğe bağlıdır. **İleri**'yi seçin.

   :::image type="content" alt-text="Yönetim Merkezi Microsoft Endpoint Manager bilgileri ekle'nin görüntüsü." source="images/mda-addappinfo.png" lightbox="images/mda-addappinfo.png":::

3. Ödevler *bölümünde* Gerekli bölümüne gidin **ve Grup** **ekle'yi seçin.** Ardından, Android uygulamasında Uç Nokta için Defender'ı hedeflemek istediğiniz kullanıcı grubunu seçebilirsiniz. **Seç'i ve** ardından **Sonraki'yi seçin**.

    > [!NOTE]
    > Seçilen kullanıcı grubu Intune'a kayıtlı kullanıcılardan oluşur.
    >
    > :::image type="content" alt-text="Yönetim Merkezi Microsoft Endpoint Manager seçilen kullanıcı gruplarının resmi." source="images/363bf30f7d69a94db578e8af0ddd044b.png" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. Gözden Geçir **+Oluştur bölümünde** , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**.

    Birkaç dakika içinde, Uç Nokta için Defender uygulaması başarıyla oluşturulabilir ve sayfanın sağ üst köşesinde bir bildirim görüntülenir.

    :::image type="content" alt-text="Uç nokta Microsoft Endpoint Manager Defender'ın Yönetim Merkezi bildiriminin görüntüsü." source="images/86cbe56f88bb6e93e9c63303397fc24f.png" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Görüntülenen uygulama bilgileri sayfasında, Monitör bölümünde Cihaz yükleme durumunu seçerek cihaz yükleme işleminin başarıyla tamamlanmıştır. 

    :::image type="content" alt-text="Yönetim Merkezi Microsoft Endpoint Manager yüklemesi görüntüsü." source="images/513cf5d59eaaef5d2b5bc122715b5844.png" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Ekleme işlemini tamamlama ve durumu denetleme

1. Cihaza Android'de Uç Nokta için Defender yüklendikten sonra uygulama simgesini gösterilir.

    ![Simge.](images/7cf9311ad676ec5142002a4d0c2323ca.jpg)

2. Uç nokta için Microsoft Defender uygulama simgesine dokunun ve uygulamayı ekleme işlemini tamamlamak için ekrandaki yönergeleri izleyin. Ayrıntılar arasında, Android'de Uç Nokta için Defender tarafından gereken Android izinlerinin son kullanıcı kabulü yer amektedir.

3. Başarılı bir şekilde işe alım sırasında cihaz, portalda bulunan Cihazlar listesinde Microsoft 365 Defender başlar.

    :::image type="content" alt-text="Uç nokta portalı için Defender'da cihazın görüntüsü." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Android veya Enterprise cihazlarda dağıtma

Android'de Uç Nokta için Defender, android Enterprise cihazları destekler.

Intune tarafından desteklenen kayıt seçenekleri hakkında daha fazla bilgi için bkz. [Kayıt Seçenekleri](/mem/intune/enrollment/android-enroll).

**Şu anda, İş profiline sahip ve Kurumsal'a ait tam kullanıcı cihaz kayıtlarına sahip olan, kişisel olarak sahip olunan cihazlar dağıtım için desteklemektedir.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Android'de Uç Nokta için Microsoft Defender'ı Yönetilen Google Play uygulaması olarak ekleme

Yönetilen Google Play'inize Uç Nokta için Microsoft Defender uygulamasını eklemek için aşağıdaki adımları izleyin.

1. Uygulama [Microsoft Endpoint Manager , Uygulamalar](https://go.microsoft.com/fwlink/?linkid=2109431) Android Uygulamaları **Ekle'ye** \> **gidin ve** \> Yönetilen **Google Play uygulaması'ni seçin**.

    :::image type="content" alt-text="Yönetim merkezi Microsoft Endpoint Manager Google Play'in resmi." source="images/579ff59f31f599414cedf63051628b2e.png" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Yönetilen Google Play sayfanız sonradan yüklenirken, arama kutusuna gidin ve 'ı girin `Microsoft Defender`. Aramanız Yönetilen Google Play'de Uç Nokta için Microsoft Defender uygulamasını görüntülemeli. Uygulamalar arama sonucunda Uç Nokta için Microsoft Defender uygulamasına tıklayın.

    ![Yönetim merkezi Microsoft Endpoint Manager arama görüntüsü.](images/0f79cb37900b57c3e2bb0effad1c19cb.png)

3. Sonraki ortaya çıkan Uygulama açıklaması sayfasında, Uç nokta için Defender'da uygulama ayrıntılarını görebilirsiniz. Sayfada bilgileri gözden geçirip Onayla'ya **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Yönetilen Google Play'in ekran görüntüsü.](images/07e6d4119f265037e3b80a20a73b856f.png)

4. Uç Nokta için Defender'ın bu uygulamanın çalışması için edinilen izinler size sunulacaktır. Bunları gözden geçirip **Onayla'ya seçin**.

    ![Uç nokta önizleme uygulaması onayı için Defender'ın ekran görüntüsü.](images/206b3d954f06cc58b3466fb7a0bd9f74.png)

5. Onay ayarları sayfası görüntülenir. Sayfada, Android'deki Uç Nokta için Defender'ın sor sor olabileceği yeni uygulama izinlerini işleme tercihinizi onaylar. Seçenekleri gözden geçirerek tercih ettiğiniz seçeneği belirleyin. **Bitti'yi seçin**.

    Varsayılan olarak, yönetilen Google Play uygulaması yeni **izinler isterken Onaylandır'ı seçer**.

    > [!div class="mx-imgBorder"]
    > ![Bildirimler sekmesinin resmi.](images/ffecfdda1c4df14148f1526c22cc0236.png)

6. İzinleri işleme seçimi yapıldıktan sonra, Uç Nokta için Microsoft **Defender'ı** uygulamalar listeniz ile eşitlemek için Eşitle'yi seçin.

    > [!div class="mx-imgBorder"]
    > ![Eşitleme sayfasının görüntüsü.](images/34e6b9a0dae125d085c84593140180ed.png)

7. Eşitleme birkaç dakika içinde tamamlanır.

    :::image type="content" alt-text="Android uygulamasının resmi." source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Android uygulamaları **ekranında** Yenile düğmesini seçin; uygulamalar listesinde Uç Nokta için Microsoft Defender görünür olmalıdır.

    :::image type="content" alt-text="Android uygulamaları listesinin görüntüsü." source="images/fa4ac18a6333335db3775630b8e6b353.png" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Uç Nokta için Defender, Intune aracılığıyla yönetilen cihazlar için uygulama yapılandırma ilkelerini destekler. Bu özellik geçerli Android izinlerini otomatik olarak almak için kullanılabilir, dolayısıyla son kullanıcının bu izni veya izinlerini kabul etme ihtiyacı olmaz.

    1. Uygulamalar sayfasında **,** İlke ve Uygulama **> ilkeleri'ne gidin > Yönetilen > ekleyin**.

       :::image type="content" alt-text="Android tarafından Microsoft Endpoint Manager yönetilen cihazların yönetim merkezi görüntüsü." source="images/android-mem.png":::

    1. Uygulama **yapılandırma ilkesi oluştur sayfasında** aşağıdaki ayrıntıları girin:

        - Ad: Uç Nokta için Microsoft Defender.
        - **Android platform olarak Enterprise'ı** seçin.
        - Yalnızca **Profil Türü olarak İş** Profili'ne tıklayın.
        - Uygulama **Seç'e tıklayın**, **Microsoft Defender ATP'yi seçin**, **Tamam'ı ve** ardından Sonraki'yi seçin.

        :::image type="content" alt-text="Uygulama yapılandırma ilkesi oluşturma sayfasının görüntüsü." source="images/android-create-app.png" lightbox="images/android-create-app.png":::

    1. Destek **Ayarlar** İzinler bölümüne gidip, desteklenen izinlerin listesini görüntülemek için Ekle'ye tıklayın. İzin Ekle bölümünde aşağıdaki izinleri seçin:

       - Dış depolama (okuma)
       - Dış depolama (yazma)

       Sonra **Tamam**’ı seçin.

       :::image type="content" alt-text="Android uygulama yapılandırma ilkesi oluşturma resmi." source="images/android-create-app-config.png" lightbox="images/android-create-app-config.png":::

    1. Şimdi hem listelenen izinleri hem de artık İzin durumu açılır listesinde otomatik yetkiyi seçerek ve sonra da Sonraki'yi seçerek otomatik olarak veri **alabilirsiniz**.

       :::image type="content" alt-text="Android otomatik olarak uygulama yapılandırma ilkesi oluştur'u resmi." source="images/android-auto-grant.png" lightbox="images/android-auto-grant.png":::

    1. Atamalar **sayfasında** , bu uygulama yapılandırma ilkesi'nin atandığı kullanıcı grubunu seçin. Dahil **etmek için grupları seç'e** tıklayın, uygun grubu seçin ve ardından Sonraki'yi **seçin**. Burada seçilen grup genellikle Uç Nokta Android uygulaması için Microsoft Defender'ı ataydığınız grupla aynıdır.

       :::image type="content" alt-text="Uygulama yapılandırma ilkesi oluşturma resmi." source="images/android-select-group.png" lightbox="images/android-select-group.png":::

    1. Sonraki sayfada **yer alan Gözden Geçir +** Oluştur sayfasında, tüm bilgileri gözden geçirin ve ardından Oluştur'a **tıklayın**.

        Depolama iznini otomatik olarak almak için Uç Nokta için Defender'ın uygulama yapılandırma ilkesi artık seçili kullanıcı grubuna atanır.

        > [!div class="mx-imgBorder"]
        > ![Android gözden geçirme uygulama yapılandırma ilkesi oluşturma resmi.](images/android-review-create.png)

10. Özellikler **Atamaları Düzenleme listesinde** Microsoft \>  \> Defender ATP **uygulaması'ı** \> **seçin**.

    :::image type="content" alt-text="Uygulama listesinin resmi." source="images/mda-properties.png" lightbox="images/mda-properties.png":::

11. Uygulamayı bir kullanıcı grubuna *Gerekli* uygulama olarak attayabilirsiniz. Cihazın bir sonraki *eşitlemesi sırasında uygulama üzerinden* iş profiline otomatik olarak Şirket Portalı. Bu atama, Gerekli bölümüne (Grup  ekle) \> gidin **, kullanıcı** grubunu seçin ve Seç'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Uygulama düzenleme sayfasının görüntüsü.](images/ea06643280075f16265a596fb9a96042.png)

12. Uygulamayı **Düzenle sayfasında** , yukarıda girilen tüm bilgileri gözden geçirebilirsiniz. Sonra ödevi başlamak **için Gözden Geçir + Kaydet'i** **ve sonra** yeniden Kaydet'i seçin.

### <a name="auto-setup-of-always-on-vpn"></a>Her Zaman Açık VPN'nin Otomatik Kurulumu

Uç Nokta için Defender, Intune aracılığıyla yönetilen cihazlar için cihaz yapılandırma ilkelerini destekler. Bu özellik, Android veya kayıtlı cihazlarda Her Zaman **Açık VPN'nin** otomatik olarak kurulumu Enterprise, dolayısıyla son kullanıcının ekleme sırasında VPN hizmetini ayarlaması gerekmektedir.

1. **Cihazlar'da** Yapılandırma **Profilleri Profil Platformu** \> Oluştur **Android** **Enterprise** \> \>

   Cihaz **kayıt türünüz** bağlı olarak, aşağıdaki seçeneklerden birinin altında Cihaz kısıtlamaları'ı seçin:
   - **Tümüyle Yönetilen, Ayrılmış ve Corporate-Owned Profili**
   - **Kişisel olarak sahip olunan İş Profili**

   **Oluştur**’u seçin.

   :::image type="content" alt-text="Cihazları yapılandırma profili Oluşturma resmi." source="images/1autosetupofvpn.png":::

2. **Yapılandırma Ayarlar** Yapılandırma **profilini benzersiz** olarak tanımlamak **için** bir Ad ve Açıklama girin.

   :::image type="content" alt-text="Cihazların yapılandırma profili Ad ve Açıklama görüntüsü." source="images/2autosetupofvpn.png":::

3. **Bağlantı'yi** seçin ve VPN'yi yapılandıryın:

   - Her **Zaman Açık VPN'yi Etkinleştir**

     Mümkün olduğunda VPN'ye otomatik olarak bağlanıp yeniden bağlanmak için iş profilinde bir VPN istemcisi kurabilirsiniz. Belirli bir cihazda her zaman açık VPN için tek bir VPN istemcisi yapılandırılabilir, bu nedenle tek bir cihaza dağıtılmış birden fazla VPN ilkesine sahip olmadığınızdan emin olun.

   - VPN **istemcisi** açılan listesinde Özel'i seçin

     Bu durumda özel VPN, Web Koruma özelliğini sağlamak için kullanılan Uç Nokta VPN için Defender'dır.

     > [!NOTE]
     > Bu VPN'nin otomatik kurulumu için Uç Nokta için Microsoft Defender uygulamasının kullanıcının cihazına yüklenmiş olması gerekir.

   - Google Play **Store'da** Uç Nokta için Microsoft Defender uygulamasının Paket Kimliği girin. Defender uygulamasının URL'si için <https://play.google.com/store/apps/details?id=com.microsoft.scmx>Paket Kimliği **com.microsoft.scmx**

   - **Kilitleme modu** Yapılandırılmadı (Varsayılan)

     ![Cihazların yapılandırma profilinin Her zaman açık VPN'yi etkinleştirmesi görüntüsü.](images/3autosetupofvpn.png)
      :::image type="content" alt-text="Cihazların yapılandırma profilinin Her zaman açık VPN'yi etkinleştirmesi görüntüsü." source="images/3autosetupofvpn.png":::

4. **Ödev**

   Atamalar **sayfasında** , bu uygulama yapılandırma ilkesi'nin atandığı kullanıcı grubunu seçin. Dahil **olacak grupları** seçin ve uygun grubu seçin ve sonra da Sonraki'yi **seçin**. Burada seçilen grup genellikle Uç Nokta Android uygulaması için Microsoft Defender'ı ataydığınız grupla aynıdır.

   ![Cihazlar yapılandırma profili Atama resmi.](images/4autosetupofvpn.png)

5. Sonraki sayfada **yer alan Gözden Geçir +** Oluştur sayfasında, tüm bilgileri gözden geçirin ve ardından Oluştur'a **tıklayın**.
Cihaz yapılandırma profili artık seçili kullanıcı grubuna atanır.

   ![Cihazlar yapılandırma profilinin Gözden Geçirme ve Oluştur'a görüntüsü.](images/5autosetupofvpn.png)

## <a name="check-status-and-complete-onboarding"></a>Durumu denetleme ve ekleme işlemini tamamlama

1. Cihaz Yükleme Durumu'na tıklayarak Android'de Uç Nokta için Microsoft Defender'ın **yükleme durumunu onaylayın**. Cihazın burada görüntülendiğinden emin olun.

    > [!div class="mx-imgBorder"]
    > ![Cihaz yükleme durumunun resmi.](images/900c0197aa59f9b7abd762ab2b32e80c.png)

2. Cihazda, iş profiline gidip ekleme durumunu **doğrulaabilirsiniz**. Uç nokta için Defender'ın kullanılabilir olduğunu ve Kişisel olarak sahip olunan cihazlara iş **profiliyle kayıtlı olduğunu onaylayın**. Kurumsal'a ait **,** tam olarak yönetilen bir cihaza kayıtlıysanız, cihazda uç nokta için Defender'ın kullanılabilir olduğunu onaylayan tek bir profiliniz olur.

    ![Mobil cihazda uygulamanın resmi.](images/c2e647fc8fa31c4f2349c76f2497bc0e.png)

3. Uygulama yüklü olduğunda uygulamayı açın ve izinleri kabul edin; ardından ekleme başarılı olacaktır.

    ![Uç nokta uygulaması için Microsoft Defender ile mobil cihaz görüntüsü](images/MDE_new.png)

4. Bu aşamada cihaz Android'de Uç Nokta için Defender'a başarıyla alındı. Bunu mobil portalda [Microsoft 365 Defender](https://security.microsoft.com) Stok sayfasına giderek **doğruleyebilirsiniz**.

    :::image type="content" alt-text="Uç nokta portalı için Microsoft Defender görüntüsü." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender'a Genel Bakış](microsoft-defender-endpoint-android.md)
- [Android'de Uç Nokta için Microsoft Defender özelliklerini yapılandırma](android-configure.md)
