---
title: Grupların ve grupların yönetimi için Microsoft 365 yaşam döngüsü Microsoft Teams
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Microsoft 365'da işbirliği araçları için yaşam döngüsü yönetim Microsoft 365
ms.openlocfilehash: a0f4622afd1a22b8cd6574865012b7f636fc06c5
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005017"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Grupların ve grupların yönetimi için Microsoft 365 yaşam döngüsü Microsoft Teams

Microsoft 365 gruplarda, kuruma gereken yönetim özelliklerini uygulamaya yardımcı olacak zengin bir araç kümesi vardır. 

Aşağıdaki bölümde özellikleri açıklar, en iyi uygulamaları önerip, yönetim gereksinimlerini ve bunları nasıl karşılayacaklarını belirlemek için doğru soruları sorma konusunda yol gösterici bilgiler sağlar.

## <a name="control-who-can-create-microsoft-365-groups"></a>Kimlerin grup oluştur Microsoft 365 denetleme

Gruplar; birden çok uç nokta (son kullanıcılar tarafından Outlook, SharePoint, Teams ve diğer ortamlar dahil olmak üzere) oluşturulabilir.

![resim desc.](../media/04.png)

Grup sahiplerini güçlendirmek ve kullanıcıların daha kolay çalışmalarını yapmalarına yardımcı olmak için self servis öneririz. Birçok farklı hizmet, hizmetin çalışması için grupların oluşturulmasını Microsoft 365, grup ve ekip oluşturmanın sınırlayıcı olması kullanıcıların üretkenliğini yavaşlatabilirsiniz.

Grupların oluşturulması için aşağıdaki yönetim seçeneklerini göz önünde önünden düşünün:

- Grupları sınırlamak için, kullanılmamaktadır grupları [otomatik olarak](microsoft-365-groups-expiration-policy.md) silmek için grupların süre sonu ilkelerini kullanın.
- Grup oluşturma işlemi, örneğin [tam zamanlı çalışanlar gibi dinamik üyelik](/azure/active-directory/users-groups-roles/groups-create-rule) içeren bir güvenlik gruplarının üyeleriyle sınırlandırın.
- Grup oluşturma işlemini bir güvenlik grubuyla sınırlandırarak kullanıcıların güvenlik grubunun üyesi olmak için, kuruluşlarının grup kullanımı ilkelerinde eğitimi tamamlamalarını gerekli hale getirir.

Kimlerin grup oluştur sınırlaması yapmak için bkz. Kimlerin grup [oluştur](manage-creation-of-groups.md) Microsoft 365 yönetme.

## <a name="group-delete-restore-and-archiving"></a>Grup silme, geri yükleme ve arşivleme

Grup Microsoft 365 silindiğinde, varsayılan olarak 30 gün boyunca korunur. Bu 30 günlük süre "geçici silme" olarak adlandırılır, çünkü grubu hala geri yükleyebilirsiniz. 30 gün sonra, grup ve onunla ilişkilendirilmiş içerik kalıcı olarak silinir ve geri yüklenemez.

Sohbeti, dosyaları veya postayı korumak için bekletme ilkeleriniz varsa, grup silindikten sonra bu öğeler korunur. Ayrıntılar [için bkz. Bekletme ilkeleri hakkında](../compliance/retention.md) bilgi.

Grubu silmek ama grup bağlantılı bir veya birden çok hizmetten içeriği korumak için bkz. Grupları, ekipleri ve grupları [Yammer](end-life-cycle-groups-teams-sites-yammer.md) bilgi.

## <a name="group-naming-policy"></a>Grup adlandırma ilkesi

Grup adlandırma ilkesi, grupları iki şekilde yönetmeye yardımcı olabilir:

- Grup adının başında veya sonunda sabit dizeleri veya Azure AD özniteliklerini ve bu grupla ilişkilendirilmiş e-posta adresini zorunlu kılınan bir ön ek/son ek adlandırma ilkesi kullanılabilir. Bunu yaparak, örneğin bölüm adlarının veya bölgelerin grup adlarında dahil edilmesini s belirttiysiniz.
- Engellenen sözcükler ilkesi, yöneticiler adları gibi bazı sözcüklerin grup adlarında kullanılmamalarını sağlar.

Adlandırma ilkeleri, grup bağlantılı hizmetlerden grup oluşturulduğunda uygulanır.

Gruplar için adlandırma ilkelerini kullanmaya karar verdiyseniz Gruplar adlandırma [Microsoft 365 bkz](groups-naming-policy.md).

## <a name="group-expiration-policy"></a>Grup süre sonu ilkesi

Bir son kullanma süresi belirtebilir ve bu dönemin sonuna ulaşan ancak yenilenmemiş olan tüm grup silinir. Son kullanma süresi, grubun oluşturulma tarihi veya son yenileme tarihiyle başlar.

Grupların süresini sona erecek şekilde ayar defa ayarlayın:
- Grubun sahipleri, süre sonu sona ererken grubu yenilemeleri hakkında bilgi edinzler.
- Etkin gruplar otomatik olarak yenilenir.
- Yenilenmemiş olan tüm grup silinir.
- Silinen tüm grup, 30 gün içinde grup sahipleri veya yöneticisi tarafından geri yüklenebilir.

Süre sonu ilkeleri, artık kullanımda yer alan grupların silinmemesiyle grupları sınırlandırmanın iyi bir yoludur. Grup süre sonu ilkesi oluşturmak için Gruplar Süre Sonu Microsoft 365 [bakın](microsoft-365-groups-expiration-policy.md).

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Eski çalışanı kaldırma ve verilerin güvenliğini sağlama](/microsoft-365/admin/add-users/remove-former-employee)
