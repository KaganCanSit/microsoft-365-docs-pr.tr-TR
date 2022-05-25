---
title: Mac'te Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma
description: Kurumsal ortamlarda Mac'te Uç Nokta için Microsoft Defender güncelleştirmelerini denetleyin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, updates, deploy
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
ms.openlocfilehash: 4612c7ca68ab0b55fa2a2f28821cb5baef6ff6e9
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669352"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'da Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [macOS üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar.

macOS'da Uç Nokta için Microsoft Defender güncelleştirmek için Microsoft AutoUpdate (MAU) adlı bir program kullanılır. Varsayılan olarak, MAU güncelleştirmeleri günlük olarak otomatik olarak denetler, ancak bunu haftalık, aylık veya el ile değiştirebilirsiniz.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Güncelleştirmeleri yazılım dağıtım araçlarınızı kullanarak dağıtmaya karar verirseniz MAU'yu yazılım güncelleştirmelerini el ile denetleyecek şekilde yapılandırmanız gerekir. MAU'un kuruluşunuzdaki Mac'ler için güncelleştirmeleri nasıl ve ne zaman denetleyebileceğini yapılandırmak için tercihleri dağıtabilirsiniz.

## <a name="use-msupdate"></a>msupdate kullanma

MAU, güncelleştirmelerin ne zaman uygulanacağı üzerinde daha hassas denetime sahip olmaları için BT yöneticileri için tasarlanmış *msupdate* adlı bir komut satırı aracı içerir. Bu aracın nasıl kullanılacağına ilişkin yönergeler [güncelleştirme Office Mac msupdate kullanılarak](/deployoffice/mac/update-office-for-mac-using-msupdate) bulunabilir.

MAU'da, macOS üzerindeki Uç Nokta için Microsoft Defender için uygulama *tanımlayıcısı WDAV00'dür*. macOS'da Uç Nokta için Microsoft Defender için en son güncelleştirmeleri indirmek ve yüklemek için terminal penceresinden aşağıdaki komutu yürütebilirsiniz:

```dos
cd /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app/Contents/MacOS
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Microsoft AutoUpdate için tercihleri ayarlama

Bu bölümde MAU'yu yapılandırmak için kullanılabilecek en yaygın tercihler açıklanmaktadır. Bu ayarlar, kuruluşunuzun kullandığı yönetim konsolu aracılığıyla yapılandırma profili olarak dağıtılabilir. Aşağıdaki bölümlerde bir yapılandırma profili örneği gösterilmiştir.

### <a name="set-the-channel-name"></a>Kanal adını ayarlama

Kanal, MAU aracılığıyla sunulan güncelleştirmelerin türünü ve sıklığını belirler. içindeki cihazlar ve `Current`içindeki `Beta` `Preview` cihazlardan önce yeni özellikleri deneyebilir.

Kanal, `Current` ürünün en kararlı sürümünü içerir.

> [!IMPORTANT]
> Microsoft AutoUpdate 4.29 sürümünden önce kanalların adları farklıydı:
>
> - `Beta` adlandırılmıştır `InsiderFast` (Insider Hızlı)
> - `Preview` adlandırılmıştır `External` (Insider Yavaş)
> - `Current` adlandırılmıştır `Production`

> [!TIP]
> Yeni özellikleri önizlemek ve erken geri bildirim sağlamak için kuruluşunuzdaki `Beta` bazı cihazları veya `Preview`için yapılandırmanız önerilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|Channelname|
|**Veri türü**|Dize|
|**Olası değerler**|Beta <p> Önizleme <p> Şu anki|
|||

> [!WARNING]
> Bu ayar, Microsoft AutoUpdate aracılığıyla güncelleştirilen tüm uygulamalar için kanalı değiştirir. Kanalı yalnızca macOS Uç Nokta için Microsoft Defender değiştirmek için, öğesini istenen kanalla değiştirdikten `[channel-name]` sonra aşağıdaki komutu yürütür:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Güncelleştirme denetimi sıklığını ayarlama

MAU'un güncelleştirmeleri arama sıklıklarını değiştirin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|UpdateCheckFrequency|
|**Veri türü**|Tamsayı|
|**Varsayılan değer**|720 (dakika)|
|**Açıklama ekleme**|Bu değer dakika cinsinden ayarlanır.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>MAU'nin güncelleştirmelerle etkileşim kurma şeklini değiştirme

MAU'nin güncelleştirmeleri arama şeklini değiştirin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|HowToCheck|
|**Veri türü**|Dize|
|**Olası değerler**|El ile <p> Otomatik Denetim <p> Otomatik İndir|
|**Açıklama ekleme**|AutomaticDownload'un mümkünse bir indirme gerçekleştireceğini ve sessizce yükleneceğini unutmayın.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>"Güncelleştirmeleri Denetle" düğmesinin etkinleştirilip etkinleştirilmediğini değiştirme

Yerel kullanıcıların Microsoft AutoUpdate kullanıcı arabirimindeki "Güncelleştirmeleri Denetle" seçeneğine tıklayıp tıklayamayacağını değiştirin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|EnableCheckForUpdatesButton|
|**Veri türü**|Boole|
|**Olası değerler**|True (varsayılan) <p> False|
|||

### <a name="disable-insider-checkbox"></a>Insider'ı devre dışı bırak onay kutusu

"Office Insider Programına Katıl..." yapmak için true olarak ayarlayın onay kutusu kullanılamıyor/kullanıcılara gri görüntülendi.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|DisableInsiderCheckbox|
|**Veri türü**|Boole|
|**Olası değerler**|False (varsayılan) <p> True|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>MAU'dan gönderilen telemetriyi sınırlama

Minimum sinyal verileri, uygulama kullanımı ve ortam ayrıntıları göndermek için false olarak ayarlayın.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|SendAllTelemetryEnabled|
|**Veri türü**|Boole|
|**Olası değerler**|True (varsayılan) <p> False|
|||

## <a name="example-configuration-profile"></a>Örnek yapılandırma profili

Aşağıdaki yapılandırma profili şunları yapmak için kullanılır:

- Cihazı Üretim kanalına yerleştirme
- Güncelleştirmeleri otomatik olarak indirme ve yükleme
- Kullanıcı arabiriminde "Güncelleştirmeleri denetle" düğmesini etkinleştirin
- Cihazdaki kullanıcıların Insider kanallarına kaydolmasına izin verme

> [!WARNING]
> Aşağıdaki yapılandırma örnek bir yapılandırmadır ve ayarların düzgün bir şekilde gözden geçirilmesi ve yapılandırmaların uyarlanması gerekmeden üretimde kullanılmamalıdır.

> [!TIP]
> Yeni özellikleri önizlemek ve erken geri bildirim sağlamak için kuruluşunuzdaki `Beta` bazı cihazları veya `Preview`için yapılandırmanız önerilir.

### <a name="jamf"></a>JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
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
</plist>
```

### <a name="intune"></a>Intune

```XML
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

MAU'yu yapılandırmak için bu yapılandırma profilini kuruluşunuzun kullandığı yönetim aracından dağıtabilirsiniz:

- JAMF'den bu yapılandırma profilini karşıya yükleyin ve Tercih Etki Alanı'nı *com.microsoft.autoupdate2* olarak ayarlayın.
- Intune bu yapılandırma profilini karşıya yükleyin ve özel yapılandırma profili adını *com.microsoft.autoupdate2* olarak ayarlayın.

## <a name="resources"></a>Kaynaklar

- [msupdate başvurusu](/deployoffice/mac/update-office-for-mac-using-msupdate)
