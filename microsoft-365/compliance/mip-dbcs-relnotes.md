---
title: Microsoft 365 karakter kümesi sürüm notları için uyumluluk desteği
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Çift bayt karakter kümesi desteği için sürüm notları.
ms.openlocfilehash: e87e88b63bf44c7ea4154fa24c05c0e8e252a446
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006758"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Çift byte karakter kümesi sürüm notları desteği

 Microsoft 365 Koruması artık çift byte karakter kümesi dillerini şu dillerde destekler:

- Çince (basitleştirilmiş)
- Çince (geleneksel)
- Korean
- Japanese

Bu destek, hassas bilgi türleri ve anahtar sözcük sözlükleri için kullanılabilir ve veri kaybı önleme (Exchange Online, SharePoint Online, OneDrive İş ve Teams için), İletişim Uyumluluğu, ofis uygulamalarında Otomatik Etiketleme ve Bulut Uygulamaları için Microsoft Defender'a yansıt olacaktır.

## <a name="known-issues"></a>Bilinen sorunlar

- E-postaya eklenen metin dosyası UTF-8 biçimindeyken byte order mark (LIŞ) olmadan olduğunda, e-posta İletişim Uyumluluğu ilkesi tarafından algılanmaz.

- İletişim Uyumluluğu ilkeleri, ilke koşulu için bir tümce girilirse değerleri algılayamaz: "İleti bu sözcüklerden herhangi birini içerir". İlkede belirtilen metin sözcük olarak yazılırsa, algılanmaz; Ancak, bir cümlenin ortasına yazılırsa, algılanmaz.

- Sözlükleri tür bilgisi olarak belirten İletişim Uyumluluğu ilkeleri özel sohbetleri Teams sohbetleri algılamaz.

- Bu aşamada, İletişim Uyumluluğu için aşağıdaki koşullar desteklenmiyor (bu sorunları gelecekte çözmeyi planlıyoruz): 
  - "İleti bu sözcüklerden herhangi birini içeriyor"
  - "İletide bu sözcüklerden hiçbiri yok"
  - "Ek bu sözcüklerden herhangi birini içerir"
  - "Ek bu sözcüklerden herhangi birini içerir"

Bunun yerine, iletiler ve ekler arasındaki desenleri algılayan anahtar sözcük sözlüğüyle özel bir Hassas Bilgi Türü (SIT) oluşturmanızı ve bu özel SIT'i İletişim Uyumluluğu ilkesi koşulu olarak kullanmanızı öneririz.
