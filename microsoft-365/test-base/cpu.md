---
title: CPU regresyon çözümlemesi
description: CPU tüketimi için regresyon sonuçlarını ve ölçümleri anlama
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 935781e929c159918f8a0aec3b4a551ab974480f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985341"
---
# <a name="intelligent-cpu-regression-analysis"></a>Akıllı CPU regresyon çözümlemesi

CPU kullanımı bir uygulamanın işletim sistemi güncelleştirmeden etkileniyor olup olmadığını gösteriyor olabilir. 

Microsoft 365 Test Base, yazılım geliştiricilere uygulamaları yaklaşan bir Windows İşletim Sistemi (OS) güncelleştirmesinde farklı sürümlerde çalışan CPU performans gerilemeleri hakkında bilgi sağlar. 

Bu CPU gerilemeleri, geliştiricilerin işletim sistemi güncelleştirmesini genel olarak dağıtılmadan önce uygulama sorunlarını (ve olası hataları) algılamasını ve çözmesini sağlar, bu da son kullanıcı için kötü bir deneyim sağlar.


### <a name="how-cpu-regression-analysis-works"></a>CPU regresyon çözümlemesi nasıl çalışır? ###

Test Bankası kullanıcısı olarak, ilişkili test betikleriyle birlikte uygulama ikili dosyalarını (tek bir .zip dosyasında) karşıya yükleyebilir ve Azure'daki Test Temel portalında uygulamanızı test etmek istediğiniz Windows işletim sistemi sürümünü kullanabilirsiniz. 

Ardından Test Temel hizmeti test betiklerini çalıştırır ve **CPU Regresyon Çözümlemesi yapar**. 

Hizmet, hedef işletim sistemi için güncelleştirmenin yayın öncesi sürümünde uygulamanın CPU kullanımının, işletim sistemi sürümünün yayımlanan SÜRÜMÜNE göre CPU kullanımına uygun olup olduğunu denetler. 

CPU kullanımı% 100 benzer karşılaştırma değildir, çünkü işletim sistemi iki sürümü üzerinde çalışan işlemler farklı işletim sistemi sürümlerine bağlı olarak tam eşleşme olabilir veya tam eşleşmesi olamayabiliyor; Bununla birlikte, Test Temel tarafından gerçekleştirilen çözümleme, uygulamanıza yönelik CPU kullanımının yaklaşan bir işletim sistemi güncelleştirmelerinden etki edip etkilememektedir ve özellikle de önceki test çalıştırmalarından geri dönüşte olan işlemleri gösterebilir.

Aşağıdaki anlık görüntüde, aynı uygulama için CPU kullanımının karşılaştırıldığında iki işletim sistemi sürümü vardır. 
-   CPU kullanımı sekmesi, sırasıyla 90. ve 10. yüzdebirlik sürümlerde her iki sürümün de kullanımının üst ve alt sınırlarını gösterir. 
-   Grafikler, ortalama kullanımın yanı sıra CPU kullanımının zaman serisini de gösterir. 

Müşteriler artık, uygulamanın CPU kullanımının işletim sistemi güncelleştirmelerinden etki olup olmadığını ve özellikle de önceki yürütmelerinden hangi işlemlerin geri azaldıklarını belirlemek için bu işlevselliği kullanabilirler.


![CPU regresyon çözümlemesi.](Media/cpu-regression-analysis.jpg)

### <a name="relevant-process-identification"></a>İlgili Süreç Kimliği ###

Burada, uygulama içinde gerilemeli işlemlerin nasıl tanımlan uygulaması olduğunu tartışalım. 

Performans regresyonlarını çözümlemek, test çalıştırma sırasında sanal bir makinede çalışan her işlem için farklı türde performans sayaçları izlemeyi gerektirir. 

Bu çözümleme, verilen bir uygulama için çok sayıda işlem için çok sayıda değişken yakalar. Tüm işlemler bir çalıştırma veya uygulamayla ilişkilendirilz. Bu zorluka çözüm olarak, verilen bir uygulama için en uygun süreçleri ortaya konulan olasılık ve bilgi teorisini kullanan bir ortak bilgi derecelendirme algoritması uygulanır. 

Bir uygulama ayrık rastgele değişken türlerinden biri olarak kabul edilirken, işlem başka türde ayrık rastgele değişken olarak kabul edilir. İki rastgele değişkenin ilişkilendirmesi, ilgi düzeyi için koşullu olasılıklar kullanılarak ölçülür. 

İşlemler, her uygulamayla ilgili ilgi derecelerine göre görüntülenir. Ayrıca, varsayılan olarak izleniyor olabilir ve CPU regresyon çözümlemesi için ilgili işlemlerle birlikte, bir işlem alt kümesini sık kullanılanlara sıntırın. Bir regresyon algılandığında, En Düşük Performans Çözümleyicisi araç seti Windows CPU performans gerilemelerinin nedenlerini çözümebilirsiniz. 

Veri Windows Çözümleyicisi, giriş olarak olay izleme günlüğü (ETL) alır ve bu .etl dosyaları portalda test için indirilebilir günlük dosyalarında kullanılabilir. CPU performansı hata ayıklaması hakkında daha fazla bilgi için bkz. Windows Çözümleyicisi belgelerine bakın.

