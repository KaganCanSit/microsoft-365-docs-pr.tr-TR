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
ms.openlocfilehash: 9ab3bb8e352a90cd4cef0c3c56496b3431e8b746
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63494464"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Windows cihazlarında Office 2013 için Modern Kimlik Doğrulama'yı etkinleştirme

Office 2013'ün yüklü olduğu herhangi bir Windows cihazı için modern kimlik doğrulamayı etkinleştirmek istiyorsanız, belirli kayıt defteri anahtarları ayarlamanız gerekir.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Office 2013 istemcileri için modern kimlik doğrulamayı etkinleştirme

> [!NOTE]
> Office 2016 istemcileri için modern kimlik doğrulama zaten etkindir. Office 2016 için kayıt defteri anahtarları ayarlamanız gerekmez. 
  
Windows çalıştıran ve Microsoft Office 2013'ün yüklü olduğu herhangi bir cihazda (örneğin, dizüstü bilgisayar veya tablet) modern kimlik doğrulamayı etkinleştirmek için, aşağıdaki kayıt defteri anahtarlarını ayarlamanız gerekir. Modern kimlik doğrulamayı etkinleştirmek istediğiniz her cihazda anahtarların ayarlanmış olması gerekir:

<br>

****

|Kayıt defteri anahtarı|Tür|Değer|
|:---|:---:|---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|
|

EWS ve Otomatik Bulma gibi web Outlook için daha yeni bir kimlik doğrulama yöntemi kullanmaya zorlamak için aşağıdaki kayıt defteri anahtarlarını oluşturun veya bu kayıt defterinde değişiklik yapın. Kullanıcıların Modern Kimlik Doğrulama'Outlook kimlik doğrulamasını kullanmaya zorlamalarını öneririz.

1. Outlook'tan çıkın.

2. Kayıt Defteri Düzenleyicisi'ni, aşağıdaki yordamlardan birini kullanarak ve bu yordamlardan birini Windows:

   - **Windows 10, Windows 8.1 ve Windows 8:** Windows Tuşu + R tuşlarına basarak Çalıştır **iletişim** kutusunu açın. regedit.exeyazın *ve* Enter tuşuna **basın.**
   - **Windows 7:** **Başlat'a** regedit.exearama kutusuna bir arama ** yazın ve Enter tuşuna **basın.**

3. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki kayıt defteri alt anahtarını bulun ve tıklatın:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Exchange\
   ```

4. *AlwaysUseMSOAuthForAutoDiscover* tuşu yoksa, *AlwaysUseMSOAuthForAutoDiscover* yazın ve Enter tuşuna **basın.**

5. *AlwaysUseMSOAuthForAutoDiscover'a sağ tıklayın ve* ardından Değiştir'e **tıklayın.**

6. Değer **verisi** kutusuna **1 yazın ve** Tamam'a **tıklayın.**

7. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki kayıt defteri alt anahtarını bulun ve tıklatın:

   ```console
   HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\
   ```

8. Yukarıdaki tabloda zaten değerler varsa, bunları değiştirin ve sonra Kayıt Defteri Düzenleyicisi'den çıkın. Yoksa, Düzen menüsünde Yeni'nin üzerine **gelin** ve eksik tuşlar için **DWORD Değeri'ne** tıklayın. 

9. Örneğin, *EnableADAL tuşu* yoksa, *EnableADAL yazın ve* Enter tuşuna **basın.**

10. *EnableADAL'a sağ tıklayın* ve sonra Değiştir'e **tıklayın.**

11. Değer **verisi** kutusuna **1 yazın ve** Tamam'a **tıklayın.**

12. Gerekirse, Sürüm anahtarı için de aynı işlemi izleyin. 

13. **Kayıt Defteri Düzenleyicisi'nden çıkın.**

Kayıt defteri anahtarlarını ayarlaytıktan sonra, Office 2013 uygulamalarını, Microsoft 365 ile Çok Faktörlü Kimlik Doğrulaması [(MFA)](set-up-multi-factor-authentication.md) kullanmak üzere Microsoft 365. 
  
Şu anda istemci uygulamalarından herhangi birinde oturum açmış durumdaysanız, değişikliğin geçerlilik kazanması için oturumu kapatıp yeniden oturum açmanız gerekir. Aksi takdirde, kimlik kuruluna kadar MRU ve dolaşım ayarları kullanılamaz.
  
## <a name="disable-modern-authentication-on-devices"></a>Cihazlarda modern kimlik doğrulamayı devre dışı bırakma

Bir cihazda modern kimlik doğrulamayı devre dışı bırakmak için aşağıdaki kayıt defteri anahtarlarını ayarlayın:

<br>

****

|Kayıt defteri anahtarı|Tür|Değer|
|:---|:---:|---:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|
   
## <a name="related-content"></a>İlgili içerik

[Office 2013'te ikinci bir doğrulama yöntemiyle oturum açma](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (makale)\
[Outlook istemleri doğrular ve](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) bu parolaya bağlanmak için Modern Kimlik Office 365 kullanmaz (makale)
