---
title: Project Server 2007 destek sonu yol haritası
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 10 Ekim 2017'de, Project Server 2007, Project Portfolio Server ve Project 2007 desteği sona erdi. Şimdi yükseltmenizi planlamak için bu makaleyi kullanın.
ms.openlocfilehash: c492c7154006a139589cff1c768dd77c13804c07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984018"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 destek sonu yol haritası

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

2017'de Office 2007 sunucuları ve uygulamaları için destek sona erdi ve geçiş planlarını düşünmen gerekiyor. Şu anda Project Server 2007 ve ilgili ürünleri kullanıyorsanız, aşağıdaki destek sonu tarihlerini not olun:
  
|**Ürün**|**Destek tarihi sonu**|
|:-----|:-----|
|Project Server 2007  <br/> |10 Ekim 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 Ekim 2017  <br/> |
|Project 2007 Standard  <br/> |10 Ekim 2017  <br/> |
|Project 2007 Professional  <br/> |10 Ekim 2017  <br/> |
   
Sunucularının emeklilikte Office 2007 sunucuları hakkında daha fazla bilgi için bkz. [Office 2007 sunucularından ve istemci ürünlerinden yükseltme](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. Sunucu Project 2007 10 Ekim 2017'de destek sonuna ulaştığı için, Microsoft artık şunları sağlar:
  
- Ortaya çıkabilir sorunlar için teknik destek.
    
- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.
    
- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.
    
- Saat dilimi güncelleştirmeleri.
    
Project Server 2007 yüklemeniz bu tarihten sonra da çalışmaya devam edecektir. Ancak, daha önce listelenen değişikliklerden dolayı, pratik olduğu anda Project Server 2007'den geçişnizi kesinlikle öneririz.
  
## <a name="what-are-my-options"></a>Seçeneklerim neler?

Project Server 2007 kullanıyorsanız, geçiş seçeneklerinizi incelemeniz gerekir. Bu seçenekler şunlardır:
  
- Geçiş Project Online
    
- Project Server'ın daha yeni bir şirket içi sürümüne (tercihen Project Server 2016)
    
|**Neden geçiş tercih Project Online**|**Neden geçiş tercih Project Server 2016**|
|:-----|:-----|
| Mobil kullanıcılarım var.  <br/> <br/>Geçişin maliyetleri önemli bir sorun (donanım, yazılım, saatler ve uygulamaya çalışma çabası). <br/><br/>  Geçiş sonrasında, ortamımı bakım maliyetleri büyük bir sorun (örneğin, otomatik güncelleştirmeler, garantili çalışma süresi, vb.).  <br/> | İş kuralları işletmemi bulutta çalıştırmamı kısıtlar.<br/><br/>  Ortamımda yapılan güncelleştirmeleri denetlemem gerekiyor.  |
   
> [!NOTE]
> Office 2007 sunucularından taşıma seçenekleri hakkında daha fazla bilgi için, [Office 2007](upgrade-from-office-2007-servers-and-products.md) sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar'a bakın. Project Server ile Project Online Sunucu aynı kaynak havuzunu paylaşa Project, karma yapılandırmayı desteklemez. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Project Server 2007'den geçiş

Project Server 2007'den geçiş yapmayı planken aşağıdaki Project göz önünde yapın:
  
- **Microsoft İş Ortağından yardım** al - Project Server 2007'den yükseltme zor olabilir ve çok fazla hazırlık ve planlama gerektirir. En başta Sunucu 2007'nin sunucularını ayar Project bu zor olabilir. Neyse ki, iş ortağınıza veya iş ortağınıza geçiş yapmayı planlayın, Project Server 2016 Microsoft Project Online. Microsoft İş Ortağı Merkezi'nde geçiş işleminize yardımcı olacak [bir Microsoft İş Ortağı arama.](https://go.microsoft.com/fwlink/p/?linkid=841249) Microsoft hesabı konusunda uzmanlığı *olan tüm Microsoft Project İş* Ortaklarının listesini görüntülemek için Gold Destek ve Portföy Yönetimi Project. 
    
- **Özelleştirmelerinizi planlama** - Project Server 2007 ortamınıza geçişte veya bu ortamda yapmış olabileceğiniz özelleştirmelerin birçoğu Project Server 2016 Project Online. Sunucu mimarisinde sürümler Project arasında önemli farklılıklar vardır. Desteklenen gerekli işletim sistemleri, veritabanı sunucuları ve istemci web tarayıcıları da farklıdır. Özelleştirmelerinizi yeni ortam için test yapmayı veya yeniden oluşturmayı planla. Planlama ayrıca, her özelleştirmenin hala gerekli olup olmadığını düşünmek için iyi bir fırsat sağlar. Daha fazla bilgi için bkz[. 2013'e yükseltme sırasında geçerli özelleştirmeler SharePoint oluşturma](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Zaman ve sabır** - Yükseltmeyi planlama, yürütme ve test etme, özellikle de yükseltme işlemini tamamlarsanız zaman ve Project Server 2016. Örneğin, Project Server 2007'den Project Server 2016'e geçirirken, önce Project Server 2010'a geçirmeniz, verilerinizi denetlemeniz ve sonra da birbirini takip eden her sürüme geçişte aynı şeyi başarmanız gerekir. Ne kadar sürenin ve ne kadar maliyeti olduğunu tahmin etmek için bir Microsoft İş Ortağı ile birlikte kontrol etmek iyi bir yol olabilir.
    
## <a name="migrate-to-project-online"></a>Geçiş Project Online

Project Server 2007'den başka bir Project Online, proje planı verilerinizi el ile geçirmek için şunları yapabilirsiniz:
  
1. Project Server 2003'den .mpp biçimine kadar proje planlarınızı kaydedin.
    
2. Project Professional 2013, Project Professional 2016 veya Project Online Masaüstü İstemcisi'nde, her .mpp dosyasını açın ve ardından dosyayı kaydedp Project Online.
    
Web App (Microsoft Project) yapılandırmanızı el ile PWA web Project Online. Örneğin, gerekli özel alanları veya kuruluş takvimlerini yeniden oluşturun. Microsoft İş Ortakları da bu işlemde yardımcı olabilir.
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Online ile çalışmaya başlama](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |E-bilgileri ayarlama ve Project Online <br/> |
|[Project Online Açıklamalarını Girin](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Size uygun Project Online planlara ilişkin bilgiler <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Project Server'ın daha yeni bir şirket içi sürümüne geçiş

En iyi değeri ve kullanıcı deneyimini elde etmek için Aşağıdakiler'e Project Online. Ancak bazı kuruluşların proje verilerini bir şirket içi ortamda tutmaları gerekmektedir. Proje verilerinizi şirket içinde tutmayı seçerseniz, Project Server 2007 ortamınızı Project Server 2010, Project Server 2013 veya başka bir Project Server 2016.
  
Project Online'a Project Server 2016. Project Server 2016, Project Server'ın önceki tüm Project içerir. Bazı özellikler yalnızca Yakın Project Online'de mevcut olsa da, en yakın şekilde kullanılabilen deneyime Project Online.
  
Her geçiş sonrasında, verilerinizin başarıyla geçir geçir başarıyla geçir geçir olup denetlemeniz gerekir.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Project Server 2016'a nasıl Project Server 2016?

Project Server 2007 ile Project Server 2016 arasındaki mimari farklılıkları doğrudan geçiş yolunu engeller. Bu nedenle, Project Server 2007 verilerinizi bu sunucuya ulaşana kadar Project Server'ın her Project Server 2016.
  
Adımları takip etmek Project Server 2016:
  
1. Project Server 2007'den Project Server 2010'a geçiş.
    
2. Project Serve 2010'dan Project Server 2013'e geçirme.
    
3. Project Server 2013'den başka bir Project Server 2016.
    
Her geçiş sonrasında, verilerinizin başarıyla geçirildikten emin olun.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>1. Adım: Project Server 2007'den Project Server 2010'a geçirme

Project Server 2007'den Project Server 2010'a yükseltmek için ne yapmak zorunda olduğunu kapsamlı bir açıklama için bkz. [Project Server 2010'a yükseltme](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Server 2010 yükseltmeye genel bakış](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |Project Server 2007'den Project Server 2010'a yükseltmek için Project görünümü <br/> |
|[Project Server 2010'a yükseltmeyi planlama](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Project Server 2007'den Project Server 2010'a yükseltme işlemi sırasında, Sistem Gereksinimleri de içinde olmak üzere planlamada dikkate alınacak noktalar  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Nasıl yükseltim?

Ayrıntılar için bkz. [Project Server 2010'a yükseltme](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Ama yükseltmek için kullanabileceğiniz iki farklı yöntem olduğunu anlamanız önemlidir:
  
- **Veritabanı ekleme yükseltmesi:** Bu yöntem yalnızca ortamınıza uygun içeriği yükseltmez, yapılandırma ayarlarını yükseltmez. Yalnızca 32 bit sunucu işletim sistemini destekleyen bir donanıma dağıtılmış Office Project Server 2007'den yükseltme sırasında bu gereklidir. İki tür veritabanı ekleme yükseltme yöntemi vardır:
    
  - **Veritabanı ekleme *tam*** yükseltmesi - Office Project Server 2007 veritabanlarında depolanan proje verilerini ve ayrıca Microsoft Project içerik veritabanında depolanan SharePoint verilerini geçirir.
    
  - **Veritabanı ekleme *çekirdek yükseltmesi*** - Yalnızca Project Server veritabanlarında depolanan proje verilerini geçirir.
    
- **Yerinde yükseltme**: Grup için yapılandırma verileri ve grup içeriğinin tüm içeriği, var olan donanımda sabit bir sırada yükseltilir. Yükseltme işlemini başlatsanız, kurulum tüm grubu çevrimdışına alır. Yükseltme Microsoft Project sonra web siteleri ve Web App siteleri kullanılamaz, ardından kurulum sunucuyu yeniden başlatın. Yerinde yükseltmeye başladıktan sonra, yükseltmeyi duraklatabilir veya önceki sürüme geri dönebilirsiniz. En iyisi üretim ortamının ayna görüntüsünü yansıtmak ve üretim ortamınıza değil, bu ortama yerinde yükseltme yapmaktır. 
    
Ek kaynaklar:
  
- [Microsoft Project Server 2010 Yükseltmesi için SuperFlow](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Project Server 2007'den Project Server 2010'a geçiş](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Web App yükseltmesi için Project dikkate Web Bölümleri](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project Yazılım Geliştirme Seti (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>2. Adım: Project Server 2013'e geçirme

Verilerinizin başarıyla geçirildikten sonra, bir sonraki adım Project Server 2013'e geçirmektir.
  
Project Server 2010'dan Project Server 2013'e yükseltmek için neler yapmak zorunda olduğunu kapsamlı bir açıklama için bkz. [Project Server 2013'e](/project/upgrade-to-project-server-2016) yükseltme. 
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Server 2013 yükseltme sürecine genel bakış](/project/upgrade-to-project-server-2016) <br/> |Project Server 2010'dan Project Server 2013'e yükseltmek için Project genel bakış  <br/> |
|[Project Server 2013'e yükseltmeyi planlama](/project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2010'dan Project Server 2013'e yükseltme işlemi sırasında, Sistem Gereksinimleri de içinde olmak üzere planlamada dikkate alınacak noktalar <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Bu sürüme yükseltme hakkında bilgi

[Server 2013'Project](/project/what-s-new-in-project-server-2013-upgrade) sürümündeki değişiklikler, bu sürüme yükseltmeyle ilgili önemli değişiklikleri açıklar. En önemlileri: 
  
- Project Server 2013'e yerinde yükseltme yoktur. Project Server 2010'dan Project Server 2013'e yükseltirken desteklenen tek yöntem veritabanı ekleme yöntemidir.
    
- Yükseltme işlemi, Project Server 2010 verilerinizi Project Server 2013 biçimine dönüştürmekle birlikte dört Project Server 2010 veritabanını da tek bir Project Web App veritabanında birleştirecek.
    
- 2013 sürümlerinde, hem SharePoint Server hem de Project Server, talep tabanlı kimlik doğrulamasıyla değiştirildi. Klasik kimlik doğrulamasını kullanıyorsanız, yükseltmeniz için bu faktörü göz önünde bulundurabilirsiniz. Daha fazla bilgi için bkz[. SharePoint 2013'te](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) klasik moddan talep tabanlı kimlik doğrulamaya geçirme.
    
Ek kaynaklar:
  
- [Project Server 2013'e yükseltme sürecine genel bakış](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Veritabanlarınızı ve Web App site Project yükseltme (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Microsoft Project Server yükseltme işlemi diyagramı](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [8 Kolay Adımda Sunucu 2010'Project 2013 Geçişi için Mükemmel Veritabanı Birleştirmesi](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>3. Adım: Geçiş Project Server 2016

Verilerinizin başarıyla geçirilir olduğunu doğruladikten sonra, bir sonraki adım verilerinizi başka bir Project Server 2016.
  
Project Server 2013'e yükseltme yapmak için neler Project Server 2016 kapsamlı bir açıklama için bkz. [Project Server 2016.](//project/upgrading-to-project-server-2016)
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Hızlı yükseltme Project Server 2016 genel bakış](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Project Server 2013'den yükseltme yapmak için neleri Project Server 2016 <br/> |
|[Yükseltme işlemini Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2013'ü yükseltmeniz ve planlamada dikkate Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Bu sürüme yükseltme hakkında bilgi

[Yükseltme işlemiyle ilgili olarak Project Server 2016 şeyler,](/project/plan-for-upgrade-to-project-server-2016) bu sürüme yükseltmeyle ilgili bazı önemli değişiklikler sağlar. Bu değişiklikler şunlardır:
  
- Project Server 2013 verilerinizi geçirebilirsiniz Project Server 2016 ortamınızı  oluşturdukta, Project Server 2016 yükleme dosyaları SharePoint Server 2016'ya dahil edilir. Daha fazla bilgi için bkz[. Dağıtım Project Server 2016](/project/deploy-project-server-2016).
    
- Kaynak planları proje Project Server 2016. Project Server 2013 kaynak planlarınız, Project Server 2016'de ve kaynak planlarında Kaynak Görev Project Online. Daha [fazla bilgi için bkz. Genel bakış: Kaynak](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) görev atamaları. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Portfolio Server 2007'den geçiş

Project Portfolio Server 2007, Project stratejisi, öncelik belirleme ve iyileştirme için Project Server 2007 ile kullanılmıştır. Bu sürümden sonra Project Portfolio Server'ın başka sürümü oluşturulmadı. Öte yandan, portföy yönetimi özellikleri Project Server 2016 sürüm Premium sürümde Project Online. Ancak, Project Portfolio Server 2007'den veriler de geçirilmez. İş sürücüleri gibi verilerin yeniden oluşturulması gerekir.
  
Diğer kaynaklar:
  
- [Project Online Açıklamaları:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) İş ve Hizmet Açıklamaları ile birlikte Project Server 2016 portföy Project Online Ekstra.
    
- [Microsoft Office Project Portfolio Server 2007 geçiş kılavuzu.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>İlgili konular

[SharePoint Server 2007 destek sonu Yol Haritası](sharepoint-2007-end-of-support.md)
  
[Office 2007 sunucularından ve istemcilerinden yükseltmeye yardımcı olan kaynaklar](upgrade-from-office-2007-servers-and-products.md)
