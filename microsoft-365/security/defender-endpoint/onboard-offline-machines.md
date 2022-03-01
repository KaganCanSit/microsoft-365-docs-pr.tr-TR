---
title: Uç nokta için Microsoft Defender'a İnternet erişimi olmayan cihazları ekleme
ms.reviewer: ''
description: İnternet erişimi olmayan cihazları kullanın; böylelikle uç nokta algılayıcısı için Microsoft Defender'a algılayıcı verileri gönderebilirsiniz
keywords: onboard, servers, vm, şirket içi, oms ağ geçidi, günlük analizi, azure günlük analizi, mma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: db219fe7ce39ae59668cedff10f03e931ddba416
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998255"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'a İnternet erişimi olmayan cihazları ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


İnternet erişimi olmayan cihazları işe almak için aşağıdaki genel adımları benimsersiniz:

> [!IMPORTANT] 
> Aşağıdaki adımlar yalnızca şu tür güncelleştirmelerin önceki sürümlerini Windows cihazlar için geçerlidir: Windows Server 2016 veya önceki sürümleri Windows 8.1 önceki sürümleri.

> [!NOTE]
> - OMS ağ geçidi sunucusu, 'TelemetryProxyServer' kayıt defteri veya GPO aracılığıyla yapılandırıldığında bağlantı Windows veya Windows Server cihazları için ara sunucu olarak kullanılamaz.
> - Telemetri Windows veya Windows Sunucu için - TelemetriProxyServer kullansanız bile, standart bir ara sunucu cihazına veya cihaza işaretmalıdır.
> - Buna ek olarak, Windows veya Windows Server bağlantısı kesik ortamlarda Sertifika Güveni Listelerini bir iç dosya veya web sunucusu aracılığıyla çevrimdışı güncelleştire mutlaka güncelleştirebilir.
> - CTL dosyalarını çevrimdışı güncelleştirme hakkında daha fazla bilgi için bkz. [CTL dosyalarını indirmek için dosya veya web sunucusu yapılandırma](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

Ekleme yöntemleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:
- [Windows'un önceki sürümlerini ekleme](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Uç nokta hizmeti için Microsoft Defender'a sunucuları ekleme](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="on-premises-devices"></a>Şirket içi cihazlar

- Ara sunucu veya hub gibi davranacak şekilde Azure Günlük Analizi'ni (eski adıyla OMS Ağ Geçidi) ayarlama:
  - [Azure Günlük Analizi Aracısı](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Kimlikte Uç Microsoft Monitoring Agent Alanı Anahtarı için Defender'ın (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) noktasını yükleme ve & yapılandırma

[Windows'un önceki sürümlerini ekleme](onboard-downlevel.md)

- Aynı Azure Log Analytics ağının çevrimdışı cihazları
  - MMA'yı aşağıdakilere işaret etmek üzere yapılandırma:
    - Ara sunucu olarak Azure Log Analytics IP'si
    - Uç nokta çalışma alanı anahtarı & Defender

## <a name="azure-virtual-machines"></a>Azure sanal makineleri

- Ara sunucu veya hub gibi davranacak şekilde Azure Günlük Analizi Ağ Geçidi'ni (eski adıyla OMS Ağ Geçidi) ayarlama:
    - [Azure Log Analytics Ağ Geçidi](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Kimlikte Uç Microsoft Monitoring Agent Alanı Anahtarı için Defender'ın (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) noktasını yükleme ve & yapılandırma
- Aynı OMS Ağ Geçidi ağı ağının çevrimdışı Azure sanal dosyaları
    - Azure Log Analytics IP'sini ara sunucu olarak yapılandırma
    - Azure Log Analytics Workspace Key & ID
- Bulut için Microsoft Defender
    - [Güvenlik İlkesi \> Log Analytics Çalışma Alanı](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Verilerime erişmek \> için Tehdit Algılaması Uç Nokta için Defender'a İzin Ver](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Daha fazla bilgi için bkz [. Güvenlik ilkeleriyle çalışma](/azure/security-center/tutorial-security-policy).
