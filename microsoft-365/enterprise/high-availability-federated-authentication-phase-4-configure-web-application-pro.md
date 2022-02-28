---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 4 Web uygulaması sunucularını yapılandırma
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Özet: Web uygulamasındaki web uygulaması ara sunucularını, iş yeriz için yüksek kullanılabilirlik federal Microsoft 365 için Microsoft Azure.'
ms.openlocfilehash: ea50a48fe4bebd997ecf6b472a60e57772bf2b0f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986692"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 4: Web uygulaması sunucularını yapılandırma

Azure altyapı hizmetlerde şirket içi kimlik doğrulaması için Microsoft 365 dağıtımın bu aşamasında, bir iç yük dengeleyici ve iki AD FS sunucusu oluşturun.
  
Aşama 5: Federasyon kimlik doğrulamasını yapılandırma aşamasına başlamadan önce bu [aşamayı tamamlamanız Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Tüm [aşamalar için Bkz. Azure'da Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) için yüksek kullanılabilirlik federal kimlik doğrulamasını dağıtma.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Azure'da İnternet'e yönelik yük dengeleyicisi oluşturma

Azure'ın gelen istemci kimlik doğrulama trafiğini İnternet'den iki web uygulaması ara sunucusuna eşit bir şekilde dağıtması için İnternet'e yönelik bir yük dengeleyici oluşturmanız gerekir.
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni e-Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Konum ve kaynak grubu değerlerini sağladığınız zaman, sonuç bloğunı Azure PowerShell isteminde veya PowerShell ISE'de çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza bağlı olarak hazır çalıştırlı PowerShell komut blokları oluşturmak için bu Microsoft Excel [kullanın](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

İnternet'e yönelik yük dengeleyicinize atanan genel IP adresini görüntülemek için, bu komutları yerel Azure PowerShell komut isteminde çalıştırın:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Federasyon hizmeti FQDN'nizi belirleme ve DNS kayıtları oluşturma

İnternet'e bağlı federasyon hizmetinizin adını belirlemek için DNS adını belirlemeniz gerekir. Azure AD Bağlan bu Microsoft 365 adla yapılandıracak ve bu aşama, Microsoft 365'in güvenlik belirteci almak üzere istemcileri bağlamaya gönderdiği URL'nin bir parçası olacak. Federasyon hizmetine örnek fs.contoso.com (fs, federasyon hizmetinin açılımıdır).
  
Federasyon hizmetiniz FDQN'niz olduktan sonra, İnternet'e yönelik yük dengeleyicinin genel IP adresine çözümleyicisi olan federasyon hizmeti FDQN için bir ortak DNS etki alanı A kaydı oluşturun.
  
|**Ad**|**Tür**|**TTL**|**Değer**|
|:-----|:-----|:-----|:-----|
|federasyon hizmeti FDQN  <br/> |A  <br/> |3600  <br/> |Azure İnternet'e yönelik yük dengeleyicinin genel IP adresi (önceki bölümde **Yazma Ana** Bilgisayarı komutuyla görüntülenir) <br/> |
   
İşte bir örnek:
  
|**Ad**|**Tür**|**TTL**|**Değer**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Ardından, federasyon hizmeti FQDN'nizi, AD FS sunucularının iç yük dengeleyicisine atanan özel IP adresine (Tablo I, öğe 4, Değer sütunu) çözümleyicisi için, kuruluş özel DNS ad alanına bir DNS adres kaydı ekleyin.
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Azure'da web uygulaması ara sunucu sanal makinelerini oluşturma

İki web uygulaması ara Azure PowerShell sanal makineler oluşturmak için aşağıdaki komut bloğuni kullanın. 
  
Aşağıdaki komut kümelerinden Azure PowerShell aşağıdaki tablolarda yer alan değerlerin olduğunu unutmayın:
  
- Sanal makineleriniz için M Tablosu
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağların için S Tablosu
    
- Tablo I, statik IP adresleriniz için
    
- Kullanılabilirlik kümeniz için A Tablosu
    
Aşama [2'de](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) Tablo M'yi tanımlamış olmalısınız: Aşama 1'de etki alanı denetleyicileriyle Tabloları R, V, S, I ve [A'da yapılandırın: Azure'i yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Tüm doğru değerleri sağladığınız zaman, sonuç bloğunı Azure PowerShell isteminde veya PowerShell ISE'de çalıştırın.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Bu sanal makineler bir intranet uygulamasına yönelik olduğundan, onlara bir genel IP adresi veya DNS etki alanı adı etiketi atanmaz ve İnternet'e açık olur. Ancak bu, onlara Azure portaldan bağlanamazsınız anlamına da gelir. Bu **Bağlan**, sanal makinenin özelliklerini görüntülerken kullanılamaz. Sanal makineye özel IP adresi veya intranet DNS adını ve yerel yönetici hesabının kimlik bilgilerini kullanarak bağlanmak için Uzak Masaüstü Bağlantısı aksesuarını veya başka bir Uzak Masaüstü aracını kullanın.
  
Bu aşamanın başarıyla tamamlanmasından sonra, yer tutucu bilgisayar adlarla elde edilen yapılandırma şu şekildedir.
  
**Aşama 4: Azure'daki yüksek kullanılabilirlik federal kimlik doğrulama altyapınız için İnternet'e yönelik yük dengeleyici ve web uygulaması ara sunucularını**

![Web uygulaması ara sunucularıyla Azure'Microsoft 365 federasyon kimlik doğrulama altyapısının yüksek kullanılabilirlik 4. aşaması.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Sonraki adım

Aşama [5: Bu iş yükünü yapılandırmaya devam etmek Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) için federasyon kimlik doğrulamasını yapılandırma.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)