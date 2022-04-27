---
title: Microsoft 365 test ortamınız için parola karması eşitlemesi
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2020
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
- seo-marvel-apr2020
ms.assetid: ''
description: 'Özet: Microsoft 365 test ortamınız için parola karması eşitlemesini ve oturum açmayı yapılandırın ve gösterin.'
ms.openlocfilehash: 91d4de08382149b5089f0c06295e77965ea022cf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093821"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için parola karması eşitlemesi

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Birçok kuruluş, şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) ormanındaki hesap kümesini Microsoft 365 aboneliklerinin Azure AD kiracısında yer alan hesap kümesiyle eşitlemek için Azure AD Bağlan ve parola karması eşitlemesini kullanır. 

Bu makalede, Microsoft 365 test ortamınıza parola karması eşitlemesini nasıl ekleyebileceğiniz açıklanır ve bu da şu yapılandırmaya neden olur:
  
![Parola karması eşitleme testi ortamı ile sanal kuruluş.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Bu test ortamının ayarlanması üç aşamadan oluşur:
- [1. Aşama: Microsoft 365 simülasyon kurumsal test ortamını oluşturma](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [2. Aşama: Testlab etki alanını oluşturma ve kaydetme](#phase-2-create-and-register-the-testlab-domain)
- [3. Aşama: APP1'e Azure AD Bağlan yükleme](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>1. Aşama: Microsoft 365 simülasyon kurumsal test ortamını oluşturma

[Microsoft 365 için sanal kurumsal temel yapılandırma](simulated-ent-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin. Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![Sanal kurumsal temel yapılandırma.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunlardan oluşur:
  
- Microsoft 365 E5 deneme sürümü veya ücretli abonelik.
- Azure sanal ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti. DC1, ad DS etki alanı> *genel etki alanı adınızı* <testlab.<için bir etki alanı denetleyicisidir.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>2. Aşama: Testlab etki alanını oluşturma ve kaydetme

Bu aşamada, bir genel DNS etki alanı ekleyin ve ardından bunu aboneliğinize ekleyin.

İlk olarak, geçerli etki alanı adınızı temel alan yeni bir genel DNS etki alanı adı oluşturmak için genel DNS kayıt sağlayıcınızla birlikte çalışın ve ardından bunu aboneliğinize ekleyin. ***Genel etki alanınız*> <testlab.<** adını kullanmanızı öneririz. Örneğin, genel etki alanı adınız **<span>contoso.com</span>** ise, genel etki alanı adını ekleyin: **<span>testlab.contoso.com</span>**.
  
Ardından, etki alanı kayıt işleminden geçerek ***testlab.<genel etki alanınızı*>** Microsoft 365 deneme veya ücretli aboneliğinize ekleyin. Bu, ***testlab.<genel etki alanınıza*>** ek DNS kayıtları eklemektir. Daha fazla bilgi için bkz. [Microsoft 365 etki alanı ekleme](../admin/setup/add-domain.md).

Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![Testlab etki alanı adınızın kaydı.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Bu yapılandırma şunlardan oluşur:

- DNS etki alanı testlab.<*genel etki alanı adınızın* kayıtlı> olduğu Microsoft 365 E5 deneme veya ücretli abonelik.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti.

*Genel etki alanı adınızı*> testlab.<şu anda nasıl olduğuna dikkat edin:

- Genel DNS kayıtları tarafından desteklenir.
- Microsoft 365 aboneliklerinizde kayıtlı.
- Sanal intranetinizdeki AD DS etki alanı.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>3. Aşama: APP1'e Azure AD Bağlan yükleme

Bu aşamada, APP1'de Azure AD Bağlan aracını yükleyip yapılandırın ve ardından çalıştığını doğrulayın.
  
İlk olarak, APP1'de Azure AD Bağlan yükleyin ve yapılandırın.

1. [Azure portal](https://portal.azure.com) genel yönetici hesabınızla oturum açın ve ARDıNDAN TESTLABUser1\\ hesabıyla APP1'e bağlanın.
    
2. APP1'in masaüstünden, yönetici düzeyinde bir Windows PowerShell komut istemi açın ve ardından Internet Explorer Artırılmış Güvenlik'i devre dışı bırakmak için şu komutları çalıştırın:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Görev **çubuğundan Internet Explorer'ı** seçin ve adresine [https://aka.ms/aadconnect](https://aka.ms/aadconnect)gidin.
    
4. Microsoft Azure Active Directory Bağlan sayfasında **İndir'i** ve ardından **Çalıştır'ı** seçin.
    
5. **Azure AD'ye Hoş Geldiniz Bağlan** sayfasında **Kabul ediyorum'ı** ve ardından **Devam'ı** seçin.
    
6. **Express Ayarlar** sayfasında **Hızlı ayarları kullan'ı** seçin.
    
7. **Azure AD'ye Bağlan** sayfasında Kullanıcı Adı alanına genel yönetici hesabınızın adını girin **,** **parolasını Parola** alanına girin ve **ardından İleri'yi** seçin.
    
8. **AD DS'ye Bağlan** sayfasında **Kullanıcı Adı** alanına **TESTLABUser1\\** yazın, **parolayı Parola** alanına girin ve **İleri'yi** seçin.
    
9. **Yapılandırmaya hazır** sayfasında **Yükle'yi** seçin.
    
10. **Yapılandırma tamamlandı** sayfasında **Çıkış'ı** seçin.
    
11. Internet Explorer'da Microsoft 365 yönetim merkezi ([https://portal.microsoft.com](https://portal.microsoft.com)) bölümüne gidin.
    
12. Sol gezinti bölmesinde **Kullanıcılar > Etkin kullanıcılar'ı** seçin.
    
    **User1** adlı hesabı not edin. Bu hesap TESTLAB AD DS etki alanından ve dizin eşitlemesinin çalıştığının kanıtıdır.
    
13. **User1** hesabını ve ardından **Lisanslar ve uygulamalar'ı** seçin.
    
14. **Ürün lisansları** bölümünde konumunuzu seçin (gerekirse), **Office 365 E5** lisansını devre dışı bırakın ve **Microsoft 365 E5** lisansını etkinleştirin. 

15. Sayfanın alt kısmındaki **Kaydet'i** ve ardından **Kapat'ı** seçin.
    
Ardından, user1 hesabının ***etki alanı adı kullanıcı adınızı*> <user1@testlab.<aboneliğinizde** oturum açabilme özelliğini test edin:

1. APP1'de oturumu kapatın ve bu kez farklı bir hesap belirterek yeniden oturum açın.

2. Kullanıcı adı ve parola istendiğinde, ***etki alanı adınızı*>** ve Kullanıcı1 parolanızı user1@testlab.<belirtin. Kullanıcı1 olarak başarıyla oturum açmalısınız.
 
User1'in TESTLAB AD DS etki alanı için etki alanı yöneticisi izinlerine sahip olmasına rağmen genel yönetici olmadığını fark edin. Bu nedenle, **yönetici** simgesini bir seçenek olarak görmezsiniz. 

Sonuçta elde edilen yapılandırmanız şöyle görünür:

![Parola karması eşitleme testi ortamı ile sanal kuruluş.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Bu yapılandırma şunlardan oluşur: 
  
- DNS etki alanı TESTLAB.<*etki alanı adınızın* kayıtlı> deneme veya ücretli abonelikleri Microsoft 365 E5 veya Office 365 E5.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, TESTLAB AD DS etki alanını düzenli aralıklarla Microsoft 365 aboneliğinizin Azure AD kiracısıyla eşitlemek için APP1 üzerinde çalışır.
- TESTLAB AD DS etki alanındaki User1 hesabı Azure AD kiracısıyla eşitlendi.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)