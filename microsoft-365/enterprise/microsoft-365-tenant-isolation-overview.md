---
title: Microsoft 365'te Kiracı Microsoft 365
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
description: Bu makalede, Microsoft'un kiracı ayırma gibi bulut hizmetlerde kiracı yalıtımnı nasıl zorunlu Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b52d936bb00ac0adef0baf428cbc5f9a8f8aba49
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959692"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Microsoft 365'te Kiracı Microsoft 365

Bulut bilgi işlem'in başlıca avantajlarından biri, aynı anda birçok müşteri genelinde ortak, ölçek ölçeklerine yol açan, paylaşılan ve ortak bir altyapı kavramıdır. Bu kavram, çok *kiralı olarak adlandırılan bir kavramdır*. Microsoft, bulut hizmetlerimizle ilgili çok kiracılı mimarilerin kurumsal düzeyde güvenlik, gizlilik, gizlilik, bütünlük ve kullanılabilirlik standartlarını desteklemesi için sürekli olarak çalışıyor.

[Güvenilir](https://www.microsoft.com/trust-center) Bilgi işlemden toplanmış önemli yatırımlara ve deneyime ve Güvenlik Geliştirme Yaşam Döngüsü'ne bağlı [olarak, Microsoft](https://www.microsoft.com/securityengineering/sdl/) bulut hizmetleri tüm kiracıların diğer tüm kiracılara açık olduğu varsayımı ile tasarlanmıştır ve bir kiracının başka bir kiracının güvenliğini veya hizmetini etkilemesini önlemeye yönelik güvenlik önlemleri uygulamaya başladık.  veya başka bir kiracının içeriğine erişmeyi sağlar.

Çok kiracılı bir ortamda kiracı yalıtımnı korumanın başlıca iki hedefi:

1.    Kiracılar genelinde müşteri içeriğinin sızıntısını veya yetkisiz erişimi engelleme; ve
2.    Bir kiracının eylemlerinin, başka bir kiracının hizmetini olumsuz etkilemesini önleme

Microsoft 365 genelinde, müşterilerin Microsoft 365 hizmetlerinden veya uygulamalarından ödün vermesini ya da diğer kiracıların veya Microsoft 365 sisteminin kendi bilgilerine yetkisiz erişim kazanmasını önlemek için çeşitli koruma formları uygulanmıştır:

- Müşteri hizmetleri için her kiracıda müşteri içeriğinin mantıksal Microsoft 365, Azure Active Directory ve rol tabanlı erişim denetimi aracılığıyla elde edilir.
- SharePoint Online, depolama düzeyinde veri yalıtım mekanizmaları sağlar.
- Microsoft, müşteri içeriğinin gizliliğini ve bütünlüğünü korumak için sıkı fiziksel güvenlik, arka plan tarama ve çok katmanlı bir şifreleme stratejisi kullanır. Tüm Microsoft 365, fiziksel erişim kazanmak için palmiye baskıları gerektiren biyometrik erişim denetimlerine sahiptir. Buna ek olarak, TÜM ABD tabanlı Microsoft çalışanlarının, işe alma sürecinin bir parçası olarak standart arka plan denetimlerini başarıyla tamamlaması gerekir. 2013'te yönetim erişimi için kullanılan denetimler hakkında daha fazla Microsoft 365 için bkz[. Microsoft 365 Denetimler](/compliance/assurance/assurance-administrative-access-controls-overview).
- Microsoft 365, BitLocker, dosya başına şifreleme, Aktarım Katmanı Güvenliği (TLS) ve İnternet Protokolü Güvenliği (IHat) dahil olmak üzere, beklemede ve aktarım sırasında müşteri içeriğini şifreleen hizmet tarafı teknolojileri kullanır. E-Microsoft 365'de şifreleme hakkında ayrıntılı bilgi için [bkz. Microsoft 365](../compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).

Birlikte, yukarıda listelenen korumalar, tek başına fiziksel yalıtarak sağlanan korumanın tehdit koruması ve risk azaltma eşdeğeri sağlayan güçlü mantıksal yalıtım denetimleri sağlar.

## <a name="related-links"></a>İlgili Bağlantılar

- [Azure Active Directory'de Yalıtım ve Erişim Denetimi](microsoft-365-isolation-in-azure-active-directory.md)
- [Office Graph ve Delve](microsoft-365-isolation-in-graph-and-delve.md)
- [Aramada Kiracı Microsoft 365 Ayırma](microsoft-365-isolation-in-microsoft-365-search.md)
- [Kaynak Sınırları](/compliance/assurance/assurance-resource-limits)
- [Kiracı Sınırlarını İzleme ve Sınama](/compliance/assurance/assurance-monitoring-and-testing)
- [Microsoft 365'de Yalıtım ve Erişim Denetimi](microsoft-365-isolation-in-microsoft-365.md)