---
title: Cihaz denetimiyle kuruluş verilerinizi koruma
description: Cihaz denetimi raporları aracılığıyla cihazınızın veri güvenliğini izleme.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8a31ce05ed6986159d9f6e4c489e6f7707cfecc4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465299"
---
# <a name="device-control-report"></a>Cihaz denetimi raporu

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender denetimi, çıkarılabilir depolama cihazlarının ve USB sürücülerinin kullanımı gibi organizasyon cihazları tarafından medya kullanımını izleme ve denetlemeyle veri kaybına karşı koruma sağlar.

Cihaz denetim raporuyla, medya kullanımıyla ilgili olayları görüntüebilirsiniz; örneğin:

- **Denetim olayları:** Dış medya bağlandıktan sonra oluşan denetim olaylarının sayısını gösterir.
- **İlke olayları:** Cihaz denetimi ilkesi tetiklendiğinde oluşan ilke olaylarının sayısını gösterir.

> [!NOTE]
> Medya kullanımını izlemeyle ilgili denetim olayı, medya kullanımına hazır cihazlar için varsayılan Uç Nokta için Microsoft Defender.

## <a name="understanding-the-audit-events"></a>Denetim olaylarını anlama

Denetim olayları şunlardır:

- **USB sürücü bağlama ve takma cihazını çıkar:** USB sürücü takılı veya bağlı değilken oluşturulan denetim olayları.
- **PnP:** Tak ve Kullan bir depolama alanı, yazıcı veya medya bağlı olduğunda denetim Bluetooth olayları oluşturulur.
- **Çıkarılabilir depolama alanı erişim denetimi:** Çıkarılabilir bir depolama erişimi denetimi ilkesi tetiklendiğinde olaylar oluşturulur. Denetim, Engelle veya İzin Ver olabilir.

## <a name="monitor-device-control-security"></a>Cihaz denetimi güvenliğini izleme

Denetimler altında Uç Nokta için Microsoft Defender, güvenlik yöneticilerine, raporlar aracılığıyla kuruluşlarının cihaz denetimi güvenliğini izlemelerine olanak sağlayan araçlar sağlar. Cihaz denetimi raporunu Raporlar ve Cihaz Microsoft 365 Defender'a > **bulabilirsiniz**.

Raporlar panosunda Cihaz **koruma** kartı, son 180 gün içinde medya türü tarafından üretilen denetim olaylarının sayısını gösterir.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](https://user-images.githubusercontent.com/81826151/138504137-e9a7673e-e988-48cd-820d-2625ec6df352.png)

Ayrıntıları **görüntüle düğmesi** , cihaz denetim raporu sayfasında daha fazla **medya kullanım verisi** gösterir.

Sayfa, tür başına toplam olay sayısı ve bir olay listesiyle birlikte bir pano sağlar. Yöneticiler saat aralığı, medya sınıfı adı ve cihaz kimliğine göre filtre uygulama.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Microsoft 365 Defender portalında Cihaz Denetimi Microsoft 365 Defender sayfası" lightbox="images/Detaileddevicecontrolreport.png":::

Bir olayı seçinca, size daha fazla bilgi gösteren bir açılır sayfa görüntülenir:

- **Genel ayrıntılar:** Bu olayın tarihi, Eylem modu, ilke ve Access.
- **Medya bilgileri:** Medya bilgileri Medya adı, Sınıf adı, Sınıf GUID, Cihaz Kimliği, Satıcı Kimliği, Seri numarası ve Veri türü bilgilerini içerir.
- **Konum ayrıntıları:** Cihaz adı, Kullanıcı ve MDATP cihaz kimliği.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Cihaz Denetim Raporuna Göre FiltreLe sayfası" lightbox="images/devicecontrolreportfilter.png":::

Kuruluş genelinde bu medyanın gerçek zamanlı etkinliğini görmek için Gelişmiş avı **aç düğmesini** seçin. Bu, eklenmiş, önceden tanımlanmış bir sorguyu içerir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Cihaz Denetim Raporu Sayfasında Sorgu" lightbox="images/Devicecontrolreportquery.png":::

Cihazın güvenliğini görmek için açılır sayfada **Cihazı aç** sayfa düğmesini seçin. Bu düğme, cihaz varlık sayfasını açar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Cihaz Varlık Sayfası" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Gecikmeleri bildirme

Cihaz denetimi raporu, medya bağlantısının olayın karta veya etki alanı listesine yansıt karşılaşması nedeniyle 12 saatlik bir gecikme süresine sahip olabilir.
