---
title: Adım 5. Mobil cihazda cihaz profillerini Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Intune'un kullanarak cihazlarda güvenli ayarları zorunlu karak bu güvenlik denetimlerini buluta geçişi için yapılandırma profillerini kullanmaya başlama.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: d44d70c50db5c086e24af575677d5d51e1b33357
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016284"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Adım 5. Mobil cihazda cihaz profillerini Microsoft Intune

Microsoft Intune ayarları ve özellikleri dahil edin. Bu ayarlar, kurum içindeki farklı cihazlarda etkinleştirebilirsiniz veya devre dışı bırakabilirsiniz. Bu ayarlar ve özellikler "yapılandırma profilleri" için eklenir. iOS/iPadOS, Android cihaz yöneticisi, Android Enterprise ve diğer platformlar dahil olmak üzere farklı cihazlar ve farklı platformlar için profil Windows. Ardından, Intune'ı kullanarak profili cihazlara uygulayabilir veya "atabilirsiniz".

Bu makale, yapılandırma profillerine başlama konusunda yol gösterir. 


![Cihazları yönetme adımları](../media/devices/intune-mdm-step-4.png#lightbox)

Yapılandırma profilleri önemli korumayı yapılandırmanıza ve kaynaklarınıza erişebilmeleri için cihazları uyumlu bir şekilde getirmenize izin verir. Daha önce, bu tür yapılandırma değişiklikleri Active Directory Etki Alanı Hizmetleri'nin Grup İlkesi ayarları kullanılarak yapılandırıldı. Modern bir güvenlik stratejisi, bu denetimlerin zorlaması şirket içi kaynaklara ve erişime bağımlı olmayan güvenlik denetimlerini buluta taşımayı içerir. Intune yapılandırma profilleri, bu güvenlik denetimlerini buluta geçişin yoludır. 

Oluşturabilecek yapılandırma profilleri hakkında size fikir vermek için bkz. Cihaz profillerini kullanarak cihazlarınıza özellik ve [Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Intune Windows için güvenlik taban çizgilerini dağıtma

Başlangıç noktası olarak, cihaz yapılandırmalarınızı Microsoft güvenlik taban çizgilerine hizalamak için bu yapılandırmalar içindeki güvenlik taban çizgilerini Microsoft Endpoint Manager. Bu yaklaşımın avantajı, temelleri güncel tutmak için Microsoft'a güvenerek Windows 10 11 özellik yayınlanır. 

Intune'Windows için güvenlik taban çizgilerini dağıtmak için, Windows 10 ve Windows 11'de kullanılabilir. [Intune'da kullanılabilir taban Windows için güvenlik taban](/mem/intune/protect/security-baselines) çizgilerini kullanma.

Şimdilik, en uygun MDM güvenlik temellerini dağıtmanız gerekir. Profili [oluşturmak ve taban çizgisi sürümünü Microsoft Intune ](/mem/intune/protect/security-baselines-configure)için bkz. Temel güvenlik taban çizgisi profillerini yönetme.

Daha sonra, Uç Nokta için Microsoft Defender ayarlanır ve Intune'a bağlandıktan sonra, Uç nokta taban çizgisi için Defender'ı dağıtın. Bu konu, bu serinin bir sonraki makalesinde eledir: [6. Adım. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu takip edin](manage-devices-with-intune-monitor-risk.md).

Bu güvenlik taban çizgilerinin CIS veya NIST uyumlu olmadığını anlamak, ancak onların önerilerini yakından yansıtmak önemlidir. Daha fazla bilgi için bkz [. Intune güvenlik taban çizgisi CIS veya NIST uyumlu mu](/mem/intune/protect/security-baselines)?

## <a name="customize-configuration-profiles-for-your-organization"></a>Yapılandırma profillerini özelleştirin

Önceden yapılandırılmış taban çizgilerinin dağıtımına ek olarak, kurumsal ölçekteki birçok kuruluş daha ayrıntılı denetim için yapılandırma profilleri kullanır. Bu yapılandırma, şirket içi Active Directory ortamında Grup İlkesi Nesneleri'ne bağımlılığı azaltmaya ve güvenlik denetimlerini buluta taşımaya yardımcı olur. 

Aşağıda gösterildiği gibi, yapılandırma profillerini kullanarak yapılandırabilirsiniz birçok ayar dört kategoride gruplandırabilir.

![Intune cihaz profili kategorileri](../media/devices/intune-device-profile-categories.png#lightbox)

Aşağıdaki tabloda çizim açık gösterilmiştir.


|Kategori |Açıklama |Örnekler  |
|---------|---------|---------|
|Cihaz özellikleri     | Cihaz özelliklerini kontrol eder. Bu kategori yalnızca iOS/iPadOS ve macOS cihazları için geçerlidir.        | Airprint, bildirimler, kilit ekranı iletileri        |
|Cihaz kısıtlamaları     | Cihazlarda güvenliği, donanımı, veri paylaşımını ve daha fazla ayarı kontrol eder        | PIN ve veri şifrelemesi gerektirme        |
|Erişim yapılandırması     |  Bir cihazı, kuruluş kaynaklarınıza eriş eriş bilgilerine erişmek üzere yapılandıran        | E-posta profilleri, VPN profilleri, Wi-Fi ayarları, sertifikalar        |
|Özel     | Özel yapılandırma ayarlama veya özel yapılandırma eylemlerini yürütme       | OEM ayarlarını ayarlama, PowerShell betiklerini yürütme        |
|    |         |         |

Kuruluşun yapılandırma profillerini özelleştirerek, aşağıdaki kılavuzu kullanın:
- İlkelerin toplam sayısını az tutarak güvenlik yönetim stratejinizi basitleştirin.
- Ayarları yukarıda listelenen kategoriler veya organizasyonunız için anlamlı olan kategoriler olarak gruplandırabilirsiniz.
- Güvenlik denetimlerini Grup İlkesi Nesneleri'den (GPO) Intune yapılandırma profillerine taşımaya devam ederken, her GPO tarafından yapılandırılan ayarların hala ilgili ve genel bulut güvenlik stratejinize katkıda bulunmak için gerekli olup olmadığını düşünün. Koşullu erişim ve Intune da dahil olmak üzere bulut hizmetleri genelinde yapılandırılan birçok ilke, başlangıçta özel GPOS'ların tasar bulunduğu şirket içi ortamda yapılandırılana kadar daha gelişmiş koruma sağlar.
- Geçerli GPO ayarlarınızı kendi uygulama ayarları içindeki özelliklerle karşılaştırmak ve eşlemek için Grup İlkesi Microsoft Endpoint Manager. Bkz[. Grup İlkesi çözümlemelerini kullanarak şirket içi grup ilkesi nesnelerinizi (GPO) çözümleme](/mem/intune/configuration/group-policy-analytics) Microsoft Endpoint Manager.
- Özel yapılandırma profillerini kullanırken buradaki kılavuzu kullanmayı tercih edin: [Intune'da özel ayarlarla profil oluşturun](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Ek kaynaklar

Cihaz profilleriyle nereden başlayacağınıza emin değilsanız, aşağıdakiler yardımcı olabilir:

- [Rehberli senaryolar](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Güvenlik taban çizgilerini](/mem/intune/protect/security-baselines)

Ortamınız okul öncesi GPOS'lar da dahilse, aşağıdaki özellikler buluta iyi bir geçiş sağlar:

- [Grup İlkesi analizi](/mem/intune/configuration/group-policy-analytics)
- [Yönetici şablonları (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Ayarlar Kataloğu](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Sonraki adımlar
[6. Adım'a gidin. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu takip edin](manage-devices-with-intune-monitor-risk.md).
