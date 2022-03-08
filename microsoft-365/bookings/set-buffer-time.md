---
title: Microsoft Bookings'te arabelleğe alma süresi ayarlama
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Donanımı temizlemeye veya sıfırlamaya zaman vermek için Microsoft Bookings'te bir randevudan önceki veya bir randevudan sonra arabelleğe kadar zaman ayarlayın.
ms.openlocfilehash: a33159b0b5f168bbb61c88bc9b4181e05c8abbb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329327"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Microsoft Bookings'te arabelleğe alma süresi ayarlama

Randevular arasında yer alan ve oda ve donanımınızı ayarlaması, temizlemesi veya sıfırlaması için müşteriyle toplantı öncesinde veya sonrasında zaman gerekli olabilir. Öte ya da müşteri randevuları arasında yolculuk yapıyorsanız, sizin ve ekibinin müşteri beklemeden randevular arasında yolculuk yapmanızı sağlamak için zaman gerekir.

Randevular başlamadan önce ara zamanları, randevular sona erdikten sonra ya da her ikisini de personele bir sonraki randevuya hazırlanmaları için gereken fazladan zamanları veabilirsiniz.

## <a name="set-buffer-time-defaults"></a>Arabelleğe süre varsayılanlarını ayarlama

Arabelleğe alma süresi varsayılanları **Bookings'in** Hizmet ayrıntıları sayfasında ayarlanır. Bu sayfada ayarlanmış tüm hizmet varsayılanları gibi, bu varsayılanlar da belirli müşteri  ihtiyaçlarını karşılamak üzere belirli bir rezervasyon için sizin tarafından düzenlenebilir.

Arabelleğe alma süresi ayarı, Hizmet ayrıntıları **sayfasındaki** Varsayılan süre seçicilerin **hemen altında** bulunabilir. Belirli bir hizmet için ayarlanmadan önce, arabelleğe alma süresi iki durumlu düğmeyi seçerek arabellek süre ayarını etkinleştirmeniz gerekir. Bu, **burada gösterildiği** gibi  her rezervasyondan önce ve sonra varsayılan rezervasyon miktarını seçmek için kullanılan Önceki ve Sonra açılan listelerinin görünmesine neden olur:

   ![Arabelleğe alma süresi etkinleştirilmiş Bookings'in resmi.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Arabellek süresi ve kullanılabilirliği

Müşterileriniz ayardeğieğinizin tampon süreleri doğrudan görmüyor ve değiştiremez. Öte yandan, arabelleğe alma süresi bir bütün olarak hizmet süresini hesaplamak için kullanılır, müşteriler hem ara bellek hem de normal randevu saatlerinde ayrılmış olarak sizi ve ilgili personelinizi görür. Müşteriler ayrıca hem randevu hem de arabelleğe yetecek kadar süre varsa sizin ve personelinizin uygunluk durumunu görebilir.

Örnek olarak, 15 dakikalık bir randevu ile bir saatlik randevu için en az 1 saat ve 15 dakika kullanılabilir bir zaman bloğu gerektirmektedir. Bu hizmetle ilgili bir randevu, bu nedenle takvimde 75 dakikalık bir zaman bloğu dolduracak ve çakışma olmadan rezervasyon yapmak için 75 dakika kullanılabilirlik süresine ihtiyaçecektir.
