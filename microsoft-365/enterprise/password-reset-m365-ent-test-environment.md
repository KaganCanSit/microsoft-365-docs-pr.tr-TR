---
title: Test ortamınız için Microsoft 365 sıfırlama
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2019
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
description: 'Özet: Test ortamınız için parola sıfırlamayı Microsoft 365 test edin.'
ms.openlocfilehash: 9aa55f42ca295577bf3b1c81ee54b1160adf3d27
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986473"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Test ortamınız için Microsoft 365 sıfırlama

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Azure Active Directory (Azure AD) self servis parola sıfırlama (SSPR) kullanıcıların parolalarını veya hesaplarını sıfırlamalarına veya kilidini açmalarına olanak sağlar.

Bu makalede, test ortamınıza parola sıfırlamaları yapılandırma ve Microsoft 365 açıklanmıştır.

SSPR'nin ayarlaması üç aşamadan önce geliyor:
- [Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Aşama 2: Parola geri yazmasını etkinleştirme](#phase-2-enable-password-writeback)
- [Aşama 3: Parola sıfırlamayı yapılandırma ve test edin](#phase-3-configure-and-test-password-reset)
    
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma

İlk olarak, parola karması [eşitlemesi yönergelerini izleyin](password-hash-sync-m365-ent-test-environment.md). 

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 ücretli abonelik.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, TESTLAB Active Directory Etki Alanı Hizmetleri (AD DS) etki alanını Microsoft 365 aboneliğinizin Azure AD kiracısına eşitlemek için APP1'te çalışır.

## <a name="phase-2-enable-password-writeback"></a>Aşama 2: Parola geri yazmasını etkinleştirme

Parola geri yazma [Test Laboratuvarı Kılavuzu'nın Aşama 2'sinde verilen yönergeleri izleyin](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

Parola sıfırlamayı kullanmak için parola geri yazma etkinleştirilmelidir.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Aşama 3: Parola sıfırlamayı yapılandırma ve test edin

Bu aşamada, grup üyeliği aracılığıyla Azure AD kiracısına parola sıfırlamayı yapılandırın ve çalıştığını doğrulayın.

İlk olarak, belirli bir Azure AD grubunda hesaplar için parola sıfırlamayı etkinleştirin.

1. Tarayıcınızın özel örneğinden, 'ı [https://portal.azure.com](https://portal.azure.com)açın ve genel yönetici hesabının kimlik bilgileriyle oturum açın.
2. Azure portalında, Grup **Azure Active Directory** >  **Grupla'ı** >  seçin.
3. Grup türünü **Güvenlik,** **Grup adı** olarak  **PWReset ve** **Üyelik türü de Atanan** olarak **ayarlayın**.
4. **Üyeler'i** seçin, Kullanıcı **3'ü bulup seçin**, Seç'i **ve** ardından Oluştur'a **seçin**.
5. Gruplar **bölmesini** kapatın.
6. Yeni Azure Active Directory gezinti bölmesinde Parola **sıfırlama'yı** seçin.
7. Parola sıfırlama **özellikleri bölmesinde,** Self Servis Parola Sıfırlama Etkin **seçeneğinin altında Seçili'yi** **seçin**.
8. Select **group,** select the **PWReset group**, and then **select** **SelectSave** > .
9. Özel tarayıcı örneğini kapatın.

Ardından, Kullanıcı 3 hesabı için parola sıfırlamayı test edin.

1. Yeni bir özel tarayıcı örneği açın ve göz atabilirsiniz [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Kullanıcı 3 hesabı kimlik bilgileriyle oturum açın.
1. Daha **fazla bilgi gerekli içinde** Sonraki'yi **seçin**. 
1. Hesabınıza **erişimi kaybetme içinde, kimlik** doğrulama telefonunuzu cep telefonu numaranıza ve kimlik doğrulama e-postasını iş veya kişisel e-posta hesabınıza ayarlayın.
1. Her ikisi de doğrulandıktan sonra **Güzel görünüyor'ı** seçin ve tarayıcının özel örneğini kapatın.
1. Yeni bir özel tarayıcı örneğinde, 'a gidin [https://aka.ms/sspr](https://aka.ms/sspr).
1. Kullanıcı 3 hesap adını girin, CAPTCHA'dan karakterleri girin ve Ardından Sonraki'yi **seçin**.
1. Doğrulama **adımı 1'i kullanmak için Alternatif e-postamı** **e-posta ile gönder'i** ve ardından E-posta'yi **seçin**. E-postayı alırsanız doğrulama kodunu girin ve Ardından Sonraki'yi **seçin**.
1. Hesabınıza **yeniden girin alanına Kullanıcı** 3 hesabı için yeni bir parola girin ve Son'a **seçin**. Kullanıcı 3 hesabının değiştirilen parolasını not edin ve güvenli bir yerde depo edin.
1. Aynı tarayıcının ayrı bir sekmesinde ' gidin [https://admin.microsoft.com](https://admin.microsoft.com), ardından Kullanıcı 3 hesap adı ve yeni parolasıyla oturum açın. Sayfa Giriş **Microsoft Office görüyoruz**.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)