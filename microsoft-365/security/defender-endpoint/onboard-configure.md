---
title: Cihazları ekleme ve cihaz Uç Nokta için Microsoft Defender yapılandırma
description: Diğer Windows 10, sunucu, cihaz Windows cihaz kullanın ve bir algılama testi çalıştırmayı öğrenin.
keywords: ekleme, Uç Nokta için Microsoft Defender ekleme, sccm, grup ilkesi, mdm, yerel betik, algılama testi
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 350f5675d1426c354f1e2ac848d3a9d14f1ecc76
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469679"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Cihazları ekleme ve cihaz Uç Nokta için Microsoft Defender yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Dağıtım Uç Nokta için Microsoft Defender iki adımlı bir işlemdir.

- Cihazları hizmete ekleme
- Hizmetin özelliklerini yapılandırma

:::image type="content" source="images/deployment-steps.png" alt-text="Ekleme ve yapılandırma işlemi" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>Cihazları hizmete ekleme
Desteklenen cihazlardan herhangi birini eklemesi için Uç Nokta için Defender portalının ekleme bölümüne gitebilirsiniz. Cihaza bağlı olarak, cihaza uygun olan uygun adımlarla, sağlanan yönetim ve dağıtım aracı seçenekleriyle yol gösterirsiniz. 

Genel olarak, cihazları hizmete onboard için:

- Cihazın en düşük gereksinimleri karşı çalıştığını [doğrulama](minimum-requirements.md)
- Cihaza bağlı olarak, Uç nokta için Defender portalının ekleme bölümünde sağlanan yapılandırma adımlarını izleyin
- Cihazlarınız için uygun yönetim aracını ve dağıtım yöntemini kullanma
- Cihazların düzgün şekilde yerleşik olduğunu doğrulamak ve hizmete rapor etmek için bir algılama testi çalıştırın



## <a name="onboarding-and-configuration-tool-options"></a>Ekleme ve yapılandırma aracı seçenekleri
Aşağıdaki tabloda, ekleme için gereken uç nokta temel alarak kullanılabilir araçlar listeledir.

| Uç nokta     | Araç seçenekleri                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Yerel betikler](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Operasyon](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)               |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


Aşağıdaki tabloda, ekleme için gereken uç nokta temel alarak kullanılabilir araçlar listeledir.

## <a name="configure-capabilities-of-the-service"></a>Hizmetin özelliklerini yapılandırma
Ekleme cihazları, Uç nokta için Micorosft Defender uç noktada algılama ve yanıtlama nın uygulama olanağını etkin bir şekilde sağlar.

Cihazları işe başladıktan sonra hizmetin diğer özelliklerini yapılandırmanız gerekir. Aşağıdaki tabloda, ortamınıza en uygun korumayı elde etmek için yapılandırabilirsiniz özellikler listelemektedir.

| Özellik | Açıklama |
|-|-|
| [Tehdit Güvenlik & Yönetimi'yi (TVM) yapılandırma](tvm-prerequisites.md) | Tehdit & Güvenlik Açığı Yönetimi aşağıdakiler dahil olmak üzere Uç Nokta için Microsoft Defender ve güvenlik yöneticileriyle güvenlik işlemleri ekiplerine benzersiz bir değer sağlar: <br><br> - Uç nokta açıkları ile uç noktada algılama ve yanıtlama (EDR) öngörüler. <br><br> - Olay soruşturmaları sırasında paha biçilemez cihaz güvenlik açığı bağlamı. <br><br> - Microsoft Intune ve Microsoft System Center Configuration Manager aracılığıyla yerleşik düzeltme işlemleri.  |
| [Yeni nesil korumayı (NGP) yapılandırma](configure-microsoft-defender-antivirus-features.md) | Microsoft Defender Virüsten Koruma, masaüstü bilgisayarlar, taşınabilir bilgisayarlar ve sunucular için yeni nesil koruma sağlayan yerleşik bir kötü amaçlı yazılımdan koruma çözümüdür. Microsoft Defender Virüsten Koruma şunları içerir:<br> <br>-Yeni ve ortaya çıkan tehditlerin neredeyse anında algılanması ve engellenmesi için bulut teslimi koruması. Makine öğrenimi ve Akıllı Güvenlik Graph ile bulut teslimi koruma, öğrenme ve korumanın desteklendiği yeni nesil teknolojilerin Microsoft Defender Virüsten Koruma.<br> <br> - Gelişmiş dosya ve süreç davranışı izleme ve diğer heuristleri kullanarak ("gerçek zamanlı koruma" olarak da bilinir) taramada her zaman açık.<br><br> - Makine öğrenimi, insan ve otomatik büyük veri çözümlemelerine ve derinlemesine tehdit direnci araştırmalarına dayalı özel koruma güncelleştirmeleri. |
| [Saldırı yüzeyini azaltmayı (ASR) yapılandırma](overview-attack-surface-reduction.md) | Saldırı yüzeyini azaltma özellikleri, Uç Nokta için Microsoft Defender ve ortaya çıkan tehditlere karşı kuruluşta cihaz ve uygulamaların korunmasına yardımcı olur. |
| [Düzeltme (AIR) & Özellikleri için Otomatik Araştırma'ya yapılandırma](configure-automated-investigations-remediation.md) | Uç Nokta için Microsoft Defender araştırma, tek tek araştırılması gereken uyarı sayısını önemli ölçüde azaltmak için Otomatik soruşturmalar'ın kullanır. Otomatik araştırma özelliği, çeşitli denetim algoritmalarını ve analistlerin (playbooks gibi) uyarıları incelemek ve ihlalleri çözmek için hemen düzeltme işlemleri yapmak için kullandığı süreçlerden faydalanr. Bu durum uyarı hacmini önemli ölçüde azaltarak güvenlik işlem uzmanlarının daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak verir. |
| [Veri Microsoft Tehdit Uzmanları (MTE) özelliklerini yapılandırma](configure-microsoft-threat-experts.md) | Microsoft Tehdit Uzmanları, benzersiz ortamlarındaki kritik tehditlerin atlamaması için uzman düzeyinde izleme ve çözümleme özelliklerine sahip Güvenlik İşlem Merkezleri (SOC) sağlayan, yönetilen bir arama hizmetidir.      |


## <a name="supported-capabilities-for-windows-devices"></a>Yeni cihazlar için Windows özellikleri

|İşletim Sistemi  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |<sup>Windows Server 2016[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Engelleme**    |         |         |         |         |         |
|Saldırı Yüzeyini Azaltma kuralları     |    E     |   E      |    E     |    E     |    E     |
|Cihaz Denetimi     |     E    |    N     |    N     |    N     |    N     |  
|Güvenlik Duvarı     |      E   |    E     |     E    |    E    |    E   |
|Ağ Koruması     |      E   |    E     |     E    |    E    |    E   |
|Yeni nesil koruma     |      E   |    E     |     E    |    E    |    E   |
|Tamper Protection     |        E   |    E     |     E    |    E    |    E   |
|Web Koruması     |       E   |    E     |     E    |    E    |    E   |
|||||||
|**Algılama**     |         |         |         |||
|Gelişmiş Av     |      E   |    E     |     E    |    E    |    E   |
|Özel dosya göstergeleri     |      E   |    E     |     E    |    E    |    E   |
|Özel ağ göstergeleri     |      E   |    E     |     E    |    E    |    E   |
|EDR Blok & Pasif Modu     |      E   |    E     |     E    |    E    |    E   |
|Algı algılama algılayıcısı     |      E   |    E     |     E    |    E    |    E   |
|Ağ & bulma uç noktası     |      E   |    N     |     N    |    N    |    N   |
|||||||
|**Yanıt**     |         |         |         |||
|Yanıt için & Araştırma (AIR)    |      E   |    E     |     E    |    E    |    E   |
|Cihaz yanıtı özellikleri: yalıtım, araştırma paketi toplama, AV taraması çalıştırma     |      E   |    E     |     E    |    E    |    E   |
|Dosya yanıtı özellikleri: dosya toplama, derin çözümleme, dosyayı engelleme, durdurma ve karantina işlemleri     |      E   |    E     |     E    |    E    |    E   |
|Canlı Yanıt    |      E   |    E     |     E    |    E    |    E   |

(<a id="fn1">1</a>) R2 ve 2016'da Windows Server 2012, birleşik çözümü ifade eder. Daha fazla bilgi için bkz. [Uç nokta Windows Defender'a Sunucu Ekleme](configure-server-endpoints.md).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 EDR algılayıcısı ve System Center Endpoint Protection (SCEP) kullanan AV için destek içerir.
