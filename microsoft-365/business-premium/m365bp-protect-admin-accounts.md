---
title: Microsoft 365 İş Ekstra'de yönetici hesaplarınızı koruma
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Microsoft 365 İş Ekstra'da yönetici hesaplarınızı ayarlamayı ve korumayı öğrenin.
ms.openlocfilehash: a4f6265fd47a449c4768e7aef82ad6fdc004011f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631838"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra'de yönetici hesaplarınızı koruma

Yönetici hesapları yükseltilmiş ayrıcalıklarla birlikte geldiğinden, bilgisayar korsanları ve siber suçlular için değerli hedeflerdir. Bu makalede şunlar açıklanmaktadır:

- [Acil durumlar için başka bir yönetici hesabı ayarlama](#create-other-admin-accounts).
- [Acil durum yönetici hesabı oluşturma](#create-an-emergency-admin-account).
- [Kendiniz için bir kullanıcı hesabı oluşturma](#create-a-user-account-for-yourself).
- [Yönetici hesaplarını koruma](#protect-admin-accounts).
- [Ek öneriler](#additional-recommendations) ve [bir sonraki hedefiniz](#next-objective).

Microsoft 365'e kaydolup bilgilerinizi girdiğinizde otomatik olarak Genel Yönetici olursunuz (Genel yönetici olarak da adlandırılır). Genel yönetici, kullanıcı hesaplarının ve Microsoft yönetim merkezindeki diğer tüm ayarların ([https://admin.microsoft.com](https://admin.microsoft.com) ) nihai denetimine sahiptir, ancak farklı erişim derecelerine sahip birçok farklı türde yönetici hesabı vardır. Her [yönetici rolü](/office365/admin/add-users/about-admin-roles) türü için farklı erişim düzeyleri hakkında bilgi için yönetici rolleri hakkında bilgi için bkz.

## <a name="create-other-admin-accounts"></a>Diğer yönetici hesaplarını oluşturma

Yalnızca Microsoft 365 yönetimi için yönetici hesaplarını kullanın. Yöneticilerin, Office uygulamalarını düzenli olarak kullanmaları için ayrı bir kullanıcı hesabı olması ve yalnızca hesap ve cihazları yönetmek için gerektiğinde ve diğer yönetici işlevleri üzerinde çalışırken yönetici hesaplarını kullanmaları gerekir. Ek lisanslar için ödeme yapmak zorunda kalabilmeniz için yönetici hesaplarınızdan Microsoft 365 lisansını kaldırmanız da iyi bir fikirdir.

Yöneticiye başka bir güvenilir çalışana erişim vermek için en az bir Genel yönetici hesabı daha ayarlamak istersiniz. Kullanıcı yönetimi için ayrı yönetici hesapları da oluşturabilirsiniz (bu role **Kullanıcı yönetimi yöneticisi** adı verilir). Daha fazla bilgi için bkz. [yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).

> [!IMPORTANT]
> Bir yönetici hesabı kümesi ayarlamanızı önersek de, kuruluşunuz için genel yönetici sayısını sınırlamak istersiniz. Ayrıca, en az ayrıcalıklı erişim kavramına bağlı kalarak yalnızca işlerini gerçekleştirmek için gereken verilere ve işlemlere erişim izni vermenizi öneririz. [En düşük ayrıcalık ilkesi hakkında daha fazla bilgi edinin](/azure/active-directory/develop/secure-least-privileged-access). 

Daha fazla yönetici hesabı oluşturmak için:

 1. <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve sol gezinti bölmesinde **Kullanıcılar** \> **Etkin kullanıcılar'ı** seçin.

    ![Sol gezinti bölmesinde Kullanıcılar'ı ve ardından Etkin kullanıcılar'ı seçin.](../media/Activeusers.png)

 2. **Etkin kullanıcılar** sayfasında, sayfanın üst kısmındaki **Kullanıcı ekle'yi** seçin. 

 3. **Kullanıcı ekle** panelinde ad ve kullanıcı adı bilgileri gibi temel bilgileri girin.

 4. **Ürün lisansları** bilgilerini girin ve ayarlayın.

 5. **İsteğe bağlı ayarlar'da**, uygunsa Yönetici merkezi erişimi ekleme dahil olmak üzere kullanıcının rolünü tanımlayın.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Yeni kullanıcı rollerini tanımlayın.":::

 6. Ayarlarınızı tamamlayın ve gözden geçirin ve ayrıntıları onaylamak için **Eklemeyi bitir'i** seçin.

## <a name="create-an-emergency-admin-account"></a>Acil durum yönetici hesabı oluşturma

Ayrıca, yanlışlıkla kendinizi kilitlememek için çok faktörlü kimlik doğrulaması (MFA) ile ayarlanmamış bir yedekleme hesabı da oluşturmanız gerekir (örneğin, ikinci bir doğrulama biçimi olarak kullandığınız telefonunuzu kaybederseniz). Bu hesabın parolasının bir tümcecik veya en az 16 karakter uzunluğunda olduğundan emin olun. Bu acil durum yönetici hesabı genellikle "kırılan hesap" olarak adlandırılır.

## <a name="create-a-user-account-for-yourself"></a>Kendiniz için bir kullanıcı hesabı oluşturma

Yöneticiyseniz, postayı denetleme gibi normal iş görevleri için bir kullanıcı hesabına ihtiyacınız vardır. Hesaplarınızı adlandırarak hangisinin hangisi olduğunu bilin. Örneğin, yönetici kimlik bilgileriniz  *Alice.Chavez <span></span>@Contoso.org* ve normal kullanıcı hesabınız *alice <span></span>@Contoso.com* gibi olabilir.

Yeni bir kullanıcı hesabı oluşturmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve sol gezinti bölmesinde **Kullanıcılar** \> **Etkin kullanıcılar'ı** seçin.

2. **Etkin kullanıcılar** sayfasında, sayfanın üst kısmındaki **Kullanıcı ekle'yi** seçin ve **Kullanıcı ekle** panelinde adı ve diğer bilgileri girin.

3. **Ürün Lisansları** bölümünde, **Microsoft 365 İş Ekstra (yönetici erişimi yok)** onay kutusunu seçin.

4. **İsteğe bağlı ayarlar** bölümünde, **Kullanıcı (yönetim merkezi erişimi yok)** için varsayılan radyo düğmesini seçili bırakın.

5. Ayarlarınızı tamamlayın ve gözden geçirin ve ayrıntıları onaylamak için **Eklemeyi bitir'i** seçin.

## <a name="protect-admin-accounts"></a>Yönetici hesaplarını koruma

Tüm yönetici hesaplarınızı korumak için şu önerileri izlediğinizden emin olun:

- Tüm yönetici hesaplarının parolasız kimlik doğrulaması (Windows Hello veya kimlik doğrulayıcı uygulaması gibi) veya MFA kullanmasını zorunlu kılar. Parolasız kimlik doğrulamasının neden önemli olduğu hakkında daha fazla bilgi edinmek için [bkz. Microsoft Güvenliği teknik incelemesi: Parolasız koruma](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2KEup).

- Yöneticiler için özel izinler kullanmaktan kaçının. Belirli kullanıcılara izin vermek yerine Azure Active Directory'deki (Azure AD) roller aracılığıyla izinler atayın. Ayrıca, yalnızca eldeki görevi gerçekleştirmek için gereken verilere ve işlemlere erişim izni verin. [Azure AD'da en az ayrıcalıklı roller hakkında bilgi edinin](/azure/active-directory/roles/delegate-by-task).

- Mümkün olduğunda izinleri atamak için yerleşik rolleri kullanın. Azure rol tabanlı erişim denetimi (RBAC) kullanabileceğiniz çeşitli yerleşik rollere sahiptir. [Yerleşik Azure AD roller hakkında daha fazla bilgi edinin](/azure/active-directory/roles/permissions-reference).

## <a name="additional-recommendations"></a>Ek öneriler

- Yönetici hesaplarını kullanmadan önce, kişisel e-posta hesapları da dahil olmak üzere tüm ilgisiz tarayıcı oturumlarını ve uygulamalarını kapatın. Özel veya gizli tarayıcı pencerelerinde de kullanabilirsiniz.

- Yönetici görevlerini tamamladıktan sonra tarayıcı oturumunu kapatmış olmanız gerekir.

## <a name="next-objective"></a>Sonraki hedef

[Güvenlik varsayılanlarını açma adımlarını](m365bp-conditional-access.md) izleyin.

