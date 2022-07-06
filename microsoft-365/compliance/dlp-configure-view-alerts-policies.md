---
title: DLP ilkeleri için uyarıları yapılandırma ve görüntüleme
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
ms.openlocfilehash: 60d5188b9288b1e131e36e145f7abb98a34d5ead
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627657"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Veri kaybı önleme ilkeleri için uyarıları yapılandırma ve görüntüleme

Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleri, hassas öğelerin yanlışlıkla paylaşılmasını önlemek için koruyucu eylemler gerçekleştirebilir. Hassas bir öğe üzerinde eylem yapıldığında, DLP için uyarılar yapılandırılarak bildirim alabilirsiniz. Bu makalede, veri kaybı önleme (DLP) ilkelerinize bağlı zengin uyarı ilkelerinin nasıl tanımlanacağı gösterilmektedir. DLP ilke ihlallerine yönelik uyarıları, olayları ve ilişkili meta verileri görüntülemek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> yeni DLP uyarı yönetimi panosunu nasıl kullanacağınızı göreceksiniz.

## <a name="features"></a>Özellik

Aşağıdaki özellikler bunun bir parçasıdır:

-   **DLP uyarı yönetimi panosu**: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a>, bu pano aşağıdaki iş yüklerinde zorunlu kılınan DLP ilkelerine yönelik uyarıları gösterir:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Aygıtları
-   **Gelişmiş uyarı yapılandırma seçenekleri**: Bu seçenekler DLP ilkesi yazma akışının bir parçasıdır. Zengin uyarı yapılandırmaları oluşturmak için bunları kullanın. Olay sayısına veya sızdırılan verilerin boyutuna bağlı olarak tek olaylı bir uyarı veya toplu uyarı oluşturabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Başlamadan önce gerekli önkoşullara sahip olduğunuzdan emin olun:

-   DLP uyarıları yönetim panosu için lisanslama
-   Uyarı yapılandırma seçenekleri için lisanslama
-   Rolleri

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>DLP uyarı yönetimi panosu için lisanslama

Office 365 DLP için uygun tüm kiracılar yeni DLP uyarı yönetimi panosuna erişebilir. Başlamak için Exchange Online, SharePoint Online ve OneDrive İş için Office 365 DLP'ye uygun olmanız gerekir. Office 365 DLP'nin lisans gereksinimleri hakkında daha fazla bilgi için bkz[. Hangi lisanslar kullanıcının hizmetten yararlanma haklarını sağlar?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

[Teams DLP'ye uygun Olan Uç Nokta DLP](endpoint-dlp-learn-about.md) kullanan müşteriler, DLP uyarı yönetimi panosunda uç nokta DLP ilkesi uyarılarını ve Teams DLP ilkesi uyarılarını görür.[](dlp-microsoft-teams.md)

### <a name="licensing-for-alert-configuration-options"></a>Uyarı yapılandırma seçenekleri için lisanslama

- **Tek olaylı uyarı yapılandırması**: E1, F1 veya G1 aboneliği ya da E3 ya da G3 aboneliği olan kuruluşlar, yalnızca her etkinlik gerçekleştiğinde bir uyarının tetiklendiği durumlarda uyarı ilkeleri oluşturabilir.
- **Toplu uyarı yapılandırması**: Bir eşiğe göre toplu uyarı ilkelerini yapılandırmak için aşağıdaki yapılandırmalardan herhangi birini kullanmanız gerekir:
  - E5 veya G5 aboneliği
  - Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Gelişmiş Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 eKeşif ve Denetim eklenti lisansı

### <a name="roles"></a>Rolleri

DLP uyarı yönetimi panosunu görüntülemek veya bir DLP ilkesindeki uyarı yapılandırma seçeneklerini düzenlemek istiyorsanız, şu rol gruplarından birinin üyesi olmanız gerekir:

-   Uyumluluk Yöneticisi
-   Uyumluluk Verileri Yöneticisi
-   Güvenlik Yöneticisi
-   Güvenlik İşleci
-   Güvenlik Okuyucusu

DLP uyarı yönetimi panosuna erişmek için Uyarıları yönet rolüne ve aşağıdaki rollerden birini kullanmanız gerekir:

-   DLP Uyumluluk Yönetimi
-   View-Only DLP Uyumluluk Yönetimi

## <a name="alert-configuration-experience"></a>Uyarı yapılandırma deneyimi

[Toplu uyarı yapılandırma seçenekleri](#licensing-for-alert-configuration-options) için uygunsanız DLP ilkesi yazma deneyiminde aşağıdaki seçenekleri satır içinde görürsünüz.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Toplu uyarı yapılandırma seçenekleri için uygun kullanıcılar için olay raporları seçeneklerini gösteren ekran görüntüsü." border="false":::

Bu yapılandırma uyarı oluşturmak için bir ilke ayarlamanıza olanak tanır:

- bir etkinlik ilke koşullarıyla her eşleştiğinde
- tanımlanan eşik karşılandığında veya aşıldığında
- etkinlik sayısına bağlı olarak
- dışarı sızan verilerin hacmine bağlı olarak

Bildirim e-postalarının taşmasını önlemek için, bir dakikalık bir zaman penceresinde gerçekleşen ve aynı DLP kuralına yönelik olan ve aynı konumdaki tüm eşleşmeler aynı uyarıda birlikte gruplandırılır. Bir dakikalık toplama süresi penceresi özelliği şu durumlarda kullanılabilir: 

- E5 veya G5 aboneliği
- Aşağıdaki özelliklerden birini içeren bir E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği:
    - Office 365 Gelişmiş Tehdit Koruması Planı 2
    - Microsoft 365 E5 Uyumluluk
    - Microsoft 365 eKeşif ve Denetim eklenti lisansı
 
E1, F1 veya G1 aboneliği ya da E3 veya G3 aboneliği olan kuruluşlar için toplama süresi 15 dakikadır.

## <a name="dlp-alert-management-dashboard"></a>DLP uyarı yönetimi panosu

DLP uyarı yönetimi panosuyla çalışmak için:

1.  <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> **Veri Kaybı Önleme'ye** gidin.

2.  DLP **uyarıları** panosunu görüntülemek için Uyarılar sekmesini seçin.

    -   Uyarı listesini daraltmak için filtreleri seçin. Görmek istediğiniz özellikleri listelemek için **Sütunları özelleştir'i** seçin. Ayrıca, uyarıları herhangi bir sütunda artan veya azalan düzende sıralamayı da seçebilirsiniz.
    -   Ayrıntıları görmek için bir uyarı seçin:

        :::image type="content" source="../media/alert-details.png" alt-text="DLP uyarı yönetimi panosundaki uyarı ayrıntılarını gösteren ekran görüntüsü." border="false":::

1.  Uyarıyla ilişkili tüm olayları görüntülemek için **Olaylar** sekmesini seçin. Ayrıntılarını görüntülemek için belirli bir olayı seçebilirsiniz. Aşağıdaki tabloda olay ayrıntılarından bazıları gösterilmektedir.
    
    | Kategori          | Özellik adı                 | Açıklama                                                                | Geçerli olay türleri                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Olay ayrıntıları*||
    |      | Kimlik                            | Olayla ilişkilendirilmiş benzersiz kimlik                                        | Tüm olaylar                               |
    |                   | Konum                      | Olayın algılandığı iş yükü                                      | Tüm olaylar                               |
    |                   | Etkinlik zamanı              | DLP ihlaline neden olan kullanıcı etkinliğinin zamanı                    | Tüm olaylar                               |
    |*Etkilenen varlıklar*||
    |  | Kullanıcı                          | DLP ihlaline neden olan kullanıcı                                          | Tüm olaylar                               |
    |                   | Ana bilgisayar adı                      | DLP ihlalinin algılandığı makinenin ana bilgisayar adı              | Cihaz olayları                           |
    |                   | IP adresi                    | Makinenin IP adresi                                                  | Cihaz olayları                           |
    |                   | Dosya yolu                     | İhlale katılan dosyanın mutlak yolu                        | SharePoint, OneDrive ve Cihazlar olayları |
    |                   | E-posta alıcıları              | DLP ilkesini ihlal eden e-postanın alıcıları                       | Exchange olayları                          |
    |                   | E-posta konusu                 | DLP ilkesini ihlal eden e-postanın konusu                          | Exchange olayları                          |
    |                   | E-posta ekleri             | E-postadaki DLP ilkesini ihlal eden eklerin adları         | Exchange olayları                          |
    |                   | Site sahibi                    | Site sahibinin adı                                                     | SharePoint ve OneDrive olayları           |
    |                   | Site URL'si                      | SharePoint veya OneDrive sitesinin tam URL'si                                | SharePoint ve OneDrive olayları           |
    |                   | Dosya oluşturuldu                  | Dosya oluşturma zamanı                                                      | SharePoint ve OneDrive olayları           |
    |                   | Dosya son değiştirildi            | Dosyanın son değiştirilme zamanı                                  | SharePoint ve OneDrive olayları           |
    |                   | Dosya boyutu                     | Dosyanın boyutu                                                           | SharePoint ve OneDrive olayları           |
    |                   | Dosya sahibi                    | Dosyanın sahibi                                                          | SharePoint ve OneDrive olayları           |
    |*İlke ayrıntıları*||
    |     | DLP ilkesi eşleştirildi            | Eşleşen DLP ilkesinin adı                                    | Tüm olaylar                               |
    |                   | Kural eşleştirildi                  | DLP ilkesinde eşleşen DLP kuralının adı                    | Tüm olaylar                               |
    |                   | Hassas bilgi türleri algılandı | DLP ilkesinin bir parçası olarak algılanan hassas bilgi türleri | Tüm olaylar                               |
    |                   | Gerçekleştirilen eylemler                 | Eşleşen DLP ilkesinin bir parçası olarak gerçekleştirilen eylemler                          | Tüm olaylar                               |
    |                   | Kullanıcı overrode ilkesi          | Kullanıcının ilke ipucu aracılığıyla ilkeyi aşırı kullanıp kullanmayacağı                | Tüm olaylar                               |
    |                   | Gerekçe metnini geçersiz kılma   | İlke ipucunu geçersiz kılmak için sağlanan gerekçe                          | Tüm olaylar                               |
    
1.  İçerikte algılanan hassas bilgi türleri hakkındaki ayrıntıları görüntülemek için **Hassas Bilgi Türleri** sekmesini seçin. Ayrıntılar arasında güvenilirlik ve sayı yer alır.

2.  Uyarıyı araştırdıktan sonra, durumu değiştirmek için **Uyarıyı yönet'i** seçin (**Etkin**, **Araştırılıyor**, **Kapatıldı** veya **Çözümlendi**). Ayrıca açıklamalar ekleyebilir ve uyarıyı kuruluşunuzdaki birine atayabilirsiniz.

    -   İş akışı yönetiminin geçmişini görmek için **Yönetim günlüğü'nü** seçin.
    -   Uyarı için gerekli eylemi gerçekleştirdikten sonra uyarının durumunu **Çözüldü** olarak ayarlayın.
