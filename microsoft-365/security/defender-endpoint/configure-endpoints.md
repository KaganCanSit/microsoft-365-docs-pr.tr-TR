---
title: Windows cihazlar için ekleme araçları ve yöntemleri
description: algılayıcı verilerini Uç Nokta için Microsoft Defender algılayıcıya gönderebilmeleri için Windows cihazları ekleme
keywords: Windows cihazları ekleme, grup ilkesi, uç nokta yapılandırma yöneticisi, mobil cihaz yönetimi, yerel betik, gp, sccm, mdm, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.openlocfilehash: fbc5a0981a6318d767252e968e45874d889aee85
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949111"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Uç Nokta için Defender'da Windows cihazlar için ekleme araçları ve yöntemleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç nokta veri kaybı önleme (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [İçeriden risk yönetimi](/microsoft-365/compliance/insider-risk-management)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Uç Nokta için Defender hizmetinin algılayıcı verilerini alabilmesi için kuruluşunuzdaki cihazların yapılandırılması gerekir. Kuruluşunuzdaki cihazları yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

Genel olarak, eklediğiniz Windows cihazı tanımlayacak ve ardından cihaza veya ortamınıza uygun olan ilgili aracı izleyeceksiniz.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="Ekleme araçları ve yöntemleri" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>Uç nokta ekleme araçları

Eklemek istediğiniz Windows uç noktasına bağlı olarak, aşağıdaki tabloda açıklanan ilgili aracı veya yöntemi kullanın.

Windows cihazı | Ekleme aracı veya yöntemi
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 ve 2019 ve 2022</li> <li>Windows Server 2012 R2 ve 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md)<br>   [Grup İlkesi](configure-endpoints-gp.md)<br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/ Mobil Cihaz Yönetimi (Intune)](configure-endpoints-mdm.md)<br>    [VDI betikleri](configure-endpoints-vdi.md) <br><br> **NOT**: Yerel betik kavram kanıtı için uygundur ancak üretim dağıtımı için kullanılmamalıdır. Üretim dağıtımı için grup ilkesi, Microsoft Endpoint Configuration Manager veya Intune kullanmanızı öneririz.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Windows veya Bulut için Microsoft Defender önceki sürümlerini ekleme](onboard-downlevel.md) [](/azure/security-center/security-center-wdatp) <br><br> **NOT**: Microsoft Monitoring Agent artık Azure Log Analytics aracısıdır. Daha fazla bilgi için bkz [. Log Analytics aracısına genel bakış](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **NOT**: Microsoft Monitoring Agent artık Azure Log Analytics aracısıdır. Daha fazla bilgi için bkz [. Log Analytics aracısına genel bakış](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 ve Windows Server 2012 R2'nin[, Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) ekleme yönergeleri kullanılarak eklenmelidir.

>[!IMPORTANT]
>Uç Nokta için Microsoft Defender Server SKU'su satın almaya uygun olmak için E5/A5, Microsoft 365 E5/A5 veya Microsoft 365 E5 Güvenlik abonelik lisansları Windows aşağıdakilerden en az birini zaten satın almış olmanız gerekir.  Lisanslama hakkında daha fazla bilgi için bkz. [Ürün Koşulları](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Konu|Açıklama
:---|:---
[grup ilkesi kullanarak cihazları ekleme](configure-endpoints-gp.md)|Yapılandırma paketini cihazlara dağıtmak için grup ilkesi kullanın.
[Microsoft Endpoint Configuration Manager kullanarak cihazları ekleme](configure-endpoints-sccm.md)|Yapılandırma paketini cihazlara dağıtmak için Microsoft Endpoint Manager (geçerli dal) sürüm 1606 veya Microsoft Endpoint Manager (geçerli dal) sürüm 1602 veya önceki sürümleri kullanabilirsiniz.
[Mobil Cihaz Yönetimi araçlarını kullanarak cihazları ekleme](configure-endpoints-mdm.md)|Yapılandırma paketini cihaza dağıtmak için Mobil Cihaz Yönetimi araçlarını veya Microsoft Intune kullanın.
[Yerel betik kullanarak cihazları ekleme](configure-endpoints-script.md)|Yapılandırma paketini uç noktalara dağıtmak için yerel betiği kullanmayı öğrenin.
[Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)|VDI cihazlarını yapılandırmak için yapılandırma paketini kullanmayı öğrenin.

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Cihazı ekledikten sonra, bir cihazın hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md).
