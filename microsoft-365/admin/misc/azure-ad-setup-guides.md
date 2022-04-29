---
title: kurulum kılavuzlarını Azure Active Directory
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Azure Active Directory kurulum kılavuzları hakkında bilgi edinin.
ms.openlocfilehash: 58f7ed9a20580db742a773cb8a7874137f0cfc4c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128422"
---
# <a name="azure-active-directory-setup-guides"></a>kurulum kılavuzlarını Azure Active Directory

Azure Active Directory (Azure AD) özellikleri kuruluşunuzu yönetmenize ve güvenliğini sağlamanıza yardımcı olur. Bu kurulum kılavuzları, bu özellikleri basit bir şekilde tümleştirmenize yardımcı olur. Aşağıdaki bölümlerde kurulum kılavuzlarını kısaca açıklayacağız ve kılavuzların bağlantılarını paylaşacağız.

## <a name="who-are-these-setup-guides-for"></a>Bu kurulum kılavuzları Who için?

Bu kurulum kılavuzları, genellikle adanmış bir kimlik ekibine sahip olmayan küçük ve orta ölçekli kuruluşlar için tasarlanmıştır. Bunları kullanmak için kimlik uzmanı olmanız gerekmez.

## <a name="what-to-expect-and-what-youll-need"></a>Ne bekleyebileceğiniz ve neye ihtiyacınız olacak?

Kurulum kılavuzları, Azure AD temel işlevselliğini yapılandırmanıza yardımcı olur. Daha gelişmiş bir yapılandırma ayarlamanız gerekirse kurulum kılavuzu sizi Azure AD portalında uygun konuma yönlendirir.

### <a name="required-permissions"></a>Gerekli izinler

Aşağıdaki yönetim rollerinin üyesi olmanız gerekir:

- Genel yönetici: Microsoft 365 kuruluşunuzda değişiklik yapmak için kurulum kılavuzlarındaki tümleşik araçları kullanmanıza olanak tanır.

- Genel okuyucu: Kurulum kılavuzlarını görüntülemenize izin verir, ancak kiracınızda değişiklik yapmanıza izin vermez.

## <a name="identity-security-for-teams"></a>Teams için kimlik güvenliği

Azure Active Directory (Azure AD), çalışanlarınızın oturum açmasına ve uygulamalara ve hizmetlere erişmesine yardımcı olan bulut tabanlı kimlik ve erişim yönetimi hizmetimizdir.
Bu katalog, kullanıcılarınızın güvende olduğundan ve Teams kullanarak en verimli şekilde zaman geçirmesini sağlamak için kullanabileceğiniz bazı temel güvenlik özelliklerini içerir.

### <a name="licensing"></a>Lisanslama

Bu katalogdaki güvenlik özelliklerini kullanmak için bir Azure Active Directory P2 lisansı gereklidir.

[Teams kataloğu için Kimlik güvenliği'ni açma](https://aka.ms/teamsidentity)

## <a name="identity-governance"></a>Kimlik İdaresi

Bu sihirbaz kataloğu, müşterilere Erişim İncelemeleri (AR), Privileged Identity Management (PIM) ve Yetkilendirme Yönetimi (ELM) dahil olmak üzere Azure Active Directory P2 işlevselliği konusunda yardımcı olmak üzere tasarlanmıştır. PIM ve ELM için, seçilmiş bir belge listesi ve yöneticinin bu işlevselliği yapılandırabileceği Azure Active Directory yönetim merkezine yönelik bir işaretçi sunuyoruz. AR için, yöneticilerin iki şablon arasından seçim yapmasına olanak tanıyan tam otomatik bir deneyim sunuyoruz. Bu şablonlar, grup sahiplerinin tüm Microsoft 365 gruplarında konuk kullanımını onaylamasına olanak tanıyan bir şablon içerir. Bu, müşterilerin bugün kullandığı en önemli ilkedir.  

Ardından, yöneticinin seçtikleri belirli bir grup için konukların gözden geçireni olduğu bir test şablonu sunuyoruz. Kiracının tüm Microsoft 365 grupları konuk kullanıcılarını kapsayan bir gözden geçirmesi zaten varsa, yönetici mevcut gözden geçirmeyi yönetmek için Azure Active Directory yönetim merkezine yönlendirilir ve otomatikleştirilmiş bir deneyim olmaz.

[Kimlik İdaresi kurulum kılavuzunu açma](https://go.microsoft.com/fwlink/p/?linkid=386330)

> [!NOTE]
> Azure Active Directory P2 lisansı, bu katalogdaki güvenlik özelliklerini kullanmak için gereklidir.

## <a name="azure-active-directory-deployment"></a>Azure Active Directory dağıtımı  

Azure Active Directory kurulum kılavuzu, en yaygın Azure AD özelliklerini önerilen sırayla ayarlamanıza yardımcı olur. Kurulum kılavuzu üç bölüme ayrılmıştır: **İlk**, **Çekirdek** ve **Gelişmiş**. Her bölümde açmanız gereken bir özellik kümesi önerilir.

Kurulum kılavuzları, tamamlamanız gereken görevlerin denetim listesini içerir ve kılavuzlarda ilerlerken ilerleme durumunuzu izleyebilirsiniz. Kılavuzlar gerektiğinde diğer kurulum kılavuzlarına da bağlanır.

[Azure Active Directory kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Microsoft hesabınıza kullanıcı ekleme veya eşitleme  

Bu kılavuz, Azure'da ve Microsoft 365 kullanıcı hesaplarını ayarlamanıza yardımcı olur. Ortamınıza ve gereksinimlerinize göre kullanıcıları tek tek eklemeyi, şirket içi dizininizi Azure AD bulut eşitleme veya Azure AD Bağlan ile geçirmeyi veya mevcut eşitleme sorunlarını gidermeyi seçebilirsiniz.

### <a name="licensing"></a>Lisanslama

Azure Active Directory eşitleme araçlarının kullanılması ücretsizdir ve tüm Microsoft 365 aboneliklere dahildir.

[Kullanıcı ekleme veya eşitleme kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="secure-your-cloud-apps-with-single-sign-on-sso"></a>Çoklu Oturum Açma (SSO) ile bulut uygulamalarınızın güvenliğini sağlama

Bu kılavuz, bulut uygulamalarını Microsoft 365 eklemenize yardımcı olmak için tasarlanmıştır. Kılavuzumuzda kiracınıza bir uygulama ekleyebilir, uygulamaya kullanıcı ekleyebilir, roller atayabilir ve daha fazlasını yapabilirsiniz.  Uygulama Tek Sign-On (SSO) destekliyorsa, bu yapılandırmada size de yol gösteririz.

### <a name="licensing"></a>Lisanslama

Microsoft 365 için her ücretli abonelik, Azure AD için ücretsiz bir abonelikle birlikte gelir. uygulamalarınızı yönetmek, kullanıcı ve grup hesapları oluşturup yönetmek için Azure AD kullanabilirsiniz.

[Microsoft 365 kurulum kılavuzuna bulut uygulaması ekleme kılavuzunu açın](https://aka.ms/AzureAppSetup)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Azure Self-Service parola sıfırlama (SSPR) kılavuzu

Bu kurulum kılavuzu self servis parola sıfırlamayı etkinleştirmenize ve yapılandırmanıza yardımcı olmak için tasarlanmıştır. Kurulum kılavuzu, parola geri yazma ve yönetici bildirimleri de dahil olmak üzere önerilen seçeneklerde size yol gösterir.

### <a name="licensing"></a>Lisanslama

SSPR aşağıdaki lisanslardan birini gerektirir:

- P1 veya P2 Azure Active Directory

- Microsoft 365 Business Premium

- E3 veya E5 Microsoft 365 Kurumsal  

- Enterprise Mobility ve Security E3 veya E5

[Self servis parola sıfırlama kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Çok faktörlü kimlik doğrulaması (MFA)

Bu kılavuz geçerli MFA durumunu sağlar ve BT yöneticilerinin kuruluş gereksinimlerini karşılayan en iyi MFA seçeneğini belirlemesine yardımcı olur. Ardından kuruluş için seçilen MFA yöntemini yapılandırma ve zorunlu tutma konusunda yardımcı olacağız.

### <a name="licensing"></a>Lisanslama

Koşullu Erişim Azure Active Directory P1 veya P2 lisansı gerektirir, güvenlik varsayılanları ve kullanıcı başına MFA ücretsizdir ve tüm Microsoft 365 aboneliklerine dahildir.

[Çok faktörlü kimlik doğrulama (MFA) kılavuzunu açma](https://go.microsoft.com/fwlink/?linkid=2183506)

## <a name="the-passwordless-setup-guide"></a>Parolasız kurulum kılavuzu

Parolasız kurulum kılavuzu, ortamınız için en iyi parolasız yöntemi belirlemenize yardımcı olacak şekilde tasarlanmıştır. Yöntemler güvenlik anahtarlarını, İş İçin Windows Hello ve Microsoft Authenticator uygulamasını içerir. Öneri İş İçin Windows Hello ise, farklı seçeneklerde size yol gösteren bir bölüm vardır. Kılavuz, adım adım plan oluşturmanıza yardımcı olacak sorular sorar.

### <a name="licensing"></a>Lisanslama

Microsoft 365 için her ücretli abonelik, Azure AD için ücretsiz bir abonelikle birlikte gelir. uygulamalarınızı yönetmek, kullanıcı ve grup hesapları oluşturup yönetmek için Azure AD kullanabilirsiniz.

[Parolasız kurulum kılavuzunu açın](https://go.microsoft.com/fwlink/?linkid=2183427).
