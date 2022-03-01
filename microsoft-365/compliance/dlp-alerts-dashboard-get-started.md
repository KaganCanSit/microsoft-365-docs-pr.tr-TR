---
title: Veri kaybı önleme uyarı panosuna başlama
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
description: Veri kaybı önleme ilkeleri için uyarıları tanımlama ve yönetmeye başlama.
ms.openlocfilehash: d295a04c27231b937ca552feb06628f857528e34
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010190"
---
# <a name="get-started-with-the-data-loss-prevention-alert-dashboard"></a>Veri kaybı önleme uyarı panosuna başlama

Veri kaybı önleme (DLP) ilkeleri, hassas öğelerinintersiz olarak paylaşımını önlemek için koruyucu işlemler gerçekleştirebilirsiniz. Hassas bir öğe üzerinde eyleme geç olduğunda, DLP için uyarılar yapılandırarak size bildirebilirsiniz. Bu makalede, veri kaybı önleme (DLP) ilkelerinize bağlı zengin uyarı ilkelerinin nasıl tanımladığınıza bakın. DLP ilkesi ihlallerine yönelik uyarıları, olayları ve ilişkili <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">meta Microsoft 365 uyumluluk merkezi</a> görüntülemek için [DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) uyarı yönetim panosunun nasıl kullanıla olacağını görebilirsiniz.

DLP uyarılarını yeni başlattıysanız, Veri kaybı önleme uyarıları [panosu hakkında bilgi edin'i gözden geçirebilirsiniz](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Başlamadan önce

Başlamadan önce, gerekli önkoşullara sahip olduğundan emin olun:

-   DLP uyarıları yönetim panosu için lisanslama
-   Uyarı yapılandırma seçenekleri için lisanslama
-   Roller

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>DLP uyarı yönetim panosu için lisanslama

DLP için tüm uygun Office 365 DLP uyarı yönetim panosuna erişim sağlar. Bu nedenle, Exchange Online, SharePoint Online ve Office 365 DLP OneDrive İş. OFFICE 365 DLP lisans gereksinimleri hakkında daha fazla bilgi için bkz. Hangi lisanslar kullanıcının hizmetten [yararlanması için hak sağlar?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Uç Nokta [DLP'sini](endpoint-dlp-learn-about.md) kullanan ve [Teams DLP](dlp-microsoft-teams.md) için uygun olan müşteriler, uç nokta DLP ilkesi uyarılarını ve DLP uyarı yönetim panosunda Teams DLP ilkesi uyarılarını görebilirler.

İçerik **önizleme** özelliği yalnızca şu lisanslarda kullanılabilir:

- Microsoft 365 (E5)
- Office 365 (E5)
- Gelişmiş Uyumluluk (E5) ekleme
- Microsoft 365 E5/A5 Bilgi Koruması ve Yönetimi
- Microsoft 365 E5/A5 Uyumluluğu

### <a name="licensing-for-alert-configuration-options"></a>Uyarı yapılandırma seçenekleri için lisanslama

**Tek olaylı** uyarı yapılandırması: E1, F1 veya G1 aboneliğine ya da E3 ya da G3 aboneliğine sahip kuruluşlar yalnızca her etkinlik oluştuğunda uyarının tetiklendiğinde uyarı ilkeleri oluşturabilir.

**Toplanan uyarı yapılandırması**: Toplam uyarı ilkelerini bir eşiğe göre yapılandırmak için, şu lisans yapılandırmalarından biri gerekir:

- E5 veya G5 aboneliği
- Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 Bulma ve Denetim eklenti lisansı ekleme

### <a name="roles"></a>Roller

DLP uyarı yönetim panosuni görüntülemek veya DLP ilkesinde uyarı yapılandırma seçeneklerini düzenlemek için, şu rol gruplarından birinin üyesi olun:

- Uyumluluk Yöneticisi
- Uyumluluk Veri Yöneticisi
- Güvenlik Yöneticisi
- Güvenlik İşleci
- Güvenlik Okuyucu

DLP uyarı yönetim panosuna erişmek için gerekenler:

- Uyarıları yönetme

ve şu iki rolden birini:

- DLP Uyumluluk Yönetimi
- View-Only DLP Uyumluluk Yönetimi

İçerik önizleme özelliğine ve Eşleşmeye duyarlı içerik ve bağlam özelliklerine erişmek için şunlara üye olmak gerekir:

- İçerik Gezgini İçerik Görüntüleyicisi rol grubu

önceden atanmış veri sınıflandırma içerik görüntüleyicisi rolüne sahip.

### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için deney erişiminiz olan roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Bu gruplar hakkında daha fazla bilgi [edinmek için Güvenlik ve Uyumluluk Merkezi'nde & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

## <a name="dlp-alert-configuration"></a>DLP uyarı yapılandırması

DLP ilkeniz için uyarı yapılandırmayı öğrenmek için bkz. Veri kaybı [önleme ile başlama](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Kuruluşların denetim günlüğü bekletme ilkesi yapılandırması, bir uyarının konsolda ne kadar süreyle görünür durumda tutularak görüle devam elerler. Daha fazla [bilgi için bkz. Denetim günlüğü bekletme](audit-log-retention-policies.md#manage-audit-log-retention-policies) ilkelerini yönetme.

### <a name="aggregate-event-alert-configuration"></a>Olay uyarı yapılandırmasını toplama

Toplu uyarı yapılandırma [seçenekleri için](#licensing-for-alert-configuration-options) lisansınız varsa, bir DLP ilkesi oluşturmak veya düzenlemek için bu seçenekleri kullanabilirsiniz.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Toplanan uyarı yapılandırma seçeneklerine uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

Bu yapılandırma, etkinlik ilkesi koşullarıyla her eş olduğunda veya etkinliklerin sayısına ya da içeri aktarılmış veri hacmine bağlı olarak belirli bir eşiğin aşılmış olduğu durumlarda uyarı oluşturmak için bir ilke ayarlamaya olanak sağlar.

### <a name="single-event-alert-configuration"></a>Tek olay uyarısı yapılandırması

DLP ilkesi oluşturmak veya [düzenlemek](#licensing-for-alert-configuration-options) için tek etkinlikli uyarı yapılandırma seçenekleri için lisansınız varsa bu seçenekleri de kullanabilirsiniz. Bir DLP kuralı her eşleşmesi olduğunda yükseltilmiş bir uyarı oluşturmak için bu seçeneği kullanın.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Tek etkinlikli uyarı yapılandırma seçeneklerine uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

## <a name="investigate-a-dlp-alert"></a>DLP uyarılarını araştırma

DLP uyarı yönetim panosuyla çalışmak için:

1. Aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi Kaybı</a> **Önleme'ye gidin**.
2. DLP **uyarıları panosuna** görüntülemek için Uyarılar sekmesini seçin.
3. Ayrıntıları görmek için bir uyarı seçin:

:::image type="content" source="../media/alert-details.png" alt-text="DLP uyarı yönetim panosunda uyarı ayrıntılarını gösteren ekran görüntüsü." border="false":::

4. Uyarıyla  ilişkili tüm olayları görüntülemek için Olaylar sekmesini seçin. Ayrıntılarını görüntülemek için belirli bir etkinliği seçebilirsiniz. Kullanılabilir olay ayrıntılarından bazılarının listesi için bkz. Veri kaybı önleme Uyarılar [panosu hakkında bilgi.](dlp-alerts-dashboard-learn.md)
5. **Uyarının** Genel Bakış **sayfasını açmak için** Ayrıntılar'ı seçin. Genel bakış sayfası bir özet sağlar:
    1. /ne olduğunu
    1. ilkenin eşleşmesına neden olan eylemleri kim gerçekleştirecek?
    1. eşleşmeye neden olan ilke ve daha fazlası hakkında bilgi 

6. Aşağıdakilere **erişmek** için Etkinlikler sekmesini seçin:
    1. ilgili içerik
    1. ile eşan hassas bilgi türleri
    1. meta veri

7. İçerikte **algılanan hassas bilgi** türleriyle ilgili ayrıntıları görüntülemek için Hassas Bilgi Türleri sekmesini seçin. Ayrıntılar güven, sayım ve hassas bilgi türüyle eşleşen içeriği içerir.

8. Uyarıyı araştırdikten sonra, öncelik yönetimi  ve uyarının yok olan yerini yönetebilirsiniz ve açıklamalar ekleyebilirsiniz.

- İş akışı yönetiminin geçmişini görmek için Yönetim **günlüğü'ne seçin**.
- Uyarı için gerekli eylemi verdikten sonra, uyarının durumunu Çözümlendi olarak **ayarlayın**.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kaybı önleme uyarıları ve uyarılar panosu hakkında bilgi](dlp-alerts-dashboard-learn.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
