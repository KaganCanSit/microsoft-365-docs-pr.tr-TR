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
description: Microsoft Bookings'e bu bağlantıdan nasıl Microsoft 365.
ms.openlocfilehash: 8a92f156406a7c3aa4539036ae31d883a6db766f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984660"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Microsoft Bookings'i açma veya kapatma

Bookings, tüm kuruluş için veya belirli kullanıcılar için açık veya kapalı olabilir. Kullanıcılar için Bookings'i açabilirsiniz; bir Bookings sayfası oluşturabilir, takvim oluşturabilir ve diğer kişilerin bu sayfayla zaman rezervasyonu yaparken onlara izin vermelerine izin ve vermezler.

> [!NOTE]
> Bu bölümlerde açıklanan yönetici denetimleri 21Vianet (Çin) Office 365 tarafından işletilen müşteriler için kullanılamaz.

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Bookings'i bu sayfayı kullanarak organizasyon için Microsoft 365 yönetim merkezi

1. Genel yönetici Microsoft 365 yönetim merkezi oturum açma.

2. Yönetim merkezinde Kuruluş  **ayarları'Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**gidin**</a>.

3. Organizasyonunuz için **Bookings'i etkinleştirmek veya** devre dışı bırakmak üzere Bookings'i kullanmasına izin ver onay kutusunu seçin.

   > [!NOTE]
   > Bookings'i kapatarak Bookings sayfalarının oluşturulması ve yönetimi de içinde olmak üzere tüm hizmetlere erişim devre dışı bırakilecektir.

4. **Değişiklikleri Kaydet**'i seçin.

## <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>PowerShell kullanarak bookings'i organizasyonunız için açma veya kapatma

PowerShell cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) kullanarak Bookings'i açmak veya kapatmak için, [Bağlan PowerShell Exchange Online e](/powershell/exchange/connect-to-exchange-online-powershell) geçin ve aşağıdaki komutu çalıştırın:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Tek tek kullanıcılar için Bookings'i açma veya kapatma

Tek tek kullanıcılar için Bookings'i devre dışı abilirsiniz.

1. Kullanıcı Sayısı'Microsoft 365 yönetim merkezi ardından Kullanıcılar Etkin **Kullanıcılar'ı** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**seçin**</a>.

1. İstediğiniz kullanıcı ve ardından Lisanslar ve **Uygulamalar'ı seçin**.

1. **Uygulamalar'a** tıklayın ve Microsoft Bookings onay kutusunu temizleyin.

## <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Serbest/meşgul bilgilerini paylaşmadan önce personel onayı gerektirme

Yöneticiler, uygunluk bilgilerini Bookings aracılığıyla paylaştırmadan ve bir rezervasyon sayfasından rezervasyona uygun olmadan önce kuruluş çalışanları tarafından kabul edilmelerini gerekli hale gelmeden önce. Bu ayar, Kuruluş ayarları **Bookings** Microsoft 365 yönetim merkezi **nin Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**sayfasında**</a> \> kullanılabilir.

Bu ayar etkinleştirildiğinde, rezervasyon takvimlerine personel olarak eklenen çalışanlar, alacakları e-posta bildiriminde Onayla/Reddet bağlantısını bulur.

## <a name="block-social-sharing-options"></a>Sosyal paylaşım seçeneklerini engelleme

Yöneticiler, rezervasyon sayfalarının sosyal ağlarda nasıl paylaşılırken denetim bulundurabilirsiniz. Bu ayar, Kuruluş ayarları **Bookings** Microsoft 365 yönetim merkezi **nin Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**sayfasında**</a> \> kullanılabilir.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Yalnızca seçili kullanıcıların Bookings takvimleri oluşturmasına izin ver

İlke kısıtlamalarını kullanarak lisanslı kullanıcıların Bookings takvimleri oluşturabileceklerini kısıtabilirsiniz. İlk olarak tüm kuruluş için Bookings'i etkinleştirmeniz gerekir. Kuruluş dahili çalışan tüm kullanıcıların Bookings lisansları olur, ancak yalnızca bu ilkeye dahil olanlar Bookings takvimleri oluşturabilir ve oluşturdukları takvimlere kimlerin eriş erişimleri üzerinde tam denetime sahip olabilir.

Bu ilkeye dahil olan kullanıcılar yeni Bookings takvimleri oluşturabilir ve mevcut Bookings takvimlerine herhangi bir kapasitede personel olarak (yönetici rolü dahil) eklenebilir. Bu ilkeye dahil olmayan kullanıcılar yeni Bookings takvimleri oluşturabilecektir ve bunu yapmaya çalışan kullanıcılar bir hata iletisi alır.

Exchange Online PowerShell'i kullanarak aşağıdaki Exchange Online gerekir. Bu cmdlet'leri Exchange Online daha fazla bilgi için bkz[. Bağlan PowerShell'Exchange Online çalıştırma](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Aşağıdaki adımlarda, kuruluşta başka Outlook Web App posta kutusu ilkeleri (OWA) ilkeleri oluşturulmaz.

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

- [E-Web üzerinde Outlook posta kutusu ilkesi Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [E-posta Web üzerinde Outlook kutusunda posta kutusu ilkesi uygulama veya Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)