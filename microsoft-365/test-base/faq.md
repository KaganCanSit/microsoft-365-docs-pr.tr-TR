---
title: Test Temeli SSS
description: Sık sorulan soruları gözden geçirin
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
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
ms.openlocfilehash: c7fd01b95d461332baaf4eac90aee4715da3e55e
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953040"
---
# <a name="test-base-faq"></a>Test Temeli SSS

**S: Paketlerimizi Test Temeli ekibine nasıl gönderebiliriz?**

**A:** Kendi kendine hizmet portalımızı kullanarak paketlerinizi doğrudan Test Temeli ortamına gönderin.

Uygulama paketinizi göndermek için [Azure Portal'a](https://www.aka.ms/testbaseportal "Test Temeli Giriş Sayfası") gidin ve kendi kendine hizmet sunan Test Temeli portalı panosu aracılığıyla uygulamanızın ikili dosyalarını, bağımlılıklarını ve test betiklerini içeren sıkıştırılmış bir klasörü karşıya yükleyin.

Daha fazla bilgi için ekleme kullanıcı kılavuzuna bakın veya yardım ve daha fazla bilgi için adresinden <testbasepreview@microsoft.com> ekibimize başvurun.

**S: Kullanıma açılan (OOB) testler nelerdir?**

**A:** Hazır (OOB) testler standartlaştırılmıştır, uygulama paketlerinin yüklendiği, otuz (30) kez başlatıldığı ve kapatıldığı varsayılan test çalıştırmalarıdır ve ardından kaldırılır.

Test Temeli için oluşturulan paketlerde şu test betikleri bulunur: yükleme, başlatma, kapatma ve isteğe bağlı olarak kaldırma betiği.

İlk çalıştırma (OOB) testleri, Windows derlemeleri karşılaştırmak için uygulamanızda standart telemetri sağlar.

**S: İlk çalıştırma testlerinin dışında test gönderebilir miyiz (yükleme, başlatma, kapatma, test betiklerini kaldırma)?**

**A:** Evet, müşteriler self servis portal panosu aracılığıyla **işlevsel testler** için uygulama paketlerini de karşıya yükleyebilir.
**İşlevsel testler** , müşterilerin kendi uygulamaları üzerinde özel işlevler çalıştırmak için betiklerini yürütmesine olanak tanıyan testlerdir.

## <a name="testing"></a>Test

**S: İşlevsel testleri destekliyor musunuz?**

**A:** Evet, Test Temeli işlevsel testleri destekler. İşlevsel testler, müşterilerimizin kendi uygulamaları üzerinde özel işlevler çalıştırmak için betiklerini yürütmesini sağlayan testlerdir.

İşlevsel test için uygulama paketinizi göndermek için, self servis portal panomuz aracılığıyla uygulamanızın ikili dosyalarını, bağımlılıklarını ve test betiklerini içeren sıkıştırılmış klasörü karşıya yükleyin.

Daha fazla bilgi için ekleme kullanıcı kılavuzuna bakın veya yardım ve daha fazla bilgi için adresinden <testbasepreview@microsoft.com> ekibimize başvurun.

**S: Test Temeli test verilerimizi nasıl işler?**

**A:** Test Tabanı, Azure ortamında test verilerinizi güvenli bir şekilde toplar ve yönetir.

**S: Test Temeli otomatikleştirilmiş testlerimizi destekleyebilir mi?**

**A:** Evet, Test Temeli otomatikleştirilmiş testleri destekler, ancak hizmet özellikleri nedeniyle şu anda el ile testleri desteklemiyoruz.

**S: Otomatikleştirilmiş testlerin hangi dillerini ve çerçevelerini destekliyorsunuz?**

**A:** Tüm dilleri ve çerçeveleri destekliyoruz. Tüm betikleri PowerShell aracılığıyla çağırırız.

Ayrıca gerekli çerçevenin bağımlı ikili dosyalarını sağlamanız (karşıya yüklemeniz) gerekir.

**S: Test Tabanı test sonuçlarını ne kadar sürede sağlar?**

**A:** Yayın öncesi derlemelerde çalıştırdığımız her test için [Azure Portal](https://www.aka.ms/testbaseportal "Test Temeli Giriş Sayfası") panonuzda 48 saat içinde sonuç sağlayacağız.

**S: Yüklemeden sonra yeniden başlatılabilir misiniz?**

**A:** Evet, işlemimiz yüklemeden sonra yeniden başlatmayı destekler. Ekleme portalında **Görevlerinizi** ayarlarken "İsteğe bağlı ayarlar" bırakma listesinden bu seçeneği belirlediğinizden emin olun.

İlk çalıştırma (OOB) testleri için _Yükleme betiği_ için yeniden başlatma gerekip gerekmediğini belirtebilirsiniz.

![Resmi yeniden başlatın.](Media/reboot.png)

İşlevsel testler için, eklenen her betik için yeniden başlatma gerekip gerekmediğini belirtebilirsiniz.

![İşlevsel testleri seçme.](Media/functionalreboot.png)

**S: Hangi Windows sürümlerini destekliyorsunuz?**

**A:** Şu anda Windows 10 istemcileri, Windows Server 2016, Windows Server 2016 Core sürümü, Windows Server 2019 ve Windows Server 2019 Core sürümünü destekliyoruz.

**S: Güvenlik Güncelleştirmesi testleri ile Özellik Güncelleştirmesi testleri arasındaki fark nedir?**

**A:** Güvenlik güncelleştirme testleri için, kullanıcılarımızın her zaman güvenli ve korumalı kalmasına odaklanan **<ins>Windows'da aylık yayın öncesi güvenlik güncelleştirmelerini</ins>** test ederiz. Özellik güncelleştirme testleri için, Windows yeni özellikler ve özellikler sunan **<ins>iki yıllık yayın öncesi özellik güncelleştirmelerini</ins>** test ediyoruz.

## <a name="debugging-options"></a>Hata ayıklama seçenekleri

**S: Hata durumunda Sanal Makineler (VM) erişimimiz var mı? Test Temeli neleri paylaşır?**

**A:** Hizmetin uyumlu olması ve yayın öncesi güncelleştirmelerin güvenli olması için vm'lere yalnızca Microsoft'un erişimi vardır. Ancak müşteriler, kilitlenme ve kilitlenme sinyalleri, güvenilirlik ölçümleri, bellek ve CPU kullanımı gibi test sonuçlarını ve diğer test ölçümlerini portal panolarında görüntüleyebilir. Ayrıca indirme ve daha fazla analiz için panoda test çalıştırmalarının günlüklerini oluşturur ve sağlarız.

Gerektiğinde kilitlenme hata ayıklaması için bellek dökümleri de sağlayabiliriz.

**S: Test sırasında sorunlar bulunursa, bu sorunları çözmek için sonraki adımlar nelerdir?**

**A:** Test Tabanı ekibi, hatanın kök nedenini belirlemek için bir ilk önceliklendirme işlemi gerçekleştirecek ve bulgularımıza bağlı olarak hata ayıklama için Microsoft'taki müşteriye veya iç ekiplere yönlendireceğiz.

Sorunları çözmek için müşterilerimizle her zaman ortak bir düzeltmede yakın çalışıyoruz.

**S: Microsoft, sorun çözülene kadar güvenlik düzeltme ekinin yayınını barındırıyor mu? Hangi alternatif çözünürlükler kullanılabilir?**

**A:** Test Temeli'nin amacı, ortak son müşterilerimizin herhangi bir sorunla karşılaşmamasını sağlamaktır. Sürümden önceki sorunları çözmek için Yazılım Satıcıları ile çok çalışacağız, ancak düzeltmenin uygun olmaması durumunda dolgular ve bloklar gibi başka çözümlerimiz var.

## <a name="miscellaneous"></a>Çeşitli

**S: Hizmet şirket içi bir sunucuyla nasıl çalışır?**

**A:** Şu anda şirket içi sunucular için destek sağlanmıyor. Ancak, sunucu HTTP uç noktasını açığa çıkartıyorsa, İnternet üzerinden bu uç noktaya bağlanabiliriz.

**S: VM'leri Who barındırıyor?**

**A:** Microsoft, bu hizmet için VM'yi sağlar ve bunun yükünü müşteriden alır.

**S: Bu hizmet web, mobil veya masaüstü uygulamalarını destekliyor mu?**

**A:** Şu anda masaüstü uygulamalarına odaklanıyoruz ancak gelecekte web uygulamaları ekleme planlarımız var ancak şu anda mobil uygulamaları desteklemiyoruz.

**S: Test Tabanı ile SUVP arasındaki fark nedir?**

**A:** Test Temeli ile SUVP arasındaki en büyük fark, iş ortaklarımızın testlerin kendileri yerine yayın öncesi güncelleştirmelere karşı doğrulanması için uygulamalarını Test Temeli Azure ortamına eklemeleridir.

Yayın öncesi güvenlik güncelleştirmeleri testine ek olarak platformumuzda yayın öncesi özellik güncelleştirmeleri testlerini destekliyoruz. Yol haritamızda başka birçok güncelleştirme türü ve işletim sistemi testi var.

**S: Hizmetle ilişkili bir maliyet var mı?**

**A:** 1 Mart 2022'den itibaren, doğrulama gereksinimleriniz için aboneliğiniz kapsamında 6 ay içinde süresi dolan 100 ücretsiz saat (800 ABD doları olarak değer verilir) sağlanır. Ücretsiz saatler tüketildikten (veya kullanılmadan önce süresi dolduktan) sonra kullanımınıza göre saat başına 8 ABD doları ölçülür.

**S: Test Temeli hakkında nasıl geri bildirim sağlayabilirim?**

**A:** Test Tabanı hakkındaki geri bildiriminizi paylaşmak için portalın sol alt kısmındaki **Geri Bildirim** simgesini seçin. Microsoft'un geri bildiriminizi daha iyi anlamasına yardımcı olmak için gönderiminize bir ekran görüntüsü ekleyin.

Ayrıca adresinden ürün önerileri gönderebilir ve diğer fikirleri <testbasepreview@microsoft.com>oylayabilirsiniz.
