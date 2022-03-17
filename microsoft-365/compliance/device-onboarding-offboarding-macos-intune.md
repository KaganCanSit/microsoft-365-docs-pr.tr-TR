---
title: MacOS cihazlarını Microsoft 365 (önizleme) kullanarak Uyumluluk çözümlerine ekleme Microsoft Intune çıkarabilirsiniz
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: MacOS cihazlarını Microsoft Intune (önizleme) kullanarak Uyumluluk çözümlerine nasıl Microsoft 365 alın ve çıkarabilirsiniz
ms.openlocfilehash: 5f8dd27490992e15d53dfc10311ce7b23b99683a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526520"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview"></a>Intune (önizleme) kullanarak MacOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma

Intune'u kullanarak macOS cihazlarını uyumluluk çözümlerine Microsoft 365 kullanabilirsiniz.

> [!IMPORTANT]
> MacOS cihazlarınıza ***dağıtılmış*** Uç Nokta için Microsoft Defender (MDE) yoksa bu yordamı kullanın

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Başlamadan önce

- [MacOS cihazlarınızı Intune'a ekli olduğundan ve cihazlarında Mobil](/mem/intune/fundamentals/deployment-guide-platform-macos) Şirket Portalı [olun](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Merkezin Erişim Merkezi'ne [Microsoft Endpoint Manager.](https://endpoint.microsoft.com/#home)
- Bu, macOS Catalina 10.15 ve daha yeni sürümünü destekler.
- Yapılandırma güncelleştirmelerini atayydığınız kullanıcı gruplarını oluşturun.
- v95+ Edge tarayıcısını macOS cihazlarınıza yükleme 


## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>MacOS cihazlarını Uyumluluk çözümleri Microsoft 365 uyumluluk çözümlerine Microsoft Intune

Uyumluluk çözümlerine bir macOS cihazı ekleme altı aşamalı bir işlemdir.

1. [Sistem yapılandırma profilleri oluşturma](#create-system-configuration-profiles)
1. [Cihaz ekleme paketini al](#get-the-device-onboarding-package)
1. [Ekleme paketini dağıtma](#deploy-the-onboarding-package)
1. [Sistem uzantısını etkinleştir](#enable-system-extension)
1. [Yükleme paketini al](#get-the-installation-package)
1. [Yükleme paketini dağıtma](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Sistem yapılandırma profilleri oluşturma

1. Bu yordam için bu dosyalara ihtiyacınız vardır.

|için gereken dosya |kaynak |
|---------|---------|
|Ekleme paketi    |Uyumluluk portalı Ekleme **paketinden indirilmiş,** dosya adı *DeviceComplianceOnboarding.xml* |
|erişilebilirlik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[full ssd.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Ağ dosyaleyicisi| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Sistem uzantıları |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE tercihi     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|MAU tercihi|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Yükleme paketi     |uyumluluk portalı Yükleme **paketinden indirilen** *wdav.pkg\* dosya adı*\* |

> [!TIP]
> *.mobileconfig dosyalarını tek tek* veya içeren tek [bir birleşik dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - full ssd.mobileconfig
> - netfilter.mobileconfig
> - sistem uzantıları
>
>Bu tek tek dosyalardan herhangi biri güncelleştirilmişse, birleştirilmiş dosyayı ya da tek tek güncelleştirilmiş dosyayı yeniden indirmeniz gerekir.

<!--2. Copy this code and save it in a file named `com.microsoft.autoupdate2.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
            <key>PayloadUUID</key>
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```
-->

2. Microsoft Endpoint Manager **centerDevicesConfiguration** >  >  **profillerini açın**.

1. Seç: **Profil oluştur** 

1. Şunları seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'a**

1. Profil için, bu örnekteki *AccessibilityformacOS gibi bir* ad seçin. **İleri**'yi seçin.

1. Yapılandırma profili dosyası olarak 1. adımda indirdiğiniz **accessibility.mobileconfig** dosyasını seçin.

1. Sonraki'yi **seçin**

1. Atamalar **sekmesinde,** bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve Sonraki'yi **seçin**.

1. Ayarlarınızı gözden geçirebilirsiniz ve **yapılandırmayı dağıtmak için** Oluştur'a tıklayın.

1. Aşağıdaki profiller için profil oluşturmak için 3-11. adımları yinele:
    1. **full ssd.mobileconfig** dosyası
    1. **com.microsoft.autoupdate2.xml** dosya
    1. Dosya için MDE **com.microsoft.wdav.xml** tercihleri
        1. virüsten koruma altyapısını veya `passive mode` = `true` .`false` Yalnızca `true`DLP dağıtımında kullanın. DLP `false` ve Uç Nokta için Microsoft Defender'ın (MDE) dağıtımında değer kullanın veya bu değeri attayın.
    1. **netfilter.mobileconfig**
 
1. Cihazları **Yapılandırma** >  **profillerini açın**, oluşturduğunuz profilleri burada görüyor olun.

1. Yapılandırma **profilleri sayfasında**, bu örnekte *AccessibilityformacOS'ta* yeni oluşturduğunuz profili seçin ve cihazların listesini ve yapılandırma profilinin dağıtım  durumunu görmek için Cihaz durumu'u seçin.

### <a name="get-the-device-onboarding-package"></a>Cihaz ekleme paketini al

1. Uyumluluk **merkezi'nde**, **Ayarlar** >  **Device Ekleme'yi açın ve** **Ekleme'yi seçin**.
 
1. ekleme **işlemini başlatmak için işletim sistemini seçin için** **macOS'u seçin**.
 
1. Dağıtım **yöntemi için Mobil** Cihaz **Yönetimi/Cihazı Yönetimi'Microsoft Intune**.
 
1. Ekleme **paketini indir'i seçin**. Bu,DeviceComplianceOnboarding.xml *dosyasındaki eklemeDeviceComplianceOnboarding.xml* içerir.

### <a name="deploy-the-onboarding-package"></a>Ekleme paketini dağıtma

1. Microsoft Endpoint Manager **centerDevicesConfiguration** >  >  **profillerini açın**.

1. Seçin: **Profil oluştur**. 

1. Şunları seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'a**

1. Bu örnekteki *OnboardingPackage gibi bir profil* adı seçin. **İleri**'yi seçin.

1. Yapılandırma *DeviceComplianceOnboarding.xml* olarak en son dosyayı seçin.

1. Sonraki'yi **seçin**

1. Atamalar **sekmesinde,** bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve Sonraki'yi **seçin**.

1. Ayarlarınızı gözden geçirebilirsiniz ve **yapılandırmayı dağıtmak için** Oluştur'a tıklayın.

### <a name="enable-system-extension"></a>Sistem uzantısını etkinleştir

1. Merkezin **Microsoft Endpoint Manager Profilleri'nin** **altında Profil** **Oluştur'a tıklayın**

1. Şunları seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Uzantılar**

1. **Oluştur'a**

1. Temel **Bilgiler sekmesinde** , bu yeni profile bir ad girin.

1. Yapılandırma ayarları **sekmesinde Sistem** **Uzantıları'nın kapsamını genişletin**.

1. Paket **tanımlayıcısı ve** **Ekip tanımlayıcısı altında** bu değerleri ayarlayın

|Paket tanımlayıcısı  |Ekip tanımlayıcısı  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Atamalar **sekmesinde,** bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve Sonraki'yi **seçin**.

1. **Yapılandırmayı dağıtmak** için Sonraki'yi seçin.

### <a name="get-the-installation-package"></a>Yükleme paketini al

1. Uyumluluk **merkezi'nde**, **Ayarlar** >  **Device Ekleme'yi açın ve** **Ekleme'yi seçin**.
 
1. ekleme **işlemini başlatmak için işletim sistemini seçin için** **macOS'u seçin**
 
1. Dağıtım **yöntemi olarak Mobil** Cihaz **Yönetimi/Cihaz Yönetimi'Microsoft Intune**
 
1. Yükleme paketini **indir'i seçin**. Bu, *wdav.pkg dosyasını size* verecek.

> [!IMPORTANT]
> *wdav.pkg'yi dağıtmadan önce.* paketi, *Mac için Intune* Uygulama Kaydırma Araçları kullanılarak *wdav.pkg.intunemac* biçiminde yeniden biçimlendirilmiş olmalıdır.
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Microsoft DLP yükleme paketini dağıtma

1. *wdav.pkg* dosyasını doğru biçime dönüştürmek ve Intune aracılığıyla dağıtmak için [Microsoft Intune'e macOS iş hattı (LOB)](/mem/intune/apps/lob-apps-macos) uygulamaları ekleme'de yer alan yordamları izleyin.

## <a name="offboard-macos-devices-using-intune"></a>Intune kullanan offboard macOS cihazları

> [!NOTE]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler altı aya kadar korunur.

2. **Merkezin Microsoft Endpoint Manager** **DevicesConfiguration** >  profillerini açın, oluşturduğunuz profilleri burada görüyor olun.

1. Yapılandırma **profilleri sayfasında** *wdav.pkg.intunemac profilini* seçin.

1. Cihazların **listesini ve** yapılandırma profilinin dağıtım durumunu görmek için Cihaz durumu'mu seçin

1. Özellikleri **ve** **Atamaları açma**

1. Grubu ödevden kaldırın. Bu, *wdav.pkg.intunemac* paketini kaldırır ve macOS cihazına Uyumluluk çözümlerinden çıkartır.
