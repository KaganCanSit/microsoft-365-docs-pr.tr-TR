---
title: Project Server 2010 destek sonu yol haritası
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
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
description: Sunucu 2010 için Project desteği 13 Nisan 2021'de sona erer. Bu makaleyi, Project Online Server şirket içi sürümünü veya daha yeni bir Project kılavuz olarak kullanın.
ms.openlocfilehash: 9d04df22af0a0614270907f4ad4026324b026211
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988772"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 destek sonu yol haritası

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Project Server 2010, **13 Nisan 2021'de destek sonuna ulaşacak**. Bu tarih, 13 Ekim 2020'de bir önceki destek sonu tarihine kadar uzatıldı. Şu anda Project Server 2010 kullanıyorsanız, bu konuyla ilgili ürünlerin destek sonu tarihlerini unutmayın:

|Ürün |Destek tarihi sonu|
|---|---|
|Project 2010 Standard|13 Ekim 2020|
|Project 2010 Professional|13 Ekim 2020|

Destek sonuna ulaşma konusunda daha fazla bilgi için bkz. Office [2010 sunucularından ve istemci ürünlerinden yükseltme](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Neredeyse bütün Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik güncelleştirmeleri elde eder. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. 13 Project 2021'de Sunucu 2010 destek sonuna ulaştıktan sonra, Microsoft artık şunları sağlamaz:

- Ortaya çıkabilir sorunlar için teknik destek.

- Bulunan ve sunucunun kararlılığıyla kullanılabilirliğini etkilebilir olan sorunlar için hata düzeltmeleri.

- Bulunan ve sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Project Server 2010 yüklemeniz bu tarihten sonra da çalışmaya devam edecektir. Ancak, daha önce listelenen değişikliklerden dolayı en kısa zamanda Project Server 2010'dan geçişnizi kesinlikle öneririz.

## <a name="what-are-my-options"></a>Seçeneklerim neler?

Geçiş seçenekleriniz şunlardır:

- Geçiş Project Online

- Project Server'ın daha yeni bir şirket içi sürümüne (tercihen Project Server 2019) geçirme

Project Server 2010 desteğinin sona erer.

![Project Server 2010 yükseltme yollarını girin.](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Project Server 2019'a geçişi neden tercih  ederim?|Neden geçiş tercih Project Online?|
|---|---|
|İş kuralları işletmemi bulutta çalıştırmamı kısıtlar.  <br/><br/>  Ortamımda yapılan güncelleştirmeleri denetlemem gerekiyor.|Mobil veya uzak kullanıcılarım var.<br/><br/>  Şirket içi sunucuları geçirmenin maliyetleri önemli bir sorun (donanım, yazılım, uygulama için gereken zaman ve çaba, vb.). <br/><br/>  Geçiş sonrasında, ortamımı koruma maliyetleri önemli bir sorun (örneğin, otomatik güncelleştirmeler, garantili çalışma süresi, vb.).|

> [!NOTE]
> Geçiş seçenekleriniz hakkında daha fazla bilgi için bkz. Office ve istemcilerinden [yükseltmenize yardımcı olacak kaynaklar](upgrade-from-office-2010-servers-and-products.md). Project Server ile Project Sunucu aynı kaynak havuzunu paylaşa Project Online, karma yapılandırmayı desteklemez.

### <a name="what-are-my-options-for-project-client"></a>bu istemci için seçeneklerim Project?

Project Professional 2010 veya Project Standard 2010 kullanıyorsanız, seçenekleriniz şunlardır:

- Project Professional veya Project Standard'un daha yeni bir sürümüne Project Standard
- Web için Web için e-Project Online Project çevrimiçi bir çözüme taşıma

#### <a name="move-to-a-newer-version-of-project-client"></a>Project istemcisinin daha yeni bir sürümüne taşıma

Project Standard 2010'dan yeni bir sürüme (Project Standard 2019) Project Standard sürümüne Project Standard 2016 veya Project Standard. En son özelliklerden yararlanmak için en yeni sürüme taşımayı öneririz. Daha az güncel bir sürüme (Project Standard 2016) geçiş aynı zamanda daha erken bir sürüme geçiş de ihtiyacınız olduğu anlamına gelir.

Benzer şekilde, Project Professional 2010'dan Project Professional 2010 veya daha yeni bir sürüme Project Professional 2016. Tekrar, mümkünse en yeni sürüme geçin. Project Server'a bağlanmak için Project Professional kullanıyorsanız, Project Professional Server'ın, kullanmakta olduğu Project Server sürümüne bağlanan bir sürüme geçiş yapmaya emin olun.

Project Professional 2010 kullanıcıları, Project Online Project Professional 2019'un abonelik tabanlı bir sürümü olan Project Professional Masaüstü istemcisini de geçirebilirsiniz. Project Plan 3 ve Project Plan 5 dahildir.

#### <a name="move-to-an-online-solution"></a>Çevrimiçi bir çözüme geç

Ayrıca, Project Professional 2010 veya Project Standard 2010'dan abonelik tabanlı Project çözümüne geçiş de edebilirsiniz. Hem Project Plan 3 hem de Plan 5 web Project Online en yeni bulut [tekliflerini Project sunar](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Her ikisi de keşfetmeye değer yeni özellikler ve avantajlar sunar.

Özellikler ve lisanslar hakkında daha fazla bilgi için bkz[. Microsoft Project açıklama.](/office365/servicedescriptions/project-online-service-description/project-online-service-description)

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Project Server 2010'dan Project önemli noktalar

Project Server 2010'dan geçiş yapmayı planla karşılarken şunları göz önünde Project:

- **Microsoft çözüm sağlayıcısından yardım al** - Project Server 2010'dan yükseltme zor olabilir. Çok fazla hazırlık ve planlama gerektirir. İlk olarak Server 2010'da ayarlamayı yapan kişi siz değil Project zor olabilir. Project Server 2019'a veya başka bir Project Online. Microsoft çözüm sağlayıcısı merkezinde bir [çözüm sağlayıcısını arama](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Özelleştirmelerinizi planlama** - Project Server 2010 ortamınızı Project Server 2019 veya başka bir Project Online. Sunucu mimarisinde sürümler Project arasında önemli farklılıklar vardır. Ayrıca, sürümlerle çalışan gerekli işletim sistemleri, veritabanı sunucuları ve web tarayıcıları farklıdır. Özelleştirmelerinizi yeni ortamda test etmek veya yeniden oluşturma hakkında bir plan hazırlarsınız. Belirli özelleştirmelerin hala gerekli olup olmadığını belirlemek için bu fırsatı değerlendirin. Daha fazla bilgi için bkz[. 2013'e yükseltme sırasında geçerli özelleştirmeler SharePoint oluşturma](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Zaman ve sabır** - Yükseltmeyi planlama, yürütme ve test etme, özellikle de Project Server 2019 yükseltmesi için önemli ölçüde zaman ve çaba gerektirir. Project Server 2010'dan Project Server 2019'a geçiş ediyorsanız, önce Project Server 2013'e geçirmeniz, verilerinizi denetlemeniz, sonra Project Server 2016'e ve sonra da Project Server 2019'a geçirmeniz gerekir. Bir zaman dilimi için Microsoft çözüm sağlayıcısına danışın ve onlara yardımcı olacak tahmini maliyet konusunda yardım alabilirsiniz.

## <a name="migrate-to-project-online"></a>Geçiş Project Online

Project Server 2010'dan başka bir Project Online, proje planı verilerinizi el ile geçirmek için aşağıdaki adımları izleyin:

1. Project Server 2010'dan .mpp biçimine kadar proje planlarınızı kaydedin.

2. Project Professional 2016, Project Professional 2019 veya Project Online Masaüstü İstemcisi'ne tıklayın, her .mpp dosyasını açın ve ardından dosyayı başka bir Project Online.

Project Online yapılandırmasını el PWA oluşturabilirsiniz (örneğin, gerekli özel alanları veya kuruluş takvimlerini yeniden oluşturun). Microsoft çözüm sağlayıcıları da bu işlemde yardımcı olabilir.

Önemli kaynaklar:

|Kaynak|Açıklama|
|---|---|
|[Project Online ile çalışmaya başlama](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|E-bilgileri ayarlama ve Project Online|
|[Project Online Hizmet Açıklaması](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Kullanılabilen farklı plan Project Online bilgiler|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Project Server'ın daha yeni bir şirket içi sürümüne geçiş

En iyi değeri ve kullanıcı deneyimini elde etmek için Aşağıdakiler'e Project Online. Ancak bazı kuruluşların proje verilerini şirket içinde tutmaları gerektir olduğunu da anlıyoruz. Proje verilerinizi şirket içinde tutmayı seçerseniz, Project Server 2010 ortamınızı Project Server 2013, Project Server 2016 veya Project Server 2019'a geçirebilirsiniz.

Project Online Server 2019'a Project öneririz. Project Server 2019, Project Server'ın önceki sürümlerde yer alan önemli özelliklerin çoğunu içerir. Özelliklerden bazıları yalnızca Project Online'de mevcut olsa da, Project Online en yakın deneyimi Project Online.

Her geçişi tamamlandıktan sonra, verilerinizin başarıyla geçirildikten emin olun.

> [!NOTE]
> Şirket içi bir çözümle sınırlıysanız ve yalnızca Project Server 2013'e kullanmayı düşünüyorsanız, bu sürümün yalnızca birkaç yıllık desteğinin kaldığnı unutmayın. Project Server 2013 Service Pack 2 13 Ekim 2023 için destek tarihi. Destek sonu tarihleri hakkında daha fazla bilgi için bkz. Microsoft Ürün [Yaşam Döngüsü İlkesi](/lifecycle/).

### <a name="how-do-i-migrate-to-project-server-2019"></a>Project Server 2019'a nasıl geçiş yapabilirim?

Project Server 2010 ile Project Server 2019 arasındaki mimari farklılıkları doğrudan geçiş yolunu engeller. Dolayısıyla, Project Project Server 2019'a ulaşana kadar, Project Server 2010 verilerinizi Project Server'ın her Project geçirebilirsiniz. Project Server 2010'dan Project Server 2019'a yükseltme adımları:

1. Project Server 2013'e geçiş.

2. Project Serve 2013'ü başka bir Project Server 2016.

3. Project Server 2016 Server 2019'Project geçirme.

Her geçişi tamamlandıktan sonra, verilerinizin başarıyla geçirildikten emin olun.

### <a name="step-1-migrate-to-project-server-2013"></a>1. Adım: Project Server 2013'e geçirme

Project Server 2010'dan Project Server 2013'e yükseltme hakkında kapsamlı bilgi için bkz. [Project Server 2013'e](/project/upgrade-to-project-server-2016) yükseltme.

Önemli kaynaklar:

- [Project Server 2013 yükseltme sürecine genel bakış](/project/upgrade-to-project-server-2016)

  Project Server 2010'dan Project Server 2013'e yükseltme hakkında üst düzey bir genel bakış elde olun.
- [Project Server 2013'e yükseltmeyi planlama](/project/plan-for-upgrade-to-project-server-2016)

  Project Server 2010'dan Project Server 2013'e yükseltirken, sistem gereksinimleri de içinde olmak üzere planlamada dikkate alınacak noktalara bakın.

- [Project Server 2013 yükseltmesi'ne gelen değişiklikler](/project/what-s-new-in-project-server-2013-upgrade), bu sürümle ilgili önemli değişiklikleri kapsar. Örneğin:

  - Project Server 2013'e yerinde yükseltme yoktur. Project Server 2010'dan Project Server 2013'e yükseltmek için desteklenen tek yöntem veritabanı ekleme yöntemidir.

  - Yükseltme işlemi, Project Server 2010 verilerinizi Project Server 2013 biçimine dönüştürmekle birlikte dört Project Server 2010 veritabanını da tek bir Project Web App veritabanında birleştirecek.

  - Hem SharePoint Server 2013 hem de Project Server 2013'te, önceki sürümden gelen talep tabanlı kimlik doğrulamasıyla değiştirildi. Klasik kimlik doğrulamasını kullanıyorsanız, yükseltme sırasında bunu göz önünde bulundurabilirsiniz. Daha fazla bilgi için bkz[. SharePoint 2013'te](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013) klasik moddan talep tabanlı kimlik doğrulamaya geçirme.

Önemli kaynaklar:

- [Project Server 2013'e yükseltme sürecine genel bakış](/project/overview-of-the-project-server-2016-upgrade-process)

- [Veritabanlarınızı ve Web App site Project yükseltme (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Microsoft Project Server yükseltme işlemi diyagramı](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [8 Kolay Adımda Sunucu 2010'Project 2013 Geçişi için Mükemmel Veritabanı Birleştirmesi](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>2. Adım: Geçiş Project Server 2016

Project Server 2013'e geçiş yaptıktan ve verilerinizin başarıyla geçirildikten sonra, bir sonraki adım Project Server 2016.

Daha fazla bilgi için bkz[. Project Server 2016](/Project/upgrade-to-project-server-2016).

Önemli kaynaklar:

- [Hızlı yükseltme Project Server 2016 genel bakış](/Project/overview-of-the-project-server-2016-upgrade-process)

  Project Server 2013'ü yükseltmeniz için neleri Project Server 2016.

- [Yükseltme işlemini Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  Project Server 2013'Project yükseltme işlemi planlamada dikkate alınacak Project Server 2016.

[Bu sürüme yükseltmeyle ilgili Project Server 2016 şeyler bu](/project/plan-for-upgrade-to-project-server-2016#thingknow) sürüme yükseltmeyle ilgili önemli değişiklikleri kapsar. Bu değişiklikler şunlardır:

- Project Server 2016 ortamınızı 2016'da Project Server 2016 dosyalarınızın SharePoint olduğunu unutmayın. Daha fazla bilgi için bkz[. Dağıtım Project Server 2016](/project/deploy-project-server-2016).

- Kaynak planları proje Project Server 2016. Project Server 2013 kaynak planlarınız, Project Server 2016'de ve kaynak planlarında Kaynak Görev Project Online. Daha [fazla bilgi için bkz. Genel bakış: Kaynak](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) görev atamaları.

### <a name="step-3-migrate-to-project-server-2019"></a>3. Adım: Project Server 2019'a geçirme

Project Server 2016'a Project Server 2016 verilerinizin başarıyla geçirilir olduğunu doğrulayan bir sonraki adım, verilerinizi Project Server 2019'a geçirmektir.

Project Server 2016 Server 2019'dan Project için ne yapmak zorunda olduğunu öğrenmek için bkz. [Project Server 2019'a yükseltme](/Project/upgrade-to-project-server-2016).

Önemli kaynaklar:

- [Project Server 2019 yükseltme sürecine genel bakış](/project/overview-of-the-project-server-2019-upgrade-process)

  Project Server 2013'den yükseltme yapmak için ne yapmak Project Server 2016.

- [Project Server 2019'a yükseltmeyi planlama](/project/plan-for-upgrade-to-project-server-2019)

  Project Server 2016 Server 2019'a Project planlamada dikkate alınacak noktalara bakın.

- [Sunucu 2019 yükseltmesi hakkında Project şeyler](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>Bu sürüme yükseltmeyle ilgili önemli değişiklikler hakkında bilgi edin:

  - Yükseltme işlemi, verilerinizi Project Server 2016 Veritabanı veritabanınıza ve İçerik SharePoint Server 2019 geçirir.  Project Server 2019, Project Server sunucu SharePoint veritabanı oluşturmaz.

  - Yükseltmeden sonra, Web App'te yapılan çeşitli Project dikkat edin.  Ayrıntılar için bkz[. Project Server 2019'daki gibi](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**Diğer kaynaklar**:

- [Project Online Açıklamaları:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) Özellikler ve Hizmetler'de yer alan portföy yönetimi Project Server 2016 Project Online Ekstra.

- [Microsoft Office Project Portfolio Server 2010 geçiş kılavuzu](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 istemci ve sunucuları ile 7. Windows özeti

Office 2010 istemcileri ve sunucuları ve Windows 7 için yükseltme, geçirme ve buluta taşıma seçeneklerinin görsel bir özeti için destek [posteri](../downloads/Office2010Windows7EndOfSupport.pdf) sonuna bakın.

[![Office 2010 istemcileri ve sunucuları ve Posta 7 posteri için Windows sonu.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Bu posterde, Office 2010 istemci ve sunucu ürünleri ve Windows 7 için destek sonunu önlemek üzere atılması gereken çeşitli yollar ve tercih edilen yollar ve Microsoft 365 Kurumsal vurgulanır.

Ayrıca bu [posteri](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) indirip letter, legal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

## <a name="related-topics"></a>İlgili konular

[SharePoint 2010'dan yükseltme](upgrade-from-sharepoint-2010.md)

[Office 2010 sunucularından ve istemcilerinden yükseltme](upgrade-from-office-2010-servers-and-products.md)
