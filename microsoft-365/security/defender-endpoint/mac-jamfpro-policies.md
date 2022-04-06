---
title: Jamf Uç Nokta için Microsoft Defender'da macOS ilkeleri için varsayılan Pro
description: Jamf 2013'te macOS Uç Nokta için Microsoft Defender ilkelerini ayarlamayı Pro
keywords: policies, microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6e3a31343468b79ff1117a60eca6a87825562778
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466795"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Jamf Uç Nokta için Microsoft Defender'da macOS ilkeleri için varsayılan Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Mac'te Uç Nokta için Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu sayfa, Jamf veya Jamf'te macOS ilkelerini ayarlamak için Pro.

Aşağıdaki adımları benimsersiniz:

1. [Uç Nokta için Microsoft Defender ekleme paketini almak](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Jamf'te ekleme paketini Pro bir yapılandırma profili oluşturun](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Kullanıcı Uç Nokta için Microsoft Defender yapılandırma](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Bildirim Uç Nokta için Microsoft Defender yapılandırma](#step-4-configure-notifications-settings)
5. [Microsoft AutoUpdate'i (MAU) yapılandırma](#step-5-configure-microsoft-autoupdate-mau)
6. [Posta dosyalarına tam disk Uç Nokta için Microsoft Defender](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Sistem için Kernel uzantısını Uç Nokta için Microsoft Defender](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Daha fazla bilgi için Sistem uzantılarını Uç Nokta için Microsoft Defender](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Ağ Uzantısını Yapılandırma](#step-9-configure-network-extension)
10. [macOS'ta Uç Nokta için Microsoft Defender taramaları zamanlama](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [MacOS Uç Nokta için Microsoft Defender da uygulama dağıtma](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>1. Adım: Uç Nokta için Microsoft Defender paketini almak

1. Daha [Microsoft 365 Defender](https://security.microsoft.com), Kullanıcı **Ayarlar > Uç Noktaları'> gidin**.

2. İşletim sistemi olarak macOS'u ve dağıtım Cihaz Yönetimi mobil Microsoft Intune olarak mobil cihaz'ı seçin.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Sayfanın Ayarlar Sayfası Microsoft Defender Güvenlik Merkezi" lightbox="images/onboarding-macos.png":::

3. Ekleme **paketini indir (Yükleme)** seçeneğini WindowsDefenderATPOnboardingPackage.zip.

4. Ayıkla .`WindowsDefenderATPOnboardingPackage.zip`

5. Dosyayı tercih ettiğiniz konuma kopyalayın. Örneğin, `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>2. Adım: Jamf'te, Pro paketini kullanarak bir yapılandırma profili oluşturun

1. Önceki bölümden `WindowsDefenderATPOnboarding.plist` dosyayı bulun.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="En Windows Defender ATP Ekleme dosyası" lightbox="images/plist-onboarding-file.png":::

2. Jamf Hizmet Pro oturum açma, **Bilgisayarları** >  **Yapılandırma Profilleri'ne gidin ve Yeni'yi** **seçin**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Üzerinde yeni bir Jamf ve Jamf panosu Pro sayfası" lightbox="images/jamf-pro-configure-profile.png":::

3. Aşağıdaki ayrıntıları girin:

   **Genel**:

   - Ad: macOS için MDE ekleme
   - Açıklama: macOS EDR MDE ile ekleme
   - Kategori: Yok
   - Dağıtım Yöntemi: Otomatik Olarak Yükleme
   - Düzey: Bilgisayar Düzeyi

4.  Uygulama Gezintisi **Özel & sayfasına Ayarlar gidin ve** Upload **Add'yi** >  seçin.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Yapılandıran uygulama ve özel ayarlar" lightbox="images/jamfpro-mac-profile.png":::

5. Dosya **Upload (PLIST dosyası) öğesini seçin ve** ardından Tercih Etki **Alanı alanına** şunları girin: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="Jamfpro plist karşıya yükleme dosyası" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Karşıya yükleme dosyası özelliği Liste dosyası" lightbox="images/jamfpro-plist-file.png":::

6. **Aç'ı** seçin ve ekleme dosyasını seçin.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Ekleme dosyası" lightbox="images/jamfpro-plist-file-onboard.png":::

7. **Seç'Upload**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Karşıya yüklenen plist dosyası" lightbox="images/jamfpro-upload-plist.png":::

8. Kapsam **sekmesini** seçin.

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Kapsam sekmesi" lightbox="images/jamfpro-scope-tab.png":::

9. Hedef bilgisayarları seçin.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Hedef bilgisayarlar" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Hedefler" lightbox="images/jamfpro-targets.png":::

10. **Kaydet**'i seçin.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Hedef bilgisayarların dağıtımı" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Hedef bilgisayarların seçimi" lightbox="images/jamfpro-target-selected.png":::

11. **Bitti'yi seçin**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Hedef grubun bilgisayarları" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Yapılandırma profilleri listesi" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>3. Adım: Uç Nokta için Microsoft Defender yapılandırma

UÇ NOKTA IÇIN MICROSOFT DEFENDER yapılandırmasının tek tek ayarlarını düzenlemek için JAMF Pro GUI kullanabilir veya metin düzenleyicisinde bir yapılandırma Plisti oluşturarak ve bunu JAMF listesine yükerek eski yöntemi Pro.

Tercih Etki Alanı olarak tam olarak `com.microsoft.wdav` **kullanmanız gerektiğini** unutmayın; Uç Nokta için Microsoft Defender adı kullanır `com.microsoft.wdav.ext` ve onun yönetilen ayarlarını yüklemek için!

(Bu `com.microsoft.wdav.ext` sürüm, GUI yöntemini kullanmayı tercih ediyorsanız, ancak henüz şemaya henüz eklenmemiş bir ayarı yapılandırmanız gerekirken nadir durumlarda da kullanılabilir.)

### <a name="gui-method"></a>GUI yöntemi

1. Schema.json dosyasını [Defender'ın GitHub deposundan indirin](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) ve yerel bir dosyaya kaydedin:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Bilgisayarlar ve Yapılandırma Profilleri'nin > yeni bir Yapılandırma Profili oluşturun, Genel sekmesinde aşağıdaki **ayrıntıları** girin:

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Yeni profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Yok (varsayılan)
    - Düzey: Bilgisayar Düzeyi (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme (varsayılan)

3. Uygulama Şemaları Özel & **sekmesine** kadar Ayarlar Uygulamalar'ı **seçin, tercih** etki alanında kullanmak üzere Özel Şema'yı Kaynak  Olarak Ekle ve Kullan'ı tıklatın.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Özel şema ekleme" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Tercih `com.microsoft.wdav` Etki Alanı olarak girin, Şema **Ekle'ye** **Upload** ve 1. Adım'da indirilen schema.json dosyasını seçin. **Kaydet**'e tıklayın.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="Upload şeması" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Aşağıdaki Tercih Etki Alanı Özellikleri'nin Uç Nokta için Microsoft Defender desteklenen tüm yapılandırma **ayarlarını görebilirsiniz**. **Yönetilsin istediğiniz ayarları** seçmek için Özellik Ekle/Kaldır'a tıklayın ve değişikliklerinizi kaydetmek için **Tamam'a** tıklayın. (Ayarlar seçimi kaldırılan kullanıcılar yönetilen yapılandırmaya dahil olmazlar; son kullanıcılar makinelerinde bu ayarları yapılandırabilecektir.)

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Seçilen yönetilen ayarlar" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Ayarların değerlerini istenen değerlerle değiştirin. Belirli bir **ayara ilişkin belgeleri** almak için Daha fazla bilgi'ye tıkabilirsiniz. ( **Plist önizlemesi'ne tıklar** ve yapılandırma plistesini nasıl görüntüley geleceklerini incelersiniz. Görsel **düzenleyiciye dönmek** için Form düzenleyicisi'ne tıklayın.)

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Ayar değerlerini değiştiren sayfa" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Kapsam **sekmesini** seçin.

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Yapılandırma profil kapsamı" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. **Contoso'nun Makine Grubu'nda öğesini seçin**.

9. **Ekle'yi** ve ardından Kaydet'i **seçin**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Yapılandırma ayarlarını ekleyebilirsiniz" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Yapılandırma ayarlarını kaydedebilirsiniz" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Yapılandırma ayarlarını tamamlayın sayfa" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Uç Nokta için Microsoft Defender zamanla yeni ayarlar ekler. Bu yeni ayarlar şemaya eklenir ve Github'da yeni bir sürüm yayımlanır.
Güncelleştirmeleri almak için tek gereken güncelleştirilmiş şema indirmek, var olan yapılandırma profilini düzenlemek ve **Application & Custom Ayarlar** sekmesinde şemayı düzenlemektir.

### <a name="legacy-method"></a>Eski yöntem

1. Aşağıdaki adımları Uç Nokta için Microsoft Defender kullanın:

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

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Yeni profilin görüntüleniyor sayfa" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Yok (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="MDATP MDAV yapılandırma ayarları" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. Uygulama **Ayarları& Özel Ayarlar'ı** **seçin**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Uygulama ve özel ayarlar" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. Dosya **Upload (PLIST dosyası) öğesini seçin**.

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Yapılandırma ayarları plist dosyası" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. **Tercihler Etki Alanı alanına** , ardından `com.microsoft.wdav`**PLIST Dosyası'Upload seçin**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Yapılandırma ayarları tercihleri etki alanı" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. Dosya **Seç'i seçin**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Plist dosyasını seçme istemi" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. **MDATP_MDAV_configuration_settings.plist'i seçin ve** ardından Aç'ı **seçin**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Mdatpmdav yapılandırma ayarları" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. **Seç'Upload**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Yapılandırma ayarı karşıya yükleme" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Yapılandırma ayarlarıyla ilgili resmi karşıya yükleme istemi" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Intune dosyasını karşıya yüklerken aşağıdaki hatayı alırsınız:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Intune dosyasını yapılandırma ayarlarıyla ilgili yükleme istemi" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. **Kaydet**'i seçin.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Yapılandırma ayarlarıyla ilgili resmi kaydetme seçeneği" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Dosya karşıya yüklendi.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Yapılandırma ayarlarıyla ilgili karşıya yüklenen dosya" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Yapılandırma ayarları sayfası" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Kapsam **sekmesini** seçin.

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Yapılandırma ayarlarının kapsamı" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. **Contoso'nun Makine Grubu'nda öğesini seçin**.

15. **Ekle'yi** ve ardından Kaydet'i **seçin**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Yapılandırma ayarları ekler" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Yapılandırma ayarlarının bildirimi" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

    ![Yapılandırma ayarları yapılandırma profil resmi.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Yapılandırma profilinin ayarları" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

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

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Yeni macOS yapılandırma profil sayfası" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - Sekme **Bildirimleri,** **Ekle'ye** tıklayın ve aşağıdaki değerleri girin:
        - **Paket Kimliği**: `com.microsoft.wdav.tray`
        - **Kritik Uyarılar: Devre Dışı** **Bırak'a tıklayın**
        - **Bildirimler:** **Etkinleştir'e tıklayın**
        - **Başlık uyarı türü**: **Dahil'i ve** **Geçici'i seçin** *(varsayılan)*
        - **Kilit ekranında bildirimler: Gizle'ye** **tıklayın**
        - **Bildirim Merkezi'nde Bildirimler**: Görüntü'ye **tıklayın**
        - **Rozet uygulama simgesi**: Görüntü'ye **tıklayın**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="Yapılandırma ayarları mdatpmdav bildirimler tepsisi" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - Sekme **Bildirimleri' tıklayın**, **bir kez** daha ekle'ye tıklayın, Yeni Bildirimler **sekmesine kadar aşağı Ayarlar**
        - **Paket Kimliği**: `com.microsoft.autoupdate2`
        - Diğer ayarları yukarıdakiyle aynı değerlere göre yapılandırma

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Yapılandırma ayarları mdatpmdav notifications mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Artık bildirim yapılandırmaları içeren iki "tablo" olduğunu unutmayın; biri Paket **Kimliği için: com.microsoft.wdav.tray** ve diğeri **de Paket Kimliği: com.microsoft.autoupdate2**. Uyarı ayarlarını gereksinimlerinize göre yapılandırabilirsiniz, ancak Paket Kimlikleri daha önce açıklananla tamamen aynı olmalı ve Bildirimler için **Include** anahtarı Açık **olarak ayarlanıyor olmalı**.

3. Kapsam sekmesini **ve** ardından Ekle'yi **seçin**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Yapılandırma ayarları için değerleri ekleyebilirsiniz sayfası" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. **Contoso'nun Makine Grubu'nda öğesini seçin**.

5. **Ekle'yi** ve ardından Kaydet'i **seçin**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Contoso makine grubunun yapılandırma ayarları için değerleri kaydedebilirsiniz sayfası" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Yapılandırma ayarlarının tamamlanma bildirimini görüntüleyen sayfa" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. **Bitti'yi seçin**. Yeni Yapılandırma profilini **görüyoruz**.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Tamamlanan yapılandırma ayarları" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>5. Adım: Microsoft AutoUpdate'i (MAU) yapılandırma

1. Aşağıdaki adımları Uç Nokta için Microsoft Defender kullanın:

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

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Yapılandırma ayarları" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV MAU ayarları
    - Açıklama: macOS için MDATP için Microsoft AutoUpdate ayarları
    - Kategori: Yok (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

5. Uygulama **Ayarları& Özel Ayarlar'ı** **seçin**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Yapılandırma ayarı uygulaması ve özel ayarlar" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. Dosya **Upload (PLIST dosyası) öğesini seçin**.

7. Tercih **Etki Alanı alanına** şunları girin: `com.microsoft.autoupdate2`, ardından **PLIST Upload seçin**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Yapılandırma ayarı tercih etki alanı" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. Dosya **Seç'i seçin**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Yapılandırma ayarıyla ilgili dosyayı seçme istemi" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. **MDATP_MDAV_MAU_settings.plist'i seçin**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Mdatpmdavmau ayarları" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. **Seç'Upload**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Yapılandırmayla ilgili dosyanın karşıya yükleme ayarı" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Yapılandırma ayarıyla ilgili dosyanın karşıya yükleme seçeneğini gösteren sayfa" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. **Kaydet**'i seçin.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Yapılandırma ayarıyla ilgili dosyanın kaydetme seçeneğini gösteren sayfa" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Kapsam **sekmesini** seçin.

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Yapılandırma ayarlarının Kapsam sekmesi" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. **Ekle**'yi seçin.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Dağıtım hedefleri ekleme seçeneği" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Yapılandırma ayarlarına daha fazla değer eklemek istediğiniz sayfa" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Yapılandırma ayarlarına daha fazla değer ekleyebilirsiniz sayfası" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. **Bitti'yi seçin**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Yapılandırma ayarlarıyla ilgili tamamlanma bildirimi" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>6. Adım: Postanıza tam disk Uç Nokta için Microsoft Defender

1. Jamf Ayarları Pro Yapılandırma **Profilleri'ne tıklayın**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Ayarları yapılandırılan profil" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. **+ Yeni'yi seçin**.

3. Aşağıdaki ayrıntıları girin:

    **Genel**
    - Ad: MDATP MDAV - EDR VE AV'ye Tam Disk Erişimi ver
    - Açıklama: MacOS Catalina veya daha yeni üzerinde, yeni Gizlilik Tercihleri İlke Denetimi
    - Kategori: Yok
    - Dağıtım yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar düzeyi

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Genel olarak yapılandırma ayarı" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. Gizlilik **Tercihleri İlkesi Denetimi Yapılandır'da Yapılandır'ı** **seçin**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Yapılandırma gizlilik ilkesi denetimi" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. Gizlilik **Tercihleri İlke Denetimi'ne** aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Yapılandırma ayarı gizlilik tercihi ilkesi denetim ayrıntıları" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. **+ Ekle'yi seçin**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Yapılandırma ayarı tüm dosyalar için sistem ilkesi ekle seçeneği" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles olarak ayarlayın**

    - "Erişim" altında: İzin Ver olarak **ayarlayın**

7. **Kaydet'i** seçin (sağ alttaki kayıt değil).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Yapılandırma ayarı için kaydetme işlemi" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. Yeni girdi `+` eklemek için **Uygulama Erişimi'nin** yanındaki işareti tıklatın.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Yapılandırma ayarıyla ilgili kaydetme işlemi" lightbox="images/tcc-add-entry.png":::

9. Aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav.epsext`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. **+ Ekle'yi seçin**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Yapılandırma ayarı tcc epsext girişi" lightbox="images/tcc-epsext-entry.png":::

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles olarak ayarlayın**

    - "Erişim" altında: İzin Ver olarak **ayarlayın**

11. **Kaydet'i** seçin (sağ alttaki kayıt değil).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="tcc epsext yapılandırma ayarının diğer örneği" lightbox="images/tcc-epsext-entry2.png":::

12. Kapsam **sekmesini** seçin.

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Yapılandırma ayarının kapsamını gösteren sayfa" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. **+ Ekle'yi seçin**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Yapılandırma ayarını gösteren sayfa" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. Grup **Adı altında** > Grupları **Grubu'>** **Contoso'nun Makine Grubu'nda öğesini seçin**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Contoso makine grubunun yapılandırma ayarı" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. **Ekle**'yi seçin.

16. **Kaydet**'i seçin.

17. **Bitti'yi seçin**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Contoso makine grubu yapılandırma ayarı" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Yapılandırma ayarı çizimi" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Alternatif olarak [full tümce.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) indirebilir ve Jamf Kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>7. Adım: Çekirdek uzantısını Uç Nokta için Microsoft Defender

> [!CAUTION]
> Apple Silicon (M1) cihazları KEXT'i desteklemez. KEXT ilkelerinden oluşan bir yapılandırma profili yüklemesi bu cihazlarda başarısız olur.

1. Yapılandırma **Profilleri'nin altında** **+ Yeni'yi seçin**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Sosyal medya gönderisi Açıklama otomatik olarak oluşturulur" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Kernel Extension
    - Açıklama: MDATP çekirdek uzantısı (kext)
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Yapılandırma ayarları mdatpmdav kernel" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. Onaylanmış **Çekirdek Uzantılarını Yapılandır'da Yapılandır'ı** **seçin**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Yapılandırma ayarlarının onaylanmış çekirdek uzantılarını görüntüleyen sayfa" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. Onaylanmış **Çekirdek Uzantıları alanına** aşağıdaki ayrıntıları girin:

    - Görünen Ad: Microsoft Corp.
    - Ekip Kimliği: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Onaylanmış Çekirdek Uzantıları bölmesi" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Kapsam **sekmesini** seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Yapılandırmanın Kapsam sekmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. **+ Ekle'yi seçin**.

7. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

8. **+ Ekle'yi seçin**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yapılandırma ayarları için ek değerler tanımladığınız sayfa" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. **Kaydet**'i seçin.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="MDATP MDAV Kernel uzantısı" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. **Bitti'yi seçin**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Yapılandırma Profilleri ayrıntıları sayfası" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Alternatif olarak[, kext.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) indirebilir ve Jamf kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>8. Adım: Sistem uzantılarının e-Uç Nokta için Microsoft Defender

1. Yapılandırma **Profilleri'nin altında** **+ Yeni'yi seçin**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Otomatik olarak oluşturulan sosyal medya gönderisi açıklaması" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Sistem Uzantıları
    - Açıklama: MDATP sistem uzantıları
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Yeni profilin yapılandırma ayarları sysext" lightbox="images/sysext-new-profile.png":::

3. Sistem **Uzantıları'nın altında Yapılandır'ı** **seçin**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Sistem uzantıları için Yapılandır seçeneğinin yer alan bölme" lightbox="images/sysext-configure.png":::

4. Sistem **Uzantıları'nın** içine aşağıdaki ayrıntıları girin:

   - Görünen Ad: Microsoft Corp. System Extensions
   - Sistem Uzantısı Türleri: İzin Verilen Sistem Uzantıları
   - Ekip Tanımlayıcısı: UBF8T346G9
   - İzin Verilen Sistem Uzantıları:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="MDATP MDAV sistem uzantıları bölmesi" lightbox="images/sysext-configure2.png":::

5. Kapsam **sekmesini** seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Hedef Bilgisayarlar seçim bölmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. **+ Ekle'yi seçin**.

7. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

8. **+ Ekle'yi seçin**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yeni macOS Yapılandırma Profili bölmesi" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. **Kaydet**'i seçin.

   :::image type="content" source="images/sysext-scope.png" alt-text="MDATP MDAV Sistem Uzantılarıyla ilgili seçeneklerin görüntüsü" lightbox="images/sysext-scope.png":::

10. **Bitti'yi seçin**.

    :::image type="content" source="images/sysext-final.png" alt-text="Yapılandırma ayarları sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>9. Adım: Ağ Uzantısını Yapılandırma

MacOS'ta Uç Nokta Algılama ve Yanıt özellikleri Uç Nokta için Microsoft Defender, yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

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

        :::image type="content" source="images/netext-create-profile.png" alt-text="mdatpmdav yapılandırma ayarı" lightbox="images/netext-create-profile.png":::

3. Kapsam **sekmesini** seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Yapılandırma ayarları sco sekmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. **+ Ekle'yi seçin**.

5. Grup **Adı altında** > **Grupları Grubu'>** **Contoso'nun Makine Grubu'nun seçin**.

6. **+ Ekle'yi seçin**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yapılandırma ayarları soluk" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. **Kaydet**'i seçin.

   :::image type="content" source="images/netext-scope.png" alt-text="İçerik Filtresi bölmesi" lightbox="images/netext-scope.png":::

8. **Bitti'yi seçin**.

   :::image type="content" source="images/netext-final.png" alt-text="Yapılandırma ayarları netext - son" lightbox="images/netext-final.png":::

Alternatif olarak[, Netfilter.mobileconfig'i](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) indirebilir ve Jamf Kullanarak Özel Yapılandırma Profillerini Dağıtma konusunda açıklandığı gibi [JAMF Yapılandırma Profilleri'ne Pro| 2. Yöntem: Upload Profili Jamf'e Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>10. Adım: macOS'ta Uç Nokta için Microsoft Defender taramaları zamanlama

[MacOS'ta bu programlarla taramaları Uç Nokta için Microsoft Defender yönergeleri izleyin](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>11. Adım: MacOS Uç Nokta için Microsoft Defender dağıtımı

1. 'i kayıtlı olduğunuz yere gidin `wdav.pkg`.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Dosya gezgini wdav paketi" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. olarak yeniden adlandır.`wdav_MDM_Contoso_200329.pkg`

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Dosya gezgini1 wdavmdm paketi" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Jamf Pro açın.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Jamfpro için yapılandırma ayarları" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Bilgisayarınızı seçin ve üst dişli simgesine tıklayın, ardından Bilgisayar **Yönetimi'ne tıklayın**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Yapılandırma ayarları - bilgisayar yönetimi" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. **Paketler'de** **+ Yeni'yi seçin**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Otomatik olarak oluşturulan paket için kuş açıklaması" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. Yeni **Paket'e** aşağıdaki ayrıntıları girin:

    **Genel sekmesi**
    - Görünen Ad: Şimdilik boş bırakın. Çünkü, pkg'nizi seçtiğiniz zaman sıfırlanır.
    - Kategori: Yok (varsayılan)
    - Dosya adı: Dosya Seç

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Yapılandırma ayarları için Genel sekmesi" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Dosyayı açın ve veya işaretlerini `wdav.pkg` seçin `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Otomatik olarak oluşturulan paketin açıklamasını görüntüleyen bilgisayar ekranı" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. **Aç**'ı seçin. Görünen **Ad'ı** **Microsoft Defender Gelişmiş Tehdit Koruması ve Güvenlik Microsoft Defender Virüsten Koruma**.

    **Bildirim Dosyası** gerekli değildir. Uç Nokta için Microsoft Defender Bildirim Dosyası olmadan çalışır.

    **Seçenekler sekmesi**: Varsayılan değerleri tutma.

    **Sınırlamalar sekmesi**: Varsayılan değerleri tutma.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Yapılandırma ayarlarının sınırlama sekmesi" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. **Kaydet**'i seçin. Paket Jamf'e Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Yapılandırma ayarlarıyla ilgili paket için yapılandırma ayarları paketi karşıya yükleme işlemi" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Paketin dağıtım için kullanılabilir olması birkaç dakika sürebilir.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Yapılandırma ayarları için paketi karşıya yükleme örneği" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. İlkeler **sayfasına** gidin.

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Yapılandırma ayarları ilkeleri" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Yeni **bir ilke oluşturmak için +** Yeni'yi seçin.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Yapılandırma ayarları yeni ilkesi" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. Genel **alanına** aşağıdaki ayrıntıları girin:

    - Görünen ad: MDATP Onboarding Contoso 200329 v100.86.92 veya sonrası

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Yapılandırma ayarları - MDATP onboard" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. Yinelenen **Iade'yi seçin**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Yapılandırma ayarları için yinelenen iade" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. **Kaydet**'i seçin.

14. **Yapılandır'ı > seçin**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Paketleri yapılandırma seçeneği" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Microsoft Defender **Gelişmiş** Tehdit **Koruması'nın yanındaki Ekle düğmesini seçin ve ardından Microsoft Defender Virüsten Koruma**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="MDATP MDA'ya daha fazla ayar ekleme seçeneği" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. **Kaydet**'i seçin.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Yapılandırma ayarları için kaydetme seçeneği" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Kapsam **sekmesini** seçin.

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Yapılandırma ayarlarıyla ilgili Kapsam sekmesi" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Hedef bilgisayarları seçin.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Bilgisayar grupları ekleme seçeneği" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Kapsam**

    **Ekle**'yi seçin.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Yapılandırma ayarları - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Yapılandırma ayarları - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Self Servis**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Yapılandırma ayarları için Self Servis sekmesi" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. **Bitti'yi seçin**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="Tamamlama seçeneğiyle Birlikte Contoso ekleme durumu" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="İlkeler sayfası" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
