---
title: Dış alıcılar hizmet uyarıları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Posta kutularının tutarak posta kutusu kotasına ulaştığını izlemek için dış alıcılar hizmet uyarılarını kullanın.
ms.openlocfilehash: 8db8e090ec5430f13153bc3edf5b3315c041d9cf
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568016"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Dış alıcılara teslimi bekleyen iletiler için hizmet uyarıları Exchange Online izlemede

Hizmet uyarıları, yöneticileri posta kuyruğa alma dışında gelen dış alıcılara bilgi Exchange Online. Bu uyarılar Microsoft dışından düzeltme eylemleri gerektirebilecektir, ancak düzeltmek için gereken bilgileri size de sağ herhangi bir şekilde sağ iseler.

Bu hizmet uyarıları aşağıdaki Microsoft 365 yönetim merkezi. Bu hizmet uyarılarını görüntülemek için Durum'a  > <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Hizmet durumu**</a> >  **Exchange Online** ardından Etkin sorunlar **sekmesine** tıklayın. Bu hizmet uyarılarını "Dış Alıcılara Sıraya Alınan İleti Eşiğin Üstünde" adıdır.

![İzleme panosunda görüntülenen dış alıcılara teslimi bekleyen iletiler Exchange Online uyarısı.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Hizmet uyarıya çift tıklarken, aşağıdakine benzer bir uç sayfası görüntülenir.

![Dış alıcılara teslimi bekleyen iletiler için hizmet uyarılarında yer alan içerik.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Bu hizmet uyarıları neleri gösteriyor?

Dış alıcılara teslimi bekleyen iletiler için hizmet uyarıları, posta dışından alıcılara gönderilen iletilerin gecikmeli Exchange Online konusunda sizi bilgilemektedir. İletileri sıraya alma, şirket içi ortamınız veya üçüncü taraf mesajlaşma ya da günlük gönderme çözümünüz nedeniyle olabilir.

İşte, iletileri dış alıcılara kuyruğa alamanın yaygın nedenlerinden bazıları. Bununla birlikte, bu hizmet uyarılarına neden olan sorunlar bu nedenlerle sınırlı değildir.

- DNS değişiklikleri

- Aşırı gönderme oranları

- Şirket içi İleti Aktarım Aracıları (MTA) veya boş disk alanı olmayan günlük oluşturma çözümleri

- Geri baskıda MTA'lar

- Yük dengeleri de içinde olmak üzere ağ sorunları

- Sertifika sorunları

Her hizmet uyarısı sorunu düzeltmeye ilişkin üst düzey öneriler içerir. Hizmet uyarısı ayrıca uyarı sırasında sıraya alınan iletilerin sayısını, iletilerin sıraya alınan etki alanını ve sıraya alınan iletilerin çoğuyla ilişkilendirilmiş SMTP hata kodunu da gösterir.

Bu hizmet uyarılarının temel nedenini belirleme hakkında daha fazla bilgi için bkz. Bu [hizmetlerde posta akışı Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Bu makale, kök nedenini düzeltmek için de önerilen eylemleri içerir.

> [!NOTE]
> Microsoft, üçüncü taraf satıcılar tarafından sağlanan her SMTP hata kodu için hesap gerçekleştir değildir. Bu nedenle yöneticilerin, kendi MTA'larına veya kuruluşları tarafından kullanılan günlük bilgilerine özgü hata kodlarını araştırmaları gerekebilir.

## <a name="more-information"></a>Daha fazla bilgi

Kuruluşunuz yakın zamanda şirket içi veya şirket içi posta akış bağlayıcılarını oluşturdu veya değiştirdiyse, daha fazla bilgi Exchange Online için aşağıdaki makalelere bakın.

- [E-postada bağlayıcıları kullanarak posta Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Postayı yönlendiren bağlayıcıları ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Posta akışıyla ilgili en iyi yöntemler](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Güvenlik ve Uyumluluk Merkezi'nde & öngörüleri](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Posta akışı panosunda Kuyruklar içgörü](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [E-posta iletisi izleme Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
