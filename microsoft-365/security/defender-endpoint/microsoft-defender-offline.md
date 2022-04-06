---
title: Microsoft Defender Çevrimdışı'da Windows
description: Microsoft Defender Çevrimdışı'i doğrudan Windows Defender Virüsten Koruma kullanabilirsiniz. Bunun ağ içinde nasıl dağıtılacağı da yönetebilirsiniz.
keywords: scan, defender, offline
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: ccb65b865afdf2a0ec0210c3593daee1cb5c09b6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476851"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Hızlı taramanın sonuçlarını çalıştırma Microsoft Defender Çevrimdışı gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Çevrimdışı, güvenilir bir ortamdan tarama başlatmaya ve çalıştırmaya olanak sağlayan bir kötü amaçlı yazılımdan koruma tarama aracıdır. Tarama normal Windows çekirdek dışından çalışır ve böylelikle virüsler ve ana önyükleme kaydına (M CLIP) bulaşan veya üzerine yazan kök setler gibi Windows kabuğunu atlayan kötü amaçlı yazılımları hedefleyebndir.

Kötü amaçlı Microsoft Defender Çevrimdışı bulaşmadan şüpheleniyorsanız veya kötü amaçlı yazılım salgınından sonra uç noktanın kapsamlı bir temiz olduğunu onaylamak istiyorsanız, parolayı kullanabilirsiniz.

Uygulama Windows 10 Windows 11, Microsoft Defender Çevrimdışı doğrudan doğrudan Windows Güvenliği ile [birini Windows Güvenliği çalıştırabilirsiniz](microsoft-defender-security-center-antivirus.md). Windows'Windows önceki sürümlerinde, kullanıcının Microsoft Defender Çevrimdışı önyüklenebilir medyaya yüklemesi, uç noktayı yeniden başlatması ve önyüklenebilir medyayı yüklemesi gerekirdi.

## <a name="prerequisites-and-requirements"></a>önkoşullar ve gereksinimler

Microsoft Defender Çevrimdışı ve Windows 10'Windows 11 sistem gereksinimleri ile aynı donanım Windows 10.

Gereksinimlerin nasıl karşı Windows 10 Windows 11 için aşağıdaki konulara bakın:

- [Minimum donanım gereksinimleri](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Donanım bileşeni yönergeleri](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Çevrimdışı işlemcilere sahip makinelerde veya ARM Server Stok Tutma birimleri Windows makinelerde desteklanmaz.

Uç noktadan Microsoft Defender Çevrimdışı için, kullanıcının yönetici ayrıcalıklarıyla oturum açmış olması gerekir.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender Çevrimdışı güncelleştirmeleri yükleme

Microsoft Defender Çevrimdışı, uç nokta üzerinde kullanılabilen en son koruma güncelleştirmelerini kullanır; bu güncelleştirmeler her Windows Defender Virüsten Koruma güncelleştirilir.

> [!NOTE]
> Çevrimdışı taramayı çalıştırmadan önce Microsoft Defender AV korumasını güncelleştirmeyi denemeniz gerekir. Grup ilkesi ile güncelleştirmeyi zorlar veya ancak normalde uç noktalara güncelleştirmeler dağıtır veya en son koruma güncelleştirmelerini Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi'nden el ile [indirip yükleyebilirsiniz](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Daha fazla [bilgi Microsoft Defender Virüsten Koruma için Güvenlik zekası güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md) başlığına bakın.

## <a name="usage-scenarios"></a>Kullanım senaryoları

Sürüm Windows 10 1607'de çevrimdışı taramayı el ile zorlayabilirsiniz. Alternatif olarak, Windows Defender uç noktanın Microsoft Defender Çevrimdışı gerektiğini belirlerse, uç nokta üzerinde kullanıcıdan istenir.

Uç noktalarınızı yönetmek için kullanıyorsanız, çevrimdışı tarama Microsoft Endpoint Manager bu taramayı gerçekleştirecek olan kullanıcıda da bu bilgi ortaya çıkar.

Bilgi istemi, aşağıdakine benzer bir bildirim aracılığıyla ortaya çıkabilir:

:::image type="content" source="../../media/notification.png" alt-text="Çalışma bildirimi Microsoft Defender Çevrimdışı" lightbox="../../media/notification.png":::

Kullanıcıya müşteri içinde de Windows Defender.

Daha Configuration Manager'te, İzleme ve Genel Bakış 'a > Genel Bakış'a giderek **uç noktaların > > Endpoint Protection Durumunu > System Center Endpoint Protection tanımlayabilirsiniz**.

Microsoft Defender Çevrimdışı taramaları, Çevrimdışı tarama **gerektiğinde Kötü** amaçlı yazılım düzeltme **durumu altında belirtilmiştir**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Durum taramasının göstergesi Microsoft Defender Çevrimdışı" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Bildirimleri yapılandırma

Microsoft Defender Çevrimdışı, diğer Microsoft Defender AV bildirimleriyle aynı ilke ayarında yapılandırılır.

Bu konu başlığı altında yer alan Windows Defender fazla bilgi için Uç [noktalar konusunda görünen bildirimleri yapılandırma başlığına](configure-notifications-microsoft-defender-antivirus.md) bakın.

## <a name="run-a-scan"></a>Tarama çalıştırma

> [!IMPORTANT]
> Bu Microsoft Defender Çevrimdışı, tüm dosyaları kaydetmeye ve çalışan programları kapatmaya devam etmek için kullanılır. Hızlı Microsoft Defender Çevrimdışı çalıştırmak yaklaşık 15 dakika sürer. Tarama tamamlandığında uç noktayı yeniden başlatacak. Tarama her zamanki çalışma ortamının dışında Windows yapılır. Kullanıcı arabirimi, kullanıcı arabirimi tarafından gerçekleştirilen normal taramadan Windows Defender. Tarama tamamlandıktan sonra, uç nokta yeniden başlatılır ve Windows şekilde yük olur.

Aşağıdakini Microsoft Defender Çevrimdışı tarama yapabilirsiniz:

- PowerShell
- Windows Yönetim Aracı (WMI)
- Windows Güvenliği uygulaması



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>PowerShell cmdlet'lerini kullanarak çevrimdışı tarama çalıştırma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Start-MpWDOScan
```

[PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve çalıştırma hakkında daha fazla bilgi Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Çevrimdışı Windows çalıştırmak için YÖNETICI Yönergesi (WMI) kullanma

Çevrimdışı [**MSFT_MpWDOScan çalıştırmak**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) için Sınıf Sınıfını kullanın.

Aşağıdaki WMI komut dosyası parçacığı, Microsoft Defender Çevrimdışı bir tarama çalıştırın; bu da uç noktanın yeniden başlatılmasına, çevrimdışı taramanın çalışmasına ve ardından yeniden başlatarak Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Daha fazla bilgi için aşağıdakilere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Windows Defender Security uygulamasını kullanarak çevrimdışı taramayı çalıştırma

1. Görev Windows Güvenliği kalkan simgesine tıklayarak veya görev çubuğundaki kalkan simgesi için başlangıç menüsünde arama **Bulut için Defender.**

2. Virüs koruması **& kutucuğuna** (veya sol menü çubuğundaki kalkan simgesine) ve ardından **Gelişmiş tarama etiketine** tıklayın:

3. **Taramayı Microsoft Defender Çevrimdışı şimdi** **tara'ya tıklayın**.

    > [!NOTE]
    > Windows 10 sürüm 1607'de, çevrimdışı tarama **Windows Ayarlar** **Update &** \> güvenlik Windows Defender  \> altında veya Windows Defender istemcisinde çalıştırabilirsiniz.

## <a name="review-scan-results"></a>Tarama sonuçlarını gözden geçirme

Microsoft Defender Çevrimdışı tarama sonuçları, uygulamanın [Tarama geçmişi Windows Güvenliği listelenir](microsoft-defender-security-center-antivirus.md).

## <a name="related-articles"></a>İlgili makaleler

- [Tarama ve düzeltme sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
