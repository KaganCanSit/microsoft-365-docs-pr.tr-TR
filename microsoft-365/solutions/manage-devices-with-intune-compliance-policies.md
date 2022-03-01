---
title: Adım 3. Intune ile cihazlar için uyumluluk ilkeleri ayarlama
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Bir cihazın ortamınıza erişmesi için en düşük gereksinimleri belirten cihaz uyumluluk ilkelerinin nasıl oluşturulacaklarını öğrenin.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 7e55ad6bf1d1cb7d95e43cb23b9c74decc8548df
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016277"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Adım 3. Intune ile cihazlar için uyumluluk ilkeleri ayarlama

Cihazları yönetime kaydetmek, ortamınız içinde daha fazla güvenlik ve denetim elde etme olanağı sağlar. [2. Adım. Cihazları Intune](manage-devices-with-intune-enroll.md) ve AutoPilot kullanarak bunu nasıl gerçekleştirebilirsiniz yönetim ayrıntılarına kaydettirin. Bu makale, cihaz uyumluluk ilkelerini yapılandırmak için sonraki adımı kapsar. 

![Cihazları yönetme adımları](../media/devices/intune-mdm-step-2.png#lightbox)

Uygulamalarınıza ve verilerinize erişen cihazların parola veya pin korumalı gibi minimum gereksinimleri karşı olduğundan ve işletim sisteminin güncel olduğundan emin olmak istiyor olun. Uyumluluk ilkeleri, cihazların karşılaması gereken gereksinimleri tanımlamanın yoludur. MEM, bir cihazı uyumlu veya uyumlu olmayan olarak işaretlemek için bu uyumluluk ilkelerini kullanır Bu ikili durum, cihazın kaynaklara erişmesine izin vermek veya bunu engellemek için koşullu erişim kurallarında bu durumu kullanabileceği Azure AD'ye geçirilir. 

## <a name="configuring-device-compliance-policies"></a>Cihaz uyumluluk ilkelerini yapılandırma

Bu kılavuz, önerilen Sıfır Güven kimliği ve cihaz erişim [ilkeleri ile sıkı bir şekilde eşgüdüm sağlar](../security/office-365-security/microsoft-365-policies-configurations.md).

Bu çizimde, uyumluluk ilkelerini tanımlama çalışması genel Olarak Sıfır Güveni önerilen ilke kümesine nereye sığıyor vurgulanır. 

[![Sıfır Güven kimliği ve cihaz erişimi ilkeleri](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

Bu çizimde, cihaz uyumluluk ilkelerini tanımlama, Sıfır Güven çerçevesi içinde önerilen koruma düzeyine ulaşmak için bir bağımlılıktır. 

Cihaz uyumluluk ilkelerini yapılandırmak için, Sıfır Güven kimliği ve cihaz erişim ilkeleri içinde öngörülen [önerilen kılavuzu ve ayarları kullanın](../security/office-365-security/microsoft-365-policies-configurations.md). Aşağıdaki tablo, her bir platform için önerilen ayarlar da dahil olmak üzere, doğrudan Intune'da bu ilkeleri yapılandırma yönergelerine bağlantı sağlar.


|İlkeler |Daha fazla bilgi  |Lisanslama |
|---------|---------|---------|
|[Cihaz uyumluluk ilkelerini tanımlama ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Her platform için bir ilke       |  Microsoft 365 E3 E5       |
|  |         |         |

## <a name="next-steps"></a>Sonraki adımlar

[4. Adım'a gidin. Azure AD'de koşullu](manage-devices-with-intune-require-compliance.md) erişim kuralı oluşturma yönergeleri için sağlıklı ve uyumlu cihazlara gerektir.