---
title: Microsoft 365 Lighthouse Tehdit yönetimi sayfasına genel bakış
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için Tehdit yönetimi sayfası hakkında bilgi edinin.
ms.openlocfilehash: 94e71d648dac3a285ecef81b4dae29305cf7e98c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823178"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>Microsoft 365 Lighthouse Tehdit yönetimi sayfasına genel bakış 

**Şunlar için geçerlidir:**

- Windows 10

Microsoft Defender Virüsten Koruma kiracıları, kullanıcıları ve cihazları virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerine karşı korur. Windows 10 yerleşik olarak sunulan ve Microsoft 365 İş Ekstra ve Microsoft365E3&nbsp;&nbsp; ile birlikte sunulan sağlam ve sürekli bir korumadır.  
  
Microsoft 365 Lighthouse'daki Tehdit yönetimi sayfasına erişmek için sol gezinti bölmesinde **Tehdit Yönetimi'ni** seçerek müşteri kiracılarınızın tehditlere karşı güvenlik duruşunu görüntüleyin. Riski azaltmanıza yardımcı olacak dikkatinizi ve önerilerinizi gerektiren kiracıları, kullanıcıları ve cihazları görürsünüz.  
  
## <a name="overview-tab"></a>Genel Bakış sekmesi  
  
Tehdit yönetimi sayfasının Genel Bakış sekmesinde, dikkat edilmesi gereken alanları belirlemek için tüm kiracılarınızda virüsten koruma durumunu izleyebilirsiniz.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Genel Bakış sekmesinin ekran görüntüsü.":::

## <a name="threats-tab"></a>Tehditler sekmesi

Tehdit yönetimi sayfasının Tehditler sekmesinde tüm kiracılarınızda Etkin, Azaltılmış, Çözümlenmiş ve İzin Verilen tehditleri görebilirsiniz. Ayrıca, hangi cihazların, kullanıcıların veya kiracıların etkilendiğini öğrenmek için her bir tehdidi filtreleyip detaya inerek tüm kiracılarınızda aynı anda birden çok tehdidi düzeltebilirsiniz.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Varsayılan temel sayfasının ekran görüntüsü.":::
  
Tehditleri şu şekilde filtreleyebilirsiniz:

- Tehdit durumu
- Tehdit önem derecesi
- Tehdit türü
- Tarih aralığı

Aşağıdaki tabloda farklı tehdit durumları ve tanımları listeleniyor:<br><br>

| Tehdit durumu | Tanım |
|---|---|
| Etkin | Tehdit cihazda etkindir. |
| Durum yok | Tehdit durumu kullanılamıyor. Tehdidi yeniden Microsoft Defender Virüsten Koruma için cihazda tam tarama çalıştırın. |
| Eylem başarısız oldu | Cihaz risk altında değil. Bir eylem başarısız oldu, ancak olası bir tehdit durduruldu ve cihazda etkin değil. Cihazda tam tarama çalıştırın. |
| El ile gerekli adımlar | Tehdit durduruldu, ancak tam tarama veya cihazın yeniden başlatılması gibi el ile bir adımın tamamlanması gerekiyor. |
| Tam tarama gerekiyor | Cihazın tam taraması gereklidir. |
| Yeniden başlatma gerekiyor | Cihazın yeniden başlatılması gerekir. |
| Kritik olmayan hatalarla düzeltilmiş | Tehdit düzeltildi ve başka bir eyleme gerek yok. |
| Karantinaya | Tehdit karantinaya alındı. Başka eyleme gerek yoktur. |
| Kaldırıldı | Tehdit cihazdan başarıyla kaldırıldı. Başka eyleme gerek yoktur. |
| Temizlenmiş | Microsoft Defender Virüsten Koruma kurtarılmış ve dezenfekte edilmiş dosyalara sahiptir. Başka eyleme gerek yoktur. |
| Izin verilen | Bu tehdit, yönetici tarafından cihazda kalmasına izin verilir. | 

## <a name="antivirus-protection-tab"></a>Virüsten koruma sekmesi

Tehdit yönetimi sayfasındaki Virüsten koruma sekmesi, tüm kiracılarınız genelindeki cihazları ve Microsoft Defender Virüsten Koruma koruma durumlarını gösterir. Durumu değerlendirebilir ve güvenlik açığı olabilecek bir veya daha fazla cihaz için işlem yapabilirsiniz. Ayrıca bir cihazı seçerek Cihaza Genel Bakış, Geçerli Tehditler ve Cihaz Eylemi durumları gibi daha fazla bilgi görüntüleyebilirsiniz.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Virüsten Koruma sekmesinin ekran görüntüsü.":::

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse temellerini dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
