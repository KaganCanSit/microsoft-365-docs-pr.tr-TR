---
title: E-posta korumasının sırası ve önceliği
keywords: güvenlik, kötü amaçlı yazılım, Microsoft 365, M365, güvenlik merkezi, Microsoft 365 Defender portalı, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Kimlik için Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler korumaların Exchange Online Protection (EOP) sıralarını ve koruma ilkelerinin öncelik değerinin hangi ilkenin uygulandığını nasıl belirleyeceklerini öğrenebilirler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5fbccec656e0508535c2fbdaa055777a07968878
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988749"
---
# <a name="order-and-precedence-of-email-protection"></a>E-posta korumasının sırası ve önceliği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında, gelen e Exchange Online e birden çok koruma formu tarafından bayrakla işaretlenir. Örneğin, EOP'de bulunan ve tüm Microsoft 365 müşterilerinin kullanımına açık olan yerleşik kimlik avı önleme ilkeleri ve Office 365 müşterileri için Microsoft Defender'ın kullanımına açık olan daha güçlü kimlik avı önleme ilkeleri. Ayrıca iletiler kötü amaçlı yazılım, istenmeyen posta, kimlik avı gibi çeşitli algılama taramalarından geçer. Tüm bu etkinliklere bakarak, hangi ilkenin uygulandığıyla ilgili bazı karışıklıklar olabilir.

Genelde, iletiye uygulanan ilke **CAT (Kategori)** özelliğinde **X-Forefront-Antispam-Report** üst bilgisinde tanımlanır. Daha fazla bilgi için bkz [. İstenmeyen posta iletisi üstbilgileri](anti-spam-message-headers.md).

İletiye hangi ilkenin uygulandığını belirleyen iki önemli faktör vardır:

- **E-posta koruma türünün önceliği**: Bu düzen yapılandırılabilir değildir ve aşağıdaki tabloda açıklanmıştır:

  <br>

  ****

  |Öncelik|E-posta koruması|Kategori|Yönetnecek yer|
  |---|---|---|---|
  |1|Kötü amaçlı yazılım|CAT:MALW|[EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)|
  |2|Kimlik avı|CAT:PHSH|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |3|Yüksek güven istenmeyen posta|CAT:HSPM|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |4|Spoofing|CAT:SPOOF|[EOP'de akıllı Spoof Intelligence içgörü](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Kullanıcı kimliğine bürünme (korumalı kullanıcılar)|UIMP|[Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Etki alanı kimliğine bürünme (korumalı etki alanları)|DIMP|[Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365](configure-mdo-anti-phishing-policies.md)|
  |7|İstenmeyen posta|CAT:SPM|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |8|Toplu|CAT:BULK|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |

  <sup>\*</sup>Bu özellikler yalnızca kimlik avı önleme ilkeleri için Microsoft Defender'da Office 365.

- İlkenin **önceliği: Her** ilke türü için (istenmeyen posta önleme, kötü amaçlı yazılımdan koruma, kimlik avı önleme, vb.), herkes için geçerli olan bir varsayılan ilke vardır, ancak belirli kullanıcılara yönelik özel ilkeler oluşturabilirsiniz. Her özel ilkenin, ilkelerin uygulanma sırası belirleyen bir öncelik değeri vardır. Varsayılan ilke her zaman en son uygulanır.

  > [!IMPORTANT]
  > Kullanıcı aynı türde birden çok ilkede tanımlanmışsa, yalnızca en yüksek önceliğe sahip ilke o ilkeye uygulanır. Bu türlerden geri kalan ilkeler kullanıcı için değerlendirilmez (varsayılan ilke dahil).

Örneğin, aynı kullanıcılar için geçerli olan Office 365 için Microsoft Defender'daki kimlik avı önleme ilkelerini ve hem kullanıcı kimliğine bürünülen hem de kimlik sahtesi olarak tanımlanan bir iletiyi göz önünde bulundurabilirsiniz:

<br>

****

|İlke adı|Öncelik|Kullanıcı kimliğine bürünme|Anti-spoing|
|---|---|---|---|
|İlke A|1|On|Kapalı|
|İlke B|2|Kapalı|On|
|

1. Kimlik sahteciliğini, kullanıcı kimliğine bürünme (5) yerine daha yüksek öncelikli (4) olduğundan ileti işaretlenir ve kimlik sahtecisi olarak kabul edilir.
2. İlke A kullanıcılara uygulanır çünkü B İlkesinden daha yüksek önceliğe sahiptir.
3. İlke A'daki ayarlara bağlı olarak, ilkede yapılan bir ifadeyi koruma devre dışı olduğundan iletide hiçbir işlem gerçek değildir.
4. İlke işleme durduğu için, İlke B kullanıcılara hiçbir zaman uygulanmaz.

Aynı kullanıcıların aynı türe sahip birden çok özel ilkeye bilerek veya bilerek dahil olması olası olduğundan, özel ilkeler için aşağıdaki tasarım yönergelerini kullanın:

- Az sayıda kullanıcıya uygulanacak ilkelere daha yüksek öncelik ve çok fazla sayıda kullanıcıya uygulanacak ilkelere daha düşük öncelik atabilirsiniz. Varsayılan ilkenin her zaman en son uygulandığını unutmayın.
- Daha yüksek öncelikli ilkelerinizi, düşük öncelikli ilkelere göre daha sıkı veya daha özel ayarlara sahip olacak şekilde yapılandırabilirsiniz.
- Daha az özel ilke kullanmayı göz önünde bulundurabilirsiniz (yalnızca daha sıkı veya daha özel ayarlara ihtiyacı olan kullanıcılar için özel ilkeler kullanın).
