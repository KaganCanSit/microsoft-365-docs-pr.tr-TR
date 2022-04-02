---
title: Olay Uç Nokta için Microsoft Defender yönetme
description: Olayları yönetmek için görev atama, durumunu güncelleştirme veya sınıflandırmayı ayarlama.
keywords: olaylar, yönetme, atama, durum, sınıflandırma, doğru uyarı, yanlış uyarı
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.technology: mde
ms.openlocfilehash: a84f7ba72acb4caf3e229f0bed4d997e123cc7ae
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466223"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>Olay Uç Nokta için Microsoft Defender yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Olayları yönetmek, her siber güvenlik operasyonlarının önemli bir parçasıdır. Olayları yönetmek için, Olaylar kuyruğundan veya **Olaylar yönetim** bölmesinden **bir olay seçin**. 


Olaylar sırasından bir **olay seçerek** , ayrıntılar için **olay sayfasını** açabilirsiniz.

:::image type="content" source="images/atp-incidents-mgt-pane-updated.png" alt-text="Olay yönetim bölmesi" lightbox="images/atp-incidents-mgt-pane-updated.png":::

Olayları kendinize atayabilirsiniz, durumunu ve sınıflandırmayı değiştirebilir, ilerleme durumlarını izlemek için bunları yeniden adlandırabilirsiniz veya yorumda bulundurabilirsiniz.

> [!TIP]
> Bir bakışta daha fazla görünürlük için, olay adları etkilenen uç nokta sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine göre otomatik olarak oluşturulur. Bu, olayın kapsamını hızla anlamana olanak sağlar.
>
> Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*
>
> Otomatik olay adlarının herhangi bir şekilde otomatik olarak adlandırılamadan önce mevcut olan olaylar adlarını korur.
>

:::image type="content" source="images/atp-incident-details-updated.png" alt-text="Olay ayrıntı sayfası" lightbox="images/atp-incident-details-updated.png":::

## <a name="assign-incidents"></a>Olay atama
Henüz bir olay atanmamışsa, olayı kendinize atamak **için Bana** ata'yi seçin. Bu şekilde, yalnızca olayın değil, aynı zamanda ilgili tüm uyarıların sahipliğini kabul eder.

## <a name="set-status-and-classification"></a>Durum ve sınıflandırmayı ayarlama
### <a name="incident-status"></a>Olay durumu
Olayları kategorilere ayırarak ( **Etkin** veya Çözümlendi **olarak)** araştırmanız ilerledikçe durumlarını değiştirerek bunları kategorilere ayırarak. Bu, ekibinizin olaylara yanıt vermede nasıl yardımcı olduğunu düzenlemenize ve yönetmenize yardımcı olur.

Örneğin, SoC analisti günün acil Etkin olaylarını  gözden geçirsin ve bunları araştırma için uygun bir nedene atasın.

Alternatif olarak, SoC analisti olay **düzeltilirse olayı** Çözümlendi olarak ayarlamış olabilir. 

### <a name="classification"></a>Sınıflandırma
Sınıflandırma ayarlamayı veya bir olayın doğru mu yoksa yanlış mı olduğunu belirtmeyi seçebilirsiniz. Bunu yapmak, ekibin desenleri görmelerine ve onlardan bilgi öğrenmelerine yardımcı olur.

### <a name="add-comments"></a>Açıklama ekleme
Bir olayla ilgili olarak açıklamalar ekleyebilir ve geçmiş olayları görüntüye bakarak, o olayda yapılan önceki değişiklikleri görüntüabilirsiniz.

Uyarıda değişiklik veya açıklama yapıldıklarında, açıklamalar ve geçmiş bölümüne kaydedilir.

Eklenen açıklamalar anında bölmede görünür.



## <a name="related-topics"></a>İlgili konular
- [Olay sırası](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Olaylar kuyruğu görüntüleme ve düzenleme](view-incidents-queue.md)
- [Olayları araştırın](investigate-incidents.md)
