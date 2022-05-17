---
title: Yönetici rollerini Microsoft 365 yönetim merkezi atama
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
description: Yönetici merkezinde belirli görevleri gerçekleştirebilmeleri için işletmenizdeki bir kullanıcıya veya birden çok kullanıcıya yönetici rolleri atamayı öğrenin.
ms.openlocfilehash: 663a5fb60fa815eab079f4ab96e53e8b168105b7
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437030"
---
# <a name="assign-admin-roles-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi yönetici rolleri atama

Microsoft iş aboneliğinizi satın alan kişi sizseniz genel yönetici olursunuz. Bu, aboneliklerinizdeki ürünler üzerinde sınırsız denetime sahip olduğunuz ve çoğu veriye erişebileceğiniz anlamına gelir.

Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](about-admin-roles.md).

Yeni kullanıcılar eklediğinizde, onlara bir yönetici rolü atamazsanız, bu *kullanıcılar kullanıcı rolündedir* ve Microsoft yönetim merkezlerinin hiçbirinde yönetici ayrıcalıklarına sahip değildir. Ancak işleri halletmek için yardıma ihtiyacınız varsa kullanıcıya yönetici rolü atayabilirsiniz. Örneğin, parolaları sıfırlamaya yardımcı olması için birine ihtiyacınız varsa, bu kişiye genel yönetici rolünü atamamanız, parola yöneticisi rolünü atamanız gerekir. Verilerinize ve çevrimiçi işletmenize sınırsız erişimi olan çok fazla genel yöneticiye sahip olmak bir güvenlik riskidir.

## <a name="watch-add-an-admin"></a>İzleyin: Yönetici ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Microsoft 365 business'a kaydolduğunda otomatik olarak genel yönetici olursunuz. İşletmeyi yönetmeye yardımcı olmak için diğer kişileri de yönetici yapabilirsiniz. 
1. Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**KullanıcılarEtkin**</a> >  kullanıcılar'ı seçin.
1. Yönetici yapmak istediğiniz kullanıcıyı seçin ve ardından **Rolleri yönet'i** seçin.

Bu videoyu faydalı bulduysanız, [küçük işletmelere ve Microsoft 365’i ilk kez kullananlara yönelik eğitim serisinin tamamına göz atın](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Yönetici rollerini atama 

Kullanıcıları bir role 2 farklı yolla atayabilirsiniz:

- Kullanıcıya rol atamak için kullanıcının ayrıntılarına ve **Rolleri yönet'e** gidebilirsiniz.
- İsterseniz **Roller'e** gidip rolü seçip birden çok kullanıcı ekleyebilirsiniz.

### <a name="assign-admin-roles-to-users-using-roles"></a>Rolleri kullanarak kullanıcılara yönetici rolleri atama

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Rol atamaları'na**</a> gidin. Kuruluşunuzda kullanılabilen yönetici rollerini görüntülemek için **Azure AD** veya **Intune** sekmelerini seçin.
2. Kullanıcıyı atamak istediğiniz yönetici rolünü seçin.
3. **Atanan** **yöneticilerEkle'yi** >  seçin.
4. Kullanıcının **görünen adını** veya **kullanıcı adını** yazın ve ardından öneri listesinden kullanıcıyı seçin.
5. İşiniz bitene kadar birden çok kullanıcı ekleyin.
6. **Kaydet'i** seçtiğinizde kullanıcı atanan yöneticiler listesine eklenir.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Etkin kullanıcılardan yönetici rolüne kullanıcı atama

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Kullanıcılar** > [Etkin kullanıcılar](https://go.microsoft.com/fwlink/p/?linkid=834822) sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. **Etkin kullanıcılar** sayfasında, yönetici rolünü değiştirmek istediğiniz kullanıcıyı seçin. Açılır bölmedeki **Roller'in** altında **Rolleri yönet'i** seçin.

3. Kullanıcıya atamak istediğiniz yönetici rolünü seçin. Aradığınız rolü görmüyorsanız listenin en altındaki **Tümünü göster'i** seçin.

## <a name="assign-admin-roles-to-multiple-users"></a>Birden çok kullanıcıya yönetici rolü atama

PowerShell'i biliyorsanız bkz. [PowerShell ile kullanıcı hesaplarına rol atama](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). Yüzlerce kullanıcıya rol atamak için idealdir.
  
On veya daha fazla kullanıcıya rol atamak için aşağıdaki yönergeleri kullanın.

## <a name="check-admin-roles-in-your-organization"></a>Kuruluşunuzdaki yönetici rollerini denetleme

Diğer kullanıcılara yönetici rolleri atamak için doğru izinlere sahip olmayabilirsiniz. Doğru izinlere sahip olduğunuzdan emin olun veya başka bir yöneticiden size rol atamasını isteyin.

Yönetici rolü izinlerini 2 farklı şekilde de kontrol edebilirsiniz:

- Kullanıcının ayrıntılarına gidebilir ve **Hesap** sayfasında **Roller'in** altına bakabilirsiniz.
- Ya da **Roller'e** gidip yönetici rolünü seçebilir ve atanmış yöneticileri seçerek hangi kullanıcıların atandığı görebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 yönetici rolleri hakkında](about-admin-roles.md) (makale)\
[yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference) (makale)\
[PowerShell ile kullanıcı hesaplarına rol atama](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (makale)\
[İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md) (makale)