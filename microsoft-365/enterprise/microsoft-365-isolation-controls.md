---
title: Microsoft 365 yalıtım denetimleri
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Yalıtma denetimlerinin şirket içinde nasıl Microsoft 365, hizmetlerin gerektiğinde bir arada çalışmasına veya değişmeden kalmasına olanak sağlar.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 514b12e44d9e81a18b691ebf3196a3d21157e71b
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959693"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 yalıtım denetimleri 

Microsoft, Microsoft 365'ın çok kiracılı mimarisinin kurumsal düzeyde güvenlik, gizlilik, gizlilik, bütünlük, yerel, uluslararası ve kullanılabilirlik standartlarını desteklediğini sürekli olarak [sağlamak için çalışır](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons). Microsoft'un sağladığı ölçek ve hizmetlerin kapsamı, önemli insan etkileşimleriyle bir Microsoft 365 yönetimi zorlaştırın ve ekonomik olmayan bir süreçtir. Microsoft 365 hizmetler, her biri insan dokunuşu veya müşteri içeriğine herhangi bir erişim gerektiren çok sayıda işlemle son derece otomatik hale getirildi ve birden çok global dağıtılmış veri merkezi aracılığıyla sağlanır. Personelimiz otomatik araçları kullanarak bu hizmetleri ve veri merkezlerini destekler ve yüksek güvenli uzaktan erişim sağlar. 

Microsoft 365, önemli iş işlevleri sağlayan ve tüm işletme deneyimine katkıda bulunan birçok Microsoft 365 oluşur. Bu hizmetlerin her biri kendi içindedir ve bir diğerleriyle tümleştirilen şekilde tasarlanmıştır.

Microsoft 365 aşağıdaki ilkelerle tasarlanmıştır:

 - **[Hizmet Odaklı Mimari](/previous-versions/aa480021(v=msdn.10)):** İyi tanımlanmış iş işlevselliği sağlayan, birlikte çalışabilir hizmetler şeklinde yazılım tasarlama ve geliştirme.
 - **[operasyon güvenliği güvencesi](https://www.microsoft.com/download/details.aspx?id=40872):** [Microsoft Güvenlik](https://www.microsoft.com/sdl/default.aspx) Geliştirme Yaşam Döngüsü, Microsoft Güvenlik Yanıt Merkezi ve siber güvenlik tehdit ortamı hakkında derinlemesine farkındalık dahil olmak üzere Microsoft'a özgü çeşitli [](https://technet.microsoft.com/library/dn440717.aspx)özellikler aracılığıyla kazanılan bilgileri bir çerçevedir.

Microsoft 365 bir arada çalışan hizmetlerdir, ancak birbirinden bağımsız olarak, hizmet olarak dağıtılabilir ve çalıştırılabilir şekilde tasarlanmıştır ve uygulanırlar. Microsoft, kuruluş varlıklarının yetkisiz veya yetkisiz değişiklik yapma ya da kötüye kullanılma fırsatlarını azaltmak için Microsoft 365 görevleri ve sorumluluk alanlarını azaltır. Microsoft 365 ekipler, rol tabanlı kapsamlı bir erişim denetim mekanizmasının parçası olarak rolleri tanımlamaktadır.

## <a name="customer-content-isolation"></a>Müşteri içerik yalıtımı

Kiracıda yer alan tüm müşteri içeriği diğer kiracılardan ve kiracıların yönetiminde kullanılan işlem ve sistem verilerinden Microsoft 365. Her hizmette veya uygulamada güvenlik Microsoft 365 en aza indirmek için çeşitli koruma Microsoft 365 uygulanır. Birden çok koruma formu kiracıların veya kiracı sisteminin kendisine yetkisiz Microsoft 365 engelleme.

Microsoft'un Kiracılar'da kiracı verileri için mantıksal yalıtma uygulama hakkında bilgi Microsoft 365 bkz. [Microsoft 365.](microsoft-365-tenant-isolation-overview.md)