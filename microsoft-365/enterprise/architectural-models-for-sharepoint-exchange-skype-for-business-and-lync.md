---
title: Lync, SharePoint, Exchange, Skype Kurumsal mimari modeller
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Lync, Exchange, Skype Kurumsal ve Lync'e mimari modeller, dağıtım ve platform seçeneklerini açıklayan IT posterlerini SharePoint.
ms.openlocfilehash: 813a143d281f85e6cbc9c0456dceaf20c674d13b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985316"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Lync, SharePoint, Exchange, Skype Kurumsal mimari modeller

Bu makaledeki IT posterlerinde, SharePoint, Exchange, Skype Kurumsal ve Lync için mimari modeller ve dağıtım seçenekleri açıklanmıştır. Ayrıca, e-SharePoint dağıtımı için tasarım Microsoft Azure.
  
Bulut Microsoft 365 kullanarak, bulut üzerinden tanıdık işbirliği ve iletişim hizmetleri sabilirsiniz. Birkaç özel durum dışında, hem şirket içi dağıtımı korurken hem de şirket içi dağıtım kullanırken kullanıcı deneyimi Microsoft 365. 

Bu birleşik kullanıcı deneyimi, her iş yükünün nereye yer aldığına ilişkin kararı karmaşıklaştırıyor. Ayrıca, şu soruları da yanıtladı:
  
- Tek tek iş yükleri için bir platform nasıl seçersiniz?
    
- Herhangi bir hizmeti şirket içinde tutmak mantıklı mı?
    
- Karma dağıtım hangi senaryoda uygun?
    
- Azure resme nasıl uyum sağlar?
    
- Sunucu iş yüklerinin Office yapılandırmaları Azure'da hangi yapılandırmaları destekler?
    
> [!TIP]
> Bu makaledeki posterlerin çoğu birden çok dilde mevcuttur. Kullanılabilir diller arasında Çince, İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce, Rusça ve İspanyolca yer almaktadır. Bu dillerden bir poster indirmek için poster küçük resmi altında Diğer **diller'i seçin**.
  
Ne düşünüyor olurken bize haber verme! Bize e-posta [cloudadopt@microsoft.com.](mailto:cloudadopt@microsoft.com) 
  
Size gereken posterleri almak için aşağıdaki bağlantıları kullanın:
  
- **Mimari modeller**: Bu kaynakları kullanarak 2016 ve SharePoint 2015 için ideal platform ve yapılandırmanızı Skype Kurumsal kullanın.
    
  - [Microsoft SharePoint 2016 mimari modelleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016 veritabanları](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype Kurumsal 2015 mimari modelleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platform**: SharePoint 2013, Exchange 2013 ve Lync 2013 için ideal platform ve yapılandırmanızı belirlemek için bu kaynakları kullanın.
    
  - [SharePoint 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 platform seçenekleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013: Azure** altyapı hizmetlerinde SharePoint Server 2013 iş yüklerini tasarlamak ve yapılandırmak için bu IT posterlerini kullanın.
    
  - [SharePoint Server 2013'ü kullanarak Azure'daki İnternet siteleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Tasarım örneği: SharePoint 2013 için Azure'da İnternet siteleri](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Azure SharePoint da olağanüstü durum kurtarmayı kurtarma](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Mimari modeller posterleri

SharePoint 2016 ve Skype Kurumsal 2015 için IT posterleri, dağıtım yöntemlerini kolay yazdırılabilir biçimde karşılaştırmak için bir yol sağlar. Posterlerde tüm yapılandırma veya platform seçenekleri listelemektedir. Her seçenek için aşağıdaki bilgileri sağlar:
  
- **Genel** bakış: Platformun kavramsal diyagramı da içinde olmak üzere kısa bir özeti.
    
- **En iyisi**: Platform için ideal olan yaygın senaryolar.
    
- **Lisans gereksinimleri**: Dağıtım için ihtiyacınız olan lisanslar.
    
- **Mimari görevleri**: Bir mimar olarak almak zorunda olduğunuz kararlar.
    
- **IT profesyonel görevleri veya sorumlulukları**: IT personelinizin planlamak zorunda olduğu günlük sorumluluklar.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Microsoft SharePoint Server 2016 Mimari Modelleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2016 Mimari Modelleri posteri için küçük resim.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=52650)    |Bu IT posteri, iş karar vericileri ve çözüm mimarlarının SharePoint gereken şirket içi yapılandırmaları olan SharePoint Online, Azure ve diğer şirket içi yapılandırmaları açıklama şeklindedir. <br/><br/> - **SharePoint Çevrimiçi (SaaS)**: SharePoint (SaaS) abonelik modeli olarak bir yazılım aracılığıyla kullanın. <br/> - **SharePoint karma**: SharePoint sitelerinizi ve uygulamalarınızı buluta kendi hızınıza göre taşıma. <br/> - **SharePoint(IaaS)**: Şirket içi ortamınızı Azure'a genişletin ve SharePoint 2016 sunucularını burada dağıtın. (Bu model yüksek kullanılabilirlik veya olağanüstü durum kurtarma ortamları ve geliştirme/test ortamları için önerilir.) <br/> - **SharePoint oluşturma**: Korumanız gereken bir veri merkezinde SharePoint ortamınızı planlama, dağıtma, koruma ve özelleştirme.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 Veritabanları

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2016 Veritabanları posteri için küçük resim.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=55041)    |Bu IT posteri, SharePoint Server 2016 veritabanları için hızlı başvurudur. Her veritabanının ayrıntılarını burada görüyorsunuz: <br/><br/> - Boyut <br/> - Ölçeklendirme kılavuzu <br/> - I/O desenleri <br/> - Gereksinimler <br/><br/>  İlk sayfada, en SharePoint veritabanlarını ve birden çok veritabanı olan hizmet uygulamalarını görebilirsiniz. İkinci sayfada, tek veritabanları olan tüm hizmet uygulamaları görüntülenir. <br/><br/>  Daha fazla bilgi için bkz[. SharePoint Server 2016'da veritabanı türleri ve açıklamaları](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype Kurumsal 2015 Mimari Modelleri

|Öğe|Açıklama|
|---|---|
|[![Mimari Modeller posterine Skype Kurumsal küçük resmi.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=55022)    |Bu posterde Skype Kurumsal Online, şirket içi, karma ve bulut özel şube değişimi (PBX) açıklandı. Ayrıca, işletme karar vericileri ve çözüm mimarlarının Exchange ve çözüm mimarlarının SharePoint yapılandırmaları ile tümleştirmesi de açık almaktadır. <br/><br/> Poster, IT profesyonellerine, şirket içinde Skype Kurumsal Online'ın ve şirket içinde Skype Kurumsal olan temel mimari modeller farkındalığını artırmaya yöneliktir. <br/><br/>Kuruluşun ihtiyaçlarına ve planlarına en uygun yapılandırmayla çalışmaya başlayabilirsiniz. Gereken diğer yapılandırmaları göz önünde bulundurarak kullanın. Örneğin, Exchange ve SharePoint ile tümleştirmeyi veya Microsoft bulut PBX tekliflerinden yararlanan bir çözümü göz önünde bulundurabilirsiniz.|
   
## <a name="platform-options-posters"></a>Platform seçenekleri posterleri

SharePoint 2013, Exchange 2013 ve Lync 2013 için IT posterleri, dağıtım yöntemlerini bir bakışta karşılaştırmanın bir yolunu sunar. Her poster, tüm yapılandırmaları veya platform seçeneklerini listeler. Her seçenek için aşağıdaki bilgileri sağlar:
  
- **Genel** bakış: Platformun kavramsal diyagramı da içinde olmak üzere kısa bir özeti.
    
- **En iyisi**: Platform için ideal olan yaygın senaryolar.
    
- **Lisans gereksinimleri**: Dağıtım için ihtiyacınız olan lisanslar.
    
- **Mimari görevleri**: Bir mimar olarak almak zorunda olduğunuz kararlar.
    
- **IT profesyonel görevleri veya sorumlulukları**: IT personelinizin planlamak zorunda olduğu günlük sorumluluklar.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint 2013 Platform Seçenekleri posteri küçük resmi.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=40332)    |İş karar vericileri ve mimarlar için bu posterde SharePoint 2013, SharePoint'te Microsoft 365 SharePoint, Microsoft 365, Azure ve yalnızca şirket içi dağıtımlarla şirket içi karma için platform seçenekleri bulunmaktadır. Her bir mimariye genel bir bakış, öneriler, lisans gereksinimleri, her bir platform için mimarlar ve IT profesyonel görevleri listeleri içerir. Posterde, Azure'SharePoint ilgili çeşitli çözümler vurgulanır.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![Platform Seçenekleri posteri Exchange küçük resmi.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=42676)    |İş karar vericileri ve mimarlar için, bu posterde 2013'Exchange platform seçenekleri açıklandı. Müşteriler şirket içinde Exchange Online, Microsoft 365 karma Exchange, Exchange Server barındırma hizmetlerinden birini Exchange. Posterde mimari seçeneklerin ayrıntıları ve her biri için ideal senaryolar, lisans gereksinimleri ve IT profesyonel sorumlulukları yer almaktadır.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Lync 2013 Platform Seçenekleri

|Öğe|Açıklama|
|---|---|
|[![Lync 2013 Platform Seçenekleri posterini küçük resim görüntüsü.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=41677)    |İşletme karar vericileri ve mimarlar için, bu posterde Lync 2013 için platform seçenekleri açıklanacak. Müşteriler lync çevrimiçi, Microsoft 365 Lync, şirket içi Lync Server ve barındırılan Lync ile Lync Online'dan birini seçebilirler. IT posteri, mimari seçeneklerin her biri için ideal senaryolar, lisans gereksinimleri ve IT profesyonel sorumlulukları gibi ayrıntılarıyla sunar.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint çözümleri posterlerine bakın

Azure'daki SharePoint için IT posterleri, SharePoint Server 2013'ü kullanan Azure tabanlı çözümleri gösterir.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013'te Microsoft Azure Siteleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2013 posterini kullanarak Azure'daki İnternet sitelerinin resmi.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=41992)    |Bu posterde, Azure'da İnternet'e yönelik siteler için önemli tasarım etkinlikleri ve önerilen mimari ana hatlarıyla açıklandı.  <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [SharePoint Server 2013'ü kullanarak Azure'daki İnternet siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>SharePoint 2013 için Azure'da İnternet siteleri

|Öğe|Açıklama|
|---|---|
|[![SharePoint Server 2013 posteri için Microsoft Azure'de İnternet sitelerinin resmi.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=41991)    |SharePoint Server 2013 kullanarak Azure'da İnternet'e yönelik bir sitenin mimarisine yönelik kendi mimariniz için başlangıç noktası olarak bu tasarım örneğini kullanın. <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [SharePoint Server 2013'ü kullanarak Azure'daki İnternet siteleri](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint Için Olağanüstü Durum Kurtarmayı Microsoft Azure

|Öğe|Açıklama|
|---|---|
|[![Acil durum kurtarma işleminin Azure'a SharePoint posteri resmi.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [Fazla dil](https://www.microsoft.com/download/details.aspx?id=41993)    |Bu IT posteri, Azure'da olağanüstü bir kurtarma ortamı için mimari ilkelerini gösterir. <br/><br/> Daha fazla bilgi için aşağıdaki makalelere bakın:  <br/><br/> - [SharePoint Server 2013'te olağanüstü durum geri yüklemesi](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 için Azure mimarileri](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)
  
- [Microsoft bulut mimarisi modelleri](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)
  
- [Karma çözümler](hybrid-solutions.md)