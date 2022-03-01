---
title: Koruma Microsoft Defender Virüsten Koruma zamanlama
description: Koruma güncelleştirmelerinin ne zaman indirilecek gün, saat ve zaman aralığını zamanlama
keywords: güncelleştirmeler, güvenlik taban çizgilerini, güncelleştirmeleri zamanlama
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
ms.openlocfilehash: fa67ff12ecfc2fb97bbc50642a5d7db99df91819
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997349"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Koruma güncelleştirmelerinin ne zaman indirildikten ve uygulanmalıdır? zamanlamayı yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma güncelleştirmeleri ne zaman bakarak indireceklerini belirlemenizi sağlar.

Uç noktalarınız için güncelleştirmeleri şu şekilde zamanabilirsiniz:

- Koruma güncelleştirmelerini denetleme için haftanın günlerini belirtme
- Koruma güncelleştirmelerini denetleme aralığını belirtme
- Koruma güncelleştirmelerini denetleme zamanı belirtme

Ayrıca, her uç noktanın koruma güncelleştirmelerini kontroldiği ve indirdiği saatleri rastgele de sıralı hale çekebilirsiniz. Daha fazla [bilgi için Tarama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) zamanlama başlığına bakın.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zaman etmek için Yapılandırma Yöneticisi'ni kullanma

1. Microsoft Endpoint Manager konsolunuzun üzerinde, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkelerini açın (sol tarafta gezinti bölmesinde Varlıklar  ve Uyumluluk'a tıklayın,  \>  \> ardından ağacı Genel Bakış veya Kötü Amaçlı Yazılım İlkeleri'ne Endpoint Protection **tıklayın**)

2. Güvenlik zekası **güncelleştirmeleri bölümüne** gidin.

3. Güncelleştirmeleri belirli bir zamanda kontrol etmek ve indirmek için:
      1. Güvenlik **zekası Endpoint Protection belirli bir zaman aralığında** 0 olarak ayarlayın.
      2. Her **gün Endpoint Protection için Güvenlik Zekası güncelleştirmelerini Endpoint Protection** güncelleştirmeleri denetlemesi gereken zamanda ayarlayın.
      3
4. Güncelleştirmeleri sürekli bir aralıkta kontrol etmek ve indirmek için, **güncelleştirmeler Endpoint Protection** arasındaki saat sayısına kadar belirli bir zaman aralığında güncelleştirmeleri denetlemeyi ve indirmeyi ayarlayın.

5. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zaman etmek için Grup İlkesi kullanma

> [!IMPORTANT]
> Varsayılan olarak, Microsoft Defender Virüsten Koruma herhangi bir zamanlanmış taramadan 15 dakika önce güncelleştirilen bir güncelleştirmeyi denetlemez. Bu ayarların etkinleştirilmesi, bu varsayılan ayarı geçersiz kılar.

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. İmza Zekası **Güncelleştirmeleri Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **ağacı genişletin** ve aşağıdaki ayarları yapılandırabilirsiniz:

    1. Güvenlik zekası **güncelleştirmelerini kontrol etmek için Haftanın günlerini belirtin ayarına çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. Güncelleştirmeleri kontrol etmek için haftanın günlerini girin. **Tamam**'a tıklayın.
    2. Güvenlik zekası **güncelleştirmelerini denetleme aralığını belirtin ayarına çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**. Güncelleştirmeler arasındaki saat sayısını girin. **Tamam**'a tıklayın.
    3. Güvenlik zekası **güncelleştirmelerini denetleme zamanı belirtin ayarına çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**. Güncelleştirmelerin denetlenir olduğu zamanı girin. Saat, uç noktanın yerel saatlerine göre uygulanır. **Tamam**'a tıklayın.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Koruma güncelleştirmelerini zamanlaması için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

[PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve çalıştırma hakkında daha fazla bilgi Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Koruma Windows zamanlaması için YÖNETIM Yönergesi(WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>İlgili makaleler

- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
