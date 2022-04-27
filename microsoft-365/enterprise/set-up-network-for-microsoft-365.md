---
title: Ağınızı Microsoft 365 için ayarlama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Ağ bağlantısına genel bakış ve uç noktaların listesi de dahil olmak üzere ağınızı Microsoft 365 için ayarlamanıza yardımcı olacak bilgiler içeren makalelerin bağlantılarını bulun.
ms.openlocfilehash: 8651fa23983cddf243081248bf1e03fb067232e2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092855"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Ağınızı Microsoft 365 için ayarlama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 ekleme işleminin önemli bir parçası, ağ ve İnternet bağlantılarınızın iyileştirilmiş erişim için ayarlandığından emin olmaktır. Şirket içi ağınızı genel olarak dağıtılmış bir Hizmet Olarak Yazılım (SaaS) buluta erişecek şekilde yapılandırmak, şirket içi veri merkezlerine giden trafik ve merkezi İnternet bağlantısı için iyileştirilmiş geleneksel bir ağdan farklıdır. 

Temel farklılıkları anlamak ve şirket içi kullanıcılarınız için en iyi performansı elde etmek üzere uç cihazlarınızı, istemci bilgisayarlarınızı ve şirket içi ağınızı değiştirmek için bu makaleleri kullanın.

## <a name="how-microsoft-365-networking-works"></a>Microsoft 365 ağı nasıl çalışır?

Microsoft 365 bağlantısına genel bakış için şu makalelere bakın:

- [Microsoft 365 ağ bağlantısına genel bakış](microsoft-365-networking-overview.md)
- [Microsoft 365 ağ bağlantısı ilkeleri](microsoft-365-network-connectivity-principles.md)
- [Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

Performansı geliştirme hakkında öneriler için bkz. [Microsoft 365 için ağ planlama ve performans ayarlama](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Ağ ekipmanı satıcısı olarak ağ Microsoft 365 desteği

Ağ ekipmanı satıcısıysanız [Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md) katılın. Ürünlerinize ve çözümlerinize Office 365 ağ bağlantısı ilkeleri oluşturmak için programa kaydolın. 

## <a name="office-365-endpoints"></a>Office 365 uç noktaları

Uç noktalar, İnternet üzerindeki Office 365 trafiği için hedef IP adresleri, DNS etki alanı adları ve URL'ler kümesidir. 

Performansı bulut tabanlı hizmetler Office 365 iyileştirmek için bazı uç noktaların istemci tarayıcılarınız ve uç ağınızdaki cihazlar tarafından özel olarak işlenmesi gerekir. Bu cihazlar arasında güvenlik duvarları, SSL Kesme ve İnceleme ile paket denetleme cihazları ve veri kaybı önleme sistemleri bulunur.

Ayrıntılar için bkz[. Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md).

Şu anda beş farklı Office 365 bulut vardır. Bu tablo sizi her biri için uç nokta listesine götürür.

|  Uç Noktaları | Açıklama |
|:-------|:-----|
| [Dünya çapında uç noktalar](urls-and-ip-address-ranges.md) | Birleşik Devletler Government Community Cloud (GCC) içeren dünya çapındaki Office 365 aboneliklerinin uç noktaları. |
| [ABD Hükümeti DoD uç noktaları](microsoft-365-u-s-government-dod-endpoints.md) | Birleşik Devletler Savunma Bakanlığı (DoD) aboneliklerinin uç noktaları. |
| [ABD Hükümeti GCC High uç noktaları](microsoft-365-u-s-government-gcc-high-endpoints.md) | Birleşik Devletler Government Community Cloud High (GCC High) aboneliklerinin uç noktaları. |
| [21Vianet uç noktaları tarafından sağlanan Office 365](urls-and-ip-address-ranges-21vianet.md) | 21Vianet tarafından sağlanan ve Çin'deki Office 365 ihtiyaçlarını karşılamak için tasarlanmış Office 365 uç noktaları. |
|||

Office 365 bulutunuzun uç noktalarının en son listesini almayı otomatikleştirmek için bkz. [Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md).

Ek uç noktalar için şu makalelere bakın:

- [Web hizmetine dahil olmayan ek uç noktalar](additional-office365-ip-addresses-and-urls.md)
- [Office Mac 2016'da ağ istekleri](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Microsoft 365 ağı için ek konular

Microsoft 365 ağındaki özel konular için şu makalelere bakın:

- [İçerik teslim ağları](content-delivery-networks.md)
- [Office 365 hizmetlerinde IPv6 desteği](ipv6-support.md)
- [Office 365 ile NAT desteği](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>Microsoft 365 için ExpressRoute

Office 365 trafik için ExpressRoute kullanımı hakkında bilgi için şu makalelere bakın:

- [Office 365 için Azure ExpressRoute](azure-expressroute.md)
- [Office 365 için ExpressRoute Uygulama](implementing-expressroute.md)
- [Office 365 için ExpressRoute ile Ağ planlaması](network-planning-with-expressroute.md)
- [Office 365 için ExpressRoute ile Yönlendirme](routing-with-expressroute.md)
