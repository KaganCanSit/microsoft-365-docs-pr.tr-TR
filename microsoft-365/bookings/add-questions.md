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
description: Çevrimiçi olarak sizinle randevu alırken müşterilere soru sormanız gerekiyorsa, rezervasyon sayfasına özel sorular ve gerekli sorular ekleyebilirsiniz.
ms.openlocfilehash: d42f883f3d58882ec5a2e8e8e2bbe7baf7ed3232
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637703"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Rezervasyon sayfasına özel ve gerekli sorular ekleme

Bookings, müşterilerinize randevu rezervasyonu yaparken sormak için sorular oluşturmanıza olanak tanır. Ayrıca hangi soruların gerekli olduğunu seçmenizi sağlar.

Her hizmetin farklı bir soru kümesine sahip olabilmesi için soruları bir hizmetle ilişkilendirirsiniz. Örneğin bir saç stilisti, saç boyama randevusu alan müşterilere çamaşır suyu veya renk tonlarına karşı bilinen alerjileri olup olmadığını sorabilir. Bu, sizin ve müşterilerinizin randevuları için vardığında zaman kazanmanıza olanak tanır.

Müşteriler randevularını oluştururken rezervasyon sayfasında özel soruları görür. Personel, Bookings takviminden yeni bir rezervasyon oluştururken veya mevcut randevuyu görüntülerken özel soruları görür. Bookings, her hizmet için aynı soruları yeniden oluşturmanız gerekmemesi için tüm sorularınızı ana listeye kaydeder. Ayrıca soruların gerekli mi yoksa isteğe bağlı mı olduğunu da seçebilirsiniz.

> [!NOTE]
> Müşterinin sorulara verdiği yanıtlar, randevularına rezervasyon takviminde baktığınızda görülebilir.

Rezervasyon sayfanızı kişiselleştirme ve özelleştirme hakkında daha fazla bilgi için bkz. [Rezervasyon sayfanızı özelleştirme](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Hizmetlerinize özel sorular ekleme

1. Microsoft 365 oturum açın ve **Bookings** gidin.

1. Takviminizi seçin.

1. **Hizmetler'e** gidin ve mevcut bir hizmeti düzenleyin veya **Hizmet ekle'yi seçin**.

1. **Özel alanlar** bölümünü seçin.

   Bazı temel müşteri bilgileri soruları ekledik: Müşteri e-postası, telefon numarası, müşteri adresi ve müşteri notları. Bunu ilk kez gerçekleştirdiğinizde, müşteri bilgileri soruları gri renkle vurgulanır. Bu, kullanıcının bu soruyu göreceği anlamına gelir. Soruyu seçerseniz, etrafındaki vurgu kutusu kaybolur ve müşterinize bu soru sorulmayacak.

   Bu örnekte telefon numarası ve müşteri notları kapatıldı ve sorulmak üzere iki yeni özel soru oluşturduk.

   ![Özel sorular ekranının görüntüsü.](../media/bookings-questions-custom-fields.png)

1. Soruyu gerekli kılmak için **Gerekli** onay kutusunu seçin. Müşteriniz gerekli soruları yanıtlayana kadar rezervasyonu tamamlayamaz.

1. Özel bir soru oluşturmak için panelin üst kısmından **Soru ekle'yi** seçin. Sorunuzu yazın ve **kaydet'i** seçin.

1. Etkinleştirmek için soruya tıklayın. Etrafında vurgulanan bir kutu görünür ve soru etkinleştirilir.

1. Sayfanın üst kısmındaki **Tamam'a** ve ardından **Hizmeti kaydet'e** tıklayın.

Bookings, aynı soruları tekrar tekrar yazmanıza gerek kalmadan her hizmete kolayca soru ekleyebilmeniz için tüm özel sorularınızı ana listeye kaydeder. Örneğin, farklı bir hizmet açarsanız, ilk hizmet için oluşturduğunuz soru Özel alanlar bölümünde gösterilir, ancak devre dışı bırakılır. Vurgulanmış dikdörtgenin görüntülenip sorunun etkinleştirilmesi için soruya tıklayın.

Bu örnekte, ilk hizmet için eklenen soruların bu hizmet için kullanılabilir olduğunu görebilirsiniz. Bu hizmet için oluşturduğunuz tüm sorular tüm hizmetler için kullanılabilir.

   ![Birden çok hizmet için görünen soruların resmi.](../media/bookings-questions-services.png)

Rezervasyon sayfanız zaten yayımlanmışsa başka bir şey yapmanız gerekmez. Müşteriler, sizinle bir sonraki rezervasyonda soruları görür. Rezervasyon sayfanız henüz yayımlanmadıysa, **Web üzerinde Outlook'den rezervasyon sayfasına** gidin ve **kaydet ve yayımla'yı** seçin.

> [!WARNING]
> Ayrıca asıl listeden soruları silebilirsiniz. Ancak, bir soruyu silerseniz her hizmetten silinir. Diğer hizmetleri etkilemediğinizden emin olmak için soruyu seçerek devre dışı bırakmanızı öneririz. Vurgulanmış dikdörtgenle çevrelenmemiş bir sorunun devre dışı bırakıldığını görebilirsiniz.

## <a name="customer-experience"></a>Müşteri deneyimi

Müşterileriniz sizinle randevu aldığınızda, temel müşteri bilgileri soruları **Ayrıntılarınızı ekleyin** bölümünde gösterilir. Eklediğiniz özelleştirilmiş sorular **Ek bilgi sağlayın** bölümünde yer alır.

![Müşterilerin sorular etkinleştirildiğinde gördüklerinin resmi.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Personel deneyimi

Müşterileriniz sizinle randevu aldığınızda, personeliniz rezervasyon takviminde soruları ve müşterinin yanıtlarını görür. Bunu görmek için **Bookings** \> **Takvim'e** gidin ve bir randevu açın.

![Sorular etkinleştirildiğinde personelin ne gördüğünün resmi.](../media/bookings-questions-staff.png)
