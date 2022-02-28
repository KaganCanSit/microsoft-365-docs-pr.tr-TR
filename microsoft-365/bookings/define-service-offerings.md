---
title: Bookings'te hizmet tekliflerinizi tanımlayın
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Hizmet adı, açıklaması, konumu, süresi ve fiyatlandırması gibi hizmet teklifleri bilgilerini girme yönergeleri. Ayrıca, hizmeti sağlamak için uygun olan çalışanları etiketebilirsiniz.
ms.openlocfilehash: 6b276d9ec2d943527f1a6d8ab310fc91406f216c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977688"
---
# <a name="define-your-service-offerings-in-bookings"></a>Bookings'te hizmet tekliflerinizi tanımlayın

Microsoft Bookings'te hizmet tekliflerinizi tanımlarken, bir hizmet adı, açıklama, konum (özellikle toplantı yapmak mı yoksa çevrimiçi toplantı yapmak mı, müşterilere ve personele varsayılan anımsatıcılar, hizmetle ilgili iç notlar ve fiyatlandırmayı ayarlarsanız. Ayrıca, hizmeti sağlamak için uygun olan çalışanları etiketebilirsiniz. Daha sonra, müşteriler iş web sitenize bir randevu rezervasyon yapmak için geldiğinde tam olarak hangi randevu türlerinin mevcut olduğunu görebilir, hizmeti sağlamak istediğiniz kişiyi seçebilir ve hizmetin maliyetinin ne kadar olduğunu görebilirler.

Ayrıca, rezervasyon sayfanız üzerinden bir hizmet için rezervasyon yaparken gönderebileceğiniz e-posta onayına ve anımsatıcılara özelleştirilmiş bilgiler ve URL'ler de  eklersiniz.

## <a name="create-the-service-details"></a>Hizmet ayrıntılarını oluşturma

1. Uygulama Microsoft 365 başlatıcısını ve ardından **Bookings'i seçin**.

2.  ->  Ayarlar [Manage services sayfasına gidin ve Yeni](https://outlook.office.com/bookings/settings/services) hizmet **ekle'yi seçin**.

3. Temel **ayrıntılar sayfasında** seçimlerinizi ekleyin.

   **Hizmet adı**: Hizmetinizin adını girin. Bu, Takvim sayfasındaki açılan menüde görünecek addır. Bu ad, herkes Takvim sayfasına el ile randevu ekleyeni de görünür ve Self servis sayfasında kutucuk olarak görünür.

   **Açıklama**: Kullanıcı Self servis sayfasında bilgi simgesine tıkladığında görünen açıklamadır.

   **Varsayılan konum**: Bu konum, hem personel hem de müşterilere gönderilen onay ve anımsatıcı e-postasında görüntülenecek ve rezervasyon için oluşturulan takvim etkinliğinde görüntülenecektir.

   **Çevrimiçi toplantı ekleme**: Bu ayar, personel üyesi için varsayılan istemci olarak hangisini yapılandırdınıza bağlı olarak, her randevu için Teams veya Skype yoluyla yapılan çevrimiçi toplantıları etkinleştirir veya devre dışı bırakır.

   - Etkin:
     - Bir Teams veya Skype toplantısının bağlantısı, arayarak bağlanılan bilgilerle birlikte hem personel hem de müşterilerin takvimleri üzerinden takvim etkinliğine eklenir.
     - Toplantıya katılma bağlantısı, aşağıdaki örnekte gösterildiği gibi, tüm onay ve anımsatıcı e-postalarına eklenir:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Bookings'te bir Teams bağlantısı örneği.":::

       > [!NOTE]
       > Teams toplantılar Teams mobil uygulaması, Teams masaüstü uygulaması, Web tarayıcısı veya telefonla arayarak bağlanarak katılabilirsiniz. Sanal randevuları randevu Teams en iyi deneyim için kiracınız için varsayılan çevrimiçi toplantı hizmeti olarak çevrimiçi toplantı hizmetini etkinleştirmenizi şiddetle öneririz.

   - Devre Dışı:
     - Randevular toplantı seçeneği içermez ve Çevrimiçi toplantı ekle etkinleştirildiğinde görünen **toplantıyla** ilgili tüm alanlar gösterilmez.

   **Süre**: Tüm toplantılara bu kadar süre için rezervasyon yapılması gerekir. Saat, rezervasyon sırasında seçilen başlangıç zamanından başarak engellenir. Personelin takviminde tam randevu saati engellenir.

   **Arabelleğe** alma süresi: Bu ayarın etkinleştirilmesi, randevu her randevu her rezervasyonda personelin takvimine fazladan zaman eklemeye olanak sağlar.

   Saat, personel takviminde engellenmiş ve serbest/meşgul bilgilerini etkiler. Bu da, randevu 15:00'de sona erer ve ara zaman 10 dakika arayla toplantının sonuna eklenirse, personelin takvimi 14:10'a kadar meşgul ve rezervasyona uygun değil olarak gösterir. Personelinizin bir toplantıya hazırlanmak için biraz zaman ihtiyacı varsa (örneğin, hastanın grafiğini gözden geçiren bir doktor veya ilgili hesap bilgilerini hazırlayan bir mali danışman) bu yararlı olabilir. Ayrıca, başka bir konuma seyahat etmek için zaman olması gibi durumlarda toplantı sonrasında yararlı olabilir.

   **Fiyat ayarlanmaz**: İlgili sayfada görüntülenecek fiyat Self-Service seçin. Fiyat **ayarlanmazsa** , fiyat veya fiyat başvurusu görünmez.

   **Notlar**: Bu alan, hem rezervasyon yapılan personel için rezervasyon etkinliğinde hem de Bookings web uygulamasının Takvim sekmesinde görüntülenen etkinlikte görünür.

   **Etkinlik başına en fazla** katılımcı sayısı: Bu ayar, birden fazla kişinin aynı randevu saati ve aynı personel (fitness sınıfı gibi) için rezervasyon yapma olanağı gerektiren hizmetler oluşturmanıza olanak sağlar. Seçilen hizmet, personel ve zaman için randevu zaman yuvası, sizin belirttiğiniz en fazla katılımcı sayısına ulaşıncaya kadar randevu alabilirsiniz. Geçerli randevu kapasitesi ve katılımcılar Bookings Web App'in Takvim sekmesinde 22/2/2007'de 2013'te 2013'e kadar olan bölümü 2013'te 2013'e kadar olan bölümü 201

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Bookings'te en fazla katılımcıyı ayarlama örneği":::

   **Müşterinin randevularını yönetmesine** izin verme: Bu ayar, Bookings Web app'in Takvim sekmesinden rezerve edilmesi şartıyla müşterinin rezervasyonda değişiklik edip etemey başka bir şey olup olmadığını belirler.

   - Etkin:

     Müşteri **onayı e-postasında** Rezervasyon Yönet düğmesi görünür. Bu düğme müşteri tarafından seçildiğinde üç seçenek görüntülenir:

     - **Yeniden zamanlama** Bu seçeneğin seçimi, kullanıcıya ilk rezervasyondan aynı hizmet ve aynı personel üyesi için yeni bir saat ve/veya tarih seçerek, hizmete özel Self-Service sayfasına getirir. İlk personel üyesi yeniden zamanlandı rezervasyona varsayılan olarak eklenmiş olsa bile, kullanıcının personel üyesini değiştirme seçeneği de vardır.
     - **Rezervasyon iptal et** Bu işlem rezervasyon iptal eder ve personelin takviminden kaldırır.
     - **Yeni rezervasyon** Bu seçenek, kullanıcıya yeni Self-Service için tüm hizmetler ve personelin listelenmiş olduğu Kullanıcı Kullanıcı Sayfasına getirir.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bookings'te Bookings'i Yönet düğmesi.":::

      Bu ayarı etkinleştirmenizi öneririz. Yalnızca İnternet sayfanız üzerinden erişim Self-Service öneririz.

   - Devre Dışı:

     Kullanıcı, Bookings Web app'in Takvim sekmesinde rezervasyon yaparken rezervasyonlarını yeniden zamanlama veya iptal etme olanağına sahip olmaz. Öte yandan Self-Service rezervasyon yaparken, bu ayar devre dışı bırakıldığında bile müşterilere Rezervasyon  Yönet düğmesi ve tüm seçenekleri sağ kalır.

     Belirli bir sayfaya erişimi sınırlamak için bu ayarı devre dışı Self-Service öneririz. Buna ek olarak, müşterilerinize başka bir şekilde, örneğin ofisi arayarak veya yardım masasına e-posta göndererek rezervasyonda nasıl değişiklik yapacaklarını söyleyen onay ve anımsatıcı e-postanıza metin eklemeyi öneririz.

4. Uygunluk **seçenekleri sayfasında**, personelinizin zamanlama ilkesi ve uygunluk durumu için Rezervasyon sayfasında seçtiğiniz seçenekleri görebilirsiniz. Daha fazla bilgi için bkz [. Zamanlama ilkelerinizi ayarlama](set-scheduling-policies.md).

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Bookings'te en fazla katılımcı ayarlama örneği.":::

5. **Varsayılan fiyat**  Bu, Sayfa Son sayfasında görüntülenecek Self-Service olur. Fiyat **ayarlanmazsa** , fiyat veya fiyat başvurusu görünmez.

6. **Notlar** Bu alan, rezervasyon yapılan personel için rezervasyon olayında ve Bookings web uygulamasında Takvim sekmesinde görüntülenen etkinlikte görünür.

7. **Özel alanlar** , belirli bir randevu her randevu için rezervasyon olduğunda gerekli bilgileri toplarken yararlı olabilir. Örnek olarak, üniversite ziyaretine önceden sigorta sağlayıcısı, kredi danışmanlıkları için kredi türü, akademik danışmanlık çalışmaları için önemli bir çalışma veya aday mülakatları için başvuran kimliği gibi örnekler verilmiştir. Müşterileriniz siz ve personeliniz ile randevu rezervasyonu yaparken bu alanlar Rezervasyon sayfasında görünür.

   Müşteri e-postası, telefon numarası, adres ve notlar çıkarılabilir olmayan alanlardır, ancak her alanın yanında Gerekli'nin seçimini kaldırarak bunları isteğe **bağlı olarak** da açabilirsiniz.

8. **Anımsatıcılar ve Onaylar** sayfasında, göndermek istediğiniz anımsatıcıları ve bildirimleri kurabilirsiniz. Anımsatıcılar ve bildirimler, randevudan önce belirtilen zamanda müşterilere, personel üyelerine veya her ikisine de gönderilir. Tercihlerinize bağlı olarak, her randevu için birden çok ileti oluşturulabilir.

   :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="Bookings'den bir onay e-postası.":::

   Buraya, yeniden zamanlama veya müşterilerin randevu için getirmesi gereken bilgiler gibi ek metinleri  dahilebilirsiniz. Aşağıda, E-posta Onayı için ek bilgiler alanında görülen, özgün onay e-postasında eklenen özelleştirilmiş **metin örneği velenmiştir** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Bir Bookings e-postası ek bilgiler.":::

9. **Müşteriniz için kısa mesaj bildirimlerini etkinleştirme** Seçiliyse SMS mesajları müşteriye gönderilir, ancak bunun için, kabul edildiyse gönderilir.

   - El ile rezervasyonda ve Sayfada Kabul Self-Service:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Bookings'te kabul edin kutusu.":::

   - Kısa mesaj bildirimleri aşağıdaki gibi olur (SMS bildirimlerinin şu anda yalnızca Kuzey Amerika'da mevcut olduğunu unutmayın):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Bookings'den bir metin bildirimi.":::

10. Varsayılan **zamanlama seçenekleri varsayılan** olarak açıktır. Müşterilerin belirli bir personel üyesi için rezervasyon rezervasyonlarını özelleştirmek için iki durumlu düğmeyi kapatın.

11. **Yayımlama seçenekleri** Bu hizmetin en son sayfada rezervasyona uygun olarak görünmesini Self-Service, yoksa hizmetin yalnızca Bookings Web App'in içindeki Takvim sekmesinde rezervasyona uygun hale mi alınıp alınamaz olduğunu seçin.
