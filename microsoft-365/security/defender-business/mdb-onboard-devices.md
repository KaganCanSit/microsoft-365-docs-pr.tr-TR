---
title: Cihazları İş için Microsoft Defender ekleme
description: İş için Microsoft Defender'da cihaz ekleme seçenekleri hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba816430521db2848273a4f7c6ca7d1a61703690
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862284"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Cihazları İş için Microsoft Defender ekleme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

İş için Microsoft Defender ile, şirketinizin cihazlarını eklemek için aralarından seçim yapabileceğiniz çeşitli seçenekler vardır. Bu makale, seçeneklerinizde size yol gösterir ve eklemenin nasıl çalıştığına ilişkin bir genel bakış içerir.

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="what-to-do"></a>Yapılması gerekenler

1. İşletim sisteminizin sekmesini seçin: 

   - İstemcileri Windows
   - Windows Sunucusu (önizleme)
   - macOS bilgisayarlar
   - mobil cihazlar

2. Ekleme seçeneklerinizi görüntüleyin ve seçili sekmedeki yönergeleri izleyin.

3. Sonraki adımlarınıza geçin.

## <a name="windows-clients"></a>[**İstemcileri Windows**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>İstemcileri Windows

Windows istemci cihazlarını İş için Defender'a eklemek için aşağıdaki seçeneklerden birini belirleyin:

- [Yerel betik](#local-script-for-windows-clients) (cihazları Microsoft 365 Defender portalında el ile ekleme için)
- [Microsoft Endpoint Manager](#endpoint-manager-for-windows-clients) ([Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil)


### <a name="local-script-for-windows-clients"></a>Windows istemcileri için yerel betik

Windows istemci cihazlarını eklemek için yerel betik kullanabilirsiniz. Bir cihazda ekleme betiğini çalıştırdığınızda, Azure Active Directory ile bir güven oluşturur (bu güven yoksa), cihazı Microsoft Endpoint Manager kaydeder (henüz kaydedilmemişse) ve ardından cihazı İş için Defender'a ekler. Yerel betik yöntemi şu anda Endpoint Manager (veya Microsoft Intune) yoksa bile çalışır. Bu yöntemi kullanarak aynı anda en fazla 10 cihaz eklemenizi öneririz.

> [!TIP]
> Yerel betik yöntemini kullandığınızda bir kerede en fazla 10 cihaz eklemenizi öneririz.

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** >  **Endpoints'i** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

3. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından **Dağıtım yöntemi** bölümünde **Yerel betik'i** seçin. 

4. **Ekleme paketini indir'i** seçin. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

5. Windows bir cihazda, yapılandırma paketinin içeriğini Desktop klasörü gibi bir konuma ayıklayın. adlı `WindowsDefenderATPLocalOnboardingScript.cmd`bir dosyanız olmalıdır. 

6. Yönetici olarak Komut İstemi'ni açın.

7. Betik dosyasının konumunu yazın. Örneğin, dosyayı Desktop klasörüne kopyaladıysanız `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`yazın ve Enter tuşuna basın (veya **Tamam'ı** seçin).

8. Betik çalıştırıldıktan sonra [Algılama testi çalıştırma](#running-a-detection-test-on-a-windows-client) bölümüne geçin.

### <a name="endpoint-manager-for-windows-clients"></a>Windows istemcileri için Endpoint Manager

Aboneliğiniz [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) içeriyorsa, Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) Windows istemciler ve diğer cihazları ekleyebilirsiniz. Örneğin, [Microsoft 365 İş Ekstra](../../business/index.yml) varsa aboneliğinizin bir parçası olarak Endpoint Manager. Endpoint Manager [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Mobil Cihaz Yönetimi özelliklerini içerir](/mem/intune/fundamentals/what-is-device-management). 

Cihazları Intune kaydetmek için kullanılabilecek çeşitli yöntemler vardır. Aşağıdaki yöntemlerden biriyle başlamanızı öneririz:

- Şirkete ait veya şirket tarafından yönetilen cihazlar için [Windows otomatik kaydı etkinleştirme](/mem/intune/enrollment/windows-enroll)
- [Kullanıcılardan kendi Windows 10/11 cihazlarını Intune kaydetmelerini isteyin](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>Windows cihazlarda otomatik kaydı etkinleştirmek için

Otomatik kaydı ayarladığınızda, kullanıcılar iş hesabını cihaza ekler. Arka planda cihaz Azure Active Directory (Azure AD) kaydedip birleştirir ve Intune kaydedilir.

1. Azure portal ([https://portal.azure.com/](https://portal.azure.com/)) gidin ve oturum açın. 

2. **Azure Active Directory** >  **Mobilite (MDM ve MAM)** > **Microsoft Intune** seçin.

3. MDM Kullanıcı kapsamını ve MAM kullanıcı kapsamını yapılandırın.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Intune'da MDM kullanıcı kapsamını ve MAM kullanıcı kapsamını ayarlamanın ekran görüntüsü.":::

   - MDM Kullanıcı kapsamı için, tüm kullanıcıların Windows cihazlarını otomatik olarak kaydedebilmesi için **Tümü** seçeneğini belirlemenizi öneririz.
   - MAM kullanıcı kapsamı bölümünde, URL'ler için aşağıdaki varsayılan değerleri kullanmanızı öneririz:

       - **MDM Kullanım Koşulları URL’si**
       - **MDM Bulma URL’si**
       - **MAM uyumluluk URL’si**

4. **Kaydet**'i seçin.

5. Bir cihaz Intune kaydedildikten sonra bir cihaz grubuna ekleyebilirsiniz. [İş için Microsoft Defender'da cihaz grupları hakkında daha fazla bilgi edinin](mdb-create-edit-device-groups.md).


> [!TIP]
> Otomatik kayıt hakkında daha fazla bilgi edinmek için bkz[. Otomatik kayıt Windows etkinleştirme](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-devices"></a>Kullanıcıların kendi Windows cihazlarını kaydetmesini sağlamak için

1. Kaydın nasıl çalıştığını görmek için aşağıdaki videoyu izleyin: <br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Bu makaleyi kuruluşunuzdaki kullanıcılarla paylaşın: [Windows 10/11 cihazlarını Intune'a kaydedin](/mem/intune/user-help/enroll-windows-10-device).

3. Bir cihaz Intune kaydedildikten sonra bir cihaz grubuna ekleyebilirsiniz. [İş için Microsoft Defender'da cihaz grupları hakkında daha fazla bilgi edinin](mdb-create-edit-device-groups.md).

### <a name="running-a-detection-test-on-a-windows-client"></a>Windows istemcisinde algılama testi çalıştırma

Windows cihazları İş için Defender'a ekledikten sonra, her şeyin düzgün çalıştığından emin olmak için Windows bir cihazda algılama testi çalıştırabilirsiniz.

1. Windows cihazında bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ni açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştırıldıktan sonra Komut İstemi penceresi otomatik olarak kapatılır. Başarılı olursa algılama testi tamamlandı olarak işaretlenir ve yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yaklaşık 10 dakika içinde yeni bir uyarı görünür.

## <a name="view-a-list-of-onboarded-devices"></a>Eklenen cihazların listesini görüntüleme

İş için Defender'a eklenen cihazların listesini görüntülemek için, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)), gezinti bölmesindeki **Uç Noktalar'ın** altında **Cihaz giriş'i** seçin.

## <a name="next-steps"></a>Sonraki adımlar

- Eklenecek başka cihazlarınız varsa, cihazlardaki işletim sistemine karşılık gelen sekmeyi [seçin (Windows istemciler, Windows Server, macOS veya mobil cihazlar](#what-to-do)) ve bu sekmedeki yönergeleri izleyin.
- Cihazları eklemeyi bitirdiyseniz [5. Adım: İş için Microsoft Defender'de güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md) bölümüne geçin
- Bkz. [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md).

## <a name="windows-server"></a>[**Windows Server:**](#tab/WindowsServerEndpoints)

## <a name="windows-server-preview"></a>Windows Sunucusu (önizleme)

Yerel betik kullanarak bir Windows Sunucusu cihazı ekleyebilirsiniz. 

> [!IMPORTANT]
> Windows Sunucusu uç noktalarını ekleme özelliği şu anda önizleme aşamasındadır.

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** >  **Endpoints'i** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

3. **Windows Server 1803, 2019 ve 2022** gibi bir işletim sistemi seçin ve ardından **Dağıtım yöntemi** bölümünde **Yerel betik'i** seçin. 

   **R2 ve 2016 Windows Server 2012** seçerseniz, indirilip çalıştırılacak iki paketiniz olur: yükleme paketi ve ekleme paketi. Yükleme paketi, İş için Microsoft Defender aracısını yükleyen bir MSI dosyası içerir. Ekleme paketi, Windows Sunucu uç noktanızı İş için Defender'a ekleme betiğini içerir. 

4. **Ekleme paketini indir'i** seçin. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

   **R2 ve 2016 Windows Server 2012** seçtiyseniz **Yükleme paketini indir'i** de seçip çıkarılabilir bir sürücüye kaydedin

5. Windows Sunucusu uç noktanızda, yükleme/ekleme paketlerinin içeriğini Desktop klasörü gibi bir konuma ayıklayın. adlı `WindowsDefenderATPLocalOnboardingScript.cmd`bir dosyanız olmalıdır. 

   R2 veya Windows Server 2016 Windows Server 2012 ekliıyorsanız, önce yükleme paketini ayıklayın.

6. Yönetici olarak Komut İstemi'ni açın.

7. Windows Server 2012R2 veya Windows Server 2016 ekliyseniz, şu komutu çalıştırın: `Msiexec /i md4ws.msi /quiet`. 

   Windows Server 1803, 2019 veya 2022'yi ekliiyorsanız, bu adımı atlayın ve 8. adıma geçin.

8. Betik dosyasının konumunu yazın. Örneğin, dosyayı Desktop klasörüne kopyaladıysanız `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`yazın ve Enter tuşuna basın (veya **Tamam'ı** seçin).

9. [Windows Sunucusunda algılama testi çalıştırma](#running-a-detection-test-on-windows-server) işlemine geçin

### <a name="running-a-detection-test-on-windows-server"></a>Windows Sunucusunda algılama testi çalıştırma

Windows Server uç noktanızı İş için Defender'a ekledikten sonra, her şeyin düzgün çalıştığından emin olmak için bir algılama testi çalıştırabilirsiniz.

1. Windows Server cihazında bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ni açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştırıldıktan sonra Komut İstemi penceresi otomatik olarak kapatılır. Başarılı olursa algılama testi tamamlandı olarak işaretlenir ve yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yaklaşık 10 dakika içinde yeni bir uyarı görünür.

## <a name="view-a-list-of-onboarded-devices"></a>Eklenen cihazların listesini görüntüleme

İş için Defender'a eklenen cihazların listesini görüntülemek için, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)), gezinti bölmesindeki **Uç Noktalar'ın** altında **Cihaz giriş'i** seçin.

## <a name="next-steps"></a>Sonraki adımlar

- Eklenecek başka cihazlarınız varsa, cihazlardaki işletim sistemine karşılık gelen sekmeyi [seçin (Windows istemciler, Windows Server, macOS veya mobil cihazlar](#what-to-do)) ve bu sekmedeki yönergeleri izleyin.
- Cihazları eklemeyi bitirdiyseniz [5. Adım: İş için Microsoft Defender'de güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md) bölümüne geçin
- Bkz. [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md).

## <a name="macos"></a>[**macOS**](#tab/macOSdevices)

## <a name="macos-computers"></a>macOS bilgisayarlar

> [!NOTE]
> - [macOS cihazlarını eklemek için yerel bir betik](#local-script-for-macos) kullanmanızı öneririz. [macOS cihazları için kaydı Intune'de ayarlayabilmenize](/mem/intune/enrollment/macos-enroll) rağmen, macOS cihazlarını İş için Defender'a eklemek için en basit yöntem yerel betiktir. 

macOS cihazlarını eklemek için aşağıdaki seçeneklerden birini belirleyin:

- [macOS için yerel betik](#local-script-for-macos) (*önerilir*)
- [macOS için Endpoint Manager](#endpoint-manager-for-macos)

### <a name="local-script-for-macos"></a>macOS için yerel betik

Yerel betiği bir macOS cihazında çalıştırdığınızda, Azure Active Directory ile bir güven oluşturur (bu güven yoksa), cihazı Microsoft Endpoint Manager kaydeder (henüz kayıtlı değilse) ve ardından cihazı İş için Defender'a ekler. Yerel betik yöntemi şu anda Endpoint Manager (veya Microsoft Intune) yoksa bile çalışır. Bu yöntemi kullanarak aynı anda en fazla 10 cihaz eklemenizi öneririz.

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** >  **Endpoints'i** seçin ve ardından **Cihaz yönetimi'nin** altında **Ekleme'yi** seçin.

3. **macOS'u** seçin ve ardından **Dağıtım yöntemi** bölümünde **Yerel betik'i** seçin. 

4. **Ekleme paketini indir'i** seçin ve çıkarılabilir bir sürücüye kaydedin. Ayrıca **Yükleme paketini indir'i** seçin ve çıkarılabilir cihazınıza kaydedin.

5. Bir macOS cihazında, yükleme paketini yerel bir dizine olarak `wdav.pkg` kaydedin.

6. Ekleme paketini, yükleme paketi için kullandığınız dizine kaydedin `WindowsDefenderATPOnboardingPackage.zip` .

7. Kaydettiğinize gitmek için Bulucu'ya `wdav.pkg` gidin ve açın.

8. **Devam'ı** seçin, Lisans koşullarını kabul edin ve istendiğinde parolanızı girin.

9. Microsoft'tan bir sürücünün yüklenmesine izin vermeniz istenir ("Sistem Uzantısı Engellendi" veya "Yükleme beklemede" veya her ikisi de. Sürücünün yüklenmesine izin verilmelidir. Yüklemeye izin vermek için **Güvenlik Tercihlerini Aç'ı** veya **Sistem Tercihlerini** >  **AçGüvenlik & Gizlilik'i** ve ardından **İzin Ver'i** seçin.

10. Ekleme paketini çalıştırmak için Bash'te aşağıdaki Python komutunu kullanın: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`

11. Bir cihaz Intune kaydedildikten sonra bir cihaz grubuna ekleyebilirsiniz. [İş için Microsoft Defender'da cihaz grupları hakkında daha fazla bilgi edinin](mdb-create-edit-device-groups.md).

### <a name="endpoint-manager-for-macos"></a>macOS için Endpoint Manager

Aboneliğinizde [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) varsa macOS cihazlarını Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) ekleyebilirsiniz. Örneğin, [Microsoft 365 İş Ekstra](../../business/index.yml) varsa aboneliğinizin bir parçası olarak Endpoint Manager. Endpoint Manager [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Mobil Cihaz Yönetimi özelliklerini içerir](/mem/intune/fundamentals/what-is-device-management). 

Cihazları Intune kaydetmek için kullanılabilecek çeşitli yöntemler vardır. Aşağıdaki yöntemlerden biriyle başlamanızı öneririz:

- [Şirkete ait macOS cihazları için bir seçenek belirleyin](#options-for-company-owned-macos-devices)
- [Kullanıcılardan kendi macOS cihazlarını Intune kaydetmelerini isteyin](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>Şirkete ait macOS cihazları için seçenekler

Şirket tarafından yönetilen macOS cihazlarını Intune kaydetmek için aşağıdaki tabloda yer alan seçeneklerden birini belirleyin:

| Seçeneği  | Açıklama  |
|---------|---------|
| Apple Otomatik Cihaz Kaydı |  Apple Business Manager veya Apple School Manager aracılığıyla satın alınan cihazlarda kayıt deneyimini otomatikleştirmek için bu yöntemi kullanın. Otomatik cihaz kaydı kayıt profilini havadan dağıtır, bu nedenle cihazlara fiziksel erişiminiz olması gerekmez. <br/><br/>Bkz. [MacOS cihazlarını Apple Business Manager veya Apple School Manager ile otomatik olarak kaydetme](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Cihaz kayıt yöneticisi (DEM)  |  Büyük ölçekli dağıtımlar ve kuruluşunuzda kayıt kurulumuna yardımcı olabilecek birden çok kişi olduğunda bu yöntemi kullanın. Cihaz kayıt yöneticisi (DEM) izinleri olan biri, tek bir Azure Active Directory hesabıyla en fazla 1.000 cihaz kaydedebilir. Bu yöntem, cihazları kaydetmek için Şirket Portalı uygulamasını veya Microsoft Intune uygulamasını kullanır. Otomatik Cihaz Kaydı aracılığıyla cihazları kaydetmek için BIR DEM hesabı kullanamazsınız.<br/><br/> Bkz[. Cihaz kayıt yöneticisi hesabı kullanarak cihazları Intune kaydetme](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Doğrudan kayıt  | Doğrudan kayıt, kullanıcı benzitesi olmayan cihazları kaydeder, bu nedenle bu yöntem tek bir kullanıcıyla ilişkilendirilmeyen cihazlar için en iyisidir. Bu yöntem, kaydettiğiniz Mac'lere fiziksel erişiminiz olmasını gerektirir. <br/><br/>Bkz. [macOS cihazları için Doğrudan Kayıt'ı kullanma](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-macos-devices-in-intune"></a>Kullanıcılardan kendi macOS cihazlarını Intune kaydetmelerini isteyin

İşletmeniz kişilerin kendi cihazlarını Intune kaydetmesini tercih ederse, kullanıcılardan şu adımları izlemelerini isteyin:

1. Şirket Portalı web sitesine ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) gidin ve oturum açın.

2. Cihazlarını eklemek için Şirket Portalı web sitesindeki yönergeleri izleyin.

3. konumundaki Şirket Portalı uygulamasını [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac)yükleyin ve uygulamadaki yönergeleri izleyin.

### <a name="confirm-that-a-macos-device-is-onboarded"></a>MacOS cihazının eklendiğini onaylayın

1. Cihazın şirketinizle ilişkili olduğunu onaylamak için Bash'te aşağıdaki Python komutunu kullanın: `mdatp health --field org_id`.

2. macOS 10.15 (Catalina) veya sonraki bir sürümü kullanıyorsanız cihazınızı korumak için İş için Defender'a onay verin. **Sistem TercihleriGüvenlik** >  **&** **PrivacyPrivacyFull** >  **Disk Erişimi'ne** >  gidin. Değişiklik yapmak için kilit simgesini seçin (iletişim kutusunun en altında) ve ardından **İş için Microsoft Defender** (veya gördüğünüz buysa **Uç Nokta için Defender**)'ı seçin.

3. Cihazın eklendiğini doğrulamak için Bash'te aşağıdaki komutu kullanın: `mdatp health --field real_time_protection_enabled`

4. Bir cihaz Intune kaydedildikten sonra bir cihaz grubuna ekleyebilirsiniz. [İş için Microsoft Defender'da cihaz grupları hakkında daha fazla bilgi edinin](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Eklenen cihazların listesini görüntüleme

İş için Defender'a eklenen cihazların listesini görüntülemek için, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)), gezinti bölmesindeki **Uç Noktalar'ın** altında **Cihaz envanteri'ni** seçin.

## <a name="next-steps"></a>Sonraki adımlar

- Eklenecek başka cihazlarınız varsa, cihazlardaki işletim sistemine karşılık gelen sekmeyi seçin ([Windows istemciler, Windows Server, macOS veya mobil cihazlar](#what-to-do)) ve bu sekmedeki yönergeleri izleyin.
- Cihazları eklemeyi bitirdiyseniz [5. Adım: İş için Microsoft Defender'de güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md) bölümüne geçin
- Bkz. [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md).

## <a name="mobile-devices"></a>[**mobil cihazlar**](#tab/mobiles)

## <a name="mobile-devices"></a>Mobil cihazlar

Android ve iOS/iPadOS cihazları gibi mobil cihazları eklemek için Microsoft Intune gerekir. [Microsoft 365 İş Ekstra](../../business/index.yml) varsa, aboneliğinizin bir parçası olarak Endpoint Manager sahip olursunuz. Endpoint Manager [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Mobil Cihaz Yönetimi özelliklerini içerir](/mem/intune/fundamentals/what-is-device-management). 

Bu cihazları Intune kaydetme konusunda yardım almak için aşağıdaki kaynaklara bakın:

- [Android cihazları kaydetme](/mem/intune/enrollment/android-enroll)
- [iOS veya iPadOS cihazlarını kaydetme](/mem/intune/enrollment/ios-enroll)

Bir cihaz Intune kaydedildikten sonra bir cihaz grubuna ekleyebilirsiniz. [İş için Microsoft Defender'da cihaz grupları hakkında daha fazla bilgi edinin](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Sonraki adımlar

- Eklenecek başka cihazlarınız varsa, cihazlardaki işletim sistemine karşılık gelen sekmeyi seçin ([Windows istemciler, Windows Server, macOS veya mobil cihazlar](#what-to-do)) ve bu sekmedeki yönergeleri izleyin.
- Cihazları eklemeyi bitirdiyseniz [5. Adım: İş için Microsoft Defender'de güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md) bölümüne geçin
- Bkz. [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md).
