---
title: Office 365 için ExpressRoute Uygulama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: İnternet'e yönelik birçok Office 365 hizmeti için alternatif yönlendirme yolu sağlayan Office 365 için ExpressRoute'u uygulamayı öğrenin.
ms.openlocfilehash: d577a30d97630b32fa080c9d17620b429562c5df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090373"
---
# <a name="implementing-expressroute-for-office-365"></a>Office 365 için ExpressRoute Uygulama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Office 365 için ExpressRoute, İnternet'e yönelik birçok Office 365 hizmeti için alternatif bir yönlendirme yolu sağlar. Office 365 için ExpressRoute mimarisi, bu IP ön eklerinin ağınıza daha sonra yeniden dağıtılma amacıyla sağlanan ExpressRoute bağlantı hatlarınıza İnternet üzerinden zaten erişilebilen Office 365 hizmetlerinin genel IP ön eklerini tanıtma temel alır. ExpressRoute ile birçok Office 365 hizmeti için İnternet üzerinden ve ExpressRoute aracılığıyla birçok farklı yönlendirme yolunu etkin bir şekilde etkinleştirirsiniz. Ağınızdaki bu yönlendirme durumu, iç ağ topolojinizin tasarımında önemli bir değişikliği temsil edebilir.
  
 **Durum:** Eksiksiz Kılavuz v2
  
ExpressRoute'unuzu Office 365 uygulama için dikkatle planlamanız ve hem çekirdek ağınıza hem de İnternet'e eklenen yolların bulunduğu ayrılmış bir bağlantı hattı aracılığıyla yönlendirmeye sahip olmanın ağ karmaşıklıklarına uyum sağlaması gerekir. Siz ve ekibiniz bu kılavuzda ayrıntılı planlama ve test gerçekleştirmezseniz, ExpressRoute bağlantı hattı etkinleştirildiğinde aralıklı olarak veya Office 365 hizmetlerine yönelik toplam bağlantı kaybıyla karşılaşma riskiniz yüksektir.
  
Başarılı bir uygulama elde etmek için altyapı gereksinimlerinizi analiz etmeniz, ayrıntılı ağ değerlendirmesi ve tasarımından geçmeniz, dağıtımı aşamalı ve kontrollü bir şekilde dikkatle planlamanız ve ayrıntılı bir doğrulama ve test planı oluşturmanız gerekir. Büyük ve dağıtılmış bir ortamda, uygulamaların birkaç aya yayıldığını görmek yaygın bir durum değildir. Bu kılavuz, önceden planlamanıza yardımcı olmak için tasarlanmıştır.
  
Büyük başarılı dağıtımların planlanması altı ay sürebilir ve genellikle ağ, Güvenlik Duvarı ve Proxy sunucu yöneticileri, Office 365 yöneticileri, güvenlik, son kullanıcı desteği, proje yönetimi ve yönetici sponsorluğu gibi kuruluştaki birçok alandan ekip üyelerini içerebilir. Planlama sürecine yaptığınız yatırım, dağıtım hatalarıyla karşılaşma olasılığını azaltır ve bu da kesinti süresine veya karmaşık ve pahalı sorun giderme işlemlerine neden olur.
  
Bu uygulama kılavuzu başlatılmadan önce aşağıdaki önkoşulların tamamlanmasını bekliyoruz.
  
1. ExpressRoute'un önerilip önerilmediğini ve onaylanıp onaylanmadığını belirlemek için bir ağ değerlendirmesi tamamladınız.

2. Bir ExpressRoute ağ hizmeti sağlayıcısı seçtiniz. [ExpressRoute iş ortakları ve eşleme konumları](/azure/expressroute/expressroute-locations) hakkındaki ayrıntıları bulun.

3. [ExpressRoute belgelerini](https://azure.microsoft.com/documentation/services/expressroute/) zaten okuyup anlamışsınızdır ve iç ağınız ExpressRoute önkoşullarını uçtan uca karşılayabilir.

4. Ekibiniz , [https://aka.ms/ert](https://aka.ms/ert)konumundaki tüm genel rehberliği ve belgeleri [https://aka.ms/expressrouteoffice365](./azure-expressroute.md)okudu ve aşağıdakiler gibi kritik teknik ayrıntıları anlamak için Channel 9'daki [Office 365 için Azure ExpressRoute Eğitim](https://channel9.msdn.com/series/aer) serisini izledi:

      - SaaS hizmetlerinin internet bağımlılıkları.

      - Asimetrik yollardan kaçınma ve karmaşık yönlendirmeyi işleme.

      - Çevre güvenliği, kullanılabilirlik ve uygulama düzeyi denetimlerini birleştirme.

## <a name="begin-by-gathering-requirements"></a>Gereksinimleri toplayarak başlayın
<a name="requirements"> </a>

Kuruluşunuzda benimsemeyi planladığınız özellikleri ve hizmetleri belirleyerek başlayın. Farklı Office 365 hizmetlerinin hangi özelliklerinin kullanılacağını ve ağınızdaki hangi konumların bu özellikleri kullanan kişileri barındıracağını belirlemeniz gerekir. Senaryo kataloğuyla, bu senaryoların her birinin gerektirdiği ağ özniteliklerini eklemeniz gerekir; örneğin, gelen ve giden ağ trafiği akışları ve Office 365 uç noktalarının ExpressRoute üzerinden kullanılabilir olup olmadığı gibi.
  
Kuruluşunuzun gereksinimlerini toplamak için:
  
- Kuruluşunuzun kullandığı Office 365 hizmetleri için gelen ve giden ağ trafiğini kataloglar. Farklı Office 365 senaryolarının gerektirdiği akışların açıklaması için Office 365 URL'ler ve IP adresi aralıkları sayfasına başvurun.

- İç WAN omurganızın ve topolojinizin ayrıntılarını, uydu sitelerinin bağlantısını, son mil kullanıcı bağlantısını, ağ çevre çıkış noktalarına yönlendirmeyi ve ara sunucu hizmetlerini gösteren mevcut ağ topolojisinin belgelerini toplayın.

  - Office 365 ve diğer Microsoft hizmetleri bağlanacağı ağ diyagramlarında hem İnternet hem de önerilen ExpressRoute bağlantı yollarını gösteren gelen hizmet uç noktalarını belirleyin.

  - Tüm coğrafi kullanıcı konumlarını ve konumlar arasındaki WAN bağlantısının yanı sıra şu anda İnternet'e çıkış yapan konumları ve ExpressRoute eşleme konumuna çıkış yapılmasının önerildiği konumları belirleyin.

  - Proxy'ler, güvenlik duvarları vb. gibi tüm uç cihazları tanımlayın ve İnternet ve ExpressRoute üzerinden giden akışlarla ilişkilerini kataloglar.

  - Son kullanıcıların hem İnternet hem de ExpressRoute akışları için Doğrudan Yönlendirme veya dolaylı uygulama ara sunucusu aracılığıyla Office 365 hizmetlerine erişip erişmeyeceğini belgeleyin.

- Ağ diyagramınıza kiracınızın ve meet-me konumlarınızın konumunu ekleyin.

- Ana kullanıcı konumlarından Office 365 kadar beklenen ve gözlemlenen ağ performansı ve gecikme süresi özelliklerini tahmin edin. Office 365 genel ve dağıtılmış bir hizmet kümesi olduğunu ve kullanıcıların kiracılarının konumundan farklı olabilecek konumlara bağlanacağını unutmayın. Bu nedenle, kullanıcı ile Microsoft küresel ağının en yakın kenarı arasındaki gecikme süresini ExpressRoute ve İnternet bağlantıları üzerinden ölçmek ve iyileştirmek önerilir. Bu göreve yardımcı olmak için ağ değerlendirmesinden elde ettiğiniz bulguları kullanabilirsiniz.

- Yeni ExpressRoute bağlantısıyla karşılanması gereken şirket ağ güvenliği ve yüksek kullanılabilirlik gereksinimlerini listeleyin. Örneğin, İnternet çıkışı veya ExpressRoute bağlantı hattı hatası durumunda kullanıcılar Office 365 erişmeye nasıl devam eder?

- Hangi gelen ve giden Office 365 ağ akışlarının İnternet yolunu ve hangilerinin ExpressRoute kullanacağını belgele. Kullanıcılarınızın coğrafi konumlarının özellikleri ve şirket içi ağ topolojinizin ayrıntıları, planın bir kullanıcı konumundan diğerine farklı olmasını gerektirebilir.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Giden ve gelen ağ trafiğinizi katalogla
<a name="trafficCatalog"> </a>

Yönlendirmeyi ve diğer ağ karmaşıklıklarını en aza indirmek için, yalnızca mevzuat gereksinimleri nedeniyle veya ağ değerlendirmesinin sonucu olarak ayrılmış bir bağlantı üzerinden geçmek için gereken ağ trafiği akışları için Office 365 için ExpressRoute kullanmanızı öneririz. Ayrıca, ExpressRoute yönlendirme ve yaklaşım giden ve gelen ağ trafiği akışlarının kapsamını uygulama projesinin farklı ve ayrı aşamaları olarak hazırlamanızı öneririz. Office 365 için ExpressRoute'u yalnızca kullanıcı tarafından başlatılan giden ağ trafiği akışları için dağıtın ve İnternet genelinde gelen ağ trafiği akışlarını bırakın, topolojik karmaşıklıktaki artışı ve ek asimetrik yönlendirme olasılıkları sunma risklerini denetlemeye yardımcı olabilir.
  
Ağ trafiği kataloğunuz, şirket içi ağınızla Microsoft arasında sahip olduğunuz tüm gelen ve giden ağ bağlantılarının listelerini içermelidir.
  
- Giden ağ trafiği akışları, şirket içi ortamınızdan( örneğin iç istemcilerden veya sunuculardan) Microsoft hizmetleri hedefine sahip bir bağlantının başlatıldığı tüm senaryolardır. Bu bağlantılar, örneğin bağlantının Office 365 yolundaki ara sunuculardan, güvenlik duvarlarından veya diğer ağ cihazlarından geçtiği durumlarda doğrudan Office 365 veya dolaylı olabilir.

- Gelen ağ trafiği akışları, Microsoft bulutundan şirket içi konağa bağlantının başlatıldığı tüm senaryolardır. Bu bağlantıların genellikle dış kaynaklı akışlar için müşteri güvenlik ilkesinin gerektirdiği güvenlik duvarından ve diğer güvenlik altyapısından geçmesi gerekir.

Hangi hizmetlerin gelen trafik göndereceğini belirlemek [için Office 365 için ExpressRoute ile yönlendirme](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) makalesinin **Yol simetrisini sağlama** bölümünü okuyun ve bağlantı bilgilerinin geri kalanını belirlemek için [Office 365 uç noktaları](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) başvuru makalesinde **Office 365 için ExpressRoute** olarak işaretlenmiş sütunu arayın.
  
Giden bağlantı gerektiren her hizmet için ağ yönlendirme, ara sunucu yapılandırması, paket incelemesi ve bant genişliği gereksinimleri gibi hizmet için planlanan bağlantıyı açıklamak istersiniz.
  
Gelen bağlantı gerektiren her hizmet için bazı ek bilgilere ihtiyacınız olacaktır. Microsoft bulutundaki sunucular, şirket içi ağınızla bağlantı kurar. Bağlantıların doğru yapıldığından emin olmak için; bu gelen bağlantıları kabul edecek hizmetlerin genel DNS girişleri, CIDR biçimlendirilmiş IPv4 IP adresleri, hangi ISS ekipmanının dahil olduğu ve bu bağlantılar için gelen NAT veya kaynak NAT'nin nasıl işlendiği.
  
Asimetrik yönlendirmenin kullanılmadığından emin olmak için İnternet üzerinden mi yoksa ExpressRoute üzerinden mi bağlandıklarına bakılmaksızın gelen bağlantılar gözden geçirilmelidir. Bazı durumlarda, Office 365 hizmetlerin gelen bağlantıları başlattığı şirket içi uç noktalarına diğer Microsoft ve Microsoft hizmetleri tarafından da erişilmesi gerekebilir. Office 365 amaçlarla bu hizmetlere ExpressRoute yönlendirmesini etkinleştirmenin diğer senaryoları bozmaması çok önemlidir. Çoğu durumda müşterilerin, ExpressRoute etkinleştirildikten sonra Microsoft'tan gelen akışların simetrik kalmasını sağlamak için kaynak tabanlı NAT gibi iç ağlarında belirli değişiklikler yapmaları gerekebilir.
  
Aşağıda gerekli ayrıntı düzeyinin bir örneği verilmişti. Bu durumda Exchange Karma, ExpressRoute üzerinden şirket içi sisteme yönlendirilir. 

|Bağlantı özelliği   |Değer  |
|----------|-----------|
|**Ağ trafiği yönü** <br/> |Gelen  <br/> |
|**Hizmet** <br/> |Exchange Karma  <br/> |
|**Genel Office 365 uç noktası (kaynak)** <br/> |Exchange Online (IP adresleri)  <br/> |
|**Genel Şirket İçi Uç Nokta (hedef)** <br/> |5.5.5.5  <br/> |
|**Genel (İnternet) DNS girişi** <br/> |Autodiscover.contoso.com  <br/> |
|**Bu şirket içi uç nokta diğer (Office 365 olmayan) Microsoft hizmetleri** <br/> |Hayır  <br/> |
|**Bu şirket içi uç nokta İnternet'te kullanıcılar/sistemler tarafından kullanılacak mı?** <br/> |Evet  <br/> |
|**Genel uç noktalar aracılığıyla yayımlanan iç sistemler** <br/> |Exchange Server istemci erişim rolü (şirket içi) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Genel uç noktanın IP tanıtımı** <br/> |**İnternet'e**: 5.5.0.0/ **16-ExpressRoute**: 5.5.5.0/24  <br/> |
|**Güvenlik/Çevre Denetimleri** <br/> |**İnternet yolu**:  **ExpressRoute yolunu** DeviceID_002: DeviceID_003  <br/> |
|**Yüksek Kullanılabilirlik** <br/> |2 coğrafi olarak yedekli / ExpressRoute bağlantı hattında Etkin/Etkin - Chicago ve Dallas  <br/> |
|**Yol simetri denetimi** <br/> |**Yöntem**: Kaynak NAT **İnternet yolu**: 192.168.5.5 **ExpressRoute yoluna** kaynak NAT gelen bağlantıları: 192.168.1.0 (Chicago) ve 192.168.2.0 (Dallas) ile kaynak NAT bağlantıları  <br/> |

Aşağıda yalnızca giden bir hizmet örneği verilmiştir:

|**Bağlantı özelliği**|**Değer**|
|----------|-----------|
|**Ağ trafiği yönü** <br/> |Giden  <br/> |
|**Hizmet** <br/> |SharePoint Online  <br/> |
|**Şirket içi uç nokta (kaynak)** <br/> |Kullanıcı iş istasyonu  <br/> |
|**Genel Office 365 uç noktası (hedef)** <br/> |SharePoint Online (IP adresleri)  <br/> |
|**Genel (İnternet) DNS girişi** <br/> |\*.sharepoint.com (ve daha fazla FQDN)  <br/> |
|**CDN Referansları** <br/> |cdn.sharepointonline.com (ve daha fazla FQDN) - CDN sağlayıcıları tarafından tutulan IP adresleri)  <br/> |
|**IP tanıtımı ve NAT kullanımda** <br/> |**İnternet yolu/Kaynak NAT**: 1.1.1.0/24  <br/> **ExpressRoute yolu/Kaynak NAT**: 1.1.2.0/24 (Chicago) ve 1.1.3.0/24 (Dallas)  <br/> |
|**Bağlantı yöntemi** <br/> |**İnternet**: katman 7 ara sunucusu (.pac dosyası) aracılığıyla  <br/> **ExpressRoute**: doğrudan yönlendirme (ara sunucu yok)  <br/> |
|**Güvenlik/Çevre Denetimleri** <br/> |**İnternet yolu**: DeviceID_002  <br/> **ExpressRoute yolu**: DeviceID_003  <br/> |
|**Yüksek Kullanılabilirlik** <br/> |**İnternet yolu**: Yedekli internet çıkışı  <br/> **ExpressRoute yolu**: 2 coğrafi olarak yedekli ExpressRoute bağlantı hattı boyunca etkin/etkin 'sıcak patates' yönlendirmesi - Chicago ve Dallas  <br/> |
|**Yol simetri denetimi** <br/> |**Yöntem**: Tüm bağlantılar için kaynak NAT  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Bölgesel bağlantı ile ağ topolojisi tasarımınız
<a name="topology"> </a>

Hizmetleri ve bunlarla ilişkili ağ trafiği akışlarını anladıktan sonra, bu yeni bağlantı gereksinimlerini içeren ve Office 365 için ExpressRoute'u kullanmak için yaptığınız değişiklikleri gösteren bir ağ diyagramı oluşturabilirsiniz. Diyagramınız şunları içermelidir:
  
1. Office 365 ve diğer hizmetlerin erişileceği tüm kullanıcı konumları.

2. Tüm internet ve ExpressRoute çıkış noktaları.

3. Yönlendiriciler, güvenlik duvarları, uygulama ara sunucuları ve yetkisiz erişim algılama/önleme dahil olmak üzere ağ içinde ve dışında bağlantıyı yöneten tüm giden ve gelen cihazlar.

4. ADFS web uygulaması proxy sunucularından bağlantıları kabul eden iç ADFS sunucuları gibi tüm gelen trafik için iç hedefler.

5. Tanıtılacak tüm IP alt ağlarının kataloğu

6. kişilerin Office 365 erişeceği her konumu belirleyin ve ExpressRoute için kullanılacak meet-me konumlarını listeleyin.

7. ExpressRoute'tan öğrenilen Microsoft IP ön eklerinin kabul edildiği, filtreleneceği ve yayılacağı iç ağ topolojinizin konumları ve bölümleri.

8. Ağ topolojisi, her ağ kesiminin coğrafi konumunu ve ExpressRoute ve/veya İnternet üzerinden Microsoft ağına nasıl bağlanıyor olduğunu göstermelidir.

Aşağıdaki diyagramda, gelen ve giden yönlendirme tanıtımlarıyla birlikte Office 365 Office 365 kişilerin kullanacağı her konum gösterilmektedir.
  
![ExpressRoute bölgesel coğrafi buluşmam.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Giden trafik için kişiler Office 365 üç yoldan biriyle erişer:
  
1. California'daki insanlar için Kuzey Amerika'da bir buluşma yeri aracılığıyla.

2. Hong Kong'daki insanlar için Hong Kong'daki bir buluşma yeri aracılığıyla.

3. Bangladeş'te daha az kişinin bulunduğu ve ExpressRoute bağlantı hattının sağlanmamış olduğu İnternet üzerinden.

![Bölgesel diyagram için giden bağlantılar.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Benzer şekilde, Office 365 gelen ağ trafiği üç yoldan birini döndürür:
  
1. California'daki insanlar için Kuzey Amerika'da bir buluşma yeri aracılığıyla.

2. Hong Kong'daki insanlar için Hong Kong'daki bir buluşma yeri aracılığıyla.

3. Bangladeş'te daha az kişinin bulunduğu ve ExpressRoute bağlantı hattının sağlanmamış olduğu İnternet üzerinden.

![Bölgesel diyagram için gelen bağlantılar.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Uygun buluşma konumunu belirleme

ExpressRoute bağlantı hattınızın ağınızı Microsoft ağına bağladığı fiziksel konum olan meet-me konumlarının seçimi, kişilerin Office 365 erişeceği konumlardan etkilenir. SaaS teklifi olarak Office 365, IaaS veya PaaS bölgesel modeli kapsamında Azure ile aynı şekilde çalışmaz. Bunun yerine Office 365, kullanıcıların birden çok veri merkezi ve bölgede uç noktalara bağlanması gerekebileceği ve kullanıcının kiracısının barındırıldığı konumda veya bölgede olmayabileceği dağıtılmış bir işbirliği hizmetleri kümesidir.
  
Bu, Office 365 için ExpressRoute için benimle buluşma konumlarını seçerken dikkat etmeniz gereken en önemli nokta, kuruluşunuzdaki kişilerin bağlanacağı yerdir. En iyi Office 365 bağlantısı için genel öneri yönlendirme uygulamaktır; böylece kullanıcı Office 365 hizmetlerine yönelik istekler en kısa ağ yolu üzerinden Microsoft ağına iletilir, bu genellikle "sıcak patates" yönlendirmesi olarak da adlandırılır. Örneğin, Office 365 kullanıcıların çoğu bir veya iki konumdaysa, bu kullanıcıların konumuna en yakın olan meet-me konumlarını seçmek en uygun tasarımı oluşturur. Şirketinizin birçok farklı bölgede büyük kullanıcı popülasyonları varsa, birden çok ExpressRoute bağlantı hattına ve meet-me konumuna sahip olmayı düşünebilirsiniz. Bazı kullanıcı konumlarınız için Microsoft ağı ve Office 365 için en kısa/en uygun yol, iç WAN ve ExpressRoute meet-me noktalarınız üzerinden değil, İnternet üzerinden olabilir.
  
Çoğu zaman, kullanıcılarınıza göreli yakınlığı olan bir bölge içinde seçilebilen birden çok meet-me konumu vardır. Kararlarınıza yol göstermek için aşağıdaki tabloyu doldurun.

**California ve New York'ta planlanan ExpressRoute buluşma konumları**

|Konum  <br/> |Kişi sayısı  <br/> |İnternet çıkışı üzerinden Microsoft ağında beklenen gecikme süresi  <br/> |ExpressRoute üzerinden Microsoft ağında beklenen gecikme süresi  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |~15ms  <br/> |~10ms (Silikon Vadisi aracılığıyla)  <br/> |
|Washington DC  <br/> |15,000  <br/> |~20ms  <br/> |~10ms (New York üzerinden)  <br/> |
|Dallas  <br/> |5,000  <br/> |~15ms  <br/> |~40ms (New York üzerinden)  <br/> |

Office 365 bölgesini, ExpressRoute ağ hizmeti sağlayıcısının benimle toplantı konumlarını ve konuma göre kişi sayısını gösteren genel ağ mimarisi geliştirildikten sonra, herhangi bir iyileştirme yapılıp yapılamadığını belirlemek için kullanılabilir. Ayrıca, benimle buluşma konumuna ulaşmak için trafiğin uzak bir konuma yönlendirildiği küresel saç tokası ağ bağlantılarını da gösterebilir. Küresel ağda bir saç tokası bulunursa, devam etmeden önce düzeltilmelidir. Başka bir buluşma konumu bulun veya saç tokasından kaçınmak için seçmeli İnternet çıkış noktalarını kullanın.
  
İlk diyagramda, Kuzey Amerika iki fiziksel konumu olan bir müşteri örneği gösterilmektedir. Office konumları, Office 365 kiracı konumları ve ExpressRoute meet-me konumları için çeşitli seçenekler hakkındaki bilgileri görebilirsiniz. Bu örnekte müşteri, iki ilkeye göre meet-me konumunu şu sırayla seçmiştir:
  
1. Kuruluşundaki kişilere en yakın olan.

2. Office 365 barındırıldığı microsoft veri merkezine en yakın konum.

![ExpressRoute ABD coğrafi olarak benimle tanışın.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Bu kavramı biraz daha genişleten ikinci diyagramda, benzer bilgiler ve karar alma süreciyle karşı karşıya kalan çok uluslu bir müşteri örneği gösterilmektedir. Bu müşterinin Bangladeş'te küçük bir ofisi var ve bölgede ayak izini büyütmeye odaklanan yalnızca on kişilik küçük bir ekip var. Chennai'de bir buluşma konumu ve Chennai'de barındırılan Office 365 olan bir Microsoft veri merkezi var, bu nedenle benimle buluşma konumu mantıklı olacaktır; ancak on kişi için fazladan bağlantı hattının masrafı ağırdır. Ağınıza baktığınızda, ağ trafiğinizi ağınıza gönderirken gecikme süresinin başka bir ExpressRoute bağlantı hattı elde etmek için sermaye harcamaktan daha etkili olup olmadığını belirlemeniz gerekir.
  
Alternatif olarak, Bangladeş'teki on kişi İnternet üzerinden Microsoft ağına gönderilen ağ trafiğinde giriş diyagramlarında gösterdiğimiz ve aşağıda yeniden üretilen iç ağlarına yönlendireceklerinden daha iyi performansla karşılaşabilir.
  
![Bölgesel diyagram için giden bağlantılar.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Office 365 uygulama planı için ExpressRoute'unuzu oluşturma
<a name="implementation"> </a>

Uygulama planınız hem ExpressRoute'u yapılandırmayla ilgili teknik ayrıntıları hem de ağınızdaki diğer tüm altyapıyı yapılandırma ayrıntılarını (örneğin, aşağıdakiler) içermelidir.
  
- ExpressRoute ile İnternet arasında hangi hizmetlerin bölündüğünü planlayın.

- Bant genişliği, güvenlik, yüksek kullanılabilirlik ve yük devretmeyi planlayın.

- Farklı konumlar için uygun yönlendirme yolu iyileştirmeleri de dahil olmak üzere gelen ve giden yönlendirme tasarlama

- ExpressRoute yollarının ağınıza ne kadar tanıtılacağına ve istemcilerin İnternet veya ExpressRoute yolunu seçme mekanizmasının ne olduğuna karar verin; örneğin, doğrudan yönlendirme veya uygulama ara sunucusu.

- [Sender Policy Framework](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) girişleri de dahil olmak üzere DNS kaydı değişikliklerini planlayın.

- Giden ve gelen kaynak NAT'sı da dahil olmak üzere NAT stratejisini planlayın.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Yönlendirmenizi hem İnternet hem de ExpressRoute ağ yolları ile planlama
<a name="paths"> </a>

- İlk dağıtımınızda, gelen e-posta veya karma bağlantı gibi tüm gelen hizmetlerin İnternet'i kullanması önerilir.

- [PAC/WPAD dosyası](./managing-office-365-endpoints.md), varsayılan yol, ara sunucu ve BGP yol tanıtımlarını yapılandırma gibi son kullanıcı istemci LAN yönlendirmesini planlayın.

- Ara sunucular, güvenlik duvarları ve bulut proxy'leri de dahil olmak üzere çevre yönlendirmesini planlayın.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Bant genişliğinizi, güvenliğinizi, yüksek kullanılabilirliğinizi ve yük devretmenizi planlama
<a name="availability"> </a>

Her ana Office 365 iş yükü için gereken bant genişliği için bir plan oluşturun. Exchange Online, çevrimiçi SharePoint ve Skype Kurumsal Çevrimiçi bant genişliği gereksinimlerini ayrı ayrı tahmin edin. başlangıç noktası olarak Exchange Online ve Skype Kurumsal için sağladığımız tahmin hesaplayıcılarını kullanabilirsiniz; ancak kuruluşunuzun bant genişliği gereksinimlerini tam olarak anlamak için kullanıcı profillerinin ve konumlarının temsili bir örneğini içeren bir pilot test gereklidir.
  
Her İnternet'te ve ExpressRoute çıkış konumunda güvenliğin nasıl işleneceğini planınıza ekleyin, genel eşlemeyi kullanmak Office 365 için tüm ExpressRoute bağlantılarını unutmayın ve yine de dış ağlara bağlanmaya yönelik şirketinizin güvenlik ilkelerine uygun olarak korunması gerekir.
  
Planınıza, hangi kişilerin ne tür bir kesintiden etkileneceği ve bu kişilerin işlerini en basit şekilde tam kapasitede nasıl gerçekleştirebileceklerine ilişkin ayrıntıları ekleyin.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Jitter, Gecikme Süresi, Tıkanıklık ve Kafa Odası ile ilgili Skype Kurumsal gereksinimleri de dahil olmak üzere bant genişliği gereksinimlerini planlama
  
Skype Kurumsal Online ayrıca, [Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı makalesinde](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917) ayrıntılı olarak verilen belirli ek ağ gereksinimlerine sahiptir.
  
[Office 365 için ExpressRoute ile ağ planlaması bölümünde Azure ExpressRoute için](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd) **bant genişliği** planlaması bölümünü okuyun.
  
Pilot kullanıcılarınız ile bant genişliği değerlendirmesi yaparken kılavuzumuzu kullanabilirsiniz; [Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Yüksek kullanılabilirlik gereksinimlerini planlama
  
gereksinimlerinizi karşılamak için yüksek kullanılabilirlik için bir plan oluşturun ve bunu güncelleştirilmiş ağ topolojisi diyagramınıza dahil edin. [Office 365 için ExpressRoute ile ağ planlaması](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd) bölümünde **Azure ExpressRoute ile yüksek kullanılabilirlik ve yük devretme** bölümünü okuyun.
  
#### <a name="plan-for-network-security-requirements"></a>Ağ güvenlik gereksinimlerini planlama
  
Ağ güvenliği gereksinimlerinizi karşılamak için bir plan oluşturun ve bunu güncelleştirilmiş ağ topolojisi diyagramınıza dahil edin. Office 365 **için ExpressRoute ile ağ planlama bölümünde Office 365 senaryolar için Azure** [ExpressRoute'a](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd) güvenlik denetimleri uygulama bölümünü okuyun.
  
### <a name="design-outbound-service-connectivity"></a>Giden hizmet bağlantısı tasarlama
<a name="outbound"> </a>

Office 365 için ExpressRoute'un yabancı olabilecek *giden* ağ gereksinimleri vardır. Özellikle, Office 365 için kullanıcılarınızı ve ağlarınızı temsil eden ve Microsoft'a giden ağ bağlantıları için kaynak uç noktalar olarak davranan IP adresleri aşağıda belirtilen belirli gereksinimleri karşılamalıdır.
  
1. Uç noktalar, şirketinize veya size ExpressRoute bağlantısı sağlayan operatöre kayıtlı genel IP adresleri olmalıdır.

2. Uç noktaların Microsoft'a tanıtılması ve ExpressRoute tarafından doğrulanması/kabul edilmesi gerekir.

3. Uç noktalar, aynı veya daha fazla tercih edilen yönlendirme ölçümüyle İnternet'e tanıtılmamalıdır.

4. ExpressRoute üzerinden yapılandırılmamış Microsoft hizmetleri bağlantı için uç noktalar kullanılmamalıdır.

Ağ tasarımınız bu gereksinimleri karşılamıyorsa, kullanıcılarınızın siyah hol veya asimetrik yönlendirme yönlendirmesi nedeniyle Office 365 ve diğer Microsoft hizmetleri bağlantı hatalarıyla karşılaşma riski yüksektir. Bu durum, Microsoft hizmetleri istekleri ExpressRoute üzerinden yönlendirildiğinde, ancak yanıtlar İnternet üzerinden geri yönlendirildiğinde (veya tam tersi) ve yanıtlar güvenlik duvarları gibi durum bilgisi olan ağ cihazları tarafından bırakıldığında oluşur.
  
Yukarıdaki gereksinimleri karşılamak için kullanabileceğiniz en yaygın yöntem, ağınızın bir parçası olarak uygulanan veya ExpressRoute operatörünüz tarafından sağlanan kaynak NAT'yi kullanmaktır. Kaynak NAT, internet ağınızın ayrıntılarını ve özel IP adreslemesini ExpressRoute'tan soyutlamanızı sağlar ve; uygun IP yolu tanıtımlarıyla birleştiğinde, yol simetrisini sağlamak için kolay bir mekanizma sağlar. ExpressRoute eşleme konumlarına özgü durum bilgisi olan ağ cihazları kullanıyorsanız yol simetrisini sağlamak için her ExpressRoute eşlemesi için ayrı NAT havuzları uygulamanız gerekir.
  
[ExpressRoute NAT gereksinimleri](/azure/expressroute/expressroute-nat) hakkında daha fazla bilgi edinin.
  
Ağ topolojisi diyagramına giden bağlantı için değişiklikleri ekleyin.
  
### <a name="design-inbound-service-connectivity"></a>Gelen hizmet bağlantısını tasarlama
<a name="inbound"> </a>

Çoğu kurumsal Office 365 dağıtımı, Exchange, SharePoint ve Skype Kurumsal karma senaryoları, posta kutusu geçişleri ve ADFS altyapısını kullanarak kimlik doğrulaması gibi Office 365 şirket içi hizmetlere bir tür gelen bağlantı olduğunu varsayar. ExpressRoute, giden bağlantı için şirket içi ağınız ile Microsoft arasında ek bir yönlendirme yolu etkinleştirdiğinizde, bu akışların İnternet'i kullanmaya devam etmesi amaçlanmış olsa bile bu gelen bağlantılar yanlışlıkla asimetrik yönlendirmeden etkilenebilir. Office 365'dan şirket içi sistemlere İnternet tabanlı gelen akışları etkilemediğinden emin olmak için aşağıda açıklanan birkaç önlem önerilir.
  
Gelen ağ trafiği akışları için asimetrik yönlendirme risklerini en aza indirmek için, tüm gelen bağlantıların ağınızın segmentlerine yönlendirilmeden önce kaynak NAT kullanması gerekir ve bu da ExpressRoute'a yönlendirme görünürlüğü sağlar. Kaynak NAT olmadan ExpressRoute'a yönlendirme görünürlüğü olan bir ağ kesimine gelen bağlantılara izin verilirse, Office 365 kaynaklı istekler İnternet'ten girer, ancak Office 365 geri gönderilen yanıt ExpressRoute ağ yolunu Microsoft ağına geri tercih eder ve bu da asimetrik yönlendirmeye neden olur.
  
Bu gereksinimi karşılamak için aşağıdaki uygulama desenlerinden birini göz önünde bulundurabilirsiniz:
  
1. İstekler, İnternet'ten şirket içi sistemlerinize giden yolda güvenlik duvarları veya yük dengeleyiciler gibi ağ donanımlarını kullanarak iç ağınıza yönlendirilmeden önce kaynak NAT gerçekleştirin.

2. ExpressRoute yollarının, ön uç sunucuları veya ters ara sunucu sistemleri gibi gelen hizmetlerin bulunduğu ağ kesimlerine yayılmadığından ve İnternet bağlantılarının işlenmediğinden emin olun.

Ağınızdaki bu senaryoların açıkça hesaplanması ve İnternet üzerinden gelen tüm ağ trafiği akışlarının tutulması, asimetrik yönlendirme dağıtım ve işletimsel riskin en aza indirilmesine yardımcı olur.
  
Bazı gelen akışları ExpressRoute bağlantıları üzerinden yönlendirmeyi seçebileceğiniz durumlar olabilir. Bu senaryolar için aşağıdaki ek konuları dikkate alın.
  
1. Office 365 yalnızca genel IP'leri kullanan şirket içi uç noktaları hedefleyebilir. Başka bir deyişle, şirket içi gelen uç nokta expressroute üzerinden yalnızca Office 365 açık olsa bile bununla ilişkilendirilmiş genel IP'ye sahip olması gerekir.

2. Office 365 hizmetlerinin şirket içi uç noktaları çözümlemek için gerçekleştirdiği tüm DNS ad çözümlemesi genel DNS kullanılarak gerçekleşir. Bu, gelen hizmet uç noktalarının FQDN'sini İnternet'teki IP eşlemelerine kaydetmeniz gerektiği anlamına gelir.

3. ExpressRoute üzerinden gelen ağ bağlantılarını almak için bu uç noktaların genel IP alt ağlarının ExpressRoute üzerinden Microsoft'a tanıtılması gerekir.

4. Bu gelen ağ trafiği akışlarını dikkatle değerlendirerek şirketinizin güvenlik ve ağ ilkelerine uygun güvenlik ve ağ denetimlerinin uygulandığını doğrulayın.

5. Şirket içi gelen uç noktalarınız ExpressRoute üzerinden Microsoft'a tanıtıldıktan sonra ExpressRoute, Office 365 dahil olmak üzere tüm Microsoft hizmetleri için bu uç noktaların tercih edilen yönlendirme yolu haline gelir. Bu, bu uç nokta alt ağlarının yalnızca Office 365 hizmetleriyle iletişim için ve Microsoft ağındaki diğer hizmetlerle iletişim için kullanılması gerektiği anlamına gelir. Aksi takdirde, tasarımınız diğer Microsoft hizmetleri gelen bağlantıların ExpressRoute üzerinden gelen bağlantıları yönlendirmeyi tercih ettiği asimetrik yönlendirmeye neden olurken, dönüş yolu İnternet'i kullanır.

6. ExpressRoute bağlantı hattının veya meet-me konumunun devre dışı olması durumunda, şirket içi gelen uç noktaların istekleri ayrı bir ağ yolu üzerinden kabul etmek için hala kullanılabilir olduğundan emin olmanız gerekir. Bu, bu uç noktaların alt ağlarını birden çok ExpressRoute bağlantı hattı üzerinden tanıtma anlamına gelebilir.

7. Özellikle bu akışlar güvenlik duvarları gibi durum bilgisi olan ağ cihazları arasında geçiş yaparken, ExpressRoute aracılığıyla ağınıza giren tüm gelen ağ trafiği akışları için kaynak NAT uygulamanızı öneririz.

8. ADFS ara sunucusu veya Exchange otomatik bulma gibi bazı şirket içi hizmetler hem Office 365 hizmetlerden hem de İnternet'ten kullanıcılardan gelen istekler alabilir. Bu istekler için Office 365, İnternet üzerinden kullanıcı istekleriyle aynı FQDN'yi hedefleyecektir. İnternet'ten bu şirket içi uç noktalara gelen kullanıcı bağlantılarına izin verirken, Office 365 bağlantıları ExpressRoute kullanmaya zorlamak, önemli yönlendirme karmaşıklığını temsil eder. ExpressRoute üzerinden bu tür karmaşık senaryolar uygulayan müşterilerin büyük çoğunluğu için operasyonel konular nedeniyle önerilmez. Bu ek yük, asimetrik yönlendirme risklerini yönetmeyi içerir ve yönlendirme tanıtımlarını ve ilkelerini birden çok boyutta dikkatle yönetmenizi gerektirir.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Asimetrik yollardan nasıl kaçınabileceğinizi göstermek için ağ topolojisi planınızı güncelleştirin
<a name="asymmetric"> </a>

Kuruluşunuzdaki kişilerin Office 365 ve İnternet'teki diğer önemli hizmetleri sorunsuz bir şekilde kullanabilmesini sağlamak için asimetrik yönlendirmeden kaçınmak istiyorsunuz. Müşterilerin asimetrik yönlendirmeye neden olan iki yaygın yapılandırması vardır. Şimdi kullanmayı planladığınız ağ yapılandırmasını gözden geçirmek ve bu asimetrik yönlendirme senaryolarından birinin mevcut olup olmadığını denetlemek için uygun bir zaman.
  
Başlamak için aşağıdaki ağ diyagramıyla ilişkili birkaç farklı durumu inceleyeceğiz. Bu diyagramda, ADFS veya şirket içi karma sunucular gibi gelen istekleri alan tüm sunucular New Jersey veri merkezindedir ve İnternet'e tanıtılır.
  
1. Çevre ağı güvenli olsa da, gelen istekler için kullanılabilir Kaynak NAT yoktur.

2. New Jersey veri merkezindeki sunucular hem internet hem de ExpressRoute yollarını görebilir.

![ExpressRoute bağlantısına genel bakış.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Bunların nasıl düzeltileceğini de önerebiliriz.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Sorun 1: İnternet üzerinden buluttan şirket içi bağlantıya
  
Aşağıdaki diyagramda, ağ yapılandırmanız İnternet üzerinden Microsoft bulutundan gelen istekler için NAT sağlamadığında alınan asimetrik ağ yolu gösterilmektedir.
  
1. Office 365 gelen isteği, şirket içi uç noktasının IP adresini genel DNS'den alır ve isteği çevre ağınıza gönderir.

2. Bu hatalı yapılandırmada trafiğin gönderildiği çevre ağında yapılandırılmış veya kullanılabilir kaynak NAT yoktur ve sonuç olarak dönüş hedefi olarak gerçek kaynak IP adresi kullanılır.

  - Ağınızdaki sunucu, dönüş trafiğini kullanılabilir herhangi bir ExpressRoute ağ bağlantısı aracılığıyla Office 365 yönlendirir.

  - Sonuç, bu akışın Office 365 için asimetrik bir yoldur ve bu da bağlantının bozulmasına neden olan bir yoldur.

![ExpressRoute Asimetrik yönlendirme sorunu 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Çözüm 1a: Kaynak NAT
  
Gelen isteğe kaynak NAT eklemek, yanlış yapılandırılmış bu ağı çözer. Bu diyagramda:
  
1. Gelen istek, New Jersey veri merkezinin çevre ağı üzerinden girmeye devam eder. Bu kez Kaynak NAT kullanılabilir.

2. Sunucudan gelen yanıt, özgün IP adresi yerine Kaynak NAT ile ilişkili IP'ye geri yönlendirilir ve bu da yanıtın aynı ağ yolu boyunca dönmesine neden olur.

![ExpressRoute Asimetrik yönlendirme çözümü 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Çözüm 1b: Yol Kapsamı
  
Alternatif olarak, ExpressRoute BGP ön eklerinin tanıtılmamasına izin vermemeyi seçebilir ve bu bilgisayarlar için alternatif ağ yolunu kaldırabilirsiniz. Bu diyagramda:
  
1. Gelen istek, New Jersey veri merkezinin çevre ağı üzerinden girmeye devam eder. Bu kez ExpressRoute bağlantı hattı üzerinden Microsoft'tan tanıtılan ön ekler New Jersey veri merkezinde kullanılamaz.

2. Sunucudan gelen yanıt, kullanılabilir tek yol üzerinden özgün IP adresiyle ilişkilendirilmiş IP'ye geri yönlendirilir ve bu da yanıtın aynı ağ yolu boyunca dönmesine neden olur.

![ExpressRoute Asimetrik yönlendirme çözümü 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Sorun 2: ExpressRoute üzerinden buluttan şirket içi bağlantıya
  
Aşağıdaki diyagramda, ağ yapılandırmanız ExpressRoute üzerinden Microsoft bulutundan gelen istekler için NAT sağlamadığında alınan asimetrik ağ yolu gösterilmektedir.
  
1. Office 365 gelen istek, DNS'den IP adresini alır ve isteği çevre ağınıza gönderir.

2. Bu hatalı yapılandırmada trafiğin gönderildiği çevre ağında yapılandırılmış veya kullanılabilir kaynak NAT yoktur ve sonuç olarak dönüş hedefi olarak gerçek kaynak IP adresi kullanılır.

  - Ağınızdaki bilgisayar, dönüş trafiğini kullanılabilir herhangi bir ExpressRoute ağ bağlantısı aracılığıyla Office 365 yönlendirir.

  - Sonuç, Office 365 asimetrik bir bağlantıdır.

![ExpressRoute Asimetrik yönlendirme sorunu 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Çözüm 2: Kaynak NAT
  
Gelen isteğe kaynak NAT eklemek, yanlış yapılandırılmış bu ağı çözer. Bu diyagramda:
  
1. Gelen istek, New York veri merkezinin çevre ağı üzerinden girmeye devam eder. Bu kez Kaynak NAT kullanılabilir.

2. Sunucudan gelen yanıt, özgün IP adresi yerine Kaynak NAT ile ilişkili IP'ye geri yönlendirilir ve bu da yanıtın aynı ağ yolu boyunca dönmesine neden olur.

![ExpressRoute Asimetrik yönlendirme çözümü 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Kağıt ağ tasarımının yol simetrisine sahip olduğunu doğrulama

Bu noktada, uygulama planınızın Office 365 kullanacağınız farklı senaryolar için rota simetrisi sunduğunu kağıt üzerinde doğrulamanız gerekir. Bir kişi hizmetin farklı özelliklerini kullandığında alınması beklenen belirli ağ yolunu tanımlayacaksınız. Şirket içi ağ ve WAN yönlendirmesinden çevre cihazlarına, bağlantı yoluna; ExpressRoute veya internet ve çevrimiçi uç nokta bağlantısı.
  
Daha önce kuruluşunuzun benimseyeceği hizmetler olarak tanımlanan tüm Office 365 ağ hizmetleri için bunu yapmanız gerekir.
  
Bu belgenin ikinci bir kişiyle yolları gözden geçirmesine yardımcı olur. Her ağ atlamasının bir sonraki yolunu nereden alması beklendiğini açıklayın ve yönlendirme yollarını bildiğinizden emin olun. ExpressRoute'un Microsoft sunucusu IP adreslerine her zaman daha kapsamlı bir yol sağladığını ve bunun İnternet varsayılan yolundan daha düşük yol maliyeti sağlayacağını unutmayın.
  
### <a name="design-client-connectivity-configuration"></a>İstemci Bağlantı Yapılandırması Tasarlama
<a name="asymmetric"> </a>

![EXPRESSRoute ile PAC dosyalarını kullanma.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
İnternet'e bağlı trafik için ara sunucu kullanıyorsanız, ağınızdaki istemci bilgisayarların ara sunucunuza geçiş yapmadan Office 365 istediğiniz ExpressRoute trafiğini gönderecek şekilde doğru yapılandırıldığından ve bazı Office 365 trafiği de dahil olmak üzere kalan trafiğin ilgili ara sunucuya gönderildiğinden emin olmak için pac veya istemci yapılandırma dosyalarını ayarlamanız gerekir. PAC dosyaları gibi [Office 365 uç noktalarını yönetme](./managing-office-365-endpoints.md) kılavuzumuzu okuyun.
  
> [!NOTE]
> Uç noktalar haftalık olarak sık sık değişir. Güncel kalmak için yapmanız gereken değişikliklerin sayısını azaltmak için yalnızca kuruluşunuzun benimsediği hizmetlere ve özelliklere göre değişiklik yapmalısınız. Değişikliklerin duyurulduğu ve tüm geçmiş değişikliklerin kaydının tutulduğu, duyurulan IP adreslerinin geçerlilik tarihine ulaşılana kadar tanıtılmayabileceği veya reklamdan kaldırılmayabileceği RSS akışındaki **Geçerlilik Tarihi'ne** çok dikkat edin.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Dağıtım ve test yordamlarınızı oluşturma
<a name="testing"> </a>

Uygulama planınız hem test hem de geri alma planlaması içermelidir. Uygulamanız beklendiği gibi çalışmıyorsa plan, sorunlar keşfedilmeden önce en az sayıda kişiyi etkileyecek şekilde tasarlanmalıdır. Planınızın dikkate alması gereken bazı üst düzey ilkeler aşağıdadır.
  
1. Kesintiyi en aza indirmek için ağ kesimi ve kullanıcı hizmeti ekleme aşamasını oluşturun.

2. ayrı bir İnternet bağlantılı konaktan izleme yolu ve TCP bağlantısı ile yolları test etme planı.

3. Tercihen, gelen ve giden hizmetlerin testi, bir test Office 365 kiracısı olan yalıtılmış bir test ağında yapılmalıdır.

      - Alternatif olarak, müşteri henüz Office 365 kullanmıyorsa veya pilot durumdaysa üretim ağında test gerçekleştirilebilir.

      - Alternatif olarak, yalnızca test ve izleme için ayrılmış bir üretim kesintisi sırasında test gerçekleştirilebilir.

      - Alternatif olarak, her katman 3 yönlendirici düğümündeki her hizmet için yollar denetlenerek test yapılabilir. Bu geri dönüş yalnızca fiziksel test eksikliği risk oluşturacağı için başka bir test mümkün değilse kullanılmalıdır.

### <a name="build-your-deployment-procedures"></a>Dağıtım yordamlarınızı oluşturma

Dağıtım yordamlarınız, daha büyük kişi gruplarına dağıtmadan önce test edilmesine izin vermek için aşamalı olarak küçük kişi gruplarına dağıtılmalıdır. ExpressRoute dağıtımını hazırlamanın birkaç yolu aşağıdadır.
  
1. ExpressRoute'u Microsoft eşlemesi ile ayarlayın ve yol tanıtımlarının yalnızca aşamalı test amacıyla tek bir konağa iletilmesine izin verme.

2. ExpressRoute ağına giden yolları ilk başta tek bir ağ kesimine tanıtın ve yol tanıtımlarını ağ kesimine veya bölgeye göre genişletin.

3. Office 365 ilk kez dağıtıyorsanız ExpressRoute ağ dağıtımını birkaç kişi için pilot olarak kullanın.

4. Ara sunucu kullanıyorsanız, daha fazla eklemeden önce test ve geri bildirimle birkaç kişiyi ExpressRoute'a yönlendirmek için alternatif olarak bir test PAC dosyası yapılandırabilirsiniz.

Uygulama planınız, alınması gereken dağıtım yordamlarının her birini veya ağ yapılandırmasını dağıtmak için kullanılması gereken komutları listelemelidir. Ağ kesintisi süresi geldiğinde, yapılan tüm değişiklikler önceden yazılmış ve eş gözden geçirilmiş yazılı dağıtım planından olmalıdır. ExpressRoute'un teknik yapılandırmasıyla ilgili kılavuzumuza bakın.
  
- E-posta göndermeye devam edecek şirket içi sunucuların IP adreslerini değiştirdiyseniz SPF TXT kayıtlarınızı güncelleştirme.

- IP adreslerini yeni bir NAT yapılandırmasını barındıracak şekilde değiştirdiyseniz, şirket içi sunucular için dns girdilerini güncelleştirme.

- Yönlendirme veya ara sunucu yapılandırmalarını korumak için Office 365 uç nokta bildirimleri için RSS akışına abone olduğunuzdan emin olun.

ExpressRoute dağıtımınız tamamlandıktan sonra test planındaki yordamlar yürütülmelidir. Her yordamın sonuçları günlüğe kaydedilmelidir. Test planı sonuçlarının uygulamanın başarılı olmadığını belirtmesi durumunda özgün üretim ortamına geri dönme yordamları eklemeniz gerekir.
  
### <a name="build-your-test-procedures"></a>Test yordamlarınızı oluşturma

Test yordamlarınız, hem ExpressRoute kullanacak hem de kullanmayacak olan Office 365 için her giden ve gelen ağ hizmeti için testler içermelidir. Yordamlar, şirket LAN'ında şirket içi olmayan kullanıcılar da dahil olmak üzere her benzersiz ağ konumundan test içermelidir.
  
Test etkinliklerine örnek olarak aşağıdakiler verilebilir.
  
1. Şirket içi yönlendiricinizden ağ operatörü yönlendiricinize ping gönderme.

2. 500+ Office 365 ve CRM Online IP adresi tanıtımlarının şirket içi yönlendiriciniz tarafından alınıp alınmadığı doğrulanır.

3. Gelen ve giden NAT'nizin ExpressRoute ile iç ağ arasında çalıştığını doğrulayın.

4. NAT'nize giden yolların yönlendiricinizden tanıtıldığını doğrulayın.

5. ExpressRoute'un tanıtılan ön eklerinizi kabul ettiğini doğrulayın.

      - Eşleme tanıtımlarını doğrulamak için aşağıdaki cmdlet'i kullanın:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Önceki örnekte olduğu gibi daha büyük bir aralığın belirli bir alt kümesi olmadığı sürece genel NAT IP aralığınızın microsoft'a başka bir ExpressRoute veya genel İnternet ağ bağlantı hattı üzerinden tanıtılmadığını doğrulayın.

7. ExpressRoute bağlantı hatları eşleştirilir ve her iki BGP oturumlarının da çalıştığını doğrulayın.

8. NAT'nizin içinde tek bir konak ayarlayın ve yeni bağlantı hattı üzerinden konak outlook.office365.com bağlantıyı test etmek için ping, tracert ve tcpping kullanın. Alternatif olarak, outlook.office365.com ile ilişkili IP adresine bağlanabildiğinizi doğrulamak için MSEE'ye yansıtılmış bir bağlantı noktasında Wireshark veya Microsoft Network Monitor 3.4 gibi bir araç kullanabilirsiniz.

9. Exchange Online için uygulama düzeyi işlevselliğini test edin.

  - Test Outlook Exchange Online bağlanabilir ve e-posta gönderebilir/alabilir.

  - Test Outlook çevrimiçi modu kullanabilir.

  - Akıllı telefon bağlantısını ve gönderme/alma özelliğini test edin.

10. SharePoint Online için uygulama düzeyi işlevselliğini test edin

  - Eşitleme istemcisini test OneDrive İş.

  - Çevrimiçi SharePoint web erişimini test edin.

11. Skype Kurumsal çağırma senaryoları için uygulama düzeyi işlevselliğini test edin:

  - Konferans aramasına kimliği doğrulanmış kullanıcı [son kullanıcı tarafından başlatılan davet] olarak katılın.

  - Kullanıcıyı [MCU'dan gönderilen davet] konferans aramasına davet edin.

  - Skype Kurumsal web uygulamasını kullanarak konferansa anonim kullanıcı olarak katılın.

  - Kablolu bilgisayar bağlantınızdan, IP telefonunuzdan ve mobil cihazınızdan aramaya katılın.

  - Federasyon kullanıcısına çağrı o PSTN Doğrulama çağrısı: çağrı tamamlandı, çağrı kalitesi kabul edilebilir, bağlantı süresi kabul edilebilir.

  - Kişilerin iletişim durumunun hem kiracının üyeleri hem de federasyon kullanıcıları için güncelleştirildiğinden emin olun.

### <a name="common-problems"></a>Yaygın sorunlar

Asimetrik yönlendirme en yaygın uygulama sorunudur. Aranacak bazı yaygın kaynaklar şunlardır:
  
- Kaynak NAT olmadan açık veya düz ağ yönlendirme topolojisi kullanma.

- Hem İnternet hem de ExpressRoute bağlantıları üzerinden gelen hizmetlere yönlendirmek için SNAT kullanmama.

- Geniş bir dağıtım öncesinde expressroute'ta gelen hizmetleri test etme.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Ağınız üzerinden ExpressRoute bağlantısını dağıtma
<a name="testing"> </a>

Dağıtımınızı bir kerede ağın bir parçasına hazırlayın ve her yeni ağ kesimi için geri alma planıyla ağın farklı bölümlerine bağlantıyı aşamalı olarak dağıtın. Dağıtımınız bir Office 365 dağıtımıyla uyumluysa, önce Office 365 pilot kullanıcılarınıza dağıtın ve buradan genişletin.
  
Önce testiniz ve ardından üretim için:
  
- ExpressRoute'u etkinleştirmek için dağıtım adımlarını çalıştırın.

- Ağ yollarının beklendiği gibi olduğunu görmek için test edin.

- Her gelen ve giden hizmette test gerçekleştirin.

- Herhangi bir sorun bulursanız geri alın.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Test ağı kesimiyle ExpressRoute'a test bağlantısı ayarlama

Artık planı kağıt üzerinde tamamladığınıza göre, küçük ölçekte test etme zamanı geldi. Bu testte, şirket içi ağınızdaki bir test alt ağına Microsoft Eşleme ile tek bir ExpressRoute bağlantısı kuracaksınız. Test alt ağından bağlantısı olan bir [deneme Office 365 kiracısı](https://go.microsoft.com/fwlink/p/?LinkID=403802) yapılandırabilir ve test alt ağından üretimde kullanacağınız tüm giden ve gelen hizmetleri ekleyebilirsiniz. Test ağı kesimi için DNS'yi ayarlayın ve tüm gelen ve giden hizmetleri oluşturun. Test planınızı yürütür ve her hizmet için yönlendirme ve yol yayma hakkında bilgi sahibi olduğunuzdan emin olun.
  
### <a name="execute-the-deployment-and-test-plans"></a>Dağıtım ve test planlarını yürütme

Yukarıda açıklanan öğeleri tamamlarken tamamladığınız alanları gözden geçirin ve dağıtım ve test planlarınızı yürütmeden önce sizin ve ekibinizin bunları incelediğinden emin olun.
  
- Ağ değişikliğine dahil olan giden ve gelen hizmetlerin listesi.

- Hem internet çıkışı hem de ExpressRoute meet-me konumlarını gösteren genel ağ mimarisi diyagramı.

- Dağıtılan her hizmet için kullanılan farklı ağ yollarını gösteren ağ yönlendirme diyagramı.

- Değişiklikleri uygulama ve gerekirse geri alma adımlarını içeren bir dağıtım planı.

- Her Office 365 ve ağ hizmetini test eden bir test planı.

- Gelen ve giden hizmetler için üretim yollarının kağıt doğrulaması tamamlandı.

- Kullanılabilirlik testi de dahil olmak üzere bir test ağ kesiminde tamamlanmış bir test.

Dağıtım planının ve test planının tamamından geçebilecek kadar uzun bir kesinti penceresi seçin; sorun giderme için uygun bir süre ve gerekirse geri dönme süresi vardır.
  
> [!CAUTION]
> Hem İnternet hem de ExpressRoute üzerinden yönlendirmenin karmaşık yapısı nedeniyle, karmaşık yönlendirme sorunlarını gidermek için bu pencereye ek arabellek süresi eklenmesi önerilir.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Skype Kurumsal Online için QoS'yi yapılandırma

QoS, Skype Kurumsal Online için ses ve toplantı avantajları elde etmek için gereklidir. ExpressRoute ağ bağlantısının diğer Office 365 hizmet erişiminizi engellemediğinden emin olduktan sonra QoS'yi yapılandırabilirsiniz. QoS yapılandırması, [Skype Kurumsal Online'da ExpressRoute ve QoS makalesinde](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) açıklanmıştır.
  
## <a name="troubleshooting-your-implementation"></a>Uygulamanızın sorunlarını giderme
<a name="troubleshooting"> </a>

İlk olarak bu uygulama kılavuzundaki adımlara bakılacaktır. Uygulama planınızda gözden kaçırılan var mı? Hatayı çoğaltmak ve hata ayıklamak için mümkünse Geri dön ve daha fazla küçük ağ testi çalıştırın.
  
Test sırasında hangi gelen veya giden hizmetlerin başarısız olduğunu belirleyin. Özellikle başarısız olan hizmetlerin her biri için IP adreslerini ve alt ağları alın. Devam edin ve kağıt üzerinde ağ topolojisi diyagramında ilerleyin ve yönlendirmeyi doğrulayın. Özellikle ExpressRoute yönlendirmesinin tanıtıldığı yeri doğrulayın, mümkünse izlemelerle kesinti sırasında bu yönlendirmeyi test edin.
  
PSPing'i her müşteri uç noktasına bir ağ izlemesi ile çalıştırın ve kaynak ve hedef IP adreslerini değerlendirerek beklendiği gibi olduklarını doğrulayın. Telnet'i 25 numaralı bağlantı noktasında kullanıma eklediğiniz herhangi bir posta konağına çalıştırın ve bu beklenen bir durumsa SNAT'nin özgün kaynak IP adresini gizlediğini doğrulayın.
  
ExpressRoute bağlantısıyla Office 365 dağıtırken ExpressRoute için hem ağ yapılandırmasının en uygun şekilde tasarlandığından hem de ağınızdaki istemci bilgisayarlar gibi diğer bileşenleri iyileştirdiğinizden emin olmanız gerektiğini unutmayın. Atlamış olabileceğiniz adımları gidermek için bu planlama kılavuzunu kullanmanın yanı sıra, [Office 365 için bir Performans sorun giderme planı](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) da yazdık.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>İlgili Konular

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 için ExpressRoute ile Yönlendirme](routing-with-expressroute.md)
  
[Office 365 için ExpressRoute ile Ağ planlaması](network-planning-with-expressroute.md)
  
[Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma](bgp-communities-in-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ağınızı Skype Kurumsal Online için iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak çağrı akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)
  
[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[ağ ve performans ayarlamayı Office 365](network-planning-and-performance.md)
