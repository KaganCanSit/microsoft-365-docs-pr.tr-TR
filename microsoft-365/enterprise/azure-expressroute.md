---
title: Office 365 için Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Azure ExpressRoute'u Office 365 ile nasıl kullanacağınızı ve onunla dağıtım yaptığınız ağ uygulama projesini nasıl planlayacağınızı öğrenin.
ms.openlocfilehash: 1350bf73fdddd2141a2df1cbcec5edebeacf7ad4
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754300"
---
# <a name="azure-expressroute-for-office-365"></a>Office 365 için Azure ExpressRoute

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Azure ExpressRoute'un Office 365 ile nasıl kullanıldığını ve Office 365 ile kullanmak üzere Azure ExpressRoute'u dağıtıyorsanız gerekli olacak ağ uygulama projesini planlamayı öğrenin. Azure'da çalışan altyapı ve platform hizmetleri genellikle ağ mimarisini ve performansla ilgili dikkate alınacak noktaları ele alarak avantaj sağlar. Bu durumlarda Azure için ExpressRoute'u öneririz. Office 365 ve Dynamics 365 gibi Hizmet Olarak Yazılım teklifleri, İnternet üzerinden güvenli ve güvenilir bir şekilde erişilecek şekilde oluşturulmuş. İnternet performansı ve güvenliği ve Office 365 için Azure ExpressRoute'u ne zaman düşünebileceğinizi öğrenmek için [Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md) makalesini okuyabilirsiniz.

> [!NOTE]
> Uç Nokta için Microsoft Defender, Azure ExpressRoute ile tümleştirme sağlamaz. Bu, müşterilerin özel bir ağdan Uç Nokta için Microsoft Defender bulut hizmetlerine bağlantıyı sağlayan ExpressRoute kuralları tanımlamasını engellemese de, hizmet veya bulut altyapısı geliştikçe kuralların korunması müşteriye aittir.

> [!NOTE]
> Çoğu durumda hizmet için en iyi bağlantı modelini sağlamadığından Microsoft 365 için ExpressRoute'u önermeyiz. Bu nedenle, Microsoft 365 için bu bağlantı modelini kullanmak için Microsoft yetkilendirmesi gerekir. Tüm müşteri isteklerini gözden geçiriyor ve ExpressRoute'u yalnızca gerekli olduğu nadir senaryolarda Microsoft 365 için yetkilendiriyoruz. Daha fazla bilgi [için lütfen Microsoft 365 için ExpressRoute kılavuzunu](https://aka.ms/erguide) okuyun ve üretkenlik, ağ ve güvenlik ekiplerinizle belgenin kapsamlı bir incelemesini takiben, gerekirse özel durum göndermek için Microsoft hesap ekibinizle birlikte çalışın. Office 365 için yol filtreleri oluşturmaya çalışan yetkisiz abonelikler [bir hata iletisi](https://support.microsoft.com/kb/3181709) alır.

## <a name="planning-azure-expressroute-for-office-365"></a>Office 365 için Azure ExpressRoute'u planlama

İnternet bağlantısına ek olarak, Office 365 ağ trafiğinin bir alt kümesini tahmin edilebilirlik ve Microsoft ağ bileşenleri için %99,95 çalışma süresi SLA'sı sunan bir doğrudan bağlantı üzerinden yönlendirmeyi seçebilirsiniz. Azure ExpressRoute, Office 365 ve diğer Microsoft bulut hizmetlerine yönelik bu ayrılmış ağ bağlantısını sağlar.

Mevcut bir MPLS WAN'ınız olup olmamasına bakılmaksızın, ExpressRoute ağ mimarinize üç yoldan biriyle eklenebilir; desteklenen bir bulut değişimi ortak konum sağlayıcısı, bir Ethernet noktadan noktaya bağlantı sağlayıcısı veya bir MPLS bağlantı sağlayıcısı aracılığıyla. [Bölgenizde hangi sağlayıcıların kullanılabilir olduğunu](/azure/expressroute/expressroute-locations) görün. Doğrudan ExpressRoute bağlantısı, aşağıdaki [Hangi Office 365 hizmetleri dahil edilir?](azure-expressroute.md#BKMK_WhatDoIGet) bölümünde açıklanan uygulamalara bağlantı sağlar. Diğer tüm uygulama ve hizmetler için ağ trafiği İnternet'ten geçmeye devam eder.

Office 365, Windows Update ve TechNet gibi tüm Microsoft uygulamalarına erişmek için İnternet üzerinden Microsoft'un veri merkezlerine bağlanan tipik bir Office 365 müşterisini gösteren aşağıdaki üst düzey ağ diyagramını göz önünde bulundurun. Müşteriler, şirket içi ağdan mı yoksa bağımsız bir internet bağlantısından mı bağlandıklarına bakılmaksızın benzer bir ağ yolu kullanır.

![Ağ bağlantısını Office 365.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Şimdi Office 365 bağlanmak için hem İnternet'i hem de ExpressRoute'u kullanan bir Office 365 müşterisini gösteren güncelleştirilmiş diyagrama bakın. Genel DNS ve Content Delivery Network düğümleri gibi bazı bağlantıların hala genel İnternet bağlantısı gerektirdiğine dikkat edin. Ayrıca Müşterinin ExpressRoute bağlantılı binasında yer almayan kullanıcılarının İnternet üzerinden bağlandıklarına da dikkat edin.

![ExpressRoute ile bağlantıyı Office 365.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Hala daha fazla bilgi mi istiyorsunuz? [Office 365 için Azure ExpressRoute ile ağ trafiğinizi yönetmeyi ve Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) [için Azure ExpressRoute'u yapılandırmayı](/azure/expressroute/expressroute-faqs) öğrenin. Ayrıca, kavramları daha ayrıntılı bir şekilde açıklamaya yardımcı olmak için Channel 9'da [Office 365 Eğitim serisi için Azure ExpressRoute'un](https://channel9.msdn.com/series/aer) 10 bölümünü kaydettik.

## <a name="what-office-365-services-are-included"></a>Hangi Office 365 hizmetleri dahildir?
<a name="BKMK_WhatDoIGet"> </a>

Aşağıdaki tabloda ExpressRoute üzerinden desteklenen Office 365 hizmetleri listelenmektedir. Bu uygulamalar için hangi ağ isteklerinin İnternet bağlantısı gerektirdiğini anlamak için [Office 365 uç noktaları makalesini](./urls-and-ip-address-ranges.md) gözden geçirin.

| Dahil edilen uygulamalar |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype Kurumsal Online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive İş <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal ve paylaşılan<sup>1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Bağlan <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Bu uygulamaların her birinin ExpressRoute üzerinden desteklenmeyen İnternet bağlantı gereksinimleri vardır. Daha fazla bilgi için [Office 365 uç noktaları makalesine](./urls-and-ip-address-ranges.md) bakın.

Office 365 için ExpressRoute'a dahil olmayan hizmetler Kurumlar için Microsoft 365 Uygulamaları istemci indirmeleri, Şirket İçi Kimlik Sağlayıcısı Oturum Açma ve Çin'de Office 365 (21 Vianet tarafından çalıştırılır) hizmetidir.

## <a name="implementing-expressroute-for-office-365"></a>Office 365 için ExpressRoute Uygulama

ExpressRoute'un uygulanması ağ ve uygulama sahiplerinin katılımını gerektirir ve yeni [ağ yönlendirme mimarisini](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bant genişliği gereksinimlerini, güvenliğin uygulanacağı yeri, yüksek kullanılabilirliği vb. belirlemek için dikkatli bir planlama gerektirir. ExpressRoute'u uygulamak için şunları yapmanız gerekir:

1. ExpressRoute'un Office 365 bağlantı planlamanızda karşıladığı ihtiyacı tam olarak anlayın. Hangi uygulamaların İnternet'i veya ExpressRoute'u kullanacağını anlayın ve Office 365 trafik için hem İnternet'i hem de ExpressRoute'u kullanma bağlamında ağ kapasitenizi, güvenliğinizi ve yüksek kullanılabilirlik gereksinimlerinizi tam olarak planlayın.

2. Hem İnternet hem de ExpressRoute trafiği<sup>1</sup> için çıkış ve eşleme konumlarını belirleyin.

3. İnternet ve ExpressRoute bağlantılarında gereken kapasiteyi belirleyin.

4. Güvenlik ve diğer standart çevre denetimlerini uygulamak için bir plan oluşturun<sup>1</sup>.

5. ExpressRoute'a abone olmak için geçerli bir Microsoft Azure hesabına sahip olun.

6. Bir bağlantı modeli ve onaylı bir [sağlayıcı](/azure/expressroute/expressroute-locations) seçin. Müşterilerin birden çok bağlantı modeli veya iş ortağı seçebileceğini ve iş ortağının mevcut ağ sağlayıcınızla aynı olması gerekmeyecektir.

7. Trafiği ExpressRoute'a yönlendirmeden önce dağıtımı doğrulayın.

8. İsteğe bağlı olarak [QoS uygulayın](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) ve bölgesel genişletmeyi değerlendirin.

<sup>1</sup> Önemli performans konuları. Buradaki kararlar gecikme süresini önemli ölçüde etkileyebilir ve bu da Skype Kurumsal gibi uygulamalar için kritik öneme sahiptir.

Ek başvurular için [ExpressRoute belgelerine](/azure/expressroute/expressroute-introduction) ek olarak [yönlendirme kılavuzumuzu](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) kullanın.

Office 365 için ExpressRoute'u satın almak için, expressroute Premium aboneliğiyle istenen sayı ve boyut devrelerini sağlamak üzere bir veya daha fazla [onaylı sağlayıcıyla](/azure/expressroute/expressroute-locations) çalışmanız gerekir. Office 365'dan satın almak için ek lisans yoktur.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/expressrouteoffice365]()

[Office 365 için ExpressRoute'a](https://aka.ms/ert) kaydolmaya hazır mısınız?

## <a name="related-topics"></a>İlgili Konular

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)

[Office 365 için ExpressRoute ile Yönlendirme](routing-with-expressroute.md)

[Office 365 için ExpressRoute ile Ağ planlaması](network-planning-with-expressroute.md)

[Office 365 için ExpressRoute Uygulama](implementing-expressroute.md)

[Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma](bgp-communities-in-expressroute.md)

[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)

[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[ağ ve performans ayarlamayı Office 365](network-planning-and-performance.md)

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)
