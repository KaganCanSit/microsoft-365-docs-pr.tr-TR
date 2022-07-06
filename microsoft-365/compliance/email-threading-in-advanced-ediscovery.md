---
title: eBulma'da e-posta yazışması oluşturma (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: EBulma (Premium) analizi yaparken, e-posta yazışması bir e-posta konuşmasını ayrıştırıp her iletiyi farklı kategorilere ayırır.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: a17f746cb0c88fb68e4654d0dd7de528135d62ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629717"
---
# <a name="email-threading-in-ediscovery-premium"></a>eBulma'da e-posta yazışması oluşturma (Premium)

Bir süredir devam eden bir e-posta konuşmasını düşünün. Çoğu durumda, e-posta yazışmasının son iletisi önceki tüm iletilerin içeriğini içerir. Bu nedenle, son ileti gözden geçirilirken yazışmada gerçekleşen konuşmanın tam bir bağlamı gösterilir. E-posta yazışması, gözden geçirenlerin herhangi bir bağlamı kaybetmeden toplanan belgelerin bir bölümünü gözden geçirebilmesi için bu tür iletileri tanımlar.

## <a name="what-does-email-threading-do"></a>E-posta yazışmaları ne işe olur?

E-posta yazışması her e-posta yazışmasını ayrıştırıp ayrı ayrı iletilere oluşturur. Her e-posta yazışması, ayrı ayrı iletiler zinciridir. Microsoft Purview eKeşif (Premium), bir e-posta iletisinin benzersiz içeriği olup olmadığını veya zincirin (üst iletiler) e-posta yazışmasında son iletide tamamen bulunup bulunmadığını belirlemek için gözden geçirme kümesindeki tüm e-posta iletilerini analiz eder. E-posta iletileri dört kapsayıcı değere ayrılır:

- **Kapsayıcı**: *Kapsayıcı* e-posta, bir e-posta yazışmasında son e-posta iletisidir ve bu e-posta yazışmasının önceki tüm içeriğini içerir.

- **Dahil eksi**: E-posta yazışması içinde belirli bir iletiyle ilişkilendirilmiş bir veya daha fazla ek varsa, e-posta iletisi *Kapsayıcı eksi* olarak belirlenir. Gözden geçiren, iş parçacığındaki belirli e-posta iletisinin ilişkili ekleri olduğunu belirlemek için Inclusive eksi değerini kullanabilir. 

- **Kapsayıcı kopya**: E-posta iletisi, *Kapsayıcı* veya Kapsayıcı eksi iletisinin tam kopyasıysa Kapsayıcı kopya olarak kabul edilir. 

- **Hiçbiri**: *Hiçbiri* değeri, iletinin içeriğinin Kapsayıcı veya Kapsayıcı eksi olarak işaretlenmiş en az bir e-posta iletisinde tamamen bulunduğunu gösterir.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Outlook'taki konuşmalardan farkı nedir?

Bir bakışta bu, Outlook'taki konuşma gruplandırmalarına benzer. Ancak bazı önemli ayrımlar vardır. İki konuşmaya çatallanmış bir e-posta konuşması düşünün; örneğin, birisi konuşmadaki en son e-posta olmayan bir e-postayı yanıtladı, bu nedenle konuşmadaki son iki e-postanın da benzersiz içeriği var.

Outlook yine de e-postaları tek bir konuşmada gruplandıracak; yalnızca son e-postayı okumak, benzersiz içerik de içeren ikinciden sona e-postanın bağlamının eksik olduğu anlamına gelir. E-posta yazışması her e-postayı ayrı ayrı bileşenlere ayırıp karşılaştırdığından, e-posta yazışması son iki e-postayı da kapsayıcı olarak işaretleyerek kapsayıcı olarak işaretlenmiş tüm e-postaları okuduğunuz sürece bağlamı kaçırmamanızı sağlar.
