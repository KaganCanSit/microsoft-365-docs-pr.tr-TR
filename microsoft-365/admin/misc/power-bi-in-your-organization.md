---
title: Kuruluşunuzda Power BI
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- PWB150
ms.assetid: d7941332-8aec-4e5e-87e8-92073ce73dc5
ROBOTS: NOINDEX
description: Power BI ve kuruluşunuzdaki kullanıcıların bu iş analizi hizmetini nasıl kullanabileceği hakkında bilgi edinin.
ms.openlocfilehash: b4e1fd299caa4045a68770adc3a2d53dd4b11ec0
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469546"
---
# <a name="using-power-bi-data-in-your-organization"></a>Kuruluşunuzda Power BI verileri kullanma

Bu sayfada, kuruluşunuzdaki kullanıcıların Power BI'yi nasıl kullanabileceği ve kuruluşunuzun bu hizmeti alış yöntemini nasıl denetleyebileceğiniz açıklanır.

## <a name="what-is-power-bi"></a>Power BI nedir?

Microsoft Power BI, kullanıcıların yeni ve kolay yollarla verileri görselleştirmesine, keşifleri paylaştırmasına ve işbirliği yapmasına olanak tanır. Daha fazla bilgi edinmek için [Power BI Web sitesine](https://powerbi.microsoft.com/en-us/) bakın.
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI ulusal, bölgesel ve sektöre özgü uyumluluk gereksinimlerini karşılıyor mu?

Power BI uyumluluğu hakkında daha fazla bilgi edinmek için bkz. [Microsoft Güven Merkezi](https://go.microsoft.com/fwlink/?LinkId=785324).
  
## <a name="how-do-users-sign-up-for-power-bi"></a>Kullanıcılar Power BI'ye nasıl kaydolur?

Yönetici olarak, [Power BI web sitesi](https://powerbi.microsoft.com/en-us/) aracılığıyla Power BI'ye kaydolabilirsiniz. Ayrıca Microsoft 365 yönetim merkezi satın alma hizmetleri sayfasından da kaydolabilirsiniz. Yönetici Power BI'ye kaydolduğunda, erişime sahip olması gereken kullanıcılara abonelik lisansları atayabilir.
  
Buna ek olarak, kuruluşunuzdaki tek tek kullanıcıların [Power BI web sitesi](https://powerbi.microsoft.com/en-us/) aracılığıyla Power BI'ye kaydolması da mümkün olabilir. Kuruluşunuzdaki bir kullanıcı Power BI'ye kaydolduğunda, o kullanıcıya otomatik olara Power BI lisansı atanır.
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>Kuruluşumdaki tek tek kullanıcılar nasıl kaydolur?

Kuruluşunuzdaki kullanıcılara uygulanabilecek üç senaryo vardır:
  
### <a name="scenario-1-your-organization-already-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-already-has-a-microsoft-365-account"></a>Senaryo 1: Kuruluşunuzun zaten bir Microsoft 365 ortamı var ve Power BI kaydolan kullanıcının zaten bir Microsoft 365 hesabı var.

Bu senaryoda, kullanıcının kiracıda (örneğin, contoso.com) iş veya okul hesabı varsa ancak henüz Power BI'si yoksa, Microsoft o hesap için planı etkinleştirir ve kullanıcıya otomatik olarak Power BI hizmetini nasıl kullanacağı bildirilir.
  
### <a name="scenario-2-your-organization-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-a-microsoft-365-account"></a>Senaryo 2: Kuruluşunuzun mevcut bir Microsoft 365 ortamı vardır ve Power BI kaydolan kullanıcının Microsoft 365 hesabı yoktur.

Bu senaryoda, kullanıcının kuruluşunuzun etki alanında (örneğin, contoso.com) bir e-posta adresi vardır ancak henüz bir Microsoft 365 hesabı yoktur. Bu durumda, kullanıcı Power BI'ye kaydolabilir ve kendisine otomatik olarak bir hesap sağlanır. Bu da kullanıcının Power BI hizmeti erişmesine olanak tanır. Örneğin, Nancy adlı bir çalışan kaydolmak için iş e-posta adresini (örneğin, Nancy@contoso.com) kullanırsa, Microsoft Otomatik olarak Nancy'yi Contoso Microsoft 365 ortamına kullanıcı olarak ekler ve bu hesap için Power BI etkinleştirir.
  
### <a name="scenario-3-your-organization-does-not-have-a-microsoft-365-environment-connected-to-your-email-domain"></a>Senaryo 3: Kuruluşunuzun e-posta etki alanınıza bağlı bir Microsoft 365 ortamı yok.

Kuruluşunuzun Power BI yararlanması için gereken yönetim eylemi yoktur.
  
> [!IMPORTANT]
> Kuruluşunuzun birden çok e-posta etki alanı varsa ve tüm e-posta adresi uzantılarının aynı kiracıda olmasını tercih ediyorsanız, herhangi bir kullanıcı birincil kiracınızı oluşturmadan önce tüm e-posta adresi etki alanlarını bu kiracıya ekleyin. Kullanıcıları oluşturulduktan sonra kiracılar arasında taşımaya yönelik otomatik bir mekanizma yoktur. Bu işlem hakkında daha fazla bilgi için, bu [makalenin devamında birden çok etki alanım varsa, kullanıcıların eklendiği kiracıyı denetleyebilirim?](#if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to) bölümüne ve Çevrimiçi [Office 365 etki alanı ekleme](../setup/add-domain.md) bölümüne bakın.
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Bu işlem, bugün kuruluşumda kullanıcıların kimliklerini yönetmek için kullandığım yöntemi nasıl değiştirecek?

Kuruluşunuzun zaten bir Microsoft 365 ortamı varsa ve kuruluşunuzdaki tüm kullanıcıların Microsoft 365 hesapları varsa kimlik yönetimi değişmez.
  
Kuruluşunuzun zaten bir Microsoft 365 ortamı varsa ancak kuruluşunuzdaki tüm kullanıcıların Microsoft 365 hesabı yoksa, kiracıda bir kullanıcı oluşturur ve kullanıcının iş veya okul e-posta adresine göre lisans atarız. Bunun anlamı, kuruluşunuzdaki kullanıcılar hizmete kaydoldukça, belirli bir anda yönettiğiniz kullanıcıların sayısının artacağıdır.
  
Dizininizi şirket içinde yönetiyor ve Active Directory Federasyon Hizmetleri (AD_FS) kullanıyorsanız, Microsoft kiracınıza kullanıcı eklemez ve kiracınıza katılmaya çalışan kullanıcılara, kuruluşunuzun yöneticisine başvurmasını bildiren bir ileti gönderilir.
  
Kuruluşunuzun e-posta etki alanınıza bağlı bir Microsoft 365 ortamı yoksa, kimliği yönetme yönteminizde bir değişiklik olmaz. Kullanıcılar yeni, yalnızca bulutta bulunan bir kullanıcı dizinine eklenir ve kiracı yöneticisi olarak işi devralmayı ve bunların yönetimini üstlenmeyi seçmeniz için size bir seçenek sağlanır.
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Kullanıcılarım için Microsoft tarafından oluşturulan bir kiracıyı yönetme süreci nasıl çalışır?

Kiracı Microsoft tarafından oluşturulduysa, aşağıdaki adımları izleyerek söz konucu kiracı üzerinde hak iddia edebilir ve yönetimini üstlenebilirsiniz:
  
1. Yönetmek istediğiniz kiracının etki alanıyla eşleşen bir e-posta adresi etki alanı kullanıp [Power BI'ye kaydolarak](https://go.microsoft.com/fwlink/?LinkId=522448) kiracıya katılın. Örneğin, Microsoft contoso.com kiracısını oluşturduysa, @contoso.com ile biten bir e-posta adresiyle kiracıya katılmanız gerekir.

1. Etki alanının sahibi olduğunuzu doğrulayarak yönetici denetimi isteyin. Kiracıya katıldıktan sonra, etki alanının sahibi olduğunuzu doğrulayarak kendinizi yönetici rolüne yükseltebilirsiniz. Bunu yapmak için aşağıdaki adımları izleyin:

::: moniker range="o365-worldwide"

3. <a href="https://admin.microsoft.com" target="_blank">https://admin.microsoft.com</a> adresine gidin.

::: moniker-end

::: moniker range="o365-21vianet"

3. <a href="https://portal.partner.microsoftonline.cn" target="_blank">https://portal.partner.microsoftonline.cn</a> adımına gidin.

::: moniker-end

4. Sol üst köşedeki uygulama başlatıcı simgesini seçin ve ardından **Yönetici**’yi seçin.

    ![Yönetici uygulamasının vurgulandığı uygulama başlatıcı.](../../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. **Yönetici olun** sayfasındaki yönergeleri okuyun ve ardından **Evet, yönetici olmak istiyorum'ı** seçin.

    > [!NOTE]
    >  Bu seçenek görünmüyorsa, zaten bir yönetici vardır.
  
## <a name="if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to"></a>Birden çok etki alanım varsa, kullanıcıların eklendiği kiracıyı denetleyebilir miyim?

Hiçbir şey yapmazsanız, her kullanıcı e-posta etki alanı ve alt etki alanı için bir kiracı oluşturulur.
  
Tüm kullanıcıların, e-posta adresi uzantılarına bakılmaksızın aynı kiracıda yer almasını isterseniz:
  
- Önceden bir hedef kiracı oluşturun veya var olan bir kiracıyı kullanın ve söz konusu kiracıda birleştirmek istediğiniz tüm etki alanlarını ve alt etki alanlarını ekleyin. Bundan sonra, e-posta adresleri söz konusu etki alanları veya alt etki alanlarıyla biten her kullanıcı kaydolduğunda otomatik olarak hedef kiracıya katılır.

> [!IMPORTANT]
> Kullanıcıları oluşturulduktan sonra kiracılar arasında taşımak için desteklenen otomatik bir mekanizma yoktur. Tek bir Microsoft 365 kiracıya etki alanı ekleme hakkında bilgi edinmek için bkz. [Office 365 etki alanı ekleme](../setup/add-domain.md).

> [!IMPORTANT]
> Kiracıları yönetme hakkında daha fazla bilgi ve kılavuz için bkz. [Power BI yönetimi nedir?](/power-bi/service-admin-administering-power-bi-in-your-organization).
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-tenant"></a>Kullanıcıların mevcut kiracıma katılmasını nasıl engelleyebilirim?

Kullanıcıların mevcut kiracınıza katılmasını önlemek için yönetici olarak uygulayabileceğiniz adımlar vardır. Kullanıcıların kiracıya katılmasını engellerseniz, kullanıcıların oturum açma girişimleri başarısız olur ve kuruluşlarının yöneticisine başvurmaya yönlendirilirler. Otomatik lisans dağıtımını daha önce devre dışı bırakmışsanız (örneğin, Öğrenciler, Öğretim Üyeleri ve Personel için Office 365 Eğitim) bu işlemi tekrarlamanız gerekmez.
  
Bu adımlar, Windows PowerShell'in kullanılmasını gerektirir. Windows PowerShell kullanmaya başlamak için bkz. [PowerShell başlangıç kılavuzu](/powershell/scripting/overview).
  
Aşağıdaki adımları gerçekleştirmek için Azure Active Directory [V2 PowerShell Modülünün](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5) en son 64 bit sürümünü yüklemeniz gerekir.
  
Bağlantıyı seçtikten sonra **çalıştır'ı** seçerek yükleyici paketini çalıştırın.
  
**Kiracıya otomatik katılımı devre dışı bırakmak için**: Yeni kullanıcıların yönetilen bir kiracıya katılmasını engellemek için bu Windows PowerShell komutunu kullanın:
  
Yeni kullanıcıların kiracıya otomatik katılımını devre dışı bırakmak için:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
Yeni kullanıcıların kiracıya otomatik katılımını etkinleştirmek için:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> Bu engelleme, kuruluşunuzdaki yeni kullanıcıların Power BI kaydolmasını engeller. Kuruluşunuz için yeni kaydolmaları devre dışı bırakmadan önce Power BI kaydolan kullanıcılar lisanslarını korumaya devam eder. Daha önce hizmete kaydolmuş olan kullanıcıların Power BI erişimini nasıl kaldırabileceğinize ilişkin yönergeler için bkz. Önceden [kaydolmuş kullanıcılar](#how-do-i-remove-power-bi-for-users-that-already-signed-up) için Power BI kaldırma Nasıl yaparım??
  
## <a name="how-can-i-allow-users-to-join-my-existing-tenant"></a>Kullanıcıların mevcut kiracıma katılmasına nasıl izin veebilirim?

Kullanıcıların kiracınıza katılmasına izin vermek için, yukarıdaki soruda açıklandığı gibi karşıt komutu çalıştırın:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Kiracıya engelleme koyduğumu nasıl doğrulayabilirim?

Aşağıdaki PowerShell betiğini kullanın:  `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Var olan kullanıcılarımın Power BI'yi kullanmaya başlamasını nasıl engelleyebilirim?

**Otomatik lisans dağıtımını devre dışı bırakma:** Var olan kullanıcılara otomatik lisans dağıtımını devre dışı bırakmak için bu Windows PowerShell betiğini kullanın. Otomatik lisans dağıtımını daha önce devre dışı bırakmışsanız (örneğin, Öğrenciler, Öğretim Üyeleri ve Personel için Office 365 Eğitim) bu işlemi tekrarlamanız gerekmez.
  
Var olan kullanıcılara otomatik lisans dağıtımını devre dışı bırakmak için:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
Var olan kullanıcılara otomatik lisans dağıtımını etkinleştirmek için:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> *AllowAdHocSubscriptions* bayrağı, kuruluşunuzdaki kullanıcıların Azure Rights Management Hizmeti'ne kaydolma olanağı da dahil olmak üzere çeşitli kullanıcı özelliklerini denetlemek için kullanılır. Bu bayrağın değiştirilmesi, bu becerilerin tümünü etkiler.
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Var olan kullanıcılarımın Power BI'ye kaydolmasına nasıl izin verebilirim?

Var olan kullanıcılarınızın Power BI'ye kaydolmasına izin vermek için, yukarıdaki soruda açıklandığı gibi karşıt komutu çalıştırın:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Önceden kaydolmuş olan kullanıcılar için Power BI'yi nasıl kaldırabilirim?

Bir kullanıcı Power BI kaydolmuşsa ancak artık Power BI erişimi olmasını istemiyorsanız, o kullanıcının Power BI lisansını kaldırabilirsiniz.
  
::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisansını kaldırmak istediğiniz kullanıcıyı bulun ve adını seçin.

3. **Lisanslar ve Uygulamalar** sekmesinde **Microsoft Power BI** onay kutusunu temizleyin.

4. **Değişiklikleri kaydet'i** seçin.

## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Kiracıma yeni kullanıcıların katıldığını nasıl anlarım?

Bu program kapsamında kiracınıza katılan kullanıcılara benzersiz bir lisans atanır ve yönetim panonuzdaki etkin kullanıcı bölmesinde bu lisans için filtre uygulayabilirsiniz.
  
Bu yeni görünümü oluşturmak için yönetim merkezinde [Özel kullanıcı görünümü oluşturma'daki](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view) adımları izleyin. **Atanan ürün lisansı'nın** altında **Microsoft Power BI'ı** seçin. Yeni görünüm oluşturulduktan sonra, kiracınızda bu programa kaydolan tüm kullanıcıları görebilirsiniz.
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Hazırlıklı olmam gereken başka şeyler var mı?

Parola sıfırlama isteklerinde bir artışla karşılaşabilirsiniz. Bu işlem hakkında bilgi için bkz. [Kullanıcı parolasını sıfırlama](../add-users/reset-passwords.md).
  
Yönetici merkezindeki standart işlem aracılığıyla kiracınızdan bir kullanıcıyı kaldırabilirsiniz. Bununla birlikte, kullanıcının hala kuruluşunuzdan alınmış etkin bir e-posta adresi varsa, tüm kullanıcıların katılımını engellemediğiniz sürece, kiracınıza yeniden katılabilir.
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-tenant"></a>Microsoft Power BI için 1 milyon lisans neden kiracımda göstersin?

Buna hak kazanmış bir kuruluş olarak, kuruluşunuzdaki kullanıcılar Microsoft Power BI hizmetini kullanmaya uygundur ve bu lisanslar kiracınızda yeni Power BI kullanıcılarına yönelik olarak sağlanan kapasiteyi gösterir. Bu lisanslar için ücret alınmaz. Kullanıcıların kendileri Power BI kaydolmasına izin vermeyi seçtiyseniz, kaydolma işlemini tamamlayan kullanıcılara bu ücretsiz lisanslardan biri atanır. Ayrıca bu lisansları yönetim merkezi aracılığıyla kullanıcılara kendiniz atamayı da seçebilirsiniz.
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Bu ücretsiz mi? Bu lisanslar için ücret ödeyecek miyim?

Bu lisanslar Power BI'nin ücretsiz sürümü içindir. Ek özellikler ilginizi çekiyorsa, Power BI Pro sürümünü gözden geçirin.
  
## <a name="why-1-million-licenses"></a>Neden 1 milyon lisans?

Kuruluşların çoğunun kullanıcılarına gecikmeden bu avantajı sağlamak için yeterli lisansa sahip olacak kadar büyük bir sayı seçtik.
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>1 milyondan fazla lisans gerekirse ne yapabilirim?

Ek lisans almanız gerekirse, daha fazla bilgi için Microsoft hesap temsilcinize başvurun.