---
title: PowerShell, WMI ve Başka Bir Ad kullanarak Uç Nokta için Microsoft Defender'ı MPCmdRun.exe
description: PowerShell, WMI ve Diğer Adlarla Uç Nokta için Microsoft Defender'ı yönetmeyi MPCmdRun.exe
keywords: geçiş sonrası, yönetme, işlemler, bakım, kullanım, PowerShell, WMI, MPCmdRun.exe, Uç Nokta için Microsoft Defender, edr
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
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: b5794b978e35faa23df51528a077fe90444fdce1
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997069"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>PowerShell, WMI ve Diğer Adlarla Uç Nokta için Microsoft Defender'ı MPCmdRun.exe

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> [Microsoft Endpoint Manager'i](/mem) kullanarak, kuruluşta cihazlar için tehdit koruması özelliklerini (uç nokta olarak da adlandırılır) yönetmenizi öneririz. Endpoint Manager[, Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [ve Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [Daha fazla bilgi Endpoint Manager](/mem/endpoint-manager-overview)
> - [Configuration Manager ve Intune ile Windows 10 ve Windows cihazlarda Uç Nokta için Microsoft Defender'ı birlikte yönetme](manage-mde-post-migration-intune.md)
> - [Intune ile Uç Nokta için Microsoft Defender'ı yönetme](manage-mde-post-migration-intune.md)

[PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell), Microsoft Defender Virüsten Koruma Yönetim Aracı (WMI) ve [Microsoft](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) Kötü Amaçlı Yazılımdan [Koruma](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) Komut Satırı Yardımcı Programı'Windows bazı yazılım ayarlarını cihazlarda MPCmdRun.exe. Örneğin, bazı ayar ayarlarını Microsoft Defender Virüsten Koruma. Ayrıca bazı durumlarda saldırı yüzeyini azaltma kurallarınızı ve exploit protection ayarlarınızı özelleştirebilirsiniz.

> [!IMPORTANT]
> PowerShell, WMI veya MCPmdRun.exe kullanarak yapılandırılan tehdit koruması özelliklerinin üzerine, Intune veya Configuration Manager ile dağıtılan yapılandırma ayarları neden olabilir.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>PowerShell ile Uç Nokta için Microsoft Defender'ı Yapılandırma

PowerShell'i kullanarak saldırı ve Microsoft Defender Virüsten Koruma azaltma kurallarını yönetabilirsiniz.<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**Microsoft Defender Virüsten Koruma** <br/><br/> Kötü amaçlı yazılımlardan koruma durumunu görüntüleme, virüsten koruma güncelleştirmelerini & taramaları için tercihleri yapılandırma ve virüsten koruma korumada başka değişiklikler yapma.*|[PowerShell cmdlet'lerini kullanarak e-postalarınızı Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Buluta teslim edilen korumayı etkinleştirmek için PowerShell cmdlet'lerini kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Kuruluş cihazlarınıza** yönelik tehditleri azaltmak için exploit protection'i yapılandırma <br/><br/> *Önce denetim modunda exploit [protection'ı](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) kullanmalarını öneririz. Bu şekilde, exploit protection'ın kurumda kullanmakta olduğu uygulamaları nasıl etkileyeceğini görebilirsiniz.*|[Exploit Protection'i özelleştirme](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Exploit Protection için PowerShell cmdlet'leri](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**PowerShell ile saldırı yüzeyini azaltma** kurallarını yapılandırma <br/><br/> *Dosya ve klasörleri saldırı yüzeyini azaltma kurallarının dışında tutmak için PowerShell kullanabilirsiniz.*|[Saldırı yüzeyini azaltma kurallarını özelleştirme: PowerShell kullanarak bu dosyaları ve & dışında tutabilirsiniz](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders) <br/><br/> Ayrıca, [PowerShell ile saldırı yüzeyini azaltma kurallarını ayarlayan António Vasconcelo'nun grafik kullanıcı arabirimi aracına bakın](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI).|
|**PowerShell ile Ağ** Korumasını Etkinleştirme <br/><br/> *Ağ Korumasını etkinleştirmek için PowerShell'i kullanabilirsiniz.*|[PowerShell ile Ağ Korumasını açma](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Fidye yazılımlarına karşı korunmak için** denetimli klasör erişimini yapılandırma <br/><br/> *[Denetimli klasör](/microsoft-365/security/defender-endpoint/controlled-folders) erişimi, yazılım önleme yazılımı koruması olarak da adlandırılır.*|[PowerShell ile denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Microsoft Defender Güvenlik Duvarı'nı** , kuruluş cihazlarına yetkisiz ağ trafiğinin akışını engellemek üzere yapılandırma|[Windows PowerShell kullanarak Gelişmiş Güvenlik Yönetimi ile Microsoft Defender Güvenlik Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Şifrelemeyi ve BitLocker'ı** yapılandırarak kuruluş kuruluşlarının çalışan cihazlarında yer alan bilgileri Windows|[BitLocker PowerShell başvuru kılavuzu](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Microsoft Defender for Endpoint for Endpoint with Windows Management Instrumentation (WMI) ile yapılandırma

WMI, ayarları alamanız, değiştirmenize ve güncelleştirmenize olanak sağlayan bir komut dosyası arabirimidir. Daha fazla bilgi edinmek için [bkz. WMI'ı kullanma](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**Cihazda bulut teslimi korumasını** etkinleştirme|[Bulut Windows korumasını etkinleştirmek için KULLANıCı Yönetimi Yönergesi'ne (WMI) kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Ayarları alın, değiştirin ve** Microsoft Defender Virüsten Koruma|[HESABı yapılandırmak ve yönetmek için WMI'Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Kullanılabilir WMI sınıfları ve örnek betiklerin listesini gözden geçirme](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Arşivlenen web sitesi [Windows Defender WMIv2 Sağlayıcı başvuru bilgilerine de bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Microsoft Kötü Amaçlı Yazılımdan Koruma Yardımcı Programı ile Uç Nokta için Microsoft Defender'Command-Line Yapılandırma (MPCmdRun.exe)

Tek bir cihazda tarama çalıştırabilirsiniz, tanılama izlemeyi başlatabilirsiniz, güvenlik zekası güncelleştirmelerini ve daha fazlasını mpcmdrun.exe komut satırı aracını kullanarak kontrol edebilirsiniz. Yardımcı programı 'da bulabilirsiniz `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Komut isteminden çalıştırın.

Daha fazla bilgi edinmek için bkz[. Microsoft Defender Virüsten Koruma ile mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Daha önce bunu yapmadıysanız, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalınızı</a> uyarıları görüntülemek, tehdit koruma özelliklerini yapılandırmak ve kuruluşun genel güvenlik uyarısı hakkında ayrıntılı bilgileri görüntülemek için yapılandırabilirsiniz.

Son kullanıcıların aynı bağlantıda hem de son kullanıcıların hangi özellikleri göreceğini Microsoft Defender Güvenlik Merkezi.

- [Genel bakış Microsoft Defender Güvenlik Merkezi](/microsoft-365/security/defender-endpoint/use)

- [Uç nokta koruması: Microsoft Defender Güvenlik Merkezi](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl olduğunu genel Tehdit ve Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Microsoft Defender Güvenlik Merkezi güvenlik işlemleri panosuna ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Intune ile Uç Nokta için Microsoft Defender'ı yönetme](manage-mde-post-migration-intune.md)
