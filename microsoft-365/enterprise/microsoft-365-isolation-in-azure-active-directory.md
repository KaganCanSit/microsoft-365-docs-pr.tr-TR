---
title: Azure Active Directory'da yalıtım ve Access Control Microsoft 365
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Bu makalede, yalıtım ve Access Control Azure Active Directory içinde birden çok kiracının verilerini birbirinden yalıtılmış durumda tutmak için nasıl çalıştığını öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 409528847d04a55926138e49128f018b349da0a3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093887"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Azure Active Directory'da yalıtım ve Access Control Microsoft 365

Azure Active Directory (Azure AD), mantıksal veri yalıtımı aracılığıyla çok güvenli bir şekilde birden çok kiracıyı barındıracak şekilde tasarlanmıştır. Azure AD'ye erişim, bir yetkilendirme katmanı tarafından geçitli olarak sağlanır. Azure AD, bir müşterinin içeriğini korumak için kiracı kapsayıcılarını güvenlik sınırları olarak kullanan müşterileri yalıtır ve böylece içeriğe ortak kiracılar tarafından erişilemez veya güvenliği tehlikeye atılamaz. Azure AD'nin yetkilendirme katmanı tarafından üç denetim gerçekleştirilir:

- Sorumlu Azure AD kiracısına erişim için etkinleştirildi mi?
- Sorumlu bu kiracıdaki verilere erişim için etkinleştirildi mi?
- Sorumlunun bu kiracıdaki rolü istenen veri erişimi türü için yetkilendirildi mi?

Doğru kimlik doğrulaması ve belirteç veya sertifika olmadan hiçbir uygulama, kullanıcı, sunucu veya hizmet Azure AD'ye erişemez. İsteklere uygun kimlik bilgileri eşlik etmemesi durumunda reddedilir.

Etkili bir şekilde, Azure AD her kiracıyı kendi korumalı kapsayıcısında barındırır ve yalnızca kiracının sahip olduğu ve yönettiği kapsayıcının ilkeleri ve izinleri vardır.
 
![Azure kapsayıcısı.](../media/office-365-isolation-azure-container.png)

Kiracı kapsayıcıları kavramı, portallardan kalıcı depolamaya kadar tüm katmanlarda dizin hizmetine derinlemesine eklenmiştir. Aynı fiziksel diskte birden çok Azure AD kiracı meta verisi depolandığında bile, kapsayıcılar arasında dizin hizmeti tarafından tanımlanandan başka bir ilişki yoktur ve bu da kiracı yöneticisi tarafından dikte edilir. İlk olarak yetkilendirme katmanından geçmeden herhangi bir istekte bulunan uygulama veya hizmetten Azure AD depolamaya doğrudan bağlantı olamaz.

Aşağıdaki örnekte, Contoso ve Fabrikam'ın her ikisi de ayrı, ayrılmış kapsayıcılara sahiptir ve bu kapsayıcılar sunucular ve depolama gibi temel alınan altyapılardan bazılarını paylaşsa da, birbirinden ayrı ve yalıtılmış olarak kalırlar ve yetkilendirme ve erişim denetimi katmanlarıyla geçitleri vardır.
 
![Azure ayrılmış kapsayıcıları.](../media/office-365-isolation-azure-dedicated-containers.png)

Ayrıca, Azure AD'nin içinden yürütülebilecek uygulama bileşeni yoktur ve bir kiracının başka bir kiracının bütünlüğünü zorla ihlal etme, başka bir kiracının şifreleme anahtarlarına erişme veya sunucudan ham verileri okuması mümkün değildir.

Varsayılan olarak Azure AD, diğer kiracılardaki kimlikler tarafından yapılan tüm işlemlere izin vermemektedir. Her kiracı, talep tabanlı erişim denetimleri aracılığıyla Azure AD içinde mantıksal olarak yalıtılır. Dizin verilerinin okuma ve yazma işlemlerinin kapsamı kiracı kapsayıcıları olarak belirlenmiştir ve bir iç soyutlama katmanı ile birlikte kiracıyı güvenlik sınırı olarak zorlayan rol tabanlı erişim denetimi (RBAC) katmanı tarafından geçitlenir. Her dizin veri erişim isteği bu katmanlar tarafından işlenir ve Microsoft 365'deki her erişim isteği yukarıdaki mantık tarafından ele alınır.

Azure AD Kuzey Amerika, ABD Hükümeti, Avrupa Birliği, Almanya ve World Wide bölümlerine sahiptir. Bir kiracı tek bir bölümde bulunur ve bölümler birden çok kiracı içerebilir. Bölüm bilgileri kullanıcılardan soyutlanır. Belirli bir bölüm (içindeki tüm kiracılar dahil) birden çok veri merkezine çoğaltılır. Kiracının bölümü, kiracının özelliklerine (örneğin, ülke kodu) göre seçilir. Her bölümdeki gizli diziler ve diğer hassas bilgiler ayrılmış bir anahtarla şifrelenir. Anahtarlar, yeni bir bölüm oluşturulduğunda otomatik olarak oluşturulur.

Azure AD sistem işlevleri, her kullanıcı oturumu için benzersiz bir örnektir. Ayrıca Azure AD, bilgilerin yetkisiz ve istenmeyen aktarımını önlemek amacıyla paylaşılan sistem kaynaklarının ağ düzeyinde yalıtılmasını sağlamak için şifreleme teknolojilerini kullanır.
