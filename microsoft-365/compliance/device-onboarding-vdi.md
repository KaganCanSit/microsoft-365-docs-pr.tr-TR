---
title: Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı
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
description: Yapılandırma paketini sanal masaüstü altyapısı (VDI) cihazına dağıtarak Microsoft 365 Uç Nokta veri kaybı önleme hizmetine eklenmelerini sağlayın.
ms.openlocfilehash: 6bfb0f69198afbcc9d2949d583e151631cc7953b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760635"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Kalıcı olmayan sanal masaüstü altyapısı cihazlarını ekleme

**Şunlar için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- Sanal masaüstü altyapısı (VDI) cihazları

> [!WARNING]
> Windows Sanal Masaüstü için Microsoft 365 Uç nokta veri kaybı önleme desteği tek oturum senaryolarını destekler. Windows Sanal Masaüstü'ne yönelik çoklu oturum senaryoları şu anda desteklenmemektedir.

## <a name="onboard-vdi-devices"></a>VDI cihazlarını ekleme

Microsoft 365 kalıcı olmayan sanal masaüstü altyapısı (VDI) oturumu eklemeyi destekler.

> [!NOTE]
> Kalıcı olmayan VDI oturumlarını eklemek için VDI cihazlarının Windows 10 1809 veya üzeri bir sürümde olması gerekir.

VDI'leri eklerken ilgili zorluklar olabilir. Bu senaryo için tipik zorluklar şunlardır:

- Gerçek sağlamadan önce Microsoft 365 eklenmelidir kısa süreli oturumları anında erken ekleme.
- Cihaz adı genellikle yeni oturumlar için yeniden kullanılır.

VDI cihazları Microsoft 365 Uyumluluk merkezinde şu şekilde görünebilir:

- Her cihaz için tek giriş.
Bu durumda, oturum oluşturulduğunda, örneğin katılımsız yanıt dosyası kullanılarak *aynı* cihaz adının yapılandırılması gerektiğini unutmayın.
- Her cihaz için birden çok giriş - her oturum için bir giriş.

Aşağıdaki adımlar VDI cihazlarını ekleme konusunda size yol gösterir ve tek ve birden çok giriş için adımları vurgular.

> [!WARNING]
> Düşük kaynak yapılandırmalarının olduğu ortamlarda, VDI önyükleme yordamı cihaz ekleme işlemini yavaşlatabilir.

1. [Microsoft Uyumluluk merkezi'nden](https://compliance.microsoft.com) VDI yapılandırma paketi .zip dosyasını (*DeviceCompliancePackage.zip*) alın.

2. Gezinti bölmesinde **Ayarlar** >  **Cihaz eklemeOnboarding'i** >  seçin.

3. **Dağıtım yöntemi** alanında **, kalıcı olmayan uç noktalar için VDI ekleme betikleri'ni** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

5. .zip dosyasından ayıklanan DeviceCompliancePackage klasöründeki dosyaları yolunun `golden` `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`altındaki resme kopyalayın.

6. Her cihaz için tek bir giriş uygulamıyorsanız DeviceComplianceOnboardingScript.cmd dosyasını kopyalayın.

7. Her cihaz için tek bir giriş uyguluyorsanız hem Onboard-NonPersistentMachine.ps1 hem de DeviceComplianceOnboardingScript.cmd dosyasını kopyalayın.

    > [!NOTE]
    > Klasörü görmüyorsanız `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , gizli olabilir. Dosya Gezgini **Gizli dosya ve klasörleri göster** seçeneğini belirlemeniz gerekir.

8. Yerel grup ilkesi Düzenleyicisi penceresini açın ve **Bilgisayar Yapılandırması** >  **Windows Ayarlar** >  **ScriptsStartup'a** >  gidin.

   > [!NOTE]
   > Etki alanı grup ilkesi, kalıcı olmayan VDI cihazlarının eklenmesi için de kullanılabilir.

9. Uygulamak istediğiniz yönteme bağlı olarak uygun adımları izleyin:

   **Her cihaz için tek giriş için**

   **PowerShell Betikleri** sekmesini seçin, ardından **Ekle'ye** tıklayın (Windows Explorer daha önce ekleme betiğini kopyaladığınız yolda açılır). PowerShell betiğini `Onboard-NonPersistentMachine.ps1`ekleme bölümüne gidin.

   **Her cihaz için birden çok giriş için**:

   **Betikler** sekmesini seçin, ardından **Ekle'ye** tıklayın (Windows Gezgin daha önce ekleme betiğini kopyaladığınız yolda doğrudan açılır). Ekleme bash betiğine `DeviceComplianceOnboardingScript.cmd`gidin.

10. Çözümünüzü test edin:
    1. Tek bir cihazla havuz oluşturun.
    1. Cihazda oturum açın.
    1. Cihazdan oturumu kapatın.
    1. Cihazda başka bir kullanıcıyla oturum açın.
    1. **Her cihaz için tek giriş için**: Microsoft Defender Güvenlik Merkezi yalnızca bir girişi denetleyin.
       **Her cihaz için birden çok giriş için**: Microsoft Defender Güvenlik Merkezi'da birden çok girdiyi denetleyin.

11. Gezinti bölmesinde **Cihazlar listesi'ne** tıklayın.

12. Cihaz adını girerek arama işlevini kullanın ve arama türü olarak **Cihaz'ı** seçin.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Kalıcı olmayan sanal masaüstü altyapısı (VDI) görüntülerini güncelleştirme

En iyi uygulama olarak, altın renkli görüntülere yama uygulamak için çevrimdışı bakım araçlarını kullanmanızı öneririz.

Örneğin, görüntü çevrimdışı kalırken bir güncelleştirmeyi yüklemek için aşağıdaki komutları kullanabilirsiniz:

```DOS
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

DISM komutları ve çevrimdışı bakım hakkında daha fazla bilgi için lütfen aşağıdaki makalelere bakın:

- [DISM kullanarak Windows görüntüsünü değiştirme](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [DISM Görüntü Yönetimi Command-Line Seçenekleri](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Çevrimdışı Windows Görüntüsündeki Bileşen Deposunun Boyutunu Küçültme](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Çevrimdışı hizmet, kalıcı olmayan VDI ortamınız için uygun bir seçenek değilse tutarlılığı ve algılayıcı durumunu sağlamak için aşağıdaki adımlar izlenmelidir:

1. Çevrimiçi bakım veya düzeltme eki uygulama için altın renkli görüntüyü önyükledikten sonra Microsoft 365 cihaz izleme algılayıcısını kapatmak için bir çıkarma betiği çalıştırın. Daha fazla bilgi için bkz. [Yerel betik kullanarak cihazları çıkarma](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. Aşağıdaki komutu bir CMD penceresinde çalıştırarak algılayıcının durdurulduğunu doğrulayın:

   ```DOS
   sc query sense
   ```

3. Görüntüye gerektiği gibi hizmet sağlayın.

4. PsExec.exe kullanarak aşağıdaki komutları çalıştırın (algılayıcının önyüklemeden bu yana birikmiş olabileceği siber klasör içeriğini temizlemek için buradan indirilebilir https://download.sysinternals.com/files/PSTools.zip) ):

    ```DOS
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Normalde yaptığınız gibi altın resmi yeniden mühürleyin.

## <a name="related-topics"></a>İlgili konular

- [grup ilkesi kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-sccm.md)
- [Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-mdm.md)
- [Yerel bir komut dosyası kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-script.md)
- [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
