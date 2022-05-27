---
title: SharePoint Online ile ilgili performans sorunlarını tanılama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2021
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: Bu makalede, Internet Explorer geliştirici araçlarını kullanarak SharePoint Online sitenizdeki yaygın sorunları nasıl tanılayabileceğiniz gösterilmektedir.
ms.openlocfilehash: 041619991fdbdcb3e953fe2a06fd63dff0e9201f
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753814"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>SharePoint Online ile ilgili performans sorunlarını tanılama

Bu makalede, Internet Explorer geliştirici araçlarını kullanarak SharePoint Online sitenizdeki yaygın sorunları nasıl tanılayabileceğiniz gösterilmektedir.
  
SharePoint Online sitesindeki bir sayfada özelleştirmelerle ilgili performans sorunu olduğunu belirlemenin dört farklı yolu vardır.

- Site ve Sayfa performansı tanılaması
  
- F12 araç çubuğu ağ izleyicisi

- Özelleştirilmemiş taban çizgisiyle karşılaştırma

- çevrimiçi yanıt üst bilgisi ölçümlerini SharePoint

Bu konuda, performans sorunlarını tanılamak için bu yöntemlerin her birinin nasıl kullanılacağı açıklanmaktadır. Sorunun nedenini bulduktan sonra, üzerinde bulabileceğiniz SharePoint performansını iyileştirme hakkındaki makaleleri kullanarak bir çözüm üzerinde https://aka.ms/tuneçalışabilirsiniz.  

## <a name="use-the-site-and-page-performance-diagnostic-from-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nden Site ve Sayfa performansı tanılamasını kullanma

> [!NOTE]
> Yöneticiyseniz ve SharePoint performansıyla ilgili sorun yaşıyorsanız, aşağıdaki **Testleri Çalıştır'ı** seçerek Microsoft 365 Yönetici Merkezi'ndeki Site ve Sayfa Performansı tanılamasını doldurun. Bu testler, yapılandırmanızı denetler ve kiracınızın SharePoint performansını iyileştirmeye yardımcı olmak için hızlı bir şekilde sonraki adımları önerir.
>> [!div class="nextstepaction"]
>> [Testleri Çalıştırma: SharePoint Performansını Denetleme](https://aka.ms/PillarSiteandPagePerf)

> [!NOTE] 
> Bu özellik Microsoft 365 Kamu, 21Vianet veya Microsoft 365 Almanya tarafından sağlanan Microsoft 365 için kullanılamaz.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>SharePoint Online'da performansı tanılamak için F12 araç çubuğunu kullanma
<a name="F12ToolInfo"> </a>

Bu makalede Internet Explorer 11'i kullanacağız. Diğer tarayıcılardaki F12 geliştirici araçlarının sürümleri benzer özelliklere sahiptir ancak bunlar biraz farklı görünebilir. F12 geliştirici araçları hakkında bilgi için bkz:
  
- [F12 Araçları'ndaki yenilikler](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85))

- [F12 geliştirici araçlarını kullanma](/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))

Geliştirici araçlarını açmak için **F12 tuşuna** basın ve ardından Wi-Fi simgesine tıklayın:
  
![F12 geliştirici araçları wifi simgesinin ekran görüntüsü.](../media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
**Ağ** sekmesinde, sayfayı yüklemek için yeşil oynat düğmesine basın. Araç, tarayıcının istediğiniz sayfayı almak için istediği tüm dosyaları döndürür. Aşağıdaki ekran görüntüsünde bu tür bir liste gösterilmektedir.
  
![Sayfa isteğiyle döndürülen dosyaların listesinin ekran görüntüsü.](../media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Bu ekran görüntüsünde gösterildiği gibi dosyaların indirme zamanlarını da sağ tarafta görebilirsiniz.
  
![İstenen sayfaların SharePoint yüklenmesi için geçen süreyi gösteren diyagram.](../media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Bu, dosyanın yüklenmesinin ne kadar sürdüğünü görsel olarak gösterir. Yeşil çizgi, sayfanın tarayıcı tarafından işlenmeye hazır olduğu zamanları temsil eder. Bu, sitenizde yavaş sayfa yüklemelerine neden olabilecek farklı dosyaların hızlı bir görünümünü sağlayabilir.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>SharePoint Online için özelleştirilmemiş bir temel ayarlama
<a name="F12ToolInfo"> </a>

Sitenizin performansının zayıf noktalarını belirlemenin en iyi yolu, SharePoint Online'da tamamen kullanıma hazır bir site koleksiyonu ayarlamaktır. Bu şekilde, sitenizin tüm çeşitli yönlerini sayfada özelleştirme olmadan elde edeceğiniz özelliklerle karşılaştırabilirsiniz. OneDrive İş giriş sayfası, özelleştirme olasılığı düşük olan ayrı bir site koleksiyonunun iyi bir örneğidir.
  
## <a name="viewing-sharepoint-response-header-information"></a>SharePoint yanıt üst bilgisi bilgilerini görüntüleme
<a name="F12ToolInfo"> </a>

SharePoint Online'da, her dosyanın yanıt üst bilgisinde tarayıcıya geri gönderilen bilgilere erişebilirsiniz. Performans sorunlarını tanılamak için en yararlı değer **SPRequestDuration** değeridir ve bu değer, isteğin sunucuda işlenmesi için geçen süreyi görüntüler. Bu, isteğin yoğun ve kaynak yoğunluklu olup olmadığını belirlemeye yardımcı olabilir. Bu, sunucunun sayfaya hizmet vermek için ne kadar iş yaptığına dair sahip olduğunuz en iyi içgörüdür.

### <a name="to-view-sharepoint-response-header-information"></a>SharePoint yanıt üst bilgisi bilgilerini görüntülemek için
  
1. F12 araçlarının yüklü olduğundan emin olun. Bu araçları indirme ve yükleme hakkında daha fazla bilgi için bkz. [F12 araçlarındaki yenilikler](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85)).

2. F12 araçlarının **Ağ** sekmesinde, sayfayı yüklemek için yeşil oynatma düğmesine basın.

3. Araç tarafından döndürülen .aspx dosyalarından birine ve ardından **AYRINTILAR'a** tıklayın.

    ![Yanıt üst bilgisinin ayrıntılarını gösterir.](../media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. **Yanıt üst bilgileri'ne** tıklayın.

    ![Yanıt üst bilgisinin URL'sini gösteren diyagram.](../media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>SharePoint Online'da performans sorunlarına neden olan nedir?
<a name="F12ToolInfo"> </a>

[SharePoint Online için Gezinti seçenekleri](navigation-options-for-sharepoint-online.md) makalesi, karmaşık yapısal gezintinin sayfanın sunucuda işlenmesinin uzun sürmesine neden olduğunu belirlemek için SPRequestDuration değerinin kullanılmasına ilişkin bir örnek gösterir. Temel site için bir değer alarak (özelleştirme olmadan), belirli bir dosyanın yüklenmesinin uzun zaman alıp almadığını belirlemek mümkündür. [SharePoint Online için Gezinti seçeneklerinde](navigation-options-for-sharepoint-online.md) kullanılan örnek ana .aspx dosyasıdır. Bu dosya, sayfa yükünüz için çalışan ASP.NET kodunun çoğunu içerir. Kullandığınız site şablonuna bağlı olarak, giriş sayfasını özelleştirdiğinizde bu start.aspx, home.aspx, default.aspx veya başka bir ad olabilir. Bu sayı temel sitenizden çok daha yüksekse, sayfanızda performans sorunlarına neden olan karmaşık bir şey olduğunu iyi bir göstergedir.
  
Sitenize özgü bir sorun olduğunu belirledikten sonra, kötü performansa neyin neden olduğunu anlamanın önerilen yolu, sayfa özelleştirmeleri gibi olası tüm nedenleri ortadan kaldırmak ve ardından bunları siteye tek tek yeniden eklemektir. Sayfanın iyi performans göstermesini sağlayan yeterli özelleştirmeyi kaldırdıktan sonra, belirli özelleştirmeleri tek tek geri ekleyebilirsiniz.
  
Örneğin, karmaşık bir gezintiniz varsa, alt siteleri göstermemek için gezintiyi değiştirmeyi deneyin, ardından bunun bir fark yaratıp oluşturmadığını görmek için geliştirici araçlarını denetleyin. Ya da büyük miktarda içerik dağıtımınız varsa bunları sayfanızdan kaldırmayı deneyin ve bunun işleri geliştirip geliştirmediğini görün. Olası tüm nedenleri ortadan kaldırır ve bunları birer birer yeniden eklerseniz, en büyük sorunun hangi özellikler olduğunu kolayca belirleyebilir ve ardından bir çözüme doğru çalışabilirsiniz.
