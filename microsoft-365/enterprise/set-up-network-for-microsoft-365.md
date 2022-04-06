---
title: Ağın daha iyi bir şekilde Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ağ bağlantısına genel bakış ve uç nokta listesi de içinde olmak üzere, daha fazla bilgi Microsoft 365 makalelerinin bağlantılarını bulun.
ms.openlocfilehash: c6dbc4362648b3695c23f363c0e6925ead97bacb
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680852"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Ağın daha iyi bir şekilde Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Kullanıcı ekleme çalışmanıza Microsoft 365, ağ ve İnternet bağlantılarının en iyi duruma getirilmiş erişim için ayarlanmış olduğundan emin olmaktır. Genel olarak dağıtılmış Hizmet Olarak Yazılım (SaaS) buluta erişmek için şirket içi ağın yapılandırılması, şirket içi veri merkezlerine trafiğin en iyi duruma getirilmiş geleneksel ağdan ve merkezi bir İnternet bağlantısından farklıdır. 

Bu makaleler, önemli farklılıkları anlamak ve şirket içi kullanıcılarınız için en iyi performansı elde etmek üzere uç cihazlarınızı, istemci bilgisayarlarınızı ve şirket içi ağlarınızı değiştirmek için kullanın.

## <a name="how-microsoft-365-networking-works"></a>Ağ Microsoft 365 nasıl çalışır?

E-Microsoft 365 bağlantısına genel bakış için şu Microsoft 365:

- [Microsoft 365 ağı bağlantısına genel bakış](microsoft-365-networking-overview.md)
- [Microsoft 365 bağlantısı ilkeleri](microsoft-365-network-connectivity-principles.md)
- [Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

Performansı geliştirme hakkında daha fazla bilgi için bkz. Daha [iyi performans için ağ planlaması ve Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Ağ Microsoft 365 satıcısı olarak destek ağı

Bir ağ donanımı satıcısı iyebilirsiniz ve bu [satıcıya Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md). Ürün ve çözümlerinize ağ bağlantısı Office 365 ilkeleri oluşturmak için programa kaydolabilirsiniz. 

## <a name="office-365-endpoints"></a>Office 365 uç noktalarını yapılandırma

Uç noktalar, İnternet'te trafiğin hedef IP adresleri, DNS etki alanı adları Office 365 URL'leridir. 

Bulut tabanlı hizmetlerde Office 365 en iyi duruma getirmek için, bazı uç noktaların istemci tarayıcıları ve uç ağınız tarafından özel olarak işlenmesi gerekir. Bu cihazlar güvenlik duvarları, SSL Kesme ve Denetleme ve paket denetleme cihazlarını ve veri kaybı önleme sistemlerini içerir.

Ayrıntılar [için Office 365 uç noktalarını](managing-office-365-endpoints.md) yönetme'ye bakın.

Şu anda beş farklı bulut Office 365 vardır. Bu tablo, sizi her birinin uç noktaları listesine alır.

|  Uç Noktaları | Açıklama |
|:-------|:-----|
| [Dünya çapında uç noktalar](urls-and-ip-address-ranges.md) | Abd Kullanıcılarını (Office 365 abonelikleri) içeren dünya çapında Government Community Cloud uç GCC. |
| [ABD Government DoD uç noktaları](microsoft-365-u-s-government-dod-endpoints.md) | Amerika Birleşik Devletleri Savunma Bölümü (DoD) aboneliklerinin uç noktaları. |
| [ABD Government GCC High uç noktaları](microsoft-365-u-s-government-gcc-high-endpoints.md) | Amerika Birleşik Devletleri'nin uç Government Community Cloud Yüksek (GCC) abonelikleridir. |
| [Office 365 21Vianet tarafından işletilen uç noktalar](urls-and-ip-address-ranges-21vianet.md) | 21Vianet Office 365 tarafından çalıştırılan ve Çin'deki veri güvenliğiyle ilgili ihtiyaçları karşılamak üzere Office 365 uç noktaları. |
|||

Bulut bağlantınız için en son uç nokta listesini Office 365 için bkz. Office 365 [IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md).

Ek uç noktalar için şu makalelere bakın:

- [Web hizmetine dahil edilen diğer uç noktalar](additional-office365-ip-addresses-and-urls.md)
- [Ağ istekleri Office Mac 2016](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Ağ oluşturma için Microsoft 365 konular

Ağ oluşturma konusunda özelleştirilmiş konular için şu Microsoft 365 bakın:

- [İçerik teslim ağları](content-delivery-networks.md)
- [Office 365 hizmetlerde IPv6 desteği](ipv6-support.md)
- [Nat desteği ve Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute'un Microsoft 365

Hızlı trafik için ExpressRoute'un kullanımı hakkında bilgi Office 365 bakın:

- [Office 365 için Azure ExpressRoute](azure-expressroute.md)
- [Proje için ExpressRoute'u Office 365](implementing-expressroute.md)
- [ExpressRoute ile ağ planlama Office 365](network-planning-with-expressroute.md)
- [Posta için ExpressRoute ile yönlendirme Office 365](routing-with-expressroute.md)
