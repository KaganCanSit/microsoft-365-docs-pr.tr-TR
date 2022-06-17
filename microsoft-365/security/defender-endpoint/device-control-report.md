---
title: Cihaz denetimiyle kuruluşunuzun verilerini koruma
description: Cihaz denetimi raporları aracılığıyla kuruluşunuzun veri güvenliğini izleyin.
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
ms.openlocfilehash: 6fe93be2ec244628f2bf2195eb453307235ea06f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129195"
---
# <a name="device-control-report"></a>Cihaz denetimi raporu

**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender cihaz denetimi, kuruluşunuzdaki çıkarılabilir depolama cihazları ve USB sürücüleri gibi cihazların medya kullanımını izleyerek ve denetleyerek veri kaybına karşı koruma sağlar.

Cihaz denetimi raporuyla, medya kullanımıyla ilgili olayları görüntüleyebilirsiniz. Bu tür olaylar şunlardır:

- **Denetim olayları:** Dış medya bağlandığında gerçekleşen denetim olaylarının sayısını gösterir.
- **İlke olayları:** Cihaz denetimi ilkesi tetiklendiğinde gerçekleşen ilke olaylarının sayısını gösterir.

> [!NOTE]
> Medya kullanımını izlemeye yönelik denetim olayı, Uç Nokta için Microsoft Defender eklenen cihazlar için varsayılan olarak etkindir.

## <a name="understanding-the-audit-events"></a>Denetim olaylarını anlama

Denetim olayları şunlardır:

- **USB sürücü bağlama ve çıkarma:** BIR USB sürücüsü takıldığında veya çıkarıldığında oluşturulan olayları denetleyin.
- **PnP:** Çıkarılabilir depolama birimi, yazıcı veya Bluetooth medya bağlandığında Tak ve Kullan denetim olayları oluşturulur.
- **Çıkarılabilir depolama birimi erişim denetimi:** Çıkarılabilir depolama erişim denetimi ilkesi tetiklendiğinde olaylar oluşturulur. Denetim, Engelleme veya İzin Ver olabilir.

## <a name="monitor-device-control-security"></a>Cihaz denetimi güvenliğini izleme

Uç Nokta için Defender'daki cihaz denetimi, güvenlik yöneticilerine kuruluşlarının cihaz denetimi güvenliğini raporlar aracılığıyla izlemelerini sağlayan araçlarla güçlendiriyor. Cihaz denetim raporunu Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) bulabilirsiniz. **Raporlar** > **Genel** > **Güvenlik raporu'na** gidin. **Cihaz denetim** kartını bulun ve raporu açmak için bağlantıyı seçin. 

**Raporlar** panosundaki Cihaz koruma kartı, son 180 gün içinde medya türü tarafından oluşturulan denetim olaylarının sayısını gösterir.

**Ayrıntıları görüntüle** düğmesi **, cihaz denetimi rapor** sayfasında daha fazla medya kullanım verisi gösterir.

Sayfa, tür başına toplam olay sayısı ve olay listesi içeren bir pano sağlar ve sayfa başına 500 olay gösterir, ancak Yöneticiler daha fazla olay görmek için aşağı kaydırabilir ve zaman aralığına, medya sınıfı adına ve cihaz kimliğine göre filtreleyebilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Microsoft 365 Defender portalındaki Cihaz Denetimi Raporu Ayrıntıları sayfası" lightbox="images/Detaileddevicecontrolreport.png":::

Bir olayı seçtiğinizde, size daha fazla bilgi gösteren bir açılır öğe görüntülenir:

- **Genel ayrıntılar:** Tarih, Eylem modu, ilke ve Bu olayın Erişimi.
- **Medya bilgileri:** Medya bilgileri Medya adı, Sınıf adı, Sınıf GUID'si, Cihaz Kimliği, Satıcı Kimliği, Seri numarası ve Veri Yolu türünü içerir.
- **Konum ayrıntıları:** Cihaz adı, Kullanıcı ve MDATP cihaz kimliği.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Cihaz Denetimi Raporundaki Filtre sayfası" lightbox="images/devicecontrolreportfilter.png":::

Kuruluş genelinde bu medyanın gerçek zamanlı etkinliğini görmek için **Gelişmiş Avcılığı Aç** düğmesini seçin. Bu ekli, önceden tanımlanmış bir sorguyu içerir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Cihazda Sorgu Denetimi Raporu sayfası" lightbox="images/Devicecontrolreportquery.png":::

Cihazın güvenliğini görmek için açılır listede **Cihazı aç sayfası** düğmesini seçin. Bu düğme, cihaz varlığı sayfasını açar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Cihaz Varlığı Sayfası" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Raporlama gecikmeleri

Medya bağlantısının gerçekleşmesinden olayın karta veya etki alanı listesine yansıtılacağı zamana kadar 12 saate kadar bir gecikme olabilir.
