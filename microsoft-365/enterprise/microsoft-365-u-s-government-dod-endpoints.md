---
title: US Government DOD uç noktalarını Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Office 365, İnternet bağlantısı gerektirir. Aşağıdaki uç noktalara yalnızca OFFICE 365 ABD Kamu DoD planlarını kullanan müşteriler erişebilir.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7c387e66d53c5e5df88e8779ea7f7d74c8d639ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090263"
---
# <a name="office-365-us-government-dod-endpoints"></a>ABD Kamu DoD uç noktalarını Office 365

*Şunun için geçerlidir: Office 365 Admin*

Office 365, İnternet bağlantısı gerektirir. Aşağıdaki uç noktalara yalnızca OFFICE 365 ABD Kamu DoD planlarını kullanan müşteriler erişebilir.
  
**Office 365 uç noktaları:** [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| Office 365 *ABD Kamu DoD* \| Office 365 ABD Kamu GCC High tarafından sağlanan dünya çapında [(GCC](microsoft-365-u-s-government-gcc-high-endpoints.md) [dahil)](urls-and-ip-address-ranges.md) \| Office 365

<br>

****

|Notlar|İndir|
|---|---|
|**Son güncelleştirme:** 28/02/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Günlük aboneliğini değiştir](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**İndir:** [JSON biçimindeki](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) tam liste|
|

Bu verileri kullanarak ağ bağlantısını yönetmeye yönelik önerilerimizi anlamak için [Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md) ile başlayın. Uç nokta verileri, etkin olmadan 30 gün önce yayınlanan yeni IP Adresleri ve URL'ler ile her ayın başında gerektiği gibi güncelleştirilir. Bu, henüz otomatik güncelleştirmeleri olmayan müşterilerin yeni bağlantı gerekmeden önce işlemlerini tamamlamalarına olanak tanır. Destek artışlarını, güvenlik olaylarını veya diğer acil operasyonel gereksinimleri ele almak için gerekirse uç noktalar da ay boyunca güncelleştirilebilir. Aşağıdaki bu sayfada gösterilen verilerin tümü REST tabanlı web hizmetlerinden oluşturulmuştur. Bu verilere erişmek için bir betik veya bir ağ cihazı kullanıyorsanız, doğrudan [Web hizmetine](microsoft-365-ip-web-service.md) gitmelisiniz.

Aşağıdaki uç nokta verileri, bir kullanıcının makinesinden Office 365'e bağlantı için gereksinimleri listeler. Microsoft'tan bir müşteri ağına giden ve bazen karma veya gelen ağ bağlantıları olarak adlandırılan ağ bağlantılarını içermez. Daha fazla bilgi için bkz. [Web hizmetine dahil olmayan ek uç noktalar](additional-office365-ip-addresses-and-urls.md).

Uç noktalar dört hizmet alanında gruplandırılır. İlk üç hizmet alanı, bağlantı için bağımsız olarak seçilebilir. Dördüncü hizmet alanı ortak bir bağımlılıktır (Ortak ve Office Microsoft 365 olarak adlandırılır) ve her zaman ağ bağlantısı olmalıdır.

Gösterilen veri sütunları şunlardır:

- **Kimlik**: Uç nokta kümesi olarak da bilinen satırın kimlik numarası. Bu kimlik, uç nokta kümesi için web hizmeti tarafından döndürülen kimlikle aynıdır.

- **Kategori**: Uç nokta kümesinin "İyileştir", "İzin Ver" veya "Varsayılan" olarak kategorize edilip edilmediğini gösterir. Bu kategoriler ve bunların yönetimine yönelik kılavuzlar hakkında bilgi edinmek için adresinden [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md)bilgi edinebilirsiniz. Bu sütun ayrıca ağ bağlantısına sahip olmak için hangi uç nokta kümelerinin gerekli olduğunu da listeler. Ağ bağlantısına sahip olması gerekmeyen uç nokta kümeleri için, uç nokta kümesi engellenirse hangi işlevlerin eksik olacağını belirtmek için bu alanda notlar sağlarız. Bir hizmet alanının tamamını hariç tutuyorsanız, gerekli olarak listelenen uç nokta kümeleri bağlantı gerektirmez.

- **HATA**: Uç nokta kümesi, Office 365 yol önekleriyle Azure ExpressRoute üzerinden destekleniyorsa bu **Evet**'tir. Gösterilen yol öneklerini içeren BGP topluluğu, listelenen hizmet alanıyla hizalanır. HATA **Hayır** olduğunda, ExpressRoute'un bu uç nokta kümesi için desteklenmediği anlamına gelir. Ancak, HATA’nın **Hayır** olduğu bir uç nokta kümesi için hiçbir yolun tanıtılmadığı varsayılmamalıdır. Azure AD Bağlan kullanmayı planlıyorsanız, uygun Azure AD Bağlan yapılandırmasına sahip olduğunuzdan emin olmak için [dikkat edilmesi gerekenler bölümünü](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) okuyun.

- **Adresler**: Uç nokta kümesi için FQDN'leri veya joker alan adlarını ve IP Adresi aralıklarını listeler. IP Adresi aralığının CIDR biçiminde olduğunu ve belirtilen ağda birçok bağımsız IP Adresi içerebileceğini unutmayın.

- **Bağlantı Noktaları**: Ağ uç noktasını oluşturmak için Adreslerle birleştirilen TCP veya UDP bağlantı noktalarını listeler. Listelenen farklı bağlantı noktalarının bulunduğu IP Adresi aralıklarında bazı yinelemeler görebilirsiniz.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Bu tablonun notları:

- Güvenlik ve Uyumluluk Merkezi (SCC), Office 365 için Azure ExpressRoute desteği sağlar. Aynı durum Raporlama, Denetim, eBulma (Premium), Birleşik DLP ve Veri İdaresi gibi SCC aracılığıyla kullanıma sunulan birçok özellik için de geçerlidir. PST İçeri Aktarma ve eBulma Dışarı Aktarma olmak üzere iki özel özellik, şu anda Azure Blob Depolama bağımlılığı nedeniyle yalnızca Office 365 yol filtreleriyle Azure ExpressRoute'u desteklemez. Bu özellikleri kullanmak için, İnternet bağlantısı veya Azure Genel yol filtreleri içeren Azure ExpressRoute dahil olmak üzere desteklenebilir Azure bağlantı seçeneklerini kullanarak Azure Blob Depolama ayrı bağlantınız olmalıdır. Bu özelliklerin her ikisi için de böyle bir bağlantı kurmayı değerlendirmeniz gerekir. Office 365 Information Protection ekibi bu sınırlamanın farkındadır ve bu özelliklerin her ikisi için Office 365 yol filtreleri ile sınırlı olarak Office 365 için Azure ExpressRoute desteği sağlamak için etkin bir şekilde çalışmaktadır.

- Kurumlar için Microsoft 365 Uygulamaları için listelenmeyen ve kullanıcıların Kurumlar için Microsoft 365 Uygulamaları uygulamaları başlatması ve belgeleri düzenlemesi için gerekli olmayan ek isteğe bağlı uç noktalar vardır. İsteğe bağlı uç noktalar Microsoft veri merkezlerinde barındırılır ve müşteri verilerini işlemez, iletmez veya depolamaz. Bu uç noktalara yönelik kullanıcı bağlantılarının varsayılan İnternet çıkış çevresine yönlendirilmesi önerilir.
