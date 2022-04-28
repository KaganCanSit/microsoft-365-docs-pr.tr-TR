---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması 3. Aşama AD FS sunucularını yapılandırma
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Microsoft Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamanız için AD FS sunucularını oluşturmayı ve yapılandırmayı öğrenin.
ms.openlocfilehash: ed0974c8286a5bbad083152d2e2f9aeb01f659df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101259"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması 3. Aşama: AD FS sunucularını yapılandırma

Azure altyapı hizmetlerinde Microsoft 365 federasyon kimlik doğrulaması için yüksek kullanılabilirlik dağıtmanın bu aşamasında, bir iç yük dengeleyici ve iki AD FS sunucusu oluşturursunuz.
  
[4. Aşama: Web uygulaması proxy'lerini yapılandırma](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) aşamasına geçmeden önce bu aşamayı tamamlamanız gerekir. Tüm aşamalar için bkz. [Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Azure'da AD FS sunucusu sanal makinelerini oluşturma

İki AD FS sunucusu için sanal makineleri oluşturmak için aşağıdaki PowerShell komut bloğunu kullanın. Bu PowerShell komut kümesi aşağıdaki tablolardaki değerleri kullanır:
  
- Sanal makineleriniz için Tablo M
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağlarınız için Tablo S
    
- Statik IP adresleriniz için Tablo I
    
- Kullanılabilirlik kümeleriniz için Tablo A
    
[2. Aşama: 1. Aşamada R](high-availability-federated-authentication-phase-2-configure-domain-controllers.md), V, S, I ve A Tablolarını yapılandırma: [Azure'ı yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md) aşamasında M Tablosunu tanımlamış olduğunuzu hatırlayın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell en son sürümünü kullanır. Bkz. [Azure PowerShell ile Kullanmaya başlayın](/powershell/azure/get-started-azureps). 
  
İlk olarak, iki AD FS sunucusu için bir Azure iç yük dengeleyici oluşturursunuz. Karakterleri kaldırarak değişkenlerin \< and > değerlerini belirtin. Tüm uygun değerleri sağladığınızda, elde edilen bloğu Azure PowerShell komut isteminde veya PowerShell ISE'de çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza göre çalışmaya hazır PowerShell komut blokları oluşturmak için bu [Microsoft Excel yapılandırma çalışma kitabını](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) kullanın. 

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

Ardından AD FS sunucusu sanal makinelerini oluşturun.
  
Tüm uygun değerleri sağladığınızda, elde edilen bloğu Azure PowerShell komut isteminde veya PowerShell ISE'de çalıştırın.
  
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
> Bu sanal makineler bir intranet uygulamasına ait olduğundan, bunlara bir genel IP adresi veya DNS etki alanı adı etiketi atanıp İnternet'e sunulmaz. Ancak bu, bunlara Azure portal bağlanamayacağınız anlamına da gelir. sanal makinenin özelliklerini görüntülediğinizde **Bağlan** seçeneği kullanılamaz. Özel IP adresini veya intranet DNS adını kullanarak sanal makineye bağlanmak için Uzak Masaüstü Bağlantısı aksesuarını veya başka bir Uzak Masaüstü aracını kullanın.
  
Her sanal makine için, seçtiğiniz uzak masaüstü istemcisini kullanın ve bir uzak masaüstü bağlantısı oluşturun. İntranet DNS'sini veya bilgisayar adını ve yerel yönetici hesabının kimlik bilgilerini kullanın.
  
Her sanal makine için, Windows PowerShell isteminde bu komutlarla bunları uygun Active Directory Domain Services (AD DS) etki alanına ekleyin.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Yer tutucu bilgisayar adlarıyla bu aşamanın başarıyla tamamlanmasından kaynaklanan yapılandırma aşağıdadır.
  
**3. Aşama: Azure'daki yüksek kullanılabilirlik federasyon kimlik doğrulama altyapınız için AD FS sunucuları ve iç yük dengeleyici**

![AD FS sunucularıyla Azure'da federasyon kimlik doğrulama altyapısı Microsoft 365 yüksek kullanılabilirlik aşaması 3. aşama.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Sonraki adım

4. Aşama: Bu iş yükünü yapılandırmaya devam etmek için [web uygulaması proxy'lerini](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) yapılandırın.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)