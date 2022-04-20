---
title: Microsoft 365 için Scheduler'ı ayarlama.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Microsoft 365 için Scheduler'ı ayarlama.
ms.openlocfilehash: ef377393134e4d8028ab0e6e40ddcc3647f60695
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953858"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Microsoft 365 için Zamanlayıcı'yı Ayarlama

Kiracı yöneticilerinin bir Zamanlayıcı yardımcısı posta kutusu ayarlaması ve Microsoft 365 hizmeti için Zamanlayıcı'yı etkinleştirmek üzere toplantı düzenleyicileri için Scheduler lisansları alması gerekir. 

## <a name="licensing"></a>Lisanslama

Daha fazla bilgi edinin: [Microsoft 365 lisanslama için Zamanlayıcı](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!NOTE]
> Toplantı katılımcılarına Zamanlayıcı veya Microsoft 365 lisansı gerekmez.
>
> Zamanlayıcı yardımcısı posta kutusu Microsoft 365 veya Zamanlayıcı lisansı gerektirmez.

## <a name="prerequisites"></a>Önkoşullar

|Önkoşul|Açıklama|
|---|---|
|Kiracı için zamanlayıcı yardımcısı posta kutusu |Kiracınızın Cortana e-posta gönderip alması için Zamanlayıcı yardımcısı posta kutusu işlevi gören bir Exchange donanım türü kaynak posta kutusu. Cortana gönderilen tüm e-postalar, bekletme ilkenize bağlı olarak kiracınızın Cortana posta kutusunda tutulur. Zamanlayıcı yardımcısı posta kutusu genellikle "Cortana" veya "Cortana Scheduler" olarak adlandırılır çünkü yardımcıdan gelen tüm e-postalar Cortana imzalanır. <ul><li>Kaynak posta kutusu Exchange donanım türü oluşturma</li><li>Posta kutusunun görünen adını ve birincil SMTP adresini `Cortana <cortana@yourdomain.com>` veya `Cortana Scheduler <cortana.scheduler@yourdomain.com>`olarak adlandırın.</li></ul> <br/> **Not:** Zamanlayıcı yardımcısı posta kutusu Microsoft 365 veya Zamanlayıcı lisansı gerektirmez.|
|Exchange Online posta kutusu |Toplantı düzenleyicileri genellikle Microsoft 365 lisanslarının bir parçası olarak Exchange Online posta kutusuna ve takvime sahip olmalıdır. Buna ek olarak, toplantı düzenleyicilerinin bir Zamanlayıcı lisansı olmalıdır. Zamanlayıcı lisansı, Zamanlayıcı yardımcısının toplantı düzenleyicisinin posta kutusunu ve takvimini kullanarak toplantı zamanlamasını sağlar. <br/><br/> Lisanslama ve fiyatlandırma bilgileri için bkz. Microsoft 365 için Scheduler. <br/><br/> **Not:** Toplantı katılımcılarına Zamanlayıcı veya Microsoft 365 lisansı gerekmez. Toplantı katılımcıları kiracının içinde veya dışında olabilir. Toplantı katılımcılarının yalnızca bir e-posta adresine erişmesi gerekir.|

## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Zamanlayıcı yardımcısı posta kutusunu ayarlama

Zamanlayıcı yardımcısı posta kutusu, ek bir Microsoft 365 veya Zamanlayıcı lisansı gerektirmeyen Exchange donanım türü bir posta kutusudur. Scheduler yardımcısından gelen tüm e-postalar Cortana (örneğin, veya `Cortana Scheduler <cortana.scheduler@yourdomain.com>`) imzalanacağından, `Cortana <cortana@yourdomain.com>` posta kutusunun görünen adı ve birincil SMTP adresi Cortana içermelidir. Zamanlayıcı yardımcısı posta kutusu oluşturulduktan sonra, posta kutusunu Zamanlayıcı yardımcısı posta kutusu olarak atamanız gerekir. Zamanlayıcı yardımcısı posta kutusunu atadıktan sonra Cortana kullanıcılarınız adına toplantı zamanlayabilirsiniz.

- Kullanıcı posta kutusu oluşturmak için Microsoft 365 yönetim merkezi kullanın. 30 günlük saklama ilkesi önerilir. 
- Posta kutunuzdaki birincil SMTP adresinde Cortana adını kullanın. , `CortanaScheduler@contoso.com`veya `Cortana.Scheduler@yourdomain.com` gibi `Cortana@yourdomain.com`adlar önerilir.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Posta kutusunu Zamanlayıcı Yardımcısı olarak belirleme

Cortana Scheduler için benzersiz bir posta kutusu oluşturulduktan sonra posta kutusunu resmi olarak Microsoft 365 olarak atamanız gerekir. Cortana Scheduler posta kutusunu atadıktan sonra, kullanıcılarınız adına toplantı zamanlayabilirsiniz.

### <a name="connect-to-powershell"></a>PowerShell'e Bağlan

Kullanıcı posta kutusu oluşturmak için Microsoft 365 yönetim merkezi kullanın. 30 günlük saklama ilkesi önerilir.
Posta kutunuzdaki birincil SMTP adresinde Cortana adını kullanın. , `CortanaScheduler@contoso.com`veya `Cortana.Scheduler@yourdomain.com` gibi `Cortana@yourdomain.com`adlar önerilir.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

### <a name="create-the-scheduler-assistant-mailbox"></a>Zamanlayıcı Yardımcısı Posta Kutusunu Oluşturma

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```

### <a name="designate-the-scheduler-assistant-mailbox"></a>Zamanlayıcı Yardımcısı Posta Kutusunu Belirleme

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Cortana Scheduler yardımcısı posta kutusunda bu "set" komutunu çalıştırdıktan sonra, bu posta kutusunun "SchedulerAssistant" olduğunu not etmek için posta kutusunda yeni bir "PersistedCapability" ayarlanır.

> [!NOTE]
> Kuruluşunuzu PowerShell'e bağlamayı öğrenmek için bkz. [PowerShell ile Microsoft 365 Bağlan](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Zamanlayıcı yardımcısı posta kutusunu doğrulama

Scheduler yardımcısı posta kutusunun oluşturulduğunu doğrulamak için

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Sonuç "false" olmalıdır.

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Sonuç şu şekilde olmalıdır:

- ResourceType: Ekipman
- Uzak Alıcı Türü: Yok
- RecipientType: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Hangi posta kutusunun Zamanlayıcı yardımcısı posta kutusu olduğunu bulmak için

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> SchedulerAssistant özelliğini ayarlamak için Scheduler yardımcısı posta kutusunun tam sağlamayı tamamlaması birkaç saat sürebilir.

## <a name="exchange-online-mailbox"></a>Exchange Online posta kutusu

Zamanlayıcı lisansı, toplantı düzenleyicisinin toplantı zamanlama görevlerini Zamanlayıcı yardımcısına devretmesini sağlayan Microsoft 365 eklentisidir. Bir posta kutusunu Zamanlayıcı yardımcısı posta kutusu olarak belirlemeye ek olarak, toplantı düzenleyicilerinin genellikle Scheduler'ın çalışması için Microsoft 365 lisansı aracılığıyla bir Zamanlayıcı lisansına ve Exchange Online posta kutusuna ve takvime de ihtiyacı olacaktır. Toplantı katılımcılarının Zamanlayıcı lisansına veya Microsoft 365 lisansına ihtiyacı yoktur.

Scheduler eklentisini satın almak için aşağıdaki lisanslardan birine ihtiyacınız vardır:

- Microsoft 365 E3, A3, E5, A5
- business basic, business, business standard, business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- business essentials, business Premium
- Plan 1 veya Plan 2 lisansını Exchange Online.

> [!NOTE]
> Microsoft 365 için Scheduler, dünya çapındaki çok kiracılı ortamlarda yalnızca İngilizce olarak kullanılabilir. **Microsoft 365 için Zamanlayıcı** şu kullanıcıların kullanımına sunulmaz:
>
> - Çin'de 21Vianet tarafından işletilen Microsoft 365
> - Veri emanetçisi Alman Telekom'un kullanıldığı Alman bulutuyla Microsoft 365
> - GCC, Tüketici, GCC Yüksek veya DoD dahil kamu bulutu
>
> Scheduler, veri konumu Alman veri merkezi olmayan Almanya'daki kullanıcıları destekler.
