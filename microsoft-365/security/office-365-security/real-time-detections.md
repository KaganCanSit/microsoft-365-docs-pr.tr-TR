---
title: tehdit gezgini ve gerçek zamanlı algılamalar temelleri Office 365 için Microsoft Defender
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için Gezgin veya Gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e7f3109048f3a4931d25029df3db9a3c217d6354
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647435"
---
# <a name="explorer-and-real-time-detections"></a>Gezgin ve Gerçek zamanlı algılamalar

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu makalede:

- [Gezgin ile Gerçek zamanlı algılamalar arasındaki farklar](#differences-between-explorer-and-real-time-detections)
- [Gezgin ve Gerçek zamanlı algılamalar için güncelleştirilmiş deneyim](#updated-experience-for-explorer-and-real-time-detections)
- [Gerekli lisanslar ve izinler](#required-licenses-and-permissions)

> [!NOTE]
> Bu, **Gezgin (Tehdit Gezgini olarak da bilinir)**, **e-posta güvenliği** ve **Gezgin ile Gerçek zamanlı algılama temelleri** (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) hakkındaki **3 makalelik serinin** bir parçasıdır. Bu serideki diğer iki makale [Gezgin'de tehdit avcılığı ve Explorer](threat-hunting-in-threat-explorer.md) [ile E-posta güvenliğidir](email-security-in-microsoft-defender.md).

Bu makalede, Explorer ile gerçek zamanlı algılama raporlaması arasındaki fark, Explorer ile güncelleştirilmiş deneyim ve eski ve yeni deneyimler arasında geçiş yapabileceğiniz gerçek zamanlı algılamalar ile gerekli lisanslar ve izinler açıklanmaktadır.

[Kuruluşunuzda Office 365 için Microsoft Defender](defender-for-office-365.md) varsa ve [izinlere](#required-licenses-and-permissions) sahipseniz, tehditleri algılamak ve düzeltmek için **Gezgin'i** (**Tehdit Gezgini** olarak da bilinir) veya **Gerçek zamanlı algılamaları** kullanabilirsiniz.

konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, E-posta & işbirliği'ne** gidin ve **Gezgin** _veya_ **Gerçek zamanlı algılamalar'ı** seçin. Doğrudan sayfaya gitmek için veya <https://security.microsoft.com/realtimereports>kullanın<https://security.microsoft.com/threatexplorer>.

Bu araçlarla şunları yapabilirsiniz:

- Bkz. Microsoft 365 güvenlik özellikleri tarafından algılanan kötü amaçlı yazılım.
- Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın.
- Explorer'daki bir görünümden otomatik araştırma ve yanıt işlemi başlatın.
- Kötü amaçlı e-postaları ve daha fazlasını araştırın.

Daha fazla bilgi için bkz. [Explorer ile e-posta güvenliği](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Gezgin ile Gerçek zamanlı algılamalar arasındaki farklar

- *Gerçek zamanlı algılamalar*, Office 365 için Defender Plan 1'de kullanılabilen bir raporlama aracıdır. *Tehdit Gezgini*, Office 365 için Defender Plan 2'de kullanılabilen bir tehdit avcılığı ve düzeltme aracıdır.
- Gerçek zamanlı algılamalar raporu, algılamaları gerçek zamanlı olarak görüntülemenizi sağlar. Tehdit Gezgini bunu da yapar, ancak belirli bir saldırı için saldırı kampanyalarını vurgulama gibi ek ayrıntılar sağlar ve güvenlik operasyonları ekiplerine tehditleri düzeltme olanağı sağlar ( [Otomatik Araştırma ve Yanıt araştırmasını](automated-investigation-response-office.md) tetikleme dahil).
- *Tüm e-posta* görünümü Tehdit Gezgini'nde kullanılabilir ancak Gerçek zamanlı algılamalar raporuna dahil değildir.
- Tehdit Gezgini'ne zengin filtreleme özellikleri ve düzeltme eylemleri dahildir. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Hizmet Açıklaması: Office 365 için Defender planlarda özellik kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Gezgin ve Gerçek zamanlı algılamalar için güncelleştirilmiş deneyim

Tehdit Gezgini ve Gerçek zamanlı algılama deneyimi, modern erişilebilirlik standartlarıyla uyumlu olacak ve iş akışını iyileştirecek şekilde güncelleştirilir. Kısa bir süre için eski deneyimle yeni deneyim arasında geçiş yapabileceksiniz.  

> [!NOTE]
> Geçiş yalnızca hesabınızı etkiler ve kiracınızdaki diğer kişileri etkilemez. 

Tehdit Gezgini ve Gerçek zamanlı algılamalar aşağıdaki görünümlere ayrılır:

- *Tüm e-postalar*: Office 365 için Defender tarafından analiz edilen tüm e-postaları gösterir ve hem iyi hem de kötü amaçlı e-postalar içerir. Bu özellik yalnızca Tehdit Gezgini'nde bulunur ve Gerçek zamanlı algılamalarda kullanılamaz. Varsayılan olarak, 30 güne kadar genişletilebilen iki günlük verileri gösterecek şekilde ayarlanır. Bu, Tehdit Gezgini için de varsayılan görünümdür.  

- *Kötü amaçlı yazılım görünümü: Kötü* amaçlı yazılım tehdidinin tanımlandığı e-postaları gösterir. Bu, Gerçek zamanlı algılamalar için varsayılan görünümdür ve iki günlük verileri gösterir (30 güne genişletilebilir).  

- *Kimlik avı görünümü*: Kimlik avı tehdidinin tanımlandığı e-postaları gösterir.

- *İçerik kötü amaçlı yazılım görünümü*: OneDrive, SharePoint veya Teams aracılığıyla paylaşılan dosyalarda tanımlanan kötü amaçlı algılamaları gösterir. 

Bu deneyimlerdeki yaygın bileşenler şunlardır:

- Filtreler

    - E-posta veya dosya özniteliklerine göre verileri görüntülemek için çeşitli filtreleri kullanabilirsiniz.  

    - Varsayılan olarak, zaman filtresi kayıtlara uygulanır ve iki gün boyunca uygulanır.  

    - Birden çok filtre uyguluyorsanız, bunlar 'AND' modunda uygulanır ve gelişmiş filtreyi kullanarak 'OR' moduna değiştirebilirsiniz.  

    - Aynı filtre için birden çok değer eklemek için virgül kullanabilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin filtreleri](../../media/explorer-new-experience-filters.png)

- Grafikler

    - Grafikler, filtrelere göre verilerin görsel ve toplu bir görünümünü sağlar. Verileri farklı boyutlara göre görüntülemek için farklı filtreler kullanabilirsiniz.  

    > [!NOTE]
    > Liste görünümünde bir girdi görüyor olsanız bile grafik görünümünde hiçbir sonuç göremeyebilirsiniz. Filtre herhangi bir veri üretmezse bu durum ortaya çıkar. Örneğin, kötü amaçlı yazılım filtre ailesini uyguladıysanız ancak temel alınan verilerin kötü amaçlı e-postaları yoksa, bu senaryo için kullanılabilir veri yok iletisini görebilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin grafik görünümü](../../media/explorer-new-experience-export-chart-data.png)

- Sonuç kılavuzu  

    - Sonuçlar kılavuzu, uyguladığınız filtrelere göre e-posta sonuçlarını gösterir.  

    - Kiracınızdaki yapılandırma kümesine bağlı olarak veriler UTC veya yerel saat diliminde gösterilir ve ilk sütunda saat dilimi bilgileri bulunur.  

    - **Yeni pencerede aç** simgesine tıklayarak liste görünümünden tek tek e-posta varlığı sayfasına gidebilirsiniz. 

    - Ayrıca, görünümünüzü iyileştirmek için sütun eklemek veya kaldırmak için sütunlarınızı özelleştirebilirsiniz.

    > [!Note]
    > Sonuç kümenizi en üst düzeye çıkarmak için *Grafik Görünümü* ile *Liste Görünümü* arasında geçiş yapabilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin kılavuz görünümü](../../media/explorer-new-experience-list-chart-view.png)

- Ayrıntılı açılır öğe  

    - E-posta özet paneline (Konu sütunundaki girdiler), alıcıya veya IP açılır menüsüne ulaşmak için köprülere tıklayabilirsiniz.  

    - E-posta özeti paneli, eski e-posta açılır öğesinin yerini alır ve ayrıca e-posta varlık paneline erişmek için bir yol sağlar.  

    - IP, alıcı ve URL gibi tek tek varlık açılırları aynı bilgileri yansıtır, ancak tek bir sekme tabanlı görünümde sunulur ve gereksinime göre farklı bölümleri genişletme ve daraltma özelliği sunulur.  

    - URL'ler gibi açılır listelerde **Tüm E-postaları Görüntüle'ye** veya **Tüm Tıklamaları Görüntüle'ye** tıklayarak bu URL'yi içeren e-postaların/tıklamaların tamamını görüntüleyebilir ve sonuç kümesini dışarı aktarabilirsiniz.  

- Eylem

    - Tehdit Gezgini'nden *E-posta silme* gibi düzeltme eylemlerini tetikleyebilirsiniz. Düzeltme, düzeltme sınırları ve düzeltmeyi izleme hakkında daha fazla bilgi için bkz. [Kötü amaçlı e-postayı düzeltme](remediate-malicious-email-delivered-office-365.md).  

- Dışarı aktarma

    - Grafik ayrıntılarını dışarı aktarmak için **Grafik verilerini** dışarı aktar'a tıklayabilirsiniz. Benzer şekilde, e-posta ayrıntılarını dışarı aktarmak için **E-posta listesini** dışarı aktar'a tıklayın.

    - E-posta listesi için en fazla 200.000 kayıt dışarı aktarabilirsiniz. Ancak, daha iyi sistem performansı ve daha düşük indirme süresi için çeşitli e-posta filtreleri kullanmanız gerekir.

    > [!div class="mx-imgBorder"]
    > ![Grafik verilerini dışarı aktarma](../../media/explorer-new-experience-export-chart-data.png)

Bu özelliklere ek olarak *, Üst URL'ler*, *En çok tıklamalar*, *En çok hedeflenen kullanıcılar* ve *E-posta kaynağı* gibi güncelleştirilmiş deneyimler de elde edersiniz. *En çok kullanılan URL'ler*, *En çok tıklanan tıklamalar* ve *En çok hedeflenen kullanıcılar* , Gezgin'de uyguladığınız filtreye göre daha fazla filtrelenebilir. 

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Gezgin veya Gerçek zamanlı algılamalardan birini kullanmak için [Office 365 için Microsoft Defender](defender-for-office-365.md) sahip olmanız gerekir:

- Explorer yalnızca Office 365 için Defender Plan 2'ye dahildir.
- Gerçek zamanlı algılamalar raporu Office 365 için Defender Plan 1'e dahildir.

Güvenlik operasyonları ekiplerinin, Office 365 için Defender tarafından korunması gereken tüm kullanıcılara lisans ataması ve Gezgin ve Gerçek zamanlı algılamaların lisanslı kullanıcılar için algılama verilerini gösterdiğinin farkında olması gerekir.

Gezgin *veya* Gerçek zamanlı algılamaları görüntülemek ve kullanmak için aşağıdaki izinlere ihtiyacınız vardır:

- Office 365 için Defender içinde:
  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory yönetim merkezinde (<https://aad.portal.azure.com>) atanabilir
  - Güvenlik Okuyucusu
- Exchange Online:
  - Kuruluş Yönetimi
  - View-Only Kuruluş Yönetimi
  - alıcıları View-Only
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın:

- [Microsoft 365 Defender portalındaki izinler](permissions-microsoft-365-security-center.md)
- [Exchange Online'de izinler](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Daha fazla bilgi

- [Tehdit Gezgini, e-posta varlığı sayfasında e-posta ayrıntılarını toplar](mdo-email-entity-page.md)
- [Teslim edilen kötü amaçlı e-postayı bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'da algılanan kötü amaçlı dosyaları görüntüleme](mdo-for-spo-odb-and-teams.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Microsoft Tehdit Koruması'nda otomatik araştırma ve yanıt](automated-investigation-response-office.md)
