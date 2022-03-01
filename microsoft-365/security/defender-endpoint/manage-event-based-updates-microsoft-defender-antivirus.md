---
title: Belirli Microsoft Defender Virüsten Koruma sonra güncelleştirmeleri uygulama
description: Bulut teslim Microsoft Defender Virüsten Koruma raporları aldıktan sonra güvenlik zekası güncelleştirmelerini nasıl uygulanacağı yönetin.
keywords: güncelleştirmeler, koruma, güncelleştirmeleri zorlar, olaylar, başlangıç, en son bildirimleri denetleme, bildirimler
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: c99e4e085de32ac4e7ec77a2155182f1a930d432
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997572"
---
# <a name="manage-event-based-forced-updates"></a>Olay tabanlı zorunlu güncelleştirmeleri yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma, örneğin başlangıçta veya bulut teslimi koruma hizmetten belirli raporlar aldıktan sonra bazı olaylardan sonra güncelleştirmelerin mi (yoksa oluşmalı mı) olduğunu belirlemenize olanak sağlar.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Tarama çalıştırmadan önce koruma güncelleştirmelerini denetleme

Zamanlanmış bir Microsoft Endpoint Configuration Manager çalıştırmadan önce koruma güncelleştirmelerini denetlemeye ve indirmeye zorlamak için MICROSOFT DEFENDER VIRÜSTEN KORUMA, Grup İlkesi, PowerShell cmdlet'leri ve WMI'yı kullanabilirsiniz.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Tarama çalıştırmadan önce koruma güncelleştirmelerini denetlemek için Yapılandırma Yöneticisi'ni kullanma

1. Microsoft Endpoint Manager konsolunuzun üzerinde, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkelerini açın (sol tarafta gezinti bölmesinde Varlıklar  ve Uyumluluk'a tıklayın,  \>  \> ardından ağacı Genel Bakış veya Kötü Amaçlı Yazılım İlkeleri'ne Endpoint Protection **tıklayın**)

2. Zamanlanmış **taramalar bölümüne gidin** ve **taramayı çalıştırmadan önce en son güvenlik zekası güncelleştirmelerini denetlemeyi Evet olarak** **ayarlayın**.

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Tarama çalıştırmadan önce koruma güncelleştirmelerini denetlemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. Tarama için bileşenleri **Windows için** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

5. Zamanlanmış **taramayı çalıştırmadan önce en son virüs ve casus yazılım tanımlarını denetleme'ye çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Tarama çalıştırmadan önce koruma güncelleştirmelerini denetlemek için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Taramayı Windows önce koruma güncelleştirmelerini denetlemek için Yönetim Yönergesi'Windows (WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
CheckForSignaturesBeforeRunningScan
```

Daha fazla bilgi için [WMIv2 API'lerini Windows Defender bkz](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Başlangıçtaki koruma güncelleştirmelerini denetleme

Grup İlkesi'i kullanarak, makine Microsoft Defender Virüsten Koruma güncelleştirmelerini denetlemeye ve indirmeye zorlamak için kullanabilirsiniz.

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. Security Intelligence **Güncelleştirmeleri'Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin**.

5. Başlatma sırasında en **son virüs ve casus yazılım tanımlarını denetleme'ye çift tıklayın** ve Seçeneği Etkin olarak **ayarlayın**.

6. **Tamam**'a tıklayın.

Ayrıca, grup ilkesi çalışmasa bile, başlangıçta güncelleştirmeleri Microsoft Defender Virüsten Koruma için Grup İlkesi, PowerShell veya WMI'ya da Microsoft Defender Virüsten Koruma yapılandırabilirsiniz.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Grup İlkesi kullanarak güncelleştirmeler Microsoft Defender Virüsten Koruma güncelleştirmeleri indirme

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. Security Intelligence **Güncelleştirmeleri'Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin**.

5. Başlatma sırasında güvenlik **zekası güncelleştirmesini başlat'a çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>PowerShell cmdlet'lerini kullanarak güncelleştirmeler Microsoft Defender Virüsten Koruma güncelleştirmeleri indirme

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Daha fazla bilgi için, [powershell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanarak Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/index) kullanarak PowerShell'i Microsoft Defender Virüsten Koruma.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>YENI Windows güncelleştirmeleri indirmek için YÖNETICI Yönetim Yönergesi'Microsoft Defender Virüsten Koruma (WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Daha fazla bilgi için [WMIv2 API'lerini Windows Defender bkz](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Bulut teslim edilen korumaya göre özel koruma değişikliklerine izin verme

Microsoft Defender AV, bulut teslimi korumasını temel alarak korumada değişiklik yapabilirsiniz. Bu tür değişiklikler normal veya zamanlanmış koruma güncelleştirmelerinin dışında oluşabilir.

Bulut teslimi korumasını etkinleştirdiyseysiniz, Microsoft Defender AV buluta şüpheli olan dosyaları Windows Defender gönderir. Bulut hizmeti dosyanın kötü amaçlı olduğunu raporlarsa ve dosya son koruma güncelleştirmesinde algılanırsa, Microsoft Defender AV'yi bu koruma güncelleştirmesini otomatik olarak alacak şekilde yapılandırmak için Grup İlkesi kullanabilirsiniz. Diğer önemli koruma güncelleştirmeleri de uygulanabilir.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Buluta teslim edilen koruma temel alınarak son güncelleştirmeleri otomatik olarak indirmek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. Security Intelligence **Güncelleştirmeleri'Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin**.

5. **Microsoft MAPS raporlarına dayalı olarak gerçek zamanlı güvenlik** zekası güncelleştirmelerine izin ver'e çift tıklayın ve seçeneği Etkin olarak **ayarlayın**. Sonra **Tamam**'a tıklayın.

6. **Microsoft MAPS'a tanım tabanlı raporları devre dışı bırakmak için bildirimlere izin ver** ve Etkin seçeneğini **ayarlayın**. Sonra **Tamam**'a tıklayın.

> [!NOTE]
> **Bildirimlerin tanım tabanlı raporları devre dışı bırakmasına izin ver seçeneği** , Microsoft MAPS'ın hatalı pozitif raporlara neden olduğu bilinen tanımları devre dışı bırakmasına olanak sağlar. Bu işlevin çalışması için bilgisayarınızı Microsoft MAPS'a katılacak şekilde yapılandırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
