---
title: eBulma'da arama sorguları oluşturma (Premium)
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
description: Microsoft 365'de eBulma (Premium) kullanarak veri ararken arama kapsamını daraltmak için anahtar sözcükleri ve koşulları kullanın.
ms.openlocfilehash: cceac6974bacb066201120ac4972393f2323353c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995018"
---
# <a name="build-search-queries-for-collections-in-ediscovery-premium"></a>eBulma'da koleksiyonlar için arama sorguları oluşturma (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

eBulma (Premium) durumunda [koleksiyon](collections-overview.md) oluştururken arama sorgusunu yapılandırırken, yasal araştırmanızla en ilgili öğeleri döndürmek için arama kapsamını daraltmak üzere belirli içeriği ve koşulları bulmak için anahtar sözcükleri kullanabilirsiniz.

![Arama sonuçlarını daraltmak için anahtar sözcükleri ve koşulları kullanın.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Anahtar sözcük aramaları

Arama sorgusundaki Anahtar Sözcükler kutusuna bir **anahtar sözcük** sorgusu yazın. Anahtar sözcükleri, gönderilen ve alınan tarihler gibi e-posta iletisi özelliklerini ya da dosya adları veya belgenin son değiştirilme tarihi gibi belge özelliklerini belirtebilirsiniz. **AND**, **OR**, **NOT** ve **NEAR** gibi boole işleci kullanan daha karmaşık sorgular kullanabilirsiniz. Ayrıca, SharePoint ve OneDrive (e-posta iletilerinde değil) belgelerde hassas bilgileri (sosyal güvenlik numaraları gibi) arayabilir veya harici olarak paylaşılmış belgeleri arayabilirsiniz. **Anahtar Sözcükler** kutusunu boş bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik arama sonuçlarında olur.

## <a name="keyword-list"></a>Anahtar sözcük listesi

Alternatif olarak, **Anahtar sözcük listesini göster** onay kutusunu seçebilir ve her satıra bir anahtar sözcük veya anahtar sözcük tümceciği yazabilirsiniz. Her satırdaki anahtar sözcükler, oluşturulan arama sorgusundaki **OR** işlecine benzer bir mantıksal işleç (arama sorgusu söz diziminde *c:s* olarak gösterilir) ile bağlanır. Bu, herhangi bir satırda anahtar sözcük içeren öğelerin arama sonuçlarında olduğu anlamına gelir. eBulma (Premium) arama sorgularında anahtar sözcük listesine en fazla 180 satır ekleyebilirsiniz.

![Sorgudaki her anahtar sözcükle ilgili istatistikleri almak için anahtar sözcük listesini kullanın.](../media/KeywordListSearch.png)

Anahtar sözcük listesini neden kullanmalısınız? Anahtar sözcük listesindeki her anahtar sözcükle eşleşen öğe sayısını gösteren istatistikler alabilirsiniz. Bu, en etkili (ve en az) anahtar sözcükleri hızla belirlemenize yardımcı olabilir. Anahtar sözcükler listesindeki bir satırda bir anahtar sözcük tümceciği (parantez içinde) de kullanabilirsiniz. Arama istatistikleri hakkında daha fazla bilgi için bkz [. Koleksiyon istatistikleri ve raporları](collection-statistics-reports.md)

## <a name="conditions"></a>Koşul -ları

Arama kapsamını daraltmak ve daha iyileştirilmiş bir sonuç kümesi döndürmek için arama koşulları ekleyebilirsiniz. Her koşul, aramayı başlattığınızda oluşturulan ve çalıştırılan arama sorgusuna bir yan tümce ekler. Koşul, **and** işlecine benzer bir mantıksal işleç (arama sorgusu söz diziminde *c:c* olarak gösterilir) tarafından anahtar sözcük kutusunda belirtilen anahtar sözcük sorgusuna mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de arama sonuçlarına dahil edilecek bir veya daha fazla koşulu karşılaması gerektiğini gösterir. Koşulların sonuçlarınızı daraltmanıza bu şekilde yardımcı olur. Arama sorgusunda kullanabileceğiniz koşulların listesi ve açıklaması için [Anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md#search-conditions) bölümündeki "Arama koşulları" bölümüne bakın.
