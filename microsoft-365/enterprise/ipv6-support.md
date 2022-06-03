---
title: Microsoft 365 hizmetlerinde IPv6 desteği
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Özet: Microsoft 365 bileşenlerinde ve Microsoft 365 kamu tekliflerinde IPv6 desteğini açıklar.'
ms.openlocfilehash: 2619567e8dac6f4b87cba0108bcf105011c4a87c
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872752"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Microsoft 365 hizmetlerinde IPv6 desteği

Kurumsal ağlar, hizmet sağlayıcıları ve cihazlar arasında IPv6'nın giderek daha fazla benimsenmesi ve desteklenmesiyle birlikte, birçok müşteri kullanıcılarının IPv6 istemcilerinden ve IPv6 ağlarından Microsoft 365 hizmetlerine erişmeye devam edip edemediğini merak ediyor. Microsoft 365 hizmetleri hem IPv6 çift yığından hem de yalnızca IPv6 cihazlarından başarıyla kullanılabilir. Aslında, tüketicilerden IPv6'nın daha iyi benimsenmesini sağlayan büyük kuruluşlara kadar artan sayıda müşterimiz var. Çoğu müşteri için, IPv4 dijital manzaralarından tamamen kaybolmaz, bu nedenle IPv6 gerektirmeyi veya Microsoft 365 özellikleri veya hizmetlerinde IPv4 önceliklerini kaldırmayı planlamıyoruz.

Microsoft 365 temel önceliklerimizden biri, herhangi bir konumdan, herhangi bir cihazdan İnternet üzerinden sorunsuz müşteri ve kullanıcı deneyimleri sağlamaktır. Buna, çift yığın yapılandırmasında IPv6 kullanan müşteri cihazlarından Microsoft 365 erişimi ve yalnızca IPv6 istemci dağıtımlarına geçiş dahildir. Çoğu durumda, Microsoft 365 [ağ bağlantı ilkeleri](microsoft-365-network-connectivity-principles.md), Microsoft 365 [URL'leri ve IP adresi aralıkları ve](urls-and-ip-address-ranges.md) Microsoft 365 [ağ planlama en iyi yöntemlerinde](network-and-migration-planning.md#best-practices-for-network-planning-and-improving-migration-performance-for-office-365) açıklandığı gibi Microsoft 365 bağlanmaya yönelik standart bir İnternet tabanlı modeli izlediğinizde , IPv6 geçişleri kullanıcı deneyiminiz için kesintiye neden olmaz.

Birçok Microsoft 365 hizmeti bugün yerel IPv6 desteği sağlar ve doğrudan IPv6 çift yığınından ve yalnızca IPv6 istemcilerinden erişilebilir. Microsoft 365 ayrıca müşteriler ve ağ çözümü sağlayıcıları tarafından IPv4 İnternet kaynaklarına bağlanmak için yaygın olarak kullanılan geleneksel IPv6 ile IPv4 çeviri teknolojilerine (temel 64 proxy'ler veya DNS64/NAT64 gibi) erişim sağlar.

Tüm SaaS hizmetlerinde ve İnternet'te olduğu gibi yerel olarak IPv6'nın da etkinleştirildiği Microsoft 365 arabirimleri, özellikleri ve API'leri kapsamı sürekli olarak ve doğrudan müşteri eylemi veya denetimi olmadan genişler. Ağlarınızda Microsoft 365 ve İnternet'e erişmesi gereken IPv6 veya yalnızca IPv6 hizmetleri çalıştırıyorsanız, ağ yeniden yapılandırmaları olmadan Microsoft 365 uçtan uca IPv6 bağlantısını sağlamak için DNS64/NAT64 gibi dinamik IPv6/IPv4 geçiş mekanizmaları eklemeniz önerilir.

Microsoft 365 hizmetlerin çoğu son kullanıcılar ve BT yöneticileri için tamamen şeffaf bir şekilde IPv6 özellikleriyle etkinleştirilmiştir veya etkinleştirilecektir. Bazı Microsoft 365 senaryoları (anonim gelen e-posta gibi) IPv6 ile birlikte kullanılmak üzere özel gereksinimlere ve dikkat edilmesi gereken noktalara sahiptir. Senaryoya özgü IPv6 gereksinimleri ve dikkat edilmesi gerekenler hakkında daha fazla bilgi için lütfen Microsoft hesabı ekibinize veya Microsoft desteğine başvurun.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Ağ Bağlantısına Genel Bakış](microsoft-365-networking-overview.md)

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 için ağ planlama ve performans ayarlama](network-planning-and-performance.md)

[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)

[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://aka.ms/netonboard)

[Microsoft hızlı ve güvenilir küresel ağını nasıl oluşturur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağ blogu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
