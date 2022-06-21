---
title: Bookings’e personel ekleme
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Bu sayfayı, personel listenizi oluşturmak ve ad, telefon numarası ve e-posta adresi gibi personel üyesi ayrıntılarını yönetmek için kullanın.
ms.openlocfilehash: b9acf72e9026b230702ed4cad232a92842b51028
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185159"
---
# <a name="add-staff-to-bookings"></a>Bookings’e personel ekleme

Bookings'teki Personel sayfası, personel listenizi oluşturduğunuz ve ad, telefon numarası ve e-posta adresi gibi personel üyesi ayrıntılarını yönettiğiniz yerdir. Ayrıca buradan her personel için çalışma saatleri ayarlayabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Bookings bir Microsoft 365 özelliği olsa da tüm personelinizin Microsoft 365 hesabı olması gerekmez. Tüm personelin rezervasyon alabilmesi ve değişiklikleri zamanlaması için geçerli bir e-posta adresi olmalıdır.

## <a name="watch-add-your-staff-to-bookings"></a>İzleyin: Bookings'e personelinizi ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Adımlar

1. Giriş sayfasından takviminizi seçin.

2. Sol bölmedeki personel seçeneğine gidin ve **Yeni personel ekle'yi** seçin.

3. Kuruluşunuzun içinden personel eklerken, **kişi ekle** alanına adlarını yazın ve açılan menüde göründüklerinde seçin. Diğer alanlar otomatik olarak doldurulur.

    Personel üyesi eklendikten sonra, adının yanındaki **x** işaretini seçip **Kişi ekle** alanını düzenleyerek tüm Bookings iletişimlerinde görünen adı düzenleyebilirsiniz. Bu, personel üyelerinin müşteriler için belirli bir unvanın veya adın görüntülenmesini istiyorsanız yararlı olabilir; örneğin, Adele Vance'i "Dr. Vance, MD" olarak listeleme.

4. Kuruluşunuzun dışından personel eklemek için e-postalarını ve diğer bilgilerini el ile doldurun.

    > [!NOTE]
    > Kiracınızın dışındaki personel, serbest/meşgul bilgilerini Bookings ile paylaşamaz.

5. Her personel üyesi için bir rol seçin: Ekip üyesi, Zamanlayıcı, Görüntüleyici veya Konuk.
    - **Ekip üyesi** rezervasyonları kendi takviminde ve rezervasyon posta kutusunda uygunluk durumunu yönetebilir. Takvimlerine bir rezervasyon ekler veya düzenlerken personel olarak atanırlar.
    - **Zamanlayıcı** , takvimdeki rezervasyonları ve müşteri ayrıntılarını yönetebilir. Ayarlara, personele ve hizmetlere salt okunur erişime sahiptir.
    - **Görüntüleyici** takvimdeki tüm rezervasyonları görebilir, ancak bunları değiştiremez veya silemez. Ayarlara salt okunur erişimleri vardır.
    - **Konuklar** rezervasyonlara atanabilir ancak rezervasyon posta kutusunu açamaz.

6. Personel **e-postalarını etkinleştirmek için kendisine atanan bir rezervasyon oluşturulduğunda veya değiştirildiğinde Tüm personele e-posta yoluyla bildir'i** seçin. Aşağıda örnek bir e-posta verilmiştir:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Bookings'ten bir bildirim e-postası.":::

7. Personel üyelerinin takvimlerinden gelen serbest/meşgul bilgilerinin Bookings aracılığıyla bookings hizmetleri için **kullanılabilirliği** etkilemesini istiyorsanız Office 365 takvimdeki etkinlikler kullanılabilirliği etkiler'i seçin.

    Örneğin, bir personel üyesinin bir ekip toplantısı veya Çarşamba günü saat 15:00'te zamanlanmış kişisel bir randevusu varsa Bookings, bu personel üyesini ilgili zaman diliminde rezervasyon yapılamaz olarak gösterir. Bu süre, aşağıdaki örnekte gösterildiği gibi Bookings takvim görünümünde meşgul veya belirsiz olarak görünür.

    :::image type="content" source="media/bookings-busy-tentative-view-2.png" alt-text="Bookings takviminin görünümü.":::

> [!IMPORTANT]
> Çift rezervasyondan kaçınmak ve personel üyelerinizin uygunluk durumunu iyileştirmek için bu ayarı açık bırakmanızı (varsayılan olarak açıktır) kesinlikle öneririz.

8. Personel üyelerinizin tüm rezerve edilebilir zamanlarını yalnızca İş Bilgileri sayfasındaki İş saatleri bölümünde ayarladığınız iş saatleri içinde olacak şekilde ayarlamak için **İş saatlerini** **kullan'ı** seçin.

    Bu kutunun seçimini kaldırarak, personele rezervasyon yapabilecekleri zaman daha fazla sınıra sahip özel saatler verilebilir. Bu, personel üyesinin yalnızca Salı ve Çarşamba günleri sitede olabileceği veya sabahlarını bir randevu türü için, öğleden sonralarını ise diğer türler için ayırdığı senaryolar için yararlıdır.

    > [!NOTE]
    > Bookings, Bookings Takviminde 100'e kadar personeli destekler.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Bookings kullanıcılarını Bookings'te Personel olarak eklemeden süper kullanıcı yapma

Bookings'te bir kişiyi müşterilerin veya müşterilerin kullanımına sunmadan personel listenize eklemek isteyebilirsiniz. Onları süper kullanıcı yaptığınızda, rezervasyon posta kutusunun yöneticisi olur. Bir rezervasyon posta kutusunun yöneticisi olmak, rezervasyon posta kutusuna tam erişim ve farklı gönderme izinlerine sahip olmak olarak tanımlanır.

> [!NOTE]
> Bu adımlar yalnızca eklenen kullanıcıya Bookings'te zaten bir **görüntüleyici** rolü atanmamışsa çalışır.

1. [PowerShell ile Microsoft 365 Bağlan](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. PowerShell'i kullanarak aşağıdaki komutlarla tam erişim atayın:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Ardından farklı gönderme izinleri atamak için bu komutu çalıştırın.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Aşağıda, Allie Bellew'i Contoso kreş rezervasyon posta kutusuna eklemeye yönelik örnek bir PowerShell komutu verilmiştir.

1. İlk olarak şu komutu çalıştırın:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Ardından şu komutu çalıştırın:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** artık yönetici erişimine sahip ancak Bookings'te rezervasyon yapılabilir personel olarak görünmüyor.
