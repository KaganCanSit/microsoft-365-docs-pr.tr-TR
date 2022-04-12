---
title: Belirli olaylardan sonra Microsoft Defender Virüsten Koruma güncelleştirmeleri uygulama
description: Microsoft Defender Virüsten Koruma başlatma veya bulut teslim algılama raporlarını aldıktan sonra güvenlik bilgileri güncelleştirmelerini nasıl uygulayacağı yönetin.
keywords: güncelleştirmeler, koruma, güncelleştirmeleri zorlama, olaylar, başlatma, en son bildirimleri denetleme
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
ms.openlocfilehash: 8ad9a5c6cd1a79152640bb153f8a130ecdd29362
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789502"
---
# <a name="manage-event-based-forced-updates"></a>Olay tabanlı zorunlu güncelleştirmeleri yönetin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma, güncelleştirmelerin başlangıçta veya bulut tarafından teslim edilen koruma hizmetinden belirli raporlar alındıktan sonra belirli olaylardan sonra gerçekleşmesi (veya olmaması) gerekip gerekmediğini belirlemenize olanak tanır.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Taramayı çalıştırmadan önce koruma güncelleştirmelerini denetleme

Microsoft Endpoint Configuration Manager, grup ilkesi, PowerShell cmdlet'lerini ve WMI'yı kullanarak Microsoft Defender Virüsten Koruma zamanlanmış taramayı çalıştırmadan önce koruma güncelleştirmelerini denetlemeye ve indirmeye zorlayabilirsiniz.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Taramayı çalıştırmadan önce koruma güncelleştirmelerini denetlemek için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'a** tıklayın, sonra ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Zamanlanmış taramalar** bölümüne gidin ve **taramayı çalıştırmadan önce en son güvenlik bilgileri güncelleştirmelerini denetle** seçeneğini **Evet** olarak ayarlayın.

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Taramayı çalıştırmadan önce koruma güncelleştirmelerini denetlemek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **Tarama** **Microsoft Defender Virüsten Koruma bileşenleri** \>  \> Windows için ağacı genişletin.

5. **Zamanlanmış tarama çalıştırmadan önce en son virüs ve casus yazılım tanımlarını denetle'ye** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Tarama çalıştırmadan önce koruma güncelleştirmelerini denetlemek için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/index) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Taramayı çalıştırmadan önce koruma güncelleştirmelerini denetlemek için Windows Yönetim Yönergesi'ni (WMI) kullanın

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
CheckForSignaturesBeforeRunningScan
```

Daha fazla bilgi için bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Başlangıçta koruma güncelleştirmelerini denetleme

makine başlatıldığında Microsoft Defender Virüsten Koruma koruma güncelleştirmelerini denetlemeye ve indirmeye zorlamak için grup ilkesi kullanabilirsiniz.

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **Güvenlik Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

5. **Başlangıçta en son virüs ve casus yazılım tanımlarını denetle'ye** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.

6. **Tamam**'a tıklayın.

grup ilkesi, PowerShell veya WMI kullanarak da Microsoft Defender Virüsten Koruma çalışmadığında bile başlangıçta güncelleştirmeleri denetleyecek şekilde yapılandırabilirsiniz.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Microsoft Defender Virüsten Koruma olmadığında güncelleştirmeleri indirmek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **Güvenlik Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

5. **Başlangıçta güvenlik bilgileri güncelleştirmesini başlat'a** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Microsoft Defender Virüsten Koruma olmadığında güncelleştirmeleri indirmek için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma yönetmek için PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma ve Microsoft Defender Virüsten Koruma ile PowerShell'i kullanma hakkında daha fazla bilgi için [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Microsoft Defender Virüsten Koruma olmadığında güncelleştirmeleri indirmek için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Daha fazla bilgi için bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Bulut tabanlı korumayı temel alan korumada geçici değişikliklere izin ver

Microsoft Defender AV, bulut tabanlı korumayı temel alarak korumasında değişiklik yapabilir. Bu tür değişiklikler normal veya zamanlanmış koruma güncelleştirmeleri dışında gerçekleşebilir.

Bulut tabanlı korumayı etkinleştirdiyseniz, Microsoft Defender AV şüpheli olduğu dosyaları Windows Defender buluta gönderir. Bulut hizmeti dosyanın kötü amaçlı olduğunu bildirirse ve dosya son koruma güncelleştirmesinde algılanırsa, grup ilkesi kullanarak Microsoft Defender AV'yi bu koruma güncelleştirmesini otomatik olarak alacak şekilde yapılandırabilirsiniz. Diğer önemli koruma güncelleştirmeleri de uygulanabilir.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Bulut tabanlı korumayı temel alan son güncelleştirmeleri otomatik olarak indirmek için grup ilkesi kullanın

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **Güvenlik Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

5. **Microsoft MAPS raporlarına göre gerçek zamanlı güvenlik bilgileri güncelleştirmelerine izin ver'e** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Sonra **Tamam**'a tıklayın.

6. **Tanım tabanlı raporları Microsoft MAPS'e devre dışı bırakmak için bildirimlere izin verin** ve seçeneği **Etkin** olarak ayarlayın. Sonra **Tamam**'a tıklayın.

> [!NOTE]
> **Tanım tabanlı raporları devre dışı bırakmak için bildirimlere izin ver** , Microsoft MAPS'in hatalı pozitif raporlara neden olduğu bilinen tanımları devre dışı bırakmasına olanak tanır. Bu işlevin çalışması için bilgisayarınızı Microsoft MAPS'e katılacak şekilde yapılandırmanız gerekir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
