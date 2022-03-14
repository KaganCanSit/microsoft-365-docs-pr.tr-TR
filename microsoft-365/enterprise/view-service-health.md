---
title: Hizmet durumunu Microsoft 365 denetleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Etkin bir hizmet kesintisi Microsoft 365 için desteği aramadan önce hizmetlerin durumunu görüntüdenin.
ms.openlocfilehash: 4a72132872c890f755cb537e06c42412aa17fb9f
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468782"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Hizmet durumunu Microsoft 365 denetleme

[![Yönetim merkezinin değiştiğini size bildirmeye yarayan etiket ve daha fazla ayrıntıyı aka.ms/aboutM365preview sayfasında bulabilirsiniz.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Microsoft hizmetleri, Yammer, Web üzerinde Office Microsoft Dynamics CRM ve mobil cihaz yönetimi bulut hizmetleri dahil olmak üzere Microsoft hizmetleri hizmet durumunu, [ Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

Yönetim merkezinde oturum açamıyorsanız, hizmet durumu sayfasını kullanarak kiracıda oturum açmanızı [](https://status.office365.com) engelleyen bilinen sorunları görebilirsiniz.  Belirli etkinliklerle ilgili bilgileri görmek için [@MSFT365status](https://twitter.com/MSFT365Status) Twitter'da bizi takip etmek için de kaydolabilirsiniz.

## <a name="how-to-check-service-health"></a>Hizmet durumunu denetleme

1. Microsoft 365 yönetim merkezi 'a gidin [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)ve bir yönetici hesabıyla oturum açın.

    > [!NOTE]
    > Genel yönetici veya hizmet desteği yöneticisi rolüne atanan kişiler hizmet durumunu  bakabilir. Exchange, SharePoint ve Skype Kurumsal yöneticilerinin hizmet durumunu görüntülemesine izin vermek için, bunların Hizmet yöneticisi rolüne de atanmaları gerekir. Hizmet durumunu görüntüley gören roller hakkında daha fazla bilgi için bkz [. Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Hizmet durumunu görüntülemek için, yönetim merkezinin sol gezintisinde  **HealthService** >  **health** seçeneğine gidin veya Giriş panosunda Hizmet durumu **kartını seçin**. Pano kartı etkin bir hizmet sorunu olup olmadığını gösterir ve ayrıntılı Hizmet durumu **sayfasının bağlantılarını** sağlar.

3. Hizmet **durumu sayfasında** , her bulut hizmetinin durumu tablo biçiminde gösterilir.

   ![Hizmet durumundaki geçerli sorunların görünümü.](../media/shd-landing-page.png)

Tüm **hizmetler sekmesi** (varsayılan görünüm), tüm hizmetleri, geçerli durumlarını ve tüm etkin olayları veya tavsiyeleri gösterir. Her hizmetin durumunu Durum **sütunundaki** bir simge ve durum gösterir.

Etkin bir hizmetle ilgili bir olay veya danışma varsa, bunlar doğrudan iç içe geçmiş tabloda hizmet adının altında listelenir. Hizmet adının sol köşesindeki köşeli çift ayraç simgesine tıklayarak, bu görünümde olayları veya tavsiyeleri gizlemek için iç içe tabloyu daraltabilirsiniz.

Görünüme filtre kullanarak yalnızca tüm etkin olayları görüntülemek için **sayfanın en üstünde** Olaylar sekmesini seçin. Danışmanlar **sekmesine seçerek** yalnızca gönderilen tüm etkin danışmanlar görüntülenir.

Geçmiş **sekmesi** , son yedi veya 30 gün içinde çözülen tüm olayları ve tavsiyeleri gösterir.

Bir Microsoft 365 hizmetiyle ilgili bir sorun yaşıyorsanız ve Bu hizmetin Hizmet durumu sayfasında listelenmiyorsa, Sorun bildir'i seçerek ve  kısa formu tamamlayarak bu sorun hakkında bize bilgi edin. Sorunun ne kadar yaygın olduğunu ve hizmetimiz tarafından kaynaklandığını görmek için diğer kuruluşlardan gelen ilgili verilere ve raporlara bakacağız. Varsa, çözümlerini takip etmek için Hizmet durumu sayfasında yeni bir olay veya danışma olarak ekleriz. Bildirilen **Sorunlar sayfasında** , kiracının bu formda raporladığı tüm sorunlar ve durum görüntülenir.

Panoda hangi hizmetlerin görüntü görüntülemekte olduğunu özelleştirmek için TercihlerCustom  >  görünümü'ne tıklayın ve Hizmet durumu pano görünüm dışında filtrelemek istediğiniz hizmetlerin onay kutularını temizleyin. İzlemek istediğiniz her hizmet için onay kutusunun seçili olduğundan emin olun.

Kiracınızı etkileyen yeni olayları ve etkin bir olayın durum değişikliklerini etkileyen e-posta bildirimlerine kaydolmak için **TercihlerEmail'i** seçin,  >  Bana e-postada hizmet ısı bildirimi gönder'e tıklayın ve ardından şunları belirtin:

- En çok iki e-posta adresi.
- Olaylar veya tavsiyeler için bildirim almak isteyip istemeyysiniz
- Bildirim almak istediğiniz hizmetler

Ayrıca, bir hizmetin her etkinliği yerine tek tek etkinlikler için e-posta bildirimlerine abone olabilirsiniz. Bunu yapmak için, e-posta bildirimi güncelleştirmelerini almak istediğiniz etkin sorunu seçin, Bu sorun için **bildirimleri yönet'i seçin** ve ardından şunları belirtin:

- En çok iki e-posta adresi.

> [!NOTE]
> Her yöneticinin Tercihleri ayarlanmış olabilir ve her yönetici hesabı için iki e-posta adresi üst sınırı vardır.

> [!TIP]
> Ayrıca, mobil Microsoft 365 Yönetici [bildirimleriyle](https://go.microsoft.com/fwlink/p/?linkid=627216) güncel durumu takip etmek için mükemmel bir yol olan Hizmet durumunu görüntülemek için de mobil aygıtınızda Microsoft 365 Yönetici uygulamasını kullanabilirsiniz.

### <a name="view-details-of-posted-service-health"></a>Gönderilen hizmet durumunun ayrıntılarını görüntüleme

Tüm **hizmetler görünümünde** , çözüm üzerinde çalışırken gönderilen tüm iletilerin akışı dahil olmak üzere sorun hakkında daha fazla bilgi gösteren sorun ayrıntıları sayfasını görmek için sorun başlığını seçin.

[![Hizmet danışmanlığını gösteren ekran görüntüsü.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

Öneri veya olay özetinde aşağıdaki bilgiler sağlanır:

- **Başlık** - Sorunun özeti.
- **Kimlik** - Sorunun sayısal tanımlayıcısıdır.
- **Hizmet** - Etkilenen hizmetin adı.
- **Son güncelleştirme** - Hizmet durumu mesajının en son güncelleştirilmiş zamanı.
- **Tahmini Başlangıç saati** - Sorunun başladığı tahmini saat.
- **Durum** - Bu sorun hizmeti nasıl etkiler?
- **Kullanıcı Etkisi** - Bu sorunun son kullanıcı üzerindeki etkisiyle ilgili kısa bir açıklama.
- **Tüm Güncelleştirmeler** - Çözüm uygulama konusunda ilerleme durumu hakkında size bilgi almak için sık sık iletiler gönderiyoruz.

![Sorun ayrıntılarını gösteren ekran görüntüsü.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Hizmet durumu ayrıntılarını çevirme

İletileri tercih ettiğiniz dilde otomatik olarak görüntülemek için makine çevirisi kullanıyoruz. [Dilinizi ayarlama hakkında daha fazla bilgi için](lang-service-health.md) Hizmet durumu panosu için dil çevirisi makalesini okuyun.

### <a name="definitions"></a>Tanımlar

Çoğu zaman hizmetler sağlam görünür ve başka bilgi saği olmaz. Hizmette sorun olduğunda, hizmet öneri veya olay olarak tanımlanır ve geçerli durum gösterilir.

> [!TIP]
> Planlı bakım olayları hizmet durumu içinde gösterilmez. Planlı bakım olaylarını, İleti merkeziyle güncel olarak **izleyebilirsiniz**. Değişikliğin ne zaman olacağını, etkisini ve buna nasıl hazırlık olacağını bulmak için Değişiklik planı olarak kategorilere ayrılmış iletilere filtre uygulama. Daha [fazla bilgi için Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) merkezi'nde bulunan İleti merkezi'ne bakın.

### <a name="incidents-and-advisories"></a>Olaylar ve öneriler

| Simge | Açıklama |
|:-----|:-----|
|![Danışma için bilgi simgesi.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Hizmet için bir öneri gösteriliyorsa, bazı kullanıcıları etkileyen sorunun farkındayız ama hizmet hala kullanılabilir durumda demektir. Öneride, genellikle sorun için geçici bir çözüm vardır ve sorun aralıklı olarak ortaya çıkıyor veya kapsamı ve kullanıcı etkisi sınırlı olabilir.  <br/> |
|![Olayı için ünlem işareti simgesi.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Hizmet için etkin bir olay gösteriliyorsa, bu kritik bir sorundur ve hizmetin kendisi veya önemli bir işlevi kullanılamıyordur. Örneğin, kullanıcı e-posta gönderip alamıyor veya oturum açamıyor olabilir. Olayların kullanıcılar üzerinde göze çarpan bir etkisi olur. Devam eden bir olayda, Hizmet durumu panosunda incelemeyle, etkiyi azaltma çabalarıyla ve çözümün onayıyla ilgili güncelleştirmeler sağlarız.  <br/> |

### <a name="status-definitions"></a>Durum tanımları

| Durum | Tanım |
|:-----|:-----|
|**İnceleniyor** | Olasın bir sorun olduğunun farkındayız; neler olup bittiği ve bunun etkisinin kapsamı konusunda daha fazla bilgi topluyoruz. |
|**Hizmet performansında düşüş** | Bir hizmetin veya özelliğin kullanımını etkileyebilecek bir sorun olduğunu doğruladık. Örneğin, hizmet her zamankinden daha yavaş performans gösteriyorsa, aralıklı kesintiler oluyorsa veya bir özellik çalışmıyorsa, bu durum bilgisini görebilirsiniz. |
|**Hizmette kesinti** | Kullanıcıların hizmete erişimini etkileyen bir sorun olduğunu saptarsak, bu durum bilgisini görürsünüz. Bu durum gösterildiğinde, sorun önemlidir ve tutarlı olarak yeniden üretiliyor olabilir. |
|**Hizmet geri yükleniyor** | Sorunun nedeni belirlenmiştir, düzeltmek için yapılacak işlemleri biliyoruz ve hizmeti sağlam duruma döndürme çalışmalarımız sürüyor demektir. |
|**Genişletilmiş kurtarma** | Bu durum, hizmeti çoğu kullanıcı için geri yüklemeye yönelik düzeltme çalışmalarının sürdüğünü ancak tüm etkilenen sistemlere ulaşmanın biraz zaman alacağını gösterir. Kalıcı bir düzeltme uygulamayı beklerken geçici bir çözüm sağladığımızda da bu durum bilgisini görebilirsiniz. |
|**İnceleme askıya alındı** | Olası bir sorunla ilgili yaptığımız ayrıntılı inceleme sonunda, incelemeye devam etmek için müşterilerden ek bilgi istenmişse, bu durum bilgisini görürsünüz. Sizin işlem yapmanız gerekirse, bize hangi verilerin veya günlüklerin gerektiğini size bildiririz. |
|**Hizmet geri yüklendi** | Düzeltme işlemlerinin temel sorunu çözdüğünü ve hizmetin sağlam duruma geri yüklendiğini doğruladık anlamına gelir. Nerede sorun çıktığını öğrenmek için, sorunun ayrıntılarını görüntüleyin. |
|**Hatalı pozitif sonuç** | Ayrıntılı bir incelemeden sonra, hizmetin iyi olduğunu ve tasarlanmadı olarak işle ilgili olduğunu doğruladık. Hizmet üzerinde hiçbir etkisi gözlemlenmedi veya olayın nedeni hizmet dışından kaynaklandı. Bu durumdaki olaylar ve danışmalar, kullanım süresi dolana kadar (etkinliğin son gönderisinde belirtilen sürenin ardından) geçmiş görünümünde görünür. |
|**Olay sonrası rapor yayımlandı** | Kök neden bilgilerini ve benzer bir sorunun tekrar ortaya çıkarmaması için sonraki adımları içeren belirli bir sorun için Olay Sonrası Raporu yayımladık. |

### <a name="message-post-types"></a>İleti Gönderi Türleri

| Tür | Tanım |
|:-----|:-----|
|**Hızlı Güncelleştirme** | Tüm müşteriler tarafından kullanılabilen olayları geniş bir şekilde etkileyen kısa ve sık artımlı güncelleştirmeler. |
|**Ek Ayrıntılar** | Bu ek gönderiler, olayları işleme konusunda daha ayrıntılı görünürlük sağlamak için daha zengin teknik ve çözüm ayrıntıları sağlar. Bu, aşağıdaki koşulların izlenmesinde ana hatları verilen [Exchange Online kullanılabilir](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements). |

### <a name="history"></a>Geçmiş

Hizmet durumu geçerli durumunıza bakmanıza ve son 30 gün içinde kiracınızı etkilenen tüm hizmet danışmanlarının ve olaylarının geçmişini görüntülemenize olanak sağlar. Tüm hizmetlerin geçmiş durumunu görüntülemek için Geçmiş **görünümü'ne** tıklayın.

Çalışma süresi taahhüdümiz hakkında daha fazla bilgi için bkz[. Çalışma süremiz için Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>İlgili konular

- [Etkinlik Raporları Microsoft 365 yönetim merkezi](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [İleti merkezi Tercihler](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Yönetim merkezinde Windows durumunu denetleme](/windows/deployment/update/check-release-health)
