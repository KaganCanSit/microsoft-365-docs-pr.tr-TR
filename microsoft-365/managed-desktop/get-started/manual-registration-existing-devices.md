---
title: Mevcut cihazlar için el ile kayıt
description: Microsoft Yönetilen Masaüstü tarafından yönetilleri için var olan cihazları kaydedin
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 1d100cc3336dcb465e54f4b81d13d50ecd4bfe1e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704244"
---
# <a name="manual-registration-for-existing-devices"></a>Mevcut cihazlar için el ile kayıt

>[!NOTE]
>Bu makalede, zaten sahip olduğu cihazları yeniden kullanma ve bunları Microsoft Yönetilen Masaüstü'ne kaydetme adımları açıklanmıştır. Yepyeni cihazlarla çalışıyorsanız, Bunun yerine Microsoft Yönetilen Masaüstü'ne [yeni cihazlar kaydetme altında yer alan adımları](manual-registration.md) izleyin. <br> <br> İş Ortakları işlemi, İş Ortaklarının cihazları [kaydetme adımları ile belgelenmiştir](partner-registration.md).

Microsoft Yönetilen Masaüstü, yepyeni cihazlarla birlikte kullanılabilir veya sahip olabileceğiniz cihazları yeniden kullanabilirsiniz. Cihazları yeniden kullansanız bile, yeniden kullanımları gerekir. Cihaz kaydetme portalının Microsoft Yönetilen Masaüstü ile Microsoft Endpoint Manager.

## <a name="prepare-to-register-existing-devices"></a>Mevcut cihazları kaydetmeye hazırlanma

**Var olan cihazları kaydetmek için:**

1. [Her cihaz için donanım karması alın.](#obtain-the-hardware-hash)
2. [Karma verilerini birleştirin](#merge-hash-data).
3. [Cihazları Microsoft Yönetilen Masaüstü'ne kaydedin](#register-devices-by-using-the-admin-portal).
4. [Resmin doğru olup olmadığını bir kez daha denetleyin.](#check-the-image)
5. [Cihazı teslim edin](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Donanım karmasını alma

Microsoft Yönetilen Masaüstü her cihazı donanım karma numarasına başvurarak benzersiz olarak tanımlar. Bu bilgileri zaten kullanmakta olan cihazlardan almak için dört seçenek vardır.

**Donanım karmasını almak için:**

- Donanım karmaları da içerecek olan AutoPilot kayıt dosyasını OEM tedarikçinize sorun.
- Daha fazla bilgi [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager).
- [Active Directory](#active-directory-powershell-script-method) Windows PowerShell veya her cihaza [el](#manual-powershell-script-method) ile bir komut dosyası çalıştırın ve sonuçları bir dosyada toplayın.
- Her cihazı başlatın, ancak kurulum Windows tamamlayın ve karmaları çıkarılabilir bir [flash sürücüde toplayın](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

Microsoft Yönetilen Microsoft Endpoint Configuration Manager kaydetmek istediğiniz mevcut cihazlardan donanım karmaları toplamak üzere Microsoft Endpoint Configuration Manager'i kullanabilirsiniz. Tüm bu önkoşulları karşıdıysanız, bilgileri toplamaya hazır olursanız.

> [!IMPORTANT]
> Bu bilgileri almak istediğiniz tüm cihazlar 1703 veya Windows 10 çalıştır mutlaka.

**Donanım karma bilgilerini toplamak için:**

1. Yapılandırma Yöneticisi konsolunda İzleme'yi **seçin**.
2. İzleme çalışma alanında Raporlama düğümünü **genişletin** , **Raporlar'ı** genişletin ve Donanım **- Genel düğümünü** seçin.
3. Raporu çalıştırın, **AutoPilot Windows'i seçin** ve sonuçları görüntüden açın.
4. Rapor görüntüleyicisinde Dışarı Aktar **simgesini** seçin ve **CSV (virgülle ayrılmış) seçeneğini** belirtin.
5. Dosyayı kaydettikten sonra, sonuçları yalnızca Microsoft Yönetilen Masaüstü'ne kaydetmeyi plandığınız cihazlara göre filtrelemeniz gerekir. Ardından, verileri Microsoft Yönetilen Masaüstü'ne yükleyin.
    - Microsoft Endpoint Manager açın ve Cihazlar **menüsüne** gidin.
    - Microsoft Yönetilen Masaüstü bölümünde Cihazlar'ı **seçin**.
    - Yeni **cihazlar kaydetmek için** bir açılır pencere açan + Cihazları kaydettir'i seçin.

Daha fazla bilgi için aşağıdaki [Yönetici Portalını kullanarak cihazları kaydetme.](#register-devices-by-using-the-admin-portal)

#### <a name="active-directory-powershell-script-method"></a>Active Directory PowerShell betik yöntemi

Active Directory ortamında, `Get-WindowsAutoPilotInfo` WinRM kullanarak Active Directory Gruplarında yer alan cihazlardan uzaktan bilgi toplamak için PowerShell cmdlet'ini kullanabilirsiniz. Ayrıca, cmdlet'i `Get-AD Computer` kullanabilir ve katalogda yer alan belirli bir donanım modeli adı için filtrelenmiş sonuçlar eldeebilirsiniz. Devam etmek için, bu önkoşulları onaylayın ve sonra devam edin.

**Active Directory PowerShell betik yöntemini kullanmak için:**

1. WinRM'nin etkinleştirildiğinden emin olun.
1. Kaydetmek istediğiniz cihazlar ağ üzerinde etkindir. Başka bir ifadeyle, bunların bağlantısı kesik veya kapalı değil.
1. Cihazlarda uzaktan yürütme izni olan bir etki alanı kimlik bilgileri parametresine sahip olduğundan emin olun.
1. Güvenlik Duvarı'Windows WMI erişimine izin verili olduğundan emin olun. Bunu yapmak için aşağıdaki adımları izleyin:

    - Güvenlik Duvarı **Windows Defender panelini açın** ve Güvenlik Duvarı üzerinden **uygulamaya veya özel seçen Windows Defender seçin**.
    - Listede **Windows Yönetim Aracı'nın (WMI)** durumunu bulun, hem Özel hem de Genel için etkinleştirin **ve** ardından Tamam'ı **seçin**.
1. Yönetim haklarına sahip bir PowerShell istemi açın.
1. Şu *betiklerden* birini çalıştırın:

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

1. Cihazlar için girdiler olabileceği tüm dizinlere erişin. Etki Alanı Hizmetleri ve Etki Alanı Hizmetleri hizmetleri *dahil* tüm dizinlerden Windows Server Active Directory girdileri Azure Active Directory. Tamamen işlemesi birkaç saat sürebilir.
1. Cihazlar için girdiler olabileceği Access yönetim hizmetleri. Her cihaza ait girdileri *AutoPilot'a* Microsoft Endpoint Configuration Manager, Microsoft Intune gibi tüm Windows kaldırın. Tamamen işlemesi birkaç saat sürebilir.

Artık cihazları kaydetmeye [devam edebilirsiniz](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>El ile PowerShell betik yöntemi

**El ile Powershell betik yöntemini kullanmak için:**

1. Yönetim haklarına sahip bir PowerShell istemi açın.
2. Çalıştır `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Çalıştır `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. [Karma verilerini birleştirin.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Flash sürücü yöntemi

**Flash sürücü yöntemini kullanmak için:**

1. Kayıtlı olduğunuz cihazdan başka bir cihaza BIR USB sürücüsü yerleştirin.
2. Yönetim haklarına sahip bir PowerShell istemi açın.
3. Çalıştır `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`.
4. Kayıtlı olduğunuz cihazı açın, ancak *kurulum deneyimini başlatmayın*. Kurulum deneyimini yanlışlıkla başlatsanız, cihazı sıfırlamanız veya yeniden başlatmanız gerekir.
5. USB sürücüye bağlanın ve SHIFT + F10 tuşlarına basın.
6. Yönetim haklarına sahip bir PowerShell istemini açın ve çalıştırın `cd <pathToUsb>`.
7. Çalıştır `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.
8. Çalıştır `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
9. USB sürücüyü kaldırın ve çalıştırarak cihazı kapatın `shutdown -s -t 0`.
10. [Karma verilerini birleştirin.](#merge-hash-data)

> [!IMPORTANT]
> Kayıt işlemini tamamlayana kadar, kayıt işlemi için kayıt işlemini tamamlayana kadar tekrar kaydetmeyin.

### <a name="merge-hash-data"></a>Karma verileri birleştirme

Donanım karma verilerini el ile PowerShell veya flash sürücü yöntemleriyle topdıysanız, kayıt işlemini tamamlamak için iki CSV dosyasındaki verileri tek bir dosyada birleştirmeniz gerekir. İşte bunu kolaylaştıran örnek bir PowerShell betiği:

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

Karma veriler tek bir CSV dosyasında birleştirilmiştir, artık cihazları kaydetmeye [devam edebilirsiniz](#register-devices-by-using-the-admin-portal).

## <a name="register-devices-by-using-the-admin-portal"></a>Yönetim Portalı'ni kullanarak cihazları kaydetme

Gezinti [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) gezinti bölmesinde **Cihazlar'ı** seçin. Microsoft Yönetilen Masaüstü bölümünde Cihazlar'ı **seçin**. Microsoft Yönetilen Masaüstü Cihazları çalışma alanında, yeni cihazları **kaydetmek** için bir açılır pencere açan + Cihazları kaydettir'i seçin.

<!-- Update with new picture [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Yönetim Portalı'ni kullanarak cihazları kaydetmek için:**

1. Dosya **karşıya yükleme'de**, daha önce oluşturduğunuz CSV dosyasının yolunu yazın.
2. Açılan [menüden](../service-description/profiles.md) bir cihaz profili seçin.
3. Cihazları **kaydettir'i seçin**. Sistem, cihazları Cihazlar blade'ını bulundurarak cihaz **listenize ekler**. Cihazlar Kayıt Beklemede **olarak işaretlenir**. Kayıt işlemi normalde 10 dakikadan kısa sürer ve başarılı olduğunda cihaz kullanıcı için hazır **olarak gösterir**. **Kullanıcı için hazır** , hazır olduğu ve kullanıcının kullanmaya başlamayı beklemesi anlamına gelir.

> [!NOTE]
> Cihazın grup üyeliğini Azure Active Directory (AAD) grup üyeliğini el ile değiştirirsiniz, cihaz profili için gruba otomatik olarak yeniden atanır ve çakışan tüm gruplardan kaldırılır.

Ana sayfada cihaz kaydının ilerleme durumunu izleyebilirsiniz. Bildirilen olası eyaletler şunlardır:

| Durum | Açıklama |
| ----- | ----- |
| Kayıt Beklemede | Kayıt henüz tamamlanmamıştır. Daha sonra tekrar kontrol edin. |
| Kayıt başarısız oldu | Kayıt tamamlanamadı. Daha fazla bilgi için bkz. [Cihaz kaydı sorunlarını giderme](#troubleshooting-device-registration). |
| Kullanıcı için hazır | Kayıt başarılı oldu. Cihaz artık kullanıcıya teslim etmek için hazır. Microsoft Yönetilen Masaüstü bunları ilk kez ayarlama için yönlendirecek, bu nedenle başka hazırlıklar yapmaya gerek yoktur. |
| Etkin | Cihaz kullanıcıya teslim edildi ve kiracınıza kayıtlı. Ayrıca bu durum, cihazı düzenli olarak kullanmakta olduklarını da gösterir. |
| Etkin değil | Cihaz kullanıcıya teslim edildi ve kiracınıza kayıtlı. Bununla birlikte, kullanıcı cihazı yakın zamanda (son yedi gün içinde) kullanmmiştir. |

### <a name="troubleshooting-device-registration"></a>Cihaz kaydı sorunlarını giderme

| Hata iletisi | Ayrıntılar |
| ----- | ----- |
| Cihaz bulunamadı | Sağlanan üretici, model veya seri numarası ile eşleşme bulamadımız için bu cihazı kaydettiremedik. Bu değerleri cihaz tedarikçiniz ile onaylayın. |
| Donanım karması geçerli değil | Bu cihaz için sağladığınız donanım karması doğru biçimlendiri yoktu. Donanım karmsını bir kez daha kontrol edin ve yeniden yayın. |
| Cihaz zaten kayıtlı | Bu cihaz zaten organizasyona kaydedilmiştir. Başka işlem gerekmez. |
| Başka bir kuruluş tarafından talep edildi cihaz | Bu cihaz başka bir kuruluş tarafından zaten iddia edildi. Cihaz sağlayıcınızı kontrol edin. |
| Beklenmeyen hata | İsteğiniz otomatik olarak işlenemez. Destek ile iletişime geçin ve İstek Kimliği'ne ulaşın: `<requestId>` |

## <a name="check-the-image"></a>Resmi kontrol edin

Cihazınız bir Microsoft Yönetilen Masaüstü iş ortağı sağlayıcıdan geliyorsa, resmin doğru olması gerekir.

Tercih ederseniz, resmi kendi başına da uygulayabilirsiniz. Çalışmaya başlamanız için, üzerinde çalışmakta olduğunuz Microsoft temsilcisine başvurun. Resmi uygulamaya başlamanız için size konum ve adımlar sağlayacaktır.

## <a name="deliver-the-device"></a>Cihazı teslim edin

> [!IMPORTANT]
> Cihazı kullanıcınıza teslim etmek için önce, bu kullanıcıya uygun lisansları [edindirin ve](../get-ready/prerequisites.md) uyguladınız.

Tüm lisanslar uygulanırsa, [kullanıcılarınızı cihazları kullanmaya hazır hale çıkarabilirsiniz](get-started-devices.md). Ardından, kullanıcınız cihazı başlatarak ilk kurulum Windows devam edebilirsiniz.
