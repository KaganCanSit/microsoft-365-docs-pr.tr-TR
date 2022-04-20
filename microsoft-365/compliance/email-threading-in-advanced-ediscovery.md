---
title: eBulma'da e-posta yazışması oluşturma (Premium)
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
description: eBulma (Premium) analizi yaparken, e-posta yazışması bir e-posta konuşmasını ayrıştırıp her iletiyi farklı kategorilere ayırır.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 51cc9ce09f1f2c9c95c3ab5a7f2175516c9ed199
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948715"
---
# <a name="email-threading-in-ediscovery-premium"></a>eBulma'da e-posta yazışması oluşturma (Premium)

Bir süredir devam eden bir e-posta konuşmasını düşünün. Çoğu durumda, e-posta yazışmasının son iletisi önceki tüm iletilerin içeriğini içerir. Bu nedenle, son ileti gözden geçirilirken yazışmada gerçekleşen konuşmanın tam bir bağlamı gösterilir. E-posta yazışması, gözden geçirenlerin herhangi bir bağlamı kaybetmeden toplanan belgelerin bir bölümünü gözden geçirebilmesi için bu tür iletileri tanımlar.

## <a name="what-does-email-threading-do"></a>E-posta yazışmaları ne işe olur?

E-posta yazışması her e-posta yazışmasını ayrıştırıp ayrı ayrı iletilere oluşturur. Her e-posta yazışması, ayrı ayrı iletiler zinciridir. Microsoft Purview eKeşif (Premium), bir e-posta iletisinin benzersiz içeriğe sahip olup olmadığını veya zincirin (üst iletiler) e-posta yazışmasında son iletide tamamen yer alıp almadığını belirlemek için gözden geçirme kümesindeki tüm e-posta karmaşıklıklarını analiz eder. E-posta iletileri dört kapsayıcı değere ayrılır:

- **Kapsayıcı**: *Kapsayıcı* e-posta, bir e-posta yazışmasında son e-posta iletisidir ve bu e-posta yazışmasının önceki tüm içeriğini içerir.

- **Dahil eksi**: E-posta yazışması içinde belirli bir iletiyle ilişkilendirilmiş bir veya daha fazla ek varsa, e-posta iletisi *Kapsayıcı eksi* olarak belirlenir. Gözden geçiren, iş parçacığındaki belirli e-posta iletisinin ilişkili ekleri olduğunu belirlemek için Inclusive eksi değerini kullanabilir. 

- **Kapsayıcı kopya**: E-posta iletisi, *Kapsayıcı* veya Kapsayıcı eksi iletisinin tam kopyasıysa Kapsayıcı kopya olarak kabul edilir. 

- **Hiçbiri**: *Hiçbiri* değeri, iletinin içeriğinin Kapsayıcı veya Kapsayıcı eksi olarak işaretlenmiş en az bir e-posta iletisinde tamamen bulunduğunu gösterir.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Outlook konuşmalarından farkı nedir?

Bu, bir bakışta Outlook konuşma gruplandırmalarına benzer. Ancak bazı önemli ayrımlar vardır. İki konuşmaya çatallanmış bir e-posta konuşması düşünün; örneğin, birisi konuşmadaki en son e-posta olmayan bir e-postayı yanıtladığından, konuşmadaki son iki e-postanın da benzersiz içeriği vardır.

Outlook e-postaları tek bir konuşmada gruplandırmaya devam eder; yalnızca son e-postayı okumak, benzersiz içerik de içeren ikinciden son e-postanın bağlamının eksik olduğu anlamına gelir. E-posta yazışması her e-postayı ayrı ayrı bileşenlere ayırıp karşılaştırdığından, e-posta yazışması son iki e-postayı da kapsayıcı olarak işaretleyerek kapsayıcı olarak işaretlenmiş tüm e-postaları okuduğunuz sürece bağlamı kaçırmamanızı sağlar.
