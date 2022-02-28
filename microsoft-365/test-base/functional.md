---
title: Test Temel'de işlevsel test
description: Mevcut otomatik işlevsel testlerle uygulamanızı test ayrıntıları
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
ms.openlocfilehash: f64480d66cd91dc4b08f9694331cfe0d9c130ee4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985016"
---
# <a name="functional-testing"></a>İşlevsel test

Yazılım satıcısı olarak, artık M365 için self servis Test Temel'i kullanarak istediğiniz test çerçevesini kullanarak özel işlevsel testler gerçekleştirebilirsiniz. 

Hizmeti ilk kez başlattığımızda, standartleştirilmiş betik aracılığıyla yönlendiren ve önceden tanımlanmış bir dizi test olan Hazır testler sunduk. Öte yandan bu, birçok Bağımsız Yazılım Satıcı (ISV) için tam test kapsamına ulaşamayebiliyordu. 

Bu nedenle, geri bildirimlerinize yanıt olarak ISV'lerimize otomatik işlevsel testleri karşıya yükleme olanağı sağlıyoruz.

Bu özelliği kullanmak için aşağıdaki adımları izleyin:

1. Upload (ikili dosyalar, bağımlılıklar ve betikler) tek bir dosya paketi .zip.
2. Çeşitli yürütme noktalarında test Sanal Makinelerini (SANAL MAKINELER) yeniden başlatmak mı istediğinize karar seçin.
3. Betikleriniz için kullanılabilir seçenekleri yönetin.
4. Yürütme sırasında VM'de Windows güncelleştirmesini ne zaman uygulayacaklarını seçin.

Yukarıdaki adımların ayrıntılı açıklamaları aşağıda vurgulanmıştır:

**Upload bir test paketidir**

Çalışmaya başlamak için, Upload sayfasına gidin, Azure'Upload M365 için Test Temel'in sol tarafındaki gezinti menüsündeki Uygulama kataloğu altında yeni bir uygulama seçin. Buradan:

Sekme 1 - Temel bilgileri girin. Uygulamanın adını ve sürümünü girin. Test türü seçeneğinde öğesini seçin ```Functional tests```. 

*Varsayılan olarak, Kutusu Dışında (OOB) seçeneğinin gerekli olduğunu unutmayın.*


![İşlevsel test sekmesini seçin.](Media/functional_testing_tab1.png)

2. Sekme: Upload tüm test (ikili dosyalar, bağımlılıklar, betikler vb.) ile bir zip dosyası yükerek paketinizin bileşenlerini düzenleyin. 

Ayrıntılar aka.ms/usl-package-outline bilgi için bkz. (Not: Hem İlk Çalıştırma testi betikleri hem de İşlevsel test içeriği aynı zip dosyasına yerleştirilsin). Şu anda, dosya boyutu 2 GB ile sınırlıdır.

Sekme 3 - Kutusu Dışında ve İşlevsel test görevlerini yapılandırma. Burada, powershell betiklerinin yollarını seçin; bu betikleri, hem uygulamanızı başlatacak, kapatacak ve kaldıracak (Hazır Kutusu Dışında) hem de tüm özel betiklerinizi işlevsel testlerinizi gerçekleştirmek için bunların yollarını seçin. **(Not: Uygulama kaldırma betiği isteğe bağlıdır).**

Şu anda, işlevsel testlerinizi yüklemek için 1 ile 8 arasında betik yükleyebilirsiniz. (Daha fazla betikye ihtiyacınız varsa, bu gönderiye lütfen yorum olun!)

![Upload testi olan en fazla 8 betik içerir.](Media/functional_testing_tab3.png)

(İsteğe bağlı) Yüklemeden sonra yeniden başlatmayı yapılandırma. Bazı uygulamalar yüklemeden sonra yeniden başlatmayı gerektirir. 

Bu ```Reboot After Execution``` betiğin yürütülmesi sonrasında bir yeniden başlatmanın yürütülmesini istediğiniz belirli Betik için Görevler sekmesindeki seçimi yapın.

4. Sekme - Windows güncelleştirmenin ne zaman yüklenimini seçin: En son Güncelleştirme Windows uygulaması, seçtiğiniz herhangi bir betikten önce yapılır. Uygulamanın yüklenmesi sonrasında, gerçek Windows kullanım senaryolarınızı yakından taklit etmek için bir güncelleştirme güncelleştirmesini yüklemeniz önerilir.

![En Windows güncelleştirmesi, belirli bir betik sonrasında yükleyebilir.](Media/functional_testing_tab4.png)

Sekme 5 - Paketi gözden geçirin ve oluşturun. Yukarıda listelenen adımları tamamlandıktan sonra, karşıya yükleme ```Create``` işlemini tamamlamak için öğesini seçin.

Paketiniz oluşturulduktan sonra paketinizin doğrulama durumunu kontrol edin.

Uygulamanızı yüklemek, başlatmak, kapatmak ve kaldırmak için bir başlangıç testi çalıştırdık. Bu, paketinizin hatasız olarak hizmetimize yüklenemediklerini doğrulamamıza olanak sağlar.

Doğrulama işlemi 24 saat kadar sürebilir. Doğrulama tamamlandıktan sonra, menüde durumu görebilir ```Manage packages``` ve şu iki girişlerden birini kullanabilirsiniz:

1. Doğrulama başarılı olur: Paket, seçtiğiniz işletim sistemi derlemeleri için Windows öncesi sürüm güncelleştirmeleri ile otomatik olarak test edilecektir.
veya
2. Doğrulama başarısız: Başarısızlığın nedenlerini araştırmanız, sorunu düzeltmeniz ve paketinizi yeniden karşıya yüklemeniz gerekir.

Ayrıca, her iki sonucun da Azure portalda bildirim simgesi aracılığıyla size bildirilmesi gerekir.
