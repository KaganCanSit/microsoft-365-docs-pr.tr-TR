---
title: Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/20/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Kurumsal Microsoft 365 için tanıtım, kavram kanıtı veya geliştirme/test ortamları ayarlamak için bu Test Laboratuvarı Kılavuzlarını kullanın.
ms.openlocfilehash: 8c4444b599682ad40ebba88b37d83125fccd99f0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097436"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365

*Bu, hem kurumsal hem de Office 365 Kurumsal için Microsoft 365 için geçerlidir.*

Test Laboratuvarı Kılavuzları (TLG) Microsoft ürünleri hakkında hızlı bir şekilde bilgi edinmenize yardımcı olur. Basitleştirilmiş ancak temsili test ortamlarını yapılandırmak için açıklayıcı yönergeler sağlar. Deneme veya ücretli abonelik süresi boyunca bu ortamları tanıtım, özelleştirme veya karmaşık kavram kanıtı oluşturmak için kullanabilirsiniz.

TLG'ler modüler olacak şekilde tasarlanmıştır. Öğrenme veya test yapılandırma gereksinimlerinizle daha yakından eşleşen birden çok yapılandırma oluşturmak için birbirleri üzerine inşa ederler. "Kendim yaptım ve çalışıyor" uygulamalı deneyimi, yeni bir ürünün veya senaryonun dağıtım gereksinimlerini anlamanıza yardımcı olur, böylece üretimde barındırmayı daha iyi planlayabilirsiniz.

Geliştirme/test ortamları olarak da bilinen uygulamaları geliştirmek ve test etmek için temsili ortamlar oluşturmak için TLG'leri de kullanabilirsiniz.
  
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Kurumsal Test Laboratuvarı Kılavuzu yığınının Microsoft 365 tüm makalelere yönelik görsel bir harita için aşağıdaki grafiği genişletin veya [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) gidin.

[![Kurumsal Test Laboratuvarı Kılavuzu yığını için Microsoft 365.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Temel yapılandırma

İlk olarak[, kuruluş için Microsoft 365 için](/microsoft-365-enterprise/) bir test ortamı oluşturun. İki farklı tür temel yapılandırma oluşturabilirsiniz:

- [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) - Şirket içi bileşenler içermeyen yalnızca bulut ortamında kurumsal özellikler ve özellikler için Microsoft 365 yapılandırmak ve göstermek istediğinizde bunu kullanın.

- [Kurumsal temel yapılandırma simülasyonu](simulated-ent-base-configuration-microsoft-365-enterprise.md) - Active Directory Domain Services (AD DS) etki alanı gibi şirket içi bileşenleri kullanan karma bulut ortamında kurumsal özellikler ve özellikler için Microsoft 365 yapılandırmak ve göstermek istediğinizde bunu kullanın.

Microsoft 365 E5 lisansını deneme veya üretim test ortamınıza eklemeyerek Office 365 E5 için test ortamları da oluşturabilirsiniz.
    
## <a name="identity"></a>Kimlik

Kimlikle ilgili özellikleri ve özellikleri göstermek için bkz:

- [Parola karması eşitleme](password-hash-sync-m365-ent-test-environment.md)
  
   AD DS etki alanı denetleyicisinden parola karma tabanlı dizin eşitlemesini etkinleştirin ve test edin.

- [Geçiş kimlik doğrulaması](pass-through-auth-m365-ent-test-environment.md)
  
   AD DS etki alanı denetleyicisinde geçiş kimlik doğrulamasını etkinleştirin ve test edin.

- [Şirket Dışı Kimlik Doğrulaması](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Ad DS etki alanı denetleyicisinde federasyon kimlik doğrulamasını etkinleştirin ve test edin.

- [Microsoft Azure AD Sorunsuz Çoklu Oturum Açma](single-sign-on-m365-ent-test-environment.md)
  
   Ad DS etki alanı denetleyicisiyle Azure AD Sorunsuz Çoklu Oturum Açma 'yı (Sorunsuz SSO) etkinleştirin ve test edin.

- [Çok faktörlü kimlik doğrulaması](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Belirli bir kullanıcı hesabı için akıllı telefon tabanlı çok faktörlü kimlik doğrulamasını etkinleştirin ve test edin.

- [Genel yönetici hesaplarını koruma](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   Genel yönetici hesaplarınızı koşullu erişim ilkeleriyle kilitleyin.

- [Parola geri yazma](password-writeback-m365-ent-test-environment.md)

   Azure AD'den AD DS kullanıcı hesabınızdaki parolayı değiştirmek için parola geri yazma özelliğini kullanın.

- [Parola sıfırlama](password-reset-m365-ent-test-environment.md)

   Parolanızı sıfırlamak için self servis parola sıfırlamayı kullanın.

- [Otomatik lisanslama ve grup üyeliği](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Otomatik lisanslama ve dinamik grup üyeliği ile yeni hesapları yönetmeyi her zamankinden daha kolay hale getirin.

- [Azure AD Kimlik Koruması](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Geçerli kullanıcı hesaplarınızı güvenlik açıkları için tarayın.

- [Kimlik ve cihaz erişimi](identity-device-access-m365-test-environment.md)

   Önerilen kimlik ve cihaz erişim yapılandırmalarını ve koşullu erişim ilkelerini test etmek için bir ortam oluşturun.

## <a name="mobile-device-management"></a>Mobil cihaz yönetimi

Mobil cihaz yönetimiyle ilgili özellikleri ve özellikleri göstermek için bkz:

- [Cihaz uyumluluk ilkeleri](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Windows 10 cihazlar için bir kullanıcı grubu ve cihaz uyumluluk ilkesi oluşturun.
    
- [iOS ve Android cihazlarını kaydetme](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   iOS veya Android cihazları kaydedin ve uzaktan yönetin.

## <a name="information-protection"></a>Bilgi koruması

Bilgi korumasıyla ilgili özellikleri ve özellikleri göstermek için bkz:

- [Artırılmış Microsoft 365 güvenliği](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Artırılmış Microsoft 365 güvenlik ayarlarını yapılandırın ve yerleşik güvenlik araçlarını araştırın.
  
- [Veri sınıflandırması](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   SharePoint Online ekip sitesindeki bir belgeye etiket yapılandırma ve uygulama.
    
- [Ayrıcalıklı erişim yönetimi](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Kuruluşunuzdaki yükseltilmiş ve ayrıcalıklı görevlere tam zamanında erişim için ayrıcalıklı erişim yönetimini yapılandırın.