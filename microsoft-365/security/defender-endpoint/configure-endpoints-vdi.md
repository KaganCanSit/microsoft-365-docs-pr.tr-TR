---
title: Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme
description: Yapılandırma paketini sanal masaüstü altyapısı (VDI) cihazında dağıtın; böylelikle Uç nokta hizmeti için Microsoft Defender'a da dahil edin.
keywords: Sanal masaüstü altyapısını (VDI) cihazı, vdi'yi, cihaz yönetimini yapılandırma, Uç nokta için Microsoft Defender'ı yapılandırma, uç noktalar
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: 3e430d44789a1f3c43ec55a20ee7e06521f2dcaf
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015240"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını mobil cihaza Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Sanal masaüstü altyapısı (VDI) cihazları
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Kalıcı VDI'ler** -  [Uç nokta için](configure-endpoints.md) Microsoft Defender'a kalıcı bir VDI makinesi ekleme, masaüstü veya dizüstü bilgisayar gibi fiziksel bir makineyle aynı şekilde uygulanır. Grup ilkesi, Microsoft Endpoint Manager ve diğer yöntemler kalıcı bir makineyi eklemede kullanılabilir. Microsoft 365 Defender portalında, (https://security.microsoft.com)ekleme'nin altında tercih ettiğiniz ekleme yöntemini seçin ve bu türle ilgili yönergeleri izleyin. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme

Uç Nokta için Defender kalıcı olmayan VDI oturumu eklemeyi destekler.

VDA'ları eklemeye yönelik zorluklarla ilgili sorunlar olabilir. Aşağıda, bu senaryoyla ilgili tipik güçlükler ve sorunlar yermaktadır:

- Gerçek sağlama öncesinde Uç Nokta için Defender'a sağlanması gereken, kısa vadeli bir oturumun anında erken eklemesi.
- Cihaz adı normalde yeni oturumlar için yeniden kullanılır.

VDI cihazları Uç nokta portalı için Defender'da şu şekilde görünebilir:

- Her cihaz için tek giriş.

  > [!NOTE]
  > Bu durumda, *oturum* oluşturulduğunda örneğin katılımsız yanıt dosyası kullanılarak aynı cihaz adının yapılandırılması gerekir.

- Her cihaz için birden çok giriş- her oturum için bir girdi.

Aşağıdaki adımlar, VDI cihazlarını ekleme adımlarını size yönlendirecek ve tek ve birden çok giriş için adımları vurgular.

> [!WARNING]
> Düşük kaynak yapılandırmalarının olduğu ortamlarda VDI önyükleme yordamı Uç nokta algılayıcısı kullanımı için Defender'ı yavaşlatabilir.

### <a name="for-windows-10-or-windows-11-or-windows-server-2019-or-windows-server-2022"></a>Windows 10, Windows 11, Windows Server 2019 veya Windows Server 2022 için

1.  Hizmet ekleme sihirbazından indirdiğiniz .zip dosyası *(WindowsDefenderATPOnboardingPackage.zip*) VDI yapılandırma paketini açın. Paketi şu portaldan da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>:

    1. Gezinti bölmesinde, Gezinti **Bölmesi'Ayarlar** >  **EndpointsDevice** >  **managementOnboarding** >  öğesini seçin.

    1. İşletim sistemini seçin.

    1.  Dağıtım yöntemi **alanında** , kalıcı olmayan uç noktalar **için VDI ekleme betikleri'ne seçin**.

    1. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. .zip dosyasından ayıklanan WindowsDefenderATPOnboardingPackage klasöründeki dosyaları yol altındaki golden/master görüntüye kopyalayın `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Her cihaz için birden çok giriş uygulayıyorsanız ( her oturum için bir girdi) WindowsDefenderATPOnboardingScript.cmd'yi kopyalayın.
    2. Her cihaz için tek bir giriş uygulayıyorsanız, hem Onboard-NonPersistentMachine.ps1 hem de WindowsDefenderATPOnboardingScript.cmd'yi kopyalayın.

    > [!NOTE]
    > Klasörü görmüyorsanız `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` gizlenmiş olabilir. Dosya Gezgini'nde Gizli **dosya ve klasörleri göster** seçeneğini seçmeniz gerekir.

3. Yerel Grup İlkesi Düzenleyicisi penceresini açın ve Betik **Başlatma'da Bilgisayar** \> **Windows Ayarlar** \> **gidin**\>.

   > [!NOTE]
   > Domain Group Policy be also used for onboarding non-persistent VDI devices.

4. Uygulamak için kullandığınız yönteme bağlı olarak, uygun adımları izleyin:
    - Her cihaza tek bir giriş için:

         **PowerShell Betikleri** sekmesini seçin, ardından **Ekle'ye** tıklayın (Windows Explorer, ekleme betiğinin daha önce kopya bulunduğu yolda açılır). PowerShell betiği eklemeye gidin `Onboard-NonPersistentMachine.ps1`. Diğer dosyayı belirtmenize gerek yok, çünkü otomatik olarak tetiklenir.

    - Her cihaz için birden çok giriş için:

         **Betikler sekmesini** seçin ve **Ekle'Windows** tıklayın (Windows Explorer, ekleme betiğinin daha önce kopya bulunduğu yolda açılır). Ekleme bash betiğine gidin `WindowsDefenderATPOnboardingScript.cmd`.

5. Çözümlerinizi test etmek için:
   1. Tek bir cihazla havuz oluşturun.
   2. Cihazda oturum açın.
   3. Cihazdan oturumu kapatın.
   4. Başka bir kullanıcıyla cihazda oturum açın.
   5. Uygulamak için kullandığınız yönteme bağlı olarak, uygun adımları izleyin:
      - Her cihaza tek bir giriş için: Portalda tek bir Microsoft 365 Defender denetleme.
      - Her cihaza birden çok giriş için: Bir portalda birden çok Microsoft 365 Defender kontrol edin.

6. Gezinti **bölmesinde Cihazlar** listesine tıklayın.

7. Cihazın adını girerek arama işlevini kullanın ve arama türü olarak **Cihaz'ı** seçin.

## <a name="for-downlevel-skus-windows-server-2008-r22012-r22016"></a>Aşağı düzey SKU'lar için (Windows Server 2008 R2/2012 R2/2016)

> [!NOTE]
> Aşağıdaki kayıt defteri yalnızca hedef "Her cihaz için tek girdi" elde etmek olduğunda ilgili kayıt defteridir.

1. Kayıt defteri değerini aşağıdaki şekilde ayarlayın:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    veya komut satırı kullanarak:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Sunucu [ekleme işlemini izleyin](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Kalıcı olmayan sanal masaüstü altyapısı (VDI) görüntülerini güncelleştirme

En iyi uygulama olarak, altın yaması/asıl resimlere yama yapmak için çevrimdışı hizmet araçlarının kullanılması önerilir.

Örneğin, resim çevrimdışıyken bir güncelleştirme yüklemek için aşağıdaki komutları kullanabilirsiniz:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

DISM komutları ve çevrimdışı hizmet hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [DISM Windows resim değiştirme](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [DISM Image Management Command-Line Options](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Çevrimdışı Depolama Alanı'nın Bileşen Mağazası'nın Boyutunu Windows Resmi](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Çevrimdışı hizmet, kalıcı olmayan VDI ortamınız için uygun bir seçenek değilse tutarlılık ve algılayıcı sağlığı sağlamak için aşağıdaki adımlar atılacaktır:

1. Çevrimiçi bakım veya düzeltme eki için ana resmi önyükledikten sonra, Uç nokta algılayıcısı için Defender'ı kapatmak için bir offboard betiği çalıştırın. Daha fazla bilgi için bkz [. Yerel betik kullanarak çıkartan cihazlar](configure-endpoints-script.md#offboard-devices-using-a-local-script).

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
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Altın/ana resmi normalde olduğu gibi yeniden kullanın.

## <a name="related-topics"></a>İlgili konular
- [Grup Windows kullanarak diğer cihazları ekleme](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows cihazları Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Mobil Windows Yönetim araçlarını kullanarak cihazları ekleme](configure-endpoints-mdm.md)
- [Yerel Windows kullanarak cihazları ekleme](configure-endpoints-script.md)
- [Uç nokta ekleme sorunları için Microsoft Defender'da sorun giderme](troubleshoot-onboarding.md)
