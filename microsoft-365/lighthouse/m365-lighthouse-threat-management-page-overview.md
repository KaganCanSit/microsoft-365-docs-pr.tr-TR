---
title: Microsoft 365 Lighthouse Yönetimi sayfasına genel bakış
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
description: Yönetilen Hizmet Sağlayıcıları (MSP) Microsoft 365 Lighthouse Tehdit yönetimi sayfası hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: e57163ba462e241c74a96db78fe701c024a037ff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329890"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>Microsoft 365 Lighthouse Yönetimi sayfasına genel bakış 

**Aşağıdakiler için geçerlidir:**

- Windows 10

Microsoft Defender Virüsten Koruma, kullanıcıları ve cihazları virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerine karşı korur. Windows 10 ve Microsoft365E3'de&nbsp;&nbsp; yerleşik olarak bulunan güçlü, sürekli Microsoft 365 İş Ekstra korumadır.  
  
Müşteri kiracılarınızı tehditlere karşı güvenlik Microsoft 365 Lighthouse için sol gezinti bölmesinde Tehdit  Yönetimi'ni seçin. Sizin ilginizi ve riski azaltmanıza yardımcı olacak önerilerinizi gerektiren kiracıları, kullanıcıları ve cihazları görebilirler.  
  
## <a name="overview-tab"></a>Genel Bakış sekmesi  
  
Tehdit yönetimi sayfasının Genel Bakış sekmesinde, dikkat gereken alanları tanımlamak için tüm kiracılar genelinde virüsten koruma durumunu izleyebilirsiniz.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Genel Bakış sekmesinin ekran görüntüsü.":::

## <a name="threats-tab"></a>Tehdit sekmesi

Tehdit yönetimi sayfasının Tehditler sekmesinde tüm kiracılar genelinde Etkin, Risk Azaltma, Çözümlenmiş ve İzin Verilen tehditlerini görebilirsiniz. Ayrıca, hangi cihazların, kullanıcıların veya kiracıların etkilendiğini öğrenmek için her tehdide filtre uygulama ve inerek tüm kiracılar genelinde birden çok tehdityi aynı anda düzeltmeniz de gerekir.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Varsayılan taban çizgisi sayfasının ekran görüntüsü.":::
  
Tehditleri şu ölçütlerle filtreleysiniz:

- Tehdit durumu
- Tehdit önem derecesi
- Tehdit türü
- Tarih aralığı

Aşağıdaki tabloda farklı tehdit durumları ve onların tanımı listelemiştir:<br><br>

| Tehdit durumu | Tanım |
|--|--|
| Etkin | Tehdit cihazda etkindir. |
| Durumu yok | Tehdit durumu kullanılamıyor. Tehdidi yeniden algılamak için cihazda Microsoft Defender Virüsten Koruma taramayı çalıştırın. |
| Eylem başarısız oldu | Cihaz risk altında değildir. Bir eylem başarısız oldu, ancak cihazda olası bir tehdit durduruldu ve etkin değil. Cihazda tam taramayı çalıştırın. |
| El ile gerekli adımlar | Tehdit durduruldu ancak tam tarama veya cihazın yeniden başlatması gibi elle bir adımın tamamlandıktan sonra gerçek zamanlı olarak başlatılmasını gerektirir. |
| Tam tarama gerekli | Cihazın tam taraması gereklidir. |
| Yeniden başlatma gerekiyor | Cihazın yeniden başlatılması gerekir. |
| Kritik olmayan hatalarla düzeltildi | Tehdit düzeltildi ve başka eyleme gerek yok. |
| Karantinaya alındı | Tehdit karantinaya alındı. Başka işlem gerekmez. |
| Kaldırıldı | Tehdit cihazdan başarıyla kaldırıldı. Başka işlem gerekmez. |
| Temizlendi | Microsoft Defender Virüsten Koruma dosyalar kurtarıldı ve ele geçirildi. Başka işlem gerekmez. |
| İzin verildi | Tehdit, yöneticinin cihazda kalmasını sağlar. | 

## <a name="antivirus-protection-tab"></a>Virüsten koruma sekmesi

Tehdit yönetimi sayfasındaki Virüsten Koruma sekmesi, tüm kiracılar ve onların güvenlik Microsoft Defender Virüsten Koruma gösterir. Durumu değerlendirebilir ve korumasız durumda olan bir veya birden çok cihaz için eyleme geçebilirsiniz. Cihaza Genel Bakış, Geçerli Tehditler ve Cihaz Eylemi durumları gibi daha fazla bilgi görüntülemek için bir cihaz da seçin.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Virüsten Koruma sekmesinin ekran görüntüsü.":::

## <a name="related-content"></a>İlgili içerik

[Temel Microsoft 365 Lighthouse dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
