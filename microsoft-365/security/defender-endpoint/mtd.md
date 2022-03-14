---
title: Uç Nokta için Microsoft Defender - Mobil Tehdit Savunması
ms.reviewer: ''
description: Uç Nokta için Microsoft Defender'da Mobil Tehdit Savunmasına Genel Bakış
keywords: mobile, defender, Endpoint için Microsoft Defender, ios, mtd, android, security
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 07cd42d1ab1c6b945525b1e9ed4b463ee76376e1
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468942"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Uç Nokta için Microsoft Defender - Mobil Tehdit Savunması

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Android ve iOS'ta Uç Nokta için Microsoft Defender mobil tehdit savunma **çözümümizdir (MTD).** Mobil cihazlar çoğunlukla takipsiz ve korumasızken şirketler bilgisayarları güvenlik açıklarından ve saldırılardan önceden korur. Mobil platformların uygulama yalıtım ve tüketici uygulaması depoları gibi yerleşik koruması olduğu durumlarda, bu platformlar web tabanlı veya diğer gelişmiş saldırılara açık kalır. Daha fazla çalışan iş için cihazları kullansın ve hassas bilgilere erişmek için, şirketlerin cihazları ve kaynaklarınızı mobil cihazlarda giderek daha gelişmiş saldırılardan korumak için bir MTD çözümü dağıtması gerekir.

## <a name="key-capabilities"></a>Önemli özellikler

Android ve iOS'ta Uç Nokta için Microsoft Defender aşağıdaki önemli özellikleri sağlar. En son özellikler ve avantajlar hakkında bilgi almak için [duyurularımızı okuyun](https://aka.ms/mdeblog).

<br>

|Özellik|Açıklama|
|---|---|
|Web Koruması|Kimlik avı önleme, güvenli olmayan ağ bağlantılarını engelleme ve özel göstergeler için destek.|
|Kötü Amaçlı Yazılımdan Koruma (yalnızca Android)|Kötü amaçlı uygulamaları tarama.|
|Jailbreak Algılama (yalnızca iOS)|Broken cihazlar algılanması.|
|Tehdit ve Güvenlik Açığı Yönetimi (TVM) |Kullanılabilir mobil cihazlarla ilgili güvenlik açığı değerlendirmesi. Uç [Nokta için](next-gen-threat-and-vuln-mgt.md) Microsoft Defender'daki uygulama hakkında Tehdit ve Güvenlik Açığı Yönetimi fazla bilgi edinmek için bu sayfayı ziyaret edin. *Bu önizlemede iOS'ta yalnızca OS güvenlik açıklarının desteklemektedir.*|
|Birleşik uyarı|Birleşik M365 güvenlik konsolunda tüm platformlardan gelen uyarılar|
|Koşullu Erişim, Koşullu başlatma|Riskli cihazların şirket kaynaklarına erişimini engelleme. Uç nokta risk işaretleri için Defender uygulama koruma ilkelerine (MAM) da eklenebilir|
|Gizlilik Denetimleri. Önizlemede (aşağıdaki nota bakın)|Uç Nokta için Microsoft Defender tarafından gönderilen verileri denetleyerek tehdit raporlarında gizliliği yapılandırabilirsiniz. *Gizlilik denetimlerinin şu anda yalnızca kayıtlı cihazlar için kullanılabilir olduğunu unutmayın. Kaydı olmayan cihazlar için denetimler daha sonra eklenecek*|
|Microsoft Tunnel ile tümleştirme|Tek bir uygulamada Microsoft Tunnel bağlantısını etkinleştirmek için bir VPN ağ geçidi çözümü olan MICROSOFT TUNNEL ile tümleştirebilirsiniz. Şu anda yalnızca Android'de kullanılabilir|

Tüm bu özellikler Uç nokta lisans sahipleri için Microsoft Defender'da kullanılabilir. Daha fazla bilgi için Lisans [gereksinimleri'ne bakın](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Genel Bakış ve Dağıtma

Mobil cihazlarda Uç Nokta için Microsoft Defender dağıtımı Microsoft Endpoint Manager (MEM) üzerinden yapılabilir. MTD özelliklerine ve dağıtımına hızlı bir genel bakış için bu videoyu izleyin:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Dağıtma

Aşağıdaki tabloda, Android ve iOS'ta Uç Nokta için Microsoft Defender'ın nasıl dağıt olduğu özetlenmiştir. Ayrıntılı belgeler için bkz. 
- [Android'de Uç Nokta için Microsoft Defender'a Genel Bakış](microsoft-defender-endpoint-android.md) ve
- [iOS'ta Uç Nokta için Microsoft Defender'a Genel Bakış](microsoft-defender-endpoint-ios.md)

**Android**

|Kayıt türü     |Ayrıntılar      |
|--------------------|-------------|
|Intune Birleşik Enterprise ile Android Endpoint Manager (Microsoft Endpoint Manager)|[Android veya Enterprise cihazlarda dağıtma](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Intune Birleşik Cihaz Yöneticisi (Endpoint Manager) Microsoft Endpoint Manager|[Cihaz Yöneticisi tarafından kayıt yapılan cihazlarda dağıtma](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Diğer Birleşik Uç Nokta Yöneticileri / Kurulum uygulama koruma ilkesi (MAM) tarafından yönetilen YÖNETILEMEYEN BYOD VEYA cihazlar|[Uygulama koruma ilkesinde (MAM) Defender risk sinyallerini yapılandırma](android-configure-mam.md)|

**iOS**

|Kayıt türü     |Ayrıntılar      |
|--------------------|-------------|
|Intune Unified Endpoint Manager (Microsoft Endpoint Manager) ile denetlenen cihazlar|1. [iOS Store uygulaması olarak dağıtın](ios-install.md)<br/>2. [Vpn olmadan denetlemeli iOS cihazları için Web Korumasını ayarlama](ios-install.md#complete-deployment-for-supervised-devices)|
|Intune UEM (Microsoft Endpoint Manager) ile kaydolan unsupervised (BYOD) cihazlar|[iOS mağaza uygulaması olarak dağıtma](ios-install.md)|
|Diğer UEM'ler / Uygulama koruma ilkesi (MAM) tarafından yönetilen yönetilemeyen BYOD VEYA cihazlar|[Uygulama koruma ilkesinde (MAM) Defender risk sinyallerini yapılandırma](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Son kullanıcı ekleme

- [iOS](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) kayıtlı cihazlar için Sıfır dokunmatik ekleme'yi yapılandırma: Yöneticiler, sıfır dokunmalı yüklemeyi kullanıcının uygulamayı açması gerekmeden kayıtlı iOS cihazlerinde Uç Nokta için Microsoft Defender'ı sessiz olarak eklemesi için yapılandırabilir. 

- [Kullanıcı eklemesini zorunlu kılınması](android-configure.md#conditional-access-with-defender-for-endpoint-on-android) için Koşullu Erişimi yapılandırma: Bu, son kullanıcıların dağıtımdan sonra Uç Nokta için Microsoft Defender uygulamasına ekli olduğundan emin olmak için uygulanabilir. Uç nokta risk işaretleri için Defender ile koşullu erişimi yapılandırma hakkında hızlı bir tanıtım için bu videoyu izleyin. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Ekleme işlemini basitleştirin

- [iOS - Zero-Touch Onboard](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview)
- [Android Enterprise - Her zaman açık VPN kurulumu](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS - VPN profilinin otomatik kurulumu](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Pilot değerlendirme

Uç nokta için Microsoft Defender ile mobil tehdit savunmasını değerlendirirken, hizmeti daha büyük bir cihaz kümesine dağıtmaya devam etmeden önce bazı ölçütlerin karşılandığı doğrulayın. Çıkış ölçütlerini tanımlayabilir ve geniş dağıtım öncesinde memnun bırakıldıklarından emin olabilirsiniz.

Bu, hizmeti hazırlarken ortaya çıkabilecek olası sorunları azaltmaya yardımcı olur. İşte size yardımcı olacak bazı testler ve çıkış ölçütleri:

- Cihazlar, cihaz stok listesinde gösterilir: Mobil cihaza Uç Nokta için Defender'ın başarıyla ekleniyor olmasıyla, cihazın güvenlik konsolunda Cihaz Envanteri'nin içinde [listelenmiş olduğunu doğrulayın](https://security.microsoft.com).

- Android cihazda kötü amaçlı yazılım algılama testi çalıştırma: Google Play Store'dan herhangi bir test virüs uygulaması yükleyin ve uç nokta için Microsoft Defender tarafından algılandığından emin olun. İşte bu test için kullanılan örnek bir uygulama: [Virüsü test edin](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). Android cihazlarda Enterprise profili olan cihazlarda yalnızca iş profilinin destekleneyleni olduğunu unutmayın.

- Kimlik avı testi çalıştırma: Uç nokta için https://smartscreentestratings2.net Microsoft Defender tarafından engellenmiş olduğunu bulmak ve doğrulamak. Android cihazlarda Enterprise profili olan cihazlarda yalnızca iş profilinin destekleneyleni olduğunu unutmayın.

- Uyarılar panoda görünür: Algılama testlerinin üzerindeki uyarıların güvenlik konsolunda [görüntüleniyor olduğunu doğrulayın](https://security.microsoft.com).

## <a name="configure"></a>Yapılandır

- [Android özelliklerini yapılandırma](android-configure.md)
- [iOS özelliklerini yapılandırma](ios-configure-features.md)
- [VPN olmadan denetleme yapılan iOS cihazları için Web Korumasını yapılandırma](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Kaynaklar

- [Android'de Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-android.md)
- [iOS'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-ios.md)
- Duyurularımızı okuyarak yaklaşan sürümler hakkında [bilgi sahibi kalın](https://aka.ms/mdeblog).

