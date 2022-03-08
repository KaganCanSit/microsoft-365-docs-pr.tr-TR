---
title: E-posta için önerilen güvenli e-posta ilkeleri - Microsoft 365 kurumsal e-posta | Microsoft Docs
description: Microsoft'un e-posta ilkelerinin ve yapılandırmalarının nasıl uygulanacakları konusunda önerilerine yönelik ilkeleri açıklar.
ms.author: dansimp
author: dansimp
manager: Laurawi
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
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: b708d7aa993bdcd74b6fe00f633e3f7933ff04b8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321747"
---
# <a name="policy-recommendations-for-securing-email"></a>E-postanın güvenliğini sağlamak için ilke önerileri

Bu makalede, modern kimlik doğrulamayı ve koşullu erişimi destekleyen kurumsal e-posta ve e-posta istemcilerini korumak için önerilen Sıfır Güven kimliği ve cihaz erişimi ilkelerinin nasıl uygulan uygulanıyor olduğu açıklanmıştır. Bu kılavuz, Ortak kimlik [ve cihaz erişimi ilkelerine yöneliktir](identity-access-policies.md) ve birkaç ek öneri içerir.

Bu öneriler, şu üç farklı güvenlik ve koruma katmanına dayalıdır ve bu katman, ihtiyaçlarınızı ayrıntılı olarak temel alarak **uygulanır: başlangıç** **noktası, kurumsal** ve **özel güvenlik**. Bu güvenlik katmanları ve önerilen istemci işletim sistemleri hakkında daha fazla bilgi edinmek için önerilen güvenlik ilkeleri ve yapılandırmalara giriş önerisinde bu önerilerden [başvurulmalıdır](microsoft-365-policies-configurations.md).

Bu öneriler, kullanıcılarınızı, mobil cihazlarda iOS ve Android için Outlook e-posta istemcileri gibi modern e-posta istemcilerini kullanmalarını gerektirir. Outlook Android için Uygulama, uygulamanın en iyi özellikleri için Office 365. Bu mobil Outlook, mobil kullanımı destekleyen ve diğer Microsoft bulut güvenlik özellikleriyle birlikte çalışacak güvenlik özellikleriyle de birlikte çalışır. Daha fazla bilgi için bkz. [iOS Outlook Android için SSS](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Ortak ilkeleri e-posta içerecek şekilde güncelleştirme

E-postayı korumak için, aşağıdaki diyagramda ortak kimlik ve cihaz erişimi ilkelerinden güncelleştirilen ilkeler çiziliyor.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="E-postanıza erişimi korumak için yapılan ilke güncelleştirmelerinin Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

ActiveSync istemcilerini engellemek için yeni Exchange Online ilkenin eklenmemiş olması gerekir. Bu, mobil cihazlarda Outlook güçler.

İlkeleri Exchange Online ve Outlook kapsamında ekliyseniz ActiveSync istemcilerini engellemek için yeni ilke oluşturmanız gerekir. Aşağıdaki tabloda listelenen ilkeleri gözden geçirin ve önerilen eklemeleri yapın veya bunların zaten dahil olduğunu onaylayın. Her ilke, Ortak kimlik ve cihaz erişimi [ilkeleri'nin ilgili yapılandırma yönergelerine bağlantı sağlar](identity-access-policies.md).

|Koruma düzeyi|İlkeler|Daha fazla bilgi|
|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski orta veya yüksek olduğunda MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut Exchange Online ödeve diğer uygulamaları dahil edin|
||[Modern kimlik doğrulamasını desteklemez istemcileri engelleme](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Bulut Exchange Online ödeve diğer uygulamaları dahil edin|
||[UYGULAMA veri koruma ilkelerini uygulama](identity-access-policies.md#apply-app-data-protection-policies)|Uygulama Outlook bir uygulama listesine ekli olduğundan emin olun. Her platformun (iOS, Android, Sistem) ilkesini güncelleştirmeye Windows|
||[Onaylanan uygulamalar ve UYGULAMA koruması gerektirme](identity-access-policies.md#require-approved-apps-and-app-protection)|Bulut Exchange Online listesine ek uygulamaları ekleme|
||[ActiveSync istemcilerini engelleme](#block-activesync-clients)|Bu yeni ilkeyi ekle|
|**Enterprise**|[Oturum açma riski düşük, orta veya *yüksek olduğunda* MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut Exchange Online ödeve diğer uygulamaları dahil edin|
||[Uyumlu bilgisayar ve *mobil cihaz* gerektirme](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Bulut Exchange Online listesine ek uygulamaları ekleme|
|**Özel güvenlik**|[*Her* zaman MFA gerektir](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bulut Exchange Online ödeve diğer uygulamaları dahil edin|
|

## <a name="block-activesync-clients"></a>ActiveSync istemcilerini engelleme

Exchange ActiveSync mobil cihazlarda mesajlaşma ve takvim verilerini eşitlemek için kullanılabilir.

Mobil cihazlarda, intune uygulama koruma ilkelerini (veya uygulama koruma ilkesinde tanımlanmamış desteklenen istemcileri) desteklemeyen modern kimlik doğrulama özellikli Exchange ActiveSync istemcileri ve temel kimlik doğrulaması kullanan Exchange ActiveSync istemcileri, Onaylanan uygulamalar ve UYGULAMA koruması gerektirme altında oluşturulan Koşullu Erişim ilkesine bağlı olarak [engellenir.](identity-access-policies.md#require-approved-apps-and-app-protection)

Diğer cihazlarda Exchange ActiveSync kimlik doğrulaması kullanmalarını engellemek için Tüm cihazlarda [Exchange ActiveSync](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices) engelleme'de yer alan ve mobil olmayan cihazlarda temel kimlik doğrulaması kullanan Exchange ActiveSync istemcilerinin Exchange Online.

Ayrıca, tüm istemci erişim isteklerini modern kimlik [doğrulamayı](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) kullanmaya güç kullanan Temel kimlik doğrulamayı devre dışı bırakmak için de kimlik doğrulama ilkelerini kullanabilirsiniz.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Erişimi izin izin Exchange Online gelen Web üzerinde Outlook

Kullanıcıların, e-posta eklerini, bilgisayarınızdan ve Web üzerinde Outlook cihazlara indirmesini kısıtabilirsiniz. Bu cihazlardaki kullanıcılar, sızdırmadan ve bu dosyaları cihazda depolamadan Office Online kullanarak bu dosyaları  görüntüleyemez ve düzenleyebilir. Ayrıca kullanıcıların ekleri, yöneticisi olmayan bir cihazda görmelerini engelleyebilirsiniz.

Adımlar şunlardır:

1. [Bağlan uzak PowerShell Exchange Online oturuma geri bağlanın](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Henüz bir OWA posta kutusu ilkenız yoksa, [New-OwaMailboxPolicy cmdlet'iyle bir](/powershell/module/exchange/new-owamailboxpolicy) ilke oluşturun.
3. Eklerin görüntülemesine izin vermek, ancak indirmeye izin vermek istemiyorsanız, şu komutu kullanın:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Ekleri engellemek için şu komutu kullanın:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. Azure portalda, şu ayarlarla yeni bir Koşullu Erişim ilkesi oluşturun:

   **Ödevler** \> **Kullanıcılar ve gruplar**: Dahil etmek ve dışlamak için uygun kullanıcıları ve grupları seçin.

   **Ödevler** \> **Bulut uygulamaları veya eylemleri** \> **Bulut uygulamaları** \> **Dahil** \> **Uygulamaları seçme**: Uygulama **seç Office 365 Exchange Online**

   **Access denetimleri** \> **Oturum**: **Uygulamanın zorunlu kısıtlamalarını kullan'ı seçin**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>iOS ve Android cihazlarının Outlook

iOS ve Android cihazlarının kullanıcılarının, iOS ve Android için Outlook kullanarak yalnızca iş veya okul içeriğine erişene emin olmak için, bu olası kullanıcıları hedef alan bir Koşullu Erişim ilkesi gerekir.

iOS ve Android için E-posta [kullanarak ileti işbirliği erişimini yönetme Outlook ilkeyi yapılandırma adımlarına bakın](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>İleti şifrelemeyi ayarlama

Azure Information Protection Office 365 İleti Şifrelemesi koruma özelliklerinden yararlanan yeni Uygulama Sistemi (OME) özellikleriyle, kuruluşlarınız korumalı e-postaları herhangi bir cihazdan herkesle kolayca paylaşabilir. Kullanıcılar, Microsoft 365.com, Gmail ve diğer e-posta hizmetlerini kullanan, diğer Outlook olmayan kuruluşlarla da korumalı iletiler gönderebilir ve alabilirsiniz.

Daha fazla bilgi için bkz[. Yeni özellik Office 365 İleti Şifrelemesi ayarlama](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Sonraki adımlar

![4. Adım: Bulut Microsoft 365 için ilkeler.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Koşullu Erişim ilkelerini aşağıdakiler için yapılandırma:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
