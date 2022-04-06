---
title: Adım 3. Intune olan cihazlar için uyumluluk ilkelerini ayarlama
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Bir cihazın ortamınıza erişmesi için en düşük gereksinimleri belirten cihaz uyumluluk ilkeleri oluşturmayı öğrenin.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f93642984ecb2439ab6e4ad484ea4f6f3303c0ce
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651377"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Adım 3. Intune olan cihazlar için uyumluluk ilkelerini ayarlama

Cihazları Intune kaydetmek, ortamınızdaki veriler için daha da fazla güvenlik ve denetim elde edebilmenizi sağlar. [2. Adım. Intune](manage-devices-with-intune-enroll.md) kullanarak bunu nasıl gerçekleştireceklerini Intune için cihazları kaydedin. Bu makale, cihaz uyumluluk ilkelerini yapılandırmak için bir sonraki adımı kapsar. 

![Cihazları yönetme adımları](../media/devices/intune-mdm-step-2.png#lightbox)

Uygulamalarınıza ve verilerinize erişen cihazların parola veya pin korumalı olması ve işletim sisteminin güncel olması gibi en düşük gereksinimleri karşıladığından emin olmak istiyorsunuz. Uyumluluk ilkeleri, cihazların karşılaması gereken gereksinimleri tanımlamanın yoludur. MEM, bir cihazı uyumlu veya uyumlu değil olarak işaretlemek için bu uyumluluk ilkelerini kullanır Bu ikili durum Azure AD'ye geçirilir. Bu durum, bir cihazın kaynaklara erişmesine izin vermek veya bunları engellemek için koşullu erişim kurallarında bu durumu kullanabilir. 

## <a name="configuring-device-compliance-policies"></a>Cihaz uyumluluk ilkelerini yapılandırma

Bu kılavuz, önerilen [Sıfır Güven kimlik ve cihaz erişim ilkeleriyle](../security/office-365-security/microsoft-365-policies-configurations.md) sıkı bir şekilde koordine edilir.

Bu çizimde, uyumluluk ilkelerini tanımlama çalışmalarının genel Sıfır Güven önerilen ilke kümesine uygun olduğu vurgulanır. 

[![kimlik ve cihaz erişim ilkelerini Sıfır Güven](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

Bu çizimde cihaz uyumluluk ilkelerinin tanımlanması, Sıfır Güven çerçevesi içinde önerilen koruma düzeyine ulaşmak için bir bağımlılıktır. 

Cihaz uyumluluk ilkelerini yapılandırmak için kimlik ve [cihaz erişim ilkeleri Sıfır Güven](../security/office-365-security/microsoft-365-policies-configurations.md) önerilen kılavuzu ve ayarları kullanın. Aşağıdaki tablo, her platform için önerilen ayarlar da dahil olmak üzere bu ilkeleri Intune yapılandırma yönergelerine doğrudan bağlantı sağlar.


|İlkeler |Daha fazla bilgi  |Lisanslama |
|---------|---------|---------|
|[Cihaz uyumluluk ilkelerini tanımlama ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Her platform için bir ilke       |  Microsoft 365 E3 veya E5       |
|  |         |         |

## <a name="next-steps"></a>Sonraki adımlar

[4. Adım'a gidin. Azure AD'de koşullu erişim kuralı oluşturma yönergeleri için iyi durumda ve uyumlu cihazlar gerektirme](manage-devices-with-intune-require-compliance.md).