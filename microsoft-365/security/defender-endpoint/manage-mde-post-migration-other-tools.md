---
title: PowerShell, WMI ve MPCmdRun.exe kullanarak Uç Nokta için Microsoft Defender yönetme
description: PowerShell, WMI ve MPCmdRun.exe ile Uç Nokta için Microsoft Defender yönetmeyi öğrenin
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 71b18f5e78301ac144faef9046420e817c65fa6b
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607377"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>PowerShell, WMI ve MPCmdRun.exe ile Uç Nokta için Microsoft Defender yönetme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Kuruluşunuzun cihazlar için tehdit koruması özelliklerini yönetmek için [Microsoft Endpoint Manager](/mem) kullanmanızı öneririz (uç noktalar olarak da adlandırılır). Endpoint Manager [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) içerir.
> - [Endpoint Manager hakkında daha fazla bilgi edinin](/mem/endpoint-manager-overview)
> - [Configuration Manager ve Intune ile Windows 10 ve Windows 11 cihazlarda Uç Nokta için Microsoft Defender birlikte yönetme](manage-mde-post-migration-intune.md)
> - [Intune ile Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration-intune.md)

[PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell), [Windows Yönetim Araçları](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) ve [Microsoft Kötü Amaçlı Yazılımdan Koruma Komut Satırı Yardımcı Programı](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe) bulunan cihazlarda bazı Microsoft Defender Virüsten Koruma ayarlarını yönetebilirsiniz. Örneğin, bazı Microsoft Defender Virüsten Koruma ayarlarını yönetebilirsiniz. Bazı durumlarda saldırı yüzeyi azaltma kurallarınızı ve yararlanma koruma ayarlarınızı özelleştirebilirsiniz.

> [!IMPORTANT]
> PowerShell, WMI veya MCPmdRun.exe kullanarak yapılandırdığınız tehdit koruma özelliklerinin üzerine Intune veya Configuration Manager ile dağıtılan yapılandırma ayarları yazılabilir.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>PowerShell ile Uç Nokta için Microsoft Defender yapılandırma

PowerShell'i kullanarak Microsoft Defender Virüsten Koruma' yı, yararlanma korumasını ve saldırı yüzeyi azaltma kurallarınızı yönetebilirsiniz.

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**Microsoft Defender Virüsten Koruma'ya yönetme** <br/><br/> Kötü amaçlı yazılımdan koruma durumunu görüntüleyin, virüsten koruma taramaları & güncelleştirmeler için tercihleri yapılandırın ve virüsten korumanızda başka değişiklikler yapın.*|[Microsoft Defender Virüsten Koruma'nın yapılandırılması ve yönetilmesi için PowerShell cmdlet'lerini kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Bulut tabanlı korumayı etkinleştirmek için PowerShell cmdlet'lerini kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|Kuruluşunuzun cihazlarında tehditleri azaltmak için **açıklardan yararlanma korumasını yapılandırma** <br/><br/> *İlk olarak [denetim modunda](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) açık koruması kullanmanızı öneririz. Bu şekilde, yararlanma korumasının kuruluşunuzun kullandığı uygulamaları nasıl etkilediğini görebilirsiniz.*|[Exploit Protection'i özelleştirin](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Yararlanma koruması için PowerShell cmdlet'leri](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|PowerShell ile **saldırı yüzeyi azaltma kurallarını yapılandırma** <br/><br/> *Dosyaları ve klasörleri saldırı yüzeyi azaltma kurallarının dışında tutmak için PowerShell'i kullanabilirsiniz.*|[Saldırı yüzeyi azaltma kurallarını özelleştirme: Dosyaları & klasörleri hariç tutmak için PowerShell kullanma](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction) <br/><br/> Ayrıca [PowerShell ile saldırı yüzeyi azaltma kurallarını ayarlamak için antónio Vasconcelo'nun grafik kullanıcı arabirimi aracına](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI) bakın.|
|PowerShell ile **Ağ Korumasını Etkinleştirme** <br/><br/> *Ağ Koruması'nı etkinleştirmek için PowerShell'i kullanabilirsiniz.*|[PowerShell ile Ağ Koruması'nı açma](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|Fidye yazılımlarına karşı korunmak için **denetimli klasör erişimini yapılandırma** <br/><br/> *[Denetimli klasör erişimi](/microsoft-365/security/defender-endpoint/controlled-folders) , antiransomware koruması olarak da adlandırılır.*|[PowerShell ile denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|Kuruluşunuzun cihazlarına veya cihazlarına gelen veya giden yetkisiz ağ trafiğini engellemek için **Microsoft Defender Güvenlik Duvarı yapılandırma**|[Windows PowerShell kullanarak Gelişmiş Güvenlik Yönetimi ile Microsoft Defender Güvenlik Duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|Kuruluşunuzun Windows çalıştıran cihazlarındaki bilgileri korumak için **şifrelemeyi ve BitLocker'ı yapılandırma**|[BitLocker PowerShell başvuru kılavuzu](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Windows Yönetim Araçları (WMI) ile Uç Nokta için Microsoft Defender yapılandırma

WMI, ayarları almanıza, değiştirmenize ve güncelleştirmenize olanak tanıyan bir betik arabirimidir. Daha fazla bilgi için bkz. [WMI kullanma](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|Bir cihazda **bulut tabanlı korumayı etkinleştirme**|[Bulut tabanlı korumayı etkinleştirmek için Windows Yönetim Yönergesi'ni (WMI) kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|Microsoft Defender Virüsten Koruma **için ayarları alma, değiştirme ve güncelleştirme**|[Microsoft Defender Virüsten Koruma'nın yapılandırılması ve yönetilmesi için WMI kullanma] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Kullanılabilir WMI sınıflarının ve örnek betiklerin listesini gözden geçirin](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Ayrıca [WMIv2 Sağlayıcısı başvuru bilgilerine Windows Defender arşivlenenlere](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN) bakın|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Microsoft Kötü Amaçlı Yazılımdan Koruma Command-Line Yardımcı Programı (MPCmdRun.exe) ile Uç Nokta için Microsoft Defender yapılandırma

Tek bir cihazda tarama çalıştırabilir, tanılama izlemeyi başlatabilir, güvenlik bilgileri güncelleştirmelerini denetleyebilir ve mpcmdrun.exe komut satırı aracını kullanarak daha fazlasını yapabilirsiniz. yardımcı programını içinde `%ProgramFiles%\Windows Defender\MpCmdRun.exe`bulabilirsiniz. Komut isteminden çalıştırın.

Daha fazla bilgi için bkz. [mpcmdrun.exeile Microsoft Defender Virüsten Koruma'yı yapılandırma ve yönetme ](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Henüz yapmadıysanız<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Microsoft 365 Defender portalınızı</a> uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve kuruluşunuzun genel güvenlik duruşu hakkında ayrıntılı bilgileri görüntülemek için yapılandırın.

Ayrıca son kullanıcıların Microsoft Defender Güvenlik Merkezi görüp göremeyeceğini ve hangi özellikleri görebileceğini de yapılandırabilirsiniz.

- [Microsoft Defender Güvenlik Merkezi genel bakış](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft Defender Güvenlik Merkezi](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Tehdit ve Güvenlik Açığı Yönetimi genel bakışını edinin](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft Defender Güvenlik Merkezi güvenlik işlemleri panosunu ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Intune ile Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration-intune.md)
