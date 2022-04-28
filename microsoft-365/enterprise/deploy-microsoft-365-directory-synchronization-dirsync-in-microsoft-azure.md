---
title: Microsoft Azure'da Microsoft 365 Dizin Eşitlemesini Dağıtma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
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
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Şirket içi dizininizle Azure AD kiracısı arasındaki hesapları eşitlemek için Azure'da bir sanal makineye Azure AD Bağlan dağıtmayı öğrenin.
ms.openlocfilehash: 077fe85307b5c64c5ece9d710a3ad171d04a21da
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092171"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Microsoft Azure'da Microsoft 365 Dizin Eşitlemesini Dağıtma

Azure Active Directory (Azure AD) Bağlan (eski adıyla Dizin Eşitleme aracı, Dizin Eşitleme aracı veya DirSync.exe aracı), şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) kullanıcılarınızı azure ad kiracınızla eşitlemek için etki alanına katılmış bir sunucuya yüklediğiniz bir uygulamadır aboneliği Microsoft 365. Microsoft 365, dizin hizmeti için Azure AD kullanır. Microsoft 365 aboneliğiniz bir Azure AD kiracısı içerir. Bu kiracı, Azure'daki diğer SaaS uygulamaları ve uygulamaları dahil olmak üzere kuruluşunuzun kimliklerinin diğer bulut iş yükleriyle yönetilmesi için de kullanılabilir.

Azure AD Bağlan şirket içi bir sunucuya yükleyebilirsiniz, ancak aşağıdaki nedenlerle Azure'daki bir sanal makineye de yükleyebilirsiniz:
  
- Bulut tabanlı sunucuları daha hızlı sağlayabilir ve yapılandırarak hizmetleri kullanıcılarınızın daha erken kullanımına sunabilirsiniz.
- Azure daha az çabayla daha iyi site kullanılabilirliği sunar.
- Kuruluşunuzdaki şirket içi sunucu sayısını azaltabilirsiniz.

Bu çözüm, şirket içi ağınızla Azure sanal ağınız arasında bağlantı gerektirir. Daha fazla bilgi için bkz. [Şirket içi ağı Microsoft Azure sanal ağa Bağlan](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> Bu makalede, tek bir ormandaki tek bir etki alanının eşitlenmesi açıklanmaktadır. Azure AD Bağlan, Active Directory ormanınızdaki tüm AD DS etki alanlarını Microsoft 365 ile eşitler. Microsoft 365 ile eşitlenecek birden çok Active Directory ormanınız varsa, bkz. [Tek Sign-On Senaryosu ile Çok Ormanlı Dizin Eşitleme](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Azure'da Microsoft 365 dizin eşitlemesini dağıtmaya genel bakış

Aşağıdaki diyagramda, şirket içi AD DS ormanını bir Microsoft 365 aboneliğiyle eşitleyen Azure'daki bir sanal makinede (dizin eşitleme sunucusu) çalışan Azure AD Bağlan gösterilmektedir.
  
![Azure'da bir sanal makinedeki Azure AD Bağlan aracı, şirket içi hesapları trafik akışına sahip bir Microsoft 365 aboneliğinin Azure AD kiracısıyla eşitler.](../media/CP-DirSyncOverview.png)
  
Diyagramda, siteden siteye VPN veya ExpressRoute bağlantısıyla bağlanan iki ağ vardır. AD DS etki alanı denetleyicilerinin bulunduğu bir şirket içi ağ ve Azure [AD Bağlan](https://www.microsoft.com/download/details.aspx?id=47594) çalıştıran bir sanal makine olan dizin eşitleme sunucusuna sahip bir Azure sanal ağı vardır. Dizin eşitleme sunucusundan kaynaklanan iki ana trafik akışı vardır:
  
-  Azure AD Bağlan, hesaplarda ve parolalarda yapılan değişiklikler için şirket içi ağdaki bir etki alanı denetleyicisini sorgular.
-  Azure AD Bağlan, hesaplarda ve parolalarda yapılan değişiklikleri Microsoft 365 aboneliğinizin Azure AD örneğine gönderir. Dizin eşitleme sunucusu şirket içi ağınızın genişletilmiş bir bölümünde olduğundan, bu değişiklikler şirket içi ağın proxy sunucusu üzerinden gönderilir.
    
> [!NOTE]
> Bu çözüm, tek bir Active Directory ormanında tek bir Active Directory etki alanının eşitlenmesini açıklar. Azure AD Bağlan, Active Directory ormanınızdaki tüm Active Directory etki alanlarını Microsoft 365 ile eşitler. Microsoft 365 ile eşitlenecek birden çok Active Directory ormanınız varsa, bkz. [Tek Sign-On Senaryosu ile Çok Ormanlı Dizin Eşitleme](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
Bu çözümü dağıtırken iki önemli adım vardır:
  
1. Bir Azure sanal ağı oluşturun ve şirket içi ağınıza siteden siteye VPN bağlantısı kurun. Daha fazla bilgi için bkz. [Şirket içi ağı Microsoft Azure sanal ağa Bağlan](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. [Azure AD Bağlan'yi](https://www.microsoft.com/download/details.aspx?id=47594) Azure'da etki alanına katılmış bir sanal makineye yükleyin ve ardından şirket içi AD DS'yi Microsoft 365 ile eşitleyin. Bu şunları içerir:
    
    Azure AD Bağlan çalıştırmak için bir Azure Sanal Makinesi oluşturma.
    
    [Azure AD Bağlan](https://www.microsoft.com/download/details.aspx?id=47594) yükleme ve yapılandırma.
    
    Azure AD Bağlan yapılandırmak için bir Azure AD yönetici hesabının kimlik bilgileri (kullanıcı adı ve parolası) ve ad DS kurumsal yönetici hesabı gerekir. Azure AD Bağlan, şirket içi AD DS ormanını Microsoft 365 eşitlemek için hemen ve sürekli olarak çalışır.
    
Bu çözümü üretim ortamına dağıtmadan önce, bu yapılandırmayı kavram kanıtı olarak, tanıtımlar veya denemeler için ayarlamak üzere [Simülasyon kurumsal temel yapılandırması'ndaki](simulated-ent-base-configuration-microsoft-365-enterprise.md) yönergeleri kullanabilirsiniz.
  
> [!IMPORTANT]
> Azure AD Bağlan yapılandırması tamamlandığında AD DS kurumsal yönetici hesabı kimlik bilgilerini kaydetmez. 
  
> [!NOTE]
> Bu çözüm, tek bir AD DS ormanının Microsoft 365 eşitlenmesini açıklar. Bu makalede ele alınan topoloji, bu çözümü uygulamanın tek bir yolunu temsil eder. Kuruluşunuzun topolojisi, benzersiz ağ gereksinimlerinize ve güvenlik konularınıza göre farklılık gösterebilir. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Azure'da Microsoft 365 için dizin eşitleme sunucusu barındırmayı planlama
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Önkoşullar

Başlamadan önce bu çözüm için aşağıdaki önkoşulları gözden geçirin:
  
- [Azure sanal ağınızı planlama](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network) bölümünde ilgili planlama içeriğini gözden geçirin.
    
- Azure sanal ağını yapılandırmaya [yönelik tüm Önkoşulları](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) karşıladığınızdan emin olun.
    
- Active Directory tümleştirme özelliğini içeren bir Microsoft 365 aboneliğiniz olmalıdır. Microsoft 365 abonelikler hakkında bilgi için [Microsoft 365 abonelik sayfasına](https://products.office.com/compare-all-microsoft-office-products?tab=2) gidin.
    
- Şirket içi AD DS ormanınızı Microsoft 365 ile eşitlemek için Azure AD Bağlan çalıştıran bir Azure Sanal Makinesi sağlayın.
    
    AD DS kurumsal yönetici hesabı ve Azure AD Yönetici hesabı için kimlik bilgilerine (adlar ve parolalar) sahip olmanız gerekir.
    
### <a name="solution-architecture-design-assumptions"></a>Çözüm mimarisi tasarım varsayımları

Aşağıdaki listede bu çözüm için yapılan tasarım seçimleri açıklanmaktadır.
  
- Bu çözüm, siteden siteye VPN bağlantısına sahip tek bir Azure sanal ağı kullanır. Azure sanal ağı, Azure AD Bağlan çalıştıran dizin eşitleme sunucusu olan tek bir sunucuya sahip tek bir alt ağı barındırıyor. 
    
- Şirket içi ağda bir etki alanı denetleyicisi ve DNS sunucuları vardır.
    
- Azure AD Bağlan çoklu oturum açma yerine parola karması eşitlemesi gerçekleştirir. Active Directory Federasyon Hizmetleri (AD FS) (AD FS) altyapısı dağıtmanız gerekmez. Parola karması eşitleme ve çoklu oturum açma seçenekleri hakkında daha fazla bilgi edinmek için bkz. [Azure Active Directory karma kimlik çözümünüz için doğru kimlik doğrulama yöntemini seçme](/azure/active-directory/hybrid/choose-ad-authn).
    
Bu çözümü ortamınıza dağıtırken göz önünde bulundurmanız gereken ek tasarım seçenekleri vardır. Bunlar şunları içerir:
  
- Mevcut bir Azure sanal ağında mevcut DNS sunucuları varsa, dizin eşitleme sunucunuzun bunları şirket içi ağdaki DNS sunucuları yerine ad çözümlemesi için kullanmasını isteyip istemediğinizi belirleyin.
    
- Mevcut bir Azure sanal ağında etki alanı denetleyicileri varsa, Active Directory Sitelerini ve Hizmetlerini yapılandırmanın sizin için daha iyi bir seçenek olup olmadığını belirleyin. Dizin eşitleme sunucusu, şirket içi ağdaki etki alanı denetleyicileri yerine Azure sanal ağındaki etki alanı denetleyicilerini hesaplardaki ve parolalardaki değişiklikleri sorgulayabilir.
    
## <a name="deployment-roadmap"></a>Dağıtım yol haritası

Azure'da bir sanal makinede Azure AD Bağlan dağıtımı üç aşamadan oluşur:
  
- 1. Aşama: Azure sanal ağını oluşturma ve yapılandırma
    
- 2. Aşama: Azure sanal makinesini oluşturma ve yapılandırma
    
- 3. Aşama: Azure AD Bağlan yükleme ve yapılandırma
    
Dağıtımdan sonra, Microsoft 365'da yeni kullanıcı hesapları için konumlar ve lisanslar atamanız gerekir.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>1. Aşama: Azure sanal ağını oluşturma ve yapılandırma

Azure sanal ağını oluşturmak ve yapılandırmak için 1. [Aşama: Şirket içi ağınızı](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) hazırlama ve [2. Aşama:](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) Şirket içi ağı bir Microsoft Azure sanal ağa Bağlan dağıtım yol haritasında [Azure'da şirket içi sanal ağı](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) oluşturma işlemini tamamlayın.
  
Bu, sonuçta elde edilen yapılandırmanızdır.
  
![Azure'da barındırılan Microsoft 365 için dizin eşitleme sunucusunun 1. aşaması.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Bu şekilde, siteden siteye VPN veya ExpressRoute bağlantısı üzerinden Azure sanal ağına bağlı bir şirket içi ağ gösterilmektedir.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>2. Aşama: Azure sanal makinesini oluşturma ve yapılandırma

Azure portal [ilk Windows sanal makinenizi oluşturma yönergelerini kullanarak Azure'da sanal makineyi oluşturun](https://go.microsoft.com/fwlink/p/?LinkId=393098). Aşağıdaki ayarları kullanın:
  
- **Temel Bilgiler** bölmesinde sanal ağınızla aynı aboneliği, konumu ve kaynak grubunu seçin. Kullanıcı adını ve parolayı güvenli bir konuma kaydedin. Sanal makineye bağlanmak için bunlara daha sonra ihtiyacınız olacaktır.
    
- **Boyut seçin** bölmesinde **A2 Standart** boyutunu seçin.
    
- **Ayarlar** bölmesindeki **Depolama** bölümünde **Standart** depolama türünü seçin. **Ağ** bölümünde, sanal ağınızın adını ve dizin eşitleme sunucusunu barındırmak için alt ağı seçin (GatewaySubnet'i değil). Diğer tüm ayarları varsayılan değerlerinde bırakın.
    
Ip adresiyle sanal makine için bir Adres (A) kaydı eklendiğinden emin olmak için iç DNS'nizi denetleyerek dizin eşitleme sunucunuzun DNS'yi doğru kullandığını doğrulayın. 
  
[Sanal makineye Bağlan](/azure/virtual-machines/windows/connect-logon) yönergelerini kullanın ve Uzak Masaüstü Bağlantısı ile dizin eşitleme sunucusuna bağlanmak için oturum açın. Oturum açtıktan sonra sanal makineyi şirket içi AD DS etki alanına ekleyin.
  
Azure AD Bağlan İnternet kaynaklarına erişim elde etmek için dizin eşitleme sunucusunu şirket içi ağın proxy sunucusunu kullanacak şekilde yapılandırmanız gerekir. Gerçekleştirilecek ek yapılandırma adımları için ağ yöneticinize başvurmanız gerekir.
  
Bu, sonuçta elde edilen yapılandırmanızdır.
  
![Azure'da barındırılan Microsoft 365 için dizin eşitleme sunucusunun 2. aşaması.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Bu şekilde, şirket içi Azure sanal ağındaki dizin eşitleme sunucusu sanal makinesi gösterilmektedir.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>3. Aşama: Azure AD Bağlan yükleme ve yapılandırma

Aşağıdaki yordamı tamamlayın:
  
1. Yerel yönetici ayrıcalıklarına sahip bir AD DS etki alanı hesabıyla Uzak Masaüstü Bağlantısı kullanarak dizin eşitleme sunucusuna Bağlan. Bkz. [sanal makineye Bağlan ve oturum açın](/azure/virtual-machines/windows/connect-logon).
    
2. Dizin eşitleme sunucusundan [Microsoft 365 için dizin eşitlemesini ayarlama](set-up-directory-synchronization.md) makalesini açın ve parola karması eşitlemesi ile dizin eşitleme yönergelerini izleyin.
    
> [!CAUTION]
> Kurulum **, yerel** kullanıcılar kuruluş biriminde (OU) AAD_xxxxxxxxxxxx hesabı oluşturur. Bu hesabı taşımayın veya kaldırmayın; eşitleme başarısız olur.
  
Bu, sonuçta elde edilen yapılandırmanızdır.
  
![Azure'da barındırılan Microsoft 365 için dizin eşitleme sunucusunun 3. aşaması.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Bu şekilde, şirket içi Azure sanal ağında Azure AD Bağlan ile dizin eşitleme sunucusu gösterilmektedir.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Microsoft 365'de kullanıcılara konumlar ve lisanslar atama

Azure AD Bağlan, şirket içi AD DS'den Microsoft 365 aboneliğinize hesaplar ekler, ancak kullanıcıların Microsoft 365 oturum açıp hizmetlerini kullanabilmesi için hesapların bir konum ve lisansla yapılandırılması gerekir. Konumu eklemek ve uygun kullanıcı hesapları için lisansları etkinleştirmek için şu adımları kullanın:
  
1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın ve ardından **Yönetici'ye** tıklayın.
    
2. Sol gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**KullanıcılarEtkin**</a> >  kullanıcılar'a tıklayın.
3. Kullanıcı hesapları listesinde, etkinleştirmek istediğiniz kullanıcının yanındaki onay kutusunu seçin.
    
4. Kullanıcının sayfasında **Ürün lisansları** için **Düzenle'ye** tıklayın.
    
5. **Ürün lisansları** sayfasında, **Konum** için kullanıcı için bir konum seçin ve ardından kullanıcı için uygun lisansları etkinleştirin.
    
6. Tamamlandığında **Kaydet'e** ve ardından iki kez **Kapat'a** tıklayın.
    
7. Ek kullanıcılar için 3. adıma Geri dön.
    
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)
  
[şirket içi ağı Microsoft Azure bir sanal ağa Bağlan](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Azure AD Bağlan'ı indirme](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Microsoft 365 için dizin eşitlemesini ayarlama](set-up-directory-synchronization.md)
