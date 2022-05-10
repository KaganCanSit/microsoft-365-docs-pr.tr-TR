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
ms.openlocfilehash: cf35a89faf3ed526c94acf362f1a927eb36420f0
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286812"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Bir öğenin ne zaman tutulacağını veya kalıcı olarak silineceğini saptamak için akış çizelgesi

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

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
