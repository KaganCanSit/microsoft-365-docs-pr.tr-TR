---
title: Uç Nokta için Microsoft Defender uyarılarını araştırma
description: Ağınızı etkileyen uyarılar, bunların ne anlama gelenleri ve bunların nasıl çözüleceğini öğrenmek için araştırma seçeneklerini kullanın.
keywords: araştırma, araştırma, cihazlar, cihaz, uyarılar kuyruğu, pano, IP adresi, dosya, gönderme, gönderimler, derin analiz, zaman çizelgesi, arama, etki alanı, URL, IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e4d379ee476276d24b683878bc4978addf220ced
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665810"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'de uyarıları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Ağınızı etkileyen uyarıları araştırın, bunların ne anlama geldiğini ve bunların nasıl çözümlendiğini anlayın.

Uyarı sayfasına gitmek için uyarılar kuyruğundan bir uyarı seçin. Bu görünüm uyarı başlığını, etkilenen varlıkları, ayrıntılar yan bölmesini ve uyarı hikayesini içerir.

Uyarı sayfasından, etkilenen varlıkları veya uyarı hikayesi ağaç görünümü altındaki varlıklardan herhangi birini seçerek araştırmanıza başlayın. Ayrıntılar bölmesi, ne seçtiğiniz hakkında daha fazla bilgiyle otomatik olarak doldurulur. Burada ne tür bilgiler görüntüleyebileceğinizi görmek için [Uç Nokta için Microsoft Defender uyarılarını gözden geçirme](/microsoft-365/security/defender-endpoint/review-alerts) bölümüne bakın.

## <a name="investigate-using-the-alert-story"></a>Uyarı hikayesini kullanarak araştırma

Uyarı hikayesi, uyarının neden tetiklendiğini, hem önce ve sonra gerçekleşen ilgili olayları hem de diğer ilgili varlıkları ayrıntılarıyla açıklar.

Varlıklara tıklanabilir ve uyarı olmayan her varlık, söz konusu varlığın kartının sağ tarafındaki genişlet simgesi kullanılarak genişletilebilir. Odaktaki varlık, o varlığın kartının sol tarafında mavi bir şeritle gösterilir ve başlıkta uyarı ilk başta odakta olur.

Ayrıntıları bir bakışta görüntülemek için varlıkları genişletin. Bir varlık seçildiğinde ayrıntılar bölmesinin bağlamı bu varlığa geçer ve daha fazla bilgiyi gözden geçirmenize ve bu varlığı yönetmenize olanak sağlar. Varlık kartının sağındaki *...* seçildiğinde söz konusu varlık için kullanılabilecek tüm eylemler gösterilir. Bu varlık odaktayken ayrıntılar bölmesinde de aynı eylemler görünür.

> [!NOTE]
> Uyarı hikayesi bölümünde birden fazla uyarı bulunabilir ve seçtiğiniz uyarıdan önce veya sonra aynı yürütme ağacıyla ilgili ek uyarılar görüntülenir.

:::image type="content" source="images/alert-story-tree.png" alt-text="odakta bir uyarı ve bazı genişletilmiş kartlar bulunan bir uyarı hikayesi" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Ayrıntılar bölmesinden eylem gerçekleştirme

İlgilendiğiniz bir varlığı seçtikten sonra, ayrıntılar bölmesi seçili varlık türüyle ilgili bilgileri, kullanılabilir olduğunda geçmiş bilgileri görüntüleyecek şekilde değişir ve doğrudan uyarı sayfasından bu varlık üzerinde **işlem yapmak** için denetimler sunar.

Araştırmayı tamamladıktan sonra, başlattığınız uyarıya dönün, uyarının durumunu **Çözüldü** olarak işaretleyin ve **Yanlış uyarı** veya **Doğru uyarı** olarak sınıflandırın. Uyarıları sınıflandırmak, daha doğru uyarılar ve daha az yanlış uyarı sağlamak için bu özelliği ayarlamaya yardımcı olur.

Bunu gerçek bir uyarı olarak sınıflandırırsanız, aşağıdaki resimde gösterildiği gibi bir belirleme de seçebilirsiniz.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Çözümlenmiş uyarının ve belirleme açılan listesinin genişletilmiş olduğu ayrıntılar bölmesi" lightbox="images/alert-details-resolved-true.png":::

bir iş kolu uygulamasıyla yanlış uyarıyla karşılaşıyorsanız, gelecekte bu tür uyarılardan kaçınmak için bir engelleme kuralı oluşturun.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Ayrıntılar bölmesindeki eylemler ve sınıflandırma ve gizleme kuralı vurgulanmış" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Yukarıda açıklanmayan sorunlarla karşılaşıyorsanız geri bildirim sağlamak veya destek bileti açmak için düğmeyi 🙂 kullanın.

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta için Microsoft Defender Uyarıları kuyruğu görüntüleme ve düzenleme](alerts-queue.md)
- [Uç Nokta için Microsoft Defender uyarılarını yönetme](manage-alerts.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş bir dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Defender listesindeki cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş bir IP adresini araştırma](investigate-ip.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş bir etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Defender'da kullanıcı hesabını araştırma](investigate-user.md)
