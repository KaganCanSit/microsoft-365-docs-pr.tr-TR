---
title: Bilgi engelleri
description: Microsoft Purview'da bilgi engellerini yapılandırmayı öğrenin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, bilgi engelleri
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
ms.openlocfilehash: 21ad4f0cc6614bed3c579a8025d83200446fec18
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627249"
---
# <a name="information-barriers"></a>Bilgi engelleri

Microsoft 365, gruplar ve kuruluşlar arasında iletişim ve işbirliği sağlar ve gerektiğinde belirli kullanıcı grupları arasındaki iletişimi ve işbirliğini kısıtlama yollarını destekler. Bu durum, kuruluşunuzda çıkar çakışmasını önlemek için iki grup arasındaki iletişimi ve işbirliğini kısıtlamak istediğiniz durumları veya senaryoları içerebilir. Bu durum, iç bilgileri korumak için kuruluşunuz içindeki belirli kişiler arasındaki iletişimi ve işbirliğini kısıtlamanız gereken durumları da içerebilir.

Microsoft Purview Bilgi Engelleri (IB), Microsoft Teams, SharePoint Online ve OneDrive İş desteklenir. Uyumluluk yöneticisi veya IB yöneticisi, Microsoft Teams'de kullanıcı grupları arasındaki iletişimlere izin veren veya bunları engelleyen ilkeler tanımlayabilir. IB ilkeleri aşağıdaki gibi durumlarda kullanılabilir:

- Günlük tüccar grubundaki kullanıcı pazarlama ekibiyle iletişim kurmamalı veya dosya paylaşmamalıdır
- Gizli şirket bilgileri üzerinde çalışan finans personeli, kuruluş içindeki belirli gruplarla iletişim kurmamalı veya dosya paylaşmamalıdır
- Ticari gizli malzeme içeren bir şirket içi ekip, kendi kuruluşundaki belirli gruplardaki kişileri aramamalı veya çevrimiçi sohbet etmemelidir
- Araştırma ekibi yalnızca bir ürün geliştirme ekibiyle çevrimiçi aramalı veya sohbet etmelidir

## <a name="configure-information-barriers"></a>Bilgi engellerini yapılandırma

Kuruluşunuzda IB'yi yapılandırmak için aşağıdaki adımları kullanın:

![Insider risk çözümü bilgi engelleri adımları.](../media/ir-solution-ib-steps.png)

1. [Bilgi engelleri](information-barriers.md) hakkında bilgi edinin
2. [Önkoşulları ve izinleri](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met) yapılandırma
3. [Kuruluşunuzdaki kullanıcıları segmentlere ayırma](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. [IB ilkeleri](information-barriers-policies.md#step-3-create-ib-policies) oluşturma ve yapılandırma
5. [IB ilkelerini](information-barriers-policies.md#step-4-apply-ib-policies) uygulama

## <a name="more-information-about-information-barriers"></a>Bilgi engelleri hakkında daha fazla bilgi

- [IB ilkeleri için öznitelikler](information-barriers-attributes.md)
- [IB ilkelerini düzenleme veya kaldırma](information-barriers-edit-segments-policies.md)
