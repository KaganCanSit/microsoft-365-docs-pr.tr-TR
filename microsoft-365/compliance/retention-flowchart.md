---
title: Bir öğenin ne zaman korunacaklarını veya kalıcı olarak silineceklerini belirlemek için akış çizelgesi
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
ms.openlocfilehash: b9c3b94dcb50499b6af72fd124da384f90d16da9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021818"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Bir öğenin ne zaman korunacaklarını veya kalıcı olarak silineceklerini belirlemek için akış çizelgesi

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bir öğeye bekletme ilkeleri uygulamak için aşağıdaki [](retention.md#the-principles-of-retention-or-what-takes-precedence) akış çizelgesini kullanarak sistemin öğeyi alıkoydurdurarak veya bekletme etiketi ya da bekletme ilkesi sonucu olarak kalıcı olarak silebilir.

Bu mantık akışı, aşağıdaki koşullardan biri geçerli olduğunda bir öğe için kullanılır:

- Birden çok bekletme ilkesi uygulanmış
- Bir bekletme etiketi ve bir veya birden çok bekletme ilkesi var

Bir öğe eBulma bekletmeye (veya eski Mahkeme nedeniyle tutma ya da In-Place Bekletme teknolojilerine) tabi olduğunda, her zaman bekletme ilkeleri ve bekletme etiketi karar akışları öncesinde korunur.

Bu akış çizelgesinde kullanılan terimlerden herhangi biri size yabancı değilse bkz. Bekletme ilkeleri [ve bekletme etiketleri hakkında bilgi edin.](retention.md)


   ![Bir öğenin ne zaman korunacaklarını veya kalıcı olarak silineceklerini belirleyen akış çizelgesi.](../media/retention-flowchart.svg)

> [!NOTE]
> Öğe için en uzun bekletme süresi ile bir bekletme ilkesi veya etikette belirtilen en uzun bekletme süresi arasında ayrım yapmak önemlidir. Benzer şekilde, öğenin en kısa son kullanım süresi ile bekletme ilkesinde belirtilen en kısa süre arasında.
> 
> Daha fazla bilgi için, bekletme bölümündeki ilkelerde grafik [sonrasındaki açıklamaya](retention.md#the-principles-of-retention-or-what-takes-precedence) bakın.
