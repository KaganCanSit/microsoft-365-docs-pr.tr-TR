---
title: Microsoft 365 test ortamında şirket içi sanal ağın benzetimi
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: "Özet: Microsoft Azure'da Microsoft 365 test ortamı olarak sanal bir şirket içi sanal ağ oluşturun."
ms.openlocfilehash: a3bc5c130ad03d1896abcf98ba9fc26d9ff2f422
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099179"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Microsoft 365 test ortamında şirket içi sanal ağın benzetimi

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Bu makalede, iki Azure sanal ağı kullanarak Microsoft Azure ile sanal hibrit bulut ortamı oluşturma adımları gösterilir. Sonuçta elde edilen yapılandırma aşağıdadır. 
  
![XPrem sanal ağında DC2 sanal makinesi ile sanal şirket içi sanal ağ test ortamının 3. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Bu, Azure IaaS hibrit bulut üretim ortamının simülasyonunu oluşturur ve şunlardan oluşur:
  
- Azure sanal ağında (TestLab sanal ağı) barındırılan sanal ve basitleştirilmiş bir şirket içi ağ.
    
- Azure'da barındırılan sanal bir şirket içi sanal ağ (XPrem).
    
- İki sanal ağ arasındaki sanal ağ eşleme ilişkisi.
    
- XPrem sanal ağında ikincil etki alanı denetleyicisi.
    
Bu, şu işlemleri yapabileceğiniz bir temel ve ortak başlangıç noktası sağlar: 
  
- Sanal Azure IaaS hibrit bulut ortamında uygulama geliştirin ve test edin.
    
- Karma bulut tabanlı BT iş yüklerinin benzetimini yapmak için, bazıları TestLab sanal ağında, bazıları da XPrem sanal ağındaki bilgisayarların test yapılandırmalarını oluşturun.
    
Bu test ortamını ayarlamanın üç ana aşaması vardır:
  
1. TestLab sanal ağını yapılandırın.
    
2. Şirket içi sanal ağı oluşturun.
    
3. DC2'yi yapılandırın.
    
> [!NOTE]
> Bu yapılandırma ücretli bir Azure aboneliği gerektirir. 

Elde edilen ortamı, ek [Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md) ile veya kendi başınıza [kuruluş için Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) özelliklerini ve işlevselliğini test etmek için kullanabilirsiniz.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> [Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) tüm makalelere görsel bir harita için kurumsal Test Laboratuvarı Kılavuz Yığını için Microsoft 365 gidin.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>1. Aşama: TestLab sanal ağını yapılandırma

TestLab adlı Azure sanal ağında DC1, APP1 ve CLIENT1 bilgisayarlarını yapılandırmak için [sanal kurumsal temel yapılandırmanın](simulated-ent-base-configuration-microsoft-365-enterprise.md) 1. **aşamasındaki** yönergeleri kullanın.
  
Bu, geçerli yapılandırmanızdır. 
  
![Azure'da sanal kurumsal temel yapılandırma.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>2. Aşama: XPrem sanal ağını oluşturma

Bu aşamada yeni XPrem sanal ağını oluşturup yapılandıracak ve ardından VNet eşlemesi ile TestLab sanal ağına bağlayacaksınız.
  
İlk olarak, yerel bilgisayarınızda bir Azure PowerShell istemi başlatın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell en son sürümünü kullanır. Bkz. [Azure PowerShell cmdlet'lerle Kullanmaya başlayın](/powershell/azureps-cmdlets-docs/). 
  
Bu komutla Azure hesabınızda oturum açın.
  
```powershell
Connect-AzAccount
```

Bu komutu kullanarak abonelik adınızı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure aboneliğinizi ayarlayın. Karakterler de dahil olmak üzere \< and > tırnak içindeki her şeyi doğru adlarla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından XPrem sanal ağını oluşturun ve bu komutlarla bir ağ güvenlik grubuyla koruyun.
  
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

Ardından, bu komutlarla TestLab ile XPrem sanal ağları arasında sanal ağ eşleme ilişkisi oluşturursunuz.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Bu, geçerli yapılandırmanızdır. 
  
![XPrem sanal ağı ve sanal ağ eşleme ilişkisi ile simülasyon şirket içi sanal ağ test ortamının 2. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>3. Aşama: DC2'yi yapılandırma

Bu aşamada, XPrem sanal ağında DC2 sanal makinesini oluşturacak ve ardından bir çoğaltma etki alanı denetleyicisi olarak yapılandıracaksınız.
  
İlk olarak DC2 için bir sanal makine oluşturun. Bu komutları yerel bilgisayarınızdaki Azure PowerShell komut isteminde çalıştırın.
  
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

Ardından, yerel yönetici hesabı adını ve parolasını kullanarak [Azure portal](https://portal.azure.com) yeni DC2 sanal makinesine bağlanın.
  
Ardından, temel bağlantı testine yönelik trafiğe izin vermek için bir Windows Güvenlik Duvarı kuralı yapılandırın. DC2'de yönetici düzeyinde Windows PowerShell komut isteminden bu komutları çalıştırın. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Ping komutu 10.0.0.4 IP adresinden dört başarılı yanıta neden olmalıdır. Bu, sanal ağ eşleme ilişkisi genelinde trafik testidir. 
  
Ardından, DC2'de Windows PowerShell komut isteminden bu komutla ek veri diskini F: sürücü harfiyle yeni bir birim olarak ekleyin.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından DC2'yi corp.contoso.com etki alanı için çoğaltma etki alanı denetleyicisi olarak yapılandırın. Dc2'de Windows PowerShell komut isteminden bu komutları çalıştırın.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Hem CORPUser1\\ parolasını hem de Dizin Hizmetleri Geri Yükleme Modu (DSRM) parolasını sağlamanız ve DC2'yi yeniden başlatmanız istendiğini unutmayın. 
  
Artık XPrem sanal ağının kendi DNS sunucusu (DC2) olduğuna göre, XPrem sanal ağını bu DNS sunucusunu kullanacak şekilde yapılandırmanız gerekir. Bu komutları yerel bilgisayarınızdaki Azure PowerShell komut isteminden çalıştırın.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Yerel bilgisayarınızdaki Azure portal CORPUser1\\ kimlik bilgileriyle DC1'e bağlanın. BILGISAYARLARıN ve kullanıcıların kimlik doğrulaması için yerel etki alanı denetleyicilerini kullanacak şekilde CORP etki alanını yapılandırmak için bu komutları DC1'de yönetici düzeyinde bir Windows PowerShell komut isteminden çalıştırın.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Bu, geçerli yapılandırmanızdır. 
  
![XPrem sanal ağında DC2 sanal makinesi ile sanal şirket içi sanal ağ test ortamının 3. aşaması.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Sanal Azure hibrit bulut ortamınız artık test için hazır.
  
Artık [kurumsal Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) ek özellikleriyle deneme yapmaya hazırsınız.
  
## <a name="next-steps"></a>Sonraki adımlar

Bu ek Test Laboratuvarı Kılavuzları kümelerini keşfedin:
  
- [Kimlik](m365-enterprise-test-lab-guides.md#identity)
- [Mobil cihaz yönetimi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Bilgi koruması](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)