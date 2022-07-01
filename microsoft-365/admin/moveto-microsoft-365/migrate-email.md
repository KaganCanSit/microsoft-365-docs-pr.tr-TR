---
title: Google Workspace'ten iş e-postası ve takvimini geçirme
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: E-postayı, kişileri ve takvimi Google Çalışma Alanı'ndan İş için Microsoft 365'e geçirmeyi öğrenin.
ms.openlocfilehash: be7637816f80ecba3c56db644114d5ddb00caeb7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602048"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Google Workspace'ten iş e-postası ve takvimini geçirme

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.

## <a name="watch-migrate-business-email-and-calendar-from-google-workspace"></a>İzleyin: Google Workspace'ten iş e-postası ve takvimini geçirme

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2198034) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Google Çalışma Alanı'ndan Exchange Online için yönetici tarafından çalıştırdığınız bir geçiş kullanabilirsiniz. Postayı tek seferde veya aşamalı olarak geçirebilirsiniz. Aşağıdaki adımlar, e-posta verilerinin aynı anda nasıl geçireceğini gösterir. Daha fazla bilgi için bkz. [G Suite geçişi gerçekleştirme](/exchange/mailbox-migration/perform-g-suite-migration).

Geçiş işlemi birkaç adım alır ve geçirmekte olduğunuz veri miktarına bağlı olarak birkaç saat ile birkaç gün arasında sürebilir.

### <a name="create-a-google-service-account"></a>Google Hizmet Hesabı oluşturma

1. Chrome tarayıcısı kullanarak [admin.google.com'de](https://admin.google.com) Google Workspace yönetici konsolunuzda oturum açın. 
1. Yeni bir sekmede veya pencerede [Hizmet Hesapları](https://console.developers.google.com/iam-admin/serviceaccounts) sayfasına gidin. 
1. **Proje oluştur'u** seçin, projeyi adlandırın ve **Oluştur'u** seçin. 
1. **Hizmet hesabı oluştur'u** seçin, bir ad girin, **Oluştur'u** ve ardından **Bitti'yi** seçin. 
1. **Eylemler** menüsünü açın, **Düzenle'yi** seçin ve Benzersiz Kimlik'i not alın. İşlemin ilerleyen bölümlerinde bu kimlik gereklidir. 
1. **Etki alanı genelinde temsilci seçmeyi göster** bölümünü açın. 
1. **G Suite Etki Alanı Genelinde Temsilci Seçmeyi Etkinleştir'i** seçin, onay ekranı için bir ürün adı girin ve **Kaydet'i** seçin. 

    > [!NOTE]
    > Ürün adı geçiş işlemi tarafından kullanılmaz, ancak iletişim kutusuna kaydetmek için gereklidir.     

1. **Eylemler** menüsünü yeniden açın ve **Anahtar oluştur'u** seçin. 
1. **JSON'u** ve ardından **Oluştur'u** seçin. 

     Özel anahtar, cihazınızdaki indirme klasörüne kaydedilir.
 
1. **Kapat**'ı seçin. 

### <a name="enable-api-usage-for-the-project"></a>Proje için API kullanımını etkinleştirme

1. [API'ler sayfasına](https://console.developers.google.com/apis/library) gidin. 
1. Arama çubuğuna **Gmail API'sini** girin.
1. Seçin ve ardından **Etkinleştir'i** seçin.
1. Google Takvim API'sinde, Kişiler API'sinde ve Kişiler API'sinde bu işlemi yineleyin. 

### <a name="grant-access-to-the-service-account"></a>Hizmet hesabına erişim izni verme

1. Google Workspace yönetici konsoluna dönün. 
1. **Güvenlik'i** seçin, ekranı aşağı kaydırın ve **API denetimlerini** açın. 
1. Ekranı aşağı kaydırın ve **Etki Alanı Genelinde Temsili Yönet'i** seçin.
1. **Yeni ekle'yi** seçin ve daha önce not ettiğiniz İstemci Kimliğini girin.
1. Ardından Google API'leri için OAuth kapsamlarını girin. Bunlar 5. adımda [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) kullanılabilir ve şunlardır:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. **Yetki ver'i** seçin. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Microsoft 365'e giden postalar için alt etki alanı oluşturma

1. **Google Workspace yönetici** konsoluna dönün.
1. **Etki Alanları**, **Etki alanlarını yönet'i** ve ardından **Etki alanı diğer adı ekle'yi** seçin. 
1. gibi `m365.contoso.com`bir etki alanı diğer adı girin.
1. Ardından **Devam'ı seçin ve etki alanı sahipliğini doğrulayın**. 

    Etki alanı doğrulaması genellikle yalnızca birkaç dakika sürer, ancak 48 saate kadar sürebilir.

1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) gidin.
1. Microsoft 365 yönetim merkezi sol gezinti bölmesinde Tüm  > **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanlarını**</a> **Göster'i** ve ardından **Etki alanı ekle'yi** seçin. 
1. Daha önce oluşturduğunuz alt etki alanını girin, ardından **Bu etki alanını kullan'ı** seçin. 
1. Etki alanını bağlamak için **Devam'ı** seçin. 
1. Ekranı aşağı kaydırın ve MX kayıtlarını, CNAME kayıtlarını ve TXT kayıtlarını not alın. 
1. **Google yönetici konsoluna** dönün.
1. **Etki Alanları'nı** seçin, **Etki alanlarını yönet'i**, **Ayrıntıları Doğrula'yı** ve ardından **Etki alanını yönet'i** seçin. 
1. Sol gezinti bölmesinde **DNS'yi** seçin ve aşağı kaydırarak **Özel kaynak kayıtları'na** gidin. 
1. Kayıt türü açılan listesini açın ve **MX'i** seçin, daha önce not ettiğiniz MX kayıt bilgilerini girin veya kopyalayıp yapıştırın ve **ardından Ekle'yi** seçin. 
1. CNAME kaydı ve TXT kaydı için işlemi yineleyin. 

    Bu değişikliklerin etkili olması biraz zaman alabilir.  

1. Microsoft 365 yönetim merkezi kaldığınız yere dönün ve **Devam'ı** seçin. 

Etki alanınız artık ayarlandı.  

### <a name="create-email-aliases-in-microsoft-365"></a>Microsoft 365'te e-posta diğer adları oluşturma

Geçişin başlayabilmesi için önce kullanıcılarınız için yeni alt etki alanıyla e-posta diğer adları oluşturmanız gerekir. 

1. Sonraki adımı başlatmak için, Microsoft 365 yönetim merkezi **etki alanı ekleme** sihirbazında **Etkin kullanıcılara git'i** seçin. 
1. Kullanıcı **adını ve e-postayı yönet'i** seçin. 
1. **Etki Alanları** açılan listesinden daha önce oluşturduğunuz alt etki alanını seçin. 
1. Bir kullanıcı adı girin, **Ekle**, **Değişiklikleri kaydet'i** seçin ve pencereyi kapatın. 

    Bu işlemi her kullanıcı için yineleyin. 

### <a name="start-the-migration-process"></a>Geçiş işlemini başlatma

İşiniz bittiğinde geçiş yapmaya hazırsınız demektir. 

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> sol gezinti bölmesinde aşağı kaydırarak **Yönetici merkezlerine** gidin ve **Exchange'i** seçin. 
1. **Alıcılar'ın** altında **geçiş'i**, **Yeni'yi**, **Exchange Online'a geçir'i**, **G Suite geçişi'ni** ve ardından **İleri'yi** seçin. 
1. Geçirmek istediğiniz posta kutularının listesini içeren bir CSV dosyası oluşturun. Dosyanın şu biçimde olduğundan emin olun: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Ayrıntılar için bkz. [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. **Dosya Seç'i seçin**, CSV dosyasına gidin, dosyayı seçin, **Aç'ı** ve **ardından İleri'yi** seçin. 
1. Test için kullanmak istediğiniz yönetici e-posta adresini doğrulayın. 
1. **Dosya Seç'i seçin**, daha önce oluşturduğunuz JSON dosyasına gidin (genellikle bilgisayarınızdaki İndirilenler klasöründe), seçin, **Aç'ı** ve **ardından İleri'yi** seçin. 
1. **Yeni geçiş toplu işlemi adı alanına bir ad** girin.
1. **Hedef teslim etki alanı** alanına oluşturduğunuz alt etki alanını girin, **İleri'yi** ve ardından **Yeni'yi** seçin. 
1. Bilgiler kaydedildikten sonra **Tamam'ı** seçin. 

    Artık geçişinizin durumunu görüntüleyebilirsiniz. 

1. Bir süre geçtikten sonra, geçiş yaptığınız kullanıcı sayısına bağlı olarak **Yenile'yi** seçin. 
1. Durum **Eşitlendi** olarak değiştirildikten sonra **Bu geçiş toplu işlemini tamamla'yı** ve ardından **Evet'i** seçin. 
1. İşlem tamamlandıktan sonra durumunuz **Tamamlandı** olarak değişir. 
1. İsterseniz geçiş hakkında daha fazla bilgi için **Ayrıntıları görüntüle'yi** seçebilirsiniz. 
1. **Kapat**'ı seçin. 
1. Google Çalışma Alanı'ndan gelen tüm e-postaların başarıyla geçirildiğini doğrulamak için Outlook'u açın.
Bunu takvim öğeleri ve kişiler için de yineleyebilirsiniz.
