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
description: Yönetici, EOP'de (EOP) posta akışını ve yönlendirmeyi yapılandırma Exchange Online Protection hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1d7bca416a6144e2745a2c5d631c3e634e935ff4
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "62988832"
---
# <a name="mail-flow-in-eop"></a>EOP'de posta akışı

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu Exchange Online olan veya Exchange Online Protection posta kutusu olmayan tek başına Exchange Online (EOP) kuruluşlarına gönderilen tüm iletiler, çalışanlarınızı görmeden önce EOP üzerinden geçer. EOP'den geçen iletileri, çalışan gelen kutularınıza yönlendirilene kadar işleme için nasıl yönlendirebilirsiniz?

## <a name="working-with-messages-and-message-access-options"></a>İletiler ve ileti erişim seçenekleriyle çalışma

EOP, iletilerinizin nasıl yönlendirildikleri konusunda esneklik sunar. Aşağıdaki konu başlıkları, posta akışı sürecindeki adımları açıklar.

[Geçersiz alıcılara gönderilen iletileri reddetmek için Dizin Tabanlı Edge Engellemesi kullanma](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Hizmet ağı çevresinde geçersiz alıcıların iletilerini reddetmenizi sağlayan Dizin Tabanlı Kenar Engelleme özelliği açıklanır.

[EOP'de kabul edilen etki alanlarını görüntülemek](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) veya düzenlemek, EOP hizmetiyle ilişkilendirilmiş etki alanlarının nasıl yönet açık olduğunu açıklar.

Organizasyona alt etki alanları eklersanız, EOP hizmetiniz bunları yönetmenize de yardımcı olabilir. Alt etki alanları hakkında daha fazla bilgi edinmek için şu [adreste yer alan Alt etki alanları için posta akışını Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Bağlayıcıları kullanarak posta akışını yapılandırmak](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) , bağlayıcıları kullanmaya giriş sağlar ve posta yönlendirmeyi özelleştirmek için bunları nasıl kullanabileceğinizi gösterir. Senaryolar, iş ortağı bir kuruluşla güvenli iletişim sağlamayı ve akıllı bir ana bilgisayar ayarlamayı içerir.

[İyileştirilmiş Bağlayıcılar için Filtreleme](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) , postanız EOP'den önce bir hizmet veya cihaza yönlendirildiyse bağlayıcıların nasıl yapılandırılması olduğunu açıklar.

EOP'nin şirket içi veya posta kutularını Exchange karma ortamlarda, şirket içi posta kutularında posta akış kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız Exchange. Bu posta akış kuralları EOP istenmeyen posta filtreleme kararını çevirerek, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşımasini sağlar. Ayrıntılar için bkz. [EOP'yi karma ortamlarda gereksiz E-posta klasörüne istenmeyen posta teslim edecek şekilde yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). İletileri her kullanıcının Gereksiz E-posta klasörüne taşımak istemiyorsanız, istenmeyen posta önleme ilkelerinizi (içerik filtresi ilkeleri olarak da bilinir) düzenleyerek başka bir eylem seçebilirsiniz. Daha fazla bilgi için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Posta akışını doğrulama

Bağlayıcı yapılandırmanız da dahil olmak üzere EOP kurulum güncelleştirmenizin düzgün çalıştığını doğrulamak için, "Bu görevin çalıştığını nasıl biliyorsunuz?" bölümüne [bakın](/exchange/standalone-eop/set-up-your-eop-service).

[Posta akışlarınızı doğru bir Microsoft 365 posta akışınızı](/exchange/mail-flow-best-practices/test-mail-flow) test etmek için yönergeler sağlar.
