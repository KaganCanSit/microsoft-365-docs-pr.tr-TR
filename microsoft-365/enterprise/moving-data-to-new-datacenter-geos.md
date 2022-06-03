---
title: Temel verileri yeni Microsoft 365 veri merkezi coğrafi bölgelerine taşıma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Yeni Office 365 veri merkezi coğrafi alanları ve çekirdek verilerinizin yeni bir coğrafi bölgeye taşınmasını istemek için veri yerleşimi seçeneğini kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c70d59edba9cd35710b315adc8f93d6139fd2595
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873588"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Temel verileri yeni Microsoft 365 veri merkezi coğrafi bölgelerine taşıma

Microsoft 365 hizmetleri için yeni veri merkezi coğrafi alanları açmaya devam ediyoruz. Bu yeni veri merkezi coğrafi alanları, devam eden müşteri talebimizi ve kullanım büyümemizi desteklemek için kapasite ve işlem kaynakları ekler. Ayrıca yeni veri merkezi coğrafi bölgeleri, temel müşteri verileri için coğrafi veri yerleşimi sunar.

Temel müşteri verileri, aşağıdakiler de dahil olmak üzere müşteri verilerinin bir alt kümesini ifade eden bir terimdir:

- posta kutusu içeriğini (e-posta gövdesi, takvim girdileri ve e-posta eklerinin içeriği) Exchange Online
- çevrimiçi site içeriğini ve bu sitede depolanan dosyaları SharePoint
- OneDrive İş karşıya yüklenen dosyalar
- Özel iletiler, kanal iletileri ve sohbetlerde kullanılan görüntüler dahil olmak üzere sohbet iletilerini Teams
  
Çekirdek müşteri verilerinin zaten var olan bir veri merkezi coğrafi alanında depolandığı mevcut müşteriler, yeni bir veri merkezi coğrafi alanının başlatılmasından etkilenmez. Yeni veri merkezi coğrafi konumuyla benzersiz özellikler, özellikler veya uyumluluk sertifikaları sunmayız. Bu iki coğrafi bölgeden herhangi birinde müşteri olarak, daha önce yaşadığınız hizmet kalitesi, performans ve güvenlik denetimleriyle aynı deneyime sahip olacaksınız. Aşağıdaki tabloda listelenen mevcut müşterilere, bekleyen kuruluşlarının temel müşteri verilerinin yeni veri merkezi coğrafi bölgelerine erken geçişini isteme seçeneği sunuyoruz.
  
| Kiracı kayıt ülkesi olan müşteriler | Önceki veri merkezi coğrafi konumu | Yeni veri merkezi coğrafi konumu | Coğrafi olarak şu tarihten itibaren kullanılabilir: |
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

1 Ekim 2020 itibarıyla kiracıya dahil Office 365 Eğitim aboneliği olan müşteriler geçiş için uygun değildir.

Tüm veri merkezi coğrafi bölgelerinin, veri merkezlerinin ve bekleyen müşteri verilerinin konumunun tam listesi [, etkileşimli veri merkezi haritalarının](https://office.com/datamaps) bir parçası olarak kullanılabilir.
  
## <a name="data-residency-option"></a>Veri yerleşimi seçeneği

Yukarıdaki tabloda listelenen veri merkezi coğrafi bölgelerinin kapsamına giren Microsoft 365 müşterileri uygun hale getirmek için bir veri yerleşimi seçeneği sunuyoruz. Bu seçenekle, veri yerleşimi gereksinimleri olan uygun müşteriler, bekleyen kuruluşlarının temel müşteri verilerinin yeni veri merkezi coğrafi bölgelerine geçirilmesini isteyebilir.  Microsoft, kayıt penceresi sırasında geçiş isteyen tüm uygun müşterilere taahhüt edilen bir son tarih sunar.  Veri merkezi [coğrafi bölgenizin](request-your-data-move.md) açık kayıt penceresi ve programa kaydolma adımları hakkında daha fazla bilgi için Verilerinizi taşıma isteğinde bulunma sayfasını gözden geçirin.  Veri taşıma işleminin tamamlanması, istek süresinin sona ermesi 24 aya kadar sürebilir.

Yeni veri merkezi coğrafi konumuyla benzersiz özellikler, özellikler veya uyumluluk sertifikaları sunmayız.

Genel olarak çalıştırılan ve otomatikleştirilmiş bir ortamda veri taşıma gerçekleştirmemiz gereken karmaşıklık, hassasiyet ve ölçek, kiracınız veya başka bir tek kiracı için bir veri taşıma işleminin tamamlanması beklendiğinde paylaşmamızı engeller. Müşteriler, veri taşıma işlemi tamamlandığında katılımcı hizmet başına İleti Merkezi'nde bir onay alır.

Veri taşıma, son kullanıcılar üzerinde en az etkiye sahip bir arka uç hizmeti işlemidir. Etkilenebilen özellikler [, Verilerinizi taşıma sırasında ve sonrasında](during-and-after-your-data-move.md) sayfasında listelenir. Kullanılabilirlik için [Microsoft Online Services Hizmet Düzeyi Sözleşmesi'ne (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) bağlıyız, dolayısıyla taşıma sırasında müşterilerin hazırlaması veya izlemesi gereken hiçbir şey yoktur. Gerekirse herhangi bir hizmet bakımı bildirimi yapılır.

Yeni veri merkezine taşınan veriler müşteriye ek ücret ödemeden tamamlanır.

## <a name="related-topics"></a>İlgili konular

[Veri taşıma isteğinde bulunma](request-your-data-move.md)

[Veri taşıma genel SSS](data-move-faq.md)
  
[Microsoft Dynamics CRM Online için yeni veri merkezi coğrafi bölgeleri](/power-platform/admin/new-datacenter-regions)
  
[Bölgeye göre Azure hizmetleri](https://azure.microsoft.com/regions/)

[Microsoft 365 Çok Coğrafi Özellikli kiracıda Teams deneyimi](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
