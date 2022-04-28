---
title: PowerShell ile Skype Kurumsal Online'i yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Skype Kurumsal Çevrimiçi ilkelerini, kullanıcı başına ilkeleri ve toplantı ayarlarını yönetmek için Microsoft 365 için PowerShell kullanın.
ms.openlocfilehash: 1c3a3e06d3fa607765382176a8c291fab2c69636
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097678"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>PowerShell ile Skype Kurumsal Online'i yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Skype Kurumsal Çevrimiçi yöneticiler ilkeleri yönetmekten sorumludur. Bu görevlerin bazılarını Microsoft 365 yönetim merkezi gerçekleştirebilirsiniz ancak diğerleri PowerShell'de daha kolaydır.

## <a name="before-you-start"></a>Başlamadan önce

> [!NOTE]
> Skype Kurumsal Online Connector şu anda en son Teams PowerShell modülünün bir parçasıdır. **PowerShell** genel sürümünün en son Teams kullanıyorsanız Skype Kurumsal Online Connector'ı yüklemeniz gerekmez.

> [!NOTE]
> Skype Kurumsal Online Yöneticileri, PowerShell aracılığıyla hem **Teams** hem **de Skype Kurumsal Online** uygulama ilkelerini yönetebilir.

[Teams PowerShell modülünü](/microsoftteams/teams-powershell-install) yükleyin.

## <a name="connect-using-admin-credentials"></a>Yönetici kimlik bilgilerini kullanarak Bağlan

1. bir Windows PowerShell komut istemi penceresi açın ve aşağıdaki komutları çalıştırın:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. **Windows PowerShell Kimlik Bilgisi İsteği** iletişim kutusuna yönetici hesabınızın adını ve parolasını yazın ve **tamam'ı** seçin.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Çok faktörlü kimlik doğrulamasıyla yönetici hesabı kullanarak Bağlan

1. bir Windows PowerShell komut istemi penceresi açın ve aşağıdaki komutları çalıştırın:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. İstendiğinde Skype Kurumsal Çevrimiçi yönetici hesabı adınızı girin.

3. **Hesabınızda oturum açın** iletişim kutusunda Skype Kurumsal Çevrimiçi yönetici parolanızı yazın ve **Oturum aç'ı** seçin.

4. **Hesabınızda oturum açın** iletişim kutusunda, doğrulama kodu gibi kimlik doğrulama bilgileri eklemek için yönergeleri izleyin ve ardından **Doğrula'yı** seçin.

Daha fazla bilgi için bkz.:

- [PowerShell ile Skype Kurumsal Çevrimiçi ilkelerini yönetme](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [PowerShell ile kullanıcı başına Skype Kurumsal Çevrimiçi ilkeleri atama](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell ile Kullanmaya başlayın](getting-started-with-microsoft-365-powershell.md)

[PowerShell cmdlet başvurularını Skype Kurumsal](/powershell/module/skype/)
