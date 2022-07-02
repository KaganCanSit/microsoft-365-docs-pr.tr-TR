---
title: Configuration Manager kullanarak Uç Nokta için Microsoft Defender yönetme
description: Configuration Manager ile Uç Nokta için Microsoft Defender yönetmeyi öğrenin
keywords: geçiş sonrası, yönetme, işlemler, bakım, kullanım, Configuration Manager, Uç Nokta için Microsoft Defender, edr
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: b253fe7dad271684f5c0e927ec162ea4e993df29
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607399"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configuration Manager ile Uç Nokta için Microsoft Defender yönetme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Intune [(](/mem/intune/fundamentals/what-is-intune)Intune) ve [Microsoft Endpoint Configuration Manager](/mem) (Configuration Manager) içeren [Microsoft Endpoint Manager](/mem/configmgr/core/understand/introduction) kullanmanızı öneririz ), kuruluşunuzun cihazlar için tehdit koruma özelliklerini (uç noktalar olarak da adlandırılır) yönetmeye yöneliktir.

- [Endpoint Manager hakkında daha fazla bilgi edinin](/mem/endpoint-manager-overview)
- [Configuration Manager ve Intune ile Windows 10 ve Windows 11 cihazlarda Uç Nokta için Microsoft Defender birlikte yönetme](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configuration Manager ile Uç Nokta için Microsoft Defender yapılandırma

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|Henüz sahip değilseniz **Configuration Manager konsolunu yükleyin** <br/><br/> *Yapılandırma Yöneticisi konsolunuz yoksa, bitleri almak ve yüklemek için bu kaynakları kullanın.*|[Yükleme medyasını alma](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Configuration Manager konsolunu yükleme](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**cihazları Uç Nokta için Microsoft Defender eklemek için Configuration Manager kullanma** <br/><br/> *Uç Nokta için Microsoft Defender'a henüz eklenmemiş cihazlarınız (veya uç noktalarınız) varsa, bunu Configuration Manager ile yapabilirsiniz.*|[Configuration Manager ile Uç Nokta için Microsoft Defender ekleme](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|kötü **amaçlı yazılımdan koruma ilkelerini ve istemci bilgisayarlar için Windows Güvenlik Duvarı güvenliğini yönetme** (uç noktalar) <br/><br/> *Uç Nokta için Microsoft Defender, yararlanma koruması, uygulama denetimi, kötü amaçlı yazılımdan koruma, güvenlik duvarı ayarları ve daha fazlası dahil olmak üzere uç nokta koruma özelliklerini yapılandırın.*|[Configuration Manager: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Kuruluşunuzun cihazlarında kötü amaçlı yazılımdan koruma güncelleştirmelerini güncelleştirme yöntemlerini seçme** <br/><br/> *Configuration Manager'da Endpoint Protection ile kötü amaçlı yazılımdan koruma tanımlarını kuruluşunuzun cihazlarında güncel tutmak için çeşitli yöntemler arasından seçim yapabilirsiniz.*|[Endpoint Protection için tanım güncelleştirmelerini yapılandırma](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Tanım güncelleştirmelerini teslim etmek için Configuration Manager kullanma](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|Çalışanların İnternet'te kötü amaçlı içerik kullanan uygulamaları kullanmasını önlemeye yardımcı olmak için **Ağ Koruması'nı etkinleştirin** <br/><br/> *Dağıtımdan önce hangi uygulamaların engellendiğini görmek için bir test ortamında ağ koruması için ilk olarak [denetim modunu](/microsoft-365/security/defender-endpoint/evaluate-network-protection) kullanmanızı öneririz.*|[Configuration Manager ile ağ korumasını açma](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|Fidye yazılımlarına karşı korunmak için **denetimli klasör erişimini yapılandırma** <br/><br/> *Denetimli klasör erişimi, antiransomware koruması olarak da adlandırılır.*|[Uç nokta koruması: Denetimli klasör erişimi](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Microsoft Endpoint Configuration Manage'da denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Henüz yapmadıysanız, Microsoft 365 Defender portalınızı uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve kuruluşunuzun genel güvenlik duruşu hakkında ayrıntılı bilgileri görüntülemek için yapılandırın. Bkz. Saldırı algılanıp durdurulurken, "ilk erişim uyarısı" gibi uyarılar tetiklendi ve [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) göründü. Ayrıca son kullanıcıların Microsoft 365 Defender portalında görüp göremeyeceğini ve hangi özellikleri görebileceğini de yapılandırabilirsiniz.

- [Microsoft 365 Defender genel bakış](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Tehdit ve Güvenlik Açığı Yönetimi genel bakışını edinin](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft 365 Defender portalı güvenlik işlemleri panosunu ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Intune ile Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration-intune.md)
