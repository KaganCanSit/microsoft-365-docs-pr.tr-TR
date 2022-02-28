---
title: Bağlan ağına şirket içi ağı Microsoft Azure ağı
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Siteden siteye VPN bağlantısı olan bir sunucu iş yüklerinin Office şirket içi Azure sanal ağın nasıl yapılandırıldığından emin olun.'
ms.openlocfilehash: 5ba05dd432a6f6fe323e9d9cfd2542dcb1cc7efb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985692"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Bağlan ağına şirket içi ağı Microsoft Azure ağı

Şirket içi bir Azure sanal ağı, şirket içi ağınıza bağlanarak, ağın Azure altyapı hizmetlarında barındırılan alt ağları ve sanal makineleri içerecek şekilde genişletebilirsiniz. Bu bağlantı, şirket içi ağınızdaki bilgisayarların Azure'daki sanal makinelere (ve tersine) doğrudan erişmelerine olanak sağlar. 

Örneğin, Azure sanal makinesi üzerinde çalışan bir dizin eşitleme sunucusunun hesaplarda yapılan değişiklikler için şirket içi etki alanı denetleyicilerinizi sorgulaması ve bu değişiklikleri Microsoft 365 gerekir. Bu makalede, Azure sanal makinelerini barındırmaya hazır bir siteden siteye sanal özel ağ (VPN) bağlantısı kullanarak şirket içi Azure sanal ağının nasıl ayar olduğu açıklanmıştır.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Şirket içi Azure sanal ağına yapılandırma

Azure'daki sanal makinelerinizi şirket içi ortamınıza göre yalıtılmış yapmak zorunda değildir. Azure sanal makinelerini şirket içi ağ kaynaklarınıza bağlamak için, şirket içi bir Azure sanal ağı yapılandırmanız gerekir. Aşağıdaki diyagramda, Azure'da sanal bir makineyle şirket içi Azure sanal ağına dağıtım yapmak için gerekli bileşenler gösterir.
  
![İnternet'e Microsoft Azure siteden siteye VPN bağlantısıyla bağlanan şirket içi ağ.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
Diyagramda, siteden siteye VPN bağlantısıyla bağlı iki ağ vardır: şirket içi ağ ve Azure sanal ağı. Siteden siteye VPN bağlantısı:

- Adreslenebilir olan ve genel İnternet'e bulunan iki uç nokta arasında.
- Şirket içi ağ üzerinde bir VPN cihazı ve Azure sanal ağı üzerinde bir Azure VPN ağ geçidi tarafından sonlandırılır.

Azure sanal ağ ana bilgisayarları sanal makinelerini. Azure sanal ağının sanal makinelerinden kaynaklanan ağ trafiği VPN ağ geçidine iletildi ve bu da trafiği siteden siteye VPN bağlantısı üzerinden şirket içi ağda VPN cihazına iletir. Bundan sonra, şirket içi ağın yönlendirme altyapısı trafiği hedefine iletir.

>[!Note]
>Ayrıca, kurum ile Microsoft ağı arasındaki doğrudan bağlantı olan [ExpressRoute'u](https://azure.microsoft.com/services/expressroute/) da kullanabilirsiniz. ExpressRoute üzerinden gelen trafik genel İnternet üzerinden seyahat etmez. Bu makalede ExpressRoute'un kullanımı açıklanmaz.
>
  
Azure sanal ağınız ile şirket içi ağınız arasında VPN bağlantısını ayarlamak için şu adımları izleyin: 
  
1. **Şirket içi:** Şirket içi VPN cihazınızı yönlendiren Azure sanal ağının adres alanı için bir şirket içi ağ yolu tanımlayın ve oluşturun.
    
2. **Microsoft Azure:** Siteden siteye VPN bağlantısıyla Azure sanal ağı oluşturun. 
    
3. **Şirket içi:** Şirket içi donanım veya yazılım VPN cihazınızı, İnternet Protokolü güvenliği (I Toplantısı) kullanan VPN bağlantısını sonlandıracak şekilde yapılandırın.
    
Siteden siteye VPN bağlantısını kurduğuktan sonra, sanal ağın alt ağlara Azure sanal makinelerini eklersiniz.
  
## <a name="plan-your-azure-virtual-network"></a>Azure sanal anızı planlama
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Önkoşullar
<a name="Prerequisites"></a>

- Bir Azure aboneliği. Azure abonelikleri hakkında bilgi için [Azure'i Satın Alma sayfasına gidin](https://azure.microsoft.com/pricing/purchase-options/).
    
- Sanal ağa ve alt ağlarına atamak için kullanılabilir özel IPv4 adres alanı; şu anda ve gelecekte gereken sanal makine sayısını karşılamak için yeterli büyüme alanı.
    
- I Toplantısı gereksinimlerini destekleyen siteden siteye VPN bağlantısını sonlandırmak için şirket içi ağnızda kullanılabilir bir VPN cihazı. Daha fazla bilgi için bkz [. Siteden siteye sanal ağ bağlantıları için VPN cihazları hakkında](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- Azure sanal ağının adres alanlarına yönlendirilen trafiğin siteden siteye VPN bağlantısını barındıran VPN cihazına yönlendirilene kadar, yönlendirme altyapıda yapılan değişiklikler.
    
- Şirket içi ağa bağlı bilgisayarlara ve Azure sanal ağının İnternet'e erişimine olanak veren bir web ara sunucusu.
    
### <a name="solution-architecture-design-assumptions"></a>Çözüm mimarisi tasarım varsayımları

Aşağıdaki liste, bu çözüm mimarisi için yapılan tasarım seçimlerini temsil eder. 
  
- Bu çözüm, siteden siteye VPN bağlantısı olan tek bir Azure sanal ağı kullanır. Azure sanal ağı, birden çok sanal makine içer dayandıran tek bir alt ağ barındırr. 
    
- Windows Server 2016 veya Windows Server 2012'ta, şirket içi ağ ile Azure sanal ağı arasında I Toplantısı yerinde VPN bağlantısı kurmak için Yönlendirme ve Uzaktan Erişim Hizmeti'ne (RRAS) kullanabilirsiniz. Cisco veya Juniper Networks VPN cihazları gibi diğer seçenekleri de kullanabilirsiniz.
    
- Şirket içi ağın Active Directory Etki Alanı Hizmetleri (AD DS), Etki Alanı Adı Sistemi (DNS) ve ara sunucu gibi ağ hizmetleri olabilir. Gereksinimlerinize bağlı olarak, bu ağ kaynaklardan bazılarının Azure sanal ağına yer olması faydalı olabilir.
    
Bir veya birden çok alt ağ ile mevcut Azure sanal ağı için, gereksinimlerinize bağlı olarak gerekli sanal makinelerinizi barındırmak üzere ek bir alt ağ için kalan adres alanı olup olmadığını belirler. Ek alt ağ için kalan adres alanınız yoksa, kendi siteden siteye VPN bağlantısı olan ek bir sanal ağ oluşturun.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Azure sanal ağı için yönlendirme altyapısı değişikliklerini planlama

Azure sanal ağının adres alanı için yönlendirilen trafiği siteden siteye VPN bağlantısını barındıran şirket içi VPN cihazına ilet etmek için şirket içi yönlendirme altyapınızı yapılandırmanız gerekir.
  
Yönlendirme altyapınızı tam olarak güncelleştirme yöntemi yönlendirme bilgilerini nasıl yönet olara bağlı olarak değişir; şöyle olabilir:
  
- El ile yapılandırmaya dayalı olarak tablo güncelleştirmelerini yönlendirme.
    
- Yönlendirme tablosu güncelleştirmeleri, Yönlendirme Bilgileri Protokolü (ATL) veya Önce En Kısa Yolu Aç (OSPF) gibi yönlendirme protokollerine dayalıdır.
    
Azure sanal ağına uygun trafiğin şirket içi VPN cihazına iletildikten emin olmak için yönlendirme uzmanınıza danışın.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Şirket içi VPN cihazından gelen ve gelen trafik için güvenlik duvarı kurallarını planlama

VPN cihazınız çevre ağı ile İnternet arasında güvenlik duvarı bulunan bir çevre ağına bağlı bir çevre ağına sahipse, siteden siteye VPN bağlantısına izin vermek için aşağıdaki kurallar için güvenlik duvarını yapılandırmanız gerekebilir.
  
- VPN cihazına trafik (İnternet'den gelen):
    
  - VPN cihazı ve IP protokolü 50 hedef IP adresi
    
  - VPN cihazı ve UDP hedef bağlantı noktası 500 için hedef IP adresi
    
  - VPN cihazı ve UDP hedef bağlantı noktası 4500'in hedef IP adresi
    
- VPN cihazından trafik (İnternet'e giden):
    
  - VPN cihazı ve IP protokolü 50'nin kaynak IP adresi
    
  - VPN cihazı ve UDP kaynak bağlantı noktası 500'in kaynak IP adresi
    
  - VPN cihazı ve UDP kaynak bağlantı noktası 4500'in kaynak IP adresi
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Azure sanal ağının özel IP adresi alanı için planlama

Azure sanal ağının özel IP adresi alanı, sanal ağı barındırmak için Azure tarafından kullanılan adreslerin ve Azure sanal makineniz için yeterli adreslerin olduğu en az bir alt ağ ile barındırmalıdır.
  
Alt ağ için gereken adres sayısını belirlemek için, şu anda ihtiyacınız olan sanal makine sayısını hesap olun, gelecekteki büyüme tahminini yapın ve alt ağın boyutunu belirlemek için aşağıdaki tabloyu kullanın.
  
|**Gereken sanal makine sayısı**|**Gereken ana bilgisayar bitlerinin sayısı**|**Alt ağın boyutu**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Azure sanal anızı yapılandırmak için planlama çalışma sayfası
<a name="worksheet"> </a>

Sanal makineleri barındırmak üzere bir Azure sanal ağı oluşturmadan önce, aşağıdaki tablolarda gereken ayarları belirlemeniz gerekir.
  
Sanal ağın ayarları için, Tablo V'ye doldurun.
  
 **Tablo V: Şirket içi sanal ağ yapılandırması**
  
|**Öğe**|**Yapılandırma öğesi**|**Açıklama**|**Değer**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Sanal ağ adı  <br/> |Azure sanal ağına (örneğin DirSyncNet) atanacak ad.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Sanal ağ konumu  <br/> |Sanal ağı içeren Azure veri merkezi (Batı ABD gibi).  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |VPN cihazı IP adresi  <br/> |İnternet'te VPN cihazınızın arabiriminin genel IPv4 adresi. Bu adresi belirlemek için IT departmanınız ile birlikte çalışabilirsiniz.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Sanal ağ adresi alanı  <br/> |Sanal ağın adres alanı (tek bir özel adres öneki içinde tanımlanmıştır). Bu adres alanı belirlemek için IT departmanınız ile birlikte çalışabilirsiniz. Adres alanı, ağ öneki biçimi olarak da bilinen Sınıfsız Etki Alanı Yönlendirmesi (CIDR) biçiminde olmalıdır. Örnek 10.24.64.0/20.  <br/> |![çizgi.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |I Yer paylaşım anahtarı  <br/> |Siteden siteye VPN bağlantısının her iki yanında da kimlik doğrulaması yapmak için kullanılacak 32 karakterlik rastgele, alfasayısal dize. Bu anahtar değerini belirlemek için IT veya güvenlik departmanınız ile birlikte çalışabilirsiniz ve sonra bu değeri güvenli bir konumda depolarız. Alternatif olarak bkz [. Önceden paylaşılan bir I İleti anahtarı için rastgele dize oluşturma](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![çizgi.](../media/Common-Images/TableLine.png) <br/> |
   
Bu çözümün alt ağları için Tablo S'de doldurun.
  
- İlk alt ağ için, Azure ağ geçidi alt ağı için 28 bit adres alanı (/28 ön ek uzunluğuna sahip) belirler. Bu [adres alanı belirleme hakkında bilgi için bkz. Azure sanal](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) ağları için ağ geçidi alt ağ adres alanı hesaplama.
    
- İkinci alt ağ için kolay bir ad, sanal ağ adresi alanına dayalı tek bir IP adresi alanı ve açıklayıcı bir amaç belirtin.
    
Sanal ağ adresi bölümünden bu adres boşluklarını belirlemek için, IT departmanınız ile birlikte çalışabilirsiniz. Her iki adres alanı da CIDR biçiminde olmalıdır.
  
 **Tablo S: Sanal ağdaki alt ağlar**
  
|**Öğe**|**Alt ağ adı**|**Alt ağ adres alanı**|**Amaç**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |Azure ağ geçidi tarafından kullanılan alt ağ.  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
Sanal ağdaki sanal makinelerin kullanmasını istediğiniz şirket içi DNS sunucuları için, Tablo D'yi doldurun. Her DNS sunucusuna kolay bir ad ve tek bir IP adresi girin. Bu kolay adın, DNS sunucusunun ana bilgisayar adıyla veya bilgisayar adıyla eşleşmesi gerek değildir. İki boş girdinin listelenmiş olduğunu, ancak daha fazla giriş ekley note. Bu listeyi belirlemek için IT departmanınız ile birlikte çalışabilirsiniz.
  
 **Tablo D: Şirket içi DNS sunucuları**
  
|**Öğe**|**DNS sunucusu kolay adı**|**DNS sunucusu IP adresi**|
|:-----|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
   
Paketleri Azure sanal ağına, siteden siteye VPN bağlantısı üzerinden kuruluş ağınıza yönlendirmek için, sanal ağı yerel ağ üzerinden yapılandırmanız gerekir. Bu yerel ağın, sanal ağda sanal makinelerin ulaş olması gereken tüm şirket içi ağ konumlarının adres alanlarının listesi vardır (CIDR biçiminde). Bu, şirket içi ağın tüm konumları veya bir alt küme olabilir. Yerel anızı tanımlayan adres alanları listesi benzersiz olmalı ve bu sanal ağ için kullanılan adres alanlarıyla veya diğer şirket içi sanal ağlarda kullanılan adres alanlarıyla çakışmalı.
  
Yerel ağ adresi alanları kümesi için, Tablo L'de doldurun. Üç boş girdinin listelenmiş olduğunu, ancak normalde daha fazla girişe ihtiyacınız olduğunu unutmayın. Bu listeyi belirlemek için IT departmanınız ile birlikte çalışabilirsiniz.
  
 **Tablo L: Yerel ağın adres ön ekleri**
  
|**Öğe**|**Yerel ağ adresi alanı**|
|:-----|:-----|
|1.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![çizgi.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![çizgi](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Dağıtım yol haritası
<a name="DeploymentRoadmap"> </a>

Şirket içi sanal ağı oluşturma ve Azure'da sanal makineler ekleme üç aşamadan oluşur:
  
- Aşama 1: Şirket içi ağına hazırlama.
    
- Aşama 2: Azure'da şirket içi sanal ağı oluşturun.
    
- Aşama 3 (İsteğe bağlı): Sanal makineler ekleme.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Aşama 1: Şirket içi ağına hazırlanma
<a name="Phase1"></a>

Şirket içi anızı, sanal ağın adres alanı için hedef alan trafiği şirket içi ağın kenarından yönlendiriciye yönlendiren ve sonunda teslim edecek bir rotayla yapılandırmanız gerekir. Yönlendirmenin, şirket içi ağ yönlendirme altyapısına nasıl ek gerekle ilgili olduğunu belirlemek için ağ yöneticinize başvurun.
  
Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Şirket içi ağın, sanal ağın adres alanı için VPN cihazına doğru bir yönlendirmesi olmalıdır.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Aşama 2: Azure'da şirket içi sanal ağı oluşturma
<a name="Phase2"></a>

İlk olarak bir soru Azure PowerShell açın. Bu güncelleştirmeleri yüklememiş Azure PowerShell, Bkz[. Azure PowerShell](/powershell/azure/get-started-azureps).

 
Ardından, bu komutla Azure hesabınızla oturum açın.
  
```powershell
Connect-AzAccount
```

Aşağıdaki komutu kullanarak abonelik adı alın.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Bu komutlarla Azure aboneliğinizi ayarlayın. Tırnak içindeki her şeyi, tırnak içindeki < > ve doğru abonelik adıyla değiştirin.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Ardından, sanal ağınız için yeni bir kaynak grubu oluşturun. Benzersiz bir kaynak grubu adı belirlemek için, bu komutu kullanarak var olan kaynak gruplarınızı listelenin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Bu komutlarla yeni kaynak grubunızı oluşturun.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından, Azure sanal ağına sahip olursanız.
  
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

Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Sanal ağ henüz şirket içi ağa bağlı değildir.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Ardından, bu komutları kullanarak siteden siteye VPN bağlantısı için ağ geçitleri oluşturun.
  
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

Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Sanal ağın artık bir ağ geçidi var.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Ardından, şirket içi VPN cihazınızı Azure VPN ağ geçidine bağlanıyor olacak şekilde yapılandırın. Daha fazla bilgi için bkz [. Siteden siteye Azure Sanal Ağ bağlantıları için VPN Cihazları hakkında](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
VPN cihazınızı yapılandırmak için aşağıdakilere ihtiyacınız vardır:
  
- Sanal ağınız için Azure VPN ağ geçidinin genel IPv4 adresi. Bu adresi görüntülemek **için Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** komutunu kullanın.
    
- Siteden siteye VPN bağlantısı için I İleti önceden paylaşılan anahtar (Tablo V- Öğe 5 - Değer sütunu).
    
Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Sanal ağ artık şirket içi ağa bağlanır.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Aşama 3 (İsteğe bağlı): Sanal makineler ekleme

Azure'da ihtiyacınız olan sanal makineleri oluşturun. Daha fazla bilgi için [bkz. Azure Windows sanal makine oluşturma](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Aşağıdaki ayarları kullanın:
  
- Temel **Bilgiler sekmesinde** , sanal ağınız ile aynı aboneliği ve kaynak grubunu seçin. Sanal makinede oturum a giriş yapmak için daha sonra bunlara ihtiyacınız olacak. Örnek **ayrıntıları bölümünde** , uygun sanal makine boyutunu seçin. Yönetici hesabının kullanıcı adını ve parolasını güvenli bir konuma yazın. 
    
- Ağ sekmesinde **,** sanal ağ adının ve barındırma sanal makineleri için alt ağın adını seçin (GatewaySubnet'te değil). Diğer tüm ayarları varsayılan değerlerinde bırakın.
    
Yeni sanal makineniz için Adres (A) kayıtlarının eklendi olduğundan emin olmak için iç DNS'nizi kontrol ederek, sanal makinenizin DNS'yi doğru şekilde çalıştığını doğrulayın. İnternet'e erişmek için, Azure sanal makinenizin şirket içi ağın ara sunucusunu kullanmak üzere yapılandırılması gerekir. Sunucuda gerçekleştirecek ek yapılandırma adımları için ağ yöneticinize başvurun.
  
Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Sanal ağ artık şirket içi ağdan erişilebilen sanal makineler barındırıyor.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Sonraki adım
  
[Dizin Microsoft 365 Eşitlemeyi Başka Bir Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)