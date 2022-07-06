---
title: Koruyucu verilerinin gelişmiş dizini oluşturma
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
description: eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizinlenmiş olarak kabul edilen tüm içerikler tamamen aranabilir hale getirmek için yeniden işlenmiştir.
ms.openlocfilehash: 0d0474306415a59615960cc15580af0f67dc49aa
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629563"
---
# <a name="advanced-indexing-of-custodian-data"></a>Koruyucu verilerinin gelişmiş dizini oluşturma

eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizinlenmiş olarak kabul edilen veya dizin oluşturma hataları olan tüm içerikler yeniden dizine alınır. Bu yeniden dizinleme işlemi *Gelişmiş dizin oluşturma* olarak adlandırılır. İçeriğin kısmen dizine eklendiğinin veya dizin oluşturma hatalarının olmasının birçok nedeni vardır. Bu, görüntü dosyalarını veya bir dosyadaki görüntülerin varlığını, desteklenmeyen dosya türlerini veya dosya boyutundaki dizin sınırlarını içerir. SharePoint dosyaları için, Yalnızca gelişmiş dizin oluşturma çalıştırmaları kısmen dizinlenmiş olarak işaretlenir veya dizin oluşturma hataları vardır. Exchange'de, görüntü ekleri olan e-posta iletileri kısmen dizine alınmamış veya dizin oluşturma hataları ile işaretlenmez. Bu, bu dosyaların Gelişmiş dizin oluşturma işlemi tarafından yeniden dizinlenmeyecekleri anlamına gelir.

Desteği işleme ve kısmen dizine alınan öğeler hakkında daha fazla bilgi edinmek için bkz:

- [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md)

- [eBulma'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md)

- [Exchange Search tarafından dizine alınan dosya biçimleri](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [SharePoint Server'da varsayılan gezinilen dosya adı uzantıları ve ayrıştırılmış dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Gelişmiş dizin oluşturma sonuçlarını görüntüleme

Gelişmiş dizin oluşturma işlemi tamamlandıktan sonra yeniden işlemenin etkinliğini anlayabilirsiniz.  Bir servis talebi için **İşleme** sekmesindeki Gelişmiş dizin oluşturma sonuçları görünümünde, grafik *karma dizine* eklenen öğe sayısını listeler.  Karma dizin, eBulma'nın (Premium) yeniden işlenmiş içeriği depoladığı yerdir.

Bu görünüm, düzeltme gerektiren öğe sayısını ve dosya türüne göre başka bir hata grafiğini de içerir. Daha fazla bilgi için bkz.:

- [Verileri işlerken hata düzeltme](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Tek öğede hata düzeltme](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Koruyucular için Gelişmiş dizini güncelleştirme

eBulma (Premium) olayına bir koruyucu eklendiğinde, kısmen dizine alınan tüm öğeler yeniden işlenir. Ancak, zaman geçtikçe, kullanıcının posta kutusuna veya OneDrive hesabına daha kısmen dizinlenmiş öğeler eklenebilir.  Gerekirse, belirli bir koruyucu için dizini güncelleştirebilirsiniz. Daha fazla bilgi için bkz. [eBulma (Premium) durumunda koruyucuları yönetme](manage-new-custodians.md#reindex-custodian-data). Ayrıca **, İşleme** sekmesindeki **Dizini güncelleştir'e** tıklayarak bir durumda tüm koruyucular için dizini güncelleştirebilirsiniz.

> [!NOTE]
> Koruyucu dizinlerin güncelleştirilmesi uzun süren bir işlemdir. Bir durumda dizinleri günde birden fazla kez güncelleştirmeniz önerilir.
