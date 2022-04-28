---
title: Office 365 için performans sorunlarını giderme planı
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makale, Office 365 performans sorunlarını gidermenize ve hatta en yaygın sorunlardan bazılarını düzeltmenize yardımcı olabilir.
ms.openlocfilehash: 7380d6beb89cdd128ccf86f47e1e3c236aabda77
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100577"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Office 365 için performans sorunlarını giderme planı

SharePoint Online, OneDrive İş, Exchange Online veya Skype Kurumsal Online ile istemci bilgisayarınız arasındaki gecikmeleri, kilitlenmeleri ve yavaş performansı belirlemek ve düzeltmek için atılacak adımları bilmeniz gerekiyor mu? Desteği çağırmadan önce, bu makale Office 365 performans sorunlarını gidermenize ve hatta en yaygın sorunlardan bazılarını düzeltmenize yardımcı olabilir.

Bu makale aslında performans sorununuzla ilgili değerli verileri yakalamak için kullanabileceğiniz örnek bir eylem planıdır. Bu makalede bazı önemli sorunlar da yer alır.

Ağ performansı konusunda yeniyseniz ve istemci makinelerinizle Office 365 arasındaki performansı izlemek için uzun vadeli bir plan yapmak istiyorsanız Office 365 [performans ayarlama ve sorun giderme - Yönetici ve BT Pro'ne](performance-tuning-using-baselines-and-history.md) göz atın.

## <a name="sample-performance-troubleshooting-action-plan"></a>Örnek performans sorunlarını giderme eylem planı

Bu eylem planı iki bölümden oluşur; bir hazırlık aşaması ve günlüğe kaydetme aşaması. Şu anda bir performans sorununuz varsa ve veri toplama işlemi yapmanız gerekiyorsa, bu planı hemen kullanmaya başlayabilirsiniz.

### <a name="prepare-the-client-computer"></a>İstemci bilgisayarı hazırlama

- Performans sorununu yeniden oluşturabilen bir istemci bilgisayar bulun. Bu bilgisayar sorun giderme sırasında kullanılacaktır.
- Test etme zamanı geldiğinde hazır olmanız için performans sorununun gerçekleşmesine neden olan adımları not edin.
- Bilgileri toplamak ve kaydetmek için araçları yükleyin:
  - [Netmon 3.4'ü](https://www.microsoft.com/download/details.aspx?id=4865) yükleyin (veya eşdeğer bir ağ izleme aracı kullanın).
  - Ücretsiz [HTTPWatch](https://www.httpwatch.com/download/) Basic Edition'ı yükleyin (veya eşdeğer bir ağ İzleme aracı kullanın).
  - Test sırasında uyguladığınız adımların kaydını tutmak için bir ekran kaydedici kullanın veya Windows Vista ve sonraki sürümlerle birlikte gelen Adım Kaydedicisi'ni (PSR.exe) çalıştırın.

### <a name="log-the-performance-issue"></a>Performans sorununu günlüğe kaydetme

- Tüm gereksiz İnternet tarayıcılarını kapatın.
- Adım Kaydedicisi'ni veya başka bir ekran kaydediciyi başlatın.
- Netmon yakalamanızı (veya ağ izleme aracını) başlatın.
- ipconfig /flushdns yazarak istemci bilgisayardaki DNS önbelleğinizi komut satırından temizleyin.
- Yeni bir tarayıcı oturumu başlatın ve HTTPWatch'u açın.
- İsteğe bağlı: Exchange Online test ediyorsanız, Office 365 yönetici konsolundan Exchange İstemci Performans Analizi aracını çalıştırın.
- Performans sorununa neden olan tam adımları yeniden oluşturun.
- Netmon'unuzun veya başka bir aracın izini durdurun.
- Komut satırında, aşağıdaki komutu yazıp ENTER tuşuna basarak Office 365 aboneliğinize bir izleme yolu çalıştırın:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Adım Kaydedicisi'ni durdurun ve videoyu kaydedin. Yakalamanın tarih ve saatini ve iyi veya kötü performans gösterip göstermediğini eklediğinizden emin olun.
- İzleme dosyalarını kaydedin. Yine, yakalamanın tarih ve saatini ve iyi veya kötü performans gösterip göstermediğini eklemeyi unutmayın.

Bu makalede bahsedilen araçları çalıştırma hakkında bilginiz yoksa endişelenmeyin çünkü sonraki adımlarda bu adımları sağlayacağız. Bu tür bir ağ yakalama işlemine alışkınsanız, günlükleri filtrelemeyi ve okumayı açıklayan [Temelleri toplama](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines) bölümüne atlayabilirsiniz.

### <a name="flush-the-dns-cache-first"></a>Önce DNS Önbelleği'ni temizleyin

Neden mi? DNS önbelleğini boşaltarak testlerinizi temiz bir sayfayla başlatmış olacaksınız. Önbelleği temizleyerek DNS çözümleyici içeriğini en güncel girişlere sıfırlamış olursunuz. Temizlemenin HOSTs dosya girdilerini kaldırmadığını unutmayın. HOST dosya girdilerini kapsamlı bir şekilde kullanıyorsanız, bu girdileri başka bir dizindeki bir dosyaya kopyalamanız ve ardından HOST dosyasını boşaltmanız gerekir.

#### <a name="flush-your-dns-resolver-cache"></a>DNS çözümleyici önbelleğinizi temizleme

1. Komut istemini açın (**Çalıştırma** \> **cmd'sini** **başlat** \> veya **Windows anahtar** \> **cmd**).
2. Aşağıdaki komutu yazın ve ENTER tuşuna basın:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsoft'un Ağ İzleme aracı ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)), ağlardaki bilgisayarlar arasında geçen paketleri(trafik) analiz eder. Office 365 ile trafiği izlemek için Netmon kullanarak paket üst bilgilerini yakalayabilir, görüntüleyebilir ve okuyabilir, arayan cihazları tanımlayabilir, ağ donanımındaki önemli ayarları denetleyebilir, bırakılan paketleri arayabilir ve şirket ağınızdaki bilgisayarlar ile Office 365 arasındaki trafik akışını izleyebilirsiniz. Trafiğin gerçek gövdesi şifrelendiğinden, yani SSL/TLS aracılığıyla 443 numaralı bağlantı noktasında hareket ettiğinden, gönderilen dosyaları okuyamazsınız. Bunun yerine, sorunun davranışını izlemenize yardımcı olabilecek paketin izlediği yolun filtrelenmemiş bir izlemesini alırsınız.

Şu anda filtre uygulamadığınızdan emin olun. Bunun yerine, izleme ve kaydetmeyi durdurmadan önce adımları izleyin ve sorunu gösterin.

Netmon 3.4'ü yükledikten sonra aracı açın ve şu adımları izleyin:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Bir Netmon izlemesi alın ve sorunu yeniden oluşturun

1. Netmon 3.4'i başlatın.
**Başlangıç** sayfasında üç bölme vardır: **Son Yakalamalar**, **Ağları Seçme** ve **Microsoft Ağ İzleyicisi'ni Kullanmaya Başlama 3.4. Dikkat edin**. Ağları Seç paneli, yakalayabileceğiniz varsayılan ağların listesini de verir. Burada ağ kartlarının seçili olduğundan emin olun.

2. **Başlangıç** sayfasının üst kısmındaki **Yeni Yakalama'ya** tıklayın. Bu, **Başlangıç** sayfası sekmesinin yanına **Capture 1** adlı yeni bir sekme ekler.
![Netmon'un Yeni Yakalama, Başlat ve Durdur düğmeleri vurgulanmış kullanıcı arabirimi.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Basit bir yakalama yapmak için araç çubuğunda **Başlat'a** tıklayın.

4. Performans sorunu oluşturan adımları yeniden oluşturun.

5. **Dosya** \> **Farklı Kaydetmeyi** **Durdur'a** \> tıklayın. Saat dilimiyle birlikte tarih ve saat vermeyi ve bunun kötü veya iyi bir performans gösterip göstermediğini belirtmeyi unutmayın.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) ücretli ve ücretsiz bir sürüm olarak gelir. Ücretsiz Basic Edition, bu test için ihtiyacınız olan her şeyi kapsar. HTTPWatch, ağ trafiğini ve sayfa yükleme süresini doğrudan tarayıcı pencerenizden izler. HTTPWatch, Internet Explorer'ın performansı grafik olarak açıklayan bir eklentisidir. Analiz HTTPWatch Studio'da kaydedilebilir ve görüntülenebilir.

> [!NOTE]
> Firefox, Google Chrome gibi başka bir tarayıcı kullanıyorsanız veya Internet Explorer'da HTTPWatch yükleyemiyorsanız, yeni bir tarayıcı penceresi açın ve klavyenizde F12 tuşuna basın. Tarayıcınızın en altında Geliştirici Aracı açılır penceresini görmeniz gerekir. Opera kullanıyorsanız, Web Denetçisi için CTRL+SHIFT+I tuşlarına basın, ardından **Ağ** sekmesine tıklayın ve aşağıda özetlenen testi tamamlayın. Bilgiler biraz farklı olacaktır, ancak yükleme süreleri milisaniye cinsinden görüntülenmeye devam eder. > HTTPWatch, SharePoint Çevrimiçi sayfa yükleme süreleriyle ilgili sorunlar için de çok kullanışlıdır.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>HTTPWatch'u çalıştırın ve sorunu yeniden oluşturun

HTTPWatch bir tarayıcı eklentisidir, bu nedenle aracı tarayıcıda kullanıma açmak Internet Explorer'ın her sürümü için biraz farklıdır. Genellikle, HTTPWatch'u Internet Explorer tarayıcısında Komutlar çubuğunun altında bulabilirsiniz. Tarayıcı pencerenizde HTTPWatch eklentisini görmüyorsanız **, Yardım** \> **Hakkında'ya** tıklayarak tarayıcınızın sürümünü denetleyin veya Internet Explorer'ın sonraki sürümlerinde dişli simgesine ve **Internet Explorer Hakkında'ya** tıklayın. **Komutlar** çubuğunu başlatmak için Internet Explorer'da menü çubuğuna sağ tıklayın ve **Komutlar çubuğu'na** tıklayın.

Geçmişte HTTPWatch hem Komutlar hem de Gezgin çubuklarıyla ilişkilendirilmiştir. Bu nedenle, yükledikten sonra simgeyi hemen görmüyorsanız (yeniden başlatmadan sonra bile) **Araçlar'ı** ve simge için araç çubuklarınızı işaretleyin. Araç çubuklarının özelleştirilebileceğini ve bunlara seçeneklerin eklenebileceğini unutmayın.

![HTTPWatch simgesinin görüntülendiği Internet Explorer'ın Komut araç çubuğu.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Internet Explorer tarayıcı penceresinde HTTPWatch'ı başlatın. Bu pencerenin en altındaki tarayıcıya yerleştirilmiş olarak görünür. **Kaydet'e** tıklayın.

2. Performans sorununa dahil olan tam adımları yeniden oluşturun. HTTPWatch'ta **Durdur** düğmesine tıklayın.

3. HTTPWatch veya **E-posta ile Gönder'i** **kaydedin**. Dosyayı tarih ve saat bilgilerini ve watch'unuzun iyi veya kötü performans gösterimi içerip içermediğini gösteren bir göstergeyi içermesi için adlandırmayı unutmayın.

![Office 365 giriş sayfasının sayfa yükü için Ağ sekmesini gösteren HTTPWatch.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Bu ekran görüntüsü HTTPWatch'un Professional sürümünden alınmıştı. Professional sürümü olan bir bilgisayarda Temel Sürüm'de alınan izlemeleri açabilir ve burada okuyabilirsiniz. bu yöntem aracılığıyla izlemeden ek bilgiler bulunabilir.

## <a name="problem-steps-recorder"></a>Sorun Adımları Kaydedicisi

Adım Kaydedicisi veya PSR.exe, oluşan sorunları kaydetmenize olanak tanır. Çok kullanışlı bir araçtır ve çalıştırılması çok basittir.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Çalışmanızı kaydetmek için Sorun Adımları Kaydedicisi'yi (PSR.exe) çalıştırın

1. Tamam **PSR.exe** \> **ÇalıştırmaYı** \> **Başlat** \> türünü kullanın veya **Windows Tuş** \> türü **PSR.exe** \> tıklayın ve enter tuşuna basın.

2. Küçük PSR.exe penceresi görüntülendiğinde **Kaydı Başlat'a** tıklayın ve performans sorununu yeniden oluşturan adımları yeniden oluşturun. Gerekirse Açıklama **Ekle'ye tıklayarak açıklama ekleyebilirsiniz**.

3. Adımları tamamladığınızda **Kaydı Durdur'a** tıklayın. Performans sorunu bir sayfa işleme ise, kaydı durdurmadan önce sayfanın işlenmesini bekleyin.

4. **Kaydet**'e tıklayın.

![Adım Kaydedicisi'nin veya PSR.exe ekran görüntüsü.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Tarih ve saat sizin için kaydedilir. Bu, PSR'nizi Netmon izlemenize ve HTTPWatch'unuza zamanında bağlar ve hassas sorun gidermeye yardımcı olur. PSR kaydındaki tarih ve saat, örneğin, oturum açma ve URL'ye göz atma ile yönetici sitesinin kısmi işlenmesi arasında bir dakika geçtiğini gösterebilir.

## <a name="read-your-traces"></a>İzlemelerinizi okuma

Ağ ve performans sorunlarını giderme hakkında bir makale aracılığıyla bilinmesi gereken her şeyi öğretmek mümkün değildir. Performans konusunda iyi bir deneyim elde eder ve ağınızın nasıl çalıştığını ve genellikle nasıl performans gösterdiği hakkında bilgi sahibi olur. Ancak en sık karşılaşılan sorunları ortadan kaldırmanızı nasıl kolaylaştırabileceğini göstermek ve en sık karşılaşılan sorunların listesini toparlamak mümkündür.

Office 365 siteleriniz için ağ izlemelerini okuma becerileri edinmek istiyorsanız, düzenli olarak sayfa yüklemelerinin izlerini oluşturmak ve bunları okuma deneyimi kazanmaktan daha iyi bir öğretmen yoktur. Örneğin, fırsatınız olduğunda bir Office 365 hizmeti yükleyin ve işlemi takip edin. DNS trafiğinin izlemesini filtreleyin veya FrameData'da göz attığınız hizmetin adını arayın. Hizmet yüklendiğinde gerçekleşen adımlar hakkında bir fikir edinmek için izlemeyi tarayın. Bu, normal sayfa yükünün nasıl görünmesi gerektiğini öğrenmenize yardımcı olur ve sorun giderme söz konusu olduğunda, özellikle performansla ilgili olarak iyi ve kötü izlemeleri karşılaştırmak size çok şey öğretebilir.

Netmon, Görüntüleme filtresi alanında Microsoft Intellisense kullanır. Intellisense veya akıllı kod tamamlama, nokta yazdığınız ve tüm kullanılabilir seçeneklerin açılan seçim kutusunda görüntülendiği numaradır. Örneğin, TCP penceresi ölçeklendirmesinden endişeleniyorsanız, bu yolla bir filtreye (örneğin  `.protocol.tcp.window < 100`) giden yolu bulabilirsiniz.

![Görüntü Filtresi alanının intellisense kullandığını gösteren Netmon ekran görüntüsü.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Netmon izlemelerinde çok fazla trafik olabilir. Bunları okuma konusunda deneyimli değilseniz, büyük olasılıkla izlemeyi ilk kez açarken bunalmış olursunuz. yapılacak ilk şey, sinyali izlemedeki arka plan gürültüsünden ayırmaktır. Office 365 karşı test ettiyseniz, görmek istediğiniz trafik de bu şekildedir. İzlemelerde gezinmeye alışkınsanız, bu listeye ihtiyacınız olmayabilir.

İstemciniz ile Office 365 arasındaki trafik TLS üzerinden hareket eder, bu da trafiğin gövdesinin şifrelendiği ve genel bir Netmon izlemesinde okunamaz hale gelir. Performans analizinizin paketteki bilgilerin ayrıntılarını bilmesi gerekmez. Bununla birlikte, paket üst bilgileri ve içerdikleri bilgilerle çok ilgilidir.

### <a name="tips-to-get-a-good-trace"></a>İyi bir izleme almak için İpuçları

- İstemci bilgisayarınızın IPv4 veya IPv6 adresinin değerini bilin. **IpConfig** yazıp ENTER tuşuna basarak komut isteminden bunu alabilirsiniz. Bu adresi bilmek, izlemedeki trafiğin doğrudan istemci bilgisayarınızı içerip içermediğini bir bakışta anlamanızı sağlar. Bilinen bir ara sunucu varsa, ping yapın ve IP adresini de alın.

- DNS çözümleyici önbelleğinizi temizleyin ve mümkünse testlerinizi çalıştırdığınız tarayıcı dışında tüm tarayıcıları kapatın. Örneğin bunu yapamıyorsanız, örneğin destek istemci bilgisayarınızın masaüstünü görmek için tarayıcı tabanlı bir araç kullanıyorsa, izlemenizi filtrelemeye hazır olun.

- Yoğun bir izlemede, kullanmakta olduğunuz Office 365 hizmetini bulun. Trafiğinizi daha önce hiç veya nadiren gördüyseniz bu, performans sorununu diğer ağ gürültüsünden ayırmada yararlı bir adımdır. Bunu yapmanın birkaç yolu vardır. Testinizin hemen öncesinde, belirli bir hizmetin (`ping outlook.office365.com`veya gibi) URL'sinde _ping_ veya `psping -4 microsoft-my.sharepoint.com:443`_PsPing_ kullanabilirsiniz. Bu ping'i veya PsPing'i bir Netmon izlemesinde (işlem adına göre) kolayca da bulabilirsiniz. Bu sana aramaya başlamak için bir yer verir.

Sorun sırasında yalnızca Netmon izlemeyi kullanıyorsanız, bu da sorun değil. Kendinizi yönlendirmek için veya `ContainsBin(FrameData, ASCII, "outlook")`gibi `ContainsBin(FrameData, ASCII, "office")` bir filtre kullanın. Çerçeve numaranızı izleme dosyasından kaydedebilirsiniz. _Çerçeve Özeti_ bölmesini sağa doğru kaydırmak ve Konuşma Kimliği sütununu aramak da isteyebilirsiniz. Burada, bu özel konuşmanın kimliği için daha sonra kaydedebileceğiniz ve yalıtılmış olarak bakabileceğiniz bir sayı gösterilir. Başka bir filtreleme uygulamadan önce bu filtreyi kaldırmayı unutmayın.

> [!TIP]
> Netmon'da birçok yararlı yerleşik filtre vardır. _Filtre_ görüntüle bölmesinin üst kısmındaki **Filtreyi Yükle** düğmesini deneyin.

![İstemci bilgisayardaki komut satırında PSPing kullanarak IP'nizi bulun.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![İstemciden gelen netmon izlemesi, TCP filtresi aracılığıyla aynı PSPing komutunu gösterir. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Trafiğinizi öğrenin ve ihtiyacınız olan bilgileri bulmayı öğrenin. Örneğin, izlemedeki hangi paketin kullandığınız Office 365 hizmetine ilk başvuruya sahip olduğunu belirlemeyi öğrenin ("Outlook" gibi).

Office 365 Outlook Online'ı örnek olarak ele alarak trafik şu şekilde başlar:

- Eşleşen QueryID'lere sahip outlook.office365.com için DNS Standart Sorgusu ve DNS Yanıtı. Bu geri dönüş için zaman farkının yanı sıra Office 365 Genel DNS'nin ad çözümleme isteğini dünyanın neresinde gönderdiğini not etmek önemlidir. İdeal olarak, dünyanın yarısının ortasından çok, mümkün olduğunca yerel olarak.

- Durum raporu Kalıcı Olarak Taşınan BIR HTTP GET İsteği (301)

- RWS Bağlan istekleri ve Bağlan yanıtları içeren RWS Trafiği. (Bu, sizin için bağlantı yapan Uzak Winsock'tır.)

- TCP SYN ve TCP SYN/ACK konuşması. Bu konuşmadaki ayarların çoğu performansınızı etkiler.

- Ardından TLS el sıkışması ve TLS sertifika konuşmalarının gerçekleştiği bir dizi TLS:TLS trafiği. (Verilerin SSL/TLS aracılığıyla şifrelenmesini unutmayın.)

Trafiğin tüm bölümleri önemlidir ve bağlantılıdır, ancak izlemenin küçük bölümleri performans sorunlarını giderme açısından özellikle önemli bilgiler içerir, bu nedenle bu alanlara odaklanacağız. Ayrıca Microsoft'ta sık karşılaşılan sorunların ilk on listesini derlemek için yeterli Office 365 performans sorunlarını giderme işlemi yaptığımızdan, bu sorunlara ve bunları kökten çıkarmak için sahip olduğumuz araçları nasıl kullanacağımıza odaklanacağız.

Tümünü hazır olarak yüklemediyseniz aşağıdaki matris birkaç aracı kullanır. Mümkün olduğunda. Yükleme noktalarına bağlantılar sağlanır. Listede [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) ve [Wireshark](https://www.wireshark.org/) gibi yaygın ağ izleme araçları bulunur, ancak rahatça kullanabileceğiniz ve ağ trafiğini filtrelemeye alışkın olduğunuz herhangi bir izleme aracını kullanabilirsiniz. Test ederken şunları unutmayın:

- *Tarayıcılarınızı kapatın ve yalnızca bir tarayıcı çalıştırarak test*  edin- Bu, yakaladığınız genel trafiği azaltır. Daha az meşgul bir izleme yapar.
- *İstemci bilgisayarda DNS çözümleyici önbelleğinizi temizleyin*  - Bu, daha temiz bir izleme için yakalamaya başladığınızda size temiz bir sayfa sağlar.

## <a name="common-issues"></a>Yaygın sorunlar

Karşılaşabileceğiniz bazı yaygın sorunlar ve bunları Ağ izlemenizde bulma.

### <a name="tcp-windows-scaling"></a>TCP Windows Ölçeklendirme

SYN - SYN/ACK içinde bulunur. Eski veya eskiyen donanımlar TCP pencereleri ölçeklendirmeden yararlanamayabilir.  Uygun TCP pencereleri ölçeklendirme ayarları olmadan, TCP üst bilgilerindeki varsayılan 16 bit arabellek milisaniye cinsinden doldurulur.  İstemci, özgün verilerin alındığına dair bir bildirim alıncaya kadar trafik göndermeye devam edemez ve bu da gecikmelere neden olur.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Aranacaklar

Ağ izlemenizde SYN - SYN/ACK trafiğini arayın.  Netmon'da gibi  `tcp.flags.syn == 1`bir filtre kullanın. Bu filtre Wireshark'ta aynıdır.

![Her iki araç için de Netmon veya Syn paketleri için Wireshark filtreleyin: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Her SYN için ilgili Bildirim'in (SYN/ACK) hedef bağlantı noktasında (DstPort) eşleşen bir kaynak bağlantı noktası (SrcPort) numarası olduğuna dikkat edin.

Ağ bağlantınız tarafından kullanılan Windows Ölçeklendirme değerini görmek için önce SYN'yi ve ardından ilgili SYN/ACK'yi genişletin.

![Zaman değişimlerini elde etmek için bir izlemede SrcPort ile DstPort'un nasıl eşleştirildiğini gösteren grafik.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>TCP Boşta Kalma Süresi Ayarlar

Geçmişe dönük olarak, çoğu çevre ağı geçici bağlantılar için yapılandırılır, yani boştaki bağlantılar genel olarak sonlandırılır. Boştaki TCP oturumları proxy'ler ve güvenlik duvarları tarafından 100 ile 300 saniyeden daha uzun bir süre arasında sonlandırılabilir. Boşta olsalar da olmasalar da uzun süreli bağlantılar oluşturup kullandığından bu durum Outlook Online için sorunludur.

Bağlantılar ara sunucu veya güvenlik duvarı cihazları tarafından sonlandırıldığında istemciye bilgi verilmez ve Outlook Online'ı kullanma girişimi, istemci bilgisayarın yeni bir bağlantı kurmadan önce bağlantıyı yeniden canlandırmayı tekrar tekrar deneyeceği anlamına gelir. Üründe askıda kalmalar, istemler veya sayfa yükleme performansında yavaşlık görebilirsiniz.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Aranacaklar

Netmon'da gidiş dönüş için Zaman Farkı alanına bakın. Gidiş dönüş, istemcinin sunucuya istek göndermesi ile geri yanıt alması arasındaki süredir. İstemci ile çıkış noktası (örn. İstemci --\> Ara Sunucu) veya Office 365 İstemcisi (İstemci --\> Office 365). Bunu birçok paket türünde görebilirsiniz.

Örneğin, Netmon'daki filtre , veya Wireshark'ta `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`gibi `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`görünebilir.

> [!TIP]
> İzlemenizdeki IP adresinin DNS sunucunuza ait olup olmadığını bilmiyor musunuz? Komut satırında aramayı deneyin. **Çalıştırmayı** \> **Başlat'a** \> tıklayın ve **cmd** yazın veya **Windows Tuşuna** \> basın ve **cmd** yazın. İstemde yazın  `nslookup <the IP address from the network trace>`. Test etmek için, kendi bilgisayarınızın IP adresinde nslookup kullanın. > Microsoft'un IP aralıklarının listesini görmek için bkz. [OFFICE 365 URL'leri ve IP adresi aralıkları](./urls-and-ip-address-ranges.md).

Bir sorun varsa, özellikle Uygulama Verilerinin geçişini gösteren TLS:TLS paketlerinde (örneğin, Netmon'da uygulama veri paketlerini aracılığıyla `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`bulabilirsiniz) bu durumda (Outlook Online) uzun Zaman Farklarının görünmesini bekleyin. Oturum boyunca zaman içinde sorunsuz bir ilerleme görmeniz gerekir. Outlook Online'ınızı yenilerken uzun gecikmeler görürseniz, bunun nedeni yüksek düzeyde sıfırlamaların gönderilmesi olabilir.

### <a name="latencyround-trip-time"></a>Gecikme/Gidiş Dönüş Süresi

Gecikme süresi, eskiyen cihazları yükseltme, ağa çok sayıda kullanıcı ekleme ve ağ bağlantısındaki diğer görevler tarafından kullanılan genel bant genişliği yüzdesi gibi birçok değişkene bağlı olarak çok fazla değişiklik gösterebilen bir ölçüdür.

Office 365 için ağ [planlama ve performans ayarlama](network-planning-and-performance.md) sayfasında Office 365 için bant genişliği hesaplayıcıları vardır.

Bağlantınızın hızını veya ISS bağlantınızın bant genişliğini ölçmeniz mi gerekiyor? Bu siteyi (veya bunun gibi siteleri) deneyin: [Speedtest Resmi Sitesi](https://www.speedtest.net/) veya tümcecik **hız testi** için favori arama motorunuzu sorgulayın.

#### <a name="tools"></a>Araçlar

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Aranacaklar

bir izlemedeki gecikme süresini izlemek için istemci bilgisayarın IP adresini ve DNS sunucusunun IP adresini Office 365 kaydettikten yararlanabilirsiniz. Bu, daha kolay izleme filtrelemesi için kullanılır. Bir ara sunucu üzerinden bağlanırsanız, işi kolaylaştırmak için istemci bilgisayarınızın IP adresine, ara sunucu/çıkış IP adresine ve Office 365 DNS IP adresine ihtiyacınız olacaktır.

outlook.office365.com gönderilen bir ping isteği, ticari markanın ardışık ICMP paketlerini göndermek için bağlanamasa bile isteği alan veri  merkezinin adını size söyler. PsPing (ücretsiz indirme aracı) ve belirli bir bağlantı noktası (443) ve belki de IPv4 (-4) kullanıyorsanız, gönderilen paketler için ortalama gidiş dönüş süresi elde edersiniz. Bu, gibi `psping -4 yourSite.sharepoint.com:443`Office 365 hizmetlerindeki diğer URL'lerde bu işe yarayacaktır. Aslında, ortalamanız için daha büyük bir örnek almak için bir dizi ping belirtebilirsiniz, gibi `psping -4 -n 20 yourSite-my.sharepoint.com:443`bir şey deneyin.

> [!NOTE]
> PsPing, ICMP paketleri göndermez. Tcp paketlerine belirli bir bağlantı noktası üzerinden ping gönderir, böylece açık olduğunu bildiğiniz herhangi bir bağlantı noktasını kullanabilirsiniz. SSL/TLS kullanan Office 365'da PsPing'inize :443 bağlantı noktası eklemeyi deneyin.

![outlook.office365.com çözümleyen ping'i ve 443'lü psping'i gösteren ve aynı zamanda ortalama 6,5ms ortalama RTT'yi bildiren ekran görüntüsü.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Ağ izlemesi yaparken yavaş çalışan Office 365 sayfasını yüklediyseniz, için `DNS`bir Netmon veya Wireshark izlemesini filtrelemeniz gerekir. Bu, aradığımız IP'lerden biridir.

IP adresini almak için Netmon'unuzu filtrelemek için atılması gereken adımlar aşağıdadır (ve DNS Gecikme Süresi'ne göz atın). Bu örnek outlook.office365.com kullanır, ancak SharePoint Online kiracısının URL'sini de kullanabilir (örneğin hithere.sharepoint.com).

1. URL'ye `ping outlook.office365.com` ping atın ve sonuçlarda ping isteğinin gönderildiği DNS sunucusunun adını ve IP adresini kaydedin.
2. Sayfayı açan ağ izlemesi veya performans sorununu size veren eylemi gerçekleştirme ya da ping üzerinde yüksek gecikme süresi görürseniz ağ izlemesi.
3. İzlemeyi Netmon'da açın ve DNS için filtreleyin (bu filtre Wireshark'ta da çalışır, ancak büyük/küçük harfe `-- dns`duyarlıdır). Ping'inizden DNS sunucusunun adını bildiğiniz için, Netmon'da şu şekilde daha hızlı filtreleyebilirsiniz: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`, Wireshark dns ve frame'te şuna benzer şekilde "namnorthwest" içerir.<br/>Yanıt paketini açın ve Netmon **Çerçeve Ayrıntıları** penceresinde **DNS'ye** tıklayarak daha fazla bilgi için genişletin. DNS bilgilerinde, isteğin Office 365 gittiği DNS sunucusunun IP adresini bulacaksınız. Sonraki adım (PsPing aracı) için bu IP adresine ihtiyacınız olacaktır. Filtreyi kaldırın, DNS Sorgusu ve Yanıtı'nı yan yana görmek için Netmon'da DNS Yanıtı'na (**Çerçeve Özeti** \> **Konuşmaları** \> Bul **DNS**) sağ tıklayın.
4. Netmon'da, DNS İsteği ile Yanıt arasındaki Zaman Uzaklığı sütununu da not edin. Sonraki adımda, kurulumu ve kullanımı kolay [PsPing](/sysinternals/downloads/psping) aracı, hem ICMP genellikle Güvenlik Duvarları'nda engellendiğinden hem de PsPing gecikme süresini milisaniye cinsinden zarif bir şekilde izlediğinden çok kullanışlıdır. PsPing bir adrese ve bağlantı noktasına tcp bağlantısını tamamlar (bizim örneğimizde 443 numaralı bağlantı noktasını aç).
5. PsPing'i yükleyin.
6. Bir komut istemi açın (Çalıştırma \> türü cmd'sini başlatın \> veya Windows Anahtar \> türü cmd) ve PsPing komutunu çalıştırmak için psping'i yüklediğiniz dizinle değiştirin. Örneklerimde C kökünde bir 'Perf' klasörü yaptığım görebilirsiniz. Hızlı erişim için de aynı işlemi yapabilirsiniz.
7. Komutunu yazarak PsPing'inizi önceki Netmon izlemenizdeki Office 365 DNS sunucusunun IP adresiyle (gibi `psping -n 20 132.245.24.82:445`bağlantı noktası numarası dahil) karşı oluşturuyorsunuz. Bu size 20 ping örneklemesi verir ve PsPing durduğunda gecikme süresinin ortalamasını alırsınız.

Ara sunucu üzerinden Office 365 yapacaksanız adımlar biraz farklıdır. Proxy/çıkış ve geri için milisaniye cinsinden ortalama gecikme süresi değerini almak için önce proxy sunucunuza PsPing uygularsınız ve ardından eksik değeri (Office 365 ve geri) almak için PsPing'i proxy'de veya doğrudan İnternet bağlantısı olan bir bilgisayarda çalıştırırsınız.

Proxy'den PsPing çalıştırmayı seçerseniz, iki milisaniye değeriniz olur: İstemci bilgisayardan ara sunucuya veya çıkış noktasına ve ara sunucu Office 365. Ve işin bitti! Değerleri kaydetmeye devam et.

PsPing'i İnternet'e doğrudan bağlantısı olan başka bir istemci bilgisayarda çalıştırırsanız, yani ara sunucu olmadan iki milisaniye değeriniz olur: İstemci bilgisayardan ara sunucuya veya çıkış noktasına ve istemci bilgisayar Office 365. Bu durumda, istemci bilgisayarın değerini proxy sunucuya veya çıkış noktasına istemci bilgisayarın değerinden Office 365 çıkarın ve RTT numaralarını istemci bilgisayarınızdan ara sunucuya veya çıkış noktasına, ara sunucudan veya çıkış noktasından Office 365'ye sahip olursunuz.

Ancak, etkilenen konumda doğrudan bağlı olan bir istemci bilgisayar bulabilir veya ara sunucuyu atlarsanız, sorunun başlangıçta orada yeniden üretilip üretmediğini görmeyi ve bundan sonra kullanmayı test etmeyi seçebilirsiniz.

Netmon izlemesinde görüldüğü gibi gecikme süresi, belirli bir oturumda yeterli sayıda varsa bu fazladan milisaniyeler eklenebilir.

![Netmon'da genel gecikme süresi; Netmon varsayılan Zaman Aralığı sütunu Çerçeve Özeti'ne eklenir.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> IP adresiniz burada gösterilen IP'lerden farklı olabilir, örneğin ping'iniz 157.56.0.0/16 veya benzer bir aralık döndürebilir. Office 365 tarafından kullanılan aralıkların listesi için [Office 365 URL'leri ve IP adresi aralıklarını](./urls-and-ip-address-ranges.md) gözden geçirin.

Örneğin 132.245 için arama yapmak istiyorsanız tüm düğümleri genişletmeyi unutmayın (bunun üst kısmında bir düğme vardır).

### <a name="proxy-authentication"></a>Proxy Kimlik Doğrulaması

Bu, yalnızca bir ara sunucu üzerinden geçiyorsanız sizin için geçerlidir. Aksi takdirde bu adımları atlayabilirsiniz. Düzgün çalışırken, ara sunucu kimlik doğrulaması milisaniye cinsinden tutarlı bir şekilde gerçekleşmelidir. Yoğun kullanım dönemlerinde (örneğin) aralıklı kötü performans görmemeniz gerekir.

Ara sunucu kimlik doğrulaması açıksa, bilgi almak için Office 365 her yeni TCP bağlantısı yaptığınızda arka planda bir kimlik doğrulama işleminden geçmeniz gerekir. Örneğin, Outlook Online'da Takvim'den Posta'ya geçiş yaparken kimlik doğrulaması yaparsınız. SharePoint Online'da bir sayfada birden çok site veya konumdan medya veya veri görüntüleniyorsa, verileri işlemek için gereken her farklı TCP bağlantısı için kimlik doğrulaması yaparsınız.

Outlook Online'da, Takvim ile posta kutunuz arasında geçiş yaptığınızda yavaş yükleme süreleri yaşayabilir veya SharePoint Online'da yavaş sayfa yüklemeleri yaşayabilirsiniz. Ancak, burada listelenmeyen başka belirtiler de vardır.

Proxy kimlik doğrulaması, çıkış proxy sunucunuzda bir ayardır. Office 365 ile ilgili bir performans sorununa neden oluyorsa ağ ekibinize danışmanız gerekir.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Aranacaklar

Proxy kimlik doğrulaması, genellikle sunucudan dosya veya bilgi istemek ya da bilgi sağlamak için yeni bir TCP oturumunun yüklenmesi gerektiğinde gerçekleşir. Örneğin, HTTP GET veya HTTP POST isteklerinde ara sunucu kimlik doğrulaması görebilirsiniz. İzlemenizde isteklerin kimliğini doğruladığınız çerçeveleri görmek istiyorsanız, Netmon'a 'NTLMSSP Özeti' sütununu ekleyin ve için  `.property.NTLMSSPSummary`filtreleyin. Kimlik doğrulamasının ne kadar sürdüğünü görmek için Zaman Aralığı sütununu ekleyin.

Netmon'a sütun eklemek için:

1. **Açıklama** gibi bir sütuna sağ tıklayın.
2. **Sütunları Seç'e** tıklayın.
3. Listede _NTLMSSP Özeti_ ve _Zaman Aralığı'nı_ bulun ve **Ekle'ye** tıklayın.
4. Yeni sütunları yan yana okuyabilmeniz için _Açıklama_ sütununun önüne veya arkasına taşıyın.
5. **Tamam**'a tıklayın.

Sütunu eklemeseniz bile Netmon filtresi çalışır. Ancak kimlik doğrulamasının hangi aşamasında olduğunuzu görebiliyorsanız sorun gidermeniz çok daha kolay olacaktır.

Ara Sunucu Kimlik Doğrulaması örneklerini ararken, NTLM Sınaması veya Kimlik Doğrulama İletisi bulunan tüm çerçeveleri incelediğinizden emin olun. Gerekirse, belirli bir trafik parçasına sağ tıklayın ve Konuşmaları \> Bul TCP. Bu Konuşmalardaki Zaman Aralığı değerlerine dikkat edin.

![Konuşmaya göre filtrelenmiş ara sunucu kimlik doğrulamasını gösteren Netmon izlemesi.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Wireshark'ta görüldüğü gibi proxy kimlik doğrulamasında dört saniyelik gecikme. **Önceki görüntülenen kare sütunundaki Zaman aralığı, çerçeve** ayrıntılarında aynı addaki alana sağ tıklayıp Sütun Olarak Ekle seçerek yapıldı.  <br/> ![Wireshark'ta 'Önceki görüntülenen çerçeveden zaman aralığı' sütunu, çerçeve ayrıntılarında aynı addaki alana sağ tıklayıp Sütun Olarak Ekle'yi seçerek yapılabilir.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS Performansı

Ad çözümleme, müşterinin ülkesine mümkün olduğunca yakın bir yerde gerçekleştiğinde en iyi ve en hızlı şekilde çalışır.

DNS ad çözümlemesi denizaşırı bir yerde gerçekleştiriliyorsa, sayfa yüklemelerine saniyeler ekleyebilir. İdeal olarak, ad çözümlemesi 100m'nin altında gerçekleşir. Aksi takdirde, daha fazla araştırma yapmalısınız.

> [!TIP]
> İstemci Bağlantısı'nın Office 365 nasıl çalıştığından emin değil misiniz? [burada](/previous-versions//dn741250(v=technet.10)) İstemci Bağlantısı Başvurusu belgesine göz atın.

#### <a name="tools"></a>Araçlar

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Aranacaklar

DNS performansını analiz etmek genellikle bir ağ izlemesi için başka bir iştir. Ancak PsPing, olası bir nedeni karara varma veya çıkarma açısından da yararlıdır.

DNS trafiği TCP ve UDP isteklerini temel alır ve yanıtlar, belirli bir isteğin belirli yanıtıyla eşleşmesine yardımcı olacak bir kimlikle açıkça işaretlenir. Örneğin, SharePoint Online bir web sayfasında ağ adı veya URL kullandığında DNS trafiğini görürsünüz. Kural olarak, Bölgeleri aktarma dışında bu trafiğin çoğu UDP üzerinden çalışır.

Hem Netmon hem de Wireshark'ta, DNS trafiğine bakmanıza olanak sağlayacak en temel filtre basitçedır `dns`. Filtreyi belirtirken küçük harf kullandığınızdan emin olun. Sorunu istemci bilgisayarınızda yeniden oluşturmaya başlamadan önce DNS çözümleyici önbelleğinizi temizlemeyi unutmayın. Örneğin, Giriş sayfası için yavaş SharePoint Çevrimiçi sayfa yükünüz varsa, tüm tarayıcıları kapatmanız, yeni bir tarayıcı açmanız, izlemeye başlamanız, DNS çözümleyici önbelleğinizi temizlemeniz ve SharePoint Online sitenize göz atmalısınız. Sayfanın tamamı çözümlenince izlemeyi durdurmanız ve kaydetmeniz gerekir.

![Netmon'da DNS için temel bir filtre DNS'dir.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Burada zaman uzaklığını görmek istiyorsunuz. Ayrıca, şu adımları tamamlayarak yapabileceğiniz **Zaman Aralığı** sütununu Netmon'a eklemek yararlı olabilir:

1. **Açıklama** gibi bir sütuna sağ tıklayın.
2. **Sütunları Seç'e** tıklayın.
3. Listede _Zaman Aralığı'nı_ bulun ve **Ekle'ye** tıklayın.
4. Yan yana okuyabilmeniz için yeni sütunu _Açıklama_ sütununun önüne veya arkasına taşıyın.
5. **Tamam**'a tıklayın.

İlgilendiğiniz bir sorgu bulursanız, çerçeve ayrıntıları panelinde söz konusu sorguya sağ tıklayıp **Konuşma bul** \> **DNS'sini** seçerek bu sorguyu yalıtmayı göz önünde bulundurun. Ağ Konuşmaları panelinin UDP trafiği günlüğünde doğrudan belirli bir konuşmaya atlandığını görebilirsiniz.

![DNS tarafından filtrelenmiş Outlook Çevrimiçi yükünün Netmon izlemesi ve sonuçları daraltmak için Konuşma Bul'u ve ardından DNS'yi kullanma.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

Wireshark'ta DNS süresi için bir sütun oluşturabilirsiniz. Wireshark'ta izlemenizi alın (veya bir izleme açın) ve veya daha yararlı bir şekilde `dns.time`filtreleyin`dns`. Herhangi bir DNS sorgusuna tıklayın ve ayrıntıların gösterildiği panelde  `Domain Name System (response)` ayrıntıları genişletin. Zaman için bir alan görürsünüz (örneğin, `[Time: 0.001111100 seconds]`. Bu kez sağ tıklayın ve **Sütun Olarak Uygula'yı** seçin. Bu, izlemenizin daha hızlı sıralanması için size bir **Time** sütunu verir. Hangi DNS çağrısının çözülmesinin en uzun sürdüğünü görmek için azalan değerlere göre sıralamak için yeni sütuna tıklayın.

[Wireshark'ta dns.time değerine (küçük harf) göre filtrelenmiş SharePoint Online'a göz atma; ayrıntılardaki süre bir sütuna dönüştürülür ve artan düzende sıralanır.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

DNS çözümleme süresi hakkında daha fazla araştırma yapmak isterseniz, TCP tarafından kullanılan DNS bağlantı noktasına karşı bir PsPing deneyin (örneğin,  `psping <IP address of DNS server>:53`) . Hala bir performans sorunu görüyor musunuz? Bunu yaparsanız, sorunun çözümü yapmak için bastığınız BELIRLI DNS uygulamasıyla ilgili bir sorundan daha geniş bir ağ sorunu olma olasılığı daha yüksektir. Ayrıca, outlook.office365.com'a yapılan bir ping'in size Outlook Online için DNS ad çözümlemenin nerede gerçekleştiğini (örneğin, outlook-namnorthwest.office365.com) göstereceğini de belirtmek gerekir.

Sorun DNS'ye özgü gibi görünüyorsa, bu sorunu daha fazla araştırmak için DNS yapılandırmalarına ve DNS İleticilerine bakmak için BT bölümünüze başvurmanız gerekebilir.

### <a name="proxy-scalability"></a>Ara Sunucu Ölçeklenebilirliği

Office 365'da Outlook Online gibi hizmetler istemcilere birden çok uzun süreli bağlantı verir. Bu nedenle, her kullanıcı daha uzun bir yaşam gerektiren daha fazla bağlantı kullanabilir.

#### <a name="tools"></a>Araçlar

Matematik

#### <a name="what-to-look-for"></a>Aranacaklar

Buna özgü bir ağ izleme veya sorun giderme aracı yoktur. Bunun yerine, sınırlamalar ve diğer değişkenler verilen bant genişliği hesaplamalarını temel alır.

### <a name="tcp-max-segment-size"></a>TCP En Büyük Segment Boyutu

SYN - SYN/ACK içinde bulunur.  Tcp paketlerinin mümkün olan en fazla veri miktarını taşıyacak şekilde yapılandırıldığından emin olmak için, bu denetimi yaptığınız performans ağ izlemelerinde yapın.

Amaç, verilerin iletimi için 1460 bayt mss görmektir. Ara sunucu arkasındaysanız veya NAT kullanıyorsanız, en iyi sonuçları elde etmek için bu testi istemciden proxy/çıkış/NAT'ye ve ara sunucu/çıkış/NAT'den Office 365 çalıştırmayı unutmayın! Bunlar farklı TCP oturumlarıdır.

#### <a name="tools"></a>Araçlar

Netmon

#### <a name="what-to-look-for"></a>Aranacaklar

TCP Maksimum Segment Boyutu (MSS), ağ izlemenizdeki üç yönlü el sıkışmasının bir diğer parametresidir; bu da ihtiyacınız olan verileri SYN - SYN/ACK paketinde bulacağınız anlamına gelir. MSS'yi görmek oldukça kolaydır.

Sahip olduğunuz tüm performans ağ izlemelerini açın ve merak ettiğiniz veya performans sorununu gösteren bağlantıyı bulun.

> [!NOTE]
> İzlemeye bakıyorsanız ve konuşmanızla ilgili trafiği bulmanız gerekiyorsa İstemci'nin IP'sine, ara sunucunun veya çıkış noktasının IP'sine ya da her ikisine de göre filtreleyin. Doğrudan giderek, izlemedeki Office 365 IP adresi için test ettiğiniz URL'ye ping göndermeniz ve buna göre filtrelemeniz gerekir.

İzlere ikinci el mi bakıyorsun? Kendinizi yönlendirmek için filtreleri kullanmayı deneyin. Netmon'da URL'yi temel alan bir arama çalıştırın; örneğin `Containsbin(framedata, ascii, "sphybridExample")`, çerçeve numarasını not alın.

Wireshark'ta gibi  `frame contains "sphybridExample"`bir şey kullanın. Wireshark'ta Uzak Winsock (RWS) trafiği bulduğunuzu fark ederseniz (Wireshark'ta [PSH, ACK] olarak görünebilir), daha önce açıklandığı gibi RWS bağlantıları ilgili SYN - SYN/ACK'lerden kısa süre önce görülebilir.

Bu noktada, çerçeve numarasını kaydedebilir, filtreyi bırakabilir, Netmon'daki Ağ Konuşmaları penceresinde **Tüm Trafik'e** tıklayarak en yakın SYN'ye bakabilirsiniz.

Daha da önemlisi, izleme sırasında IP adresi bilgilerinden hiçbirini almadıysanız, izlemede URL'nizi bulmak (örneğin, öğesinin `sphybridExample-my.sharepoint.com`bir parçası) size filtrelemeniz için IP adresleri verir.

İzlemede görmek istediğiniz bağlantıyı bulun. Bunu, izlemeyi tarayarak, IP adreslerine göre filtreleyerek veya Netmon'daki Ağ Konuşmaları penceresini kullanarak belirli Konuşma Kimliklerini seçerek yapabilirsiniz. SYN paketini bulduğunuzda, Çerçeve Ayrıntıları panelinde TCP (Netmon'da) veya İletim Denetimi Protokolü'ne (Wireshark'ta) genişletin. TCP Seçenekleri ve MaxSegmentSize seçeneklerini genişletin. İlgili SYN-ACK çerçevesini bulun ve TCP Seçenekleri ve MaxSegmentSize'ı genişletin. İki değerin küçük kısmı En Büyük Segment Boyutunuz olur. Bu resimde, Netmon'da TCP Sorun Giderme adlı yerleşik Sütunu kullanıyorum.

![Yerleşik sütunlar kullanılarak Netmon'da filtrelenen ağ izlemesi.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Yerleşik sütun **, Çerçeve Ayrıntıları** panelinin en üstünde yer alır. (Normal görünümünüze geri dönmek için **Sütunlar'a** yeniden tıklayın ve **saat dilimi'ni** seçin.)

![TCP Sorun Giderme seçeneği için Sütunlar açılan listesinin bulunduğu yer (Çerçeve Özeti'nin üstünde).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

İşte Wireshark'ta filtrelenmiş bir izleme. MSS değerine (`tcp.options.mss`) özgü bir filtre vardır. Syn, SYN/ACK, ACK el sıkışmasının çerçeveleri, Çerçeve Ayrıntılarına eşdeğer Wireshark'ın alt kısmında bağlanır (çerçeve 47 ACK, 46 SYN/ACK'ye bağlantılar, 43 SYN'ye bağlantılar) bu tür işleri kolaylaştırmak için.

![Wireshark'ta En Büyük Segment Boyutu (MSS) için tcp.options.mss tarafından filtrelenen izleme.](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

**Seçmeli Bildirim'i** denetlemeniz gerekiyorsa (bu matristeki bir sonraki konu), izlemenizi kapatmayın!

### <a name="selective-acknowledgment"></a>Seçmeli Bildirim

SYN - SYN/ACK içinde bulunur. Hem SYN hem de SYN/ACK'de İzin Verilir olarak bildirilmelidir. Seçmeli Bildirim (SACK), bir paket veya paket eksik olduğunda verilerin daha sorunsuz bir şekilde yeniden iletimini sağlar. Cihazlar bu özelliği devre dışı bırakabilir ve bu da performans sorunlarına yol açabilir.

Ara sunucu arkasındaysanız veya NAT kullanıyorsanız, en iyi sonuçları elde etmek için bu testi istemciden proxy/çıkış/NAT'ye ve ara sunucu/çıkış/NAT'den Office 365 çalıştırmayı unutmayın! Bunlar farklı TCP oturumlarıdır.

#### <a name="tools"></a>Araçlar

Netmon

#### <a name="what-to-look-for"></a>Aranacaklar

Seçmeli Bildirim (SACK), SYN-SYN/ACK el sıkışmasında başka bir parametredir. SYN - SYN/ACK izlemenizi birçok şekilde filtreleyebilirsiniz.

İzlemeyi tarayarak, IP adreslerine göre filtreleyerek veya Netmon'daki Ağ Konuşmaları penceresini kullanarak konuşma kimliğine tıklayarak görmek istediğiniz izlemedeki bağlantıyı bulun. SYN paketini bulduğunuzda, Çerçeve Ayrıntıları bölümünde Netmon'da TCP'yi veya Wireshark'ta İletim Denetimi Protokolü'ni genişletin. TCP Seçenekleri'ni ve ardından SACK'i genişletin. İlgili SYN-ACK çerçevesini bulun ve TCP Seçeneklerini ve SACK alanını genişletin. Hem SYN hem de SYN/ACK'de belirli SACK'e izin verilir. Hem Netmon hem de Wireshark'ta görüldüğü gibi SACK değerleri aşağıdadır.

![Tcp.flags.syn == 1 sonucu olarak Netmon'da Seçmeli Bildirim (SACK).](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![Wireshark'ta tcp.flags.syn == 1 filtresiyle görüldüğü gibi SACK.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS Coğrafi Konumu

Dünyanın neresinde Office 365 DNS çağrınızı çözümlemeye çalışır bağlantı hızınızı etkiler.

Outlook Online'da, ilk DNS araması tamamlandıktan sonra, en yakın veri merkezinize bağlanmak için bu DNS'nin konumu kullanılır. Verilerinizin depolandığı veri merkezine (dC) bağlanmak için omurga ağını kullanan bir Outlook Çevrimiçi CAS sunucusuna bağlanacaksınız. Bu daha hızlı.

SharePoint Online'a erişirken, yurt dışında seyahat eden bir kullanıcı etkin veri merkezine yönlendirilir. Bu, konumu SPO kiracısının ana tabanına (kullanıcının ABD tabanlı olması durumunda ABD'de bir dC) dayanan dC'dir.

Lync Online'da aynı anda birden fazla dC'de etkin düğümler vardır. Lync çevrimiçi örnekleri için istek gönderildiğinde, Microsoft'un DNS'i isteğin dünyanın neresinden geldiğini belirler ve Lync Online'ın etkin olduğu en yakın bölgesel dC'den IP adreslerini döndürür.

> [!TIP]
> İstemcilerin Office 365 nasıl bağlanacakları hakkında daha fazla bilgi sahibi olmanız mı gerekiyor? [İstemci Bağlantısı](/previous-versions//dn741250(v=technet.10)) başvuru makalesine (ve yararlı grafiklerine) göz atın.

#### <a name="tools"></a>Araçlar

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Aranacaklar

İstemcinin DNS sunucularından Microsoft'un DNS sunucularına ad çözümleme istekleri çoğu durumda Microsoft DNS'nin bölgesel bir veri merkezinin (dC) IP adresini döndürmesine neden olmalıdır. Bu senin için ne anlama geliyor? Merkeziniz Hindistan'ın Bangalore kentindeyse ancak Birleşik Devletler seyahat ediyorsanız, tarayıcınız Outlook Online için istekte bulunduğunda Microsoft'un DNS sunucuları ip adreslerini bölgesel bir veri merkezi olan Birleşik Devletler veri merkezlerine teslim etmelidir. Outlook posta gerekiyorsa, bu veriler Microsoft'un veri merkezleri arasındaki hızlı omurga ağında gezinecektir.

Ad çözümlemesi kullanıcı konumuna mümkün olduğunca yakın olduğunda DNS en hızlı şekilde çalışır. Avrupa'daysanız, Avrupa'da bir Microsoft DNS'ye gitmek ve (ideal olarak) Avrupa'daki bir veri merkeziyle ilgilenmek istiyorsunuz. Avrupa'daki bir istemcinin DNS'ye ve Amerika'daki bir veri merkezine giden performansı daha yavaş olacaktır.

DNS isteğinizin dünyanın neresinde yönlendirildiğini belirlemek için Ping aracını outlook.office365.com karşı çalıştırın. Avrupa'daysanız, outlook-emeawest.office365.com gibi bir yanıt görmeniz gerekir. Amerika'da, outlook-namnorthwest.office365.com gibi bir şey beklersin.

İstemci bilgisayarda komut istemini açın (Başlatma \> Çalıştırma \> cmd veya Windows anahtar \> türü cmd aracılığıyla). ping outlook.office365.com yazın ve ENTER tuşuna basın. IPv4 aracılığıyla ping yapmak istiyorsanız -4 belirtmeyi unutmayın. ICMP paketlerinden yanıt alamayabilirsiniz, ancak isteğin yönlendirildiği DNS'nin adını görmeniz gerekir. Bu bağlantının gecikme numaralarını görmek istiyorsanız ping ile döndürülen sunucunun IP adresine PsPing uygulamayı deneyin.

![Outlook-namnorthwest'te çözünürlüğü gösteren outlook.office365.com ping'i.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![Ortalama 28 milisaniyelik gecikme süresini gösteren outlook.office365.com ping tarafından döndürülen IP adresine PSPing.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 Uygulama Sorunlarını Giderme

#### <a name="tools"></a>Araçlar

- Netmon
- HTTPWatch
- Tarayıcıda F12 Konsolu

Ağa özgü bu makalede uygulamaya özgü sorun gidermede kullanılan araçları ele almayacağız. Ancak [bu sayfada](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848) *kullanabileceğiniz* kaynaklar bulabilirsiniz.

## <a name="related-topics"></a>İlgili Konular

[Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)