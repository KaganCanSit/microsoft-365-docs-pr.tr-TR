---
title: Rezervasyon sayfasına özel ve gerekli sorular ekleme
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: fd6b7587-5055-4bcd-83a4-13bd4929bfff
description: Çevrimiçi olarak randevu alan müşterilere soru sormanız gerekirse rezervasyon sayfasına özel sorular ve gerekli sorular ebilirsiniz.
ms.openlocfilehash: d7d997ff02e2a6b8d849cb50014924733bac8e32
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984663"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Rezervasyon sayfasına özel ve gerekli sorular ekleme

Bookings, randevular için müşterilerinize sorular sormanızı sağlar. Ayrıca, hangi soruların gerekli olduğunu seçmenizi de sağlar.

Her hizmetin farklı bir soru kümesine sahip olabilir ve böylece soruları bir hizmetle ilişkilendirmelisiniz. Örneğin, bir hairtylist, all'lar veya tint'lere bilinen herhangi bir alerjisi olup olmadığını sormak için, size bir kıl rengi randevu randevuyu sorar. Bu, sizin ve müşterileriniz randevuya ulaşarak zaman kazanmak için size olanak sağlar.

Müşteriler randevularını rezervasyon sayfasında oluştururken özel soruları görebilirler. Personel Bookings takviminde yeni bir rezervasyon oluşturdukta veya mevcut bir randevuyu görüntülerken özel soruları görebilir. Bookings, her hizmet için aynı soruları yeniden oluşturmak zorunda olmadığınız için tüm sorularınızı bir ana listeye kaydeder. Ayrıca, soruların gerekli mi yoksa isteğe bağlı mı olduğunu da seçebilirsiniz.

> [!NOTE]
> Rezervasyon takviminde randevuya bakarak müşterinin sorularına yanıtlarını alabilirsiniz.

Rezervasyon sayfanızı kişiselleştirme ve özelleştirme hakkında daha fazla bilgi için bkz [. Rezervasyon sayfanızı özelleştirme](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Hizmetlerinize özel sorular ekleme

1. Oturum açma ve Microsoft 365 **Bookings'e gidin**.

1. **Hizmetler'e gidin** ve mevcut bir hizmeti düzenleyin veya **Hizmet ekle'yi seçin**.

1. Ekranı aşağı kaydırarak **Özel alanlar bölümüne** gidin ve Değiştir'i **seçin**.

   Bazı temel müşteri bilgileri sorularını zaten ekledik: Müşteri e-postası, telefon numarası, müşteri adresi ve müşteri notları. Bunu ilk kez yapmak için müşteri bilgileri soruları gri renkle vurgulanır. Bu, kullanıcının bu soruyu göreceği anlamına gelir. Soruyu seçmenizin ardından çevresindeki vurgu kutusu kaybolur ve müşterinize bu soru sorulamaz.

   Bu örnekte, telefon numarası ve müşteri notları kapatılan ve sormak üzere iki yeni özel soru oluşturduk.

   ![Özel sorular ekranı görüntüsü.](../media/bookings-questions-custom-fields.png)

1. Soruyu zorunlu yapmak için Gerekli **onay** kutusunu seçin. Müşteriniz gerekli soruları yanıtlayana kadar rezervasyon işlemini tamamlayabilecektir.

1. Özel bir soru oluşturmak için **panelin üst kısmından** Soru ekle'yi seçin. Sorusunu yazın ve ardından Kaydet'i **seçin**.

1. Etkinleştirmek için soruya tıklayın. Çevresinde vurgulu bir kutu görünür ve soru etkinleştirilir.

1. Sayfanın **en** üstünde Tamam'a tıklayın ve ardından **Hizmeti kaydet'e tıklayın**.

Bookings, tüm özel sorularınızı ana listeye kaydederek aynı soruları tekrar tekrar yazmanıza gerek kalmadan her hizmete kolayca soru eklemenizi sağlar. Örneğin, farklı bir hizmet açarsanız, ilk hizmet için oluşturduğunuz soru Özel alanlar bölümünde gösterir ama devre dışı bırakılır. Soruyu tıklatın; böylece vurgulu bir dikdörtgen görüntülenir ve soru etkinleştirilir.

Bu örnekte, ilk hizmet için eklenen soruların bu hizmette kullanılabilir olduğunu görüyorsunuz. Bu hizmet için tüm sorular tüm hizmetlerde kullanılabilir.

   ![Birden çok hizmet için görünen soruların resmi.](../media/bookings-questions-services.png)

Rezervasyon sayfanız zaten yayımlanmışsa başka bir şey yapmaya gerek yok. Müşteriler bir sonraki rezervasyonda soruları görebilirler. Rezervasyon sayfanız henüz yayımlanmadısa, rezervasyon sayfasının üzerinden rezervasyon sayfasına  gidin ve Web üzerinde Outlook ve **yayımla'yı seçin**.

> [!WARNING]
> Ayrıca, asıl listeden soruları silebilirsiniz. Ancak bir soruyu sildikten sonra tüm hizmetlerden silinir. Başka hizmetlerden etkilenmey etmek için soruyu seçerek devre dışı bırakmanızı öneririz. Bir soru, vurgulu bir dikdörtgen içinde değilken devre dışı bırakılmıştır.

## <a name="customer-experience"></a>Müşteri deneyimi

Müşterileriniz size bir randevu zaman geldiğinde, Ayrıntılarınızı ekleyin bölümünde temel müşteri **bilgileri soruları** yer amayacak. Ek bilgi sağlama bölümünde, ek bilgi **ekleyebilirsiniz** .

![Sorular etkinleştirildiğinde müşterilerin ne göreceğinin resmi.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Personel deneyimi

Müşterileriniz size randevu zaman geldiğinde, personeliniz soruları ve müşterinin yanıtlarını rezervasyon takviminde görebilir. Bunu görmek için **Bookings Takvimi'ne** \> **gidin** ve bir randevu açın.

![Sorular etkinleştirildiğinde personelin ne göreceğinin resmi.](../media/bookings-questions-staff.png)
