---
title: Rezervasyon takvimini silme
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Bookings Microsoft 365 yönetim merkezi takvimlerini Windows PowerShell takvimleri silmek için takvimi veya takvimi kullanın.
ms.openlocfilehash: 48556951382b95316ffdb9e07c1c561758276ded
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983370"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Bookings'te bir rezervasyon takvimini silme

Bu makalede istenmeyen bir rezervasyon takvimini nasıl silebilirsiniz? Randevu takvimini takvim Microsoft 365 yönetim merkezi PowerShell'i kullanabilirsiniz. Bookings takvimi, Takvim'de bulunan bir Exchange Online, dolayısıyla rezervasyon takvimini silmek için ilgili kullanıcı hesabını silebilirsiniz.

> [!IMPORTANT]
> 2017 veya daha önce oluşturduğunuz tüm rezervasyon takvimleri, bu konudaki PowerShell yönergeleri kullanılarak silinmelidir. 2018 veya sonrasında oluşturulan tüm rezervasyon takvimleri takvim takvimlerinden Microsoft 365 yönetim merkezi.

Rezervasyon takvimi, rezervasyon takvimiyle ilgili tüm bilgilerin ve verilerin depolandığı takvimdir. Bunlar:

- Rezervasyon takvimi oluşturulduğunda eklenen iş bilgileri, logo ve çalışma saatleri
- Rezervasyon takvimi oluşturulduğunda eklenen ilgili personel ve hizmetler
- Randevular oluşturulduktan sonra rezervasyon takvimine eklenen tüm rezervasyonlar ve izin randevuları.

> [!WARNING]
> Bir rezervasyon takvimi silindikten sonra, bu ek bilgiler de kalıcı olarak silinir ve kurtarılamaz.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Takvimde bir rezervasyon takvimini Microsoft 365 yönetim merkezi

1. En son Microsoft 365 yönetim merkezi.

1. Yönetim merkezinde **Kullanıcılar** 'ı seçin.

   ![Kullanıcı Arabirimi'nin Microsoft 365 yönetim merkezi.](../media/bookings-admin-center-users.png)

1. **Etkin Kullanıcılar** sayfasında silmek istediğiniz kullanıcıların adlarını seçin ve ardından **Kullanıcıyı sil**'i seçin.

   ![Kullanıcı Arabirimini Sil'in Microsoft 365 yönetim merkezi.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Exchange Online PowerShell kullanarak rezervasyon Exchange Online silme

[PowerShell Bağlan Exchange Online hakkında](/powershell/exchange/exchange-online-powershell-v2) önkoşullar ve yol gösterici bilgi için bkz. PowerShell'e Exchange Online.

Bu adımları gerçekleştirmek için, "Yönetici olarak çalıştır" seçeneğini kullanarak çalıştırılan etkin bir Microsoft PowerShell komut penceresi kullanıyorsanız gerekir.

1. PowerShell penceresinde, aşağıdaki komutu çalıştırarak EXO V2 modülünü yükleme:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > [EXO V2 modülünü zaten yüklemişsiniz](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module), önceki komut yazıldığı gibi çalışır.
   
2. Çalıştırmak için gereken komut aşağıdaki söz dizimlerini kullanır:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ kullanıcı asıl adı biçimindeki hesabınızdır (örneğin, `john@contoso.com`).

3. İstendiğinde, kalıcı olarak silmek istediğiniz rezervasyon Microsoft 365 barındıran kiracının kiracı yöneticisi kimlik bilgileriyle oturum açın.

4. Bu komut işlemeyi tamamlaydıktan sonra, kiracınıza rezervasyon posta kutularının listesini almak için aşağıdaki komutu girin:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. Aşağıdaki komutu yazın:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Kalıcı olarak silmek istediğiniz rezervasyon posta kutusu diğer adının tam adını yazmaya dikkat edin.

6. Takvimin silindi olduğunu doğrulamak için aşağıdaki komutu girin:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Silinen takvim çıktıda görünmez.
