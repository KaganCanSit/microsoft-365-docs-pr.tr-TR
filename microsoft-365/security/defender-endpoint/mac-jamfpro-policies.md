---
title: Jamf sitesinde macOS'ta Uç Nokta için Microsoft Defender ilkelerini Pro
description: Jamf 2013'te macOS'ta Uç Nokta için Microsoft Defender ilkelerini ayarlamayı Pro
keywords: policies, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 981e2afc2bfe3ff27bf5be492c98f96229a6deab
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011989"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Jamf sitesinde macOS'ta Uç Nokta için Microsoft Defender ilkelerini Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Mac'te Uç Nokta için Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu sayfa, Jamf veya Jamf'te macOS ilkelerini ayarlamak için Pro.

Aşağıdaki adımları benimsersiniz:

1. [Uç nokta ekleme paketi için Microsoft Defender'ı almak](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Jamf'te ekleme paketini Pro bir yapılandırma profili oluşturun](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Uç nokta ayarları için Microsoft Defender'ı yapılandırma](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Uç nokta bildirim ayarları için Microsoft Defender'ı yapılandırma](#step-4-configure-notifications-settings)
5. [Microsoft AutoUpdate'i (MAU) yapılandırma](#step-5-configure-microsoft-autoupdate-mau)
6. [Uç Nokta için Microsoft Defender'a tam disk erişimi ver](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Uç Nokta için Microsoft Defender için Kernel uzantısını onaylama](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Uç Nokta için Microsoft Defender için Sistem uzantılarını onaylama](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Ağ Uzantısını Yapılandırma](#step-9-configure-network-extension)
10. [macOS'ta Uç Nokta için Microsoft Defender ile taramaları zamanlama](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [macOS'ta Uç Nokta için Microsoft Defender'ı Dağıtma](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>1. Adım: Uç nokta ekleme paketi için Microsoft Defender'ı almak

1. Daha [Microsoft 365 Defender](https://security.microsoft.com), Kullanıcı **Ayarlar > Uç Noktaları'> gidin**.

2. İşletim sistemi olarak macOS'u ve dağıtım yöntemi olarak mobil Microsoft Intune Yönetim / Mobil Cihaz Yönetimi'Microsoft Intune seçin.

    ![Resim Microsoft Defender Güvenlik Merkezi.](images/onboarding-macos.png)

3. Ekleme **paketini indir (Yükleme)** seçeneğini WindowsDefenderATPOnboardingPackage.zip.

4. Ayıkla .`WindowsDefenderATPOnboardingPackage.zip`

5. Dosyayı tercih ettiğiniz konuma kopyalayın. Örneğin, `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>2. Adım: Jamf'te, Pro paketini kullanarak bir yapılandırma profili oluşturun

1. Önceki bölümden `WindowsDefenderATPOnboarding.plist` dosyayı bulun.

   ![WindowsDefenderATPOnboarding dosyasının resmi.](images/plist-onboarding-file.png)

2. Jamf Hizmet Pro oturum açma, **Bilgisayarları** >  **Yapılandırma Profilleri'ne gidin ve Yeni'yi** **seçin**.

    ![Panoda yeni bir Jamf Pro resmi.](images/jamf-pro-configure-profile.png)

3. Aşağıdaki ayrıntıları girin:

   **Genel**:

   - Ad: macOS için MDE ekleme
   - Açıklama: macOS EDR MDE ile ekleme
   - Kategori: Yok
   - Dağıtım Yöntemi: Otomatik Olarak Yükleme
   - Düzey: Bilgisayar Düzeyi

4.  Uygulama Gezintisi **Özel & sayfasına Ayarlar gidin ve** Upload **Add'yi** >  seçin.

    ![Uygulamayı yapılandırma ve özel ayarların görüntüsü.](images/jamfpro-mac-profile.png)

5. Dosya **Upload (PLIST dosyası) öğesini seçin ve** ardından Tercih Etki **Alanı alanına** şunları girin: `com.microsoft.wdav.atp`.

    ![Jamfpro plist yükleme dosyasının resmi.](images/jamfpro-plist-upload.png)

    ![Karşıya yükleme dosyası özelliği Liste dosyasının görüntüsü.](images/jamfpro-plist-file.png)

6. **Aç'ı** seçin ve ekleme dosyasını seçin.

    ![Ekleme dosyasının görüntüsü.](images/jamfpro-plist-file-onboard.png)

7. **Seç'Upload**.

    ![plist dosyasını karşıya yükleme resmi.](images/jamfpro-upload-plist.png)

8. Kapsam **sekmesini** seçin.

    ![Kapsam sekmesinin resmi.](images/jamfpro-scope-tab.png)

9. Hedef bilgisayarları seçin.

    ![Hedef bilgisayar resmi.](images/jamfpro-target-computer.png)

    ![Hedef resmi.](images/jamfpro-targets.png)

10. **Kaydet**'i seçin.

    ![Dağıtım hedef bilgisayarlarının görüntüsü.](images/jamfpro-deployment-target.png)

    ![Seçilen hedef bilgisayarların görüntüsü.](images/jamfpro-target-selected.png)

11. **Bitti'yi seçin**.

    ![Hedef grup bilgisayarlarının resmi.](images/jamfpro-target-group.png)

    ![Yapılandırma profillerinin listesi.](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>3. Adım: Uç nokta ayarları için Microsoft Defender'ı yapılandırma

Uç nokta yapılandırması için Microsoft Defender'ın tek tek ayarlarını düzenlemek için JAMF Pro GUI kullanabilir veya metin düzenleyicisinde bir yapılandırma Plisti oluşturarak ve bunu JAMF posta kutusuna yükerek eski yöntemi Pro.

Tercih Etki Alanı olarak tam olarak `com.microsoft.wdav` kullanmanız **gerektiğini unutmayın;** Uç Nokta `com.microsoft.wdav.ext` için Microsoft Defender yalnızca bu adı kullanır ve onun yönetilen ayarlarını yüklemek için!

(Bu `com.microsoft.wdav.ext` sürüm, GUI yöntemini kullanmayı tercih ediyorsanız, ancak henüz şemaya henüz eklenmemiş bir ayarı yapılandırmanız gerekirken nadir durumlarda da kullanılabilir.)

### <a name="gui-method"></a>GUI yöntemi

1. Schema.json dosyasını [Defender'ın GitHub deposundan indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) ve yerel bir dosyaya kaydedin:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Bilgisayarlar ve Yapılandırma Profilleri'nin > yeni bir Yapılandırma Profili oluşturun, Genel sekmesinde aşağıdaki **ayrıntıları** girin:

    ![Yeni profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Yok (varsayılan)
    - Düzey: Bilgisayar Düzeyi (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme (varsayılan)

3. Uygulama Şemaları Özel & **sekmesine** kadar Ayarlar Uygulamalar'ı **seçin, tercih** etki alanında kullanmak üzere Özel Şema'yı Kaynak  Olarak Ekle ve Kullan'ı tıklatın.

    ![Özel şema ekleme.](images/4137189bc3204bb09eed3aabc41afd78.png)

4. Tercih `com.microsoft.wdav` Etki Alanı olarak girin, Şema **Ekle'ye** **Upload** ve 1. Adım'da indirilen schema.json dosyasını seçin. **Kaydet**'e tıklayın.

    ![Upload şema.](images/a6f9f556037c42fabcfdcb1b697244cf.png)

5. Tercih Etki Alanı Özellikleri'nin altında, Uç nokta yapılandırma ayarları için desteklenen tüm Microsoft **Defender'ı görebilirsiniz**. **Yönetilsin istediğiniz ayarları** seçmek için Özellik Ekle/Kaldır'a tıklayın ve değişikliklerinizi kaydetmek için **Tamam'a** tıklayın. (Ayarlar seçimi kaldırılan kullanıcılar yönetilen yapılandırmaya dahil olmazlar; son kullanıcılar makinelerinde bu ayarları yapılandırabilecektir.)

    ![Yönetilen ayarlar'ı seçin.](images/817b3b760d11467abe9bdd519513f54f.png)

6. Ayarların değerlerini istenen değerlerle değiştirin. Belirli bir **ayara ilişkin belgeleri** almak için Daha fazla bilgi'ye tıkabilirsiniz. ( **Plist önizlemesi'ne tıklar** ve yapılandırma plistesini nasıl görüntüley geleceklerini incelersiniz. Görsel **düzenleyiciye dönmek** için Form düzenleyicisi'ne tıklayın.)

    ![Ayarlar değerlerini değiştirin.](images/a14a79efd5c041bb8974cb5b12b3a9b6.png)

7. Kapsam **sekmesini** seçin.

    ![Yapılandırma profili kapsamı.](images/9fc17529e5577eefd773c658ec576a7d.png)

8. **Contoso'nun Makine Grubu'nda öğesini seçin**.

9. **Ekle'yi** ve ardından Kaydet'i **seçin**.

    ![Yapılandırma ayarları - ekleyin.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Yapılandırma ayarları - kaydedin.](images/6f093e42856753a3955cab7ee14f12d9.png)

10. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

    ![Yapılandırma ayarları - bitti.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

Uç Nokta için Microsoft Defender zaman içinde yeni ayarlar ekler. Bu yeni ayarlar şemaya eklenir ve Github'da yeni bir sürüm yayımlanır.
Güncelleştirmeleri almak için tek gereken güncelleştirilmiş şema indirmek, var olan yapılandırma profilini düzenlemek ve **Application & Custom Ayarlar** sekmesinde şemayı düzenlemektir.

### <a name="legacy-method"></a>Eski yöntem

1. Uç nokta yapılandırma ayarları için aşağıdaki Microsoft Defender'ı kullanın:

    - enableGerçekTimeProtection
    - edilgenMode

    > [!NOTE]
    > MacOS için üçüncü taraf BIR AV'yi çalıştırmayı planlıyorsanız varsayılan olarak açık değildir.`true`

    - dışlamalar
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR örnek üzerindedir; kavram kanıtıyla gidiyorsanız, özellikle EICAR'ı test ediyorsanız kaldırın.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - etiketler
    - hideStatusMenuIcon

     Bilgi için bkz. [JAMF tam yapılandırma profili için özellik listesi](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. Dosyayı farklı kaydedin `MDATP_MDAV_configuration_settings.plist`.

3. Jamf Pro panosunda **Bilgisayarlar'ı** ve bu bilgisayar yapılandırma **profillerini açın**. **Yeni'ye** tıklayın ve Genel **sekmesine** geçiş yapın.

    ![Yeni profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Yok (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

    ![MDATP MDAV yapılandırma ayarlarının resmi.](images/3160906404bc5a2edf84d1d015894e3b.png)

5. Uygulama **Ayarları& Özel Ayarlar'ı** **seçin**.

    ![Uygulama ve özel ayarların görüntüsü.](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. Dosya **Upload (PLIST dosyası) öğesini seçin**.

    ![Yapılandırma ayarları plist dosyasının görüntüsü.](images/6f85269276b2278eca4bce84f935f87b.png)

7. **Tercihler Etki Alanı alanına** , ardından `com.microsoft.wdav`**PLIST Dosyası'Upload seçin**.

    ![Yapılandırma ayarları tercihler etki alanının resmi.](images/db15f147dd959e872a044184711d7d46.png)

8. Dosya **Seç'i seçin**.

    ![Yapılandırma ayarlarının görüntüsü dosyayı seçin.](images/526e978761fc571cca06907da7b01fd6.png)

9. **MDATP_MDAV_configuration_settings.plist'i seçin ve** ardından Aç'ı **seçin**.

    ![mdatpmdav yapılandırma ayarlarının resmi.](images/98acea3750113b8dbab334296e833003.png)

10. **Seç'Upload**.

    ![Karşıya yükleme yapılandırması ayarının görüntüsü.](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![Yapılandırma ayarlarının karşıya yükleme görüntüsü.](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    > [!NOTE]
    > Intune dosyasını karşıya yüklerken aşağıdaki hatayı alırsınız:
    >
    >![Intune dosyası yükleme yapılandırma ayarlarının görüntüsü.](images/8e69f867664668796a3b2904896f0436.png)

11. **Kaydet**'i seçin.

    ![Yapılandırma ayarlarının görüntüsü Resmi kaydet.](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. Dosya karşıya yüklendi.

    ![Karşıya yüklenen yapılandırma ayarları dosyasının görüntüsü.](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![Karşıya yüklenen yapılandırma ayarları dosyasının görüntüsü.](images/a422e57fe8d45689227e784443e51bd1.png)

13. Kapsam **sekmesini** seçin.

    ![Yapılandırma ayarları kapsamı görüntüsü.](images/9fc17529e5577eefd773c658ec576a7d.png)

14. **Contoso'nun Makine Grubu'nda öğesini seçin**.

15. **Ekle'yi** ve ardından Kaydet'i **seçin**.

    ![Yapılandırma ayarları addsav resmi.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Eklemeyi kaydeden yapılandırma ayarlarının görüntüsü.](images/6f093e42856753a3955cab7ee14f12d9.png)

16. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

    ![Yapılandırma ayarları yapılandırma profil resmi.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

## <a name="step-4-configure-notifications-settings"></a>4. Adım: Bildirim ayarlarını yapılandırma

Bu adımlar macOS 10.15 (Catalina) veya daha yeni sürümler için geçerlidir.

1. Jamf panosunda Pro, **Bilgisayarlar'ı ve ardından** Yapılandırma **Profilleri'ne tıklayın**.

2. **Yeni'ye** tıklayın ve Seçenekler için aşağıdaki ayrıntıları **girin**:

    - Sekme **Genel**:
        - **Ad**: MDATP MDAV Bildirim ayarları
        - **Açıklama**: macOS 10.15 (Catalina) veya daha yeni
        - **Kategori**: Yok *(varsayılan)*
        - **Dağıtım Yöntemi**: Otomatik Olarak Yükleme *(varsayılan)*
        - **Düzey**: Bilgisayar Düzeyi *(varsayılan)*

        ![Yeni macOS yapılandırma profil ekranı görüntüsü.](images/c9820a5ff84aaf21635c04a23a97ca93.png)

    - Sekme **Bildirimleri,** **Ekle'ye** tıklayın ve aşağıdaki değerleri girin:
        - **Paket Kimliği**: `com.microsoft.wdav.tray`
        - **Kritik Uyarılar: Devre Dışı** **Bırak'a tıklayın**
        - **Bildirimler:** **Etkinleştir'e tıklayın**
        - **Başlık uyarı türü**: **Dahil'i ve** **Geçici'i seçin** *(varsayılan)*
        - **Kilit ekranında bildirimler: Gizle'ye** **tıklayın**
        - **Bildirim Merkezi'nde Bildirimler**: Görüntü'ye **tıklayın**
        - **Rozet uygulama simgesi**: Görüntü'ye **tıklayın**

        ![Yapılandırma ayarları mdatpmdav bildirim tepsisi resmi.](images/7f9138053dbcbf928e5182ee7b295ebe.png)

    - Sekme **Bildirimleri' tıklayın**, **bir kez** daha ekle'ye tıklayın, Yeni Bildirimler **sekmesine kadar aşağı Ayarlar**
        - **Paket Kimliği**: `com.microsoft.autoupdate2`
        - Diğer ayarları yukarıdakiyle aynı değerlere göre yapılandırma

        ![Yapılandırma ayarları mdatpmdav notifications mau resmi.](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)

        Artık bildirim yapılandırmaları içeren iki "tablo" olduğunu unutmayın; biri Paket **Kimliği için: com.microsoft.wdav.tray** ve diğeri **de Paket Kimliği: com.microsoft.autoupdate2**. Uyarı ayarlarını gereksinimlerinize göre yapılandırabilirsiniz, ancak Paket Kimlikleri daha önce açıklananla tamamen aynı olmalı ve Bildirimler için **Include** anahtarı Açık **olarak ayarlanıyor olmalı**.

3. Kapsam sekmesini **ve** ardından Ekle'yi **seçin**.

    ![Yapılandırma ayarları kapsam ekleme resmi.](images/441aa2ecd36abadcdd8aed03556080b5.png)

4. **Contoso'nun Makine Grubu'nda öğesini seçin**.

5. **Ekle'yi** ve ardından Kaydet'i **seçin**.

    ![Contoso makine grp kaydetme yapılandırma ayarlarının görüntüsü.](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    ![Kaydetme ekleme yapılandırma ayarlarının görüntüsü.](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

6. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

    ![img yapılan yapılandırma ayarının görüntüsü.](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>5. Adım: Microsoft AutoUpdate'i (MAU) yapılandırma

1. Uç nokta yapılandırma ayarları için aşağıdaki Microsoft Defender'ı kullanın:

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
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

2. Olarak kaydedin `MDATP_MDAV_MAU_settings.plist`.

3. Jamf Pro panosunda Genel'i **seçin**.

    ![Genel ayar yapılandırma resminin görüntüsü.](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV MAU ayarları
    - Açıklama: macOS için MDATP için Microsoft AutoUpdate ayarları
    - Kategori: Yok (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

5. Uygulama **Ayarları& Özel Ayarlar'ı** **seçin**.

    ![Yapılandırma ayarı uygulamasının ve özel ayarların görüntüsü.](images/1f72e9c15eaafcabf1504397e99be311.png)

6. Dosya **Upload (PLIST dosyası) öğesini seçin**.

    ![Yapılandırma ayarı plist resmi.](images/1213872db5833aa8be535da57653219f.png)

7. Tercih **Etki Alanı alanına** şunları girin: `com.microsoft.autoupdate2`, ardından **PLIST Upload seçin**.

    ![Yapılandırma ayarı ön etki alanının resmi.](images/1213872db5833aa8be535da57653219f.png)

8. Dosya **Seç'i seçin**.

    ![Yapılandırma ayarının choosefile görüntüsü.](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. **MDATP_MDAV_MAU_settings.plist'i seçin**.

    ![Yapılandırma ayarı mdatpmdavmau ayarlarının görüntüsü.](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. **Seç'Upload**.
    ![Yapılandırma ayarlama ayarlarının resmi.](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![uplimg yapılandırma ayarının resmi.](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. **Kaydet**'i seçin.

    ![Yapılandırma ayarı saveimg görüntüsü.](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. Kapsam **sekmesini** seçin.

     ![Yapılandırma ayarı kapsam sekmesi görüntüsü.](images/10ab98358b2d602f3f67618735fa82fb.png)

13. **Ekle**'yi seçin.

    ![Yapılandırma ayarı addimg1 görüntüsü.](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![Yapılandırma ayarı addimg2 görüntüsü.](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![Yapılandırma ayarı addimg3 görüntüsü.](images/321ba245f14743c1d5d51c15e99deecc.png)

14. **Bitti'yi seçin**.

    ![Yapılandırma ayarı doneimage görüntüsü.](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>6. Adım: Uç Nokta için Microsoft Defender'a tam disk erişimi ver

1. Jamf Ayarları Pro Yapılandırma **Profilleri'ne tıklayın**.

    ![Yapılandırma ayarı yapılandırma profilinin görüntüsü.](images/264493cd01e62c7085659d6fdc26dc91.png)

2. **+ Yeni'yi seçin**.

3. Aşağıdaki ayrıntıları girin:

    **Genel**
    - Ad: MDATP MDAV - EDR VE AV'ye Tam Disk Erişimi ver
    - Açıklama: MacOS Catalina veya daha yeni üzerinde, yeni Gizlilik Tercihleri İlke Denetimi
    - Kategori: Yok
    - Dağıtım yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar düzeyi

    ![Genel yapılandırma ayarının resmi.](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. Gizlilik **Tercihleri İlkesi Denetimi Yapılandır'da Yapılandır'ı** **seçin**.

    ![Yapılandırma gizlilik ilkesi denetimi görüntüsü.](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. Gizlilik **Tercihleri İlke Denetimi'ne** aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    ![Yapılandırma ayarının gizlilik tercih ilkesi denetimi ayrıntılarının görüntüsü.](images/22cb439de958101c0a12f3038f905b27.png)

6. **+ Ekle'yi seçin**.

    ![Yapılandırma ayarı tüm dosyalara sistem ilkesi ekle ayarının görüntüsü.](images/bd93e78b74c2660a0541af4690dd9485.png)

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles olarak ayarlayın**

    - "Erişim" altında: İzin Ver olarak **ayarlayın**

7. **Kaydet'i** seçin (sağ alttaki kayıt değil).

    ![Görüntü yapılandırma ayarının resimleri kaydetmesi.](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. Yeni girdi `+` eklemek için **Uygulama Erişimi'nin** yanındaki işareti tıklatın.

    ![Yapılandırma ayarının uygulama erişiminin görüntüsü.](images/tcc-add-entry.png)

9. Aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav.epsext`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. **+ Ekle'yi seçin**.

    ![Yapılandırma ayarı tcc epsext giriş görüntüsü.](images/tcc-epsext-entry.png)

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles olarak ayarlayın**

    - "Erişim" altında: İzin Ver olarak **ayarlayın**

11. **Kaydet'i** seçin (sağ alttaki kayıt değil).

    ![Yapılandırma ayarı tcc epsext image2 görüntüsü.](images/tcc-epsext-entry2.png)

12. Kapsam **sekmesini** seçin.

    ![Yapılandırma ayarı kapsamının resmi.](images/2c49b16cd112729b3719724f581e6882.png)

13. **+ Ekle'yi seçin**.

    ![Yapılandırma ayarı ekleme görüntüsü.](images/57cef926d1b9260fb74a5f460cee887a.png)

14. Grup **Adı altında** > Grupları **Grubu'>** **Contoso'nun Makine Grubu'nda öğesini seçin**.

    ![Contoso makine yapılandırması ayarının görüntüsü.](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. **Ekle**'yi seçin.

16. **Kaydet**'i seçin.

17. **Bitti'yi seçin**.

    ![Yapılandırma ayarının donimg resmi.](images/809cef630281b64b8f07f20913b0039b.png)

    ![Yapılandırma ayarının donimg2 görüntüsü.](images/6c8b406ee224335a8c65d06953dc756e.png)

Alternatif olarak [full tümce.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) indirebilir ve Jamf Kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>7. Adım: Uç Nokta için Microsoft Defender için Çekirdek uzantısını onaylama

> [!CAUTION]
> Apple Silicon (M1) cihazları KEXT'i desteklemez. KEXT ilkelerinden oluşan bir yapılandırma profili yüklemesi bu cihazlarda başarısız olur.

1. Yapılandırma **Profilleri'nin altında** **+ Yeni'yi seçin**.

    ![Otomatik olarak oluşturulan bir sosyal medya gönderisi Açıklamanın ekran görüntüsü.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Kernel Extension
    - Açıklama: MDATP çekirdek uzantısı (kext)
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    ![Yapılandırma ayarları mdatpmdav kernel görüntüsü.](images/24e290f5fc309932cf41f3a280d22c14.png)

3. Onaylanmış **Çekirdek Uzantılarını Yapılandır'da Yapılandır'ı** **seçin**.

    ![Onaylanmış çekirdek uç yapılandırma ayarlarının görüntüsü.](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

4. Onaylanmış **Çekirdek Uzantıları alanına** aşağıdaki ayrıntıları girin:

    - Görünen Ad: Microsoft Corp.
    - Ekip Kimliği: UBF8T346G9

    ![Yapılandırma ayarları uygulamanın çekirdek uzantısının görüntüsü.](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. Kapsam **sekmesini** seçin.

    ![Yapılandırma ayarları kapsam sekmesi img resmi.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. **+ Ekle'yi seçin**.

7. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

8. **+ Ekle'yi seçin**.

    ![Yapılandırma ayarlarının görüntüsü resim ekler.](images/0dde8a4c41110dbc398c485433a81359.png)

9. **Kaydet**'i seçin.

    ![Saveimag yapılandırma ayarlarının görüntüsü.](images/0add8019b85a453b47fa5c402c72761b.png)

10. **Bitti'yi seçin**.

    ![Doneimag yapılandırma ayarlarının görüntüsü.](images/1c9bd3f68db20b80193dac18f33c22d0.png)

Alternatif olarak[, kext.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) indirebilir ve Jamf kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>8. Adım: Uç Nokta için Microsoft Defender için Sistem uzantılarını onaylama

1. Yapılandırma **Profilleri'nin altında** **+ Yeni'yi seçin**.

    ![Otomatik olarak oluşturulan bir sosyal medya gönderisi Açıklamanın ekran görüntüsü.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Sistem Uzantıları
    - Açıklama: MDATP sistem uzantıları
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    ![Configuration settings sysext new prof.](images/sysext-new-profile.png)

3. Sistem **Uzantıları'nın altında Yapılandır'ı** **seçin**.

   ![Sysext config yapılandırma ayarlarının görüntüsü.](images/sysext-configure.png)

4. Sistem **Uzantıları'nın** içine aşağıdaki ayrıntıları girin:

   - Görünen Ad: Microsoft Corp. System Extensions
   - Sistem Uzantısı Türleri: İzin Verilen Sistem Uzantıları
   - Ekip Tanımlayıcısı: UBF8T346G9
   - İzin Verilen Sistem Uzantıları:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![sysextconfig2 yapılandırma ayarlarının görüntüsü.](images/sysext-configure2.png)

5. Kapsam **sekmesini** seçin.

    ![Yapılandırma ayarları kapsam resmi.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. **+ Ekle'yi seçin**.

7. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

8. **+ Ekle'yi seçin**.

   ![Yapılandırma ayarları eklenti resmi.](images/0dde8a4c41110dbc398c485433a81359.png)

9. **Kaydet**'i seçin.

   ![Sysext kapsamı yapılandırma ayarlarının görüntüsü.](images/sysext-scope.png)

10. **Bitti'yi seçin**.

    ![Sysext-final yapılandırma ayarlarının görüntüsü.](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>9. Adım: Ağ Uzantısını Yapılandırma

Uç Nokta Algılama ve Yanıt özellikleri kapsamında, macOS'ta Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

Bu adımlar macOS 10.15 (Catalina) veya daha yeni sürümler için geçerlidir.

1. Jamf panosunda Pro, **Bilgisayarlar'ı ve ardından** Yapılandırma **Profilleri'ne tıklayın**.

2. **Yeni'ye** tıklayın ve Seçenekler için aşağıdaki ayrıntıları **girin**:

    - Sekme **Genel**:
        - **Ad**: Microsoft Defender Ağ Uzantısı
        - **Açıklama**: macOS 10.15 (Catalina) veya daha yeni
        - **Kategori**: Yok *(varsayılan)*
        - **Dağıtım Yöntemi**: Otomatik Olarak Yükleme *(varsayılan)*
        - **Düzey**: Bilgisayar Düzeyi *(varsayılan)*

    - Sekme **İçerik Filtresi**:
        - **Filtre Adı**: Microsoft Defender İçerik Filtresi
        - **Tanımlayıcı**: `com.microsoft.wdav`
        - Hizmet **Adresi**, Kuruluş **,** **Kullanıcı Adı**, **Parola**, **Sertifikayı boş** bırakın (**Dahil edin** *seçili* değildir)
        - **Filtre Sırası**: Denetçi
        - **Yuva Filtresi**: `com.microsoft.wdav.netext`
        - **Yuva Filtresi belirlenmiş gereksinim**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Ağ **Filtresi alanlarını** boş bırakın (**Include** *seçili* değildir)

        Tanımlayıcı, **Yuva Filtresi** **ve Yuva** **Filtresi'nin belirlenmiş Gereksinimin tam** değerleri yukarıda belirtildiği gibi olduğunu unutmayın.

        ![Yapılandırma ayarı mdatpmdav görüntüsü.](images/netext-create-profile.png)
        
 > [!NOTE]
 > Jamf, doğrudan arabirim üzerinden ayarlanan yerleşik içerik filtresi ayarlarını destekler.

3. Kapsam **sekmesini** seçin.

   ![Yapılandırma ayarları sco sekmesinin resmi.](images/0df36fc308ba569db204ee32db3fb40a.png)

4. **+ Ekle'yi seçin**.

5. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

6. **+ Ekle'yi seçin**.

    ![Yapılandırma ayarlarının soluk resmi.](images/0dde8a4c41110dbc398c485433a81359.png)

7. **Kaydet**'i seçin.

    ![Yapılandırma ayarlarının netextscop hakkında bilgi edinebilirsiniz.](images/netext-scope.png)

8. **Bitti'yi seçin**.

    ![Yapılandırma ayarları netextfinal görüntüsü.](images/netext-final.png)

Alternatif olarak[, Netfilter.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) indirebilir ve Jamf Kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>10. Adım: macOS'ta Uç Nokta için Microsoft Defender ile taramaları zamanlama

[macOS'ta Uç nokta için Microsoft Defender ile tarama zamanlama'da verilen yönergeleri izleyin](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>11. Adım: macOS'ta Uç Nokta için Microsoft Defender'ı Dağıtma

1. 'i kayıtlı olduğunuz yere gidin `wdav.pkg`.

    ![Dosya gezgini wdav pkg görüntüsü.](images/8dde76b5463047423f8637c86b05c29d.png)

2. olarak yeniden adlandır.`wdav_MDM_Contoso_200329.pkg`

    ![Dosya gezgini1 wdavmdmpkg resmi.](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. Jamf Pro açın.

    ![Yapılandırma ayarları jamfpro resmi.](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. Bilgisayarınızı seçin ve üst dişli simgesine tıklayın, ardından Bilgisayar **Yönetimi'ne tıklayın**.

    ![Yapılandırma ayarları compmgmt görüntüsü.](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. **Paketler'de** **+ Yeni'yi seçin**.
    ![Yeni bird Açıklama içeren bir resim otomatik olarak oluşturulan paket.](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. Yeni **Paket'e** aşağıdaki ayrıntıları girin:

    **Genel sekmesi**
    - Görünen Ad: Şimdilik boş bırakın. Çünkü, pkg'nizi seçtiğiniz zaman sıfırlanır.
    - Kategori: Yok (varsayılan)
    - Dosya adı: Dosya Seç

    ![Yapılandırma ayarları genel sekmesinin görüntüsü.](images/21de3658bf58b1b767a17358a3f06341.png)

    Dosyayı açın ve veya işaretlerini `wdav.pkg` seçin `wdav_MDM_Contoso_200329.pkg`.

    ![Otomatik olarak oluşturulan Açıklama bilgisayar ekranı açıklamasının ekran görüntüsü.](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. **Aç**'ı seçin. Görünen **Ad'ı** **Microsoft Defender Gelişmiş Tehdit Koruması ve Güvenlik Microsoft Defender Virüsten Koruma**.

    **Bildirim Dosyası** gerekli değildir. Uç Nokta için Microsoft Defender Bildirim Dosyası olmadan çalışır.

    **Seçenekler sekmesi**: Varsayılan değerleri tutma.

    **Sınırlamalar sekmesi**: Varsayılan değerleri tutma.

     ![Yapılandırma ayarları sınırlama sekmesinin resmi.](images/56dac54634d13b2d3948ab50e8d3ef21.png)

8. **Kaydet**'i seçin. Paket Jamf'e Pro.

   ![Upl jamf pro yapılandırma ayarlarının görüntüsü.](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   Paketin dağıtım için kullanılabilir olması birkaç dakika sürebilir.

   ![Yapılandırma ayarları paketi görüntüsü.](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. İlkeler **sayfasına** gidin.

    ![Yapılandırma ayarları açıklarının görüntüsü.](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. Yeni **bir ilke oluşturmak için +** Yeni'yi seçin.

    ![Yapılandırma ayarları yeni ilkenin resmi.](images/847b70e54ed04787e415f5180414b310.png)


11. Genel **alanına** aşağıdaki ayrıntıları girin:

    - Görünen ad: MDATP Onboarding Contoso 200329 v100.86.92 veya sonrası

    ![Yapılandırma ayarlarımdatponboard resmi.](images/625ba6d19e8597f05e4907298a454d28.png)

12. Yinelenen **Iade'yi seçin**.

    ![Otomatik olarak iade yapılandırmasını ayarlarının görüntüsü.](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

13. **Kaydet**'i seçin.

14. **Yapılandır'ı > seçin**.

    ![Yapılandırma ayarları paketinin yapılandırmasının resmi.](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. Microsoft Defender **Gelişmiş** Tehdit **Koruması'nın yanındaki Ekle düğmesini seçin ve ardından Microsoft Defender Virüsten Koruma**.

    ![MDATP ve MDA ekleme yapılandırma ayarlarının resmi.](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. **Kaydet**'i seçin.

    ![Yapılandırma settingssavimg görüntüsü.](images/9d6e5386e652e00715ff348af72671c6.png)

17. Kapsam **sekmesini** seçin.

    ![Yapılandırma ayarları scptab resmi.](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. Hedef bilgisayarları seçin.

    ![Yapılandırma ayarları tgtcomp görüntüsü.](images/6eda18a64a660fa149575454e54e7156.png)

    **Kapsam**

    **Ekle**'yi seçin.

    ![Ad1img yapılandırma ayarlarının resmi.](images/1c08d097829863778d562c10c5f92b67.png)

    ![Ad2img yapılandırma ayarlarının resmi.](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **Self Servis**

    ![Yapılandırma ayarlarının kendi kendine hizmet görüntüsü.](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. **Bitti'yi seçin**.

    ![Do1img yapılandırma ayarlarının resmi.](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![Do2img yapılandırma ayarlarının resmi.](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)
