---
title: Microsoft 365 değerlendirmesini geri ayanız
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 değerlendirmesini geri ayanız
ms.openlocfilehash: 5ff858ef652c7fc536310c9d27887863d156fb5d
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63495018"
---
# <a name="microsoft-365-network-assessment"></a>Microsoft 365 değerlendirmesini geri ayanız

Ağ Microsoft 365 Yönetici'nin ağ bağlantısında **, ağ** değerlendirmeleri birçok ağ performansı ölçümünü bir toplamını kurumsal ağ çevre durumu bilginizin anlık görüntüsü olarak tasarlanmıştır. Ağ değerlendirmesinde, müşteriden sorumlu olan ağ tasarımının proje kullanıcı deneyimini Office 365 olduğu anlat. Ağ değerlendirmeleri hem kiracının tamamını hem de kullanıcıların kiracınıza bağladığı coğrafi konumların tamamını kapsıyor. Değerlendirmeler, Microsoft 365 bir şekilde şirketin ağ durumu hakkında bilgi almak ve herhangi bir genel ofis konumu için ayrıntılı rapora hızla gitmek için kolay bir yol sağlar.

Ağ değerlendirme noktaları değeri 0 ile 100 arasındadır ve TCP gecikme süresinin, indirme hızının ve UDP bağlantı kalitesi ölçümlerinin ortalamasıdır. Bu ölçümler günde bir kez der edilir. Microsoft'a ait ağların performans ölçümleri, değerlendirme sonuçlarının belirsiz ve şirket ağına özgü olduğundan emin olmak için bu ölçümler dışında tutuldur.

> [!div class="mx-imgBorder"]
> ![Ağ değerlendirme değeri.](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Ağ değerlendirme değeri çok düşükse, Microsoft 365 istemcilerinin kiracıya bağlanırken veya hızlı yanıt veren kullanıcı deneyimini sürdürmede önemli sorunlar yaşamaları önermektedir. Yüksek bir değer, düzgün yapılandırılmış bir ağı birkaç devam eden performans sorunuyla gösterir. %80 değeri, sağlıklı bir taban çizgisini temsil eder ve üstünde ağ performansından dolayı Microsoft 365 bağlantısı veya yanıt süresi hakkında normal kullanıcı şikayetleri almayabilirsiniz. Iterative ağ bağlantısı geliştirmeleri yapılırken, kullanıcı deneyimiyle birlikte bu değer de artar.

| Ağ değerlendirmesi | Beklenen kullanıcı deneyimi |
| :----------------- | :----------------------- |
| 100                | En iyi                     |
| 80                 | Önerilere karşılama    |
| 60                 | Kabul edilebilir               |
| 40                 | Kullanıcılar sorun yaşanıyor olabilir |
| 20                 | Kullanıcılar şikayetçi olabilir       |
| 0                  | Ağ sorunları yaygın bir tartışma konusu |

## <a name="network-assessment-panel"></a>Ağ değerlendirme paneli

Kiracının kapsamındaki veya belirli bir ofis konumu kapsamındaki her ağ değerlendirmesinde, değerlendirmeyle ilgili ayrıntıların yer alan bir panel gösterilir. Bu panelde, değerlendirmenin bir yüzdelik çubuk grafiği ve yalnızca ölçü verileri alınan iş yükleri de dahil olmak üzere her bileşen iş yükünün toplam noktaları olarak gösterilir. Ofis konumu ağ değerlendirmesi için, ofis konumuyla aynı şehirde veri bildirilen beş Microsoft 365 müşterilerden her biri için müşterilerden yüzdeyle karşılaştırmayı da gösteririz.

> [!div class="mx-imgBorder"]
> ![Örnek ağ değerlendirme değeri.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

**Panelde yer** alan Değerlendirme dökümü, bileşen iş yüklerinin her biri için değerlendirmeyi gösterir.

Değerlendirme **geçmişi,** değerlendirme ve karşılaştırmanın son 30 günü gösterir. Ayrıca, geçmiş sekmesini kullanarak herhangi bir ofis konumunun metrik geçmişini iki yıl boyunca raporleyebilirsiniz. Geçmiş sekmesi, rapor etmek istediğiniz öznitelikleri seçmenize olanak sağlar. Rapor zaman dilimini seçerek, ağ güncelleştirme projesinin etkisini vurgular ve ağ değerlendirmenize ilişkin iyileştirmeleri görüntüebilirsiniz.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Kiracı ağ değerlendirmeleri ve ofis konumu ağ değerlendirmeleri

Ağ değerlendirmesi, ofis konumunun ağ çevresini Microsoft'un ağına yönelik tasarımı ölçüleri. Ağ çevresini iyileştirmeler her ofis konumu için en iyi şekilde yapılır.

Ağ performansına genel bakış sayfasında tüm kiracı Microsoft 365 bir ağ değerlendirme değeri gösteririz. Bu değer, tüm ofis konumları için ağ değerlendirmelerinin ağırlıklı ortalamasıdır. Ayrıca, bu konumun özet sayfasında algılanan her ofis konumu için belirli bir ağ değerlendirme değeri vardır.

## <a name="exchange-online"></a>Exchange Online

Daha Exchange Online için, istemci makineden Exchange ön Exchange TCP gecikme süresi ölçülür. Ağın müşterilerin LAN ve WAN'ı üzerinden uzaklığı bu gecikme süresini etkilemektedir. Ayrıca, ağ aracı cihaz veya hizmetlerden de etki olabilir ve bu da bağlantının gecikmesini sağlar veya paketlerin yeniden gönderilene neden olur. Ayrıca, en yakın ön Exchange kapılardan etkilenmez. Önceki üç gün boyunca tüm ölçümlerde orta değer (50. yüzdebirlik veya P50 ölçüsü olarak da bilinir) alınır.

Aşağıdaki Exchange Online kullanılarak değerlendirme yapılır. Eşikler arasındaki herhangi bir TCP gecikme sayısı bant içinde doğrusal olarak noktalara atanır.

| TCP Gecikme Süresi   | Puanlar |
| :------------ | :----- |
| 10 ms veya daha az  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms veya daha fazla | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

Çevrimiçi SharePoint Online için kullanıcının belgeye İnternet'SharePoint veya Siteden OneDrive hızı ölçülür. İstemci makinesi ile Microsoft'un ağı arasındaki ağ devreleri üzerindeki bant genişliği bu etkiyi etkiler. Ayrıca, karmaşık ağ cihazlarında performans sorunları veya bu alanlarda yetersiz kapsamda olan ağ tıkanıklığı da çoğunlukla Wi-Fi etkiler. İndirme hızı saniye başına megabayt cinsinden ölçülür ve bu da saniyede megabit olarak derecelendirilmiş bir devrenin yaklaşık onda biridir. İkinci birim başına MegaBayt yararlı olur, çünkü 1 saniye içinde hangi boyut dosyasının indirilemediklerine doğrudan bakabilirsiniz. Önceki üç gün boyunca yapılan tüm ölçümlerde, 25. yüzdebirlik (P25 ölçüsü olarak da bilinir) alınır. Bu 25. yüzdebirlik, zaman içinde değişen tıkanıklığı azaltmaya yardımcı olur.

Aşağıdaki SharePoint Online değerlendirmesi yapılır. Eşikler arasındaki herhangi bir indirme hızı numarasına bant içinde doğrusal olarak puan atanır.

| İndirme hızı | Puanlar |
| :------------- | :----- |
| 20MBps veya daha fazlası | 100    |
| 14MBps         | 80     |
| 8MBps          | 60     |
| 4MBps          | 40     |
| 2MBps          | 20     |
| 0MBps          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Daha Microsoft Teams Ağ kalitesi UDP gecikme süresi, UDP değişimi ve UDP paket kaybı olarak ölçülür. UDP, iş akışı için arama ve konferans ses ve video medya bağlantısı Microsoft Teams. UDP daha yaygın TCP protokolüne ayrı olarak yapılandırıldığından, bu durum ağın UDP desteğinde bağlantı boşluklarını ve indirme hızının yanı sıra gecikme süresi ve indirme hızıyla aynı faktörlerden etki edilebilir. Önceki üç gün boyunca tüm ölçümlerde orta değer (50. yüzdebirlik veya P50 ölçüsü olarak da bilinir) alınır. 

Bir ile beş arasında bir ölçek için bu UDP ölçümlerinden ortalama bir görüş puanı hesaplarız. Bunu, ağ değerlendirmesi için 0-100 puanlık Microsoft Teams eşlemiz.  İyi genel olarak 87,5 puan, genel olarak kötü de 50 puan altında olur.

## <a name="related-topics"></a>İlgili konular

[Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı](office-365-network-mac-perf-overview.md)

[Microsoft 365 performansı içgörüleri hakkında bilgi edinin](office-365-network-mac-perf-insights.md)

[Microsoft 365 bağlantı test aracı](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a](office-365-network-mac-location-services.md)
