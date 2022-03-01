---
title: Bookings'e personel ekleme
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Personel listenizi oluşturmak ve ad, telefon numarası ve e-posta adresi gibi personel üyesi ayrıntılarını yönetmek için bu sayfayı kullanın.
ms.openlocfilehash: 03ebf5c21e40d53e87067866e05fc37c2c255331
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016296"
---
# <a name="add-staff-to-bookings"></a>Bookings'e personel ekleme

Bookings'te Personel sayfası, personel listenizi oluşturtunuz ve ad, telefon numarası ve e-posta adresi gibi personel üyesi ayrıntılarını yönetebilirsiniz. Buradan her personel üyesi için çalışma saatleri de ayarlayabiliyoruz.

## <a name="before-you-begin"></a>Başlamadan önce

Bookings, Microsoft 365 bir özelliği olsa da, tüm personel üyelerinizin bir eğitim Microsoft 365 olması gerekmez. Rezervasyon al ve değişiklikleri zamanlaması için tüm personel üyelerinin geçerli bir e-posta adresine sahip olması gerekir.

## <a name="watch-add-your-staff-to-bookings"></a>İzle: Personelinizi Bookings'e ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Adımlar

> [!NOTE]
> Bu adımlar henüz yeni Bookings deneyiminde mevcut değildir.

1. Personeli yönet sayfasına [gidin ve Personel](https://outlook.office.com/bookings/staff) **ekle'yi seçin**

2. Personel **Ekle düğmesini** seçin.

3. Kurum içinde personeli eklerken, Kişi ekle alanına bu kişilerin adını yazın  ve açılan menüde görünenleri seçin. Diğer alanlar otomatik olarak yüklenir.

    Bir personel üyesi eklendiktan sonra tüm Bookings iletişimlerinde görünen adı, adının yanındaki **x'i** seçerek ve Kişi ekle **alanını düzenleyerek düzenleyebilirsiniz** . Personel üyelerinin müşteriler için belirli bir unvan veya ad görüntülenebilir. Örneğin, Adele Vance'yi "Dr. Vance, MD" olarak listelemek bu yararlı olabilir.

4. Kurum dışından personel eklemek için e-postalarını ve diğer bilgilerini el ile doldurun.

    > [!NOTE]
    > Kiracınız dışından personel Bookings ile serbest/meşgul bilgilerini paylaşabilecektir.

5. Her personel üyesi için bir rol seçin: Yönetici, Görüntüleyici veya Konuk.
    - **Yöneticiler tüm** ayarları düzenleyebilir, personel ekleyemez ve kaldırabilir, rezervasyon oluşturabilir, düzenleyebilir veya silebilir.
    - **Görüntüleyenler** takvimde tüm rezervasyonları görebilir ancak bunları değiştiremez veya silemezler. Ayarlara salt okunur erişimleri vardır.
    - **Konuklar** rezervasyonlara atanabilir, ancak rezervasyon posta kutusunu açabilirsiniz.

6. Personel **e-postalarını etkinleştirmek için, Tüm personele e-postayla** bildir'i seçin. Aşağıdaki örnek bir e-postadır:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Bookings'den gelen bir bildirim e-postası.":::

7. Personel **üyelerinin takvimlerinden Office 365**/meşgul bilgisinin Bookings aracılığıyla bookings hizmetleri için kullanılabilirliği etkilemesini istemeniz durumu takviminde Olaylar'ı seçin.

    Örneğin, bir personel üyesinin Çarşamba günü 15:00'da zamanlanan bir ekip toplantısı veya kişisel randevu varsa, Bookings o zaman yuvasında uygun olmadığı için personel üyesini rezerve edilmeyi gösterir. Bu zaman, aşağıdaki örnekte gösterildiği gibi Bookings takvim görünümünde meşgul veya belirsiz olarak görünür.

    :::image type="content" source="media/bookings-busy-tentative-view.jpg" alt-text="Bir Bookings takviminin görünümü.":::

> [!IMPORTANT]
> Çift rezervasyon yapmaktan kaçınmak ve personel üyelerinizin uygunluk durumunu en iyi duruma getirmek için bu ayarı açık bırakmanızı (varsayılan olarak açıktır) kesinlikle öneririz.

8. Personel **üyelerinizin** tüm kitapçık zamanlarını yalnızca İş Bilgileri sayfasındaki İş saatleri bölümünde ayar kitapçık saatlerinden farklı olacak şekilde ayarlamak için  İş saatlerini kullan'ı seçin.

    Bu kutunun seçimini kaldırarak personele, rezervasyon yapılabilirken daha fazla sınırlayıcı olan özel saatler verilir. Bu, personel üyesinin yalnızca Salı ve Çarşamba günlerini sitede bulunduğu veya sabahlarını bir randevu türüne ve diğer türler için öğleden sonraları ayırmaları gereken senaryolarda yararlıdır.

    > [!NOTE]
    > Bookings, Bir Bookings Takvimi'ne 100'e kadar personel üyesini destekler.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Bir Bookings kullanıcıyı Bookings'te Personel olarak eklemeden süper kullanıcı yapma

Bir kişiyi Bookings'te müşterilere veya müşterilere sağlamak zorunda kalmadan personel listeniz'e ekleyebilirsiniz. Bu kullanıcıya süper kullanıcı olduktan sonra rezervasyon posta kutusunun yöneticisi olur. Bir rezervasyon posta kutusunun yöneticisi olmak, rezervasyon posta kutusuna tam erişim ve farklı gönderme izinlerine sahip olarak tanımlanır.

> [!NOTE]
> Bu adımlar yalnızca eklenen kullanıcı Bookings'te bir **görüntüleyici rolüne** henüz atanmamışsa çalışır.

1. [Bağlan PowerShell Microsoft 365'e çok zaman var](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. PowerShell kullanarak, aşağıdaki komutlarla tam erişim attayın:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Daha sonra gönderme izinleri atamak için bu komutu çalıştırın.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Bu örnekte, Allie Bellew'i Contoso çocuk bakım rezervasyon posta kutusuna eklemeye yardımcı olacak örnek bir PowerShell komutu yer alır.

1. Önce şu komutu çalıştırın:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Sonra şu komutu çalıştırın:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew'in** artık yönetici erişimi var, ancak Bookings'te uygun personel olarak görünmüyor.
