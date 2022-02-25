---
title: Aramada Kiracı Microsoft 365 ayırma
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Bu makalede, Arama'da kiracı ayırmanın kiracı verilerini birbirinden ayırmak için kiracı yalıtımnın nasıl Microsoft 365 bulabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3416afdeceaa7000b516ec89b4a2a1e59d8708d0
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959690"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a>Aramada Kiracı Microsoft 365 ayırma

SharePoint Online araması, kiracılar arasında sızdırılan bilgilere karşı koruma ile paylaşılan veri yapılarının verimliliğini dengede paylaşan bir kiracı ayırma modeli kullanır. Bu modelle, Arama özelliklerinin şunları önleyeriz:

- Diğer kiracılardan belge içeren sorgu sonuçlarını geri dönme
- Sorgu sonuçlarında yeterli bilgilerin ortaya çıkar olması, nitelikli bir kullanıcının diğer kiracılar hakkında bilgi anladığı sonuçlar ortaya çıkar
- Başka bir kiracının şemasını veya ayarlarını gösterme
- Kiracılar arasında çözümleme işleme bilgilerini karıştırma veya sonuçları yanlış kiracıda depolama
- Başka bir kiracıdan sözlük girdilerini kullanma

Her kiracı veri türü için, kodda yanlışlıkla bilgi sızdır ızdırasını önlemek için bir veya daha fazla koruma katmanı kullanıruz. En kritik veriler, tek kusurların gerçek veya bilgi sızıntısını algılamayacak şekilde en fazla koruma katmanına sahip olduğundan emin olun.

## <a name="tenant-separation-for-the-search-index"></a>Arama Dizini için Kiracı Ayırmaları

Arama dizini, dizin bileşenlerini barındıran sunucularda diskte depolanır ve kiracılar dizin dosyalarını paylaşır. Kiracının dizine alan belgeleri yalnızca o kiracının sorguları için görünür durumdadır. Üç bağımsız mekanizma bilgi sızıntısını önler:

- Kiracı kimliği filtrelemesi
- Kiracı kimliği terimi öneki
- ACL denetimleri

Belgeleri yanlış kiracıya geri iade etmek için üç mekanizmanın da Search'e başarısız olması gerekir.

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>Kiracı Kimliği Filtreleme ve Kiracı Kimliği Terimi Öneki

Kiracı kimliğiyle tam metin dizininde dizine alan her terimin ön eklerini arayın. Örneğin, "*foo*" terimi "*123*" kimliğine sahip bir kiracı için dizine alındıyken, tam metin dizininde girdi "*123foo" olur*.

Her sorgu kiracı kimliği filtreleme adı verilen bir işlem kullanılarak kiracı kimliğini içerecek şekilde dönüştürülür. Örneğin, "*foo" sorgusu* "ana guid<*biçimine*>. *foo* AND *tenantID*:<*guid*>"; burada <*guid*> sorguyu gerçekleştiren kiracıyı temsil eder. Bu sorgu dönüştürmesi her dizin düğümünde  gerçekleşir ve bunu ne sorgu ne de içerik işleme etkileyenin. Kiracı kimliği her sorguya eklendiklerinden, bir kiracıda en iyi eşleşme derecelendirmesi değerine bakarak diğer kiracılarda bir terimin sıklığı ortaya atılamaz.

Kiracı kimliği terim öneki yalnızca tam metin dizininde gerçekleşir. "title *:foo*" gibi alanlı aramalar, kiracı kimliğinde terimlerin ön ekleri olmayan bir yapay arama dizinine gider. Bunun yerine, alanlı aramalara alan adı önek olur. Örneğin, "*title:foo*" sorgusu "*fields.title:foo AND fields.tenantID*:<*guid*>." Bir terimin sıklığı, yapay arama dizininde isabetlerin derecelendirmesini etkilemey olduğundan, terim ön ek özelliğine göre kiracı ayrımlarına gerek yoktur. "*title:foo" gibi bir alanlı arama* için kiracı içeriği ayırma, sorgu dönüştürmeye göre kiracı kimliği filtrelemeye bağlıdır.

## <a name="document-access-control-list-checks"></a>Belge Erişimi Denetim Listesi Denetimleri

Arama, arama dizinine kaydedilen ACL'ler aracılığıyla belgelere erişimi kontrol eder. Her öğe özel bir ACL alanında bir dizi terimle dizine alındı. ACL alanı, her grup veya kullanıcı için belgeyi görüntüley deneyimi için bir terim içerir. Her sorgu, kimliği doğrulanmış kullanıcının ait olduğu her grup için bir erişim denetimi girdisi (ACE) koşulları listesiyle geliştir edilir.

Örneğin, "Guid bilgi <*gibi* bir>. *foo AND tenantID*:<*guid*>" şöyle olur: "<*guid>*. *foo AND tenantID*:<*guidAND* >  (*docACL:*<*ace1OR*>  *docACL*:<*ace2OR*>  *docACL*:<*ace3*> *...*)"

Kullanıcı ve grup tanımlayıcıları ile bu şekilde ADE'ler benzersiz olduğundan, bu durum yalnızca bazı kullanıcılar tarafından görülebilen belgeler için kiracılar arasında ek güvenlik düzeyi sağlar. Kiracıda normal kullanıcılara erişim iznini alan özel "Dış kullanıcılar hariç herkes" ACE'sinde de aynı durum söz edilir. Ancak "Herkes" için ADE'ler tüm kiracılarda aynı olduğu için, ortak belgeler için kiracı ayırma kiracı kimliği filtrelemeye bağlıdır. A AC'leri reddet de de destek olar. Sorgu büyütmesi, ace'lerle eşleşme olduğunda sonuçtan belgeyi kaldıran bir yan tümce ekler.

Bir Exchange Online aramada dizin, SharePoint Online'da olduğu gibi kiracı kimliği (abonelik kimliği) yerine bireysel kullanıcının posta kutuları için posta kutusu kimliği bölümüdür. Bölümleme mekanizması SharePoint Online ile aynıdır, ancak ACL filtresi yoktur.
