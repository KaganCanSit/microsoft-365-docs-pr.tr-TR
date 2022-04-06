---
title: Uyarı Uç Nokta için Microsoft Defender araştırma
description: Anızı etkileyen uyarılar, bunların ne anlama gelenler ve bunların nasıl çözülecekleri ile ilgili ayrıntılı bilgi almak için araştırma seçeneklerini kullanın.
keywords: araştırma, araştırma, cihazlar, cihaz, uyarılar sırası, pano, IP adresi, dosya, gönderme, gönderiler, derin çözümleme, zaman çizelgesi, arama, etki alanı, URL, IP
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
ms.openlocfilehash: e2ebdffa171266fdc0ec77047c9fecc5be9e56ba
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471175"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>E-postada uyarıları Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Anızı etkileyen uyarıları araştırmanız, bunların ne anlama gelen olduğunu ve bunların nasıl çözülecek olduğunu anlamanız gerekir.

Uyarı sayfasına gitmek için uyarılar sırasından bir uyarı seçin. Bu görünüm uyarı başlığını, etkilenen varlıkları, yan ayrıntılar bölmesini ve uyarı yazını içerir.

Uyarı sayfasından, uyarı ağacı görünümünün altındaki etkilenen varlıkları veya varlıkları seçerek araştırmanıza başlayabilirsiniz. Ayrıntılar bölmesi, seçtiğiniz konuyla ilgili ek bilgilerle otomatik olarak gösterilir. Burada ne tür bilgiler görüntü ola görüntülemek için, Bu [makalenin Tamam görünümünde uyarıları Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Uyarı hikayelerini kullanarak araştırma

Uyarının neden tetiklendiğinden, öncesinde ve sonrasında olan ilgili olayların yanı sıra diğer ilgili varlıklar da uyarının ayrıntılarını içerir.

Varlıklar tıklanabilirdir ve uyarı olmayan her varlık, o varlık kartının sağ tarafındaki genişletme simgesi kullanılarak genişletilebilir. Odakta olan varlık, bu varlık kartının sol tarafında mavi bir şeritle ve başlığında ilk başta odakta olacak şekilde uyarı gelecektir.

Ayrıntıları bir bakışta görmek için varlıkları genişletin. Bir varlık seçmek, ayrıntılar bölmesinin bağlamını bu varlığa geçirerek daha fazla bilgi gözden geçirmenizi ve o varlığı yönetmenizi sağlar. Varlık *kartının* sağ tarafından ... seçisinde, o varlık için kullanılabilir tüm eylemler ortaya çıkar. Aynı eylemler, o varlık odaktayken ayrıntılar bölmesinde gösterilir.

> [!NOTE]
> Uyarı anlatısı bölümü, seçtiğiniz uyarıdan önce veya sonra görünen aynı yürütme ağacıyla ilgili ek uyarılar içeren birden fazla uyarı içerebilir.

:::image type="content" source="images/alert-story-tree.png" alt-text="Odakta bir uyarının ve genişletilmiş bazı kartların olduğu uyarı anlatısı" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Ayrıntılar bölmesinden eyleme geçin

İlginizi olan bir varlık seçtikten sonra, ayrıntılar bölmesi mevcut olduğunda seçili varlık türü, tarihi bilgiler ve bu varlık üzerinde doğrudan uyarı sayfasından işlem yapmak üzere denetimler sunacak şekilde değişir.

Incelemeyi tamamlaydıktan sonra, başlama uyarıya geri gidin, uyarının durumunu Çözümlendi olarak işaret edin ve  Bunu Yanlış uyarı veya Doğru uyarısı olarak  **sınıflandıryın**. Uyarıların sınıf ayarı, bu özelliğin daha fazla doğru uyarı ve daha az yanlış uyarı sağlama özelliğine yardımcı olur.

Bu uyarıyı doğru uyarı olarak sınıflandırsanız, aşağıdaki resimde gösterildiği gibi bir karar da seçin.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Çözümlenen uyarının ve açılan karartma açılan listesinde genişletilmiş ayrıntılar bölmesi" lightbox="images/alert-details-resolved-true.png":::

İş hattı uygulamasında yanlış uyarıyla karşılaşıyorsanız, gelecekte bu uyarı türünden kaçınmak için bir gizleme kuralı oluşturun.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Gösterme kuralının vurgulu olduğu ayrıntılar bölmesinde eylemler ve sınıflandırma" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Yukarıda açıklanmaz bir sorunla yaşıyorsanız geri bildirim sağlamak veya 🙂 bir destek bileti açmak için düğmeyi kullanın.


## <a name="related-topics"></a>İlgili konular
- [Yeni Uyarı kuyruğu Uç Nokta için Microsoft Defender ve düzenleme](alerts-queue.md)
- [Uyarı Uç Nokta için Microsoft Defender yönetme](manage-alerts.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Defender'da kullanıcı hesabını araştırma](investigate-user.md)


