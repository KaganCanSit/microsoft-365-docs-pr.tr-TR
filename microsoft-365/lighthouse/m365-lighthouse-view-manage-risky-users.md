---
title: Riskli kullanıcıları görüntüleme ve yönetme
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse, riskli kullanıcıları görüntülemeyi ve yönetmeyi öğrenin.
ms.openlocfilehash: 708fc0576c85d9b8511ac6b31ed0398fae1b20d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704922"
---
# <a name="view-and-manage-risky-users"></a>Riskli kullanıcıları görüntüleme ve yönetme

Microsoft, kullanıcı oturum açma işaretlerini her gün toplar ve analiz eder. Bu sinyaller, iyi kullanıcı oturum açma davranışı düzenleri oluşturmak ve olası riskli oturum açma girişimlerini tanımlamak için kullanılır. Azure Active Directory (Azure AD) Kimlik Koruması bu sinyalleri kullanarak kullanıcı oturum açma girişimlerini gözden geçirer ve şüpheli etkinlikler varsa önlem alır.

Microsoft 365 Lighthouse kiracılar genelinde tek bir riskli kullanıcı görünümü sağlayarak Azure AD Kimlik Koruması tarafından algılanan riskleri yönetmenize yardımcı olur. Riskli kullanıcıların parolalarını sıfırlayarak veya kullanıcı hesaplarının kendi hesaplarında oturum açmalarını engelleyerek hızlı bir Microsoft 365 edinebilirsiniz. Ayrıca, bir kullanıcının riskini daha iyi anlamak ve sonraki adımları belirlemek için içgörüleri görüntüebilirsiniz.

Azure AD Kimlik Koruması, çeşitli türler için riskler tanımlar. Bu riskler:

- Sızdırılan kimlik bilgileri
- Anonim IP kullanımı
- Atipik seyahat
- Virüs bulaşmış cihazlardan oturum açma
- IP adreslerinden şüpheli etkinliklerle oturum açma
- Yabancı konumlardan oturum açma

## <a name="before-you-begin"></a>Başlamadan önce

Kullanıcılar riskli kullanıcılar listesinde görünmeden önce aşağıdaki koşulların karşılanıyor olması gerekir:

- Müşteri kiracısı, her kullanıcı Azure AD Premium lisansına sahip olması gerekir. Hangi lisansların Azure AD Identity Protection'i desteklemesi hakkında daha fazla bilgi için bkz [. Kimlik Koruması nedir?](/azure/active-directory/identity-protection/overview-identity-protection)

- Müşteri kiracısı, kiracı kiracı içinde Microsoft 365 Lighthouse. Kiracının etkin olup olmadığını belirlemek için Kiracılar [sayfasına Microsoft 365 Lighthouse bakın](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Algılanan riskleri gözden geçirme ve önlem alma

Azure AD Kimlik Koruması'da, risk algılamaları Azure AD'de kullanıcı hesaplarıyla ilgili tanımlanan şüpheli eylemleri içerir.

1. Deniz Feneri'nin sol gezinti bölmesinde Kullanıcılar'ı **seçin**.

2. Riskli **Kullanıcılar sekmesini** seçin.

3. Listede Risk durumu Risk altında olan kullanıcıları **gözden geçirebilirsiniz**.

4. Her **kullanıcı için algılanan riskler** hakkında ayrıntılı bilgi almak için Risk algılamalarını görüntüle'yi seçin. Risk türleri ve algılama hakkında daha fazla bilgi için bkz. [Risk nedir?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. Her kullanıcı için, risk algılamalarını değerlendirin ve uygun şekilde aşağıdaki eylemlerden birini seçin:

    - Parolayı sıfırlama – kullanıcı parolasını değiştirme veya sıfırlama.

    - Oturum açmasını engelle: Bu kullanıcı olarak herkesin oturum açmasını önle.

    - Güvenliğin ihlal edilmiş olduğunu onaylayın – risk durumunu güvenliği ihlal edilmiş olarak ayarlayın.

    - Kullanıcı riskini yok say - risk durumunu yok say olacak şekilde ayarlayın.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Bir kerede birden çok kullanıcı hesabı üzerinde işlem

Etkilenen birden çok kullanıcı üzerinde aynı anda işlem yapmak için:

1. Riskli **Kullanıcılar sekmesinde** , üzerinde işlem yapmak istediğiniz kullanıcı kümelerini seçin.

2. Gerçekleştirmek için aşağıdaki eylemlerden birini seçin:

    - Parolayı sıfırlayın

    - Oturum açma engelleme

    - Güvenliğin ihlal edilmiş olduğunu onaylama

    - Kullanıcı riskini yok sayma

> [!NOTE]
> Yönetmekte olduğu kuruluşun hızlı erişim Azure AD Premium P2 varsa, Kullanıcı risk tabanlı koşullu erişim ilkelerini etkinleştirmeniz önerilir. Daha fazla bilgi için bkz [. Koşullu Erişim: Kullanıcı risk tabanlı Koşullu Erişim](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>İlgili içerik
[Öğretici: Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) veya parola değişikliklerini tetiklemek için kullanıcı oturum açmalarında risk algılamaları kullanma (makale)\
[Risk nedir?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[Riskleri düzeltme ve kullanıcıların engellemesini kaldırma](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (makale)
