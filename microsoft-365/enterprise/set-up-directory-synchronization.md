---
title: Microsoft 365 için dizin eşitlemesini ayarlama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Microsoft 365 ile şirket içi Active Directory arasında dizin eşitlemesi ayarlamayı öğrenin.
ms.openlocfilehash: 49240d056520a83c0828440e21c5cf26943bae8e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092899"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Microsoft 365 için dizin eşitlemesini ayarlama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365, kimlik doğrulaması için kimlikleri ve bulut tabanlı kaynaklara erişim izinlerini depolamak ve yönetmek için bir Azure Active Directory (Azure AD) kiracısı kullanır. 

şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) etki alanınız veya ormanınız varsa, AD DS kullanıcı hesaplarınızı, gruplarınızı ve kişilerinizi Microsoft 365 aboneliğinizin Azure AD kiracısıyla eşitleyebilirsiniz. Bu, Microsoft 365 için karma kimliktir. Bileşenleri şunlardır.

![Microsoft 365 için dizin eşitleme bileşenleri.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Bağlan bir şirket içi sunucuda çalışır ve AD DS'nizi Azure AD kiracısıyla eşitler. Dizin eşitlemesi ile birlikte şu kimlik doğrulama seçeneklerini de belirtebilirsiniz:

- Parola karması eşitlemesi (PHS)

  Azure AD kimlik doğrulamasının kendisini gerçekleştirir.

- Doğrudan kimlik doğrulaması (PTA)

  Azure AD' de kimlik doğrulamasını gerçekleştiren AD DS vardır.

- Şirket Dışı Kimlik Doğrulaması

  Azure AD, başka bir kimlik sağlayıcısına kimlik doğrulaması isteyen istemci bilgisayarı ifade eder.

Daha fazla bilgi için bkz [. Karma kimlikler](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Azure AD Bağlan önkoşullarını gözden geçirin

Microsoft 365 aboneliğinizle ücretsiz bir Azure AD aboneliği alırsınız. Dizin eşitlemesini ayarladığınızda, şirket içi sunucularınızdan birine Azure AD Bağlan yüklersiniz.
  
Microsoft 365 için yapmanız gerekenler:
  
- Şirket içi etki alanınızı doğrulayın. Azure AD Bağlan sihirbazı bu konuda size yol gösterir.
- Microsoft 365 kiracınızın ve AD DS'nizin yönetici hesaplarının kullanıcı adlarını ve parolalarını alın.

Azure AD Bağlan yüklediğiniz şirket içi sunucunuz için şunları yapmanız gerekir:
  
|**Sunucu İşletim Sistemi**|**Diğer yazılımlar**|
|:-----|:-----|
|R2 ve üzerini Windows Server 2012 | - PowerShell varsayılan olarak yüklenir, hiçbir eylem gerekmez.  <br> - Net 4.5.1 ve üzeri sürümler Windows Update aracılığıyla sunulur. Denetim Masası Windows Sunucusu'na en son güncelleştirmeleri yüklediğinizden emin olun. |
|Service Pack 1 (SP1) ile Windows Server 2008 R2** veya Windows Server 2012 | - PowerShell'in en son sürümü Windows Management Framework 4.0 sürümünde kullanılabilir. [Microsoft İndirme Merkezi'nden](https://go.microsoft.com/fwlink/p/?LinkId=717996) arama yapın.  <br> - .Net 4.5.1 ve üzeri sürümler [Microsoft İndirme Merkezi'nden](https://go.microsoft.com/fwlink/p/?LinkId=717996) edinilebilir. |
|Windows Server 2008 | - PowerShell'in desteklenen en son sürümü Windows Management Framework 3.0 sürümünde, [Microsoft İndirme Merkezi'nde](https://go.microsoft.com/fwlink/p/?LinkId=717996) kullanılabilir.  <br> - .Net 4.5.1 ve üzeri sürümler [Microsoft İndirme Merkezi'nden](https://go.microsoft.com/fwlink/p/?LinkId=717996) edinilebilir. |

Donanım, yazılım, hesap ve izin gereksinimleri, SSL sertifika gereksinimleri ve Azure AD [Bağlan](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) için nesne sınırları ayrıntıları için bkz. Azure Active Directory Bağlan önkoşulları.
  
Ayrıca azure AD Bağlan [sürüm yayın geçmişini](/azure/active-directory/hybrid/reference-connect-version-history) gözden geçirerek her sürüme nelerin dahil olduğunu ve düzelttiklerini görebilirsiniz.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Azure AD Bağlan yükleme ve dizin eşitlemesini yapılandırma

Başlamadan önce şunları yaptığınızdan emin olun:

- Microsoft 365 genel yöneticisinin kullanıcı adı ve parolası
- AD DS etki alanı yöneticisinin kullanıcı adı ve parolası
- Hangi kimlik doğrulama yöntemi (PHS, PTA, federasyon)
- [Azure AD Sorunsuz Çoklu Oturum Açma (SSO)](/azure/active-directory/hybrid/how-to-connect-sso) kullanmak isteyip istemediğiniz

Şu adımları izleyin:

1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) ()https://admin.microsoft.com) oturum açın ve sol gezinti bölmesinde **Etkin Kullanıcılar'ı** \> seçin.
2. **Etkin kullanıcılar** sayfasında **Diğer** (üç nokta) **Dizin eşitlemesi'ni**\> seçin.
  
3. **Azure Active Directory hazırlık** sayfasında, başlamak **için İndirme merkezine git'i seçerek Azure AD Bağlan aracını edinin**. 
4. [Azure AD Bağlan ve Azure AD Bağlan Sistem Durumu yükleme yol haritasındaki](/azure/active-directory/hybrid/how-to-connect-install-roadmap) adımları izleyin.

## <a name="3-finish-setting-up-domains"></a>3. Etki alanlarını ayarlamayı bitirin

Etki alanlarınızı ayarlamayı tamamlamak [için DNS kayıtlarınızı yönetirken Microsoft 365 için DNS kayıtları oluşturma](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) başlığı altında yer alan adımları izleyin.

## <a name="next-step"></a>Sonraki adım

[Kullanıcı hesaplarına lisans atama](assign-licenses-to-user-accounts.md)