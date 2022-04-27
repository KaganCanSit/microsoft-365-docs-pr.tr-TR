---
title: Microsoft 365 test ortamınız için doğrudan kimlik doğrulaması
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Microsoft 365 test ortamınız için doğrudan kimlik doğrulamasını yapılandırın.'
ms.openlocfilehash: f6ad952ebde8556bd3c0c9b7e4e66c006b1c7578
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094382"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için doğrudan kimlik doğrulaması

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Microsoft bulut tabanlı hizmetler ve uygulamalarda kimlik doğrulaması için doğrudan şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) altyapısını kullanmak isteyen kuruluşlar doğrudan kimlik doğrulaması kullanabilir. Bu makalede, Microsoft 365 test ortamınızı doğrudan kimlik doğrulaması için nasıl yapılandırabileceğiniz açıklanır ve bu da aşağıdaki yapılandırmayla sonuçlanır:
  
![Doğrudan kimlik doğrulama testi ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Bu test ortamını ayarlamanın iki aşaması vardır:

1.    Parola karması eşitlemesi ile Microsoft 365 simülasyon kurumsal test ortamını oluşturun.
2.    Doğrudan kimlik doğrulaması için APP1'de Azure AD Bağlan yapılandırın.
    
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınının Microsoft 365 tüm makalelerin görsel haritası için [buraya](../downloads/Microsoft365EnterpriseTLGStack.pdf) tıklayın.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>1. Aşama: Microsoft 365 test ortamınız için parola karması eşitlemesini yapılandırma

[Microsoft 365 için parola karması eşitlemesindeki](password-hash-sync-m365-ent-test-environment.md) yönergeleri izleyin. Elde edilen yapılandırmanız aşağıdadır.
  
![Parola karması eşitleme testi ortamı ile sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunlardan oluşur: 
  
- Deneme veya ücretli aboneliği Microsoft 365 E5.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, İnternet'e bağlı basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, TESTLAB AD DS etki alanını düzenli aralıklarla Microsoft 365 aboneliğinizin Azure AD kiracısıyla eşitlemek için APP1 üzerinde çalışır.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>2. Aşama: Doğrudan kimlik doğrulaması için APP1'de Azure AD Bağlan yapılandırma

Bu aşamada, APP1'de Azure AD Bağlan doğrudan kimlik doğrulamasını kullanacak şekilde yapılandıracak ve ardından çalıştığını doğrulaacaksınız.

### <a name="configure-azure-ad-connect-on-app1"></a>APP1'de Azure AD Bağlan yapılandırma

1.    [Azure portal](https://portal.azure.com) genel yönetici hesabınızla oturum açın ve ARDıNDAN TESTLAB\User1 hesabıyla APP1'e bağlanın.

2.    APP1'in masaüstünden Azure AD Bağlan çalıştırın.

3.    **Hoş Geldiniz sayfasında** **Yapılandır'a** tıklayın.

4.    Ek görevler sayfasında **Kullanıcı oturumunu değiştir'e** ve ardından **İleri'ye** tıklayın.

5.    **Azure AD'ye Bağlan** sayfasında genel yönetici hesabı kimlik bilgilerinizi yazın ve **İleri'ye** tıklayın.

6.    **Kullanıcı oturum açma** sayfasında Doğrudan **kimlik doğrulaması'na** ve ardından **İleri'ye** tıklayın.

7.    **Yapılandırmaya hazır** sayfasında **Yapılandır'a** tıklayın.

8.    **Yapılandırma tamamlandı** sayfasında **Çıkış'a** tıklayın.

9.    Azure portal sol bölmede **Azure AD Bağlan Azure Active Directory >'e** tıklayın. **Geçiş kimlik doğrulaması** özelliğinin **Etkin** olarak göründüğünü doğrulayın.

10.    **Doğrudan kimlik doğrulama'ya** tıklayın. **Doğrudan kimlik doğrulama bölmesi,** Kimlik Doğrulama Aracılarınızın yüklü olduğu sunucuları listeler. Listede APP1'i görmeniz gerekir. **Geçiş kimlik doğrulaması** bölmesini kapatın.

Ardından, user1@testlab ile aboneliğinizde oturum açma özelliğini test edin <strong>.</strong>\<your public domain> Kullanıcı1 hesabının kullanıcı adı.

1. APP1'de oturumu kapatın ve bu kez farklı bir hesap belirterek yeniden oturum açın.

2. Kullanıcı adı ve parola istendiğinde <strong>user1@testlab belirtin.</strong>\<your public domain> ve User1 parolasını seçin. Kullanıcı1 olarak başarıyla oturum açmalısınız.

User1'in TESTLAB AD DS etki alanı için etki alanı yöneticisi izinlerine sahip olmasına rağmen genel yönetici olmadığını fark edin. Bu nedenle, **yönetici** simgesini bir seçenek olarak görmezsiniz.

Elde edilen yapılandırmanız şunlardır:

![Doğrudan kimlik doğrulama testi ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Bu yapılandırma şunlardan oluşur:

- DNS etki alanı testlab'ine sahip Microsoft 365 E5 deneme sürümü veya ücretli abonelikler.\<your domain name> Kayıtlı.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, İnternet'e bağlı basitleştirilmiş bir kuruluş intraneti. Kimlik Doğrulama Aracısı, Microsoft 365 aboneliğinizin Azure AD kiracısından gelen doğrudan kimlik doğrulama isteklerini işlemek için APP1 üzerinde çalışır.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)