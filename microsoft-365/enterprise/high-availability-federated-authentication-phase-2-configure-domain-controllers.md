---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması 2. Aşama Etki alanı denetleyicilerini yapılandırma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "Özet: Microsoft Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamanız için etki alanı denetleyicilerini ve dizin eşitleme sunucusunu yapılandırın."
ms.openlocfilehash: 765ccb0aaf2611947f505b53b5689009dadd5148
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940700"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması 2. Aşama: Etki alanı denetleyicilerini yapılandırma

Azure altyapı hizmetlerinde Microsoft 365 federasyon kimlik doğrulaması için yüksek kullanılabilirlik dağıtmanın bu aşamasında, Azure sanal ağında iki etki alanı denetleyicisini ve dizin eşitleme sunucusunu yapılandıracaksınız. Daha sonra kimlik doğrulaması için istemci web istekleri, bu kimlik doğrulama trafiğini siteden siteye VPN bağlantısı üzerinden şirket içi ağınıza göndermek yerine Azure sanal ağında doğrulanabilir.
  
> [!NOTE]
> Active Directory Federasyon Hizmetleri (AD FS), Active Directory Etki Alanı Hizmetleri (AD DS) etki alanı denetleyicilerinin yerine Azure Active Directory (Azure AD) kullanamaz. 
  
[3. Aşama: AD FS sunucularını yapılandırma](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) aşamasına geçmeden önce bu aşamayı tamamlamanız gerekir. Tüm aşamalar için bkz. [Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) .
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Azure'da etki alanı denetleyicisi sanal makinelerini oluşturma

İlk olarak, Tablo M'nin **Sanal makine adı** sütununu doldurmanız ve **Minimum boyut** sütununda gerektiğinde sanal makine boyutlarını değiştirmeniz gerekir.
  
|**Öğe**|**Sanal makine adı**|**Galeri resmi**|**Depolama türü**|**En küçük boyut**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ilk etki alanı denetleyicisi, örnek DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ikinci etki alanı denetleyicisi, örnek DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (dizin eşitleme sunucusu, örnek DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ilk AD FS sunucusu, örneğin ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ikinci AD FS sunucusu, örnek ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ilk web uygulaması ara sunucusu, örneğin WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![Satır.](../media/Common-Images/TableLine.png) (ikinci web uygulaması ara sunucusu, örneğin WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tablo M - Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulaması için sanal makineler**
  
Sanal makine boyutlarının tam listesi için bkz. [Sanal makineler için boyutlar](/azure/virtual-machines/sizes).
  
Aşağıdaki Azure PowerShell komut bloğu, iki etki alanı denetleyicisi için sanal makineleri oluşturur. Karakterleri kaldırarak değişkenlerin \< and > değerlerini belirtin. Bu Azure PowerShell komut bloğunun aşağıdaki tablolardaki değerleri kullandığını unutmayın:
  
- Sanal makineleriniz için Tablo M
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağlarınız için Tablo S
    
- Statik IP adresleriniz için Tablo I
    
- Kullanılabilirlik kümeleriniz için Tablo A
    
[1. Aşama: Azure'ı yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md) bölümünde R, V, S, I ve A tablolarını tanımlamış olduğunuzu hatırlayın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell'in en son sürümünü kullanır. Bkz. [Azure PowerShell'i kullanmaya başlama](/powershell/azure/get-started-azureps). 
  
Tüm doğru değerleri sağladığınızda, elde edilen bloğu Azure PowerShell isteminde veya yerel bilgisayarınızdaki PowerShell Tümleşik Betik Ortamı'nda (ISE) çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza göre çalışmaya hazır PowerShell komut blokları oluşturmak için bu [Microsoft Excel yapılandırma çalışma kitabını](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) kullanın. 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Bu sanal makineler bir intranet uygulamasına ait olduğundan, bunlara bir genel IP adresi veya DNS etki alanı adı etiketi atanıp İnternet'e sunulmaz. Ancak bu, azure portalından bunlara bağlanamayacağınız anlamına da gelir. Sanal makinenin özelliklerini görüntülediğinizde **Bağlan** seçeneği kullanılamaz. Özel IP adresini veya intranet DNS adını kullanarak sanal makineye bağlanmak için Uzak Masaüstü Bağlantısı aksesuarını veya başka bir Uzak Masaüstü aracını kullanın.
  
## <a name="configure-the-first-domain-controller"></a>İlk etki alanı denetleyicisini yapılandırma

Seçtiğiniz uzak masaüstü istemcisini kullanın ve ilk etki alanı denetleyicisi sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, ilk etki alanı denetleyicisi sanal makinesindeki bir Windows PowerShell komut isteminden bu komutla **ek veri diskini ilk etki alanı denetleyicisine** ekleyin:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, kuruluş ağınızdaki kaynakların adlarına ve IP adreslerine ping göndermek için **ping** komutunu kullanarak ilk etki alanı denetleyicisinin kuruluş ağınızdaki konumlara bağlantısını test edin.
  
Bu yordam, DNS ad çözümlemesinin düzgün çalışmasını (sanal makinenin şirket içi DNS sunucularıyla doğru şekilde yapılandırılmasını) ve paketlerin şirket içi sanal ağa gönderilip gönderilebilmesini sağlar. Bu temel test başarısız olursa, DNS ad çözümlemesi ve paket teslim sorunlarını gidermek için BT departmanınıza başvurun.
  
Ardından, ilk etki alanı denetleyicisindeki Windows PowerShell komut isteminden aşağıdaki komutları çalıştırın:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Bir etki alanı yönetici hesabının kimlik bilgilerini sağlamanız istenir. Bilgisayar yeniden başlatılır.
  
## <a name="configure-the-second-domain-controller"></a>İkinci etki alanı denetleyicisini yapılandırma

seçtiğiniz uzak masaüstü istemcisini kullanın ve ikinci etki alanı denetleyicisi sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, ikinci etki alanı denetleyicisi sanal makinesindeki bir Windows PowerShell komut isteminden bu komutla **ikinci etki alanı denetleyicisine** ek veri diski eklemeniz gerekir:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından aşağıdaki komutları çalıştırın:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

Bir etki alanı yönetici hesabının kimlik bilgilerini sağlamanız istenir. Bilgisayar yeniden başlatılır.
  
Ardından, Azure'ın sanal makinelere DNS sunucuları olarak kullanmak üzere iki yeni etki alanı denetleyicisinin IP adreslerini ataması için sanal ağınızın DNS sunucularını güncelleştirmeniz gerekir. Değişkenleri doldurun ve ardından yerel bilgisayarınızdaki bir Windows PowerShell komut isteminden şu komutları çalıştırın:
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

İki etki alanı denetleyicisini, şirket içi DNS sunucularıyla DNS sunucuları olarak yapılandırılmamaları için yeniden başlatacağımıza dikkat edin. Her ikisi de DNS sunucuları olduğundan, etki alanı denetleyicilerine yükseltildiklerinde şirket içi DNS sunucularıyla DNS ileticileri olarak otomatik olarak yapılandırıldılar.
  
Ardından, Azure sanal ağındaki sunucuların yerel etki alanı denetleyicilerini kullandığından emin olmak için bir Active Directory çoğaltma sitesi oluşturmamız gerekir. Bir etki alanı yöneticisi hesabıyla etki alanı denetleyicisine bağlanın ve yönetici düzeyinde bir Windows PowerShell isteminden aşağıdaki komutları çalıştırın:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Dizin eşitleme sunucusunu yapılandırma

Seçtiğiniz uzak masaüstü istemcisini kullanın ve dizin eşitleme sunucusu sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, Windows PowerShell isteminde bu komutlarla uygun AD DS etki alanına ekleyin.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Yer tutucu bilgisayar adlarıyla bu aşamanın başarıyla tamamlanmasından kaynaklanan yapılandırma aşağıdadır.
  
**2. Aşama: Azure'da yüksek kullanılabilirlik federasyon kimlik doğrulama altyapınız için etki alanı denetleyicileri ve dizin eşitleme sunucusu**

![Azure'da etki alanı denetleyicileriyle yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulama altyapısının 2. aşaması.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Sonraki adım

3. Aşama: Bu iş yükünü yapılandırmaya devam etmek için [AD FS sunucularını](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) yapılandırın.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)