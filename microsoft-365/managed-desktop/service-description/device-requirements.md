---
title: Cihaz gereksinimleri
description: Cihazların Microsoft Yönetilen Masaüstü ile çalışması için minimum donanım ve yazılım gereksinimlerinin özeti
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 5fb600434c8f6d7b62e7fd7408c3567a34c0eda0
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010782"
---
# <a name="device-requirements"></a>Cihaz gereksinimleri

Microsoft Yönetilen Masaüstü, cihaz gereksinimlerini düzenli olarak hizmete dahil edilecek şekilde değerlendirir. Bu makalede, Microsoft Yönetilen Masaüstü ile çalışmak için bir cihazın karşılaması gereken donanım ve yazılım gereksinimleri açıklanmıştır. Bu gereksinimlere göre hizmetle birlikte kullanmak üzere onaylanmış belirli cihazların listesini gözden geçirebilirsiniz. Mağaza veya iş cihazları sitesinde Microsoft [Yönetilen Windows Pro filtresi](https://www.microsoft.com/en-us/windows/business/devices)

> [!NOTE]
> Bu gereksinimler herhangi bir zamanda değişebilir, ancak donanım gereksinimi değişiklikleriyle ilgili 30 gün bildirim sağlaruz. En son değiştirilen gereksinimler ile işaretlenir <b>\*</b>. 

## <a name="check-hardware-requirements"></a>Donanım gereksinimlerini denetleme

Cihaz belirlemelerini gözden geçirmenin yanı sıra, indirilebilir hazırlık değerlendirme denetleyicisini kullanarak[](../get-ready/readiness-assessment-downloadable.md), verilen cihazın gerekli gereksinimleri karşı çalıştığını doğru edebilirsiniz. Bu araç ayrıca, hizmetin çalışması için gerekli olan ağ ayarlarını ve uç noktaları da denetler.

## <a name="minimum-requirements"></a>En düşük gereksinimler

Microsoft Yönetilen Masaüstü'ne kaydolmak için bir cihazın tüm bu gereksinimleri karşılaması veya aşması gerekir.

### <a name="manufacturer"></a>Üretici

Cihaz, şu üreticiler tarafından yapılmış olması gerekir:

- Dell
- HP
- Lenovo
- Microsoft

> [!NOTE] 
> Microsoft Yönetilen Masaüstü tarafından yönetilen cihazlar, 01 Mart 2022'den önce OEM tarafından destek olmalısınız. Portföyümüzdeki cihazların yaşam destek sonuna ne zaman ulaşacaklarını bulmak için OEM'niz ile birlikte çalışabilirsiniz. Yaşam destek sonu öncesinde cihazların değiştirilmesinden müşteriler sorumlu olur. OEM desteğinin dışından düşen cihazlar Microsoft Yönetilen Masaüstü tarafından yönetil olmaya devam edecektir, ancak bu cihazlar için destek, hizmetimiz tarafından risk altında tutulabilecek güvenlik ve performans sorunları riski ile sınırlı olabilir.
</b>

### <a name="installed-software"></a>Yüklü yazılım

Bu yazılımın önceden yüklenmiş olması gerekir:

- <b>\*</b>Windows 10 veya Windows 11: Enterprise, Pro ya da Pro İş Istasyonu sürümü
- Kurumlar için Microsoft 365 Uygulamaları'un 64 bit Kurumlar için Microsoft 365 Uygulamaları 
- Tüm geçerli cihaz sürücüleri


### <a name="physical-features"></a>Fiziksel özellikler

Cihazların şu özelliklere sahip olması gerekir:

- UEFI güvenli önyükleme için etkin 
- Güvenilir Platform Modülü 2.0 
- Sanallaştırma tabanlı güvenlik özelliğine sahip 
- [HYPERvisor korumalı CODE integrity](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) supported by the THE THE

Bu özellikler ve onlarla ilgili olan ve hizmetin kullandığı teknolojiler hakkında daha fazla bilgi için [bkz. Microsoft Yönetilen Masaüstü teknolojileri](../intro/technologies.md).

> [!NOTE]
>- ARM işlemciler desteklenmiyor.
>- <b>\*</b>Windows 11'in ek [donanım gereksinimleri vardır](/windows/whats-new/windows-11-requirements).

Cihazlar depolama ve bellek için aşağıdaki sınırları karşılamalı veya bunu aşmalı:

- Önyükleme sürücüsü sabit disk dışında bir tür olmalıdır. Örneğin, SSD, NVMe ve eMMC sürücülerinin hepsi geçerli seçeneklerdir.
- Önyükleme sürücüsü en az 128 GB kapasitesine sahip olmalıdır.
- İç cihaz belleğinin (RAM) 8 GB'a eşit veya fazla olması gerekir.

Cihaz 1 Temmuz 2020'den sonra yapıldı ise bu cihazda destek olmak için bir IR kamerası, parmak izi okuyucusu veya her [ikisi de Windows Hello](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security).

## <a name="recommended-features"></a>Önerilen özellikler

Şu özelliklere sahip cihazları seçerseniz kullanıcılarınız çok daha iyi bir deneyimden sonra sahip olur:

- Intel vPro platform işlemcisi veya AMD Ryzen Pro işlemci
- En az 256 GB kapasitesine sahip SSD türünün önyükleme sürücüsü
- En az 16 GB iç cihaz belleği (RAM)
- Modern Bekleme desteği
- Cihaz Güvenli çekirdek bilgisayar türündedir
- Kernel DMA Protection'i destekler
