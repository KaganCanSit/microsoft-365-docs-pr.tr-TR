---
title: Önerilen güvenli belge ilkeleri - Microsoft 365 ilkeleri için | Microsoft Docs
description: Microsoft'un dosya erişiminin güvenliğini sağlamayla ilgili SharePoint ilkelerini açıklar.
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
ms.openlocfilehash: 4425ee0a4ee9abb7c87be7ed45d9f5c94b84cdc6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477027"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Site ve dosyaların güvenliğini SharePoint ilke önerileri

Bu makalede, kimlik ve cihaz erişimi ilkelerini korumak için önerilen kimlik Sıfır Güven cihaz erişimi ilkelerinin nasıl SharePoint ve OneDrive İş. Bu kılavuz, ortak kimlik [ve cihaz erişim ilkelerine yöneliktir](identity-access-policies.md).

Bu öneriler, şu üç farklı güvenlik ve koruma katmanına dayalıdır SharePoint dosyaları, şu şekildeki ihtiyaçlarınızı ayrıntılı olarak temel alarak **uygulanabilir: başlangıç** **noktası, kurumsal** ve **özel güvenlik**. Genel bakış bilgisinde, bu önerilerden başvurulan bu güvenlik katmanları ve önerilen istemci işletim sistemleri hakkında daha fazla [bilgi edinmek için bkz](microsoft-365-policies-configurations.md).

Bu kılavuzu uygulamaya ek olarak, siteleri SharePoint ve özelleştirilmiş güvenlik içeriği için uygun izinler ayarlama da dahil, doğru koruma miktarına sahip olarak yapılandırmış olun.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Genel ilkeleri e-SharePoint güncelleştirme OneDrive İş

Ortak kimlik ve cihaz SharePoint OneDrive için, aşağıdaki diyagramda ortak kimlik ve cihaz erişim ilkelerinden güncelleştirilen ilkeler çiziliyor.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Postane erişimi korumayla ilgili ilke güncelleştirmelerinin SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Ortak ilkeleri SharePoint yeni ilkeler oluşturduysanız, yalnızca yeni ilkeleri oluşturmanız gerekir. Koşullu Erişim ilkeleri için, SharePoint kuralları OneDrive.

Yeni ilkeler, belirttiğiniz sitelere belirli erişim gereksinimleri uygulayarak kuruluş ve özelleştirilmiş güvenlik içeriği SharePoint koruma uygular.

Aşağıdaki tabloda, gözden geçirmeniz ve güncelleştirmeniz veya yeni oluşturmanız gereken ilkeler liste SharePoint. Ortak ilkeler, Ortak kimlik ve cihaz erişimi ilkeleri [makalesinde yer alan ilişkili yapılandırma yönergelerine](identity-access-policies.md) bağlantı sağlar.

|Koruma düzeyi|İlkeler|Daha fazla bilgi|
|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski orta veya yüksek olduğunda MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut SharePoint diğer özellikleri de ödeve dahil edin.|
||[Modern kimlik doğrulamasını desteklemez istemcileri engelleme](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Bulut SharePoint diğer özellikleri de ödeve dahil edin.|
||[UYGULAMA veri koruma ilkelerini uygulama](identity-access-policies.md#apply-app-data-protection-policies)|Tüm önerilen uygulamaların uygulama listesine ek olduğundan emin olun. Her platformun (iOS, Android, Mobil Cihazlar) ilkesini güncelleştir Windows.|
||[Mobil uygulamada zorunlu kısıtlamaları SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Bu yeni ilkeyi ekleyin. Bu, Azure Active Directory (Azure AD) için bu ayarda belirtilen ayarları SharePoint. Bu ilke tüm kullanıcılar için geçerlidir, ancak yalnızca bu ilkeye dahil olan sitelere SharePoint etkiler.|
|**Enterprise**|[Oturum açma riski düşük, orta veya *yüksek olduğunda* MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut SharePoint ödevlere notlarınızı dahil edin.|
||[Uyumlu bilgisayar ve *mobil cihaz* gerektirme](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Bulut SharePoint bu uygulamaları ekleyin.|
||[SharePoint denetimi ilkesi:](#sharepoint-access-control-policies) Yalnızca tarayıcı erişimine izin ver ve SharePoint cihazlardan belirli sitelere erişime izin ver.|Bu, dosyaların düzenlenmesini ve indir indirebilirsiniz. Siteleri belirtmek için PowerShell kullanın.|
|**Özel güvenlik**|[*Her* zaman MFA gerektir](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut SharePoint diğer özellikleri de ödeve dahil edin.|
||[SharePoint denetim ilkesi:](#use-app-enforced-restrictions-in-sharepoint) Belirli sitelere, SharePoint olmayan cihazlardan erişimi engelleme.|Siteleri belirtmek için PowerShell kullanın.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Mobil uygulamada uygulamanın zorunlu SharePoint

SharePoint'de erişim denetimleri SharePoint, Azure AD'den Azure AD'ye dış içerikte yapılandırılan ilkeleri zorunlu SharePoint. Bu ilke tüm kullanıcılar için geçerlidir, ancak yalnızca PowerShell kullanarak belirttiğiniz sitelere erişimi SharePoint.

Bu ilkeyi yapılandırmak için, Kolay erişilen cihazlardan erişimi denetleme'de "SharePoint site koleksiyonlarına veya OneDrive hesaplarına erişimi engelleme veya sınırlama" [bağlantılarına bakın](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>SharePoint denetimi ilkelerini denetleme

Microsoft, cihaz erişim denetimleriyle kurumsal SharePoint özelleştirilmiş güvenlik içeriği ile tüm sitelerde ve sitelerde yer alan içeriği korumanıza izin verir. Bunu yapmak için, koruma düzeyini ve korumanın uygulanacak siteleri belirten bir ilke oluşturulur.

- Enterprise: Yalnızca tarayıcı erişimine izin ver. Bu, kullanıcıların dosyaları düzenlemesini ve indirmesini sağlar.
- Özel güvenlik siteleri: Unmanaged cihazlarından erişimi engelin.

Unmanaged cihazlarından erişimi denetleme altında SharePoint "Belirli site koleksiyonlarına veya OneDrive hesaplarına erişimi engelleme veya sınırlama" [bağlantılarına bakın](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Bu ilkeler birlikte nasıl çalışır?

Site izinlerinin genellikle sitelere SharePoint ilgili iş ihtiyaçlarına dayalı olduğunu anlamanız önemlidir. Bu izinler site sahipleri tarafından yönetilir ve son derece dinamik olabilir. SharePoint erişim ilkelerinin kullanılması, kullanıcıların başlangıç noktası, kurumsal veya özel güvenlik koruması ile ilişkilendirilmiş bir Azure AD grubuna atanmış olup olmadığınıza bakılmaksızın bu sitelerin korumasını sağlar.

Aşağıdaki çizimde, cihaz erişim ilkelerinin SharePoint için sitelere erişimi nasıl koruy korumları gösterilmiştir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Cihaz erişim ilkelerinin SharePoint koruma örneği" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James'in başlangıç noktası Koşullu Erişim ilkeleri atanmıştır, ancak kurumsal veya özel güvenlik SharePoint belirli sitelere erişim izni verilmiştir.

- James, bilgisayarını kullanarak kuruluş veya özel güvenlik korumasına üye olduğu bir siteye erişse, bu siteye erişim izni ve verilmesini sağlar.
- James, yöneticisi olmayan telefonunu kullanarak bir kuruluş koruma sitesine erişmişse ve başlangıç noktası kullanıcılarına izin verilirse, bu site için yapılandırılmış cihaz erişim ilkesinden dolayı kuruluş sitesine yalnızca tarayıcı erişimi alır.
- İbrahim özel bir güvenlik sitesine erişmişse ve o da unmaned telefonunu kullanarak üyesi olursa, bu site için yapılandırılmış erişim ilkesi nedeniyle engellenir. Bu siteye yalnızca kendi yönetilen bilgisayarını kullanarak erişebilirsiniz.

## <a name="next-step"></a>Sonraki adım

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="4. Adım - Bulut uygulamaları Microsoft 365 ilkeleri" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::


Koşullu Erişim ilkelerini aşağıdakiler için yapılandırma:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)