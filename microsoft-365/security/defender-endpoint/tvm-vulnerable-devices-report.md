---
title: Korumasız cihazlar raporu - Tehdit ve Güvenlik Açığı Yönetimi
description: Zayıf cihaz eğilimlerini ve güncel istatistikleri gösteren bir rapor. Amaç, nefesi ve cihazınızın açık kalma kapsamını anlamanızdır.
keywords: Uç Nokta için Microsoft Defender ve TVM'ye açık cihazlar için Uç Nokta için Microsoft Defender, tvm, tehdit & saldırıya maruz kalma, tehdit ve güvenlik açığını azaltma, güvenlik yapılandırmasını izleme
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
ms.openlocfilehash: fa5280d9c6f396e8e164397210c1b58dfcfc8d9b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466729"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>Korumasız cihazlar raporu - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Rapor, korumasız cihaz eğilimleri ve güncel istatistikleri olan grafikleri ve çubuk grafikleri gösterir. Amaç, nefesi ve cihazınızın açık kalma kapsamını anlamanızdır.

Raporlar ve Korumasız cihazlar Microsoft 365 Defender a gidip raporlar **> erişin**

İki sütun vardır:

- Eğilimler (zamanla). Son 30 günü, 3 ay, 6 ayyı veya özel bir tarih aralığını gösterebilir.
- Durum (geçerli bilgiler)

**Filtre**: Verileri güvenlik açığı önem düzeyi, açıkları açıkları, güvenlik açığı yaşı, işletim sistemi platformu, Windows 10 ya da Windows 11 ya da cihaz grubuna göre filtre edebilirsiniz.

**Detaya** gitme: Daha fazla bilgi araştırmak istediğiniz bir içgörü varsa, cihaz envanteri sayfasında filtrelenmiş cihazların listesini görüntülemek için ilgili çubuk grafiği seçin. Buradan listeyi dışarı aktarabilirsiniz.

## <a name="severity-level-graphs"></a>Önem düzeyi grafikleri

Her cihaz, söz konusu cihazda bulunan en ciddi güvenlik açığına bağlı olarak yalnızca bir kez sayılır.

:::image type="content" source="images/tvm-report-severity.png" alt-text=" Geçerli cihaz güvenlik açığı önem düzeylerini ve zaman içinde bu düzeyleri gösteren grafikler." lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>Exploit availability graphs

Her cihaz, en yüksek bilinen exploit düzeyine bağlı olarak yalnızca bir kez sayılır.

:::image type="content" source="images/tvm-report-exploit-availability.png" alt-text="Mevcut cihaz açıklarını ve zaman içinde kullanılabilirliği gösteren grafikler" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>Güvenlik açığı yaşı grafikleri

Her cihaz en eski güvenlik açığı yayın tarihi altında yalnızca bir kez sayılır. Eski güvenlik açıkları daha yüksek bir sömürülmek ihtimaline sahip.

:::image type="content" source="images/tvm-report-age.png" alt-text="Mevcut cihaz güvenlik açığı yaşını ve zaman içinde yaşa göre yaşı gösteren grafikler" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>İşletim sistemi platform grafiklerini kullanarak korumasız cihazlar

Her işletim sisteminde, yazılım güvenlik açıkları nedeniyle ortaya çıkacak cihaz sayısı.

:::image type="content" source="images/tvm-report-os.png" alt-text="İşletim sistemi platformuna göre mevcut korumasız cihazları ve işletim sistemi platformlarının korumasız cihazlarını zaman içinde gösteren grafikler" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>Yeni sürüm Windows tarafından korumasız cihazlar

Her sürümde, her Windows 10 veya Windows 11 ve korumasız uygulamalar veya işletim sistemi nedeniyle açığa açığa çıkaran cihaz sayısı.

:::image type="content" source="images/tvm-report-version.png" alt-text="Zaman içinde aynı sürüme göre Windows 10 zayıf cihazları ve aynı sürüme göre Windows 10 cihazları gösteren grafikler" lightbox="images/tvm-report-version.png":::

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
