---
title: Yönetici hesaplarınızı koruma
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Yönetici hesaplarınızı ayarlamayı ve korumayı öğrenin.
ms.openlocfilehash: 32522596fc41c209d7c05173d75b36ab331fae5c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011835"
---
# <a name="protect-your-administrator-accounts"></a>Yönetici hesaplarınızı koruma

Yönetici hesapları yükseltilmiş ayrıcalıklarla sahip olduğundan, bunlar korsanlar ve siber suçlular için değerli hedeftir. Bu makalede şu açıklanmıştır:

- Acil durumlar için ek yönetici hesabı ayarlama.
- Bu hesapların korunması.

E-posta Microsoft 365 ve bilginizi girerseniz, otomatik olarak Genel yönetici olurnuz. Genel yönetici, Microsoft yönetim merkezinde kullanıcı hesaplarının ve tüm diğer ayarların tam denetimine sahip olur, ancak erişim dereceleri değişen birçok farklı yönetici hesabı vardır. Her [tür yönetici rolüne](/office365/admin/add-users/about-admin-roles) ilişkin farklı erişim düzeyleri hakkında bilgi için bkz. yönetici rolleri.

## <a name="create-additional-admin-accounts"></a>Ek yönetici hesapları oluşturma

Yönetici hesaplarını yalnızca yönetim için kullanın. Yöneticilerin, Office uygulamalarının düzenli kullanımı için ayrı bir kullanıcı hesabı olması ve yalnızca hesapları ve cihazları yönetmek için gerekli olduğu zaman ve diğer yönetici işlevleri üzerinde çalışırken yönetim hesaplarını kullanmaları gerekir. Ayrıca bu lisansları ödemeniz gerek Microsoft 365 yönetici hesaplarından kaldırmak da iyi bir fikirdir.

Başka bir güvenilir çalışana yönetici erişimi vermek için en az bir Genel yönetici hesabı daha ayarlamak gerekir. Ayrıca, kullanıcı yönetimi için ayrı yönetici hesapları da oluşturabilirsiniz (bu rol, Kullanıcı yönetimi **yöneticisi olarak adlandırılan).** Daha fazla bilgi için bkz [. yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).

Ek yönetici hesapları oluşturmak için:

 1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">gidin ve sol</a> gezintide **Kullanıcılar** \> **Etkin Kullanıcılar'ı** seçin.

    ![Sol gezintide Kullanıcılar'ı ve ardından Etkin kullanıcılar'ı seçin.](../media/Activeusers.png)

 2. Etkin **kullanıcılar sayfasında** , sayfanın **en üstünde Kullanıcı** ekle'yi seçin ve Yeni **kullanıcı panelinde adı** ve diğer bilgileri girin.
 3. Roller bölümünü **genişletin** ve bu kullanıcıya **genel yönetici erişimi** vermek için Genel yönetici'yi seçin. Ayrıca Özelleştirilmiş **yönetici'yi seçebilir** ve görüntülenen rollerden herhangi birini seçebilirsiniz.

    Alternatif e-posta adresi metin **kutusuna alternatif bir e-posta** girin. Kilitli olursanız parola bilgilerini kurtarmak için bu adresi kullanabilirsiniz. Genel yöneticiler için bu adrese bir fatura bildirimi de gönderilir.

    ![Yönetici rolünü seçin.](../media/adminroles.png)

 4. Ürün **lisansları bölümünde**, Microsoft 365 İş için seçiciyi **Kapalı'ya** ve Ürün lisansı **olmayan kullanıcı oluştur seçeneğini De**' **tıklatın**.

    ![Ürün lisansını seçin.](../media/productlicense.png)

## <a name="create-an-emergency-admin-account"></a>Acil durum yönetici hesabı oluşturma

Çok faktörlü kimlik doğrulaması (MFA) ile ayarlanmayacak bir yedek hesabı da oluşturmanız gerekir; böylece kendinizi yanlışlıkla kilitlemezsiniz (örneğin, ikinci doğrulama biçimi olarak kullanmakta olduğu telefonunuzu kaybedersiniz). Bu hesabın parolasının bir tümcecik veya en az 16 karakter uzunluğunda olduğundan emin olun. Bu çoğunlukla "break-glass hesabı" olarak adlandırılır.

## <a name="create-a-user-account-for-yourself"></a>Kendiniz için bir kullanıcı hesabı oluşturun

Postayı kontrol etmek de dahil olmak üzere, organizasyonla işbirliğine katılmak için kullanıcı hesabını kullanın. Bu, yönetici kimlik bilgilerinizin  *Hervez.Chavez <span></span>@Contoso.org'a* benzey olduğu ve normal kullanıcı hesabınız *Dayı <span></span>@Ali'ye benzer Contoso.com*.

Yeni kullanıcı hesabı oluşturmak için:

1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">gidin ve sol</a> gezintide **Kullanıcılar** \> **Etkin Kullanıcılar'ı** seçin.
2. Etkin **kullanıcılar sayfasında** , sayfanın **en üstünde Kullanıcı** ekle'yi seçin ve Yeni **kullanıcı panelinde adı** ve diğer bilgileri girin.
3. Roller bölümünü **genişletin** ve Kullanıcı (yönetim **erişimi yok) 'ı seçin**.
4. Ürün **lisansları bölümünde**, İş için seçiciyi **Microsoft 365'a** **taşıma**.

## <a name="turn-on-security-defaults"></a>Güvenlik varsayılanlarını açma

Güvenlik varsayılanları, Microsoft'un sizin organizasyonunız adına yönetmesi için önceden yapılandırılmış güvenlik ayarları sağlayarak kimliğinizin korunmasına yardımcı olur. Bu ayarlar arasında, tüm yöneticiler ve kullanıcı hesapları için Multi-Factor Authentication'ın (MFA) etkinleştirilmesi yer almaktadır. Güvenlik varsayılanları hakkında daha fazla bilgi edinmek ve bunları etkinleştirmeyi öğrenmek için bkz [. Güvenlik varsayılanlarını açma](m365-campaigns-conditional-access.md).

## <a name="additional-recommendations"></a>Ek öneriler

- Yönetici hesaplarını kullanmadan önce, kişisel e-posta hesapları da dahil olmak üzere tüm ilgili olmayan tarayıcı oturumlarını ve uygulamalarını kapatın. Özel veya gizli tarayıcı pencerelerini de kullanabilirsiniz.
- Yönetici görevlerini tamamladıktan sonra, tarayıcı oturumunu oturumundan çıkmayı sağlar.
