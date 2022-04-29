---
title: Engellenen kullanıcıları Kısıtlı kullanıcılar portalından kaldırma
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
description: Yöneticiler, Microsoft 365 Defender portalındaki Kısıtlı kullanıcılar sayfasından kullanıcıları kaldırmayı öğrenebilir. Kullanıcılar, genellikle hesap güvenliğinin aşılmasına bağlı olarak giden istenmeyen posta göndermek için Kısıtlı kullanıcılar portalına eklenir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 229dfbb7a0441f4a6cb6632432c0032f4ce4308e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130746"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>engellenen kullanıcıları Microsoft 365'deki Kısıtlı kullanıcılar portalından kaldırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bir kullanıcı [, hizmet](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) sınırlarında veya [giden istenmeyen posta ilkelerinde](configure-the-outbound-spam-policy.md) belirtilen giden gönderme sınırlarından birini aşarsa, kullanıcının e-posta göndermesi kısıtlanır, ancak yine de e-posta alabilir.

Kullanıcı, Microsoft 365 Defender portalındaki **Kısıtlı kullanıcılar** sayfasına eklenir. E-posta göndermeye çalıştıklarında ileti, [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) hata kodu ve aşağıdaki metinle birlikte teslim edilmedi raporunda (NDR veya geri dönen ileti olarak da bilinir) döndürülür:

> "Geçerli bir gönderen olarak tanınmadığınız için iletiniz teslim edilemedi. Bunun en yaygın nedeni, e-posta adresinizin istenmeyen posta gönderdiğinden şüphelenilmiş olması ve artık e-posta göndermesine izin verilmemiş olmasıdır.  Yardım için e-posta yöneticinize başvurun. Uzak Sunucu '550 5.1.8 Erişim reddedildi, hatalı giden gönderen döndürdü."

Yöneticiler, Microsoft 365 Defender veya Exchange Online PowerShell'deki **Kısıtlı kullanıcılar** sayfasından kullanıcıları kaldırabilir.

## <a name="learn-more-on-restricted-entities"></a>Kısıtlı varlıklar hakkında daha fazla bilgi edinin

Kısıtlanmış varlık, gizliliği tehlikeye girmiş veya gönderme sınırını aşmış olduğundan e-posta göndermesi engellenmiş bir varlıktır.

2 tür kısıtlanmış varlık vardır: 

- **Kısıtlanmış kullanıcı**: Bir kullanıcının neden kısıtlandığını ve kısıtlanmış kullanıcıları nasıl işleyebileceğinizi öğrenin (bu makale).  

- **Kısıtlanmış bağlayıcı**: Bağlayıcının neden kısıtlandığı ve kısıtlanmış bağlayıcıların nasıl işlendiği hakkında daha fazla bilgi için bkz. [Kısıtlı varlıklar portalından engellenen bağlayıcıları kaldırma](remove-blocked-connectors.md). 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Kısıtlı kullanıcılar** sayfasına gitmek için kullanın<https://security.microsoft.com/restrictedusers>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Kısıtlı kullanıcılar portalından kullanıcıları kaldırmak için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Kısıtlı kullanıcılar portalına salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Giden e-posta sınırlarını aşan bir gönderen, güvenliği aşılmış bir hesabın göstergesidir. Kullanıcıyı Kısıtlı kullanıcılar portalından kaldırmadan önce, hesabın denetimini yeniden kazanmak için gerekli adımları izlediğinizden emin olun. Daha fazla bilgi için bkz. [Office 365'da güvenliği aşılmış bir e-posta hesabını yanıtlama](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Kullanıcıyı Kısıtlı kullanıcılar listesinden kaldırmak için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **Kısıtlı kullanıcıları** **gözden geçir'e** \> gidin. **Doğrudan Kısıtlı kullanıcılar** sayfasına gitmek için kullanın<https://security.microsoft.com/restrictedusers>.

2. **Kısıtlı kullanıcılar** sayfasında, engelini kaldırmak istediğiniz kullanıcıyı bulmak ve seçmek için kullanıcıya tıklayın.

3. Görüntülenen **Engellemeyi Kaldır** eylemine tıklayın.

4. Görüntülenen **Kullanıcının engellemesini kaldır** açılır öğesinde, kısıtlı hesap hakkındaki ayrıntıları okuyun. Hesabın gizliliğinin ihlal edilmesi durumunda uygun eylemleri gerçekleştirdiğinizden emin olmak için önerileri gözden geçirmeniz gerekir.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Sonraki ekranda gelecekteki güvenliğin aşılmasını önlemeye yardımcı olacak öneriler bulunur. Çok faktörlü kimlik doğrulamasını (MFA) etkinleştirmek ve parolayı sıfırlamak iyi bir savunmadır.

   İşiniz bittiğinde **Gönder'e** tıklayın.

6. Değişikliği onaylamak için **Evet'e** tıklayın.

   > [!NOTE]
   > Tüm kısıtlamaların kullanıcıdan kaldırılması 1 saat kadar sürebilir.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Kısıtlı kullanıcılar için uyarı ayarlarını doğrulama

**Kullanıcının e-posta göndermesi kısıtlandı** adlı varsayılan uyarı ilkesi, kullanıcıların giden posta göndermesi engellendiğinde yöneticileri otomatik olarak bilgilendirir. Bu ayarları doğrulayabilir ve bildirim için ek kullanıcılar ekleyebilirsiniz. Uyarı ilkeleri hakkında daha fazla bilgi için bkz[. Microsoft 365 uyarı ilkeleri](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Uyarıların çalışması için denetim günlüğü aramanın açık olması gerekir. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Uyarı ilkesi'ne** gidin. **Doğrudan Uyarı ilkesi** sayfasına gitmek için kullanın<https://security.microsoft.com/alertpolicies>.

2. **Uyarı ilkesi** sayfasında Kullanıcı'nın **e-posta göndermesi kısıtlandı** adlı uyarıyı bulun ve seçin. İlkeleri ada göre sıralayabilir veya **arama** kutusunu kullanarak ilkeyi bulabilirsiniz.

3. Kullanıcının görüntülenen **e-postayı göndermesi kısıtlandı** açılır öğesinde, aşağıdaki ayarları doğrulayın veya yapılandırın:
   - **Durum**: Uyarının açık ![olduğunu doğrulayın.](../../media/scc-toggle-on.png)
   - **E-posta alıcıları**: **Düzenle'ye** tıklayın ve görüntülenen **Alıcıları düzenle** açılır penceresinde aşağıdaki ayarları doğrulayın veya yapılandırın:
     - **E-posta bildirimleri gönder**: Bunun seçili olduğunu doğrulayın (**Açık**).
     - **E-posta alıcıları**: Varsayılan değer **TenantAdmins'tir** (genel **yönetici** üyeleri anlamına gelir). Daha fazla alıcı eklemek için kutunun boş bir alanına tıklayın. Alıcıların listesi görüntülenir ve bir alıcıyı filtrelemek ve seçmek için bir ad yazmaya başlayabilirsiniz. Kaldır simgesine tıklayarak ![kutudan var olan bir alıcıyı kaldırabilirsiniz.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.
     - **Günlük bildirim sınırı**: Varsayılan değer **Sınır yok'dur** , ancak günlük en fazla bildirim sayısı için bir sınır seçebilirsiniz.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

4. **Kullanıcının e-posta açılır öğesi göndermesi kısıtlandı** bölümüne geri dönüp **Kapat'a** tıklayın.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Exchange Online PowerShell kullanarak kullanıcıları Kısıtlı kullanıcılar listesinden görüntüleme ve kaldırma

E-posta göndermesi kısıtlanmış kullanıcıların listesini görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-BlockedSenderAddress
```

Belirli bir kullanıcıyla ilgili ayrıntıları görüntülemek için değerini e-posta adresiyle değiştirin \<emailaddress\> ve aşağıdaki komutu çalıştırın:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Bir kullanıcıyı Kısıtlı kullanıcılar listesinden kaldırmak için yerine e-posta adresini yazın \<emailaddress\> ve aşağıdaki komutu çalıştırın:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
