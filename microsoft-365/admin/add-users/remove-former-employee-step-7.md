---
title: 7. Adım - Eski çalışanın kullanıcı hesabını silme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Eski çalışanın kullanıcı hesabını silmek için bu adımları izleyin.
ms.openlocfilehash: 631405b66c777060463a4e98620ff3c8b06c7e77
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983494"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>7. Adım - Eski çalışanın kullanıcı hesabını silme

Eski çalışanın tüm kullanıcı verilerini kaydedip eriştikten sonra eski çalışanın hesabını silebilirsiniz.

> [!IMPORTANT]
> E-posta iletme özelliğini ayarladıysanız veya paylaşılan posta kutusuna dönüştürdüyseniz, hesabı silmeyin. Hem iletme özelliğinin hem de paylaşılan posta kutusunun dayanak noktası olarak bu hesaba ihtiyacı vardır.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Silmek istediğiniz çalışanın adını seçin.
3. Kullanıcının adının altında, Kullanıcı **sil'i seçin**. Bu kullanıcı için istediğiniz seçenekleri belirleyin ve ardından Kullanıcı **sil'i seçin**. Bu kullanıcının e-posta adresine ve e-posta adresine zaten başka bir kullanıcı OneDrive, bu şeyi burada yeniden yapmak zorunda değilsiniz.

Bir kullanıcıyı sildiğinizde, hesabı yaklaşık 30 gün süreyle devre dışı bırakılır. Hesap kalıcı olarak silinmeden önce hesabı geri yüklemek için bu kadar süreniz vardır.

## <a name="watch-delete-a-former-employees-user-account"></a>İzle: Eski çalışanın kullanıcı hesabını silme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

Bu videoyu faydalı bulduysanız, [küçük işletmelere ve Microsoft 365’i ilk kez kullananlara yönelik eğitim serisinin tamamına göz atın](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>Kuruluşunuzda Active Directory kullanılıyor mu?

If your organization synchronizes user accounts to Microsoft 365 from a local Active Directory environment, you must delete and restore those user accounts in your local Active Directory service. Bunları Office 365'te silemez veya geri yükleyemezsiniz.

Active Directory'de kullanıcı hesabını silmeyi ve geri yüklemeyi öğrenmek için bkz [. Kullanıcı Hesabı Silme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
Azure Active Directory kullanıyorsanız bkz. [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Bir çalışanın e-posta oturumunu sonlandırma hakkında bilmeniz gerekenler

Burada, bir çalışanın e-postadan (Exchange) nasıl çıkarılacağı ile ilgili bilgileri bulabilirsiniz.

<br>

****

|Ne yapabilirsiniz?|Nasıl yapmalısınız?|
|:-----|:-----|
|Oturumu sonlandırma (Web üzerinde Outlook, Outlook, Exchange Active Sync gibi) ve yeni bir oturum açmaya zorlama|Parolayı sıfırlayın|
|Oturumu sonlandırma ve sonraki oturumlara erişimi engelleme (tüm protokoller için)|Hesabı devre dışı bırakın. Örneğin, (Exchange veya PowerShell kullanarak): <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|Belirli bir protokolün (ActiveSync gibi) oturumunu sonlandırma|Protokolü devre dışı bırakın. Örneğin, (Exchange veya PowerShell kullanarak): <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

Yukarıdaki işlemler üç yerde yapılabilir:
  
<br>

****

|Oturumu burada sonlandırırsanız|Bu kadar zaman alır|
|---|---|
|Exchange yönetim merkezinde veya PowerShell kullanarak|Beklenen gecikme 30 dakikadır|
|Azure Active Directory yönetim merkezinde|Beklenen gecikme 60 dakikadır|
|Şirket içi ortamında|Beklenen gecikme 3 saat veya daha fazladır|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>Hesap sonlandırma işlemi için hızlı yanıt alma

**En Hızlı**: Exchange yönetim merkezini (PowerShell kullanarak) veya Azure Active Directory yönetim merkezini kullanın. Şirket içi ortamında, değişikliğin DirSync üzerinden eşitlenmesi birkaç saat sürebilir.
  
**Şirket içinde Exchange Datacenter'da bulunan kullanıcılar için en hızlısı**: Azure Active Directory yönetim merkezini/Exchange yönetim merkezini kullanarak oturumu sonlandırın VE değişiklikleri şirket içi ortamda da yapın. Aksi takdirde DirSync, Azure Active Directory yönetim merkezindeki/Exchange yönetim merkezindeki değişikliğin üzerine yazar.
  
## <a name="related-content"></a>İlgili içerik

[Bir kullanıcı geri yükleme](restore-user.md) (makale)

[Parolaları sıfırlama](reset-passwords.md) (makale)
