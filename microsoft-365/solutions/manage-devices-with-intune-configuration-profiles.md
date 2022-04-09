---
title: Adım 5. Microsoft Intune'de cihaz profillerini dağıtma
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Bu güvenlik denetimlerini buluta geçiş yapmak için Intune kullanarak cihazlarda güvenli ayarları zorunlu kılmak için yapılandırma profilleriyle Kullanmaya başlayın.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: fe137e626d5199f1709504d025411586965ae9fd
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737418"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Adım 5. Microsoft Intune'de cihaz profillerini dağıtma

Microsoft Intune, kuruluşunuzdaki farklı cihazlarda etkinleştirebileceğiniz veya devre dışı bırakabileceğiniz ayarlar ve özellikler içerir. Bu ayarlar ve özellikler "yapılandırma profillerine" eklenir. iOS/iPadOS, Android cihaz yöneticisi, Android Enterprise ve Windows gibi farklı cihazlar ve farklı platformlar için profiller oluşturabilirsiniz. Ardından, profili cihazlara uygulamak veya "atamak" için Intune kullanın.

Bu makale, yapılandırma profillerini kullanmaya başlama konusunda rehberlik sağlar. 


![Cihazları yönetme adımları](../media/devices/intune-mdm-step-4.png#lightbox)

Yapılandırma profilleri, önemli korumayı yapılandırmanızı ve cihazları kaynaklarınıza erişebilmeleri için uyumlu hale getirmenizi sağlar. Daha önce, bu tür yapılandırma değişiklikleri Active Directory Domain Services grup ilkesi ayarları kullanılarak yapılandırıldı. Modern bir güvenlik stratejisi, güvenlik denetimlerini bu denetimlerin uygulanması şirket içi kaynaklara ve erişime bağımlı olmayan buluta taşımayı içerir. Intune yapılandırma profilleri, bu güvenlik denetimlerini buluta aktarmanın yoludur. 

Oluşturabileceğiniz yapılandırma profilleri hakkında fikir vermek için bkz. [Microsoft Intune'de cihaz profillerini kullanarak cihazlarınıza özellik ve ayar uygulama](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Intune için Windows güvenlik temellerini dağıtma

Başlangıç noktası olarak, cihaz yapılandırmalarınızı Microsoft güvenlik temelleriyle hizalamak istiyorsanız, Microsoft Endpoint Manager içindeki güvenlik temellerini öneririz. Bu yaklaşımın avantajı, Windows 10 ve 11 özellik yayımlandıkçe temelleri güncel tutmak için Microsoft'a güvenebilmenizdir. 

Windows 10 ve Windows 11 için kullanılabilen Intune Windows güvenlik temellerini dağıtmak için. Kullanılabilir taban çizgileri hakkında bilgi edinmek için bkz. [Intune'da Windows cihazları yapılandırmak için güvenlik](/mem/intune/protect/security-baselines) temellerini kullanma.

Şimdilik en uygun MDM güvenlik temelini dağıtmanız gerekir. Profili oluşturmak ve temel sürümü seçmek için [bkz. Microsoft Intune güvenlik temeli profillerini yönetme](/mem/intune/protect/security-baselines-configure).

Daha sonra Uç Nokta için Microsoft Defender ayarlandığında ve Intune bağladığınızda Uç Nokta için Defender temellerini dağıtın. Bu konu başlığı, bu serinin sonraki makalesinde ele alınmıştır: [6. Adım. Cihaz riskini ve güvenlik temellerine uyumluluğunu izleyin](manage-devices-with-intune-monitor-risk.md).

Bu güvenlik temellerinin CIS veya NIST uyumlu olmadığını ancak önerilerini yakından yansıttığını anlamak önemlidir. Daha fazla bilgi için bkz. [Intune güvenlik temelleri CIS veya NIST uyumlu mu?](https://docs.microsoft.com/mem/intune/protect/security-baselines#are-the-intune-security-baselines-cis-or-nist-compliant)

## <a name="customize-configuration-profiles-for-your-organization"></a>Kuruluşunuz için yapılandırma profillerini özelleştirme

Önceden yapılandırılmış temelleri dağıtmaya ek olarak, birçok kurumsal ölçekli kuruluş daha ayrıntılı denetim için yapılandırma profilleri uygular. Bu yapılandırma, şirket içi Active Directory ortamındaki grup ilkesi Nesnelerine bağımlılığı azaltmaya ve güvenlik denetimlerini buluta taşımaya yardımcı olur. 

Yapılandırma profillerini kullanarak yapılandırabileceğiniz birçok ayar aşağıda gösterildiği gibi dört kategoride gruplandırılabilir.

![cihaz profili kategorilerini Intune](../media/devices/intune-device-profile-categories.png#lightbox)

Aşağıdaki tabloda çizim açıklanmaktadır.


|Kategori |Açıklama |Örnekler  |
|---------|---------|---------|
|Cihaz özellikleri     | Cihazdaki özellikleri denetler. Bu kategori yalnızca iOS/iPadOS ve macOS cihazları için geçerlidir.        | Airprint, bildirimler, kilit ekranı iletileri        |
|Cihaz kısıtlamaları     | Cihazlarda güvenliği, donanımı, veri paylaşımını ve daha fazla ayarı denetler        | PIN gerektirme, veri şifrelemesi        |
|Erişim yapılandırması     |  Bir cihazı kuruluşunuzun kaynaklarına erişecek şekilde yapılandırıyor        | E-posta profilleri, VPN profilleri, Wi-Fi ayarları, sertifikaları        |
|Özel     | Özel yapılandırma ayarlama veya özel yapılandırma eylemlerini yürütme       | OEM ayarlarını yapın, PowerShell betiklerini yürütün        |
|    |         |         |

Kuruluşunuz için yapılandırma profillerini özelleştirirken aşağıdaki kılavuzu kullanın:
- İlkelerin genel sayısını küçük tutarak güvenlik idaresi stratejinizi basitleştirin.
- Ayarları yukarıda listelenen kategorilere veya kuruluşunuz için anlamlı kategorilere gruplandırın.
- Güvenlik denetimlerini grup ilkesi Nesnelerinden (GPO) Intune yapılandırma profillerine taşırken, her GPO tarafından yapılandırılan ayarların hala uygun olup olmadığını ve genel bulut güvenlik stratejinize katkıda bulunmak için gerekli olup olmadığını göz önünde bulundurun. Koşullu erişim ve Intune dahil olmak üzere bulut hizmetleri genelinde yapılandırılabilir birçok ilke, özel GPO'ların ilk tasarlandığı şirket içi ortamda yapılandırılabilenden daha gelişmiş bir koruma sağlar.
- Geçerli GPO ayarlarınızı Microsoft Endpoint Manager içindeki özelliklerle karşılaştırmak ve eşlemek için grup ilkesi Analytics'i kullanın. Bkz. [Microsoft Endpoint Manager'da grup ilkesi analizi kullanarak şirket içi grup ilkesi nesnelerinizi (GPO) analiz](/mem/intune/configuration/group-policy-analytics) etme.
- Özel yapılandırma profillerini kullanırken buradaki yönergeleri kullandığınızdan emin olun: [Intune'de özel ayarlarla bir profil oluşturun](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Ek kaynaklar

Cihaz profilleriyle nereden başlayacağınızı emin değilseniz, aşağıdakiler yardımcı olabilir:

- [Kılavuzlu senaryolar](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Güvenlik temelleri](/mem/intune/protect/security-baselines)

Ortamınız şirket içi GPO'lar içeriyorsa, aşağıdaki özellikler buluta iyi bir geçiştir:

- [grup ilkesi analizi](/mem/intune/configuration/group-policy-analytics)
- [Yönetici şablonları (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Ayarlar Kataloğu](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Sonraki adımlar
[6. Adım'a gidin. Cihaz riskini ve güvenlik temellerine uyumluluğunu izleyin](manage-devices-with-intune-monitor-risk.md).
