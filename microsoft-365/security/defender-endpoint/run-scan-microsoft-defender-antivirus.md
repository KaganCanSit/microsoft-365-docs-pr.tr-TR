---
title: Microsoft Defender Virüsten Koruma'de isteğe bağlı taramaları çalıştırma ve özelleştirme
description: PowerShell, Windows Yönetim Araçları veya Windows Güvenliği uygulamasıyla uç noktalarda tek tek kullanarak isteğe bağlı taramaları çalıştırma ve yapılandırma
keywords: tarama, isteğe bağlı, dos, intune, anlık tarama
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: bca0e953b759f447e8274e8766cbcada273eb614
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788886"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>İsteğe bağlı Microsoft Defender Virüsten Koruma taramalarını yapılandırın ve çalıştırın

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Tek tek uç noktalarda isteğe bağlı tarama çalıştırabilirsiniz. Bu taramalar hemen başlar ve tarama için konum veya tür gibi parametreler tanımlayabilirsiniz. Taramayı çalıştırdığınızda üç tür arasından seçim yapabilirsiniz: Hızlı tarama, tam tarama ve özel tarama. Çoğu durumda hızlı tarama kullanın. Hızlı tarama, kayıt defteri anahtarları ve bilinen Windows başlangıç klasörleri gibi sistemle başlamak için kötü amaçlı yazılımların kaydedilebileceği tüm konumları gözden geçirin.

Her zaman açık, gerçek zamanlı koruma ile birlikte, dosyalar açıldığında ve kapatıldığında incelenir ve bir kullanıcı bir klasöre her gittiği zaman hızlı tarama, sistem ve çekirdek düzeyinde kötü amaçlı yazılımlarla başlayan kötü amaçlı yazılımlara karşı güçlü koruma sağlamaya yardımcı olur. Çoğu durumda hızlı tarama yeterlidir ve zamanlanmış veya isteğe bağlı taramalar için önerilen seçenektir. [Tarama türleri hakkında daha fazla bilgi edinin](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma, yerel tarama gerçekleştirirken [LocalSystem](/windows/win32/services/localsystem-account) hesabı bağlamında çalışır. Ağ taramaları için cihaz hesabının bağlamını kullanır. Etki alanı cihaz hesabının paylaşıma erişmek için uygun izinleri yoksa tarama çalışmaz. Cihazın erişim ağ paylaşımı için izinlere sahip olduğundan emin olun.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Tarama çalıştırmak için Microsoft Endpoint Manager kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Uç nokta güvenliği** \> **Virüsten Koruma'yı** seçin.

3. Sekmeler listesinde, **iyi durumda olmayan uç noktaları Windows 10 veya iyi durumda olmayan uç noktaları** **Windows 11** seçin.

4. Sağlanan eylemler listesinden **Hızlı Tarama** (önerilen) veya **Tam Tarama'yı** seçin.

   [![Windows 10 iyi durumda olmayan uç noktalar sekmesindeki tarama seçenekleri.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Tarama çalıştırmak için Microsoft Endpoint Manager kullanma hakkında daha fazla bilgi için bkz. [Kötü amaçlı yazılımdan koruma ve güvenlik duvarı görevleri: İsteğe bağlı tarama gerçekleştirme](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Tarama çalıştırmak için mpcmdrun.exe komut satırı yardımcı programını kullanma

Aşağıdaki `-scan` parametreyi kullanın:

```console
mpcmdrun.exe -scan -scantype 1
```

Tam tarama başlatma veya yol tanımlama dahil olmak üzere aracın ve ek parametrelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için mpcmdrun.exe komut satırı aracını kullanma](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>Tarama çalıştırmak için Microsoft Intune kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. Kenar çubuğundan **Cihazlar** \> **Tüm Cihazlar'ı** seçin ve taramak istediğiniz cihazı seçin.

3. **... öğesini seçin. Daha fazla**. Seçeneklerden **Hızlı Tarama** (önerilen) veya **Tam Tarama'yı** seçin.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Tarama çalıştırmak için Windows Güvenliği uygulamasını kullanma

Tek tek uç [noktalarda tarama](microsoft-defender-security-center-antivirus.md) çalıştırma yönergeleri için bkz. Windows Güvenliği uygulamasında tarama çalıştırma.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Tarama çalıştırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Start-MpScan
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Tarama çalıştırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

**MSFT_MpScan** sınıfının [**Start** yöntemini](/previous-versions/windows/desktop/defender/start-msft-mpscan) kullanın.

İzin verilen parametreler hakkında daha fazla bilgi için bkz. [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)