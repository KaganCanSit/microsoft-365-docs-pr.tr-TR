---
title: Arama ve çözümleme ayarlarını yapılandırma - Advanced eDiscovery
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
ms.custom: seo-marvel-mar2020
description: Bir Advanced eDiscovery gözden geçirme kümesine uygulanacak dosya ayarlarını yapılandırabilirsiniz. Buna çözümleme ayarları ve Optik karakter tanıma da dahildir.
ms.openlocfilehash: 65175950a430dd6b43cac207e16a17cf02d1bbbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983236"
---
# <a name="configure-search-and-analytics-settings-in-advanced-ediscovery"></a>E-postada arama ve çözümleme Advanced eDiscovery

Aşağıdaki işlevselliği denetlemeniz için her Advanced eDiscovery durumu için ayarları yapılandırabilirsiniz.

- Yinelenenler ve e-posta dizileri yakın

- Temalar

- Otomatik olarak yeniden yapılan gözden geçirme kümesi sorgusu

- Metni yoksayma

- Optik karakter tanıma

Bir vakanın arama ve çözümleme ayarlarını yapılandırmak için:

1. Olay **Advanced eDiscovery** vakayı seçin.

2. Giriş **sekmesindeki Ayarlar** Arama ve **çözümleme'nin & seç'e** **tıklayın**.

   Olay ayarları sayfası görüntülenir. Bu ayarlar, bir vakanın tüm gözden geçirme kümelere uygulanır.

   ![Bir olay için çözümleme ve arama Advanced eDiscovery yapılandırabilirsiniz.](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Yinelenenler ve e-posta dizileri yakın

Bu bölümde, yinelenen algılama için, yinelenen algılamaya yakın olan ve e-posta dizileri için parametreler belirtebilirsiniz. Daha fazla bilgi için bkz. [Yinelenen algılama yakınları ve](near-duplicate-detection-in-advanced-ediscovery.md) [E-posta dizileri](email-threading-in-advanced-ediscovery.md).

- **Yinelenenler/e-posta dizileri yakınına:** Açık olduğunda, yinelenen algılama, yinelenen algılama'nın yakınında ve e-posta iş parçacığı, gözden geçirme kümesinde veriler üzerinde çözümlemeler çalıştırarak iş akışının bir parçası olarak dahil edilir.

- **Belge ve e-posta benzerlik eşiği:** İki belge için benzerlik düzeyi eşiğin üzerinde olursa, her iki belge de neredeyse aynı yinelenen kümeye konz.

- **En az/en fazla sözcük sayısı:** Bu ayarlar, yakın yinelemelerin ve e-posta dizilerinin çözümlemesi için yalnızca en az sözcük sayısı ve en fazla sözcük sayısı en fazla olan belgelerde gerçekleştirilecek.

## <a name="themes"></a>Temalar

Bu bölümde temalar için parametreler belirtebilirsiniz. Daha fazla bilgi için bkz. [Temalar](themes-in-advanced-ediscovery.md).

- **Temalar:** Açık olduğunda, gözden geçirme kümesinde veriler üzerinde çözümlemeler çalıştırsanız, temalar kümelemesi iş akışının bir parçası olarak gerçekleştirilir.

- **En fazla tema sayısı:** Gözden geçirme kümesinde veriler üzerinde çözümlemeler çalıştırarak oluşturulacak en fazla tema sayısını belirtir.

- **Temalara numara eklemek için:** Açık olduğunda, temaları oluşturmak için sayılar (temayı tanımlayabilir) dahil edilir. 

- **Maksimum tema sayısını dinamik olarak ayarlayın:** Bazı durumlarda, istenen tema sayısını üretecek şekilde bir gözden geçirme kümesinde yeterli belge olmuyor olabilir. Bu ayar etkinleştirildiğinde, Advanced eDiscovery tema sayısını zorunlu olmayı denemeden, en fazla tema sayısını dinamik olarak ayarlar.

## <a name="review-set-query"></a>Küme sorgusunu gözden geçirme

Çözümlemeden sonra kaydedilmiş **Gözden Geçirme için otomatik olarak arama** oluştur onay kutusunu Advanced eDiscovery Gözden Geçirme için adlı gözden geçirme kümesi sorgusunu **otomatik olarak oluşturur.** 

![Otomatik olarak yeniden yapılan Gözden Geçirme sorgusu.](../media/AeDForReviewQuery.png)

Bu sorgu, temel olarak yinelenen öğeleri gözden geçirme kümesinden filtreler. Bu, gözden geçirme kümesinde benzersiz öğeleri gözden geçirmenizi sağlar. Bu sorgu ancak durum içinde bir gözden geçirme kümesi için çözümlemeler çalıştırabilirsiniz. Daha fazla bilgi için, gözden geçirme kümesi sorguları hakkında bilgi [için bkz. Gözden geçirme kümesinde verileri sorgulama](review-set-search.md).

## <a name="ignore-text"></a>Metni yoksayma

Bazı durumlarda, e-posta içeriği ne olursa olsun e-posta iletilerine eklenen uzun sorumluluk reddi gibi belirli metinlerin çözümleme kalitesini azalacak durumlar vardır. Yoksayılacak metinleri biliyorsanız, metnin hariç tutulacak metin dizesini ve çözümleme işlevselliğini (Yakın yinelemeler, E-posta dizileri, Temalar ve İlgi Düzeyi) belirterek, bu metni çözümlemelerin dışında tutabilirsiniz. Normal ifadelerin (RegEx) yoksayılan metin olarak kullanımı da de desteklenen bir metindir.

## <a name="optical-character-recognition-ocr"></a>Optik karakter tanıma (OCR)

Bu ayar açık olduğunda, resim dosyalarında OCR işlemi çalıştıracağız. OCR işleme aşağıdaki durumlarda çalıştırın:

- Bir vakaya [koruyucular ve özel olmayan](non-custodial-data-sources.md) veri kaynakları ekleniyorken. Resim dosyalarına OCR uygulandığında, bu dosyalarda bulunan metinler koleksiyon sırasında aranabilir. OCR işlemi, Gelişmiş dizin [oluşturma işlemi sırasında](indexing-custodian-data.md) gerçekleştirilir. OCR yalnızca Gelişmiş dizin oluşturma sırasında işlenen öğelerde çalıştırabilirsiniz. Örneğin, kısmen dizine alınan veya başka dizin oluşturma hataları olan büyük bir PDF dosyası Gelişmiş dizin oluşturma sırasında işleniyorsa, bu dosyaya OCR de uygulanır. Başka bir deyişle, OCR işleme yalnızca Gelişmiş dizin oluşturma işlemi sırasında yeniden dizine alınan dosyalarda gerçekleşir. Bu durum, bir vakaya koruyucuların ekli olduğu durumlar olabilir, ancak bazı e-posta ekleri OCR için işlenmez çünkü bu dosyalar Gelişmiş dizin oluşturma sırasında işlenmez.

- Başka veri kaynaklarından gelen içerik (koruyucuyla ilişkili olmayan ve özel olmayan bir veri kaynağında bu vakaya ekli olmayan) gözden geçirme kümesine ekleniyor.

Gözden geçirme kümesine veri eklendikten sonra resim metni gözden geçirebilirsiniz, aranır, etiketlenir ve çözümlenir. Ayıklanan metni gözden geçirme kümesinde, seçili resim dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz.:

- [Custo custing advanced indexing](indexing-custodian-data.md)

- [Gözden geçirme kümesine arama sonuçları ekleme](add-data-to-review-set.md#optical-character-recognition)

- [Desteklenen resim dosyası türleri](supported-filetypes-ediscovery20.md#image)
