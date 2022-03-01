---
title: Adım 4. Intune ile sağlıklı ve uyumlu cihazlar gerektirme
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: Azure AD'de uyumlu cihazlar gerektirmeye yönelik bir koşullu erişim ilkesi oluşturun ve kullanıcılar herhangi bir konumda herhangi bir cihazdan çalışırken şirket verilerini güvende tutabilirsiniz.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
ms.openlocfilehash: 8a953c76a3461b0f6dbf1b3663d5cef41f038371
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016279"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>Adım 4. Intune ile sağlıklı ve uyumlu cihazlar gerektirme

Koşullu Erişim, hizmete erişim izni vermeden önce cihaz durumunun ek doğrulamalarını sağlar. Koşullu Erişim koşulları belirtmedikçe çalışmaz. [3. Adım'da. Uyumluluk ilkeleri ayarlayın,](manage-devices-with-intune-compliance-policies.md) bir cihazın ortamınıza erişmek için karşılaması gereken en düşük gereksinimleri belirten uyumluluk ilkelerini tanımlamış oluruz. Bu makalede, uyumlu cihazlar gerektirmek üzere Azure AD'de ilgili Koşullu Erişim ilkesi oluştursunuz. Bu, kullanıcılara herhangi bir cihazdan ve herhangi bir konumdan çalışma olanağı sağlarken, şirket verilerinizin güvenliğini de korumanıza yardımcı olur.

Cihaz uyumluluk ilkelerini ayardikten ve bunları kullanıcı gruplarına atadikten sonra, Intune cihazın uyumlu olup olmadığını Azure AD'ye haber verir. Bu durumu erişim koşulu olarak kullanmak için, Azure AD yöneticinizle birlikte çalışarak uyumlu bilgisayarlar ve mobil cihazlar gerektiren bir Koşullu Erişim kuralı oluşturabilirsiniz.


![Cihazları yönetme adımları](../media/devices/intune-mdm-step-3.png#lightbox)

Önerilen Sıfır Güven kimliği ve cihaz erişim kuralı kümesi bu kuralı içerir. Aşağıda [gösterildiği gibi, Uyumlu bilgisayar ve](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) mobil cihazlar gerektirme'ye bakın.


[![Sıfır Güven kimliği ve cihaz erişimi ilkeleri](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



Şunları yapmak için emin olun:
- Uyumluluk ilkelerinize atadınız kullanıcı gruplarını Koşullu Erişim ilkesine atanan kullanıcı gruplarıyla eşgüdüm sağlayın.
- Koşullu Erişim ilkesi tümüyle atamadan önce, Durum ve Denetim Modu özelliklerini kullanarak Koşullu Erişim ilkelerinizi test edin. Bu, ilkenin sonuçlarını anlamanıza yardımcı olur.
- Erişilen verilerin ve/veya uygulamanın gizliliğine göre yetkisiz kullanım süresi ayarlayın. 
- Uyumluluk ilkelerinizin yasal düzenlemelere veya diğer uyumluluk gereksinimlerine müdahale etmey olduğundan emin olun. 
- Uyumluluk ilkeleri için cihaz iade aralıklarını anlayabilirsiniz.
- Uyumluluk ilkeleriyle yapılandırma profilleri arasındaki çakışmaları önle. Tercih ettiysanız sonuçları anlıyoruz.

İlkeler arasındaki çakışmalar da dahil olmak üzere Intune'daki cihaz profillerini gidermek için bkz. İlkeler arasındaki çakışmalar dahil olmak üzere sık [sorulan Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

Not: Başlangıç olarak uyumlu bilgisayarlara gerek kalmadan, mobil cihazlar gerektirmeden başlamak için bkz. Uyumlu bilgisayar [gerektirme (](../security/office-365-security/identity-access-policies.md)telefon ve tablet değil) 

## <a name="next-steps"></a>Sonraki adımlar

[5. Adım'a gidin. Mobil cihazda cihaz profillerini Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
