---
title: Korumasız cihazlar raporu - Tehdit ve Güvenlik Açığı Yönetimi
description: Zayıf cihaz eğilimlerini ve güncel istatistikleri gösteren bir rapor. Amaç, nefesi ve cihazınızın açık kalma kapsamını anlamanızdır.
keywords: Endpoint-tvm korumasına açık cihazlar için Microsoft Defender, Uç Nokta için Microsoft Defender, tvm, tehdit güvenlik & saldırıya maruz kalma durumunu azaltma, tehdit ve güvenlik açığını azaltma, güvenlik yapılandırmasını izleme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1f096433534abb91b9cb14b8db2737dacf566624
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997513"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>Korumasız cihazlar raporu - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Rapor, korumasız cihaz eğilimleri ve güncel istatistikleri olan grafikleri ve çubuk grafikleri gösterir. Amaç, nefesi ve cihazınızın açık kalma kapsamını anlamanızdır.

Raporlar ve Korumasız cihazlar Microsoft 365 Defender a gidip raporlar **> erişin**

İki sütun vardır:

- Eğilimler (zamanla). Son 30 günü, 3 ay, 6 ayyı veya özel bir tarih aralığını gösterebilir.
- Durum (geçerli bilgiler)

**Filtre**: Verileri güvenlik açığı önem düzeyi, açıkları açıkları, güvenlik açığı yaşı, işletim sistemi platformu, Windows 10 veya Windows 11 sürümüne ya da cihaz grubuna göre filtre edebilirsiniz.

**Detaya** gitme: Daha fazla bilgi araştırmak istediğiniz bir içgörü varsa, cihaz envanteri sayfasında filtrelenmiş cihazların listesini görüntülemek için ilgili çubuk grafiği seçin. Buradan listeyi dışarı aktarabilirsiniz.

## <a name="severity-level-graphs"></a>Önem düzeyi grafikleri

Her cihaz, söz konusu cihazda bulunan en ciddi güvenlik açığına bağlı olarak yalnızca bir kez sayılır.

:::image type="content" alt-text="Geçerli cihaz açığı önem düzeyi grafiklerinden biri ve zaman içinde düzeyleri gösteren bir grafik." source="images/tvm-report-severity.png" lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>Exploit availability graphs

Her cihaz, en yüksek bilinen exploit düzeyine bağlı olarak yalnızca bir kez sayılır.

:::image type="content" alt-text="Mevcut cihaz açıklarının kullanılabilirliğini gösteren bir grafik ve zaman içinde kullanılabilirliği gösteren bir grafik." source="images/tvm-report-exploit-availability.png" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>Güvenlik açığı yaşı grafikleri

Her cihaz en eski güvenlik açığı yayın tarihi altında yalnızca bir kez sayılır. Eski güvenlik açıkları daha yüksek bir sömürülmek ihtimaline sahip.

:::image type="content" alt-text="Geçerli cihaz güvenlik açığının yaşını gösteren bir grafik ve zaman içinde yaşı gösteren bir grafik." source="images/tvm-report-age.png" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>İşletim sistemi platform grafiklerini kullanarak korumasız cihazlar

Her işletim sisteminde, yazılım güvenlik açıkları nedeniyle ortaya çıkacak cihaz sayısı.

:::image type="content" alt-text="İşletim sistemi platformuna göre geçerli korumasız cihazların bir grafiği ve zaman içinde işletim sistemi platformlarının korumasız cihazları gösteren bir grafik." source="images/tvm-report-os.png" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>Yeni sürüm Windows tarafından korumasız cihazlar

Her bir sürümde, Windows 10 veya Windows 11 sürümüne sahip olan ve korumasız uygulamalar veya işletim sistemi nedeniyle açığa çıkaran cihaz sayısı.

![Aynı sürüme göre geçerli korumasız cihazların bir Windows 10 ve zaman içinde aynı sürüme göre zayıf Windows 10 gösteren bir grafik.](images/tvm-report-version.png)lightbox="images/tvm-report-version.png"::

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
