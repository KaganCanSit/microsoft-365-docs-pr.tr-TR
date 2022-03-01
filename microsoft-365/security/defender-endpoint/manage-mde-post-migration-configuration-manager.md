---
title: Configuration Manager kullanarak Uç Nokta için Microsoft Defender'ı yönetme
description: Configuration Manager ile Uç Nokta için Microsoft Defender'ı yönetmeyi öğrenin
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
- m365solution-scenario
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 40bac47a4c22e3a8706ed4b38b479fff5d500410
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027514"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configuration Manager ile Uç Nokta için Microsoft Defender'ı Yönetme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Microsoft Endpoint Manager([Intune](/mem)) Microsoft Intune ve [Microsoft Endpoint Configuration Manager](/mem/intune/fundamentals/what-is-intune) (Configuration Manager) gibi cihazlarınıza yönelik tehdit koruması özelliklerini [](/mem/configmgr/core/understand/introduction) yönetmek için Microsoft Endpoint Configuration Manager (Configuration Manager) kullanmanızı öneririz ( uç noktalar olarak da adlandırılır).

- [Daha fazla bilgi Endpoint Manager](/mem/endpoint-manager-overview)
- [Configuration Manager ve Intune ile Windows 10 ve Windows cihazlarda Uç Nokta için Microsoft Defender'ı birlikte yönetme](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Configuration Manager ile Uç Nokta için Microsoft Defender'ı Yapılandırma

<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**2010'a** sahip değilken Yapılandırma Yöneticisi konsolunu yükleme <br/><br/> *Henüz Yapılandırma Yönetim konsolunuz yoksa, bitleri almak ve yüklemek için bu kaynakları kullanın.*|[Yükleme ortamını al](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Configuration Manager konsolunu yükleme](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Cihazları Uç Nokta için Microsoft Defender'a ekleme için Configuration Manager'ı** kullanma <br/><br/> *Henüz Uç Nokta için Microsoft Defender'a ekli cihazlarınız (veya uç noktalarınız) varsa, bunu Configuration Manager ile de kullanabilirsiniz.*|[Configuration Manager ile Uç Nokta için Microsoft Defender'a Ekleme](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Kötü amaçlı yazılımdan koruma ilkelerini ve Windows bilgisayarlar için Güvenlik Duvarı** güvenliğini yönetme (uç noktalar) <br/><br/> *Uç nokta için Microsoft Defender, exploit protection, uygulama denetimi, kötü amaçlı yazılımdan koruma, güvenlik duvarı ayarları gibi daha birçok uç nokta koruma özelliklerini yapılandırabilirsiniz.*|[Yapılandırma Yöneticisi: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Kötü amaçlı yazılımlardan koruma güncelleştirmelerini kuruluş** cihazlarında güncelleştirme yöntemlerini seçme <br/><br/> *Configuration Manager Endpoint Protection da farklı yöntemler kullanarak, kötü amaçlı yazılımdan koruma tanımlarını kuruluş cihazlarında güncel tutmak için çeşitli yöntemlerden birini seçebilirsiniz.*|[Güncelleştirmeler için tanım güncelleştirmelerini Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Tanım güncelleştirmeleri yapmak için Yapılandırma Yöneticisi'ni kullanma](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Çalışanların İnternet'de** kötü amaçlı içerik kullanan uygulamaları kullanmalarını önlemeye yardımcı olmak için Ağ Korumasını Etkinleştir <br/><br/> *Bir test [ortamında, hangi](/microsoft-365/security/defender-endpoint/evaluate-network-protection) uygulamaların gitmeden önce engellenmiş olacağını görmek için önce ağ koruması için denetim modunu kullanmanız önerilir.*|[Configuration Manager ile ağ korumasını açma](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Fidye yazılımlarına karşı korunmak için** denetimli klasör erişimini yapılandırma <br/><br/> *Denetimli klasör erişimi, yazılım önleme yazılımı koruması olarak da adlandırılır.*|[Uç nokta koruması: Denetimli klasör erişimi](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Microsoft Uç Nokta Yapılandırma Yönetimi'de denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Daha önce bunu yapmadısanız, Microsoft 365 Defender portalınızı uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve genel güvenlik sonrası hakkında ayrıntılı bilgileri görüntülemek üzere yapılandırabilirsiniz. Bkz. Saldırı algılandığında ve durdurulurken "ilk erişim uyarısı" gibi uyarılar tetiklendi ve [Microsoft 365 Defender portalda görüldü](/microsoft-365/security/defender/microsoft-365-defender). Ayrıca, son kullanıcıların portalda hangi özellikleri göreceğini Microsoft 365 Defender.

- [Genel bakış Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl olduğunu genel Tehdit ve Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft 365 Defender portal güvenlik işlemleri panosuna ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Intune ile Uç Nokta için Microsoft Defender'ı yönetme](manage-mde-post-migration-intune.md)
