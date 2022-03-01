---
title: Microsoft 365 Defender'de olayları öncelik Microsoft 365 Defender
description: başka bir e-postada olay sırasındaki olayları filtrelemeyi Microsoft 365 Defender
keywords: olay, kuyruk, genel bakış, cihazlar, kimlikler, kullanıcılar, posta kutusu, e-posta, olaylar, çözümleme, yanıt, değerlendirme
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: fafb48af3aa0c38146073a0682323496bc0431e2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015534"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Microsoft 365 Defender'de olayları öncelik Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender çözümlemeleri uygular ve farklı ürünlerden ilgili uyarıları ve otomatik soruşturmaları bir olay haline toplar. Microsoft 365 Defender ayrıca, kullanıcıların tüm ürün paketinde yer alan  end-end görünürlükleri nedeniyle kötü amaçlı olarak tanımlanlan etkinlikler Microsoft 365 Defender benzersiz uyarılar tetikler. Bu görünüm, güvenlik analistlerine daha kapsamlı bir saldırı hikayesi sunar ve bu hikaye, güvenlik analistlerine kuruluş genelindeki karmaşık tehditleri daha iyi an ve yardımcı olur.

Olay **sırası,** cihazlar, kullanıcılar ve posta kutuları arasında oluşturulmuş bir olay koleksiyonunu gösterir. Bilgili bir siber güvenlik yanıtı kararı önceliklerini belirlemek ve oluşturmak için olaylarda sıralamanıza yardımcı olur. Buna, olay triyaksı da bilinir.

Microsoft 365 Defender portalının hızlı **başlatılmasında Olaylar & veya >'den** olay <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sırasına Microsoft 365 Defender</a>. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Olay sırası örneği." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

En **son olaylar ve uyarılar** bölümünde, alınan uyarı sayısının ve son 24 saat içinde oluşturulan olay sayısının grafiği gösterilir.

Varsayılan olarak, yeni portalda Microsoft 365 Defender sırası son altı ayda görülen olayları görüntüler. En son olay listenin en üstünde yer alıyor, böylece ilk olarak siz de onu görüyorsunuz.

Olay sırasında özelleştirilebilir sütunlar vardır (Sütunları **seç'i** seçerek), olayın farklı özelliklerini veya etkileyen varlıkları görünür haletebilirsiniz. Bu, çözümleme için olayları önceliklendirme konusunda bilinçli bir karar alamanıza yardımcı olur.

Bir bakışta daha fazla görünürlük için otomatik olay adlandırma, etkilenen uç noktaların sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine dayalı olarak olay adları üretir. Bu, olayın kapsamını hızla anlamana olanak sağlar.

Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*

> [!NOTE]
> Otomatik olay adlandırmanın adı değişmeden önce mevcut olan olayları değiştirmez.

Olay sırası, uygulandığında ortamınız içinde var olan tüm olayları kapsamlı olarak süpürmenizi veya belirli bir senaryoya veya tehdite odaklanmaya karar vermenizi sağlayan birden çok filtreleme seçeneği de sunar. Olay sırasında filtre uygulamak, hangi olayın acil dikkat gerektirdiğini belirlemeye yardımcı olabilir. 

## <a name="available-filters"></a>Kullanılabilir filtreler

Varsayılan olay sırasında Filtreler'i seçerek filtrelenmiş bir olay kümesi görüntüleyebilirsiniz. Filtreler bölmesini görüntüleyebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Olay sırası için filtreler bölmesi örneği." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Varsayılan filtre, Yeni ve Sürüyor durumuna sahip tüm uyarıları **ve** **olayları göstermektir** .

Bu tabloda, kullanılabilen filtre adları listelenmiş olur.

| Filtre adı | Açıklama |
|:-------|:-----|
| Durum | Yeni **,** Sürüyor **veya Çözümlendi'yi** **seçin**. |
| Önem Derecesi | Bir olayın önem derecesi, varlığınız üzerindeki etkisini gösterir. Önem derecesi ne kadar yüksek ise, etkisi o kadar büyük olur ve genellikle en acil dikkat gerektirir. Yüksek **,** **Orta,** Düşük **veya** **Bilgilendirme'yi seçin**. |
| Olay ataması | Herkese atanan, Bana atanan veya Atanmamış'ı seçin. |
| Birden çok hizmet kaynağı  | Filtrenin birden çok hizmet kaynağı için geçerli olup olmadığını belirtin. |
| Hizmet kaynakları  | Yalnızca uyarı içeren olayları görmek için filtre kullanın: Uygulama Yönetimi, Microsoft 365 Defender, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender. |
| Etiketler | Listeden bir veya birden çok etiket adı seçin. |
| Birden çok kategori  | Filtrenin birden çok kategori için olup olmadığını belirtin. |
| Kategoriler | Görülen belirli taktiklere, tekniklere veya saldırı bileşenlerine odaklanmak için kategorileri seçin. |
| işletim sistemi platformu | İşletim sistemine göre olay sırası görünümünü sınırlandırabilirsiniz. |
| Sınıflandırma | Olayları, ilgili uyarıların sınıflandırmaları kümesine göre filtrele. Doğru **uyarı**, Yanlış **uyarılar veya Ayarlanmaz'ı** **seçin**. |
| İnceleme durumu | Olayları otomatik araştırmanın durumuna göre filtrele.  |
| İlişkili tehdit | Olayları adlandırılmış bir tehditle filtrele.  |
| Yerkarak | Olayları adlandırılmış bir tehditci tarafından filtrele.  |
| Veri duyarlılığı | Bazı saldırılar hassas veya değerli verileri imha etmek için hedefe odaklanır. Olaya hassas verilerin dahil olup olmadığını görmek üzere bir filtre uygulayarak, hassas bilgilerin ele geçirildiklerinden hemen kararlaştırabilirsiniz ve bu olaylara öncelik ve önceliklerini belirlemeniz gerekir. <br><br>Bu filtrenin kullanılabilir durumda Microsoft Bilgi Koruması açıksa kullanılabilir.|
|||

## <a name="save-defined-filters-as-urls"></a>Tanımlı filtreleri URL olarak kaydetme

Olay sırasında yararlı bir filtre yapılandırdıktan sonra, tarayıcı sekmesinin URL'sine yer işareti ekleyebilirsiniz veya bunu bir Web sayfasına, Word belgesine veya istediğiniz yere bağlantı olarak kaydedebilirsiniz. Bu, olay kuyruğuna tek tıklamayla erişim sağlar; örneğin:

- Yeni olaylar
- Yüksek öneme sahip olaylar
- Atanmamış olaylar
- Yüksek önem düzeyi olan, atanmamış olaylar
- Bana atanan olaylar
- Bana ve Uç Nokta için Microsoft Defender'a atanan olaylar
- Belirli bir etiket veya etikete sahip olaylar
- Belirli bir tehdit kategorisine sahip olaylar
- Belirli bir ilişkili tehdit ile ilgili olaylar
- Belirli bir actor'a sahip olaylar

Kullanışlı filtre görünümlerini LISTENIZI URL olarak derledik ve depoladıktan sonra, bunu kullanarak kuyrukta meydana gelen olayları hızla işleyen, önceliklerini belirlemek ve sonraki [](manage-incidents.md) atama ve çözümlemelerde bunları yönetmek için kullanabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

En yüksek önceliğin hangi olayı gerektirdiğini belirledikten sonra, o olayı seçin ve:

- [Etiketler](manage-incidents.md) , atama, hatalı pozitif olaylar için anında çözüm ve açıklamalar için olayın özelliklerini yönetin.
- Araştırmanıza [başlar.](investigate-incidents.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Olaylara genel bakış](incidents-overview.md)
- [Olayları yönetme](manage-incidents.md)
- [Olayları araştırma](investigate-incidents.md)
