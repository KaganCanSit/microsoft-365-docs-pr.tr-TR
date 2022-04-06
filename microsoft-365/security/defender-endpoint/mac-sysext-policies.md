---
title: macOS Catalina için yeni yapılandırma profilleri ve macOS'un daha yeni sürümleri
description: Bu konu başlığında, macOS Catalina'daki çekirdek uzantılarının ve macOS'un daha yeni sürümlerindeki çekirdek uzantılarının yerine gelen sistem uzantılarından yararlanmak için değiştirilmesi gereken değişiklikler açıklanmıştır.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, kernel, system, extensions, catalina
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ROBOTS: noindex,nofollow
ms.technology: mde
ms.openlocfilehash: 53194aac16091b9afd9559b4f372c2d436c198bf
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474717"
---
# <a name="new-configuration-profiles-for-macos-catalina-and-newer-versions-of-macos"></a>macOS Catalina için yeni yapılandırma profilleri ve macOS'un daha yeni sürümleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

macOS gelişimle hizalama olarak, macOS üzerinde çekirdek uzantıları yerine sistem uzantılarını Uç Nokta için Microsoft Defender bir güncelleştirme hazırlamaya hazırlanıyoruz. Bu güncelleştirme yalnızca macOS Catalina (10.15.4) ve daha yeni macOS sürümleri için geçerli olur.

MacOS üzerinde yönetilen bir Uç Nokta için Microsoft Defender (JAMF, Intune veya başka bir MDM çözümü aracılığıyla) dağıtım yaptıysanız, yeni yapılandırma profillerini dağıtmanız gerekir. Bu adımların başarısızılması, kullanıcıların bu yeni bileşenleri çalıştırmak için onay istemleri almalarına neden olur.

## <a name="jamf"></a>JAMF

### <a name="jamf-system-extensions-policy"></a>JAMF Sistem Uzantıları İlkesi

Sistem uzantılarını onaylamak için aşağıdaki yükü oluşturun:

1. Bilgisayarlarda **ve > Profiller'de Seçenekler'i** **> Uzantıları'ı seçin**.
2. Sistem **Uzantısı Türleri açılan listesinden** **İzin Verilen Sistem** Uzantıları'ı seçin.
3. Ekip **Kimliği için UBF8T346G9** kullanın.
4. İzin Verilen Sistem Uzantıları listesine aşağıdaki **paket tanımlayıcılarını** ekleyin:

    - **com.microsoft.wdav.epsext**
    - **com.microsoft.wdav.netext**

    :::image type="content" source="images/mac-approved-system-extensions.png" alt-text=" Onaylanan sistem uzantıları sayfası" lightbox="images/mac-approved-system-extensions.png":::

### <a name="privacy-preferences-policy-control"></a>Gizlilik Tercihleri İlke Denetimi

Yeni Uç Nokta Güvenlik Uzantısına Tam Disk Erişimi vermek için aşağıdaki JAMF Uç Nokta için Microsoft Defender ekleyin. Bu ilke, uzantıyı aygıtınızda çalıştırmanız için önk gerekli bir ilkedir.

1. Seçenekler **Gizlilik Tercihleri** \> **İlke Denetimi'ne tıklayın**.
2. Tanımlayıcı `com.microsoft.wdav.epsext` ve **Paket** türü `Bundle ID` **olarak kullanın**.
3. Kod Gereksinimini `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
4. Uygulama **veya hizmeti** **SystemPolicyAllFiles olarak ayarlayın ve** İzin Ver'e **erişin**.

   :::image type="content" source="images/mac-system-extension-privacy.png" alt-text=" Gizlilik Tercihleri İlke Denetimi menü öğesi" lightbox="images/mac-system-extension-privacy.png":::

### <a name="network-extension-policy"></a>Ağ Uzantısı İlkesi

MacOS'ta Uç Nokta Algılama ve Yanıt özellikleri Uç Nokta için Microsoft Defender, yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

> [!NOTE]
> JAMF'in, cihaza macOS üzerinde Uç Nokta için Microsoft Defender ağ uzantılarının etkinleştirilmesi için önkoşul olan içerik filtreleme ilkeleri için yerleşik destek değildir. Dahası, JAMF bazen dağıtılan ilkelerin içeriğini değiştirir.
> Bu nedenle, aşağıdaki adımlar yapılandırma profilinin imzalanmasını içeren geçici bir çözüm sağlar.

1. Metin düzenleyicisi kullanarak aşağıdaki içeriği cihazınıza `com.microsoft.network-extension.mobileconfig` kaydedin:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1">
        <dict>
            <key>PayloadUUID</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadType</key>
            <string>Configuration</string>
            <key>PayloadOrganization</key>
            <string>Microsoft Corporation</string>
            <key>PayloadIdentifier</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender Network Extension</string>
            <key>PayloadDescription</key>
            <string/>
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
                    <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                    <key>PayloadType</key>
                    <string>com.apple.webcontent-filter</string>
                    <key>PayloadOrganization</key>
                    <string>Microsoft Corporation</string>
                    <key>PayloadIdentifier</key>
                    <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                    <key>PayloadDisplayName</key>
                    <string>Approved Network Extension</string>
                    <key>PayloadDescription</key>
                    <string/>
                    <key>PayloadVersion</key>
                    <integer>1</integer>
                    <key>PayloadEnabled</key>
                    <true/>
                    <key>FilterType</key>
                    <string>Plugin</string>
                    <key>UserDefinedName</key>
                    <string>Microsoft Defender Network Extension</string>
                    <key>PluginBundleID</key>
                    <string>com.microsoft.wdav</string>
                    <key>FilterSockets</key>
                    <true/>
                    <key>FilterDataProviderBundleIdentifier</key>
                    <string>com.microsoft.wdav.netext</string>
                    <key>FilterDataProviderDesignatedRequirement</key>
                    <string>identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                </dict>
            </array>
        </dict>
    </plist>
    ```

2. Terminal'de yardımcı program çalıştırarak yukarıdaki dosyanın doğru kopyalanmış `plutil` olduğunu doğrulayın:

    ```bash
    $ plutil -lint <PathToFile>/com.microsoft.network-extension.mobileconfig
    ```

    Örneğin, dosya Belgeler'de depolanıyorsa:

    ```bash
    $ plutil -lint ~/Documents/com.microsoft.network-extension.mobileconfig
    ```

    Komut çıktısını doğrula `OK`.

    ```bash
    <PathToFile>/com.microsoft.network-extension.mobileconfig: OK
    ```

3. JAMF'in [yerleşik sertifika](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) yetkilisini kullanarak imzalama sertifikası oluşturmak için bu sayfada verilen yönergeleri izleyin.

4. Sertifika oluşturulduktan ve cihazınıza yüklendikten sonra, dosyayı imzalamak için Terminal'de aşağıdaki komutu çalıştırın:

    ```bash
    $ security cms -S -N "<CertificateName>" -i <PathToFile>/com.microsoft.network-extension.mobileconfig -o <PathToSignedFile>/com.microsoft.network-extension.signed.mobileconfig
    ```

    Örneğin, sertifika adı **SigningCertificate** ise ve imzalanmış dosya Belgeler'de depolanıyorsa:

    ```bash
    $ security cms -S -N "SigningCertificate" -i ~/Documents/com.microsoft.network-extension.mobileconfig -o ~/Documents/com.microsoft.network-extension.signed.mobileconfig
    ```

5. JAMF portalında Yapılandırma **Profilleri'ne gidin** ve Daha fazla **Upload** tıklayın. Dosya `com.microsoft.network-extension.signed.mobileconfig` istendiğinde seçin.

## <a name="intune"></a>Intune

### <a name="intune-system-extensions-policy"></a>Intune Uzantıları İlkesi

Sistem uzantılarını onaylamak için:

1. Cihaz Intune yapılandırmasını **yönet'i** \> **açın**. Profilleri **Yönet** \> **Profil** **Oluştur'a**\> tıklayın.
2. Profil için bir ad seçin. **Platform=macOS'u** **Profile type=Extensions olarak değiştirme**. **Oluştur**’u seçin.
3. Sekmede `Basics` , bu yeni profile bir ad girin.
4. `Configuration settings` Sekmede, bölüme aşağıdaki girdileri `Allowed system extensions` ekleyin:

   <br>

   ****

   |Paket tanımlayıcısı|Ekip tanımlayıcısı|
   |---|---|
   |com.microsoft.wdav.epsext|UBF8T346G9|
   |com.microsoft.wdav.netext|UBF8T346G9|
   |||

   :::image type="content" source="images/mac-system-extension-intune2.png" alt-text=" Sistem yapılandırma profilleri sayfası" lightbox="images/mac-system-extension-intune2.png":::

5. Sekmede `Assignments` bu profili Tüm Cihazlar için **Tüm Kullanıcılar'& attayabilirsiniz**.
6. Bu yapılandırma profilini gözden geçirin ve oluşturun.

### <a name="create-and-deploy-the-custom-configuration-profile"></a>Özel Yapılandırma Profili oluşturma ve dağıtma

Aşağıdaki yapılandırma profili ağ uzantısını sağlar ve Uç Nokta Güvenliği sistemi uzantısına Tam Disk Erişimi verir.

Aşağıdaki içeriğisysext.xmladlı **bir dosyaya kaydedin**:

```xml
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft Corporation</string>
        <key>PayloadIdentifier</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender System Extensions</string>
        <key>PayloadDescription</key>
        <string/>
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
                <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                <key>PayloadType</key>
                <string>com.apple.webcontent-filter</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                <key>PayloadDisplayName</key>
                <string>Approved Network Extension</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>FilterType</key>
                <string>Plugin</string>
                <key>UserDefinedName</key>
                <string>Microsoft Defender Network Extension</string>
                <key>PluginBundleID</key>
                <string>com.microsoft.wdav</string>
                <key>FilterSockets</key>
                <true/>
                <key>FilterDataProviderBundleIdentifier</key>
                <string>com.microsoft.wdav.netext</string>
                <key>FilterDataProviderDesignatedRequirement</key>
                <string>identifier &quot;com.microsoft.wdav.netext&quot; and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
            </dict>
            <dict>
                <key>PayloadUUID</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadType</key>
                <string>com.apple.TCC.configuration-profile-policy</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadDisplayName</key>
                <string>Privacy Preferences Policy Control</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>Services</key>
                <dict>
                    <key>SystemPolicyAllFiles</key>
                    <array>
                        <dict>
                            <key>Identifier</key>
                            <string>com.microsoft.wdav.epsext</string>
                            <key>CodeRequirement</key>
                            <string>identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                            <key>IdentifierType</key>
                            <string>bundleID</string>
                            <key>StaticCode</key>
                            <integer>0</integer>
                            <key>Allowed</key>
                            <integer>1</integer>
                        </dict>
                    </array>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Yukarıdaki dosyanın doğru kopyalanmış olduğunu doğrulayın. Terminal'de aşağıdaki komutu çalıştırın ve çıkışta olduğunu doğrulayın `OK`:

```bash
$ plutil -lint sysext.xml
sysext.xml: OK
```

Bu özel yapılandırma profilini dağıtmak için:

1. Cihaz Intune yapılandırmasını **yönet'i** \> **açın**. Profilleri **Yönet** \> **Profil** **Oluştur'a**\> tıklayın.
2. Profil için bir ad seçin. **Platform=macOS ve Profil** **türü=Özel'i seçin**. **Yapılandır'ı seçin**.
3. Yapılandırma profilini açın **vesysext.xml.** Bu dosya önceki adımda oluşturulmuş.
4. **Tamam**'ı seçin.

   :::image type="content" source="images/mac-system-extension-intune.png" alt-text="Sayfa içinde sistem Intune." lightbox="images/mac-system-extension-intune.png":::

5. Sekmede `Assignments` bu profili Tüm Cihazlar için **Tüm Kullanıcılar'& attayabilirsiniz**.
6. Bu yapılandırma profilini gözden geçirin ve oluşturun.
