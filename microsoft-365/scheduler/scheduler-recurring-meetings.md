---
title: Dinamik Yinelenen Toplantıları Zamanlama
ms.author: sarichardson
author: sallyri
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.reviewer: strettin
ms.localizationpriority: medium
description: Kullanıcılar dinamik yinelenen toplantıları zamanlama hakkında daha fazla bilgi öğrenebilir.
ms.openlocfilehash: d4f99b336088e7c565c741a8f631e4fefbada68f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989977"
---
# <a name="scheduling-dynamic-recurring-meetings"></a>Dinamik Yinelenen Toplantıları Zamanlama

Scheduler'ın dinamik toplantıları, kullanıcının meşgul zamanlaması etrafında çalışır. Scheduler tarafından yönetilen yinelenen toplantılar, toplantılarda geleneksel yinelenen toplantılardan farklı Outlook. Gelecek takviminizi açık tutmak ve katılımcılarla çakışmaları en aza indirmek için, Zamanlayıcı aynı anda yinelenen bir toplantının tek bir örneğini zamanlar.

Örnek olarak, "Cortana 30 dakikalık odaklanma süresi planla" sorulsa, başlangıçta takvimde bir sonraki uygun tarih için 30 dakikalık bir randevu oluşturulacak.  Bu randevu saati geçirildiktan sonra, Zamanlayıcı, aşağıdaki tarihte başka bir randevu örneği için rezervasyon yapmak için devam eder. Özgün zaman çizelgesi şu anda kullanılamıyorsa, Zamanlayıcı zamanı uygunluk durumunuz temel alarak ayarlar.

Davetlilerle yapılan toplantılarda da aynı heurist uygulanabilir. İsteğinize katılımcıları dahil etmek ve Cortana "her iki haftada bir toplantı zamanlama" isteğinde bulundurarak bu soruyu sorsanız. İlk ve bunu takipan her toplantı, kurum içindeki tüm katılımcıların mevcut uygunluk durumuna göre dinamik olarak zamanlanan toplantı olur. Bir sonraki tarihte siz veya bir katılımcı uygun değil ya da ofis dışında olursa, toplantı saati herkesin uygun olduğu tarihe göre otomatik olarak ayarlanır ve yeni zamanlanan tarihe göre takip edilen toplantı örnekleri için istenen tempo korunur.

## <a name="booking-with-attendees-outside-your-organization"></a>Kuruluş dışındaki katılımcılarla rezervasyon

Sanal yardımcınız, kuruluş dışından katılımcılarla zaman zamanlaması zamanlaması için dış katılımcılara ilk toplantı için zaman seçeneklerini gönderir. Düzenleyicinin ve şirket içi katılımcıların uygunluk durumuna bağlı olarak gelecek tüm toplantılar otomatik olarak zamanlandı.

Zamanlayıcı, günlük, haftalık ve aylık aralıkları destekler.

## <a name="examples-of-how-to-request-recurring-meetings"></a>Yinelenen Toplantıların Nasıl İsteği Üzerine Örnek

Burada, yinelenen toplantıları zamanlamayı e-posta yoluyla Cortana bazı örnekler verilmiştir:

- "Cortana, 2 haftada bir toplantı zamanla."
- "Gözden geçirme için aylık 30 dakika kitap."
- "Cortana Her Salı günü 30 dakika tolamayacak."
- "Cortana, her Cuma için 15:30'da 30 dakika zamanlama"

## <a name="changing-recurring-frequency"></a>Yinelenen Sıklığı Değiştirme

Zamanlayıcı tarafından yönetilen herhangi bir yinelenen toplantının veya yinelenen olmayan toplantının sıklığını değiştirebilirsiniz. E-Cortana toplantı ileti dizisinde yer alan son onay e-postasında yanıt verin ve yanıt Cortana:

- "Bunu her ay bir kez değiştir."
- "Cortana, bu toplantıyı iki hafta yapma."

## <a name="cancelling-recurring-meetings"></a>Yinelenen Toplantıları iptal

Toplantının en son Cortana iletisine yanıt ve zamanlanan örneği iptal etmek için "bu toplantıyı iptal etmek" istemeniz gerekir. Ancak, Zamanlayıcı aynı sıklıkta gelecek toplantıları zamanlamayı sürdürecek. Alternatif olarak, Zamanlayıcı'nın bir sonraki örneği istediğiniz tarih veya saatle yeniden zamanlaması da istenmektedir. Yinelenen serinin tamamını iptal etmek isterseniz,"bu seriyi iptal et" ile yanıt verin; bundan sonra hiçbir şey zaman olmayacaktır.

## <a name="recurring-meeting-limitations"></a>Yinelenen Toplantı Sınırlamaları

Tekrarlama türleriyle ilgili bazı teknik sınırlamalar olduğunu lütfen unutmayın. Zamanlayıcı şunları anebilir ve desteklemektedir:

- Aynı zaman aralığı içindeki birden çok tekrarı desteklanmaz (örneğin: "haftada iki kez").
- Yineleme için bitiş tarihleri desteklenmemektedir (örneğin: "20 Aralık'a kadar her gün"). Her toplantının bir önceki toplantının tamamlanmasından sonra zamanlandığı için, toplantının en son iletisine "bu toplantı Cortana" yanıtını verebilirsiniz.
- Zamanlayıcı şu anda 90'dan fazla yineleme sıklıklarını desteklememektedir.
