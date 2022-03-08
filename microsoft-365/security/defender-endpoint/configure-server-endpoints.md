---
title: Uç Windows için Microsoft Defender hizmetine ek sunucu ekleme
description: Algılayıcı Windows uç nokta algılayıcısı için Microsoft Defender'a algılayıcı verilerini gönderemleri için kullanıcı sunucularını kullanın.
keywords: onboard sunucusu, sunucu, 2012r2, 2016, 2019, sunucu ekleme, cihaz yönetimi, Uç nokta sunucuları için Microsoft Defender'ı yapılandırma, Uç nokta sunucuları için Microsoft Defender'ı ekleme, Uç nokta sunucuları için Microsoft Defender'ı ekleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2979216cb87982210ac33dd8e273702f8bc18bf0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328099"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Uç Windows için Microsoft Defender hizmetine ek sunucu ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Windows Server 2012 R2
- Windows Server 2016
- Windows Server Semi-Annual Enterprise Kanalı
- Windows Server 2019 ve sonrası
- Windows Server 2019 çekirdek sürümü
- Windows Server 2022
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Uç Nokta için Defender, desteği Windows Server işletim sistemini de içerecek şekilde genişlettir. Bu destek, gelişmiş saldırı algılama ve soruşturma özelliklerini konsol üzerinden sorunsuz Microsoft 365 Defender sağlar. Windows Server desteği, sunucu etkinlikleri, çekirdek ve bellek saldırı algılaması için kapsam hakkında daha ayrıntılı bilgi sağlar ve yanıt eylemlerini sağlar.

Bu konu başlığında, uç nokta için Microsoft Defender'Windows belirli sunucularının nasıl ekli olduğu açıklanmıştır.

Temelleri temel sunucularında indirme ve Windows Güvenliği için Temelleri Windows için [Temeller'Windows Güvenliği bakın](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Windows Server eklemeye genel bakış

Sunucuları başarılı bir şekilde ekleme için aşağıdaki genel adımları tamamlamanız gerekir.

![Windows Sunucuları ve Windows 10 için işe Windows 10 çizimi](images/server-onboarding-tools-methods.png)

**Windows Server 2012 R2 ve Windows Server 2016 (Önizleme)**

>[!IMPORTANT]
> Bu işlevselliği kullanmak için önizleme özelliklerinin önizlemesini Microsoft 365 Defender uç noktalar bölümünde açabilirsiniz. Gelişmiş özellikler [Microsoft 365 Defender > Ayarlar > Uç >'ne gidin ve](https://security.microsoft.com/preferences2/integration) Önizleme özelliklerini açma.

- Yükleme ve ekleme paketlerini indirme
- Yükleme paketini uygulama
- İlgili araç için ekleme adımlarını izleyin

**Windows Server Semi-Annual Enterprise Channel ve Windows Server 2019**

- Ekleme paketini indirin
- İlgili araç için ekleme adımlarını izleyin

>[!IMPORTANT]
>Uç Nokta Sunucusu SKU için Microsoft Defender'ı satın almaya uygun olmak için, aşağıdakilerin, Windows E5/A5, Microsoft 365 E5/A5 veya Microsoft 365 E5 Güvenlik abonelik lisanslarının minimum birleştirilmiş bir toplamını satın almalısınız.  Lisanslama hakkında daha fazla bilgi için, Ürün [Koşulları'ne bakın](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  



### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview"></a>Modern Windows Server 2012 (Önizleme) R2 ve 2016 işlevleriyle yeni özellikler

R2 ve Windows Server 2012'nin önceki Windows Server 2016, Microsoft Monitoring Agent (MMA) kullanımını gerekli kıldı.

Yeni birleşik çözüm paketi, bağımlılıkları ve yükleme adımlarını kaldırarak sunucuları eklemeyi kolaylaştırır. Buna ek olarak, bu birleşik çözüm paketi aşağıdaki büyük geliştirmelerle birlikte gelir:

- [Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) R2 [için Yeni nesil korumasıyla](/microsoft-365/security/defender-endpoint/next-generation-protection) Windows Server 2012 oluşturma
- [Saldırı Surface Azaltma (ASR) kuralları](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Ağ Koruması](/microsoft-365/security/defender-endpoint/network-protection)
- [Denetimli Klasör Erişimi](/microsoft-365/security/defender-endpoint/controlled-folders)
- [İstenmeyen Uygulama (PUA) engellemesi olasılığı](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Gelişmiş algılama özellikleri](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Cihazlar ve dosyalar üzerinde](/microsoft-365/security/defender-endpoint/respond-machine-alerts) genişletilmiş yanıt [özellikleri](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR Modunda Yenile](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Canlı Yanıt](/microsoft-365/security/defender-endpoint/live-response)
- [Otomatik Araştırma ve Yanıt (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Tamper Protection](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

Birleşik çözüm, işe kullandığınız sunucuya bağlı olarak, Microsoft Defender Virüsten Koruma ve/veya EDR olarak yüklenir. Aşağıdaki tablo hangi bileşenin yük olduğunu ve varsayılan olarak nelerin yerleşik olduğunu gösterir.

|Sunucu sürümü|AV|EDR|
|----|----|----|
|Windows Server 2012 R2 SP1|![Evet.](images/svg/check-yes.svg)|![Evet.](images/svg/check-yes.svg)|
|Windows Server 2016|Yerleşik|![Evet.](images/svg/check-yes.svg)|
|Windows Server 2019 veya sonraki bir sonrakini yükleme|Yerleşik|Yerleşik|

Sunucularınızı daha önce MMA kullanarak ekleme yaptıysanız, yeni çözüme geçiş için [Sunucu](server-migration.md) geçişi'de sağlanan yönergeleri izleyin.

>[!NOTE]
>R2 Windows Server 2012 ve Windows Server 2016'de bu ekleme yöntemi önizlemedeyken, Microsoft Monitoring Agent (MMA) kullanarak önceki ekleme yöntemini kullanmaya devam Microsoft Monitoring Agent seçebilirsiniz. Daha fazla bilgi için bkz. [MMA kullanarak uç noktaları yükleme ve yapılandırma](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

#### <a name="known-issues-and-limitations-on-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>R2 ve 2016'da yeni, birleşik çözüm Windows Server 2012 bilinen sorunlar ve sınırlamalar

Aşağıdaki özel bilgiler, Windows Server 2012 R2 ve 2016 için yeni birleşik çözüm paketinde geçerlidir:

- Proxy sunucusundaki Uç nokta hizmeti [URL'leri için Microsoft Defender'a erişimi etkinleştir](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) seçeneğinde belirtilen bağlantı gereksinimlerini karşılar. Bunlar, Windows Server 2019'unkilerle eşdeğerdir. 
- Statik TelemetryProxyServer kullanılırken ve sertifika iptal listesi (CRL) URL'lerine SYSTEM hesabı bağlamından erişiken buluta yönelik Windows Server 2012 R2 bağlantısıyla ilgili bir sorunu araştırıyoruz. Bunun hemen risk azaltması, bu tür bağlantı sağlayan alternatif bir ara sunucu seçeneğini kullanmak veya SİSM hesap bağlamında WinInet ayarı üzerinden aynı proxy'yi yapılandırmaktır.
- Daha önce, Windows Server 2016'da (Microsoft Monitoring Agent MMA) kullanımına, Defender bulut hizmetleriyle bağlantı sağlamak için OMS / Log Analytics ağ geçidinin kullanımına izin veridi. Windows Server 2019, Windows Server 2022 ve Windows 10'de Uç Nokta için Microsoft Defender gibi yeni çözüm bu ağ geçidini desteklemez.

- Yükleme Windows Server 2016, Microsoft Defender Virüsten Koruma, etkin ve güncel olduğunu doğrulayın. Windows Update'i kullanarak en son platform sürümünü indirip yükleyebilirsiniz. Alternatif olarak, güncelleştirme paketini [Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) Kataloğu'dan veya [MMPC'den el ile indirebilirsiniz](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).  
- R2 Windows Server 2012 de, kullanıcı arabirimi veya Microsoft Defender Virüsten Koruma. Buna ek olarak, programda kullanıcı Windows Server 2016 yalnızca temel işlemlere izin verir. Bir cihazda yerel olarak işlem yapmak için PowerShell, WMI ve Diğer Adlar ile [Uç Nokta için Microsoft Defender'ı yönetme MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). Sonuç olarak, kullanıcıdan bir karar aldığı veya belirli bir görevi gerçekleştirmesi istendiğinde olduğu gibi, özellikle kullanıcı etkileşimini temel alan özellikler beklendiği gibi çalışmayabilirsiniz. Koruma özelliğini etkiley sürece, kullanıcı arabirimini devre dışı bırakmanız veya etkinleştirmeniz ya da yönetilen sunucu üzerinde kullanıcı etkileşimi gerektirmeniz önerilir.
- Saldırı Yüzeyini Azaltma kurallarının hepsi tüm işletim sistemlerinde kullanılamaz. Saldırı [Yüzeyini Azaltma (ASR) kuralları'ne bakın](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules).
- Ağ [Koruması'nın etkinleştirmek](/microsoft-365/security/defender-endpoint/network-protection) için ek yapılandırma gereklidir:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  Buna ek olarak, yüksek hacimli ağ trafiğine sahip makinelerde, bu özelliği geniş bir kitleyle etkinleştirmeden önce ortamınız için performans testinin kullanılması kesinlikle önerilir. Ek kaynak tüketimini hesaba atamanız gerekiyor olabilir.
- R2 Windows Server 2012 de, Ağ Olayları zaman çizelgesinde yer alamayabilirsiniz. Bu sorun, Windows [12 Ekim 2021 aylık toplaması (KB5006714](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e)) kapsamında yayımlanan bir Güncelleştirme Güncelleştirmesini gerektirir.
- İşletim sistemi yükseltmeleri desteklenmiyor. Ardından, yükseltmeden önce çıkarabilirsiniz.
- R2'de *sunucu* rollerinin otomatik dışlamaları Windows Server 2012, bununla birlikte, işletim sistemi dosyaları için yerleşik dışlamalar vardır. Dışlama ekleme hakkında daha fazla bilgi için bkz. Şu anda desteklenen Enterprise bilgisayarlarla ilgili virüs tarama [Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- Şu anda, modern, birleşik çözümü kaldırmayı ve önceki MMA tabanlı algılayıcıyı yeniden yüklemeyi seçerseniz EDR kilitlenmelerle karşılaşabilirsiniz`MsSenseS.exe`. 

Geçici bir çözüm olarak, varsa aşağıdaki kayıt defteri anahtarlarını kaldırın:
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\fdedb2b8-61e4-4a7e-8b15-abf214a08fcc`
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\c60418cc-7e07-400f-ae3b-d521c5dbd96f`

Aşağıdaki komutları kullanabilirsiniz:

```cmd
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v fdedb2b8-61e4-4a7e-8b15-abf214a08fcc /f
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v c60418cc-7e07-400f-ae3b-d521c5dbd96f /f
```
Yeniden başlatma gerekmez.


<a name="integration-with-azure-defender"></a>

## <a name="integration-with-microsoft-defender-for-cloud"></a>Bulut için Microsoft Defender ile tümleştirme

Uç Nokta için Microsoft Defender, Bulut için Microsoft Defender ile sorunsuz bir şekilde tümleştirilmiştir. Sunuculara otomatik olarak ekleme, sunucuların Azure Defender tarafından izlenmesini sağlamak için Uç Nokta için Defender'da görünür ve Bulut için Microsoft Defender müşterisi olarak ayrıntılı soruşturmalar yürütebilirsiniz.

Daha fazla bilgi için bkz [. Bulut için Microsoft Defender ile Tümleştirme](azure-server-integration.md).

> [!NOTE]
> Modern birleşik Windows Server 2012 önizlemesini çalıştıran R2 ve 2016'da, uyarı ve otomatik dağıtım için sunucular için Bulut için Microsoft Defender / Microsoft Defender ile tümleştirme henüz kullanılamaz. Bu makinelere yeni çözümü el ile yüklemenize devam edebilirsiniz ancak Bulut için Microsoft Defender'da herhangi bir uyarı görüntülenmez.

> [!NOTE]
> - Sunucular için Microsoft Defender ile Uç Nokta için Microsoft Defender arasındaki tümleştirme, Windows Server 2022, [Windows Server 2019 ve Windows Virtual Desktop'u (WVD) destekleyecek şekilde genişletildi](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).
> - Bu tümleştirmeyi kullanan sunucu uç noktası izlemesi, bu Office 365 GCC devre dışı bırakılmıştır.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 ve Windows Server 2016

> [!NOTE]
> R2 Windows Server 2012 ve Windows Server 2016'de bu ekleme yöntemi önizlemedeyken, Microsoft Monitoring Agent (MMA) kullanarak önceki ekleme yöntemini kullanmaya devam Microsoft Monitoring Agent seçebilirsiniz. Daha fazla bilgi için bkz. [MMA kullanarak uç noktaları yükleme ve yapılandırma](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

### <a name="prerequisites"></a>Önkoşullar

**R2'nin Windows Server 2012 önkoşulları**

Makinelerinizi en son aylık toplama paketiyle tamamen [güncelleştirmeniz](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) varsa, ek **önkoşul** yoktur.

Yükleyici paketi, aşağıdaki bileşenlerin bir güncelleştirme aracılığıyla zaten yüklü olup olduğunu kontrol edin:

- [Müşteri deneyimi ve tanılama telemetrisi güncelleştirmesi](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Çalışma Zamanında Evrensel C Çalışma Zamanı Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

**Windows Server 2016 için önkoşullar** 

En Son Toplu Güncelleştirme (LCU) ile makinenizi tümüyle güncelleştirme dışında, Microsoft Defender Virüsten Koruma, etkin ve güncel olduğunu doğrulayın. Windows Update'i kullanarak en son platform sürümünü indirip yükleyebilirsiniz. Alternatif olarak, güncelleştirme paketini [Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) Kataloğu'dan veya [MMPC'den el ile indirebilirsiniz](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64). 

> [!NOTE]
> 4.10 ile başlayan bir sürüm numarası Windows Defender'ın yerleşik sürümünü kullanılabilir en son platforma başarıyla güncelleştirmek için, bir hizmet yığını güncelleştirmesi ve 20 Eylül 2018'e eşit veya daha sonra (KB4457127 (OS Derlemesi 14393.2515) son Toplu Güncelleştirme (LCU) uygulanmış olmalıdır.

**Üçüncü taraf güvenlik çözümleriyle çalışmanın önkoşulları**

Üçüncü taraf kötü amaçlı yazılımlardan koruma çözümü kullanmayı amaçlı kullanıyorsanız, pasif Microsoft Defender Virüsten Koruma çalıştırmaniz gerekir. Yükleme ve ekleme işlemi sırasında pasif moduna ayarlamayı unutmayın.

**Windows Server 2012 R2 ve 2016'da Uç Nokta için Microsoft Defender'a yeni güncelleştirme paketi**

EDR Windows Algılayıcı bileşenine yönelik düzenli ürün geliştirmeleri ve düzeltmeler almak için [KB5005292 Güncelleştirmesini kb5005292'in](https://go.microsoft.com/fwlink/?linkid=2168277) uygulandığını veya onaylandıktan emin olun. Ayrıca, koruma bileşenlerini güncel tutmak için bkz. [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

### <a name="onboarding-steps-summary"></a>Ekleme adımları özeti

- 1. ADIM: [Yükleme ve ekleme paketlerini indirme](#step-1-download-installation-and-onboarding-packages)
- 2. ADIM: [Yükleme ve ekleme paketini uygulama](#step-2-apply-the-installation-and-onboarding-package)
- 3. [ADIM:Ekleme adımlarını tamamlama](#step-3-complete-the-onboarding-steps) 


### <a name="step-1-download-installation-and-onboarding-packages"></a>1. ADIM:Yükleme ve ekleme paketlerini indirme

Portaldan hem yükleme hem **de** **ekleme paketlerini** indirmeniz gerekir.

> [!div class="mx-imgBorder"]
> ![Ekleme panosu görüntüsü](images/install-agent-onboard.png)


   > [!NOTE]
   > Windows Server 2012R2'de, Microsoft Defender Virüsten Koruma paketi tarafından yüklenir ve pasif moduna ayarlamadıysanız etkin olur. Yükleme Windows Server 2016, Microsoft Defender Virüsten Koruma önce bir özellik olarak yüklenmiş ([bkz. MDE'ye](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016) geçiş) ve tümüyle güncelleştirilmelidir.
   > 
   > Microsoft kötü amaçlı yazılımlardan koruma çözümü çalıştırıyorsanız, yüklemeden önce Microsoft dışı çözümün Microsoft Defender Virüsten Koruma için (Defender İşlemleri sekmesindeki [bu Microsoft Defender](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) İşlemleri listesinden) dışlamalar ekleyebilirsiniz.  Ayrıca, Microsoft olmayan güvenlik çözümlerini Defender Virüsten Koruma dışlama listesine eklemeniz de önerilir.


Yükleme **paketi,** Uç nokta aracısı için Microsoft Defender'ı yük eden bir MSI dosyası içerir.

Ekleme **paketi aşağıdaki** dosyaları içerir:

- `OptionalParamsPolicy` - örnek koleksiyona olanak sağlayan ayarı içerir
- `WindowsDefenderATPOnboardingScript.cmd` - ekleme betiği içerir

Aşağıdaki adımları kullanarak paketleri indirin: 

1. Daha Microsoft 365 Defender, Cihaz Yönetimi **Ayarlar > Ekleme'> gidin**.

2. **R2 Windows Server 2012 2016'ya seçin**.

3. Yükleme **paketini indir'i** seçin ve .msi kaydedin. 
 
4. Ekleme **paketini indir'i** seçin ve .zip kaydedin.

5. Yükleme paketini, yükleme seçenekleriden herhangi birini kullanarak Microsoft Defender Virüsten Koruma. Yükleme için yönetim izinleri gerekir.



### <a name="step-2-apply-the-installation-and-onboarding-package"></a>2. ADIM:Yükleme ve ekleme paketini uygulama
Bu adımda, makinenizi eklemeye hazırlamak için cihazınızı Uç Nokta bulut ortamı için Microsoft Defender'a eklemeden önce gerekli önleme ve algılama bileşenlerini yüklemiş oluruz. Tüm [önkoşulların karşı](#prerequisites) olduğundan emin olmak. 

   > [!NOTE]
   > Microsoft Defender Virüsten Koruma yüklenir ve pasif moduna ayarlamadıysanız etkin olur. 

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Uç nokta paketleri için Microsoft Defender'ı yükleme seçenekleri

Önceki bölümde bir yükleme paketi indirdiniz. Yükleme paketi, Uç nokta bileşenleri için tüm Microsoft Defender yükleyicisini içerir. 

Aracıyı yüklemek için aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz:
- [Komut satırı kullanarak yükleme](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Betik kullanarak yükleme](#install-microsoft-defender-for-endpoint-using-a-script)
- [Grup İlkesi kullanarak yükleme ve ekleme paketlerini uygulama](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Komut çizgisini kullanarak Uç Nokta için Microsoft Defender'ı yükleme
Önceki adımda yer alan yükleme paketini kullanarak Uç Nokta için Microsoft Defender'ı yükleyin. 


Uç Nokta için Microsoft Defender'ı yüklemek için aşağıdaki komutu çalıştırın:

```console
Msiexec /i md4ws.msi /quiet
```

Kaldırmak için, önce uygun kaldırma betiği kullanılarak makinenin çıkarlı olduğundan emin olur. Ardından, kaldırma işlemini gerçekleştirmek için \> Denetim \> Masası Programları ve Özellikleri'ni kullanın.

Alternatif olarak, Uç Nokta için Microsoft Defender'ı kaldırmak için aşağıdaki kaldırma komutunu çalıştırın:

```console
Msiexec /x md4ws.msi /quiet
```

Yukarıdaki komutun başarılı olması için, yüklemede kullanılan paketle aynı paketi kullanabilirsiniz.

Anahtar `/quiet` tüm bildirimlerin gizlenmelerini sağlar.

> [!NOTE]
> Microsoft Defender Virüsten Koruma pasif moduna otomatik olarak gitmez. Microsoft dışı bir virüsten Microsoft Defender Virüsten Koruma veya kötü amaçlı yazılımdan koruma çözümü çalıştırdıysanız, pasif modunda çalıştıracak şekilde ayarlamayı seçebilirsiniz. Komut satırı yüklemelerinde, isteğe bağlı isteğe `FORCEPASSIVEMODE=1` bağlı Microsoft Defender Virüsten Koruma müdahaleyi önlemek için bileşen pasif moduna geçer. Ardından, Block gibi özellikleri desteklemek amacıyla ekleme sonrasında Defender Virüsten Koruma'nın pasif modunda EDR kalmasını sağlamak için "ForceDefenderPassiveMode" kayıt defteri anahtarını ayarlayın.

Windows Server desteği, sunucu etkinlikleri, çekirdek ve bellek saldırı algılaması için kapsam hakkında daha ayrıntılı bilgi sağlar ve yanıt eylemlerini sağlar.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Komut dosyası kullanarak Uç Nokta için Microsoft Defender'ı yükleme

Yüklemeyi, kaldırmayı [ve](server-migration.md#installer-script) ekleme işlemini otomatik hale etmeye yardımcı olmak için yükleyici betiği kullanabilirsiniz. Daha fazla bilgi için, aşağıdaki bölümde verilen yönergelere bakarak betiği Grup İlkesi ile kullanma bölümüne bakın.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Grup ilkesi kullanarak Uç nokta yükleme ve ekleme paketleri için Microsoft Defender'ı uygulama

1. Grup ilkesi oluşturma: <br> Grup İlkesi [Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz **Grup** İlkesi Nesneleri'ne sağ tıklayın ve Yeni'ye **tıklayın**. Görüntülenen iletişim kutusuna yeni GPO'nun adını girin ve Tamam'a **tıklayın**.

2. Grup İlkesi [Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'nı, Tercihler'i** ve denetim masası **ayarları'nı seçin**.

4. Zamanlanmış **görevler'e sağ tıklayın**, **Yeni'nin** üzerine gelin ve Anlık Görev **(En az 7 Windows) tıklayın**.

5. Açılan **Görev** penceresinde Genel **sekmesine** gidin. Güvenlik **seçenekleri'nin** altında **Kullanıcı veya Grubu Değiştir'e** tıklayın, SİSS SISTEMI yazın ve Adları **Denetleme'ye ve Tamam'a** **tıklayın**. NT AUTHORITY\SYSTEM, görevin çalıştıracak olduğu kullanıcı hesabı olarak görünür.

6. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

7. Ad alanına, zamanlanmış görev için uygun bir ad yazın (örneğin, Uç Nokta Dağıtımı için Defender).

8. Eylemler sekmesine **gidin** ve Yeni **... öğesini seçin.** Eylem alanında **Program başlat'ın** seçili olduğundan **emin** olun. Yükleme [işlemini yükleyici](server-migration.md#installer-script) betiği gerçekleştirebilir ve yükleme tamamlandıktan hemen sonra ekleme adımını gerçekleştirebilirsiniz. Önce *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* sonra da bağımsız değişkenleri sağla:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```  

     >[!NOTE]
    >Önerilen yürütme ilkesi ayarıdır `Allsigned`. Bunun için betiğin imzalama sertifikası, betiğin uç noktada SYSTEM olarak çalışıyorsa Yerel Bilgisayar Güvenilen Yayımcılar deposuna içeri aktarılması gerekir.

    Dosya \\sunucusunun paylaşılan paylaşılan dosyanın tam etki alanı adını (FQDN) kullanarak servername-or-the-space\share-name'yi UNC *yoluylainstall.ps1* değiştirin. Yükleyici paketi md4ws.msi aynı dizine yerleştiril olmalıdır.  Ayrıca UNC yolu izinlerinin, platformu yükleyerek bilgisayar hesabına okuma erişimine izin olduğundan da emin olun.

   

    Microsoft olmayan kötü amaçlı yazılım Microsoft Defender Virüsten Koruma birlikte kullanılabilmelerini istediğiniz senaryolarda, yükleme sırasında pasif modunu ayarlamak için $Passive parametresini ekleyin.

9. **Tamam'ı** seçin ve tüm açık GPMC pencerelerini kapatın.

10. GPO'nun Kuruluş Birimine (OU) bağlantısını eklemek için sağ tıklayın ve Varolan **bir GPO'ya bağlantı ekle'yi seçin**. Görüntülenen iletişim kutusunda, bağlantısını eklemek istediğiniz Grup İlkesi Nesnesi'ne tıklayın. **Tamam**'a tıklayın.

Ek yapılandırma ayarları için bkz [. Örnek koleksiyon ayarlarını yapılandırma ve](configure-endpoints-gp.md#configure-sample-collection-settings) [Diğer önerilen yapılandırma ayarları](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>3. ADIM:Ekleme adımlarını tamamlama

Aşağıdaki adımlar yalnızca üçüncü taraf bir kötü amaçlı yazılımdan koruma çözümü kullanıyorsanız uygulanabilir. Pasif modu ayarı için aşağıdaki Microsoft Defender Virüsten Koruma gerekir. Doğru yapılandırıldığından emin olun:

1. Aşağıdaki kayıt defteri girdisini ayarlayın:
    - Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Ad: `ForceDefenderPassiveMode`
    - Tür: `REG_DWORD`
    - Değer: `1`

2. Pasif modunun yapılandırıldığından emin olmak için aşağıdaki PowerShell komutunu çalıştırın:

    ```powershell
    Get-WinEvent -FilterHashtable @{ProviderName="Microsoft-Windows-Sense" ;ID=84}
    ```

3. Pasif modu olayı içeren son bir olayın olduğunu onaylayın:

    ![Pasif modu doğrulama sonucu görüntüsü](images/atp-verify-passive-mode.png)

> [!IMPORTANT]
>
> - Sunucuları izlemek için Bulut için Microsoft Defender'ı kullanırsınız, otomatik olarak uç nokta kiracısı için bir Defender oluşturulur (ABD kullanıcıları için ABD'de, Avrupa kullanıcıları için AB'de ve birleşik Krallık kullanıcıları için İngiltere'de).
Uç Nokta için Defender tarafından toplanan veriler, sağlama sırasında tanımlandığı gibi kiracının coğrafi konumda depolanır.
> - Bulut için Microsoft Defender'ı kullanmadan önce Uç Nokta için Defender'ı kullanırsanız, daha sonra Bulut için Microsoft Defender ile tümleştirin, kiracınızı oluşturulduğunda verileriniz belirttiğiniz konumda depolanır.
> - Yapılandırıldığında, verilerinizin depolandığı konumu değiştiremezsiniz. Verilerinizi başka bir konuma taşımanız gerekirse, kiracıyı sıfırlamak için Microsoft Desteği'ne başvurun.
> - Windows Server 2019 ve Windows Server 2022 ile Microsoft Endpoint Manager için ekleme paketi şu anda bir betik gönderir. Configuration Manager'da betikleri dağıtma hakkında daha fazla bilgi için bkz. [Configuration Manager'da paketler ve programlar](/configmgr/apps/deploy-use/packages-and-programs).
> - Yerel betik, kavram kanıtı için uygundur, ancak üretim dağıtımı için kullanılmamalısınız. Üretim dağıtımı için Grup İlkesi veya Dağıtım Microsoft Endpoint Configuration Manager.



## <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Kanal ve Windows Server 2019 ve Windows Server 2022

Windows Server 2019 ve Windows Server 2022 ile Microsoft Endpoint Manager ekleme paketi şu anda bir betik gönderir. Configuration Manager'da betikleri dağıtma hakkında daha fazla bilgi için bkz. [Configuration Manager'da paketler ve programlar](/configmgr/apps/deploy-use/packages-and-programs).

### <a name="download-package"></a>Paketi indir

1. Daha Microsoft 365 Defender, Cihaz Yönetimi **Ayarlar > Ekleme'> gidin**.

2. Windows **Server 1803 ve 2019'ı seçin**.

3. Paketi **indir'i seçin**. Belgeyi farklı WindowsDefenderATPOnboardingPackage.zip.

4. Ekleme adımlarını tamamlama [bölümünde verilen adımları](#step-3-complete-the-onboarding-steps) izleyin.


## <a name="verify-the-onboarding-and-installation"></a>Ekleme ve yükleme doğrulama

Uç nokta Microsoft Defender Virüsten Koruma Microsoft Defender'ın çalıştığını doğrulayın.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Eklemeyi doğrulamak için bir algılama testi çalıştırma

Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta cihazı için Microsoft Defender'da algılama testi çalıştırma](run-detection-test.md).

> [!NOTE]
> Çalışma Microsoft Defender Virüsten Koruma gerekli değildir, ancak bu gereklidir. Birincil uç nokta koruma çözümü başka bir virüsten koruma satıcısı ürünü ise, Defender Virüsten Koruma'ı Pasif modunda çalıştırabilirsiniz. Pasif modunun, Uç nokta algılayıcısı (SENSE) için Microsoft Defender'ın çalıştığını doğruladikten sonra yalnızca pasif modunun açık olduğunu onaylayın.

1. Postanın yüklü olduğunu doğrulamak Microsoft Defender Virüsten Koruma komutu çalıştırın:

    >[!NOTE]
    >Bu doğrulama adımı yalnızca etkin kötü amaçlı yazılımdan koruma çözümünüz Microsoft Defender Virüsten Koruma bu adımı kullanıyorsanız gereklidir.

    `sc.exe query Windefend`


    Sonuç 'Belirtilen hizmet, yüklü bir hizmet olarak yok' ise, bu hizmet için başka bir Microsoft Defender Virüsten Koruma. 


    Windows sunucularında gruplarınızı yapılandırmak ve yönetmek için Grup İlkesi Microsoft Defender Virüsten Koruma hakkında bilgi için bkz. Grup İlkesi ayarlarını kullanarak grup ayarlarını yapılandırma [Microsoft Defender Virüsten Koruma](use-group-policy-microsoft-defender-antivirus.md).

2. Uç nokta için Microsoft Defender'ın çalıştığını doğrulamak için aşağıdaki komutu çalıştırın:

    `sc.exe query sense`

    Sonuç çalışıyor olduğunu göster olmalı. Eklemeyle ilgili sorunlarla karşılaşırsanız bkz. [Ekleme sorunlarını giderme](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma

Sunucunun Uç nokta hizmeti [için Defender'a](run-detection-test.md) rapor çalıştığını doğrulamak için yeni eklenen bir cihazda algılama testi çalıştırma'daki adımları izleyin.

## <a name="next-steps"></a>Sonraki adımlar

Cihazları hizmete başarıyla işe başladıktan sonra, Uç Nokta için Microsoft Defender'ın tek tek bileşenlerini yapılandırmanız gerekir. Çeşitli [bileşenlerin etkinleştirilmesi](prepare-deployment.md#adoption-order) konusunda yol olması için Benimseme sırasına bakın.

## <a name="offboard-windows-servers"></a>Offboard Windows sunucuları

Windows Server 2012 istemci cihazlarında kullanılabilen yöntemle Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 ve Windows Server 2019 Core edition Windows 10 çıkarabilirsiniz.

- [Grup İlkesi kullanan offboard cihazları](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Configuration Manager kullanan offboard cihazları](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Mobil Cihaz Yönetimi araçlarını kullanarak offboard ve monitör cihazları](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Yerel betik kullanan offboard cihazları](configure-endpoints-script.md#offboard-devices-using-a-local-script)

Diğer Windows sunucu sürümleri için, hizmetten iki Windows çıkarabilirsiniz:

- MMA aracısı kaldırma
- Uç nokta çalışma alanı yapılandırması için Defender'ı kaldırma

>[!NOTE]
>*Diğer Windows sunucu sürümleri için bu çıkarma yönergeleri, MMA gerektiren Windows Server 2016 ve Windows Server 2012 R2 uç noktası için önceki Microsoft Defender'ı çalıştırmayı da içerir. Yeni ve açık olmayan çözüme geçirme yönergeleri, Uç Nokta için [Microsoft Defender'daki Sunucu geçiş senaryolarındadır](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>İlgili konular

- [Windows'un önceki sürümlerini ekleme](onboard-downlevel.md)
- [Cihaz Windows 10 ekleme](configure-endpoints.md)
- [Windows olmayan cihazları ekleme](configure-endpoints-non-windows.md)
- [Ara sunucu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [Yeni eklenen Uç nokta cihazı için Defender'da bir algılama testi çalıştırma](run-detection-test.md)
- [Uç nokta ekleme sorunları için Microsoft Defender sorunlarını giderme](troubleshoot-onboarding.md)
