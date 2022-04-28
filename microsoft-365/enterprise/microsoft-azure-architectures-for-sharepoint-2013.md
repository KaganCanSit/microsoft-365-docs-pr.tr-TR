---
title: SharePoint 2013 için Microsoft Azure Mimarileri
ms.author: bcarter
author: brendacarter
manager: scotv
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: SharePoint 2013 çözümlerinin hangi türlerinin Microsoft Azure sanal makinelerde barındırılabileceğini ve Azure'ı bir çözümü barındıracak şekilde nasıl ayarlayacağınızı öğrenin.
ms.openlocfilehash: 7761eb9b62000c03b2983bc5ed56a62e20981db7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097414"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>SharePoint 2013 için Microsoft Azure Mimarileri

Azure, SharePoint Server 2013 çözümünü barındırmak için iyi bir ortamdır. Çoğu durumda Microsoft 365 öneririz, ancak Azure'da barındırılan SharePoint Sunucu grubu belirli çözümler için iyi bir seçenek olabilir. Bu makalede, Azure platformuna uygun olması için SharePoint çözümlerinin mimarisinin nasıl tasarlandığı açıklanır. Örnek olarak aşağıdaki iki özel çözüm kullanılır:
  
- [Microsoft Azure'da SharePoint Server 2013 Olağanüstü Durum Kurtarma](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [SharePoint Server 2013 kullanarak Microsoft Azure'daki İnternet Siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Azure Altyapı Hizmetleri için önerilen SharePoint çözümleri

Azure altyapı hizmetleri, SharePoint çözümleri barındırmak için cazip bir seçenektir. Bazı çözümler bu platform için diğerlerinden daha uygundur. Aşağıdaki tabloda önerilen çözümler gösterilmektedir.
  
|**Çözüm**|**Bu çözümün Azure için neden önerildiğinden**|
|:-----|:-----|
|Geliştirme ve test ortamları  <br/> |Bu ortamları oluşturmak ve yönetmek kolaydır.  <br/> |
|Şirket içi SharePoint gruplarından Azure'a olağanüstü durum kurtarma  <br/> |**Barındırılan ikincil veri merkezi** Farklı bir bölgedeki ikincil veri merkezine yatırım yapmak yerine Azure'i kullanın. <br/> **Daha düşük maliyetli olağanüstü durum kurtarma ortamları** Şirket içi olağanüstü durum kurtarma ortamından daha az kaynak için bakım ve ödeme. Kaynak sayısı seçtiğiniz olağanüstü durum kurtarma ortamına bağlıdır: soğuk bekleme, sıcak bekleme veya etkin bekleme. <br/> **Daha esnek platform** Olağanüstü bir durumda, yük gereksinimlerini karşılamak için kurtarma SharePoint grubunuzun ölçeğini kolayca genişletin. Kaynaklara artık ihtiyacınız kalmadığında ölçeği daraltın. <br/> Bkz. [Microsoft Azure'da SharePoint Server 2013 Olağanüstü Durum Kurtarma](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|özellikleri kullanan ve Microsoft 365'de kullanılamayan İnternet'e yönelik siteler  <br/> |**Çalışmalarınızı odaklama** Altyapı oluşturmak yerine harika bir site oluşturmaya odaklan. <br/> **Azure'da esneklik avantajından yararlanma** Yeni sunucular ekleyerek grubu talebe göre boyutlandırın ve yalnızca ihtiyacınız olan kaynaklar için ödeme uygulayın. Dinamik makine ayırma desteklenmez (otomatik ölçeklendirme). <br/> **Azure Active Directory (AD) kullanma** Müşteri hesapları için Azure AD'nin avantajlarından yararlanın. <br/> Microsoft 365 Derin raporlama ve web analizi ekleme **bölümünde kullanılamayan SharePoint işlevselliği ekleyin**. <br/> bkz[. SharePoint Server 2013 kullanarak Microsoft Azure'da İnternet Siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Microsoft 365 veya şirket içi ortamları desteklemek için uygulama grupları  <br/> |Hem şirket içi hem de bulut ortamlarını desteklemek için Azure'da **uygulama derleyin, test edin ve barındırabilirsiniz**. <br/> Şirket içi ortamlar için yeni donanım satın almak yerine bu rolü Azure'da **barındırın**. <br/> |
   
İntranet ve işbirliği çözümleri ve iş yükleri için aşağıdaki seçenekleri göz önünde bulundurun:
  
- Microsoft 365 iş gereksinimlerinizi karşılayıp karşılamadığını veya çözümün bir parçası olup olmadığını belirleyin. Microsoft 365 her zaman güncel olan zengin bir özellik kümesi sağlar.
    
- Microsoft 365 tüm iş gereksinimlerinizi karşılamıyorsa, Microsoft Danışmanlık Hizmetleri'nden (MCS) şirket içinde SharePoint 2013'ün standart bir uygulamasını düşünün. Standart mimari, özelleştirilmiş bir mimariden daha hızlı, daha ucuz ve daha kolay bir çözüm olabilir. 
    
- Standart bir uygulama iş gereksinimlerinizi karşılamıyorsa özelleştirilmiş bir şirket içi çözümü göz önünde bulundurun.
    
- Bulut platformu kullanmak iş gereksinimleriniz için önemliyse Azure altyapı hizmetlerinde barındırılan SharePoint 2013'ün standart veya özelleştirilmiş bir uygulamasını göz önünde bulundurun. SharePoint çözümlerinin Azure'da destekleniyor olması, diğer yerel Olmayan Microsoft genel bulut platformlarına göre çok daha kolaydır.
    
## <a name="before-you-design-the-azure-environment"></a>Azure ortamını tasarlamadan önce

Bu makalede örnek SharePoint topolojileri kullanılırken, bu tasarım kavramlarını herhangi bir SharePoint grubu topolojisiyle kullanabilirsiniz. Azure ortamını tasarlamadan önce, SharePoint grubu tasarlamak için aşağıdaki topoloji, mimari, kapasite ve performans kılavuzunu kullanın:
  
- [SharePoint 2013 BT uzmanları için mimari tasarımı](/SharePoint/technical-reference/technical-diagrams)
    
- [SharePoint Server 2013'te performans ve kapasite yönetimini planlama](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a>Active Directory etki alanı türünü belirleme

Her SharePoint Sunucusu grubu, grup kurulumu için yönetim hesapları sağlamak üzere Active Directory'ye dayanır. Şu anda Azure'da SharePoint çözümleri için iki seçenek vardır. Bunlar aşağıdaki tabloda açıklanmıştır.
  
|**Seçeneği**|**Açıklama**|
|:-----|:-----|
|Ayrılmış etki alanı  <br/> |SharePoint grubunuzu desteklemek için ayrılmış ve yalıtılmış bir Active Directory etki alanını Azure'a dağıtabilirsiniz. Bu, genel kullanıma yönelik İnternet siteleri için iyi bir seçimdir.  <br/> |
|Şirket içi etki alanını şirket içi bağlantı aracılığıyla genişletme  <br/> |Şirket içi etki alanını şirket içi bağlantı aracılığıyla genişlettiğinizde, kullanıcılar SharePoint grubuna intranetiniz üzerinden şirket içinde barındırılmış gibi erişir. şirket içi Active Directory ve DNS uygulamanızdan yararlanabilirsiniz.  <br/> Şirket içi grubunuzdan yük devretmek üzere Azure'da olağanüstü durum kurtarma ortamı oluşturmak için şirket içi bağlantı gereklidir.  <br/> |
   
Bu makale, şirket içi etki alanını şirket içi bağlantı aracılığıyla genişletmeye yönelik tasarım kavramlarını içerir. Çözümünüz ayrılmış bir etki alanı kullanıyorsa, şirket içi bağlantı gerekmez.
  
## <a name="design-the-virtual-network"></a>Sanal ağı tasarlama

öncelikle Azure'da sanal makinelerinizi yerleştirebileceğiniz alt ağları içeren bir sanal ağa ihtiyacınız vardır. Sanal ağın, bir kısmını alt ağlara atadığınız özel bir IP adresi alanına ihtiyacı vardır.
  
Şirket içi ağınızı bir şirket içi bağlantı üzerinden Azure'a genişletiyorsanız (olağanüstü durum kurtarma ortamı için gereklidir), şirket içi ortamınızı ve diğer Azure sanal ağlarını içerebilen, kuruluş ağınızda başka bir yerde kullanılmamış bir özel adres alanı seçmeniz gerekir. 
  
**Şekil 1: Azure'da sanal ağ içeren şirket içi ortam**

![SharePoint çözümü için sanal ağ tasarımını Microsoft Azure. Azure ağ geçidi için bir alt ağ. Sanal makineler için bir alt ağ.](../media/OPrrasconWA-AZarch.png)
  
Bu diyagramda:
  
- Azure'daki bir sanal ağ, şirket içi ortamda yan yana gösterilir. İki ortam henüz siteler arası bir bağlantıyla bağlanmamış, bu da siteden siteye VPN bağlantısı veya ExpressRoute olabilir.
    
- Bu noktada sanal ağ yalnızca alt ağları içerir ve diğer mimari öğeleri içermez. Bir alt ağ Azure ağ geçidini barındıracak ve diğer alt ağlar SharePoint grubunun katmanlarını barındıracak ve active Directory ve DNS için bir alt ağ daha barındıracaktır.
    
## <a name="add-cross-premises-connectivity"></a>Şirket içi bağlantı ekleme

Sonraki dağıtım adımı, şirket içi bağlantılar oluşturmaktır (bu çözüm için geçerliyse). Şirket içi bağlantılar için, azure ağ geçidi ayrı bir ağ geçidi alt asında bulunur ve bu alt ağda bir adres alanı oluşturup atamanız gerekir. 
  
Şirket içi bir bağlantı planlarken, bir Azure ağ geçidi ve şirket içi ağ geçidi cihazına bağlantı tanımlayıp oluşturursunuz.
  
**Şekil 2: Şirket içi ortamla Azure arasında siteden siteye bağlantı sağlamak için Azure ağ geçidi ve şirket içi ağ geçidi cihazı kullanma**

![Siteler arası VPN bağlantısı veya ExpressRoute olabilecek şirket içi bir bağlantıyla Azure sanal ağına bağlı şirket içi ortam.](../media/AZarch-VPNgtwyconnct.png)
  
Bu diyagramda:
  
- Önceki diyagrama ek olarak, şirket içi ortam, siteden siteye VPN bağlantısı veya ExpressRoute olabilecek şirket içi bir bağlantıyla Azure sanal ağına bağlanır.
    
- Azure ağ geçidi bir ağ geçidi alt ağı üzerindedir.
    
- Şirket içi ortam, yönlendirici veya VPN sunucusu gibi bir ağ geçidi cihazı içerir.
    
Şirket içi sanal ağı planlamak ve oluşturmak için bkz. [şirket içi ağı Microsoft Azure sanal ağa Bağlan](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Active Directory Domain Services (AD DS) ve DNS ekleme

Azure'da olağanüstü durum kurtarma için, Windows Server AD hem şirket içinde hem de Azure sanal makinelerinde dağıtıldığı karma bir senaryoda Windows Server AD ve DNS'yi dağıtırsınız.
  
**Şekil 3: Karma Active Directory etki alanı yapılandırması**

![Azure sanal ağına dağıtılan STwo sanal makineleri ve SharePoint Grubu alt ağı, çoğaltma etki alanı denetleyicileri ve DNS sunucularıdır.](../media/AZarch-HyADdomainConfig.png)
  
Bu diyagram, bir Windows Server AD ve DNS alt a bilgisayarına iki sanal makine ekleyerek önceki diyagramları temel alır. Bu sanal makineler çoğaltma etki alanı denetleyicileri ve DNS sunucularıdır. Bunlar şirket içi Windows Server AD ortamının bir uzantısıdır. 
  
Aşağıdaki tabloda Azure'daki bu sanal makineler için yapılandırma önerileri sağlanmaktadır. Bunları, Azure ortamınızın şirket içi ortamınızla iletişim kurmadığı ayrılmış bir etki alanı için bile kendi ortamınızı tasarlamak için bir başlangıç noktası olarak kullanın.
  
|**Öğe**|**Yapılandırma**|
|:-----|:-----|
|Azure'da sanal makine boyutu  <br/> |Standart katmanda A1 veya A2 boyutu  <br/> |
|İşletim sistemi  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory rolü  <br/> |Genel katalog sunucusu olarak atanan AD DS etki alanı denetleyicisi. Bu yapılandırma, şirket içi bağlantı genelinde çıkış trafiğini azaltır.  <br/> Yüksek değişim oranlarına sahip çok etki alanılı bir ortamda (bu yaygın değildir), çoğaltma trafiğini azaltmak için şirket içindeki etki alanı denetleyicilerini Azure'daki genel katalog sunucularıyla eşitlenmemesi için yapılandırın.  <br/> |
|DNS rolü  <br/> |ETKI alanı denetleyicilerinde DNS Sunucusu hizmetini yükleyin ve yapılandırın.  <br/> |
|Veri diskleri  <br/> |Active Directory veritabanını, günlüklerini ve SYSVOL'leri ek Azure veri disklerine yerleştirin. Bunları işletim sistemi disklerine veya Azure tarafından sağlanan geçici disklere yerleştirmeyin.  <br/> |
|IP adresleri  <br/> |Statik IP adreslerini kullanın ve etki alanı denetleyicileri yapılandırıldıktan sonra bu adresleri sanal ağdaki sanal makinelere atamak için sanal ağı yapılandırın.  <br/> |
   
> [!IMPORTANT]
> Azure'da Active Directory'yi dağıtmadan önce [Azure Sanal Makineler'da Windows Server Active Directory Dağıtma Yönergeleri'ne](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100) bakın. Bunlar, çözümünüz için farklı bir mimari veya farklı yapılandırma ayarları gerekip gerekmediğini belirlemenize yardımcı olur. 
  
## <a name="add-the-sharepoint-farm"></a>SharePoint grubu ekleme

SharePoint grubunun sanal makinelerini uygun alt ağlardaki katmanlara yerleştirin.
  
**Şekil 4: SharePoint sanal makinelerin yerleşimi**

![SharePoint Grubu alt ağı içindeki Azure sanal ağına eklenen veritabanı sunucuları ve SharePoint sunucu rolleri.](../media/AZarch-SPVMsinCloudSer.png)
  
Bu diyagram, ilgili katmanlarına SharePoint grubu sunucu rollerini ekleyerek önceki diyagramları temel alır.
  
- veritabanı katmanını oluşturmak SQL Server çalışan iki veritabanı sanal makinesi.
    
- Aşağıdaki katmanların her biri için SharePoint Server 2013 çalıştıran iki sanal makine: ön uç sunucuları, dağıtılmış önbellek sunucuları ve arka uç sunucuları.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Kullanılabilirlik kümeleri ve hata etki alanları için sunucu rollerini tasarlama ve ayarlama

Hata etki alanı, rol örneklerinin çalıştırıldığı bir donanım grubudur. Aynı hata etki alanındaki sanal makineler Azure altyapısı tarafından aynı anda güncelleştirilebilir. Ya da aynı rafı paylaştıkları için aynı anda başarısız olabilirler. Aynı hata etki alanında iki sanal makine bulundurma riskini önlemek için, sanal makinelerinizi bir kullanılabilirlik kümesi olarak yapılandırabilirsiniz ve bu da her sanal makinenin farklı bir hata etki alanında olmasını sağlar. Kullanılabilirlik kümesi olarak üç sanal makine yapılandırılırsa Azure, sanal makinelerden en fazla ikisinin aynı hata etki alanında yer almayacağını garanti eder.
  
bir SharePoint grubu için Azure mimarisi tasarlarken, aynı sunucu rollerini bir kullanılabilirlik kümesinin parçası olacak şekilde yapılandırın. Bu, sanal makinelerinizin birden çok hata etki alanına yayılmasını sağlar.
  
**Şekil 5: SharePoint grubu katmanları için yüksek kullanılabilirlik sağlamak için Azure Kullanılabilirlik Kümelerini kullanma**

![SharePoint 2013 çözümü için Azure altyapısındaki kullanılabilirlik kümelerinin yapılandırması.](../media/AZenv-WinAzureAvailSetsHA.png)
  
Bu diyagram, Azure altyapısındaki kullanılabilirlik kümelerinin yapılandırmasını çağırır. Aşağıdaki rollerin her biri ayrı bir kullanılabilirlik kümesi paylaşır:
  
- Active Directory ve DNS
    
- Veritabanı
    
- Arka uç
    
- Önbelleği dağıtma
    
- Ön uç
    
SharePoint grubu Azure platformunda ince ayar yapılması gerekebilir. Tüm bileşenlerin yüksek kullanılabilirliğini sağlamak için sunucu rollerinin tümünün aynı şekilde yapılandırıldığından emin olun.
  
Burada, belirli kapasite ve performans hedeflerini karşılayan standart bir İnternet Siteleri mimarisini gösteren bir örnek verilmiştir. Bu örnek şu mimari modelinde yer alır: [SharePoint Server 2013 için İnternet Siteleri Arama Mimarileri](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Şekil 6: Üç katmanlı bir grup içinde kapasite ve performans hedefleri için planlama örneği**

![Standart SharePoint 2013 İnternet Siteleri mimarisi ve belirli kapasite ve performans hedeflerine uyan bileşen ayırmaları.](../media/AZarch-CapPerfexmpArch.png)
  
Bu diyagramda:
  
- Üç katmanlı bir grup temsil edilir: web sunucuları, uygulama sunucuları ve veritabanı sunucuları.
    
- Üç web sunucusu birden çok bileşenle aynı şekilde yapılandırılır.
    
- İki veritabanı sunucusu aynı şekilde yapılandırılır.
    
- Üç uygulama sunucusu aynı şekilde yapılandırılmamış. Bu sunucu rolleri, Azure'da kullanılabilirlik kümeleri için ince ayar gerektirir.
    
Şimdi uygulama sunucusu katmanına daha yakından bakalım.
  
**Şekil 7: İnce ayarlamadan önce uygulama sunucusu katmanı**

![Microsoft Azure kullanılabilirlik kümelerini ayarlamadan önce Sunucu 2013 uygulama sunucusu katmanını SharePoint örnek.](../media/AZarch-AppServtierBefore.png)
  
Bu diyagramda:
  
- Uygulama katmanına üç sunucu dahildir.
    
- İlk sunucu dört bileşen içerir.
    
- İkinci sunucu üç bileşen içerir.
    
- Üçüncü sunucu iki bileşen içerir.
    
Bileşen sayısını, grup için performans ve kapasite hedeflerine göre belirlersiniz. Bu mimariyi Azure'a uyarlamak için dört bileşeni üç sunucuda da çoğaltacağız. Bu, bileşen sayısını performans ve kapasite için gerekli olandan daha fazla artırır. Sonuçta bu tasarım, bu üç sanal makine bir kullanılabilirlik kümesine atandığında Azure platformundaki dört bileşenin de yüksek kullanılabilirliğini güvence altına alır.
  
**Şekil 8: İnce ayarlamadan sonra uygulama sunucusu katmanı**

![Microsoft Azure kullanılabilirlik kümelerini ayarladıktan sonra Sunucu 2013 uygulama sunucusu katmanını SharePoint örnek.](../media/AZarch-AppServtierAfter.png)
  
Bu diyagram, aynı dört bileşenle aynı şekilde yapılandırılmış üç uygulama sunucusunu da gösterir.
  
SharePoint grubunun katmanlarına kullanılabilirlik kümeleri eklediğimizde uygulama tamamlanır.
  
**Şekil 9: Azure altyapı hizmetlerinde tamamlanan SharePoint grubu**

![Sanal ağ, şirket içi bağlantı, alt ağlar, VM'ler ve kullanılabilirlik kümeleri ile Azure altyapı hizmetlerinde 2013 grubu SharePoint örnek.](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Bu diyagramda Azure altyapı hizmetlerinde uygulanan SharePoint grubu ve her katmandaki sunucular için hata etki alanları sağlamak üzere kullanılabilirlik kümeleri gösterilir.
  
## <a name="see-also"></a>Ayrıca Bkz

[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)
  
[SharePoint Server 2013 kullanarak Microsoft Azure'daki İnternet Siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Microsoft Azure'da SharePoint Server 2013 Olağanüstü Durum Kurtarma](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)