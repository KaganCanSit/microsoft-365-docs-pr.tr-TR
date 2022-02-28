---
title: E-posta dizileri Advanced eDiscovery
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
description: Bir ileti çözümlemesi Advanced eDiscovery e-posta dizileri bir e-posta konuşmalarını ayrıştırıyor ve her iletiyi farklı kategorilere ayırıyor.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 788858d6acaccbe07f3190b5adaaa05fe95c33a5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983721"
---
# <a name="email-threading-in-advanced-ediscovery"></a>E-posta dizileri Advanced eDiscovery

Bir süredir devam eden bir e-posta konuşmalarını düşünün. Çoğu durumda, e-posta ileti dizisinde yer alan son ileti önceki tüm iletilerin içeriğini içerir. Bu nedenle, son iletinin gözden geçirmesi konuşmada geçen konuşmanın tam bağlamını sağlar. E-posta dizileri, gözden geçirenlerin herhangi bir bağlam kaybı olmadan toplanan belgelerin çok küçük bir bölümünü gözden geçirmesini sağlar.

## <a name="what-does-email-threading-do"></a>E-posta zincirleri ne işe geliyor?

E-posta ileti dizileri, her e-posta iş parçacığını ayrıştırarak tek tek iletilere olan iş parçacıklarını çözümler. Her e-posta zinciri, tek tek iletiler zinciridir. Advanced eDiscovery e-posta iletilerinin benzersiz içeriği olup olmadığını veya zincirin (üst iletiler) e-posta zincirinin son iletisinde wholly olup olmadığını belirlemek için gözden geçirme kümesi içindeki tüm e-posta dağınıklarını analiz eder. E-posta iletileri dört kapsayıcı değere ayrılır:

- **Kapsayıcı**: Kapsayıcı bir *e-posta* , e-posta ileti dizisinde yer alan son e-posta iletisidir ve bu e-posta ileti dizisinde yer alan önceki tüm içeriği içerir.

- **Kapsayıcı eksi**: E-posta ileti dizisi  içinde belirli bir iletiyle ilişkilendirilmiş bir veya daha fazla ek varsa, e-posta iletisi Kapsayıcı olarak belirlenmiştir. Gözden geçirenler, iş parçacığı içindeki belirli e-posta iletisinde ilişkilendirilmiş ekleri olduğunu belirlemek için Kapsayıcı eksi değerini kullanabilir. 

- **Kapsayıcı kopya**: E-posta iletisi, Kapsayıcı veya *Kapsayıcı* eksi iletinin tam bir kopyası ise, Kapsayıcı bir kopya olarak kabul edilir. 

- **Yok**: *Yok değeri* , iletinin içeriğinin Kapsayıcı veya Kapsayıcı eksi olarak işaretlenmiş en az bir e-posta iletisi içinde yer içerdiğini gösterir.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Görüşmelerde yapılan konuşmalardan Outlook?

Bir bakışta bu, çalışma sayfalarındaki konuşma gruplamaları gibi Outlook. Bununla birlikte, bazı önemli farklar vardır. İki konuşmaya mürekkeple yapılan bir e-posta konuşmalarını düşünün; Örneğin, konuşmada son e-posta olmayan bir e-posta yanıtını alan biri, konuşmada son iki e-postanın da benzersiz içeriği olur.

Outlook e-postaları yine de tek bir konuşmada gruplandırabilirsiniz; yalnızca son e-postayı okumak, benzersiz içeriği de içeren ikinciden son e-postanın bağlamının eksik olması anlamına geliyor. E-posta zincirleri her e-postayı tek tek bileşenlerle ayrıştırıyor ve bunları karşılaştırıyor olduğundan, e-posta zincirleri son iki e-postanın ikisini de dahil olarak işaretleyecek ve böylece kapsayıcı olarak işaretlenmiş tüm e-postaları okuduğun sürece hiçbir bağlamı kaçırmayacağız.
