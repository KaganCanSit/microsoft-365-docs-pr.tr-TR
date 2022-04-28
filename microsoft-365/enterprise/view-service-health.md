---
title: Microsoft 365 hizmet durumunu denetleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Etkin bir hizmet kesintisi olup olmadığını görmek için desteği aramadan önce Microsoft 365 hizmetlerinin sistem durumunu görüntüleyin.
ms.openlocfilehash: 3155d9a26fd2b34eb4f5bc820e906d35f1f7fdff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090219"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Microsoft 365 hizmet durumunu denetleme

[![Yönetim merkezinin değiştiğini size bildirmeye yarayan etiket ve daha fazla ayrıntıyı aka.ms/aboutM365preview sayfasında bulabilirsiniz.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Web üzerinde Office, Yammer, Microsoft Dynamics CRM ve mobil cihaz yönetimi bulut **Hizmet durumu** [hizmetleri dahil olmak üzere Microsoft hizmetleri durumunu Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

Yönetim merkezinde oturum açamıyorsanız, kiracınızda oturum açmanızı engelleyen bilinen sorunları denetlemek için [hizmet durumu sayfasını](https://status.office365.com) kullanabilirsiniz.  Ayrıca, belirli olaylarla ilgili bilgileri görmek için Twitter'daki [@MSFT365status](https://twitter.com/MSFT365Status) bizi takip etmek için kaydolun.

## <a name="how-to-check-service-health"></a>Hizmet durumunu denetleme

1. konumundaki Microsoft 365 yönetim merkezi [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)gidin ve bir yönetici hesabıyla oturum açın.

    > [!NOTE]
    > Genel yönetici veya hizmet desteği yöneticisi rolüne atanan kişiler hizmet durumunu görüntüleyebilir. Exchange, SharePoint ve Skype Kurumsal yöneticilerinin hizmet durumunu görüntülemesine izin vermek için, bunların Hizmet yöneticisi rolüne de atanmaları gerekir. Hizmet durumunu görüntüleyebilen roller hakkında daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Hizmet durumunu görüntülemek için yönetim merkezinin sol tarafındaki gezinti bölmesinde **Sistem Durumu** >  **Hizmet durumu'na** gidin veya **Giriş panosundaki** **Hizmet durumu** kartını seçin. Pano kartı etkin bir hizmet sorunu olup olmadığını gösterir ve ayrıntılı **Hizmet durumu** sayfasına bağlantılar içerir.

3. **Hizmet durumu** sayfasında, her bulut hizmetinin sistem durumu tablo biçiminde gösterilir.

   ![Hizmet durumuyla ilgili güncel sorunların görünümü.](../media/shd-landing-page.png)

**Tüm hizmetler** sekmesi (varsayılan görünüm), tüm hizmetleri, geçerli durumlarını ve etkin olayları veya önerileri gösterir. **Sistem Durumu** sütunundaki bir simge ve durum, her hizmetin durumunu gösterir.

Bir hizmet için etkin bir olay veya danışmanlık varsa, bunlar doğrudan iç içe bir tablodaki hizmet adının altında listelenir. Hizmet adının solundaki köşeli çift ayraç simgesine tıklayarak bu görünümdeki olayları veya önerileri gizlemek için iç içe tabloyu daraltabilirsiniz.

Görünümünüzü yalnızca tüm etkin olayları gösterecek şekilde filtrelemek için sayfanın üst kısmındaki **Olaylar** sekmesini seçin. **Danışmanlar** sekmesi seçildiğinde yalnızca gönderilen tüm etkin öneriler gösterilir.

**Geçmiş** sekmesi, son yedi veya 30 gün içinde çözülen tüm olayları ve önerileri gösterir.

bir Microsoft 365 hizmetiyle ilgili sorun yaşıyorsanız ve **Hizmet durumu sayfasında** listelendiğini görmüyorsanız, **Sorun bildir'i** seçip kısa formu tamamlayarak bu konuda bize bilgi verin. Sorunun ne kadar yaygın olduğunu ve hizmetimizden kaynaklanıp kaynaklandığını görmek için diğer kuruluşların ilgili verilerine ve raporlarına göz atacağız. Bunu yaptıysa, **Hizmet durumu sayfasına yeni** bir olay veya danışmanlık olarak ekleriz. Burada çözümü izleyebilirsiniz. **Bildirilen Sorunlar** sayfası, kiracınızın bu formdan bildirdiği tüm sorunları ve durumu gösterir.

Panoda hangi hizmetlerin görüntülendiğine ilişkin görünümünüzü özelleştirmek için **TercihlerÖzel** >  **görünüm'ü** seçin ve Hizmet durumu pano görünümünüzde filtrelemek istediğiniz hizmetlerin onay kutularını temizleyin. İzlemek istediğiniz her hizmet için onay kutusunun seçili olduğundan emin olun.

Kiracınızı etkileyen yeni olayların e-posta bildirimlerine ve etkin bir olayın durum değişikliklerine kaydolmak için **TercihlerEmail'i** >  seçin, **Bana e-postada hizmet sıcaklık bildirimleri gönder'e** tıklayın ve şunları belirtin:

- En fazla iki e-posta adresi.
- Olaylar veya öneriler için bildirim isteyip istemediğiniz
- Bildirim almak istediğiniz hizmetler

Ayrıca, bir hizmet için her olay yerine tek tek olaylar için e-posta bildirimlerine abone olabilirsiniz. Bunu yapmak için, e-posta bildirim güncelleştirmelerini almak istediğiniz etkin sorunu seçin, **Bu sorun için bildirimleri yönet'i** seçin ve şunları belirtin:

- En fazla iki e-posta adresi.

> [!NOTE]
> Her yöneticinin Tercihleri ayarlanmış olabilir ve yukarıdaki iki e-posta adresi sınırı yönetici hesabı başınadır.

> [!TIP]
> Hizmet durumu görüntülemek için mobil cihazınızdaki [Microsoft 365 Yönetici uygulamasını](https://go.microsoft.com/fwlink/p/?linkid=627216) da kullanabilirsiniz. Bu, anında iletme bildirimleriyle güncel kalmanın harika bir yoludur.

### <a name="view-details-of-posted-service-health"></a>Gönderilen hizmet durumunun ayrıntılarını görüntüleme

**Tüm hizmetler** görünümünde, bir çözüm üzerinde çalışırken gönderilen tüm iletilerin akışı da dahil olmak üzere sorun hakkında daha fazla bilgi gösteren sorun ayrıntı sayfasını görmek için sorun başlığını seçin.

[![Hizmet önerisini gösteren ekran görüntüsü.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

Öneri veya olay özetinde aşağıdaki bilgiler sağlanır:

- **Başlık** - Sorunun özeti.
- **Kimlik** - Sorunun sayısal tanımlayıcısı.
- **Hizmet** - Etkilenen hizmetin adı.
- **Son güncelleştirme** - Hizmet durumu iletisinin son güncelleştirilme zamanı.
- **Tahmini Başlangıç saati** - Sorunun başladığı tahmini zaman.
- **Durum** - Bu sorunun hizmeti nasıl etkilediği.
- **Kullanıcı Etkisi** - Bu sorunun son kullanıcı üzerindeki etkisinin kısa bir açıklaması.
- **Tüm Güncelleştirmeler** - Bir çözümü uygularken kaydettiğimiz ilerlemeyi size bildirmek için sık sık ileti gönderiyoruz.

![Sorun ayrıntılarını gösteren ekran görüntüsü.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Hizmet durumu ayrıntılarını çevirme

İletileri tercih ettiğiniz dilde otomatik olarak görüntülemek için makine çevirisini kullanırız. Dilinizi ayarlama hakkında daha fazla bilgi [için Hizmet durumu panosu için dil çevirisini](lang-service-health.md) okuyun.

### <a name="definitions"></a>Tanımlar

Çoğu zaman, hizmetler daha fazla bilgi olmadan sağlıklı görünür. Hizmette sorun olduğunda, hizmet öneri veya olay olarak tanımlanır ve geçerli durum gösterilir.

> [!TIP]
> Planlı bakım olayları hizmet durumu içinde gösterilmez. **İleti merkezi** ile güncel kalarak planlı bakım olaylarını izleyebilirsiniz. Değişikliğin ne zaman gerçekleşeceğini, etkisini ve buna nasıl hazırlanacağını öğrenmek için Değişiklik planı olarak kategorilere ayrılmış iletilere filtreleyin. Diğer ayrıntılar için bkz. [Microsoft 365'de İleti merkezi](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).

### <a name="incidents-and-advisories"></a>Olaylar ve öneriler

| Simge | Açıklama |
|:-----|:-----|
|![Danışmanlık için bilgi simgesi.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Hizmet için bir öneri gösteriliyorsa, bazı kullanıcıları etkileyen sorunun farkındayız ama hizmet hala kullanılabilir durumda demektir. Öneride, genellikle sorun için geçici bir çözüm vardır ve sorun aralıklı olarak ortaya çıkıyor veya kapsamı ve kullanıcı etkisi sınırlı olabilir.  <br/> |
|![Olay için ünlem işareti simgesi.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Hizmet için etkin bir olay gösteriliyorsa, bu kritik bir sorundur ve hizmetin kendisi veya önemli bir işlevi kullanılamıyordur. Örneğin, kullanıcı e-posta gönderip alamıyor veya oturum açamıyor olabilir. Olayların kullanıcılar üzerinde göze çarpan bir etkisi olur. Devam eden bir olayda, Hizmet durumu panosunda incelemeyle, etkiyi azaltma çabalarıyla ve çözümün onayıyla ilgili güncelleştirmeler sağlarız.  <br/> |

### <a name="status-definitions"></a>Durum tanımları

| Durum | Tanım |
|:-----|:-----|
|**Araştırı** | Olasın bir sorun olduğunun farkındayız; neler olup bittiği ve bunun etkisinin kapsamı konusunda daha fazla bilgi topluyoruz. |
|**Hizmet performansında düşüş** | Bir hizmetin veya özelliğin kullanımını etkileyebilecek bir sorun olduğunu doğruladık. Örneğin, hizmet her zamankinden daha yavaş performans gösteriyorsa, aralıklı kesintiler oluyorsa veya bir özellik çalışmıyorsa, bu durum bilgisini görebilirsiniz. |
|**Hizmette kesinti** | Kullanıcıların hizmete erişimini etkileyen bir sorun olduğunu saptarsak, bu durum bilgisini görürsünüz. Bu durum gösterildiğinde, sorun önemlidir ve tutarlı olarak yeniden üretiliyor olabilir. |
|**Hizmet geri yükleniyor** | Sorunun nedeni belirlenmiştir, düzeltmek için yapılacak işlemleri biliyoruz ve hizmeti sağlam duruma döndürme çalışmalarımız sürüyor demektir. |
|**Genişletilmiş kurtarma** | Bu durum, hizmeti çoğu kullanıcı için geri yüklemeye yönelik düzeltme çalışmalarının sürdüğünü ancak tüm etkilenen sistemlere ulaşmanın biraz zaman alacağını gösterir. Kalıcı bir düzeltme uygulamayı beklerken geçici bir çözüm sağladığımızda da bu durum bilgisini görebilirsiniz. |
|**İnceleme askıya alındı** | Olası bir sorunla ilgili yaptığımız ayrıntılı inceleme sonunda, incelemeye devam etmek için müşterilerden ek bilgi istenmişse, bu durum bilgisini görürsünüz. Sizin işlem yapmanız gerekirse, bize hangi verilerin veya günlüklerin gerektiğini size bildiririz. |
|**Hizmet geri yüklendi** | Düzeltme işlemlerinin temel sorunu çözdüğünü ve hizmetin sağlam duruma geri yüklendiğini doğruladık anlamına gelir. Nerede sorun çıktığını öğrenmek için, sorunun ayrıntılarını görüntüleyin. |
|**Hatalı pozitif** | Ayrıntılı bir araştırmadan sonra hizmetin iyi durumda olduğunu ve tasarlandığı şekilde çalıştığını doğruladık. Hizmet üzerinde herhangi bir etki gözlemlenmedi veya olayın nedeni hizmetin dışından kaynaklandı. Bu duruma sahip olaylar ve öneriler, süresi dolana kadar geçmiş görünümünde görünür (bu olay için son gönderide belirtilen süreden sonra). |
|**Olay sonrası rapor yayımlandı** | Benzer bir sorunun yeniden oluşmamasını sağlamak için kök neden bilgilerini ve sonraki adımları içeren belirli bir sorun için Olay Sonrası Raporu yayımladık. |

### <a name="message-post-types"></a>İleti Gönderi türleri

| Tür | Tanım |
|:-----|:-----|
|**Hızlı Güncelleştirme** | Olayları geniş ölçüde etkileyen kısa ve sık artımlı güncelleştirmeler tüm müşterilerin kullanımına sunulur. |
|**Ek Ayrıntılar** | Bu ek gönderiler, olayların işlenmesine ilişkin daha ayrıntılı görünürlük sağlamak için daha zengin teknik ve çözüm ayrıntıları sağlar. Bu, [Exchange Online izleme](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements) için belirtilen gereksinimleri karşılayan kiracılar için kullanılabilir. |

### <a name="history"></a>Geçmiş

Hizmet durumu, geçerli durumunuzu incelemenize ve son 30 gün içinde kiracınızı etkileyen hizmet önerilerinin ve olayların geçmişini görüntülemenize olanak tanır. Tüm hizmetlerin geçmiş durumunu görüntülemek için **Geçmiş görünümü'nü** seçin.

Çalışma süresi taahhüdümüz hakkında daha fazla bilgi için bkz. [Microsoft 365 saydam işlemler](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>İlgili konular

- [Microsoft 365 yönetim merkezi Etkinlik Raporları](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [İleti merkezi Tercihleri](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Yönetim merkezinde sürüm durumunu Windows denetleme](/windows/deployment/update/check-release-health)
