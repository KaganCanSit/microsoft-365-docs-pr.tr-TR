---
title: Uç nokta için Microsoft Defender'a geçiş - Kurulum
description: Uç nokta için Defender'a geçme. Microsoft Defender Virüsten Koruma'i yüklemeyi içeren kurulum Microsoft Defender Virüsten Koruma.
keywords: geçiş, Uç Nokta için Microsoft Defender, virüsten koruma, pasif modu, kurulum işlemi
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
ms.topic: article
ms.custom: migrationguides
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 99d0de5562b31cdc0f5d6c17d1e9f855ef5a55ea
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027487"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Uç Nokta için Microsoft Defender'a geçiş - Aşama 2: Kurulum

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Aşama 1: Hazırlık.](images/phase-diagrams/prepare.png)](switch-to-mde-phase-1.md)<br/>[Aşama 1: Hazırlama](switch-to-mde-phase-1.md)|![Aşama 2: Ayarlama.](images/phase-diagrams/setup.png)<br/>Aşama 2: Ayarlama|[![Aşama 3: Ekleme3.](images/phase-diagrams/onboard.png)](switch-to-mde-phase-3.md)<br/>[Aşama 3: Ekleme](switch-to-mde-phase-3.md)|
|---|---|---|
||*Buradasınız!*||

**Uç nokta için [Defender'a geçişin Kurulum aşamasına hoş geldiniz](switch-to-mde-overview.md#the-migration-process)**. Bu aşama aşağıdaki adımları içerir:

1. [Uç noktalarınıza Microsoft Defender Virüsten Koruma yeniden yükleyin/etkinleştirin](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Uç Nokta için Defender'ı yapılandırma](#configure-defender-for-endpoint).
3. [Var olan çözümünüz için dışlama listesine Uç Nokta için Defender ekleyin](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Var olan çözümlerinizi dışlama listesine sizin için Microsoft Defender Virüsten Koruma](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Cihaz gruplarınızı, cihaz koleksiyonlarınızı ve kuruluş birimlerinizi ayarlayın](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Uç noktalarınıza Microsoft Defender Virüsten Koruma yeniden yükleme/etkinleştirme

Microsoft dışı virüsten Windows veya kötü amaçlı yazılımdan koruma çözümünüz yüklü olduğunda, Microsoft Defender Virüsten Koruma veya devre dışı bırakılmış olabilir. Farklı bir Windows uç nokta Uç nokta için Defender'a ekli olduğunda, Microsoft Defender Virüsten Koruma edilgen modda ve Microsoft olmayan bir virüsten koruma çözümüyle birlikte çalıştırabilirsiniz. Daha fazla bilgi edinmek için bkz. [Uç Nokta için Defender ile Virüsten Koruma](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Uç nokta için Defender'a geçiş yaparken, yeniden yüklemek veya etkinleştirmek için bazı adımları Microsoft Defender Virüsten Koruma. Aşağıdaki tabloda, iş istemcileriniz ve sunucularınız üzerinde Windows açık almaktadır.
<br/> <br/>

|Uç nokta türü|Ne yapmalı?|
|---|---|
|Windows istemcileri (Windows 10 11'i çalıştıran uç Windows gibi)|Genel olarak, bu istemcilerde herhangi bir Windows işlem Microsoft Defender Virüsten Koruma kaldırmanız gerekir. İşte nedeni: <br/><br/> Microsoft Defender Virüsten Koruma hala yüklü olması gerekir, ancak büyük olasılıkla geçiş işleminin bu noktasında devre dışıdır. <br/><br/> Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü yüklüyse ve istemciler uç nokta için Defender'a henüz yüklenmemişse, Microsoft Defender Virüsten Koruma devre dışı bırakılır. <br/><br/> Daha sonra, istemci uç noktaları Uç Nokta için Defender'a ekli olduğunda, bu uç noktalar Microsoft dışı bir virüsten koruma çözümü çalıştırıyorsa, Microsoft Defender Virüsten Koruma pasif moduna girer. <br/><br/> Microsoft dışı virüsten koruma çözümü kaldırılırsa, Microsoft Defender Virüsten Koruma moduna otomatik olarak girer.|
|Windows sunucuları|Windows Server'da, e-Microsoft Defender Virüsten Koruma yeniden yüklemeniz ve kendiniz pasif moduna ayarlamanız gerekir. Bu Windows, Microsoft olmayan bir virüsten koruma/kötü amaçlı yazılım yüklü olduğunda, Microsoft Defender Virüsten Koruma olmayan virüsten koruma çözümüyle birlikte çalıştıramaz. Böyle durumlarda, Microsoft Defender Virüsten Koruma devre dışı bırakılır veya el ile kaldırılır. <br/><br/> Microsoft Defender Virüsten Koruma Server'da Windows yüklemek veya etkinleştirmek için aşağıdaki görevleri gerçekleştirin: <br/>- [Windows Server'da DisableAntiCcaware özelliğini false olarak ayarlama](#set-disableantispyware-to-false-on-windows-server) (yalnızca gerekiyorsa)<br/>- [E-Microsoft Defender Virüsten Koruma yeniden Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Microsoft Defender Virüsten Koruma Windows Server, sürüm 1803 veya sonraki bir sürüme yeniden yükleme](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Microsoft Defender Virüsten Koruma Server'da Windows moduna ayarlama](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Windows Server'da e-postayı yeniden yükleme veya yeniden Microsoft Defender Virüsten Koruma sorunlarıyla karşılaşılan varsa, bkz. sorun giderme[: Microsoft Defender Virüsten Koruma Windows Server'da kaldırıyor](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Microsoft virüsten koruma Microsoft Defender Virüsten Koruma durumları hakkında daha fazla bilgi edinmek için Uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).

### <a name="set-disableantispyware-to-false-on-windows-server"></a>Windows Server'da DisableAntiWare ayarını false olarak ayarlama

[Geçmişte DisableAntiCcaware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) kayıt defteri anahtarı, mcAfee, Microsoft Defender Virüsten Koruma gibi başka bir virüsten koruma ürününü devre dışı bırakmak ve dağıtmak için kullanılmıştır. **Genelde, Windows** cihazlarınıza ve uç noktalarınıza bu kayıt defteri anahtarınız sahip olmazsınız;  `DisableAntiSpyware` ancak, yapılandırmadınız varsa, değerini false olarak ayarlamak için şu şekilde ayarlanır:

1. Windows Server aygıtınızda Kayıt Defteri Düzenleyicisi'ni açın.

2. 'a gidin `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. Bu klasörde **DisableAntiWordsware** adlı bir DWORD girdisi bakın.
   - Bu girdiyi görmüyorsanız hazırsanız.
   - **DisableAnti Birware görüyorsanız**, 4. adıma geçin.

4. DisableAntiWordsware DWORD'e sağ tıklayın ve değiştir'i **seçin**.

5. Değeri olarak ayarlayın `0`. (Bu eylem kayıt defteri anahtarının değerini *false olarak ayarlar*.)

> [!TIP]
> Bu kayıt defteri anahtarı hakkında daha fazla bilgi edinmek için [bkz. DisableAntiAntiWare](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>E-posta Microsoft Defender Virüsten Koruma yeniden Windows Server 2016

Kötü Amaçlı Yazılımdan Koruma [ve Command-Line Yardımcı Programı'nı](command-line-arguments-microsoft-defender-antivirus.md) kullanarak, Microsoft Defender Virüsten Koruma yeniden Windows Server 2016.

1. Sunucu üzerinde yerel bir yönetici olarak Komut İstemi'ne açın.

2. Aşağıdaki konumu çalıştırın: `MpCmdRun.exe -wdenable`

3. Cihazı yeniden başlatın.


### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Microsoft Defender Virüsten Koruma Server, Windows Microsoft Defender Virüsten Koruma 1803 veya sonraki sürümler için yeniden etkinleştirme

> [!IMPORTANT]
> Aşağıdaki yordam yalnızca etki alanlarının aşağıdaki sürümlerini çalıştıran uç noktalar veya cihazlar Windows:
> - Windows Server 2019
> - Windows Server 2022
> - Windows Server, sürüm 1803 (yalnızca çekirdek modu)

1. Sunucu üzerinde yerel bir yönetici olarak Oturum Aç'Windows PowerShell.

2. Aşağıdaki PowerShell cmdlet'lerini çalıştırın:

   ```powershell
   # For Windows Server 2016
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Gui
   # For Windows Server 2019 and Windows Server 2022
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

   PowerShell'i çalıştıran bir görev sırası içinde DISM komutu kullanırken, bu komutlar için cmd.exe gerekir.
   Örneğin:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Cihazı yeniden başlatın.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Microsoft Defender Virüsten Koruma Server'da Windows moduna ayarlama

> [!TIP]
> Artık R2 ve Microsoft Defender Virüsten Koruma 2016'da pasif Windows Server 2012 çalıştırabilirsiniz. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender'ı yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Kayıt Defteri Düzenleyicisi'ni açın ve ardından

   ```text
   Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
   ```

2. **ForceDefenderPassiveMode** adlı bir DWORD girdisini düzenleyin (veya oluşturun) ve aşağıdaki ayarları belirtin:

   - DWORD değerini **1 olarak ayarlayın**.
   - **Taban'ın** altında **Onaltılı'ya seçin**.

> [!NOTE]
> Uç Nokta için Defender'a eklemeden sonra, Microsoft Defender Virüsten Koruma Server'da pasif moduna Windows gerekir. Pasif modunun beklendiği gibi ayarlanmış olduğunu doğrulamak için **, Microsoft-Windows-Windows Defender** İşlem günlüğünde (`C:\Windows\System32\winevt\Logs`burada) *5007'i* arayın ve **ForceDefenderPassiveMode** veya **EdilgenMode** kayıt defteri anahtarlarının Onay ile ayarlandıktan sonra **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Windows Server 2012 R2 veya Windows Server 2016?

Yukarıdaki yöntemi kullanarak Microsoft Defender Virüsten Koruma R2 ve 2016 Windows Server 2012 pasif modunda çalıştırabilirsiniz. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender'ı yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Uç Nokta için Defender'ı Yapılandırma

Geçiş işleminin bu adımı, uç Microsoft Defender Virüsten Koruma yapılandırmayı içerir. Intune'i öneririz; bununla birlikte, aşağıdaki tabloda listelenen yöntemlerden herhangi birini yapabilirsiniz:
<br/><br/>

|Yöntem|Ne yapmalı?|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **NOT**: Intune artık bu iş Microsoft Endpoint Manager.|1. Yönetim merkezine [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açma.<br/><br/>2. **Cihazlar** \> **Yapılandırma profilleri'ne** ve sonra yapılandırmak istediğiniz profil türünü seçin. Henüz bir Cihaz kısıtlamaları profil türü oluşturmadısanız veya yeni bir profil türü oluşturmak için bkz. Cihaz kısıtlama ayarlarını yapılandırma [Microsoft Intune.](/intune/device-restrictions-configure)<br/><br/>3. **Özellikler'i** ve ardından Yapılandırma ayarları: **Düzenle'yi seçin**<br/><br/>4. Genişletme **Microsoft Defender Virüsten Koruma**.<br/><br/>5. Bulut **teslimi korumasını etkinleştirin**.<br/><br/>6. Örnek **göndermeden önce kullanıcılara sor açılan listesinde** Tüm örnekleri otomatik **olarak gönder'i seçin**.<br/><br/>7. **İstenmeyen olabilecek uygulamaları algıla açılan** listesinde Etkinleştir'i veya **Denetim'i** **seçin**.<br/><br/>8. Gözden **Geçir + kaydet'i** ve sonra Kaydet'i **seçin**. <br/><br/> **İpucu**: Intune cihaz profilleri hakkında daha fazla bilgi ve ayarlarını oluşturma ve yapılandırma gibi bilgiler için bkz. [Microsoft Intune profili nedir?](/intune/device-profiles)|
|Microsoft Uç Noktası Yapılandırma Yöneticisi|[Configuration Manager'da güvenlik ilkeleri oluşturmak ve Endpoint Protection için bkz](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Kötü amaçlı yazılımdan koruma ilkelerinizi 2013'e ayarlarken, [](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) gerçek zamanlı koruma ayarlarını gözden geçirmeyi ve engellemeyi ilk [görüşte etkinleştirmeyi unutmayın](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|Denetim Masası'Windows|Buradaki yönergeleri izleyin: [Microsoft Defender Virüsten Koruma](/mem/intune/user-help/turn-on-defender-windows). (Bazı dosya *Windows Defender Virüsten Koruma* yerine *başka Microsoft Defender Virüsten Koruma* e-Windows.)|
|[Gelişmiş Grup İlkesi Yönetimi](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> veya <br/><br/> [Grup İlkesi Yönetim Konsolu](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Bilgisayar **yapılandırması Yönetim şablonları** \> **ve** \> **Windows** **şablonları'Microsoft Defender Virüsten Koruma**\>.<br/><br/>2. Bu ayarı kapatma adlı **bir ilke Microsoft Defender Virüsten Koruma**.<br/><br/>3. İlke **ayarını düzenle'yi** seçin ve ilkenin devre dışı bırakıldı olduğundan emin olun. Bu eylem, e-Microsoft Defender Virüsten Koruma. <br/>(Bazı dosya *Windows Defender Virüsten Koruma* yerine *başka Microsoft Defender Virüsten Koruma* e-Windows.)|

> [!TIP]
> İlkeleri, kuruma yönelik cihazlar eklemeden önce dağıtabilirsiniz.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Var olan çözümünüz için dışlama listesine Uç Nokta için Microsoft Defender ekleme

Kurulum işleminin bu adımı, var olan uç nokta koruma çözümünüz ve kurumuz tarafından kullanan diğer tüm güvenlik ürünlerinin dışlama listesine Uç Nokta için Defender eklemeyi içerir.

> [!TIP]
> Dışlamaları yapılandırmayla ilgili yardım almak için çözüm sağlayıcınızın belgelerine bakın.

Yapılandırılan belirli dışlamalar, uç nokta veya Windows kullandığınız sürüme bağlı olarak çalışır ve aşağıdaki tabloda listelenmiştir.
<br/><br/>

| işletim sistemi |Dışlamalar |
|:--|:--|
|Windows 11 <br/><br/>Windows 10 sürüm [1803 veya](/windows/release-health/status-windows-10-1803) sonraki sürümü (Bkz. [Windows 10 sürüm bilgilerini görme](/windows/release-health/release-information))<br/><br/>Windows 10 [KB4493441](https://support.microsoft.com/help/4493441) yüklü olan sürüm 1703 veya 1709 <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, sürüm 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>Buna ek olarak, modern, birleşik çözümü çalıştıran Windows Server 2012 R2 ve 2016'da[, KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) kullanarak Sense EDR bileşenini güncelleştirdikten sonra aşağıdaki dışlamalar gereklidir:<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**NOT**: Ana Bilgisayar Geçici Dosyalarını İzleme 6\45 farklı numaralandırıldı alt klasörler olabilir.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Var olan çözümlerinizi dışlama listesine sizin için Microsoft Defender Virüsten Koruma

Kurulum işleminin bu adımı sırasında, var olan çözümlerinizi dışlama listesine Microsoft Defender Virüsten Koruma eklersiniz. Dışlamalarınızı dışlamalarınızı aşağıdaki tabloda Microsoft Defender Virüsten Koruma yöntemlerden birini seçebilirsiniz:
<br/><br/>

|Yöntem|Ne yapmalı?|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **NOT**: Intune artık bu iş Microsoft Endpoint Manager.|1. Yönetim merkezine [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açma.<br/><br/>2. **Cihazlar** \> **Yapılandırma profilleri'ne** tıklayın ve sonra yapılandırmak istediğiniz profili seçin.<br/><br/>3. **Yönet'in altında** Özellikler'i **seçin**.<br/><br/>4. Yapılandırma **ayarları: Düzenle'yi seçin**.<br/><br/>5. **Dışlamalar Microsoft Defender Virüsten Koruma** ve sonra **Dışlamalar Microsoft Defender Virüsten Koruma genişletin**.<br/><br/>6. Taramaların dışında tutulacak dosyaları ve klasörleri, uzantıları ve işlemleri Microsoft Defender Virüsten Koruma. Başvuru için bkz. [Microsoft Defender Virüsten Koruma dışı bırakmalar](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. Gözden **Geçir + kaydet'i** ve sonra Kaydet'i **seçin**.|
|[Microsoft Uç Noktası Yapılandırma Yöneticisi](/mem/configmgr/)|1. [Yapılandırma Yöneticisi](/mem/configmgr/core/servers/manage/admin-console) konsolunu kullanarak Varlıklar  \> ve Uyumluluk **Endpoint Protection** \> **Kötü** Amaçlı Yazılım İlkeleri'ne gidin ve değiştirmek istediğiniz ilkeyi seçin.<br/><br/>2. Dosya ve klasörler, uzantılar ve işlemler için, taramaların dışında tutulacak dışlama Microsoft Defender Virüsten Koruma belirtin.|
|[Grup İlke Nesnesi](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. Grup İlkesi yönetim bilgisayarınızda, Grup İlkesi Yönetim Konsolu'nu [açın, yapılandırmak](https://technet.microsoft.com/library/cc731212.aspx) istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.<br/><br/>2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.<br/><br/>3. Dışlamalar'da **Windows Microsoft Defender Virüsten Koruma \> \> genişletin**. (Bazı dosya *Windows Defender Virüsten Koruma* yerine *başka Microsoft Defender Virüsten Koruma* e-Windows.)<br/><br/>4. Yol Dışlamaları **ayarına çift tıklayın** ve dışlamaları ekleyin.<br/><br/>5. Seçeneği Etkin olarak **ayarlayın**.<br/><br/>6. Seçenekler bölümünün **altında** Göster **... öğesini seçin**.<br/><br/>7. Her klasörü Değer adı sütununu altında kendi **satırına** belirtin. Bir dosya belirtirsanız, dosyanın sürücü harfi, klasör yolu, dosya adı ve uzantıyla birlikte tam bir yol girmeye emin olun. Değer **sütununa 0** **girin.**<br/><br/>8. **Tamam'ı seçin**.<br/><br/>9. Uzantı Dışlamaları **ayarına çift tıklayın** ve dışlamaları ekleyin.<br/><br/>10. Seçeneği Etkin olarak **ayarlayın**.<br/><br/>11. Seçenekler bölümünün **altında** Göster **... öğesini seçin**.<br/><br/>12. Her dosya uzantısını Değer adı sütununu altına kendi **satırına** girin. Değer **sütununa 0** **girin.**<br/><br/>13. Tamam'ı **seçin**.|
|Yerel grup ilkesi nesnesi|1. Uç noktada veya cihazda, Yerel Grup İlkesi Düzenleyicisi'ni açın.<br/><br/>2. Bilgisayar Yapılandırması **Yönetim Şablonları ve** \> **Bileşenler Windows** \> **Özel** \> **Microsoft Defender Virüsten Koruma** \> **gidin**. (Bazı dosya *Windows Defender Virüsten Koruma* yerine *başka Microsoft Defender Virüsten Koruma* e-Windows.)<br/><br/>3. Yol ve işlem dışlamalarınızı belirtin.|
|Kayıt defteri anahtarı|1. Şu kayıt defteri anahtarını dışarı aktarın: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Kayıt defteri anahtarını içeri aktarın. İşte iki örnek:<br/>- Yerel yol: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>- Ağ paylaşımı: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Dışlamalar hakkında aşağıdaki noktaları unutmayın

Bu taramalara [dışlamalar Microsoft Defender Virüsten Koruma,](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) yol ve işlem dışlamaları ekley gerekir.

Aşağıdaki noktaları unutmayın:

- *Yol dışlamaları* belirli dosyaları ve bu dosyalara erişimle ilgili her türlü erişimi dışlar.
- *süreç dışlamaları* , bir işleme dokunan her şeyi hariç tutmaz, ancak sürecin kendisini dışlamaz.
- İşlem dışlamalarınızı yalnızca adlarına göre değil, tam yolları kullanarak listele. (Yalnızca ad yöntemi daha az güvenlidir.)
- Her yürütülebilir dosyayı (.exe) hem yol dışlama hem de sürecin dışlanması olarak listelersanız, işlem ve dokunduğu her şey dışlar.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Cihaz gruplarınızı, cihaz koleksiyonlarınızı ve kuruluş birimlerinizi ayarlama

Cihaz grupları, cihaz koleksiyonları ve kuruluş birimleri, güvenlik ekibimizin güvenlik ilkelerini verimli ve etkili bir şekilde yönetmelerini ve atamalarını sağlar. Aşağıdaki tabloda bu grupların her biri ve bunların nasıl yapılandırıldıları açık almaktadır. Organizasyonunız üç koleksiyon türü de kullanmay olabilir.
<br/><br/>

|Koleksiyon türü|Ne yapmalı?|
|---|---|
|[Cihaz grupları](/microsoft-365/security/defender-endpoint/machine-groups) (eski adı *makine grupları*), güvenlik işlemleri ekibimizin otomatik araştırma ve düzeltme gibi güvenlik özelliklerini yapılandırmasını sağlar. <br/><br/> Cihaz grupları, güvenlik işlemleri ekibimizin gerekirse düzeltme eylemleri gerçekleştirsin diye bu cihazlara erişim atamak için de yararlıdır. <br/><br/> Saldırı algılandığında ve durdurulurken "ilk erişim uyarısı" gibi uyarılar tetiklenir ve [Microsoft 365 Defender portalda görüldü](/microsoft-365/security/defender/microsoft-365-defender).|1. Portala () Microsoft 365 Defender gidin<https://security.microsoft.com>.<br/><br/>2. Sol gezinti bölmesinde, Uç Nokta İzinleri **Cihaz** **Ayarlar'ı** \> \> **seçin**\>.<br/><br/>3. **+ Cihaz grubu ekle'yi seçin**.<br/><br/>4. Cihaz grubu için bir ad ve açıklama belirtin.<br/><br/>5. **Otomasyon düzeyi listesinde** bir seçenek belirtin. (Tam - **otomatik olarak tehditleri düzeltmenizi öneririz**.) Çeşitli otomasyon düzeyleri hakkında daha fazla bilgi edinmek için bkz [. Tehditlerin düzeltmesi](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Cihaz grubuna hangi cihazların ait olduğunu belirlemek üzere eşleşen bir kural için koşullar belirtin. Örneğin, bir etki alanı, işletim sistemi sürümü seçebilir ve hatta cihaz [etiketlerini kullanabilirsiniz](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. **Kullanıcı erişimi** sekmesinde, cihaz grubuna dahil olan cihazlara erişimi olması gereken rolleri belirtin.<br/><br/>8. **Bitti'yi seçin**.|
|[Cihaz koleksiyonları](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) , güvenlik işlemleri ekibimizin uygulamaları yönetmesini, uyumluluk ayarlarını dağıtmalarını veya kuruluş cihazlarına yazılım güncelleştirmeleri yüklemesini sağlar. <br/><br/> Cihaz koleksiyonları Configuration [Manager kullanılarak oluşturulur](/mem/configmgr/).|Koleksiyon [oluşturma'daki adımları izleyin](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Kuruluş birimleri](/azure/active-directory-domain-services/create-ou) kullanıcı hesapları, hizmet hesapları veya bilgisayar hesapları gibi nesneleri mantıksal olarak gruplama olanağı sağlar. <br/><br/> Ardından yöneticileri belirli kuruluş birimlerine atayın ve hedefli yapılandırma ayarlarını zorunlu kılınacak grup ilkesi uygulayabilirsiniz. <br/><br/> Kuruluş birimleri Etki Alanı [Hizmetleri Azure Active Directory'de tanımlanır](/azure/active-directory-domain-services).|Etki Alanı Hizmetleri tarafından [yönetilen bir etki alanında Kuruluş Azure Active Directory oluşturma'daki adımları izleyin](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! Uç nokta için [Defender'a geçişin Kurulum aşamasını tamamladınız](switch-to-mde-overview.md#the-migration-process)!

- [Aşama 3: Uç nokta için Defender'a Ekleme ile devam edin](switch-to-mde-phase-3.md)
