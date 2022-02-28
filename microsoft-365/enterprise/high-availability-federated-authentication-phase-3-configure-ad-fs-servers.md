---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 3 AD FS sunucularını yapılandırma
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Aynı dosyada yüksek kullanılabilirlik federal kimlik doğrulamanız için AD FS sunucularını Microsoft 365 yapılandırmayı Microsoft Azure.
ms.openlocfilehash: c26fc68aa382ce93c62b6edbce4040b7e0813474
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988735"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 3: AD FS sunucularını yapılandırma

Azure altyapı hizmetlerde şirket içi kimlik doğrulaması için Microsoft 365 dağıtımın bu aşamasında, bir iç yük dengeleyici ve iki AD FS sunucusu oluşturun.
  
Aşama 4: Web uygulaması sunucularını [yapılandırma aşamasına başlamadan önce bu aşamayı tamamlamanız gerekir](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Tüm [aşamalar için Bkz. Azure'da Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) için yüksek kullanılabilirlik federal kimlik doğrulamasını dağıtma.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Azure'da AD FS sunucusu sanal makinelerini oluşturma

İki AD FS sunucusu için sanal makineler oluşturmak üzere aşağıdaki PowerShell komut bloğunı kullanın. Bu PowerShell komut kümesi aşağıdaki tablolarda yer alan değerleri kullanır:
  
- Sanal makineleriniz için M Tablosu
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağların için S Tablosu
    
- Tablo I, statik IP adresleriniz için
    
- Kullanılabilirlik kümeniz için A Tablosu
    
Aşama [2'de](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) Tablo M'yi tanımlamış olmalısınız: Aşama 1'de etki alanı denetleyicileriyle Tabloları R, V, S, I ve [A'da yapılandırın: Azure'i yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni e-Azure PowerShell](/powershell/azure/get-started-azureps). 
  
İlk olarak, iki AD FS sunucusu için bir Azure iç yük dengeleyicisi oluşturun. Karakterleri kaldırarak değişkenler için değerleri \< and > belirtin. Tüm doğru değerleri sağladığınız zaman, sonuç bloğunı Azure PowerShell isteminde veya PowerShell ISE'de çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza bağlı olarak hazır çalıştırlı PowerShell komut blokları oluşturmak için bu Microsoft Excel [kullanın](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Ardından, AD FS sunucusu sanal makinelerini oluşturun.
  
Tüm doğru değerleri sağladığınız zaman, sonuç bloğunı Azure PowerShell isteminde veya PowerShell ISE'de çalıştırın.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> Bu sanal makineler bir intranet uygulamasına yönelik olduğundan, onlara bir genel IP adresi veya DNS etki alanı adı etiketi atanmaz ve İnternet'e açık olur. Ancak bu, onlara Azure portaldan bağlanamazsınız anlamına da gelir. Bu **Bağlan**, sanal makinenin özelliklerini görüntülerken kullanılamaz. Sanal makineye özel IP adresini veya intranet DNS adını kullanarak bağlanmak için Uzak Masaüstü Bağlantısı donatısını veya başka bir Uzak Masaüstü aracını kullanın.
  
Her sanal makine için, tercihiniz uzak masaüstü istemcisini kullanın ve bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Her sanal makinede, komut isteminde şu komutları kullanarak bunları uygun Active Directory Etki Alanı Hizmetleri (AD DS) Windows PowerShell katılın.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Bu aşamanın başarıyla tamamlanmasından sonra, yer tutucu bilgisayar adlarla elde edilen yapılandırma şu şekildedir.
  
**Aşama 3: Azure'da yüksek kullanılabilirlik şirket içi kimlik doğrulama altyapınız için AD FS sunucuları ve iç yük dengeleyici**

![AD FS sunucularıyla Azure'Microsoft 365 federasyon kimlik doğrulama altyapısının yüksek kullanılabilirlik 3. aşaması.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Sonraki adım

Aşama [4: Bu iş yükünü yapılandırmaya devam etmek için web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) uygulaması sunucularını yapılandırma.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)