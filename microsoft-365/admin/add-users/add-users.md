---
title: Kullanıcı ekleme ve lisans atama
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- MET150
description: Her ekip üyesinin oturum açması ve iş için postanıza erişmesi için bir Microsoft 365 olması gerekir. Kullanıcıları ekleme ve lisans atamayı öğrenin.
ms.date: 07/01/2020
ms.openlocfilehash: 90ef6506d10c0f4c106dd18816ccd2f11803a079
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011815"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Kullanıcıları ekleme ve lisansları aynı anda atama

İşletmeler için Oturum açma ve oturum açma bilgilerine erişmeden önce ekibi Microsoft 365 [gerekir](https://www.microsoft.com/microsoft-365/business). Kullanıcı hesaplarını eklemenin en kolay yolu, kullanıcı hesaplarını aynı anda ve tek <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">tek Microsoft 365 yönetim merkezi.</a> Bu adımı tamamlandıktan sonra, kullanıcılarınız Microsoft 365 lisansına, oturum açma kimlik bilgilerine ve posta Microsoft 365 sahip olur.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="before-you-begin"></a>Başlamadan önce

Kullanıcıları eklemek ve lisans atamak için genel yönetici, lisans veya kullanıcı yöneticisi olmak gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>İzle: Pano görünümünde kullanıcı ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Videoda kullanılan adımlar, kullanıcıları eklemek için farklı bir başlangıç noktası gösterir, ancak kalan adımlar aşağıdaki yordamla aynıdır.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Pano görünümünde kullanıcıları tek tek ekleme

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Ekran görüntüsü: Yönetim merkezi pano görünümü":::

::: moniker range="o365-worldwide"

1. yönetim merkezine gidin <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Kullanıcılar Etkin **kullanıcılar'a** >  **gidin** ve Kullanıcı **ekle'yi seçin**.
3. Temel **bilgileri ayarlayın bölmesinde, temel** kullanıcı bilgilerini doldurun ve Ardından Sonraki'yi **seçin**.
    - **Ad** Adı, soyadı, görünen adı ve kullanıcı adını doldurun.
    - **Etki alanı** Kullanıcının hesabı için etki alanını seçin. Örneğin, kullanıcının kullanıcı adı Jakob ve etki alanı contoso.com ise, kullanıcı e-posta jakob@contoso.com.
    - **Parola ayarları** Otomatik olarak yenilenmiş parolayı kullanmayı veya kullanıcı için kendi güçlü parolanızı oluşturmanızı sağlar.
    - Kullanıcının 90 gün sonra parolasını değiştirmesi gerekir. Bu kullanıcı ilk oturum **aya geldiğinde parolasını değiştirmesini gerektir'i de seçebilirsiniz**.
    - Kullanıcı ekli olduğunda parolayı e-postayla göndermek isteyip istemeyebilirsiniz.
4. Ürün **lisanslarını ata bölmesinde** , kullanıcı için konumu ve uygun lisansı seçin. Kullanılabilir lisansınız yoksa da kullanıcı ekleyebilir ve ek lisans satın alabilirsiniz. Kullanıcının **lisansına** sahip olduğu uygulamaları sınırlamak için Uygulamalar'ı genişletin ve uygulamaları seçin veya seçimleri kaldırın. **İleri**'yi seçin.
5. İsteğe **bağlı ayarlar bölmesinde** **Roller'i genişletarak** bu kullanıcıya yönetici yapın. Kullanıcı **hakkında ek** bilgi eklemek için Profil bilgileri'ne tıklayın.
6. **Sonraki'yi** seçin, yeni kullanıcı ayarlarınızı gözden geçirip istediğiniz değişiklikleri yapın, ardından Eklemeyi bitir'i ve **kapat'ı** **seçin**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Yönetici basitleştirilmiş görünümünde kullanıcı ekleme

Bu sayfayı yönetim merkezinde görüyorsanız, yöneticinin basitleştirilmiş **görünümündesinizdir**. Kullanıcı eklemek için aşağıdaki adımları izleyin.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Ekran görüntüsü: Basitleştirilmiş yönetim merkezi görünümü":::

::: moniker range="o365-worldwide"

1. yönetim merkezine gidin <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Başka **bir kişi için hesap oluştur'a seçin**.
3. Kullanıcı **hesabı ekle sayfasında** , oturum a doldurmak için kullanacakları ad ve soyadı, görünen ad ve kullanıcı adını doldurun.
4. En çok 5 e-posta adresi... metin kutusuna **kullanıcının e-posta** adresini ekleyin. Bu, yeni kullanıcının bu hizmetlerde oturum açması için gereken bilgileri edin Microsoft 365 sağlar.
5. Bu **bilgileri kaydetmek** için **Kullanıcı ekle ve Oturum** açma bilgilerini indir'i seçin.

## <a name="add-multiple-users-at-the-same-time"></a>Aynı anda birden çok kullanıcı ekleme

Aynı anda birden çok kullanıcı eklemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:

- **Kişi toplu olarak eklemek için bir elektronik tablo kullanın.** Bkz [. Aynı anda birkaç kullanıcı ekleme](../../enterprise/add-several-users-at-the-same-time.md).
- **Hesap eklemeyi ve lisans atamayı otomatikleştirin.** Bkz[. Microsoft 365 PowerShell ile kullanıcı hesapları oluşturma](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Windows PowerShell cmdlet'lerini kullanmayı biliyorsanız, bu yöntemi seçin.
- **ActiveDirectory mi kullanıyorsunuz?** [Etki alanı için dizin eşitlemesini Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Başka bir hesapta Active Directory Bağlan hesaplarını (ve diğer Active Directory nesnelerini) çoğaltmak için Azure AD Microsoft 365. Eşitleme yalnızca kullanıcı hesaplarını ekler. E-posta ve diğer e-posta uygulamalarını kullanamadan önce eşitlenen kullanıcılara lisans Office gerekir.
- **Başka bir iş Exchange?** Bkz[. Birden çok e-posta hesabını başka bir hesaba Office 365](/Exchange/mailbox-migration/mailbox-migration). Tam, aşamalı veya karma Microsoft 365 bir geçiş yöntemi kullanarak birden çok posta kutusunu Exchange geçirerek, kullanıcıları geçiş işlemi kapsamında otomatik olarak eklersiniz. Geçiş yalnızca kullanıcı hesaplarını ekler. E-posta ve diğer kullanıcı uygulamalarını kullanamadan önce kullanıcılara lisans Office gerekir. Bir kullanıcıya lisans ata atadığınız zaman, yetkisiz kullanım süresi 30 gün olacak şekilde devre dışı bırakılır. Lisans atama [hakkında bilgi](../manage/assign-licenses-to-users.md) Microsoft 365 yönetim merkezi.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı eklemenizden sonra, Microsoft'tan bir e-posta bildirimi alırsınız. E-posta, e-postada oturum açması için kişinin kullanıcı kimliğini ve Microsoft 365. Yeni parolaları bildirirken kullandığınız işlemi uygulayın. PC veya [](../setup/employee-quick-setup.md) [Mac bilgisayara Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) uygulamalarını indirme ve yükleme ve mobil cihazda Office uygulamaları ve e-postayı ayarlama gibi ayarlamaları yapmak için Çalışan hızlı başlangıç kılavuzunu [yeni kullanıcılarınız ile paylaşın](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>İlgili içerik

[yeni çalışan ekleme (Microsoft 365](add-new-employee.md))\
[Aynı anda birkaç kullanıcı ekleme (Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md))\
[Microsoft 365'de bir Microsoft 365](restore-user.md) geri yükleme (makale)\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)\
[Kuruluştan kullanıcı silme](delete-a-user.md) (makale)
