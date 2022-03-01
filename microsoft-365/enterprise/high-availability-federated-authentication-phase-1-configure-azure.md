---
title: Azure'a yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 1 Yapılandırma
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Özet: Posta için Microsoft Azure kullanılabilirliği yüksek federasyon kimlik doğrulaması barındırmak üzere kullanıcı altyapısını Microsoft 365.'
ms.openlocfilehash: 35666baf98b45419f41a0078729ac5a5a6fab995
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014387"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 1: Azure'i yapılandırma

Bu aşamada, azure'da sanal makineleri 2, 3 ve 4. aşamalarda barındıracak kaynak gruplarını, sanal ağı (VNet) ve kullanılabilirlik kümelerini oluşturmanız gerekir. Aşama 2: Etki alanı denetleyicilerini [yapılandırmaya başlamadan önce bu aşamayı tamamlamanız gerekir](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Tüm [aşamalar için Bkz. Azure'da Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) için yüksek kullanılabilirlik federal kimlik doğrulamasını dağıtma.
  
Azure'a şu temel bileşenler sağ):
  
- Kaynak grupları
    
- Azure sanal makinelerini barındırmak için alt ağların olduğu şirket içi bir Azure sanal ağı (VNet)
    
- Alt ağ yalıtımı gerçekleştirmek için ağ güvenlik grupları
    
- Kullanılabilirlik kümeleri
    
## <a name="configure-azure-components"></a>Azure bileşenlerini yapılandırma

Azure bileşenlerini yapılandırmaya başlamadan önce aşağıdaki tabloları doldurun. Azure'ı yapılandırma yordamlarında size yardımcı olmak için, bu bölümü yazdırarak gerekli bilgileri bir yere yazın veya bu bölümü bir belgeye kopyalayıp doldurun. VNet'in ayarları için, Tablo V'ye doldurun.
  
|**Öğe**|**Yapılandırma ayarı**|**Açıklama**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNet adı  <br/> |VNet'e atanacak ad (örnek FedAuthNet).  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |VNet konumu  <br/> |Sanal ağı içeren bölgesel Azure veri merkezi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |VPN cihazı IP adresi  <br/> |İnternet'te VPN cihazınızın arabiriminin genel IPv4 adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet adres alanı  <br/> |Sanal ağın adres alanı. Bu adres alanı belirlemek için IT departmanınız ile birlikte çalışabilirsiniz.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |I Yer paylaşım anahtarı  <br/> |Siteden siteye VPN bağlantısının her iki yanında da kimlik doğrulaması yapmak için kullanılacak 32 karakterlik rastgele, alfasayısal dize. Bu anahtar değerini belirlemek için, IT veya güvenlik departmanınız ile birlikte çalışma. Alternatif olarak bkz [. Önceden paylaşılan bir I İleti anahtarı için rastgele dize oluşturma](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo V: Şirket içi sanal ağ yapılandırması**
  
Ardından, bu çözümün alt ağları için Tablo S'de doldurun. Tüm adres alanları, ağ öneki biçimi olarak da bilinen Sınıfsız Etki Alanı Yönlendirme (CIDR) biçiminde olmalıdır. Örnek 10.24.64.0/20.
  
İlk üç alt ağ için, sanal ağ adres alanı temel alarak bir ad ve tek bir IP adresi alanı belirtin. Ağ geçidi alt ağın 27 bit adres süresini (/27 ön ek uzunluğuna sahip) Azure ağ geçidi alt ağın şu şekilde belirler:
  
1. VNet'in adres alanı içinde değişken bitleri 1 olarak ayarlayın; ağ geçidi alt ağı tarafından kullanılan bitlere kadar, sonra da kalan bitleri 0 olarak ayarlayın.
    
2. Sonuçta elde edilen bitleri ondalık değere dönüştürerek ağ geçidi alt ağ boyutuna ayarlanmış ön ek uzunluğu ile bir adres alanı olarak ifade etme.
    
Bu [hesaplamayı sizin için gerçekleştiren bir](address-space-calculator-for-azure-gateway-subnets.md) PowerShell komut bloğu ve C# veya Python konsolu uygulaması için bkz. Azure ağ geçidi alt ağları için adres alanı hesaplayıcı.
  
Sanal ağ adresi bölümünden bu adres boşluklarını belirlemek için, IT departmanınız ile birlikte çalışabilirsiniz.
  
|**Öğe**|**Alt ağ adı**|**Alt ağ adres alanı**|**Amaç**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Active Directory Etki Alanı Hizmetleri (AD DS) etki alanı denetleyicisi ve dizin eşitleme sunucusu sanal makineleri (SANAL CIHAZLARı) tarafından kullanılan alt ağ.  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |AD FS sanal bilgisayarları tarafından kullanılan alt ağ.  <br/> |
|3.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Web uygulaması ara sunucusu VM'leri tarafından kullanılan alt ağ.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Azure ağ geçidi sanal bilgisayarları tarafından kullanılan alt ağ.  <br/> |
   
 **Tablo S: Sanal ağdaki alt ağlar**
  
Ardından, sanal makinelere atanan statik IP adresleri ve yük dengeleyici örnekleri için Tablo I'yi doldurun.
  
|**Öğe**|**Amaç**|**Alt ağ üzerinde IP adresi**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |İlk etki alanı denetleyicisinin statik IP adresi  <br/> |Tablo S'nin Öğe 1'inde tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |İkinci etki alanı denetleyicisinin statik IP adresi  <br/> |Tablo S'nin Öğe 1'inde tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Dizin eşitleme sunucusunun statik IP adresi  <br/> |Tablo S'nin Öğe 1'inde tanımlanan alt ağın adres alanı için altıncı olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |AD FS sunucuları için iç yük dengeleyicinin statik IP adresi  <br/> |Tablo S'nin Öğe 2'de tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |İlk AD FS sunucusunun statik IP adresi  <br/> |Tablo S'nin Öğe 2'de tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |İkinci AD FS sunucusunun statik IP adresi  <br/> |Tablo S'nin Öğe 2'de tanımlanan alt ağın adres alanı için altıncı olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |İlk web uygulaması ara sunucusunun statik IP adresi  <br/> |Tablo S'nin Öğe 3'te tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |İkinci web uygulaması ara sunucusunun statik IP adresi  <br/> |Tablo S'nin Öğe 3'te tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo I: Sanal ağdaki statik IP adresleri**
  
Başlangıçta sanal ağda etki alanı denetleyicilerini ayarlarken kullanmak istediğiniz şirket içi ağdaki iki Etki Alanı Adı Sistemi (DNS) sunucusu için Tablo D'yi doldurun. Bu listeyi belirlemek için IT departmanınız ile birlikte çalışabilirsiniz.
  
|**Öğe**|**DNS sunucusu kolay adı**|**DNS sunucusu IP adresi**|
|:-----|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo D: Şirket içi DNS sunucuları**
  
Paketleri şirket içi ağdan siteden siteye VPN bağlantısı üzerinden kuruluş ağınıza yönlendirmek için, sanal ağı, kurum içi ağ bağlantınız için tüm erişilebilir konumlarda adres alanlarının listesini (CIDR notasyonunda) bulunan yerel bir ağ ile yapılandırmanız gerekir. Yerel anızı tanımlayan adres alanları listesi benzersiz olmalı ve diğer sanal ağlarda veya diğer yerel ağlarda kullanılan adres alanıyla çakışmalı.
  
Yerel ağ adresi alanları kümesi için, Tablo L'de doldurun. Üç boş girdinin listelenmiş olduğunu, ancak normalde daha fazla girişe ihtiyacınız olduğunu unutmayın. Bu adres alanı listesini belirlemek için, IT departmanınız ile birlikte çalışabilirsiniz.
  
|**Öğe**|**Yerel ağ adresi alanı**|
|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo L: Yerel ağın adres ön ekleri**
  
Şimdi de iş yeriz için federasyon kimlik doğrulamanızı barındırmak üzere Azure altyapısını Microsoft 365.
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni e-Azure PowerShell](/powershell/azure/get-started-azureps). 
  
İlk olarak, bir Azure PowerShell istemini başlatarak hesabınızla oturum açın.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Özel ayarlarınıza bağlı olarak hazır çalıştırlı PowerShell komut blokları oluşturmak için bu Microsoft Excel [kullanın](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

Aşağıdaki komutu kullanarak abonelik adı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Dosyanın daha eski Azure PowerShell, bunun yerine bu komutu kullanın.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Azure aboneliğinizi ayarlayın. Tırnak içindeki her şeyi, karakterlerle birlikte \< and > doğru adla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından, yeni kaynak gruplarını oluşturun. Benzersiz bir kaynak grubu adları kümesi belirlemek için, bu komutu kullanarak varolan kaynak gruplarınızı listelenin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Benzersiz kaynak grubu adları kümesi için aşağıdaki tabloyu doldurun.
  
|**Öğe**|**Kaynak grubu adı**|**Amaç**|
|:-----|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Etki alanı denetleyicileri  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |AD FS sunucuları  <br/> |
|3.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Web uygulaması ara sunucuları  <br/> |
|4.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Altyapı öğeleri  <br/> |
   
 **Tablo R: Kaynak grupları**
  
Bu komutlarla yeni kaynak gruplarınızı oluşturun.
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından, Azure sanal ağına ve alt ağlarını oluşturun.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Ardından, sanal makineleri olan her alt ağ için ağ güvenlik grupları oluşturun. Alt ağ yalıtımnı gerçekleştirmek için, alt ağın ağ güvenlik grubuna izin verilen veya reddedilen belirli trafik türleri için kurallar  ekebilirsiniz.
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Ardından, bu komutları kullanarak siteden siteye VPN bağlantısı için ağ geçitleri oluşturun.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Tek tek kullanıcıların şirket içi kimlik doğrulaması şirket içi kaynaklara güvenmez. Ancak, bu siteden siteye VPN bağlantısı kullanılamaz hale gelirse, VNet'te etki alanı denetleyicileri şirket içi Active Directory Etki Alanı Hizmetleri'ne yapılan kullanıcı hesapları ve gruplar için güncelleştirmeleri almaz. Bunun olmasını sağlamak için, siteden siteye VPN bağlantınız için yüksek kullanılabilirliği yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Yüksek Kullanılabilir Şirket İçi ve VNet-To-VNet Bağlantısı](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Ardından, bu komutun görüntüsünden sanal ağınız için Azure VPN ağ geçidinin genel IPv4 adresini kaydedin:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Ardından, şirket içi VPN cihazınızı Azure VPN ağ geçidine bağlanıyor olacak şekilde yapılandırın. Daha fazla bilgi için bkz [. VPN cihazınızı yapılandırma](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Şirket içi VPN cihazınızı yapılandırmak için aşağıdakilere ihtiyacınız vardır:
  
- Azure VPN ağ geçidinin genel IPv4 adresi.
    
- Siteden siteye VPN bağlantısı için I İleti önceden paylaşılan anahtar (Tablo V - Öğe 5 - Değer sütunu).
    
Ardından, şirket içi ağınız üzerinden sanal ağın adres alanınıza erişilebilir olduğundan emin olun. Bu işlem genellikle VPN cihazınıza sanal ağ adresi alanı için karşılık gelen bir rota ekleniyor ve ardından bu yönlendirmenin, kuruluş ağının yönlendirme altyapısının kalan alanlarına reklam yapılmasıyla yapılır. Bunun nasıl yapacaklarını belirlemek için, IT bölümüyle birlikte çalışma.
  
Ardından, üç kullanılabilirlik kümesi adlarını tanımlayın. Tablo A'ya doldurma. 
  
|**Öğe**|**Amaç**|**Kullanılabilirlik kümesi adı**|
|:-----|:-----|:-----|
|1.  <br/> |Etki alanı denetleyicileri  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS sunucuları  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Web uygulaması ara sunucuları  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo A: Kullanılabilirlik kümeleri**
  
Sanal makineleri aşama 2, 3 ve 4'te  oluştur sırasında bu adlara ihtiyacınız olur.
  
Bu yeni komutlarla yeni kullanılabilirlik Azure PowerShell oluşturun.
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

Bu, bu aşamanın başarıyla tamamlanmasının sonucunda elde edilen yapılandırmadır.
  
**Aşama 1: Projeniz için yüksek kullanılabilirlik federal kimlik doğrulaması için Azure Microsoft 365**

![Azure altyapısıyla Azure'da federasyon Microsoft 365 için yüksek kullanılabilirlik aşaması 1. aşama.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Sonraki adım

Aşama [2'yi kullanma: Etki alanı denetleyicilerini bu](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) iş yükünün yapılandırmasına devam edecek şekilde yapılandırabilirsiniz.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)

[Kimlik Microsoft 365 anlama](deploy-identity-solution-identity-model.md)