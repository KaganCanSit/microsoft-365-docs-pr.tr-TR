---
title: Hesabınızı kapatma
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: Hesabınızı Microsoft ile kapattığınızda lisanslar, kullanıcılar ve kullanıcı verileri dahil olmak üzere hesabınızla ilgili tüm bilgiler silinir.
ms.date: 04/02/2021
ms.openlocfilehash: c036a4cda929d58265a088b15a43772caacb0b94
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102470"
---
# <a name="close-your-account"></a>Hesabınızı kapatma

Microsoft’la hesabınızı kapattığınızda hesabınızla ilişkili tüm bilgiler silinir. Bu bilgiler aboneliklerden, lisanslardan, ödeme yöntemlerinden, kullanıcılardan ve kullanıcı verilerinden oluşur.

## <a name="before-you-begin"></a>Başlamadan önce

Bu işlemi başlatmadan önce korumak istediğiniz tüm verileri yedeklediğinizden emin olun.

Bu makaledeki görevleri yerine getirmek için Genel yönetici veya Fatura yöneticisi olmalısınız. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>1. Adım: Kullanıcıları silme

Tek bir genel yönetici dışındaki tüm kullanıcıları silin. Genel yönetici hesabı kapatma adımlarını tamamlar. Bu işlemin sonunda dizini silebilmeniz için önce diğer tüm kullanıcıları silmeniz gerekir.

Kullanıcılar şirket içinden eşitlenirse, önce eşitlemeyi kapatın, ardından Azure portal veya Azure PowerShell cmdlet'lerini kullanarak bulut dizinindeki kullanıcıları silin.

Kullanıcıları silmek için bkz [. Kullanıcı yönetimi yöneticisi: Bir veya daha fazla kullanıcıyı silme](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Kullanıcıları toplu olarak silmek için [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet'ini de kullanabilirsiniz.

Kuruluşunuz Microsoft Azure Active Directory (Azure AD) ile eşitlenen Active Directory kullanıyorsa, bunun yerine kullanıcı hesabını Active Directory'den silin. Yönergeler için bkz. [Azure Active Directory'da kullanıcıları toplu silme](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>2. Adım: Tüm etkin abonelikleri iptal etme

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.
2. **Ürünler** sekmesinde etkin bir abonelik bulun. Üç noktayı (diğer eylemler) ve ardından **Aboneliği iptal et**'i seçin.
3. **Aboneliği iptal et** bölmesinde iptal etme nedeninizi seçin. İsterseniz geri bildirim sağlayabilirsiniz.
4. **Kaydet**'i seçin.
5. Tüm etkin abonelikleri iptal etmek için 1 ile 4 arasındaki adımları yineleyin.

## <a name="step-3-delete-all-disabled-subscriptions"></a>3. Adım: Devre dışı bırakılan tüm abonelikleri silme

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.
2. **Ürünler** sekmesinde devre dışı bırakılmış bir abonelik seçin.
3. Abonelik ayrıntıları sayfasındaki **Abonelik ve ödeme ayarları** bölümünde **Aboneliği sil'i** seçin.
4. **Aboneliği sil** bölmesinde **Aboneliği sil'i** seçin.
5. **Aboneliği sil** iletişim kutusunda **Evet'i** seçin.
6. Devre dışı bırakılan her abonelik için, tüm abonelikler silinene kadar 3 ile 5 arasındaki adımları yineleyin.

> [!NOTE]
> Devre dışı bırakılmış bir aboneliği hemen silemiyorsanız [desteğe başvurun](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>4. Adım: Çok faktörlü kimlik doğrulamasını devre dışı bırakma

1. Yönetim merkezinde bir Genel yönetici hesabıyla oturum açın. Sahip olduğunuz rolleri doğrulamak için bkz. [Kuruluşunuzdaki yönetici rollerini denetleme](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. **Etkin Kullanıcılar** >  sayfasına gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
3. **Çok faktörlü kimlik doğrulamasını** seçin.
4. Çok faktörlü kimlik doğrulaması sayfasında, kullanmakta olduğunuz genel yönetici hesabı dışındaki tüm hesapları devre dışı bırakın.

[PowerShell'i birden çok kullanıcı için çok faktörlü kimlik doğrulamasını devre dışı bırakmak için de kullanabilirsiniz](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>5. Adım: Azure Active Directory dizinini silme

1. Genel yönetici hesabıyla <a href="https://aad.portal.azure.com/" target="_blank">Azure AD yönetim merkezinde</a> oturum açın.
2. **Azure Active Directory**’yi seçin.
3. Silmek istediğiniz kuruluşa geçin.
4. **Kiracıyı sil'i** seçin.
5. Kuruluşunuz bir veya daha fazla denetimde başarısız olursa, denetimleri geçirme hakkında daha fazla bilgi için bir bağlantı görürsünüz. Tüm denetimleri geçtikten sonra işlemi tamamlamak için **Sil'i** seçin.

Bu son adımı tamamladıktan sonra Microsoft hesabınız kapatılır ve silinir.

## <a name="related-content"></a>İlgili içerik 

[İş için Microsoft 365 faturanızı veya faturanızı anlama](./billing-and-payments/understand-your-invoice2.md) (makale)\
[Aboneliğinizi iptal etme](./subscriptions/cancel-your-subscription.md) (makale)

