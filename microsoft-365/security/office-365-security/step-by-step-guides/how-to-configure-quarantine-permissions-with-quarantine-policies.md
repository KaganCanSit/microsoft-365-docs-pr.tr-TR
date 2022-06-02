---
title: Karantina izinlerini ve ilkelerini yapılandırma
description: AdminOnlyPolicy, sınırlı erişim, tam erişim ve güvenlik yöneticilerine ve kullanıcılara hatalı pozitif klasörleri yönetmek için basit bir yol sağlama gibi farklı gruplar arasında karantina ilkeleri ve izinleri yapılandırma adımları.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: d2a3de0af3e824fcc8276bd339469253d1e3588c
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842478"
---
# <a name="how-to-configure-quarantine-permissions-and-policies"></a>Karantina izinlerini ve ilkelerini yapılandırma

Karma çalışmanın evrimi ile daha agresif bir güvenlik duruşu talebi arttıkça, güvenlik yöneticilerine ve kullanıcılara hatalı pozitif klasörleri yönetmek için çok basit bir yol sağlamak çok önemlidir. Yöneticiler ve kullanıcılar, açıklayıcı bir yaklaşım benimsedi ve bunu aşağıdaki yönergelerle gerçekleştirebilir.

> [!TIP]
> Karantina izinlerini ve ilkelerini ayarlamaya çalışan yöneticileri hedefleyen kısa bir video için [bu bağlantıya bakın](https://www.youtube.com/watch?v=vnar4HowfpY). Son kullanıcıysanız işleme bu [1 dakikalık genel bakışı](https://www.youtube.com/watch?v=s-vozLO43rI) tercih edin.

## <a name="what-you-will-need"></a>İhtiyacınız olan şey
- Yeterli izinler (Güvenlik Yöneticisi rolü)
- Aşağıdaki adımları gerçekleştirmek için 5 dakika.

## <a name="creating-custom-quarantine-policies-with-request-release-flow"></a>İstek yayın akışı ile Özel karantina ilkeleri oluşturma

Özel ilkelerimiz, kullanıcıların ***False positive** _ klasöründe hangi öğeleri önceliklendirmek için kullanabileceklerine karar verme olanağı sağlar ve kullanıcının bu öğelerin _release* klasörden istemesine olanak tanır.

1. Kullanıcınızın önceliklendirmesini değil önceliklendirmesini istediğiniz öğelerin hangi karar kategorilerine (toplu, istenmeyen posta, kimlik avı, yüksek güvenilirlikli kimlik avı veya kötü amaçlı yazılım) karar verin.
1. Kullanıcıların önceliklendirmesini istemediğiniz kategoriler için, öğeleri **AdminOnlyPolicy'ye** atayın. Kullanıcıların sınırlı erişimle önceliklendirmesini istediğiniz kategoriye gelince, istek yayın erişimiyle *özel bir ilke oluşturabilir* ve kullanıcıları bu kategoriye atayabilirsiniz.
1. **AdminOnlyPolicy'ye** kötü amaçlı yazılım ve yüksek güvenilirlikli kimlik avı öğelerinin atanacağı, düzenli güvenilirlik kimlik avı öğelerine *istek yayınıyla sınırlı erişim* atanacağı, toplu ve istenmeyen postaların ise kullanıcılar için tam erişim olarak bırakılabilmesi **kesinlikle önerilir**.

> [!IMPORTANT]
> Ayrıntılı özel ilkelerin nasıl oluşturulabileceği hakkında daha fazla bilgi için bkz[. Karantina ilkeleri - Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md).

## <a name="assigning-quarantine-polices-and-enabling-notification-with-organization-branding"></a>Karantina ilkeleri atama ve kuruluş markasıyla bildirimi etkinleştirme

Kullanıcıların önceliklendirebileceği veya önceliklendirmeyebileceği öğe kategorilerine karar verildikten ve karşılık gelen karantina ilkeleri oluşturulduktan sonra, yöneticilerin bu ilkeleri ilgili kullanıcılara ataması ve bildirimleri etkinleştirmesi gerekir.

1. *Tam erişim* kategorisine dahil etmek istediğiniz kullanıcıları, grupları veya etki alanlarını ve *sınırlı erişim* kategorisini ve *Yalnızca Yönetici* kategorisini belirleyin.
1. [Microsoft Güvenlik portalında](https://security.microsoft.com) oturum açın.
1. **E-posta & işbirliği** > **İlkeleri & kurallarını** seçin.
1. **Tehdit ilkeleri'ne tıklayın**.
1. Aşağıdakilerden her birini seçin: **İstenmeyen posta önleme ilkeleri**, **Kimlik avı önleme ilkesi**, **Kötü Amaçlı Yazılımdan Koruma ilkesi**.
1. **İlke oluştur'u** ve **ardından Gelen'i** seçin.
1. İlkenin uygulanacağı ilke Adı, kullanıcılar, gruplar veya etki alanları ve **İleri'yi** ekleyin.
1. **Eylemler** sekmesinde kategoriler için **İletiyi karantinaya al'ı** seçin. *Karantina ilkesini seçme* için ek bir panel olduğunu fark edeceksiniz. Daha önce oluşturduğunuz karantina ilkesini seçmek için bu açılan listeyi kullanın.
1. **Gözden Geçir** bölümüne gidin ve **onayla** düğmesine tıklayarak yeni ilkeyi oluşturun.
1. Diğer ilkeler için de aynı adımları yineleyin: **Kimlik avı önleme ilkesi**, **Kötü Amaçlı Yazılımdan Koruma ilkesi** ve **ek ilkesi Kasa**.

> [!TIP]
> Şimdiye kadar öğrendiklerin hakkında daha ayrıntılı bilgi için bkz[. İstenmeyen posta filtresi ilkelerini yapılandırma - Office 365 | ](../../office-365-security/configure-your-spam-filter-policies.md)|  Microsoft Docs [EOP'de kimlik avı önleme ilkelerini yapılandırma - Office 365 | ](../../office-365-security/configure-anti-phishing-policies-eop.md) |  Microsoft Docs [Kötü amaçlı yazılımdan koruma ilkelerini yapılandırma - Office 365 | ](../../office-365-security/configure-anti-malware-policies.md)|  Microsoft Docs [Office 365 için Microsoft Defender Kasa Ekler ilkelerini ayarlama - Office 365 | Microsoft Docs](../../office-365-security/set-up-safe-attachments-policies.md)

## <a name="next-steps"></a>Sonraki Adımlar

- Kuruluşunuzun marka logosu, görünen adı ve sorumluluk reddini etkinleştirmek için karantina ilkesinde bulunan **Genel ilkeyi** kullanın.
- Ayrıca karantina bildirimi için **Kullanıcı sıklığını 1 gün** olarak ayarlayın.

## <a name="more-information"></a>Daha fazla bilgi

Kuruluş markalama ve bildirim ayarları hakkında daha fazla bilgi için [karantina ilkeleri - Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md)
