---
title: Pertahanan Microsoft untuk Titik Akhir değerlendirmeyi etkinleştirme
description: Lisans durumunu denetleme ve uç noktaları ekleme dahil olmak üzere Microsoft 365 Defender deneme laboratuvarınızı veya pilot ortamınızı etkinleştirin
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
ms.openlocfilehash: 2acde87daaff88ec9ce7458218919342a9f1edd8
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782511"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Pertahanan Microsoft untuk Titik Akhir değerlendirme ortamını etkinleştirme


Bu makale, üretim cihazlarını kullanarak Pertahanan Microsoft untuk Titik Akhir için değerlendirme ortamını ayarlama adımlarında size yol gösterir. 


> [!TIP]
> Pertahanan Microsoft untuk Titik Akhir ayrıca önceden yapılandırılmış cihazlar ekleyebileceğiniz ve platformun özelliklerini değerlendirmek için simülasyonlar çalıştırabileceğiniz bir ürün içi değerlendirme laboratuvarıyla birlikte gelir. Laboratuvar, gelişmiş tehdit avcılığı ve tehdit analizi gibi birçok özellik için rehberlik de dahil olmak üzere Pertahanan Microsoft untuk Titik Akhir değerini hızla göstermeye yardımcı olabilecek basitleştirilmiş bir kurulum deneyimiyle birlikte gelir. Daha fazla bilgi için bkz [. Özellikleri değerlendirme](../defender-endpoint/evaluation-lab.md). <br> Bu makalede sağlanan yönergelerle değerlendirme laboratuvarı arasındaki temel fark, değerlendirme ortamında üretim cihazlarının kullanıldığı, değerlendirme laboratuvarının ise üretim dışı cihazlar kullandığıdır. 

Pertahanan Microsoft untuk Titik Akhir değerlendirmesini etkinleştirmek için aşağıdaki adımları kullanın.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="Microsoft Defender değerlendirme ortamında Pertahanan Microsoft untuk Titik Akhir etkinleştirme adımları" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [1. Adım. Lisans durumunu denetleme](#step-1-check-license-state)
- [2. Adım. Uç noktaları ekleme](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Adım 1. Lisans durumunu denetleme

Doğru şekilde sağlandığını doğrulamak için önce lisans durumunu denetlemeniz gerekir. Bunu yönetim merkezi veya **Microsoft Azure portalı** üzerinden yapabilirsiniz.


1. Lisanslarınızı görüntülemek için **Microsoft Azure portalına** gidin ve [Microsoft Azure portalı lisans bölümüne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="Microsoft 365 Defender portalındaki Azure Lisanslama sayfası" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. Alternatif olarak, yönetim merkezinde **BillingSubscriptions'a** >  gidin.

    Ekranda sağlanan tüm lisansları ve geçerli **Durumlarını** görürsünüz.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="Microsoft Azure portalındaki Faturalama lisansları sayfası" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Adım 2. Desteklenen yönetim araçlarından herhangi birini kullanarak uç noktaları ekleme

Lisans durumunun düzgün sağlandığını doğruladıktan sonra, cihazları hizmete eklemeye başlayabilirsiniz. 

Pertahanan Microsoft untuk Titik Akhir değerlendirmek amacıyla değerlendirmeyi gerçekleştirmek üzere birkaç Windows cihazı seçmenizi öneririz.

Desteklenen yönetim araçlarından herhangi birini kullanmayı seçebilirsiniz, ancak Intune en iyi tümleştirmeyi sağlar. Daha fazla bilgi için bkz[. Microsoft Intune'de Pertahanan Microsoft untuk Titik Akhir yapılandırma](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

[Plan dağıtımı](../defender-endpoint/deployment-strategy.md) konusunda, Uç Nokta için Defender'ı dağıtmak için uygulamanız gereken genel adımlar özetlenmiştir.  

Ekleme işlemine hızlı bir genel bakış için bu videoyu izleyin ve kullanılabilir araçlar ve yöntemler hakkında bilgi edinin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Ekleme aracı seçenekleri

Aşağıdaki tabloda, eklemeniz gereken uç noktayı temel alan kullanılabilir araçlar listelenir.

Uç nokta | Araç seçenekleri
:---|:---
**Windows** | [Yerel betik (en fazla 10 cihaz)](../defender-endpoint/configure-endpoints-script.md), [grup ilkesi](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](../defender-endpoint/configure-endpoints-mdm.md), [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md), [VDI betikleri](../defender-endpoint/configure-endpoints-vdi.md), [ Bulut için Microsoft Defender ile tümleştirme](../defender-endpoint/configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)
**macOS** | [Yerel betikler](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Mobil Cihaz Yönetimi](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [Yerel betik](../defender-endpoint/linux-install-manually.md),  [Puppet](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Uygulama tabanlı](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Sonraki adım
[pilotu Pertahanan Microsoft untuk Titik Akhir için ayarlama](eval-defender-endpoint-pilot.md)
 
[Değerlendirme Pertahanan Microsoft untuk Titik Akhir](eval-defender-endpoint-overview.md) için genel bakışa dönün

[Değerlendirme ve pilot Microsoft 365 Defender](eval-overview.md) genel bakışa dönün
