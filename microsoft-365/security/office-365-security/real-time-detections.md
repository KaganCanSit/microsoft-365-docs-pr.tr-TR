---
title: Tehdit Gezgini ve Gerçek zamanlı algılamalar Office 365 için Microsoft Defender'da temel Office 365
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
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için Gezgin'i veya Gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b889649de7b56d6a1b5300ff323850a4e555b57
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775378"
---
# <a name="explorer-and-real-time-detections"></a>Explorer ve Gerçek zamanlı algılamalar

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu makalede:

- [Gezgin ile Gerçek zamanlı algılamalar arasındaki farklar](#differences-between-explorer-and-real-time-detections)
- [Gezgin ve Gerçek zamanlı algılamalar için güncelleştirilmiş deneyim](#updated-experience-for-explorer-and-real-time-detections)
- [Gerekli lisanslar ve izinler](#required-licenses-and-permissions)

> [!NOTE]
> Bu, **Gezgin'de (Tehdit** Gezgini olarak da bilinir), **e-posta** güvenliği ve Explorer ile Gerçek zamanlı algılamalar (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) içeren **3** makalelik bir serinin bir bölümü. Bu dizide yer alan diğer iki makale de [Explorer'da](threat-hunting-in-threat-explorer.md) tehdit avı ve Explorer ile [E-posta güvenliğidir](email-security-in-microsoft-defender.md).

Bu makalede, Gezgin ile gerçek zamanlı algılamalar raporlaması, Explorer ile güncelleştirilmiş deneyim ve eski ve yeni deneyimler arasında geçiş yapmak için gereklen lisanslar ile izinler arasında geçiş farkları açıklanmıştır.

[Microsoft Defender for Office 365](defender-for-office-365.md) varsa ve izinlere sahipsiniz, tehditleri tespit etmek ve [](#required-licenses-and-permissions)düzeltmek için **Explorer'ı** (Tehdit Gezgini olarak da **bilinir) veya** Gerçek  zamanlı algılamaları kullanabilirsiniz.

aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>adresi & **gidin ve Gezgin'i** veya Gerçek  _zamanlı_ **algılamalar'ı seçin**. Doğrudan sayfaya gitmek için veya kullanın <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

Bu araçlarla şunlarıabilirsiniz:

- Güvenlik özellikleri tarafından algılanan kötü amaçlı Microsoft 365 bakın.
- Kimlik avı URL'sini görüntüden karar veri'ye tıklayın.
- Gezgin'de bir görünümden otomatik bir araştırma ve yanıt işlemi başlatın.
- Kötü amaçlı e-postaları ve daha fazlasını araştırabilirsiniz.

Daha fazla bilgi için bkz. [Explorer ile e-posta güvenliği](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Gezgin ile Gerçek zamanlı algılamalar arasındaki farklar

- *Gerçek zamanlı algılamalar,* plan 1 için Defender'da bulunan Office 365 aracıdır. *Threat Explorer*, Plan 2'ye yönelik Defender'da bulunan bir tehdit Office 365 aracıdır.
- Gerçek zamanlı algılamalar raporu, algılamaları gerçek zamanlı olarak görüntülemeye olanak sağlar. Threat Explorer bunu da yapar, ancak belirli bir saldırı için saldırı kampanyaları vurgulama gibi ek ayrıntılar sağlar ve güvenlik işlemleri ekiplerine tehditleri düzeltme (Otomatik Araştırma ve Yanıt soruşturmasını tetikleme dahil) olanağı [sağlar](automated-investigation-response-office.md).
- Threat *Explorer'da* Tüm e-posta görünümü kullanılabilir, ancak Gerçek zamanlı algılamalar raporuna dahil değildir.
- Zengin filtreleme özellikleri ve düzeltme eylemleri Threat Explorer'da yer almaktadır. Daha fazla bilgi için bkz. [Çevrimiçi Hizmet Office 365 için Microsoft Defender: Yeni planlar için Defender'da Office 365 kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Gezgin ve Gerçek zamanlı algılamalar için güncelleştirilmiş deneyim

Tehdit Gezgini ve Gerçek zamanlı algılamalar deneyimi, modern erişilebilirlik standartlarına uygun hale getirmek ve iş akışını iyileştirmek için güncelleştirilir. Kısa bir süre için, eski deneyimle yeni deneyim arasında geçişabileceksiniz.  

> [!NOTE]
> Bu toplama yalnızca kendi hesabınıza etkiler ve kiracınız içindeki diğer herkesi etkilemez. 

Tehdit Gezgini ve Gerçek zamanlı algılamalar aşağıdaki görünümlere ayrılır:

- *Tüm e-posta*: Office 365 için Defender tarafından analiz edilir ve hem iyi hem de kötü amaçlı e-postaları içerir. Bu özellik yalnızca Threat Explorer'da mevcuttur ve Gerçek zamanlı algılamalarda kullanılamaz. Varsayılan olarak, 30 gün'e kadar genişletilen iki günlük verileri gösterecek şekilde ayarlanmıştır. Tehdit Gezgini için de varsayılan görünüm bu olur.  

- *Kötü amaçlı yazılım* görünümü: Kötü amaçlı yazılım tehdidinin tanım olduğu e-postaları gösterir. Bu, Gerçek zamanlı algılamalar için varsayılan görünümdir ve iki günlük verileri gösterir (30 gün'e genişletilir).  

- *Kimlik avı görünümü*: Kimlik avı tehdidinin tanım olduğu e-postaları gösterir.

- *İçerik kötü amaçlı yazılım* görünümü: Paylaşılan dosyalarda kimlik ya da yazılım OneDrive SharePoint kötü amaçlı algılamaları Teams. 

Bu deneyimler içindeki yaygın bileşenler şu şekildedir:

- Filtreler

    - E-posta veya dosya özniteliklerine göre verileri görüntülemek için çeşitli filtreleri kullanabilirsiniz.  

    - Varsayılan olarak, zaman filtresi kayıtlara uygulanır ve iki gün süreyle uygulanır.  

    - Birden çok filtre uyguluyorsanız, bunlar 'VE' modunda uygulanır ve gelişmiş filtreyi 'VEYA' moduna değiştirmek için kullanabilirsiniz.  

    - Aynı filtre için birden çok değer eklemek üzere virgül kullanabilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin filtreleri](../../media/explorer-new-experience-filters.png)

- Grafikler

    - Grafikler, filtrelere dayalı olarak verilerin görsel, toplu bir görünümünü sağlar. Verileri farklı boyutlara göre görüntülemek için farklı filtreler kullanabilirsiniz.  

    > [!NOTE]
    > Liste görünümünde bir girdi görüyorsanız bile, grafik görünümünde hiç sonuç görenemebilirsiniz. Filtre herhangi bir veri üretmezse bu durum ortaya olur. Örneğin, kötü amaçlı yazılım ailenizi filtrele uyguladıysanız ama temel alınan veride hiç kötü amaçlı e-posta yoksa, bu senaryo için kullanılabilir veri olmadığını iletisiyle de alabilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin grafik görünümü](../../media/explorer-new-experience-export-chart-data.png)

- Sonuçlar kılavuzu  

    - Sonuçlar kılavuzu, uygulanan filtrelere göre e-posta sonuçlarını gösterir.  

    - Kiracıdaki yapılandırma kümesine bağlı olarak veriler UTC veya yerel saat diliminde gösterilir ve ilk sütunda saat dilimi bilgileri yer eder.  

    - Liste görünümünden, Yeni pencerede aç simgesine tıklayarak tek tek **e-posta varlık sayfasına ulaşabilirsiniz** . 

    - Görünümlerinizi iyileştirmek için sütunları ekp veya kaldırmak için de özelleştirebilirsiniz.

    > [!Note]
    > Sonuç kümenizi en üst düzeye *çıkarmak için Grafik* Görünümü *ile Liste Görünümü* arasında geçişabilirsiniz.  

    > [!div class="mx-imgBorder"]
    > ![Gezgin kılavuz görünümü](../../media/explorer-new-experience-list-chart-view.png)

- Ayrıntılı uçarak çıkış  

    - E-posta özet paneline (Konu sütunundaki girdiler), alıcı veya IP uç hakkında bilgi almak için köprülere tıkleyebilirsiniz.  

    - E-posta özeti paneli, eski e-posta uç şimdi çıkış yerini alır ve e-posta varlık paneline erişim yolu da sağlar.  

    - IP, alıcı ve URL gibi tek tek varlık açılır tüm bilgileri aynı bilgileri yansıtabilir, ancak gereksinime bağlı olarak farklı bölümleri genişletme ve daraltma özelliğiyle, sekme tabanlı görünümde sunabilirsiniz.  

    - URL'ler gibi dışarı aktarmalar için, bu URL'yi içeren e-posta/tıklamaların tamamını görüntülemek için Tüm E-postayı Görüntüle veya Tüm Tıklamaları Görüntüle'yi tıklatmanın yanı sıra sonuç kümesini de dışarı aktarabilirsiniz.   

- Eylemler

    - Tehdit Gezgini'nde, e-postayı silme gibi *düzeltme eylemlerini tetiklebilirsiniz*. Düzeltme, düzeltme sınırları ve düzeltmeyi izleme hakkında daha fazla bilgi için bkz. Kötü amaçlı [e-postaları düzeltme](remediate-malicious-email-delivered-office-365.md).  

- Dışarı aktarma

    - Grafik ayrıntılarını dışarı **aktar için Grafik verilerini dışarı** aktar'ı tıklatın. Benzer şekilde, e-posta **ayrıntılarını dışarı aktar için E-posta** listesini dışarı aktar'a tıklayın.

    - E-posta listesi için en çok 200.000 kaydı dışarı aktarabilirsiniz. Bununla birlikte, sistem performansının daha iyi olması ve indirme süresinin azalması için çeşitli e-posta filtrelerini kullansanız gerekir.

    > [!div class="mx-imgBorder"]
    > ![Grafik verilerini dışarı aktarma](../../media/explorer-new-experience-export-chart-data.png)

Bu özelliklere ek olarak, İlk URL'ler, En çok tıklamalar *, En* çok hedefli kullanıcılar ve E-posta kaynağı *gibi* güncelleştirilmiş deneyimleri *de edinebilirsiniz*. *En çok url'ler*, En çok  tıklar ve En çok hedefli kullanıcılar, Gezgin'de uygulamış olunan filtreye göre daha fazla filtre uygulanabilir.  

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Explorer veya [Gerçek zamanlı algılamaları Office 365](defender-for-office-365.md) için Microsoft Defender'a sahip olmak gerekir:

- Explorer, plan 2 için Defender'Office 365 dahil edilir.
- Gerçek zamanlı algılamalar raporu, Plan 1'den Office 365 Defender'a dahildir.

Güvenlik İşlemleri ekipleri, Güvenlik İşlemleri ekiplerinin Office 365 için Defender ile korunması gereken tüm kullanıcılar için lisans ataması ve Gezgin'in ve Gerçek zamanlı algılamaların lisanslı kullanıcılar için algılama verilerini göstereceklerini biliyor olması gerekir.

Gezgin'i veya Gerçek *zamanlı algılamaları* görüntülemek ve kullanmak için aşağıdaki izinlere ihtiyacınız vardır:

- Office 365 için Defender'da:
  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory merkezinden atanabilir)<https://aad.portal.azure.com>
  - Güvenlik Okuyucu
- Exchange Online:
  - Kuruluş Yönetimi
  - View-Only Yönetimi
  - View-Only'i seçin
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın:

- [Microsoft 365 Defender portalında izinler](permissions-microsoft-365-security-center.md)
- [Web'de Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Daha fazla bilgi

- [Threat Explorer e-posta varlık sayfasında e-posta ayrıntılarını toplar](mdo-email-entity-page.md)
- [Teslim edilen kötü amaçlı e-postaları bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'de algılanan kötü amaçlı dosyaları Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Microsoft Tehdit Koruması'da otomatik araştırma ve yanıt](automated-investigation-response-office.md)
