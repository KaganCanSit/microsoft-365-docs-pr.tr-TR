---
title: SharePoint Online'da performans ayarlamaya giriş
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, SharePoint Online'da en iyi performans için sayfalar tasarlarken hangi özellikleri dikkate SharePoint açıklanmıştır.
ms.openlocfilehash: deabb059e2121743b35d5519e4b8684a08dd28b4
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015202"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online'da performans ayarlamaya giriş

Bu makalede, SharePoint Online'da en iyi performans için sayfalar tasarlarken hangi özellikleri dikkate SharePoint açıklanmıştır.
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online ölçümleri

SharePoint Online için aşağıdaki geniş ölçümler, performansla ilgili gerçek zamanlı veriler sağlar:
  
- Sayfalar ne kadar hızlı yük biner?
    
- Sayfa başına kaç gidiş dönüş gereklidir
    
- Hizmetle ilgili sorunlar
    
- Performans düşüşüne neden olan diğer şeyler
    
### <a name="conclusions-reached-because-of-the-data"></a>Veriler nedeniyle sonuca ulaşıldı

Veriler bize şunları söyler:
  
- Sayfaların çoğu SharePoint Online'da iyi performans sağlar.
    
- Özelleştirilmeyen sayfalar hızla yük içerir.
    
- OneDrive İş, ekip siteleri ve site _layouts gibi sistem sayfalarının hepsi hızla gelir.
    
- SharePoint Online sayfalarının en yavaş %1'i, 5.000 milisaniyeden fazla yük alır.
    
Kullanabileceğiniz bir basit karşılaştırma testi, birkaç özelleştirilmiş özellik kullandığından kendi portalınıza ait yükleme süresiyle OneDrive İş karşılaştırarak performansı ölçmek olabilir. Bu genellikle Destek'in ağ performansı sorunlarını giderirken tamamlamanız için sizden ilk adım olacaktır.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Performansı kontrol etmek için standart bir kullanıcı hesabı kullanma

Site Koleksiyonu Yöneticisi, Site Sahibi, Düzenleyici veya Katkıda Bulunan başka güvenlik gruplarında yer alan, daha fazla izine sahip ve dolayısıyla SharePoint fazla öğe içerir.
  
Bu durum şirket içi SharePoint SharePoint Online için geçerlidir, ancak şirket içi bir senaryoda farklılıklar SharePoint Online'daki gibi kolayca fark SharePoint.
  
Bir sayfanın kullanıcılar için nasıl bir performans sergilenesini doğru bir şekilde değerlendirmek için, standart bir kullanıcı hesabı kullanarak yazma denetimlerinin ve güvenlik gruplarıyla ilgili fazladan trafiğin yüklenmesini önlemeniz gerekir.
  
## <a name="connection-categories-for-performance-tuning"></a>Performans ayarı için bağlantı kategorileri

Sunucuyla kullanıcı arasındaki bağlantıları üç ana bileşene ayırabilirsiniz. Yükleme sürelerine dair içgörü SharePoint için SharePoint Online sayfalarını tasarlarken bunları göz önünde bulundurabilirsiniz.
  
- **Sunucu** Microsoft'un veri merkezlerinde barındırıyor olduğu sunucular.
    
- **Ağ** Veri merkeziyle kullanıcılarınız arasında Microsoft ağı, İnternet ve şirket içi ağınız vardır.
    
- **Tarayıcı** Sayfanın yükleniyor olduğu yer.
    
Bu üç bağlantı içinde sayfaların %95'ine neden olan genellikle beş neden vardır. Bu nedenlerin her biri bu makalede ele alınmıştır:
  
- Gezinti sorunları
    
- İçerikleri alma
    
- Büyük dosyalar
    
- Sunucuya çok sayıda istek
    
- Web Bölümü işleme
    
### <a name="server-connection"></a>Sunucu bağlantısı

Şirket içi posta hizmet SharePoint etkileyen sorunların çoğu SharePoint Online'da da geçerlidir.
  
Beklediğiniz gibi, sunucuların şirket içi verilerde nasıl performans üzerinde çok daha fazla SharePoint. SharePoint Online ile bazı şeyler biraz farklıdır. Sunucuya ne kadar çok iş gönderirsiniz, sayfayı işlemek o kadar uzun sürer. Bu SharePoint en büyük culprits, birçok web bölümü içeren karmaşık sayfalardır.
  
SharePoint Server şirket içi
  
![Şirket içi sunucunun ekran görüntüsü.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Çevrimiçi sunucunun ekran görüntüsü.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
SharePoint Online'la, bazı sayfa istekleri aslında birden çok sunucuya çağrılıyor olabilir. Ayrı bir istek için sunucular arasında bir istek matrisini hazır bulundurabilirsiniz. Bu etkileşimler sayfa yükleme perspektifi açısından oldukça pahalıdır ve işleri yavaşlatacak.
  
Bu sunucudan sunucuya etkileşimlere örnek olarak:
  
- Web'den SQL Sunucularına
    
- Web'den uygulama sunucularına
    
Sunucu etkileşimlerini yavaşlatan bir diğer şey de önbellekle ilgili misses'tir. Şirket içi SharePoint farklı olarak, daha önce ziyaret ettiysiniz bir sayfa için aynı sunucuya isabet etme ihtimali çok düşük olabilir; bu da nesneyi önbelleğe almayı gereksiz hale getirdi.
  
### <a name="network-connection"></a>Ağ bağlantısı

WAN kullanmayan SharePoint şirket içi ağlarda, veri merkezi ile son kullanıcılar arasında yüksek hızda bağlantı kullanabilirsiniz. Genel olarak, ağ açısından işler kolayca yönetilebilir.
  
SharePoint Online ile, göz önünde bulundur birkaç etmen daha vardır; örneğin:
  
- Microsoft ağı
    
- İnternet
    
- ISS
    
Ağ bağlantılarının hangi SharePoint (ve hangi ağı) kullanıyor olursanız olun, normalde ağın meşgul olmasına neden olacak şeyler şunlardır:
  
- Büyük yük
    
- Birçok dosya
    
- Sunucuya büyük fiziksel mesafe
    
SharePoint Online'da kullanabileceğiniz bir özellik de Microsoft CDN dir (Content Delivery Network). Temel CDN, temel olarak birden çok veri merkezinde dağıtılmış dağıtılmış sunucu koleksiyonudur. Sayfa CDN, istemci sunucudan çok uzakta olsa bile sayfa içeriğinin istemciye yakın bir sunucuda SharePoint. Microsoft, özelleştirilen yerel sayfa örneklerini, örneğin çevrimiçi çevrimiçi yönetici giriş sayfasını depolamak için gelecekte SharePoint kullanacağız. CDN'ler hakkında daha fazla bilgi için bkz. [İçerik teslim ağları](content-delivery-networks.md).
  
Farkında olmak için ihtiyacınız olan ancak çok fazla şey yapamayabilecek bir şey isS'nizin bağlantı hızıdır. Basit bir hız test aracı size bağlantı hızını gösterir.
  
### <a name="browser-connection"></a>Tarayıcı bağlantısı

Web tarayıcıları açısından performans açısından göz önünde bulundurabilirsiniz.
  
Karmaşık sayfaları ziyaret etmek performansı etkileyebilir. Çoğu tarayıcıda yalnızca küçük bir önbellek vardır (yaklaşık 90 MB) ve ortalama web sayfası genellikle 1,6 MB civarındadır. Bu sürenin kullandık olması çok uzun zaman almzz.
  
Bant genişliği de sorun olabilir. Örneğin, bir kullanıcı başka bir oturumda video izliyorsa, bu sizin SharePoint etkiler. Kullanıcıların medya akışına engel olamasa da, sayfanın kullanıcılara nasıl yük akışını kontrol edebilirsiniz.
  
En iyi performansı elde etmek için SharePoint Çevrimiçi sayfa özelleştirme teknikleri ve diğer en iyi yöntemler için aşağıdaki makalelere göz atın.
  
- [SharePoint Online için gezinti seçenekleri](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online için Sayfa Tanılama aracını kullanma](page-diagnostics-for-spo.md)
    
- [SharePoint Online için görüntü iyileştirme](image-optimization-for-sharepoint-online.md)
    
- [SharePoint Online'da resimleri ve JavaScript'i SharePoint geciktirme](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online'da SharePoint ve büyütme](minification-and-bundling-in-sharepoint-online.md)
    
- [CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)
    
- [SharePoint Online'da performansı iyileştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'SharePoint kullanma](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [SharePoint Online’da kapasite planlaması ve yük testi](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [SharePoint Online ile ilgili performans SharePoint tanılama](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [SharePoint Online ile nesne SharePoint kullanma](using-the-object-cache-with-sharepoint-online.md)
    
- [Nasıl yapılan: SharePoint Online'da kısıtlanıyor veya engellenmiş SharePoint önleme](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
