---
title: Mobil cihazlarda Office 2013 için Modern kimlik Windows etkinleştirme
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
ms.openlocfilehash: 468658c3b346c7923937ff9595699a20306ed6a9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754178"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Mobil cihazlarda Office 2013 için Modern kimlik Windows etkinleştirme

Microsoft Office 2013 on Microsoft Windows bilgisayarlar Modern kimlik doğrulamayı destekler. Ancak bu anahtarı açmak için aşağıdaki kayıt defteri anahtarlarını yapılandırmamız gerekir:

|Kayıt defteri anahtarı|Tür|Değer|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> Modern kimlik doğrulama 2016 veya Office'te zaten etkindir. Office 365'in sonraki sürümleri için bu kayıt defteri anahtarlarını Office.

## <a name="enable-modern-authentication-for-office-2013-clients"></a>Office 2013 istemcileri için modern kimlik doğrulamayı etkinleştirme

1. Outlook'u kapatın.

2. Aşağıdaki metni kopyalayıp yapıştırmak için Not Defteri:

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. Dosyayı kolayca bulmanız için .txt bir konuma kaydetmek yerine .reg dosya uzantısıyla kaydedin. Örneğin, `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. Dosya Gezgini'ni (eski adı Windows Gezgini) açın, az önce kayıtlı olan .reg dosyasının bulunduğu konuma gidin ve dosyaya çift tıklayın.

5. Görüntülenen **Kullanıcı hesabı denetimi iletişim** kutusunda, **uygulamanın aygıtınızda** değişiklik olmasına izin vermek için Evet'e tıklayın.

6. Görüntülenen Kayıt **Defteri Düzenleyicisi** uyarı iletişim kutusunda, değişiklikleri kabul **etmek için** Evet'e tıklayın.

Kayıt defteri anahtarlarını ayarlaytıktan sonra, Office 2013 uygulamalarını, Microsoft 365 ile çok faktörlü kimlik doğrulaması (MFA) kullanmak için Microsoft 365. Daha fazla bilgi için bkz [. Çok faktörlü kimlik doğrulamasını ayarlama](set-up-multi-factor-authentication.md).

Şu anda herhangi bir istemci Office oturum açmadıysanız, değişikliğin geçerliksi için oturum açmalı ve yeniden oturum dönebilirsiniz. Aksi takdirde, kimlik kuruluna kadar MRU ve dolaşım ayarları kullanılamaz.

## <a name="disable-modern-authentication-on-devices"></a>Cihazlarda modern kimlik doğrulamayı devre dışı bırakma

Bir cihazda modern kimlik doğrulamayı devre dışı bırakma yordamı çok benzer, ancak daha az kayıt defteri anahtarı gereklidir ve değerlerini 0 olarak ayarlamanız gerekir.

|Kayıt defteri anahtarı|Tür|Değer|
|---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|

```text
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Exchange]
"AlwaysUseMSOAuthForAutoDiscover"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
"EnableADAL"=dword:00000000
```

## <a name="related-content"></a>İlgili içerik

[Office 2013'te ikinci bir doğrulama yöntemiyle oturum açma](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)

[Outlook istemleri doğrular ve parolayı bağlanmak için Modern Kimlik Doğrulama'Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
