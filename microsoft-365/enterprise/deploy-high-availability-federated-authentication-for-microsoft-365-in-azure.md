---
title: Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Özet: Microsoft Azure'da Microsoft 365 aboneliğiniz için yüksek kullanılabilirlik federasyon kimlik doğrulamasını yapılandırın."
ms.openlocfilehash: 64fc02e6ecaa400da6d6130cb9ae630279102fcc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093426"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Azure'da Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulamasını dağıtma

Bu makalede, şu sanal makinelerle Azure altyapı hizmetlerinde Microsoft Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulaması dağıtmaya yönelik adım adım yönergelere bağlantılar bulunur:
  
- İki web uygulaması proxy sunucusu
    
- İki Active Directory Federasyon Hizmetleri (AD FS) (AD FS) sunucusu
    
- İki çoğaltma etki alanı denetleyicisi
    
- Azure AD Bağlan çalıştıran bir dizin eşitleme sunucusu
    
Her sunucu için yer tutucu adları içeren yapılandırma aşağıdadır.
  
**Azure'da Microsoft 365 altyapısı için yüksek kullanılabilirlik federasyon kimlik doğrulaması**

![Azure'da yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulama altyapısının son yapılandırması.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Tüm sanal makineler tek bir şirket içi Azure sanal ağında (VNet) bulunur. 
  
> [!NOTE]
> Tek tek kullanıcıların federasyon kimlik doğrulaması, şirket içi kaynakları kullanmaz. Ancak, şirket içi bağlantılar kullanılamaz duruma gelirse, sanal ağdaki etki alanı denetleyicileri şirket içi Active Directory Etki Alanı Hizmetleri'nde (AD DS) yapılan kullanıcı hesapları ve gruplarında güncelleştirme almaz. Bunun olmamasını sağlamak için, şirket içi bağlantınız için yüksek kullanılabilirlik yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Yüksek Oranda Kullanılabilir Şirket İçi Ve Sanal Ağdan Sanal Ağa Bağlantı](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Belirli bir rol için her sanal makine çifti kendi alt ağı ve kullanılabilirlik kümesindedir.
  
> [!NOTE]
> Bu sanal ağ şirket içi ağa bağlı olduğundan, bu yapılandırma bir yönetim alt ağında sıçrama kutusu veya izleme sanal makinelerini içermez. Daha fazla bilgi için bkz[. N katmanlı mimari için Windows VM'leri çalıştırma](/azure/guidance/guidance-compute-n-tier-vm). 
  
Bu yapılandırmanın sonucu, tüm Microsoft 365 kullanıcılarınız için federasyon kimlik doğrulamasına sahip olmanızdır. Bu kimlik doğrulamasında, Microsoft 365 hesapları yerine oturum açmak için AD DS kimlik bilgilerini kullanabilirler. Federasyon kimlik doğrulama altyapısı, şirket içi uç ağınız yerine Azure altyapı hizmetlerinde daha kolay dağıtılan yedekli bir sunucu kümesi kullanır.
  
## <a name="bill-of-materials"></a>Ürün reçetesi

Bu temel yapılandırma aşağıdaki Azure hizmetleri ve bileşenleri kümesini gerektirir:
  
- Yedi sanal makine
    
- Dört alt ağı olan bir şirket içi ağlar arası sanal ağ
    
- Dört kaynak grubu
    
- Üç kullanılabilirlik kümesi
    
- Bir Azure aboneliği
    
Bu yapılandırma için sanal makineler ve bunların varsayılan boyutları aşağıdadır.
  
|**Öğe**|**Sanal makine açıklaması**|**Azure galeri görüntüsü**|**Varsayılan boyut**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |İlk etki alanı denetleyicisi  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |İkinci etki alanı denetleyicisi  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Bağlan sunucusu  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |İlk AD FS sunucusu  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |İkinci AD FS sunucusu  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |İlk web uygulaması ara sunucusu  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |İkinci web uygulaması proxy sunucusu  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Bu yapılandırmanın tahmini maliyetlerini hesaplamak için bkz. [Azure fiyatlandırma hesaplayıcısı](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Dağıtım aşamaları

Bu iş yükünü aşağıdaki aşamalarda dağıtırsınız:
  
- [1. Aşama: Azure'ı yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md). Kaynak grupları, depolama hesapları, kullanılabilirlik kümeleri ve şirket içi sanal ağ oluşturun.
    
- [2. Aşama: Etki alanı denetleyicilerini yapılandırın](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Çoğaltma AD DS etki alanı denetleyicilerini ve dizin eşitleme sunucusunu oluşturun ve yapılandırın.
    
- [3. Aşama: AD FS sunucularını yapılandırın](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). İki AD FS sunucusunu oluşturun ve yapılandırın.
    
- [4. Aşama: Web uygulaması proxy'lerini yapılandırın](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). İki web uygulaması proxy sunucusunu oluşturun ve yapılandırın.
    
- [5. Aşama: Microsoft 365 için federasyon kimlik doğrulamasını yapılandırın](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Microsoft 365 aboneliğiniz için federasyon kimlik doğrulamasını yapılandırın.
    
Bu makaleler, Azure altyapı hizmetlerinde Microsoft 365 için işlevsel, yüksek kullanılabilirliğe sahip federasyon kimlik doğrulaması oluşturmak üzere önceden tanımlanmış bir mimari için açıklayıcı, aşama aşama kılavuz sağlar. Aşağıdakileri unutmayın:
  
- Deneyimli bir AD FS uygulayıcısıysanız, 3. ve 4. aşamalardaki yönergeleri uyarlamak ve ihtiyaçlarınıza en uygun sunucu kümesini oluşturmaktan çekinmeyin.
    
- Mevcut bir şirket içi sanal ağa sahip mevcut bir Azure hibrit bulut dağıtımınız varsa, 1. ve 2. aşamalardaki yönergeleri uyarlamak veya atlamaktan ve AD FS ile web uygulaması proxy sunucularını uygun alt ağlara yerleştirmekten çekinmeyin.
    
Geliştirme/test ortamı veya bu yapılandırmanın kavram kanıtı oluşturmak için bkz. [Microsoft 365 geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>Sonraki adım

[1. Aşama: Azure'ı yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md) ile bu iş yükünün yapılandırmasını başlatın. 
