---
title: Google Workspace'den iş e-postası ve takvimi geçirme
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
description: E-postayı, kişileri ve takvimi Google Workspace'den işletmeler için Microsoft 365 öğrenin.
ms.openlocfilehash: a5ceccfde47b5084326aae9346b1c645cef7114a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015288"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Google Workspace'den iş e-postası ve takvimi geçirme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Google Workspace'den geçiş yapmak için yönetici Exchange Online kullanabilirsiniz. Postayı bir kerede veya aşamalı olarak geçirebilirsiniz. Aşağıdaki adımlarda, e-posta verilerini aynı anda nasıl geçirilir? Daha fazla bilgi için bkz [. G Suite geçişi gerçekleştirme](/exchange/mailbox-migration/perform-g-suite-migration).

Geçiş işlemi çeşitli adımlar içerir ve geçişte bulunduğunuz veri miktarına bağlı olarak birkaç saat ile birkaç gün arasında sürebilir.

## <a name="try-it"></a>Deneyin!

### <a name="create-a-google-service-account"></a>Google Hizmet Hesabı oluşturma

1. Chrome tarayıcı kullanarak, Google Workspace yönetici konsolunuzun içinde oturum [açın ve admin.google.com](https://admin.google.com). 
1. Yeni bir sekmede veya pencerede Hizmet Hesapları [sayfasına](https://console.developers.google.com/iam-admin/serviceaccounts) gidin. 
1. Proje **oluştur'a** seçin, projeyi adını yazın ve Oluştur'a **seçin**. 
1. Hizmet **hesabı oluştur'a seçin**, bir ad girin, **Oluştur'a ve sonra** Bitti'ye **seçin**. 
1. Eylemler menüsünü **açın** , **Düzenle'yi** seçin ve Benzersiz Kimliği not alır. Bu kimlik, işlem devam ediyor olacak. 
1. Etki alanı **genelinde temsilciyi göster bölümünü** açın. 
1. **G Suite Etki Alanı Genelinde Temsilci seçeneğini etkinleştir'i** seçin, izin ekranı için bir ürün adı girin ve Kaydet'i **seçin**. 

    > [!NOTE]
    > Ürün adı geçiş işlemi tarafından kullanılmaz, ancak iletişim kutusunda kaydetmek için gereklidir.     

1. Eylemler menüsünü **yeniden** açın ve Tuş **oluştur'a tıklayın**. 
1. **JSON'u** ve ardından **Oluştur'u seçin**. 

     Özel anahtar, cihazınızın indirme klasörüne kaydedilir.
 
1. **Kapat**'ı seçin. 

### <a name="enable-api-usage-for-the-project"></a>Proje için API kullanımını etkinleştirme

1. [API'ler sayfasına gidin](https://console.developers.google.com/apis/library). 
1. Arama çubuğuna **Gmail API'sini girin**.
1. Bu seçeneği ve ardından Etkinleştir'i **seçin**.
1. Google Takvim API'si, Kişiler API'si ve Kişiler API'si için bu işlemi yineler. 

### <a name="grant-access-to-the-service-account"></a>Hizmet hesabına erişim izni ver

1. Google Workspace yönetici konsoluna geri dönebilirsiniz. 
1. **Güvenlik'i** seçin, aşağı kaydırın ve **API denetimlerini açın**. 
1. Sayfayı aşağı kaydırın ve Etki **Alanı Genelinde Temsilciyi Yönet'i seçin**.
1. Yeni **ekle'yi** seçin ve daha önce not notunu yapmış olduğunu İstemci Kimliği'ne girin.
1. Ardından, Google API'ler için OAuth kapsamlarını girin. Bunlar 5. [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) şu adımlarda kullanılabilir:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. **Yetkilendir'i seçin**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Etki alanına gidip gelen postalar için alt Microsoft 365

1. **Google Workspace yönetici konsoluna** geri dönebilirsiniz.
1. Etki **Alanları,** Etki **alanlarını yönet ve** ardından Etki alanı **diğer adı ekle'yi seçin**. 
1. gibi bir etki alanı diğer adı girin `m365.contoso.com`.
1. Ardından **Devam'ı seçin ve etki alanı sahipliğini doğrulayın**. 

    Etki alanı doğrulaması genellikle yalnızca birkaç dakika sürer, ancak 48 saate kadar da sürebilir.

1. En [son Microsoft 365 yönetim merkezi.](https://admin.microsoft.com)
1. Gezinti Microsoft 365 yönetim merkezi gezintide, Show  >  all **Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a> öğesini ve sonra da Add **domain öğesini seçin**. 
1. Daha önce oluşturduğunuz alt etki alanını girin ve sonra Bu etki alanını **kullan'ı seçin**. 
1. Etki alanını bağlamak için Devam'ı **seçin**. 
1. Sayfayı aşağı kaydırın ve MX kayıtlarını, CNAME kayıtlarını ve TXT kayıtlarını not alır. 
1. **Google yönetici konsoluna geri dönebilirsiniz**.
1. Etki **Alanları'ı** seçin, **Etki alanlarını yönet'i** seçin, **Ayrıntıları Doğrula'ya** ve sonra da Etki **alanını yönet'e tıklayın**. 
1. Sol gezintide DNS'yi **seçin ve** Özel kaynak **kayıtları'na kadar aşağı kaydırın**. 
1. Kayıt türü açılan listesinde **MX'i** seçin, daha önce not edilen MX kayıt bilgilerini girin veya kopyalayıp yapıştırın, sonra da Ekle'yi **seçin**. 
1. CNAME kaydı ve TXT kaydı için işlemi yineler. 

    Bu değişikliklerin etkili bir şekilde yürürlüğe girecekleri zaman olabilir.  

1. Bu seçeneğin gerisinde kalan Microsoft 365 yönetim merkezi Devam'ı **seçin**. 

Etki alanınız artık ayarlanmıştır.  

### <a name="create-email-aliases-in-microsoft-365"></a>E-posta diğer adlarını Microsoft 365

Geçiş işlemi başlamadan önce, kullanıcılarınız için yeni alt etki alanıyla e-posta diğer adlarını oluşturmanız gerekir. 

1. Sonraki adımı başlatmak için, çalışma **sayfasındaki Etki** Alanı Ekle sihirbazında Microsoft 365 yönetim merkezi **Kullanıcılara Git'i seçin**. 
1. Bir kullanıcı seçin, ardından Kullanıcı adını ve **e-postayı yönet'i seçin**. 
1. Etki **Alanları** açılan listesinde, daha önce oluşturduğunuz alt etki alanlarını seçin. 
1. Bir kullanıcı adı girin, **Ekle,Değişiklikleri** **kaydet'i** seçin ve pencereyi kapatın. 

    Her kullanıcı için bu işlemi yineler. 

### <a name="start-the-migration-process"></a>Geçiş işlemini başlatma

Bitirdikten sonra, geçişe hazır oluruz. 

1. Gezintinin sol gezintisinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetim **merkezleri'ne kadar aşağı kaydırın ve** **Tamam'ı Exchange**. 
1. **Alıcılar'ın altında** **geçiş'i** seçin, **Yeni'yi****,** Geçiş'i Exchange Online **G Suite geçişi'ne ve sonra** da **Sonraki'ye seçin**. 
1. Geçirmek istediğiniz posta kutularının listesinin bulunduğu bir CSV dosyası oluşturun. Dosyanın şu biçimde olduğundan emin olun: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Ayrıntılar için bkz [. aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Dosya **Seç'i** seçin, CSV dosyasına gidin, dosyayı seçin, **Aç'ı ve sonra** İleri'yi **seçin**. 
1. Test etmek için kullanmak istediğiniz yönetici e-posta adresini doğrulayın. 
1. Dosya **Seç'i** seçin, daha önce oluşturduğunuz JSON dosyasına gidin (genellikle bilgisayarınızdan İndirilenler klasöründe bulunur), dosyayı seçin, Aç'ı ve **sonra Sonraki'yi** **seçin**. 
1. Yeni geçiş toplu işlemi **adı alanına bir ad girin**.
1. Oluşturduğunuz alt etki alanını Hedef teslim etki alanı **alanına girin** , Sonraki'yi ve **sonra da** Yeni'yi **seçin**. 
1. Bilgiler kaydedildiktan sonra Tamam'ı **seçin**. 

    Artık geçiş işleminin durumunu görüntüabilirsiniz. 

1. Bir süre geçtikten sonra, kaç kullanıcı geçirebilirsinize bağlı olarak Yenile'yi **seçin**. 
1. Durum Eşitleniyor olarak değiştirlandıktan **sonra Bu geçiş** toplu işlemini **tamamla'ya ve sonra Evet'e** **seçin**. 
1. İşlem tamamlandıktan sonra, durumunuz Tamamlandı olarak **değişir**. 
1. İstediğiniz zaman, geçiş hakkında daha **fazla bilgi** için Ayrıntıları görüntüle'yi seçin. 
1. **Kapat**'ı seçin. 
1. Google Outlook'dan gelen tüm e-postaların başarıyla geçirilir olduğunu doğrulamak için Outlook'i açın.
Bu işlemi takvim öğeleri ve kişiler için de yineebilirsiniz.
