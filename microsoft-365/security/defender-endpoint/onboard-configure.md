---
title: Cihazları ekleyin ve Uç Nokta için Microsoft Defender işlevlerini yapılandırın
description: Windows 10 cihazları, sunucuları, Windows dışı cihazları ekleme ve algılama testi çalıştırmayı öğrenin.
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
ms.openlocfilehash: d218e09c8cc300552bcc9f230c1d375d33a5feb6
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530564"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Cihazları ekleyin ve Uç Nokta için Microsoft Defender işlevlerini yapılandırın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Uç Nokta için Microsoft Defender dağıtmak iki adımlı bir işlemdir.

- Cihazları hizmete ekleme
- Hizmetin özelliklerini yapılandırma

:::image type="content" source="images/deployment-steps.png" alt-text="Ekleme ve yapılandırma işlemi" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>Cihazları hizmete ekleme
Desteklenen cihazlardan herhangi birini eklemek için Uç Nokta için Defender portalının ekleme bölümüne gitmeniz gerekir. Cihaza bağlı olarak, uygun adımlarla yönlendirilirsiniz ve cihaza uygun yönetim ve dağıtım aracı seçenekleri sağlanır. 

Cihazları hizmete eklemek için:

- Cihazın [en düşük gereksinimleri](minimum-requirements.md) karşıladığını doğrulayın
- Cihaza bağlı olarak, Uç Nokta için Defender portalının ekleme bölümünde sağlanan yapılandırma adımlarını izleyin
- Cihazlarınız için uygun yönetim aracını ve dağıtım yöntemini kullanın
- Cihazların düzgün şekilde eklendiğini ve hizmete bildirildiğini doğrulamak için bir algılama testi çalıştırın

Bu makale, Windows İstemcisi ve Sunucu sürümleri için geçerli olan ekleme yöntemleri hakkında bilgi sağlar.

## <a name="onboarding-and-configuration-tool-options"></a>Ekleme ve yapılandırma aracı seçenekleri
Aşağıdaki tabloda, eklemeniz gereken uç noktayı temel alan kullanılabilir araçlar listelenir.

| Uç nokta     | Araç seçenekleri                       |
|--------------|------------------------------------------|
| **Windows İstemcisi**  |     [Mobil Cihaz Yönetimi / Microsoft Intune](configure-endpoints-mdm.md) <br> [Grup İlkesi](configure-endpoints-gp.md) <br> [Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md) <br>[VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **Windows Server:**  | [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [Yerel betikler](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Kukla](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)               |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


> [!NOTE]
> Microsoft Endpoint Manager tarafından yönetilmeyen cihazlar için (Microsoft Intune veya Microsoft Endpoint Configuration Manager), Uç Nokta için Microsoft Defender için Güvenlik Yönetimi'ni kullanabilirsiniz  doğrudan Endpoint Manager'den Microsoft Defender için güvenlik yapılandırmaları almak için.

Aşağıdaki tabloda, eklemeniz gereken uç noktayı temel alan kullanılabilir araçlar listelenir.

## <a name="configure-capabilities-of-the-service"></a>Hizmetin özelliklerini yapılandırma
Cihazları ekleme, Uç Nokta için Microsoft Defender uç nokta algılama ve yanıt özelliğini etkili bir şekilde etkinleştirir.

Cihazları ekledikten sonra hizmetin diğer özelliklerini yapılandırmanız gerekir. Aşağıdaki tabloda, ortamınız için en iyi korumayı elde etmek için yapılandırabileceğiniz özellikler listelemektedir.

| Yeteneği | Açıklama |
|-|-|
| [Tehdit & Güvenlik Açığı Yönetimini Yapılandırma (TVM)](tvm-prerequisites.md) | Tehdit & Güvenlik Açığı Yönetimi, Uç Nokta için Microsoft Defender bir bileşenidir ve hem güvenlik yöneticilerine hem de güvenlik operasyonları ekiplerine aşağıdakiler gibi benzersiz bir değer sağlar: <br><br> - Uç nokta güvenlik açıklarıyla ilişkili gerçek zamanlı uç nokta algılama ve yanıt (EDR) içgörüleri. <br><br> - Olay araştırmaları sırasında çok değerli cihaz güvenlik açığı bağlamı. <br><br> - Microsoft Intune ve Microsoft System Center Configuration Manager aracılığıyla yerleşik düzeltme işlemleri.  |
| [Yeni nesil korumayı (NGP) yapılandırma](configure-microsoft-defender-antivirus-features.md) | Microsoft Defender Virüsten Koruma, masaüstü bilgisayarlar, taşınabilir bilgisayarlar ve sunucular için yeni nesil koruma sağlayan yerleşik bir kötü amaçlı yazılımdan koruma çözümüdür. Microsoft Defender Virüsten Koruma şunları içerir:<br> <br>-Yeni ve yeni tehditlerin neredeyse anında algılanması ve engellenmesi için bulut tabanlı koruma. Bulut tabanlı koruma, makine öğrenmesi ve Akıllı Güvenlik Grafı ile birlikte Microsoft Defender Virüsten Koruma'yı destekleyen yeni nesil teknolojilerin bir parçasıdır.<br> <br> - Gelişmiş dosya ve işlem davranışı izleme ve diğer buluşsal yöntemler kullanılarak her zaman açık tarama ("gerçek zamanlı koruma" olarak da bilinir).<br><br> - Makine öğrenmesi, insan ve otomatik büyük veri analizi ve derinlemesine tehdit direnci araştırmalarına dayalı ayrılmış koruma güncelleştirmeleri. |
| [Saldırı yüzeyini azaltmayı yapılandırma (ASR)](overview-attack-surface-reduction.md) | Uç Nokta için Microsoft Defender'daki saldırı yüzeyi azaltma özellikleri, kuruluştaki cihazların ve uygulamaların yeni ve yeni tehditlere karşı korunmasına yardımcı olur. |
| [Otomatik Araştırma & Düzeltme (AIR) özelliklerini yapılandırma](configure-automated-investigations-remediation.md) | Uç Nokta için Microsoft Defender, tek tek araştırılması gereken uyarı hacmini önemli ölçüde azaltmak için Otomatik araştırma kullanır. Otomatik araştırma özelliği, uyarıları incelemek ve ihlalleri çözmek için anında düzeltme eylemi uygulamak için analistler tarafından kullanılan çeşitli inceleme algoritmalarından ve işlemlerden (playbook'lar gibi) yararlanır. Bu, uyarı hacmini önemli ölçüde azaltarak güvenlik operasyonları uzmanlarının daha karmaşık tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak sağlar. |
| [Microsoft Tehdit Uzmanları (MTE) özelliklerini yapılandırma](configure-microsoft-threat-experts.md) | Microsoft Tehdit Uzmanları, güvenlik operasyon merkezlerine (SOC) benzersiz ortamlarındaki kritik tehditlerin kaçırılmamasını sağlamaya yardımcı olmak için uzman düzeyinde izleme ve analiz sağlayan yönetilen bir avcılık hizmetidir.      |


## <a name="supported-capabilities-for-windows-devices"></a>Windows cihazları için desteklenen özellikler

|İşletim Sistemi  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |<sup>Windows Server 2016[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Önleme**    |         |         |         |         |         |
|Saldırı Yüzeyi Azaltma kuralları     |    E     |   E      |    E     |    E     |    E     |
|Cihaz Denetimi     |     E    |    N     |    N     |    N     |    N     |  
|Güvenlik duvarı     |      E   |    E     |     E    |    E    |    E   |
|Ağ Koruması     |      E   |    E     |     E    |    E    |    E   |
|Yeni nesil koruma     |      E   |    E     |     E    |    E    |    E   |
|Kurcalama Koruması     |        E   |    E     |     E    |    E    |    E   |
|Web Koruması     |       E   |    E     |     E    |    E    |    E   |
|||||||
|**Algılama**     |         |         |         |||
|Gelişmiş Avcılık     |      E   |    E     |     E    |    E    |    E   |
|Özel dosya göstergeleri     |      E   |    E     |     E    |    E    |    E   |
|Özel ağ göstergeleri     |      E   |    E     |     E    |    E    |    E   |
|Pasif Mod & EDR Bloğu     |      E   |    E     |     E    |    E    |    E   |
|Algılama algılayıcısı     |      E   |    E     |     E    |    E    |    E   |
|Uç nokta & ağ cihazı bulma     |      E   |    N     |     N    |    N    |    N   |
|||||||
|**Yanıt**     |         |         |         |||
|Otomatik Araştırma & Yanıtı (AIR)    |      E   |    E     |     E    |    E    |    E   |
|Cihaz yanıtı özellikleri: yalıtım, araştırma paketi toplama, AV taraması çalıştırma     |      E   |    E     |     E    |    E    |    E   |
|Dosya yanıtı özellikleri: dosya toplama, derin analiz, blok dosyası, durdurma ve karantina işlemleri     |      E   |    E     |     E    |    E    |    E   |
|Canlı Yanıt    |      E   |    E     |     E    |    E    |    E   |

(<a id="fn1">1</a>) Windows Server 2012 R2 ve 2016 için modern, birleşik çözümü ifade eder. Daha fazla bilgi için bkz. [Uç Nokta için Defender hizmetine Windows Sunucuları ekleme](configure-server-endpoints.md).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2, EDR algılayıcısı ve System Center Endpoint Protection (SCEP) kullanan AV için destek içerir.
