---
title: Project Server 2007 destek sonu yol haritası
ms.author: efrene
author: efrene
manager: scotv
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
description: 10 Ekim 2017'de Project Server 2007, Project Portfolio Server ve Project 2007 desteği sona erdi. Yükseltmenizi şimdi planlamak için bu makaleyi kullanın.
ms.openlocfilehash: 3abceb4eb9d26cf8d9b5394265ba84cf7dc714ba
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941140"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 destek sonu yol haritası

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Office 2007 sunucuları ve uygulamaları için destek 2017'de sona erdi ve geçiş planlarını göz önünde bulundurmanız gerekiyor. Şu anda Project Server 2007 ve ilgili ürünleri kullanıyorsanız aşağıdaki destek sonu tarihlerini not edin:
  
|**Ürün**|**Destek sonu tarihi**|
|:-----|:-----|
|Project Server 2007  <br/> |10 Ekim 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 Ekim 2017  <br/> |
|Project 2007 Standard  <br/> |10 Ekim 2017  <br/> |
|Project 2007 Professional  <br/> |10 Ekim 2017  <br/> |
   
Office 2007 sunucularının kullanımdan kaldırılması hakkında daha fazla bilgi için bkz. [Office 2007 sunucularından ve istemci ürünlerinden yükseltme](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>*Destek sonu* ne anlama gelir?

Microsoft ürünlerinin çoğu, yeni özellikler, hata düzeltmeleri, güvenlik düzeltmeleri vb. edindikleri bir destek yaşam döngüsüne sahiptir. Bu yaşam döngüsü genellikle ürünün ilk sürümünden itibaren 10 yıl sürer. Bu yaşam döngüsünün sonu, ürünün destek sonu olarak bilinir. Project Server 2007 10 Ekim 2017'de destek sonuna ulaştığından, Microsoft artık şunları sağlamamaktadır:
  
- Oluşabilecek sorunlar için teknik destek.
    
- Sunucunun kararlılığını ve kullanılabilirliğini etkileyebilecek sorunlar için hata düzeltmeleri.
    
- Sunucuyu güvenlik ihlallerine açık hale getirebilecek güvenlik açıklarına yönelik güvenlik düzeltmeleri.
    
- Saat dilimi güncelleştirmeleri.
    
Project Server 2007 yüklemeniz bu tarihten sonra çalışmaya devam edecektir. Ancak, daha önce listelenen değişiklikler nedeniyle, project server 2007'den en kısa sürede geçmenizi kesinlikle öneririz.
  
## <a name="what-are-my-options"></a>Seçeneklerim nelerdir?

Project Server 2007 kullanıyorsanız geçiş seçeneklerinizi incelemeniz gerekir; bunlar şunlardır:
  
- Project Online'a geçiş
    
- Project Server'ın daha yeni bir şirket içi sürümüne geçiş (tercihen Project Server 2016)
    
|**Neden Project Online'a geçmeyi tercih ederim?**|**Neden Project Server 2016'ya geçmeyi tercih ederim?**|
|:-----|:-----|
| Mobil kullanıcılarım var.  <br/> <br/>Geçiş maliyetleri önemli bir sorundur (donanım, yazılım, saatler ve uygulama çabası). <br/><br/>  Geçiş sonrasında ortamımı koruma maliyetleri önemli bir sorundur (örneğin, otomatik güncelleştirmeler, garantili çalışma süresi vb.).  <br/> | İş kuralları, işletmemi bulutta çalıştırmamı kısıtlar.<br/><br/>  Ortamımdaki güncelleştirmeleri denetlemem gerekiyor.  |
   
> [!NOTE]
> Office 2007 sunucularınızdan geçiş seçenekleri hakkında daha fazla bilgi için bkz. [Office 2007 sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2007-servers-and-products.md). Project Server ve Project Online aynı kaynak havuzunu paylaşamadığından, Project Server'ın karma yapılandırmayı desteklemediğini unutmayın. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Project Server 2007'den geçiş yaparken dikkat edilmesi gereken önemli noktalar

Project Server 2007'den geçiş yapmayı planlarken aşağıdakileri göz önünde bulundurun:
  
- **Microsoft İş Ortağından yardım alma** - Project Server 2007'den yükseltme zor olabilir ve çok fazla hazırlık ve planlama gerektirir. Project Server 2007'yi ilk olarak ayarlayan kişi siz değilseniz bu özellikle zor olabilir. Neyse ki, Ister Project Server 2016'ya ister Project Online'a geçirmeyi planlayın, size yardımcı olabilecek Microsoft İş Ortakları vardır. Microsoft İş Ortağı Merkezi'nden geçiş işleminize yardımcı olması için [bir Microsoft İş Ortağı](https://go.microsoft.com/fwlink/p/?linkid=841249) arayın. Project'te uzmanlığı olan tüm Microsoft İş Ortaklarının listesini görüntülemek için  *Altın Proje ve Portföy Yönetimi* terimini arayın. 
    
- **Özelleştirmelerinizi planlama** - Project Server 2007 ortamınızda yaptığınız özelleştirmelerin çoğu, Project Server 2016 veya Project Online'a geçiş yaptığınızda çalışmayabilir. Sürümler arasında Project Server mimarisinde önemli farklılıklar vardır. Desteklenen gerekli işletim sistemleri, veritabanı sunucuları ve istemci web tarayıcıları da farklılık gösterir. Yeni ortam için özelleştirmelerinizi test etme veya yeniden derlemeyi planlayın. Planlama, her özelleştirmenin hala gerekli olup olmadığını düşünmek için iyi bir fırsat sağlar. Daha fazla bilgi için bkz. [SharePoint 2013'e yükseltme sırasında geçerli özelleştirmeler için plan oluşturma](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Zaman ve sabır** - Yükseltme planlaması, yürütme ve test, özellikle Project Server 2016'ya yükseltirseniz zaman ve çaba gerektirir. Örneğin, Project Server 2007'den Project Server 2016'ya geçiş yapıyorsanız, önce Project Server 2010'a geçmeniz, verilerinizi denetlemeniz ve ardından birbirini izleyen her sürüme geçiş yaparken aynı şeyi yapmanız gerekir. Ne kadar süreceğine ve maliyetine yönelik tahminler almak için bir Microsoft İş Ortağına danışın.
    
## <a name="migrate-to-project-online"></a>Project Online'a geçiş

Project Server 2007'den Project Online'a geçiş yapmayı seçerseniz, proje planı verilerinizi el ile geçirmek için aşağıdakileri yapabilirsiniz:
  
1. Project Server 2003'ten .mpp biçimine proje planlarınızı kaydedin.
    
2. Project Professional 2013, Project Professional 2016 veya Project Online Masaüstü İstemcisi'nde, her .mpp dosyasını açın ve ardından kaydedip Project Online'da yayımlayın.
    
Microsoft Project Web App (PWA) yapılandırmanızı Project Online'da el ile oluşturabilirsiniz. Örneğin, gerekli özel alanları veya kurumsal takvimleri yeniden oluşturun. Microsoft İş Ortakları da bu işlemde yardımcı olabilir.
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Online ile çalışmaya başlama](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Project Online'ı ayarlama ve kullanma <br/> |
|[Project Online Hizmet Açıklamaları](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Kullanabileceğiniz farklı Project Online planları hakkında bilgi <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Project Server'ın daha yeni bir şirket içi sürümüne geçiş

Project Online'a geçiş yaparak en iyi değeri ve kullanıcı deneyimini elde ettiğinize kesinlikle inanıyoruz. Ancak bazı kuruluşların proje verilerini şirket içi ortamda tutması gerektiğini de anlıyoruz. Proje verilerinizi şirket içinde tutmayı seçerseniz, Project Server 2007 ortamınızı Project Server 2010, Project Server 2013 veya Project Server 2016'ya geçirebilirsiniz.
  
Project Online'a geçiremiyorsanız, Project Server 2016'ya geçmenizi öneririz. Project Server 2016, Project Server'ın önceki sürümlerinin tüm özelliklerini içerir. Bazı özellikler yalnızca Project Online'da kullanılabilse de, Project Online ile sağlanan deneyimle en yakından eşleşir.
  
Her geçiş sonrasında verilerinizin başarıyla geçirildiğini denetlemeniz gerekir.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Project Server 2016'ya nasıl geçiş yapabilirim?

Project Server 2007 ile Project Server 2016 arasındaki mimari farklılıklar doğrudan geçiş yolunu engeller. Bu nedenle, Project Server 2007 verilerinizi Project Server 2016'ya ulaşana kadar Project Server'ın birbirini izleyen her sürümüne geçirmeniz gerekir.
  
Project Server 2016'da şu adımları izleyin:
  
1. Project Server 2007'den Project Server 2010'a geçiş.
    
2. Project Serve 2010'dan Project Server 2013'e geçiş yapın.
    
3. Project Server 2013'ten Project Server 2016'ya geçiş.
    
Her geçiş sonrasında verilerinizin başarıyla geçirildiğini doğrulayın.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>1. Adım: Project Server 2007'den Project Server 2010'a geçiş

Project Server 2007'den Project Server 2010'a yükseltmek için yapmanız gerekenlerin kapsamlı bir açıklaması için bkz. [Project Server 2010'a yükseltme](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Server 2010 yükseltmeye genel bakış](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |Project Server 2007'den Project Server 2010'a yükseltmek için yapmanız gerekenlerin üst düzey görünümü <br/> |
|[Project Server 2010'a Yükseltmeyi Planlama](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Sistem Gereksinimleri de dahil olmak üzere Project Server 2007'den Project Server 2010'a yükseltme yaparken dikkat edilmesi gereken planlama konuları  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Nasıl yükseltebilirim?

Ayrıntılar için bkz. [Project Server 2010'a yükseltme](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Ancak yükseltmek için kullanabileceğiniz iki farklı yöntem olduğunu anlamak önemlidir:
  
- **Veritabanı ekleme yükseltmesi:** Bu yöntem yalnızca ortamınızın içeriğini yükselter, yapılandırma ayarlarını yükseltmez. Yalnızca 32 bit sunucu işletim sistemini destekleyen donanımlara dağıtılan Office Project Server 2007'den yükseltme yapıyorsanız bu gereklidir. İki tür veritabanı ekleme yükseltme yöntemi vardır:
    
  - **Veritabanı ekleme *tam yükseltmesi*** - Office Project Server 2007 veritabanlarında depolanan proje verilerinin yanı sıra SharePoint içerik veritabanında depolanan Microsoft Project Web App sitesi verilerini geçirir.
    
  - **Veritabanı ekleme *çekirdek yükseltmesi*** - Yalnızca Project Server veritabanlarında depolanan proje verilerini geçirir.
    
- **Yerinde yükseltme**: Grup için yapılandırma verileri ve grup üzerindeki tüm içerik mevcut donanıma sabit bir sırayla yükseltilir. Yükseltme işlemini başlattığınızda kurulum tüm grubu çevrimdışına alır. Yükseltme tamamlanana kadar web siteleri ve Microsoft Project Web App siteleri kullanılamaz ve ardından kurulum sunucuyu yeniden başlatır. Yerinde yükseltmeye başladıktan sonra yükseltmeyi duraklatamaz veya önceki sürüme geri döndüremezsiniz. En iyisi üretim ortamınızın yansıtılmış görüntüsünü oluşturmak ve üretim ortamınızda değil bu ortama yerinde yükseltme yapmaktır. 
    
Ek kaynaklar:
  
- [Microsoft Project Server 2010 Yükseltmesi için SuperFlow](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Project Server 2007'den Project Server 2010'a geçiş](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Project Web App Web Bölümleri için yükseltmeyle ilgili dikkat edilmesi gerekenler](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project Yazılım Geliştirme Seti (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>2. Adım: Project Server 2013'e geçiş

Verilerinizin başarıyla geçirildiğini doğruladıktan sonra, sonraki adım Project Server 2013'e geçmektir.
  
Project Server 2010'dan Project Server 2013'e yükseltmek için yapmanız gerekenlerin kapsamlı bir açıklaması için bkz. [Project Server 2013'e yükseltme](/project/upgrade-to-project-server-2016). 
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Server 2013 yükseltme işlemine genel bakış](/project/upgrade-to-project-server-2016) <br/> |Project Server 2010'dan Project Server 2013'e yükseltmek için yapmanız gerekenlere genel bakış  <br/> |
|[Project Server 2013'e yükseltmeyi planlama](/project/plan-for-upgrade-to-project-server-2016) <br/> |Sistem Gereksinimleri de dahil olmak üzere Project Server 2010'dan Project Server 2013'e yükseltme yaparken dikkat edilmesi gereken planlama konuları <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Bu sürüme yükseltme hakkında bilinmesi gerekenler

[Project Server 2013 yükseltmesindeki yenilikler](/project/what-s-new-in-project-server-2013-upgrade) , bu sürüm için yükseltmeye yönelik önemli değişiklikleri açıklar. En önemlileri şunlardır: 
  
- Project Server 2013'e yerinde yükseltme yoktur. Veritabanı ekleme yöntemi, Project Server 2010'dan Project Server 2013'e yükseltmek için desteklenen tek yöntemdir.
    
- Yükseltme işlemi Yalnızca Project Server 2010 verilerinizi Project Server 2013 biçimine dönüştürmekle kalmaz, aynı zamanda dört Project Server 2010 veritabanını tek bir Project Web App veritabanında birleştirir.
    
- 2013 sürümlerinde hem SharePoint Server hem de Project Server talep tabanlı kimlik doğrulaması olarak değiştirildi. Klasik kimlik doğrulaması kullanıyorsanız yükseltmeniz için bu faktörü göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [SharePoint 2013'te klasik moddan talep tabanlı kimlik doğrulamasına geçiş](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
Ek kaynaklar:
  
- [Project Server 2013'e yükseltme işlemine genel bakış](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Veritabanlarınızı ve Project Web App site koleksiyonlarınızı yükseltme (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Microsoft Project Server yükseltme işlemi diyagramı](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [8 Kolay Adımda Harika Veritabanı Birleştirme, Project Server 2010-2013 Geçişi](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>3. Adım: Project Server 2016'ya geçiş

Verilerinizin başarıyla geçirildiğini doğruladıktan sonra, sonraki adım Project Server 2016'ya geçiş yapmaktır.
  
Project Server 2013'ten Project Server 2016'ya yükseltmek için yapmanız gerekenlerin kapsamlı bir açıklaması için bkz. [Project Server 2016'ya yükseltme](/project/upgrading-to-project-server-2016).
  
Önemli kaynaklar:
  
|**Kaynak**|**Açıklama**|
|:-----|:-----|
|[Project Server 2016 yükseltme işlemine genel bakış](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Project Server 2013'ten Project Server 2016'ya yükseltmek için yapmanız gerekenlere genel bakış <br/> |
|[Project Server 2016'ya yükseltmeyi planlama](/project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2013'ten Project Server 2016'ya yükseltecek planlama konuları <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Bu sürüme yükseltme hakkında bilinmesi gerekenler

[Project Server 2016 yükseltmesi hakkında bilmeniz gerekenler](/project/plan-for-upgrade-to-project-server-2016) , bu sürüm için yükseltme için aşağıdaki bazı önemli değişiklikleri bildirir:
  
- Project Server 2013 verilerinizi geçirebileceğiniz Project Server 2016 ortamınızı oluşturduğunuzda, Project Server 2016 yükleme dosyaları SharePoint Server 2016'ya eklenir. Daha fazla bilgi için bkz. [Project Server 2016'yı dağıtma](/project/deploy-project-server-2016).
    
- Project Server 2016'da kaynak planları kullanım dışıdır. Project Server 2013 kaynak planlarınız Project Server 2016'da ve Project Online'da Resource Engagements'a geçirilecek. Daha fazla bilgi için bkz [. Genel Bakış: Kaynak görevlendirmeleri](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Portfolio Server 2007'den geçiş

Project Portfolio Server 2007, portföy stratejisi, öncelik belirleme ve iyileştirme için Project Server 2007 ile birlikte kullanılmıştır. Bu sürümden sonra Project Portfolio Server'ın ek sürümleri oluşturulmadı. Ancak portföy yönetimi özellikleri Project Server 2016 ve Project Online'ın Premium sürümünde kullanılabilir. Ancak Project Portfolio Server 2007'den alınan veriler de bu verilere geçirilemiyor. İş etmenleri gibi verilerin yeniden oluşturulması gerekir.
  
Diğer kaynaklar:
  
- [Project Online Hizmet Açıklamaları:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) Project Server 2016 ve Project Online Premium'a dahil edilen portföy yönetimi özelliklerine bakın.
    
- [Microsoft Office Project Portfolio Server 2007 geçiş kılavuzu.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>İlgili konular

[SharePoint Server 2007 destek sonu Yol Haritası](sharepoint-2007-end-of-support.md)
  
[Office 2007 sunucularından ve istemcilerinden yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2007-servers-and-products.md)
