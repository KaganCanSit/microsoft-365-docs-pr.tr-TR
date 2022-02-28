---
title: Test ortamınız için parola Microsoft 365 eşitlemesi
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Parola karması eşitlemesini yapılandırarak ve gösterirken test ortamınız için Microsoft 365 açma.'
ms.openlocfilehash: 746a0e1112df6ebf99569bfed58d08d0a4519d7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986474"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Test ortamınız için parola Microsoft 365 eşitlemesi

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Birçok kuruluş, şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) ormanı içinde yer alan hesap kümelerini Microsoft 365 aboneliklerinin Azure AD kiracısı hesap kümesiyle eşitlemek için Azure AD Bağlan ve parola karma eşitlemesini kullanır. 

Bu makalede, karma parola eşitlemesini test ortamınıza nasıl Microsoft 365 ve bu da bu yapılandırmayla sonuç verir:
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Bu sınama ortamını ayarlama üç aşama içerir:
- [Aşama 1: Sanal Microsoft 365 test ortamı oluşturma](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Aşama 2: Testlab etki alanını oluşturma ve kaydetme](#phase-2-create-and-register-the-testlab-domain)
- [Aşama 3: APP1'e Azure AD Bağlan yükleme](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Aşama 1: Sanal Microsoft 365 test ortamı oluşturma

Kurumsal taban yapılandırmasının [benzetimi yapılan yönergeleri izleyerek Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Sanal kurumsal temel yapılandırmadır.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 ücretli abonelik.
- Azure sanal ağının DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, İnternet'e bağlı basitleştirilmiş bir kuruluş intraneti. DC1, testlab.<ad ve AD DS etki alanınız *için>* denetleyicisidir.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Aşama 2: Testlab etki alanını oluşturma ve kaydetme

Bu aşamada, bir genel DNS etki alanı ekleyin ve ardından bu etki alanını aboneliğinize ekleyin.

İlk olarak, genel DNS kayıt sağlayıcınızla birlikte çalışarak geçerli etki alanı adınızı temel alan yeni bir genel DNS etki alanı adı oluşturun ve ardından bu adı aboneliğinize ekleyin. Genel etki alanınıza **testlab.<*adını öneririz*>**. Örneğin, ortak etki alanı adınız **<span>contoso.com</span>** ise, genel etki alanı adını ekleyin: **<span>testlab.contoso.com</span>**.
  
Ardından, etki alanı kayıt <aracılığıyla genel etki alanı etki Microsoft 365 deneme veya ücretli aboneliğinize **testlab.Microsoft 365 >** ekleyin. Bu, **testlab.<etki alanınıza ek DNS *kayıtlarını eklemektir*>** . Daha fazla bilgi için bkz[. Etki alanına Microsoft 365](../admin/setup/add-domain.md).

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Testlab etki alanı adınızın kaydı.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Bu yapılandırma şunları oluşur:

- A Microsoft 365 E5 trial or paid subscription with the DNS domain testlab.<*your public domain name*>.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.

Testlab.<*genel etki alanı adınızın nasıl>* dikkat:

- Genel DNS kayıtları tarafından desteklenen.
- Microsoft 365 aboneliklerinize kayıtlı.
- Sanal intranetinizin AD DS etki alanı.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Aşama 3: APP1'e Azure AD Bağlan yükleme

Bu aşamada, APP1'de Azure AD Bağlan aracını yükleyin ve yapılandırın, ardından çalıştığını doğrulayın.
  
İlk olarak, APP1'te Azure AD Bağlan'i yükleyin ve yapılandırın.

1. [Azure portalında](https://portal.azure.com), genel yönetici hesabınızla oturum açın ve SONRA TESTLABUser1 hesabıyla APP1'e\\ bağlanın.
    
2. APP1 masaüstünde, yönetici düzeyinde bir Windows PowerShell istemi açın ve Internet Explorer Artırılmış Güvenlik'i devre dışı bırakmak için şu komutları çalıştırın:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Görev çubuğundan **Internet Explorer'ı seçin** ve seçeneğine gidin [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Çalışma sayfası Microsoft Azure Active Directory Bağlan **İndir'i ve** ardından Çalıştır'ı **seçin**.
    
5. **Azure AD'ye Hoş Geldiniz sayfasında Bağlan** kabul **ediyorum'ı ve ardından** Devam'ı **seçin**.
    
6. Express **Ayarlar sayfasında** Use **express settings öğesini seçin**.
    
7. **Azure AD'Bağlan** hesap adınızı girin, Kullanıcı Adı alanına genel yönetici hesap adınızı girin **,** Parola alanına parolasını girin ve ardından Sonraki'yi **seçin**.
    
8. **Ad DS Bağlan Ad'a** Tıklayın sayfasında, Kullanıcı Adı alanına **TESTLABUser1\\** girin **,** Parola alanına parolasını girin ve **Ardından Sonraki'yi** **seçin**.
    
9. Yapılandırmaya **hazır sayfasında Yükle'yi** **seçin**.
    
10. Yapılandırma tamamlandı **sayfasında Çıkış'ı** **seçin**.
    
11. Internet Explorer'da, Bağlantı Çubuğu'Microsoft 365 yönetim merkezi() gidin[https://portal.microsoft.com](https://portal.microsoft.com).
    
12. Sol gezinti bölmesinde Kullanıcılar'ı **ve etkin > seçin**.
    
    Kullanıcı1 adlı **hesaba dikkatin**. Bu hesap TESTLAB AD DS etki alanına yöneliktir ve dizin eşitlemenin çalıştığının kanıtıdır.
    
13. Kullanıcı1 **hesabını ve** ardından Lisanslar **ve uygulamalar'ı seçin**.
    
14. Ürün **lisansları'nın** altında, yer seçin (gerekirse), Office 365 E5 devre  dışı bırak'ı ve sonra **Microsoft 365 E5** etkinleştirin. 

15. Sayfanın **alt** kısmında Kaydet'i seçin ve sonra Kapat'ı **seçin**.
    
Ardından, Kullanıcı1 hesabının etki alanı adı kullanıcı adınızı **user1@testlab.<>** aboneliğiniz için oturum açma becerinizi test edin:

1. Uygulama1'den, oturumları ve sonra bu kez farklı bir hesap belirterek yeniden oturum açın.

2. Kullanıcı adı ve parola istendiğinde, **user1@testlab.<*alanı adınızı ve*>** Kullanıcı1 parolasını belirtin. Kullanıcı1 olarak başarıyla oturum a girişlisiniz.
 
Kullanıcı1'in TESTLAB AD DS etki alanı için etki alanı yöneticisi izinleri olmasına rağmen, bu bir genel yönetici değildir. Bu nedenle, bir seçenek olarak **Yönetici** simgesini görmeyebilirsiniz. 

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:

![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Bu yapılandırma şunları oluşur: 
  
- Microsoft 365 E5 TESTLAB.Office 365 E5 alanıyla deneme veya ücretli abonelikler için veya deneme aboneliklerinizi <*etki* alanı adınızın> gerekir.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, TESTLAB AD DS etki alanını düzenli aralıklarla Microsoft 365 aboneliğinizin Azure AD kiracısına eşitlemek için APP1'de çalışır.
- TESTLAB AD DS etki alanındaki Kullanıcı1 hesabı, Azure AD kiracısı ile eşitlenmiş.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)