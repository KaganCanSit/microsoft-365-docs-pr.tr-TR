---
title: Test ortamınıza yalnızca bulut için kimlik ve cihaz Microsoft 365 önkoşulları
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Yalnızca bulut Microsoft 365 önkoşulları ile kimliği ve cihaz erişimini test etmek için bir kullanıcı ortamı oluşturun.
ms.openlocfilehash: a0d9a50552b981f8595f661330a7c200e1d54f8a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016439"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Test ortamınıza yalnızca bulut için kimlik ve cihaz Microsoft 365 önkoşulları

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

[Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md), Azure Active Directory (Azure AD) ile tümleştirilmiş tüm hizmetlere erişimi korumak için önerilen yapılandırmalar ve koşullu erişim ilkeleridir.

Bu makalede, kimlik ve cihaz erişimi için Microsoft 365 önkoşul olan yapılandırmanın buluttaki gereksinimlerine uyan [](../security/office-365-security/identity-access-prerequisites.md#prerequisites) bir test ortamının nasıl yapılandırıldığından emin olun?

Bu test ortamını ayarlamanın sekiz aşaması vardır:

1. Hafif test ortamınızı oluşturma
2. Adlandırılmış konumları yapılandırma
3. Kendi kendine parola sıfırlamayı yapılandırma
4. Çok faktörlü kimlik doğrulamasını yapılandırma
5. Bilgisayarlara etki alanına katılmış bilgisayarlarda otomatik cihaz Windows etkinleştirme
6. Azure AD parola korumasını yapılandırma 
7. Azure AD Identity Protection'i etkinleştirme
8. Exchange Online Skype Kurumsal Online için modern kimlik doğrulamayı etkinleştirme

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>Aşama 1: Hafif bir test Microsoft 365 oluşturma

Hafif taban [yapılandırma'daki yönergeleri izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
Sonuçta elde edilen yapılandırma şu şekildedir.

![Hafif bir Microsoft 3656 Enterprise ortamıdır.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>Aşama 2: Adlandırılmış konumları yapılandırma

İlk olarak, kurum tarafından kullanılan genel IP adreslerini veya adres aralıklarını belirlersiniz.

Ardından, adresleri veya adres [aralıklarını adlandırılmış konumlar olarak eklemek Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) Konumlar'da adlandırılmış konumları yapılandırma konusunda verilen yönergeleri izleyin. 

## <a name="phase-3-configure-self-service-password-reset"></a>Aşama 3: Self servis parola sıfırlamayı yapılandırma

Parola sıfırlama Test Laboratuvarı [Kılavuzu'nın Aşama 3'lü yönergeleri izleyin](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Belirli bir Azure AD grubunda hesaplar için parola sıfırlamayı etkinleştirerek, bu hesapları Parola sıfırlama **grubuna** ekleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Yalnızca Kullanıcı 2 hesabı için parola sıfırlamayı test edin.

## <a name="phase-4-configure-multi-factor-authentication"></a>Aşama 4: Çok faktörlü kimlik doğrulamasını yapılandırma

Aşağıdaki kullanıcı hesapları [için Multi-Factor Authentication Test Lab Kılavuzu'nın Aşama 2'sinde](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) verilen yönergeleri izleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Yalnızca Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını test etmek.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Aşama 5: Etki alanına katılmış veya bilgisayarlara otomatik cihaz Windows etkinleştirme 

Etki [alanına katılmış](/azure/active-directory/devices/hybrid-azuread-join-plan) bilgisayarlarda otomatik cihaz kaydını etkinleştirmek için bu Windows izleyin.

## <a name="phase-6-configure-azure-ad-password-protection"></a>Aşama 6: Azure AD parola korumasını yapılandırma 

Zayıf [parolaları](/azure/active-directory/authentication/concept-password-ban-bad) ve değişkenlerini engellemek için bu yönergeleri izleyin.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>Aşama 7: Azure AD Kimlik Korumasını Etkinleştirme

[Azure AD Kimlik Koruma Test Laboratuvarı Kılavuzu'nın 2. Aşaması'nın yönergelerini izleyin](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Aşama 8: Exchange Online Skype Kurumsal Online için modern kimlik doğrulamayı etkinleştirme

Daha Exchange Online için bu [yönergeleri izleyin](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

Skype Kurumsal Online için:

1. Bağlan [Online'Skype Kurumsal edin](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Bu komutu çalıştırın.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Değişikliğin bu komutla başarılı olduğunu doğrulayın.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Sonuç, kimlik ve cihaz erişimi için yalnızca bulut önkoşullu yapılandırmasının [gereksinimlerini](../security/office-365-security/identity-access-prerequisites.md#prerequisites) karşılamaya uygun bir test ortamıdır. 

## <a name="next-step"></a>Sonraki adım

[Önkoşulları temel alan ilkeleri](../security/office-365-security/identity-access-policies.md) yapılandırmak ve kimlikleri ve cihazları korumak için Ortak kimlik ve cihaz erişimi ilkelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Ek kimlik Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md#identity)

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
