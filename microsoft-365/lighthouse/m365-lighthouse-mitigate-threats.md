---
title: Tehditlere ve tehditlere Microsoft Defender Virüsten Koruma
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
description: MICROSOFT 365 LIGHTHOUSE kullanan Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, güvenlik tehditlerini azaltmak Microsoft Defender Virüsten Koruma.
ms.openlocfilehash: 297c35104ae58efb1b7c58d3d1968158d42c0fce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315519"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Tehditlere ve tehditlere Microsoft Defender Virüsten Koruma

Microsoft 365 Lighthouse, iş ortaklarının tüm kiracılar genelinde tehditleri araştırmasına ve azaltmak için olanak sağlar. Ayrıca cihazlara virüsten koruma taramaları başlatabilirsiniz, cihazların en son Microsoft Defender Virüsten Koruma güncelleştirmelerini alıyor olduğundan emin olabilir ve virüsten koruma taramalarından sonra bekleyen eylemleri gözden geçirebilirsiniz. Deniz Feneri yalnızca daha sonraki bir Windows 10 çalışan cihazları destekler.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft 365 Lighthouse yalnızca iş ortağı kiracısına dağıtılır; müşteri kiracılarında değil, aynı zamanda sizin ve müşteri kiracıların bu kiracıların her ikisinde de listelenen gereksinimleri [karşı Microsoft 365 Lighthouse emin olun](m365-lighthouse-requirements.md).

- Kullanıcıların standart (Microsoft Defender Virüsten Koruma birlikte) çalıştır ediyor Windows. Deniz Feneri, Microsoft dışı virüsten koruma yazılımlarını desteklemez. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma](/mem/intune/user-help/turn-on-defender-windows).

- Oturum aktan sonra, iş ortağı kiracıda Genel Yönetici olmak gerekir.

## <a name="investigate-active-threats"></a>Etkin tehditleri araştırma

Belirli bir tehdide yönelik araştırma yapmak için:

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Tehditler **sekmesini** seçin.

3. Tehdit listesinden, araştırma yapmak istediğiniz tehditi seçin.

Tehdit ayrıntıları bölmesi aşağıdaki bilgileri sağlar:

| Kategori                                      | Tanım                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Cihaz ve kiracı                             | Tehdidin bulunduğu cihaz adı ve kiracı. Ek bilgileri görmek için cihazın adını seçin. |
| Tehdit durumu                                 | Tehdidin durumu.                                                                                    |
| Tehdit türü                                   | Tehdit türü.                                                                                              |
| Tehdit önem derecesi                               | Tehdit önem derecesi (Ciddi, Yüksek, Orta, Düşük, Bilinmiyor)                                                    |
| Örnekler                                     | Bu tehdidin cihaz üzerinde kaç kez mevcut olduğunu gösterir.                                                    |
| İlk olarak algılandı                                | Tehdit bu cihazda ilk kez algılandığında.                                                           |
| Belgeler                                 | Tehditle ilgili ek bilgilere bağlantı.                                                             |
| Bu tehdit ile bu kiracının diğer cihazları | Aynı kiracıda aynı etkin tehdit olan diğer cihazların listesi.                                      |
| Bu tehdit ile diğer kiracılar                | Aynı etkin tehditle diğer kiracıların listesi.                                                         |

Belirli bir cihaza yönelik tehditleri araştırmak için:

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Virüsten **Koruma sekmesini** seçin.

3. Listeden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde Geçerli **tehditler sekmesini** seçin.

Deniz feneri, cihazda bulunan tüm tehditleri görüntüler. Ayrıntıları görmek için tehdidi seçin.

## <a name="scan-for-threats-on-a-device"></a>Bir cihazda tehditlere karşı tarama

Hızlı tarama, kayıt defteri anahtarları ve başlangıç klasörleri gibi kötü amaçlı yazılımlara neden olan yaygın konumları arar. Tam tarama işlemi tüm cihazda arama verir. Çoğu durumda, hızlı tarama yeterli olur ve zamanlanmış taramalar için önerilen seçenektir.

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Virüsten **Koruma sekmesini** seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde Tam tarama çalıştır **veya Hızlı tarama** **çalıştır'ı seçin**.

Ayrıca, listeden her bir cihaz adının yanındaki onay kutusunu seçerek ve ardından Tam tarama çalıştır veya Hızlı tarama çalıştır'ı **seçerek birden çok** **cihazı tarayabilirsiniz**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Daha fazla bilgi için güncelleştirme Microsoft Defender Virüsten Koruma

Tek bir Microsoft Defender Virüsten Koruma güncelleştirme yapmak için:

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Virüsten **Koruma sekmesini** seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde Virüsten korumayı **güncelleştir'i seçin**.

Listede her cihaz adının yanındaki onay kutusunu seçerek ve ardından Virüsten koruma yazılımını güncelleştir'i seçerek birden çok cihaz için **güncelleştirmeler edinebilirsiniz**.

Yeni bir ilke oluşturmanız gerekirse, cihaz ayrıntıları bölmesinde **İlkeyi** güncelleştir'i seçin. Deniz Feneri sizi deniz fenerine (MEM) Microsoft Endpoint Manager yönlendirecek. İlke oluşturma hakkında daha fazla bilgi için bkz. [İlke altında uyumluluk Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Cihazda bekleyen virüsten koruma eylemlerini denetleme

Bir cihaza art arda eylemler uygulandığında, eylem için bekleyen bir ileti alırsınız. Cihazda bekleyen eylemleri kontrol etmek için:

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Virüsten **Koruma sekmesini** seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde, bekleyen eylemleri **görüntülemek için Cihaz eylem** durumları sekmesini seçin.

## <a name="restart-a-device"></a>Cihazı yeniden başlatma

Bazı güncelleştirmeler için cihazın düzgün bir şekilde yeniden başlatılması gerekiyor olabilir.

1. Deniz Feneri'nin sol gezinti bölmesinde Tehdit **yönetimi'ni seçin**.

2. Virüsten **Koruma sekmesini** seçin.

3. Cihaz listesinden bir cihaz seçin.

4. Cihaz ayrıntıları bölmesinde Cihazı yeniden **başlat'ı seçin**.

Ayrıca, listeden her cihaz adının yanındaki onay kutusunu seçin ve ardından Cihazı yeniden başlat'ı seçerek birden çok cihazı **yeniden başlatabilirsiniz**.

## <a name="related-content"></a>İlgili içerik

[Sistem Gereksinimleri Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (makale)\
[Tehdit yönetimi sayfasına genel bakış ](m365-lighthouse-threat-management-page-overview.md) (makale)\
[Microsoft Intune'de uyumluluk](/mem/intune/protect/create-compliance-policy) ilkesi oluşturma (makale)\
[Microsoft Defender Virüsten Koruma](/mem/intune/user-help/turn-on-defender-windows) (makale)\
[Microsoft Güvenlik Zekası](https://www.microsoft.com/wdsi/threats) (web sayfası)