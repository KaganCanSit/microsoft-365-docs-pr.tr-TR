---
title: Geçiş Uç Nokta için Microsoft Defender - Hazırla
description: Geçiş yapmaya hazır olun ve Uç Nokta için Microsoft Defender. Cihazlarınızı güncelleştirin ve ağ bağlantılarınızı yapılandırabilirsiniz.
keywords: geçiş, Uç Nokta için Microsoft Defender, en iyi yöntem
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
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: aa0bd45c1765e2aa794e00e437bf08a63d1d742f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476741"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Geçiş Uç Nokta için Microsoft Defender - Aşama 1: Hazırlık

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Aşama 1: Hazırlık.](images/phase-diagrams/prepare.png#lightbox)<br/>Aşama 1: Hazırlama | [![Aşama 2: Ayarlama](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Aşama 2: Ayarlama](switch-to-mde-phase-2.md) | [![Aşama 3: Ekleme](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Aşama 3: Ekleme](switch-to-mde-phase-3.md) |
|--|--|--|
|*Buradasınız!*| | |

**Uç nokta için [Defender'a geçişin Hazırlık aşamasına hoş geldiniz](switch-to-mde-overview.md#the-migration-process)**.

Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Güncelleştirmeleri kuruluşun cihazları arasında alın ve dağıtın](#get-and-deploy-updates-across-your-organizations-devices)
2. [Uç Nokta için Defender'ı Al](#get-microsoft-defender-for-endpoint).
3. [Portala erişim Microsoft 365 Defender ver](#grant-access-to-the-microsoft-365-defender-portal).
4. [Cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırabilirsiniz](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Güncelleştirmeleri kuruluşun cihazları arasında alın ve dağıtın

En iyi uygulama olarak, kuruluş cihazlarınızı ve uç noktalarını güncel tutmanızı sağlar. Var olan uç nokta koruma ve virüsten koruma çözümünün güncel olduğundan ve kuruma bağlı işletim sistemlerinin ve uygulamalarının da en son güncelleştirmelere sahip olduğundan emin olun. Bunu şimdi yapmak, uç nokta ve taşıma için Defender'a geçiş yaparken daha sonra sorunları Microsoft Defender Virüsten Koruma.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Var olan çözüme güncel olduğundan emin olun

Var olan uç nokta koruma çözümünün güncel olduğundan ve kuruluş cihazlarında en son güvenlik güncelleştirmelerinin olduğundan emin olun.

Yardıma mı ihtiyacınız var? Çözüm sağlayıcınızın belgelerine bakın.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Kuruluş cihazlarının güncel olduğundan emin olun

Kuruluş cihazlarınızı güncelleştirmek için yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:

<br/><br/>

|işletim sistemi|Kaynak|
|---|---|
|Windows|[Microsoft Update](https://www.update.microsoft.com)|
|macOS|[Mac'inize yazılımı güncelleştirme](https://support.apple.com/HT201541)|
|iOS|[IPhone, iPad veya iPod touch yazılımınızı güncelleştirme](https://support.apple.com/HT204204)|
|Android|[Android & güncelleştirme ve güncelleştirme denetleme](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: Sisteminizi Güncelleştirme](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

Artık kuruluş cihazlarınızı güncellemiş olduğunuuza göre, sıradaki adım Uç Nokta için Defender'ı almak, lisans atamak ve hizmetin sağlanmasıdır.

1. Bugün Uç Nokta için Defender'ı satın alın veya deneyin. [Ücretsiz denemeyi başlat veya bir teklif talep.](https://aka.ms/mdatp)

2. Lisanslarınızı doğru şekilde sağlandı doğrulayın. [Lisans durumunu kontrol edin](production-deployment.md#check-license-state).

3. Özel bulut örneğiniz Defender for Endpoint'ı ayarlayın. Bkz [. Uç nokta kurulumu için Defender: Kiracı yapılandırması](production-deployment.md#tenant-configuration).

4. Kuruluşlarda uç noktalar (örneğin cihazlar) internete erişmek için proxy kullanıyorsa bkz. Uç nokta kurulumu için [Defender: Ağ yapılandırması](production-deployment.md#network-configuration).

Bu noktada, güvenlik yöneticilerinize ve güvenlik işleçlerine bu portalı kullanarak erişim Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">hazır olursunuz</a>.

> [!NOTE]
> Microsoft 365 Defender portalı bazen Uç Nokta için Defender portalı olarak da adlandırılır ve portalın üzerinden erişilebilir<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. Eski Microsoft Defender Güvenlik Merkezi (https://securitycenter.windows.com) yakında yeni portala Microsoft 365 Defender yönlendirecek. Daha fazla bilgi edinmek için [portala Microsoft 365 Defender bakın](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Portala erişim Microsoft 365 Defender ver

En <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a>, Uç Nokta için Defender'ın özelliklerine ve özelliklerine erişen ve yapılandırılan alandır. Daha fazla bilgi edinmek için [portala genel Microsoft 365 Defender bakın](use.md).

Ana Microsoft 365 Defender izinleri, temel izinler veya rol tabanlı erişim denetimi (RBAC) kullanılarak verebilirsiniz. İzinler üzerinde daha ayrıntılı denetime sahip olmak için RBAC'yi öneririz.

1. Güvenlik yöneticilerinizin ve güvenlik işleçlerinin rollerini ve izinlerini planla. Bkz [. Rol tabanlı erişim denetimi](prepare-deployment.md#role-based-access-control).

2. RBAC'yi ayarlayın ve yapılandıryın. Özellikle de [Intune](/mem/intune/fundamentals/what-is-intune) işletim sistemi, macOS, iOS ve Android cihazlarının bir birleşimini kullanıyorsa, RBAC Windows 10 i yapılandırmanız önerilir. Bkz[. Ayarları kullanarak RBAC Intune](/mem/intune/fundamentals/role-based-access-control).

    Organizasyonunız bu yöntemlerden farklı bir Intune gerektiriyorsa, aşağıdaki seçeneklerden birini seçin:

    - [Yapılandırma Yöneticisi](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [Gelişmiş grup ilkesi Yönetimi](/microsoft-desktop-optimization-pack/agpm)
    - [Windows Admin Center](/windows-server/manage/windows-admin-center/overview)

3. Portala erişim Microsoft 365 Defender. (Yardım mı gerekiyor? Bkz [. RBAC kullanarak portal erişimini yönetme](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma

Cihazlarınız ve Uç Nokta için Defender arasında iletişimi etkinleştirmek için, proxy ve İnternet ayarlarını yapılandırabilirsiniz. Aşağıdaki tabloda, çeşitli işletim sistemleri ve özellikler için ara sunucu ve İnternet ayarlarınızı yapılandırmak üzere kullanabileceğiniz kaynakların bağlantıları yer alır:

<br/><br/>

|Özellikler|İşletim Sistemi|Kaynaklar|
|---|---|---|
|[Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) (EDR)|[Windows 10](/windows/release-health/release-information) veya sonrası<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 veya sonrası](/windows-server/get-started/whats-new-in-windows-server-1803)|[Makine ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)|
|EDR|[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Proxy ve internet bağlantısı ayarlarını yapılandırma](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|EDR|macOS (sistem [gereksinimlerine bakın)](microsoft-defender-endpoint-mac.md)|[macOS'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-mac.md#network-connections)|
|[Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 veya sonrası](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)|[Ağ bağlantılarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-network-connections-microsoft-defender-antivirus.md)|
|Virüsten koruma|macOS (sistem [gereksinimlerine bakın)](microsoft-defender-endpoint-mac.md)|[macOS'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-mac.md#network-connections)|
|Virüsten koruma|Linux (sistem [gereksinimlerine bakın](microsoft-defender-endpoint-linux.md#system-requirements))|[Linux'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-linux.md#network-connections)|


## <a name="next-step"></a>Sonraki adım

**Tebrikler**! Uç nokta için **Defender'a** [geçişin Hazırlık aşamasını tamamladın](switch-to-mde-overview.md#the-migration-process)!

- [Uç Nokta için Defender'ı ayarlamaya devam edin](switch-to-mde-phase-2.md).
