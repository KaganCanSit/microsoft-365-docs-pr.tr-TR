---
title: Etki alanı için dizin eşitlemesini Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Etki alanınız ve şirket içi Active Directory Microsoft 365 arasında dizin eşitlemesi ayarlamayı öğrenin.
ms.openlocfilehash: 61b2dd822d0e65ebbf97ddcbfc3c8a03887c45a6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988715"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Etki alanı için dizin eşitlemesini Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365, kimlik Azure Active Directory için kimlikleri depolamak ve yönetmek ve bulut tabanlı kaynaklara erişim izinleri için bir Azure Active Directory (Azure AD) kiracısı kullanır. 

Şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) etki alanınız veya ormanınız varsa, AD DS kullanıcı hesaplarınızı, gruplarınızı ve kişilerinizi Microsoft 365 aboneliğinizin Azure AD kiracısı ile eşit edebilirsiniz. Bu, kimlik yönetiminin karma Microsoft 365. Bileşenleriniz burada vemektedir.

![Eşitleme için dizin eşitlemesi Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Bağlan şirket içi bir sunucuda çalışır ve AD DS'nizi Azure AD kiracısı ile eşitler. Dizin eşitlemeyle birlikte, şu kimlik doğrulama seçeneklerini de belirtebilirsiniz:

- Parola karması eşitlemesi (PHS)

  Azure AD, kimlik doğrulamayı kendisinin gerçekleştirir.

- Geçişli kimlik doğrulaması (PTA)

  Azure AD'nin kimlik doğrulamayı gerçekleştirmesi için AD DS vardır.

- Federasyon kimlik doğrulaması

  Azure AD, başka bir kimlik sağlayıcısına kimlik doğrulaması talep etmek için istemci bilgisayara başvurur.

Daha [fazla bilgi için bkz](plan-for-directory-synchronization.md) . Karma kimlikler.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Azure AD önkoşullarını Bağlan

Microsoft 365 aboneliğiyle, ücretsiz bir Azure AD Microsoft 365 alırsınız. Dizin eşitlemesini ayar zaman, şirket içi sunuculardan Bağlan Azure AD Eşitlemesi'ne yüklemiş oluruz.
  
Bu Microsoft 365 şunları da gerekir:
  
- Şirket içi etki alanınızı doğrulayın. Azure AD Bağlan sihirbazı bu işlemde size yol sunar.
- Kiracınız ve AD DS'nizin yönetici hesapları için kullanıcı Microsoft 365 ve parolaları alın.

Azure AD Bağlan'i yüklemeniz gereken şirket içi sunucunuz için:
  
|**Sunucu işletim sistemi**|**Diğer yazılımlar**|
|:-----|:-----|
|Windows Server 2012 R2 ve sonrası | - PowerShell varsayılan olarak yüklenir, herhangi bir işlem gerekmez.  <br> - NET 4.5.1 ve sonraki sürümler, Sürüm Güncelleştirmesi Windows sunulur. Denetim Masası'nda Windows Server için en son güncelleştirmeleri yüklemiş olun. |
|Windows Pack 1 (SP1)** ile Windows Server 2008 R2 veya Windows Server 2012 | - PowerShell'in en son sürümü Windows Management Framework 4.0 sürümünde kullanılabilir. [Microsoft İndirme Merkezi'nde arama.](https://go.microsoft.com/fwlink/p/?LinkId=717996)  <br> - .NET 4.5.1 ve sonraki sürümler [Microsoft İndirme Merkezi'nde kullanılabilir](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | - PowerShell'in desteklenen en son sürümü microsoft indirme Windows Management Framework 3.0 sürümünde [kullanılabilir](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .NET 4.5.1 ve sonraki sürümler [Microsoft İndirme Merkezi'nde kullanılabilir](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Azure AD [Azure Active Directory Bağlan](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) donanım, yazılım, hesap ve izin gereksinimleri, SSL sertifika gereksinimleri ve nesne sınırları ayrıntıları için bkz. Bağlan.
  
Ayrıca, her sürüme nelerin dahil olduğunu Bağlan [için](/azure/active-directory/hybrid/reference-connect-version-history) Azure AD'nin sürüm geçmişini de gözden geçirsiniz.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Azure AD eşitlemesini Bağlan eşitlemesini yapılandırma

Başlamadan önce şunları sahip olduğunu emin olun:

- Genel yöneticinin kullanıcı adı Microsoft 365 parolası
- AD DS etki alanı yöneticisinin kullanıcı adı ve parolası
- Hangi kimlik doğrulama yöntemi (PHS, PTA, federasyon)
- [Azure AD Sorunsuz Çoklu Oturum Açma(SSO) kullanmak isteyip istemeysiniz](/azure/active-directory/hybrid/how-to-connect-sso)

Şu adımları izleyin:

1. Gezinti Bölmesinde [oturum Microsoft 365 yönetim merkezi (](https://admin.microsoft.com) vehttps://admin.microsoft.com) sol **gezintide** \> **Kullanıcılar Etkin** Kullanıcılar'ı seçin.
2. Etkin kullanıcılar **sayfasında,** Diğer (üç **nokta**) Dizin **eşitlemesi'ne**\> tıklayın.
  
3. Hazırlığı **Azure Active Directory,** Azure AD Destek Aracı bağlantısını almak **için İndirme merkezine Bağlan'ı** seçin. 
4. [Azure AD Bağlan Azure AD Bağlan Yükleme yol haritası'daki adımları izleyin](/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Etki alanlarını ayarlamayı bitirme

Etki alanlarınızı [ayarlamayı bitirmek için MICROSOFT 365 DNS kayıtlarınızı](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) yönetirken DNS kayıtları oluşturma'daki adımları izleyin.

## <a name="next-step"></a>Sonraki adım

[Kullanıcı hesaplarına lisans atama](assign-licenses-to-user-accounts.md)