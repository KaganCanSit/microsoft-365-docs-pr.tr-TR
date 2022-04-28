---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 4 Web uygulaması proxy'lerini yapılandırma
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Özet: Microsoft Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamanız için web uygulaması proxy sunucularını yapılandırın."
ms.openlocfilehash: 2200d4f7c0aafbaff11dd5d9b5b5b414fae06b5f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091291"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması 4. Aşama: Web uygulaması proxy'lerini yapılandırma

Azure altyapı hizmetlerinde Microsoft 365 federasyon kimlik doğrulaması için yüksek kullanılabilirlik dağıtmanın bu aşamasında, bir iç yük dengeleyici ve iki AD FS sunucusu oluşturursunuz.
  
[5. Aşama: Microsoft 365 için federasyon kimlik doğrulamasını yapılandırma](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) aşamasına geçmeden önce bu aşamayı tamamlamanız gerekir. Tüm aşamalar için bkz. [Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Azure'da İnternet'e yönelik yük dengeleyici oluşturma

Azure'ın İnternet'ten gelen istemci kimlik doğrulama trafiğini iki web uygulaması ara sunucusu arasında eşit bir şekilde dağıtması için İnternet'e yönelik bir yük dengeleyici oluşturmanız gerekir.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell en son sürümünü kullanır. Bkz. [Azure PowerShell ile Kullanmaya başlayın](/powershell/azure/get-started-azureps). 
  
Konum ve kaynak grubu değerlerini sağladığınızda, elde edilen bloğu Azure PowerShell komut isteminde veya PowerShell ISE'de çalıştırın.
  
> [!TIP]
> Özel ayarlarınıza göre çalışmaya hazır PowerShell komut blokları oluşturmak için bu [Microsoft Excel yapılandırma çalışma kitabını](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) kullanın. 

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

İnternet'e yönelik yük dengeleyicinize atanan genel IP adresini görüntülemek için, yerel bilgisayarınızdaki Azure PowerShell komut isteminde şu komutları çalıştırın:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Federasyon hizmeti FQDN'nizi belirleme ve DNS kayıtları oluşturma

İnternet'te federasyon hizmeti adınızı tanımlamak için DNS adını belirlemeniz gerekir. Azure AD Bağlan, Microsoft 365 bir güvenlik belirteci almak için bağlanan istemcilere gönderdiği URL'nin bir parçası olacak olan 5. Aşamada bu adla Microsoft 365 yapılandıracaktır. Örnek olarak fs.contoso.com (fs, federasyon hizmeti anlamına gelir).
  
Federasyon hizmeti FDQN'nizi aldıktan sonra, federasyon hizmeti FDQN için Azure İnternet'e yönelik yük dengeleyicinin genel IP adresine çözümlenen bir genel DNS etki alanı A kaydı oluşturun.
  
|**Ad**|**Tür**|**TTL**|**Değer**|
|:-----|:-----|:-----|:-----|
|federasyon hizmeti FDQN  <br/> |A  <br/> |3600  <br/> |Azure İnternet'e yönelik yük dengeleyicinin genel IP adresi (önceki **bölümdeKi Write-Host** komutu tarafından görüntülenir) <br/> |
   
Aşağıda bir örnek verilmiştir:
  
|**Ad**|**Tür**|**TTL**|**Değer**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Ardından, kuruluşunuzun özel DNS ad alanına, federasyon hizmeti FQDN'nizi AD FS sunucuları için iç yük dengeleyiciye atanan özel IP adresine çözümleyen bir DNS adresi kaydı ekleyin (Tablo I, öğe 4, Değer sütunu).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Azure'da web uygulaması proxy sunucusu sanal makinelerini oluşturma

İki web uygulaması proxy sunucusu için sanal makineleri oluşturmak için aşağıdaki Azure PowerShell komut bloğunu kullanın. 
  
Aşağıdaki Azure PowerShell komut kümelerinin aşağıdaki tablolardaki değerleri kullandığını unutmayın:
  
- Sanal makineleriniz için Tablo M
    
- Kaynak gruplarınız için Tablo R
    
- Sanal ağ ayarlarınız için Tablo V
    
- Alt ağlarınız için Tablo S
    
- Statik IP adresleriniz için Tablo I
    
- Kullanılabilirlik kümeleriniz için Tablo A
    
[2. Aşama: 1. Aşamada R](high-availability-federated-authentication-phase-2-configure-domain-controllers.md), V, S, I ve A Tablolarını yapılandırma: [Azure'ı yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md) aşamasında M Tablosunu tanımlamış olduğunuzu hatırlayın.
  
Tüm uygun değerleri sağladığınızda, elde edilen bloğu Azure PowerShell komut isteminde veya PowerShell ISE'de çalıştırın.
  
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
> Bu sanal makineler bir intranet uygulamasına ait olduğundan, bunlara bir genel IP adresi veya DNS etki alanı adı etiketi atanıp İnternet'e sunulmaz. Ancak bu, bunlara Azure portal bağlanamayacağınız anlamına da gelir. sanal makinenin özelliklerini görüntülediğinizde **Bağlan** seçeneği kullanılamaz. Özel IP adresini veya intranet DNS adını ve yerel yönetici hesabının kimlik bilgilerini kullanarak sanal makineye bağlanmak için Uzak Masaüstü Bağlantısı aksesuarını veya başka bir Uzak Masaüstü aracını kullanın.
  
Yer tutucu bilgisayar adlarıyla bu aşamanın başarıyla tamamlanmasından kaynaklanan yapılandırma aşağıdadır.
  
**4. Aşama: Azure'daki yüksek kullanılabilirlik federasyon kimlik doğrulama altyapınız için İnternet'e yönelik yük dengeleyici ve web uygulaması proxy sunucuları**

![Web uygulaması proxy sunucularıyla Azure'da federasyon kimlik doğrulama altyapısı Microsoft 365 yüksek kullanılabilirlik aşaması 4. aşama.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Sonraki adım

5. Aşama: Bu iş yükünü yapılandırmaya devam etmek [için Microsoft 365 için federasyon kimlik doğrulamasını](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) yapılandırın.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)