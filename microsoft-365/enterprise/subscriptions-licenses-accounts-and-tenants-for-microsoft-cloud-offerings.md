---
title: Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: Microsoft bulut tekliflerinin tamamladığı kuruluşların, aboneliklerin, lisansların, kullanıcı hesaplarının ve kiracıların ilişkilerini anlıyoruz.
ms.openlocfilehash: c8f6fca0a5c9ce56c3565612e0de9b40d6e0254c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986716"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar

Microsoft, bulut tekliflarında kimliklerin ve faturalamanın tutarlı kullanımı için kuruluşlar, abonelikler, lisanslar ve kullanıcı hesapları hiyerarşisi sağlar:
  
- Microsoft 365 ve Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Hiyerarşinin öğeleri

Hiyerarşinin öğeleri şöyledir:
  
### <a name="organization"></a>Kuruluş

Kuruluş, Microsoft bulut tekliflerini kullanan, genellikle bir veya birden çok genel Etki Alanı Adı Sistemi (DNS) etki alanı adıyla tanımlanan, örneğin bir işletmeyi temsil contoso.com. Kuruluş, abonelikler için bir kapsayıcıdır.
  
### <a name="subscriptions"></a>Abonelikler

Abonelik, microsoft ile bir veya birden çok Microsoft bulut platform veya hizmeti kullanan ve kullanıcı başına lisans ücretine veya bulut tabanlı kaynak kullanımına göre tahakkuk eden bir sözleşmedir. 

- Microsoft'un Hizmet Olarak Yazılım (SaaS) tabanlı bulut teklifleri (Microsoft 365 ve Dynamics 365) kullanıcı başına lisans ücretidir. 
- Hizmet Olarak Microsoft Platformu (PaaS) ve Hizmet Olarak Altyapı (IaaS) bulut teklifleri (Azure) ücreti bulut kaynak kullanımına göre ücret alır.
 
Deneme aboneliğini de kullanabilirsiniz, ancak belirli bir süre veya tüketim ücretlerinin ardından abonelik sona erer. Deneme aboneliğini ücretli bir aboneliğe dönüştürebilirsiniz.
  
Kuruluşlar, Microsoft'un bulut teklifleri için birden çok aboneliği olabilir. Şekil 1, birden çok Azure aboneliğine Microsoft 365 Dynamics 365 aboneliğine ve birden çok Azure aboneliğine sahip tek bir kuruluşu gösterir.

**Şekil 1: Bir kuruluş için birden çok abonelik örneği**

![Microsoft'un bulut teklifleri için birden çok aboneliği olan örnek bir kuruluş.](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Lisanslar

Microsoft'un SaaS bulut teklifleri için lisans, belirli bir kullanıcı hesabının bulut tekliflerini kullanmasını sağlar. Aboneliğinizin bir parçası olarak sabit bir aylık ücret tahsil edildi. Yöneticiler abonelikte tek tek kullanıcı hesaplarına lisans atar. Şekil 2'de yer alan örnekte, Contoso Corporation'ın 100 lisansı olan bir Microsoft 365 E5 aboneliği vardır ve bu abonelik en çok 100 kullanıcı hesabının en çok Microsoft 365 E5 kullanımına olanak sağlar.
  
**Şekil 2: Kuruluşun SaaS tabanlı abonelikleri içindeki lisanslar**

![Microsoft'un SaaS tabanlı bulut teklifleri için abonelikler içinde birden çok lisans örneği.](../media/Subscriptions/Subscriptions-Fig2.png)

>[!Note]
>En iyi güvenlik uygulaması, yönetim işlevleri için belirli roller atanmış ayrı kullanıcı hesapları kullanmaktır. Bu adanmış yönetici hesaplarına, yönetecekleri bulut hizmetleri için lisans atanmaları gerekmektedir. Örneğin, SharePoint yönetici hesabına lisans atamanız Microsoft 365.
>

Azure PaaS tabanlı bulut hizmetleri için, yazılım lisansları hizmet fiyatlarında yerleşik olarak yer alır.
  
Azure IaaS tabanlı sanal makinelerde, sanal makine görüntüsü üzerinde yüklü yazılım veya uygulamayı kullanmak için ek lisans gerekebilir. Bazı sanal makine görüntülerinin lisanslı yazılım sürümleri yüklüdir ve bu ücret sunucu için dakika başına ücrete dahildir. 2014 ve 2016'da SQL Server makine SQL Server örnekleridir. 
  
Bazı sanal makine görüntülerinin uygulamaların deneme sürümleri yüklüdir ve deneme süresi dışında kullanmak için ek yazılım uygulaması lisansları gerekir. Örneğin, SharePoint Server 2016 Deneme sanal makine görüntüsü, SharePoint Server 2016'nın deneme sürümünü içerir. SharePoint Server 2016'nın deneme süresinin sona erme tarihinden sonra da kullanmaya devam etmek için Microsoft'tan SharePoint Server 2016 lisansı ve istemci lisansları satın alısınız. Bu ücretler Azure aboneliğinden ayrıdır ve sanal makinenin çalıştırı için dakikalık ücret uygulanır.
  
### <a name="user-accounts"></a>Kullanıcı hesapları

Microsoft'un tüm bulut tekliflerinin kullanıcı hesapları, kullanıcı hesapları ve grupları Azure Active Directory bir kiracıda (Azure AD) depolanır. Bir Azure AD kiracısı, sunucu tabanlı bir hizmet olan Azure AD Bağlan kullanılarak var olan Active Directory Etki Alanı Hizmetleri (AD DS) Windows hesaplarıyla eşitlenir. Bu, dizin eşitlemesi olarak bilinir.
  
Şekil 3, kuruluşun hesaplarını içeren ortak bir Azure AD kiracısı kullanan birden çok abonelik örneği gösterir.
  
**Şekil 3: Aynı Azure AD kiracısı kullanan bir kuruluşun birden çok aboneliği**

![Aynı Azure AD kiracısı kullanan, birden çok aboneliği olan örnek bir kuruluş.](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Kiracılar

SaaS bulut teklifleri için kiracı, bulut hizmetleri sağlayan sunucuların bulunduğu bölgesel bir konumdır. Örneğin, Contoso Corporation, Paris merkezinde 15.000 çalışan için Microsoft 365, EMS ve Dynamics 365 aboneliklerini barındırmak üzere Avrupa bölgesi seçti.
  
Azure PaaS hizmetleri ve Azure IaaS'da barındırılan sanal makine tabanlı iş yükleri, dünya genelindeki herhangi bir Azure veri merkezinde kiraya sahip olabilir. Azure PaaS uygulamasını veya hizmetini ya da bir IaaS iş yükünün öğesini  oluşturmak için konum olarak bilinen Azure veri merkezi'ne siz belirtirsiniz.
  
Azure AD kiracısı, hesapları ve grupları içeren belirli bir Azure AD örneğidir. Microsoft 365 Dynamics 365'in ücretli veya deneme abonelikleri ücretsiz bir Azure AD kiracısı içerir. Bu Azure AD kiracısı diğer Azure hizmetlerini içermemektedir ve Azure deneme sürümü veya ücretli abonelikle aynı değildir.
  
### <a name="summary-of-the-hierarchy"></a>Hiyerarşinin özeti

İşte hızlı bir özet:
  
- Bir kuruluşun birden fazla aboneliği olabilir
    
  - Bir aboneliğin birden çok lisansı olabilir
    
  - Lisanslar tek tek kullanıcı hesaplarına atanabilir
    
  - Kullanıcı hesapları bir Azure AD kiracısı içinde depolanır
    
Kuruluşların, aboneliklerin, lisansların ve kullanıcı hesaplarının ilişkisine bir örnek:
  
- Ortak etki alanı adıyla tanımlanan kuruluş.
    
  - Kullanıcı Microsoft 365 E3 olan bir abonelik.
    
    Kullanıcı Microsoft 365 E5 olan bir abonelik.
    
    Kullanıcı lisansları olan bir Dynamics 365 aboneliği.
    
    Birden çok Azure aboneliği.
    
  - Kuruluşun ortak bir Azure AD kiracısı kullanıcı hesapları.
    
Birden çok Microsoft bulut teklifi aboneliği, ortak bir kimlik sağlayıcısı gibi işlem alan aynı Azure AD kiracıyı kullanabilir. Şirket içi AD DS'nizin eşitlenmiş hesaplarını içeren merkezi bir Azure AD kiracısı, kurum için bulut tabanlı Hizmet Olarak Kimlik (IDaaS) sağlar. 
  
**Şekil 4: Bir kuruluş için eşitlenmiş şirket içi hesapları ve IDaaS**

![Identity as a Service (IaaS) IDaaS for your organization.](../media/Subscriptions/Subscriptions-Fig4.png)
  
Şekil 4, ortak bir Azure AD kiracısı tarafından Azure AD Etki Alanı Hizmetleri kullanan Azure IaaS'ta Microsoft'un SaaS bulut tekliflerini, Azure PaaS uygulamalarını ve sanal makinelerini nasıl kullanıla bir şekilde gösterir. Azure AD Bağlan, şirket içi AD DS ormanıyı Azure AD kiracısı ile eşitler.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Birden çok Microsoft bulut teklifi için abonelikleri birleştirme

Aşağıdaki tabloda, tek bir bulut teklifi türü için (birinci sütuna inen etiketler) zaten bir aboneliğe sahip olduğunu ve farklı bir bulut teklifi (sütunlar arasında gidip) için abonelik eklemeye dayalı olarak birden çok Microsoft bulut tekliflerini nasıl birleştirebilirsiniz?
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |Yok  <br/> |Azure portaldan, organizasyona bir Azure aboneliği eklersiniz.  <br/> |İlk kuruluştan, organizasyona Dynamics 365 aboneliği Microsoft 365 yönetim merkezi.  <br/> |
|**Azure** <br/> |Microsoft 365 aboneliğini eklemeniz gerekir.  <br/> |Yok  <br/> |Organizasyonunıza Dynamics 365 aboneliği eklersiniz.  <br/> |
|**Dynamics 365** <br/> |Microsoft 365 aboneliğini eklemeniz gerekir.  <br/> |Azure portaldan, organizasyona bir Azure aboneliği eklersiniz.  <br/> |Yok  <br/> |
   
Microsoft SaaS tabanlı hizmetler için organizasyona abonelik eklemenin kolay bir yolu yönetim merkezi üzerindendir:
  
1. Oturum açma bilgilerine Microsoft 365 yönetim merkezi [https://admin.microsoft.com](https://admin.microsoft.com) Yöneticisi veya **Genel yönetici** hesabınızla **oturum** açın.
    
2. Yönetim merkezi giriş sayfasının sol **gezintisinde Faturalama'ya** ve **hizmet** satın **alın'a tıklayın**.
    
3. Hizmetleri satın **alma sayfasında** yeni aboneliklerinizi satın alın.
    
Yönetim merkezi, SaaS tabanlı bulut teklifleri için Microsoft 365 abonelikleri için kuruluş ve Azure AD kiracısını yeni aboneliklere atar.
  
Aynı kuruluşa ve Azure AD kiracısına sizin aboneliğiniz olarak bir Azure Microsoft 365 eklemek için:
  
1. Azure portalında ([https://portal.azure.com](https://portal.azure.com)) azure ad **DC Microsoft 365 Genel yönetici** hesabınızla **oturum** açın.
    
2. Sol gezintide **Abonelikler'e ve** sonra da Ekle'ye **tıklayın**.
    
3. Abonelik **ekle sayfasında** bir teklif seçin ve ödeme bilgilerini ve sözleşmeyi tamamlayın.
    
Azure ve Microsoft 365 aboneliklerini ayrı olarak satın aldıysanız ve Microsoft 365 Azure AD kiracınıza Azure aboneliğiniz üzerinden erişmek için Mevcut bir Azure aboneliğini kendi kiracınıza ekleme [Azure Active Directory bakın](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal mimarlar için Microsoft bulutu çizimleri](../solutions/cloud-architecture-models.md)
  
[Lync, SharePoint, Exchange, Skype Kurumsal mimari modeller](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Karma çözümler](hybrid-solutions.md)

## <a name="next-step"></a>Sonraki adım

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)
