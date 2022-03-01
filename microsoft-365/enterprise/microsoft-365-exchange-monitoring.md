---
title: Exchange Online için izleme Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: E Exchange Online ta e-posta olayları veya danışmalar hakkında bilgi için izleme Microsoft 365.
ms.openlocfilehash: 22985d1fd6e79693a526c8ec008e189593543ae6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021726"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online için izleme Microsoft 365

Exchange Online Exchange Online <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">aboneliğinde Microsoft 365 yönetim merkezi</a> hizmetinin durumunu izlemek için Exchange izleme Microsoft 365 kullanabilirsiniz. Exchange Online izlemesi, bu kategorilerde toplanan olaylar ve tavsiyeler hakkında size bilgi sağlar:

- **Altyapı**: Sorun, Microsoft'un düzenli Microsoft 365 sağlamak ve sorunu çözmek için sahip olduğu yeni bir altyapıda algılandı. Örneğin, e-posta Exchange Online bulut altyapısıyla ilgili sorunlar Exchange kullanıcılar Microsoft 365 erişemeyr.
- **Üçüncü taraf altyapı**: Bu sorun, organizasyon tarafından bağımlılık yapılan üçüncü taraf altyapıda algılanır ve çözüm için kuruluştan işlem gerektirir. Örneğin, kullanıcı kimlik doğrulama işlemleri, kullanıcıların üçüncü taraf güvenlik belirteci hizmetine (STS) bağlanmasını engelleyen bir üçüncü taraf güvenlik belirteci hizmeti (STS) sağlayıcısı tarafından Exchange Online.
- **Müşteri altyapısı**: Sorun, kuruluş altyapınız içinde algılanır ve çözüm için kuruluştan işlem gerektirir. Örneğin, süresi dolan bir Exchange Online nedeniyle organizasyon tarafından barındırılan STS sağlayıcısından kimlik doğrulama belirteci elde edemeyen kullanıcılar Exchange Online erişim sağ yapamazlar.

aşağıdaki örnekte, Kuruluş ve öncelik  hesabı senaryolarında Microsoft 365 yönetim merkezi Durumu > Hizmet durumu bilgisinde bulunan Hizmet  [durumu sayfası örneği](../admin/setup/priority-accounts.md).

![Sayfanın Hizmet durumu Microsoft 365 yönetim merkezi.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Organizasyonla ilgili sorunlar,** kuruluş düzeyinde izleme ve öncelik hesabı izleme tarafından tanımlanır ve kullanılır.

Kurumdaki sorunlar'ın altındaki Sistem  Durumu sütununu değeri, kuruluş altyapısının mı yoksa üçüncü taraf yazılımının kuruluş kullanıcılarının ve/veya öncelik hesaplarının hizmet durumu deneyimini etkileyeceğini Exchange Online. Danışmanlar veya olaylar için *, eylemlerinizin* çözümü gerekir.

**Microsoft** hizmet durumu **altındaki Sistem** Durumu sütununu değeri, hizmetin iyi olduğunu ya da Microsoft'un bakımınıta olduğu bulut hizmetlerini temel alan danışmanlara veya olaylara sahip olduğunu gösterir.

Aşağıdaki örnekte, Exchange Online Hizmet Microsoft 365 yönetim merkezi durumu > hizmet durumu sayfasında bulunan kuruluş düzeyi ve öncelik hesabı senaryolarının durumunu **gösteren > izleme > Exchange Online**.

![Sayfa Exchange Online İzleme Microsoft 365 yönetim merkezi.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example.png)

İzleme **Exchange Online**, sistem durumu iyi olup olmadığını Exchange Online ilgili olay veya tavsiyeler olup olmadığını görebilirsiniz. Daha Exchange Online ile, belirli e-posta senaryolarının hizmet durumunu göz atabilirsiniz ve kuruluş düzeyi senaryolarının etkisini belirlemek için gerçek zamanlı sinyallere yakın bir yerde görüntüebilirsiniz. Ayrıca, öncelik hesabı senaryolarının durumunu da öğrenebilirsiniz.

## <a name="requirements"></a>Gereksinimler

Bu önizleme, şu gereksinimleri karşılaması gereken müşteriler için etkinleştirilmiştir:

- Şu ürünlerin bir veya birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

  Örneğin, kuruluşta uygun ürünlerden toplam 5.500 Office 365 E3, 2.500 Microsoft 365 E5 olmak üzere 3.000 Microsoft 365 E5 lisansı olabilir.

- Bir veya birden çok temel Microsoft 365 hizmeti için, örneğin Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve diğer uygulamaları içeren en az 50 aylık etkin Office vardır.

- Hizmet Durumu Panosu düzeyinde izinlere sahip olan her rol, Sistem Durumu Exchange Online erişim sağlar. Daha fazla bilgi için bkz. [Microsoft 365 hizmet durumunu denetleme](view-service-health.md).

## <a name="organization-level-scenarios"></a>Kuruluş düzeyi senaryolar

İzleme Exchange Online aşağıdaki senaryoları destekler:

- **E-posta** istemcileri: E-posta okuma etkinliğine dayalı olarak aşağıdaki e-posta istemcilerinin durumunu görüntüebilirsiniz:

  - Outlook masaüstü
  - Web üzerinde Outlook
  - iOS ve Android'in yerel posta istemcileri
  - iOS Outlook Android'de Outlook Mobile uygulaması
  - Outlook Mac istemcisi

   Bu istemciler için, e-postayı okuyan kullanıcılara dayalı olarak son 30 dakika içinde etkin kullanıcı sayısını, ayrıca panoda yer alan olay ve tavsiyeleri görebilirsiniz. Bu veriler, bir sorun olup olduğunu görmek için önceki haftanın aynı aralığıyla karşılaştırıldı.

   >[!Note]
   > Etkin kullanıcı sayısı, örneğin kullanıcı e-postayı okuduğunda tek bir etkinlikle ölçülür. Yalnızca son 30 etkinliklerin dakikalarını hesaplar.

- **Uygulama bağlantısı**: Tahmini bağlantı, kuruluş cihazları ve Exchange Online cihazları arasındaki başarılı, yapay bağlantı yüzdesine dayalıdır ve Microsoft'un kontrolü dışındaki sorunları içerebilir. Daha fazla bilgi edinmek için Bağlantı [Microsoft 365'lara bakın](microsoft-365-connectivity-optics.md).

- **Temel Kimlik Doğrulama ve Modern** Kimlik Doğrulama: Hizmette başarıyla doğrulanmış Exchange Online sayısı.

- **Posta akışı**: İletinin posta kutusuna ulaşana kadar herhangi bir gecikme olmadan posta kutusuna başarıyla teslim edilen ileti Microsoft 365.

  ![Posta teslimi için Exchange durumu izleme örneği.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

Bu senaryolarda, ana panoda son 30 dakika için anahtar sayılardır. Bu senaryoların her biri için ayrıntılı görünümler, önceki haftayla karşılaştırıldığında 30 dakikalık toplamayla yedi günlük yakın gerçek zamanlı eğilimi gösterir.

## <a name="priority-accounts-monitoring-scenarios"></a>Öncelik hesapları izleme senaryoları

Gelişmiş Exchange Online hesabı izlemeyle, öncelik hesaplarını yapılandırdikten sonra aşağıdaki senaryoların durumunu [görüntüebilirsiniz](/microsoft-365/admin/setup/priority-accounts):

- Exchange lisansı

- Posta Kutusu depolama alanı

- İleti sınırı

- Klasör başına alt klasörler

- Klasör hiyerarşisi

- Kurtarılabilir öğeler

Lisans Exchange durumu, kiracı yöneticisi tarafından ele alınabilecek geçersiz lisans sorunları nedeniyle öncelik hesabının oturum aç olup olmadığını denetler.

Yukarıdaki kalan beş senaryo, öncelik hesabı posta kutunuzu bu sınırlarda açıklanan sınırlara ulaşarak veya bu sınırlarda açıklanan sınırlara [ulaşarak Exchange Online kontrol edin](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

Bu senaryolarda, öncelik hesaplarınızı etkileyen etkin ve çözümlenmiş tavsiyeleri ve olayları görebilirler. Öncelik hesapları için tanımlayıcı bilgiler öneri veya olay ayrıntılarında önerilerle birlikte görüntülenir. İşte, Hizmet durumu bilgi durumu ve **durumu > sayfası > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Öncelik hesaplarınızı etkileyen etkin ve çözümlenmiş tavsiyelere ve olaylara örnek":::

Etkilenen hesap bölmesinde Durum sütunu **şu** değerlere sahiptir:

- Düzeltildi: Öncelik hesabı için danışmaya veya olayın neden olduğu sorun giderildi. Artık bir sorun yok. 

- Etkin: Öncelik hesabı için danışmaya veya olayın neden olduğu sorun devam ediyor. Sorun devam ediyor. 

- Gecikmeli: Danışmaya veya olayına neden olan sorun, öncelik hesabı için 96 saat içinde ele alınamamıştır, bu nedenle askıya alınır. Sorun devam ediyor. 

İşte bir örnek.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Etkilenen hesap bölmesinde durum sütunu örneği":::

Hiçbir hesap Etkin durumda kalmadan danışma veya olay **çözülür** . 

## <a name="send-us-feedback"></a>Bize geri bildirim gönderin

Geri bildirim sağlamanın iki yolu vardır:

- Sayfanın **her sayfasında** bulunan Geri bildirim ver seçeneğini Microsoft 365 yönetim merkezi.

- Belirli bir olay veya **danışma için Bu gönderi yardımcı mı?** bağlantısını kullanarak geri bildirim gönderin.

  !["Bu gönderi yardımcı mı?" bağlantısına tıklayın.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

#### <a name="1-why-dont-i-see-exchange-online-monitoring-under-health-in-the-microsoft-365-admin-center"></a>1. Sistem Durumu altında neden Exchange Online izlemesi" Microsoft 365 yönetim merkezi? 

İlk olarak, yönetim sayfasının Giriş sayfasındaki yeni yönetim **merkezini etkinleştirmiş** <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi.</a>

Ardından, aşağıdaki iki gereksinimlerin ikisini de karşılamıyor olun:

- Şu ürünlerin bir veya birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

- Bir veya birden çok temel Microsoft 365 hizmeti için, örneğin Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve diğer uygulamaları içeren en az 50 aylık etkin Office vardır.

Kuruluş lisans sayısı 5.000'in altında ise ve temel hizmetlerde aylık etkin kullanıcılar 50'nin altına düştüğünde, bu gereksinimler karşılanana kadar Exchange Online izleme etkinleştirilmez.

#### <a name="2-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>2. Her istemci için panoda etkin kullanıcı sayısı düşük gibi görünür. Kullanıcılara atanmış çok sayıda etkin lisansımız var. Bu ne anlama geliyor?

İzlemede gösterilen etkin kullanıcı sayısı, kullanıcıların özellikte etkinliği gerçekleştirilen 30 dakikalık bir pencereye dayalıdır. Bu, kullanım sayılarıyla karıştırılmamalıdır. Kullanım numaralarını görüntülemek için raporlarda etkinlik raporlarını kullanın Microsoft 365 yönetim merkezi **Raporları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**.**</a>

#### <a name="3-will-there-be-other-monitoring-scenarios-for-other-services-such-as-teams-and-sharepoint"></a>3. Örnek veri ve saat gibi diğer hizmetler için başka Teams senaryoları SharePoint?

Microsoft, bu deneyimi doğrudan şirket içindeki Hizmet Durumu panosu Microsoft 365 yönetim merkezi. Bu, Microsoft'a diğer hizmetler için izleme senaryoları genişletme fırsatları sunar ve paylaşacak haber olduğunda duyurulacak.

#### <a name="4-what-is-the-plan-for-general-availability-of-this-experience"></a>4. Bu deneyimin genel olarak kullanılabilirliği planı nedir?

Microsoft, sistem Exchange Online doğrudan Sistem Durumu panosu <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**üzerinde** izleme Microsoft 365 yönetim merkezi</a>.

Bu yeni tümleşik deneyimle, Microsoft'un planı geri bildirimlerinizi toplamak ve ardından genel kullanılabilirlik için planlarımızı tanımlamaktır.

#### <a name="5-is-this-a-free-included-or-paid-extra-feature"></a>5. Bu ücretsiz (dahil) veya ücretli (ek) bir özellik mi? 

Bu, önizlemede olan ücretsiz bir özelliktir ve yalnızca soru 1. soruda gereksinimleri karşı olan müşteriler tarafından kullanılabilir. Bu içeriği almak için ücretli bir seçenek yok.

#### <a name="6-how-do-i-provide-feedback"></a>6. Nasıl geri bildirim sağlarim?

Genel geri bildirim için, **izleme** sayfasının sağ alt köşesindeki Geri **bildirim Exchange Online** kullanın. 

Olaylar veya tavsiyeler hakkında geri bildirim için Bu gönderi yardımcı **mı? bağlantısını** kullanın.

#### <a name="7-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>7. Etkinlik eğilimlerini gösterecek senaryolar için veriler nerede kullanılabilir?

Veriler, Veri Kaynağı Exchange Online araç Exchange Online. İstek Exchange Online ulaşmadan önce bir hata Exchange Online, etkinlik sinyalinde bir hata olur.

#### <a name="8-are-there-any-privacy-concerns"></a>8. Gizlilikle ilgili bir endişeniz var mı?

Hizmet meta verilerine odaklanmayı ve kullanıcı içeriğini izlemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet durumunu Microsoft 365 denetleme](view-service-health.md) 

- [Exchange Online sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits)

- [Öncelik hesaplarını yönetme ve izleme](/microsoft-365/admin/setup/priority-accounts)

- [Microsoft 365'de Öncelik Hesaplarını Kullanma](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)

- [Posta kutusu kullanımının izlemesinde Exchange Online uyarıları](microsoft-365-mailbox-utilization-service-alerts.md)

- [Sistem izlemesinde MRS kaynak gecikmeleri için Exchange Online uyarıları](microsoft-365-mrs-source-delays-service-alerts.md)
