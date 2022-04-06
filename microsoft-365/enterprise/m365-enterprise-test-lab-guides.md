---
title: Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kurumsal tasarım için gösterim, kavram kanıtı veya geliştirme/test ortamları ayarlamak üzere bu Test Laboratuvarı Microsoft 365 kullanın.
ms.openlocfilehash: 18b243a0fea9cb4864a0375740c4ebadcc44d6c3
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681666"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar

*Bu, hem kurumsal hem Microsoft 365 kurumsal iş için Office 365 Kurumsal.*

Test Laboratuvarı Kılavuzları (TGS) Microsoft ürünleri hakkında hızlı bir şekilde bilgi alamanıza yardımcı olur. Bunlar, basitleştirilmiş ancak temsili test ortamlarını yapılandırmak için önkızlı yönergeler sağlar. Deneme veya ücretli abonelik süresince bu ortamları gösterim, özelleştirme veya karmaşık kavram kanıtı oluşturmak için kullanabilirsiniz.

TGS'ler modüler bir şekilde tasarlanmıştır. Öğrenme veya yapılandırma ihtiyaçlarını test eden birden çok yapılandırma oluşturmak için birbirinin üzerine gelir. "Kendim hazırdım ve çalışıyor" uygulamalı deneyim, yeni bir ürünün veya senaryonun dağıtım gereksinimlerini anlamanıza yardımcı olur, böylece ürünü üretimde barındırmayı daha iyi planlayabilirsiniz.

Ayrıca, geliştirme/test ortamları olarak da bilinen uygulamaları geliştirmek ve test etmek için temsili ortamlar oluşturmak için TGS'leri kullanabilirsiniz.
  
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Kurumsal Test Laboratuvarı Kılavuzu yığınına yönelik Microsoft 365 görsel bir harita için aşağıdaki grafiği genişletin veya Microsoft 365 Test Laboratuvarı Kılavuzu [Yığını'nın üzerine gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![Kurumsal Microsoft 365 Test Laboratuvarı Kılavuzu yığını için kağıt kağıt.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Temel yapılandırma

İlk olarak, kurumsal ortamda Microsoft 365 [bir test ortamı oluşturun](/microsoft-365-enterprise/). İki farklı tür temel yapılandırma oluşturabilirsiniz:

- [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) - Bunu, şirket içi bileşenlerin yer Microsoft 365 bulut tabanlı bir ortamdaki kurumsal özellikleri ve yetenekleri yapılandırmak ve göstermek için kullanın.

- [Sanal kurumsal temel](simulated-ent-base-configuration-microsoft-365-enterprise.md) yapılandırma - Bunu, Active Directory Etki Alanı Hizmetleri (AD DS) etki alanı gibi şirket içi bileşenleri kullanan karma bir bulut ortamındaki kurumsal özellikler ve özellikler için Microsoft 365 yapılandırmak ve göstermek istediğiniz zaman kullanın.

Deneme veya üretim test ortamınıza Office 365 E5 için Microsoft 365 E5 ortamınız için test ortamları da oluşturabilirsiniz.
    
## <a name="identity"></a>Kimlik

Kimlikle ilgili özellikleri ve özellikleri göstermek için bkz:

- [Parola karması eşitlemesi](password-hash-sync-m365-ent-test-environment.md)
  
   Ad DS etki alanı denetleyicisinden parola karma tabanlı dizin eşitlemesini etkinleştirin ve test edin.

- [Geçişli kimlik doğrulaması](pass-through-auth-m365-ent-test-environment.md)
  
   Bir AD DS etki alanı denetleyicisinde geçişli kimlik doğrulamayı etkinleştirin ve test eder.

- [Federasyon kimlik doğrulaması](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Ad DS etki alanı denetleyicisine yönelik federasyon kimlik doğrulamasını etkinleştirin ve test eder.

- [Azure AD Sorunsuz Çoklu Oturum Açma](single-sign-on-m365-ent-test-environment.md)
  
   Azure AD Sorunsuz Çoklu Oturum Açma'yi (Sorunsuz SSO) AD DS etki alanı denetleyicisiyle etkinleştirin ve test edin.

- [Çok faktörlü kimlik doğrulaması](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Belirli bir kullanıcı hesabı için akıllı telefon tabanlı çok faktörlü kimlik doğrulamasını etkinleştirin ve test edin.

- [Genel yönetici hesaplarını koruma](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   Koşullu erişim ilkeleriyle genel yönetici hesaplarınızı kilitler.

- [Parola geri yazma](password-writeback-m365-ent-test-environment.md)

   Ad DS kullanıcı hesabı parolanızı Azure AD'den değiştirmek için parola geri yazma kullanın.

- [Parola sıfırlama](password-reset-m365-ent-test-environment.md)

   Kendi kendine parola sıfırlamayı kullanarak parolanızı sıfırlayın.

- [Otomatik lisans ve grup üyeliği](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Otomatik lisanslama ve dinamik grup üyeliğiyle yeni hesapları yönetmeyi her zamankinden daha kolay hale getirir.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Geçerli kullanıcı hesaplarınızı güvenlik açıkları için tarayın.

- [Kimlik ve cihaz erişimi](identity-device-access-m365-test-environment.md)

   Önerilen kimlik ve cihaz erişimi yapılandırmalarını ve koşullu erişim ilkelerini test etmek için bir ortam oluşturun.

## <a name="mobile-device-management"></a>Mobil cihaz yönetimi

Mobil cihaz yönetimiyle ilgili özellik ve yetenekleri göstermek için bkz:

- [Cihaz uyumluluğu ilkeleri](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Mobil cihazlarınız için bir kullanıcı grubu ve cihaz Windows 10 ilkesi oluşturun.
    
- [iOS ve Android cihazları kaydetme](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   iOS veya Android cihazları kaydettirin ve uzaktan yönetin.

## <a name="information-protection"></a>Bilgi koruması

Bilgi korumasıyla ilgili özellik ve özellikleri göstermek için bkz:

- [Artırılmış Microsoft 365 güvenliği](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Daha yüksek güvenlik Microsoft 365 için ayarları yapılandırın ve yerleşik güvenlik araçlarını araştırın.
  
- [Veri sınıflandırması](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   SharePoint Online ekip sitesinde etiketleri yapılandırarak belgeye uygulayabilirsiniz.
    
- [Ayrıcalıklı erişim yönetimi](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Kurum içinde yükseltilmiş ve ayrıcalıklı görevlere tam zamanında erişmek için ayrıcalıklı erişim yönetimini yapılandırın.