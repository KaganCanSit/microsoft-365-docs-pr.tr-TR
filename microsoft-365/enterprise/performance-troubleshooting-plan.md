---
title: Destek için performans sorunlarını giderme Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
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
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: Bu makale, performans sorunlarını Office 365 gidermenize ve hatta en yaygın sorunlardan bazılarını düzeltmenize yardımcı olabilir.
ms.openlocfilehash: 23779158c250a94873f44139faa783e0079ab642
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988728"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Destek için performans sorunlarını giderme Office 365

SharePoint Online, OneDrive İş, Exchange Online veya Skype Kurumsal Online ile istemci bilgisayarınız arasındaki gecikmeleri, askıda kalmaları ve düşük performansı belirlemeye yönelik adımları biliyor musunuz? Desteği aramadan önce, bu makale Office 365 sorunları gidermenize, hatta en yaygın sorunlardan bazılarını çözmenize yardımcı olabilir.

Bu makale aslında, performans sorun yaşanıyorken bu sorunla ilgili değerli veriler yakalamak için kullanabileceğiniz örnek bir eylem planıdır. Bu makalede en önemli bazı sorunlar da yer almaktadır.

Ağ performansında yeniyseniz ve istemci makineleriniz ile Office 365 arasındaki performansı izlemek için uzun vadeli bir plan yapmak için, Office 365 performans ayarlama ve sorun giderme [- Yönetici](performance-tuning-using-baselines-and-history.md) ve PRO.

## <a name="sample-performance-troubleshooting-action-plan"></a>Örnek performans sorunlarını giderme eylem planı

Bu eylem planı iki parçadan oluşur; bir hazırlık aşaması ve bir de günlüğe kaydetme aşaması. Şu anda bir performans sorunun varsa ve veri toplamanız gerekirse, hemen bu planı kullanmaya başlayabilirsiniz.

### <a name="prepare-the-client-computer"></a>İstemci bilgisayarı hazırlama

- Performans sorununu yeniden üretebilir bir istemci bilgisayar bulun. Bu bilgisayar sorun giderme sırasında kullanılır.
- Performans sorununa neden olan adımları not edin, böylece test zamanı geldiğinde hazır oluruz.
- Bilgileri toplamak ve kaydını oluşturmak için araçları yükleyin:
  - [Netmon 3.4'ü yükleyin](https://www.microsoft.com/download/details.aspx?id=4865) (veya eşdeğer bir ağ izleme aracı kullanın).
  - HTTPWatch'ın ücretsiz Basic [Edition'ı yükleyin](https://www.httpwatch.com/download/) (veya eşdeğer bir ağ izleme aracı kullanın).
  - Test sırasında atılacak adımların kaydını tutmak için bir ekran kaydedici kullanın veya Windows Vista ve sonraki sürümlerle birlikte gelen Adım Kaydedicisi (PSR.exe) kaydedicisini çalıştırın.

### <a name="log-the-performance-issue"></a>Performans sorunu günlüğe kaydedilir

- Tüm fazla kullanılan İnternet tarayıcılarını kapatın.
- Adım Kaydedicisi'ne veya başka bir ekran kaydediciyi başlatma.
- Netmon yakalamanızı (veya ağ izleme aracını) başlatma.
- İstemci bilgisayarda komut satırlarından ipconfig flushdns yazarak DNS önbelleğinizi temizleyin.
- Yeni bir tarayıcı oturumu başlatarak HTTPWatch'i açın.
- İsteğe bağlı: Exchange Online test ediyorsanız, Exchange Performans Çözümleyicisi aracını yönetici Office 365 çalıştırın.
- Performans sorununa neden olan tam adımları yeniden üretin.
- Netmon veya başka bir aracın izlemesini durdurun.
- Komut satırına bir izleme yolu çalıştırarak Office 365 komutunu yazın ve ENTER tuşuna basın:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Adım Kaydedicisi'i durdurun ve videoyu kaydedin. Yakalama tarih ve saatlerini ve iyi veya kötü performans gösterdiğine emin olun.
- İzleme dosyalarını kaydedin. Yine, yakalama tarih ve saatlerini ve iyi veya kötü performans gösterdiğine de emin olun.

Bu makalede sözü geçen araçları çalıştırmaya alışık değilsanız, merak etmeyin, bir sonraki adımda bu adımlar sağlanmıştır. Bu tür ağ yakalama çalışmalara alışkınsanız, günlükleri filtreleme ve okumanın açık olduğu Temel toplama'ya geçebilirsiniz.[](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)

### <a name="flush-the-dns-cache-first"></a>Önce DNS Önbelleğini temizleyin

Neden mi? DNS önbelleğini temizerek, testlerinizi temiz bir sayfayla başlatıyor oluruz. Önbelleği temizlayarak, DNS çözümleyici içeriğini en güncel girdilere sıfırlarsiniz. Temizlemenin, ANTS dosya girdilerini kaldırma olmadığını unutmayın. HOST dosyası girdilerini yoğun olarak kullanıyorsanız, bu girdileri başka bir dizindeki bir dosyaya kopyalamanız ve sonra HOST dosyasını boşaltmanız gerekir.

#### <a name="flush-your-dns-resolver-cache"></a>DNS çözümleyici önbelleğinizi temizleme

1. Komut istemini açın, (**Start** \> **Run** \> **cmd veya Windows**  \> **cmd**).
2. Aşağıdaki komutu yazın ve ENTER tuşuna basın:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsoft'un Ağ İzleme aracı ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) paketleri, yani ağlarda bilgisayarlar arasında geçen trafiği analiz eder. Office 365'la trafiği takip etmek için Netmon'ı kullanarak paket üst bilgilerini yakalamak, görüntülemek ve okumak, aradaki cihazları tanımlamak, ağ donanımının önemli ayarlarını kontrol etmek, bırakılan paketleri görmek ve şirket ağınız ile şirket ağınızdaki bilgisayarlar arasındaki trafiğin akışını Office 365. Trafiğin gerçek gövdesi şifrelenmiş olduğundan (yani SSL/TLS üzerinden bağlantı noktası 443 üzerinden seyahat olduğundan) gönderilen dosyaları okuyamabilirsiniz. Bunun yerine, paketin izlemesi gereken yolun filtrelenmemiş bir izlemesini alır ve bu da sorun davranışını takip etmeye yardımcı olabilir.

Şu anda filtre uygulamamayı lütfen. Bunun yerine, izleme ve kaydetmeyi durdurmadan önce adımların üzerinden geçerek sorunu gösterin.

Netmon 3.4'ü yükledikten sonra aracı açın ve şu adımları izleyin:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Netmon izlemesi alma ve sorunu yeniden oluşturma

1. Netmon 3.4'ü başlat.
Başlat sayfasında üç bölme **vardır: Son** Yakalamalar **, Ağları** Seçin ve **Microsoft Ağ İzleyicisi 3.4'ü Başlarken. Bildirim**. Ağları Seçin paneli, yakalamanız için uygun olan varsayılan ağların listesini de verir. Burada ağ kartlarının seçili olduğundan emin olun.

2. Başlangıç **sayfasının en** üstünde Yeni **Yakalama'ya** tıklayın. Böylece, Başlat sayfa sekmesinin yanına **Yakalama** **1 adında yeni bir sekme ekler**.
![Yeni Yakalama, Başlat ve Durdur düğmelerinin vurgulu olduğu Netmon kullanıcı arabirimi.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Basit bir yakalama almak için araç çubuğunda **Başlat'a** tıklayın.

4. Bir performans sorunu ortaya konu alan adımları yeniden üretin.

5. Dosyayı **Farklı** **Kaydet'i** \> \> **Durdur'a tıklayın**. Saat dilimiyle birlikte tarih ve saat vermeyi ve iyi performans mı yoksa kötü performans mı gösterdiğinden bahsetmeyi unutmayın.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) ücretli ve ücretsiz sürüm olarak gelir. Ücretsiz olan Basic Edition, bu test için ihtiyacınız olan her şeyi kapsar. HTTPWatch ağ trafiğini ve tarayıcı pencerenizin hemen üzerinden sayfa yükleme sürelerini izler. HTTPWatch, performansı grafik olarak tanımlayan bir Internet Explorer eklentisidir. Çözümleme HTTPWatch Studio'da kaydedilebilir ve  görüntüilebilir.

> [!NOTE]
> Firefox, Google Chrome gibi başka bir tarayıcı kullanıyorsanız veya Internet Explorer'da HTTPWatch yükleyeyebilirsiniz, yeni bir tarayıcı penceresi açın ve klavyenizde F12 tuşuna basın. Tarayıcınızın en altında Geliştirici Aracı açılır kutusunu görüyorsanız. Opera kullanıyorsanız, Web Inspector için CTRL+SHIFT+I tuşlarına basın, ardından Ağ sekmesine tıklayın ve aşağıda açıklanan testleri yapın. Bilgiler biraz farklı olur, ancak yükleme süreleri mili saniye cinsinden görüntülenir. > HTTPWatch, çevrimiçi çevrimiçi sayfa yükleme süreleriyle SharePoint sorunlar için de kullanışlıdır.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>HTTPWatch'i çalıştırma ve sorunu yeniden oluşturma

HTTPWatch bir tarayıcı eklentisidir, bu nedenle aracın tarayıcıda açık hali Internet Explorer'ın her sürümü için biraz farklıdır. Normalde, HTTPWatch'ı Internet Explorer tarayıcısında Komut çubuğunun altında bulabilirsiniz. Tarayıcı pencerenizin HTTPWatch eklentisını görmüyorsanız,  \> Yardım Hakkında'ya tıklayarak veya Internet Explorer'ın daha sonraki sürümlerinde dişli simgesine ve ardından **Internet Explorer** Hakkında'ya tıklayarak tarayıcınızın sürümünü kontrol edin. Komut çubuğunu **başlatmak için** Internet Explorer'da menü çubuğuna sağ tıklayın ve Komut çubuğu'ne **tıklayın**.

Geçmişte, HTTPWatch Komutlar ve Explorer çubuklarının her ikiyle de ilişkilendirildi, dolayısıyla yükledikten sonra simgeyi hemen görmüyorsanız (yeniden başlattıktan sonra bile), Araçlar'ı ve araç çubuklarınıza simgeyi kontrol edin. Araç çubuklarının özelleştirebileceğinizi ve bu araç çubuklarına seçenekler eklenebileceğinizi unutmayın.

![HTTPWatch simgesinin görüntülendiğinde Internet Explorer'ın Komut araç çubuğu.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. HTTPWatch'ı bir Internet Explorer tarayıcı penceresinde başlatın. Pencerenin en altında tarayıcıya yerleştirildi olarak görünür. **Kayıt'a tıklayın**.

2. Performans sorunuyla ilgili tam adımları yeniden üretin. **HTTPWatch'da** Durdur düğmesine tıklayın.

3. **HTTPWatch'ı** kaydedin veya **E-postaYla Gönder'i seçin**. Dosyayı, tarih ve saat bilgisi olacak şekilde ve İzlemenizin iyi veya kötü performans göstergesini içerdiğine ilişkin bir ad ve veri içerdiğini unutmayın.

![Giriş sayfasının Ağ sekmesini gösteren HTTPWatch Office 365.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Bu ekran görüntü httpwatch'un Professional sürümündendir. Temel Sürümde alınan izlemeleri, basit sürümü olan bir Professional açıp okuyabilirsiniz. Bu yöntemle alınan izlemeden ek bilgiler edinebilirsiniz.

## <a name="problem-steps-recorder"></a>Sorun Adımları Kaydedicisi

Adım Kaydedicisi veya PSR.exe, sorunları oluşurken kaydetmeye olanak sağlar. Bu çok yararlı bir araçtır ve çalıştırması çok basittir.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Çalışmanızı kaydetmek için Sorun Adımları Kaydedicisi PSR.exe'i (PSR.exe) çalıştırma

1. **Tamam'a** **tıklarsanız** \> \> **PSR.exe** \> **Çalıştır** türünü kullanın veya **Tamam'a Windows tuşuna** \> **PSR.exe** \> ENTER tuşuna basın.

2. Küçük ekran PSR.exe, Kaydı **Başlat'a tıklayın** ve performans sorunu yeniden üretin adımları yeniden üretin. Gerekirse, Açıklama Ekle'ye tıklayarak **açıklama abilirsiniz**.

3. Adımları **tamamlamışken** Kaydı Durdur'a tıklayın. Performans sorunu bir sayfa işlemede ise kaydı durdurmadan önce sayfanın işlemesi için bekleyin.

4. **Kaydet**'e tıklayın.

![Adım Kaydedicisi veya Kaydedicisi'nin ekran PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Tarih ve saat sizin için kaydedilir. Bu, PSR'nizi zamanında Netmon izlemenize ve HTTPWatch'a bağlar ve hassas sorun gidermede yardımcı olur. PSR kaydında tarih ve saat; örneğin, oturum açma ile URL'ye göz atma arasında bir dakika geçerek yönetici sitesinin kısmen iş günü olduğunu gösterebilir.

## <a name="read-your-traces"></a>İzlemelerinizi okuma

Ağ ve performans sorunlarını gidermeyle ilgili her şeyi bir makaleyle öğretmek mümkün değildir. İyi bir performans elde olmak için deneyim ve ağ bağlantılarının nasıl çalıştığını ve genelde performansının nasıl olduğunu öğrenebilirsiniz. Ancak, bir sık karşılaşılan sorunlar listesi oluşturmak ve araçların en yaygın sorunları ortadan kaldırmayı nasıl kolaylaştıracaklarını göstermek mümkündür.

Office 365 siteleriniz için ağ izlemelerini okuma becerileri almak için, düzenli olarak sayfa yükleme izlemeleri oluşturmak ve bunları okuma deneyimi kazanmaktan daha iyi bir öğretmen yoktur. Örneğin, fırsatın olduğunda, bir veri hizmeti Office 365 ve işlemi takip etme. DNS trafiğine yönelik izlemeye filtre uygulama veya FrameData'da göz atttıyır hizmetinin adını aratır. Hizmet yüklenirken oluşan adımlar hakkında bir fikir almak için izlemeyi tarayın. Bu normal sayfa yüklemelerinin nasıl bir görünüme sahip olması gerektiğini öğrenmenıza yardımcı olur ve sorun giderme durumunda, özellikle de performansla ilgili iyi ve kötü izleri karşılaştırmak size çok şey öğretebilir.

Netmon, Görüntü filtresi alanında Microsoft Intellisense kullanır. Intellisense veya akıllı kod tamamlama, bir nokta yazmanın ve kullanılabilir tüm seçeneklerin açılan seçim kutusunda görüntülenebilir olduğu bir püf noktasıdır. Örneğin TCP pencere ölçeklendirmesi hakkında endişe ediyorsanız, filtreye (  `.protocol.tcp.window < 100`örneğin) bu şekilde yolunu bulabilirsiniz.

![Görüntüleme Filtresi alanında intellisense'in kullandığını gösteren Netmon ekran görüntüsü.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Netmon izleri içinde çok fazla trafik olabilir. Bunları okumada deneyimli değilsanız, izlemenin ilk kez açılması sizi bunaltmış olabilir. Öncelikle izde sinyali arka plan gürültüsünden ayırmamız gerekir. Test Office 365 ve görmek istediğiniz trafik de bu. İzlerde gezinmeye alışıyorsanız, bu listeye ihtiyacınız olmayabilir.

İstemciniz ve müşteriniz Office 365 TLS üzerinden seyahat ediyor, bu da trafik gövdesinin şifrelenir ve genel bir Netmon izlemesinde okunamaz olduğu anlamına gelir. Performans çözümlemenizin pakette yer alan bilgilerin belirli bilgilerini bilmek zorunda değil. Bununla birlikte, paket üst bilgileri ve içeren bilgilerle çok ilgileniyor.

### <a name="tips-to-get-a-good-trace"></a>İpuçları bir iz almak için yardım

- İstemci bilgisayarınızın IPv4 veya IPv6 adresinin değerini bilebilirsiniz. Bunu, komut isteminde IPConfig yazarak ve ENTER **tuşuna** basarak elde edebilirsiniz. Bu adresi bilmek izteki trafiğin doğrudan istemci bilgisayarınızla ilgili olup olmadığını bir bakışta öğrenmenizi sağlar. Bilinen bir proxy varsa, ona da ping işlemi yapmak ve IP adresini almak.

- DNS çözümleyici önbelleğinizi temizleyin ve mümkünse, testleri çalıştıracak olan tarayıcı dışındaki tüm tarayıcıları kapatın. Bunu, örneğin destek, istemci bilgisayarınızın masaüstünü görmek için tarayıcı tabanlı bir araç kullanıyorsa izlemenizi filtrelemeye hazır olun.

- Meşgul izlemesinde, Office 365 hizmeti bulun. Daha önce trafiğinizi hiç ya da nadiren gören bu, performans sorununa diğer ağ gürültülerinden ayırmak için yararlı bir adımdır. Bunu birkaç şekilde yapabilirsiniz. Sınamadan hemen önce, _ping veya_ _PsPing'i_ belirli hizmetin URL'sinde (`ping outlook.office365.com` veya , örneğin) `psping -4 microsoft-my.sharepoint.com:443`kullanabilirsiniz. Ayrıca, ping veya PsPing'i bir Netmon izlemesinde (işlem adına göre) kolayca bulabilirsiniz. Bu, aramaya başlamana bir yer olur.

Netmon izlemesini yalnızca sorunun olduğu zaman kullanıyorsanız, bu da sorun değildir. Kendinizi yönlendirmek için veya gibi bir filtre `ContainsBin(FrameData, ASCII, "office")` kullanın `ContainsBin(FrameData, ASCII, "outlook")`. Çerçeve numaranızı izleme dosyasından kaydedebilirsiniz. Ayrıca Çerçeve Özeti bölmesini en _sağa kaydırarak_ Konuşma Kimliği sütununa bakmanız da iyi olabilir. Burada, bu belirli konuşmanın kimliği için gösterilen bir sayı vardır; bunu kaydedebilirsiniz ve daha sonra yalıtım altında bakabilirsiniz. Başka herhangi bir filtre uygulamadan önce bu filtreyi kaldırmayı unutmayın.

> [!TIP]
> Netmon'un yararlı birçok yerleşik filtresi vardır. Görüntü **filtresi bölmesinin** üst kısmında yer alan Filtre _Yükle düğmesini_ deneyin.

![İstemci bilgisayarın komut satırda PSPing komutunu kullanarak IP'nizi bulun.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![TCP filtresi aracılığıyla aynı PSPing komutunu gösteren istemciden Netmon izlemesi. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Trafiğinize aşinalık elde edin ve ihtiyacınız olan bilgileri bulmayı öğrenin. Örneğin, kullanmakta olduğu hizmet için ilk başvuruya izlemede hangi paketin Office 365 olduğunu belirlemeyi öğrenin ("Outlook").

Örnek Office 365 Outlook Çevrimiçi olarak ele alınarak, trafik aşağıdakine benzer şekilde başlar:

- Eşleşen QueryID'lerle eşleşen outlook.office365.com için DNS Standart Sorgusu ve DNS Yanıtı. Bu dönüş süresi için saat farksını ve ayrıca dünyanın en Office 365 DNS'in ad çözümleme isteği gönderdiğini not etmek önemlidir. İdeal olarak, dünyanın yarısını değil, mümkün olduğunca yerel olarak.

- Durum raporu Kalıcı Olarak Taşınmış olan bir HTTP GET İsteği (301)

- RWS istekleri ve yanıtlarını Bağlan RWS Bağlan. (Bu, sizin için bağlantı yapan Uzak Winsock'un bağlantısıdır.)

- Bir TCP SYN ve TCP SYN/CK görüşmesi. Bu konuşmanın birçok ayarı performansınızı etkiler.

- Sonra, TLS el sıkışması ve TLS sertifika görüşmeleri yapılan bir dizi TLS:TLS trafiği. (Verilerin SSL/TLS ile şifrelenmiş olduğunu unutmayın.)

Trafiğin tüm bölümleri önemli ve bağlantılıdır, ancak izlemenin küçük bölümleri özellikle performans sorunlarını gidermeyle ilgili önemli bilgiler içerir ve bu yüzden bu alanlara odaklanacağız. Ayrıca, Sık karşılaşılan sorunlar için bir İlk On listesi derlemek üzere Microsoft'ta Office 365 performans sorunlarını gidermeye yetecek kadar performans sorunu giderme yaptık, bu sorunlara ve sonra da bunların köküne indirecek araçları nasıl kullanabileceğimize odaklanacağız.

Bunların hepsini yüklememişsiniz, aşağıdaki matris çeşitli araçlardan kullanır. Mümkün olduğu her yerde. Yükleme noktalarına bağlantılar sağlanır. Liste [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) ve [Wireshark](https://www.wireshark.org/) gibi yaygın ağ izleme araçlarını içerir, ancak rahat kullanılan ve ağ trafiğini filtrelemeye alışık olduğunuz herhangi bir izleme aracını kullanın. Test sırasında şunları unutmayın:

- *Tarayıcılarınızı kapatın ve yalnızca bir tarayıcı çalıştırarak test*  edin - Bu, toplam yakalama trafiğinizi azaltır. Daha az yoğun bir izleme yapar.
- *İstemci bilgisayarda DNS çözümleyici önbelleğinizi*  temizleyin - Bu, yakalamanızı almaya başsanız daha temiz bir izleme için size temiz bir başlangıç sağlar.

## <a name="common-issues"></a>Sık karşılaşılan sorunlar

Karşılaş karşılaşabilirsiniz bazı yaygın sorunlar ve bunları Ağ izlemesinde nasıl bu şekilde bulabilirsiniz.

### <a name="tcp-windows-scaling"></a>TCP Windows Ölçeklendirme

SYN - SYN/ACK'de bulunur. Eski donanım ve eskime donanımı TCP pencereleri ölçeklendirmeden yararlanamayy.  Uygun TCP pencereleri ölçeklendirme ayarları olmadan, TCP üst bilgilerindaki varsayılan 16 bit ara bellek mili saniyeler içinde dolar.  İstemci orijinal verilerin alınmıştır ve bu da gecikmelere neden olmak için bildirim alana kadar trafik göndermeye devamamaz.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Ağ izlemesinde SYN - SYN/ACK trafiğine bakın.  Netmon'da, gibi bir filtre kullanın  `tcp.flags.syn == 1`. Bu filtre Wireshark'ta da aynıdır.

![Her iki araç için Syn paketleri için Netmon veya Wireshark filtresi: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Her SYN için, ilgili Bildirimin (SYN/ACK) hedef bağlantı noktasıyla (DstPort) eşan bir kaynak bağlantı noktası (SrcPort) numarası olduğunu fark edin.

Ağ bağlantınız Windows ölçeklendirme değerini görmek için, önce SYN'i ve sonra da ilişkili SYN/ACK'ı genişletin.

![Zaman aralığına almak için SrcPort'un bir izlemede DstPort ile nasıl eş zaman olacağını gösteren grafik.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>TCP Boşta Kalma Süresi Ayarlar

Geçmişten, çoğu çevre ağı geçici bağlantılar için yapılandırılır ve bu da boşta kalma bağlantıların genellikle sonlandırildiği anlamına gelir. Boşta kalma TCP oturumları 100 ile 300 saniyeden uzun bir süre içinde, sunucu ve güvenlik duvarları tarafından sonlandırılır. Bu, Outlook Online için sorundur çünkü boşta olsun veya olsun, uzun süreli bağlantılar oluşturur ve kullanır.

Bağlantılar ara sunucu veya güvenlik duvarı cihazları tarafından sonlandırılsa, istemciye bildirilmez ve Outlook Online'ı kullanmaya çalışmanız, istemci bilgisayarın yeni bir bağlantı kurmadan önce bağlantıyı tekrar tekrar canlandırmaya çalışması anlamına gelecektir. Sayfa yüklemesinde ürün, istemler veya performansın yanıtlanmaz olduğunu görebilirsiniz.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Netmon'da, bir gidiş dönüş için Saat Farkı alanına bakın. Gidiş dönüş, istemcinin sunucuya istek göndermesi ile yanıt alma arasındaki zamandır. İstemci ile çıkış noktası (ör. İstemci --\> Proxy) veya İstemcinin Office 365 (İstemci -- Office 365\>). Bunu birçok paket türü içinde görüyoruz.

Örneğin, Netmon'daki filtre , veya  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`Wireshark'ta gibi olabilir  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.

> [!TIP]
> İzlemenizin IP adresinin DNS sunucunuza ait olup olmadığını bilmiyor musunuz? Komut satırına bakarak deneyin. **Çalıştır'ı** \>  \> başlat'a **tıklayın ve cmd yazın** veya **Windows tuşuna** \> basarak **cmd yazın**. Komut istemine yazın  `nslookup <the IP address from the network trace>`. Test etmek için, kendi bilgisayarınızın IP adresine karşı nslookup kullanın. > Microsoft'un IP aralıklarının listesini görmek için bkz. OFFICE 365 [VE IP adresi aralıkları](./urls-and-ip-address-ranges.md).

Bir sorun varsa, bu durumda (Outlook Online) Uygulama Verileri pasajı görünen özellikle TLS:TLS paketlerinde uzun Saat Farkları görünmesi gerekir (örneğin Netmon'da `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`uygulama veri paketlerini üzerinden bulabilirsiniz). Oturumlar arasında zaman içinde düzgün bir ilerlemeyle bakabilirsiniz. Outlook Online'nızı yenilerken uzun gecikmeler görüyorsanız, bunun nedeni gönderilen büyük ölçüde sıfırlamalar olabilir.

### <a name="latencyround-trip-time"></a>Gecikme/Gidiş Dönüş Süresi

Gecikme süresi; eski cihazların yükseltilmesi, ağa çok sayıda kullanıcı ekleme ve ağ bağlantısında diğer görevler tarafından kullanılan genel bant genişliğinin yüzdesi gibi birçok değişkene bağlı olarak çok değişebilecek bir ölçüdür.

Bu çalışma sayfası için ağ Office 365 ve performans ayarı seçenekleri için bant genişliği [hesaplayıcıları Office 365](network-planning-and-performance.md) vardır.

Bağlantı hızınızı veya ISS bağlantı bant genişliğini mi ölçmeniz gerekiyor? Bu siteyi (veya benzer siteleri) deneyin: [Speedtest Resmi Sitesi](https://www.speedtest.net/) veya tümcecik hız testi için en sevdiğiniz arama **motorunu sorgular**.

#### <a name="tools"></a>Araçlar

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Bir izlemede gecikme süresini izlemek için, istemci bilgisayarın IP adresini ve dns sunucusunun IP adresini aynı adrese kaydeden Office 365. Bu, izleme filtrelemeyi kolaylaştırmak için kullanılır. Bir proxy aracılığıyla bağlanıyorsanız, işi kolaylaştırmak için istemci bilgisayarınızın IP adresine, proxy/çıkış IP adresine Office 365 DNS IP adresine ihtiyacınız olacaktır.

Alıcıya gönderilen bir ping isteği outlook.office365.com ping ticari markayı art arda ICMP paketleri göndermek üzere bağlanamıyor olsa bile, isteği alan  veri merkezi adını size söyler. PsPing (ücretsiz indirme aracı) ve belirli bağlantı noktasını (443) kullanıyorsanız ve belki IPv4 (-4) kullanmak için gönderilen paketler için ortalama bir gidiş dönüş süresi elde olur. Bu, aşağıdaki gibi Office 365 hizmetlerde yer alan diğer URL'lerde çalışır`psping -4 yourSite.sharepoint.com:443`. Aslında, ortalamanız için daha büyük bir örnek almak için bir dizi ping belirterek bunun gibi bir şey deneyin `psping -4 -n 20 yourSite-my.sharepoint.com:443`.

> [!NOTE]
> PsPing, ICMP paketleri göndermez. TCP paketleriyle belirli bir bağlantı noktası üzerinden ping gönderir, böylece açık olduğunu biliyor herhangi birini kullanabilirsiniz. SSL/TLS kullanan Office 365, PsPing bağlantı noktası 443'ü bağlamayı deneyin.

![6,5m ortalama RTT'yi de raporlamak için, outlook.office365.com ping çözümlemesi ve 443 aynı işlemi yapan PSPing'i gösteren ekran görüntü.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Yavaş performans gösteren bir Office 365 ağ izleme yaparken yüklemiş olursanız, için netmon veya Wireshark izlemesini filtrelemeniz gerekir`DNS`. Bu, bizim de araymız olan IP'lerden biri.

IP adresini almak (ve DNS Gecikme Süresine göz atarak) Netmon'a filtre uygulama adımlarını izleyin. Bu örnekte outlook.office365.com, ancak bir SharePoint Online kiracının URL'sini de (örneğin hithere.sharepoint.com) kullanabilirsiniz.

1. URL'ye ping `ping outlook.office365.com` sınaması ekleyin ve sonuçlarda, ping isteğinin gönderildiği DNS sunucusunun adını ve IP adresini yazın.
2. Sayfayı açmak veya size performans sorununu veren eylemi yapmak ya da ping'de yüksek gecikme süresi görüyorsanız, kendi başına ağ izleme işlemi.
3. İzlemeyi Netmon'da açın ve DNS için filtre (bu filtre Wireshark'ta da çalışır, ancak büyük/harfe duyarlıdır `-- dns`). DNS sunucusunun adını ping'inize göre de netmon'da şu şekilde daha hızlı filtre kullanabilirsiniz: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`Wireshark'ta şu şekilde görünen dns and frame contains "namnorthwest".<br/>Yanıt paketini açın ve Netmon **Frame Details** penceresinde, daha fazla bilgi için **genişletmek için DNS'e** tıklayın. DNS bilgisinde, isteğin Posta'da gitti DNS sunucusunun IP adresini Office 365. Bir sonraki adım (PsPing aracı) için bu IP adresi gerekir. Filtreyi kaldırın, DNS Sorgusunu ve Yanıtını yan yana görmek için Netmon'da DNS Yanıtına sağ tıklayın (Frame **Summary** \> **Find Conversations** \> **DNS**).
4. Netmon'da ayrıca, DNS İsteği ile Yanıt arasındaki Saat Farkı sütununu da notun. Sonraki adımda, yüklemesi ve kullanımı kolay [PsPing](/sysinternals/downloads/psping) aracı çok kullanışlıdır, çünkü hem ICMP çoğu zaman Güvenlik Duvarlarında engellenir hem de PsPing gecikme süresini mili saniye cinsinden zarif bir şekilde izler. PsPing, bir adrese ve bağlantı noktasına (bu durumda açık bağlantı noktası 443) bir TCP bağlantısı tamamlar.
5. PsPing yükleyin.
6. Komut istemini açın (\> \> Çalıştır komutu cmd yazın veya Windows Tuşu \> cmd yazın) ve Dizini PsPing komutunu çalıştırmak için PsPing'i yüklemiş olduğunu dizine değiştirme. Örneklerimde, C'nin kökünde bir 'Perf' klasörü oluşturmamı görüyorsunuz. Hızlı erişim için de aynı şeyi yapabiliriz.
7. PsPing'inizi bağlantı noktası numarası gibi önceki Netmon izlemenizin Office 365 DNS sunucusunun IP adresine göre yapmak için komutu yazın`psping -n 20 132.245.24.82:445`. Bu size 20 ping'den örnekleme ve PsPing durduğunda gecikme süresinin ortalamasını sağlar.

Bir proxy sunucusu üzerinden Office 365, adımlar biraz farklıdır. Önce proxy/çıkış ve geri için mili saniye cinsinden ortalama bir gecikme süresi değeri almak için proxy sunucunuza PsPing atlarsınız ve sonra eksik değeri (proxy'ye ve geri dönmek için) proxy'de veya doğrudan İnternet bağlantısı olan bir bilgisayarda PsPing Office 365 çalıştırmanız gerekir.

Proxy sunucudan PsPing çalıştırmayı seçerseniz, mili saniye cinsinden iki değeriniz olur: İstemci bilgisayardan proxy sunucusuna veya çıkış noktasına ve proxy sunucusundan Office 365. Hepsi bu kadar! Yine de değerleri kaydediyor.

PsPing'i İnternet'e doğrudan bağlantısı olan, yani proxy olmayan başka bir istemci bilgisayarda çalıştırmanız, mili saniye cinsinden iki değeriniz olur: İstemci bilgisayardan proxy sunucusuna veya çıkış noktasına ve aynı noktadan diğerine Office 365. Bu durumda, istemci bilgisayardan proxy sunucusuna veya çıkış noktasına değerini, istemci bilgisayardan Office 365'e değerinden çıkarırsınız ve istemci bilgisayarınızdan proxy sunucusuna veya çıkış noktasına ve proxy sunucusundan veya çıkış noktasından Office 365.

Öte yandan, etkilenen bir bilgisayarı doğrudan bağlı veya proxy'yi atlayan bir istemci bilgisayar bulsanız bile, öncelikle sorunun bu bilgisayarda yeniden ortaya çıkar mı olduğunu görebilir ve bundan sonra bu bilgisayarla test edin.

Netmon izlemesinde de görülen gecikme süresi, herhangi bir oturumda yeterince varsa bu fazladan milisaniyelerin bir bedeli olabilir.

![Çerçeve Özeti'ne eklenmiş varsayılan Netmon Zaman Aralığı sütunuyla Netmon'daki genel gecikme süresi.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> IP adresiniz burada gösterilen IP'lerden farklı olabilir, örneğin, ping'iniz 157.56.0.0/16 gibi bir aralık veya benzer bir aralık geri dönecektir. E-posta adresleri tarafından kullanılan aralıkların Office 365 için [URL'ler Office 365 IP adresi aralıklarını denetleme.](./urls-and-ip-address-ranges.md)

Örneğin 132,245'i aramak için tüm düğümleri genişletmeyi unutmayın (bunun için en üstte bir düğme vardır).

### <a name="proxy-authentication"></a>Proxy Kimlik Doğrulaması

Bu yalnızca, bir proxy sunucu üzerinden gidiyorsanız sizin için geçerlidir. Yoksa, bu adımları atlayabilirsiniz. Düzgün çalışırken, proxy kimlik doğrulaması mili saniye cinsinden tutarlı şekilde olmalıdır. Tepe kullanım dönemleri (örneğin) sırasında aralıklı kötü performans görmeyin.

Proxy kimlik doğrulaması açıksa, bilgi almak için ara sunucu hizmetine Office 365 her TCP bağlantısı sanız perde arkasında bir kimlik doğrulama sürecinden geçmelisiniz. Dolayısıyla, örneğin, Outlook Online'da Takvim'den Posta'ya geçişte, kimlik doğrulamanız olur. SharePoint Online'da ise, bir sayfada birden çok site veya konumdan medya veya veriler görüntü varsa, verileri işlemek için gereken her farklı TCP bağlantısı için kimlik doğrulamanız gerekir.

Outlook Online'da, Takvim ile posta kutunuz arasında her geçişte yavaş yükleme süreleriyle veya SharePoint Online'da sayfa yüklemeleri yavaş olabilir. Bununla birlikte, burada listelenmiyor başka belirtiler de vardır.

Proxy kimlik doğrulaması, çıkış proxy sunucunuzda bir ayardır. Bu sorun, e-Office 365 bir performans sorununa neden oluyorsa, ağ ekibinize danışmanız gerekir.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Yeni bir TCP oturumu gerekirken, yaygın olarak sunucudan dosya veya bilgi talep etmek veya bilgi sağlamak için proxy kimlik doğrulaması  sürer. Örneğin, HTTP GET veya HTTP POST istekleri çevresinde proxy kimlik doğrulaması görebilirler. İzlemenize istekleri kimlik doğrulayanın çerçevelerini görmek için Netmon'a 'NTLMSSP Özeti' sütununu ekleyin ve için filtre kullanın  `.property.NTLMSSPSummary`. Kimlik doğrulamanın ne kadar süreyle devam ye alan olduğunu görmek için Zaman Aralığı sütununu ekleyin.

Netmon'a sütun eklemek için:

1. Açıklama gibi bir sütuna sağ **tıklayın**.
2. Sütunları **Seç'e tıklayın**.
3. Listede _NTLMSSP Özet_ ve _Zaman Aralığı'nın_ yerini bulun ve Ekle'ye **tıklayın**.
4. Yan yana okuyabilk için yeni sütunları _Açıklama_ sütunlarının önünde veya arkasında bir yere taşıma.
5. **Tamam**'a tıklayın.

Sütunu eklemese bile Netmon filtresi çalışır. Ancak, kimlik doğrulamanın hangi aşamasında olduğunu görebilirseniz, sorun gidermeniz çok daha kolay olur.

Proxy Kimlik Doğrulaması örneklerini arıyorsanız, NTLM Görev veya Kimlik Doğrulama İletisi bulunan tüm çerçeveleri incelemeyi sağlar. Gerekirse, trafiğin belirli bir parçasını sağ tıklatın ve Konuşmaları Bul TCP'sini \> tıklatın. Bu Konuşmalar'daki Zaman Aralığı değerlerine dikkat edersiniz.

![Konuşmaya göre filtrelenmiş proxy kimlik doğrulamasını gösteren Netmon izlemesi.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Wireshark'ta olduğu gibi proxy kimlik doğrulamasında dört saniyelik gecikme. Önceki **görüntülenen kareden** zaman aralığı sütunu, çerçeve ayrıntılarında aynı addaki alana sağ tıklar ve Sütun Olarak Ekle seçerek yapılmış.  <br/> ![Wireshark'ta 'Önceki görüntülenen kareden zaman aralığı' sütunu, çerçeve ayrıntılarında aynı addaki alana sağ tık tıklar ve Sütun Olarak Ekle seçerek kullanılabilir.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS Performansı

Ad çözümlemesi, istemcinin ülkesine mümkün olduğunca yakın olduğunda en iyi ve en hızlı şekilde çalışır.

DNS ad çözümlemesi deniz aşırı sürüyorsa, sayfa yüklemeleri saniyeler sürebilir. İdeal olarak, ad çözümlemesi 100ms altında gerçekleşir. Yoksa, daha fazla araştırma yapsanız gerekir.

> [!TIP]
> İstemci Bağlantısı'nın bu bağlantıda nasıl olduğundan emin Office 365? Buradaki İstemci Bağlantısı Başvurusu belgesine göz [atabilirsiniz](/previous-versions//dn741250(v=technet.10)).

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Nelere bakmalı?

DNS performansını çözümlemek, bir ağ izlemesi için genellikle başka bir iştir. Bununla birlikte, PsPing de olası bir nedenin in veya çıkışını ortaya çıkmada yararlıdır.

DNS trafiği TCP ve UDP isteklerine dayalıdır ve yanıtlar, belirli bir isteği kendi yanıtıyla eşleşmeye yardımcı olacak bir Kimlikle açıkça işaretlenir. DNS trafiğini, örneğin SharePoint Online bir web sayfasında bir ağ adı veya URL'si kullandığında görebilirsiniz. Bir kural olarak, Bölgeleri aktarılması dışında bu trafiğin çoğu UDP üzerinden çalışır.

Hem Netmon hem de Wireshark'ta, DNS trafiğine bakmanın en basit filtresi basit bir filtredir `dns`. Filtreyi belirtirken küçük harf kullanmaya emin olun. İstemci bilgisayarınızda sorunu yeniden oluşturmaya başlamadan önce DNS çözümleyici önbelleğinizi temizlemeyi unutmayın. Örneğin, Giriş sayfası için yavaş SharePoint Online sayfa yüklemesi kullanıyorsanız, tüm tarayıcıları kapatmanız, yeni bir tarayıcı açmanız, izlemeyi başlatmanız, DNS çözümleyici önbelleğini temizlemeniz ve SharePoint Online sitenize göz atması gerekir. Sayfanın tamamı çözümlenin, izlemenin tamamını durdurarak kaydetmeniz gerekir.

![DNS, Netmon'daki DNS için temel bir filtredir.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Saat farkına buradan bakabilirsiniz. Ayrıca Zaman Aralığı sütununu **Netmon'a** eklemek yararlı olabilir; bunu aşağıdaki adımları tamamlayarak da bunuabilirsiniz:

1. Açıklama gibi bir sütuna sağ **tıklayın**.
2. Sütunları **Seç'e tıklayın**.
3. Listede _Zaman Aralığı'nın_ yerini bulun ve Ekle'ye **tıklayın**.
4. Yan yana okuyabilk için yeni sütunu _Açıklama_ sütunlarının önünde veya arkasında bir yere taşıma.
5. **Tamam**'a tıklayın.

İlginizi gereken bir sorgu bulursanız, bunu, çerçeve ayrıntıları panelinde o sorguyu sağ tıklatıp Konuşmaları Bul **DNS'sini seçerek çıkarabilirsiniz**\>. Ağ Konuşmaları paneli UDP trafiği günlüğünde sağa doğru, belirli bir konuşmaya atlar.

![DNS'e göre filtrelenmiş Outlook Çevrimiçi yüklemenin Netmon izlemesi ve sonuçları daraltmak için Konuşmaları Bul ve DNS'i kullanma.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

Wireshark'ta DNS süresi için bir sütun oluşturabilirsiniz. Wireshark'ta izlemenizi alma (veya bir izleme açma) ve 'ya göre filtreleme `dns`veya daha da yararlı bir şekilde filtreleme  `dns.time`. Herhangi bir DNS sorgusuna tıklayın ve ayrıntıları gösteren panelde ayrıntıları  `Domain Name System (response)` genişletin. Zaman için bir alan (örneğin, `[Time: 0.001111100 seconds]`. Bu kez sağ tıklayın ve Sütun Olarak **Uygula'yı seçin**. Bu size izlemenizi **daha** hızlı sıralamanız için bir Zaman sütunu ve verecek. Hangi DNS aramasını çözümlemenin en uzun süren olduğunu görmek için azalan değerlere göre sıralamak için yeni sütuna tıklayın.

[Wireshark'ta dns.time (küçük harf) ile filtrelenmiş SharePoint Online göz atma (ayrıntılardaki saat sütun haline gelen saat ve artan düzende sıralanmış).](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

DNS çözümleme süresiyle ilgili daha fazla araştırma yapmak için, TCP tarafından kullanılan DNS bağlantı noktasına (örneğin, ) karşı bir PsPing deneyin  `psping <IP address of DNS server>:53`. Hala bir performans sorunu görüyor musunuz? Bunu biliyorsanız, sorun muhtemelen, çözümleme yapmak için o dns uygulamasındaki bir sorundan daha geniş bir ağ sorunu olur. Ayrıca, outlook.office365.com için DNS ad çözümlemesi için DNS ad çözümlemesi'nin nerede (örneğin, Outlook) yer alıyor olduğunu bir kez daha outlook-namnorthwest.office365.com.

Sorun DNS'e özgü görünüyorsa, sorunu daha fazla araştırmak üzere DNS yapılandırmalarını ve DNS Forwarders'i incelemeleri için IT departmanınıza başvurılması gerekebilir.

### <a name="proxy-scalability"></a>Proxy Ölçeklenebilirliği

İnternet'Outlook Online gibi Office 365 hizmetler istemcilere birden çok uzun vadeli bağlantı sağlar. Bu nedenle, her kullanıcı daha uzun ömür gerektiren daha fazla bağlantı kullanabilir.

#### <a name="tools"></a>Araçlar

Matematik

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Buna özgü bir ağ izleme veya sorun giderme aracı yoktur. Bunun yerine, sınırlamalar ve diğer değişkenler verilen bant genişliği hesaplamalarına dayalıdır.

### <a name="tcp-max-segment-size"></a>TCP Maksimum Segment Boyutu

SYN - SYN/ACK'de bulunur.  TCP paketlerinin mümkün olan en fazla miktarda veri taşıy sağlayacak şekilde yapılandırıldığından emin olmak için, gerçekleştirilen tüm performans ağ izlemesinde bu denetimi gerçekleştirin.

Hedef, veri iletimi için 1460 baytlık MSS görmektir. Bir proxy arkasındaysanız veya NAT kullanıyorsanız, en iyi sonuçları elde etmek için istemciden proxy/çıkış/NAT'ye ve proxy/çıkış/NAT'tan NAT'a bu testi Office 365 unutmayın! Bunlar farklı TCP oturumlarıdır.

#### <a name="tools"></a>Araçlar

Netmon

#### <a name="what-to-look-for"></a>Nelere bakmalı?

TCP Maksimum Segment Boyutu (MSS), ağ izlemesi sırasındaki üç yollı el sıkışmalarının bir başka parametresidir ve buna göre, ihtiyacınız olan verileri SYN - SYN/ACK paketinde bulabilirsiniz. MSS'i görmek gerçekten oldukça basittir.

Sahip olunan herhangi bir performans ağ izlemesi açın ve merak ettiğim veya performans sorununu gösteren bağlantıyı bulun.

> [!NOTE]
> Bir izlemeye bakıyorsanız ve konuşmanıza uygun trafiği bulmanız gerekirse İstemcinin IP'sini veya proxy sunucusunun veya çıkış noktasının IP'sini ya da her ikisini birden filtrenin. Doğrudan gidip, izlemede yer alan ip adresi için ping Office 365 ve buna göre filtre uygulamanız gerekir.

İzlemeye ikinci el mi bakıyorsunuz? Kendinizi yönlendirmek için filtreler kullanmayı deneyin. Netmon'da, URL'yi temel alan bir arama çalıştırın `Containsbin(framedata, ascii, "sphybridExample")`; örneğin, çerçeve numarasını not edin.

Wireshark'ta gibi bir şey kullanın  `frame contains "sphybridExample"`. Uzak Winsock (RWS) trafiği tespit ettiysanız (Wireshark'ta [PSH, ACK] olarak görünebilir), daha önce açıktığı gibi, RW bağlantılarında ilgili SYN - SYN/ACK'lar öncesinde kısa süre görülebnin olduğunu unutmayın.

Bu noktada, çerçeve numarasını kaydedebilirsiniz, filtreyi atabilirsiniz, en yakın SYN'ye bakmak için Netmon'daki Ağ Konuşmaları penceresinde Tüm Trafik'e tıklarsınız.

En önemlisi, izlemenin olduğu sırada herhangi bir IP adresi bilgisi almadıysanız, izlemede URL'nizi bulmak ( `sphybridExample-my.sharepoint.com`örneğin, bir parçası) size filtre için gereken IP adreslerini ve verecek.

İzlemede görmek istediğiniz bağlantıyı bulun. Bunu yapmak için izlemeyi tarayın, IP adreslerine göre filtrelenin veya Netmon'daki Ağ Konuşmaları penceresini kullanarak belirli Konuşma Kimliklerini seçin. SYN paketini bulanın, Çerçeve Ayrıntıları panelinde TCP (Netmon'da) veya İletim Denetimi Protokolü'ne (Wireshark'ta) genişletin. TCP Seçenekleri ve MaxSegmentSize'ı genişletin. İlgili SYN-ACK çerçevesini bulun ve TCP Seçenekleri ve MaxSegmentSize'ı genişletin. İki değerden küçük olan boyut, Maksimum Segment Boyutunuz olur. Bu resimde Netmon'daki TCP Sorun Giderme adlı yerleşik Sütundan istiyorum.

![Netmon'da yerleşik sütunlar kullanılarak filtrelenmiş ağ izlemesi.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Yerleşik sütun Çerçeve Ayrıntıları panelinin **en üstündedir** . (Normal görünüme dönmek için tekrar **Sütunlar'a tıklayın ve** ardından Saat Dilimi'ne **tıklayın**.)

![TCP Sorun Giderme seçeneği için Sütunlar açılan listesinde (Çerçeve Özeti'nin üstünde) bulun.](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Burada, Wireshark'ta filtre uygulanmış bir izleme ve var. MSS değerine () özgü bir filtre vardır`tcp.options.mss`. Bir SYN, SYN/ACK, ACK el sıkışması çerçeveleri Wireshark'ın en altında bağlantılıdır ve Çerçeve Ayrıntılarına eşdeğerdir (buna göre 47 ACK çerçevesi 46 SYN/ACK'ya, 43 SYN'ye bağlar) ve böylece bu tür çalışma daha kolay olur.

![Wireshark'ta Max Segment Size (MSS) için tcp.options.mss ile filtrelenmiş izleme.](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Seçmeli Bildirim'i **denetlemeniz gerekirse (bu matriste** bir sonraki konu), izlemenizi kapatabilirsiniz!

### <a name="selective-acknowledgment"></a>Seçmeli Bildirim

SYN - SYN/ACK'de bulunur. Hem SYN hem de SYN/ACK'da İzin Verilen olarak rapor gerekir. Seçmeli Bildirim (SACK), bir paket veya paketler kaybolduğunda daha sorunsuz veri iletimsine olanak sağlar. Cihazlar bu özelliği devre dışı bırakarak performans sorunlarına yol açabilir.

Bir proxy arkasındaysanız veya NAT kullanıyorsanız, en iyi sonuçları elde etmek için istemciden proxy/çıkış/NAT'ye ve proxy/çıkış/NAT'tan NAT'a bu testi Office 365 unutmayın! Bunlar farklı TCP oturumlarıdır.

#### <a name="tools"></a>Araçlar

Netmon

#### <a name="what-to-look-for"></a>Nelere bakmalı?

Seçmeli Bildirim (SACK), SYN-SYN/ACK el sıkışması içinde bir başka parametredir. SYN - SYN/ACK için izlemenizi birçok şekilde filtreleyebilirsiniz.

Görmek istediğiniz izlemede bağlantıyı bulmak için izlemeyi tarayın, IP adreslerine göre filtre kullanın veya Netmon'daki Ağ Konuşmaları penceresini kullanarak Konuşma Kimliği'ne tıklayın. SYN paketini bulanın, Çerçeve Ayrıntıları bölümünde TCP (Netmon'da) veya İletim Denetimi Protokolü'ne (Wireshark'ta) gidin. TCP Seçenekleri'ne ve sonra SACK'ya tıklayın. İlgili SYN-ACK çerçevesini bulun ve TCP Seçenekleri ve SACK alanını genişletin. Hem SYN hem de SYN/ACK'da belirli bir SACK'ya izin ver. Burada, hem Netmon'da hem de Wireshark'ta görülen SACK değerleri ve ve daha sonraları yer almaktadır.

![tcp.flags.syn == 1 sonucunda Netmon'daki Seçmeli Bildirim (SACK).](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![Wireshark'ta tcp.flags.syn == 1 filtresine sahip SACK.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS Coğrafi Konumu

Dünyanın diğer yerleri Office 365 DNS aramanızı çözümlemeye çalıştığında bağlantı hızınız buna neden olur.

Outlook Online'da, ilk DNS araması tamamlandıktan sonra, en yakın veri merkezinize bağlanmak için bu DNS'in konumu kullanılır. Bir Outlook Online CAS sunucusuna bağlanırsınız ve bu da verilerinizin depolandığı veri merkezine (dC) bağlanmak için omurga ağı kullanır. Bu daha hızlıdır.

SharePoint Online'a erişirken, yurt dışındaki bir kullanıcı kendi etkin veri merkezlerine yönlendirilir. Bu, konumu SPO kiracılarının yurt üssüne dayalı olan dC'dir (dolayısıyla kullanıcı ABD tabanlı ise ABD'de bir dC).

Lync online'ın bir defada birden çok dC'de etkin düğümleri vardır. Lync çevrimiçi örnekleri için istekler gönder geldiğinde, Microsoft'un DNS'i isteğin dünyanın nereden geldiğini belirler ve Lync Online'ın etkin olduğu en yakın bölgesel dC'den IP adresleri geri dönecektir.

> [!TIP]
> İstemcilerin E-İş'e nasıl bağlan daha fazla bilgi Office 365? İstemci Bağlantısı başvuru [makalesine](/previous-versions//dn741250(v=technet.10)) (ve yararlı grafiklerine) göz atabilirsiniz.

#### <a name="tools"></a>Araçlar

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Nelere bakmalı?

İstemcinin DNS sunucularından Microsoft'un DNS sunucularına yapılan istekler çoğu durumda Microsoft DNS'in bir bölgesel veri merkezinde (dC) IP'sini döndüren Microsoft DNS'sine neden olması gerekir. Bu sizin için ne anlama geliyor? Merkeziniz Hindistan Bangalore'ta bulunuyorsa, ancak siz ABD'de seyahat ediyorsanız, tarayıcınız Outlook Online için bir istekte bulunuyorsa, Microsoft'un DNS sunucularının IP adreslerini ABD'nin veri merkezlerine (bölgesel bir veri merkezi) teslim olması gerekir. Bir postanın posta Outlook, bu veriler Microsoft'un hızlı omurga ağı üzerinden veri merkezleri arasında ilerler.

Ad çözümlemesi kullanıcının bulunduğu konuma mümkün olduğunca yakın olduğunda DNS en hızlı şekilde çalışır. Avrupa'daysanız Avrupa'daki bir Microsoft DNS'ine gitmek ve (ideal olarak) Avrupa'daki bir veri merkeziyle uğraşmak gerekir. Avrupa'daki bir istemciden ve Amerika'daki bir DNS'e ve veri merkezinden performans yavaş olacaktır.

DNS isteğinizin dünyanın outlook.office365.com nereye yönlendirileceğini belirlemek için Ping aracını karşıdan çalıştırabilirsiniz. Avrupa'daysanız, Böyle bir şey tarafından yanıt outlook-emeawest.office365.com. Amerika'da, böyle bir şey outlook-namnorthwest.office365.com.

İstemci bilgisayarda komut istemini açın (Çalıştırmayı \> \> Başlat cmd veya cmd Windows \> cmd yazın). ping outlook.office365.com ENTER tuşuna basın. IPv4 üzerinden ping belirtmek için -4 belirtmeyi unutmayın. ICMP paketlerinden yanıt alamayasınız, ancak isteğin yönlendirilen DNS'in adını görmeniz gerekir. Bu bağlantının gecikme süresi numaralarını görmek için ping tarafından döndürülen sunucunun IP adresine PsPing yapmaya deneyin.

![outlook-namnorthwest outlook.office365.com çözünürlük gösteren ping sınaması.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![Ortalama 28 milisaniyelik gecikme süresini gösteren outlook.office365.com ping tarafından döndürülen IP adresine PSPing.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 Sorunlarını Giderme

#### <a name="tools"></a>Araçlar

- Netmon
- HTTPWatch
- Tarayıcıda F12 Konsolu

Ağa özel bu makalede uygulamaya özgü sorun gidermede kullanılan araçlar bizim için gerekli değil. Ancak, kullanabileceğiniz kaynakları  *bu* [sayfada bulabilirsiniz](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>İlgili Konular

[Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)