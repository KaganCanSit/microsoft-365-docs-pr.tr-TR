---
title: Test Tabanı SSS
description: Sık sorulan soruları gözden geçirme
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 668631563b35a848df5bfbdfd930be17efce8c04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988176"
---
# <a name="test-base-faq"></a>Test Tabanı SSS

**S: Paketlerimizi Test Bankası ekibine nasıl göndereceğiz?**

**A:** Paketlerinizi kendi kendine hizmet eden portalımızı kullanarak doğrudan Test Temel ortamına gönderin.

Uygulama paketinizi göndermek için [Azure Portal'a](https://www.aka.ms/testbaseportal "Test Tabanı Giriş Sayfası") gidin ve kendi kendine hizmet eden Test Temel portalı panosu üzerinden uygulama ikili dosyalarını, bağımlılıklarını ve test betiklerini içeren sıkıştırılmış bir klasörü karşıya yükleyin. 

Daha fazla bilgi için lütfen ekleme kullanıcı kılavuzuna bakın veya yardım ve daha <testbasepreview@microsoft.com> fazla bilgi için ekibimizle iletişime geçin.

**S: Yeni olmayan (OOB) testleri nedir?**

**A:** Standart hale getirildikten sonra uygulama paketleri yüklenir, başlatılacak ve otuz (30) kez kapatılan ve sonra kaldırılan varsayılan test çalıştırmaları standart hale getirılmıştır. 

Test Temel için oluşturulan paketlerde aşağıdaki test betikleri vardır: yükleme, başlatma, kapatma ve isteğe bağlı olarak kaldırma betiği. 

Standart dışı (OOB) testleri, uygulamanız üzerinden standart telemetri sağlar ve bu derlemeleri Windows sağlar.

**S: Hazır gelen testler dışında test gönderebilirsiniz (yükleme, başlatma, kapatma, kaldırma test betikleri)?**

**A:** Evet, müşteriler self servis portal panosu üzerinden **işlevsel testler** için uygulama paketleri de yükleyebilir.
**İşlevsel testler** , müşterilerin betiklerini kendi uygulamasında özel işlevler çalıştırmalarına olanak sağlayan testlerdir.


## <a name="testing"></a>Test

**S: İşlevsel testleri destekliyor musunuz?**

**A:** Evet, Test Tabanı işlevsel testleri destekler. İşlevsel testler, müşterilerimizin betiklerini kendi uygulamasında özel işlevler çalıştırmalarına olanak sağlayan testlerdir. 

Uygulama paketinizi işlevsel test amacıyla göndermek için, uygulama ikili dosyalarını, bağımlılıklarını ve test betiklerini içeren sıkıştırılmış klasörü kendi kendine portal panomuz aracılığıyla karşıya yükleyin. 

Daha fazla bilgi için lütfen ekleme kullanıcı kılavuzuna bakın veya yardım ve daha <testbasepreview@microsoft.com> fazla bilgi için ekibimizle iletişime geçin.

**S: Test Tabanı test verilerimizi nasıl işler?**

**A:** Test Base, Test verilerinizi Azure ortamında güvenli bir şekilde toplar ve yönetir. 

**S: Test Bankası otomatik testlerimizi destekleye devam mı etmek istedi?**

**A:** Evet, Test Bankası otomatik testleri destekler, ancak hizmet özellikleri nedeniyle şu anda el ile yapılan testleri desteklemez.

**S: Otomatik testlerin hangi dil ve çerçevelerini destekliyorsunuz?**

**A:** Tüm dil ve çerçeveleri destekliyoruz. Tüm betikleri PowerShell aracılığıyla çağırıriz. 

Ayrıca gerekli çerçevenin bağımlı ikililerini de sağlay (karşıya yükleme) gerekir.

**S: Test Tabanı test sonuçlarını ne zaman sağlar?**

**A:** Yayın öncesi sürüm derlemeleri üzerinde çalıştırmız her test için, sonuçları Azure Portal pano üzerinde 48 saat içinde [size sunaruz](https://www.aka.ms/testbaseportal "Test Tabanı Giriş Sayfası") .

**S: Yükledikten sonra yeniden başlat biliyor musunuz?**

**A:** Evet, bizim süreç yüklemeden sonra yeniden başlatmayı destekliyor. Ekleme portalında Görevlerinizi ayarlarken "İsteğe bağlı ayarlar" açılır **listesinden bu** seçeneği seçmeye emin olun.

Hazır (OOB) testleri için Yükleme betiği için yeniden başlatma gerekip gerek olmadığını _belirtebilirsiniz._

![Resmi yeniden başlatma.](Media/reboot.png)

İşlevsel testler içinyken, eklenen her betik için yeniden başlatma gerekip gerek olmadığını belirtsiniz.

![İşlevsel testleri seçme.](Media/functionalreboot.png)

**S: Windows sürümleri destekliyorsunuz?**

**A:** Şu anda Windows 10, Windows Server 2016, Windows Server 2016 Core version, Windows Server 2019 ve Windows Server 2019 Çekirdek sürümünü destekliyoruz.

**S: Güvenlik Güncelleştirmesi testleri ile Özellik Güncelleştirmesi testleri arasında ne fark vardır?**

**A:** Güvenlik güncelleştirmesi testlerinde, kullanıcılarımızın her zaman **<ins></ins>** güvenli ve korumalı tutmaya odaklanan aylık yayın öncesi sürüm güvenlik güncelleştirmeleri Windows test edildi. Özellik güncelleştirmesi testlerinde, özelliklere ve özelliklere **<ins></ins>** yönelik yeni özellikler ve özellikler ekan iki yıllık sürüm öncesi özellik güncelleştirmelerinde Windows.

## <a name="debugging-options"></a>Hata Ayıklama seçenekleri

**S: Hata durumunda Sanal Makineler'e (SANAL MAKINELER) erişim elde ediyor muz? Test Bankası neyi paylaşır?**

**A:** Hizmetin uyumlu olması ve yayın öncesi güncelleştirmelerin güvenli olması için, yalnızca Microsoft'un sanal filmlere erişimi olur. Bununla birlikte, müşteriler kilitlenme ve kilitlenme işaretleri, güvenilirlik ölçümleri, bellek ve CPU kullanımı vb. dahil olmak üzere test sonuçlarını ve diğer test ölçümlerini portal panolarında  görebilirsiniz. Ayrıca, indirmek ve daha fazla çözümleme yapmak için panoda test çalıştırma günlüklerini de oluşturabilir ve sağlaruz. 

Ayrıca gerektiğinde kilitlenme hata ayıklaması için bellek dökümü de s sağlamamız gerekir.

**S: Test sırasında sorunlar bulunursa, bu sorunları çözmek için sonraki adımlar neler?**

**A:** Test Bankası ekibi hatanın temel nedenini belirlemek için bir ilk önce değerlendirme işlemi gerçekleştirecek ve bulgularımıza bağlı olarak hata ayıklama için Microsoft içindeki müşteriye veya iç ekiplere yönlendiracağız. 

Tüm sorunları çözmek için her zaman birlikte düzeltme yapmak için müşterilerimizle birlikte çalışıyoruz. 

**S: Microsoft, sorun çözülene kadar güvenlik düzeltme ekini yayımlar mı? Hangi alternatif çözünürlükler kullanılabilir?**

**A:** Test Temel'in amacı, ortak son müşterilerimizin hiçbir sorunla karşı karşıya olmasını garanti etmektir. Yazılım Satıcıları ile birlikte sürümden önce herhangi bir sorunu çözmek için çok çalışıyoruz, ancak düzeltmenin uygun çalışmama durumu için shimler ve bloklar gibi başka çözümlarımız var.

## <a name="miscellaneous"></a>Diğer

**S: Hizmet, önceden var olan bir sunucuyla nasıl çalışır?**

**A:** Şu anda, prem sunucuları için destek sağlanmaz. Öte yandan, sunucu HTTP uç noktasını açığa çıkarıyorsa, İnternet üzerinden bağlanabilirsiniz.

**S: Who ana bilgisayarlarını nasıl barındırıyor?**

**A:** Microsoft, bu hizmet için VM'yi sağlar ve bunun yükünü müşteriden sağlar.

**S: Bu hizmet web, mobil veya masaüstü uygulamalarını destekliyor mu?**

**A:** Şu anda odak noktası masaüstü uygulamalarıdır, bununla birlikte, gelecekte web uygulamaları eklemeyi planlıyoruz, ancak şu anda mobil uygulamaları desteklememektedir.

**S: Test Tabanı ile ARACıNıN arasındaki fark nedir?**

**A:** Test Tabanı ile THEP arasındaki en büyük fark, iş ortaklarımızın uygulamaları, testlerden kendi çıkarları yerine, doğrulama için Test Temel Azure ortamına eklemeleridir. 

Sürüm öncesi güvenlik güncelleştirmeleri testlerine ek olarak, platformumuz üzerinde yayın öncesi özellik güncelleştirmeleri testlerini de destekliyoruz. Yol haritamızda başka türde güncelleştirmeler ve işletim sistemi testlerimiz var.

**S: Hizmetle ilişkilendirilmiş bir ücret var mı?**

**A:** Test Temel hizmeti Genel Kullanılabilirlik (GA) tarihine kadar kullanıcılara ücretsiz olarak sağlanır. Bu zaman içinde tüm müşteriler için yürürlüğe girecek bir maliyet yapısını duyuracak. 

**S: Test Tabanı hakkında nasıl geri bildirim s olabilirim?**

**A:** Test Tabanı hakkında geri bildiriminizi paylaşmak için **portalın sol** alt köşesindeki Geri Bildirim simgesini seçin. Microsoft'un geri bildiriminizi daha iyi an an önce an göndermenize yardımcı olmak için gönderinize bir ekran görüntüsü ekleme. 

Ayrıca ürün önerilerini gönderebilirsiniz ve 'da diğer fikirleri destek oya atabilirsiniz <testbasepreview@microsoft.com>.
