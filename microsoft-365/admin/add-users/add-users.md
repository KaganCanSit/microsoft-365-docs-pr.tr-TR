---
title: Microsoft 365'de kullanıcı ekleme ve lisans atama
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
description: Microsoft 365 lisanslara, oturum açma kimlik bilgilerine ve Microsoft 365 posta kutularına sahip olabilmeleri için her ekip üyesine bir kullanıcı hesabı vermeyi öğrenin.
ms.date: 07/01/2020
ms.openlocfilehash: 8ebc4b99840f9987d115539d0039efa1950499d3
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466822"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Aynı anda kullanıcı ekleme ve lisans atama

Ekibinizdeki kişilerin oturum açabilmesi ve [iş için Microsoft 365](https://www.microsoft.com/microsoft-365/business) erişebilmesi için önce bir kullanıcı hesabına ihtiyacı vardır. Kullanıcı hesaplarını eklemenin en kolay yolu, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">bunları Microsoft 365 yönetim merkezi</a> birer birer eklemektir. Bu adımı gerçekleştirdikten sonra, kullanıcılarınızın Microsoft 365 lisansları, oturum açma kimlik bilgileri ve Microsoft 365 posta kutuları vardır.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Kullanıcı eklemek ve lisans atamak için genel yönetici, lisans veya kullanıcı yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>İzleyin: Pano görünümüne kullanıcı ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Videoda kullanılan adımlar, kullanıcı eklemek için farklı bir başlangıç noktası gösterir, ancak kalan adımlar aşağıdaki yordamla aynıdır.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Pano görünümünde kullanıcıları birer birer ekleme

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Ekran görüntüsü: Yönetim merkezi pano görünümü":::

::: moniker range="o365-worldwide"

1. Şuradan yönetim merkezine gidin: <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. **KullanıcılarEtkin** >  **kullanıcılar'a** gidin ve **Kullanıcı ekle'yi** seçin.
3. **Temel bilgileri ayarla** bölmesinde, temel kullanıcı bilgilerini doldurun ve **İleri'yi** seçin.
    - **Adı** Ad ve soyadını, görünen adı ve kullanıcı adını girin.
    - **Etki alanı** Kullanıcı hesabının etki alanını seçin. Örneğin, kullanıcının kullanıcı adı Jakob ve etki alanı contoso.com ise jakob@contoso.com kullanarak oturum açar.
    - **Parola ayarları** Otomatik olarak oluşturulan parolayı kullanmayı veya kullanıcı için kendi güçlü parolanızı oluşturmayı seçin.
    - Kullanıcı 90 gün sonra parolasını değiştirmelidir. Alternatif olarak **, bu kullanıcının ilk oturum açma sırasında parolasını değiştirmesini gerektir'i** de seçebilirsiniz.
    - Kullanıcı eklendiğinde parolayı e-postayla göndermek isteyip istemediğinizi seçin.
4. **Ürün lisansları ata** bölmesinde, kullanıcı için konumu ve uygun lisansı seçin. Kullanılabilir lisansınız yoksa da kullanıcı ekleyebilir ve ek lisans satın alabilirsiniz. **Uygulamalar'ı** genişletin ve kullanıcının lisansı olan uygulamaları sınırlamak için uygulamaları seçin veya seçimini kaldırın. **İleri**'yi seçin.
5. bu kullanıcıyı yönetici yapmak için **İsteğe bağlı ayarlar** bölmesinde **Roller'i** genişletin. Kullanıcı hakkında ek bilgi eklemek için **Profil bilgileri'ni** genişletin.
6. **İleri'yi** seçin, yeni kullanıcınızın ayarlarını gözden geçirin, istediğiniz değişiklikleri yapın, ardından **Eklemeyi bitir'i** ve ardından **Kapat'ı** seçin.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Yönetici basitleştirilmiş görünümüne kullanıcı ekleme

Bu sayfayı yönetim merkezinde görüyorsanız, **basitleştirilmiş yönetici görünümündesiniz** demektir. Kullanıcı eklemek için aşağıdaki adımları izleyin.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Ekran görüntüsü: Basitleştirilmiş yönetim merkezi görünümü":::

::: moniker range="o365-worldwide"

1. Şuradan yönetim merkezine gidin: <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. **Başka bir kişi için hesap oluştur'u** seçin.
3. **Kullanıcı hesabı ekle** sayfasında, oturum açmak için kullanacakları ad ve soyadı, görünen ad ve kullanıcı adını girin.
4. **En fazla 5 e-posta adresi... metin kutusuna kullanıcının e-posta adresini** ekleyin. Bu, yeni kullanıcının Microsoft 365 hizmetlerinde oturum açmak için ihtiyaç duyduğu bilgileri almasını sağlar.
5. Bu bilgileri kaydetmek istiyorsanız **Kullanıcı ekle** **ve Oturum açma bilgilerini indir'i** seçin.

## <a name="add-multiple-users-at-the-same-time"></a>Aynı anda birden çok kullanıcı ekleme

Aynı anda birden çok kullanıcı eklemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:

- **Kişileri toplu olarak eklemek için bir elektronik tablo kullanın.** Bkz. [Aynı anda birkaç kullanıcı ekleme](../../enterprise/add-several-users-at-the-same-time.md).
- **Hesap eklemeyi ve lisans atamayı otomatikleştirin.** Bkz. [Microsoft 365 PowerShell ile kullanıcı hesapları oluşturma](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Windows PowerShell cmdlet'lerini kullanmayı zaten biliyorsanız bu yöntemi seçin.
- **ActiveDirectory mi kullanıyorsunuz?** [Microsoft 365 için dizin eşitlemesini ayarlayın](../../enterprise/set-up-directory-synchronization.md). Microsoft 365 Active Directory kullanıcı hesaplarını (ve diğer Active Directory nesnelerini) çoğaltmak için Azure AD Bağlan aracını kullanın. Eşitleme yalnızca kullanıcı hesaplarını ekler. E-posta ve diğer Office uygulamalarını kullanabilmeleri için eşitlenen kullanıcılara lisans atamanız gerekir.
- **Exchange'den mi geçiş yapıyorsun?** Bkz. [Birden çok e-posta hesabını Office 365 geçirmenin yolları](/Exchange/mailbox-migration/mailbox-migration). Tam geçiş, aşamalı veya karma bir Exchange yöntemi kullanarak birden çok posta kutusunu Microsoft 365 geçirdiğinizde, geçişin bir parçası olarak kullanıcıları otomatik olarak eklersiniz. Geçiş yalnızca kullanıcı hesaplarını ekler. E-posta ve diğer Office uygulamalarını kullanabilmeleri için önce kullanıcılara lisans atamanız gerekir. Kullanıcıya lisans atamazsanız, 30 günlük yetkisiz kullanım süresinden sonra posta kutusu devre dışı bırakılır. Microsoft 365 yönetim merkezi [kullanıcılara lisans atamayı](../manage/assign-licenses-to-users.md) öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı ekledikten sonra Microsoft'tan bir e-posta bildirimi alırsınız. E-posta, Microsoft 365 oturum açabilmesi için kişinin kullanıcı kimliğini ve parolasını içerir. Yeni parolaları bildirirken kullandığınız işlemi uygulayın. [PC veya Mac'e Office uygulamaları indirip yükleme ve](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) [mobil cihazda Office uygulamaları ve e-postayı ayarlama](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f) gibi ayarlamalar yapmak için [Çalışan hızlı başlangıç kılavuzunu](../setup/employee-quick-setup.md) yeni kullanıcılarınızla paylaşın.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 yeni çalışan ekleme](add-new-employee.md) (makale)\
[Microsoft 365 için aynı anda birkaç kullanıcı ekleme](../../enterprise/add-several-users-at-the-same-time.md) (makale)\
[Microsoft 365'da bir kullanıcıyı geri yükleme](restore-user.md) (makale)\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)\
[Kuruluşunuzdan kullanıcı silme](delete-a-user.md) (makale)
