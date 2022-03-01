---
title: İş için Microsoft Defender'da raporlar (önizleme)
description: İş için Microsoft Defender'da (önizleme) kullanılabilen raporlara genel bir bakış elde edin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 85e1958c9577b68737aa2803dc115c83f757654e
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027578"
---
# <a name="reports-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da raporlar (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. İş için Microsoft Defender (önizleme), aşağıdaki tabloda açıklandığı gibi çeşitli raporlar içerir:<br/><br/>

Web portalına () Microsoft 365 Defender raporları bulabilirsiniz[https://security.microsoft.com](https://security.microsoft.com). Bu makalede bu raporlar, bunları nasıl kullanabileceğiniz ve nasıl bulun olduğu açıklanmıştır.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

<br/><br/>

## <a name="reports-in-defender-for-business"></a>İş için Defender'da Raporlar

|Rapor  |Açıklama  |
|---------|---------|
| **Güvenlik raporu**  | Güvenlik raporu, kurum kimlikleri, cihazları ve uygulamaları hakkında bilgi sağlar. Bu rapora erişmek için gezinti bölmesinde **ReportsGeneralSecurity report'ı** >  >  **seçin**. <br/><br/>**İpucu** Benzer bilgileri, web portalınız portalında () Microsoft 365 Defender görüntüleyebilirsiniz [https://security.microsoft.com](https://security.microsoft.com). |
| **Tehdit koruması**  | Tehdit koruması raporu, uyarılar ve uyarı eğilimleri hakkında bilgi sağlar. Son 30 **gün içinde** tetiklenen uyarılar hakkında bilgileri görüntülemek için Uyarı eğilimleri sütununu kullanın. Çözümlenmemiş **uyarı** kategorileri ve bunların sınıflandırması gibi uyarılar hakkında geçerli anlık görüntü bilgilerini görüntülemek için Uyarı durumu sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsThreat** >  >  **protection'ı seçin**. <br/><br/>**İpucu**: Uyarılar hakkında bilgileri **görüntülemek için** Olaylar listesini de kullanabilirsiniz. Geçerli olayları görüntülemek ve yönetmek **için gezinti bölmesinde** Olaylar'ı seçin. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da (önizleme) olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md). |
| **Cihaz durumu ve uyumluluğu** | Cihaz durumu ve uyumluluk raporu, cihaz durumu ve eğilimleri hakkında bilgi sağlar. Defender For Business (önizleme) algılayıcılarının cihazlarda düzgün çalışıp çalışmadı veya algılayıcıların geçerli durumunu belirlemek için bu Microsoft Defender Virüsten Koruma. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsDevice** >  >  **durum ve uyumluluk'u seçin**. <br/><br/>**İpucu**: Cihazınızın cihazları **hakkında bilgileri** görüntülemek için Cihaz envanteri listesini kullanabilirsiniz. Gezinti bölmesinde Cihaz **envanteri'ni seçin**. Daha fazla bilgi edinmek için bkz [. Microsoft Defender İş'te cihazları yönetme (önizleme).](mdb-manage-devices.md). |
| **Korumasız cihazlar** | Zayıf cihazlar raporu, cihazlar ve eğilimler hakkında bilgi sağlar. Son 30 gün içinde uyarı içeren cihazlarla ilgili bilgileri görüntülemek için Eğilimler sütununu kullanın. Uyarı içeren **cihazlarla** ilgili geçerli anlık görüntü bilgilerini görüntülemek için Durum sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsYullanabilir** >  >  **cihazlar'ı seçin**.<br/><br/>**İpucu**: Cihazınızın cihazları **hakkında bilgileri** görüntülemek için Cihaz envanteri listesini kullanabilirsiniz. Gezinti bölmesinde Cihaz **envanteri'ni seçin**. Daha fazla bilgi edinmek için bkz [. Microsoft Defender İş'te cihazları yönetme (önizleme).](mdb-manage-devices.md). |
| **Web koruması** | Web koruma raporu kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, açıklarından yararlanma sitelerine, güvenilmeyen veya itibarsız sitelere ve açıkça engellenen sitelere erişme denemelerini gösterir. Engellenen site kategorileri yetişkin içeriği, boş zaman siteleri, yasal sorumluluk siteleri ve daha fazlasını içerir. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsWeb** >  **protection'ı** >  seçin.<br/><br/>**İpucu**: Henüz sizin için web korumasını yapılandırmadısanız, rapor **görünümünde Ayarlar** Web Koruma düğmesini seçin. Sonra, **Kurallar'ın** altında **Web içeriği filtreleme'yi seçin**. Web içeriği filtreleme hakkında daha fazla bilgi edinmek için bkz [. Web içeriği filtreleme](../defender-endpoint/web-content-filtering.md). |

## <a name="see-also"></a>Ayrıca bkz.

- [İş için Microsoft Defender'ı (önizleme) kullanmaya başlama](mdb-get-started.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da cihazları yönetme (önizleme)](mdb-manage-devices.md)
