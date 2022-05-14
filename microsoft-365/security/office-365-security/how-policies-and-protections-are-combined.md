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
description: Yöneticiler, Exchange Online Protection'de (EOP) korumaların uygulama sırası ve koruma ilkelerindeki öncelik değerinin hangi ilkenin uygulandığını nasıl belirlediği hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8b7bf48de0939ec913982feb399b38dc2c540157
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417764"
---
# <a name="order-and-precedence-of-email-protection"></a>E-posta korumasının sırası ve önceliği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, gelen e-postalar birden çok koruma biçimiyle işaretlenebilir. Örneğin, EOP'de tüm Microsoft 365 müşterilerin kullanımına sunulan yerleşik kimlik avı önleme ilkeleri ve Office 365 için Microsoft Defender müşterilerin kullanımına sunulan daha sağlam kimlik avı önleme ilkeleri. İletiler ayrıca kötü amaçlı yazılım, istenmeyen posta, kimlik avı vb. için birden çok algılama taramasından geçer. Tüm bu etkinlik göz önünde bulundurulduğunda, ilkenin hangi ilkenin uygulandığı konusunda bazı karışıklıklar olabilir.

Genel olarak, bir iletiye uygulanan bir ilke **CAT (Category)** özelliğindeki **X-Forefront-Antispam-Report** üst bilgisinde tanımlanır. Daha fazla bilgi için bkz [. İstenmeyen postadan koruma iletisi üst bilgileri](anti-spam-message-headers.md).

İletiye hangi ilkenin uygulandığını belirleyen iki önemli faktör vardır:

- **E-posta koruma türü için işleme sırası**: Bu sıra yapılandırılamaz ve aşağıdaki tabloda açıklanmıştır:

  |Sipariş|E-posta koruması|Kategori|Yönetileceği yer|
  |:---:|---|---|---|
  |1|Malware|CAT:MALW|[EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)|
  |2|Kimlik Avı|CAT:PHSH|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |3|Yüksek güvenilirlikli istenmeyen posta|CAT:HSPM|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |4|Sızdırma|CAT:SPOOF|[EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Kullanıcı kimliğe bürünme (korumalı kullanıcılar)|UIMP|[Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Etki alanı kimliğe bürünme (korumalı etki alanları)|GAMZE|[Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md)|
  |7|Spam|CAT:SPM|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|
  |8|Toplu|CAT:BULK|[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)|

  <sup>\*</sup>Bu özellikler yalnızca Office 365 için Microsoft Defender kimlik avı önleme ilkelerinde kullanılabilir.

- **İlkenin önceliği**: Her ilke türü için (istenmeyen posta, kötü amaçlı yazılımdan koruma, kimlik avından koruma vb.) herkes için geçerli olan varsayılan bir ilke vardır, ancak belirli kullanıcılar (alıcılar) için geçerli olan özel ilkeler oluşturabilirsiniz. Her özel ilkenin, ilkelerin uygulanacağı sırayı belirleyen bir öncelik değeri vardır. Varsayılan ilke her zaman en son uygulanır.

  > [!IMPORTANT]
  > Alıcı aynı türdeki birden çok ilkede (istenmeyen posta, kimlik avı önleme vb.) tanımlanmışsa, alıcıya yalnızca en yüksek önceliğe sahip ilke uygulanır. Bu türdeki diğer ilkeler alıcı için değerlendirilmez (varsayılan ilke dahil).

Örneğin, **Office 365 için Microsoft Defender'de aynı kullanıcılar için geçerli olan** aşağıdaki **kimlik avı önleme ilkelerini** ve **hem kullanıcı kimliğine bürünme hem de kimlik sahtekarlığı** olarak tanımlanan bir iletiyi göz önünde bulundurun:

|İlke adı|Öncelik|Kullanıcı kimliğe bürünme|Kimlik sahtekarlığı önleme|
|---|:---:|:---:|:---:|
|İlke A|1|-Inı|Kapalı|
|İlke B|2|Kapalı|-Inı|

1. Kimlik sahtekarlığı (4) kullanıcı kimliğine bürünmeden önce değerlendirildiğinden ileti kimlik sahtekarlığı olarak tanımlanır (5).
2. İlke A, İlke B'den daha yüksek bir önceliğe sahip olduğundan önce uygulanır.
3. İlke A'daki ayarlara bağlı olarak, kimlik sahtekarlığı önleme kapatıldığından iletide hiçbir işlem yapılmaz.
4. Dahil edilen tüm alıcılar için kimlik avı önleme ilkelerinin işlenmesi durdurulduğundan, İlke B, aynı zamanda İlke A'da bulunan alıcılara hiçbir zaman uygulanmaz.

Aynı kullanıcılar kasıtlı olarak veya istemeden aynı türde birden çok ilkeye dahil edilebileceğinden, özel ilkeler için aşağıdaki tasarım yönergelerini kullanın:

- Az sayıda kullanıcı için geçerli ilkelere daha yüksek bir öncelik ve çok sayıda kullanıcı için geçerli ilkelere daha düşük öncelik atayın. Varsayılan ilkenin her zaman en son uygulandığını unutmayın.
- Daha yüksek öncelikli ilkelerinizi, düşük öncelikli ilkelerden daha katı veya daha özel ayarlara sahip olacak şekilde yapılandırın.
- Daha az özel ilke kullanmayı göz önünde bulundurun (yalnızca daha katı veya daha özel ayarlar gerektiren kullanıcılar için özel ilkeler kullanın).
