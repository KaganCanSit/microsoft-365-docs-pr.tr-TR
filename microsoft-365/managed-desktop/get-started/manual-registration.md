---
title: El ile kayıt
description: Cihazları Microsoft Yönetilen Masaüstü tarafından yönetilmiyor olarak kaydetme
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
ms.openlocfilehash: aaa1446cbb1ffdc20b023f568a7fd41d6cf01848
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704962"
---
# <a name="manual-registration"></a>El ile kayıt

Microsoft Yönetilen Masaüstü, yepyeni cihazlarla birlikte kullanılabilir veya sahip olabileceğiniz cihazları yeniden kullanabilirsiniz. Cihazları yeniden kullansanız bile, yeniden kullanımları gerekir. Cihaz kaydetme portalının Microsoft Yönetilen Masaüstü ile Microsoft Endpoint Manager.

> [!NOTE]
> Cihaz almak için bir iş ortağıyla mı çalışıyorsunuz? Bu durum geçerli bir durumsa donanım karmaları almakla ilgili endişelenmenize gerek yok; sizin için bunu hallederler. İş Ortağı Merkezi'nde iş ortağınız ile bir ilişki kurduğundan [emin olun](https://partner.microsoft.com/dashboard). İş ortağınız İş Ortağı Merkezi yardımı'nda [daha fazla bilgi edin olabilir](/partner-center/request-a-relationship-with-a-customer). <br><br>Bu ilişki kurulduktan sonra, iş ortağınız cihazları sizin adına kaydedecek; başka işlem yapmanız gerekmez. Ayrıntıları görmek istediğiniz veya iş ortağınız ile ilgili sorular varsa, bkz. İş [ortağı kaydı](partner-registration.md). Cihazlar kaydedildiktan sonra, resmi kontrol etmeye [ve cihazları kullanıcılarınıza](#check-the-image) [teslim etmeye](#deliver-the-device) devam edebilirsiniz.

## <a name="prepare-to-register-brand-new-devices"></a>Yepyeni cihazlar için kaydolmaya hazırlanma

Yeni cihazlarınız olduktan sonra şu adımları izleyin:

1. [Her cihaz için donanım karması alın.](#obtain-the-hardware-hash)
2. [Karma verilerini birleştirin](#merge-hash-data).
3. [Cihazları Microsoft Yönetilen Masaüstü'ne kaydedin](#register-devices-by-using-the-admin-portal).
4. [Resmin doğru olup olmadığını bir kez daha denetleyin.](#check-the-image)
5. [Cihazı teslim edin](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Donanım karmasını alma

Microsoft Yönetilen Masaüstü her cihazı donanım karma numarasına başvurarak benzersiz olarak tanımlar. Bu bilgileri almak için üç seçenek vardır.

**Donanım karmasını almak için:**

- Donanım karmaları da içerecek olan AutoPilot kayıt dosyasını OEM tedarikçinize sorun.
- Her Windows PowerShell [bir komut](#powershell-script-method) dosyası çalıştırın ve sonuçları bir dosyada toplayın.
- Her cihazı başlatın, ancak kurulum Windows tamamlayın ve karmaları çıkarılabilir bir [flash sürücüde toplayın](#flash-drive-method).

#### <a name="powershell-script-method"></a>PowerShell betik yöntemi

[ PowerShell Galerisi webGet-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) sitesindeGet-WindowsAutoPilotInfo.ps1PowerShell betiği kullanabilirsiniz. Cihaz kimliği ve donanım karması hakkında daha fazla bilgi için bkz[. AutoPilot'a cihaz Windows.](/mem/autopilot/add-devices#device-identification)

**Powershell betik yöntemini kullanmak için:**

1. Yönetim haklarına sahip bir PowerShell istemi açın.
2. Çalıştır `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Çalıştır `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. Sonraki `powershell -ExecutionPolicy restricted` kısıtlanmamış betiklerin çalıştırmasını önlemek için çalıştırın.

#### <a name="flash-drive-method"></a>Flash sürücü yöntemi

**Flash sürücü yöntemini kullanmak için:**

1. Kayıtlı olduğunuz cihazdan başka bir cihaza BIR USB sürücüsü yerleştirin.
2. Yönetim haklarına sahip bir PowerShell istemi açın.
3. Çalıştır `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Kayıtlı olduğunuz cihazı açın, ancak *kurulum deneyimini başlatmayın*. Kurulum deneyimini yanlışlıkla başlatsanız, cihazı sıfırlamanız veya yeniden başlatmanız gerekir.
5. USB sürücüye bağlanın ve SHIFT + F10 tuşlarına basın.
6. Yönetim haklarına sahip bir PowerShell istemini açın ve çalıştırın `cd <pathToUsb>`.
7. Çalıştır `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Çalıştır `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. USB sürücüyü kaldırın ve ardından çalıştırarak cihazı kapatın `shutdown -s -t 0`

> [!IMPORTANT]
> Kayıt işlemini tamamlayana kadar, kayıt işlemi için kayıt işlemini tamamlayana kadar tekrar kaydetmeyin.

### <a name="merge-hash-data"></a>Karma verileri birleştirme

Kayıt işlemini tamamlamak için CSV dosyalarında yer alan verilerin tek bir dosyada birleştirilmiş olarak yer almaları gerekir. İşte bunu kolaylaştıran örnek bir PowerShell betiği:

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

> [!NOTE]
> Ek sütunlar desteklenmiyor. Teklifler desteklenmiyor. Yalnızca ANSI biçimindeki metin dosyaları kullanılabilir (Unicode değil). Üst bilgiler büyük/harfe duyarlıdır. Bu gereksinimler nedeniyle Excel dosyanın CSV dosyası olarak düzenlenmesi kullanılabilir bir dosya oluşturmaz. Cihaz seri numarasında baştaki sıfırları korumayı sağlar.

### <a name="register-devices-by-using-the-admin-portal"></a>Yönetim Portalı'ni kullanarak cihazları kaydetme

Gezinti [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) gezinti bölmesinde **Cihazlar'ı** seçin. Microsoft Yönetilen Masaüstü bölümünde Cihazlar'ı **seçin**. Microsoft Yönetilen Masaüstü Cihazları çalışma alanında, yeni cihazları **kaydetmek** için bir açılır pencere açan + Cihazları kaydettir'i seçin.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Yönetim Portalı'ni kullanarak cihazları kaydetmek için:**

1. Dosya **karşıya yükleme'de**, daha önce oluşturduğunuz CSV dosyasının yolunu yazın.
2. Açılan [menüden](../service-description/profiles.md) bir cihaz profili seçin.
3. Cihazları **kaydettir'i seçin**. Sistem cihazları, Kayıt Beklemede olarak işaretlenmiş **Cihazlar** **listenize ekler**. Kayıt işlemi normalde 10 dakikadan kısa sürer ve cihaz başarılı bir şekilde Kullanıcı için hazır olarak gösterir; bu, hazır olduğu ve kullanıcının kullanmaya başlamayı beklemesi anlamına gelir.

> [!NOTE]
> Cihazın grup üyeliğini Azure Active Directory (AAD) grup üyeliğini el ile değiştirirsiniz, cihaz profili için gruba otomatik olarak yeniden atanır ve çakışan tüm gruplardan kaldırılır.

Ana sayfada cihaz kaydının ilerleme durumunu izleyebilirsiniz. Bildirilen olası eyaletler şunlardır:

| Durum | Açıklama |
| -----|-----|
| Kayıt Beklemede | Kayıt henüz tamamlanmamıştır. Daha sonra tekrar kontrol edin. |
| Kayıt başarısız oldu | Kayıt tamamlanamadı. Daha fazla bilgi için bkz. [Cihaz kaydı sorunlarını giderme](#troubleshooting-device-registration). |
| Kullanıcı için hazır | Kayıt başarılı oldu. Cihaz artık kullanıcıya teslim etmek için hazır. Microsoft Yönetilen Masaüstü bunları ilk kez ayarlama için yönlendirecek, bu nedenle başka hazırlıklar yapmaya gerek yoktur. |
| Etkin | Cihaz kullanıcıya teslim edildi ve kiracınıza kayıtlı. Ayrıca bu durum, cihazı düzenli olarak kullanmakta olduklarını da gösterir. |
| Etkin değil | Cihaz kullanıcıya teslim edildi ve kiracınıza kayıtlı. Bununla birlikte, cihazı yakın zamanda (son yedi gün içinde) hiç kullanılmadı.  |

#### <a name="troubleshooting-device-registration"></a>Cihaz kaydı sorunlarını giderme

| Hata iletisi | Ayrıntılar |
|-----| ----- |
| Cihaz bulunamadı | Sağlanan üretici, model veya seri numarası ile eşleşme bulamadımız için bu cihazı kaydettiremedik. Bu değerleri cihaz tedarikçiniz ile onaylayın. |
| Donanım karması geçerli değil | Bu cihaz için sağladığınız donanım karması doğru biçimlendiri yoktu. Donanım karmsını bir kez daha kontrol edin ve yeniden yayın. |
| Cihaz zaten kayıtlı | Bu cihaz zaten organizasyona kaydedilmiştir. Başka işlem gerekmez. |
| Başka bir kuruluş tarafından talep edildi cihaz | Bu cihaz başka bir kuruluş tarafından zaten iddia edildi. Cihaz sağlayıcınızı kontrol edin. |
| Beklenmeyen hata | İsteğiniz otomatik olarak işlenemez. Destek ile iletişime geçin ve İstek Kimliği'ne ulaşın: `<requestId>` |

### <a name="check-the-image"></a>Resmi kontrol edin

Cihazınız bir Microsoft Yönetilen Masaüstü iş ortağı sağlayıcıdan geliyorsa, resmin doğru olması gerekir.

Tercih ederseniz, resmi kendi başına da uygulayabilirsiniz. Çalışmaya başlamanız için, birlikte çalışmakta olduğunuz Microsoft temsilcisine başvurun. Temsilci resmi uygulama konumunu ve adımlarını size sağlayacaktır.

### <a name="autopilot-group-tag"></a>AutoPilot grup etiketi

Cihazları kaydetmek için Yönetici portalını kullanırken, İş Ortağı Merkezi'ni kullanarak cihazları kaydetme altında listelenen cihaz profiliyle ilişkili AutoPilot Grup Etiketini [otomatik olarak atarız](partner-registration.md).
Hizmet, tüm Microsoft Yönetilen Masaüstü cihazlarını günlük olarak izler ve grup etiketini henüz sahip olmadığınız cihazlara atar.

### <a name="deliver-the-device"></a>Cihazı teslim edin

> [!IMPORTANT]
> Cihazı kullanıcınıza teslim etmek için önce, bu kullanıcıya uygun lisansları [edindirin ve](../get-ready/prerequisites.md) uyguladınız.

Tüm lisanslar uygulanırsa kullanıcılarınızı [cihazları kullanmaya hazır hale çıkarabilirsiniz](get-started-devices.md). Ardından, kullanıcınız cihazı başlatarak ilk kurulum Windows devam edebilirsiniz.
