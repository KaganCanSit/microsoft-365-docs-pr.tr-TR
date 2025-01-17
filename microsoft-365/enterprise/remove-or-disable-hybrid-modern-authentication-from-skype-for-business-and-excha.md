---
title: karma modern kimlik doğrulamasını Skype Kurumsal ve Exchange kaldırma veya devre dışı bırakma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede Karma Modern Kimlik Doğrulaması'nın Skype Kurumsal ve Exchange'den nasıl kaldırılacağı veya devre dışı bırakılacağı açıklanmaktadır.
ms.openlocfilehash: 6456873f7338b97b3255f3976e7520580ac2a142
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017820"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>karma modern kimlik doğrulamasını Skype Kurumsal ve Exchange kaldırma veya devre dışı bırakma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Karma Modern Kimlik Doğrulamasını (HMA) yalnızca geçerli ortamınız için uygun olmadığını bulmak için etkinleştirdiyseniz HMA'yı devre dışı bırakabilirsiniz. Bu makalede nasıl yapılır açıklanmaktadır.

## <a name="who-is-this-article-for"></a>Bu makale Who içindir?

Skype Kurumsal Online veya Şirket İçi ve/veya Exchange Online ya da Şirket İçi'nde Modern Kimlik Doğrulama'yı etkinleştirdiyseniz ve HMA'yı devre dışı bırakmanız gerektiğini fark ettiyseniz, bu adımlar size yöneliktir.

> [!IMPORTANT]
> Skype Kurumsal Online veya Şirket İçi'ndeyseniz, karma topoloji HMA'nız varsa ve başlamadan önce desteklenen topolojilere bakmanız gerekiyorsa '[Modern Kimlik Doğrulaması ile desteklenen Skype Kurumsal topolojileri](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)' makalesine bakın.

## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Karma Modern Kimlik Doğrulamasını devre dışı bırakma (Exchange)

1. **şirket içi Exchange**: [Exchange Yönetim Kabuğu'nı açın](/powershell/exchange/open-the-exchange-management-shell) ve aşağıdaki komutları çalıştırın:

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
   Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
   ```

2. **Exchange Online**: [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Modern Kimlik Doğrulamasını devre dışı bırakmak için aşağıdaki komutu çalıştırın:

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
   ```

## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Karma Modern Kimlik Doğrulamasını devre dışı bırakma (Skype Kurumsal)

1. **şirket içi Skype Kurumsal**: Skype Kurumsal Yönetim Kabuğu'nda aşağıdaki komutları çalıştırın:

   ```powershell
   Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
   ```

2. **Skype Kurumsal Online**: [Skype Kurumsal Online PowerShell'e Bağlan](manage-skype-for-business-online-with-microsoft-365-powershell.md). Modern Kimlik Doğrulamasını devre dışı bırakmak için aşağıdaki komutu çalıştırın:

   ```powershell
   Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
   ```

[Modern Kimlik Doğrulamasına genel bakış bağlantısı](hybrid-modern-auth-overview.md).
