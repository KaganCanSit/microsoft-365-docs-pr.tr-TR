---
title: Dış alıcılar hizmet uyarıları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
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
description: Posta kutusu kotasına ulaşan ayrı tutmadaki posta kutularını izlemek için dış alıcılar hizmet uyarılarını kullanın.
ROBOTS: NOINDEX
ms.openlocfilehash: 2eac85b5a4b6f0f1c7c8737041edc9de50b5a074
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840463"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Exchange Online izlemede dış alıcılara teslimi bekleyen iletiler için hizmet uyarıları

Hizmet uyarıları, yöneticileri Exchange Online dışındaki dış alıcılara posta kuyruğa alma konusunda bilgilendirmektedir. Bu uyarılar Microsoft dışında düzeltme eylemleri gerektirebilir, ancak düzeltme için gereken bilgileri sağlayabilir.

Bu hizmet uyarıları Microsoft 365 yönetim merkezi görüntülenir. Bu hizmet uyarılarını görüntülemek için **Sistem Durumu** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Hizmet durumu Exchange Online'na**</a> >  gidin ve **Etkin sorunlar** sekmesine tıklayın. Bu hizmet uyarılarının adı "Dış Alıcılara Eşiklerin Üzerinde İleti Kuyruğa Alma" şeklindedir.

![Exchange Online izleme panosunda görüntülenen dış alıcılara teslimi bekleyen iletiler için hizmet uyarısı.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Hizmet uyarısına çift tıkladığınızda, aşağıdakine benzer bir açılır sayfa görüntülenir.

![Dış alıcılara teslim edilmeyi bekleyen iletiler için hizmet uyarısında içerik.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Bu hizmet uyarıları neleri gösteriyor?

Dış alıcılara teslim edilmeyi bekleyen iletiler için hizmet uyarıları, Exchange Online dışındaki alıcıları hedefleyen iletilerin gecikebileceğini size bildirir. İletilerin kuyruğa alınması şirket içi ortamınızdan veya üçüncü taraf mesajlaşma veya günlük oluşturma çözümünden kaynaklanıyor olabilir.

Burada, iletileri dış alıcılara kuyruğa almak için bazı yaygın nedenler yer alır. Ancak, bu hizmet uyarılarına neden olan sorunlar bu nedenlerle sınırlı olmayabilir.

- DNS değişiklikleri

- Aşırı gönderme oranları

- Yetersiz veya boş disk alanı olmayan şirket içi İleti Aktarım Aracıları (MTA) veya günlük çözümleri

- Ters baskıda MTA'lar

- Yük dengeleyiciler de dahil olmak üzere ağ sorunları

- Sertifika sorunları

Her hizmet uyarısı, sorunu düzeltmek için üst düzey öneriler içerir. Hizmet uyarısı ayrıca uyarı sırasında kuyruğa alınan ileti sayısını, iletilerin kuyruğa alındığı etki alanını ve kuyruğa alınan iletilerin çoğuyla ilişkili SMTP hata kodunu gösterir.

Bu hizmet uyarılarının kök nedenini belirleme hakkında daha fazla bilgi için bkz. [Exchange Online'de posta akışı bilgileri](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Bu makale, kök nedeni düzeltmek için önerilen eylemleri de içerir.

> [!NOTE]
> Microsoft, üçüncü taraf satıcılar tarafından sağlanan her SMTP hata kodunu hesaba ekleyemez. Bu nedenle yöneticilerin, kendi MTA'larına veya kuruluşlarının kullandığı günlük çözümlerine özgü hata kodlarını araştırmaları gerekebilir.

## <a name="more-information"></a>Daha fazla bilgi

Kuruluşunuz yakın zamanda şirket içi veya Exchange Online kuruluşunuzda posta akışı bağlayıcıları oluşturduysa veya değiştirdiyse, daha fazla bilgi için aşağıdaki makalelere bakın.

- [Exchange Online'de bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Postayı yönlendirmek için bağlayıcıları ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Posta akışı en iyi yöntemleri](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Güvenlik & Uyumluluk Merkezi'nde posta akışı içgörüleri](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Posta akışı panosundaki kuyruklar içgörüleri](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Exchange Online'da e-posta iletisini izleme](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
