---
title: Olaylar kuyruğu görüntüleme ve düzenleme
ms.reviewer: ''
description: Olay listesine bakın ve listeyi sınırlandıracak filtreler uygulayarak daha odaklanmış bir görünüm elde etmeyi öğrenin.
keywords: görüntüleme, düzenleme, olaylar, toplama, soruşturmalar, kuyruk, ttp
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: df5cbf5297a17dafb80a93ed49c7f7d81bc49d68
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474387"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>Olay kuyruğu Uç Nokta için Microsoft Defender ve düzenleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Olaylar **sırası,** ağ bağlantısında yer alan cihazlardan bayrakla işaretlenmiş olay koleksiyonunu gösterir. Bilgili bir siber güvenlik yanıtı kararı önceliklerini belirlemek ve oluşturmak için olaylarda sıralamanıza yardımcı olur.

Varsayılan olarak, kuyrukta son 30 günde görülen olaylar görüntülenir ve en son olay listenin en üstünde yer alıyor ve en son olayları önce görmene yardımcı olur.

Olaylar sırası görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır. 

Üst gezintiden şunlarıabilirsiniz:
- Sütunları eklemek veya kaldırmak için sütunları özelleştirme 
- Sayfa başına görüntülemek istediğiniz öğe sayısını değiştirme
- Sayfa başına gösterecek öğeleri seçme
- Batch-select the incidents to assign 
- Sayfalar arasında gezinme
- Filtre uygulama

:::image type="content" source="images/atp-incident-queue.png" alt-text="Olaylar sırası" lightbox="images/atp-incident-queue.png":::

## <a name="sort-and-filter-the-incidents-queue"></a>Olayları sırala ve filtrele
Olay listesini sınırlandırarak daha odaklanmış bir görünüm elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="severity"></a>Önem Derecesi

Olay önem derecesi | Açıklama
:---|:---
Yüksek </br>(Red) | Çoğunlukla gelişmiş kalıcı tehditlerle (APT) ilişkili tehditlerdir. Bu olaylar cihazlara iyi bir zarar verebilir ve önem derecesine bağlı olarak yüksek risklidir.
Orta </br>(Orange) | Kuruluşta anormal kayıt defteri değişikliği, şüpheli dosyaların yürütülmesi ve saldırı aşamalarına özgü gözlemlenen davranışlar gibi nadiren gözlenen tehdit.
Düşük </br>(Sarı) | Yaygın kötü amaçlı yazılımla ve bilgisayar korsanlığı araçlarıyla ilişkilendirilmiş olan ve kuruluşa yönelik gelişmiş bir tehdit anlamına gelmez.
Bilgilendirme </br>(Gri) | Bilgilendirme olayları, ağa zarar verir gibi kabul edilir ancak takip etmek iyi olabilir.

## <a name="assigned-to"></a>Atanan
Herkese veya size atananları seçerek listeyi filtrelemeyi seçebilirsiniz.

### <a name="category"></a>Kategori
Olaylar, siber güvenlikle ilgili kill zincirinin içinde olduğu evrenin açıklamasına göre kategorilere ayrılmıştır. Bu görünüm, tehdit analistini bağlama göre dağıtım için öncelik, aciliyet ve karşılık gelen yanıt stratejisini belirlemeye yardımcı olur.

### <a name="status"></a>Durum
Hangilerinin etkin veya çözümlenmiş olduğunu görmek için, gösterilen olay listesini durumlarına göre sınırlandırabilirsiniz.

### <a name="data-sensitivity"></a>Veri duyarlılığı
Duyarlılık etiketleri içeren olayları göstermek için bu filtreyi kullanın.

## <a name="incident-naming"></a>Olay adlandırma

Olayın kapsamını bir bakışta anlamak için, olay adları etkilenen uç nokta sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine göre otomatik olarak oluşturulur.

Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*

> [!NOTE]
> Otomatik olay adlandırmanın daha önce var olan olayları, adını korur.


## <a name="see-also"></a>Ayrıca bkz.
- [Olay sırası](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Olayları yönetin](manage-incidents.md)
- [Olayları araştırın](investigate-incidents.md)

