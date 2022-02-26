---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 2 Etki alanı denetleyicileri yapılandırma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Aynı sunucuda yer alan yüksek kullanılabilirlik federasyon kimlik doğrulaması için etki alanı denetleyicileri ve dizin Microsoft 365 sunucusunu Microsoft Azure.'
ms.openlocfilehash: 82199d6782e9c2497214d501da9e27ac0956edcd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973727"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 2: Etki alanı denetleyicilerini yapılandırma

Azure altyapı hizmetlerde şirket dışı kimlik doğrulaması için Microsoft 365 dağıtımın bu aşamasında, iki etki alanı denetleyicisini ve Azure sanal ağın dizin eşitleme sunucusunu yapılandırabilirsiniz. Bundan sonra, istemci web istekleri, bu kimlik doğrulama trafiğini şirket içi ağınıza siteden VPN bağlantısı üzerinden göndermek yerine Azure sanal ağın kimliği doğrulanabilir.
  
> [!NOTE]
> Active Directory Federasyon Hizmetleri (AD FS), Active Directory Azure Active Directory Hizmetleri (AD DS) etki alanı denetleyicilerinin yerine başka bir ad (Azure AD) kullanamaz. 
  
Aşama [3: AD FS sunucularını yapılandırma aşamasına başlamadan önce bu aşamayı tamamlamanız gerekir](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Tüm [aşamalar için Bkz. Azure'da Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) için yüksek kullanılabilirlik federal kimlik doğrulamasını dağıtma.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Azure'da etki alanı denetleyicisi sanal makinelerini oluşturma

İlk olarak, Tablo M'nin **Sanal makine adı** sütununu doldurmanız ve Sanal makine boyutlarını Minimum boyut sütununda gerektiğinde **değiştirmeniz** gerekir.
  
|**Öğe**|**Sanal makine adı**|**Galeri resmi**|**Depolama türü**|**Minimum boyut**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ilk etki alanı denetleyicisi, örnek DC1)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ikinci etki alanı denetleyicisi, örnek DC2)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (dizin eşitleme sunucusu, örnek DS1)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ilk AD FS sunucusu, örnek ADFS1)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ikinci AD FS sunucusu, örnek ADFS2)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ilk web uygulaması ara sunucusu, örnek WEB1)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) (ikinci web uygulaması ara sunucusu, örnek WEB2)  <br/> |Windows Server 2016 Center  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tablo M - Azure'daki iş yerizleri için yüksek kullanılabilirlik Microsoft 365 sanal makineler**
  
Sanal makine boyutlarının tam listesi için bkz. [Sanal makine boyutları](/azure/virtual-machines/virtual-machines-windows-sizes).
  
Aşağıdaki Azure PowerShell komutu bloğu, iki etki alanı denetleyicisi için sanal makineler oluşturur. Karakterleri kaldırarak değişkenler için değerleri \< and > belirtin. Bu komut Azure PowerShell aşağıdaki tablolarda yer alan değerleri kullanır:
  
- Sanal makineleriniz için M Tablosu
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağların için S Tablosu
    
- Tablo I, statik IP adresleriniz için
    
- Kullanılabilirlik kümeniz için A Tablosu
    
Aşama 1'de R, V, S, I ve A Tablolarını tanımla [evre: Azure'i yapılandırın](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Aşağıdaki komut kümeleri, dosyanın en son sürümünü Azure PowerShell. Bkz[. Yeni e-Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Tüm doğru değerleri sağladığınız zaman, sonuç bloğuyu yerel bilgisayarınızdaki Azure PowerShell Komut İstemi'nde veya PowerShell Tümleşik Betik Ortamı'nda (ISE) çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza bağlı olarak hazır çalıştırlı PowerShell komut blokları oluşturmak için bu Microsoft Excel [kullanın](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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
> Bu sanal makineler bir intranet uygulamasına yönelik olduğundan, onlara bir genel IP adresi veya DNS etki alanı adı etiketi atanmaz ve İnternet'e açık olur. Ancak bu, onlara Azure portaldan bağlanamazsınız anlamına da gelir. Bu **Bağlan**, sanal makinenin özelliklerini görüntüle görüntüde kullanılamaz. Sanal makineye özel IP adresini veya intranet DNS adını kullanarak bağlanmak için Uzak Masaüstü Bağlantısı donatısını veya başka bir Uzak Masaüstü aracını kullanın.
  
## <a name="configure-the-first-domain-controller"></a>İlk etki alanı denetleyicisini yapılandırma

Tercihiniz uzak masaüstü istemcisini kullanın ve ilk etki alanı denetleyicisi sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, ilk etki alanı denetleyicisi sanal makinesine gelen bir Windows PowerShell komut isteminde bu komutu kullanarak ek veri diskini ilk etki **alanı denetleyicisine ekleyin**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, kuruluş ağınız içinde yer alan kaynakların ip adreslerine ping yapmak için **ping** komutunu kullanarak ilk etki alanı denetleyicisinin kuruluş ağınıza olan konumlarla bağlantısını test edin.
  
Bu yordam, DNS ad çözümlemenin doğru (sanal makine şirket içi DNS sunucularında doğru yapılandırıldığından) ve paketlerin şirket içi sanal ağa ve bu ağdan gönderileceğini sağlar. Bu temel sınama başarısız olursa, DNS ad çözümlemesi ve paket teslim sorunlarını gidermek için IT departmanınıza ulaşın.
  
Ardından, ilk Windows PowerShell denetleyicisinin Komut İstemi'ne aşağıdaki komutları çalıştırın:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Etki alanı yöneticisi hesabının kimlik bilgilerini girmeniz istenir. Bilgisayar yeniden başlatılır.
  
## <a name="configure-the-second-domain-controller"></a>İkinci etki alanı denetleyicisini yapılandırma

Tercihiniz uzak masaüstü istemcisini kullanın ve ikinci etki alanı denetleyicisi sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, ikinci etki alanı denetleyicisi sanal makinesine gelen bir Windows PowerShell komut isteminden bu komutu kullanarak ek veri diskini ikinci etki **alanı denetleyicisine eklemeniz gerekir**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, aşağıdaki komutları çalıştırın:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

Etki alanı yöneticisi hesabının kimlik bilgilerini girmeniz istenir. Bilgisayar yeniden başlatılır.
  
Ardından, Azure'ın DNS sunucuları olarak kullanmak üzere iki yeni etki alanı denetleyicisinin IP adreslerini sanal makinelere ataması için sanal ağınız için DNS sunucularını güncelleştirmeniz gerekir. Değişkenleri doldurun ve yerel bilgisayarınızda bir Windows PowerShell komutu isteminden bu komutları çalıştırın:
  
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

Şirket içi DNS sunucularında DNS sunucuları olarak yapılandırılmamaları için iki etki alanı denetleyicisini yeniden başlattık. Her iki DNS sunucusu da olduğundan, etki alanı denetleyicilerine yükseltilirken otomatik olarak şirket içi DNS sunucularıyla DNS ileticileri olarak yapılandırılırlar.
  
Ardından, Azure sanal ağı'daki sunucuların yerel etki alanı denetleyicilerinde olduğundan emin olmak için bir Active Directory çoğaltma sitesi oluşturmamız gerekir. Bağlan alanı yöneticisi hesabı olan bir etki alanı denetleyicisine başvurun ve yönetici düzeyindeki bir kullanıcı isteminden aşağıdaki Windows PowerShell çalıştırın:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Dizin eşitleme sunucusunu yapılandırma

Tercihiniz uzak masaüstü istemcisini kullanın ve dizin eşitleme sunucusu sanal makinesine bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Ardından, Komut isteminde bu komutları kullanarak uygun AD DS etki Windows PowerShell katılın.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Bu aşamanın başarıyla tamamlanmasından sonra, yer tutucu bilgisayar adlarla elde edilen yapılandırma şu şekildedir.
  
**Aşama 2: Azure'da yüksek kullanılabilirlik federal kimlik doğrulama altyapınız için etki alanı denetleyicileri ve dizin eşitleme sunucusu**

![Etki alanı denetleyicileriyle Azure'daki federasyon Microsoft 365 için yüksek kullanılabilirlik aşaması 2. aşama.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Sonraki adım

Aşama [3: Bu iş yükünü yapılandırmaya devam etmek için AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) sunucularını yapılandırma.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 ve mimari merkezi](../solutions/index.yml)