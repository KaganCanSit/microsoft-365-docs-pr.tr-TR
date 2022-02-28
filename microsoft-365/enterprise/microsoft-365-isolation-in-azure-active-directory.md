---
title: Microsoft 365'de Yalıtma ve Erişim Denetimi Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
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
description: Bu makalede, Yalıtılmış ve Erişim Denetimi'nin, birden çok kiracının verilerini ayrı bir kiracıdan ayrı tutmak için nasıl Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 11c2c488f0168815a1485f5833c5520259db0fa5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984488"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Microsoft 365'de Yalıtma ve Erişim Denetimi Azure Active Directory

Azure Active Directory (Azure AD) birden çok kiracıyı mantıksal veri yalıtım aracılığıyla yüksek güvenli bir şekilde barındırmak üzere tasarlanmıştır. Azure AD'ye erişim bir yetkilendirme katmanı tarafından kapılandı. Azure AD, müşterinin içeriğini korumak için kiracı kapsayıcılarını kullanarak müşterileri yalıtır ve böylece içeriklere ortak kiracılar tarafından erişilemez veya güvenliği aşamaz. Üç denetim Azure AD'nin yetkilendirme katmanı tarafından gerçekleştirilir:

- Anapara Azure AD kiracısına erişim için etkinleştirildi mi?
- Bu kiracıda verilere erişim için anapara etkin mi?
- Bu kiracıda anaparanın rolü, istenen veri erişimi türü için yetkili mi?

Hiçbir uygulama, kullanıcı, sunucu veya hizmet, doğru kimlik doğrulaması ve belirteç veya sertifika olmadan Azure AD'ye erişebilir. düzgün kimlik bilgileriyle birlikte olmazsa, istekler reddedilir.

Etkili bir şekilde, Azure AD kiracının yalnızca sahibi olduğu ve kiracı tarafından yönetilen kapsayıcı içinde ilkeler ve izinler bulunan, her kiracıyı kendi korumalı kapsayıcısı içinde barındırır.
 
![Azure kapsayıcısı.](../media/office-365-isolation-azure-container.png)

Kiracı kapsayıcıları kavramı, portallardan kalıcı depolamaya kadar tüm katmanlarda dizin hizmetine derinlemesine uygulanır. Aynı fiziksel diskte birden çok Azure AD kiracı meta verisi depolansa bile, dizin hizmeti tarafından tanımlanandan başka kapsayıcılar arasında ilişki yoktur ve bu da kiracı yöneticisi tarafından dikte edilir. Yetkilendirme katmanına girmeden, herhangi bir talepte olan uygulama veya hizmetten Azure AD depolama alanına doğrudan bağlantı silerek bu bağlantı mümkün olmaz.

Aşağıdaki örnekte, Contoso ve Fabrikam ayrı, ayrılmış kapsayıcılara sahip ve bu kapsayıcılar aynı temel altyapının (sunucular ve depolama gibi) bazılarını paylaşsa da, bunlar birbirinden ayrı kalır ve birbirinden ayrı kalır ve yetkilendirme ve erişim denetimi katmanlarıyla kapılanmış durumda kalır.
 
![Azure'a özel kapsayıcılar.](../media/office-365-isolation-azure-dedicated-containers.png)

Buna ek olarak, Azure AD'den yürütülebilir uygulama bileşenleri yoktur ve bir kiracının başka bir kiracının bütünlüğünü ihlal etmek, başka bir kiracının şifreleme anahtarlarına erişmek veya sunucudan ham verileri okuması mümkün değildir.

Varsayılan olarak, Azure AD diğer kiracılarda kimlikler tarafından verilen tüm işlemlere izinlanmaz. Her kiracı, talep tabanlı erişim denetimleri aracılığıyla Azure AD'de mantıksal olarak yalıtılmış olur. Dizin verilerini okuma ve yazma, kiracı kapsayıcılarının kapsamındadır ve birlikte güvenlik sınırı olarak kiracıyı zorunlu alan bir iç özet katmanı ve rol tabanlı erişim denetimi (RBAC) katmanıyla kaplanır. Her dizin veri erişim isteği bu katmanlar tarafından işlenir ve Microsoft 365 istekleri yukarıdaki mantıkla uygulanır.

Azure AD'de Kuzey Amerika, ABD Kamu, Avrupa Birliği, Almanya ve World Wide bölümleri vardır. Kiracı tek bir bölümde yer almaktadır ve bölümler birden çok kiracı içerebilir. Bölüm bilgileri kullanıcılardan uzak bir özetdir. Verilen bölüm (içindeki tüm kiracılar dahil) birden çok veri merkezlerine çoğaltılır. Kiracının bölümü, kiracının özelliklerine (örneğin, ülke koduna) göre seçilir. Her bölümdeki sırlar ve diğer hassas bilgiler, özel bir anahtarla şifrelenir. Yeni bir bölüm oluşturulduğunda anahtarlar otomatik olarak oluşturulur.

Azure AD sistem işlevleri, her kullanıcı oturumu için benzersiz bir örnektir. Buna ek olarak, Azure AD, yetkisiz ve yetkisiz bilgi aktarımını önlemek üzere ağ düzeyinde paylaşılan sistem kaynaklarının yalıtımsını sağlamak için şifreleme teknolojileri kullanır.
