---
title: İlke sırasını İş için Microsoft Defender anlama
description: İş için Microsoft Defender'da ilkelerle öncelik sırası hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 13e803666cc7af14af52031eb86a2f86edf06f80
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666316"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>İlke sırasını İş için Microsoft Defender anlama

> [!IMPORTANT]
> İş için Microsoft Defender, 1 Mart 2022'de başlayarak [Microsoft 365 İş Ekstra](../../business-premium/index.md) müşterilerine dağıtılıyor. Tek başına abonelik olarak İş için Defender önizleme aşamasındadır ve istekte bulunmak için [buraya kaydolan](https://aka.ms/mdb-preview) müşterilere ve BT İş Ortaklarına aşamalı olarak dağıtılacaktır. Önizleme, [bir dizi ilk senaryo](mdb-tutorials.md#try-these-preview-scenarios) içerir ve düzenli olarak özellikler ekleyeceğiz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da ilke sırası

İş için Microsoft Defender, çalışanlarınızın kullandığı cihazların korunduğundan emin olmak için önceden tanımlanmış ilkeler içerir. Güvenlik ekibiniz de yeni ilkeler ekleyebilir. Örneğin, bazı cihazlara belirli ayarları ve diğer cihazlara farklı ayarları uygulamak istediğinizi varsayalım. Bunu yapmak için yeni nesil koruma ilkeleri veya güvenlik duvarı ilkeleri gibi ilkeler ekleyebilirsiniz.

İlkeler eklendikçe bir öncelik sırası atandığını fark edeceksiniz. Tanımladığınız ilkelerin öncelik sırasını düzenleyebilirsiniz, ancak varsayılan ilkeler için öncelik sırasını değiştiremezsiniz. Örneğin, Windows istemci cihazlarınız için üç yeni nesil koruma ilkeniz olduğunu varsayalım. Bu durumda, varsayılan ilkeniz öncelik olarak 3 numaradır. İlkelerinizin 1 ve 2 numaralı sırasını değiştirebilirsiniz, ancak varsayılan ilke listenizde 3 numarada kalır. 

**Birden çok ilke hakkında hatırlamanız gereken önemli şey, cihazların yalnızca ilk uygulanan ilkeyi almasıdır.** Önceki üç yeni nesil ilke örneğimize bakarak, üç ilkenin de hedeflediği cihazlarınız olduğunu varsayalım. Bu durumda, bu cihazlar ilke numarası 1'i alır, ancak 2 ve 3 numaralı ilkeleri almaz. 

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">İş için Microsoft Defender hakkındaki kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="key-points-to-remember-about-policy-order"></a>İlke sırası hakkında hatırlanması gereken önemli noktalar

- İlkelere öncelik sırası atanır.

- Cihazlar yalnızca ilk uygulanan ilkeyi alır.

- İlkelerin öncelik sırasını değiştirebilirsiniz.

- Varsayılan ilkelere en düşük öncelik sırası verilir.

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Defender'Kullanmaya başlayın kullanma](mdb-get-started.md)

- [Cihazları yönetme](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)

- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)