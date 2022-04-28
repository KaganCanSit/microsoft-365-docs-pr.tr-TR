---
title: Yalnızca Microsoft 365 test ortamınızda bulut için kimlik ve cihaz erişimi önkoşulları
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Yalnızca bulut kimlik doğrulaması önkoşullarıyla kimlik ve cihaz erişimini test etmek için bir Microsoft 365 ortamı oluşturun.
ms.openlocfilehash: 88138600e516412b74c38234647147197742f2de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097524"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Yalnızca Microsoft 365 test ortamınızda bulut için kimlik ve cihaz erişimi önkoşulları

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

[Kimlik ve cihaz erişim yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md), Azure Active Directory (Azure AD) ile tümleştirilen tüm hizmetlere erişimi korumak için önerilen yapılandırmalar ve koşullu erişim ilkeleri kümesidir.

Bu makalede, kimlik ve cihaz erişimi için [yalnızca bulut önkoşul yapılandırmasının](../security/office-365-security/identity-access-prerequisites.md#prerequisites) gereksinimlerini karşılayan bir Microsoft 365 test ortamının nasıl yapılandırıldığı açıklanır.

Bu test ortamını ayarlamak için sekiz aşama vardır:

1. Basit test ortamınızı oluşturma
2. Adlandırılmış konumları yapılandırma
3. Self servis parola sıfırlamayı yapılandırma
4. Çok faktörlü kimlik doğrulamasını yapılandırma
5. Etki alanına katılmış Windows bilgisayarların otomatik cihaz kaydını etkinleştirme
6. Azure AD parola korumasını yapılandırma 
7. Azure AD Kimlik Koruması'nı etkinleştirme
8. Exchange Online ve Skype Kurumsal Online için modern kimlik doğrulamasını etkinleştirme

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>1. Aşama: Basit Microsoft 365 test ortamınızı oluşturun

[Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
Sonuçta elde edilen yapılandırma aşağıdadır.

![Basit Microsoft 3656 Enterprise test ortamı.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>2. Aşama: Adlandırılmış konumları yapılandırma

İlk olarak, kuruluşunuz tarafından kullanılan genel IP adreslerini veya adres aralıklarını belirleyin.

Ardından, adresleri veya adres [aralıklarını adlandırılmış konumlar olarak eklemek için Azure Active Directory'de](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) adlandırılmış konumları yapılandırma başlığı altında verilen yönergeleri izleyin. 

## <a name="phase-3-configure-self-service-password-reset"></a>3. Aşama: Self servis parola sıfırlamayı yapılandırma

[Parola sıfırlama Test Laboratuvarı Kılavuzu'nun 3. Aşamasındaki](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset) yönergeleri izleyin. 

Belirli bir Azure AD grubundaki hesaplar için parola sıfırlamayı etkinleştirirken bu hesapları **Parola sıfırlama** grubuna ekleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Parola sıfırlamayı yalnızca Kullanıcı 2 hesabı için test edin.

## <a name="phase-4-configure-multi-factor-authentication"></a>4. Aşama: Çok faktörlü kimlik doğrulamasını yapılandırma

Aşağıdaki kullanıcı hesapları için [çok faktörlü kimlik doğrulaması Test Laboratuvarı Kılavuzu'nun 2. Aşamasındaki](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) yönergeleri izleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Çok faktörlü kimlik doğrulamasını yalnızca Kullanıcı 2 hesabı için test edin.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>5. Aşama: Etki alanına katılmış Windows bilgisayarların otomatik cihaz kaydını etkinleştirme 

Etki alanına katılmış Windows bilgisayarların otomatik cihaz kaydını etkinleştirmek için [bu yönergeleri](/azure/active-directory/devices/hybrid-azuread-join-plan) izleyin.

## <a name="phase-6-configure-azure-ad-password-protection"></a>6. Aşama: Azure AD parola korumasını yapılandırma 

Bilinen zayıf parolaları ve bunların değişkenlerini engellemek için [bu yönergeleri](/azure/active-directory/authentication/concept-password-ban-bad) izleyin.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>7. Aşama: Azure AD Kimlik Koruması'nı etkinleştirme

[Azure AD Kimlik Koruması Test Laboratuvarı Kılavuzu'nun 2. Aşamasındaki](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection) yönergeleri izleyin. 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>8. Aşama: Exchange Online ve Skype Kurumsal Online için modern kimlik doğrulamasını etkinleştirme

Exchange Online için [bu yönergeleri](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later) izleyin. 

Skype Kurumsal Online için:

1. Skype Kurumsal [Online'a Bağlan](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Bu komutu çalıştırın.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Bu komutla değişikliğin başarılı olduğunu doğrulayın.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Sonuç, kimlik ve cihaz erişimi için [yalnızca bulut önkoşul yapılandırmasının](../security/office-365-security/identity-access-prerequisites.md#prerequisites) gereksinimlerini karşılayan bir test ortamıdır. 

## <a name="next-step"></a>Sonraki adım

[Önkoşulları oluşturan ilkeleri yapılandırmak ve](../security/office-365-security/identity-access-policies.md) kimlikleri ve cihazları korumak için Ortak kimlik ve cihaz erişim ilkelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Ek kimlik Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md#identity)

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)
