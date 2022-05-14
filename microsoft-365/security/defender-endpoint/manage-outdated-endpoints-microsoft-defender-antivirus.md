---
title: Microsoft Defender AV koruma güncelleştirmelerini güncel dışı uç noktalara uygulama
description: Bir süredir güncelleştirilmemiş uç noktalar için güncelleştirmelerin ne zaman ve nasıl uygulanacağını tanımlayın.
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
ms.openlocfilehash: c6d8eeb23312f7e4775aacfcadc0d040fc3f0394
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415914"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Güncel olmayan uç nokta taramalarını ve Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma, bir uç noktanın bir güncelleştirmeyi ne kadar süreyle önleyebileceğini veya kendisini güncelleştirmek ve taramak için gerekli olmadan önce kaç taramayı kaçırabileceğini tanımlamanızı sağlar. Bu, özellikle cihazların genellikle bir şirket veya dış ağa bağlı olmadığı ortamlarda veya günlük olarak kullanılmayan cihazlarda kullanışlıdır.

Örneğin, belirli bir bilgisayarı kullanan bir çalışan üç gün boyunca moladadır ve bu süre boyunca bilgisayarında oturum açmaz.

Kullanıcı çalışmaya geri döndüğünde ve bilgisayarında oturum açtığında, Microsoft Defender Virüsten Koruma en son koruma güncelleştirmelerini hemen denetleyecek ve indirecek ve bir tarama çalıştıracaktır.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Bir süredir güncelleştirilmemiş uç noktalar için yakalama koruma güncelleştirmelerini ayarlama

Microsoft Defender Virüsten Koruma belirli bir süre için koruma güncelleştirmelerini indirmediyse, bir sonraki oturum açmada en son güncelleştirmeyi otomatik olarak denetleyip indirecek şekilde ayarlayabilirsiniz. [Başlangıçta otomatik güncelleştirme indirmelerini genel olarak devre dışı bırakmışsanız](manage-event-based-updates-microsoft-defender-antivirus.md) bu yararlı olur.

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'a** tıklayın, sonra ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Güvenlik bilgileri güncelleştirmeleri** bölümüne gidin ve aşağıdaki ayarları yapılandırın:

    1. **İstemci bilgisayar art arda ikiden fazla zamanlanmış güncelleştirme için çevrimdışıysa Güvenlik bilgileri güncelleştirmesini zorla** seçeneğini **Evet** olarak ayarlayın.
    2. Güvenlik **bilgileri güncelleştirmeleri için kaynak olarak Configuration Manager kullanılıyorsa...** için, Configuration Manager tarafından sunulan koruma güncelleştirmelerinin güncel olmayan olarak kabul edilmesi gereken saatleri belirtin. Bu, tanımlanan [geri dönüş kaynak sırasına](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) göre bir sonraki güncelleştirme konumunun kullanılmasına neden olur.

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Yakalama güncelleştirme özelliğini etkinleştirmek ve yapılandırmak için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **İmza Güncelleştirmeleri > Microsoft Defender Virüsten Koruma > bileşenleri Windows** için ağacı genişletin.

5. **Yakalama güvenlik bilgileri güncelleştirmesinin gerekli olduğu gün sayısını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender AV'nin en son koruma güncelleştirmesini denetlemesini ve indirmesini istediğiniz gün sayısını girin.

6. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
SignatureUpdateCatchupInterval
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Korumanın güncel olmayan olarak bildirildiği gün sayısını ayarlayın

Ayrıca, Microsoft Defender Virüsten Koruma korumasının eski veya güncel olmayan olarak kabul edildiği gün sayısını da belirtebilirsiniz. Belirtilen gün sayısından sonra istemci kendisini güncel değil olarak bildirir ve bilgisayarın kullanıcısına bir hata gösterir. Ayrıca, WSUS veya Microsoft Update ilk kaynak olarak ayarlandıktan sonra ikincil kaynak olarak MMPC kullanılırken Microsoft Defender Virüsten Koruma diğer kaynaklardan bir güncelleştirmeyi indirmeye (tanımlanan [geri dönüş kaynak sırasına](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) göre) neden olabilir.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Korumanın güncel olmayan olarak kabul edilmesinden önceki gün sayısını belirtmek için grup ilkesi kullanın

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **İmza Güncelleştirmeleri > Microsoft Defender Virüsten Koruma > bileşenleri Windows** için ağacı genişletin ve aşağıdaki ayarları yapılandırın:

    1. **Casus yazılım tanımlarının eski olduğu düşünülmeden önce geçmesi gereken gün sayısını tanımla'ya** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender AV'nin casus yazılım Güvenlik bilgileri'nin güncel olmasını göz önünde bulundurmasını istediğiniz gün sayısını girin.

    2. **Tamam**'a tıklayın.

    3. **Virüs tanımlarının eski olduğu düşünülmeden önce geçmesi gereken gün sayısını tanımla'ya** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender AV'nin virüs Güvenlik bilgileri'nin güncel olmasını göz önünde bulundurmasını istediğiniz gün sayısını girin.

    4. **Tamam**'a tıklayın.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Bir süredir taranmayan uç noktalar için yakalama taramaları ayarlama

Microsoft Defender Virüsten Koruma taramayı zorlamadan önce kaçırılacak ardışık zamanlanmış taramaların sayısını ayarlayabilirsiniz.

Bu özelliği etkinleştirme işlemi şu şekildedir:

1. En az bir zamanlanmış tarama ayarlayın ( [Taramaları zamanlama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) konusuna bakın).
2. Yakalama tarama özelliğini etkinleştirin.
3. Yakalama taraması gerçekleşmeden önce atlanacak tarama sayısını tanımlayın.

Bu özellik hem tam hem de hızlı taramalar için etkinleştirilebilir.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Yakalama tarama özelliğini etkinleştirmek ve yapılandırmak için grup ilkesi kullanma

1. En az bir zamanlanmış tarama ayarladığınızdan emin olun.

2. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

4. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

5. Ağacı genişleterek bileşenleri **Windows > Microsoft Defender Virüsten Koruma > Aşağıdaki ayarları tarayın** ve yapılandırın:

    1. Zamanlanmış hızlı taramalar ayarladıysanız, **Yakalama hızlı taramasını aç** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.
    2. Zamanlanmış tam taramalar ayarladıysanız, **Yakalama tam taramasını aç** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Tamam**'a tıklayın.
    3. **Yakalama taramasının zorlandığı gün sayısını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.
    4. Kullanıcı bilgisayarda bir sonraki oturum açtığında tarama otomatik olarak çalıştırılmadan önce kaçırabileceğiniz tarama sayısını girin. Çalıştırılan tarama türü, **Zamanlanmış tarama için kullanılacak tarama türünü belirtin** ( [Taramaları zamanlama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) konusuna bakın) tarafından belirlenir. **Tamam**'a tıklayın.

> [!NOTE]
> grup ilkesi ayarı başlığı gün sayısını ifade eder. Ancak ayar, yakalama taraması çalıştırılmadan önce tarama sayısına (günler değil) uygulanır.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yönetmek için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) kullanma.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'a** tıklayın, sonra ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Zamanlanmış taramalar** bölümüne gidin ve **İstemci bilgisayar çevrimdışıysa seçili tarama türünü taramaya zorla...** seçeneğini **Evet** olarak ayarlayın.

3. **Tamam**'a tıklayın.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
