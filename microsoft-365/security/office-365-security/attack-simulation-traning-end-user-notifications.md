---
title: Saldırı benzetimi eğitimi için son kullanıcı bildirimleri
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler, Plan 2'de Yer alan Microsoft Defender'da Saldırı benzetimi eğitimi için son kullanıcı bildirimi e-Office 365 mesajları oluştur yapmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: bddd0b587e8fbf3007009a070cbd3e7616faac04
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2021
ms.locfileid: "63019057"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Saldırı benzetimi eğitimi için son kullanıcı bildirimleri

Microsoft 365 E5 için Microsoft Defender veya Office 365 Plan 2'de Saldırı benzetimi eğitimi içinde, son kullanıcı bildirimleri kullanıcılara gönderilen e-posta iletileridir İki temel bildirim türü vardır:

- **Benzetim bildirimleri**: Bu iletiler, kullanıcılar eğitimlere kaydolsa ve gerekli eğitimlerin anımsatıcıları olarak gönderilir.
- **Olumlu olumlu bildirimler**: Kullanıcılar sanal bir kimlik avı iletisi gönderdiği zaman bu iletiler gönderilir.

Kullanılabilir son kullanıcı bildirimini görmek için Microsoft 365 Defender portalını <https://security.microsoft.com>'da açın ve ardından E-posta ve işbirliği **Saldırı** \>  \> benzetimi eğitimi **&-kullanıcı bildirimleri sekmesine** gidin. Doğrudan Son kullanıcı **bildirimleri sekmesine gitmek için** kullanın<https://security.microsoft.com/attacksimulator?viewid=endUserNotification>.

Son **kullanıcı bildirimleri sekmesinin** iki sekmesi vardır:

- **Genel bildirimler**: Yerleşik ve değişiklik yapılamayan bildirimleri içerir.
- **Kiracı bildirimleri**: Oluşturduğunuz özel bildirimleri içerir.

Her bildirim için aşağıdaki bilgiler gösterilir:

- **Bildirimler**: Bildirimin adı.
- **Dil**: Bildirim birden çok çeviri içeriyorsa, ilk iki dil doğrudan gösterilir. Kalan dilleri görmek için sayısal simgenin (örneğin, **+10) üzerine gelin**.
- **Tür**: Değer Benzetim bildirimi **veya Pozitif** **bildirim bildirimidir**.
- **Kaynak**: Yerleşik bildirimler için değer **Genel'edir**. Özel bildirimler için değer **Kiracı'dır**.
- **Durum**
- **Bağlantılı benzetimler**
- **Oluşturan**: Yerleşik bildirimler için değer **Microsoft'un değeridir**. Özel bildirimler için değer, bildirimi oluşturan kullanıcının UPN değeridir.
- **Oluşturulma zamanı**
- **Değiştiren**
- **Son değiştirme saati**

Listede bir bildirim bulmak için Ara simgesini ![kullanın.](../../media/m365-cc-sc-search-icon.png) **Bildirimin** adını bulmak için arama kutusu.

Bildirimleri türe göre grupla için Grup simgesine ![tıklayın.](../../media/m365-cc-sc-group-icon.png) **Grupla** ve ardından Bildirim **türü'ne seçin**. Bildirimlerin grubunu çözmek için Yok'a **tıklayın**.

Yalnızca kiracı **bildirimleri sekmesinde** Filtre simgesine ![tıklayın.](../../media/m365-cc-sc-filter-icon.png) seçin.

Görüntülenen bir veya birden çok sütunu kaldırmak için Sütunları özelleştir simgesine ![tıklayın.](../../media/m365-cc-sc-customize-icon.png) **Sütunları özelleştirin**.

Listeden bir bildirim seçerek, aşağıdaki bilgileriyle birlikte ayrıntılar açılır.

- **Önizleme** sekmesi: Bildirim mesajını görüntüleyin. İletiyi farklı dillerde görüntülemek için Dil seçin **kutusunu** kullanın.
- **Ayrıntılar** sekmesi: Bildirimle ilgili ayrıntıları görüntüleyin:
  - **Bildirim açıklaması**
  - **Kaynak**: Yerleşik bildirimler için değer **Genel'edir**. Özel bildirimler için değer **Kiracı'dır**.
  - **Bildirim türü**
  - **Değiştiren**
  - **Son değiştirme**

## <a name="create-end-user-notifications"></a>Son kullanıcı bildirimleri oluşturma

Kiracı **bildirimleri sekmesinde Yeni** simge oluştur'a ![tıkleyebilirsiniz.](../../media/m365-cc-sc-create-icon.png) **Yeni son** kullanıcı bildirim sihirbazını başlatmak için Yeni oluştur.

1. Ayrıntıları **tanımla sayfasında** **, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Bildirim türünü seçin**: **Pozitif bildirim veya** **Benzetim bildirimi** kullanılabilir.
   - **Ad**: Benzersiz bir ad girin.
   - **Açıklama**: İsteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

2. İçerik **tanımla sayfasında** , kullanılabilen tek ayar İş dilinde **içerik ekle düğmesidir** . Buna tıklayınca, aşağıdaki **ayarları içeren varsayılan dilde** içerik ekle açılır öğesinin görüntülenir:
   - **Görünen addan**
   - **E-posta adresine**
   - **E-postanın dilini seçin**: Listeden bir dil seçin.
   - **Bunu varsayılan dil olarak işaretleme**: Bu bildirim için ilk ve tek dil olduğundan, bu değer seçilir ve değeri değiştiremezsiniz.
   - **Konu**: Varsayılan değer kimlik **avını bildirimi için teşekkür ederim değeridir**, ancak bunu değiştirebilirsiniz.
   - **E-postayı** içeri aktar: İsteğe bağlı olarak, var  olan bir düz metin iletisi dosyasını içeri aktararak bu düğmeye tıklayabilirsiniz ve sonra da Dosya seç'e tıklayabilirsiniz.
   - E-posta içerik alanı: İki sekme kullanılabilir:
     - **Metin** sekmesi: Bildirim e-postanızı oluşturmak için zengin bir metin düzenleyicisi kullanılabilir. Normal yazı tipi ve biçimlendirme ayarlarına ek olarak, aşağıdaki ayarlar da kullanılabilir:
       - **Dinamik etiket**: Aşağıdaki etiketlerden seçim yapın:
         - **Ad ekle**
         - **Soyadı ekle**
         - **UPN ekleme**
         - **E-posta adresi ekleme**
         - **Yük ekle**
     - **Kod** sekmesi: HTML kodunu doğrudan görüntüleyebilirsiniz ve değiştirebilirsiniz.

   Sayfanın üst kısmında yer alan E-posta **önizleme düğmesine** tıklayarak sonuçların önizlemesini görüntüleyebilirsiniz.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

   Az önce oluşturduğunuz **bildirimin aşağıdaki** bilgilerle özetlenmiş olduğu İçerik tanımla sayfasına dönersiniz:

   - **Dil**
   - **Konu**
   - **Kategori**
   - **Eylemler**: Aşağıdaki simgeler kullanılabilir:
     - ![Düzenle simgesi.](../../media/m365-cc-sc-edit-icon.png) **Düzenleyin**
     - ![Görünüm simgesi.](../../media/m365-cc-sc-view-icon.png) **Görünüm**
     - ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Sil**: Bildirimin yalnızca dil sürümü varsa, bildirimi silemezsiniz.

   Bildirimin farklı bir dilde bir sürümünü eklemek için Çeviri ekle simgesine ![tıklayın](../../media/m365-cc-sc-create-icon.png). Görüntülenen **Çeviri ekle** açılır sayfasında, daha önce açıklanan Varsayılan dilde içerik ekle açılır sayfasındaki ayarlarla aynı ayarlar kullanılabilir. Tek fark, ek çevirilerde **bunu varsayılan dil olarak işaretle'yi** seçmenizdir.

   Bitirdikten sonra Kaydet'e **tıklayın.**

   Bildirimin desteklenen 12 dilde çevirisi yapılan sürümlerini oluşturmak için bu adımları gereken kadar yineleebilirsiniz.

   Bitirdikten sonra, Sonraki'ne **tıklayın.**

3. Bildirimi **gözden geçir sayfasında** , bildiriminizin ayrıntılarını gözden geçirebilirsiniz.

   Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

   Yeni **benzetim bildirimi oluşturuldu** sayfasında, bağlantıları kullanarak yeni bir bildirim oluşturabilir, benzetim başlatabilirsiniz veya tüm bildirimleri görüntüleyebilirsiniz.

   Bitirdikten sonra Bitti'ye **tıklayın**.

Kiracı bildirimleri **sekmesine** geri dönebilirsiniz; oluşturduğunuz bildirim artık listeledir.

Bir bildirim seçerek aşağıdaki ek seçenekleri kullanabilirsiniz:

Yeni oluşturduğunuz bildirimin **Pozitif bir** bildirim bildirim seçin listesinde göründüğü Pozitif bildirim **sayfasına dönersiniz** .

- Bildirimi değiştirmek veya başka çeviriler eklemek için bildirimi seçin ve ardından Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Daha önce** açıklandığı gibi (çoğu değer zaten doldurulmuş olarak) bildirim sihirbazını başlatmak için bildirimi düzenleyin. Bildirimde desteklenen 12 dilin çevirileri zaten varsa, daha fazla çeviri ekzzzzsiniz.

- Bildirimin kopyasını oluşturmak için, bildirimi seçin ve ardından ![Bir kopya oluştur simgesi.](../../media/m365-cc-sc-copy-icon.png).

- Bir bildirimi silmek için, bildirimi seçin ve ardından ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png).

## <a name="related-links"></a>İlgili bağlantılar

[Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md)

[Kimlik avı saldırı benzetimi oluşturma](attack-simulation-training.md)

[Saldırı benzetimi eğitimi için benzetim otomasyonları](attack-simulation-training-simulation-automations.md)
