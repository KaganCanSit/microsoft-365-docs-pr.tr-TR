---
title: Mac'te Uç Nokta için Microsoft Defender'a bağlı Intune tabanlı dağıtım
description: Mac'te Uç Nokta için Microsoft Defender'ı, Microsoft Intune.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 4979ee5f3953ced1073779fdcabb7eb361d4911a
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012017"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>macOS üzerinde Uç Nokta için Microsoft Defender için Intune tabanlı dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [macOS'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu konuda, macOS'ta Intune aracılığıyla Uç Nokta için Microsoft Defender'ın nasıl dağıt olduğu açıklanmıştır. Başarılı bir dağıtım için aşağıdaki adımların tamamlanmasını gerekir:

1. [Ekleme paketini indirin](#download-the-onboarding-package)
1. [İstemci cihazı kurulumu](#client-device-setup)
1. [Sistem uzantılarını onaylama](#approve-system-extensions)
1. [Sistem Yapılandırması profilleri oluşturma](#create-system-configuration-profiles)
1. [Uygulamayı yayımla](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün önkoşullarının ve sistem gereksinimlerinin açıklaması için [macOS'ta](microsoft-defender-endpoint-mac.md) uç nokta için ana Microsoft Defender sayfasına bakın.

## <a name="overview"></a>Genel bakış

Aşağıdaki tabloda, Mac'te Uç Nokta için Microsoft Defender'ı Intune aracılığıyla dağıtmak ve yönetmek için atılması gereken adımlar özetlenmiştir. Daha ayrıntılı adımları aşağıda bulabilirsiniz.

<br>

****

|Adım|Örnek dosya adları|BundleIdentifier|
|---|---|---|
|[Ekleme paketini indirin](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Uç Nokta için Microsoft Defender için Sistem Uzantısını Onaylama](#approve-system-extensions)|MDATP_SysExt.xml|Yok|
|[Uç Nokta için Microsoft Defender için Çekirdek Uzantısını Onaylama](#download-the-onboarding-package)|MDATP_KExt.xml|Yok|
|[Uç Nokta için Microsoft Defender'a tam disk erişimi ver](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Ağ Uzantısı ilkesi](#network-filter)|MDATP_NetExt.xml|Yok|
|[Microsoft AutoUpdate'i (MAU) yapılandırma](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[Uç nokta yapılandırma ayarları için Microsoft Defender](mac-preferences.md#intune-full-profile) <p> **Not:** macOS için üçüncü taraf BIR AV'yi çalıştırmayı planlıyorsanız, olarak `passiveMode` ayarlayın `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Uç Nokta ve MS AutoUpdate (MAU) bildirimleri için Microsoft Defender'ı yapılandırma](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 veya com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirin

Microsoft 365 Defender portaldan ekleme paketlerini indirin:

1. Uygulama Microsoft 365 Defender Uç Noktaları Cihaz **yönetimi Ayarlar** \> **Ekleme'ye** \>  \> **gidin**.

2. İşletim sistemini **macOS olarak ve dağıtım** yöntemini Mobil Cihaz Yönetimi **/ Mobil Cihaz Yönetimi / Dağıtım Microsoft Intune**.

    ![Ekleme ayarları ekran görüntüsü.](images/macos-install-with-intune.png)

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

Sonraki adım, Uç nokta için Microsoft Defender'ın ihtiyacı olan sistem yapılandırma profillerini oluşturmaktır.
Cihaz [Microsoft Endpoint Manager, Cihazlar](https://endpoint.microsoft.com/) Yapılandırması **profilleri'ni** \> açın.

### <a name="onboarding-blob"></a>Ekleme blobu

Bu profil, Uç Nokta için Microsoft Defender ile ilgili lisans bilgilerini içerir. Bu profil olmadan, Uç Nokta için Microsoft Defender lisansının olmadığını bildirecek.

1. Yapılandırma **Profilleri'nin** altında **Profil Oluştur'a tıklayın**.
1. **PlatformmacOS**=, **Profil** **türüTemplates'i**= seçin. **Şablon adı**= **Özel.** **Oluştur'a tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Özel Yapılandırma Profili oluşturma.](images/mdatp-6-systemconfigurationprofiles-1.png)

1. Profil için bir ad seçin, örneğin "Bulut için Defender veya macOS için uç nokta ekleme". **İleri**'ye tıklayın.

    > [!div class="mx-imgBorder"]
    > ![Özel Yapılandırma Profili - ad.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. Yapılandırma profili adı için "MacOS için Uç nokta ekleme için Defender" gibi bir ad seçin.
1. Bir dağıtım [kanalı seçin](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Yukarıdaki ekleme paketinden WindowsDefenderATPOnboarding.xml yapılandırma profili dosyası olarak intune/WindowsDefenderATPOnboarding.xml seçin.

    > [!div class="mx-imgBorder"]
    > ![Özel Yapılandırma Profili için bir dosyadan yapılandırmayı içeri aktarın.](images/mdatp-6-systemconfigurationprofiles.png)

1. **İleri**'ye tıklayın.
1. Ödev sekmesinde **cihazları ata.** Sonraki'ye **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Özel Yapılandırma Profili - atama.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. Gözden Geçir ve **Oluştur**.
1. Cihaz **Yapılandırması** \> **profillerini açın**, oluşturduğunuz profili burada görebilirler.

    > [!div class="mx-imgBorder"]
    > ![Özel Yapılandırma Profili - bitti.](images/mdatp-6-systemconfigurationprofiles-3.png)

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
    > ![Sistem uzantısı ayarları.](images/mac-system-extension-intune2.png)

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
    > ![Kernel extension settings.](images/mac-kernel-extension-intune2.png)

1. Ödevler **sekmesinde,** bu profili Tüm Cihazlarda Tüm **Kullanıcılar'a & attayabilirsiniz**.
1. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="full-disk-access"></a>Tam Disk Erişimi

   > [!CAUTION]
   > macOS 10.15 (Catalina) yeni güvenlik ve gizlilik iyileştirmeleri içerir. Bu sürümden başarak, uygulamalar varsayılan olarak açık izin alınmadan diskte bazı konumlara (Belgeler, İndirmeler, Masaüstü, vb.) erişemez. Bu iznin olmamasıyla, Uç Nokta için Microsoft Defender cihazınızı tam olarak koruyamaz.
   >
   > Bu yapılandırma profili, Uç Nokta için Microsoft Defender'a Tam Disk Erişimi sağlar. Daha önce Intune aracılığıyla Uç Nokta için Microsoft Defender'ı yapılandırdıysanız, dağıtımı bu yapılandırma profiliyle güncelleştirmenizi öneririz.

uygulama [**depomuzdan full yapılandırılması**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Endpoint Full Disk Access için Defender"ı kullanın ve **full blob.mobileconfig'i** Yapılandırma profil adı olarak indirin.

### <a name="network-filter"></a>Ağ Filtresi

Uç Nokta Algılama ve Yanıt özellikleri kapsamında, macOS'ta Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

Mobil [**depolama depomuzdan netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Uç Nokta Ağ Filtresi için Defender"ı kullanın ve indirilen **netfilter.mobileconfig** Öğesini Yapılandırma profil adı olarak uygulayın.

### <a name="notifications"></a>Bildirimler

Bu profil, macOS'ta Uç Nokta için Microsoft Defender ve Microsoft Otomatik Güncelleştirme'nin bildirimleri macOS 10.15 (Catalina) veya daha yeni sürümlerde kullanıcı arabiriminde görüntülemesine izin vermek için kullanılır.

[**Notif.mobileconfig'i**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) [GitHub indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Yukarıdan [Onboarding blob](#onboarding-blob) için yönergeleri izleyin, profil adı olarak "Uç Nokta Bildirimleri için Defender"ı kullanın ve **notif.mobileconfig'i** Yapılandırma profil adı olarak indirin.

### <a name="view-status"></a>Durumu Görüntüle

Intune değişiklikleri kayıtlı cihazlara yayıldıktan sonra, bunları Cihaz durumunu izle'nin **altında** \> **listelenmiş olarak görüntüebilirsiniz**:

> [!div class="mx-imgBorder"]
> ![İzlemede Cihaz Durumu görünümü.](images/mdatp-7-devicestatusblade.png)

## <a name="publish-application"></a>Uygulamayı yayımla

Bu adım, kaydolan makinelerde Uç Nokta için Microsoft Defender'ın dağıtımına olanak sağlar.

1. Uygulama [Microsoft Endpoint Manager Uygulamalar'a](https://endpoint.microsoft.com/) **gidin**.

    > [!div class="mx-imgBorder"]
    > ![Uygulama oluşturmak için hazır.](images/mdatp-8-app-before.png)

1. macOS için platforma > öğesini ve Ekle'> seçin.
1. Uygulama **türümacOS'u**= seçin, Seç'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Uygulama türünü belirtin.](images/mdatp-9-app-type.png)

1. Varsayılan değerleri tutmak için Sonraki'yi **tıklatın**.

    > [!div class="mx-imgBorder"]
    > ![Uygulama özellikleri.](images/mdatp-10-properties.png)

1. Ödev ekleyin, Sonraki'ye **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Intune ödev bilgileri ekran görüntüsü.](images/mdatp-11-assignments.png)

1. Gözden Geçir ve **Oluştur**.
1. Tüm uygulamalar **listesinde görmek** \> **için Platform** \> **macOS'a** göre Uygulamalar'ı ziyaret edin.

    > [!div class="mx-imgBorder"]
    > ![Uygulamalar listesi.](images/mdatp-12-applications.png)

Daha fazla bilgi için bkz[. MacOS cihazlarına Uç Nokta için Microsoft Defender Ekleme Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Yukarıda da belirtildiği gibi, tüm gerekli yapılandırma profillerini oluşturmanız ve bunları tüm makinelere basmanız gerekir.

## <a name="client-device-setup"></a>İstemci cihazı kurulumu

Standart veya standart yükleme dışında bir Mac cihaz için özel bir Şirket Portalı [gerekli değil](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Cihaz yönetimini onaylayın.

    > [!div class="mx-imgBorder"]
    > ![Cihaz yönetimi ekran görüntüsünü onaylayın.](images/mdatp-3-confirmdevicemgmt.png)

    Sistem **Tercihlerini Aç'ı** seçin, **listede Yönetim Profili'nin** yerini bulun ve Onayla... **öğesini seçin**. Yönetim Profiliniz Doğrulanmış olarak **görüntülenir**:

    ![Yönetim profili ekran görüntüsü.](images/mdatp-4-managementprofile.png)

2. **Devam'ı** seçin ve kaydı tamamlamak için.

   Artık daha fazla cihaz kaydolabilirsiniz. Ayrıca, sistem yapılandırmasını ve uygulama paketlerini sağlamayı tamamladikten sonra bunları daha sonra kaydolabilirsiniz.

3. Intune'da Cihazları Tüm **cihazları** \> **yönet'i** \> açın. Aşağıda listelenenler arasında cihazınızı görüyoruz:

   > [!div class="mx-imgBorder"]
   > ![Cihaz Ekle ekran görüntüsü.](images/mdatp-5-alldevices.png)

## <a name="verify-client-device-state"></a>İstemci cihazı durumunu doğrulama

1. Yapılandırma profilleri cihazlarınıza dağıtıldıktan sonra Mac **aygıtınızda Sistem** \> **Tercihleri** Profilleri'ne gidin.

    > [!div class="mx-imgBorder"]
    > ![Sistem Tercihleri ekran görüntüsü.](images/mdatp-13-systempreferences.png)

    ![Sistem Tercihleri Profilleri ekran görüntüsü.](images/mdatp-14-systempreferencesprofiles.png)

2. Aşağıdaki yapılandırma profillerini olduğunu ve yüklü olduğunu doğrulayın. Yönetim **Profili** , Intune sistem profili olmalı. _Wdav-config_ ve _wdav-kext_ , Intune'a eklenen sistem yapılandırma profilleridir:

    ![Profiller ekran görüntüsü.](images/mdatp-15-managementprofileconfig.png)

3. Ayrıca sağ üst köşede Uç Nokta için Microsoft Defender simgesini de görüyor olun:

    > [!div class="mx-imgBorder"]
    > ![Durum çubuğunda Uç Nokta için Microsoft Defender simgesinin ekran görüntüsü.](images/mdatp-icon-bar.png)

## <a name="troubleshooting"></a>Sorun giderme

Sorun: Lisans bulunamadı.

Çözüm: Bu adımları kullanarak bir cihaz profili oluşturmak için yukarıdaki adımları WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Günlüğe kaydetme yükleme sorunları

Hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz. Günlük [yükleme sorunları](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Kaldırma

İstemci [cihazlarından](mac-resources.md#uninstalling) macOS'ta Uç Nokta için Microsoft Defender'ı kaldırma hakkında ayrıntılar için bkz. Kaldırma.
