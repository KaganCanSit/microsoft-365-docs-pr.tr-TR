---
title: macOS için cihaz denetimi
description: Mac'te USB Uç Nokta için Microsoft Defender çıkarılabilir depolamadan gelen tehditleri azaltmak için mac'te depolamayı yapılandırmayı öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, cihaz, kontrol, usb, çıkarılabilir, medya
ms.prod: m365-security
ms.mktglfcycl: security
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
ms.openlocfilehash: fbe693272a2f2893dff5f8614f3f9eff301069fd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477313"
---
# <a name="device-control-for-macos"></a>macOS için cihaz denetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="requirements"></a>Gereksinimler

macOS için cihaz denetimi aşağıdaki önkoşullara sahip:

> [!div class="checklist"]
>
> - Uç Nokta için Microsoft Defender hakkı (deneme sürümü olabilir)
> - Minimum işletim sistemi sürümü: macOS 11 veya daha yüksek
> - Minimum ürün sürümü: 101.34.20

## <a name="device-control-policy"></a>Cihaz denetimi ilkesi

macOS için cihaz denetimi yapılandırmak için, kurum içinde yerine koymak istediğiniz kısıtlamaları açıklayan bir ilke oluşturmanız gerekir.

Cihaz denetimi ilkesi, diğer tüm ürün ayarlarını yapılandırmak için kullanılan yapılandırma profilinde yer almaktadır. Daha fazla bilgi için bkz [. Yapılandırma profili yapısı](mac-preferences.md#configuration-profile-structure).

Cihaz denetimi ilkesi yapılandırma profili içinde aşağıdaki bölümde tanımlanır:

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|deviceControl|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

Cihaz denetimi ilkesi aşağıdakiler için kullanılabilir:

- [Cihaz denetimi tarafından yükseltilmiş bildirimler için URL hedefini özelleştirme](#customize-url-target-for-notifications-raised-by-device-control)
- [Çıkarılabilir cihazlara izin verme veya engelleme](#allow-or-block-removable-devices)

### <a name="customize-url-target-for-notifications-raised-by-device-control"></a>Cihaz denetimi tarafından yükseltilmiş bildirimler için URL hedefini özelleştirme

Yerine konan cihaz denetim ilkesi bir cihazda zorunlu tutulsa (örneğin, çıkarılabilir bir medya cihazına erişim kısıtlanmışsa), kullanıcıya bir bildirim görüntülenir.

:::image type="content" source="images/mac-device-control-notification.png" alt-text="Cihaz denetim bildirimi" lightbox="images/mac-device-control-notification.png":::

Son kullanıcılar bu bildirime tıklaytılarında, varsayılan tarayıcıda bir web sayfası açılır. Son kullanıcılar bildirimi tıklayana kadar açılan URL'yi yapılandırabilirsiniz.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|navigationTarget|
|**Veri türü**|Dize|
|**Açıklamalar**|Tanımlanmamışsa, ürün, ürünün 4.|
|

### <a name="allow-or-block-removable-devices"></a>Çıkarılabilir cihazlara izin verme veya engelleme

Cihaz denetimi ilkesine bağlı çıkarılabilir medya bölümü çıkarılabilir medyaya erişimi kısıtlamak için kullanılır.

> [!NOTE]
> Şu anda çıkarılabilir medya türleri desteklemektedir ve şu ilkeye dahil olabilir: USB depolama cihazları.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|removableMediaPolicy|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

İlkenin bu bölümü hiyerarşik bir bölümdir ve en yüksek esnekliği sağlar ve çok çeşitli kullanım durumlarını kapsayan bir bölümtür. En üst düzeyde, satıcı kimliğiyle tanımlanan satıcılar vardır. Her satıcı için, ürün kimliğiyle tanımlanan ürünler vardır. Son olarak, her ürün için belirli cihazlara açıklama ekli seri numaraları vardır.

```text
|-- policy top level
    |-- vendor 1
        |-- product 1
            |-- serial number 1
            ...
            |-- serial number N
        ...
        |-- product N
    ...
    |-- vendor N
```

Cihaz tanımlayıcılarını bulma hakkında bilgi için bkz [. Cihaz tanımlayıcılarını bulma](#look-up-device-identifiers).

İlke, en özel girdiden en genele doğru değerlendirilir. Başka bir ifadeyle, cihaz takılı olduğunda ürün her çıkarılabilir medya cihazı için ilkede en özel eşleşmeyi bulmaya çalışır ve izinleri bu düzeyde uygulayabilir. Eşleşme yoksa, bir sonraki en iyi eşleşme uygulanır ve en üst düzeyde belirtilen izinlere kadar uygulanır; bu, cihaz ilkenin başka hiçbir girdiyle eşleşmezse varsayılan ayardır.

#### <a name="policy-enforcement-level"></a>İlke zorlama düzeyi

Çıkarılabilir medya bölümünün altında, aşağıdaki değerlerden birini almaya devam eden zorlama düzeyini ayarlama seçeneği vardır:

- `audit` - Bu zorlama düzeyi altında, bir cihaza erişim kısıtlanmışsa kullanıcıya bir bildirim görüntülenir, ancak cihaz hala kullanılabilir. Bu zorlama düzeyi, bir ilkenin ne kadar etkili olduğunu değerlendirmek için yararlı olabilir.
- `block` - Bu zorlama düzeyi altında, kullanıcının cihazda gerçekleştirebilirsiniz işlemleri ilkede tanımlanan işlemlerle sınırlıdır. Ayrıca, kullanıcıya bir bildirim de yükseltilmiştir.

> [!NOTE]
> Varsayılan olarak, zorlama düzeyi olarak ayarlanır `audit`.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|enforcementLevel|
|**Veri türü**|Dize|
|**Olası değerler**|denetim (varsayılan) <p> engelle|
|

#### <a name="default-permission-level"></a>Varsayılan izin düzeyi

Çıkarılabilir medya bölümünün en üst düzeyinde, ilkede yer alan başka hiçbir şey ile eşleşmeen cihazlar için varsayılan izin düzeyini yapılandırabilirsiniz.

Bu ayar şöyle de ayarlanabilirsiniz:

- `none` - Cihazda hiçbir işlem gerçekleştirilene kadar
- Aşağıdaki değerlerin birleşimi:
  - `read` - Cihazda okuma işlemlerine izin verilir
  - `write` - Cihazda yazma işlemlerine izin verilir
  - `execute` - Cihazda yürütme işlemlerine izin verilir

> [!NOTE]
> İzin `none` düzeyinde varsa, diğer tüm izinler (`read`, veya `write``execute`) yoksayılır.
>
> İzin `execute` yalnızca Mach-O ikililerinin yürütülmesine başvurur. Betiklerin veya diğer yük türlerinin yürütülmesi dahil değildir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|izin|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|yok <p> okuma <p> yazma <p> yürütme|
|

#### <a name="restrict-removable-media-by-vendor-product-and-serial-number"></a>Çıkarılabilir medyayı satıcı, ürün ve seri numarasına göre kısıtlama

USB cihazları gibi [çıkarılabilir cihazlara izin](#allow-or-block-removable-devices) verme veya engelleme konusunda açıklandığı gibi, satıcı kimliği, ürün kimliği ve seri numarasıyla çıkarılabilir medya tanımlanır.

Çıkarılabilir medya ilkesi en üst düzeyinde, isteğe bağlı olarak satıcı düzeyinde daha ayrıntılı kısıtlamalar tanımlayabilirsiniz.

Sözlük `vendors` bir veya daha fazla girdi içerir ve her girdi satıcı kimliği tarafından tanımlanır.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|satıcılar|
|**Veri türü**|Sözlük (iç içe tercih)|
|

Her satıcı için, o satıcıdan cihazlar için istediğiniz izin düzeyini belirtebilirsiniz.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|izin|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|Varsayılan izin [düzeyinin aynısı](#default-permission-level)|
|

Ayrıca, isteğe bağlı olarak daha ayrıntılı izinlerin tanımlandığı satıcıya ait ürün kümelerini de belirtebilirsiniz. Sözlük `products` bir veya daha fazla girdi içerir ve her girdi ürün kimliği tarafından tanımlanır.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|ürünler|
|**Veri türü**|Sözlük (iç içe tercih)|
|

Her ürün için, bu ürün için istediğiniz izin düzeyini belirtebilirsiniz.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|izin|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|Varsayılan izin [düzeyinin aynısı](#default-permission-level)|
|

Ayrıca, daha ayrıntılı izinlerin tanımlandığı isteğe bağlı bir seri numarası kümesi de belirtebilirsiniz.

Sözlük `serialNumbers` bir veya daha fazla girdi içerir ve her girdi seri numarasıyla tanımlanır.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|seriSayılar|
|**Veri türü**|Sözlük (iç içe tercih)|
|

Her seri numarası için istediğiniz izin düzeyini belirtebilirsiniz.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|izin|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|Varsayılan izin [düzeyinin aynısı](#default-permission-level)|
|

#### <a name="example-device-control-policy"></a>Örnek cihaz denetim ilkesi

Aşağıdaki örnekte, yukarıdaki kavramlardan tüm kavramların bir cihaz denetim ilkesiyle nasıl bir araya alına bir araya gel! Aşağıdaki örnekte, çıkarılabilir medya ilkesi hiyerarşik yapısına dikkat etmiş olursunuz.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>navigationTarget</key>
        <string>[custom URL for notifications]</string>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>[enforcement level]</string> <!-- audit / block -->
            <key>permission</key>
            <array>
                <string>[permission]</string> <!-- none / read / write / execute -->
                <!-- other permissions -->
            </array>
            <key>vendors</key>
            <dict>
                <key>[vendor id]</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>[permission]</string> <!-- none / read / write / execute -->
                        <!-- other permissions -->
                    </array>
                    <key>products</key>
                    <dict>
                        <key>[product id]</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>[permission]</string> <!-- none / read / write / execute -->
                                <!-- other permissions -->
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>[serial-number]</key>
                                <array>
                                    <string>[permission]</string> <!-- none / read / write / execute -->
                                    <!-- other permissions -->
                                </array>
                                <!-- other serial numbers -->
                            </dict>
                        </dict>
                        <!-- other products -->
                    </dict>
                </dict>
                <!-- other vendors -->
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

Aşağıdaki belgelere cihaz denetimi ilkeleriyle ilgili daha fazla örneklemiz var:

- [Veri için cihaz denetimi ilkelerine Intune](mac-device-control-intune.md)
- [JAMF için cihaz denetimi ilkeleri örnekleri](mac-device-control-jamf.md)

#### <a name="look-up-device-identifiers"></a>Cihaz tanımlayıcılarını bakma

USB cihazının satıcı kimliğini, ürün kimliğini ve seri numarasını bulmak için:

1. Mac cihazında oturum açın.
1. Tanımlayıcıları görmek istediğiniz USB cihazını takın.
1. macOS'un en üst düzey menüsünde Bu **Mac Hakkında'ya tıklayın**.

   :::image type="content" source="images/mac-device-control-lookup-1.png" alt-text="Bu Mac hakkında sayfası" lightbox="images/mac-device-control-lookup-1.png":::

1. Sistem **Raporu'mu seçin**.

   :::image type="content" source="images/mac-device-control-lookup-2.png" alt-text="Sistem raporu" lightbox="images/mac-device-control-lookup-2.png":::

1. Sol sütundan **USB'yi seçin**.

   :::image type="content" source="images/mac-device-control-lookup-3.png" alt-text="Tüm USB cihazlarının görünümü" lightbox="images/mac-device-control-lookup-3.png":::
    

1. **USB Cihaz Ağacı** altında, takmış olduğunuz USB cihazına gidin.

   :::image type="content" source="images/mac-device-control-lookup-4.png" alt-text="BIR USB cihazının ayrıntıları" lightbox="images/mac-device-control-lookup-4.png":::

1. Satıcı kimliği, ürün kimliği ve seri numarası görüntülenir. Çıkarılabilir medya ilkesine satıcı kimliği ve ürün kimliğini eklerken, bölümü yalnızca sonra eklemeniz gerekir `0x`. Örneğin, aşağıdaki resimde satıcı kimliği ve ürün `1000` kimliği yer almaktadır `090c`.

#### <a name="discover-usb-devices-in-your-organization"></a>Kuruluş içinde USB cihazlarını keşfedin

Usb cihazlardan gelen bağlama, bağlama ve bağlamadan çıkış ve toplu değişiklik etkinliklerini gelişmiş Uç Nokta için Microsoft Defender görüntüebilirsiniz. Bu olaylar, şüpheli kullanım etkinliğini tanımlamak veya iç soruşturmalar gerçekleştirmek için yararlı olabilir.

```bash
DeviceEvents
    | where ActionType == "UsbDriveMounted" or ActionType == "UsbDriveUnmounted" or ActionType == "UsbDriveDriveLetterChanged"
    | where DeviceId == "<device ID>"
```

## <a name="device-control-policy-deployment"></a>Cihaz denetimi ilkesi dağıtımı

Cihaz denetimi ilkesi, MacOS'ta cihaz ayarları için tercihleri ayarlama konusunda açıklandığı [Uç Nokta için Microsoft Defender ekli olmalı](mac-preferences.md).

Bu profil, Yapılandırma profili dağıtımı'nda listelenen yönergeler [kullanılarak dağıtılabilir](mac-preferences.md#configuration-profile-deployment).

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

Intune YA DA JAMF aracılığıyla yapılandırma profilini ittirdikten sonra, Terminal'de aşağıdaki komutu çalıştırarak ürün tarafından başarıyla alınip alınamadı kontrol edin:

```bash
mdatp device-control removable-media policy list
```

Bu komut, ürünün kullanmakta olduğu cihaz denetim ilkesi için standart çıktıya yazdırılır. Bu durumda, `Policy is empty`(a) yapılandırma profilinin bu belgede açıklandığı gibi gerçekten cihaza yönetim konsolundan cihaza itilmiş olduğundan ve (b) geçerli bir cihaz denetim ilkesi olduğundan emin olun.

İlke başarıyla teslim edilen ve bir veya daha fazla cihaz takılı olan bir cihazda, tüm cihazları ve onlara uygulanan geçerli izinleri listeleyen aşağıdaki komutu çalıştırabilirsiniz.

```bash
mdatp device-control removable-media devices list
```

Çıkış örneği:

```Output
.Device(s)
|-o Name: Untitled 1, Permission ["read", "execute"]
| |-o Vendor: General "fff0"
| |-o Product: USB Flash Disk "1000"
| |-o Serial number: "04ZSSMHI2O7WBVOA"
| |-o Mount point: "/Volumes/TESTUSB"
```

Yukarıdaki örnekte, takılı yalnızca bir `read` `execute` çıkarılabilir medya cihazı vardır ve cihaza teslim edilen cihaz denetim ilkesine göre bu cihaza ve izinlere sahip olur.

## <a name="related-topics"></a>İlgili konular

- [Veri için cihaz denetimi ilkelerine Intune](mac-device-control-intune.md)
- [JAMF için cihaz denetimi ilkeleri örnekleri](mac-device-control-jamf.md)
