---
title: İş için Microsoft Defender'da (önizleme) ilke siparişlerini anlama
description: Microsoft Defender İş'te (önizleme) ilkelerle öncelik sırası hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 01d6b5cc77068bc8f86d4a32777663ae251acd8d
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027517"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da (önizleme) ilke siparişlerini anlama

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da ilke sırası

İş için Microsoft Defender (önizleme), çalışanlarınızı kullanan cihazların korunmasına yardımcı olmak için önceden tanımlanmış ilkeler içerir. Güvenlik ekipleriniz de yeni ilkeler ekleyebilir. Örneğin, bazı ayarları bazı cihazlara ve diğer cihazlara farklı ayarlar uygulamak istediğiniz varsayalım. Bunu, yeni nesil koruma ilkeleri veya güvenlik duvarı ilkeleri gibi ilkeler ekleyerek de bunuabilirsiniz.

İlkeler eklendikken, bir öncelik sırası atandı bildirimini fark ettiysiniz. Tanımladığınız ilkeler için öncelik sıralarını düzenleyebilirsiniz, ancak varsayılan ilkeler için öncelik sıralarını değiştiremezsiniz. Örneğin, cihaz ve istemci Windows üç yeni nesil koruma ilkeniz olduğunu varsayalım. Bu durumda, varsayılan ilkeniz önceliğe sahip 3 numaradır. İlkelerinizi 1 ve 2 numaralı olacak şekilde değiştirebilirsiniz, ancak varsayılan ilke listede 3 numaradan kalacaktır. 

**Birden çok ilke hakkında unutmamanız gereken önemli olan, cihazların yalnızca ilk uygulanan ilkeyi almayacaklarıdır.** Önceki üç yeni nesil ilke örneğimize başvurup, üç ilkenin de hedeflemektedir. Bu durumda, bu cihazlar 1 numaralı ilkeyi alır ancak 2 ve 3 numaralı ilkeleri almaz. 

## <a name="key-points-to-remember-about-policy-order"></a>İlke sırasıyla ilgili anımsanacak önemli noktalar

- İlkelere öncelik sırası atanır

- Cihazlar yalnızca ilk uygulanan ilkeyi alır

- İlkelerin öncelik sıralarını değiştirebilirsiniz

- Varsayılan ilkelere en düşük öncelik sırası verilir

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Defender'ı (önizleme) kullanmaya başlama](mdb-get-started.md)

- [Cihazları yönet](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)