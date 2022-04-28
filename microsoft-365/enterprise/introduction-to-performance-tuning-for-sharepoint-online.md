---
title: SharePoint Online için performans ayarlamaya giriş
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Bu makalede, SharePoint Online'da en iyi performans için sayfalar tasarlarken dikkate almanız gereken belirli noktalar açıklanmaktadır.
ms.openlocfilehash: b31696766d3201b6677bf0c63108fad72c3ed49d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100753"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online için performans ayarlamaya giriş

Bu makalede, SharePoint Online'da en iyi performans için sayfalar tasarlarken dikkate almanız gereken belirli noktalar açıklanmaktadır.
     
## <a name="sharepoint-online-metrics"></a>çevrimiçi ölçümleri SharePoint

SharePoint Online için aşağıdaki geniş ölçümler performans hakkında gerçek dünya verileri sağlar:
  
- Sayfaların yükleme hızı
    
- Sayfa başına kaç gidiş dönüş gerekir?
    
- Hizmetle ilgili sorunlar
    
- Performans düşüşlerine neden olan diğer şeyler
    
### <a name="conclusions-reached-because-of-the-data"></a>Veriler nedeniyle sonuçlara ulaşıldı

Veriler bize şu bilgileri verir:
  
- Sayfaların çoğu SharePoint Online'da iyi performans gösterir.
    
- Özelleştirilmemiş sayfalar hızla yüklenir.
    
- OneDrive İş, ekip siteleri ve _layouts gibi sistem sayfalarının tümü hızlı yüklenir.
    
- SharePoint Online sayfalarının en yavaş %1'inin yüklenmesi 5.000 milisaniyeden fazla sürer.
    
Kullanabileceğiniz basit karşılaştırma testlerinden biri, kendi portalınızın yükleme süresini OneDrive İş giriş sayfasının yükleme süresiyle karşılaştırarak performansı ölçmektir. Bu genellikle Destek'in ağ performansı sorunlarını giderirken tamamlamanızı isteyeceği ilk adım olacaktır.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Performansı denetlerken standart kullanıcı hesabı kullanma

Site Koleksiyonu Yöneticisi, Site Sahibi, Düzenleyici veya Katkıda Bulunan başka bir güvenlik grubuna aittir, daha fazla izne sahiptir ve bu nedenle bir sayfaya yük SharePoint ek öğelere sahiptir.
  
Bu, şirket içi ve SharePoint Online SharePoint için geçerlidir, ancak şirket içi bir senaryoda farklar SharePoint Online'daki kadar kolay fark edilmeyecektir.
  
Bir sayfanın kullanıcılar için nasıl performans göstereceğini doğru bir şekilde değerlendirmek için, yazma denetimlerinin ve güvenlik gruplarıyla ilgili ek trafiğin yüklenmesini önlemek için standart bir kullanıcı hesabı kullanmanız gerekir.
  
## <a name="connection-categories-for-performance-tuning"></a>Performans ayarlama için bağlantı kategorileri

Sunucu ile kullanıcı arasındaki bağlantıları üç ana bileşene ayırabilirsiniz. Yükleme sürelerine ilişkin içgörüler için SharePoint Çevrimiçi sayfaları tasarlarken bunları göz önünde bulundurun.
  
- **Sunucu** Microsoft'un veri merkezlerinde barındırdığını sunucular.
    
- **Ağ** Veri merkezi ile kullanıcılarınız arasındaki Microsoft ağı, İnternet ve şirket içi ağınız.
    
- **Tarayıcı** Sayfanın yüklendiği yer.
    
Bu üç bağlantıda genellikle yavaş sayfaların %95'ine neden olan beş neden vardır. Bu nedenlerin her biri bu makalede ele alınılmaktadır:
  
- Gezinti sorunları
    
- İçerik dağıtımı
    
- Büyük dosyalar
    
- Sunucuya yönelik birçok istek
    
- Web Bölümü işleme
    
### <a name="server-connection"></a>Sunucu bağlantısı

Şirket içi SharePoint performansı etkileyen sorunların çoğu SharePoint Online için de geçerlidir.
  
Beklediğiniz gibi, sunucuların şirket içi SharePoint performansı üzerinde çok daha fazla denetime sahip olursunuz. SharePoint Online ile işler biraz farklıdır. Sunucuya ne kadar çok iş yaparsanız, sayfayı işlemek o kadar uzun sürer. SharePoint ile, bu açıdan en büyük suçlular birden çok web bölümü içeren karmaşık sayfalardır.
  
şirket içi SharePoint Sunucusu
  
![Şirket içi sunucunun ekran görüntüsü.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Çevrimiçi sunucunun ekran görüntüsü.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
SharePoint Online ile, bazı sayfa istekleri aslında birden çok sunucuyu çağırabilir. Tek bir istek için sunucular arasında bir istek matrisi bulabilirsiniz. Bu etkileşimler sayfa yükü açısından pahalıdır ve işleri yavaşlatacaktır.
  
Bu sunucudan sunucuya etkileşimlere örnek olarak şunlar verilebilir:
  
- Web'SQL Sunucuları
    
- Web'de uygulama sunucuları
    
Sunucu etkileşimlerini yavaşlatabilecek bir diğer şey de önbellek isabetsizleridir. Şirket içi SharePoint aksine, daha önce ziyaret ettiğiniz bir sayfa için aynı sunucuya ulaşma olasılığınız düşüktür; bu da nesne önbelleğe alma özelliğinin kullanım dışı olmasına neden olur.
  
### <a name="network-connection"></a>Ağ bağlantısı

WAN kullanmayan şirket içi SharePoint, veri merkezi ile son kullanıcılar arasında yüksek hızlı bir bağlantı kullanabilirsiniz. Genel olarak, işleri ağ açısından kolayca yönetebilirsiniz.
  
SharePoint Online ile dikkate alınması gereken birkaç faktör daha vardır; örneğin:
  
- Microsoft ağı
    
- İnternet
    
- ISS
    
Hangi SharePoint sürümünü (ve hangi ağı) kullanıyorsanız kullanın, genellikle ağın meşgul olmasına neden olacak şeyler şunlardır:
  
- Büyük yük
    
- Birçok dosya
    
- Sunucuya büyük fiziksel uzaklık
    
SharePoint Online'da kullanabileceğiniz bir özellik microsoft CDN (Content Delivery Network). CDN temelde birden çok veri merkezine dağıtılan dağıtılmış sunucu koleksiyonudur. bir CDN ile, istemci kaynak SharePoint Sunucusundan uzak olsa bile sayfalardaki içerik istemciye yakın bir sunucuda barındırılabilir. Microsoft, özelleştirilemeyen sayfaların yerel örneklerini (örneğin, SharePoint Çevrimiçi yönetici giriş sayfası) depolamak için gelecekte bunu daha fazla kullanacaktır. CDN'ler hakkında daha fazla bilgi için bkz. [İçerik teslim ağları](content-delivery-networks.md).
  
Bilmeniz gereken ancak çok fazla şey yapamayabileceğiniz bir şey, ISS'nizin bağlantı hızıdır. Basit bir hız testi aracı size bağlantı hızını söyler.
  
### <a name="browser-connection"></a>Tarayıcı bağlantısı

Performans açısından web tarayıcılarında dikkate alınması gereken birkaç faktör vardır.
  
Karmaşık sayfaları ziyaret etmeniz performansı etkiler. Çoğu tarayıcıda yalnızca küçük bir önbellek (yaklaşık 90 MB), ortalama web sayfası ise genellikle 1,6 MB civarındadır. Buna alışmak uzun sürmez.
  
Bant genişliği de sorun olabilir. Örneğin, bir kullanıcı başka bir oturumda video izliyorsa, bu durum SharePoint sayfanızın performansını etkiler. Kullanıcıların akış medyasını engellemesine engel olamasanız da, bir sayfanın kullanıcılar için nasıl yüklenip yükleneceğini denetleyebilirsiniz.
  
En iyi performansı elde etmeye yardımcı olmak için farklı SharePoint Çevrimiçi sayfa özelleştirme teknikleri ve diğer en iyi yöntemler için aşağıdaki makalelere göz atın.
  
- [SharePoint Online için gezinti seçenekleri](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online için Sayfa Tanılama aracını kullanma](page-diagnostics-for-spo.md)
    
- [SharePoint Online için görüntü iyileştirme](image-optimization-for-sharepoint-online.md)
    
- [SharePoint Online'da görüntülerin ve JavaScript'in yüklenmesini geciktirme](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online'da küçültme ve paketleme](minification-and-bundling-in-sharepoint-online.md)
    
- [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md)
    
- [SharePoint Online'da performansı geliştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü kullanma](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [SharePoint Online’da kapasite planlaması ve yük testi](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [SharePoint Online ile ilgili performans sorunlarını tanılama](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [SharePoint Online ile nesne önbelleğini kullanma](using-the-object-cache-with-sharepoint-online.md)
    
- [Nasıl yapılır: SharePoint Online'da kısıtlama veya engellenmekten kaçınma](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
