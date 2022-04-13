---
title: Jamf Pro'da macOS ilkelerinde Uç Nokta için Microsoft Defender ayarlama
description: Jamf Pro'da macOS ilkelerinde Uç Nokta için Microsoft Defender ayarlamayı öğrenin
keywords: policies, microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 8d248eef175da6de3e329b4ec9b75b1111c668a6
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824728"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Jamf Pro'da macOS ilkelerinde Uç Nokta için Microsoft Defender ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Mac'te Uç Nokta için Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu sayfa Jamf Pro'de macOS ilkelerini ayarlamak için uygulamanız gereken adımlarda size yol gösterir.

Aşağıdaki adımları uygulamanız gerekir:

1. [Uç Nokta için Microsoft Defender ekleme paketini alma](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Ekleme paketini kullanarak Jamf Pro'da yapılandırma profili oluşturma](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Uç Nokta için Microsoft Defender ayarlarını yapılandırma](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Uç Nokta için Microsoft Defender bildirim ayarlarını yapılandırma](#step-4-configure-notifications-settings)
5. [Microsoft AutoUpdate'i (MAU) yapılandırma](#step-5-configure-microsoft-autoupdate-mau)
6. [Uç Nokta için Microsoft Defender tam disk erişimi verme](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Uç Nokta için Microsoft Defender için Çekirdek uzantısını onayla](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Uç Nokta için Microsoft Defender için Sistem uzantılarını onaylama](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Ağ Uzantısını Yapılandırma](#step-9-configure-network-extension)
10. [macOS'ta Uç Nokta için Microsoft Defender ile tarama zamanlama](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [macOS'ta Uç Nokta için Microsoft Defender dağıtma](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>1. Adım: Uç Nokta için Microsoft Defender ekleme paketini alma

1. [Microsoft 365 Defender](https://security.microsoft.com) Ayarlar > **Uç Noktaları > Ekleme'ye** gidin.

2. İşletim sistemi olarak macOS ve dağıtım yöntemi olarak Mobil Cihaz Yönetimi / Microsoft Intune'yi seçin.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Microsoft Defender Güvenlik Merkezi Ayarlar sayfası" lightbox="images/onboarding-macos.png":::

3. **Ekleme paketini indir** (WindowsDefenderATPOnboardingPackage.zip) seçeneğini belirleyin.

4. öğesini ayıklayın `WindowsDefenderATPOnboardingPackage.zip`.

5. Dosyayı tercih ettiğiniz konuma kopyalayın. Örneğin, `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>2. Adım: Ekleme paketini kullanarak Jamf Pro'de yapılandırma profili oluşturma

1. Önceki bölümde yer alan dosyayı `WindowsDefenderATPOnboarding.plist` bulun.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="Windows Defender ATP Ekleme dosyası" lightbox="images/plist-onboarding-file.png":::

2. Jamf Pro oturum açın, **Bilgisayarlar** >  **Yapılandırma Profilleri'ne** gidin ve **Yeni'yi** seçin.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Yeni bir Jamf Pro panosu oluşturduğunuz sayfa" lightbox="images/jamf-pro-configure-profile.png":::

3. Aşağıdaki ayrıntıları girin:

   **Genel**:

   - Ad: macOS için MDE ekleme
   - Açıklama: macOS için MDE EDR ekleme
   - Kategori: Yok
   - Dağıtım Yöntemi: Otomatik Olarak Yükleme
   - Düzey: Bilgisayar Düzeyi

4.  **Uygulama & Özel Ayarlar** sayfasına gidin ve **Upload** >  **Ekle'yi** seçin.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Yapılandırma uygulaması ve özel ayarlar" lightbox="images/jamfpro-mac-profile.png":::

5. **Upload Dosya (PLIST dosyası)** öğesini seçin ve **ardından Tercih Etki Alanı'nda** şu değeri girin: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="jamfpro plist karşıya yükleme dosyası" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Dosya karşıya yükleme özelliği List dosyası" lightbox="images/jamfpro-plist-file.png":::

6. **Aç'ı** seçin ve ekleme dosyasını seçin.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Ekleme dosyası" lightbox="images/jamfpro-plist-file-onboard.png":::

7. **Upload'ı** seçin.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Karşıya yüklenen plist dosyası" lightbox="images/jamfpro-upload-plist.png":::

8. **Kapsam** sekmesini seçin.

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Kapsam sekmesi" lightbox="images/jamfpro-scope-tab.png":::

9. Hedef bilgisayarları seçin.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Hedef bilgisayarlar" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Hedefler" lightbox="images/jamfpro-targets.png":::

10. **Kaydet**'i seçin.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Hedef bilgisayarların dağıtımı" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Hedef bilgisayarların seçimi" lightbox="images/jamfpro-target-selected.png":::

11. **Bitti'yi** seçin.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Hedef grubun bilgisayarları" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Yapılandırma profillerinin listesi" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>3. Adım: Uç Nokta için Microsoft Defender ayarlarını yapılandırma

UÇ NOKTA IÇIN MICROSOFT DEFENDER yapılandırmasının tek tek ayarlarını düzenlemek için JAMF Pro GUI kullanabilir veya metin düzenleyicisinde bir yapılandırma Plist'i oluşturup JAMF Pro'e yükleyerek eski yöntemi kullanabilirsiniz.

**Tercih Etki Alanı** olarak tam `com.microsoft.wdav` olarak kullanmanız gerektiğini unutmayın Uç Nokta için Microsoft Defender yalnızca bu adı kullanır ve `com.microsoft.wdav.ext` yönetilen ayarlarını yükler!

(Gui `com.microsoft.wdav.ext` yöntemini kullanmayı tercih ettiğiniz nadir durumlarda sürüm kullanılabilir, ancak şemaya henüz eklenmemiş bir ayarı da yapılandırmanız gerekir.)

### <a name="gui-method"></a>GUI yöntemi

1. Schema.json dosyasını [Defender'ın GitHub deposundan](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) indirin ve yerel bir dosyaya kaydedin:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Bilgisayarlar -> Yapılandırma Profilleri altında yeni bir Yapılandırma Profili oluşturun, **Genel** sekmesine aşağıdaki ayrıntıları girin:

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Yeni bir profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Hiçbiri (varsayılan)
    - Düzey: Bilgisayar Düzeyi (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle (varsayılan)

3. **Uygulama & Özel Ayarlar** sekmesine gidin, **Dış Uygulamalar'ı** seçin, Ekle'ye tıklayın ve tercih etki alanında kullanmak üzere **Kaynak olarak Özel Şema'yı** kullanın.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Özel şema ekleme" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Tercih Etki Alanı olarak girin`com.microsoft.wdav`, **Şema Ekle'ye** tıklayın ve 1. Adımda indirilen schema.json dosyasını **Upload**. **Kaydet**'e tıklayın.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="şemayı Upload" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Desteklenen tüm Uç Nokta için Microsoft Defender yapılandırma ayarlarını aşağıda **, Tercih Etki Alanı Özellikleri** altında görebilirsiniz. Yönetilmesini istediğiniz ayarları seçmek için **Özellikler ekle/kaldır'a** tıklayın ve değişikliklerinizi kaydetmek için **Tamam'a** tıklayın. (seçili olmayan Ayarlar yönetilen yapılandırmaya dahil edilmeyecektir; son kullanıcı bu ayarları makinelerinde yapılandırabilecektir.)

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Seçilen yönetilen ayarlar" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Ayarların değerlerini istenen değerlerle değiştirin. Belirli bir ayarın belgelerini almak için **Daha fazla bilgi'ye** tıklayabilirsiniz. ( **Plist önizlemesine** tıklayarak yapılandırma plist'in nasıl görüneceğini inceleyebilirsiniz. **Görsel düzenleyicisine dönmek için Form düzenleyicisi'ne** tıklayın.)

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Ayarlar değerlerini değiştirdiğiniz sayfa" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. **Kapsam** sekmesini seçin.

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Yapılandırma profili kapsamı" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. **Contoso'nun Makine Grubu'nun seçin**.

9. **Ekle'yi** ve ardından **Kaydet'i** seçin.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Yapılandırma ayarlarını ekleyebileceğiniz sayfa" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Yapılandırma ayarlarını kaydedebileceğiniz sayfa" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. **Bitti'yi** seçin. Yeni **Yapılandırma profilini** görürsünüz.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Yapılandırma ayarlarını tamamladığınız sayfa" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Uç Nokta için Microsoft Defender zaman içinde yeni ayarlar ekler. Bu yeni ayarlar şemaya eklenir ve github'da yeni bir sürüm yayımlanır.
Güncelleştirmelere sahip olmak için yapmanız gereken tek şey, **uygulama & Özel Ayarlar** sekmesinde güncelleştirilmiş bir şema indirmek, var olan yapılandırma profilini **düzenlemek ve Şemayı düzenlemektir**.

### <a name="legacy-method"></a>Eski yöntem

1. Aşağıdaki Uç Nokta için Microsoft Defender yapılandırma ayarlarını kullanın:

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Varsayılan olarak açık değildir, macOS için bir üçüncü taraf AV çalıştırmayı planlıyorsanız olarak ayarlayın `true`.

    - Dışlamalar
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR örnektedir, bir kavram kanıtından geçiyorsanız, özellikle EICAR'ı test ediyorsanız kaldırın.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - Etiketler
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

2. Dosyayı olarak `MDATP_MDAV_configuration_settings.plist`kaydedin.

3. Jamf Pro panosunda **Bilgisayarlar'ı** ve **yapılandırma profillerini** açın. **Yeni'ye** tıklayın ve **Genel** sekmesine geçin.

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Yeni profil görüntüleyen sayfa" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV yapılandırma ayarları
    - Açıklama:\<blank\>
    - Kategori: Hiçbiri (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="MDATP MDAV yapılandırma ayarları" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. **Uygulama & Özel Ayarlar** **Yapılandır'ı** seçin.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Uygulama ve özel ayarlar" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. **Upload Dosyası (PLIST dosyası) öğesini** seçin.

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Yapılandırma ayarları plist dosyası" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. **Tercihler Etki Alanı** alanına yazın `com.microsoft.wdav`ve **PLIST Dosyası'Upload** seçin.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Yapılandırma ayarları tercihleri etki alanı" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. **Dosya Seç'i** seçin.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Plist dosyasını seçme istemi" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. **MDATP_MDAV_configuration_settings.plist** dosyasını ve ardından **Aç'ı** seçin.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="mdatpmdav yapılandırma ayarları" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. **Upload'ı** seçin.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Yapılandırma ayarı karşıya yükleme" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Yapılandırma ayarlarıyla ilgili görüntüyü karşıya yükleme istemi" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Intune dosyasını karşıya yüklerseniz aşağıdaki hatayı alırsınız:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Yapılandırma ayarlarıyla ilgili intune dosyasını karşıya yükleme istemi" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. **Kaydet**'i seçin.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Yapılandırma ayarlarıyla ilgili görüntüyü kaydetme seçeneği" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Dosya karşıya yüklenir.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Yapılandırma ayarlarıyla ilgili karşıya yüklenen dosya" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Yapılandırma ayarları sayfası" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. **Kapsam** sekmesini seçin.

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Yapılandırma ayarlarının kapsamı" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. **Contoso'nun Makine Grubu'nun seçin**.

15. **Ekle'yi** ve ardından **Kaydet'i** seçin.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Yapılandırma ayarları addsav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Yapılandırma ayarlarının bildirimi" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. **Bitti'yi** seçin. Yeni **Yapılandırma profilini** görürsünüz.

    ![Yapılandırma ayarları yapılandırma profili görüntüsünün görüntüsü.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Yapılandırma profilinin ayarları" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

## <a name="step-4-configure-notifications-settings"></a>4. Adım: Bildirim ayarlarını yapılandırma

Bu adımlar macOS 10.15 (Catalina) veya daha yeni sürümler için geçerlidir.

1. Jamf Pro panosunda **Bilgisayarlar'ı** ve ardından **Yapılandırma Profilleri'ni** seçin.

2. **Yeni'ye** tıklayın ve **Seçenekler** için aşağıdaki ayrıntıları girin:

    - Sekme **Genel**:
        - **Ad**: MDATP MDAV Bildirim ayarları
        - **Açıklama**: macOS 10.15 (Catalina) veya daha yenisi
        - **Kategori**: Hiçbiri *(varsayılan)*
        - **Dağıtım Yöntemi**: Otomatik Olarak Yükle *(varsayılan)*
        - **Düzey**: Bilgisayar Düzeyi *(varsayılan)*

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Yeni macOS yapılandırma profili sayfası" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - Sekme **Bildirimleri'ne** tıklayın, **Ekle'ye** tıklayın ve aşağıdaki değerleri girin:
        - **Paket Kimliği**: `com.microsoft.wdav.tray`
        - **Kritik Uyarılar**: **Devre Dışı Bırak'a** tıklayın
        - **Bildirimler**: **Etkinleştir'e** tıklayın
        - **Başlık uyarı türü**: **Ekle ve**  *Geçici'yi seçin (varsayılan)*
        - **Kilit ekranında bildirimler**: **Gizle'ye** tıklayın
        - **Bildirim Merkezi'ndeki bildirimler**: **Görüntüle'ye** tıklayın
        - **Rozet uygulaması simgesi**: **Görüntü'ye** tıklayın

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="Yapılandırma ayarları mdatpmdav bildirim tepsisi" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - Sekme **Bildirimleri'ne** tıklayın, Bir kez daha **ekle'ye** tıklayın, aşağı kaydırarak **Yeni Bildirimler Ayarlar**
        - **Paket Kimliği**: `com.microsoft.autoupdate.fba`
        - Ayarların geri kalanını yukarıdakilerle aynı değerlerle yapılandırın

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Yapılandırma ayarları mdatpmdav notifications mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Artık bildirim yapılandırmalarına sahip iki 'tablonuz' olduğunu unutmayın **; biri Paket Kimliği için: com.microsoft.wdav.tray**, diğeri **paket kimliği: com.microsoft.autoupdate.fba**. Uyarı ayarlarını gereksinimlerinize göre yapılandırabilirsiniz ancak Paket Kimlikleri daha önce açıklandığı gibi olmalı ve **Bildirimler** için **Ekle** anahtarı **Açık** olmalıdır.

3. **Kapsam** sekmesini ve ardından **Ekle'yi** seçin.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Yapılandırma ayarları için değer ekleyebileceğiniz sayfa" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. **Contoso'nun Makine Grubu'nun seçin**.

5. **Ekle'yi** ve ardından **Kaydet'i** seçin.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Contoso makine grubu yapılandırma ayarları için değerleri kaydedebileceğiniz sayfa" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Yapılandırma ayarlarının tamamlanma bildirimini görüntüleyen sayfa" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. **Bitti'yi** seçin. Yeni **Yapılandırma profilini** görürsünüz.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Tamamlanan yapılandırma ayarları" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>5. Adım: Microsoft AutoUpdate'i (MAU) yapılandırma

1. Aşağıdaki Uç Nokta için Microsoft Defender yapılandırma ayarlarını kullanın:

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

2. olarak `MDATP_MDAV_MAU_settings.plist`kaydedin.

3. Jamf Pro panosunda **Genel'i** seçin.

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Yapılandırma ayarları" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV MAU ayarları
    - Açıklama: macOS için MDATP için Microsoft AutoUpdate ayarları
    - Kategori: Hiçbiri (varsayılan)
    - Dağıtım Yöntemi: Otomatik Olarak Yükle(varsayılan)
    - Düzey: Bilgisayar Düzeyi(varsayılan)

5. **Uygulama & Özel Ayarlar** **Yapılandır'ı** seçin.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Yapılandırma ayarı uygulaması ve özel ayarlar" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. **Upload Dosyası (PLIST dosyası) öğesini** seçin.

7. **Tercih Etki Alanı** alanına şunu girin: `com.microsoft.autoupdate2`ve **ardından PLIST Dosyası'Upload** seçin.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Yapılandırma ayarı tercih etki alanı" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. **Dosya Seç'i** seçin.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Yapılandırma ayarıyla ilgili dosyayı seçme istemi" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. **MDATP_MDAV_MAU_settings.plist** öğesini seçin.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="mdatpmdavmau ayarları" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. **Upload'ı** seçin.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Yapılandırma ayarıyla ilgili dosyanın karşıya yüklenmesi" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Yapılandırma ayarıyla ilgili dosyanın karşıya yükleme seçeneğinin görüntülendiği sayfa" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. **Kaydet**'i seçin.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Yapılandırma ayarıyla ilgili dosya için kaydetme seçeneğinin görüntülendiği sayfa" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. **Kapsam** sekmesini seçin.

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Yapılandırma ayarları için Kapsam sekmesi" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. **Ekle**'yi seçin.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Dağıtım hedefleri ekleme seçeneği" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Yapılandırma ayarlarına daha fazla değer eklediğiniz sayfa" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Yapılandırma ayarlarına daha fazla değer ekleyebileceğiniz sayfa" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. **Bitti'yi** seçin.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Yapılandırma ayarlarıyla ilgili tamamlama bildirimi" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>6. Adım: Uç Nokta için Microsoft Defender tam disk erişimi verme

1. Jamf Pro panosunda **Yapılandırma Profilleri'ni** seçin.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Ayarların yapılandırılacağı profil" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. **+ Yeni'yi** seçin.

3. Aşağıdaki ayrıntıları girin:

    **Genel**
    - Ad: MDATP MDAV - EDR ve AV'ye Tam Disk Erişimi verme
    - Açıklama: macOS Catalina veya daha yeni sürümlerde yeni Gizlilik Tercihleri İlkesi Denetimi
    - Kategori: Yok
    - Dağıtım yöntemi: Otomatik Olarak Yükle
    - Düzey: Bilgisayar düzeyi

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Genel olarak yapılandırma ayarı" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. **Gizlilik Tercihlerini Yapılandır İlke Denetimi'nde** **Yapılandır'ı** seçin.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Yapılandırma gizlilik ilkesi denetimi" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. **Gizlilik Tercihleri İlkesi Denetimi'ne** aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Yapılandırma ayarı gizlilik tercihi ilkesi denetim ayrıntıları" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. **+ Ekle'yi** seçin.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Yapılandırma ayarı sistem ilkesi tüm dosyaları ekle seçeneği" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles** olarak ayarlayın

    - "Erişim" altında: **İzin Ver** olarak ayarlayın

7. **Kaydet'i** seçin (sağ alttakini değil).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Yapılandırma ayarı için kaydetme işlemi" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. `+` Yeni bir giriş eklemek için **Uygulama Erişimi'nin** yanındaki işaretine tıklayın.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Yapılandırma ayarıyla ilgili kaydetme işlemi" lightbox="images/tcc-add-entry.png":::

9. Aşağıdaki ayrıntıları girin:

    - Tanımlayıcı: `com.microsoft.wdav.epsext`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. **+ Ekle'yi** seçin.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Yapılandırma ayarı tcc epsext girdisi" lightbox="images/tcc-epsext-entry.png":::

    - Uygulama veya hizmet altında: **SystemPolicyAllFiles** olarak ayarlayın

    - "Erişim" altında: **İzin Ver** olarak ayarlayın

11. **Kaydet'i** seçin (sağ alttakini değil).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="Tcc epsext yapılandırma ayarının diğer örneği" lightbox="images/tcc-epsext-entry2.png":::

12. **Kapsam** sekmesini seçin.

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Yapılandırma ayarının kapsamını gösteren sayfa" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. **+ Ekle'yi** seçin.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Yapılandırma ayarını gösteren sayfa" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. **Grup Adı'nın** altında **Bilgisayar Grupları** > > **Contoso'nun MachineGroup öğesini** seçin.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Contoso machine group yapılandırma ayarı" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. **Ekle**'yi seçin.

16. **Kaydet**'i seçin.

17. **Bitti'yi** seçin.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="contoso machine-group yapılandırma ayarı" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Yapılandırma ayarı çizimi" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Alternatif olarak[, fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) dosyasını indirebilir ve [Jamf Pro| kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF Yapılandırma Profillerine yükleyebilirsiniz Yöntem 2: Jamf Pro yapılandırma profilini Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>7. Adım: Uç Nokta için Microsoft Defender için Çekirdek uzantısını onaylama

> [!CAUTION]
> Apple Silicon (M1) cihazları KEXT'yi desteklemez. KEXT ilkelerini içeren bir yapılandırma profilinin yüklenmesi bu cihazlarda başarısız olur.

1. **Yapılandırma Profilleri'nde** **+ Yeni'yi** seçin.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Sosyal medya gönderisi Açıklama otomatik olarak oluşturuldu" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Çekirdek Uzantısı
    - Açıklama: MDATP çekirdek uzantısı (kext)
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Yapılandırma ayarları mdatpmdav çekirdeği" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. **Onaylı Çekirdek Uzantılarını Yapılandır** bölümünde **Yapılandır'ı** seçin.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Yapılandırma ayarlarının onaylanan çekirdek uzantılarını gösteren sayfa" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. **Onaylı Çekirdek Uzantıları'na** aşağıdaki ayrıntıları girin:

    - Görünen Ad: Microsoft Corp.
    - Ekip Kimliği: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Onaylı Çekirdek Uzantıları bölmesi" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. **Kapsam** sekmesini seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Yapılandırmanın Kapsam sekmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. **+ Ekle'yi** seçin.

7. **Grup Adı'nın** altında **Bilgisayar Grupları** > seçin > **Contoso'nun Makine Grubunu** seçin.

8. **+ Ekle'yi** seçin.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yapılandırma ayarları için ek değerler tanımladığınız sayfa" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. **Kaydet**'i seçin.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="MDATP MDAV Çekirdek uzantısı" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. **Bitti'yi** seçin.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Yapılandırma Profilleri ayrıntıları sayfası" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Alternatif olarak[, kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) dosyasını indirebilir ve [Jamf Pro| kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF Yapılandırma Profilleri'ne yükleyebilirsiniz Yöntem 2: Jamf Pro yapılandırma profilini Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>8. Adım: Uç Nokta için Microsoft Defender için Sistem uzantılarını onaylama

1. **Yapılandırma Profilleri'nde** **+ Yeni'yi** seçin.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Otomatik olarak oluşturulan sosyal medya gönderisinin açıklaması" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Aşağıdaki ayrıntıları girin:

    **Genel**

    - Ad: MDATP MDAV Sistem Uzantıları
    - Açıklama: MDATP sistem uzantıları
    - Kategori: Yok
    - Dağıtım Yöntemi: Otomatik Olarak Yükleme
    - Düzey: Bilgisayar Düzeyi

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Yapılandırma ayarları sysext yeni profili" lightbox="images/sysext-new-profile.png":::

3. **Sistem Uzantıları'nda** **Yapılandır'ı** seçin.

   :::image type="content" source="images/sysext-configure.png" alt-text="Sistem uzantıları için Yapılandır seçeneğini içeren bölme" lightbox="images/sysext-configure.png":::

4. **Sistem Uzantıları'na** aşağıdaki ayrıntıları girin:

   - Görünen Ad: Microsoft Corp. Sistem Uzantıları
   - Sistem Uzantısı Türleri: İzin Verilen Sistem Uzantıları
   - Takım Tanımlayıcısı: UBF8T346G9
   - İzin Verilen Sistem Uzantıları:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="MDATP MDAV sistem uzantıları bölmesi" lightbox="images/sysext-configure2.png":::

5. **Kapsam** sekmesini seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Hedef Bilgisayarlar seçim bölmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. **+ Ekle'yi** seçin.

7. **Grup Adı'nın** altında **Bilgisayar Grupları** > seçin > **Contoso'nun Makine Grubunu** seçin.

8. **+ Ekle'yi** seçin.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yeni macOS Yapılandırma Profili bölmesi" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. **Kaydet**'i seçin.

   :::image type="content" source="images/sysext-scope.png" alt-text="MDATP MDAV Sistem Uzantıları ile ilgili seçeneklerin görüntülenmesi" lightbox="images/sysext-scope.png":::

10. **Bitti'yi** seçin.

    :::image type="content" source="images/sysext-final.png" alt-text="Yapılandırma ayarları sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>9. Adım: Ağ Uzantısını Yapılandırma

Uç Nokta Algılama ve Yanıt özelliklerinin bir parçası olarak macOS'ta Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender portalına bildirir. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesine izin verir.

Bu adımlar macOS 10.15 (Catalina) veya daha yeni sürümler için geçerlidir.

1. Jamf Pro panosunda **Bilgisayarlar'ı** ve ardından **Yapılandırma Profilleri'ni** seçin.

2. **Yeni'ye** tıklayın ve **Seçenekler** için aşağıdaki ayrıntıları girin:

    - Sekme **Genel**:
        - **Ad**: Microsoft Defender Ağ Uzantısı
        - **Açıklama**: macOS 10.15 (Catalina) veya daha yenisi
        - **Kategori**: Hiçbiri *(varsayılan)*
        - **Dağıtım Yöntemi**: Otomatik Olarak Yükle *(varsayılan)*
        - **Düzey**: Bilgisayar Düzeyi *(varsayılan)*

    - Sekme **İçerik Filtresi**:
        - **Filtre Adı**: Microsoft Defender İçerik Filtresi
        - **Tanımlayıcı**: `com.microsoft.wdav`
        - **Hizmet Adresi**, **Kuruluş**, **Kullanıcı Adı**, **Parola**, **Sertifika** boş bırakın (**Ekle** seçili *değil*)
        - **Filtre Sırası**: Denetçi
        - **Yuva Filtresi**: `com.microsoft.wdav.netext`
        - **Yuva Filtresi Belirlenmiş Gereksinimi**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - **Ağ Filtresi** alanlarını boş bırakın (**Ekle** seçili *değil*)

        **Tanımlayıcı**, **Yuva Filtresi** ve **Yuva Filtresi Belirlenmiş Gereksinim'in** yukarıda belirtildiği gibi tam değerleri olduğunu unutmayın.

        :::image type="content" source="images/netext-create-profile.png" alt-text="mdatpmdav yapılandırma ayarı" lightbox="images/netext-create-profile.png":::

3. **Kapsam** sekmesini seçin.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Yapılandırma ayarları sco sekmesi" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. **+ Ekle'yi** seçin.

5. **Grup Adı'nın** altında **Bilgisayar Grupları** > seçin > **Contoso'nun Makine Grubunu** seçin.

6. **+ Ekle'yi** seçin.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Yapılandırma ayarları soluk" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. **Kaydet**'i seçin.

   :::image type="content" source="images/netext-scope.png" alt-text="İçerik Filtresi bölmesi" lightbox="images/netext-scope.png":::

8. **Bitti'yi** seçin.

   :::image type="content" source="images/netext-final.png" alt-text="Yapılandırma ayarları netext - final" lightbox="images/netext-final.png":::

Alternatif olarak, [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) dosyasını indirebilir ve [Jamf Pro| kullanarak Özel Yapılandırma Profilleri Dağıtma bölümünde açıklandığı gibi JAMF Yapılandırma Profilleri'ne yükleyebilirsiniz Yöntem 2: Jamf Pro yapılandırma profilini Upload](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>10. Adım: macOS'ta Uç Nokta için Microsoft Defender ile tarama zamanlama

[macOS'ta Uç Nokta için Microsoft Defender ile tarama zamanlama](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp) yönergelerini izleyin.

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>11. Adım: macOS'ta Uç Nokta için Microsoft Defender dağıtma

1. kaydettiğiniz `wdav.pkg`yere gidin.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Dosya gezgini wdav paketi" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. olarak `wdav_MDM_Contoso_200329.pkg`yeniden adlandırın.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Dosya gezgini1 wdavmdm paketi" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Jamf Pro panosunu açın.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="jamfpro için yapılandırma ayarları" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Bilgisayarınızı seçin ve üstteki dişli simgesine tıklayın, ardından **Bilgisayar Yönetimi'ni** seçin.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Yapılandırma ayarları - bilgisayar yönetimi" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. **Paketler'de** **+ Yeni'yi** seçin.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Otomatik olarak oluşturulan paket için kuş Açıklaması" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. **Yeni Paket'e** aşağıdaki ayrıntıları girin:

    **Genel sekmesi**
    - Görünen Ad: Şimdilik boş bırakın. Çünkü pkg'nizi seçtiğinizde sıfırlanır.
    - Kategori: Hiçbiri (varsayılan)
    - Dosya adı: Dosya Seç

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Yapılandırma ayarları için Genel sekmesi" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Dosyayı açın ve veya `wdav_MDM_Contoso_200329.pkg`üzerine `wdav.pkg` gelin.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Otomatik olarak oluşturulan paketin açıklamasını görüntüleyen bilgisayar ekranı" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. **Aç**'ı seçin. **Görünen Ad'ı** **Microsoft Defender Gelişmiş Tehdit Koruması ve Microsoft Defender Virüsten Koruma** olarak ayarlayın.

    **Bildirim Dosyası** gerekli değildir. Uç Nokta için Microsoft Defender Bildirim Dosyası olmadan çalışır.

    **Seçenekler sekmesi**: Varsayılan değerleri koru.

    **Sınırlamalar sekmesi**: Varsayılan değerleri koru.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Yapılandırma ayarları için sınırlama sekmesi" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. **Kaydet**'i seçin. Paket Jamf Pro'a yüklenir.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Yapılandırma ayarlarıyla ilgili paket için yapılandırma ayarları paketi karşıya yükleme işlemi" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Paketin dağıtım için kullanılabilir olması birkaç dakika sürebilir.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Yapılandırma ayarları için paketi karşıya yükleme örneği" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. **İlkeler** sayfasına gidin.

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Yapılandırma ayarları ilkeleri" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Yeni bir ilke oluşturmak için **+ Yeni'yi** seçin.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Yapılandırma ayarları yeni ilkesi" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. **Genel'de** aşağıdaki ayrıntıları girin:

    - Görünen ad: MDATP Contoso 200329 v100.86.92 veya üzerini ekleme

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Yapılandırma ayarları - MDATP ekleme" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. **Yinelenen İade Et'i** seçin.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Yapılandırma ayarları için yinelenen iade" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. **Kaydet**'i seçin.

14. **Paketler > Yapılandır'ı** seçin.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Paketleri yapılandırma seçeneği" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. **Microsoft Defender Gelişmiş Tehdit Koruması'nın** yanındaki **Ekle** düğmesini seçin ve Microsoft Defender Virüsten Koruma.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="MDATP MDA'ya daha fazla ayar ekleme seçeneği" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. **Kaydet**'i seçin.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Yapılandırma ayarları için kaydetme seçeneği" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. **Kapsam** sekmesini seçin.

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Yapılandırma ayarlarıyla ilgili Kapsam sekmesi" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Hedef bilgisayarları seçin.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Bilgisayar grupları ekleme seçeneği" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Kapsam**

    **Ekle**'yi seçin.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Yapılandırma ayarları - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Yapılandırma ayarları - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Self servis**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Yapılandırma ayarları için Self Servis sekmesi" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. **Bitti'yi** seçin.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="Contoso ekleme durumu ve bunu tamamlama seçeneği" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="İlkeler sayfası" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
