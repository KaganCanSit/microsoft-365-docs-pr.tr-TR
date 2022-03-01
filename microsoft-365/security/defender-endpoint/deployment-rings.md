---
title: Uç nokta için Microsoft Defender'ı halkalar içinde dağıtma
description: Uç nokta için Microsoft Defender'ı halkalar olarak dağıtmayı öğrenin
keywords: dağıtma, halkalar, değerlendirme, pilot, insider hızlı, insider yavaş, kurulum, ekleme, aşama, dağıtım, dağıtma, benimseme, yapılandırma
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a7a9673591f4d77197390541a58169a58b04fe91
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021632"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Uç nokta için Microsoft Defender'ı halkalar içinde dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Uç nokta için Microsoft Defender'ı dağıtma işlemi, halka tabanlı bir dağıtım yaklaşımı kullanılarak yapılabilir.

Dağıtım halkaları aşağıdaki senaryolarda uygulanabilir:

- [Yeni dağıtımlar](#new-deployments)
- [Mevcut dağıtımlar](#existing-deployments)

## <a name="new-deployments"></a>Yeni dağıtımlar

![Dağıtım halkalarının resmi.](images/deployment-rings.png)

Halka tabanlı yaklaşım, hizmeti daha büyük bir cihaz kümesinde dağıtmaya devam etmeden önce belirli ölçütlerin karşılandığı bir uç nokta kümesi belirleme yöntemidir. Her halka için çıkış ölçütlerini tanımlayabilir ve bir sonraki halkaya geçene kadar memnun bırakıldıklarından emin olabilirsiniz.

Halka tabanlı bir dağıtım benimsenme, hizmetin dağıtımı sırasında ortaya çıkabilecek olası sorunları azaltmaya yardımcı olur. İlk olarak belirli sayıda cihazı pilot olarak kullanarak olası sorunları tanımlayabilir ve ortaya çıkabilecek riskleri azaltmak için kullanılabilirsiniz.

Tablo 1, kullanabileceğiniz dağıtım halkaları için bir örnek sağlar.

**Tablo 1**:

<br>

****

|Dağıtım halkası|Açıklama|
|---|---|
|Değerlendir|1. Çaldır: Pilot test için 50 sistemi belirleme|
|Pilot|Halka 2: Üretim ortamında sonraki 50-100 uç noktasını belirleme|
|Tam dağıtım|3. Halka: Hizmeti ortamın kalan kalanına daha büyük adımlarla yuvarlayın|
|

### <a name="exit-criteria"></a>Çıkış ölçütü

Bu halkalar için örnek bir çıkış ölçütleri kümesi şunları içerebilir:

- Cihazlar cihaz stok listesinde görünür
- Uyarılar panoda görünür
- [Algılama testi çalıştırma](run-detection-test.md)
- [Bir cihazda benzetimi yapılan saldırıyı çalıştırma](attack-simulations.md)

### <a name="evaluate"></a>Değerlendir

Hizmete makinenizi ekleme için ortamınıza az sayıda test makinesi girin. İdeal olan, bu makinelerde 50'den az uç nokta olmasıdır.

### <a name="pilot"></a>Pilot

Uç Nokta için Microsoft Defender, hizmete ekleyip ekleyip eky hizmetinin çeşitli uç noktalarını destekler. Bu halkada, ekleme için birkaç cihaz tanımlayın ve tanımladığınız çıkış ölçütlerine göre bir sonraki dağıtım halkası ile devam edin.

Aşağıdaki tablo desteklenen uç noktaları ve hizmete cihaz ekleme için kullanabileceğiniz ilgili aracı gösterir.

| Uç nokta     | Dağıtım aracı                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br> NOT: Üretim ortamında 10'dan fazla cihazı dağıtmak için, bunun yerine Grup İlkesi yöntemini veya aşağıda listelenen diğer desteklenen araçları kullanın.<br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Cihaz Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Operasyon](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               |

### <a name="full-deployment"></a>Tam dağıtım

Bu aşamada, dağıtımınızı planlamanıza [yardımcı olacak](deployment-strategy.md) Dağıtım malzemelerini planlamak için kullanabilirsiniz.

Aşağıdaki malzemeyi kullanarak, kuruma en uygun uç nokta mimarisi için Microsoft Defender'ı seçin.

|**Öğe**|**Açıklama**|
|:-----|:-----|
|[![Uç nokta dağıtım stratejisi için Microsoft Defender'ın küçük resmi.](images/mde-deployment-strategy.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Mimari malzemeleri, aşağıdaki mimariler için dağıtımınızı planlamanıza yardımcı olur: <ul><li> Bulut yerel </li><li> Birlikte yönetim </li><li> Şirket içi</li><li>Değerlendirme ve yerel ekleme</li></ul>

## <a name="existing-deployments"></a>Mevcut dağıtımlar

### <a name="windows-endpoints"></a>Windows uç noktalarını yapılandırma

Sunucularda Windows/veya Windows için, Güvenlik Güncelleştirmesi Doğrulama programını **(BUCA**) kullanarak önceden test etmek için birkaç makine seçersiniz (Salı düzeltme eki olmadan önce).

Daha fazla bilgi için bkz.:

- [Güvenlik Güncelleştirmesi Doğrulama Programı nedir?](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Yazılım Güncelleştirmesi Doğrulama Programı ve Microsoft Kötü Amaçlı Yazılıma Karşı Koruma Merkezi -TwC Etkileşimli Zaman Çizelgesi Bölüm 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Windows olmayan uç noktalar

MacOS ve Linux ile birkaç sistem alıp Beta kanalında çalıştırabilirsiniz.

> [!NOTE]
> En az bir güvenlik yöneticisi ve bir geliştirici ideal olarak, derlemenin Geçerli kanala dönüşmeden önce uyumluluk, performans ve güvenilirlik sorunlarını bu şekilde bulmanı sağlar.

Kanalın seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. Güncelleştirmeleri ve yeni özellikleri ilk alan cihazlar Beta cihazlardır, daha sonra Önizleme ve son olarak Güncel takip eder.

![Insider halkaları resmi.](images/insider-rings.png)

Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, aşağıdaki kuruluşta bazı cihazları Beta veya Önizleme'yi kullanmak üzere yapılandırmanız önerilir.

> [!WARNING]
> İlk yüklemeden sonra kanalı değiştirmek için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: var olan paketi kaldırın, cihazınızı yeni kanalı kullanmak üzere yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belge'de yer alan adımları izleyin.
