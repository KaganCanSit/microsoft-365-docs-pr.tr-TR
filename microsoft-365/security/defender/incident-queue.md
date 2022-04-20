---
title: Microsoft 365 Defender'de olayların önceliklerini belirleme
description: Microsoft 365 Defender'da olay kuyruğundan olayları filtrelemeyi öğrenin
keywords: olay, kuyruk, genel bakış, cihazlar, kimlikler, kullanıcılar, posta kutusu, e-posta, olaylar, analiz, yanıt, önceliklendirme
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 285da473c8e8035a28ee6e64c4950e2b8fe373f5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944425"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Microsoft 365 Defender'de olayların önceliklerini belirleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender bağıntı analizi uygular ve farklı ürünlerden gelen ilgili uyarıları ve otomatik araştırmaları bir olaya toplar. Microsoft 365 Defender, Microsoft 365 Defender ürün paketinin tamamında uçtan uca görünürlük göz önünde bulundurulduğunda yalnızca kötü amaçlı olarak tanımlanabilen etkinliklerle ilgili benzersiz uyarılar tetikler. Bu görünüm, güvenlik analistlerinize kuruluşunuz genelindeki karmaşık tehditleri daha iyi anlamalarına ve bunlarla başa çıkmalarına yardımcı olan daha geniş bir saldırı hikayesi sunar.

**Olay kuyruğu**, cihazlar, kullanıcılar ve posta kutuları arasında oluşturulan bir olay koleksiyonunu gösterir. Olay önceliklerini belirleme ve olay önceliklendirme olarak bilinen bir bilgili siber güvenlik yanıtı kararı oluşturma amacıyla olayları sıralamanıza yardımcı olur.

**olaylar & uyarıları > Microsoft 365 Defender** <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalının</a> hızlı başlatılması sırasında olaylar bölümünden olay kuyruğuna ulaşabilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Microsoft 365 Defender portalındaki olay kuyruğunun gösterildiği Olay bölümü." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

**En son olaylar ve uyarılar** bölümü, alınan uyarı sayısının ve son 24 saat içinde oluşturulan olayların grafiğini gösterir.

Varsayılan olarak, Microsoft 365 Defender portalındaki olay kuyruğu son altı ayda görülen olayları görüntüler. En son olay listenin en üstündedir, böylece ilk olarak görebilirsiniz.

Olay kuyruğunda, olayın farklı özelliklerine veya etkilenen varlıklara görünürlük sağlayan özelleştirilebilir sütunlar ( **Sütunları seç'i seçin**) vardır. Bu, analiz için olayların önceliklendirilmesiyle ilgili bilinçli bir karar vermenize yardımcı olur.

Bir bakışta ek görünürlük için otomatik olay adlandırma, etkilenen uç nokta sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine göre olay adları oluşturur. Bu, olayın kapsamını hızlı bir şekilde anlamanıza olanak tanır.

Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*

> [!NOTE]
> Otomatik olay adlandırmanın dağıtımından önce var olan olayların adı değiştirilmez.

Olay kuyruğu, uygulandığında ortamınızdaki tüm mevcut olayların kapsamlı bir taramasını gerçekleştirmenize veya belirli bir senaryoya veya tehdide odaklanmaya karar vermenize olanak tanıyan birden çok filtreleme seçeneği de sunar. Olay kuyruğuna filtre uygulamak, hangi olayın hemen ilgilenilmesi gerektiğini belirlemeye yardımcı olabilir. 

Olay listesinin üstündeki **Filtreler** listesi, geçerli olarak uygulanan filtreleri gösterir.

## <a name="available-filters"></a>Kullanılabilir filtreler

Filtrelenmiş bir olay kümesi belirttiğiniz filtre bölmesini görmek  için varsayılan olay kuyruğundan **Filtre'yi** seçebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Microsoft 365 Defender portalında olay kuyruğunun Filtreler bölmesi." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Filtre **bölmesini,** olay listesinin üzerindeki **Filtreler** listesinden herhangi birini seçerek de görebilirsiniz.

Bu tabloda, kullanılabilen filtre adları listelenir.

| Filtre adı | Açıklama |
|:-------|:-----|
| Durum | **Yeni**, Sürüyor veya **Çözümlendi'yi** seçin.  |
| Önem | Bir olayın önem derecesi, varlıklarınız üzerindeki etkisini gösterir. Önem derecesi ne kadar yüksek olursa, etki o kadar büyük olur ve genellikle en acil dikkati gerektirir. **Yüksek**, **Orta**, **Düşük** veya **Bilgilendirici'yi** seçin. |
| Olay ataması | Atanan kullanıcıyı veya kullanıcıları seçin. |
| Birden çok hizmet kaynağı  | Filtrenin birden fazla hizmet kaynağı için olup olmadığını belirtin. |
| Hizmet kaynakları  | Şu uyarıları içeren olayları belirtin: Uygulama İdaresi, Microsoft 365 Defender, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender, Microsoft Defender for Cloud Apps. |
| Etiketler | Listeden bir veya birden çok etiket adı seçin. |
| Birden çok kategori  | Filtrenin birden fazla kategori için olup olmadığını belirtin. |
| Kategori | Görülen belirli taktiklere, tekniklere veya saldırı bileşenlerine odaklanmak için kategorileri seçin. |
| Varlık | Kullanıcı, cihaz, posta kutusu veya uygulama adı gibi bir varlığın adını belirtin. |
| Veri duyarlılığı | Bazı saldırılar, hassas veya değerli verileri sızdırmak için hedeflemeye odaklanır. Belirli duyarlılık etiketleri için bir filtre uygulayarak hassas bilgilerin ele geçirilip geçirilmemiş olabileceğini hızla belirleyebilir ve bu olayları ele geçirmeyi önceliklendikleyebilirsiniz. <br><br> Bu filtre yalnızca [Microsoft Purview Information Protection duyarlılık etiketlerini](../../compliance/sensitivity-labels.md) uyguladığınızda bilgileri görüntüler. |
| Cihaz grupları | [Bir cihaz grubu](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) adı belirtin. |
| İşletim sistemi platformu | Cihaz işletim sistemlerini belirtin. |
| Sınıflandırma | İlgili uyarıların sınıflandırma kümesini belirtin. |
| Otomatik araştırma durumu | Otomatik araştırmanın durumunu belirtin.  |
| İlişkili tehdit | Adlandırılmış bir tehdit belirtin.  |
| Aktör | Adlandırılmış bir tehdit aktörü belirtin.  |
|||

Varsayılan filtre, **Durumu Yeni** ve **Devam Ediyor** olan ve **Düşük**, **Orta** veya **Yüksek** önem derecesine sahip tüm uyarıları ve olayları göstermektir.

**Filtreler** listesindeki bir filtrenin adında **X** işaretini seçerek filtreyi hızla kaldırabilirsiniz. 

## <a name="save-custom-filters-as-urls"></a>Özel filtreleri URL olarak kaydetme

Olaylar kuyruğunda yararlı bir filtre yapılandırdıktan sonra, tarayıcı sekmesinin URL'sine yer işareti ekleyebilir veya başka bir şekilde web sayfasına, Word belgesine veya tercih ettiğiniz bir yere bağlantı olarak kaydedebilirsiniz. Bu, olay kuyruğunun önemli görünümlerine tek tıklamayla erişmenizi sağlayacaktır, örneğin:

- Yeni olaylar
- Yüksek önem dereceli olaylar
- Atanmamış olaylar
- Yüksek önem derecesi, atanmamış olaylar
- Bana atanan olaylar
- Bana ve Uç Nokta için Microsoft Defender için atanan olaylar
- Belirli bir etiket veya etikete sahip olaylar
- Belirli bir tehdit kategorisine sahip olaylar
- Belirli bir ilişkili tehdide sahip olaylar
- Belirli bir aktörle ilgili olaylar

Yararlı filtre görünümleri listenizi DERleyip URL olarak depoladıktan sonra, kuyruğunuzdaki olayları hızlı bir şekilde işlemek ve önceliklerini ayarlamak ve bunları sonraki atama ve analiz için [yönetmek](manage-incidents.md) için kullanabilirsiniz.

## <a name="search-for-incidents"></a>Olayları arama

Olay listesinin üstündeki **Ad veya kimlik ara** kutusundan olay kimliğini veya olay adını yazabilirsiniz. Arama sonuçları listesinden bir olay seçtiğinizde, Microsoft 365 Defender portalı olayın özelliklerini içeren ve [araştırmanızı](investigate-incidents.md) başlatabileceğiniz yeni bir sekme açar.

## <a name="search-for-impacted-assets"></a>Etkilenen varlıkları arama

Bir varlığı&mdash; kullanıcı, cihaz, posta kutusu veya uygulama adı&mdash; olarak adlandırabilir ve tüm ilgili olayları bulabilirsiniz. 

## <a name="specify-a-time-range"></a>Zaman aralığı belirtme

Varsayılan olay listesi, son altı ay içinde gerçekleşen olaylara yöneliktir. Takvim simgesinin yanındaki açılan kutudan şunları seçerek yeni bir zaman aralığı belirtebilirsiniz:

 - 1 gün
 - 3 gün
 - 1 hafta
 - 30 gün
 - 30 gün
 - 6 ay
 - Hem tarihleri hem de saatleri belirtebileceğiniz özel bir aralık

## <a name="next-steps"></a>Sonraki adımlar

Hangi olayın en yüksek önceliğe sahip olduğunu belirledikten sonra seçin ve:

- Etiketler, atama, hatalı pozitif olaylar ve açıklamalar için anında çözüm için olayın özelliklerini [yönetin](manage-incidents.md).
- [Araştırmalarınızı](investigate-incidents.md) başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Olaylara genel bakış](incidents-overview.md)
- [Olayları yönetin](manage-incidents.md)
- [Olayları araştırın](investigate-incidents.md)
