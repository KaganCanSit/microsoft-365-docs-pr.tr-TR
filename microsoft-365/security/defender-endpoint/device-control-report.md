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
ms.openlocfilehash: f066610fec75b9c8f32e021460ae2f4b3471503c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998178"
---
# <a name="device-control-report"></a>Cihaz denetimi raporu

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta cihaz denetimi için Microsoft Defender, çıkarılabilir depolama cihazlarının ve USB sürücülerinin kullanımı gibi organizasyon cihazları tarafından medya kullanımını denetleyerek veri kaybına karşı koruma sağlar.

Cihaz denetim raporuyla, medya kullanımıyla ilgili olayları görüntüebilirsiniz; örneğin:

- **Denetim olayları:** Dış medya bağlandıktan sonra oluşan denetim olaylarının sayısını gösterir.
- **İlke olayları:** Cihaz denetimi ilkesi tetiklendiğinde oluşan ilke olaylarının sayısını gösterir.

> [!NOTE]
> Medya kullanımını izlemek için denetim olayı, Uç Nokta için Microsoft Defender'a ekli cihazlar için varsayılan olarak etkinleştirilir.

## <a name="understanding-the-audit-events"></a>Denetim olaylarını anlama

Denetim olayları şunlardır:

- **USB sürücü bağlama ve takma cihazını çıkar:** USB sürücü takılı veya bağlı değilken oluşturulan denetim olayları.
- **PnP:** Çıkarılabilir depolama alanı, yazıcı veya medya bağlı olduğunda Tak ve Bluetooth olayları oluşturulur.
- **Çıkarılabilir depolama alanı erişim denetimi:** Çıkarılabilir bir depolama erişimi denetimi ilkesi tetiklendiğinde olaylar oluşturulur. Denetim, Engelle veya İzin Ver olabilir.

## <a name="monitor-device-control-security"></a>Cihaz denetimi güvenliğini izleme

Uç Nokta için Microsoft Defender'daki cihaz denetimi, güvenlik yöneticilerine, raporlarda kuruluşlarının cihaz denetimi güvenliğini izlemelerine olanak sağlayan araçlar sağlar. Cihaz denetimi raporunu Raporlar ve Cihaz Microsoft 365 Defender'a > **bulabilirsiniz**.

Raporlar panosunda Cihaz **koruma** kartı, son 180 gün içinde medya türü tarafından üretilen denetim olaylarının sayısını gösterir.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](https://user-images.githubusercontent.com/81826151/138504137-e9a7673e-e988-48cd-820d-2625ec6df352.png)

Ayrıntıları **görüntüle düğmesi** , cihaz denetim raporu sayfasında daha fazla **medya kullanım verisi** gösterir.

Sayfa, tür başına toplam olay sayısı ve bir olay listesiyle birlikte bir pano sağlar. Yöneticiler saat aralığı, medya sınıfı adı ve cihaz kimliğine göre filtre uygulama.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportDetails](images/Detaileddevicecontrolreport.png)

Bir olayı seçinca, size daha fazla bilgi gösteren bir açılır sayfa görüntülenir:

- **Genel ayrıntılar:** Bu olayın tarihi, Eylem modu, ilke ve Access.
- **Medya bilgileri:** Medya bilgileri Medya adı, Sınıf adı, Sınıf GUID, Cihaz Kimliği, Satıcı Kimliği, Seri numarası ve Veri türü bilgilerini içerir.
- **Konum ayrıntıları:** Cihaz adı, Kullanıcı ve MDATP cihaz kimliği.

> [!div class="mx-imgBorder"]
> ![FilterOnDeviceControlReport](images/devicecontrolreportfilter.png)

Kuruluş genelinde bu medyanın gerçek zamanlı etkinliğini görmek için Gelişmiş avı **aç düğmesini** seçin. Bu, eklenmiş, önceden tanımlanmış bir sorguyu içerir.

> [!div class="mx-imgBorder"]
> ![QueryOnDeviceControlReport](images/Devicecontrolreportquery.png)

Cihazın güvenliğini görmek için açılır sayfada **Cihazı aç** sayfa düğmesini seçin. Bu düğme, cihaz varlık sayfasını açar.

> [!div class="mx-imgBorder"]
> ![DeviceEntityPage](images/Devicesecuritypage.png)

## <a name="reporting-delays"></a>Gecikmeleri bildirme

Cihaz denetimi raporu, medya bağlantısının olayın karta veya etki alanı listesine yansıt karşılaşması nedeniyle 12 saatlik bir gecikme süresine sahip olabilir.
