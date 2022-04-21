---
title: Microsoft Bookings'de SMS metin bildirimlerini ve anımsatıcılarını yapılandırma
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Microsoft Bookings'da istemciler, müşteriler ve iş ortakları için SMS metin bildirimlerini yapılandırmayı öğrenin.
ms.openlocfilehash: 8183f89a73d3a9fa8573bfaa55935865eeb794dd
ms.sourcegitcommit: 5b321693214e3859f5af8f1774d2a5ff685ab3b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65014968"
---
# <a name="configure-sms-text-notifications-and-reminders-in-microsoft-bookings"></a>Microsoft Bookings'de SMS metin bildirimlerini ve anımsatıcılarını yapılandırma

Microsoft Bookings ile, randevu alan kişiye gönderilecek SMS kısa mesaj bildirimlerini ayarlayabilirsiniz. SMS bildirimlerini Bookings web uygulamasındaki Bookings veya Teams'daki Bookings uygulamasında ayarlayabilirsiniz. Katılımcılar, müşteriler veya iş ortakları self servis rezervasyon sayfasında SMS bildirimleri almayı da kabul edebilir veya devre dışı bırakabilirsiniz. Ayrıca gönderene **STOP** yanıtını vererek SMS bildirimlerini almayı da geri çevirebilirler.

SMS bildirimleri, sanal rezervasyon randevuları için Teams toplantı bağlantısını içerir.

> [!Note]
> Bookings lisansı olan müşteriler için 30 Eylül 2022'ye kadar sınırsız SMS bildirimi sağlayacağız. Promosyon döneminin sonuna yaklaştıkça lisans gereksinimleriyle ilgili ek ayrıntılar sağlayacağız. Promosyon döneminden sonra fiyatlandırma ayrıntılarını almak için hesap ekibinize veya desteğinize başvurun.

## <a name="before-you-begin"></a>Başlamadan önce

Katılımcıların, müşterilerin veya iş ortaklarının SMS bildirimleri alabilmesi için geçerli bir Birleşik Devletler veya Kanada telefon numarasına ihtiyacı vardır.

## <a name="configure-sms-notification-in-microsoft-bookings"></a>Microsoft Bookings'da SMS bildirimini yapılandırma

SMS bildirimini Bookings birkaç yolla yapılandırabilirsiniz:

- Bookings web uygulamasında, [Bookings'de hizmet tekliflerinizi tanımlama](define-service-offerings.md) konusunun **Kısa mesaj bildirimlerini etkinleştirme** adımlarını izleyin.

- Teams'deki Booking uygulamasında **Ayarlar** >  **Appointment** **typeAdd appointment type (Randevu türü** >  ekle) öğesine gidin ve **Onlara kısa mesaj gönder'i** seçin.

## <a name="tracking-and-metrics-for-sms-notifications"></a>SMS bildirimleri için izleme ve ölçümler

> [!NOTE]
> Teams ve Bookings verilerini Teams yönetim merkezinde görmek için Teams yöneticisi olmanız gerekir.

Kuruluşunuzdaki SMS bildirimleri kullanımıyla ilgili önemli verileri Teams yönetim merkezinden izleyebilirsiniz. Kullanım raporları, gönderilen saat ve tarih, kaynak numarası, ileti türü, olay türü ve teslim durumu gibi verileri içerir. 30 Eylül 2022'den sonra SMS bildirimleri için tahmin ve bütçeye yardımcı olmak için tanıtım döneminde SMS bildirim telemetrisini kullanabilirsiniz.

1. Teams yönetim merkezinde **Sanal Ziyaretler SMS bildirimleri**.

2. **Analiz & Raporları** sayfasında SMS bildirimleri kullanımı'nı seçin.

    :::image type="content" source="../media/analytics-reporting.png" alt-text="Ekran görüntüsü: Teams yönetim merkezinde SMS metin bildirimleri Analiz ve raporlama sayfası":::

İlgili içerik

[Microsoft Bookings](bookings-overview.md)\
[Microsoft Bookings açma veya kapatma](turn-bookings-on-or-off.md)\
[iOS ve Android için Microsoft Bookings uygulamasını edinin](get-bookings-app.md)\
