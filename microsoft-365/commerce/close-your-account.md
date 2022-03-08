---
title: Hesabı kapatma
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
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
description: Microsoft ile olan hesabı kapatsanız, hesabınızla ilgili tüm bilgiler lisanslar, kullanıcılar ve kullanıcı verileri dahil silinir.
ms.date: 04/02/2021
ms.openlocfilehash: b1ac828d047d2c2b9f39185a66ccc77976b8324b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317297"
---
# <a name="close-your-account"></a>Hesabı kapatma

Microsoft’la hesabınızı kapattığınızda hesabınızla ilişkili tüm bilgiler silinir. Bu bilgiler aboneliklerden, lisanslardan, ödeme yöntemlerinden, kullanıcılardan ve kullanıcı verilerinden oluşur.

## <a name="before-you-begin"></a>Başlamadan önce

Bu işlemi başlatmadan önce korumak istediğiniz tüm verileri yedeklediğinizden emin olun.

Bu makaledeki görevleri yerine etmek için Genel veya Faturalama yöneticisi siz olun. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>1. Adım: Kullanıcıları silme

Tek bir genel yönetici dışında tüm kullanıcıları silin. Genel yönetici hesabı kapatma adımlarını tamamlar. Bu işlem sonunda dizini silebilirsiniz, önce diğer tüm kullanıcıları silmeniz gerekir.

Kullanıcılar şirket içinde eşitlenmişse, önce eşitlemeyi kapatın, ardından Azure portalını veya Azure PowerShell cmdlet'lerini kullanarak bulut dizininde kullanıcıları silin.

Kullanıcıları silmek için bkz. [Kullanıcı yönetimi yöneticisi: Bir veya birden çok kullanıcı silme](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Kullanıcıları toplu olarak silmek için [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet'ini de kullanabilirsiniz.

If your organization uses Active Directory that synchronizes Microsoft Azure Active Directory with Microsoft Azure Active Directory, delete the user account from Active Directory, instead. Yönergeler için bkz. [Kullanıcıların toplu olarak Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>2. Adım: Tüm etkin abonelikleri iptal etme

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a>  >  products sayfasına gidin.
2. Ürünler **sekmesinde** etkin bir abonelik bulun. Üç noktayı (diğer eylemler) ve ardından Aboneliği iptal **et'i seçin**.
3. Aboneliği **iptal et** bölmesinde iptal etme nedenini seçin. İsteğe bağlı olarak, herhangi bir geri bildirim gönderin.
4. **Kaydet**'i seçin.
5. Tüm etkin abonelikleri iptal etmek için 1 ile 4 arasında olan adımları yinelayın.

## <a name="step-3-delete-all-disabled-subscriptions"></a>3. Adım: Tüm devre dışı bırakılmış abonelikleri silme

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a>  >  products sayfasına gidin.
2. Ürünler sekmesinde **devre** dışı bırakılmış bir aboneliği seçin.
3. Abonelik ayrıntıları sayfasında, Abonelik ve **ödeme ayarları bölümünde Aboneliği sil'i** **seçin**.
4. Aboneliği sil **bölmesinde Aboneliği** **sil'i seçin**.
5. Aboneliği sil **iletişim kutusunda** Evet'i **seçin**.
6. Devre dışı bırakılmış her abonelik için, 3 ile 5 arasında olan adımları tüm abonelikler silinene kadar yinelayın.

> [!NOTE]
> Devre dışı bırakılmış bir aboneliği hemen silemiyorsanız, [destekle iletişime geçin](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>4. Adım: Çok faktörlü kimlik doğrulamasını devre dışı bırakma

1. Yönetim merkezinde bir Genel yönetici hesabıyla oturum açın. Sahip olduğunuz rolleri doğrulamak için bkz [. Kuruluşta yönetici rollerini denetleme](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. **UsersActive** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">users sayfasına</a> gidin.
3. **Multi-factor authentication'ı seçin**.
4. Çok faktörlü kimlik doğrulama sayfasında, kullanmakta olduğunuz genel yönetici hesabı dışında tüm hesapları devre dışı bırakabilirsiniz.

Ayrıca, Birden çok [kullanıcı için çok faktörlü kimlik doğrulamasını devre dışı bırakmak üzere PowerShell'i de kullanabilirsiniz](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>5. Adım: Dizinde dizini Azure Active Directory

1. Bir Genel yönetici <a href="https://aad.portal.azure.com/" target="_blank">hesabıyla Azure AD</a> yönetim merkezinde oturum açın.
2. **Azure Active Directory**’yi seçin.
3. Silmek istediğiniz kuruluşa geçiş.
4. Kiracıyı **sil'i seçin**.
5. Bir veya daha fazla denetim başarısız olursa, denetimleri nasıl geçireceğiyle ilgili daha fazla bilgiye ulaşabilirsiniz. Tüm denetimleri tamamlandıktan sonra, işlemi **tamamlamak için Sil'i** seçin.

Bu son adımı tamamlandıktan sonra Microsoft hesabınız kapatılır ve silinir.

## <a name="related-content"></a>İlgili içerik 

[İş için faturanızı veya faturanızı Microsoft 365 (](./billing-and-payments/understand-your-invoice2.md)makale)\
[Aboneliğinizi iptal etme](./subscriptions/cancel-your-subscription.md) (makale)

