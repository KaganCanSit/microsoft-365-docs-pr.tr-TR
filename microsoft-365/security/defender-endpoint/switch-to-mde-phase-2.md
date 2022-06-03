---
title: Uç Nokta için Microsoft Defender geçiş - Kurulum
description: Uç Nokta için Defender'a geçiş yapın. Microsoft Defender Virüsten Koruma yüklemeyi de içeren kurulum işlemini gözden geçirin.
keywords: geçiş, Uç Nokta için Microsoft Defender, virüsten koruma, pasif mod, kurulum işlemi
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
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: fe789a8f4eaaee68fd18832b5d45125407525ccd
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873908"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Uç Nokta için Microsoft Defender Geçiş - 2. Aşama: Kurulum

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![1. Aşama: Hazırlanın.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Aşama 1: Hazırlık](switch-to-mde-phase-1.md)|![2. Aşama: Ayarlama.](images/phase-diagrams/setup.png#lightbox)<br/>Aşama 2: Kurulum|[![3. Aşama: Ekleme3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Aşama 3: Katılım](switch-to-mde-phase-3.md)|
|---|---|---|
||*Buradasınız!*||

**[Uç Nokta için Defender'a geçmenin Kurulum aşamasına](switch-to-mde-overview.md#the-migration-process) hoş geldiniz**. Bu aşama aşağıdaki adımları içerir:

1. [Uç noktalarınızda Microsoft Defender Virüsten Koruma yeniden yükleyin/etkinleştirin](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Uç Nokta için Defender'ı yapılandırın](#configure-defender-for-endpoint).
3. [Mevcut çözümünüz için dışlama listesine Uç Nokta için Defender'ı ekleyin](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Mevcut çözümünüzü Microsoft Defender Virüsten Koruma için dışlama listesine ekleyin](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Cihaz gruplarınızı, cihaz koleksiyonlarınızı ve kuruluş birimlerinizi ayarlayın](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Uç noktalarınızda Microsoft Defender Virüsten Koruma yeniden yükleme/etkinleştirme

Windows'ın belirli sürümlerinde, Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma çözümünüz yüklendiğinde Microsoft Defender Virüsten Koruma büyük olasılıkla kaldırılmış veya devre dışı bırakılmıştır. Windows çalıştıran uç noktalar Uç Nokta için Defender'a eklendiğinde, Microsoft Defender Virüsten Koruma Microsoft dışı bir virüsten koruma çözümünün yanı sıra pasif modda çalıştırılabilir. Daha fazla bilgi için bkz [. Uç Nokta için Defender ile virüsten koruma](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Uç Nokta için Defender'a geçiş yaparken, Microsoft Defender Virüsten Koruma yeniden yüklemek veya etkinleştirmek için belirli adımları uygulamanız gerekebilir. Aşağıdaki tabloda, Windows istemcilerinizde ve sunucularınızda ne yapabileceğiniz açıklanmaktadır.

|Uç nokta türü|Yapılması gerekenler|
|---|---|
|Windows istemcileri (Windows 10 ve Windows 11 çalıştıran uç noktalar gibi)|Genel olarak, Windows istemcileri için herhangi bir işlem yapmanız gerekmez (Microsoft Defender Virüsten Koruma kaldırılmadığı sürece). Genel olarak, Microsoft Defender Virüsten Koruma hala yüklü olmalıdır, ancak büyük olasılıkla geçiş işleminin bu noktasında devre dışı bırakılmıştır. <br/><br/> Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü yüklüyse ve istemciler henüz Uç Nokta için Defender'a eklenmediğinde, Microsoft Defender Virüsten Koruma otomatik olarak devre dışı bırakılır. Daha sonra istemci uç noktaları Uç Nokta için Defender'a eklendiğinde, bu uç noktalar Microsoft dışı bir virüsten koruma çözümü çalıştırıyorsa Microsoft Defender Virüsten Koruma pasif moda geçer. <br/><br/> Microsoft dışı virüsten koruma çözümü kaldırılırsa Microsoft Defender Virüsten Koruma otomatik olarak etkin moda geçer.|
|Windows sunucuları|Windows Server'da, Microsoft Defender Virüsten Koruma yeniden yüklemeniz ve el ile pasif moda ayarlamanız gerekir. Windows sunucularda, Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma yazılımı yüklendiğinde Microsoft Defender Virüsten Koruma Microsoft dışı virüsten koruma çözümüyle birlikte çalışamaz. Bu gibi durumlarda, Microsoft Defender Virüsten Koruma devre dışı bırakılır veya el ile kaldırılır. <br/><br/> Windows Server'da Microsoft Defender Virüsten Koruma yeniden yüklemek veya etkinleştirmek için aşağıdaki görevleri gerçekleştirin: <br/>- [Microsoft Defender Virüsten Koruma Windows Server 2016 yeniden yükleme](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Microsoft Defender Virüsten Koruma Windows Server, sürüm 1803 veya sonraki bir sürüme yeniden yükleyin](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Windows Sunucusu'nda Microsoft Defender Virüsten Koruma pasif moda ayarlama](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Windows Server'da Microsoft Defender Virüsten Koruma yeniden yükleme veya yeniden etkinleştirme sorunlarıyla karşılaşırsanız bkz[. Sorun Giderme: Microsoft Defender Virüsten Koruma Windows Sunucusunda kaldırılıyor](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Microsoft dışı virüsten koruma ile Microsoft Defender Virüsten Koruma durumları hakkında daha fazla bilgi edinmek için bkz. [uyumluluk Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>Windows Server 2016'da Microsoft Defender Virüsten Koruma yeniden etkinleştirme

Windows Server 2016 Microsoft Defender Virüsten Koruma yeniden etkinleştirmek için [Kötü Amaçlı Yazılımdan Koruma Command-Line Yardımcı Programı'nı](command-line-arguments-microsoft-defender-antivirus.md) kullanabilirsiniz.

1. Sunucuda yerel yönetici olarak Komut İstemi'ni açın.

2. Aşağıdaki komutu çalıştırın: `MpCmdRun.exe -wdenable`

3. Cihazı yeniden başlatın.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Windows Server, sürüm 1803 veya sonraki sürümlerde Microsoft Defender Virüsten Koruma yeniden etkinleştirme

> [!IMPORTANT]
> Aşağıdaki yordam yalnızca aşağıdaki Windows sürümlerini çalıştıran uç noktalar veya cihazlar için geçerlidir:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Sunucusu, sürüm 1803 (yalnızca çekirdek modu)

1. Sunucuda yerel yönetici olarak Windows PowerShell açın.

2. Aşağıdaki PowerShell cmdlet'lerini çalıştırın:

   ```powershell
   # For Windows Server 2016
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Gui
   # For Windows Server 2019 and Windows Server 2022
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

   DISM komutunu PowerShell çalıştıran bir görev dizisi içinde kullanırken, aşağıdaki cmd.exe yolu gereklidir.
   Örneğin:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Cihazı yeniden başlatın.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Windows Sunucusu'nda Microsoft Defender Virüsten Koruma pasif moda ayarlama

> [!TIP]
> Artık Microsoft Defender Virüsten Koruma Windows Server 2012 R2 ve 2016'da pasif modda çalıştırabilirsiniz. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Kayıt Defteri Düzenleyicisi'ni açın ve öğesine `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`gidin.

2. **ForceDefenderPassiveMode** adlı bir DWORD girdisini düzenleyin (veya oluşturun) ve aşağıdaki ayarları belirtin:

   - DWORD değerini **1** olarak ayarlayın.

   - **Temel'in** altında **Onaltılık** seçeneğini belirleyin.

> [!NOTE]
> Uç Nokta için Defender'a eklendikten sonra Microsoft Defender Virüsten Koruma Windows Sunucusu'nda pasif moda ayarlamanız gerekebilir. Pasif modun beklendiği gibi ayarlandığını doğrulamak için **Microsoft-Windows-Windows Defender İşletim** günlüğünde (konumunda `C:\Windows\System32\winevt\Logs`bulunur) *5007 olayını* arayın ve **ForceDefenderPassiveMode** veya **PassiveMode** kayıt defteri anahtarlarının **tarafından 0x1** olarak ayarlandığını onaylayın.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Windows Server 2012 R2 mi yoksa Windows Server 2016 mi kullanıyorsunuz?

Artık yukarıdaki yöntemi kullanarak Microsoft Defender Virüsten Koruma Windows Server 2012 R2 ve 2016'da pasif modda çalıştırabilirsiniz. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Uç Nokta için Defender'ı yapılandırma

Geçiş işleminin bu adımı, uç noktalarınız için Microsoft Defender Virüsten Koruma yapılandırmayı içerir. Intune kullanmanızı öneririz; ancak aşağıdaki tabloda listelenen yöntemlerden herhangi birini kullanabilirsiniz:

|Yöntem|Yapılması gerekenler|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **NOT**: Intune artık Microsoft Endpoint Manager bir parçasıdır.|1. [Microsoft Endpoint Manager yönetim merkezine](https://go.microsoft.com/fwlink/?linkid=2109431) gidin ve oturum açın.<br/><br/>2. **Cihazlar** \> **Yapılandırma profilleri'ni** seçin ve ardından yapılandırmak istediğiniz profil türünü seçin. Henüz bir **Cihaz kısıtlamaları** profil türü oluşturmadıysanız veya yeni bir tane oluşturmak istiyorsanız bkz. [Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure).<br/><br/>3. **Özellikler'i** ve ardından **Yapılandırma ayarları: Düzenle'yi** seçin<br/><br/>4. **Microsoft Defender Virüsten Koruma** genişletin.<br/><br/>5. **Bulut tabanlı korumayı** etkinleştirin.<br/><br/>6. **Kullanıcılara örnek göndermeden önce sor** açılan listesinde **Tüm örnekleri otomatik olarak gönder'i** seçin.<br/><br/>7. **İstenmeyebilecek uygulamaları algıla** açılan listesinde **Etkinleştir veya Denetle'yi** seçin.<br/><br/>8. **Gözden geçir + kaydet'i** ve ardından **Kaydet'i** seçin. <br/><br/> **İpucu**: Ayarlarını oluşturma ve yapılandırma da dahil olmak üzere Intune cihaz profilleri hakkında daha fazla bilgi için bkz. [Microsoft Intune cihaz profilleri nedir?](/intune/device-profiles).|
|Microsoft Uç Noktası Yapılandırma Yöneticisi|Bkz. [Configuration Manager'da Endpoint Protection için kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Kötü amaçlı yazılımdan koruma ilkelerinizi oluştururken ve yapılandırırken [, gerçek zamanlı koruma ayarlarını](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) gözden geçirmeyi ve [ilk bakışta engellemeyi etkinleştirmeyi](configure-block-at-first-sight-microsoft-defender-antivirus.md) unutmayın.
|Windows'da Denetim Masası|Buradaki yönergeleri izleyin: [Microsoft Defender Virüsten Koruma açın](/mem/intune/user-help/turn-on-defender-windows). (*bazı Windows* sürümlerinde *Microsoft Defender Virüsten Koruma* yerine Windows Defender Virüsten Koruma görebilirsiniz.)|
|[Gelişmiş grup ilkesi Yönetimi](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> veya <br/><br/> [Grup İlkesi Yönetim Konsolu](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. **Bilgisayar yapılandırması** \> **Yönetim şablonları** \> **Windows bileşenler** \> **Microsoft Defender Virüsten Koruma** gidin.<br/><br/>2. **Microsoft Defender Virüsten Koruma kapat** adlı bir ilke arayın.<br/><br/>3. **İlke ayarını düzenle'yi** seçin ve ilkenin devre dışı bırakıldıkdan emin olun. Bu eylem Microsoft Defender Virüsten Koruma etkinleştirir. <br/>(*bazı Windows* sürümlerinde *Microsoft Defender Virüsten Koruma* yerine Windows Defender Virüsten Koruma görebilirsiniz.)|

> [!TIP]
> İlkeleri kuruluşunuzun cihazları eklemeden önce dağıtabilirsiniz.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Mevcut çözümünüz için dışlama listesine Uç Nokta için Microsoft Defender ekleme

Kurulum işleminin bu adımı, mevcut uç nokta koruma çözümünüz ve kuruluşunuzun kullandığı diğer güvenlik ürünlerinin dışlama listesine Uç Nokta için Defender'ı eklemeyi içerir.

> [!TIP]
> Dışlamaları yapılandırma konusunda yardım almak için çözüm sağlayıcınızın belgelerine bakın.

Yapılandırılacak özel dışlamalar, uç noktalarınızın veya cihazlarınızın hangi Windows sürümünün çalıştığına ve aşağıdaki tabloda listelendiğine bağlıdır.

| OS |Dışlamalar |
|:--|:--|
|Windows 11 <br/><br/>Windows 10, [sürüm 1803](/lifecycle/announcements/windows-server-1803-end-of-servicing) veya üzeri ([Windows 10 sürüm bilgilerine](/windows/release-health/release-information) bakın)<br/><br/>[kb4493441](https://support.microsoft.com/help/4493441) yüklü Windows 10, sürüm 1703 veya 1709 <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Sunucusu, sürüm 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>Ayrıca, modern, birleşik çözümü çalıştıran Windows Server 2012 R2 ve 2016'da[, KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) kullanarak Sense EDR bileşenini güncelleştirdikten sonra aşağıdaki dışlamalar gereklidir:<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**NOT**: Konak Geçici Dosyalarını İzleme 6\45 farklı numaralı alt klasörler olabilir.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Mevcut çözümünüzü Microsoft Defender Virüsten Koruma için dışlama listesine ekleme

Kurulum işleminin bu adımı sırasında, mevcut çözümünüzü Microsoft Defender Virüsten Koruma dışlama listesine eklersiniz. Aşağıdaki tabloda listelendiği gibi dışlamalarınızı Microsoft Defender Virüsten Koruma eklemek için çeşitli yöntemler arasından seçim yapabilirsiniz: 

|Yöntem|Yapılması gerekenler|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **NOT**: Intune artık Microsoft Endpoint Manager bir parçasıdır.|1. [Microsoft Endpoint Manager yönetim merkezine](https://go.microsoft.com/fwlink/?linkid=2109431) gidin ve oturum açın.<br/><br/>2. **Cihazlar** \> **Yapılandırma profilleri'ni** seçin ve ardından yapılandırmak istediğiniz profili seçin.<br/><br/>3. **Yönet'in** altında **Özellikler'i** seçin.<br/><br/>4. **Yapılandırma ayarları: Düzenle'yi** seçin.<br/><br/>5. **Microsoft Defender Virüsten Koruma** genişletin ve Microsoft Defender Virüsten Koruma **Dışlamalar'ı** genişletin.<br/><br/>6. Microsoft Defender Virüsten Koruma taramalarının dışında tutulacak dosya ve klasörleri, uzantıları ve işlemleri belirtin. Başvuru için bkz. [Microsoft Defender Virüsten Koruma dışlamalar](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. **Gözden geçir + kaydet'i** ve ardından **Kaydet'i** seçin.|
|[Microsoft Uç Noktası Yapılandırma Yöneticisi](/mem/configmgr/)|1. [Configuration Manager konsolunu](/mem/configmgr/core/servers/manage/admin-console) kullanarak **Varlıklar ve Uyumluluk** \> **Endpoint Protection** \> **Kötü Amaçlı Yazılımdan Koruma İlkeleri'ne** gidin ve değiştirmek istediğiniz ilkeyi seçin.<br/><br/>2. Microsoft Defender Virüsten Koruma taramalarının dışında tutulacak dosya ve klasörler, uzantılar ve işlemler için dışlama ayarlarını belirtin.|
|[Grup İlke Nesnesi](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve düzenle'yi seçin.<br/><br/>2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.<br/><br/>3. **Dışlamalar Microsoft Defender Virüsten Koruma bileşenleri \> Windows \>** için ağacı genişletin. (*bazı Windows* sürümlerinde *Microsoft Defender Virüsten Koruma* yerine Windows Defender Virüsten Koruma görebilirsiniz.)<br/><br/>4. **Yol Dışlamaları** ayarına çift tıklayın ve dışlamaları ekleyin.<br/><br/>5. Seçeneği **Etkin** olarak ayarlayın.<br/><br/>6. **Seçenekler** bölümünün altında **Göster...** öğesini seçin.<br/><br/>7. **Her klasörü Değer adı** sütununun altında kendi satırında belirtin. Bir dosya belirtirseniz, sürücü harfi, klasör yolu, dosya adı ve uzantı da dahil olmak üzere dosyanın tam yolunu girdiğinizden emin olun. **Değer** sütununa **0** girin.<br/><br/>8. **Tamam'ı** seçin.<br/><br/>9. **Uzantı Dışlamaları** ayarına çift tıklayın ve dışlamaları ekleyin.<br/><br/>10. Seçeneği **Etkin** olarak ayarlayın.<br/><br/>11. **Seçenekler** bölümünün altında **Göster...** öğesini seçin.<br/><br/>12. Her dosya uzantısını **Değer adı** sütununun altına kendi satırına girin. **Değer** sütununa **0** girin.<br/><br/>13. **Tamam'ı** seçin.|
|Yerel grup ilkesi nesnesi|1. Uç nokta veya cihazda Yerel grup ilkesi Düzenleyicisi'ni açın.<br/><br/>2. **Bilgisayar Yapılandırması** \> **Yönetim Şablonları** \> **Windows Bileşenler** \> **Microsoft Defender Virüsten Koruma** \> **Dışlamalar'a** gidin. (*bazı Windows* sürümlerinde *Microsoft Defender Virüsten Koruma* yerine Windows Defender Virüsten Koruma görebilirsiniz.)<br/><br/>3. Yolunuzu ve işlem dışlamalarınızı belirtin.|
|Kayıt defteri anahtarı|1. Aşağıdaki kayıt defteri anahtarını dışarı aktarın: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Kayıt defteri anahtarını içeri aktarın. burada iki örnek verilmiştir:<br/>- Yerel yol: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>- Ağ paylaşımı: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Dışlamalar hakkında aşağıdaki noktaları göz önünde bulundurun

[Microsoft Defender Virüsten Koruma taramalarına dışlamalar](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) eklediğinizde yol ve işlem dışlamaları eklemeniz gerekir.

Aşağıdaki noktaları göz önünde bulundurun:

- *Yol dışlamaları* belirli dosyaları ve bu dosyaların eriştikleri her şeyi dışlar.
- *İşlem dışlamaları* , bir işlemin dokunduğu her şeyi dışlar, ancak işlemin kendisini dışlamaz.
- İşlem dışlamalarınızı yalnızca adlarıyla değil tam yollarını kullanarak listeleyin. (Yalnızca ad yöntemi daha az güvenlidir.)
- Her yürütülebilir dosyayı (.exe) hem yol dışlama hem de işlem dışlaması olarak listelerseniz, işlem ve dokunduğu her şey dışlanır.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Cihaz gruplarınızı, cihaz koleksiyonlarınızı ve kuruluş birimlerinizi ayarlama

Cihaz grupları, cihaz koleksiyonları ve kuruluş birimleri, güvenlik ekibinizin güvenlik ilkelerini verimli ve etkili bir şekilde yönetmesine ve atamasına olanak tanır. Aşağıdaki tabloda bu grupların her biri ve bunların nasıl yapılandırıldığı açıklanmaktadır. Kuruluşunuz üç koleksiyon türünün tümünü de kullanmayabilir.

|Koleksiyon türü|Yapılması gerekenler|
|---|---|
|[Cihaz grupları](/microsoft-365/security/defender-endpoint/machine-groups) (eski adı *makine grupları*), güvenlik operasyonları ekibinizin otomatik araştırma ve düzeltme gibi güvenlik özelliklerini yapılandırmasına olanak tanır. <br/><br/> Cihaz grupları, güvenlik operasyonları ekibinizin gerekirse düzeltme eylemleri gerçekleştirebilmesi için bu cihazlara erişim atamak için de kullanışlıdır. <br/><br/> Cihaz grupları, Saldırı algılanıp durdurulurken, "ilk erişim uyarısı" gibi uyarılar tetiklenir ve [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) görüntülenir.|1. Microsoft 365 Defender portalına (<https://security.microsoft.com>) gidin.<br/><br/>2. Sol taraftaki gezinti bölmesinde **Uç Noktalar İzinleri** \>  \> **Cihaz** **grupları'nı Ayarlar** \> seçin.<br/><br/>3. **+ Cihaz grubu ekle'yi** seçin.<br/><br/>4. Cihaz grubu için bir ad ve açıklama belirtin.<br/><br/>5. **Otomasyon düzeyi** listesinde bir seçenek belirleyin. ( **Tam - tehditleri otomatik olarak düzeltmenizi** öneririz.) Çeşitli otomasyon düzeyleri hakkında daha fazla bilgi edinmek için bkz. [Tehditler nasıl düzeltilir](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated)?<br/><br/>6. Hangi cihazların cihaz grubuna ait olduğunu belirlemek için eşleşen bir kural için koşulları belirtin. Örneğin, bir etki alanı, işletim sistemi sürümü seçebilir veya hatta [cihaz etiketlerini](/microsoft-365/security/defender-endpoint/machine-tags) kullanabilirsiniz.<br/><br/>7. **Kullanıcı erişimi** sekmesinde, cihaz grubuna dahil edilen cihazlara erişimi olması gereken rolleri belirtin.<br/><br/>8. **Bitti'yi** seçin.|
|[Cihaz koleksiyonları](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) , güvenlik operasyonları ekibinizin uygulamaları yönetmesine, uyumluluk ayarlarını dağıtmasına veya kuruluşunuzdaki cihazlara yazılım güncelleştirmeleri yüklemesine olanak tanır. <br/><br/> Cihaz koleksiyonları [Configuration Manager](/mem/configmgr/) kullanılarak oluşturulur.|[Koleksiyon oluşturma](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create) başlığındaki adımları izleyin.|
|[Kuruluş birimleri](/azure/active-directory-domain-services/create-ou) , kullanıcı hesapları, hizmet hesapları veya bilgisayar hesapları gibi nesneleri mantıksal olarak gruplandırmanızı sağlar. <br/><br/> Ardından yöneticileri belirli kuruluş birimlerine atayabilir ve hedeflenen yapılandırma ayarlarını zorunlu kılmak için grup ilkesi uygulayabilirsiniz. <br/><br/> Kuruluş birimleri [Azure Active Directory Etki Alanı Hizmetleri'nde](/azure/active-directory-domain-services) tanımlanır.|[Azure Active Directory Domain Services yönetilen etki alanında Kuruluş Birimi oluşturma başlığı altında yer alan](/azure/active-directory-domain-services/create-ou) adımları izleyin.|

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! [Uç Nokta için Defender'a geçmenin Kurulum aşamasını](switch-to-mde-overview.md#the-migration-process) tamamladınız!

- [3. Aşamaya Geçin: Uç Nokta için Defender'a ekleme](switch-to-mde-phase-3.md)
