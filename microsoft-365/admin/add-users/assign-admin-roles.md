---
title: Yönetici rollerini atama Microsoft 365 yönetim merkezi
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
ms.custom:
- MSStore_Link
- okr_smb
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: eac4d046-1afd-4f1a-85fc-8219c79e1504
description: Yönetici merkezinde belirli görevleri gerçekleştirecek bir kullanıcıya veya işletmedeki birden çok kullanıcıya yönetici rolleri atamayı öğrenin.
ms.openlocfilehash: fd38bb9ed378e6b3ffc20a79ca71eb2943599dcc
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996106"
---
# <a name="assign-admin-roles"></a>Yönetici rollerini atama

Microsoft iş aboneliğinizi satın alan kişi sizseniz, genel yöneticisiniz. Bu, abonelikleriniz içinde ürünler üzerinde sınırsız denetime sahip olduğunu ve çoğu veriye erişebilirsiniz.

Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](about-admin-roles.md).

Yeni kullanıcıları eklerken, bu kullanıcılara yönetici rolü atamazsanız bu kullanıcılar kullanıcı rolünde olur ve Microsoft  yönetim merkezlerinden herhangi biri için yönetici ayrıcalıklarına sahip değildir. Ancak, işleri yapmak için yardıma gerek varsa, kullanıcıya bir yönetici rolü attaysanız. Örneğin, parolaları sıfırlamaya yardımcı olması için birine ihtiyacınız varsa, bu kullanıcıya genel yönetici rolü atamanız gerekmektedir, bu kullanıcıya parola yöneticisi rolü atamanız gerekir. Verilerinize ve çevrimiçi işletmenize sınırsız erişimi olan çok fazla genel yönetici olması bir güvenlik riski sağlar.

## <a name="watch-add-an-admin"></a>İzle: Yönetici ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Microsoft 365 Business'a kaydolarak otomatik olarak genel yönetici oluruz. İşletmenin yönetimine yardımcı olmak için diğer kişiler de yönetici olabilir. 
1. Etkin Microsoft 365 yönetim merkezi **Kullanıcılar'ı** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**seçin**</a>.
1. Yönetici yapmak istediğiniz kullanıcıyı seçin ve sonra da Rolleri **Yönet'i seçin**.

Bu videoyu faydalı bulduysanız, [küçük işletmelere ve Microsoft 365’i ilk kez kullananlara yönelik eğitim serisinin tamamına göz atın](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Yönetici rollerini atama 

Kullanıcıları 2 farklı şekilde bir role atabilirsiniz:

- Kullanıcıya rol atamak için kullanıcının ayrıntılarına **ve** Rolleri yönet'e gidebilirsiniz.
- Ya da **Roller'e gidip** rolü seçin ve sonra birden çok kullanıcı ekleyin.

### <a name="assign-admin-roles-to-users-using-roles"></a>Roller'i kullanan kullanıcılara yönetici rolleri atama

1. Yönetim merkezinde Rol <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**atamaları'ne gidin**</a>. Organizasyon için **kullanılabilir yönetici** **rollerini görüntülemek için Azure AD veya Intune** sekmelerini seçin.
2. Kullanıcıya atamak istediğiniz yönetici rolünü seçin.
3. Atanan **yöneticilerAdresi'ni** >  **seçin**.
4. Kullanıcının görünen adını veya **kullanıcı** adını **yazın** ve ardından öneri listesinden bir kullanıcı seçin.
5. Bitirene kadar birden çok kullanıcı ekleyin.
6. **Kaydet'i** seçin; ardından kullanıcı atanan yöneticiler listesine eklenir.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Etkin kullanıcılardan bir kullanıcıya yönetici rolü atama

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Kullanıcılar Etkin kullanıcılar **sayfasına** > gidin.[](https://go.microsoft.com/fwlink/p/?linkid=834822)

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Etkin **kullanıcılar sayfasında** , yönetici rolünü değiştirmek istediğiniz kullanıcıyı seçin. Uç uç bölmesindeki Roller'in **altında** Rolleri **Yönet'i seçin**.

3. Kullanıcıya atamak istediğiniz yönetici rolünü seçin. İstediğiniz rolü görmüyorsanız, listenin **en altındaki Tüm** göster'i seçin.

## <a name="assign-admin-roles-to-multiple-users"></a>Birden çok kullanıcıya yönetici rolü atama

PowerShell'i biliyorsanız bkz. [PowerShell ile kullanıcı hesaplarına rol atama](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). Bu, yüzlerce kullanıcıya rol atamak için idealdir.
  
On veya daha fazla kullanıcıya rol atamak için aşağıdaki yönergeleri kullanın.

## <a name="check-admin-roles-in-your-organization"></a>Kuruluşta yönetici rollerini denetleme

Diğer kullanıcılara yönetici rolleri atamak için doğru izinlere sahip olamayabilirsiniz. Doğru izinlere sahip olup olmadığını kontrol edin veya başka bir yöneticiden rolleri sizin için atamasını sorun.

Yönetici rolü izinlerini 2 farklı şekilde kontrol edin:

- Kullanıcının ayrıntılarına gidip Hesap sayfasında **Roller'in altına** **bakabilirsiniz** .
- Ayrıca, **Roller'e gidip** yönetici rolünü ve atanmış yöneticileri seçerek hangi kullanıcıların atandığı hakkında bilgi edinebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Yönetici Microsoft 365 hakkında](about-admin-roles.md) (makale)\
[Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference) (makale)\
[PowerShell ile kullanıcı hesaplarına rol atama](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (makale)\
[İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md) (makale)