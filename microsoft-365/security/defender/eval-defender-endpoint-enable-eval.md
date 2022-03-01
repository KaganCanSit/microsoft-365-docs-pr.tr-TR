---
title: Uç nokta değerlendirme için Microsoft Defender'ı etkinleştirme
description: Lisans Microsoft 365 Defender denetleme ve ekleme uç noktalarını da içeren deneme laboratuvarı veya pilot ortamınızı etkinleştirme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 846fd6854b8e2dcb408aaa55348380bb91c6b907
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014193"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Uç nokta değerlendirme ortamı için Microsoft Defender'ı etkinleştirme


Bu makale, üretim cihazlarını kullanarak Uç Nokta için Microsoft Defender için değerlendirme ortamını ayarlama adımları boyunca size yol sunar. 


> [!TIP]
> Uç Nokta için Microsoft Defender, önceden yapılandırılmış cihazlar ekip platformun özelliklerini değerlendirmek üzere benzetimler çalıştırılan bir ürün için değerlendirme laboratuvarı da içerir. Laboratuvar, gelişmiş av ve tehdit analizi gibi birçok özellik için yol gösterme de dahil olmak üzere Uç Nokta için Microsoft Defender'ın değerini hızla göstermeye yardımcı olacak basitleştirilmiş bir ayarlama deneyimiyle geliyor. Daha fazla bilgi için bkz [. Özellikleri Değerlendirme](../defender-endpoint/evaluation-lab.md). <br> Bu makalede sağlanan kılavuz ile değerlendirme laboratuvarı arasındaki temel fark değerlendirme ortamı üretim cihazlarını, değerlendirme laboratuvarı ise üretim dışı cihazlar kullanır. 

Uç Nokta için Microsoft Defender değerlendirmesini etkinleştirmek üzere aşağıdaki adımları kullanın.

![Microsoft Defender değerlendirme ortamında Uç Nokta için Microsoft Defender'ı etkinleştirme adımları.](../../media/defender/m365-defender-endpoint-eval-enable-steps.png)

- [1. Adım. Lisans durumunu denetleme](#step-1-check-license-state)
- [2. Adım. Ekleme uç noktaları](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Adım 1. Lisans durumunu denetleme

Düzgün sağ olduğunu doğrulamak için önce lisans durumunu denetlemeniz gerekir. Bunu yönetim merkezi aracılığıyla veya genel merkezin Microsoft Azure **.**


1. Lisanslarınızı görüntülemek için Lisanslar **portalına Microsoft Azure gidin** ve lisans Microsoft Azure [bölümüne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   ![Azure Lisanslama sayfasının resmi.](../../media/defender/atp-licensing-azure-portal.png)

1. Alternatif olarak, yönetim merkezinde **BillingSubscriptions'a** >  gidin.

    Ekranda, sağlanan tüm lisansları ve onların geçerli durumunu **görürsünüz**.

    ![Fatura lisanslarının resmi.](../../media/defender/atp-billing-subscriptions.png)

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Adım 2. Desteklenen yönetim araçlardan herhangi birini kullanarak uç noktaları ekleme

Lisans durumunun düzgün sağlandıktan sonra, hizmete cihazları eklemeye başlayabilirsiniz. 

Uç Nokta için Microsoft Defender'ı değerlendirme amacıyla, değerlendirmenin hangi cihazlarda Windows fazla cihaz seçmenizi öneririz.

Desteklenen yönetim araçlardan herhangi birini kullanmayı seçebilirsiniz, ancak Intune en iyi tümleştirmeyi sağlar. Daha fazla bilgi için bkz. [Microsoft Intune'de Uç Nokta için Microsoft Defender'ı yapılandırma](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

Dağıtım [planlama başlığında](../defender-endpoint/deployment-strategy.md) , Uç Nokta için Defender'ı dağıtmak için ihtiyacınız olan genel adımlar özetlanmıştır.  

Ekleme sürecine hızlı bir genel bakış için bu videoyu izleyin ve kullanılabilir araçlar ve yöntemler hakkında bilgi edinin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Ekleme aracı seçenekleri

Aşağıdaki tabloda, ekleme için gereken uç nokta temel alarak kullanılabilir araçlar listeledir.

Uç nokta | Araç seçenekleri
:---|:---
**Windows** | [Yerel betik (10](../defender-endpoint/configure-endpoints-script.md) cihaza kadar)[, Grup](../defender-endpoint/configure-endpoints-gp.md) İlkesi, [Microsoft Endpoint Manager/ Mobil](../defender-endpoint/configure-endpoints-mdm.md) Cihaz Yöneticisi, [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md), [VDI betikleri](../defender-endpoint/configure-endpoints-vdi.md), [Bulut için Microsoft Defender ile Tümleştirme](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender)
**macOS** | [Yerel betikler](../defender-endpoint/mac-install-manually.md)[, Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Mobil Cihaz Yönetimi](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [Yerel betik](../defender-endpoint/linux-install-manually.md),  [Suz](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Uygulamaya dayalı](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Sonraki adım
[Uç Nokta için Microsoft Defender pilot kurulumu](eval-defender-endpoint-pilot.md)
 
Uç Nokta için [Microsoft Defender'ı Değerlendir'e genel bakış](eval-defender-endpoint-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
