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
description: Eski bir çalışanın tüm kullanıcı verilerini kaydedip erişdikten sonra, Microsoft 365 yönetim merkezi eski çalışanın hesabını silebilirsiniz.
ms.openlocfilehash: d6e53dd8d14add9383e3eff9d3c1d90a5087ec45
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436283"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>7. Adım - Eski çalışanın kullanıcı hesabını silme

Eski çalışanın tüm kullanıcı verilerini kaydedip eriştikten sonra eski çalışanın hesabını silebilirsiniz.

> [!IMPORTANT]
> E-posta iletme özelliğini ayarladıysanız veya paylaşılan posta kutusuna dönüştürdüyseniz, hesabı silmeyin. Hem iletme özelliğinin hem de paylaşılan posta kutusunun dayanak noktası olarak bu hesaba ihtiyacı vardır.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Silmek istediğiniz çalışanın adını seçin.
3. Kullanıcının adının altında **Kullanıcıyı sil'i** seçin. Bu kullanıcı için istediğiniz seçenekleri belirleyin ve ardından **Kullanıcıyı sil'i** seçin. Bu kullanıcının e-postasına ve OneDrive başka bir kullanıcıya zaten erişim verdiyseniz, bunu burada tekrar yapmanız gerekmez.

Bir kullanıcıyı sildiğinizde, hesabı yaklaşık 30 gün süreyle devre dışı bırakılır. Hesap kalıcı olarak silinmeden önce hesabı geri yüklemek için bu kadar süreniz vardır.

## <a name="watch-delete-a-former-employees-user-account"></a>İzleme: Eski bir çalışanın kullanıcı hesabını silme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

Bu videoyu faydalı bulduysanız, [küçük işletmelere ve Microsoft 365’i ilk kez kullananlara yönelik eğitim serisinin tamamına göz atın](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>Kuruluşunuzda Active Directory kullanılıyor mu?

Kuruluşunuz kullanıcı hesaplarını yerel bir Active Directory ortamından Microsoft 365 eşitlerse, bu kullanıcı hesaplarını yerel Active Directory hizmetinizde silmeniz ve geri yüklemeniz gerekir. Bunları Office 365'te silemez veya geri yükleyemezsiniz.

Active Directory'de kullanıcı hesabını silmeyi ve geri yüklemeyi öğrenmek için bkz. [Kullanıcı Hesabını Silme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
Azure Active Directory kullanıyorsanız [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet'ine bakın.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Bir çalışanın e-posta oturumunu sonlandırma hakkında bilmeniz gerekenler

Burada, bir çalışanın e-postadan (Exchange) nasıl çıkarılacağı ile ilgili bilgileri bulabilirsiniz.

<br>

****

|Ne yapabilirsiniz?|Nasıl yapmalısınız?|
|:-----|:-----|
|Oturumu sonlandırma (Web üzerinde Outlook, Outlook, Exchange Active Sync gibi) ve yeni bir oturum açmaya zorlama|Parolayı sıfırlayın|
|Oturumu sonlandırma ve sonraki oturumlara erişimi engelleme (tüm protokoller için)|Hesabı devre dışı bırakın. Örneğin, (Exchange yönetim merkezinde veya PowerShell kullanarak): <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|Belirli bir protokolün (ActiveSync gibi) oturumunu sonlandırma|Protokolü devre dışı bırakın. Örneğin, (Exchange yönetim merkezinde veya PowerShell kullanarak): <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
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

[Kullanıcıyı geri yükleme](restore-user.md) (makale)

[Parolaları sıfırlama](reset-passwords.md) (makale)
