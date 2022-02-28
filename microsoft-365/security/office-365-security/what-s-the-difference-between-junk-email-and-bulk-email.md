---
title: Gereksiz&apos; e-posta ile toplu e-posta arasındaki fark nedir?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) gereksiz e-posta (istenmeyen posta) ile toplu e-posta (gri posta) arasındaki Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e8a896ac3360ccf799dbe34c7e298f76140ee6d5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983363"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>EOP'de gereksiz e-posta ile toplu e-posta arasındaki fark nedir?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu olan Exchange Online kuruluşlarda, müşteriler bazen şunları sorar: "Gereksiz e-posta ve toplu e-posta arasındaki fark nedir?" Bu konuda farklılık açıklanmıştır ve EOP'de kullanılabilen denetimler açıklanmıştır.

- **Gereksiz e-posta** , talep edilmemiş ve evrensel olarak istenmeyen iletiler olan (doğru tanım olduğunda) istenmeyen e-postadır. Varsayılan olarak, EOP istenmeyen postaları kaynak e-posta sunucusunun itibarına dayanarak reddeder. Bir ileti kaynak IP incelemesini geçerse, istenmeyen posta filtrelemeye gönderilir. İleti istenmeyen posta filtresiyle istenmeyen posta olarak sınıflandırılmışsa, ileti varsayılan olarak hedeflenen alıcılara teslim edilir ve Gereksiz E-posta klasörüne taşınır.

  - İstenmeyen posta filtreleme kararlarını alacak eylemleri yapılandırabilirsiniz. Yönergeler için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

  - İstenmeyen posta filtreleme kararını kabul ediyorsanız, İletileri ve dosyaları Microsoft'a bildirme konusunda açıklandığı gibi, istenmeyen posta veya istenmeyen posta değil olarak değerlendirilen iletileri Microsoft'a çeşitli yollarla [bildirebilirsiniz](report-junk-email-messages-to-microsoft.md).

- **Toplu e-postayı** ( _gri posta olarak_ da bilinir) sınıflandırmak daha zordur. İstenmeyen posta sürekli bir tehdittir, ancak toplu e-posta çoğunlukla tek seferlik reklamlar veya pazarlama iletileridir. Bazı kullanıcılar toplu e-posta iletilerini (aslında bu iletileri almak için bilerek oturum açık olarak) isterken, diğer kullanıcılar toplu e-postanın istenmeyen posta olduğunu düşünün. Örneğin, bazı kullanıcılar Contoso Corporation'dan reklam iletileri veya siber güvenlik için yaklaşan bir konferans davetleri almak isterken, diğer kullanıcılar da aynı iletilerin istenmeyen posta olduğunu düşünün.

  Toplu e-postanın nasıl tanım olduğu hakkında daha fazla bilgi için bkz. [EOP'de toplu şikayet düzeyi (BCL).](bulk-complaint-level-values.md)

## <a name="how-to-manage-bulk-email"></a>Toplu e-postayı yönetme

Toplu e-postaya karışık tepki nedeniyle, her kuruluş için geçerli evrensel kılavuz yok.

İstenmeyen posta önleme tanımları, toplu e-postaları istenmeyen posta olarak tanımlamak için kullanılan varsayılan bir BCL eşiğine sahip olur. Yöneticiler eşiği artırabilir veya azaltabilir. Daha fazla bilgi için, aşağıdaki konulara bakın:

- [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

- [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Kolayca gözden kaçırılabilir bir diğer seçenek daha: Kullanıcı toplu e-posta alma konusunda şikayet ediyorsa ancak iletileri EOP'de istenmeyen posta filtrelemesini geçen saygın gönderenlerden alıyorsa, toplu e-posta iletisinde aboneliği kaldır seçeneğinin kullanıcı tarafından işaretlenebilir.
