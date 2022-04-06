---
title: Uç Nokta için Microsoft Defender hizmetine ekleme
description: Uç Nokta için Microsoft Defender hizmetine uç noktaların nasıl Uç Nokta için Microsoft Defender öğrenin
keywords: uç nokta için microsoft defender, ekleme, dağıtma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 387598581ec52de2089bee2a98a15dcc60a54bd9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471703"
---
# <a name="onboard-to-the-microsoft-defender-for-endpoint-service"></a>Uç Nokta için Microsoft Defender hizmetine ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Posta e-postalarını dağıtmanın çeşitli Uç Nokta için Microsoft Defender ve çözüm içindeki yeteneklerin nasıl yapılandırıldığından emin olur.


Uç Nokta için Defender'ı dağıtmak için şu adımları uygulayın:

- 1. Adım: Hizmete uç noktaları ekleme
- 2. Adım: Özellikleri yapılandırma

:::image type="content" source="images/deployment-steps.png" alt-text="Dağıtım adımları" lightbox="images/deployment-steps.png":::




## <a name="step-1-onboard-endpoints-using-any-of-the-supported-management-tools"></a>1. Adım: Desteklenen yönetim araçlardan herhangi birini kullanarak uç noktaları ekleme

Dağıtım [planlama başlığında](deployment-strategy.md) , Uç Nokta için Defender'ı dağıtmak için ihtiyacınız olan genel adımlar özetlanmıştır.

Ekleme sürecine hızlı bir genel bakış için bu videoyu izleyin ve kullanılabilir araçlar ve yöntemler hakkında bilgi edinin.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Mimarinizi tanımdikten sonra, hangi dağıtım yönteminin kullanmaya karar vermeniz gerekir. Seçtiğiniz dağıtım aracı, uç noktaları hizmete nasıl eklemenizi etkiler.

### <a name="onboarding-tool-options"></a>Ekleme aracı seçenekleri

Aşağıdaki tabloda, ekleme için gereken uç nokta temel alarak kullanılabilir araçlar listeledir.

| Uç nokta     | Araç seçenekleri                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br> [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](azure-server-integration.md) |
| **macOS**    | [Yerel betikler](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Operasyon](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 


## <a name="step-2-configure-capabilities"></a>2. Adım: Özellikleri yapılandırma
Uç noktaları işe başladıktan sonra, özellikleri yapılandırmış oluruz. Aşağıdaki tabloda yapılandırabilirsiniz bileşenler listelemektedir. Kullanmak istediğiniz bileşenleri seçin ve uygun olanları kaldırın.

| Özellik | Açıklama |
|-|-|
| [Uç Nokta & Yanıtı (EDR)](overview-endpoint-detection-response.md) | Uç nokta ve uç noktada algılama ve yanıtlama için Defender, gerçek zamanlı olarak yakın olan ve işlemlebilir gelişmiş saldırı algılamaları sağlar. Güvenlik analistleri uyarıları etkili bir şekilde önceliklendirmek, ihlallerin tam kapsamı için görünürlük kazanmak ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirmektedir. |
| [Tehdit & Güvenlik Açığı Yönetimi (TVM)](next-gen-threat-and-vuln-mgt.md) | Tehdit & Güvenlik Açığı Yönetimi, Uç Nokta için Microsoft Defender'in bir bileşenidir ve şu özellikleriyle birlikte hem güvenlik yöneticilerine hem de güvenlik işlemleri ekiplerine benzersiz bir değer sağlar: - Gerçek zamanlı güvenlik uç noktada algılama ve yanıtlama (EDR ) uç nokta güvenlik açıkları ile ilişkili öngörüler - Olay soruşturmaları sırasında paha biçilemez cihaz güvenlik açığı bağlamı - Microsoft Intune ve Microsoft güvenlik açıkları aracılığıyla yerleşik düzeltme System Center Configuration Manager.  |
| [Yeni nesil koruma (NGP)](microsoft-defender-antivirus-windows.md) | Microsoft Defender Virüsten Koruma, masaüstü bilgisayarlar, taşınabilir bilgisayarlar ve sunucular için yeni nesil koruma sağlayan yerleşik bir kötü amaçlı yazılımdan koruma çözümüdür. Microsoft Defender Virüsten Koruma şunları içerir:<br> <br>-Yeni ve ortaya çıkan tehditlerin neredeyse anında algılanması ve engellenmesi için bulut teslimi koruması. Makine öğrenimi ve Akıllı Güvenlik Graph ile bulut teslimi koruma, öğrenme ve korumanın desteklendiği yeni nesil teknolojilerin Microsoft Defender Virüsten Koruma.<br> <br> - Gelişmiş dosya ve süreç davranışı izleme ve diğer heuristleri kullanarak ("gerçek zamanlı koruma" olarak da bilinir) taramada her zaman açık.<br><br> - Makine öğrenimi, insan ve otomatik büyük veri çözümlemelerine ve derinlemesine tehdit direnci araştırmalarına dayalı özel koruma güncelleştirmeleri. |
| [Saldırı Yüzeyini Azaltma (ASR)](overview-attack-surface-reduction.md) | Saldırı yüzeyini azaltma özellikleri, Uç Nokta için Microsoft Defender ve ortaya çıkan tehditlere karşı kuruluşta cihaz ve uygulamaların korunmasına yardımcı olur. |
| [Düzeltme & (AIR) Otomatik İnceleme](automated-investigations.md) | Uç Nokta için Microsoft Defender araştırma, tek tek araştırılması gereken uyarı sayısını önemli ölçüde azaltmak için Otomatik soruşturmalar'ın kullanır. Otomatik araştırma özelliği, çeşitli denetim algoritmalarını ve analistlerin (playbooks gibi) uyarıları incelemek ve ihlalleri çözmek için hemen düzeltme işlemleri yapmak için kullandığı süreçlerden faydalanr. Bu durum uyarı hacmini önemli ölçüde azaltarak güvenlik işlem uzmanlarının daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak verir. |
| [Microsoft Tehdit Uzmanları (MTE)](microsoft-threat-experts.md) | Microsoft Tehdit Uzmanları, benzersiz ortamlarındaki kritik tehditlerin atlamaması için uzman düzeyinde izleme ve çözümleme özelliklerine sahip Güvenlik İşlem Merkezleri (SOC) sağlayan, yönetilen bir arama hizmetidir.      |

Uç noktaları işe başladıktan sonra koruma, yeni nesil koruma ve saldırı yüzeyini azaltma uç noktada algılama ve yanıtlama çeşitli özellikleri yapılandırmış oluruz.

## <a name="example-deployments"></a>Örnek dağıtımlar

Bu dağıtım kılavuzunda, uç noktaları eklemeye ve özellikleri yapılandırmaya yardımcı olmak için iki dağıtım aracı kullanmada size yol sunaruz.

Örnek dağıtımlarda kullanılan araçlar:

- [Microsoft Endpoint Configuration Manager kullanarak işe Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Microsoft Endpoint Manager kullanarak işe Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

Yukarıda belirtilen dağıtım araçlarını kullanarak, uç nokta özellikleri için aşağıdaki Defender'ı yapılandırma kılavuzuna sahip oluruz:

- Uç nokta algılama ve yanıt yapılandırması
- Yeni nesil koruma yapılandırması
- Saldırı yüzeyini azaltma yapılandırması

## <a name="related-topics"></a>İlgili konular

- [Microsoft Endpoint Configuration Manager kullanarak işe Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Microsoft Endpoint Manager kullanarak işe Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
- [Microsoft 365 E5 aboneliğinde Güvenli Belgeler](../office-365-security/safe-docs.md)
