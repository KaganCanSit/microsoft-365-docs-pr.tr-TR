---
title: Bir öğenin ne zaman saklandığını veya silindiğini saptamak için akış çizelgesi
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bir öğenin birden çok bekletme ilkesi veya bekletme etiketi ve bekletme ilkesi olduğunda sonucu belirlemek için akış çizelgesi kullanma
ms.openlocfilehash: 4e5c1cf887144f89764e88a39ba14a95a2df576c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633465"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Bir öğenin ne zaman tutulacağını veya kalıcı olarak silineceğini saptamak için akış çizelgesi

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Bir öğeye [bekletme ilkelerini](retention.md#the-principles-of-retention-or-what-takes-precedence) uygulamak için aşağıdaki akış çizelgesini kullanarak sistemin saklama etiketinin veya bekletme ilkesinin bir sonucu olarak saklamayı mı yoksa kalıcı olarak mı sileceğini belirleyin.

Bu mantıksal akış, aşağıdaki koşullardan biri uygulandığında bir öğe için kullanılır:

- Birden fazla bekletme ilkesi uygulandı
- Bekletme etiketi ve bir veya daha fazla bekletme ilkesi vardır

Bir öğe bir eBulma ayrı tutmasına (veya Dava tutma veya In-Place tutma eski teknolojilerine) tabi olduğunda, saklama ilkeleri ve bekletme etiketi için karar akışlarından önce her zaman korunur.

Bu akış çizelgesinde kullanılan terimlerden herhangi biri size yabancıysa bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).


   ![Bir öğenin ne zaman tutulacağını veya kalıcı olarak silineceğini belirlemek için akış çizelgesi.](../media/retention-flowchart.svg)

> [!NOTE]
> Öğe için en uzun saklama süresi ile bir bekletme ilkesi veya etiketinde belirtilen en uzun süre arasında ayrım yapmak önemlidir. Benzer şekilde, öğe için en kısa süre sonu tarihi ile bekletme ilkesinde belirtilen en kısa süre arasında.
> 
> Daha fazla bilgi için [bekletme ilkeleri](retention.md#the-principles-of-retention-or-what-takes-precedence) bölümündeki grafik sonrasındaki açıklamaya bakın.
