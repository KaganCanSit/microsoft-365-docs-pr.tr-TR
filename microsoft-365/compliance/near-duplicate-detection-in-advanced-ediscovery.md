---
title: eBulma'da neredeyse yinelenen algılama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: eBulma'da (Premium) büyük/küçük harf verilerini analiz ederken benzer belgeleri kısa metne göre gruplandırmak için neredeyse yinelenen algılamayı kullanın.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e22444845005f4cf155340e13856722976715d91
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997614"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>eBulma'da neredeyse yinelenen algılama (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bir alt kümenin aynı şablonu temel aldığı ve çoğunlukla aynı ortak dile sahip olduğu, burada ve orada birkaç farkla gözden geçirilecek bir belge kümesini düşünün. Gözden geçiren kişi bu alt kümeyi tanımlayıp bunlardan birini ayrıntılı bir şekilde gözden geçirebilse ve geri kalanlar için farkları gözden geçirebilse, tüm belgelerin kapsanması için yalnızca birkaç zaman ayırarak benzersiz bilgileri kaçırmaz. Yakın yinelenen algılama, inceleme sürecinizi daha verimli hale getirmenize yardımcı olmak için metin olarak benzer belgeleri gruplandırıyor.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Neredeyse yinelenen algılama çalıştırıldığında, sistem her belgeyi metinle ayrıştırıyor. Ardından, benzerliklerinin ayarlanan eşikten büyük olup olmadığını belirlemek için her belgeyi birbiriyle karşılaştırır. Bu durumda belgeler birlikte gruplandırılır. Tüm belgeler karşılaştırılıp gruplandırıldıktan sonra, her gruptan bir belge "özet" olarak işaretlenir; belgelerinizi gözden geçirirken, önce bir özeti gözden geçirebilir ve aynı yakın yinelenen kümedeki diğer belgeleri gözden geçirerek özet ile gözden geçirmedeki belge arasındaki farka odaklanabilirsiniz.
