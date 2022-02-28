---
title: SSS'ler Microsoft 365 Zamanlayıcı
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: SSS'ler Microsoft 365 Zamanlayıcı
ms.openlocfilehash: 2392c48de3d80cf41d179eb053c46967626b5159
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989991"
---
# <a name="scheduler-for-microsoft-365-faq"></a>SSS'ler Microsoft 365 Zamanlayıcı

**Soru:** Scheduler; Cortana Için Cortana, Günlük *Brifing* E-postası ve *E-postalarımı Oynat* gibi diğer Windows *özellikleriyle nasıl tümleştirilmiştir*?</br>
Zamanlayıcı, diğer çalışma saat özelliklerinden bağımsız Cortana dir. Diğer Cortana kiracı düzeyinde devre dışı bırakılabilir ve Zamanlayıcı e-posta adresi kullanılarak cortana@yourdomain.com etkinleştirilebilir. Şu anda, kullanıcılar zamanlayıcıyla yalnızca e-posta yoluyla etkileşimde bulunabilirsiniz.

**Soru:** Bu yalnızca iş başka kişi Outlook? Diğer e-posta ürünleri destek var mı?</br>
Lisansınız olduğu sürece, yukarıdaki üç gereksinimler dışında, kullanıcılar herhangi bir cortana@yourdomain.com cihazda herhangi bir e-posta istemcisini kullanarak e-posta ile e-posta gönderebilirsiniz.

**Soru:** Kişiler kişisel kişi listesinde yer alan kişiler Outlook GAL veya başka bir şirket eşdeğerinde olabilir mi?</br>
Toplantı katılımcıları, şirket içinde veya dışında e-posta adresi olan herhangi biri olabilir. Ne yazık ki, Zamanlayıcı, bugün GAL'de araarak adları e-posta adreslerine / diğer adlara otomatik olarak çevirebilir.

**Soru:** Scheduler'i yüklü sürümüm (şirket içi) sürümüyle kullanabilir Outlook?</br>
Zamanlayıcı için zamanlama Exchange Online. Posta (Exchange Server) ile çalışmıyor. Herhangi bir e-posta istemcisiyle, Outlook Masaüstü, OWA, iOS, android, gmail ile çalışır.

**Soru:** Arka Outlook açık olması gereken bir durum var mı?</br>
Outlook arka planda açık olması gerekir. Tek gereken e-posta Cortana posta göndermek ve işi büyük kısmını yapmak için ona güvenmektir.

## <a name="frequently-asked-trust-and-privacy-questions"></a>Sık Sorulan Güven ve Gizlilik Soruları

**Soru:** Zamanlayıcı nasıl çalışır?</br>
Zamanlayıcı, insan yardımcıları ile geliştirilmiş Zamanlama Zekası (AI) kullanır. AI modelleri, verilerle doğal iletişim dilinde destek için bir ihtiyaç Cortana, toplantı isteği gözden geçirme ve tamamlama için insan'a ilerler.

**Soru:** Who istekleri gözden geçiren insanlar insanlar mı? </br>
Zamanlayıcı yardımcıları, kişisel ve çok gizli bilgiler için onaylı Microsoft Sağlayıcı Güvenlik ve Gizlilik Güvencesi 'ne (SSPA) sahiptir.

**Soru:** SSPA Yardımcıları neleri  bakabilirsiniz?</br>
Scheduler ve SSPA Yardımcıları, bu adrese gönderilen e-postaları Cortana. Zincir e-posta alışverişinde, yalnızca Cortana e-posta adresini içeren e-postalar işlenir; e-posta eklenmeden önce dizide yer alan önceki Cortana işlenmez.

**Soru:** Müşteri verileri Zamanlayıcı'nın Veri Kaynağı'Flow? </br>
Zamanlayıcı, tüm müşteri içeriğini kiracı sınırları içinde depolar ve verileri GDPR yönergelerine, Microsoft 365 Güven & ve kiracı e-posta ilkelerine uygun olarak korur.

**Soru:** Zamanlayıcı, iç katılımcıların serbest/meşgul verilerini nasıl işler? </br>
Scheduler'ın otomasyonu, katılımcıların ve düzenleyicinin karşılıklı olarak sağ kullandığı saatleri tanımlamak için *findMeetingTimes* hizmetini kullanır. Bu hizmet, Outlook formunda Önerilen Zamanlar *gibi diğer* Outlook gücü sağlar. Serbest/meşgul katılımcı bilgileri açıkça serbest/meşgul blokları olarak tüketilmez.

**Soru:** Scheduler GDPR Uyumlu mu? </br>
Evet.

**Soru:** Who posta kutusuna Cortana var mı? </br>
Zamanlayıcı, kiracının posta kutusuna gönderilen toplantı isteklerini ve ilişkili e-postaları Cortana. Microsoft'un, kiracı yöneticisinin isteği üzerine Cortana kutusu onayı dışında posta kutusuna başka hiçbir şekilde erişimi yoktur.

**Soru:** AI modellerinin eğitimi için müşteri verileri kullanılıyor mu?</br>
Veri eğitim kümeleri için Scheduler'Microsoft 365 hiçbir müşteri içeriği kullanılamaz. Tüm müşteri içeriği müşteri kiracıdadır.

**Soru:** Scheduler şifreli postayı işler mi?</br>
Hayır, şifrelenmiş posta Zamanlayıcı iş akışı tarafından reddedilir.
