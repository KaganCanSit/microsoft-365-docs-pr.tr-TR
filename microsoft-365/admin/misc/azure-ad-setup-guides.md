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
ms.openlocfilehash: 059890bd6a79ced1f7121e973b070790dffd8db9
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403621"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory kurulum kılavuzları

Azure Active Directory (Azure AD) özellikleri, organizasyonlarınızı yönetmenize ve güvenliklerini sağlamanıza yardımcı olur. Bu kurulum kılavuzları, bu özellikleri basit bir yolla tümleştirin. Aşağıdaki bölümlerde, kurulum kılavuzlarını kısaca açıklarız ve kılavuzların bağlantılarını paylaşacağız.

## <a name="who-are-these-setup-guides-for"></a>Who kılavuzlar ne için?

Bu kurulum kılavuzları, genellikle özel bir kimlik ekibine sahip olmayan küçük ve orta ölçekli kuruluşlara yönelik tasarlanmıştır. Bunları kullanmak için kimlik uzmanı olmak zorunda değilsiniz.

## <a name="what-to-expect-and-what-youll-need"></a>Neler beklemeli ve nelere ihtiyacınız var?

Kurulum kılavuzları, Azure AD'nin temel işlevlerini yapılandırmanıza yardımcı olur. Daha gelişmiş bir yapılandırma kurmanız gerekirse, kurulum kılavuzu sizi Azure AD portalında uygun konuma yönlendirecek.

### <a name="required-permissions"></a>Gerekli izinler

Aşağıdaki yönetim rollerinin üyesi olmak gerekir:

- Genel yönetici: Kurulum kılavuzlarında, kuruluş içinde veya farklı kuruluşlarda değişiklik yapmak için tümleşik araçları Microsoft 365 sağlar.

- Genel okuyucu: Kurulum kılavuzlarını görüntülemenize olanak sağlar, ancak kiracınızı değişiklik yapmaz.

## <a name="identity-security-for-teams"></a>Kimlik yönetimi için Teams

Azure Active Directory (Azure AD), çalışanlarının oturum açmalarına ve uygulama ve hizmetlere erişmelerine yardımcı olan bulut tabanlı kimlik ve erişim yönetim hizmetimizdir.
Bu katalog, kullanıcılarınızı güvende olduğundan ve kullanıcılarınızı güvenli bir şekilde kullanırken en üretken zamanları için kullanabileceğiniz bazı temel güvenlik Teams.

### <a name="licensing"></a>Lisanslama

Bu Azure Active Directory güvenlik özelliklerini kullanmak için bir P2 lisansı gereklidir.

[Teams için Identity security Teams açma](https://aka.ms/teamsidentity)

## <a name="azure-active-directory-deployment"></a>Azure Active Directory dağıtımı  

Aşağıdaki Azure Active Directory kılavuzu, en yaygın Azure AD özelliklerini önerilen bir sırada ayarlamanıza yardımcı olur. Kurulum kılavuzu üç bölüme ayrılır: **İlk**, **Çekirdek** ve **Gelişmiş**. Her bölümde, açması gereken bir özellik kümesi önerilir.

Kurulum kılavuzları tamamlamanız gereken görevlerin denetim listesini içerir ve kılavuzlar arasında ilerleken ilerlemenizi izleyebilirsiniz. Ayrıca kılavuzlar, gerektiğinde diğer kurulum kılavuzlarına da bağlantı sağlar.

[Kurulum Azure Active Directory açın](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Microsoft hesabınıza kullanıcı ekleme veya eşitleme  

Bu kılavuz, Azure ve Microsoft 365'de kullanıcı hesaplarının kurulumunu Microsoft 365. Ortamınıza ve ihtiyaçlarınıza bağlı olarak, kullanıcıları tek tek eklemeyi, Azure AD bulut eşitlemesi ile şirket içi dizininizi geçirmeyi veya Azure AD ad Bağlan geçirmeyi ya da mevcut eşitleme sorunlarını gidermeyi seçebilirsiniz.

### <a name="licensing"></a>Lisanslama

Eşitleme Azure Active Directory araçları ücretsizdir ve tüm aboneliklere Microsoft 365 dahildir.

[Kullanıcı ekleme veya eşitleme kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="add-a-cloud-app-to-microsoft-365"></a>Web sitenize bulut uygulaması Microsoft 365 

Bu kılavuz, uygulamalarınıza bulut uygulamaları eklemenize yardımcı olmak Microsoft 365. Kılavuzumuza göre kiracınıza uygulama ekleyebilir, uygulamaya kullanıcı ekleyebilir, roller atayabilirsiniz ve daha fazlasını.  Uygulama Tek Kullanıcılı (SSO) Sign-On, bu yapılandırmada size yol gösteririz.

### <a name="licensing"></a>Lisanslama

Microsoft 365 abonelikleri, ücretsiz bir Azure AD aboneliğiyle birlikte gelir. Uygulamalarınızı yönetmek, kullanıcı ve grup hesaplarını oluşturmak ve yönetmek için Azure AD'i kullanabilirsiniz.

[Kurulum kılavuzu için Bulut uygulaması Microsoft 365 açma](https://aka.ms/AzureAppSetup)

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

## <a name="the-passwordless-setup-guide"></a>Parolasız kurulum kılavuzu

Parolasız kurulum kılavuzu, ortamınız için en iyi parolasız yöntemi belirlemenize yardımcı olacak şekilde tasarlanmıştır. Bu yöntemler güvenlik anahtarlarını, İş İçin Windows Hello ve Microsoft Authenticator içerir. Öneriniz doğru İş İçin Windows Hello, farklı seçeneklerde size yol kılavuzunun olduğu bir bölüm vardır. Kılavuz, adım adım bir plan hazırlarken size sorular sorar.

### <a name="licensing"></a>Lisanslama

Microsoft 365 abonelikleri, ücretsiz bir Azure AD aboneliğiyle birlikte gelir. Uygulamalarınızı yönetmek, kullanıcı ve grup hesaplarını oluşturmak ve yönetmek için Azure AD'i kullanabilirsiniz.

[Parolasız kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183427).
