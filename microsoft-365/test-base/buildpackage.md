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
ms.openlocfilehash: 277c185b633263a12687eec5a8eb9a1a34e1dbed
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015453"
---
# <a name="build-a-package"></a>Paket oluşturma
Paket, test .zip betiklerinizi içeren, önkoşul olan ikili dosya ve test betikleri içeren bir dosyadır. Bu Hızlı Başlangıç, ilk paketinizi oluşturmanız için size yol sunar ve bu pakette, uygulamanın Hazır gelen kutusu testini gerçekleştirebilirsiniz. 
  
*    *Hazır **(OOB)** testi, uygulama yüklemesi, başlatması, kapatması ve kaldırması yapar. Yüklemeden sonra, tek bir kaldırma çalıştırılamadan önce başlatma-kapatma yordamı 30 kez tekrarlanır. OOB testi, tüm standart derlemeleri karşılaştıracak şekilde paketiniz üzerinde standart Windows sağlar.*  
    
İsteğe bağlı olarak, başvuru yapmak [ve başlangıç yapmak](https://aka.ms/testbase-sample-package) için örnek paketimizi indirebilirsiniz. 

## <a name="create-a-folder-structure"></a>Klasör yapısı oluşturma 

Yerel bilgisayarınızda, aşağıdaki gibi bir klasör yapısı oluşturun:<br> 
![Paket oluşturmak için kullanılan klasör yapısı](Media/buildpackage1.png)

Şu klasörler kullanılır:
* **Uygulama\ikili**: Uygulama ve bağımlılık ikililerini kaydedin.<br> 
* **Uygulama\betikler**: betikleri kaydedarak uygulamayı yükleyin, açın, kapatın ve kaldırın.<br> 
* **Uygulama\günlükler**: Betikler bu klasöre günlükleri çıkış olarak yazmalı, test tamam ondan sonra günlükleri indirebilir ve çözümleyebilirsiniz.<br> 

## <a name="copy-binary-files"></a>İkili dosyaları kopyalama
Uygulama yükleme dosyalarınızı **App\bin klasörüne kopyalayın**. Uygulamanıza bağımlılıklar varsa, önce bunların yüklenmiş olması gerekir. Ayrıca, bağımlılık yükleme dosyalarını **App\bin klasörüne kopyalayın**.<br> 
![Klasördeki uygulama dosyalarının konumu](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>PowerShell betikleri ekleme
OOB sınaması yapmak için, PowerShell betiklerini eklemeniz ve uygulamanızı yüklemeniz, başlatmanız, kapatmanız ve kaldırmanız gerekir.
> [!NOTE]  
> *OOB testinde betikleri yükleme, başlatma ve kapatma betikleri gerekirken, betiği kaldırma isteğe bağlıdır*.
    
Betik aşağıdaki gibi klasöre eklenmiştir:  
![PowerShell betik dosyalarının klasördeki konumu](Media/buildpackage3.png)

Betikler çoğunlukla aşağıdaki davranışları içerir:<br> 
-   **Uygulamayı yüklemek/başlatmak/kapatmak/kaldırmak için komutları çalıştırın**. Örneğin, uygulamanız bir MSI dosyası ise, [yüklemek için msiexec](/windows-server/administration/windows-commands/msiexec) çalıştırın. <br> 
-   **Yükleme/başlatma/kapatma/kaldırma işlemi sonucundan emin olmak**, beklenen sonuç sıfır çıkış kodu iade etmektir. Test Base, sıfırdan başka bir çıkış kodu döndüren bir betiği hata olarak işaretler.<br> 
-   **Yeterli günlük kaydedin**, gelecekte kullanmak için uygun günlükleri kaydedin.<br> 

Lütfen aşağıdaki örneklere bakın. Bunları dosyalarınıza kopyalayıp buna uygun değişiklikler yapabilirsiniz. <br>

**Betik yükleme örneği (App\scripts\install\job.ps1)**
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

**Komut dosyası başlatma örneği (App\scripts\launch\job.ps1)**
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
Betikler ve ikili dosyalar hazır olduktan sonra, klasörü bir zip dosyası olarak sıkıştırmaya devam edersiniz. Uygulama klasörüne sağ tıklayın, ZIP dosyasına **sıkıştır'ı seçin**.<br>
![Zip dosyasına sıkıştırma](Media/buildpackage4.png)


## <a name="verify-your-package-locally-optional"></a>Paketinizi yerel olarak doğrulama (isteğe bağlı)
Zip paketini hazırdikten sonra Test Temel hesabınıza yükleyebilirsiniz. <br>
Bununla birlikte, betiklerin karşıya yüklemeden önce düzgün çalışması için testi yerel olarak çalıştırmak en iyisidir. Yerel bir test sorunları hızla tanımlayabilir ve karşıya yükleme işleminizi hızlandırabilirsiniz. Yerel olarak doğrulamak için aşağıdaki adımları izleyin:<br>
1.  Sanal makine hazırlama (Sanal Makine)<br>
    Şu anda her test için temiz bir ortam gerektiğinden, bu yerel test Windows sanal bir makine öneririz. Azure'da Windows VM oluşturmak kolaydır (Hızlı Başlangıç [: Windows](/azure/virtual-machines/windows/quick-create-portal) sanal makine), test için uygun bir Windows sürümü (resim) (örneğin, *Windows 10 Pro, sürüm 21H2*) seçin.<br>

2.  Paketinizi sanal makineye kopyalama<br>
    Paket dosyanızı SANAL MAKINE'ye kopyalamanın birçok yolu vardır. Azure VM kullanıyorsanız şunları seçebilirsiniz:
     -  Dosyayı doğrudan Uzak Masaüstü bağlantınıza kopyalayın. <br>
     -  Azure dosya paylaşımını kullanma ([Hızlı Başlangıç: Azure dosyası oluşturma ve yönetme](/azure/storage/files/storage-files-quick-create-use-windows))
    
    Bu test için belirli bir klasör oluşturabilir ve paket dosyasını bu klasörün altında kopyaabilirsiniz. Örneğin, *C:\TestBase*.<br>
3.  Paketi test etmek<br>
    Test Windows PowerShell açın, paketi içeren dizine (örneğin, CD C:\TestBase) geçiş yapın ve testlerinizi paket üzerinde çalıştırmaya başlatın:<br>
    a.  Paket dosyasını ayıkla.
     -  *Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase*<br>
    
    b.  Yükleme betiği çalıştırın.  
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    c.  Gerekirse VM'yi yeniden başlatın.<br>
    
    d.  Başlatma betiği çalıştırma.
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    e.  Betiği kapat'a çalıştır.
     -  *C:\TestBase\App\scripts\close\job.ps1*<br>
    
    f.  Kaldırma betiği çalıştırın (varsa).
     -  *C:\TestBase\App\scripts\uninstall\job.ps1*<br>
    
    Her adımdan sonra, betiğinizin içinde sorun olup olduğunu kontrol edin. Tüm betikler beklendiği gibi çalıştırıldısa, paketiniz Test Temel hesabınıza yüklenmeye hazır olur.


## <a name="next-steps"></a>Sonraki adımlar
[Upload olarak](uploadApplication.md)
 
 
