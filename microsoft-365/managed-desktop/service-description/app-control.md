---
title: Uygulama denetimi
description: Uygulama denetimi ve güven uygulamaları nasıl kullanılır
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 108c4d3d64f503d2221aed9df9724faee85b2998
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015308"
---
# <a name="app-control"></a>Uygulama denetimi

Uygulama denetimi, Microsoft Yönetilen Masaüstü'de istemci cihazlarında kodun yürütülmesini kısıtlayan isteğe bağlı bir güvenlik uygulamasıdır.

Bu denetim kötü amaçlı yazılım veya kötü amaçlı betik riskini azalttı. Denetim için yalnızca müşteri tarafından onaylanan yayıncılar listesi tarafından imzalanan kodların çalıştırılması gerekir. Bu denetimin birçok güvenlik avantajları vardır, ancak öncelikli olarak verileri ve kimliği istemci tabanlı açıklardan korumayı hedefler.

Microsoft Yönetilen Masaüstü, temel üretkenlik senaryolarına olanak sağlayan bir temel ilke oluşturarak uygulama denetim ilkelerinin yönetimini basitleştiriyor. Ortamınıza özel olan diğer imzacılara ve betiklere güveni genişletebilirsiniz.

Herhangi bir güvenlik teknolojisi kullanıcı deneyimi, güvenlik ve maliyet arasında bir denge gerektirir. Uygulama denetimi ortamınız içinde kötü amaçlı yazılımların tehdidini azaltır, ancak bunun kullanıcı için sonuçları ve IT yöneticinizin başka eylemleri vardır.

| Ek güvenlik ve sorumluluklar | Açıklama |
| ------ | ------ |
| Ek güvenlik | Uygulama denetimi ilkesi tarafından güvenilmiyor olan uygulamaların veya betiklerin cihazlarda çalıştırılası engellenir. |
| Ek sorumluluklarınız | <ul><li>Uygulama denetim ilkesi tarafından engellenmiş olup olmayacaklarını belirlemek için uygulamalarınızı test etmek sizin sorumluluğundadır.</li><li>Bir uygulama engellenmişse (veya engellenmişse), gerekli imzacı ayrıntılarını belirlemek sizin sorumluluğunuzdur. Yönetici portalı aracılığıyla bir değişiklik isteğide bulundurabilirsiniz.</li></ul>
| Microsoft Yönetilen Masaüstü sorumlulukları | <ul><li>Microsoft Managed Desktop; Microsoft 365 Uygulamaları, Windows, Teams, OneDrive gibi temel Microsoft ürünlerini sağlayan temel ilkeyi koruma sağlar.</li><li>Microsoft Yönetilen Masaüstü güvenilir imzalarınızı ekler ve güncelleştirilmiş ilkeyi cihazlarınıza dağıtır.</li></ul>

## <a name="managing-trust-in-applications"></a>Uygulamalarda güveni yönetme

Microsoft Yönetilen Masaüstü, Microsoft teknolojilerinin temel bileşenlerine güvenen bir temel ilkeyi temel alıyor. Daha sonra *Microsoft Yönetilen* Masaüstü'ne, zaten hangi uygulamalara ve betiklere güveniyoruz konusunda bilgi edinerek kendi uygulamalarınızı ve betiklerinizi güvene eklersiniz.

### <a name="base-policy"></a>Temel ilke

Microsoft Siber güvenlik uzmanlarıyla işbirliği içinde Microsoft Yönetilen Masaüstü, standart bir ilke oluşturur ve sürdürür. Bu standart ilke:

- Office 365 aracılığıyla dağıtılan uygulamaların çoğunu Microsoft Intune.
- Güvenilmeyen dosyaların kod derlemesi veya yürütülmesi gibi tehlikeli etkinlikleri engeller.

Temel ilke, yazılım yürütmeyi kısıtlamak için aşağıdaki yaklaşımı benimser:

- Yöneticilerin çalıştıracakları dosyaların çalışmasına izin verilir.
- Kullanıcı tarafından yazılabilir *dizinlerde* yer alan konumlarda yer alan dosyaların çalıştırılabilir.
- Dosyalar güvenilir imzalayan [tarafından imzalanmıştır](#signer-requests).
- Microsoft tarafından imzalanan dosyaların çoğu çalıştırabilirsiniz, ancak bazıları kod derleme gibi yüksek riskli işlemleri önlemek için engellenir.

Kullanıcı yönetici dışında bir cihaza uygulama veya betik ekleye eklene ise (yani, kullanıcı yazılabilir bir dizinde yer asa), yürütülmesine izin vermez. Uygulamaya veya betike yönetici tarafından önceden izin verildi ise yürütmeye izin verilir.

Bizim ilkemiz, aşağıdaki senaryolarda uygulamaların yürütülmesini durduracak:

- Bir kullanıcı kötü amaçlı yazılım yüklemek için kandırmaya çalışıyorsa.
- Bir uygulamada bir güvenlik açığı olması kullanıcı, kötü amaçlı yazılım yüklemek için çalışır.
- Kullanıcı bilerek yetkisiz bir uygulamayı veya betiği çalıştırmayı deniyorsa.

### <a name="signer-requests"></a>İmzacı istekleri

Bir imzacı isteği dosyalamanız şartıyla hangi yazılım yayıncıları tarafından güveniniz olduğunu *bize bildirebilirsiniz*. Bunu yaparak şunları yapıyoruz:

- Bu güven bilgilerini temel uygulama denetim ilkesine ekleyin.
- Bu yayımcının sertifikasıyla imzalanan tüm yazılımların cihazlarınız üzerinde çalışmasına izin ver.

## <a name="audit-and-enforced-policies"></a>Denetim ve Zorunlu İlkeler

Microsoft Yönetilen Masaüstü, Microsoft Intune denetimi sağlamak için aşağıdaki ilkeleri kullanır:

### <a name="audit-policy"></a>Denetim ilkesi

Bu ilke, bir uygulamanın veya betiğin Zorunlu ilke tarafından engellenmiş olup olmadığını kaydetmek için günlükler oluşturur.

Denetim ilkeleri uygulama denetim kurallarını zorunlu kabul etmez. Bu amaçlar, bir uygulamanın yayımcıyı muaf tutulacak şekilde belirleyip gerektirmeyeceklerini test etme amaçlıdır. Belirtilen uygulamaların veya betiğin yürütülmesini veya yüklenmesi engellemek yerine, Olay Görüntüleyicisi'nde uyarıları (8003 veya 8006 olay) günlüğe kaydeder.

### <a name="enforced-policy"></a>Zorunlu ilke

Bu ilke güvenilmeyen uygulamaların ve betiklerin çalışmalarını engeller ve bir uygulama veya betik engel olduğunda günlükler oluşturur. Zorunlu ilkeler, standart kullanıcıların kullanıcı yazılabilir dizinlerde depolanan uygulamaları veya betikleri yürütmesini engellemektedir.

Test grubunda yer alan cihazların, herhangi bir uygulamanın soruna neden olup olmadığını doğrulamak için bir Denetim ilkesi uygulanmıştır. Diğer tüm gruplar (İlk, Hızlı ve Geniş) Zorunlu bir ilke kullanır. Bu gruplarda yer alan kullanıcılar güvenilmeyen uygulamaları veya betikleri çalıştırabilecektir.
