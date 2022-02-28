---
title: Yinelenen algılamaya yakın - eBulma
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
description: Metin olarak benzeyen belgeleri, örnek olay çözümlemeleri veya çözümlemek için yinelenen algılamaya yakın Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: cbd01bd38f45a397a82a8db3774997349f4eec88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987307"
---
# <a name="near-duplicate-detection-in-advanced-ediscovery"></a>Advanced eDiscovery'de yinelenen algılamanın Advanced eDiscovery

Bir alt kümenin aynı şablonu temel alan ve burada ve burada birkaç farklılıkla çoğunlukla aynı ortak dile sahip olduğu, gözden geçirnecek bir belge kümesi düşünün. Gözden geçiren biri bu alt kümeyi tanımlayabilirse, bunlardan birini kapsamlı bir şekilde gözden geçirerek geri kalan kısmın arasındaki farkları gözden geçirese, benzersiz hiçbir bilgiyi kaçıramaz ve bu şekilde tüm belgelerin kapak yazılarını okumalarını çok az zaman alabilir. Yinelenen algılamanın yakınında, inceleme sürecinizi daha verimli hale getirirken belgeye metin olarak benzeyen belgeleri bir arada gruplamanız gerekir.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Yinelenen algılamaya yakın bir yerde çalıştırılan sistem, her belgeyi metinle ayrıştırıyor. Ardından, benzerliklerinin küme eşiğinden büyük olup olmadığını belirlemek için her belgeyi diğerleriyle karşılaştırıldığında. Öyle ise, belgeler birlikte grup grup gruplandı. Tüm belgeler karşılaştırıldıktan ve gruplandığında, her gruptan bir belge "özet" olarak işaretlenir; özetini gözden geçirerek, önce bir özet gözden geçirerek, yakın çoğaltılmış küme içinde diğer belgeleri gözden geçirerek, gözden geçirılan özet ile belge arasındaki farka odaklanabilirsiniz.
