---
title: Microsoft Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma
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
description: Microsoft Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma hakkında bilgi edinin
ms.openlocfilehash: e5cc3ff25895f3eb7557566eb8a38722a1aee35f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632365"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme ve çıkarma

macOS cihazlarını Microsoft Purview çözümlerine eklemek için Intune kullanabilirsiniz.

> [!IMPORTANT]
> macOS ***cihazlarınıza dağıtılmış*** Uç Nokta için Microsoft Defender (MDE) yoksa bu yordamı kullanın

**Şunlar için geçerlidir:**

- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)

## <a name="before-you-begin"></a>Başlamadan önce

- [macOS cihazlarınızın Intune eklenip Şirket Portalı](/mem/intune/fundamentals/deployment-guide-platform-macos) [uygulamasına](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) kaydedildiğinden emin olun. 
- [Microsoft Endpoint Manager merkezine](https://endpoint.microsoft.com/#home) erişiminiz olduğundan emin olun.
- Bu, macOS sürüm Catalina 10.15 ve üzerini destekler.
- Yapılandırma güncelleştirmelerini atayacağınız kullanıcı gruplarını oluşturun.
- macOS cihazlarınıza v95+ Edge tarayıcısını yükleme 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Microsoft Intune kullanarak macOS cihazlarını Microsoft Purview çözümlerine ekleme

MacOS cihazını Uyumluluk çözümlerine ekleme altı aşamalı bir işlemdir.

1. [Sistem yapılandırma profilleri oluşturma](#create-system-configuration-profiles)
1. [Cihaz ekleme paketini alma](#get-the-device-onboarding-package)
1. [Ekleme paketini dağıtma](#deploy-the-onboarding-package)
1. [Sistem uzantısını etkinleştirme](#enable-system-extension)
1. [Yükleme paketini alma](#get-the-installation-package)
1. [Yükleme paketini dağıtma](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Sistem yapılandırma profilleri oluşturma

1. Bu yordam için bu dosyalara ihtiyacınız olacaktır.

|için gereken dosya |Kaynak |
|---------|---------|
|Paket ekleme    |uyumluluk portalı **Ekleme paketinden** indirildi, dosya adı *DeviceComplianceOnboarding.xml* |
|Erişilebilir -lik |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
tam disk erişimi     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Ağ dosyalayıcısı| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Sistem uzantıları |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE tercihi     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|MAU tercihi|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Yükleme paketi     |uyumluluk portalından indirildi **Yükleme paketi**, dosya adı *\*wdav.pkg*\* |

> [!TIP]
> *.mobileconfig* dosyalarını tek tek veya aşağıdakileri içeren [tek bir birleştirilmiş dosyada](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) indirebilirsiniz:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sistem uzantıları
>
>Bu dosyalardan herhangi biri güncelleştirildiyse, birleştirilmiş dosyayı veya tek tek güncelleştirilmiş dosyayı tek tek indirmeniz gerekir.

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

2. **Microsoft Endpoint Manager merkezi** > **Cihazlar** > **Yapılandırma profillerini** açın.

1. Seç: **Profil oluştur** 

1. Seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'u** seçin

1. Bu örnekteki *AccessibilityformacOS* gibi bir profil adı seçin. **İleri**'yi seçin.

1. Yapılandırma profili dosyası olarak 1. adımda indirdiğiniz **accessibility.mobileconfig** dosyasını seçin.

1. **İleri'yi** seçin

1. **Atamalar** sekmesinde, bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve **İleri'yi** seçin.

1. Ayarlarınızı gözden geçirin ve **oluştur'u** seçerek yapılandırmayı dağıtın.

1. Aşağıdakiler için profil oluşturmak için 3-11 arası adımları yineleyin:
    1. **fulldisk.mobileconfig** dosyası
    1. **com.microsoft.autoupdate2.xml** dosyası
    1. MDE tercihleri **com.microsoft.wdav.xml** dosyası
        1. Virüsten koruma altyapısını `passive mode` = `true` veya `false`ayarlayın. Yalnızca DLP dağıtıyorsanız kullanın `true`. DLP ve Uç Nokta için Microsoft Defender (MDE) dağıtırken bir değer kullanın `false` veya atayın.
    1. **netfilter.mobileconfig**
 
1. **Cihaz** > **Yapılandırma profillerini** açın, oluşturduğunuz profilleri orada görmeniz gerekir.

1. **Yapılandırma profilleri** sayfasında, az önce oluşturduğunuz profili seçin, bu örnekte *ErişilebilirlikformacOS* ve cihaz listesini ve yapılandırma profilinin dağıtım durumunu görmek için **Cihaz durumu'nu** seçin.

### <a name="get-the-device-onboarding-package"></a>Cihaz ekleme paketini alma

1. **Uyumluluk merkezinde** **Ayarlar** > **Cihaz Ekleme'yi** açın ve **Ekleme'yi** seçin.
 
1. **Ekleme işlemini başlatmak için İşletim sistemini seçin** için **macOS'u** seçin.
 
1. **Dağıtım yöntemi** için **Mobil Cihaz Yönetimi/Microsoft Intune'ı** seçin.
 
1. **Ekleme paketini indir'i** seçin. Bu, *DeviceComplianceOnboarding.xml* dosyasındaki ekleme kodunu içerir.

### <a name="deploy-the-onboarding-package"></a>Ekleme paketini dağıtma

1. **Microsoft Endpoint Manager merkezi** > **Cihazlar** > **Yapılandırma profillerini** açın.

1. Seçin: **Profil oluştur**. 

1. Seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Özel**

1. **Oluştur'u** seçin

1. Bu örnekteki *OnboardingPackage* gibi bir profil adı seçin. **İleri**'yi seçin.

1. Yapılandırma profili dosyası olarak *DeviceComplianceOnboarding.xml* dosyasını seçin.

1. **İleri'yi** seçin

1. **Atamalar** sekmesinde, bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve **İleri'yi** seçin.

1. Ayarlarınızı gözden geçirin ve **oluştur'u** seçerek yapılandırmayı dağıtın.

### <a name="enable-system-extension"></a>Sistem uzantısını etkinleştirme

1. **Microsoft Endpoint Manager merkezinde** **Yapılandırma Profilleri'nin** altında **Profil Oluştur'u** seçin

1. Seçin:
    1. **Platform = macOS**
    1. **Profil türü = Şablonlar**
    1. **Şablon adı = Uzantılar**

1. **Oluştur'u** seçin

1. **Temel Bilgiler** sekmesinde bu yeni profile bir ad verin.

1. **Yapılandırma ayarları** sekmesinde **Sistem Uzantıları'nı** genişletin.

1. **Paket tanımlayıcısı** ve **Ekip tanımlayıcısı** altında bu değerleri ayarlayın

|Paket tanımlayıcısı  |Ekip tanımlayıcısı  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. **Atamalar** sekmesinde, bu yapılandırmaları dağıtmak istediğiniz grubu ekleyin ve **İleri'yi** seçin.

1. Yapılandırmayı dağıtmak için **İleri'yi** seçin.

### <a name="get-the-installation-package"></a>Yükleme paketini alma

1. **Uyumluluk merkezinde** **Ayarlar** > **Cihaz Ekleme'yi** açın ve **Ekleme'yi** seçin.
 
1. **Ekleme işlemini başlatmak için işletim sistemini seçin** **için macOS'u** seçin
 
1. **Dağıtım yöntemi** için **Mobil Cihaz Yönetimi/Microsoft Intune'ı** seçin
 
1. **Yükleme paketini indir'i** seçin. Bu size *wdav.pkg* dosyasını verir.

> [!IMPORTANT]
> *wdav.pkg* dosyasını dağıtmadan önce. paketi Intune aracılığıyla, *Mac için Intune Uygulama Sarmalama Araçları* kullanılarak *wdav.pkg.intunemac* biçiminde yeniden biçimlendirilmelidir.
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Microsoft DLP yükleme paketini dağıtma

1. *wdav.pkg* dosyasını uygun biçime dönüştürmek ve Intune aracılığıyla dağıtmak için [macOS iş kolu (LOB) uygulamalarını Microsoft Intune ekleme'deki](/mem/intune/apps/lob-apps-macos) yordamları izleyin.

## <a name="offboard-macos-devices-using-intune"></a>Intune kullanarak macOS cihazlarını çıkarma

> [!NOTE]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru dahil olmak üzere cihazdaki veriler altı aya kadar saklanır.

2. **Microsoft Endpoint Manager merkezinde** **Cihazlar** > **Yapılandırma profillerini** açın, oluşturduğunuz profilleri orada görmeniz gerekir.

1. **Yapılandırma profilleri** sayfasında *wdav.pkg.intunemac* profilini seçin.

1. Cihazların listesini ve yapılandırma profilinin dağıtım durumunu görmek için **Cihaz** durumu'nu seçin

1. **Özellikler** ve **Atamalar'ı** açma

1. Grubu atamadan kaldırın. Bu işlem *wdav.pkg.intunemac* paketini kaldırır ve macOS cihazını Uyumluluk çözümlerinden kaldırır.
