---
title: Adım 1. Uygulama Koruma İlkelerini Uygulama
ms.author: bcarter
author: brendacarter
f1.keywords:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
manager: dougeby
audience: ITPro
ms.topic: article
description: Belirli şirket verilerini diğer uygulamalara kopyalanan ve yapıştırılan belirli şirket verilerini engellemek için, Mobil uygulama korumasını Uygulama Koruma ilkeleriyle (APP) yapılandırabilirsiniz.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 4535e4a05ac8408e57c767999de66c39a4bf0274
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016282"
---
# <a name="step-1-implement-app-protection-policies"></a>Adım 1. Uygulama Koruma İlkelerini Uygulama

Intune Uygulama Koruma ilkeleri (APP), bazen Mobil Uygulama Yönetimi (MAM) olarak da adlandırılır ve cihaz yönetilse bile şirket verilerini korur. Bu sayede, kullanıcıların cihazlarını yönetime "kaydetme" için sahip olduğu (BYO) ve kişisel cihazları iş yerinde etkinleştirebilirsiniz. Uygulama Koruma ilkeleri, belirttiğiniz uygulamalarda yer alan şirket verilerinin cihaz'daki diğer uygulamalara kopyalanamaz ve yapıştırılamay olduğundan emin olur.

![Uygulama koruma ilkeleri oluşturma adımları](../media/devices/intune-app-steps.png#lightbox)

Bu şekilde:
- Uygulama ile Intune, kuruluş verilerinizle kişisel verileriniz arasında bir duvar oluşturur. Uygulama koruma ilkeleri, hangi uygulamaların verilerinize erişmesine izin verilmiyor? tanımlar.
- Kullanıcı kuruluş kimlik bilgileriyle oturum açasa bile, Intune, kuruluş verilerinizin kişisel uygulamalara kopyalayıp yapıştır kopyasını engellemek ve bu verilere PIN erişimi gerektirmek için uygulama katmanında bir ilke uygular.
- Uygulama Koruma ilkesi oluşturdukktan sonra, koşullu erişim ilkesiyle veri korumasını zorunlu kılındı. 

Bu yapılandırma, kullanıcı deneyimini neredeyse hiç etkilemeden güvenlik sorunlarınızı büyük ölçüde artırır.  Çalışanlar iyi tanır ve Office Microsoft Teams gibi uygulamaları kullanabilir; aynı zamanda da kuruluş, uygulamalar ve cihazlar içinde bulunan verileri koruyabilir.

Koruma gereken özel İş Hattı uygulamalarına sahipsiniz, şu anda bu uygulamalarla APP'i etkinleştirmek için uygulama kaydırma aracını kullanabilirsiniz. Veya Intune App SDK'yı kullanarak tümleştirebilirsiniz. Uygulama koruma ilkeleri uygulamanıza uygulandığında, Intune tarafından yönetilebilir ve Intune tarafından yönetilen uygulama olarak tanınır. Intune kullanarak İş Hattı uygulamalarınızı koruma hakkında daha fazla bilgi için bkz. yeni uygulamayla uygulamaları [mobil uygulama yönetimine Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Mobil uygulama korumasını yapılandırma

Bu kılavuz, önerilen Sıfır Güven kimliği ve cihaz erişim [ilkeleri ile sıkı bir şekilde eşgüdüm sağlar](../security/office-365-security/microsoft-365-policies-configurations.md). Intune'da Mobil Uygulama koruma ilkelerini oluşturdukktan sonra, azure AD'de mobil uygulama korumasını zorunlu kılan koşullu erişim ilkelerini yapılandırmak için kimlik ekibimizle birlikte çalışabilirsiniz. 

Bu çizimde iki ilke vurgulanır (ayrıca, çizimin altındaki tabloda da açıklanmıştır).

[![Sıfır Güven kimliği ve cihaz erişimi ilkeleri](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

Bu ilkeleri yapılandırmak için, Sıfır Güven kimliği ve cihaz erişim ilkeleri içinde öngörülen [önerilen kılavuzu ve ayarları kullanın](../security/office-365-security/microsoft-365-policies-configurations.md). Aşağıdaki tablo, Intune ve Azure AD'de bu ilkeleri yapılandırma yönergelerine doğrudan bağlantı sağlar.


|Adım  |İlkeler  |Daha fazla bilgi  |Lisanslama  |
|---------|---------|---------|---------|
|1   |  [Uygulama Koruma İlkeleri (UYGULAMA) veri korumasını uygulama](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | Platform başına One Intune Uygulama Koruması ilkesi (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 E5        |
|2     | [Onaylanan uygulamalar ve uygulama koruması gerektirme ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  iOS, iPadOS veya Android kullanan telefonlar ve tabletler için mobil uygulama korumasını zorunlular.   |  Microsoft 365 E3 E5       |
| | | | |

## <a name="next-steps"></a>Sonraki adımlar

[2. Adım'a gidin. Intune ile cihazları yönetime kaydettirin](manage-devices-with-intune-enroll.md). 