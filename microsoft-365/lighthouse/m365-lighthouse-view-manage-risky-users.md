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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için riskli kullanıcıları görüntülemeyi ve yönetmeyi öğrenin.
ms.openlocfilehash: 0b7567404b909927a80b69184299baae131f8eb7
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824278"
---
# <a name="view-and-manage-risky-users"></a>Riskli kullanıcıları görüntüleme ve yönetme

Microsoft, her gün trilyonlarca kullanıcı oturum açma sinyali toplar ve analiz eder. Bu sinyaller, iyi kullanıcı oturum açma davranışı desenleri oluşturmaya ve olası riskli oturum açma girişimlerini belirlemeye yardımcı olmak için kullanılır. Azure Active Directory (Azure AD) Kimlik Koruması, bu sinyalleri kullanarak kullanıcı oturum açma girişimlerini gözden geçirir ve şüpheli bir etkinlik varsa işlem gerçekleştirir.

Microsoft 365 Lighthouse, tüm yönetilen kiracılarınızda riskli kullanıcıların tek bir görünümünü sağlayarak Azure AD Kimlik Koruması tarafından algılanan riskleri yönetmeye yardımcı olur. Parolalarını sıfırlayarak veya Microsoft 365 hesaplarında oturum açmalarını engelleyerek riskli kullanıcıların güvenliğini hızla sağlayabilirsiniz. Ayrıca bir kullanıcının riskini daha iyi anlamak ve sonraki adımları belirlemek için içgörüleri görüntüleyebilirsiniz.

Azure AD Kimlik Koruması, aşağıdakiler de dahil olmak üzere birçok türün risklerini tanımlar:

- Sızdırılan kimlik bilgileri
- Anonim IP kullanımı
- Atipik seyahat
- Virüslü cihazlardan oturum açma
- Şüpheli etkinlikle IP adreslerinden oturum açma
- Tanıdık olmayan konumlardan oturum açma

## <a name="before-you-begin"></a>Başlamadan önce

Kullanıcıların riskli kullanıcılar listesinde görünebilmesi için aşağıdaki koşulların karşılanması gerekir:

- Müşteri kiracısının her kullanıcı için bir Azure AD Premium lisansı olmalıdır. Azure AD Kimlik Koruması'nın desteklendiği lisanslar hakkında daha fazla bilgi için bkz. [Kimlik Koruması nedir?](/azure/active-directory/identity-protection/overview-identity-protection)

- Müşteri kiracısının Microsoft 365 Lighthouse içinde etkin olması gerekir. Kiracının etkin olup olmadığını belirlemek için bkz. [Microsoft 365 Lighthouse Kiracılar sayfasına genel bakış](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Algılanan riskleri gözden geçirin ve işlem yapın

Azure AD Kimlik Koruması'nda risk algılamaları, Azure AD'deki kullanıcı hesaplarıyla ilgili olarak tanımlanan şüpheli eylemleri içerir.

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Riskli Kullanıcılar** sekmesini seçin.

3. Risk durumu **Risk** altında olan kullanıcıları listede gözden geçirin.

4. Her kullanıcı için algılanan riskler hakkında ayrıntılı bilgi almak için **Risk algılamalarını görüntüle'yi** seçin. Risk türleri ve algılama hakkında daha fazla bilgi için bkz. [Risk nedir?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. Her kullanıcı için risk algılamalarını değerlendirin ve aşağıdaki eylemlerden birini uygun şekilde seçin:

    - Parolayı sıfırla – kullanıcı parolasını değiştirin veya sıfırlayın.

    - Oturum açmayı engelle - herkesin bu kullanıcı olarak oturum açmasını engelleyin.

    - Kullanıcının güvenliğinin aşıldığını onaylayın – risk durumunu güvenliği aşıldığını onaylayacak şekilde ayarlayın.

    - Kullanıcı riskini kapatma - Risk durumunu kapatılmış olarak ayarlayın.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Aynı anda birden çok kullanıcı hesabı üzerinde eylem gerçekleştirme

Aynı anda birden çok etkilenen kullanıcı üzerinde işlem yapmak için:

1. **Riskli Kullanıcılar** sekmesinde, üzerinde işlem yapmak istediğiniz kullanıcı kümesini seçin.

2. Gerçekleştirilecek aşağıdaki eylemlerden birini seçin:

    - Parolayı sıfırlayın

    - Oturum açmayı engelle

    - Kullanıcının güvenliğinin aşıldığını onaylayın

    - Kullanıcı riskini kapatma

> [!NOTE]
> Yönettiğiniz kuruluşun Azure AD Premium P2 lisansı varsa, Kullanıcı risk tabanlı koşullu erişim ilkelerini etkinleştirmeniz önerilir. Daha fazla bilgi için bkz [. Koşullu Erişim: Kullanıcı risk tabanlı Koşullu Erişim](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>İlgili içerik
[Öğretici: Azure AD Multi-Factor Authentication veya parola değişikliklerini tetikleme amacıyla kullanıcı oturum açma işlemleri için risk algılamalarını kullanma](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (makale)\
[Risk nedir?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (makale) \
[Riskleri düzeltme ve kullanıcıların engellemesini kaldırma](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (makale)
