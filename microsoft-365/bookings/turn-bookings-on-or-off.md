---
title: Microsoft Bookings'i açma veya kapatma
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Microsoft 365'te Microsoft Bookings'e erişmeyi öğrenin.
ms.openlocfilehash: 3feacd756c141dd51edd7e987c1c4a2033524ae3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328506"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Microsoft Bookings'i açma veya kapatma

Bookings, tüm kuruluş için veya belirli kullanıcılar için açık veya kapalı olabilir. Kullanıcılar için Bookings'i açabilirsiniz; bir Bookings sayfası oluşturabilir, takvim oluşturabilir ve diğer kişilerin bu sayfayla zaman rezervasyonu yaparken onlara izin vermelerine izin ve vermezler.

> [!NOTE]
> Bu bölümlerde açıklanan yönetici denetimleri 21Vianet (Çin) tarafından işletilen Office 365 müşterileri için kullanılamaz.

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezini kullanarak Bookings'i organizasyonunız için açma veya kapatma

1. Microsoft 365 yönetim merkezinde genel yönetici olarak oturum açma.

2. Yönetim  **merkezindeSettings Kuruluş ayarlarına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**gidin**</a>.

3. Organizasyonunuz için **Bookings'i etkinleştirmek veya** devre dışı bırakmak üzere Bookings'i kullanmasına izin ver onay kutusunu seçin.

   > [!NOTE]
   > Bookings'i kapatarak Bookings sayfalarının oluşturulması ve yönetimi de içinde olmak üzere tüm hizmetlere erişim devre dışı bırakilecektir.

4. **Değişiklikleri Kaydet**'i seçin.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>PowerShell kullanarak bookings'i organizasyonunız için açma veya kapatma

PowerShell cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) kullanarak Bookings'i açmak veya kapatmak için, [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın ve aşağıdaki komutu çalıştırın:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

Bookings'i kimlerin kullanabileceğini kontrol etmek için aşağıdaki ayarları kullanın, Bookings bilgilerini paylaşıp paylaşmayacaklarına ve personelin bir Booking takvimine eklenmeden önce onay gerekip ihtiyaç olmadığına karar verin.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Ekran görüntüsü: Bookings'i kimlerin kullanabileceğini denetlemenizi sağlayan ayarlar, Bookings bilgilerini paylaşılırken ve personel onayı":::

### <a name="block-bookings-from-outside-your-organization"></a>Kuruluş dışından rezervasyonları engelleme

Bookings'i yalnızca organizasyon organizasyonumdan randevu ayarlayacak şekilde kurarak yeni randevu alabilirsiniz. Yalnızca, organizasyonda oturum veya kimliği doğrulanmış randevular için rezervasyon yapan kullanıcılar randevular için kullanılabilir.

### <a name="block-social-sharing-options"></a>Sosyal paylaşım seçeneklerini engelleme

Rezervasyon sayfalarının sosyal ağlarda nasıl paylaşılacaklarını kontrol edin. Bu ayar, Microsoft 365 yönetim merkezinde **SettingsOrg** ->  **settingsBookings** ->  altında yer almaktadır.

### <a name="block-sharing-staff-details-with-customers"></a>Personel ayrıntılarını müşterilerle paylaşmayı engelleme

İletişim bilgileri gibi personel ayrıntıları hiçbir zaman e-posta veya diğer iletişim yoluyla müşterilere gönderilmez.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Serbest/meşgul bilgilerini paylaşmadan önce personel onayı gerektirme

Organizasyon personelinizin uygunluk bilgileri Bookings aracılığıyla paylaşılmadan ve bir rezervasyon sayfasından rezervasyon için uygun olmadan önce kabul  edilebilirler.

Bu ayar etkinleştirildiğinde, rezervasyon takvimlerine personel olarak eklenen kişiler, isteği Onaylama/Reddetme bağlantısını **içeren bir e-posta** alır.

## <a name="restrict-collection-of-customer-data"></a>Müşteri verileri koleksiyonunu kısıtlama

Uyumluluk nedenleriyle, bazı müşteri bilgilerini toplamak istemeyebilirsiniz. Bu seçeneklerden herhangi biri için onay kutusunu seçersiniz, bu alanlar müşterilerinize veya müşterilerinize gösterilen formlara dahil edilir.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Ekran görüntüsü: Müşterilerin hassas verileri sizin ile paylaşmasını önlemeye yardımcı olmak için onay kutularını seçin":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Tek tek kullanıcılar için Bookings'i açma veya kapatma

Tek tek kullanıcılar için Bookings'i devre dışı abilirsiniz.

1. Microsoft 365 yönetim merkezine gidin, ardından Kullanıcılar Etkin **Kullanıcılar'ı** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**seçin**</a>.

1. İstediğiniz kullanıcı ve ardından Lisanslar ve **Uygulamalar'ı seçin**.

1. **Uygulamalar'a** tıklayın ve Microsoft Bookings onay kutusunu temizleyin.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Yalnızca seçili kullanıcıların Bookings takvimleri oluşturmasına izin ver

İlke kısıtlamalarını kullanarak lisanslı kullanıcıların Bookings takvimleri oluşturabileceklerini kısıtabilirsiniz. İlk olarak tüm kuruluş için Bookings'i etkinleştirmeniz gerekir. Organizasyon dahil tüm kullanıcıların Bookings lisansları olur, ama yalnızca bu ilkeye dahil olanlar Bookings takvimleri oluşturabilir ve oluşturdukları takvimlere kimlerin eriş erişimleri üzerinde tam denetime sahip olabilir.

Bu ilkeye dahil olan kullanıcılar yeni Bookings takvimleri oluşturabilir ve mevcut Bookings takvimlerine herhangi bir kapasitede personel olarak (yönetici rolü dahil) eklenebilir. Bu ilkeye dahil olmayan kullanıcılar yeni Bookings takvimleri oluşturabilecektir ve bunu yapmaya çalışan kullanıcılar bir hata iletisi alır.

Exchange Online PowerShell'i kullanarak aşağıdaki komutları çalıştırmalısınız. Exchange Online cmdlet'lerini çalıştırma hakkında daha fazla bilgi için bkz [. Exchange Online PowerShell'e Bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Aşağıdaki adımlarda, kuruluşta başka Outlook Web App (OWA) posta kutusu ilkeleri oluşturulmaz.

1. Bookings takvimleri oluşturmasına izin verilen kullanıcılar için yeni bir posta kutusu ilkesi oluşturun. (Yeni posta kutusu ilkeleri varsayılan olarak Bookings takvim oluşturmasına izin verilir.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Daha fazla bilgi için bkz [. New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Bookings takvimleri oluşturma izni vermek istediğiniz her kullanıcı için bu komutu çalıştırarak ilgili kullanıcılara bu ilkeyi attayabilirsiniz.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Daha fazla bilgi için bkz. [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. İsteğe bağlı: Bookings'i organizasyonlu diğer tüm kullanıcılar için devre dışı bırakmak için bu komutu çalıştırın.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Daha fazla bilgi için bkz. [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

OWA posta kutusu ilkeleri hakkında daha fazla bilgi için aşağıdaki konu başlıklarına bakın:

- [Exchange Online'da web üzerinde Outlook posta kutusu ilkesi oluşturma](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Exchange Online'da bir posta kutusunda Web üzerinde Outlook posta kutusu ilkesi uygulama veya kaldırma](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
