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
description: Kullanıcıların takvimlerini kuruluş içindeki veya dışındaki herkesle paylaşabilmesi için Microsoft 365 yönetim merkezi takvim paylaşımını etkinleştirin.
ms.openlocfilehash: 9179e79e27320df2b943a9342ee0c2a91c866448
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468568"
---
# <a name="share-microsoft-365-calendars-with-external-users"></a>dış kullanıcılarla Microsoft 365 takvimleri paylaşma

Bazen kullanıcılarınızın kuruluşunuzun dışındaki kişilerle toplantı zamanlaması gerekir. Microsoft 365, ortak toplantı zamanlarını bulma sürecini basitleştirmek için takvimleri bu kişilerin kullanımına sunabilirsiniz. Bunlar, kuruluşunuzdaki kullanıcılar için serbest ve meşgul zamanlarını görmesi gereken ancak Microsoft 365 kuruluşunuz için kullanıcı hesapları olmayan kişilerdir.

Microsoft 365 yönetim merkezi kuruluşunuzdaki tüm kullanıcılar için takvim paylaşımını etkinleştirebilirsiniz. Paylaşım etkinleştirildikten sonra kullanıcılarınız Outlook Web App kullanarak takvimlerini kuruluş içindeki veya dışındaki herkesle paylaşabilir. Kuruluş içindeki kişiler paylaşılan takvimi kendi takvimleriyle birlikte görüntüleyebilir. Kuruluşun dışındaki kişilere ise takvimi görüntülemek için kullanabilecekleri bir URL gönderilir. Kuruluşunuzdaki kullanıcılar ne zaman ve ne kadar paylaşacaklarına karar verir.

> [!NOTE]
> Takvimleri Exchange Server 2013 (şirket içi çözüm) kullanan bir kuruluşla paylaşmak istiyorsanız, Exchange yöneticisinin bulutla bir kimlik doğrulama ilişkisi ayarlaması gerekir. Bu, federasyon olarak bilinir ve en düşük yazılım gereksinimlerini karşılamalıdır. Daha fazla bilgi için bkz [. Paylaşım](/exchange/sharing-exchange-2013-help) .
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi kullanarak takvim paylaşımını etkinleştirme

1. Yönetim merkezinde **Ayarlar** \> **Kuruluş ayarları'na** gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Hizmetler** sekmesinde</a> **Takvim'i** seçin.
  
3. **Takvim** sayfasında, kullanıcıların takvimlerini kuruluşunuzun dışında Microsoft 365 veya Exchange sahip kişilerle paylaşmasına izin vermek isteyip istemediğinizi seçin. Anonim kullanıcıların (kimlik bilgileri olmayan kullanıcıların) takvimlere e-posta daveti aracılığıyla erişmesine izin vermek isteyip istemediğinizi seçin.

4. Kullanıcıların kullanımına sunulabilecek takvim bilgilerinin türünü seçin. Tüm bilgilere izin verebilir veya yalnızca zamana veya zamana, konuya ve konuma sınırlayabilirsiniz.

## <a name="external-sharing-sync-interval"></a>Dış paylaşım eşitleme aralığı

Kiracınızın dışında paylaşım için anlık eşitleme şu anda desteklenmiyor. Bu yapılandırmalarda paylaşabilirsiniz ancak eşitleme düzenli aralıklarla gerçekleşir. İki tür kiracılar arası paylaşım vardır:

1. **Başka bir Microsoft 365 kullanıcıya Microsoft 365 (dış paylaşım etkinse):** Tam olarak paylaşılan bir takvim oluşturulur, ancak eşitleme yaklaşık üç saatte bir gerçekleşir. Bu kurulum için anında eşitleme sonunda etkinleştirilecektir.

2. **Outlook.com kullanıcısına Microsoft 365**: Dış paylaşım devre dışı bırakılırsa, başka bir Microsoft 365 kullanıcıyla paylaşım da bu gruba girer. Paylaşım sırasında, alıcının herhangi bir takvim hizmetine eklemek için kullanabileceği bir ICS URL'si oluşturulur. ICS aboneliğiyle, alıcının takvim hizmeti yeni güncelleştirmeleri almak için ICS aboneliğinin ne zaman eşitlenmesini seçer. Alıcı bir Outlook.com veya Microsoft 365 kullanıcısıysa, eşitleme yaklaşık üç saatte bir gerçekleşir.

## <a name="invite-people-to-access-calendars"></a>Kişileri takvimlere erişmeleri için davet etme

Paylaşım etkinleştirildikten sonra, takvim sahipleri davetleri belirli kullanıcılara genişletebilir. Yönergeler için bkz[. Outlook Web App takviminizi paylaşma](https://support.microsoft.com/office/7ecef8ae-139c-40d9-bae2-a23977ee58d5).

## <a name="related-content"></a>İlgili içerik

[Site için dış paylaşımı açma veya kapatma](/sharepoint/change-external-sharing-site) (makale)\
[Microsoft 365 yönetim merkezi genel bakış](../admin-overview/admin-center-overview.md) (video)\
[E-posta ve takvimleri yönetme](/admin) (bağlantı sayfası)

