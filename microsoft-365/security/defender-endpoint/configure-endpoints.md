---
title: Windows cihazlarına ekleme araçları Windows yöntemleri
description: Algılayıcı Windows uç nokta algılayıcısı için Microsoft Defender'a gönderiler için cihaz kullanın
keywords: Onboard Windows ilke, grup ilkesi, uç nokta yapılandırma yöneticisi, mobil cihaz yönetimi, yerel komut dosyası, gp, sccm, mdm, intune
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
ms.openlocfilehash: c4b70bfa9875d1e8c09d21e9435d8b4200555b5c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011832"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Uç Nokta için Defender'da Windows cihazlar için ekleme araçları ve yöntemleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 Insider risk yönetimi](/microsoft-365/compliance/insider-risk-management)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kuruluş cihazları, Uç Nokta için Defender hizmetinin bunlardan algılayıcı verilerini al etkileysin diye yapılandırılması gerekir. Kuruluşta cihazları yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

Genel olarak, hangi cihazı Windows olduğunu belirleyerek cihaza veya ortamınıza uygun olan aracı takip edersiniz.

![Ekleme araçları ve yöntemleri görüntüsü](images/onboarding-config-tools.png)

## <a name="endpoint-onboarding-tools"></a>Uç nokta ekleme araçları

Ekleme yapmak istediğiniz Windows uç noktasına bağlı olarak, aşağıdaki tabloda açıklanan ilgili aracı veya yöntemi kullanın.

Windows cihazı seçin | Ekleme aracı veya yöntemi
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 ve 2019 ve 2022</li> <li>Windows Server 2012 R2 ve 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md)<br>   [Grup İlkesi](configure-endpoints-gp.md)<br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/ Mobil Cihaz Yönetimi (Intune)](configure-endpoints-mdm.md)<br>    [VDI betikleri](configure-endpoints-vdi.md) <br><br> **NOT**: Yerel bir betik kavram kanıtı için uygundur, ancak üretim dağıtımı için kullanılmaları gerekir. Üretim dağıtımı için Grup İlkesi, Grup İlkesi, Microsoft Endpoint Configuration Manager Intune'ı kullanmanızı öneririz.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Windows'ın önceki sürümlerini](onboard-downlevel.md) ekleme veya [Bulut için Microsoft Defender](/azure/security-center/security-center-wdatp) <br><br> **NOT**: Microsoft Monitoring Agent Azure Log Analytics aracısı oldu. Daha fazla bilgi edinmek için bkz. [Log Analytics aracıya genel bakış](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **NOT**: Microsoft Monitoring Agent Azure Log Analytics aracısı oldu. Daha fazla bilgi edinmek için bkz. [Log Analytics aracıya genel bakış](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 ve Windows Server 2012 R2'nin Onboard [Windows kullanılarak Windows gerekir](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>Uç Nokta Sunucusu SKU için Microsoft Defender'ı satın almaya uygun olmak için, aşağıdakilerin, Windows E5/A5, Microsoft 365 E5/A5 veya Microsoft 365 E5 Güvenlik abonelik lisanslarının minimum birleştirilmiş bir toplamını satın almalısınız.  Lisanslama hakkında daha fazla bilgi için, Ürün [Koşulları'ne bakın](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Konu|Açıklama
:---|:---
[Grup İlkesi kullanarak cihazları ekleme](configure-endpoints-gp.md)|Yapılandırma paketini cihazlara dağıtmak için Grup İlkesi'ne kullanın.
[Microsoft Endpoint Configuration Manager kullanarak cihazları Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Yapılandırma paketini cihazlara dağıtmak için Microsoft Endpoint Manager (geçerli dalı) sürüm 1606 veya Microsoft Endpoint Manager (geçerli dalı) sürüm 1602 veya daha önceki bir sürümünü kullanabilirsiniz.
[Mobil Cihaz Yönetimi araçlarını kullanarak cihazları ekleme](configure-endpoints-mdm.md)|Mobil Cihaz Yönetimi araçlarını veya Microsoft Intune paketin dağıtımı için Mobil Cihaz Yönetimi araçlarını kullanın.
[Yerel betik kullanarak cihazları ekleme](configure-endpoints-script.md)|Uç noktalara yapılandırma paketini dağıtmak için yerel betiği kullanmayı öğrenin.
[Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](configure-endpoints-vdi.md)|VDI cihazlarını yapılandırmak için yapılandırma paketini kullanmayı öğrenin.

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta cihazı için Microsoft Defender'da algılama testi çalıştırma](run-detection-test.md).
