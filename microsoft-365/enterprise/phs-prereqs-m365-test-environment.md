---
title: Test ortamınıza parola karması eşitlemesi için kimlik ve cihaz Microsoft 365 önkoşulları
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
description: Parola Microsoft 365 eşitleme kimlik doğrulamasının önkoşulları ile kimliği ve cihaz erişimini test etmek için bir kullanıcı ortamı oluşturun.
ms.openlocfilehash: fc8ca3288204880810856e79d485305de75f9c27
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014391"
---
# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>Test ortamınıza parola karması eşitlemesi için kimlik ve cihaz Microsoft 365 önkoşulları

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

[Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md), Microsoft 365'de (Azure AD) ile tümleşik olan tüm hizmetlere erişimi korumaya yönelik bir dizi yapılandırma Azure Active Directory koşullu erişim ilkesidir.

Bu makalede, kimlik ve cihaz erişimi için parola Microsoft 365 karma eşitlemesi kimlik doğrulaması önkoşul yapılandırmasıyla karma karma eşitlemenin gereksinimlerini karşılayacak bir test ortamının nasıl yapılandırıldığından emin olunması açıklanmıştır.[](../security/office-365-security/identity-access-prerequisites.md#prerequisites)

Bu test ortamını ayarlamanın on aşaması vardır:

1. Parola karması eşitleme test ortamıyla sanal bir kuruluş oluşturma
2. Azure AD sorunsuz çoklu oturum açma yapılandırma
3. Adlandırılmış konumları yapılandırma
4. Parola geri yazma ayarlarını yapılandırma
5. Tüm kullanıcı hesapları için kendi kendine parola sıfırlamayı yapılandırma
6. Tüm kullanıcı hesapları için çok faktörlü kimlik doğrulamasını yapılandırma
7. Bilgisayarlara etki alanına katılmış bilgisayarlarda otomatik cihaz Windows etkinleştirme
8. Azure AD parola korumasını yapılandırma 
9. Azure AD Identity Protection'i etkinleştirme
10. Exchange Online Skype Kurumsal Online için modern kimlik doğrulamayı etkinleştirme

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>Aşama 1: Test ortamında parola karma eşitlemesi ile benzetimi yapılan Microsoft 365 oluşturma

Parola karması eşitleme [Test Laboratuvarı Kılavuzu'daki](password-hash-sync-m365-ent-test-environment.md) yönergeleri izleyin.
Sonuçta elde edilen yapılandırma şu şekildedir.

![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Aşama 2: Azure AD'yi sorunsuz çoklu oturum açma yapılandırma

[Azure AD Sorunsuz Çoklu Oturum Açma Test Laboratuvarı Kılavuzu'nın Aşama 2'sinde verilen yönergeleri izleyin](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Aşama 3: Adlandırılmış konumları yapılandırma

İlk olarak, kurum tarafından kullanılan genel IP adreslerini veya adres aralıklarını belirlersiniz.

Ardından, adresleri veya adres [aralıklarını adlandırılmış konumlar olarak eklemek Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) Konumlar'da adlandırılmış konumları yapılandırma konusunda verilen yönergeleri izleyin. 

## <a name="phase-4-configure-password-writeback"></a>Aşama 4: Parola geri yazma ayarlarını yapılandırma

Parola geri yazma [Test Laboratuvarı Kılavuzu'nın Aşama 2'sinde verilen yönergeleri izleyin](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Aşama 5: Self servis parola sıfırlamayı yapılandırma

Parola sıfırlama Test Laboratuvarı [Kılavuzu'nın Aşama 3'lü yönergeleri izleyin](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Belirli bir Azure AD grubunda hesaplar için parola sıfırlamayı etkinleştirerek, bu hesapları Parola sıfırlama **grubuna** ekleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Yalnızca Kullanıcı 2 hesabı için parola sıfırlamayı test edin.

## <a name="phase-6-configure-multi-factor-authentication"></a>Aşama 6: Çok faktörlü kimlik doğrulamasını yapılandırma

Aşağıdaki kullanıcı hesapları [için Multi-Factor Authentication Test Lab Kılavuzu'nın Aşama 2'sinde](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) verilen yönergeleri izleyin:

- Kullanıcı 2
- Kullanıcı 3
- Kullanıcı 4
- Kullanıcı 5

Yalnızca Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını test etmek.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Aşama 7: Etki alanına katılmış bilgisayarlarda otomatik cihaz Windows etkinleştirme 

Etki [alanına katılmış](/azure/active-directory/devices/hybrid-azuread-join-plan) bilgisayarlarda otomatik cihaz kaydını etkinleştirmek için bu Windows izleyin.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Aşama 8: Azure AD parola korumasını yapılandırma 

Zayıf [parolaları](/azure/active-directory/authentication/concept-password-ban-bad) ve değişkenlerini engellemek için bu yönergeleri izleyin.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Aşama 9: Azure AD Kimlik Korumasını Etkinleştirme

[Azure AD Kimlik Koruma Test Laboratuvarı Kılavuzu'nın 2. Aşaması'nın yönergelerini izleyin](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Aşama 10: Exchange Online ve Skype Kurumsal Online için modern kimlik doğrulamayı etkinleştirme

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

Sonuç, kimlik ve cihaz erişimi için parola karma eşitlemesi önkoşul yapılandırmasıyla [Active Directory'nin](../security/office-365-security/identity-access-prerequisites.md#prerequisites) gereksinimlerini karşılamaya uygun bir test ortamıdır. 

## <a name="next-step"></a>Sonraki adım

[Önkoşulları temel alan ilkeleri](../security/office-365-security/identity-access-policies.md) yapılandırmak ve kimlikleri ve cihazları korumak için Ortak kimlik ve cihaz erişimi ilkelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Ek kimlik Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md#identity)

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
