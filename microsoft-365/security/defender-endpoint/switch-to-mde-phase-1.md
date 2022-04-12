---
title: Pertahanan Microsoft untuk Titik Akhir geçiş yapma - Hazırlama
description: Pertahanan Microsoft untuk Titik Akhir geçiş yapmaya hazırlanın. Cihazlarınızı güncelleştirin ve ağ bağlantılarınızı yapılandırın.
keywords: geçiş, Pertahanan Microsoft untuk Titik Akhir, en iyi uygulama
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
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: c08ab1c96adc2b9d83cc6869573f2f0dbe75ac78
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782929"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Pertahanan Microsoft untuk Titik Akhir Geçiş - 1. Aşama: Hazırlama

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![1. Aşama: Hazırlanın.](images/phase-diagrams/prepare.png#lightbox)<br/>Aşama 1: Hazırlık | [![Aşama 2: Kurulum](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Aşama 2: Kurulum](switch-to-mde-phase-2.md) | [![Aşama 3: Katılım](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Aşama 3: Katılım](switch-to-mde-phase-3.md) |
|--|--|--|
|*Buradasınız!*| | |

**[Uç Nokta için Defender'a geçmenin Hazırlama aşamasına](switch-to-mde-overview.md#the-migration-process) hoş geldiniz**.

Bu geçiş aşaması aşağıdaki adımları içerir:

1. [Güncelleştirmeleri kuruluşunuzun cihazlarına alma ve dağıtma](#get-and-deploy-updates-across-your-organizations-devices)
2. [Uç Nokta için Defender'ı edinin](#get-microsoft-defender-for-endpoint).
3. [Microsoft 365 Defender portalına erişim izni verin](#grant-access-to-the-microsoft-365-defender-portal).
4. [Cihaz ara sunucusu ve internet bağlantısı ayarlarını yapılandırın](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Güncelleştirmeleri kuruluşunuzun cihazlarına alma ve dağıtma

En iyi uygulama olarak, kuruluşunuzun cihazlarını ve uç noktalarını güncel tutun. Mevcut uç nokta koruma ve virüsten koruma çözümünüzün güncel olduğundan ve kuruluşunuzun işletim sistemleriyle uygulamalarının da en son güncelleştirmelere sahip olduğundan emin olun. Bunu şimdi yapmak, uç nokta ve Microsoft Defender Virüsten Koruma için Defender'a geçiş yaparken daha sonra sorunları önlemeye yardımcı olabilir.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Mevcut çözümünüzün güncel olduğundan emin olun

Mevcut uç nokta koruma çözümünüzü güncel tutun ve kuruluşunuzun cihazlarında en son güvenlik güncelleştirmelerinin olduğundan emin olun.

Yardıma mı ihtiyacınız var? Çözüm sağlayıcınızın belgelerine bakın.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Kuruluşunuzun cihazlarının güncel olduğundan emin olun

Kuruluşunuzun cihazlarını güncelleştirmek için yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:

|OS|Kaynak|
|---|---|
|Windows|[Microsoft Update](https://www.update.microsoft.com)|
|macOS|[Mac bilgisayarınızda yazılımı güncelleştirme](https://support.apple.com/HT201541)|
|iOS|[iPhone, iPad veya iPod touch'ınızı güncelleştirme](https://support.apple.com/HT204204)|
|Android|[Android sürümünüzü denetleme & güncelleştirme](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: Sisteminizi Güncelleştirme](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Pertahanan Microsoft untuk Titik Akhir alma

Kuruluşunuzun cihazlarını güncelleştirdiğinize göre, sonraki adım Uç Nokta için Defender'ı almak, lisans atamak ve hizmetin sağlandığından emin olmaktır.

1. Uç Nokta için Defender'i hemen satın alın veya deneyin. [Ücretsiz deneme başlatın veya teklif isteyin](https://aka.ms/mdatp).

2. Lisanslarınızın düzgün bir şekilde sağlandığını doğrulayın. [Lisans durumunuzu denetleyin](production-deployment.md#check-license-state).

3. Uç Nokta için Defender'ın ayrılmış bulut örneğini ayarlayın. Bkz [. Uç Nokta için Defender kurulumu: Kiracı yapılandırması](production-deployment.md#tenant-configuration).

4. Kuruluşunuzdaki uç noktalar (cihazlar gibi) İnternet'e erişmek için ara sunucu kullanıyorsa bkz. [Uç nokta için Defender kurulumu: Ağ yapılandırması](production-deployment.md#network-configuration).

Bu noktada, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalını</a> kullanacak güvenlik yöneticilerinize ve güvenlik operatörlerinize erişim izni vermek için hazırsınız.

> [!NOTE]
> Microsoft 365 Defender portalı bazen Uç Nokta için Defender portalı olarak adlandırılır ve adresine <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>adresinden erişilebilir. Eski Microsoft Defender Güvenlik Merkezi (https://securitycenter.windows.com) yakında Microsoft 365 Defender portalına yönlendirilir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portala genel bakış](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalına erişim izni verme

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a>, Uç Nokta için Defender'ın özelliklerine ve özelliklerine erişip yapılandırdığınız yerdir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalına genel bakış](use.md).

Microsoft 365 Defender portalına yönelik izinler, temel izinler veya rol tabanlı erişim denetimi (RBAC) kullanılarak verilebilir. İzinler üzerinde daha ayrıntılı denetim sahibi olmak için RBAC kullanmanızı öneririz.

1. Güvenlik yöneticileriniz ve güvenlik operatörleriniz için rolleri ve izinleri planlayın. Bkz [. Rol tabanlı erişim denetimi](prepare-deployment.md#role-based-access-control).

2. RBAC'yi ayarlayın ve yapılandırın. Özellikle kuruluşunuz [Windows 10](/mem/intune/fundamentals/what-is-intune), macOS, iOS ve Android cihazlarının birleşimini kullanıyorsa RBAC'yi yapılandırmak için Intune kullanmanızı öneririz. Bkz. [Intune kullanarak RBAC'yi ayarlama](/mem/intune/fundamentals/role-based-access-control).

    Kuruluşunuz Intune dışında bir yöntem gerektiriyorsa aşağıdaki seçeneklerden birini belirleyin:

    - [Yapılandırma Yöneticisi](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Gelişmiş grup ilkesi Yönetimi](/microsoft-desktop-optimization-pack/agpm)
    
    - [Windows Admin Center](/windows-server/manage/windows-admin-center/overview)

3. Microsoft 365 Defender portalına erişim izni verin. (Yardıma mı ihtiyacınız var? Bkz. [RBAC kullanarak portal erişimini yönetme](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Cihaz ara sunucusu ve internet bağlantısı ayarlarını yapılandırma

Cihazlarınız ile Uç Nokta için Defender arasında iletişimi etkinleştirmek için ara sunucu ve internet ayarlarını yapılandırın. Aşağıdaki tabloda, çeşitli işletim sistemleri ve özellikleri için proxy ve internet ayarlarınızı yapılandırmak için kullanabileceğiniz kaynakların bağlantıları yer alır:

|Yetenek -lerini|İşletim Sistemi|Kaynaklar|
|---|---|---|
|[Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) (EDR)|[Windows 10](/windows/release-health/release-information) veya üzeri<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 veya üzeri](/windows-server/get-started/whats-new-in-windows-server-1803)<br/><br/>[Windows Server 2016*](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Makine ara sunucusu ve internet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)|
|EDR [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Ara sunucu ve internet bağlantısı ayarlarını yapılandırma](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|EDR|macOS (bkz [. Sistem gereksinimleri](microsoft-defender-endpoint-mac.md)|[macOS'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-mac.md#network-connections)|
|[Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 veya üzeri](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Microsoft Defender Virüsten Koruma ağ bağlantılarını yapılandırın ve doğrulayın](configure-network-connections-microsoft-defender-antivirus.md)|
|Antivirus|macOS (bkz [. Sistem gereksinimleri](microsoft-defender-endpoint-mac.md)|[macOS'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-mac.md#network-connections)|
|Antivirus|Linux (bkz [. Sistem gereksinimleri](microsoft-defender-endpoint-linux.md#system-requirements))|[Linux'ta Uç Nokta için Defender: Ağ bağlantıları](microsoft-defender-endpoint-linux.md#network-connections)|

*Windows Server 2012 R2 ve 2016 için modern, birleşik çözümün yüklenmesini gerektirir. Daha fazla bilgi için bkz. [Windows sunucularını Pertahanan Microsoft untuk Titik Akhir hizmetine ekleme](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="next-step"></a>Sonraki adım

**Tebrikler**! [Uç Nokta için Defender'a geçmenin Hazırlama aşamasını](switch-to-mde-overview.md#the-migration-process) tamamladınız!

- [Uç Nokta için Defender'ı ayarlamaya devam edin](switch-to-mde-phase-2.md).
