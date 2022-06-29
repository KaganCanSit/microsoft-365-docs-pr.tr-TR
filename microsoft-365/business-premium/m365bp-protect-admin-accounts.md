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
ms.openlocfilehash: e20fa8f408668287065f6aa1e30490fd8e3c2fec
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489935"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra'de yönetici hesaplarınızı koruma

Yönetici hesapları yükseltilmiş ayrıcalıklarla birlikte geldiğinden, bilgisayar korsanları ve siber suçlular için değerli hedeflerdir. Bu makalede şunlar açıklanmaktadır:

- Acil durumlar için ek yönetici hesabı ayarlama.
- Bu hesapları koruma.

Microsoft 365'e kaydolup bilgilerinizi girdiğinizde otomatik olarak Genel Yönetici olursunuz (Genel yönetici olarak da adlandırılır). Genel yönetici, kullanıcı hesaplarının ve Microsoft yönetim merkezindeki diğer tüm ayarların ([https://admin.microsoft.com](https://admin.microsoft.com) ) nihai denetimine sahiptir, ancak farklı erişim derecelerine sahip birçok farklı türde yönetici hesabı vardır. Her [yönetici rolü](/office365/admin/add-users/about-admin-roles) türü için farklı erişim düzeyleri hakkında bilgi için yönetici rolleri hakkında bilgi için bkz.

## <a name="create-additional-admin-accounts"></a>Ek yönetici hesapları oluşturma

Yalnızca yönetim için yönetici hesaplarını kullanın. Yöneticiler, Office uygulamalarının düzenli kullanımı için ayrı bir kullanıcı hesabına sahip olmalı ve yalnızca hesapları ve cihazları yönetmek için gerektiğinde ve diğer yönetici işlevleri üzerinde çalışırken yönetim hesaplarını kullanmalıdır. Ayrıca, microsoft 365 lisansını yönetici hesaplarından kaldırmak da iyi bir fikirdir, böylece bu lisanslar için ödeme yapmak zorunda değilsiniz.

Yöneticiye başka bir güvenilir çalışana erişim vermek için en az bir ek Genel yönetici hesabı ayarlamak istersiniz. Kullanıcı yönetimi için ayrı yönetici hesapları da oluşturabilirsiniz (bu role **Kullanıcı yönetimi yöneticisi** adı verilir). Daha fazla bilgi için bkz. [yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).

Ek yönetici hesapları oluşturmak için:

 1. <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve sol gezinti bölmesinde **Kullanıcılar** \> **Etkin kullanıcılar'ı** seçin.

    ![Sol gezinti bölmesinde Kullanıcılar'ı ve ardından Etkin kullanıcılar'ı seçin.](../media/Activeusers.png)

 1. **Etkin kullanıcılar** sayfasında, sayfanın üst kısmındaki **Kullanıcı ekle'yi** seçin. 

 1. **Kullanıcı ekle** panelinde ad ve kullanıcı adı bilgileri gibi temel bilgileri girin.

 1. **Ürün lisansları** bilgilerini girin ve ayarlayın.

 1. **İsteğe bağlı ayarlar'da**, uygunsa Yönetici merkezi erişimi ekleme dahil olmak üzere kullanıcının rolünü tanımlayın.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Yeni kullanıcı rollerini tanımlayın.":::

 1. Ayarlarınızı tamamlayın ve gözden geçirin ve ayrıntıları onaylamak için **Eklemeyi bitir'i** seçin.

## <a name="create-an-emergency-admin-account"></a>Acil durum yönetici hesabı oluşturma

Ayrıca, yanlışlıkla kendinizi kilitlememek için çok faktörlü kimlik doğrulaması (MFA) ile ayarlanmamış bir yedekleme hesabı da oluşturmanız gerekir (örneğin, ikinci bir doğrulama biçimi olarak kullandığınız telefonunuzu kaybederseniz). Bu hesabın parolasının bir tümcecik veya en az 16 karakter uzunluğunda olduğundan emin olun. Bu genellikle "kırılan hesap" olarak adlandırılır.

## <a name="create-a-user-account-for-yourself"></a>Kendiniz için bir kullanıcı hesabı oluşturma

Posta denetimi de dahil olmak üzere kuruluşunuzla işbirliğine katılmak için kullanıcı hesabınızı kullanın. Bu, yönetici kimlik bilgilerinizin  *Alice.Chavez <span></span>@Contoso.org* gibi olabileceği ve normal kullanıcı hesabınızın *Alice <span></span>@Contoso.com* gibi olabileceği anlamına gelir.

Yeni bir kullanıcı hesabı oluşturmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve sol gezinti bölmesinde **Kullanıcılar** \> **Etkin kullanıcılar'ı** seçin.

1. **Etkin kullanıcılar** sayfasında, sayfanın üst kısmındaki **Kullanıcı ekle'yi** seçin ve **Kullanıcı ekle** panelinde adı ve diğer bilgileri girin.

1. **Ürün Lisansları** bölümünde, **Microsoft 365 İş Ekstra (yönetici erişimi yok)** onay kutusunu seçin.

1. **İsteğe bağlı ayarlar** bölümünde, **Kullanıcı (yönetim merkezi erişimi yok)** için varsayılan radyo düğmesini seçili bırakın.

1. Ayarlarınızı tamamlayın ve gözden geçirin ve ayrıntıları onaylamak için **Eklemeyi bitir'i** seçin.

## <a name="additional-recommendations"></a>Ek öneriler

- Yönetici hesaplarını kullanmadan önce, kişisel e-posta hesapları da dahil olmak üzere tüm ilgisiz tarayıcı oturumlarını ve uygulamalarını kapatın. Özel veya gizli tarayıcı pencerelerinde de kullanabilirsiniz.

- Yönetici görevlerini tamamladıktan sonra tarayıcı oturumunu kapatmış olmanız gerekir.

## <a name="next-objective"></a>Sonraki hedef

[Güvenlik varsayılanlarını açma adımlarını](m365bp-conditional-access.md) izleyin.

