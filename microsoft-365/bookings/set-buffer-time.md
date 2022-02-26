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
ms.openlocfilehash: c3d07be3c858eca5f6e9a672581b386625f5dd80
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973579"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Microsoft Bookings'te arabelleğe alma süresi ayarlama

Randevular arasında yer alan ve oda ve donanımınızı ayarlaması, temizlemesi veya sıfırlaması için müşteriyle toplantı öncesinde veya sonrasında zaman gerekli olabilir. Öte ya da müşteri randevuları arasında yolculuk yapıyorsanız, sizin ve ekibinin müşteri beklemeden randevular arasında yolculuk yapmanızı sağlamak için zaman gerekir.

Randevular başlamadan önce ara zamanları, randevular sona erdikten sonra ya da her ikisini de personele bir sonraki randevuya hazırlanmaları için gereken fazladan zamanları veabilirsiniz.

## <a name="set-buffer-time-defaults"></a>Arabelleğe süre varsayılanlarını ayarlama

Arabelleğe alma süresi varsayılanları **Bookings'in** Hizmet ayrıntıları sayfasında ayarlanır. Bu sayfada ayarlanmış tüm hizmet varsayılanları gibi, bu varsayılanlar da belirli müşteri  ihtiyaçlarını karşılamak üzere belirli bir rezervasyon için sizin tarafından düzenlenebilir.

Arabelleğe alma süresi ayarı, Hizmet ayrıntıları **sayfasındaki** Varsayılan süre seçicilerin **hemen altında** bulunabilir. Belirli bir hizmet için ayarlanmadan önce, arabelleğe alma süresi iki durumlu düğmeyi seçerek arabellek süre ayarını etkinleştirmeniz gerekir. Bu, **burada gösterildiği** gibi  her rezervasyondan önce ve sonra varsayılan rezervasyon miktarını seçmek için kullanılan Önceki ve Sonra açılan listelerinin görünmesine neden olur:

   ![Arabelleğe alma süresi etkinleştirilmiş Bookings'in resmi.](../media/bookings-buffertime.png)

## <a name="buffer-time-and-appointment-timing"></a>Arabelleğe alma süresi ve randevu zamanlaması

Müşterilerin ne zaman toplantı yapmak istediğinizle ilgili karışıklığı önlemek için Bookings takviminize, ilgili personele e-posta onayları ve anımsatıcılar olarak tampon süre ve gerçek randevu süresi (müşterilerin tanışmayı beklemede olduğu zaman) gösterir. Örneğin, 15 dakika ön randevu zamanları içeren bir müşteriyle randevu için Bookings'te aşağıdakini görebilirsiniz.

Olayın kendisi (aşağıdaki resimde solda), arabellek süresi için daha açık renkli gölgelendirme ve gerçek müşteri randevusu için koyu gölgelendirme gösterir. Randevu aramasını (olayı seçinca açılır) özellikle randevun Katie Jordan ile 09:00 ile 10:00 arasında olduğunu belirtir ve randevudan 15 dakika önce ve randevudan 0 dakika sonra ara sıra içerir. Müşteri yalnızca 09:00 ile 10:00 arasında randevu zamanı ile ilgili onay ve anımsatıcılar alsa da, personele yapılan onaylar ve anımsatıcılar benzer şekilde belirli tampon ve randevu saatlerine başvurur.

   ![Ara zaman gösteren Bookings randevu çağrısını gösteren resim.](../media/bookings-buffertime-callout.png)

## <a name="buffer-time-and-availability"></a>Arabellek süresi ve kullanılabilirliği

Müşterileriniz ayardeğieğinizin tampon süreleri doğrudan görmüyor ve değiştiremez. Öte yandan, arabelleğe alma süresi bir bütün olarak hizmet süresini hesaplamak için kullanılır, müşteriler hem ara bellek hem de normal randevu saatlerinde ayrılmış olarak sizi ve ilgili personelinizi görür. Müşteriler ayrıca hem randevu hem de arabelleğe yetecek kadar süre varsa sizin ve personelinizin uygunluk durumunu görebilir.

Örnek olarak, 15 dakikalık bir randevu ile bir saatlik randevu için en az 1 saat ve 15 dakika kullanılabilir bir zaman bloğu gerektirmektedir. Bu hizmetle ilgili bir randevu, bu nedenle takvimde 75 dakikalık bir zaman bloğu dolduracak ve çakışma olmadan rezervasyon yapmak için 75 dakika kullanılabilirlik süresine ihtiyaçecektir.
