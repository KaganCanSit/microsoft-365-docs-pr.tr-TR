---
title: Geçiş sonrası Uç Nokta için Microsoft Defender'ı yönetme
description: Artık Uç Nokta için Microsoft Defender'a geçiş yaptığına göre, bir sonraki adımınız tehdit koruması özelliklerinizi yönetmektir
keywords: geçiş sonrası, yönetme, işlemler, bakım, kullanım, Uç Nokta için Microsoft Defender, edr
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
ms.topic: conceptual
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2be934da8a87e02ead5c395097d90ccde46cb9d7
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997083"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Uç Nokta için Microsoft Defender'ı yönetme, geçiş sonrası

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Önceki uç nokta korumanız ve virüsten koruma çözümden Uç Nokta için Microsoft Defender'a taşındıktan sonra, bir sonraki adımınız özellik ve yeteneklerinizi yönetmektir. Kuruluş [cihazlarınızı ve Microsoft Endpoint Manager](/mem/endpoint-manager-overview) ayarlarını [yönetmek için Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) bilgisayarlarını içeren Microsoft Endpoint Configuration Manager'i öneririz. Bununla birlikte, Etki Alanı Hizmetleri'nin kendi Etki Alanı Hizmetleri'sinde Grup [İlkesi Nesneleri Azure Active Directory kullanabilirsiniz](/azure/active-directory-domain-services/manage-group-policy).

Aşağıdaki tabloda, kullanabileceğiniz çeşitli araçlar/yöntemler listele birlikte daha fazla bilgi edinebilirsiniz.

<br/><br/>

|Araç/Yöntem|Açıklama|
|---|---|
|**[Yeni portalda güvenlik açığı yönetimi ve](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** pano [içgörülerini Microsoft 365 Defender](https://security.microsoft.com/) sağlar|Tehdit & güvenlik açığı yönetimi panosu, güvenlik işlemleri ekibimizin maruz kalmakta ve kuruluşun güvenlik açıkını geliştirmek için kullanabileceği işlem gerçekleştirilebilir bilgiler sağlar. <br/><br/> Bkz[. Tehdit & güvenlik açığı yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) [ve Tehditlere Genel Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (önerilir)|Microsoft Intune (Intune) bileşenleri arasında yer [alan Microsoft Endpoint Manager](/mem/endpoint-manager-overview), mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimine (MAM) odaklanır. Intune ile, cep telefonları, tabletler ve dizüstü bilgisayarlar gibi kuruluş cihazlarında nasıl kullanılacaklarını siz kontrol edin. Uygulamaları kontrol etmek için belirli ilkeler de yapılandırabilirsiniz. <br/><br/> Bkz [. Intune kullanarak Uç Nokta için Microsoft Defender'ı yönetme](manage-mde-post-migration-intune.md).|
|**[Microsoft Uç Noktası Yapılandırma Yöneticisi](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager olarak bilinen yapılandırma yöneticisi System Center Configuration Manager, bu uygulamanın bir [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Configuration Manager kullanıcılarınızı, cihazlarınızı ve yazılımınızı yönetmenize yardımcı olan güçlü bir araçtır. <br/><br/> Bkz [. Configuration Manager ile Uç Nokta için Microsoft Defender'ı Yönetme](manage-mde-post-migration-configuration-manager.md).|
|**[Etki Alanı Hizmetleri'Azure Active Directory Grup İlkesi Nesneleri](/azure/active-directory-domain-services/manage-group-policy)**|[Azure Active Directory Alanı Hizmetleri,](/azure/active-directory-domain-services/overview) kullanıcılar ve cihazlar için yerleşik Grup İlkesi Nesneleri içerir. Yerleşik Grup İlkesi Nesnelerini ortamınız için gereken şekilde özelleştirebileceğiniz gibi, özel Grup İlkesi Nesneleri ve kuruluş birimleri de oluşturabilirsiniz. <br/><br/> Bkz [. Grup İlkesi Nesneleriyle Uç Nokta için Microsoft Defender'ı Yönetme](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI ve MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Kuruluş cihazlarında Microsoft Endpoint Manager koruma özelliklerini yönetmek için Microsoft Endpoint Manager (Intune ve Configuration Manager'ı da içerir) kullanmanızı öneririz. Bununla birlikte, PowerShell, WMI veya Microsoft Defender Virüsten Koruma cihazlar (uç noktalar) ile tek tek cihazlarda (uç noktalar) ayarları gibi bazı MPCmdRun.exe yapılandırabilirsiniz.* <br/><br/> PowerShell'i kullanarak saldırı ve Microsoft Defender Virüsten Koruma azaltma kurallarını yönetabilirsiniz. Bkz [. PowerShell ile Uç Nokta için Microsoft Defender'ı Yapılandırma](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Dışlamaları Windows dışlamaları yönetmek için Yönetim Aracı'Microsoft Defender Virüsten Koruma kullanabilirsiniz. Bkz [. WMI ile Uç Nokta için Microsoft Defender'ı Yapılandırma](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Microsoft Kötü Amaçlı Yazılımdan Koruma yardımcı Command-Line Yardımcı Programı'nı (MPCmdRun.exe) Microsoft Defender Virüsten Koruma dışlamaları yönetmek ve ağınız ile bulut arasındaki bağlantıları doğrulamak için kullanabilirsiniz. Bkz [. Güvenlik Ayarları ile Uç Nokta için Microsoft Defender'MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)
