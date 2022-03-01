---
title: Azure Active Directory kurulum kılavuzları
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Kurulum kılavuzları hakkında bilgi Azure Active Directory.
ms.openlocfilehash: 0150e88f6e5fc4f7a77ecfcecbc61395bf015c51
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018871"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory kurulum kılavuzları

Azure Active Directory (Azure AD) özellikleri, organizasyonlarınızı yönetmenize ve güvenliklerini sağlamanıza yardımcı olur. Bu kurulum kılavuzları, bu özellikleri basit bir yolla tümleştirin. Aşağıdaki bölümlerde, kurulum kılavuzlarına ilişkin kısa bir açıklama ve kılavuzların bağlantılarını paylaşacağız.

## <a name="who-are-these-setup-guides-for"></a>Who kılavuzlar ne için?

Bu kurulum kılavuzları, genellikle özel bir kimlik ekibine sahip olmayan küçük ve orta ölçekli kuruluşlara yönelik tasarlanmıştır. Bunları kullanmak için kimlik uzmanı olmak zorunda değilsiniz.

## <a name="what-to-expect-and-what-youll-need"></a>Neler beklemeli ve nelere ihtiyacınız var?

Kurulum kılavuzları, Azure AD'nin temel işlevlerini yapılandırmanıza yardımcı olur. Daha gelişmiş bir yapılandırma kurmanız gerekirse, kurulum kılavuzu sizi Azure AD portalında uygun konuma yönlendirecek.

### <a name="required-permissions"></a>Gerekli izinler

Aşağıdaki yönetici rollerinin üyesi olmak gerekir:

- Genel yönetici: Kurulum kılavuzlarında tümleşik araçları kullanarak kuruluş içinde değişiklikler Microsoft 365 sağlar.

- Genel okuyucu: Kurulum kılavuzlarını görüntülemenize olanak sağlar, ancak kiracınızı değişiklik yapmaz.

## <a name="azure-active-directory-deployment"></a>Azure Active Directory dağıtımı  

Aşağıdaki Azure Active Directory kılavuzu, en yaygın Azure AD özelliklerini önerilen bir sırada ayarlamanıza yardımcı olur. Kurulum kılavuzu üç bölüme ayrılır: **İlk**, **Çekirdek** ve **Gelişmiş**. Her bölümde, açması gereken bir özellik kümesi önerilir.

Kurulum kılavuzları tamamlamanız gereken görevlerin denetim listesini içerir ve kılavuzlar arasında ilerleken ilerlemenizi izleyebilirsiniz. Ayrıca kılavuzlar, gerektiğinde diğer kurulum kılavuzlarına da bağlantı sağlar.

[Kurulum Azure Active Directory açın](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Microsoft hesabınıza kullanıcı ekleme veya eşitleme  

Bu kılavuz, Azure ve Microsoft 365'te kullanıcı hesaplarınız kurulumunu aluymanıza yardımcı Microsoft 365. Ortamınıza ve ihtiyaçlarınıza bağlı olarak, kullanıcıları tek tek eklemeyi, Azure AD bulut eşitlemesi ile şirket içi dizininizi geçirmeyi veya Azure AD ad Bağlan geçirmeyi ya da mevcut eşitleme sorunlarını gidermeyi seçebilirsiniz.

[Kullanıcı ekleme veya eşitleme kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183349).

### <a name="licensing"></a>Lisanslama

Eşitleme Azure Active Directory araçları ücretsizdir ve tüm aboneliklere Microsoft 365 dahildir.

## <a name="azure-self-service-password-reset-sspr-guide"></a>Azure Self-Service parola sıfırlama (SSPR) kılavuzu

Bu kurulum kılavuzu, self servis parola sıfırlamayı etkinleştirmeye ve yapılandırmanıza yardımcı olmak için tasarlanmıştır. Kurulum kılavuzu, parola geri yazma ve yönetici bildirimleri gibi önerilen seçeneklerde size yol sunar.

### <a name="licensing"></a>Lisanslama

SSPR için aşağıdaki lisanslardan biri gerekir:

- Azure Active Directory P1 veya P2

- Microsoft 365 Business Premium

- Microsoft 365 Kurumsal E3 veya E5  

- Enterprise Mobil Kullanım ve Güvenlik E3 veya E5

[Self servis parola sıfırlama kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Çok faktörlü kimlik doğrulaması (MFA)

Bu kılavuz, geçerli MFA durumunu sağlar ve IT yöneticilerinin kuruluşlarının gereksinimlerini karşılayacak en iyi MFA seçeneğini seçmelerine yardımcı olur. Ardından, kuruluş için seçilen MFA yöntemini yapılandırma ve zorlama konusunda yardımcı olabiliriz.

### <a name="licensing"></a>Lisanslama

Koşullu Erişim için Azure Active Directory P1 veya P2 lisansı gerekir; güvenlik varsayılanları ve kullanıcı başına MFA ücretsizdir ve tüm Microsoft 365 dahildir.

[Multi-Factor Authentication (MFA) kılavuzunu açma](https://go.microsoft.com/fwlink/?linkid=2183506)

### <a name="the-passwordless-setup-guide"></a>Parolasız kurulum kılavuzu

Parolasız kurulum kılavuzu, ortamınız için en iyi parolasız yöntemi belirlemenize yardımcı olacak şekilde tasarlanmıştır. Bu yöntemler güvenlik anahtarlarını, Windows Hello İş'i ve Microsoft Authenticator içerir. Öneriniz İş Windows Hello ise, farklı seçeneklerde size yol kılavuzunun olduğu bir bölüm vardır. Kılavuz, adım adım bir plan hazırlarken size sorular sorar.

[Parolasız kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183427).
