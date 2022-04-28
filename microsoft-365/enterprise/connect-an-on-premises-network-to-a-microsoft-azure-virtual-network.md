---
title: şirket içi ağı Microsoft Azure bir sanal ağa Bağlan
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'Özet: Siteler arası VPN bağlantısıyla Office sunucu iş yükleri için şirket içi Azure sanal ağını yapılandırmayı öğrenin.'
ms.openlocfilehash: 8f9d8336bb50821374ada700613d2ae6142baf6d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094868"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>şirket içi ağı Microsoft Azure bir sanal ağa Bağlan

Şirket içi ağınıza bağlı olan şirket içi Azure sanal ağı, ağınızı Azure altyapı hizmetlerinde barındırılan alt ağları ve sanal makineleri içerecek şekilde genişletir. Bu bağlantı, şirket içi ağınızdaki bilgisayarların Azure'daki sanal makinelere doğrudan erişmesine olanak tanır ve tam tersi de geçerlidir. 

Örneğin, Azure sanal makinesinde çalışan bir dizin eşitleme sunucusunun hesaplarda yapılan değişiklikleri şirket içi etki alanı denetleyicilerinizi sorgulaması ve bu değişiklikleri Microsoft 365 aboneliğinizle eşitlemesi gerekir. Bu makalede, Azure sanal makinelerini barındırmaya hazır bir siteden siteye sanal özel ağ (VPN) bağlantısı kullanarak şirket içi Azure sanal ağının nasıl ayarlanacağı gösterilmektedir.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Şirket içi Azure sanal ağını yapılandırma

Azure'daki sanal makinelerinizin şirket içi ortamınızdan yalıtılması gerekmez. Azure sanal makinelerini şirket içi ağ kaynaklarınıza bağlamak için bir şirket içi Azure sanal ağı yapılandırmanız gerekir. Aşağıdaki diyagramda, Azure'da bir sanal makine ile şirket içi azure sanal ağını dağıtmak için gerekli bileşenler gösterilmektedir.
  
![Siteden siteye VPN bağlantısıyla Microsoft Azure bağlı şirket içi ağ.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
Diyagramda, siteden siteye VPN bağlantısıyla bağlanan iki ağ vardır: şirket içi ağ ve Azure sanal ağı. Siteden siteye VPN bağlantısı:

- Adreslenebilir ve genel İnternet'te bulunan iki uç nokta arasında.
- Şirket içi ağdaki bir VPN cihazı ve Azure sanal ağındaki bir Azure VPN ağ geçidi tarafından sonlandırıldı.

Azure sanal ağı sanal makineleri barındırıyor. Azure sanal ağındaki sanal makinelerden kaynaklanan ağ trafiği VPN ağ geçidine iletilir ve bu da trafiği siteden siteye VPN bağlantısı üzerinden şirket içi ağdaki VPN cihazına iletir. Ardından şirket içi ağın yönlendirme altyapısı trafiği hedefine iletir.

>[!Note]
>Ayrıca, kuruluşunuzla Microsoft ağı arasındaki doğrudan bağlantı olan [ExpressRoute'u](https://azure.microsoft.com/services/expressroute/) da kullanabilirsiniz. ExpressRoute üzerinden gelen trafik genel İnternet üzerinden seyahat etmez. Bu makalede ExpressRoute kullanımı açıklanmaz.
>
  
Azure sanal ağınızla şirket içi ağınız arasında VPN bağlantısını ayarlamak için şu adımları izleyin: 
  
1. **Şirket içi:** Azure sanal ağının adres alanı için şirket içi VPN cihazınızı işaret eden bir şirket içi ağ yolu tanımlayın ve oluşturun.
    
2. **Microsoft Azure:** Siteden siteye VPN bağlantısına sahip bir Azure sanal ağı oluşturun. 
    
3. **Şirket içi:** İnternet Protokolü güvenliğini (IPsec) kullanan VPN bağlantısını sonlandırmak için şirket içi donanım veya yazılım VPN cihazınızı yapılandırın.
    
Siteden siteye VPN bağlantısını kurduktan sonra, sanal ağın alt ağlarına Azure sanal makineleri eklersiniz.
  
## <a name="plan-your-azure-virtual-network"></a>Azure sanal ağınızı planlama
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Önkoşullar
<a name="Prerequisites"></a>

- Bir Azure aboneliği. Azure abonelikleri hakkında bilgi için [Azure'ı Satın Alma sayfasına](https://azure.microsoft.com/pricing/purchase-options/) gidin.
    
- Sanal ağa ve alt ağlarına atanacak kullanılabilir bir özel IPv4 adres alanı ve şimdi ve gelecekte ihtiyaç duyulan sanal makine sayısını karşılamak için yeterli büyüme alanı.
    
- IPsec gereksinimlerini destekleyen siteden siteye VPN bağlantısını sonlandırmak için şirket içi ağınızdaki kullanılabilir bir VPN cihazı. Daha fazla bilgi için bkz [. Siteler arası sanal ağ bağlantıları için VPN cihazları hakkında](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- Yönlendirme altyapınızda yapılan değişiklikler, Azure sanal ağının adres alanına yönlendirilen trafiğin siteden siteye VPN bağlantısını barındıran VPN cihazına iletilmesidir.
    
- Şirket içi ağa bağlı bilgisayarlara ve Azure sanal ağına İnternet erişimi sağlayan bir web proxy'si.
    
### <a name="solution-architecture-design-assumptions"></a>Çözüm mimarisi tasarım varsayımları

Aşağıdaki liste, bu çözüm mimarisi için yapılan tasarım seçimlerini temsil eder. 
  
- Bu çözüm, siteden siteye VPN bağlantısına sahip tek bir Azure sanal ağı kullanır. Azure sanal ağı, birden çok sanal makine içerebilen tek bir alt ağı barındırıyor. 
    
- Şirket içi ağ ile Azure sanal ağı arasında IPsec siteden siteye VPN bağlantısı kurmak için Windows Server 2016 veya Windows Server 2012'da Yönlendirme ve Uzaktan Erişim Hizmeti'ni (RRAS) kullanabilirsiniz. Cisco veya Juniper Networks VPN cihazları gibi diğer seçenekleri de kullanabilirsiniz.
    
- Şirket içi ağda Active Directory Domain Services (AD DS), Etki Alanı Adı Sistemi (DNS) ve ara sunucu gibi ağ hizmetleri hala olabilir. Gereksinimlerinize bağlı olarak, bu ağ kaynaklarından bazılarını Azure sanal ağına yerleştirmek yararlı olabilir.
    
Bir veya daha fazla alt ağa sahip mevcut bir Azure sanal ağı için gereksinimlerinize bağlı olarak, gerekli sanal makinelerinizi barındıracak ek bir alt ağ için kalan adres alanı olup olmadığını belirleyin. Ek bir alt ağ için kalan adres alanınız yoksa, kendi siteden siteye VPN bağlantısı olan ek bir sanal ağ oluşturun.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Azure sanal ağı için yönlendirme altyapısı değişikliklerini planlama

Şirket içi yönlendirme altyapınızı, Azure sanal ağının adres alanını hedefleyen trafiği siteden siteye VPN bağlantısını barındıran şirket içi VPN cihazına iletecek şekilde yapılandırmanız gerekir.
  
Yönlendirme altyapınızı güncelleştirmenin tam yöntemi, yönlendirme bilgilerini nasıl yönettiğinize bağlıdır ve bu da aşağıdakiler olabilir:
  
- El ile yapılandırmaya göre yönlendirme tablosu güncelleştirmeleri.
    
- Yönlendirme Bilgileri Protokolü (RIP) veya Önce En Kısa Yolu Aç (OSPF) gibi yönlendirme protokollerini temel alan yönlendirme tablosu güncelleştirmeleri.
    
Azure sanal ağını hedefleyen trafiğin şirket içi VPN cihazına iletildiğinden emin olmak için yönlendirme uzmanınıza başvurun.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Şirket içi VPN cihazına gelen ve bu cihazdan gelen trafik için güvenlik duvarı kurallarını planlama

VPN cihazınız çevre ağı ile İnternet arasında güvenlik duvarı bulunan bir çevre ağındaysa, siteden siteye VPN bağlantısına izin vermek için güvenlik duvarını aşağıdaki kurallar için yapılandırmanız gerekebilir.
  
- VPN cihazına trafik (İnternet'ten gelen):
    
  - VPN cihazının hedef IP adresi ve IP protokolü 50
    
  - VPN cihazının hedef IP adresi ve UDP hedef bağlantı noktası 500
    
  - VPN cihazının hedef IP adresi ve UDP hedef bağlantı noktası 4500
    
- VPN cihazından gelen trafik (İnternet'e giden):
    
  - VPN cihazının kaynak IP adresi ve IP protokolü 50
    
  - VPN cihazının kaynak IP adresi ve UDP kaynak bağlantı noktası 500
    
  - VPN cihazının kaynak IP adresi ve UDP kaynak bağlantı noktası 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Azure sanal ağının özel IP adresi alanını planlama

Azure sanal ağının özel IP adresi alanı, Azure tarafından sanal ağı barındırmak için kullanılan ve Azure sanal makineleriniz için yeterli adrese sahip en az bir alt ağa sahip adresleri barındırabilmelidir.
  
Alt ağ için gereken adres sayısını belirlemek için, şimdi ihtiyacınız olan sanal makine sayısını sayın, gelecekteki büyüme için tahminde bulunur ve ardından alt ağın boyutunu belirlemek için aşağıdaki tabloyu kullanın.
  
|**Gereken sanal makine sayısı**|**Gereken konak bit sayısı**|**Alt ağın boyutu**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Azure sanal ağınızı yapılandırmaya yönelik planlama çalışma sayfası
<a name="worksheet"> </a>

Sanal makineleri barındırmak için bir Azure sanal ağı oluşturmadan önce, aşağıdaki tablolarda gerekli ayarları belirlemeniz gerekir.
  
Sanal ağın ayarları için Tablo V'yi doldurun.
  
 **Tablo V: Şirket içi sanal ağ yapılandırması**
  
|**Öğe**|**Yapılandırma öğesi**|**Açıklama**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Sanal ağ adı  <br/> |Azure sanal ağına atanacak bir ad (örneğin DirSyncNet).  <br/> |![Satır.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Sanal ağ konumu  <br/> |Sanal ağı (Batı ABD gibi) içerecek Azure veri merkezi.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |VPN cihazı IP adresi  <br/> |VPN cihazınızın İnternet üzerindeki arabiriminin genel IPv4 adresi. Bu adresi belirlemek için BT bölümünüzle birlikte çalışın.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Sanal ağ adres alanı  <br/> |Sanal ağ için adres alanı (tek bir özel adres ön ekinde tanımlanır). Bu adres alanını belirlemek için BT departmanınızla birlikte çalışın. Adres alanı, ağ ön eki biçimi olarak da bilinen Sınıfsız Etki Alanları Arası Yönlendirme (CIDR) biçiminde olmalıdır. 10.24.64.0/20 örnektir.  <br/> |![Satır.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |IPsec paylaşılan anahtarı  <br/> |Siteden siteye VPN bağlantısının her iki tarafının kimliğini doğrulamak için kullanılacak 32 karakterlik rastgele, alfasayısal bir dize. Bu anahtar değerini belirlemek ve güvenli bir konumda depolamak için BT veya güvenlik departmanınızla birlikte çalışın. Alternatif olarak, bkz. [Önceden paylaşılan IPsec anahtarı için rastgele bir dize oluşturma](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![Satır.](../media/Common-Images/TableLine.png) <br/> |
   
Bu çözümün alt ağları için Tablo S'yi doldurun.
  
- İlk alt ağ için Azure ağ geçidi alt ağı için 28 bit adres alanını (/28 ön ek uzunluğuyla) belirleyin. Bu adres alanını belirleme hakkında bilgi için bkz. [Azure sanal ağları için ağ geçidi alt ağ adres alanını hesaplama](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) .
    
- İkinci alt ağ için kolay bir ad, sanal ağ adres alanını temel alan tek bir IP adresi alanı ve açıklayıcı bir amaç belirtin.
    
Sanal ağ adres alanından bu adres alanlarını belirlemek için BT departmanınızla birlikte çalışın. Her iki adres alanı da CIDR biçiminde olmalıdır.
  
 **Tablo S: Sanal ağdaki alt ağlar**
  
|**Öğe**|**Alt ağ adı**|**Alt ağ adres alanı**|**Amaç**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |Azure ağ geçidi tarafından kullanılan alt ağ.  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
Sanal ağdaki sanal makinelerin kullanmasını istediğiniz şirket içi DNS sunucuları için Tablo D'yi doldurun. Her DNS sunucusuna kolay bir ad ve tek bir IP adresi verin. Bu kolay adın DNS sunucusunun ana bilgisayar adı veya bilgisayar adıyla eşleşmesi gerekmez. İki boş girdinin listelendiğini, ancak daha fazla giriş ekleyebileceğinizi unutmayın. Bu listeyi belirlemek için BT bölümünüzle birlikte çalışın.
  
 **Tablo D: Şirket içi DNS sunucuları**
  
|**Öğe**|**DNS sunucusu kolay adı**|**DNS sunucusu IP adresi**|
|:-----|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
   
Paketleri Azure sanal ağından siteden siteye VPN bağlantısı üzerinden kuruluş ağınıza yönlendirmek için, sanal ağı yerel bir ağ ile yapılandırmanız gerekir. Bu yerel ağda, kuruluşunuzun şirket içi ağındaki sanal makinelerin ulaşması gereken tüm konumlar için adres alanlarının (CIDR biçiminde) listesi bulunur. Bu, şirket içi ağdaki tüm konumlar veya bir alt küme olabilir. Yerel ağınızı tanımlayan adres alanlarının listesi benzersiz olmalıdır ve bu sanal ağ veya diğer şirket içi sanal ağlarınız için kullanılan adres alanlarıyla çakışmamalıdır.
  
Yerel ağ adres alanları kümesi için Tablo L'yi doldurun. Üç boş girdinin listelendiğini ancak genellikle daha fazlasına ihtiyacınız olacağını unutmayın. Bu listeyi belirlemek için BT bölümünüzle birlikte çalışın.
  
 **Tablo L: Yerel ağ için adres ön ekleri**
  
|**Öğe**|**Yerel ağ adres alanı**|
|:-----|:-----|
|1.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Satır.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Satır](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Dağıtım yol haritası
<a name="DeploymentRoadmap"> </a>

Şirket içi sanal ağı oluşturma ve Azure'a sanal makine ekleme üç aşamadan oluşur:
  
- 1. Aşama: Şirket içi ağınızı hazırlayın.
    
- 2. Aşama: Azure'da şirket içi sanal ağı oluşturma.
    
- 3. Aşama (İsteğe bağlı): Sanal makineler ekleyin.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>1. Aşama: Şirket içi ağınızı hazırlama
<a name="Phase1"></a>

Şirket içi ağınızı, sanal ağın adres alanına yönelik trafiği şirket içi ağın kenarındaki yönlendiriciye yönlendiren ve sonuçta teslim eden bir yolla yapılandırmanız gerekir. Yolu şirket içi ağınızın yönlendirme altyapısına nasıl ekleyeceğini belirlemek için ağ yöneticinize başvurun.
  
Elde edilen yapılandırmanız aşağıdadır.
  
![Şirket içi ağın, sanal ağın adres alanı için VPN cihazına işaret eden bir yolu olmalıdır.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>2. Aşama: Azure'da şirket içi sanal ağı oluşturma
<a name="Phase2"></a>

İlk olarak bir Azure PowerShell istemi açın. Azure PowerShell yüklemediyseniz bkz. [Azure PowerShell ile Kullanmaya başlayın](/powershell/azure/get-started-azureps).

 
Ardından, bu komutla Azure hesabınızda oturum açın.
  
```powershell
Connect-AzAccount
```

Aşağıdaki komutu kullanarak abonelik adınızı alın.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Bu komutlarla Azure aboneliğinizi ayarlayın. < ve > karakterleri de dahil olmak üzere tırnak içindeki her şeyi doğru abonelik adıyla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından sanal ağınız için yeni bir kaynak grubu oluşturun. Benzersiz bir kaynak grubu adı belirlemek için bu komutu kullanarak mevcut kaynak gruplarınızı listeleyin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Bu komutlarla yeni kaynak grubunuzu oluşturun.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından Azure sanal ağını oluşturacaksınız.
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Elde edilen yapılandırmanız aşağıdadır.
  
![Sanal ağ henüz şirket içi ağa bağlı değil.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Ardından, siteden siteye VPN bağlantısı için ağ geçitlerini oluşturmak için bu komutları kullanın.
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Elde edilen yapılandırmanız aşağıdadır.
  
![Sanal ağın artık bir ağ geçidi vardır.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Ardından, şirket içi VPN cihazınızı Azure VPN ağ geçidine bağlanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [Siteden siteye Azure Sanal Ağ bağlantıları için VPN Cihazları hakkında](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
VPN cihazınızı yapılandırmak için aşağıdakilere ihtiyacınız olacaktır:
  
- Sanal ağınız için Azure VPN ağ geçidinin genel IPv4 adresi. Bu adresi görüntülemek için **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** komutunu kullanın.
    
- Siteden siteye VPN bağlantısı için IPsec önceden paylaşılan anahtarı (Tablo V- Öğe 5 - Değer sütunu).
    
Elde edilen yapılandırmanız aşağıdadır.
  
![Sanal ağ artık şirket içi ağa bağlıdır.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>3. Aşama (İsteğe bağlı): Sanal makine ekleme

Azure'da ihtiyacınız olan sanal makineleri oluşturun. Daha fazla bilgi için bkz. [Azure portal ile Windows sanal makine oluşturma](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Aşağıdaki ayarları kullanın:
  
- **Temel Bilgiler** sekmesinde, sanal ağınızla aynı aboneliği ve kaynak grubunu seçin. Daha sonra sanal makinede oturum açmak için bunlara ihtiyacınız olacaktır. **Örnek ayrıntıları** bölümünde uygun sanal makine boyutunu seçin. Yönetici hesabı kullanıcı adını ve parolasını güvenli bir konuma kaydedin. 
    
- **Ağ** sekmesinde, sanal ağınızın adını ve sanal makineleri barındırmak için alt ağı (GatewaySubnet'i değil) seçin. Diğer tüm ayarları varsayılan değerlerinde bırakın.
    
Yeni sanal makineniz için Adres (A) kayıtlarının eklendiğinden emin olmak için iç DNS'nizi denetleyerek sanal makinenizin DNS'yi doğru kullandığını doğrulayın. İnternet'e erişmek için Azure sanal makinelerinizin şirket içi ağınızın proxy sunucusunu kullanacak şekilde yapılandırılması gerekir. Sunucuda gerçekleştirilecek ek yapılandırma adımları için ağ yöneticinize başvurun.
  
Elde edilen yapılandırmanız aşağıdadır.
  
![Sanal ağ artık şirket içi ağdan erişilebilen sanal makineleri barındırıyor.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Sonraki adım
  
[Microsoft Azure'da Microsoft 365 Dizin Eşitlemesini Dağıtma](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)