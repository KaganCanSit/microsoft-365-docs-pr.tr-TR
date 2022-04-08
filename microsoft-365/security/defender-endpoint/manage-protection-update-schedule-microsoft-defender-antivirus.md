---
title: Microsoft Defender Virüsten Koruma koruma güncelleştirmelerini zamanlama
description: Koruma güncelleştirmelerinin indirileceği gün, saat ve aralığı zamanlama
keywords: güncelleştirmeler, güvenlik temelleri, güncelleştirmeleri zamanlama
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 566b79c534ed13bbdf5f1d66e6ffdbc5ab43a5b2
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715000"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Koruma güncelleştirmelerinin indirilme ve kullanılma zamanlamasını yönetin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma güncelleştirmeleri ne zaman arayıp indirmesi gerektiğini belirlemenizi sağlar.

Uç noktalarınız için güncelleştirmeleri şu şekilde zamanlayabilirsiniz:

- Koruma güncelleştirmelerini denetlemek için haftanın gününü belirtme
- Koruma güncelleştirmelerinin denetlenme aralığını belirtme
- Koruma güncelleştirmelerinin denetlenme zamanını belirtme

Ayrıca, her uç noktanın koruma güncelleştirmelerini denetleyebileceği ve indirebileceği saatleri de rastgele ayarlayabilirsiniz. Daha fazla bilgi için [Taramaları zamanlama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) konusuna bakın.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zamanlamak için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'a** tıklayın, sonra ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Güvenlik bilgileri güncelleştirmeleri** bölümüne gidin.

3. Güncelleştirmeleri belirli bir zamanda denetlemek ve indirmek için:
      1. **Belirli bir aralıkta Endpoint Protection güvenlik bilgileri güncelleştirmelerini denetle...** değerini **0** olarak ayarlayın.
      2. **Endpoint Protection güvenlik bilgileri güncelleştirmelerini her gün denetle'yi güncelleştirmelerin** denetlenmesi gereken zamana ayarlayın.
      3
4. Güncelleştirmeleri sürekli aralıklarla denetlemek ve indirmek **için, Endpoint Protection güvenlik bilgileri güncelleştirmelerini belirli bir aralıkta denetle...** değerini güncelleştirmeler arasında gerçekleşmesi gereken saat sayısına ayarlayın.

5. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zamanlamak için grup ilkesi kullanma

> [!IMPORTANT]
> Varsayılan olarak, "SignatureScheduleDay" "8" olarak, "SignatureUpdateInterval" ise "0" olarak ayarlandığından Microsoft Defender Virüsten Koruma koruma güncelleştirmelerini zamanlamaz.
Bu ayarların etkinleştirilmesi bu varsayılanı geçersiz kılar.

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **İmza Yönetim Bilgileri Güncelleştirmeleri** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin ve aşağıdaki ayarları yapılandırın:

    1. **Güvenlik bilgileri güncelleştirmelerini denetlemek için Haftanın gününü belirtin ayarına** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Güncelleştirmeleri denetlemek için haftanın gününü girin. **Tamam**'a tıklayın.
    2. **Güvenlik bilgileri güncelleştirmelerini denetlemek için aralığı belirtin ayarına** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Güncelleştirmeler arasındaki saat sayısını girin. **Tamam**'a tıklayın.
    3. **Güvenlik bilgileri güncelleştirmelerinin denetlenme zamanını belirtin ayarına** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Güncelleştirmelerin denetlenmesi gereken zamanı girin. Zaman, uç noktanın yerel saatini temel alır. **Tamam**'a tıklayın.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zamanlamak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zamanlamak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
