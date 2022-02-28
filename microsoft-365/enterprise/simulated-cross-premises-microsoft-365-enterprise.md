---
title: Bir test ortamında benzetimi yapılan şirket Microsoft 365 sanal ağı
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: seo-marvel-apr2020
description: 'Özet: Bir test ortamı olarak bu ağda sanal bir Microsoft Azure şirket içi sanal Microsoft 365 oluşturun.'
ms.openlocfilehash: 0d0e22b5c9a12f4757a6dff5892ef72a757d2bda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988147"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Bir test ortamında benzetimi yapılan şirket Microsoft 365 sanal ağı

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Bu makale, iki Azure sanal ağı kullanarak karma ve sanal bir Microsoft Azure bir bulut ortamı oluşturma konusunda size yol verir. Sonuçta elde edilen yapılandırma şu şekildedir. 
  
![XPrem VNet'te DC2 sanal makinesiyle, sanal şirket içi sanal ağ test ortamının 3. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Bu işlem, Azure IaaS karma bulut üretim ortamının benzetimini eder ve aşağıdakilerden oluşur:
  
- Azure sanal ağına (TestLab sanal ağı) barındırılan sanal ve basitleştirilmiş bir şirket içi ağ.
    
- Azure'da (XPrem) barındırılan sanal bir şirket içi ağ benzetimi.
    
- İki sanal ağ arasındaki VNet eşleme ilişkisi.
    
- XPrem sanal ağın ikincil etki alanı denetleyicisi.
    
Bu, temel ve genel bir başlangıç noktası sağlar; burada: 
  
- Sanal bir Azure IaaS karma bulut ortamında uygulamaları geliştirin ve test edin.
    
- Bulut tabanlı karma IT iş yüklerinin benzetimini yapmak için, bazıları TestLab sanal ağı içinde ve bazıları da XPrem sanal ağı içinde olmak üzere bilgisayarların test yapılandırmaları oluşturun.
    
Bu test ortamını ayarlamanın üç önemli aşaması vardır:
  
1. TestLab sanal ağına yapılandırma.
    
2. Şirket içi sanal ağı oluşturun.
    
3. DC2'yi yapılandırma.
    
> [!NOTE]
> Bu yapılandırma için ücretli bir Azure aboneliği gerekir. 

Sonuç ortamını, ek Test Laboratuvarı Kılavuzları ile veya kendi [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) kurumsal özelliklerin ve [işlevlerinin test](m365-enterprise-test-lab-guides.md) etmek için kullanabilirsiniz.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal [test Microsoft 365 Kılavuzu yığınına](../downloads/Microsoft365EnterpriseTLGStack.pdf) göre görsel bir harita için Microsoft 365 Test Laboratuvarı Kılavuzu Yığını'nın görsel bir haritasına gidin.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Aşama 1: TestLab sanal ağına yapılandırma

TestLab adlı Azure sanal ağına DC1 [](simulated-ent-base-configuration-microsoft-365-enterprise.md), APP1 ve CLIENT1 bilgisayarlarını yapılandırmak için sanal kurumsal temel yapılandırmanın Aşama **1'inde** verilen yönergeleri kullanın.
  
Bu, geçerli yapılandırmanızdır. 
  
![Azure'daki sanal kurumsal temel yapılandırmadır.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Aşama 2: XPrem sanal ağı oluşturma

Bu aşamada, yeni XPrem sanal ağına bağlanma ve ardından bunu VNet eşliğiyle TestLab sanal ağına bağlamanız gerekir.
  
İlk olarak, yerel Azure PowerShell bir bağlantı istemi başlatın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni cmdlet'leri Azure PowerShell başlama](/powershell/azureps-cmdlets-docs/). 
  
Bu komutla Azure hesabınızla oturum açın.
  
```powershell
Connect-AzAccount
```

Bu komutu kullanarak abonelik adı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure aboneliğinizi ayarlayın. Tırnak içindeki her şeyi, karakterlerle birlikte \< and > doğru adlarla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından, XPrem sanal ağına oluşturun ve bu komutlarla bir ağ güvenlik grubuyla koruyun.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Ardından, bu komutlarla TestLab ve XPrem VNet'leri arasında VNet eşleme ilişkisi oluşturun.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Bu, geçerli yapılandırmanızdır. 
  
![XPrem VNet ve VNet eşleme ilişkisiyle, sanal şirket içi sanal ağ test ortamının aşama 2. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Aşama 3: DC2'yi yapılandırma

Bu aşamada, XPrem sanal ağına DC2 sanal makinesi oluşturun ve sonra bunu bir çoğaltma etki alanı denetleyicisi olarak yapılandırabilirsiniz.
  
İlk olarak, DC2 için bir sanal makine oluşturun. Bu komutları yerel Azure PowerShell Komut İstemi'nde çalıştırın.
  
```powershell
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ardından, yerel yönetici hesap adını ve parolasını kullanarak [Azure portaldan](https://portal.azure.com) yeni DC2 sanal makinesine bağlanın.
  
Ardından, temel bağlantı Windows izin verecek bir Güvenlik Duvarı kuralı yapılandırabilirsiniz. DC2'de yönetici Windows PowerShell komut isteminde, bu komutları çalıştırın. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Ping komutu IP adresi 10.0.0.4'den dört başarılı yanıta neden olacaktır. Bu, VNet eşleme ilişkisi genelindeki trafiğin bir sınamasıdır. 
  
Ardından, EK veri diskini, DC2'de yer alan Sürücü komutu isteminde yer alan bu komutla F Windows PowerShell harfiyle yeni bir birim olarak ekleyin.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, DC2'yi etki alanı için bir çoğaltma etki corp.contoso.com olarak yapılandırabilirsiniz. Bu komutları DC2'de Windows PowerShell komut isteminden çalıştırın.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

HEM CORPUser1\\ parolasını hem de Dizin Hizmetleri Geri Yükleme Modu (DSRM) parolasını girmenizi ve DC2'yi yeniden başlatmanızı istenir. 
  
XPrem sanal ağının kendi DNS sunucusuna (DC2) sahip olduğu için, XPrem sanal ağına bu DNS sunucusunu kullanmak üzere yapılandırmanız gerekir. Bu komutları yerel Azure PowerShell Komut İstemi'ne göre çalıştırın.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Yerel bilgisayarınızda Azure portalında CORPUser1 kimlik bilgileriyle DC1'e\\ bağlanın. CORP etki alanını bilgisayarlar ve kullanıcılar kimlik doğrulaması için yerel etki alanı denetleyicisini kullanacak şekilde yapılandırmak için, bu komutları DC1'de yönetici Windows PowerShell komut isteminden çalıştırın.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Bu, geçerli yapılandırmanızdır. 
  
![XPrem VNet'te DC2 sanal makinesiyle, sanal şirket içi sanal ağ test ortamının 3. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Sanal Azure karma bulut ortamınız artık test etmeye hazır.
  
Artık kurumsal kullanıma uygun uygulamanın ek özelliklerini [Microsoft 365 hazır mısınız](https://www.microsoft.com/microsoft-365/enterprise)?
  
## <a name="next-steps"></a>Sonraki adımlar

Bu ek Test Laboratuvarı Kılavuzlarını keşfedin:
  
- [Kimlik](m365-enterprise-test-lab-guides.md#identity)
- [Mobil cihaz yönetimi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Bilgi koruması](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)