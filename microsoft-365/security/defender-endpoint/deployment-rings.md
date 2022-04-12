---
title: halkalarda Pertahanan Microsoft untuk Titik Akhir dağıtma
description: halkalarda Pertahanan Microsoft untuk Titik Akhir dağıtmayı öğrenin
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
ms.openlocfilehash: 41f47720582f715e6c5d28276ddd87777e9669d5
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783391"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>halkalarda Pertahanan Microsoft untuk Titik Akhir dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Pertahanan Microsoft untuk Titik Akhir dağıtma işlemi halka tabanlı dağıtım yaklaşımı kullanılarak gerçekleştirilebilir.

Dağıtım halkaları aşağıdaki senaryolarda uygulanabilir:

- [Yeni dağıtımlar](#new-deployments)
- [Mevcut dağıtımlar](#existing-deployments)

## <a name="new-deployments"></a>Yeni dağıtımlar

:::image type="content" source="images/deployment-rings.png" alt-text="Dağıtım halkaları" lightbox="images/deployment-rings.png":::

Halka tabanlı yaklaşım, hizmeti daha büyük bir cihaz kümesine dağıtmaya devam etmeden önce eklenen bir uç nokta kümesini tanımlama ve belirli ölçütlerin karşılandığını doğrulama yöntemidir. Her halka için çıkış ölçütlerini tanımlayabilir ve bir sonraki halkaya geçmeden önce bunların karşılandığından emin olabilirsiniz.

Halka tabanlı dağıtımı benimsemek, hizmeti kullanıma alırken ortaya çıkabilecek olası sorunları azaltmaya yardımcı olur. Önce belirli sayıda cihazın pilot işlemini yaparak olası sorunları belirleyebilir ve ortaya çıkabilecek olası riskleri azaltabilirsiniz.

Tablo 1, kullanabileceğiniz dağıtım kademelerinin bir örneğini sağlar.

**Tablo 1**:

<br>

****

|Dağıtım halkası|Açıklama|
|---|---|
|Değerlendirmek|Halka 1: Pilot test için 50 sistemi tanımlama|
|Pilot|Halka 2: Üretim ortamındaki sonraki 50-100 uç noktayı belirleme|
|Tam dağıtım|Halka 3: Hizmeti ortamın geri kalanına daha büyük artışlarla dağıtın|
|

### <a name="exit-criteria"></a>Çıkış ölçütleri

Bu halkalar için örnek bir çıkış ölçütü kümesi şunlar olabilir:

- Cihazlar cihaz envanter listesinde gösterilir
- Uyarılar panoda görünür
- [Algılama testi çalıştırma](run-detection-test.md)
- [Cihazda sanal saldırı çalıştırma](attack-simulations.md)

### <a name="evaluate"></a>Değerlendirmek

Ortamınızda hizmete eklemek için az sayıda test makinesi belirleyin. İdeal olan, bu makinelerin 50'den az uç nokta olmasıdır.

### <a name="pilot"></a>Pilot

Pertahanan Microsoft untuk Titik Akhir hizmete ekleyebileceğiniz çeşitli uç noktaları destekler. Bu halkada, eklemek üzere birkaç cihazı belirleyin ve tanımladığınız çıkış ölçütlerine göre bir sonraki dağıtım halkasına devam etmeye karar verin.

Aşağıdaki tabloda desteklenen uç noktalar ve cihazları hizmete eklemek için kullanabileceğiniz ilgili araç gösterilmektedir.

| Uç nokta     | Dağıtım aracı                       |
|--------------|------------------------------------------|
| **Windows**  |  [Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md) <br> NOT: Üretim ortamında 10'dan fazla cihaz dağıtmak istiyorsanız, bunun yerine grup ilkesi yöntemini veya aşağıda listelenen diğer desteklenen araçları kullanın.<br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br>   [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md) <br> [Bulut için Microsoft Defender ile tümleştirme](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [Yerel betik](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Yerel betik](linux-install-manually.md) <br> [Kukla](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               |

### <a name="full-deployment"></a>Tam dağıtım

Bu aşamada, [dağıtımınızı](deployment-strategy.md) planlamanıza yardımcı olması için Dağıtım planlama malzemesini kullanabilirsiniz.

Kuruluşunuzu en iyi şekilde paketleyen uygun Pertahanan Microsoft untuk Titik Akhir mimarisini seçmek için aşağıdaki malzemeyi kullanın.

|**Öğe**|**Açıklama**|
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Pertahanan Microsoft untuk Titik Akhir dağıtımı stratejisi" lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Mimari malzeme, dağıtımınızı aşağıdaki mimariler için planlamanıza yardımcı olur: <ul><li> Bulutta yerel </li><li> Ortak yönetim </li><li> Şirket içi</li><li>Değerlendirme ve yerel ekleme</li></ul>

## <a name="existing-deployments"></a>Mevcut dağıtımlar

### <a name="windows-endpoints"></a>uç noktaları Windows

Windows ve/veya Windows Sunucuları için **, Güvenlik Güncelleştirmesi Doğrulama programını (SUVP**) kullanarak önceden test etmek üzere birkaç makine seçersiniz (Salı düzeltme eki uygulamadan önce).

Daha fazla bilgi için bkz.:

- [Güvenlik Güncelleştirmesi Doğrulama Programı nedir?](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Yazılım Güncelleştirme Doğrulama Programı ve Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi Kuruluşu - TwC Etkileşimli Zaman Çizelgesi Bölüm 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Windows olmayan uç noktalar

macOS ve Linux ile birkaç sistem alıp Beta kanalında çalıştırabilirsiniz.

> [!NOTE]
> İdeal olarak en az bir güvenlik yöneticisi ve bir geliştirici, böylece derlemeNin Geçerli kanala erişmesini sağlamadan önce uyumluluk, performans ve güvenilirlik sorunlarını bulabilirsiniz.

Kanal seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. Beta'daki cihazlar, güncelleştirmeleri ve yeni özellikleri ilk alan cihazlardır, daha sonra Önizleme ve son olarak Current tarafından takip edilir.

:::image type="content" source="images/insider-rings.png" alt-text="Insider halkaları" lightbox="images/insider-rings.png":::


Yeni özellikleri önizlemek ve erken geri bildirim sağlamak için kuruluşunuzdaki bazı cihazları Beta veya Önizleme kullanacak şekilde yapılandırmanız önerilir.

> [!WARNING]
> İlk yüklemeden sonra kanalın değiştirilmesi için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: Mevcut paketi kaldırın, cihazınızı yeni kanalı kullanacak şekilde yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belgedeki adımları izleyin.
