---
title: Web'de arama sorguları Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: Belirli bir alanı kullanarak verileri ararken arama kapsamını daraltmak için anahtar sözcükleri ve Advanced eDiscovery koşulları Microsoft 365.
ms.openlocfilehash: 8ad708b9733dd7d96f1025f116a31a92d757afd2
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027539"
---
# <a name="build-search-queries-for-collections-in-advanced-ediscovery"></a>Web'de koleksiyonlar için arama sorguları Advanced eDiscovery

Advanced eDiscovery durumunda bir koleksiyon oluştururken arama sorgusunu yapılandırarak, aramanın kapsamını yasal incelemenize en uygun öğeleri geri çekmek üzere daraltmak üzere belirli içerik ve koşulları bulmak için anahtar sözcükler kullanabilirsiniz.[](collections-overview.md)

![Arama sonuçlarını daraltmak için anahtar sözcükleri ve koşulları kullanın.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Anahtar sözcük aramaları

Arama sorgusunun Anahtar Sözcükler **kutusuna bir** anahtar sözcük sorgusu yazın. Gönderilen ve alınan tarihler gibi anahtar sözcükleri, e-posta iletisi özelliklerini ya da dosya adları veya belgenin en son değiştir olduğu tarih gibi belge özelliklerini belirtebilirsiniz. VE, YADA, NOT ve NEAR gibi Boole işleci kullanan daha **karmaşık** **sorgular** **kullanabilirsiniz**. Ayrıca, SharePoint ve OneDrive'daki belgelerde (e-posta iletileri içinde değil) hassas bilgileri (sosyal güvenlik numaraları gibi) arayabilir veya dış olarak paylaşılan belgeleri arayabilirsiniz. Anahtar Sözcükler kutusunu **boş** bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik arama sonuçlarında yer verir.

## <a name="keyword-list"></a>Anahtar sözcük listesi

Alternatif olarak, Anahtar sözcük listesini **göster onay kutusunu** seçin ve her satıra bir anahtar sözcük veya anahtar sözcük tümceciği yazın. Her satırdaki anahtar sözcükler, oluşturulan arama sorgusunda **OR** işlecine benzeyen bir mantıksal işleçle (arama sorgusu söz dizimsinde *c:s* ile temsil edilen) bağlantılıdır. Bu, herhangi bir satırda anahtar sözcük içeren öğelerin arama sonuçlarında yer alan öğeler olduğu anlamına gelir. Arama sorgularında anahtar sözcük listesine en çok 180 Advanced eDiscovery ekleyebilirsiniz.

![Sorguda yer alan her anahtar sözcükle ilgili istatistikler almak için anahtar sözcük listesini kullanın.](../media/KeywordListSearch.png)

Anahtar sözcük listesini neden kullanasınız? Anahtar sözcük listesinde her anahtar sözcükle kaç öğenin eş olduğunu göstermek için istatistikler eldeebilirsiniz. Bu, en etkili (ve en az) anahtar sözcükleri hızla tanımlamanıza yardımcı olabilir. Anahtar sözcükler listesinde bir satırda bir anahtar sözcük tümceciği de (parantez içinde) kullanabilirsiniz. Arama istatistikleri hakkında daha fazla bilgi için bkz [. Koleksiyon istatistikleri ve raporları](collection-statistics-reports.md)

## <a name="conditions"></a>Koşullar

Bir aramanın kapsamını daraltmak ve daha daraltılmış bir sonuç kümesi geri dönmek için arama koşulları  eklersiniz. Her koşul, oluşturulan ve siz arama başlatmak üzere çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul, anahtar sözcük kutusunda belirtilen anahtar sözcük sorgusuna, AND işlecine benzeyen bir mantıksal işleçle (arama sorgusu söz dizimsinde *c:c* ile temsil edilen) **mantıksal olarak** bağlanır. Bu, öğelerin arama sonuçlarına dahil etmek için hem anahtar sözcük sorgusunu hem de bir veya daha fazla durumu karşılaması gereken anlamına gelir. Koşullar, sonuçlarınızı daraltmanıza böyle yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için, Anahtar sözcük sorguları ve arama koşulları'nın "Arama koşulları" [bölümüne bakın](keyword-queries-and-search-conditions.md#search-conditions).
