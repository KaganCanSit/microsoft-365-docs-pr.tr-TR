---
title: Project Server 2013 destek sonu yol haritası
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: 11 Nisan 2023 Project Server 2013 için destek sona erer. Bu makaleyi, Project Online Server şirket içi sürümünü veya daha yeni bir Project kılavuz olarak kullanın.
ms.openlocfilehash: 5a9ae38e819dfdb8f9cc2ca3719dccea2d33fa3e
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2021
ms.locfileid: "62990617"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Project Server 2013 destek sonu yol haritası

Project Server 2013 için destek **11 Nisan 2023'te sona erecek**. Şu anda Project Server 2013 kullanıyorsanız, Project 2013 masaüstü uygulamasının da aynı destek sonu tarihlerini olduğunu unutmayın.

## <a name="what-does-end-of-support-mean"></a>Desteğin *sonu ne anlama* geliyor?

Neredeyse bütün Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik güncelleştirmeleri elde eder. Bu yaşam döngüsü normalde ürünün ilk sürümüne göre 10 yıl devam eder. Bu yaşam döngüsünün sonu ürünün destek sonu olarak bilinir. 11 Project 2023'te Project Server 2013 destek sonuna ulaştıktan sonra, Microsoft artık şunları sağlamaz:

- Ortaya çıkabilir sorunlar için teknik destek.

- Bulunan ve sunucunun kararlılığıyla kullanılabilirliğini etkilebilir olan sorunlar için hata düzeltmeleri.

- Bulunan ve sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Project Server 2013 yüklemeniz bu tarihten sonra da çalışmaya devam edecektir. Ancak, daha önce listelenen değişikliklerden dolayı en kısa zamanda Project Server 2013'den geçişnizi kesinlikle öneririz.

## <a name="what-are-my-options"></a>Seçeneklerim neler?

Geçiş seçenekleriniz şunlardır:

- Geçiş Project Online

- Project Server'ın daha yeni bir şirket içi sürümüne (tercihen Project Server Subscription Edition) geçirme

|Project Server 2019'a geçişi neden tercih  ederim?|Neden geçiş tercih Project Online?|
|---|---|
|İş kuralları işletmemi bulutta çalıştırmamı kısıtlar.  <br/><br/>  Ortamımda yapılan güncelleştirmeleri denetlemem gerekiyor.|Mobil veya uzak kullanıcılarım var.<br/><br/>  Şirket içi sunucuları geçirmenin maliyetleri önemli bir sorun (donanım, yazılım, uygulama için gereken zaman ve çaba, vb.). <br/><br/>  Geçiş sonrasında, ortamımı koruma maliyetleri önemli bir sorun (örneğin, otomatik güncelleştirmeler, garantili çalışma süresi, vb.).|

> [!NOTE]
> Project Server karma yapılandırmayı desteklemez, çünkü Project Server Project Online aynı kaynak havuzunu paylaşamaz.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>Project Server 2013'Project önemli noktalar

Project Server 2013'Project göz önünde önünde olun:

- **Microsoft çözüm sağlayıcısından yardım al** - Project Server 2013'den yükseltme zor olabilir. Çok fazla hazırlık ve planlama gerektirir. İlk olarak Server 2013'ü ilk kez ayarlayanın kişi siz Project zor olabilir. Project Server Subscription Edition'a veya başka bir Project Online, Microsoft çözüm sağlayıcıları yardımcı olabilir. Microsoft çözüm sağlayıcısı merkezinde bir [çözüm sağlayıcısını arama](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Zaman ve sabır** - Yükseltmeyi planlama, yürütme ve test etme, özellikle de Project Server Subscription Edition yükseltmesi için önemli ölçüde zaman ve çaba gerektirir. Project Server 2013'den Project Server Subscription Edition'a geçiş ediyorsanız, önce Project Server 2016'a geçirmeniz, verilerinizi denetlemeniz ve ardından Project Server Subscription Edition'a geçişniz gerekir. Bir zaman dilimi için Microsoft çözüm sağlayıcısına danışın ve onlara yardımcı olacak tahmini maliyet konusunda yardım alabilirsiniz.

## <a name="migrate-to-project-online"></a>Geçiş Project Online

Project Server 2013'Project Online geçirmeyi seçerseniz, proje planı verilerinizi el ile geçirmek için şu adımları izleyin:

1. Project Server 2013'ten .mpp biçimine kadar proje planlarınızı kaydedin.

2. Project Professional 2016, Project Professional 2019 veya Project Online Masaüstü İstemcisi'ne tıklayın, her .mpp dosyasını açın ve ardından dosyayı başka bir Project Online.

Project Online yapılandırmasını el PWA oluşturabilirsiniz (örneğin, gerekli özel alanları veya kuruluş takvimlerini yeniden oluşturun). Microsoft çözüm sağlayıcıları da bu işlemde yardımcı olabilir.

Önemli kaynaklar:

|Kaynak|Açıklama|
|---|---|
|[Project Online ile çalışmaya başlama](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|E-bilgileri ayarlama ve Project Online|
|[Project Online Hizmet Açıklaması](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Kullanılabilen farklı plan Project Online bilgiler|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Project Server'ın daha yeni bir şirket içi sürümüne geçiş

En iyi değeri ve kullanıcı deneyimini elde etmek için Aşağıdakiler'e Project Online. Ancak bazı kuruluşların proje verilerini şirket içinde tutmaları gerektir olduğunu da anlıyoruz. Proje verilerinizi şirket içinde tutmayı seçerseniz, Project Server 2013 ortamınızı Project Server 2016, Project Server 2019 veya Project Server Subscription Edition'a geçirebilirsiniz.

Project Online'e Project Online, Project Server'ın önceki sürümlerindeki temel özelliklerin çoğunu içeren Project Server Subscription Edition'a Project. Özelliklerden bazıları yalnızca Project Online'de mevcut olsa da, Project Online en yakın deneyimi Project Online. Göz önünde önünde olacak ek etmenler:

- Project Server Subscription Edition, ileriye doğru Project Server'ın yeni ana sürümlerini sürüm bırakma ihtiyacını ortadan kaldıran bir sürekli güncelleştirme modeli içerir.
- Hem Project Server 2016 2019 desteği 14 Temmuz 2026'da sona erecek. Herhangi bir sürüme geçiş yaptıysanız, üç yıl içinde başka bir yükseltme planlamanız gerekir. Daha fazla bilgi için hem [2016 hem de 2019](/lifecycle/products/project-server-2016) için destek [yaşam döngüsü sayfalarına bakın](/lifecycle/products/project-server-2019).

Her geçişi tamamlandıktan sonra, verilerinizin başarıyla geçirildikten emin olun.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>Project Server Subscription Edition'a nasıl geçiş yapabilirim?

Project Server 2013 ile Project Server Subscription Edition arasındaki mimari farklılıkları doğrudan geçiş yolunu engeller. Bu nedenle, önce Project Server 2013 verilerinizi Project Server 2016 sonra Project Server Subscription Edition'a geçirmeniz gerekir. 

1. Geçiş Project Server 2016.

2. Project Server 2016 Server Subscription Edition Project a geçin.

Her geçişi tamamlandıktan sonra, verilerinizin başarıyla geçirildikten emin olun.

### <a name="step-1-migrate-to-project-server-2016"></a>1. Adım: Geçişin Project Server 2016

Project Server 2013'Project Server 2016 yükseltme hakkında kapsamlı bilgi için bkz. [Project Server 2016.](/project/upgrade-to-project-server-2016)

Önemli kaynaklar:

- [Hızlı yükseltme Project Server 2016 genel](/project/upgrade-to-project-server-2016) bakış: Project Server 2013'den Project Server 2016'e yükseltme hakkında üst düzey Project Server 2016.
- [Project Server 2016'e yükseltmeyi](/project/plan-for-upgrade-to-project-server-2016) planlama: Project Server 2013'den Project Server 2016 gereksinimleri de içinde olmak üzere, yükseltme sırasında planlamada dikkate alınacak noktalara bakın.
- [Yükseltme Project Server 2016](/project/upgrading-to-project-server-2016): Yükseltme işlemiyle ilgili ayrıntılı yönergelere bakın.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>2. Adım: Project Server Subscription Edition'a geçirme

Project Server 2016'a Project Server 2016 verilerinizin başarıyla geçirilir olduğunu doğruladikten sonra, bir sonraki adım Project Server Subscription Edition'a geçirmektir.

Daha fazla bilgi için bkz[. Project Server Subscription Edition'a yükseltme](/project/upgrade-project-server-subscription-edition).

Önemli kaynaklar:

- [Project Server Subscription Edition](/project/overview-project-server-subscription-edition-upgrade-process) yükseltme sürecine genel bakış: Project Server 2013'ü yükseltme ve yükseltme işlemlerine Project Server 2016.
- [Project Server Subscription Edition'a](/Project/plan-upgrade-project-server-subscription-edition) yükseltmeyi planlama: Project Server 2013'den Project Server 2016'a yükseltme işlemi sırasında planlamada dikkate alınacak Project Server 2016.
- [Project Server Subscription Edition'a yükseltme](/project/how-to-upgrade-project-server-subscription-edition): Yükseltme işlemiyle ilgili ayrıntılı yönergelere bakın.


