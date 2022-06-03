---
title: Verilerinizi taşıma sırasında ve sonrasında
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
ms.localizationpriority: medium
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Veri taşıma işlemleri, Microsoft kiracınız için hizmetleri ve ilişkili verileri yeni bir veri merkezi coğrafi alanına taşırken gerçekleşen arka uç işlemleridir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 76d4921db83c5f13ad7f6d62b4826540b12528a0
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872302"
---
# <a name="during-and-after-your-data-move"></a>Verilerinizi taşıma sırasında ve sonrasında

Veri taşıma işlemleri, son kullanıcıları en az etkileyen arka uç işlemidir. Microsoft kiracınız için her hizmeti ve ilişkili verileri yeni bir veri merkezi coğrafi konumuna taşırken herhangi bir eylem gerekmez. Veri aktarımı ve doğrulama, kullanıcılar üzerinde en az etkiyle önceden arka planda gerçekleşir.
  
> [!NOTE]
> Taşımalar her hizmet için farklı zamanlarda gerçekleşir. Sonuç olarak, her hizmet için farklı bir zamanda açıklanan azaltılmış işlevselliği görürsünüz.
  
Exchange Online, SharePoint Online ve Teams sohbet hizmetinin her biri için taşıma tamamlandığında onay için Microsoft 365 İleti Merkezi'ni izleyin. Aşağıdaki tabloda gösterildiği gibi, bekleyen temel müşteri verilerinin yeni veri merkezi coğrafi alanına taşınmaları kayıt döneminin sona ermesinin ardından 24 aya kadar sürebilir.

| Kayıt ülkesi olan müşteriler | Tüm taşımalar şu şekilde tamamlanır: |
|:-----|:-----|
|Avustralya, Yeni Zelanda, Fiji  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Japonya  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Hindistan  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Kanada  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Güney Kore  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Birleşik Krallık  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Fransa  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Birleşik Arap Emirlikleri  <br/> |1 Temmuz 2022 Cuma  <br/> |
|South Africa  <br/> |1 Temmuz 2022 Cuma  <br/> |
|İsviçre, Liechtenstein  <br/> |1 Temmuz 2022 Cuma  <br/> |
|Norveç  <br/> |1 Kasım 2022, İstanbul  <br/> |
|Almanya  <br/> |1 Mayıs 2023, Mayıs 2023  <br/> |
|Brezilya  <br/> |1 Haziran 2023 Perşembe  <br/> |
|İsveç  <br/> |1 Haziran 2024, Ağustos 2024, Ağustos 2024, Temmuz 2024  <br/> |

## <a name="exchange-online"></a>Exchange Online

Her kullanıcının tek bir kiracı için yeni veri merkezi coğrafi konumuna taşınması zaman aldığından, bazı kullanıcılar taşıma sırasında eski veri merkezi coğrafi alanında, diğerleri ise yeni veri merkezi coğrafi alanında yer alır. Bu, birden çok posta kutusuna erişmeyi içeren bazı özelliklerin, taşıma işleminin bir döneminde tam olarak çalışmayabileceği ve bunun da haftalar sürebileceği anlamına gelir. Bu özellikler aşağıdaki bölümlerde açıklanmıştır.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Outlook Web Access'te "Paylaşılan Klasör" seçeneğini açma

Bazı kullanıcılar, "Paylaşılan Klasör" özelliğini kullanarak Outlook Web Access'te başka bir posta kutusundan (kullanıcının okuma veya yazma izinlerine sahip olduğu) paylaşılan posta klasörünü açar. Aşağıdaki tabloda, posta kutusu taşıma sırasında paylaşılan klasörlere erişimin nasıl çalıştığı açıklanmaktadır. Paylaşılan posta kutusuna tam izinlere sahip kullanıcıların taşıma sırasında Outlook Web Erişimi'ni kullanarak posta kutusunu açabileceğini lütfen unutmayın.
  
| Yapılandırma | Açıklama |
|:-----|:-----|
|Kullanıcının başka bir posta kutusu için posta kutusu klasörü izni var  <br/> |Potansiyel olarak sınırlı.  <br/> Kiracı taşıma sırasında A Kullanıcısı ve B Posta Kutusu aynı coğrafi bölgede değilse, A Kullanıcısı B Posta Kutusu'nun B Posta Kutusu'nda yalnızca belirli bir klasöre izni varsa, A Kullanıcısı Outlook Web Access'te B Posta Kutusu'nun klasörünü açamaz.  <br/> Paylaşılan klasör eklemek için sol gezinti panelinde kullanıcı adına sağ tıklayın ve **Paylaşılan klasör ekle'yi** seçin.  <br/> |
|Başka bir posta kutusuna tam posta kutusu izni olan kullanıcı  <br/> |Tam olarak desteklenir.  <br/> A Kullanıcısının B Posta Kutusu'nda "Tam Erişim" izni varsa, A Kullanıcısı B Posta Kutusu'nun gösterildiği bir pencere açmak için Outlook Web Access'in sol gezinti panelinde paylaşılan klasöre tıklayabilir.  Kullanıcı, taşıma sırasında web erişimi Outlook kullanarak herhangi bir olumsuz etki olmadan paylaşılan posta kutusunu açabilir. Sınırlama yalnızca posta kutusunda klasör düzeyinde paylaşım için geçerlidir.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online taşındığında, aşağıdaki hizmetlere ilişkin veriler de taşınır:
  
- OneDrive İş

- Microsoft 365 Video hizmetleri

- Tarayıcıda Office

- Microsoft 365 Kurumsal Uygulamaları

- Microsoft 365 için Visio Pro

SharePoint Online verilerinizi taşımayı tamamladıktan sonra aşağıdaki etkilerden bazılarını görebilirsiniz.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 Video Hizmetleri

- Video için veri taşıma işlemi, SharePoint Online'daki içeriğinizin geri kalanındaki taşıma işlemlerinden daha uzun sürer.

- SharePoint Çevrimiçi içerik taşındıktan sonra, videoların oynatılamadığı bir zaman dilimi olacaktır.

- Koda dönüştürülmüş kopyaları önceki veri merkezinden kaldırıyor ve yeni veri merkezinde yeniden koda aktarıyoruz.

### <a name="search"></a>Arama

SharePoint Online verilerinizi taşıma işleminiz boyunca, arama dizininizi ve arama ayarlarınızı yeni bir konuma geçiririz. SharePoint Online verilerinizin taşınmasını **tamamlayana** kadar kullanıcılarınıza özgün konumdaki dizinden hizmet etmeye devam ediyoruz. Yeni konumda, SharePoint Online verilerinizi taşımayı tamamladıktan sonra arama otomatik olarak içeriğinizde gezinmeye başlar. Bu noktadan itibaren, geçirilen dizinden kullanıcılarınıza hizmet ederiz. Geçiş sonrasında içeriğinizde yapılan değişiklikler, gezinme tarafından alınana kadar geçirilen dizine dahil değildir. Müşterilerin çoğu, SharePoint Çevrimiçi verilerini taşımayı tamamladıktan hemen sonra sonuçların daha az yeni olduğunu fark etmez, ancak bazı müşteriler ilk 24-48 saat içinde daha az yenilikle karşılaşabilir.
  
Aşağıdaki arama özellikleri etkilenir:
  
- Arama sonuçları ve Arama Web Bölümleri: Sonuçlar, gezinme onları alana kadar geçiş sonrasında gerçekleşen değişiklikleri içermez. 

- Delve: Delve, gezinme tarafından seçilene kadar geçiş sonrasında gerçekleşen değişiklikleri içermez.

- Site için Popülerlik ve Arama Raporları: Yeni konumdaki Excel raporların sayısı yalnızca SharePoint Çevrimiçi verilerinizi taşımayı tamamladıktan sonra çalıştırılan kullanım raporlarından geçirilen sayımları ve sayıları içerir. Ara dönemdeki sayımlar kaybolur ve kurtarılamaz. Bu süre genellikle birkaç gündür. Bazı müşteriler daha kısa veya daha uzun kayıplar yaşayabilir.

- Video Portalı: Video Portalı'nın sayılarını ve istatistiklerini görüntüleme, Excel Raporların istatistiklerine bağlıdır, bu nedenle video portalının görüntüleme sayıları ve istatistikleri Excel raporlarıyla aynı süre boyunca kaybolur.

- eBulma: Geçiş sırasında değiştirilen öğeler, gezinme değişiklikleri alana kadar gösterilmez.

- Veri Kaybı Koruması (DLP): Gezinme değişiklikleri alana kadar değişen öğelerde ilkeler uygulanmaz.

Geçişin bir parçası olarak, varsayılan bölge değişir ve tüm yeni içerik yeni varsayılan bölgede bekleyen konumda depolanır. Mevcut içerik, yönetim merkezindeki SharePoint Online veri konumunda yapılan ilk değişiklikten sonra 90 güne kadar arka planda sizi etkilemeden hareket eder.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Dosyalar sekmesi

Geçiş tamamlandıktan sonra, kullanıcı ilk kez kullanmayı denediğinde Dosyalar sekmesinin tamamen yüklenmesi ek zaman alabilir (7 saniyeye kadar). 

### <a name="read-only-period"></a>Salt okunur dönem

Teams sohbet hizmetleri her yazışmayı ayrı ayrı taşır.  taşıma sırasında iş parçacığı salt okunur durumda kilitlenir ve bu durum iş parçacığı başına birkaç saniye sürer.  Geçiş sırasında iş parçacıklarına erişilebilir durumda kalır.

## <a name="skype-for-business"></a>Skype Kurumsal

Skype Kurumsal taşıma artık kullanılamaz.  Skype Kurumsal Online 31 Temmuz 2021'de [kullanımdan kaldırılacaktır](/lifecycle/announcements/skype-for-business-online-retirement). Bu süre sonunda, hizmete artık erişilemez.
  
## <a name="related-topics"></a>İlgili konular

[Veri taşıma isteğinde bulunma](request-your-data-move.md)

[Veri taşıma genel SSS](data-move-faq.md)
  
[Microsoft Dynamics CRM Online için yeni veri merkezi coğrafi bölgeleri](/power-platform/admin/new-datacenter-regions)
  
[Bölgeye göre Azure hizmetleri](https://azure.microsoft.com/regions/)
