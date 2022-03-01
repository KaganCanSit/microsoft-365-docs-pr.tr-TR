---
title: Kısıtlanmış kullanıcılar portalında engellenen kullanıcıları kaldırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: Yöneticiler, kullanıcı kaldırmayı öğrenmek için portalda Kısıtlı kullanıcılar Microsoft 365 Defender. Kullanıcılar, genellikle hesabın tehlikeye atılmış sonucu olarak, giden istenmeyen posta göndermek için Kısıtlanmış kullanıcılar portalına eklenir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 66b810f7bb6381d405ee7ffc0d6b1cf7a10f2bf2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033363"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Engellenen kullanıcıları Microsoft 365'te Kısıtlanmış kullanıcılar portalında Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kullanıcı, hizmet sınırlarında veya giden istenmeyen posta ilkesinde belirtilen giden gönderme sınırlarından birini aşarsa[, kullanıcının](configure-the-outbound-spam-policy.md) e-posta göndermesi kısıtlanır, ancak yine de e-posta almaya devamebilir.[](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options)

Kullanıcı, kullanıcı portalının Kısıtlı **kullanıcılar** Microsoft 365 Defender eklenir. E-posta göndermeye çalışsalar, ileti [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) hata kodu ve aşağıdaki metinle birlikte teslim edilemedi raporunda (NDR veya geri dönen iletiler olarak da bilinir) döndürülür:

> "Geçerli bir gönderen olarak tanınmadınız için iletiniz teslim edilmedi. Bunun en yaygın nedeni, e-posta adresinizin istenmeyen posta gönderme şüphesi ve artık e-posta göndermesine izin verilmemektedir.  Yardım için e-posta yöneticinize başvurun. Uzak Sunucu '550 5.1.8 Erişim reddedildi, giden hatalı gönderen."

Yöneticiler Microsoft 365 Defender PowerShell'de veya Exchange Online sayfasından kullanıcıları kaldırabilir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kısıtlanmış kullanıcılar **sayfasına gitmek için** kullanın <https://security.microsoft.com/restrictedusers>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Kısıtlanmış kullanıcılar portalında kullanıcıları kaldırmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi **rol gruplarının** **üyesi olun** .
  - Kısıtlanmış kullanıcılar portalına salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Giden e-posta sınırlarını aşan bir gönderen, güvenliği aşılmış bir hesabın göstergesidir. Kısıtlanmış kullanıcılar portalında kullanıcı kaldırmadan önce, hesabının kontrolünü yeniden kazanmak için gerekli adımları takip etmeye emin olun. Daha fazla bilgi için bkz[. Güvenliği tehlikeye atılmış bir e-posta hesabını Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Kısıtlı Microsoft 365 Defender listesinden bir kullanıcı kaldırmak için Kullanıcı Ekle portalını kullanma

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve işbirliği **& Gözden** \> **Geçirme** \> **Kısıtlanmış kullanıcılar'a gidin**. Doğrudan Kısıtlanmış kullanıcılar **sayfasına gitmek için** kullanın <https://security.microsoft.com/restrictedusers>.

2. Kısıtlanmış **kullanıcılar sayfasında** , kullanıcıya tıklayarak engelini kaldırmak istediğiniz kullanıcıyı bulun ve seçin.

3. Görüntülenen **Engellemeyi Kaldır** eylemini tıklatın.

4. Görüntülenen **Kullanıcının engellemesini kaldır** açılır bölmesinde, kısıtlanmış hesap hakkında ayrıntıları okuyun. Hesabın güvenliği ihlal edilmiş olması durumunda doğru eylemleri gerçekleştiresiniz diye önerilere göz atabilirsiniz.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Sonraki ekranda, gelecekte ödünleri önlemeye yardımcı olacak öneriler vardır. Çok faktörlü kimlik doğrulamasını (MFA) etkinleştirmek ve parolayı sıfırlamak iyi bir savunmadır.

   Bitirdikten sonra Gönder'e **tıklayın**.

6. Değişikliği **onaylamak** için Evet'e tıklayın.

   > [!NOTE]
   > Tüm kısıtlamaların kullanıcıdan kaldırılması 1 saat kadar zaman alabiliyor.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Kısıtlanmış kullanıcılar için uyarı ayarlarını doğrulama

Kullanıcı e-posta **göndermeyle kısıtlandı** adlı varsayılan uyarı ilkesi, kullanıcıların giden posta göndermesi engel olduğunda yöneticilere otomatik olarak bildirim gönderir. Bu ayarları doğrular ve bildirim eklemek için başka kullanıcılar  eklersiniz. Uyarı ilkeleri hakkında daha fazla bilgi için bkz[. İlke ve Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Uyarıların çalışması için denetim günlüğü aramanın açık olması gerekir. Daha fazla bilgi için [bkz. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

1. Microsoft 365 Defender portalında, E-posta ve İşbirliği **& ve** \> **Kurallar & ilkesi'ne** \> **gidin**.

2. Uyarı ilkesi **sayfasında** , Kullanıcı e-posta gönderme kısıtlaması **adlı uyarıyı bulun ve seçin**. İlkeleri adlarına göre sıralanmış veya Arama **kutusunu kullanarak** ilkeyi bulabilirsiniz.

3. Görüntülenen **E-posta göndermeyle kısıtlanmış kullanıcı** açılır sayfasında, aşağıdaki ayarları doğrulayın veya yapılandıryın:
   - **Durum**: Uyarının Iki durumlu düğmeyi açık ![olduğunu doğrulayın](../../media/scc-toggle-on.png).
   - **E-posta** alıcıları: **Görüntülenen Alıcıları** düzenle açılır sayfasında Düzenle'ye tıklayın **ve şu ayarları doğrulayın** veya yapılandır:
     - **E-posta bildirimleri gönderme**: Bunun seçili olduğunu doğrulayın (**On**).
     - **E-posta** alıcıları: Varsayılan değer **TenantAdmins değeridir** (başka bir ifadeyle Genel **yönetici üyeleri** ). Daha fazla alıcı eklemek için, kutunun boş bir alanına tıklayın. Alıcıların listesi görüntülenir ve filtrelemek ve bir alıcı seçmek için ad yazmaya başlayabilirsiniz. Var olan bir alıcıyı kaldır simgesine tıklayarak kutudan ![kaldırabilirsiniz.](../../media/m365-cc-sc-remove-selection-icon.png) yazın.
     - **Günlük bildirim sınırı**: Varsayılan değer Sınır **yok'tır** , ancak günlük en fazla bildirim sayısı için bir sınır seçin.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

4. Kullanıcı tarafından **e-posta göndermeyle ilgili olarak kısıtlanan iletiye** geri dönerek Kapat'ı **tıklatın**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Kullanıcıları Exchange Online ve Kısıtlanmış kullanıcılar listesinden kaldırmak için PowerShell'i kullanma

E-posta göndermesi kısıtlanmış kullanıcıların listesini görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-BlockedSenderAddress
```

Belirli bir kullanıcıyla ilgili ayrıntıları görüntülemek için, e-posta \<emailaddress\> adresiyle değiştirin ve aşağıdaki komutu çalıştırın:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Kısıtlanmış kullanıcılar listesinden bir kullanıcı kaldırmak için, o kullanıcının e-posta \<emailaddress\> adresiyle değiştirin ve aşağıdaki komutu çalıştırın:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
