---
title: Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Ortaya çıkan sorunları erken algılamanıza yardımcı olmak için istemci bilgisayar bağlantılarınızın geçmişini denetlemeyi öğrenin.
ms.openlocfilehash: ceb56f88d057d3a003f158369c9d35223852c7fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100445"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365

Office 365 ile işletmeniz arasındaki bağlantı performansını denetlemenin bazı basit yolları vardır ve bağlantınızın kaba bir temelini belirlemenize olanak tanır. İstemci bilgisayar bağlantılarınızın performans geçmişini bilmek, ortaya çıkan sorunları erken algılamanıza, sorunları tanımlamanıza ve tahmin etmenize yardımcı olabilir.
  
Performans sorunları üzerinde çalışmaya alışkın değilseniz, bu makale bazı yaygın soruları göz önünde bulundurmanıza yardımcı olacak şekilde tasarlanmıştır. Gördüğünüz sorunun Office 365 hizmet olayı değil performans sorunu olduğunu nasıl anlarsınız? İyi bir performans için nasıl plan yapabilirsiniz, uzun vadeli? Performansı nasıl takip edebilirsiniz? Ekibiniz veya istemcileriniz Office 365 kullanırken yavaş performans görüyorsa ve bu sorulardan herhangi birini merak ediyorsanız okumaya devam edin.
  
> [!IMPORTANT]
> **İstemcinizle Office 365 arasında şu anda bir performans sorunu mu var?** [Office 365 için Performans sorun giderme planında](performance-troubleshooting-plan.md) açıklanan adımları izleyin. 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Office 365 performansı hakkında bilmeniz gereken bir şey

Office 365, otomasyon ve gerçek kişiler tarafından izlenen yüksek kapasiteli, ayrılmış bir Microsoft ağında yaşar. Office 365 bulutu korumanın bir parçası, mümkün olduğunda performans ayarlama ve akış sağlamadır. Office 365 bulutu istemcilerinin İnternet üzerinden bağlanması gerektiğinden, Office 365 hizmetlerinde de performansa ince ayar yapmak için sürekli çaba sarf edilmektedir.

Performans iyileştirmeleri bulutta hiçbir zaman durmaz, bu nedenle bulutu sağlıklı ve hızlı tutma deneyimi de yoktur. Konumunuzdan Office 365'a bağlanırken bir performans sorununuz varsa, destek olayıyla başlamamak veya beklememek en iyisidir. Bunun yerine, sorunu 'içeriden dışa' araştırmaya başlamanız gerekir. Başka bir ifadeyle ağınızın içinden başlayın ve Office 365... Destek ile bir servis talebi açmadan önce, verileri toplayabilir ve sorunu keşfedecek ve çözebilecek eylemler gerçekleştirebilirsiniz.
  
> [!IMPORTANT]
> Office 365 kapasite planlaması ve sınırları hakkında bilgi edinin. Bu bilgiler, bir performans sorununu çözmeye çalışırken sizi eğrinin önüne koyar. burada [Microsoft 365 ve Office 365 hizmet açıklamalarının bağlantısı yer alır](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Bu merkezi bir merkezdir ve Office 365 tarafından sunulan tüm hizmetlerin buradan kendi Hizmet Açıklamalarına giden bir bağlantısı vardır. Başka bir deyişle, SharePoint Online'ın standart sınırlarını görmeniz gerekirse, örneğin Çevrimiçi [Hizmet Açıklaması'nı SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) tıklayıp [SharePoint Çevrimiçi Sınırlar bölümünü](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) bulursunuz.
  
Performansın kayan bir ölçek olduğunu anlayarak sorun giderme işleminize girdiğinizden emin olun. Bu idealleştirilmiş bir değer elde etmek ve kalıcı olarak korumakla ilgili değildir. Çok sayıda kullanıcıya ekleme veya büyük veri geçişleri yapma gibi bazen yüksek bant genişliğine sahip görevler stresli olacaktır, bu nedenle performans etkilerini *planlayın* . Performans hedefleriniz hakkında kabaca bir fikriniz olmalıdır, ancak birçok değişken performansa dahil olduğundan performans değişir.
  
Performans sorunlarını giderme, belirli hedeflere ulaşmak ve bu sayıları süresiz olarak korumakla ilgili değildir, tüm değişkenler göz önünde bulundurulduğunda mevcut etkinlikleri iyileştirmekle ilgilidir. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Tamam, performans sorunu nasıl görünür?

İlk olarak, karşılaştığınız şeyin gerçekten bir hizmet olayı değil performans sorunu olduğundan emin olmanız gerekir. Performans sorunu, Office 365 hizmet olayından farklıdır. Bunları nasıl ayırt etmek istediğiniz aşağıda anlatılıyor.
  
Hizmet Olayları, Office 365 hizmetinin kendisi sorun yaşadığında gerçekleşir. Microsoft 365 yönetim merkezi **Geçerli sistem durumu** altında kırmızı veya sarı simgeler görebilirsiniz. Office 365 bağlanan istemci bilgisayarlarda performansın yavaş olduğunu fark edebilirsiniz. Örneğin Geçerli sistem durumu kırmızı bir simge bildirirse ve Exchange yanında **Araştırılıyor** ifadesini görüyorsanız, kuruluşunuzda Exchange Online kullanan istemci posta kutularının yavaş olduğundan şikayet eden kişilerden de arama alabilirsiniz. Bu durumda, Exchange Online performansınızın Hizmet sorunlarının kurbanı olduğunu varsaymak mantıklıdır.
  
![Exchange hariç tüm iş yüklerinin yeşil gösterildiği ve Hizmetin Geri Yüklendiği'ni gösteren Office 365 Sistem Durumu panosu.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
Bu noktada, Office 365 yöneticisi olarak sistem bakımı hakkında güncel bilgiler edinmek için **Geçerli sistem durumunu** denetlemeniz **ve ardından Ayrıntıları ve geçmişi görüntüle** seçeneğini sık sık denetlemeniz gerekir. **Geçerli sistem durumu** panosu, hizmetteki değişiklikler ve sorunlar hakkında sizi güncelleştirmek için yapılmıştır. Sistem durumu geçmişine, yöneticiden yöneticiye yazılan notlar ve açıklamalar, ölçmenize ve devam eden çalışmalar hakkında sizi haberdar etmeye yardımcı olur.
  
![Exchange Online hizmetinin geri yüklendiğini ve nedenini açıklayan Office 365 sistem durumu panosunun resmi.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Olaylar performansın yavaşlamasına neden olabilse de performans sorunu bir hizmet olayı değildir. Performans sorunu şöyle görünür:
  
- Yönetim merkezi **Geçerli sistem** durumu hizmet için ne bildirse de bir performans sorunu oluşur.
    
-  Akışı yapılan bir davranışın tamamlanması uzun sürüyor veya hiçbir zaman tamamlanamadı.
    
- Sorunu da çoğaltabilirsiniz veya doğru adım dizisini yaparsanız bunun gerçekleşeceğini bilirsiniz.
    
-  Sorun aralıklıysa, yine de bir desen olabilir. Örneğin, saat 10:00'a kadar Office 365 her zaman erişemeyen kullanıcılardan aramalar yapacağınızı biliyorsunuz. Aramalar öğlen saatlerine kadar sona erecek.
    
Bu liste muhtemelen tanıdık geliyordur; belki de çok tanıdık. Bunun bir performans sorunu olduğunu fark ettikten sonra soru şu olur: "Bundan sonra ne yapacaksınız?" Bu makalenin geri kalanı tam olarak bunu belirlemenize yardımcı olur.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Performans sorununu tanımlama ve test etme

Performans sorunları genellikle zaman içinde ortaya çıkar, bu nedenle gerçek sorunu tanımlamak zor olabilir. Sorun bağlamı hakkında iyi bir fikirle iyi bir sorun deyimi oluşturun ve ardından tekrarlanabilir test adımları uygulamanız gerekir. Yeterli bilgi sağlamayan sorun deyimlerine bazı örnekler aşağıda verilmiştir:
  
- Gelen Kutumdan Takvimime geçmek eskiden fark etmediğim bir şeydi ve şimdi kahve molası oldu. Eskiden olduğu gibi davranmasını sağlayabilir misin?
    
- Dosyalarımı SharePoint Online'a yüklemek sonsuza kadar sürüyor. Neden öğleden sonra yavaş oluyor ama başka bir zaman hızlı oluyor? Hızlı olamaz mı?
    
Yukarıdaki sorun ifadelerinin neden olduğu birçok büyük zorluk vardır. Özellikle, ilgilenemeyecek kadar çok belirsizlik var. Örneğin:
  
- Dizüstü bilgisayarda hareket etmek için Gelen Kutusu ve Takvim arasında nasıl geçiş yapılır belirsizdir.
    
- Kullanıcı "Hızlı olamaz mı" dediğinde, "hızlı" nedir?
    
- "Sonsuza dek" ne kadar sürer? Birkaç saniye mi? Ya da birkaç dakika? Ya da kullanıcı öğle yemeğine çıkabilir ve eylem geri döndükten 10 dakika sonra tamamlanabilir mi?
    
Yönetici ve sorun giderici, aşağıdaki gibi genel *deyimlerden sorunun ayrıntılarının* farkında olamaz. Örneğin, sorunun ne zaman başladığını bilmezler. Sorun giderici, kullanıcının evden çalıştığını bilmiyor olabilir ve yalnızca ev ağında yavaş geçiş görüyor olabilir. Veya kullanıcının yerel istemcide yoğun RAM kullanan diğer uygulamaları çalıştırması. Yöneticiler kullanıcının eski bir işletim sistemi çalıştırdığını bilmiyor veya son güncelleştirmeleri çalıştırmamış olabilir.
  
Kullanıcılar bir performans sorunu bildirdiğinde toplayacak çok fazla bilgi vardır. Bilgileri alma ve kaydetme, sorunun kapsamını belirleme olarak adlandırılır. Performans sorunları hakkında bilgi toplamak için kullanabileceğiniz temel bir kapsam listesi aşağıdadır. Bu liste kapsamlı değildir, ancak başlamak için bir yerdir:
  
- Sorun hangi tarihte ve günün veya gecenin hangi saatinde meydana geldi?
    
- Ne tür bir istemci bilgisayar kullanıyordunuz ve iş ağına (VPN, Kablolu, Kablosuz) nasıl bağlanır?
    
- Uzaktan mı çalışıyordunuz yoksa ofiste miydiniz?
    
- Aynı eylemleri başka bir bilgisayarda denediniz ve aynı davranışı gördünüz mü?
    
- Gerçekleştirdiğiniz eylemleri yazabilmeniz için size sorun veren adımları izleyin.
    
- Performans saniye veya dakika cinsinden ne kadar yavaş?
    
- Dünyanın neresindesin?
    
Bu soruların bazıları diğerlerinden daha belirgindir. Çoğu kullanıcı sorun gidericinin sorunu yeniden oluşturmak için tam adımlara ihtiyacı olduğunu anlar. Sonuçta, sorunun ne olduğunu başka nasıl kaydedebilirsiniz ve sorunun düzeltilip gidermediğini başka nasıl test edebilirsiniz? "Sorunu hangi tarih ve saatle gördünüz?" ve "Dünyanın neresinde bulunuyorsunuz?", birlikte kullanılabilecek bilgiler gibi şeyler daha az açıktır. Kullanıcının ne zaman çalıştığına bağlı olarak, birkaç saatlik zaman farkı, şirketinizin ağının bazı bölümlerinde bakımın zaten devam ettiği anlamına gelebilir. Örneğin, şirketinizin hem SharePoint Online hem de Şirket İçi SharePoint Server 2013 örneğindeki arama dizinlerini sorgulayan karma SharePoint Arama gibi karma bir uygulaması vardır; güncelleştirmeler şirket içi grubunda devam ediyor olabilir. Şirketinizin tamamı buluttaysa, sistem bakımı ağ donanımı eklemeyi veya kaldırmayı, şirket genelinde güncelleştirmeleri dağıtmayı ya da DNS'de veya diğer temel altyapıda değişiklik yapmayı içerebilir.
  
Bir performans sorununu giderirken, bu biraz olay yeri gibidir, kanıttan herhangi bir sonuç elde etmek için hassas ve dikkatli olmanız gerekir. Bunu yapmak için kanıt toplayarak iyi bir sorun bildirimi almanız gerekir. Bilgisayarın bağlamını, kullanıcının bağlamını, sorunun ne zaman başladığını ve performans sorununu ortaya çıkarmış tam adımları içermelidir. Bu sorun deyimi notlarınızdaki en üstteki sayfa olmalıdır ve kalmalıdır. Çözüm üzerinde çalıştıktan sonra sorun bildiriminde yeniden gezinerek, gerçekleştirdiğiniz eylemlerin sorunu çözmüş olup olmadığını test etmek ve kanıtlamak için adımları atmış olursunuz. Bu, işinizin ne zaman yapıldığını bilmek için kritik öneme sahiptir.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Performans iyiyken nasıl görünürdü biliyor musun?

Eğer şanssızsan, kimse bilmiyor. Kimsenin numarası yoktu. Başka bir deyişle, hiç kimse "Office 365'da Bir Gelen Kutusu'nu getirmek için kaç saniye sürdüğünü?" veya "Yöneticiler Lync Online toplantısı yaparken ne kadar süre geçti?" sorusunu yanıtlayamıyor. Bu, birçok şirket için yaygın bir senaryodur.
  
Performans temeli burada eksik mi?
  
Temeller, performansınız için bir bağlam sağlar. Şirketinizin gereksinimlerine bağlı olarak zaman zaman taban çizgisini sık sık almalısınız. Daha büyük bir şirketseniz, Operasyon ekibiniz şirket içi ortamınız için temelleri zaten alabilir. Örneğin, ayın ilk Pazartesi günü tüm Exchange sunucularına ve üçüncü Pazartesi günü tüm SharePoint sunucularınıza düzeltme eki uygularsanız, Operasyon ekibinizin büyük olasılıkla kritik işlevlerin çalışır durumda olduğunu kanıtlamak için düzeltme eki uygulama sonrasında çalıştırdığı görevlerin ve senaryoların bir listesi vardır. Örneğin, Gelen Kutusu'nu açmak, Gönder/Al'a tıklamak ve klasörlerin güncelleştirilmesini sağlamak veya SharePoint, sitenin ana sayfasına göz atmak, kurumsal Arama sayfasına gitmek ve sonuçları döndüren bir arama yapmak.
  
Uygulamalarınız Office 365 ise, en temel taban çizgilerinden bazıları ağınızdaki bir istemci bilgisayardan, çıkış noktasına veya ağınızdan ayrılıp Office 365 çıktığınız noktaya kadar geçen süreyi (milisaniye cinsinden) ölçebilirsiniz. Araştırabileceğiniz ve kaydedebileceğiniz bazı yararlı temeller şunlardır:
  
- İstemci bilgisayarınızla çıkış noktanız (örneğin, ara sunucunuz) arasındaki cihazları tanımlayın.
    
  - Ortaya çıkan performans sorunları için bağlamınız (IP adresleri, cihaz türü ve cetera) olması için cihazlarınızı bilmeniz gerekir.
    
  - Proxy sunucuları yaygın çıkış noktalarıdır, bu nedenle web tarayıcınızın hangi ara sunucuyu kullanacak şekilde ayarlandığını (varsa) kontrol edebilirsiniz.
    
  - Ağınızı keşfedip eşleyebilecek üçüncü taraf araçlar vardır, ancak cihazlarınızı öğrenmenin en güvenli yolu ağ ekibinizin bir üyesine sormaktır.
    
- İnternet servis sağlayıcınızı (ISS) tanımlayın, iletişim bilgilerini yazın ve kaç bağlantı hattına sahip olduğunuzu sorun.
    
- Şirketinizin içinde, istemcinizle çıkış noktası arasındaki cihazların kaynaklarını belirleyin veya ağ sorunları hakkında konuşmak için acil durum kişisini belirleyin.
    
Araçlarla basit testlerin sizin için hesaplayabileceğiniz bazı temeller şunlardır:
  
- İstemci bilgisayarınızdan çıkış noktanıza milisaniye cinsinden süre
    
- Çıkış noktanızdan milisaniye cinsinden Office 365 zaman
    
- Gözattığınızda Office 365 URL'lerini çözümleyen sunucu dünyasındaki konum
    
- ISS'nizin DNS çözümlemesinin milisaniye cinsinden hızı, paket gelişindeki tutarsızlıklar (ağ değişimi), karşıya yükleme ve indirme süreleri milisaniye cinsinden
    
Bu adımların nasıl gerçekleştirildiğini bilmiyorsanız, bu makalede daha ayrıntılı bilgi vereceğiz. 
  
## <a name="what-is-a-baseline"></a>Temel nedir?

Kötü gittiğinde etkisini anlarsınız, ancak geçmiş performans verilerinizi bilmiyorsanız, ne kadar kötü olabileceğine ve ne zaman kötüleşebileceğine ilişkin bir bağlam elde etmek mümkün değildir. Temel olmadan, bulmacayı çözmek için önemli ipucunu kaçırıyorsunuz: bulmaca kutusundaki resim. Performans sorunlarını gidermede bir  *karşılaştırma* noktasına ihtiyacınız vardır. Basit performans taban çizgilerini almak zor değildir. Operasyon ekibinize bunları belirli bir zamanlamaya göre yürütmekle görev yapılabilir. Örneğin, bağlantınızın şöyle göründüğünü düşünelim: 
  
![İstemci, ara sunucu ve Office 365 bulutu gösteren temel ağ grafiği.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Bu, ağ ekibinize danıştığınız ve şirketinizden bir ara sunucu aracılığıyla İnternet'e ayrıldığınızı ve bu proxy'nin istemci bilgisayarınızın buluta gönderdiği tüm istekleri işlediğini öğrendiğiniz anlamına gelir. Bu durumda, bağlantınızın tüm aradaki cihazları listeleyen basitleştirilmiş bir sürümünü çizmeniz gerekir. Şimdi istemci, çıkış noktası (İnternet için ağınızı bıraktığınız yer) ve Office 365 bulut arasındaki performansı test etmek için kullanabileceğiniz araçlar ekleyin.
  
![İstemci, ara sunucu ve bulut ile temel ağ ve PSPing, TraceTCP ve ağ izlemeleri için araç önerileri.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Seçenekler, performans verilerini bulmak için ihtiyacınız olan uzmanlık miktarı nedeniyle **Basit** ve **Gelişmiş** olarak listelenir. Bir ağ izlemesi, PsPing ve TraceTCP gibi komut satırı araçlarını çalıştırmaya kıyasla çok zaman alır. Bu iki komut satırı aracı, Office 365 tarafından engellenecek ICMP paketlerini kullanmadığından ve istemci bilgisayardan veya proxy sunucusundan (erişiminiz varsa) ayrılıp Office 365 ulaşması için gereken süreyi milisaniye cinsinden verdikleri için seçilmiştir. Bir bilgisayardan diğerine her bir atlama bir zaman değeriyle sonuçlanır ve bu temeller için harikadır! Aynı şekilde, bu komut satırı araçları da komuta bir bağlantı noktası numarası eklemenize olanak tanır, çünkü Office 365 Güvenli Yuva Katmanı ve Aktarım Katmanı Güvenliği (SSL ve TLS) tarafından kullanılan bağlantı noktası olan 443 numaralı bağlantı noktası üzerinden iletişim kurar. Ancak, diğer üçüncü taraf araçları sizin durumunuz için daha iyi çözümler olabilir. Microsoft bu araçların tümünü desteklemez, bu nedenle herhangi bir nedenle PsPing ve TraceTCP'yi çalıştıramazsanız Netmon gibi bir araçla bir ağ izlemesine geçin. 
  
İş saatlerinin öncesinde, yeniden yoğun kullanım sırasında ve sonra da saatler sonra bir temel alabilirsiniz. Bu, sonunda aşağıdakine benzer bir klasör yapısına sahip olabileceğiniz anlamına gelir:
  
![Performans verilerinizi klasörler halinde düzenlemenin bir yolunu öneren grafik.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Ayrıca dosyalarınızı adlandırma kuralı da seçmelisiniz. İşte birkaç örnek:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Bunu yapmanın birçok farklı yolu vardır, ancak biçimi **\<dateTime\>\<what's happening in the test\>** kullanmak başlamak için iyi bir yerdir. Bu konuda dikkatli olmak, sorunları daha sonra gidermeye çalışırken çok yardımcı olacaktır. Daha sonra "8 Şubat'ta iki iz aldım, biri iyi performans gösterdi, biri kötü gösterdi, böylece bunları karşılaştırabiliriz" diyebilirsiniz. Bu, sorun giderme için yararlıdır. 
  
Geçmiş taban çizgilerinizi korumak için düzenli bir yönteme sahip olmanız gerekir. Bu örnekte, basit yöntemler üç komut satırı çıkışı üretti ve sonuçlar ekran görüntüsü olarak toplandı, ancak bunun yerine ağ yakalama dosyalarınız olabilir. Sizin için en uygun yöntemi kullanın. Geçmiş taban çizgilerinizi depolayın ve çevrimiçi hizmetler davranışında değişiklikler fark ettiğiniz noktalarda bunlara başvurun. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Pilot sırasında neden performans verileri toplanır?

Temelleri oluşturmak için Office 365 hizmetinin pilot aşamasından daha iyi bir zaman yoktur. Ofisinizde binlerce kullanıcı, yüz binlerce veya beş kullanıcı olabilir, ancak birkaç kullanıcıyla bile performans dalgalanmalarını ölçmek için testler yapabilirsiniz. Büyük bir şirket söz konusu olduğunda, Office 365 pilot çalışması Office 365 birkaç yüz kullanıcıdan oluşan temsili bir örnek, sorunların ortaya çıkmadan önce nerede ortaya çıkabileceğini bilmeniz için birkaç bin kullanıcıya yansıtılabilir.
  
Küçük bir şirket söz konusu olduğunda, tüm kullanıcıların aynı anda hizmete gittiği ve pilot çalışma olmadığı küçük bir şirket söz konusu olduğunda, kötü performans gösteren bir işlemle ilgili sorunları gidermesi gerekebilecek herkese gösterilecek verileriniz olması için performans önlemlerini koruyun. Örneğin, aniden binanızda gezinebileceğinizi fark ederseniz, önceden hızlı bir şekilde gerçekleşen orta ölçekli bir grafiği karşıya yüklemek için gereken sürede gezinebilirsiniz.
  
## <a name="how-to-collect-baselines"></a>Temelleri toplama

Tüm sorun giderme planları için en azından bunları tanımlamanız gerekir:
  
- Kullandığınız istemci bilgisayar (bilgisayar veya cihaz türü, IP adresi ve soruna neden olan eylemler)
    
- İstemci bilgisayarın dünyanın neresinde bulunduğu (örneğin, bu kullanıcının ağa yönelik bir VPN'de, uzaktan veya şirket intranetinde çalışıp çalışmadığı)
    
- İstemci bilgisayarın ağınızdan kullandığı çıkış noktası (trafiğin bir ISS veya İnternet için işletmenizden ayrıldığı nokta)
    
 Ağınızın düzenini ağ yöneticisinden öğrenebilirsiniz. Küçük bir ağdaysanız sizi İnternet'e bağlayan cihazlara göz atın ve düzen hakkında sorularınız varsa ISS'nizi arayın. Başvurunuz için son düzenin grafiğini oluşturun. 
  
Bu bölüm, basit komut satırı araçlarına ve yöntemlerine ve daha gelişmiş araç seçeneklerine ayrılmıştır. Önce basit yöntemleri ele alacağız. Ancak şu anda bir performans sorununuz varsa gelişmiş yöntemlere atlayıp örnek performans sorunlarını giderme eylem planını denemeniz gerekir.
  
### <a name="simple-methods"></a>Basit yöntemler

Bu basit yöntemlerin amacı, Office 365 performansı hakkında bilgi sahibi olmanız için zaman içinde basit performans taban çizgilerini almayı, anlamayı ve uygun şekilde depolamayı öğrenmektir. Aşağıda daha önce gördüğünüz gibi basit bir diyagram bulabilirsiniz:
  
![İstemci, ara sunucu ve bulut ile temel ağ ve PSPing, TraceTCP ve ağ izlemeleri için araç önerileri.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> Bir isteğin işlenmesinin ne kadar sürdüğünü ve isteğin hedefe ulaşması için gereken ağ atlamaları veya bir bilgisayardan diğerine kaç bağlantı olduğunu milisaniye cinsinden göstermek için kullanışlı bir araç olduğundan TraceTCP bu ekran görüntüsüne eklenir. TraceTCP, atlamalar sırasında kullanılan sunucuların adlarını da verebilir ve bu da Destek'teki bir Microsoft Office 365 sorun gidericisi için yararlı olabilir. > TraceTCP komutları çok basit olabilir, örneğin: >  `tracetcp.exe outlook.office365.com:443`> Komuta bağlantı noktası numarasını eklemeyi unutmayın! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) ücretsiz bir indirmedir ancak Wincap'e dayanır. Wincap, Netmon tarafından da kullanılan ve yüklenen bir araçtır. Ayrıca gelişmiş yöntemler bölümünde Netmon kullanıyoruz. 
  
 Birden çok ofisiniz varsa, bu konumların her birinde bir istemciden veri kümesi saklamanız gerekir. Bu test gecikme süresini ölçer. Bu durumda, bir istemcinin Office 365 istek göndermesi ile isteği yanıtlaması arasındaki süreyi açıklayan Office 365 bir sayı değeridir. Test, bir istemci bilgisayarda etki alanınızın içinden kaynaklanır ve ağınızın içinden, çıkış noktası üzerinden, İnternet üzerinden Office 365 ve geriye doğru gidiş dönüşlü bir gidiş dönüş ölçmeyi arar. 
  
Çıkış noktasıyla( bu örnekte ara sunucu) ilgilenmenin birkaç yolu vardır. 1'den 2'ye ve sonra 2'den 3'e kadar izleyebilir ve ardından ağınızın kenarına son toplamı almak için sayıları milisaniye cinsinden ekleyebilirsiniz. Ya da bağlantıyı, Office 365 adresleri için ara sunucuyu atlayacak şekilde yapılandırabilirsiniz. Güvenlik duvarı, ters ara sunucu veya ikisinin bir birleşimine sahip daha büyük bir ağda, ara sunucuda trafiğin çok sayıda URL için geçmesine izin verecek özel durumlar yapmanız gerekebilir. Office 365 tarafından kullanılan uç noktaların listesi için bkz. [URL'leri ve IP adresi aralıklarını Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Kimlik doğrulama ara sunucunuz varsa, aşağıdakiler için özel durumları test ederek başlayın:
  
- 80 ve 443 bağlantı noktaları
    
- TCP ve HTTP'ler
    
- Bu URL'lerden herhangi birine giden bağlantılar:
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Tüm kullanıcıların herhangi bir ara sunucu girişimi veya kimlik doğrulaması olmadan bu adreslere girmesine izin verilmelidir. Daha küçük bir ağda, bunları web tarayıcınızda ara sunucu atlama listenize eklemelisiniz. 
  
Bunları Internet Explorer'daki proxy atlama listenize eklemek için **Araçlar** \> **İnternet Seçenekleri** \> **Bağlantıları** \> **LAN ayarları** \> **Gelişmiş'e** gidin. Gelişmiş sekmesi, proxy sunucunuzu ve proxy sunucu bağlantı noktanızı da bulacağınız yerdir. **Gelişmiş** düğmesine erişmek **için LAN'ınız için ara sunucu kullan** onay kutusuna tıklamanız gerekebilir. **Yerel adresler için proxy sunucusunu atla** seçeneğinin işaretli olduğundan emin olmak istersiniz. **Gelişmiş'e** tıkladığınızda, özel durumlar girebileceğiniz bir metin kutusu görürsünüz. Yukarıda listelenen joker karakter URL'lerini noktalı virgüllerle ayırın, örneğin:
  
\*.microsoftonline.com; \*.sharepoint.com
  
Proxy'nizi atladıktan sonra ping veya PsPing'i doğrudan bir Office 365 URL'sinde kullanabilmeniz gerekir. Sonraki adım ping **outlook.office365.com** test etmek olacaktır. Veya PsPing veya komuta bağlantı noktası numarası sağlamanıza olanak sağlayacak başka bir araç kullanıyorsanız, milisaniye cinsinden ortalama gidiş dönüş süresini görmek için **portal.microsoftonline.com:443** karşı PsPing. 
  
Gidiş dönüş süresi veya RTT, outlook.office365.com gibi bir sunucuya HTTP isteği göndermenin ne kadar sürdüğünü ölçen ve sunucunun bunu yaptığını bildiğini kabul eden bir yanıt alan bir sayı değeridir. Bazen bunun RTT olarak kısaltılmış olduğunu görürsünüz. Bu, nispeten kısa bir süre olmalıdır.
  
Bu testi yapmak için [PSPing'i](/sysinternals/downloads/psping) veya Office 365 tarafından engellenen ICMP paketlerini kullanmayan başka bir aracı kullanmanız gerekir. 
  
 **Doğrudan bir Office 365 URL'sinden milisaniye cinsinden genel gidiş dönüş süresi almak için PsPing'i kullanma**
  
1. Şu adımları tamamlayarak yükseltilmiş bir komut istemi çalıştırın:
    
1. **Başlat**'a tıklayın.
    
2. **Aramayı Başlat** kutusuna cmd yazın ve CTRL+SHIFT+ENTER tuşlarına basın.
    
3. **Kullanıcı Hesabı Denetimi** iletişim kutusu görüntülenirse, görüntülenen eylemin istediğiniz eylem olduğunu onaylayın ve **ardından Devam'a** tıklayın.
    
2. Aracın (bu örnekte PsPing) yüklü olduğu klasöre gidin ve şu Office 365 URL'leri test edin:
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![PSPing komutu 443 numaralı bağlantı noktasını microsoft-my.sharepoint.com.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
443 bağlantı noktası numarasını eklediğinizden emin olun. Office 365 şifrelenmiş bir kanalda çalıştığını unutmayın. Bağlantı noktası numarası olmadan PsPing yaparsanız isteğiniz başarısız olur. Kısa listenize ping işlemi yaptıktan sonra Milisaniye (ms) cinsinden Ortalama süre'yi arayın. Kaydetmek istediğiniz şey bu!
  
![2,8 milisaniyelik gidiş dönüş süresiyle PSPing'e proxy uygulama istemcisini gösteren grafik.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Ara sunucu atlama hakkında bilginiz yoksa ve her şeyi adım adım gerçekleştirmeyi tercih ediyorsanız, önce ara sunucunuzun adını öğrenmeniz gerekir. Internet Explorer'da **Araçlar** \> **İnternet Seçenekleri** \> **Bağlantıları** \> **LAN ayarları** \> **Gelişmiş'e** gidin. **Gelişmiş** sekmesi, proxy sunucunuzun listelendiğini göreceğiniz yerdir. Bu görevi tamamlayarak bir komut isteminde ara sunucuya ping gönderin: 
  
 **Proxy sunucusuna ping göndermek ve 1- 2. aşama için milisaniye cinsinden gidiş dönüş değeri almak için**
  
1. Şu adımları tamamlayarak yükseltilmiş bir komut istemi çalıştırın:
    
1. **Başlat**'a tıklayın.
    
2. **Aramayı Başlat** kutusuna cmd yazın ve CTRL+SHIFT+ENTER tuşlarına basın.
    
3. **Kullanıcı Hesabı Denetimi** iletişim kutusu görüntülenirse, görüntülenen eylemin istediğiniz eylem olduğunu onaylayın ve **ardından Devam'a** tıklayın.
    
2. ping yazıp \<the name of the proxy server your browser uses, or the IP address of the proxy server\> ENTER tuşuna basın. PsPing veya başka bir araç yüklüyse, bunun yerine bu aracı kullanmayı seçebilirsiniz. 
    
    Komutunuz şu örneklerden herhangi biri gibi görünebilir: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. İzleme test paketleri göndermeyi durdurduğunda, milisaniye cinsinden ortalamayı listeleyen küçük bir özet alırsınız ve bu, peşinde olduğunuz değerdir. komut isteminin ekran görüntüsünü alın ve adlandırma kuralınızı kullanarak kaydedin. Bu noktada, diyagramı değerle doldurmaya da yardımcı olabilir.
    
Belki sabahın erken saatlerinde bir izleme almış olabilirsiniz ve istemciniz ara sunucuya (veya İnternet'e çıkan çıkış sunucusuna) hızlı bir şekilde ulaşabilir. Bu durumda, numaralarınız aşağıdaki gibi görünebilir:
  
![İstemciden 2,8 milisaniyelik ara sunucuya gidiş dönüş süresini gösteren grafik.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
İstemci bilgisayarınız ara sunucu (veya çıkış) sunucusuna erişimi olan birkaç seçimden biriyse, bu bilgisayara uzaktan bağlanarak, buradan bir Office 365 URL'sine PsPing komut istemini çalıştırarak testin bir sonraki ayağını çalıştırabilirsiniz. Bu bilgisayara erişiminiz yoksa, bir sonraki adımla ilgili yardım almak için ağ kaynaklarınıza başvurabilir ve tam sayıları bu şekilde alabilirsiniz. Bu mümkün değilse, söz konusu Office 365 URL'sine karşı bir PsPing alın ve proxy sunucunuza karşı PsPing veya Ping zamanı ile karşılaştırın. 
  
Örneğin, istemciden Office 365 URL'sine 51,84 milisaniyeniz varsa ve istemciden ara sunucuya (veya çıkış noktasına) 2,8 milisaniyeniz varsa, çıkıştan Office 365 49,04 milisaniyeye sahip olursunuz. Benzer şekilde, günün yüksekliği boyunca istemciden ara sunucuya 12,25 milisaniye ve istemciden Office 365 URL'ye 62,01 milisaniye PsPing'iniz varsa, Office 365 URL'sine proxy çıkışı için ortalama değeriniz 49,76 milisaniyedir.
  
![Değerlerin çıkarılabilmesi için istemciden ara sunucuya istemciden Office 365'a kadar milisaniye cinsinden ping'i gösteren ek grafik.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Sorun giderme açısından, yalnızca bu taban çizgilerini korumaktan ilginç bir şey bulabilirsiniz. Örneğin, ara sunucu veya çıkış noktasından Office 365 URL'sine kadar genellikle yaklaşık 40 milisaniye ile 59 milisaniye arasında gecikme süresine sahip olduğunuzu fark ederseniz, ve yaklaşık 3 milisaniye ile 7 milisaniye (günün bu saatinde gördüğünüz ağ trafiği miktarına bağlı olarak) ara sunucu veya çıkış noktası gecikme süresine sahip bir istemciniz varsa, ara sunucuya veya çıkış taban çizgilerine son üç istemciniz gösteriliyorsa mutlaka bir sorun olduğunu anlarsınız 45 milisaniyelik bir gecikme süresi.
  
### <a name="advanced-methods"></a>Gelişmiş yöntemler

Office 365 için İnternet isteklerinizde neler olduğunu gerçekten öğrenmek istiyorsanız, ağ izlemeleri hakkında bilgi sahibi olmanız gerekir. Bu izlemeler için hangi araçları tercih ettiğiniz fark etmez; HTTPWatch, Netmon, İleti Çözümleyicisi, Wireshark, Fiddler, Geliştirici Panosu aracı veya diğer araçlar ağ trafiğini yakalayıp filtreleyebilir. Bu bölümde, sorunun daha eksiksiz bir resmini elde etmek için bu araçlardan birden fazlasını çalıştırmanın yararlı olduğunu göreceksiniz. Test ederken, bu araçlardan bazıları kendi başına proxy görevi de görür. Office 365 [için performans sorun giderme planı](performance-troubleshooting-plan.md) başlıklı yardımcı makalede kullanılan araçlar [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) veya [WireShark'ı](https://www.wireshark.org/) içerir.
  
Performans temeli almak bu yöntemin basit bir parçasıdır ve adımların çoğu, bir performans sorununu giderme işlemiyle aynıdır. Performans için temel oluşturmanın daha gelişmiş yöntemleri, ağ izlemelerini alıp depolamanızı gerektirir. Bu makaledeki örneklerin çoğu SharePoint Online'ı kullanır, ancak test etmek ve kaydetmek için abone olduğunuz Office 365 hizmetlerindeki yaygın eylemlerin bir listesini geliştirmeniz gerekir. Aşağıda bir temel örnek verilmiştir:
  
- SPO için temel liste - ** 1. Adım: ** SPO web sitesinin giriş sayfasına göz atın ve bir ağ izlemesi yapın. İzlemeyi kaydedin. 
    
- SPO için temel liste - **2. Adım:** Enterprise Ara ve ağ izlemesi yaparak terim (şirketinizin adı gibi) arayın. İzlemeyi kaydedin. 
    
- SPO için temel liste - **3. Adım:** Büyük bir dosyayı SharePoint Çevrimiçi belge kitaplığına Upload ve ağ izlemesi yapın. İzlemeyi kaydedin. 
    
- SPO için temel liste - **4. Adım:** OneDrive web sitesinin giriş sayfasına göz atın ve bir ağ izlemesi yapın. İzlemeyi kaydedin. 
    
Bu liste, kullanıcıların SharePoint Online'a karşı gerçekleştirebilecekleri en önemli yaygın eylemleri içermelidir. OneDrive İş giden izlemenin son adımının, SharePoint Online giriş sayfasının yükü (genellikle şirketler tarafından özelleştirilir) ile nadiren özelleştirilen OneDrive İş giriş sayfası arasında bir karşılaştırma oluşturduğuna dikkat edin. Yavaş yüklenen SharePoint Online sitesine gelince bu temel bir testtir. Testinizde bu farkın kaydını oluşturabilirsiniz.
  
Bir performans sorununun ortasındaysanız, adımların çoğu temel alma işlemiyle aynıdır. Ağ izlemeleri kritik hale gelir, bu nedenle sonraki önemli izlemeleri  *nasıl*  alacağımıza bakacağız. 
  
Bir performans sorununu çözmek için,  *şu anda* performans sorununu yaşadığınız sırada bir izleme almanız gerekir. Günlükleri toplamak için uygun araçlara sahip olmanız ve bir eylem planına, yani mümkün olan en iyi bilgileri toplamak için gerçekleştirebileceğiniz sorun giderme eylemlerinin listesine ihtiyacınız vardır. Yapılacak ilk şey, dosyaların zamanlamayı yansıtan bir klasöre kaydedilebilmesi için testin tarih ve saatini kaydetmektir. Ardından, sorun adımlarını daraltın. Bunlar test için kullanacağınız tam adımlardır. Temel bilgileri unutmayın: Sorun yalnızca Outlook ile ilgiliyse, sorun davranışının yalnızca bir Office 365 hizmetinde oluştuğundan emin olun. Bu sorunun kapsamını daraltmak, çözebileceğiniz bir şeye odaklanmanıza yardımcı olur. 
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)