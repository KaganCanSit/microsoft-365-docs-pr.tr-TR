---
title: eBulma için CJK/Double Byte desteği (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft 365'deki Microsoft Purview eKeşif (Premium) uygulamasının çift baytlık karakter kümesi kullanan Çince, Japonca ve Korece (CJK) dilleri nasıl desteklediğini öğrenin.
ms.openlocfilehash: e6399136713ff7be4b3c065de05b587a3f942b01
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095916"
---
# <a name="cjk-language-support-for-ediscovery-premium"></a>eKeşif için CJK dil desteği (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif (Premium), bir inceleme kümesindeki aşağıdaki gelişmiş senaryolar için çift baytlık karakter kümesi dillerini destekler (bunlar topluca *CJK* dilleri olarak bilinen Basitleştirilmiş Çince, Geleneksel Çince, Japonca ve Korece'yi içerir):

- [Bir gözden geçirme kümesindeki verileri sorguladığınızda](review-set-search.md).

- [Belgeleri bir gözden geçirme kümesinde etiketlediğinizde](tagging-documents.md).

- Bir [gözden geçirme kümesindeki büyük/küçük harf verilerini](analyzing-data-in-review-set.md) neredeyse yinelenen algılama, e-posta yazışması ve tema analizi kullanarak analiz ettiğinizde.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**CJK karakterleri içeren öğeleri toplamak için bir arama oluşturmak Nasıl yaparım??**

eBulma'da (Premium) içerik ararken [anahtar sözcük aramaları](building-search-queries.md#keyword-searches), [anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md) için CJK karakterlerini kullanabilirsiniz. Microsoft Purview eKeşif (Standart) ve İçerik Arama'da içerik ararken CJK karakterlerini arama da desteklenir.

Boole [işleçleri](keyword-queries-and-search-conditions.md#search-operators) **VE**, **OR**, **NOT** ve **NEAR** dahil olmak üzere tüm arama işleçleri ve [arama koşulları](keyword-queries-and-search-conditions.md#search-conditions) için CJK desteği sağlıyoruz.

İçerik konumlarının veya öğelerin CJK karakterleri içerdiğinden eminseniz ancak aramalar sonuç döndürmüyorsa sorgu dili-ülke/bölge simgesine tıklayın ![İçerik aramasında dil-ülke/bölge simgesini sorgula.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) ve arama için ilgili dil-ülke kültür kodu değerini seçin. Varsayılan dil/bölge nötrdür.

**Aynı anda birden çok dil arayabilir miyim?**

Arama senaryonuza bağlıdır.

- eBulma'da (Premium) [bir gözden geçirme kümesindeki verileri sorguladığınızda](review-set-search.md), birden çok dil arayabilirsiniz.

- [Veri toplamak için bir arama oluşturduğunuzda](create-draft-collection.md), hedeflediğiniz her dil için ayrı koleksiyonlar oluşturun. Örneğin, hem Çince hem de Korece içeren bir belge arıyorsanız, ilk koleksiyonunuz için Çince'yi ve ikinci koleksiyonunuz için Korece'yi seçin.

**Gözden geçirme kümesindeki sorgular için dil seçmek için sorgu dili-ülke/bölge simgesini görmüyorum. Gözden geçirme kümesi aramasında sorgu dilini nasıl belirtebilirim?**

Gözden geçirme kümesi sorguları için bir belge dili belirtmeniz gerekmez. eBulma (Premium), bir gözden geçirme kümesine içerik eklediğinizde belge dillerini otomatik olarak algılar. Bu, sorgu sonuçlarınızı bir gözden geçirme kümesinde iyileştirmenize yardımcı olur.

**[Dosya meta verilerinde](view-documents-in-review-set.md#file-metadata) algılanan dilleri görebilir miyim?**

Hayır, dosya meta verilerinde algılanan dilleri göremezsiniz.

**Gözden geçirme kümesindeki belge dillerine göre filtreleyebilir miyim**?

Hayır, bir gözden geçirme kümesindeki belge dillerine göre filtreleyemez, sıralayamaz veya arama yapamazsınız.

**Gözden geçirme kümesi senaryoları için bu CJK sürümü var olan aramalarımı ve gözden geçirme kümelerimden herhangi birini etkiler mi?**

Hayır, mevcut aramalarınızın ve gözden geçirme kümelerinizin hiçbiri değişmez. Mevcut verileri yeniden dizine almanız gerekmez ve İngilizce metin arama sonuçları aynı olacaktır.

**Görüntüleme dilimi Çince, Japonca veya Korece olarak değiştirmek Nasıl yaparım??**

Görüntüleme dilini ve saat dilimini değiştirme hakkında bilgi için bkz. [Office 365 için dil ve bölge ayarlarını ayarlama](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Bilinen sorunlar

- OCR, görüntü dosyalarındaki CJK karakterlerini desteklemez

- [Not Ekleme görünümündeki](view-documents-in-review-set.md#annotate-view) e-posta dosyaları (*.eml ve *.msg gibi) CJK dillerinde desteklenmez.

- [Metin görünümünde](view-documents-in-review-set.md#text-view) arama isabeti vurgulama CJK dillerinde desteklenmez.

- Verileri çözümlemek için kullanılan [İlgi modülü](using-relevance.md) CJK dillerini desteklemez.

- CJK dillerinde [sorgu tabanlı ayrı tutmalar](managing-holds.md#manage-non-custodial-holds) desteklenmez.