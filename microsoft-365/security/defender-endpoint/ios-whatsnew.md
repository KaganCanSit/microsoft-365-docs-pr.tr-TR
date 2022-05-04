---
title: iOS'ta Uç Nokta için Microsoft Defender'deki yenilikler
description: iOS'ta önceki Uç Nokta için Microsoft Defender sürümlerine yönelik önemli değişiklikler hakkında bilgi edinin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 7f3a687eb365813192948e48514bf7384cc584d0
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188215"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Microsoft Defender'deki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


## <a name="integration-with-tunnel"></a>Tunnel ile tümleştirme
iOS'taki Uç Nokta için Microsoft Defender artık tek bir uygulamada güvenliği ve bağlantıyı etkinleştirmek için bir VPN ağ geçidi çözümü olan Microsoft Tunnel ile tümleştirilebilir.  Tunnel ile tümleştirme, iOS'ta tek bir uygulamayla daha basit ve güvenli bir VPN deneyimi sağlar. Bu özellik daha önce yalnızca Android'de kullanılabilirdi. Daha fazla ayrıntı için [buradaki techcommunity gönderisine bakın](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Denetimli iOS cihazlarında geliştirilmiş deneyim

iOS'ta Uç Nokta için Microsoft Defender artık bu tür cihazlarda platform tarafından sağlanan artan yönetim özellikleri göz önüne alındığında denetimli iOS/iPadOS cihazlarında özel yeteneklere sahiptir. Ayrıca **cihazda yerel BIR VPN ayarlamadan** Web Koruması sağlayabilir. Bu, son kullanıcılara kimlik avı ve diğer web tabanlı saldırılardan korunmaya devam ederken sorunsuz bir deneyim sunar. Ayrıntılar için [bu belgeleri ziyaret edin](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Uç Nokta için Microsoft Defender artık Uygulama mağazasında Microsoft Defender

Uç Nokta için Microsoft Defender artık uygulama mağazasında **Microsoft Defender** olarak kullanılabilir. Bu güncelleştirmeyle, uygulama **ABD bölgesindeki Tüketiciler** için önizleme olarak kullanıma sunulacaktır. uygulamada iş veya kişisel hesabınızla nasıl oturum açtığınıza bağlı olarak, Uç Nokta için Microsoft Defender veya kişiler için Microsoft Defender özelliklerine erişebilirsiniz. Daha fazla bilgi için [bu bloga](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) bakın.

## <a name="threat-and-vulnerability-management"></a>Tehdit ve Güvenlik Açığı Yönetimi

25 Ocak 2022'de Android ve iOS'ta Tehdit ve Güvenlik Açığı yönetiminin genel kullanılabilirliğini duyurduk. Diğer ayrıntılar için [buradaki techcommunity gönderisine](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663) bakın.


## <a name="1128250101"></a>1.1.28250101
- **Tunnel ile tümleştirme** - iOS'taki Uç Nokta için Microsoft Defender artık tek bir uygulamada güvenliği ve bağlantıyı etkinleştirmek için bir VPN ağ geçidi çözümü olan Microsoft Tunnel ile tümleştirilebilir. Daha fazla bilgi için bkz. [Microsft Tunnel Genel Bakış](/mem/intune/protect/microsoft-tunnel-overview).
- Microsoft Endpoint Manager (Intune) aracılığıyla kaydedilen **kayıtlı iOS cihazları için sıfır dokunmayla ekleme** genel kullanıma sunulmuştur. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender sıfır dokunma ekleme](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- Hata düzeltmeleri.


## <a name="1124210103"></a>1.1.24210103

- Denetimli cihazlarda İnternet bağlantısı sorunları çözüldü. Daha fazla bilgi için bkz. [Uç Nokta için Defender'ı kayıtlı iOS cihazlarında dağıtma](ios-install.md).
- Hata düzeltmeleri.

## <a name="1123250104"></a>1.1.23250104

- Performans iyileştirmeleri - Pil performansını bu sürümle test edin ve geri bildiriminizi bize bildirin.
- **Kayıtlı iOS cihazları için sıfır dokunmayla ekleme** - Bu sürümle, Microsoft Endpoint Manager (Intune) aracılığıyla kaydedilen cihazlar için Sıfır dokunma ekleme önizlemesi eklenmiştir. Daha fazla bilgi için kurulum ve yapılandırma hakkında daha fazla bilgi için bu [belgelere](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) bakın.
- **Gizlilik Denetimleri** - Kimlik avı uyarısı raporu için gizlilik denetimlerini yapılandırın. Daha fazla bilgi için bkz [. iOS özelliklerini yapılandırma](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Hata düzeltmeleri ve performans geliştirmeleri 
  - Bu sürümde performans iyileştirmeleri yapılmıştır. Bu sürümle pil performansını test edin ve geri bildiriminizi bize bildirin.

## <a name="1120240103"></a>1.1.20240103
- Cihaz Durumu kartı - Cihaz Durumu kartı, son kullanıcılara bekleyen yazılım güncelleştirmeleri hakkında bildirimde bulunur.
- Kullanılabilirlik iyileştirmeleri - Son kullanıcılar artık MSDefender uygulamasının kendisinden Uç Nokta IÇIN Defender VPN'i devre dışı bırakabilir. Bu güncelleştirmeden önce son kullanıcıların VPN'i yalnızca Ayarlar uygulamasından devre dışı bırakması gerekiyordu.
- Hata düzeltmeleri.

## <a name="1120020101"></a>1.1.20020101
- UX Geliştirmeleri - Uç Nokta için Microsoft Defender yeni bir görünüme sahiptir.
- Hata düzeltmeleri.

## <a name="1117240101"></a>1.1.17240101
- Intune aracılığıyla Mobil Uygulama Yönetimi (MAM) desteği genellikle bu sürümle sağlanır. Daha fazla bilgi için bkz[. Uygulama koruması ilkeleriniz için kullanılabilir Uç Nokta için Microsoft Defender risk sinyalleri](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Jailbreak Algılama** genel kullanıma sunulmuştur. Daha fazla bilgi için bkz. [Cihaz risk sinyallerine göre Koşullu Erişim İlkesi'ni ayarlama](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- Microsoft Endpoint Manager (Intune) aracılığıyla kayıtlı cihazlar için **VPN profilinin otomatik kurulumu** genel olarak kullanılabilir. Daha fazla bilgi için bkz. [Kayıtlı iOS cihazları için VPN profilini Otomatik Ayarlama](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Hata düzeltmeleri.

## <a name="1115140101"></a>1.1.15140101

- **Jailbreak Algılama** önizleme aşamasındadır. Daha fazla bilgi için bkz. [Cihaz risk sinyallerine göre Koşullu Erişim İlkesi'ni ayarlama](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **VPN profilinin otomatik kurulumu**, Microsoft Endpoint Manager (Intune) aracılığıyla kayıtlı cihazlar için önizleme aşamasındadır. Daha fazla bilgi için bkz. [Kayıtlı iOS cihazları için VPN profilini Otomatik Ayarlama](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Microsoft Defender ATP ürün adı artık uygulama mağazasında Uç Nokta için Microsoft Defender olarak güncelleştirildi.
- Geliştirilmiş oturum açma deneyimi.
- Hata düzeltmeleri.

## <a name="1115010101"></a>1.1.15010101

- Bu sürümle, iPadOS/iPad cihazları için destek duyuruyoruz.
- Hata düzeltmeleri.
