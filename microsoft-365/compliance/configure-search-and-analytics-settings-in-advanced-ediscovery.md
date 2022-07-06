---
title: Arama ve analiz ayarlarını yapılandırma - eBulma (Premium)
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
ms.assetid: ''
ms.custom: seo-marvel-mar2020
description: Bir durumda tüm inceleme kümesi için geçerli olan Microsoft Purview eKeşif (Premium) ayarlarını yapılandırın. Bu, analiz ve Optik karakter tanıma ayarlarını içerir.
ms.openlocfilehash: 315448606e99a768bacd8d7d4ac7f858c79c7bed
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624575"
---
# <a name="configure-search-and-analytics-settings-in-ediscovery-premium"></a>eBulma'da arama ve analiz ayarlarını yapılandırma (Premium)

Aşağıdaki işlevleri denetlemek için her Microsoft Purview eKeşif (Premium) olayı için ayarları yapılandırabilirsiniz.

- Yakın yinelemeler ve e-posta yazışmaları

- Temalar

- Otomatik oluşturulan gözden geçirme kümesi sorgusu

- Metni yoksay

- Optik karakter tanıma

Bir servis talebi için arama ve analiz ayarlarını yapılandırmak için:

1. **eBulma (Premium)** sayfasında servis talebini seçin.

2. **Ayarlar** sekmesindeki **Arama & analizi'nin** altında **Seç'e** tıklayın.

   Servis talebi ayarları sayfası görüntülenir. Bu ayarlar, bir durumda tüm gözden geçirme kümelerine uygulanır.

   ![eBulma (Premium) olayı için analiz ve arama ayarlarını yapılandırın.](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Yakın yinelemeler ve e-posta yazışmaları

Bu bölümde, yinelenen algılama, neredeyse yinelenen algılama ve e-posta iş parçacığı oluşturma için parametreler ayarlayabilirsiniz. Daha fazla bilgi için bkz [. Neredeyse yinelenen algılama](near-duplicate-detection-in-advanced-ediscovery.md) ve [E-posta iş parçacığı oluşturma](email-threading-in-advanced-ediscovery.md).

- **Yakın yinelemeler/e-posta yazışmaları:** Açıldığında, bir gözden geçirme kümesindeki veriler üzerinde analiz çalıştırdığınızda, yinelenen algılama, neredeyse yinelenen algılama ve e-posta iş parçacığı oluşturma iş akışının bir parçası olarak eklenir.

- **Belge ve e-posta benzerliği eşiği:** İki belge için benzerlik düzeyi eşiğin üzerindeyse, her iki belge de aynı yakın yinelenen kümeye konur.

- **En az/en fazla sözcük sayısı:** Bu ayarlar, yakın yinelemelerin ve e-posta yazışması analizinin yalnızca en az en az sözcük sayısına ve en fazla en fazla sözcük sayısına sahip belgelerde gerçekleştirileceğini belirtir.

## <a name="themes"></a>Temalar

Bu bölümde, temalar için parametreler ayarlayabilirsiniz. Daha fazla bilgi için bkz [. Temalar](themes-in-advanced-ediscovery.md).

- **Temalar:** Açık olduğunda, bir gözden geçirme kümesindeki veriler üzerinde analiz çalıştırdığınızda tema kümelemesi iş akışının bir parçası olarak gerçekleştirilir.

- **Tema sayısı üst sınırı:** Bir gözden geçirme kümesindeki veriler üzerinde analiz çalıştırdığınızda oluşturulabilecek en fazla tema sayısını belirtir.

- **Temalara sayıları dahil et:** Açıldığında, temalar oluşturulurken sayılar (bir temayı tanımlayan) eklenir. 

- **En fazla tema sayısını dinamik olarak ayarlayın:** Bazı durumlarda, bir gözden geçirme kümesinde istenen sayıda tema oluşturmak için yeterli belge olmayabilir. Bu ayar etkinleştirildiğinde, eBulma (Premium) en fazla tema sayısını zorlamak yerine en fazla tema sayısını dinamik olarak ayarlar.

## <a name="review-set-query"></a>Küme sorgusunu gözden geçirme

**Analizden sonra kaydedilen gözden geçirme için otomatik olarak oluştur** onay kutusunu seçerseniz, eBulma (Premium) gözden geçirme için adlı gözden geçirme kümesi sorgusunu otomatik olarak oluşturur **.** 

![Gözden Geçir otomatik oluşturulan sorgusu.](../media/AeDForReviewQuery.png)

Bu sorgu temelde gözden geçirme kümesindeki yinelenen öğeleri filtreler. Bu, gözden geçirme kümesindeki benzersiz öğeleri gözden geçirmenize olanak tanır. Bu sorgu yalnızca olayda bir gözden geçirme kümesi için analiz çalıştırdığınızda oluşturulur. Gözden geçirme kümesi sorguları hakkında daha fazla bilgi için bkz. [Gözden geçirme kümesindeki verileri sorgulama](review-set-search.md).

## <a name="ignore-text"></a>Metni yoksay

E-postanın içeriğinden bağımsız olarak e-posta iletilerine eklenen uzun sorumluluk reddi gibi belirli metinlerin analiz kalitesini azaltacağı durumlar vardır. Yoksayılması gereken metinleri biliyorsanız, metnin dışlanması gereken metin dizesini ve analiz işlevselliğini (yakın yinelemeler, E-posta yazışması, Temalar ve İlgi) belirterek bunu analizden dışlayabilirsiniz. Yoksayılan metin olarak normal ifadelerin (RegEx) kullanılması da desteklenir.

## <a name="optical-character-recognition-ocr"></a>Optik karakter tanıma (OCR)

Bu ayar açıldığında, OCR işlemesi görüntü dosyalarında çalıştırılır. OCR işleme aşağıdaki durumlarda çalıştırılır:

- Bir olaya koruyucular ve [gözetimsiz veri kaynakları](non-custodial-data-sources.md) eklendiğinde. Resim dosyalarına OCR uygulandığında, bu dosyalardaki metin bir koleksiyon sırasında aranabilir. [OCR işleme, Gelişmiş dizin oluşturma](indexing-custodian-data.md) işlemi sırasında gerçekleştirilir. OCR yalnızca Gelişmiş dizin oluşturma sırasında işlenen öğelerde çalıştırılır. Örneğin, kısmen dizine alınan veya başka dizin oluşturma hataları olan büyük bir PDF dosyası Gelişmiş dizin oluşturma sırasında işlenirse, dosyada da OCR uygulanır. Başka bir deyişle, OCR işleme yalnızca Gelişmiş dizin oluşturma işlemi sırasında yeniden dizine alınan dosyalarda gerçekleşir. Bu, bir servis talebine koruyucuların eklendiği ancak bazı e-posta eklerinin OCR için işlenmeyeceği durumlar olabileceği anlamına gelir çünkü bu dosyalar Gelişmiş dizin oluşturma sırasında işlenmez.

- Diğer veri kaynaklarından (bir koruyucuyla ilişkilendirilmemiş ve koruyucu olmayan bir veri kaynağında olaya eklenen) içerik bir gözden geçirme kümesine eklendiğinde.

Veriler bir gözden geçirme kümesine eklendikten sonra görüntü metni gözden geçirilebilir, aranabilir, etiketlenebilir ve analiz edilebilir. Ayıklanan metni, gözden geçirme kümesindeki seçili görüntü dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz.:

- [Koruyucu verilerinin gelişmiş dizini oluşturma](indexing-custodian-data.md)

- [Gözden geçirme kümesine arama sonuçları ekleme](add-data-to-review-set.md#optical-character-recognition)

- [Desteklenen görüntü dosyası türleri](supported-filetypes-ediscovery20.md#image)
