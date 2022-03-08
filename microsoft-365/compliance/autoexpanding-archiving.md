---
title: Otomatik genişleyen arşivleme hakkında bilgi
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 37cdbb02-a24a-4093-8bdb-2a7f0b3a19ee
description: Posta kutularına ek arşiv depolama sağlayan otomatik genişleyen arşivleme Exchange Online öğrenin.
ms.openlocfilehash: 1b4b8d81868cc97fc8e8faf5b0dc449e4c07a868
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328869"
---
# <a name="learn-about-auto-expanding-archiving"></a>Otomatik genişleyen arşivleme hakkında bilgi

Daha Office 365 posta kutuları, kullanıcılara ek posta kutusu depolama alanı sağlar. Kullanıcının arşiv posta kutusu etkinleştirildikten sonra, 100 GB'a kadar ek depolama alanı kullanılabilir. Geçmişte, 100 GB depolama alanı kotasına ulaşıldı ancak kuruluşlar bir arşiv posta kutusu için ek depolama alanı isteğinde bulundu. Artık durum böyle değildir.

Bu arşivleme özelliği (Microsoft 365 genişletme olarak da *adlandırılan) arşiv* posta kutularında 1,5 TB'a kadar ek depolama alanı sağlar. Arşiv posta kutusunda depolama kotasına ulaşılırsa, Microsoft 365 posta kutusu 1,5 TB'a ulaşana kadar arşiv boyutunu otomatik olarak artırır (ve artımlı olarak).

Otomatik genişleyen arşivlemeyi açmayla ilgili adım adım yönergeler için bkz. [Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).

> [!NOTE]
> Otomatik genişleyen arşivleme, paylaşılan posta kutularını da destekler. Paylaşılan bir posta kutusunun arşivini etkinleştirmek için bir Exchange Online Plan 2 lisansı veya Exchange Online lisansı olan bir Exchange Online Arşivleme Lisansı gereklidir.

## <a name="how-auto-expanding-archiving-works"></a>Otomatik genişleyen arşivleme nasıl çalışır?

Daha önce de açıklanması gibi, kullanıcının arşiv posta kutusu etkinleştirildiğinde ek posta kutusu depolama alanı oluşturulur. Otomatik genişleyen arşivleme etkinleştirildiğinde, arşiv Microsoft 365 kutusunun boyutunu düzenli aralıklarla denetler. Bir arşiv posta kutusu depolama sınırına yaklaşsa, arşiv Microsoft 365 otomatik olarak ek depolama alanı oluşturur. Kullanıcının bu ek depolama alanı biterse, Microsoft 365 arşive daha fazla depolama alanı ekler. Kullanıcının arşivi 1,5 TB boyuta ulaşana kadar bu işlem devam eder. Bu işlem otomatik olarak yapılır ve bu da yöneticilerin ek arşiv depolaması talep etmek veya otomatik genişleyen arşivlemeyi yönetmek zorunda olmadığınız anlamına gelir.

Burada, bu işleme hızlı bir genel bakış ve hızla göz atacağız.

![Otomatik genişleyen arşivleme sürecine genel bakış.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. Arşivleme, kullanıcı posta kutusu veya paylaşılan posta kutusu için etkinleştirilir. 100 GB depolama alanı olan bir arşiv posta kutusu oluşturulur ve arşiv posta kutusunun uyarı kotası 90 GB olarak ayarlanır.

2. Yönetici, posta kutusu için otomatik genişleyen arşivlemeyi sağlar. Arşiv posta kutusu (Kurtarılabilir Öğeler klasörü de içinde olmak üzere) 90 GB'a ulaştığında otomatik genişleyen bir arşive dönüştürülür ve Microsoft 365 1,5 TB boyuta ulaşana kadar arşive depolama alanı ekler. Ek depolama alanı sağlanması 30 gün kadar zaman alır.

   > [!NOTE]
   > Posta kutusu bekletme ilkesine yerleştirilirse veya bir bekletme ilkesine atanmışsa, otomatik genişleyen arşivleme etkinleştirildiğinde arşiv posta kutusunun depolama kotası 110 GB'a artırıldı. Benzer şekilde, arşiv uyarısı kotası da 100 GB'a artırıldı.

3. Microsoft 365 gerektiğinde otomatik olarak daha fazla depolama alanı ekler.

> [!IMPORTANT]
> Otomatik genişleyen arşivleme, günde 1 GB'i aşmaan büyüme hızına sahip tek tek kullanıcılar (veya paylaşılan posta kutuları) için yalnızca kullanılan posta kutuları için destekler. Kullanıcının arşiv posta kutusu yalnızca o kullanıcıya yöneliktir. Bir arşiv posta kutusuna ileti kopyalamak için günlük kayıt, aktarım kuralları veya otomatik iletme kuralları kullanımına izin verilmez. Microsoft, kullanıcının arşiv posta kutusunun diğer kullanıcıların arşiv verilerini depolamak için kullandığı veya uygun olmayan kullanım durumlarında kullandığı durumlarda ek arşivlemeyi reddetme hakkını rezerve ediyor.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Ek arşiv depolama alanına neler taşınır?

Otomatik genişleyen arşiv depolama alanını verimli bir şekilde kullanmak için, klasörler taşınabilirsiniz. Microsoft 365, arşive ek depolama alanı ek olduğunda hangi klasörlerin taşın posta ile taşındığını belirler. Bazen bir klasör taşındığında, bir veya birden çok alt klasör otomatik olarak oluşturulur ve taşıma işlemini kolaylaştırmak için özgün klasördeki öğeler bu klasörlere dağıtılır. Dosya listesinde klasör listesinin arşiv bölümü görüntülenirken Outlook alt klasörler özgün klasörün altında görüntülenir. Bu alt klasörleri adlandırmak Microsoft 365 **\<folder name\>adlandırma kuralı şu şekildedir _yyyy (aaaa, yyyy h_mm)**, burada:

- **yyyy** , klasördeki iletilerin alın aldığı yıldır.

- **aaa aaa, yyyy h_m**, alt klasörün Office 365 tarafından UTC biçiminde, kullanıcının saat dilimine ve Outlook'te bölgesel ayarlarına göre oluşturulmuş tarih ve saattir.

Aşağıdaki ekran görüntüleri, iletilerin otomatik olarak genişletilmiş arşive taşınmadan önce ve kaldırıldıktan sonra klasör listesini gösterir.

 **Ek depolama alanı eklenmeden önce**

![Arşiv hazırlamadan önce arşiv posta kutusunun klasör listesi.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Ek depolama alanı eklendikten sonra**

![Arşiv otomatik genişledikten sonra arşiv posta kutusunun klasör listesi.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Daha önce açıklandığı gibi, Microsoft 365 arşive dağıtan içeriği arşive dağıtmaya yardımcı olmak için öğeleri alt klasörlere taşır (ve bunları yukarıda açıklanan adlandırma kuralını kullanarak adlandırarak adlandırabilirsiniz). Ancak, öğeleri alt klasörlere taşıma durumu her zaman böyle değildir. Bazen bir klasörün tamamı arşivlenen bir arşive taşınabiliyor. Bu durumda, klasörün özgün adı korunur.  Bu klasör, arşiv arşivinde Outlook arşive taşındığında görünür değildir.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Outlook genişletilmiş bir arşivdeki öğelere erişmek için bazı önemli gereksinimler

Otomatik genişletilmiş bir arşivde depolanan iletilere erişmek için, kullanıcıların aşağıdaki müşterilerden birini Outlook gerekir:

- Outlook 2016 için Outlook 2019'Windows

- Web üzerinde Outlook

- mac Outlook 2016 2019 Outlook veya Outlook 2019

Otomatik genişletilmiş bir arşivde depolanan iletilere Outlook veya Web üzerinde Outlook kullanırken göz önünde bulundurabilirsiniz.

- Arşiv posta kutunuzda, otomatik genişletilmiş depolama alanına taşınanlar da dahil olmak üzere herhangi bir klasöre erişebilirsiniz.

- Bir arşiv posta kutusunda en az bir otomatik genişletilmiş depolama alanı varsa, arşiv posta kutusundan veya arşiv arşivinden klasör silemezsiniz. Başka bir deyişle, otomatik genişletilmiş depolama alanı sağlandıktan sonra arşivdeki hiçbir klasörü silemezsiniz.

- Otomatik olarak genişletilmiş depolama alanında öğeleri silebilirsiniz. Bununla birlikte, posta kutusunda otomatik genişleyen arşivleme etkinleştirildikten sonra bir öğeyi kurtarmak için Silinmiş Öğeleri Kurtar özelliğini kullanaabilirsiniz.

- Otomatik genişletilmiş arşivleme için arama web'Outlook (OWA) kullanılabilir. Çevrimiçi Arşiv'e benzer şekilde, ek depolama alanına taşınmış öğeleri arayabilirsiniz. OWA'da arama kapsamı olarak arşiv seçildiğinde, tüm arşivlerde (otomatik genişletilmiş arşivler de içinde) ve buna karşılık gelen alt klasörlerde arama yapılacaktır. Yalnızca bulut arşiv örneğinde (birincil posta kutusu hala şirket içinde) otomatik genişletilmiş arşiv özelliği için aramanın desteklene olmadığını unutmayın.

- Otomatik olarak genişletilmiş arşiv araması Aylık Outlook Kanalında Outlook için Windows'de Enterprise sunulmaktadır. Bu güncelleştirmeyle Geçerli Posta Kutusu kapsamı kullanılabilir, böylelikle otomatik olarak genişletilmiş arşivde aramanızı sağlar. Yalnızca bulut arşiv örneğinde (birincil posta kutusu hala şirket içinde) otomatik genişletilmiş arşiv özelliği için aramanın desteklene olmadığını unutmayın. Bu özellik ve diğer destek Microsoft Arama daha fazla bilgi için bkz. Outlook Windows hangi [Exchange Online kullanır Microsoft Arama](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045). 

- Otomatik genişletilmiş bir arşiv Outlook öğe sayıları (Outlook ve Web üzerinde Outlook' içinde) ve Okundu/Okunmadı sayıları doğru olmayabilir.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Otomatik genişleyen arşivleme ve diğer uyumluluk özellikleri

Bu bölümde, otomatik genişleyen arşivleme ile diğer uyumluluk ve veri idaresi özellikleri arasındaki işlevler açık bir şekilde açık almaktadır.

- **eBulma:** İçerik Arama veya eBulma Hizmeti gibi bir eBulma aracı In-Place, otomatik genişletilmiş bir arşivde ek depolama alanlarında da arama yapılacaktır.

- **Bekletme:** Güvenlik ve uyumluluk merkezinde Exchange Online'te Mahkeme Nedeniyle Tutma veya eBulma olay bekletme ve bekletme ilkeleri gibi araçları kullanarak posta kutusunu bekletmeye devam etmek için, otomatik genişletilmiş bir arşivde yer alan içerik de saklama durumunda olur.

- **Mesajlaşma kayıtları yönetimi (MRM):** Posta kutusu öğelerinin kullanımdan Exchange Online için MRM silme ilkelerini kullanırsanız, otomatik genişletilmiş arşivde yer alan süresi dolmuş öğeler de silinir.

- **İçeri aktarma hizmeti:** PST dosyalarını kullanıcının Office 365 arşive içeri aktarma işlemi için İçeri Aktarma Hizmeti'ne kullanabilirsiniz. PST dosyalarından kullanıcının arşiv posta kutusuna 100 GB'a kadar veri aktarabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Otomatik genişleyen arşivleme hakkında daha teknik ayrıntılar için bkz. Microsoft 365 [Genişletme Arşivleri Hakkında SSS](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).

Otomatik genişleyen arşivlemeyi etkinleştirmeye hazırsanız, bkz. [Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).
