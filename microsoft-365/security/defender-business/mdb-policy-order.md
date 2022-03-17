---
title: İş için Microsoft Defender'da ilke siparişlerini anlama
description: İş için Microsoft Defender'daki ilkelerle öncelik sırası hakkında bilgi
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
ms.openlocfilehash: 373f3eb821e00f903837f98896ed5dab0588e946
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63524915"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da ilke siparişlerini anlama

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da ilke sırası

İş için Microsoft Defender, çalışanlarınızı kullanan cihazların korunmasına yardımcı olmak için önceden tanımlanmış ilkeler içerir. Güvenlik ekipleriniz de yeni ilkeler ekleyebilir. Örneğin, bazı ayarları bazı cihazlara ve diğer cihazlara farklı ayarlar uygulamak istediğiniz varsayalım. Bunu, yeni nesil koruma ilkeleri veya güvenlik duvarı ilkeleri gibi ilkeler ekleyerek de bunuabilirsiniz.

İlkeler eklendikken, bir öncelik sırası atandı bildirimini fark ettiysiniz. Tanımladığınız ilkeler için öncelik sıralarını düzenleyebilirsiniz, ancak varsayılan ilkeler için öncelik sıralarını değiştiremezsiniz. Örneğin, cihaz ve istemci Windows üç yeni nesil koruma ilkeniz olduğunu varsayalım. Bu durumda, varsayılan ilkeniz önceliğe sahip 3 numaradır. İlkelerinizi 1 ve 2 numaralı olacak şekilde değiştirebilirsiniz, ancak varsayılan ilke listede 3 numaradan kalacaktır. 

**Birden çok ilke hakkında unutmamanız gereken önemli olan, cihazların yalnızca ilk uygulanan ilkeyi almayacaklarıdır.** Önceki üç yeni nesil ilke örneğimize başvurup, üç ilkenin de hedeflemektedir. Bu durumda, bu cihazlar 1 numaralı ilkeyi alır ancak 2 ve 3 numaralı ilkeleri almaz. 

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="key-points-to-remember-about-policy-order"></a>İlke sırasıyla ilgili anımsanacak önemli noktalar

- İlkelere öncelik sırası atanır.

- Cihazlar yalnızca ilk uygulanan ilkeyi alır.

- İlkelerin öncelik sıralarını değiştirebilirsiniz.

- Varsayılan ilkelere en düşük öncelik sırası verilir.

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Defender'ı kullanmaya başlama](mdb-get-started.md)

- [Cihazları yönet](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)