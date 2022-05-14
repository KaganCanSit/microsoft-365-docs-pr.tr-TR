---
title: İstenmeyebilecek uygulamaları Microsoft Defender Virüsten Koruma ile engelleme
description: Adware gibi istenmeyen yazılımları engellemek için istenmeyebilecek uygulama (PUA) virüsten koruma özelliğini etkinleştirin.
keywords: pua, etkinleştirme, istenmeyen yazılım, istenmeyen uygulamalar, adware, tarayıcı araç çubuğu, algılama, engelleme, Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: mimilone, julih
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: m365-security-compliance
ms.openlocfilehash: c7307e7c690e9664f6a848fcd93ed27f1062455a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418368"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>İstenmeyen olası uygulamaları tespit edin ve engelleyin

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

İstenmeyebilecek uygulamalar (PUA), makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya en kötü ihtimalle beklenmeyen veya istenmeyen olabilecek diğer yazılımları yüklemesine neden olabilecek bir yazılım kategorisidir. PUA bir virüs, kötü amaçlı yazılım veya başka bir tehdit türü olarak kabul edilmez, ancak uç nokta performansını veya kullanımını olumsuz etkileyen uç noktalarda eylemler gerçekleştirebilir. *PUA* terimi, bazı istenmeyen davranış türleri nedeniyle Uç Nokta için Microsoft Defender tarafından değerlendirildiği gibi kötü bir üne sahip bir uygulamaya da başvurabilir.

İşte birkaç örnek:

- **Web** sayfalarına reklam ekleyen yazılımlar da dahil olmak üzere reklamları veya promosyonları görüntüleyen reklam yazılımları.
- Aynı varlık tarafından dijital olarak imzalanan diğer yazılımları yüklemeyi teklif eden paketleme **yazılımı**. Ayrıca, PUA olarak nitelendiren diğer yazılımları yüklemeyi teklif eden yazılımlar.
- **Güvenlik** ürünlerinin varlığında farklı davranan yazılımlar da dahil olmak üzere güvenlik ürünleri tarafından algılamayı aktif olarak atlatmaya çalışan kaçınma yazılımı.

> [!TIP]
> Daha fazla örnek ve uygulamaları güvenlik özelliklerine özel dikkat çekmek üzere etiketlemek için kullandığımız ölçütlerin tartışması için bkz. [Microsoft kötü amaçlı yazılımları ve istenmeyebilecek uygulamaları nasıl tanımlar](/windows/security/threat-protection/intelligence/criteria)?

İstenmeyebilecek uygulamalar ağınıza gerçek kötü amaçlı yazılım bulaşması riskini artırabilir, kötü amaçlı yazılım bulaşmalarının tanımlanmasını zorlaştırır veya temizlemede BT kaynaklarını boşa harcar. PUA koruması Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016'da desteklenir. Windows 10 (sürüm 2004 ve üzeri) Microsoft Defender Virüsten Koruma, Enterprise (E5) cihazlar için PUA olarak kabul edilen uygulamaları varsayılan olarak engeller.

## <a name="microsoft-edge"></a>Microsoft Edge

Chromium tabanlı [yeni Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea), istenmeyebilecek uygulama indirmelerini ve ilişkili kaynak URL'lerini engeller. Bu özellik [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) aracılığıyla sağlanır.

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Chromium tabanlı Microsoft Edge PUA korumasını etkinleştirme

Microsoft Edge 'de istenmeyebilecek uygulama koruması (Chromium tabanlı sürüm 80.0.361.50) varsayılan olarak kapalı olsa da, tarayıcı içinden kolayca açılabilir.

1. Edge tarayıcınızda üç noktayı ve ardından **Ayarlar'ı** seçin.

2. **Gizlilik, arama ve hizmetler'i** seçin.

3. **Güvenlik** bölümünün altında **İstenmeyebilecek uygulamaları engelle'yi** açın.

> [!TIP]
> Microsoft Edge (Chromium tabanlı) çalıştırıyorsanız, Microsoft Defender SmartScreen [tanıtım sayfalarımızdan](https://demo.smartscreen.msft.net/) birinde test ederek PUA korumasının URL'yi engelleme özelliğini güvenle keşfedebilirsiniz.

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen ile URL'leri engelleme

PUA koruması açık Chromium tabanlı Edge'de Microsoft Defender SmartScreen sizi PUA ile ilişkili URL'lerden korur.

Güvenlik yöneticileri, kullanıcı gruplarını PUA ile ilişkili URL'lerden korumak için Microsoft Edge ve Microsoft Defender SmartScreen birlikte nasıl çalışabileceğini [yapılandırabilir](/DeployEdge/configure-microsoft-edge). [PuA'yı engelleme](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled) de dahil olmak üzere Microsoft Defender SmartScreen için açıkça çeşitli [grup ilkesi ayarları](/DeployEdge/microsoft-edge-policies#smartscreen-settings) vardır. Ayrıca, yöneticiler Microsoft Defender SmartScreen açmak veya kapatmak için grup ilkesi ayarlarını kullanarak Microsoft Defender SmartScreen bir bütün olarak [yapılandırabilir](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen).

Uç Nokta için Microsoft Defender, Microsoft tarafından yönetilen bir veri kümesini temel alan kendi blok listesine sahip olsa da, bu listeyi kendi tehdit bilgilerinize göre özelleştirebilirsiniz. Uç Nokta için Microsoft Defender portalında [göstergeler oluşturup yönetiyorsanız](manage-indicators.md) Microsoft Defender SmartScreen yeni ayarlara saygı gösterir.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Microsoft Defender Virüsten Koruma ve PUA koruması

Microsoft Defender Virüsten Koruma'daki istenmeyebilecek uygulama (PUA) koruma özelliği, ağınızdaki uç noktalarda PUA'yi algılayabilir ve engelleyebilir.

> [!NOTE]
> Bu özellik Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016'da kullanılabilir.

Microsoft Defender Virüsten Koruma PUA dosyalarını ve bunları indirme, taşıma, çalıştırma veya yükleme girişimlerini engeller. Engellenen PUA dosyaları karantinaya taşınır. Bir uç noktada PUA dosyası algılandığında, Microsoft Defender Virüsten Koruma kullanıcıya bir bildirim gönderir (bildirimler diğer tehdit algılamalarıyla aynı biçimde [devre dışı bırakılmadığı sürece](configure-notifications-microsoft-defender-antivirus.md)). Bildirimin içeriği belirtilmesi için ile `PUA:` önsözü oluşturulur.

Bildirim, [Windows Güvenliği uygulamasındaki normal karantina listesinde](microsoft-defender-security-center-antivirus.md) görünür.

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma'de PUA korumasını yapılandırma

PUA korumasını [Microsoft Intune](/mem/intune/protect/device-protect), [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [grup ilkesi](/azure/active-directory-domain-services/manage-group-policy) veya [PowerShell cmdlet'leri](/powershell/module/defender/?preserve-view=true&view=win10-ps) aracılığıyla etkinleştirebilirsiniz.

İstenmeyebilecek uygulamaları engellemeden algılamak için pua korumasını denetim modunda da kullanabilirsiniz. Algılamalar Windows olay günlüğünde yakalanır.

> [!TIP]
> özelliğin çalıştığını onaylamak ve çalışır durumda görmek için [demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep) Uç Nokta için Microsoft Defender tanıtım web sitesini ziyaret edin.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Şirketiniz bir iç yazılım güvenliği uyumluluk denetimi gerçekleştiriyorsa ve hatalı pozitif sonuçları önlemek istiyorsanız, denetim modunda PUA koruması yararlıdır.

### <a name="use-intune-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için Intune kullanma

Daha fazla bilgi için bkz. [Microsoft Intune cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure) ve [Windows 10 için cihaz kısıtlama ayarlarını Microsoft Defender Virüsten Koruma Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-configuration-manager-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için Configuration Manager kullanma

PUA koruması, Microsoft Endpoint Manager (Geçerli Dal) içinde varsayılan olarak etkindir.

Microsoft Endpoint Manager yapılandırma (Geçerli Dal) ile ilgili ayrıntılar için bkz[. Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Zamanlanmış tarama ayarları](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings).

System Center 2012 Configuration Manager için bkz. [Configuration Manager'da Endpoint Protection için İstenmeyebilecek Uygulama Koruma İlkesiNi Dağıtma](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> Microsoft Defender Virüsten Koruma tarafından engellenen PUA olayları Microsoft Endpoint Configuration Manager değil Windows Olay Görüntüleyicisi bildirilir.

### <a name="use-group-policy-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için grup ilkesi kullanma

1. [Windows 10 Ekim 2020 Güncelleştirmesi (20H2) için Yönetim Şablonlarını (.admx)](https://www.microsoft.com/download/details.aspx?id=102157) indirme ve yükleme

2. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

3. Yapılandırmak istediğiniz grup ilkesi Nesnesi'ni ve ardından **Düzenle'yi** seçin.

4. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

5. Bileşenleri \> **Microsoft Defender Virüsten Koruma Windows** ağacı **genişletin.**

6. **İstenmeyebilecek uygulamalar için algılamayı yapılandır'a** çift tıklayın.

7. PUA korumasını etkinleştirmek için **Etkin'i** seçin.

8. **Seçenekler'de** **engelle'yi** seçerek istenmeyebilecek uygulamaları engelleyin veya ayarın ortamınızda nasıl çalıştığını test etmek için **Denetim Modu'nu** seçin. **Tamam**'ı seçin.

9. grup ilkesi nesnenizi her zamanki gibi dağıtın.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için PowerShell cmdlet'lerini kullanma

#### <a name="to-enable-pua-protection"></a>PUA korumasını etkinleştirmek için

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Bu cmdlet'in değeri, devre dışı bırakılmışsa özelliği açmak için `Enabled` ayarlanır.

#### <a name="to-set-pua-protection-to-audit-mode"></a>PUA korumasını denetim moduna ayarlamak için

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Ayarı `AuditMode` PUA'ları engellemeden algılar.

#### <a name="to-disable-pua-protection"></a>PUA korumasını devre dışı bırakmak için

PUA korumasını açık tutmanızı öneririz. Ancak, aşağıdaki cmdlet'i kullanarak kapatabilirsiniz:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Bu cmdlet'in değeri, etkinleştirildiyse özelliği kapatacak `Disabled` şekilde ayarlanır.

Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/index) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

## <a name="view-pua-events-using-powershell"></a>PowerShell kullanarak PUA olaylarını görüntüleme

PUA olayları Windows Olay Görüntüleyicisi bildirilir, ancak Microsoft Endpoint Manager veya Intune raporlanmaz. İşlenen tehditleri görüntülemek Microsoft Defender Virüsten Koruma cmdlet'ini de kullanabilirsiniz`Get-MpThreat`. İşte bir örnek:

```console
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## <a name="get-email-notifications-about-pua-detections"></a>PUA algılamaları hakkında e-posta bildirimleri alma

PUA algılamaları hakkında posta almak için e-posta bildirimlerini açabilirsiniz.

Microsoft Defender Virüsten Koruma olaylarını görüntülemeyle ilgili ayrıntılar için bkz. [Olay kimlikleriyle ilgili sorunları giderme](troubleshoot-microsoft-defender-antivirus.md). PUA olayları **1160** olay kimliği altında kaydedilir.

## <a name="view-pua-events-using-advanced-hunting"></a>Gelişmiş avcılığı kullanarak PUA olaylarını görüntüleme

[Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) kullanıyorsanız PUA olaylarını görüntülemek için gelişmiş bir avcılık sorgusu kullanabilirsiniz. Aşağıda örnek bir sorgu verilmişti:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Gelişmiş avcılık hakkında daha fazla bilgi edinmek için bkz. [Gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Dosyaları PUA korumasının dışında tutma

Bazen bir dosya PUA koruması tarafından yanlışlıkla engellenir veya görevi tamamlamak için BIR PUA özelliği gerekir. Böyle durumlarda, dışlama listesine bir dosya eklenebilir.

Daha fazla bilgi için bkz. [Dosya uzantısına ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Davranışsal, buluşsal ve gerçek zamanlı korumayı yapılandırın](configure-protection-features-microsoft-defender-antivirus.md)
