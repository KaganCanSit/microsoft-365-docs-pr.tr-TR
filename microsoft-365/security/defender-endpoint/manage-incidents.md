---
title: Uç nokta olayları için Microsoft Defender'ı yönetme
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
ms.openlocfilehash: 45c08c5a3c304a23b5761d96a4d9aceb1b4f1562
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011985"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>Uç nokta olayları için Microsoft Defender'ı yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Olayları yönetmek, her siber güvenlik operasyonlarının önemli bir parçasıdır. Olayları yönetmek için, Olaylar kuyruğundan veya **Olaylar yönetim** bölmesinden **bir olay seçin**. 


Olaylar sırasından bir **olay seçerek** , ayrıntılar için **olay sayfasını** açabilirsiniz.


![Olay yönetim bölmesinin resmi.](images/atp-incidents-mgt-pane-updated.png)

Olayları kendinize atayabilirsiniz, durumunu ve sınıflandırmayı değiştirebilir, ilerleme durumlarını izlemek için bunları yeniden adlandırabilirsiniz veya yorumda bulundurabilirsiniz.

> [!TIP]
> Bir bakışta daha fazla görünürlük için, olay adları etkilenen uç nokta sayısı, etkilenen kullanıcılar, algılama kaynakları veya kategoriler gibi uyarı özniteliklerine göre otomatik olarak oluşturulur. Bu, olayın kapsamını hızla anlamana olanak sağlar.
>
> Örneğin: *Birden çok kaynak tarafından bildirilen birden çok uç noktada çok aşamalı olay.*
>
> Otomatik olay adlarının herhangi bir şekilde otomatik olarak adlandırılamadan önce mevcut olan olaylar adlarını korur.
>


![Olay ayrıntı sayfasının görüntüsü.](images/atp-incident-details-updated.png)

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
- [Olayları araştırma](investigate-incidents.md)
