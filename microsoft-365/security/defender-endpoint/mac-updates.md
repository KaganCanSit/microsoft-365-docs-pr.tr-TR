---
title: Mac'te Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma
description: Kurumsal ortamlarda Mac Uç Nokta için Microsoft Defender güncelleştirmelerini kontrol edin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, güncelleştirmeler, dağıtma
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
ms.openlocfilehash: 0b9ddf9693a242b3b8c466cfa1616b62c5eb73b9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469305"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>MacOS'ta Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [macOS Uç Nokta için Microsoft Defender üzerinde Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar.

MacOS Uç Nokta için Microsoft Defender güncelleştirme yapmak için Microsoft AutoUpdate (MAU) adlı bir program kullanılır. Varsayılan olarak, MAU güncelleştirmeleri otomatik olarak günlük olarak denetler, ancak bunu haftalık, aylık veya el ile değiştirebilirsiniz.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Yazılım dağıtım araçlarınızı kullanarak güncelleştirmeleri dağıtmaya karar verirsiniz, MAU'yı yazılım güncelleştirmelerini el ile denetlemesi için yapılandırmanız gerekir. MAU'un kurumda Mac'ler için güncelleştirmeleri nasıl ve ne zaman denetlerken yapılandırma tercihlerini dağıtabilirsiniz.

## <a name="use-msupdate"></a>Msupdate kullan

MAU, güncelleştirmelerin ne zaman uygulandığını daha hassas bir denetime sahip olacak şekilde, IT yöneticilerine göre tasarlanmış, *msupdate* olarak adlandırılan bir komut satırı aracı içerir. Bu aracı kullanma yönergeleri, Güncelleştirme Office Mac [güncelleştirme konusunda bulunabilir](/deployoffice/mac/update-office-for-mac-using-msupdate).

MAU'da, macOS üzerinde Uç Nokta için Microsoft Defender tanımlayıcısı *WDAV00'tur*. macOS üzerinde en son güncelleştirmeleri Uç Nokta için Microsoft Defender yüklemek için Terminal penceresinde aşağıdaki komutu yürütün:

```dos
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Microsoft AutoUpdate için tercihleri ayarlama

Bu bölümde MAU'ları yapılandırmak için kullanılmaktadır. Bu ayarlar, kurumunuzun kullanmakta olduğu yönetim konsolu aracılığıyla bir yapılandırma profili olarak dağıtılabilir. Aşağıdaki bölümlerde bir yapılandırma profili örneği gösterilir.

### <a name="set-the-channel-name"></a>Kanal adını ayarlama

Kanal, MAU aracılığıyla sunulan güncelleştirmelerin türünü ve sıklığını belirler. 'daki cihazlar `Beta` , ve 'daki cihazlardan önce yeni özellikleri deneyebilir `Preview` `Current`.

Kanal `Current` , ürünün en kararlı sürümünü içerir.

> [!IMPORTANT]
> Microsoft AutoUpdate'in 4.29 sürümünden önce kanalların adları farklıydı:
>
> - `Beta` adı verildi `InsiderFast` (Insider Hızlı)
> - `Preview` adı verildi `External` (Insider Yavaş)
> - `Current` adlı `Production`

> [!TIP]
> Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, kurumuzdan bazı cihazları veya için yapılandırmanız `Beta` önerilir `Preview`.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|ChannelName|
|**Veri türü**|Dize|
|**Olası değerler**|Beta <p> Önizleme <p> Geçerli|
|||

> [!WARNING]
> Bu ayar, Microsoft AutoUpdate aracılığıyla güncelleştirilen tüm uygulamaların kanalını değiştirir. MacOS'ta yalnızca Uç Nokta için Microsoft Defender kanalı değiştirmek için, istediğiniz kanalla değiştirdikten sonra `[channel-name]` aşağıdaki komutu yürütün:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Güncelleştirme denetimi sıklığını ayarlama

MAU'un güncelleştirmeleri ne sıklıkta araması olduğunu değiştirme.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|UpdateCheckFrequency|
|**Veri türü**|Tamsayı|
|**Varsayılan değer**|720 (dakika)|
|**Açıklama ekleme**|Bu değer dakika olarak ayarlanır.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>MAU'un güncelleştirmelerle etkileşim kurmasini değiştirme

MAU'un güncelleştirmeleri aramasini değiştirme.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|HowToCheck|
|**Veri türü**|Dize|
|**Olası değerler**|El ile <p> AutomaticCheck <p> AutomaticDownload|
|**Açıklama ekleme**|AutomaticDownload indirme işlemi yapar ve mümkünse sessizce yüklenir.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>"Güncelleştirmeleri Denetleme" düğmesinin etkin olup olmadığını değiştirme

Yerel kullanıcıların Microsoft AutoUpdate kullanıcı arabiriminde "Güncelleştirmeleri Denetleme" seçeneğine tık isteyip göremeyeceklerini değiştirme.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|EnableCheckForUpdatesButton|
|**Veri türü**|Boole|
|**Olası değerler**|True (varsayılan) <p> False|
|||

### <a name="disable-insider-checkbox"></a>Insider onay kutusunu devre dışı bırak

"Office Insider Programına Katıl..." yapmak için True olarak ayarlayın onay kutusu kullanılamaz / kullanıcılara gri gösterilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.autoupdate2`|
|**Anahtar**|DisableInsiderCheckbox|
|**Veri türü**|Boole|
|**Olası değerler**|False (varsayılan) <p> True|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>MAU'dan gönderilen telemetriyi sınırlandırma

Uygulama kullanımı yok veya ortam ayrıntıları yok, en az sinyal verisi göndermek için false olarak ayarlayın.

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

Aşağıdaki yapılandırma profili, aşağıdakiler için kullanılır:

- Cihazı Üretim kanalına
- Güncelleştirmeleri otomatik olarak indirme ve yükleme
- Kullanıcı arabiriminde "Güncelleştirmeleri denetleme" düğmesini etkinleştirme
- Cihaz kullanıcılarının Insider kanallarına kaydolmasına izin verme

> [!WARNING]
> Aşağıdaki yapılandırma örnek bir yapılandırmadır ve ayarları düzgün bir şekilde gözden geçirmeden ve yapılandırmaları uyarlamadan üretimde kullanılmamalı.

> [!TIP]
> Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, kurumuzdan bazı cihazları veya için yapılandırmanız `Beta` önerilir `Preview`.

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

MAU'yı yapılandırmak için, bu yapılandırma profilini kurumda şu yönetim aracından dağıtabilirsiniz:

- JAMF'den, bu yapılandırma profilini karşıya yükleyin ve Tercih Etki Alanını *com.microsoft.autoupdate2 olarak ayarlayın*.
- Bu Intune, bu yapılandırma profilini karşıya yükleyin ve özel yapılandırma profili adını *com.microsoft.autoupdate2 olarak ayarlayın*.

## <a name="resources"></a>Kaynaklar

- [msupdate başvurusu](/deployoffice/mac/update-office-for-mac-using-msupdate)
