---
title: Olayları iş yer Microsoft 365 Defender
description: Nasıl atamayı, durumu güncelleştirmeyi,
keywords: olay, olaylar, çözümleme, yanıt, uyarılar, ilişkili uyarılar, atama, güncelleştirme, durum, yönetme, sınıflandırma, microsoft, 365, m365
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
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 14332b2787b59e2ef192741dc97e59a7c7cb5418
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499517"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Olayları iş yer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Olay yönetimi, olay iş akışınıza en uygun zamanı en iyi duruma getirmek ve tehditlere daha hızlı bir şekilde müdahale etmek ve tehditlere karşı daha hızlı bir şekilde müdahale etmek için önem taşıyor.

Microsoft 365 Defender portalının (security.microsoft.com) hızlı başlatmada Olaylar **&** veya Olaylar'> olayları [yönetebilirsiniz](https://security.microsoft.com). İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Microsoft 365 Defender portalında Olaylar sayfası" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Olaylarınızı şöyle yönetebilirsiniz:

- [Olay adını düzenleme](#edit-the-incident-name)
- [Olay etiketleri ekleme](#add-incident-tags)
- [Olayı kullanıcı hesabına atama](#assign-an-incident)
- [Bunları çözme](#resolve-an-incident)
- [Sınıflandırmasını belirtme](#specify-the-classification)
- [Açıklama ekleme](#add-comments)

Olayları, Bir olayın Olay yönetme **bölmesinden** yönetebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Microsoft 365 Defender portalında Olayı yönet bölmesi" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Bu bölmeyi, şu bölmede **yer alan Olayı** yönet bağlantısından görüntüleyebilirsiniz:

- Olay sırasındaki bir olayın Özellikler bölmesi.
- **Bir** olayın özet sayfası.

Uyarıları bir olaydan diğerine taşımak istediğiniz durumlarda, bunu da Uyarılar sekmesinden yapmaya devam edersiniz; böylece ilgili tüm  uyarıları içeren daha büyük veya daha küçük bir olay oluşturulur.

## <a name="edit-the-incident-name"></a>Olay adını düzenleme

Microsoft 365 Defender, etkilenen uç noktalarının sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine dayalı olarak otomatik olarak bir ad atar. Bu, olayın kapsamını hızla anlamana olanak sağlar. Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*

Olayı yönet bölmesindeki Olay adı **alanından** olay **adını düzenleyebilirsiniz** .

> [!NOTE]
> Otomatik olay adlandırma özelliğinin adı devre dışı olmadan önce mevcut olan olaylar, bu olayları korur.

## <a name="add-incident-tags"></a>Olay etiketleri ekleme

Örneğin, bir olay grubunu ortak bir özel durumla bayrak eklemek için, bir olaya özel etiketler ebilirsiniz. Belirli bir etiket içeren tüm olaylar için sonradan olay kuyruğuna filtre ebilirsiniz.

Yazmaya başladığınızda, daha önce kullanılmış ve seçilmiş etiketler listesinden seçim yapmaya başlayabilirsiniz.

## <a name="assign-an-incident"></a>Olay atama

Henüz bir olay atanmamışsa, Atanacak yer **kutusunu seçerek** kullanıcı hesabını belirtebilirsiniz. Bir olayı yeniden atamak için, hesap adının yanındaki "x" öğesini ve ardından Ata kutusunu seçerek geçerli atama **hesabını** kaldırın. Bir olayın sahipliğini atamak, ilgili tüm uyarılara aynı sahipliği atar.

Olay kuyruğuna filtre ataarak size atanmış olayları listesini eldeebilirsiniz. 

1. Olay sırasında Filtreler'i **seçin**.
2. Olay atama **bölümünde, Hepsini** **seç'i ve Bana** **atanan'ı seçin**.
3. **Uygula'ya** tıklayın ve filtreler **bölmesini** kapatın.

Ardından, size atanmış olay listesini hızla görmek için, sonuçta elde edilen URL'yi tarayıcınızda yer işareti olarak kaydedebilirsiniz.

## <a name="resolve-an-incident"></a>Bir olayı çözme

Olay düzeltildise, iki durumlu **düğmeyi sağa taşımak** için Olayı çöz'e seçin. Bir olayı çözmenin, olayla ilgili tüm bağlantılı ve etkin uyarıları da çözmediğini unutmayın.

Çözümlenmezse bir olay Etkin olarak **görüntülenir**.

## <a name="specify-the-classification"></a>Sınıflandırmayı belirtme

Sınıflandırma **alanında** , olayın aşağıdaki gibi bir olay olup olmadığını belirtirsiniz:

- **Ayarlanmaz** (varsayılan).
- **Bir tehdit** türünde gerçek pozitif sonuç. Gerçek bir tehditi doğru gösteren olaylar için bu sınıflandırmayı kullanın. Tehdit türünü belirtmek, güvenlik ekibinin tehdit düzenlerini görmelerine ve organizasyonunu onlardan savunmaya yardımcı olur.
- **Bilgilendirme, etkinlik türüyle** beklenen etkinlik. Güvenlik testleri, kırmızı ekip etkinliği ve güvenilir uygulamalarla kullanıcılardan beklenen alışılmışın dışında bir davranış için olayları sınıflandırmak üzere bu kategorideki seçenekleri kullanın.
- **Teknik olarak** yanlış ve yanıltıcı olduğundan, sizin karartılan olay türleri için hatalı pozitif sonuçlar yoksayılabilir.

Olayları sınıflama, durumunu ve türünü belirtme, zaman içinde daha iyi Microsoft 365 Defender algılama belirlemesi sağlamak için gerekli ayarlamaları yapmak için gerekli ayarlamaları yapmak için yardımcı olur.

## <a name="add-comments"></a>Açıklama ekleme

Açıklama alanı içeren bir olayda birden **çok açıklama ebilirsiniz** . Her açıklama, olayın geçmiş olaylarına eklenir. Özet sayfasındaki Açıklamalar ve geçmiş bağlantısından bir **olayın açıklamalarını ve** **geçmişini görebilirsiniz.**

## <a name="next-steps"></a>Sonraki adımlar

Yeni olaylar için araştırmanıza [başlayabilirsiniz](investigate-incidents.md).

süreç içinde yaşanan olaylarda, incelemenize devam [etmek gerekir](investigate-incidents.md).

Çözülen olaylarda, olay [sonrası inceleme gerçekleştirin](first-incident-post.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olaylara öncelik belirleyin](incident-queue.md)
- [Olayları araştırın](investigate-incidents.md)
