---
title: Microsoft 365 test ortamınız için Azure AD Sorunsuz Çoklu Oturum Açma
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
- TLGS
- Ent_TLGs
ms.assetid: ''
description: "Özet: Test ortamınız için Azure AD Sorunsuz Çoklu Oturum Açma'Microsoft 365 ve test edin."
ms.openlocfilehash: 4a420da5251ecef900f2efe9573db1d51a6bd597
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988145"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için Azure AD Sorunsuz Çoklu Oturum Açma

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Azure AD Sorunsuz Sign-On Çoklu Oturum (Sorunsuz SSO), bilgisayarlarını veya kuruluş ağlarına bağlı cihazlarına bağlı kullanıcılarda otomatik olarak oturumlar. Azure AD Sorunsuz SSO, ek şirket içi bileşenlere gerek kalmadan kullanıcılara bulut tabanlı uygulamalara kolay erişim sağlar.

Bu makalede, Azure AD Sorunsuz SSO için Microsoft 365 test ortamınızı nasıl yapılandırabilirsiniz?

Azure AD Sorunsuz SSO'nun ayarlama işlemi iki aşama içerir:
- [Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Aşama 2: Azure AD Sorunsuz SSO Bağlan App1'de Azure AD'yi yapılandırma](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma

Karma parola [eşitlemesi için verilen yönergeleri Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 ücretli abonelik.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, TESTLAB Active Directory Etki Alanı Hizmetleri (AD DS) etki alanını düzenli aralıklarla Microsoft 365 aboneliğinizin Azure AD kiracısına eşitlemek için APP1'de çalışır.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Aşama 2: Azure AD Sorunsuz SSO Bağlan App1'de Azure AD'yi yapılandırma

Bu aşamada, Azure AD Sorunsuz SSO Bağlan App1'de Azure AD Ad'yi yapılandırın ve çalıştığını doğrulayın.

### <a name="configure-azure-ad-connect-on-app1"></a>APP1'te Azure AD Bağlan'yi yapılandırma

1. [Azure portalında](https://portal.azure.com), genel yönetici hesabınızla oturum açın ve SONRA TESTLAB\User1 hesabıyla APP1'e bağlanın.

2. APP1 masaüstünden Azure AD Bağlan.

3. Hoş Geldiniz **sayfasında Yapılandır'ı** **seçin**.

4. Ek görevler **sayfasında,** Kullanıcı oturum açma **ayarlarını değiştir'i seçin ve** sonra da Sonraki'yi **seçin**.

5. **Azure AD'Bağlan** oturum açma sayfasında genel yönetici hesabı kimlik bilgilerinizi girin ve Ardından Sonraki'yi **seçin**.

6. Kullanıcı oturum **açma sayfasında,** Çoklu oturum açma **etkinleştir'i seçin ve sonra** da Sonraki'yi **seçin**.

7. Çoklu oturum **açma etkinleştir sayfasında Kimlik** bilgilerini **girin'i seçin**.

8. Kullanıcı **Windows Güvenliği** **kullanıcı1** ve parolasını girin, Tamam'ı ve sonra **da Sonraki'yi** **seçin**.

9. Yapılandırmaya **Hazır sayfasında Yapılandır'ı** **seçin**.

10. Yapılandırma tamamlandı **sayfasında Çıkış'ı** **seçin**.

11. Azure portalında, sol bölmede Azure Active Directory  > **Azure AD Bağlan**. Sorunsuz çoklu **oturum açma özelliğinin Etkin** olarak görüntülendiğinden **emin olun**.

Ardından, abonelik aboneliğiniz için oturum açma becerinizi test user1@testlab <strong>.</strong>\<*your public domain*> kullanıcı adını girin.

1. APP1 üzerinde Internet Explorer'dan, ayarlar simgesini seçin ve sonra İnternet **Seçenekleri'ni seçin**.
 
2. İnternet **Seçenekleri'nin** altında Güvenlik **sekmesini** seçin.

3. Yerel **intranet'i** ve ardından Siteler'i **seçin**.

4. Yerel **intranet'te** Gelişmiş'i **seçin**.

5. Bu **web sitesini bölgeye ekle'de** **https <span>://</span>** autologon.microsoftazuread-sso.com **AddCloseOKOK'u** >  >  >  **seçin**.

6. Bu kez farklı bir hesap belirterek oturum açın ve ardından yeniden oturum açın.

7. Oturum açmanız istendiğinde oturum açma <strong>user1@testlab.</strong>\<*your public domain*> seçin ve ardından Sonraki'yi **seçin**. Parola sorulmadan Kullanıcı1 olarak başarıyla oturum açın. Bu, Azure AD Sorunsuz SSO'nun çalıştığını kanıtlar.

Kullanıcı1'in TESTLAB AD DS etki alanı için etki alanı yöneticisi izinleri olmasına rağmen, bunun Azure AD için bir genel yönetici olmadığınına dikkat edin. Bu nedenle, bir seçenek olarak **Yönetici** simgesini görmeyebilirsiniz.

Sonuçta elde edilen yapılandırmanız şöyledir:

![Geçişli kimlik doğrulama test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Bu yapılandırma şunları oluşur:

- A Microsoft 365 E5 trial or paid subscriptions with the DNS domain testlab.\<*your domain name*> kaydedildi.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, Microsoft 365 aboneliğinizin Azure AD kiracısı olan hesap ve grupların listesini TESTLAB AD DS etki alanıyla eşitlemek için APP1'te çalışır.
- Azure AD Sorunsuz SSO etkinleştirildiğinden, sanal intranet'te bilgisayarlar kullanıcı hesabı parolası belirtmeden Microsoft 365 bulut kaynaklarında oturum açabilirsiniz.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)