---
title: Yavaş bir ağ üzerinde Office 365 için en iyi yöntemler
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makale, yavaş bir ağ üzerinde e-posta ve güvenlik Office 365 yöntemleri konusunda size yol sağlar.
ms.openlocfilehash: 0b3b46bcc28b8c25f363268adfa720f4d1df47b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985008"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Yavaş bir ağ üzerinde Office 365 için en iyi yöntemler

İnternet bağlantınız her zaman hızlı ve hızlı olursa iyi olmaz mıydı? Belki o gün de gelir. Ancak bu arada, balklı bir ağın çevresinde çalışmak ve günlük işlerinizi yapmaya devam etmek için bazı pratik uygulamalar vardır. Office 365 bulut tabanlı bir hizmet olsa da, içeriğinizi çevrimdışı olarak çalışmak ve değişikliklerinizi sorunsuz bir şekilde eşitlemek için birçok yol sağlar. Bunun yanı sıra, yalnızca uygulamalar daha hızlı çalışır ve kullanıcı arabirimi daha hızlı yanıt verir. Önemli olan şudur: Office 365 her iki dünyanın da en iyisini sağlar. İşte bundan nasıl yararlan yararlanıy o kadar.

> [!TIP]
> Ağ bağlantının ne kadar yavaş (veya hızlı) olduğunu mu görmek istiyor musunuz? [OOKLA Hız testini veya](https://www.speedtest.net/) Ağ [Hız Testi Uygulamasını deneyin](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Ağım neden bu kadar yavaş?

Ağ performansının kendisinde bir denetimimiz yoktur, ancak sahne gerisinde neler olduğunu anlamak yardımcı olabilir. İnternet inanılmaz karmaşıktır, ancak durumu daha iyi anlamanıza yardımcı olacak birkaç kavram vardır. Bu makaledeki en iyi yöntemlerin takip etmek, performans sorunlarını geçici olarak çözmek ve sıkıntıyı azaltmak için yardımcı olabilir.

### <a name="major-factors-that-affect-network-performance"></a>Ağ performansını etkileyen önemli faktörler

![Ağ Performansı Etmenleri.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Bant genişliği ve gecikme** süresi: Ağ performansının en önemli iki önlemi, bant genişliği ve gecikme süresidir:

- Bant genişliği, saniye başına bit sayısıyla üretilen iş hızıdır. Ne kadar büyükse o kadar iyi olur. Bant genişliği, su borusu gibi bir alandır. Boru ne kadar büyükse, "içinden" o kadar fazla su geçenin.

- Gecikme süresi, içeriğin bir sunucu veya hizmetten cihazınıza süresidir ve mili saniye cinsinden ölçülür. Ne kadar hızlı olursa o kadar iyi olur. Düşük bant genişliği, seyrek bağlantı veya iletim süresi gibi bir dizi faktör gecikmeye neden olabilir.

 **Yaygın sorunlar**: Bant genişliği ve gecikme süresinin yanı sıra, diğer sorunların ağ performansı üzerindeki etkisi vardır ve çoğunlukla öngörülemez. Ağ performansı günün saatlerine veya fiziksel konumunuza bağlı olarak dalgalanmaya neden olabilir. Doğal afetler veya önemli bir kamu etkinliği gibi İnternet kullanımının artışa neden olduğu bazı olaylarda, ağ tıkanıklığı yaşanabilir. Yüklenen sayfanın boyutu ve karmaşıklığı, aktarılan dosyaların sayısı ve boyutu performansı doğrudan etkileyebilir. WiFi bağlantısının performansı geçici olarak düşebilir: örneğin, binlerce kişinin yer olduğu büyük bir konferans toplantısında herkesten aynı anda tweet atayın isteğinde bulundurarak yoklamalar yaptırabilirsiniz.

 **Uydu ağıyla** ilgili dikkate alınacak noktalar: Karasal ağ, geri ülke, yolcu gemisi veya uzaktaki bilimsel bölge gibi karasal ağın uygun olmadığını durumlarda yararlıdır. Bu ağlar, ekvatordan 22.000 mil yüksek bir coğrafi yörüngede bulunan uydulara dayanıyor. Öte yandan, bir iletim aslında yaklaşık 90.000 mil yol alır ve bu nedenle uydu ağının gecikme süresi (500 ms veya daha çok) karasal ağa (20 - 50 ms) göre daha fazladır. En iyi koşullarda bu gecikmeyi fark etmezsiniz, ancak büyük dosyaları indirirken, video akışı yapmak ve oyun oynamak için büyük olasılıkla fark etmezsiniz. Bir diğer sorun, fırtına ve tipi gibi ağır havaların uydu iletimini geçici olarak keseceği "yağmur karartma" sorunudur.

## <a name="are-you-sure-its-the-network"></a>Ağ olduğundan emin misiniz?

Performans sorunlarıyla her kez deneyimlenin, ilk olarak sorunun temel nedeninin cihazınızın olduğundan emin olun. Büyük bir gelişme için iki şey yapabilirim:

- Cihazınızın iyi bir şekilde çalışıyor olduğundan ve bilgisayarınızda kötü amaçlı yazılım olmadığınından emin olun.

- Mümkünse daha fazla bellek satın alın. Cihazınızın performansını artırmanın en basit ve çoğunlukla en etkili yolu bellek eklemektir. Bu, büyük dosya ve videolarla çalışırken özellikle yararlı olur.

Daha fazla bilgi için bkz. [Windows performans ve bakım](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) [İpuçları performans ve](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance) performans iyileştirme Windows 10.

## <a name="best-practices-for-using-your-browser"></a>Tarayıcınızı kullanmaya yönelik en iyi yöntemler

Tarayıcınız, Office 365'i yüklemek için gereken ağ geçididir, dolayısıyla özellikle de bir sayfayı yüklemek için gereken süre ve Office 365 hizmetine ne sıklıkta seyahat Office 365 olabilir.

### <a name="browsers-in-general"></a>Genel olarak tarayıcılar

Genel olarak tarayıcılar için bazı öneriler:

- Performansı etkileyebilirsiniz veya aslında ihtiyacınız olmayan tarayıcı eklentilerini devre dışı bırakabilirsiniz.

- Geçici internet dosyalarınız için önbellek boyutunu artırma.

- İş veya okul hesabınızla oturum açtıktan sonra, gün boyunca tarayıcı penceresini açık tutabilirsiniz. Yeniden oturum açmadan diğer sekmeleri ve pencereleri açabilirsiniz. Başka bir hesapta oturum açmanız gerekirse Özel Gözatma'ya bakın.

- Her sayfa indirildikten ve açıldıktan sonra, sekmeleri kullanarak bu sayfayı açık tutabilirsiniz. Sekmeler arasında gezinmek ve gün içinde daha sonra sayfayı kullanmak kolaydır. Yalnızca sayfada en son verilere ihtiyacınız varsa sayfayı yenileyin.

- Sayfanın açılması çok uzun zaman alıyorsa, sayfa indirmeyi durdurun (ESC tuşuna basın) ve sonra sayfayı yenileyin (F5 tuşuna basın).

- Mümkünse, seyahatleri daha az Office 365. Örneğin, listelerde veya kitaplıklarda küçük şeyler yapmak yerine, büyük bir kitaplıkta dosyaları bulmak için arama ve doğrudan istediğiniz sonuçlara gitmek için listede filtreleme kullanın. Ya da sayfa yükleme süresini en aza indiren görünümler oluşturun. Daha fazla bilgi için bkz[. Çalışma kitaplarında büyük listeleri ve kitaplıkları Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Video performansı düşükse, videoyu indirmeniz ve aygıtınızda izlemeniz mümkün olabilir. İndirme bağlantısı sağ tıklamanız veya video bağlantısına sağ tıklar ve Hedefi Farklı **Kaydet'i seçmeniz mümkün olabilir**.

### <a name="browser-specific"></a>Tarayıcıya özgü

Tarayıcınız için bazı öneriler:

- **Internet Explorer**: Önceki sürümlere göre önemli performans geliştirmeleri elde etmek için Internet Explorer Sürüm 11 veya daha sonraki bir sürümüne yükseltin. Daha fazla bilgi için bkz [. Internet Explorer sorun giderme kılavuzu](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Daha fazla bilgi için bkz. [Firefox yavaş veya çalışmayı durdur ediyor](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Daha fazla bilgi için bkz. [Apple - Safari](https://www.apple.com/safari/).
- **Chrome**: Daha fazla bilgi için Bkz. [Chrome Yardımı](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>E-posta ve posta Outlook için en Outlook Web App

E-postayı okumak, yazmak ve düzenlemek herkesin günlerinin büyük bir bölümünü ifade ediyor. Hem Outlook hem de Outlook Web App (OWA) çevrimdışı destek sağlar. Akıllı telefonda e-posta uygulaması kullanmak da yararlı bir alternatiftir. Aşağıdaki seçenekleri, ihtiyaçlarınızı en iyi şekilde kullanın:

- Önceki sürümlere göre önemli performans Outlook için Yükseltme'nin en son sürümüne yükseltin.

- Outlook Web App, çevrimdışı iletiler, kişiler ve takvim olayları oluşturmanıza olanak sağlar. Bu iletiler, OWA'nın bir sonraki bağlantısına geldiğinde karşıya Office 365. OWA'ya çevrimdışı modda ayarlama ve kullanma hakkında daha fazla bilgi için bkz[. Outlook Web App kullanma](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook, önbelleğe alınmış modda çalışmana olanak sağlar ve mümkün olduğunda otomatik olarak bağlanır. Posta kutunuzu Outlook veya yalnızca bir bölümünü indirmeniz gerekir. Daha fazla bilgi için bkz[. Önbelleğe Alınmış Exchange Modunu Açma](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) [ve Çevrimdışı çalışma'ya Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook, çevrimdışı mod da sunar. Bunu kullanmak için, önce önbelleğe alınmış modu ayarlasın, böylece hesaptan alınan bilgilerin bilgisayarınıza kopyalanır. Çevrimdışı moddayken, Outlook gönderme ve alma ayarlarını kullanarak veya el ile çevrimiçi çalışacak şekilde ayarsanız, Çevrimdışı'ya bağlanmaya çalışır. Daha fazla bilgi için bkz [. Veri](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282) bağlantısı ücretlerinden kaçınmak için Çevrimdışı [çalışma, Çevrimdışı](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) çalışırken gönderme ve alma ayarlarını değiştirme ve Çevrimdışı çalışmadan [çevrimiçi çalışmaya geçme](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Akıllı telefonunuz varsa, bu telefonu kullanarak telefon operatörünüzün ağı üzerinden e-postanızı ve takviminizi önceliklendirebilirsiniz.

> [!NOTE]
> İşte, OWA veya Outlook konusunda yol gösterici bazı kılavuzlar. Aygıtınızda disk alanı sorun yoksa, Outlook eksiksiz bir özellik kümesine sahip olabilir ve sizin için en iyisi bu olabilir. Aygıtınızda disk alanı soruna nedense, özelliklerin bir alt kümesini de olan, ancak çevrimiçi çalışma durumlarında en iyi şekilde çalışan OWA'ı kullanmayı düşünebilirsiniz. Kuşkusuz bu iki birlikte de kullanabilirsiniz, çünkü birlikte iyi çalışırlar.

## <a name="best-practices-for-using-onedrive-for-business"></a>E-postanın kullanımına yönelik en OneDrive İş

OneDrive İş dosyalarla çevrimiçi ve çevrimdışı çalışmak için en yeniden tasarlanmıştır. Bu ayarlamayı bir kez gerçekleştirin, değişiklikleri eşitleme işlemi istediğiniz yerde ve istediğiniz zaman otomatik olarak ve güvenilir bir şekilde yapılır. Ağ yavaşsa, dosyaların çevrimdışı sürümüyle çalışabilirsiniz.

OneDrive İş eşitleme uygulaması SharePoint Online ve Office 365 iş aboneliğiyle birlikte gelir veya OneDrive İş eşitleme uygulamasını ücretsiz indirebilirsiniz.[](https://support.microsoft.com/kb/2903984) Bu uygulama aynı zamanda Explorer'da **Aç veya Diğer** **Upload daha** hızlıdır. Daha fazla bilgi için bkz[. Kendi dosyalarınızı eşitlemek OneDrive İş için bilgisayarınızı Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

İşte, eşitleme uygulamasını kullanmaya yönelik bazı OneDrive İş kılavuzu:

- Büyük bir kitaplığı ilk kez eşitlerken, eşitlemeyi çalışma saatleri dışı, örneğin gece başlatmanız gerekir.
- Güncelleştirmeleri [eşitlemeyi geçici olarak durdurmak için, OneDrive İş uygulamasıyla](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) kitaplığı eşitlemeyi durdur özelliğini kullanabilirsiniz. Bununla birlikte, çok fazla sayıda güncelleştirmenin kuyrukta bir kuyrukta bir kuyruk oluşturmalarını önlemek ve aynı belge üzerinde birkaç kişi çalışıyorsa birleştirme çakışmaları riskini en aza indirmek için, bu özelliği kısa süreler için, örneğin bir defada birkaç saat kullanın.

## <a name="best-practices-for-using-onenote"></a>E-postanın kullanımına yönelik en OneNote

Her SharePoint ekip sitesinde yerleşik bir OneNote defteri vardır ve kolayca kendi not defterinizi oluşturabilirsiniz. OneNote, görevleri tamamlamak için her gün ihtiyacınız olan zamanında bilgileri toplamak için mükemmel bir yol sağlar. Örneğin, birçok ekip bu notları OneNote, proje notları, fikirler, planlar ve durum raporları için bir toplama noktası olarak kullanır. Bu birbirinden ayrı bilgileri sayfalar, bölümler ve sekmeleri kullanarak düzgün bir şekilde düzenleyebilirsiniz.

İçeriklere OneNote, içeriğe masaüstü, dizüstü bilgisayar, tablet veya akıllı telefon gibi hemen her cihazdan erişmenizdir. Ayrıca, kaydetme veya eşitleme konusunda endişelenmenize gerek yok, çünkü OneNote sizin için bunu yapar.

Daha fazla bilgi için bkz. [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Lync Online'ı ve Skype Kurumsal için en iyi yöntemler

Aşağıda, ağınız yavaşken Skype Kurumsal Lync Online veya Lync Online'ı kullanmaya yönelik genel yönergeler ve bilgiler vemektedir:

- Mümkün olduğunda anlık mesajlaşmayı kullanın çünkü yavaş ağlarda iyi çalışır.

- Sanal özel ağ (VPN) veya uzaktan erişim hizmeti (RAS) bağlantıları üzerinden telefon çağrısı yapmaktan kaçının.

- Ses cihazınızın onaylandıktan emin olun. Daha fazla bilgi için Bkz. [Microsoft Lync için Nitelikli Telefonlar ve Cihazlar](/skypeforbusiness/lync-cert/ip-phones).

- Çevrimiçi PowerPoint Slaytlar'ı kullanırken, slaytların boyutunu ve karmaşıklığını düşürebilirsiniz. Daha fazla bilgi için İpuçları [performansı iyileştirmeye yönelik iyileştirmeler hakkında bilgi için bkz](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Video performansı, ağ performansına çok bağımlıdır. Ağınız yavaşsa video kullanmaktan kaçının.

Daha fazla bilgi için bkz[. Lync Online'da](https://support.microsoft.com/kb/2386655) düşük ses veya görüntü kalitesi ya da diğer çalışma [kitaplarında Skype Kurumsal](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Liste kullanmaya yönelik en SharePoint yöntemleri

Verileri "temizlemek", çözümlemek veya rapor etmek için liste verileriyle çevrimdışı çalışmak, yavaş bir ağın etkilerini en aza indirmek için mükemmel bir yol sağlar. Microsoft Access 2019 ve Microsoft Access 2016 listelerin çoğunu bağlantı Access 2016 okuyabilir ve yazabilirsiniz. Ayrıca, listeyi bir Excel Tablosuna aktarabilirsiniz. Bu tabloyla liste arasında Excel veri bağlantısı oluşturur. Yeni [listelerle bağlantılı tablolarla çevrimdışı çalışma SharePoint öğrenin](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).

Daha fazla bilgi için Büyük listeleri ve kitaplıkları tek bir kitaplıkta yönetme konusunda yer alan "Büyük [listeleri yönetme hakkında daha fazla Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Web sayfalarını özelleştirmek için en iyi yöntemler

Web sayfasını özelleştirebilirsiniz ve istemeden sayfada performans düşük olabilir. Sayfanın karmaşıklığı ve boyutu, sayfaya eklenen web bölümlerinin sayısı, başlangıçta görüntülenen liste veya kitaplık öğelerinin sayısı ve sayfayı kodma yolunuz gibi bir dizi faktör etkili olabilir.

Daha fazla bilgi için bkz[. Çevrimiçi SharePoint ayarlama](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>E-postanın kullanımına yönelik en Project Online

Aşağıdaki yönergeler ağ performansını geliştirmeye yardımcı olabilir.

- Project Online SharePoint Online eşitleme gerektirir ve bu da zaman alıcı olabilir. Proje ekiplerinin devir oranı düşükse, Daha Fazla Project Yayımlama ve Yayımlama Project için Site Eşitleme'Project devre dışılayın. Active Directory eşitlemesini, sistemi gerçekten ihtiyacı olan kaynak gruplarıyla sınırlandırma ve büyük gruplar eşitledikten sonra tüm olası izin sorunlarını izleme.

- Organizasyonunız proje siteleri kullanıyorsa, bunları otomatik olarak değil, istek üzerine oluşturun. Bu ilk yayımlama deneyimini hızlandırır ve gereksiz siteler ve içerikler oluşturulmasını önler.

- Project Sayfası (PDP) tüm projenin yeniden hesaplanmasına neden olabilir ve iş akışı eylemleri başlatebilir; bu işlemlerin ikisi de yoğun performansla çalışan işlemlerdir. Aynı PDP'de iki güncelleştirme işleminin aynı anda tetiklenmesinden kaçınmak için, takvim alanlarını (Başlangıç tarihi, Bitiş tarihi, Durum tarihi ve Geçerli tarih) ve zamanlanmış olmayan alanları (proje adı, açıklama ve sahip) güncelleştirmeden kaçının.

- Her PDP'Web Bölümleri özel alan sayısını azaltma. Yükü geliştirmek ve zaman kazanmak için yalnızca güncelleştirme gerektiren alanlarla özel bir PDP oluşturun.

- Raporlama için OData kullanırken, sunucu tarafı filtrelemeyi kullanarak çalışma zamanında sorgularsınız veri miktarını sınırlandırın.

Daha fazla bilgi için bkz[. Performans Project Online ayarlama](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Sorunları bildirmenin en iyi yolu nedir?

Microsoft, ağın izlenmesi, bant genişliği ve gecikme süresini ölçme, sayfa yükleme süresini iyileştirme, disk I/O süresini azaltma, Sayfaları En Düşük İndirme Stratejisini kullanmak üzere yeniden tasarlama, veri merkezlerine donanım ekleme ve daha fazla veri merkezi ekleme ile Office 365'ın genel performansını sürekli olarak geliştirmektedir. Geçerli durumunuz denetleniyor ve sorunları raporlama hakkında daha fazla bilgi için bkz[. Hizmet Office 365 denetleme](view-service-health.md).

## <a name="see-also"></a>Ayrıca bkz.

[Network planning and performance tuning for Office 365](network-planning-and-performance.md)

[Office 365 Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
