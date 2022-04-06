---
title: PowerShell Skype Kurumsal Online'i yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: Skype Kurumsal Online ilkelerini, kullanıcı Microsoft 365 için PowerShell'i ve toplantı ayarlarını yönetmek için kullanın.
ms.openlocfilehash: cb546a7e4130509d7acd0021b3cb78df23c1819f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474482"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>PowerShell Skype Kurumsal Online'i yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Skype Kurumsal online yöneticileri ilkeleri yönetmekten sorumludur. Aynı anda bu görevlerden bir Microsoft 365 yönetim merkezi, diğerleri PowerShell'de daha kolaydır.

## <a name="before-you-start"></a>Başlamadan önce

> [!NOTE]
> Skype Kurumsal Online Connector şu anda en son PowerShell modülünde Teams vardır. En son **PowerShell Teams** kullanıyorsanız, Skype Kurumsal Online Connector'ı yüklemenize gerek yok.

> [!NOTE]
> Skype Kurumsal Online Yöneticileri, PowerShell aracılığıyla **Teams** **Skype Kurumsal Online uygulama** ilkelerini yönetebilir.

[Teams PowerShell modülünü yükleyin](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>Bağlan kimlik bilgilerini kullanma

1. Windows PowerShell komut istemi penceresini açın ve aşağıdaki komutları çalıştırın:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. Kimlik **Windows PowerShell İsteği iletişim** kutusuna yönetici hesap adı ve parolanızı yazın ve Tamam'ı **seçin**.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Bağlan faktörlü kimlik doğrulaması olan bir yönetici hesabı kullanma

1. Windows PowerShell istemi penceresini açın ve aşağıdaki komutları çalıştırın:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Çevrimiçi yönetici hesap adı Skype Kurumsal istendiğinde oturum açın.

3. Hesabınıza **oturum açın iletişim kutusunda Oturum** aç iletişim kutusuna Skype Kurumsal Online yöneticisi parolanızı yazın ve Oturum aç'ı **seçin**.

4. Hesabınızla **oturum açın iletişim kutusunda** , yönergeleri izleyerek doğrulama kodu gibi kimlik doğrulama bilgilerini ekleyin ve ardından Doğrula'ya **tıklayın**.

Daha fazla bilgi için bkz.:

- [PowerShell Skype Kurumsal Online ilkelerini yönetme](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [PowerShell ile kullanıcı başına Skype Kurumsal Online ilkeleri atama](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Kullanmaya başlayın PowerShell ile Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype Kurumsal PowerShell cmdlet başvuruları](/powershell/module/skype/)
