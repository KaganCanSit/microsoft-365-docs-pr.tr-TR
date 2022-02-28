---
title: Test ortamınız için Microsoft 365 doğrulama
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Özet: Test ortamınız için geçişli Microsoft 365 yapılandırın.'
ms.openlocfilehash: dcc23662683ffaf65a0ec5fa3698f729dc215af7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983836"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Test ortamınız için Microsoft 365 doğrulama

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Microsoft bulut tabanlı hizmet ve uygulamalarında kimlik doğrulaması için doğrudan şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) altyapılarını kullanmak isteyen kuruluşlar, doğrudan kimlik doğrulamayı kullanabilir. Bu makalede, Microsoft 365 test ortamınızı geçişli kimlik doğrulaması için nasıl yapılandırabilirsiniz ve bunun sonucunda aşağıdaki yapılandırmalar açıklanmıştır:
  
![Geçişli kimlik doğrulama test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Bu test ortamını ayarlamanın iki aşaması vardır:

1.    Parola karması Microsoft 365 sanal kurumsal test ortamı oluşturun.
2.    Uygulama1'Bağlan Azure AD kimlik doğrulamasını yapılandırabilirsiniz.
    
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal [Test](../downloads/Microsoft365EnterpriseTLGStack.pdf) Laboratuvarı Kılavuzu yığınına göre görsel bir harita Microsoft 365 için buraya tıklayın.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma

Karma parola [eşitlemesi için verilen yönergeleri Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Sonuçta elde edilen yapılandırmanız şu şekildedir.
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunları oluşur: 
  
- Microsoft 365 E5 veya ücretli aboneliği seçin.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, APP1'de çalıştırarak TESTLAB AD DS etki alanını düzenli aralıklarla Microsoft 365 Azure AD kiracısına eşitler.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Aşama 2: Geçişli kimlik Bağlan app1 üzerinde Azure AD'yi yapılandırma

Bu aşamada, uygulama1 üzerinde Azure AD Bağlan'yi geçişli kimlik doğrulamayı kullanmak üzere yapılandırın ve sonra çalıştığını doğrulayın.

### <a name="configure-azure-ad-connect-on-app1"></a>APP1'te Azure AD Bağlan'yi yapılandırma

1.    [Azure portalında](https://portal.azure.com), genel yönetici hesabınızla oturum açın ve SONRA TESTLAB\User1 hesabıyla APP1'e bağlanın.

2.    APP1'in masaüstünden Azure AD Bağlan.

3.    Hoş Geldiniz **sayfasında Yapılandır'a** **tıklayın**.

4.    Ek görevler sayfasında, Kullanıcı oturum açma **ayarlarını değiştir'e tıklayın ve** sonra da Sonraki'ye **tıklayın**.

5.    **Azure AD Bağlan e** Ekle sayfasında genel yönetici hesabı kimlik bilgilerinizi yazın ve ardından Sonraki'ye **tıklayın**.

6.    Kullanıcı oturum **açma sayfasında,** Geçişli kimlik **doğrulama'ya tıklayın ve** sonra da Sonraki'ye **tıklayın**.

7.    Yapılandırmaya **hazır sayfasında Yapılandır'a** **tıklayın**.

8.    Yapılandırma tamamlandı **sayfasında Çıkış'a** **tıklayın**.

9.    Azure portalında, sol bölmede Azure **AD Azure Active Directory >'e Bağlan**. Geçişli kimlik **doğrulama özelliğinin Etkin** olarak görüntülendiğinden **emin olun**.

10.    **Geçişli kimlik doğrulama'ya tıklayın**. **Geçişli kimlik doğrulama** bölmesinde, Kimlik Doğrulama Aracılarının yüklü olduğu sunucular gösterilir. Listede APP1'i görüyor olması gerekir. Geçişli **kimlik doğrulama bölmesini** kapatın.

Ardından, abonelik aboneliğiniz için oturum açma becerinizi test user1@testlab <strong>.</strong>\<your public domain> kullanıcı adını girin.

1. Uygulama1'den, oturumları ve sonra bu kez farklı bir hesap belirterek yeniden oturum açın.

2. Kullanıcı adı ve parola istendiğinde, parolayı <strong>user1@testlab.</strong>\<your public domain> ve Kullanıcı1 parolası. Kullanıcı1 olarak başarıyla oturum a girişlisiniz.

Kullanıcı1'in TESTLAB AD DS etki alanı için etki alanı yöneticisi izinleri olmasına rağmen, bu bir genel yönetici değildir. Bu nedenle, bir seçenek olarak **Yönetici** simgesini görmeyebilirsiniz.

Sonuçta elde edilen yapılandırmanız şöyledir:

![Geçişli kimlik doğrulama test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Bu yapılandırma şunları oluşur:

- A Microsoft 365 E5 trial or paid subscriptions with the DNS domain testlab.\<your domain name> kaydedildi.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti. Bir Kimlik Doğrulama Aracısı, Microsoft 365 aboneliğinizin Azure AD kiracıdan gelen geçişli kimlik doğrulama isteklerini işlemek için APP1 Microsoft 365 çalışır.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)