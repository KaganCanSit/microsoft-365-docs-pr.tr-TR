---
title: DLP Uyarıları panosunu kullanmaya başlama
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
description: Veri kaybı önleme ilkeleri için uyarıları tanımlamaya ve yönetmeye başlayın.
ms.openlocfilehash: de980fadbc6b6091a0257c032dacab4220704f62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625467"
---
# <a name="get-started-with-the-data-loss-prevention-alerts-dashboard"></a>Veri kaybı önleme Uyarıları panosunu kullanmaya başlama

Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleri, hassas öğelerin yanlışlıkla paylaşılmasını önlemek için koruyucu eylemler gerçekleştirebilir. Hassas bir öğe üzerinde eylem yapıldığında, DLP için uyarılar yapılandırılarak bildirim alabilirsiniz. Bu makalede, veri kaybı önleme (DLP) ilkelerinize bağlı zengin uyarı ilkelerinin nasıl tanımlanacağı gösterilmektedir. DLP ilke ihlallerine yönelik uyarıları, olayları ve ilişkili meta verileri görüntülemek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> DLP [uyarı yönetimi panosunu](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) nasıl kullanacağınızı göreceksiniz.

DLP uyarılarını yeni kullanıyorsanız [Veri kaybı önleme uyarıları panosu hakkında bilgi edinin sayfasını](dlp-alerts-dashboard-learn.md) gözden geçirmeniz gerekir

## <a name="before-you-begin"></a>Başlamadan önce

Başlamadan önce gerekli önkoşullara sahip olduğunuzdan emin olun:

-   DLP uyarıları yönetim panosu için lisanslama
-   Uyarı yapılandırma seçenekleri için lisanslama
-   Rolleri

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>DLP uyarı yönetimi panosu için lisanslama

DLP için uygun tüm kiracılar DLP uyarı yönetimi panosuna erişebilir. Başlamak için Exchange Online, SharePoint Online ve OneDrive İş için Microsoft Purview DLP'ye uygun olmanız gerekir. DLP'nin lisans gereksinimleri hakkında daha fazla bilgi için bkz [. Hangi lisanslar kullanıcının hizmetten yararlanma haklarını sağlar?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

[Teams DLP'ye uygun Olan Uç Nokta DLP](endpoint-dlp-learn-about.md) kullanan müşteriler, DLP uyarı yönetimi panosunda uç nokta DLP ilkesi uyarılarını ve Teams DLP ilkesi uyarılarını görür.[](dlp-microsoft-teams.md)

**İçerik önizleme** özelliği yalnızca şu lisanslar için kullanılabilir:

- Microsoft 365 (E5)
- Office 365 (E5)
- Gelişmiş Uyumluluk (E5) eklentisi
- Microsoft 365 E5/A5 Information Protection ve İdare
- Microsoft 365 E5/A5 Uyumluluğu

### <a name="licensing-for-alert-configuration-options"></a>Uyarı yapılandırma seçenekleri için lisanslama

**Tek olaylı uyarı yapılandırması**: E1, F1 veya G1 aboneliği ya da E3 ya da G3 aboneliği olan kuruluşlar, yalnızca her etkinlik gerçekleştiğinde bir uyarının tetiklendiği durumlarda uyarı ilkeleri oluşturabilir.

**Toplu uyarı yapılandırması**: Toplu uyarı ilkelerini bir eşiğe göre yapılandırmak için şu lisans yapılandırmalarından birini kullanmanız gerekir:

- E5 veya G5 aboneliği
- Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Gelişmiş Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 eKeşif ve Denetim eklenti lisansı

### <a name="roles"></a>Rolleri

DLP uyarı yönetimi panosunu görüntülemek veya bir DLP ilkesindeki uyarı yapılandırma seçeneklerini düzenlemek istiyorsanız, şu rol gruplarından birinin üyesi olmanız gerekir:

- Uyumluluk Yöneticisi
- Uyumluluk Verileri Yöneticisi
- Güvenlik Yöneticisi
- Güvenlik İşleci
- Güvenlik Okuyucusu

DLP uyarı yönetimi panosuna erişmek için şunlar gerekir:

- Uyarıları yönetin

ve bu iki rolden biri:

- DLP Uyumluluk Yönetimi
- View-Only DLP Uyumluluk Yönetimi

İçerik önizleme özelliğine ve Eşleştirilen hassas içeriğe ve bağlam özelliklerine erişmek için şunlara üye olmanız gerekir:

- İçerik Gezgini İçerik Görüntüleyicisi rol grubu

veri sınıflandırması içerik görüntüleyici rolü önceden atanmıştır.

### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinizde ince ayar yapmak için test yapabileceğiniz roller ve rol grupları vardır.

Aşağıda, önizleme aşamasında olan geçerli rollerin listesi yer alır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Roller](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Yönetici
- Information Protection Analisti
- Information Protection Araştırmacısı
- Information Protection Okuyucu

Aşağıda, önizleme aşamasında olan geçerli rol gruplarının listesi yer alır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Rol grupları](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection Yöneticileri
- Information Protection Analistleri
- Information Protection Araştırmacıları
- Information Protection Okuyucular

## <a name="dlp-alert-configuration"></a>DLP uyarı yapılandırması

DLP ilkenizde uyarı yapılandırmayı öğrenmek için bkz. [Veri kaybı önleme ile nereden başlayacağınız](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Kuruluşunuz denetim günlüğü saklama ilkesi yapılandırması, bir uyarının konsolunda ne kadar süre görünür kalacağını denetler. Daha fazla bilgi için bkz. [Denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md#manage-audit-log-retention-policies) .

### <a name="aggregate-event-alert-configuration"></a>Olay uyarısı yapılandırmasını toplama

Kuruluşunuz [toplu uyarı yapılandırma seçenekleri](#licensing-for-alert-configuration-options) için lisanslanmışsa, bir DLP ilkesi oluştururken veya düzenlerken bu seçenekleri görürsünüz.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Toplu uyarı yapılandırma seçenekleri için uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

Bu yapılandırma, bir etkinliğin ilke koşullarıyla her eşleştiğinde veya etkinliklerin sayısına veya dışarı aktarılan verilerin hacmine bağlı olarak belirli bir eşiğin aşılması durumunda uyarı oluşturmak için bir ilke ayarlamanıza olanak tanır.

### <a name="single-event-alert-configuration"></a>Tek olay uyarısı yapılandırması

Kuruluşunuz [tek olaylı uyarı yapılandırma seçenekleri](#licensing-for-alert-configuration-options) için lisanslıysa, DLP ilkesi oluştururken veya düzenlerken bu seçenekleri görürsünüz. DLP kuralı eşleşmesi her gerçekleştiğinde tetiklenen bir uyarı oluşturmak için bu seçeneği kullanın.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Tek olay uyarısı yapılandırma seçenekleri için uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

## <a name="investigate-a-dlp-alert"></a>DLP uyarısını araştırma

DLP uyarı yönetimi panosuyla çalışmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> **Veri kaybı önleme** bölümüne gidin.
2. DLP **uyarıları** panosunu görüntülemek için Uyarılar sekmesini seçin.
3. Ayrıntıları görmek için bir uyarı seçin:

:::image type="content" source="../media/alert-details.png" alt-text="DLP uyarı yönetimi panosundaki uyarı ayrıntılarını gösteren ekran görüntüsü." border="false":::

4. Uyarıyla ilişkili tüm olayları görüntülemek için **Olaylar** sekmesini seçin. Ayrıntılarını görüntülemek için belirli bir olayı seçebilirsiniz. Kullanılabilir olay ayrıntılarından bazılarının listesi için bkz. [Veri kaybı önleme Uyarıları panosu hakkında bilgi edinin](dlp-alerts-dashboard-learn.md).
5. **Uyarının** **Genel Bakış** sayfasını açmak için Ayrıntılar'ı seçin. Genel bakış sayfası bir özet sağlar:
    1. ne olduğunu
    1. İlke eşleşmesine neden olan eylemleri gerçekleştiren kişi
    1. eşleşen ilke hakkında bilgi ve daha fazlası 

6. **Aşağıdakilere** erişmek için Olaylar sekmesini seçin:
    1. dahil olan içerik
    1. hassas bilgi türleri eşleştirildi
    1. Meta veri

7. İçerikte algılanan hassas bilgi türleri hakkındaki ayrıntıları görüntülemek için **Hassas Bilgi Türleri** sekmesini seçin. Ayrıntılar arasında güvenilirlik, sayı ve hassas bilgi türüyle eşleşen içerik yer alır.

8. Uyarıyı araştırdıktan sonra, önceliklendirmeyi yönetebileceğiniz, uyarının eğilimini yönetebileceğiniz ve açıklama ekleyebileceğiniz **Genel Bakış** sekmesine dönün.

- İş akışı yönetiminin geçmişini görmek için **Yönetim günlüğü'nü** seçin.
- Uyarı için gerekli eylemi gerçekleştirdikten sonra uyarının durumunu **Çözüldü** olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kaybı önleme uyarıları ve uyarılar panosu hakkında bilgi edinin](dlp-alerts-dashboard-learn.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
