---
title: Önerilen güvenli belge ilkeleri - kurumsal | için Microsoft 365 Microsoft Docs
description: SharePoint dosya erişiminin güvenliğini sağlama hakkında Microsoft önerilerine yönelik ilkeleri açıklar.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 3a2a8e5be8fb78824e8670f94a2e087da9538329
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972155"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>SharePoint sitelerin ve dosyaların güvenliğini sağlamaya yönelik ilke önerileri

Bu makalede, SharePoint ve OneDrive İş korumak için önerilen Sıfır Güven kimlik ve cihaz erişim ilkelerinin nasıl uygulandığı açıklanır. Bu kılavuz [, ortak kimlik ve cihaz erişim ilkelerine](identity-access-policies.md) dayalıdır.

Bu öneriler, gereksinimlerinizin ayrıntı düzeyine göre uygulanabilen SharePoint dosyaları için üç farklı güvenlik ve koruma katmanını temel alır: **başlangıç noktası**, **kuruluş** ve **özel güvenlik**. Bu güvenlik katmanları ve önerilen istemci işletim sistemleri hakkında daha fazla bilgi edinmek için [genel bakış](microsoft-365-policies-configurations.md) bölümünde bu önerilere başvurabilirsiniz.

Bu kılavuzu uygulamaya ek olarak, kurumsal ve özel güvenlik içeriği için uygun izinleri ayarlama da dahil olmak üzere SharePoint siteleri doğru koruma miktarıyla yapılandırırken emin olun.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Yaygın ilkeleri SharePoint ve OneDrive İş içerecek şekilde güncelleştirme

SharePoint ve OneDrive dosyaları korumak için, aşağıdaki diyagramda ortak kimlik ve cihaz erişim ilkelerinden hangi ilkelerin güncelleştirildiği gösterilmektedir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="SharePoint erişimini korumaya yönelik ilke güncelleştirmelerinin özeti" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Ortak ilkeleri oluştururken SharePoint eklediyseniz, yalnızca yeni ilkeleri oluşturmanız gerekir. Koşullu Erişim ilkeleri için SharePoint OneDrive içerir.

Yeni ilkeler, belirttiğiniz SharePoint sitelere belirli erişim gereksinimlerini uygulayarak kurumsal ve özel güvenlik içeriği için cihaz korumasını uygular.

Aşağıdaki tabloda, SharePoint için gözden geçirmeniz ve güncelleştirmeniz veya yeni oluşturmanız gereken ilkeler listelenir. Ortak ilkeler, [Ortak kimlik ve cihaz erişim ilkeleri](identity-access-policies.md) makalesindeki ilişkili yapılandırma yönergelerine bağlanır.

|Koruma düzeyi|İlkeler|Daha fazla bilgi|
|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski *orta* veya *yüksek* olduğunda MFA gerektirme](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut uygulamalarının atanma aşamasına SharePoint ekleyin.|
||[Modern kimlik doğrulamayı desteklemeyen istemcileri engelleme](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Bulut uygulamalarının atanma aşamasına SharePoint ekleyin.|
||[APP veri koruma ilkelerini uygulama](identity-access-policies.md#apply-app-data-protection-policies)|Önerilen tüm uygulamaların uygulama listesine eklendiğinden emin olun. Her platform (iOS, Android, Windows) için ilkeyi güncelleştirin.|
||[SharePoint'da uygulama tarafından zorunlu kılınan kısıtlamaları kullanma](#use-app-enforced-restrictions-in-sharepoint)|Bu yeni ilkeyi ekleyin. Bu, Azure Active Directory 'a (Azure AD) SharePoint'de belirtilen ayarları kullanmasını bildirir. Bu ilke tüm kullanıcılar için geçerlidir, ancak yalnızca SharePoint erişim ilkelerine dahil edilen sitelere erişimi etkiler.|
|**Enterprise**|[Oturum açma riski *düşük*, *orta* veya *yüksek* olduğunda MFA gerektirme](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut uygulamalarının atamalarına SharePoint ekleyin.|
||[Uyumlu bilgisayarlar *ve* mobil cihazlar gerektirme](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Bulut uygulamaları listesine SharePoint ekleyin.|
||[SharePoint erişim denetimi ilkesi](#sharepoint-access-control-policies): Yönetilmeyen cihazlardan belirli SharePoint sitelerine yalnızca tarayıcı erişimine izin verin.|Bu, dosyaların düzenlenmesini ve indirilmesini engeller. Siteleri belirtmek için PowerShell'i kullanın.|
|**Özel güvenlik**|[*Her zaman* MFA iste](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut uygulamalarının atanma aşamasına SharePoint ekleyin.|
||[SharePoint erişim denetimi ilkesi](#use-app-enforced-restrictions-in-sharepoint): Yönetilmeyen cihazlardan belirli SharePoint sitelerine erişimi engelleyin.|Siteleri belirtmek için PowerShell'i kullanın.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>SharePoint'de uygulama tarafından zorunlu kılınan kısıtlamaları kullanma

SharePoint'de erişim denetimleri uygularsanız, Azure AD'ye SharePoint yapılandırdığınız ilkeleri zorlamasını bildirmek için Azure AD'de Koşullu Erişim ilkeleri oluşturulur. Varsayılan olarak, bu ilke tüm kullanıcılar için geçerlidir, ancak yalnızca SharePoint'de erişim denetimlerini oluşturduğunuzda PowerShell kullanarak belirttiğiniz sitelere erişimi etkiler. İlkenin kapsamı belirli kullanıcılar, gruplar veya siteler için de değiştirilebilir.

Bu ilkeyi yapılandırmak için [Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices) bölümünde "Belirli SharePoint site koleksiyonlarına veya OneDrive hesaplarına erişimi engelleme veya sınırlama" konusuna bakın.

## <a name="sharepoint-access-control-policies"></a>Erişim denetimi ilkelerini SharePoint

Microsoft, SharePoint sitelerdeki içeriği cihaz erişim denetimleriyle kurumsal ve özel güvenlik içeriğiyle korumanızı önerir. Bunu, koruma düzeyini ve korumanın uygulanacağı siteleri belirten bir ilke oluşturarak yaparsınız.

- Enterprise siteler: Yalnızca tarayıcı erişimine izin ver. Bu, kullanıcıların dosyaları düzenlemesini ve indirmesini engeller.
- Özel güvenlik siteleri: Yönetilmeyen cihazlardan erişimi engelleyin.

[Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices) bölümünde "Belirli SharePoint site koleksiyonlarına veya OneDrive hesaplarına erişimi engelleme veya sınırlama" bölümüne bakın.

## <a name="how-these-policies-work-together"></a>Bu ilkeler birlikte nasıl çalışır?

SharePoint site izinlerinin genellikle sitelere erişim için iş gereksinimine dayandığını anlamak önemlidir. Bu izinler site sahipleri tarafından yönetilir ve son derece dinamik olabilir. SharePoint cihaz erişim ilkelerinin kullanılması, kullanıcıların başlangıç noktası, kuruluş veya özel güvenlik korumasıyla ilişkili bir Azure AD grubuna atanmasından bağımsız olarak bu sitelere koruma sağlar.

Aşağıdaki çizimde, SharePoint cihaz erişim ilkelerinin bir kullanıcı için sitelere erişimi nasıl koruduğuna ilişkin bir örnek verilmiştir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="SharePoint cihaz erişim ilkelerinin siteleri nasıl koruduğuna bir örnek" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James'in başlangıç noktası Koşullu Erişim ilkeleri atanmıştır, ancak kurumsal veya özel güvenlik korumasına sahip SharePoint sitelerine erişim verilebilir.

- James üyesi olduğu bir siteye bilgisayarını kullanarak kurumsal veya özel güvenlik koruması ile erişirse, erişimi verilir.
- James, başlangıç noktası kullanıcıları için izin verilen yönetilmeyen telefonunu kullanarak üyesi olduğu bir kurumsal koruma sitesine erişirse, bu site için yapılandırılan cihaz erişim ilkesi nedeniyle kuruluş sitesine yalnızca tarayıcı erişimi alır.
- James yönetilmeyen telefonunu kullanarak üyesi olduğu özel bir güvenlik sitesine erişirse, bu site için yapılandırılan erişim ilkesi nedeniyle engellenir. Bu siteye yalnızca yönetilen bilgisayarını kullanarak erişebilir.

## <a name="next-step"></a>Sonraki adım

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="4. Adım - Microsoft 365 bulut uygulamaları için ilkeler" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Koşullu Erişim ilkelerini yapılandırma:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
