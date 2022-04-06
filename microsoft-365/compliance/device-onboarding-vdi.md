---
title: Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme
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
description: Yapılandırma paketini, Microsoft 365 Uç nokta veri kaybı önleme hizmetine dahil etmek için sanal masaüstü altyapısı (VDI) cihazında dağıtın.
ms.openlocfilehash: 00804c93022f21715e3604eeb45c22caa4745f91
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682162"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Kalıcı olmayan sanal masaüstü altyapısı cihazlarını ekleme

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- Sanal masaüstü altyapısı (VDI) cihazları

> [!WARNING]
> Microsoft 365 Masaüstü için uç nokta veri kaybı önleme Windows, tek oturum senaryolarını destekler. Sanal Masaüstü'nüzde Windows oturum senaryoları şu anda desteklenmiyor.

## <a name="onboard-vdi-devices"></a>VDI cihazlarını ekleme

Microsoft 365 kalıcı olmayan sanal masaüstü altyapısı (VDI) oturumu eklemeyi destekler.

> [!NOTE]
> Kalıcı olmayan VDI oturumları için VDI cihazlarının 1809 veya Windows 10 devam ediyor olması gerekir.

VDA'ları eklemeye yönelik zorluklarla ilgili sorunlar olabilir. Aşağıda, bu senaryoyla ilgili tipik güçlükler ve sorunlar yermaktadır:

- Gerçek sağlama öncesinde son oturumlara Microsoft 365 olan kısa Microsoft 365 erken ekleme.
- Cihaz adı normalde yeni oturumlar için yeniden kullanılır.

VDI cihazları Uyumluluk merkezi'Microsoft 365 aşağıdaki gibi görünebilir:

- Her cihaz için tek giriş.
Bu durumda, oturum *oluşturulduğunda aynı cihaz* adının yapılandırılması gerektiğini unutmayın; örneğin katılımsız yanıt dosyası kullanılarak.
- Her cihaz için birden çok giriş- her oturum için bir girdi.

Aşağıdaki adımlar, VDI cihazlarını ekleme adımlarını size yönlendirecek ve tek ve birden çok giriş için adımları vurgular.

> [!WARNING]
> Kaynak yapılandırmalarının düşük olduğu ortamlarda VDI önyükleme yordamı cihaz ekleme işlemini yavaşlatabilir.

1. Microsoft Uyumluluk Merkezi'nden VDI .zip paketini (*DeviceCompliancePackage.zip*) [edinebilirsiniz](https://compliance.microsoft.com).

2. Gezinti bölmesinde,Device  > **onboardingOnboarding Ayarlar'ı** >  seçin.

3. Dağıtım yöntemi **alanında** , kalıcı olmayan uç noktalar **için VDI ekleme betikleri'ne seçin**.

4. Paketi **indir'e** tıklayın ve .zip kaydedin.

5. Dosyadan ayıklanan DeviceCompliancePackage klasöründeki dosyaları .zip yolunun `golden` altındaki görüntüye kopyalayın `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Her cihaz için tek bir girdi uygulayıyorsanız, DeviceComplianceOnboardingScript.cmd'yi kopyalayın.

7. Her cihaz için tek bir giriş uygulayıyorsanız, hem Onboard-NonPersistentMachine.ps1 DeviceComplianceOnboardingScript.cmd'yi kopyalayın.

    > [!NOTE]
    > Klasörü görmüyorsanız `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` gizlenmiş olabilir. Dosya Gezgini'nde Gizli **dosya ve klasörleri göster** seçeneğini seçmeniz gerekir.

8. Yerel Grup İlkesi Düzenleyicisi penceresini açın ve Bilgisayar **Yapılandırması'Windows Ayarlar** >  >  **Başlat'a** >  gidin.

   > [!NOTE]
   > Domain Group Policy be also used for onboarding non-persistent VDI devices.

9. Uygulamak için kullandığınız yönteme bağlı olarak, uygun adımları izleyin:

   **Her cihaz için tek bir giriş için**

   **PowerShell Betikleri** sekmesini seçin, ardından **Ekle'ye** tıklayın (Windows Explorer, ekleme betiğinin daha önce kopya bulunduğu yolda açılır). PowerShell betiği eklemeye gidin `Onboard-NonPersistentMachine.ps1`.

   **Her cihaz için birden çok giriş için**:

   **Betikler sekmesini** seçin ve **Ekle'Windows** tıklayın (Windows Explorer, ekleme betiğinin daha önce kopya bulunduğu yolda açılır). Ekleme bash betiğine gidin `DeviceComplianceOnboardingScript.cmd`.

10. Çözümlerinizi test etmek için:
    1. Tek bir cihazla havuz oluşturun.
    1. Cihazda oturum açın.
    1. Cihazdan oturumu kapatın.
    1. Başka bir kullanıcıyla cihazda oturum açın.
    1. **Her cihaza tek bir giriş için**: Bir cihazda yalnızca bir giriş Microsoft Defender Güvenlik Merkezi.
       **Her cihaz için birden çok giriş için**: Bir cihazda birden çok Microsoft Defender Güvenlik Merkezi.

11. Gezinti **bölmesinde Cihazlar** listesine tıklayın.

12. Cihazın adını girerek arama işlevini kullanın ve arama türü olarak **Cihaz'ı** seçin.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Kalıcı olmayan sanal masaüstü altyapısı (VDI) görüntülerini güncelleştirme

En iyi uygulama olarak, altın renkli resimlere yama yapmak için çevrimdışı hizmet araçlarının kullanılması önerilir.

Örneğin, resim çevrimdışıyken bir güncelleştirme yüklemek için aşağıdaki komutları kullanabilirsiniz:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

DISM komutları ve çevrimdışı hizmet hakkında daha fazla bilgi için lütfen aşağıdaki makalelere bakın:

- [DISM Windows resim değiştirme](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [DISM Image Management Command-Line Options](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Çevrimdışı Depolama Alanı'nın Bileşen Mağazası'nın Boyutunu Windows Resmi](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Çevrimdışı hizmet, kalıcı olmayan VDI ortamınız için uygun bir seçenek yoksa tutarlılık ve algılayıcı sağlığı sağlamak için aşağıdaki adımlar atılacaktır:

1. Çevrimiçi bakım veya düzeltme eki için altın resmi önyükledikten sonra, cihaz izleme algılayıcısı olan Microsoft 365 kapatmak için bir offboard betiği çalıştırın. Daha fazla bilgi için bkz [. Yerel betik kullanarak çıkartan cihazlar](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. CmD penceresinde aşağıdaki komutu çalıştırarak algılayıcının durdurulurken durdurulur:

   ```console
   sc query sense
   ```

3. Görüntüyü gereken şekilde servise alın.

4. Önyüklemeden bu yana algılayıcının PsExec.exe siber klasör içeriğini temizlemeye kadar indirilebilen e-postayı ( https://download.sysinternals.com/files/PSTools.zip) PsExec.exe) kullanarak aşağıdaki komutları çalıştırın:

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Altın resmi her zaman olduğu gibi yeniden kapatabilirsiniz.

## <a name="related-topics"></a>İlgili konular

- [Grup Windows 10 kullanarak Windows 11 cihazı ekleme ve kullanma](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 cihaz ve 11 Windows cihaz Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma](device-onboarding-mdm.md)
- [Yerel bir Windows 10 kullanarak Windows 10 ve 11 Windows cihaz kullanın](device-onboarding-script.md)
- [Microsoft Defender Gelişmiş Tehdit Koruması'nın ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
