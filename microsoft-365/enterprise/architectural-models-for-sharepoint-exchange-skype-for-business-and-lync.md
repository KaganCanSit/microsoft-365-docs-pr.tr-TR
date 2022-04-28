---
title: SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modeller
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modelleri, dağıtım ve platform seçeneklerini açıklayan BT posterleri edinin.
ms.openlocfilehash: 859d952fc9a2e4e9315c7fef3e56b4e59d0f60d6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096886"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modeller

Bu makaledeki BT posterleri SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modelleri ve dağıtım seçeneklerini açıklar. Ayrıca Microsoft Azure'da SharePoint dağıtmaya yönelik tasarım bilgileri de sağlar.
  
Microsoft 365 kullanarak, bulut üzerinden tanıdık işbirliği ve iletişim hizmetleri sağlayabilirsiniz. Birkaç özel durum dışında, şirket içi dağıtımı sürdürürken veya Microsoft 365 kullanırken kullanıcı deneyimi aynı kalır. 

Bu birleşik kullanıcı deneyimi, her iş yükünün nereye yerleştirileceğine karar verme kararını karmaşıklaştırır. Ayrıca şu sorulara da neden olur:
  
- Tek tek iş yükleri için nasıl bir platform seçersiniz?
    
- Herhangi bir hizmeti şirket içinde tutmak mantıklı mı?
    
- Karma dağıtım hangi senaryoda uygundur?
    
- Azure resme nasıl uyuyor?
    
- Office sunucu iş yüklerinin hangi yapılandırmaları Azure desteği?
    
> [!TIP]
> Bu makaledeki posterlerin çoğu birden çok dilde kullanılabilir. Kullanılabilir diller Çince, İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce, Rusça ve İspanyolcadır. Bu dillerden birinde poster indirmek için poster küçük resminin altında **Diğer diller'i** seçin.
  
Düşüncelerinizi bize bildirin! [Bize cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com) adresine e-posta gönderin. 
  
İhtiyacınız olan posterleri almak için aşağıdaki bağlantıları kullanın:
  
- **Mimari modeller**: SharePoint 2016 ve Skype Kurumsal 2015 için ideal platformunuzu ve yapılandırmanızı belirlemek için bu kaynakları kullanın.
    
  - [Microsoft SharePoint 2016 mimari modelleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016 veritabanları](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype Kurumsal 2015 mimari modelleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platform**: SharePoint 2013, Exchange 2013 ve Lync 2013 için ideal platformunuzu ve yapılandırmanızı belirlemek için bu kaynakları kullanın.
    
  - [SharePoint 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Azure'da SharePoint Server 2013: Azure altyapı hizmetlerinde** SharePoint Server 2013 iş yüklerini tasarlamak ve yapılandırmak için bu BT posterlerini kullanın.
    
  - [SharePoint Server 2013 kullanarak Azure'daki İnternet siteleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Tasarım örneği: SharePoint 2013 için Azure'daki İnternet siteleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Azure'a olağanüstü durum kurtarma SharePoint](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Mimari model posterleri

SharePoint 2016 ve Skype Kurumsal 2015 için BT posterleri, dağıtım yöntemlerini yazdırması kolay bir biçimde karşılaştırmak için bir yol sağlar. Posterler tüm yapılandırma veya platform seçeneklerini listeler. Her seçenek için aşağıdaki bilgileri sağlar:
  
- **Genel bakış**: Kavramsal diyagram da dahil olmak üzere platformun kısa bir özeti.
    
- **En iyisi**: Platform için ideal olan yaygın senaryolar.
    
- **Lisans gereksinimleri**: Dağıtım için ihtiyacınız olan lisanslar.
    
- **Mimari görevleri**: Mimar olarak vermeniz gereken kararlar.
    
- **BT uzmanlarına yönelik görevler veya sorumluluklar**: BT personelinizin planlama yapması gereken günlük sorumluluklar.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Microsoft SharePoint Server 2016 Mimari Modelleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2016 Mimari Modelleri posterinin küçük resmi.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=52650)    |Bu BT posteri, iş karar alıcılarının ve çözüm mimarlarının bilmesi gereken SharePoint Çevrimiçi, Azure ve SharePoint şirket içi yapılandırmalarını açıklar. <br/><br/> - **SharePoint Online (SaaS):** Hizmet olarak yazılım (SaaS) abonelik modeli aracılığıyla SharePoint kullanın. <br/> - **karma SharePoint**: SharePoint sitelerinizi ve uygulamalarınızı kendi hızınızda buluta taşıyın. <br/> - **Azure'da (IaaS) SharePoint**: Şirket içi ortamınızı Azure'a genişletin ve SharePoint 2016 sunucularını orada dağıtın. (Bu model, yüksek kullanılabilirlik veya olağanüstü durum kurtarma ortamları ve geliştirme/test ortamları için önerilir.) <br/> - **Şirket içi SharePoint**: SharePoint ortamınızı koruduğunuz bir veri merkezinde planlayın, dağıtın, koruyun ve özelleştirin.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 Veritabanları

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2016 Veritabanları posterinin küçük resmi.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=55041)    |Bu BT posteri, SharePoint Server 2016 veritabanları için hızlı bir başvurudur. Her veritabanının ayrıntılarını görürsünüz: <br/><br/> - Boyut <br/> - Ölçeklendirme kılavuzu <br/> - G/Ç desenleri <br/> - Gereksinimler <br/><br/>  İlk sayfada SharePoint sistem veritabanları ve birden çok veritabanı olan hizmet uygulamaları gösterilir. İkinci sayfada, tek veritabanları olan tüm hizmet uygulamaları gösterilir. <br/><br/>  Daha fazla bilgi için bkz. [SharePoint Server 2016'da veritabanı türleri ve açıklamaları](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype Kurumsal 2015 Mimari Modelleri

|Öğe|Açıklama|
|---|---|
|[![Skype Kurumsal Mimari Modelleri posterinin küçük resmi.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=55022)    |Bu posterde çevrimiçi, şirket içi, hibrit ve bulut özel dal değişimi (PBX) Skype Kurumsal açıklanmaktadır. Ayrıca, iş karar alıcılarının ve çözüm mimarlarının bilmesi gereken Exchange ve SharePoint yapılandırmalarıyla tümleştirmeyi açıklar. <br/><br/> Poster, BT uzmanlarına Skype Kurumsal Online ve şirket içi Skype Kurumsal kullanabilecekleri temel mimari modellerin farkındalığını artırmak için tasarlanmıştır. <br/><br/>Kuruluşunuzun gereksinimlerine ve planlara en uygun yapılandırmayla başlayın. Gerektiğinde diğer yapılandırmaları göz önünde bulundurun ve kullanın. Örneğin, Exchange ve SharePoint ile tümleştirmeyi veya Microsoft bulut PBX teklifinden yararlanan bir çözümü kullanmayı düşünebilirsiniz.|
   
## <a name="platform-options-posters"></a>Platform seçenekleri posterleri

SharePoint 2013, Exchange 2013 ve Lync 2013 için BT posterleri, dağıtım yöntemlerini bir bakışta karşılaştırmak için bir yol sağlar. Her posterde tüm yapılandırmalar veya platform seçenekleri listelenir. Her seçenek için aşağıdaki bilgileri sağlar:
  
- **Genel bakış**: Kavramsal diyagram da dahil olmak üzere platformun kısa bir özeti.
    
- **En iyisi**: Platform için ideal olan yaygın senaryolar.
    
- **Lisans gereksinimleri**: Dağıtım için ihtiyacınız olan lisanslar.
    
- **Mimari görevleri**: Mimar olarak vermeniz gereken kararlar.
    
- **BT uzmanlarına yönelik görevler veya sorumluluklar**: BT personelinizin planlama yapması gereken günlük sorumluluklar.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint 2013 Platform Seçenekleri posterinin küçük resmi.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=40332)    |İş karar alıcıları ve mimarları için bu posterde SharePoint 2013, Microsoft 365 SharePoint, Microsoft 365, Azure ve yalnızca şirket içi dağıtımlarla şirket içi karma platform seçenekleri gösterilir. Her bir mimariye genel bakış, öneriler, lisans gereksinimleri ve her platform için mimar ve BT uzmanı görevlerinin listelerini içerir. Posterde Azure'da çeşitli SharePoint çözümleri vurgulanır.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![Exchange Platform Seçenekleri posterinin küçük resmi.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=42676)    |İş karar alıcıları ve mimarları için bu posterde Exchange 2013'e yönelik platform seçenekleri açıklanmaktadır. Müşteriler Microsoft 365, karma Exchange, şirket içi Exchange Server ve barındırılan Exchange ile Exchange Online arasından seçim yapabilir. Posterde her mimari seçeneğin ayrıntıları ve her birine yönelik ideal senaryolar, lisans gereksinimleri ve BT uzmanı sorumlulukları yer alır.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Lync 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![Lync 2013 Platform Seçenekleri posterinin küçük resmi.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=41677)    |İş karar alıcıları ve mimarları için bu posterde Lync 2013'e yönelik platform seçenekleri açıklanmaktadır. Müşteriler Microsoft 365, karma Lync, şirket içi Lync Server ve barındırılan Lync ile Lync Online arasından seçim yapabilir. BT posterinde her mimari seçeneğin ayrıntıları ve her birine yönelik ideal senaryolar, lisans gereksinimleri ve BT uzmanı sorumlulukları yer alır.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure çözümleri posterlerinde SharePoint

Azure'daki SharePoint için BT posterleri, SharePoint Server 2013 kullanan Azure tabanlı çözümleri gösterir.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 Kullanarak Microsoft Azure'daki İnternet Siteleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2013 posteri kullanılarak Azure'daki İnternet sitelerinin görüntüsü.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=41992)    |Bu posterde, Azure'daki İnternet'e yönelik siteler için temel tasarım etkinlikleri ve önerilen mimari özetlenmektedir.  <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [SharePoint Server 2013 kullanarak Azure'daki İnternet siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>SharePoint 2013 için Azure'daki İnternet siteleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2013 posteri için Microsoft Azure'deki İnternet sitelerinin görüntüsü.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=41991)    |SharePoint Server 2013 kullanarak Azure'da İnternet'e yönelik bir sitenin kendi mimariniz için başlangıç noktası olarak bu tasarım örneğini kullanın. <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [SharePoint Server 2013 kullanarak Azure'daki İnternet siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>olağanüstü durum kurtarmayı Microsoft Azure SharePoint

|Öğe|Açıklama|
|---|---|
|[![Azure'a SharePoint olağanüstü durum kurtarma işleminin posterinin görüntüsü.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [Diğer diller](https://www.microsoft.com/download/details.aspx?id=41993)    |Bu BT posteri, Azure'da olağanüstü durum kurtarma ortamı için mimari ilkelerini gösterir. <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [Azure'da SharePoint Server 2013 olağanüstü durum kurtarma](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)
  
- [Microsoft bulut mimarisi modelleri](../solutions/cloud-architecture-models.md)
  
- [test laboratuvarı kılavuzlarını Microsoft 365](m365-enterprise-test-lab-guides.md)
  
- [Hibrit çözümler](hybrid-solutions.md)