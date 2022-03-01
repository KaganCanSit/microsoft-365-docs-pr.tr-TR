---
title: Temel verileri yeni veri Microsoft 365 coğrafi olarak taşıma
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 11/16/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Yeni veri Office 365 ve temel verilerinizin yeni bir coğrafi bölgeye taşınmasını talep etmek için veri ikamet seçeneğini nasıl kullanabileceğiniz hakkında bilgi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 590d1b7e72f79e0e6cfd4e29a0a78560f6c13433
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997603"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Temel verileri yeni veri Microsoft 365 coğrafi olarak taşıma

Veri hizmetleri için yeni veri merkezi coğrafi olarak açılmaya Microsoft 365 devam ediyor. Bu yeni veri merkezi, sürekli müşteri talebi ve kullanım büyümemizi desteklemek için kapasite ve bilgi işlem kaynakları ekler. Buna ek olarak, yeni veri merkezi coğrafi konum, çekirdek müşteri verileri için coğrafi olarak yer sağlar. 

Çekirdek müşteri verileri, müşteri verisi alt kümesini ifade etmek için kullanılan terimdir: 
- Exchange Online kutusu içeriğini (e-posta gövdesi, takvim girdileri ve e-posta eklerinin içeriği) kaydetme
- SharePoint Online site içeriği ve bu site içinde depolanan dosyalar
- OneDrive İş'a yüklenen OneDrive İş
- Teams iletiler, kanal iletileri ve sohbetlerde kullanılan resimler dahil olmak üzere sohbet iletilerinin nasıl görüntü olduğunu
  
Zaten var olan bir veri merkezinde coğrafi olarak depolanan temel müşteri verilerine sahip olan mevcut müşteriler, yeni bir veri merkezi coğrafi olarak başlatılmasını etkilenmez. Yeni veri merkezi coğrafi olarak hiç benzersiz özellik, özellik veya uyumluluk sertifikasına sahip yokuz. Bu iki coğrafi coğrafi bölge arasında yer alan bir müşteri olarak, daha önce olduğu gibi hizmet, performans ve güvenlik denetimleriyle aynı kaliteyi elde edersiniz. Kuruluşlarının temel müşteri verilerini yeni veri merkezlerinin coğrafi olarak erken geçişini talep etmek için, aşağıdaki tabloda listelenen mevcut müşterileri sunuyoruz.
  
| Kiracı kayıt ülkesi olan müşteriler | Önceki veri merkezi coğrafi | Yeni veri merkezi coğrafi | Şu zamandan beri coğrafi olarak kullanılabilir: |
|:-----|:-----|:-----|:-----|
|**Japonya**| Asya/Pasifik | Japonya | Aralık 2014 |
|**Avustralya, Yeni Zelanda, Fiji**| Asya/Pasifik | Avustralya | Mart 2015 |
|**Hindistan**| Asya/Pasifik | Hindistan | Ekim 2015 |
|**Kanada**| Amerika Birleşik Devletleri | Kanada | Mayıs 2016 |
|**Birleşik Krallık**| Avrupa Birliği | Birleşik Krallık | Eylül 2016 |
|**Güney Kore**| Asya/Pasifik | Güney Kore | Nisan 2017 |
|**Fransa**| Avrupa Birliği | Fransa | Mart 2018 |
|**Birleşik Arap Emirlikleri**| Avrupa Birliği | Birleşik Arap Emirlikleri | Haziran 2019 |
|**South Africa**| Avrupa Birliği | South Africa | Temmuz 2019 |
|**İsviçre, Liechtenstein**| Avrupa Birliği | İsviçre | Aralık 2019 |
|**Almanya**| Avrupa Birliği | Almanya | Aralık 2019 |
|**Norveç**| Avrupa Birliği | Norveç | Nisan 2020 |
|**Brezilya**| Amerika | Brezilya | Kasım 2020 |
|**İsveç**| Avrupa Birliği | İsveç | Kasım 2021 |

1 Ekim 2020'den Office 365 Eğitim aboneliği olan müşteriler geçiş için uygun değildir.

Tüm veri merkezi coğrafi konumlarının, veri merkezlerinin ve müşteri verilerinin kalan konumunun tam listesi, etkileşimli veri merkezi [haritaların bir parçası olarak mevcuttur](https://office.com/datamaps). 
  
## <a name="data-residency-option"></a>Veri ikamet seçeneği

Yukarıdaki tabloda yer alan veri merkezi coğrafi verileri kapsamındaki Microsoft 365 müşterilere uygun bir veri ikamet seçeneği sunuyoruz. Bu seçenekle, veri ikamet gereksinimleri olan uygun müşteriler, geri kalan temel müşteri verilerini yeni veri merkezlerine coğrafi olarak geçirme isteğinde olabilir.  Microsoft, kayıt penceresinde geçiş isteyen tüm uygun müşterilere taahhütte son tarihi sunmaktadır.  Veri [merkezinizin açık kayıt penceresi coğrafi](request-your-data-move.md) olarak hakkında daha fazla ayrıntı ve programa kaydolma adımları için Verileri taşıma isteğinde bulunabilirsiniz sayfasını gözden geçirebilirsiniz.  Verinin taşır işleminin tamamlanması, istek döneminin sona erdikten sonra 24 ay kadar sürebilir.

Yeni veri merkezi coğrafi olarak hiç benzersiz özellik, özellik veya uyumluluk sertifikasına sahip yokuz.
    
Genel olarak işletilen ve otomatik bir ortamda veri taşıma işlemleri gerçekleştirmemiz gereken karmaşıklık, duyarlık ve ölçek kiracınız veya tek bir kiracı için bir veri taşıma işleminin tamamlanması beklenende verileri paylaşmamızı yasaklar. Veri taşıma tamamlandığında, müşteriler İleti Merkezi'nde katılımcı hizmetlere göre bir onay mesajı alırlar. 
    
Veri hareketleri, son kullanıcıları çok az etkileyen bir arka uç hizmet işlemidir. Etkilenmiyor olabilir özellikler, Verilerinizi taşıma sırasında ve [sonrasında sayfasında listelenir](during-and-after-your-data-move.md) . Müşterilerin taşıma sırasında hazır veya izlemesi gereken hiçbir şey kalmaması için kullanılabilirlik için Microsoft Çevrimiçi Hizmetler Hizmet Düzeyi Sözleşmesi'ne [(SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) bağlı kalın. Gerekirse, hizmet bakımı yapılır. 

Veriler yeni veri merkezi coğrafi olarak taşınır ve müşteriye hiçbir ek ücret ödemeden tamamlanır.
    
## <a name="related-topics"></a>İlgili konular 
 
[Verilerinizin taşınması nasıl gerekir?](request-your-data-move.md)
    
[Veri taşıma genel SSS](data-move-faq.yml)
  
[Veriler için yeni veri merkezi coğrafi Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Bölgeye göre Azure hizmetleri](https://azure.microsoft.com/regions/)

[Teams Coğrafi Microsoft 365 bir kiraya sahip bir deneyim](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
