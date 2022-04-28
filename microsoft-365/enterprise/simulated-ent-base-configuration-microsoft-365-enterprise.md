---
title: Microsoft 365 için kurumsal temel yapılandırma simülasyonu
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Kurumsal Microsoft 365 için sanal bir kurumsal test ortamı oluşturmak için bu Test Laboratuvarı Kılavuzu'nu kullanın.
ms.openlocfilehash: 9c52bf657e91ceca9ef6e43f20a523a57a7b5042
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078723"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Sanal kurumsal temel yapılandırma

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Bu makalede, aşağıdakileri içeren kuruluş için Microsoft 365 için basitleştirilmiş bir ortamın nasıl oluşturulacağı açıklanır:

- Microsoft 365 E5 deneme sürümü veya ücretli abonelik.
- Bir Azure sanal ağındaki üç sanal makineden (DC1, APP1 ve CLIENT1) oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti.
 
![Sanal kurumsal temel yapılandırma.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Basitleştirilmiş bir test ortamı oluşturmak iki aşamayı içerir:
- [1. Aşama: Simülasyon intraneti oluşturma](#phase-1-create-a-simulated-intranet)
- [2. Aşama: Microsoft 365 E5 aboneliğinizi oluşturma](#phase-2-create-your-microsoft-365-e5-subscription)

Elde edilen ortamı, ek [Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md) ile veya kendi başınıza [kuruluş için Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) özelliklerini ve işlevselliğini test etmek için kullanabilirsiniz.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.

## <a name="phase-1-create-a-simulated-intranet"></a>1. Aşama: Simülasyon intraneti oluşturma

Bu aşamada Azure altyapı hizmetlerinde Active Directory Domain Services (AD DS) etki alanı denetleyicisi, uygulama sunucusu ve istemci bilgisayar içeren bir intranet simülasyonu oluşturun.

Karma kimliği ve diğer özellikleri yapılandırmak ve göstermek [için bu bilgisayarları kurumsal Test Laboratuvarı Kılavuzları için ek Microsoft 365](m365-enterprise-test-lab-guides.md) kullanacaksınız.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Yöntem 1: Azure Resource Manager şablonuyla simülasyon intranetinizi oluşturma

Bu yöntemde, simülasyon intranetini oluşturmak için bir Azure Resource Manager şablonu kullanırsınız. Azure Resource Manager şablonları, Azure ağ altyapısını, sanal makineleri ve bunların yapılandırmasını oluşturmaya yönelik tüm yönergeleri içerir.

Şablonu dağıtmadan önce, [şablon BENİOKU sayfasını](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) okuyun ve aşağıdaki bilgileri hazır bulundurun:

- Test ortamınızın genel DNS etki alanı adı (testlab.\<*your public domain*>). **Bu adı Özel dağıtım** sayfasının **Etki Alanı Adı** alanına girersiniz.
- Sanal makinelerinizin genel IP adreslerinin URL'leri için bir DNS etiketi ön eki. Bu etiketi **Özel dağıtım** sayfasının **Dns Etiketi Ön Eki** alanına girmeniz gerekir.

Yönergeleri okuduktan sonra başlamak için [ŞABLON BENİOKU sayfasında](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) **Azure'a Dağıt'ı** seçin.

>[!Note]
>Azure Resource Manager şablonu tarafından oluşturulan sanal intranet ücretli bir Azure aboneliği gerektirir.

Şablon tamamlandıktan sonra yapılandırmanız şöyle görünür:

![Azure altyapı hizmetlerindeki sanal intranet.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Yöntem 2: Azure PowerShell ile simülasyon intranetinizi oluşturma

Bu yöntemde ağ altyapısını, sanal makineleri ve bunların yapılandırmasını oluşturmak için Windows PowerShell ve Azure PowerShell modülünü kullanırsınız.

PowerShell ile Azure altyapısının öğelerini birer birer oluşturma deneyimi elde etmek istiyorsanız bu yöntemi kullanın. Daha sonra PowerShell komut bloklarını Azure'daki diğer sanal makineleri kendi dağıtımınız için özelleştirebilirsiniz.

#### <a name="step-1-create-dc1"></a>1. Adım: DC1 oluşturma

Bu adımda, bir Azure sanal ağı oluşturur ve AD DS etki alanı için etki alanı denetleyicisi olan bir sanal makine olan DC1'i eklersiniz.

İlk olarak, yerel bilgisayarınızda bir Windows PowerShell komut istemi başlatın.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell en son sürümünü kullanır. Bkz. [Azure PowerShell cmdlet'lerle Kullanmaya başlayın](/powershell/azureps-cmdlets-docs/). 
  
Aşağıdaki komutla Azure hesabınızda oturum açın.
  
```powershell
Connect-AzAccount
```

Aşağıdaki komutu kullanarak abonelik adınızı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure aboneliğinizi ayarlayın. Köşeli ayraçlar ("<" ve ">") dahil olmak üzere tırnak işaretleri içindeki her şeyi doğru adla değiştirin.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ardından, sanal kurumsal test laboratuvarınız için yeni bir kaynak grubu oluşturun. Benzersiz bir kaynak grubu adı belirlemek için bu komutu kullanarak mevcut kaynak gruplarınızı listeleyin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Bu komutlarla yeni kaynak grubunuzu oluşturun. Köşeli ayraçlar da dahil olmak üzere tırnak işaretleri içindeki her şeyi doğru adlarla değiştirin.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından, sanal kurumsal ortamın kurumsal ağ alt ağını barındıracak ve bunu bir ağ güvenlik grubuyla koruyacak TestLab sanal ağını oluşturun. Kaynak grubunuzun adını girin ve yerel bilgisayarınızdaki PowerShell komut isteminde bu komutları çalıştırın.
  
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

Ardından DC1 sanal makinesini oluşturacak ve **testlab** için etki alanı denetleyicisi olarak yapılandıracaksınız.\<your public domain> AD DS etki alanı ve TestLab sanal ağının sanal makineleri için bir DNS sunucusu. Örneğin, genel etki alanı adınız **<span>contoso.com</span>** ise, DC1 sanal makinesi **<span>testlab.contoso.com</span>** etki alanı için bir etki alanı denetleyicisi olacaktır.
  
DC1 için bir Azure sanal makinesi oluşturmak için kaynak grubunuzun adını doldurun ve bu komutları yerel bilgisayarınızdaki PowerShell komut isteminde çalıştırın.
  
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

DC1'de yerel yönetici hesabı için bir kullanıcı adı ve parola girmeniz istenir. Güçlü bir parola kullanın ve hem adı hem de parolayı güvenli bir konuma kaydedin.
  
Ardından DC1 sanal makinesine bağlanın:
  
1. [Azure portal](https://portal.azure.com) **Kaynak Grupları'nı** seçin > <**_yeni kaynak grubunuzun adı_*_> > _* DC1** >  **Bağlan**.
    
2. Açık bölmede **RDP dosyasını indir'i** seçin. İndirilen DC1.rdp dosyasını açın ve **Bağlan'ı** seçin.
    
3. DC1 yerel yönetici hesabı adını belirtin:
    
   - Windows 7 için:
    
     **Windows Güvenliği** iletişim kutusunda **Başka bir hesap kullan'ı** seçin. **Kullanıcı adı** alanına **DC1local\\**< *yönetici hesabı adını*> girin.
    
   - Windows 8 veya Windows 10 için:
    
     **Windows Güvenliği** iletişim kutusunda **Diğer seçenekler'i** ve ardından **Farklı bir hesap kullan'ı** seçin. **Kullanıcı adı** alanına **DC1local\\**< *yönetici hesabı adını*> girin.
    
4. **Parola** alanına yerel yönetici hesabının parolasını girin ve **Tamam'ı** seçin.
    
5. İstendiğinde **Evet'i** seçin.
    
Ardından, DC1'de yönetici düzeyinde bir Windows PowerShell komut isteminde bu komutla F: sürücü harfiyle yeni bir birim olarak ek bir veri diski ekleyin.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ardından, DC1'i bir etki alanı denetleyicisi ve **testlab** için DNS sunucusu olarak yapılandırın.\<*your public domain*> Etki alanı. Genel etki alanı adınızı belirtin, köşeli ayraçları kaldırın ve ardından bu komutları DC1'de yönetici düzeyinde Windows PowerShell komut isteminde çalıştırın.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Güvenli mod yönetici parolası belirtmeniz gerekir. Bu parolayı güvenli bir konumda depolayın.
  
Bu komutların tamamlanmasının birkaç dakika sürebileceğini unutmayın.
  
DC1 yeniden başlatıldıktan sonra DC1 sanal makinesine yeniden bağlanın.
  
1. [Azure portal](https://portal.azure.com) kaynak *grubu adınızı* **DC1** >  Bağlan> >  > <**Kaynak Grupları'nı** **seçin.**
    
2. İndirilen DC1.rdp dosyasını çalıştırın ve **Bağlan'ı** seçin.
    
3. **Windows Güvenliği'da** **Başka bir hesap kullan'ı** seçin. **Kullanıcı adı** alanına **TESTLABlocal\\**< *yönetici hesabı adını*> girin.
    
4. **Parola** kutusuna yerel yönetici hesabının parolasını girin ve **Tamam'ı** seçin.
    
5. İstendiğinde **Evet'i** seçin.
    
Ardından, Active Directory'de TESTLAB etki alanı üyesi bilgisayarlarda oturum açarken kullanılacak bir kullanıcı hesabı oluşturun. Bu komutu yönetici düzeyinde Windows PowerShell komut isteminde çalıştırın.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Bu komutun Sizden User1 hesabı parolasını sağlamanız istendiğini unutmayın. Bu hesap tüm TESTLAB etki alanı üyesi bilgisayarlar için uzak masaüstü bağlantıları için kullanılacaktır, bu nedenle güçlü bir parola seçin. User1 hesabı parolasını kaydedin ve güvenli bir konumda depolayın.
  
Ardından, yeni User1 hesabını etki alanı, kuruluş ve şema yöneticisi olarak yapılandırın. Bu komutu yönetici düzeyinde Windows PowerShell komut isteminde çalıştırın.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

DC1 ile Uzak Masaüstü oturumunu kapatın ve TESTLABUser1\\ hesabını kullanarak yeniden bağlanın.
  
Ardından, Ping aracının trafiğine izin vermek için bu komutu yönetici düzeyinde Windows PowerShell komut isteminde çalıştırın.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Geçerli yapılandırmanız şöyle görünür:
  
![Sanal kurumsal temel yapılandırmanın 1. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>2. Adım: APP1'i yapılandırma

Bu adımda, başlangıçta web ve dosya paylaşım hizmetleri sağlayan bir uygulama sunucusu olan APP1'i oluşturup yapılandıracaksınız.

APP1 için Azure Sanal Makinesi oluşturmak için kaynak grubunuzun adını doldurun ve yerel bilgisayarınızda komut isteminde bu komutları çalıştırın.
  
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

Ardından, APP1 yerel yönetici hesabı adını ve parolasını kullanarak APP1 sanal makinesine bağlanın ve ardından bir Windows PowerShell komut istemi açın.
  
APP1 ile DC1 arasındaki ad çözümlemesini ve ağ iletişimini denetlemek için **ping dc1.testlab** komutunu çalıştırın.\<*your public domain name*> komutunu seçip dört yanıt olduğunu doğrulayın.
  
Ardından, Windows PowerShell isteminde bu komutlarla APP1 sanal makinesini TESTLAB etki alanına ekleyin.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

**Add-Computer** komutunu çalıştırdıktan sonra TESTLABUser1\\ etki alanı hesabı kimlik bilgilerini sağlamanız gerektiğini unutmayın.
  
APP1 yeniden başlatıldıktan sonra TESTLABUser1\\ hesabını kullanarak buna bağlanın ve ardından yönetici düzeyinde bir Windows PowerShell komut istemi açın.
  
Ardından, APP1'de yönetici düzeyinde Windows PowerShell komut isteminde bu komutla APP1'i bir web sunucusu yapın.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Ardından, bu PowerShell komutlarıyla APP1'de klasörün içinde paylaşılan bir klasör ve bir metin dosyası oluşturun.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Geçerli yapılandırmanız şöyle görünür:
  
![Sanal kurumsal temel yapılandırmanın 2. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>3. Adım: İsteMCİ1'i yapılandırma

Bu adımda, intranette tipik bir dizüstü bilgisayar, tablet veya masaüstü bilgisayar işlevi gören CLIENT1'i oluşturup yapılandıracaksınız.

> [!NOTE]  
> Aşağıdaki komut kümesi, datacenter Windows Server 2016 çalıştıran client1'i oluşturur ve bu işlem tüm Azure abonelik türleri için yapılabilir. Visual Studio tabanlı bir Azure aboneliğiniz varsa, Azure portal ile Windows 10 çalıştıran client1 oluşturabilirsiniz[.](https://portal.azure.com)
  
İsteMCİ1 için Azure Sanal Makinesi oluşturmak için kaynak grubunuzun adını doldurun ve yerel bilgisayarınızda komut isteminde bu komutları çalıştırın.
  
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

Ardından, client1 yerel yönetici hesabı adını ve parolasını kullanarak client1 sanal makinesine bağlanın ve ardından yönetici düzeyinde bir Windows PowerShell komut istemi açın.
  
client1 ile DC1 arasındaki ad çözümlemesini ve ağ iletişimini denetlemek için **ping dc1.testlab** komutunu çalıştırın.\<*your public domain name*> Windows PowerShell komut isteminde komutunu çalıştırın ve dört yanıt olduğunu doğrulayın.
  
Ardından, Windows PowerShell isteminde bu komutlarla CLIENT1 sanal makinesini TESTLAB etki alanına ekleyin.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

**Add-Computer** komutunu çalıştırdıktan sonra TESTLABUser1\\ etki alanı hesabı kimlik bilgilerinizi sağlamanız gerektiğini unutmayın.
  
İsteMCİ1 yeniden başlatıldıktan sonra TESTLABUser1\\ hesap adını ve parolasını kullanarak bağlanın ve ardından yönetici düzeyinde bir Windows PowerShell komut istemi açın.
  
Ardından, APP1'de web ve dosya paylaşımı kaynaklarına İstemci1'den erişebildiğinizden emin olun.
  
1. Sunucu Yöneticisi ağaç bölmesinde **Yerel Sunucu'ya** tıklayın.
    
2. **İsteMCİ1 özellikleri** bölümünde **IE Artırılmış Güvenlik Yapılandırması'nın** yanındaki **Açık'ı** seçin.
    
3. **Internet Explorer Artırılmış Güvenlik Yapılandırması'nda** **Yöneticiler** ve **Kullanıcılar** için **Kapalı'yı** ve ardından **Tamam'ı** seçin.
    
4. Başlangıç ekranında **Internet Explorer'ı** ve ardından **Tamam'ı** seçin.
    
5. Adres çubuğuna **http <span>://</span>app1.testab.**\<*your public domain name*>**/** yazın ve **Enter tuşuna** basın. APP1 için varsayılan Internet Information Services web sayfasını görmeniz gerekir.
    
6. Masaüstü görev çubuğunda Dosya Gezgini simgesini seçin.
    
7. Adres çubuğuna **app1Files\\ yazın\\\\** ve **Enter tuşuna** basın. Dosyalar paylaşılan klasörünün içeriğini içeren bir klasör penceresi görmeniz gerekir.
    
8. **Paylaşılan dosyalar** klasörü penceresinde **Example.txt** dosyasına çift tıklayın. Example.txt dosyasının içeriğini görmeniz gerekir.
    
9. **example.txt - Not Defteri** ve **Dosyalar** paylaşılan klasör pencerelerini kapatın.
    
Geçerli yapılandırmanız şöyle görünür:
  
![Sanal kurumsal temel yapılandırmanın 3. adımı.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>2. Aşama: Microsoft 365 E5 aboneliğinizi oluşturma

Bu aşamada, üretim aboneliğinizden ayrı olan yeni bir Azure AD kiracısı kullanan yeni bir Microsoft 365 E5 aboneliği oluşturursunuz. Bunu iki şekilde yapabilirsiniz:

- Microsoft 365 E5 deneme aboneliği kullanın.

  Microsoft 365 E5 deneme aboneliği 30 gündür ve bu abonelik kolayca 60 güne uzatılabilir. Deneme aboneliğinin süresi dolduğunda, aboneliği ücretli aboneliğe dönüştürmeniz veya yeni bir deneme aboneliği oluşturmanız gerekir. Yeni deneme abonelikleri oluşturmak, karmaşık senaryolar içerebilecek yapılandırmanızı geride bırakacağınız anlamına gelir.  

- Az sayıda lisansa sahip ayrı bir Microsoft 365 E5 üretim aboneliği kullanın.

  Bu ek bir maliyettir, ancak süresi dolmayan bir çalışma test ortamınız olmasını sağlar; içinde özellikleri, yapılandırmaları ve senaryoları deneyebilirsiniz. Kavram kanıtı, eşlere ve yönetime yönelik tanıtım ve uygulama geliştirme ve test işlemleri için uzun vadede aynı test ortamını kullanabilirsiniz. Önerilen yöntem budur.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Office 365 E5 deneme aboneliğine kaydolma

Azure portal CORP\User1 hesabıyla client1'e bağlanın.

Yeni bir Office 365 E5 deneme aboneliği oluşturmak için basit temel yapılandırma Test Laboratuvarı Kılavuzu'nun [1. Aşamasındaki](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) yönergeleri gerçekleştirin.

Yeni Office 365 E5 deneme aboneliğinizi yapılandırmak için basit temel yapılandırma Test Laboratuvarı Kılavuzu'nun [2. Aşamasındaki](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) yönergeleri gerçekleştirin.

#### <a name="using-an-office-365-e5-test-environment"></a>Office 365 E5 test ortamı kullanma

Yalnızca bir Office 365 test ortamına ihtiyacınız varsa, bu makalenin geri kalanını okumanız gerekmez.

Hem Microsoft 365 hem de Office 365 için geçerli olan ek [Test Laboratuvarı Kılavuzları için bkz. Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Microsoft 365 E5 deneme aboneliği ekleme

Microsoft 365 E5 deneme aboneliği eklemek ve kullanıcı hesaplarınızı lisanslarla yapılandırmak için basit temel yapılandırma Test Laboratuvarı Kılavuzu'nun 3. [Aşamasındaki](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) yönergeleri gerçekleştirin.

  
## <a name="results"></a>Sonuç -ları

Test ortamınızda artık aşağıdakiler vardır:
  
- Deneme aboneliğini Microsoft 365 E5.
- Tüm uygun kullanıcı hesaplarınız Microsoft 365 E5 kullanmak üzere etkinleştirilir.
- Simülasyon ve basitleştirilmiş intranet.
    
Son yapılandırmanız şöyle görünür:
  
![Sanal kurumsal temel yapılandırmanın 2. aşaması.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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