---
title: Karma Modern Kimlik Doğrulama'nın dosya ve ağ bağlantılarından Skype Kurumsal veya devre dışı Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, Karma Modern Kimlik Doğrulama'nın etki ve denetimlerinden nasıl kaldır Skype Kurumsal Exchange.
ms.openlocfilehash: efc84ead5ea8219e77391f2a8ebe51e5fa23da8c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988146"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Karma Modern Kimlik Doğrulama'nın dosya ve ağ bağlantılarından Skype Kurumsal veya devre dışı Exchange

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Karma Modern Kimlik Doğrulama'yı (HMA) yalnızca geçerli ortamınıza uygun bulmanız için etkinleştirdiyseniz HMA'yı devre dışı abilirsiniz. Bu makalede nasıl olduğu açıklanmıştır.
  
## <a name="who-is-this-article-for"></a>Who ne için?

Skype Kurumsal Online'da veya Şirket İçi'de Modern Kimlik Doğrulama'yı etkinleştirdiyse, ve/veya Exchange Online veya Şirket İçi'ne yönelikse ve HMA'yı devre dışı bırakmanız gerekiyorsa, bu adımlar size yöneliktir.

> [!IMPORTANT]
> Skype Kurumsal Online'da veya Şirket içinde isanız, karma topoloji HMA'nız varsa ve başlamadan önce desteklenen topolojilere bakmanız gerekirse , 'Modern Kimlik Doğrulaması ile desteklenen [Skype Kurumsal topolojileri](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)' makalesine bakın.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Karma Modern Kimlik Doğrulama 'ı (Karma Modern Kimlik Doğrulama) devre dışı Exchange

1. **Exchange Için:** Exchange Yönetim Kabuğu'Exchange aşağıdaki komutları çalıştırın: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Bağlan Uzak PowerShell Exchange Online'i](/powershell/exchange/connect-to-exchange-online-powershell) kullanabilirsiniz. *OAuth2ClientProfileEnabled bayrağınızı 'false' bayrağına* çevirmek için aşağıdaki komutu çalıştırın:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Karma Modern Kimlik Doğrulama'nın (Kimlik Doğrulama) devre dışı Skype Kurumsal

1. **Skype Kurumsal Için: Yönetim** Kabuğu'Skype Kurumsal çalıştırın:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype Kurumsal Online**: Bağlan PowerShell [ile Skype Kurumsal Online'a](manage-skype-for-business-online-with-microsoft-365-powershell.md) bağlanın. Modern Kimlik Doğrulama'yi devre dışı bırakmak için aşağıdaki komutu çalıştırın:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Modern Kimlik Doğrulamaya genel bakış bağlantısına geri dönebilirsiniz](hybrid-modern-auth-overview.md) . 
