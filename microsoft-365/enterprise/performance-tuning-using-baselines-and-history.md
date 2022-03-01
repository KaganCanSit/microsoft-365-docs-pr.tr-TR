---
title: Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 07/08/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
- SPO_Content
description: Ortaya çıkan sorunları daha önce algılamanıza yardımcı olmak için istemci bilgisayar bağlantılarının geçmişini nasıl kontrol etmeyi öğrenin.
ms.openlocfilehash: 7395b7459264a9463b2b850590163983873a13db
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019481"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama

İş bağlantınız ve işletmeniz arasındaki bağlantı Office 365 denetlemenin birkaç basit yolu vardır ve bu, bağlantınız için kabaca bir taban çizgisi kurmanızı sağlar. İstemci bilgisayar bağlantılarının performans geçmişini bilmek yeni ortaya çıkan sorunları önceden algılamanıza, sorunları tanımlamanıza ve tahmin kurmanıza yardımcı olabilir.
  
Performans sorunları üzerinde çalışmaya alışmadıysanız, bu makale bazı yaygın soruları değerlendirmenizi sağlamak için tasarlanmıştır. Bu sorunun bir hizmet olayı değil de performans sorunu olduğunu Office 365 biliyor musunuz? Uzun dönemde iyi bir performans için nasıl plan hazırlarsınız? Performansı nasıl takip musunuz? Takımınız veya müşterileriniz e-postanızı kullanırken yavaş performansla Office 365 ve bu sorulardan herhangi birini merak ediyorsanız okumaya devam okuyun.
  
> [!IMPORTANT]
> **İstemciniz ile şu anda Office 365 bir performans sorunu mu var?** Sorunları gidermek için Performans sorunlarını giderme [planında belirtilen Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Performans hakkında bilgi Office 365 şey

Office 365, otomasyon ve gerçek kişiler tarafından izlenen, yüksek kapasiteli özel bir Microsoft ağı içinde yer alıyor. Bulut tabanlı bulutun Office 365 mümkün olduğunca performans ayarlaması ve akışıdır. Bulut tabanlı Office 365 İnternet üzerinden bağlanmak zorunda olduğu için, bu hizmetlerde performans üzerinde ince ayarlamalar yapmak için Office 365 vardır.

Performans iyileştirmeleri hiçbir zaman gerçekten bulutta durur, dolayısıyla bulutu sağlıklı ve hızlı tutma deneyimi de aynı değildir. Konumunuzdan Başka bir yere bağlanırken performans sorunu Office 365, Destek sorunuyla başlamamanız veya beklemeniz en iyisidir. Bunun yerine, sorunu 'içeriden' araştırmaya başlasın. Başka bir ifadeyle, ağınız içinden işe başlayabilir ve işlerinizi tamam Office 365. Destek ile bir vakayı açmadan önce veri toplanacak ve sorunu inceleyecek ve çözülecek işlemler gerçekleştirebilirsiniz.
  
> [!IMPORTANT]
> Kapasite planlaması ve sınırlamalarına dikkat Office 365. Bu bilgiler, bir performans sorununu çözmeye çalışırken eğrinin ilerisinde çalışmamanize neden olur. İşte, hizmet açıklamalarını [Microsoft 365 Office 365 bağlantı](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Burası merkezi bir merkezdir ve merkez tarafından sunulan Office 365 kendi Hizmet Açıklamalarına giden bir bağlantı vardır. Başka bir ifadeyle, örneğin SharePoint Online için standart sınırları görmek zorunda olacağınız anlamına gelir; örneğin, [SharePoint Çevrimiçi](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) Hizmet Açıklaması'SharePoint [bulabilirsiniz](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).
  
Performans ölçeğinin kaydırılarak olduğunu anarak sorun gidermeye devam edin. Ideal bir değer elde etmek ve bunu kalıcı olarak korumakla ilgili değildir. Çok fazla sayıda kullanıcı tarafından işe alma veya büyük veri geçişleri yapma gibi zaman zaman yüksek bant genişliğine sahip görevlere bu nedenle performans  etkilerini planlamanız gerekir. Performans hedefleriniz hakkında kabaca bir fikri olması gerekir, ancak birçok değişken performansla oynayabilir, dolayısıyla performans değişiklik gösterir.
  
Performans sorunlarını gidermek için belirli hedeflere ulaşamaz ve bu sayıları süresiz olarak koruyabilirsiniz; önemli olan, mevcut etkinlikleri tüm değişkenlere göre geliştirmektir. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Tamam, bir performans sorunu nasıl görünüyor?

Öncelikle bir hizmet sorunu değil, gerçekten performans sorunu olduğundan emin olun. Performans sorunu, o e-Office 365. Bunları şu şekilde ayıracağız:
  
Hizmet Olayları, hizmet Office 365 sorunlar olduğunda olur. Geçerli durum altında kırmızı veya sarı **simgeler** Microsoft 365 yönetim merkezi. E-posta bağlantılarına bağlanan istemci bilgisayarlarda performansın yavaş Office 365 olabilir. Örneğin, Geçerli durum raporları kırmızı bir simge gösterirse ve Exchange'in yanında Araştırılıyor ifadesini görüyorsanız, yine de organizasyonu kullanan istemci posta kutularının yavaş Exchange Online gelen kişilerden gelen aramaları alabilirsiniz. Böyle bir durumda, performansının Hizmet sorunları Exchange Online olduğunu varsayabilirsiniz.
  
![Hizmet Office 365 durumu olarak gösterilen Sistem Durumu panosu, yeşil renkle Exchange iş yüklerinin olduğu sistem durumu panosu.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
Bu noktada, sistem yöneticisi Office 365 sistem durumunu denetlemeniz ve sonra sistem bakımıyla  ilgili güncel bilgileri tutmak için sık sık Ayrıntıları ve geçmişi görüntülemeniz gerekir. Geçerli **durum** panosu, sizi hizmette yapılan değişiklikler ve sorunlar hakkında güncelleştirmek için yapıldı. Yöneticiden yöneticiye olmak için durum geçmişine yazılan notlar ve açıklamalar, ölçerken yardımcı olmak ve devam eden çalışma hakkında sizi bilgili tutmak için hazırlanmıştır.
  
![Hizmet durumu panosunun Office 365 ve neden Exchange Online geri yüklendi ifadesinin resmi.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Olaylar performansın yavaşlamaya neden olmasına rağmen, bir performans sorunu hizmet olayı değildir. Bir performans sorunu şu şekildedir:
  
- Yönetim merkezi Geçerli durum'da hizmet için nelerin raporlanması **önemli** değil; bir performans sorunu ortaya çıkar.
    
-  Akış için kullanılan bir davranışın tamamlanması veya hiç tamamlanmadı olması çok uzun zaman alır.
    
- Sorunu çoğaltabilirsiniz veya doğru adım dizilerini uygulayın ve soruna neden olacağını bilebilirsiniz.
    
-  Sorun aralıklı olarak devam ediyorsa, yine de bir desen olabilir. Örneğin, saat 10:00'da her zaman erişim iznine sahip ola kullanıcılardan gelen aramaların Office 365. Aramalar öğlen saat civarında bitirecek.
    
Bu liste büyük olasılıkla tanıdık gelecektir; Belki çok tanıdık geliyordur. Bunun bir performans sorunu olduğunu an olduğunda, "Bundan sonra ne yapacak?" sorusu gelir. Bu makalenin kalan bölümü tam olarak bunu belirlemenize yardımcı olur.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Performans sorununu tanımlama ve sınama

Performans sorunları genellikle zaman içinde ortaya çıkıyor, bu nedenle asıl sorunu tanımlamak zor olabilir. Sorun bağlamında iyi bir fikir olan iyi bir sorun deyimi oluşturun ve sonra tekrarlanabilir test adımları gerekir. Burada, yeterli bilgi sağ sağlayacak sorun ifadelerine bazı örnekler verilmiştir:
  
- Eskiden Gelen Kutumdan Takvimime geçiş, önceden fark etmedim ve şimdi kahve molası verdim. Eskiden olduğu gibi davranması için bir neden var mı?
    
- Dosyalarımı SharePoint Online'a yüklemem sonsuza dek devam ediyor. Neden öğleden sonra yavaş da, diğer saatlerinde hızlı? Hızlı değil mi?
    
Yukarıdaki sorun açıklamalarına göre bazı büyük güçlükler vardır. Özel olarak, anlaşılamay gereken çok fazla ambiyans. Örneğin:
  
- Gelen kutusu ile Takvim arasında geçişin önceden dizüstü bilgisayarda nasıl olduğu belirsizdir.
    
- Kullanıcı "Hızlı değil mi" de olduğunda, "hızlı" olan nedir?
    
- "Sonsuza dek" ne kadar sürer? Birkaç saniye mi? Ya da birkaç dakika? Yoksa kullanıcı yemeğe çıkar ve eylem geri döndükten 10 dakika sonra biter mi?
    
Yönetici ve sorun giderici, aşağıdaki genel açıklamalarda yer alan sorunun  ayrıntılarını fark etmeyebilirsiniz. Örneğin, sorunun ne zaman başladığı onlar tarafından bilmiyor. Sorun giderici kullanıcının evden çalıştığını bilmiyor ve yalnızca kendi ev ağlarındayken yavaş geçişle çalıştığını görüyor olabilir. Ya da kullanıcının yerel istemcide yoğun RAM ile çalışan diğer uygulamaları çalıştırması da olabilir. Yöneticiler, kullanıcının daha eski bir işletim sistemi çalıştırıyor veya son güncelleştirmeleri çalıştırmamış olduğunu bilmiyor olabilir.
  
Kullanıcılar bir performans sorunu raporlasa, topları gereken çok fazla bilgi vardır. Bilgileri alma ve kaydetme, sorunun tanınması olarak adlandırılan bir çağrıdır. Performans sorunları hakkında bilgi toplamak için kullanabileceğiniz temel bir listeye aşağıdan bakabilirsiniz. Bu liste çok kapsamlı değildir, ancak başlangıç için bir yerdir:
  
- Sorun hangi tarihte ve günün veya gecenin hangi saatlerinde başladı?
    
- Ne tür bir istemci bilgisayar kullanıyorsunuz ve iş ağınıza nasıl bağlan bağlanmalı (VPN, Kablolu, Kablosuz)?
    
- Uzaktan mı çalışıyor, ofiste miydiniz?
    
- Başka bir bilgisayarda da aynı eylemleri deneyp aynı davranışı mı görüyorsunuz?
    
- Gerçekleştireceğimiz eylemleri not al aşağıdan yazmak için, soruna neden olan adımları izleyin.
    
- Performans saniye veya dakika olarak ne kadar yavaş?
    
- Dünyanın nerede bulunuyorsunuz?
    
Bu sorulardan bazıları diğerlerine göre daha belirgindir. Çoğu kişi, sorun gidericinin sorunu yeniden oluşturmak için tam adımlara ihtiyacı olduğunu anlar. Sonuçta, neyin yanlış olduğunu başka nasıl kaydınız olur ve sorunun düzeldi mi olduğunu başka nasıl sın derliysiniz? Daha az belirgin olan şeyler, "Sorunu hangi tarih ve saatle görüyorsunuz?" ve "Dünyanın neredesiniz?" gibi, birlikte kullanılmaktadır. Kullanıcının ne zaman çalıştığına bağlı olarak, birkaç saatlik zaman farkı, şirket ağlarının bazı bölümleri üzerinde bakım çalışmaları devam ediyor olabilir. Örneğin, şirketinizin hem SharePoint Online'da hem de Şirket içi SharePoint Server 2013 örneğinde arama dizinlerini sorguldıran karma bir SharePoint Arama gibi karma bir uygulaması vardır, şirket içi sunucuda güncelleştirmeler devam ediyor olabilir. Şirketinizin hepsi bulutta ise, sistem bakımı ağ donanımı eklemeyi veya kaldırmayı, şirket çapında güncelleştirmeler sağlamayı ya da DNS'te veya diğer çekirdek altyapıda değişiklikler eklemeyi veya kaldırmayı içerebilir.
  
Bir performans sorununu giderirken, bu biraz olay yeri incelemeye benzer, kanıtlardan sonuç elde etmek için hassas ve dikkatli olmak gerekir. Bunu yapmak için, kanıt toparak iyi bir sorun açıklaması elde etmek gerekir. Bilgisayarın bağlamı, kullanıcının bağlamı, sorunun ne zaman başladığı ve performans sorununu ortaya çıkaran tam adımlar buna dahildir. Bu sorun açıklaması notlarınız arasında en üstteki sayfada olmalı ve orada kal olmalı. Çözüm üzerinde çalışıp çalışmadıktan sonra sorun açıklamasının yeniden üzerinden geçerek gerçekleştirip gerçekleştirip gerçekleştir olmadığını test edip kanıtlamak için gerekli adımları atabilirsiniz. Bu, orada çalışmanızı ne zaman tamamla ilgili olduğunu bilmek açısından önemlidir.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Performansın iyi olduğu zaman nasıl olduğunu biliyor musunuz?

Şanslı değilsanız, kimse bilmiyor. Hiç kimsenin numarası yoktu. Bu, hiç kimsenin "Office 365'ta bir Gelen Kutusu'na göz attırma süresi kaç saniye sürüyordu?" veya "Yöneticilerin bir Lync Online toplantısı olduğunda ne kadar sürüyordu?" sorusunu yanıtlamayacak. Bu, birçok şirket için yaygın bir senaryodur.
  
Performans taban çizgisi burada ne eksik?
  
Taban çizgisi performansınız için size bir bağlam sunar. Şirketinizin gereksinimlerine bağlı olarak, sık sık bir taban çizgisi alsanız iyi olur. Daha büyük bir şirketseniz, Operasyon ekibinin şirket içi ortamınız için taban çizgilerini zaten almaları gerekir. Örneğin, ayın ilk Pazartesi günü tüm Exchange sunucularında ve üçüncü Pazartesi günü tüm SharePoint sunucularında düzeltme ekleri gerçekleştirıyorsanız, Operasyon ekibinin büyük olasılıkla düzeltme eki uygulama sonrası çalıştırılacak görevlerin ve senaryoların listesi vardır ve bu liste kritik işlevlerin çalışır durumda olduğunu kanıtlayabilir. Örneğin, Gelen Kutusu'na açma, Gönder/Al'a tıklama ve klasörlerin güncelleştiril olduğundan emin olun veya SharePoint'ta sitenin ana sayfasına göz atarak kurumsal Arama sayfasına gidin ve sonuç döndüren bir arama yapma.
  
Uygulamalarınız Office 365'te ise, ağın içindeki bir istemci bilgisayardan, çıkış noktasına veya ağdan çıkıp çıkış noktasına kadar olan zamanı (mili saniye) ölçmek için atılacak en temel taban çizgilerinden bazıları Office 365. Araştırılması ve kaydednuz için bazı yararlı taban çizgilerini burada bulabilirsiniz:
  
- İstemci bilgisayarınızla çıkış noktanız (örneğin, proxy sunucunuz) arasındaki cihazları seçin.
    
  - Ortaya çıkan performans sorunlarına bağlam (IP adresleri, cihazın türü, ve veri türü) sahip olmak için cihazlarınızı tanıyor olun.
    
  - Proxy sunucuları yaygın çıkış noktalarıdır, dolayısıyla web tarayıcınızın varsa kullanmak üzere ayarlanmış ara sunucuyu denetlemesini sebilirsiniz.
    
  - Anızı keşfetmesi ve eşlemesi için üçüncü taraf araçlar vardır, ancak cihazlarınızı bulmanın en güvenli yolu ağ ekibinin bir üyesine sormaktır.
    
- İnternet servis sağlayıcınızı (ISS) seçin, iletişim bilgilerini not edin ve kaç devreniz olduğunu ve ne kadar bant genişliğiniz olduğunu sorun.
    
- Şirketi içinde, istemciniz ile çıkış noktası arasındaki kaynakları tanımlayabilir veya ağ sorunları hakkında konuşmak için bir acil durum kişisi tanımlayabilirsiniz.
    
Burada, araçlarla yapılan basit bir testin sizin için hesapy maliyet hesapy maliyete sahip bazı taban çizgilerini vardır:
  
- İstemci bilgisayarınızdan çıkış noktanıza kadar olan mili saniye cinsinden süre
    
- Çıkış noktanızı mili saniye Office 365 kadar olan süre
    
- Gözatmanıza göre sunucu URL'lerini çözüm Office 365 konum
    
- Mili saniye cinsinden ISS'nizin DNS çözümleme hızı, paket geliş (ağ değişimi), yükleme ve indirme süreleri ile ilgili tutarsızlıklar
    
Bu adımları nasıl gerçekleştirmiş olduğunu biliyorsanız, bu makalede daha ayrıntılı bilgi edinacağız. 
  
## <a name="what-is-a-baseline"></a>Taban çizgisi nedir?

Kötü gittiği zaman etkisini bilirsiniz, ancak geçmiş performans verilerinizi bilmiyorsanız, ne zaman ve ne kadar kötü hale geldiğinde bir bağlama sahip olmak mümkün değildir. Dolayısıyla bir taban çizgisi olmadan, bulmacayı çözmek için en önemli ipucu olan bulmaca kutusunda resim eksik olur. Performans sorunlarını gidermede, bir karşılaştırma noktasına ihtiyacınız  *vardır*. Basit performans taban çizgilerini almak zor değildir. Operasyon ekibinin bir takvime göre bunları taşıma görevi olabilir. Örneğin, bağlantının aşağıdaki gibi olduğunu varsayabilirsiniz: 
  
![İstemci, proxy ve sunucu bulutlarını gösteren Office 365 grafiği.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Bu, ağ ekibiyle birlikte kontrol aldığınız ve şirketinizi İnternet için bir proxy sunucusu üzerinden İnternet'e aldığınızı ve istemci bilgisayarınızın buluta gönderdiği tüm istekleri bu proxy'nin işleyeceği anlamına gelir. Bu durumda, bağlantının aradaki tüm cihazları liste halinde liste halinde basitleştirilmiş bir sürümünü çizmeniz gerekir. Şimdi de istemciyle çıkış noktası (İnternet için ağınıza çıkış noktası) ve bulut arasında performansı test etmek için kullanabileceğiniz Office 365 sınayın.
  
![İstemci, proxy ve bulut ile temel ağ ve araç önerileri PSPing, TraceTCP ve ağ izleme.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Performans verilerini bulmak **için gereken** **uzmanlık** miktarından dolayı seçenekler Basit ve Gelişmiş olarak listelenmiştir. Ağ izleme, PsPing ve TraceTCP gibi komut satırı araçlarını çalıştırmaya göre çok uzun zaman alır. Bu iki komut satırı aracı, Office 365 tarafından engellenen ICMP paketleri kullanmamaları ve istemci bilgisayardan veya proxy sunucusundan (erişiminiz varsa) ayrılacak mili saniye cinsinden zaman vermeleri ve Office 365'e ulaşacakları için seçilmiştir. Bir bilgisayardan diğerine her sıçrama bir zaman değeriyle sonuçlanır ve bu da taban çizgisi için mükemmeldir! En önemlisi, bu komut satırı araçları komuta bir bağlantı noktası numarası eklemenize olanak sağlar; Office 365 Güvenli Yuva Katmanı ve Aktarım Katmanı Güvenliği (SSL ve TLS) tarafından kullanılan bağlantı noktası olan bağlantı noktası 443 üzerinden iletişim kurarsa, bu yararlı olur. Bununla birlikte, diğer üçüncü taraf araçları sizin durumunuz için daha iyi bir çözüm olabilir. Microsoft bu araçların hepsini desteklemez, bu nedenle herhangi bir nedenden dolayı PsPing ve TraceTCP'nin çalışmaya devam etmelerini alamasanız da Netmon gibi bir araçla ağ izlemeye devam edin. 
  
Taban çizgilerini iş saatlerinden önce, tekrar yoğun kullanım sırasında ve tekrar saatler sonra alırsınız. Bu, sonunda biraz buna benzer bir klasör yapınız olduğu anlamına gelir:
  
![Performans verilerinizi klasörlerde düzenleme yolunu teklifen grafik.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Ayrıca dosyalarınıza bir adlandırma kuralı da koyabilirsiniz. İşte birkaç örnek:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Bunu yapmak için birçok farklı yol vardır, ancak bu biçimi kullanmak **\<dateTime\>\<what's happening in the test\>** iyi bir başlangıç olabilir. Bu konuda titiz olmak, daha sonra sorunları gidermeye çalışırken size çok yardımcı olur. Daha sonra şöyle dersiniz: "8 Şubat'ta iki izleme aldım, biri iyi, biri kötü performans gösterdiği için bunları karşılaştıracağız". Bu, sorun giderme için yararlıdır. 
  
Geçmiş taban çizgilerinizi tutmak için düzenli bir yol gerekir. Bu örnekte, basit yöntemler üç komut satırı çıktısı üretti ve sonuçlar ekran görüntüsü olarak toplanıyor, ancak bunun yerine ağ yakalama dosyalarınız da olabilir. Size en uygun yöntemi kullanın. Geçmiş taban çizgilerinizi depolar ve çevrimiçi hizmetlerin davranışında değişiklik fark eden noktalarda bu taban çizgilerine bakın. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Pilot çalışma sırasında neden performans verileri toplayabilirsiniz?

Temel yapmaya başlamak için, temel uygulama hizmetinin pilot çalışma süresinden daha Office 365 yoktur. Ofisinizin binlerce, yüz binlerce kullanıcısı veya beş olabilir, ancak birkaç kullanıcıyla bile performans dalgalanmalarını ölçmek üzere testler gerçekleştirebilirsiniz. Büyük bir şirket durumunda, birkaç yüz kullanıcıdan sadece Office 365 temsili bir örnek, birkaç bin kullanıcıya kadar proje dışında proje olabileceği için, sorunlardan önce sorunların nerede ortaya çık olabileceğini bilirsiniz.
  
Pilot çalışma olmayan tüm kullanıcıların aynı anda hizmete gidecekleri küçük bir şirket olması durumunda, performansı kötü olan bir işlemde sorun gidermesi gerekebilecek herhangi birine gösterecek verileriniz olması için performans ölçülerini alın. Örneğin daha önce çabuk olan orta büyüklükte bir grafiği karşıya yüklemek için gereken sürede bütün binayı dolaştırabiliyorsanız.
  
## <a name="how-to-collect-baselines"></a>Taban çizgilerini toplama

Tüm sorun giderme planlarında, en azından bunları tanımlamanıza gerek vardır:
  
- Kullanmakta olduğunu istemci bilgisayar (bilgisayar veya cihazın türü, IP adresi ve soruna neden olan eylemler)
    
- İstemci bilgisayarın dünyada bulunduğu yer (örneğin, bu kullanıcının ağa yönelik bir VPN'de olup olmadığı, uzaktan çalışma veya şirket intraneti üzerinde çalışma)
    
- İstemci bilgisayarın ağınız üzerinden kullandığı çıkış noktası (trafiğin işletmeden ISS veya İnternet'e çıkış noktası)
    
 Ağ yöneticinizden, ağ düzeninizi bulabilirsiniz. Küçük bir ağa bağlıysanız, sizi İnternet'e bağlayan cihazlara bakın ve düzen hakkında sorularınız varsa ISS'nizi arayın. Başvuru için son düzenin bir grafiğini oluşturun. 
  
Bu bölüm, basit komut satırı araçlarına ve yöntemlerine ve daha gelişmiş araç seçeneklerine bozuk olur. Önce basit yöntemleri açıklarız. Ancak, şu anda bir performans sorunun varsa, gelişmiş yöntemlere atlayıp örnek performans sorunlarını giderme eylem planını denemeniz gerekir.
  
### <a name="simple-methods"></a>Basit yöntemler

Bu basit yöntemlerin amacı, performans hakkında bilinçli olmak için zaman içinde basit performans taban çizgilerini alma, anlama ve uygun şekilde depolamayı Office 365 etmektir. Daha önce de bildiğiniz gibi basit bir diyagram şu şekilde:
  
![İstemci, proxy ve bulut ile temel ağ ve araç önerileri PSPing, TraceTCP ve ağ izleme.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP'nin bu ekran görüntüde yer aldığı için, bir isteğin işlemeye alındığına mili saniye cinsinden ve isteğin hedefe ulaşmak için bir bilgisayardan bir sonrakine kaç sıçrama veya bağlantı atlayıp ulaştığını mili saniye cinsinden göstermede yararlı bir araçtır. TraceTCP ayrıca sıçramalarda kullanılan sunucuların adlarını da verir ve bu Destek'te bir sorun giderici Microsoft Office 365 yararlı olabilir. > TraceTCP komutları çok basit olabilir, örneğin: >  `tracetcp.exe outlook.office365.com:443`> Bağlantı noktası numarasını komuta dahil edin! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) ücretsiz bir indirmedir, ancak Wincap ile dayandır. Wincap de Netmon tarafından kullanılan ve yüklenmiş bir araçtır. Netmon'i ayrıca gelişmiş yöntemler bölümünde de kullanıruz. 
  
 Birden fazla ofisiniz varsa, bu konumların her birsinde de bir istemciden gelen bir veri kümesi tutmalısiniz. Bu sınama, bu durumda Office 365'e istek gönderen bir istemciyle isteği yanıtlayın arasındaki Office 365 bir sayı değeri olan gecikme süresini zamanlar. Test, etki alanınız içinde bir istemci bilgisayardan kaynak olur ve ağınız içinde, bir çıkış noktasından İnternet'e ve geri doğru gidiş dönüş Office 365 baktır. 
  
Bu durumda proxy sunucusu çıkış noktasıyla başa çıkış noktasına birkaç yol vardır. 1'den 2'ye ve sonra 2'den 3'e kadar izleme ve sonra da sayıları mili saniye cinsinden ekp, toplamını ağ bağlantınızı kenarına çıkarabilirsiniz. Ya da, bu adresler için proxy'yi atlayarak bağlantıyı Office 365 yapılandırabilirsiniz. Güvenlik duvarı, ters ara sunucu veya bu ikinin bir birleşiminin birleşiminin olduğu daha büyük bir ağda, çok sayıda URL için trafiğin geçişini sağlayacak ara sunucu üzerinde özel durumlar yapmak gerekebilir. OFFICE 365 tarafından kullanılan uç noktaların listesi için bkz. Office 365 [VE IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Kimlik doğrulayıcı bir proxy'niz varsa, aşağıdaki özel durumları test etmekle başlayabilirsiniz:
  
- 80 ve 443 bağlantı noktaları
    
- TCP ve HTTP'ler
    
- Şu URL'lerin herhangi birini giden bağlantılar:
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Tüm kullanıcıların, herhangi bir proxy müdahalesi veya kimlik doğrulaması olmadan bu adreslere erişim iznine sahip olması gerekir. Daha küçük bir ağ üzerinde, bunları web tarayıcınızdaki proxy atlama listeniz'e eklemeniz gerekir. 
  
Bunları Internet Explorer'da proxy atlama listene eklemek için Araçlar  \> İnternet Seçenekleri Bağlantılar LAN **ayarları** \> **Gelişmiş'e** \>  \> **gidin**. Gelişmiş sekmesi, proxy sunucu ve proxy sunucu bağlantı noktasınızı da burada bulur. Gelişmiş düğmesine erişmek için LAN'niz için **ara sunucu kullanın** onay kutusuna **tıklamanız** gerekir. Yerel adresler için ara sunucuyu **atla'nın işaretli olduğundan emin** olun. **Gelişmiş'e** tıklarken, özel durumları girebilirsiniz. Yukarıda listelenen joker karakter URL'leri noktalı virgülle birbirinden ayırma; örneğin:
  
\*.microsoftonline.com; \*.sharepoint.com
  
Proxy'nizi atlayan bir kez ping veya PsPing'i doğrudan bir URL'de Office 365 gerekir. Sıradaki **adım ping testi** yapmak outlook.office365.com. Ya da PsPing veya komutta bağlantı noktası numarası sağlarken başka bir araç kullanıyorsanız, ortalama gidiş dönüş sürelerini mili saniye cinsinden görmek için **portal.microsoftonline.com:443** karşı PsPing. 
  
Gidiş dönüş süresi veya RTT, outlook.office365.com gibi bir sunucuya HTTP isteği göndermenin ve sunucunun bunu yaptığını bildiğini kabul eden bir yanıt almak için ne kadar zaman yaptığını ölçüleri alan bir sayı değeridir. Bunu bazen RTT olarak kısaltılmış olarak da görüyorsunuz. Bu, görece kısa bir süre olabilir.
  
Bu testi yapmak için [PSPing](/sysinternals/downloads/psping) veya güvenlik tarafından engellenen ICMP paketleri kullanmayan başka bir Office 365 kullanalım. 
  
 **Doğrudan bir URL'den mili saniye cinsinden genel bir gidiş dönüş süresi almak için PsPing Office 365 kullanma**
  
1. Şu adımları tamamlayarak yükseltilmiş komut istemini çalıştırın:
    
1. **Başlat**'a tıklayın.
    
2. Arama Başlat **kutusuna** cmd yazın ve ardından CTRL+SHIFT+ENTER tuşlarına basın.
    
3. Kullanıcı Hesabı **Denetimi iletişim** kutusu görüntülenirse, görüntülenen eylemin istediğiniz eylem olduğunu onaylayın ve sonra Devam'a **tıklayın**.
    
2. Aracın (bu durumda PsPing) yüklü olduğu klasöre gidin ve şu kullanıcı URL'lerini test Office 365:
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![Bağlantı noktası 443'microsoft-my.sharepoint.com PSPing komutu.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Bağlantı noktası numarası 443'ü de içermeye emin olun. Şifreli Office 365 kanalda çalıştığını unutmayın. Bağlantı noktası numarası olmadan PsPing yaptıysanız, isteğiniz başarısız olur. Kısa listeniz için ping işlemi yaptıktan sonra, mili saniye olarak (ms) Ortalama süreye bakın. Kaydetmek istediğiniz şey bu!
  
![İstemci ile proxy arasında 2,8 milisaniyelik bir gidiş dönüş süresine sahip PSPing'i gösteren grafik.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Proxy atlama hakkında bilginiz yoksa ve her şeyi adım adım yapmak isterseniz, önce proxy sunucu adını bulmanız gerekir. Internet Explorer'da Araçlar Internet **Seçenekleri** \> **Connections** LAN **ayarları** \> \> **Advanced seçeneğine** \> **gidin**. Gelişmiş **sekmesi** , proxy sunucu listenizin listelenmiş olduğudur. Bir komut isteminde şu görevi tamamlayarak bu proxy sunucusunda ping sınaması yapmak: 
  
 **Proxy sunucusunda ping yapmak ve aşama 1'den 2'ye mili saniye cinsinden bir gidiş dönüş değeri almak için**
  
1. Şu adımları tamamlayarak yükseltilmiş komut istemini çalıştırın:
    
1. **Başlat**'a tıklayın.
    
2. Arama Başlat **kutusuna** cmd yazın ve ardından CTRL+SHIFT+ENTER tuşlarına basın.
    
3. Kullanıcı Hesabı **Denetimi iletişim** kutusu görüntülenirse, görüntülenen eylemin istediğiniz eylem olduğunu onaylayın ve sonra Devam'a **tıklayın**.
    
2. ping yazın ve \<the name of the proxy server your browser uses, or the IP address of the proxy server\> ENTER tuşuna basın. PsPing veya başka bir araç yüklüyse, bunun yerine o aracı kullanmayı da seçebilirsiniz. 
    
    Komutunuz aşağıdaki örneklerden herhangi biri gibi olabilir: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. İzleme işlemi test paketleri göndermeyi durdurursa, mili saniye cinsinden ortalamayı listeleen küçük bir özet elde olur ve bundan sonra da aynı değere sahip oluruz. İstemin ekran görüntüsünü alın ve adlandırma kuralınızı kullanarak kaydedin. Bu noktada, diyagramı değerle doldurmanıza da yardımcı olabilir.
    
Sabah erken saatlerde bir izleme almış ve istemciniz proxy'e (veya İnternet'e çıkışta hangi çıkış sunucusuna olursa olsun) hızlı şekilde bağlanıyor olabilir. Bu durumda, numaralarınız aşağıdaki gibi olabilir:
  
![Bir istemciden proxy'ye 2,8 milisaniyelik gidiş dönüş süresi gösteren grafik.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
İstemci bilgisayarınız proxy (veya çıkış) sunucusuna erişimi olan az sayıda bilgisayardan biri ise, bu bilgisayara uzaktan bağlanarak ve buradan bir Office 365 URL'sinde PsPing yapmak için komut istemini çalıştırarak testin bir sonraki adımını atabilirsiniz. Bu bilgisayara erişiminiz yoksa, sonraki adımla ilgili yardım için ağ kaynaklarınıza başvurarak tam sayıları bu şekilde edinebilirsiniz. Bu mümkün değilse, söz konusu URL'Office 365 PsPing kullanın ve proxy sunucunuza karşı PsPing veya Ping süresiyle karşılaştırın. 
  
Örneğin, istemciden Office 365 URL'sinin 51,84 mili saniyesi varsa ve istemciden proxy sunucusuna (veya çıkış noktasına) 2,8 mili saniyelik mili saniyeniz varsa, çıkıştan Office 365. Benzer şekilde, günün yoğun saatlerinde istemciden proxy sunucusuna 12,25 mili saniye ve istemciden Office 365 URL'sinde 62,01 mili saniyelik PsPing aldıysanız, Office 365 URL'nize proxy çıkış için ortalama değeriniz 49,76 milisaniyedir.
  
![Değerlerin çıkarılana kadar istemciden proxy'e ve istemciden proxy Office 365 milisaniye cinsinden ping'i gösteren ek grafik.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Sorun giderme anlamında, bu taban çizgilerini saklayarak ilginç bir şey bulabilirsiniz. Örneğin, Genelde proxy veya çıkış noktasından Office 365 URL'sinde yaklaşık 40 mili saniye ile 59 mili saniye arasında gecikme süresine sahip olduğunu ve yaklaşık 3 mili saniye ile 7 mili saniye arasında (günün belirli bir saatlerinde karşınıza gelen ağ trafiğinin miktarına bağlı olarak) yaklaşık 3 milisaniye ile çıkış noktası gecikme süresinin olduğunu bulursanız, son üç istemcinizin ara sunucu veya çıkış taban çizgilerinden birini gösteriyorsa mutlaka bir sorun olduğunu bilirsiniz 45 milisaniyelik bir gecikme süresidir.
  
### <a name="advanced-methods"></a>Gelişmiş yöntemler

İnternet isteklerinize ne olduğunu gerçekten bilmek Office 365, ağ izlemeleri hakkında bilgi sahibi olmak gerekir. Bu izlemeler için hangi araçları tercih ederseniz kullanın, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, Geliştirici Pano aracı veya diğer araçlar, ağ trafiğini yakalayıp filtreleyebilirsiniz. Bu bölümde, sorunun daha eksiksiz bir resmini görmek için bu araçlardan birden fazlasını çalıştırmanın yararlı olacağını göreceğiniz. Test sırasında, bu araçlardan bazıları kendi sağlarına da aracı gibi davranır. [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) [veya](performance-troubleshooting-plan.md) [WireShark](https://www.wireshark.org/) Office 365 performans sorunu giderme planı yardımcı makalesinde kullanılan araçlar.
  
Performans taban çizgisi almak bu yöntemin basit kısmıdır ve adımların çoğu bir performans sorunu gidermek için kullanılan adımlarla aynıdır. Performans için taban çizgisi oluşturmanın daha gelişmiş yöntemleri, ağ izleri alıp depolamanız gerekir. Bu makaledeki örneklerin çoğunda SharePoint Online ekleyebilirsiniz, ancak test etmek ve kaydetmek için abone Office 365 hizmetlerde bir ortak eylemler listesi geliştirmeniz gerekir. Temel bir örnek şöyledir:
  
- SPO için taban çizgisi listesi - ** 1. Adım: ** SPO web sitesinin giriş sayfasına gidin ve ağ izleme yapma. İzlemeyi kaydedin. 
    
- SPO için taban çizgisi listesi - 2. Adım **:** Genel Arama yoluyla bir terim (örneğin şirket adınız) için arama Enterprise ve ağ izlemesi yapma. İzlemeyi kaydedin. 
    
- SPO için taban çizgisi listesi- **3. Adım:** Upload Online belge kitaplığına büyük bir dosya SharePoint ve ağ izlemesi yapma. İzlemeyi kaydedin. 
    
- SPO için taban çizgisi listesi- **4. Adım:** Web sitenizin OneDrive sayfasına göz atın ve ağ izleme ekleyin. İzlemeyi kaydedin. 
    
Bu liste, kullanıcıların SharePoint Online'a karşı  gerçekleştir yaptıkları en önemli SharePoint içerir. Son adım olan OneDrive İş'a gidip izleme yapmak için, SharePoint Online giriş sayfasının yükü (çoğu zaman şirketler tarafından özelleştirilebilir) ile OneDrive İş sayfası (nadiren özelleştirilebilir) arasında bir karşılaştırma sağlar. Bu, SharePoint Online sitesinde yavaş yüklenen bir testtir. Testniz için bu farkın kaydını  derlemeniz gerekir.
  
Bir performans sorununun ortasındaysanız, taban çizgisi almakla aynı adımların çoğu aynıdır. Ağ izleri çok önemli hale gelebilir, bu nedenle bundan  *sonra önemli*  izlerin nasıl ele ala idare olacağız. 
  
Bir performans sorunuyla  *başa olmak* için, hemen şimdi performans sorunuyla karşılaşılırken bir izleme alıyor olması gerekir. Günlükleri toplamak için uygun araçlarınız olması ve bir eylem planınız, başka bir ifadeyle, toplanabilirsiniz en iyi bilgileri toplamak için atlanacak sorun giderme eylemlerinin listesi olması gerekir. İlk olarak, dosyaların zamanlamasını yansıtan bir klasöre kaydedilebilir ve bu şekilde testin tarih ve saati kaydedilebilir. Ardından, sorunun adımlarını kendi kendilerine göre daraltabilirsiniz. Bunlar test etmek için tam olarak hangi adımları kullanacağız? Temel bilgileri unutmayın: Sorun yalnızca Başka bir Outlook ise, sorun davranışının tek bir hizmette veya hizmette Office 365 olun. Bu sorunun kapsamını daraltmak, çözerek üzerinde odaklanmanıza yardımcı olur. 
  
## <a name="see-also"></a>Ayrıca bkz.

[Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)