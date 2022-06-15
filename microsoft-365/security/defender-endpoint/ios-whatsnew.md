---
title: iOS'da Uç Nokta için Microsoft Defender'deki yenilikler
description: iOS'da Uç Nokta için Microsoft Defender önceki sürümlerine yönelik önemli değişiklikler hakkında bilgi edinin.
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
ms.openlocfilehash: 3f05c819e5390504bca9c1f5aaa7f85d1e7edc2a
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090489"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>iOS'da Uç Nokta için Microsoft Defender'deki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="network-protection"></a>Ağ koruması
Uç Nokta için Microsoft Defender'da Ağ Koruması artık genel önizleme aşamasındadır. Ağ koruması, sahte Wi-Fi ilgili tehditlere, ananas cihazları gibi sahte donanımlara karşı koruma sağlar ve ilgili bir tehdit algılandığında kullanıcıya bildirir. Kullanıcılar güvenli olmayan bir bağlantıya bağlandıklarında güvenli ağlara bağlanmak ve ağları değiştirmek için kılavuzlu bir deneyim de görür.

Özelliği Microsoft Endpoint Manager Yönetici merkezinden yapılandırma gibi esneklik sunmak için çeşitli yönetici denetimleri içerir. Yöneticiler, uç nokta için Defender tarafından iOS cihazlardan gönderilen verileri yapılandırmak için gizlilik denetimlerini de etkinleştirebilir. Daha fazla bilgi için [Bkz. Ağ Korumasını Yapılandırma]().

iOS için ağ koruması kiracınız için zaten etkin. Ağ koruması özelliğini test eden son kullanıcılar TestFlight aracılığıyla uygulamanın önizleme sürümünü yükleyebilir. https://aka.ms/mdeiospp iOS cihazda adresine gidin. Bu, cihazınıza TestFlight uygulamasını yüklemenizi veya zaten yüklü olması durumunda TestFlight açmanızı ister. TestFlight uygulamasında, Microsoft Defender Uç Noktasını yüklemek için ekrandaki yönergeleri izleyin. Lütfen MDE sürüm numarasının 1.1.29270104 olduğunu doğrulayın.

## <a name="integration-with-tunnel"></a>Tunnel ile tümleştirme
iOS Uç Nokta için Microsoft Defender artık tek bir uygulamada güvenliği ve bağlantıyı etkinleştirmek için vpn ağ geçidi çözümü Microsoft Tunnel ile tümleştirilebilir.  Tunnel ile tümleştirme, tek bir uygulamayla iOS daha basit ve güvenli bir VPN deneyimi sağlar. Bu özellik daha önce yalnızca Android kullanılabilirdi. Daha fazla ayrıntı için [buradaki techcommunity gönderisine bakın](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Denetimli iOS cihazlarda geliştirilmiş deneyim

iOS'da Uç Nokta için Microsoft Defender artık bu tür cihazlarda platform tarafından sağlanan artan yönetim özellikleri göz önünde bulundurulduğunda denetimli iOS/iPadOS cihazlarında özel yeteneklere sahiptir. Ayrıca **cihazda yerel BIR VPN ayarlamadan** Web Koruması sağlayabilir. Bu, son kullanıcılara kimlik avı ve diğer web tabanlı saldırılardan korunmaya devam ederken sorunsuz bir deneyim sunar. Ayrıntılar için [bu belgeleri ziyaret edin](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Uç Nokta için Microsoft Defender artık Uygulama mağazasında Microsoft Defender

Uç Nokta için Microsoft Defender artık uygulama mağazasında **Microsoft Defender** olarak kullanılabilir. Bu güncelleştirmeyle, uygulama **ABD bölgesindeki Tüketiciler** için önizleme olarak kullanıma sunulacaktır. uygulamada iş veya kişisel hesabınızla nasıl oturum açtığınıza bağlı olarak, Uç Nokta için Microsoft Defender veya kişiler için Microsoft Defender özelliklerine erişebilirsiniz. Daha fazla bilgi için [bu bloga](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) bakın.

## <a name="threat-and-vulnerability-management"></a>Tehdit ve Güvenlik Açığı Yönetimi

25 Ocak 2022'de tehdit ve güvenlik açığı yönetiminin Android ve iOS genel kullanıma sunulduğu duyuruldu. Diğer ayrıntılar için [buradaki techcommunity gönderisine](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663) bakın.

## <a name="1128250101"></a>1.1.28250101
- **Tunnel ile tümleştirme** - iOS'daki Uç Nokta için Microsoft Defender artık tek bir uygulamada güvenliği ve bağlantıyı etkinleştirmek için bir VPN ağ geçidi çözümü olan Microsoft Tunnel ile tümleştirilebilir. Daha fazla bilgi için bkz. [Microsoft Tunnel Genel Bakış](/mem/intune/protect/microsoft-tunnel-overview).
- Microsoft Endpoint Manager (Intune) aracılığıyla kaydedilen **kayıtlı iOS cihazlar için sıfır dokunmayla ekleme** genel olarak kullanılabilir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender sıfır dokunma ekleme](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- Hata düzeltmeleri.


## <a name="1124210103"></a>1.1.24210103

- Denetimli cihazlarda İnternet bağlantısı sorunları çözüldü. Daha fazla bilgi için bkz. [Kayıtlı iOS cihazlarda Uç Nokta için Defender'ı dağıtma](ios-install.md).
- Hata düzeltmeleri.

## <a name="1123250104"></a>1.1.23250104

- Performans iyileştirmeleri - Pil performansını bu sürümle test edin ve geri bildiriminizi bize bildirin.
- **Kayıtlı iOS cihazlar için sıfır dokunmayla ekleme** - Bu sürümle, Microsoft Endpoint Manager (Intune) aracılığıyla kaydedilen cihazlar için Sıfır dokunma ekleme önizlemesi eklenmiştir. Daha fazla bilgi için kurulum ve yapılandırma hakkında daha fazla bilgi için bu [belgelere](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) bakın.
- **Gizlilik Denetimleri** - Kimlik avı uyarısı raporu için gizlilik denetimlerini yapılandırın. Daha fazla bilgi için bkz[. iOS özelliklerini yapılandırma](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Hata düzeltmeleri ve performans geliştirmeleri 
  - Bu sürümde performans iyileştirmeleri yapılmıştır. Bu sürümle pil performansını test edin ve geri bildiriminizi bize bildirin.

## <a name="1120240103"></a>1.1.20240103
- Cihaz Durumu kartı - Cihaz Durumu kartı, son kullanıcılara bekleyen yazılım güncelleştirmeleri hakkında bildirimde bulunur.
- Kullanılabilirlik iyileştirmeleri - Son kullanıcılar artık Uç Nokta için Defender VPN'i Microsoft Defender uygulamasının kendisinden devre dışı bırakabilir. Bu güncelleştirmeden önce son kullanıcıların VPN'i yalnızca Ayarlar uygulamasından devre dışı bırakması gerekiyordu.
- Hata düzeltmeleri.

## <a name="1120020101"></a>1.1.20020101
- UX Geliştirmeleri - Uç Nokta için Microsoft Defender yeni bir görünüme sahiptir.
- Hata düzeltmeleri.

## <a name="1117240101"></a>1.1.17240101
- Intune aracılığıyla Mobil Uygulama Yönetimi (MAM) desteği genellikle bu sürümle sağlanır. Daha fazla bilgi için bkz[. Uygulama koruması ilkeleriniz için kullanılabilir Uç Nokta için Microsoft Defender risk sinyalleri](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Jailbreak Algılama** genel kullanıma sunulmuştur. Daha fazla bilgi için bkz. [Cihaz risk sinyallerine göre Koşullu Erişim İlkesi'ni ayarlama](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- Microsoft Endpoint Manager (Intune) aracılığıyla kayıtlı cihazlar için **VPN profilinin otomatik kurulumu** genel olarak kullanılabilir. Daha fazla bilgi için bkz. [Kayıtlı iOS cihazlar için VPN profilini otomatik ayarlama](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Hata düzeltmeleri.

## <a name="1115140101"></a>1.1.15140101

- **Jailbreak Algılama** önizleme aşamasındadır. Daha fazla bilgi için bkz. [Cihaz risk sinyallerine göre Koşullu Erişim İlkesi'ni ayarlama](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **VPN profilinin otomatik kurulumu**, Microsoft Endpoint Manager (Intune) aracılığıyla kayıtlı cihazlar için önizleme aşamasındadır. Daha fazla bilgi için bkz. [Kayıtlı iOS cihazlar için VPN profilini otomatik ayarlama](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Microsoft Defender ATP ürün adı artık uygulama mağazasında Uç Nokta için Microsoft Defender olarak güncelleştirildi.
- Geliştirilmiş oturum açma deneyimi.
- Hata düzeltmeleri.

## <a name="1115010101"></a>1.1.15010101

- Bu sürümle, iPadOS/iPad cihazları için destek duyuruyoruz.
- Hata düzeltmeleri.
