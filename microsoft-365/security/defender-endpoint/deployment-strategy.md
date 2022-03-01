---
title: Uç nokta dağıtımı için Microsoft Defender'ı planlama
description: Ortamınız için en iyi Uç nokta dağıtım stratejisi için Microsoft Defender'ı seçme
keywords: dağıtma, plan, dağıtım stratejisi, yerel bulut, yönetim, şirket içi, değerlendirme, ekleme, yerel, grup ilkesi, gp, uç nokta yöneticisi, mem
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
ms.openlocfilehash: cfdbb84cfcc2cda08572709adb3b13db83e319fa
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011951"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Uç nokta dağıtımı için Microsoft Defender'ı planlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Paketin içindeki güvenlik özelliklerini en üst düzeye çıkarmak ve kurumlarınızı siber tehditlere karşı daha iyi korumak için Uç Nokta dağıtımı için Microsoft Defender'ı planlamalısınız.

Bu çözüm, ortam mimarinizi belirleme, ihtiyaçlarınıza en uygun dağıtım aracını seçme ve özellikleri yapılandırma konusunda yol gösterici kılavuzlar sağlar.

![Dağıtım akışı resmi.](images/deployment-guide-plan.png)

## <a name="step-1-identify-architecture"></a>1. Adım: Mimariyi tanımlama

Her kurumsal ortamın benzersiz olduğunu anlıyoruz, bu nedenle size hizmetin dağıtımı konusunda esneklik sağlamak için çeşitli seçenekler sağladık.

Ortamınıza bağlı olarak, bazı araçlar belirli mimarilere daha uygun olur.

Aşağıdaki malzemeyi kullanarak, kuruma en uygun uç nokta mimarisi için Defender'ı seçin.

| Öğe | Açıklama |
|:-----|:-----|
|[![Uç nokta dağıtım stratejisi için Defender'ın küçük resmi.](images/mde-deployment-strategy.png)](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Mimari malzemeleri, aşağıdaki mimariler için dağıtımınızı planlamanıza yardımcı olur: <ul><li> Bulut yerel </li><li> Birlikte yönetim </li><li> Şirket içi</li><li>Değerlendirme ve yerel ekleme</li>

## <a name="step-2-select-deployment-method"></a>2. Adım: Dağıtım yöntemini seçme

| Uç nokta     | Dağıtım aracı                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Cihaz Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Operasyon](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

Aşağıdaki tabloda, dağıtımı uygun şekilde planlamak için kullanabileceğiniz desteklenen uç noktalar ve buna karşılık gelen dağıtım aracı listeledir.

|Uç nokta|Dağıtım aracı|
|---|---|
|**Windows**|[Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Cihaz Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-azure-defender)|
|**macOS**|[Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md)|
|**Linux Server**|[Yerel betik](linux-install-manually.md) <br> [Operasyon](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Uygulamaya dayalı](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>3. Adım: Özellikleri yapılandırma

Ekleme uç noktalarının ardından, pakette kullanılabilen güçlü güvenlik korumasını en üst düzeye çıkarmak için Uç Nokta için Defender'daki güvenlik özelliklerini yapılandırabilirsiniz. Bu özellikler şunlardır:

- Uç nokta algılama ve yanıt
- Yeni nesil koruma
- Saldırı yüzeyini azaltma

## <a name="related-topics"></a>İlgili konular

- [Dağıtım aşamaları](deployment-phases.md)
