---
title: Microsoft Defender Virüsten Koruma ile tehditleri azaltma
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için Microsoft Defender Virüsten Koruma tehditleri azaltma hakkında bilgi edinin.
ms.openlocfilehash: 428370ce5e49bba0bc9489143864f9b88b2e8c3f
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824354"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma ile tehditleri azaltma

Microsoft 365 Lighthouse, iş ortaklarının tüm kiracılarınızda tehditleri araştırmasına ve azaltmasına olanak tanır. Ayrıca cihazlarda virüsten koruma taramaları başlatabilir, cihazların Microsoft Defender Virüsten Koruma için en son güncelleştirmeleri almasını sağlayabilir ve virüsten koruma taramalarının ardından bekleyen eylemleri gözden geçirebilirsiniz. Lighthouse yalnızca Windows 10 veya üzerini çalıştıran cihazları destekler.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft 365 Lighthouse yalnızca iş ortağı kiracısında dağıtılır; müşteri kiracılarında dağıtılmaz, ancak sizin ve müşteri kiracılarınızın [Microsoft 365 Lighthouse gereksinimlerinde listelenen gereksinimleri](m365-lighthouse-requirements.md) karşıladığından emin olun.

- Kullanıcıların Microsoft Defender Virüsten Koruma çalıştırıyor olması gerekir (Windows dahil). Lighthouse, Microsoft dışı virüsten koruma yazılımlarını desteklemez. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma açma](/mem/intune/user-help/turn-on-defender-windows).

- Oturum açmakta olduğunuz iş ortağı kiracısında Genel Yönetici olmanız gerekir.

## <a name="investigate-active-threats"></a>Etkin tehditleri araştırma

Belirli bir tehdidi araştırmak için:

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Tehditler** sekmesini seçin.

3. Tehdit listesinden araştırmak istediğiniz tehdidi seçin.

Tehdit ayrıntıları bölmesi aşağıdaki bilgileri sağlar:

| Kategori                                      | Tanım                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Cihaz ve kiracı                             | Tehdidin bulunduğu cihaz adı ve kiracı. Ek bilgileri görmek için cihaz adını seçin. |
| Tehdit durumu                                 | Tehdidin durumu.                                                                                    |
| Tehdit türü                                   | Tehdit türü.                                                                                              |
| Tehdit önem derecesi                               | Tehdidin önem derecesi (Şiddetli, Yüksek, Orta, Düşük, Bilinmeyen)                                                    |
| Örnek                                     | Cihazda bulunan bu tehdidin örnek sayısı.                                                    |
| İlk algılandı                                | Bu cihazda tehdit ilk algılandığında.                                                           |
| Belge                                 | Tehdit hakkında ek bilgilere bağlantı.                                                             |
| Bu kiracıdaki bu tehditle birlikte diğer cihazlar | Aynı kiracıdaki aynı etkin tehditle birlikte diğer cihazların listesi.                                      |
| Bu tehditle birlikte diğer kiracılar                | Aynı etkin tehdide sahip diğer kiracıların listesi.                                                         |

Belirli bir cihazdaki tehditleri araştırmak için:

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Virüsten koruma** sekmesini seçin.

3. Listeden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde **Geçerli tehditler** sekmesini seçin.

Lighthouse, cihazda bulunan tüm tehditleri görüntüler. Ayrıntıları görmek için tehdidi seçin.

## <a name="scan-for-threats-on-a-device"></a>Bir cihazdaki tehditleri tarama

Hızlı tarama, kayıt defteri anahtarları ve bilinen başlangıç klasörleri gibi kötü amaçlı yazılımların bulunabileceği yaygın konumları arar. Tam tarama, cihazın tamamını arar. Çoğu durumda hızlı tarama yeterlidir ve zamanlanmış taramalar için önerilen seçenektir.

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Virüsten koruma** sekmesini seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde **Tam tarama çalıştır** veya **Hızlı tarama çalıştır'ı** seçin.

Ayrıca, listedeki her cihaz adının yanındaki onay kutusunu seçip **Tam tarama çalıştır veya Hızlı tarama çalıştır'ı** seçerek birden çok cihazı **tarayabilirsiniz**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma güncelleştirmelerini alma

Microsoft Defender Virüsten Koruma tek bir cihazda güncelleştirmek için:

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Virüsten koruma** sekmesini seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde **Virüsten korumayı güncelleştir'i** seçin.

Listedeki her cihaz adının yanındaki onay kutusunu ve ardından **Virüsten korumayı güncelleştir'i** seçerek birden çok cihaz için güncelleştirmeler alabilirsiniz.

Yeni bir ilke oluşturmanız gerekiyorsa cihaz ayrıntıları **bölmesinden İlkeyi güncelleştir'i** seçin. Lighthouse sizi Microsoft Endpoint Manager(MEM) sayfasına yönlendirecektir. İlke oluşturma hakkında daha fazla bilgi için bkz. [Microsoft Intune'de uyumluluk ilkesi oluşturma](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Cihazda bekleyen virüsten koruma eylemlerini denetleme

Bir cihaza ardışık eylemler uygulandığında bekleyen bir eylem iletisi alırsınız. Bir cihazda hangi eylemlerin beklemede olduğunu denetlemek için:

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Virüsten koruma** sekmesini seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde, bekleyen eylemleri görüntülemek için **Cihaz eylem durumları** sekmesini seçin.

## <a name="restart-a-device"></a>Cihazı yeniden başlatma

Bazı güncelleştirmelerin doğru yüklenmesi için cihazın yeniden başlatılması gerekebilir.

1. Lighthouse'un sol gezinti bölmesinde **Tehdit yönetimi'ni** seçin.

2. **Virüsten koruma** sekmesini seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde **Cihazı yeniden başlat'ı** seçin.

Ayrıca, listedeki her cihaz adının yanındaki onay kutusunu seçip **Cihazı yeniden başlat'ı** seçerek birden çok cihazı yeniden başlatabilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse gereksinimleri](m365-lighthouse-requirements.md) (makale)\
[Tehdit yönetimi sayfasına genel bakış](m365-lighthouse-threat-management-page-overview.md) (makale)\
[Microsoft Intune'de uyumluluk ilkesi oluşturma](/mem/intune/protect/create-compliance-policy) (makale)\
[Microsoft Defender Virüsten Koruma aç](/mem/intune/user-help/turn-on-defender-windows) (makale)\
[Microsoft Güvenlik Zekası](https://www.microsoft.com/wdsi/threats) (web sayfası)
