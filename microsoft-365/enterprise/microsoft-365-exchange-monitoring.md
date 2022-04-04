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
ms.openlocfilehash: 07d43a6f61ffe3e38f927d47e09d0a9685925f73
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520726"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online için izleme Microsoft 365

Exchange Online izleme aşağıdaki kuruluş düzeyi senaryoları destekler:

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

- **Web Outlook Oturum Açma**: Oturum açıp başarıyla başlatan kullanıcıların Web üzerinde Outlook.
  
Burada, ana panoda yer alan diğer tüm posta Exchange Online senaryolara bir örnek ve almaktadır.

![Denetim İzleme için kuruluş Exchange Online senaryoları.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Bu senaryolarda, ana panoda son 30 dakika için anahtar sayılardır. Bu senaryoların her biri için ayrıntılı görünümler, önceki haftayla karşılaştırıldığında 30 dakikalık toplamayla yedi günlük yakın gerçek zamanlı eğilimi gösterir.

![Posta teslimi için Exchange durumu izleme örneği.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

"Sorunun kaynağı" olarak etiketlenen iletişimde, "Kendi kuruluşunuz" olarak etiketlenmiş, sizin için oluşturulmuş olayları veya tavsiyeleri fark edebilirsiniz. Bunlar, azaltma ve çözüm için dikkat çekmenizi gerektiren tek tek kuruluşa yönelik olan bildirimlerdir. Hizmet durumu altında oluşturulacak ve kuruma olası etki konusunda bilgi sağlandı bilgisi sağlayan çeşitli türlerde sorunlar hakkında daha fazla bilgi için, aşağıdaki makalelere bakın:

- [Posta kutusu kullanımıyla ilgili hizmet uyarıları](microsoft-365-mailbox-utilization-service-alerts.md)

- [MRS kaynak gecikmeleri için hizmet uyarıları](microsoft-365-mrs-source-delays-service-alerts.md)

- [Dış alıcılara teslimi bekleyen iletiler için hizmet uyarıları](microsoft-365-external-recipient-service-alerts.md)

## <a name="priority-accounts-monitoring-scenarios"></a>Öncelik hesapları izleme senaryoları

Gelişmiş Exchange Online hesabı izlemeyle, öncelik hesaplarını yapılandırdikten sonra aşağıdaki senaryoların durumunu [görüntüebilirsiniz](/microsoft-365/admin/setup/priority-accounts):

- Exchange lisansı

- Posta Kutusu depolama alanı

- İleti sınırı

- Klasör başına alt klasörler

- Klasör hiyerarşisi

- Kurtarılabilir öğeler

Lisans Exchange, kiracı yöneticisi tarafından ele alınabilecek geçersiz lisans sorunları nedeniyle öncelik hesabının oturum aç olup olmadığını denetler.

Yukarıdaki kalan beş senaryo, öncelik hesabı posta kutunuzu bu sınırlarda açıklanan sınırlara ulaşarak veya bu sınırlarda açıklanan sınırlara [ulaşarak Exchange Online kontrol edin](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

Bu senaryolarda, öncelik hesaplarınızı etkileyen etkin ve çözümlenmiş tavsiyeleri ve olayları görebilirler. Öncelik hesapları için tanımlayıcı bilgiler öneri veya olay ayrıntılarında önerilerle birlikte görüntülenir. İşte, Health **> Hizmet durumu > Exchange Online sayfasından bir > Hizmet durumu > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Öncelik hesaplarınızı etkileyen etkin ve çözümlenmiş tavsiyelere ve olaylara örnek":::

Etkilenen hesap bölmesinde Durum sütunu **şu** değerlere sahiptir:

- Düzeltildi: Öncelik hesabı için danışmaya veya olayın neden olduğu sorun giderildi. Artık bir sorun yok. 

- Etkin: Öncelik hesabı için danışmaya veya olayın neden olduğu sorun devam ediyor. Sorun devam ediyor. 

- Gecikmeli: Danışmaya veya olayına neden olan sorun 96 saat içinde öncelik hesabına yönelik olarak ele alınamamıştır ve bu nedenle askıya alınır. Sorun devam ediyor. 

İşte bir örnek.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Etkilenen hesap bölmesinde durum sütunu örneği":::

Hiçbir hesap Etkin durumda kalmadan danışma veya olay **çözülür** .

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="1-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>1. Her istemci için panoda etkin kullanıcı sayısı düşük gibi görünür. Kullanıcılara atanmış çok sayıda etkin lisansımız var. Bu ne anlama geliyor?

İzlemede gösterilen etkin kullanıcı sayısı, kullanıcıların özellikte etkinliği gerçekleştirilen 30 dakikalık bir pencereye dayalıdır. Bu, kullanım sayılarıyla karıştırılmamalıdır. Kullanım numaralarını görüntülemek için raporlarda etkinlik raporlarını kullanın Microsoft 365 yönetim merkezi **Raporları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**.**</a>

### <a name="2-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>2. Etkinlik eğilimlerini gösterecek senaryolar için veriler nerede kullanılabilir?

Veriler, Veri Kaynağı Exchange Online araç Exchange Online. İstek Exchange Online ulaşmadan önce bir hata Exchange Online, etkinlik sinyalinde bir hata olduğunu varsa.
