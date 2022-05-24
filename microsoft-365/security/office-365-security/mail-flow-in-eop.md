---
title: EOP'de posta akışı
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: Yönetici, Exchange Online Protection (EOP) içinde posta akışını ve yönlendirmeyi yapılandırma seçenekleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e0267af0297dce41657c76e97964e5c02fbe5815
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648755"
---
# <a name="mail-flow-in-eop"></a>EOP'de posta akışı

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olan Microsoft 365 kuruluşlarda veya Exchange Online posta kutusu olmayan tek başına Exchange Online Protection (EOP) kuruluşlarında, kuruluşunuza gönderilen tüm iletiler kullanıcılar görmeden önce EOP'yi geçer. kullanıcı posta kutularına yönlendirilmeden önce EOP'nin içinden geçen iletileri işleme için yönlendirme hakkında seçenekleriniz vardır.

## <a name="working-with-messages-and-message-access-options"></a>İletiler ve ileti erişim seçenekleriyle çalışma

EOP, iletilerinizin nasıl yönlendirildiğinde esneklik sağlar. Aşağıdaki konular, posta akışı işlemindeki adımları açıklar.

[Geçersiz alıcılara gönderilen iletileri reddetmek için Dizin Tabanlı Uç Engelleme'yi kullanma](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Hizmet ağı çevresinde geçersiz alıcılar için iletileri reddetmenize olanak tanıyan Dizin Tabanlı Uç Engelleme özelliğini açıklar.

[EOP'de kabul edilen etki alanlarını görüntüleme veya düzenleme, EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) hizmetinizle ilişkili etki alanlarının nasıl yönetileceğini açıklar.

Kuruluşunuza alt etki alanları eklerseniz, EOP hizmetiniz bunları yönetmenize de yardımcı olabilir. Alt etki alanları hakkında daha fazla bilgi için [bkz. Exchange Online'da alt etki alanları için posta akışını etkinleştirme](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Bağlayıcıları kullanarak posta akışını yapılandırma bağlayıcıları](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) tanıtır ve posta yönlendirmeyi özelleştirmek için bunları nasıl kullanabileceğinizi gösterir. Senaryolar arasında bir iş ortağı kuruluşuyla güvenli iletişimin sağlanması ve akıllı bir konak ayarlanması yer alır.

[Bağlayıcılar için Gelişmiş Filtreleme](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) , postanız EOP'ye gitmeden önce bir hizmete veya cihaza yönlendirilmişse bağlayıcıların nasıl yapılandırıldığını açıklar.

EOP'nin şirket içi Exchange posta kutularını koruduğu karma ortamlarda, şirket içi Exchange posta akışı kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız gerekir. Bu posta akışı kuralları, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşıyabilmesi için EOP istenmeyen posta filtreleme kararını çevirir. Ayrıntılar için bkz. [Karma ortamlarda Gereksiz E-posta klasörüne istenmeyen posta göndermek için EOP'yi yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). İletileri her kullanıcının Gereksiz E-posta klasörüne taşımak istemiyorsanız, istenmeyen posta önleme ilkelerinizi (içerik filtresi ilkeleri olarak da bilinir) düzenleyerek başka bir eylem seçebilirsiniz. Daha fazla bilgi için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Posta akışını doğrulama

Bağlayıcı yapılandırmanız da dahil olmak üzere EOP kurulumunuzun düzgün çalıştığını doğrulamak için bkz. "Bu görevin çalıştığını nasıl anlarsınız?" bölümünde [EOP hizmetinizi ayarlama](/exchange/standalone-eop/set-up-your-eop-service).

[Microsoft 365 bağlayıcılarınızı doğrulayarak posta akışını](/exchange/mail-flow-best-practices/test-mail-flow) test etme, posta akışınızın doğru ayarlandığını test etmeye yönelik yönergeler sağlar.
