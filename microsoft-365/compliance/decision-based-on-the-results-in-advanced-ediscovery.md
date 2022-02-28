---
title: Karar, sonuçların temel Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: aed65bcd-0a4f-43e9-b5e5-b98cc376bdf8
description: Advanced eDiscovery'daki Karar Advanced eDiscovery gözden geçirme dosya kümelerinin doğru boyutunu belirlemenize yardımcı olacak verileri nasıl sağladığını öğrenin.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 32682690c6febac247d67e3b78f56d1f71b9a2fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988616"
---
# <a name="decisions-based-on-relevance-results-in-advanced-ediscovery"></a>İlgi düzeyi sonuçlarına dayalı kararlar Advanced eDiscovery
  
Advanced eDiscovery'daki İlgi Düzeyi modülünde, Karar sekmesi, gözden geçirme dosyalarının boyutunu belirlemek için karar destek istatistiklerini görüntülemek ve kullanmak için ek bilgiler sağlar.
  
## <a name="using-the-decide-tab"></a>Karar ver sekmesini kullanma

![İlgi DüzeyiNe Karar Verme.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Bu sekme aşağıdaki bileşenleri içerir:
  
- **Sorun**: Buradan, ilgi alanlarından sorunu listeden seçebilirsiniz.

- **Gözden geçirme-geri çekme** oranı: İlgi dereceleri Advanced eDiscovery gözden geçirme karşılaştırmaları. Grafikte Kesme noktası, gözden geçirilecek dosyaların ilgi derecesi puanına eşlenen yüzdesini temsil eder. Bu, İlgi Düzeyi Testi aşamasında ve kültür için Dışarı Aktarma eşiği olarak kullanılır. Gözden geçirilecek dosya sayısı için varsayılan kesme noktası, Geri Çekme ile Duyarlık arasındaki bakiyenin en uygun olduğu noktadadır. Gerçek kesme noktası, hedefler ve maliyete (gözden geçirme) ve riske (%geri çekme) bağlı olarak kullanıcı tarafından belirlenecektir. Kaydırıcıyı kullanarak kesme kesme noktasını ayarlayabilir, uygun dosyaların yüzdesini ayarlarken ve bir kararı doğrulamadan önce grafik ve parametreler üzerindeki etkisi görebilirsiniz.

- **Parametreler**: Gözden Geçirme, Geri Çekme, Sonraki ilgili ve Toplam maliyet parametreleri, tüm vakanın koleksiyonuna ilişkin gözden geçirme kümesiyle ilgili kümülatif hesaplanan istatistiklerdir. Bu parametrelerin tanımları aşağıdaki gibidir:

  - **Gözden** Geçir: Bu kesme kesmeye dayalı olarak gözden geçirilecek dosyaların yüzdesi.

  - **Geri** Çekme: Gözden geçirme kümesinde ilgili dosyaların yüzdesi.

  - **Sonraki uygun**: Gözden geçirme kümesinde yer alan ve ilgili başka bir dosyayı inceleme maliyeti.

  - **Toplam maliyet**: Dava dosyalarının bu yüzdesini gözden geçirme maliyeti. Maliyet parametresi ayarları Büyük/Harf Yöneticisi tarafından ayarlanır.

  - **İlgi düzeyi puanına** göre dağılım: Solda koyu gri görünen dosyalar, kesmeoff puanının altında yer almaktadır. Araç ipucu, İlgi Derecesini ve toplam dosyalara göre ayarlanmış gözden geçirme dosyasındaki dosyaların ilgili yüzdesini görüntüler.

Genişletilmiş Ayrıntılar **bölmesi** daha fazla ayrıntı görüntüler. Koleksiyon rakamlarında yer alan dosyalar boş veya ampul dosyaları içermez. Aile dosyaları rakamları, Ilgi Düzeyi'ne yüklenmemiş ancak yine de ailenin bir parçası olarak say edilen dosyaları temsil ediyor.
