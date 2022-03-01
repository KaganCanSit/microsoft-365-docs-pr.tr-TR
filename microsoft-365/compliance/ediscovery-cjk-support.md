---
title: Destek için CJK/Double Byte Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: İngilizce'Advanced eDiscovery karakter Microsoft 365 çift byte karakter kümesi kullanan Çince, Japonca ve Korece (CJK) dillerini nasıl desteklediğini öğrenin.
ms.openlocfilehash: 4c1871eb49754ba93d762989e3cff9c53950d2c6
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027533"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>Destek için CJK dil Advanced eDiscovery

Advanced eDiscovery gözden geçirme kümesinde aşağıdaki gelişmiş senaryolarda çift byte karakter kümesi dillerini destekler (bunlar toplu olarak *CJK* dilleri olarak bilinen Basitleştirilmiş Çince, Geleneksel Çince, Japonca ve Korecedir):

- Gözden [geçirme kümesinde verileri sorgularken](review-set-search.md).

- Belgeleri bir [gözden geçirme kümesinde etiketlerken](tagging-documents.md).

- Yinelenen [algılamayı, e-posta dizisini ve tema](analyzing-data-in-review-set.md) çözümlemelerini kullanarak bir gözden geçirme kümesinde büyük/küçük harf verilerini çözümlerken.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**CJK karakterleri içeren öğeleri toplamak için nasıl arama oluşturabilirim?**

Bir metinde içerik ararken anahtar sözcük [aramaları](building-search-queries.md#keyword-searches), anahtar sözcük [sorguları](keyword-queries-and-search-conditions.md) ve arama koşulları için CJK Advanced eDiscovery. Core eKovery ve İçerik Arama'da içerik ararken CJK karakterlerinin aranma özelliği de desteklene.

Boole işleçleri **AND, OR**[,](keyword-queries-and-search-conditions.md#search-conditions) **NOT** ve NEAR dahil olmak üzere tüm arama işleçleri ve arama koşulları için CJK desteği **sağlıyoruz**.[](keyword-queries-and-search-conditions.md#search-operators)

İçerik konumlarında veya öğelerinde CJK karakterlerinin bulunduğuna eminsiniz ancak aramalar herhangi bir sonuç döndürenip, sorgu dili-ülke/bölge simgesine tıklayın. ![İçerik arama'daki sorgu dili-ülke/bölge simgesi.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) ve arama için ilgili dilin ülke kültür kodu değerini seçin. Varsayılan dil/bölge nötr olur.

**Aynı anda birden çok dil için arama kullanabilir miyim?**

Bu, arama senaryonıza bağlıdır.

- [Advanced eDiscovery'ta bir gözden](review-set-search.md) geçirme kümesinde verileri sorgularken, birden çok dili arayabilirsiniz.

- Veri [toplamak için bir arama oluşturmaktayken](create-draft-collection.md) hedefle hedefleriniz olan her dil için ayrı koleksiyonlar oluşturun. Örneğin, hem Çince hem de Korece içeren bir belgeyi arıyorsanız, ilk koleksiyonunuz için Çince'yi ve ikinci koleksiyonunuz için de Korece'yi seçin.

**Gözden geçirme kümesinde sorgular için dil seçmek için sorgu dili-ülke/bölge simgesini göremiyorum. Gözden geçirme kümesi aramalarında sorgu dilini nasıl belirtebilirsiniz?**

Gözden geçirme kümesi sorgularında, belge dilini belirtmenize gerek yok. Advanced eDiscovery gözden geçirme kümesine içerik eklerken belge dillerini otomatik olarak algılar. Bu, sorgu sonuçlarınızı gözden geçirme kümesi içinde en iyi duruma getirmenize yardımcı olur.

**Dosya meta verilerinde algılanan dilleri [görebilir miyim](view-documents-in-review-set.md#file-metadata)?**

Hayır, dosya meta verilerinde algılanan dilleri göremiyorum.

**Gözden geçirme kümesinde belge dillere göre filtre uygulamam gerekir mi**?

Hayır, gözden geçirme kümesinde belge dillerini filtreleyamaz, sıraamaz veya bu dillere göre aramaamazsınız.

**Gözden geçirme kümesi senaryoları için bu CJK sürümü var olan aramalarımı ve gözden geçirme kümelerimi etkileyecek mi?**

Hayır, var olan arama ve gözden geçirme kümelerinizi hiçbiri değişmez. Var olan verileri yeniden biçimlendirmeniz gerekmektedir ve İngilizce metin arama sonuçları aynı olur.

**Görüntü dilimi Çince, Japonca veya Korece olarak nasıl değiştirebilirim?**

Görüntü dilini ve saat dilimini değiştirme hakkında bilgi için bkz. Saat ve saat dilimi ayarları [nasıl Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Bilinen sorunlar

- OCR resim dosyalarından CJK karakterlerini desteklemez

- Ek Açıklama görünümündeki e-posta dosyaları (*.eml ve *.[](view-documents-in-review-set.md#annotate-view)msg gibi) CJK dillerinde destek desteklemez.

- Metin görünümünde arama [araması vurgulama](view-documents-in-review-set.md#text-view) , CJK dilleri için desteklenmiyor.

- Verileri [çözümlemek için](using-relevance.md) kullanılan ilgi düzeyi modülü CJK dillerini desteklemez.

- [Sorgu tabanlı sındırlar](managing-holds.md#manage-non-custodial-holds) CJK dillerde destek desteklemez.