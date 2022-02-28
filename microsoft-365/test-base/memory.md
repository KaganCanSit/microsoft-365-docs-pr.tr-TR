---
title: Bellek regresyon çözümlemesi
description: Bellek regresyonu nasıl çıkar?
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
ms.openlocfilehash: c4c6ec61ea96966237976ea71b82931e37efd278
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988175"
---
# <a name="memory-regression-analysis"></a>Bellek Regresyon Çözümlemesi

Test Tabanı, uygulamalarınızı çalıştıran test VM'lerde önemli bellek kullanımının arttıkça olduğunu daha net farknıza yardımcı olur. Bellek kullanımı gibi performans ölçümleri genel uygulama durumuna işaret edebilir ve bu eklemenin uygulamalarınızı en iyi şekilde gerçekleştirmesini büyük ölçüde yardımcı olacağını inanıyoruz.

Diğer ayrıntılar için okumaya devam edin veya en son iyileştirmeleri hızlıca izlemek için bu videoyu izleyin. 

M365'in regresyon çözümlemesinde yardımcı olmak için sınanma olanağı hakkında daha fazla bilgi için bkz. İşlem güvenilirliğine dayalı regresyon sonuçları.

<b>Bellek regresyonlarına daha yakından bakma</b>

M365 için Test Temel panosu, yeni yayımlanan bir Windows güncelleştirmesinde uygulamanız tarafından kullanılan belleği gösterir ve bu belleği son yayımlanan Windows bellekle karşıtır. 

Bu ayın geliştirmeleriyle birlikte, sık kullanılan işlemleriniz arasında artık bellek gerileme çözümlemesi öne çıktı. Uygulamalar birden çok işlem içerebilir ve Güvenilirlik sekmesi aracılığıyla sık kullanılan işlemlerinizi kendiniz seçebilirsiniz. Daha sonra hizmetimiz, bu sık kullanılan işlemlerde bellek gerilemelerini tanımlayabilir ve test karşılaştırması farklı güncelleştirme Windows yayımlar. Bir regresyon algılanırsa, regresyonla ilgili ayrıntılar kolayca kullanılabilir.

Şimdi bu özelliği ayrıntılı olarak incelealım ve Windows Performance Analyzer kullanarak bellek gerilemelerini nasıl giderebilirsiniz?

Bellek regresyon nedeniyle oluşan hata sinyali, Bellek Kullanımı altındaki Test sonuçları sayfasındaki M365 için Test Tabanı panosunda gösterilir:

![Bellek kullanımı sonuçları.](Media/01_memory-utilization-results.png)


Bellek tüketimi daha yüksek olduğu için uygulamanın başarısız olması Test Özeti ```Fail``` sayfasında da görüntülenir:

![Test özeti sonuçları.](Media/02_test-summary.png)

Bu hata sinyallerini ön plana çıkararak, amacımız, uygulamanız için son kullanıcı deneyimini kesintiye neden olan ve etki altında tutulacak olası sorunları açıkça bayrakla işaret etmektir. 

Daha fazla araştırma yapmak için günlük dosyalarını indirebilir ve Windows Çözümleyicisi'ne veya tercih ettiğiniz araç setini kullanabilirsiniz. Ayrıca, sorunu düzeltme ve son kullanıcıları etkileyen sorunları önlemeye yardımcı olmak için M365 için Test Temel'i birlikte çalışabilirsiniz.

Bellek işaretleri, tüm test çalıştırmaları için M365 için Test Tabanı hizmetinin Bellek Kullanımı sekmesinde yakalanır. Aşağıdaki örnekte, Ağustos 2020 ön sürüm güvenlik güncelleştirmesi ile birlikte "Test Bellek Stresi" uygulamasıyla birlikte yeni bir test çalıştırıldı. (Bu uygulama, ekibimiz tarafından bellek gerilemelerini göstermek için yazılmıştır.)

![Bellek regresyon sonuçları.](Media/03_memory-regression%20comparison.png)

Bu örnekte, sık kullanılan işlem "USLTestMemoryStress.exe" işlemi, Temmuz güncelleştirmesi ile karşılaştırıldığında sürüm öncesi Ağustos güncelleştirmesinde ortalama 100 MB tüketmektedir; dolayısıyla M365 için Test Temeli bir regresyon tanımlanır. 

Burada "USLTestMemoryStress_Aux1.exe" ve "USLTestMemoryStress_Aux2.exe" olarak gösterilen diğer işlemler de aynı uygulamaya aittir, ancak iki sürümün yaklaşık olarak aynı miktarda bellek tüketmesi dolayısıyla "geçti" ve sağlıklı kabul edilirler.

Ana işlemde regresyon "istatistiksel olarak anlamlı" olarak belirlendi, böylece hizmet bu farkı kullanıcıya iletecek ve vurgular. Karşılaştırma istatistiksel olarak anlamlı olsaydı, vurgulanmazdı. Bellek kullanımı gürültülü olabilir, dolayısıyla derlemeler ve sürümler arasında tutarsız farklılıklara karşı anlamlı farkları ayırt etmek için istatistiksel modeller kullanıyoruz. 

Doğru fark (hatalı pozitif) olduğunda karşılaştırma nadiren işaretlenir, ancak bu regresyonları (veya doğru pozitif pozitifleri) doğru tanımlama olasılığını geliştirmek için gerekli bir ticari karşılıktır.

Sonraki adım, bellek gerilemenin neden olduğunu anlamaktır. Aşağıda gösterildiği gibi, Günlük dosyalarını indir seçeneğinden her iki yürütme için de zip dosyalarını indirebilirsiniz. 

Bu zip dosyaları, ETL dosyasında bulunan betik sonuçları ve bellek ve CPU performans verileri de içinde olmak üzere test çalıştırma sonuçlarınızı içerir.

![Bellek gerileme test dosyaları.](Media/04_memory-regression-test-files.png)

İki test çalıştırması için günlükleri indirip sıkıştırmayı açabilirsiniz, ardından her klasör içinde ETL dosyasını bulup bunları hedef.etl (sürüm öncesi güncelleştirmede test çalıştırma için) ve temel.etl (son yayımlanan güncelleştirmede test çalıştırması için) olarak yeniden adlandırarak araştırmayı ve gezintiyi basitleştirebilirsiniz.
 
## <a name="next-steps"></a>Sonraki adımlar

Akıllı CPU regresyon çözümlemesini anlamaya başlamak için sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Sonraki adım](cpu.md)

<!---
Add button for next page
-->
