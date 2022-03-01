---
title: 1. Adım - Bir çalışanın iş yer açması için Microsoft 365
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
description: Eski çalışanın oturum açması ve bu hizmetlere erişimi Microsoft 365 engelin.
ms.openlocfilehash: 5643c12f46fb09f76f16dc2632baf1538d358dd5
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012874"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>1. Adım - Eski bir çalışanın oturum açmasını ve bu hizmetlere erişimi Microsoft 365 engelleme

Kullanıcının oturum açma erişimini hemen engellemeniz gerekirse, parolasını sıfırlamanız gerekir. Bu adımda, oturum açma için kullanıcının oturumlarını Microsoft 365.

> [!NOTE]
> Diğer yöneticiler için oturum açmanın başlatılmış olması için genel yönetici olmak gerekir. Yönetici olmayan kullanıcılar için, bu eylemi gerçekleştirmek için Kullanıcı Yöneticisi veya Yardım Masası Yöneticisi kullanıcısı kullanabilirsiniz. [Yönetici Rolleri hakkında daha fazla bilgi](about-admin-roles.md)

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Kullanıcı adının yanındaki kutuyu seçin ve sonra Parolayı **sıfırla'yı seçin**.
3. Yeni bir parola girin ve Sıfırla'yı **seçin**. (Ona göndermeyin.)
4. Özellikler bölmesine gitmek için kullanıcının adını seçin ve Hesap sekmesinde **Tüm** oturumların oturumu **kapatma seçeneğini seçin**.

Bir saat içinde veya o kullanıcı geçerli Microsoft 365 sayfadan ayrıldıktan sonra yeniden oturum açması istenir. Erişim belirteci bir saat uygun olduğu için zaman çizelgesi, o belirteçte ne kadar zaman kalan süreye ve geçerli web sayfasının dışında çıkıp çıkmalarına bağlıdır.
  
> [!IMPORTANT]
> Kullanıcı posta kutusunun Web üzerinde Outlook tıklarsanız, hemen dışarı atmayabilirsiniz. Oturum açma veya tarayıcısını yenileme gibi farklı bir kutucuk OneDrive anda, oturum açma başlatılır.
  
PowerShell kullanarak kullanıcının oturumlarını hemen imzalamak için [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) cmdlet'ine bakın.
  
Bir kişiyi e-postadan çıkarmak için gerekenler hakkında daha fazla bilgi için bkz. [Bir çalışanın e-posta oturumunu sonlandırma hakkında bilmeniz gerekenler](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Eski çalışanın hizmetlere erişimini Microsoft 365 engelleme

> [!IMPORTANT]
 > Bir hesabı engellemenin etkili bir şekilde 24 saate kadar sürebilir. Kullanıcının oturum açma erişimini hemen engellemeniz gerekirse, yukarıdaki adımları izleyin ve parolasını sıfırlayın.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Engellemek istediğiniz çalışanın adını seçin ve kullanıcı adının altında Bu kullanıcıyı engelle simgesini **seçin**.
3. Kullanıcının **oturum açmasını engelle'yi seçin ve** sonra da Kaydet'i **seçin**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Eski çalışanın e-postaya Exchange Online erişmesini engelleme

Microsoft 365 aboneliğinizin bir parçası olarak e-postanız varsa Exchange yönetim merkezinde oturum açmalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a> ve eski çalışanın e-postalarına erişimini engellemek için bu adımları izleyin.
  
1. Alıcı Posta Exchange için > **merkezine** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">gidin</a>.
1. Listeden kullanıcı posta kutusunu seçin ve sonra Ayrıntılar Bölmesi'nde *(sağ* tarafta) E-posta uygulamaları'nın altında E-posta uygulamalarını yönet **ayarlarını yönet'i seçin**. Tüm **seçenekler** için kaydırıcıyı kapatma; **Mobil (Exchange ActiveSync)**, **Web üzerinde Outlook**, **Outlook masaüstü (MAPI)**, **Exchange web** hizmetleri, **POP3** ve **IMAP**.
1. **Kaydet**'i seçin.

## <a name="related-content"></a>İlgili içerik

[Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center) (makale)\

[Bir kullanıcı geri yükleme](restore-user.md) (makale)
