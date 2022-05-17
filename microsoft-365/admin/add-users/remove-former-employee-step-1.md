---
title: 1. Adım - Eski bir çalışanın oturum açmasını engelleme ve Microsoft 365 hizmetlerine erişimi engelleme
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
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Genel yöneticiler, eski bir çalışanın oturum açmasını ve Microsoft 365 hizmetlerine erişimini engelleyebilir.
ms.openlocfilehash: eec436a182f5e065f445167dea38fe99390ca105
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436657"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>1. Adım - Eski bir çalışanın oturum açmasını engelleme ve Microsoft 365 hizmetlerine erişimi engelleme

Bir kullanıcının oturum açma erişimini hemen engellemeniz gerekiyorsa, parolasını sıfırlamanız gerekir. Bu adımda, kullanıcının Microsoft 365 oturumunu kapatmaya zorlayın.

> [!NOTE]
> Diğer yöneticiler için oturumu kapatmayı başlatmak için genel yönetici olmanız gerekir. Yönetici olmayan kullanıcılar için, bu eylemi gerçekleştirmek için Bir Kullanıcı Yöneticisi veya Yardım Masası Yöneticisi kullanıcısı kullanabilirsiniz. [Yönetici Rolleri hakkında daha fazla bilgi edinin](about-admin-roles.md)

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Kullanıcı adının yanındaki kutuyu seçin ve ardından **Parolayı sıfırla'yı** seçin.
3. Yeni bir parola girin ve **sıfırla'yı** seçin. (Onlara göndermeyin.)
4. Özellikler bölmesine gitmek için kullanıcının adını seçin ve **Hesap** sekmesinde **Tüm oturumların oturumunu kapat'ı** seçin.

Bir saat içinde (veya bulundukları geçerli Microsoft 365 sayfasından ayrıldıktan sonra) yeniden oturum açmaları istenir. Erişim belirteci bir saat için iyidir, bu nedenle zaman çizelgesi bu belirteçte ne kadar süre kaldığına ve geçerli web sayfasından çıkıp çıkmadığına bağlıdır.
  
> [!IMPORTANT]
> Kullanıcı Web üzerinde Outlook içindeyse, yalnızca posta kutusuna tıklarsanız, hemen dışarı atılamayabilir. OneDrive gibi farklı bir kutucuk seçtikleri veya tarayıcılarını yeniledikleri anda oturum kapatma başlatılır.
  
Kullanıcının oturumunu hemen kapatmak için PowerShell'i kullanmak için [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) cmdlet'ine bakın.
  
Bir kişiyi e-postadan çıkarmak için gerekenler hakkında daha fazla bilgi için bkz. [Bir çalışanın e-posta oturumunu sonlandırma hakkında bilmeniz gerekenler](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Eski çalışanın Microsoft 365 hizmetlerine erişimini engelleme

> [!IMPORTANT]
 > Bir hesabın engellenmesinin etkili olması 24 saat kadar sürebilir. Kullanıcının oturum açma erişimini hemen engellemeniz gerekiyorsa yukarıdaki adımları izleyin ve parolasını sıfırlayın.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Engellemek istediğiniz çalışanın adını seçin ve kullanıcı adının altında **Bu kullanıcıyı engelle** simgesini seçin.
3. **Kullanıcının oturum açmasını engelle'yi** ve ardından **Kaydet'i** seçin.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Eski çalışanın e-postaya Exchange Online erişmesini engelleme

Microsoft 365 aboneliğinizin bir parçası olarak e-postanız varsa<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">, Exchange yönetim merkezinde</a> oturum açın ve eski çalışanınızın e-postasına erişmesini engellemek için bu adımları izleyin.
  
1. Exchange yönetim merkezine > **Alıcı Posta** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">Kutuları'na</a> gidin.
1. Listeden kullanıcı posta kutusunu seçin ve ardından *Ayrıntılar Bölmesi'nde* (sağ taraftaki) **E-posta uygulamaları** altında **E-posta uygulamaları ayarlarını yönet'i** seçin. Tüm seçenekler için kaydırıcıyı **kapatın**; **Mobil (Exchange ActiveSync)**, **Web üzerinde Outlook**, **Outlook masaüstü (MAPI)**, **Exchange web hizmetleri**, **POP3** ve **IMAP**.
1. **Kaydet**'i seçin.

## <a name="related-content"></a>İlgili içerik

[Exchange Online yönetim merkezini Exchange](/exchange/exchange-admin-center) (makale)\

[Kullanıcıyı geri yükleme](restore-user.md) (makale)
