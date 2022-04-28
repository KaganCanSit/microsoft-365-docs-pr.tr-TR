---
title: Microsoft 365 test ortamınız için parola sıfırlama
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Microsoft 365 test ortamınız için parola sıfırlamayı yapılandırın ve test edin.'
ms.openlocfilehash: 4e68372aee44887641d626c3e3667adbdedd5a1e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095630"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için parola sıfırlama

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Azure Active Directory (Azure AD) self servis parola sıfırlama (SSPR), kullanıcıların parolalarını veya hesaplarını sıfırlamasına veya kilidini açmasına olanak tanır.

Bu makalede, Microsoft 365 test ortamınızda parola sıfırlamalarını yapılandırma ve test etme işlemleri açıklanmaktadır.

SSPR'nin ayarlanması üç aşamadan oluşur:
- [1. Aşama: Microsoft 365 test ortamınız için parola karması eşitlemesini yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [2. Aşama: Parola geri yazmayı etkinleştirme](#phase-2-enable-password-writeback)
- [3. Aşama: Parola sıfırlamayı yapılandırma ve test edin](#phase-3-configure-and-test-password-reset)
    
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>1. Aşama: Microsoft 365 test ortamınız için parola karması eşitlemesini yapılandırma

İlk olarak [, parola karması eşitlemesindeki](password-hash-sync-m365-ent-test-environment.md) yönergeleri izleyin. 

Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![Parola karması eşitleme testi ortamı ile sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunlardan oluşur:
  
- Microsoft 365 E5 deneme sürümü veya ücretli abonelik.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, TESTLAB Active Directory Domain Services (AD DS) etki alanını Microsoft 365 aboneliğinizin Azure AD kiracısına eşitlemek için APP1 üzerinde çalışır.

## <a name="phase-2-enable-password-writeback"></a>2. Aşama: Parola geri yazmayı etkinleştirme

[Parola geri yazma Test Laboratuvarı Kılavuzu'nun 2. Aşamasındaki](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain) yönergeleri izleyin.

Parola sıfırlamayı kullanmak için parola geri yazma özelliğini etkinleştirmiş olmanız gerekir.
  
## <a name="phase-3-configure-and-test-password-reset"></a>3. Aşama: Parola sıfırlamayı yapılandırma ve test edin

Bu aşamada, grup üyeliği aracılığıyla Azure AD kiracısında parola sıfırlamayı yapılandırın ve ardından çalıştığını doğrulayın.

İlk olarak, belirli bir Azure AD grubundaki hesaplar için parola sıfırlamayı etkinleştirin.

1. Tarayıcınızın özel bir örneğinden öğesini açın [https://portal.azure.com](https://portal.azure.com)ve ardından genel yönetici hesabınızın kimlik bilgileriyle oturum açın.
2. Azure portal **Azure Active Directory** >  **GroupsYeni** >  **grup'ı** seçin.
3. **Grup türünü** **Güvenlik**, **Grup** **adı'nı PWReset** ve **Üyelik türünü** **Atanan** olarak ayarlayın.
4. **Üyeler'i** seçin, **Kullanıcı 3'i** bulup seçin, **Seç'i** ve ardından **Oluştur'u** seçin.
5. **Gruplar** bölmesini kapatın.
6. Azure Active Directory bölmesinde sol gezinti bölmesinde **Parola sıfırlama'yı** seçin.
7. **Parola sıfırlama özellikleri** bölmesinde, **Self Servis Parola Sıfırlama Etkin** seçeneğinin altında **Seçili'yi** seçin.
8. **Grup seç'i** seçin, **PWReset** grubunu seçin ve ardından **Kaydet'i** >  seçin.
9. Özel tarayıcı örneğini kapatın.

Ardından, Kullanıcı 3 hesabı için parola sıfırlamayı test edin.

1. Yeni bir özel tarayıcı örneği açın ve adresine [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)gidin.
1. Kullanıcı 3 hesabı kimlik bilgileriyle oturum açın.
1. **Daha fazla bilgi gerekli** bölümünde **İleri'yi** seçin. 
1. **Hesabınıza erişiminizi kaybetme** bölümünde, kimlik doğrulama telefonunu cep telefonu numaranıza ve kimlik doğrulama e-postasını iş veya kişisel e-posta hesabınıza ayarlayın.
1. Her ikisi de doğrulandıktan sonra **İyi görünüyor'ı** seçin ve tarayıcının özel örneğini kapatın.
1. Yeni bir özel tarayıcı örneğinde adresine [https://aka.ms/sspr](https://aka.ms/sspr)gidin.
1. Kullanıcı 3 hesabı adını girin, CAPTCHA'dan karakterleri girin ve **İleri'yi** seçin.
1. **Doğrulama 1. adım** için **Alternatif e-postama e-posta gönder'i ve ardından E-posta'yı** seçin. E-postayı aldığınızda doğrulama kodunu girin ve **İleri'yi** seçin.
1. **Hesabınıza geri dönün bölümünde** Kullanıcı 3 hesabı için yeni bir parola girin ve **Son'u** seçin. Kullanıcı 3 hesabının değiştirilmiş parolasını not edin ve güvenli bir konumda saklayın.
1. Aynı tarayıcının ayrı bir sekmesinde adresine gidin [https://admin.microsoft.com](https://admin.microsoft.com)ve ardından Kullanıcı 3 hesabı adı ve yeni parolası ile oturum açın. **Microsoft Office Giriş** sayfasını görmeniz gerekir.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)