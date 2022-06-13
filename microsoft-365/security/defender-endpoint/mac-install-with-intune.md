---
title: Mac'te Uç Nokta için Microsoft Defender için Intune tabanlı dağıtım
description: Microsoft Intune kullanarak Mac'e Uç Nokta için Microsoft Defender yükleyin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 4c2c1f7c11c57ca45411b74023807077f73ba8bf
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044116"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>macOS Uç Nokta için Microsoft Defender için Intune tabanlı dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [macOS üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu konuda, Intune aracılığıyla macOS üzerinde Uç Nokta için Microsoft Defender nasıl dağıtılacağı açıklanmaktadır. Başarılı bir dağıtım için aşağıdaki adımların tümünün tamamlanması gerekir:

1. [Ekleme paketini indirme](#download-the-onboarding-package)
1. [İstemci cihazı kurulumu](#client-device-setup)
1. [Sistem uzantılarını onaylama](#approve-system-extensions)
1. [Sistem Yapılandırması profilleri oluşturma](#create-system-configuration-profiles)
1. [Uygulamayı yayımlama](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümü için önkoşulların ve sistem gereksinimlerinin açıklaması için [macOS sayfasındaki ana Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md) bakın.

## <a name="overview"></a>Genel bakış

Aşağıdaki tabloda, Intune aracılığıyla Mac'lerde Uç Nokta için Microsoft Defender dağıtmak ve yönetmek için uygulamanız gereken adımlar özetlenmektedir. Aşağıda daha ayrıntılı adımlar sunulmaktadır.

<br>

****

|Adım|Örnek dosya adları|BundleIdentifier|
|---|---|---|
|[Ekleme paketini indirme](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Uç Nokta için Microsoft Defender için Sistem Uzantısını Onayla](#approve-system-extensions)|MDATP_SysExt.xml|Yok|
|[Uç Nokta için Microsoft Defender için Çekirdek Uzantısını Onayla](#download-the-onboarding-package)|MDATP_KExt.xml|Yok|
|[Uç Nokta için Microsoft Defender tam disk erişimi verme](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Ağ Uzantısı ilkesi](#network-filter)|MDATP_NetExt.xml|Yok|
|[Microsoft AutoUpdate'i (MAU) yapılandırma](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[yapılandırma ayarlarını Uç Nokta için Microsoft Defender](mac-preferences.md#intune-full-profile) <p> **Not:** macOS için bir üçüncü taraf AV çalıştırmayı planlıyorsanız olarak ayarlayın `passiveMode` `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Uç Nokta için Microsoft Defender ve MS AutoUpdate (MAU) bildirimlerini yapılandırma](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 veya com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirme

Ekleme paketlerini Microsoft 365 Defender portalından indirin:

1. Microsoft 365 Defender portalında **Ayarlar** \> **Uç Noktalar** \> **Cihaz yönetimi** \> **Ekleme'ye** gidin.

2. İşletim sistemini **macOS** ve dağıtım yöntemini **Mobil Cihaz Yönetimi / Microsoft Intune** olarak ayarlayın.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Ekleme ayarları sayfası" lightbox="images/macos-install-with-intune.png":::

3. **Ekleme paketini indir'i** seçin. Aynı dizine _WindowsDefenderATPOnboardingPackage.zip_ olarak kaydedin.

4. .zip dosyasının içeriğini ayıklayın:

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

## <a name="create-system-configuration-profiles"></a>Sistem Yapılandırması profilleri oluşturma

Sonraki adım, ihtiyaç Uç Nokta için Microsoft Defender sistem yapılandırma profilleri oluşturmaktır.
[Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com/) **Cihazlar** \> **Yapılandırma profilleri'ni** açın.

### <a name="onboarding-blob"></a>Blob ekleme

Bu profil, Uç Nokta için Microsoft Defender lisans bilgilerini içerir. Bu profil olmadan Uç Nokta için Microsoft Defender lisanslanmadığını bildirir.

1. **Yapılandırma Profilleri'nin** altında **Profil Oluştur'u** seçin.
1. **Platform**= **macOS**, **Profil türü Şablonları'nı**= seçin. **Şablon adı**= **Özel**. **Oluştur'a** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Özel Yapılandırma Profili oluşturma sayfası" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Profil için "Bulut için Defender veya macOS için uç nokta ekleme" gibi bir ad seçin. **İleri**'ye tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Özel Yapılandırma Profili adı alanı" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Yapılandırma profili adı için bir ad seçin; örneğin, "macOS için Uç Nokta ekleme için Defender".
1. [Bir dağıtım kanalı](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices) seçin.
1. Yukarıdaki ekleme paketinden yapılandırma profili dosyası olarak ayıkladığınız intune/WindowsDefenderATPOnboarding.xml öğesini seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Özel Yapılandırma Profili için bir dosyadan yapılandırma içeri aktarma" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. **İleri**'ye tıklayın.
1. **Atama** sekmesinde cihazları atayın. **İleri'ye** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Özel yapılandırma profili - atama" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Gözden Geçir ve **Oluştur'u seçin**.
1. **Cihaz** \> **Yapılandırma profillerini** açın, oluşturduğunuz profili burada görebilirsiniz.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Özel yapılandırma profilinin tamamlanması" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Sistem Uzantılarını Onayla

Bu profil macOS 10.15 (Catalina) veya daha yeni sürümler için gereklidir. Eski macOS yoksayılır.

1. **Yapılandırma Profilleri'nin** altında **Profil Oluştur'u** seçin.
1. **Platform**= **macOS**, **Profil türü Şablonları'nı**= seçin. **Şablon adı**= **Uzantılar**. **Oluştur'a** tıklayın.
1. **Temel Bilgiler** sekmesinde, bu yeni profile bir ad verin.
1. **Yapılandırma ayarları** sekmesinde Sistem **Uzantıları'nı** genişletin, **İzin verilen sistem uzantıları bölümüne aşağıdaki girdileri** ekleyin:

    |Paket tanımlayıcısı|Ekip tanımlayıcısı|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Sistem uzantısının ayarları" lightbox="images/mac-system-extension-intune2.png":::

1. **Atamalar** sekmesinde, bu profili **Tüm Kullanıcılar & Tüm cihazlar'a atayın**.
1. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="kernel-extensions"></a>Çekirdek Uzantıları

Bu profil macOS 10.15 (Catalina) veya üzeri için gereklidir. Daha yeni macOS yoksayılır.

> [!CAUTION]
> Apple Silicon (M1) cihazları KEXT'yi desteklemez. KEXT ilkelerini içeren bir yapılandırma profilinin yüklenmesi bu cihazlarda başarısız olur.

1. **Yapılandırma Profilleri'nin** altında **Profil Oluştur'u** seçin.
1. **Platform**= **macOS**, **Profil türü Şablonları'nı**= seçin. **Şablon adı**= **Uzantılar**. **Oluştur'a** tıklayın.
1. **Temel Bilgiler** sekmesinde, bu yeni profile bir ad verin.
1. **Yapılandırma ayarları** sekmesinde **Çekirdek Uzantıları'nı** genişletin.
1. **Takım tanımlayıcısını** **UBF8T346G9** olarak ayarlayın ve **İleri'ye** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-kernel-extension-intune2.png" alt-text="Çekirdek uzantıları için izin verilen ekip tanımlayıcıları." lightbox="images/mac-kernel-extension-intune2.png":::

1. **Atamalar** sekmesinde, bu profili **Tüm Kullanıcılar & Tüm cihazlar'a atayın**.
1. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="full-disk-access"></a>Tam Disk Erişimi

   > [!CAUTION]
   > macOS 10.15 (Catalina) yeni güvenlik ve gizlilik geliştirmeleri içerir. Bu sürümden başlayarak, uygulamalar varsayılan olarak açık onay olmadan disk üzerindeki belirli konumlara (Belgeler, İndirmeler, Masaüstü vb.) erişemez. Bu onay olmadığında, Uç Nokta için Microsoft Defender cihazınızı tam olarak koruyamaz.
   >
   > Bu yapılandırma profili, Uç Nokta için Microsoft Defender Için Tam Disk Erişimi verir. daha önce Uç Nokta için Microsoft Defender Intune aracılığıyla yapılandırdıysanız, dağıtımı bu yapılandırma profiliyle güncelleştirmenizi öneririz.

[GitHub depomuzdan](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles) [**fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) dosyasını indirin.

Profil adı olarak "Uç Nokta Tam Disk Erişimi için Defender"ı ve Yapılandırma profili adı olarak **fulldisk.mobileconfig** dosyasını indirerek [blobu](#onboarding-blob) yukarıdan ekleme yönergelerini izleyin.

### <a name="network-filter"></a>Ağ Filtresi

Uç Nokta Algılama ve Yanıt özelliklerinin bir parçası olarak macOS'da Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender portalına bildirir. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesine izin verir.

[GitHub depomuzdan](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles) [**netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) dosyasını indirin.

Profil adı olarak "Uç Nokta Ağ Filtresi için Defender"ı ve Yapılandırma profili adı olarak **netfilter.mobileconfig** dosyasını indirerek [blobu](#onboarding-blob) yukarıdan ekleme yönergelerini izleyin.

### <a name="notifications"></a>Bildirim

Bu profil, macOS ve Microsoft Otomatik Güncelleştirme'de Uç Nokta için Microsoft Defender macOS 10.15 (Catalina) veya daha yeni sürümlerde kullanıcı arabiriminde bildirimleri görüntülemesine izin vermek için kullanılır.

[GitHub depomuzdan](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles) [**notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) dosyasını indirin.

Profil adı olarak "Uç Nokta Bildirimleri için Defender" ve Yapılandırma profili adı olarak **notif.mobileconfig** dosyasını indirerek [yukarıdan blob](#onboarding-blob) ekleme yönergelerini izleyin.

### <a name="view-status"></a>Durumu Görüntüle

Intune değişiklikleri kayıtlı cihazlara yayıldıktan sonra cihaz **durumunu** **izleme** \> altında listelendiğini görebilirsiniz:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Cihaz durumunun görünümü" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Uygulamayı yayımlama

Bu adım, kayıtlı makinelere Uç Nokta için Microsoft Defender dağıtılmasına olanak tanır.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com/) **Uygulamalar'ı** açın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Uygulamanın genel bakış sayfası" lightbox="images/mdatp-8-app-before.png":::

1. Platforma göre > macOS > Ekle'yi seçin.
1. **Uygulama türü'nü**= seçin **macOS** **Seç'e** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Belirli uygulama türü" lightbox="images/mdatp-9-app-type.png":::

1. Varsayılan değerleri koru'ya tıklayın, **İleri'ye** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Uygulama özellikleri sayfası" lightbox="images/mdatp-10-properties.png":::

1. Ödev ekleyin, **İleri'ye** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Intune atama bilgileri sayfası" lightbox="images/mdatp-11-assignments.png":::

1. Gözden Geçir ve **Oluştur'u seçin**.
1. Tüm uygulamalar listesinde görmek için **Platforma** \> göre **Uygulamalar** \> **macOS** ziyaret edebilirsiniz.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Uygulama listeleri sayfası" lightbox="images/mdatp-12-applications.png":::

Daha fazla bilgi için bkz[. Microsoft Intune kullanarak macOS cihazlara Uç Nokta için Microsoft Defender ekleme](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Yukarıda açıklandığı gibi tüm gerekli yapılandırma profillerini oluşturmanız ve bunları tüm makinelere göndermeniz gerekir.

## <a name="client-device-setup"></a>İstemci cihazı kurulumu

Standart bir [Şirket Portalı yüklemesinin](/intune-user-help/enroll-your-device-in-intune-macos-cp) ötesinde bir Mac cihazı için özel sağlama gerekmez.

1. Cihaz yönetimini onaylayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Cihaz yönetimini onayla sayfası" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    **Sistem Tercihlerini Aç'ı** seçin, listede **Yönetim Profili'ni** bulun ve **Onayla...** öğesini seçin. Yönetim Profiliniz **Doğrulandı** olarak görüntülenir:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Yönetim profili sayfası" lightbox="images/mdatp-4-managementprofile.png":::

2. **Devam'ı** seçin ve kaydı tamamlayın.

   Artık daha fazla cihaz kaydedebilirsiniz. Ayrıca, sistem yapılandırmasını ve uygulama paketlerini sağlamayı tamamladıktan sonra bunları daha sonra da kaydedebilirsiniz.

3. Intune'de **Cihazları** \> **Yönet** \> **Tüm cihazlar'ı** açın. Burada cihazınızı listelenenler arasında görebilirsiniz:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Tüm Cihazlar sayfası" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>İstemci cihaz durumunu doğrulama

1. Yapılandırma profilleri cihazlarınıza dağıtıldıktan sonra Mac cihazınızda **Sistem Tercihleri** \> **Profilleri'ni** açın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Sistem tercihleri sayfası" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Sistem Tercihleri Profilleri sayfası" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Aşağıdaki yapılandırma profillerinin mevcut ve yüklü olduğunu doğrulayın. **Yönetim Profili**, Intune sistem profili olmalıdır. _Wdav-config_ ve _wdav-kext_, Intune eklenen sistem yapılandırma profilleridir:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Profiller sayfası" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. Sağ üst köşede Uç Nokta için Microsoft Defender simgesini de görmeniz gerekir:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Durum çubuğundaki Uç Nokta için Microsoft Defender simgesi" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Sorun giderme

Sorun: Lisans bulunamadı.

Çözüm: WindowsDefenderATPOnboarding.xml kullanarak bir cihaz profili oluşturmak için yukarıdaki adımları izleyin.

## <a name="logging-installation-issues"></a>Yükleme sorunlarını günlüğe kaydetme

Bir hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz [. Yükleme sorunlarını günlüğe kaydetme](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Kaldırma

İstemci cihazlarından macOS Uç Nokta için Microsoft Defender kaldırma hakkında ayrıntılı bilgi için bkz. [Kaldırma](mac-resources.md#uninstalling).
