---
title: Bookings arabellek süresini ayarlama
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Ekipmanı temizlemek veya sıfırlamak için zaman sağlamak için Microsoft Bookings randevudan önce veya sonra arabellek süresi ayarlayın.
ms.openlocfilehash: 49e58d53cec466c824a40281e3199f1544e74744
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637593"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Microsoft Bookings'de arabellek süresini ayarlama

Bazı randevularınız, odanızı ve ekipmanınızı ayarlamak, temizlemek veya sıfırlamak için müşterinizle görüşmeden önce veya sonra zaman gerektirebilir. Veya müşteri randevuları arasında yoldaysanız, sizin ve ekibinizin müşteriyi bekletmeden randevular arasında seyahat etmesini sağlamak için zamana ihtiyacınız olabilir.

Randevular başlamadan önce, randevular sona erdikten sonra arabelleğe alma süresi ayarlayabilir veya her ikisini birden personele bir sonraki randevularına hazırlanmaları için gereken ek süreyi verebilirsiniz.

## <a name="set-buffer-time-defaults"></a>Arabellek süresi varsayılanlarını ayarlama

Arabellek süresi varsayılanları Bookings **Hizmet ayrıntıları** sayfasında ayarlanır. Bu sayfada ayarlanan tüm hizmet varsayılanları gibi, bu varsayılanlar da belirli bir rezervasyon için sizin tarafınızdan belirli müşteri gereksinimlerini karşılayacak şekilde düzenlenebilir.

Arabellek süresi ayarı **Hizmet ayrıntıları** sayfasında bulunabilir. Belirli bir hizmet için ayarlanabilmesi için önce arabellek süresi düğmesini seçerek arabellek süresi ayarını etkinleştirmeniz gerekir. Bu, burada gösterildiği gibi her rezervasyondan önce ve sonra tutulacak varsayılan süreyi seçmek için kullanılan **Önce** ve **Sonra** açılan listelerinin görünmesine neden olur:

   ![Arabellek süresi etkin Bookings görüntüsü.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Arabellek süresi ve kullanılabilirlik

Müşterileriniz ayarladığınız arabellek sürelerini doğrudan görmez ve değiştiremez. Ancak, arabellek süresi genel hizmet süresini hesaplamak için kullanıldığından, müşteriler sizi ve ilgili personelinizi hem arabelleğe hem de normal randevu zamanlarında ayrılmış olarak görür. Müşteriler ayrıca hem randevu hem de arabelleğe alma süresi için yeterli zaman varsa yalnızca sizin ve personelinizin uygunluk durumunu görür.

Örneğin, 15 dakikalık randevu öncesi arabellek süresine sahip bir saatlik randevu için en az 1 saat 15 dakikalık kullanılabilir bir zaman bloğu gerekir. Bu nedenle bu hizmet için bir randevu takviminizdeki 75 dakikalık bir zaman bloğunu dolduracak ve çakışma olmadan rezervasyon yapmak için 75 dakikalık uygunluk süresine ihtiyaç duyar.
