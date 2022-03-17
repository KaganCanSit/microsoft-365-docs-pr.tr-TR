---
title: İş için Microsoft Defender'da Raporlar
description: İş için Microsoft Defender'da bulunan raporlara genel bir bakış elde edin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68b5c15b69c1f485bb9ed90bab06c2ceaa2978d9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527092"
---
# <a name="reports-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da Raporlar

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Web portalına () Microsoft 365 Defender raporları bulabilirsiniz[https://security.microsoft.com](https://security.microsoft.com). Bu makalede bu raporlar, bunları nasıl kullanabileceğiniz ve nasıl bulun olduğu açıklanmıştır.

<br/><br/>

## <a name="reports-in-defender-for-business"></a>İş için Defender'da Raporlar

|Rapor  |Açıklama  |
|---------|---------|
| **Güvenlik raporu**  | Güvenlik raporu, şirketinizin kimlikleri, cihazları ve uygulamaları hakkında bilgi sağlar. Bu rapora erişmek için gezinti bölmesinde **ReportsGeneralSecurity report'ı** >  >  **seçin**. <br/><br/>**İpucu** Benzer bilgileri, web portalınız portalında () Microsoft 365 Defender görüntüleyebilirsiniz [https://security.microsoft.com](https://security.microsoft.com). |
| **Tehdit koruması**  | Tehdit koruması raporu, uyarılar ve uyarı eğilimleri hakkında bilgi sağlar. Son 30 **gün içinde** tetiklenen uyarılar hakkında bilgileri görüntülemek için Uyarı eğilimleri sütununu kullanın. Çözümlenmemiş **uyarı** kategorileri ve bunların sınıflandırması gibi uyarılar hakkında geçerli anlık görüntü bilgilerini görüntülemek için Uyarı durumu sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsThreat** >  >  **protection'ı seçin**. <br/><br/>**İpucu**: Uyarılar hakkında bilgileri **görüntülemek için** Olaylar listesini de kullanabilirsiniz. Geçerli olayları görüntülemek ve yönetmek **için gezinti bölmesinde** Olaylar'ı seçin. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md). |
| **Cihaz durumu ve uyumluluğu** | Cihaz durumu ve uyumluluk raporu, cihaz durumu ve eğilimleri hakkında bilgi sağlar. Bu raporu, Defender for Business algılayıcılarının cihazlarda düzgün çalışıp çalışmadı veya algılayıcıların geçerli durumunu Microsoft Defender Virüsten Koruma. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsDevice** >  >  **durum ve uyumluluk'u seçin**. <br/><br/>**İpucu**: Cihazınızın cihazları **hakkında** bilgileri görüntülemek için Cihaz envanteri listesini kullanabilirsiniz. Gezinti bölmesinde Cihaz **envanteri'ni seçin**. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md). |
| **Korumasız cihazlar** | Zayıf cihazlar raporu, cihazlar ve eğilimler hakkında bilgi sağlar. Son 30 gün içinde uyarı içeren cihazlarla ilgili bilgileri görüntülemek için Eğilimler sütununu kullanın. Uyarı içeren **cihazlarla** ilgili geçerli anlık görüntü bilgilerini görüntülemek için Durum sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsYullanabilir** >  >  **cihazlar'ı seçin**.<br/><br/>**İpucu**: Cihazınızın cihazları **hakkında** bilgileri görüntülemek için Cihaz envanteri listesini kullanabilirsiniz. Gezinti bölmesinde Cihaz **envanteri'ni seçin**. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md). |
| **Web koruması** | Web koruma raporu kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, açıklarından yararlanma sitelerine, güvenilmeyen veya itibarsız sitelere ve açıkça engellenen sitelere erişme denemelerini gösterir. Engellenen site kategorileri yetişkin içeriği, boş zaman siteleri, yasal sorumluluk siteleri ve daha fazlasını içerir. Bu rapora erişmek için gezinti bölmesinde **ReportsEndpointsWeb** >  **protection'ı** >  seçin.<br/><br/>**İpucu**: Henüz şirketin web korumasını yapılandırmadınız, rapor **Ayarlar** Web Koruma düğmesini seçin. Sonra, **Kurallar'ın** altında **Web içeriği filtreleme'yi seçin**. Web içeriği filtreleme hakkında daha fazla bilgi edinmek için bkz [. Web içeriği filtreleme](../defender-endpoint/web-content-filtering.md). |

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="see-also"></a>Ayrıca bkz.

- [İş için Microsoft Defender'ı kullanmaya başlama](mdb-get-started.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md)