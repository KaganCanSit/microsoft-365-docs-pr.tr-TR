---
title: Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Yeni bir abonelikte Microsoft 365 için yüksek kullanılabilirlik federal kimlik doğrulamasını Microsoft Azure.'
ms.openlocfilehash: 70d597663a1920706dbab164dda05b7142f7fd04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984023"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma

Bu makalede, Bu sanal makineler ile Azure altyapı hizmetlerde Microsoft Microsoft 365 için yüksek kullanılabilirlik federal kimlik doğrulaması dağıtımına ilişkin adım adım yönergelerin bağlantıları vardır:
  
- İki web uygulaması ara sunucusu
    
- İki Active Directory Federasyon Hizmetleri (AD FS) sunucusu
    
- İki çoğaltma etki alanı denetleyicisi
    
- Azure AD eşitlemesini çalıştıran bir dizin eşitleme Bağlan
    
Her sunucunun yer tutucu adlarının yer tutucu adlarının yer tutucu olduğu yapılandırma burada ve şekildedir.
  
**Azure'da yeni altyapı için yüksek Microsoft 365 federasyon kimlik doğrulaması**

![Azure'da yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulama altyapısının son yapılandırması.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Tüm sanal makineler tek bir şirket içi Azure sanal ağına (VNet) bulunmaktadır. 
  
> [!NOTE]
> Tek tek kullanıcıların şirket içi kimlik doğrulaması şirket içi kaynaklara güvenmez. Bununla birlikte, şirket içi bağlantı kullanılamaz hale gelirse, VNet'te etki alanı denetleyicileri şirket içi Active Directory Etki Alanı Hizmetleri'ne (AD DS) yapılan kullanıcı hesapları ve gruplar için güncelleştirmeleri almaz. Bunun olmasını sağlamak için, şirket içi bağlantınız için yüksek kullanılabilirliği yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Yüksek Kullanılabilir Şirket İçi ve VNet-To-VNet Bağlantısı](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Belirli bir rol için her sanal makine çifti kendi alt ağ ve kullanılabilirlik kümesindedir.
  
> [!NOTE]
> Bu VNet şirket içi ağa bağlı olduğundan, bu yapılandırma bir yönetim alt ağına atlama kutusu veya izleme sanal makinelerini dahil değildir. Daha fazla bilgi için [bkz. N Windows mimarisi için çalışan sanallar](/azure/guidance/guidance-compute-n-tier-vm). 
  
Bu yapılandırmanın sonucu, tüm Microsoft 365 kullanıcınız için federal kimlik doğrulamanız olacak ve bu kullanıcılar kendi ad DS kimlik bilgilerini kullanarak Microsoft 365. Şirket içi kimlik doğrulama altyapısı, şirket içi uç ağınız yerine Azure altyapı hizmetlerde daha kolay dağıtılan yedekli bir sunucu kümesi kullanır.
  
## <a name="bill-of-materials"></a>Malzeme faturası

Bu temel yapılandırma için aşağıdaki Azure hizmetleri ve bileşenleri kümesi gerekir:
  
- Yedi sanal makine
    
- Dört alt ağ ile bir şirket içi sanal ağ
    
- Dört kaynak grubu
    
- Üç kullanılabilirlik kümesi
    
- Bir Azure aboneliği
    
İşte sanal makineler ve bu yapılandırma için varsayılan boyutları.
  
|**Öğe**|**Sanal makine açıklaması**|**Azure galerisi resmi**|**Varsayılan boyut**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |İlk etki alanı denetleyicisi  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|2.  <br/> |İkinci etki alanı denetleyicisi  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Bağlan sunucusu  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|4.  <br/> |İlk AD FS sunucusu  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|5.  <br/> |İkinci AD FS sunucusu  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|6.  <br/> |İlk web uygulaması ara sunucusu  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
|7.  <br/> |İkinci web uygulaması ara sunucusu  <br/> |Windows Server 2016 Center  <br/> |D2  <br/> |
   
Bu yapılandırmanın tahmini maliyetlerini hesaplamak için bkz. [Azure fiyatlandırma hesaplayıcı](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Dağıtım aşamaları

Bu iş yükünü aşağıdaki aşamalarda dağıtın:
  
- [Aşama 1: Azure'i yapılandırma](high-availability-federated-authentication-phase-1-configure-azure.md). Kaynak grupları, depolama hesapları, kullanılabilirlik kümeleri ve şirket içi sanal ağ oluşturun.
    
- [Aşama 2: Etki alanı denetleyicilerini yapılandırma](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Çoğaltma AD DS etki alanı denetleyicileri ve dizin eşitleme sunucusu oluşturun ve yapılandırabilirsiniz.
    
- [Aşama 3: AD FS sunucularını yapılandırma](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). İki AD FS sunucusu oluşturun ve yapılandırabilirsiniz.
    
- [Aşama 4: Web uygulaması sunucularını yapılandırma](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). İki web uygulaması ara sunucularını oluşturun ve yapılandırabilirsiniz.
    
- [Aşama 5: Posta için federasyon kimlik Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Microsoft 365 aboneliğiniz için federasyon kimlik Microsoft 365 yapılandırma.
    
Bu makalelerde, Azure altyapı hizmetlerde iş için işlevsel, yüksek kullanılabilirlikli bir federasyon kimlik doğrulaması oluşturmak üzere önceden tanımlanmış bir mimariye Microsoft 365, aşama aşama kılavuz sağlanır. Şunları unutmayın:
  
- Deneyimli bir AD FS uygulayıcısıysanız, 3. ve 4. aşamalarda yer alan yönergeleri uyarlamak ve ihtiyaçlarınıza en uygun sunucu kümelerini oluşturmakta özgür olursanız.
    
- Zaten var olan bir şirket içi sanal ağı olan bir Azure karma bulut dağıtımınız varsa, 1. ve 2. aşamalarda verilen yönergeleri uyarlamak veya atlayıp AD FS ve web uygulaması ara sunucularını uygun alt ağlara yer değiştirebilirsiniz.
    
Bu yapılandırmanın bir geliştirme/test ortamı veya kavram kanıtı oluşturması için bkz. Microsoft 365 [geliştirme/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>Sonraki adım

Aşama 1: Azure'la bu iş [yükünün yapılandırmasını başlatma.](high-availability-federated-authentication-phase-1-configure-azure.md) 
