---
title: Adım 1. Hazırlık Microsoft 365 Defender planlama
description: Çalışmanızı güvenlik Microsoft 365 Defender tümleştirerek bu işlemlerin hazırlık Microsoft 365 Defender planlamanın temelleri.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 45abe5dfa77e9ed224f2d55e15986eba732f2aff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326447"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Adım 1. Hazırlık Microsoft 365 Defender planlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Güvenlik işlemlerinizin geçerli vade süresi ne olursa olsun, Güvenlik İşlemleri Merkezinize (SOC) uyum içinde çalışmanız önemlidir. Her kuruluşa uyan tek bir model varken, bazı yönler diğer kuruluşlardan daha yaygındır. 

Aşağıdaki bölümlerde SOC'nin temel işlevleri açıklanmaktadır.

## <a name="provide-situational-awareness-of-modern-threats"></a>Modern tehditlere karşı durumsal farkındalık sağlama

SOC ekibi yeni ve gelen tehditlere karşı hazırlanır ve bunun için kuruluşla birlikte çalışarak önlem ve tepkiler kurmasını sağlar. SOC ekibinin modern saldırı yöntemleri ve tekniklerde üst düzeyde eğitim almış ve tehdit tehditlerini anlayacaktır. CK çerçevesi, [Siber Kill Zinciri](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) veya [MITRE ATT&](https://attack.mitre.org/) gibi paylaşılan tehdit zekası ve çerçeveleri personelinizi tehdit analistleri ve tehdit analistleri ile güçlendirin.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Siber olaylara ve olaylara birinci, ikinci ve potansiyel olarak üçüncü düzey yanıtlar sağlama

SOC, güvenlik olayları ve olaylarda savunmanın ön hattıdır. Bir olay, tehdit, saldırı, ilke ihlali veya denetim bulgusu bir uyarıyı veya eylem aramasını tetiklerse, SOC ekibi öncelik belirleme, içerme veya araştırma için bu durumu yükseltme değerlendirmesini yapar. Bu nedenle, SOC ilk satırı yanıtlayanların güvenlik olayları ve göstergeleri hakkında geniş teknik bilgiye sahip olması gerekir.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Kuruluş güvenlik kaynaklarını izleme ve günlüğe kaydetmeyi merkezileştirme 

GENELLIKLE SOC ekibinin temel işlevi, güvenlik duvarları, izinsiz giriş önleme sistemleri, veri kaybı önleme sistemleri, Tehdit ve Güvenlik Açığı Yönetimi sistemleri ve kimlik sistemleri gibi tüm güvenlik cihazlarının düzgün çalışır ve izlenir durumda olduğundan emin olmaktır. SOC ekipleri, güvenlik bilgilerini merkezi ve güvenli hale getirildiklerinden emin olmak için kimlik, DevOps, bulut, uygulama, veri bilimi ve diğer iş ekipleri gibi daha geniş ağ işlemleriyle birlikte çalışır. Buna ek olarak, SOC ekibi verilerin kullanılabilir ve okunabilir biçimlerde günlüklerini korumaktan sorumludur. Bunlar birbirinden ayrı biçimleri ayrıştırma ve normalleştirmeyi içerebilir.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Kırmızı, Mavi ve Mor ekibin faaliyete hazırlığı kurma

Her SOC ekibi bir siber olayı yanıta cevap olarak hazırlığını test edeler. Deneme, tablo topları ve alıştırmalar gibi eğitim alıştırmaları aracılığıyla, IT'de, güvenlikte ve iş düzeyindeki çeşitli bireylerle birlikte yapılabilir. Bireysel eğitim alıştırması ekipleri temsili rollere dayalı olarak oluşturulur ve bir defender (Mavi Ekip), bir saldırgan (Kırmızı Ekip) rolünü oynamaktadır ya da güçlü ve zayıf noktaları kullanarak hem Mavi hem de Kırmızı ekiplerin yöntem ve tekniklerini geliştirmeye çalışan saldırganlar olarak (Mor Takım) ortaya çıkar.

## <a name="next-step"></a>Sonraki adım

[2. Adım. Zero Trust Framework kullanarak SOC tümleştirme hazırlık değerlendirmesini gerçekleştirme](integrate-microsoft-365-defender-secops-readiness.md)
