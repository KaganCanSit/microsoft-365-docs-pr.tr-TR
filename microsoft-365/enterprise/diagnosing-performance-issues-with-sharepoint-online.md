---
title: SharePoint Online ile ilgili performans SharePoint tanılama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, Internet Explorer geliştirici araçlarını kullanarak SharePoint Online sitenize ilişkin genel sorunları nasıl tanıyabilirsiniz?
ms.openlocfilehash: acd5fc05f933e5d47b5bb14c2d3317ea3a6e0186
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007240"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>SharePoint Online ile ilgili performans SharePoint tanılama

Bu makalede, Internet Explorer geliştirici araçlarını kullanarak SharePoint Online sitenize ilişkin genel sorunları nasıl tanıyabilirsiniz?
  
SharePoint Online sitesinde bir sayfanın özelleştirmelerle ilgili bir performans sorunu olduğunu belirlemenin dört farklı yolu vardır.

- Site ve Sayfa performansı tanılama
  
- F12 araç çubuğu ağ monitörü

- Özelleştirilmeyen temel ile karşılaştırma

- SharePoint Online yanıt üst bilgisi ölçümleri

Bu konu başlığında, performans sorunlarını tanılamak için bu yöntemlerin her birini nasıl kullanabileceğiniz açıklanmıştır. Sorunun nedenini ortaya çıkartıktan sonra, üzerinde bulunabilecek performans iyileştirme makalelerini kullanarak SharePoint üzerinde çalışabilirsinizhttps://aka.ms/tune.  

## <a name="use-the-site-and-page-performance-diagnostic-from-the-microsoft-365-admin-center"></a>Site ve Sayfa performansı tanılamayı Sistem Merkezi'Microsoft 365 Yönetici kullanma

> [!NOTE]
> Yöneticiyseniz ve SharePoint'de performansla ilgili sorun yapıyorsanız, aşağıdaki Testleri Çalıştır'ı seçin.  Bu seçim Merkezi'nde Site ve Sayfa Performansı tanılamasını Microsoft 365 Yönetici. Bu testler yapılandırmanızı kontrol eder ve kiracınız için performans iyileştirmeye yardımcı SharePoint sonraki adımları hızla önerebilir.
>> [!div class="nextstepaction"]
>> [Testleri Çalıştırma: Test SharePoint Denetleme](https://aka.ms/PillarSiteandPagePerf)
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>SharePoint Online'da performansı tanılamak için F12 araç çubuğunu kullanma
<a name="F12ToolInfo"> </a>

Bu makalede Internet Explorer 11'i kullanıyoruz. F12 geliştirici araçlarının diğer tarayıcılarda sürümleri biraz farklı görünüyor olsa da benzer özelliklere sahiptir. F12 geliştirici araçları hakkında bilgi için bkz:
  
- [F12 Araçları'nın tüm yenileri](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85))

- [F12 geliştirici araçlarını kullanma](/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))

Geliştirici araçlarını getirmek için **F12 tuşuna** basın ve sonra Wi-Fi tıklayın:
  
![F12 geliştirici araçları wifi simgesinin ekran görüntüsü.](../media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Sayfa **yüklemek** için Ağ sekmesindeki yeşil oynat düğmesine basın. Araç, istediğiniz sayfayı almak için tarayıcının istekte bulunarak tüm dosyalarını döndürür. Aşağıdaki ekran görüntüde bu tür bir liste gösterilir.
  
![Bir sayfa isteğiyle birlikte döndürülen dosya listesinin ekran görüntüsü.](../media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Bu ekran görüntüsinde gösterildiği gibi, sağ tarafta dosyaların indirme zamanlarını da görebilirsiniz.
  
![İstenen sayfaları başka bir sayfadan yüklemek için gereken SharePoint.](../media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Bu size, dosyanın ne kadar süreyle yüklerinin olduğunu görsel olarak da ifade sağlar. Yeşil çizgi, sayfanın tarayıcı tarafından iş yapmaya ne zaman hazır olduğunu gösterir. Bu görünüm, sitenize sayfa yüklemelerinin yavaş olmasına neden olan farklı dosyaları hızla görüntülemenizi sağlar.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>SharePoint Online için özelleştirilmeyen bir temel ayarlama
<a name="F12ToolInfo"> </a>

Sitenizin performansında zayıf noktaları belirlemenin en iyi yolu, SharePoint Online'da tamamen ilk gelen site koleksiyonu ayarlamaktır. Bu şekilde, sitenizin tüm farklı yönleriyle sayfa üzerinde hiçbir özelleştirmeyle elde edilecekleri karşılaştırabilirsiniz. En OneDrive İş sayfası, hiç özelleştirmesi mümkün olan ayrı bir site koleksiyonu örneğidir.
  
## <a name="viewing-sharepoint-response-header-information"></a>Yanıt SharePoint bilgilerini görüntüleme
<a name="F12ToolInfo"> </a>

SharePoint Online'da, her dosyanın yanıt üst bilgisinde tarayıcıya geri gönderilen bilgilere erişebilirsiniz. Performans sorunlarını tanılamak için en yararlı değer, isteğin sunucuda geçen işlenme miktarını görüntüleyen **SPRequestDuration** değeridir. İsteğin çok yoğun ve kaynak kullanımı yoğun olup olmadığının belirlenmesine yardımcı olabilir. Sunucunun sayfaya hizmet vermek için ne kadar iş yaptığıyla ilgili olarak edinen en iyi bilgidir.

### <a name="to-view-sharepoint-response-header-information"></a>Yanıt üst SharePoint bilgilerini görüntülemek için
  
1. F12 araçlarının yüklü olduğundan emin olmak. Bu araçları indirme ve yükleme hakkında daha fazla bilgi için bkz [. F12 araçlarıyla ilgili güncelleştirmeler](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85)).

2. F12 araçlarında, **Ağ sekmesindeki** yeşil oynat düğmesine basarak sayfayı yükleyebilirsiniz.

3. Araç tarafından döndürülen .aspx dosyalarından birini tıklatın ve sonra DA AYRINTILAR'ı **tıklatın**.

    ![Yanıt üstbilgisi ayrıntılarını gösterir.](../media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Yanıt **üst bilgileri'ne tıklayın**.

    ![Yanıt üst bilgisinin URL'sini gösteren diyagram.](../media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>SharePoint Online'da performans sorunlarının nedeni nedir?
<a name="F12ToolInfo"> </a>

[SharePoint Online](navigation-options-for-sharepoint-online.md) için gezinti seçenekleri makalesinde, SPRequestDuration değeri kullanılarak sayfanın sunucuda işlemesi çok uzun zaman alan karmaşık yapısal gezintinin neden olduğunu belirleyen bir örnek yer alır. Temel bir siteye (özelleştirme olmadan) değer alarak, belirli bir dosyanın yüklemesi uzun zaman alıp almadı bunu belirlemek mümkündür. Ana .aspx dosyası[, SharePoint Online](navigation-options-for-sharepoint-online.md) için Gezinti seçeneklerinde kullanılan örnektir. Bu dosya, sayfa ASP.NET çalışan en yaygın dosya kodunu içerir. Kullandığınız site şablonuna bağlı olarak start.aspx, home.aspx, default.aspx veya giriş sayfasını özelleştirerek başka bir ad kullanabilirsiniz. Bu sayı temel sitenize göre önemli ölçüde yüksekse, sayfanız üzerinde devam ediyor olan ve performans sorunlarına neden olan bir karmaşıklık olduğu iyi bir göstergedir.
  
Sorunun sitenize özel olduğunu belirlediktan sonra, kötü performansa neyin neden olduğunu anlamanın önerilen yolu, sayfa özelleştirmeleri gibi olası tüm nedenleri ortadan kaldırmak ve sonra bunları siteye tek tek geri eklemektir. Sayfanın iyi bir performansta olduğu yeterince özelleştirmeyi kaldırdıktan sonra, belirli özelleştirmeleri tek tek geri ebilirsiniz.
  
Örneğin, gezintiniz çok karmaşıksa, gezintiyi alt siteleri göster gösterecek şekilde değiştirmeyi deneyin ve sonra geliştirici araçlarını kontrol edin ve bunun bir değişiklik olup olmadığını kontrol edin. Ya da büyük miktarda içerik rulosu varsa bunları sayfadan kaldırmayı deneyin ve bunun herhangi bir iyileştirme olup geliştirmeye yönelik olup bakın. Tüm olası nedenleri ortadan kaldıracak ve bunları bir defada yeniden eklersanız, hangi özelliklerin en çok soruna neden olduğunu kolayca belirleyebilir ve çözüm üzerinde çalışabilirsiniz.
