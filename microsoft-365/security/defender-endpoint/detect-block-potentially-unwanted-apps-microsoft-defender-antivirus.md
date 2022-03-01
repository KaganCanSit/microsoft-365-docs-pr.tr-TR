---
title: İstenmeyen olabilecek uygulamaları e-postayla Microsoft Defender Virüsten Koruma
description: Ad yazılımı gibi istenmeyen yazılımları engellemek için istenmeyen olabilecek uygulama (PUA) virüsten koruma özelliğini etkinleştirin.
keywords: pua, etkinleştirme, istenmeyen yazılım, istenmeyen uygulamalar, adware, tarayıcı araç çubuğu, algıla, engelle, Microsoft Defender Virüsten Koruma
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
ms.openlocfilehash: b193279f9891badc78e639776a57a366a0fa8109
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015190"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>İstenmeyen olabilecek uygulamaları algılama ve engelleme

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

İstenmeyen olabilecek uygulamalar (PUA), makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya en kötü de beklenmedik veya istenmeyen başka yazılımlar yüklemesine neden olabilecek bir yazılım kategorisidir. PUA bir virüs, kötü amaçlı yazılım veya diğer tehdit türü olarak kabul alınmaz, ancak uç nokta performansını veya kullanımını olumsuz etkileyen uç noktalarda eylemler gerçekleştirebilir. *PUA* terimi ayrıca, belirli istenmeyen davranış türleri nedeniyle Uç Nokta için Microsoft Defender tarafından değerlendirilen, saygınlığı düşük olan bir uygulamaya da başvurur.

İşte birkaç örnek:

- **Web sayfalarına** reklam eken yazılımlar da dahil olmak üzere reklam veya promosyonları görüntüleyen reklam yazılımı.
- **Aynı varlık tarafından** dijital olarak imzalanmaz başka bir yazılım yüklemek için teklif sunan bundling yazılımı. Ayrıca, PUA olarak nitelendirilen başka bir yazılım yüklemesi de sunan yazılımdır.
- **Güvenlik ürünleri varlığında** farklı davranan yazılımlar da dahil olmak üzere, güvenlik ürünleri tarafından algıdan kurtulmaya çalışan bir yazılım.

> [!TIP]
> Uygulamaları güvenlik özelliklerinden özellikle dikkat çekmek üzere etiketlemek üzere bu ölçütler hakkında daha fazla örnek ve tartışma için bkz. Microsoft kötü amaçlı yazılımları ve potansiyel [olarak istenmeyen uygulamaları nasıl tanımlar](/windows/security/threat-protection/intelligence/criteria).

İstenmeyen olabilecek uygulamalar, ağnıza gerçek kötü amaçlı yazılımdan bulaşma riskini artırabilir, kötü amaçlı yazılım bulaşmalarının belirlenmesini zorlaştırabilir veya temizlemek için IT kaynaklarını israf edebilir. PUA koruması Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016. Windows 10 (sürüm 2004 ve sonraki sürümler) içinde Microsoft Defender Virüsten Koruma, Enterprise (E5) cihazları için PUA olarak kabul edilen uygulamaları engeller.

## <a name="microsoft-edge"></a>Microsoft Edge

Tabanlı [Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea) olan yeni Chromium, istenmeyen uygulama indirmeleri ve ilişkili kaynak URL'lerini engeller. Bu özellik, [diğer Microsoft Defender SmartScreen.](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Tabanlı iki yıllık bir Chromium PUA korumasını Microsoft Edge

Microsoft Edge'te istenmeyen uygulama koruması (Chromium tabanlı, 80.0.361.50 sürümü) varsayılan olarak kapalı olsa da, tarayıcının içinde kolayca kapatabilirsiniz.

1. Edge tarayıcınızda üç noktayı seçin ve sonra da Üç **Nokta'Ayarlar.**

2. Gizlilik **, arama ve hizmetler'i seçin**.

3. Güvenlik bölümünde **,** İstenmeyen olabilecek **uygulamaları engelle'ye tıklayın**.

> [!TIP]
> Microsoft Edge (Chromium tabanlı) çalıştırıyorsanız, puA korumanın URL engelleme özelliğini, bu özellikleri Microsoft Defender SmartScreen [veya tanıtım](https://demo.smartscreen.msft.net/) sayfalarımızı test Microsoft Defender SmartScreen bulabilirsiniz.

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Url'leri Microsoft Defender SmartScreen

PUA Chromium açık olan Kullanıcı Tabanlı Edge'de, Microsoft Defender SmartScreen PUA ile ilişkili URL'lere karşı sizi korur.

Güvenlik yöneticileri, kullanıcı [gruplarını](/DeployEdge/configure-microsoft-edge) PUA Microsoft Edge Microsoft Defender SmartScreen için kullanıcı grupları üzerinde nasıl çalışacaklarını ve nasıl çalışacaklarını yapılandırabilirsiniz. [PUA'yı engelleme dahil](/DeployEdge/microsoft-edge-policies#smartscreen-settings) olmak üzere, Microsoft Defender SmartScreen için [açık olarak birkaç grup ilkesi ayarı vardır](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). Ayrıca yöneticiler grup ilkesi [ayarlarını Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) veya kapatmak için grup ilkesi ayarlarını kullanarak bir bütün olarak Microsoft Defender SmartScreen yapılandırabilirsiniz.

Uç Nokta için Microsoft Defender'ın Microsoft tarafından yönetilen bir veri kümesine dayalı olarak kendi engelleme listesi olsa da, kendi tehdit zekanız üzerine bu listeyi özelleştirebilirsiniz. Uç nokta [portalı için Microsoft Defender'da](manage-indicators.md) göstergeler oluşturmanız ve yönetmeniz Microsoft Defender SmartScreen ayarlarına uygun olur.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Microsoft Defender Virüsten Koruma PUA koruması

Microsoft Defender Virüsten Koruma'daki istenmeyen uygulama (PUA) koruma özelliği, ağ bağlantı noktalarında PUA'yı algılanabilir ve engelleyebilir.

> [!NOTE]
> Bu özellik Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 ve Windows Server 2016.

Microsoft Defender Virüsten Koruma PUA dosyalarını ve bunları indirmeye, taşımaya, çalıştırmaya veya yüklemeye yönelik tüm denemeleri engeller. Engellenen PUA dosyaları karantinaya taşınır. Bir uç noktada PUA dosyası algılandığında, Microsoft Defender Virüsten Koruma kullanıcıya bir bildirim [gönderir (bildirimler](configure-notifications-microsoft-defender-antivirus.md) diğer tehdit algılamaları ile aynı biçimde devre dışı bırakılamaz. Bildirimin içeriği belirtmek için `PUA:` önleri bildirimin yer alır.

Bildirim, her zamanki karantina [listesinde Windows Güvenliği görüntülenir](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Web'de PUA korumasını Microsoft Defender Virüsten Koruma

PUA korumasını [etkinleştiren Microsoft Intune](/mem/intune/protect/device-protect)[, Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection) [İlkesi](/azure/active-directory-domain-services/manage-group-policy) ile veya [PowerShell cmdlet'leri aracılığıyla etkinleştirabilirsiniz](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Ayrıca, istenmeyen olabilecek uygulamaları engellemeden algılamak için denetim modunda PUA korumasını da kullanabilirsiniz. Algılamalar, olay günlüğünde Windows yakalanır.

> [!TIP]
> Özelliğin çalıştığını onaylamak ve nasıl çalıştığını görmek için [demo.wd.microsoft.com'de](https://demo.wd.microsoft.com/Page/UrlRep) Uç Nokta için Microsoft Defender tanıtım web sitesini ziyaret edin.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Denetlenen modda PUA koruması, şirket içi yazılım güvenliği uyumluluk denetimi yapıyorsa ve hatalı pozitif sonuçlardan kaçınmakıyorsa yararlıdır.

### <a name="use-intune-to-configure-pua-protection"></a>INtune kullanarak PUA korumasını yapılandırma

Daha [fazla bilgi için Intune'da Microsoft Intune](/intune/device-restrictions-configure) Windows 10 ve cihaz Microsoft Defender Virüsten Koruma için cihaz kısıtlama ayarlarını [yapılandırma'ya](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) bakın.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için Yapılandırma Yöneticisi'ni kullanma

PUA koruması geçerli dosya (Geçerli Microsoft Endpoint Manager) içinde varsayılan olarak etkindir.

Bkz[. Kötü amaçlı yazılım önleme ilkeleri](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) oluşturma ve dağıtma: İlkeyi (Güncel Dalı) yapılandırmayla ilgili ayrıntılar Microsoft Endpoint Manager tarama ayarları.

Daha System Center 2012 Configuration Manager için bkz. Configuration Manager'da İstenmeyen Uygulama [Koruma İlkesi Endpoint Protection Dağıtma](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> Microsoft Defender Virüsten Koruma tarafından engellenen PUA olayları, Olay Görüntüleyicisi'Windows tarafından Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için Grup İlkesi kullanma

1. Ekim [2020 Güncelleştirmesini (20H2) Windows 10 Yönetim Şablonlarını (.admx) indirme ve yükleme](https://www.microsoft.com/download/details.aspx?id=102157)

2. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Yapılandırmak istediğiniz Grup İlkesi Nesnesini seçin ve sonra da Düzenle'yi **seçin**.

4. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

5. Bileşenleri Ve Bileşenleri Windows **için** \> **ağacı Microsoft Defender Virüsten Koruma**.

6. İstenmeyen olabilecek **uygulamalar için Algılamayı yapılandır'a çift tıklayın**.

7. PUA **korumasını** etkinleştirmek için Etkin'i seçin.

8. **Seçenekler'de**, **istenmeyen olabilecek** uygulamaları engellemek için Engelle'yi seçin veya **ayarın ortamınız** içinde nasıl çalıştığını test etmek için Denetim Modu'seçin. **Tamam**'ı seçin.

9. Grup İlkesi nesnenizi her zaman olduğu gibi dağıtın.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için PowerShell cmdlet'lerini kullanma

#### <a name="to-enable-pua-protection"></a>PUA korumasını etkinleştirmek için

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Devre dışı bırakılmışsa özelliği etkinleştirirken `Enabled` bu cmdlet'in değerini ayarlama.

#### <a name="to-set-pua-protection-to-audit-mode"></a>PUA korumasını denetim moduna ayarlamak için

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Ayar `AuditMode` , PUA'ları engellemeden algılar.

#### <a name="to-disable-pua-protection"></a>PUA korumasını devre dışı bırakmak için

PUA korumasının açık tutmasını öneririz. Bununla birlikte, aşağıdaki cmdlet'i kullanarak kapat yapabilirsiniz:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Bu cmdlet'in değeri, `Disabled` etkinleştirilmişse özelliği kapatacak şekilde ayarlama.

Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>PowerShell kullanarak PUA olaylarını görüntüleme

PUA olayları Olay Görüntüleyicisi'nde Windows ancak En son Microsoft Endpoint Manager Intune'da değil. Bu cmdlet'i `Get-MpThreat` aynı zamanda ele alan tehditleri Microsoft Defender Virüsten Koruma kullanabilirsiniz. İşte bir örnek:

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

## <a name="get-email-notifications-about-pua-detections"></a>PUA algılamaları hakkında e-posta bildirimleri alın

PUA algılamaları hakkında posta almak için e-posta bildirimlerini açabilirsiniz.

Olayları [görüntüleme hakkında ayrıntılı bilgi için](troubleshoot-microsoft-defender-antivirus.md) olay kimliklerini Microsoft Defender Virüsten Koruma bakın. PUA olayları, olay kimliği **1160'ın altına kaydedilir**.

## <a name="view-pua-events-using-advanced-hunting"></a>Gelişmiş avı kullanarak PUA etkinliklerini görüntüleme

Uç nokta için [Microsoft Defender'ı kullanıyorsanız](microsoft-defender-endpoint.md), PUA etkinliklerini görüntülemek için gelişmiş bir av sorgusu kullanabilirsiniz. İşte örnek bir sorgu:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Gelişmiş av hakkında daha fazla bilgi edinmek için bkz. Gelişmiş [avla tehditlere karşı önceden arama.](advanced-hunting-overview.md)

## <a name="exclude-files-from-pua-protection"></a>Dosyaları PUA korumasının dışında tut

Bazen bir dosya, PUA koruması tarafından hatalı bir şekilde engellenir veya görevi tamamlamak için bir PUA özelliği gerekir. Böyle durumlarda, dosya dışlama listesine eklenebilir.

Daha fazla bilgi için bkz [. Dosya uzantısını ve klasör konumunu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md)
