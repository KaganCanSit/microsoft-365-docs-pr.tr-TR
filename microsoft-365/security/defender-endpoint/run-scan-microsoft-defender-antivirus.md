---
title: E-postalarda isteğe bağlı taramaları çalıştırarak Microsoft Defender Virüsten Koruma
description: PowerShell kullanarak isteğe bağlı taramaları, Windows Araçları'Windows veya Windows Güvenliği uygulamasıyla uç noktaları çalıştırma ve yapılandırma
keywords: Scan, on-demand, dos, intune, instant scan
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
ms.openlocfilehash: 1f82fe410634ab92f7b403a30bcbcdf9a61634ba
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008106"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Taramalarda isteğe bağlı olarak Microsoft Defender Virüsten Koruma çalıştırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Tek tek uç noktalar üzerinde isteğe bağlı tarama çalıştırebilirsiniz. Bu taramalar hemen başlar ve tarama için konum veya tür gibi parametreler tanımlayabilirsiniz. Taramayı çalıştıracakken, üç tür arasından seçim kullanabilirsiniz: Hızlı tarama, tam tarama ve özel tarama. Çoğu durumda, hızlı tarama kullanın. Hızlı tarama, kayıt defteri anahtarları ve bilinen başlangıç klasörleri gibi sistemle başlamak üzere kötü amaçlı yazılım kaydedilmiş Windows tüm konumlara göz atıyor.

Her zaman açık, gerçek zamanlı korumayla birlikte, açıldığında ve kapatılan dosyaları gözden birleştiren ve kullanıcı bir klasöre her defa geldiğinde hızlı tarama, sistemle ve çekirdek düzeyinde kötü amaçlı yazılımla başlayan kötü amaçlı yazılımlara karşı güçlü koruma sağlar. Çoğu durumda, hızlı tarama yeterli olur ve zamanlanmış veya isteğe bağlı taramalar için önerilen seçenektir. [Tarama türleri hakkında daha fazla bilgi.](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan)

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma, yerel bir tarama yaparken [LocalSystem](/windows/win32/services/localsystem-account) hesabının bağlamında çalışır. Ağ taramaları için, cihaz hesabının bağlamını kullanır. Etki alanı cihaz hesabının paylaşıma erişmek için uygun izinleri yoksa, tarama çalışmaz. Cihazın erişim ağı paylaşımı üzerinde izinleri olduğundan emin olun.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Tarama Microsoft Endpoint Manager için Microsoft Endpoint Manager'i kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum aç'a gidin.

2. Uç nokta **güvenliği Virüsten Koruma'ya** \> **seçin**.

3. Sekme listesinde, uygun **olmayan uç Windows 10 seçin veya** uygun olmayan **11 Windows uç noktalarını seçin**.

4. Sağlanan eylemler listesinde Hızlı Tarama (önerilen) **veya** Tam **Tarama'ya tıklayın**.

   [![Sağlıksız uç Windows 10 tarama seçenekleri.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> E-posta veya Microsoft Endpoint Manager hakkında daha fazla bilgi için bkz. Kötü amaçlı yazılımdan koruma ve güvenlik duvarı görevleri[: isteğe bağlı tarama gerçekleştirme](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Tarama mpcmdrun.exe komut satırı yardımcı programını kullanma

Aşağıdaki parametreyi `-scan` kullanın:

```console
mpcmdrun.exe -scan -scantype 1
```

Aracı ve tam tarama başlatma ya da yolları tanımlama gibi ek parametreleri kullanma hakkında daha fazla bilgi için bkz. mpcmdrun.exe'yi yapılandırmak ve yönetmek için [mpcmdrun.exe komut satırı aracını Microsoft Defender Virüsten Koruma](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>Tarama Microsoft Intune için Microsoft Intune'i kullanma

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum aç'a gidin.

2. Kenar çubuğundan Tüm **Cihazlar'ı** \> **seçin** ve taramak istediğiniz cihazı seçin.

3. Şu seçeneği seçin **: ... Diğer.** Seçeneklerden Hızlı Tarama ( **önerilen) veya** Tam **Tarama'ya tıklayın**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Tarama Windows Güvenliği için Windows Güvenliği uygulamasını kullanma

Tek [tek uç noktalara tarama Windows Güvenliği için](microsoft-defender-security-center-antivirus.md) bkz. Windows Güvenliği içinde tarama çalıştırma.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Tarama çalıştırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Start-MpScan
```

powershell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma [ve Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) yapılandırmak ve çalıştırmak için [PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma.

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Tarama Windows için YÖNETICI Yönergesi (WMI) kullanma

Sınıf [**sınıfı için**](/previous-versions/windows/desktop/defender/start-msft-mpscan) Başlangıç **MSFT_MpScan** kullanın.

İzin verilen parametreler hakkında daha fazla bilgi için [WMIv2 API'Windows Defender bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)
