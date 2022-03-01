---
title: 6. Adım. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu izleme
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Microsoft Intune için Defender'a bağlanmayı ve erişim koşulu olarak cihaz riskini izlemeyi öğrenin.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f58611f555b022b69211e39f149effef925dde17
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016276"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>6. Adım. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu izleme

Organizasyonunız Uç Nokta için Microsoft Defender'ı dağıttıktan sonra, uç nokta için Defender ile tümleştirme ile Microsoft Intune daha iyi içgörüler ve koruma elde edin. Mobil cihazlarda bu, erişim koşulu olarak cihaz riskini izleme olanağını da içerir. Diğer Windows için, güvenlik taban çizgilerine bu cihazların uyumluluğunu izleyebilirsiniz. 

![Uç nokta ve Microsoft Intune için Defender tümleştirmesi resmi](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

Bu şekilde:
- Uç Nokta için Microsoft Defender, cihazlar için tehdit korumasının gelişmiş yaklaşımını büyük ölçüde artırır. 
- Microsoft Intune, Uygulama Koruma İlkelerini ayarlamanıza ve cihazları yönetmenize olanak tanırken (yapılandırma değişiklikleri dahil), Uç Nokta için Defender sürekli tehditlere karşı cihazlarınızı izler ve saldırılarınızı düzeltmek için otomatik eylem gerçekleştirebilirsiniz. 
- Intune'ı uç nokta için Defender'a cihaz ekleme için kullanabilirsiniz. Bunu yapmak için ayrıca bu cihazların Uç nokta uç nokta veri kaybı önleme (Uç nokta DLP) Microsoft 365 etkinleştirmesini sağlarsınız.

Bu makale şu adımları içerir:
- Bağlan Microsoft Intune için Defender'a
- Cihaz riskini izleme
- Güvenlik taban çizgilerine uyumluluğu izleme

Uç Nokta için Defender henüz ayar yaramadısa değerlendirme ve pilot ortamını ayarlamak [için tehdit koruması yöneticinizle birlikte çalışabilirsiniz](../security/defender/eval-defender-endpoint-overview.md). Bu makaledeki özellikleri denemek için pilot grupla birlikte çalışabilirsiniz.

## <a name="connect-microsoft-intune-to-defender-for-endpoint"></a>Bağlan Microsoft Intune için Defender'a

Uç nokta için Defender ile Microsoft Intune tümleştirmesini yapılandırmak basittir. Bu makaleyi kullanın: [Intune'da Uç Nokta için Microsoft Defender'ı Yapılandırma](/mem/intune/protect/advanced-threat-protection-configure). 

![Bağlan için Microsoft Defender'a Intune](../media/devices/connect-intune-to-microsoft-defender.png#lightbox)

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Cihaz riskini erişim koşulu olarak izleme

Uç nokta için Microsoft Defender dağıtılmış olarak tehdit risk sinyallerinden yararlanılabilir. Bu sayede cihaza erişimi risk puanına göre engelleyebilirsiniz. Microsoft, risk puanı orta veya daha düşük olan cihazlara erişim izni vermenizi önermektedir.

Android ve iOS/iPadOS için tehdit işaretleri Uygulama Koruma İlkeleri'niz (APP) içinde kullanılabilir. Bunu yapılandırma hakkında bilgi için bkz. [Cihaz risk düzeyini ayarlamak için uygulama koruma ilkesi oluşturma ve atama](/mem/intune/protect/advanced-threat-protection-configure).

Tüm platformlar için, var olan cihaz uyumluluk ilkelerde risk düzeyini değiştirebilirsiniz. Cihaz [risk düzeyini ayarlamak için bkz. Uyumluluk ilkesi oluşturma ve atama](/mem/intune/protect/advanced-threat-protection-configure).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Güvenlik taban çizgilerini dağıtma ve bu ayarlara uyumluluğu izleme

11 Windows 10, Windows için geçerlidir

[5. Adım makalesi. Yapılandırma profillerini dağıtın](manage-devices-with-intune-configuration-profiles.md), Windows 10 11'de kullanılabilen güvenlik taban çizgilerini kullanarak yapılandırma profilleriyle çalışmaya Windows 10 başlamayı Windows. Uç Nokta için Microsoft Defender ayrıca, uç nokta (uç nokta) ayarları dahil olmak üzere Uç nokta için Defender yığınında tüm güvenlik denetimlerini en iyi duruma uç noktada algılama ve yanıtlama güvenlik EDR. Bunlar, E-posta Microsoft Intune.

İdeal olarak, Uç nokta için Defender'a ekli cihazlar, başlangıçta Windows'in güvenliğini sağlamak için Windows Intune güvenlik temeli ve Uç nokta güvenlik denetimleri için Defender'ı en iyi şekilde yapılandırmak üzere en üstteki Uç nokta güvenlik temeli için Defender.) dağıtılır.

Riskler ve tehditlerle ilgili en son verilerden faydalanmek ve taban çizgisi geliştikçe çakışmaları en aza indirmek için, piyasaya çıktıları yayımlanan tüm ürünlerde taban çizgilerinin en son sürümlerini her zaman kullanın. 

Uç Nokta için Defender'ı kullanarak bu taban çizgilerine uyumluluğu izleyebilirsiniz. 

![Güvenlik taban çizgilerine uyumluluğu izleme kartı](../media/devices/secconmgmt-baseline-card.png#lightbox)

Güvenlik taban çizgilerini dağıtmak ve bu ayarlara uyumluluğu izlemek için bu tablodaki adımları kullanın.


|Adım  |Açıklama  |
|---------|---------|
|1     |Önemli kavramları gözden geçirin ve Uç Nokta için Microsoft Defender ile Intune güvenlik Windows karşılaştırarak. <br><br>Önerileri [öğrenmek için bkz. Uç nokta güvenlik temeli için Microsoft Defender](../security/defender-endpoint/configure-machines-security-baseline.md) uyumluluğu artırma.<br><br>[Intune'da kullanılabilir güvenlik Windows ](/mem/intune/protect/security-baselines) için güvenlik taban çizgilerini kullanarak yapılandırma ve çakışmaları önleme.         |
|2     |  Intune Windows güvenlik temeli ayarlarını dağıtın. 5. Adım'daki rehbere udıysanız bunu [zaten tamammış olabilir. Yapılandırma profillerini dağıtın](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Intune için Uç Nokta taban çizgisi ayarları için Defender'ı dağıtın. Profili [oluşturmak ve taban çizgisi sürümünü Microsoft Intune](/mem/intune/protect/security-baselines-configure) için bkz. Temel güvenlik taban çizgisi profillerini yönetme.<br><br>Buradaki yönergeleri de takip edin: Uç [nokta güvenlik temeli için Microsoft Defender'ı gözden geçirme ve atama](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | Uç Nokta için Defender'da cihaz yapılandırma [yönetimiyle ilgili güvenlik taban çizgisi kartını gözden geçirin](../security/defender-endpoint/configure-machines.md).          |
| | |

## <a name="next-steps"></a>Sonraki adımlar
[7. Adım'a gidin. Uç noktalara bilgi koruma özellikleriyle DLP uygulama](manage-devices-with-intune-dlp-mip.md).