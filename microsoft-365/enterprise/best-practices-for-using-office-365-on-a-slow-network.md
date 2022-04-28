---
title: Yavaş bir ağda Office 365 kullanmaya yönelik en iyi yöntemler
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Bu makale, yavaş bir ağda Office 365 kullanmak için benimseyebileceğiniz en iyi yöntemler konusunda size yol gösterir.
ms.openlocfilehash: 5ed3a9dfc665d5067fb3f310fc74aa4b100190f2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091643"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Yavaş bir ağda Office 365 kullanmaya yönelik en iyi yöntemler

İnternet bağlantınız her zaman hızlı olsa ve hiç kapanmasa iyi olmaz mıydı? Belki o gün gelecek. Ancak bu arada, bal gibi bir ağda çalışmak ve günlük işlerinizi halletmek için yapabileceğiniz pratik şeyler vardır. Office 365 bulut tabanlı bir hizmet olsa da, içeriğinizle çevrimdışı çalışmak ve değişikliklerinizi sorunsuz bir şekilde eşitlenmiş halde tutmak için birçok yol sağlar. Ayrıca, uygulamalar daha hızlı çalıştığı ve kullanıcı arabiriminin daha hızlı yanıt vermesine neden olduğu için içerikle çevrimdışı çalışmak bazen daha verimlidir. Önemli olan şu: Office 365 size her iki dünyanın da en iyilerini sunar. Bundan nasıl yararlanıldığını burada bulabilirsiniz.

> [!TIP]
> Ağ bağlantınızın ne kadar yavaş (veya hızlı) olduğunu görmek ister misiniz? [OOKLA Hız testini](https://www.speedtest.net/) veya [Ağ Hızı Testi Uygulamasını](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70) deneyin.

## <a name="why-is-my-network-so-slow"></a>Ağım neden bu kadar yavaş?

Ağ performansının kendisi üzerinde denetiminiz olmasa da, arka planda neler olduğunu anlamanıza yardımcı olur. İnternet son derece karmaşıktır, ancak durumu çok daha iyi anlamanıza yardımcı olabilecek birkaç kavram vardır. Bu makaledeki en iyi yöntemlerin takip etmek, performans sorunlarını geçici olarak çözmeye ve hayal kırıklığını azaltmaya yardımcı olabilir.

### <a name="major-factors-that-affect-network-performance"></a>Ağ performansını etkileyen önemli faktörler

![Ağ Performansı Faktörleri.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Bant genişliği ve gecikme süresi**: Ağ performansının en önemli iki ölçüsü bant genişliği ve gecikme süresidir:

- Bant genişliği, saniye başına bit cinsinden ölçülen aktarım hızıdır. Daha büyük daha iyidir. Bant genişliği bir su borusu gibidir. Boru ne kadar büyükse, o kadar fazla su "içine koyabilirsiniz".

- Gecikme süresi, içeriğin bir sunucudan veya hizmetten cihazınıza gelmesi için geçen süredir ve milisaniye cinsinden ölçülür. Daha hızlı daha iyidir. Gecikme süresi düşük bant genişliği, seyrek bağlantı veya iletim süresi gibi çeşitli faktörlerden kaynaklanabilir.

 **Yaygın sorunlar**: Bant genişliği ve gecikme süresinin yanı sıra, diğer sorunlar ağ performansını etkiler ve genellikle öngörülemez. Ağ performansı günün saati veya fiziksel konumunuza göre dalgalanabilir. Doğal afet veya büyük bir genel olay gibi İnternet kullanımında ani artış gösteren bazı olaylar meydana geldiğinde ağ tıkanabilir. Yüklenen sayfanın boyutu ve karmaşıklığı ile aktarılan dosyaların sayısı ve boyutu performansı doğrudan etkileyebilir. WiFi bağlantısı geçici olarak düşebilir: Örneğin, herkesin aynı anda tweet atmalarını isteyerek binlerceden oluşan büyük bir konferans toplantısını yoklarsınız.

 **Uydu ağıyla ilgili dikkat edilmesi gerekenler**: Uydu ağı, karasal ağ arka ülke, yolcu gemisi veya uzak bilimsel alan gibi uygulanabilir olmadığında yararlıdır. Bu ağlar, ekvatordan 22.000 mil yukarıda jeosenkron bir yörüngede konumlandırılmış uyduları kullanır. Ancak, bir iletim aslında yaklaşık 90.000 mil ilerler ve bu nedenle uydu ağı, karasal bir ağa (20 ile 50 ms) göre daha yavaş bir gecikme süresine (500 ms veya daha fazla) sahiptir. En iyi koşullarda, bu gecikmeyi fark edemeyebilirsiniz, ancak büyük dosyaları indirmek, video akışı ve oyun oynamak için büyük olasılıkla fark edeceksiniz. Bir diğer sorun da fırtınalar ve tipi gibi ağır havaların uydu iletimini geçici olarak kesintiye uğratabileceği "yağmur solması"dır.

## <a name="are-you-sure-its-the-network"></a>Ağ olduğundan emin misin?

Performans sorunlarıyla karşılaştığınızda öncelikle sorunun kök nedeninin cihazınızın olmadığından emin olun. Büyük bir gelişme yaratabilecek iki şey yapabilirsiniz:

- Cihazınızın iyi çalıştığından ve bilgisayarınızda kötü amaçlı yazılım olmadığından emin olun.

- Mümkünse daha fazla bellek satın alın. Bellek eklemek, cihazınızda performansı artırmanın en basit ve çoğunlukla en etkili yoludur. Özellikle büyük dosya ve videolarla çalışırken yararlıdır.

Daha fazla bilgi için bkz[. Windows Performans ve bakım](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) ve [Windows 10 bilgisayar performansını geliştirmek için İpuçları](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Tarayıcınızı kullanmak için en iyi yöntemler

Tarayıcınız Office 365 için ağ geçidiniz olduğundan, özellikle bir sayfayı yükleme süresi ve Office 365 hizmetine gidiş dönüş yaptığınız sıklıkta performans üzerinde bir etkisi olabilir.

### <a name="browsers-in-general"></a>Genel olarak tarayıcılar

Genel olarak tarayıcılar için bazı öneriler şunlardır:

- Performansı etkileyebilecek veya gerçekten ihtiyacınız olmayan tarayıcı eklentilerini devre dışı bırakın.

- Geçici internet dosyalarınızın önbellek boyutunu artırın.

- İş veya okul hesabınızda oturum açtıktan sonra tarayıcı penceresini gün boyunca açık tutun. Yeniden oturum açmadan diğer sekmeleri ve pencereleri açabilirsiniz. Başka bir hesapta oturum açmanız gerekiyorsa Özel Gözatma'yı kullanın.

- Her sayfa indirilip açıldıktan sonra sekmeleri kullanarak bunları açık tutun. Sekmeler arasında gezinmek ve günün ilerleyen bölümlerinde sayfayı kullanmak kolaydır. Yalnızca bu sayfadaki en son verilere ihtiyacınız varsa sayfayı yenileyin.

- Bir sayfanın açılması çok uzun sürüyorsa, sayfa indirmeyi durdurun (ESC tuşuna basın) ve ardından sayfayı yenileyin (F5 tuşuna basın).

- Mümkün olduğunda gidiş dönüşleri Office 365 azaltın. Örneğin, listeler veya kitaplıklar arasında sayfalama yapmak yerine, büyük bir kitaplıktaki dosyaları bulmak için aramayı ve doğrudan istediğiniz sonuçlara ulaşmak için listede filtrelemeyi kullanın. Alternatif olarak, sayfa yükleme süresini en aza indiren görünümler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [Office 365'da büyük listeleri ve kitaplıkları yönetme](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Video performansı düşükse, videoyu indirip cihazınızda izleyebilirsiniz. İndirme bağlantısı kullanılabilir veya video bağlantısına sağ tıklayıp **Hedefi Farklı Kaydet'i** seçebilirsiniz.

### <a name="browser-specific"></a>Tarayıcıya özgü

Belirli tarayıcınız için bazı öneriler şunlardır:

- **Internet Explorer**: Önceki sürümlere göre önemli performans geliştirmeleri için Internet Explorer Sürüm 11 veya sonraki bir sürüme yükseltin. Daha fazla bilgi için bkz [. Internet Explorer için sorun giderme kılavuzu](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Daha fazla bilgi için bkz. [Firefox yavaş çalışıyor veya çalışmayı durduruyor](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Daha fazla bilgi için bkz. [Apple - Safari](https://www.apple.com/safari/).
- **Chrome**: Daha fazla bilgi için [Bkz. Chrome Yardımı](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Outlook ve Outlook Web App kullanmaya yönelik en iyi yöntemler

E-posta okumak, yazmak ve düzenlemek herkesin gününün önemli bir parçasıdır. Hem Outlook hem de Outlook Web App (OWA) çevrimdışı destek sunar. Akıllı telefonunuzda e-posta uygulaması kullanmak da başka bir yararlı alternatiftir. Gereksinimlerinize en uygun aşağıdaki seçenekleri kullanın:

- Önceki sürümlere göre önemli performans geliştirmeleri için Outlook en son sürümüne yükseltin.

- Outlook Web App, OWA bir sonraki Office 365 bağlanabildiğinde karşıya yüklenen çevrimdışı iletiler, kişiler ve takvim olayları oluşturmanıza olanak tanır. OWA'yı çevrimdışı modda ayarlama ve kullanma hakkında daha fazla bilgi için bkz. [Çevrimdışı Outlook Web App kullanma](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook, mümkün olduğunda otomatik olarak bağlandığı önbelleğe alınmış modda çalışmanızı sağlar. Posta kutunuzun tamamını veya yalnızca bir bölümünü Outlook indirmeniz gerekir. Daha fazla bilgi için bkz. [Önbelleğe Alınmış Exchange Modu'nu açma](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) ve [Outlook çevrimdışı çalışma](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook çevrimdışı mod da sunar. Bunu kullanmak için, önce hesabınızdaki bilgilerin bilgisayarınıza kopyalanacağı önbelleğe alınmış modu ayarlamanız gerekir. Çevrimdışı modda Outlook gönderme ve alma ayarlarını kullanarak veya çevrimiçi çalışacak şekilde el ile ayarladığınızda bağlanmayı dener. Daha fazla bilgi için bkz [. Veri bağlantısı ücretlerinden kaçınmak için çevrimdışı çalışma](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [Çevrimdışı çalışırken gönderme ve alma ayarlarını değiştirme](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) ve [Çevrimdışı çalışmadan çevrimiçine geçme](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Akıllı telefonunuz varsa, e-postanızı ve takviminizi telefon operatörünüzün ağı üzerinden önceliklendirmek için kullanabilirsiniz.

> [!NOTE]
> Outlook veya OWA'nın ne zaman kullanılacağına ilişkin bazı yönergeler aşağıda verilmiştir. Cihazınızda disk alanı sorun değilse, Outlook tam bir özellik kümesine sahiptir ve sizin için en iyi sonucu verebilir. Cihazınızda disk alanı sorunu varsa, özelliklerin bir alt kümesine sahip olan ama aynı zamanda çevrimiçi bir durumda en iyi şekilde çalışan OWA'yı kullanmayı göz önünde bulundurun. Elbette, birlikte iyi çalıştıkları için ikisini de kullanabilirsiniz.

## <a name="best-practices-for-using-onedrive-for-business"></a>OneDrive İş kullanmak için en iyi yöntemler

OneDrive İş, dosyalarınızı çevrimiçi ve çevrimdışı olarak kullanmak için sıfırdan tasarlanmıştır. Bunu ayarladıktan sonra, değişiklikleri yaptığınız her yerde ve her zaman otomatik ve güvenilir bir şekilde eşitler. Ağ yavaşsa, dosyaların çevrimdışı sürümüyle çalışabilirsiniz.

OneDrive İş eşitleme uygulaması SharePoint Online ve Office 365 iş aboneliğiyle birlikte gelir veya OneDrive İş eşitleme uygulamasını ücretsiz [olarak indirebilirsiniz](https://support.microsoft.com/kb/2903984). Bu uygulama, **Gezginde Aç** veya **Upload** komutlarını kullanmaktan da daha hızlıdır. Daha fazla bilgi için bkz. [Office 365'da OneDrive İş dosyalarınızı eşitlemek için bilgisayarınızı ayarlama](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

OneDrive İş eşitleme uygulamasını kullanmaya yönelik bazı ek yönergeler aşağıda verilmiştir:

- Büyük bir kitaplığı ilk kez eşitlüyorsanız, eşitlemeyi çalışma saatleri dışında (örneğin, gece) başlatın.
- Güncelleştirmeleri eşitlemeyi geçici olarak durdurmak için [Kitaplığı OneDrive İş uygulamasıyla](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) eşitlemeyi durdur özelliğini kullanabilirsiniz. Ancak bu özelliği, çok sayıda güncelleştirmesi kuyruğa almaktan kaçınmak ve aynı belge üzerinde birkaç kişi çalışıyorsa birleştirme çakışması riskini en aza indirmek için birkaç saat gibi kısa süreler için kullanın.

## <a name="best-practices-for-using-onenote"></a>OneNote kullanmak için en iyi yöntemler

Her SharePoint ekip sitesinde yerleşik bir OneNote not defteri vardır ve kolayca kendi not defterinizi oluşturabilirsiniz. OneNote, görevleri yerine getirmek için her gün ihtiyacınız olan zamanında bilgileri toplamanın harika bir yoludur. Örneğin, birçok ekip haftalık toplantılar, proje notları, fikirler, planlar ve durum raporları için koleksiyon noktası olarak OneNote kullanır. Sayfalar, bölümler ve sekmeler kullanarak bu farklı bilgileri düzgün bir şekilde düzenleyebilirsiniz.

OneNote güzelliği, içeriğe masaüstü, dizüstü bilgisayar, tablet veya akıllı telefon gibi hemen her cihazdan erişebilmenizdir. Kaydetme veya eşitleme konusunda endişelenmenize gerek yoktur çünkü OneNote sizin için yapar.

Daha fazla bilgi için bkz. [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Skype Kurumsal ve Lync Online'ı kullanmaya yönelik en iyi yöntemler

Ağınız yavaşken Skype Kurumsal veya Lync Online kullanmaya yönelik genel yönergeler aşağıdadır:

- Yavaş bir ağda düzgün çalıştığından, mümkün olduğunda anlık iletileri kullanın.

- Sanal özel ağ (VPN) veya uzaktan erişim hizmeti (RAS) bağlantıları üzerinden telefon aramaları yapmaktan kaçının.

- Ses cihazınızın onaylandığından emin olun. Daha fazla bilgi için bkz. [Microsoft Lync için Uygun Telefonlar ve Cihazlar](/skypeforbusiness/lync-cert/ip-phones).

- Çevrimiçi sunuda PowerPoint kullanırken slaytların boyutunu ve karmaşıklığını azaltın. Daha fazla bilgi için bkz. [Sununuzun performansını geliştirmek için İpuçları](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Video performansı ağ performansına çok bağlıdır. Ağınız yavaşsa video kullanmaktan kaçının.

Daha fazla bilgi için bkz. [Lync Online'da düşük ses veya video kalitesi](https://support.microsoft.com/kb/2386655) veya [Skype Kurumsal bağlantı sorunlarını giderme](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>SharePoint listelerini kullanmaya yönelik en iyi yöntemler

Verileri "temizlemek", analiz etmek veya raporlamak için liste verileriyle çevrimdışı çalışmak, yavaş bir ağın etkisini en aza indirmenin harika bir yoludur. Microsoft Access 2019 ve Microsoft Access 2016 listelerinin çoğunu bunlara bağlanarak okuyabilir ve yazabilirsiniz. Ayrıca, listeyi Excel tablosuyla liste arasında tek yönlü bir veri bağlantısı oluşturan Excel Tablosuna da aktarabilirsiniz. [SharePoint listelerine bağlı tablolarla çevrimdışı çalışmayı](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e) öğrenin.

Daha fazla bilgi için Office 365'de [büyük listeleri ve kitaplıkları yönetme bölümündeki "Büyük listeleri](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784) yönetme hakkında daha fazla bilgi" bölümüne bakın.

## <a name="best-practices-for-customizing-web-pages"></a>Web sayfalarını özelleştirmek için en iyi yöntemler

Bir web sayfasını özelleştirdiğinizde, istemeden sayfada düşük performansa neden olabilirsiniz. Sayfanın karmaşıklığı ve boyutu, eklenen web bölümü sayısı, başlangıçta kaç liste veya kitaplık öğesinin görüntülendiği ve sayfayı nasıl kodladığınız gibi bir dizi etkenin etkisi olabilir.

Daha fazla bilgi için bkz[. Çevrimiçi performans SharePoint ayarlama](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>Project Online kullanmak için en iyi yöntemler

Aşağıdaki yönergeler ağ performansını artırmaya yardımcı olabilir.

- Project Online ve SharePoint Online, zaman alıcı olabilecek eşitleme gerektirir. Proje ekiplerinizin cirosu düşükse, Project Yayımlama ve Ayrıntı Sayfaları performansını Project geliştirmek için Site Eşitleme Project devre dışı bırakın. Active Directory eşitlemesini sistemi kullanması gereken kaynak gruplarıyla sınırlayın ve büyük grupların eşitlenmesinden sonra olası izin sorunlarını izleyin.

- Kuruluşunuz proje sitelerini kullanıyorsa, bunları otomatik olarak değil isteğe bağlı olarak oluşturun. Bu, ilk yayımlama deneyimini hızlandırır ve gereksiz siteler ve içerik oluşturmaktan kaçınır.

- Project Ayrıntı Sayfaları (PDP), projenin tamamının yeniden hesaplanması tetiklenebilir ve her ikisi de yoğun performans gerektiren işlemler olabilecek iş akışı eylemlerini başlatabilir. Aynı PDP'de aynı anda iki güncelleştirme işlemini tetiklememek için takvim alanlarını (Başlangıç tarihi, Bitiş tarihi, Durum tarihi ve Geçerli tarih) ve zamanlanmamış alanları (proje adı, açıklama ve sahip) güncelleştirmekten kaçının.

- Her PDP'de görüntülenen Web Bölümleri ve özel alanların sayısını azaltın. Yükü geliştirmek ve zaman kazanmak için güncelleştirme gerektiren tek alanlara sahip ayrılmış bir PDP oluşturun.

- Raporlama için OData kullandığınızda, sunucu tarafı filtrelemeyi kullanarak çalışma zamanında sorguladığınız veri miktarını sınırlayın.

Daha fazla bilgi için bkz[. Project Online performansını ayarlama](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Sorunları bildirmenin en iyi yolu nedir?

Microsoft ağı izleyerek, bant genişliğini ve gecikme süresini ölçerek, sayfa yükleme süresini iyileştirerek, disk G/Ç'sini azaltarak, sayfaları Minimum İndirme Stratejisi'ni kullanacak şekilde yeniden tasarlayarak, veri merkezlerine donanım ekleyerek ve daha fazla veri merkezi ekleyerek Office 365 genel performansını sürekli olarak geliştirir. Geçerli durumunuzu denetleme ve sorun bildirme hakkında daha fazla bilgi için bkz. [Office 365 hizmet durumunu denetleme](view-service-health.md).

## <a name="see-also"></a>Ayrıca bkz.

[Network planning and performance tuning for Office 365](network-planning-and-performance.md)

[Office 365 Ağ Bağlantı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
