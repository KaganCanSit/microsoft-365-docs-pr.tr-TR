---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması 1. Aşama Azure'ı yapılandırma
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Özet: Microsoft 365 için yüksek kullanılabilirlikli federasyon kimlik doğrulamasını barındırmak için Microsoft Azure altyapısını yapılandırın.'
ms.openlocfilehash: f83aa494fcdead8f29810dea06193934b8ef26b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098394"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması 1. Aşama: Azure'ı yapılandırma

Bu aşamada, Azure'da sanal makineleri 2, 3 ve 4. aşamalarda barındıracak kaynak gruplarını, sanal ağı (VNet) ve kullanılabilirlik kümelerini oluşturursunuz. [2. Aşama: Etki alanı denetleyicilerini yapılandırma](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) aşamasına geçmeden önce bu aşamayı tamamlamanız gerekir. Tüm aşamalar için bkz. [Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
Azure şu temel bileşenlerle sağlanmalıdır:
  
- Kaynak grupları
    
- Azure sanal makinelerini barındırmak için alt ağlara sahip bir şirket içi Azure sanal ağı (VNet)
    
- Alt ağ yalıtımı gerçekleştirmek için ağ güvenlik grupları
    
- Kullanılabilirlik kümeleri
    
## <a name="configure-azure-components"></a>Azure bileşenlerini yapılandırma

Azure bileşenlerini yapılandırmaya başlamadan önce aşağıdaki tabloları doldurun. Azure'ı yapılandırma yordamlarında size yardımcı olmak için bu bölümü yazdırın ve gerekli bilgileri yazın veya bu bölümü bir belgeye kopyalayıp doldurun. VNet ayarları için Tablo V'yi doldurun.
  
|**Öğe**|**Yapılandırma ayarı**|**Açıklama**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Sanal ağ adı  <br/> |Sanal ağa atanacak bir ad (örneğin FedAuthNet).  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Sanal ağ konumu  <br/> |Sanal ağı içerecek bölgesel Azure veri merkezi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |VPN cihazı IP adresi  <br/> |VPN cihazınızın İnternet üzerindeki arabiriminin genel IPv4 adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Sanal ağ adres alanı  <br/> |Sanal ağın adres alanı. Bu adres alanını belirlemek için BT departmanınızla birlikte çalışın.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |IPsec paylaşılan anahtarı  <br/> |Siteden siteye VPN bağlantısının her iki tarafının kimliğini doğrulamak için kullanılacak 32 karakterlik rastgele, alfasayısal bir dize. Bu anahtar değerini belirlemek için BT veya güvenlik departmanınızla birlikte çalışın. Alternatif olarak, bkz. [Önceden paylaşılan IPsec anahtarı için rastgele bir dize oluşturma](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo V: Şirket içi sanal ağ yapılandırması**
  
Ardından, bu çözümün alt ağları için Tablo S'yi doldurun. Tüm adres alanları, ağ ön eki biçimi olarak da bilinen Sınıfsız Etki Alanları Arası Yönlendirme (CIDR) biçiminde olmalıdır. 10.24.64.0/20 örnektir.
  
İlk üç alt ağ için, sanal ağ adres alanını temel alan bir ad ve tek bir IP adresi alanı belirtin. Ağ geçidi alt ağı için Azure ağ geçidi alt ağı için 27 bit adres alanını (/27 ön ek uzunluğuyla) aşağıdakilerle belirleyin:
  
1. Sanal ağın adres alanında değişken bitlerini 1 olarak, ağ geçidi alt ağı tarafından kullanılan bitlere kadar ayarlayın, ardından kalan bitleri 0 olarak ayarlayın.
    
2. Elde edilen bitleri ondalık değere dönüştürün ve ön ek uzunluğu ağ geçidi alt ağı boyutuna ayarlanmış bir adres alanı olarak ifade edin.
    
PowerShell komut bloğu ve sizin için bu hesaplamayı gerçekleştiren C# veya Python konsol uygulaması için bkz. [Azure ağ geçidi alt ağları için adres alanı hesaplayıcısı](address-space-calculator-for-azure-gateway-subnets.md) .
  
Sanal ağ adres alanından bu adres alanlarını belirlemek için BT departmanınızla birlikte çalışın.
  
|**Öğe**|**Alt ağ adı**|**Alt ağ adres alanı**|**Amaç**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Active Directory Domain Services (AD DS) etki alanı denetleyicisi ve dizin eşitleme sunucusu sanal makineleri (VM) tarafından kullanılan alt ağ.  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |AD FS VM'leri tarafından kullanılan alt ağ.  <br/> |
|3.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Web uygulaması proxy VM'leri tarafından kullanılan alt ağ.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Azure ağ geçidi VM'leri tarafından kullanılan alt ağ.  <br/> |
   
 **Tablo S: Sanal ağdaki alt ağlar**
  
Ardından, sanal makinelere ve yük dengeleyici örneklerine atanan statik IP adresleri için Tablo I'yi doldurun.
  
|**Öğe**|**Amaç**|**Alt ağda IP adresi**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |İlk etki alanı denetleyicisinin statik IP adresi  <br/> |Tablo S'nin Madde 1'de tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |İkinci etki alanı denetleyicisinin statik IP adresi  <br/> |Tablo S'nin Madde 1'inde tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Dizin eşitleme sunucusunun statik IP adresi  <br/> |Tablo S'nin Madde 1'inde tanımlanan alt ağın adres alanı için altıncı olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |AD FS sunucuları için iç yük dengeleyicinin statik IP adresi  <br/> |Tablo S'nin Madde 2'de tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |İlk AD FS sunucusunun statik IP adresi  <br/> |Tablo S'nin Madde 2'de tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |İkinci AD FS sunucusunun statik IP adresi  <br/> |Tablo S'nin Madde 2'sinde tanımlanan alt ağın adres alanı için altıncı olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |İlk web uygulaması proxy sunucusunun statik IP adresi  <br/> |Tablo S'nin Madde 3'te tanımlanan alt ağın adres alanı için dördüncü olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |İkinci web uygulaması proxy sunucusunun statik IP adresi  <br/> |Tablo S'nin Madde 3'te tanımlanan alt ağın adres alanı için beşinci olası IP adresi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo I: Sanal ağdaki statik IP adresleri**
  
Şirket içi ağınızda ilk olarak sanal ağınızdaki etki alanı denetleyicilerini ayarlarken kullanmak istediğiniz iki Etki Alanı Adı Sistemi (DNS) sunucusu için Tablo D'yi doldurun. Bu listeyi belirlemek için BT departmanınızla birlikte çalışın.
  
|**Öğe**|**DNS sunucusu kolay adı**|**DNS sunucusu IP adresi**|
|:-----|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo D: Şirket içi DNS sunucuları**
  
Paketleri şirket içi ağdan kuruluş ağınıza siteden siteye VPN bağlantısı üzerinden yönlendirmek için, kuruluşunuzun şirket içi ağındaki tüm ulaşılabilir konumlar için adres alanlarının (CIDR gösteriminde) listesini içeren yerel bir ağ ile sanal ağı yapılandırmanız gerekir. Yerel ağınızı tanımlayan adres alanları listesi benzersiz olmalı ve diğer sanal ağlar veya diğer yerel ağlar için kullanılan adres alanıyla çakışmamalıdır.
  
Yerel ağ adres alanları kümesi için Tablo L'yi doldurun. Üç boş girdinin listelendiğini ancak genellikle daha fazlasına ihtiyacınız olacağını unutmayın. Bu adres alanları listesini belirlemek için BT bölümünüzle birlikte çalışın.
  
|**Öğe**|**Yerel ağ adres alanı**|
|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo L: Yerel ağ için adres ön ekleri**
  
Şimdi Microsoft 365 için federasyon kimlik doğrulamanızı barındıracak Azure altyapısını oluşturmaya başlayalım.
  
> [!NOTE]
> Aşağıdaki komut kümeleri Azure PowerShell en son sürümünü kullanır. Bkz. [Azure PowerShell ile Kullanmaya başlayın](/powershell/azure/get-started-azureps). 
  
İlk olarak bir Azure PowerShell istemi başlatın ve hesabınızda oturum açın.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Özel ayarlarınıza göre çalışmaya hazır PowerShell komut blokları oluşturmak için bu [Microsoft Excel yapılandırma çalışma kitabını](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) kullanın. 

Aşağıdaki komutu kullanarak abonelik adınızı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure PowerShell'ın eski sürümleri için bunun yerine bu komutu kullanın.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Azure aboneliğinizi ayarlayın. Karakterler de dahil olmak üzere \< and > tırnak içindeki her şeyi doğru adla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından yeni kaynak gruplarını oluşturun. Benzersiz bir kaynak grubu adı kümesini belirlemek için, mevcut kaynak gruplarınızı listelemek için bu komutu kullanın.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Benzersiz kaynak grubu adları kümesi için aşağıdaki tabloyu doldurun.
  
|**Öğe**|**Kaynak grubu adı**|**Amaç**|
|:-----|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Etki alanı denetleyicileri  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |AD FS sunucuları  <br/> |
|3.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Web uygulaması proxy sunucuları  <br/> |
|4.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Altyapı öğeleri  <br/> |
   
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

Ardından Azure sanal ağını ve alt ağlarını oluşturacaksınız.
  
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

Ardından, sanal makineleri olan her alt ağ için ağ güvenlik grupları oluşturursunuz. Alt ağ yalıtımı gerçekleştirmek için, bir alt ağın ağ güvenlik grubuna izin verilen veya reddedilen belirli trafik türleri için kurallar ekleyebilirsiniz.
  
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

Ardından, siteden siteye VPN bağlantısı için ağ geçitlerini oluşturmak için bu komutları kullanın.
  
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
> Tek tek kullanıcıların federasyon kimlik doğrulaması, şirket içi kaynakları kullanmaz. Ancak, bu siteden siteye VPN bağlantısı kullanılamaz hale gelirse, VNet'teki etki alanı denetleyicileri şirket içi Active Directory Etki Alanı Hizmetleri'nde yapılan kullanıcı hesapları ve gruplarında güncelleştirmeleri almaz. Bunun olmamasını sağlamak için siteden siteye VPN bağlantınız için yüksek kullanılabilirlik yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Yüksek Oranda Kullanılabilir Şirket İçi Ve Sanal Ağdan Sanal Ağa Bağlantı](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Ardından, şu komutun görüntüsünden sanal ağınız için Azure VPN ağ geçidinin genel IPv4 adresini kaydedin:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Ardından, şirket içi VPN cihazınızı Azure VPN ağ geçidine bağlanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [VPN cihazınızı yapılandırma](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Şirket içi VPN cihazınızı yapılandırmak için aşağıdakilere ihtiyacınız olacaktır:
  
- Azure VPN ağ geçidinin genel IPv4 adresi.
    
- Siteden siteye VPN bağlantısı için IPsec önceden paylaşılan anahtarı (Tablo V - Öğe 5 - Değer sütunu).
    
Ardından, sanal ağın adres alanına şirket içi ağınızdan erişilebilir olduğundan emin olun. Bu genellikle VPN cihazınıza sanal ağ adres alanına karşılık gelen bir yol ekleyerek ve ardından bu yolu kuruluş ağınızın yönlendirme altyapısının geri kalanına tanıtarak yapılır. Bunun nasıl yapılacağını belirlemek için BT bölümünüzle birlikte çalışın.
  
Ardından üç kullanılabilirlik kümesinin adlarını tanımlayın. A Tablosunu doldurun. 
  
|**Öğe**|**Amaç**|**Kullanılabilirlik kümesi adı**|
|:-----|:-----|:-----|
|1.  <br/> |Etki alanı denetleyicileri  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS sunucuları  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Web uygulaması proxy sunucuları  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tablo A: Kullanılabilirlik kümeleri**
  
Sanal makineleri 2, 3 ve 4. aşamalarda oluştururken bu adlara ihtiyacınız olacaktır.
  
Bu Azure PowerShell komutlarıyla yeni kullanılabilirlik kümelerini oluşturun.
  
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

Bu, bu aşamanın başarıyla tamamlanmasından kaynaklanan yapılandırmadır.
  
**1. Aşama: Microsoft 365 için yüksek kullanılabilirliğe yönelik federasyon kimlik doğrulaması için Azure altyapısı**

![Azure altyapısıyla Azure'da federasyon kimlik doğrulaması Microsoft 365 yüksek kullanılabilirlik aşamasının 1. aşaması.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Sonraki adım

2. Aşama: Bu iş yükünün yapılandırmasına devam etmek için [etki alanı denetleyicilerini yapılandırın](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) .
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)

[Microsoft 365 kimlik modellerini anlama](deploy-identity-solution-identity-model.md)