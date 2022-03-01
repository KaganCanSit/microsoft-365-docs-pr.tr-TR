---
title: Uç nokta uyarıları için Microsoft Defender'ı araştırma
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
ms.openlocfilehash: f228d0ca44589b9c140226c2b39984c717c7d9f8
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011889"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da uyarıları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Anızı etkileyen uyarıları araştırmanız, bunların ne anlama gelen olduğunu ve bunların nasıl çözülecek olduğunu anlamanız gerekir.

Uyarı sayfasına gitmek için uyarılar sırasından bir uyarı seçin. Bu görünüm uyarı başlığını, etkilenen varlıkları, yan ayrıntılar bölmesini ve uyarı yazını içerir.

Uyarı sayfasından, uyarı ağacı görünümünün altındaki etkilenen varlıkları veya varlıkları seçerek araştırmanıza başlayabilirsiniz. Ayrıntılar bölmesi, seçtiğiniz konuyla ilgili ek bilgilerle otomatik olarak gösterilir. Burada ne tür bilgiler görüntüyebilirsiniz? Görmek için Bkz [. Uç Nokta için Microsoft Defender'da uyarıları gözden geçirme](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Uyarı hikayelerini kullanarak araştırma

Uyarının neden tetiklendiğinden, öncesinde ve sonrasında olan ilgili olayların yanı sıra diğer ilgili varlıklar da uyarının ayrıntılarını içerir.

Varlıklar tıklanabilirdir ve uyarı olmayan her varlık, o varlık kartının sağ tarafındaki genişletme simgesi kullanılarak genişletilebilir. Odakta olan varlık, bu varlık kartının sol tarafında mavi bir şeritle ve başlığında ilk başta odakta olacak şekilde uyarı gelecektir.

Ayrıntıları bir bakışta görmek için varlıkları genişletin. Bir varlık seçmek, ayrıntılar bölmesinin bağlamını bu varlığa geçirerek daha fazla bilgi gözden geçirmenizi ve o varlığı yönetmenizi sağlar. Varlık *kartının* sağ tarafından ... seçisinde, o varlık için kullanılabilir tüm eylemler ortaya çıkar. Aynı eylemler, o varlık odaktayken ayrıntılar bölmesinde gösterilir.

> [!NOTE]
> Uyarı anlatısı bölümü, seçtiğiniz uyarıdan önce veya sonra görünen aynı yürütme ağacıyla ilgili ek uyarılar içeren birden fazla uyarı içerebilir.

![Odaklanan bir uyarı ve genişletilmiş bazı kartlar ile bir uyarı hikayesi örneği.](images/alert-story-tree.png)

## <a name="take-action-from-the-details-pane"></a>Ayrıntılar bölmesinden eyleme geçin

İlginizi olan bir varlık seçtikten sonra, ayrıntılar bölmesi mevcut olduğunda seçili varlık türü, tarihi bilgiler ve bu varlık üzerinde doğrudan uyarı sayfasından işlem yapmak üzere denetimler sunacak şekilde değişir.

Incelemeyi tamamlaydıktan sonra, başlama uyarıya geri gidin, uyarının durumunu Çözümlendi olarak işaret edin ve  Bunu Yanlış uyarı veya Doğru uyarısı olarak  **sınıflandıryın**. Uyarıların sınıf ayarı, bu özelliğin daha fazla doğru uyarı ve daha az yanlış uyarı sağlama özelliğine yardımcı olur.

Bu uyarıyı doğru uyarı olarak sınıflandırsanız, aşağıdaki resimde gösterildiği gibi bir karar da seçin.

![Çözümlenmiş uyarının ve karartma açılan penceresinin genişletilen bölümü.](images/alert-details-resolved-true.png)

İş hattı uygulamasında yanlış uyarıyla karşılaşıyorsanız, gelecekte bu uyarı türünden kaçınmak için bir gizleme kuralı oluşturun.

![Gizleme kuralı vurgulanmış olarak ayrıntılar bölmesinde eylemler ve sınıflandırma.](images/alert-false-suppression-rule.png)

> [!TIP]
> Yukarıda açıklanmaz bir sorunla yaşıyorsanız geri bildirim sağlamak veya 🙂 bir destek bileti açmak için düğmeyi kullanın.


## <a name="related-topics"></a>İlgili konular
- [Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Defender'da kullanıcı hesabını araştırma](investigate-user.md)


