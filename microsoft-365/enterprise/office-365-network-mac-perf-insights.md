---
title: Microsoft 365 Ağ Analizler
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Ağ Analizler
ms.openlocfilehash: 429b066a7132cb29f2a35d43857534695391d33c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015169"
---
# <a name="microsoft-365-network-insights"></a>Microsoft 365 Ağ Analizler

**Ağ içgörüleri**, kiracınız Microsoft 365 toplanan performans ölçümleridir ve kiracınız içinde yalnızca yönetici kullanıcılar tarafından görüntülemeye kullanılabilir. Analizler merkezi'nde Microsoft 365 Yönetici görüntülenir<https://portal.microsoft.com/adminportal/home#/networkperformance>.

Analizler konumlarınız için ağ çevreleri tasarlamaya yardımcı olmak üzere tasarlanmıştır. Her içgörü, kullanıcıların kiracınıza eriştiği her coğrafi konumda belirli bir genel soruna ilişkin performans özellikleri hakkında canlı ayrıntılar sağlar.

Her ofis konumu için altı belirli ağ içgörüleri gösterebilirsiniz:

- [Geri dönülen ağ çıkış](#backhauled-network-egress)
- [Ağ aracı cihazı](#network-intermediary-device)
- [Yakın gelecekte bulunan müşteriler için daha iyi performans algılandı](#better-performance-detected-for-customers-near-you)
- [En iyi olmayan ön Exchange Online kapı kullanımı](#use-of-a-non-optimal-exchange-online-service-front-door)
- [En iyi olmayan çevrimiçi hizmet SharePoint ön kapı kullanımı](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Ön kapılardan düşük SharePoint indirme hızı](#low-download-speed-from-sharepoint-front-door)
- [Çin kullanıcısı en iyi ağ çıkış](#china-user-optimal-network-egress)

Kiracı için iki kiracı düzeyinde ağ içgörüleri gösterebilirsiniz:

- [Exchange sorunlardan etkilenen örnek bağlantıları oluşturma](#exchange-sampled-connections-affected-by-connectivity-issues)
- [SharePoint sorunlardan etkilenen örnek bağlantıları oluşturma](#sharepoint-sampled-connections-affected-by-connectivity-issues)

Bu içgörüler, üretkenlik puanı sayfalarında da görünür.

>[!IMPORTANT]
>Microsoft 365 Yönetici Merkezi'nde ağ içgörüleri, performans önerileri ve değerlendirmeleri şu anda önizleme durumundadır ve yalnızca özellik önizleme programına Microsoft 365 kiracılar tarafından kullanılabilir.

## <a name="backhauled-network-egress"></a>Geri dönülen ağ çıkış

Ağ içgörüleri hizmeti, bir kullanıcı konumuyla ağ çıkış arasındaki uzaklığın 500 km'den (800 kilometre) fazla olduğunu algılarsa bu içgörü görüntülenir. Bu, trafiğin Microsoft 365 İnternet uç cihazına veya ara sunucuya geri sağlandı olarak işaret edebilirsiniz.

Bu içgörü, bazı özet görünümlerde Egress" olarak kısaltıldı.

> [!div class="mx-imgBorder"]
> ![Geri çıkışlı ağ çıkış.](../media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Bu, ofis konumuyla ağ çıkış arasındaki uzaklığın 500 km'den fazla (800 kilometre) olduğunu tanımlar. Ofis konumu, kimliği belirsiz bir istemci makinesi konumu tarafından tanımlanır ve ağ çıkış konumu ise ters IP Adresi ile konum veritabanları kullanılarak tanımlanır. Makinelerde Konum Hizmetleri devre dışı Windows ofis konumu yanlış olabilir. Ters IP adresi veritabanı bilgileri yanlışsa ağ çıkış konumu yanlış olabilir.

Bu içgörüyle ilgili ayrıntılar şunlardır:

- Office konumu
- Konumdaki toplam kiracı kullanıcısı tahmini yüzdesi
- Geçerli ağ çıkış konumu
- Çıkış konumunun ilgi düzeyi
- Konumla geçerli çıkış noktası arasındaki uzaklık
- Koşulun ilk algılandığında tarih
- Koşulun çözüme kavuşturulma tarihi

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Ofis konumu için mümkün olduğunca yakın bir şekilde ağ çıkış önerilir.  Microsoft 365, trafiğin Microsoft'un genel ağına en uygun şekilde ve en yakın Microsoft 365 ön kapıya yönlendirmesi gerekir. Microsoft, iletişim durumu hem de ön kapı gibi konumların kullanıcılara yakın olması, daha iyi performans için hem iletişim durumu noktalarını hem de Microsoft 365 ön kapılarını genişleten kullanıcılara daha iyi performans sağlar.

Bu sorunun çözümü hakkında daha fazla bilgi için bkz. ağ [Egress](microsoft-365-network-connectivity-principles.md#egress-network-connections-locally) Ağ Bağlantısı [İlkeleri'Microsoft 365 yerel olarak güncelleştirme](microsoft-365-network-connectivity-principles.md).

## <a name="network-intermediary-device"></a>Ağ aracı cihazı

Kullanıcılarınız ve Microsoft ağı arasında cihazlar algılamızsa bu içgörü görüntülenir. Ağ trafiğinin bu tür cihazları at Microsoft 365 gecikmeye duyarlı olmasını öneririz. Bu öneri, Ağ Bağlantısı [Microsoft 365 de açıklanmıştır](microsoft-365-network-connectivity-principles.md).

Sunduğumuz tek ağ aracı içgörü, Exchange, SharePoint ve Teams için kritik Microsoft 365 ağ uç noktalarının ağ aracı cihazları tarafından kesişme ve şifresinin çözülmesi sırasında SSL sonu ve incelemesidir.

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Ara sunucular, VPN'ler ve veri kaybı önleme cihazları gibi ağ ara cihazları, trafiğin ara olduğu istemcilerde Microsoft 365 ve kararlılığını etkileyebilir.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Ağ trafiği için işlemeyi atla olarak algılanan ağ Microsoft 365 yapılandırabilirsiniz.

## <a name="better-performance-detected-for-customers-near-you"></a>Yakın gelecekte bulunan müşteriler için daha iyi performans algılandı

Ağ içgörüleri hizmeti metro alanınıza gelen önemli sayıda müşterinizin bu ofisteki kullanıcılara göre daha iyi performansa sahip olduğunu algılarsa bu içgörü görüntülenir.

Bu içgörü bazı özet görünümlerde "Eşler" olarak kısaltıldı.

> [!div class="mx-imgBorder"]
> ![Göreli ağ performansı.](../media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Bu içgörü, bu ofis konumuyla aynı Microsoft 365 müşterilerin toplam performansını inceler. Kullanıcılarınızı ortalama gecikme süresi komşu kiracıların ortalama gecikme süresinden %10 daha uzunsa bu içgörü görüntülenir.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Şirket ağ veya ISS'nizin gecikme süresi, performans sorunları veya mimari tasarım sorunları da dahil olmak üzere bu koşulun birçok nedeni olabilir. Ofis ağınız ve geçerli ön kapı arasındaki rotada bulunan her atlama arasındaki Microsoft 365 inceler. Daha fazla bilgi için ağ [bağlantısı Microsoft 365 ilkelere bakın](microsoft-365-network-connectivity-principles.md).

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>En iyi olmayan ön Exchange Online kapı kullanımı

Ağ içgörüleri hizmeti belirli bir konumdaki kullanıcıların en iyi içgörüler hizmet ön Exchange Online bağlana olmadığını algılarsa bu içgörü görüntülenir.

Bu içgörü, bazı özet görünümlerde "Yönlendirme" olarak kısaltıldı.

> [!div class="mx-imgBorder"]
> ![En uygun olmayan EXO ön kapı.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Ofis Exchange Online tarafından kullanmaya uygun ön kapı listesini listelemektedir. Geçerli testte bu listede yer Exchange Online bir hizmet ön Exchange Online olduğu gösteriyorsa bu öneriyi öne çıkaracağız.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

En iyi durumda olmayan bir Exchange Online ön kapı kullanılması ağ arka örneğinden kaynaklansa da yerel ve doğrudan ağ çıkışları önerilir. Uzak bir DNS Tekrarlı Çözümleyici sunucusu uygulamanız gerekirse, sunucu yapılandırmasını ağ çıkışla hizalamanız önerilir.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>En iyi olmayan çevrimiçi hizmet SharePoint ön kapı kullanımı

Ağ içgörüleri hizmeti belirli bir konumdaki kullanıcıların Çevrimiçi hizmet ön kapılarından en yakın SharePoint bağlana olmadığını algılarsa bu içgörü görüntülenir.

Bu içgörü, bazı özet görünümlerde "Afd" olarak kısaltıldı.

> [!div class="mx-imgBorder"]
> ![En uygun olmayan SPO ön kapı.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Test istemcisinin SharePoint bağlanıyor olduğu SharePoint Online hizmet ön kapımız tanınıyor. Ardından, ofis konumu şehri olarak bu şehir için beklenen SharePoint Çevrimiçi hizmet ön kapı ile karşılaştıracağız. Eş eş eşleşmezse bu öneriyi biz karşılarız.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

En iyi durumda olmayan bir SharePoint Online hizmet ön kapı kullanımı şirket ağı çıkış öncesinde ağ geri dönmeden kaynaklandır olabilir; bu durumda yerel ve doğrudan ağ çıkışlarını öneririz. Bu soruna uzak DNS Yineleyici Çözümleyici sunucusunun kullanılması da neden olabilir ve bu durumda DNS Yineleyici Çözümleyici sunucusunu ağ çıkışla hizalamayı öneririz.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Ön kapılardan düşük SharePoint indirme hızı

Ağ içgörüleri hizmeti belirli ofis konumuyla SharePoint Online arasındaki bant genişliğinin 1 MBps'den az olduğunu algılarsa bu içgörü görüntülenir.

Bu içgörü, bazı özet görünümlerde "Performans" olarak kısaltıldı.

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Kullanıcının SharePoint Online'dan ve hizmet ön kapılardan OneDrive İş indirme hızı, saniye başına megabayt (MBp) cinsinden ölçülür. Bu değer 1 MBps'den küçükse, bu içgörü sağlariz.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

İndirme hızlarını geliştirmek için bant genişliğinin artması gerekiyor olabilir. Alternatif olarak, ofis konumdaki bilgisayarlar ve SharePoint Online hizmet ön SharePoint tıkanıklığı olabilir. Bu koşul, yeterli bant genişliği mevcut olsa bile kullanıcıların indirme hızını kısıtlar.

## <a name="china-user-optimal-network-egress"></a>Çin kullanıcısı en iyi ağ çıkış

Bu içgörü, kuruluşta Çin'de başka coğrafi konumlarda yer alan kullanıcı Microsoft 365 bağlanıyorsa görüntülenir.

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Kuruluşta özel WAN bağlantısı varsa, Çin'deki ofis konumlarından aşağıdaki konumlardan herhangi birini kullanarak İnternet'e çıkışı olan bir ağ WAN devresi yapılandırmanızı öneririz:

- Hong Kong
- Japonya
- Tayvan
- Güney Kore
- Singapur
- Malezya

İnternet çıkışlarının kullanıcılardan bu konumlardan daha fazla uzak olması performansı düşürecek ve Çin'de çıkış, sınır çapraz tıkanıklığı nedeniyle yüksek gecikme süresi ve bağlantı sorunlarına neden olabilir.

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Bu içgörüyle ilgili performans sorunlarını nasıl azaltmak için bkz. [Çin Microsoft 365 genel kiracı performans iyileştirme hakkında bilgi.](microsoft-365-networking-china.md)

## <a name="exchange-sampled-connections-affected-by-connectivity-issues"></a>Exchange sorunlardan etkilenen örnek bağlantıları oluşturma

Bu içgörü, örnek bağlantıların %50'sinde veya daha fazlası etkilendiği zaman ortaya çıktı. Etki, değerlendirmenin her Exchange %60'ın altında olmasıyla tanımlanır.

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Bu, kullanıcı çoğu kullanıcınizin büyük olasılıkla Posta'ya bağlanırken Outlook sorunlar yaşadığını Exchange Online. Örneklerin yüzdesi, 60 nokta altında gösteren kullanıcıların yüzdesini temsil eder.  

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Daha önce etkinleştirmedıysanız, ofis konumu ağ bağlantısı görünürlüğünü etkinleştirin. Zayıf ağ bağlantısı nedeniyle hangi ofislerin etkilendiğini bulun ve her biri için kullanıcıları Microsoft'un ağına bağlayan ağ çevresini geliştirmenin yollarını bulun.

## <a name="sharepoint-sampled-connections-affected-by-connectivity-issues"></a>SharePoint sorunlardan etkilenen örnek bağlantıları oluşturma

Bu içgörü, örnek bağlantıların %50'sinde veya daha fazlası etkilendiği zaman ortaya çıktı. Etki, değerlendirmenin her SharePoint %40'ın altında olmasıyla tanımlanır.

### <a name="what-does-this-mean"></a>Bu ne anlama geliyor?

Bu, kullanıcı çoğu kullanıcınizin büyük olasılıkla veri ve kaynak sorunları SharePoint olduğunu OneDrive. Örneklerin yüzdesi, 40 nokta altında gösteren kullanıcıların yüzdesini temsil eder.  

### <a name="what-should-i-do"></a>Ne yapmalıyım?

Daha önce etkinleştirmedıysanız, ofis konumu ağ bağlantısı görünürlüğünü etkinleştirin. Zayıf ağ bağlantısı nedeniyle hangi ofislerin etkilendiğini bulun ve her biri için kullanıcıları Microsoft'un ağına bağlayan ağ çevresini geliştirmenin yollarını bulun.

## <a name="related-topics"></a>İlgili konular

[Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı](office-365-network-mac-perf-overview.md)

[Microsoft 365 değerlendirmesini geri ayanız](office-365-network-mac-perf-score.md)

[Microsoft 365 bağlantı test aracı](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a](office-365-network-mac-location-services.md)
