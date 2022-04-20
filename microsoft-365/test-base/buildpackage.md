---
title: Paket oluşturma
description: Paketinizi oluşturma
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 02/28/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: db09d1b182965c0a21945b025601c21d5100212b
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952918"
---
# <a name="build-a-package"></a>Paket oluşturma

Paket, Test Temeli'ni kullanmak için önkoşul olan uygulama ikili ve test betiklerinizi içeren bir .zip dosyasıdır. Bu Hızlı Başlangıç, uygulamanızda ilk paketinizi oluşturmanız için size yol gösterir. Bu paketle uygulamanızda ilk çalıştırma testi gerçekleştirebilirsiniz.

- *Kullanıma **Açık (OOB)** testi, uygulamanızın yükleme, başlatma, kapatma ve kaldırma işlemlerini gerçekleştirir. Yüklemeden sonra başlatma-kapatma yordamı, tek bir kaldırma çalıştırılmadan önce 30 kez yinelenir. OOB testi, Windows derlemeleri karşılaştırmak için paketinizde standart telemetri sağlar.*

İsteğe bağlı olarak, başvurmak ve başlamak için [örnek paketimizi](https://aka.ms/testbase-sample-package) indirebilirsiniz.

## <a name="create-a-folder-structure"></a>Klasör yapısı oluşturma

Yerel bilgisayarınızda aşağıdaki gibi bir klasör yapısı oluşturun:

![Paket oluşturmak için kullanılan klasör yapısı](Media/buildpackage1.png)

Bu klasörler kullanılır:

- **Uygulama\bin**: Uygulamayı ve bağımlılık ikili dosyalarını kaydedin.
- **Uygulama\betikler**: Uygulamanızı yüklemek, başlatmak, kapatmak ve kaldırmak için betikleri kaydedin.
- **Uygulama\günlükler**: Betikler günlükleri bu klasöre çıkarmalıdır, ardından test tamamlandıktan sonra günlükleri indirip analiz edebilirsiniz.

## <a name="copy-binary-files"></a>İkili dosyaları kopyalama

Uygulama yükleme dosyalarınızı **App\bin'e** kopyalayın. Uygulamanızın bağımlılıkları varsa, önce bunların yüklenmesi gerekir. Ayrıca, bağımlılık yükleme dosyalarını **App\bin'e** kopyalayın.

![Klasördeki uygulama dosyaları konumu](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>PowerShell betikleri ekleme

OOB testi gerçekleştirmek için uygulamanızı yüklemek, başlatmak, kapatmak ve kaldırmak için PowerShell betikleri eklemeniz gerekir.

> [!NOTE]
> *OOB testinde, yükleme, başlatma ve kapatma betikleri gerekirken kaldırma betiği isteğe bağlıdır*.

Betik klasöre aşağıdaki gibi eklenmelidir:

![PowerShell betik dosyalarının klasördeki konumu](Media/buildpackage3.png)

Betik genellikle aşağıdaki davranışları içerir:

- **Uygulamayı yüklemek/başlatmak/kapatmak/kaldırmak için komutlarını çalıştırın**. Örneğin, uygulamanız bir MSI dosyasıysa, yüklemek için [msiexec](/windows-server/administration/windows-commands/msiexec) komutunu çalıştırın.
- **Yükleme/başlatma/kapatma/kaldırma işleminin sonucunu denetleyin**, sonuç bekleniyorsa sıfır çıkış kodu döndürun. Test Temeli, sıfır olmayan bir çıkış kodu döndürdüğünde betik çalıştırmasını hata olarak işaretler.
- **Yeterli günlükleri kaydedin**, gelecekte kullanmak üzere uygun günlükleri kaydedin.

Lütfen aşağıdaki örneklere bakın. Bunları dosyalarınıza kopyalayıp buna göre değişiklik yapabilirsiniz.

**Yükleme betiği örneği (App\scripts\install\job.ps1)**:

```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"

        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Installing TestBaseM365 Digital Clock")
        push-location "..\..\bin"
        if ([Environment]::Is64BitProcess) {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        else {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        $arguments = "/i "+$installer_name+" /quiet /L*v "+"$log_dir"+"\atp-client-installation.log"

        $installer = Start-Process msiexec.exe $arguments -wait -passthru
        pop-location

        if ($installer.exitcode -eq 0) {
            log("Installation succesful as $($installer.exitcode)")
        }
        else {
            log("Error: Installation failed as $($installer.exitcode)")
            $exit_code = $installer.exitcode
        }

        log("Installation script finished as $exit_code")
        pop-location
        exit $exit_code
```

**Başlatma betiği örneği (App\scripts\launch\job.ps1)**:

```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"

        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Launch TestBaseM365 Digital Clock")

        $PROCESS_NAME = "DigitalClock"
        $exePath = "C:\Program Files\Test Base M365\DigitalClock\DigitalClock.exe"

        Start-Process -FilePath $exePath

         if (Get-Process -Name $PROCESS_NAME) {
                log("Launch successfully $PROCESS_NAME...")
                $exit_code = 0
         }
         else {
            log("Not launched $PROCESS_NAME...")
            $exit_code = 1
         }

        log("Launch script finished as $exit_code")
        pop-location
        exit $exit_code
```

## <a name="compress-to-zip-file"></a>Zip dosyasına sıkıştırma

Betikler ve ikili dosyalar hazırlandıktan sonra klasörü zip dosyasına sıkıştırmaya devam edin. Uygulama klasörüne sağ tıklayın, **ZIP dosyasına sıkıştır'ı** seçin.

![Zip dosyasına sıkıştırma](Media/buildpackage4.png)

## <a name="verify-your-package-locally-optional"></a>Paketinizi yerel olarak doğrulama (isteğe bağlı)

Zip paketini derledikten sonra Test Temeli hesabınıza yükleyebilirsiniz.

Ancak, karşıya yüklemeden önce betiklerin düzgün çalıştığından emin olmak için testi yerel olarak çalıştırmak en iyi yöntemdir. Yerel bir test sorunları hızla belirleyebilir ve karşıya yükleme işleminizi hızlandırabilir. Yerel olarak doğrulamak için aşağıdaki adımları izleyin:

1. VM hazırlama (Sanal Makine)

   Her test için şu anda temiz bir Windows ortamı gerektiğinden, bu yerel test için bir sanal makine kullanmanızı öneririz. Azure'da Windows VM oluşturmak kolaydır ([Hızlı başlangıç: Windows sanal makine](/azure/virtual-machines/windows/quick-create-portal)), örneğin Windows 10 Pro, sürüm *21H2* gibi testiniz için uygun bir Windows sürümü (görüntü) seçebilirsiniz.<br>

2. Paketinizi VM'ye kopyalama

   Paket dosyanızı VM'ye kopyalamanın birçok yolu vardır. Azure VM kullanıyorsanız şunları seçebilirsiniz:

     - Dosyayı doğrudan Uzak Masaüstü bağlantınıza kopyalayın.
     - Azure dosya paylaşımını kullanma ([Hızlı Başlangıç: Azure dosyasını oluşturma ve yönetme](/azure/storage/files/storage-files-quick-create-use-windows))

   Bu test için belirli bir klasör oluşturabilir ve paket dosyasını bu klasörün altına kopyalayabilirsiniz. Örneğin, *C:\TestBase*.

3. Paketi test edin

   Windows PowerShell açın, paketi içeren dizine (örneğin, `cd C:\TestBase`) geçin ve testlerinizi paket üzerinde çalıştırmaya başlayın:

   1. Paket dosyasını ayıklayın.

      ```powershell
      Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase
      ```

   2. Yükleme betiğini çalıştırın.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   3. Gerekirse VM'yi yeniden başlatın.

   4. Başlatma betiğini çalıştırın.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   5. Kapatma betiğini çalıştırın.

      ```powershell
      C:\TestBase\App\scripts\close\job.ps1
      ```

   6. Kaldırma betiğini çalıştırın (varsa).

      ```powershell
      C:\TestBase\App\scripts\uninstall\job.ps1
      ```

Her adımdan sonra betiğinizde herhangi bir sorun olup olmadığını kontrol edebilirsiniz. Tüm betikler beklendiği gibi çalıştırılırsa paketiniz Test Temeli hesabınıza yüklenmeye hazırdır.

## <a name="next-steps"></a>Sonraki adımlar

[Paket Upload](uploadApplication.md)
