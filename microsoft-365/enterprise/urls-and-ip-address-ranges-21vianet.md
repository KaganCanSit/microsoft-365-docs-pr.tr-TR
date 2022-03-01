---
title: 21Vianet tarafından işletilen Office 365 için URL'ler ve IP adresi aralıkları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: Bu makalede, Çin'de 21Vianet tarafından Office 365 verilerle ilgili URL'ler ve IP adresi aralıkları listelanmıştır.
hideEdit: true
ms.openlocfilehash: 8250fcddbc9b23317a0a3760b59c5f7776b98378
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2022
ms.locfileid: "63010110"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>21Vianet tarafından işletilen Office 365 için URL'ler ve IP adresi aralıkları

 *Geçerlidir: Office 365 21Vianet tarafından işletilen yöneticiler - Küçük İşletme Yöneticisi, 21Vianet tarafından Office 365 - Yönetici*

**Özet**: Aşağıdaki uç noktalar (FQDN'ler, bağlantı noktaları, URL'ler, IPv4 ve IPv6 ön ekleri) 21 Vianet tarafından işletilen Office 365 için geçerlidir ve yalnızca bu planları kullanan kuruluşlara üretkenlik hizmetleri sunmak üzere tasarlanmıştır.
  
 **Office 365** uç noktaları: *21 Vianet* |  tarafından işletilen Office 365 ([GCC dahil)](urls-and-ip-address-ranges.md)  | Office 365 ABD Government [DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 ABD Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Son güncelleştirme:** 28/09/2021 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Günlük aboneliğini değiştir](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**İndirin:** Tüm gerekli ve isteğe bağlı hedefler bir [JSON biçimlendirilmiş](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) listesindedir.

Bu verileri [kullanarak ağ Office 365 yönetme](managing-office-365-endpoints.md) önerilerimizi anlamak için Uç noktaları yönetme ile başlayabilirsiniz. Her ayın başlangıcında, etkin olmaya 30 gün önceden yayımlanan yeni IP Adresleri ve URL'ler ile uç nokta verileri gerektiğinde güncelleştirilir. Bu, yeni bağlantı gerekmeden önce henüz otomatik güncelleştirmeleri olan müşterilerin işlemlerini tamamlamalarına olanak sağlar. Ayrıca, ay içinde yükseltmeleri, güvenlik olaylarını veya diğer acil işlem gereksinimlerini desteklemek için uç noktalar da güncelleştirilebilir. Aşağıdaki bu sayfada gösterilen verilerin hepsi REST tabanlı web hizmetlerinden oluşturulur. Bu verilere erişmek için komut dosyası veya ağ cihazı kullanıyorsanız, doğrudan [Web hizmetine gitebilirsiniz](microsoft-365-ip-web-service.md) .

Aşağıdaki uç nokta verilerinde, kullanıcının makinesiyle Posta'ya bağlantı Office 365. Microsoft'tan müşteri ağına yapılan ağ bağlantıları (bazen karma veya gelen ağ bağlantıları olarak da adlandırılan) dahil değildir.

Uç noktalar dört hizmet alanı olarak gruplandı. Bağlantı için ilk üç hizmet alanı bağımsız olarak seçilebilir. Dördüncü hizmet alanı yaygın bir bağımlılıktır (ortak ve ortak Microsoft 365 adı Office) ve her zaman ağ bağlantısına sahip olması gerekir.

Gösterilen veri sütunları:

- **Kimlik**: Uç nokta kümesi olarak da bilinen satırın kimlik numarası. Bu kimlik, uç nokta kümesi için web hizmetinin döndürülen kimliğiyle aynıdır.

- **Kategori**: Uç nokta kümesine "En İyi Duruma Getirme", "İzin Ver" veya "Varsayılan" olarak kategorilere ayrılmış olup olmadığını gösterir. Bu kategoriler ve bunların yönetimiyle ilgili rehberlik makalesinde okuyabilirsiniz [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Bu sütun, ağ bağlantısının olması için gereken uç nokta kümelerini de listeler. Ağ bağlantısı olması gerekmayacak uç nokta kümelerini, uç nokta kümesi engellenirse hangi işlevlerin eksik olacağını göstermek için bu alanda notlar sağlaruz. Tüm hizmet alanı dışında bırakıyorsanız, gerekli olarak listelenen uç nokta kümeleri bağlantı gerektirmez.

- **HATA**: Uç nokta **kümesi,** yönlendirme önekleriyle birlikte Azure ExpressRoute üzerinden destek Office 365 olur. Gösterilen yol ön eklerini içeren BGP topluluğu, listelenen hizmet alanıyla hizalanır. HATAY olduğunda **,** bu ExpressRoute'un bu uç nokta kümesi için desteklen destekleme desteklemesi anlamına gelir. Bununla birlikte, HATAYİS'in Hayır olduğu bir uç nokta kümesi için hiçbir yönlendirmenin tanıtılma olduğu **varsayma gerekir**.

- **Adresler**: Uç nokta kümesi için FQDN'leri veya joker karakterli etki alanı adlarını ve IP Adresi aralıklarını listeler. IP Adresi aralığının CIDR biçiminde olduğunu ve belirtilen ağda birçok ayrı IP Adresi yer ağına sahip olduğunu unutmayın.
 
- **Bağlantı** noktaları: Ağ uç noktasını oluşturmak için Adresler ile birleştirilmiş TCP veya UDP bağlantı noktalarını listeler. LISTELENEN farklı bağlantı noktaları olan IP Adresi aralıklarında bazı yinelemeler olduğunu farkebilirsiniz.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]