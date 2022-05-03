---
title: İş için Microsoft Defender raporları
description: İş için Defender'da güvenlik raporlarına genel bir bakış elde edin. Raporlar algılanan tehditleri, uyarıları, güvenlik açıklarını ve cihaz durumunu gösterir.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a4fbfc830c349df69180524305339582f444a609
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174833"
---
# <a name="reports-in-microsoft-defender-for-business"></a>İş için Microsoft Defender raporları

Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) çeşitli raporlar mevcuttur. Bu makalede bu raporlar, bunları nasıl kullanabileceğiniz ve nasıl bulabileceğiniz açıklanmaktadır.

## <a name="reports-in-defender-for-business"></a>İş için Defender'daki raporlar

|Rapor  |Açıklama  |
|---------|---------|
| **Güvenlik raporu**  | Güvenlik raporu şirketinizin kimlikleri, cihazları ve uygulamaları hakkında bilgi sağlar. Bu rapora erişmek için gezinti bölmesinde **RaporlarGenelGüvenlik** >  >  **raporu'na** tıklayın. <br/><br/>**IPUCU** Benzer bilgileri Microsoft 365 Defender portalınızın ([https://security.microsoft.com](https://security.microsoft.com)) giriş sayfasında görüntüleyebilirsiniz. |
| **Tehdit koruması**  | Tehdit koruması raporu, uyarılar ve uyarı eğilimleri hakkında bilgi sağlar. Son 30 gün içinde tetiklenen uyarılar hakkındaki bilgileri görüntülemek için **Uyarı eğilimleri** sütununu kullanın. Çözümlenmemiş uyarı kategorileri ve bunların sınıflandırması gibi uyarılar hakkındaki geçerli anlık görüntü bilgilerini görüntülemek için **Uyarı durumu** sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **RaporlarEndpointsThreat** >  >  **koruması'nı** seçin. <br/><br/>**İpucu**: Uyarılar hakkındaki bilgileri görüntülemek için **Olaylar** listesini de kullanabilirsiniz. Geçerli olayları görüntülemek ve yönetmek için gezinti bölmesinde **Olaylar'ı** seçin. Daha fazla bilgi için bkz. [İş için Microsoft Defender olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md). |
| **Cihaz durumu ve uyumluluğu** | Cihaz durumu ve uyumluluk raporu, cihaz durumu ve eğilimleri hakkında bilgi sağlar. İş için Defender algılayıcılarının cihazlarda düzgün çalışıp çalışmadığını ve Microsoft Defender Virüsten Koruma geçerli durumunu belirlemek için bu raporu kullanabilirsiniz. Bu rapora erişmek için gezinti bölmesinde **RaporlarEndpointsCihaz** >  >  **durumu ve uyumluluğu'na** tıklayın. <br/><br/>**İpucu**: Şirketinizin cihazları hakkındaki bilgileri görüntülemek için **Cihaz envanter** listesini kullanabilirsiniz. Gezinti bölmesinde **Cihaz envanteri'ni** seçin. Daha fazla bilgi için bkz. [İş için Microsoft Defender cihazları yönetme](mdb-manage-devices.md). |
| **Güvenlik açığı olan cihazlar** | Güvenlik açığı bulunan cihazlar raporu, cihazlar ve eğilimler hakkında bilgi sağlar. Son 30 gün içinde uyarıları olan cihazlar hakkındaki bilgileri görüntülemek için **Eğilimler** sütununu kullanın. Uyarı içeren cihazlar hakkındaki geçerli anlık görüntü bilgilerini görüntülemek için **Durum** sütununu kullanın. Bu rapora erişmek için gezinti bölmesinde **RaporlarEndpointsVulnerable** >  >  **cihazlar'ı** seçin.<br/><br/>**İpucu**: Şirketinizin cihazları hakkındaki bilgileri görüntülemek için **Cihaz envanter** listesini kullanabilirsiniz. Gezinti bölmesinde **Cihaz envanteri'ni** seçin. Daha fazla bilgi için bkz. [İş için Microsoft Defender cihazları yönetme](mdb-manage-devices.md). |
| **Web koruması** | Web koruma raporu kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, güvenlik açığından yararlanma sitelerine, güvenilmeyen veya saygınlığı düşük sitelere ve açıkça engellenen sitelere erişme girişimlerini gösterir. Engellenen sitelerin kategorileri yetişkin içeriği, boş zaman siteleri, yasal sorumluluk siteleri ve daha fazlasını içerir. Bu rapora erişmek için gezinti bölmesinde **RaporlarEndpointsWeb** >  >  **koruması'nı** seçin.<br/><br/>**İpucu**: Şirketiniz için henüz web koruması yapılandırmadıysanız rapor görünümünde **Ayarlar** düğmesini seçin. Ardından, **Kurallar'ın** altında **Web içeriği filtreleme'yi** seçin. Web içeriği filtreleme hakkında daha fazla bilgi edinmek için bkz. [Web içeriği filtreleme](../defender-endpoint/web-content-filtering.md). |

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="see-also"></a>Ayrıca bkz.

- [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)
