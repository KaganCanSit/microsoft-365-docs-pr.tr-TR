---
title: Office 365 için Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Azure ExpressRoute'u Office 365 ve dağıtım için ağ uygulama projesini planlama hakkında bilgi edinin.
ms.openlocfilehash: 9a4f4be76751ec03610bd766f51ec91526ca18a4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986482"
---
# <a name="azure-expressroute-for-office-365"></a>Office 365 için Azure ExpressRoute

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Azure ExpressRoute'un Azure ExpressRoute ile birlikte nasıl Office 365 ve Azure ExpressRoute'u bu uygulamayla birlikte kullanmak üzere dağıtıyorsanız gerekli olacak ağ uygulama projesinin nasıl planla Office 365. Azure'da çalışan altyapı ve platform hizmetleri, ağ mimarisi ve performansla ilgili konuları ele alarak genellikle yarar sağlar. Bu durumlarda Azure için ExpressRoute'u öneririz. Web Hizmetleri ve Dynamics 365 Office 365 Hizmet Olarak Yazılım teklifleri, İnternet üzerinden güvenli ve güvenilir bir şekilde erişilleri için yerleşik olarak bulundu. İnternet performansı ve güvenliği hakkında bilgi edinebilir ve Azure ExpressRoute'u ne zaman Office 365 ağ bağlantısını değerlendirme [Office 365 okuyabilirsiniz](assessing-network-connectivity.md).

> [!NOTE]
> Uç Nokta için Microsoft Defender, Azure ExpressRoute ile tümleştirme sağlamaz. Bu, müşterilerin özel bir ağdan Uç nokta bulut hizmetleri için Microsoft Defender'a bağlantısı etkinleştiren ExpressRoute kurallarını tanımlamalarını durdurmasa da, hizmet veya bulut altyapısı geliştikçe kuralların müşterilere açık olması müşteriye bırakılmıştır.

> [!NOTE]
> Çoğu durumda hizmet için en Microsoft 365 modeli sağlamay olduğundan, ExpressRoute'u bu hizmet için önerilmez. Bu nedenle, microsoft yetkilendirmenin bu bağlantı modelini daha iyi kullanmak için Microsoft 365. Tüm müşteri isteklerini gözden geçirer ve ExpressRoute Microsoft 365 yalnızca gerekli olduğu nadir senaryolarda yetkilendir ederiz. Daha fazla bilgi için [Microsoft 365 için ExpressRoute](https://aka.ms/erguide) kılavuzunu okuyun ve belgeyi üretkenliğiniz, ağınız ve güvenlik ekipleriyle kapsamlı bir şekilde gözden geçirmenizi, gerekirse bir özel durum göndermek için Microsoft hesabı ekibiyle birlikte çalışmanızı sağlar. Yeni e-posta için rota filtreleri oluşturmaya Office 365 yetkisiz abonelikler bir [hata iletisi alır](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>Azure ExpressRoute'u proje Office 365

İnternet bağlantısına ek olarak, Office 365 ağ trafiğinin bir alt kümesini öngörülebilirlik ve Microsoft ağ bileşenleri için %99,95 çalışma süresi SLA'sı sunan bir doğrudan bağlantı üzerinden yönlendirmeyi seçebilirsiniz. Azure ExpressRoute size bu özel ağ bağlantısını Office 365 Microsoft bulut hizmetleriyle sunar.

Mevcut MPLS WAN'nıza sahip olup olmadığınıza bakılmaksızın, ExpressRoute üç şekilden birini kullanarak ağ mimarinize eklenebilir; bir desteklenen bulut değişimi birlikte konum sağlayıcısı, Ethernet noktadan noktaya bağlantı sağlayıcısı veya MPLS bağlantı sağlayıcısı aracılığıyla. Bölgenizin [hangi sağlayıcılarının kullanılabilir olduğunu görme](/azure/expressroute/expressroute-locations). Doğrudan ExpressRoute bağlantısı, aşağıdaki Hangi hizmetler dahil Office 365 [belirtilen uygulamalara bağlantıyı etkinleştirir](azure-expressroute.md#BKMK_WhatDoIGet). Diğer tüm uygulama ve hizmetlerin ağ trafiği İnternet'den geçmeye devam edecektir.

tipik bir Office 365 müşterisi tarafından Office 365, Windows Update ve TechNet gibi tüm Microsoft uygulamalarına erişmek için İnternet üzerinden Microsoft'un veri merkezlerine bağlanmasını gösteren aşağıdaki üst düzey ağ diyagramını göz önünde bulundurabilirsiniz. Hem şirket içi ağdan hem de bağımsız bir İnternet bağlantısından bağlanan müşteriler benzer bir ağ yolu kullanır.

![Office 365 bağlantısını denetleyin.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Şimdi de İnternet'i ve ExpressRoute'u kullanarak Office 365 kullanan bir müşteriyi gösteren güncelleştirilmiş diyagrama Office 365. Genel DNS ve yerel ağ düğümleri gibi bazı Content Delivery Network hala genel İnternet bağlantısı gerektir. Ayrıca, müşterinin ExpressRoute bağlantılı binalarında yer alan kullanıcıların İnternet üzerinden bağlantıda olduğunu da fark ettiysiniz.

![Office 365 Route ile bağlantıda bağlantı sağlar.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Daha fazla bilgi almak mı istiyor musunuz? İş için [Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) ile ağ trafiğinizi yönetmeyi Office 365 ayrıca Azure [ExpressRoute'u](/azure/expressroute/expressroute-faqs) bu ağ hizmeti için Office 365. Kavramları daha kapsamlı açıklamaya yardımcı olmak için, Kanal 9'da Office 365 için [Azure ExpressRoute'un](https://channel9.msdn.com/series/aer) 10 bölümlık bir Eğitim serisi kaydettik.

## <a name="what-office-365-services-are-included"></a>Hangi Office 365 hizmetler dahildir?
<a name="BKMK_WhatDoIGet"> </a>

Aşağıdaki tabloda, ExpressRoute üzerinden Office 365 hizmetleri listelemektedir. Bu uygulamalara [Office 365 yönelik hangi ağ isteklerinin](./urls-and-ip-address-ranges.md) İnternet bağlantısı gerektir olduğunu anlamak için lütfen aşağıdaki uç noktalar makalesini gözden geçirebilirsiniz.

| Dahil olan uygulamalar |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype Kurumsal <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive İş <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal ve <sup>paylaşım1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Bağlan <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Bu uygulamaların her biri ExpressRoute üzerinden desteklenen İnternet bağlantısı gereksinimlerine sahiptir, [daha fazla bilgi Office 365 için](./urls-and-ip-address-ranges.md) aşağıdaki uç noktalar makalesine bakın.

Office 365 için ExpressRoute'a dahil olmayan hizmetler Kurumlar için Microsoft 365 Uygulamaları istemci indirmeleri, Şirket İçi Kimlik Sağlayıcısı Oturum Açma ve Office 365 (21 Vianet tarafından işletilen) hizmetidir.

## <a name="implementing-expressroute-for-office-365"></a>Proje için ExpressRoute'u Office 365

ExpressRoute'u uygulamak için ağ ve uygulama sahiplerinin katılımı gerekir ve yeni ağ yönlendirme mimarisini [, bant](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) genişliği gereksinimlerini, güvenliğin nerede uygulan uygulandığını, yüksek kullanılabilirliği, daha birçok farklı özelliği belirlemek için dikkatli bir planlama yapmayı gerektirir. ExpressRoute'u uygulamak için şunları gerekir:

1. Hızlı bağlantı planlamanız için ExpressRoute'un memnun Office 365 anlıyoruz. Hangi uygulamaların İnternet'i veya ExpressRoute'u kullanmayacaklarını anlamalı ve hem İnternet hem de ExpressRoute'u daha iyi bir trafik için kullanma bağlamında ağ kapasitesi, güvenlik ve yüksek kullanılabilirlik Office 365 planlasın.

2. Hem İnternet hem de ExpressRoute trafiği için çıkış ve eşleme konumlarını <sup>belirleme1</sup>.

3. İnternet ve ExpressRoute bağlantılarda gereken kapasiteyi belirler.

4. Güvenliği ve diğer standart çevre denetimlerini uygulamak için planınız hazır <sup>olmalı1</sup>.

5. ExpressRoute'a Microsoft Azure için geçerli bir hesabınız olmalıdır.

6. Bir bağlantı modeli ve onaylanmış sağlayıcı [seçin](/azure/expressroute/expressroute-locations). Müşterilerin birden çok bağlantı modeli veya iş ortağı seçe bir iş ortağı seçeyle ilgili olarak iş ortağının mevcut ağ sağlayıcınızla aynı olması gerek olmadığını unutmayın.

7. Trafiği ExpressRoute'a yönlendirmeden önce dağıtımı doğrulamalısınız.

8. İsteğe bağlı [olarak QoS uygulayarak](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) bölgesel genişletmeyi değerlendirin.

<sup>1</sup> Performansla ilgili dikkate alınacak önemli noktalar. Burada alınan kararlar gecikme süresini çok ciddi düzeyde etkilemektedir ve bu durum gecikme süresinin önemli bir etkisi Skype Kurumsal.

Ek başvurular için, ExpressRoute [belgelerine](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) ek olarak [yönlendirme kılavuzumızı kullanın](/azure/expressroute/expressroute-introduction).

Office 365 için ExpressRoute'u satın almak için, bir veya birden çok onaylanmış sağlayıcıyla birlikte çalışmanız ve ExpressRoute hizmeti aboneliğiyle istenen devrelerin sayısını ve boyutunu Premium gerekir.[](/azure/expressroute/expressroute-locations) Lisans satın almak için ek Office 365.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/expressrouteoffice365]()

ExpressRoute'a kaydolmaya [hazır Office 365 mısınız](https://aka.ms/ert)?

## <a name="related-topics"></a>İlgili Konular

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)

[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)

[Posta için ExpressRoute ile yönlendirme Office 365](routing-with-expressroute.md)

[ExpressRoute ile ağ planlama Office 365](network-planning-with-expressroute.md)

[Proje için ExpressRoute'u Office 365](implementing-expressroute.md)

[Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma](bgp-communities-in-expressroute.md)

[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)

[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)
