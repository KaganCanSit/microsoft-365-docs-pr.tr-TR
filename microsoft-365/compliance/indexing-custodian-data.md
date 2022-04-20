---
title: Koruyucu verilerinin gelişmiş dizini oluşturma
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
description: Bir eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizinlenmiş olarak kabul edilen tüm içerik, tamamen aranabilir hale getirmek için yeniden işlenmiştir.
ms.openlocfilehash: 3c6f0079f87dbc4711fed7d776204c287d5b5865
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64932007"
---
# <a name="advanced-indexing-of-custodian-data"></a>Koruyucu verilerinin gelişmiş dizini oluşturma

eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizinlenmiş veya dizin oluşturma hataları olduğu kabul edilen tüm içerikler yeniden dizine alınır. Bu yeniden dizinleme işlemi *Gelişmiş dizin oluşturma* olarak adlandırılır. İçeriğin kısmen dizine eklendiğinin veya dizin oluşturma hatalarının olmasının birçok nedeni vardır. Bu, görüntü dosyalarını veya bir dosyadaki görüntülerin varlığını, desteklenmeyen dosya türlerini veya dosya boyutundaki dizin sınırlarını içerir. SharePoint dosyalar için, Yalnızca gelişmiş dizin oluşturma işlemleri kısmen dizinlenmiş olarak işaretlenir veya dizin oluşturma hataları vardır. Exchange,resim ekleri olan e-posta iletileri kısmen dizine alınmaz veya dizin oluşturma hataları ile işaretlenmez. Bu, bu dosyaların Gelişmiş dizin oluşturma işlemi tarafından yeniden dizinlenmeyecekleri anlamına gelir.

Desteği işleme ve kısmen dizine alınan öğeler hakkında daha fazla bilgi edinmek için bkz:

- [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md)

- [eBulma'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md)

- [Exchange Arama tarafından dizine alınan dosya biçimleri](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [SharePoint Server'da varsayılan gezilen dosya adı uzantıları ve ayrıştırılmış dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Gelişmiş dizin oluşturma sonuçlarını görüntüleme

Gelişmiş dizin oluşturma işlemi tamamlandıktan sonra yeniden işlemenin etkinliğini anlayabilirsiniz.  Bir servis talebi için **İşleme** sekmesindeki Gelişmiş dizin oluşturma sonuçları görünümünde, grafik *karma dizine* eklenen öğe sayısını listeler.  Karma dizin, eBulma'nın (Premium) yeniden işlenen içeriği depoladığı yerdir.

Bu görünüm, düzeltme gerektiren öğe sayısını ve dosya türüne göre başka bir hata grafiğini de içerir. Daha fazla bilgi için bkz.:

- [Verileri işlerken hata düzeltme](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Tek öğede hata düzeltme](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Koruyucular için Gelişmiş dizini güncelleştirme

eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizine alınan tüm öğeler yeniden işlenir. Ancak, zaman geçtikçe, kullanıcının posta kutusuna veya OneDrive hesabına daha kısmen dizinlenmiş öğeler eklenebilir.  Gerekirse, belirli bir koruyucu için dizini güncelleştirebilirsiniz. Daha fazla bilgi için bkz. [eBulma (Premium) durumunda koruyucuları yönetme](manage-new-custodians.md#reindex-custodian-data). Ayrıca **, İşleme** sekmesindeki **Dizini güncelleştir'e** tıklayarak bir durumda tüm koruyucular için dizini güncelleştirebilirsiniz.

> [!NOTE]
> Koruyucu dizinlerin güncelleştirilmesi uzun süren bir işlemdir. Bir durumda dizinleri günde birden fazla kez güncelleştirmeniz önerilir.
