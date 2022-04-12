---
title: Pertahanan Microsoft untuk Titik Akhir dağıtımınızı planlama
description: Ortamınız için en iyi Pertahanan Microsoft untuk Titik Akhir dağıtım stratejisini seçin
keywords: dağıtım, plan, dağıtım stratejisi, buluta özel, yönetim, şirket içi, değerlendirme, ekleme, yerel, grup ilkesi, gp, uç nokta yöneticisi, mem
search.product: eADQiWindows 10XVcnh
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 63996aa4d046ac719e0e6b98ed4c5980e0d979be
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783875"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Pertahanan Microsoft untuk Titik Akhir dağıtımınızı planlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Paketin içindeki güvenlik özelliklerini en üst düzeye çıkarmak ve kuruluşunuzu siber tehditlere karşı daha iyi korumak için Pertahanan Microsoft untuk Titik Akhir dağıtımınızı planlayın.

Bu çözüm, ortam mimarinizi tanımlama, gereksinimlerinize en uygun dağıtım aracı türünü seçme ve özellikleri yapılandırma konusunda rehberlik sağlar.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="Dağıtım akışı" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>1. Adım: Mimariyi tanımlama

Her kurumsal ortamın benzersiz olduğunu anlıyoruz, bu nedenle hizmetin nasıl dağıtılacağı konusunda size esneklik sağlamak için çeşitli seçenekler sağladık.

Ortamınıza bağlı olarak, bazı araçlar belirli mimariler için daha uygundur.

Kuruluşunuzu en iyi şekilde paketleyen uygun Uç Nokta için Defender mimarisini seçmek için aşağıdaki malzemeyi kullanın.

| Öğe | Açıklama |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Uç Nokta için Defender dağıtımı stratejisi" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Mimari malzeme, dağıtımınızı aşağıdaki mimariler için planlamanıza yardımcı olur: <ul><li> Bulutta yerel </li><li> Ortak yönetim </li><li> Şirket içi</li><li>Değerlendirme ve yerel ekleme</li>

## <a name="step-2-select-deployment-method"></a>2. Adım: Dağıtım yöntemini seçin

| Uç nokta     | Dağıtım aracı                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Kukla](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

Aşağıdaki tabloda, dağıtımı uygun şekilde planlamak için kullanabileceğiniz desteklenen uç noktalar ve ilgili dağıtım aracı listelenmektedir.

|Uç nokta|Dağıtım aracı|
|---|---|
|**Windows**|[Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**macOS**|[Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md)|
|**Linux Server**|[Yerel betik](linux-install-manually.md) <br> [Kukla](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Uygulama tabanlı](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>3. Adım: Özellikleri yapılandırma

Uç noktaları ekledikten sonra, pakette kullanılabilen güçlü güvenlik korumasını en üst düzeye çıkarabilmeniz için Uç Nokta için Defender'daki güvenlik özelliklerini yapılandırın. Özellikler şunlardır:

- Uç nokta algılama ve yanıt
- Yeni nesil koruma
- Saldırı yüzeyini azaltma

## <a name="related-topics"></a>İlgili konular

- [Dağıtım aşamaları](deployment-phases.md)
