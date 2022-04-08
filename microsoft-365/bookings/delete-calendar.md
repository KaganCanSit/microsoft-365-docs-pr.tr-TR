---
title: Rezervasyon takvimi silme
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Bookings takvimleri silmek için Microsoft 365 yönetim merkezi veya Windows PowerShell kullanın.
ms.openlocfilehash: 5b91a6b2c3d3d0637a017b0250ec45394958e147
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714383"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Bookings'da rezervasyon takvimini silme

> [!NOTE]
> Bu makale, Microsoft Bookings en son sürümüyle etkileşim kurmanıza yardımcı olur. Önceki sürümler önümüzdeki aylarda kullanımdan kaldırılacak.

Bu makalede, istenmeyen bir rezervasyon takvimini nasıl silebileceğiniz açıklanmaktadır. rezervasyon takvimini Microsoft 365 yönetim merkezi silebilir veya PowerShell'i kullanabilirsiniz. Bookings takvimi, Exchange Online bir posta kutusu olduğundan, rezervasyon takvimini silmek için ilgili kullanıcı hesabını silersiniz.

> [!IMPORTANT]
> 2017 veya daha önce oluşturduğunuz tüm rezervasyon takvimlerinin bu konudaki PowerShell yönergeleri kullanılarak silinmesi gerekir. 2018 veya sonrasında oluşturulan tüm rezervasyon takvimleri Microsoft 365 yönetim merkezi silinebilir.

Rezervasyon takvimi, aşağıdakiler dahil olmak üzere bu rezervasyon takvimi ve verileriyle ilgili tüm bilgilerin depolandığı yerdir:

- Rezervasyon takvimi oluşturulduğunda eklenen iş bilgileri, logo ve çalışma saatleri
- Rezervasyon takvimi oluşturulduğunda eklenen ilgili personel ve hizmetler
- Tüm rezervasyonlar ve izin randevuları oluşturulduktan sonra rezervasyon takvimine eklenir.

> [!WARNING]
> Rezervasyon takvimi silindikten sonra bu ek bilgiler de kalıcı olarak silinir ve kurtarılamaz.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi bir rezervasyon takvimini silme

1. Microsoft 365 yönetim merkezi gidin.

1. Yönetim merkezinde **Kullanıcılar** 'ı seçin.

   ![Microsoft 365 yönetim merkezi'deki Kullanıcılar kullanıcı arabiriminin görüntüsü.](../media/bookings-admin-center-users.png)

1. **Etkin Kullanıcılar** sayfasında silmek istediğiniz kullanıcıların adlarını seçin ve ardından **Kullanıcıyı sil**'i seçin.

   ![Microsoft 365 yönetim merkezi'de Kullanıcı Kullanıcı Arabirimini Sil'in görüntüsü.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Exchange Online PowerShell kullanarak rezervasyon takvimini silme

[Exchange Online PowerShell'e](/powershell/exchange/exchange-online-powershell-v2) bağlanmak için önkoşullar ve yönergeler için bkz. PowerShell Exchange Online Bağlan.

Bu adımları gerçekleştirmek için, "Yönetici olarak çalıştır" seçeneğini belirleyerek çalıştırdığınız etkin bir Microsoft PowerShell komut penceresi kullanıyor olmanız gerekir.

1. PowerShell penceresinde aşağıdaki komutu çalıştırarak EXO V2 modülünü yükleyin:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > [EXO V2 modülünü zaten yüklediyseniz](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module), önceki komut yazıldığında çalışır.
   
2. Çalıştırmanız gereken komut aşağıdaki söz dizimini kullanır:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ , kullanıcı asıl adı biçimindeki hesabınızdır (örneğin, `john@contoso.com`).

3. İstendiğinde, kalıcı olarak silmek istediğiniz rezervasyon takvimini barındıran Microsoft 365 kiracıda kiracı yöneticisi kimlik bilgileriyle oturum açın.

4. Bu komutun işlenmesi tamamlandıktan sonra, kiracınızdaki rezervasyon posta kutularının listesini almak için aşağıdaki komutu girin:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. Aşağıdaki komutu yazın:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Kalıcı olarak silmek istediğiniz rezervasyon posta kutusu diğer adının tam adını yazarken dikkatli olun.

6. Takvimin silindiğini doğrulamak için aşağıdaki komutu girin:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Silinen takvim çıktıda görünmez.
