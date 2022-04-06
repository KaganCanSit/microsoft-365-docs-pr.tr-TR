---
title: Posta için güvenlik varsayılanlarını Microsoft 365 İş Ekstra
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Güvenlik varsayılanlarının, güvenlik ayarları için önceden yapılandırılmış güvenlik ayarları sağlayarak kimlikle ilgili saldırılardan korunmasına nasıl yardımcı Microsoft 365 İş Ekstra.
ms.openlocfilehash: 9684dc2be113d6f511f1a84e8865ac04a6881ecc
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634679"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Posta için güvenlik varsayılanlarını Microsoft 365 İş Ekstra

Güvenlik varsayılanları, Microsoft'un sizin organizasyonunız adına yönetmesi için önceden yapılandırılmış güvenlik ayarları sağlayarak kimliğinizin korunmasına yardımcı olur. Bu ayarlar arasında, tüm yöneticiler ve kullanıcı hesapları için Multi-Factor Authentication'ın (MFA) etkinleştirilmesi yer almaktadır. Çoğu kuruluş için, güvenlik varsayılanları iyi düzeyde ek oturum açma güvenliği sağlar.

Güvenlik varsayılanları ve zorunlu kılınan ilkeler hakkında daha fazla bilgi için bkz [. Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz 22 Ekim 2019'da veya daha sonra oluşturuldu ise sizin için güvenlik varsayılanları otomatik olarak etkinleştirildiyse,&mdash; onaylamak için ayarlarınızı denetlemeniz gerekir.

Ağ bağlantınız (Azure AD) Azure Active Directory varsayılanları etkinleştirmek veya etkin olup olduklarını görmek için:

1. Güvenlik yöneticisi, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yöneticisi veya Genel yönetici kimlik bilgileriyle oturum açın.

2. Sol bölmede, Her Şeyi **Göster'i seçin ve** Yönetim **merkezleri'nin altında Genel Azure Active Directory****.**

3. Yönetim merkezinin sol bölmesinde **Azure Active Directory'yi** **Azure Active Directory**.

4. Pano'daki sol menüden Yönet bölümünde **Özellikler'i** **seçin**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Özellikler menü Azure Active Directory gösteren yönetim merkezinin ekran görüntüsü.":::

5. Özellikler sayfasının en altında **, Güvenlik** varsayılanlarını **Yönet'i seçin**.

6. Sağ bölmede, Güvenlik varsayılanlarını **Etkinleştir ayarını** görebilirsiniz. Evet **seçiliyse** , güvenlik varsayılanları zaten etkindir ve başka eylem gerekmez. Güvenlik varsayılanları şu anda etkin değilse, etkinleştirmek **için Evet'i** seçin ve sonra da Kaydet'i **seçin**.

> [!NOTE]
> Koşullu Erişim ilkelerini daha önce kullandıysanız, güvenlik varsayılanlarını kullanmadan önce ilkeleri kapatmanız gerekir.
>
> Güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini kullanabilirsiniz, ancak ikisini de aynı anda kullanabilirsiniz.

## <a name="consider-using-conditional-access"></a>Koşullu Erişim'i kullanmayı düşünün

Kuruluşta karmaşık güvenlik gereksinimleri varsa veya güvenlik ilkeleriniz üzerinde daha ayrıntılı denetime ihtiyacınız varsa, benzer veya daha yüksek güvenlik sonrası bir gönderiyi elde etmek için güvenlik varsayılanları yerine Koşullu Erişim'i kullanmayı düşünmelisiniz. 

Koşullu Erişim, oturum açma olaylarına tepki veren ilkeler oluşturmanıza ve tanımlamanıza olanak sağlar ve kullanıcıya uygulama veya hizmete erişim izni verilmeden önce ek eylemler ister. Koşullu Erişim ilkeleri ayrıntılı ve özel olabilir; kullanıcıların her zaman ve her yerde üretken olması için güç sağlar, ancak aynı zamanda organizasyonlarınızı da korur.

Tüm müşteriler güvenlik varsayılanlarını kullanabilirken, Koşullu Erişim için aşağıdaki planlardan biri için lisans gerekir:

- Azure Active Directory Premium P1 veya P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 E5
- Enterprise Mobil & E3 veya E5

Koşullu Erişim'i kullanarak güvenlik varsayılanları tarafından etkinleştirilen ilkelerle eşdeğer ilkeler yapılandırmak için, aşağıdaki adım adım kılavuzlara göz atabilirsiniz:

- [Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)

- [Azure yönetimi için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)

- [Eski kimlik doğrulamayı engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

- [Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

- [Azure AD MFA kaydı gerektirme](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - Kimlik doğrulama işleminin bir parçası olan Azure AD Identity Protection Azure Active Directory Premium P2

Koşullu Erişim hakkında daha fazla bilgi edinmek için bkz [. Koşullu Erişim nedir?](/azure/active-directory/conditional-access/overview) Koşullu Erişim ilkeleri oluşturma hakkında daha fazla bilgi için bkz [. Koşullu Erişim ilkesi oluşturma](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Koşullu Erişim sağlayan, ancak henüz hiçbir Koşullu Erişim ilkesi oluşturmamış bir planınız veya lisansınız varsa, güvenlik varsayılanlarını kullanabilirsiniz. Bununla birlikte, Koşullu Erişim ilkelerini kullanamadan önce güvenlik varsayılanlarını kapatmanız gerekir.
