---
title: Custo custing advanced indexing
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
description: Bir özel durum durumuna bir custo Advanced eDiscovery, kısmen dizine alındı olarak kabul edilmiş olan tüm içerikler, tümüyle aranabilir hale olmak için yeniden işlenmiştir.
ms.openlocfilehash: 1c43f55f399f69d58e05c073e688170d53480b42
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "62997101"
---
# <a name="advanced-indexing-of-custodian-data"></a>Custo custing advanced indexing

Bir özel durumla ilgili bir Advanced eDiscovery ekli olduğunda, kısmen dizine alındı olarak kabulilen veya dizin oluşturma hataları olan tüm içerik yeniden dizine eklenir. Bu yeniden dizin oluşturma işlemi, Gelişmiş *dizin oluşturma olarak adlandırılan işlemdir*. İçeriğin kısmen dizine alındı veya dizin oluşturma hataları olan birçok nedeni vardır. Bunlar resim dosyalarını veya bir dosyada görüntülerin varlığını, desteklenmeyen dosya türlerini veya dosya boyutu dizin oluşturma sınırlarını içerir. Daha SharePoint için, Gelişmiş dizin oluşturma yalnızca kısmen dizine alındı olarak işaretlenmiş veya dizin hataları olan öğelerde çalışır. Resim Exchange e-posta iletileri kısmen dizine alınmış olarak veya dizin oluşturma hatalarında işaretlanmaz. Bu, bu dosyaların Gelişmiş dizin oluşturma işlemiyle yeniden dizinei oluşturmaymayacakları anlamına gelir.

Desteği işleme ve kısmen dizine alan öğeler hakkında daha fazla bilgi için bkz:

- [Dosyalarda desteklenen dosya Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [eBulma'da kısmen dizine alan öğeler](partially-indexed-items-in-content-search.md)

- [Arama tarafından dizine alan Exchange biçimleri](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [SharePoint Server'da varsayılan gezinilen dosya adı uzantıları ve ayrıştırıldı dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Gelişmiş dizin oluşturma sonuçlarını görüntüleme

Gelişmiş dizin oluşturma işlemi tamamlandıktan sonra, yeniden işlemenin ne kadar etkili olduğunu anlamış oluruz.  Bir vakanın İşleme sekmesindeki Gelişmiş dizin oluşturma  sonuçları görünümünde, grafikte karma dizine eklenen öğe *sayısı listelenmiştir*.  Karma dizin, Advanced eDiscovery içeriği depolar.

Bu görünüm, düzeltme gerektiren öğelerin sayısını ve dosya türüne göre başka bir hata grafiği de içerir. Daha fazla bilgi için bkz.:

- [Veri işleme hatası düzeltmesi](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Tek öğe hatası düzeltmesi](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Koruyucular için Gelişmiş dizini güncelleştirme

Bir özel durum durumuna bir custo Advanced eDiscovery, kısmen dizine eklenen tüm öğeler yeniden işlenmiştir. Bununla birlikte, zaman geçtikten sonra kısmen dizine alınan öğeler kullanıcının posta kutusuna veya posta kutusuna OneDrive.  Gerekirse, belirli custogüncelleştirmeyi için dizini güncelleştirin. Daha fazla bilgi için bkz[. Bir vakada koruyucuları Advanced eDiscovery yönetme](manage-new-custodians.md#reindex-custodian-data). Ayrıca, işleme sekmesindeki Güncelleştir dizinine tıklayarak bir durumda tüm **koruyucular için dizini** **güncelleştirebilirsiniz** .

> [!NOTE]
> Custo indexes'i güncelleştirmek uzun süre çalışan bir işlemdir. Bir durumda dizinleri günde birden çok kez güncelleştirmediğiniz önerilir.
