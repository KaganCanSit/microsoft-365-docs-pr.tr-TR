---
title: Program için Scheduler'ın Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Program için Scheduler'ın Microsoft 365.
ms.openlocfilehash: 3315c362a6e6ae1eb4fa9bf54d388a89dd667136
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988621"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Program için Zamanlayıcı'ya Microsoft 365

Kiracı yöneticilerinin bir Zamanlayıcı yardımcısı posta kutusu ayarlaması ve toplantı düzenleyicileri için Zamanlayıcı lisanslarını almaları gerekir. Bu hizmet için Zamanlayıcıyı Microsoft 365 gerekir. 

## <a name="licensing"></a>Lisanslama

Daha fazla bilgi: [Lisanslama Microsoft 365 zamanlayıcı](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!Note]
> Toplantı katılımcıları için Zamanlayıcı veya Toplantı lisansı Microsoft 365 gerek değildir. <br>Zamanlayıcı yardımcısı posta kutusu bir posta kutusu Microsoft 365 Zamanlayıcı lisansı gerektirmez.

## <a name="prerequisites"></a>Önkoşullar

| Önkoşul | Açıklama |
|-------------------|-------------|
|Kiracı için bir Zamanlayıcı Yardımcısı posta kutusu |Kiracınıza Exchange-posta gönder ve almak için kiracınız için Zamanlayıcı yardımcısı posta kutusu gibi görev alan bir kaynak Cortana. E-Cortana gönderilen tüm e-postalar, bekletme ilkeniz Cortana kiracının posta kutusunda korunur. Yardımcının tüm e-postaları otomatik olarak imza Cortana, genellikle "Cortana" veya "Cortana Scheduler" olarak Cortana.<ul><li>Kaynak posta kutusunda Exchange türü oluşturma</li><li>Posta kutusunun görünen adını ve birincil SMTP adresini veya adını `Cortana <cortana@yourdomain.com>` yazın `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul>**Not:** Zamanlayıcı yardımcısı posta kutusu bir posta kutusu Microsoft 365 Zamanlayıcı lisansı gerektirmez.|
|Exchange Online kutusunu geri alın |Toplantı düzenleyicileri, normalde toplantı Exchange Online bir posta kutusuna ve takvime sahip Microsoft 365 gerekir. Buna ek olarak, toplantı düzenleyicilerinin bir Zamanlayıcı lisansı olması gerekir. Zamanlayıcı lisansı, Zamanlayıcı yardımcısının toplantı zamanlaması için toplantı düzenleyicisinin posta kutusunu ve takvimini kullanmasını sağlar.<br/><br/> Lisans ve fiyatlandırma Microsoft 365 için Scheduler'a bakın.  <br/><br/>**Not:** Toplantı katılımcıları için Zamanlayıcı veya Toplantı lisansı Microsoft 365 gerek değildir. Toplantı katılımcıları kiracının içinde veya dışında olabilir. Toplantı katılımcıları yalnızca bir e-posta adresine erişmeleri gerekir.|


## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Zamanlayıcı yardımcısı posta kutusunu ayarlama

Zamanlayıcı yardımcısı posta kutusu, Exchange posta kutusu veya Zamanlayıcı lisansı gerektirmeyen, Microsoft 365 donanım türü bir posta kutusudur. Zamanlayıcı yardımcısının tüm e-postaları Cortana olarak imzalanacaklarından `Cortana <cortana@yourdomain.com>` `Cortana Scheduler <cortana.scheduler@yourdomain.com>`, posta kutusunun görünen adı ve birincil SMTP adresi Cortana. Zamanlayıcı yardımcısı posta kutusu oluşturulduktan sonra, posta kutusunu Zamanlayıcı yardımcısı posta kutusu olarak atamanız gerekir. Scheduler yardımcısı posta kutusunu Cortana, kullanıcılarınız adına toplantı zamanlamayı kullanabilirsiniz.

- Kullanıcı Microsoft 365 yönetim merkezi kutusu oluşturmak için posta kutusunu kullanın. 30 günlük bir bekletme ilkesi önerilir. 
- Posta kutunuz Cortana SMTP adresinin adını kullanın. , veya `Cortana@yourdomain.com`gibi `CortanaScheduler@contoso.com``Cortana.Scheduler@yourdomain.com` adlar önerilir.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Posta kutusunu Zamanlayıcı Yardımcısı olarak atama

Zaman çizelgesi için benzersiz bir Cortana posta kutusu oluşturulduktan sonra, posta kutusunu resmi bir Microsoft 365 atamanız gerekir. Zamanlamayı Cortana kutusu, kullanıcılarınız adına toplantı zamanlaması için kullanılabilir.

#### <a name="connect-to-powershell"></a>Bağlan PowerShell'e

Kullanıcı Microsoft 365 yönetim merkezi kutusu oluşturmak için posta kutusunu kullanın. 30 günlük bir bekletme ilkesi önerilir.
Posta kutunuz Cortana SMTP adresinin adını kullanın. , veya `Cortana@yourdomain.com`gibi `CortanaScheduler@contoso.com``Cortana.Scheduler@yourdomain.com` adlar önerilir.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

#### <a name="create-the-scheduler-assistant-mailbox"></a>Zamanlayıcı Yardımcısı Posta Kutusu Oluşturma

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```
    
#### <a name="designate-the-scheduler-assistant-mailbox"></a>Zamanlayıcı Yardımcısı Posta Kutusu Atama

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Cortana Scheduler yardımcı posta kutusunda bu "küme" komutunu çalıştırdikten sonra, posta kutusunda yeni bir "PersistedCapability" ayarlanır ve bu posta kutusunun "SchedulerAssistant" olduğunu unutmayın.

> [!Note]
> Organizasyonlarınızı PowerShell'e bağlamayı öğrenmek için bkz. [Bağlan PowerShell Microsoft 365 e bağlama](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Zamanlayıcı yardımcısı posta kutusunu doğrulama

Zamanlayıcı yardımcısı posta kutusunun oluşturulmuş olduğunu doğrulamak için

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Sonuç "yanlış" olması gerekir.

<br>

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Sonuç
- ResourceType: Ekipman
- Uzak Alıcı Türü: Yok
- RecipientType: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

<br/>

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Zamanlayıcı yardımcısı posta kutusunun hangi posta kutusu olduğunu bulmak için

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!Important]
> SchedulerAssistant özelliğinin ayarlanacak tam hazırlığı, Zamanlayıcı yardımcısı posta kutusunun tamamlanması birkaç saat sürebilir.


## <a name="exchange-online-mailbox"></a>Exchange Online kutusunu geri alın

Zamanlayıcı lisansı, Microsoft 365'a bir eklentidir ve düzenleyicinin toplantı zamanlama görevlerini Zamanlayıcı yardımcılarına atamasını sağlar. Posta kutusunu Zamanlayıcı yardımcısı posta kutusu olarak atamaya ek olarak, toplantı düzenleyicilerinin de Scheduler'ın çalışması için Microsoft 365 lisansı aracılığıyla bir Zamanlayıcı lisansı ve Exchange Online kutusu ve Exchange Online kutusu ve takvimi gerekir. Toplantı katılımcıları için Zamanlayıcı lisansı veya lisans Microsoft 365.

Scheduler eklentiyi satın almak için aşağıdaki lisanslardan birini gerektirirsiniz:

- Microsoft 365 E3, A3, E5, A5
- İş Temel, İş, İş Standart, İş Premium
- Office 365 E1, A1, E3, A3, E5, A5
- İş Temel İş, İş Premium
- Exchange Online Plan 1 veya Plan 2 lisansı. 

> [!Note]
> Web için Zamanlayıcı Microsoft 365 yalnızca dünya çapında çok kiracılı ortamlarda kullanılabilir. **Zamanlama Microsoft 365** şu kullanıcılarına kullanılamaz:
> 
> - Microsoft 365 21Vianet tarafından işletilen yeni bir ağ
> - Microsoft 365 emaneti German Telekom'un kullandığı Alman bulutlu bir bulut kullanıyor
> - GCC, Consumer, GCC High veya DoD dahil kamu bulutu
> 
> Zamanlayıcı, Veri konumu Almanca veri merkezi olmayan Almanya'daki kullanıcıları destekler.
