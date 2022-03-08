---
title: Office 365 US Government DOD uç noktaları
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/28/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: Office 365, İnternet bağlantısı gerektirir. Aşağıdaki uç noktalara yalnızca ABD Government DoD planlarını Office 365 müşteriler erişilebilir.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 000ae3590b0c99b59f557e6b70deaa60649054a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325647"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 ABD Government DoD uç noktaları

*Geçerli Olduğu Yer: Office 365 Admin*

Office 365, İnternet bağlantısı gerektirir. Aşağıdaki uç noktalara yalnızca ABD Government DoD planlarını Office 365 müşteriler erişilebilir.
  
**Office 365 uç noktaları:** [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| Office 365 tarafından işletilen dünya çapında [(GCC dahil)](urls-and-ip-address-ranges.md) \| *Office 365 ABD Government DoD* \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)

<br>

****

|Notlar|İndir|
|---|---|
|**Son güncelleştirme:** 28/02/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Günlük aboneliğini değiştir](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**İndir:** [JSON biçiminde tam liste](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

Bu verileri [kullanarak ağ Office 365 yönetme](managing-office-365-endpoints.md) önerilerimizi anlamak için Uç noktaları yönetme ile başlayabilirsiniz. Her ayın başlangıcında, etkin olmaya 30 gün önceden yayımlanan yeni IP Adresleri ve URL'ler ile uç nokta verileri gerektiğinde güncelleştirilir. Bu özellik, yeni bağlantı gerekmeden önce henüz otomatik güncelleştirmeleri olan müşterilerin işlemlerini tamamlamalarına olanak sağlar. Ayrıca, ay içinde yükseltmeleri, güvenlik olaylarını veya diğer acil işlem gereksinimlerini desteklemek için uç noktalar da güncelleştirilebilir. Aşağıdaki bu sayfada gösterilen verilerin hepsi REST tabanlı web hizmetlerinden oluşturulur. Bu verilere erişmek için komut dosyası veya ağ cihazı kullanıyorsanız, doğrudan [Web hizmetine gitebilirsiniz](microsoft-365-ip-web-service.md) .

Aşağıdaki uç nokta verilerinde, kullanıcının makinesiyle Posta'ya bağlantı Office 365. Microsoft'tan müşteri ağına yapılan ağ bağlantıları (bazen karma veya gelen ağ bağlantıları olarak da adlandırılan) dahil değildir. Daha fazla bilgi için bkz [. Web hizmetine dahil değildir ek uç noktalar](additional-office365-ip-addresses-and-urls.md).

Uç noktalar dört hizmet alanı olarak gruplandı. Bağlantı için ilk üç hizmet alanı bağımsız olarak seçilebilir. Dördüncü hizmet alanı yaygın bir bağımlılıktır (ortak ve ortak Microsoft 365 adı Office) ve her zaman ağ bağlantısına sahip olması gerekir.

Gösterilen veri sütunları:

- **Kimlik**: Uç nokta kümesi olarak da bilinen satırın kimlik numarası. Bu kimlik, uç nokta kümesi için web hizmetinin döndürülen kimliğiyle aynıdır.

- **Kategori**: Uç nokta kümesine "En İyi Duruma Getirme", "İzin Ver" veya "Varsayılan" olarak kategorilere ayrılmış olup olmadığını gösterir. Bu kategoriler ve bunların yönetimiyle ilgili rehberlik makalesinde okuyabilirsiniz [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Bu sütun, ağ bağlantısının olması için gereken uç nokta kümelerini de listeler. Ağ bağlantısı olması gerekmayacak uç nokta kümelerini, uç nokta kümesi engellenirse hangi işlevlerin eksik olacağını göstermek için bu alanda notlar sağlaruz. Tüm hizmet alanı dışında bırakıyorsanız, gerekli olarak listelenen uç nokta kümeleri bağlantı gerektirmez.

- **HATA**: Uç nokta **kümesi,** yönlendirme önekleriyle birlikte Azure ExpressRoute üzerinden destek Office 365 olur. Gösterilen yol ön eklerini içeren BGP topluluğu, listelenen hizmet alanıyla hizalanır. HATAY olduğunda **,** bu ExpressRoute'un bu uç nokta kümesi için desteklen destekleme desteklemesi anlamına gelir. Bununla birlikte, HATAYİS'in Hayır olduğu bir uç nokta kümesi için hiçbir yönlendirmenin tanıtılma olduğu **varsayma gerekir**. Azure AD Ad Bağlan'i kullanmayı planlıyorsanız, uygun Azure AD ad [](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) e-Bağlan emin olmak için dikkat edilmesi gerekenler bölümünü okuyun.

- **Adresler**: Uç nokta kümesi için FQDN'leri veya joker karakterli etki alanı adlarını ve IP Adresi aralıklarını listeler. IP Adresi aralığının CIDR biçiminde olduğunu ve belirtilen ağda birçok ayrı IP Adresi yer ağına sahip olduğunu unutmayın.

- **Bağlantı** noktaları: Ağ uç noktasını oluşturmak için Adresler ile birleştirilmiş TCP veya UDP bağlantı noktalarını listeler. LISTELENEN farklı bağlantı noktaları olan IP Adresi aralıklarında bazı yinelemeler olduğunu farkebilirsiniz.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Bu tabloya notlar:

- Güvenlik ve Uyumluluk Merkezi (SCC), güvenlik ve uyumluluk nedeniyle Azure ExpressRoute'Office 365. Raporlama, Denetim, Genel Denetim, Birleşik DLP ve Veri Yönetimi gibi SCC aracılığıyla ortaya Advanced eDiscovery birçok özellik için de aynı durum geçerlidir. İki özellik (PST İçeri Aktarma ve eBulma Dışarı Aktarma) şu anda Azure Blob verilerine bağımlılıkları nedeniyle Office 365 yol filtreleriyle Azure ExpressRoute'u Depolama. Bu özellikleri kullanmak için Azure Blob bağlantı Depolama İnternet bağlantısı veya Azure Genel rota filtreleriyle Azure ExpressRoute gibi Azure bağlantı seçeneklerini kullanarak ayrı bir bağlantınız olur. Bu özelliklerin her ikisi için de böyle bir bağlantı kurmayı değerlendirmelisiniz. Office 365 Information Protection ekibi bu sınırlamanın farkındadır ve her iki özellik için de rota filtreleriyle sınırlı olarak Office 365 Office 365 için Azure ExpressRoute desteği sağlamak üzere etkin bir şekilde çalışıyor.

- Listelenmiyor olan ve kullanıcıların Kurumlar için Microsoft 365 Uygulamaları uygulamaları başlatması ve belgeleri düzenlemesi için gerekli Kurumlar için Microsoft 365 Uygulamaları isteğe bağlı başka uç noktalar da vardır. İsteğe bağlı uç noktalar Microsoft veri merkezlerinde barındırıldı ve müşteri verilerini işlemez, iletmez veya depolamaz. Bu uç noktalara yönelik kullanıcı bağlantılarının varsayılan İnternet çıkış çevresine yönlendirileceklerini öneririz.
