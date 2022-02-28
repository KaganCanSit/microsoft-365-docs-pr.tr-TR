---
title: Kullanıcı için sanal kurumsal temel yapılandırma Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Kurumsal test ortamı için sanal bir kurumsal test ortamı oluşturmak üzere bu Test Laboratuvarı Microsoft 365 kullanın.
ms.openlocfilehash: d335ed074adc6abe8bc1dabf58392d5b9051ccc6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984323"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Sanal kurumsal temel yapılandırma

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Bu makalede, kurumsal şirketler için şunları içeren basitleştirilmiş Microsoft 365 ortamın nasıl oluşturulacakları açıklanmıştır:

- Deneme Microsoft 365 E5 ücretli abonelik.
- İnternet'e bağlı, Azure sanal ağına (DC1, APP1 ve CLIENT1) üç sanal makineden oluşan basitleştirilmiş bir kuruluş intraneti.
 
![Sanal kurumsal temel yapılandırmadır.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Basitleştirilmiş bir test ortamı oluşturma işlemi iki aşama içerir:
- [Aşama 1: Sanal bir intranet oluşturma](#phase-1-create-a-simulated-intranet)
- [Aşama 2: Microsoft 365 E5 oluşturma](#phase-2-create-your-microsoft-365-e5-subscription)

Sonuç ortamını, ek Test Laboratuvarı Kılavuzları ile veya kendi [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) kurumsal özelliklerin ve [işlevlerinin test](m365-enterprise-test-lab-guides.md) etmek için kullanabilirsiniz.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>Aşama 1: Sanal bir intranet oluşturma

Bu aşamada, Active Directory Etki Alanı Hizmetleri (AD DS) etki alanı denetleyicisi, uygulama sunucusu ve istemci bilgisayar içeren Azure altyapı hizmetlerinde sanal bir intranet oluşturmaktır.

Karma kimliği ve diğer özellikleri yapılandırmak [ve göstermek için Microsoft 365 Test](m365-enterprise-test-lab-guides.md) Laboratuvarı Kılavuzlarında bu bilgisayarları kuruluş test laboratuvarı kılavuzlarının ek çalışmalarında kullanacağız.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Yöntem 1: Azure Kaynak Yöneticisi şablonuyla sanal intranet oluşturma

Bu yöntemde, sanal intranet oluşturmak için bir Azure Kaynak Yöneticisi şablonu kullanırsınız. Azure Kaynak Yöneticisi şablonları, Azure ağ altyapısını, sanal makineleri ve bunların yapılandırmalarını oluşturma yönergelerinin hepsini içerir.

Şablonu dağıtmadan önce, şablon [BENI OKUNdu sayfasını](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) okuyun ve aşağıdaki bilgilerin hazır olduğunu okuyun:

- Test ortamının (testlab.) ortak DNS etki alanı adı.\<*your public domain*> Bu adı, Özel dağıtım **sayfasının Etki** Alanı Adı **alanına girebilirsiniz** .
- Sanal makinenizin genel IP adreslerinin URL'leri için bir DNS etiketi öneki. Bu etiketi, Özel dağıtım sayfasının **Dns Etiketi Öneki** alanına **girmeniz** gerekir.

Yönergeleri okuduktan sonra, çalışmaya **başlamak için Şablon BENI OKUNDU** sayfasında [Azure'a Dağıt'ı](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) seçin.

>[!Note]
>Azure Resource Manager şablonu tarafından yerleşik sanal intranet için ücretli bir Azure aboneliği gerekir.

Şablon tamamlandıktan sonra, yapılandırmanız aşağıdaki gibi olur:

![Azure altyapı hizmetlerde sanal intranet.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>2. Yöntem: Daha fazla bilgiyle sanal intranet Azure PowerShell

Bu yöntemde, Windows PowerShell altyapısını, sanal Azure PowerShell ve bunların yapılandırmasını oluşturmak için Azure PowerShell modülü kullanılır.

PowerShell ile Azure altyapısının öğelerini adım adım oluşturma deneyimi elde etmek için bu yöntemi kullanın. Ardından PowerShell komut bloklarını, Azure'daki diğer sanal makineler için kendi dağıtımınız için özelleştirebilirsiniz.

#### <a name="step-1-create-dc1"></a>1. Adım: DC1 oluşturma

Bu adımda, bir Azure sanal ağı oluşturun ve AD DS etki alanı için etki alanı denetleyicisi olan sanal bir makine olan DC1'i ekleyin.

İlk olarak, Windows PowerShell bilgisayarınızda bir Komut İstemi komutu başlatın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni cmdlet'leri Azure PowerShell başlama](/powershell/azureps-cmdlets-docs/). 
  
Aşağıdaki komutla Azure hesabınızla oturum açın.
  
```powershell
Connect-AzAccount
```

Aşağıdaki komutu kullanarak abonelik adı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure aboneliğinizi ayarlayın. Tırnak işaretleri içindeki her şeyi, ayraçlar ("<" ve ">") dahil, doğru adla değiştirin.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ardından, sanal kurumsal test laboratuvarınız için yeni bir kaynak grubu oluşturun. Benzersiz bir kaynak grubu adı belirlemek için, bu komutu kullanarak var olan kaynak gruplarınızı listelenin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Bu komutlarla yeni kaynak grubunızı oluşturun. Açılı ayraçlar da dahil olmak üzere tırnak içindeki her şeyi doğru adlarla değiştirin.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından, sanal kurumsal ortamın şirket ağı alt ağına ev sahipliği edecek ve bunu bir ağ güvenlik grubuyla koruyacak TestLab sanal ağı oluşturun. Kaynak grubu adının doldurun ve yerel bilgisayarınızda PowerShell komut isteminde bu komutları çalıştırın.
  
```powershell
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Ardından, DC1 sanal makinesi oluşturun ve testlab için bir etki alanı denetleyicisi olarak **yapılandırabilirsiniz.**\<your public domain> AD DS etki alanı ve TestLab sanal ağının sanal makineleri için bir DNS sunucusu. Örneğin, ortak etki alanı adınız **<span>contoso.com</span>** ise, DC1 sanal makinesi **<span>testlab.contoso.com</span> etki alanı için bir etki alanı denetleyicisi** olur.
  
DC1 için bir Azure sanal makinesi oluşturmak için, kaynak grubu adının doldurun ve bu komutları yerel bilgisayarınızda PowerShell komut isteminde çalıştırın.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

DC1'de yerel yönetici hesabı için kullanıcı adı ve parola istenir. Güçlü bir parola kullanın ve hem ad hem de parolayı güvenli bir konuma yazın.
  
Ardından DC1 sanal makinesine bağlanin:
  
1. [Azure portalında,](https://portal.azure.com) Kaynak Grupları **' > <** **_kaynak grubu_*_*> > _DC1** >  **Bağlan.**
    
2. Açık bölmede **RDP dosyasını indir'i seçin**. İndirilen DC1.rdp dosyasını açın ve Tamam'ı **Bağlan**.
    
3. DC1 yerel yönetici hesabı adını belirtin:
    
   - 7 Windows için:
    
     Yeni **Windows Güvenliği kutusunda** Başka bir hesap **kullan'ı seçin**. Kullanıcı **adı alanına** **DC1local\\**< *yönetici hesap adını girin ve ardından*>.
    
   - Daha fazla Windows 8 veya Windows 10:
    
     Yeni **Windows Güvenliği kutusunda** Diğer **seçenekler'i** ve sonra Farklı bir hesap **kullan'ı seçin**. Kullanıcı **adı alanına** **DC1local\\**< *yönetici hesap adını girin ve ardından*>.
    
4. Parola **alanına**, yerel yönetici hesabının parolasını girin ve Tamam'ı **seçin**.
    
5. Soruldiğinde Evet'i **seçin**.
    
Ardından, F sürücü harfiyle yeni bir ses düzeyi olarak fazladan bir veri diski ekleyin. Bu komut DC1'de yönetici Windows PowerShell komut istemindedir.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, testlab için DC1'i etki alanı denetleyicisi ve DNS sunucusu **olarak yapılandırabilirsiniz.**\<*your public domain*> etki alanını seçin. Ortak etki alanı adınızı belirtin, köşeli ayraçları kaldırın ve bu komutları DC1'de yönetici Windows PowerShell komut isteminde çalıştırın.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Güvenli mod yönetici parolası belirtmeniz gerekir. Bu parolayı güvenli bir yerde depo edin.
  
Bu komutların tamamlanmasının birkaç dakika gerektirebiliyor.
  
DC1 yeniden başlatıldıktan sonra DC1 sanal makinesine yeniden bağlanin.
  
1. [Azure portalında,](https://portal.azure.com) KAYNAK grubu **adı olarak** **DC1** > <*Kaynak Grupları'*> > seçin  > **Bağlan**.
    
2. İndirilen DC1.rdp dosyasını çalıştırın ve sonra **İndir'i Bağlan**.
    
3. Yeni **Windows Güvenliği** Başka bir **hesap kullan'ı seçin**. Kullanıcı **adı alanına** **TESTLABlocal\\**< *yönetici hesap adı girin ve>*.
    
4. Parola **kutusuna** yerel yönetici hesabının parolasını girin ve Tamam'ı **seçin**.
    
5. Soruldiğinde Evet'i **seçin**.
    
Ardından, Active Directory'de TESTLAB etki alanı üyesi bilgisayarlarda oturum a hesaplarken kullanılacak bir kullanıcı hesabı oluşturun. Bu komutu yönetici düzeyinde bir komut isteminde Windows PowerShell komutu çalıştırın.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Bu komutun User1 hesabı parolasını girmenizi istendiğinde unutmayın. Bu hesap, tüm TESTLAB etki alanı üyesi bilgisayarlara uzak masaüstü bağlantıları için kullanılacaktır, bu nedenle güçlü bir parola seçin. Kullanıcı1 hesabı parolasını kaydedin ve güvenli bir yerde depolar.
  
Ardından, yeni User1 hesabını etki alanı, kuruluş ve şema yöneticisi olarak yapılandırabilirsiniz. Bu komutu yönetici düzeyindeki komut isteminde Windows PowerShell çalıştırın.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

DC1 ile Uzak Masaüstü oturumunu kapatın ve TESTLABUser1\\ hesabını kullanarak yeniden bağlanin.
  
Ardından, Ping aracının trafiğine izin vermek için bu komutu yönetici düzeyinde bir Windows PowerShell isteminde çalıştırın.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Geçerli yapılandırmanız şöyle görünüyor:
  
![Sanal kurumsal temel yapılandırmanın 1. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>2. Adım: APP1'i yapılandırma

Bu adımda, başlangıçta web ve dosya paylaşım hizmetleri sağlayan bir uygulama sunucusu olan APP1'i oluşturabilir ve yapılandırırsınız.

APP1 için Azure Sanal Makinesi oluşturmak için, kaynak grubu adının doldurun ve bu komutları yerel bilgisayarınızda komut isteminde çalıştırın.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ardından, APP1 yerel yönetici hesap adı ve parolasını kullanarak APP1 sanal makinesine bağlanin ve sonra Windows PowerShell istemini açın.
  
Ad çözümlemesi ile APP1 ile DC1 arasındaki ağ iletişimini kontrol etmek için **ping dc1.testlab komutunu çalıştırın.**\<*your public domain name*> komutunu kullanın ve dört yanıt olduğunu doğrulayın.
  
Ardından, komut isteminde bu komutları kullanarak APP1 sanal makinesiyle TESTLAB etki Windows PowerShell katılın.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bilgisayar Ekle komutunu çalıştırdikten **sonra TESTLABUser1**\\ etki alanı hesabı kimlik bilgilerini eklemeniz gerektiğini unutmayın.
  
APP1 yeniden başlatıldıktan sonra TESTLABUser1\\ hesabını kullanarak bu hesaba bağlanın ve sonra bir yönetici düzeyinde Windows PowerShell istemi açın.
  
Ardından APP1'i yönetici düzeyinde ve APP1'de Windows PowerShell komut isteminde bu komutun yer alan bir web sunucusu yapma.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Ardından, bu PowerShell komutlarıyla APP1'de klasör içinde bir paylaşılan klasör ve bir metin dosyası oluşturun.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Geçerli yapılandırmanız şöyle görünüyor:
  
![Sanal kurumsal temel yapılandırmanın 2. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>3. Adım: CLIENT1'i yapılandırma

Bu adımda, intranet'te normal bir dizüstü bilgisayar, tablet veya masaüstü bilgisayar gibi işlem yapan CLIENT1'i oluşturabilir ve yapılandırabilirsiniz.

> [!NOTE]  
> Aşağıdaki komut kümesi, Tüm Azure abonelikleri Windows Server 2016 veri merkezi üzerinde çalışan CLIENT1'i oluşturur. Visual Studio tabanlı bir Azure aboneliğiniz varsa, Azure portalında çalıştırarak MÜŞTERI1 Windows 10 [istemci oluşturabilirsiniz](https://portal.azure.com).
  
İSTEMCI1 için Azure Sanal Makinesi oluşturmak için, kaynak grubu adının doldurun ve bu komutları yerel bilgisayarınızda komut isteminde çalıştırın.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ardından, CLIENT1 yerel yönetici hesap adı ve parolasını kullanarak CLIENT1 sanal makinesine bağlanın ve sonra bir yönetici düzeyindeki Windows PowerShell istemini açın.
  
Ad çözümlemesini ve CLIENT1 ile DC1 arasındaki ağ iletişimini kontrol etmek için **, ping dc1.testlab komutunu çalıştırın.**\<*your public domain name*> komutuna Windows PowerShell ve dört yanıt olduğunu doğrulayın.
  
Ardından, komut isteminde bu komutları kullanarak CLIENT1 sanal makinesiyle TESTLAB etki Windows PowerShell katılın.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bilgisayar Ekle komutunu çalıştırdikten sonra TESTLABUser1\\ etki alanı hesabı kimlik **bilgilerinizi eklemeniz gerektiğini** unutmayın.
  
İSTEMCI1 yeniden başlatıldıktan sonra TESTLABUser1\\ hesap adı ve parolasını kullanarak istemciye bağlanın ve sonra yönetici düzeyinde bir Windows PowerShell istemi açın.
  
Ardından, İstemci1'den APP1'te web ve dosya paylaşımı kaynaklarına erişebilirsiniz.
  
1. Sunucu Yöneticisi'nde, ağaç bölmesinde Yerel **Sunucu'ya tıklayın**.
    
2. **İstemci1 için Özellikler'de**,  **IE Gelişmiş Güvenlik Yapılandırması'nın yanındaki Açık'ı seçin**.
    
3. **Internet Explorer Gelişmiş Güvenlik Yapılandırması'nın altında** Yöneticiler **ve** Kullanıcılar için **Kapalı'ya** **tıklayın ve** ardından Tamam'a **tıklayın**.
    
4. Başlangıç ekranından Internet **Explorer'ı ve** sonra Tamam'ı **seçin**.
    
5. Adres çubuğuna **http <span>://</span>app1.testab.**\<*your public domain name*>**/** girin ve Enter tuşuna **basın**. APP1 için varsayılan Internet Information Services sayfası görüyorsanız.
    
6. Masaüstü görev çubuğunda Dosya Gezgini simgesini seçin.
    
7. Adres çubuğuna **app1Files\\\\\\ girin ve** Enter tuşuna **basın**. Dosyalar paylaşılan klasörünün içeriğini içeren bir klasör penceresi görüyor olun.
    
8. Dosyalar **paylaşılan** klasör penceresinde, paylaşılan **klasörExample.txttıklayın** . Dosyanın içeriğini Example.txt.
    
9. Paylaşılan - **example.txt Not Defteri** Dosyalar **paylaşılan klasör** pencerelerini kapatın.
    
Geçerli yapılandırmanız şöyle görünüyor:
  
![Sanal kurumsal temel yapılandırmanın 3. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Aşama 2: Microsoft 365 E5 oluşturma

Bu aşamada, üretim aboneliğinizin Microsoft 365 E5 bir Azure AD kiracısı kullanan yeni bir Azure AD aboneliği oluşturabilirsiniz. Bunu iki şekilde yapabilirsiniz:

- Microsoft 365 E5'in deneme aboneliğini kullanın.

  En Microsoft 365 E5 deneme aboneliği 30 gündür ve bu süre 60 gün kadar kolayca uzatılabilir. Deneme aboneliğinin süresi dolduğunda, aboneliği ücretli bir aboneliğe dönüştürmeniz veya yeni bir deneme aboneliği oluşturmanız gerekir. Yeni deneme abonelikleri oluşturmak, geride karmaşık senaryoları da içerecek olan yapılandırmanızı bırak anlamına gelir.  

- Az sayıda lisansı olan Microsoft 365 E5 abonelik aboneliklerini kullanın.

  Bu ek bir maliyettir, ancak süresi dolmadan bir çalışma test ortamına sahip olasınız; bu özellik, yapılandırma ve senaryoları  denemeyi deneyin. Aynı test ortamını, kavram kanıtı, eşler ve yönetim tanıtımları, uygulama geliştirme ve test etme için uzun vadeli olarak kullanabilirsiniz. Bu önerilen yöntemdir.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Office 365 E5 deneme aboneliğine kaydolma

Azure portaldan CORP\User1 hesabıyla CLIENT1'e bağlanın.

Yeni bir deneme sürümü Office 365 E5 için basit temel yapılandırma Test Laboratuvarı [Kılavuzu'nın Aşama 1'inde](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) verilen yönergeleri uygulayın.

Yeni ana bilgisayar deneme Office 365 E5 yapılandırmak için basit temel yapılandırma Test Laboratuvarı [Kılavuzu'nın 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription). Aşama yönergelerini gerçekleştirin.

#### <a name="using-an-office-365-e5-test-environment"></a>Office 365 E5 sınama ortamı kullanma

Yalnızca bir test Office 365 ihtiyacınız varsa, bu makalenin kalan kalanını okumazsınız.

Hem Test Laboratuvarı Kılavuzları hem test hem de test Microsoft 365 Office 365 için Microsoft 365 [Test Laboratuvarı Kılavuzlarına bakın](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Microsoft 365 E5 deneme aboneliği ekleme

Basit temel Microsoft 365 E5 Test Laboratuvarı Kılavuzu'nın Aşama [3'ü](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) altında verilen yönergeleri gerçekleştirin.

  
## <a name="results"></a>Sonuçlar

Test ortamınız artık şunları sağlar:
  
- Microsoft 365 E5 deneme aboneliğini seçin.
- Hesaplarınızı kullanmak için tüm uygun kullanıcı hesaplarınız Microsoft 365 E5.
- Benzetimi yapılan ve basitleştirilmiş bir intranet.
    
Son yapılandırmanız şöyle görünüyor:
  
![Sanal kurumsal temel yapılandırmanın aşama 2. aşaması.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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