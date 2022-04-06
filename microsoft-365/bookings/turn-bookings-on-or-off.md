---
title: Microsoft Bookings’i açma veya kapatma
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Microsoft 365'ta Microsoft Bookings erişimi Microsoft 365.
ms.openlocfilehash: 09fba96265bc3d2b67db9152f0c6020e10183314
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634811"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Microsoft Bookings’i açma veya kapatma

Bookings için veya belirli kullanıcılar için açık ya da kapalı olabilir. Kullanıcılarınız için Bookings, yeni bir sayfa Bookings takvim oluşturabilir ve diğer kişilerin kendileriyle zaman rezervasyonlarına izin ve vermezler.

> [!NOTE]
> Bu bölümlerde açıklanan yönetici denetimleri 21Vianet (Çin) Office 365 tarafından işletilen müşteriler için kullanılamaz.

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>E Bookings i kullanarak e-postanızı açma veya Microsoft 365 yönetim merkezi

1. Genel yönetici Microsoft 365 yönetim merkezi oturum açma.

2. Yönetim merkezinde Kuruluş  **ayarları'Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**gidin**</a>.

3. Kuruluş için posta kutusunu etkinleştirmek **veya devre dışı bırakmak üzere Bookings'i** kullanmasına izin Bookings kutusunu seçin.

   > [!NOTE]
   > Devre dışı Bookings, sayfalar oluşturulması ve yönetimi de dahil olmak üzere hizmete tüm Bookings devre Bookings olur.

4. **Değişiklikleri Kaydet**'i seçin.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>PowerShell Bookings kullanarak e-postalarınızı açma veya kapatma

[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) Bookings PowerShell cmdlet'ini kullanarak bu Exchange Online açmak veya kapatmak için, PowerShell Bağlan e Exchange Online [komutu çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell) ve şu komutu çalıştırın:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

Bookings'i kimlerin kullanabileceğini kontrol etmek için aşağıdaki ayarları kullanın, Bookings bilgileri paylaşıp paylaşılamayacaklarına ve personelin rezervasyon takvimine eklenmeden önce onay gerekip ihtiyaç olmadığına karar verin.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Ekran Ayarlar: Paylaşılan bilgileri ve personel onayı Bookings denetlemeye olanak Bookings izin veren ekran görüntüsü":::

### <a name="block-bookings-from-outside-your-organization"></a>Kuruluş dışından rezervasyonları engelleme

Yalnızca organizasyon Bookings randevu ayarlay kuruluşu için randevu ayarlamanızı s ayarlayın. Yalnızca, kuruluşta oturummış ve kimliği doğrulanmış olan kullanıcılar randevular için rezervasyonlar yer almaktadır.

### <a name="block-social-sharing-options"></a>Sosyal paylaşım seçeneklerini engelleme

Rezervasyon sayfalarının sosyal ağlarda nasıl paylaşılacaklarını kontrol edin. Bu ayar, Ayarları Microsoft 365 yönetim merkezi altında **Ayarlar** ->  **Org ayarları** ->  **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Personel ayrıntılarını müşterilerle paylaşmayı engelleme

İletişim bilgileri gibi personel ayrıntıları hiçbir zaman e-posta veya diğer iletişim yoluyla müşterilere gönderilmez.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Serbest/meşgul bilgilerini paylaşmadan önce personel onayı gerektirme

Organizasyon personelinizin uygunluk bilgileri bir rezervasyon sayfasından Bookings ile paylaşılmadan önce kabul edilmelerini gerekli haletebilirsiniz.

Bu ayar etkinleştirildiğinde, rezervasyon takvimlerine personel olarak eklenen kişiler, isteği Onaylama/Reddetme bağlantısını **içeren bir e-posta** alır.

## <a name="restrict-collection-of-customer-data"></a>Müşteri verileri koleksiyonunu kısıtlama

Uyumluluk nedenleriyle, bazı müşteri bilgilerini toplamak istemeyebilirsiniz. Bu seçeneklerden herhangi biri için onay kutusunu seçersiniz, bu alanlar müşterilerinize veya müşterilerinize gösterilen formlara dahil edilir.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Ekran görüntüsü: Müşterilerin hassas verileri sizin ile paylaşmasını önlemeye yardımcı olmak için onay kutularını seçin":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Kullanıcıları Bookings açma veya kapatma

Bu özelliği tek Bookings devre dışı abilirsiniz.

1. Kullanıcı Sayısı'Microsoft 365 yönetim merkezi ardından Kullanıcılar Etkin **Kullanıcılar'ı** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**seçin**</a>.

1. İstediğiniz kullanıcı ve ardından Lisanslar ve **Uygulamalar'ı seçin**.

1. **Uygulamalar'a** genişletin ve bu onay kutusunu Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Yalnızca seçili kullanıcıların takvim oluşturmasına Bookings ver

İlke kısıtlamalarını kullanarak, lisanslı kullanıcıların kendi takvimleri oluşturabileceklerini Bookings kısıtabilirsiniz. İlk olarak tüm Bookings izinlerini etkinleştirmeniz gerekir. Tüm kullanıcıların kuruluşlarında Bookings lisansı olur, ancak yalnızca bu ilkeye dahil olanlar takvimler oluşturabilir Bookings ve oluşturdukları takvimlere kimlerin eriş erişimleri üzerinde tam denetime sahip olabilir.

Bu ilkeye dahil olan kullanıcılar yeni takvimler Bookings ve mevcut takvimlere herhangi bir kapasiteyle (yönetici rolü dahil) personel olarak Bookings eklenebilir. Bu ilkeye dahil olmayan kullanıcılar yeni takvimler oluşturabilecek Bookings ve bunu yapmaya çalışan kullanıcılar bir hata iletisi alır.

Exchange Online PowerShell'i kullanarak aşağıdaki Exchange Online gerekir. Bu cmdlet'leri Exchange Online daha fazla bilgi için bkz[. Bağlan PowerShell'Exchange Online çalıştırma](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Aşağıdaki adımlarda, kuruluşta başka Outlook Web App posta kutusu ilkeleri (OWA) ilkeleri oluşturulmaz.

1. Takvim oluşturmasına izin verilen kullanıcılar için yeni bir posta Bookings oluşturun. (Bookings posta kutusu ilkeleri varsayılan olarak takvim oluşturmasına izin verilir.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Daha fazla bilgi için bkz [. New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Takvim oluşturma izni vermek istediğiniz her kullanıcı için bu komutu çalıştırarak ilgili kullanıcılara bu Bookings attayabilirsiniz.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Daha fazla bilgi için bkz. [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. İsteğe Bağlı: Bu komutu, diğer tüm kullanıcılar Bookings devre dışı bırakmak için çalıştırın.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Daha fazla bilgi için bkz. [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

OWA posta kutusu ilkeleri hakkında daha fazla bilgi için aşağıdaki konu başlıklarına bakın:

- [E-Web üzerinde Outlook posta kutusu ilkesi Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [E-posta Web üzerinde Outlook kutusunda posta kutusu ilkesi uygulama veya Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
