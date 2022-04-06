---
title: Uç Nokta için Microsoft Defender - Onboard'a geçiş
description: Geçiş tarak Uç Nokta için Microsoft Defender. Cihazları ekin ve Microsoft olmayan çözümlerinizi kaldırın.
keywords: migration, Uç Nokta için Microsoft Defender, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.topic: article
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 4f387ae01af51292667f810176970f3607b489b3
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634415"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Geçiş: Uç Nokta için Microsoft Defender - Aşama 3: Ekleme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Aşama 1: Hazırla3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Aşama 1: Hazırlık](switch-to-mde-phase-1.md) | [![Aşama 2: Kurulum](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Aşama 2: Kurulum](switch-to-mde-phase-2.md) | ![Aşama 3: Katılım](images/phase-diagrams/onboard.png#lightbox)<br/>Aşama 3: Katılım |
|--|--|--|
|| |*Buradasınız!* |

**Uç nokta için [Defender'a geçişin Aşama 3'e hoş geldiniz](switch-to-mde-overview.md#the-migration-process)**. Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Cihazları Uç Nokta için Defender'a ekleme](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [Bir algılama testi çalıştırın](#run-a-detection-test).
3. [Uç Microsoft Defender Virüsten Koruma edilgen modda olduğunu onaylayın](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [Yeni e-posta güncelleştirmelerini Microsoft Defender Virüsten Koruma](#get-updates-for-microsoft-defender-antivirus).
5. [Microsoft olmayan çözümlerinizi kaldırın](#uninstall-your-non-microsoft-solution).
6. [Uç Nokta için Defender'ın düzgün çalıştığından emin olun](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Cihazları mobil cihaza Uç Nokta için Microsoft Defender

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Uç **Ayarlar** \> **Ekleme'yi** \> **seçin** (Cihaz **yönetimi'nin altında**).

3. Ekleme **işlemini başlatmak için işletim sistemini seçin listesinden** bir işletim sistemi seçin.

4. Dağıtım **yöntemi'nin** altında bir seçenek belirtin. Kuruluş cihazlarınızı ekleme için bağlantıları ve istemleri izleyin. Yardıma mı ihtiyacınız var? Ekleme [yöntemlerine bakın](#onboarding-methods) (bu makalede).

> [!NOTE]
> Ekleme sırasında bir sorun olursa bkz. Ekleme [Uç Nokta için Microsoft Defender giderme](troubleshoot-onboarding.md). Bu makalede, uç noktalarda ekleme sorunlarının ve yaygın hataların nasıl çözül olduğu açıklanmıştır.

### <a name="onboarding-methods"></a>Ekleme yöntemleri

> [!IMPORTANT]
> Bulut için Microsoft Defender kullanıyorsanız, bkz. [Bulut için Microsoft Defender](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

Dağıtım yöntemleri, işletim sistemine ve tercih edilen yöntemlere bağlı olarak değişir. Aşağıdaki tabloda, Uç Nokta için Defender'a eklemeye yardımcı olacak kaynaklar listeledir:

|İşletim sistemleri  |Yöntemler  |
|---------|---------|
|Windows 10 veya sonrası<br/><br/>Windows Server 2019 veya sonraki bir sonrakini yükleme<br/><br/>Windows Server, sürüm 1803 veya sonrası<br/><br/>Windows Server 2012 R2 ve 2016<sup>[[1](#fn1)]<sup>  |   [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md)<br><br/>   [Grup İlkesi](configure-endpoints-gp.md)<br/><br/>[Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md)<br/><br/>[Microsoft Endpoint Manager/ Mobil Cihaz Yönetimi (Intune)](configure-endpoints-mdm.md)<br>    [VDI betikleri](configure-endpoints-vdi.md) <br><br> **NOT**: Yerel bir betik kavram kanıtı için uygundur, ancak üretim dağıtımı için kullanılmaları gerekir. Üretim dağıtımı için, üretim ürün grup ilkesi, Microsoft Endpoint Configuration Manager veya destek Intune. |
|Windows Server 2008 R2 SP1 | [Microsoft Monitoring Agent (MMA) veya](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) [Bulut için Microsoft Defender](/azure/security-center/security-center-wdatp) <br><br> **NOT**: Microsoft Monitoring Agent Azure Log Analytics aracısı oldu. Daha fazla bilgi edinmek için bkz. [Log Analytics aracıya genel bakış](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 SP1 Pro<br/><br/>Windows 7 SP1| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **NOT**: Microsoft Monitoring Agent Azure Log Analytics aracısı oldu. Daha fazla bilgi edinmek için bkz. [Log Analytics aracıya genel bakış](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (sistem [gereksinimlerine bakın)](microsoft-defender-endpoint-mac.md) | [Yerel betik](mac-install-manually.md)<br/><br/>[Microsoft Endpoint Manager](mac-install-with-intune.md)<br/><br/>[JAMF Pro](mac-install-with-jamf.md)<br/><br/>[Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md)   |
| Linux (sistem [gereksinimlerine bakın](microsoft-defender-endpoint-linux.md#system-requirements)) |  [Yerel betik](linux-install-manually.md) <br><br/> [Operasyon](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| iOS | [Microsoft Endpoint Manager](ios-install.md)     |
|Android  | [Microsoft Endpoint Manager](android-intune.md)  | 

(<a id="fn1">1</a>) Windows Server 2016 ve Windows Server 2012 R2'nin Onboard [Windows kullanılarak Windows gerekir](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma

Cihazlarınızı uç nokta için Defender'a düzgün bir şekilde bağlı olduğunu doğrulamak için bir algılama testi çalıştırabilirsiniz.

|İşletim sistemi|Kılavuz|
|---|---|
|Windows 10 veya sonrası<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server, sürüm 1803 veya sonrası<br/><br/>Windows Server 2016<br/><br/>Windows Server 2012 R2|Bkz [. Algılama testi çalıştırma](run-detection-test.md).<br/><br/>Uç nokta tanıtım senaryoları için Defender sitesini (<https://demo.wd.microsoft.com>) ziyaret edin ve senaryoların birini veya birden fazlasını deneyin. Örneğin, Buluta teslim **edilen koruma tanıtım senaryosunu** deneyin.|
|macOS (sistem [gereksinimlerine bakın)](microsoft-defender-endpoint-mac.md)|Buradan KENDI uygulamasını indirin ve kullanın <https://aka.ms/mdatpmacosdiy>. <br/><br/> Daha fazla bilgi için bkz. [macOS'ta Uç Nokta için Defender](microsoft-defender-endpoint-mac.md).|
|Linux (sistem [gereksinimlerine bakın](microsoft-defender-endpoint-linux.md#system-requirements))|1. Aşağıdaki komutu çalıştırın ve **1 sonucu için bakın**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. Terminal penceresini açın ve şu komutu çalıştırın: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. Algılanan tehditleri listeleyen şu komutu çalıştırın: `mdatp threat list`.<br/><br/>Daha fazla bilgi için bkz. [Linux'ta Uç Nokta için Defender](microsoft-defender-endpoint-linux.md).|

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Uç Microsoft Defender Virüsten Koruma edilgen modda olduğunu doğrulama

Uç noktanız Artık Uç Nokta için Defender'a alındıkndan, bir sonraki adımınız edilgen modda Microsoft Defender Virüsten Koruma emin olmaktır. Aşağıdaki tabloda açıklandığı gibi, birkaç yöntemden birini kullanabilirsiniz:

|Yöntem|Ne yapmalı?|
|---|---|
|Komut İstemi|1. Bir Windows Komut İstemi'ne açın.<br/><br/>2. yazın ve `sc query windefend`Enter tuşuna basın.<br/><br/>3. Pasif modunda çalışma Microsoft Defender Virüsten Koruma için sonuçları gözden geçirebilirsiniz.|
|PowerShell|1. Windows cihazda, yönetici Windows PowerShell olarak oturum açın.<br/><br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. Sonuçları gözden geçirin. Pasif modunu **görüyor olun**.|
|Windows Güvenliği uygulaması|1. Windows cihazda, Windows Güvenliği açın.<br/><br/>2. Virüs koruması **için &'i seçin**.<br/><br/>3. **Sağlayıcılar Who koruma altında Sağlayıcılar'ı** **yönet'i seçin**.<br/><br/>4. Güvenlik **sağlayıcıları sayfasındaki** Virüsten **Koruma'nın** altında, **Microsoft Defender Virüsten Koruma'i bulun**.|
|Görev Yöneticisi|1. Windows Yöneticisi uygulamasını açın.<br/><br/>2. Ayrıntılar **sekmesini** seçin. Listede **MsMpEng.exe** listeniz var mı?|

> [!NOTE]
> Dosyanın bazı *Windows Defender Virüsten Koruma* sürümlerinde *Microsoft Defender Virüsten Koruma* yerine başkalarını Windows.
> Pasif modu ve etkin mod hakkında daha fazla bilgi edinmek için, pasif [modu ve etkin mod hakkında daha fazla Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Microsoft Defender Virüsten Koruma Server'da Windows pasif moduna el ile ayarlama

Windows Server Microsoft Defender Virüsten Koruma, sürüm 1803 veya daha yenisi ya da Windows Server 2019 veya Windows Server 2022'de pasif moduna ayarlamak için şu adımları izleyin:

1. Kayıt Defteri Düzenleyicisi'ni açın ve sonra 'a gidin `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. **ForceDefenderPassiveMode** adlı bir DWORD girdisini düzenleyin (veya oluşturun) ve aşağıdaki ayarları belirtin:

   - DWORD değerini **1 olarak ayarlayın**.

   - **Taban'ın** altında **Onaltılı'ya seçin**.

> [!NOTE]
> Kayıt defteri anahtarını ayarlamak için başka yöntemler kullanabilirsiniz, örneğin:
>
> - [grup ilkesi Tercihi](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [Local grup ilkesi Object tool](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [Bir paket Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Microsoft Defender Virüsten Koruma'da Windows Server 2016

E-posta Windows Server 2016, e-postayı el ile Microsoft Defender Virüsten Koruma gerekebilir. Bu görevi gerçekleştirmek için cihazda PowerShell cmdlet'ini `mpcmdrun.exe -wdenable` kullanın.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Daha fazla bilgi için güncelleştirme Microsoft Defender Virüsten Koruma

Cihazlarınızı Microsoft Defender Virüsten Koruma edilgen modda çalışıyor olsa bile, yeni kötü amaçlı yazılımlara ve saldırı tekniklerine karşı korumak için gereken en son teknoloji ve özelliklere sahip olmanın güvence Microsoft Defender Virüsten Koruma, güncel tutmak kritik öneme sahiptir. (Uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).)

Güncelleştirmelerin güncel tutmayla ilgili iki tür Microsoft Defender Virüsten Koruma vardır:

- Güvenlik zekası güncelleştirmeleri

- Ürün güncelleştirmeleri

Güncelleştirmelerinizi almak için, Güncelleştirmeleri yönetme ve [temelleri Microsoft Defender Virüsten Koruma yönergeleri izleyin](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>Microsoft olmayan çözümlerinizi kaldırma

Bu noktada:

- Uç nokta için Defender'a kuruluş cihazlarınızı ekleme ve

- Microsoft Defender Virüsten Koruma yüklü ve etkinse,

Ardından, bir sonraki adımınız Microsoft dışı virüsten koruma, kötü amaçlı yazılımdan koruma ve uç nokta koruma çözümlerinizi kaldırmaktır. Microsoft olmayan çözümlerinizi kaldırdığınız zaman, pasif Microsoft Defender Virüsten Koruma moduna geçer. Çoğu durumda bu otomatik olarak gerçekleşir. 

> [!IMPORTANT]
> Herhangi bir nedenden Microsoft Defender Virüsten Koruma Microsoft dışı virüsten koruma/kötü amaçlı yazılımlardan koruma çözümlerinizi kaldırdikten sonra herhangi bir nedenle etkin moda giremenizi sağlarsa, bkz. Microsoft Defender Virüsten Koruma edilgen modunda takılmış [gibi görünüyorsa](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

Microsoft olmayan çözümlerinizi kaldırma konusunda yardım almak için, çözümle ilgili teknik destek ekibine başvurun.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Uç Nokta için Defender'ın düzgün çalıştığından emin olun

Artık Uç Nokta için Defender'ı kabul ettiynize ve Microsoft olmayan eski çözümlerinizi kaldırdığınıza göre, bir sonraki adımınız Uç Nokta için Defender'ın düzgün çalıştığından emin olmaktır. Bu görevi gerçekleştirmenin en iyi yollarından biri, Uç nokta tanıtım senaryoları için Defender sitesini () ziyaret etmektir[https://demo.wd.microsoft.com](https://demo.wd.microsoft.com). Bu sayfada, en azından aşağıdakiler dahil olmak üzere tanıtım senaryolarından birini veya birden fazlasını deneyin:

- Bulut teslimi koruma

- İstenmeyen Olabilecek Uygulamalar (PUA)

- Ağ Koruması (NP)

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="next-steps"></a>Sonraki adımlar

**Tebrikler**! Uç Nokta için [Defender'a geçiş işleminizi tamamladınız](switch-to-mde-overview.md#the-migration-process)!

- [Portalda ( ) güvenlik](security-operations-dashboard.md) Microsoft 365 Defender ziyaret edin[https://security.microsoft.com](https://security.microsoft.com).

- [Uç Nokta için Defender'ı Yönet, geçiş sonrası](manage-mde-post-migration.md).
