---
title: Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Microsoft bulut tekliflerindeki kuruluşların, aboneliklerin, lisansların, kullanıcı hesaplarının ve kiracıların ilişkilerini anlayın.
ms.openlocfilehash: 9a3f41af3945055ebfc3217837b0bdaf8aab411a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101171"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar

Microsoft, bulut tekliflerinde kimliklerin ve faturalamanın tutarlı bir şekilde kullanılması için kuruluşların, aboneliklerin, lisansların ve kullanıcı hesaplarının hiyerarşisini sağlar:
  
- Microsoft 365 ve Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Hiyerarşinin öğeleri

Hiyerarşinin öğeleri şunlardır:
  
### <a name="organization"></a>Organizasyon

Kuruluş, genellikle contoso.com gibi bir veya daha fazla genel Etki Alanı Adı Sistemi (DNS) etki alanı adıyla tanımlanan Microsoft bulut tekliflerini kullanan bir işletme varlığını temsil eder. Kuruluş, abonelikler için bir kapsayıcıdır.
  
### <a name="subscriptions"></a>Abonelik

Abonelik, Kullanıcı başına lisans ücretine veya bulut tabanlı kaynak tüketimine bağlı olarak ücretlerin tahakkuk ettiği bir veya daha fazla Microsoft bulut platformu veya hizmetini kullanmak için Microsoft ile yapılan bir anlaşmadır. 

- Microsoft'un Hizmet Olarak Yazılım (SaaS) tabanlı bulut teklifleri (Microsoft 365 ve Dynamics 365) kullanıcı başına lisans ücreti alır. 
- Microsoft'un Hizmet Olarak Platform (PaaS) ve Hizmet Olarak Altyapı (IaaS) bulut teklifleri (Azure) bulut kaynağı tüketimine göre ücretlendirilir.
 
Deneme aboneliği de kullanabilirsiniz, ancak aboneliğin süresi belirli bir süre veya tüketim ücretinden sonra dolar. Deneme aboneliğini ücretli aboneliğe dönüştürebilirsiniz.
  
Kuruluşlar Microsoft'un bulut teklifleri için birden fazla aboneliğe sahip olabilir. Şekil 1'de birden çok Microsoft 365 aboneliği, Dynamics 365 aboneliği ve birden çok Azure aboneliği olan tek bir kuruluş gösterilmektedir.

**Şekil 1: Bir kuruluş için birden çok abonelik örneği**

![Microsoft'un bulut teklifleri için birden çok aboneliği olan örnek bir kuruluş.](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Lisanslar

Microsoft'un SaaS bulut tekliflerinde lisans, belirli bir kullanıcı hesabının bulut teklifinin hizmetlerini kullanmasına izin verir. Aboneliğinizin bir parçası olarak aylık sabit bir ücret alınır. Yöneticiler, abonelikteki tek tek kullanıcı hesaplarına lisans atar. Şekil 2'deki örnekte Contoso Corporation'ın 100 lisansa sahip bir Microsoft 365 E5 aboneliği vardır ve bu da Microsoft 365 E5 özellikleri ve hizmetlerini kullanmak için 100'e kadar bireysel kullanıcı hesabı sağlar.
  
**Şekil 2: Bir kuruluşun SaaS tabanlı aboneliklerindeki lisanslar**

![Microsoft'un SaaS tabanlı bulut teklifleri için abonelikler içinde birden çok lisans örneği.](../media/Subscriptions/Subscriptions-Fig2.png)

>[!Note]
>Güvenlik için en iyi yöntem, yönetim işlevleri için belirli roller atanmış ayrı kullanıcı hesapları kullanmaktır. Bu ayrılmış yönetici hesaplarına, yönetdikleri bulut hizmetleri için bir lisans atanması gerekmez. Örneğin, SharePoint yönetici hesabına Microsoft 365 lisansı atanması gerekmez.
>

Azure PaaS tabanlı bulut hizmetleri için yazılım lisansları hizmet fiyatlandırmasına yerleşik olarak eklenir.
  
Azure IaaS tabanlı sanal makineler için, bir sanal makine görüntüsünde yüklü olan yazılımı veya uygulamayı kullanmak için ek lisanslar gerekebilir. Bazı sanal makine görüntülerinde yazılımın lisanslı sürümleri yüklüdür ve maliyet sunucu için dakika başına ücrete dahil edilir. SQL Server 2014 ve SQL Server 2016 için sanal makine görüntüleri örnek olarak verilebilir. 
  
Bazı sanal makine görüntülerinde uygulamaların deneme sürümleri yüklüdür ve deneme süresinden sonra kullanılmak üzere ek yazılım uygulama lisanslarına ihtiyaç duyar. Örneğin, SharePoint Server 2016 Deneme sanal makinesi görüntüsü, önceden yüklenmiş SharePoint Server 2016'nın deneme sürümünü içerir. Deneme süre sonu tarihinden sonra SharePoint Server 2016'yı kullanmaya devam etmek için Microsoft'tan SharePoint Server 2016 lisansı ve istemci lisansları satın almalısınız. Bu ücretler Azure aboneliğinden ayrıdır ve sanal makineyi çalıştırmak için dakika başına ücret uygulanır.
  
### <a name="user-accounts"></a>Kullanıcı hesapları

Microsoft'un tüm bulut tekliflerinin kullanıcı hesapları, kullanıcı hesaplarını ve gruplarını içeren bir Azure Active Directory (Azure AD) kiracısında depolanır. Azure AD kiracısı, Windows sunucu tabanlı bir hizmet olan Azure AD Bağlan kullanılarak mevcut Active Directory Domain Services (AD DS) hesaplarınızla eşitlenebilir. Bu, dizin eşitlemesi olarak bilinir.
  
Şekil 3'de, kuruluşun hesaplarını içeren ortak bir Azure AD kiracısı kullanan bir kuruluşun birden çok aboneliği örneği gösterilmektedir.
  
**Şekil 3: Bir kuruluşun aynı Azure AD kiracısını kullanan birden çok aboneliği**

![Tümü aynı Azure AD kiracısını kullanan birden çok aboneliği olan örnek bir kuruluş.](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Kiracı

SaaS bulut teklifleri için kiracı, bulut hizmetleri sağlayan sunucuları barındıran bölgesel konumdur. Örneğin Contoso Corporation, Paris'teki 15.000 çalışanın Microsoft 365, EMS ve Dynamics 365 aboneliklerini barındırmak için Avrupa bölgesini seçti.
  
Azure IaaS'de barındırılan Azure PaaS hizmetleri ve sanal makine tabanlı iş yükleri, dünyanın farklı yerlerindeki herhangi bir Azure veri merkezinde kiracıya sahip olabilir. IaaS iş yükünün Azure PaaS uygulamasını veya hizmetini veya öğesini oluştururken konum olarak bilinen Azure veri merkezini belirtirsiniz.
  
Azure AD kiracısı, hesapları ve grupları içeren belirli bir Azure AD örneğidir. Microsoft 365 veya Dynamics 365 ücretli veya deneme abonelikleri ücretsiz bir Azure AD kiracısı içerir. Bu Azure AD kiracısı diğer Azure hizmetlerini içermez ve Azure deneme sürümü veya ücretli abonelikle aynı değildir.
  
### <a name="summary-of-the-hierarchy"></a>Hiyerarşinin özeti

Hızlı bir özet aşağıda verilmiştir:
  
- Bir kuruluşun birden çok aboneliği olabilir
    
  - Bir aboneliğin birden çok lisansı olabilir
    
  - Lisanslar tek tek kullanıcı hesaplarına atanabilir
    
  - Kullanıcı hesapları bir Azure AD kiracısında depolanır
    
Aşağıda kuruluşların, aboneliklerin, lisansların ve kullanıcı hesaplarının ilişkisine bir örnek verilmiştir:
  
- Genel etki alanı adıyla tanımlanan bir kuruluş.
    
  - Kullanıcı lisanslarına sahip bir Microsoft 365 E3 aboneliği.
    
    Kullanıcı lisanslarına sahip bir Microsoft 365 E5 aboneliği.
    
    Kullanıcı lisanslarına sahip bir Dynamics 365 aboneliği.
    
    Birden çok Azure aboneliği.
    
  - Kuruluşun ortak bir Azure AD kiracısında bulunan kullanıcı hesapları.
    
Birden çok Microsoft bulut teklifi aboneliği, ortak kimlik sağlayıcısı işlevi gören aynı Azure AD kiracısını kullanabilir. Şirket içi AD DS'nizin eşitlenmiş hesaplarını içeren merkezi bir Azure AD kiracısı, kuruluşunuz için bulut tabanlı Hizmet Olarak Kimlik (IDaaS) sağlar. 
  
**Şekil 4: Bir kuruluş için eşitlenmiş şirket içi hesapları ve IDaaS**

![Kuruluşunuz için Hizmet Olarak Kimlik (IaaS) IDaaS.](../media/Subscriptions/Subscriptions-Fig4.png)
  
Şekil 4'te ortak bir Azure AD kiracısını Microsoft'un SaaS bulut teklifleri, Azure PaaS uygulamaları ve Azure IaaS'de Azure AD Domain Services kullanan sanal makineler tarafından nasıl kullanıldığı gösterilmektedir. Azure AD Bağlan, şirket içi AD DS ormanını Azure AD kiracısıyla eşitler.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Birden çok Microsoft bulut teklifi için abonelikleri birleştirme

Aşağıdaki tabloda, bir bulut teklifi türü için zaten bir aboneliğe sahip olmanıza (ilk sütuna inen etiketler) ve farklı bir bulut teklifi için abonelik eklemeye (sütunlar arasında gidip) bağlı olarak birden çok Microsoft bulut teklifini nasıl birleştirebileceğiniz açıklanmaktadır.
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |NA  <br/> |Azure portal kuruluşunuza bir Azure aboneliği eklersiniz.  <br/> |kuruluşunuza Microsoft 365 yönetim merkezi bir Dynamics 365 aboneliği eklersiniz.  <br/> |
|**Azure** <br/> |Kuruluşunuza bir Microsoft 365 aboneliği eklersiniz.  <br/> |NA  <br/> |Kuruluşunuza dynamics 365 aboneliği eklersiniz.  <br/> |
|**Dynamics 365** <br/> |Kuruluşunuza bir Microsoft 365 aboneliği eklersiniz.  <br/> |Azure portal kuruluşunuza bir Azure aboneliği eklersiniz.  <br/> |NA  <br/> |
   
Microsoft SaaS tabanlı hizmetler için kuruluşunuza abonelik eklemenin kolay bir yolu yönetim merkezidir:
  
1. **Kullanıcı Yöneticiniz** veya **Genel yönetici** hesabınızla Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) oturum açın.
    
2. **Yönetim merkezi** giriş sayfasının sol gezinti bölmesinde **Faturalama'ya** ve ardından **Hizmetleri satın al'a** tıklayın.
    
3. **Hizmetleri satın al** sayfasında yeni aboneliklerinizi satın alın.
    
Yönetim merkezi, Microsoft 365 aboneliğinizin kuruluş ve Azure AD kiracısını SaaS tabanlı bulut teklifleri için yeni aboneliklere atar.
  
Microsoft 365 aboneliğinizle aynı kuruluşa ve Azure AD kiracısına sahip bir Azure aboneliği eklemek için:
  
1. Microsoft 365 **Azure AD DC yöneticiniz** veya **Genel yönetici** hesabınızla Azure portal ([https://portal.azure.com](https://portal.azure.com)) oturum açın.
    
2. Sol gezinti bölmesinde **Abonelikler'e** ve ardından **Ekle'ye** tıklayın.
    
3. **Abonelik ekle** sayfasında bir teklif seçin ve ödeme bilgilerini ve sözleşmeyi tamamlayın.
    
Azure ve Microsoft 365 aboneliklerini ayrı olarak satın aldıysanız ve Azure aboneliğinizden Microsoft 365 Azure AD kiracısına erişmek istiyorsanız, [Azure Active Directory kiracınıza var olan bir Azure aboneliğini ekleme](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) başlığı altında yer alan yönergelere bakın.
 
## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal mimarlar için Microsoft bulutu çizimleri](../solutions/cloud-architecture-models.md)
  
[SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modeller](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hibrit çözümler](hybrid-solutions.md)

## <a name="next-step"></a>Sonraki adım

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
