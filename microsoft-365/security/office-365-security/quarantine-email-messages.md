---
title: Karantinaya alınmış e-posta iletileri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler tehlikeli veya istenmeyen iletilerin Exchange Online Protection bir etki altında bulunan EOP'de karantina hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ac2d1bf550fd340c1e94ed5f3503352b40ba6556
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682779"
---
# <a name="quarantined-email-messages-in-eop-and-defender-for-office-365"></a>EOP'de e-posta iletileri karantinaya alınmış ve Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online ya da tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu Exchange Online kuruluşlarda, karantina tehlikeli veya istenmeyen iletileri tutmak için kullanılabilir.

Kötü amaçlı yazılımdan koruma ilkeleri, herhangi bir _ek kötü amaçlı_ yazılım içeriyorsa iletiyi otomatik olarak karantinaya alır. Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

Varsayılan olarak, istenmeyen posta önleme İlkeleri kimlik avını karantinaya alır ve yüksek güvene sahip kimlik avı iletilerini karantinaya alır ve kullanıcının Gereksiz E-posta klasörüne istenmeyen posta, yüksek güvene sahip istenmeyen posta ve toplu e-posta iletileri sağlar. Ancak istenmeyen postayı karantinaya almak, yüksek güvene sahip istenmeyen posta ve toplu e-posta iletilerini karantinaya almak için de istenmeyen posta önleme ilkeleri oluşturabilir ve özelleştirebilirsiniz. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

Karantinaya alınmış iletilerle hem kullanıcılar hem de yöneticiler kullanılabilir:

- _Karantina ilkeleri_ , iletinin neden karantinaya alındığına (desteklenen özellikler için) bağlı olarak, kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor veya verilmeyecekleri tanımlar. Varsayılan karantina ilkeleri, geçmiş özelliklerini aşağıda açıklandığı gibi zorlar. Yöneticiler, kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve uygulayabilir, ayrıca karantina bildirimlerini de açabilirsiniz. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

- Yöneticiler tüm kullanıcılar için tüm karantinaya alınmış ileti türleriyle çalışabilirsiniz. Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım olarak karantinaya alınmış iletilerde, yüksek güven kimlik avında veya posta akış kuralları (aktarım kuralları olarak da bilinir) sonucunda çalışabilirsiniz. Daha fazla bilgi için bkz [. EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme](manage-quarantined-messages-and-files.md).

- Varsayılan olarak, kullanıcılar alıcısı olduğu karantinaya alınmış iletilerle ve ileti istenmeyen posta, toplu e-posta veya kimlik avı (kimlik avına yüksek güven değildir) olarak karantinaya alınmış iletilerde çalışır. Daha fazla bilgi için bkz [. EOP'de kullanıcı olarak karantinaya alınmış iletileri bulma ve serbest bırakma](find-and-release-quarantined-messages-as-a-user.md).

  Yöneticiler, kullanıcıların kendi karantinaya alınmış kimlik avı iletilerini yönetmesini önlemek için, istenmeyen posta önleme ilkelerinde Kimlik avı e-posta filtreleme kararının karantinaya alınmış  iletilerine erişimi göz önüne alan bir karantina ilkesi atamalıdır. Daha fazla bilgi için bkz[. İstenmeyen posta](quarantine-policies.md#anti-spam-policies) önleme ilkeleri içinde karantina [ilkeleri atamaQuarantine ilkeleri](quarantine-policies.md).

- Yöneticiler ve kullanıcılar karantinada Microsoft'a hatalı pozitif sonuçlar bildirebilirsiniz.

- Karantinaya alınmış iletilerin süre dolmadan önce karantinada tutulma süresi, iletinin neden karantinaya alındığına bağlı olarak değişir. İletileri karantinaya alan özellikler ve buna karşılık gelen bekletme dönemleri aşağıdaki tabloda açıklanmıştır:

  |Karantina nedeni|Varsayılan bekletme süresi|Özelleştirilebilir mi?|Açıklamalar|
  |---|---|:---:|---|
  |İstenmeyen posta önleme ilkeleri tarafından karantinaya alınan iletiler: istenmeyen posta, yüksek güven istenmeyen posta, kimlik avı, yüksek güven amaçlı kimlik avı veya toplu.|15 gün: <ul><li>Varsayılan istenmeyen posta önleme ilkesinde.</li><li>PowerShell'de oluştur ilkelerin istenmeyen posta önleme ilkelerde.</li></ul> <p> İlke portalında kendi 30 günlük istenmeyen posta önleme Microsoft 365 Defender vardır.|Evet|İstenmeyen posta önleme ilkelerde bu değeri yapılandırarak (daha düşük) değeri yapılandırarak. Daha fazla bilgi için İstenmeyen posta önleme ilkelerini yapılandırma altında İstenmeyen postayı şu kadar süre karantinada **tutma (**_KarantinaRetentionPeriod_) [ayarına bakın](configure-your-spam-filter-policies.md).|
  |Kimlik avı önleme ilkeleri tarafından karantinaya alınan iletiler: EOP'de kimlik sahte e-postası zekası; kullanıcı kimliğine bürünme, etki alanı kimliğe bürünme veya posta kutusu kimliğine bürünme veya posta kutusu Office 365.|30 gün|Evet|Bu bekletme süresi ayrıca, istenmeyen posta önleme ilkelerindeki İstenmeyen postayı bu kadar süre karantinada **tutma (**_KarantinaRetentionPeriod_) ayarı **tarafından da denetlenir**. Kullanılan bekletme süresi, alıcının tanımlandığı **ilk eşleşen istenmeyen** posta önleme ilkesinden gelen değerdir.|
  |Kötü amaçlı yazılımdan koruma ilkeleri (kötü amaçlı yazılım iletileri) tarafından karantinaya alınan iletiler.|15 gün|Hayır||
  |Kasa için Defender'Kasa Ekler ilkeleri tarafından karantinaya alınan Office 365 amaçlı yazılım iletileri).|15 gün|Hayır||
  |Posta akışı kuralları tarafından karantinaya alınan iletiler: Eylem İletiyi barındırılan **karantinaya (Karantina) teslim etmektir**.|30 gün|Hayır||
  |Dosyalar Kasa, SharePoint, OneDrive ve Microsoft Teams (kötü amaçlı yazılım dosyaları) için ekler tarafından karantinaya alındı.|15 gün|Hayır||

  İletinin kullanım süresi karantinadan dolduğunda, kurtarılamaz.

Karantina hakkında daha fazla bilgi için bkz. Karantina hakkında [SSS](quarantine-faq.yml).
