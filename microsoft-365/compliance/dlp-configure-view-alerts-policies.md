---
title: Veri kaybı önleme ilkeleri için uyarıları yapılandırma ve görüntüleme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Veri kaybı önleme ilkeleri için uyarıları tanımlamayı ve yönetmeyi öğrenin.
ms.openlocfilehash: 9b8ee897502f76dbdb63e3fbac99e4223f378a1a
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018868"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Veri kaybı önleme uyarıları için uyarıları yapılandırma ve görüntüleme

Veri kaybı önleme (DLP) ilkeleri, hassas öğelerinintersiz olarak paylaşımını önlemek için koruyucu işlemler gerçekleştirebilirsiniz. Hassas bir öğe üzerinde eyleme geç olduğunda, DLP için uyarılar yapılandırarak size bildirebilirsiniz. Bu makalede, veri kaybı önleme (DLP) ilkelerinize bağlı zengin uyarı ilkelerinin nasıl tanımladığınıza bakın. DLP ilkesi ihlallerine yönelik uyarıları, olayları ve ilişkili <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">meta verileri görüntülemek</a> için Microsoft 365 uyumluluk merkezi DLP uyarı yönetim panosunun nasıl kullanıla olacağını görürsünüz.

## <a name="features"></a>Özellikler

Aşağıdaki özellikler bunun bir bölümünü içerir:

-   **DLP uyarı yönetimi panosu**: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>, bu pano aşağıdaki iş yüklerinde zorunlu kılınan DLP ilkelerine yönelik uyarıları gösterir:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Cihazlar
-   **Gelişmiş uyarı yapılandırma seçenekleri**: Bu seçenekler DLP ilkesi yazma akışının bir parçasıtır. Zengin uyarı yapılandırmaları oluşturmak için bu yapılandırmaları kullanın. Sızdırılan verilerin sayısına veya boyutuna bağlı olarak tek etkinlikli uyarı veya toplu uyarı oluşturabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Başlamadan önce, gerekli önkoşullara sahip olduğundan emin olun:

-   DLP uyarıları yönetim panosu için lisanslama
-   Uyarı yapılandırma seçenekleri için lisanslama
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>DLP uyarı yönetim panosu için lisanslama

DLP için tüm uygun Office 365 DLP uyarı yönetim panosuna erişim sağlar. Bu nedenle, Exchange Online, SharePoint Online ve Office 365 DLP OneDrive İş. OFFICE 365 DLP lisans gereksinimleri hakkında daha fazla bilgi için bkz. Hangi lisanslar kullanıcının hizmetten [yararlanması için hak sağlar?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Uç Nokta [DLP'sini](endpoint-dlp-learn-about.md) kullanan ve [Teams DLP](dlp-microsoft-teams.md) için uygun olan müşteriler, uç nokta DLP ilkesi uyarılarını ve DLP uyarı yönetim panosunda Teams DLP ilkesi uyarılarını görebilirler.

### <a name="licensing-for-alert-configuration-options"></a>Uyarı yapılandırma seçenekleri için lisanslama

- **Tek olaylı** uyarı yapılandırması: E1, F1 veya G1 aboneliğine ya da E3 ya da G3 aboneliğine sahip kuruluşlar yalnızca her etkinlik oluştuğunda uyarının tetiklendiğinde uyarı ilkeleri oluşturabilir.
- **Toplanan uyarı yapılandırması**: Bir eşik tabanlı toplam uyarı ilkelerini yapılandırmak için, aşağıdaki yapılandırmalardan birini kullanabilirsiniz:
  - E5 veya G5 aboneliği
  - Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 Bulma ve Denetim eklenti lisansı ekleme

### <a name="roles"></a>Roller

DLP uyarı yönetim panosuni görüntülemek veya DLP ilkesinde uyarı yapılandırma seçeneklerini düzenlemek için, şu rol gruplarından birinin üyesi olun:

-   Uyumluluk Yöneticisi
-   Uyumluluk Veri Yöneticisi
-   Güvenlik Yöneticisi
-   Güvenlik İşleci
-   Güvenlik Okuyucu

DLP uyarı yönetimi panosuna erişmek için, Uyarılar rolünü ve aşağıdaki rollerden birini yönetmeniz gerekir:

-   DLP Uyumluluk Yönetimi
-   View-Only DLP Uyumluluk Yönetimi

## <a name="alert-configuration-experience"></a>Uyarı yapılandırma deneyimi

Toplu uyarı yapılandırma seçeneklerine uygunsanız [,](#licensing-for-alert-configuration-options) DLP ilkesi yazma deneyiminde aşağıdaki seçenekleri satır içinde görüyorsunuz.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Toplanan uyarı yapılandırma seçeneklerine uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

Bu yapılandırma, uyarı oluşturmak için bir ilke ayarlamaya olanak sağlar:

- bir etkinliğin ilke koşullarıyla her eşleşmesi
- tanımlı eşik karşılandığı veya aşılırken
- etkinliklerin sayısına göre
- exfiltrated verilerin hacmine bağlı olarak

Bildirim e-postalarının akınını önlemek için, bir dakikalık bir pencere içinde oluşan ve aynı DLP kuralına yönelik olan tüm eşleşmeler, aynı uyarıda birlikte gruptur. Bir dakika toplama zaman penceresi özelliği şularda kullanılabilir: 

- E5 veya G5 aboneliği
- Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 Bulma ve Denetim eklenti lisansı ekleme
 
E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği olan kuruluşlar için toplama süresi penceresi 15 dakikadır.

## <a name="dlp-alert-management-dashboard"></a>DLP uyarı yönetim panosu

DLP uyarı yönetim panosuyla çalışmak için:

1.  Aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi Kaybı</a> **Önleme'ye gidin**.

2.  DLP **uyarıları panosuna** görüntülemek için Uyarılar sekmesini seçin.

    -   Uyarı listesini iyileştirmek için filtreleri seçin. Görmek **istediğiniz özellikleri** liste için Sütunları özelleştir'i seçin. Ayrıca, uyarıları herhangi bir sütunda artan veya azalan düzende sıralamayı da seçebilirsiniz.
    -   Ayrıntıları görmek için bir uyarı seçin:

        :::image type="content" source="../media/alert-details.png" alt-text="DLP uyarı yönetim panosunda uyarı ayrıntılarını gösteren ekran görüntüsü." border="false":::

1.  Uyarıyla  ilişkili tüm olayları görüntülemek için Olaylar sekmesini seçin. Ayrıntılarını görüntülemek için belirli bir etkinliği seçebilirsiniz. Aşağıdaki tabloda olay ayrıntılarının bazıları yer alır.
    
    | Kategori          | Özellik adı                 | Açıklama                                                                | Geçerli olay türleri                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Olay ayrıntıları*||
    |      | Kimlik                            | Etkinlikle ilişkilendirilmiş benzersiz kimlik                                        | Tüm etkinlikler                               |
    |                   | Konum                      | Olayın algılandığında iş yükü                                      | Tüm etkinlikler                               |
    |                   | Etkinlik zamanı              | DLP ihlaline neden olan kullanıcı etkinliğinin zamanı                    | Tüm etkinlikler                               |
    |*Etkide olan varlıklar*||
    |  | Kullanıcı                          | DLP ihlaline neden olan kullanıcı                                          | Tüm etkinlikler                               |
    |                   | Ana bilgisayar adı                      | DLP ihlali algılandığında makinenin ana bilgisayar adı              | Cihazlar olayları                           |
    |                   | IP adresi                    | Makinenin IP adresi                                                  | Cihazlar olayları                           |
    |                   | Dosya yolu                     | İhlali olan dosyanın mutlak yolu                        | SharePoint, OneDrive ve Cihazlar olaylarını geri edin |
    |                   | E-posta alıcıları              | DLP ilkesi ihlal eden e-postanın alıcıları                       | Exchange etkinlikleri                          |
    |                   | E-posta konusu                 | DLP ilkesi ihlal eden e-postanın konusu                          | Exchange etkinlikleri                          |
    |                   | E-posta ekleri             | E-postada yer alan ve DLP İlkesini ihlal eden eklerin adları         | Exchange etkinlikleri                          |
    |                   | Site sahibi                    | Site sahibinin adı                                                     | SharePoint ve OneDrive hakkında           |
    |                   | Site URL'si                      | Sitenin veya sitenin SharePoint URL'si OneDrive URL'si                                | SharePoint ve OneDrive hakkında           |
    |                   | Dosya oluşturuldu                  | Dosya oluşturma zamanı                                                      | SharePoint ve OneDrive hakkında           |
    |                   | En son değiştirilen dosya            | Dosyada son değişiklik zamanı                                  | SharePoint ve OneDrive hakkında           |
    |                   | Dosya boyutu                     | Dosya boyutu                                                           | SharePoint ve OneDrive hakkında           |
    |                   | Dosya sahibi                    | Dosyanın sahibi                                                          | SharePoint ve OneDrive hakkında           |
    |*İlke ayrıntıları*||
    |     | DLP ilkesi eşleşmeli            | Eşleri olan DLP ilkesi adı                                    | Tüm etkinlikler                               |
    |                   | Eşanlı kural                  | DLP ilkesinde yer alan ve ile eşenen DLP kuralının adı                    | Tüm etkinlikler                               |
    |                   | Algılanan hassas bilgi türleri | DLP ilkesi kapsamında algılanan hassas bilgi türleri | Tüm etkinlikler                               |
    |                   | 2007'de                 | Eşanlı DLP ilkesi kapsamında  alınan eylemler                          | Tüm etkinlikler                               |
    |                   | Kullanıcı aşırı kullanıcı ilkesi          | Kullanıcının ilke ipucu aracılığıyla ilkeyi overrode edip edip olmadığı                | Tüm etkinlikler                               |
    |                   | Yaslama metnini geçersiz kılma   | İlke ipucu geçersiz kılınan gerekçelendirme                          | Tüm etkinlikler                               |
    
1.  İçerikte **algılanan hassas bilgi** türleriyle ilgili ayrıntıları görüntülemek için Hassas Bilgi Türleri sekmesini seçin. Ayrıntılar güven ve sayım içerir.

2.  Uyarıyı araştırtıktan sonra, **durumu değiştirmek için Uyarıyı** yönet'i seçin (**Etkin**, **Araştırılıyor**, **Yok,** **Çözüldü).** Ayrıca, açıklama ekleyebilir ve uyarıyı kuruluşta başka birine atamazsiniz.

    -   İş akışı yönetiminin geçmişini görmek için Yönetim **günlüğü'ne seçin**.
    -   Uyarı için gerekli eylemi verdikten sonra, uyarının durumunu Çözümlendi olarak **ayarlayın**.
