---
title: hizmet tekliflerinizi Bookings'de tanımlama
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Hizmet adı, açıklama, konum, süre ve fiyatlandırma gibi hizmet teklifleri bilgilerini girme yönergeleri. Hizmeti sağlamak için uygun çalışanları da etiketleyebilirsiniz.
ms.openlocfilehash: 7d4bd5d8e75610785176f8c527576b0609cf71a4
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714405"
---
# <a name="define-your-service-offerings-in-bookings"></a>hizmet tekliflerinizi Bookings'de tanımlama

> [!NOTE]
> Bu makale, Microsoft Bookings en son sürümüyle etkileşim kurmanıza yardımcı olur. Önceki sürümler önümüzdeki aylarda kullanımdan kaldırılacak.

hizmet tekliflerinizi Microsoft Bookings tanımlarken, bir hizmet adı, açıklama, konum (şahsen toplantı yapmak mı yoksa çevrimiçi toplantı mı yapmak istediğinizi seçin), süre, müşterilere ve personele varsayılan anımsatıcılar, hizmetle ilgili iç notlar ve fiyatlandırma ayarlarsınız. Hizmeti sağlamak için uygun çalışanları da etiketleyebilirsiniz. Ardından, müşteriler iş web sitenize randevu almak için geldiğinde, tam olarak ne tür randevular olduğunu görebilir, hizmeti sağlamak istedikleri kişiyi ve hizmetlerinin maliyetini seçebilirler.

Ayrıca, birisi rezervasyon sayfanız aracılığıyla bir hizmet rezervasyonu yaparken gönderdiğiniz e-posta onayına ve anımsatıcılara özelleştirilmiş bilgiler ve URL'ler ekleyebilirsiniz.

## <a name="create-the-service-details"></a>Hizmet ayrıntılarını oluşturma

1. Microsoft 365'da Uygulama başlatıcıyı ve ardından **Bookings'ı** seçin.

2. **Takvim** >  **Hizmetleriniz'e** gidin ve **Yeni hizmet ekle'yi** seçin.

3. **Temel ayrıntılar** sayfasında seçimlerinizi ekleyin.

   **Hizmet adı**: Hizmetinizin adını girin. Bu, Takvim sayfasındaki açılan menüde görünecek addır. Bu ad, herkes Takvim sayfasına el ile randevu eklediğinde de görünür ve Self servis sayfasında kutucuk olarak görünür.

   **Açıklama**: Girdiğiniz açıklama, kullanıcı Self servis sayfasındaki bilgi simgesine tıkladığında görüntülenen açıklamadır.

   **Varsayılan konum**: Bu konum, hem personel hem de müşteriler için onay ve anımsatıcı e-postalarında görüntülenecek konumdur ve rezervasyon için oluşturulan takvim etkinliğinde görüntülenir.

   **Çevrimiçi toplantı ekle**: Bu ayar, personel üyesi için varsayılan istemci olarak yapılandırdığınıza bağlı olarak, Teams veya Skype aracılığıyla her randevu için çevrimiçi toplantıları etkinleştirir veya devre dışı bırakır.

   - Etkin:
     - Rezervasyona özgü bir Teams veya Skype toplantısının bağlantısı, arayarak bağlanma bilgilerinin yanı sıra hem personelin hem de müşterilerin takvimlerindeki takvim etkinliğine eklenir.
     - Toplantıya katılma bağlantısı, aşağıdaki örnekte gösterildiği gibi tüm onay ve anımsatıcı e-postalarına eklenir:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Bookings'da Teams toplantısına katılma bağlantısı örneği.":::

       > [!NOTE]
       > Teams toplantılara Teams mobil uygulaması, Teams masaüstü uygulaması, Web tarayıcısında veya telefonla arayarak bağlanma yoluyla katılabilirsiniz. Sanal randevuları ayırma konusunda en iyi deneyimi sağlamak için Teams kiracınız için varsayılan çevrimiçi toplantı hizmeti olarak etkinleştirmenizi kesinlikle öneririz.

   - Devre dışı:
     - Randevular bir toplantı seçeneği içermez ve Çevrimiçi toplantı ekle etkinleştirildiğinde görüntülenen **toplantıyla** ilgili tüm alanlar gösterilmez.

   **Süre**: Tüm toplantıların bu süre için rezerve edilmesi gerekir. Zaman, rezervasyon sırasında seçilen başlangıç saatinden itibaren engellenir. Personelin takvimlerinde tam randevu süresi engellenir.

   **Arabellek süresi**: Bu ayarın etkinleştirilmesi, her randevu rezervasyonunda personelin takvimine ek süre eklenmesine olanak tanır.

   Bu süre personelin takviminde engellenir ve serbest/meşgul bilgilerini etkiler. Bu, randevunun 15:00'te sona ereceği ve toplantının sonuna 10 dakikalık arabellek süresi eklendiği takdirde, personelin takvimi saat 15:10'a kadar meşgul ve rezervasyon yapılamıyor olarak gösterilir. Personelinizin bir hastanın grafiğini gözden geçirmesi veya ilgili hesap bilgilerini hazırlayan bir finansal danışman gibi bir toplantıya hazırlanmadan önce zamana ihtiyacı varsa bu yararlı olabilir. Bir toplantıdan sonra, örneğin birinin başka bir konuma seyahat etmek için zamana ihtiyacı olduğunda da yararlı olabilir.

   **Fiyat ayarlanmadı**: Self-Service sayfasında görüntülenecek fiyat seçeneklerini belirleyin. **Fiyat ayarlanmadı** seçilirse maliyet veya fiyatlandırmaya dair hiçbir fiyat veya başvuru görünmez.

   **Notlar**: Bu alan, rezervasyonu yapılan personelin rezervasyon etkinliğinde ve Bookings web uygulamasının Takvim sekmesinde görünen olayda görünür.

   **Etkinlik başına maksimum katılımcı** sayısı: Bu ayar, birden çok kişinin aynı randevu saatini ve aynı personeli (fitness sınıfı gibi) rezerve edebilmesini gerektiren hizmetler oluşturmanıza olanak tanır. Seçilen hizmet, personel ve saat için randevu zaman aralığı, sizin belirttiğiniz maksimum katılımcı sayısına ulaşılana kadar rezervasyon için kullanılabilir. Geçerli randevu kapasitesi ve katılımcılar, Bookings Web uygulamasının Takvim sekmesinde görüntülenebilir.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Bookings'da maksimum katılımcıyı ayarlama örneği":::

   **Müşterinin rezervasyonunu yönetmesine izin ver**: Bu ayar, Bookings Web uygulamasının Takvim sekmesinden rezervasyon yapılması koşuluyla müşterinin rezervasyonunu değiştirip değiştiremeyeceğini veya iptal edip etmeyeceğini belirler.

   - Etkin:

     **Rezervasyonu Yönet** düğmesi, müşteri onay e-postası üzerinde görünür. Bu düğme müşteri tarafından seçildiğinde üç seçenek görünür:

     - **Yeniden Zamanla** Bu seçeneğin seçilmesi, kullanıcıyı hizmete özgü bir Self-Service sayfasına getirir. Burada, özgün rezervasyondan aynı hizmet ve aynı personel üyesi için yeni bir saat ve/veya tarih seçebilir. Orijinal personel üyesi varsayılan olarak yeniden zamanlanmış rezervasyona eklenmiş olsa da, kullanıcının personel üyesini değiştirme seçeneğine de sahip olduğunu unutmayın.
     - **Rezervasyonu iptal et** Bu işlem rezervasyonu iptal eder ve personelin takviminden kaldırır.
     - **Yeni rezervasyon** Bu seçenek, kullanıcıyı yeni bir rezervasyon zamanlaması için tüm hizmetlerin ve personelin listelendiği Self-Service sayfasına getirir.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bookings'de Bookings Yönet düğmesi.":::

      Bu ayarı yalnızca Self-Service sayfasına erişen müşterilerle rahat ediyorsanız etkin bırakmanızı öneririz.

   - Devre dışı:

     Kullanıcı, Bookings Web uygulamasının Takvim sekmesinden rezervasyon yaparken rezervasyonunu yeniden zamanlayabilme veya iptal etme olanağına sahip olmayacaktır. Ancak Self-Service sayfasından rezervasyon yaparken, müşteriler bu ayar devre dışı bırakıldığında bile **Rezervasyonu Yönet** düğmesine ve tüm seçeneklerine sahip olmaya devam eder.

     Self-Service sayfasına erişimi sınırlamak istiyorsanız bu ayarı devre dışı bırakmanızı öneririz. Ayrıca, müşterilerinize ofisi arayarak veya yardım masasına e-posta göndererek başka yollarla rezervasyonlarında nasıl değişiklik yapacaklarını bildiren onay ve anımsatıcı e-postalarınıza metin eklemenizi öneririz.

4. **Kullanılabilirlik seçenekleri** sayfasında, zamanlama ilkeniz ve personelinizin uygunluk durumu için **Rezervasyon sayfanızdan** seçtiğiniz seçenekleri görebilirsiniz. Daha fazla bilgi için bkz [. Zamanlama ilkelerinizi ayarlama](set-scheduling-policies.md).

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Bookings'da maksimum katılımcıyı ayarlama örneği.":::

5. **Varsayılan fiyat**  Bu, Self-Service sayfasında görüntülenecek fiyattır. **Fiyat ayarlanmadı** seçilirse maliyet veya fiyatlandırmaya dair hiçbir fiyat veya başvuru görünmez.

6. **Notlar** Bu alan, rezervasyonu yapılan personelin rezervasyon etkinliğinde ve Bookings web uygulamasının Takvim sekmesinde görünen olayda görünür.

7. **Özel alanlar** , belirli bir randevu her rezerve edildiğinde gereken bilgileri toplarken yararlı olabilir. Örnek olarak klinik ziyareti öncesinde sigorta sağlayıcısı, kredi danışmaları için kredi türü, akademik danışmanlık için çalışmanın büyük bölümü veya aday görüşmeleri için başvuran kimliği verilebilir. Bu alanlar, müşterileriniz sizinle ve personelinizle randevu rezervasyonu gerçekleştirdiğinde Rezervasyon sayfasında görünür.

   Müşteri e-postası, telefon numarası, adres ve notlar çıkarılabilir olmayan alanlardır, ancak her alanın yanındaki **Gerekli** seçimini kaldırarak bunları isteğe bağlı hale getirebilirsiniz.

8. **Anımsatıcılar ve Onaylar** sayfasında, gönderdiğiniz anımsatıcıları ve bildirimleri ayarlayabilirsiniz. Anımsatıcılar ve bildirimler, randevudan önce belirli bir zamanda müşterilere, personel üyelerine veya her ikisine de gönderilir. Tercihinize göre her randevu için birden çok ileti oluşturulabilir.

   :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="Bookings bir onay e-postası.":::

   Yeniden zamanlama veya müşterilerin randevu için getirmesi gerekenler gibi istediğiniz ek metinleri buraya ekleyebilirsiniz. Aşağıda, **E-posta Onayı için ek bilgiler** alanında görülen özgün onay e-postasına eklenen özelleştirilmiş metin örneği verilmiştir:

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Bookings e-postadaki ek bilgiler.":::

9. **Müşteriniz için kısa mesaj bildirimlerini etkinleştirme** Seçilirse, sms mesajları müşteriye gönderilir, ancak yalnızca kabul ederse gönderilir.

   - El ile rezervasyon ve Self-Service Sayfasında kabul etme kutusu:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Bookings'daki kabul etme kutusu.":::

   - Kısa mesaj bildirimleri aşağıdaki gibi görünür (SMS bildirimlerinin şu anda yalnızca Kuzey Amerika'de kullanılabildiğini unutmayın):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Bookings'dan kısa mesaj bildirimi.":::

10. **Varsayılan zamanlama seçenekleri** varsayılan olarak açıktır. Müşterilerin belirli bir personel üyesini nasıl ayırttığını özelleştirmek istiyorsanız iki durumlu düğmeyi kapatın.

11. **Yayımlama seçenekleri** Bu hizmetin Self-Service sayfasında rezerve edilebilir olarak görünmesini mi yoksa hizmetin yalnızca Bookings Web uygulamasının Takvim sekmesinde rezerve edilebilir olmasını mı istediğinizi seçin.
