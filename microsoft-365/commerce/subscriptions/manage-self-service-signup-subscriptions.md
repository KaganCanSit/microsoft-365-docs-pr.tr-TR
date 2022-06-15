---
title: Self servis kaydolma aboneliklerini yönetme
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
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
search.appverid: MET150
description: Kuruluşunuz için ücretsiz self servis kaydolma aboneliklerini yönetmeyi öğrenin.
ms.date: 03/17/2021
ms.openlocfilehash: 58c58c849b72c170e0ccf10de54389bd1245bced
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102360"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Self servis kaydolma aboneliklerini yönetme

## <a name="what-are-self-service-sign-up-subscriptions"></a>Self servis kaydolma abonelikleri nelerdir?

Kuruluşunuzdaki kullanıcıların kaydolabilecekleri sınırlı sayıda ücretsiz self servis kaydolma aboneliği vardır. Kullanıcı yalnızca self servis kaydolma aboneliğine kaydolabilir ve bu aboneliği kendisi için kullanabilir. Kullanıcıların kaydolmasını engelleyerek ve kullanıcıların kaydolmuş olduğu ücretsiz abonelikleri silerek self servis kayıt aboneliklerini yönetirsiniz. Self servis kaydolma ve kullanılabilir abonelikler hakkında daha fazla bilgi için bkz. [Kuruluşunuzda self servis kaydolmayı kullanma](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Self servis kaydolma aboneliklerinin listesini görüntüleme

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.
2. **Ürünler** sekmesinde filtre simgesini ve ardından **Ücretsiz'i** seçin. Tüm self servis kaydolma aboneliklerinin listesi görüntülenir.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Bu aboneliklerin self servis satın alma aboneliklerinden farkı nedir?

Self servis kaydolma abonelikleri ücretsizdir ve self servis satın alma aboneliklerinden daha büyük bir ürün listesi için kullanılabilir. Bir kullanıcı self servis satın alma aboneliğine kaydolduğunda, bu abonelik için ödemekten sorumludur. Self servis satın alma abonelikleri yalnızca Power Platform ürünleri (Power BI, Power Apps ve Power Automate), Project ve Visio için kullanılabilir. Daha fazla bilgi için bkz. [Self servis satın alma hakkında SSS](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Kullanıcıların kaydolmasını engelleme

Kullanıcıların self servis kayıt aboneliklerine kaydolup kaydolamayacağını denetlemek için **AllowAdHocSubscriptions** parametresiyle [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) cmdlet'ini kullanırsınız. Daha fazla bilgi için bkz. [Self servis ayarları Nasıl yaparım? denetlensin mi?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Self servis kaydolma aboneliğini silme

> [!IMPORTANT]
> Self servis kaydolma aboneliğini sildiğinizde, tüm kullanıcıların verilerine ve e-postalarına erişmesini engeller ve tüm verileri ve e-postaları silersiniz.

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.
2. **Ürünler** sekmesinde filtre simgesini ve ardından **Ücretsiz'i** seçin.
3. Silmek istediğiniz self servis kaydolma aboneliğini seçin. 
4. Abonelik ayrıntıları sayfasındaki **Abonelikler ve ödeme ayarları** bölümünde **Aboneliği sil'i** seçin.
5. **Aboneliği sil** bölmesinde onay kutusunu ve ardından **Aboneliği sil'i** seçin.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Dizin silmeyi engelleyen bir self servis kaydolma aboneliğim var

Bireysel kullanıcıların kaydolabileceği self servis kaydolma ürünleri, Azure AD dizininizde kimlik doğrulaması için bir konuk kullanıcı da oluşturur. Veri kaybını önlemek için, bu self servis ürünleri dizinden tamamen silinene kadar dizin silmelerini engeller. Bunlar yalnızca Azure AD yöneticisi tarafından silinebilir. Daha fazla bilgi için bkz. [Azure Active Directory dizinini silme](/azure/active-directory/users-groups-roles/directory-delete-howto).
