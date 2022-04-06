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
ms.openlocfilehash: 2de0e67c78ac558f4bdc2648790e49fad86e3178
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595070"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Çift byte karakter kümesi sürüm notları desteği

 Microsoft 365 Information Protection artık çift byte karakter kümesi dillerini destekler:

- Çince (basitleştirilmiş)
- Çince (geleneksel)
- Korean
- Japanese

Bu destek hassas bilgi türleri ve anahtar sözcük sözlükleri için kullanılabilir ve veri kaybı önleme (Exchange Online, SharePoint Online, OneDrive İş ve Teams için), İletişim Uyumluluğu, Ofis uygulamaları ve Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Bilinen sorunlar

- E-postaya eklenmiş bir metin dosyası, byte order mark (LIŞ) olmadan UTF-8 biçiminde olduğunda, e-posta İletişim Uyumluluğu ilkesi tarafından algılanmaz.

- İletişim Uyumluluğu ilkeleri, ilke koşulu için bir tümce girilirse değerleri algıamaz: "İleti şu sözcüklerden herhangi birini içeriyor". İlkede belirtilen metin sözcük olarak yazılırsa, algılanmaz; Ancak, bir cümlenin ortasına yazılmışsa, algılanmaz.

- Sözlükleri tür bilgisi olarak belirten İletişim Uyumluluğu ilkeleri özel sohbetleri Teams sohbetleri algılamaz.

- Bu aşamada, İletişim Uyumluluğu için aşağıdaki koşullar desteklenmiyor (bu sorunları gelecekte çözmeyi planlıyoruz): 
  - "İleti bu sözcüklerden herhangi birini içeriyor"
  - "İletide bu sözcüklerden hiçbiri yok"
  - "Ek bu sözcüklerden herhangi birini içerir"
  - "Ek bu sözcüklerden herhangi birini içerir"

- Veri kaybı önleme ilkeleri, Japonca dahil olmak üzere Doğu Asya dilleri için aşağıda belirtilen koşullar dışında Catalina 10.15 ve daha yüksek sürümü çalıştıran macOS cihazlarında (önizleme) zorunlu kılınabilir.
  - Japonya banka hesap numarası gibi yerleşik şablon kullanımı gibi tam genişlikli numaralar algılanmaz
  - Sınırlayıcı olmayan sayılar algılanmaz
  - Yarım genişlikli bir alanla ayrılan anahtar sözcükler hassas bir bilgi türü için algılanmaz. Örneğin: Japonca sözcük hassas bilgi türünde ayarlanmıştır ve bir tümce içinde yer alan sözlük algılanmaz
  - İngilizce ve Japonca (東京2020) içeren sözcükler algılanmaz

Bunun yerine, iletiler ve ekler arasındaki desenleri algılayan anahtar sözcük sözlüğüyle özel bir Hassas Bilgi Türü (SIT) oluşturmanızı ve bu özel SIT'i İletişim Uyumluluğu ilkesi koşulu olarak kullanmanızı öneririz.
