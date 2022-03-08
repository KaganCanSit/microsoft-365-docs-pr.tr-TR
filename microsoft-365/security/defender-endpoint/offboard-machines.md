---
title: Uç nokta için Microsoft Defender hizmetinin offboard cihazları
description: Uç Windows için Microsoft Defender'dan cihaz, sunucu, Windows olmayan cihazları ekleme
keywords: offboarding, Microsoft Defender for Endpoint offboarding, offboarding
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c2ec837ebc9fef0aabd2810dbd22db24597c52da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322611"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Uç nokta için Microsoft Defender hizmetinin offboard cihazları

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformlar**
- macOS
- Linux
- Windows Server 2012 R2
- Windows Server 2016

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Tercih ettiğiniz dağıtım yöntemine bağlı olarak ilgili yönergeleri izleyin.

> [!NOTE]
> Bir cihaz çıkarıldığında, 7 gün [sonra](fix-unhealthy-sensors.md#inactive-devices) Etkin Değil durumuna geçebilirsiniz.
>
> Çıkarılan cihazların verileri (Zaman Çizelgesi, Uyarılar, Güvenlik Açıkları vb.) yapılandırılmış bekletme süresi dolana kadar [portalda](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) kalır.
>
> Cihazın profili (veriler olmadan) en fazla 180 gün boyunca [](machines-view-overview.md) Cihazlar Listesinde kalır.
>
> Buna ek olarak, son 30 gün içinde etkin olunan cihazlar, kurum una açık kalma puanını ve Cihazlar için Microsoft Güvenli Puanı'Tehdit ve Güvenlik Açığı Yönetimi olan veriler üzerinde faktör faktöre bağlı değildir. [](tvm-exposure-score.md)
>
> Yalnızca etkin cihazları görüntülemek için algılayıcıların durumuna [, cihaz](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views) etiketlerine veya [makine gruplarına](machine-tags.md) göre [filtre edebilirsiniz](machine-groups.md).

## <a name="offboard-windows-devices"></a>Offboard Windows cihazlar

- [Yerel betik kullanan offboard cihazları](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Grup İlkesi kullanan offboard cihazları](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Mobil Cihaz Yönetimi araçlarını kullanan offboard cihazları](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Offboard Sunucuları

- [Offboard sunucuları](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Kapalı alan olmayan Windows cihazlar

- [Kapalı alan olmayan Windows cihazlar](configure-endpoints-non-windows.md#offboard-non-windows-devices)
