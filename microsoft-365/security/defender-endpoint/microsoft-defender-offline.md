---
title: Windows'da Microsoft Defender Çevrimdışı
description: doğrudan Windows Defenderin virustentorjunta uygulamasından Microsoft Defender Çevrimdışı kullanabilirsiniz. Ayrıca ağınızda nasıl dağıtılacağı da yönetilebilir.
keywords: tarama, defender, çevrimdışı
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
ms.openlocfilehash: ea7d316a7fc31724466dcd459ed72792cea817fd
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787698"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Microsoft Defender çevrimdışı tarama sonuçlarını gözden geçirin ve çalıştırın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Çevrimdışı, güvenilir bir ortamdan önyükleme yapmanıza ve tarama çalıştırmanıza olanak tanıyan bir kötü amaçlı yazılımdan koruma tarama aracıdır. Tarama normal Windows çekirdeğinin dışından çalıştırılarak ana önyükleme kaydını (MBR) etkileyen veya üzerine yazan virüsler ve rootkit'ler gibi Windows kabuğu atlama girişiminde bulunan kötü amaçlı yazılımları hedefleyebilir.

Kötü amaçlı yazılım bulaştığından şüpheleniyorsanız veya kötü amaçlı yazılım salgınından sonra uç noktanın kapsamlı bir şekilde temizlenip temizlenmediğini onaylamak istiyorsanız Microsoft Defender Çevrimdışı kullanabilirsiniz.

Windows 10 ve Windows 11 Microsoft Defender Çevrimdışı doğrudan [Windows Güvenliği uygulamasından](microsoft-defender-security-center-antivirus.md) tek tıklamayla çalıştırılabilir. Windows önceki sürümlerinde, kullanıcının önyüklenebilir medyaya Microsoft Defender Çevrimdışı yüklemesi, uç noktayı yeniden başlatması ve önyüklenebilir medyayı yüklemesi gerekiyordu.

## <a name="prerequisites-and-requirements"></a>önkoşullar ve gereksinimler

Windows 10 ve Windows 11 Microsoft Defender Çevrimdışı, Windows 10 ile aynı donanım gereksinimlerine sahiptir.

Windows 10 ve Windows 11 gereksinimleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [En düşük donanım gereksinimleri](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Donanım bileşeni yönergeleri](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Çevrimdışı ARM işlemcili makinelerde veya Windows Sunucu Stok Tutma Birimlerinde desteklenmez.

Uç noktadan Microsoft Defender Çevrimdışı çalıştırmak için kullanıcının yönetici ayrıcalıklarıyla oturum açması gerekir.

## <a name="microsoft-defender-offline-updates"></a>güncelleştirmeleri Microsoft Defender Çevrimdışı

Microsoft Defender Çevrimdışı uç noktada kullanılabilen en son koruma güncelleştirmelerini kullanır; Windows Defenderin virustentorjunta her güncelleştirildiğinde güncelleştirilir.

> [!NOTE]
> Çevrimdışı taramayı çalıştırmadan önce Microsoft Defender AV korumasını güncelleştirmeye çalışmanız gerekir. bir güncelleştirmeyi grup ilkesi ile zorlayabilirsiniz veya normalde uç noktalara güncelleştirme dağıtabilirsiniz ya da [Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi'nden](https://www.microsoft.com/security/portal/definitions/adl.aspx) en son koruma güncelleştirmelerini el ile indirip yükleyebilirsiniz.

Daha fazla bilgi için [Microsoft Defender Virüsten Koruma Güvenlik bilgileri güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md) konusuna bakın.

## <a name="usage-scenarios"></a>Kullanım senaryoları

Windows 10 sürüm 1607'de çevrimdışı taramayı el ile zorlayabilirsiniz. Alternatif olarak, Windows Defender Microsoft Defender Çevrimdışı çalıştırılması gerektiğini belirlerse, kullanıcıdan uç noktada istemde bulunur.

Çevrimdışı tarama gerçekleştirme gereksinimi, uç noktalarınızı yönetmek için kullanıyorsanız Microsoft Endpoint Manager'da da ortaya çıkar.

İstem, aşağıdakine benzer bir bildirim aracılığıyla gerçekleşebilir:

:::image type="content" source="../../media/notification.png" alt-text="Microsoft Defender Çevrimdışı çalıştırma bildirimi" lightbox="../../media/notification.png":::

Kullanıcıya Windows Defender istemcisinde de bildirim gönderilir.

Configuration Manager'da **İzleme > Genel Bakış > Güvenlik > Endpoint Protection Durumu > System Center Endpoint Protection Durumu'na** giderek uç noktaların durumunu belirleyebilirsiniz.

Microsoft Defender Çevrimdışı taramaları **Kötü amaçlı yazılım düzeltme durumu** altında **Çevrimdışı tarama gerekiyor** olarak belirtilir.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Microsoft Defender Çevrimdışı için tarama göstergesi" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Bildirimleri yapılandırma

Microsoft Defender Çevrimdışı bildirimleri, diğer Microsoft Defender AV bildirimleriyle aynı ilke ayarında yapılandırılır.

Windows Defender'deki bildirimler hakkında daha fazla bilgi için [Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md) konusuna bakın.

## <a name="run-a-scan"></a>Tarama çalıştırma

> [!IMPORTANT]
> Microsoft Defender Çevrimdışı kullanmadan önce tüm dosyaları kaydettiğinizden ve çalışan programları kapattığınıza emin olun. Microsoft Defender Çevrimdışı taramasının çalıştırılması yaklaşık 15 dakika sürer. Tarama tamamlandığında uç noktayı yeniden başlatır. Tarama, normal Windows işletim ortamı dışında gerçekleştirilir. Kullanıcı arabirimi, Windows Defender tarafından gerçekleştirilen normal taramadan farklı görünür. Tarama tamamlandıktan sonra uç nokta yeniden başlatılır ve Windows normal şekilde yüklenir.

Aşağıdakilerle bir Microsoft Defender Çevrimdışı taraması çalıştırabilirsiniz:

- PowerShell
- Windows Yönetim Araçları (WMI)
- Windows Güvenliği uygulaması



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Çevrimdışı tarama çalıştırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Start-MpWDOScan
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Çevrimdışı tarama çalıştırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Çevrimdışı tarama çalıştırmak için [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) sınıfını kullanın.

Aşağıdaki WMI betik parçacığı hemen bir Microsoft Defender Çevrimdışı taraması çalıştırır ve bu da uç noktanın yeniden başlatılmasına, çevrimdışı taramanın çalıştırılmasına ve ardından yeniden başlatılıp Windows önyüklemesine neden olur.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Daha fazla bilgi için aşağıdakilere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Çevrimdışı tarama çalıştırmak için Windows Defender Güvenlik uygulamasını kullanma

1. Görev çubuğundaki kalkan simgesine tıklayarak veya başlangıç menüsünde **Bulut için Defender arayarak Windows Güvenliği** uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğuna (veya sol menü çubuğundaki kalkan simgesine) ve ardından **Gelişmiş tarama** etiketine tıklayın:

3. **tarama Microsoft Defender Çevrimdışı** seçin ve **Şimdi tara'ya** tıklayın.

    > [!NOTE]
    > Windows 10 sürüm 1607'de çevrimdışı tarama, **Windows Ayarlar** **Güncelleştirme &** \> güvenlik \> **Windows Defender** altından veya Windows Defender istemcisinden çalıştırılabilir.

## <a name="review-scan-results"></a>Tarama sonuçlarını gözden geçirme

Microsoft Defender Çevrimdışı tarama sonuçları[, Windows Güvenliği uygulamasının Tarama geçmişi bölümünde](microsoft-defender-security-center-antivirus.md) listelenir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Taramaların ve düzeltmelerin sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
