---
title: Temel Hareketlilik ve Güvenlik ile yönetilen cihazlar hakkında ayrıntılı bilgi edinebilirsiniz
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Windows PowerShell Temel Mobil Kullanım ve Güvenlik cihazları hakkında ayrıntılı bilgi almak için Mobil Kullanım ve Güvenlik cihazlarını kullanın.
ms.openlocfilehash: 25c7f89dda32121306bfe2434620d17396f2e870
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973705"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Temel Hareketlilik ve Güvenlik ile yönetilen cihazlar hakkında ayrıntılı bilgi edinebilirsiniz

Bu makalede, temel mobil Windows PowerShell ve güvenlik için ayar takımınız hakkında ayrıntılı bilgi almak üzere Windows PowerShell'i nasıl kullanabileceğiniz gösterir.

Burada, size mevcut cihaz ayrıntılarının dökümünü ve ve bir çözümlemeyi ve sonra da 365'i 15.

|**Ayrıntı**|**PowerShell'de nelere bakın?**|
|:----------------|:------------------------------------------------------------------------------|
|Cihaz Temel Hareketlilik ve Güvenlik'e kayıtlıdır. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md)| *theisManagedparameter*  değeri:<br/>**True**= cihaz kaydedildi.<br/>**False**= cihaz kayıtlı değil. |
|Cihaz, cihaz güvenlik ilkeleriniz ile uyumludur. Daha fazla bilgi için bkz [. Cihaz güvenliği ilkeleri oluşturma](create-device-security-policies.md)| *theisCompliantparameter*  değeri:<br/>**True**  = cihaz ilkelerle uyumludur.<br/>**False**  = cihaz ilkelerle uyumlu değildir.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Temel Mobil Kullanım ve Güvenlik PowerShell parametreleri.":::

> [!NOTE]
> Bu makaledeki komutlar ve betikler, aşağıdakiler tarafından yönetilen cihazlarla  [ilgili Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Başlamadan önce

Bu makalede açıklanan komutları ve betikleri çalıştırmak için birkaç şeyi ayarlamak gerekir.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>1. Adım: Kurulum için Azure Active Directory Modülü'Windows PowerShell

Bu adımlarla ilgili daha fazla bilgi için  [bkz. Bağlan PowerShell Microsoft 365 e tıklayın](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. BT Uzmanları  [için Microsoft Online Services Sign-In Yardımcısı RTWlve'i](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi)  seçin ve Microsoft Online Services Oturum Açma Yardımcısı için  **İndir'i seçin**.

2. Aşağıdaki adımları Microsoft Azure Active Directory için Windows PowerShell Modülü'ne yükleyin:

    1. Yönetici düzeyinde bir PowerShell komut istemini açın.

    2. `Install-Module MSOnline` Komutu çalıştırın.

    3. Bilgisayar sağlayıcısının yüklemeniz istenirse NuGet Y yazın ve ENTER tuşuna basın.

    4. PsGallery'den modülü yüklemeniz istenirse, Y yazın ve ENTER tuşuna basın.

    5. Yükleme sonrasında, PowerShell komut penceresini kapatın.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>2. Adım: Bağlan aboneliğinize Microsoft 365 adım

1. Windows Azure Active Directory için Modülde Windows PowerShell, aşağıdaki komutu çalıştırın.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. Genel Windows PowerShell Yönetici hesabınız için kullanıcı adını ve parolayı yazın Microsoft 365 Tamam'ı **seçin**.

3. Aşağıdaki komutu çalıştırın.

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>3. Adım: PowerShell betiklerini çalıştırama

> [!NOTE]
> PowerShell betiklerini çalıştıracak şekilde önceden ayarlanmışsanız bu adımı atlayabilirsiniz.

Bu komut Get-MsolUserDeviceComplianceStatus.ps1 çalıştırmak için, PowerShell betiklerini çalıştırmayı etkinleştirmeniz gerekir.

1. Windows MasaüstünüzdenBaşlat'ı seçin **** ve başlat yazın Windows PowerShell. Sağ tıklayın ve Windows PowerShell Yönetici olarak  **çalıştır'ı seçin**.

2. Aşağıdaki komutu çalıştırın.

   ```powershell
   Set-ExecutionPolicy  RemoteSigned
   ```

3. Sorulsa, Y yazın ve Enter tuşuna basın.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Get-MsolDevice tüm cihazların ayrıntılarını görüntülemek için Get-MsolDevice cmdlet'ini çalıştırın.

1. Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell.

2. Aşağıdaki komutu çalıştırın.

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Daha fazla örnek için bkz  [. Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>Cihaz ayrıntılarını almak için betik çalıştırma

İlk olarak, betiği bilgisayarınıza kaydedin.

1. Aşağıdaki metni kopyalayıp bu belgeye Not Defteri.

   ```powershell
   param (
   [PSObject[]]$users = @(),
   [Switch]$export,
   [String]$exportFileName = "UserDeviceComplianceStatus_" + (Get-Date -Format "yyMMdd_HHMMss") + ".csv",
   [String]$exportPath = [Environment]::GetFolderPath("Desktop")
   )
   [System.Collections.IDictionary]$script:schema = @{
   DeviceId = ''
   DeviceOSType = ''
   DeviceOSVersion = ''
   DeviceTrustLevel = ''
   DisplayName = ''
   IsCompliant = ''
   IsManaged = ''
   ApproximateLastLogonTimestamp = ''
   DeviceObjectId = ''
   RegisteredOwnerUpn = ''
   RegisteredOwnerObjectId = ''
   RegisteredOwnerDisplayName = ''
   }
   function createResultObject
   {
   [PSObject]$resultObject = New-Object -TypeName PSObject -Property $script:schema
   return $resultObject
   }
   If ($users.Count -eq 0)
   {
   $users = Get-MsolUser
   }
   [PSObject[]]$result = foreach ($u in $users)
   {
   [PSObject]$devices = get-msoldevice -RegisteredOwnerUpn $u.UserPrincipalName
   foreach ($d in $devices)
   {
   [PSObject]$deviceResult = createResultObject
   $deviceResult.DeviceId = $d.DeviceId
   $deviceResult.DeviceOSType = $d.DeviceOSType
   $deviceResult.DeviceOSVersion = $d.DeviceOSVersion
   $deviceResult.DeviceTrustLevel = $d.DeviceTrustLevel
   $deviceResult.DisplayName = $d.DisplayName
   $deviceResult.IsCompliant = $d.GraphDeviceObject.IsCompliant
   $deviceResult.IsManaged = $d.GraphDeviceObject.IsManaged
   $deviceResult.DeviceObjectId = $d.ObjectId
   $deviceResult.RegisteredOwnerUpn = $u.UserPrincipalName
   $deviceResult.RegisteredOwnerObjectId = $u.ObjectId
   $deviceResult.RegisteredOwnerDisplayName = $u.DisplayName
   $deviceResult.ApproximateLastLogonTimestamp = $d.ApproximateLastLogonTimestamp
   $deviceResult
   }
   }
   If ($export)
   {
   $result | Export-Csv -path ($exportPath + "\" + $exportFileName) -NoTypeInformation
   }
   Else
   {
   $result
   }
   ```

2. Bu dosyayı, Windows PowerShell uzantısını kullanarak bir betik dosyası olarak .ps1; örneğin, Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Tek bir kullanıcı hesabının cihaz bilgilerini almak için betiği çalıştırın

1. Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell.

2. Betiği kaydeden klasöre gidin. Örneğin, bunu C:\PS-Scripts klasörüne kaydettiysiniz, aşağıdaki komutu çalıştırın.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Cihaz ayrıntılarını almak istediğiniz kullanıcıyı tanımlamak için aşağıdaki komutu çalıştırın. Bu örnekte, iş ayrıntıları bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Betiği başlatmak için aşağıdaki komutu çalıştırın.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Bilgiler, Windows Masaüstünüze CSV dosyası olarak dışarı aktarıldı. CSV'nin dosya adını ve yolunu belirtmek için ek parametreler kullanabilirsiniz.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Bir grup kullanıcının cihaz bilgilerini almak için betiği çalıştırın

1. Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell.

2. Betiği kaydeden klasöre gidin. Örneğin, bunu C:\PS-Scripts klasörüne kaydettiysiniz, aşağıdaki komutu çalıştırın.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Cihaz ayrıntılarını almak istediğiniz grubu tanımlamak için aşağıdaki komutu çalıştırın. Bu örnekte, FinanceStaff grubunda yer alan kullanıcılar için ayrıntılar yer alır.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Betiği başlatmak için aşağıdaki komutu çalıştırın.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Bilgiler, Windows Masaüstünüze CSV dosyası olarak dışarı aktarıldı. CSV'nin dosya adını ve yolunu belirtmek için ek parametreler kullanabilirsiniz.

## <a name="related-topics"></a>İlgili konular

[Microsoft Bağlan Kullanımı Geri Bırakıldı](/collaborate/connect-redirect)

[Temel Hareketlilik ve Güvenlik'e Genel Bakış](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
