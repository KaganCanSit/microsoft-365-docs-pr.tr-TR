---
title: Eski uç noktalara Microsoft Defender Virüsten Koruma koruma güncelleştirmeleri uygulama
description: Bir süredir güncelleştirilmemiş uç noktalar için güncelleştirmelerin ne zaman ve nasıl uygulanacağını tanımlayın.
keywords: güncelleştirmeler, koruma, güncel olmayan, eski, eski, yakalama
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fcf13258b8012bfd2a5875b52b8d844040aee73e
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623488"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Güncel olmayan uç nokta taramalarını ve Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetin

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**

- Windows

Microsoft Defender Virüsten Koruma ile güvenlik ekibiniz bir uç noktanın güncelleştirmeyi ne kadar süreyle önleyebileceğini veya güncelleştirmeyi alıp tarama çalıştırması gerekmeden önce kaç taramayı kaçırabileceğini tanımlayabilir. Bu özellik özellikle cihazların genellikle bir şirkete veya dış ağa bağlı olmadığı ortamlarda veya günlük olarak kullanılmayan cihazlarda kullanışlıdır.

Örneğin, belirli bir bilgisayarı kullanan bir çalışan üç gün işten izin alır ve bu süre boyunca bilgisayarında oturum açmaz. Çalışan işe döndüğünde ve bilgisayarında oturum açtığında, Microsoft Defender Virüsten Koruma en son koruma güncelleştirmelerini hemen denetleyecek ve indirecek ve ardından bir tarama çalıştıracaktır.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Bir süredir güncelleştirilmemiş uç noktalar için yakalama koruma güncelleştirmelerini ayarlama

Microsoft Defender Virüsten Koruma belirli bir süre için koruma güncelleştirmelerini indirmediyse, birisi bir sonraki uç noktada oturum açtığında en son güncelleştirmeyi otomatik olarak denetleyecek ve indirecek şekilde ayarlayabilirsiniz. [Başlangıçta otomatik güncelleştirme indirmelerini genel olarak devre dışı bırakmışsanız](manage-event-based-updates-microsoft-defender-antivirus.md) bu yapılandırma yararlıdır.

Yakalama koruma güncelleştirmelerini ayarlamak için çeşitli yöntemlerden birini kullanabilirsiniz:

- [Yapılandırma Yöneticisi](#use-configuration-manager-to-configure-catch-up-protection-updates)
- [Grup İlkesi](#use-group-policy-to-enable-and-configure-the-catch-up-update-feature)
- [PowerShell cmdlet'leri](#use-powershell-cmdlets-to-configure-catch-up-protection-updates)
- [Windows Yönetim Yönergesi (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates)

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'u** seçin, ardından ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Güvenlik bilgileri güncelleştirmeleri** bölümüne gidin ve aşağıdaki ayarları yapılandırın:

    - **İstemci bilgisayar art arda ikiden fazla zamanlanmış güncelleştirme için çevrimdışıysa Güvenlik bilgileri güncelleştirmesini zorla** seçeneğini **Evet** olarak ayarlayın.
    - **Güvenlik bilgileri güncelleştirmeleri için kaynak olarak Configuration Manager kullanılıyorsa...** için, Configuration Manager tarafından teslim edilen koruma güncelleştirmelerinin güncel olmayan olarak kabul edilmesi gereken saatleri belirtin. Bu ayar, tanımlanan [geri dönüş kaynak sırasına](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) göre bir sonraki güncelleştirme konumunun kullanılmasına neden olur.

3. **Tamam**'ı seçin.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Yakalama güncelleştirme özelliğini etkinleştirmek ve yapılandırmak için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesi'ne sağ tıklayın ve düzenle'yi seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'i** ve ardından **Yönetim şablonları'nı** seçin.

4. **İmza Güncelleştirmeleri > Microsoft Defender Virüsten Koruma > bileşenleri Windows** için ağacı genişletin.

5. **Yakalama güvenlik bilgileri güncelleştirmesinin gerekli olduğu gün sayısını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender Virüsten Koruma en son koruma güncelleştirmesini denetlemesini ve indirmesini istediğiniz gün sayısını girin.

6. **Tamam**'ı seçin.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell cmdlet'lerini kullanma](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Yakalama koruma güncelleştirmelerini yapılandırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
SignatureUpdateCatchupInterval
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdaki makaleye bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Korumanın güncel değil olarak bildirildiği gün sayısını ayarlayın

Ayrıca, Microsoft Defender Virüsten Koruma korumasının eski veya güncel olmayan olarak kabul edildiği gün sayısını da belirtebilirsiniz. Belirtilen gün sayısından sonra istemci kendisini "güncel değil" olarak bildirir ve uç nokta kullanıcısına bir hata gösterir. Bir uç nokta güncel değil olarak kabul edildiğinde, Microsoft Defender Virüsten Koruma diğer kaynaklardan bir güncelleştirmeyi indirmeye çalışabilir (tanımlanan [geri dönüş kaynak sırasına](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) göre).

uç nokta korumasının güncel olmadığının kabul edildiği gün sayısını belirtmek için grup ilkesi kullanabilirsiniz.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Korumanın güncel olmadığını kabul etmeden önceki gün sayısını belirtmek için grup ilkesi kullanın

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'i** ve ardından **Yönetim şablonları'nı** seçin.

4. **İmza Güncelleştirmeleri > Microsoft Defender Virüsten Koruma > bileşenleri Windows** için ağacı genişletin ve aşağıdaki ayarları yapılandırın:

    1. **Casus yazılım tanımlarının eski olduğu düşünülmeden önce geçmesi gereken gün sayısını tanımla'ya** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender Virüsten Koruma casus yazılım Güvenlik bilgileri'nin güncel olmasını istediğiniz gün sayısını girin.

    2. **Tamam**'ı seçin.

    3. **Virüs tanımlarının eski olduğu düşünülmeden önce geçmesi gereken gün sayısını tanımla'ya** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Microsoft Defender Virüsten Koruma virüs Güvenlik bilgileri'nin güncel olmasını istediğiniz gün sayısını girin.

    4. **Tamam**'ı seçin.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Bir süredir taranmayan uç noktalar için yakalama taramaları ayarlama

Microsoft Defender Virüsten Koruma taramayı zorlamadan önce kaçırılacak ardışık zamanlanmış taramaların sayısını ayarlayabilirsiniz.

Bu özelliği etkinleştirme işlemi şu şekildedir:

1. En az bir zamanlanmış tarama ayarlayın ( [Zamanlanmış taramalar](scheduled-catch-up-scans-microsoft-defender-antivirus.md) makalesine bakın).

2. Yakalama tarama özelliğini etkinleştirin.

3. Yakalama taraması gerçekleşmeden önce atlanacak tarama sayısını tanımlayın.

Bu özellik hem tam hem de hızlı taramalar için etkinleştirilebilir. 

> [!TIP]
> Çoğu durumda hızlı taramalar kullanmanızı öneririz. Daha fazla bilgi için bkz [. Hızlı tarama, tam tarama ve özel tarama](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan). 

Yakalama taramalarını ayarlamak için çeşitli yöntemlerden birini kullanabilirsiniz:

- [Grup İlkesi](#use-group-policy-to-enable-and-configure-the-catch-up-scan-feature)
- [Yakalama taramalarını yapılandırmak için PowerShell cmdlet'lerini kullanma](#use-powershell-cmdlets-to-configure-catch-up-scans)
- [Windows Yönetim Yönergesi (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-scans)
- [Yapılandırma Yöneticisi](#use-configuration-manager-to-configure-catch-up-scans)

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Yakalama tarama özelliğini etkinleştirmek ve yapılandırmak için grup ilkesi kullanma

1. En az bir zamanlanmış tarama ayarladığınızdan emin olun.

2. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

4. **İlkeler'i** ve ardından **Yönetim şablonları'nı** seçin.

5. Ağacı genişleterek bileşenleri **Windows > Microsoft Defender Virüsten Koruma > Aşağıdaki ayarları tarayın** ve yapılandırın:

    - Zamanlanmış hızlı taramalar ayarladıysanız, **Yakalama hızlı taramasını aç** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.
    - Zamanlanmış tam taramalar ayarladıysanız, **Yakalama tam taramasını aç** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Tamam**'ı seçin.
    - **Yakalama taramasının zorlandığı gün sayısını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.
    - Kullanıcı uç noktada bir sonraki oturum açtığında tarama otomatik olarak çalıştırılmadan önce kaçırabileceğiniz tarama sayısını girin. Çalıştırılan tarama türü, **Zamanlanmış tarama için kullanılacak tarama türünü belirtin** ( [Taramaları zamanlama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) makalesine bakın) tarafından belirlenir. **Tamam**'ı seçin.

> [!NOTE]
> grup ilkesi ayarı başlığı gün sayısını ifade eder. Ancak ayar, yakalama taraması çalıştırılmadan önce tarama sayısına (günler değil) uygulanır.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Microsoft Defender Virüsten Koruma’yı yönetmek için PowerShell cmdlet'lerini kullanın](use-powershell-cmdlets-microsoft-defender-antivirus.md) 
- [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdaki makaleye bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Yakalama taramalarını yapılandırmak için Configuration Manager kullanma

1. Microsoft Endpoint Manager konsolunuzda, değiştirmek istediğiniz kötü amaçlı yazılımdan koruma ilkesini açın (soldaki gezinti bölmesinde **Varlıklar ve Uyumluluk'u** seçin, ardından ağacı **Genel Bakış** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri**) olarak genişletin

2. **Zamanlanmış taramalar** bölümüne gidin ve **İstemci bilgisayar çevrimdışıysa seçili tarama türünü taramaya zorla...** seçeneğini **Evet** olarak ayarlayın.

3. **Tamam**'ı seçin.

4. [Güncelleştirilmiş ilkeyi her zamanki gibi dağıtın](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
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
