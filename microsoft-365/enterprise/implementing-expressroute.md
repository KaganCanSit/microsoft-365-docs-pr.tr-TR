---
title: Proje için ExpressRoute'u Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: İnternet'e yönelik birçok posta hizmetine alternatif bir yönlendirme yolu sağlayan Office 365 için ExpressRoute'u nasıl Office 365 öğrenin.
ms.openlocfilehash: 9fbfaec8304c0ad5273aed3f07cb3d32c590c638
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015199"
---
# <a name="implementing-expressroute-for-office-365"></a>Proje için ExpressRoute'u Office 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

E-posta için ExpressRoute Office 365 İnternet'e yönelik birçok posta hizmetine alternatif bir Office 365 sağlar. Office 365 için ExpressRoute'un mimarisi, İnternet üzerinden zaten erişilebilir olan Office 365 hizmetlerinin genel IP ön eklerini, söz konusu IP ön eklerinin ağnıza daha sonra yeniden dağıtılmalarını için sağlanan ExpressRoute devrelerine reklamını temel almaktadır. ExpressRoute ile, birçok farklı hizmet için İnternet üzerinden ve ExpressRoute aracılığıyla çeşitli yönlendirme yollarını etkili Office 365 etkinleştirirsiniz. Ağ üzerinde bu yönlendirme durumu, iç ağ topolojinizin tasarımında önemli bir değişikliği temsil ediyor olabilir.
  
 **Durum:** Tam Kılavuzu v2
  
Hem çekirdek ağınıza ve İnternet'e yönlendiren yönlendirmelerin yer alan adanmış bağlantı hattı üzerinden kullanılabilir olmasıyla ilgili ağ karmaşıklıklarına uyum sağlayacak şekilde Office 365 için ExpressRoute uygulamanızı dikkatle planlamanız gerekir. Siz ve takımınız bu kılavuzda ayrıntılı planlamayı ve testi gerçekleştiremediyseniz, ExpressRoute devresi etkinleştirildiğinde Office 365 hizmetleriyle bağlantıda aralıklı olarak veya toplam bağlantı kaybıyla yaşama riskiniz yüksektir.
  
Başarılı bir uygulama için, altyapı gereksinimlerinizi çözümlemeniz, ayrıntılı ağ değerlendirmesi ve tasarımdan geçen ve dikkatle aşamalı ve denetimli bir şekilde derlemeniz ve ayrıntılı bir doğrulama ve test planı oluşturmanız gerekir. Büyük, dağıtılmış bir ortamda, uygulamanın birkaç aya yayılma sık karşılaşılan bir durum değildir. Bu kılavuz, ileriyi planlamanıza yardımcı olacak şekilde tasarlanmıştır.
  
Büyük ve başarılı dağıtımların planlaması altı ay sürebilir ve çoğu durumda kuruluşun ağ, Güvenlik Duvarı ve Ara Sunucu yöneticileri, Office 365 yöneticileri, güvenlik, son kullanıcı desteği, proje yönetimi ve üst düzey sponsorluk gibi birçok alandan ekip üyelerini içerir. Planlama sürecine yatırım yapmak, hizmet kesintisi veya karmaşık ve pahalı sorun giderme işlemleriyle sonuçlanacak dağıtım hatalarının ortaya çıkma olasılığını düşürecek.
  
Bu uygulama kılavuzuna başlamadan önce aşağıdaki önkulların tamam olmasını bekliyoruz.
  
1. ExpressRoute'un önerilen ve onaylanan bir yol olup olmadığını belirlemek için ağ değerlendirmesini tamamladınız.

2. Bir ExpressRoute ağ servis sağlayıcısı seçtiysiniz. [ExpressRoute iş ortakları ve eşleme konumları hakkında ayrıntılı bilgi bulabilirsiniz](/azure/expressroute/expressroute-locations).

3. [ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) belgelerini zaten okumuş ve anlamışsınızdır; iç ağınız ExpressRoute önkulları sona kadar karşılayacaktır.

4. Takımınız [https://aka.ms/expressrouteoffice365](./azure-expressroute.md)[https://aka.ms/ert](https://aka.ms/ert), üzerinde yer alan genel rehberlik ve belgelerin hepsini okuyun ve aşağıdakiler gibi kritik teknik ayrıntıların anlaşılması için Kanal 9'da [Office 365 için Azure ExpressRoute](https://channel9.msdn.com/series/aer) Eğitim serisini izledi:

      - SaaS hizmetlerinin internet bağımlılıkları.

      - Asimetrik yönlendirmelerden kaçınma ve karmaşık yönlendirmeyi işleme.

      - Çevre güvenliği, kullanılabilirlik ve uygulama düzeyi denetimleri bir çerçeveye dahil edilir.

## <a name="begin-by-gathering-requirements"></a>Başlangıç olarak gereksinimleri toplama
<a name="requirements"> </a>

Başlangıç olarak, kuruluş içinde hangi özellikleri ve hizmetleri benimsemeyi planla kapsamında olduğunu belirlersiniz. Farklı e-posta hizmetlerinin hangi özelliklerinin Office 365 kullanılamayacaklarını ve ağ üzerinde hangi konumların bu özellikleri kullananları barındıracaklarını belirlemeniz gerekir. Senaryo kataloğunu kullanarak, bu senaryolardan her biri için gereken ağ özniteliklerini eklemeniz gerekir; örneğin, gelen ve giden ağ trafiği akışları ve Office 365 ExpressRoute üzerinden kullanılabilir olup olmadığını.
  
Kuruluş gereksinimleri toplamak için:
  
- Kurumda kullanmakta olduğu her hizmet için gelen Office 365 giden ağ trafiğinin kataloğunu hazırlar. Farklı Office 365 senaryolar için farklı akışların açıklaması için URL'ler ve IP Office 365 sayfasına bakın.

- Mevcut ağ topolojinizin iç WAN omurgasını ve topolojisini, uydu sitelerinin bağlantısını, son mesafe kullanıcı bağlantısını, çevre çevre çıkış noktalarına yönlendirmeyi ve ara sunucu hizmetlerini gösteren belgeleri toplayın.

  - Hem İnternet hem de önerilen ExpressRoute bağlantı yollarını gösteren Office 365 diğer Microsoft hizmetleri bağlantı kuracakları ağ diyagramlarında gelen hizmeti uç noktalarını belirleme.

  - Tüm coğrafi kullanıcı konumlarını ve konumlar arasındaki WAN bağlantısını, ayrıca şu anda İnternet'e çıkış olan konumları ve ExpressRoute eşleme konumu için çıkış olması önerilen konumları tanımlayabilirsiniz.

  - Bilgi ekleri, güvenlik duvarları gibi tüm uç cihazları tanımlayabilir ve bunların İnternet ve ExpressRoute'un üzerinden akışların akışlarıyla ilişkilerinin kataloğunu bulabilirsiniz.

  - Son kullanıcıların hem İnternet hem de ExpressRoute Office 365 için doğrudan Yönlendirme veya dolaylı uygulama ara sunucusu aracılığıyla hizmetlere mi erişeceklerini belgele.

- Ağ diyagramınıza kiracının konumunu ve buluşma konumlarını ekleyin.

- Başlıca kullanıcı konumlarından projelere beklenen ve gözlemlenen ağ performansını ve gecikme özelliklerini Office 365. E-Office 365 ve dağıtılmış bir hizmet kümesi olduğunu ve kullanıcıların kiracılarının konumdan farklı konumlara bağlanacaklarını unutmayın. Bu nedenle, ExpressRoute ve İnternet bağlantıları üzerinden kullanıcıyla Microsoft genel ağının en yakın kenarı arasındaki gecikme süresini ölçmesi ve iyileştirmesi önerilir. Ağ değerlendirmesinde elde edilen bulgularınızı bu göreve yardımcı olmak için kullanabilirsiniz.

- Yeni ExpressRoute bağlantısıyla karşılaması gereken şirket ağı güvenlik ve yüksek kullanılabilirlik gereksinimlerini listele. Örneğin, İnternet çıkış veya ExpressRoute bağlantı hattı hatası Office 365 kullanıcılar posta bağlantı hattına erişmeye nasıl devam eder?

- Gelen ve giden ya da giden Office 365 İnternet yolunu ve hangilerini ExpressRoute'u kullanmayacaklarını belgele. Kullanıcılarının coğrafi konumlarının ayrıntıları ve şirket içi ağ topolojinizin ayrıntıları, planın bir kullanıcı konumdan diğerine farklı olması gerektirmektedir.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Giden ve gelen ağ trafiğinizin kataloğunu oluşturma
<a name="trafficCatalog"> </a>

Yönlendirmeyi ve diğer ağ karmaşıklıklarını en aza indirmek için, ExpressRoute'u yalnızca yasal düzenleme gereksinimleri nedeniyle veya ağ değerlendirmesi sonucu adanmış bir bağlantı üzerinden olması gereken ağ trafiği akışlarında Office 365 için kullanmanızı öneririz. Buna ek olarak, ExpressRoute yönlendirmenin kapsamını aşamalara güncelleştirmenizi ve giden ve gelen ağ trafiği akışlarına uygulama projesinin farklı ve ayrı aşamaları olarak yaklaşmanız önerilir. Office 365 için ExpressRoute'u yalnızca kullanıcının başlattığı giden ağ trafiği akışlarına dağıtmak ve gelen ağ trafiği akışlarını İnternet üzerinde bırakmak, topolojinin karmaşıklığında artışı ve ek asimetrik yönlendirme olasılıklarının ortaya çıkma riskini denetlemeye yardımcı olabilir.
  
Ağ trafiği kataloğumuz, şirket içi ağınız ile Microsoft arasında olacak tüm gelen ve giden ağ bağlantılarının listelerini içeriyor olmalıdır.
  
- Giden ağ trafiği akışları, iç istemciler veya sunucular gibi şirket içi ortamınız üzerinden başlatılan ve hedef olarak bir bağlantının söz konusu olduğu tüm Microsoft hizmetleri. Bu bağlantılar, Office 365 yolunda ara sunuculardan, güvenlik duvarlardan veya diğer ağ cihazlardan geçen bağlantılar gibi doğrudan Office 365.

- Gelen ağ trafiği akışları, Microsoft bulutundan şirket içi bir ana makineye başlatılan bir bağlantının olduğu tüm senaryolardır. Bu bağlantılar normalde, dışarıdan gelen akışlar için müşteri güvenlik ilkesi tarafından gereken güvenlik duvarından ve diğer güvenlik altyapısından geçerek devam eder.

Hangi hizmetlerin  gelen trafiği göndereceklerini belirlemek ve bağlantı bilgisinin kalan bölümünü belirlemek için [Office 365 için ExpressRoute](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) ile yönlendirme makalenin Yönlendirme simetrisini sağlama bölümünü okuyun ve Office 365 uç noktaları başvuru makalesinde [Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) için **ExpressRoute** olarak işaretlenmiş sütunun olup olmadığını denetleyin.
  
Giden bağlantı gerektiren her hizmette, hizmet için ağ yönlendirmesi, ara sunucu yapılandırması, paket incelemesi ve bant genişliği gereksinimlerini içeren planlı bağlantıyı açıklamak istemeyebilirsiniz.
  
Gelen bağlantı gerektiren her hizmette, bazı ek bilgilere ihtiyacınız vardır. Microsoft bulutunda yer alan sunucular, şirket içi ağınıza bağlantı kuracak. Bağlantıların doğru bir şekilde yapılır olduğundan emin olmak için, bu bağlantının tüm yönlerini (aşağıdakiler gibi) açıklamak istemeniz gerekir: bu gelen bağlantıları kabul eden hizmetler için genel DNS girdileri, CIDR biçimlendirmeli IPv4 IP adresleri, hangi ISS donanımının söz konusu olduğu ve bu bağlantılar için gelen NAT veya kaynak NAT'nin nasıl iş haberleri olduğunu.
  
Asimetrik yönlendirmenin hiç ortayamey olduğundan emin olmak için, İnternet üzerinden mi yoksa ExpressRoute üzerinden mi bağlanıyor olsun, gelen bağlantıların gözden geçirilmesi gerekir. Bazı durumlarda, Office 365 hizmetlerinin gelen bağlantı başlattığı şirket içi uç noktalara başka Microsoft tarafından da erişilebilir ve başka bir şirket içi Microsoft hizmetleri. En önemli olan, bu hizmetlere ExpressRoute yönlendirmesini aynı Office 365 sağlamak diğer senaryoları bozmaz. Birçok durumda, ExpressRoute etkinleştirildikten sonra Microsoft'tan gelen akışların simetrik kalmasını sağlamak için müşterilerin kendi iç ağlarında belirli değişiklikler (örneğin, kaynak tabanlı NAT) uygulamaya ihtiyacı olabilir.
  
Burada, gereken ayrıntı düzeyinin bir örneği velanmıştır. Bu durumda, Exchange ExpressRoute üzerinden şirket içi sisteme yönlendirilebilir. 

|Bağlantı özelliği   |Değer  |
|----------|-----------|
|**Ağ trafiği yönü** <br/> |Gelen  <br/> |
|**Hizmet** <br/> |Exchange Karma  <br/> |
|**Genel Office 365 noktası (kaynak)** <br/> |Exchange Online (IP adresleri)  <br/> |
|**Genel Şirket İçi Uç Noktası (hedef)** <br/> |5.5.5.5  <br/> |
|**Genel (İnternet) DNS girdisi** <br/> |Autodiscover.contoso.com  <br/> |
|**Bu şirket içi uç noktası diğer (şirket içi olmayan) Office 365 tarafından mı Microsoft hizmetleri** <br/> |Hayır  <br/> |
|**Bu şirket içi uç noktası İnternet'in kullanıcılar/sistemler tarafından kullanılacak mı** <br/> |Evet  <br/> |
|**Genel uç noktalar aracılığıyla yayımlanan iç sistemler** <br/> |Exchange Server erişim rolü (şirket içi) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Genel uç noktanın IP tanıtımları** <br/> |**İnternet'e**: **ExpressRoute'a** 5.5.0.0/16: 5.5.5.0/24  <br/> |
|**Güvenlik/Çevre Denetimleri** <br/> |**İnternet yolu**: DeviceID_002  **ExpressRoute yolu**: DeviceID_003  <br/> |
|**Yüksek Kullanılabilirlik** <br/> |Yedekli 2 coğrafi / ExpressRoute bağlantı hattı arasında Etkin/Etkin - Chicago ve Dallas  <br/> |
|**Yol simetrisi denetimi** <br/> |**Yöntem**: Kaynak NAT **İnternet yolu**: 192.168.5.5 **ExpressRoute** yoluna Kaynak NAT gelen bağlantıları: 192.168.1.0 (Chicago) ve 192.168.2.0'a (Dallas) Kaynak NAT bağlantıları  <br/> |

İşte yalnızca giden bağlantı olan bir hizmete örnek:

|**Bağlantı özelliği**|**Değer**|
|----------|-----------|
|**Ağ trafiği yönü** <br/> |Giden  <br/> |
|**Hizmet** <br/> |SharePoint Online  <br/> |
|**Şirket içi uç noktası (kaynak)** <br/> |Kullanıcının iş istasyonu  <br/> |
|**Genel Office 365 noktası (hedef)** <br/> |SharePoint Online (IP adresleri)  <br/> |
|**Genel (İnternet) DNS girdisi** <br/> |\*.sharepoint.com (ve daha fazla FQDN)  <br/> |
|**CDN Başvuruları** <br/> |cdn.sharepointonline.com (ve daha fazla FQDN) - sağlayıcılar tarafından sürdürülen IP CDN)  <br/> |
|**IP reklamları ve kullanımda NAT** <br/> |**İnternet yolu/Kaynak NAT**: 1.1.1.0/24  <br/> **ExpressRoute yolu/Kaynak NAT**: 1.1.2.0/24 (Chicago) ve 1.1.3.0/24 (Dallas)  <br/> |
|**Bağlantı yöntemi** <br/> |**İnternet**: katman 7 ara sunucusu üzerinden (.pac dosyası)  <br/> **ExpressRoute**: doğrudan yönlendirme (ara sunucu yok)  <br/> |
|**Güvenlik/Çevre Denetimleri** <br/> |**İnternet yolu**: DeviceID_002  <br/> **ExpressRoute yolu**: DeviceID_003  <br/> |
|**Yüksek Kullanılabilirlik** <br/> |**İnternet yolu**: Yedekli İnternet çıkış  <br/> **ExpressRoute yolu**: Yedekli 2 coğrafi ExpressRoute bağlantı hattı üzerinden Etkin/Etkin 'sıcak patates' yönlendirmesi - Chicago ve Dallas  <br/> |
|**Yol simetrisi denetimi** <br/> |**Yöntem**: Tüm bağlantılar için Kaynak NAT  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Bölgesel bağlantıyla ağ topolojisi tasarımınız
<a name="topology"> </a>

Hizmetleri ve ilişkili ağ trafiği akışlarını anlıyoruz, bu yeni bağlantı gereksinimlerini bir arada bulunduran ve ağ trafiği için ExpressRoute'u kullanmak üzere yaptığınız değişiklikleri gösteren bir ağ Office 365. Diyagramınız şunları içermeli:
  
1. Posta ve diğer Office 365 erişilebilen tüm kullanıcı konumları.

2. Tüm İnternet ve ExpressRoute çıkış noktaları.

3. Yönlendiriciler, güvenlik duvarları, uygulama ara sunucuları ve izinsiz giriş algılama/önleme gibi ağ üzerinden bağlantı yöneten tüm giden ve gelen cihazları.

4. Tüm gelen trafiğin iç hedefleri, örneğin ADFS web uygulaması ara sunucularından gelen bağlantıları kabul eden iç ADFS sunucuları.

5. Tanıtacak tüm IP alt ağlarının kataloğu

6. Kişilerin postanıza nereden erişeceklerini Office 365 ve ExpressRoute için kullanılacak buluşma konumlarını listele.

7. ExpressRoute'tan öğrenilen Microsoft IP ön eklerinin kabul edilme, filtre uygulama ve yayılma konumu olan iç ağ topolojinizin konumları ve bölümleri.

8. Ağ topolojisi, her ağ kesiminin coğrafi konumunu ve bunun ExpressRoute ve/veya İnternet üzerinden Microsoft ağına nasıl bağlandığını göstersin.

Aşağıdaki diyagramda, kişilerin gelen ve giden yönlendirme tanıtımlarının yanı sıra Office 365'i hangi konumdan kullanacakları Office 365.
  
![ExpressRoute bölgesel coğrafi meet-me.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Giden trafik için, kişiler posta Office 365 şu üç şekilden biriniarak erişebilir:
  
1. California'daki kişiler için Kuzey Amerika'daki bir buluşma konumu aracılığıyla.

2. Hong Kong'daki kişiler için Hong Kong'daki bir buluşma konumu aracılığıyla.

3. Daha az kişinin bulunduğu ve sağlanan ExpressRoute devresi olmadığının Bangladeş'te İnternet aracılığıyla.

![Bölgesel diyagram için giden bağlantılar.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Benzer şekilde, bir iş akışından gelen Office 365 şu üç şekilden birini döndürür:
  
1. California'daki kişiler için Kuzey Amerika'daki bir buluşma konumu aracılığıyla.

2. Hong Kong'daki kişiler için Hong Kong'daki bir buluşma konumu aracılığıyla.

3. Daha az kişinin bulunduğu ve sağlanan ExpressRoute devresi olmadığının Bangladeş'te İnternet aracılığıyla.

![Bölgesel diyagram için gelen bağlantılar.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Uygun buluşma konumunu belirleme

ExpressRoute bağlantı hattının ağınızı Microsoft ağına bağlandığı fiziksel konum olan buluşma konumları seçimi, kişilerin bu konuma nereden erişeceklerini Office 365 etkiler. SaaS teklifi olarak, Office 365, Azure'daki gibi IaaS veya PaaS bölgesel modeli altında çalışmaz. Bunun yerine Office 365, kullanıcıların birden çok veri merkezi ve bölgede uç noktalara bağlanması gerekebilen dağıtılmış bir işbirliği hizmetleri kümesidir ve bu durum kullanıcının kiracısı için aynı konumda veya bölgede olmayabilir.
  
Bu, Office 365 için ExpressRoute'un buluşma konumlarını seçerken dikkate alınması gereken en önemli noktanın, Office 365 kişilerin nereden bağlanacaklarıdır. En iyi Office 365 bağlantısı için yönlendirmeyi uygulamanız, böylelikle Office 365 hizmetleri için kullanıcı isteklerinin en kısa ağ yolu üzerinden Microsoft ağına geçirileni, bu da çoğunlukla 'sıcak patates' yönlendirmesi olarak da adlandırılır. Örneğin, kullanıcıların Office 365 biri veya iki konumda yer aldısa, bu kullanıcıların bulunduğu konuma en yakın buluşma konumlarının seçerek en uygun tasarımı oluşturması gerekir. Şirketinizin birçok farklı bölgede büyük kullanıcı nüfusları varsa, birden çok ExpressRoute devresi ve buluşma konumu olması göz önünde bulundurabilirsiniz. Kullanıcı konumlarından bazıları için, Microsoft ağına ve Office 365'e giden en kısa/en uygun yol, iç WAN'iniz ve ExpressRoute buluşma noktalarınız üzerinden değil İnternet üzerinden olabilir.
  
Çoğu zaman, bir bölgede kullanıcılarınıza görece yakın olan ve seçili olan birden çok buluşma konumu vardır. Kararlarınızı yönlendiren aşağıdaki tabloyu doldurun.

**California ve New York'ta planlanan ExpressRoute buluşma konumları**

|Konum  <br/> |Kişi sayısı  <br/> |İnternet çıkış üzerinden Microsoft ağına beklenen gecikme süresi  <br/> |ExpressRoute üzerinden Microsoft ağına beklenen gecikme süresi  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |~15ms  <br/> |~10ms (Silicon Valley üzerinden)  <br/> |
|Washington DC  <br/> |15,000  <br/> |~20ms  <br/> |~10ms (New York üzerinden)  <br/> |
|Dallas  <br/> |5,000  <br/> |~15ms  <br/> |~40ms (New York üzerinden)  <br/> |

Office 365 bölgesini, ExpressRoute ağ servis sağlayıcısının buluşma konumlarını ve konuma göre kişi miktarını gösteren genel ağ mimarisi geliştirildi. İyileştirmeler yapıp yapılanamadı bunu belirlemek için kullanılabilir. Ayrıca, buluşma konumunu almak için trafiğin uzak bir konuma yönlendirilen Alıkan ağ bağlantılarını da gösterebilir. Genel ağ üzerinde AA'lar keşfedilse, devam etmeden önce bir düzeltme olmalıdır. Başka bir buluşma konumu bulun veya A breakpin'i önlemek için seçmeli İnternet çıkış noktalarını kullanın.
  
İlk diyagramda, Kuzey Amerika'da iki fiziksel konumu olan bir müşteri örneği görünür. Ofis konumlarını, kiracı konumlarını Office 365 ve ExpressRoute buluşma konumları için çeşitli seçenekleri görebilirler. Bu örnekte müşteri buluşma konumunu sırasıyla şu iki ilkeyi temel alarak seçmiştir:
  
1. Kuruluşundaki insanlara yakınlık.

2. Verilerin barındırıldı olduğu Microsoft veri merkezine Office 365 yakınlık.

![ExpressRoute ABD coğrafi meet-me.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Bu kavramı biraz daha genişleterek, ikinci diyagramda benzer bilgiler ve karar verme durumlarında karşı karşıya olan çok uluslu bir müşteri örneği görünür. Bu müşterinin Bangladeş'te, bölgedeki etki alanı kaplamayı üzerine üzerine odaklanan yalnızca on kişilik küçük bir ekibi olan küçük bir ofisi vardır. Chennai'de bir buluşma konumu ve Office 365'de barındırılan bir Microsoft veri merkezi vardır, dolayısıyla buluşma konumu anlamlı olabilir; ancak, on kişi için ek devrenin yükü ağır gelebilir. Ağınıza bakarken, ağ trafiğinizi ağınız üzerinden göndermenin neden olduğu gecikme süresinin, başka bir ExpressRoute devresi almak için harcadığınız paradan daha etkili olup olmadığını belirlemeniz gerekir.
  
Alternatif olarak, giriş diyagramlarında gösterdiğimiz ve aşağıda çizilen diyagramlarda gösterdiğimiz gibi, Bangladeş'te on kişi ağ trafiklerini iç ağlarında yönlendirmeye göre İnternet üzerinden Microsoft ağına gönderilirken daha iyi bir performans da kullanabilirler.
  
![Bölgesel diyagram için giden bağlantılar.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Uygulama planınız için ExpressRoute Office 365 oluşturma
<a name="implementation"> </a>

Aşağıda olduğu gibi, uygulama planınız hem ExpressRoute'u yapılandırmanın teknik ayrıntılarını hem de ağ üzerinde diğer tüm altyapıyı yapılandırma ayrıntılarını kapsayacaktır.
  
- Hangi hizmetlerin ExpressRoute ile İnternet arasında bölüneceklerini planla.

- Bant genişliğini, güvenliği, yüksek kullanılabilirliği ve yük devretmeyi plan edin.

- Farklı konumlar için düzgün yönlendirme iyileştirmeleri de içinde olmak üzere, gelen ve giden yönlendirmeyi tasarlama

- Ne kadar ExpressRoute yönlendirmelerinin ağınıza tanıtacağız ve istemcilerin İnternet veya ExpressRoute yolunu seçme mekanizmasının ne olduğuna karar verin; örneğin, doğrudan yönlendirme veya uygulama ara sunucusu.

- Sender Policy Framework girdileri de [içinde olmak üzere, DNS kaydı değişikliklerini](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) planla.

- Giden ve gelen kaynak NAT de içinde olmak üzere NAT stratejisini planla.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Hem İnternet hem de ExpressRoute ağ yollarınızı kullanarak yönlendirmenizi planlama
<a name="paths"> </a>

- İlk dağıtımınız için, gelen e-posta veya karma bağlantı gibi tüm gelen hizmetlerinin İnternet'i kullanılması önerilir.

- [PAC/WPAD](./managing-office-365-endpoints.md) dosyası, varsayılan yönlendirme, ara sunucular ve BGP yönlendirme tanıtımları gibi son kullanıcı istemci LAN yönlendirmesini plan edin.

- Ara sunucular, güvenlik duvarları ve bulut ara sunucuları dahil olmak üzere çevre yönlendirmesini plan edin.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Bant genişliği, güvenlik, yüksek kullanılabilirlik ve yük devretmeyi planlama
<a name="availability"> </a>

Önemli her iş yükünün gerekli olduğu bant genişliği Office 365 oluşturun. Çevrimiçi bant Exchange Online, SharePoint Online ve diğer Skype Kurumsal ayrı tahmin edin. başlangıç noktası olarak Exchange Online ve Skype Kurumsal için sağladığımız Tahmin Hesaplayıcılarını kullanabilirsiniz; bununla birlikte, kurum un bant genişliği gereksinimlerini tam olarak anlamak için temsili örnek kullanıcı profilleri ve konumlarla bir pilot testi yapılması gerekir.
  
Planınıza her İnternet ve ExpressRoute çıkış konumu için güvenliğin nasıl iş dışarıdan iş ağa bağlanıyor olacağını ekleyin, Office 365'e yönelik tüm ExpressRoute bağlantılarını anımsayın ve yine de şirket güvenlik ilkelerinize uygun olarak dış ağlara bağlanma güvenlik ilkelerine uygun olarak güvenlik altına alınmalıdır.
  
Hangi kişilerin ne tür kesintiden etkilenecekleri ve bu kişilerin en basit şekilde çalışmalarını tam kapasiteyle nasıl gerçekleştireceklerine ilişkin ayrıntıları planınıza ekleyin.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Gecikme, Tıkanıklık ve Skype Kurumsal Alanı ile ilgili gecikme gereksinimlerini içeren bant genişliği gereksinimlerini planlama
  
Skype Kurumsal Online'ın belirli fazladan ağ gereksinimleri de vardır. Bunlar, Skype Kurumsal Online'da Medya Kalitesi ve Ağ [Bağlantısı Performansı makalesinde ayrıntılı olarak açıklanmıştır](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Daha fazla bilgi **için ExpressRoute** ile ağ planlama [makalesinde Azure ExpressRoute için bant Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Pilot kullanıcılarınız ile bir bant genişliği değerlendirmesi yaparken bu kılavuzu kullanabilirsiniz; [Office 365 ve performans geçmişini kullanarak performans ayarını kullanma](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Yüksek kullanılabilirlik gereksinimlerini planlama
  
İhtiyaçlarınızı karşılamak üzere yüksek kullanılabilirlik için bir plan oluşturun ve bunu güncelleştirilmiş ağ topolojisi diyagramınıza dahil edin. Daha fazla bilgi **için ExpressRoute ile ağ planlama makalesinde Azure ExpressRoute** ile [yüksek kullanılabilirlik ve yük devretme Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Ağ güvenlik gereksinimlerini planlama
  
Ağ güvenliği gereksinimlerinizi karşılamak üzere bir plan oluşturun ve bunu güncelleştirilmiş ağ topolojisi diyagramınıza dahil edin. Daha fazla bilgi **için ExpressRoute ile ağ Office 365 senaryolarında Azure ExpressRoute'a** [güvenlik denetimleri uygulama Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Giden hizmeti bağlantısını tasarlama
<a name="outbound"> </a>

E-Office 365 ExpressRoute'un  size yabancı gelen ağ gereksinimleri olabilir. Özel olarak, Microsoft'a giden ağ bağlantıları için kaynak uç Office 365 olmak üzere kullanıcılarınızı ve ağlarınızı temsil eden IP adresleri, aşağıda açıklanan belirli gereksinimleri karşılamalıdır.
  
1. Uç noktalar, şirketinize veya sizin için ExpressRoute bağlantısı sağlayan taşıyıcıya kaydedilmiş genel IP adresleri olmalıdır.

2. Uç noktalar Microsoft'a tanıt edilmeli ve ExpressRoute tarafından doğrulandır edilmeli/kabul edilmeli.

3. Uç noktalar, aynı veya daha fazla tercih edilen yönlendirme ölçümüyle İnternet'e tanıt edilmemelidir.

4. Uç noktalar, ExpressRoute üzerinden yapılandırılmamış Microsoft hizmetleri bağlantıda kullanılamaz.

Ağ tasarımınız bu gereksinimleri karşılamıyorsa, kullanıcılarının yönlendirme kara delikleri veya asimetrik yönlendirme nedeniyle Office 365 diğer ağ bağlantı hataları ve Microsoft hizmetleri bağlantı hataları yaşama riski yüksektir. Bu durum, Microsoft hizmetleri istekleri ExpressRoute üzerinden yönlendirildi ancak yanıtlar İnternet üzerinden geri yönlendirildi (veya tersi) ve yanıtlar, güvenlik duvarı gibi durum bilgisi olan ağ cihazları tarafından bırakılır.
  
Yukarıdaki gereksinimleri karşılamak için kullanabileceğiniz en yaygın yöntem, ağ kapsamında uygulanan veya ExpressRoute taşıyıcınız tarafından sağlanan kaynak NAT'yi kullanmaktır. Kaynak NAT, ExpressRoute'tan İnternet ağın ayrıntılarının ve özel IP adreslerinin özetini alamanıza olanak sağlar ve; düzgün IP yönlendirme tanıtımları ile birlikte, yol simetrisini sağlamak için kolay bir mekanizma sağlar. ExpressRoute eşleme konumlarına özgü, durum bilgili ağ cihazları kullanıyorsanız, yol simetrisini sağlamak için her ExpressRoute eşliği için ayrı NAT havuzları uygulamanız gerekir.
  
[ExpressRoute NAT gereksinimleri hakkında daha fazla bilgi edinebilirsiniz](/azure/expressroute/expressroute-nat).
  
Giden bağlantıyla ilgili değişiklikleri ağ topolojisi diyagramına ekleyin.
  
### <a name="design-inbound-service-connectivity"></a>Gelen hizmeti bağlantısını tasarlama
<a name="inbound"> </a>

Kurumsal Office 365 dağıtımlarının çoğunda, Office 365, SharePoint ve Skype Kurumsal karma senaryolarında, posta kutusu geçişleri ve ADFS altyapısı kullanılarak kimlik doğrulamasında olduğu gibi, Exchange Office 365'den şirket içi hizmetlere bir tür gelen bağlantı olduğu varsayabilirsiniz. ExpressRoute'ta giden bağlantı için şirket içi ağınız ile Microsoft arasında fazladan bir yönlendirme yolu etkinleştirirsiniz; bu gelen bağlantılar, İnternet'i kullanmaya devam etmeyi sürdürse bile, asimetrik yönlendirmeden yanlışlıkla etki yararlanabilir. İnternet tabanlı gelen akışların şirket içi sistemlere olan İnternet tabanlı akışları üzerinde bir etki Office 365 için aşağıda açıklanan birkaç önlemin alınması önerilir.
  
Gelen ağ trafiği akışlarında asimetrik yönlendirme riskini en aza indirmek için, gelen bağlantıların tümlerinin ağ bağlantılarınızı ExpressRoute'ta yönlendirme görünürlüğüne sahip olan kesimlerine yönlendirilmesi için önce kaynak NAT'yi kullanması gerekir. Gelen bağlantıların, ExpressRoute içinde yönlendirme görünürlüğü olan bir ağ kesimine kaynak NAT olmadan girmesine izin verilirse, Office 365'tan kaynaklanan istekler İnternet'e girer, ancak Office 365'a giden yanıt Microsoft ağına geri dönüş için ExpressRoute ağ yolunu tercih eder ve asimetrik yönlendirmeye neden olur.
  
Bu gereksinimi karşılamak için aşağıdaki uygulama düzenlerinden birini kullanabilirsiniz:
  
1. İnternet'tan şirket içi sistemlerinize giden yolda güvenlik duvarları veya yük dengeciler gibi ağ donanımlarını kullanarak istekler iç ağınıza yönlendirmeden önce kaynak NAT gerçekleştirin.

2. Ön uç sunucuları veya ters ara sunucu sistemleri gibi gelen hizmetlerinin iş ettiği İnternet bağlantılarının bulunduğu ağ kesimlerinde ExpressRoute yönlendirmelerinin yayılmay olduğundan emin olun.

Ağ'da bu senaryoların açıkça muhasebeilmesi ve tüm gelen ağ trafiği akışlarının İnternet üzerinde tutulması, dağıtım ve işlemde asimetrik yönlendirme riskini en aza indirmeye yardımcı olur.
  
Bazı durumlarda, bazı gelen akışları ExpressRoute bağlantıları üzerinden yönlendirmeyi seçebilirsiniz. Bu senaryolar için, aşağıdaki fazla dikkate alınacak noktalara göz önünde bulundurul.
  
1. Office 365 genel IP'leri kullanan şirket içi uç noktaları hedefleyene kadar kullanılabilir. Başka bir ifadeyle, şirket içi gelen uç noktası ExpressRoute üzerinden yalnızca Office 365 açık olsa bile, bu uç noktayla ilişkilendirilmiş genel IP'nin olması gerekir.

2. Hizmetlerin şirket içi uç Office 365 çözümlemek için gerçekleştirecekleri tüm DNS ad çözümlemeleri genel DNS kullanılarak olur. Bu, gelen hizmeti uç noktalarının FQDN'sini İnternet'te IP eşlemeleri olarak kaydetmelisiniz.

3. ExpressRoute üzerinden gelen ağ bağlantılarını almak için, bu uç noktalara yönelik genel IP alt ağlarının ExpressRoute üzerinden Microsoft'a tanıt olması gerekir.

4. Şirket güvenlik ve ağ ilkelerinize uygun olarak bu gelen ağ trafiği akışlarına düzgün güvenlik ve ağ denetimlerinin uygulandığını sağlamak için, bu akışları dikkatle değerlendirin.

5. Şirket içi gelen uç noktalarınız ExpressRoute üzerinden Microsoft'a tanıtıldıktan sonra, ExpressRoute bu uç noktalar da dahil olmak üzere tüm Microsoft hizmetleri uç noktaları için etkili bir şekilde tercih Office 365. Başka bir ifadeyle, bu uç nokta alt ağları yalnızca Office 365 hizmetleriyle iletişim için kullanılmalıdır ve Microsoft ağının diğer hizmetleriyle kullanılamaz. Aksi takdirde, Microsoft hizmetleri tasarımınız diğer ağ bağlantılarının gelen bağlantıları ExpressRoute üzerinden yönlendirmeyi tercih ettiği asimetrik yönlendirmeye neden olurken, dönüş yolu İnternet'i kullanır.

6. Bir ExpressRoute bağlantı hattı veya buluşma konumu kapalı durumda olduğu durumda, şirket içi gelen uç noktalarının ayrı bir ağ yolu üzerinden istekleri kabul etmek için hala kullanılabilir durumda olduğundan emin olun. Bu, birden çok ExpressRoute bağlantı hattı aracılığıyla bu uç noktalar için alt ağların reklamını yapmak anlamına da olabilir.

7. ExpressRoute aracılığıyla ağınıza giren tüm gelen ağ trafiği akışları için, özellikle de bu akışlar güvenlik duvarı gibi durum bilgili ağ cihazlarında kesişıyorsa, kaynak NAT uygulanması önerilir.

8. ADFS ara sunucusu veya otomatik bulma Exchange gibi bazı şirket içi hizmetler, hem Office 365 hizmetlerinden hem de İnternet'Office 365 kullanıcılardan gelen istekler alsa da olabilir. Bu istekler Office 365 İnternet üzerinden yapılan kullanıcı istekleriyle aynı FQDN'yi hedefler. Bu şirket içi uç noktalara İnternet'te gelen kullanıcı bağlantılarına izin verme ve ExpressRoute'u kullanmasına izin Office 365, önemli bir yönlendirme karmaşıklığı temsil eder. Müşterilerin büyük çoğunluğunun işlemlerde dikkate alınması gereken noktalar nedeniyle ExpressRoute üzerinden bu tür karmaşık senaryoları uygulamaması önerilmez. Bu ek yük asimetrik yönlendirme risklerini yönetmeyi de içerir ve birden çok boyutta yönlendirme tanıtımlarını ve ilkelerini dikkatle yönetmenizi gerektirir.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Asimetrik yönlendirmeleri nasıl önleyersiniz? göstermek için ağ topolojisi planınızı güncelleştirme
<a name="asymmetric"> </a>

Organizasyonlu kişilerin hem İnternet'te hem de diğer önemli hizmetlerde Office 365 sorunsuz şekilde kullanamalarını sağlamak için asimetrik yönlendirmeyi önlemek istiyor olun. Müşterilerin asimetrik yönlendirmeye neden olan iki yaygın yapılandırma vardır. Şimdi kullanmayı planladığınız ağ yapılandırmasını gözden geçirmek ve bu asimetrik yönlendirme senaryolarından birinin söz olup olmadığını kontrol etmek için uygun bir zaman.
  
Başlangıç olarak, aşağıdaki ağ diyagramıyla ilişkili birkaç farklı durumu incelemiz. Bu diyagramda, ADFS veya şirket içi karma sunucular gibi gelen istekleri alan tüm sunucular New Jersey veri merkezindedir ve İnternet'e tanıtıldı.
  
1. Çevre ağı güvenliyken, gelen istekler için  kullanılabilir Kaynak NAT yoktur.

2. New Jersey veri merkezinde bulunan sunucular hem İnternet hem de ExpressRoute yönlendirmelerini görebilir.

![ExpressRoute bağlantısına genel bakış.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Ayrıca bunları nasıl düzelteceğime ilişkin önerilerimiz de vardır.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Sorun 1: İnternet üzerinden buluttan şirket içi bağlantı
  
Aşağıdaki diyagramda, ağ yapılandırmanız İnternet üzerinden Microsoft bulutundan gelen istekler için NAT sağlamasa da asimetrik ağ yolu göster göstermektedir.
  
1. Şirket dışından gelen Office 365, şirket içi uç noktanın IP adresini genel DNS'den alınır ve isteği çevre ağınıza gönderir.

2. Bu hatalı yapılandırmada, trafiğin gönderildiği çevre ağına yapılandırılmış veya kullanılabilir Kaynak NAT yoktur ve bunun sonucunda dönüş hedefi olarak gerçek kaynak IP adresi kullanılır.

  - Ağ bağlantınız sunucusu dönüş trafiğini kullanılabilir herhangi bir ExpressRoute Office 365 üzerinden bu trafiği yönlendirer.

  - Sonuç, bu akışın Asimetrik yoludur ve Office 365 bağlantısı bozuk olur.

![ExpressRoute Asimetrik yönlendirme sorunu 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Çözüm 1a: Kaynak NAT
  
Gelen isteğine yalnızca kaynak NAT eklemek bu hatalı ağ yapılandırması sorununu çözer. Bu diyagramda:
  
1. Gelen istek New Jersey veri merkezinin çevre ağı aracılığıyla girmeye devam eder. Bu kez Kaynak NAT sağlanmaktadır.

2. Sunucudan gelen yanıt özgün IP adresi yerine Kaynak NAT ile ilişkilendirilmiş IP'ye doğru geri yönlendirildi ve sonuçta yanıt aynı ağ yolu üzerinden geri dönüyor.

![ExpressRoute Asimetrik yönlendirme çözümü 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Çözüm 1b: YönlendirmeCoping
  
Alternatif olarak, ExpressRoute BGP ön eklerin tanıt olmasına izin vermeyerek bu bilgisayarlar için diğer ağ yolunu kaldırmayı seçebilirsiniz. Bu diyagramda:
  
1. Gelen istek New Jersey veri merkezinin çevre ağı aracılığıyla girmeye devam eder. Bu kez, ExpressRoute bağlantı hattı üzerinden Microsoft'tan tanıtilen ön ekler New Jersey veri merkezine kullanılamaz.

2. Sunucudan gelen yanıt özgün IP adresiyle ilişkilendirilmiş IP'ye kullanılabilir tek yönlendirme üzerinden geri döner ve sonuçta yanıt aynı ağ yolu üzerinden dönmüş olur.

![ExpressRoute Asimetrik yönlendirme çözümü 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Sorun 2: ExpressRoute üzerinden buluttan şirket içi bağlantı
  
Aşağıdaki diyagramda, ağ yapılandırmanız ExpressRoute üzerinden Microsoft bulutundan gelen istekler için NAT sağlamasa da asimetrik ağ yolu gösterilebilir.
  
1. Gelen istek, Office 365 IP adresini DNS'den alınır ve isteği çevre ağınıza gönderir.

2. Bu hatalı yapılandırmada, trafiğin gönderildiği çevre ağına yapılandırılmış veya kullanılabilir Kaynak NAT yoktur ve bunun sonucunda dönüş hedefi olarak gerçek kaynak IP adresi kullanılır.

  - Ağ bilgisayarınız dönüş trafiğini tüm kullanılabilir ExpressRoute ağ Office 365 bu ağ üzerinden yönlendirsin.

  - Sonuç, çalışma saatlerinin Asimetrik Office 365.

![ExpressRoute Asimetrik yönlendirme sorunu 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Çözüm 2: Kaynak NAT
  
Gelen isteğine yalnızca kaynak NAT eklemek bu hatalı ağ yapılandırması sorununu çözer. Bu diyagramda:
  
1. Gelen istek New York veri merkezinin çevre ağı aracılığıyla girmeye devam eder. Bu kez Kaynak NAT sağlanmaktadır.

2. Sunucudan gelen yanıt özgün IP adresi yerine Kaynak NAT ile ilişkilendirilmiş IP'ye doğru geri yönlendirildi ve sonuçta yanıt aynı ağ yolu üzerinden geri dönüyor.

![ExpressRoute Asimetrik yönlendirme çözümü 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Ağ tasarımının yol simetrisine sahip olduğunu kağıt üzerinde doğrulama

Bu noktada, uygulama plan ın, bu planı kullanmakta olacağınız farklı senaryolarda yönlendirme simetrisi sunduğuna kağıt üzerinde Office 365. Bir kişi hizmetin farklı özelliklerini kullandığında, alınması beklenen belirli ağ yönlendirmelerini tanımlayabilirsiniz. Şirket içi ağına ve WAN yönlendirmeden çevre cihazlarına, bağlantı yoluna; ExpressRoute veya İnternet'e ve çevrimiçi uç nokta bağlantısına açık.
  
Bu, daha önce kuruma benimseyen hizmetler Office 365 tüm ağ hizmetleri için sizin de bunu yapmak gerekir.
  
Bu kağıt üzerinde yönlendirmeleri adım adım takip eden bu belgeyi ikinci bir kişi ile birlikte yapmak yardımcı olabilir. Her ağ atlamalarının bir sonraki yönlendirmeyi alması beklenen yeri o sunucuya açıklayıp yönlendirme yollarını biliyorsanız emin olun. İnternet varsayılan yönlendirmeye göre yönlendirme maliyetini düşüren ExpressRoute'un Microsoft sunucu IP adreslerine her zaman daha kapsamlı bir yönlendirme sağlayacaktır.
  
### <a name="design-client-connectivity-configuration"></a>İstemci Bağlantı Yapılandırmasını Tasarlama
<a name="asymmetric"> </a>

![ExpressRoute ile PAC dosyalarını kullanma.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
İnternet'e bağlı trafik için ara sunucu kullanıyorsanız, ağınızdaki istemci bilgisayarların ara sunucunuzdan geçiş yapmadan Office 365'e göndermek istediğiniz ExpressRoute trafiğini gönderecek şekilde doğru yapılandırıldığından ve Office 365 trafiğinin bazıları da dahil olmak üzere kalan trafiğin ilgili ara sunucuya gönderildiğiden emin olmak için tüm PAC veya istemci yapılandırma dosyalarını ayarlamanız gerekir. PAC dosyaları gibi [tüm uç Office 365 yönetme](./managing-office-365-endpoints.md) kılavuzumızı okuyun.
  
> [!NOTE]
> Uç noktalar sık sık, her hafta olarak değişir. Güncel kalmak için ihtiyacınız olacak değişiklik sayısını azaltmak için, yalnızca kuruluşun benimsemiş olduğu hizmetlere ve özelliklere göre değişiklik yapabilirsiniz. Değişikliklerin duyurul olduğu ve  geçmiş değişikliklerle ilgili kaydın tutulıldığı RSS akışında Geçerli Tarih'e çok dikkat olun; geçerlik tarihine ulaşılana kadar, duyurulan IP adresleri tanıtılamaz veya tanıtımdan kaldırılabilir.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Dağıtım ve test yordamlarınızı oluşturma
<a name="testing"> </a>

Uygulama planınız hem test hem de geri alma planlamasını içermeli. Uygulama beklendiği gibi çalışmıyorsa, planın sorunlar keşfedilmadan önce mümkün olan en az sayıda kişiyi etkilemesini tasarla çalışması gerekir. Aşağıda, planlarınızı göz önünde bulundurmalıdır.
  
1. Kesintileri en aza indirmek için ağ kesimi ve kullanıcı hizmeti ekleme aşamalarını kullanın.

2. İnternet'e bağlı ayrı bir ana bilgisayarda izleme yolu ve TCP bağlantısıyla yolları test etme planı.

3. Tercihen, gelen ve giden hizmetlerinin testi yalıtılmış bir test ağına, bir test ağına veya kiracıya Office 365 gerekir.

      - Alternatif olarak, müşteri henüz üretim ağına sahip veya pilot aşamasında ise üretim Office 365 test yapılabilir.

      - Alternatif olarak, yalnızca test ve izleme için kenara ayarlanmış bir üretim kesintisi sırasında test yapılabilir.

      - Alternatif olarak, katman 3 yönlendirme düğümlerinin her bir hizmet için yönlendirmelerin denetlenerek test yapılabilir. Bu, başka test mümkün olmadığı zaman kullanılmalıdır çünkü fiziksel test olmaması risklere neden olur.

### <a name="build-your-deployment-procedures"></a>Dağıtım yordamlarınızı oluşturma

Daha büyük kişi gruplarına dağıtım öncesinde, dağıtım yordamlarınızı test amacıyla aşamalı olarak küçük gruplarda dağıtmalısınız. Aşağıda, ExpressRoute'un dağıtımını aşamalı olarak uygulamanın çeşitli yolları ve açıkları ve yapılabilir.
  
1. ExpressRoute'u Microsoft eşliğiyle ayarlayın ve yönlendirme tanıtımlarını yalnızca aşamalı test amacıyla tek bir ana bilgisayara iletin.

2. ExpressRoute ağına yönlendirmeleri ilk başta tek bir ağ kesimine tanıtabilirsiniz ve yönlendirme tanıtımlarını ağ kesimi veya bölgeye göre genişletebilirsiniz.

3. Dağıtım sırasında Office 365, ExpressRoute ağ dağıtımını birkaç kişi için pilot olarak kullanın.

4. Ara sunucuları kullanıyorsanız, alternatif olarak, daha fazla eklemeden önce test ve geri bildirimle birkaç kişiyi ExpressRoute'a yönlendirecek bir test PAC dosyası yapılandırabilirsiniz.

Uygulama planınız, alınması gereken dağıtım yordamlarının her biri veya ağ yapılandırmasının dağıtımı için kullanılmaları gereken komutları listelemektedir. Ağ kesintisi zamanı geldiğinde yapılan tüm değişiklikler, önceden yazılmış ve bir iş esnası tarafından gözden geçirmesi gereken yazılı dağıtım planından olmalıdır. ExpressRoute'un teknik yapılandırmasıyla ilgili kılavuzlarımıza bakın.
  
- E-posta göndermeye devam edecek şirket içi sunucuların IP adreslerini değiştirdiysanız, SPF TXT kayıtlarınızı güncelleştirin.

- Yeni NAT yapılandırmasına olanak sağlayacak şekilde IP adreslerini değiştirdiysanız, şirket içi sunucularda tüm DNS girdilerini güncelleştirme.

- Tüm yönlendirme veya ara sunucu yapılandırmalarını korumak amacıyla Office 365 uç nokta bildirimleri için RSS akışına abone olduğundan emin olun.

ExpressRoute dağıtımınız tamamlandıktan sonra, test planında yer alan yordamlar yürütülmektedir. Her yordamın sonuçları günlüğe kayded gerekir. Test planı sonuçlarının uygulamanın başarılı olmadığını belirt içermesi durumunda, özgün üretim ortamına geri dönme yordamlarını da dahil edin.
  
### <a name="build-your-test-procedures"></a>Test yordamlarınızı oluşturma

Test yordamlarında, hem ExpressRoute'u kullanan hem de kullanmayacak her Office 365 giden ve gelen ağ hizmetinin testleri yer a olmalıdır. Yordamlar, şirket LAN'sinde yer olmayan kullanıcılar da dahil olmak üzere her benzersiz ağ konumu için testler içerebilir.
  
Bazı örnek test etkinlikleri şunlardır.
  
1. Şirket içi yönlendiriciniz üzerinden ağ operatörü yönlendiricinize ping işlemi gerçekleştirin.

2. Şirket içi yönlendiriciniz 500+Office 365 CRM Online IP adresi tanıtımlarını alınmıştır.

3. ExpressRoute ile iç ağ arasında gelen ve giden NAT'nizin çalışıyor olduğunu doğrulama.

4. Yönlendiriciden NAT'nize yönlendirmelerin tanıt insanlar olduğunu doğrulayın.

5. ExpressRoute'un tanıtıldı ön eklerinizi kabul etmiş olduğunu doğrulama.

      - Eşleme tanıtımlarını doğrulamak için aşağıdaki cmdlet'i kullanın:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Genel NAT IP aralığınızı, önceki örnekte olduğu gibi daha büyük bir aralığın belirli bir alt kümesi olmadığı sürece, başka hiçbir ExpressRoute veya genel İnternet ağı bağlantı hattı aracılığıyla Microsoft'a tanıtılama olmadığını doğrular.

7. ExpressRoute devreleri eşleştirildi, her iki BGP oturumunu da çalıştırıyor olduğunu doğrula.

8. NAT'nizin içinde tek bir ana bilgisayar ayarlayın ve yeni bağlantı hattı üzerinden ana bilgisayar bağlantısını test etmek için ping, tracert ve tcpping outlook.office365.com. Alternatif olarak, MSEE'ye yansıtılmış bir bağlantı noktası üzerinde Wireshark veya Microsoft Network Monitor 3.4 gibi bir araç kullanarak outlook.office365.com ile ilişkilendirilmiş IP adresine bağlanabileceksiniz.

9. Tüm işlevler için uygulama düzeyi Exchange Online.

  - E Outlook e-posta gönderme/alma Exchange Online bağlantı kuranın test edin.

  - Outlook modunu kullanabileceğini test edin.

  - Akıllı telefon bağlantısını ve gönderme/alma özelliğini test edin.

10. SharePoint Online için uygulama düzeyi işlevselliğini test edin

  - Eşitleme OneDrive İş test sınayın.

  - SharePoint Online web erişimini test edin.

11. Arama senaryoları için uygulama Skype Kurumsal işlevselliğini test etmek:

  - Kimliği doğrulanmış kullanıcı olarak konferans aramalarına katılın [son kullanıcı tarafından başlatılan davet].

  - Kullanıcıyı konferans araması için davet et [MCU'dan gönderilen davet].

  - Skype Kurumsal web uygulamasını kullanarak anonim kullanıcı olarak konferansa katılın.

  - Kablolu PC bağlantınız, IP telefonunuz ve mobil cihazınızla çağrıya katılın.

  - Federasyon kullanıcısını pstN Çağrı Doğrulamasına arama: Çağrı tamamlanır, çağrı kalitesi kabul edilebilir olur, bağlantı süresi kabul edilebilir olur.

  - Hem kiracının üyeleri hem de federasyon kullanıcıları için kişilerin iletişim durumunun güncelleştirilmiş olduğunu doğrulayın.

### <a name="common-problems"></a>Sık karşılaşılan sorunlar

En yaygın uygulama sorunu asimetrik yönlendirmedir. Burada, sık kullanılan bazı kaynaklara bakın:
  
- Kaynak NAT olmadan açık veya düz bir ağ yönlendirme topolojisi kullanma.

- Hem İnternet hem de ExpressRoute bağlantıları üzerinden gelen hizmetlerini yönlendiren SNAT kullanmama.

- Genel dağıtım öncesinde bir test ağına ExpressRoute'ta gelen hizmetlerini test etmeyebilirsiniz.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Ağınız aracılığıyla ExpressRoute bağlantısını dağıtma
<a name="testing"> </a>

Dağıtımınızı bir defada ağın bir kesimini aşamalı olarak planla, ağın farklı bölümlerine aşamalı olarak sunar ve her yeni ağ kesimi için geri alma planı sunar. Dağıtımınız tek bir dağıtımla Office 365, önce pilot kullanıcılarınıza dağıtın Office 365 ardından bu dağıtımın süresini uzatın.
  
Önce test sonra üretim için:
  
- ExpressRoute'u etkinleştirmek için dağıtım adımlarını çalıştırın.

- Ağ yönlendirmelerini görmenin beklendiği gibi olduğunu test etmek.

- Gelen ve giden her hizmette test gerçekleştirin.

- Herhangi bir sorun keşfedersanız geri alma.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Test ağ kesimiyle ExpressRoute'a bir test bağlantısı ayarlama

Kağıt üzerinde planınız tamamlandı olduğu için, küçük bir ölçekte test etmek zamanı geldi. Bu testte, şirket içi ağ üzerinde test alt ağına Microsoft Eşliği ile tek bir ExpressRoute bağlantısı kurabilirsiniz. Test alt ağın [Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) bağlantısı olan bir deneme sürümü kiracısı yapılandırabilir ve üretimde kullanmakta olacağınız tüm giden ve gelen hizmetlerini test alt ağın içinde sınayabilirsiniz. Test ağ kesimi için DNS'yi ayarlayın ve tüm gelen ve giden hizmetlerini ayarlayın. Test planınızı yürütün ve her hizmetin yönlendirmesi ve yönlendirme yayılması hakkında bilgi sahibi olduğunuzden emin olur.
  
### <a name="execute-the-deployment-and-test-plans"></a>Dağıtım ve test planlarını yürütme

Yukarıda açıklanan öğeleri tamamlarken, tamamlamış olduğunuz alanları gözden geçirin ve dağıtım ve test planlarınızı yürütmeden önce, hem sizin hem de takımınız tarafından gözden geçirildiklerinden emin olun.
  
- Ağ değişikliğine katılan giden ve gelen hizmetlerinin listesi.

- Hem İnternet çıkış hem de ExpressRoute buluşma konumlarını gösteren genel ağ mimarisi diyagramı.

- Dağıtılan her hizmet için kullanılan farklı ağ yollarını gösteren ağ yönlendirme diyagramı.

- Değişiklikleri uygulama ve gerekirse geri alma adımlarını dan yer alan bir dağıtım planı.

- Her bir hizmet veya ağ hizmetini Office 365 bir test planı.

- Gelen ve giden hizmetleri için üretim yönlendirmelerinin kağıt üzerinde tamamlanmış doğrulaması.

- Kullanılabilirlik testi de içinde olmak üzere test ağı kesimi genelinde tamamlanmış bir test.

Tüm dağıtım planını ve test planını çalıştıracak kadar uzun olan, sorun gidermeye ve gerekirse geri dönmek için zamanına sahip olan bir kesinti penceresi seçin.
  
> [!CAUTION]
> Hem İnternet hem de ExpressRoute üzerinden yönlendirmenin karmaşık doğası nedeniyle, karmaşık yönlendirme sorunlarını gidermek için bu pencereye ek süre ekinin kullanılması önerilir.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Skype Kurumsal Online için QoS'i yapılandırma

Skype Kurumsal Online için ses ve toplantı avantajlarını elde etmek Skype Kurumsal gerekir. ExpressRoute ağ bağlantısının diğer ağ hizmeti erişiminizi engellemey olduğundan emin olduktan sonra QoS'i Office 365 yapılandırabilirsiniz. QoS yapılandırması, [Skype Kurumsal Online'da ExpressRoute ve QoS makalesinde açıklanmıştır](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d).
  
## <a name="troubleshooting-your-implementation"></a>Uygulama sorun giderme
<a name="troubleshooting"> </a>

Bakılacak ilk yer, bu uygulama kılavuzunda yer alan adımlardır; uygulama planlarında herhangi bir adım at oldu mu? Geri dönüp hatayı çoğaltmak ve hata ayıklaması yapmak için mümkünse başka küçük ağ testleri çalıştırın.
  
Test sırasında hangi gelen veya giden hizmetlerin başarısız olduğunu belirleme. Özel olarak başarısız olan hizmetlerden her biri için IP adreslerini ve alt ağları kullanın. Devam edin ve kağıt üzerinde ağ topolojisi diyagramının üzerinden geçin ve yönlendirmeyi doğrulayın. Özellikle ExpressRoute yönlendirmenin tanıtıldı yerini doğrulama, mümkünse izlemelerle kesinti sırasında bu yönlendirmeyi test etme.
  
Her müşteri uç noktasına bir ağ izleme ile PSPing çalıştırın ve kaynak ve hedef IP adreslerini değerlendirerek bunların beklendiği gibi olduğunu doğrular. Bağlantı noktası 25'te göstermekte olduğu tüm posta ana bilgisayarlarında telnet'i çalıştırın ve beklenen bu ise SNAT'ın özgün kaynak IP adresini gizler olduğunu doğrulayın.
  
Office 365'i ExpressRoute bağlantısıyla dağıtırken, hem ExpressRoute için ağ yapılandırmasının en uygun şekilde tasarlan olduğundan hem de ağınızdaki istemci bilgisayarlar gibi diğer bileşenleri en iyi duruma getirerek bu yapılandırmayı en iyi duruma getirerek çalışmanız gerekir. Kaçırdığınız adımlarla ilgili sorunları gidermek için bu planlama kılavuzunu kullanmaya ek olarak, bir de Office 365 için Performans sorunlarını [giderme Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c).
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>İlgili Konular

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)
  
[Posta için ExpressRoute ile yönlendirme Office 365](routing-with-expressroute.md)
  
[ExpressRoute ile ağ planlama Office 365](network-planning-with-expressroute.md)
  
[Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma](bgp-communities-in-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online için a Skype Kurumsal iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak arama akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)
  
[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)
