---
title: Windows cihazlarında Office 2013 için Modern Kimlik Doğrulama'yı etkinleştirme
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: 2013 yüklü olan cihazlarda modern kimlik doğrulamayı etkinleştirmek için kayıt Microsoft Office ayarlamayı öğrenin.
ms.openlocfilehash: c5af8daa0538a1eb89521b12d1c85c310df6d012
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2021
ms.locfileid: "63005439"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Windows cihazlarında Office 2013 için Modern Kimlik Doğrulama'yı etkinleştirme

Office 2013'ün yüklü olduğu herhangi bir Windows cihazı için modern kimlik doğrulamayı etkinleştirmek istiyorsanız, belirli kayıt defteri anahtarları ayarlamanız gerekir.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Office 2013 istemcileri için modern kimlik doğrulamayı etkinleştirme

> [!NOTE]
> Office 2016 istemcileri için modern kimlik doğrulama zaten etkindir. Office 2016 için kayıt defteri anahtarları ayarlamanız gerekmez. 
  
Windows çalıştıran ve Microsoft Office 2013'ün yüklü olduğu herhangi bir cihazda (örneğin, dizüstü bilgisayar veya tablet) modern kimlik doğrulamayı etkinleştirmek için, aşağıdaki kayıt defteri anahtarlarını ayarlamanız gerekir. Modern kimlik doğrulamayı etkinleştirmek istediğiniz her cihazda anahtarların ayarlanmış olması gerekir:
  
|**Kayıt defteri anahtarı**|**Tür**|**Değer** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |
   
Kayıt defteri anahtarlarını ayarlaytıktan sonra, Office 2013 uygulamalarını, Microsoft 365 ile Çok Faktörlü Kimlik Doğrulaması [(MFA)](set-up-multi-factor-authentication.md) kullanmak üzere Microsoft 365. 
  
Şu anda istemci uygulamalarından herhangi birinde oturum açmış durumdaysanız, değişikliğin geçerlilik kazanması için oturumu kapatıp yeniden oturum açmanız gerekir. Aksi takdirde, kimlik kuruluna kadar MRU ve dolaşım ayarları kullanılamaz.
  
## <a name="disable-modern-authentication-on-devices"></a>Cihazlarda modern kimlik doğrulamayı devre dışı bırakma

Bir cihazda modern kimlik doğrulamayı devre dışı bırakmak için aşağıdaki kayıt defteri anahtarlarını ayarlayın:
  
|**Kayıt defteri anahtarı**|**Tür**|**Değer**|
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL |REG_DWORD|0|
   
## <a name="related-content"></a>İlgili içerik

[Office 2013'te ikinci bir doğrulama yöntemiyle oturum açma](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (makale)\
[Outlook istemleri doğrular ve](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) bu parolaya bağlanmak için Modern Kimlik Office 365 kullanmaz (makale)

