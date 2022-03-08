---
title: Office 365 URL’leri ve IP adresi aralıkları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 02/28/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Özet: Office 365 için İnternet bağlantısı gerekir. Aşağıdaki uç noktalara, E-posta planları (Office 365) dahil Government Community Cloud müşteriler GCC.'
hideEdit: true
ms.openlocfilehash: 21d80523fc2cdba2e6a7bb9f08909bd7d6152a4b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324736"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365 URL’leri ve IP adresi aralıkları

Office 365, İnternet bağlantısı gerektirir. Aşağıdaki uç noktalara, E-posta planları (Office 365) dahil Government Community Cloud müşteriler GCC.
  
*Office 365 Worldwide (+GCC)* \| [Office 365 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 ABD Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| [Office 365 U.S. Government GCC High tarafından işletilen GCC.](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Notlar|İndir|Kullanım|
|---|---|---|
|**Son güncelleştirme:** 28/02/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Günlük aboneliğini değiştir](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**İndirin:** Tüm gerekli ve isteğe bağlı hedefler bir [JSON biçimlendirilmiş](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) listesindedir.|**Kullan:** PAC dosyaları [proxy'miz](managing-office-365-endpoints.md#pacfiles)|
|

Bu verileri [kullanarak ağ Office 365 yönetme](managing-office-365-endpoints.md) önerilerimizi anlamak için Uç noktaları yönetme ile başlayabilirsiniz. Her ayın başlangıcında, etkin olmaya 30 gün önceden yayımlanan yeni IP Adresleri ve URL'ler ile uç nokta verileri gerektiğinde güncelleştirilir. Bu, yeni bağlantı gerekmeden önce henüz otomatik güncelleştirmeleri olan müşterilerin işlemlerini tamamlamalarına olanak sağlar. Ayrıca, ay içinde yükseltmeleri, güvenlik olaylarını veya diğer acil işlem gereksinimlerini desteklemek için uç noktalar da güncelleştirilebilir. Aşağıdaki bu sayfada gösterilen verilerin hepsi REST tabanlı web hizmetlerinden oluşturulur. Bu verilere erişmek için komut dosyası veya ağ cihazı kullanıyorsanız, doğrudan [Web hizmetine gitebilirsiniz](microsoft-365-ip-web-service.md) .

Aşağıdaki uç nokta verilerinde, kullanıcının makinesiyle Posta'ya bağlantı Office 365. Microsoft'tan bir müşteri ağına yapılan ağ bağlantıları için kullanılan IP adreslerinin ayrıntıları (bazen karma veya gelen ağ bağlantıları olarak da adlandırılan) için daha fazla bilgi için bkz. [Ek](additional-office365-ip-addresses-and-urls.md) uç noktalar.

Uç noktalar, üç birincil iş yükünü ve bir dizi ortak kaynağı temsil eden dört hizmet alanı olarak grup ayarlanır. Gruplar, trafik akışlarını belirli bir uygulamayla ilişkilendirmek için kullanılabilir; bununla birlikte, özelliklerin genellikle birden çok iş yükü genelinde uç noktaları kullandığına bağlı olarak, bu gruplar erişimi kısıtlamak için etkin bir şekilde kullanılamaz.

Gösterilen veri sütunları:

- **Kimlik**: Uç nokta kümesi olarak da bilinen satırın kimlik numarası. Bu kimlik, uç nokta kümesi için web hizmetinin döndürülen kimliğiyle aynıdır.

- **Kategori**: Uç nokta kümesine "En İyi Duruma Getirme", "İzin Ver" veya "Varsayılan" olarak kategorilere ayrılmış olup olmadığını gösterir. Bu kategorileri ve bunların yönetimiyle ilgili kılavuzu Yeni Kategori'de veya [uç nokta Office 365 okuyabilirsiniz](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Bu sütun, ağ bağlantısının olması için gereken uç nokta kümelerini de listeler. Ağ bağlantısı olması gerekmayacak uç nokta kümelerini, uç nokta kümesi engellenirse hangi işlevlerin eksik olacağını göstermek için bu alanda notlar sağlaruz. Tüm hizmet alanı dışında bırakıyorsanız, gerekli olarak listelenen uç nokta kümeleri bağlantı gerektirmez.

- **HATA**: Uç nokta **kümesi,** yönlendirme önekleriyle birlikte Azure ExpressRoute üzerinden destek Office 365 olur. Gösterilen yol ön eklerini içeren BGP topluluğu, listelenen hizmet alanıyla hizalanır. HATAY olduğunda **,** bu ExpressRoute'un bu uç nokta kümesi için desteklen destekleme desteklemesi anlamına gelir. Bununla birlikte, HATAYİS'in Hayır olduğu bir uç nokta kümesi için hiçbir yönlendirmenin tanıtılma olduğu **varsayma gerekir**.

- **Adresler**: Uç nokta kümesi için FQDN'leri veya joker karakterli etki alanı adlarını ve IP Adresi aralıklarını listeler. IP Adresi aralığının CIDR biçiminde olduğunu ve belirtilen ağda birçok ayrı IP Adresi yer ağına sahip olduğunu unutmayın.

- **Bağlantı** noktaları: Ağ uç noktasını oluşturmak için Adresler ile birleştirilmiş TCP veya UDP bağlantı noktalarını listeler. LISTELENEN farklı bağlantı noktaları olan IP Adresi aralıklarında bazı yinelemeler olduğunu farkebilirsiniz.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> IP adreslerini ve URL'Yammer hakkında öneriler için, bu blogda Yammer için sabit kodlu [IP](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) adresleri kullanılması önerilmez Yammer bakın.

## <a name="related-topics"></a>İlgili Konular

[YENI IP Adresi ve URL Web Office 365 başka uç noktalar da dahil değil](additional-office365-ip-addresses-and-urls.md)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)

[Genel Microsoft Stream uç noktaları](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Ekran Microsoft 365 izleme](./monitor-connectivity.md)

[Kök CA ve üçüncü taraf uygulama sisteminde Ara CA paketi](../compliance/encryption-office-365-certificate-chains.md)
  
[İstemci bağlantısı](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[İçerik teslim ağları](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure IP Aralıkları ve Hizmet Etiketleri – Genel Bulut](https://www.microsoft.com/download/details.aspx?id=56519)

[Microsoft Azure IP Aralıkları ve Hizmet Etiketleri – US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[Microsoft Azure IP Aralıkları ve Hizmet Etiketleri – Çin Bulutu](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Genel IP Alanı](https://www.microsoft.com/download/details.aspx?id=53602)

[Hizmet Adı ve Aktarım Protokolü Bağlantı Noktası Numarası Kayıt Defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
