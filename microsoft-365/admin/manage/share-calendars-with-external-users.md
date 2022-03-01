---
title: Dış kullanıcılarla takvimleri paylaşma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd
description: Kullanıcıların takvimlerini kuruluş Microsoft 365 yönetim merkezi kuruluş içindeki veya dışındaki herkesle paylaşlarını sağlamak için takvim paylaşımını etkinleştirme.
ms.openlocfilehash: 00ae4b96c54ae6b1471a90f598b9f96821947db3
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018887"
---
# <a name="share-calendars-with-external-users"></a>Dış kullanıcılarla takvimleri paylaşma

Bazen kullanıcılarının, kuruluş dışındaki kullanıcılarla toplantı zamanlamaları gerekir. Sık kullanılan toplantı zamanlarını bulma işlemini basitleştirmek için Microsoft 365, takvimleri bu kişilerin kullanımına smanızı sağlar. Bu kişiler, kendi kuruluşlarında yer alan kullanıcılar için uygun ve meşgul zamanları görmeleri gereken, ancak iş veya Microsoft 365 vardır.

Takvim paylaşımını, aynı kuruluşta yer alan tüm Microsoft 365 yönetim merkezi. Paylaşım etkinleştirildikten sonra, kullanıcılarınız Outlook Web App kuruluş içindeki veya dışındaki herkesle kendi takvimlerini paylaşmak için Outlook Web App'i kullanabilir. Kuruluşun içindeki kişiler de kendi takvimleriyle birlikte paylaşılan takvimi de 2. Kuruluşun dışındaki kişilere ise takvimi görüntülemek için kullanabilecekleri bir URL gönderilir. Ne zaman paylaşacağıza ve ne kadar paylaşılaca kuruluşta yer alan kullanıcılar karar verir.

> [!NOTE]
> takvimleri Exchange Server 2013 (şirket içi bir çözüm) kullanan bir kuruluşla paylaşmak için, Exchange yöneticisinin bulutla kimlik doğrulama ilişkisi ayarlaması gerekir. Buna federasyon adı ve en düşük yazılım gereksinimlerini karşılaması gerekir. Daha [fazla bilgi](/exchange/sharing-exchange-2013-help) için bkz. Paylaşım.
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Takvimi kullanarak takvim paylaşımını Microsoft 365 yönetim merkezi

1. Yönetim merkezinde Kuruluş **ayarları'Ayarlar** \> **gidin** ve Hizmetler sekmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank"> Takvim'i</a> **seçin**.
  
3. Takvim **sayfasında,** kullanıcıların takvimlerini kuruluş dışında yer alan ve takvimlerini kendi takvimleriyle paylaşmak isteyip Microsoft 365 Exchange. Anonim kullanıcıların (kimlik bilgileri olmayan kullanıcılar) e-posta daveti yoluyla takvimlere erişmesine izin vermek isteyip istemediknizi seçin.

4. Kullanıcıların ne tür takvim bilgilerine sahip olacaklarını seçin. Tüm bilgilere izin verme veya bilgileri yalnızca saat, konu ve yalnızca saat ile sınırlandırabilirsiniz.

## <a name="external-sharing-sync-interval"></a>Dış paylaşım eşitleme aralığı

Kiracınız dışında paylaşım için hızlı eşitleme şu anda desteklenmiyor. Bu yapılandırmalarda paylaşabilirsiniz, ancak eşitleme düzenli aralıklarla gerçekleşecektir. Kiracılar arası paylaşımın iki türü vardır:

1. **Microsoft 365 başka bir Microsoft 365** kullanıcıya paylaşma (dış paylaşım etkinleştirildiyse): Tamamen paylaşılan bir takvim oluşturulur, ancak eşitleme yaklaşık olarak her üç saatte bir gerçekleşecek. Bu kurulum için bir süre sonra hızlı eşitleme etkinleştirilebilir.

2. **Microsoft 365.com Outlook**: Dış paylaşım devre dışı bırakılmışsa, başka bir Microsoft 365 kullanıcıyla paylaşmak da bu gruba düşer. Paylaşımda bir ICS URL'si oluşturulur ve alıcı bu URL'yi kullanarak herhangi bir takvim hizmetine ekleyebilir. ICS aboneliğiyle, yeni güncelleştirmeleri almak için ICS aboneliğinin ne zaman eşitlen bir alıcının takvim hizmeti tarafından seçebilirsiniz. Alıcı bir Outlook.com veya Microsoft 365 kullanıcı ise, eşitleme yaklaşık olarak her üç saatte bir olur.

## <a name="invite-people-to-access-calendars"></a>Kişileri takvimlere erişmeleri için davet etme

Paylaşım etkinleştirildikten sonra, takvim sahipleri belirli kullanıcılara davetleri genişletebilirsiniz. Yönergeler için bkz[. Takvim paylaşımında Outlook Web App](https://support.microsoft.com/office/7ecef8ae-139c-40d9-bae2-a23977ee58d5).

## <a name="related-content"></a>İlgili içerik

[Bir site için dış paylaşımı açma veya kapatma](/sharepoint/change-external-sharing-site) (makale)\
[Videoya genel Microsoft 365 yönetim merkezi](../admin-overview/admin-center-overview.md) (video)\
[E-postayı ve takvimleri yönetme](/admin) (bağlantı sayfası)

