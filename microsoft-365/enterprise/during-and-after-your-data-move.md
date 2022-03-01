---
title: Verileriniz taşınma sırasında ve sonrasında
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 09/22/2021
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
description: Veri hareketleri, Microsoft'un kiracınız için hizmetleri ve ilişkili verileri yeni bir veri merkezi coğrafi olarak taşırken  meydana gelen arka uç işlemleridir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1fcb62897f1feabe0ca8c447c51e61c7d752138c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998075"
---
# <a name="during-and-after-your-data-move"></a>Verileriniz taşınma sırasında ve sonrasında

Veri hareketleri, son kullanıcıları çok az etkileyen bir arka uç işlemidir. Microsoft kiracınız için her hizmeti ve ilişkili verileri coğrafi olarak yeni bir veri merkezi'ne taşırken herhangi bir işlem yapmak gerekmez. Veri aktarımı ve doğrulama, kullanıcılar üzerinde çok az etkiyle arka planda gerçekleşir.
  
> [!NOTE]
> Her hizmet için farklı zamanlarda taşınır. Sonuç olarak, her hizmet için farklı bir zamanda açıklanan azaltılmış işlevselliğin olduğunu görüyorsunuz. 
  
Her bir Microsoft 365, SharePoint Online ve bir sohbet hizmetinin tamamlandıktan sonra Exchange Online için Teams merkezini izleyin. Aşağıdaki tabloda gösterildiği gibi, geri kalan temel müşteri verilerini yeni veri merkezi coğrafi olarak tamamlamak için kayıt döneminin sonundan 24 ay kadar sürebilir.   

| Kayıt ülkesinde olan müşteriler | Tüm hareketler, |
|:-----|:-----|
|Avustralya, Yeni Zelanda, Fiji  <br/> |1 Temmuz 2022  <br/> |
|Japonya  <br/> |1 Temmuz 2022  <br/> |
|Hindistan  <br/> |1 Temmuz 2022  <br/> |
|Kanada  <br/> |1 Temmuz 2022  <br/> |
|Güney Kore  <br/> |1 Temmuz 2022  <br/> |
|Birleşik Krallık  <br/> |1 Temmuz 2022  <br/> |
|Fransa  <br/> |1 Temmuz 2022  <br/> |
|Birleşik Arap Emirlikleri  <br/> |1 Temmuz 2022  <br/> |
|South Africa  <br/> |1 Temmuz 2022  <br/> |
|İsviçre, Liechtenstein  <br/> |1 Temmuz 2022  <br/> |
|Norveç  <br/> |1 Kasım 2022  <br/> |
|Almanya  <br/> |1 Mayıs 2023  <br/> |
|Brezilya  <br/> |1 Haziran 2023  <br/> |
|İsveç  <br/> |1 Haziran 2024  <br/> |

## <a name="exchange-online"></a>Exchange Online

Her kullanıcının tek bir kiracı için yeni veri merkezi coğrafi olarak taşınması zaman alılı olduğundan, bazı kullanıcılar taşıma sırasında hala eski veri merkezinde coğrafi olarak yer alırken, diğerleri de yeni veri merkezinde coğrafi olarak yer alır. Bu, birden çok posta kutusuna erişmeyi içeren bazı özelliklerin taşıma sürecinde tam olarak çalışmayy başka bir anlama gelir ve bu süre haftalar sürebilir. Bu özellikler aşağıdaki bölümlerde açıklanmıştır.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Web Access'te "Outlook Klasörü" açma

Bazı kullanıcılar "Paylaşılan Klasör" özelliğini kullanarak Web Access'te başka bir posta kutusunda (kullanıcının okuma veya yazma izinleri olan) Outlook bir paylaşılan posta klasörü açar. Aşağıdaki tabloda, posta kutusu taşıma sırasında paylaşılan klasörlere erişimin nasıl çalışır? Paylaşılan posta kutusu üzerinde tam izinlere sahip kullanıcıların, taşıma sırasında Web Access'i Outlook kullanarak posta kutusunu açabilirsiniz. 
  
| Yapılandırma | Açıklama |
|:-----|:-----|
|Kullanıcının başka bir posta kutusu için posta kutusu klasör izni var  <br/> |Olası sınırlı.  <br/> Kiracı taşıma sırasında A Kullanıcısı ve B Posta Kutusu aynı coğrafi konumlarda yoksa, A Kullanıcısı B Posta Kutusu'nun yalnızca belirli bir klasör üzerinde izni varsa, A Kullanıcısı Outlook Web Erişimi'ne posta kutusu B'nin klasörünü açamaz.  <br/> Paylaşılan klasör eklemek için, sol gezinti bölmesinde kullanıcı adına sağ tıklayın ve Paylaşılan klasör **ekle'yi seçin**.  <br/> |
|Başka bir posta kutusu için tam posta kutusu izni olan kullanıcı  <br/> |Tam destek.  <br/> A Kullanıcısı'nın Posta Kutusu B üzerinde "Tam Erişim" izni varsa, Kullanıcı B'yi gösteren bir pencere açmak için Web Access'Outlook sol gezinti bölmesinde paylaşılan klasöre tıklar.  Kullanıcı, herhangi bir olumsuz etki Outlook Web Access'i kullanarak paylaşılan posta kutusunu açabilir. Bu sınırlama yalnızca posta kutusunda klasör düzeyinde paylaşım için geçerlidir.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Çevrimiçi SharePoint taşındığında, aşağıdaki hizmetlerin verileri de taşınır:
  
- OneDrive İş
    
- Microsoft 365 Video hizmetleri
    
- Office tarayıcıda yeniden kullanma
    
- Microsoft 365 Kurumsal Uygulamaları
    
- Visio Pro için Microsoft 365
    
SharePoint Online verilerinizi taşımayı tamamladikten sonra, aşağıdaki etkilerden bazılarını alabilirsiniz.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 Video Hizmetleri

- Video için veri taşıma, SharePoint Online'daki içeriğinizin geri kalanından daha uzun sürer.
    
- SharePoint Online içeriği taşındıktan sonra, videolar çalınmayabilecek bir zaman dilimi olur.
    
- Önceki veri merkezinden trans-coded kopyaları kaldırıyor ve yeni veri merkezinde yeniden transcoding ile yeniden dağıtıyoruz.
    
### <a name="search"></a>Arama

SharePoint Online verilerinizi taşıma kursunda, arama dizininizi ve arama ayarlarınızı yeni bir konuma geçiririz. SharePoint Online verilerinizin  taşıması tamamlanana kadar, özgün konumda dizinden kullanıcılarınızı hizmet vermeye devam edeceğiz. Yeni konumda, SharePoint Online verilerinizi taşımayı tamamladikten sonra arama otomatik olarak SharePoint başlatılır. Bu noktadan sonra, kullanıcılarınıza geçirilen dizinden yardımcı olabiliriz. Geçiş sonrasında yapılan içerik değişiklikleriniz, gezinme işlemi bu değişiklikleri alana kadar geçirilen dizine dahil olmaz. Müşterilerin çoğu, SharePoint Online verilerini taşımayı tamamladikten hemen sonra sonuçların az olduğunu fark etmez, ancak bazı müşteriler ilk 24-48 saatte daha az taze deneyim elde eder 
  
Aşağıdaki arama özellikleri etkilenir:
  
- Arama sonuçları ve Web Bölümleri sonuçları: Gezinme işlemi, geçiş sonrasında 40 gün içinde yapılan değişiklikleri içermez. 
    
- Delve: Delve geçiş sonrasında herhangi bir değişiklik içermez.
    
- Sitenin Popülerliği ve Arama Raporları: Yeni konumdaki Excel raporları için sayma sayısı, yalnızca SharePoint Online verilerinizi taşımayı tamamladikten sonra devam eden kullanım raporlarından geçirilen sayımları ve sayımları içerir. Ara dönemdeki tüm sayımlar kaybolur ve kurtarılamaz. Bu dönem genellikle birkaç gündür. Bazı müşterilerin kayıpları daha kısa veya daha uzun olabilir.
    
- Video Portalı: Video Portalı'nın görüntüleme sayıları ve istatistikleri Excel Raporları istatistiklerine bağlıdır, bu nedenle Video Portalı için görüntüleme sayıları ve istatistikleri, Excel raporlarıyla aynı süre için kaybolur.
    
- eBulma: Geçiş sırasında değişen öğeler, gezinme işlemi değişiklikleri alana kadar gösterilmez.
    
- Veri Kaybına Karşı Koruma (DLP): İlkeler, gezinme değişiklikleri alana kadar değişiklik yapılan öğelerde zorunlu kılınmaz.

Geçiş işlemi kapsamında, varsayılan bölge değişir ve tüm yeni içerik yeni varsayılan bölgede depolanır. Var olan içerik, ilk değişiklikten sonra yönetim merkezinde SharePoint Online veri konumu yapıldıktan sonra 90 gün boyunca sizi etkilemeden arka planda hareket eder.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Dosyalar sekmesi

Geçiş tamamlandıktan sonra Dosyalar sekmesinin kullanıcı ilk kez kullanmayı denemesi sırasında tam olarak yüklensi daha fazla zaman (7 saniyeye kadar) sürebilir. 

### <a name="read-only-period"></a>Salt okunur dönem

Teams sohbet hizmetleri her bir konuyu tek tek taşır.  Taşıma sırasında iş parçacığı salt okunur durumda kilitlenir ve bu da her zincirde birkaç saniye sürer.  İş parçacıklarını geçiş sırasında erişilebilir durumda kalır.

## <a name="skype-for-business"></a>Skype Kurumsal

Skype Kurumsal artık kullanılamaz.  [Skype Kurumsal Online,](/lifecycle/announcements/skype-for-business-online-retirement) 31 Temmuz 2021'de kaldıracak. Bu süre sonunda, hizmete artık erişilemez. 
  
## <a name="related-topics"></a>İlgili konular 
 
[Verilerinizin taşınması nasıl gerekir?](request-your-data-move.md)
    
[Veri taşıma genel SSS](data-move-faq.yml)
  
[Veriler için yeni veri merkezi coğrafi Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Bölgeye göre Azure hizmetleri](https://azure.microsoft.com/regions/)
