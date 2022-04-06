---
title: Intune Mac'te Uç Nokta için Microsoft Defender tabanlı dağıtım
description: Mac Uç Nokta için Microsoft Defender'i kullanarak E-posta Microsoft Intune.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: a511405c2d8fb4753debbadf0744d6277639648b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475267"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Intune macOS'ta Uç Nokta için Microsoft Defender tabanlı dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [macOS Uç Nokta için Microsoft Defender üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu konu başlığında, Uç Nokta için Microsoft Defender macOS üzerinde Intune. Başarılı bir dağıtım için aşağıdaki adımların tamamlanmasını gerekir:

1. [Ekleme paketini indirin](#download-the-onboarding-package)
1. [İstemci cihazı kurulumu](#client-device-setup)
1. [Sistem uzantılarını onaylama](#approve-system-extensions)
1. [Sistem Yapılandırması profilleri oluşturma](#create-system-configuration-profiles)
1. [Uygulamayı yayımla](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün [önkoşullarının Uç Nokta için Microsoft Defender için macOS'ta](microsoft-defender-endpoint-mac.md) ana sürüm sayfasına bakın.

## <a name="overview"></a>Genel bakış

Aşağıdaki tabloda, Mac'lerde postalarınızı dağıtmak ve yönetmek için Uç Nokta için Microsoft Defender adımlar özetlenmiştir ve bu Intune. Daha ayrıntılı adımları aşağıda bulabilirsiniz.

<br>

****

|Adım|Örnek dosya adları|BundleIdentifier|
|---|---|---|
|[Ekleme paketini indirin](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Sistem Uzantısını Onaylamak için Uç Nokta için Microsoft Defender](#approve-system-extensions)|MDATP_SysExt.xml|Yok|
|[Sistem için Çekirdek Uzantısını Uç Nokta için Microsoft Defender](#download-the-onboarding-package)|MDATP_KExt.xml|Yok|
|[Posta dosyalarına tam disk Uç Nokta için Microsoft Defender](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Ağ Uzantısı ilkesi](#network-filter)|MDATP_NetExt.xml|Yok|
|[Microsoft AutoUpdate'i (MAU) yapılandırma](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[Uç Nokta için Microsoft Defender ayarlarını değiştirme](mac-preferences.md#intune-full-profile) <p> **Not:** macOS için üçüncü taraf BIR AV'yi çalıştırmayı planlıyorsanız, olarak `passiveMode` ayarlayın `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Otomatik Uç Nokta için Microsoft Defender MS AutoUpdate (MAU) bildirimlerini yapılandırma](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 veya com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirin

Microsoft 365 Defender portaldan ekleme paketlerini indirin:

1. Uygulama Microsoft 365 Defender Uç Noktaları Cihaz **yönetimi Ayarlar** \> **Ekleme'ye** \>  \> **gidin**.

2. İşletim sistemini **macOS olarak ve dağıtım** yöntemini Mobil Cihazlar /Cihaz Yönetimi **olarak Microsoft Intune**.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Ekleme ayarları sayfası" lightbox="images/macos-install-with-intune.png":::

3. Ekleme **paketini indir'i seçin**. Dosyayı aynı _WindowsDefenderATPOnboardingPackage.zip_ farklı bir dizine kaydedin.

4. Dosyanın içeriğini .zip:

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

Sıradaki adım, ihtiyaçlara uygun sistem Uç Nokta için Microsoft Defender oluşturmaktır.
Cihaz [Microsoft Endpoint Manager, Cihazlar](https://endpoint.microsoft.com/) Yapılandırması **profilleri'ni** \> açın.

### <a name="onboarding-blob"></a>Ekleme blobu

Bu profil, lisans bilgilerini Uç Nokta için Microsoft Defender. Bu profil Uç Nokta için Microsoft Defender, lisansının olmadığını bildirecek.

1. Yapılandırma **Profilleri'nin** altında **Profil Oluştur'a tıklayın**.
1. **PlatformmacOS**=, **Profil** **türüTemplates'i**= seçin. **Şablon adı**= **Özel.** **Oluştur'a tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Özel Yapılandırma Profili oluşturma sayfası" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Profil için bir ad seçin. Örneğin, "macOS için Bulut için Defender uç nokta ekleme". **İleri**'ye tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Özel Yapılandırma Profili adı alanı" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Yapılandırma profili adı için "MacOS için Uç nokta ekleme için Defender" gibi bir ad seçin.
1. Bir dağıtım [kanalı seçin](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Yukarıdaki ekleme paketinden WindowsDefenderATPOnboarding.xml yapılandırma profili dosyası olarak intune/WindowsDefenderATPOnboarding.xml seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Özel Yapılandırma Profili için bir dosyadan yapılandırmayı içeri aktarma" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. **İleri**'ye tıklayın.
1. Ödev sekmesinde **cihazları ata.** Sonraki'ye **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Özel yapılandırma profili - atama" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Gözden Geçir ve **Oluştur**.
1. Cihaz **Yapılandırması** \> **profillerini açın**, oluşturduğunuz profili burada görebilirler.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Özel yapılandırma profilinin tamamlanması" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Sistem Uzantılarını Onaylama

Bu profil macOS 10.15 (Catalina) veya daha yeni sürümler için gereklidir. Bu, eski macOS'ta yok sayılacak.

1. Yapılandırma **Profilleri'nin** altında **Profil Oluştur'a tıklayın**.
1. **PlatformmacOS**=, **Profil** **türüTemplates'i**= seçin. **Şablon adı**= **Uzantılar**. **Oluştur'a tıklayın**.
1. Temel **Bilgiler sekmesinde** , bu yeni profile bir ad girin.
1. Yapılandırma **ayarları sekmesinde** , Sistem **Uzantıları'nın İzin verilen** sistem uzantıları bölümünde **şu girişleri ekleyin** :

    |Paket tanımlayıcısı|Ekip tanımlayıcısı|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Sistem uzantısının ayarları" lightbox="images/mac-system-extension-intune2.png":::

1. Ödevler **sekmesinde,** bu profili Tüm Cihazlarda Tüm **Kullanıcılar'a & attayabilirsiniz**.
1. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="kernel-extensions"></a>Kernel Extensions

Bu profil macOS 10.15 (Catalina) veya daha eski için gereklidir. Daha yeni macOS'ta yok sayılacak.

> [!CAUTION]
> Apple Silicon (M1) cihazları KEXT'i desteklemez. KEXT ilkelerinden oluşan bir yapılandırma profili yüklemesi bu cihazlarda başarısız olur.

1. Yapılandırma **Profilleri'nin** altında **Profil Oluştur'a tıklayın**.
1. **PlatformmacOS**=, **Profil** **türüTemplates'i**= seçin. **Şablon adı**= **Uzantılar**. **Oluştur'a tıklayın**.
1. Temel **Bilgiler sekmesinde** , bu yeni profile bir ad girin.
1. Yapılandırma ayarları **sekmesinde Kernel** **Extensions'i genişletin**.
1. Ekip **tanımlayıcısını** **UBF8T346G9 olarak ayarlayın ve Sonraki'ye** **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Sistem uzantısının Çekirdek ayarları" lightbox="images/mac-system-extension-intune2.png":::

1. Ödevler **sekmesinde,** bu profili Tüm Cihazlarda Tüm **Kullanıcılar'a & attayabilirsiniz**.
1. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="full-disk-access"></a>Tam Disk Erişimi

   > [!CAUTION]
   > macOS 10.15 (Catalina) yeni güvenlik ve gizlilik iyileştirmeleri içerir. Bu sürümden başarak, uygulamalar varsayılan olarak açık izin alınmadan diskte bazı konumlara (Belgeler, İndirmeler, Masaüstü, vb.) erişemez. Bu iznin olmaması Uç Nokta için Microsoft Defender, cihazınızı tam olarak koruyamaz.
   >
   > Bu yapılandırma profili, posta dosyalarına Tam Disk Uç Nokta için Microsoft Defender. Daha önce bu yapılandırmayı Uç Nokta için Microsoft Defender Intune, dağıtımı bu yapılandırma profiliyle güncelleştirmenizi öneririz.

uygulama [**depomuzdan full yapılandırılması**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Endpoint Full Disk Access için Defender"ı kullanın ve **full blob.mobileconfig'i** Yapılandırma profil adı olarak indirin.

### <a name="network-filter"></a>Ağ Filtresi

MacOS'ta Uç Nokta Algılama ve Yanıt özellikleri Uç Nokta için Microsoft Defender, yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

Mobil [**depolama depomuzdan netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Uç Nokta Ağ Filtresi için Defender"ı kullanın ve indirilen **netfilter.mobileconfig** Öğesini Yapılandırma profil adı olarak uygulayın.

### <a name="notifications"></a>Bildirimler

Bu profil, macOS'Uç Nokta için Microsoft Defender Microsoft Otomatik Güncelleştirmesi'nin bildirimleri macOS 10.15 (Catalina) veya daha yeni sürümlerde kullanıcı arabiriminde görüntülemesine izin vermek için kullanılır.

[**Notif.mobileconfig'i**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Uç Nokta Bildirimleri için Defender"ı kullanın ve **notif.mobileconfig'i** Yapılandırma profil adı olarak indirin.

### <a name="view-status"></a>Durumu Görüntüle

Kayıt Intune ilgili cihazlara bu değişiklikler yayıldıktan sonra, bunları Cihaz durumunu izle'nin **altında** \> **listelenmiş olarak görüntüebilirsiniz**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Cihaz durumunun görünümü" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Uygulamayı yayımla

Bu adım, kayıtlı makinelerde Uç Nokta için Microsoft Defender dağıtımına olanak sağlar.

1. Uygulama [Microsoft Endpoint Manager Uygulamalar'a](https://endpoint.microsoft.com/) **gidin**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Uygulamaya genel bakış sayfası" lightbox="images/mdatp-8-app-before.png":::

1. macOS için platforma > öğesini ve Ekle'> seçin.
1. Uygulama **türümacOS'u**= seçin, Seç'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Belirli uygulama türü" lightbox="images/mdatp-9-app-type.png":::

1. Varsayılan değerleri tutmak için Sonraki'yi **tıklatın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Uygulama özellikleri sayfası" lightbox="images/mdatp-10-properties.png":::

1. Ödev ekleyin, Sonraki'ye **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Ödev Intune sayfası" lightbox="images/mdatp-11-assignments.png":::

1. Gözden Geçir ve **Oluştur**.
1. Tüm uygulamalar **listesinde görmek** \> **için Platform** \> **macOS'a** göre Uygulamalar'ı ziyaret edin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Uygulama listeleri sayfası" lightbox="images/mdatp-12-applications.png":::

Daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender kullanarak macOS cihazlarına posta Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Yukarıda da belirtildiği gibi, tüm gerekli yapılandırma profillerini oluşturmanız ve bunları tüm makinelere basmanız gerekir.

## <a name="client-device-setup"></a>İstemci cihazı kurulumu

Standart veya standart yükleme dışında bir Mac cihaz için özel bir Şirket Portalı [gerekli değil](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Cihaz yönetimini onaylayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Cihaz yönetimini onayla sayfası" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    Sistem **Tercihlerini Aç'ı** seçin, **listede Yönetim Profili'nin** yerini bulun ve Onayla... **öğesini seçin**. Yönetim Profiliniz Doğrulanmış olarak **görüntülenir**:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Yönetim profili sayfası" lightbox="images/mdatp-4-managementprofile.png":::

2. **Devam'ı** seçin ve kaydı tamamlamak için.

   Artık daha fazla cihaz kaydolabilirsiniz. Ayrıca, sistem yapılandırmasını ve uygulama paketlerini sağlamayı tamamladikten sonra bunları daha sonra kaydolabilirsiniz.

3. Cihaz Intune Cihazları **Yönet'i** \>  \> **açın**. Aşağıda listelenenler arasında cihazınızı görüyoruz:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Tüm Cihazlar sayfası" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>İstemci cihazı durumunu doğrulama

1. Yapılandırma profilleri cihazlarınıza dağıtıldıktan sonra Mac **aygıtınızda Sistem** \> **Tercihleri** Profilleri'ne gidin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Sistem tercihleri sayfası" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Sistem Tercihleri Profilleri sayfası" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Aşağıdaki yapılandırma profillerini olduğunu ve yüklü olduğunu doğrulayın. Yönetim **Profili,** en Intune profilidir. _Wdav-config_ ve _wdav-kext_, aşağıdaki bağlantılara eklenen sistem yapılandırma Intune:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Profiller sayfası" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. Sağ üst köşede Uç Nokta için Microsoft Defender simgesi de gösterilir:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Durum çubuğundaki Uç Nokta için Microsoft Defender simgesi" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Sorun giderme

Sorun: Lisans bulunamadı.

Çözüm: Bu adımları kullanarak bir cihaz profili oluşturmak için yukarıdaki adımları WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Günlüğe kaydetme yükleme sorunları

Hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz. Günlük [yükleme sorunları](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Kaldırma

İstemci [cihazlarından](mac-resources.md#uninstalling) macOS'ta Uç Nokta için Microsoft Defender hakkında ayrıntılar için bkz. Kaldırma.
