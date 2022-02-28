---
title: Self servis kayıt aboneliklerini yönetme
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
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
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid: MET150
description: Organizasyonunuz için ücretsiz self servis kayıt aboneliklerini yönetmeyi öğrenin.
ms.date: 03/17/2021
ms.openlocfilehash: 24f852a1eb9983e211000b59bda32eaa2c6bf0fa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985034"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Self servis kayıt aboneliklerini yönetme

## <a name="what-are-self-service-sign-up-subscriptions"></a>Self servis kayıt abonelikleri nedir?

Sınırlı sayıda ücretsiz self servis kayıt aboneliği, kuruma kaydolan kullanıcılar tarafından kullanılabilir. Bir kullanıcı sadece kendi kendine kayıt olmak için kaydolarak kendi kendine kayıt aboneliği kullanabilir. Kullanıcıların kaydolmasını engelleyerek ve kullanıcıların kaydolan ücretsiz aboneliklerini silerek self servis kayıt aboneliklerini yönetirsiniz. Self servis kaydolma ve kullanılabilir abonelikler hakkında daha fazla bilgi için bkz [. Kurumda self servis kayıt kullanma](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Self servis kayıt aboneliklerinin listesini görüntüleme

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a>  >  products sayfasına gidin.
2. Ürünler sekmesinde **filtre** simgesini ve ardından Ücretsiz'i **seçin**. Tüm self servis kayıt aboneliklerinin listesi görüntülenir.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Bu aboneliklerin self servis satın alma aboneliklerinden ne kadar farklı?

Self servis kayıt abonelikleri ücretsizdir ve self servis satın alma abonelikleri yerine daha geniş bir ürün listesinde kullanılabilir. Bir kullanıcı self servis satın alma aboneliğine oturum ayanınca, ödemeden sorumlu olur. Self servis satın alma abonelikleri yalnızca Power Platform ürünleri (Power BI, Power Apps, Power Automate), Project ve Visio. Daha fazla bilgi için bkz [. Self servis satın alma hakkında SSS](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Kullanıcıların kaydolmasını engelleme

[**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) cmdlet'ini **AllowAdHocSubscriptions** parametresiyle kullanarak kullanıcıların self servis kayıt aboneliklerine kaydolup kaydolamay denetlemelerini sağlarsınız. Daha fazla bilgi için bkz [. Self servis ayarları nasıl kontrol musunuz?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Self servis kayıt aboneliğini silme

> [!IMPORTANT]
> Self servis kayıt aboneliğini silerek tüm kullanıcıların verilerine ve e-postalarına erişmesini, ardından tüm verileri ve e-postayı silmesini engelleyebilirsiniz.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a>  >  products sayfasına gidin.
2. Ürünler sekmesinde **filtre** simgesini ve ardından Ücretsiz'i **seçin**.
3. Silmek istediğiniz self servis kayıt aboneliğini seçin. 
4. Abonelik ayrıntıları sayfasında, Abonelikler ve **ödeme ayarları bölümünde Aboneliği** **sil'i seçin**.
5. Aboneliği **sil bölmesinde onay** kutusunu seçin ve ardından Aboneliği sil'i **seçin**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Dizin silmeyi engelleyen bir self servis kayıt aboneliğim var

Tek tek kullanıcıların kaydolabilirsiniz self servis kayıt ürünleri, Azure AD dizinde kimlik doğrulaması için bir konuk kullanıcı da oluşturabilir. Veri kaybını önlemek için, bu self servis ürünler dizinden tamamen silinene kadar dizin silmelerini engelleyebilir. Bunlar yalnızca Azure AD yöneticisi tarafından silinebilir. Daha fazla bilgi için bkz[. Dizin silme Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
