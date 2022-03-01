---
title: Güncel değil uç noktalarına Microsoft Defender AV koruma güncelleştirmelerini uygulama
description: Bir süre güncelleştirilmiş uç noktalar için güncelleştirmelerin ne zaman ve nasıl uygulanması gerektiğini tanımlayın.
keywords: güncelleştirmeler, koruma, güncel olmayan, güncel olmayan, eski, yakalama
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: a708bf6ef34767b338c40cf8004e4c497658fc36
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998068"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Güncel Microsoft Defender Virüsten Koruma uç noktaların güncelleştirmelerini ve taramalarını yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma, uç noktanın güncelleştirmeyi ne kadar süreyle önlediğini veya uç noktanın kendisini güncelleştirmek ve taramak için gerekli olmadan önce kaç taramayı kaçıra geçeyle ilgili olduğunu tanımlamanıza olanak sağlar. Bu özellikle, cihazların çoğunlukla şirket veya dış ağa bağlı olduğu ortamlarda veya günlük olarak kullanılmadan kullanılan ortamlarda kullanışlıdır.

Örneğin, belirli bir bilgisayarı kullanan çalışan üç gün boyunca tatilde olur ve bu süre boyunca kendi bilgisayarınızda oturum açmaz.

Kullanıcı çalışmaya döndüğünde ve kendi bilgisayarınızda oturum açtığında, Microsoft Defender Virüsten Koruma en son koruma güncelleştirmelerini hemen kontrol edin ve indirin, sonra da bir tarama çalıştırın.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Bir süredir güncelleştirilmiş uç noktalar için catch-up protection güncelleştirmeleri ayarlama

Daha Microsoft Defender Virüsten Koruma bir süre için koruma güncelleştirmelerini indirmezse, sonraki oturum açma sırasında en son güncelleştirmeyi otomatik olarak kontrol etmek ve indirmek üzere kurabilirsiniz. Başlangıçta otomatik güncelleştirme indirmeleri genel [olarak devre dışı bırakıldı ise bu yararlı olur](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Yakalama koruması güncelleştirmelerini yapılandırmak için Yapılandırma Yöneticisi'ni kullanma

1. Microsoft Endpoint Manager konsolunuzun üzerinde, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkelerini açın (sol tarafta gezinti bölmesinde Varlıklar  ve Uyumluluk'a tıklayın,  \>  \> ardından ağacı Genel Bakış veya Kötü Amaçlı Yazılım İlkeleri'ne Endpoint Protection **tıklayın**)

2. Güvenlik zekası **güncelleştirmeleri bölümüne** gidin ve aşağıdaki ayarları yapılandırabilirsiniz:

    1. İstemci **bilgisayar birbirini takip eden ikiden fazla zamanlanmış** güncelleştirme için Evet olarak çevrimdışıysa, güvenlik zekası güncelleştirmesini zorla **güncelleştirmesi ayarlayın**.
    2. Configuration  **Manager,** güvenlik zekası güncelleştirmeleri için kaynak olarak kullanılıyorsa... için, koruma güncelleştirmelerinin Configuration Manager tarafından teslim edilen süre önce güncel kabul edilecek saatleri belirtin. Bu, tanımlanan geri dönüş kaynağı sırasına bağlı olarak bir sonraki güncelleştirme [konumunun kullanılmaya neden olur](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Göz alıcı güncelleştirme özelliğini etkinleştirmek ve yapılandırmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. İmza **Güncelleştirmeleri'Windows bileşenleri > Microsoft Defender Virüsten Koruma > ağacı genişletin**.

5. Bir yakalama güvenlik **zekası güncelleştirmesi için** gerekli olan gün sayısını tanımla ayarına çift tıklayın ve seçeneği Etkin olarak **ayarlayın**. Microsoft Defender AV'nin en son koruma güncelleştirmesini denetlemesini ve indirmesini istediğiniz gün sayısını girin.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Yakala koruma güncelleştirmelerini yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

[PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve çalıştırma hakkında daha fazla bilgi Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Yakalama Windows güncelleştirmelerini yapılandırmak için KULLANıCı Yönetimi Yönergesi'ne (WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
SignatureUpdateCatchupInterval
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Korumanın güncel olduğu bildirmeden önceki gün sayısını ayarlama

Ayrıca, korumanın eski veya güncel Microsoft Defender Virüsten Koruma kaç gün sonra olduğunu da belirtsiniz. Belirtilen sayıda gün sonra, istemci kendini güncel değil olarak rapor eder ve bilgisayar kullanıcıya bir hata gösterir. Ayrıca, WSUS veya Microsoft Update Microsoft Defender Virüsten Koruma i ilk kaynak olarak ayardikten sonra mmPC'nin ikincil kaynak olarak [](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)kullanımı gibi durumlarda olduğu gibi, başka kaynaklardan bir güncelleştirme indirmeye çalışmanız da (tanımlı geri dönüş kaynağı sırasına bağlı olarak) neden olabilir.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Korumanın güncel olduğu kabul edilen tarihten önceki gün sayısını belirtmek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. İmza **Güncelleştirmeleri'Windows bileşenleri > Microsoft Defender Virüsten Koruma > ağacı genişletin** ve aşağıdaki ayarları yapılandırabilirsiniz:

    1. Casus yazılım **tanımlarının güncel kabul edilen gün sayısını tanımla'ya çift tıklayın ve** Seçeneği Etkin olarak **ayarlayın**. Microsoft Defender AV'nin casus yazılım olarak değerlendirisini istediğiniz gün sayısını girin Güvenlik zekası güncel değil.

    2. **Tamam**'a tıklayın.

    3. Virüs tanımlarının **güncel kabul edilen gün sayısını tanımla'ya** çift tıklayın ve Seçeneği Etkin olarak **ayarlayın**. Microsoft Defender AV'nin virüs güvenlik zekası'nın güncel olmayan olarak değerlendirisini istediğiniz gün sayısını girin.

    4. **Tamam**'a tıklayın.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Bir süredir taranmış uç noktaları yakalama taramaları ayarlama

Bu taramayı zorlamadan önce atlanan art arda Microsoft Defender Virüsten Koruma tarama sayısını ayarlayın.

Bu özelliği etkinleştirme işlemi şöyledir:

1. En az bir zamanlanmış tarama ayarlayın (Tarama zamanlama [başlığına](scheduled-catch-up-scans-microsoft-defender-antivirus.md) bakın).
2. Yakalama tarama özelliğini etkinleştirin.
3. Yakalama taraması öncesinde atlanacak tarama sayısını tanımlayın.

Bu özellik hem tam hem de hızlı taramalarda etkinleştirilebilir.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Göz alıcı tarama özelliğini etkinleştirmek ve yapılandırmak için Grup İlkesi kullanma

1. En az bir zamanlanmış tarama ayarlayın.

2. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

4. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

5. Tarama için bileşenleri **Windows için > Microsoft Defender Virüsten Koruma > ve** aşağıdaki ayarları yapılandırabilirsiniz:

    1. Zamanlanmış hızlı taramaları ayarlarsanız, Hızlı taramayı aç ayarını  çift tıklatın ve seçeneği Etkin olarak **ayarlayın**.
    2. Zamanlanmış tam taramaları ayarladıysanız, Göz alıcı tam  taramayı aç ayarını çift tıklatın ve seçeneği Etkin olarak **ayarlayın**. **Tamam**'a tıklayın.
    3. Yakalama **taramasının zorunlu olduğu gün** sayısını tanımla ayarına çift tıklayın ve seçeneği Etkin olarak **ayarlayın**.
    4. Kullanıcı bir sonraki PC'de oturum açtığında, taramanın otomatik olarak çalıştırılamadan önce kaç tarama çalıştırıla olacağını girin. Çalıştırlanan taramanın türü, Zamanlanmış tarama için kullanmak üzere tarama türünü **belirtme (Tarama** zamanlama [başlığına](scheduled-catch-up-scans-microsoft-defender-antivirus.md) bakın) ile belirlenir. **Tamam**'a tıklayın.

> [!NOTE]
> Grup İlkesi ayar başlığı, gün sayısını ifade eder. Ancak bu ayar, taramanın çalıştırılamadan önce günlere değil tarama sayısına uygulanır.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Yakala taramalarını yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Microsoft Defender Virüsten Koruma ile PowerShell'in nasıl kullanıldığı hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma'ı yönetmek için [PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma ve Defender Virüsten Koruma [cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Kayıt Windows (WMI) kullanarak yakalama taramalarını yapılandırma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Göz alıcı taramaları yapılandırmak için Yapılandırma Yöneticisi'ni kullanma

1. Microsoft Endpoint Manager konsolunuzun üzerinde, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkelerini açın (sol tarafta gezinti bölmesinde Varlıklar  ve Uyumluluk'a tıklayın,  \>  \> ardından ağacı Genel Bakış veya Kötü Amaçlı Yazılım İlkeleri'ne Endpoint Protection **tıklayın**)

2. Zamanlanmış **taramalar bölümüne gidin** ve **İstemci bilgisayar çevrimdışıysa, seçili tarama türünü taramaya zorla... seçeneğine** **Evet'e gidin**.

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="related-articles"></a>İlgili makaleler

- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
